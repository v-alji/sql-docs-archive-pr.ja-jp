---
title: レプリケーションサブスクライバーと AlwaysOn 可用性グループ (SQL Server) |Microsoft Docs
ms.custom: ''
ms.date: 01/16/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- failover subscribers with AlwaysOn
- Availability Groups [SQL Server], interoperability
- replication [SQL Server], AlwaysOn Availability Groups
ms.assetid: 0995f269-0580-43ed-b8bf-02b9ad2d7ee6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 449b5ac416f2ae86395c40a984678ed4258b3b85
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641869"
---
# <a name="replication-subscribers-and-alwayson-availability-groups-sql-server"></a><span data-ttu-id="1e117-102">レプリケーション サブスクライバーと AlwaysOn 可用性グループ (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="1e117-102">Replication Subscribers and AlwaysOn Availability Groups (SQL Server)</span></span>
  <span data-ttu-id="1e117-103">レプリケーション サブスクライバーであるデータベースを含む AlwaysOn 可用性グループがフェールオーバーすると、レプリケーション サブスクリプションが失敗することがあります。</span><span class="sxs-lookup"><span data-stu-id="1e117-103">When an AlwaysOn availability group containing a database that is a replication subscriber fails over, the replication subscription might fail.</span></span> <span data-ttu-id="1e117-104">トランザクション レプリケーションのプッシュ サブスクライバーの場合、サブスクリプションが AG リスナー名を使用して作成されていれば、フェールオーバー後にディストリビューション エージェントは自動的にレプリケーションを継続します。</span><span class="sxs-lookup"><span data-stu-id="1e117-104">For transactional replication push subscribers, the distribution agent will continue to replicate automatically after a failover if the subscription was created using the AG listener name.</span></span> <span data-ttu-id="1e117-105">トランザクション レプリケーションのプル サブスクライバーの場合、サブスクリプションが AG リスナー名を使用して作成されており、元のサブスクライバー サーバーが稼働中であれば、フェールオーバー後にディストリビューション エージェントは自動的にレプリケーションを継続します。</span><span class="sxs-lookup"><span data-stu-id="1e117-105">For transactional replication pull subscribers, the distribution agent will continue to replicate automatically after a failover, if the subscription was created using the AG listener name and the original subscriber server is up and running.</span></span> <span data-ttu-id="1e117-106">これは、ディストリビューション エージェントのジョブは元のサブスクライバー (AG のプライマリ レプリカ) 上でのみ作成されるためです。</span><span class="sxs-lookup"><span data-stu-id="1e117-106">This is because the distribution agent jobs only get created on the original subscriber (primary replica of the AG).</span></span> <span data-ttu-id="1e117-107">マージ サブスクライバーの場合、レプリケーション管理者はサブスクリプションを再作成して、手動でサブスクライバーを再構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1e117-107">For merge subscribers, a replication administrator must manually reconfigure the subscriber, by recreating the subscription.</span></span>  
  
## <a name="what-is-supported"></a><span data-ttu-id="1e117-108">サポート対象</span><span class="sxs-lookup"><span data-stu-id="1e117-108">What is Supported</span></span>  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="1e117-109">レプリケーションは、パブリッシャーの自動フェールオーバー、トランザクション サブスクライバーの自動フェールオーバー、およびマージ サブスクライバーの手動フェールオーバーをサポートします。</span><span class="sxs-lookup"><span data-stu-id="1e117-109">replication supports the automatic failover of the publisher, the automatic failover of transactional subscribers, and the manual failover of merge subscribers.</span></span> <span data-ttu-id="1e117-110">可用性データベース上のディストリビューターのフェールオーバーはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="1e117-110">The failover of a distributor on an availability database is not supported.</span></span> <span data-ttu-id="1e117-111">AlwaysOn は、Websync および [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Compact のシナリオと組み合わせることはできません。</span><span class="sxs-lookup"><span data-stu-id="1e117-111">AlwaysOn cannot be combined with Websync and [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Compact scenarios.</span></span>  
  
 <span data-ttu-id="1e117-112">**マージ プル サブスクリプションのフェールオーバー**</span><span class="sxs-lookup"><span data-stu-id="1e117-112">**Failover of a Merge Pull Subscription**</span></span>  
  
 <span data-ttu-id="1e117-113">可用性グループのフェールオーバー時のプル サブスクリプションは失敗します。これは、サーバー インスタンスの障害によってプライマリ レプリカが使用できなくなっており、プライマリ レプリカをホストするサーバー インスタンスの **msdb** データベースに格納されたジョブをプル エージェントが見つけることができないためです。</span><span class="sxs-lookup"><span data-stu-id="1e117-113">A pull subscription fails upon availability group failover, because pull agent cannot find the jobs stored in the **msdb** database of the server instance that hosts the primary replica; which is not available because the server instance has failed.</span></span>  
  
 <span data-ttu-id="1e117-114">**マージ プッシュ サブスクリプションのフェールオーバー**</span><span class="sxs-lookup"><span data-stu-id="1e117-114">**Failover of a Merge Push Subscription**</span></span>  
  
 <span data-ttu-id="1e117-115">可用性グループのフェールオーバー時のプッシュ サブスクリプションは失敗します。これは、プッシュ エージェントが元のサブスクライバーの元のサブスクリプション データベースに接続できなくなっているためです。</span><span class="sxs-lookup"><span data-stu-id="1e117-115">A push subscription fails upon availability group failover, because the push agent can no longer connect to original subscription database on original subscriber.</span></span>  
  
