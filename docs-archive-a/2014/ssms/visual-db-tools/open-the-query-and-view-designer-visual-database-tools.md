---
title: クエリおよびビュー デザイナーを開く (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- opening View Designer
- View Designer, opening
- Query Designer [SQL Server], opening
- opening Query Designer
ms.assetid: b473f258-d53c-41c0-9ad9-528a2ff141f4
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3a36a0a9f014759269517a5774167f84c19b0b18
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641383"
---
# <a name="open-the-query-and-view-designer-visual-database-tools"></a><span data-ttu-id="940e4-102">クエリおよびビュー デザイナーを開く (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="940e4-102">Open the Query and View Designer (Visual Database Tools)</span></span>
  <span data-ttu-id="940e4-103">ビューの定義を開いたり、クエリまたはビューの結果を表示したり、クエリを作成したり開いたりすると、クエリおよびビュー デザイナーが開きます。</span><span class="sxs-lookup"><span data-stu-id="940e4-103">The Query and View Designer opens when you open the definition of a view, show the results for a query or view, or create or open a query.</span></span> <span data-ttu-id="940e4-104">クエリおよびビュー デザイナーは、4 つの個別のペインで構成されています。</span><span class="sxs-lookup"><span data-stu-id="940e4-104">It consists of four separate panes:</span></span>  
  
-   <span data-ttu-id="940e4-105">ダイアグラム ペインには、データ接続で選択したテーブルまたはテーブル値オブジェクトが、グラフィカルに表示されます。</span><span class="sxs-lookup"><span data-stu-id="940e4-105">The Diagram pane presents a graphic display of the tables or table-valued objects you have selected from the data connection.</span></span> <span data-ttu-id="940e4-106">また、テーブル間の結合リレーションシップも示されます。</span><span class="sxs-lookup"><span data-stu-id="940e4-106">It also shows any join relationships among them.</span></span>  
  
-   <span data-ttu-id="940e4-107">抽出条件ペインでは、表示するデータ列、結果の順序、選択する行などのクエリ オプションを選択してスプレッドシート形式のグリッドに入力することにより、クエリ オプションを指定できます。</span><span class="sxs-lookup"><span data-stu-id="940e4-107">The Criteria pane allows you to specify query options - such as which data columns to display, how to order the results, and what rows to select - by entering your choices into a spreadsheet-like grid.</span></span>  
  
-   <span data-ttu-id="940e4-108">SQL ペインでは、任意の SQL ステートメントを作成できます。抽出条件ペインおよびダイアグラム ペインでも SQL ステートメントを作成できますが、どちらの場合も SQL ステートメントは SQL ペインに作成されます。</span><span class="sxs-lookup"><span data-stu-id="940e4-108">You can use the SQL pane to create your own SQL statement, or you can use the Criteria pane and Diagram pane to create the statement, in which case the SQL statements will be created in the SQL pane.</span></span> <span data-ttu-id="940e4-109">クエリを作成すると、SQL ペインは自動的に更新され、読みやすいように書式が変更されます。</span><span class="sxs-lookup"><span data-stu-id="940e4-109">As you build your query, the SQL pane automatically updates and reformats to be easily read.</span></span>  
  
-   <span data-ttu-id="940e4-110">結果ペインには、最後に実行された選択クエリの結果が表示されます。</span><span class="sxs-lookup"><span data-stu-id="940e4-110">The Results pane shows the results of the most recently executed Select query.</span></span> <span data-ttu-id="940e4-111">他の種類のクエリ結果は、メッセージ ボックスに表示されます。</span><span class="sxs-lookup"><span data-stu-id="940e4-111">(The results of other query types are displayed in message boxes.)</span></span>  
  
-   <span data-ttu-id="940e4-112">これらのペインはクエリおよびビューを操作する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="940e4-112">These panes are useful for working with both queries and views.</span></span>  
  
-   <span data-ttu-id="940e4-113">ビューまたはクエリを開くと、いくつかのペインまたはすべてのペインがビューまたはクエリと共に開きます。</span><span class="sxs-lookup"><span data-stu-id="940e4-113">When you open a view or query some or all of the panes open with it.</span></span> <span data-ttu-id="940e4-114">どのペインが開くかは、 **[オプション]** ダイアログ ボックスの設定、および接続しているデータベース管理システムの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="940e4-114">Which ones open depend on the settings in the **Options** dialog box and what database management system you're connected to.</span></span> <span data-ttu-id="940e4-115">既定の設定では、4 つすべてが開きます。</span><span class="sxs-lookup"><span data-stu-id="940e4-115">The default is that all four open.</span></span>  
  
### <a name="to-open-the-query-and-view-designer-for-a-view"></a><span data-ttu-id="940e4-116">クエリおよびビュー デザイナーでビューを開くには</span><span class="sxs-lookup"><span data-stu-id="940e4-116">To open the Query and View Designer for a view</span></span>  
  
1.  <span data-ttu-id="940e4-117">オブジェクト エクスプローラーで、開くビューを右クリックし、 **[デザイン]** または **[ビューを開く]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="940e4-117">In Object Explorer, right-click the view you want to open and click **Design** or **Open View**.</span></span>  
  
     <span data-ttu-id="940e4-118">**[デザイン]** を選択すると、 **[オプション]** ダイアログ ボックスで選択したオプションに従い、クエリおよびビュー デザイナーのペインが開きます。</span><span class="sxs-lookup"><span data-stu-id="940e4-118">If you chose **Design**, the Query and View Designer panes open as dictated by the options selected in the **Options** dialog box.</span></span> <span data-ttu-id="940e4-119">**[ビューを開く]** を選択すると、既定で結果ペインのみが開きます。</span><span class="sxs-lookup"><span data-stu-id="940e4-119">If you chose **Open View**, only the Results pane opens by default.</span></span>  
  
### <a name="to-open-the-query-and-view-designer-for-an-existing-query"></a><span data-ttu-id="940e4-120">クエリおよびビュー デザイナーで既存のクエリを開くには</span><span class="sxs-lookup"><span data-stu-id="940e4-120">To open the Query and View Designer for an existing query</span></span>  
  
1.  <span data-ttu-id="940e4-121">ソリューション エクスプローラーで、 **[クエリ]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="940e4-121">In Solution Explorer, expand the **Queries** folder.</span></span>  
  
2.  <span data-ttu-id="940e4-122">開くクエリをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="940e4-122">Double-click the query you want to open.</span></span>  
  
3.  <span data-ttu-id="940e4-123">クエリ ステートメントを強調表示し、強調表示された領域を右クリックして、 **[エディターでクエリをデザイン]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="940e4-123">Highlight the query statement(s), right-click the highlighted area and click **Design Query in Editor**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="940e4-124">参照</span><span class="sxs-lookup"><span data-stu-id="940e4-124">See Also</span></span>  
 <span data-ttu-id="940e4-125">[クエリおよびビューのデザイン方法に関するトピック &#40;Visual Database Tools&#41;](visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="940e4-125">[Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;](visual-database-tools.md) </span></span>  
 [<span data-ttu-id="940e4-126">クエリおよびビュー デザイナー ツール (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="940e4-126">Query and View Designer Tools &#40;Visual Database Tools&#41;</span></span>](query-and-view-designer-tools-visual-database-tools.md)  
  
  
