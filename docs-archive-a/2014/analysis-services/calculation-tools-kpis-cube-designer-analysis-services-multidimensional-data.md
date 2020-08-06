---
title: 計算ツール (キューブデザイナーの [Kpi] タブ) (Analysis Services 多次元データ) |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.kpisview.calculationtoolspane.f1
ms.assetid: c030c725-7763-4c23-9988-4b274a88fc31
author: minewiskan
ms.author: owend
ms.openlocfilehash: 7bb8470173b0a413795fb7b5e3213bb50aa8ee43
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633537"
---
# <a name="calculation-tools-kpis-tab-cube-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="fb3b9-102">[計算ツール] (キューブ デザイナーの [KPI] タブ) (Analysis Services - 多次元データ)</span><span class="sxs-lookup"><span data-stu-id="fb3b9-102">Calculation Tools (KPIs Tab, Cube Designer) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="fb3b9-103">キューブ デザイナーの **[KPI]** タブの **[計算ツール]** ペインを使用すると、主要業績評価指標 (KPI) で使用可能なメタデータ、関数、およびテンプレートを検索できます。</span><span class="sxs-lookup"><span data-stu-id="fb3b9-103">Use the **Calculation Tools** pane on the **KPIs** tab in Cube Designer to explore metadata, functions, and templates available for use in Key Performance Indicators (KPIs).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fb3b9-104">このペインはフォーム ビューでのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="fb3b9-104">This pane is displayed only in form view.</span></span>  
  
## <a name="options"></a><span data-ttu-id="fb3b9-105">Options</span><span class="sxs-lookup"><span data-stu-id="fb3b9-105">Options</span></span>  
 <span data-ttu-id="fb3b9-106">**Metadata**</span><span class="sxs-lookup"><span data-stu-id="fb3b9-106">**Metadata**</span></span>  
 <span data-ttu-id="fb3b9-107">選択したキューブのメタデータを表示します。</span><span class="sxs-lookup"><span data-stu-id="fb3b9-107">Displays the metadata for the selected cube.</span></span>  
  
 <span data-ttu-id="fb3b9-108">選択した要素を **KPI フォーム エディター** ペインにドラッグし、ペイン内の選択した場所にその要素の多次元式 (MDX) の構文を含めます。</span><span class="sxs-lookup"><span data-stu-id="fb3b9-108">Drag a selected element to the **KPI Form Editor** pane to include the Multidimensional Expressions (MDX) syntax for that element at the selected location in the pane.</span></span>  
  
 <span data-ttu-id="fb3b9-109">**関数**</span><span class="sxs-lookup"><span data-stu-id="fb3b9-109">**Functions**</span></span>  
 <span data-ttu-id="fb3b9-110">式および条件で使用可能な関数を表示します。</span><span class="sxs-lookup"><span data-stu-id="fb3b9-110">Displays the functions available for expressions and conditions.</span></span>  
  
 <span data-ttu-id="fb3b9-111">選択した要素を **KPI フォーム エディター** ペインにドラッグし、ペイン内の選択した場所にその要素の MDX の構文を含めます。</span><span class="sxs-lookup"><span data-stu-id="fb3b9-111">Drag a selected element to the **KPI Form Editor** pane to include the MDX syntax for that element at the selected location in the pane.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fb3b9-112">プロジェクト モードでは、 **[計算ツール]** ダイアログ ボックスは [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]に付属している MDXFunctions.xml という名前の XML ファイルから、このオプションについての情報を読み取ります。</span><span class="sxs-lookup"><span data-stu-id="fb3b9-112">In project mode, the **Calculation Tools** dialog box reads information for this option from an XML file named MDXFunctions.xml, included with [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="fb3b9-113">オンライン モードでは、このオプションについての情報は、このインスタンスの MDSCHEMA_FUNCTIONS スキーマ行セットから取得します。</span><span class="sxs-lookup"><span data-stu-id="fb3b9-113">In online mode, information for this option is retrieved from the MDSCHEMA_FUNCTIONS schema rowset for the instance.</span></span>  
  
 <span data-ttu-id="fb3b9-114">**テンプレート**</span><span class="sxs-lookup"><span data-stu-id="fb3b9-114">**Templates**</span></span>  
 <span data-ttu-id="fb3b9-115">KPI で使用可能な事前定義テンプレートを表示します。</span><span class="sxs-lookup"><span data-stu-id="fb3b9-115">Displays the predefined templates available for KPIs.</span></span>  
  
 <span data-ttu-id="fb3b9-116">選択した要素を **KPI フォーム エディター** ペインにドラッグし、ペイン内の選択した場所にその要素の MDX の構文を含めます。</span><span class="sxs-lookup"><span data-stu-id="fb3b9-116">Drag a selected element to the **KPI Form Editor** pane to include the MDX syntax for that element at the selected location in the pane.</span></span>  
  
