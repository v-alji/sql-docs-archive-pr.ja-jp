---
title: Always On 可用性グループのサーバーインスタンスの構成 (SQL Server) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], server instance
- Availability Groups [SQL Server], about
ms.assetid: fad8db32-593e-49d5-989c-39eb8399c416
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3392e6189b687516e627d847acceedb165141117
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741314"
---
# <a name="configuration-of-a-server-instance-for-always-on-availability-groups-sql-server"></a><span data-ttu-id="338a7-102">Always On 可用性グループのためのサーバー インスタンスの構成 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="338a7-102">Configuration of a Server Instance for Always On Availability Groups (SQL Server)</span></span>
  <span data-ttu-id="338a7-103">このトピックでは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)][!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] でサポートするために [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] のインスタンスを構成する際の要件について説明します。</span><span class="sxs-lookup"><span data-stu-id="338a7-103">This topic contains information about the requirements for configuring an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to support [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="338a7-104">Windows Server フェールオーバー クラスタリング (WSFC) ノードおよび [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスの [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] の前提条件と制限に関する基本情報については、「[AlwaysOn 可用性グループの前提条件、制限事項、および推奨事項 &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="338a7-104">For essential information about [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] prerequisites and restrictions for Windows Server Failover Clustering (WSFC) nodes and for instances of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], see [Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md).</span></span>  
  
 
  
##  <a name="terms-and-definitions"></a><a name="TermsAndDefinitions"></a> <span data-ttu-id="338a7-105">用語と定義</span><span class="sxs-lookup"><span data-stu-id="338a7-105">Terms and Definitions</span></span>  
  
 <span data-ttu-id="338a7-106">データベース ミラーリングに代わる、高可用性と災害復旧のためのエンタープライズ レベルのソリューション。</span><span class="sxs-lookup"><span data-stu-id="338a7-106">A high-availability and disaster-recovery solution that provides an enterprise-level replacement for database mirroring.</span></span> <span data-ttu-id="338a7-107">*可用性グループ*は、相互にフェールオーバーされる個別のユーザーデータベース (*可用性データベース*と呼ばれます) のフェールオーバー環境をサポートします。</span><span class="sxs-lookup"><span data-stu-id="338a7-107">An *availability group* supports a failover environment for a discrete set of user databases, known as *availability databases*, that fail over together.</span></span>  
  
 <span data-ttu-id="338a7-108">可用性レプリカ</span><span class="sxs-lookup"><span data-stu-id="338a7-108">availability replica</span></span>  
 <span data-ttu-id="338a7-109">可用性グループのインスタンス化。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の特定のインスタンスによってホストされ、可用性グループに属する各可用性データベースのローカル コピーを保持します。</span><span class="sxs-lookup"><span data-stu-id="338a7-109">An instantiation of an availability group that is hosted by a specific instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] and that maintains a local copy of each availability database that belongs to the availability group.</span></span> <span data-ttu-id="338a7-110">可用性グループには、2 種類の可用性レプリカ ( *プライマリ レプリカ* と 1 ～ 4 つの *セカンダリ レプリカ*) があります。</span><span class="sxs-lookup"><span data-stu-id="338a7-110">Two types of availability replicas exist: a single *primary replica* and one to four *secondary replicas*.</span></span> <span data-ttu-id="338a7-111">可用性グループの可用性レプリカをホストするサーバー インスタンスは、同じ Windows Server フェールオーバー クラスタリング (WSFC) クラスター内の別のノードにある必要があります。</span><span class="sxs-lookup"><span data-stu-id="338a7-111">The server instances that host the availability replicas for a given availability group must reside on different nodes of a single Windows Server Failover Clustering (WSFC) cluster.</span></span>  
  
 [<span data-ttu-id="338a7-112">データベースミラーリングエンドポイント</span><span class="sxs-lookup"><span data-stu-id="338a7-112">database mirroring endpoint</span></span>](../../database-mirroring/the-database-mirroring-endpoint-sql-server.md)  
 <span data-ttu-id="338a7-113">エンドポイントとは、SQL Server でネットワーク経由の通信を行うことができるようにする SQL Server オブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="338a7-113">An endpoint is a SQL Server object that enables SQL Server to communicate over the network.</span></span> <span data-ttu-id="338a7-114">データベース ミラーリングおよび [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] に参加する場合、サーバー インスタンスには特別な専用のエンドポイントが必要です。</span><span class="sxs-lookup"><span data-stu-id="338a7-114">To participate in database mirroring and/or [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] a server instance requires a special, dedicated endpoint.</span></span> <span data-ttu-id="338a7-115">サーバー インスタンスのすべてのミラーリングと可用性グループの接続は、同じデータベース ミラーリング エンドポイントを使用します。</span><span class="sxs-lookup"><span data-stu-id="338a7-115">All mirroring and availability group connections on a server instance use the same database mirroring endpoint.</span></span> <span data-ttu-id="338a7-116">このエンドポイントの用途は特殊で、他のサーバー インスタンスからこれらの接続を受信するためにのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="338a7-116">This endpoint is a special-purpose endpoint used exclusively to receive these connections from other server instances.</span></span>  
  
##  <a name="to-configure-a-server-instance-to-support-alwayson-availability-groups"></a><a name="ConfigSI"></a><span data-ttu-id="338a7-117">AlwaysOn 可用性グループをサポートするようにサーバーインスタンスを構成するには</span><span class="sxs-lookup"><span data-stu-id="338a7-117">To Configure a Server Instance to Support AlwaysOn Availability Groups</span></span>  
 <span data-ttu-id="338a7-118">[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]をサポートする場合、サーバー インスタンスは、可用性グループをホストする WSFC フェールオーバー クラスター内のノードにあり、 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] が有効になっていて、データベース ミラーリング エンドポイントを持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="338a7-118">To support [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], a server instance must reside on a node in the WSFC failover cluster that hosts the availability group, be [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] enabled, and possess a database mirroring endpoint.</span></span>  
  