## <a name="how-to-create-transactional-subscription-in-an-alwayson-environment"></a><span data-ttu-id="1e117-116">AlwaysOn 環境でトランザクション サブスクリプションを作成する方法</span><span class="sxs-lookup"><span data-stu-id="1e117-116">How to Create Transactional Subscription in an AlwaysOn Environment</span></span>  
 <span data-ttu-id="1e117-117">トランザクション レプリケーションの場合、サブスクライバーの可用性グループを構成およびフェールオーバーするために、次の手順を使用します。</span><span class="sxs-lookup"><span data-stu-id="1e117-117">For transactional replication, use the following steps to configure and failover a subscriber availability group:</span></span>  
  
1.  <span data-ttu-id="1e117-118">サブスクリプションを作成する前に、適切な AlwaysOn 可用性グループにサブスクライバー データベースを追加します。</span><span class="sxs-lookup"><span data-stu-id="1e117-118">Before creating the subscription, add the subscriber database to the appropriate AlwaysOn availability group.</span></span>  
  
2.  <span data-ttu-id="1e117-119">サブスクライバーの可用性グループ リスナーを、可用性グループ内のすべてのノードにリンク サーバーとして追加します。</span><span class="sxs-lookup"><span data-stu-id="1e117-119">Add the subscriber's availability group Listener as a linked server to all nodes of the availability group.</span></span> <span data-ttu-id="1e117-120">この手順により、すべての潜在的なフェールオーバー パートナーがそのリスナーを認識し、そのリスナーに接続できるようになります。</span><span class="sxs-lookup"><span data-stu-id="1e117-120">This step ensures that all potential failover partners are aware of and can connect to the listener.</span></span>  
  
3.  <span data-ttu-id="1e117-121">以下の「 **トランザクション レプリケーションのプッシュ サブスクリプションの作成** 」セクションのスクリプトを使用して、サブスクライバーの可用性グループ リスナーの名前を使用するサブスクリプションを作成します。</span><span class="sxs-lookup"><span data-stu-id="1e117-121">Using the script in the **Creating a Transactional Replication Push Subscription** section below, create the subscription using the name of the availability group listener of the subscriber.</span></span> <span data-ttu-id="1e117-122">フェールオーバー後、リスナー名は常に有効になるのに対し、サブスクライバーの実際のサーバー名は、新しいプライマリになった実際のノードによって異なります。</span><span class="sxs-lookup"><span data-stu-id="1e117-122">After a failover, the listener name will always remain valid, whereas the actual server name of the subscriber will depend on the actual node that became the new primary.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="1e117-123">サブスクリプションは [!INCLUDE[tsql](../../../includes/tsql-md.md)] スクリプトを使用して作成する必要があります。 [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]を使用して作成できません。</span><span class="sxs-lookup"><span data-stu-id="1e117-123">The subscription must be created by using a [!INCLUDE[tsql](../../../includes/tsql-md.md)] script and cannot be created using [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)].</span></span>  
  
