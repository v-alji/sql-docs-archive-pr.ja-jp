---
title: 画像をゲージのポインターとして指定する (レポートビルダーと SSRS) |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 9d73b3c3-a068-4868-a2be-0cd261b6e92b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c694cdb90fb668c43eb7e9971bba967bad8dd9cb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719455"
---
# <a name="specify-an-image-as-a-pointer-on-a-gauge-report-builder-and-ssrs"></a><span data-ttu-id="ced21-102">画像をゲージのポインターとして指定する (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="ced21-102">Specify an Image as a Pointer on a Gauge (Report Builder and SSRS)</span></span>
  <span data-ttu-id="ced21-103">ゲージには 3 つの組み込みスタイルが用意されており、これらを使用してポインターの外観をカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="ced21-103">The gauge contains three built-in styles that can be used to customize the appearance of the pointer.</span></span> <span data-ttu-id="ced21-104">放射状ゲージには、針、マーカー、およびバーの 3 種類の組み込みスタイルがあります。</span><span class="sxs-lookup"><span data-stu-id="ced21-104">For a radial gauge, the built in styles are: Needle, Marker and Bar.</span></span> <span data-ttu-id="ced21-105">線形ゲージには、マーカー、バー、および温度計の 3 種類の組み込みスタイルがあります。</span><span class="sxs-lookup"><span data-stu-id="ced21-105">For a linear gauge, the built-in styles are Marker, Bar, and Thermometer.</span></span> <span data-ttu-id="ced21-106">独自のポインターが必要な場合は、自分で作成した画像をポインターとして使用できます。</span><span class="sxs-lookup"><span data-stu-id="ced21-106">If a unique pointer is required, the user can create and specify an image which can be used as a fully functional pointer.</span></span>  
  
 <span data-ttu-id="ced21-107">ポインターの画像を指定する場合、その画像は次の仕様を満たしている必要があります。</span><span class="sxs-lookup"><span data-stu-id="ced21-107">When you are specifying an image for the pointer, your image must have the following specifications:</span></span>  
  
-   <span data-ttu-id="ced21-108">ポインターの原点または回転の中心は、画像の上部にある必要があります。</span><span class="sxs-lookup"><span data-stu-id="ced21-108">The origin of the pointer, or center of rotation, must be at the top of the image.</span></span>  
  
-   <span data-ttu-id="ced21-109">ポインターの端は下向きである必要があります。</span><span class="sxs-lookup"><span data-stu-id="ced21-109">The end of the pointer must be pointing down.</span></span>  
  
 <span data-ttu-id="ced21-110">ポインターは不規則な形状なので、画像の不必要な部分を隠すために透過色を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ced21-110">Since the pointer is an irregular shape, you will need to specify a transparency color to hide the unnecessary portions of the image.</span></span> <span data-ttu-id="ced21-111">指定した色はゲージ上で表示されないので、通常はゲージ上に使用されない色を透過色として使用してください。</span><span class="sxs-lookup"><span data-stu-id="ced21-111">Consider using a color that would not normally be shown on the gauge as the transparency color, since the colors specified will not appear on the gauge.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../includes/ssrbrddup-md.md)]  
  
### <a name="to-specify-an-image-as-a-pointer-on-the-gauge"></a><span data-ttu-id="ced21-112">画像をゲージのポインターとして指定するには</span><span class="sxs-lookup"><span data-stu-id="ced21-112">To specify an image as a pointer on the gauge</span></span>  
  
1.  <span data-ttu-id="ced21-113">[デザイン] ビューでゲージのポインターをクリックします。</span><span class="sxs-lookup"><span data-stu-id="ced21-113">In Design view, click the pointer of the gauge.</span></span>  
  