1.  <span data-ttu-id="338a7-119">可用性グループに追加するすべてのサーバー インスタンスの AlwaysOn 可用性グループ機能を有効にします。</span><span class="sxs-lookup"><span data-stu-id="338a7-119">Enable the AlwaysOn Availability Groups feature on every server instance that is to participate in one or more availability groups.</span></span> <span data-ttu-id="338a7-120">特定の可用性グループの特定のサーバー インスタンスがホストできる可用性レプリカは 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="338a7-120">A given server instance can host only a single availability replica for a given availability group.</span></span>  
  
2.  <span data-ttu-id="338a7-121">サーバー インスタンスに、データベース ミラーリング エンドポイントが存在することを確認します。</span><span class="sxs-lookup"><span data-stu-id="338a7-121">Ensure that the server instance possesses a database mirroring endpoint.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="338a7-122">関連タスク</span><span class="sxs-lookup"><span data-stu-id="338a7-122">Related Tasks</span></span>  
 <span data-ttu-id="338a7-123">**AlwaysOn 可用性グループを有効にするには**</span><span class="sxs-lookup"><span data-stu-id="338a7-123">**To enable AlwaysOn Availability Groups**</span></span>  
  
-   [<span data-ttu-id="338a7-124">AlwaysOn 可用性グループの有効化と無効化 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="338a7-124">Enable and Disable AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](enable-and-disable-always-on-availability-groups-sql-server.md)  
  
 <span data-ttu-id="338a7-125">**データベース ミラーリング エンドポイントが存在するかどうかを確認するには**</span><span class="sxs-lookup"><span data-stu-id="338a7-125">**To determine whether a database mirroring endpoint exists**</span></span>  
  
-   [<span data-ttu-id="338a7-126">sys.database_mirroring_endpoints &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="338a7-126">sys.database_mirroring_endpoints &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql)  
  
 <span data-ttu-id="338a7-127">**データベース ミラーリング エンドポイントを作成するには**</span><span class="sxs-lookup"><span data-stu-id="338a7-127">**To create a database mirroring endpoint**</span></span>  
  
