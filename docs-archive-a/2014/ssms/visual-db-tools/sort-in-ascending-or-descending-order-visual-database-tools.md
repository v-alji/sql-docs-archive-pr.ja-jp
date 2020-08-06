---
title: 昇順または降順の並べ替え (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- descending sorts
- ascending sorts
ms.assetid: d61cc55b-9ee8-4ecf-a32f-6459ae43910b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 67b5e6b00f62cfc297cc5930bc8cf3a41314a2f8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644744"
---
# <a name="sort-in-ascending-or-descending-order-visual-database-tools"></a><span data-ttu-id="12943-102">昇順または降順の並べ替え (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="12943-102">Sort in Ascending or Descending Order (Visual Database Tools)</span></span>
  <span data-ttu-id="12943-103">`ASC` 句で `DESC` または `ORDER BY` キーワードを使用すると、結果セットの 1 つ以上の列を基準に、クエリ結果を昇順または降順に並べ替えることができます。</span><span class="sxs-lookup"><span data-stu-id="12943-103">You can sort query results in ascending or descending order on one or more of the columns in the result set by using the `ASC` or `DESC` keywords with the `ORDER BY` clause.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="12943-104">並べ替え順序を決定する要素として列の照合順序があります。</span><span class="sxs-lookup"><span data-stu-id="12943-104">The sort order is determined in part by the column's collation sequence.</span></span> <span data-ttu-id="12943-105">この照合順序は、 [[照合順序] ダイアログ ボックス](visual-database-tools.md)で変更できます。</span><span class="sxs-lookup"><span data-stu-id="12943-105">You can change the collation sequence in the [Collation Dialog Box](visual-database-tools.md).</span></span>  
  
 <span data-ttu-id="12943-106">次の手順は、ORDER BY 句を使用して 1 つ以上の列を並べ替えるクエリを、クエリおよびビュー デザイナーで開いていると想定しています。</span><span class="sxs-lookup"><span data-stu-id="12943-106">The following procedure assumes that you have a query open in Query and View Designer that uses the ORDER BY clause to sort one or more columns.</span></span>  
  
### <a name="to-specify-or-change-the-order-in-which-results-are-sorted"></a><span data-ttu-id="12943-107">結果の並べ替え順序を指定または変更するには</span><span class="sxs-lookup"><span data-stu-id="12943-107">To specify or change the order in which results are sorted</span></span>  
  
1.  <span data-ttu-id="12943-108">[抽出条件ペイン](criteria-pane-visual-database-tools.md)で、並べ替えを行う列の **[並べ替えの種類]** フィールドをクリックします。</span><span class="sxs-lookup"><span data-stu-id="12943-108">In the [Criteria pane](criteria-pane-visual-database-tools.md), click the **Sort Type** field for the column that you want to reorder.</span></span>  
  
2.  <span data-ttu-id="12943-109">**[昇順]** または **[降順]** を選択して、列の並べ替え順序を指定します。</span><span class="sxs-lookup"><span data-stu-id="12943-109">Choose **Ascending** or **Descending** to specify the sort order for the column.</span></span>  
  
 <span data-ttu-id="12943-110">抽出条件ペインで操作を行うと、最後に行った操作に合わせてクエリの UNION 句が変化します。</span><span class="sxs-lookup"><span data-stu-id="12943-110">Notice that as you work in the Criteria pane, your query's UNION clause changes to match your most recent actions.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="12943-111">複数の列を使用して結果を並べ替えるときは、[並べ替え順序] 列を使用して、列を検索する順序を互いの列を基準にして指定します。</span><span class="sxs-lookup"><span data-stu-id="12943-111">When sorting results by more than one column, specify the order in which columns are searched relative to each other by using the Sort Order column.</span></span> <span data-ttu-id="12943-112">詳細については、「[クエリ内の複数の列の並べ替え (Visual Database Tools)](sort-multiple-columns-in-queries-visual-database-tools.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="12943-112">For more information, see [Sort Multiple Columns in Queries &#40;Visual Database Tools&#41;](sort-multiple-columns-in-queries-visual-database-tools.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12943-113">参照</span><span class="sxs-lookup"><span data-stu-id="12943-113">See Also</span></span>  
 <span data-ttu-id="12943-114">[クエリ結果の並べ替えとグループ化 &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="12943-114">[Sort and Group Query Results &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md) </span></span>  
 <span data-ttu-id="12943-115">[Visual Database Tools &#40;クエリ結果の概要&#41;](summarize-query-results-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="12943-115">[Summarize Query Results &#40;Visual Database Tools&#41;](summarize-query-results-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="12943-116">クエリおよびビューのデザインの操作方法に関するトピック (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="12943-116">Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;</span></span>](design-queries-and-views-how-to-topics-visual-database-tools.md)  
  
  
