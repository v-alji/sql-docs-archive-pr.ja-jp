---
title: キュー更新の競合の検出と解決 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- conflict resolution [SQL Server replication], queued updating subscriptions
- viewing queued updating conflicts
- conflict resolution [SQL Server replication]
- queued updating subscriptions [SQL Server replication]
- articles [SQL Server replication], conflict resolution
ms.assetid: 084ac587-25e7-4bd0-a385-556bbe07d02f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8c4608347ab119e25caa45b0ee4a592a953e34a4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645497"
---
# <a name="queued-updating-conflict-detection-and-resolution"></a><span data-ttu-id="a0887-102">Queued Updating Conflict Detection and Resolution</span><span class="sxs-lookup"><span data-stu-id="a0887-102">Queued Updating Conflict Detection and Resolution</span></span>
  <span data-ttu-id="a0887-103">キュー更新サブスクリプションによって複数の場所にある同じデータを変更できるため、パブリッシャーでデータを同期するときに競合が起こる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a0887-103">Because queued updating subscriptions allow modifications to the same data at multiple locations, there may be conflicts when data is synchronized at the Publisher.</span></span> <span data-ttu-id="a0887-104">レプリケーションによって、パブリッシャーとデータの変更を同期するときに競合を検出し、パブリケーションを作成したときに選択した解決方法でこれらの競合を解決します。</span><span class="sxs-lookup"><span data-stu-id="a0887-104">Replication detects any conflicts when changes are synchronized with the Publisher and resolves those conflicts using the resolution policy you selected when creating the publication.</span></span> <span data-ttu-id="a0887-105">発生する可能性がある競合は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="a0887-105">The following conflicts can occur:</span></span>  
  
-   <span data-ttu-id="a0887-106">更新および挿入競合。</span><span class="sxs-lookup"><span data-stu-id="a0887-106">Update and insert conflicts.</span></span> <span data-ttu-id="a0887-107">この競合は、同一のデータが 2 つの異なる場所で変更された場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="a0887-107">This conflict happens when the same data is changed at two locations.</span></span> <span data-ttu-id="a0887-108">一方の変更が競合の優先データとなり、他方は非優先データとなります。</span><span class="sxs-lookup"><span data-stu-id="a0887-108">One change wins, and the other one loses.</span></span>  
  
-   <span data-ttu-id="a0887-109">削除競合。</span><span class="sxs-lookup"><span data-stu-id="a0887-109">Delete conflicts.</span></span> <span data-ttu-id="a0887-110">この競合は、同一行が、ある箇所で削除され、別の箇所で変更された場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="a0887-110">This conflict occurs when the same row is deleted at one location and changed at the other.</span></span>  
  
 <span data-ttu-id="a0887-111">競合の検出と解決は、時間とリソースの消費が大きいプロセスであるため、複数のサブスクライバーがそれぞれ異なるデータのサブセットを変更できるようにデータ パーティションを作成して、アプリケーションの競合を最小限に抑えるようにします。</span><span class="sxs-lookup"><span data-stu-id="a0887-111">Conflict detection and resolution can be a time-consuming and resource-intensive process; therefore, it is best to minimize conflicts in the application by creating data partitions so that different Subscribers modify different subsets of data.</span></span>  
  
