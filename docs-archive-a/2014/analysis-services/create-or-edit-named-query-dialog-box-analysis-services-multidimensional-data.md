---
title: '[名前付きクエリの作成] または [名前付きクエリの編集] ダイアログボックス (Analysis Services 多次元データ) |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dsvdesigner.createnamedquery.f1
helpviewer_keywords:
- Create Named Query dialog box
ms.assetid: 8e192ad6-a0b1-4e21-bb3f-087c93e62941
author: minewiskan
ms.author: owend
ms.openlocfilehash: cb255a44d2dde18e8d5e20343c7c5396f2e867d6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634736"
---
# <a name="create-or-edit-named-query-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="6f1cf-102">[名前付きクエリの作成] または [名前付きクエリの編集] ダイアログ ボックス (Analysis Services - 多次元データ)</span><span class="sxs-lookup"><span data-stu-id="6f1cf-102">Create or Edit Named Query Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="6f1cf-103">**の** [名前付きクエリの作成]/[名前付きクエリの編集] [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] ダイアログ ボックスを使用すると、 **データ ソース ビュー デザイナー**内で名前付きクエリを作成または編集できます。</span><span class="sxs-lookup"><span data-stu-id="6f1cf-103">Use the **Create/Edit Named Query** dialog box in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to create or edit a named query in **Data Source View Designer**.</span></span> <span data-ttu-id="6f1cf-104">名前付きクエリは、他の [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] オブジェクトの基となるテーブルとして扱うことができます。</span><span class="sxs-lookup"><span data-stu-id="6f1cf-104">A named query can be treated as a table, on which you can base other [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] objects.</span></span> <span data-ttu-id="6f1cf-105">**[名前付きクエリの作成]/[名前付きクエリの編集]** ダイアログ ボックスは、次の方法で表示します。</span><span class="sxs-lookup"><span data-stu-id="6f1cf-105">You can display the **Create/Edit Named Query** dialog box by:</span></span>  
  
-   <span data-ttu-id="6f1cf-106">**データ ソース ビュー デザイナー** の **[ツール バー]** ペインで、 **[新しい名前付きクエリ]** をクリックする。</span><span class="sxs-lookup"><span data-stu-id="6f1cf-106">Clicking **New Named Query** on the **Toolbar** pane of **Data Source View Designer**.</span></span>  
  
-   <span data-ttu-id="6f1cf-107">**データ ソース ビュー デザイナー** の **[ダイアグラム]** ペインを右クリックして **[新しい名前付きクエリ]** をクリックする。</span><span class="sxs-lookup"><span data-stu-id="6f1cf-107">Right-clicking the **Diagram** pane of **Data Source View Designer** and selecting **New Named Query**.</span></span>  
  
-   <span data-ttu-id="6f1cf-108">**データ ソース ビュー デザイナー** の **[ダイアグラム]** ペインまたは **[テーブル]** ペインで名前付きクエリの名前を右クリックして、 **[名前付きクエリの編集]** をクリックする。</span><span class="sxs-lookup"><span data-stu-id="6f1cf-108">Right-clicking the name of a named query in the **Diagram** or **Tables** pane of **Data Source View Designer** and selecting **Edit Named Query**.</span></span>  
  
 <span data-ttu-id="6f1cf-109">入力するクエリは、基になるプロバイダーで有効なクエリ コマンドである必要があります。</span><span class="sxs-lookup"><span data-stu-id="6f1cf-109">The query entered must be a valid query command for the underlying provider.</span></span> <span data-ttu-id="6f1cf-110">クエリは検証用に基になるプロバイダーが指定された状態で用意され、返される列を識別できるようになっています。</span><span class="sxs-lookup"><span data-stu-id="6f1cf-110">The query is prepared with the underlying provider for validation, and to identify the columns returned.</span></span> <span data-ttu-id="6f1cf-111">ダイアログ ボックスでは、次の 2 つのビューを表示できます。</span><span class="sxs-lookup"><span data-stu-id="6f1cf-111">The dialog box can present two views:</span></span>  
  