2.  <span data-ttu-id="ced21-114">Optionalゲージにポインターが存在しない場合は、ゲージを右クリックし、[**ポインターの追加**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="ced21-114">(Optional) If no pointer exists on the gauge, right-click on the gauge and select **Add Pointer**.</span></span> <span data-ttu-id="ced21-115">ポインターがゲージに追加されます。</span><span class="sxs-lookup"><span data-stu-id="ced21-115">A pointer is added to the gauge.</span></span>  
  
3.  <span data-ttu-id="ced21-116">リボンの [**挿入**] タブをクリックし、[イメージ] アイコンをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="ced21-116">Click the **Insert** tab on the ribbon and double-click the image icon.</span></span> <span data-ttu-id="ced21-117">**[画像のプロパティ]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ced21-117">The **Image Properties** dialog box opens.</span></span>  
  
4.  <span data-ttu-id="ced21-118">画像をレポートに追加します。</span><span class="sxs-lookup"><span data-stu-id="ced21-118">Add an image to your report.</span></span> <span data-ttu-id="ced21-119">詳細については、「[レポート &#40;レポートビルダーおよび SSRS&#41;に画像を埋め込む](report-design/embed-an-image-in-a-report-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ced21-119">For more information, see [Embed an Image in a Report &#40;Report Builder and SSRS&#41;](report-design/embed-an-image-in-a-report-report-builder-and-ssrs.md).</span></span>  
  
5.  <span data-ttu-id="ced21-120">プロパティ ペインを開きます。</span><span class="sxs-lookup"><span data-stu-id="ced21-120">Open the Properties pane.</span></span>  
  
6.  <span data-ttu-id="ced21-121">デザイン画面で、ポインターをクリックします。</span><span class="sxs-lookup"><span data-stu-id="ced21-121">On the design surface, click on the pointer.</span></span> <span data-ttu-id="ced21-122">ポインターのプロパティがプロパティ ペインに表示されます。</span><span class="sxs-lookup"><span data-stu-id="ced21-122">The properties for the pointer are displayed in the Properties pane.</span></span>  
  
7.  <span data-ttu-id="ced21-123">[ポインターイメージ] ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="ced21-123">Expand the PointerImage node.</span></span>  
  
8.  <span data-ttu-id="ced21-124">[**ソース**] で、ドロップダウンリストから [**埋め込み**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="ced21-124">In **Source**, select **Embedded** from the drop-down list.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ced21-125">画像がデータベースまたは Web に保存されている場合は、このプロパティに適切なオプションを指定できます。</span><span class="sxs-lookup"><span data-stu-id="ced21-125">If your image is stored in the database or on the web, you can specify the appropriate option for this property.</span></span> <span data-ttu-id="ced21-126">詳細については、「 [[画像のプロパティ] ダイアログボックス」、「全般 &#40;レポートビルダー」、および「SSRS&#41;](../../2014/reporting-services/image-properties-dialog-box-general-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ced21-126">For more information, see [Image Properties Dialog Box, General &#40;Report Builder and SSRS&#41;](../../2014/reporting-services/image-properties-dialog-box-general-report-builder-and-ssrs.md).</span></span>  
  
9. <span data-ttu-id="ced21-127">[**値**] で、ドロップダウンリストから画像の名前を選択します。</span><span class="sxs-lookup"><span data-stu-id="ced21-127">In **Value**, select the name of your image from the drop-down list.</span></span>  
  
10. <span data-ttu-id="ced21-128">**TransparentColor**で、画像から削除する色の値を選択します。</span><span class="sxs-lookup"><span data-stu-id="ced21-128">In **TransparentColor**, pick a color value that you want to remove from the image.</span></span> <span data-ttu-id="ced21-129">これで、ゲージのポインターのシームレスな外観が作成されます。</span><span class="sxs-lookup"><span data-stu-id="ced21-129">This will create a seamless appearance for the pointer in the gauge.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ced21-130">参照</span><span class="sxs-lookup"><span data-stu-id="ced21-130">See Also</span></span>  
 <span data-ttu-id="ced21-131">[ゲージのポインターの書式設定 &#40;レポートビルダーと SSRS&#41;](report-design/formatting-pointers-on-a-gauge-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ced21-131">[Formatting Pointers on a Gauge &#40;Report Builder and SSRS&#41;](report-design/formatting-pointers-on-a-gauge-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="ced21-132">[ゲージをレポートに追加する &#40;レポートビルダーと SSRS&#41;](report-design/add-a-gauge-to-a-report-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ced21-132">[Add a Gauge to a Report &#40;Report Builder and SSRS&#41;](report-design/add-a-gauge-to-a-report-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="ced21-133">[レポートビルダーおよび SSRS&#41;&#40;線、色、および画像の書式設定](report-design/images-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ced21-133">[Formatting Lines, Colors, and Images &#40;Report Builder and SSRS&#41;](report-design/images-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="ced21-134">ゲージ (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="ced21-134">Gauges &#40;Report Builder and SSRS&#41;</span></span>](report-design/gauges-report-builder-and-ssrs.md)  
  
  