## <a name="detecting-conflicts"></a><span data-ttu-id="a0887-112">競合の検出</span><span class="sxs-lookup"><span data-stu-id="a0887-112">Detecting Conflicts</span></span>  
 <span data-ttu-id="a0887-113">パブリケーションを作成してキュー更新を有効にすると、 **newid()** を既定値とする**uniqueidentifier**列 ( **msrepl_tran_version** ) が、レプリケーションによって作成元のテーブルに追加されます。</span><span class="sxs-lookup"><span data-stu-id="a0887-113">When creating a publication and enabling queued updating, replication adds a **uniqueidentifier** column (**msrepl_tran_version**) with the default of **newid()** to the underlying table.</span></span> <span data-ttu-id="a0887-114">パブリッシュされたデータがパブリッシャーまたはサブスクライバーで変更されると、行は新しいグローバルな一意識別子 (GUID) を受け取り、新しい行が存在することを示します。</span><span class="sxs-lookup"><span data-stu-id="a0887-114">When published data is changed at either the Publisher or the Subscriber, the row receives a new globally unique identifier (GUID) to indicate that a new row version exists.</span></span> <span data-ttu-id="a0887-115">キュー リーダー エージェントは同期のとき、この列を使って競合の有無を確認します。</span><span class="sxs-lookup"><span data-stu-id="a0887-115">The Queue Reader Agent uses this column during synchronization to determine if a conflict exists.</span></span>  
  
 <span data-ttu-id="a0887-116">キューに登録されたトランザクションは、行の古い値と新しい値を保持しています。</span><span class="sxs-lookup"><span data-stu-id="a0887-116">A transaction in a queue maintains the old and new row version values.</span></span> <span data-ttu-id="a0887-117">トランザクションがパブリッシャーに適用されると、トランザクションの GUID とパブリケーションの GUID が比較されます。</span><span class="sxs-lookup"><span data-stu-id="a0887-117">When the transaction is applied at the Publisher, the GUIDs from the transaction and the GUID in the publication are compared.</span></span> <span data-ttu-id="a0887-118">トランザクションの古い GUID がパブリケーションの GUID と一致した場合は、パブリケーションは更新され、行にはサブスクライバーで作成された新しい GUID が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="a0887-118">If the old GUID stored in the transaction matches the GUID in the publication, the publication is updated and the row is assigned the new GUID that was generated by the Subscriber.</span></span> <span data-ttu-id="a0887-119">トランザクションの GUID でパブリケーションを更新すると、パブリケーションとトランザクションの間で一致する行が得られます。</span><span class="sxs-lookup"><span data-stu-id="a0887-119">By updating the publication with the GUID from the transaction, you have matching row versions in the publication and in the transaction.</span></span>  
  
 <span data-ttu-id="a0887-120">トランザクションの古い GUID がパブリケーションの GUID と一致しない場合は、競合が検出されます。</span><span class="sxs-lookup"><span data-stu-id="a0887-120">If the old GUID stored in the transaction does not match the GUID in the publication, a conflict is detected.</span></span> <span data-ttu-id="a0887-121">パブリケーションの新しい GUID は、異なる 2 つの行のバージョンが存在することを示します。1 つはサブスクライバーが送信するトランザクションの行で、もう 1 つはパブリッシャーの新しい行です。</span><span class="sxs-lookup"><span data-stu-id="a0887-121">The new GUID in the publication indicates that two different row versions exist: one in the transaction being submitted by the Subscriber and a newer one that exists on the Publisher.</span></span> <span data-ttu-id="a0887-122">この場合、このサブスクライバーのトランザクションを同期する前に、他のサブスクライバーまたはパブリッシャーがパブリケーション内の同一の行を更新しています。</span><span class="sxs-lookup"><span data-stu-id="a0887-122">In this case, another Subscriber or the Publisher updated the same row in the publication before this Subscriber transaction was synchronized.</span></span>  
  
 <span data-ttu-id="a0887-123">マージ レプリケーションの場合とは違って、GUID 列を使用するのは行を識別するためでなく、行に変更があったかどうかを調べるためです。</span><span class="sxs-lookup"><span data-stu-id="a0887-123">Unlike merge replication, the use of a GUID column is not used to identify the row itself, but is used to check if the row has changed.</span></span>  
  
## <a name="resolving-conflicts"></a><span data-ttu-id="a0887-124">競合の解決</span><span class="sxs-lookup"><span data-stu-id="a0887-124">Resolving Conflicts</span></span>  
 <span data-ttu-id="a0887-125">キュー更新を使用してパブリケーションを作成するときは、競合が検出された場合に使用する競合回避モジュールを選択します。</span><span class="sxs-lookup"><span data-stu-id="a0887-125">When you create a publication using queued updating, you select a conflict resolver to be used if any conflicts are detected.</span></span> <span data-ttu-id="a0887-126">競合回避モジュールでは、同期中に同じ行の複数のバージョンが検出された場合に、キュー リーダー エージェントで処理する方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="a0887-126">The conflict resolver governs how the Queue Reader Agent handles different versions of the same row encountered during synchronization.</span></span> <span data-ttu-id="a0887-127">パブリケーションにサブスクリプションがなければ、パブリケーションの作成後に競合解決方法を変更できます。</span><span class="sxs-lookup"><span data-stu-id="a0887-127">You can change the conflict resolution policy after the publication is created as long as there are no subscriptions to the publication.</span></span> <span data-ttu-id="a0887-128">使用可能な競合解決方法は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="a0887-128">The conflict resolver choices are the following:</span></span>  
  
-   <span data-ttu-id="a0887-129">パブリッシャー優先 (既定値)</span><span class="sxs-lookup"><span data-stu-id="a0887-129">Publisher wins (the default)</span></span>  
  
