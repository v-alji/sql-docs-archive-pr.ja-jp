---
title: RANK を使用して検索結果を制限する方法 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- row ranking [full-text search]
- relevance ranking values [full-text search]
- full-text search [SQL Server], rankings
- index rankings [full-text search]
- ranked results [full-text search]
- rankings [full-text search]
- per-row rank values [full-text search]
ms.assetid: 06a776e6-296c-4ec7-9fa5-0794709ccb17
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ab1b930b3238cb541965e1984d1561f1a1c22d87
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87717702"
---
# <a name="limit-search-results-with-rank"></a><span data-ttu-id="d80d7-102">RANK を使用して検索結果を制限する方法</span><span class="sxs-lookup"><span data-stu-id="d80d7-102">Limit Search Results with RANK</span></span>
  <span data-ttu-id="d80d7-103">[CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) 関数と [FREETEXTTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql) 関数は、0 ～ 1000 の序数値 (順位値) を含む "RANK" 列を返します。</span><span class="sxs-lookup"><span data-stu-id="d80d7-103">The [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) and [FREETEXTTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql) functions return a column named RANK that contains ordinal values from 0 through 1000 (rank values).</span></span> <span data-ttu-id="d80d7-104">これらの値を使用すれば、選択基準への適合度合いに応じて、返された行に順位を付けることができます。</span><span class="sxs-lookup"><span data-stu-id="d80d7-104">These values are used to rank the rows returned according to how well they match the selection criteria.</span></span> <span data-ttu-id="d80d7-105">この順位値が示しているのは、結果セット内の各行の単なる相対順位であり、値が小さいほど関連性は低くなります。</span><span class="sxs-lookup"><span data-stu-id="d80d7-105">The rank values indicate only a relative order of relevance of the rows in the result set, with a lower value indicating lower relevance.</span></span> <span data-ttu-id="d80d7-106">実際の値は重要ではなく、通常はクエリが実行されるたびに変わります。</span><span class="sxs-lookup"><span data-stu-id="d80d7-106">The actual values are unimportant and typically differ each time the query is run.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d80d7-107">CONTAINS 述語と FREETEXT 述語は順位値を返しません。</span><span class="sxs-lookup"><span data-stu-id="d80d7-107">The CONTAINS and FREETEXT predicates do not return any rank values.</span></span>  
  
 <span data-ttu-id="d80d7-108">検索条件と一致するアイテムの数が膨大になることがよくあります。</span><span class="sxs-lookup"><span data-stu-id="d80d7-108">The number of items matching a search condition is often very large.</span></span> <span data-ttu-id="d80d7-109">CONTAINSTABLE クエリまたは FREETEXTTABLE クエリから多数の一致結果が返されないようにするには、オプションの *top_n_by_rank* パラメーターを使用して、返される行を制限します。</span><span class="sxs-lookup"><span data-stu-id="d80d7-109">To prevent CONTAINSTABLE or FREETEXTTABLE queries from returning too many matches, use the optional *top_n_by_rank* parameter, which returns only a subset of rows.</span></span> <span data-ttu-id="d80d7-110">*top_n_by_rank* は整数値です。 *n*は、降順で上位 *n* 個の一致結果のみを返すことを示します。</span><span class="sxs-lookup"><span data-stu-id="d80d7-110">*top_n_by_rank* is an integer value, *n*, that specifies that only the *n* highest ranked matches are to be returned, in descending order.</span></span> <span data-ttu-id="d80d7-111">*top_n_by_rank* を他のパラメーターと組み合わせた場合、クエリから返される行数は、実際にすべての述語に一致する行数より少なくなります。</span><span class="sxs-lookup"><span data-stu-id="d80d7-111">If *top_n_by_rank* is combined with other parameters, the query could return fewer rows than the number of rows that actually match all the predicates.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="d80d7-112">は、一致結果を順位で並べ替え、指定された数の行のみを返します。</span><span class="sxs-lookup"><span data-stu-id="d80d7-112">orders the matches by rank and returns only up to the specified number of rows.</span></span> <span data-ttu-id="d80d7-113">このオプションを使用すると、パフォーマンスが大幅に向上します。</span><span class="sxs-lookup"><span data-stu-id="d80d7-113">This choice can result in a dramatic increase in performance.</span></span> <span data-ttu-id="d80d7-114">たとえば、通常ならば 100 万行のテーブルから 10 万行を返すクエリに対して、上位 100 行だけを返すように要求すれば、そのクエリの処理が速くなります。</span><span class="sxs-lookup"><span data-stu-id="d80d7-114">For example, a query that would normally return 100,000 rows from a table of one million rows are processed more quickly if only the top 100 rows are requested.</span></span>  
  
