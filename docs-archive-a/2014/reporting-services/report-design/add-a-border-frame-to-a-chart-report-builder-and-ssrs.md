---
title: グラフへの枠線の追加 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: ca0c5040-40bb-4cb7-bc2b-5bcbe73858bb
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4c91d3de00caa4eab6ed1894042b2214b7dcf4b9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739385"
---
# <a name="add-a-border-frame-to-a-chart-report-builder-and-ssrs"></a><span data-ttu-id="185b4-102">グラフへの枠線の追加 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="185b4-102">Add a Border Frame to a Chart (Report Builder and SSRS)</span></span>
  <span data-ttu-id="185b4-103">グラフの視覚効果を高めるには、グラフの外枠に罫線の使用を検討してください。</span><span class="sxs-lookup"><span data-stu-id="185b4-103">To give a chart more visual impact, consider using a border frame around the outside of the chart.</span></span> <span data-ttu-id="185b4-104">枠線を選択するには、 **[グラフのプロパティ]** ダイアログ ボックスを使用するか、プロパティ ペインを使用します。</span><span class="sxs-lookup"><span data-stu-id="185b4-104">You can select a border frame by using the **Chart Properties** dialog box or by using the Properties pane.</span></span> <span data-ttu-id="185b4-105">グラフの枠線を他のデータ領域に適用することはできません。</span><span class="sxs-lookup"><span data-stu-id="185b4-105">The chart border frames cannot be applied to any other data region.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-apply-a-border-to-a-chart"></a><span data-ttu-id="185b4-106">グラフに罫線を適用するには</span><span class="sxs-lookup"><span data-stu-id="185b4-106">To apply a border to a chart</span></span>  
  
1.  <span data-ttu-id="185b4-107">グラフ上の任意の場所を右クリックし、表示されるオプションから **[グラフのプロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="185b4-107">Right-click anywhere on the chart and select **Chart Properties**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="185b4-108">**[グラフのプロパティ]** が表示されていない場合は、ショートカット メニューの **[グラフ]** をポイントし、 **[グラフのプロパティ]** 選択します。</span><span class="sxs-lookup"><span data-stu-id="185b4-108">If you do not see the **Chart Properties**, point to **Chart** on the shortcut menu and select **Chart Properties**.</span></span>  
  
2.  <span data-ttu-id="185b4-109">**[罫線]** を選択し、グラフに適用する罫線の種類をクリックします。</span><span class="sxs-lookup"><span data-stu-id="185b4-109">Select **Border**, and click the type of border to apply to the chart.</span></span>  
  
3.  <span data-ttu-id="185b4-110">(省略可) 罫線のスタイルを表す値を選択するか、式を入力します。</span><span class="sxs-lookup"><span data-stu-id="185b4-110">(Optional) Select a value or type an expression that represents the style of the border.</span></span>  
  
4.  <span data-ttu-id="185b4-111">(省略可) グラフの周囲に外枠として描く線の色を指定します。</span><span class="sxs-lookup"><span data-stu-id="185b4-111">(Optional) Specify the color of the line that will be drawn around the chart as the border.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="185b4-112">**[線の色]** ボックスの一覧には一般的な色が含まれています。</span><span class="sxs-lookup"><span data-stu-id="185b4-112">The **Line color** list contains common colors.</span></span> <span data-ttu-id="185b4-113">他の色を選択するには、一覧の **[その他の色]** をクリックし、一覧の横にある式 ( **[fx]** ) ボタンをクリックして **[式]** エディターを表示します。</span><span class="sxs-lookup"><span data-stu-id="185b4-113">If you want to select from a list of more colors, click **More colors** in the list or click the expression (**fx**) button next to the list to bring up the **Expression** editor.</span></span>  
  
5.  <span data-ttu-id="185b4-114">(省略可) 罫線の幅を指定します。</span><span class="sxs-lookup"><span data-stu-id="185b4-114">(Optional) Specify the width of the border.</span></span> <span data-ttu-id="185b4-115">有効な値は 0.25pt から 20pt までです。</span><span class="sxs-lookup"><span data-stu-id="185b4-115">Valid values are between 0.25pt and 20pt.</span></span> <span data-ttu-id="185b4-116">優れた視覚効果を得るには、罫線のサイズを 1pt から 3pt までの間に維持することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="185b4-116">Consider keeping the size of your border to between 1 and 3pt for the best visual effect.</span></span>  
  
6.  <span data-ttu-id="185b4-117">(省略可) レポートの背景が白以外の場合、ページの色を同じ色に定義することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="185b4-117">(Optional) If your report contains a background color other than white, consider defining a page color that is the same color.</span></span> <span data-ttu-id="185b4-118">ページの色は、罫線の外の背景色です。</span><span class="sxs-lookup"><span data-stu-id="185b4-118">The page color is the background color outside of the border line.</span></span>  
  
7.  <span data-ttu-id="185b4-119">(省略可) フレームの種類を選択している場合、フレーム タイプと色を指定します。</span><span class="sxs-lookup"><span data-stu-id="185b4-119">(Optional) If you choose a Frame type, specify a style and color for the frame.</span></span> <span data-ttu-id="185b4-120">**[フレームの塗りつぶしの色]** ボックスの一覧には一般的な色が含まれています。</span><span class="sxs-lookup"><span data-stu-id="185b4-120">The **Frame fill color** list contains common colors.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="185b4-121">参照</span><span class="sxs-lookup"><span data-stu-id="185b4-121">See Also</span></span>  
 <span data-ttu-id="185b4-122">[グラフ &#40;レポート ビルダーおよび SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="185b4-122">[Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="185b4-123">[グラフの書式設定 (レポート ビルダーおよび SSRS)](formatting-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="185b4-123">[Formatting a Chart &#40;Report Builder and SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="185b4-124">グラフへの傾斜、エンボス、およびテクスチャのスタイルの追加 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="185b4-124">Add Bevel, Emboss, and Texture Styles to a Chart &#40;Report Builder and SSRS&#41;</span></span>](chart-effects-add-bevel-emboss-or-texture-report-builder.md)  
  
  
