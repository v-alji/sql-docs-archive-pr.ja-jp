---
title: '[色の選択] ダイアログボックス (レポートビルダーおよび SSRS) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.selectcolor.f1
- "10090"
helpviewer_keywords:
- Select Color dialog box
ms.assetid: ac7089a3-5c7b-4f53-8348-180610e86da2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a2526b755fd4e08faf79998d351e824371fac2f8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739144"
---
# <a name="select-color-dialog-box-report-builder-and-ssrs"></a><span data-ttu-id="d2af2-102">[色の選択] ダイアログ ボックス (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="d2af2-102">Select Color Dialog Box (Report Builder and SSRS)</span></span>
  <span data-ttu-id="d2af2-103">**[色の選択]** ダイアログ ボックスを使用すると、データ領域やテキスト ボックスにある 1 つまたは複数のセルの背景色や、グラフの色のオプションを指定できます。</span><span class="sxs-lookup"><span data-stu-id="d2af2-103">Use the **Select Color** dialog box to specify color options for the background of a single cell or multiple cells within a data region or a text box, or for a chart.</span></span>  
  
## <a name="options"></a><span data-ttu-id="d2af2-104">Options</span><span class="sxs-lookup"><span data-stu-id="d2af2-104">Options</span></span>  
 <span data-ttu-id="d2af2-105">**[カラー セレクター]**</span><span class="sxs-lookup"><span data-stu-id="d2af2-105">**Color selector**</span></span>  
 <span data-ttu-id="d2af2-106">色の選択方法を指定する 3 つのオプションから選択します。</span><span class="sxs-lookup"><span data-stu-id="d2af2-106">Choose from three options that specify how you want to select colors:</span></span>  
  
-   <span data-ttu-id="d2af2-107">**ピッカー - カラー サークル** 色合い/鮮やかさ/明るさ (HSB) の色値を使用して色を選択します。</span><span class="sxs-lookup"><span data-stu-id="d2af2-107">**Picker - Color circle** Choose a color using Hue/Saturation/Brightness (HSB) color values.</span></span>  
  
-   <span data-ttu-id="d2af2-108">**ピッカー - カラー スクエア** 赤/緑/青 (RGB) の色値を使用して色を選択します。</span><span class="sxs-lookup"><span data-stu-id="d2af2-108">**Picker - Color square** Choose a color using Red/Green/Blue (RGB) color values.</span></span>  
  
