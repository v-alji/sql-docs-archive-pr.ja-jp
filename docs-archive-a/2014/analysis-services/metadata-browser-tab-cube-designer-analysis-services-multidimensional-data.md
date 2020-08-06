---
title: '[メタデータ] ([ブラウザー] タブ、キューブデザイナー) (Analysis Services-多次元データ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.browsecube.metadatapane.f1
ms.assetid: a1ace545-488d-4645-8330-56408a5e8abd
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8093ac8cac8e3cd5a609e97b47ede89912897e8a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740578"
---
# <a name="metadata-browser-tab-cube-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="255df-102">[メタデータ] (キューブ デザイナーの [ブラウザー] タブ) (Analysis Services - 多次元データ)</span><span class="sxs-lookup"><span data-stu-id="255df-102">Metadata (Browser Tab, Cube Designer) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="255df-103">キューブ構造の参照、関連するメジャーの確認、ディメンションの閲覧と作成には、キューブ デザイナーの **[ブラウザー]** タブの **[メタデータ]** ペインを使用します。</span><span class="sxs-lookup"><span data-stu-id="255df-103">Use the **Metadata** pane on the **Browser** tab in Cube Designer to browse the structure of the cube, to see related measures, and to view and create dimensions.</span></span> <span data-ttu-id="255df-104">階層のドリル ダウン、使用できるメジャーと KPI の一覧表示、オブジェクトの完全修飾名のコピーなどを実行できます。</span><span class="sxs-lookup"><span data-stu-id="255df-104">You can drill down into hierarchies, view a list of available measures and KPIs, and copy the fully qualified names of objects.</span></span>  
  
 <span data-ttu-id="255df-105">**[メタデータ]** ペインからクエリ作成領域にオブジェクトや階層をドラッグして新しいクエリを作成したり、データをエクスポートして Excel で参照したりすることもできます。</span><span class="sxs-lookup"><span data-stu-id="255df-105">You can also drag the objects and hierarchies in the **Metadata** pane to the query building area, to create new queries or export data for browsing in Excel.</span></span>  
  
## <a name="options"></a><span data-ttu-id="255df-106">Options</span><span class="sxs-lookup"><span data-stu-id="255df-106">Options</span></span>  
 <span data-ttu-id="255df-107">**Metadata**</span><span class="sxs-lookup"><span data-stu-id="255df-107">**Metadata**</span></span>  
 <span data-ttu-id="255df-108">現在のビューで使用可能なメタデータを表示します。</span><span class="sxs-lookup"><span data-stu-id="255df-108">Displays the metadata available in the current view.</span></span> <span data-ttu-id="255df-109">キューブ アイコンをクリックしてビュー (現在選択されているパースペクティブまたはキューブ) を変更した後、 **[キューブの選択]** ダイアログ ボックスを使用して新しいキューブまたはパースペクティブを選択できます。</span><span class="sxs-lookup"><span data-stu-id="255df-109">You can change the view (that is, the currently selected perspective or cube) by clicking the cube icon, and then using the **Cube Selection** dialog box to choose a new cube or perspective.</span></span> <span data-ttu-id="255df-110">**[メジャー グループ]** をクリックして、ドロップダウン リストから新しいメジャー グループを選択し、 **[メタデータ]** ペインで利用可能なオブジェクトをフィルター選択することもできます。</span><span class="sxs-lookup"><span data-stu-id="255df-110">You can also click **Measure Group**, and select a new measure group from the dropdown list to filter the objects that are available in the **Metadata** pane.</span></span>  
  
 <span data-ttu-id="255df-111">選択した項目を、 [!INCLUDE[msCoName](../includes/msconame-md.md)] [レポート] **ペインの** Office 11.0 PivotTable コントロールのフィルター、データ、行、または列の領域にドラッグして、選択した項目のデータを表示します。</span><span class="sxs-lookup"><span data-stu-id="255df-111">Drag selected items to the filter, data, row, or column areas of the [!INCLUDE[msCoName](../includes/msconame-md.md)] Office 11.0 PivotTable control in the **Report** pane to display the data for the selected item.</span></span>  
  
 <span data-ttu-id="255df-112">**関数**</span><span class="sxs-lookup"><span data-stu-id="255df-112">**Functions**</span></span>  
 <span data-ttu-id="255df-113">**[ブラウザー]** でクエリまたはデータ ビューの作成に使用できるすべての関数、演算子、および定数を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="255df-113">Displays a list of all functions, operators, and constants that can be used to create queries or data views in the **Browser**.</span></span> <span data-ttu-id="255df-114">関数を使用するには、目的の関数を探して、クエリ領域にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="255df-114">To use a function, locate the one you want, and drag it into the query area.</span></span> <span data-ttu-id="255df-115">対応する構文の定義がテキストに追加されます。</span><span class="sxs-lookup"><span data-stu-id="255df-115">The syntax definition is added to the text</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="255df-116">グラフィカル デザイン ビューで作業している場合、 **[関数]** の一覧は利用できません。</span><span class="sxs-lookup"><span data-stu-id="255df-116">The **Function** list is not available when you are working in graphical design view.</span></span>  
  
 <span data-ttu-id="255df-117">テーブル モデルで作業している場合は、関数の一覧に MDX 関数と DAX 関数の両方が含まれます。</span><span class="sxs-lookup"><span data-stu-id="255df-117">When working with a tabular model, the list of functions includes both MDX functions and DAX functions.</span></span> <span data-ttu-id="255df-118">そうでない場合は、一覧に MDX だけが含まれます。</span><span class="sxs-lookup"><span data-stu-id="255df-118">Otherwise, the list includes only MDX.</span></span> <span data-ttu-id="255df-119">多次元モデルは、オブジェクトの定義の一部として DAX 式を組み込むことはできますが、直接 DAX 関数を使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="255df-119">A multidimensional model cannot use DAX functions directly, although a DAX expression might be included as part of an object definition.</span></span>  
  
 <span data-ttu-id="255df-120">ヒント: DAX 関数が格納されているフォルダーは、全大文字で表示されます。</span><span class="sxs-lookup"><span data-stu-id="255df-120">Tip: The folders that contain DAX functions are listed in all upper-case letters.</span></span> <span data-ttu-id="255df-121">その他すべてのフォルダーには、MDX 関数が格納されています。</span><span class="sxs-lookup"><span data-stu-id="255df-121">All other folders contain MDX functions.</span></span> <span data-ttu-id="255df-122">たとえば、統計関数には 2 つのフォルダーがあり、関連する DAX 関数は **STATISTICAL** に格納されています。</span><span class="sxs-lookup"><span data-stu-id="255df-122">For example, there are two folders for statistical functions: **STATISTICAL** contains the related DAX functions.</span></span>  
  
