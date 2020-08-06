---
title: パブリケーションのサブスクライブ | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.conc.subtopubs.f1
helpviewer_keywords:
- subscriptions [SQL Server replication], about subscriptions
- pull subscriptions [SQL Server replication]
- subscriptions [SQL Server replication]
- push subscriptions [SQL Server replication], about push subscriptions
- merge replication subscribing [SQL Server replication]
- merge replication subscribing [SQL Server replication], about subscribing
- publications [SQL Server replication], subscribing
- push subscriptions [SQL Server replication]
- pull subscriptions [SQL Server replication], about pull subscriptions
- snapshot replication [SQL Server], subscribing
- transactional replication, subscribing
ms.assetid: 088ee30a-05ab-47c4-92ed-316b93e12445
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c565aae26c6d549eb67043168797d5fb059c8e2a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631767"
---
# <a name="subscribe-to-publications"></a><span data-ttu-id="7a17f-102">パブリケーションのサブスクライブ</span><span class="sxs-lookup"><span data-stu-id="7a17f-102">Subscribe to Publications</span></span>
  <span data-ttu-id="7a17f-103">サブスクリプションとは、パブリケーションのデータとデータベース オブジェクトのコピーを要求することです。</span><span class="sxs-lookup"><span data-stu-id="7a17f-103">A subscription is a request for a copy of the data and database objects in a publication.</span></span> <span data-ttu-id="7a17f-104">サブスクリプションでは、受信するパブリケーションおよびパブリケーションの受信場所と受信時間が定義されます。</span><span class="sxs-lookup"><span data-stu-id="7a17f-104">A subscription defines which publication will be received, and where and when it will be received.</span></span> <span data-ttu-id="7a17f-105">サブスクリプションを設計する場合は、エージェント処理を実行する場所を考慮してください。</span><span class="sxs-lookup"><span data-stu-id="7a17f-105">When planning for subscriptions, consider where you want agent processing to occur.</span></span> <span data-ttu-id="7a17f-106">選択するサブスクリプションの種類によって、エージェントが実行される場所が決まります。</span><span class="sxs-lookup"><span data-stu-id="7a17f-106">The type of subscription you choose controls where the agent runs.</span></span> <span data-ttu-id="7a17f-107">プッシュ サブスクリプションではマージ エージェントまたはディストリビューション エージェントがディストリビューターで実行されるのに対し、プル サブスクリプションではサブスクライバーでエージェントが実行されます。</span><span class="sxs-lookup"><span data-stu-id="7a17f-107">With a push subscription, the Merge Agent or Distribution Agent runs at the Distributor, whereas with a pull subscription, agents run at the Subscribers.</span></span> <span data-ttu-id="7a17f-108">サブスクリプションの作成後にその種類を変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="7a17f-108">After a subscription is created, it cannot be changed from one type to another.</span></span>  
  
