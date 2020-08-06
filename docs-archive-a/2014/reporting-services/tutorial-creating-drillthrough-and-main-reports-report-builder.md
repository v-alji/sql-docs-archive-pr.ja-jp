---
title: 'チュートリアル: 詳細レポートとメイン レポートの作成 (レポート ビルダー) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 7168c8d3-cef5-4c4a-a0bf-fff1ac5b8b71
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d7d30b59a0c5523ed50df06f8587bbd701ae4c79
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737807"
---
# <a name="tutorial-creating-drillthrough-and-main-reports-report-builder"></a><span data-ttu-id="45544-102">チュートリアル: 詳細レポートとメイン レポートの作成 (レポート ビルダー)</span><span class="sxs-lookup"><span data-stu-id="45544-102">Tutorial: Creating Drillthrough and Main Reports (Report Builder)</span></span>
  <span data-ttu-id="45544-103">このチュートリアルでは、詳細レポートとメイン レポートの 2 種類のレポートの作成方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="45544-103">This tutorial teaches you how to create two kinds of reports: a drillthrough report and a main report.</span></span> <span data-ttu-id="45544-104">これらのレポートで使用する売上データのサンプルは、Analysis Services キューブから取得します。</span><span class="sxs-lookup"><span data-stu-id="45544-104">The sample sales data used in these reports is retrieved from an Analysis Services cube.</span></span> <span data-ttu-id="45544-105">次の図は、作成するレポートを示しています。</span><span class="sxs-lookup"><span data-stu-id="45544-105">The following illustration shows the reports you will create.</span></span>  
  
 <span data-ttu-id="45544-106">![rs_DrillthroughCubeTutorial](../../2014/tutorials/media/rs-drillthroughcubetutorial.gif "rs_DrillthroughCubeTutorial")</span><span class="sxs-lookup"><span data-stu-id="45544-106">![rs_DrillthroughCubeTutorial](../../2014/tutorials/media/rs-drillthroughcubetutorial.gif "rs_DrillthroughCubeTutorial")</span></span>  
  
 <span data-ttu-id="45544-107">次の図は、メインレポートのフィールド値 [Games] と [Toys] が詳細レポートのタイトルにどのように表示されるかを示しています。</span><span class="sxs-lookup"><span data-stu-id="45544-107">The following illustration shows how the field value, Games and Toys, in the main report displays in the drillthrough report's title.</span></span> <span data-ttu-id="45544-108">この詳細レポートには、Games and Toys 製品カテゴリに関連するデータが含まれています。</span><span class="sxs-lookup"><span data-stu-id="45544-108">The data in the drillthrough pertains to the Games and Toys product category.</span></span>  
  
 <span data-ttu-id="45544-109">![rs_DrillthroughCubeTutorialParmExpr](../../2014/tutorials/media/rs-drillthroughcubetutorialparmexpr.gif "rs_DrillthroughCubeTutorialParmExpr")</span><span class="sxs-lookup"><span data-stu-id="45544-109">![rs_DrillthroughCubeTutorialParmExpr](../../2014/tutorials/media/rs-drillthroughcubetutorialparmexpr.gif "rs_DrillthroughCubeTutorialParmExpr")</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="45544-110">学習する内容</span><span class="sxs-lookup"><span data-stu-id="45544-110">What You Will Learn</span></span>  
 <span data-ttu-id="45544-111">**詳細レポートでは、次の内容を学習します。**</span><span class="sxs-lookup"><span data-stu-id="45544-111">**In the drillthrough report you will learn how to:**</span></span>  
  
