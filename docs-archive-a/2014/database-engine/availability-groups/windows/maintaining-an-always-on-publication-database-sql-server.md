---
title: AlwaysOn パブリケーションデータベースのメンテナンス (SQL Server) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], interoperability
- replication [SQL Server], AlwaysOn Availability Groups
ms.assetid: 55b345fe-2eb9-4b04-a900-63d858eec360
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e8f36d29049140b6e5bbdfc1a4e716d41a766a06
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640227"
---
# <a name="maintaining-an-alwayson-publication-database-sql-server"></a><span data-ttu-id="b23b4-102">AlwaysOn パブリケーション データベースのメンテナンス (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="b23b4-102">Maintaining an AlwaysOn Publication Database (SQL Server)</span></span>
  <span data-ttu-id="b23b4-103">このトピックでは、AlwaysOn 可用性グループを使用するときのパブリケーション データベースのメンテナンスについての特別な考慮事項について説明します。</span><span class="sxs-lookup"><span data-stu-id="b23b4-103">This topic discusses special considerations for maintaining a publication database when you use AlwaysOn availability groups.</span></span>  
  
 
  
##  <a name="maintaining-a-published-database-in-an-availability-group"></a><a name="MaintainPublDb"></a><span data-ttu-id="b23b4-104">可用性グループでのパブリッシュされたデータベースのメンテナンス</span><span class="sxs-lookup"><span data-stu-id="b23b4-104">Maintaining a Published Database in an Availability Group</span></span>  
 <span data-ttu-id="b23b4-105">AlwaysOn パブリケーション データベースのメンテナンスは、通常のパブリケーション データベースのメンテナンスと基本的に同じです。ただし、次の点を考慮する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b23b4-105">Maintaining an AlwaysOn publication database is basically the same as maintaining a standard publication database, with the following considerations:</span></span>  
  
-   <span data-ttu-id="b23b4-106">管理は、プライマリ レプリカ ホストで行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="b23b4-106">Administration must occur at the primary replica host.</span></span> <span data-ttu-id="b23b4-107">[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]では、プライマリ レプリカ ホストと読み取り可能なセカンダリ レプリカの **[ローカル パブリケーション]** フォルダーにパブリケーションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b23b4-107">In [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], publications appear under the **Local Publications** folder for the primary replica host and also for readable secondary replicas.</span></span> <span data-ttu-id="b23b4-108">フェールオーバー後、プライマリに昇格したセカンダリが読み取り不可である場合は、変更を反映させるために [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] を手動で更新する必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="b23b4-108">After failover, you might have to manually refresh [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] for the change to be reflected if the secondary that was promoted to primary was not readable.</span></span>  
  
-   <span data-ttu-id="b23b4-109">レプリケーション モニターは、常に元のパブリッシャーの下でパブリケーション情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="b23b4-109">Replication Monitor always displays publication information under the original publisher.</span></span> <span data-ttu-id="b23b4-110">ただし、元のパブリッシャーをサーバーとして追加することで、この情報を任意のレプリカからレプリケーション モニターで表示することができます。</span><span class="sxs-lookup"><span data-stu-id="b23b4-110">However, this information can be viewed in Replication Monitor from any replica by adding the original publisher as a server.</span></span>  
  