##  <a name="examples-of-using-rank-to-limit-search-results"></a><a name="examples"></a> <span data-ttu-id="d80d7-115">RANK を使用して検索結果を制限する例</span><span class="sxs-lookup"><span data-stu-id="d80d7-115">Examples of Using RANK to Limit Search Results</span></span>  
  
### <a name="example-a-searching-for-only-the-top-three-matches"></a><span data-ttu-id="d80d7-116">例 A: 上位 3 件の一致結果のみを検索する</span><span class="sxs-lookup"><span data-stu-id="d80d7-116">Example A: Searching for only the top three matches</span></span>  
 <span data-ttu-id="d80d7-117">次の例では、CONTAINSTABLE を使用して上位 3 件の一致結果のみを返します。</span><span class="sxs-lookup"><span data-stu-id="d80d7-117">The following example uses CONTAINSTABLE to return only the top three matches.</span></span>  
  
```  
USE AdventureWorks2012  
GO  
  
SELECT K.RANK, AddressLine1, City  
FROM Person.Address AS A  
  INNER JOIN  
  CONTAINSTABLE(Person.Address, AddressLine1, 'ISABOUT ("des*",  
    Rue WEIGHT(0.5),  
    Bouchers WEIGHT(0.9))',  
    3) AS K  
  ON A.AddressID = K.[KEY]  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
RANK        Address                          City  
----------- -------------------------------- ------------------------------  
172         9005, rue des Bouchers           Paris  
172         5, rue des Bouchers              Orleans  
172         5, rue des Bouchers              Metz  
  
(3 row(s) affected)  
```  
  
  
### <a name="example-b-searching-for-the-top-ten-matches"></a><span data-ttu-id="d80d7-118">例 B: 上位 10 件の一致結果を検索する</span><span class="sxs-lookup"><span data-stu-id="d80d7-118">Example B: Searching for the top ten matches</span></span>  
 <span data-ttu-id="d80d7-119">次の例では、CONTAINSTABLE を使用して、 `Description` 列内で "light" または "lightweight" という単語の近くに "aluminum" という語句を含んでいる、上位 5 種の製品の説明を返します。</span><span class="sxs-lookup"><span data-stu-id="d80d7-119">The following example uses CONTAINSTABLE to return the description of the top 5 products where the `Description` column contains the word "aluminum" near either the word "light" or the word "lightweight".</span></span>  
  
```  
USE AdventureWorks2012  
GO  
  
SELECT FT_TBL.ProductDescriptionID,  
   FT_TBL.Description,   
   KEY_TBL.RANK  
FROM Production.ProductDescription AS FT_TBL INNER JOIN  
   CONTAINSTABLE (Production.ProductDescription,  
      Description,   
      '(light NEAR aluminum) OR  
      (lightweight NEAR aluminum)',  
      5  
   ) AS KEY_TBL  
   ON FT_TBL.ProductDescriptionID = KEY_TBL.[KEY]  
GO  
```  
  
  
##  <a name="how-search-query-results-are-ranked"></a><a name="how"></a> <span data-ttu-id="d80d7-120">検索クエリの結果が順位付けされる方法</span><span class="sxs-lookup"><span data-stu-id="d80d7-120">How Search Query Results Are Ranked</span></span>  
 <span data-ttu-id="d80d7-121">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のフルテキスト検索では、フルテキスト クエリが返すデータの関連性を示す省略可能なスコア (順位値) を生成できます。</span><span class="sxs-lookup"><span data-stu-id="d80d7-121">Full-text search in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] can generate an optional score (or rank value) that indicates the relevance of the data returned by a full-text query.</span></span> <span data-ttu-id="d80d7-122">この順位値は 1 行ごとに計算され、クエリの結果セットを関連性に従って並べ替える順序付け基準として使用できます。</span><span class="sxs-lookup"><span data-stu-id="d80d7-122">This rank value is calculated on every row and can be used as an ordering criteria to sort the result set of a given query by relevance.</span></span> <span data-ttu-id="d80d7-123">順位値は、単に、結果セット内の各行の相対的な関連順位を示します。</span><span class="sxs-lookup"><span data-stu-id="d80d7-123">The rank values indicate only a relative order of relevance of the rows in the result set.</span></span> <span data-ttu-id="d80d7-124">実際の値は重要ではなく、通常はクエリが実行されるたびに変わります。</span><span class="sxs-lookup"><span data-stu-id="d80d7-124">The actual values are unimportant and typically differ each time the query is run.</span></span> <span data-ttu-id="d80d7-125">順位値は、他のクエリでは意味を持ちません。</span><span class="sxs-lookup"><span data-stu-id="d80d7-125">The rank value does not hold any significance across queries.</span></span>  
  
