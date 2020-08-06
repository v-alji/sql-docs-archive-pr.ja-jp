---
title: ヒープ (クラスター化インデックスなしのテーブル) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- heaps
ms.assetid: df5c4dfb-d372-4d0f-859a-a2d2533ee0d7
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2a39bac2e0352f2adc7749e980d5cc91044f8ab2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645066"
---
# <a name="heaps-tables-without-clustered-indexes"></a><span data-ttu-id="4e5ab-102">ヒープ (クラスター化インデックスなしのテーブル)</span><span class="sxs-lookup"><span data-stu-id="4e5ab-102">Heaps (Tables without Clustered Indexes)</span></span>
  <span data-ttu-id="4e5ab-103">ヒープとはクラスター化インデックスを使用しないテーブルのことです。</span><span class="sxs-lookup"><span data-stu-id="4e5ab-103">A heap is a table without a clustered index.</span></span> <span data-ttu-id="4e5ab-104">1 つまたは複数の非クラスター化インデックスを、ヒープとして格納されているテーブルに作成することができます。</span><span class="sxs-lookup"><span data-stu-id="4e5ab-104">One or more nonclustered indexes can be created on tables stored as a heap.</span></span> <span data-ttu-id="4e5ab-105">ヒープには、順序を指定せずにデータが格納されます。</span><span class="sxs-lookup"><span data-stu-id="4e5ab-105">Data is stored in the heap without specifying an order.</span></span> <span data-ttu-id="4e5ab-106">通常、最初にデータが格納される順序はテーブルに行が挿入された順序と同じですが、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] では行を効率的に格納できるようにヒープ内でデータが移動される場合があるため、データの順序は予測できません。</span><span class="sxs-lookup"><span data-stu-id="4e5ab-106">Usually data is initially stored in the order in which is the rows are inserted into the table, but the [!INCLUDE[ssDE](../../includes/ssde-md.md)] can move data around in the heap to store the rows efficiently; so the data order cannot be predicted.</span></span> <span data-ttu-id="4e5ab-107">ヒープから返される行の順序を保証するには、`ORDER BY` 句を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4e5ab-107">To guarantee the order of rows returned from a heap, you must use the `ORDER BY` clause.</span></span> <span data-ttu-id="4e5ab-108">テーブルにクラスター化インデックスを作成し、テーブルがヒープにならないようにすることで、行が格納される順序を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="4e5ab-108">To specify the order for storage of the rows, create a clustered index on the table, so that the table is not a heap.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4e5ab-109">クラスター化インデックスを作成する代わりにテーブルをヒープのままにしておくとよい場合もありますが、ヒープを効果的に使用するには高度なスキルが必要です。</span><span class="sxs-lookup"><span data-stu-id="4e5ab-109">There are sometimes good reasons to leave a table as a heap instead of creating a clustered index, but using heaps effectively is an advanced skill.</span></span> <span data-ttu-id="4e5ab-110">テーブルをヒープのままにしておく妥当な理由がない限り、ほとんどのテーブルには、慎重に選択されたクラスター化インデックスが必要です。</span><span class="sxs-lookup"><span data-stu-id="4e5ab-110">Most tables should have a carefully chosen clustered index unless a good reason exists for leaving the table as a heap.</span></span>  
  
## <a name="when-to-use-a-heap"></a><span data-ttu-id="4e5ab-111">ヒープを使用する場合</span><span class="sxs-lookup"><span data-stu-id="4e5ab-111">When to Use a Heap</span></span>  
 <span data-ttu-id="4e5ab-112">非クラスター化インデックスのないヒープ テーブルの場合、行を検索するには (テーブル スキャンで) テーブル全体を調べる必要があります。</span><span class="sxs-lookup"><span data-stu-id="4e5ab-112">If a table is a heap and does not have any nonclustered indexes, then the entire table must be examined (a table scan) to find any row.</span></span> <span data-ttu-id="4e5ab-113">企業の 12 の支社の一覧など、テーブルが小さい場合にはこの方法で対応できます。</span><span class="sxs-lookup"><span data-stu-id="4e5ab-113">This can be acceptable when the table is tiny, such as a list of the 12 regional offices of a company.</span></span>  
  
 <span data-ttu-id="4e5ab-114">テーブルがヒープとして格納されている場合、各行の識別には、ファイル番号、データ ページ番号、およびページのスロットで構成された行識別子 (RID) が使用されます。</span><span class="sxs-lookup"><span data-stu-id="4e5ab-114">When a table is stored as a heap, individual rows are identified by reference to a row identifier (RID) consisting of the file number, data page number, and slot on the page.</span></span> <span data-ttu-id="4e5ab-115">行識別子 (ROWID) には、小さく効率的な構造が使用されています。</span><span class="sxs-lookup"><span data-stu-id="4e5ab-115">The row id is a small and efficient structure.</span></span> <span data-ttu-id="4e5ab-116">データ設計者は、データが常に非クラスター化インデックスを通じてアクセスされ、RID がクラスター化インデックス キーより小さい場合に、ヒープを使用することもあります。</span><span class="sxs-lookup"><span data-stu-id="4e5ab-116">Sometimes data architects use heaps when data is always accessed through nonclustered indexes and the RID is smaller than a clustered index key.</span></span>  
  
