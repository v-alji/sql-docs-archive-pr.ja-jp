---
title: ページの圧縮の実装 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- page compression [Database Engine]
- compression [SQL Server], page
ms.assetid: 78c83277-1dbb-4e07-95bd-47b14d2b5cd4
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e6edba79d1548d68e60f406d370abd5354a62fcb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643959"
---
# <a name="page-compression-implementation"></a><span data-ttu-id="017d3-102">ページの圧縮の実装</span><span class="sxs-lookup"><span data-stu-id="017d3-102">Page Compression Implementation</span></span>
  <span data-ttu-id="017d3-103">このトピックでは、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] に実装されているページの圧縮方法の概要を説明します。</span><span class="sxs-lookup"><span data-stu-id="017d3-103">This topic summarizes how the [!INCLUDE[ssDE](../../includes/ssde-md.md)] implements page compression.</span></span> <span data-ttu-id="017d3-104">この概要では、データに必要なストレージ領域の計画に役立つ基本的な情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="017d3-104">This summary provides basic information to help you plan the storage space that you need for your data.</span></span>  
  
 <span data-ttu-id="017d3-105">ページの圧縮は、テーブル、テーブル パーティション、インデックス、およびインデックス パーティションに対して同じような方法で行われます。</span><span class="sxs-lookup"><span data-stu-id="017d3-105">Page compression is similar for tables, table partitions, indexes, and index partitions.</span></span> <span data-ttu-id="017d3-106">テーブルについてのページの圧縮に関する次の説明は、すべての種類のオブジェクトについてのページの圧縮に当てはまります。</span><span class="sxs-lookup"><span data-stu-id="017d3-106">The following description of page compression for a table applies equally to page compression for all object types.</span></span> <span data-ttu-id="017d3-107">次の例では文字列を圧縮しますが、プレフィックスの圧縮とディクショナリの圧縮の両方において、他のデータ型に同じ原則が当てはまります。</span><span class="sxs-lookup"><span data-stu-id="017d3-107">The following examples compress character strings, but both prefix and dictionary compression apply the same principles to other data types.</span></span>  
  
 <span data-ttu-id="017d3-108">ページの圧縮によるリーフ レベルのテーブルとインデックスの圧縮では、次の順番で 3 つの操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="017d3-108">Compressing the leaf level of tables and indexes with page compression consists of three operations in the following order:</span></span>  
  
1.  <span data-ttu-id="017d3-109">行の圧縮</span><span class="sxs-lookup"><span data-stu-id="017d3-109">Row compression</span></span>  
  
2.  <span data-ttu-id="017d3-110">プレフィックスの圧縮</span><span class="sxs-lookup"><span data-stu-id="017d3-110">Prefix compression</span></span>  
  