-   <span data-ttu-id="a0887-130">パブリッシャー優先およびサブスクリプション再初期化</span><span class="sxs-lookup"><span data-stu-id="a0887-130">Publisher wins and the subscription is reinitialized</span></span>  
  
-   <span data-ttu-id="a0887-131">サブスクライバー優先</span><span class="sxs-lookup"><span data-stu-id="a0887-131">Subscriber wins</span></span>  
  
 <span data-ttu-id="a0887-132">競合は記録され、競合表示モジュールによって表示可能です。</span><span class="sxs-lookup"><span data-stu-id="a0887-132">Conflicts are recorded and can be viewed using the Conflict Viewer.</span></span>  
  
 <span data-ttu-id="a0887-133">**キュー更新の競合解決方法を設定するには**</span><span class="sxs-lookup"><span data-stu-id="a0887-133">**To set the queued updating conflict resolution policy**</span></span>  
  
-   [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]<span data-ttu-id="a0887-134">: [キュー更新の競合解決オプションの設定 &#40;SQL Server Management Studio&#41;](../publish/create-an-updatable-subscription-to-a-transactional-publication.md)</span><span class="sxs-lookup"><span data-stu-id="a0887-134">: [Set Queued Updating Conflict Resolution Options &#40;SQL Server Management Studio&#41;](../publish/create-an-updatable-subscription-to-a-transactional-publication.md)</span></span>  
  
-   <span data-ttu-id="a0887-135">レプリケーション Transact-SQL プログラミング : [トランザクション パブリケーションの更新可能なサブスクリプションの有効化](../publish/enable-updating-subscriptions-for-transactional-publications.md)</span><span class="sxs-lookup"><span data-stu-id="a0887-135">Replication Transact-SQL programming: [Enable Updating Subscriptions for Transactional Publications](../publish/enable-updating-subscriptions-for-transactional-publications.md)</span></span>  
  
 <span data-ttu-id="a0887-136">**データの競合を表示するには**</span><span class="sxs-lookup"><span data-stu-id="a0887-136">**To view data conflicts**</span></span>  
  
-   [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]<span data-ttu-id="a0887-137">: [トランザクション パブリケーションのデータの競合の表示 &#40;SQL Server Management Studio&#41;](../view-data-conflicts-for-transactional-publications-sql-server-management-studio.md)</span><span class="sxs-lookup"><span data-stu-id="a0887-137">: [View Data Conflicts for Transactional Publications &#40;SQL Server Management Studio&#41;](../view-data-conflicts-for-transactional-publications-sql-server-management-studio.md)</span></span>  
  
### <a name="publisher-wins"></a><span data-ttu-id="a0887-138">パブリッシャー優先</span><span class="sxs-lookup"><span data-stu-id="a0887-138">Publisher Wins</span></span>  
 <span data-ttu-id="a0887-139">競合解決方法がパブリッシャー優先の場合は、トランザクションの一貫性はパブリッシャーのデータに基づいて維持されます。</span><span class="sxs-lookup"><span data-stu-id="a0887-139">When the conflict resolution is set to the Publisher wins, transactional consistency is maintained based on the data at the Publisher.</span></span> <span data-ttu-id="a0887-140">競合を起こしたトランザクションは、それを開始したサブスクライバーにロールバックされます。</span><span class="sxs-lookup"><span data-stu-id="a0887-140">The conflicting transaction is rolled back at the Subscriber that initiated it.</span></span>  
  
 <span data-ttu-id="a0887-141">キュー リーダー エージェントが競合を検出すると、補正コマンドが生成されます。補正コマンドをディストリビューション データベースに通知することで、このコマンドはサブスクライバーへ反映されます。</span><span class="sxs-lookup"><span data-stu-id="a0887-141">The Queue Reader Agent detects a conflict and compensating commands are generated and propagated to the Subscriber by posting them in the distribution database.</span></span> <span data-ttu-id="a0887-142">その後、ディストリビューション エージェントは、競合状態のトランザクションを発信したサブスクライバーに補正コマンドを適用します。</span><span class="sxs-lookup"><span data-stu-id="a0887-142">The Distribution Agent then applies the compensating commands to the Subscriber that originated the conflicting transaction.</span></span> <span data-ttu-id="a0887-143">補正アクションによって、パブリッシャーの行に一致するようにサブスクライバーの行が更新されます。</span><span class="sxs-lookup"><span data-stu-id="a0887-143">The compensating actions update the rows on the Subscriber to match the rows on the Publisher.</span></span>  
  
 <span data-ttu-id="a0887-144">補正コマンドが適用されるまでは、サブスクライバーにロールバックされるトランザクションの結果を読み取ることができます。</span><span class="sxs-lookup"><span data-stu-id="a0887-144">Until the compensating commands are applied, it is possible to read the results of a transaction that will eventually be rolled back at the Subscriber.</span></span> <span data-ttu-id="a0887-145">この処理は、ダーティ リード ("READ UNCOMMITTED" 分離レベル) と同じです。</span><span class="sxs-lookup"><span data-stu-id="a0887-145">This is equivalent to a dirty read (read uncommitted isolation level).</span></span> <span data-ttu-id="a0887-146">後で発生する従属トランザクションは補正されません。</span><span class="sxs-lookup"><span data-stu-id="a0887-146">There is no compensation for the subsequent dependent transactions that can occur.</span></span> <span data-ttu-id="a0887-147">ただし、トランザクション境界は受け入れられます。そして、トランザクション内のすべてのアクションがコミットされます。競合の場合はロールバックされます。</span><span class="sxs-lookup"><span data-stu-id="a0887-147">However, transaction boundaries are honored and all the actions within a transaction are either committed, or in the case of a conflict, rolled back.</span></span>  
  
### <a name="publisher-wins-and-the-subscription-is-reinitialized"></a><span data-ttu-id="a0887-148">パブリッシャー優先およびサブスクリプション再初期化</span><span class="sxs-lookup"><span data-stu-id="a0887-148">Publisher Wins and the Subscription Is Reinitialized</span></span>  
 <span data-ttu-id="a0887-149">競合を解決するためにサブスクライバーを再初期化すると、サブスクライバーのトランザクション一貫性が最も高くなります。ただし、パブリケーションのデータ量が多い場合、この再初期化には時間がかかります。</span><span class="sxs-lookup"><span data-stu-id="a0887-149">Reinitializing the Subscriber to resolve conflicts maintains strict transactional consistency at the Subscriber, but it can be time consuming if the publication contains large amounts of data.</span></span>  
  
 <span data-ttu-id="a0887-150">キュー リーダー エージェントが競合を検出すると、キューに登録された残りのトランザクション (競合状態のトランザクションも含む) は拒否され、サブスクライバーには再初期化のマークが付けられます。</span><span class="sxs-lookup"><span data-stu-id="a0887-150">When the Queue Reader Agent detects a conflict, all remaining transactions in the queue (including the transaction in conflict) are rejected, and the Subscriber is marked for reinitialization.</span></span> <span data-ttu-id="a0887-151">パブリケーションに対して次に作成されるスナップショットは、ディストリビューション エージェントによってサブスクライバーに適用されます。</span><span class="sxs-lookup"><span data-stu-id="a0887-151">The next snapshot generated for the publication is applied by the Distribution Agent to the Subscriber.</span></span>  
  
### <a name="subscriber-wins"></a><span data-ttu-id="a0887-152">サブスクライバー優先</span><span class="sxs-lookup"><span data-stu-id="a0887-152">Subscriber Wins</span></span>  
 <span data-ttu-id="a0887-153">サブスクライバー優先の方法による競合の検出は、パブリッシャー優先を更新した前回のサブスクライバー トランザクションを意味します。</span><span class="sxs-lookup"><span data-stu-id="a0887-153">Conflict detection under the Subscriber wins policy means the last Subscriber transaction to update the Publisher wins.</span></span> <span data-ttu-id="a0887-154">この場合、競合が検出されても、サブスクライバーによって送信されたトランザクションは引き続き使用され、パブリッシャーが更新されます。</span><span class="sxs-lookup"><span data-stu-id="a0887-154">In this case, when a conflict is detected, the transaction sent by the Subscriber is still used and the Publisher is updated.</span></span> <span data-ttu-id="a0887-155">そのような変更によってもデータの整合性が失われない場合には、サブスクライバー優先の方法が適しています。</span><span class="sxs-lookup"><span data-stu-id="a0887-155">This policy is suitable for applications where such changes do not compromise data integrity.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0887-156">参照</span><span class="sxs-lookup"><span data-stu-id="a0887-156">See Also</span></span>  
 [<span data-ttu-id="a0887-157">Updatable Subscriptions for Transactional Replication</span><span class="sxs-lookup"><span data-stu-id="a0887-157">Updatable Subscriptions for Transactional Replication</span></span>](updatable-subscriptions-for-transactional-replication.md)  
  
  