-   <span data-ttu-id="b23b4-111">ストアド プロシージャまたはレプリケーション管理オブジェクト (RMO) を使用して現在のプライマリでレプリケーションを管理する場合、パブリッシャー名を指定する際には、データベースのレプリケーションを有効にしたインスタンス (元のパブリッシャー) の名前を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b23b4-111">When using stored procedures or Replication Management Objects (RMO) to administer replication at the current primary, for cases in which you specify the Publisher name, you must specify the name of the instance on which the database was enabled for replication (the original publisher).</span></span> <span data-ttu-id="b23b4-112">適切な名前を決定するには、`PUBLISHINGSERVERNAME` 関数を使用します。</span><span class="sxs-lookup"><span data-stu-id="b23b4-112">To determine the appropriate name, use the `PUBLISHINGSERVERNAME` function.</span></span> <span data-ttu-id="b23b4-113">パブリッシング データベースを可用性グループに参加させると、セカンダリ データベース レプリカに格納されているレプリケーション メタデータは、プライマリにあるレプリケーション メタデータと同一になります。</span><span class="sxs-lookup"><span data-stu-id="b23b4-113">When a publishing database joins an availability group, the replication metadata stored in the secondary database replicas is identical to that at the primary.</span></span> <span data-ttu-id="b23b4-114">その結果、プライマリでレプリケーションが有効なパブリケーション データベースでは、セカンダリのシステム テーブルに格納されるパブリッシャー インスタンス名は、セカンダリではなくプライマリの名前になります。</span><span class="sxs-lookup"><span data-stu-id="b23b4-114">Consequently, for publication databases enabled for replication at the primary, the publisher instance name stored in system tables at the secondary is the name of the primary, not the secondary.</span></span> <span data-ttu-id="b23b4-115">これにより、パブリケーション データベースがセカンダリにフェールオーバーした場合に、レプリケーションの構成およびメンテナンスに影響が出ます。</span><span class="sxs-lookup"><span data-stu-id="b23b4-115">This affects replication configuration and maintenance if the publication database fails over to a secondary.</span></span> <span data-ttu-id="b23b4-116">たとえば、フェールオーバー後にセカンダリでストアドプロシージャを使用してレプリケーションを構成していて、別のレプリカで有効にされたパブリケーションデータベースに対するプルサブスクリプションが必要な場合、またはのパラメーターとして、現在のパブリッシャーではなく元のパブリッシャーの名前を指定する必要があり *@publisher* `sp_addpullsubscription` `sp_addmergepulllsubscription` ます。</span><span class="sxs-lookup"><span data-stu-id="b23b4-116">For example, if you are configuring replication with stored procedures at a secondary after failover, and you want a pull subscription to a publication database that was enabled at a different replica, you must specify the name of the original publisher instead of the current publisher as the *@publisher* parameter of `sp_addpullsubscription` or `sp_addmergepulllsubscription`.</span></span> <span data-ttu-id="b23b4-117">ただし、フェールオーバー後にパブリケーション データベースを有効にした場合、システム テーブルに格納されるパブリッシャー インスタンス名は、現在のプライマリ ホストの名前になります。</span><span class="sxs-lookup"><span data-stu-id="b23b4-117">However, if you enable a publication database after failover, the publisher instance name stored in the system tables is the name of the current primary host.</span></span> <span data-ttu-id="b23b4-118">この場合は、パラメーターに現在のプライマリレプリカのホスト名を使用し *@publisher* ます。</span><span class="sxs-lookup"><span data-stu-id="b23b4-118">In this case, you would use the host name of the current primary replica for the *@publisher* parameter.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b23b4-119">などの一部のプロシージャでは、 `sp_addpublication` *@publisher* パラメーターはのインスタンスではないパブリッシャーに対してのみサポートされます [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。このような場合、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] AlwaysOn には関係ありません。</span><span class="sxs-lookup"><span data-stu-id="b23b4-119">For some procedures, such as `sp_addpublication`, the *@publisher* parameter is supported only for publishers that are not instances of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]; in these cases, it is not relevant for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] AlwaysOn.</span></span>  
  
-   <span data-ttu-id="b23b4-120">フェールオーバー後に [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] でサブスクリプションを同期するには、サブスクライバーからプル サブスクリプションを同期し、アクティブなパブリッシャーからプッシュ サブスクリプションを同期します。</span><span class="sxs-lookup"><span data-stu-id="b23b4-120">To synchronize a subscription in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] after a failover, synchronize pull subscriptions from the subscriber and synchronize push subscriptions from the active publisher.</span></span>  
  
##  <a name="removing-a-published-database-from-an-availability-group"></a><a name="RemovePublDb"></a> <span data-ttu-id="b23b4-121">可用性グループからのパブリッシュされたデータベースの削除</span><span class="sxs-lookup"><span data-stu-id="b23b4-121">Removing a Published Database from an Availability Group</span></span>  
 <span data-ttu-id="b23b4-122">パブリッシュされたデータベースを可用性グループから削除する場合、またはパブリッシュされたメンバー データベースを含む可用性グループを削除する場合、次の点を考慮します。</span><span class="sxs-lookup"><span data-stu-id="b23b4-122">Consider the following issues if a published database is removed from an availability group, or if an availability group that has a published member database is dropped.</span></span>  
  
-   <span data-ttu-id="b23b4-123">元のパブリッシャーのパブリケーションデータベースを可用性グループのプライマリレプリカから削除する場合は、 `sp_redirect_publisher` *@redirected_publisher* パブリッシャー/データベースペアのリダイレクトを削除するために、パラメーターの値を指定せずにを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b23b4-123">If the publication database at the original publisher is removed from an availability group primary replica, you must run `sp_redirect_publisher` without specifying a value for the *@redirected_publisher* parameter in order to remove the redirection for the publisher/database pair.</span></span>  
  
    ```  
    EXEC sys.sp_redirect_publisher   
        @original_publisher = 'MyPublisher',  
        @published_database = 'MyPublishedDB';  
    ```  
  
     <span data-ttu-id="b23b4-124">データベースはプライマリで復旧中の状態のままとなり、復元する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b23b4-124">The database will be left in the recovering state at the primary and must be restored.</span></span> <span data-ttu-id="b23b4-125">データベースを復元すると、レプリケーションは元のパブリッシャーに対して変更なしで動作します。</span><span class="sxs-lookup"><span data-stu-id="b23b4-125">Once you do this, replication should work unchanged against the original Publisher.</span></span>  
  
