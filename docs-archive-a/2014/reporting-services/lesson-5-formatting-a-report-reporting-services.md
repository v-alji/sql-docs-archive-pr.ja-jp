---
title: 'レッスン 5 : レポートの書式設定 (Reporting Services) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: ae46efa9-6e04-48ec-afb4-5a2314dcb05a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 00f0d780e957fd9ff995fefb1d033275a7da428d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644842"
---
# <a name="lesson-5-formatting-a-report-reporting-services"></a><span data-ttu-id="36861-102">レッスン 5 : レポートの書式設定 (Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="36861-102">Lesson 5: Formatting a Report (Reporting Services)</span></span>
  <span data-ttu-id="36861-103">Sales Orders レポートに 1 つのデータ領域といくつかのフィールドを追加した後、日付および通貨のフィールド、および列ヘッダーを書式設定できます。</span><span class="sxs-lookup"><span data-stu-id="36861-103">Now that you've added a data region and some fields to the Sales Orders report, you can format the date and currency fields and the column headers.</span></span>  
  
 <span data-ttu-id="36861-104">このトピックの内容:</span><span class="sxs-lookup"><span data-stu-id="36861-104">In this topic:</span></span>  
  
-   [<span data-ttu-id="36861-105">日付の書式設定</span><span class="sxs-lookup"><span data-stu-id="36861-105">Format the Date</span></span>](#bkmk_format_date)  
  
-   [<span data-ttu-id="36861-106">通貨の書式設定</span><span class="sxs-lookup"><span data-stu-id="36861-106">Format the Currency</span></span>](#bkmk_format_currency)  
  
-   [<span data-ttu-id="36861-107">テキスト スタイルおよび列幅の変更</span><span class="sxs-lookup"><span data-stu-id="36861-107">Change Text Style and Column Widths</span></span>](#bkmk_change_textstyle)  
  
##  <a name="format-the-date"></a><a name="bkmk_format_date"></a><span data-ttu-id="36861-108">日付の書式設定</span><span class="sxs-lookup"><span data-stu-id="36861-108">Format the Date</span></span>  
 <span data-ttu-id="36861-109">日付フィールドには、既定では日付と時刻の情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="36861-109">The Date field displays date and time information by default.</span></span> <span data-ttu-id="36861-110">このフィールドを書式設定して、日付のみを表示できます。</span><span class="sxs-lookup"><span data-stu-id="36861-110">You can format it to display only the date.</span></span>  
  
#### <a name="to-format-a-date-field"></a><span data-ttu-id="36861-111">日付フィールドを書式設定するには</span><span class="sxs-lookup"><span data-stu-id="36861-111">To format a date field</span></span>  
  
1.  <span data-ttu-id="36861-112">**[デザイン]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="36861-112">Click the **Design** tab.</span></span>  
  
2.  <span data-ttu-id="36861-113">`[Date]` フィールド式が入力されているセルを右クリックし、[ **テキスト ボックスのプロパティ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="36861-113">Right-click the cell with the `[Date]` field expression and then click **Text Box Properties**.</span></span>  
  
3.  <span data-ttu-id="36861-114">[**数値**] をクリックし、[**カテゴリ**] フィールドでを選択し `Date` ます。</span><span class="sxs-lookup"><span data-stu-id="36861-114">Click **Number**, and then in the **Category** field, select `Date`.</span></span>  
  
4.  <span data-ttu-id="36861-115">**[型]** ボックスで **[2000 年 1 月 31 日]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="36861-115">In the **Type** box, select **January 31, 2000**.</span></span>  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
6.  <span data-ttu-id="36861-116">レポートをプレビューして `[Date]` フィールドに対する変更を確認し、デザイン ビューに戻ります。</span><span class="sxs-lookup"><span data-stu-id="36861-116">Preview the report to see the change to the `[Date]` field and then change back to design view.</span></span>  
  
##  <a name="format-the-currency"></a><a name="bkmk_format_currency"></a><span data-ttu-id="36861-117">通貨の書式を設定する</span><span class="sxs-lookup"><span data-stu-id="36861-117">Format the Currency</span></span>  
 <span data-ttu-id="36861-118">[LineTotal] フィールドには通常の数値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="36861-118">The LineTotal field displays a general number.</span></span> <span data-ttu-id="36861-119">このフィールドを書式設定して、数値を通貨として表示します。</span><span class="sxs-lookup"><span data-stu-id="36861-119">Format it to display the number as currency.</span></span>  
  
#### <a name="to-format-a-currency-field"></a><span data-ttu-id="36861-120">通貨フィールドを書式設定するには</span><span class="sxs-lookup"><span data-stu-id="36861-120">To format a currency field</span></span>  
  
1.  <span data-ttu-id="36861-121">`[LineTotal]` フィールド式が入力されているセルを右クリックし、[ **テキスト ボックスのプロパティ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="36861-121">Right-click the cell with the `[LineTotal]` field expression and then click **Text Box Properties**.</span></span>  
  
2.  <span data-ttu-id="36861-122">**[数値]** をクリックし、 **[Category]** フィールドで **[通貨]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="36861-122">Click **Number**, and in the **Category** field, select **Currency**.</span></span>  
  
3.  <span data-ttu-id="36861-123">地域設定が英語 (米国) の場合、既定値は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="36861-123">If your regional setting is English (United States), the defaults should be:</span></span>  
  
    -   <span data-ttu-id="36861-124">**小数点以下の桁数 : 2**</span><span class="sxs-lookup"><span data-stu-id="36861-124">**Decimal places: 2**</span></span>  
  
    -   <span data-ttu-id="36861-125">**負の数値 : ($12345.00)**</span><span class="sxs-lookup"><span data-stu-id="36861-125">**Negative numbers: ($12345.00)**</span></span>  
  
    -   <span data-ttu-id="36861-126">**記号 : $ 英語 (米国)**</span><span class="sxs-lookup"><span data-stu-id="36861-126">**Symbol: $ English (United States)**</span></span>  
  
4.  <span data-ttu-id="36861-127">[ **位取り区切り記号 (,) を使用する]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="36861-127">Select **Use 1000 separator (,)**.</span></span>  
  
     <span data-ttu-id="36861-128">"**$12,345.00**" というサンプル テキストが表示されている場合、正しい設定が行われています。</span><span class="sxs-lookup"><span data-stu-id="36861-128">If the sample text is:**$12,345.00**, then your settings are correct.</span></span>  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
6.  <span data-ttu-id="36861-129">レポートをプレビューして `[LineTotal]` フィールドに対する変更を確認し、デザイン ビューに戻ります。</span><span class="sxs-lookup"><span data-stu-id="36861-129">Preview the report to see the change to the `[LineTotal]` field and then change back to design view.</span></span>  
  
##  <a name="change-text-style-and-column-widths"></a><a name="bkmk_change_textstyle"></a><span data-ttu-id="36861-130">テキストのスタイルと列の幅を変更する</span><span class="sxs-lookup"><span data-stu-id="36861-130">Change Text Style and Column Widths</span></span>  
 <span data-ttu-id="36861-131">ヘッダー行の書式を変更して、レポートのデータの行と区別することもできます。</span><span class="sxs-lookup"><span data-stu-id="36861-131">You can also change the formatting of the header row to differentiate it from the rows of data in the report.</span></span> <span data-ttu-id="36861-132">最後に、列の幅を調整します。</span><span class="sxs-lookup"><span data-stu-id="36861-132">Lastly, you will adjust the widths of the columns.</span></span>  
  
#### <a name="to-format-header-rows-and-table-columns"></a><span data-ttu-id="36861-133">ヘッダー行およびテーブル列を書式設定するには</span><span class="sxs-lookup"><span data-stu-id="36861-133">To format header rows and table columns</span></span>  
  
1.  <span data-ttu-id="36861-134">テーブルをクリックし、列ハンドルおよび行ハンドルをテーブルの上部および横に表示します。</span><span class="sxs-lookup"><span data-stu-id="36861-134">Click the table so that column and row handles appear above and next to the table.</span></span>  
  
     <span data-ttu-id="36861-135">![デザイン、ヘッダー行と詳細行のあるテーブル](../../2014/tutorials/media/rs-basictabledetailsdesign.gif "デザイン、ヘッダー行と詳細行のあるテーブル")</span><span class="sxs-lookup"><span data-stu-id="36861-135">![Design, Table with header row and detail row](../../2014/tutorials/media/rs-basictabledetailsdesign.gif "Design, Table with header row and detail row")</span></span>  
  
     <span data-ttu-id="36861-136">テーブルの上と横のグレーのバーは、列および行ハンドルです。</span><span class="sxs-lookup"><span data-stu-id="36861-136">The gray bars along the top and side of the table are the column and row handles.</span></span>  
  
2.  <span data-ttu-id="36861-137">列ハンドルの間の罫線をポイントします。カーソルが 2 方向の矢印の形状に変化します。</span><span class="sxs-lookup"><span data-stu-id="36861-137">Point to the line between column handles so that the cursor changes into a double arrow.</span></span> <span data-ttu-id="36861-138">列をドラッグして、目的のサイズに変更します。</span><span class="sxs-lookup"><span data-stu-id="36861-138">Drag the columns to the size you want.</span></span>  
  
3.  <span data-ttu-id="36861-139">列ヘッダー ラベルを含む行を選択し、 **[書式]** メニューの **[フォント]** をポイントして **[太字]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="36861-139">Select the row containing column header labels and from the **Format** menu, point to **Font** and then click **Bold**.</span></span>  
  
4.  <span data-ttu-id="36861-140">レポートをプレビューするには、[**プレビュー** ] タブをクリックします。次のようになります。</span><span class="sxs-lookup"><span data-stu-id="36861-140">To preview your report, click the **Preview** tab. It should look something like this:</span></span>  
  
     <span data-ttu-id="36861-141">![列ヘッダーが太字になっているテーブルのプレビュー](../../2014/tutorials/media/rs-basictabledetailsformattedpreview.gif "列ヘッダーが太字になっているテーブルのプレビュー")</span><span class="sxs-lookup"><span data-stu-id="36861-141">![Preview of table with bold column headers](../../2014/tutorials/media/rs-basictabledetailsformattedpreview.gif "Preview of table with bold column headers")</span></span>  
  
5.  <span data-ttu-id="36861-142">**[ファイル]** メニューの **[すべてを保存]** をクリックして、レポートを保存します。</span><span class="sxs-lookup"><span data-stu-id="36861-142">On the **File** menu, click **Save All** to save the report.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="36861-143">次の手順</span><span class="sxs-lookup"><span data-stu-id="36861-143">Next Steps</span></span>  
 <span data-ttu-id="36861-144">ここでは、列ヘッダー、日付値、および通貨値を書式設定しました。</span><span class="sxs-lookup"><span data-stu-id="36861-144">You have successfully formatted column headers and date and currency values.</span></span> <span data-ttu-id="36861-145">次に、レポートにグループ化および合計を追加します。</span><span class="sxs-lookup"><span data-stu-id="36861-145">Next, you will add grouping and totals to your report.</span></span> <span data-ttu-id="36861-146">「[レッスン 6: グループと合計の追加 &#40;Reporting Services&#41;」](../reporting-services/lesson-6-adding-grouping-and-totals-reporting-services.md) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="36861-146">See [Lesson 6: Adding Grouping and Totals &#40;Reporting Services&#41;](../reporting-services/lesson-6-adding-grouping-and-totals-reporting-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36861-147">参照</span><span class="sxs-lookup"><span data-stu-id="36861-147">See Also</span></span>  
 <span data-ttu-id="36861-148">[&#40;レポートビルダーと SSRS&#41;の数値と日付の書式設定](report-design/formatting-numbers-and-dates-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="36861-148">[Formatting Numbers and Dates &#40;Report Builder and SSRS&#41;](report-design/formatting-numbers-and-dates-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="36861-149">レンダリングの動作 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="36861-149">Rendering Behaviors &#40;Report Builder  and SSRS&#41;</span></span>](report-design/rendering-behaviors-report-builder-and-ssrs.md)  
  
  
