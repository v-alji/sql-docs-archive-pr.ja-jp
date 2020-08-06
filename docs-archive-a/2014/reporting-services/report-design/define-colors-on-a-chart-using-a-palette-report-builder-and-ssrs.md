---
title: パレットを使用したグラフの色の定義 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: d95efc22-5a32-43d4-9bd2-12753e7fd395
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7db137ed87b0c84e43577dcf2936a6287abd8e36
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640705"
---
# <a name="define-colors-on-a-chart-using-a-palette-report-builder-and-ssrs"></a><span data-ttu-id="1834a-102">パレットを使用したグラフの色の定義 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="1834a-102">Define Colors on a Chart Using a Palette (Report Builder and SSRS)</span></span>
  <span data-ttu-id="1834a-103">グラフの色パレットは、定義済みのパレットを選択するかカスタム パレットを定義すると、変更できます。</span><span class="sxs-lookup"><span data-stu-id="1834a-103">You can change the color palette for a chart by selecting a pre-defined palette or defining a custom palette.</span></span> <span data-ttu-id="1834a-104">カスタム パレットはレポート固有です。</span><span class="sxs-lookup"><span data-stu-id="1834a-104">Custom palettes are report-specific.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-change-the-colors-on-the-chart-using-a-built-in-color-palette"></a><span data-ttu-id="1834a-105">組み込みの色パレットを使用してグラフの色を変更するには</span><span class="sxs-lookup"><span data-stu-id="1834a-105">To change the colors on the chart using a built-in color palette</span></span>  
  
1.  <span data-ttu-id="1834a-106">プロパティ ペインを開きます。</span><span class="sxs-lookup"><span data-stu-id="1834a-106">Open the Properties pane.</span></span>  
  
2.  <span data-ttu-id="1834a-107">デザイン画面で、グラフをクリックします。</span><span class="sxs-lookup"><span data-stu-id="1834a-107">On the design surface, click the chart.</span></span> <span data-ttu-id="1834a-108">グラフ オブジェクトのプロパティがプロパティ ペインに表示されます。</span><span class="sxs-lookup"><span data-stu-id="1834a-108">The properties for the chart object are displayed in the Properties pane.</span></span>  
  
     <span data-ttu-id="1834a-109">プロパティ ペインの上部のドロップダウン リストに、オブジェクト名 (既定では**Chart1** ) が表示されます。</span><span class="sxs-lookup"><span data-stu-id="1834a-109">The object name (**Chart1** by default) appears in the drop-down list at the top of the Properties pane.</span></span>  
  
3.  <span data-ttu-id="1834a-110">**[グラフ]** セクションの Palette プロパティで、ドロップダウン リストから新しいパレットを選択します。</span><span class="sxs-lookup"><span data-stu-id="1834a-110">In the **Chart** section, for the Palette property, select a new palette from the drop-down list.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="1834a-111">定義済みのパレットでは、色および順序を変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="1834a-111">You cannot change the colors or order in a pre-defined palette.</span></span>  
  
### <a name="to-define-your-own-colors-on-the-chart-using-a-custom-color-palette"></a><span data-ttu-id="1834a-112">カスタムの色パレットを使用してグラフの色を独自に定義するには</span><span class="sxs-lookup"><span data-stu-id="1834a-112">To define your own colors on the chart using a custom color palette</span></span>  
  
1.  <span data-ttu-id="1834a-113">プロパティ ペインを開きます。</span><span class="sxs-lookup"><span data-stu-id="1834a-113">Open the Properties pane.</span></span>  
  
2.  <span data-ttu-id="1834a-114">デザイン画面で、グラフをクリックします。</span><span class="sxs-lookup"><span data-stu-id="1834a-114">On the design surface, click the chart.</span></span> <span data-ttu-id="1834a-115">グラフ オブジェクトのプロパティがプロパティ ペインに表示されます。</span><span class="sxs-lookup"><span data-stu-id="1834a-115">The properties for the chart object are displayed in the Properties pane.</span></span>  
  
3.  <span data-ttu-id="1834a-116">[**グラフ**] セクションのプロパティで `Palette` 、[**カスタム**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="1834a-116">In the **Chart** section, for the `Palette` property, select **Custom**.</span></span>  
  
4.  <span data-ttu-id="1834a-117">CustomPaletteColors プロパティで、コレクションの編集ボタン ( **[...]** ) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1834a-117">In the CustomPaletteColors property, click the Edit Collection (**...**) button.</span></span> <span data-ttu-id="1834a-118">**[ReportColorExpression コレクション エディター]** が表示されます。</span><span class="sxs-lookup"><span data-stu-id="1834a-118">The **ReportColorExpression Collection Editor** opens.</span></span>  
  
5.  <span data-ttu-id="1834a-119">**[追加]** をクリックして、色を追加します。</span><span class="sxs-lookup"><span data-stu-id="1834a-119">Click **Add** to add a color.</span></span> <span data-ttu-id="1834a-120">ドロップダウン リストから色を選択するか、[式] を選択して具体的な色の 16 進値 (たとえば "オレンジ" の場合は ff6600) を指定します。</span><span class="sxs-lookup"><span data-stu-id="1834a-120">Select a color from the drop-down list or select Expression and specify a hex value for a specific color, such as ff6600 for "Orange".</span></span>  
  
     <span data-ttu-id="1834a-121">16 進値の詳細については、MSDN の「 [カラー テーブル](https://go.microsoft.com/fwlink/?linkid=9258) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1834a-121">For more information about hex values, see [Color Table](https://go.microsoft.com/fwlink/?linkid=9258) on MSDN.</span></span>  
  
6.  <span data-ttu-id="1834a-122">さらにパレットに色を追加するには、 **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1834a-122">Click **Add** to add more colors to the palette.</span></span>  
  
7.  <span data-ttu-id="1834a-123">終了したら **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1834a-123">When you are done, click **OK**.</span></span>  
  
 <span data-ttu-id="1834a-124">カスタム パレットを使用している場合は、色の順序を変更して、グラフ内の各系列の色を変更することができます。</span><span class="sxs-lookup"><span data-stu-id="1834a-124">If you are using a custom palette, you can change the order of the colors to change the color of different series in the chart.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1834a-125">参照</span><span class="sxs-lookup"><span data-stu-id="1834a-125">See Also</span></span>  
 <span data-ttu-id="1834a-126">[グラフの系列の色の書式設定 &#40;レポート ビルダーおよび SSRS&#41;](formatting-series-colors-on-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="1834a-126">[Formatting Series Colors on a Chart &#40;Report Builder and SSRS&#41;](formatting-series-colors-on-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="1834a-127">[グラフ &#40;レポート ビルダーおよび SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="1834a-127">[Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="1834a-128">複数の図形グラフでの色の統一 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="1834a-128">Specify Consistent Colors across Multiple Shape Charts &#40;Report Builder and SSRS&#41;</span></span>](shape-charts-report-builder-and-ssrs.md)  
  
  
