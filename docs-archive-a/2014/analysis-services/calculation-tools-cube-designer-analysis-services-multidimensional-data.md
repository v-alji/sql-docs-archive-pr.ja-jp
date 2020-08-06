---
title: 計算ツール (キューブデザイナーの [計算] タブ) (Analysis Services 多次元データ) |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.calculationsview.calculationtoolspane.f1
ms.assetid: b1aa8a1a-6532-45d2-8f53-d3e211d7197a
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6701a15a7d773a90e48ec39dc976b9ef579c9ec8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633539"
---
# <a name="calculation-tools-calculations-tab-cube-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="239db-102">計算ツール (キューブ デザイナーの [計算] タブ) (Analysis Services - 多次元データ)</span><span class="sxs-lookup"><span data-stu-id="239db-102">Calculation Tools (Calculations Tab, Cube Designer) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="239db-103">キューブ デザイナーの **[計算]** タブの **[計算ツール]** ペインを使用すると、計算に使用するメタデータ、関数、およびテンプレートを検索できます。</span><span class="sxs-lookup"><span data-stu-id="239db-103">Use the **Calculation Tools** pane on the **Calculations** tab in Cube Designer to explore metadata, functions, and templates available for use in calculations.</span></span>  
  
## <a name="options"></a><span data-ttu-id="239db-104">Options</span><span class="sxs-lookup"><span data-stu-id="239db-104">Options</span></span>  
 <span data-ttu-id="239db-105">**Metadata**</span><span class="sxs-lookup"><span data-stu-id="239db-105">**Metadata**</span></span>  
 <span data-ttu-id="239db-106">選択したキューブのメタデータを表示します。</span><span class="sxs-lookup"><span data-stu-id="239db-106">Displays the metadata for the selected cube.</span></span>  
  
 <span data-ttu-id="239db-107">選択した要素をスクリプト エディター ペイン、計算されるメンバー フォーム エディター ペイン、または名前付きセット フォーム エディター ペインにドラッグし、ペイン内の選択した場所にその要素の多次元式 (MDX) 構文を含めます。</span><span class="sxs-lookup"><span data-stu-id="239db-107">Drag a selected element to the Script Editor, Calculated Member Form Editor, or Named Set Form Editor pane to include the Multidimensional Expressions (MDX) syntax for that element at the selected location in the pane.</span></span>  
  
 <span data-ttu-id="239db-108">**関数**</span><span class="sxs-lookup"><span data-stu-id="239db-108">**Functions**</span></span>  
 <span data-ttu-id="239db-109">式および条件で使用可能な関数を表示します。</span><span class="sxs-lookup"><span data-stu-id="239db-109">Displays the functions available for expressions and conditions.</span></span>  
  
 <span data-ttu-id="239db-110">選択した要素を **スクリプト エディター**ペイン、 **計算されるメンバー フォーム エディター**ペインまたは **名前付きセット フォーム エディター** ペインにドラッグし、ペイン内の選択した場所にその要素の多次元式 (MDX) 構文を含めます。</span><span class="sxs-lookup"><span data-stu-id="239db-110">Drag a selected element to the **Script Editor**, **Calculated Member Form Editor**, or **Named Set Form Editor** pane to include the MDX syntax for that element at the selected location in the pane.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="239db-111">プロジェクト モードでは、 **[計算ツール]** ダイアログ ボックスは [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]に付属している MDXFunctions.xml という名前の XML ファイルから、このオプションについての情報を読み取ります。</span><span class="sxs-lookup"><span data-stu-id="239db-111">In project mode, the **Calculation Tools** dialog box reads information for this option from an XML file named MDXFunctions.xml, included with [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="239db-112">オンライン モードでは、このオプションについての情報は、このインスタンスの MDSCHEMA_FUNCTIONS スキーマ行セットから取得します。</span><span class="sxs-lookup"><span data-stu-id="239db-112">In online mode, information for this option is retrieved from the MDSCHEMA_FUNCTIONS schema rowset for the instance.</span></span>  
  
 <span data-ttu-id="239db-113">**テンプレート**</span><span class="sxs-lookup"><span data-stu-id="239db-113">**Templates**</span></span>  
 <span data-ttu-id="239db-114">計算されるメンバー、名前付きセット、およびスクリプト コマンドで使用可能な定義済みのテンプレートを表示します。</span><span class="sxs-lookup"><span data-stu-id="239db-114">Displays the predefined templates available for calculated members, named sets, and script commands.</span></span>  
  
 <span data-ttu-id="239db-115">選択した要素を **スクリプト エディター**ペイン、 **計算されるメンバー フォーム エディター**ペインまたは **名前付きセット フォーム エディター** ペインにドラッグし、ペイン内の選択した場所にその要素の多次元式 (MDX) 構文を含めます。</span><span class="sxs-lookup"><span data-stu-id="239db-115">Drag a selected element to the **Script Editor**, **Calculated Member Form Editor**, or **Named Set Form Editor** pane to include the MDX syntax for that element at the selected location in the pane.</span></span>  
  
## <a name="context-menu"></a><span data-ttu-id="239db-116">コンテキスト メニュー</span><span class="sxs-lookup"><span data-stu-id="239db-116">Context Menu</span></span>  
 <span data-ttu-id="239db-117">**[計算ツール]** ペインで要素を右クリックして表示されるショートカット メニューでは、次のオプションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="239db-117">The following options are available in the context menu displayed by right-clicking an element in the **Calculation Tools** pane:</span></span>  
  
 <span data-ttu-id="239db-118">**コピー**</span><span class="sxs-lookup"><span data-stu-id="239db-118">**Copy**</span></span>  
 <span data-ttu-id="239db-119">**[メタデータ]** または **[関数]** で選択した要素をクリップボードにコピーします。</span><span class="sxs-lookup"><span data-stu-id="239db-119">Select to copy the selected element in **Metadata** or **Functions** to the Clipboard.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="239db-120">**[テンプレート]** が選択されている場合は、このオプションは表示されません。</span><span class="sxs-lookup"><span data-stu-id="239db-120">This option is not displayed if **Templates** is selected.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="239db-121"> このオプションは、 **[メタデータ]** に表示されるディメンションの **[セット]** フォルダーや、 **[関数]** に表示される関数の関数グループ フォルダーなど、選択されたメンバーがコピーできない場合には無効になります。</span><span class="sxs-lookup"><span data-stu-id="239db-121">This option is disabled if the selected member cannot be copied, such as the **Sets** folder of a dimension displayed in **Metadata** or the function group folder for a function displayed in **Functions**.</span></span>  
  
 <span data-ttu-id="239db-122">**[メンバーのフィルター選択]**</span><span class="sxs-lookup"><span data-stu-id="239db-122">**Filter Members**</span></span>  
 <span data-ttu-id="239db-123">**[メンバーのフィルター選択]** ダイアログ ボックスを表示し、 **[メタデータ]** で選択した要素について表示されたメンバーをフィルター処理します。</span><span class="sxs-lookup"><span data-stu-id="239db-123">Select to display the **Filter Members** dialog box and filter members displayed for the selected element in **Metadata**.</span></span> <span data-ttu-id="239db-124">**[メンバーのフィルター選択]** ダイアログ ボックスの詳細については、「[[メンバーのフィルター選択] ダイアログ ボックス &#40;Analysis Services - 多次元データ&#41;](filter-members-dialog-box-analysis-services-multidimensional-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="239db-124">For more information about the **Filter Members** dialog box, see [Filter Members Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](filter-members-dialog-box-analysis-services-multidimensional-data.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="239db-125"> このオプションは、 **[メタデータ]** が選択されている場合にのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="239db-125">This option is displayed only if **Metadata** is selected.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="239db-126"> このオプションは、属性のレベルが **[メタデータ]** で選択されている場合にのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="239db-126">This option is enabled only if a level for an attribute is selected in **Metadata**.</span></span>  
  
 <span data-ttu-id="239db-127">**Add Template**</span><span class="sxs-lookup"><span data-stu-id="239db-127">**Add Template**</span></span>  
 <span data-ttu-id="239db-128">選択されたテンプレートに基づいて、新しく計算されるメンバー、名前付きセット、またはスクリプト コマンドをキューブ スクリプトに追加し、そのコマンドに適する **スクリプト エディター**、 **計算されるメンバー フォーム エディター**、または **名前付きセット フォーム エディター** を表示するか、 **スクリプト エディター** ペインの内容を、(スクリプト ビューの) キューブ スクリプト内のコマンドの場所へスクロールします。</span><span class="sxs-lookup"><span data-stu-id="239db-128">Select to add a new calculated member, named set, or script command based on the selected template to the cube script and display the **Script Editor**, **Calculated Member Form Editor**, or **Named Set Form Editor** as appropriate for that command (in form view) or to scroll the contents of the **Script Editor** pane to the location of the command in the cube script (in script view).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="239db-129"> このオプションは、 **[メタデータ]** が選択されている場合にのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="239db-129">This option is displayed only if **Metadata** is selected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="239db-130">参照</span><span class="sxs-lookup"><span data-stu-id="239db-130">See Also</span></span>  
 <span data-ttu-id="239db-131">[キューブデザイナー &#40;Analysis Services-多次元データ&#41;](cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="239db-131">[Cube Designer &#40;Analysis Services - Multidimensional Data&#41;](cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="239db-132">[ツールバー &#40;キューブデザイナーの [計算] タブ&#41; &#40;Analysis Services-多次元データ&#41;](toolbar-calculations-tab-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="239db-132">[Toolbar &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](toolbar-calculations-tab-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="239db-133">[[スクリプトオーガナイザー &#40;計算] タブ、キューブデザイナー&#41; &#40;Analysis Services-多次元データ&#41;](script-organizer-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="239db-133">[Script Organizer &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](script-organizer-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="239db-134">[計算されるメンバーフォームエディター &#40;[計算] タブ、キューブデザイナー&#41; &#40;Analysis Services-多次元データ&#41;](calculated-member-form-editor-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="239db-134">[Calculated Member Form Editor &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](calculated-member-form-editor-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="239db-135">[名前付きセットフォームエディター &#40;の [計算] タブ、キューブデザイナー&#41; &#40;Analysis Services-多次元データ&#41;](named-set-form-editor-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="239db-135">[Named Set Form Editor &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](named-set-form-editor-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="239db-136">[スクリプトエディターの [&#40;の計算] タブ、キューブデザイナー&#41; &#40;Analysis Services-多次元データ&#41;](script-editor-calculations-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="239db-136">[Script Editor &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](script-editor-calculations-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="239db-137">キューブデザイナーの計算 &#40;&#41; &#40;Analysis Services-多次元データ&#41;</span><span class="sxs-lookup"><span data-stu-id="239db-137">Calculations &#40;Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;</span></span>](calculations-cube-designer-analysis-services-multidimensional-data.md)  
  
  
