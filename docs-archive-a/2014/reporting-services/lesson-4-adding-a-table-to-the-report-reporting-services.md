---
title: 'レッスン 4 : レポートへのテーブルの追加 (Reporting Services) | Microsoft Docs'
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 5ddf2914-bcdd-427d-8cba-0ccb8342f819
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 52694168bd60b8e3807db6204f33a89815573093
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632975"
---
# <a name="lesson-4-adding-a-table-to-the-report-reporting-services"></a><span data-ttu-id="95ca4-102">レッスン 4 : レポートへのテーブルの追加 (Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="95ca4-102">Lesson 4: Adding a Table to the Report (Reporting Services)</span></span>
  <span data-ttu-id="95ca4-103">データセットを定義したら、レポートのデザインを開始できます。</span><span class="sxs-lookup"><span data-stu-id="95ca4-103">After the dataset is defined, you can start designing the report.</span></span> <span data-ttu-id="95ca4-104">レポートのレイアウトを作成するには、データ領域、テキスト ボックス、画像、およびレポートに含めるその他のアイテムを、デザイン画面にドラッグ アンド ドロップします。</span><span class="sxs-lookup"><span data-stu-id="95ca4-104">You create a report layout by dragging and dropping data regions, text boxes, images, and other items that you want to include in your report to the design surface.</span></span>  
  
 <span data-ttu-id="95ca4-105">基になるデータセットからデータ行を繰り返し表示するアイテムを *データ領域*と呼びます。</span><span class="sxs-lookup"><span data-stu-id="95ca4-105">Items that contain repeated rows of data from underlying datasets are called *data regions*.</span></span> <span data-ttu-id="95ca4-106">基本的なレポートのデータ領域は 1 つだけですが、表形式のレポートにグラフを追加する場合には、データ領域を追加できます。</span><span class="sxs-lookup"><span data-stu-id="95ca4-106">A basic report will have only one data region, but you can add more, for example, if you want to add a chart to your tabular report.</span></span> <span data-ttu-id="95ca4-107">データ領域を追加したら、そのデータ領域にフィールドを追加できます。</span><span class="sxs-lookup"><span data-stu-id="95ca4-107">After you add a data region, you can add fields to the data region.</span></span>  
  
### <a name="to-add-a-table-data-region-and-fields-to-a-report-layout"></a><span data-ttu-id="95ca4-108">[テーブル] データ領域とフィールドをレポート レイアウトに追加するには</span><span class="sxs-lookup"><span data-stu-id="95ca4-108">To add a Table data region and fields to a report layout</span></span>  
  
