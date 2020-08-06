---
title: 計算されるメンバーフォームエディター (キューブデザイナーの [計算] タブ) (Analysis Services 多次元データ) |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.calculationexpression.calculatedmember.f1
ms.assetid: f7719b9e-b1e6-4792-90a6-30d9d8eb1196
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9dd45ece03fd81e0e7356e7bdcd0ec8dc53287bb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633549"
---
# <a name="calculated-member-form-editor-calculations-tab-cube-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="816b6-102">計算されるメンバー フォーム エディター (キューブ デザイナーの [計算] タブ) (Analysis Services - 多次元データ)</span><span class="sxs-lookup"><span data-stu-id="816b6-102">Calculated Member Form Editor (Calculations Tab, Cube Designer) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="816b6-103">キューブ デザイナーの **[計算]** タブの **計算されるメンバー フォーム エディター** ペインを使用すると、計算されるメンバーを作成したり変更したりできます。</span><span class="sxs-lookup"><span data-stu-id="816b6-103">Use the **Calculated Member Form Editor** pane on the **Calculations** tab in Cube Designer to create or modify a calculated member.</span></span>  
  
 <span data-ttu-id="816b6-104">**注** &#xA0;&#xA0;&#xA0;このペインはフォーム ビューでのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="816b6-104">**Note** This pane is displayed only in form view.</span></span>  
  
