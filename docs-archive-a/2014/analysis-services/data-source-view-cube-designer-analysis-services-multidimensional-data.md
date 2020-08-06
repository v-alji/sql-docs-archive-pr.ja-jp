---
title: '[データソースビュー] (キューブデザイナーの [キューブ構造] タブ) (Analysis Services-多次元データ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.cubebuilder.datasourcepane.f1
ms.assetid: 1e39c910-5c10-4624-be27-ca02a461b46b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8c949eaa17ec9d8bf585a5d595f31779382c41ed
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716995"
---
# <a name="data-source-view-cube-structure-tab-cube-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="5f9bf-102">[データ ソース ビュー] (キューブ デザイナーの [キューブ構造] タブ) (Analysis Services - 多次元データ)</span><span class="sxs-lookup"><span data-stu-id="5f9bf-102">Data Source View (Cube Structure Tab, Cube Designer) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="5f9bf-103">**[データ ソース ビュー]** ペインを使用すると、選択されたキューブに関連付けられているデータ ソース ビューのテーブルおよび列を表示できます。</span><span class="sxs-lookup"><span data-stu-id="5f9bf-103">Use the **Data Source View** pane to view tables and columns from the data source view associated with the selected cube.</span></span> <span data-ttu-id="5f9bf-104">このペインを使用すると、 **[データ ソース ビュー]** ペインから **[メジャー]** ペインに列をドラッグすることで、メジャー グループおよびメジャーを作成できます。</span><span class="sxs-lookup"><span data-stu-id="5f9bf-104">This pane is used to create measure groups and measures by dragging columns from the **Data Source View** pane to the **Measures** pane.</span></span>  
  
## <a name="options"></a><span data-ttu-id="5f9bf-105">Options</span><span class="sxs-lookup"><span data-stu-id="5f9bf-105">Options</span></span>  
 <span data-ttu-id="5f9bf-106">**データソースビュー**</span><span class="sxs-lookup"><span data-stu-id="5f9bf-106">**Data Source View**</span></span>  
 <span data-ttu-id="5f9bf-107">選択されたキューブに関連付けられているデータ ソース ビューを表示します。</span><span class="sxs-lookup"><span data-stu-id="5f9bf-107">Displays the data source view associated with the selected cube.</span></span>  
  
 <span data-ttu-id="5f9bf-108">**(表示領域の移動)**</span><span class="sxs-lookup"><span data-stu-id="5f9bf-108">**(Move viewpoint)**</span></span>  
 <span data-ttu-id="5f9bf-109">ペインの右下隅のスクロール バーの間をクリックすると、表示する **[データ ソース ビュー]** ペインの領域を選択します。</span><span class="sxs-lookup"><span data-stu-id="5f9bf-109">Click the lower right corner of the pane, between the scrollbars, to select an area of the **Data Source View** pane to view.</span></span>  
  