3.  <span data-ttu-id="017d3-111">ディクショナリの圧縮</span><span class="sxs-lookup"><span data-stu-id="017d3-111">Dictionary compression</span></span>  
  
 <span data-ttu-id="017d3-112">ページの圧縮を使用する場合、行の圧縮のみを使用して、リーフ レベル以外のページのインデックスが圧縮されます。</span><span class="sxs-lookup"><span data-stu-id="017d3-112">When you use page compression, non-leaf-level pages of indexes are compressed by using only row compression.</span></span> <span data-ttu-id="017d3-113">行の圧縮の詳細については、 [「行の圧縮の実装」](../data-compression/row-compression-implementation.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="017d3-113">For more information about row compression, see [Row Compression Implementation](../data-compression/row-compression-implementation.md).</span></span>  
  
## <a name="prefix-compression"></a><span data-ttu-id="017d3-114">プレフィックスの圧縮</span><span class="sxs-lookup"><span data-stu-id="017d3-114">Prefix Compression</span></span>  
 <span data-ttu-id="017d3-115">圧縮される各ページに対して、プレフィックスの圧縮では次の手順が実行されます。</span><span class="sxs-lookup"><span data-stu-id="017d3-115">For each page that is being compressed, prefix compression uses the following steps:</span></span>  
  
1.  <span data-ttu-id="017d3-116">列ごとに、各列の値についてストレージ領域の削減に使用できる値が識別されます。</span><span class="sxs-lookup"><span data-stu-id="017d3-116">For each column, a value is identified that can be used to reduce the storage space for the values in each column.</span></span>  
  
2.  <span data-ttu-id="017d3-117">各列のプレフィックス値を表す行が作成され、ページ ヘッダーの直後にある圧縮情報 (CI) 構造体に格納されます。</span><span class="sxs-lookup"><span data-stu-id="017d3-117">A row that represents the prefix values for each column is created and stored in the compression information (CI) structure that immediately follows the page header.</span></span>  
  
3.  <span data-ttu-id="017d3-118">列内の連続するプレフィックス値が、対応するプレフィックスへの参照に置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="017d3-118">The repeated prefix values in the column are replaced by a reference to the corresponding prefix.</span></span> <span data-ttu-id="017d3-119">行の値が選択されたプレフィックス値と完全に一致しなくても、部分的な一致を示すことができます。</span><span class="sxs-lookup"><span data-stu-id="017d3-119">If the value in a row does not exactly match the selected prefix value, a partial match can still be indicated.</span></span>  
  
 <span data-ttu-id="017d3-120">次の図に、プレフィックスの圧縮が行われる前のテーブルのサンプル ページを示します。</span><span class="sxs-lookup"><span data-stu-id="017d3-120">The following illustration shows a sample page of a table before prefix compression.</span></span>  
  
 <span data-ttu-id="017d3-121">![プレフィックスの圧縮前のページ](../media/skt-tblcompression1c.gif "プレフィックスの圧縮前のページ")</span><span class="sxs-lookup"><span data-stu-id="017d3-121">![Page before prefix compression](../media/skt-tblcompression1c.gif "Page before prefix compression")</span></span>  
  
 <span data-ttu-id="017d3-122">次の図に、プレフィックスの圧縮後の同じページを示します。</span><span class="sxs-lookup"><span data-stu-id="017d3-122">The following illustration shows the same page after prefix compression.</span></span> <span data-ttu-id="017d3-123">プレフィックスはヘッダーに移動され、列の値はプレフィックスへの参照に変更されます。</span><span class="sxs-lookup"><span data-stu-id="017d3-123">The prefix is moved to the header, and the column values are changed to references to the prefix.</span></span>  
  
 <span data-ttu-id="017d3-124">![プレフィックスの圧縮後のページ](../media/tblcompression2.gif "プレフィックスの圧縮後のページ")</span><span class="sxs-lookup"><span data-stu-id="017d3-124">![Page after prefix compression](../media/tblcompression2.gif "Page after prefix compression")</span></span>  
  
 <span data-ttu-id="017d3-125">1 行目の最初の列にある値 4b は、その行にプレフィックスの最初の 4 文字 (aaab) に加え、文字 b が存在することを示します。</span><span class="sxs-lookup"><span data-stu-id="017d3-125">In the first column of the first row, the value 4b indicates that the first four characters of the prefix (aaab) are present for that row, and also the character b.</span></span> <span data-ttu-id="017d3-126">これにより、結果の値は aaabb (元の値) になります。</span><span class="sxs-lookup"><span data-stu-id="017d3-126">This makes the resultant value aaabb, which is the original value.</span></span>  
  
## <a name="dictionary-compression"></a><span data-ttu-id="017d3-127">ディクショナリの圧縮</span><span class="sxs-lookup"><span data-stu-id="017d3-127">Dictionary Compression</span></span>  
 <span data-ttu-id="017d3-128">プレフィックスの圧縮が完了した後、ディクショナリの圧縮が適用されます。</span><span class="sxs-lookup"><span data-stu-id="017d3-128">After prefix compression has been completed, dictionary compression is applied.</span></span> <span data-ttu-id="017d3-129">ディクショナリの圧縮では、ページ上の任意の場所で繰り返される値を検索し、それらの値を CI 領域に格納します。</span><span class="sxs-lookup"><span data-stu-id="017d3-129">Dictionary compression searches for repeated values anywhere on the page, and stores them in the CI area.</span></span> <span data-ttu-id="017d3-130">プレフィックスの圧縮とは異なり、ディクショナリの圧縮は 1 つの列に制限されません。</span><span class="sxs-lookup"><span data-stu-id="017d3-130">Unlike prefix compression, dictionary compression is not restricted to one column.</span></span> <span data-ttu-id="017d3-131">ディクショナリの圧縮では、ページ上の任意の場所で繰り返し現れる値を置き換えることができます。</span><span class="sxs-lookup"><span data-stu-id="017d3-131">Dictionary compression can replace repeated values that occur anywhere on a page.</span></span> <span data-ttu-id="017d3-132">次の図に、ディクショナリの圧縮後の同じページを示します。</span><span class="sxs-lookup"><span data-stu-id="017d3-132">The following illustration shows the same page after dictionary compression.</span></span>  
  
 <span data-ttu-id="017d3-133">![ディクショナリの圧縮後のページ](../media/tblcompression3.gif "ディクショナリの圧縮後のページ")</span><span class="sxs-lookup"><span data-stu-id="017d3-133">![Page after dictionary compression](../media/tblcompression3.gif "Page after dictionary compression")</span></span>  
  
 <span data-ttu-id="017d3-134">値 4b がページのさまざまな列から参照されていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="017d3-134">Note that the value 4b has been referenced from different columns of the page.</span></span>  
  
## <a name="when-page-compression-occurs"></a><span data-ttu-id="017d3-135">ページの圧縮が行われるタイミング</span><span class="sxs-lookup"><span data-stu-id="017d3-135">When Page Compression Occurs</span></span>  
 <span data-ttu-id="017d3-136">ページの圧縮を含む新しいテーブルを作成した場合、圧縮は行われません。</span><span class="sxs-lookup"><span data-stu-id="017d3-136">When a new table is created that has page compression, no compression occurs.</span></span> <span data-ttu-id="017d3-137">ただし、テーブルのメタデータで、ページの圧縮を使用する必要があることが示されます。</span><span class="sxs-lookup"><span data-stu-id="017d3-137">However, the metadata for the table indicates that page compression should be used.</span></span> <span data-ttu-id="017d3-138">データが最初のデータ ページに追加されると、データに対して行の圧縮が行われます。</span><span class="sxs-lookup"><span data-stu-id="017d3-138">As data is added to the first data page, data is row-compressed.</span></span> <span data-ttu-id="017d3-139">このページはいっぱいではないため、ページの圧縮による利点は得られません。</span><span class="sxs-lookup"><span data-stu-id="017d3-139">Because the page is not full, no benefit is gained from page compression.</span></span> <span data-ttu-id="017d3-140">ページがいっぱいになると、次の行を追加することによって、ページの圧縮操作が開始されます。</span><span class="sxs-lookup"><span data-stu-id="017d3-140">When the page is full, the next row to be added initiates the page compression operation.</span></span> <span data-ttu-id="017d3-141">ページ全体が確認され、各列でプレフィックスの圧縮が評価された後、すべての列でディクショナリの圧縮が評価されます。</span><span class="sxs-lookup"><span data-stu-id="017d3-141">The whole page is reviewed; each column is evaluated for prefix compression, and then all columns are evaluated for dictionary compression.</span></span> <span data-ttu-id="017d3-142">ページの圧縮により、ページ上に行を追加するための十分な領域が作成されると、行が追加され、行とページの両方でデータが圧縮されます。</span><span class="sxs-lookup"><span data-stu-id="017d3-142">If page compression has created enough room on the page for an additional row, the row is added, and the data is both row- and page-compressed.</span></span> <span data-ttu-id="017d3-143">ページの圧縮によって確保される領域から、CI 構造体に必要な領域を引いた領域が小さい場合は、そのページに対してページの圧縮は使用されません。</span><span class="sxs-lookup"><span data-stu-id="017d3-143">If the space gained by page compression minus the space that is required for the CI structure is not significant, page compression is not used for that page.</span></span> <span data-ttu-id="017d3-144">それ以降に追加される行はこの新しいページ内に格納されます。行が収まらない場合は、別の新しいページがテーブルに追加されます。</span><span class="sxs-lookup"><span data-stu-id="017d3-144">Future rows either fit onto the new page or, if they do not fit, a new page is added to the table.</span></span> <span data-ttu-id="017d3-145">最初のページと同様に、新しいページでは最初にページの圧縮は行われません。</span><span class="sxs-lookup"><span data-stu-id="017d3-145">Similar to the first page, the new page is not at first page-compressed.</span></span>  
  
 <span data-ttu-id="017d3-146">データが含まれる既存のテーブルがページの圧縮対象に変わると、各ページは再構築され、評価されます。</span><span class="sxs-lookup"><span data-stu-id="017d3-146">When an existing table that contains data is converted to page compression, each page is rebuilt and evaluated.</span></span> <span data-ttu-id="017d3-147">すべてのページが再構築されると、テーブル、インデックス、またはパーティションも再構築されます。</span><span class="sxs-lookup"><span data-stu-id="017d3-147">Rebuilding all the pages causes the rebuilding of the table, index, or partition.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="017d3-148">参照</span><span class="sxs-lookup"><span data-stu-id="017d3-148">See Also</span></span>  
 <span data-ttu-id="017d3-149">[データの圧縮](data-compression.md) </span><span class="sxs-lookup"><span data-stu-id="017d3-149">[Data Compression](data-compression.md) </span></span>  
 [<span data-ttu-id="017d3-150">行の圧縮の実装</span><span class="sxs-lookup"><span data-stu-id="017d3-150">Row Compression Implementation</span></span>](row-compression-implementation.md)  
  
  