1.  <span data-ttu-id="95ca4-109">**[ツールボックス]** で **[表]** をクリックし、デザイン画面内をクリックして、マウスをドラッグします。</span><span class="sxs-lookup"><span data-stu-id="95ca4-109">In the **Toolbox**, click **Table**, and then click on the design surface and drag the mouse.</span></span> <span data-ttu-id="95ca4-110">デザイン画面の中央に 3 列のテーブル データ領域が作成されます。</span><span class="sxs-lookup"><span data-stu-id="95ca4-110">Report Designer draws a table data region with three columns in the center of the design surface.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="95ca4-111">**[レポート データ]** ペインの左側に **[ツールボックス]** タブが表示されます。</span><span class="sxs-lookup"><span data-stu-id="95ca4-111">The **Toolbox** may appear as a tab on the left side of the **Report Data** pane.</span></span> <span data-ttu-id="95ca4-112">**ツールボックス**を開くには、[**ツールボックス**] タブの上にポインターを移動します。**ツールボックス**が表示されていない場合は、[**表示**] メニューの [**ツールボックス**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95ca4-112">To open the **Toolbox**, move the pointer over the **Toolbox** tab. If the **Toolbox** is not visible, from the **View** menu, click **Toolbox**.</span></span>  
  
2.  <span data-ttu-id="95ca4-113">**レポートデータ**ペインで、 **AdventureWorksDataset**データセットを展開してフィールドを表示します。</span><span class="sxs-lookup"><span data-stu-id="95ca4-113">In the **Report Data** pane, expand the **AdventureWorksDataset** dataset to display the fields.</span></span>  
  
3.  <span data-ttu-id="95ca4-114">[Date] フィールドを、 **[レポート データ]** ペインからテーブルの最初の列にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="95ca4-114">Drag the Date field from the **Report Data** pane to the first column in the table.</span></span>  
  
     <span data-ttu-id="95ca4-115">フィールドを最初の列にドラッグすると、2 つの処理が行われます。</span><span class="sxs-lookup"><span data-stu-id="95ca4-115">When you drop the field into the first column, two things happen.</span></span> <span data-ttu-id="95ca4-116">1 つは、 *フィールド式*と呼ばれるフィールド名が `[Date]`のように角かっこで囲まれてデータ セルに表示されます。</span><span class="sxs-lookup"><span data-stu-id="95ca4-116">First, the data cell will display the field name, known as the *field expression*, in brackets: `[Date]`.</span></span> <span data-ttu-id="95ca4-117">2 つ目は、列ヘッダー値が [ヘッダー] 行 (フィールド式のすぐ上) に自動的に追加されます。</span><span class="sxs-lookup"><span data-stu-id="95ca4-117">Second, a column header value is automatically added to Header row, just above the field expression.</span></span> <span data-ttu-id="95ca4-118">既定では、この列がフィールド名になります。</span><span class="sxs-lookup"><span data-stu-id="95ca4-118">By default, the column is the name of the field.</span></span> <span data-ttu-id="95ca4-119">ヘッダー行のテキストを選択し、新しい名前を入力することができます。</span><span class="sxs-lookup"><span data-stu-id="95ca4-119">You can select the Header row text and type a new name.</span></span>  
  
4.  <span data-ttu-id="95ca4-120">[Order] フィールドを、 **[レポート データ]** ペインからテーブルの 2 番目の列にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="95ca4-120">Drag the Order field from the **Report Data** pane to the second column in the table.</span></span>  
  
5.  <span data-ttu-id="95ca4-121">[Product] フィールドを、 **[レポート データ]** ペインからテーブルの 3 番目の列にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="95ca4-121">Drag the Product field from the **Report Data** pane to the third column in the table.</span></span>  
  
6.  <span data-ttu-id="95ca4-122">[Qty] フィールドを、3 番目の列の右端沿いに、垂直方向のカーソルとマウス ポインターが正符号 [+] になるまでドラッグします。</span><span class="sxs-lookup"><span data-stu-id="95ca4-122">Drag the Qty field to the right edge of the third column until you get a vertical cursor and the mouse pointer has a plus sign [+].</span></span> <span data-ttu-id="95ca4-123">マウス ボタンを離すと `[Qty]`の 4 番目の列が作成されます。</span><span class="sxs-lookup"><span data-stu-id="95ca4-123">When you release the mouse button, a fourth column is created for `[Qty]`.</span></span>  
  
7.  <span data-ttu-id="95ca4-124">同様に \[Line Total\] フィールドを追加して、5 番目の列を作成します。</span><span class="sxs-lookup"><span data-stu-id="95ca4-124">Add the LineTotal field in the same way, creating a fifth column.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="95ca4-125">列ヘッダーは [Line Total] です。</span><span class="sxs-lookup"><span data-stu-id="95ca4-125">The column header is Line Total.</span></span> <span data-ttu-id="95ca4-126">レポート デザイナーは、LineTotal を 2 つの語に分割して、列の表示名を自動的に作成します。</span><span class="sxs-lookup"><span data-stu-id="95ca4-126">Report Designer automatically creates a friendly name for the column by splitting LineTotal into two words.</span></span>  
  
     <span data-ttu-id="95ca4-127">次の図は、[Date]、[Order]、[Product]、[Qty]、および [Line Total] の各フィールドを使用して作成したテーブル データ領域を示しています。</span><span class="sxs-lookup"><span data-stu-id="95ca4-127">The following diagram shows a table data region that has been populated with these fields: Date, Order, Product, Qty, and Line Total.</span></span>  
  
     <span data-ttu-id="95ca4-128">![デザイン、ヘッダー行と詳細行のあるテーブル](../../2014/tutorials/media/rs-basictabledetailsdesign.gif "デザイン、ヘッダー行と詳細行のあるテーブル")</span><span class="sxs-lookup"><span data-stu-id="95ca4-128">![Design, Table with header row and detail row](../../2014/tutorials/media/rs-basictabledetailsdesign.gif "Design, Table with header row and detail row")</span></span>  
  
## <a name="preview-your-report"></a><span data-ttu-id="95ca4-129">レポートをプレビューする</span><span class="sxs-lookup"><span data-stu-id="95ca4-129">Preview Your Report</span></span>  
 <span data-ttu-id="95ca4-130">レポートをプレビューすると、最初にレポート サーバーにパブリッシュする必要なしに、表示レポートを表示できます。</span><span class="sxs-lookup"><span data-stu-id="95ca4-130">Previewing a report enables you to view the rendered report without having to first publish it to a report server.</span></span> <span data-ttu-id="95ca4-131">デザイン時にレポートを頻繁にプレビューできます。</span><span class="sxs-lookup"><span data-stu-id="95ca4-131">You will probably want to preview your report frequently during design time.</span></span> <span data-ttu-id="95ca4-132">レポートをプレビューするとデザインとデータ接続の検証が実行されるため、エラーと問題を修正した後にレポートをレポート サーバーにパブリッシュできます。</span><span class="sxs-lookup"><span data-stu-id="95ca4-132">Previewing the report will also run validation on the design and data connections so you can correct errors and issues before publishing the report to a report server.</span></span>  
  
#### <a name="to-preview-a-report"></a><span data-ttu-id="95ca4-133">レポートをプレビューするには</span><span class="sxs-lookup"><span data-stu-id="95ca4-133">To preview a report</span></span>  
  
-   <span data-ttu-id="95ca4-134">[**プレビュー** ] タブをクリックします。レポートデザイナーによってレポートが実行され、[プレビュー] ビューに表示されます。</span><span class="sxs-lookup"><span data-stu-id="95ca4-134">Click the **Preview** tab. Report Designer runs the report and displays it in Preview view.</span></span>  
  
     <span data-ttu-id="95ca4-135">[プレビュー] ビューに表示されたレポートの一部を次の図に示します。</span><span class="sxs-lookup"><span data-stu-id="95ca4-135">The following diagram shows part of the report in Preview view.</span></span>  
  
     <span data-ttu-id="95ca4-136">![プレビュー、列が 5 つあるテーブルの詳細行](../../2014/tutorials/media/rs-basictabledetailspreview.gif "プレビュー、列が 5 つあるテーブルの詳細行")</span><span class="sxs-lookup"><span data-stu-id="95ca4-136">![Preview, Detail rows of table with 5 columns](../../2014/tutorials/media/rs-basictabledetailspreview.gif "Preview, Detail rows of table with 5 columns")</span></span>  
  
     <span data-ttu-id="95ca4-137">通貨 ([Line Total] 列) は小数点以下 6 桁まで表示され、日付にはタイム スタンプが付いています。</span><span class="sxs-lookup"><span data-stu-id="95ca4-137">Notice that the currency (in the Line Total column) has six places after the decimal, and the date has includes a time stamp.</span></span> <span data-ttu-id="95ca4-138">次のレッスンで書式設定を修正します。</span><span class="sxs-lookup"><span data-stu-id="95ca4-138">You're going to fix that formatting in the next lesson.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="95ca4-139">**[ファイル]** メニューの **[すべてを保存]** をクリックして、レポートを保存します。</span><span class="sxs-lookup"><span data-stu-id="95ca4-139">On the **File** menu, click **Save All** to save the report.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="95ca4-140">次の手順</span><span class="sxs-lookup"><span data-stu-id="95ca4-140">Next Steps</span></span>  
 <span data-ttu-id="95ca4-141">[テーブル] データ領域がレポートに、フィールドがデータ領域にそれぞれ正しく追加され、レポートが正しくプレビューされました。</span><span class="sxs-lookup"><span data-stu-id="95ca4-141">You have successfully added a Table data region to your report, added fields to the data region, and previewed your report.</span></span> <span data-ttu-id="95ca4-142">次は、列ヘッダー、日付、および通貨の値の書式を設定します。</span><span class="sxs-lookup"><span data-stu-id="95ca4-142">Next, you will format column headers and date and currency values.</span></span> <span data-ttu-id="95ca4-143">「[レッスン 5: レポートの書式設定 &#40;Reporting Services&#41;](../reporting-services/lesson-5-formatting-a-report-reporting-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="95ca4-143">See [Lesson 5: Formatting a Report &#40;Reporting Services&#41;](../reporting-services/lesson-5-formatting-a-report-reporting-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95ca4-144">参照</span><span class="sxs-lookup"><span data-stu-id="95ca4-144">See Also</span></span>  
 <span data-ttu-id="95ca4-145">[テーブル &#40;レポートビルダーと SSRS&#41;](report-design/tables-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="95ca4-145">[Tables &#40;Report Builder  and SSRS&#41;](report-design/tables-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="95ca4-146">データセット フィールド コレクション &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="95ca4-146">Dataset Fields Collection &#40;Report Builder and SSRS&#41;</span></span>](report-data/dataset-fields-collection-report-builder-and-ssrs.md)  
  
  