## <a name="diagram-context-menu"></a><span data-ttu-id="5f9bf-110">ダイアグラムのショートカット メニュー</span><span class="sxs-lookup"><span data-stu-id="5f9bf-110">Diagram Context Menu</span></span>  
 <span data-ttu-id="5f9bf-111">**[データ ソース ビュー]** ペインのダイアグラムの背景を右クリックすると表示されるショートカット メニューでは、次のオプションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="5f9bf-111">The following options are available in the context menu displayed by right-clicking the diagram background of the **Data Source View** pane:</span></span>  
  
 <span data-ttu-id="5f9bf-112">**SHOW TABLES**</span><span class="sxs-lookup"><span data-stu-id="5f9bf-112">**Show Tables**</span></span>  
 <span data-ttu-id="5f9bf-113">**[テーブルの表示]** ダイアログ ボックスを表示します。</span><span class="sxs-lookup"><span data-stu-id="5f9bf-113">Displays the **Show Table** dialog box.</span></span> <span data-ttu-id="5f9bf-114">**[テーブルの表示]** ダイアログ ボックスの詳細については、「[[テーブルの表示] ダイアログ ボックス (Analysis Services - 多次元データ)](show-table-dialog-box-analysis-services-multidimensional-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5f9bf-114">For more information about the **Show Table** dialog box, see [Show Table Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](show-table-dialog-box-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="5f9bf-115">**[すべてのテーブルを表示]**</span><span class="sxs-lookup"><span data-stu-id="5f9bf-115">**Show All Tables**</span></span>  
 <span data-ttu-id="5f9bf-116">キューブに関連付けられているデータ ソース ビューに含まれるすべてのテーブルをペインに表示します。</span><span class="sxs-lookup"><span data-stu-id="5f9bf-116">Displays in the pane all tables included in the data source view associated with the cube.</span></span>  
  
 <span data-ttu-id="5f9bf-117">**[使用されたテーブルのみを表示]**</span><span class="sxs-lookup"><span data-stu-id="5f9bf-117">**Show Only Used Tables**</span></span>  
 <span data-ttu-id="5f9bf-118">関連付けられているデータ ソース ビューのキューブによって使用されているテーブルだけをペインに表示します。</span><span class="sxs-lookup"><span data-stu-id="5f9bf-118">Displays in the pane only those tables used by the cube from the associated data source view.</span></span>  
  
 <span data-ttu-id="5f9bf-119">**フレンドリ名の表示**</span><span class="sxs-lookup"><span data-stu-id="5f9bf-119">**Show Friendly Names**</span></span>  
 <span data-ttu-id="5f9bf-120">選択すると、オブジェクトの表示名がペインに表示されます。</span><span class="sxs-lookup"><span data-stu-id="5f9bf-120">Selects to show friendly names for the objects in the pane.</span></span>  
  
 <span data-ttu-id="5f9bf-121">**[すべて選択]**</span><span class="sxs-lookup"><span data-stu-id="5f9bf-121">**Select All**</span></span>  
 <span data-ttu-id="5f9bf-122">ペイン内のすべてのオブジェクトが選択されます。</span><span class="sxs-lookup"><span data-stu-id="5f9bf-122">Selects all of the objects in the pane.</span></span>  
  
 <span data-ttu-id="5f9bf-123">**[テーブルの検索]**</span><span class="sxs-lookup"><span data-stu-id="5f9bf-123">**Find Table**</span></span>  
 <span data-ttu-id="5f9bf-124">**[テーブルの検索]** ダイアログ ボックスを表示します。</span><span class="sxs-lookup"><span data-stu-id="5f9bf-124">Displays the **Find Table** dialog box.</span></span> <span data-ttu-id="5f9bf-125">**[テーブルの検索]** ダイアログ ボックスの詳細については、「[[テーブルの検索] ダイアログ ボックス (Analysis Services - 多次元データ)](find-table-dialog-box-analysis-services-multidimensional-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5f9bf-125">For more information about the **Find Table** dialog box, see [Find Table Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](find-table-dialog-box-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="5f9bf-126">**[テーブルの整列]**</span><span class="sxs-lookup"><span data-stu-id="5f9bf-126">**Arrange Tables**</span></span>  
 <span data-ttu-id="5f9bf-127">**[斜線レイアウトに切り替え]** または **[四角形レイアウトに切り替え]** を選択して指定したレイアウトに従って、ペイン内のオブジェクトを並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="5f9bf-127">Arranges the objects in the pane according to the layout specified by selecting either **Switch to Diagonal Layout** or **Switch to Rectangular Layout**.</span></span>  
  
 <span data-ttu-id="5f9bf-128">**[斜線レイアウトに切り替え]**</span><span class="sxs-lookup"><span data-stu-id="5f9bf-128">**Switch to Diagonal Layout**</span></span>  
 <span data-ttu-id="5f9bf-129">オブジェクトを斜線パターンで整列できます。</span><span class="sxs-lookup"><span data-stu-id="5f9bf-129">Select to arrange objects in a diagonal pattern.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5f9bf-130"> このオプションは、 **[四角形レイアウトに切り替え]** が選択されている場合にのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="5f9bf-130">This option is displayed only if **Switch to Rectangular Layout** is selected.</span></span>  
  
 <span data-ttu-id="5f9bf-131">**[四角形レイアウトに切り替え]**</span><span class="sxs-lookup"><span data-stu-id="5f9bf-131">**Switch to Rectangular Layout**</span></span>  
 <span data-ttu-id="5f9bf-132">オブジェクトを四角形パターンで整列できます。</span><span class="sxs-lookup"><span data-stu-id="5f9bf-132">Select to arrange objects in a rectangular pattern.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5f9bf-133"> このオプションは、 **[斜線レイアウトに切り替え]** が選択されている場合にのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="5f9bf-133">This option is displayed only if **Switch to Diagonal Layout** is selected.</span></span>  
  
 <span data-ttu-id="5f9bf-134">**[データ ソース ビューの編集]**</span><span class="sxs-lookup"><span data-stu-id="5f9bf-134">**Edit Data Source View**</span></span>  
 <span data-ttu-id="5f9bf-135">オブジェクトに関連付けられているデータ ソース ビューのデータ ソース ビュー デザイナーを表示します。</span><span class="sxs-lookup"><span data-stu-id="5f9bf-135">Displays Data Source View Designer for the data source view associated with the object.</span></span> <span data-ttu-id="5f9bf-136">データ ソース ビュー デザイナーの詳細については、「[データ ソース ビュー デザイナー &#40;Analysis Services - 多次元データ&#41;](data-source-view-designer-analysis-services-multidimensional-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5f9bf-136">For more information about Data Source View Designer, see [Data Source View Designer &#40;Analysis Services - Multidimensional Data&#41;](data-source-view-designer-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="5f9bf-137">**[データ ソース ビューを表示]**</span><span class="sxs-lookup"><span data-stu-id="5f9bf-137">**Show Data Source View In**</span></span>  
 <span data-ttu-id="5f9bf-138">**[データ ソース ビュー]** ペインの表示モードとして、次のオプションのいずれかのオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="5f9bf-138">Select one of the following options to toggle between viewing the **Data Source View** pane in the following modes:</span></span>  
  
-   <span data-ttu-id="5f9bf-139">ダイアグラム</span><span class="sxs-lookup"><span data-stu-id="5f9bf-139">Diagram</span></span>  
  
     <span data-ttu-id="5f9bf-140">現在のキューブに関連付けられているテーブルおよび列のダイアグラムを表示します。</span><span class="sxs-lookup"><span data-stu-id="5f9bf-140">Displays a diagram of the tables and columns associated with the current cube.</span></span>  
  
-   <span data-ttu-id="5f9bf-141">ツリー</span><span class="sxs-lookup"><span data-stu-id="5f9bf-141">Tree</span></span>  
  
     <span data-ttu-id="5f9bf-142">現在のキューブに関連付けられているテーブルおよび列を含むツリー ビューを表示します。</span><span class="sxs-lookup"><span data-stu-id="5f9bf-142">Displays a tree view containing the tables and columns associated with the current cube.</span></span>  
  
 <span data-ttu-id="5f9bf-143">**[ダイアグラムのコピー元]**</span><span class="sxs-lookup"><span data-stu-id="5f9bf-143">**Copy Diagram From**</span></span>  
 <span data-ttu-id="5f9bf-144">**[データ ソース ビュー]** ペインに表示する、キューブに関連付けられたデータ ソース ビューに含まれているいずれかのダイアグラムを選択します。</span><span class="sxs-lookup"><span data-stu-id="5f9bf-144">Select one of the diagrams included in the data source view associated with the cube to display it in the **Data Source View** pane.</span></span>  
  
 <span data-ttu-id="5f9bf-145">**Zoom**</span><span class="sxs-lookup"><span data-stu-id="5f9bf-145">**Zoom**</span></span>  
 <span data-ttu-id="5f9bf-146">利用可能なズーム オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="5f9bf-146">Select an available zoom option.</span></span>  
  
 <span data-ttu-id="5f9bf-147">**プロパティ**</span><span class="sxs-lookup"><span data-stu-id="5f9bf-147">**Properties**</span></span>  
 <span data-ttu-id="5f9bf-148">キューブに関連付けられたデータ ソース ビューのために、 **の** [プロパティ] [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] ウィンドウを表示します。</span><span class="sxs-lookup"><span data-stu-id="5f9bf-148">Displays the **Properties** window in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] for the data source view associated with the cube.</span></span>  
  
## <a name="table-context-menu"></a><span data-ttu-id="5f9bf-149">テーブルのショートカット メニュー</span><span class="sxs-lookup"><span data-stu-id="5f9bf-149">Table Context Menu</span></span>  
 <span data-ttu-id="5f9bf-150">**[データ ソース ビュー]** ペインのテーブルまたはビューの名前を右クリックすると表示されるショートカット メニューでは、次のオプションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="5f9bf-150">The following options are available in the context menu displayed by right-clicking the name of a table or view in the **Data Source View** pane:</span></span>  
  
 <span data-ttu-id="5f9bf-151">**[関連テーブルの表示]**</span><span class="sxs-lookup"><span data-stu-id="5f9bf-151">**Show Related Tables**</span></span>  
 <span data-ttu-id="5f9bf-152">データ ソース ビューで選択されたテーブルに関連するテーブルをペインに表示します。</span><span class="sxs-lookup"><span data-stu-id="5f9bf-152">Displays in the pane the tables related to the selected table in the data source view.</span></span>  
  
 <span data-ttu-id="5f9bf-153">**[テーブルの非表示]**</span><span class="sxs-lookup"><span data-stu-id="5f9bf-153">**Hide Table**</span></span>  
 <span data-ttu-id="5f9bf-154">ペインからテーブルを削除します。</span><span class="sxs-lookup"><span data-stu-id="5f9bf-154">Removes the table from the pane.</span></span>  
  
 <span data-ttu-id="5f9bf-155">**データの探索**</span><span class="sxs-lookup"><span data-stu-id="5f9bf-155">**Explore Data**</span></span>  
 <span data-ttu-id="5f9bf-156">選択されているテーブルの **[データの探索]** ダイアログ ボックスを表示します。</span><span class="sxs-lookup"><span data-stu-id="5f9bf-156">Display the **Explore Data** dialog box for the selected table.</span></span>  
  
 <span data-ttu-id="5f9bf-157">**[データ ソース ビューの編集]**</span><span class="sxs-lookup"><span data-stu-id="5f9bf-157">**Edit Data Source View**</span></span>  
 <span data-ttu-id="5f9bf-158">選択したテーブルを含むデータ ソース ビューのデータ ソース ビュー デザイナーを表示します。</span><span class="sxs-lookup"><span data-stu-id="5f9bf-158">Displays Data Source View Designer for the data source view that contains the selected table.</span></span> <span data-ttu-id="5f9bf-159">データ ソース ビュー デザイナーの詳細については、「[データ ソース ビュー デザイナー &#40;Analysis Services - 多次元データ&#41;](data-source-view-designer-analysis-services-multidimensional-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5f9bf-159">For more information about Data Source View Designer, see [Data Source View Designer &#40;Analysis Services - Multidimensional Data&#41;](data-source-view-designer-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="5f9bf-160">**[テーブルから新しいメジャー グループを作成]**</span><span class="sxs-lookup"><span data-stu-id="5f9bf-160">**New Measure Group from Table**</span></span>  
 <span data-ttu-id="5f9bf-161">選択されているテーブルに基づいて、 **[メジャー]** ペインに新しいメジャー グループを定義します。</span><span class="sxs-lookup"><span data-stu-id="5f9bf-161">Defines a new measure group in the **Measures** pane based on the selected table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5f9bf-162">このオプションは、テーブルがまだ **[メジャー]** ペインのメジャー グループによって参照されていない場合にだけ有効になります。</span><span class="sxs-lookup"><span data-stu-id="5f9bf-162">This option is enabled only if the table is not yet referenced by a measure group in the **Measures** pane.</span></span>  
  
 <span data-ttu-id="5f9bf-163">**プロパティ**</span><span class="sxs-lookup"><span data-stu-id="5f9bf-163">**Properties**</span></span>  
 <span data-ttu-id="5f9bf-164">**で選択されているテーブルの** [プロパティ] [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] ウィンドウを表示します。</span><span class="sxs-lookup"><span data-stu-id="5f9bf-164">Displays the **Properties** window in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] for the selected table.</span></span>  
  
## <a name="column-context-menu"></a><span data-ttu-id="5f9bf-165">列のショートカット メニュー</span><span class="sxs-lookup"><span data-stu-id="5f9bf-165">Column Context Menu</span></span>  
 <span data-ttu-id="5f9bf-166">**[データ ソース ビュー]** ペインのテーブルまたはビューの列の名前を右クリックすると表示されるショートカット メニューでは、次のオプションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="5f9bf-166">The following options are available in the context menu displayed by right-clicking the name of a column in a table or view in the **Data Source View** pane:</span></span>  
  
 <span data-ttu-id="5f9bf-167">**[列から新しいメジャーを作成]**</span><span class="sxs-lookup"><span data-stu-id="5f9bf-167">**New Measure from Column**</span></span>  
 <span data-ttu-id="5f9bf-168">選択されている列に基づいて、 **[メジャー]** ペインに新しいメジャーを定義します。</span><span class="sxs-lookup"><span data-stu-id="5f9bf-168">Defines a new measure in the **Measures** pane based on the selected column.</span></span>  
  
 <span data-ttu-id="5f9bf-169">**データの探索**</span><span class="sxs-lookup"><span data-stu-id="5f9bf-169">**Explore Data**</span></span>  
 <span data-ttu-id="5f9bf-170">選択した列が含まれるテーブルの **[データの探索]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="5f9bf-170">Display the **Explore Data** dialog box for the table that contains the selected column.</span></span>  
  
 <span data-ttu-id="5f9bf-171">**[データ ソース ビューの編集]**</span><span class="sxs-lookup"><span data-stu-id="5f9bf-171">**Edit Data Source View**</span></span>  
 <span data-ttu-id="5f9bf-172">選択した列を含むデータ ソース ビューのデータ ソース ビュー デザイナーを表示します。</span><span class="sxs-lookup"><span data-stu-id="5f9bf-172">Displays Data Source View Designer for the data source view that contains the selected column.</span></span> <span data-ttu-id="5f9bf-173">データ ソース ビュー デザイナーの詳細については、「[データ ソース ビュー デザイナー &#40;Analysis Services - 多次元データ&#41;](data-source-view-designer-analysis-services-multidimensional-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5f9bf-173">For more information about Data Source View Designer, see [Data Source View Designer &#40;Analysis Services - Multidimensional Data&#41;](data-source-view-designer-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="5f9bf-174">**プロパティ**</span><span class="sxs-lookup"><span data-stu-id="5f9bf-174">**Properties**</span></span>  
 <span data-ttu-id="5f9bf-175">**で選択されている列の** [プロパティ] [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] ウィンドウを表示します。</span><span class="sxs-lookup"><span data-stu-id="5f9bf-175">Displays the **Properties** window in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] for the selected column.</span></span>  
  
## <a name="relationship-context-menu"></a><span data-ttu-id="5f9bf-176">リレーションシップのショートカット メニュー</span><span class="sxs-lookup"><span data-stu-id="5f9bf-176">Relationship Context Menu</span></span>  
 <span data-ttu-id="5f9bf-177">**[データ ソース ビュー]** ペインのリレーションシップを右クリックすると表示されるショートカット メニューでは、次のオプションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="5f9bf-177">The following options are available in the context menu displayed by right-clicking a relationship in the **Data Source View** pane:</span></span>  
  
 <span data-ttu-id="5f9bf-178">**[データ ソース ビューの編集]**</span><span class="sxs-lookup"><span data-stu-id="5f9bf-178">**Edit Data Source View**</span></span>  
 <span data-ttu-id="5f9bf-179">選択されているリレーションシップを含むデータ ソース ビューのデータ ソース ビュー デザイナーを表示します。</span><span class="sxs-lookup"><span data-stu-id="5f9bf-179">Displays Data Source View Designer for the data source view that contains the selected relationship.</span></span> <span data-ttu-id="5f9bf-180">データ ソース ビュー デザイナーの詳細については、「[データ ソース ビュー デザイナー &#40;Analysis Services - 多次元データ&#41;](data-source-view-designer-analysis-services-multidimensional-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5f9bf-180">For more information about Data Source View Designer, see [Data Source View Designer &#40;Analysis Services - Multidimensional Data&#41;](data-source-view-designer-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="5f9bf-181">**プロパティ**</span><span class="sxs-lookup"><span data-stu-id="5f9bf-181">**Properties**</span></span>  
 <span data-ttu-id="5f9bf-182">選択したリレーションシップの **[プロパティ]** ウィンドウを [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] に表示します。</span><span class="sxs-lookup"><span data-stu-id="5f9bf-182">Displays the **Properties** window in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] for the selected relationship.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f9bf-183">参照</span><span class="sxs-lookup"><span data-stu-id="5f9bf-183">See Also</span></span>  
 <span data-ttu-id="5f9bf-184">[ツールバー &#40;キューブデザイナーの [キューブ構造] タブ&#41; &#40;Analysis Services-多次元データ&#41;](toolbar-cube-structure-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="5f9bf-184">[Toolbar &#40;Cube Structure Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](toolbar-cube-structure-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="5f9bf-185">[メジャー &#40;キューブデザイナーの [キューブ構造] タブ&#41; &#40;Analysis Services-多次元データ&#41;](measures-cube-structure-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="5f9bf-185">[Measures &#40;Cube Structure Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](measures-cube-structure-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="5f9bf-186">[ディメンション &#40;キューブデザイナーの [キューブ構造] タブでは&#41; &#40;Analysis Services-多次元データ&#41;](dimensions-cube-structure-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="5f9bf-186">[Dimensions &#40;Cube Structure Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](dimensions-cube-structure-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="5f9bf-187">キューブ構造 &#40;キューブデザイナーの&#41; &#40;Analysis Services-多次元データ&#41;</span><span class="sxs-lookup"><span data-stu-id="5f9bf-187">Cube Structure &#40;Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;</span></span>](cube-structure-cube-designer-analysis-services-multidimensional-data.md)  
  
  