|<span data-ttu-id="7a17f-109">サブスクリプション</span><span class="sxs-lookup"><span data-stu-id="7a17f-109">Subscription</span></span>|<span data-ttu-id="7a17f-110">特性</span><span class="sxs-lookup"><span data-stu-id="7a17f-110">Characteristics</span></span>|<span data-ttu-id="7a17f-111">いつ使用するか</span><span class="sxs-lookup"><span data-stu-id="7a17f-111">Use When</span></span>|  
|------------------|---------------------|--------------|  
|<span data-ttu-id="7a17f-112">プッシュ サブスクリプション</span><span class="sxs-lookup"><span data-stu-id="7a17f-112">Push Subscription</span></span>|<span data-ttu-id="7a17f-113">プッシュ サブスクリプションでは、サブスクライバーからの要求なしにパブリッシャーが変更をサブスクライバーに反映します。</span><span class="sxs-lookup"><span data-stu-id="7a17f-113">With a push subscription, the Publisher propagates changes to a Subscriber without a request from the Subscriber.</span></span> <span data-ttu-id="7a17f-114">変更は、要求時、連続的、スケジュールのいずれかの方法に基づいて、サブスクライバーにプッシュできます。</span><span class="sxs-lookup"><span data-stu-id="7a17f-114">Changes can be pushed to Subscribers on demand, continuously, or on a scheduled basis.</span></span> <span data-ttu-id="7a17f-115">ディストリビューション エージェントまたはマージ エージェントはディストリビューターで実行されます。</span><span class="sxs-lookup"><span data-stu-id="7a17f-115">The Distribution Agent or Merge Agent runs at the Distributor.</span></span>|<span data-ttu-id="7a17f-116">連続的に、または定期的なスケジュールで頻繁にデータの同期をとる場合</span><span class="sxs-lookup"><span data-stu-id="7a17f-116">Data will typically be synchronized continuously or on a frequently recurring schedule.</span></span><br /><br /> <span data-ttu-id="7a17f-117">パブリケーションがほぼリアルタイムのデータの移動を必要とする場合</span><span class="sxs-lookup"><span data-stu-id="7a17f-117">Publications require near real-time movement of data.</span></span><br /><br /> <span data-ttu-id="7a17f-118">ディストリビューターのプロセッサのオーバーヘッドが高くなってもパフォーマンスに影響しない場合</span><span class="sxs-lookup"><span data-stu-id="7a17f-118">The higher processor overhead at the Distributor does not affect performance.</span></span><br /><br /> <span data-ttu-id="7a17f-119">スナップショット レプリケーションとトランザクション レプリケーションで最も頻繁に使用する場合</span><span class="sxs-lookup"><span data-stu-id="7a17f-119">Most often used with snapshot and transactional replication.</span></span>|  
|<span data-ttu-id="7a17f-120">プル サブスクリプション</span><span class="sxs-lookup"><span data-stu-id="7a17f-120">Pull Subscription</span></span>|<span data-ttu-id="7a17f-121">プル サブスクリプションでは、パブリッシャーで変更を行うようにサブスクライバーが要求します。</span><span class="sxs-lookup"><span data-stu-id="7a17f-121">With a pull subscription, the Subscriber requests changes made at the Publisher.</span></span> <span data-ttu-id="7a17f-122">プル サブスクリプションでは、サブスクライバーのユーザーがデータの変更をいつ同期するかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="7a17f-122">Pull subscriptions allow the user at the Subscriber to determine when the data changes are synchronized.</span></span> <span data-ttu-id="7a17f-123">ディストリビューション エージェントまたはマージ エージェントはサブスクライバーで実行されます。</span><span class="sxs-lookup"><span data-stu-id="7a17f-123">The Distribution Agent or the Merge Agent runs at the Subscriber.</span></span>|<span data-ttu-id="7a17f-124">連続的ではなく、要求時またはスケジュールに基づいてデータを同期する場合</span><span class="sxs-lookup"><span data-stu-id="7a17f-124">Data will typically be synchronized on demand or on a schedule rather than continuously.</span></span><br /><br /> <span data-ttu-id="7a17f-125">パブリケーションに多くのサブスクライバーがある場合、またはリソースの消費が大きすぎてディストリビューターですべてのエージェントを実行できない場合 (またはその両方)</span><span class="sxs-lookup"><span data-stu-id="7a17f-125">The publication has a large number of Subscribers, and/or it would be too resource-intensive to run all the agents at the Distributor.</span></span><br /><br /> <span data-ttu-id="7a17f-126">サブスクライバーが独立しているか、接続解除されているか、またはモバイルである場合。</span><span class="sxs-lookup"><span data-stu-id="7a17f-126">Subscribers are autonomous, disconnected, and/or mobile.</span></span> <span data-ttu-id="7a17f-127">サブスクライバーでは、いつ接続して変更を同期するかが決定されます。</span><span class="sxs-lookup"><span data-stu-id="7a17f-127">Subscribers will determine when they will connect and synchronize changes.</span></span><br /><br /> <span data-ttu-id="7a17f-128">マージ レプリケーションで最も頻繁に使用する場合</span><span class="sxs-lookup"><span data-stu-id="7a17f-128">Most often used with merge replication.</span></span>|  
  
