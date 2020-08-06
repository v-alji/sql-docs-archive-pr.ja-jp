---
title: 可用性グループの監視 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- Availability Groups [SQL Server], troubleshooting
ms.assetid: 1d5e3291-0d0a-45a1-88e5-1fc242d17210
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: da41c6d629ffb57749ae9c13e715f535e98aa3da
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634644"
---
# <a name="monitoring-of-availability-groups-sql-server"></a><span data-ttu-id="7d042-102">可用性グループの監視 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="7d042-102">Monitoring of Availability Groups (SQL Server)</span></span>
  <span data-ttu-id="7d042-103">AlwaysOn 可用性グループのプロパティと状態を監視するには、次のツールを使用します。</span><span class="sxs-lookup"><span data-stu-id="7d042-103">To monitor the properties and state of an AlwaysOn availability group you can use the following tools.</span></span>  
  
|<span data-ttu-id="7d042-104">ツール</span><span class="sxs-lookup"><span data-stu-id="7d042-104">Tool</span></span>|<span data-ttu-id="7d042-105">簡単な説明</span><span class="sxs-lookup"><span data-stu-id="7d042-105">Brief Description</span></span>|<span data-ttu-id="7d042-106">リンク</span><span class="sxs-lookup"><span data-stu-id="7d042-106">Links</span></span>|  
|----------|-----------------------|-----------|  
|<span data-ttu-id="7d042-107">System Center Monitoring pack for SQL Server</span><span class="sxs-lookup"><span data-stu-id="7d042-107">System Center Monitoring pack for SQL Server</span></span>|<span data-ttu-id="7d042-108">Monitoring pack for SQL Server (SQLMP) は、可用性グループ、可用性レプリカ、および可用性データベースを IT 管理者が監視するための推奨ソリューションです。</span><span class="sxs-lookup"><span data-stu-id="7d042-108">The Monitoring pack for SQL Server (SQLMP) is the recommended solution for monitoring availability groups, availability replica and availability databases for IT administrators.</span></span> <span data-ttu-id="7d042-109">[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] に特に関連する監視機能は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="7d042-109">Monitoring features that are particularly relevance to [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] include the following:</span></span><br /><br /> <span data-ttu-id="7d042-110">可用性グループ、可用性レプリカ、および可用性データベースを多数のコンピューターから自動検出する機能。</span><span class="sxs-lookup"><span data-stu-id="7d042-110">Automatic discoverability of availability groups, availability replicas, and availability database from among hundreds of computers.</span></span> <span data-ttu-id="7d042-111">これにより、 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] の在庫を簡単に追跡できます。</span><span class="sxs-lookup"><span data-stu-id="7d042-111">This enables you to easily keep track of your [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] inventory.</span></span><br /><br /> <span data-ttu-id="7d042-112">System Center Operations Manager (SCOM) の完全な警告機能とチケット機能。</span><span class="sxs-lookup"><span data-stu-id="7d042-112">Fully capable System Center Operations Manager (SCOM) alerting and ticketing.</span></span> <span data-ttu-id="7d042-113">これらの機能は、問題の早期解決を可能にする詳細な情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="7d042-113">These features provide detailed knowledge that enables faster resolution to a problem.</span></span><br /><br /> <span data-ttu-id="7d042-114">ポリシー ベースの管理 (PBM) を使用した AlwaysOn 正常性状態の監視のカスタム拡張機能。</span><span class="sxs-lookup"><span data-stu-id="7d042-114">A custom extension to AlwaysOn Health monitoring using Policy Based management (PBM).</span></span><br /><br /> <span data-ttu-id="7d042-115">正常性状態は、可用性データベースから可用性レプリカにロールアップされます。</span><span class="sxs-lookup"><span data-stu-id="7d042-115">Health roll ups from availability databases to availability replicas.</span></span><br /><br /> <span data-ttu-id="7d042-116">System Center Operations Manager コンソールから [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] を管理するカスタム タスク。</span><span class="sxs-lookup"><span data-stu-id="7d042-116">Custom tasks that manage [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] from the System Center Operations Manager console.</span></span>|<span data-ttu-id="7d042-117">監視パック (SQLServerMP.msi) および *SQL Server Management Pack Guide for System Center Operations Manager* (SQLServerMPGuide.doc) をダウンロードするには、以下を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7d042-117">To download the monitoring pack (SQLServerMP.msi) and *SQL Server Management Pack Guide for System Center Operations Manager* (SQLServerMPGuide.doc), see:</span></span><br /><br /> [<span data-ttu-id="7d042-118">System Center Monitoring pack for SQL Server</span><span class="sxs-lookup"><span data-stu-id="7d042-118">System Center Monitoring pack for SQL Server</span></span>](https://www.microsoft.com/download/details.aspx?displaylang=en&id=10631)|  
|[!INCLUDE[tsql](../../../includes/tsql-md.md)]|[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] <span data-ttu-id="7d042-119">のカタログ ビューと動的管理ビューは、可用性グループとそのレプリカ、データベース、リスナー、および WSFC クラスター環境に関する豊富な情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="7d042-119">catalog and dynamic management views provide a wealth of information about your availability groups and their replicas, databases, listeners, and WSFC cluster environment.</span></span>|[<span data-ttu-id="7d042-120">可用性グループの監視 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="7d042-120">Monitor Availability Groups &#40;Transact-SQL&#41;</span></span>](monitor-availability-groups-transact-sql.md)|  
|[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]|<span data-ttu-id="7d042-121">**[オブジェクト エクスプローラーの詳細]** ペインには、接続先の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスでホストされている可用性グループの基本情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="7d042-121">The **Object Explorer Details** pane displays basic information about the availability groups hosted on the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to which you are connected.</span></span><br /><br /> <span data-ttu-id="7d042-122">ヒント: このペインを使用して、複数の可用性グループ、レプリカ、またはデータベースを選択し、選択したオブジェクトで一般的な管理タスク (可用性グループからの複数の可用性レプリカまたはデータベースの削除など) を実行します。</span><span class="sxs-lookup"><span data-stu-id="7d042-122">Tip: Use this pane to select multiple availability groups, replicas, or databases and to perform routine administrative tasks on the selected objects; for example, removing multiple availability replicas or databases from an availability group.</span></span>|<span data-ttu-id="7d042-123">[[オブジェクト エクスプローラーの詳細] を使用した可用性グループの監視 &#40;SQL Server Management Studio&#41;](use-object-explorer-details-to-monitor-availability-groups.md)</span><span class="sxs-lookup"><span data-stu-id="7d042-123">[Use the Object Explorer Details to Monitor Availability Groups &#40;SQL Server Management Studio&#41;](use-object-explorer-details-to-monitor-availability-groups.md)</span></span>|  
|[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]|<span data-ttu-id="7d042-124">**[プロパティ]** ダイアログ ボックスを使用して、可用性グループ、レプリカ、またはリスナーのプロパティを表示し、必要に応じてその値を変更できます。</span><span class="sxs-lookup"><span data-stu-id="7d042-124">**Properties** dialog boxes enable you to view the properties of availability groups, replicas, or listeners and, in some cases, to change their values.</span></span>|[<span data-ttu-id="7d042-125">可用性グループのプロパティの表示 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="7d042-125">View Availability Group Properties &#40;SQL Server&#41;</span></span>](view-availability-group-properties-sql-server.md)<br /><br /> [<span data-ttu-id="7d042-126">可用性レプリカのプロパティの表示 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="7d042-126">View Availability Replica Properties &#40;SQL Server&#41;</span></span>](view-availability-replica-properties-sql-server.md)<br /><br /> [<span data-ttu-id="7d042-127">可用性グループ リスナーのプロパティの表示 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="7d042-127">View Availability Group Listener Properties &#40;SQL Server&#41;</span></span>](view-availability-group-listener-properties-sql-server.md)|  
|<span data-ttu-id="7d042-128">システム モニター</span><span class="sxs-lookup"><span data-stu-id="7d042-128">System Monitor</span></span>|<span data-ttu-id="7d042-129">**SQLServer:Availability Replica** パフォーマンス オブジェクトには、可用性レプリカに関する情報を報告するパフォーマンス カウンターが含まれています。</span><span class="sxs-lookup"><span data-stu-id="7d042-129">The **SQLServer:Availability Replica** performance object contains performance counters that report information about availability replicas.</span></span>|[<span data-ttu-id="7d042-130">SQL Server、可用性レプリカ</span><span class="sxs-lookup"><span data-stu-id="7d042-130">SQL Server, Availability Replica</span></span>](../../../relational-databases/performance-monitor/sql-server-availability-replica.md)|  
|<span data-ttu-id="7d042-131">システム モニター</span><span class="sxs-lookup"><span data-stu-id="7d042-131">System Monitor</span></span>|<span data-ttu-id="7d042-132">**SQLServer:Database Replica** パフォーマンス オブジェクトには、特定のセカンダリ レプリカのセカンダリ データベースに関する情報を報告するパフォーマンス カウンターが含まれています。</span><span class="sxs-lookup"><span data-stu-id="7d042-132">The **SQLServer:Database Replica** performance object contains performance counters that report information about the secondary databases on a given secondary replica.</span></span><br /><br /> <span data-ttu-id="7d042-133">SQL Server の **SQLServer:Databases** オブジェクトには、トランザクション ログの利用状況などを監視するパフォーマンス カウンターが含まれています。</span><span class="sxs-lookup"><span data-stu-id="7d042-133">The **SQLServer:Databases** object in SQL Server contains performance counters that monitor transaction log activities, among other things.</span></span> <span data-ttu-id="7d042-134">可用性データベースでのトランザクション ログの利用状況の監視に関連性が高いカウンターは、 **[Log Flush Write Time (ms)]** 、 **[Log Flushes/sec]** 、 **[Log Pool Cache Misses/sec]** 、 **[Log Pool Disk Reads/sec]** 、および **[Log Pool Requests/sec]** です。</span><span class="sxs-lookup"><span data-stu-id="7d042-134">The following counters are particularly relevant for monitoring transaction-log activity on availability databases: **Log Flush Write Time (ms)**, **Log Flushes/sec**, **Log Pool Cache Misses/sec**, **Log Pool Disk Reads/sec**, and **Log Pool Requests/sec**.</span></span>|<span data-ttu-id="7d042-135">[SQL Server、Database ReplicaQL Server](../../../relational-databases/performance-monitor/sql-server-database-replica.md) および [SQL Server、Databases オブジェクト](../../../relational-databases/performance-monitor/sql-server-databases-object.md)</span><span class="sxs-lookup"><span data-stu-id="7d042-135">[SQL Server, Database Replica](../../../relational-databases/performance-monitor/sql-server-database-replica.md) and [SQL Server, Databases Object](../../../relational-databases/performance-monitor/sql-server-databases-object.md)</span></span>|  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="7d042-136">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="7d042-136">Related Content</span></span>  
  
-   <span data-ttu-id="7d042-137">**ブログ:**</span><span class="sxs-lookup"><span data-stu-id="7d042-137">**Blogs:**</span></span>  
  
     [<span data-ttu-id="7d042-138">AlwaysOn の正常性モデル: パート 1: 正常性モデルのアーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="7d042-138">The AlwaysOn Health Model Part 1 -- Health Model Architecture</span></span>](https://docs.microsoft.com/archive/blogs/sqlalwayson/the-alwayson-health-model-part-1-health-model-architecture)  
  
     [<span data-ttu-id="7d042-139">AlwaysOn の正常性モデル: パート 2: 正常性モデルの拡張</span><span class="sxs-lookup"><span data-stu-id="7d042-139">The AlwaysOn Health Model Part 2 -- Extending the Health Model</span></span>](https://docs.microsoft.com/archive/blogs/sqlalwayson/the-alwayson-health-model-part-2-extending-the-health-model)  
  
     [<span data-ttu-id="7d042-140">Monitoring AlwaysOn Health with PowerShell - Part 1: Basic Cmdlet Overview</span><span class="sxs-lookup"><span data-stu-id="7d042-140">Monitoring AlwaysOn Health with PowerShell - Part 1: Basic Cmdlet Overview</span></span>](https://docs.microsoft.com/archive/blogs/sqlalwayson/monitoring-alwayson-health-with-powershell-part-1-basic-cmdlet-overview)  
  
     [<span data-ttu-id="7d042-141">Monitoring AlwaysOn Health with PowerShell - Part 2: Advanced Cmdlet Usage</span><span class="sxs-lookup"><span data-stu-id="7d042-141">Monitoring AlwaysOn Health with PowerShell - Part 2: Advanced Cmdlet Usage</span></span>](https://docs.microsoft.com/archive/blogs/sqlalwayson/monitoring-alwayson-health-with-powershell-part-2-advanced-cmdlet-usage)  
  
     [<span data-ttu-id="7d042-142">Monitoring AlwaysOn Health with PowerShell - Part 3 : A Simple Monitoring Application</span><span class="sxs-lookup"><span data-stu-id="7d042-142">Monitoring AlwaysOn Health with PowerShell - Part 3 : A Simple Monitoring Application</span></span>](https://docs.microsoft.com/archive/blogs/sqlalwayson/monitoring-alwayson-health-with-powershell-part-3-a-simple-monitoring-application)  
  
     [<span data-ttu-id="7d042-143">Monitoring AlwaysOn Health with PowerShell - Part 4 : Integration with SQL Server Agent</span><span class="sxs-lookup"><span data-stu-id="7d042-143">Monitoring AlwaysOn Health with PowerShell - Part 4 : Integration with SQL Server Agent</span></span>](https://docs.microsoft.com/archive/blogs/sqlalwayson/monitoring-alwayson-health-with-powershell-part-4-integration-with-sql-server-agent)  
  
     [<span data-ttu-id="7d042-144">SQL Server AlwaysOn チームのブログ:SQL Server AlwaysOn チームのオフィシャル ブログ</span><span class="sxs-lookup"><span data-stu-id="7d042-144">SQL Server AlwaysOn Team Blogs: The official SQL Server AlwaysOn Team Blog</span></span>](https://docs.microsoft.com/archive/blogs/sqlalwayson/)  
  
     [<span data-ttu-id="7d042-145">CSS SQL Server エンジニアのブログ</span><span class="sxs-lookup"><span data-stu-id="7d042-145">CSS SQL Server Engineers Blogs</span></span>](https://blogs.msdn.com/b/psssql/)  
  
-   <span data-ttu-id="7d042-146">**ホワイト ペーパー:**</span><span class="sxs-lookup"><span data-stu-id="7d042-146">**Whitepapers:**</span></span>  
  
     [<span data-ttu-id="7d042-147">SQL Server 2012 に関する Microsoft ホワイト ペーパー</span><span class="sxs-lookup"><span data-stu-id="7d042-147">Microsoft White Papers for SQL Server 2012</span></span>](https://msdn.microsoft.com/library/hh403491.aspx)  
  
     [<span data-ttu-id="7d042-148">SQL Server ユーザー諮問チームのホワイト ペーパー</span><span class="sxs-lookup"><span data-stu-id="7d042-148">SQL Server Customer Advisory Team Whitepapers</span></span>](http://sqlcat.com/)  
  
## <a name="see-also"></a><span data-ttu-id="7d042-149">参照</span><span class="sxs-lookup"><span data-stu-id="7d042-149">See Also</span></span>  
 <span data-ttu-id="7d042-150">[AlwaysOn 可用性グループカタログビュー &#40;Transact-sql&#41;](/sql/relational-databases/system-catalog-views/always-on-availability-groups-catalog-views-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="7d042-150">[AlwaysOn Availability Groups Catalog Views &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/always-on-availability-groups-catalog-views-transact-sql) </span></span>  
 <span data-ttu-id="7d042-151">[Transact-sql&#41;&#40;の動的管理ビューおよび関数の AlwaysOn 可用性グループ](/sql/relational-databases/system-dynamic-management-views/always-on-availability-groups-dynamic-management-views-functions) </span><span class="sxs-lookup"><span data-stu-id="7d042-151">[AlwaysOn Availability Groups Dynamic Management Views and Functions &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/always-on-availability-groups-dynamic-management-views-functions) </span></span>  
 <span data-ttu-id="7d042-152">[可用性グループの自動フェールオーバーのための柔軟なフェールオーバーポリシー &#40;SQL Server&#41;](flexible-automatic-failover-policy-availability-group.md) </span><span class="sxs-lookup"><span data-stu-id="7d042-152">[Flexible Failover Policy for Automatic Failover of an Availability Group &#40;SQL Server&#41;](flexible-automatic-failover-policy-availability-group.md) </span></span>  
 <span data-ttu-id="7d042-153">[AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="7d042-153">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="7d042-154">[可用性グループとデータベースミラーリングのための自動ページ修復 &#40;&#41;](../../../sql-server/failover-clusters/automatic-page-repair-availability-groups-database-mirroring.md) </span><span class="sxs-lookup"><span data-stu-id="7d042-154">[Automatic Page Repair &#40;For Availability Groups and Database Mirroring&#41;](../../../sql-server/failover-clusters/automatic-page-repair-availability-groups-database-mirroring.md) </span></span>  
 [<span data-ttu-id="7d042-155">AlwaysOn ダッシュボードの使用 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="7d042-155">Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;</span></span>](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  