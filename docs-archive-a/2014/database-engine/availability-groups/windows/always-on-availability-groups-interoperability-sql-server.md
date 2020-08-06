---
title: Always On 可用性グループの相互運用性 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], about
- Availability Groups [SQL Server], interoperability
ms.assetid: daf87f90-2623-42ca-912c-b8f07d210510
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: bbd9de348b2e36feefd7efea52dee0b8c13a9f34
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632711"
---
# <a name="always-on-availability-groups-interoperability-sql-server"></a><span data-ttu-id="b7df3-102">Always On 可用性グループの相互運用性 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="b7df3-102">Always On Availability Groups: Interoperability (SQL Server)</span></span>
  <span data-ttu-id="b7df3-103">このトピックでは、 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] の他の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 機能との間の [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]の相互運用性について説明します。</span><span class="sxs-lookup"><span data-stu-id="b7df3-103">This topic documents interoperability of [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] with other [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] features in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>  
  

  
##  <a name="features-that-interoperate-with-alwayson-availability-groups"></a><a name="Interop"></a><span data-ttu-id="b7df3-104">AlwaysOn 可用性グループと相互運用可能な機能</span><span class="sxs-lookup"><span data-stu-id="b7df3-104">Features That Interoperate with AlwaysOn Availability Groups</span></span>  
 <span data-ttu-id="b7df3-105">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] で [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] と相互運用可能な [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]機能を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="b7df3-105">The following table lists [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] features that interoperate with [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="b7df3-106">**詳細情報** 列のリンクは、特定の機能に関して相互運用性に関する考慮事項が存在することを示します。</span><span class="sxs-lookup"><span data-stu-id="b7df3-106">A link in the **More Information** column indicates that interoperability considerations exist for a given feature.</span></span>  
  
|<span data-ttu-id="b7df3-107">機能</span><span class="sxs-lookup"><span data-stu-id="b7df3-107">Feature</span></span>|<span data-ttu-id="b7df3-108">説明</span><span class="sxs-lookup"><span data-stu-id="b7df3-108">More Information</span></span>|  
|-------------|----------------------|  
|<span data-ttu-id="b7df3-109">変更データ キャプチャ</span><span class="sxs-lookup"><span data-stu-id="b7df3-109">Change data capture</span></span>|[<span data-ttu-id="b7df3-110">レプリケーション、Change Tracking、変更データキャプチャ、AlwaysOn 可用性グループ &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="b7df3-110">Replication, Change Tracking, Change Data Capture, and AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](replicate-track-change-data-capture-always-on-availability.md)|  
|<span data-ttu-id="b7df3-111">Change tracking</span><span class="sxs-lookup"><span data-stu-id="b7df3-111">Change tracking</span></span>|[<span data-ttu-id="b7df3-112">レプリケーション、Change Tracking、変更データキャプチャ、AlwaysOn 可用性グループ &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="b7df3-112">Replication, Change Tracking, Change Data Capture, and AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](replicate-track-change-data-capture-always-on-availability.md)|  
|<span data-ttu-id="b7df3-113">包含データベース</span><span class="sxs-lookup"><span data-stu-id="b7df3-113">Contained databases</span></span>|[<span data-ttu-id="b7df3-114">包含データベースと AlwaysOn 可用性グループ (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="b7df3-114">Contained Databases with AlwaysOn Availability Groups (SQL Server)</span></span>](always-on-availability-groups-sql-server.md)|  
|<span data-ttu-id="b7df3-115">データベース暗号化</span><span class="sxs-lookup"><span data-stu-id="b7df3-115">Database encryption</span></span>|[<span data-ttu-id="b7df3-116">AlwaysOn 可用性グループ &#40;SQL Server を持つ暗号化されたデータベース&#41;</span><span class="sxs-lookup"><span data-stu-id="b7df3-116">Encrypted Databases with AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](encrypted-databases-with-always-on-availability-groups-sql-server.md)|  
|<span data-ttu-id="b7df3-117">データベース スナップショット</span><span class="sxs-lookup"><span data-stu-id="b7df3-117">Database snapshots</span></span>|[<span data-ttu-id="b7df3-118">AlwaysOn 可用性グループ &#40;SQL Server を持つデータベーススナップショット&#41;</span><span class="sxs-lookup"><span data-stu-id="b7df3-118">Database Snapshots with AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](database-snapshots-with-always-on-availability-groups-sql-server.md)|  
|<span data-ttu-id="b7df3-119">FILESTREAM と FileTable</span><span class="sxs-lookup"><span data-stu-id="b7df3-119">FILESTREAM and FileTable</span></span>|[<span data-ttu-id="b7df3-120">AlwaysOn 可用性グループ &#40;SQL Server を使用した FILESTREAM と FileTable&#41;</span><span class="sxs-lookup"><span data-stu-id="b7df3-120">FILESTREAM and FileTable with AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](filestream-and-filetable-with-always-on-availability-groups-sql-server.md)|  
|<span data-ttu-id="b7df3-121">フルテキスト検索</span><span class="sxs-lookup"><span data-stu-id="b7df3-121">Full-text search</span></span>|<span data-ttu-id="b7df3-122">注: フルテキスト インデックスは、AlwaysOn セカンダリ データベースと同期されます。</span><span class="sxs-lookup"><span data-stu-id="b7df3-122">Note: Full-Text indexes are synchronized with AlwaysOn secondary databases.</span></span>|  
|<span data-ttu-id="b7df3-123">ログ配布</span><span class="sxs-lookup"><span data-stu-id="b7df3-123">Log shipping</span></span>|[<span data-ttu-id="b7df3-124">ログ配布から AlwaysOn 可用性グループ &#40;SQL Server への移行の前提条件&#41;</span><span class="sxs-lookup"><span data-stu-id="b7df3-124">Prerequisites for Migrating from Log Shipping to AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](prereqs-migrating-log-shipping-to-always-on-availability-groups.md)|  
|<span data-ttu-id="b7df3-125">リモート BLOB ストア (RBS)</span><span class="sxs-lookup"><span data-stu-id="b7df3-125">Remote Blob Store (RBS)</span></span>|[<span data-ttu-id="b7df3-126">リモート Blob ストア &#40;RBS&#41; と AlwaysOn 可用性グループ &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="b7df3-126">Remote Blob Store &#40;RBS&#41; and AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](remote-blob-store-rbs-and-always-on-availability-groups-sql-server.md)|  
|<span data-ttu-id="b7df3-127">レプリケーション[で AlwaysOn 可用性グループのレプリケーションを構成する (SQL Server)](configure-replication-for-always-on-availability-groups-sql-server.md)</span><span class="sxs-lookup"><span data-stu-id="b7df3-127">Replication[Configure Replication for AlwaysOn Availability Groups (SQL Server)](configure-replication-for-always-on-availability-groups-sql-server.md)</span></span><br /><br /> [<span data-ttu-id="b7df3-128">AlwaysOn パブリケーションデータベースのメンテナンス &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="b7df3-128">Maintaining an AlwaysOn Publication Database &#40;SQL Server&#41;</span></span>](maintaining-an-always-on-publication-database-sql-server.md)<br /><br /> [<span data-ttu-id="b7df3-129">レプリケーション、Change Tracking、変更データキャプチャ、AlwaysOn 可用性グループ &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="b7df3-129">Replication, Change Tracking, Change Data Capture, and AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](replicate-track-change-data-capture-always-on-availability.md)<br /><br /> [<span data-ttu-id="b7df3-130">レプリケーションサブスクライバーと AlwaysOn 可用性グループ &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="b7df3-130">Replication Subscribers and AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](replication-subscribers-and-always-on-availability-groups-sql-server.md)|  
|<span data-ttu-id="b7df3-131">Analysis Services</span><span class="sxs-lookup"><span data-stu-id="b7df3-131">Analysis Services</span></span>|[<span data-ttu-id="b7df3-132">Analysis Services と AlwaysOn 可用性グループ</span><span class="sxs-lookup"><span data-stu-id="b7df3-132">Analysis Services with AlwaysOn Availability Groups</span></span>](analysis-services-with-always-on-availability-groups.md)|  
|<span data-ttu-id="b7df3-133">Reporting Services</span><span class="sxs-lookup"><span data-stu-id="b7df3-133">Reporting Services</span></span>|<span data-ttu-id="b7df3-134">読み取り専用セカンダリ レプリカをレポート データ ソースとして使用し、読み取り/書き込み可能なプライマリ レプリカの負荷を軽減します。</span><span class="sxs-lookup"><span data-stu-id="b7df3-134">Utilize read only secondary replicas as a reporting data source and reduce the load on your primary read-write replica.</span></span><br /><br /> [<span data-ttu-id="b7df3-135">Reporting Services AlwaysOn 可用性グループ &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="b7df3-135">Reporting Services with AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](reporting-services-with-always-on-availability-groups-sql-server.md)|  
|<span data-ttu-id="b7df3-136">Service Broker</span><span class="sxs-lookup"><span data-stu-id="b7df3-136">Service Broker</span></span>|[<span data-ttu-id="b7df3-137">Service Broker AlwaysOn 可用性グループ &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="b7df3-137">Service Broker with AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](service-broker-with-always-on-availability-groups-sql-server.md)|  
|<span data-ttu-id="b7df3-138">SQL Server エージェント</span><span class="sxs-lookup"><span data-stu-id="b7df3-138">SQL Server Agent</span></span>||  
  
##  <a name="features-that-do-not-interoperate-with-alwayson-availability-groups"></a><a name="NoInterop"></a><span data-ttu-id="b7df3-139">AlwaysOn 可用性グループと相互運用できない機能</span><span class="sxs-lookup"><span data-stu-id="b7df3-139">Features that Do Not Interoperate with AlwaysOn Availability Groups</span></span>  
 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] <span data-ttu-id="b7df3-140">は、次の機能との相互運用はできません。</span><span class="sxs-lookup"><span data-stu-id="b7df3-140">does not interoperate with the following features:</span></span>  
  
-   <span data-ttu-id="b7df3-141">複数データベースにまたがるトランザクション/分散トランザクション</span><span class="sxs-lookup"><span data-stu-id="b7df3-141">Cross-database transactions/distributed transactions</span></span>  
  
     <span data-ttu-id="b7df3-142">このようなトランザクションがサポートされない理由の詳細については、「[データベース ミラーリングまたは AlwaysOn 可用性グループではサポートされない複数データベースにまたがるトランザクション &#40;SQL Server&#41;](transactions-always-on-availability-and-database-mirroring.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b7df3-142">For information about why such transactions are not supported, see [Cross-Database Transactions Not Supported For Database Mirroring or AlwaysOn Availability Groups &#40;SQL Server&#41;](transactions-always-on-availability-and-database-mirroring.md).</span></span>  
  
-   <span data-ttu-id="b7df3-143">データベース ミラーリング</span><span class="sxs-lookup"><span data-stu-id="b7df3-143">Database mirroring</span></span>  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="b7df3-144">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="b7df3-144">Related Content</span></span>  
  
-   <span data-ttu-id="b7df3-145">**ブログ:**</span><span class="sxs-lookup"><span data-stu-id="b7df3-145">**Blogs:**</span></span>  
  
     [<span data-ttu-id="b7df3-146">移行ガイド：以前のクラスタリングおよびミラーリングの展開によるSQL Server 2012フェールオーバークラスタリングおよび可用性グループへの移行</span><span class="sxs-lookup"><span data-stu-id="b7df3-146">Migration Guide: Migrating to SQL Server 2012 Failover Clustering and Availability Groups from Prior Clustering and Mirroring Deployments</span></span>](https://blogs.msdn.com/b/sqlalwayson/archive/2012/04/09/now-available-migration-guide-migrating-to-sql-server-2012-failover-clustering-and-availability-groups-from-prior-clustering-and-mirroring-deployments.aspx)  
  
     [<span data-ttu-id="b7df3-147">SQL Server AlwaysOn チームのブログ:SQL Server AlwaysOn チームのオフィシャル ブログ</span><span class="sxs-lookup"><span data-stu-id="b7df3-147">SQL Server AlwaysOn Team Blogs: The official SQL Server AlwaysOn Team Blog</span></span>](https://blogs.msdn.com/b/sqlalwayson/)  
  
     [<span data-ttu-id="b7df3-148">CSS SQL Server エンジニアのブログ</span><span class="sxs-lookup"><span data-stu-id="b7df3-148">CSS SQL Server Engineers Blogs</span></span>](https://blogs.msdn.com/b/psssql/)  
  
-   <span data-ttu-id="b7df3-149">**ホワイト ペーパー:**</span><span class="sxs-lookup"><span data-stu-id="b7df3-149">**Whitepapers:**</span></span>  
  
     [<span data-ttu-id="b7df3-150">Migration Guide: Migrating to AlwaysOn Availability Groups from Prior Deployments Combining Database Mirroring and Log Shipping</span><span class="sxs-lookup"><span data-stu-id="b7df3-150">Migration Guide: Migrating to AlwaysOn Availability Groups from Prior Deployments Combining Database Mirroring and Log Shipping</span></span>](https://msdn.microsoft.com/library/jj635217)  
  
     [<span data-ttu-id="b7df3-151">高可用性と災害復旧のための Microsoft SQL Server AlwaysOn ソリューション ガイド</span><span class="sxs-lookup"><span data-stu-id="b7df3-151">Microsoft SQL Server AlwaysOn Solutions Guide for High Availability and Disaster Recovery</span></span>](https://go.microsoft.com/fwlink/?LinkId=227600)  
  
     [<span data-ttu-id="b7df3-152">SQL Server 2012 に関する Microsoft ホワイト ペーパー</span><span class="sxs-lookup"><span data-stu-id="b7df3-152">Microsoft White Papers for SQL Server 2012</span></span>](https://msdn.microsoft.com/library/hh403491.aspx)  
  
     [<span data-ttu-id="b7df3-153">SQL Server ユーザー諮問チームのホワイト ペーパー</span><span class="sxs-lookup"><span data-stu-id="b7df3-153">SQL Server Customer Advisory Team Whitepapers</span></span>](http://sqlcat.com/)  
  
## <a name="see-also"></a><span data-ttu-id="b7df3-154">参照</span><span class="sxs-lookup"><span data-stu-id="b7df3-154">See Also</span></span>  
 <span data-ttu-id="b7df3-155">[AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="b7df3-155">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="b7df3-156">AlwaysOn 可用性グループ &#40;SQL Server の前提条件、制限事項、推奨事項&#41;</span><span class="sxs-lookup"><span data-stu-id="b7df3-156">Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](prereqs-restrictions-recommendations-always-on-availability.md)  
  
  