## <a name="merge-replication-subscription-types"></a><span data-ttu-id="7a17f-129">マージ レプリケーション サブスクリプションの種類</span><span class="sxs-lookup"><span data-stu-id="7a17f-129">Merge Replication Subscription Types</span></span>  
 <span data-ttu-id="7a17f-130">すべての種類のレプリケーションでプッシュ サブスクリプションとプル サブスクリプションが使用できます。</span><span class="sxs-lookup"><span data-stu-id="7a17f-130">All replication types allow push and pull subscriptions.</span></span> <span data-ttu-id="7a17f-131">マージ レプリケーションでは、2 つのサブスクリプションを区別するために、クライアント サブスクリプションとサーバー サブスクリプションという語を使用します。</span><span class="sxs-lookup"><span data-stu-id="7a17f-131">Merge replication uses two additional terms to distinguish subscriptions: client subscriptions and server subscriptions.</span></span> <span data-ttu-id="7a17f-132">クライアント サブスクリプションとサーバー サブスクリプションのどちらの種類も、プッシュ サブスクリプションとプル サブスクリプションで使用できます。</span><span class="sxs-lookup"><span data-stu-id="7a17f-132">Both client and server subscription types can be used with push and pull subscriptions.</span></span> <span data-ttu-id="7a17f-133">クライアント サブスクリプションはほとんどのサブスクライバーに適していますが、サーバー サブスクリプションは通常、データを他のサブスクライバーに再パブリッシュするサブスクライバーで使用されます。</span><span class="sxs-lookup"><span data-stu-id="7a17f-133">Client subscriptions are appropriate for most Subscribers, whereas server subscriptions are typically used for Subscribers that republish data to other Subscribers.</span></span> <span data-ttu-id="7a17f-134">サブスクリプションの選択は、競合の解決にも影響します。</span><span class="sxs-lookup"><span data-stu-id="7a17f-134">Subscription choice also affects conflict resolution.</span></span>  
  