4.  <span data-ttu-id="1e117-124">プル サブスクリプションを作成する場合:</span><span class="sxs-lookup"><span data-stu-id="1e117-124">If creating a pull subscription:</span></span>  
  
    1.  <span data-ttu-id="1e117-125">[!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]のプライマリ サブスクライバー ノードで、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] エージェント ツリーを開きます。</span><span class="sxs-lookup"><span data-stu-id="1e117-125">In [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)], on the primary subscriber node, open the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent tree.</span></span>  
  
    2.  <span data-ttu-id="1e117-126">**プル ディストリビューション エージェント** ジョブを識別し、そのジョブを編集します。</span><span class="sxs-lookup"><span data-stu-id="1e117-126">Identify the **Pull Distribution Agent** job and edit the job.</span></span>  
  
    3.  <span data-ttu-id="1e117-127">**[エージェントを実行します]** ジョブ ステップで、 `-Publisher` と `-Distributor` の各パラメーターを確認します。</span><span class="sxs-lookup"><span data-stu-id="1e117-127">On the **Run Agent** job step, check the `-Publisher` and `-Distributor` parameters.</span></span> <span data-ttu-id="1e117-128">これらのパラメーターに適切な直接サーバーと、パブリッシャーおよびディストリビューター サーバーのインスタンス名が含まれていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="1e117-128">Make sure that these parameters contain the correct direct server and instance names of the publisher and distributor server.</span></span>  
  
    4.  <span data-ttu-id="1e117-129">`-Subscriber` パラメーターを、サブスクライバーの可用性グループ リスナーの名前に変更します。</span><span class="sxs-lookup"><span data-stu-id="1e117-129">Change the `-Subscriber` parameter to the subscriber's availability group listener name.</span></span>  
  
 <span data-ttu-id="1e117-130">この手順に従ってサブスクリプションを作成した場合、フェールオーバー後には何もする必要がありません。</span><span class="sxs-lookup"><span data-stu-id="1e117-130">When you create your subscription following these steps, then you won't have to do anything after a failover.</span></span>  
  
## <a name="creating-a-transactional-replication-push-subscription"></a><span data-ttu-id="1e117-131">トランザクション レプリケーションのプッシュ サブスクリプションの作成</span><span class="sxs-lookup"><span data-stu-id="1e117-131">Creating a Transactional Replication Push Subscription</span></span>  
  
```  
-- commands to execute at the publisher, in the publisher database:  
use [<publisher database name>]  
EXEC sp_addsubscription @publication = N'<publication name>',   
       @subscriber = N'<availability group listener name>',   
       @destination_db = N'<subscriber database name>',   
       @subscription_type = N'Push',   
       @sync_type = N'automatic', @article = N'all', @update_mode = N'read only', @subscriber_type = 0;  
GO  
  
EXEC sp_addpushsubscription_agent @publication = N'<publication name>',   
       @subscriber = N'<availability group listener name>',   
       @subscriber_db = N'<subscriber database name>',   
       @job_login = null, @job_password = null, @subscriber_security_mode = 1;  
GO  
```  
  
## <a name="to-resume-the-merge-agents-after-the-availability-group-of-the-subscriber-fails-over"></a><span data-ttu-id="1e117-132">サブスクライバーの可用性グループがフェールオーバーした後で、マージ エージェントを再開するには</span><span class="sxs-lookup"><span data-stu-id="1e117-132">To Resume the Merge Agents After the Availability Group of the Subscriber Fails Over</span></span>  
 <span data-ttu-id="1e117-133">マージ レプリケーションでは、レプリケーション管理者が次の手順に従い、手動でサブスクライバーを再構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1e117-133">For merge replication, a replication administrator must manually reconfigure the subscriber with the following steps:</span></span>  
  
1.  <span data-ttu-id="1e117-134">`sp_subscription_cleanup` を実行し、サブスクライバーの古いサブスクリプションを削除します。</span><span class="sxs-lookup"><span data-stu-id="1e117-134">Execute `sp_subscription_cleanup` to remove the old subscription for the subscriber.</span></span> <span data-ttu-id="1e117-135">この操作は、新しいプライマリ レプリカ (以前のセカンダリ レプリカ) で実行します。</span><span class="sxs-lookup"><span data-stu-id="1e117-135">Perform this action on the new primary replica (which was formerly the secondary replica).</span></span>  
  
2.  <span data-ttu-id="1e117-136">新しいサブスクリプションを作成し、新しいスナップショットから開始して、サブスクリプションを再作成します。</span><span class="sxs-lookup"><span data-stu-id="1e117-136">Recreate the subscription by creating a new subscription, beginning with a new snapshot.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1e117-137">現在のプロセスはマージ レプリケーションのサブスクライバーには不便ですが、マージ レプリケーションの主なシナリオは、サブスクライバーで AlwaysOn 可用性グループを使用しない未接続のユーザー (デスクトップ、ラップトップ、携帯端末) です。</span><span class="sxs-lookup"><span data-stu-id="1e117-137">The current process is inconvenient for merge replication subscribers, however the main scenario for merge replication is disconnected users (desktops, laptops, handset devices) which will not use AlwaysOn availability groups on the subscriber.</span></span>  
  
  
