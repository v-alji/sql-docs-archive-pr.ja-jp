---
title: 行を含めるまたは除外する (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- search criteria [SQL Server], excluding rows
- search criteria [SQL Server], WHERE clause
- included rows
- search conditions [SQL Server], HAVING clause
- search criteria [SQL Server], including rows
- row excluded in search [SQL Server]
- search criteria [SQL Server], HAVING clause
- search conditions [SQL Server], WHERE clause
- row included in search [SQL Server]
- excluding rows
ms.assetid: ba4e1202-31a2-444d-8365-c68a530ef223
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7b2d31c51296fa73a503e59a14adb60d79a61178
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641928"
---
# <a name="include-or-exclude-rows-visual-database-tools"></a><span data-ttu-id="e22e5-102">行を含めるまたは除外する (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="e22e5-102">Include or Exclude Rows (Visual Database Tools)</span></span>
  <span data-ttu-id="e22e5-103">選択クエリによって返される行の数を制限するには、検索条件またはフィルター条件を作成します。</span><span class="sxs-lookup"><span data-stu-id="e22e5-103">To restrict the number of rows a SELECT query should return, you create search conditions or filter criteria.</span></span> <span data-ttu-id="e22e5-104">SQL では、ステートメントの WHERE 句、または集計クエリの作成中に HAVING 句で検索条件が表示されます。</span><span class="sxs-lookup"><span data-stu-id="e22e5-104">In SQL, search conditions appear in the WHERE clause of the statement, or if you are creating an aggregate query, in the HAVING clause.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e22e5-105">検索条件を使用して、更新クエリ、結果の挿入クエリ、値の挿入クエリ、削除クエリ、およびテーブルの作成クエリの対象となる行を表すこともできます。</span><span class="sxs-lookup"><span data-stu-id="e22e5-105">You can also use search conditions to indicate which rows are affected by an Update, Insert Results, Insert Values, Delete, or Make Table query.</span></span>  
  
 <span data-ttu-id="e22e5-106">クエリを実行すると、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] により検索条件が調べられ、検索中のテーブルの各行に適用されます。</span><span class="sxs-lookup"><span data-stu-id="e22e5-106">When the query runs, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] examines and applies the search condition to each row in the tables you are searching.</span></span> <span data-ttu-id="e22e5-107">条件を満たす行は、クエリに加えられます。</span><span class="sxs-lookup"><span data-stu-id="e22e5-107">If the row meets the condition, it is included in the query.</span></span> <span data-ttu-id="e22e5-108">たとえば、特定の地域の全従業員を検索する検索条件は、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="e22e5-108">For example, a search condition that would find all the employees in a particular region might be:</span></span>  
  
```  
region = 'UK'  
```  
  
 <span data-ttu-id="e22e5-109">結果に行を含めるための条件を設定する場合は、複数の検索条件を使用できます。</span><span class="sxs-lookup"><span data-stu-id="e22e5-109">To establish the criteria for including a row in a result, you can use multiple search conditions.</span></span> <span data-ttu-id="e22e5-110">たとえば、次の検索条件は、2 つの検索条件で構成されています。</span><span class="sxs-lookup"><span data-stu-id="e22e5-110">For example, the following search criterion consists of two search conditions.</span></span> <span data-ttu-id="e22e5-111">両方の条件を満たす行だけが、クエリの結果セットに含められます。</span><span class="sxs-lookup"><span data-stu-id="e22e5-111">The query includes a row in the result set only if that row satisfies both of the conditions.</span></span>  
  
```  
region = 'UK' AND product_line = 'Housewares'  
```  
  
 <span data-ttu-id="e22e5-112">検索条件は AND または OR で結合できます。</span><span class="sxs-lookup"><span data-stu-id="e22e5-112">You can combine these conditions with AND or OR.</span></span> <span data-ttu-id="e22e5-113">前の例では AND を使用しています。</span><span class="sxs-lookup"><span data-stu-id="e22e5-113">The previous example uses AND.</span></span> <span data-ttu-id="e22e5-114">一方、次に示す条件では OR が使われています。</span><span class="sxs-lookup"><span data-stu-id="e22e5-114">In contrast, the following criterion uses OR.</span></span> <span data-ttu-id="e22e5-115">結果セットには、いずれか一方または両方の検索条件を満たす行が含まれます。</span><span class="sxs-lookup"><span data-stu-id="e22e5-115">The result set will include any row that satisfies either or both of the search conditions:</span></span>  
  
```  
region = 'UK' OR product_line = 'Housewares'  
```  
  
 <span data-ttu-id="e22e5-116">1 つの列に対する複数の検索条件を結合することもできます。</span><span class="sxs-lookup"><span data-stu-id="e22e5-116">You can even combine search conditions on a single column.</span></span> <span data-ttu-id="e22e5-117">たとえば、次の検索条件では、region 列に対する 2 つの条件が結合されています。</span><span class="sxs-lookup"><span data-stu-id="e22e5-117">For example, the following criterion combines two conditions on the region column:</span></span>  
  
```  
region = 'UK' OR region = 'US'  
```  
  
 <span data-ttu-id="e22e5-118">検索条件の結合方法の詳細については、次の各トピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="e22e5-118">For details about combining search conditions, see the following topics:</span></span>  
  
