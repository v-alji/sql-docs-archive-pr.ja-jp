---
title: 'レッスン 6: グループと合計の追加 (Reporting Services) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: e3d61228-2aa4-42cc-955e-602dbf3406a7
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b98798005a984edf00aff469d4c1b09aa2e34d98
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644834"
---
# <a name="lesson-6-adding-grouping-and-totals-reporting-services"></a><span data-ttu-id="d22cf-102">レッスン 6: グループと合計の追加 (Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="d22cf-102">Lesson 6: Adding Grouping and Totals (Reporting Services)</span></span>
  <span data-ttu-id="d22cf-103">レポートにグループと合計を追加すると、データを整理して要約できます。</span><span class="sxs-lookup"><span data-stu-id="d22cf-103">Add grouping and totals to your report to organize and summarize your data.</span></span>  
  
 <span data-ttu-id="d22cf-104">累計をレポートに追加する方法の詳細については、「 [Reporting Services (SSRS) レポートへの合計の追加](https://www.tutorialgateway.org/add-total-and-subtotal-to-ssrs-report/)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d22cf-104">For information about adding running totals to reports, see: [Adding totals to Reporting Services (SSRS) reports](https://www.tutorialgateway.org/add-total-and-subtotal-to-ssrs-report/).</span></span>  
  
 <span data-ttu-id="d22cf-105">**このトピックの内容:**</span><span class="sxs-lookup"><span data-stu-id="d22cf-105">**In this topic:**</span></span>  
  
-   [<span data-ttu-id="d22cf-106">レポートのデータをグループ化するには</span><span class="sxs-lookup"><span data-stu-id="d22cf-106">To group data in a report</span></span>](#bkmk_groupdata)  
  
-   [<span data-ttu-id="d22cf-107">レポートに合計を追加するには</span><span class="sxs-lookup"><span data-stu-id="d22cf-107">To add totals to a report</span></span>](#bkmk_addtotals)  
  
-   [<span data-ttu-id="d22cf-108">レポートに毎日の合計を追加するには</span><span class="sxs-lookup"><span data-stu-id="d22cf-108">To add a daily total to a report</span></span>](#bkmk_adddailytotal)  
  
-   [<span data-ttu-id="d22cf-109">レポートに総計を追加するには</span><span class="sxs-lookup"><span data-stu-id="d22cf-109">To add a grand total to a report</span></span>](#bkmk_addgrandtotal)  
  
-   [<span data-ttu-id="d22cf-110">レポートをレポートサーバーにパブリッシュするには (省略可能)</span><span class="sxs-lookup"><span data-stu-id="d22cf-110">To Publish the Report to the Report Server (Optional)</span></span>](#bkmk_publishreport)  
  
##  <a name="to-group-data-in-a-report"></a><a name="bkmk_groupdata"></a><span data-ttu-id="d22cf-111">レポートのデータをグループ化するには</span><span class="sxs-lookup"><span data-stu-id="d22cf-111">To group data in a report</span></span>  
  
1.  <span data-ttu-id="d22cf-112">**[デザイン]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="d22cf-112">Click the **Design** tab.</span></span>  
  
2.  <span data-ttu-id="d22cf-113">**行グループ**ペインが表示されない場合は、デザイン画面を右クリックして [**表示**] をクリックし、[**グループ化**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d22cf-113">If you do not see the **Row Groups** pane , right-click the design surface and click **view** and then click **Grouping**.</span></span>  
  
3.  <span data-ttu-id="d22cf-114">**[レポート データ]** ウィンドウから、`Date` フィールドを **[行グループ]** ウィンドウにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="d22cf-114">From the **Report Data** pane, drag the `Date` field to the **Row Groups** pane.</span></span> <span data-ttu-id="d22cf-115">**(詳細)** 行の上に配置します。</span><span class="sxs-lookup"><span data-stu-id="d22cf-115">Place it above the row called **(Details)**.</span></span>  
  
     <span data-ttu-id="d22cf-116">グループを示す角かっこが行ハンドルに表示されます。</span><span class="sxs-lookup"><span data-stu-id="d22cf-116">Note that the row handle now has a bracket in it, to show a group.</span></span> <span data-ttu-id="d22cf-117">テーブルにも 2 つの日付列が表示されます (点線の両側に 1 つずつ)。</span><span class="sxs-lookup"><span data-stu-id="d22cf-117">The table now also has two Date columns -- one on either side of a vertical dotted line.</span></span>  
  
     ![](../../2014/tutorials/media/rs-basictablegroups1design.gif "rs_BasicTableGroups1Design")  
  
4.  <span data-ttu-id="d22cf-118">**[レポート データ]** ウィンドウから、`Order` フィールドを **[行グループ]** ウィンドウにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="d22cf-118">From the **Report Data** pane, drag the `Order` field to the **Row Groups** pane.</span></span> <span data-ttu-id="d22cf-119">**(詳細)** の上、Date の下に配置します。</span><span class="sxs-lookup"><span data-stu-id="d22cf-119">Place it below Date and above **(Details)**.</span></span>  
  
     <span data-ttu-id="d22cf-120">2 つのグループを示す 2 個の角かっこが行ハンドルに表示されます。</span><span class="sxs-lookup"><span data-stu-id="d22cf-120">Note that the row handle now has two brackets in it, to show two groups.</span></span> <span data-ttu-id="d22cf-121">テーブルにも2つの列があり `Order` ます。</span><span class="sxs-lookup"><span data-stu-id="d22cf-121">The table now has two `Order` columns, too.</span></span>  
  
5.  <span data-ttu-id="d22cf-122">二重線の 右側 にある元の Date 列と **Order** 列を削除します。</span><span class="sxs-lookup"><span data-stu-id="d22cf-122">Delete the original Date and Order columns to the **right** of the double line.</span></span> <span data-ttu-id="d22cf-123">これにより、この個別のレコード値が削除されるので、グループ値のみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d22cf-123">This removes this individual record values so that only the group value is displayed.</span></span> <span data-ttu-id="d22cf-124">2 つの列の列ハンドルを選択し、右クリックして **[列の削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d22cf-124">Select the column handles for the two columns, right-click and click **Delete Columns**.</span></span>  
  
     <span data-ttu-id="d22cf-125">![削除する列の選択](../../2014/tutorials/media/rs-basictablegroupsdeletecols.gif "削除する列の選択")</span><span class="sxs-lookup"><span data-stu-id="d22cf-125">![Select columns to delete](../../2014/tutorials/media/rs-basictablegroupsdeletecols.gif "Select columns to delete")</span></span>  
  
     <span data-ttu-id="d22cf-126">列ヘッダーと日付の書式をもう一度設定できます。</span><span class="sxs-lookup"><span data-stu-id="d22cf-126">You can format the column headers and date again.</span></span>  
  
6.  <span data-ttu-id="d22cf-127">**[プレビュー]** タブに切り替えて、レポートをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="d22cf-127">Switch to the **Preview** tab to preview the report.</span></span> <span data-ttu-id="d22cf-128">この画面は次の図のようになります。</span><span class="sxs-lookup"><span data-stu-id="d22cf-128">It should look similar to the following illustration:</span></span>  
  
     <span data-ttu-id="d22cf-129">![Date、次に Order でグループ化されたテーブル](../../2014/tutorials/media/rs-basictablegroupspreview.gif "Date、次に Order でグループ化されたテーブル")</span><span class="sxs-lookup"><span data-stu-id="d22cf-129">![Table grouped by date and then order](../../2014/tutorials/media/rs-basictablegroupspreview.gif "Table grouped by date and then order")</span></span>  
  
##  <a name="to-add-totals-to-a-report"></a><a name="bkmk_addtotals"></a><span data-ttu-id="d22cf-130">レポートに合計を追加するには</span><span class="sxs-lookup"><span data-stu-id="d22cf-130">To add totals to a report</span></span>  
  
1.  <span data-ttu-id="d22cf-131">デザイン ビューに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="d22cf-131">Switch to Design view.</span></span>  
  
2.  <span data-ttu-id="d22cf-132">`[LineTotal]`フィールドが含まれるデータ領域セルを右クリックし、 **[合計の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d22cf-132">Right-click the data region cell that contains the field `[LineTotal]`, and click **Add Total**.</span></span>  
  
     <span data-ttu-id="d22cf-133">各注文の合計金額を示す行が追加されます。</span><span class="sxs-lookup"><span data-stu-id="d22cf-133">This adds a row with a sum of the dollar amount for each order.</span></span>  
  
3.  <span data-ttu-id="d22cf-134">`[Qty]`フィールドが含まれるセルを右クリックし、 **[合計の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d22cf-134">Right-click the cell that contains the field `[Qty]`, and click **Add Total**.</span></span>  
  
     <span data-ttu-id="d22cf-135">各注文の合計数量が合計行に追加されます。</span><span class="sxs-lookup"><span data-stu-id="d22cf-135">This adds a sum of the quantity for each order to the totals row.</span></span>  
  
4.  <span data-ttu-id="d22cf-136">`Sum[Qty]`の左側にある空のセルに、ラベルを「**注文合計**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="d22cf-136">In the empty cell to the left of `Sum[Qty]`, type the label "**Order Total"**.</span></span>  
  
5.  <span data-ttu-id="d22cf-137">合計行に背景色を追加できます。</span><span class="sxs-lookup"><span data-stu-id="d22cf-137">You can add a background color to the totals row.</span></span> <span data-ttu-id="d22cf-138">2 つの合計セルとラベル セルを選択します。</span><span class="sxs-lookup"><span data-stu-id="d22cf-138">Select the two sum cells and the label cell.</span></span>  
  
6.  <span data-ttu-id="d22cf-139">**[書式]** メニューの **[背景色]** をクリックし、 **[淡い灰色]** をクリックして、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d22cf-139">On the **Format** menu, click **Background Color**, click **Light Gray**, and click **OK**.</span></span>  
  
     <span data-ttu-id="d22cf-140">![[デザイン] ビュー: 注文合計がある基本的なテーブル](../../2014/tutorials/media/rs-basictablesumlinetotaldesign.gif "[デザイン] ビュー: 注文合計がある基本的なテーブル")</span><span class="sxs-lookup"><span data-stu-id="d22cf-140">![Design view: Basic table with order total](../../2014/tutorials/media/rs-basictablesumlinetotaldesign.gif "Design view: Basic table with order total")</span></span>  
  
##  <a name="to-add-a-daily-total-to-a-report"></a><a name="bkmk_adddailytotal"></a><span data-ttu-id="d22cf-141">レポートに日単位の合計を追加するには</span><span class="sxs-lookup"><span data-stu-id="d22cf-141">To add a daily total to a report</span></span>  
  
1.  <span data-ttu-id="d22cf-142">Order セルを右クリックし、 **[合計の追加]** をポイントして、 **[後]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d22cf-142">Right-click the Order cell, point to **Add Total**, and click **After**.</span></span>  
  
     <span data-ttu-id="d22cf-143">これにより、各日の数量と金額の合計を含む新しい行と、[Order] 列に "**Total**" というラベルが追加されます。</span><span class="sxs-lookup"><span data-stu-id="d22cf-143">This adds a new row containing sums of the quantity and dollar amount for each day, and the label "**Total**" in the Order column.</span></span>  
  
2.  <span data-ttu-id="d22cf-144">同じセルで **「合計」** の前に **「毎日の」** と入力し、 **[毎日の合計]** と表示します。</span><span class="sxs-lookup"><span data-stu-id="d22cf-144">Type the word **Daily** before the word **Total** in the same cell, so it reads **Daily Total**.</span></span>  
  
3.  <span data-ttu-id="d22cf-145">**[毎日の合計]** セル、2 個の **[合計]** セル、およびその間にある空のセルを選択します。</span><span class="sxs-lookup"><span data-stu-id="d22cf-145">Select the **Daily Total** cell, the two **Sum** cells and the empty cell between them.</span></span>  
  
4.  <span data-ttu-id="d22cf-146">**[書式]** メニューの **[背景色]** をクリックし、 **[オレンジ]** をクリックして、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d22cf-146">On the **Format** menu, click **Background Color**, click **Orange**, and click **OK**.</span></span>  
  
     ![](../../2014/tutorials/media/rs-basictablesumdaytotaldesign.gif "rs_BasicTableSumDayTotalDesign")  
  
##  <a name="to-add-a-grand-total-to-a-report"></a><a name="bkmk_addgrandtotal"></a><span data-ttu-id="d22cf-147">レポートに総計を追加するには</span><span class="sxs-lookup"><span data-stu-id="d22cf-147">To add a grand total to a report</span></span>  
  
1.  <span data-ttu-id="d22cf-148">Date セルを右クリックし、 **[合計の追加]** をポイントして、 **[後]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d22cf-148">Right-click the Date cell, point to **Add Total**, and click **After**.</span></span>  
  
     <span data-ttu-id="d22cf-149">これにより、レポート全体の数量と金額の合計と、列の**合計**ラベルを含む新しい行が追加さ `Date` れます。</span><span class="sxs-lookup"><span data-stu-id="d22cf-149">This adds a new row containing sums of the quantity and dollar amount for the entire report, and the **Total** label in the `Date` column.</span></span>  
  
2.  <span data-ttu-id="d22cf-150">同じセルで **「合計」** の代わりに **「総計」** と入力し、 **[総計]** と表示します。</span><span class="sxs-lookup"><span data-stu-id="d22cf-150">Type the word **Grand** before the word **Total** in the same cell, so it reads **Grand Total**.</span></span>  
  
3.  <span data-ttu-id="d22cf-151">**[総計]** セル、2 個の **[合計]** セル、およびその間にある空のセルを選択します。</span><span class="sxs-lookup"><span data-stu-id="d22cf-151">Select the **Grand Total** cell, the two **Sum** cells and the empty cells between them.</span></span>  
  
4.  <span data-ttu-id="d22cf-152">**[書式]** メニューの **[背景色]** をクリックし、 **[薄い青]** をクリックして、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d22cf-152">On the **Format** menu, click **Background Color**, click **Light Blue**, and click **OK**.</span></span>  
  
     <span data-ttu-id="d22cf-153">![[デザイン] ビュー: 基本的なテーブルの総計](../../2014/tutorials/media/rs-basictablesumgrandtotaldesign.gif "[デザイン] ビュー: 基本的なテーブルの総計")</span><span class="sxs-lookup"><span data-stu-id="d22cf-153">![Design view: Grand total in basic table](../../2014/tutorials/media/rs-basictablesumgrandtotaldesign.gif "Design view: Grand total in basic table")</span></span>  
  
5.  <span data-ttu-id="d22cf-154">[プレビュー] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d22cf-154">Click Preview.</span></span>  
  
     <span data-ttu-id="d22cf-155">最終的なページは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="d22cf-155">The last page should look something like this:</span></span>  
  
     <span data-ttu-id="d22cf-156">![プレビュー: 総計がある基本的なテーブル](../../2014/tutorials/media/rs-basictablesumgrandtotalpreview.gif "プレビュー: 総計がある基本的なテーブル")</span><span class="sxs-lookup"><span data-stu-id="d22cf-156">![Preview: Basic table with grand total](../../2014/tutorials/media/rs-basictablesumgrandtotalpreview.gif "Preview: Basic table with grand total")</span></span>  
  
##  <a name="to-publish-the-report-to-the-report-server-optional"></a><a name="bkmk_publishreport"></a><span data-ttu-id="d22cf-157">レポートをレポートサーバーにパブリッシュするには (省略可能)</span><span class="sxs-lookup"><span data-stu-id="d22cf-157">To Publish the Report to the Report Server (Optional)</span></span>  
  
1.  <span data-ttu-id="d22cf-158">オプションの手順では、完成したレポートをネイティブ モードのレポート サーバーにパブリッシュして、レポート マネージャーでレポートを表示できるようにします。</span><span class="sxs-lookup"><span data-stu-id="d22cf-158">An optional step is to publish the completed report to the native mode report server so you can view the report from Report Manager.</span></span>  
  
2.  <span data-ttu-id="d22cf-159">ツール バーの **[プロジェクト]** をクリックし、 **[チュートリアルのプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d22cf-159">On the toolbar click **Project** and then click **tutorial Properties...**</span></span>  
  
3.  <span data-ttu-id="d22cf-160">[ **TargetServerURL** ] に、レポートサーバーの名前を入力します。たとえば、 **http:// \<servername> /reportserver**と指定します。</span><span class="sxs-lookup"><span data-stu-id="d22cf-160">In the **TargetServerURL** type the name of the name of your report server, for example **http://\<servername>/reportserver**</span></span>  
  
4.  <span data-ttu-id="d22cf-161">**[OK]**</span><span class="sxs-lookup"><span data-stu-id="d22cf-161">Click **OK**</span></span>  
  
5.  <span data-ttu-id="d22cf-162">ツール バーの **[ビルド]** をクリックし、 **[Tutorial の配置]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d22cf-162">On the toolbar click **Build** and then click **Deploy tutorial**.</span></span>  
  
     <span data-ttu-id="d22cf-163">出力ウィンドウに次のようなメッセージが表示されていれば、正常に展開されたことを示しています。</span><span class="sxs-lookup"><span data-stu-id="d22cf-163">If you see a message similar to the following in the output window, it indicates a successful deployment.</span></span>  
  
    > <span data-ttu-id="d22cf-164">------ ビルド開始: プロジェクト: tutorial、構成: デバッグ ------'Sales Orders.rdl' をスキップしています。</span><span class="sxs-lookup"><span data-stu-id="d22cf-164">------ Build started: Project: tutorial, Configuration: Debug ------Skipping 'Sales Orders.rdl'.</span></span> <span data-ttu-id="d22cf-165">項目は最新です。ビルド完了--0 エラー、0警告------配置開始: プロジェクト: チュートリアル、構成: デバッグ------http:// \<server name> /reportserverdeploy report '/Tutorial/Sales Orders ' に配置します。配置完了--0 エラー、0個の警告 = = = = = = = = = = ビルド: 1 成功または最新の状態、0失敗、0スキップ = = = = = = = = = = =、1成功、0失敗、0スキップ = = = = = = = = = = = = = = = = =</span><span class="sxs-lookup"><span data-stu-id="d22cf-165">Item is up to date.Build complete -- 0 errors, 0 warnings------ Deploy started: Project: tutorial, Configuration: Debug ------Deploying to http://\<server name>/reportserverDeploying report '/tutorial/Sales Orders'.Deploy complete -- 0 errors, 0 warnings========== Build: 1 succeeded or up-to-date, 0 failed, 0 skipped ==================== Deploy: 1 succeeded, 0 failed, 0 skipped ==========</span></span>  
  
     <span data-ttu-id="d22cf-166">次のようなメッセージが表示されている場合は、レポート サーバーに対する権限があることと、管理者特権を使用して [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] を開始したことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="d22cf-166">If you see an error message similar to the following, verify you have permissions on the report server and you have started [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] with administrator privileges.</span></span>  
  
    > <span data-ttu-id="d22cf-167">"ユーザー ' XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX \\<ユーザー名 ' に付与されたアクセス許可 \> は、この操作を実行するのに十分ではありません"</span><span class="sxs-lookup"><span data-stu-id="d22cf-167">"The permissions granted to user 'XXXXXXXX\\<your user name\>' are insufficient for performing this operation"</span></span>  
  
6.  <span data-ttu-id="d22cf-168">管理者特権を使用してレポートマネージャーを開始します。たとえば、Internet Explorer のアイコンを右クリックし、[**管理者として実行**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d22cf-168">Start Report Manager with administrator privileges, for example, right-click the icon for Internet Explorer and click **Run as administrator**.</span></span>  
  
     <span data-ttu-id="d22cf-169">レポート マネージャーの URL (たとえば `http://<server name>/reports`) を参照します。</span><span class="sxs-lookup"><span data-stu-id="d22cf-169">Browse to the Report Manager URL, for example: `http://<server name>/reports`.</span></span>  
  
7.  <span data-ttu-id="d22cf-170">レポートを含むフォルダーを参照し、レポート `Sales Orders` の名前をクリックして、表示レポートをブラウザーで表示します。</span><span class="sxs-lookup"><span data-stu-id="d22cf-170">Browse to the folder that contains the report and click the name of the report `Sales Orders` to view the rendered report in the browser.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="d22cf-171">次の手順</span><span class="sxs-lookup"><span data-stu-id="d22cf-171">Next Steps</span></span>  
 <span data-ttu-id="d22cf-172">これで、「基本的なテーブル レポートの作成」チュートリアルを終了します。</span><span class="sxs-lookup"><span data-stu-id="d22cf-172">You have successfully completed the Creating a Basic Table Report tutorial.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d22cf-173">参照</span><span class="sxs-lookup"><span data-stu-id="d22cf-173">See Also</span></span>  
 [<span data-ttu-id="d22cf-174">データのフィルター、グループ化、および並べ替え &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="d22cf-174">Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;</span></span>](report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)  
  
  