## <a name="context-menu"></a><span data-ttu-id="fb3b9-117">コンテキスト メニュー</span><span class="sxs-lookup"><span data-stu-id="fb3b9-117">Context Menu</span></span>  
 <span data-ttu-id="fb3b9-118">**[計算ツール]** ペインで要素を右クリックして表示されるショートカット メニューでは、次のオプションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="fb3b9-118">The following options are available in the context menu displayed by right-clicking an element in the **Calculation Tools** pane:</span></span>  
  
 <span data-ttu-id="fb3b9-119">**コピー**</span><span class="sxs-lookup"><span data-stu-id="fb3b9-119">**Copy**</span></span>  
 <span data-ttu-id="fb3b9-120">**[メタデータ]** または **[関数]** で選択した要素をクリップボードにコピーします。</span><span class="sxs-lookup"><span data-stu-id="fb3b9-120">Select to copy the selected element in **Metadata** or **Functions** to the Clipboard.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fb3b9-121">**[テンプレート]** が選択されている場合は、このオプションは表示されません。</span><span class="sxs-lookup"><span data-stu-id="fb3b9-121">This option is not displayed if **Templates** is selected.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fb3b9-122"> このオプションは、 **[メタデータ]** に表示されるディメンションの **[セット]** フォルダーや、 **[関数]** に表示される関数の関数グループ フォルダーなど、選択されたメンバーがコピーできない場合には無効になります。</span><span class="sxs-lookup"><span data-stu-id="fb3b9-122">This option is disabled if the selected member cannot be copied, such as the **Sets** folder of a dimension displayed in **Metadata** or the function group folder for a function displayed in **Functions**.</span></span>  
  
 <span data-ttu-id="fb3b9-123">**[メンバーのフィルター選択]**</span><span class="sxs-lookup"><span data-stu-id="fb3b9-123">**Filter Members**</span></span>  
 <span data-ttu-id="fb3b9-124">**[メンバーのフィルター選択]** ダイアログ ボックスを表示し、 **[メタデータ]** で選択した要素について表示されたメンバーをフィルター処理します。</span><span class="sxs-lookup"><span data-stu-id="fb3b9-124">Select to display the **Filter Members** dialog box and filter members displayed for the selected element in **Metadata**.</span></span> <span data-ttu-id="fb3b9-125">**[メンバーのフィルター選択]** ダイアログ ボックスの詳細については、「[[メンバーのフィルター選択] ダイアログ ボックス &#40;Analysis Services - 多次元データ&#41;](filter-members-dialog-box-analysis-services-multidimensional-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fb3b9-125">For more information about the **Filter Members** dialog box, see [Filter Members Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](filter-members-dialog-box-analysis-services-multidimensional-data.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fb3b9-126"> このオプションは、 **[メタデータ]** が選択されている場合にのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="fb3b9-126">This option is displayed only if **Metadata** is selected.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fb3b9-127"> このオプションは、属性のレベルが **[メタデータ]** で選択されている場合にのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="fb3b9-127">This option is enabled only if a level for an attribute is selected in **Metadata**.</span></span>  
  
 <span data-ttu-id="fb3b9-128">**Add Template**</span><span class="sxs-lookup"><span data-stu-id="fb3b9-128">**Add Template**</span></span>  
 <span data-ttu-id="fb3b9-129">選択されたテンプレートに基づいて、新しく計算されるメンバー、名前付きセット、またはスクリプト コマンドをキューブ スクリプトに追加し、 **KPI フォーム エディター** をフォーム ビューで表示します。</span><span class="sxs-lookup"><span data-stu-id="fb3b9-129">Select to add a new calculated member, named set, or script command based on the selected template to the cube script and display the **KPI Form Editor** in form view.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fb3b9-130"> このオプションは、 **[メタデータ]** が選択されている場合にのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="fb3b9-130">This option is displayed only if **Metadata** is selected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb3b9-131">参照</span><span class="sxs-lookup"><span data-stu-id="fb3b9-131">See Also</span></span>  
 <span data-ttu-id="fb3b9-132">[キューブデザイナー &#40;Analysis Services-多次元データ&#41;](cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="fb3b9-132">[Cube Designer &#40;Analysis Services - Multidimensional Data&#41;](cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="fb3b9-133">[Kpi &#40;キューブデザイナー&#41; &#40;Analysis Services-多次元データ&#41;](kpis-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="fb3b9-133">[KPIs &#40;Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](kpis-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="fb3b9-134">[ツールバー &#40;キューブデザイナーの [Kpi] タブ&#41; &#40;Analysis Services-多次元データ&#41;](toolbar-kpis-tab-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="fb3b9-134">[Toolbar &#40;KPIs Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](toolbar-kpis-tab-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="fb3b9-135">[[KPI オーガナイザー &#40;Kpi] タブ、キューブデザイナー&#41; &#40;Analysis Services-多次元データ&#41;](kpi-organizer-kpis-tab-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="fb3b9-135">[KPI Organizer &#40;KPIs Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](kpi-organizer-kpis-tab-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="fb3b9-136">[KPI フォームエディター &#40;[Kpi] タブ、キューブデザイナー&#41; &#40;Analysis Services-多次元データ&#41;](kpi-form-editor-kpis-tab-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="fb3b9-136">[KPI Form Editor &#40;KPIs Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](kpi-form-editor-kpis-tab-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="fb3b9-137">[KPI ブラウザー &#40;[Kpi] タブ、キューブデザイナー&#41; &#40;Analysis Services-多次元データ&#41;](kpi-browser-kpis-tab-cube-designer-analysis-services-multidimensional-data.md)</span><span class="sxs-lookup"><span data-stu-id="fb3b9-137">[KPI Browser &#40;KPIs Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](kpi-browser-kpis-tab-cube-designer-analysis-services-multidimensional-data.md)</span></span>  
  
  