-   <span data-ttu-id="b23b4-126">パブリケーション データベースが元のパブリッシャーからレプリカにフェールオーバーし、そのパブリケーション データベースを可用性グループのプライマリ レプリカから削除した場合、ストアド プロシージャ `sp_redirect_publisher` を使用して元のパブリッシャーを新しいパブリッシャーに明示的にリダイレクトします。</span><span class="sxs-lookup"><span data-stu-id="b23b4-126">If the publication database fails over from the original publisher to a replica and the database is removed from the availability group primary replica, use the stored procedure `sp_redirect_publisher` to explicitly redirect the original publisher to the new publisher.</span></span> <span data-ttu-id="b23b4-127">データベースは復旧中の状態のままとなり、復元する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b23b4-127">The database will be left in the recovering state and must be restored.</span></span> <span data-ttu-id="b23b4-128">データベースを復元すると、レプリケーションは可用性グループの下で引き続き機能します。</span><span class="sxs-lookup"><span data-stu-id="b23b4-128">Once you do this, replication should continue to work as it did under the availability group.</span></span>  
  
    ```  
    EXEC sys.sp_redirect_publisher   
        @original_publisher = 'MyPublisher',  
        @published_database = 'MyPublishedDB',  
        @redirected_publisher = 'MyNewPublisher';  
    ```  
  
     <span data-ttu-id="b23b4-129">元のパブリッシャーのリモート サーバーは、以降にアクセスできなくなる場合でもディストリビューターから削除しないでください。</span><span class="sxs-lookup"><span data-stu-id="b23b4-129">Do not remove the remote server for the original publisher from the distributor, even if the server can no longer be accessed.</span></span> <span data-ttu-id="b23b4-130">ディストリビューターでパブリケーション メタデータ クエリに対応するために、元のパブリッシャーのサーバー メタデータが必要です。</span><span class="sxs-lookup"><span data-stu-id="b23b4-130">The server metadata for the original publisher is needed at the distributor to satisfy publication metadata queries.</span></span>  
  