-   <span data-ttu-id="6f1cf-112">Visual Database Tools (VDT) クエリ ビルダー</span><span class="sxs-lookup"><span data-stu-id="6f1cf-112">Visual Database Tools (VDT) Query Builder</span></span>  
  
     <span data-ttu-id="6f1cf-113">すべてのユーザー向けです。VDT クエリ ビルダーには、SQL クエリをビジュアルに構築しテストするためのユーザー インターフェイス ツールが備えられています。</span><span class="sxs-lookup"><span data-stu-id="6f1cf-113">For all users, the VDT Query Builder view provides a set of user interface tools for visually constructing and testing a SQL query.</span></span>  
  
-   <span data-ttu-id="6f1cf-114">汎用クエリ ビルダー</span><span class="sxs-lookup"><span data-stu-id="6f1cf-114">Generic Query Builder</span></span>  
  
     <span data-ttu-id="6f1cf-115">上級ユーザー向けです。汎用クエリ ビルダーには、SQL クエリを構築しテストするための、より単純で直接的なユーザー インターフェイスが備えられています。</span><span class="sxs-lookup"><span data-stu-id="6f1cf-115">For advanced users, the Generic Query Builder view provides a simpler, more direct user interface for constructing and testing a SQL query.</span></span>  
  
## <a name="options"></a><span data-ttu-id="6f1cf-116">Options</span><span class="sxs-lookup"><span data-stu-id="6f1cf-116">Options</span></span>  
 <span data-ttu-id="6f1cf-117">**名前**</span><span class="sxs-lookup"><span data-stu-id="6f1cf-117">**Name**</span></span>  
 <span data-ttu-id="6f1cf-118">クエリの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="6f1cf-118">Type the name of the query.</span></span>  
  
 <span data-ttu-id="6f1cf-119">**説明**</span><span class="sxs-lookup"><span data-stu-id="6f1cf-119">**Description**</span></span>  
 <span data-ttu-id="6f1cf-120">クエリのな説明をオプションで入力します。</span><span class="sxs-lookup"><span data-stu-id="6f1cf-120">Type the optional description of the query.</span></span>  
  
 <span data-ttu-id="6f1cf-121">**データ ソース**</span><span class="sxs-lookup"><span data-stu-id="6f1cf-121">**Data Source**</span></span>  
 <span data-ttu-id="6f1cf-122">クエリのデータ ソースを指定します。</span><span class="sxs-lookup"><span data-stu-id="6f1cf-122">Specifies the data source for the query.</span></span>  
  
 <span data-ttu-id="6f1cf-123">**[クエリ定義]**</span><span class="sxs-lookup"><span data-stu-id="6f1cf-123">**Query definition**</span></span>  
 <span data-ttu-id="6f1cf-124">クエリ定義では、選択したビューに応じて、クエリの定義とテストを行うためのツール バーとペインを表示します。</span><span class="sxs-lookup"><span data-stu-id="6f1cf-124">The query definition provides a toolbar and panes in which to define and test the query, depending on the selected view.</span></span>  
  
 <span data-ttu-id="6f1cf-125">**ツール バー**</span><span class="sxs-lookup"><span data-stu-id="6f1cf-125">**Toolbar**</span></span>  
 <span data-ttu-id="6f1cf-126">ツール バーは、データセットの管理、表示するペインの選択、さまざまなクエリ機能の制御に使用します。</span><span class="sxs-lookup"><span data-stu-id="6f1cf-126">Use the toolbar to manage datasets, select panes to display, and control various query functions.</span></span>  
  
