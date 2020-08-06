---
title: 可用性グループの作成と構成 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], deploying
- Availability Groups [SQL Server], configuring
- Availability Groups [SQL Server], creating
ms.assetid: 7f89fab8-6ee2-4273-9de0-e594bfb9407f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: bc33da393527c19985f5e7b214ba4bc02dc2f3af
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743445"
---
# <a name="creation-and-configuration-of-availability-groups-sql-server"></a><span data-ttu-id="fb513-102">可用性グループの作成と構成 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="fb513-102">Creation and Configuration of Availability Groups (SQL Server)</span></span>
  <span data-ttu-id="fb513-103">このセクションの各トピックでは、単一の WSFC (Windows Server フェールオーバー クラスタリング) フェールオーバー クラスターを構成する各 WSFC ノード上の [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] のインスタンスに対し、 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] の実装を配置する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="fb513-103">The topics in this section explain how to deploy a [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] implementation on instances of [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] that reside on different Windows Server Failover Clustering (WSFC) nodes within a single WSFC failover cluster.</span></span>  
  
 <span data-ttu-id="fb513-104">可用性グループを初めて作成する前に、次のトピックの情報をよく理解しておくことを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="fb513-104">Before you create your first availability group, we strongly recommend that you familiarize yourself with the information in the following topics:</span></span>  
  
 [<span data-ttu-id="fb513-105">AlwaysOn 可用性グループ &#40;SQL Server の前提条件、制限事項、推奨事項&#41;</span><span class="sxs-lookup"><span data-stu-id="fb513-105">Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](prereqs-restrictions-recommendations-always-on-availability.md)  
 <span data-ttu-id="fb513-106">このトピックでは、コンピューター、WSFC ノード、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]インスタンス、可用性グループ、可用性レプリカ、および可用性データベースに関して、それぞれの前提条件、制限、および推奨事項を取り上げます。</span><span class="sxs-lookup"><span data-stu-id="fb513-106">This topic describes the prerequisites, restrictions, and recommendations for computers; WSFC nodes; instances of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]; availability groups, replicas, and databases.</span></span> <span data-ttu-id="fb513-107">このトピックでは、セキュリティに関する考慮事項も取り上げています。</span><span class="sxs-lookup"><span data-stu-id="fb513-107">This topic also contains information about security considerations.</span></span>  
  
 [<span data-ttu-id="fb513-108">はじめに AlwaysOn 可用性グループ &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fb513-108">Getting Started with AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](getting-started-with-always-on-availability-groups-sql-server.md)  
 <span data-ttu-id="fb513-109">サーバー インスタンスの構成、可用性グループの構成、クライアント接続に必要な可用性グループの構成、可用性グループの管理、可用性グループの監視について、それぞれ手順を紹介します。</span><span class="sxs-lookup"><span data-stu-id="fb513-109">Contains information about the steps for configuring a server instance, creating an availability group, configuring the availability group for client connections, managing availability groups, and monitoring availability groups.</span></span>  
  
 
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="fb513-110">関連タスク</span><span class="sxs-lookup"><span data-stu-id="fb513-110">Related Tasks</span></span>  
 <span data-ttu-id="fb513-111">**のサーバーインスタンスを構成するには[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]**</span><span class="sxs-lookup"><span data-stu-id="fb513-111">**To configure a server instance for [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]**</span></span>  
  
-   [<span data-ttu-id="fb513-112">AlwaysOn 可用性グループの有効化と無効化 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fb513-112">Enable and Disable AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](enable-and-disable-always-on-availability-groups-sql-server.md)  
  
-   [<span data-ttu-id="fb513-113">AlwaysOn 可用性グループ &#40;SQL Server PowerShell のデータベースミラーリングエンドポイントを作成&#41;</span><span class="sxs-lookup"><span data-stu-id="fb513-113">Create a Database Mirroring Endpoint for AlwaysOn Availability Groups &#40;SQL Server PowerShell&#41;</span></span>](database-mirroring-always-on-availability-groups-powershell.md)  
  
-   [<span data-ttu-id="fb513-114">Windows 認証でのデータベース ミラーリング エンドポイントの作成 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="fb513-114">Create a Database Mirroring Endpoint for Windows Authentication &#40;Transact-SQL&#41;</span></span>](../../database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)  
  
-   [<span data-ttu-id="fb513-115">データベース ミラーリング エンドポイントで発信接続に証明書を使用できるようにする &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="fb513-115">Allow a Database Mirroring Endpoint to Use Certificates for Outbound Connections &#40;Transact-SQL&#41;</span></span>](../../database-mirroring/database-mirroring-use-certificates-for-outbound-connections.md)  
  
 <span data-ttu-id="fb513-116">**AlwaysOn 可用性グループの構成を開始するには**</span><span class="sxs-lookup"><span data-stu-id="fb513-116">**To get started with configuring AlwaysOn Availability Groups**</span></span>  
  
-   [<span data-ttu-id="fb513-117">はじめに AlwaysOn 可用性グループ &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fb513-117">Getting Started with AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](getting-started-with-always-on-availability-groups-sql-server.md)  
  
 <span data-ttu-id="fb513-118">**新しい可用性グループを作成して構成するには**</span><span class="sxs-lookup"><span data-stu-id="fb513-118">**To create and configure a new availability group**</span></span>  
  
-   [<span data-ttu-id="fb513-119">可用性グループ ウィザードの使用 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="fb513-119">Use the Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](use-the-availability-group-wizard-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="fb513-120">可用性グループの作成 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="fb513-120">Create an Availability Group &#40;Transact-SQL&#41;</span></span>](create-an-availability-group-transact-sql.md)  
  
-   [<span data-ttu-id="fb513-121">可用性グループの作成 &#40;SQL Server PowerShell&#41;</span><span class="sxs-lookup"><span data-stu-id="fb513-121">Create an Availability Group &#40;SQL Server PowerShell&#41;</span></span>](../../../powershell/sql-server-powershell.md)  
  
-   <span data-ttu-id="fb513-122">[[新しい可用性グループ] ダイアログ ボックスの使用 &#40;SQL Server Management Studio&#41;](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)</span><span class="sxs-lookup"><span data-stu-id="fb513-122">[Use the New Availability Group Dialog Box &#40;SQL Server Management Studio&#41;](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)</span></span>  
  
-   [<span data-ttu-id="fb513-123">可用性レプリカを追加または変更する場合のエンドポイント URL の指定 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fb513-123">Specify the Endpoint URL When Adding or Modifying an Availability Replica &#40;SQL Server&#41;</span></span>](specify-endpoint-url-adding-or-modifying-availability-replica.md)  
  
-   [<span data-ttu-id="fb513-124">可用性グループ リスナーの作成または構成 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fb513-124">Create or Configure an Availability Group Listener &#40;SQL Server&#41;</span></span>](create-or-configure-an-availability-group-listener-sql-server.md)  
  
-   [<span data-ttu-id="fb513-125">自動フェールオーバーの条件を制御する柔軟なフェールオーバー ポリシーの構成 (AlwaysOn 可用性グループ)</span><span class="sxs-lookup"><span data-stu-id="fb513-125">Configure the Flexible Failover Policy to Control Conditions for Automatic Failover (AlwaysOn Availability Groups)</span></span>](configure-flexible-automatic-failover-policy.md)  
  
-   [<span data-ttu-id="fb513-126">可用性レプリカでのバックアップの構成 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fb513-126">Configure Backup on Availability Replicas &#40;SQL Server&#41;</span></span>](configure-backup-on-availability-replicas-sql-server.md)  
  
-   [<span data-ttu-id="fb513-127">可用性レプリカでの読み取り専用アクセスの構成 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fb513-127">Configure Read-Only Access on an Availability Replica &#40;SQL Server&#41;</span></span>](configure-read-only-access-on-an-availability-replica-sql-server.md)  
  
-   [<span data-ttu-id="fb513-128">可用性グループの読み取り専用ルーティングの構成 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fb513-128">Configure Read-Only Routing for an Availability Group &#40;SQL Server&#41;</span></span>](configure-read-only-routing-for-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="fb513-129">可用性グループへのセカンダリ レプリカの参加 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fb513-129">Join a Secondary Replica to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="fb513-130">AlwaysOn セカンダリデータベース &#40;SQL Server でのデータ移動の開始&#41;</span><span class="sxs-lookup"><span data-stu-id="fb513-130">Start Data Movement on an AlwaysOn Secondary Database &#40;SQL Server&#41;</span></span>](start-data-movement-on-an-always-on-secondary-database-sql-server.md)  
  
-   [<span data-ttu-id="fb513-131">可用性グループに対するセカンダリ データベースの手動準備 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fb513-131">Manually Prepare a Secondary Database for an Availability Group &#40;SQL Server&#41;</span></span>](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="fb513-132">可用性グループへのセカンダリ データベースの参加 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fb513-132">Join a Secondary Database to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="fb513-133">可用性グループのデータベースのためのログインとジョブの管理 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fb513-133">Management of Logins and Jobs for the Databases of an Availability Group &#40;SQL Server&#41;</span></span>](../../logins-and-jobs-for-availability-group-databases.md)  
  
 <span data-ttu-id="fb513-134">**トラブルシューティングを行うには**</span><span class="sxs-lookup"><span data-stu-id="fb513-134">**To troubleshoot**</span></span>  
  
-   [<span data-ttu-id="fb513-135">AlwaysOn 可用性グループ構成 (SQL Server) の削除に関するトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="fb513-135">Troubleshoot AlwaysOn Availability Groups Configuration (SQL Server)deleted</span></span>](troubleshoot-always-on-availability-groups-configuration-sql-server.md)  
  
-   [<span data-ttu-id="fb513-136">失敗したファイルの追加操作のトラブルシューティング &#40;AlwaysOn 可用性グループ&#41;</span><span class="sxs-lookup"><span data-stu-id="fb513-136">Troubleshoot a Failed Add-File Operation &#40;AlwaysOn Availability Groups&#41;</span></span>](troubleshoot-a-failed-add-file-operation-always-on-availability-groups.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="fb513-137">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="fb513-137">Related Content</span></span>  
  
-   <span data-ttu-id="fb513-138">**ブログ:**</span><span class="sxs-lookup"><span data-stu-id="fb513-138">**Blogs:**</span></span>  
  
     [<span data-ttu-id="fb513-139">AlwaysON - HADRON 学習シリーズ:HADRON 対応データベースでのワーカー プールの使用</span><span class="sxs-lookup"><span data-stu-id="fb513-139">AlwaysON - HADRON Learning Series: Worker Pool Usage for HADRON Enabled Databases</span></span>](https://blogs.msdn.com/b/psssql/archive/2012/05/17/alwayson-hadron-learning-series-worker-pool-usage-for-hadron-enabled-databases.aspx)  
  
     [<span data-ttu-id="fb513-140">SQL Server AlwaysOn チームのブログ:SQL Server AlwaysOn チームのオフィシャル ブログ</span><span class="sxs-lookup"><span data-stu-id="fb513-140">SQL Server AlwaysOn Team Blogs: The official SQL Server AlwaysOn Team Blog</span></span>](https://blogs.msdn.com/b/sqlalwayson/)  
  
     [<span data-ttu-id="fb513-141">CSS SQL Server エンジニアのブログ</span><span class="sxs-lookup"><span data-stu-id="fb513-141">CSS SQL Server Engineers Blogs</span></span>](https://blogs.msdn.com/b/psssql/)  
  
-   <span data-ttu-id="fb513-142">**ビデオ:**</span><span class="sxs-lookup"><span data-stu-id="fb513-142">**Videos:**</span></span>  
  
     [<span data-ttu-id="fb513-143">Microsoft SQL Server コード ネーム "Denali" AlwaysOn シリーズ パート 1: 次世代の高可用性ソリューションの概要</span><span class="sxs-lookup"><span data-stu-id="fb513-143">Microsoft SQL Server Code-Named "Denali" AlwaysOn Series,Part 1: Introducing the Next Generation High Availability Solution</span></span>](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI302)  
  
     [<span data-ttu-id="fb513-144">Microsoft SQL Server コードネーム "Denali" AlwaysOn シリーズ パート 2: AlwaysOn を使用したミッション クリティカルな高可用性ソリューションの構築</span><span class="sxs-lookup"><span data-stu-id="fb513-144">Microsoft SQL Server Code-Named "Denali" AlwaysOn Series,Part 2: Building a Mission-Critical High Availability Solution Using AlwaysOn</span></span>](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI404)  
  
-   <span data-ttu-id="fb513-145">**ホワイト ペーパー:**</span><span class="sxs-lookup"><span data-stu-id="fb513-145">**Whitepapers:**</span></span>  
  
     [<span data-ttu-id="fb513-146">高可用性と災害復旧のための Microsoft SQL Server AlwaysOn ソリューション ガイド</span><span class="sxs-lookup"><span data-stu-id="fb513-146">Microsoft SQL Server AlwaysOn Solutions Guide for High Availability and Disaster Recovery</span></span>](https://go.microsoft.com/fwlink/?LinkId=227600)  
  
     [<span data-ttu-id="fb513-147">SQL Server 2012 に関する Microsoft ホワイト ペーパー</span><span class="sxs-lookup"><span data-stu-id="fb513-147">Microsoft White Papers for SQL Server 2012</span></span>](https://msdn.microsoft.com/library/hh403491.aspx)  
  
     [<span data-ttu-id="fb513-148">SQL Server ユーザー諮問チームのホワイト ペーパー</span><span class="sxs-lookup"><span data-stu-id="fb513-148">SQL Server Customer Advisory Team Whitepapers</span></span>](http://sqlcat.com/)  
  
## <a name="see-also"></a><span data-ttu-id="fb513-149">参照</span><span class="sxs-lookup"><span data-stu-id="fb513-149">See Also</span></span>  
 <span data-ttu-id="fb513-150">[AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="fb513-150">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="fb513-151">[可用性グループ &#40;SQL Server の管理&#41;](administration-of-an-availability-group-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="fb513-151">[Administration of an Availability Group &#40;SQL Server&#41;](administration-of-an-availability-group-sql-server.md) </span></span>  
 <span data-ttu-id="fb513-152">[AlwaysOn 可用性グループ (SQL Server) での運用上の問題のための AlwaysOn ポリシー](always-on-policies-for-operational-issues-always-on-availability.md) </span><span class="sxs-lookup"><span data-stu-id="fb513-152">[AlwaysOn Policies for Operational Issues with AlwaysOn Availability Groups (SQL Server)](always-on-policies-for-operational-issues-always-on-availability.md) </span></span>  
 <span data-ttu-id="fb513-153">[可用性グループの監視 &#40;SQL Server&#41;](monitoring-of-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="fb513-153">[Monitoring of Availability Groups &#40;SQL Server&#41;](monitoring-of-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="fb513-154">AlwaysOn 可用性グループの相互運用性 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="fb513-154">AlwaysOn Availability Groups: Interoperability (SQL Server)</span></span>](always-on-availability-groups-interoperability-sql-server.md)  
  
