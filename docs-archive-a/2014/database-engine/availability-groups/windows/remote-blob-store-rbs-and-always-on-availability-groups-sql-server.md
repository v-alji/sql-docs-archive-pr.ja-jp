---
title: リモート Blob ストア (RBS) と AlwaysOn 可用性グループ (SQL Server) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
ms.assetid: 01a70258-d4fd-40bc-bc44-c490b5d6c420
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f12a11162d286731b2b510a9051183e6c3025b2a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634065"
---
# <a name="remote-blob-store-rbs-and-alwayson-availability-groups-sql-server"></a><span data-ttu-id="57dcd-102">リモート BLOB ストア (RBS) と AlwaysOn 可用性グループ (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="57dcd-102">Remote Blob Store (RBS) and AlwaysOn Availability Groups (SQL Server)</span></span>
  [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]<span data-ttu-id="57dcd-103">では、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [リモート blob ストア (RBS)](../../../relational-databases/blob/remote-blob-store-rbs-sql-server.md) blob オブジェクト (blob) に対して高可用性とディザスターリカバリーのソリューションを提供できます。</span><span class="sxs-lookup"><span data-stu-id="57dcd-103">can provide a high-availability and disaster recovery solution for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)][Remote Blob Store (RBS)](../../../relational-databases/blob/remote-blob-store-rbs-sql-server.md) BLOB objects (blobs).</span></span> [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] <span data-ttu-id="57dcd-104">では、可用性データベースに格納されている RBS メタデータとスキーマをセカンダリ レプリカにレプリケートすることによってこれらを保護します。</span><span class="sxs-lookup"><span data-stu-id="57dcd-104">protects any RBS metadata and schemas stored in an availability database by replicating them to the secondary replicas.</span></span> <span data-ttu-id="57dcd-105">これは SharePoint コンテンツ データベースです。</span><span class="sxs-lookup"><span data-stu-id="57dcd-105">This is the SharePoint Content Database.</span></span> <span data-ttu-id="57dcd-106">一般に、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] には、この RBS メタデータが BLOB とは別に格納されます。</span><span class="sxs-lookup"><span data-stu-id="57dcd-106">Generally speaking, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] stores this RBS metadata independently from the blob.</span></span>  
  
 <span data-ttu-id="57dcd-107">次のように、RBD の BLOB データの保護は BLOB ストアの場所によって異なります。</span><span class="sxs-lookup"><span data-stu-id="57dcd-107">The protection for RBD BLOB data depends on the BLOB Store Location, as follows:</span></span>  
  
|<span data-ttu-id="57dcd-108">BLOB ストアの場所</span><span class="sxs-lookup"><span data-stu-id="57dcd-108">BLOB Store Location</span></span>|<span data-ttu-id="57dcd-109">可用性グループによるこの BLOB データの保護</span><span class="sxs-lookup"><span data-stu-id="57dcd-109">Can Availability Groups Protect This BLOB Data?</span></span>|  
|-------------------------|-----------------------------------------------------|  
|<span data-ttu-id="57dcd-110">RBS メタデータを含む同じデータベース (RBS リモート FILESTREAM プロバイダーを使用して格納)</span><span class="sxs-lookup"><span data-stu-id="57dcd-110">The same database that contains the RBS metadata  (stored using a RBS remote FILESTREAM provider)</span></span>|<span data-ttu-id="57dcd-111">はい</span><span class="sxs-lookup"><span data-stu-id="57dcd-111">Yes</span></span>|  
|<span data-ttu-id="57dcd-112">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の同じインスタンスにある別のデータベース (RBS リモート FILESTREAM プロバイダーを使用して格納)</span><span class="sxs-lookup"><span data-stu-id="57dcd-112">Another database in the same instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (stored using a RBS remote FILESTREAM provider)</span></span>|<span data-ttu-id="57dcd-113">はい</span><span class="sxs-lookup"><span data-stu-id="57dcd-113">Yes</span></span><br /><br /> <span data-ttu-id="57dcd-114">このデータベースは、RBS メタデータを含むデータベースと同じ可用性グループに含めることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="57dcd-114">We recommend that you put this database in the same availability group as the database that contains the RBS metadata.</span></span>|  
|<span data-ttu-id="57dcd-115">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の別のインスタンスにある別のデータベース (RBS リモート FILESTREAM プロバイダーを使用して格納)</span><span class="sxs-lookup"><span data-stu-id="57dcd-115">Another database in a different instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (stored using a RBS remote FILESTREAM provider)</span></span>|<span data-ttu-id="57dcd-116">はい</span><span class="sxs-lookup"><span data-stu-id="57dcd-116">Yes</span></span><br /><br /> <span data-ttu-id="57dcd-117">このデータベースは、別の可用性グループに含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="57dcd-117">This database must be in a separate availability group.</span></span>|  
|<span data-ttu-id="57dcd-118">サード パーティの BLOB ストア</span><span class="sxs-lookup"><span data-stu-id="57dcd-118">A third-party BLOB store</span></span>|<span data-ttu-id="57dcd-119">いいえ</span><span class="sxs-lookup"><span data-stu-id="57dcd-119">No</span></span><br /><br /> <span data-ttu-id="57dcd-120">この BLOB データを保護するには、BLOB ストア プロバイダーの高可用性メカニズムを使用します。</span><span class="sxs-lookup"><span data-stu-id="57dcd-120">To protect this BLOB data, use the high-availability mechanisms of the BLOB store provider.</span></span>|  
  