## <a name="options"></a><span data-ttu-id="816b6-105">Options</span><span class="sxs-lookup"><span data-stu-id="816b6-105">Options</span></span>  
 <span data-ttu-id="816b6-106">**名前**</span><span class="sxs-lookup"><span data-stu-id="816b6-106">**Name**</span></span>  
 <span data-ttu-id="816b6-107">計算されるメンバーの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="816b6-107">Type the name of the calculated member.</span></span>  
  
 <span data-ttu-id="816b6-108">**[親のプロパティ]**</span><span class="sxs-lookup"><span data-stu-id="816b6-108">**Parent Properties**</span></span>  
 <span data-ttu-id="816b6-109">展開して、 **[親階層]**、 **[親メンバー]**、および **[変更]** の各オプションを表示します。</span><span class="sxs-lookup"><span data-stu-id="816b6-109">Expand to view the **Parent hierarchy**, **Parent member**, and **Change** options.</span></span>  
  
 <span data-ttu-id="816b6-110">**親階層**</span><span class="sxs-lookup"><span data-stu-id="816b6-110">**Parent hierarchy**</span></span>  
 <span data-ttu-id="816b6-111">計算されるメンバーを含めるために選択したキューブ内でディメンションと階層を選択します。</span><span class="sxs-lookup"><span data-stu-id="816b6-111">Select the dimension and hierarchy in the selected cube that is to include the calculated member.</span></span> <span data-ttu-id="816b6-112">[メジャー] を選択して、計算されるメジャーを定義します。</span><span class="sxs-lookup"><span data-stu-id="816b6-112">Select MEASURES to define a calculated measure.</span></span>  
  
 <span data-ttu-id="816b6-113">**[親メンバー]**</span><span class="sxs-lookup"><span data-stu-id="816b6-113">**Parent member**</span></span>  
 <span data-ttu-id="816b6-114">計算されたメンバーが下に表示されるメンバーを選択します。</span><span class="sxs-lookup"><span data-stu-id="816b6-114">Select the member beneath which the calculated member is to appear.</span></span>  
  
 <span data-ttu-id="816b6-115">**注** &nbsp;&nbsp;&nbsp;このオプションは、 **[親階層]** に [メジャー] 以外の階層が指定されている場合に利用できます。</span><span class="sxs-lookup"><span data-stu-id="816b6-115">**Note** This option is available if **Parent hierarchy** specifies a hierarchy other than MEASURES.</span></span>  
  
 <span data-ttu-id="816b6-116">**変更**</span><span class="sxs-lookup"><span data-stu-id="816b6-116">**Change**</span></span>  
 <span data-ttu-id="816b6-117">**[親メンバーの選択]** ダイアログ ボックスを表示し、 **[親メンバー]** のメンバーを選択します。</span><span class="sxs-lookup"><span data-stu-id="816b6-117">Select to display the **Select Parent Member** dialog box and choose a member for **Parent member**.</span></span> <span data-ttu-id="816b6-118">**[親メンバーの選択]** ダイアログ ボックスの詳細については、「[[親メンバーの選択] ダイアログ ボックス &#40;Analysis Services - 多次元データ&#41;](select-parent-member-dialog-box-analysis-services-multidimensional-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="816b6-118">For more information about the **Select Parent Member** dialog box, see [Select Parent Member Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](select-parent-member-dialog-box-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="816b6-119">**[式]**</span><span class="sxs-lookup"><span data-stu-id="816b6-119">**Expression**</span></span>  
 <span data-ttu-id="816b6-120">展開して、計算されるメンバーの多次元式 (MDX) を表示または編集します。</span><span class="sxs-lookup"><span data-stu-id="816b6-120">Expand to view or edit the Multidimensional Expressions (MDX) expression for the calculated member.</span></span>  
  
 <span data-ttu-id="816b6-121">選択した要素を **[計算ツール]** ペインからこのオプションへドラッグして、選択した要素に対して MDX 構文を含めます。</span><span class="sxs-lookup"><span data-stu-id="816b6-121">Drag selected elements from the **Calculation Tools** pane to this option to include the MDX syntax for the selected element.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="816b6-122">この式は文字列または数値として評価することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="816b6-122">It is recommended that this expression evaluate to a string or to a numeric value.</span></span>  
  
 <span data-ttu-id="816b6-123">**追加のプロパティ**</span><span class="sxs-lookup"><span data-stu-id="816b6-123">**Additional Properties**</span></span>  
 <span data-ttu-id="816b6-124">展開して、 **[書式設定文字列]**、 **[表示]**、 **[空以外の動作]**、 **[色の式]**、および **[フォントの式]** の各オプションを表示します。</span><span class="sxs-lookup"><span data-stu-id="816b6-124">Expand to view the **Format string**, **Visible**, **Non-empty behavior**, **Color Expressions**, and **Font Expressions** options.</span></span>  
  
 <span data-ttu-id="816b6-125">**[書式設定文字列]**</span><span class="sxs-lookup"><span data-stu-id="816b6-125">**Format string**</span></span>  
 <span data-ttu-id="816b6-126">計算されるメンバーが返す値の書式設定に使用するために、MDX 書式設定文字列を入力するか、定義済みの書式設定文字列を選択します。</span><span class="sxs-lookup"><span data-stu-id="816b6-126">Type the MDX format string used to format the value returned by the calculated member, or select a predefined format string.</span></span>  
  
 <span data-ttu-id="816b6-127">MDX 書式設定文字列の詳細については、「[FORMAT_STRING の内容 &#40;MDX&#41;](multidimensional-models/mdx/mdx-cell-properties-format-string-contents.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="816b6-127">For more information about MDX format strings, see [FORMAT_STRING Contents &#40;MDX&#41;](multidimensional-models/mdx/mdx-cell-properties-format-string-contents.md).</span></span>  
  
 <span data-ttu-id="816b6-128">**Visible**</span><span class="sxs-lookup"><span data-stu-id="816b6-128">**Visible**</span></span>  
 <span data-ttu-id="816b6-129">**[True]** を選択すると、計算されるメンバーのクライアント アプリケーションへの表示を許可します。</span><span class="sxs-lookup"><span data-stu-id="816b6-129">Select **True** to allow the calculated member to be visible to client applications.</span></span>  
  
 <span data-ttu-id="816b6-130">**[空以外の動作]**</span><span class="sxs-lookup"><span data-stu-id="816b6-130">**Non-empty behavior**</span></span>  
 <span data-ttu-id="816b6-131">計算されるメンバーの MDX で NON EMPTY クエリの解決に使用するメジャー名を選択します。</span><span class="sxs-lookup"><span data-stu-id="816b6-131">Select the name of the measure used to resolve NON EMPTY queries in MDX for the calculated member.</span></span> <span data-ttu-id="816b6-132">**[空以外の動作]** プロパティが空白の場合、メンバーが空であるかどうかを判断するために、計算されるメンバーを繰り返し評価する必要があります。</span><span class="sxs-lookup"><span data-stu-id="816b6-132">If the **Non Empty Behavior** property is blank, the calculated member must be evaluated repeatedly to determine if a member is empty.</span></span> <span data-ttu-id="816b6-133">**[空以外の動作]** プロパティにメジャー名が格納されるときに、指定されたメジャーが空の場合は、計算されるメンバーは空として処理されます。</span><span class="sxs-lookup"><span data-stu-id="816b6-133">If the **Non Empty Behavior** property contains the name of a measure, the calculated member is treated as empty if the specified measure is empty.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="816b6-134">このプロパティの使用は非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="816b6-134">This property is deprecated.</span></span> <span data-ttu-id="816b6-135">これを設定しないでください。</span><span class="sxs-lookup"><span data-stu-id="816b6-135">Avoid setting it.</span></span> <span data-ttu-id="816b6-136">詳細については、「 [SQL Server 2014 の非推奨の Analysis Services 機能](deprecated-analysis-services-features-in-sql-server-2014.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="816b6-136">See [Deprecated Analysis Services Features in SQL Server 2014](deprecated-analysis-services-features-in-sql-server-2014.md) for details.</span></span>  
  
 <span data-ttu-id="816b6-137">**色の式**</span><span class="sxs-lookup"><span data-stu-id="816b6-137">**Color Expressions**</span></span>  
 <span data-ttu-id="816b6-138">展開して **[前景の色]** オプションおよび **[背景色]** オプションを表示します。</span><span class="sxs-lookup"><span data-stu-id="816b6-138">Expand to view the **Fore color** and **Back color** options.</span></span>  
  
 <span data-ttu-id="816b6-139">**[前景の色]**</span><span class="sxs-lookup"><span data-stu-id="816b6-139">**Fore color**</span></span>  
 <span data-ttu-id="816b6-140">計算されるメンバーの前景色を指定するために、MDX 式を入力します。</span><span class="sxs-lookup"><span data-stu-id="816b6-140">Type the MDX expression that provides the foreground color of the calculated member.</span></span>  
  
 <span data-ttu-id="816b6-141">選択した要素を **[計算ツール]** ペインからこのオプションへドラッグして、選択した要素に対して MDX 構文を含めます。</span><span class="sxs-lookup"><span data-stu-id="816b6-141">Drag selected elements from the **Calculation Tools** pane to this option to include the MDX syntax for the selected element.</span></span>  
  
 <span data-ttu-id="816b6-142">色の選択ボタンをクリックして、 **[色]** ダイアログ ボックスを表示し、指定する色の RGB 値 (赤、緑、青) を MDX 式に挿入します。</span><span class="sxs-lookup"><span data-stu-id="816b6-142">Click the color selection button to display the **Color** dialog box and insert the RGB (Red-Green-Blue) value for a specified color into the MDX expression.</span></span> <span data-ttu-id="816b6-143">RGB 値の詳細については、「[FORE_COLOR および BACK_COLOR の内容 &#40;MDX&#41;](multidimensional-models/mdx/mdx-cell-properties-fore-color-and-back-color-contents.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="816b6-143">For more information about RGB values, see [FORE_COLOR and BACK_COLOR Contents &#40;MDX&#41;](multidimensional-models/mdx/mdx-cell-properties-fore-color-and-back-color-contents.md).</span></span>  
  
 <span data-ttu-id="816b6-144">**[背景色]**</span><span class="sxs-lookup"><span data-stu-id="816b6-144">**Back color**</span></span>  
 <span data-ttu-id="816b6-145">計算されるメンバーの背景色を指定するために、MDX 式を入力します。</span><span class="sxs-lookup"><span data-stu-id="816b6-145">Type the MDX expression that provides the background color of the calculated member.</span></span>  
  
 <span data-ttu-id="816b6-146">選択した要素を **[計算ツール]** ペインからこのオプションへドラッグして、選択した要素に対して MDX 構文を含めます。</span><span class="sxs-lookup"><span data-stu-id="816b6-146">Drag selected elements from the **Calculation Tools** pane to this option to include the MDX syntax for the selected element.</span></span>  
  
 <span data-ttu-id="816b6-147">色の選択ボタンをクリックして、 **[色]** ダイアログ ボックスを表示し、指定する色の RGB 値 (赤、緑、青) を MDX 式に挿入します。</span><span class="sxs-lookup"><span data-stu-id="816b6-147">Click the color selection button to display the **Color** dialog box and insert the RGB (Red-Green-Blue) value for a specified color into the MDX expression.</span></span> <span data-ttu-id="816b6-148">RGB 値の詳細については、「[FORE_COLOR および BACK_COLOR の内容 &#40;MDX&#41;](multidimensional-models/mdx/mdx-cell-properties-fore-color-and-back-color-contents.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="816b6-148">For more information about RGB values, see [FORE_COLOR and BACK_COLOR Contents &#40;MDX&#41;](multidimensional-models/mdx/mdx-cell-properties-fore-color-and-back-color-contents.md).</span></span>  
  
 <span data-ttu-id="816b6-149">**[フォントの式]**</span><span class="sxs-lookup"><span data-stu-id="816b6-149">**Font Expressions**</span></span>  
 <span data-ttu-id="816b6-150">展開して **[フォント名]**、 **[フォント サイズ]**、および **[フォント フラグ]** の各オプションを表示します。</span><span class="sxs-lookup"><span data-stu-id="816b6-150">Expand to view the **Font name**, **Font size**, and **Font flags** options.</span></span>  
  
 <span data-ttu-id="816b6-151">**フォント名**</span><span class="sxs-lookup"><span data-stu-id="816b6-151">**Font name**</span></span>  
 <span data-ttu-id="816b6-152">計算されるメンバーに使用するフォント名を指定するために、MDX 式を入力します。</span><span class="sxs-lookup"><span data-stu-id="816b6-152">Type the MDX expression that provides the name of the font used for the calculated member.</span></span>  
  
 <span data-ttu-id="816b6-153">選択した要素を **[計算ツール]** ペインからこのオプションへドラッグして、選択した要素に対して MDX 構文を含めます。</span><span class="sxs-lookup"><span data-stu-id="816b6-153">Drag selected elements from the **Calculation Tools** pane to this option to include the MDX syntax for the selected element.</span></span>  
  
 <span data-ttu-id="816b6-154">フォントの選択ボタンをクリックして、 **[フォント]** ダイアログ ボックスを表示し、指定するフォントのプロパティ値を MDX 式に挿入します。</span><span class="sxs-lookup"><span data-stu-id="816b6-154">Click the font selection button to display the **Font** dialog box and insert the property values for a specified font into the MDX expression.</span></span> <span data-ttu-id="816b6-155">プロパティ値の詳細については、「[プロパティ値の作成および使用 &#40;MDX&#41;](creating-and-using-property-values-mdx.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="816b6-155">For more information about property values, see [Creating and Using Property Values &#40;MDX&#41;](creating-and-using-property-values-mdx.md).</span></span>  
  
 <span data-ttu-id="816b6-156">**フォント サイズ**</span><span class="sxs-lookup"><span data-stu-id="816b6-156">**Font size**</span></span>  
 <span data-ttu-id="816b6-157">計算されたメンバーに使用するフォント サイズを指定するために、MDX 式を入力します。</span><span class="sxs-lookup"><span data-stu-id="816b6-157">Type the MDX expression that provides the size of the font used for the calculated member.</span></span>  
  
 <span data-ttu-id="816b6-158">選択した要素を **[計算ツール]** ペインからこのオプションへドラッグして、選択した要素に対して MDX 構文を含めます。</span><span class="sxs-lookup"><span data-stu-id="816b6-158">Drag selected elements from the **Calculation Tools** pane to this option to include the MDX syntax for the selected element.</span></span>  
  
 <span data-ttu-id="816b6-159">フォントの選択ボタンをクリックして、 **[フォント]** ダイアログ ボックスを表示し、指定するフォントのプロパティ値を MDX 式に挿入します。</span><span class="sxs-lookup"><span data-stu-id="816b6-159">Click the font selection button to display the **Font** dialog box and insert the property values for a specified font into the MDX expression.</span></span> <span data-ttu-id="816b6-160">プロパティ値の詳細については、「[プロパティ値の作成および使用 &#40;MDX&#41;](creating-and-using-property-values-mdx.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="816b6-160">For more information about property values, see [Creating and Using Property Values &#40;MDX&#41;](creating-and-using-property-values-mdx.md).</span></span>  
  
 <span data-ttu-id="816b6-161">**[フォント フラグ]**</span><span class="sxs-lookup"><span data-stu-id="816b6-161">**Font flags**</span></span>  
 <span data-ttu-id="816b6-162">下線、太字など、計算されるメンバーに使用するフォントのフォント フラグを含む、ビットマップ形式の値を指定するために、MDX 式を入力します。</span><span class="sxs-lookup"><span data-stu-id="816b6-162">Type the MDX expression that provides the bitmapped value containing the font flags, such as underline or bold, of the font used for the calculated member.</span></span>  
  
 <span data-ttu-id="816b6-163">選択した要素を **[計算ツール]** ペインからこのオプションへドラッグして、選択した要素に対して MDX 構文を含めます。</span><span class="sxs-lookup"><span data-stu-id="816b6-163">Drag selected elements from the **Calculation Tools** pane to this option to include the MDX syntax for the selected element.</span></span>  
  
 <span data-ttu-id="816b6-164">フォントの選択ボタンをクリックして、 **[フォント]** ダイアログ ボックスを表示し、指定するフォントのプロパティ値を MDX 式に挿入します。</span><span class="sxs-lookup"><span data-stu-id="816b6-164">Click the font selection button to display the **Font** dialog box and insert the property values for a specified font into the MDX expression.</span></span> <span data-ttu-id="816b6-165">プロパティ値の詳細については、「[プロパティ値の作成および使用 &#40;MDX&#41;](creating-and-using-property-values-mdx.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="816b6-165">For more information about property values, see [Creating and Using Property Values &#40;MDX&#41;](creating-and-using-property-values-mdx.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="816b6-166">参照</span><span class="sxs-lookup"><span data-stu-id="816b6-166">See Also</span></span>  
 <span data-ttu-id="816b6-167">[Custom](multidimensional-models-olap-logical-cube-objects/calculations.md) </span><span class="sxs-lookup"><span data-stu-id="816b6-167">[Calculations](multidimensional-models-olap-logical-cube-objects/calculations.md) </span></span>  
 <span data-ttu-id="816b6-168">[計算されるメンバーの作成](multidimensional-models/create-calculated-members.md) </span><span class="sxs-lookup"><span data-stu-id="816b6-168">[Create Calculated Members](multidimensional-models/create-calculated-members.md) </span></span>  
 <span data-ttu-id="816b6-169">[キューブデザイナー &#40;Analysis Services-多次元データ&#41;](cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="816b6-169">[Cube Designer &#40;Analysis Services - Multidimensional Data&#41;](cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="816b6-170">[キューブデザイナーの計算 &#40;&#41; &#40;Analysis Services-多次元データ&#41;](calculations-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="816b6-170">[Calculations &#40;Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](calculations-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="816b6-171">[ツールバー &#40;キューブデザイナーの [計算] タブ&#41; &#40;Analysis Services-多次元データ&#41;](toolbar-calculations-tab-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="816b6-171">[Toolbar &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](toolbar-calculations-tab-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="816b6-172">[[スクリプトオーガナイザー &#40;計算] タブ、キューブデザイナー&#41; &#40;Analysis Services-多次元データ&#41;](script-organizer-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="816b6-172">[Script Organizer &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](script-organizer-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="816b6-173">[計算ツール &#40;[計算] タブ、キューブデザイナー&#41; &#40;Analysis Services-多次元データ&#41;](calculation-tools-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="816b6-173">[Calculation Tools &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](calculation-tools-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="816b6-174">[名前付きセットフォームエディター &#40;の [計算] タブ、キューブデザイナー&#41; &#40;Analysis Services-多次元データ&#41;](named-set-form-editor-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="816b6-174">[Named Set Form Editor &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](named-set-form-editor-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="816b6-175">[スクリプトエディターの [&#40;の計算] タブ、キューブデザイナー&#41; &#40;Analysis Services-多次元データ&#41;](script-editor-calculations-cube-designer-analysis-services-multidimensional-data.md)</span><span class="sxs-lookup"><span data-stu-id="816b6-175">[Script Editor &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](script-editor-calculations-cube-designer-analysis-services-multidimensional-data.md)</span></span>  
  
  