### <a name="statistics-for-ranking"></a><span data-ttu-id="d80d7-126">順位付けの統計</span><span class="sxs-lookup"><span data-stu-id="d80d7-126">Statistics for Ranking</span></span>  
 <span data-ttu-id="d80d7-127">順位付けに使用する統計はインデックス作成時に収集されます。</span><span class="sxs-lookup"><span data-stu-id="d80d7-127">When an index is built, statistics are collected for use in ranking.</span></span> <span data-ttu-id="d80d7-128">フルテキスト カタログの作成処理で、単一のインデックス構造が直接作成されるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="d80d7-128">The process of building a full-text catalog does not directly result in a single index structure.</span></span> <span data-ttu-id="d80d7-129">代わりに、データにインデックスが作成されたとき、Full-Text Engine for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] によって中間インデックスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="d80d7-129">Instead, the Full-Text Engine for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] creates intermediate indexes as data is indexed.</span></span> <span data-ttu-id="d80d7-130">その後、Full-Text Engine は必要に応じてこれらのインデックスをより大きなインデックスにマージします。</span><span class="sxs-lookup"><span data-stu-id="d80d7-130">The Full-Text Engine then merges these indexes into a larger index as needed.</span></span> <span data-ttu-id="d80d7-131">この処理は何度も繰り返される場合があります。</span><span class="sxs-lookup"><span data-stu-id="d80d7-131">This process can be repeated many times.</span></span> <span data-ttu-id="d80d7-132">次に、Full-Text Engine は "マスター マージ" と呼ばれる処理を行います。この処理では、すべての中間インデックスが 1 つの巨大なインデックスに結合されます。</span><span class="sxs-lookup"><span data-stu-id="d80d7-132">The Full-Text Engine then conducts a "master merge" that combines all of the intermediate indexes into one large master index.</span></span>  
  
 <span data-ttu-id="d80d7-133">統計は各中間インデックス レベルで収集されます。</span><span class="sxs-lookup"><span data-stu-id="d80d7-133">Statistics are collected at each intermediate index level.</span></span> <span data-ttu-id="d80d7-134">インデックスがマージされると、統計もマージされます。</span><span class="sxs-lookup"><span data-stu-id="d80d7-134">The statistics are merged when the indexes are merged.</span></span> <span data-ttu-id="d80d7-135">マスターのマージ処理中にのみ生成される統計もあります。</span><span class="sxs-lookup"><span data-stu-id="d80d7-135">Some statistical values can only be generated during the master merging process.</span></span>  
  
 <span data-ttu-id="d80d7-136">クエリの結果セットの順位付けを行う際に、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] では最も大きい中間インデックスの統計が使用されます。</span><span class="sxs-lookup"><span data-stu-id="d80d7-136">While ranking a query result set, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] uses statistics from the largest intermediate index.</span></span> <span data-ttu-id="d80d7-137">これは、中間インデックスがマージされているかどうかで決まります。</span><span class="sxs-lookup"><span data-stu-id="d80d7-137">This depends on whether intermediate indexes have been merged or not.</span></span> <span data-ttu-id="d80d7-138">したがって、中間インデックスがマージされていない場合、順位付けの統計の精度にばらつきが生じることがあります。</span><span class="sxs-lookup"><span data-stu-id="d80d7-138">As a result, ranking statistics can vary in accuracy if the intermediate indexes have not been merged.</span></span> <span data-ttu-id="d80d7-139">時間が経つにつれて同じクエリが異なる順位結果を返すことがあるのは、フルテキスト インデックス データの追加、変更、および削除が行われ、小さなインデックスがマージされていくためです。</span><span class="sxs-lookup"><span data-stu-id="d80d7-139">This explains why the same query can return different rank results over time as full-text indexed data is added, modified, and deleted, and as the smaller indexes are merged.</span></span>  
  
 <span data-ttu-id="d80d7-140">インデックスのサイズを最小化し、計算を容易にするために、統計はしばしば丸められます。</span><span class="sxs-lookup"><span data-stu-id="d80d7-140">To minimize the size of the index and computational complexity, statistics are often rounded.</span></span>  
  
 <span data-ttu-id="d80d7-141">共通に使用される用語と順位の計算に必要な統計値を以下の表に示します。</span><span class="sxs-lookup"><span data-stu-id="d80d7-141">The list below includes some commonly used terms and statistical values that are important in calculating rank.</span></span>  
  
 <span data-ttu-id="d80d7-142">プロパティ</span><span class="sxs-lookup"><span data-stu-id="d80d7-142">Property</span></span>  
 <span data-ttu-id="d80d7-143">行の中でフルテキスト インデックスが付けられた列です。</span><span class="sxs-lookup"><span data-stu-id="d80d7-143">A full-text indexed column of the row.</span></span>  
  
 <span data-ttu-id="d80d7-144">ドキュメント</span><span class="sxs-lookup"><span data-stu-id="d80d7-144">Document</span></span>  
 <span data-ttu-id="d80d7-145">クエリで返されるエンティティです。</span><span class="sxs-lookup"><span data-stu-id="d80d7-145">The entity that is returned in queries.</span></span> <span data-ttu-id="d80d7-146">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] では行に相当します。</span><span class="sxs-lookup"><span data-stu-id="d80d7-146">In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] this corresponds to a row.</span></span> <span data-ttu-id="d80d7-147">1 つの行にフルテキスト インデックスが付いた列が複数含まれるのと同様に、1 つのドキュメントには複数のプロパティが含まれる場合があります。</span><span class="sxs-lookup"><span data-stu-id="d80d7-147">A document can have multiple properties, just as a row can have multiple full-text indexed columns.</span></span>  
  
 <span data-ttu-id="d80d7-148">インデックス</span><span class="sxs-lookup"><span data-stu-id="d80d7-148">Index</span></span>  
 <span data-ttu-id="d80d7-149">1 つまたは複数のドキュメントの単一の逆インデックスです。</span><span class="sxs-lookup"><span data-stu-id="d80d7-149">A single inverted index of one or more documents.</span></span> <span data-ttu-id="d80d7-150">インデックスはすべてメモリまたはディスクに格納されています。</span><span class="sxs-lookup"><span data-stu-id="d80d7-150">This may be entirely in memory or on disk.</span></span> <span data-ttu-id="d80d7-151">クエリ統計の多くは、一致した個々のインデックスと関連しています。</span><span class="sxs-lookup"><span data-stu-id="d80d7-151">Many query statistics are relative to the individual index where the match occurred.</span></span>  
  
 <span data-ttu-id="d80d7-152">フルテキスト カタログ</span><span class="sxs-lookup"><span data-stu-id="d80d7-152">Full-Text Catalog</span></span>  
 <span data-ttu-id="d80d7-153">クエリで 1 つのエンティティとして扱われる中間インデックスのコレクションです。</span><span class="sxs-lookup"><span data-stu-id="d80d7-153">A collection of intermediate indexes treated as one entity for queries.</span></span> <span data-ttu-id="d80d7-154">カタログは、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 管理者に対して表示される組織の単位です。</span><span class="sxs-lookup"><span data-stu-id="d80d7-154">Catalogs are the unit of organization visible to the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] administrator.</span></span>  
  
 <span data-ttu-id="d80d7-155">語、トークン、またはアイテム</span><span class="sxs-lookup"><span data-stu-id="d80d7-155">Word, token or item</span></span>  
 <span data-ttu-id="d80d7-156">フルテキスト エンジンの一致単位です。</span><span class="sxs-lookup"><span data-stu-id="d80d7-156">The unit of matching in the full-text engine.</span></span> <span data-ttu-id="d80d7-157">ドキュメントからのテキスト ストリームは、言語固有のワード ブレーカーによって語またはトークンにトークン化されます。</span><span class="sxs-lookup"><span data-stu-id="d80d7-157">Streams of text from documents are tokenized into words, or tokens by language-specific word breakers.</span></span>  
  
 <span data-ttu-id="d80d7-158">個数</span><span class="sxs-lookup"><span data-stu-id="d80d7-158">Occurrence</span></span>  
 <span data-ttu-id="d80d7-159">ワード ブレーカーによって決定されるドキュメント プロパティのワード オフセットです。</span><span class="sxs-lookup"><span data-stu-id="d80d7-159">The word offset in a document property as determined by the word breaker.</span></span> <span data-ttu-id="d80d7-160">最初のワードはオカレンス 1、次のワードはオカレンス 2 というように、それ以降順番に番号が付けられます。</span><span class="sxs-lookup"><span data-stu-id="d80d7-160">The first word is at occurrence 1, the next at 2, and so on.</span></span> <span data-ttu-id="d80d7-161">語句クエリおよび近接クエリで誤った判断を行わないように、文と段落の末尾にはより大きな間隔値のオカレンスが使用されます。</span><span class="sxs-lookup"><span data-stu-id="d80d7-161">In order to avoid false positives in phrase and proximity queries, end-of-sentence and end-of-paragraph introduce larger occurrence gaps.</span></span>  
  
 <span data-ttu-id="d80d7-162">TermFrequency</span><span class="sxs-lookup"><span data-stu-id="d80d7-162">TermFrequency</span></span>  
 <span data-ttu-id="d80d7-163">行におけるキー値の出現回数です。</span><span class="sxs-lookup"><span data-stu-id="d80d7-163">The number times the key value occurs in a row.</span></span>  
  
 <span data-ttu-id="d80d7-164">IndexedRowCount</span><span class="sxs-lookup"><span data-stu-id="d80d7-164">IndexedRowCount</span></span>  
 <span data-ttu-id="d80d7-165">インデックスが付けられた合計行数です。</span><span class="sxs-lookup"><span data-stu-id="d80d7-165">Total number of rows indexed.</span></span> <span data-ttu-id="d80d7-166">この値は、中間インデックスに保持されている数を基にして計算されます。</span><span class="sxs-lookup"><span data-stu-id="d80d7-166">This is computed, based on counts maintained in the intermediate indexes.</span></span> <span data-ttu-id="d80d7-167">この数の精度にはばらつきがあります。</span><span class="sxs-lookup"><span data-stu-id="d80d7-167">This number can vary in accuracy.</span></span>  
  
 <span data-ttu-id="d80d7-168">KeyRowCount</span><span class="sxs-lookup"><span data-stu-id="d80d7-168">KeyRowCount</span></span>  
 <span data-ttu-id="d80d7-169">指定されたキーを格納するフルテキスト カタログの合計行数です。</span><span class="sxs-lookup"><span data-stu-id="d80d7-169">Total number of rows in the full-text catalog that contain a given key.</span></span>  
  
 <span data-ttu-id="d80d7-170">MaxOccurrence</span><span class="sxs-lookup"><span data-stu-id="d80d7-170">MaxOccurrence</span></span>  
 <span data-ttu-id="d80d7-171">行内の指定したプロパティでフルテキスト カタログに保存された最大オカレンスです。</span><span class="sxs-lookup"><span data-stu-id="d80d7-171">The largest occurrence stored in a full-text catalog for a given property in a row.</span></span>  
  
 <span data-ttu-id="d80d7-172">MaxQueryRank</span><span class="sxs-lookup"><span data-stu-id="d80d7-172">MaxQueryRank</span></span>  
 <span data-ttu-id="d80d7-173">Full-Text Engine が返す最大順位 (1,000) です。</span><span class="sxs-lookup"><span data-stu-id="d80d7-173">The maximum rank, 1000, returned by the Full-Text Engine.</span></span>  
  
  