## <a name="non-sql-server-subscribers"></a><span data-ttu-id="7a17f-135">Non-SQL Server Subscribers</span><span class="sxs-lookup"><span data-stu-id="7a17f-135">Non-SQL Server Subscribers</span></span>  
 <span data-ttu-id="7a17f-136">Oracle および IBM DB2 は、プッシュ サブスクリプションを使用してスナップショット パブリケーションとトランザクション パブリケーションをサブスクライブできます。</span><span class="sxs-lookup"><span data-stu-id="7a17f-136">Oracle and IBM DB2 can subscribe to snapshot and transactional publications using push subscriptions.</span></span> <span data-ttu-id="7a17f-137">詳細については、「 [Non-SQL Server Subscribers](non-sql/non-sql-server-subscribers.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7a17f-137">For more information, see [Non-SQL Server Subscribers](non-sql/non-sql-server-subscribers.md).</span></span>  
  
## <a name="creating-subscriptions"></a><span data-ttu-id="7a17f-138">サブスクリプションの作成</span><span class="sxs-lookup"><span data-stu-id="7a17f-138">Creating Subscriptions</span></span>  
 <span data-ttu-id="7a17f-139">サブスクリプションを作成するには、次の情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="7a17f-139">To create a subscription, you supply the following information:</span></span>  
  
-   <span data-ttu-id="7a17f-140">パブリケーションの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="7a17f-140">The name of the publication.</span></span>  
  
-   <span data-ttu-id="7a17f-141">サブスクライバーとサブスクリプション データベースの名前</span><span class="sxs-lookup"><span data-stu-id="7a17f-141">The name of the Subscriber and the subscription database.</span></span>  
  
-   <span data-ttu-id="7a17f-142">ディストリビューション エージェントまたはマージ エージェントをディストリビューターとサブスクライバーのどちらで実行するか</span><span class="sxs-lookup"><span data-stu-id="7a17f-142">Whether the Distribution Agent or Merge Agent runs at the Distributor or at the Subscriber.</span></span>  
  
-   <span data-ttu-id="7a17f-143">ディストリビューション エージェントまたはマージ エージェントを、連続的、スケジュール、要求時のどの方法に基づいて実行するか</span><span class="sxs-lookup"><span data-stu-id="7a17f-143">Whether the Distribution Agent or Merge Agent runs continuously, on a scheduled basis, or on demand only.</span></span>  
  
-   <span data-ttu-id="7a17f-144">スナップショット エージェントがサブスクリプションの初期スナップショットを作成するかどうか、およびディストリビューション エージェントまたはマージ エージェントがそのスナップショットをサブスクライバーで適用するかどうか</span><span class="sxs-lookup"><span data-stu-id="7a17f-144">Whether the Snapshot Agent should create an initial snapshot for the subscription and whether the Distribution Agent or Merge Agent should apply that snapshot at the Subscriber.</span></span>  
  
-   <span data-ttu-id="7a17f-145">ディストリビューション エージェントまたはマージ エージェントを実行するときに使用するアカウント</span><span class="sxs-lookup"><span data-stu-id="7a17f-145">Accounts under which the Distribution Agent or Merge Agent will run.</span></span>  
  
-   <span data-ttu-id="7a17f-146">マージ レプリケーションの場合、サブスクリプションの種類はサーバーとクライアントです。</span><span class="sxs-lookup"><span data-stu-id="7a17f-146">For merge replication, the type of subscription: server or client.</span></span>  
  
 <span data-ttu-id="7a17f-147">**プッシュ サブスクリプションを作成するには**</span><span class="sxs-lookup"><span data-stu-id="7a17f-147">**To create a push subscription**</span></span>  
  
 [<span data-ttu-id="7a17f-148">プッシュ サブスクリプションを作成する</span><span class="sxs-lookup"><span data-stu-id="7a17f-148">Create a Push Subscription</span></span>](create-a-push-subscription.md)  
  
 <span data-ttu-id="7a17f-149">**プッシュ サブスクリプションのプロパティを表示または変更するには**</span><span class="sxs-lookup"><span data-stu-id="7a17f-149">**To view or modify push subscription properties**</span></span>  
  
 [<span data-ttu-id="7a17f-150">プッシュ サブスクリプションのプロパティの表示または変更</span><span class="sxs-lookup"><span data-stu-id="7a17f-150">View and Modify Push Subscription Properties</span></span>](view-and-modify-push-subscription-properties.md)  
  
 <span data-ttu-id="7a17f-151">**プッシュ サブスクリプションを削除するには**</span><span class="sxs-lookup"><span data-stu-id="7a17f-151">**To delete a push subscription**</span></span>  
  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]<span data-ttu-id="7a17f-152">:[プッシュ サブスクリプションの削除](delete-a-push-subscription.md)</span><span class="sxs-lookup"><span data-stu-id="7a17f-152">: [Delete a Push Subscription](delete-a-push-subscription.md)</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7a17f-153">サブスクリプションを削除しても、パブリッシュされたオブジェクトはサブスクライバーから削除されません。</span><span class="sxs-lookup"><span data-stu-id="7a17f-153">Deleting a subscription does not remove published objects from the Subscriber.</span></span>  
  
 <span data-ttu-id="7a17f-154">**プル サブスクリプションを作成するには**</span><span class="sxs-lookup"><span data-stu-id="7a17f-154">**To create a pull subscription**</span></span>  
  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]<span data-ttu-id="7a17f-155">:[Create a Pull Subscription](create-a-pull-subscription.md)</span><span class="sxs-lookup"><span data-stu-id="7a17f-155">: [Create a Pull Subscription](create-a-pull-subscription.md)</span></span>  
  
 <span data-ttu-id="7a17f-156">**プル サブスクリプションのプロパティを表示または変更するには**</span><span class="sxs-lookup"><span data-stu-id="7a17f-156">**To view or modify pull subscription properties**</span></span>  
  
 [<span data-ttu-id="7a17f-157">プル サブスクリプションのプロパティの表示または変更</span><span class="sxs-lookup"><span data-stu-id="7a17f-157">View and Modify Pull Subscription Properties</span></span>](view-and-modify-pull-subscription-properties.md)  
  
 <span data-ttu-id="7a17f-158">**プル サブスクリプションを削除するには**</span><span class="sxs-lookup"><span data-stu-id="7a17f-158">**To delete a pull subscription**</span></span>  
  
 [<span data-ttu-id="7a17f-159">プル サブスクリプションの削除</span><span class="sxs-lookup"><span data-stu-id="7a17f-159">Delete a Pull Subscription</span></span>](delete-a-pull-subscription.md)  
  
## <a name="see-also"></a><span data-ttu-id="7a17f-160">参照</span><span class="sxs-lookup"><span data-stu-id="7a17f-160">See Also</span></span>  
 <span data-ttu-id="7a17f-161">[サブスクライバーのセキュリティ保護](security/secure-the-subscriber.md) </span><span class="sxs-lookup"><span data-stu-id="7a17f-161">[Secure the Subscriber](security/secure-the-subscriber.md) </span></span>  
 [<span data-ttu-id="7a17f-162">サブスクリプションの有効期限と非アクティブ化</span><span class="sxs-lookup"><span data-stu-id="7a17f-162">Subscription Expiration and Deactivation</span></span>](subscription-expiration-and-deactivation.md)  
  
  
