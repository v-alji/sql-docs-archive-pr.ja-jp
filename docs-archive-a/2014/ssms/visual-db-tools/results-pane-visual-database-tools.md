---
title: 結果ペイン (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- View Designer, Results pane
- result sets [SQL Server], queries
- synchronization [SQL Server], query results with definition
- displaying query results in grid
- grid showing query results [SQL Server]
- showing query results in grid
- Query Designer [SQL Server], Results pane
- results [SQL Server], query
- viewing query results
- queries [SQL Server], results
- Results pane
ms.assetid: 6309a1bc-a628-4141-8bb5-b35924bd19f9
author: stevestein
ms.author: sstein
ms.openlocfilehash: f0db32336931f74777be56befcde9501dc484b69
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631450"
---
# <a name="results-pane-visual-database-tools"></a><span data-ttu-id="3bd17-102">結果ペイン (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="3bd17-102">Results Pane (Visual Database Tools)</span></span>
  <span data-ttu-id="3bd17-103">結果ペインには、最後に実行された選択クエリの結果が表示されます。</span><span class="sxs-lookup"><span data-stu-id="3bd17-103">The Results pane shows the results of the most recently executed SELECT query.</span></span> <span data-ttu-id="3bd17-104">他の種類のクエリ結果は、メッセージ ボックスに表示されます。結果ペインを表示するには、クエリまたはビューを表示または作成するか、テーブルのデータを返します。</span><span class="sxs-lookup"><span data-stu-id="3bd17-104">(The results of other query types are displayed in message boxes.) To open the results pane, open or create a query or view or return a table's data.</span></span> <span data-ttu-id="3bd17-105">結果ペインが既定で表示されない場合は、 **[クエリ デザイナー]** メニューの **[ペイン]** をポイントし、 **[結果]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3bd17-105">If the results pane doesn't show by default, from the **Query Designer** menu, point to **Pane**, and then click **Results**.</span></span>  
  
## <a name="what-you-can-do-in-the-results-pane"></a><span data-ttu-id="3bd17-106">結果ペインで可能な操作</span><span class="sxs-lookup"><span data-stu-id="3bd17-106">What You Can Do in the Results Pane</span></span>  
  
-   <span data-ttu-id="3bd17-107">最後に実行された選択クエリの結果セットを表形式で参照。</span><span class="sxs-lookup"><span data-stu-id="3bd17-107">View the result set for the most recently executed SELECT query in a spreadsheet-like grid.</span></span>  
  
-   <span data-ttu-id="3bd17-108">単一のテーブルまたはビューからのデータを表示するクエリまたはビューについて、結果セットに含まれる各列の値の編集、新しい行の追加、既存の行の削除。</span><span class="sxs-lookup"><span data-stu-id="3bd17-108">For queries or views that show data from a single table or view, you can edit the values in individual columns in the result set, add new rows, and delete existing rows.</span></span>  
  
## <a name="limitations-in-the-results-pane"></a><span data-ttu-id="3bd17-109">結果ペインの制限</span><span class="sxs-lookup"><span data-stu-id="3bd17-109">Limitations in the Results Pane</span></span>  
  
-   <span data-ttu-id="3bd17-110">テーブル値関数から返された結果は、一部の場合に限り更新できます。</span><span class="sxs-lookup"><span data-stu-id="3bd17-110">Results returned by table-valued functions can only be updated in some cases.</span></span>  
  
-   <span data-ttu-id="3bd17-111">複数のテーブルまたはビューの列を含むクエリまたはビューは更新できません。</span><span class="sxs-lookup"><span data-stu-id="3bd17-111">Queries or views that include columns from more than one table or view cannot be updated.</span></span>  
  
-   <span data-ttu-id="3bd17-112">ストアド プロシージャから返された結果は更新できません。</span><span class="sxs-lookup"><span data-stu-id="3bd17-112">Results returned by a stored procedure cannot be updated.</span></span>  
  
-   <span data-ttu-id="3bd17-113">GROUP BY 句または DISTINCT 句を使用したクエリまたはビューは更新できません。</span><span class="sxs-lookup"><span data-stu-id="3bd17-113">Queries or views using the GROUP BY or DISTINCT clauses are not updatable.</span></span>  
  
## <a name="navigating-in-the-results-pane"></a><span data-ttu-id="3bd17-114">結果ペイン内を移動する</span><span class="sxs-lookup"><span data-stu-id="3bd17-114">Navigating in the Results Pane</span></span>  
 <span data-ttu-id="3bd17-115">結果ペインの下端にあるナビゲーション バーを使用すると、レコード間をすばやく移動できます。</span><span class="sxs-lookup"><span data-stu-id="3bd17-115">You can quickly navigate through the records using the navigation bar at the bottom of the Results pane.</span></span>  
  
 <span data-ttu-id="3bd17-116">最初のレコードと最後のレコードに移動するボタンや、次のレコードと前のレコードに移動するボタン、特定のレコードに移動するボタンがあります。</span><span class="sxs-lookup"><span data-stu-id="3bd17-116">There are buttons for going to the first and last records, the next and previous records, and for going to a particular record.</span></span>  
  
 <span data-ttu-id="3bd17-117">特定のレコードに移動するには、ナビゲーション バー内のテキスト ボックスに行番号を入力し、Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="3bd17-117">To go to a particular record, type the number of the row in the text box in the navigation bar and then press ENTER.</span></span>  
  
 <span data-ttu-id="3bd17-118">クエリおよびビュー デザイナーでキーボード ショートカットを使用する方法については、「[クエリおよびビュー デザイナーでの操作 (Visual Database Tools)](visual-database-tools.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3bd17-118">For information about using keyboard shortcuts in the Query and View Designer see [Navigate in the Query and View Designer &#40;Visual Database Tools&#41;](visual-database-tools.md).</span></span>  
  
## <a name="keeping-the-results-set-synchronized-with-the-query-definition"></a><span data-ttu-id="3bd17-119">結果セットとクエリ定義を同期化する</span><span class="sxs-lookup"><span data-stu-id="3bd17-119">Keeping the Results Set Synchronized with the Query Definition</span></span>  
 <span data-ttu-id="3bd17-120">クエリまたはビューの結果を操作していると、結果ペイン内のレコードがクエリ定義の同期化対象から外れてしまう場合があります。</span><span class="sxs-lookup"><span data-stu-id="3bd17-120">While you are working on the results of a query or view it is possible for the records in the results pane to get out of synchronization with the query's definition.</span></span> <span data-ttu-id="3bd17-121">たとえば、テーブル内の 5 列のうち 4 列についてクエリを実行し、ダイアグラム ペインを使用して 5 番目の列をクエリの定義に追加した場合、その 5 番目の列のデータは、結果ペインに自動的に追加されません。</span><span class="sxs-lookup"><span data-stu-id="3bd17-121">For example, if you run a query for four out of five columns in a table, and then use the Diagram pane to add the fifth column to the definition of the query, that fifth column's data will not automatically be added to the Results pane.</span></span> <span data-ttu-id="3bd17-122">結果ペインに新たなクエリ定義を反映するには、再度クエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="3bd17-122">To make the results pane reflect the new query definition, run the query again.</span></span>  
  
 <span data-ttu-id="3bd17-123">クエリが変更されると、結果ペインの右下端に警告アイコンと "クエリが変更されました。" というテキストが表示され、</span><span class="sxs-lookup"><span data-stu-id="3bd17-123">If a query changes, an alert icon and the text "Query Changed" appears in the lower-right corner of the results pane.</span></span> <span data-ttu-id="3bd17-124">ペインの左上端にも警告アイコンが表示されます。</span><span class="sxs-lookup"><span data-stu-id="3bd17-124">The icon is repeated in the upper-left corner of the pane.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bd17-125">参照</span><span class="sxs-lookup"><span data-stu-id="3bd17-125">See Also</span></span>  
 <span data-ttu-id="3bd17-126">[Visual Database Tools &#40;クエリの作成&#41;](create-queries-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="3bd17-126">[Create Queries &#40;Visual Database Tools&#41;](create-queries-visual-database-tools.md) </span></span>  
 <span data-ttu-id="3bd17-127">[Visual Database Tools &#40;クエリの実行&#41;](run-queries-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="3bd17-127">[Run Queries &#40;Visual Database Tools&#41;](run-queries-visual-database-tools.md) </span></span>  
 <span data-ttu-id="3bd17-128">[クエリおよびビューのデザイン方法に関するトピック &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="3bd17-128">[Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md) </span></span>  
 <span data-ttu-id="3bd17-129">[ダイアグラムペイン &#40;Visual Database Tools&#41;](diagram-pane-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="3bd17-129">[Diagram Pane &#40;Visual Database Tools&#41;](diagram-pane-visual-database-tools.md) </span></span>  
 <span data-ttu-id="3bd17-130">[抽出条件ペイン &#40;Visual Database Tools&#41;](criteria-pane-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="3bd17-130">[Criteria Pane &#40;Visual Database Tools&#41;](criteria-pane-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="3bd17-131">結果ペインのデータの操作 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="3bd17-131">Work with Data in the Results Pane &#40;Visual Database Tools&#41;</span></span>](results-pane-visual-database-tools.md)  
  
  
