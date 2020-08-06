---
title: レポートへのグラフの追加 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: a6b595dc-f775-4a53-8554-74a0bf9335ec
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 789dd6cce10b0425833ea63f2f7941ea75970a25
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631562"
---
# <a name="add-a-chart-to-a-report-report-builder-and-ssrs"></a><span data-ttu-id="234f1-102">レポートへのグラフの追加 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="234f1-102">Add a Chart to a Report (Report Builder and SSRS)</span></span>
  <span data-ttu-id="234f1-103">データをビジュアル形式でまとめるには、グラフ データ領域を使用します。</span><span class="sxs-lookup"><span data-stu-id="234f1-103">When you want to summarize data in a visual format, use a Chart data region.</span></span> <span data-ttu-id="234f1-104">表示するデータの種類に対して適切な種類のグラフを選択することが重要です。</span><span class="sxs-lookup"><span data-stu-id="234f1-104">It is important to choose an appropriate chart type for the type of data that you are presenting.</span></span> <span data-ttu-id="234f1-105">これにより、データをグラフ形式にした場合にどの程度わかりやすくなるかが決まります。</span><span class="sxs-lookup"><span data-stu-id="234f1-105">This affects how well the data can be interpreted when put in chart form.</span></span> <span data-ttu-id="234f1-106">グラフ要素の詳細については、「 [グラフ &#40;レポート ビルダーおよび SSRS&#41;](charts-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="234f1-106">For more information, see [Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="234f1-107">グラフ データ領域をレポートに追加するには、グラフの新規作成ウィザードを実行するのが最も簡単な方法です。</span><span class="sxs-lookup"><span data-stu-id="234f1-107">The simplest way to add a Chart data region to your report is to run the New Chart Wizard.</span></span> <span data-ttu-id="234f1-108">このウィザードを使用して、縦棒グラフ、折れ線グラフ、円グラフ、横棒グラフ、および面グラフを作成できます。</span><span class="sxs-lookup"><span data-stu-id="234f1-108">The wizard offers column, line, pie, bar, and area charts.</span></span> <span data-ttu-id="234f1-109">これらのグラフおよびその他の種類のグラフは、手動で追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="234f1-109">For these and other chart types, you can also add a chart manually.</span></span>  
  
 <span data-ttu-id="234f1-110">グラフ データ領域をデザイン画面に追加したら、グラフのグラフ データ ペインに数値データおよび非数値データのレポート データセット フィールドをドラッグします。</span><span class="sxs-lookup"><span data-stu-id="234f1-110">After you add a Chart data region to the design surface, you can drag report dataset fields for numeric and non-numeric data to the Chart Data pane of the chart.</span></span> <span data-ttu-id="234f1-111">グラフをクリックすると、系列グループ、カテゴリ グループ、および値の 3 つの領域を持つグラフ データ ペインが表示されます。</span><span class="sxs-lookup"><span data-stu-id="234f1-111">Click the chart to display the Chart Data pane with its three areas: Series Groups, Category Groups, and Values.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-chart-to-a-report-by-using-the-chart-wizard"></a><span data-ttu-id="234f1-112">グラフ ウィザードを使用してグラフをレポートに追加するには</span><span class="sxs-lookup"><span data-stu-id="234f1-112">To add a chart to a report by using the Chart Wizard</span></span>  
  
1.  > [!NOTE]  
    >  <span data-ttu-id="234f1-113">グラフ ウィザードは、レポート ビルダーでのみ利用可能です。</span><span class="sxs-lookup"><span data-stu-id="234f1-113">The Chart Wizard is only available in Report Builder.</span></span>  
  
     <span data-ttu-id="234f1-114">**[挿入]** タブの **[グラフ]** をクリックし、次に **[グラフ ウィザード]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="234f1-114">On the **Insert** tab, click **Chart**, and then click **Chart Wizard**.</span></span>  
  
2.  <span data-ttu-id="234f1-115">グラフの **新規作成** ウィザードの手順に従って操作します。</span><span class="sxs-lookup"><span data-stu-id="234f1-115">Follow the steps in the **New** Chart wizard.</span></span>  
  
3.  <span data-ttu-id="234f1-116">**[ホーム]** タブで **[実行]** をクリックして、表示されたレポートを確認します。</span><span class="sxs-lookup"><span data-stu-id="234f1-116">On the **Home** tab, click **Run** to see the rendered report.</span></span>  
  
4.  <span data-ttu-id="234f1-117">レポートの作業を続行するには、 **[実行]** タブで **[デザイン]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="234f1-117">On the **Run** tab, click **Design** to continue working on the report.</span></span>  
  
### <a name="to-add-a-chart-to-a-report"></a><span data-ttu-id="234f1-118">レポートにグラフを追加するには</span><span class="sxs-lookup"><span data-stu-id="234f1-118">To add a chart to a report</span></span>  
  
1.  <span data-ttu-id="234f1-119">レポートを作成し、データセットを定義します。</span><span class="sxs-lookup"><span data-stu-id="234f1-119">Create a report and define a dataset.</span></span> <span data-ttu-id="234f1-120">詳細については、「[レポート &#40;レポートビルダーおよび SSRS&#41;にデータを追加する](../report-data/report-datasets-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="234f1-120">For more information, see [Add Data to a Report &#40;Report Builder and SSRS&#41;](../report-data/report-datasets-ssrs.md).</span></span>  
  
2.  <span data-ttu-id="234f1-121">**[挿入]** タブの **[グラフ]** をクリックし、次に **[グラフの挿入]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="234f1-121">On the **Insert** tab, click **Chart**, and then click **Insert Chart**.</span></span>  
  
3.  <span data-ttu-id="234f1-122">デザイン画面上のグラフの左上隅となる場所をクリックし、グラフの右下隅となる位置までドラッグします。</span><span class="sxs-lookup"><span data-stu-id="234f1-122">Click on the design surface where you want the upper-left corner of the chart, and then drag to where you want the lower-right corner of the chart.</span></span>  
  
     <span data-ttu-id="234f1-123">**[グラフの種類を選択]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="234f1-123">The **Select Chart Type** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="234f1-124">追加するグラフの種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="234f1-124">Select the type of chart you want to add.</span></span> [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
5.  <span data-ttu-id="234f1-125">グラフをクリックして、 **グラフ データ** ペインを表示します。</span><span class="sxs-lookup"><span data-stu-id="234f1-125">Click the chart to display the **Chart Data** pane.</span></span>  
  
6.  <span data-ttu-id="234f1-126">1 つまたは複数のフィールドを **[値]** 領域に追加します。</span><span class="sxs-lookup"><span data-stu-id="234f1-126">Add one or more fields to the **Values** area.</span></span> <span data-ttu-id="234f1-127">この情報は値軸にプロットされます。</span><span class="sxs-lookup"><span data-stu-id="234f1-127">This information will be plotted on the value axis.</span></span>  
  
7.  <span data-ttu-id="234f1-128">グループ化したフィールドを **[カテゴリ グループ]** 領域に追加します。</span><span class="sxs-lookup"><span data-stu-id="234f1-128">Add a grouping field to the **Category Groups** area.</span></span> <span data-ttu-id="234f1-129">このフィールドを **[カテゴリ グループ]** 領域に追加すると、グループ化したフィールドが自動的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="234f1-129">When you add this field to the **Category Groups** area, a grouping field is automatically created for you.</span></span> <span data-ttu-id="234f1-130">グループごとに、系列のデータ ポイントを表します。</span><span class="sxs-lookup"><span data-stu-id="234f1-130">Each group represents a data point in your series.</span></span>  
  
8.  <span data-ttu-id="234f1-131">カテゴリ別にデータをまとめるには、データ フィールドを右クリックし、 **[系列のプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="234f1-131">To summarize the data by category, right-click the data field and click **Series Properties**.</span></span> <span data-ttu-id="234f1-132">**[カテゴリ]** ボックスの一覧からカテゴリ フィールドを選択します。</span><span class="sxs-lookup"><span data-stu-id="234f1-132">In the **Category** box, select the category field from the drop-down list.</span></span> [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
9. <span data-ttu-id="234f1-133">**[ホーム]** タブで **[実行]** をクリックして、表示されたレポートを確認します。</span><span class="sxs-lookup"><span data-stu-id="234f1-133">On the **Home** tab, click **Run** to see the rendered report.</span></span>  
  
10. <span data-ttu-id="234f1-134">レポートの作業を続行するには、 **[実行]** タブで **[デザイン]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="234f1-134">On the **Run** tab, click **Design** to continue working on the report.</span></span>  
  
 <span data-ttu-id="234f1-135">横棒グラフや縦棒グラフなど、軸を使用するグラフでは、カテゴリ軸にすべてのカテゴリ ラベルが表示されるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="234f1-135">On charts with axes, such as bar and column charts, the category axis may not display all the category labels.</span></span> <span data-ttu-id="234f1-136">軸ラベルの変更方法の詳細については、「[軸の間隔の指定 (レポート ビルダーおよび SSRS)](specify-an-axis-interval-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="234f1-136">For more information about how to change the axis labels, see [Specify an Axis Interval &#40;Report Builder and SSRS&#41;](specify-an-axis-interval-report-builder-and-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="234f1-137">参照</span><span class="sxs-lookup"><span data-stu-id="234f1-137">See Also</span></span>  
 <span data-ttu-id="234f1-138">[グラフ &#40;レポート ビルダーおよび SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="234f1-138">[Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="234f1-139">[グラフの種類 &#40;レポート ビルダーおよび SSRS&#41;](chart-types-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="234f1-139">[Chart Types &#40;Report Builder and SSRS&#41;](chart-types-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="234f1-140">[グラフ内の空のデータ ポイントおよび NULL データ ポイント (レポート ビルダーおよび SSRS)](empty-and-null-data-points-in-charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="234f1-140">[Empty and Null Data Points in Charts &#40;Report Builder and SSRS&#41;](empty-and-null-data-points-in-charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="234f1-141">[チュートリアル: レポートへの横棒グラフの追加 (レポート ビルダー)](https://go.microsoft.com/fwlink/?LinkId=198052) </span><span class="sxs-lookup"><span data-stu-id="234f1-141">[Tutorial: Adding a Bar Chart to Your Report (Report Builder)](https://go.microsoft.com/fwlink/?LinkId=198052) </span></span>  
 <span data-ttu-id="234f1-142">[チュートリアル: レポートへの横棒グラフの追加 (レポート デザイナー)](https://go.microsoft.com/fwlink/?LinkId=198042) </span><span class="sxs-lookup"><span data-stu-id="234f1-142">[Tutorial: Adding a Bar Chart to a Report (Report Designer)](https://go.microsoft.com/fwlink/?LinkId=198042) </span></span>  
 <span data-ttu-id="234f1-143">[チュートリアル: レポートへの円グラフの追加 (レポート ビルダー)](https://go.microsoft.com/fwlink/?LinkId=198051) </span><span class="sxs-lookup"><span data-stu-id="234f1-143">[Tutorial: Adding a Pie Chart to Your Report (Report Builder)](https://go.microsoft.com/fwlink/?LinkId=198051) </span></span>  
 [<span data-ttu-id="234f1-144">チュートリアル: レポートへの円グラフの追加 (レポート デザイナー)</span><span class="sxs-lookup"><span data-stu-id="234f1-144">Tutorial: Adding a Pie Chart to a Report (Report Designer)</span></span>](https://go.microsoft.com/fwlink/?LinkId=198041)  
  
  