### <a name="rank-computation-issues"></a><span data-ttu-id="d80d7-174">順位計算に関する問題点</span><span class="sxs-lookup"><span data-stu-id="d80d7-174">Rank Computation Issues</span></span>  
 <span data-ttu-id="d80d7-175">順位の計算処理はさまざまな要因に依存します。</span><span class="sxs-lookup"><span data-stu-id="d80d7-175">The process of computing rank, depends on a number of factors.</span></span>  <span data-ttu-id="d80d7-176">ワード ブレーカーの言語が異なると、テキストをトークン化する方法も異なります。</span><span class="sxs-lookup"><span data-stu-id="d80d7-176">Different language word breakers tokenize text differently.</span></span> <span data-ttu-id="d80d7-177">たとえば、あるワード ブレーカーは "dog-house" という文字列を "dog" "house" に分割しますが、別のワード ブレーカーは "dog-house" に分割します。</span><span class="sxs-lookup"><span data-stu-id="d80d7-177">For example, the string "dog-house" could be broken into "dog" "house" by one word breaker and into "dog-house" by another.</span></span> <span data-ttu-id="d80d7-178">これは、指定された言語によって一致および順位が異なるということを意味します。単語だけでなく、ドキュメント長も異なるからです。</span><span class="sxs-lookup"><span data-stu-id="d80d7-178">This means that matching and ranking will vary based on the language specified, because not only are the words different, but so is the document length.</span></span> <span data-ttu-id="d80d7-179">ドキュメント長の違いは、クエリすべての順位付けに影響します。</span><span class="sxs-lookup"><span data-stu-id="d80d7-179">The document length difference can affect ranking for all queries.</span></span>  
  
 <span data-ttu-id="d80d7-180">`IndexRowCount` などの統計は大きく異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="d80d7-180">Statistics such as `IndexRowCount` can vary widely.</span></span> <span data-ttu-id="d80d7-181">たとえば、カタログのマスター インデックスに 20 億の行が格納されている場合、1 つの新規ドキュメントにメモリ内で中間インデックスが作成され、そのメモリ内インデックスのドキュメント数に基づいてドキュメントが順位付けされると、マスター インデックスのドキュメントの順位と整合性のない結果になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d80d7-181">For example, if a catalog has 2 billion rows in the master index, then one new document is indexed into an in-memory intermediate index, and ranks for that document based on the number of documents in the in-memory index could be skewed compared with ranks for documents from the master index.</span></span> <span data-ttu-id="d80d7-182">こうした理由から、任意の作成処理により大量の行がインデックス化または再インデックス化された場合は、ALTER FULLTEXT CATALOG ... REORGANIZE [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを使用してこれらのインデックスをマスター インデックスにマージすることを推奨します。</span><span class="sxs-lookup"><span data-stu-id="d80d7-182">For this reason, it is recommended that after any population that results in large number of rows being indexed or re-indexed the indexes be merged into a master index using the ALTER FULLTEXT CATALOG ... REORGANIZE [!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span> <span data-ttu-id="d80d7-183">また、中間インデックスの数やサイズなどのパラメーターを基に、Full-Text Engine によるインデックスのマージも自動的に実行されます。</span><span class="sxs-lookup"><span data-stu-id="d80d7-183">The Full-Text Engine will also automatically merge the indexes based on parameters such as the number and size of intermediate indexes.</span></span>  
  
 <span data-ttu-id="d80d7-184">`MaxOccurrence` の値は 1 ～ 32 の範囲のいずれかに正規化されます。</span><span class="sxs-lookup"><span data-stu-id="d80d7-184">`MaxOccurrence` values are normalized into 1 of 32 ranges.</span></span> <span data-ttu-id="d80d7-185">これは、たとえば 50 語のドキュメントが 100 語のドキュメントと同様に扱われるということを意味します。</span><span class="sxs-lookup"><span data-stu-id="d80d7-185">This means, for example, that a document 50 words long is treated the same as a document 100 words long.</span></span> <span data-ttu-id="d80d7-186">正規化に使用される表を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="d80d7-186">Below is the table used for normalization.</span></span> <span data-ttu-id="d80d7-187">ドキュメントの長さは、隣接するテーブル値32と128の間の範囲内にあるため、実際には同じ長さの 128 (32 < <= 128) として扱われ `docLength` ます。</span><span class="sxs-lookup"><span data-stu-id="d80d7-187">Because the document lengths are in the range between adjacent table values 32 and 128, they are effectively treated as having the same length, 128 (32 < `docLength` <= 128).</span></span>  
  
