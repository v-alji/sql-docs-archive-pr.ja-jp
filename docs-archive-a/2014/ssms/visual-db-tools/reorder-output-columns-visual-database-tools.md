---
title: 列の出力順の変更 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- reordering output columns [SQL Server]
- output columns [SQL Server]
ms.assetid: 76462885-de4a-4290-a26b-90696d3671f4
author: stevestein
ms.author: sstein
ms.openlocfilehash: 97fa3f768b03f24b8c8d154624a2d7a91aba45f3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641382"
---
# <a name="reorder-output-columns-visual-database-tools"></a><span data-ttu-id="3b734-102">列の出力順の変更 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="3b734-102">Reorder Output Columns (Visual Database Tools)</span></span>
  <span data-ttu-id="3b734-103">選択クエリにデータ列を追加する順序によって、結果での列の表示順序が決まります。</span><span class="sxs-lookup"><span data-stu-id="3b734-103">The order in which you add data columns to a Select query determines the order in which they appear in the results.</span></span> <span data-ttu-id="3b734-104">最初にクエリに追加した列は結果の左端に表示され、次に追加した列はその右隣に表示されます。</span><span class="sxs-lookup"><span data-stu-id="3b734-104">The first column you add to the query appears leftmost in the results, the second column next, and so on.</span></span>  
  
 <span data-ttu-id="3b734-105">また、更新クエリや挿入クエリを作成する場合、追加した列の順序は、データの処理順序に反映されます。</span><span class="sxs-lookup"><span data-stu-id="3b734-105">If you are creating Update or Insert queries, the order in which you add columns affects the order in which data is processed.</span></span>  
  
 <span data-ttu-id="3b734-106">そのため、データ列を並べ替えると、結果セットの列が表示される順序や処理される順序を変更できます。</span><span class="sxs-lookup"><span data-stu-id="3b734-106">To control where a data column appears in the result set, or in what order it is used, you can reorder the columns.</span></span>  
  
### <a name="to-reorder-columns-for-output"></a><span data-ttu-id="3b734-107">列の出力順を変更するには</span><span class="sxs-lookup"><span data-stu-id="3b734-107">To reorder columns for output</span></span>  
  
1.  <span data-ttu-id="3b734-108">[抽出条件ペイン](visual-database-tools.md)で、対象の列を含む行の左側にある行セレクター ボタンをクリックして、行を選択します。</span><span class="sxs-lookup"><span data-stu-id="3b734-108">In the [Criteria pane](visual-database-tools.md), select the row containing the column by clicking the row selector button to the left of the row.</span></span>  
  
2.  <span data-ttu-id="3b734-109">行セレクター ボタンにポインターを置き、行を新しい場所にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="3b734-109">Point to the row selector button and drag the row to a new location.</span></span>  
  
     <span data-ttu-id="3b734-110">または</span><span class="sxs-lookup"><span data-stu-id="3b734-110">-or-</span></span>  
  
     <span data-ttu-id="3b734-111">[SQL ペイン](sql-pane-visual-database-tools.md)で列名の順序を編集します。</span><span class="sxs-lookup"><span data-stu-id="3b734-111">Edit the order of the column names in the [SQL pane](sql-pane-visual-database-tools.md).</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="3b734-112">抽出条件ペインの特定の場所にデータ行を追加するには、抽出条件ペインの該当する場所に空白行を挿入し、その行に挿入するデータ列を指定します。</span><span class="sxs-lookup"><span data-stu-id="3b734-112">You can add a data row at a specific location in the Criteria pane by inserting a blank row into the Criteria pane, and then specifying the data column to insert.</span></span> <span data-ttu-id="3b734-113">詳しくは、「[クエリに列を追加する方法 (Visual Database Tools)](add-columns-to-queries-visual-database-tools.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="3b734-113">For details, see [Add Columns to Queries &#40;Visual Database Tools&#41;](add-columns-to-queries-visual-database-tools.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b734-114">参照</span><span class="sxs-lookup"><span data-stu-id="3b734-114">See Also</span></span>  
 <span data-ttu-id="3b734-115">[クエリ結果の並べ替えとグループ化 &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="3b734-115">[Sort and Group Query Results &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md) </span></span>  
 <span data-ttu-id="3b734-116">[Visual Database Tools &#40;クエリ結果の概要&#41;](summarize-query-results-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="3b734-116">[Summarize Query Results &#40;Visual Database Tools&#41;](summarize-query-results-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="3b734-117">クエリに関する基本操作の実行 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="3b734-117">Perform Basic Operations with Queries &#40;Visual Database Tools&#41;</span></span>](perform-basic-operations-with-queries-visual-database-tools.md)  
  
  
