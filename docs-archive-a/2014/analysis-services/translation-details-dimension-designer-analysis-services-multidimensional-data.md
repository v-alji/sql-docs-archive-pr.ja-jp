---
title: 翻訳の詳細 ([翻訳] タブ、ディメンションデザイナー) (Analysis Services 多次元データ) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dimensiondesigner.translations.translationpane.tranlationdetails.f1
ms.assetid: 0aa61df3-f2b0-4703-a63b-124da672dcc3
author: minewiskan
ms.author: owend
ms.openlocfilehash: a7cbe4a3c69111d0f82f96ff5125f80fe0c2c57f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738767"
---
# <a name="translation-details-translations-tab-dimension-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="f2797-102">[翻訳の詳細] ([翻訳] タブ、ディメンション デザイナー) (Analysis Services - 多次元データ)</span><span class="sxs-lookup"><span data-stu-id="f2797-102">Translation Details (Translations Tab, Dimension Designer) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="f2797-103">ディメンション デザイナーの **[翻訳]** タブの **[翻訳の詳細]** ペインを使用すると、現在選択しているディメンションの翻訳を定義および管理できます。</span><span class="sxs-lookup"><span data-stu-id="f2797-103">Use the **Translation Details** pane on the **Translations** tab of Dimension Designer to define and manage translations for the currently selected dimension.</span></span>  
  
 <span data-ttu-id="f2797-104">**[翻訳の詳細] ペインを表示するには**</span><span class="sxs-lookup"><span data-stu-id="f2797-104">**To display the Translations Details pane**</span></span>  
  
1.  <span data-ttu-id="f2797-105">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] プロジェクトを開き、目的のディメンションを開きます。</span><span class="sxs-lookup"><span data-stu-id="f2797-105">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project, and then open the dimension that you want.</span></span>  
  
2.  <span data-ttu-id="f2797-106">**[翻訳]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="f2797-106">Click the **Translations** tab.</span></span>  
  
## <a name="options"></a><span data-ttu-id="f2797-107">Options</span><span class="sxs-lookup"><span data-stu-id="f2797-107">Options</span></span>  
 <span data-ttu-id="f2797-108">**[既定の言語]**</span><span class="sxs-lookup"><span data-stu-id="f2797-108">**Default Language**</span></span>  
 <span data-ttu-id="f2797-109">既定の言語におけるディメンション オブジェクトの名前を設定します。</span><span class="sxs-lookup"><span data-stu-id="f2797-109">Sets the names of the dimension objects in the default language.</span></span>  
  
 <span data-ttu-id="f2797-110">**オブジェクトの種類**</span><span class="sxs-lookup"><span data-stu-id="f2797-110">**Object Type**</span></span>  
 <span data-ttu-id="f2797-111">翻訳されるプロパティを表示します。</span><span class="sxs-lookup"><span data-stu-id="f2797-111">Displays the property that will be translated.</span></span> <span data-ttu-id="f2797-112">値が指定されているオブジェクトとプロパティのみが翻訳できます。</span><span class="sxs-lookup"><span data-stu-id="f2797-112">Only objects and properties for which values have been specified can be translated.</span></span> <span data-ttu-id="f2797-113">次のプロパティが翻訳されます。</span><span class="sxs-lookup"><span data-stu-id="f2797-113">The following properties can be translated:</span></span>  
  
-   <span data-ttu-id="f2797-114">Dimension</span><span class="sxs-lookup"><span data-stu-id="f2797-114">Dimension</span></span>  
  
     <span data-ttu-id="f2797-115">`Caption` プロパティと `AttributeAllMember` プロパティ</span><span class="sxs-lookup"><span data-stu-id="f2797-115">`Caption` and `AttributeAllMember` properties</span></span>  
  
-   <span data-ttu-id="f2797-116">属性</span><span class="sxs-lookup"><span data-stu-id="f2797-116">Attribute</span></span>  
  
     <span data-ttu-id="f2797-117">`Caption`、`AttributeHierarchyDisplayFolder`、および `NamingTemplate` プロパティ</span><span class="sxs-lookup"><span data-stu-id="f2797-117">`Caption`, `AttributeHierarchyDisplayFolder`, and `NamingTemplate` properties</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f2797-118">`NamingTemplate` プロパティは、親属性でのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="f2797-118">The `NamingTemplate` property is available only for parent attributes.</span></span>  
  