```  
{ 16, 32, 128, 256, 512, 725, 1024, 1450, 2048, 2896, 4096, 5792, 8192, 11585,   
16384, 23170, 28000, 32768, 39554, 46340, 55938, 65536, 92681, 131072, 185363,   
262144, 370727, 524288, 741455, 1048576, 2097152, 4194304 };  
  
```  
  
  
### <a name="ranking-of-containstable"></a><span data-ttu-id="d80d7-188">CONTAINSTABLE の順位付け</span><span class="sxs-lookup"><span data-stu-id="d80d7-188">Ranking of CONTAINSTABLE</span></span>  
 <span data-ttu-id="d80d7-189">[CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) の順位付けでは次のアルゴリズムを使用します。</span><span class="sxs-lookup"><span data-stu-id="d80d7-189">[CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) ranking uses the following algorithm:</span></span>  
  
```  
StatisticalWeight = Log2( ( 2 + IndexedRowCount ) / KeyRowCount )  
Rank = min( MaxQueryRank, HitCount * 16 * StatisticalWeight / MaxOccurrence )  
```  
  
 <span data-ttu-id="d80d7-190">句の一致は個々のキーと同様に順位付けされます。ただし、`KeyRowCount` (句を含む行数) には予測値が使用され、不正確で実際の値よりも大きくなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d80d7-190">Phrase matches are ranked just like individual keys except that `KeyRowCount` (the number of rows containing the phrase) is estimated and can be inaccurate and higher than the actual number.</span></span>  
  
 <span data-ttu-id="d80d7-191">**NEAR の順位付け**</span><span class="sxs-lookup"><span data-stu-id="d80d7-191">**Ranking of NEAR**</span></span>  
  
 <span data-ttu-id="d80d7-192">CONTAINSTABLE では、NEAR オプションを使用することで、相互に近接する 2 つ以上の検索語句に対するクエリをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="d80d7-192">CONTAINSTABLE supports querying for two or more search terms in proximity to each other by using the NEAR option.</span></span> <span data-ttu-id="d80d7-193">返される各行の順位値は、いくつかのパラメーターに基づいています。</span><span class="sxs-lookup"><span data-stu-id="d80d7-193">The rank value of each returned row is based on several parameters.</span></span> <span data-ttu-id="d80d7-194">順位付けの主な要因の 1 つは、ドキュメントの長さに関連した一致の合計数 ( *ヒット*) です。</span><span class="sxs-lookup"><span data-stu-id="d80d7-194">One major ranking factor is the total number of matches (or *hits*) relative to the length of the document.</span></span> <span data-ttu-id="d80d7-195">したがって、たとえば、100 語のドキュメントと 900 語のドキュメントに同一の一致が含まれている場合は、100 語のドキュメントの方が順位が高くなります。</span><span class="sxs-lookup"><span data-stu-id="d80d7-195">Thus, for example, if a 100-word document and a 900-word document contain identical matches, the 100-word document is ranked higher.</span></span>  
  
 <span data-ttu-id="d80d7-196">行における各ヒットの合計の長さも、そのヒットの最初と最後の検索語句の間の距離に基づいてその行の順位に影響を与えます。</span><span class="sxs-lookup"><span data-stu-id="d80d7-196">The total length of each hit in a row will also contribute to the ranking of that row based on the distance between the first and last search terms of that hit.</span></span> <span data-ttu-id="d80d7-197">距離が小さいほど、ヒットは行の順位値に大きく影響します</span><span class="sxs-lookup"><span data-stu-id="d80d7-197">The smaller the distance, the more the hit contributes to the rank value of the row.</span></span> <span data-ttu-id="d80d7-198">フルテキスト クエリで最大距離の整数が指定されていない場合、論理語の間隔が 100 を超えるヒットのみが含まれるドキュメントは、その順位が 0 になります。</span><span class="sxs-lookup"><span data-stu-id="d80d7-198">If a full-text query does not specify an integer as the maximum distance, a document that contains only hits whose distances are greater than 100 logical terms apart, will have a ranking of 0.</span></span>  
  
 <span data-ttu-id="d80d7-199">**ISABOUT の順位付け**</span><span class="sxs-lookup"><span data-stu-id="d80d7-199">**Ranking of ISABOUT**</span></span>  
  
 <span data-ttu-id="d80d7-200">CONTAINSTABLE は、ISABOUT オプションを指定した重み付け語句のクエリをサポートします。</span><span class="sxs-lookup"><span data-stu-id="d80d7-200">CONTAINSTABLE supports querying for weighted terms by using the ISABOUT option.</span></span> <span data-ttu-id="d80d7-201">ISABOUT は、従来の情報検索用語で言うところのベクトル空間クエリです。</span><span class="sxs-lookup"><span data-stu-id="d80d7-201">ISABOUT is a vector-space query in traditional information retrieval terminology.</span></span> <span data-ttu-id="d80d7-202">既定の順位付けアルゴリズムには、Jaccard という一般的に知られている公式が使用されます。</span><span class="sxs-lookup"><span data-stu-id="d80d7-202">The default ranking algorithm used is Jaccard, a widely known formula.</span></span> <span data-ttu-id="d80d7-203">クエリ内の用語ごとに順位付けが計算され、以下に示す方法で各順位付けが結合されます。</span><span class="sxs-lookup"><span data-stu-id="d80d7-203">The ranking is computed for each term in the query and then combined as described below.</span></span>  
  
