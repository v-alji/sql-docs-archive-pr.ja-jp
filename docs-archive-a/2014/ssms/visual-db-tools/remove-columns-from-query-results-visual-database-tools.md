---
title: クエリ結果からの列の削除 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- columns [SQL Server], deleting
- result sets [SQL Server], queries
- removing columns
- results [SQL Server], query
- deleting columns
- queries [SQL Server], results
ms.assetid: a7de7a87-4249-49bd-863d-dc0b40a49e78
author: stevestein
ms.author: sstein
ms.openlocfilehash: 90d502ad2cdb4c67d5d4f23f262b56cb17ea7519
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711409"
---
# <a name="remove-columns-from-query-results-visual-database-tools"></a><span data-ttu-id="e19b6-102">クエリ結果からの列の削除 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="e19b6-102">Remove Columns from Query Results (Visual Database Tools)</span></span>
  <span data-ttu-id="e19b6-103">選択クエリで使用する列を結果セットには表示しない場合、つまりクエリの選択リストにはその列が必要ない場合、出力から列を削除できます。</span><span class="sxs-lookup"><span data-stu-id="e19b6-103">If you are using a column in a Select query but do not want to display it in the result set (that is, you do not want it in the query's select list), you can remove it from output.</span></span> <span data-ttu-id="e19b6-104">クエリ出力から列を削除した後でも、検索条件や並べ替えフィールドとしてその列を使用できます。</span><span class="sxs-lookup"><span data-stu-id="e19b6-104">After you remove the column from the query's output, you can still use it in search conditions or as a sorting field.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e19b6-105">クエリから完全に列を削除する場合は、「 [クエリからの列の削除 (Visual Database Tools)](visual-database-tools.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e19b6-105">If you want to remove a column from the query altogether, see [Remove Columns from Queries &#40;Visual Database Tools&#41;](visual-database-tools.md).</span></span>  
  
### <a name="to-remove-a-column-from-the-query-output"></a><span data-ttu-id="e19b6-106">クエリ出力から列を削除するには</span><span class="sxs-lookup"><span data-stu-id="e19b6-106">To remove a column from the query output</span></span>  
  
-   <span data-ttu-id="e19b6-107">**[抽出条件ペイン]** で、削除するデータ列の **[出力]** 列にあるチェック ボックスをオフにします</span><span class="sxs-lookup"><span data-stu-id="e19b6-107">In the **Criteria Pane**, clear the check box in the **Output** column for the data column you want to remove.</span></span> <span data-ttu-id="e19b6-108">(クエリ出力に列を戻す場合は、 **[出力]** 列にあるチェック ボックスを再度オンにします)。</span><span class="sxs-lookup"><span data-stu-id="e19b6-108">(If you want to add the column back to the query output, you can check the **Output** column again.)</span></span>  
  
     <span data-ttu-id="e19b6-109">または</span><span class="sxs-lookup"><span data-stu-id="e19b6-109">-or-</span></span>  
  
-   <span data-ttu-id="e19b6-110">[SQL ペイン](sql-pane-visual-database-tools.md)の出力リストから列を削除します。</span><span class="sxs-lookup"><span data-stu-id="e19b6-110">Remove the column from the output list in the [SQL pane](sql-pane-visual-database-tools.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e19b6-111">参照</span><span class="sxs-lookup"><span data-stu-id="e19b6-111">See Also</span></span>  
 <span data-ttu-id="e19b6-112">[Visual Database Tools &#40;クエリに列を追加&#41;](add-columns-to-queries-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="e19b6-112">[Add Columns to Queries &#40;Visual Database Tools&#41;](add-columns-to-queries-visual-database-tools.md) </span></span>  
 <span data-ttu-id="e19b6-113">[クエリからの列の削除 &#40;Visual Database Tools&#41;](visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="e19b6-113">[Remove Columns from Queries &#40;Visual Database Tools&#41;](visual-database-tools.md) </span></span>  
 <span data-ttu-id="e19b6-114">[クエリ結果の並べ替えとグループ化 &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="e19b6-114">[Sort and Group Query Results &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md) </span></span>  
 <span data-ttu-id="e19b6-115">[Visual Database Tools &#40;クエリ結果の概要&#41;](summarize-query-results-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="e19b6-115">[Summarize Query Results &#40;Visual Database Tools&#41;](summarize-query-results-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="e19b6-116">クエリに関する基本操作の実行 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="e19b6-116">Perform Basic Operations with Queries &#40;Visual Database Tools&#41;</span></span>](perform-basic-operations-with-queries-visual-database-tools.md)  
  
  