## <a name="context-menu"></a><span data-ttu-id="255df-123">コンテキスト メニュー</span><span class="sxs-lookup"><span data-stu-id="255df-123">Context Menu</span></span>  
 <span data-ttu-id="255df-124">**[メタデータ]** ペインで表示される要素を右クリックして表示されるショートカット メニューでは、次のオプションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="255df-124">The following options are available in the context menu displayed by right-clicking an element displayed in the **Metadata** pane:</span></span>  
  
|<span data-ttu-id="255df-125">オプション</span><span class="sxs-lookup"><span data-stu-id="255df-125">Option</span></span>|<span data-ttu-id="255df-126">[説明]</span><span class="sxs-lookup"><span data-stu-id="255df-126">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="255df-127">**[クエリに追加]**</span><span class="sxs-lookup"><span data-stu-id="255df-127">**Add to Query**</span></span>|<span data-ttu-id="255df-128">選択したオブジェクトをクエリ作成領域の下のペインに追加します。</span><span class="sxs-lookup"><span data-stu-id="255df-128">Click to add the selected object to the lower pane of the query building area.</span></span>|  
|<span data-ttu-id="255df-129">**[フィルターに追加]**</span><span class="sxs-lookup"><span data-stu-id="255df-129">**Add to Filter**</span></span>|<span data-ttu-id="255df-130">選択したディメンション、属性、階層、またはレベルを **[ブラウザー]** のフィルター領域に追加します。</span><span class="sxs-lookup"><span data-stu-id="255df-130">Click to add the selected dimension, attribute, hierarchy, or level to the filter area of the **Browser**.</span></span><br /><br /> <span data-ttu-id="255df-131">注: このオプションは、ディメンション、属性、階層、またはレベルが選択されている場合にのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="255df-131">Note: This option is enabled only if a dimension, attribute, hierarchy, or level is selected.</span></span>|  
|<span data-ttu-id="255df-132">**コピー**</span><span class="sxs-lookup"><span data-stu-id="255df-132">**Copy**</span></span>|<span data-ttu-id="255df-133">選択した項目をクリップボードに追加します。</span><span class="sxs-lookup"><span data-stu-id="255df-133">Click to add the selected item to the Clipboard.</span></span><br /><br /> <span data-ttu-id="255df-134">注: このオプションでは、オブジェクトの完全修飾名がコピーされます。</span><span class="sxs-lookup"><span data-stu-id="255df-134">Note: This option copies the fully qualified name of the object.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="255df-135">参照</span><span class="sxs-lookup"><span data-stu-id="255df-135">See Also</span></span>  
 <span data-ttu-id="255df-136">[ツールバー &#40;[ブラウザー] タブ、キューブデザイナー&#41; &#40;Analysis Services-多次元データ&#41;](toolbar-browser-tab-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="255df-136">[Toolbar &#40;Browser Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](toolbar-browser-tab-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="255df-137">[[Excel で分析] &#40;[ブラウザー] タブ、キューブデザイナー&#41; &#40;Analysis Services-多次元データ&#41;](analyze-in-excel-browser-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="255df-137">[Analyze in Excel &#40;Browser Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](analyze-in-excel-browser-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="255df-138">[キューブデザイナーの [&#40;ブラウザー] タブの [クエリとフィルター]&#41; &#40;Analysis Services-多次元データ&#41;](query-filter-browser-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="255df-138">[Query and Filter &#40;Browser Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](query-filter-browser-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="255df-139">ブラウザー &#40;キューブデザイナー&#41; &#40;Analysis Services-多次元データ&#41;</span><span class="sxs-lookup"><span data-stu-id="255df-139">Browser &#40;Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;</span></span>](browser-cube-designer-analysis-services-multidimensional-data.md)  
  
  
