---
title: 日付または通貨として軸ラベルを書式設定する (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: e9a01a74-2f51-4b35-be3a-a6138568f6cf
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ffe9d903a2271db95d4b1c2ef6201d2b0f3edab3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634844"
---
# <a name="format-axis-labels-as-dates-or-currencies-report-builder-and-ssrs"></a><span data-ttu-id="1786c-102">日付または通貨として軸ラベルを書式設定する (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="1786c-102">Format Axis Labels as Dates or Currencies (Report Builder and SSRS)</span></span>
  <span data-ttu-id="1786c-103">適切に書式設定された DateTime 値を軸に表示すると、これらの値が日数として自動的にグラフに表示されます。</span><span class="sxs-lookup"><span data-stu-id="1786c-103">When you show properly formatted DateTime values on an axis, a chart will automatically display these values as days.</span></span> <span data-ttu-id="1786c-104">月や時間の間隔など、X 軸の日付や期間を指定するには、軸ラベルの書式を設定し、軸間隔の種類を有効な日付または期間に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1786c-104">To specify a date/time interval for the x-axis, such as an interval of months or an interval of hours, you must format the axis labels and set the type of axis interval to a valid date or time interval.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1786c-105">縦棒グラフおよび散布図の横軸 (X 軸) はカテゴリ軸です。</span><span class="sxs-lookup"><span data-stu-id="1786c-105">In column and scatter charts, the horizontal, or x-axis, is the category axis.</span></span> <span data-ttu-id="1786c-106">横棒グラフの縦軸 (Y 軸) もカテゴリ軸です。</span><span class="sxs-lookup"><span data-stu-id="1786c-106">In bar charts, the vertical, or y-axis, is the category axis.</span></span>  
  
 <span data-ttu-id="1786c-107">期間を適切に書式設定するには、X 軸に表示される値が <xref:System.DateTime> データ型に評価される必要があります。</span><span class="sxs-lookup"><span data-stu-id="1786c-107">In order to format time intervals correctly, the values displayed on the x-axis must evaluate to a <xref:System.DateTime> data type.</span></span> <span data-ttu-id="1786c-108">フィールドに <xref:System.String>のデータ型が設定されている場合、グラフでは間隔が日付や時間として計算されません。</span><span class="sxs-lookup"><span data-stu-id="1786c-108">If your field has a data type of <xref:System.String>, the chart will not calculate intervals as dates or times.</span></span> <span data-ttu-id="1786c-109">グラフ要素の詳細については、「 [グラフ &#40;レポート ビルダーおよび SSRS&#41;](charts-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1786c-109">For more information, see [Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="1786c-110">数値を Y 軸に追加した場合、既定では、グラフに数値が表示されるまで書式が設定されません。</span><span class="sxs-lookup"><span data-stu-id="1786c-110">When a numeric value is added to the y-axis, by default, the chart does not format the number before displaying it.</span></span> <span data-ttu-id="1786c-111">数値フィールドが売上額の場合、グラフを読みやすくするために、数値を通貨として書式設定することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="1786c-111">If your numeric field is a sales figure, consider formatting the numbers as currencies to increase the readability of the chart.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-format-x-axis-labels-as-monthly-intervals"></a><span data-ttu-id="1786c-112">X 軸のラベルの間隔を月単位に書式設定するには</span><span class="sxs-lookup"><span data-stu-id="1786c-112">To format x-axis labels as monthly intervals</span></span>  
  
1.  <span data-ttu-id="1786c-113">グラフの横軸 (X 軸) を右クリックし、 **[横軸のプロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="1786c-113">Right-click the horizontal, or x-axis, of the chart, and select **HorizontalAxis Properties**.</span></span>  
  
2.  <span data-ttu-id="1786c-114">**[横軸のプロパティ]** ダイアログ ボックスで、 **[数値]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="1786c-114">In the **HorizontalAxis Properties** dialog box, select **Number**.</span></span>  
  
3.  <span data-ttu-id="1786c-115">**[カテゴリ]** ボックスの一覧で、 **[日付]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="1786c-115">From the **Category** list, select **Date**.</span></span> <span data-ttu-id="1786c-116">**[種類]** ボックスの一覧で、X 軸のラベルに適用する日付書式を選択します。</span><span class="sxs-lookup"><span data-stu-id="1786c-116">From the **Type** list, select a date format to apply to the x-axis labels.</span></span>  
  
4.  <span data-ttu-id="1786c-117">**[軸のオプション]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="1786c-117">Select **Axis Options.**</span></span>  
  
5.  <span data-ttu-id="1786c-118">**[間隔]** で、「 **1**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="1786c-118">In **Interval**, type **1**.</span></span> <span data-ttu-id="1786c-119">**[間隔の種類]** プロパティで、 **[月]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="1786c-119">In **Interval type** property, select **Months**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="1786c-120">間隔の種類を指定しない場合、グラフでは日単位の間隔が計算されます。</span><span class="sxs-lookup"><span data-stu-id="1786c-120">If you do not specify an interval type, the chart will calculate intervals in terms of days.</span></span>  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-format-y-axis-labels-using-a-currency-format"></a><span data-ttu-id="1786c-121">通貨の書式を使用して Y 軸ラベルを書式設定するには</span><span class="sxs-lookup"><span data-stu-id="1786c-121">To format y-axis labels using a currency format</span></span>  
  
1.  <span data-ttu-id="1786c-122">グラフの縦軸 (Y 軸) を右クリックし、 **[縦軸のプロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="1786c-122">Right-click the vertical, or y-axis, of the chart, and select **VerticalAxis Properties**.</span></span>  
  
2.  <span data-ttu-id="1786c-123">**[縦軸のプロパティ]** ダイアログ ボックスで、 **[数値]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="1786c-123">In the **VerticalAxis Properties** dialog box, select **Number**.</span></span>  
  
3.  <span data-ttu-id="1786c-124">**[カテゴリ]** ボックスの一覧で、 **[通貨]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="1786c-124">From the **Category** list, select **Currency**.</span></span> <span data-ttu-id="1786c-125">**[記号]** ボックスの一覧で、Y 軸ラベルに適用する通貨書式を選択します。</span><span class="sxs-lookup"><span data-stu-id="1786c-125">From the **Symbol** list, select a currency format to apply to the y-axis labels.</span></span>  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1786c-126">参照</span><span class="sxs-lookup"><span data-stu-id="1786c-126">See Also</span></span>  
 <span data-ttu-id="1786c-127">[グラフの軸ラベルの書式設定 (レポート ビルダーおよび SSRS)](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="1786c-127">[Formatting Axis Labels on a Chart &#40;Report Builder and SSRS&#41;](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="1786c-128">[グラフの書式設定 (レポート ビルダーおよび SSRS)](formatting-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="1786c-128">[Formatting a Chart &#40;Report Builder and SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="1786c-129">[対数スケールの指定 &#40;レポート ビルダーおよび SSRS&#41;](specify-a-logarithmic-scale-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="1786c-129">[Specify a Logarithmic Scale &#40;Report Builder and SSRS&#41;](specify-a-logarithmic-scale-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="1786c-130">軸の間隔の指定 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="1786c-130">Specify an Axis Interval &#40;Report Builder and SSRS&#41;</span></span>](specify-an-axis-interval-report-builder-and-ssrs.md)  
  
  