1.  [<span data-ttu-id="45544-112">テーブルまたはマトリックス ウィザードを使用して詳細マトリックス レポートとデータセットを作成する</span><span class="sxs-lookup"><span data-stu-id="45544-112">Create a Drillthrough Matrix Report and Dataset from the Table or Matrix Wizard</span></span>](#DMatrixAndDataset)  
  
    1.  [<span data-ttu-id="45544-113">データ接続を指定する</span><span class="sxs-lookup"><span data-stu-id="45544-113">Specify a Data Connection</span></span>](#DConnection)  
  
    2.  [<span data-ttu-id="45544-114">MDX クエリを作成する</span><span class="sxs-lookup"><span data-stu-id="45544-114">Create an MDX Query</span></span>](#DMDXQuery)  
  
    3.  [<span data-ttu-id="45544-115">データをグループにまとめる</span><span class="sxs-lookup"><span data-stu-id="45544-115">Organize Data into Groups Style</span></span>](#DLayout)  
  
    4.  [<span data-ttu-id="45544-116">小計と合計を追加する</span><span class="sxs-lookup"><span data-stu-id="45544-116">Add Subtotals and Totals</span></span>](#DTotals)  
  
    5.  [<span data-ttu-id="45544-117">スタイルの選択</span><span class="sxs-lookup"><span data-stu-id="45544-117">Choose a Style</span></span>](#DStyle)  
  
2.  [<span data-ttu-id="45544-118">データに通貨の書式を設定する</span><span class="sxs-lookup"><span data-stu-id="45544-118">Format Data as Currency</span></span>](#DFormat)  
  
3.  [<span data-ttu-id="45544-119">売上の値をスパークラインで表示する列を追加する</span><span class="sxs-lookup"><span data-stu-id="45544-119">Add columns to Show Sales Values in Sparklines</span></span>](#DSparkline)  
  
4.  [<span data-ttu-id="45544-120">製品カテゴリ名を含むレポート タイトルを追加する</span><span class="sxs-lookup"><span data-stu-id="45544-120">Add Report Title with Product Category Name</span></span>](#DReportTitle)  
  
5.  [<span data-ttu-id="45544-121">パラメーターのプロパティを更新する</span><span class="sxs-lookup"><span data-stu-id="45544-121">Update Parameter Properties</span></span>](#DParameter)  
  
6.  [<span data-ttu-id="45544-122">レポートを SharePoint ライブラリに保存する</span><span class="sxs-lookup"><span data-stu-id="45544-122">Save the Report to a SharePoint Library</span></span>](#DSave)  
  
 <span data-ttu-id="45544-123">**メイン レポートでは、次の内容を学習します。**</span><span class="sxs-lookup"><span data-stu-id="45544-123">**In the main report you will learn how to:**</span></span>  
  
1.  [<span data-ttu-id="45544-124">テーブルまたはマトリックス ウィザードを使用してメイン マトリックス レポートとデータセットを作成する</span><span class="sxs-lookup"><span data-stu-id="45544-124">Create the Main Matrix Report and Dataset from the Table or Matrix Wizard</span></span>](#MMatrixAndDataset)  
  
    1.  [<span data-ttu-id="45544-125">データ接続を指定する</span><span class="sxs-lookup"><span data-stu-id="45544-125">Specify a Data Connection</span></span>](#MConnection)  
  
    2.  [<span data-ttu-id="45544-126">MDX クエリを作成する</span><span class="sxs-lookup"><span data-stu-id="45544-126">Create an MDX Query</span></span>](#MMDXQuery)  
  
    3.  [<span data-ttu-id="45544-127">データをグループにまとめる</span><span class="sxs-lookup"><span data-stu-id="45544-127">Organize Data into Groups</span></span>](#MLayout)  
  
    4.  [<span data-ttu-id="45544-128">小計と合計を追加する</span><span class="sxs-lookup"><span data-stu-id="45544-128">Add Subtotals and Totals</span></span>](#MTotals)  
  
    5.  [<span data-ttu-id="45544-129">スタイルの選択</span><span class="sxs-lookup"><span data-stu-id="45544-129">Choose a Style</span></span>](#MStyle)  
  
2.  [<span data-ttu-id="45544-130">総計行を削除する</span><span class="sxs-lookup"><span data-stu-id="45544-130">Remove the Grand Total Row</span></span>](#MGrandTotal)  
  
3.  [<span data-ttu-id="45544-131">ドリルスルーのためのテキスト ボックス アクションを構成する</span><span class="sxs-lookup"><span data-stu-id="45544-131">Configure Text Box Action for Drillthrough</span></span>](#MDrillthrough)  
  
4.  [<span data-ttu-id="45544-132">数値をインジケーターに置き換える</span><span class="sxs-lookup"><span data-stu-id="45544-132">Replace Numeric Values with Indicators</span></span>](#MIndicators)  
  
5.  [<span data-ttu-id="45544-133">パラメーターのプロパティを更新する</span><span class="sxs-lookup"><span data-stu-id="45544-133">Update Parameter Properties</span></span>](#MParameter)  
  
6.  [<span data-ttu-id="45544-134">レポートタイトルを追加する</span><span class="sxs-lookup"><span data-stu-id="45544-134">Add a Report Title</span></span>](#MTitle)  
  
7.  [<span data-ttu-id="45544-135">レポートを SharePoint ライブラリに保存する</span><span class="sxs-lookup"><span data-stu-id="45544-135">Save the Report to a SharePoint Library</span></span>](#MSave)  
  
8.  [<span data-ttu-id="45544-136">メイン レポートと詳細レポートを実行する</span><span class="sxs-lookup"><span data-stu-id="45544-136">Run the Main and Drillthrough Reports</span></span>](#MRunReports)  
  
 <span data-ttu-id="45544-137">このチュートリアルの推定所要時間: 30 分。</span><span class="sxs-lookup"><span data-stu-id="45544-137">Estimated time to complete this tutorial: 30 minutes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45544-138">必要条件</span><span class="sxs-lookup"><span data-stu-id="45544-138">Requirements</span></span>  
 <span data-ttu-id="45544-139">このチュートリアルでは、Contoso Sales キューブにアクセスする必要があります。</span><span class="sxs-lookup"><span data-stu-id="45544-139">This tutorial requires access to the Contoso Sales cube.</span></span> <span data-ttu-id="45544-140">この必要条件は、詳細レポートとメイン レポートの両方に適用されます。</span><span class="sxs-lookup"><span data-stu-id="45544-140">This requirement applies to both the drillthrough and the main reports.</span></span> <span data-ttu-id="45544-141">要件に関する詳細については、「[チュートリアルの前提条件 (レポート ビルダー)](../reporting-services/report-builder-tutorials.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="45544-141">For more information about requirements, see [Prerequisites for Tutorials &#40;Report Builder&#41;](../reporting-services/report-builder-tutorials.md).</span></span>  
  
##  <a name="1-create-a-drillthrough-report-from-the-table-or-matrix-wizard"></a><a name="DMatrixAndDataset"></a><span data-ttu-id="45544-142">1. テーブルまたはマトリックスウィザードから詳細レポートを作成する</span><span class="sxs-lookup"><span data-stu-id="45544-142">1. Create a Drillthrough Report from the Table or Matrix Wizard</span></span>  
 <span data-ttu-id="45544-143">[作業の開始] ダイアログ ボックスから、 **テーブルまたはマトリックス ウィザード**を使用してマトリックス レポートを作成します。</span><span class="sxs-lookup"><span data-stu-id="45544-143">From the Getting Started dialog box, create a matrix report by using the **Table or Matrix Wizard**.</span></span> <span data-ttu-id="45544-144">このウィザードには、レポート デザイン モードと共有データセット デザイン モードの 2 つのモードがあります。</span><span class="sxs-lookup"><span data-stu-id="45544-144">There are two modes available in the wizard: report design and shared dataset design.</span></span> <span data-ttu-id="45544-145">このチュートリアルでは、レポート デザイン モードを使用します。</span><span class="sxs-lookup"><span data-stu-id="45544-145">In this tutorial, you will use the report design mode.</span></span>  
  
#### <a name="to-create-a-new-report"></a><span data-ttu-id="45544-146">新しいレポートを作成するには</span><span class="sxs-lookup"><span data-stu-id="45544-146">To create a new report</span></span>  
  
1.  <span data-ttu-id="45544-147">[**スタート**] をクリックし、[**プログラム**]、[レポートビルダー] の順にポイントし、[ [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)] **Report Builder\*\*\*\*レポートビルダー**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-147">Click **Start**, point to **Programs**, point to [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)] **Report Builder**, and then click **Report Builder**.</span></span>  
  
     <span data-ttu-id="45544-148">**[作業の開始]** ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="45544-148">The **Getting Started** dialog box opens.</span></span> <span data-ttu-id="45544-149">表示されない場合は、[**レポートビルダー** ] ボタンの [**新規**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-149">If it does not appear, from the **Report Builder** button, click **New**.</span></span>  
  
2.  <span data-ttu-id="45544-150">左ペインで、 **[新しいレポート]** が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="45544-150">In the left pane, verify that **New Report** is selected.</span></span>  
  
3.  <span data-ttu-id="45544-151">右ペインで、 **[テーブルまたはマトリックス ウィザード]** が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="45544-151">In the right pane, verify that **Table or Matrix Wizard** is selected.</span></span>  
  
##  <a name="1a-specify-a-data-connection"></a><a name="DConnection"></a><span data-ttu-id="45544-152">sr-1.</span><span class="sxs-lookup"><span data-stu-id="45544-152">1a.</span></span> <span data-ttu-id="45544-153">データ接続を指定する</span><span class="sxs-lookup"><span data-stu-id="45544-153">Specify a Data Connection</span></span>  
 <span data-ttu-id="45544-154">データ接続には、Analysis Services キューブや [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] データベースなどの外部データ ソースに接続するときに必要な情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="45544-154">A data connection contains the information necessary to connect to an external data source such as an Analysis Services cube or a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database.</span></span> <span data-ttu-id="45544-155">データ接続を指定するには、レポート サーバーの共有データ ソースを使用するか、このレポートでのみ使用する埋め込みデータ ソースを作成します。</span><span class="sxs-lookup"><span data-stu-id="45544-155">To specify a data connection, you can use a shared data source from the report server or create an embedded data source that is used only in this report.</span></span> <span data-ttu-id="45544-156">このチュートリアルでは、埋め込みデータ ソースを使用します。</span><span class="sxs-lookup"><span data-stu-id="45544-156">In this tutorial, you will use an embedded data source.</span></span> <span data-ttu-id="45544-157">共有データ ソースの使用方法の詳細については、「[別の方法でデータ接続を取得する (レポート ビルダー)](../reporting-services/alternative-ways-to-get-a-data-connection-report-builder.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="45544-157">To learn more about using a shared data source, see [Alternative Ways to Get a Data Connection &#40;Report Builder&#41;](../reporting-services/alternative-ways-to-get-a-data-connection-report-builder.md).</span></span>  
  
#### <a name="to-create-an-embedded-data-source"></a><span data-ttu-id="45544-158">埋め込みデータ ソースを作成するには</span><span class="sxs-lookup"><span data-stu-id="45544-158">To create an embedded data source</span></span>  
  
1.  <span data-ttu-id="45544-159">**[データセットの選択]** ページで **[データセットを作成する]** を選択し、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-159">On the **Choose a dataset** page, select **Create a dataset**, and then click **Next**.</span></span> <span data-ttu-id="45544-160">**[データ ソースへの接続の選択]** ページが開きます。</span><span class="sxs-lookup"><span data-stu-id="45544-160">The **Choose a connection to a data source** page opens.</span></span>  
  
2.  <span data-ttu-id="45544-161">**[新規作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-161">Click **New**.</span></span> <span data-ttu-id="45544-162">**[データ ソースのプロパティ]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="45544-162">The **Data Source Properties** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="45544-163">**[名前]** に、データ ソースの名前として「 **Online and Reseller Sales Detail** 」と入力します。</span><span class="sxs-lookup"><span data-stu-id="45544-163">In **Name**, type **Online and Reseller Sales Detail** as the name for the data source.</span></span>  
  
4.  <span data-ttu-id="45544-164">**[接続の種類の選択]** で、 **[Microsoft SQL Server Analysis Services]** を選択し、 **[構築]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-164">In **Select a connection type**, select **Microsoft SQL Server Analysis Services**, and then click **Build**.</span></span>  
  
5.  <span data-ttu-id="45544-165">**[データ ソース]** で、データ ソースが **[Microsoft SQL Server Analysis Services (AdomdClient)]** になっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="45544-165">In **Data source**, verify that the data source is **Microsoft SQL Server Analysis Services (AdomdClient)**.</span></span>  
  
6.  <span data-ttu-id="45544-166">**[サーバー名]** に、Analysis Services のインスタンスがインストールされているサーバーの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="45544-166">In **Server name**, type the name of a server where an instance of Analysis Services is installed.</span></span>  
  
7.  <span data-ttu-id="45544-167">**[データベース名の選択または入力]** で、Contoso キューブを選択します。</span><span class="sxs-lookup"><span data-stu-id="45544-167">In **Select or enter a database name**, select the Contoso cube.</span></span>  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
9. <span data-ttu-id="45544-168">**[接続文字列]** に次の構文が含まれていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="45544-168">Verify that **Connection string** contains the following syntax:</span></span>  
  
    ```  
    Data Source=<servername>; Initial Catalog = Contoso  
    ```  
  
     <span data-ttu-id="45544-169">`<servername>` は、Analysis Services がインストールされている [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスの名前です。</span><span class="sxs-lookup"><span data-stu-id="45544-169">The `<servername>` is the name of an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] with Analysis Services installed.</span></span>  
  
10. <span data-ttu-id="45544-170">**[資格情報の種類]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-170">Click **Credentials type**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="45544-171">データ ソースの権限の構成によっては、既定の認証オプションを変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="45544-171">Depending on how permissions are configured on the data source, you might need to change the default authentication options.</span></span> <span data-ttu-id="45544-172">詳細については、「 [セキュリティ (レポート ビルダー)](report-builder/security-report-builder.md)で作成するモバイル レポートで使用できます。</span><span class="sxs-lookup"><span data-stu-id="45544-172">For more information, see [Security &#40;Report Builder&#41;](report-builder/security-report-builder.md).</span></span>  
  
11. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     <span data-ttu-id="45544-173">**[データ ソースへの接続の選択]** ページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="45544-173">The **Choose a connection to a data source** page appears.</span></span>  
  
12. <span data-ttu-id="45544-174">データ ソースに接続できることを確認するために、 **[接続テスト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-174">To verify that you can connect to the data source, click **Test Connection**.</span></span>  
  
     <span data-ttu-id="45544-175">**正常に作成されたメッセージ接続**が表示されます。</span><span class="sxs-lookup"><span data-stu-id="45544-175">The message **Connection created successfully** appears.</span></span>  
  
13. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
14. <span data-ttu-id="45544-176">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-176">Click **Next**.</span></span>  
  
##  <a name="1b-create-an-mdx-query"></a><a name="DMDXQuery"></a><span data-ttu-id="45544-177">ドル.</span><span class="sxs-lookup"><span data-stu-id="45544-177">1b.</span></span> <span data-ttu-id="45544-178">MDX クエリを作成する</span><span class="sxs-lookup"><span data-stu-id="45544-178">Create an MDX Query</span></span>  
 <span data-ttu-id="45544-179">レポートでは、クエリが事前に定義された共有データセットを使用するか、そのレポートでのみ使用する埋め込みデータセットを作成できます。</span><span class="sxs-lookup"><span data-stu-id="45544-179">In a report, you can use a shared dataset that has a predefined query, or you can create an embedded dataset for use only in your report.</span></span> <span data-ttu-id="45544-180">このチュートリアルでは、埋め込みデータセットを作成します。</span><span class="sxs-lookup"><span data-stu-id="45544-180">In this tutorial, you will create an embedded dataset.</span></span>  
  
#### <a name="to-create-query-filters"></a><span data-ttu-id="45544-181">クエリ フィルターを作成するには</span><span class="sxs-lookup"><span data-stu-id="45544-181">To create query filters</span></span>  
  
1.  <span data-ttu-id="45544-182">[**クエリのデザイン**] ページのメタデータペインで、[ **...**] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-182">On the **Design a query** page, in the Metadata pane, click the button **(...)**.</span></span>  
  
2.  <span data-ttu-id="45544-183">**[キューブの選択]** ダイアログ ボックスで、Sales をクリックし、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-183">In the **Cube Selection** dialog box, click Sales, and then click **OK**.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="45544-184">MDX クエリを手動で作成しない場合は、![デザイン モードへの切り替え](media/rsqdicon-designmode.gif "デザイン モードに切り替える") アイコンをクリックしてクエリ デザイナーをクエリ モードに切り替え、完成した MDX をクエリ デザイナーに貼り付けます。その後、「[データセットを作成するには](#DSkip)」の手順 6 に進みます。</span><span class="sxs-lookup"><span data-stu-id="45544-184">If you do not want to build the MDX query manually, click the ![Switch to Design mode](media/rsqdicon-designmode.gif "Switch to Design mode") icon, toggle the query designer to Query mode, paste the completed MDX to the query designer, and then proceed to step 6 in [To create the dataset](#DSkip).</span></span>  
  
    ```  
    SELECT NON EMPTY { [Measures].[Sales Amount], [Measures].[Sales Return Amount] } ON COLUMNS, NON EMPTY { ([Channel].[Channel Name].[Channel Name].ALLMEMBERS * [Product].[Product Category Name].[Product Category Name].ALLMEMBERS * [Product].[Product Subcategory Name].[Product Subcategory Name].ALLMEMBERS ) } DIMENSION PROPERTIES MEMBER_CAPTION, MEMBER_UNIQUE_NAME ON ROWS FROM ( SELECT ( { [Date].[Calendar Year].&[2009] } ) ON COLUMNS FROM ( SELECT ( { [Sales Territory].[Sales Territory Group].&[North America] } ) ON COLUMNS FROM ( SELECT ( STRTOSET(@ProductProductCategoryName, CONSTRAINED) ) ON COLUMNS FROM ( SELECT ( { [Channel].[Channel Name].&[2], [Channel].[Channel Name].&[4] } ) ON COLUMNS FROM [Sales])))) WHERE ( [Sales Territory].[Sales Territory Group].&[North America], [Date].[Calendar Year].&[2009] ) CELL PROPERTIES VALUE, BACK_COLOR, FORE_COLOR, FORMATTED_VALUE, FORMAT_STRING, FONT_NAME, FONT_SIZE, FONT_FLAGS  
    ```  
  
3.  <span data-ttu-id="45544-185">メジャー グループ ペインで Channel を展開し、Channel Name をフィルター ペインの **[階層]** 列にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="45544-185">In the Measure Group pane, expand Channel, and then drag Channel Name to the **Hierarchy** column in the filter pane.</span></span>  
  
     <span data-ttu-id="45544-186">Channel というディメンション名が自動的に **[ディメンション]** 列に追加されます。</span><span class="sxs-lookup"><span data-stu-id="45544-186">The dimension name, Channel, is automatically added to the **Dimension** column.</span></span> <span data-ttu-id="45544-187">**[ディメンション]** 列と **[演算子]** 列は変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="45544-187">Do not change the **Dimension** or **Operator** columns.</span></span>  
  
4.  <span data-ttu-id="45544-188">**[フィルター式]** 列の下矢印をクリックして、 **[フィルター式]** の一覧を開きます。</span><span class="sxs-lookup"><span data-stu-id="45544-188">To open the **Filter Expression** list, click the down arrow in the **Filter Expression** column.</span></span>  
  
5.  <span data-ttu-id="45544-189">フィルター式の一覧で、 **[All Channel]** を展開し、 **[Online]** と **[Reseller]** をクリックして、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-189">In the filter expression list, expand **All Channel**, click **Online**, click **Reseller**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="45544-190">Channel を Online と Reseller のみに制限するフィルターがクエリに追加されます。</span><span class="sxs-lookup"><span data-stu-id="45544-190">The query now includes a filter to include only these channels: Online and Reseller.</span></span>  
  
6.  <span data-ttu-id="45544-191">Sales Territory ディメンションを展開し、Sales Territory Group を **[階層]** 列 ( **Channel Name**の下) にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="45544-191">Expand the Sales Territory dimension, and then drag Sales Territory Group to the **Hierarchy** column (below **Channel Name**).</span></span>  
  
7.  <span data-ttu-id="45544-192">**[フィルター式]** の一覧を開き、 **[All Sales Territory]** を展開して **[North America]** をクリックし、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-192">Open the **Filter Expression** list, expand **All Sales Territory**, click **North America**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="45544-193">North America の売上のみを含めるフィルターがクエリに追加されます。</span><span class="sxs-lookup"><span data-stu-id="45544-193">The query now has a filter to include only sales in North America.</span></span>  
  
8.  <span data-ttu-id="45544-194">メジャー グループ ペインで Date を展開し、Calendar Year をフィルター ペインの **[階層]** 列にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="45544-194">In the Measure Group pane, expand Date, and then drag Calendar Year to the **Hierarchy** column in the filter pane.</span></span>  
  
     <span data-ttu-id="45544-195">Date というディメンション名が自動的に **[ディメンション]** 列に追加されます。</span><span class="sxs-lookup"><span data-stu-id="45544-195">The dimension name, Date, is automatically added to the **Dimension** column.</span></span> <span data-ttu-id="45544-196">**[ディメンション]** 列と **[演算子]** 列は変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="45544-196">Do not change the **Dimension** or **Operator** columns.</span></span>  
  
9. <span data-ttu-id="45544-197">**[フィルター式]** 列の下矢印をクリックして、 **[フィルター式]** の一覧を開きます。</span><span class="sxs-lookup"><span data-stu-id="45544-197">To open the **Filter Expression** list, click the down arrow in the **Filter Expression** column.</span></span>  
  
10. <span data-ttu-id="45544-198">フィルター式の一覧で、 **[All Date]** を展開し、 **[Year 2009]** をクリックして、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-198">In the filter expression list, expand **All Date**, click **Year 2009**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="45544-199">2009 年のデータのみを含めるフィルターがクエリに追加されます。</span><span class="sxs-lookup"><span data-stu-id="45544-199">The query now includes a filter to include only the calendar year 2009.</span></span>  
  
#### <a name="to-create-the-parameter"></a><span data-ttu-id="45544-200">パラメーターを作成するには</span><span class="sxs-lookup"><span data-stu-id="45544-200">To create the parameter</span></span>  
  
1.  <span data-ttu-id="45544-201">Product ディメンションを展開し、Product Category Name メンバーを **[階層]** 列 ( **Calendar Year**の下) にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="45544-201">Expand the Product dimension, and then drag the Product Category Name member to the **Hierarchy** column below **Calendar Year**.</span></span>  
  
2.  <span data-ttu-id="45544-202">**[フィルター式]** の一覧を開き、 **[All Products]** をクリックして、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-202">Open the **Filter Expression** list, click **All Products**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="45544-203">**[パラメーター]** チェック ボックスをクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-203">Click the **Parameter** checkbox.</span></span> <span data-ttu-id="45544-204">パラメーター ProductProductCategoryName がクエリに追加されます。</span><span class="sxs-lookup"><span data-stu-id="45544-204">The query now includes the parameter ProductProductCategoryName.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="45544-205">このパラメーターは、製品カテゴリの名前を格納します。</span><span class="sxs-lookup"><span data-stu-id="45544-205">The parameter contains the names of product categories.</span></span> <span data-ttu-id="45544-206">メイン レポートで製品カテゴリの名前をクリックすると、その名前が、このパラメーターを使用して詳細レポートに渡されます。</span><span class="sxs-lookup"><span data-stu-id="45544-206">When you click a product category name in the main report, its name is passed to the drillthrough report by using this parameter.</span></span>  
  
###  <a name="to-create-the-dataset"></a><a name="DSkip"></a><span data-ttu-id="45544-207">データセットを作成するには</span><span class="sxs-lookup"><span data-stu-id="45544-207">To create the dataset</span></span>  
  
1.  <span data-ttu-id="45544-208">Channel ディメンションから Channel Name をデータ ペインにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="45544-208">From the Channel dimension, drag Channel Name to the data pane.</span></span>  
  
2.  <span data-ttu-id="45544-209">Product ディメンションから Product Category Name をデータ ペインにドラッグして、Channel Name の右側に配置します。</span><span class="sxs-lookup"><span data-stu-id="45544-209">From the Product dimension, drag Product Category Name to the data pane, and then place it to the right of Channel Name.</span></span>  
  
3.  <span data-ttu-id="45544-210">Product ディメンションから Product Subcategory Name をデータ ペインにドラッグして、Product Category Name の右側に配置します。</span><span class="sxs-lookup"><span data-stu-id="45544-210">From the Product dimension, drag Product Subcategory Name to the data pane, and then place it to the right of Product Category Name.</span></span>  
  
4.  <span data-ttu-id="45544-211">メタデータ ペインで、 **[メジャー]**、Sales の順に展開します。</span><span class="sxs-lookup"><span data-stu-id="45544-211">In the Metadata pane, expand **Measure**, and then expand Sales.</span></span>  
  
5.  <span data-ttu-id="45544-212">Sales Amount メジャーをデータ ペインにドラッグして、Product Subcategory Name の右側に配置します。</span><span class="sxs-lookup"><span data-stu-id="45544-212">Drag the Sales Amount measure to the data pane, and then place it to the right of Product Subcategory Name.</span></span>  
  
6.  <span data-ttu-id="45544-213">クエリデザイナーのツールバーで、[**実行] (!)** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-213">On the query designer toolbar, click **Run (!)**.</span></span>  
  
7.  <span data-ttu-id="45544-214">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-214">Click **Next**.</span></span>  
  
##  <a name="1c-organize-data-into-groups"></a><a name="DLayout"></a><span data-ttu-id="45544-215">1c.</span><span class="sxs-lookup"><span data-stu-id="45544-215">1c.</span></span> <span data-ttu-id="45544-216">データをグループにまとめる</span><span class="sxs-lookup"><span data-stu-id="45544-216">Organize Data into Groups</span></span>  
 <span data-ttu-id="45544-217">データをグループ化するフィールドを選択し、詳細データおよび集計データを表示する行と列を含むマトリックスをデザインします。</span><span class="sxs-lookup"><span data-stu-id="45544-217">When you select the fields on which to group the data, you design a matrix with rows and columns that displays detail and aggregated data.</span></span>  
  
#### <a name="to-organize-data-into-groups"></a><span data-ttu-id="45544-218">データをグループにまとめるには</span><span class="sxs-lookup"><span data-stu-id="45544-218">To organize data into groups</span></span>  
  
1.  <span data-ttu-id="45544-219">デザイン ビューに切り替えるには、 **[デザイン]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-219">To switch to design view, click **Design**.</span></span>  
  
2.  <span data-ttu-id="45544-220">**[フィールドの配置]** ページで、Product_Subcategory_Name を **[行グループ]** にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="45544-220">On the **Arrange fields** page, drag Product_Subcategory_Name to **Row groups**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="45544-221">名前のスペースはアンダースコア (_) に置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="45544-221">The spaces in the names are replaced with underscores (_).</span></span> <span data-ttu-id="45544-222">たとえば、Product Category Name は Product_Category_Name になります。</span><span class="sxs-lookup"><span data-stu-id="45544-222">For example Product Category Name is Product_Category_Name.</span></span>  
  
3.  <span data-ttu-id="45544-223">Channel_Name を **[列グループ]** にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="45544-223">Drag Channel_Name to **Column groups**.</span></span>  
  
4.  <span data-ttu-id="45544-224">Sales_Amount を **[値]** にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="45544-224">Drag Sales_Amount to **Values**.</span></span>  
  
     <span data-ttu-id="45544-225">Sales_Amount は Sum 関数 (数値フィールドの既定の集計関数) を使用して自動的に集計されます。</span><span class="sxs-lookup"><span data-stu-id="45544-225">Sales_Amount is automatically aggregated by the Sum function, the default aggregate for numeric fields.</span></span> <span data-ttu-id="45544-226">値は `[Sum(Sales_Amount)]` です。</span><span class="sxs-lookup"><span data-stu-id="45544-226">The value is `[Sum(Sales_Amount)]`.</span></span>  
  
     <span data-ttu-id="45544-227">使用可能なその他の集計関数を表示するには、ドロップダウン リストを開きます (集計関数は変更しないでください)。</span><span class="sxs-lookup"><span data-stu-id="45544-227">To view the other aggregate functions available, open the drop-down list (do not change the aggregate function).</span></span>  
  
5.  <span data-ttu-id="45544-228">Sales_Return_Amount を **[値]** にドラッグして、 `[Sum(Sales_Amount)]`の下に配置します。</span><span class="sxs-lookup"><span data-stu-id="45544-228">Drag Sales_Return_Amount to **Values**, and then place it below `[Sum(Sales_Amount)]`.</span></span>  
  
     <span data-ttu-id="45544-229">手順 4. および 5. で、マトリックスに表示するデータを指定します。</span><span class="sxs-lookup"><span data-stu-id="45544-229">Steps 4 and 5 specify the data to display in the matrix.</span></span>  
  
6.  <span data-ttu-id="45544-230">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-230">Click **Next**.</span></span>  
  
##  <a name="1d-add-subtotals-and-totals"></a><a name="DTotals"></a><span data-ttu-id="45544-231">引か.</span><span class="sxs-lookup"><span data-stu-id="45544-231">1d.</span></span> <span data-ttu-id="45544-232">小計と合計を追加する</span><span class="sxs-lookup"><span data-stu-id="45544-232">Add Subtotals and Totals</span></span>  
 <span data-ttu-id="45544-233">グループを作成したら、フィールドの集計値を表示する行を追加して書式を設定できます。</span><span class="sxs-lookup"><span data-stu-id="45544-233">After you create groups, you can add and format rows where the aggregate values for the fields will display.</span></span> <span data-ttu-id="45544-234">すべてのデータを表示するか、グループ化されたデータの展開と折りたたみをユーザーが対話的に行えるようにするかも選択できます。</span><span class="sxs-lookup"><span data-stu-id="45544-234">You can also choose whether to show all the data or to let a user expand and collapse grouped data interactively.</span></span>  
  
#### <a name="to-add-subtotals-and-totals"></a><span data-ttu-id="45544-235">小計と合計を追加するには</span><span class="sxs-lookup"><span data-stu-id="45544-235">To add subtotals and totals</span></span>  
  
1.  <span data-ttu-id="45544-236">[**レイアウトの選択**] ページの [**オプション**] で、[**小計と総計を表示**する] が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="45544-236">On the **Choose the layout** page, under **Options**, verify that **Show subtotals and grand totals** is selected.</span></span>  
  
     <span data-ttu-id="45544-237">ウィザードのプレビュー ペインに、4 行を含むマトリックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="45544-237">The wizard Preview pane displays a matrix with four rows.</span></span>  
  
2.  <span data-ttu-id="45544-238">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-238">Click **Next**.</span></span>  
  
##  <a name="1e-choose-a-style"></a><a name="DStyle"></a><span data-ttu-id="45544-239">1e.</span><span class="sxs-lookup"><span data-stu-id="45544-239">1e.</span></span> <span data-ttu-id="45544-240">スタイルを選択する</span><span class="sxs-lookup"><span data-stu-id="45544-240">Choose a Style</span></span>  
 <span data-ttu-id="45544-241">スタイルは、フォント スタイル、色、および罫線のスタイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="45544-241">A style specifies a font style, a set of colors, and a border style.</span></span>  
  
#### <a name="to-specify-a-style"></a><span data-ttu-id="45544-242">スタイルを指定するには</span><span class="sxs-lookup"><span data-stu-id="45544-242">To specify a style</span></span>  
  
1.  <span data-ttu-id="45544-243">[**スタイルの選択**] ページのスタイルペインで、[スレート] を選択します。</span><span class="sxs-lookup"><span data-stu-id="45544-243">On the **Choose a Style** page, in the Styles pane, select Slate.</span></span>  
  
2.  <span data-ttu-id="45544-244">**[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-244">Click **Finish**.</span></span>  
  
     <span data-ttu-id="45544-245">テーブルがデザイン画面に追加されます。</span><span class="sxs-lookup"><span data-stu-id="45544-245">The table is added to the design surface.</span></span>  
  
3.  <span data-ttu-id="45544-246">レポートをプレビューするには、 **[実行 (!)]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-246">To preview the report, click **Run (!)**.</span></span>  
  
##  <a name="2-format-data-as-currency"></a><a name="DFormat"></a><span data-ttu-id="45544-247">2. データを通貨として書式設定する</span><span class="sxs-lookup"><span data-stu-id="45544-247">2. Format Data as Currency</span></span>  
 <span data-ttu-id="45544-248">詳細レポートの売上高のフィールドに通貨の書式設定を適用します。</span><span class="sxs-lookup"><span data-stu-id="45544-248">Apply currency formatting to the sales amount fields in the drillthrough report.</span></span>  
  
#### <a name="to-format-data-as-currency"></a><span data-ttu-id="45544-249">データに通貨の書式を設定するには</span><span class="sxs-lookup"><span data-stu-id="45544-249">To format data as currency</span></span>  
  
1.  <span data-ttu-id="45544-250">デザイン ビューに切り替えるには、 **[デザイン]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-250">To switch to design view, click **Design**.</span></span>  
  
2.  <span data-ttu-id="45544-251">複数のセルを選択して一度に書式を設定するには、Ctrl キーを押して、数値の売上データを含むセルを選択します。</span><span class="sxs-lookup"><span data-stu-id="45544-251">To select and format multiple cells at one time, press the Ctrl key, and then select the cells that contain the numeric sales data.</span></span>  
  
3.  <span data-ttu-id="45544-252">**[ホーム]** タブの **[数値]** グループで、 **[通貨]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-252">On the **Home** tab, in the **Number** group, click **Currency**.</span></span>  
  
##  <a name="3-add-columns-to-show-sales-values-in-sparklines"></a><a name="DSparkline"></a><span data-ttu-id="45544-253">3. 売上の値をスパークラインで表示する列を追加する</span><span class="sxs-lookup"><span data-stu-id="45544-253">3. Add Columns to Show Sales Values in Sparklines</span></span>  
 <span data-ttu-id="45544-254">このレポートでは、売上と売上返品を、通貨値ではなくスパークラインで表示します。</span><span class="sxs-lookup"><span data-stu-id="45544-254">Instead of showing sales and sales returns as currency values, the report shows the values in a sparkline.</span></span>  
  
#### <a name="to-add-sparklines-to-columns"></a><span data-ttu-id="45544-255">列にスパークラインを追加するには</span><span class="sxs-lookup"><span data-stu-id="45544-255">To add sparklines to columns</span></span>  
  
1.  <span data-ttu-id="45544-256">デザイン ビューに切り替えるには、 **[デザイン]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-256">To switch to design view, click **Design**.</span></span>  
  
2.  <span data-ttu-id="45544-257">マトリックスの合計グループで、 **[Sales Amount]** 列を右クリックし、 **[列の挿入]** をクリックして、 **[右]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-257">In the Total group of the matrix, right-click the **Sales Amount** column, click **Insert Column**, and then click **Right**.</span></span>  
  
     <span data-ttu-id="45544-258">**[Sales Amount]** の右側に空の列が追加されます。</span><span class="sxs-lookup"><span data-stu-id="45544-258">An empty column is added to the right of **Sales Amount**.</span></span>  
  
3.  <span data-ttu-id="45544-259">リボンで **[四角形]** をクリックし、Product_Subcategory 行グループの `[Sum(Sales_Amount)]` セルの右側にある空のセルをクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-259">On the ribbon, click **Rectangle**, and then click the empty cell to the right of the `[Sum(Sales_Amount)]` cell in the [Product_Subcategory] row group.</span></span>  
  
4.  <span data-ttu-id="45544-260">リボンで **[スパークライン]** アイコンをクリックし、四角形を追加したセルをクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-260">On the ribbon, click the **Sparkline** icon, and then click the cell where the rectangle was added.</span></span>  
  
5.  <span data-ttu-id="45544-261">**[スパークラインの種類を選択]** ダイアログ ボックスで、 **[縦棒]** が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="45544-261">In the **Select Sparkline Type** dialog box, verify that **Column** type is selected.</span></span>  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
7.  <span data-ttu-id="45544-262">スパークラインを右クリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-262">Right-click the sparkline.</span></span>  
  
8.  <span data-ttu-id="45544-263">グラフ データ ペインで、 **[フィールドの追加]** アイコンをクリックし、Sales_Amount をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-263">In the Chart Data pane, click the **Add field** icon, and then click Sales_Amount.</span></span>  
  
9. <span data-ttu-id="45544-264">`Sales_Return_Amount` 列を右クリックし、右側に列を追加します。</span><span class="sxs-lookup"><span data-stu-id="45544-264">Right-click the `Sales_Return_Amount` column, and then add a column to the right of it.</span></span>  
  
10. <span data-ttu-id="45544-265">手順 2. ～ 6. を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="45544-265">Repeat steps 2 through 6.</span></span>  
  
11. <span data-ttu-id="45544-266">スパークラインを右クリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-266">Right-click the sparkline.</span></span>  
  
12. <span data-ttu-id="45544-267">グラフ データ ペインで、 **[フィールドの追加]** アイコンをクリックし、Sales_Return_Amount をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-267">In the Chart Data pane, click the **Add field** icon, and then click Sales_Return_Amount.</span></span>  
  
13. <span data-ttu-id="45544-268">レポートをプレビューするには、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-268">To preview the report, click **Run**.</span></span>  
  
##  <a name="4-add-report-title-with-product-category-name"></a><a name="DReportTitle"></a><span data-ttu-id="45544-269">4. 製品カテゴリ名を含むレポートタイトルを追加する</span><span class="sxs-lookup"><span data-stu-id="45544-269">4. Add Report Title with Product Category Name</span></span>  
 <span data-ttu-id="45544-270">レポート タイトルは、レポートの最上部に表示されます。</span><span class="sxs-lookup"><span data-stu-id="45544-270">A report title appears at the top of the report.</span></span> <span data-ttu-id="45544-271">レポート ヘッダーがあれば、そこにレポート タイトルを配置します。レポート ヘッダーを使用しない場合は、レポート本文の一番上のテキスト ボックスに配置します。</span><span class="sxs-lookup"><span data-stu-id="45544-271">You can place the report title in a report header or, if the report does not use one, in a text box at the top of the report body.</span></span> <span data-ttu-id="45544-272">このチュートリアルでは、自動的にレポート本文の一番上に配置されるテキスト ボックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="45544-272">In this tutorial, you will use the text box that is automatically placed at the top of the report body.</span></span>  
  
#### <a name="to-add-a-report-title"></a><span data-ttu-id="45544-273">レポート タイトルを追加するには</span><span class="sxs-lookup"><span data-stu-id="45544-273">To add a report title</span></span>  
  
1.  <span data-ttu-id="45544-274">デザイン ビューに切り替えるには、 **[デザイン]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-274">To switch to design view, click **Design**.</span></span>  
  
2.  <span data-ttu-id="45544-275">デザイン画面で、 **[クリックしてタイトルを追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-275">On the design surface, click **Click to add title**.</span></span>  
  
3.  <span data-ttu-id="45544-276">「 **Sales and Returns for Category:**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="45544-276">Type **Sales and Returns for Category:**.</span></span>  
  
4.  <span data-ttu-id="45544-277">右クリックして **[プレースホルダーの作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-277">Right-click, and then click **Create Placeholder**.</span></span>  
  
5.  <span data-ttu-id="45544-278">**[値]** ボックスの一覧の右側にある **[(fx)]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-278">Click the **(fx)** button to the right of the **Value** list.</span></span>  
  
6.  <span data-ttu-id="45544-279">**[式]** ダイアログ ボックスのカテゴリ ペインで **[データセット]** をクリックし、 **[値]** ボックスの一覧で `First(Product_Category_Name)`をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-279">In the **Expression** dialog box, in the Category pane, click **Dataset**, and then in the **Values** list double-click `First(Product_Category_Name)`.</span></span>  
  
     <span data-ttu-id="45544-280">**[式]** ボックスに次の式が含まれます。</span><span class="sxs-lookup"><span data-stu-id="45544-280">The **Expression** box contains the following expression:</span></span>  
  
    ```  
    =First(Fields!Product_Category_Name.Value, "DataSet1")  
    ```  
  
7.  <span data-ttu-id="45544-281">レポートをプレビューするには、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-281">To preview the report, click **Run**.</span></span>  
  
 <span data-ttu-id="45544-282">レポート タイトルに含まれるのは、最初の製品カテゴリの名前です。</span><span class="sxs-lookup"><span data-stu-id="45544-282">The report title includes the name of the first product category.</span></span> <span data-ttu-id="45544-283">この後の手順でこのレポートを詳細レポートとして実行すると、メイン レポートでクリックした製品カテゴリの名前を反映して製品カテゴリの名前が動的に変化します。</span><span class="sxs-lookup"><span data-stu-id="45544-283">Later, after you run this report as a drillthrough report, the product category name will dynamically change to reflect the name of the product category that was clicked in the main report.</span></span>  
  
##  <a name="5-update-parameter-properties"></a><a name="DParameter"></a><span data-ttu-id="45544-284">5. パラメーターのプロパティを更新する</span><span class="sxs-lookup"><span data-stu-id="45544-284">5. Update Parameter Properties</span></span>  
 <span data-ttu-id="45544-285">既定ではパラメーターが表示されますが、この設定は、このレポートには適していません。</span><span class="sxs-lookup"><span data-stu-id="45544-285">By default parameters are visible, which is not appropriate for this report.</span></span> <span data-ttu-id="45544-286">したがって、詳細レポートのパラメーターのプロパティを更新します。</span><span class="sxs-lookup"><span data-stu-id="45544-286">You will update the parameter properties for the drillthrough report.</span></span>  
  
#### <a name="to-hide-a-parameter"></a><span data-ttu-id="45544-287">パラメーターを非表示にするには</span><span class="sxs-lookup"><span data-stu-id="45544-287">To hide a parameter</span></span>  
  
1.  <span data-ttu-id="45544-288">レポート データ ペインで **[パラメーター]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="45544-288">In the Report Data pane, expand **Parameters**.</span></span>  
  
2.  <span data-ttu-id="45544-289">[ \@ Productproductcategoryname を右クリックし、[**パラメーターのプロパティ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-289">Right-click \@ProductProductCategoryName, and then click **Parameter Properties**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="45544-290">名前の横の \@ 文字は、これがパラメーターであることを示しています。</span><span class="sxs-lookup"><span data-stu-id="45544-290">The \@ character next to the name indicates that this is a parameter.</span></span>  
  
3.  <span data-ttu-id="45544-291">**[全般]** タブで **[非表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-291">On the **General** tab, click **Hidden**.</span></span>  
  
4.  <span data-ttu-id="45544-292">**[プロンプト]** ボックスに「 **Product Category**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="45544-292">In the **Prompt** box, type **Product Category**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="45544-293">このパラメーターは非表示なので、このプロンプトは使用されません。</span><span class="sxs-lookup"><span data-stu-id="45544-293">Because the parameter is hidden, this prompt is never used.</span></span>  
  
5.  <span data-ttu-id="45544-294">必要に応じて、 **[使用できる値]** と **[既定値]** をクリックしてそれぞれのオプションを確認します。</span><span class="sxs-lookup"><span data-stu-id="45544-294">Optionally, click **Available Values** and **Default Values** and review their options.</span></span> <span data-ttu-id="45544-295">これらのタブのオプションは変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="45544-295">Do not change any options on these tabs.</span></span>  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
##  <a name="6-save-the-report-to-a-sharepoint-library"></a><a name="DSave"></a><span data-ttu-id="45544-296">6. レポートを SharePoint ライブラリに保存する</span><span class="sxs-lookup"><span data-stu-id="45544-296">6. Save the Report to a SharePoint Library</span></span>  
 <span data-ttu-id="45544-297">レポートは、SharePoint ライブラリ、レポート サーバー、またはコンピューターに保存することができます。</span><span class="sxs-lookup"><span data-stu-id="45544-297">You can save the report to a SharePoint library, report server, or your computer.</span></span> <span data-ttu-id="45544-298">コンピューターに保存する場合は、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] のいくつかの機能 (レポート パーツ、サブレポートなど) が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="45544-298">If you save the report to your computer, a number of [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] features such as report parts and subreports are not available.</span></span> <span data-ttu-id="45544-299">このチュートリアルでは、SharePoint ライブラリにレポートを保存します。</span><span class="sxs-lookup"><span data-stu-id="45544-299">In this tutorial, you will save the report to a SharePoint library.</span></span>  
  
#### <a name="to-save-the-report"></a><span data-ttu-id="45544-300">レポートを保存するには</span><span class="sxs-lookup"><span data-stu-id="45544-300">To save the report</span></span>  
  
1.  <span data-ttu-id="45544-301">レポート ビルダーのボタンの **[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-301">From the Report Builder button, click **Save**.</span></span> <span data-ttu-id="45544-302">**[レポートとして保存]** ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="45544-302">The **Save As Report** dialog box opens.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="45544-303">レポートを再保存すると、自動的に以前の場所に再保存されます。</span><span class="sxs-lookup"><span data-stu-id="45544-303">If you are resaving a report, it is automatically resaved to its previous location.</span></span> <span data-ttu-id="45544-304">場所を変更するには、 **[名前を付けて保存]** オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="45544-304">To change the location, use the **Save As** option.</span></span>  
  
2.  <span data-ttu-id="45544-305">最近使用したレポート サーバーと SharePoint サイトの一覧を表示するには、 **[最近使ったサイトとサーバー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-305">To show a list of recently used report servers and SharePoint sites, click **Recent Sites and Servers**.</span></span>  
  
3.  <span data-ttu-id="45544-306">レポートを保存する権限がある SharePoint サイトの名前を入力するか選択します。</span><span class="sxs-lookup"><span data-stu-id="45544-306">Select or type the name of the SharePoint site where you have permission to save reports.</span></span>  
  
     <span data-ttu-id="45544-307">SharePoint ライブラリの URL の構文を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="45544-307">The URL of the SharePoint library has the following syntax:</span></span>  
  
    ```  
    Http://<ServerName>/<Sites>/  
    ```  
  
4.  <span data-ttu-id="45544-308">**[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-308">Click **Save**.</span></span>  
  
     <span data-ttu-id="45544-309">**[最近使ったサイトとサーバー]** に、SharePoint サイトのライブラリの一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="45544-309">**Recent Sites and Servers** lists the libraries on the SharePoint site.</span></span>  
  
5.  <span data-ttu-id="45544-310">レポートを保存するライブラリに移動します。</span><span class="sxs-lookup"><span data-stu-id="45544-310">Navigate to the library where you will save the report.</span></span>  
  
6.  <span data-ttu-id="45544-311">**[名前]** ボックスに表示されている既定の名前を「 **ResellerVSOnlineDrillthrough**」に変更します。</span><span class="sxs-lookup"><span data-stu-id="45544-311">In the **Name** box, replace the default name with **ResellerVSOnlineDrillthrough**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="45544-312">メイン レポートも同じ場所に保存します。</span><span class="sxs-lookup"><span data-stu-id="45544-312">You will save the main report to the same location.</span></span> <span data-ttu-id="45544-313">メイン レポートと詳細レポートをそれぞれ異なるサイトまたはライブラリに保存する場合は、メイン レポートの **[レポートに移動する]** アクションのパスを更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="45544-313">If you want to save the main and drillthrough reports to different sites or libraries, you must update the path of the **Go to report** action in the main report.</span></span>  
  
7.  <span data-ttu-id="45544-314">**[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-314">Click **Save**.</span></span>  
  
##  <a name="1-create-a-new-report-from-the-table-or-matrix-wizard"></a><a name="MMatrixAndDataset"></a><span data-ttu-id="45544-315">1. テーブルまたはマトリックスウィザードから新しいレポートを作成する</span><span class="sxs-lookup"><span data-stu-id="45544-315">1. Create a New Report from the Table or Matrix Wizard</span></span>  
 <span data-ttu-id="45544-316">**[作業の開始]** ダイアログ ボックスから、 **テーブルまたはマトリックス ウィザード**を使用してマトリックス レポートを作成します。</span><span class="sxs-lookup"><span data-stu-id="45544-316">From the **Getting Started** dialog box, create a matrix report by using the **Table or Matrix Wizard**.</span></span>  
  
#### <a name="to-create-a-new-report"></a><span data-ttu-id="45544-317">新しいレポートを作成するには</span><span class="sxs-lookup"><span data-stu-id="45544-317">To create a new report</span></span>  
  
1.  <span data-ttu-id="45544-318">[**スタート**] をクリックし、[**プログラム**]、[レポートビルダー] の順にポイントし、[ [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)] **Report Builder\*\*\*\*レポートビルダー**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-318">Click **Start**, point to **Programs**, point to [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)] **Report Builder**, and then click **Report Builder**.</span></span>  
  
2.  <span data-ttu-id="45544-319">**[作業の開始]** ダイアログ ボックスで、 **[新しいレポート]** が選択されていることを確認し、 **[テーブルまたはマトリックス ウィザード]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-319">In the **Getting Started** dialog box, verify that **New Report** is selected, and then click **Table or Matrix Wizard**.</span></span>  
  
##  <a name="1a-specify-a-data-connection"></a><a name="MConnection"></a><span data-ttu-id="45544-320">sr-1.</span><span class="sxs-lookup"><span data-stu-id="45544-320">1a.</span></span> <span data-ttu-id="45544-321">データ接続を指定する</span><span class="sxs-lookup"><span data-stu-id="45544-321">Specify a Data Connection</span></span>  
 <span data-ttu-id="45544-322">メイン レポートに埋め込みデータ ソースを追加します。</span><span class="sxs-lookup"><span data-stu-id="45544-322">You will add an embedded data source to the main report.</span></span>  
  
#### <a name="to-create-an-embedded-data-source"></a><span data-ttu-id="45544-323">埋め込みデータ ソースを作成するには</span><span class="sxs-lookup"><span data-stu-id="45544-323">To create an embedded data source</span></span>  
  
1.  <span data-ttu-id="45544-324">**[データセットの選択]** ページで **[データセットを作成する]** を選択し、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-324">On the **Choose a dataset** page, select **Create a dataset**, and then click **Next**.</span></span>  
  
2.  <span data-ttu-id="45544-325">**[新規作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-325">Click **New**.</span></span>  
  
3.  <span data-ttu-id="45544-326">**[名前]** に、データ ソースの名前として「 **Online and Reseller Sales Main** 」と入力します。</span><span class="sxs-lookup"><span data-stu-id="45544-326">In **Name**, type **Online and Reseller Sales Main** as the name for the data source.</span></span>  
  
4.  <span data-ttu-id="45544-327">**[接続の種類の選択]** で、 **[Microsoft SQL Server Analysis Services]** を選択し、 **[構築]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-327">In **Select a connection type**, select **Microsoft SQL Server Analysis Services**, and then click **Build**.</span></span>  
  
5.  <span data-ttu-id="45544-328">**[データ ソース]** で、データ ソースが **[Microsoft SQL Server Analysis Services (AdomdClient)]** になっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="45544-328">In **Data source**, verify that the data source is **Microsoft SQL Server Analysis Services (AdomdClient)**.</span></span>  
  
6.  <span data-ttu-id="45544-329">[**サーバー名**] に、のインスタンスがインストールされているサーバーの名前を入力し [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="45544-329">In **Server name**, type the name of a server where an instance of [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] is installed.</span></span>  
  
7.  <span data-ttu-id="45544-330">**[データベース名の選択または入力]** で、Contoso キューブを選択します。</span><span class="sxs-lookup"><span data-stu-id="45544-330">In **Select or enter a database name**, select the Contoso cube.</span></span>  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
9. <span data-ttu-id="45544-331">**[接続文字列]** に次の構文が含まれていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="45544-331">Verify that the **Connection string** contains the following syntax:</span></span>  
  
    ```  
    Data Source=<servername>; Initial Catalog = Contoso  
    ```  
  
10. <span data-ttu-id="45544-332">**[資格情報の種類]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-332">Click **Credentials type**.</span></span>  
  
     <span data-ttu-id="45544-333">データ ソースの権限の構成によっては、既定の認証を変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="45544-333">Depending on how permissions are configured on the data source, you might need to change the default authentication.</span></span>  
  
11. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
12. <span data-ttu-id="45544-334">データ ソースに接続できることを確認するために、 **[接続テスト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-334">To verify that you can connect to the data source, click **Test Connection**.</span></span>  
  
13. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
14. <span data-ttu-id="45544-335">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-335">Click **Next**.</span></span>  
  
##  <a name="1b-create-an-mdx-query"></a><a name="MMDXQuery"></a><span data-ttu-id="45544-336">ドル.</span><span class="sxs-lookup"><span data-stu-id="45544-336">1b.</span></span> <span data-ttu-id="45544-337">MDX クエリを作成する</span><span class="sxs-lookup"><span data-stu-id="45544-337">Create an MDX Query</span></span>  
 <span data-ttu-id="45544-338">次に、埋め込みデータセットを作成します。</span><span class="sxs-lookup"><span data-stu-id="45544-338">Next, create an embedded dataset.</span></span> <span data-ttu-id="45544-339">これを行うには、クエリ デザイナーを使用して、フィルター、パラメーター、および計算されるメンバーと、データセット自体を作成します。</span><span class="sxs-lookup"><span data-stu-id="45544-339">To do so, you will use the query designer to create filters, parameters, and calculated members as well as the dataset itself.</span></span>  
  
#### <a name="to-create-query-filters"></a><span data-ttu-id="45544-340">クエリ フィルターを作成するには</span><span class="sxs-lookup"><span data-stu-id="45544-340">To create query filters</span></span>  
  
1.  <span data-ttu-id="45544-341">[**クエリのデザイン**] ページのメタデータペインの [キューブ] セクションで、省略記号ボタン **([..**.]) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-341">On the **Design a query** page, in the Metadata pane, in the cube section, click the ellipsis **(...)**.</span></span>  
  
2.  <span data-ttu-id="45544-342">**[キューブの選択]** ダイアログ ボックスで、Sales をクリックし、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-342">In the **Cube Selection** dialog box, click Sales, and then click **OK**.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="45544-343">MDX クエリを手動で作成しない場合は、![デザイン モードへの切り替え](media/rsqdicon-designmode.gif "デザイン モードに切り替える") アイコンをクリックしてクエリ デザイナーをクエリ モードに切り替え、完成した MDX をクエリ デザイナーに貼り付けます。その後、「[データセットを作成するには](#MSkip)」の手順 5 に進みます。</span><span class="sxs-lookup"><span data-stu-id="45544-343">If you do not want to build the MDX query manually, click the ![Switch to Design mode](media/rsqdicon-designmode.gif "Switch to Design mode") icon, toggle the query designer to Query mode, paste the completed MDX to the query designer, and then proceed to step 5 in [To create the dataset](#MSkip).</span></span>  
  
    ```  
    WITH MEMBER [Measures].[Net QTY] AS [Measures].[Sales Quantity] -[Measures].[Sales Return Quantity] MEMBER [Measures].[Net Sales] AS [Measures].[Sales Amount] - [Measures].[Sales Return Amount] SELECT NON EMPTY { [Measures].[Net QTY], [Measures].[Net Sales] } ON COLUMNS, NON EMPTY { ([Channel].[Channel Name].[Channel Name].ALLMEMBERS * [Product].[Product Category Name].[Product Category Name].ALLMEMBERS ) } DIMENSION PROPERTIES MEMBER_CAPTION, MEMBER_UNIQUE_NAME ON ROWS FROM ( SELECT ( { [Date].[Calendar Year].&[2009] } ) ON COLUMNS FROM ( SELECT ( STRTOSET(@ProductProductCategoryName, CONSTRAINED) ) ON COLUMNS FROM ( SELECT ( { [Sales Territory].[Sales Territory Group].&[North America] } ) ON COLUMNS FROM ( SELECT ( { [Channel].[Channel Name].&[2], [Channel].[Channel Name].&[4] } ) ON COLUMNS FROM [Sales])))) WHERE ( [Sales Territory].[Sales Territory Group].&[North America], [Date].[Calendar Year].&[2009] ) CELL PROPERTIES VALUE, BACK_COLOR, FORE_COLOR, FORMATTED_VALUE, FORMAT_STRING, FONT_NAME, FONT_SIZE, FONT_FLAGSQuery text: Code.  
    ```  
  
3.  <span data-ttu-id="45544-344">メジャー グループ ペインで Channel を展開し、Channel Name をフィルター ペインの **[階層]** 列にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="45544-344">In the Measure Group pane, expand Channel, and then drag Channel Name to the **Hierarchy** column in the filter pane.</span></span>  
  
     <span data-ttu-id="45544-345">Channel というディメンション名が自動的に **[ディメンション]** 列に追加されます。</span><span class="sxs-lookup"><span data-stu-id="45544-345">The dimension name, Channel, is automatically added to the **Dimension** column.</span></span> <span data-ttu-id="45544-346">**[ディメンション]** 列と **[演算子]** 列は変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="45544-346">Do not change the **Dimension** or **Operator** columns.</span></span>  
  
4.  <span data-ttu-id="45544-347">**[フィルター式]** 列の下矢印をクリックして、 **[フィルター式]** の一覧を開きます。</span><span class="sxs-lookup"><span data-stu-id="45544-347">To open the **Filter Expression** list, click the down arrow in the **Filter Expression** column.</span></span>  
  
5.  <span data-ttu-id="45544-348">フィルター式の一覧で、 **[All Channel]** を展開し、 **[Online]** と **[Reseller]** をクリックして、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-348">In the filter expression list, expand **All Channel**, click **Online** and **Reseller**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="45544-349">Channel を Online と Reseller のみに制限するフィルターがクエリに追加されます。</span><span class="sxs-lookup"><span data-stu-id="45544-349">The query now includes a filter to include only these channels: Online and Reseller.</span></span>  
  
6.  <span data-ttu-id="45544-350">販売区域ディメンションを展開し、Sales 区域グループを [**階層**] 列の [ **Channel Name**] の下にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="45544-350">Expand the Sales Territory dimension, and then drag Sales Territory Group to the **Hierarchy** column, below **Channel Name**.</span></span>  
  
7.  <span data-ttu-id="45544-351">**[フィルター式]** の一覧を開き、 **[All Sales Territory]** を展開して **[North America]** をクリックし、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-351">Open the **Filter Expression** list, expand **All Sales Territory**, click **North America**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="45544-352">North America の売上のみを含めるフィルターがクエリに追加されます。</span><span class="sxs-lookup"><span data-stu-id="45544-352">The query now has a filter to include only sales in North America.</span></span>  
  
8.  <span data-ttu-id="45544-353">メジャー グループ ペインで Date を展開し、Calendar Year をフィルター ペインの **[階層]** 列にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="45544-353">In the Measure Group pane, expand Date, and drag Calendar Year to the **Hierarchy** column in the filter pane.</span></span>  
  
     <span data-ttu-id="45544-354">Date というディメンション名が自動的に **[ディメンション]** 列に追加されます。</span><span class="sxs-lookup"><span data-stu-id="45544-354">The dimension name, Date, is automatically added to the **Dimension** column.</span></span> <span data-ttu-id="45544-355">**[ディメンション]** 列と **[演算子]** 列は変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="45544-355">Do not change the **Dimension** or **Operator** columns.</span></span>  
  
9. <span data-ttu-id="45544-356">**[フィルター式]** 列の下矢印をクリックして、 **[フィルター式]** の一覧を開きます。</span><span class="sxs-lookup"><span data-stu-id="45544-356">To open the **Filter Expression** list, click the down arrow in the **Filter Expression** column.</span></span>  
  
10. <span data-ttu-id="45544-357">フィルター式の一覧で、 **[All Date]** を展開し、 **[Year 2009]** をクリックして、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-357">In the filter expression list, expand **All Date**, click **Year 2009**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="45544-358">2009 年のデータのみを含めるフィルターがクエリに追加されます。</span><span class="sxs-lookup"><span data-stu-id="45544-358">The query now includes a filter to include only the calendar year 2009.</span></span>  
  
#### <a name="to-create-the-parameter"></a><span data-ttu-id="45544-359">パラメーターを作成するには</span><span class="sxs-lookup"><span data-stu-id="45544-359">To create the parameter</span></span>  
  
1.  <span data-ttu-id="45544-360">Product ディメンションを展開し、Product Category Name メンバーを **[階層]** 列 ( **Sales Territory Group**の下) にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="45544-360">Expand the Product dimension, and then drag the Product Category Name member to the **Hierarchy** column below **Sales Territory Group**.</span></span>  
  
2.  <span data-ttu-id="45544-361">**[フィルター式]** の一覧を開き、 **[All Products]** をクリックして、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-361">Open the **Filter Expression** list, click **All Products**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="45544-362">**[パラメーター]** チェック ボックスをクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-362">Click the **Parameter** checkbox.</span></span> <span data-ttu-id="45544-363">パラメーター ProductProductCategoryName がクエリに追加されます。</span><span class="sxs-lookup"><span data-stu-id="45544-363">The query now includes the parameter ProductProductCategoryName.</span></span>  
  
#### <a name="to-create-calculated-members"></a><span data-ttu-id="45544-364">計算されるメンバーを作成するには</span><span class="sxs-lookup"><span data-stu-id="45544-364">To create calculated members</span></span>  
  
1.  <span data-ttu-id="45544-365">計算されるメンバー ペインの中にカーソルを置き、右クリックして **[新しい計算されるメンバー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-365">Place the cursor inside the Calculated Members pane, right-click, and then click **New Calculated Member**.</span></span>  
  
2.  <span data-ttu-id="45544-366">メタデータペインで、[**メジャー** ]、[Sales] の順に展開します。</span><span class="sxs-lookup"><span data-stu-id="45544-366">In the Metadata pane, expand **Measures** and then expand Sales.</span></span>  
  
3.  <span data-ttu-id="45544-367">Sales Quantity メジャーを **[式]** ボックスにドラッグし、マイナス記号 (-) を入力します。次に、Sales Return Quantity メジャーを **[式]** ボックスにドラッグして、マイナス記号の後に配置します。</span><span class="sxs-lookup"><span data-stu-id="45544-367">Drag the Sales Quantity measure to the **Expression** box, type the subtraction character (-), and then drag the Sales Return Quantity measure to the **Expression** box; place it after the subtraction character.</span></span>  
  
     <span data-ttu-id="45544-368">式が次のようになります。</span><span class="sxs-lookup"><span data-stu-id="45544-368">The following code shows the expression:</span></span>  
  
    ```  
    [Measures].[Sales Quantity] - [Measures].[Sales Return Quantity]  
    ```  
  
4.  <span data-ttu-id="45544-369">[名前] ボックスに「 **Net QTY**」と入力し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-369">In the Name box, type **Net QTY**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="45544-370">計算されるメンバー ペインに、計算されるメンバー **Net QTY** が表示されます。</span><span class="sxs-lookup"><span data-stu-id="45544-370">The Calculated Members pane lists the **Net QTY** calculated member.</span></span>  
  
5.  <span data-ttu-id="45544-371">**[計算されるメンバー]** を右クリックし、 **[新しい計算されるメンバー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-371">Right-click **Calculated Members**, and then click **New Calculated Member**.</span></span>  
  
6.  <span data-ttu-id="45544-372">メタデータ ペインで、 **[メジャー]**、Sales の順に展開します。</span><span class="sxs-lookup"><span data-stu-id="45544-372">In the Metadata pane, expand **Measures**, and then expand Sales.</span></span>  
  
7.  <span data-ttu-id="45544-373">Sales Amount メジャーを **[式]** ボックスにドラッグし、マイナス記号 (-) を入力します。次に、Sales Return Amount メジャーを **[式]** ボックスにドラッグして、マイナス記号の後に配置します。</span><span class="sxs-lookup"><span data-stu-id="45544-373">Drag the Sales Amount measure to the **Expression** box, type the subtraction character (-), and then drag the Sales Return Amount measure to the **Expression** box; place it after the subtraction character.</span></span>  
  
     <span data-ttu-id="45544-374">式が次のようになります。</span><span class="sxs-lookup"><span data-stu-id="45544-374">The following code shows the expression:</span></span>  
  
    ```  
    [Measures].[Sales Amount] - [Measures].[Sales Return Amount]  
    ```  
  
8.  <span data-ttu-id="45544-375">**[名前]** ボックスに「  **Net Sales**」と入力し、 **[OK]** をクリックします。計算されるメンバー ペインに、計算されるメンバー **Net Sales** が表示されます。</span><span class="sxs-lookup"><span data-stu-id="45544-375">In the **Name** box, type  **Net Sales**, and then click **OK**.The Calculated Members pane lists the **Net Sales** calculated member.</span></span>  
  
###  <a name="to-create-the-dataset"></a><a name="MSkip"></a><span data-ttu-id="45544-376">データセットを作成するには</span><span class="sxs-lookup"><span data-stu-id="45544-376">To create the dataset</span></span>  
  
1.  <span data-ttu-id="45544-377">Channel ディメンションから Channel Name をデータ ペインにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="45544-377">From the Channel dimension, drag Channel Name to the data pane.</span></span>  
  
2.  <span data-ttu-id="45544-378">Product ディメンションから Product Category Name をデータ ペインにドラッグして、Channel Name の右側に配置します。</span><span class="sxs-lookup"><span data-stu-id="45544-378">From the Product dimension, drag Product Category Name to the data pane, and then place it to the right of Channel Name.</span></span>  
  
3.  <span data-ttu-id="45544-379">**[計算されるメンバー]** から `Net QTY` をデータ ペインにドラッグして、Product Category Name の右側に配置します。</span><span class="sxs-lookup"><span data-stu-id="45544-379">From **Calculated Members**, drag `Net QTY` to the data pane, and then place it to the right of Product Category Name.</span></span>  
  
4.  <span data-ttu-id="45544-380">[計算されるメンバー] から Net Sales をデータ ペインにドラッグして、 `Net QTY`の右側に配置します。</span><span class="sxs-lookup"><span data-stu-id="45544-380">From Calculated Members, drag Net Sales to the data pane, and then place it to the right of `Net QTY`.</span></span>  
  
5.  <span data-ttu-id="45544-381">クエリデザイナーのツールバーで、[**実行] (!)** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-381">On the query designer toolbar, click **Run (!)**.</span></span>  
  
     <span data-ttu-id="45544-382">クエリの結果セットを確認します。</span><span class="sxs-lookup"><span data-stu-id="45544-382">Review the query result set.</span></span>  
  
6.  <span data-ttu-id="45544-383">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-383">Click **Next**.</span></span>  
  
##  <a name="1c-organize-data-into-groups"></a><a name="MLayout"></a><span data-ttu-id="45544-384">1c.</span><span class="sxs-lookup"><span data-stu-id="45544-384">1c.</span></span> <span data-ttu-id="45544-385">データをグループにまとめる</span><span class="sxs-lookup"><span data-stu-id="45544-385">Organize Data into Groups</span></span>  
 <span data-ttu-id="45544-386">データをグループ化するフィールドを選択し、詳細データおよび集計データを表示する行と列を含むマトリックスをデザインします。</span><span class="sxs-lookup"><span data-stu-id="45544-386">When you select the fields on which to group data, you design a matrix with rows and columns that displays detail and aggregated data.</span></span>  
  
#### <a name="to-organize-data-into-groups"></a><span data-ttu-id="45544-387">データをグループにまとめるには</span><span class="sxs-lookup"><span data-stu-id="45544-387">To organize data into groups</span></span>  
  
1.  <span data-ttu-id="45544-388">**[フィールドの配置]** ページで、Product_Category_Name を **[行グループ]** にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="45544-388">On the **Arrange fields** page, drag Product_Category_Name to **Row groups**.</span></span>  
  
2.  <span data-ttu-id="45544-389">Channel_Name を **[列グループ]** にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="45544-389">Drag Channel_Name to **Column groups**.</span></span>  
  
3.  <span data-ttu-id="45544-390">`Net_QTY` を **[値]** にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="45544-390">Drag `Net_QTY` to **Values**.</span></span>  
  
     <span data-ttu-id="45544-391">`Net_QTY` は Sum 関数 (数値フィールドの既定の集計関数) を使用して自動的に集計されます。</span><span class="sxs-lookup"><span data-stu-id="45544-391">`Net_QTY` is automatically aggregated by the Sum function, the default aggregate for numeric fields.</span></span> <span data-ttu-id="45544-392">値は `[Sum(Net_QTY)]` です。</span><span class="sxs-lookup"><span data-stu-id="45544-392">The value is `[Sum(Net_QTY)]`.</span></span>  
  
     <span data-ttu-id="45544-393">使用可能なその他の集計関数を表示するには、ドロップダウン リストを開きます。</span><span class="sxs-lookup"><span data-stu-id="45544-393">To view the other aggregate functions available, open the drop-down list.</span></span> <span data-ttu-id="45544-394">集計関数は変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="45544-394">Do not change the aggregate function.</span></span>  
  
4.  <span data-ttu-id="45544-395">`Net_Sales_Return` を **[値]** にドラッグして、 `[Sum(Net_QTY)]`の下に配置します。</span><span class="sxs-lookup"><span data-stu-id="45544-395">Drag `Net_Sales_Return` to **Values** and then place it below `[Sum(Net_QTY)]`.</span></span>  
  
     <span data-ttu-id="45544-396">手順 3. および 4. で、マトリックスに表示するデータが指定されます。</span><span class="sxs-lookup"><span data-stu-id="45544-396">Steps 3 and 4 specify the data to display in the matrix.</span></span>  
  
##  <a name="1d-add-subtotals-and-totals"></a><a name="MTotals"></a><span data-ttu-id="45544-397">引か.</span><span class="sxs-lookup"><span data-stu-id="45544-397">1d.</span></span> <span data-ttu-id="45544-398">小計と合計を追加する</span><span class="sxs-lookup"><span data-stu-id="45544-398">Add Subtotals and Totals</span></span>  
 <span data-ttu-id="45544-399">レポートには小計と総計を表示できます。</span><span class="sxs-lookup"><span data-stu-id="45544-399">You can show subtotals and grand totals in reports.</span></span> <span data-ttu-id="45544-400">メイン レポートのデータはインジケーターとして表示されるため、ウィザードの完了後に総計を削除します。</span><span class="sxs-lookup"><span data-stu-id="45544-400">The data in the main report displays as an indicator; you will remove the grand total after you complete the wizard.</span></span>  
  
#### <a name="to-add-subtotals-and-grand-totals"></a><span data-ttu-id="45544-401">小計と総計を追加するには</span><span class="sxs-lookup"><span data-stu-id="45544-401">To add subtotals and grand totals</span></span>  
  
1.  <span data-ttu-id="45544-402">[**レイアウトの選択**] ページの [**オプション**] で、[**小計と総計を表示**する] が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="45544-402">On the **Choose the layout** page, under **Options**, verify that **Show subtotals and grand totals** is selected.</span></span>  
  
     <span data-ttu-id="45544-403">ウィザードのプレビュー ペインに、4 行を含むマトリックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="45544-403">The wizard Preview pane displays a matrix with four rows.</span></span>  <span data-ttu-id="45544-404">レポートを実行すると、最初の行が列グループになり、2 行目に列見出し、3 行目に製品カテゴリのデータ (`[Sum(Net_ QTY)]` と `[Sum(Net_Sales)]`)、4 行目に合計が含まれます。</span><span class="sxs-lookup"><span data-stu-id="45544-404">When you run the report, each row will display in the following way: The first row is the column group, the second row contains the column headings, the third row contains the product category data (`[Sum(Net_ QTY)]` and `[Sum(Net_Sales)]`, and the fourth row contains the totals.</span></span>  
  
2.  <span data-ttu-id="45544-405">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-405">Click **Next**.</span></span>  
  
##  <a name="1e-choose-a-style"></a><a name="MStyle"></a><span data-ttu-id="45544-406">1e.</span><span class="sxs-lookup"><span data-stu-id="45544-406">1e.</span></span> <span data-ttu-id="45544-407">スタイルを選択する</span><span class="sxs-lookup"><span data-stu-id="45544-407">Choose a Style</span></span>  
 <span data-ttu-id="45544-408">レポートに "スレート" スタイルを適用します。</span><span class="sxs-lookup"><span data-stu-id="45544-408">Apply the Slate style to the report.</span></span> <span data-ttu-id="45544-409">これは、詳細レポートで使用されているのと同じスタイルです。</span><span class="sxs-lookup"><span data-stu-id="45544-409">This is the same style that the drillthrough report uses.</span></span>  
  
#### <a name="to-specify-a-style"></a><span data-ttu-id="45544-410">スタイルを指定するには</span><span class="sxs-lookup"><span data-stu-id="45544-410">To specify a style</span></span>  
  
1.  <span data-ttu-id="45544-411">[**スタイルの選択**] ページのスタイルペインで、[スレート] を選択します。</span><span class="sxs-lookup"><span data-stu-id="45544-411">On the **Choose a Style** page, in the Styles pane, select Slate.</span></span>  
  
2.  <span data-ttu-id="45544-412">**[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-412">Click **Finish**.</span></span>  
  
3.  <span data-ttu-id="45544-413">レポートをプレビューするには、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-413">To preview the report, click **Run**.</span></span>  
  
##  <a name="2-remove-the-grand-total-row"></a><a name="MGrandTotal"></a><span data-ttu-id="45544-414">2. 総計行を削除する</span><span class="sxs-lookup"><span data-stu-id="45544-414">2. Remove the Grand Total Row</span></span>  
 <span data-ttu-id="45544-415">データ値は、列グループの合計も含め、インジケーターの状態として表示されます。</span><span class="sxs-lookup"><span data-stu-id="45544-415">The data values are shown as indictor states, including the column group totals.</span></span> <span data-ttu-id="45544-416">したがって、総計を表示する行を削除します。</span><span class="sxs-lookup"><span data-stu-id="45544-416">Remove the row that displays the grand total.</span></span>  
  
#### <a name="to-remove-the-grand-total-row"></a><span data-ttu-id="45544-417">総計行を削除するには</span><span class="sxs-lookup"><span data-stu-id="45544-417">To remove the grand total row</span></span>  
  
1.  <span data-ttu-id="45544-418">デザイン ビューに切り替えるには、 **[デザイン]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-418">To switch to design view, click **Design**.</span></span>  
  
2.  <span data-ttu-id="45544-419">合計行 (マトリックスの最後の行) をクリックし、右クリックして **[行の削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-419">Click the Total row (the last row in the matrix), right-click, and then click **Delete Rows**.</span></span>  
  
3.  <span data-ttu-id="45544-420">レポートをプレビューするには、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-420">To preview the report, click **Run**.</span></span>  
  
##  <a name="3-configure-text-box-action-for-drillthrough"></a><a name="MDrillthrough"></a><span data-ttu-id="45544-421">3. ドリルスルーのテキストボックスアクションを構成する</span><span class="sxs-lookup"><span data-stu-id="45544-421">3. Configure Text Box Action for Drillthrough</span></span>  
 <span data-ttu-id="45544-422">ドリルスルーを有効にするために、メイン レポートのテキスト ボックスでアクションを指定します。</span><span class="sxs-lookup"><span data-stu-id="45544-422">To enable the drillthrough, specify an action on a text box in the main report.</span></span>  
  
#### <a name="to-enable-an-action"></a><span data-ttu-id="45544-423">アクションを有効にするには</span><span class="sxs-lookup"><span data-stu-id="45544-423">To enable an action</span></span>  
  
1.  <span data-ttu-id="45544-424">デザイン ビューに切り替えるには、 **[デザイン]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-424">To switch to design view, click **Design**.</span></span>  
  
2.  <span data-ttu-id="45544-425">Product_Category_Name が含まれるセルを右クリックし、 **[テキスト ボックスのプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-425">Right-click the cell that contains Product_Category_Name, and then click **Text Box Properties**.</span></span>  
  
3.  <span data-ttu-id="45544-426">[**操作**] タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-426">Click the **Action** tab.</span></span>  
  
4.  <span data-ttu-id="45544-427">[**レポートにジャンプ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="45544-427">Select **Go to report.**</span></span>  
  
5.  <span data-ttu-id="45544-428">**[レポートの指定]** で、 **[参照]** をクリックして、ResellerVSOnlineDrillthrough という名前の詳細レポートを指定します。</span><span class="sxs-lookup"><span data-stu-id="45544-428">In **Specify a report**, click **Browse**, and then locate the drillthrough report named ResellerVSOnlineDrillthrough.</span></span>  
  
6.  <span data-ttu-id="45544-429">詳細レポートを実行するためのパラメーターを追加するには、 **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-429">To add a parameter to run the drillthrough report, click **Add**.</span></span>  
  
7.  <span data-ttu-id="45544-430">**[名前]** ボックスの一覧から ProductProductCategoryName を選択します。</span><span class="sxs-lookup"><span data-stu-id="45544-430">In the **Name** list, select ProductProductCategoryName.</span></span>  
  
8.  <span data-ttu-id="45544-431">**[値]** に「`[Product_Category_Name.UniqueName]`」を入力します。</span><span class="sxs-lookup"><span data-stu-id="45544-431">In **Value**, type `[Product_Category_Name.UniqueName]`.</span></span>  
  
     <span data-ttu-id="45544-432">Product_Category_Name はデータセットのフィールドです。</span><span class="sxs-lookup"><span data-stu-id="45544-432">Product_Category_Name is a field in the dataset.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="45544-433">ドリルスルー アクションには一意の値が必要なため、`UniqueName` プロパティを含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="45544-433">You must include the `UniqueName` property because the drillthrough action requires a unique value.</span></span>  
  
9. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
#### <a name="to-format-the-drillthrough-field"></a><span data-ttu-id="45544-434">ドリルスルー フィールドの書式を設定するには</span><span class="sxs-lookup"><span data-stu-id="45544-434">To format the drillthrough field</span></span>  
  
1.  <span data-ttu-id="45544-435">`Product_Category_Name`が含まれるセルを右クリックし、 **[テキスト ボックスのプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-435">Right-click the cell that contains the `Product_Category_Name`, and then click **Text Box Properties**.</span></span>  
  
2.  <span data-ttu-id="45544-436">**[フォント]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-436">Click the **Font** tab.</span></span>  
  
3.  <span data-ttu-id="45544-437">**[文字飾り]** ボックスの一覧の **[下線]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="45544-437">In the **Effects** list, select **Underline**.</span></span>  
  
4.  <span data-ttu-id="45544-438">**[色]** ボックスの一覧の **[青]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="45544-438">In the **Color** list, select **Blue**.</span></span>  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
6.  <span data-ttu-id="45544-439">レポートをプレビューするには、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-439">To preview your report, click **Run**.</span></span>  
  
 <span data-ttu-id="45544-440">製品カテゴリ名が、一般的なリンクの書式 (下線付きの青い文字) になります。</span><span class="sxs-lookup"><span data-stu-id="45544-440">The product category names are in the common link format (blue and underlined).</span></span>  
  
##  <a name="4-replace-numeric-values-with-indicators"></a><a name="MIndicators"></a><span data-ttu-id="45544-441">4. 数値をインジケーターに置き換える</span><span class="sxs-lookup"><span data-stu-id="45544-441">4. Replace Numeric Values with Indicators</span></span>  
 <span data-ttu-id="45544-442">販売ルート Online および Reseller の数量と売上の状態をインジケーターで表示します。</span><span class="sxs-lookup"><span data-stu-id="45544-442">Use indicators to show the state of quantities and sales for Online and Reseller channels.</span></span>  
  
#### <a name="to-add-an-indicator-for-net-qty-values"></a><span data-ttu-id="45544-443">Net QTY 値のインジケーターを追加するには</span><span class="sxs-lookup"><span data-stu-id="45544-443">To add an indicator for Net QTY values</span></span>  
  
1.  <span data-ttu-id="45544-444">デザイン ビューに切り替えるには、 **[デザイン]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-444">To switch to design view, click **Design**.</span></span>  
  
2.  <span data-ttu-id="45544-445">リボンで **[四角形]** アイコンをクリックし、 `[Sum(Net QTY)]` 列グループの `[Product_Category_Name]` 行グループにある `Channel_Name` セルの中をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-445">On the ribbon, click the **Rectangle** icon, and then click in the `[Sum(Net QTY)]` cell in the `[Product_Category_Name]` row group in the `Channel_Name` column group.</span></span>  
  
3.  <span data-ttu-id="45544-446">リボンで **[インジケーター]** アイコンをクリックし、四角形の中をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-446">On the ribbon, click the **Indicator** icon, and then click inside the rectangle.</span></span> <span data-ttu-id="45544-447">**[インジケーターの種類の選択]** ダイアログ ボックスが表示されます。 **[指向性]** インジケーターが選択されています。</span><span class="sxs-lookup"><span data-stu-id="45544-447">The **Select Indicator Type** dialog box opens with the **Directional** indicator selected.</span></span>  
  
4.  <span data-ttu-id="45544-448">**[3 つの図形]** をクリックし、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-448">Click the **3 Signs** type, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="45544-449">インジケーターを右クリックし、ゲージ データ ペインで、 **[(未指定)]** の横にある下矢印をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-449">Right-click the indicator and in the Gauge Data pane, click the down arrow next to **(Unspecified)**.</span></span> <span data-ttu-id="45544-450">[`Net_QTY`] を選択します。</span><span class="sxs-lookup"><span data-stu-id="45544-450">Select `Net_QTY`.</span></span>  
  
6.  <span data-ttu-id="45544-451">`[Sum(Net QTY)]` [合計] `[Product_Category_Name]` の **行グループにある**セルに対して、手順 2. ～ 5. を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="45544-451">Repeat steps 2 through 5 for the `[Sum(Net QTY)]` cell in the `[Product_Category_Name]` row group within **Total**.</span></span>  
  
#### <a name="to-add-an-indicator-for-net-sales-values"></a><span data-ttu-id="45544-452">Net Sales 値のインジケーターを追加するには</span><span class="sxs-lookup"><span data-stu-id="45544-452">To add an indicator for Net Sales values</span></span>  
  
1.  <span data-ttu-id="45544-453">リボンで **[四角形]** アイコンをクリックし、 `[Sum(Net_Sales)]` 列グループの `[Product_Category_Name]` 行グループにある `Channel_Name` セルの中をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-453">On the ribbon, click the **Rectangle** icon, and then click inside the `[Sum(Net_Sales)]` cell in the `[Product_Category_Name]` row group in the `Channel_Name` column group.</span></span>  
  
2.  <span data-ttu-id="45544-454">リボンで **[インジケーター]** アイコンをクリックし、四角形の中をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-454">On the ribbon, click the **Indicator** icon, and then click inside the rectangle.</span></span>  
  
3.  <span data-ttu-id="45544-455">**[3 つの図形]** をクリックし、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-455">Click the **3 Signs** type, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="45544-456">インジケーターを右クリックし、ゲージ データ ペインで、 **[(未指定)]** の横にある下矢印をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-456">Right-click the indicator and in the Gauge Data pane, click the down arrow next to **(Unspecified)**.</span></span> <span data-ttu-id="45544-457">[`Net_Sales`] を選択します。</span><span class="sxs-lookup"><span data-stu-id="45544-457">Select `Net_Sales`.</span></span>  
  
5.  <span data-ttu-id="45544-458">`[Sum(Net_Sales)]` [合計] `[Product_Category_Name]` の **行グループにある**セルに対して、手順 1. ～ 4. を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="45544-458">Repeat steps 1 through 4 for the `[Sum(Net_Sales)]` cell in the `[Product_Category_Name]` row group within **Total**.</span></span>  
  
6.  <span data-ttu-id="45544-459">レポートをプレビューするには、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-459">To preview your report, click **Run**.</span></span>  
  
##  <a name="5-update-parameter-properties"></a><a name="MParameter"></a><span data-ttu-id="45544-460">5. パラメーターのプロパティを更新する</span><span class="sxs-lookup"><span data-stu-id="45544-460">5. Update Parameter Properties</span></span>  
 <span data-ttu-id="45544-461">既定ではパラメーターが表示されますが、この設定は、このレポートには適していません。</span><span class="sxs-lookup"><span data-stu-id="45544-461">By default, parameters are visible, which is not appropriate for this report.</span></span> <span data-ttu-id="45544-462">パラメーターのプロパティを更新して、パラメーターを内部パラメーターにします。</span><span class="sxs-lookup"><span data-stu-id="45544-462">You will update the parameter properties to make the parameter internal.</span></span>  
  
#### <a name="to-make-the-parameter-internal"></a><span data-ttu-id="45544-463">パラメーターを内部パラメーターにするには</span><span class="sxs-lookup"><span data-stu-id="45544-463">To make the parameter internal</span></span>  
  
1.  <span data-ttu-id="45544-464">レポート データ ペインで **[パラメーター]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="45544-464">In the Report Data pane, expand **Parameters**.</span></span>  
  
2.  <span data-ttu-id="45544-465">レポート データ ペインで `@ProductProductCategoryName,` を右クリックし、 **[パラメーターのプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-465">Right-click `@ProductProductCategoryName,` and then click **Parameter Properties**.</span></span>  
  
3.  <span data-ttu-id="45544-466">**[全般]** タブで **[内部]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-466">On the **General** tab, click **Internal**.</span></span>  
  
4.  <span data-ttu-id="45544-467">必要に応じて、 **[使用できる値]** タブと **[既定値]** タブをクリックしてそれぞれのオプションを確認します。</span><span class="sxs-lookup"><span data-stu-id="45544-467">Optionally, click the **Available Values** and **Default Values** tabs and review their options.</span></span> <span data-ttu-id="45544-468">これらのタブのオプションは変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="45544-468">Do not change any options on these tabs.</span></span>  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
##  <a name="6-add-a-report-title"></a><a name="MTitle"></a><span data-ttu-id="45544-469">6. レポートタイトルを追加する</span><span class="sxs-lookup"><span data-stu-id="45544-469">6. Add a Report Title</span></span>  
 <span data-ttu-id="45544-470">メイン レポートにタイトルを追加します。</span><span class="sxs-lookup"><span data-stu-id="45544-470">Add a title to the main report.</span></span>  
  
#### <a name="to-add-a-report-title"></a><span data-ttu-id="45544-471">レポート タイトルを追加するには</span><span class="sxs-lookup"><span data-stu-id="45544-471">To add a report title</span></span>  
  
1.  <span data-ttu-id="45544-472">デザイン画面で、 **[クリックしてタイトルを追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-472">On the design surface, click **Click to add title**.</span></span>  
  
2.  <span data-ttu-id="45544-473">「 **2009 Product Category Sales: Online and Reseller Category:**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="45544-473">Type **2009 Product Category Sales: Online and Reseller Category:**.</span></span>  
  
3.  <span data-ttu-id="45544-474">入力したテキストを選択します。</span><span class="sxs-lookup"><span data-stu-id="45544-474">Select the text you typed.</span></span>  
  
4.  <span data-ttu-id="45544-475">リボンの **[ホーム]** タブの [フォント] グループで、フォントとして **[Times New Roman]** 、サイズとして **[16pt]** 、スタイルとして **[太字]** と **[斜体]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="45544-475">On the **Home** tab of the ribbon, in the Font group, select the **Times New Roman** font, **16pt** size, and the **Bold** and **Italic** styles.</span></span>  
  
5.  <span data-ttu-id="45544-476">レポートをプレビューするには、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-476">To preview your report, click **Run**.</span></span>  
  
##  <a name="7-save-the-main-report-to-a-sharepoint-library"></a><a name="MSave"></a><span data-ttu-id="45544-477">7. メインレポートを SharePoint ライブラリに保存する</span><span class="sxs-lookup"><span data-stu-id="45544-477">7. Save the Main Report to a SharePoint Library</span></span>  
 <span data-ttu-id="45544-478">メイン レポートを SharePoint ライブラリに保存します。</span><span class="sxs-lookup"><span data-stu-id="45544-478">Save the main report to a SharePoint library.</span></span>  
  
#### <a name="to-save-the-report"></a><span data-ttu-id="45544-479">レポートを保存するには</span><span class="sxs-lookup"><span data-stu-id="45544-479">To save the report</span></span>  
  
1.  <span data-ttu-id="45544-480">デザイン ビューに切り替えるには、 **[デザイン]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-480">To switch to design view, click **Design**.</span></span>  
  
2.  <span data-ttu-id="45544-481">レポート ビルダーのボタンの **[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-481">From the Report Builder button, click **Save**.</span></span>  
  
3.  <span data-ttu-id="45544-482">オプションで、最近使用したレポート サーバーと SharePoint サイトの一覧を表示するには、 **[最近使ったサイトとサーバー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-482">Optionally, to show a list of recently used report servers and SharePoint sites, click **Recent Sites and Servers**.</span></span>  
  
4.  <span data-ttu-id="45544-483">レポートを保存する権限がある SharePoint サイトの名前を入力するか選択します。</span><span class="sxs-lookup"><span data-stu-id="45544-483">Select or type the name of the SharePoint site where you have permission to save reports.</span></span> <span data-ttu-id="45544-484">SharePoint ライブラリの URL の構文を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="45544-484">The URL of the SharePoint library has the following syntax:</span></span>  
  
    ```  
    Http://<ServerName>/<Sites>/  
    ```  
  
5.  <span data-ttu-id="45544-485">レポートを保存するライブラリに移動します。</span><span class="sxs-lookup"><span data-stu-id="45544-485">Navigate to the library where you want to save the report.</span></span>  
  
6.  <span data-ttu-id="45544-486">**[名前]** に表示されている既定の名前を「 **ResellerVSOnlineMain**」に変更します。</span><span class="sxs-lookup"><span data-stu-id="45544-486">In **Name**, replace the default name with **ResellerVSOnlineMain**.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="45544-487">メイン レポートは、詳細レポートを保存した場所と同じ場所に保存します。</span><span class="sxs-lookup"><span data-stu-id="45544-487">Save the main report to the same location where you saved the drillthrough report.</span></span> <span data-ttu-id="45544-488">メイン レポートと詳細レポートをそれぞれ異なるサイトまたはライブラリに保存する場合は、メイン レポートの **[レポートに移動する]** アクションで指定されている詳細レポートの場所が正しいことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="45544-488">To save the main and drillthrough reports to different sites or libraries, confirm that the **Go to report** action in the main report, points to the correct location of the drillthrough report.</span></span>  
  
7.  <span data-ttu-id="45544-489">**[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-489">Click **Save**.</span></span>  
  
##  <a name="8-run-the-main-and-drillthrough-reports"></a><a name="MRunReports"></a><span data-ttu-id="45544-490">8. メインレポートと詳細レポートを実行する</span><span class="sxs-lookup"><span data-stu-id="45544-490">8. Run the Main and Drillthrough Reports</span></span>  
 <span data-ttu-id="45544-491">メイン レポートを実行し、製品カテゴリの列の値をクリックして詳細レポートを実行します。</span><span class="sxs-lookup"><span data-stu-id="45544-491">Run the main report, and then click values in the product category column to run the drillthrough report.</span></span>  
  
#### <a name="to-run-the-reports"></a><span data-ttu-id="45544-492">レポートを実行するには</span><span class="sxs-lookup"><span data-stu-id="45544-492">To run the reports</span></span>  
  
1.  <span data-ttu-id="45544-493">レポートを保存した SharePoint ライブラリを開きます。</span><span class="sxs-lookup"><span data-stu-id="45544-493">Open the SharePoint library where the reports are saved.</span></span>  
  
2.  <span data-ttu-id="45544-494">ResellerVSOnlineMain をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-494">Double-click ResellerVSOnlineMain.</span></span>  
  
     <span data-ttu-id="45544-495">レポートが実行されて、製品カテゴリの売上情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="45544-495">The report runs and displays product category sales information.</span></span>  
  
3.  <span data-ttu-id="45544-496">製品カテゴリ名が含まれている列の **[Games and Toys]** リンクをクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-496">Click the **Games and Toys** link in the column that contains product category names.</span></span>  
  
     <span data-ttu-id="45544-497">詳細レポートが実行されて、Games and Toys 製品カテゴリの値のみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="45544-497">The drillthrough report runs, displaying only the values for the Games and Toys product category.</span></span>  
  
4.  <span data-ttu-id="45544-498">メイン レポートに戻るには、Internet Explorer の [戻る] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="45544-498">To return to the main report, click the Internet Explorer back button.</span></span>  
  
5.  <span data-ttu-id="45544-499">必要に応じて、他の製品カテゴリの名前をクリックして動作を確認します。</span><span class="sxs-lookup"><span data-stu-id="45544-499">Optionally, explore other product categories by clicking their names.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45544-500">参照</span><span class="sxs-lookup"><span data-stu-id="45544-500">See Also</span></span>  
 [<span data-ttu-id="45544-501">チュートリアル &#40;レポートビルダー&#41;</span><span class="sxs-lookup"><span data-stu-id="45544-501">Tutorials &#40;Report Builder&#41;</span></span>](report-builder-tutorials.md)  
  
  
