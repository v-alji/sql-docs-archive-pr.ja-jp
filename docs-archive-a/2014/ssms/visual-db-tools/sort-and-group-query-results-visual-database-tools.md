---
title: クエリ結果の並べ替えおよびグループ化 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- View Designer, Results pane
- result sets [SQL Server], queries
- queries [SQL Server], groups
- Query Designer [SQL Server], Results pane
- results [SQL Server], query
- grouping query results
- row sorting [SQL Server]
- queries [SQL Server], results
- ordering query results [SQL Server]
- Results pane
- sorting query results [SQL Server]
ms.assetid: b004e1c0-cacc-4241-9426-9fd426978918
author: stevestein
ms.author: sstein
ms.openlocfilehash: fdaede20960356404cd0319c213abb76a19b8a77
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711401"
---
# <a name="sort-and-group-query-results-visual-database-tools"></a><span data-ttu-id="9484e-102">クエリ結果の並べ替えおよびグループ化 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="9484e-102">Sort and Group Query Results (Visual Database Tools)</span></span>
  <span data-ttu-id="9484e-103">基になるデータの行グループ全体に結果の各行が対応するようなクエリ結果を作成することができます。</span><span class="sxs-lookup"><span data-stu-id="9484e-103">You can create a query result in which each result row corresponds to an entire group of rows from the original data.</span></span>  
  
 <span data-ttu-id="9484e-104">このようなクエリの作成の詳細については、次の表の各トピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="9484e-104">To learn the details about creating such queries, see the topics listed in the following table.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9484e-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="9484e-105">In This Section</span></span>  
 [<span data-ttu-id="9484e-106">行の並べ替え (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="9484e-106">Sort Rows &#40;Visual Database Tools&#41;</span></span>](visual-database-tools.md)  
 <span data-ttu-id="9484e-107">行を並べ替える各種の方法、およびそれらを使用する目的について説明します。</span><span class="sxs-lookup"><span data-stu-id="9484e-107">Describes the various ways in which you can sort rows and why you would use them.</span></span>  
  
 [<span data-ttu-id="9484e-108">行グループの集約 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="9484e-108">Collapse Groups of Rows &#40;Visual Database Tools&#41;</span></span>](collapse-groups-of-rows-visual-database-tools.md)  
 <span data-ttu-id="9484e-109">計算や複製の削除など、行を折りたたむ各種の方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9484e-109">Describes the various ways to collapse rows, such as calculating or eliminating duplicates.</span></span>  
  
 [<span data-ttu-id="9484e-110">ORDER BY 句での並べ替え (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="9484e-110">Sort with ORDER BY &#40;Visual Database Tools&#41;</span></span>](sort-with-order-by-visual-database-tools.md)  
 <span data-ttu-id="9484e-111">特定の順序で結果を返す方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="9484e-111">Provides steps for returning results in a specified order.</span></span>  
  
 [<span data-ttu-id="9484e-112">昇順または降順の並べ替え (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="9484e-112">Sort in Ascending or Descending Order &#40;Visual Database Tools&#41;</span></span>](sort-in-ascending-or-descending-order-visual-database-tools.md)  
 <span data-ttu-id="9484e-113">並べ替えの方向を変更、または設定する手順を説明します。</span><span class="sxs-lookup"><span data-stu-id="9484e-113">Provides steps for changing or setting sort direction.</span></span>  
  
 [<span data-ttu-id="9484e-114">クエリ内の複数の列の並べ替え (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="9484e-114">Sort Multiple Columns in Queries &#40;Visual Database Tools&#41;</span></span>](sort-multiple-columns-in-queries-visual-database-tools.md)  
 <span data-ttu-id="9484e-115">複数列に対して結果セットの順序を設定する手順を説明します。</span><span class="sxs-lookup"><span data-stu-id="9484e-115">Provides steps for setting the order of results sets for multiple columns.</span></span>  
  
 [<span data-ttu-id="9484e-116">クエリ結果内の行のグループ化 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="9484e-116">Group Rows in Query Results &#40;Visual Database Tools&#41;</span></span>](group-rows-in-query-results-visual-database-tools.md)  
 <span data-ttu-id="9484e-117">データをグループ化して集計情報のサブセットを作成する手順を説明します。</span><span class="sxs-lookup"><span data-stu-id="9484e-117">Provides steps for creating subsets of summary information by organizing data into groups.</span></span>  
  
 [<span data-ttu-id="9484e-118">グループの条件を指定する方法 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="9484e-118">Specify Conditions for Groups &#40;Visual Database Tools&#41;</span></span>](specify-conditions-for-groups-visual-database-tools.md)  
 <span data-ttu-id="9484e-119">行のグループに適用する検索条件を作成する手順を説明します。</span><span class="sxs-lookup"><span data-stu-id="9484e-119">Provides steps for creating search conditions that apply to groups of rows.</span></span>  
  
 [<span data-ttu-id="9484e-120">列の出力順の変更 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="9484e-120">Reorder Output Columns &#40;Visual Database Tools&#41;</span></span>](reorder-output-columns-visual-database-tools.md)  
 <span data-ttu-id="9484e-121">現在の並べ替え設定を変更する手順を説明します。</span><span class="sxs-lookup"><span data-stu-id="9484e-121">Provides steps for changing current sorting settings.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="9484e-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="9484e-122">Related Sections</span></span>  
 [<span data-ttu-id="9484e-123">クエリ結果の要約 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="9484e-123">Summarize Query Results &#40;Visual Database Tools&#41;</span></span>](summarize-query-results-visual-database-tools.md)  
 <span data-ttu-id="9484e-124">クエリ結果の集計に関するトピックへのリンクが用意されています。</span><span class="sxs-lookup"><span data-stu-id="9484e-124">Provides links to topics on summarizing query results.</span></span>  
  
 [<span data-ttu-id="9484e-125">クエリに関する基本操作の実行 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="9484e-125">Perform Basic Operations with Queries &#40;Visual Database Tools&#41;</span></span>](perform-basic-operations-with-queries-visual-database-tools.md)  
 <span data-ttu-id="9484e-126">最も一般的なクエリ タスクに関するトピックへのリンクが用意されています。</span><span class="sxs-lookup"><span data-stu-id="9484e-126">Provides links to topics covering the most common query tasks.</span></span>  
  
 [<span data-ttu-id="9484e-127">クエリおよびビューのデザインの操作方法に関するトピック (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="9484e-127">Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;</span></span>](design-queries-and-views-how-to-topics-visual-database-tools.md)  
 <span data-ttu-id="9484e-128">クエリおよびビュー デザイナーの使用方法を説明するトピックへのリンクが用意されています。</span><span class="sxs-lookup"><span data-stu-id="9484e-128">Provides links to topics covering how to use the Query and View Designer.</span></span>  
  
  