```  
ContainsRank = same formula used for CONTAINSTABLE ranking of a single term (above).  
Weight = the weight specified in the query for each term. Default weight is 1.  
WeightedSum = ??[key=1 to n] ContainsRankKey * WeightKey  
Rank =  ( MaxQueryRank * WeightedSum ) / ( ( ??[key=1 to n] ContainsRankKey^2 )   
      + ( ??[key=1 to n] WeightKey^2 ) - ( WeightedSum ) )  
  
```  
  
  
### <a name="ranking-of-freetexttable"></a><span data-ttu-id="d80d7-204">FREETEXTTABLE の順位付け</span><span class="sxs-lookup"><span data-stu-id="d80d7-204">Ranking of FREETEXTTABLE</span></span>  
 <span data-ttu-id="d80d7-205">[FREETEXTTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql) の順位付けは、OKAPI BM25 という公式を使用して計算されます。</span><span class="sxs-lookup"><span data-stu-id="d80d7-205">[FREETEXTTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql) ranking is based on the OKAPI BM25 ranking formula.</span></span> <span data-ttu-id="d80d7-206">FREETEXTTABLE クエリは屈折生成 (クエリに含まれる元の単語の変化形生成) を行って単語をクエリに追加します。これらの単語は別々の単語として扱われ、生成元の単語とは特に関連を持ちません。</span><span class="sxs-lookup"><span data-stu-id="d80d7-206">FREETEXTTABLE queries will add words to the query via inflectional generation (inflected forms of the original query words); these words are treated as separate words with no special relationship to the words from which they were generated.</span></span> <span data-ttu-id="d80d7-207">シソーラス機能によって生成されたシノニムは、同等に重み付けされた別々の用語として扱われます。</span><span class="sxs-lookup"><span data-stu-id="d80d7-207">Synonyms generated from the Thesaurus feature are treated as separate, equally weighted terms.</span></span> <span data-ttu-id="d80d7-208">クエリ内の各単語が順位の要素となります。</span><span class="sxs-lookup"><span data-stu-id="d80d7-208">Each word in the query contributes to the rank.</span></span>  
  
