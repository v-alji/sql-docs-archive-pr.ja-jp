---
title: 線、色、および画像の書式設定 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.textboxproperties.border.f1
- "10502"
- "10094"
- sql12.rtp.rptdesigner.pictureproperties.border.f1
- "10063"
- sql12.rtp.rptdesigner.rectangleproperties.border.f1
- "10055"
- sql12.rtp.rptdesigner.subreportproperties.border.f1
- "10126"
- sql12.rtp.rptdesigner.shared.borderdv.f1
- "10066"
- sql12.rtp.rptdesigner.reportbody.border.f1
ms.assetid: 0f5f0d2a-9537-4152-b441-b40d7f04cf4c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 681ff6b46f692804aef5c7cbbc16e5abe99dbb2d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711698"
---
# <a name="formatting-lines-colors-and-images-report-builder-and-ssrs"></a><span data-ttu-id="9e2ef-102">線、色、および画像の書式設定 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="9e2ef-102">Formatting Lines, Colors, and Images (Report Builder and SSRS)</span></span>
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="9e2ef-103">には、線、色、データ領域、画像、その他のレポート アイテムの書式を設定する機能が用意されています。</span><span class="sxs-lookup"><span data-stu-id="9e2ef-103">gives you the ability to format lines, colors, data regions, images, and other report items.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="borders-lines-and-gridlines"></a><span data-ttu-id="9e2ef-104">罫線、線、グリッド線</span><span class="sxs-lookup"><span data-stu-id="9e2ef-104">Borders, Lines and Gridlines</span></span>  
 <span data-ttu-id="9e2ef-105">罫線、線、およびグリッド線を使用すると、ページ上のアイテムを視覚的に結合できるため、レポートを表示するユーザーにとってレポートの内容が読みやすくなります。</span><span class="sxs-lookup"><span data-stu-id="9e2ef-105">Borders, lines, and gridlines can visually tie items together on the page and help your report readers easily read the contents of the report.</span></span> <span data-ttu-id="9e2ef-106">定義済みの罫線スタイルを使用すると、テキスト ボックス、テキスト ボックスのグループ、画像などの周囲に簡単に罫線を追加できます。</span><span class="sxs-lookup"><span data-stu-id="9e2ef-106">Using the predefined border styles, you can quickly add a border around a text box, a group of text boxes, or an image.</span></span> <span data-ttu-id="9e2ef-107">また、罫線、線、グリッド線のスタイル、幅、および色を変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="9e2ef-107">In addition, you can change the style, width, and color for the borders, lines, and gridlines.</span></span> <span data-ttu-id="9e2ef-108">罫線は、選択したアイテム全体の周り、またはアイテムの端に沿って (テキスト ボックスの下辺に沿った罫線など) 追加されます。</span><span class="sxs-lookup"><span data-stu-id="9e2ef-108">Borders are added around the entire item selected or around a border along an edge of the item, for example, a border along the bottom of a text box.</span></span>  
  
 <span data-ttu-id="9e2ef-109">テキスト ボックス内、レポート レイアウト内、または画像の周囲の罫線とグリッド線を書式設定するには、レポート アイテムの **プロパティ** ダイアログ ボックスの **[罫線]** タブを使用します。</span><span class="sxs-lookup"><span data-stu-id="9e2ef-109">To format borders and gridlines in a text box, report layout, or around an image, use the **Border** tab of the report item's **Properties** dialog box.</span></span> <span data-ttu-id="9e2ef-110">たとえば、画像の周りに罫線を追加するには、画像を右クリックし、 **[画像のプロパティ]** ダイアログ ボックスで **[罫線]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9e2ef-110">For example, if you want to add a border around an image, right-click the image and then in the **Image Properties** dialog box, click **Border**.</span></span>  
  
 <span data-ttu-id="9e2ef-111">標準の罫線枠だけでなく、追加の罫線枠もグラフに適用できます。</span><span class="sxs-lookup"><span data-stu-id="9e2ef-111">In addition to the standard border frames, additional border frames can be applied to charts.</span></span> <span data-ttu-id="9e2ef-112">詳細については、「[グラフへの枠線の追加 &#40;レポート ビルダーおよび SSRS&#41;](add-a-border-frame-to-a-chart-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9e2ef-112">For more information, see [Add a Border Frame to a Chart &#40;Report Builder and SSRS&#41;](add-a-border-frame-to-a-chart-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="9e2ef-113">罫線をレポート自体に追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="9e2ef-113">You can also add a border to the report itself.</span></span> <span data-ttu-id="9e2ef-114">詳細については、「 [レポートへの罫線の追加 &#40;レポート ビルダーおよび SSRS&#41;](add-a-border-to-a-report-report-builder-and-ssrs.md)の詳細を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9e2ef-114">For more information, see [Add a Border to a Report &#40;Report Builder and SSRS&#41;](add-a-border-to-a-report-report-builder-and-ssrs.md).</span></span>  
  
## <a name="applying-background-colors"></a><span data-ttu-id="9e2ef-115">背景色の適用</span><span class="sxs-lookup"><span data-stu-id="9e2ef-115">Applying Background Colors</span></span>  
 <span data-ttu-id="9e2ef-116">レポート全体の背景、レポート内のテキスト ボックスの背景、またはデータ領域内のセルやセルのグループに、塗りつぶしの色を追加できます。</span><span class="sxs-lookup"><span data-stu-id="9e2ef-116">A solid color can be added to the background of the entire report, a text box within the report, or to a cell or group of cells within a data region.</span></span> <span data-ttu-id="9e2ef-117">既定の背景色は白ですが、レポート アイテムの **プロパティ** ダイアログ ボックスの **[塗りつぶし]** タブで色を選択できます。</span><span class="sxs-lookup"><span data-stu-id="9e2ef-117">By default, the background color is white; however, you can select a color from the **Fill** tab of the report item's **Properties** dialog box.</span></span> <span data-ttu-id="9e2ef-118">たとえば、テキスト ボックスの背景色を変更する場合は、テキスト ボックスを右クリックして、 **[テキスト ボックスのプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9e2ef-118">For example, if you want to change the background color of a text box, right-click the text box and select **Text Box Properties**.</span></span> <span data-ttu-id="9e2ef-119">**[塗りつぶし]** をクリックして、適切な色を選択します。</span><span class="sxs-lookup"><span data-stu-id="9e2ef-119">Click **Fill** and then select the color you want.</span></span> <span data-ttu-id="9e2ef-120">このダイアログ ボックスでは、選択したアイテムの背景色を選択することも、背景に表示される画像を追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="9e2ef-120">In this dialog box, you can select a background color for the selected item or you can add an image that appears in the background.</span></span>  
  
 <span data-ttu-id="9e2ef-121">グラフを使用する場合は、背景色のグラデーションとパターンのスタイルも指定できます。</span><span class="sxs-lookup"><span data-stu-id="9e2ef-121">When you use the chart, you can also specify gradients and pattern styles for background colors.</span></span> <span data-ttu-id="9e2ef-122">詳細については、「[グラフの書式設定 &#40;レポート ビルダーおよび SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9e2ef-122">For more information, see [Formatting a Chart &#40;Report Builder and SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md).</span></span>  
  
## <a name="using-images-as-formatting"></a><span data-ttu-id="9e2ef-123">書式設定での画像の使用</span><span class="sxs-lookup"><span data-stu-id="9e2ef-123">Using Images as Formatting</span></span>  
 <span data-ttu-id="9e2ef-124">画像が含まれているフィールドはデータ領域に追加できます。</span><span class="sxs-lookup"><span data-stu-id="9e2ef-124">Fields that contain images can be added to a data region.</span></span> <span data-ttu-id="9e2ef-125">画像フィールドを使用した場合、画像はレポートの実行時にレポートに表示されます。</span><span class="sxs-lookup"><span data-stu-id="9e2ef-125">If you use an image field, the images appear in the report with the report is run.</span></span>  
  
 <span data-ttu-id="9e2ef-126">ロゴなどの画像をレポートの背景に追加したり、四角形、テキスト ボックス、テーブル、マトリックスなどのグラフの一部、またはレポートの本文やページのセクションに追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="9e2ef-126">You can also add images such as logos to the background of your report or to a rectangle, text box, table, matrix, or some parts of a chart, or to the body and page sections of a report.</span></span> <span data-ttu-id="9e2ef-127">詳細については、「[画像 &#40;レポート ビルダーおよび SSRS& #41;](images-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9e2ef-127">For more information, see [Images &#40;Report Builder and SSRS&#41;](images-report-builder-and-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e2ef-128">参照</span><span class="sxs-lookup"><span data-stu-id="9e2ef-128">See Also</span></span>  
 <span data-ttu-id="9e2ef-129">[テキストとプレースホルダーの書式設定 &#40;レポート ビルダーおよび SSRS&#41;](formatting-text-and-placeholders-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="9e2ef-129">[Formatting Text and Placeholders &#40;Report Builder and SSRS&#41;](formatting-text-and-placeholders-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="9e2ef-130">[数値と日付の書式設定 &#40;レポート ビルダーおよび SSRS&#41;](formatting-numbers-and-dates-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="9e2ef-130">[Formatting Numbers and Dates &#40;Report Builder and SSRS&#41;](formatting-numbers-and-dates-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="9e2ef-131">[テキスト ボックス内のテキストの書式設定 &#40;レポート ビルダーおよび SSRS&#41;](format-text-in-a-text-box-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="9e2ef-131">[Format Text in a Text Box &#40;Report Builder and SSRS&#41;](format-text-in-a-text-box-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="9e2ef-132">[[塗りつぶし] ダイアログ ボックス &#40;レポート ビルダーおよび SSRS&#41;](../fill-dialog-box-report-builder-and-ssrs.md)</span><span class="sxs-lookup"><span data-stu-id="9e2ef-132">[Fill Dialog Box &#40;Report Builder and SSRS&#41;](../fill-dialog-box-report-builder-and-ssrs.md)</span></span>  
  
  
