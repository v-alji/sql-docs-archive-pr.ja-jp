---
title: サブクエリの作成 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- search criteria [SQL Server], subqueries
- nested queries
- subqueries [SQL Server], SQL pane
ms.assetid: 34f6b9b4-ca3a-4a4f-9594-36e513f1c547
author: stevestein
ms.author: sstein
ms.openlocfilehash: 540228839b9734992be008b5d4fb7d717176832e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641955"
---
# <a name="create-subqueries-visual-database-tools"></a><span data-ttu-id="67c8a-102">サブクエリの作成 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="67c8a-102">Create Subqueries (Visual Database Tools)</span></span>
  <span data-ttu-id="67c8a-103">クエリの結果は、他のクエリへの入力内容として使用できます。</span><span class="sxs-lookup"><span data-stu-id="67c8a-103">You can use the results of one query as the input for another.</span></span> <span data-ttu-id="67c8a-104">IN( ) 関数、EXISTS 演算子、FROM 句などを使用するサブクエリの結果を、ステートメントとして再利用できます。</span><span class="sxs-lookup"><span data-stu-id="67c8a-104">You can use the results of a subquery as a statement that uses the IN( ) function, the EXISTS operator, or the FROM clause.</span></span>  
  
 <span data-ttu-id="67c8a-105">サブクエリは、SQL ペインに直接入力して作成することも、クエリをコピーおよび貼り付けして作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="67c8a-105">You can create a subquery by entering it directly into the SQL pane or by copying a query and pasting it into another.</span></span>  
  
### <a name="to-define-a-subquery-in-the-sql-pane"></a><span data-ttu-id="67c8a-106">SQL ペインでサブクエリを定義するには</span><span class="sxs-lookup"><span data-stu-id="67c8a-106">To define a subquery in the SQL pane</span></span>  
  
1.  <span data-ttu-id="67c8a-107">最初のクエリを作成します。</span><span class="sxs-lookup"><span data-stu-id="67c8a-107">Create the primary query.</span></span>  
  
2.  <span data-ttu-id="67c8a-108">SQL ペインで SQL ステートメントを選択し、 **[コピー]** をクリックしてクリップボードにクエリを移動します。</span><span class="sxs-lookup"><span data-stu-id="67c8a-108">In the SQL pane, select the SQL statement, and then use **Copy** to move the query to the Clipboard.</span></span>  
  
3.  <span data-ttu-id="67c8a-109">新しいクエリの入力を開始し、WHERE 句または FROM 句に最初のクエリを **[貼り付け]** で貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="67c8a-109">Start the new query, and then use **Paste** to move the first query into the new query's WHERE or FROM clause.</span></span>  
  
     <span data-ttu-id="67c8a-110">たとえば、 `products` および `suppliers`という 2 つのテーブルがあり、スウェーデンの業者の製品をすべて表示するクエリを作成するとします。</span><span class="sxs-lookup"><span data-stu-id="67c8a-110">For example, imagine you have two tables, `products` and `suppliers`, and you want to create a query showing all products for suppliers in Sweden.</span></span> <span data-ttu-id="67c8a-111">まず、 `suppliers` からスウェーデンの業者を検索するクエリを作成します。</span><span class="sxs-lookup"><span data-stu-id="67c8a-111">Create the first query on the `suppliers` table to find all Swedish suppliers:</span></span>  
  
    ```  
    SELECT supplier_id  
    FROM supplier  
    WHERE (country = 'Sweden')  
    ```  
  
     <span data-ttu-id="67c8a-112">[コピー] を使用してクリップボードにこのクエリをコピーします。</span><span class="sxs-lookup"><span data-stu-id="67c8a-112">Use the Copy command to move this query to the Clipboard.</span></span> <span data-ttu-id="67c8a-113">次に、 `products` テーブルから製品に関する情報を一覧表示する 2 番目のクエリを作成します。</span><span class="sxs-lookup"><span data-stu-id="67c8a-113">Create the second query using the `products` table, listing the information you need about products:</span></span>  
  
    ```  
    SELECT product_id, supplier_id, product_name  
    FROM products  
    ```  
  
     <span data-ttu-id="67c8a-114">SQL ペインで、2 番目のクエリに WHERE 句を追加し、クリップボードにある最初のクエリを貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="67c8a-114">In the SQL pane, add a WHERE clause to the second query, then paste the first query from the Clipboard.</span></span> <span data-ttu-id="67c8a-115">最初のクエリをかっこで囲むと、最終的に次のようになります。</span><span class="sxs-lookup"><span data-stu-id="67c8a-115">Place parentheses around the first query, so that the end result looks like this:</span></span>  
  
    ```  
    SELECT product_id, supplier_id, product_name  
    FROM products  
    WHERE supplier_id IN  
       (SELECT supplier_id  
      FROM supplier  
      WHERE (country = 'Sweden'))  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="67c8a-116">参照</span><span class="sxs-lookup"><span data-stu-id="67c8a-116">See Also</span></span>  
 <span data-ttu-id="67c8a-117">[Visual Database Tools &#40;サポートされているクエリの種類&#41;](visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="67c8a-117">[Supported Query Types &#40;Visual Database Tools&#41;](visual-database-tools.md) </span></span>  
 [<span data-ttu-id="67c8a-118">検索基準の指定 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="67c8a-118">Specify Search Criteria &#40;Visual Database Tools&#41;</span></span>](specify-search-criteria-visual-database-tools.md)  
  
  
