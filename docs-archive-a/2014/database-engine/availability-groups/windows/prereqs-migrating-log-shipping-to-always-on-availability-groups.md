---
title: ログ配布から AlwaysOn 可用性グループへの移行の前提条件 (SQL Server) |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- log shipping [SQL Server], AlwaysOn Availability Groups
- Availability Groups [SQL Server], interoperability
ms.assetid: 2738ce65-205e-4682-92d8-dc7e37c58b2b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 76b50d5af8eb520b3764ff56397c040f2d0d0141
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718728"
---
# <a name="prerequisites-for-migrating-from-log-shipping-to-alwayson-availability-groups-sql-server"></a><span data-ttu-id="74032-102">ログ配布から AlwaysOn 可用性グループへの移行の前提条件 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="74032-102">Prerequisites for Migrating from Log Shipping to AlwaysOn Availability Groups (SQL Server)</span></span>
  <span data-ttu-id="74032-103">このトピックでは、ログ配布プライマリ データベースと 1 つまたは複数のセカンダリ データベースを、AlwaysOn プライマリ データベースとセカンダリ データベースに変換するための前提条件について説明します。</span><span class="sxs-lookup"><span data-stu-id="74032-103">This topic describes the prerequisites for converting a log shipping primary database along with one or more of its secondary databases to an AlwaysOn primary database and secondary database(s).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="74032-104">可用性グループのプライマリまたはセカンダリ データベース (場合によっては読み取り可能) は、ログ配布プライマリ データベースとして構成できます。</span><span class="sxs-lookup"><span data-stu-id="74032-104">You can configure any primary or secondary database (possibly readable) in an availability group as a log shipping primary database.</span></span>  
  
 <span data-ttu-id="74032-105">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="74032-105">**In This Topic:**</span></span>  
  
