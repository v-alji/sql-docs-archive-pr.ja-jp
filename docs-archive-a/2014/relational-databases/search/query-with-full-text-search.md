---
title: フルテキスト検索でのクエリ | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- queries [full-text search], about full-text queries
- queries [full-text search], predicates
- full-text queries [SQL Server], about full-text queries
- full-text search [SQL Server], querying SQL Server
- full-text queries [SQL Server]
- queries [full-text search], functions
ms.assetid: 7624ba76-594b-4be5-ac10-c3ac4a3529bd
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d78707925303d5e19d93b170f257d76fb7d1747d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716202"
---
# <a name="query-with-full-text-search"></a><span data-ttu-id="2d127-102">フルテキスト検索でのクエリ</span><span class="sxs-lookup"><span data-stu-id="2d127-102">Query with Full-Text Search</span></span>
  <span data-ttu-id="2d127-103">フルテキスト検索を定義するため、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のフルテキスト クエリでは、フルテキスト述語 (CONTAINS と FREETEXT) およびフルテキスト関数 (CONTAINSTABLE と FREETEXTTABLE) が使用されます。</span><span class="sxs-lookup"><span data-stu-id="2d127-103">To define full-text searches, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] full-text queries use the full-text predicates (CONTAINS and FREETEXT) and functions (CONTAINSTABLE and FREETEXTTABLE.</span></span> <span data-ttu-id="2d127-104">この述語と関数は、さまざまな形式のクエリ用語に対応する豊富な [!INCLUDE[tsql](../../includes/tsql-md.md)] 構文をサポートします。</span><span class="sxs-lookup"><span data-stu-id="2d127-104">These support rich [!INCLUDE[tsql](../../includes/tsql-md.md)] syntax that supports a variety of forms of query terms.</span></span> <span data-ttu-id="2d127-105">フルテキスト クエリを記述するには、これらの述語と関数をいつどのように使用するかを理解する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2d127-105">To write full-text queries, you must learn when and how to use these predicates and functions.</span></span>  
  
##  <a name="overview-of-the-full-text-predicates-contains-and-freetext"></a><a name="OV_ft_predicates"></a><span data-ttu-id="2d127-106">フルテキスト述語 (CONTAINS と FREETEXT) の概要</span><span class="sxs-lookup"><span data-stu-id="2d127-106">Overview of the Full-Text Predicates (CONTAINS and FREETEXT)</span></span>  
 <span data-ttu-id="2d127-107">CONTAINS 述語と FREETEXT 述語は、TRUE 値または FALSE 値を返します。</span><span class="sxs-lookup"><span data-stu-id="2d127-107">The CONTAINS and FREETEXT predicates return a TRUE or FALSE value.</span></span> <span data-ttu-id="2d127-108">これらの述語は、特定の行がフルテキスト クエリと一致するかどうかを判断する選択基準としてのみ使用します。</span><span class="sxs-lookup"><span data-stu-id="2d127-108">They can be used only to specify selection criteria for determining whether a given row matches the full-text query.</span></span> <span data-ttu-id="2d127-109">一致する行は結果セットで返されます。</span><span class="sxs-lookup"><span data-stu-id="2d127-109">Matching rows are returned in the result set.</span></span> <span data-ttu-id="2d127-110">CONTAINS と FREETEXT は、SELECT ステートメントの WHERE 句または HAVING 句で指定します。</span><span class="sxs-lookup"><span data-stu-id="2d127-110">CONTAINS and FREETEXT are specified in the WHERE or HAVING clause of a SELECT statement.</span></span> <span data-ttu-id="2d127-111">これらの述語は、LIKE や BETWEEN など他の [!INCLUDE[tsql](../../includes/tsql-md.md)] 述語と組み合わせて使用できます。</span><span class="sxs-lookup"><span data-stu-id="2d127-111">They can be combined with any of the other [!INCLUDE[tsql](../../includes/tsql-md.md)] predicates, such as LIKE and BETWEEN.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2d127-112">これらの述語の構文と引数の詳細については、「 [CONTAINS &#40;transact-sql&#41;](/sql/t-sql/queries/contains-transact-sql) 」と「 [FREETEXT &#40;transact-sql&#41;](/sql/t-sql/queries/freetext-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2d127-112">For information about the syntax and arguments of these predicates, see [CONTAINS &#40;Transact-SQL&#41;](/sql/t-sql/queries/contains-transact-sql) and [FREETEXT &#40;Transact-SQL&#41;](/sql/t-sql/queries/freetext-transact-sql).</span></span>  
  
 <span data-ttu-id="2d127-113">CONTAINS または FREETEXT を使用する場合は、検索するテーブルの単一の列、一連の列、すべての列のいずれかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="2d127-113">When using CONTAINS or FREETEXT, you can specify either a single column, a list of columns, or all columns in the table to be searched.</span></span> <span data-ttu-id="2d127-114">また、フルテキスト クエリで単語区切りとステミング、類義語辞典の検索、およびノイズ ワードの削除を行うために使用される言語リソースの言語を指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="2d127-114">Optionally, you can specify the language whose resources will be used by given full-text query for word breaking and stemming, thesaurus lookups, and noise-word removal.</span></span>  
  
 <span data-ttu-id="2d127-115">CONTAINS と FREETEXT は、次のようにさまざまな検索で利用できます。</span><span class="sxs-lookup"><span data-stu-id="2d127-115">CONTAINS and FREETEXT are useful for different kind of matches, as follows:</span></span>  
  
-   <span data-ttu-id="2d127-116">CONTAINS (または CONTAINSTABLE) は、単語または語句との完全一致検索やあいまい一致検索、特定の範囲内での近接検索、または重み付き検索に使用します。</span><span class="sxs-lookup"><span data-stu-id="2d127-116">Use CONTAINS (or CONTAINSTABLE) for precise or fuzzy (less precise) matches to single words and phrases, the proximity of words within a certain distance of one another, or weighted matches.</span></span> <span data-ttu-id="2d127-117">CONTAINS を使用する場合は、検索するテキストを指定する検索条件を少なくとも 1 つ指定し、一致を判断する条件を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2d127-117">When using CONTAINS, you must specify at least one search condition that specifies the text that you are searching for and the conditions that determine matches.</span></span>  
  
     <span data-ttu-id="2d127-118">検索条件の間には論理演算を使用できます。</span><span class="sxs-lookup"><span data-stu-id="2d127-118">You can use logical operation between search conditions.</span></span> <span data-ttu-id="2d127-119">詳細については、このトピックの「 [CONTAINS および CONTAINSTABLE でのブール演算子 (AND、OR、および NOT) の使用](#Using_Boolean_Operators)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2d127-119">For more information, see [Using Boolean operators-AND, OR, AND NOT (in CONTAINS and CONTAINSTABLE)](#Using_Boolean_Operators), later in this topic.</span></span>  
  
-   <span data-ttu-id="2d127-120">FREETEXT (または FREETEXTTABLE) は、指定した単語、語句、または文章 ( *freetext 文字列*) の正確な文字列の並びではなく、意味を照合する場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="2d127-120">Use FREETEXT (or FREETEXTTABLE) for matching the meaning, but not the exact wording, of specified words, phrases or sentences (the *freetext string*).</span></span> <span data-ttu-id="2d127-121">指定した列のフルテキスト インデックスに、用語または一定の形式の用語が見つかった場合は、一致すると判断されます。</span><span class="sxs-lookup"><span data-stu-id="2d127-121">Matches are generated if any term or form of any term is found in the full-text index of a specified column.</span></span>  
  
 <span data-ttu-id="2d127-122">この作業を終えると、CONTAINS または FREETEXT 述語に 4 つの要素で構成される名前を使用して、リンク サーバー上の対象のテーブルのフルテキスト インデックス列にクエリを実行できます。</span><span class="sxs-lookup"><span data-stu-id="2d127-122">You can use a four-part name in the CONTAINS or FREETEXT predicate to query full-text indexed columns of the target tables on a linked server.</span></span> <span data-ttu-id="2d127-123">フルテキスト クエリを受け取るようリモート サーバーを準備するには、リモート サーバー上の検索対象のテーブルおよび列にフルテキスト インデックスを作成し、リモート サーバーをリンク サーバーとして追加します。</span><span class="sxs-lookup"><span data-stu-id="2d127-123">To prepare a remote server to receive full-text queries, create a full-text index on the target tables and columns on the remote server and then add the remote server as a linked server.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2d127-124">データベース互換性レベルが100に設定されている場合、 [OUTPUT 句](/sql/t-sql/queries/output-clause-transact-sql)でフルテキスト述語を使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="2d127-124">Full-text predicates are not allowed in the [OUTPUT Clause](/sql/t-sql/queries/output-clause-transact-sql) when the database compatibility level is set to 100.</span></span>  
  
 
  
### <a name="examples"></a><span data-ttu-id="2d127-125">例</span><span class="sxs-lookup"><span data-stu-id="2d127-125">Examples</span></span>  
  
#### <a name="a-using-contains-with-simple_term"></a><span data-ttu-id="2d127-126">A.</span><span class="sxs-lookup"><span data-stu-id="2d127-126">A.</span></span> <span data-ttu-id="2d127-127">CONTAINS を <simple_term> と共に使用する</span><span class="sxs-lookup"><span data-stu-id="2d127-127">Using CONTAINS with <simple_term></span></span>  
 <span data-ttu-id="2d127-128">次の例では、 `"Mountain"` という単語を含み、価格が `$80.99` であるすべての製品を検索します。</span><span class="sxs-lookup"><span data-stu-id="2d127-128">The following example finds all products with a price of `$80.99` that contain the word `"Mountain"`.</span></span>  
  
```  
USE AdventureWorks2012  
GO  
  
SELECT Name, ListPrice  
FROM Production.Product  
WHERE ListPrice = 80.99  
   AND CONTAINS(Name, 'Mountain')  
GO  
```  
  
#### <a name="b-using-freetext-to-search-for-words-containing-specified-character-values"></a><span data-ttu-id="2d127-129">B.</span><span class="sxs-lookup"><span data-stu-id="2d127-129">B.</span></span> <span data-ttu-id="2d127-130">FREETEXT を使用して、指定した文字値を含む単語を検索する</span><span class="sxs-lookup"><span data-stu-id="2d127-130">Using FREETEXT to search for words containing specified character values</span></span>  
 <span data-ttu-id="2d127-131">次の例では、vital、safety、components に関連する単語を含むすべてのドキュメントを検索します。</span><span class="sxs-lookup"><span data-stu-id="2d127-131">The following example searches for all documents containing the words related to vital, safety, components.</span></span>  
  
```  
USE AdventureWorks2012  
GO  
  
SELECT Title  
FROM Production.Document  
WHERE FREETEXT (Document, 'vital safety components')  
GO  
```  
  
 
  
##  <a name="overview-of-the-full-text-functions-containstable-and-freetexttable"></a><a name="OV_ft_functions_CONTAINSTABLE_FREETEXTTABLE"></a><span data-ttu-id="2d127-132">フルテキスト関数 (CONTAINSTABLE と FREETEXTTABLE) の概要</span><span class="sxs-lookup"><span data-stu-id="2d127-132">Overview of the Full-Text Functions (CONTAINSTABLE and FREETEXTTABLE)</span></span>  
 <span data-ttu-id="2d127-133">CONTAINSTABLE 関数と FREETEXTTABLE 関数は、SELECT ステートメントの FROM 句で通常のテーブル名と同じように指定できます。</span><span class="sxs-lookup"><span data-stu-id="2d127-133">The CONTAINSTABLE and FREETEXTTABLE functions are referenced like a regular table name in the FROM clause of a SELECT statement.</span></span> <span data-ttu-id="2d127-134">この関数では、フルテキスト クエリと一致する 0 行、1 行、または 2 行以上で構成されるテーブルが返されます。</span><span class="sxs-lookup"><span data-stu-id="2d127-134">They return a table of zero, one, or more rows that match the full-text query.</span></span> <span data-ttu-id="2d127-135">返されたテーブルには、ベース テーブルの行のうち、関数のフルテキスト検索条件に指定した選択基準に一致する行のみが含まれます。</span><span class="sxs-lookup"><span data-stu-id="2d127-135">The returned table contains only rows of the base table that match the selection criteria specified in the full-text search condition of the function.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2d127-136">これらの関数の構文と引数の詳細については、「 [CONTAINSTABLE &#40;transact-sql&#41;](/sql/relational-databases/system-functions/containstable-transact-sql) 」と「 [FREETEXTTABLE &#40;transact-sql&#41;](/sql/relational-databases/system-functions/freetexttable-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2d127-136">For information about the syntax and arguments of these functions, see [CONTAINSTABLE &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/containstable-transact-sql) and [FREETEXTTABLE &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/freetexttable-transact-sql).</span></span>  
  
 <span data-ttu-id="2d127-137">このいずれかの関数を使用するクエリでは、次のように、各行の関連順位値 (RANK) とフルテキスト キー (KEY) が取得されます。</span><span class="sxs-lookup"><span data-stu-id="2d127-137">Queries using one of these functions return a relevance ranking value (RANK) and full-text key (KEY) for each row, as follows:</span></span>  
  
-   <span data-ttu-id="2d127-138">KEY 列</span><span class="sxs-lookup"><span data-stu-id="2d127-138">KEY column</span></span>  
  
     <span data-ttu-id="2d127-139">KEY 列には、返された行の一意の値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="2d127-139">The KEY column returns unique values of the returned rows.</span></span> <span data-ttu-id="2d127-140">KEY 列は、選択基準を指定する際に使用できます。</span><span class="sxs-lookup"><span data-stu-id="2d127-140">The KEY column can be used to specify selection criteria.</span></span>  
  
-   <span data-ttu-id="2d127-141">RANK 列</span><span class="sxs-lookup"><span data-stu-id="2d127-141">RANK column</span></span>  
  
     <span data-ttu-id="2d127-142">RANK 列は、各行が選択条件にどの程度一致しているかを示す *順位値* を返します。</span><span class="sxs-lookup"><span data-stu-id="2d127-142">The RANK column returns a *rank value* for each row that indicates how well the row matched the selection criteria.</span></span> <span data-ttu-id="2d127-143">行内のテキストまたはドキュメントの順位値が高いほど、指定したフルテキスト クエリとその行との関連性が高いことを示します。</span><span class="sxs-lookup"><span data-stu-id="2d127-143">The higher the rank value of the text or document in a row, the more relevant the row is for the given full-text query.</span></span> <span data-ttu-id="2d127-144">複数の行に同じ順位が付けられる可能性もあるので注意してください。</span><span class="sxs-lookup"><span data-stu-id="2d127-144">Note that different rows can be ranked identically.</span></span> <span data-ttu-id="2d127-145">*top_n_by_rank* パラメーター (省略可能) を指定して、返される一致の数を制限することもできます。</span><span class="sxs-lookup"><span data-stu-id="2d127-145">You can limit the number of matches to be returned by specifying the optional *top_n_by_rank* parameter.</span></span> <span data-ttu-id="2d127-146">詳細については、「 [RANK を使用して検索結果を制限する方法](limit-search-results-with-rank.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2d127-146">For more information, see [Limit Search Results with RANK](limit-search-results-with-rank.md).</span></span>  
  
 <span data-ttu-id="2d127-147">どちらの関数を使用する場合も、フルテキスト検索の対象となるベース テーブルを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2d127-147">When using either of these functions, you must specify the base table that is to be full-text searched.</span></span> <span data-ttu-id="2d127-148">述語と同様に、検索するテーブルの単一の列、一連の列、またはすべての列を指定できます。また、必要に応じて、指定したフルテキスト クエリで使用される言語リソースの言語を指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="2d127-148">As with the predicates, you can specify a single column, a list of columns, or all columns in the table to be searched, and optionally, the language whose resources will be used by given full-text query.</span></span>  
  
 <span data-ttu-id="2d127-149">CONTAINSTABLE は CONTAINS と同様の検索に役立ち、FREETEXTTABLE は FREETEXT と同様の検索に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="2d127-149">CONTAINSTABLE is useful for the same kinds of matches as CONTAINS, and FREETEXTTABLE is useful for the same kinds of matches as FREETEXT.</span></span> <span data-ttu-id="2d127-150">詳細については、このトピックの前の「 [フルテキスト述語 (CONTAINS と FREETEXT) の概要](#OV_ft_predicates)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2d127-150">For more information, see [Overview of the Full-Text Predicates (CONTAINS and FREETEXT)](#OV_ft_predicates), earlier in this topic.</span></span> <span data-ttu-id="2d127-151">CONTAINSTABLE 関数と FREETEXTTABLE 関数を使用するクエリを実行する場合は、返された行を元の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ベース テーブルの行と明示的に結合する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2d127-151">When running queries that use the CONTAINSTABLE and FREETEXTTABLE functions you must explicitly join rows that are returned with the rows in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] base table.</span></span>  
  
 <span data-ttu-id="2d127-152">通常、CONTAINSTABLE または FREETEXTTABLE の結果をベース テーブルと結合します。</span><span class="sxs-lookup"><span data-stu-id="2d127-152">Typically, the result of CONTAINSTABLE or FREETEXTTABLE needs to be joined with the base table.</span></span> <span data-ttu-id="2d127-153">その場合、一意なキー列の名前を把握している必要があります。</span><span class="sxs-lookup"><span data-stu-id="2d127-153">In such cases, you need to know the unique key column name.</span></span> <span data-ttu-id="2d127-154">この列は、フルテキストが有効なすべてのテーブルで発生し、テーブルに一意の行を適用するために使用されます (*一意の \* \* キー列*)。</span><span class="sxs-lookup"><span data-stu-id="2d127-154">This column, which occurs in every full-text enabled table, is used to enforce unique rows for the table (the *unique\*\*key column*).</span></span> <span data-ttu-id="2d127-155">詳細については、「 [フルテキスト インデックスの管理](../indexes/indexes.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="2d127-155">For more information, see [Manage Full-Text Indexes](../indexes/indexes.md).</span></span>  
  
 
  
### <a name="examples"></a><span data-ttu-id="2d127-156">例</span><span class="sxs-lookup"><span data-stu-id="2d127-156">Examples</span></span>  
  
#### <a name="a-using-containstable"></a><span data-ttu-id="2d127-157">A.</span><span class="sxs-lookup"><span data-stu-id="2d127-157">A.</span></span> <span data-ttu-id="2d127-158">CONTAINSTABLE を使用する</span><span class="sxs-lookup"><span data-stu-id="2d127-158">Using CONTAINSTABLE</span></span>  
 <span data-ttu-id="2d127-159">次の例では、 **Description** 列の "light" または "lightweight" という語の近くに "aluminum" という語があるすべての製品の説明 ID と説明を返します。</span><span class="sxs-lookup"><span data-stu-id="2d127-159">The following example returns the description ID and description of all products for which the **Description** column contain the word "aluminum" near either the word "light" or the word "lightweight."</span></span> <span data-ttu-id="2d127-160">また、順位値が 2 以上の行だけを返します。</span><span class="sxs-lookup"><span data-stu-id="2d127-160">Only rows with a rank value of 2 or higher are returned.</span></span>  
  
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
      (lightweight NEAR aluminum)'  
   ) AS KEY_TBL  
   ON FT_TBL.ProductDescriptionID = KEY_TBL.[KEY]  
WHERE KEY_TBL.RANK > 2  
ORDER BY KEY_TBL.RANK DESC;  
GO  
```  
  
#### <a name="b-using-freetexttable"></a><span data-ttu-id="2d127-161">B.</span><span class="sxs-lookup"><span data-stu-id="2d127-161">B.</span></span> <span data-ttu-id="2d127-162">FREETEXTTABLE を使用する</span><span class="sxs-lookup"><span data-stu-id="2d127-162">Using FREETEXTTABLE</span></span>  
 <span data-ttu-id="2d127-163">次の例では、FREETEXTTABLE クエリを拡張して、順位の高いものから順に行を返し、各行の順位を選択リストに追加します。</span><span class="sxs-lookup"><span data-stu-id="2d127-163">The following example extends a FREETEXTTABLE query to return the highest ranked rows first and to add the ranking of each row to the select list.</span></span> <span data-ttu-id="2d127-164">クエリを指定するには、 **Productdescriptionid**がテーブルの一意のキー列であることを把握している必要があり `ProductDescription` ます。</span><span class="sxs-lookup"><span data-stu-id="2d127-164">To specify the query, you must know that **ProductDescriptionID** is the unique key column for the `ProductDescription` table.</span></span>  
  
```  
USE AdventureWorks2012  
GO  
  
SELECT KEY_TBL.RANK, FT_TBL.Description  
FROM Production.ProductDescription AS FT_TBL   
     INNER JOIN  
     FREETEXTTABLE(Production.ProductDescription, Description,  
                    'perfect all-around bike') AS KEY_TBL  
     ON FT_TBL.ProductDescriptionID = KEY_TBL.[KEY]  
ORDER BY KEY_TBL.RANK DESC  
GO  
```  
  
 <span data-ttu-id="2d127-165">以下に、同じクエリを拡張して、順位の値が 10 以上の行だけを返す例を示します。</span><span class="sxs-lookup"><span data-stu-id="2d127-165">Here is an extension of the same query that only returns rows with a rank value of 10 or greater:</span></span>  
  
```  
USE AdventureWorks2012  
GO  
  
SELECT KEY_TBL.RANK, FT_TBL.Description  
FROM Production.ProductDescription AS FT_TBL   
     INNER JOIN  
     FREETEXTTABLE(Production.ProductDescription, Description,  
                    'perfect all-around bike') AS KEY_TBL  
     ON FT_TBL.ProductDescriptionID = KEY_TBL.[KEY]  
WHERE KEY_TBL.RANK >= 10  
ORDER BY KEY_TBL.RANK DESC  
GO  
```  
  
 
  
##  <a name="using-boolean-operators---and-or-and-not---in-contains-and-containstable"></a><a name="Using_Boolean_Operators"></a><span data-ttu-id="2d127-166">ブール演算子-AND、OR、および NOT in CONTAINS と CONTAINSTABLE の使用</span><span class="sxs-lookup"><span data-stu-id="2d127-166">Using Boolean operators - AND, OR, and NOT - in CONTAINS and CONTAINSTABLE</span></span>  
 <span data-ttu-id="2d127-167">CONTAINS 述語と CONTAINSTABLE 関数は、同じ検索条件を使用します。</span><span class="sxs-lookup"><span data-stu-id="2d127-167">The CONTAINS predicate and CONTAINSTABLE function use the same search conditions.</span></span> <span data-ttu-id="2d127-168">どちらも、論理演算子 (AND、OR、および NOT) を使用して複数の検索語句を結合し、論理演算を実行します。</span><span class="sxs-lookup"><span data-stu-id="2d127-168">Both support combining several search terms by using Boolean operators-AND, OR, AND NOT-to perform logical operations.</span></span> <span data-ttu-id="2d127-169">たとえば、AND を使用して "latte" と "New York-style bagel" の両方を含む行を検索できます。</span><span class="sxs-lookup"><span data-stu-id="2d127-169">You could use AND, for example, to find rows that contain both "latte" and "New York-style bagel".</span></span> <span data-ttu-id="2d127-170">また、AND NOT を使用して "bagel" を含み、かつ "cream cheese" を含まない行を検索することもできます。</span><span class="sxs-lookup"><span data-stu-id="2d127-170">You can use AND NOT, for example, to find the rows that contain "bagel" but do not contain "cream cheese".</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2d127-171">一方、FREETEXT と FREETEXTTABLE では、ブール演算子は検索対象の語として扱われます。</span><span class="sxs-lookup"><span data-stu-id="2d127-171">In contrast, FREETEXT and FREETEXTTABLE treat the Boolean terms as words to be searched.</span></span>  
  
 <span data-ttu-id="2d127-172">CONTAINS を、論理演算子 AND、OR、および NOT を使用する他の述語と組み合わせる方法については、「[検索条件 &#40;Transact-SQL&#41;](/sql/t-sql/queries/search-condition-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2d127-172">For information about combining CONTAINS with other predicates that use the logical operators AND, OR, and NOT, see [Search Condition &#40;Transact-SQL&#41;](/sql/t-sql/queries/search-condition-transact-sql).</span></span>  
  
### <a name="example"></a><span data-ttu-id="2d127-173">例</span><span class="sxs-lookup"><span data-stu-id="2d127-173">Example</span></span>  
 <span data-ttu-id="2d127-174">次の例では、 [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] データベースの ProductDescription テーブルを使用します。</span><span class="sxs-lookup"><span data-stu-id="2d127-174">The following example uses the ProductDescription table of the [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] database.</span></span> <span data-ttu-id="2d127-175">このクエリでは、CONTAINS 述語を使用して、説明 ID が 5 以外で、説明に "Aluminum" と "spindle" という両方の単語が含まれている説明を検索します。</span><span class="sxs-lookup"><span data-stu-id="2d127-175">The query uses the CONTAINS predicate to search for descriptions in which the description ID is not equal to 5 and the description contains both the word "Aluminum" and the word "spindle."</span></span> <span data-ttu-id="2d127-176">検索条件では、AND ブール演算子を使用します。</span><span class="sxs-lookup"><span data-stu-id="2d127-176">The search condition uses the AND Boolean operator.</span></span>  
  
```  
USE AdventureWorks2012  
GO  
  
SELECT Description  
FROM Production.ProductDescription  
WHERE ProductDescriptionID <> 5 AND  
   CONTAINS(Description, 'aluminum AND spindle')  
GO  
```  
  
 
  
##  <a name="additional-considerations-for-full-text-queries"></a><a name="Additional_Considerations"></a><span data-ttu-id="2d127-177">フルテキストクエリに関するその他の考慮事項</span><span class="sxs-lookup"><span data-stu-id="2d127-177">Additional Considerations for Full-Text Queries</span></span>  
 <span data-ttu-id="2d127-178">フルテキスト クエリを記述する場合は、次の点も考慮してください。</span><span class="sxs-lookup"><span data-stu-id="2d127-178">When writing full-text queries also consider the following:</span></span>  
  
-   <span data-ttu-id="2d127-179">LANGUAGE オプション</span><span class="sxs-lookup"><span data-stu-id="2d127-179">The LANGUAGE option</span></span>  
  
     <span data-ttu-id="2d127-180">クエリ用語の多くは、ワード ブレーカーの動作に大きく依存します。</span><span class="sxs-lookup"><span data-stu-id="2d127-180">Many query terms depend heavily on word-breaker behavior.</span></span> <span data-ttu-id="2d127-181">適切なワード ブレーカー (およびステミング機能) および類義語辞典ファイルを使用するために、LANGUAGE オプションを指定することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="2d127-181">To ensure that you are using the correct word breaker (and stemmer) and thesaurus file, we recommend that you specify the LANGUAGE option.</span></span> <span data-ttu-id="2d127-182">詳細については、「 [フルテキスト インデックス作成時の言語の選択](choose-a-language-when-creating-a-full-text-index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2d127-182">For more information, see [Choose a Language When Creating a Full-Text Index](choose-a-language-when-creating-a-full-text-index.md).</span></span>  
  
-   <span data-ttu-id="2d127-183">ストップワード</span><span class="sxs-lookup"><span data-stu-id="2d127-183">Stopwords</span></span>  
  
     <span data-ttu-id="2d127-184">フルテキスト クエリを定義する際に、Full-Text Engine でストップワード (ノイズ ワードとも呼ばれます) が検索基準から除外されます。</span><span class="sxs-lookup"><span data-stu-id="2d127-184">When defining a full-text query, the Full-Text Engine discards stopwords (also called noise words) from the search criteria.</span></span> <span data-ttu-id="2d127-185">ストップワードとは、"a"、"and"、"is"、"the" などの頻出する単語で、特定のテキストの検索には通常役立ちません。</span><span class="sxs-lookup"><span data-stu-id="2d127-185">Stopwords are words such as "a," "and," "is," or "the," that can occur frequently but that typically do not help when searching for particular text.</span></span> <span data-ttu-id="2d127-186">ストップワードはストップリストに列挙されています。</span><span class="sxs-lookup"><span data-stu-id="2d127-186">Stopwords are listed in a stoplist.</span></span> <span data-ttu-id="2d127-187">各フルテキスト インデックスには特定のストップリストが関連付けられ、それによってクエリから、またはインデックス作成時にインデックスから除外されるストップワードが決まります。</span><span class="sxs-lookup"><span data-stu-id="2d127-187">Each full-text index is associated with a specific stoplist, which determines what stopwords are omitted from the query or the index at indexing time.</span></span> <span data-ttu-id="2d127-188">詳細については、「 [フルテキスト検索に使用するストップワードとストップリストの構成と管理](full-text-search.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2d127-188">For more information, see [Configure and Manage Stopwords and Stoplists for Full-Text Search](full-text-search.md).</span></span>  
  
-   <span data-ttu-id="2d127-189">類義語辞典</span><span class="sxs-lookup"><span data-stu-id="2d127-189">The thesaurus</span></span>  
  
     <span data-ttu-id="2d127-190">FREETEXT クエリと FREETEXTTABLE クエリでは、類義語辞典を既定で使用します。</span><span class="sxs-lookup"><span data-stu-id="2d127-190">FREETEXT and FREETEXTTABLE queries use the thesaurus by default.</span></span> <span data-ttu-id="2d127-191">CONTAINS と CONTAINSTABLE では、省略可能な THESAURUS 引数をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="2d127-191">CONTAINS and CONTAINSTABLE support an optional THESAURUS argument.</span></span>  
  
-   <span data-ttu-id="2d127-192">大文字小文字の区別</span><span class="sxs-lookup"><span data-stu-id="2d127-192">Case sensitivity</span></span>  
  
     <span data-ttu-id="2d127-193">フルテキスト検索クエリでは大文字と小文字は区別されません。</span><span class="sxs-lookup"><span data-stu-id="2d127-193">Full-text search queries are case-insensitive.</span></span> <span data-ttu-id="2d127-194">ただし、日本語の場合は、同じ発音を複数の方法で表記できます。この表記方法を正規化することは、大文字と小文字の区別をなくすことに似ています。たとえば、「かな」で検索することで、大文字小文字を区別しない検索に近い検索を実現できます。</span><span class="sxs-lookup"><span data-stu-id="2d127-194">However, in Japanese, there are multiple phonetic orthographies in which the concept of orthographic normalization is akin to case insensitivity (for example, kana = insensitivity).</span></span> <span data-ttu-id="2d127-195">しかし、このような正規化はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="2d127-195">This type of orthographic normalization is not supported.</span></span>  
  

  
##  <a name="querying-varbinarymax-and-xml-columns"></a><a name="varbinary"></a><span data-ttu-id="2d127-196">Varbinary (max) 列および xml 列のクエリ</span><span class="sxs-lookup"><span data-stu-id="2d127-196">Querying varbinary(max) and xml Columns</span></span>  
 <span data-ttu-id="2d127-197">`varbinary(max)` 列、`varbinary` 列、または `xml` 列にフルテキスト インデックスが設定されている場合は、他のフルテキスト インデックス列と同様に、フルテキスト述語 (CONTAINS および FREETEXT) とフルテキスト関数 (CONTAINSTABLE および FREETEXTTABLE) を使用して、これらの列に対するクエリを実行できます。</span><span class="sxs-lookup"><span data-stu-id="2d127-197">If a `varbinary(max)`, `varbinary`, or `xml` column is full-text indexed, it can be queried using the full-text predicates (CONTAINS and FREETEXT) and functions (CONTAINSTABLE and FREETEXTTABLE), like any other full-text indexed column.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="2d127-198">フルテキスト検索は image 列に対しても実行できます。</span><span class="sxs-lookup"><span data-stu-id="2d127-198">Full-text search also works with image columns.</span></span> <span data-ttu-id="2d127-199">ただし、`image` データ型は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の今後のバージョンでは削除される予定です。</span><span class="sxs-lookup"><span data-stu-id="2d127-199">However, the `image` data type will be removed in a future version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="2d127-200">新規の開発作業ではこのデータ型を使用せず、現在このデータ型を使用しているアプリケーションの変更を検討してください。</span><span class="sxs-lookup"><span data-stu-id="2d127-200">Avoid using this data type in new development work, and plan to modify applications that currently use it.</span></span> <span data-ttu-id="2d127-201">代わりに、`varbinary(max)` データ型を使用してください。</span><span class="sxs-lookup"><span data-stu-id="2d127-201">Use the `varbinary(max)` data type instead.</span></span>  
  
### <a name="varbinarymax-or-varbinary-data"></a><span data-ttu-id="2d127-202">varbinary(max) データまたは varbinary データ</span><span class="sxs-lookup"><span data-stu-id="2d127-202">varbinary(max) or varbinary data</span></span>  
 <span data-ttu-id="2d127-203">単一の `varbinary(max)` 列または `varbinary` 列に、さまざまな型のドキュメントを格納できます。</span><span class="sxs-lookup"><span data-stu-id="2d127-203">A single `varbinary(max)` or `varbinary` column can store many types of documents.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="2d127-204">では、専用のフィルターがオペレーティング システムにインストールされ、使用できるようになっている任意のドキュメント型がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="2d127-204">supports any document type for which a filter is installed and available in the operative system.</span></span> <span data-ttu-id="2d127-205">各ドキュメントのドキュメント型は、ドキュメントのファイル拡張子によって識別されます。</span><span class="sxs-lookup"><span data-stu-id="2d127-205">The document type of each document is identified by the file extension of the document.</span></span> <span data-ttu-id="2d127-206">たとえば、ファイル拡張子が .doc である場合、フルテキスト検索では、Microsoft Word ドキュメントをサポートするフィルターが使用されます。</span><span class="sxs-lookup"><span data-stu-id="2d127-206">For example, for a .doc file extension, full-text search uses the filter that supports Microsoft Word documents.</span></span> <span data-ttu-id="2d127-207">使用可能なドキュメント型の一覧を確認するには、 [sys.fulltext_document_types](/sql/relational-databases/system-catalog-views/sys-fulltext-document-types-transact-sql) カタログ ビューに対してクエリを実行してください。</span><span class="sxs-lookup"><span data-stu-id="2d127-207">For a list of available document types, query the [sys.fulltext_document_types](/sql/relational-databases/system-catalog-views/sys-fulltext-document-types-transact-sql) catalog view.</span></span>  
  
 <span data-ttu-id="2d127-208">Full-Text Engine では、オペレーティング システムにインストールされている既存のフィルターを利用できます。</span><span class="sxs-lookup"><span data-stu-id="2d127-208">Note that the Full-Text Engine can leverage existing filters that are installed in the operating system.</span></span> <span data-ttu-id="2d127-209">オペレーティング システムのフィルター、ワード ブレーカー、およびステミング機能を使用する前に、次のコードを実行してこれらのリソースをサーバー インスタンスに読み込む必要があります。</span><span class="sxs-lookup"><span data-stu-id="2d127-209">Before you can use operating-system filters, word breakers, and stemmers, you must load them in the server instance, as follows:</span></span>  
  
```  
EXEC sp_fulltext_service @action='load_os_resources', @value=1  
```  
  
 <span data-ttu-id="2d127-210">`varbinary(max)` 列にフルテキスト インデックスを作成するには、Full-Text Engine が `varbinary(max)` 列にあるドキュメントのファイル拡張子にアクセスする必要があります。</span><span class="sxs-lookup"><span data-stu-id="2d127-210">To create a full-text index on a `varbinary(max)` column, the Full-Text Engine needs access to the file extensions of the documents in the `varbinary(max)` column.</span></span> <span data-ttu-id="2d127-211">この情報は、型列と呼ばれるテーブル列に格納されている必要があります。型列は、フルテキスト インデックスの `varbinary(max)` 列に関連付けられている必要があります。</span><span class="sxs-lookup"><span data-stu-id="2d127-211">This information must be stored in a table column, called a type column, that must be associated with the `varbinary(max)` column in the full-text index.</span></span> <span data-ttu-id="2d127-212">Full-Text Engine は、ドキュメントにインデックスを作成する際に、型列のファイル拡張子を参照して、使用するフィルターを特定します。</span><span class="sxs-lookup"><span data-stu-id="2d127-212">When indexing a document, the Full-Text Engine uses the file extension in the type column to identify which filter to use.</span></span>  
  
 
  
### <a name="xml-data"></a><span data-ttu-id="2d127-213">xml データ</span><span class="sxs-lookup"><span data-stu-id="2d127-213">xml data</span></span>  
 <span data-ttu-id="2d127-214">`xml` データ型の列には、XML ドキュメントと XML フラグメントのみが格納されます。XML ドキュメントには XML フィルターのみが使用されるため、</span><span class="sxs-lookup"><span data-stu-id="2d127-214">An `xml` data type column stores only XML documents and fragments, and only the XML filter is used for the documents.</span></span> <span data-ttu-id="2d127-215">型列は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="2d127-215">Therefore, a type column is unnecessary.</span></span> <span data-ttu-id="2d127-216">`xml` 列では、フルテキスト インデックスによって XML 要素のコンテンツにインデックスが設定されますが、XML マークアップは無視されます。</span><span class="sxs-lookup"><span data-stu-id="2d127-216">On `xml` columns, the full-text index indexes the content of the XML elements, but ignores the XML markup.</span></span> <span data-ttu-id="2d127-217">属性値には、数値でない限り、フルテキスト インデックスが設定されます。</span><span class="sxs-lookup"><span data-stu-id="2d127-217">Attribute values are full-text indexed unless they are numeric values.</span></span> <span data-ttu-id="2d127-218">要素タグはトークンの境界として使用されます。</span><span class="sxs-lookup"><span data-stu-id="2d127-218">Element tags are used as token boundaries.</span></span> <span data-ttu-id="2d127-219">複数言語を含む整形式の XML または HTML ドキュメントやフラグメントはサポートされます。</span><span class="sxs-lookup"><span data-stu-id="2d127-219">Well-formed XML or HTML documents and fragments containing multiple languages are supported.</span></span>  
  
 <span data-ttu-id="2d127-220">列に対するクエリの詳細につい `xml` ては、「 [XML 列でのフルテキスト検索の使用](../xml/use-full-text-search-with-xml-columns.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2d127-220">For more information about querying on an `xml` column, see [Use Full-Text Search with XML Columns](../xml/use-full-text-search-with-xml-columns.md).</span></span>  
  
 
  
##  <a name="supported-forms-of-query-terms"></a><a name="supported"></a><span data-ttu-id="2d127-221">サポートされているクエリ用語の形式</span><span class="sxs-lookup"><span data-stu-id="2d127-221">Supported Forms of Query Terms</span></span>  
 <span data-ttu-id="2d127-222">このセクションでは、フルテキスト述語および行セット値関数による各クエリ形式のサポートの概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="2d127-222">This section summarizes the support provided for each form of query by the full-text predicates and rowset-valued functions.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2d127-223">指定したクエリ語句の構文については、次の表の **Supported by** 列の対応するリンクをクリックしてください。</span><span class="sxs-lookup"><span data-stu-id="2d127-223">For the syntax a given query term, click the corresponding links in **Supported by** column of the following table.</span></span>  
  
|<span data-ttu-id="2d127-224">クエリ用語の形式</span><span class="sxs-lookup"><span data-stu-id="2d127-224">Query-term form</span></span>|<span data-ttu-id="2d127-225">説明</span><span class="sxs-lookup"><span data-stu-id="2d127-225">Description</span></span>|<span data-ttu-id="2d127-226">サポートしているもの</span><span class="sxs-lookup"><span data-stu-id="2d127-226">Supported by</span></span>|  
|----------------------|-----------------|------------------|  
|<span data-ttu-id="2d127-227">1 つ以上の語または句 (*単純語句*)</span><span class="sxs-lookup"><span data-stu-id="2d127-227">One or more specific words or phrases (*simple term*)</span></span>|<span data-ttu-id="2d127-228">フルテキスト検索において、語 (または *トークン*) とは、指定された言語の規則に従って適切なワード ブレーカーによって境界が識別された文字列です。</span><span class="sxs-lookup"><span data-stu-id="2d127-228">In full-text search, a word (or *token*) is a string whose boundaries are identified by appropriate word breakers, following the linguistic rules of the specified language.</span></span> <span data-ttu-id="2d127-229">有効な句は、複数の語から構成されます。句読点を含む場合も含まない場合もあります。</span><span class="sxs-lookup"><span data-stu-id="2d127-229">A valid phrase consists of multiple words, with or without any punctuation marks between them.</span></span><br /><br /> <span data-ttu-id="2d127-230">たとえば、"クロワッサン" は単語で、"caf?</span><span class="sxs-lookup"><span data-stu-id="2d127-230">For example, "croissant" is a word, and "caf??</span></span> <span data-ttu-id="2d127-231">au lait "は、語句です。</span><span class="sxs-lookup"><span data-stu-id="2d127-231">au lait" is a phrase.</span></span> <span data-ttu-id="2d127-232">このような語や句は単純語句と呼ばれています。</span><span class="sxs-lookup"><span data-stu-id="2d127-232">Words and phrases such as these are called simple terms.</span></span><br /><br /> <span data-ttu-id="2d127-233">詳細については、このトピックの後の「 [特定の語または句 (単純語句) の検索](#Simple_Term)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2d127-233">For more information, see [Searching for Specific word or Phrase (Simple Term)](#Simple_Term), later in this topic.</span></span>|<span data-ttu-id="2d127-234">[CONTAINS](/sql/t-sql/queries/contains-transact-sql) および [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) は、句に完全一致するものを検索します。</span><span class="sxs-lookup"><span data-stu-id="2d127-234">[CONTAINS](/sql/t-sql/queries/contains-transact-sql) and [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) look for an exact match for the phrase.</span></span><br /><br /> <span data-ttu-id="2d127-235">[FREETEXT](/sql/t-sql/queries/freetext-transact-sql) および [FREETEXTTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql) は、句を個々の語に分解します。</span><span class="sxs-lookup"><span data-stu-id="2d127-235">[FREETEXT](/sql/t-sql/queries/freetext-transact-sql) and [FREETEXTTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql) break up the phrase into separate words.</span></span>|  
|<span data-ttu-id="2d127-236">指定したテキストで始まる語または句 (*プレフィックス語句*)</span><span class="sxs-lookup"><span data-stu-id="2d127-236">A word or a phrase where the words begin with specified text (*prefix term*)</span></span>|<span data-ttu-id="2d127-237">プレフィックス語句とは、派生語または変化形を生成するために語の前に付けられる文字列です。</span><span class="sxs-lookup"><span data-stu-id="2d127-237">A prefix term refers to a string that is affixed to the front of a word to produce a derivative word or an inflected form.</span></span><br /><br /> <span data-ttu-id="2d127-238">1 つのプレフィックス語句の場合、指定したプレフィックス語句で始まるすべての語が、結果セットに含まれます。</span><span class="sxs-lookup"><span data-stu-id="2d127-238">For a single prefix term, any word starting with the specified term will be part of the result set.</span></span> <span data-ttu-id="2d127-239">たとえば、"auto\*" は、"automatic"、"automobile" などに一致します。</span><span class="sxs-lookup"><span data-stu-id="2d127-239">For example, the term "auto\*" matches "automatic", "automobile", and so forth.</span></span><br /><br /> <span data-ttu-id="2d127-240">句の場合、句を構成する各語がプレフィックス語句と見なされます。</span><span class="sxs-lookup"><span data-stu-id="2d127-240">For a phrase, each word within the phrase is considered to be a prefix term.</span></span> <span data-ttu-id="2d127-241">たとえば、"auto tran\*" は "automatic transmission" や "automobile transducer" に一致しますが、"automatic motor transmission" には一致しません。</span><span class="sxs-lookup"><span data-stu-id="2d127-241">For example, the term "auto tran\*" matches "automatic transmission" and "automobile transducer", but it does not match "automatic motor transmission".</span></span><br /><br /> <span data-ttu-id="2d127-242">詳細については、このトピックの後の「 [プレフィックス検索 (プレフィックス語句) の実行](#Prefix_Term)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2d127-242">For more information, see [Performing Prefix Searches (Prefix Term)](#Prefix_Term), later in this topic.</span></span>|<span data-ttu-id="2d127-243">[CONTAINS](/sql/t-sql/queries/contains-transact-sql) および [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql)</span><span class="sxs-lookup"><span data-stu-id="2d127-243">[CONTAINS](/sql/t-sql/queries/contains-transact-sql) and [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql)</span></span>|  
|<span data-ttu-id="2d127-244">特定の語の変化形 (*生成語-変化形*)</span><span class="sxs-lookup"><span data-stu-id="2d127-244">Inflectional forms of a specific word (*generation term-inflectional*)</span></span>|<span data-ttu-id="2d127-245">変化形は、動詞のさまざまな時制および活用、または名詞の単数形と複数形です。</span><span class="sxs-lookup"><span data-stu-id="2d127-245">The inflectional forms are the different tenses and conjugations of a verb or the singular and plural forms of a noun.</span></span> <span data-ttu-id="2d127-246">たとえば、"drive" という語の変化形を検索します。</span><span class="sxs-lookup"><span data-stu-id="2d127-246">For example, search for the inflectional form of the word "drive".</span></span> <span data-ttu-id="2d127-247">テーブルのさまざまな行に、"drive"、"drives"、"drove"、"driving"、および "driven" が含まれている場合、これらはどれも drive という語から変化して生成されているので結果セットに入ります。</span><span class="sxs-lookup"><span data-stu-id="2d127-247">If various rows in the table include the words "drive", "drives", "drove", "driving", and "driven", all would be in the result set because each of these can be inflectionally generated from the word drive.</span></span><br /><br /> <span data-ttu-id="2d127-248">詳細については、このトピックの後の「 [特定の語の変化形 (生成語) の検索](#Inflectional_Generation_Term)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2d127-248">For more information, see [Searching for the Inflectional Form of a Specific Word (Generation Term)](#Inflectional_Generation_Term), later in this topic.</span></span>|<span data-ttu-id="2d127-249">[FREETEXT](/sql/t-sql/queries/freetext-transact-sql)および[FREETEXTTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql)は、指定されたすべての単語の変化形条項を既定で検索します。</span><span class="sxs-lookup"><span data-stu-id="2d127-249">[FREETEXT](/sql/t-sql/queries/freetext-transact-sql) and [FREETEXTTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql) look for inflectional terms of all specified words by default.</span></span><br /><br /> <span data-ttu-id="2d127-250">[CONTAINS](/sql/t-sql/queries/contains-transact-sql) および [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) は、省略可能な INFLECTIONAL 引数をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="2d127-250">[CONTAINS](/sql/t-sql/queries/contains-transact-sql) and [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) support an optional INFLECTIONAL argument.</span></span>|  
|<span data-ttu-id="2d127-251">特定の単語の同義語形式 (*生成語-類義語辞典*)</span><span class="sxs-lookup"><span data-stu-id="2d127-251">Synonymous forms of a specific word (*generation term-thesaurus*)</span></span>|<span data-ttu-id="2d127-252">類義語辞典は、ユーザー指定の用語のシノニムを定義します。</span><span class="sxs-lookup"><span data-stu-id="2d127-252">A thesaurus defines user-specified synonyms for terms.</span></span> <span data-ttu-id="2d127-253">たとえば、エントリ "{car, automobile, truck, van}" が類義語辞典に追加されると、"car" という語の類義語形式を検索できます。</span><span class="sxs-lookup"><span data-stu-id="2d127-253">For example, if an entry, "{car, automobile, truck, van}", is added to a thesaurus, you can search for the thesaurus form of the word "car".</span></span> <span data-ttu-id="2d127-254">"automobile"、"truck"、"van"、または "car" という語は、"car" という語を含むシノニムの拡張セットに属しているため、クエリ処理されるテーブルの行のうち、これらのいずれかの語を含むすべての行が結果セットに表示されます。</span><span class="sxs-lookup"><span data-stu-id="2d127-254">All rows in the table queried that include the words "automobile", "truck", "van", or "car", appear in the result set because each of these words belong to the synonym expansion set containing the word "car".</span></span><br /><br /> <span data-ttu-id="2d127-255">類義語辞典ファイルの構造の詳細については、「 [フルテキスト検索に使用する類義語辞典ファイルの構成と管理](configure-and-manage-thesaurus-files-for-full-text-search.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2d127-255">For information about the structure of thesaurus files, see [Configure and Manage Thesaurus Files for Full-Text Search](configure-and-manage-thesaurus-files-for-full-text-search.md).</span></span>|<span data-ttu-id="2d127-256">[FREETEXT](/sql/t-sql/queries/freetext-transact-sql) と [FREETEXTTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql) は、類義語辞典を既定で使用します。</span><span class="sxs-lookup"><span data-stu-id="2d127-256">[FREETEXT](/sql/t-sql/queries/freetext-transact-sql) and [FREETEXTTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql) use the thesaurus by default.</span></span><br /><br /> <span data-ttu-id="2d127-257">[CONTAINS](/sql/t-sql/queries/contains-transact-sql) および [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) は、省略可能な THESAURUS 引数をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="2d127-257">[CONTAINS](/sql/t-sql/queries/contains-transact-sql) and [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) support an optional THESAURUS argument.</span></span>|  
|<span data-ttu-id="2d127-258">他の語または句に近接する語または句 (*近接語句*)</span><span class="sxs-lookup"><span data-stu-id="2d127-258">A word or phrase close to another word or phrase (*proximity term*)</span></span>|<span data-ttu-id="2d127-259">近接語句とは、互いに近接する語または句を表します。最初の検索語句と最後の検索語句を分離する非検索用語の最大数を指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="2d127-259">A proximity term indicates words or phrases that are near to each other., You can also specify the maximum number of non-search terms that separate the first and last search terms.</span></span> <span data-ttu-id="2d127-260">さらに、任意の順序で語や句を検索したり、指定した順序で語や句を検索したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="2d127-260">In addition, you can search for words or phrases in any order, or in the order in which you specify them.</span></span><br /><br /> <span data-ttu-id="2d127-261">たとえば、"ice" という語の近くに "hockey" という語がある行や、"ice skating" という句の近くに "ice hockey" という句がある行を検索できます。</span><span class="sxs-lookup"><span data-stu-id="2d127-261">For example, you want to find the rows in which the word "ice" is near the word "hockey" or in which the phrase "ice skating" is near the phrase "ice hockey".</span></span><br /><br /> <span data-ttu-id="2d127-262">詳細については、「 [NEAR による他の単語の近くにある単語の検索](search-for-words-close-to-another-word-with-near.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2d127-262">For more information, see [Search for Words Close to Another Word with NEAR](search-for-words-close-to-another-word-with-near.md).</span></span>|<span data-ttu-id="2d127-263">[CONTAINS](/sql/t-sql/queries/contains-transact-sql) および [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql)</span><span class="sxs-lookup"><span data-stu-id="2d127-263">[CONTAINS](/sql/t-sql/queries/contains-transact-sql) and [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql)</span></span>|  
|<span data-ttu-id="2d127-264">重み付け値を使用している語または句 (*重み付け語句*)</span><span class="sxs-lookup"><span data-stu-id="2d127-264">Words or phrases using weighted values (*weighted term*)</span></span>|<span data-ttu-id="2d127-265">一連の語句内における各語句の重要度を示す重み付け値です。</span><span class="sxs-lookup"><span data-stu-id="2d127-265">A weighting value that indicates the degree of importance for each word and phrase within a set of words and phrases.</span></span> <span data-ttu-id="2d127-266">重み付け値 0.0 は最低値であり、重み付け値 1.0 は最高値です。</span><span class="sxs-lookup"><span data-stu-id="2d127-266">A weight value of 0.0 is the lowest, and a weight value of 1.0 is the highest.</span></span><br /><br /> <span data-ttu-id="2d127-267">たとえば、複数の語句を検索するクエリでは、検索条件の各検索語に、他の語との相対的な重要性を示す重み付け値を割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="2d127-267">For example, in a query searching for multiple terms, you can assign each search word a weight value indicating its importance relative to the other words in the search condition.</span></span> <span data-ttu-id="2d127-268">この種のクエリ結果では、検索語に割り当てた相対的な重みに従って、最も関連性の高い行が最初に返されます。</span><span class="sxs-lookup"><span data-stu-id="2d127-268">The results for this type of query return the most relevant rows first, according to the relative weight you have assigned to search words.</span></span> <span data-ttu-id="2d127-269">結果セットには、指定した語句 (またはそれらの間のコンテンツ) のいずれかを含むドキュメントまたは行が含まれます。ただし、各検索語句に関連付けられている重み付け値の違いにより、一部の結果が他の結果より関連性が高いと見なされます。</span><span class="sxs-lookup"><span data-stu-id="2d127-269">The result sets contain documents or rows containing any of the specified terms (or content between them); however, some results will be considered more relevant than others because of the variation in the weighted values associated with different searched terms.</span></span><br /><br /> <span data-ttu-id="2d127-270">詳細については、このトピックの後の「 [重み付け値を使用する語または句 (重み付け語句) の検索](#Weighted_Term)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2d127-270">For more information, see [Searching for Words or Phrases Using Weighted Values (Weighted Term)](#Weighted_Term), later in this topic.</span></span>|[<span data-ttu-id="2d127-271">CONTAINSTABLE</span><span class="sxs-lookup"><span data-stu-id="2d127-271">CONTAINSTABLE</span></span>](/sql/relational-databases/system-functions/containstable-transact-sql)|  
  

  
###  <a name="searching-for-specific-word-or-phrase-simple-term"></a><a name="Simple_Term"></a><span data-ttu-id="2d127-272">特定の語または句 (単純語句) の検索</span><span class="sxs-lookup"><span data-stu-id="2d127-272">Searching for Specific Word or Phrase (Simple Term)</span></span>  
 <span data-ttu-id="2d127-273">[CONTAINS](/sql/t-sql/queries/contains-transact-sql)、 [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql)、 [FREETEXT](/sql/t-sql/queries/freetext-transact-sql)、または [FREETEXTTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql) を使用すると、テーブルで特定の句を検索できます。</span><span class="sxs-lookup"><span data-stu-id="2d127-273">You can use [CONTAINS](/sql/t-sql/queries/contains-transact-sql), [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql), [FREETEXT](/sql/t-sql/queries/freetext-transact-sql), or [FREETEXTTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql) to search a table for a specific phrase.</span></span> <span data-ttu-id="2d127-274">たとえば、データベース内のテーブルを検索して、 `ProductReview` [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] "learning curve" という語句の製品に関するすべてのコメントを検索する場合は、次のように CONTAINS 述語を使用できます。</span><span class="sxs-lookup"><span data-stu-id="2d127-274">For example, if you want to search the `ProductReview` table in the [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] database to find all comments about a product with the phrase "learning curve", you could use the CONTAINS predicate as follows:</span></span>  
  
```  
USE AdventureWorks2012  
GO  
  
SELECT Comments  
FROM Production.ProductReview  
WHERE CONTAINS(Comments, '"learning curve"')  
GO  
```  
  
 <span data-ttu-id="2d127-275">検索条件 (この場合は "learning curve") には、1 つ以上の語で構成される複雑な条件を指定できます。</span><span class="sxs-lookup"><span data-stu-id="2d127-275">The search condition, in this case "learning curve", can be quite complex and can be composed of one or more terms</span></span>  
  
 
  
###  <a name="performing-prefix-searches-prefix-term"></a><a name="Prefix_Term"></a><span data-ttu-id="2d127-276">プレフィックス検索 (プレフィックス語句) の実行</span><span class="sxs-lookup"><span data-stu-id="2d127-276">Performing Prefix Searches (Prefix Term)</span></span>  
 <span data-ttu-id="2d127-277">[CONTAINS](/sql/t-sql/queries/contains-transact-sql) または [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) を使用すると、指定したプレフィックスを持つ語または句を検索することができます。</span><span class="sxs-lookup"><span data-stu-id="2d127-277">You can use [CONTAINS](/sql/t-sql/queries/contains-transact-sql) or [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) to search for words or phrases with a specified prefix.</span></span> <span data-ttu-id="2d127-278">指定したプレフィックスで始まるテキストが含まれる列のすべてのエントリが返されます。</span><span class="sxs-lookup"><span data-stu-id="2d127-278">All entries in the column that contain text beginning with the specified prefix are returned.</span></span> <span data-ttu-id="2d127-279">たとえば、 `top`というプレフィックス ( `top``ple`、 `top``ping`、 `top`など) が含まれるすべての行を検索する場合、</span><span class="sxs-lookup"><span data-stu-id="2d127-279">For example, to search for all rows that contain the prefix `top`-, as in `top``ple`, `top``ping`, and `top`.</span></span> <span data-ttu-id="2d127-280">クエリは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="2d127-280">The query looks like this:</span></span>  
  
```  
USE AdventureWorks2012  
GO  
  
SELECT Description, ProductDescriptionID  
FROM Production.ProductDescription  
WHERE CONTAINS (Description, '"top*"' )  
GO  
```  
  
 <span data-ttu-id="2d127-281">アスタリスク (\*) より前のテキストに一致するすべてのテキストが返されます。</span><span class="sxs-lookup"><span data-stu-id="2d127-281">All text that matches the text specified before the asterisk (\*) is returned.</span></span> <span data-ttu-id="2d127-282">`CONTAINS (DESCRIPTION, 'top*')`のように、テキストとアスタリスクを二重引用符で囲まなかった場合、フルテキスト検索ではアスタリスクはワイルドカードとして認識されません。</span><span class="sxs-lookup"><span data-stu-id="2d127-282">If the text and asterisk are not delimited by double quotation marks, as in `CONTAINS (DESCRIPTION, 'top*')`, full-text search does not consider the asterisk to be a wildcard..</span></span>  
  
 <span data-ttu-id="2d127-283">プレフィックス語句が句の場合、句を構成する各トークンは、それぞれ独立したプレフィックス語句と見なされます。</span><span class="sxs-lookup"><span data-stu-id="2d127-283">When the prefix term is a phrase, each token making up the phrase is considered a separate prefix term.</span></span> <span data-ttu-id="2d127-284">それらのプレフィックス語句で始まる語を持つすべての行が返されます。</span><span class="sxs-lookup"><span data-stu-id="2d127-284">All rows that have words beginning with the prefix terms will be returned.</span></span> <span data-ttu-id="2d127-285">たとえば、"light bread\*" というプレフィックス語句を使用すると、"light breaded"、"lightly breaded"、または "light bread" というテキストを含む行が検索されますが、"lightly toasted bread" は対象から除外されます。</span><span class="sxs-lookup"><span data-stu-id="2d127-285">For example, the prefix term "light bread\*" will find rows with text of "light breaded," "lightly breaded," or "light bread," but it will not return "lightly toasted bread".</span></span>  
  
 
  
###  <a name="searching-for-inflectional-forms-of-a-specific-word-generation-term"></a><a name="Inflectional_Generation_Term"></a><span data-ttu-id="2d127-286">特定の語の変化形形式の検索 (生成語)</span><span class="sxs-lookup"><span data-stu-id="2d127-286">Searching for Inflectional Forms of a Specific Word (Generation Term)</span></span>  
 <span data-ttu-id="2d127-287">[CONTAINS](/sql/t-sql/queries/contains-transact-sql)、 [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql)、 [FREETEXT](/sql/t-sql/queries/freetext-transact-sql)、または [FREETEXTTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql) を使用すると、動詞のさまざまな時制および活用、または名詞の単数形と複数形 (変化形検索)、または特定の語のシノニム形 (類義語辞典検索) を検索できます。</span><span class="sxs-lookup"><span data-stu-id="2d127-287">You can use [CONTAINS](/sql/t-sql/queries/contains-transact-sql), [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql), [FREETEXT](/sql/t-sql/queries/freetext-transact-sql), or [FREETEXTTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql) to search for all the different tenses and conjugations of a verb or both the singular and plural forms of a noun (an inflectional search) or for synonymous forms of a specific word (a thesaurus search).</span></span>  
  
 <span data-ttu-id="2d127-288">次の例は `Comments` データベースの `ProductReview` テーブルの `AdventureWorks` 列にある "foot" のすべての語形 ("foot"、"feet" など) を検索します。</span><span class="sxs-lookup"><span data-stu-id="2d127-288">The following example searches for any form of "foot" ("foot", "feet", and so on) in the `Comments` column of the `ProductReview` table in the `AdventureWorks` database.</span></span>  
  
```  
USE AdventureWorks2012  
GO  
  
SELECT Comments, ReviewerName  
FROM Production.ProductReview  
WHERE CONTAINS (Comments, 'FORMSOF(INFLECTIONAL, "foot")')  
GO  
```  
  
> [!NOTE]  
>  <span data-ttu-id="2d127-289">フルテキスト検索では、動詞のさまざまな時制および活用または名詞の単数形と複数形の検索を可能にするステマーが使用されます。</span><span class="sxs-lookup"><span data-stu-id="2d127-289">Full-text search uses stemmers, which allow you to search for the different tenses and conjugations of a verb, or both the singular and plural forms of a noun.</span></span> <span data-ttu-id="2d127-290">ステマーの詳細については、「 [検索用のワード ブレーカーとステミング機能の構成と管理](configure-and-manage-word-breakers-and-stemmers-for-search.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2d127-290">For more information about stemmers, see [Configure and Manage Word Breakers and Stemmers for Search](configure-and-manage-word-breakers-and-stemmers-for-search.md).</span></span>  
  

  
###  <a name="searching-for-words-or-phrases-using-weighted-values-weighted-term"></a><a name="Weighted_Term"></a><span data-ttu-id="2d127-291">重み付け値を使用した単語または語句の検索 (重み付け語句)</span><span class="sxs-lookup"><span data-stu-id="2d127-291">Searching for Words or Phrases Using Weighted Values (Weighted Term)</span></span>  
 <span data-ttu-id="2d127-292">[CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) を使用すると、重み付け値を指定して語または句を検索することができます。</span><span class="sxs-lookup"><span data-stu-id="2d127-292">You can use [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) to search for words or phrases and specify a weighting value.</span></span> <span data-ttu-id="2d127-293">重みは 0.0 ～ 1.0 の数値で指定し、一連の語句内における各語句の重要度を示します。</span><span class="sxs-lookup"><span data-stu-id="2d127-293">Weight, measured as a number from 0.0 through 1.0, indicates the importance of each word and phrase within a set of words and phrases.</span></span> <span data-ttu-id="2d127-294">重み 0.0 は最低値であり、重み 1.0 は最高値です。</span><span class="sxs-lookup"><span data-stu-id="2d127-294">A weight of 0.0 is the lowest, and a weight of 1.0 is the highest.</span></span>  
  
 <span data-ttu-id="2d127-295">次の例のクエリは、重みを使用して、文字列 "Bay" で始まるテキストに "Street" または "View" が含まれる顧客住所をすべて検索します。</span><span class="sxs-lookup"><span data-stu-id="2d127-295">The following example shows a query that searches for all customer addresses, using weights, in which any text beginning with the string "Bay" has either "Street" or "View".</span></span> <span data-ttu-id="2d127-296">結果では、指定した語が多く含まれている行ほど高い順位が付けられます。</span><span class="sxs-lookup"><span data-stu-id="2d127-296">The results give a higher rank to those rows that contain more of the words specified.</span></span>  
  
```  
USE AdventureWorks2012  
GO  
  
SELECT AddressLine1, KEY_TBL.RANK   
FROM Person.Address AS Address INNER JOIN  
CONTAINSTABLE(Person.Address, AddressLine1, 'ISABOUT ("Bay*",   
         Street WEIGHT(0.9),   
         View WEIGHT(0.1)  
         ) ' ) AS KEY_TBL  
ON Address.AddressID = KEY_TBL.[KEY]  
ORDER BY KEY_TBL.RANK DESC  
GO  
```  
  
 <span data-ttu-id="2d127-297">重み付け語句は、単純語句、プレフィックス語句、生成語、または近接語句と組み合わせて使用できます。</span><span class="sxs-lookup"><span data-stu-id="2d127-297">A weighted term can be used in conjunction with any simple term, prefix term, generation term, or proximity term.</span></span>  
  

  
##  <a name="viewing-the-tokenization-result-of-a-word-breaker-thesaurus-and-stoplist-combination"></a><a name="tokens"></a><span data-ttu-id="2d127-298">ワードブレーカー、類義語辞典、およびストップリストの組み合わせによるトークン化の結果の表示</span><span class="sxs-lookup"><span data-stu-id="2d127-298">Viewing the Tokenization Result of a Word Breaker, Thesaurus, and Stoplist Combination</span></span>  
 <span data-ttu-id="2d127-299">特定のワード ブレーカー、類義語辞典、ストップリストの組み合わせをクエリ文字列入力に適用した後に、**sys.dm_fts_parser** 動的管理ビューを使用すると、トークン化の結果を確認できます。</span><span class="sxs-lookup"><span data-stu-id="2d127-299">After applying a given word breaker, thesaurus, and stoplist combination to a query string input, you can view the tokenization result by using the **sys.dm_fts_parser** dynamic management view.</span></span> <span data-ttu-id="2d127-300">詳細については、「[sys.dm_fts_parser &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-parser-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2d127-300">For more information, see [sys.dm_fts_parser &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-parser-transact-sql).</span></span>  
  
 
  
## <a name="see-also"></a><span data-ttu-id="2d127-301">参照</span><span class="sxs-lookup"><span data-stu-id="2d127-301">See Also</span></span>  
 <span data-ttu-id="2d127-302">[CONTAINS &#40;Transact-SQL&#41;](/sql/t-sql/queries/contains-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="2d127-302">[CONTAINS &#40;Transact-SQL&#41;](/sql/t-sql/queries/contains-transact-sql) </span></span>  
 <span data-ttu-id="2d127-303">[CONTAINSTABLE &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/containstable-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="2d127-303">[CONTAINSTABLE &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/containstable-transact-sql) </span></span>  
 <span data-ttu-id="2d127-304">[FREETEXT &#40;Transact-SQL&#41;](/sql/t-sql/queries/freetext-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="2d127-304">[FREETEXT &#40;Transact-SQL&#41;](/sql/t-sql/queries/freetext-transact-sql) </span></span>  
 <span data-ttu-id="2d127-305">[FREETEXTTABLE &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/freetexttable-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="2d127-305">[FREETEXTTABLE &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/freetexttable-transact-sql) </span></span>  
 <span data-ttu-id="2d127-306">[フルテキスト検索クエリの作成 &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="2d127-306">[Create Full-Text Search Queries &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/visual-database-tools.md) </span></span>  
 [<span data-ttu-id="2d127-307">フルテキスト クエリのパフォーマンスの向上</span><span class="sxs-lookup"><span data-stu-id="2d127-307">Improve the Performance of Full-Text Queries</span></span>](improve-the-performance-of-full-text-queries.md)  
  
  
