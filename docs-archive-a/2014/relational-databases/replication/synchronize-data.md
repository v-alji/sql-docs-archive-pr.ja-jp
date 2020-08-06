---
title: データの同期 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- synchronization [SQL Server replication], about synchronization
- merge replication synchronization [SQL Server replication]
- scripts [SQL Server replication], synchronization and
- synchronization [SQL Server replication]
- snapshot replication [SQL Server], synchronization
- transactional replication, synchronization
- subscriptions [SQL Server replication], synchronizing
- on demand script execution
- replication [SQL Server], synchronization
- scripts [SQL Server replication]
ms.assetid: 724802f7-7d69-46d3-a330-bd8aa7f53114
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c92cc4d1ae8e836f169a731ecf3c37c81f3dbf10
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716230"
---
# <a name="synchronize-data"></a><span data-ttu-id="17dab-102">データの同期</span><span class="sxs-lookup"><span data-stu-id="17dab-102">Synchronize Data</span></span>
  <span data-ttu-id="17dab-103">データの同期とは、初期スナップショットをサブスクライバーで適用した後に、パブリッシャーとサブスクライバーの間でデータとスキーマ変更を反映する処理のことです。</span><span class="sxs-lookup"><span data-stu-id="17dab-103">Synchronizing data refers to the process of data and schema changes being propagated between the Publisher and Subscribers after the initial snapshot has been applied at the Subscriber.</span></span> <span data-ttu-id="17dab-104">同期は、次のように実行されます。</span><span class="sxs-lookup"><span data-stu-id="17dab-104">Synchronization can occur:</span></span>  
  
-   <span data-ttu-id="17dab-105">連続して実行。これは通常、トランザクション レプリケーションの場合です。</span><span class="sxs-lookup"><span data-stu-id="17dab-105">Continuously, which is typical for transactional replication.</span></span>  
  
-   <span data-ttu-id="17dab-106">要求時に実行。これは通常、マージ レプリケーションの場合です。</span><span class="sxs-lookup"><span data-stu-id="17dab-106">On demand, which is typical for merge replication.</span></span>  
  
-   <span data-ttu-id="17dab-107">スケジュールに基づいて実行。これは通常、スナップショット レプリケーションの場合です。</span><span class="sxs-lookup"><span data-stu-id="17dab-107">On a schedule, which is typical for snapshot replication.</span></span>  
  
 <span data-ttu-id="17dab-108">サブスクリプションが同期されると、使用しているレプリケーションの種類に基づいて異なる処理が実行されます。</span><span class="sxs-lookup"><span data-stu-id="17dab-108">When a subscription is synchronized, different processes occur based on the type of replication you are using:</span></span>  
  
-   <span data-ttu-id="17dab-109">スナップショット レプリケーション。</span><span class="sxs-lookup"><span data-stu-id="17dab-109">Snapshot replication.</span></span> <span data-ttu-id="17dab-110">同期とは、ディストリビューション エージェントがサブスクライバーでスナップショットを再適用して、サブスクリプション データベースのスキーマおよびデータがパブリケーション データベースとの一貫性を持つようにすることを意味します。</span><span class="sxs-lookup"><span data-stu-id="17dab-110">Synchronization means that the Distribution Agent reapplies the snapshot at the Subscriber so that schema and data at the subscription database is consistent with the publication database.</span></span>  
  
     <span data-ttu-id="17dab-111">データまたはスキーマへの変更がパブリッシャーで行われている場合、サブスクライバーに変更を反映させるために、新しいスナップショットを生成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="17dab-111">If modifications to data or schema have been made at the Publisher, a new snapshot must be generated in order to propagate modifications to the Subscriber.</span></span>  
  
-   <span data-ttu-id="17dab-112">トランザクション レプリケーション。</span><span class="sxs-lookup"><span data-stu-id="17dab-112">Transactional replication.</span></span> <span data-ttu-id="17dab-113">同期とは、ディストリビューション エージェントが更新、挿入、削除、およびその他の変更をディストリビューション データベースからサブスクライバーに転送することを意味します。</span><span class="sxs-lookup"><span data-stu-id="17dab-113">Synchronization means that the Distribution Agent transfers updates, inserts, deletes, and any other changes from the distribution database to the Subscriber.</span></span>  
  