## <a name="when-not-to-use-a-heap"></a><span data-ttu-id="4e5ab-117">ヒープを使用しない場合</span><span class="sxs-lookup"><span data-stu-id="4e5ab-117">When Not to Use a Heap</span></span>  
 <span data-ttu-id="4e5ab-118">データが、並べ替えた順序で頻繁に取得される場合は、ヒープを使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="4e5ab-118">Do not use a heap when the data is frequently returned in a sorted order.</span></span> <span data-ttu-id="4e5ab-119">並べ替え用の列にクラスター化インデックスが存在すると、並べ替え操作が実行されない場合があります。</span><span class="sxs-lookup"><span data-stu-id="4e5ab-119">A clustered index on the sorting column could avoid the sorting operation.</span></span>  
  
 <span data-ttu-id="4e5ab-120">データが頻繁にグループ化される場合は、ヒープを使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="4e5ab-120">Do not use a heap when the data is frequently grouped together.</span></span> <span data-ttu-id="4e5ab-121">データの並べ替えはグループ化よりも前に行う必要がありますが、並べ替え用の列にクラスター化インデックスが存在すると、並べ替え操作が実行されない場合があります。</span><span class="sxs-lookup"><span data-stu-id="4e5ab-121">Data must be sorted before it is grouped, and a clustered index on the sorting column could avoid the sorting operation.</span></span>  
  
 <span data-ttu-id="4e5ab-122">広範囲のデータがテーブルから頻繁に照会される場合は、ヒープを使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="4e5ab-122">Do not use a heap when ranges of data are frequently queried from the table.</span></span>  <span data-ttu-id="4e5ab-123">範囲列にクラスター化インデックスが存在すると、ヒープ全体の並べ替えが実行されなくなります。</span><span class="sxs-lookup"><span data-stu-id="4e5ab-123">A clustered index on the range column will avoid sorting the entire heap.</span></span>  
  
 <span data-ttu-id="4e5ab-124">非クラスター化インデックスが存在せず、テーブルが大きい場合は、ヒープを使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="4e5ab-124">Do not use a heap when there are no nonclustered indexes and the table is large.</span></span> <span data-ttu-id="4e5ab-125">ヒープでは、特定の行を探すためにヒープのすべての行を読み取る必要があります。</span><span class="sxs-lookup"><span data-stu-id="4e5ab-125">In a heap, all rows of the heap must be read to find any row.</span></span>  
  
## <a name="managing-heaps"></a><span data-ttu-id="4e5ab-126">ヒープの管理</span><span class="sxs-lookup"><span data-stu-id="4e5ab-126">Managing Heaps</span></span>  
 <span data-ttu-id="4e5ab-127">ヒープを作成するには、クラスター化インデックスのないテーブルを作成します。</span><span class="sxs-lookup"><span data-stu-id="4e5ab-127">To create a heap, create a table without a clustered index.</span></span> <span data-ttu-id="4e5ab-128">既にテーブルにクラスター化インデックスが含まれている場合は、クラスター化インデックスを削除して、テーブルをヒープに戻します。</span><span class="sxs-lookup"><span data-stu-id="4e5ab-128">If a table already has a clustered index, drop the clustered index to return the table to a heap.</span></span>  
  
 <span data-ttu-id="4e5ab-129">ヒープを削除するには、ヒープにクラスター化インデックスを作成します。</span><span class="sxs-lookup"><span data-stu-id="4e5ab-129">To remove a heap, create a clustered index on the heap.</span></span>  
  
 <span data-ttu-id="4e5ab-130">使用されていない領域を再利用できるようにヒープを再構築するには、ヒープにクラスター化インデックスを作成してから、そのクラスター化インデックスを削除します。</span><span class="sxs-lookup"><span data-stu-id="4e5ab-130">To rebuild a heap to reclaim wasted space, create a clustered index on the heap, and then drop that clustered index.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="4e5ab-131">クラスター化インデックスを作成または削除するには、テーブル全体を再作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4e5ab-131">Creating or dropping clustered indexes requires rewriting the entire table.</span></span> <span data-ttu-id="4e5ab-132">テーブルに非クラスター化インデックスがある場合は、クラスター化インデックスが変更されるたびに、すべての非クラスター化インデックスを再作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4e5ab-132">If the table has nonclustered indexes, all the nonclustered indexes must all be recreated whenever the clustered index is changed.</span></span> <span data-ttu-id="4e5ab-133">このため、ヒープからクラスター化インデックス構造への変更、またはその逆の変更には時間がかかり、tempdb でデータの順序を並べ替えるためのディスク領域が必要になります。</span><span class="sxs-lookup"><span data-stu-id="4e5ab-133">Therefore, changing from a heap to a clustered index structure or back can take a lot of time and require disk space for reordering data in tempdb.</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="4e5ab-134">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="4e5ab-134">Related Content</span></span>  
 [<span data-ttu-id="4e5ab-135">CREATE INDEX &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="4e5ab-135">CREATE INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-index-transact-sql)  
  
 [<span data-ttu-id="4e5ab-136">DROP INDEX &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="4e5ab-136">DROP INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-index-transact-sql)  
  
 [<span data-ttu-id="4e5ab-137">クラスター化インデックスと非クラスター化インデックスの概念</span><span class="sxs-lookup"><span data-stu-id="4e5ab-137">Clustered and Nonclustered Indexes Described</span></span>](clustered-and-nonclustered-indexes-described.md)  
  
  
