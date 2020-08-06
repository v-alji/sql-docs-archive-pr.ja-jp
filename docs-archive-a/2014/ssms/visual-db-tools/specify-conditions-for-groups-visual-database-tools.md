---
title: グループの条件を指定する方法 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- HAVING clause, query groups
- group query conditions [SQL Server]
ms.assetid: 269ad9c5-3261-4526-badf-7be3c869f229
author: stevestein
ms.author: sstein
ms.openlocfilehash: da9bc1b70fbfae8bf2a68a3a3ba332020020f310
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630732"
---
# <a name="specify-conditions-for-groups-visual-database-tools"></a><span data-ttu-id="f0336-102">グループの条件を指定する方法 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="f0336-102">Specify Conditions for Groups (Visual Database Tools)</span></span>
  <span data-ttu-id="f0336-103">グループ全体に適用する条件を HAVING 句で指定すると、クエリに出力するグループを制限できます。</span><span class="sxs-lookup"><span data-stu-id="f0336-103">You can limit the groups that appear in a query by specifying a condition that applies to groups as a whole - a HAVING clause.</span></span> <span data-ttu-id="f0336-104">データをグループ化し、集計した後、HAVING 句で条件を適用します。</span><span class="sxs-lookup"><span data-stu-id="f0336-104">After the data has been grouped and aggregated, the conditions in the HAVING clause are applied.</span></span> <span data-ttu-id="f0336-105">条件を満たすグループだけがクエリに表示されます。</span><span class="sxs-lookup"><span data-stu-id="f0336-105">Only the groups that meet the conditions appear in the query.</span></span>  
  
 <span data-ttu-id="f0336-106">たとえば、 `titles` テーブルで、出版社別のすべての本の平均価格のうち、$10.00 を超える平均価格だけを表示できます。</span><span class="sxs-lookup"><span data-stu-id="f0336-106">For example, you might want to see the average price of all books for each publisher in a `titles` table, but only if the average price exceeds $10.00.</span></span> <span data-ttu-id="f0336-107">その場合、HAVING 句に `AVG(price) > 10`などの条件を指定します。</span><span class="sxs-lookup"><span data-stu-id="f0336-107">In that case, you could specify a HAVING clause with a condition such as `AVG(price) > 10`.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f0336-108">場合によっては、グループ全体に条件を適用する前に、グループから個別の行を削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f0336-108">In some instances, you might want to exclude individual rows from groups before applying a condition to groups as a whole.</span></span> <span data-ttu-id="f0336-109">詳細については、「[同一クエリ内で HAVING 句および WHERE 句を使用する (Visual Database Tools)](visual-database-tools.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f0336-109">For details, see [Use HAVING and WHERE Clauses in the Same Query &#40;Visual Database Tools&#41;](visual-database-tools.md).</span></span>  
  
 <span data-ttu-id="f0336-110">AND または OR で条件を結合して、HAVING 句に複合条件を作成できます。</span><span class="sxs-lookup"><span data-stu-id="f0336-110">You can create complex conditions for a HAVING clause by using AND and OR to link conditions.</span></span> <span data-ttu-id="f0336-111">検索条件での AND および OR の使用の詳細については、「[1 つの列に対して複数の検索条件を指定する (Visual Database Tools)](specify-multiple-search-conditions-for-one-column-visual-database-tools.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f0336-111">For details about using AND and OR in search conditions, see [Specify Multiple Search Conditions for One Column &#40;Visual Database Tools&#41;](specify-multiple-search-conditions-for-one-column-visual-database-tools.md).</span></span>  
  
### <a name="to-specify-a-condition-for-a-group"></a><span data-ttu-id="f0336-112">グループの条件を指定するには</span><span class="sxs-lookup"><span data-stu-id="f0336-112">To specify a condition for a group</span></span>  
  
1.  <span data-ttu-id="f0336-113">検索するグループを指定します。</span><span class="sxs-lookup"><span data-stu-id="f0336-113">Specify the groups for your query.</span></span> <span data-ttu-id="f0336-114">詳しくは、「[クエリ結果内の行のグループ化 (Visual Database Tools)](group-rows-in-query-results-visual-database-tools.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f0336-114">For details, see [Group Rows in Query Results &#40;Visual Database Tools&#41;](group-rows-in-query-results-visual-database-tools.md).</span></span>  
  
2.  <span data-ttu-id="f0336-115">条件の基準になる列が[抽出条件ペイン](criteria-pane-visual-database-tools.md)にまだない場合は、抽出条件ペインに追加します。</span><span class="sxs-lookup"><span data-stu-id="f0336-115">If it is not already in the [Criteria pane](criteria-pane-visual-database-tools.md), add the column on which you want to base the condition.</span></span> <span data-ttu-id="f0336-116">条件に含まれている列が、既にグループ列または集計列となっている場合がよくあります。集計関数または GROUP BY 句の一部である列は使用できません。</span><span class="sxs-lookup"><span data-stu-id="f0336-116">(Most often the condition involves a column that is already a group or summary column.) You cannot use a column that is not part of an aggregate function or of the GROUP BY clause.</span></span>  
  
3.  <span data-ttu-id="f0336-117">**[フィルター]** 列で、グループに適用する条件を指定します。</span><span class="sxs-lookup"><span data-stu-id="f0336-117">In the **Filter** column, specify the condition to apply to the group.</span></span>  
  
     <span data-ttu-id="f0336-118">次の例に示すように、 [クエリおよびビュー デザイナー](query-and-view-designer-tools-visual-database-tools.md) により、 [SQL ペイン](sql-pane-visual-database-tools.md)のステートメントに HAVING 句が自動的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="f0336-118">The [Query and View Designer](query-and-view-designer-tools-visual-database-tools.md) automatically creates a HAVING clause in the statement in the [SQL pane](sql-pane-visual-database-tools.md), such as in the following example:</span></span>  
  
    ```  
    SELECT pub_id, AVG(price)  
    FROM titles  
    GROUP BY pub_id  
    HAVING (AVG(price) > 10)  
  
    ```  
  
4.  <span data-ttu-id="f0336-119">条件を追加指定するたびに、手順 2. および手順 3. を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="f0336-119">Repeat steps 2 and 3 for each additional condition you want to specify.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0336-120">参照</span><span class="sxs-lookup"><span data-stu-id="f0336-120">See Also</span></span>  
 [<span data-ttu-id="f0336-121">クエリ結果の並べ替えおよびグループ化 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="f0336-121">Sort and Group Query Results &#40;Visual Database Tools&#41;</span></span>](sort-and-group-query-results-visual-database-tools.md)  
  
  