-   <span data-ttu-id="f2797-119">Hierarchy</span><span class="sxs-lookup"><span data-stu-id="f2797-119">Hierarchy</span></span>  
  
     <span data-ttu-id="f2797-120">`Caption` プロパティと `AllMemberName` プロパティ</span><span class="sxs-lookup"><span data-stu-id="f2797-120">`Caption` and `AllMemberName` properties</span></span>  
  
-   <span data-ttu-id="f2797-121">Level</span><span class="sxs-lookup"><span data-stu-id="f2797-121">Level</span></span>  
  
     <span data-ttu-id="f2797-122">`Caption` プロパティ</span><span class="sxs-lookup"><span data-stu-id="f2797-122">`Caption` property</span></span>  
  
 **\<Language>**  
 <span data-ttu-id="f2797-123">選択した言語でディメンション オブジェクトのプロパティ値を入力、または選択します。</span><span class="sxs-lookup"><span data-stu-id="f2797-123">Type or select the property value of the dimension object in the selected language.</span></span> <span data-ttu-id="f2797-124">参照ボタン (**[...]**) をクリックすると、編集中のプロパティに応じて次のダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f2797-124">Clicking the ellipsis button (**...**) opens additional dialog boxes, depending on the property being edited:</span></span>  
  
-   <span data-ttu-id="f2797-125">`NamingTemplate` プロパティ</span><span class="sxs-lookup"><span data-stu-id="f2797-125">`NamingTemplate` property</span></span>  
  
     <span data-ttu-id="f2797-126">[&#91;レベル名前付けテンプレート&#93; ダイアログ ボックス &#40;Analysis Services - 多次元データ&#41;](level-naming-template-dialog-box-analysis-services-multidimensional-data.md) を表示します。</span><span class="sxs-lookup"><span data-stu-id="f2797-126">Displays the [Level Naming Template Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](level-naming-template-dialog-box-analysis-services-multidimensional-data.md).</span></span>  
  
-   <span data-ttu-id="f2797-127">`Caption` プロパティ (属性の場合)</span><span class="sxs-lookup"><span data-stu-id="f2797-127">`Caption` property (for attributes)</span></span>  
  
     <span data-ttu-id="f2797-128">[&#91;属性データの翻訳&#93; ダイアログ ボックス &#40;Analysis Services - 多次元データ&#41;](attribute-data-translation-dialog-box-analysis-services-multidimensional-data.md) を表示します。</span><span class="sxs-lookup"><span data-stu-id="f2797-128">Displays the [Attribute Data Translation Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](attribute-data-translation-dialog-box-analysis-services-multidimensional-data.md).</span></span>  
  
## <a name="shortcut-menu"></a><span data-ttu-id="f2797-129">ショートカット メニュー</span><span class="sxs-lookup"><span data-stu-id="f2797-129">Shortcut Menu</span></span>  
 <span data-ttu-id="f2797-130">**[翻訳の詳細]** ペインで翻訳を右クリックして表示されるショートカット メニューでは、次のオプションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="f2797-130">The following options are available in the shortcut menu displayed by right-clicking a translation in the **Translation Details** pane:</span></span>  
  
 <span data-ttu-id="f2797-131">**[新しい翻訳]**</span><span class="sxs-lookup"><span data-stu-id="f2797-131">**New Translation**</span></span>  
 <span data-ttu-id="f2797-132">**[言語の選択]** ダイアログ ボックスを表示して、新しい翻訳を作成します。</span><span class="sxs-lookup"><span data-stu-id="f2797-132">Select to display the **Select Language** dialog box and create a new translation.</span></span> <span data-ttu-id="f2797-133">翻訳は、 **[翻訳の詳細]** グリッドに新しい列として表示されます。</span><span class="sxs-lookup"><span data-stu-id="f2797-133">The translation will appear as a new column in the **Translation Details** grid.</span></span>  
  
 <span data-ttu-id="f2797-134">**[翻訳の削除]**</span><span class="sxs-lookup"><span data-stu-id="f2797-134">**Delete Translation**</span></span>  
 <span data-ttu-id="f2797-135">選択された翻訳を削除します。</span><span class="sxs-lookup"><span data-stu-id="f2797-135">Select to delete the selected translation.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f2797-136">このオプションは、翻訳を削除するためにセルを右クリックした場合にのみ有効になります。</span><span class="sxs-lookup"><span data-stu-id="f2797-136">The option is enabled only if you right-clicked a cell to delete the translation.</span></span>  
  
 <span data-ttu-id="f2797-137">**[新しいキャプション列]**</span><span class="sxs-lookup"><span data-stu-id="f2797-137">**New Caption Column**</span></span>  
 <span data-ttu-id="f2797-138">**[翻訳の詳細]** グリッドで属性を変更するときに選択すると、 **[属性データの翻訳]** ダイアログ ボックスが表示され、新しいキャプション列を定義できます。</span><span class="sxs-lookup"><span data-stu-id="f2797-138">Select to display the **Attribute Data Translation** dialog box and define a new caption column when you modify an attribute in the **Translation Details** grid.</span></span> <span data-ttu-id="f2797-139">このオプションを有効にするには、属性の翻訳列のセルが **翻訳の詳細** グリッドで選択されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="f2797-139">To enable this option, a cell in a translation column for an attribute must be selected in the **Translation Details** grid.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f2797-140">このオプションは、属性の翻訳列を削除するためにセルを右クリックした場合にのみ有効になります。</span><span class="sxs-lookup"><span data-stu-id="f2797-140">The option is enabled only if you right-clicked a cell to delete the translation column of an attribute.</span></span>  
  
 <span data-ttu-id="f2797-141">**[キャプション列の編集]**</span><span class="sxs-lookup"><span data-stu-id="f2797-141">**Edit Caption Column**</span></span>  
 <span data-ttu-id="f2797-142">**[翻訳の詳細]** グリッドで属性を変更するときに選択すると、 **[属性データの翻訳]** ダイアログ ボックスが表示され、既存のキャプション列を変更できます。</span><span class="sxs-lookup"><span data-stu-id="f2797-142">Select to display the **Attribute Data Translation** dialog box and modify an existing caption column when you modify an attribute in the **Translation Details** grid.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f2797-143"> このオプションは、属性のキャプション列を含む翻訳列のセルが **翻訳の詳細** グリッドで選択されている場合のみ有効です。</span><span class="sxs-lookup"><span data-stu-id="f2797-143">The option is enabled only if a cell in a translation column that contains a caption column for an attribute must be selected in the **Translation Details** grid.</span></span>  
  
 <span data-ttu-id="f2797-144">**[キャプション列の削除]**</span><span class="sxs-lookup"><span data-stu-id="f2797-144">**Delete Caption Column**</span></span>  
 <span data-ttu-id="f2797-145">選択すると、 **[翻訳の詳細]** グリッドで選択している属性のキャプション列が削除されます。</span><span class="sxs-lookup"><span data-stu-id="f2797-145">Select to delete the caption column for the selected attribute in the **Translation Details** grid.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f2797-146">このオプションは、属性のキャプション列を含む翻訳列のセルを右クリックした場合にのみ有効になります。</span><span class="sxs-lookup"><span data-stu-id="f2797-146">The option is enabled only if you right-clicked a cell in a translation column that contains a caption column for an attribute.</span></span>  
  
 <span data-ttu-id="f2797-147">**[すべての属性を表示]**</span><span class="sxs-lookup"><span data-stu-id="f2797-147">**Show All Attributes**</span></span>  
 <span data-ttu-id="f2797-148">属性階層が無効になっている属性を含め、選択したディメンションに定義されている全属性が表示されます。</span><span class="sxs-lookup"><span data-stu-id="f2797-148">Select to toggle the display of all attributes defined for the selected dimension, including attributes for which attribute hierarchies are disabled.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2797-149">参照</span><span class="sxs-lookup"><span data-stu-id="f2797-149">See Also</span></span>  
 [<span data-ttu-id="f2797-150">翻訳 &#40;ディメンションデザイナー&#41; &#40;Analysis Services-多次元データ&#41;</span><span class="sxs-lookup"><span data-stu-id="f2797-150">Translations &#40;Dimension Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;</span></span>](translations-dimension-designer-analysis-services-multidimensional-data.md)  
  
  
