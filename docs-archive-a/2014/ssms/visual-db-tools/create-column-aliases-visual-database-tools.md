---
title: 列の別名の作成 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- columns [SQL Server], aliases
- aliases [SQL Server], columns
ms.assetid: e2e1c166-8ea7-47a2-b6a7-e419bf0fa3bb
author: stevestein
ms.author: sstein
ms.openlocfilehash: febe7ed27ed10a283cab549bc65299577d69761c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634208"
---
# <a name="create-column-aliases-visual-database-tools"></a><span data-ttu-id="ffea8-102">列の別名の作成 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="ffea8-102">Create Column Aliases (Visual Database Tools)</span></span>
  <span data-ttu-id="ffea8-103">列名に別名を作成すると、列名、計算、および集計値を簡単に操作できるようになります。</span><span class="sxs-lookup"><span data-stu-id="ffea8-103">You can create aliases for column names to make it easier to work with column names, calculations, and summary values.</span></span> <span data-ttu-id="ffea8-104">たとえば、列の別名を作成するのは次の場合です。</span><span class="sxs-lookup"><span data-stu-id="ffea8-104">For example, you can create a column alias to:</span></span>  
  
-   <span data-ttu-id="ffea8-105">`(quantity * unit_price)` などの式や集計関数に対して、"Total Amount" などの列名を作成する場合。</span><span class="sxs-lookup"><span data-stu-id="ffea8-105">Create a column name, such as "Total Amount," for an expression such as `(quantity * unit_price)` or for an aggregate function.</span></span>  
  
-   <span data-ttu-id="ffea8-106">次のものに対する `"d_id"` など、列名の短縮形を作成する場合: `"discounts.stor_id."`</span><span class="sxs-lookup"><span data-stu-id="ffea8-106">Create a shortened form of a column name, such as `"d_id"` for `"discounts.stor_id."`</span></span>  
  
 <span data-ttu-id="ffea8-107">列の別名を定義すると、その別名を選択クエリで使用してクエリ出力を指定できます。</span><span class="sxs-lookup"><span data-stu-id="ffea8-107">After you have defined a column alias, you can use the alias in a Select query to specify query output.</span></span>  
  
### <a name="to-create-a-column-alias"></a><span data-ttu-id="ffea8-108">列の別名を作成するには</span><span class="sxs-lookup"><span data-stu-id="ffea8-108">To create a column alias</span></span>  
  
1.  <span data-ttu-id="ffea8-109">**[抽出条件ペイン]** で、別名を作成するデータ列を含む行を指定し、必要に応じて出力対象として設定します。</span><span class="sxs-lookup"><span data-stu-id="ffea8-109">In the **Criteria Pane**, locate the row containing the data column for which you want to create an alias, and if necessary, mark it for output.</span></span> <span data-ttu-id="ffea8-110">グリッドにデータ列がない場合は、列を追加します。</span><span class="sxs-lookup"><span data-stu-id="ffea8-110">If the data column is not already in the grid, add it.</span></span>  
  
2.  <span data-ttu-id="ffea8-111">その行の **[エイリアス]** 列に別名を入力します。</span><span class="sxs-lookup"><span data-stu-id="ffea8-111">In the **Alias** column for that row, enter the alias.</span></span> <span data-ttu-id="ffea8-112">別名を付けるときは、SQL の名前付け規則に従う必要があります。</span><span class="sxs-lookup"><span data-stu-id="ffea8-112">The alias must follow all naming conventions for SQL.</span></span> <span data-ttu-id="ffea8-113">入力した別名にスペースが含まれる場合は、自動的に区切り記号が付きます。</span><span class="sxs-lookup"><span data-stu-id="ffea8-113">If the alias name you enter contains spaces, the Query and View Designer automatically puts delimiters around it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffea8-114">参照</span><span class="sxs-lookup"><span data-stu-id="ffea8-114">See Also</span></span>  
 <span data-ttu-id="ffea8-115">[Visual Database Tools &#40;クエリに列を追加&#41;](visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="ffea8-115">[Add Columns to Queries &#40;Visual Database Tools&#41;](visual-database-tools.md) </span></span>  
 <span data-ttu-id="ffea8-116">[クエリ結果の並べ替えとグループ化 &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="ffea8-116">[Sort and Group Query Results &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md) </span></span>  
 <span data-ttu-id="ffea8-117">[Visual Database Tools &#40;クエリ結果の概要&#41;](summarize-query-results-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="ffea8-117">[Summarize Query Results &#40;Visual Database Tools&#41;](summarize-query-results-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="ffea8-118">クエリに関する基本操作の実行 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="ffea8-118">Perform Basic Operations with Queries &#40;Visual Database Tools&#41;</span></span>](perform-basic-operations-with-queries-visual-database-tools.md)  
  
  
