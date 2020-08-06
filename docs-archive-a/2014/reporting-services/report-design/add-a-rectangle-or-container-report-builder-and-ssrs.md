---
title: 四角形またはコンテナーの追加 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10061"
- sql12.rtp.rptdesigner.rectangleproperties.general.f1
ms.assetid: f905c35f-754d-4d02-80f3-85e29ddda826
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5fddda2f02b9f370d9742ae6add5bae444f8f55f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631549"
---
# <a name="add-a-rectangle-or-container-report-builder-and-ssrs"></a><span data-ttu-id="47b39-102">四角形またはコンテナーの追加 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="47b39-102">Add a Rectangle or Container (Report Builder and SSRS)</span></span>
  <span data-ttu-id="47b39-103">グラフィック要素によってレポートの領域を分けたり、レポートの領域を強調したり、1 つ以上のレポート アイテムに背景を提供したりするには、レポートに四角形を追加します。</span><span class="sxs-lookup"><span data-stu-id="47b39-103">Add a rectangle to your report when you want a graphical element to separate areas of the report, emphasize areas of a report, or provide a background for one or more report items.</span></span> <span data-ttu-id="47b39-104">また、四角形をコンテナーとして使用すると、レポートでのデータ領域のレンダリング方法を制御することもできます。</span><span class="sxs-lookup"><span data-stu-id="47b39-104">Rectangles are also used as containers to help control the way data regions render in a report.</span></span> <span data-ttu-id="47b39-105">四角形の外観は、背景や罫線の色など、四角形のプロパティを編集することによりカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="47b39-105">You can customize the appearance of a rectangle by editing rectangle properties such as the background and border colors.</span></span> <span data-ttu-id="47b39-106">四角形をコンテナーとして使用する方法について詳しくは、「[四角形と線 &#40;レポート ビルダーおよび SSRS&#41;](rectangles-and-lines-report-builder-and-ssrs.md)」および「[マトリックスとグラフでの同じデータの表示 &#40;レポート ビルダー&#41;](display-the-same-data-on-a-matrix-and-a-chart-report-builder.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="47b39-106">For more information about using a rectangle as a container, see [Rectangles and Lines &#40;Report Builder and SSRS&#41;](rectangles-and-lines-report-builder-and-ssrs.md) and [Display the Same Data on a Matrix and a Chart &#40;Report Builder&#41;](display-the-same-data-on-a-matrix-and-a-chart-report-builder.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-rectangle"></a><span data-ttu-id="47b39-107">四角形を追加するには</span><span class="sxs-lookup"><span data-stu-id="47b39-107">To add a rectangle</span></span>  
  
1.  <span data-ttu-id="47b39-108">**[挿入]** タブの **[レポート アイテム]** グループで **[四角形]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="47b39-108">On the **Insert** tab, in the **Report Items** group, click **Rectangle.**</span></span>  
  
2.  <span data-ttu-id="47b39-109">デザイン画面で、四角形の左上隅となる位置をクリックし、四角形の右下隅となる位置までドラッグします。</span><span class="sxs-lookup"><span data-stu-id="47b39-109">On the design surface, click the location where you want the upper left corner of the rectangle, and drag to where you want the lower-right corner.</span></span>  
  
     <span data-ttu-id="47b39-110">カーソルを移動すると、デザイン画面の他のオブジェクトと並んだときに "スナップ線" が表示されます。</span><span class="sxs-lookup"><span data-stu-id="47b39-110">Note that as you move the cursor, "snap lines" appear as the cursor lines up with other objects on the design surface.</span></span> <span data-ttu-id="47b39-111">これらのスナップ線はオブジェクトを配置する場合に役に立ちます。</span><span class="sxs-lookup"><span data-stu-id="47b39-111">These help you if you want objects to be aligned.</span></span>  
  
### <a name="to-create-a-container"></a><span data-ttu-id="47b39-112">コンテナーを作成するには</span><span class="sxs-lookup"><span data-stu-id="47b39-112">To create a container</span></span>  
  
1.  <span data-ttu-id="47b39-113">四角形レポート アイテムをレポートに追加します。</span><span class="sxs-lookup"><span data-stu-id="47b39-113">Add a rectangle report item to the report.</span></span>  
  
2.  <span data-ttu-id="47b39-114">レポート アイテムを四角形にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="47b39-114">Drag other report items into the rectangle.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="47b39-115">四角形はアイテムの単なるコンテナーで、アイテムを四角形内で作成するか四角形にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="47b39-115">A rectangle is only a container for items that you either create in the rectangle or drag into the rectangle.</span></span> <span data-ttu-id="47b39-116">デザイン画面に既に存在するアイテムの周囲に四角形を描画した場合、四角形はコンテナーとして機能しません。</span><span class="sxs-lookup"><span data-stu-id="47b39-116">If you draw a rectangle around an item that already exists on the design surface, the rectangle will not act as its container.</span></span>  
  
### <a name="to-change-rectangle-properties-such-as-color-style-or-weight"></a><span data-ttu-id="47b39-117">色、スタイル、太さなどの四角形のプロパティを変更するには</span><span class="sxs-lookup"><span data-stu-id="47b39-117">To change rectangle properties such as color, style, or weight</span></span>  
  
1.  <span data-ttu-id="47b39-118">四角形を選択し、[ホーム] タブの **[罫線]** セクションで線の色、スタイル、または太さのオプションをクリックします。</span><span class="sxs-lookup"><span data-stu-id="47b39-118">Select the rectangle, and then click the line color, style, or weight options in the **Border** section of the Home tab.</span></span>  
  
2.  <span data-ttu-id="47b39-119">**[罫線]** ボタンの横にある矢印をクリックして、四角形のどの辺を変更するかを指定します。</span><span class="sxs-lookup"><span data-stu-id="47b39-119">Click the arrow next to the **Border** button to determine which sides of the rectangle to change.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="47b39-120">線のスタイルを [**二重**線] に設定し、線の幅が 1 1/2 pt または狭い場合は、レポートをレポートビルダー、レポートデザイナー、またはレポートマネージャーで実行すると、線が二重に表示されないことがあります。</span><span class="sxs-lookup"><span data-stu-id="47b39-120">If you set the line style to **Double** and the line width is 1 1/2 pt or narrower, the line may not appear double when you run the report in Report Builder, Report Designer, or Report Manager.</span></span> <span data-ttu-id="47b39-121">レポートを他の形式 (Microsoft Word、Acrobat PDF など) にエクスポートすると、二重に表示されます。</span><span class="sxs-lookup"><span data-stu-id="47b39-121">It will appear double when you export the report to other formats such as Microsoft Word and Acrobat PDF.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47b39-122">参照</span><span class="sxs-lookup"><span data-stu-id="47b39-122">See Also</span></span>  
 <span data-ttu-id="47b39-123">[四角形と線 &#40;レポート ビルダーおよび SSRS&#41;](rectangles-and-lines-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="47b39-123">[Rectangles and Lines &#40;Report Builder and SSRS&#41;](rectangles-and-lines-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="47b39-124">レンダリングの動作 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="47b39-124">Rendering Behaviors &#40;Report Builder  and SSRS&#41;</span></span>](rendering-behaviors-report-builder-and-ssrs.md)  
  
  
