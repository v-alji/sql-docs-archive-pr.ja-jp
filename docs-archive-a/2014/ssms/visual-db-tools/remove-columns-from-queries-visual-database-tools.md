---
title: クエリからの列の削除 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- removing columns
- queries [SQL Server], columns
- deleting columns
- dropping columns
ms.assetid: 6d9819b8-ee2f-4838-9713-c5e3ad37ab46
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8532f5240729a2516a0c07ae943dd42dc01d9c1c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719341"
---
# <a name="remove-columns-from-queries-visual-database-tools"></a><span data-ttu-id="9a62b-102">クエリからの列の削除 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="9a62b-102">Remove Columns from Queries (Visual Database Tools)</span></span>
  <span data-ttu-id="9a62b-103">クエリで列を使用する必要がなくなった場合は、列を削除できます。</span><span class="sxs-lookup"><span data-stu-id="9a62b-103">If you no longer want to use a column in a query, you can remove it.</span></span> <span data-ttu-id="9a62b-104">列を削除すると、選択リスト、並べ替えの指定、検索条件、 **SQL ペイン**、およびグループ化の指定での列の参照がクエリおよびビュー デザイナーから削除されます。</span><span class="sxs-lookup"><span data-stu-id="9a62b-104">If you do, the Query and View Designer removes references to the column in the select list, the sort specification, the search criteria, **SQL Pane**, and any grouping specifications.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9a62b-105">クエリそのものから列を削除せずに、選択クエリの結果だけから列を削除する方法もあります。</span><span class="sxs-lookup"><span data-stu-id="9a62b-105">If you want to remove a column from just the output of a Select query, you can do so without removing it from the query altogether.</span></span> <span data-ttu-id="9a62b-106">詳細については、「[クエリ結果からの列の削除 (Visual Database Tools)](visual-database-tools.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9a62b-106">For details, see [Remove Columns from Query Results &#40;Visual Database Tools&#41;](visual-database-tools.md).</span></span>  
  
### <a name="to-remove-a-column-from-the-query"></a><span data-ttu-id="9a62b-107">クエリから列を削除するには</span><span class="sxs-lookup"><span data-stu-id="9a62b-107">To remove a column from the query</span></span>  
  
-   <span data-ttu-id="9a62b-108">**抽出条件ペイン**で、削除する列を含むグリッド行を選択し、Del キーを押します。</span><span class="sxs-lookup"><span data-stu-id="9a62b-108">In the **Criteria Pane**, select the grid row containing the column you want to remove and then press DELETE.</span></span>  
  
     <span data-ttu-id="9a62b-109">または</span><span class="sxs-lookup"><span data-stu-id="9a62b-109">-or-</span></span>  
  
-   <span data-ttu-id="9a62b-110">[SQL ペイン](sql-pane-visual-database-tools.md)の列に対するすべての参照を削除します。</span><span class="sxs-lookup"><span data-stu-id="9a62b-110">Remove all references to the column in the [SQL Pane](sql-pane-visual-database-tools.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a62b-111">参照</span><span class="sxs-lookup"><span data-stu-id="9a62b-111">See Also</span></span>  
 <span data-ttu-id="9a62b-112">[Visual Database Tools &#40;クエリに列を追加&#41;](add-columns-to-queries-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="9a62b-112">[Add Columns to Queries &#40;Visual Database Tools&#41;](add-columns-to-queries-visual-database-tools.md) </span></span>  
 <span data-ttu-id="9a62b-113">[クエリ結果の並べ替えとグループ化 &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="9a62b-113">[Sort and Group Query Results &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md) </span></span>  
 <span data-ttu-id="9a62b-114">[Visual Database Tools &#40;クエリ結果の概要&#41;](summarize-query-results-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="9a62b-114">[Summarize Query Results &#40;Visual Database Tools&#41;](summarize-query-results-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="9a62b-115">クエリに関する基本操作の実行 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="9a62b-115">Perform Basic Operations with Queries &#40;Visual Database Tools&#41;</span></span>](perform-basic-operations-with-queries-visual-database-tools.md)  
  
  