-   <span data-ttu-id="17dab-114">マージ レプリケーション。</span><span class="sxs-lookup"><span data-stu-id="17dab-114">Merge replication.</span></span> <span data-ttu-id="17dab-115">同期とは、マージ エージェントがサブスクライバーからパブリッシャーに変更をアップロードし、パブリッシャーからサブスクライバーに変更をダウンロードすることを意味します。</span><span class="sxs-lookup"><span data-stu-id="17dab-115">Synchronization means that the Merge Agent uploads changes from the Subscriber to the Publisher and then downloads changes from the Publisher to the Subscriber.</span></span> <span data-ttu-id="17dab-116">競合が存在する場合は、検出されて解決されます。</span><span class="sxs-lookup"><span data-stu-id="17dab-116">Conflicts, if any, are detected and resolved.</span></span> <span data-ttu-id="17dab-117">データは集約され、最終的にパブリッシャーとすべてのサブスクライバーでデータ値が同じになります。</span><span class="sxs-lookup"><span data-stu-id="17dab-117">Data is converged, and the Publisher and all Subscribers eventually end up with the same data values.</span></span> <span data-ttu-id="17dab-118">競合が検出されて解決された場合、一部のユーザーがコミットした作業は、定義されたポリシーに応じて、競合が解決するように変更されます。</span><span class="sxs-lookup"><span data-stu-id="17dab-118">If conflicts were detected and resolved, work that was committed by some of the users is changed to resolve the conflict according to policies you define.</span></span>  
  
 <span data-ttu-id="17dab-119">スナップショット パブリケーションでは、同期が発生するたびに、サブスクライバーでスキーマが完全に更新されます。そのため、すべてのスキーマ変更がサブスクライバーに適用されます。</span><span class="sxs-lookup"><span data-stu-id="17dab-119">Snapshot publications completely refresh the schema at the Subscriber every time synchronization occurs, so all schema changes are applied to the Subscriber.</span></span> <span data-ttu-id="17dab-120">トランザクション レプリケーションとマージ レプリケーションでも、最も一般的なスキーマ変更がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="17dab-120">Transactional replication and merge replication also support the most common schema changes.</span></span> <span data-ttu-id="17dab-121">詳細については、「[パブリケーション データベースでのスキーマの変更](publish/make-schema-changes-on-publication-databases.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="17dab-121">For more information, see [Make Schema Changes on Publication Databases](publish/make-schema-changes-on-publication-databases.md).</span></span>  
  
 <span data-ttu-id="17dab-122">プッシュ サブスクリプションを同期するには、「[Synchronize a Push Subscription](synchronize-a-push-subscription.md)」 (プッシュ サブスクリプションの同期) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="17dab-122">To synchronize a push subscription, see [Synchronize a Push Subscription](synchronize-a-push-subscription.md).</span></span>  
  
 <span data-ttu-id="17dab-123">プル サブスクリプションを同期するには、「[Synchronize a Pull Subscription](synchronize-a-pull-subscription.md)」 (プル サブスクリプションの同期) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="17dab-123">To synchronize a pull subscription, see [Synchronize a Pull Subscription](synchronize-a-pull-subscription.md).</span></span>  
  
 <span data-ttu-id="17dab-124">同期のスケジュールを設定するには、「 [Specify Synchronization Schedules](specify-synchronization-schedules.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="17dab-124">To set synchronization schedules, see [Specify Synchronization Schedules](specify-synchronization-schedules.md).</span></span>  
  
 <span data-ttu-id="17dab-125">**同期の競合を表示および解決するには**</span><span class="sxs-lookup"><span data-stu-id="17dab-125">**To view and resolve synchronization conflicts**</span></span>  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]<span data-ttu-id="17dab-126">:[マージ パブリケーションでのデータの競合の表示および解決 &#40;SQL Server Management Studio&#41;](view-and-resolve-data-conflicts-for-merge-publications.md)</span><span class="sxs-lookup"><span data-stu-id="17dab-126">: [View and Resolve Data Conflicts for Merge Publications &#40;SQL Server Management Studio&#41;](view-and-resolve-data-conflicts-for-merge-publications.md)</span></span>  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]<span data-ttu-id="17dab-127">:[トランザクション パブリケーションのデータの競合の表示 &#40;SQL Server Management Studio&#41;](view-data-conflicts-for-transactional-publications-sql-server-management-studio.md)</span><span class="sxs-lookup"><span data-stu-id="17dab-127">: [View Data Conflicts for Transactional Publications &#40;SQL Server Management Studio&#41;](view-data-conflicts-for-transactional-publications-sql-server-management-studio.md)</span></span>  
  
## <a name="executing-code-during-synchronization"></a><span data-ttu-id="17dab-128">同期中のコード実行</span><span class="sxs-lookup"><span data-stu-id="17dab-128">Executing Code During Synchronization</span></span>  
 <span data-ttu-id="17dab-129">レプリケーションでは、同期中にコードを実行する方法が 2 つサポートされています。</span><span class="sxs-lookup"><span data-stu-id="17dab-129">Replication supports two methods of executing code during synchronization</span></span>  
  
-   <span data-ttu-id="17dab-130">要求時スクリプト実行は、トランザクション レプリケーションおよびマージ レプリケーションでサポートされています。</span><span class="sxs-lookup"><span data-stu-id="17dab-130">On demand script execution is supported for transactional replication and merge replication.</span></span> <span data-ttu-id="17dab-131">要求時スクリプト実行を使用すると、同期中に実行する SQL スクリプトを指定できます。</span><span class="sxs-lookup"><span data-stu-id="17dab-131">Using on demand script execution you can specify a SQL script to run during synchronization.</span></span> <span data-ttu-id="17dab-132">スクリプトはサブスクライバーにコピーされ、同期処理の開始時に **sqlcmd** を使用して実行されます。</span><span class="sxs-lookup"><span data-stu-id="17dab-132">The script is copied to the Subscriber and executed using **sqlcmd** at the beginning of the synchronization process.</span></span> <span data-ttu-id="17dab-133">スクリプトは、レプリケートされた変更をサブスクライバーに適用するときに、それらの変更へはアクセスしません。</span><span class="sxs-lookup"><span data-stu-id="17dab-133">The script does not have access to the replicated changes as they are applied to the Subscriber.</span></span> <span data-ttu-id="17dab-134">詳細については、「[同期中のスクリプトの実行 (レプリケーション Transact-SQL プログラミング)](execute-scripts-during-synchronization-replication-transact-sql-programming.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="17dab-134">For more information, see [Execute Scripts During Synchronization &#40;Replication Transact-SQL Programming&#41;](execute-scripts-during-synchronization-replication-transact-sql-programming.md).</span></span>  
  
-   <span data-ttu-id="17dab-135">ビジネス ロジック ハンドラーは、マージ レプリケーションでサポートされています。</span><span class="sxs-lookup"><span data-stu-id="17dab-135">Business logic handlers are supported for merge replication.</span></span> <span data-ttu-id="17dab-136">ビジネス ロジック ハンドラー フレームワークを使用すると、マネージド コードのアセンブリを記述して、マージ同期処理中に呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="17dab-136">Using the business logic handler framework you can write a managed code assembly that is called during the merge synchronization process.</span></span> <span data-ttu-id="17dab-137">このアセンブリには、データの変更、競合、およびエラーなど、同期中に発生するさまざまな状況に対処するためのビジネス ロジックを記述できます。</span><span class="sxs-lookup"><span data-stu-id="17dab-137">The assembly includes business logic that can respond to a number of conditions during synchronization: data changes, conflicts, and errors.</span></span> <span data-ttu-id="17dab-138">詳細については、「[Execute Business Logic During Merge Synchronization](merge/execute-business-logic-during-merge-synchronization.md)」(マージ同期中のビジネス ロジックの実行) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="17dab-138">For more information, see [Execute Business Logic During Merge Synchronization](merge/execute-business-logic-during-merge-synchronization.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17dab-139">参照</span><span class="sxs-lookup"><span data-stu-id="17dab-139">See Also</span></span>  
 [<span data-ttu-id="17dab-140">マージ レプリケーションの競合の検出と解決</span><span class="sxs-lookup"><span data-stu-id="17dab-140">Detect and Resolve Merge Replication Conflicts</span></span>](merge/advanced-merge-replication-conflict-detection-and-resolution.md)  
  
  
