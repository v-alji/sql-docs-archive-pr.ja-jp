---
title: Unicode 圧縮の実装 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Unicode data compression
- compression [SQL Server], Unicode data
ms.assetid: 44e69e60-9b35-43fe-b9c7-8cf34eaea62a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 4c928062169ed7feb03f1031362530474109976a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643954"
---
# <a name="unicode-compression-implementation"></a><span data-ttu-id="dd3bb-102">Unicode 圧縮の実装</span><span class="sxs-lookup"><span data-stu-id="dd3bb-102">Unicode Compression Implementation</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="dd3bb-103">では、Standard Compression Scheme for Unicode (SCSU) アルゴリズムの実装を使用して、行またはページの圧縮オブジェクトに格納する Unicode 値を圧縮します。</span><span class="sxs-lookup"><span data-stu-id="dd3bb-103">uses an implementation of the Standard Compression Scheme for Unicode (SCSU) algorithm to compress Unicode values that are stored in row or page compressed objects.</span></span> <span data-ttu-id="dd3bb-104">これらの圧縮オブジェクトでは、`nchar(n)` 列および `nvarchar(n)` 列の Unicode 圧縮が自動的に行われます。</span><span class="sxs-lookup"><span data-stu-id="dd3bb-104">For these compressed objects, Unicode compression is automatic for `nchar(n)` and `nvarchar(n)` columns.</span></span> <span data-ttu-id="dd3bb-105">[!INCLUDE[ssDE](../../includes/ssde-md.md)] では、ロケールに関係なく、Unicode データが 2 バイトで格納されます。</span><span class="sxs-lookup"><span data-stu-id="dd3bb-105">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] stores Unicode data as 2 bytes, regardless of locale.</span></span> <span data-ttu-id="dd3bb-106">これは UCS-2 エンコードと呼ばれています。</span><span class="sxs-lookup"><span data-stu-id="dd3bb-106">This is known as UCS-2 encoding.</span></span> <span data-ttu-id="dd3bb-107">ロケールによっては、SQL Server の SCSU 圧縮実装で保存できる最大領域がストレージ領域の 50% になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="dd3bb-107">For some locales, the implementation of SCSU compression in SQL Server can save up to 50 percent in storage space.</span></span>  
  
## <a name="supported-data-types"></a><span data-ttu-id="dd3bb-108">サポートされるデータ型</span><span class="sxs-lookup"><span data-stu-id="dd3bb-108">Supported Data Types</span></span>  
 <span data-ttu-id="dd3bb-109">Unicode 圧縮では、固定長の `nchar(n)` データ型および `nvarchar(n)` データ型がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="dd3bb-109">Unicode compression supports the fixed-length `nchar(n)` and `nvarchar(n)` data types.</span></span> <span data-ttu-id="dd3bb-110">行外または `nvarchar(max)` 列に格納されるデータ値は圧縮されません。</span><span class="sxs-lookup"><span data-stu-id="dd3bb-110">Data values that are stored off row or in `nvarchar(max)` columns are not compressed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dd3bb-111">行内に格納される場合であっても、`nvarchar(max)` データでは Unicode 圧縮がサポートされません。</span><span class="sxs-lookup"><span data-stu-id="dd3bb-111">Unicode compression is not supported for `nvarchar(max)` data even if it is stored in row.</span></span> <span data-ttu-id="dd3bb-112">ただし、このデータ型ではページ圧縮の利点を得ることができます。</span><span class="sxs-lookup"><span data-stu-id="dd3bb-112">However, this data type can still benefit from page compression.</span></span>  
  
## <a name="upgrading-from-earlier-versions-of-sql-server"></a><span data-ttu-id="dd3bb-113">以前のバージョンの SQL Server からのアップグレード</span><span class="sxs-lookup"><span data-stu-id="dd3bb-113">Upgrading from Earlier Versions of SQL Server</span></span>  
 <span data-ttu-id="dd3bb-114">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースを [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] にアップグレードした場合、圧縮されているか圧縮されていないかにかかわらず、データベース オブジェクトに対して Unicode 圧縮に関連する変更は加えられません。</span><span class="sxs-lookup"><span data-stu-id="dd3bb-114">When a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database is upgraded to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], Unicode compression-related changes are not made to any database object, compressed or uncompressed.</span></span> <span data-ttu-id="dd3bb-115">データベースのアップグレード後、オブジェクトには次のような影響があります。</span><span class="sxs-lookup"><span data-stu-id="dd3bb-115">After the database is upgraded, objects are affected as follows:</span></span>  
  
-   <span data-ttu-id="dd3bb-116">オブジェクトが圧縮されていない場合、何も変更は加えられず、オブジェクトは以前と同様に機能します。</span><span class="sxs-lookup"><span data-stu-id="dd3bb-116">If the object is not compressed, no changes are made and the object continues to function as it did previously.</span></span>  
  
-   <span data-ttu-id="dd3bb-117">行またはページ圧縮されたオブジェクトは、以前と同様に機能します。</span><span class="sxs-lookup"><span data-stu-id="dd3bb-117">Row- or page-compressed objects continue to function as they did previously.</span></span> <span data-ttu-id="dd3bb-118">圧縮されていないデータは、値が更新されない限り、圧縮されていない形式のままになります。</span><span class="sxs-lookup"><span data-stu-id="dd3bb-118">Uncompressed data remains in uncompressed form until its value is updated.</span></span>  
  