```  
Rank = ??[Terms in Query] w ( ( ( k1 + 1 ) tf ) / ( K + tf ) ) * ( ( k3 + 1 ) qtf / ( k3 + qtf ) ) )  
Where:   
w is the Robertson-Sparck Jones weight.   
In simplified form, w is defined as:   
w = log10 ( ( ( r + 0.5 ) * ( N - R + r + 0.5 ) ) / ( ( R - r + 0.5 ) * ( n - r + 0.5 ) )  
N is the number of indexed rows for the property being queried.   
n is the number of rows containing the word.   
K is ( k1 * ( ( 1 - b ) + ( b * dl / avdl ) ) ).   
dl is the property length, in word occurrences.   
avdl is the average length of the property being queried, in word occurrences.   
k1, b, and k3 are the constants 1.2, 0.75, and 8.0, respectively.   
tf is the frequency of the word in the queried property in a specific row.   
qtf is the frequency of the term in the query.   
```  
  
  
## <a name="see-also"></a><span data-ttu-id="d80d7-209">参照</span><span class="sxs-lookup"><span data-stu-id="d80d7-209">See Also</span></span>  
 [<span data-ttu-id="d80d7-210">フルテキスト検索でのクエリ</span><span class="sxs-lookup"><span data-stu-id="d80d7-210">Query with Full-Text Search</span></span>](query-with-full-text-search.md)  
  
  