-   <span data-ttu-id="d2af2-109">**パレット - 標準色** 定義済みの色値の一覧から色を選択します。</span><span class="sxs-lookup"><span data-stu-id="d2af2-109">**Palette - Standard colors** Choose a color from a predefined list of color values.</span></span>  
  
 <span data-ttu-id="d2af2-110">**[カラー サークル]**</span><span class="sxs-lookup"><span data-stu-id="d2af2-110">**Color circle**</span></span>  
 <span data-ttu-id="d2af2-111">HSB 値は円筒座標系に対応しているため、HSB 色に使用します。</span><span class="sxs-lookup"><span data-stu-id="d2af2-111">Use for HSB colors because HSB values are mapped onto a cylindrical coordinate system.</span></span> <span data-ttu-id="d2af2-112">色合いは実際の色、鮮やかさは色の純度、明るさは相対的な明るさや暗さを表します。</span><span class="sxs-lookup"><span data-stu-id="d2af2-112">Hue is the actual color, saturation is purity of color, brightness is relative brightness or darkness.</span></span>  
  
 <span data-ttu-id="d2af2-113">色を選択すると、円の中心で色が決まります。</span><span class="sxs-lookup"><span data-stu-id="d2af2-113">When you pick a color, the center of the circle determines the color.</span></span> <span data-ttu-id="d2af2-114">色合いを変更するには、カラー スライダーを使用します。</span><span class="sxs-lookup"><span data-stu-id="d2af2-114">Use the color slider to change the hue.</span></span> <span data-ttu-id="d2af2-115">X 座標と Y 座標はそれぞれ、鮮やかさの値と明るさの値を表します。</span><span class="sxs-lookup"><span data-stu-id="d2af2-115">The x and y coordinates represent saturation and brightness values respectively.</span></span>  
  
 <span data-ttu-id="d2af2-116">**[カラー スクエア]**</span><span class="sxs-lookup"><span data-stu-id="d2af2-116">**Color square**</span></span>  
 <span data-ttu-id="d2af2-117">RGB 値はデカルト座標系に対応しているため、RGB 色に使用します。</span><span class="sxs-lookup"><span data-stu-id="d2af2-117">Use for RGB colors because RGB values are mapped to a Cartesian coordinate system.</span></span> <span data-ttu-id="d2af2-118">R は赤、G は緑、B は青の値を表します。</span><span class="sxs-lookup"><span data-stu-id="d2af2-118">R is the value for Red, G is the value for Green, B is the value for Blue.</span></span>  
  
 <span data-ttu-id="d2af2-119">色を選択すると、正方形の中心で色が決まります。</span><span class="sxs-lookup"><span data-stu-id="d2af2-119">When you pick a color, the center of the square determines the color.</span></span> <span data-ttu-id="d2af2-120">カラー スライダーを使用して、選択した色の範囲を変更します。</span><span class="sxs-lookup"><span data-stu-id="d2af2-120">Use the color slider to change the range of the chosen color.</span></span> <span data-ttu-id="d2af2-121">X 座標と Y 座標は、残りの 2 つの色を表します。</span><span class="sxs-lookup"><span data-stu-id="d2af2-121">The x and y coordinates represent the other two colors.</span></span> <span data-ttu-id="d2af2-122">たとえば、緑を選択した場合、スライダーでは緑の値の範囲が示され、X 座標と Y 座標では赤と青の値がそれぞれ示されます。</span><span class="sxs-lookup"><span data-stu-id="d2af2-122">For example, if you pick green, the slider shows the range of green values, the x and y coordinates represent red and blue values respectively.</span></span>  
  
 <span data-ttu-id="d2af2-123">**[パレットの標準色]**</span><span class="sxs-lookup"><span data-stu-id="d2af2-123">**Standard palette color**</span></span>  
 <span data-ttu-id="d2af2-124">列挙体の名前付きの色に使用し [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] `KnownColor` ます。</span><span class="sxs-lookup"><span data-stu-id="d2af2-124">Use for named colors from the [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] `KnownColor` enumeration.</span></span>  
  
 <span data-ttu-id="d2af2-125">**[カラー システム]**</span><span class="sxs-lookup"><span data-stu-id="d2af2-125">**Color system**</span></span>  
 <span data-ttu-id="d2af2-126">RGB 色または HSB 色を指定します。</span><span class="sxs-lookup"><span data-stu-id="d2af2-126">Specify RGB or HSB colors.</span></span> <span data-ttu-id="d2af2-127">ここで行う選択により、RGB 値または HSB 値が表示されるように画面が変更されます。これらの値は、 **[カラー セレクター]** のカラー サークルまたはカラー スクエアを使用する際に対話的に更新されます。</span><span class="sxs-lookup"><span data-stu-id="d2af2-127">This choice changes the display to show RGB or HSB values, which are updated interactively when you use a color circle or color square for the **Color selector**.</span></span>  
  
 <span data-ttu-id="d2af2-128">色に透明度の値を指定できる場合は、いくつかのプロパティで **[アルファ]** 値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="d2af2-128">The **Alpha** value displays for some properties when a color can include a transparency value.</span></span> <span data-ttu-id="d2af2-129">たとえば、グラフの系列を塗りつぶす場合などがこれに該当します。</span><span class="sxs-lookup"><span data-stu-id="d2af2-129">For example, Chart series fill.</span></span> <span data-ttu-id="d2af2-130">透明度をサポートしていないプロパティでは、この値が無効になっています。</span><span class="sxs-lookup"><span data-stu-id="d2af2-130">For properties that do not support transparency, this value is disabled.</span></span>  
  
 <span data-ttu-id="d2af2-131">**赤**</span><span class="sxs-lookup"><span data-stu-id="d2af2-131">**Red**</span></span>  
 <span data-ttu-id="d2af2-132">RGB 色の赤の要素を表す 10 進値です。</span><span class="sxs-lookup"><span data-stu-id="d2af2-132">The decimal value for the red part of the RGB color.</span></span> <span data-ttu-id="d2af2-133">スピン ボックスを使用して値を変更するか、0 ～ 255 の値を入力します。</span><span class="sxs-lookup"><span data-stu-id="d2af2-133">Use the spin box to change the value or type in a value between 0 and 255.</span></span>  
  
 <span data-ttu-id="d2af2-134">**緑**</span><span class="sxs-lookup"><span data-stu-id="d2af2-134">**Green**</span></span>  
 <span data-ttu-id="d2af2-135">RGB 色の緑の要素を表す 10 進値です。</span><span class="sxs-lookup"><span data-stu-id="d2af2-135">The decimal value for the green part of the RGB color.</span></span> <span data-ttu-id="d2af2-136">スピン ボックスを使用して値を変更するか、0 ～ 255 の値を入力します。</span><span class="sxs-lookup"><span data-stu-id="d2af2-136">Use the spin box to change the value or type in a value between 0 and 255.</span></span>  
  
 <span data-ttu-id="d2af2-137">**青**</span><span class="sxs-lookup"><span data-stu-id="d2af2-137">**Blue**</span></span>  
 <span data-ttu-id="d2af2-138">RGB 色の青の要素を表す 10 進値です。</span><span class="sxs-lookup"><span data-stu-id="d2af2-138">The decimal value for the blue part of the RGB color.</span></span> <span data-ttu-id="d2af2-139">スピン ボックスを使用して値を変更するか、0 ～ 255 の値を入力します。</span><span class="sxs-lookup"><span data-stu-id="d2af2-139">Use the spin box to change the value or type in a value between 0 and 255.</span></span>  
  
 <span data-ttu-id="d2af2-140">**[アルファ]**</span><span class="sxs-lookup"><span data-stu-id="d2af2-140">**Alpha**</span></span>  
 <span data-ttu-id="d2af2-141">アルファ (色の透明度) を表す 10 進値です。</span><span class="sxs-lookup"><span data-stu-id="d2af2-141">The decimal value for the alpha or transparency part of the color.</span></span> <span data-ttu-id="d2af2-142">この値が有効な場合は、スライダーを使用して透明度を調整できます。</span><span class="sxs-lookup"><span data-stu-id="d2af2-142">When this value is enabled, you can use the slider switch to adjust the degree of transparency you want.</span></span>  
  
 <span data-ttu-id="d2af2-143">**Hue**</span><span class="sxs-lookup"><span data-stu-id="d2af2-143">**Hue**</span></span>  
 <span data-ttu-id="d2af2-144">HSB 色の色合いを表す 10 進値です。</span><span class="sxs-lookup"><span data-stu-id="d2af2-144">The decimal value for the hue of the HSB color.</span></span> <span data-ttu-id="d2af2-145">スピン ボックスを使用して値を変更するか、0 ～ 255 の値を入力します。</span><span class="sxs-lookup"><span data-stu-id="d2af2-145">Use the spin box to change the value or type in a value between 0 and 255.</span></span>  
  
 <span data-ttu-id="d2af2-146">**[鮮やかさ]**</span><span class="sxs-lookup"><span data-stu-id="d2af2-146">**Saturation**</span></span>  
 <span data-ttu-id="d2af2-147">HSB 色の鮮やかさを表す 10 進値です。</span><span class="sxs-lookup"><span data-stu-id="d2af2-147">The decimal value for the saturation of the HSB color.</span></span> <span data-ttu-id="d2af2-148">スピン ボックスを使用して値を変更するか、0 ～ 255 の値を入力します。</span><span class="sxs-lookup"><span data-stu-id="d2af2-148">Use the spin box to change the value or type in a value between 0 and 255.</span></span>  
  
 <span data-ttu-id="d2af2-149">**明るさ**</span><span class="sxs-lookup"><span data-stu-id="d2af2-149">**Brightness**</span></span>  
 <span data-ttu-id="d2af2-150">HSB 色の明るさを表す 10 進値です。</span><span class="sxs-lookup"><span data-stu-id="d2af2-150">The decimal value for the brightness of the HSB color.</span></span> <span data-ttu-id="d2af2-151">スピン ボックスを使用して値を変更するか、0 ～ 255 の値を入力します。</span><span class="sxs-lookup"><span data-stu-id="d2af2-151">Use the spin box to change the value or type in a value between 0 and 255.</span></span>  
  
 <span data-ttu-id="d2af2-152">**色のサンプル**</span><span class="sxs-lookup"><span data-stu-id="d2af2-152">**Color sample**</span></span>  
 <span data-ttu-id="d2af2-153">ペインの左半分に現在の色が表示され、ペインの右半分に選択している新しい色が対話的に表示されます。</span><span class="sxs-lookup"><span data-stu-id="d2af2-153">Shows the current color on the left half of the pane and interactively shows the new color you are choosing on the right half of the pane.</span></span> <span data-ttu-id="d2af2-154">既定の色がない場合は、ペインの左半分は白くなります。</span><span class="sxs-lookup"><span data-stu-id="d2af2-154">If there is no default color, the left half of the pane is white.</span></span> <span data-ttu-id="d2af2-155">ほとんどの RDL のプロパティには既定の色がありません。</span><span class="sxs-lookup"><span data-stu-id="d2af2-155">Most RDL properties have no default color.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2af2-156">参照</span><span class="sxs-lookup"><span data-stu-id="d2af2-156">See Also</span></span>  
 <span data-ttu-id="d2af2-157">[レポートアイテムの書式設定 &#40;レポートビルダーと SSRS&#41;](report-design/formatting-report-items-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="d2af2-157">[Formatting Report Items &#40;Report Builder and SSRS&#41;](report-design/formatting-report-items-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="d2af2-158">テキストとプレースホルダーの書式設定 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="d2af2-158">Formatting Text and Placeholders &#40;Report Builder and SSRS&#41;</span></span>](report-design/formatting-text-and-placeholders-report-builder-and-ssrs.md)  
  
  