-   <span data-ttu-id="dd3bb-119">行またはページ圧縮されたテーブルに新しい行を挿入すると、Unicode 圧縮を使用して圧縮されます。</span><span class="sxs-lookup"><span data-stu-id="dd3bb-119">New rows that are inserted into a row- or page-compressed table are compressed using Unicode compression.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="dd3bb-120">Unicode 圧縮を十分に活用するには、ページまたは行の圧縮を使用してオブジェクトを再構築する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dd3bb-120">To take full advantage of the benefits of Unicode compression, the object must be rebuilt with page or row compression.</span></span>  
  
## <a name="how-unicode-compression-affects-data-storage"></a><span data-ttu-id="dd3bb-121">Unicode 圧縮によるデータ ストレージへの影響</span><span class="sxs-lookup"><span data-stu-id="dd3bb-121">How Unicode Compression Affects Data Storage</span></span>  
 <span data-ttu-id="dd3bb-122">行またはページの圧縮で圧縮されているテーブル内で、インデックスが作成または再構築されたときや値が変更されたとき、その影響を受けたインデックスまたは値は、圧縮後のサイズが現在のサイズより小さくなる場合に限り、圧縮して格納されます。</span><span class="sxs-lookup"><span data-stu-id="dd3bb-122">When an index is created or rebuilt or when a value is changed in a table that was compressed with row or page compression, the affected index or value is stored compressed only if its compressed size is less than its current size.</span></span> <span data-ttu-id="dd3bb-123">これにより、Unicode 圧縮によってテーブルの行またはインデックスのサイズが大きくなる状況が回避されます。</span><span class="sxs-lookup"><span data-stu-id="dd3bb-123">This prevents rows in a table or index from increasing in size because of Unicode compression.</span></span>  
  
 <span data-ttu-id="dd3bb-124">圧縮により節約されるストレージ領域は、圧縮されるデータの特性とデータのロケールによって異なります。</span><span class="sxs-lookup"><span data-stu-id="dd3bb-124">The storage space that compression saves depends on the characteristics of the data that is being compressed and the locale of the data.</span></span> <span data-ttu-id="dd3bb-125">次の表に、いくつかのロケールで節約できる領域の一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="dd3bb-125">The following table lists the space savings that can be achieved for several locales.</span></span>  
  
|<span data-ttu-id="dd3bb-126">Locale</span><span class="sxs-lookup"><span data-stu-id="dd3bb-126">Locale</span></span>|<span data-ttu-id="dd3bb-127">圧縮率</span><span class="sxs-lookup"><span data-stu-id="dd3bb-127">Compression percent</span></span>|  
|------------|-------------------------|  
|<span data-ttu-id="dd3bb-128">英語</span><span class="sxs-lookup"><span data-stu-id="dd3bb-128">English</span></span>|<span data-ttu-id="dd3bb-129">50%</span><span class="sxs-lookup"><span data-stu-id="dd3bb-129">50%</span></span>|  
|<span data-ttu-id="dd3bb-130">ドイツ語</span><span class="sxs-lookup"><span data-stu-id="dd3bb-130">German</span></span>|<span data-ttu-id="dd3bb-131">50%</span><span class="sxs-lookup"><span data-stu-id="dd3bb-131">50%</span></span>|  
|<span data-ttu-id="dd3bb-132">ヒンディー語</span><span class="sxs-lookup"><span data-stu-id="dd3bb-132">Hindi</span></span>|<span data-ttu-id="dd3bb-133">50%</span><span class="sxs-lookup"><span data-stu-id="dd3bb-133">50%</span></span>|  
|<span data-ttu-id="dd3bb-134">トルコ語</span><span class="sxs-lookup"><span data-stu-id="dd3bb-134">Turkish</span></span>|<span data-ttu-id="dd3bb-135">48%</span><span class="sxs-lookup"><span data-stu-id="dd3bb-135">48%</span></span>|  
|<span data-ttu-id="dd3bb-136">ベトナム語</span><span class="sxs-lookup"><span data-stu-id="dd3bb-136">Vietnamese</span></span>|<span data-ttu-id="dd3bb-137">39%</span><span class="sxs-lookup"><span data-stu-id="dd3bb-137">39%</span></span>|  
|<span data-ttu-id="dd3bb-138">日本語</span><span class="sxs-lookup"><span data-stu-id="dd3bb-138">Japanese</span></span>|<span data-ttu-id="dd3bb-139">15%</span><span class="sxs-lookup"><span data-stu-id="dd3bb-139">15%</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dd3bb-140">参照</span><span class="sxs-lookup"><span data-stu-id="dd3bb-140">See Also</span></span>  
 <span data-ttu-id="dd3bb-141">[データの圧縮](data-compression.md) </span><span class="sxs-lookup"><span data-stu-id="dd3bb-141">[Data Compression](data-compression.md) </span></span>  
 <span data-ttu-id="dd3bb-142">[sp_estimate_data_compression_savings &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-estimate-data-compression-savings-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="dd3bb-142">[sp_estimate_data_compression_savings &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-estimate-data-compression-savings-transact-sql) </span></span>  
 <span data-ttu-id="dd3bb-143">[ページの圧縮の実装](page-compression-implementation.md) </span><span class="sxs-lookup"><span data-stu-id="dd3bb-143">[Page Compression Implementation](page-compression-implementation.md) </span></span>  
 [<span data-ttu-id="dd3bb-144">sys.dm_db_persisted_sku_features &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="dd3bb-144">sys.dm_db_persisted_sku_features &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-persisted-sku-features-transact-sql)  
  
  
