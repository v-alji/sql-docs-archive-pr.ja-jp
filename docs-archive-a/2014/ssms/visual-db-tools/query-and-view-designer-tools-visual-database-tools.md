---
title: クエリおよびビュー デザイナー ツール (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.querydesigner
- vdt.pane.diagram
- vdt.pane.grid
- vdt.dlgbox.querybuilder
- vdt.pane.sql
- vdt.pane.results
helpviewer_keywords:
- Query Designer [SQL Server], panes
- View Designer, panes
- Query Designer [SQL Server], components
- View Designer, components
ms.assetid: 12e4b5a5-b793-4b6c-a0e5-c450c49bf26f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 29bd3fa9e171551197927aae0d1bc00446df6e7f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720781"
---
# <a name="query-and-view-designer-tools-visual-database-tools"></a><span data-ttu-id="d3a1e-102">クエリおよびビュー デザイナー ツール (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="d3a1e-102">Query and View Designer Tools (Visual Database Tools)</span></span>
  <span data-ttu-id="d3a1e-103">クエリ、ビュー、インライン関数、または単一ステートメント ストアド プロシージャをデザインするときに使用するデザイナーは、ダイアグラム ペイン、抽出条件ペイン、SQL ペイン、および結果ペインで構成されています。</span><span class="sxs-lookup"><span data-stu-id="d3a1e-103">When you design a query, view, in-line function, or single-statement stored procedure, the designer you use consists of four panes: the Diagram pane, the Criteria pane, the SQL pane, and the Results pane.</span></span>  
  
 <span data-ttu-id="d3a1e-104">![クエリ デザイナー](../../database-engine/media//vs-queryviewdsgpanes.gif "[クエリ デザイナー]")</span><span class="sxs-lookup"><span data-stu-id="d3a1e-104">![Query Designer](../../database-engine/media//vs-queryviewdsgpanes.gif "Query Designer")</span></span>  
  
-   <span data-ttu-id="d3a1e-105">ダイアグラム ペインには、問い合わせているテーブルおよび他のテーブル値オブジェクトが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d3a1e-105">The Diagram pane displays the tables and other table-valued objects that you are querying.</span></span> <span data-ttu-id="d3a1e-106">それぞれの四角形は、テーブルまたはテーブル値オブジェクトを表し、使用可能なデータ列を表示します。</span><span class="sxs-lookup"><span data-stu-id="d3a1e-106">Each rectangle represents a table or table-valued object and shows the available data columns.</span></span> <span data-ttu-id="d3a1e-107">結合は、四角形の間を結ぶ線で示されます。</span><span class="sxs-lookup"><span data-stu-id="d3a1e-107">Joins are indicated by lines between the rectangles.</span></span> <span data-ttu-id="d3a1e-108">詳細については、「[ダイアグラム ペイン (Visual Database Tools)](visual-database-tools.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d3a1e-108">For more information, see [Diagram Pane &#40;Visual Database Tools&#41;](visual-database-tools.md).</span></span>  
  
-   <span data-ttu-id="d3a1e-109">抽出条件ペインにはスプレッドシート形式のグリッドが表示されます。このグリッドで、表示するデータ列、選択する行、行をグループ化する方法などを指定できます。</span><span class="sxs-lookup"><span data-stu-id="d3a1e-109">The Criteria pane contains a spreadsheet-like grid in which you specify options, such as which data columns to display, what rows to select, how to group rows, and so on.</span></span> <span data-ttu-id="d3a1e-110">詳細については、「[抽出条件ペイン (Visual Database Tools)](criteria-pane-visual-database-tools.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d3a1e-110">For more information, see [Criteria Pane &#40;Visual Database Tools&#41;](criteria-pane-visual-database-tools.md).</span></span>  
  
-   <span data-ttu-id="d3a1e-111">SQL ペインには、クエリまたはビューの SQL ステートメントが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d3a1e-111">The SQL pane displays the SQL statement for the query or view.</span></span> <span data-ttu-id="d3a1e-112">デザイナーで作成された SQL ステートメントを編集したり、独自の SQL ステートメントを入力したりできます。</span><span class="sxs-lookup"><span data-stu-id="d3a1e-112">You can edit the SQL statement created by the Designer or you can enter your own SQL statement.</span></span> <span data-ttu-id="d3a1e-113">このペインは、UNION クエリなど、ダイアグラム ペインや抽出条件ペインでは作成できない SQL ステートメントを入力する場合に特に便利です。</span><span class="sxs-lookup"><span data-stu-id="d3a1e-113">It is particularly useful for entering SQL statements that cannot be created using the Diagram and Criteria panes, such as union queries.</span></span> <span data-ttu-id="d3a1e-114">詳細については、「[SQL ペイン (Visual Database Tools)](sql-pane-visual-database-tools.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d3a1e-114">For more information, see [SQL Pane &#40;Visual Database Tools&#41;](sql-pane-visual-database-tools.md).</span></span>  
  
-   <span data-ttu-id="d3a1e-115">結果ペインのグリッドには、クエリまたはビューによって取得されたデータが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d3a1e-115">The Results pane shows a grid with data retrieved by the query or view.</span></span> <span data-ttu-id="d3a1e-116">クエリおよびビュー デザイナーでは、最後に実行した選択クエリの結果がペインに表示されます。</span><span class="sxs-lookup"><span data-stu-id="d3a1e-116">In the Query and View Designer, the pane shows the results of the most recently executed SELECT query.</span></span> <span data-ttu-id="d3a1e-117">グリッドのセルの値を編集してデータベースを変更できます。また、行を追加したり削除したりできます。</span><span class="sxs-lookup"><span data-stu-id="d3a1e-117">You can modify the database by editing values in the cells of the grid, and you can add or delete rows.</span></span> <span data-ttu-id="d3a1e-118">詳細については、「[SQL ペイン (Visual Database Tools)](results-pane-visual-database-tools.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d3a1e-118">For more information, see [Results Pane &#40;Visual Database Tools&#41;](results-pane-visual-database-tools.md).</span></span>  
  
 <span data-ttu-id="d3a1e-119">どのペインでも、クエリやビューを作成できます。たとえば、表示する列を指定するには、ダイアグラム ペインの場合は、その列を選択します。抽出条件ペインの場合は、その列を入力します。SQL ペインの場合は、その列を SQL ステートメント内に記述します。</span><span class="sxs-lookup"><span data-stu-id="d3a1e-119">You can create a query or view by working in any of the panes: you can specify a column to display by choosing it in the Diagram pane, entering it into the Criteria pane, or making it part of the SQL statement in the SQL pane.</span></span>  
  
## <a name="displaying-and-hiding-panes"></a><span data-ttu-id="d3a1e-120">ペインの表示と非表示</span><span class="sxs-lookup"><span data-stu-id="d3a1e-120">Displaying and Hiding Panes</span></span>  
 <span data-ttu-id="d3a1e-121">ペインを非表示にする場合、または非表示になっているペインを表示する場合は、デザイン画面を右クリックして **[ペイン]** をポイントし、ペインの名前をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d3a1e-121">To hide a pane or display a pane that is not visible, right-click the design surface, point to **Pane**, and then click the name of the pane.</span></span> <span data-ttu-id="d3a1e-122">クエリおよびビュー デザイナーがクエリ デザイナー モードで開かれている場合、 **[結果]** ペインは使用できません。</span><span class="sxs-lookup"><span data-stu-id="d3a1e-122">If the Query and View Designer is opened in Query Designer mode, the **Results** pane is not available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3a1e-123">参照</span><span class="sxs-lookup"><span data-stu-id="d3a1e-123">See Also</span></span>  
 <span data-ttu-id="d3a1e-124">[クエリおよびビューのデザイン方法に関するトピック &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="d3a1e-124">[Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md) </span></span>  
 <span data-ttu-id="d3a1e-125">[クエリおよびビューデザイナー &#40;Visual Database Tools&#41;を開きます。](open-the-query-and-view-designer-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="d3a1e-125">[Open the Query and View Designer &#40;Visual Database Tools&#41;](open-the-query-and-view-designer-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="d3a1e-126">SQL エディター (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="d3a1e-126">SQL Editor &#40;Visual Database Tools&#41;</span></span>](sql-editor-visual-database-tools.md)  
  
  
