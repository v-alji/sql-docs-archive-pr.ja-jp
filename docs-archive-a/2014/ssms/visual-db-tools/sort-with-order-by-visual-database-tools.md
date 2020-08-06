---
title: ORDER BY 句での並べ替え (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- ORDER BY clause [Visual Database Tools]
ms.assetid: 459f5640-8058-4c24-97e7-7bbd6168bc39
author: stevestein
ms.author: sstein
ms.openlocfilehash: 93bdb9ed01c7935c5b9dae543804fca758a9262d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737362"
---
# <a name="sort-with-order-by-visual-database-tools"></a><span data-ttu-id="f1172-102">ORDER BY 句での並べ替え (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="f1172-102">Sort with ORDER BY (Visual Database Tools)</span></span>
  <span data-ttu-id="f1172-103">ORDER BY 句を使用すると、返される行内のクエリの結果を、1 つまたは複数の列を使用して並べ替えることができます。</span><span class="sxs-lookup"><span data-stu-id="f1172-103">You can sort query results by one or more of the columns in the returned rows by using an ORDER BY clause.</span></span> <span data-ttu-id="f1172-104">ORDER BY 句は、抽出条件ペインでオプションを選択することによって定義できます。</span><span class="sxs-lookup"><span data-stu-id="f1172-104">You can define an ORDER BY clause by choosing options in the Criteria Details pane.</span></span>  
  
### <a name="to-sort-a-query-using-an-order-by-clause"></a><span data-ttu-id="f1172-105">ORDER BY 句を使用してクエリを並べ替えるには</span><span class="sxs-lookup"><span data-stu-id="f1172-105">To sort a query using an ORDER BY clause</span></span>  
  
1.  <span data-ttu-id="f1172-106">クエリを開くか、新規作成します。</span><span class="sxs-lookup"><span data-stu-id="f1172-106">Open a query or create a new one.</span></span>  
  
2.  <span data-ttu-id="f1172-107">[抽出条件ペイン](visual-database-tools.md)で、クエリ結果の並べ替えに使用する列に対応する行の **[並べ替えの種類]** 列をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f1172-107">In the [Criteria Pane](visual-database-tools.md), click the **Sort Type** column for the row corresponding to the column that you want to use to sort your query results.</span></span>  
  
3.  <span data-ttu-id="f1172-108">ドロップダウン リストから、 *[昇順]* または *[降順]* を選択します。</span><span class="sxs-lookup"><span data-stu-id="f1172-108">Choose *Ascending* or *Descending* from the drop-down list.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f1172-109">列の **[並べ替えの種類]** のエントリを削除すると、その列が ORDER BY 句から削除されます。</span><span class="sxs-lookup"><span data-stu-id="f1172-109">Clearing the **Sort Type** entry for a column removes that column from the ORDER BY clause.</span></span>  
  
 <span data-ttu-id="f1172-110">抽出条件ペインで操作を行うと、最後に行った操作に合わせてクエリの UNION 句が変化します。</span><span class="sxs-lookup"><span data-stu-id="f1172-110">Notice that as you work in the Criteria pane, your query's UNION clause changes to match your most recent actions.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f1172-111">複数の列を使用して結果を並べ替えるときは、 **[並べ替え順序]** 列を使用して、列を検索する順序を互いの列を基準にして指定します。</span><span class="sxs-lookup"><span data-stu-id="f1172-111">When sorting results by more than one column, specify the order in which columns are searched relative to each other by using the **Sort Order** column.</span></span> <span data-ttu-id="f1172-112">詳細については、「 **クエリ内の複数の列を並べ替える方法**」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f1172-112">For more information, see **How to: Sort Multiple Columns in Queries**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1172-113">参照</span><span class="sxs-lookup"><span data-stu-id="f1172-113">See Also</span></span>  
 <span data-ttu-id="f1172-114">[クエリ結果の並べ替えとグループ化 &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="f1172-114">[Sort and Group Query Results &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md) </span></span>  
 <span data-ttu-id="f1172-115">[Visual Database Tools &#40;クエリ結果の概要&#41;](summarize-query-results-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="f1172-115">[Summarize Query Results &#40;Visual Database Tools&#41;](summarize-query-results-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="f1172-116">クエリおよびビューのデザインの操作方法に関するトピック (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="f1172-116">Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;</span></span>](design-queries-and-views-how-to-topics-visual-database-tools.md)  
  
  