-   <span data-ttu-id="b23b4-131">可用性グループ全体を削除した場合、メンバーであるレプリケートされたデータベースについての動作は、パブリッシュされたデータベースを可用性グループから削除した場合と同じです。</span><span class="sxs-lookup"><span data-stu-id="b23b4-131">If a complete availability group is removed, the behavior with regard to a member replicated database is the same as when a published database is removed from an availability group.</span></span> <span data-ttu-id="b23b4-132">データベースを復元し、リダイレクトを変更すると、レプリケーションを最後のプライマリから再開できます。</span><span class="sxs-lookup"><span data-stu-id="b23b4-132">Replication can be resumed from the last primary as soon as the database has been restored and the redirection has been modified.</span></span> <span data-ttu-id="b23b4-133">データベースを元のパブリッシャーで復元した場合、リダイレクトを削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b23b4-133">If the database is restored at its original publisher, redirection should be removed.</span></span> <span data-ttu-id="b23b4-134">データベースを別のホストで復元した場合、新しいホストに対してリダイレクトを明示的に指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b23b4-134">If the database is restored at a different host, redirection should be explicitly directed to the new host.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b23b4-135">メンバー データベースをパブリッシュした可用性グループを削除した場合、またはパブリッシュされたデータベースを可用性グループから削除した場合、パブリッシュされたデータベースのすべてのコピーは復旧中の状態のままとなります。</span><span class="sxs-lookup"><span data-stu-id="b23b4-135">When an availability group is removed that has published member databases, or a published database is removed from an availability group, all copies of the published databases will be left in the recovering state.</span></span> <span data-ttu-id="b23b4-136">それぞれを復元すると、パブリッシュされたデータベースとして表示されます。</span><span class="sxs-lookup"><span data-stu-id="b23b4-136">If restored, each will appear as a published database.</span></span> <span data-ttu-id="b23b4-137">1 つのコピーだけをパブリケーション メタデータで保持する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b23b4-137">Only one copy should be retained with publication metadata.</span></span> <span data-ttu-id="b23b4-138">パブリッシュされたデータベース コピーのレプリケーションを無効にするには、最初にすべてのサブスクリプションとパブリケーションをデータベースから削除します。</span><span class="sxs-lookup"><span data-stu-id="b23b4-138">To disable replication for a published database copy, first remove all subscriptions and publications from the database.</span></span>  
  
     <span data-ttu-id="b23b4-139">`sp_dropsubscription` を実行してパブリケーション サブスクリプションを削除します。</span><span class="sxs-lookup"><span data-stu-id="b23b4-139">Run `sp_dropsubscription` to remove publication subscriptions.</span></span> <span data-ttu-id="b23b4-140">*@ignore_distributributor*ディストリビューターでアクティブなパブリッシングデータベースのメタデータを保持するには、パラメーターを1に設定してください。</span><span class="sxs-lookup"><span data-stu-id="b23b4-140">Make sure to set the parameter *@ignore_distributributor* to 1 to preserve the metadata for the active publishing database at the distributor.</span></span>  
  
    ```  
    USE MyDBName;  
    GO  
  
    EXEC sys.sp_dropsubscription   
        @subscriber = 'MySubscriber',  
        @publication = 'MyPublication',  
        @article = 'all',  
        @ignore_distributor = 1;  
    ```  
  
     <span data-ttu-id="b23b4-141">`sp_droppublication` を実行してすべてのパブリケーションを削除します。</span><span class="sxs-lookup"><span data-stu-id="b23b4-141">Run `sp_droppublication` to remove all publications.</span></span> <span data-ttu-id="b23b4-142">ここでも、パラメーターを1に設定して、 *@ignore_distributor* アクティブなパブリッシングデータベースのメタデータをディストリビューターで保持します。</span><span class="sxs-lookup"><span data-stu-id="b23b4-142">Again, set the parameter *@ignore_distributor* to 1 to preserve the metadata for the active publishing database at the distributor.</span></span>  
  
    ```  
    EXEC sys.sp_droppublication   
        @publication = 'MyPublication',  
        @ignore_distributor = 1;  
    ```  
  
     <span data-ttu-id="b23b4-143">`sp_replicationdboption` を実行してデータベースのレプリケーションを無効にします。</span><span class="sxs-lookup"><span data-stu-id="b23b4-143">Run `sp_replicationdboption` to disable replication for the database.</span></span>  
  
    ```  
    EXEC sys.sp_replicationdboption  
        @dbname = 'MyDBName',  
        @optname = 'publish',  
        @value = 'false';  
    ```  
  
     <span data-ttu-id="b23b4-144">この時点で、パブリッシュされたデータベースのコピーを保持または削除できます。</span><span class="sxs-lookup"><span data-stu-id="b23b4-144">At this point, the copy of the published database can be retained or dropped.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="b23b4-145">関連タスク</span><span class="sxs-lookup"><span data-stu-id="b23b4-145">Related Tasks</span></span>  
  
-   [<span data-ttu-id="b23b4-146">AlwaysOn 可用性グループ用のレプリケーションの構成 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="b23b4-146">Configure Replication for AlwaysOn Availability Groups (SQL Server)</span></span>](always-on-availability-groups-sql-server.md)  
  
-   [<span data-ttu-id="b23b4-147">レプリケーション、Change Tracking、変更データキャプチャ、AlwaysOn 可用性グループ &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="b23b4-147">Replication, Change Tracking, Change Data Capture, and AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](replicate-track-change-data-capture-always-on-availability.md)  
  
-   [<span data-ttu-id="b23b4-148">レプリケーション管理に関する FAQ</span><span class="sxs-lookup"><span data-stu-id="b23b4-148">Replication Administration FAQ</span></span>](../../../relational-databases/replication/administration/frequently-asked-questions-for-replication-administrators.md)  
  
-   [<span data-ttu-id="b23b4-149">レプリケーションサブスクライバーと AlwaysOn 可用性グループ &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="b23b4-149">Replication Subscribers and AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](replication-subscribers-and-always-on-availability-groups-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="b23b4-150">参照</span><span class="sxs-lookup"><span data-stu-id="b23b4-150">See Also</span></span>  
 <span data-ttu-id="b23b4-151">[AlwaysOn 可用性グループ &#40;SQL Server の前提条件、制限事項、推奨事項&#41;](prereqs-restrictions-recommendations-always-on-availability.md) </span><span class="sxs-lookup"><span data-stu-id="b23b4-151">[Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md) </span></span>  
 <span data-ttu-id="b23b4-152">[AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="b23b4-152">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="b23b4-153">[AlwaysOn 可用性グループ: 相互運用性 (SQL Server)](always-on-availability-groups-interoperability-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="b23b4-153">[AlwaysOn Availability Groups: Interoperability (SQL Server)](always-on-availability-groups-interoperability-sql-server.md) </span></span>  
 [<span data-ttu-id="b23b4-154">SQL Server レプリケーション</span><span class="sxs-lookup"><span data-stu-id="b23b4-154">SQL Server Replication</span></span>](../../../relational-databases/replication/sql-server-replication.md)  
  
  