##  <a name="limitations"></a><a name="Limitations"></a> <span data-ttu-id="57dcd-121">制限事項</span><span class="sxs-lookup"><span data-stu-id="57dcd-121">Limitations</span></span>  
  
-   <span data-ttu-id="57dcd-122">RBS Maintainer は、プライマリ レプリカで対象にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="57dcd-122">RBS maintainers need to be targeted on the primary replica.</span></span>  
  
##  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="57dcd-123">推奨事項</span><span class="sxs-lookup"><span data-stu-id="57dcd-123">Recommendations</span></span>  
  
-   <span data-ttu-id="57dcd-124">可用性グループ リスナーを使用します。</span><span class="sxs-lookup"><span data-stu-id="57dcd-124">Use an availability group listener.</span></span> <span data-ttu-id="57dcd-125">詳細については、「 [可用性グループ リスナー、クライアント接続、およびアプリケーションのフェールオーバー &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md)での 1 つ以上の可用性グループの構成と管理において重要です。</span><span class="sxs-lookup"><span data-stu-id="57dcd-125">For more information, see [Availability Group Listeners, Client Connectivity, and Application Failover &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md).</span></span>  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="57dcd-126">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="57dcd-126">Related Content</span></span>  
  
-   <span data-ttu-id="57dcd-127">[リモート BLOB ストアのメンテナンス](https://msdn.microsoft.com/library/gg316773\(SQL.105\).aspx) ( [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] オンライン ブック)</span><span class="sxs-lookup"><span data-stu-id="57dcd-127">[Maintaining Remote BLOB Store](https://msdn.microsoft.com/library/gg316773\(SQL.105\).aspx) (in [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] Books Online)</span></span>  
  
-   <span data-ttu-id="57dcd-128">[RBS Maintainer の実行](https://blogs.msdn.com/b/sqlrbs/archive/2010/03/19/running-rbs-maintainer.aspx) (ブログ)</span><span class="sxs-lookup"><span data-stu-id="57dcd-128">[Running RBS Maintainer](https://blogs.msdn.com/b/sqlrbs/archive/2010/03/19/running-rbs-maintainer.aspx) (blog)</span></span>  
  
-   <span data-ttu-id="57dcd-129">[FILESTREAM プロバイダーでのリモート BLOB ストレージ (RBS) の構成 (SharePoint 2010)](https://blogs.msdn.com/b/mvpawardprogram/archive/2012/04/02/configure-remote-blob-storage-rbs-with-the-filestream-provider-sharepoint-2010.aspx) (ブログ)</span><span class="sxs-lookup"><span data-stu-id="57dcd-129">[Configure Remote BLOB Storage (RBS) with the FILESTREAM provider (SharePoint 2010)](https://blogs.msdn.com/b/mvpawardprogram/archive/2012/04/02/configure-remote-blob-storage-rbs-with-the-filestream-provider-sharepoint-2010.aspx) (blog)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57dcd-130">参照</span><span class="sxs-lookup"><span data-stu-id="57dcd-130">See Also</span></span>  
 <span data-ttu-id="57dcd-131">[AlwaysOn クライアント接続 &#40;SQL Server&#41;](always-on-client-connectivity-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="57dcd-131">[AlwaysOn Client Connectivity &#40;SQL Server&#41;](always-on-client-connectivity-sql-server.md) </span></span>  
 [<span data-ttu-id="57dcd-132">リモート BLOB ストア &#40;RBS&#41; &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="57dcd-132">Remote Blob Store &#40;RBS&#41; &#40;SQL Server&#41;</span></span>](../../../relational-databases/blob/remote-blob-store-rbs-sql-server.md)  
  
  