-   [<span data-ttu-id="e22e5-119">抽出条件ペインで検索条件を組み合わせる場合の規則 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="e22e5-119">Conventions for Combining Search Conditions in the Criteria Pane &#40;Visual Database Tools&#41;</span></span>](conventions-combine-search-conditions-in-criteria-pane-visual-db-tools.md)  
  
-   [<span data-ttu-id="e22e5-120">1 つの列に対して複数の検索条件を指定する (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="e22e5-120">Specify Multiple Search Conditions for One Column &#40;Visual Database Tools&#41;</span></span>](visual-database-tools.md)  
  
-   [<span data-ttu-id="e22e5-121">複数の列に対して複数の検索条件を指定する (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="e22e5-121">Specify Multiple Search Conditions for Multiple Columns &#40;Visual Database Tools&#41;</span></span>](specify-multiple-search-conditions-for-multiple-columns-visual-database-tools.md)  
  
-   [<span data-ttu-id="e22e5-122">AND が優先する場合の条件を結合する (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="e22e5-122">Combine Conditions When AND Has Precedence &#40;Visual Database Tools&#41;</span></span>](combine-conditions-when-and-has-precedence-visual-database-tools.md)  
  
-   [<span data-ttu-id="e22e5-123">OR が優先する場合の条件を結合する (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="e22e5-123">Combine Conditions When OR Has Precedence &#40;Visual Database Tools&#41;</span></span>](combine-conditions-when-or-has-precedence-visual-database-tools.md)  
  
## <a name="examples"></a><span data-ttu-id="e22e5-124">例</span><span class="sxs-lookup"><span data-stu-id="e22e5-124">Examples</span></span>  
 <span data-ttu-id="e22e5-125">次に、さまざまな演算子と行抽出条件を使用したクエリの例を示します。</span><span class="sxs-lookup"><span data-stu-id="e22e5-125">Here are some examples of queries using various operators and row criteria:</span></span>  
  
-   <span data-ttu-id="e22e5-126">**リテラル** 単独のテキスト、数値、日付、または論理値です。</span><span class="sxs-lookup"><span data-stu-id="e22e5-126">**Literal** A single text, numeric, date, or logical value.</span></span> <span data-ttu-id="e22e5-127">次の例では、リテラルを使って、イギリス内の従業員に関する行をすべて検索します。</span><span class="sxs-lookup"><span data-stu-id="e22e5-127">The following example uses a literal to find all rows for employees in the United Kingdom:</span></span>  
  
    ```  
    WHERE region = 'UK'  
    ```  
  
-   <span data-ttu-id="e22e5-128">**列参照** ある列の値と別の列の値を比較します。</span><span class="sxs-lookup"><span data-stu-id="e22e5-128">**Column reference** Compares the values in one column with the values in another.</span></span> <span data-ttu-id="e22e5-129">次の例では、 `products` テーブルで製造費が輸送費より少ないすべての行を検索します。</span><span class="sxs-lookup"><span data-stu-id="e22e5-129">The following example searches a `products` table for all rows in which the value of the production cost is lower than the shipping cost:</span></span>  
  
    ```  
    WHERE prod_cost < ship_cost  
    ```  
  
-   <span data-ttu-id="e22e5-130">**関数** 関数を参照して、データベースのバックエンドで検索する値を計算します。</span><span class="sxs-lookup"><span data-stu-id="e22e5-130">**Function** A reference to a function that the database back-end can resolve to calculate a value for the search.</span></span> <span data-ttu-id="e22e5-131">データベース サーバーで定義されている関数、またはスカラー値を返すユーザー定義関数を指定できます。</span><span class="sxs-lookup"><span data-stu-id="e22e5-131">The function can be a function defined by the database server or a user-defined function that returns a scalar value.</span></span> <span data-ttu-id="e22e5-132">次の例では、今日発生した注文を検索します。GETDATE( ) 関数は今日の日付を返します。</span><span class="sxs-lookup"><span data-stu-id="e22e5-132">The following example searches for orders placed today (the GETDATE( ) function returns the current date):</span></span>  
  
    ```  
    WHERE order_date = GETDATE()  
    ```  
  
-   <span data-ttu-id="e22e5-133">**NULL** 次の例では、 `authors` テーブルでファイルに名前のデータがあるすべての著者を検索します。</span><span class="sxs-lookup"><span data-stu-id="e22e5-133">**NULL** The following example searches an `authors` table for all authors who have a first name on file:</span></span>  
  
    ```  
    WHERE au_fname IS NOT NULL  
    ```  
  
-   <span data-ttu-id="e22e5-134">**計算式** 計算結果がリテラル、列参照、または他の式になります。</span><span class="sxs-lookup"><span data-stu-id="e22e5-134">**Calculation** The result of a calculation that can involve literals, column references, or other expressions.</span></span> <span data-ttu-id="e22e5-135">次の例では、 `products` テーブルで小売り価格が製造費の 2 倍を超えるすべての行を検索します。</span><span class="sxs-lookup"><span data-stu-id="e22e5-135">The following example searches a `products` table to find all rows in which the retail sales price is more than twice the production cost:</span></span>  
  
    ```  
    WHERE sales_price > (prod_cost * 2)  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="e22e5-136">参照</span><span class="sxs-lookup"><span data-stu-id="e22e5-136">See Also</span></span>  
 <span data-ttu-id="e22e5-137">[クエリおよびビューのデザイン方法に関するトピック &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="e22e5-137">[Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md) </span></span>  
 <span data-ttu-id="e22e5-138">[Visual Database Tools &#40;検索条件を指定し&#41;](specify-search-criteria-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="e22e5-138">[Specify Search Criteria &#40;Visual Database Tools&#41;](specify-search-criteria-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="e22e5-139">パラメーターを使用したクエリ (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="e22e5-139">Query with Parameters &#40;Visual Database Tools&#41;</span></span>](query-with-parameters-visual-database-tools.md)  
  
  
