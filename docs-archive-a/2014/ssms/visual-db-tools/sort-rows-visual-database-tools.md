---
title: 行の並べ替え (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- sorting rows [SQL Server]
- sorting query results [SQL Server]
ms.assetid: 780ef467-f96e-4373-8235-6dacbedb05a2
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4939c08a4be8c6a7aa3a52d55928abe077f25d76
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737368"
---
# <a name="sort-rows-visual-database-tools"></a><span data-ttu-id="18042-102">行の並べ替え (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="18042-102">Sort Rows (Visual Database Tools)</span></span>
  <span data-ttu-id="18042-103">クエリ結果の行は、並べ替えることができます。</span><span class="sxs-lookup"><span data-stu-id="18042-103">You can order the rows in a query result.</span></span> <span data-ttu-id="18042-104">つまり、特定の列または列のセットを指定し、その値で結果セットの行の順序を決定できます。</span><span class="sxs-lookup"><span data-stu-id="18042-104">That is, you can name a particular column or set of columns whose values determine the order of rows in the result set.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="18042-105">並べ替え順序を決定する要素として列の照合順序があります。</span><span class="sxs-lookup"><span data-stu-id="18042-105">The sort order is determined in part by the column's collation sequence.</span></span> <span data-ttu-id="18042-106">この照合順序は、 [[照合順序] ダイアログ ボックス](visual-database-tools.md)で変更できます。</span><span class="sxs-lookup"><span data-stu-id="18042-106">You can change the collation sequence in the [Collation Dialog Box](visual-database-tools.md).</span></span>  
  
 <span data-ttu-id="18042-107">クエリ結果は、次の方法で並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="18042-107">There are several ways in which you can sort query results:</span></span>  
  
-   <span data-ttu-id="18042-108">**昇順または降順に行を並べ替える** 既定では、SQL は ORDER BY 句で指定された列を使用して、行を昇順に並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="18042-108">**You can arrange rows in ascending or descending order** By default, SQL uses order-by columns to arrange rows in ascending order.</span></span> <span data-ttu-id="18042-109">たとえば、書名を値段の安い順に並べるには、price 列を基準に行を単純に並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="18042-109">For example, to arrange the book titles by ascending price, simply sort the rows by the price column.</span></span> <span data-ttu-id="18042-110">結果の SQL ステートメントは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="18042-110">The resulting SQL might look like this:</span></span>  
  
    ```  
    SELECT *  
    FROM titles  
    ORDER BY price  
  
    ```  
  
     <span data-ttu-id="18042-111">反対に、価格の高い本から順に書名を配列する場合は、最も高価なものを先頭にして並べ替えるように明示的に指定します。</span><span class="sxs-lookup"><span data-stu-id="18042-111">On the other hand, if you want to arrange the titles with the more expensive books first, you can explicitly specify a highest-first ordering.</span></span> <span data-ttu-id="18042-112">つまり、price 列の値を降順にして結果行を並べ替えるように指定します。</span><span class="sxs-lookup"><span data-stu-id="18042-112">That is, you indicate that the result rows should be arranged by descending values of the price column.</span></span> <span data-ttu-id="18042-113">結果の SQL ステートメントは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="18042-113">The resulting SQL might look like this:</span></span>  
  
    ```  
    SELECT *  
    FROM titles  
    ORDER BY price DESC  
  
    ```  
  
-   <span data-ttu-id="18042-114">**複数の列を使って並べ替える** たとえば、最初に州、次に都市の順序で並べ替えると、各著者に対して 1 行を表示する結果セットを作成できます。</span><span class="sxs-lookup"><span data-stu-id="18042-114">**You can sort by multiple columns** For example, you can create a result set with one row for each author, ordering first by state and then by city.</span></span> <span data-ttu-id="18042-115">結果の SQL ステートメントは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="18042-115">The resulting SQL might look like this:</span></span>  
  
    ```  
    SELECT *  
    FROM authors   
    ORDER BY state, city  
  
    ```  
  
-   <span data-ttu-id="18042-116">**結果セットに含まれない列を使って並べ替える** たとえば、価格が結果セットに含まれていなくても、価格の高い順に書名を並べた結果セットを作成できます。</span><span class="sxs-lookup"><span data-stu-id="18042-116">**You can sort by columns not appearing in the result set** For example, you can create a result set with the most expensive titles first, even though the prices do not appear.</span></span> <span data-ttu-id="18042-117">結果の SQL ステートメントは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="18042-117">The resulting SQL might look like this:</span></span>  
  
    ```  
    SELECT title_id, title  
    FROM titles  
    ORDER BY price DESC  
  
    ```  
  
-   <span data-ttu-id="18042-118">**派生列を使って並べ替える** たとえば、印税が最高額である本の書名を最初に表示する結果セットを作成できます。</span><span class="sxs-lookup"><span data-stu-id="18042-118">**You can sort by derived columns** For example, you can create a result set in which each row contains a book title - with the books that pay the highest royalty per copy appearing first.</span></span> <span data-ttu-id="18042-119">結果の SQL ステートメントは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="18042-119">The resulting SQL might look like this:</span></span>  
  
    ```  
    SELECT title, price * royalty / 100 as royalty_per_unit  
    FROM titles  
    ORDER BY royalty_per_unit DESC  
  
    ```  
  
     <span data-ttu-id="18042-120">各本の 1 冊あたりの印税を計算する式は、太字で示してあります。</span><span class="sxs-lookup"><span data-stu-id="18042-120">(The formula for calculating the royalty that each book earns per copy is emphasized.)</span></span>  
  
     <span data-ttu-id="18042-121">派生列の計算には、上記の例のように SQL 構文を使用することも、スカラー値を返すユーザー定義関数を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="18042-121">To calculate a derived column, you can use SQL syntax, as in the preceding example, or you can use a user-defined function that returns a scalar value.</span></span> <span data-ttu-id="18042-122">ユーザー定義関数の詳細については、SQL Server のマニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="18042-122">For more information about user-defined functions, see the SQL Server documentation.</span></span>  
  
-   <span data-ttu-id="18042-123">**グループ化された行を並べ替える** たとえば、都市とその都市の著者数が各行に記述されていて、多数の著者を含む都市が最初に表示される結果セットを作成できます。</span><span class="sxs-lookup"><span data-stu-id="18042-123">**You can sort grouped rows** For example; you can create a result set in which each row describes a city, plus the number of authors in that city - with the cities containing many authors appearing first.</span></span> <span data-ttu-id="18042-124">結果の SQL ステートメントは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="18042-124">The resulting SQL might look like this:</span></span>  
  
    ```  
    SELECT city, state, COUNT(*)  
    FROM authors  
    GROUP BY city, state  
    ORDER BY COUNT(*) DESC, state  
  
    ```  
  
     <span data-ttu-id="18042-125">2 番目の並べ替えの基準にする列として、 `state` 列が指定されています。</span><span class="sxs-lookup"><span data-stu-id="18042-125">Notice that the query uses `state` as a secondary sort column.</span></span> <span data-ttu-id="18042-126">したがって、著者の数が同じ州がある場合は、アルファベット順に表示されます。</span><span class="sxs-lookup"><span data-stu-id="18042-126">Thus, if two states have the same number of authors, those states will appear in alphabetical order.</span></span>  
  
-   <span data-ttu-id="18042-127">**各種言語のデータを使用して並べ替える** つまり、列の既定の規則とは異なる照合規則を使用して、列を並べ替えることができます。</span><span class="sxs-lookup"><span data-stu-id="18042-127">**You can sort using international data** That is; you can sort a column using collating conventions that differ from the default conventions for that column.</span></span> <span data-ttu-id="18042-128">たとえば、Jaime Pati?? を使用してすべての書名を取得するクエリを作成できます。i/o.</span><span class="sxs-lookup"><span data-stu-id="18042-128">For example, you can write a query that retrieves all the book titles by Jaime Pati??o.</span></span> <span data-ttu-id="18042-129">アルファベット順に書名を表示するには、書名列に対してスペイン語の照合規則を使用します。</span><span class="sxs-lookup"><span data-stu-id="18042-129">To display the titles in alphabetical order, you use a Spanish collating sequence for the title column.</span></span> <span data-ttu-id="18042-130">結果の SQL ステートメントは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="18042-130">The resulting SQL might look like this:</span></span>  
  
    ```  
    SELECT title  
    FROM   
        authors   
        INNER JOIN   
            titleauthor   
            ON authors.au_id   
            =  titleauthor.au_id   
            INNER JOIN  
                titles   
                ON titleauthor.title_id   
                =  titles.title_id   
    WHERE   
         au_fname = 'Jaime' AND   
         au_lname = 'Pati??o'  
    ORDER BY   
         title COLLATE SQL_Spanish_Pref_CP1_CI_AS  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="18042-131">参照</span><span class="sxs-lookup"><span data-stu-id="18042-131">See Also</span></span>  
 <span data-ttu-id="18042-132">[クエリ結果の並べ替えとグループ化 &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="18042-132">[Sort and Group Query Results &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="18042-133">クエリおよびビューのデザインの操作方法に関するトピック (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="18042-133">Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;</span></span>](design-queries-and-views-how-to-topics-visual-database-tools.md)  
  
  