|<span data-ttu-id="6f1cf-127">値</span><span class="sxs-lookup"><span data-stu-id="6f1cf-127">Value</span></span>|<span data-ttu-id="6f1cf-128">説明</span><span class="sxs-lookup"><span data-stu-id="6f1cf-128">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6f1cf-129">**[汎用クエリ ビルダーに切り替えます]**</span><span class="sxs-lookup"><span data-stu-id="6f1cf-129">**Switch to Generic Query Builder**</span></span>|<span data-ttu-id="6f1cf-130">選択すると、汎用クエリ ビルダーのビューで使用されるオプションのみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="6f1cf-130">Select to display only the options available to the Generic Query Builder view.</span></span> <span data-ttu-id="6f1cf-131">次のオプションのみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="6f1cf-131">Only the following options are displayed:</span></span><br /><span data-ttu-id="6f1cf-132">**SQL ペイン**</span><span class="sxs-lookup"><span data-stu-id="6f1cf-132">**SQL pane**</span></span><br /><span data-ttu-id="6f1cf-133">**結果ペイン**</span><span class="sxs-lookup"><span data-stu-id="6f1cf-133">**Result pane**</span></span><br /><span data-ttu-id="6f1cf-134">**[ツール バー]**。 **[VDT クエリ ビルダーに切り替えます]** と **[実行]**</span><span class="sxs-lookup"><span data-stu-id="6f1cf-134">**Toolbar**, containing only **Switch to VDT Query Builder** and **Run**</span></span><br /><br /> <br /><br /> <span data-ttu-id="6f1cf-135">注: このオプションは、**[VDT クエリ ビルダーに切り替えます]** が選択されている場合にのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="6f1cf-135">Note: This option is displayed only if **Switch to VDT Query Builder** is selected.</span></span>|  
|<span data-ttu-id="6f1cf-136">**[VDT クエリ ビルダーに切り替えます]**</span><span class="sxs-lookup"><span data-stu-id="6f1cf-136">**Switch to VDT Query Builder**</span></span>|<span data-ttu-id="6f1cf-137">選択すると、Visual Database Tools (VDT) クエリ ビルダーのビューで使用できるオプションがすべて表示されます。</span><span class="sxs-lookup"><span data-stu-id="6f1cf-137">Select to display all of the options available to the Visual Database Tools (VDT) Query Builder view.</span></span><br /><br /> <span data-ttu-id="6f1cf-138">注: このオプションは、 **[汎用クエリ ビルダーに切り替えます]** が選択されている場合にのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="6f1cf-138">Note: This option is displayed only if **Switch to Generic Query Builder** is selected.</span></span>|  
|<span data-ttu-id="6f1cf-139">**[ダイアグラム ペインの表示/非表示]**</span><span class="sxs-lookup"><span data-stu-id="6f1cf-139">**Show/Hide Diagram Pane**</span></span>|<span data-ttu-id="6f1cf-140">**ダイアグラムペイン**の表示と非表示を切り替えます。</span><span class="sxs-lookup"><span data-stu-id="6f1cf-140">Shows or hides the **Diagram pane**.</span></span><br /><br /> <span data-ttu-id="6f1cf-141">**メモ**このオプションは **、[VDT クエリビルダーに切り替え**] が選択されている場合にのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="6f1cf-141">**Note** This option is displayed only if **Switch to VDT Query Builder** is selected.</span></span>|  
|<span data-ttu-id="6f1cf-142">**[グリッド ペインの表示/非表示]**</span><span class="sxs-lookup"><span data-stu-id="6f1cf-142">**Show/Hide Grid Pane**</span></span>|<span data-ttu-id="6f1cf-143">[**グリッド] ペイン**の表示と非表示を切り替えます。</span><span class="sxs-lookup"><span data-stu-id="6f1cf-143">Shows or hides the **Grid pane**.</span></span><br /><br /> <span data-ttu-id="6f1cf-144">注: このオプションは、**[VDT クエリ ビルダーに切り替えます]** が選択されている場合にのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="6f1cf-144">Note: This option is displayed only if **Switch to VDT Query Builder** is selected.</span></span>|  
|<span data-ttu-id="6f1cf-145">**[SQL ペインの表示/非表示]**</span><span class="sxs-lookup"><span data-stu-id="6f1cf-145">**Show/Hide SQL Pane**</span></span>|<span data-ttu-id="6f1cf-146">**[SQL]** ペインの表示と非表示を切り替えます。</span><span class="sxs-lookup"><span data-stu-id="6f1cf-146">Shows or hides the **SQL pane**.</span></span><br /><br /> <span data-ttu-id="6f1cf-147">注: このオプションは、**[VDT クエリ ビルダーに切り替えます]** が選択されている場合にのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="6f1cf-147">Note: This option is displayed only if **Switch to VDT Query Builder** is selected.</span></span>|  
|<span data-ttu-id="6f1cf-148">**[結果ペインの表示/非表示]**</span><span class="sxs-lookup"><span data-stu-id="6f1cf-148">**Show/Hide Result Pane**</span></span>|<span data-ttu-id="6f1cf-149">**[結果]** ペインの表示と非表示を切り替えます。</span><span class="sxs-lookup"><span data-stu-id="6f1cf-149">Shows or hides the **Result pane**.</span></span><br /><br /> <span data-ttu-id="6f1cf-150">注: このオプションは、**[VDT クエリ ビルダーに切り替えます]** が選択されている場合にのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="6f1cf-150">Note: This option is displayed only if **Switch to VDT Query Builder** is selected.</span></span>|  
|<span data-ttu-id="6f1cf-151">**実行**</span><span class="sxs-lookup"><span data-stu-id="6f1cf-151">**Run**</span></span>|<span data-ttu-id="6f1cf-152">クエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="6f1cf-152">Runs the query.</span></span> <span data-ttu-id="6f1cf-153">結果は **結果ペイン**に表示されます。</span><span class="sxs-lookup"><span data-stu-id="6f1cf-153">Results are displayed in the **Result pane**.</span></span>|  
|<span data-ttu-id="6f1cf-154">**[SQL の確認]**</span><span class="sxs-lookup"><span data-stu-id="6f1cf-154">**Verify SQL**</span></span>|<span data-ttu-id="6f1cf-155">クエリの SQL ステートメントを確認します。</span><span class="sxs-lookup"><span data-stu-id="6f1cf-155">Verifies the SQL statement in the query.</span></span><br /><br /> <span data-ttu-id="6f1cf-156">注: このオプションは、**[VDT クエリ ビルダーに切り替えます]** が選択されている場合にのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="6f1cf-156">Note: This option is displayed only if **Switch to VDT Query Builder** is selected.</span></span>|  
|<span data-ttu-id="6f1cf-157">**昇順で並べ替え**</span><span class="sxs-lookup"><span data-stu-id="6f1cf-157">**Sort Ascending**</span></span>|<span data-ttu-id="6f1cf-158">**グリッド ペイン**で選択した列の出力行を昇順で並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="6f1cf-158">Sorts output rows on the selected column in the **Grid pane**, in ascending order.</span></span><br /><br /> <span data-ttu-id="6f1cf-159">注: このオプションは、**[VDT クエリ ビルダーに切り替えます]** が選択されている場合にのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="6f1cf-159">Note: This option is displayed only if **Switch to VDT Query Builder** is selected.</span></span>|  
|<span data-ttu-id="6f1cf-160">**降順で並べ替え**</span><span class="sxs-lookup"><span data-stu-id="6f1cf-160">**Sort Descending**</span></span>|<span data-ttu-id="6f1cf-161">**グリッド ペイン**で選択した列の出力行を降順で並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="6f1cf-161">Sorts output rows on the selected column in the **Grid pane**, in descending order.</span></span><br /><br /> <span data-ttu-id="6f1cf-162">注: このオプションは、**[VDT クエリ ビルダーに切り替えます]** が選択されている場合にのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="6f1cf-162">Note: This option is displayed only if **Switch to VDT Query Builder** is selected.</span></span>|  
|<span data-ttu-id="6f1cf-163">**フィルターの削除**</span><span class="sxs-lookup"><span data-stu-id="6f1cf-163">**Remove Filter**</span></span>|<span data-ttu-id="6f1cf-164">**グリッド ペイン**で選択されている行に並べ替え条件を適用できる場合、その条件を削除します。</span><span class="sxs-lookup"><span data-stu-id="6f1cf-164">Removes sort criteria, if applicable, for the selected row in the **Grid pane**.</span></span><br /><br /> <span data-ttu-id="6f1cf-165">注: このオプションは、**[VDT クエリ ビルダーに切り替えます]** が選択されている場合にのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="6f1cf-165">Note: This option is displayed only if **Switch to VDT Query Builder** is selected.</span></span>|  
|<span data-ttu-id="6f1cf-166">**[Group By の使用]**</span><span class="sxs-lookup"><span data-stu-id="6f1cf-166">**Use Group By**</span></span>|<span data-ttu-id="6f1cf-167">クエリにグループ化機能を追加します。</span><span class="sxs-lookup"><span data-stu-id="6f1cf-167">Adds grouping functionality to the query.</span></span><br /><br /> <span data-ttu-id="6f1cf-168">注: このオプションは、**[VDT クエリ ビルダーに切り替えます]** が選択されている場合にのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="6f1cf-168">Note: This option is displayed only if **Switch to VDT Query Builder** is selected.</span></span>|  
|<span data-ttu-id="6f1cf-169">**[テーブルの追加]**</span><span class="sxs-lookup"><span data-stu-id="6f1cf-169">**Add Table**</span></span>|<span data-ttu-id="6f1cf-170">**[テーブルの追加]** ダイアログ ボックスを表示し、クエリに新しいテーブルやビューを追加できます。</span><span class="sxs-lookup"><span data-stu-id="6f1cf-170">Displays the **Add Table** dialog box to add a new table or view to the query.</span></span> <span data-ttu-id="6f1cf-171">**[テーブルの追加]** ダイアログ ボックスの詳細については、「[[テーブルの追加] ダイアログ ボックス &#40;Analysis Services - 多次元データ&#41;](add-table-dialog-box-analysis-services-multidimensional-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6f1cf-171">For more information about the **Add Table** dialog box, see [Add Table Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](add-table-dialog-box-analysis-services-multidimensional-data.md).</span></span><br /><br /> <span data-ttu-id="6f1cf-172">注: このオプションは、**[VDT クエリ ビルダーに切り替えます]** が選択されている場合にのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="6f1cf-172">Note: This option is displayed only if **Switch to VDT Query Builder** is selected.</span></span>|  
  
 <span data-ttu-id="6f1cf-173">**ダイアグラムペイン**</span><span class="sxs-lookup"><span data-stu-id="6f1cf-173">**Diagram pane**</span></span>  
 <span data-ttu-id="6f1cf-174">クエリによって参照されるオブジェクトをダイアグラムとして表示します。</span><span class="sxs-lookup"><span data-stu-id="6f1cf-174">Displays the objects referenced by the query as a diagram.</span></span> <span data-ttu-id="6f1cf-175">このダイアグラムには、クエリに含まれるテーブルと、その結合状態が表示されます。</span><span class="sxs-lookup"><span data-stu-id="6f1cf-175">The diagram shows the tables included in the query, and how they are joined.</span></span> <span data-ttu-id="6f1cf-176">テーブルの列の横にあるチェック ボックスをオンにすると、クエリの出力にその列が追加されます。オフにすると、削除されます。</span><span class="sxs-lookup"><span data-stu-id="6f1cf-176">Select or clear the check box next to a column in a table to add or remove it from the query output.</span></span>  
  
 <span data-ttu-id="6f1cf-177">テーブルをクエリに追加すると、ダイアログ ボックスでは、テーブルのキーを基にしてテーブル間の結合が行われます。</span><span class="sxs-lookup"><span data-stu-id="6f1cf-177">When you add tables to the query, the dialog box creates joins between tables based on the keys in the table.</span></span> <span data-ttu-id="6f1cf-178">結合を追加するには、あるテーブルのフィールドを別のテーブルのフィールドにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="6f1cf-178">To add a join, drag a field from one table onto a field in another table.</span></span> <span data-ttu-id="6f1cf-179">結合を管理するには、結合を右クリックします。</span><span class="sxs-lookup"><span data-stu-id="6f1cf-179">To manage a join, right-click the join.</span></span>  
  
 <span data-ttu-id="6f1cf-180">**ダイアグラム ペイン** を右クリックすると、テーブルの追加や削除、すべてのテーブルの選択、ペインの表示と非表示の切り替えができます。</span><span class="sxs-lookup"><span data-stu-id="6f1cf-180">Right-click the **Diagram pane** to add or remove tables, select all the tables, and show or hide panes.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6f1cf-181">**ダイアグラム ペイン**、 **グリッド ペイン**、および **SQL ペイン** の内容は同期しているため、1 つのペインで加えた変更は他の 2 つのペインにも反映されます。</span><span class="sxs-lookup"><span data-stu-id="6f1cf-181">The contents of the **Diagram pane**, **Grid pane**, and **SQL pane** are synchronized, so that changes in one pane are reflected in the other two panes.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="6f1cf-182">クエリの種類の変更は、ダイアログ ボックスではサポートされません。</span><span class="sxs-lookup"><span data-stu-id="6f1cf-182">Changing query types is not supported by the dialog box.</span></span>  
  
 <span data-ttu-id="6f1cf-183">**グリッド ペイン**</span><span class="sxs-lookup"><span data-stu-id="6f1cf-183">**Grid pane**</span></span>  
 <span data-ttu-id="6f1cf-184">クエリから参照されるオブジェクトをグリッドに表示します。</span><span class="sxs-lookup"><span data-stu-id="6f1cf-184">Displays the objects referenced by the query in a grid.</span></span> <span data-ttu-id="6f1cf-185">このペインを使用して、クエリに列を追加したり、列を削除したりできます。また、各列の設定の変更も変更できます。</span><span class="sxs-lookup"><span data-stu-id="6f1cf-185">You can use this pane to add and remove columns to the query and change the settings for each column.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6f1cf-186">**ダイアグラム ペイン**、 **グリッド ペイン**、および **SQL ペイン** の内容は同期しているため、1 つのペインで加えた変更は他の 2 つのペインにも反映されます。</span><span class="sxs-lookup"><span data-stu-id="6f1cf-186">The contents of the **Diagram pane**, **Grid pane**, and **SQL pane** are synchronized, so that changes in one pane are reflected in the other two panes.</span></span>  
  
 <span data-ttu-id="6f1cf-187">**SQL ペイン**</span><span class="sxs-lookup"><span data-stu-id="6f1cf-187">**SQL pane**</span></span>  
 <span data-ttu-id="6f1cf-188">クエリを SQL ステートメントとして表示します。</span><span class="sxs-lookup"><span data-stu-id="6f1cf-188">Displays the query as a SQL statement.</span></span> <span data-ttu-id="6f1cf-189">入力することで、クエリの SQL ステートメントを変更できます。</span><span class="sxs-lookup"><span data-stu-id="6f1cf-189">Type to change the SQL statement for the query.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6f1cf-190">**ダイアグラム ペイン**、 **グリッド ペイン**、および **SQL ペイン** の内容は同期しているため、1 つのペインで加えた変更は他の 2 つのペインにも反映されます。</span><span class="sxs-lookup"><span data-stu-id="6f1cf-190">The contents of the **Diagram pane**, **Grid pane**, and **SQL pane** are synchronized, so that changes in one pane are reflected in the other two panes.</span></span>  
  
 <span data-ttu-id="6f1cf-191">**結果ペイン**</span><span class="sxs-lookup"><span data-stu-id="6f1cf-191">**Result pane**</span></span>  
 <span data-ttu-id="6f1cf-192">**ツール バー** ペインで **[実行]** をクリックしたときに、クエリの結果を表示します。</span><span class="sxs-lookup"><span data-stu-id="6f1cf-192">Displays the results of the query when you click **Run** on the **Toolbar** pane.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f1cf-193">参照</span><span class="sxs-lookup"><span data-stu-id="6f1cf-193">See Also</span></span>  
 <span data-ttu-id="6f1cf-194">[多次元データ &#40;Analysis Services のデザイナーとダイアログボックス&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="6f1cf-194">[Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="6f1cf-195">データ ソース ビューでの名前付きクエリの定義 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="6f1cf-195">Define Named Queries in a Data Source View &#40;Analysis Services&#41;</span></span>](multidimensional-models/define-named-queries-in-a-data-source-view-analysis-services.md)  
  
  