-   [<span data-ttu-id="74032-106">可用性グループの前提条件</span><span class="sxs-lookup"><span data-stu-id="74032-106">Availability Group Prerequisites</span></span>](#AGPrereqsRealAddress)  
  
-   [<span data-ttu-id="74032-107">ログ配布の前提条件</span><span class="sxs-lookup"><span data-stu-id="74032-107">Log Shipping Prerequisites</span></span>](#LogShipPrereqs)  
  
-   [<span data-ttu-id="74032-108">関連タスク</span><span class="sxs-lookup"><span data-stu-id="74032-108">Related Tasks</span></span>](#RelatedTasks)  
  
-   [<span data-ttu-id="74032-109">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="74032-109">Related Content</span></span>](#RelatedContent)  
  
##  <a name="availability-group-prerequisites"></a><a name="AGPrereqsRealAddress"></a><span data-ttu-id="74032-110">可用性グループの前提条件</span><span class="sxs-lookup"><span data-stu-id="74032-110">Availability Group Prerequisites</span></span>  
 <span data-ttu-id="74032-111">バックアップ ジョブを可用性グループのプライマリ レプリカ上で実行できるようにするには、AlwaysOn 可用性グループの次のバックアップ設定を使用します。</span><span class="sxs-lookup"><span data-stu-id="74032-111">To allow backup jobs to run on the primary replica of the availability group, use the following AlwaysOn Availability Groups backup settings:</span></span>  
  
|<span data-ttu-id="74032-112">プロパティ</span><span class="sxs-lookup"><span data-stu-id="74032-112">Property</span></span>|<span data-ttu-id="74032-113">設定</span><span class="sxs-lookup"><span data-stu-id="74032-113">Setting</span></span>|  
|--------------|-------------|  
|<span data-ttu-id="74032-114">可用性グループの自動バックアップ設定</span><span class="sxs-lookup"><span data-stu-id="74032-114">Automated backup preference of availability group</span></span>|<span data-ttu-id="74032-115">[プライマリ レプリカ上のみ]</span><span class="sxs-lookup"><span data-stu-id="74032-115">Only on the primary replica</span></span>|  
|<span data-ttu-id="74032-116">プライマリ レプリカのバックアップの優先順位。</span><span class="sxs-lookup"><span data-stu-id="74032-116">Backup priority of the primary replica.</span></span>|<span data-ttu-id="74032-117">>0</span><span class="sxs-lookup"><span data-stu-id="74032-117">>0</span></span>|  
  
 <span data-ttu-id="74032-118">**詳細情報:**</span><span class="sxs-lookup"><span data-stu-id="74032-118">**For more information:**</span></span>  
  
 [<span data-ttu-id="74032-119">可用性グループのプロパティの表示 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="74032-119">View Availability Group Properties &#40;SQL Server&#41;</span></span>](view-availability-group-properties-sql-server.md)  
  
 [<span data-ttu-id="74032-120">可用性レプリカでのバックアップの構成 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="74032-120">Configure Backup on Availability Replicas &#40;SQL Server&#41;</span></span>](configure-backup-on-availability-replicas-sql-server.md)  
  
##  <a name="log-shipping-prerequisites"></a><a name="LogShipPrereqs"></a><span data-ttu-id="74032-121">ログ配布の前提条件</span><span class="sxs-lookup"><span data-stu-id="74032-121">Log Shipping Prerequisites</span></span>  
  
-   <span data-ttu-id="74032-122">ログ配布プライマリ データベースは、可用性グループの初期/現在のプライマリ レプリカをホストしている [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスに存在している必要があります。</span><span class="sxs-lookup"><span data-stu-id="74032-122">The log shipping primary database must reside on the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that hosts the initial/current primary replica of the availability group.</span></span>  
  
-   <span data-ttu-id="74032-123">AlwaysOn セカンダリ データベースに変換するには、ログ配布セカンダリ データベースは次の条件を満たしている必要があります。</span><span class="sxs-lookup"><span data-stu-id="74032-123">For a given log shipping secondary database to be converted to an AlwaysOn secondary database, it must:</span></span>  
  
    -   <span data-ttu-id="74032-124">プライマリ データベースと同じ名前を使用している。</span><span class="sxs-lookup"><span data-stu-id="74032-124">Use the same name as the primary database.</span></span>  
  
    -   <span data-ttu-id="74032-125">可用性グループのセカンダリ レプリカをホストしているサーバー インスタンスに存在している。</span><span class="sxs-lookup"><span data-stu-id="74032-125">Reside on a server instance that hosts a secondary replica for the availability group.</span></span>  
  
 <span data-ttu-id="74032-126">バックアップ ジョブをプライマリ データベース上で実行した後は、バックアップ ジョブを無効にし、復元ジョブを特定のセカンダリ データベース上で実行した後は、復元ジョブを無効にします。</span><span class="sxs-lookup"><span data-stu-id="74032-126">Once the backup job has run on the primary database, disable the backup job, and once the restore job has run on a given secondary database, disable the restore job.</span></span>  
  
 <span data-ttu-id="74032-127">可用性グループのすべてのセカンダリ データベースを作成した後、セカンダリ レプリカにバックアップを実行する場合は、可用性グループの自動バックアップ設定を再構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="74032-127">After you have created all the secondary databases for the availability group, if you want to perform backups on secondary replicas, you need to re-configure the automated backup preference of the availability group.</span></span>  
  
 <span data-ttu-id="74032-128">**詳細情報:**</span><span class="sxs-lookup"><span data-stu-id="74032-128">**For more information:**</span></span>  
  
 <span data-ttu-id="74032-129">[可用性グループへのログ配布構成の変換](https://blogs.msdn.com/b/sqlalwayson/archive/2012/01/09/converting-a-logshipping-configuration-to-availability-group.aspx) (SQL Server ブログ)</span><span class="sxs-lookup"><span data-stu-id="74032-129">[Converting a logshipping configuration to Availability Group](https://blogs.msdn.com/b/sqlalwayson/archive/2012/01/09/converting-a-logshipping-configuration-to-availability-group.aspx) (a SQL Server blog)</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="74032-130">関連タスク</span><span class="sxs-lookup"><span data-stu-id="74032-130">Related Tasks</span></span>  
 <span data-ttu-id="74032-131">**ログ配布**</span><span class="sxs-lookup"><span data-stu-id="74032-131">**Log shipping**</span></span>  
  
-   [<span data-ttu-id="74032-132">ログ配布を SQL Server 2014 &#40;Transact-sql&#41;にアップグレードする</span><span class="sxs-lookup"><span data-stu-id="74032-132">Upgrade Log Shipping to SQL Server 2014 &#40;Transact-SQL&#41;</span></span>](../../log-shipping/upgrading-log-shipping-to-sql-server-2016-transact-sql.md)  
  
-   [<span data-ttu-id="74032-133">ログ配布の削除 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="74032-133">Remove Log Shipping &#40;SQL Server&#41;</span></span>](../../log-shipping/remove-log-shipping-sql-server.md)  
  
 <span data-ttu-id="74032-134">**AlwaysOn 可用性グループ**</span><span class="sxs-lookup"><span data-stu-id="74032-134">**AlwaysOn Availability Groups**</span></span>  
  
-   [<span data-ttu-id="74032-135">可用性グループ ウィザードの使用 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="74032-135">Use the Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](use-the-availability-group-wizard-sql-server-management-studio.md)  
  
-   <span data-ttu-id="74032-136">[[新しい可用性グループ] ダイアログ ボックスの使用 &#40;SQL Server Management Studio&#41;](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)</span><span class="sxs-lookup"><span data-stu-id="74032-136">[Use the New Availability Group Dialog Box &#40;SQL Server Management Studio&#41;](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)</span></span>  
  
-   [<span data-ttu-id="74032-137">可用性グループの作成 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="74032-137">Create an Availability Group &#40;Transact-SQL&#41;</span></span>](create-an-availability-group-transact-sql.md)  
  
-   [<span data-ttu-id="74032-138">可用性グループの作成 &#40;SQL Server PowerShell&#41;</span><span class="sxs-lookup"><span data-stu-id="74032-138">Create an Availability Group &#40;SQL Server PowerShell&#41;</span></span>](../../../powershell/sql-server-powershell.md)  
  
-   [<span data-ttu-id="74032-139">可用性グループへのセカンダリ データベースの参加 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="74032-139">Join a Secondary Database to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="74032-140">可用性レプリカでのバックアップの構成 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="74032-140">Configure Backup on Availability Replicas &#40;SQL Server&#41;</span></span>](configure-backup-on-availability-replicas-sql-server.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="74032-141">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="74032-141">Related Content</span></span>  
  
-   <span data-ttu-id="74032-142">**ブログ:**</span><span class="sxs-lookup"><span data-stu-id="74032-142">**Blogs:**</span></span>  
  
     [<span data-ttu-id="74032-143">可用性グループへのログ配布構成の変換</span><span class="sxs-lookup"><span data-stu-id="74032-143">Converting a logshipping configuration to Availability Group</span></span>](https://docs.microsoft.com/archive/blogs/sqlalwayson/converting-a-logshipping-configuration-to-availability-group)  
  
     [<span data-ttu-id="74032-144">Add a Log Shipping Primary Database and Secondary Database(s) to an Existing Availability Group</span><span class="sxs-lookup"><span data-stu-id="74032-144">Add a Log Shipping Primary Database and Secondary Database(s) to an Existing Availability Group</span></span>](https://docs.microsoft.com/archive/blogs/sqlalwayson/add-a-log-shipping-primary-database-and-secondary-databases-to-an-existing-availability-group)  
  
     [<span data-ttu-id="74032-145">SQL Server AlwaysOn チームのブログ:SQL Server AlwaysOn チームのオフィシャル ブログ</span><span class="sxs-lookup"><span data-stu-id="74032-145">SQL Server AlwaysOn Team Blogs: The official SQL Server AlwaysOn Team Blog</span></span>](https://docs.microsoft.com/archive/blogs/sqlalwayson/)  
  
     [<span data-ttu-id="74032-146">CSS SQL Server エンジニアのブログ</span><span class="sxs-lookup"><span data-stu-id="74032-146">CSS SQL Server Engineers Blogs</span></span>](https://blogs.msdn.com/b/psssql/)  
  
-   <span data-ttu-id="74032-147">**ホワイト ペーパー:**</span><span class="sxs-lookup"><span data-stu-id="74032-147">**Whitepapers:**</span></span>  
  
     [<span data-ttu-id="74032-148">Migration Guide: Migrating to AlwaysOn Availability Groups from Prior Deployments Combining Database Mirroring and Log Shipping</span><span class="sxs-lookup"><span data-stu-id="74032-148">Migration Guide: Migrating to AlwaysOn Availability Groups from Prior Deployments Combining Database Mirroring and Log Shipping</span></span>](https://msdn.microsoft.com/library/jj635217)  
  
     [<span data-ttu-id="74032-149">SQL Server 2012 に関する Microsoft ホワイト ペーパー</span><span class="sxs-lookup"><span data-stu-id="74032-149">Microsoft White Papers for SQL Server 2012</span></span>](https://msdn.microsoft.com/library/hh403491.aspx)  
  
     [<span data-ttu-id="74032-150">SQL Server ユーザー諮問チームのホワイト ペーパー</span><span class="sxs-lookup"><span data-stu-id="74032-150">SQL Server Customer Advisory Team Whitepapers</span></span>](http://sqlcat.com/)  
  
## <a name="see-also"></a><span data-ttu-id="74032-151">参照</span><span class="sxs-lookup"><span data-stu-id="74032-151">See Also</span></span>  
 <span data-ttu-id="74032-152">[ログ配布について &#40;SQL Server&#41;](../../log-shipping/about-log-shipping-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="74032-152">[About Log Shipping &#40;SQL Server&#41;](../../log-shipping/about-log-shipping-sql-server.md) </span></span>  
 <span data-ttu-id="74032-153">[AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="74032-153">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="74032-154">可用性グループの監視 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="74032-154">Monitoring of Availability Groups &#40;SQL Server&#41;</span></span>](monitoring-of-availability-groups-sql-server.md)  
  
  