-   [<span data-ttu-id="338a7-128">AlwaysOn 可用性グループ &#40;SQL Server PowerShell のデータベースミラーリングエンドポイントを作成&#41;</span><span class="sxs-lookup"><span data-stu-id="338a7-128">Create a Database Mirroring Endpoint for AlwaysOn Availability Groups &#40;SQL Server PowerShell&#41;</span></span>](database-mirroring-always-on-availability-groups-powershell.md)  
  
-   [<span data-ttu-id="338a7-129">Windows 認証でのデータベース ミラーリング エンドポイントの作成 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="338a7-129">Create a Database Mirroring Endpoint for Windows Authentication &#40;Transact-SQL&#41;</span></span>](../../database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)  
  
-   [<span data-ttu-id="338a7-130">データベース ミラーリング エンドポイントで発信接続に証明書を使用できるようにする &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="338a7-130">Allow a Database Mirroring Endpoint to Use Certificates for Outbound Connections &#40;Transact-SQL&#41;</span></span>](../../database-mirroring/database-mirroring-use-certificates-for-outbound-connections.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="338a7-131">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="338a7-131">Related Content</span></span>  
  
-   <span data-ttu-id="338a7-132">**ブログ:**</span><span class="sxs-lookup"><span data-stu-id="338a7-132">**Blogs:**</span></span>  
  
     [<span data-ttu-id="338a7-133">AlwaysON - HADRON 学習シリーズ:HADRON 対応データベースでのワーカー プールの使用</span><span class="sxs-lookup"><span data-stu-id="338a7-133">AlwaysON - HADRON Learning Series: Worker Pool Usage for HADRON Enabled Databases</span></span>](https://blogs.msdn.com/b/psssql/archive/2012/05/17/alwayson-hadron-learning-series-worker-pool-usage-for-hadron-enabled-databases.aspx)  
  
     [<span data-ttu-id="338a7-134">SQL Server AlwaysOn チームのブログ:SQL Server AlwaysOn チームのオフィシャル ブログ</span><span class="sxs-lookup"><span data-stu-id="338a7-134">SQL Server AlwaysOn Team Blogs: The official SQL Server AlwaysOn Team Blog</span></span>](https://blogs.msdn.com/b/sqlalwayson/)  
  
     [<span data-ttu-id="338a7-135">CSS SQL Server エンジニアのブログ</span><span class="sxs-lookup"><span data-stu-id="338a7-135">CSS SQL Server Engineers Blogs</span></span>](https://blogs.msdn.com/b/psssql/)  
  
-   <span data-ttu-id="338a7-136">**ビデオ:**</span><span class="sxs-lookup"><span data-stu-id="338a7-136">**Videos:**</span></span>  
  
     [<span data-ttu-id="338a7-137">Microsoft SQL Server コード ネーム "Denali" AlwaysOn シリーズ パート 1: 次世代の高可用性ソリューションの概要</span><span class="sxs-lookup"><span data-stu-id="338a7-137">Microsoft SQL Server Code-Named "Denali" AlwaysOn Series,Part 1: Introducing the Next Generation High Availability Solution</span></span>](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI302)  
  
     [<span data-ttu-id="338a7-138">Microsoft SQL Server コードネーム "Denali" AlwaysOn シリーズ パート 2: AlwaysOn を使用したミッション クリティカルな高可用性ソリューションの構築</span><span class="sxs-lookup"><span data-stu-id="338a7-138">Microsoft SQL Server Code-Named "Denali" AlwaysOn Series,Part 2: Building a Mission-Critical High Availability Solution Using AlwaysOn</span></span>](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI404)  
  
-   <span data-ttu-id="338a7-139">**ホワイト ペーパー:**</span><span class="sxs-lookup"><span data-stu-id="338a7-139">**Whitepapers:**</span></span>  
  
     [<span data-ttu-id="338a7-140">高可用性と災害復旧のための Microsoft SQL Server AlwaysOn ソリューション ガイド</span><span class="sxs-lookup"><span data-stu-id="338a7-140">Microsoft SQL Server AlwaysOn Solutions Guide for High Availability and Disaster Recovery</span></span>](https://go.microsoft.com/fwlink/?LinkId=227600)  
  
     [<span data-ttu-id="338a7-141">SQL Server 2012 に関する Microsoft ホワイト ペーパー</span><span class="sxs-lookup"><span data-stu-id="338a7-141">Microsoft White Papers for SQL Server 2012</span></span>](https://msdn.microsoft.com/library/hh403491.aspx)  
  
     [<span data-ttu-id="338a7-142">SQL Server ユーザー諮問チームのホワイト ペーパー</span><span class="sxs-lookup"><span data-stu-id="338a7-142">SQL Server Customer Advisory Team Whitepapers</span></span>](http://sqlcat.com/)  
  
## <a name="see-also"></a><span data-ttu-id="338a7-143">参照</span><span class="sxs-lookup"><span data-stu-id="338a7-143">See Also</span></span>  
 <span data-ttu-id="338a7-144">[AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="338a7-144">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="338a7-145">[AlwaysOn 可用性グループ &#40;SQL Server の前提条件、制限事項、推奨事項&#41;](prereqs-restrictions-recommendations-always-on-availability.md) </span><span class="sxs-lookup"><span data-stu-id="338a7-145">[Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md) </span></span>  
 <span data-ttu-id="338a7-146">[データベース ミラーリング エンドポイント &#40;SQL Server&#41;](../../database-mirroring/the-database-mirroring-endpoint-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="338a7-146">[The Database Mirroring Endpoint &#40;SQL Server&#41;](../../database-mirroring/the-database-mirroring-endpoint-sql-server.md) </span></span>  
 <span data-ttu-id="338a7-147">[AlwaysOn 可用性グループ: 相互運用性 (SQL Server)](always-on-availability-groups-interoperability-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="338a7-147">[AlwaysOn Availability Groups: Interoperability (SQL Server)](always-on-availability-groups-interoperability-sql-server.md) </span></span>  
 <span data-ttu-id="338a7-148">[フェールオーバークラスタリングと AlwaysOn 可用性グループ &#40;SQL Server&#41;](failover-clustering-and-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="338a7-148">[Failover Clustering and AlwaysOn Availability Groups &#40;SQL Server&#41;](failover-clustering-and-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="338a7-149">[Windows Server フェールオーバー クラスタリング &#40;WSFC&#41; と SQL Server](../../../sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="338a7-149">[Windows Server Failover Clustering &#40;WSFC&#41; with SQL Server](../../../sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server.md) </span></span>  
 [<span data-ttu-id="338a7-150">AlwaysOn フェールオーバークラスターインスタンス</span><span class="sxs-lookup"><span data-stu-id="338a7-150">AlwaysOn Failover Cluster Instances</span></span>](../../../sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server.md)  
  
