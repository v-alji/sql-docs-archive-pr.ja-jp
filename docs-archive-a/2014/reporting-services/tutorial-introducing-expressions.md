---
title: 'チュートリアル: 式の概要 | Microsoft Docs'
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 2d05ef4c-5f91-48b2-8795-f0a201a0b3cc
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 62a815800dba0730052eb812124d4561d031d0e3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737795"
---
# <a name="tutorial-introducing-expressions"></a><span data-ttu-id="a9aca-102">チュートリアル: 式の概要</span><span class="sxs-lookup"><span data-stu-id="a9aca-102">Tutorial: Introducing Expressions</span></span>
  <span data-ttu-id="a9aca-103">式を使用すると、強力で柔軟なレポートを作成できます。</span><span class="sxs-lookup"><span data-stu-id="a9aca-103">Expressions help you create powerful and flexible reports.</span></span> <span data-ttu-id="a9aca-104">このチュートリアルでは、一般的な関数および演算子を使用した式を作成および実装する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="a9aca-104">This tutorial teaches you to create and implement expressions that use common functions and operators.</span></span> <span data-ttu-id="a9aca-105">[**式**] ダイアログボックスを使用すると、名前の値を連結する式を作成したり、別のデータセットの値を参照したり、フィールドの値に基づいてさまざまな画像を表示したりできます。</span><span class="sxs-lookup"><span data-stu-id="a9aca-105">You will use the **Expression** dialog box to write expressions that concatenate name values, look up values in a separate dataset, display different pictures based on field values, and so on.</span></span>  
  
 <span data-ttu-id="a9aca-106">レポートは縞状で、各行には白と白でない色が交互に使用されます。</span><span class="sxs-lookup"><span data-stu-id="a9aca-106">The report is a barred report with alternating row colors in white and a color.</span></span> <span data-ttu-id="a9aca-107">レポートには、白以外の行の色を選択するためのパラメーターが含まれています。</span><span class="sxs-lookup"><span data-stu-id="a9aca-107">The report includes a parameter for selecting the color of the non-white rows.</span></span>  
  
 <span data-ttu-id="a9aca-108">次の図に、ここで作成するレポートと同様のレポートを示します。</span><span class="sxs-lookup"><span data-stu-id="a9aca-108">The following illustration shows a report similar to the one you will create.</span></span>  
  
 <span data-ttu-id="a9aca-109">![rs_ExpressionsTutorial](../../2014/tutorials/media/rs-expressionstutorial.gif "rs_ExpressionsTutorial")</span><span class="sxs-lookup"><span data-stu-id="a9aca-109">![rs_ExpressionsTutorial](../../2014/tutorials/media/rs-expressionstutorial.gif "rs_ExpressionsTutorial")</span></span>  
  
##  <a name="what-you-will-learn"></a><a name="BackToTop"></a><span data-ttu-id="a9aca-110">学習内容</span><span class="sxs-lookup"><span data-stu-id="a9aca-110">What You Will Learn</span></span>  
 <span data-ttu-id="a9aca-111">このチュートリアルでは、次の方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="a9aca-111">In this tutorial you will learn how to do the following:</span></span>  
  
1.  [<span data-ttu-id="a9aca-112">テーブルまたはマトリックス ウィザードを使用して表レポートとデータセットを作成する</span><span class="sxs-lookup"><span data-stu-id="a9aca-112">Create a Table Report and Dataset from the Table or Matrix Wizard</span></span>](#Setup)  
  
2.  [<span data-ttu-id="a9aca-113">データ ソースおよびデータセットの既定名を更新する</span><span class="sxs-lookup"><span data-stu-id="a9aca-113">Update Default Names of the Data Source and Dataset</span></span>](#UpdateNames)  
  
3.  [<span data-ttu-id="a9aca-114">姓、名、およびイニシャルを表示する</span><span class="sxs-lookup"><span data-stu-id="a9aca-114">Display First Name, Initial, and Last Name</span></span>](#Concatenate)  
  
4.  [<span data-ttu-id="a9aca-115">画像を使用して性別を表示する</span><span class="sxs-lookup"><span data-stu-id="a9aca-115">Use Images to Display Gender</span></span>](#Gender)  
  
5.  [<span data-ttu-id="a9aca-116">CountryRegion 名を参照する</span><span class="sxs-lookup"><span data-stu-id="a9aca-116">Look Up CountryRegion Name</span></span>](#Lookup)  
  
6.  [<span data-ttu-id="a9aca-117">前回の購入日からの日数をカウントする</span><span class="sxs-lookup"><span data-stu-id="a9aca-117">Count Days Since Last Purchase</span></span>](#Count)  
  
7.  [<span data-ttu-id="a9aca-118">インジケーターを使用して売上比較を示す</span><span class="sxs-lookup"><span data-stu-id="a9aca-118">Use an Indicator to Show Sales Comparison</span></span>](#Indicator)  
  
8.  [<span data-ttu-id="a9aca-119">レポートに "緑色のバー" レポートを作成する</span><span class="sxs-lookup"><span data-stu-id="a9aca-119">Make the Report a "Green Bar" Report</span></span>](#GreenBar)  
  
### <a name="other-optional-steps"></a><span data-ttu-id="a9aca-120">その他のオプションの手順</span><span class="sxs-lookup"><span data-stu-id="a9aca-120">Other Optional Steps</span></span>  
  
-   [<span data-ttu-id="a9aca-121">日付列の書式を設定する</span><span class="sxs-lookup"><span data-stu-id="a9aca-121">Format Date Column</span></span>](#DateFormat)  
  
-   [<span data-ttu-id="a9aca-122">レポートタイトルを追加する</span><span class="sxs-lookup"><span data-stu-id="a9aca-122">Add a Report Title</span></span>](#Title)  
  
-   [<span data-ttu-id="a9aca-123">レポートを保存する</span><span class="sxs-lookup"><span data-stu-id="a9aca-123">Save the Report</span></span>](#Save)  
  
 <span data-ttu-id="a9aca-124">このチュートリアルの推定所要時間: 30 分。</span><span class="sxs-lookup"><span data-stu-id="a9aca-124">Estimated time to complete this tutorial: 30 minutes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9aca-125">必要条件</span><span class="sxs-lookup"><span data-stu-id="a9aca-125">Requirements</span></span>  
 <span data-ttu-id="a9aca-126">要件の詳細については、[「チュートリアルの前提条件 (レポート ビルダー)」](../reporting-services/report-builder-tutorials.md) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a9aca-126">For information about requirements, see [Prerequisites for Tutorials &#40;Report Builder&#41;](../reporting-services/report-builder-tutorials.md).</span></span>  
  
##  <a name="1-create-a-table-report-and-dataset-from-the-table-or-matrix-wizard"></a><a name="Setup"></a><span data-ttu-id="a9aca-127">1. テーブルまたはマトリックスウィザードからテーブルレポートとデータセットを作成する</span><span class="sxs-lookup"><span data-stu-id="a9aca-127">1. Create a Table Report and Dataset from the Table or Matrix Wizard</span></span>  
 <span data-ttu-id="a9aca-128">表レポート、データ ソース、およびデータセットを作成します。</span><span class="sxs-lookup"><span data-stu-id="a9aca-128">Create a table report, a data source, and a dataset.</span></span> <span data-ttu-id="a9aca-129">テーブルのレイアウト時には、少数のフィールドのみを含めておきます。</span><span class="sxs-lookup"><span data-stu-id="a9aca-129">When you lay out the table, you will include only a few fields.</span></span> <span data-ttu-id="a9aca-130">ウィザードの完了後に、列を手動で追加します。</span><span class="sxs-lookup"><span data-stu-id="a9aca-130">After you complete the wizard you will manually add columns.</span></span> <span data-ttu-id="a9aca-131">ウィザードを使用すると、容易にテーブルをレイアウトし、スタイルを適用できます。</span><span class="sxs-lookup"><span data-stu-id="a9aca-131">The wizard makes it easy for you to lay out the table and apply a style.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a9aca-132">このチュートリアルのクエリにはデータ値が含まれているため、外部のデータ ソースを必要としません。</span><span class="sxs-lookup"><span data-stu-id="a9aca-132">In this tutorial, the query contains the data values, so that it does not need an external data source.</span></span> <span data-ttu-id="a9aca-133">このため、クエリが非常に長くなっています。</span><span class="sxs-lookup"><span data-stu-id="a9aca-133">This makes the query quite long.</span></span> <span data-ttu-id="a9aca-134">ビジネス環境でクエリにデータを含めることはありません。</span><span class="sxs-lookup"><span data-stu-id="a9aca-134">In a business environment, a query would not contain the data.</span></span> <span data-ttu-id="a9aca-135">これは、学習に使用することのみを目的としています。</span><span class="sxs-lookup"><span data-stu-id="a9aca-135">This is for learning purposes only.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a9aca-136">このチュートリアルでは、ウィザードに関する複数の手順を 1 つにまとめて示します。</span><span class="sxs-lookup"><span data-stu-id="a9aca-136">In this tutorial, the steps for the wizard are consolidated into one procedure.</span></span> <span data-ttu-id="a9aca-137">レポート サーバーの参照、データ ソースの選択、データセットの作成に関する詳細な手順については、このシリーズの最初のチュートリアル (「[チュートリアル: 基本的な表レポートの作成 &#40;レポート ビルダー&#41;](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md)」) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a9aca-137">For step-by-step instructions about how to browse to a report server, choose a data source, and create a dataset, see the first tutorial in this series: [Tutorial: Creating a Basic Table Report &#40;Report Builder&#41;](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md).</span></span>  
  
#### <a name="to-create-a-new-table-report"></a><span data-ttu-id="a9aca-138">新しい表レポートを作成するには</span><span class="sxs-lookup"><span data-stu-id="a9aca-138">To create a new table report</span></span>  
  
1.  <span data-ttu-id="a9aca-139">[**スタート**] をクリックし、[**プログラム**]、[レポートビルダー] の順にポイントし、[ [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)] **Report Builder\*\*\*\*レポートビルダー**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-139">Click **Start**, point to **Programs**, click [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)]**Report Builder**, and then click **Report Builder**.</span></span>  
  
     <span data-ttu-id="a9aca-140">[**はじめに**] ダイアログボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a9aca-140">The **Getting Started** dialog box appears.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a9aca-141">[**はじめに**] ダイアログボックスが表示されない場合は、[**レポートビルダー** ] ボタンの [**新規作成**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-141">If the **Getting Started** dialog box does not appear, from the **Report Builder** button, click **New**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a9aca-142">ClickOnce バージョンのレポートビルダーを使用する場合は、レポートマネージャーを開き、[**レポートビルダー**] をクリックするか、Reporting Services コンテンツの種類 (レポートなど) が有効になっている SharePoint サイトにアクセスして、共有ドキュメントライブラリの [**ドキュメント**] タブにある [**新しいドキュメント**] メニューの [**レポートのレポートビルダー** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-142">If you prefer using the ClickOnce version of Report Builder, open Report Manager and click **Report Builder**, or go to a SharePoint site on which Reporting Services content types such as reports are enabled and click **Report Builder Report** on the **New Document** menu on the **Documents** tab of a shared documents library.</span></span>  
  
2.  <span data-ttu-id="a9aca-143">左ペインで、 **[新しいレポート]** が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="a9aca-143">In the left pane, verify that **New Report** is selected.</span></span>  
  
3.  <span data-ttu-id="a9aca-144">右ペインで、 **[テーブルまたはマトリックス ウィザード]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-144">In the right pane, click **Table or Matrix Wizard**.</span></span>  
  
4.  <span data-ttu-id="a9aca-145">**[データセットの選択]** ページで、 **[データセットを作成する]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-145">On the **Choose a dataset** page, click **Create a dataset**.</span></span>  
  
5.  <span data-ttu-id="a9aca-146">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-146">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="a9aca-147">**[データ ソースへの接続の選択]** ページで、種類が **[SQL Server]** のデータ ソースを選択します。</span><span class="sxs-lookup"><span data-stu-id="a9aca-147">On the **Choose a connection to a data source** page, select a data source that is type **SQL Server**.</span></span> <span data-ttu-id="a9aca-148">一覧からデータ ソースを選択するか、レポート サーバーを参照してデータ ソースを選択します。</span><span class="sxs-lookup"><span data-stu-id="a9aca-148">Select a data source from the list or browse to the report server to select one.</span></span>  
  
7.  <span data-ttu-id="a9aca-149">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-149">Click **Next**.</span></span>  
  
8.  <span data-ttu-id="a9aca-150">**[クエリのデザイン]** ページで、 **[テキストとして編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-150">On the **Design a query** page, click **Edit as Text**.</span></span>  
  
9. <span data-ttu-id="a9aca-151">次のクエリをクエリ ペインに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="a9aca-151">Paste the following query into the query pane:</span></span>  
  
    ```  
    SELECT 'Lauren' AS FirstName,'Johnson' AS LastName, 'American Samoa' AS StateProvince, 1 AS CountryRegionID,'Unknown' AS Gender, CAST(9996.60 AS money) AS YTDPurchase, CAST('2010-6-10' AS date) AS LastPurchase  
    UNION SELECT'Warren' AS FirstName, 'Pal' AS LastName, 'New South Wales' AS StateProvince, 2 AS CountryRegionID, 'Male' AS Gender, CAST(5747.25 AS money) AS YTDPurchase, CAST('2010-7-3' AS date) AS LastPurchase  
    UNION SELECT 'Fernando' AS FirstName, 'Ross' AS LastName, 'Alberta' AS StateProvince, 3 AS CountryRegionID, 'Male' AS Gender, CAST(9248.15 AS money) AS YTDPurchase, CAST('2010-10-17' AS date) AS LastPurchase  
    UNION SELECT 'Rob' AS FirstName, 'Caron' AS LastName, 'Northwest Territories' AS StateProvince, 3 AS CountryRegionID, 'Male' AS Gender, CAST(742.50 AS money) AS YTDPurchase, CAST('2010-4-29' AS date) AS LastPurchase  
    UNION SELECT 'James' AS FirstName, 'Bailey' AS LastName, 'British Columbia' AS StateProvince, 3 AS CountryRegionID, 'Male' AS Gender, CAST(1147.50 AS money) AS YTDPurchase, CAST('2010-6-15' AS date) AS LastPurchase  
    UNION SELECT  'Bridget' AS FirstName, 'She' AS LastName, 'Hamburg' AS StateProvince, 4 AS CountryRegionID, 'Female' AS Gender, CAST(7497.30 AS money) AS YTDPurchase, CAST('2010-5-10' AS date) AS LastPurchase  
    UNION SELECT 'Alexander' AS FirstName, 'Martin' AS LastName, 'Saxony' AS StateProvince, 4 AS CountryRegionID, 'Male' AS Gender, CAST(2997.60 AS money) AS YTDPurchase, CAST('2010-11-19' AS date) AS LastPurchase  
    UNION SELECT 'Yolanda' AS FirstName, 'Sharma' AS LastName ,'Micronesia' AS StateProvince, 5 AS CountryRegionID, 'Female' AS Gender, CAST(3247.95 AS money) AS YTDPurchase, CAST('2010-8-23' AS date) AS LastPurchase  
    UNION SELECT 'Marc' AS FirstName, 'Zimmerman' AS LastName, 'Moselle' AS StateProvince, 6 AS CountryRegionID, 'Male' AS Gender, CAST(1200.00 AS money) AS YTDPurchase, CAST('2010-11-16' AS date) AS LastPurchase  
    UNION SELECT 'Katherine' AS FirstName, 'Abel' AS LastName, 'Moselle' AS StateProvince, 6 AS CountryRegionID, 'Female' AS Gender, CAST(2025.00 AS money) AS YTDPurchase, CAST('2010-12-1' AS date) AS LastPurchase  
    UNION SELECT 'Nicolas' as FirstName, 'Anand' AS LastName, 'Seine (Paris)' AS StateProvince, 6 AS CountryRegionID, 'Male' AS Gender, CAST(1425.00 AS money) AS YTDPurchase, CAST('2010-12-11' AS date) AS LastPurchase  
    UNION SELECT 'James' AS FirstName, 'Peters' AS LastName, 'England' AS StateProvince, 12 AS CountryRegionID, 'Male' AS Gender, CAST(887.50 AS money) AS YTDPurchase, CAST('2010-8-15' AS date) AS LastPurchase  
    UNION SELECT 'Alison' AS FirstName, 'Nath' AS LastName, 'Alaska' AS StateProvince, 7 AS CountryRegionID, 'Female' AS Gender, CAST(607.50 AS money) AS YTDPurchase, CAST('2010-10-13' AS date) AS LastPurchase  
    UNION SELECT 'Grace' AS FirstName, 'Patterson' AS LastName, 'Kansas' AS StateProvince, 7 AS CountryRegionID, 'Female' AS Gender, CAST(1215.00 AS money) AS YTDPurchase, CAST('2010-10-18' AS date) AS LastPurchase  
    UNION SELECT 'Bobby' AS FirstName, 'Sanchez' AS LastName, 'North Dakota' AS StateProvince, 7 AS CountryRegionID, 'Female' AS Gender, CAST(6191.00 AS money) AS YTDPurchase, CAST('2010-9-17' AS date) AS LastPurchase  
    UNION SELECT 'Charles' AS FirstName, 'Reed' AS LastName, 'Nebraska' AS StateProvince, 7 AS CountryRegionID, 'Male' AS Gender, CAST(8772.00 AS money) AS YTDPurchase, CAST('2010-8-27' AS date) AS LastPurchase  
    UNION SELECT 'Orlando' AS FirstName, 'Romeo' AS LastName, 'Texas' AS StateProvince, 7 AS CountryRegionID, 'Male' AS Gender, CAST(8578.00 AS money) AS YTDPurchase, CAST('2010-7-29' AS date) AS LastPurchase  
    UNION SELECT 'Cynthia' AS FirstName, 'Randall' AS LastName, 'Utah' AS StateProvince, 7 AS CountryRegionID, 'Female' AS Gender, CAST(7218.10 AS money) AS YTDPurchase, CAST('2010-1-11' AS date) AS LastPurchase  
    UNION SELECT 'Rebecca' AS FirstName, 'Roberts' AS LastName, 'Washington' AS StateProvince, 7 AS CountryRegionID, 'Female' AS Gender, CAST(8357.80 AS money) AS YTDPurchase, CAST('2010-10-28' AS date) AS LastPurchase  
    UNION SELECT 'Cristian' AS FirstName, 'Petulescu' AS LastName, 'Wisconsin' AS StateProvince, 7 AS CountryRegionID, 'Male' AS Gender, CAST(3470.00 AS money) AS YTDPurchase, CAST('2010-11-30' AS date) AS LastPurchase  
    UNION SELECT 'Cynthia' AS FirstName, 'Randall' AS LastName, 'Utah' AS StateProvince, 7 AS CountryRegionID, 'Female' AS Gender, CAST(7218.10 AS money) AS YTDPurchase, CAST('2010-1-11' AS date) AS LastPurchase  
    UNION SELECT 'Rebecca' AS FirstName, 'Roberts' AS LastName, 'Washington' AS StateProvince, 7 AS CountryRegionID, 'Female' AS Gender, CAST(8357.80 AS money) AS YTDPurchase, CAST('2010-10-28' AS date) AS LastPurchase  
    UNION SELECT 'Cristian' AS FirstName, 'Petulescu' AS LastName, 'Wisconsin' AS StateProvince, 7 AS CountryRegionID, 'Male' AS Gender, CAST(3470.00 AS money) AS YTDPurchase, CAST('2010-11-30' AS date) AS LastPurchase  
    ```  
  
     <span data-ttu-id="a9aca-152">クエリには、生年月日、名前、姓、州または郡、国または地域の識別子、性別、年度累計購入額などを示す列の名前が指定されています。</span><span class="sxs-lookup"><span data-stu-id="a9aca-152">The query specifies column names that include a birth date, first name, last name, state or province, country/region identifier, gender, and year-to-date purchases.</span></span>  
  
10. <span data-ttu-id="a9aca-153">クエリデザイナーのツールバーで、[**実行**] (**!**) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-153">On the query designer toolbar, click **Run** (**!**).</span></span> <span data-ttu-id="a9aca-154">結果セットには FirstName、LastName、StateProvince、CountryRegionID、Gender、YTDPurchase、および LastPurchase の各列が含まれ、20 行のデータが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a9aca-154">The result set displays 20 rows of data and includes the following columns: FirstName, LastName, StateProvince, CountryRegionID, Gender, YTDPurchase, and LastPurchase.</span></span>  
  
11. <span data-ttu-id="a9aca-155">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-155">Click **Next**.</span></span>  
  
12. <span data-ttu-id="a9aca-156">**[フィールドの配置]** ページで、 **[使用できるフィールド]** ボックスから **[値]** ボックスに、次に示すフィールドを指定順にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-156">On the **Arrange fields** page, drag the following fields, in the specified order, from the **Available Fields** list to the **Values** list.</span></span>  
  
    -   <span data-ttu-id="a9aca-157">StateProvince</span><span class="sxs-lookup"><span data-stu-id="a9aca-157">StateProvince</span></span>  
  
    -   <span data-ttu-id="a9aca-158">CountryRegionID</span><span class="sxs-lookup"><span data-stu-id="a9aca-158">CountryRegionID</span></span>  
  
    -   <span data-ttu-id="a9aca-159">LastPurchase</span><span class="sxs-lookup"><span data-stu-id="a9aca-159">LastPurchase</span></span>  
  
    -   <span data-ttu-id="a9aca-160">YTDPurchase</span><span class="sxs-lookup"><span data-stu-id="a9aca-160">YTDPurchase</span></span>  
  
     <span data-ttu-id="a9aca-161">CountryRegionID および YTDPurchase には数値データが格納されているため、これらには既定で SUM 集計が適用されます。</span><span class="sxs-lookup"><span data-stu-id="a9aca-161">Because the CountryRegionID and YTDPurchase contain numeric data, the SUM aggregate is applied to them by default.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a9aca-162">この時点で FirstName フィールドと LastName フィールドは含まれていません。</span><span class="sxs-lookup"><span data-stu-id="a9aca-162">The FirstName and LastName fields are not included.</span></span> <span data-ttu-id="a9aca-163">これらは後の手順で追加します。</span><span class="sxs-lookup"><span data-stu-id="a9aca-163">You will add them in a later step.</span></span>  
  
13. <span data-ttu-id="a9aca-164">[**値**] ボックスの一覧で、を右クリック `CountryRegionID` し、[**合計**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-164">In the **Values** list, right-click `CountryRegionID` and click the **Sum** option.</span></span>  
  
     <span data-ttu-id="a9aca-165">これでもう CountryRegionID には合計が適用されていません。</span><span class="sxs-lookup"><span data-stu-id="a9aca-165">Sum is no longer applied to CountryRegionID.</span></span>  
  
14. <span data-ttu-id="a9aca-166">**[値]** ボックスの一覧の **[YTDPurchase]** を右クリックし、 **[合計]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-166">In the **Values** list, right-click **YTDPurchase** and click the **Sum** option.</span></span>  
  
     <span data-ttu-id="a9aca-167">これでもう YTDPurchase には合計が適用されていません。</span><span class="sxs-lookup"><span data-stu-id="a9aca-167">Sum is no longer applied to YTDPurchase.</span></span>  
  
15. <span data-ttu-id="a9aca-168">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-168">Click **Next**.</span></span>  
  
16. <span data-ttu-id="a9aca-169">**[レイアウトの選択]** ページで、**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-169">On the **Choose the layout** page, click **Next**.</span></span>  
  
17. <span data-ttu-id="a9aca-170">[**スタイルの選択**] ページで [**スレート**] をクリックし、[**完了**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-170">On the **Choose a style** page, click **Slate**, and then click **Finish**.</span></span>  
  
##  <a name="2-update-default-names-of-the-data-source-and-dataset"></a><a name="UpdateNames"></a><span data-ttu-id="a9aca-171">2. データソースおよびデータセットの既定の名前を更新する</span><span class="sxs-lookup"><span data-stu-id="a9aca-171">2. Update Default Names of the Data Source and Dataset</span></span>  
  
#### <a name="to-update-the-default-name-of-the-data-source"></a><span data-ttu-id="a9aca-172">データ ソースの既定名を更新するには</span><span class="sxs-lookup"><span data-stu-id="a9aca-172">To update the default name of the data source</span></span>  
  
1.  <span data-ttu-id="a9aca-173">レポート データ ペインで **[データ ソース]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="a9aca-173">In the Report Data pane, expand **Data Sources**.</span></span>  
  
2.  <span data-ttu-id="a9aca-174">**[DataSource1]** を右クリックし、 **[データ ソースのプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-174">Right-click **DataSource1** and click **Data Source Properties.**</span></span>  
  
3.  <span data-ttu-id="a9aca-175">**[名前]** ボックスに「 **ExpressionsDataSource**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="a9aca-175">In the **Name** box, type **ExpressionsDataSource**</span></span>  
  
4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
#### <a name="to-update-the-default-name-of-the-dataset"></a><span data-ttu-id="a9aca-176">データセットの既定名を更新するには</span><span class="sxs-lookup"><span data-stu-id="a9aca-176">To update the default name of the dataset</span></span>  
  
1.  <span data-ttu-id="a9aca-177">レポート データ ペインで **[データセット]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="a9aca-177">In the Report Data pane, expand **Datasets**.</span></span>  
  
2.  <span data-ttu-id="a9aca-178">**[DataSet1]** を右クリックし、 **[データセットのプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-178">Right-click **DataSet1** and click **Dataset Properties.**</span></span>  
  
3.  <span data-ttu-id="a9aca-179">**[名前]** ボックスに「 **Expressions**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="a9aca-179">In the **Name** box, type **Expressions**</span></span>  
  
4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
##  <a name="3-display-first-name-initial-and-last-name"></a><a name="Concatenate"></a><span data-ttu-id="a9aca-180">3. 名、イニシャル、姓を表示する</span><span class="sxs-lookup"><span data-stu-id="a9aca-180">3. Display First Name, Initial, and Last Name</span></span>  
 <span data-ttu-id="a9aca-181">姓およびイニシャルを含む名前に評価される式に、**Left** 関数および**連結** (**&**) 演算子を使用します。</span><span class="sxs-lookup"><span data-stu-id="a9aca-181">Use the **Left** function and the **Concatenate** (**&**) operator in an expression that evaluates to a name that includes an initial and a last name.</span></span> <span data-ttu-id="a9aca-182">式を手順どおりに作成することも、手順をスキップして先に進み、チュートリアルから式をコピーして **[式]** ダイアログ ボックスに貼り付けることもできます。</span><span class="sxs-lookup"><span data-stu-id="a9aca-182">You can build the expression step by step or skip ahead in the procedure and copy/paste the expression from the tutorial into the **Expression** dialog box.</span></span>  
  
#### <a name="to-add-the-name-column"></a><span data-ttu-id="a9aca-183">Name 列を追加するには</span><span class="sxs-lookup"><span data-stu-id="a9aca-183">To add the Name column</span></span>  
  
1.  <span data-ttu-id="a9aca-184">**[StateProvince]** 列を右クリックし、 **[列の挿入]** をポイントして、 **[左]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-184">Right-click the **StateProvince** column, point to **Insert Column**, and then click **Left**.</span></span>  
  
     <span data-ttu-id="a9aca-185">**[StateProvince]** 列の左側に、新しい列が追加されます。</span><span class="sxs-lookup"><span data-stu-id="a9aca-185">A new column is added to the left of the **StateProvince** column.</span></span>  
  
2.  <span data-ttu-id="a9aca-186">新しい列のタイトルをクリックし、「**Name**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="a9aca-186">Click the title of the new column and type **Name**</span></span>  
  
3.  <span data-ttu-id="a9aca-187">**[Name]** 列のデータ セルを右クリックし、 **[式]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-187">Right-click the data cell for the **Name** column and click **Expression**.</span></span>  
  
4.  <span data-ttu-id="a9aca-188">**[式]** ダイアログ ボックスで、 **[共通の関数]** を展開し、 **[テキスト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-188">In the **Expression** dialog box, expand **Common Functions**, and then click **Text**.</span></span>  
  
5.  <span data-ttu-id="a9aca-189">**[アイテム]** ボックスの一覧の **[Left]** をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-189">In the **Item** list, double-click **Left**.</span></span>  
  
     <span data-ttu-id="a9aca-190">**Left** 関数が式に追加されます。</span><span class="sxs-lookup"><span data-stu-id="a9aca-190">The **Left** function is added to the expression.</span></span>  
  
6.  <span data-ttu-id="a9aca-191">**[カテゴリ]** ボックスの一覧の **[フィールド (Expressions)]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-191">In the **Category** list, click **Fields (Expressions)**.</span></span>  
  
7.  <span data-ttu-id="a9aca-192">**[値]** ボックスの一覧の **[FirstName]** をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-192">In the **Values** list, double-click **FirstName**.</span></span>  
  
8.  <span data-ttu-id="a9aca-193">「 **, 1)**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="a9aca-193">Type **, 1)**</span></span>  
  
     <span data-ttu-id="a9aca-194">この式により、 **FirstName** 値の左から数えて 1 文字が抽出されます。</span><span class="sxs-lookup"><span data-stu-id="a9aca-194">This expression extracts one character from the **FirstName** value, counting from the left.</span></span>  
  
9. <span data-ttu-id="a9aca-195">「**&" "&**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="a9aca-195">Type **&" "&**</span></span>  
  
10. <span data-ttu-id="a9aca-196">**[値]** ボックスの一覧の **[LastName]** をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-196">In the **Values** list, double-click **LastName**.</span></span>  
  
     <span data-ttu-id="a9aca-197">完成した式は、次のようになります。 `=Left(Fields!FirstName.Value, 1) &" "& Fields!LastName.Value`</span><span class="sxs-lookup"><span data-stu-id="a9aca-197">The completed expression: `=Left(Fields!FirstName.Value, 1) &" "& Fields!LastName.Value`</span></span>  
  
11. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
12. <span data-ttu-id="a9aca-198">**[実行]** をクリックして、レポートをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-198">Click **Run** to preview the report.</span></span>  
  
##  <a name="4-use-images-to-display-gender"></a><a name="Gender"></a><span data-ttu-id="a9aca-199">4. 画像を使用して性別を表示する</span><span class="sxs-lookup"><span data-stu-id="a9aca-199">4. Use Images to Display Gender</span></span>  
 <span data-ttu-id="a9aca-200">画像を使用して個人の性別を示し、3 つ目の画像を使用して不明な性別値を識別します。</span><span class="sxs-lookup"><span data-stu-id="a9aca-200">Use images to show the gender of a person, and identify unknown gender values by using a third image.</span></span> <span data-ttu-id="a9aca-201">レポートに、非表示の画像を 3 つと、画像を表示するための新しい列を追加し、Gender フィールドの値に基づいて、この列に表示する画像を決定します。</span><span class="sxs-lookup"><span data-stu-id="a9aca-201">You will add to the report three hidden images and a new column to display the images, and then determine the image that appears in the column based on the value of the Gender field.</span></span>  
  
 <span data-ttu-id="a9aca-202">レポートを縞状レポートにする際に、画像を格納するテーブル セルに色を適用するには、四角形を追加して、この四角形に画像を追加します。</span><span class="sxs-lookup"><span data-stu-id="a9aca-202">To apply a color to the table cell that contains the image when you make the report a barred report, you will add a rectangle and then add the image to the rectangle.</span></span> <span data-ttu-id="a9aca-203">四角形を使用するのは、背景色を画像には適用せず、四角形に適用できるようにするためです。</span><span class="sxs-lookup"><span data-stu-id="a9aca-203">You need to use a rectangle because you can apply a background color to a rectangle, but not to an image.</span></span>  
  
 <span data-ttu-id="a9aca-204">このチュートリアルでは、Windows と共にインストールされた画像を使用しますが、それ以外の任意の画像を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="a9aca-204">The tutorial uses images that are installed with Windows, but you can use any images available to you.</span></span> <span data-ttu-id="a9aca-205">埋め込み画像を使用する場合は、ローカル コンピューターにもレポート サーバーにもその画像をインストールする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="a9aca-205">You will use embedded images, and they do not need to be installed on your local computer or the report server.</span></span>  
  
#### <a name="to-add-images-to-the-report-body"></a><span data-ttu-id="a9aca-206">画像をレポート本文に追加するには</span><span class="sxs-lookup"><span data-stu-id="a9aca-206">To add images to the report body</span></span>  
  
1.  <span data-ttu-id="a9aca-207">**[デザイン]** をクリックしてデザイン ビューに戻ります。</span><span class="sxs-lookup"><span data-stu-id="a9aca-207">Click **Design** to return to design view.</span></span>  
  
2.  <span data-ttu-id="a9aca-208">リボンの **[挿入]** タブで **[画像]** をクリックして、レポート本文内のテーブルより下をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-208">On the **Insert** tab of the ribbon, click **Image** and then click in the report body, below the table.</span></span>  
  
     <span data-ttu-id="a9aca-209">**[画像のプロパティ]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a9aca-209">The **Image Properties** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="a9aca-210">**[インポート]** をクリックし、C:\Users\Public\Public Pictures\Sample Pictures に移動します。</span><span class="sxs-lookup"><span data-stu-id="a9aca-210">Click **Import** and navigate to C:\Users\Public\Public Pictures\Sample Pictures.</span></span>  
  
4.  <span data-ttu-id="a9aca-211">Penguins.JPG をクリックし、**[開く]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-211">Click Penguins.JPG and click **Open**.</span></span>  
  
     <span data-ttu-id="a9aca-212">[**画像のプロパティ**] ダイアログボックスで、[**表示**] をクリックし、[**非表示**] オプションをクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-212">In the **Image Properties** dialog box, click **Visibility** and then click the **Hide** option.</span></span>  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
6.  <span data-ttu-id="a9aca-213">手順 2. ～ 5. を繰り返します。ただし画像は Koala.JPG を選択します。</span><span class="sxs-lookup"><span data-stu-id="a9aca-213">Repeat steps 2 through 5, but choose Koala.JPG.</span></span>  
  
7.  <span data-ttu-id="a9aca-214">手順 2. ～ 5. を繰り返します。ただし画像は Tulips.JPG を選択します。</span><span class="sxs-lookup"><span data-stu-id="a9aca-214">Repeat steps 2 through 5, but choose Tulips.JPG.</span></span>  
  
#### <a name="to-add-the-gender-column"></a><span data-ttu-id="a9aca-215">Gender 列を追加するには</span><span class="sxs-lookup"><span data-stu-id="a9aca-215">To add the Gender column</span></span>  
  
1.  <span data-ttu-id="a9aca-216">[**名前**] 列を右クリックし、[**列の挿入**] をポイントして、[**右**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-216">Right-click the **Name** column, point to **Insert Column**, and then click **Right**.</span></span>  
  
     <span data-ttu-id="a9aca-217">[**名前**列の右側に新しい列が追加されます。</span><span class="sxs-lookup"><span data-stu-id="a9aca-217">A new column is added to the right of the **Name** column.</span></span>  
  
2.  <span data-ttu-id="a9aca-218">新しい列のタイトルをクリックし、「**Gender**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="a9aca-218">Click the title of the new column and type **Gender**</span></span>  
  
#### <a name="to-add-a-rectangle"></a><span data-ttu-id="a9aca-219">四角形を追加するには</span><span class="sxs-lookup"><span data-stu-id="a9aca-219">To add a rectangle</span></span>  
  
-   <span data-ttu-id="a9aca-220">リボンの [**挿入**] タブで、[**四角形**] をクリックし、[**性別**] 列のデータセル内をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-220">On the **Insert** tab of the ribbon, click **Rectangle** and then click in the data cell of the **Gender** column.</span></span>  
  
     <span data-ttu-id="a9aca-221">四角形がセルに追加されます。</span><span class="sxs-lookup"><span data-stu-id="a9aca-221">A rectangle is added to the cell.</span></span>  
  
#### <a name="to-add-an-image-to-the-rectangle"></a><span data-ttu-id="a9aca-222">四角形に画像を追加するには</span><span class="sxs-lookup"><span data-stu-id="a9aca-222">To add an image to the rectangle</span></span>  
  
1.  <span data-ttu-id="a9aca-223">四角形を右クリックし、[**挿入**] をポイントして、[**イメージ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-223">Right-click in the rectangle, point to **Insert**, and then click **Image**.</span></span>  
  
2.  <span data-ttu-id="a9aca-224">[**イメージのプロパティ**] ダイアログボックスで、[**このイメージを使用する**] の横にある下矢印をクリックし、追加したイメージの1つを選択します (たとえば、Penguins.JPG)。</span><span class="sxs-lookup"><span data-stu-id="a9aca-224">In the **Image Properties** dialog box, click the down arrow beside **Use this image**, and select one of the images you added, for example, Penguins.JPG.</span></span>  
  
3.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
#### <a name="to-use-images-to-show-gender"></a><span data-ttu-id="a9aca-225">画像を使用して性別を示すには</span><span class="sxs-lookup"><span data-stu-id="a9aca-225">To use images to show gender</span></span>  
  
1.  <span data-ttu-id="a9aca-226">[**性別**] 列のデータセルで画像を右クリックし、[**画像のプロパティ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-226">Right-click the image in the data cell in the **Gender** column and click **Image Properties**.</span></span>  
  
2.  <span data-ttu-id="a9aca-227">[**画像のプロパティ**] ダイアログボックスで、[次の**画像を使用**] ボックスの横にある式の [ **fx** ] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-227">In the **Image Properties** dialog box, click the expression **fx** button next to the **Use this image** text box.</span></span>  
  
3.  <span data-ttu-id="a9aca-228">**[式]** ダイアログ ボックスで、 **[共通の関数]** を展開し、 **[プログラム フロー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-228">In the **Expression** dialog box, expand **Common Functions** and click **Program Flow**.</span></span>  
  
4.  <span data-ttu-id="a9aca-229">**[アイテム]** ボックスの一覧の **[Switch]** をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-229">In the **Item** list, double-click **Switch**.</span></span>  
  
5.  <span data-ttu-id="a9aca-230">**[カテゴリ]** ボックスの一覧の **[フィールド (Expressions)]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-230">In the **Category** list, click **Fields (Expressions)**.</span></span>  
  
6.  <span data-ttu-id="a9aca-231">**[値]** ボックスの一覧の **[Gender]** をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-231">In the **Values** list, double-click **Gender**.</span></span>  
  
7.  <span data-ttu-id="a9aca-232">「\*\* ="Male", "Koala",\*\*」と入力します。</span><span class="sxs-lookup"><span data-stu-id="a9aca-232">Type **="Male", "Koala",**</span></span>  
  
8.  <span data-ttu-id="a9aca-233">**[値]** ボックスの一覧の **[Gender]** をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-233">In the **Values** list, double-click **Gender**.</span></span>  
  
9. <span data-ttu-id="a9aca-234">「\*\* ="Female", "Penguins",\*\*」と入力します。</span><span class="sxs-lookup"><span data-stu-id="a9aca-234">Type **="Female", "Penguins",**</span></span>  
  
10. <span data-ttu-id="a9aca-235">**[値]** ボックスの一覧の **[Gender]** をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-235">In the **Values** list, double-click **Gender**.</span></span>  
  
11. <span data-ttu-id="a9aca-236">「**="Unknown", "Tulips")**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="a9aca-236">Type **="Unknown", "Tulips")**</span></span>  
  
     <span data-ttu-id="a9aca-237">完成した式は、次のようになります。 `=Switch(Fields!Gender.Value ="Male", "Koala",Fields!Gender.Value ="Female","Penguins",Fields!Gender.Value ="Unknown","Tulips")`</span><span class="sxs-lookup"><span data-stu-id="a9aca-237">The completed expression: `=Switch(Fields!Gender.Value ="Male", "Koala",Fields!Gender.Value ="Female","Penguins",Fields!Gender.Value ="Unknown","Tulips")`</span></span>  
  
12. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
13. <span data-ttu-id="a9aca-238">もう一度 [ **OK** ] をクリックして、[**画像のプロパティ**] ダイアログボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="a9aca-238">Click **OK** again to close the **Image Properties** dialog box.</span></span>  
  
14. <span data-ttu-id="a9aca-239">**[実行]** をクリックして、レポートをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-239">Click **Run** to preview the report.</span></span>  
  
##  <a name="5-look-up-countryregion-name"></a><a name="Lookup"></a><span data-ttu-id="a9aca-240">5. 国名を検索する</span><span class="sxs-lookup"><span data-stu-id="a9aca-240">5. Look Up CountryRegion Name</span></span>  
 <span data-ttu-id="a9aca-241">国/地域の識別子の代わりに国/地域の名前を表示するには、国データセットを作成し、 **Lookup**関数を使用します。</span><span class="sxs-lookup"><span data-stu-id="a9aca-241">Create the CountryRegion dataset and use the **Lookup** function to display the name of a country/region instead of the identifier of the country/region.</span></span>  
  
#### <a name="to-create-the-countryregion-dataset"></a><span data-ttu-id="a9aca-242">CountryRegion データセットを作成するには</span><span class="sxs-lookup"><span data-stu-id="a9aca-242">To create the CountryRegion dataset</span></span>  
  
1.  <span data-ttu-id="a9aca-243">**[デザイン]** をクリックしてデザイン ビューに戻ります。</span><span class="sxs-lookup"><span data-stu-id="a9aca-243">Click **Design** to return to design view.</span></span>  
  
2.  <span data-ttu-id="a9aca-244">レポートデータペインで、[**新規作成**] をクリックし、[**データセット**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-244">In the Report Data pane, click **New** and then click **Dataset**.</span></span>  
  
3.  <span data-ttu-id="a9aca-245">**[レポートに埋め込まれたデータセットを使用します]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-245">Click **Use a dataset embedded in my report**.</span></span>  
  
4.  <span data-ttu-id="a9aca-246">**[データ ソース]** ボックスの一覧の [ExpressionsDataSource] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-246">In the **Data source** list, select ExpressionsDataSource.</span></span>  
  
5.  <span data-ttu-id="a9aca-247">**[名前]** ボックスに「 **CountryRegion**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="a9aca-247">In the **Name** box, type **CountryRegion**</span></span>  
  
6.  <span data-ttu-id="a9aca-248">クエリの種類に **[テキスト]** が選択されていることを確認し、 **[クエリ デザイナー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-248">Verify that the **Text** query type is selected and click **Query Designer**.</span></span>  
  
7.  <span data-ttu-id="a9aca-249">**[テキストとして編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-249">Click **Edit as Text**.</span></span>  
  
8.  <span data-ttu-id="a9aca-250">次のクエリをコピーし、クエリ ペインに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="a9aca-250">Copy and paste the following query into the query pane:</span></span>  
  
    ```  
    SELECT 1 AS ID, 'American Samoa' AS CountryRegion  
    UNION SELECT 2 AS CountryRegionID, 'Australia' AS CountryRegion  
    UNION SELECT 3 AS ID, 'Canada' AS CountryRegion  
    UNION SELECT 4 AS ID, 'Germany' AS CountryRegion  
    UNION SELECT 5 AS ID, 'Micronesia' AS CountryRegion  
    UNION SELECT 6 AS ID, 'France' AS CountryRegion  
    UNION SELECT 7 AS ID, 'United States' AS CountryRegion  
    UNION SELECT 8 AS ID, 'Brazil' AS CountryRegion  
    UNION SELECT 9 AS ID, 'Mexico' AS CountryRegion  
    UNION SELECT 10 AS ID, 'Japan' AS CountryRegion  
    UNION SELECT 10 AS ID, 'Australia' AS CountryRegion  
    UNION SELECT 12 AS ID, 'United Kingdom' AS CountryRegion  
    ```  
  
9. <span data-ttu-id="a9aca-251">[**実行**] (**!**) をクリックしてクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="a9aca-251">Click **Run** (**!**) to run the query.</span></span>  
  
     <span data-ttu-id="a9aca-252">クエリ結果は国/地域の識別子と名前です。</span><span class="sxs-lookup"><span data-stu-id="a9aca-252">The query results are the country/region identifiers and names.</span></span>  
  
10. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
11. <span data-ttu-id="a9aca-253">**[OK]** を再度クリックして、 **[データセットのプロパティ]** ダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="a9aca-253">Click **OK** again to close the **Dataset Properties** dialog box.</span></span>  
  
#### <a name="to-look-up-values-in-the-countryregion-dataset"></a><span data-ttu-id="a9aca-254">CountryRegion データセット内の値を参照するには</span><span class="sxs-lookup"><span data-stu-id="a9aca-254">To look up values in the CountryRegion dataset</span></span>  
  
1.  <span data-ttu-id="a9aca-255">[ **Country REGION id** ] 列タイトルをクリックし、テキスト "id" を削除します。</span><span class="sxs-lookup"><span data-stu-id="a9aca-255">Click the **Country Region ID** column title and delete the text: ID.</span></span>  
  
2.  <span data-ttu-id="a9aca-256">**[Country Region]** 列のデータ セルを右クリックし、 **[式]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-256">Right-click the data cell for the **Country Region** column and click **Expression**.</span></span>  
  
3.  <span data-ttu-id="a9aca-257">先頭の等号 (=) 部分を除いて、式を削除します。</span><span class="sxs-lookup"><span data-stu-id="a9aca-257">Delete the expression except the initial equal (=) sign.</span></span>  
  
     <span data-ttu-id="a9aca-258">式は次のようになります。 `=`</span><span class="sxs-lookup"><span data-stu-id="a9aca-258">The remaining expression is: `=`</span></span>  
  
4.  <span data-ttu-id="a9aca-259">[**式**] ダイアログボックスで、[**共通の関数**] を展開し、[**その他**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-259">In the **Expression** dialog box, expand **Common Functions** and click **Miscellaneous**.</span></span>  
  
5.  <span data-ttu-id="a9aca-260">[**アイテム**] ボックスの一覧の [**参照**] をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-260">In the **Item** list, double-click **Lookup**.</span></span>  
  
6.  <span data-ttu-id="a9aca-261">**[カテゴリ]** ボックスの一覧の **[フィールド (Expressions)]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-261">In the **Category** list, click **Fields (Expressions)**.</span></span>  
  
7.  <span data-ttu-id="a9aca-262">[**値**] ボックスの一覧で、をダブルクリックし `CountryRegionID` ます。</span><span class="sxs-lookup"><span data-stu-id="a9aca-262">In the **Values** list, double-click `CountryRegionID`.</span></span>  
  
8.  <span data-ttu-id="a9aca-263">カーソルが別の位置にある場合は、`CountryRegionID.Value` の直後に置きます。</span><span class="sxs-lookup"><span data-stu-id="a9aca-263">If the cursor is not already immediately after `CountryRegionID.Value`, place it there.</span></span>  
  
9. <span data-ttu-id="a9aca-264">右かっこを削除し、「**,Fields!ID.value, Fields!CountryRegion.value, "CountryRegion")**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="a9aca-264">Delete the right parenthesis and then type **,Fields!ID.value, Fields!CountryRegion.value, "CountryRegion")**</span></span>  
  
     <span data-ttu-id="a9aca-265">完成した式は、次のようになります。 `=Lookup(Fields!CountryRegionID.Value,Fields!ID.value, Fields!CountryRegion.value, "CountryRegion")`</span><span class="sxs-lookup"><span data-stu-id="a9aca-265">The completed expression: `=Lookup(Fields!CountryRegionID.Value,Fields!ID.value, Fields!CountryRegion.value, "CountryRegion")`</span></span>  
  
     <span data-ttu-id="a9aca-266">**Lookup**関数の構文では、国の値を返す国データセット内の COUNTRYREGIONID と ID の間の参照を指定します。これは、国データセットにも含まれます。</span><span class="sxs-lookup"><span data-stu-id="a9aca-266">The syntax of the **Lookup** function specifies a lookup between CountryRegionID and ID in the CountryRegion dataset that returns the CountryRegion value, which is also in the CountryRegion dataset.</span></span>  
  
10. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
11. <span data-ttu-id="a9aca-267">**[実行]** をクリックして、レポートをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-267">Click **Run** to preview the report.</span></span>  
  
##  <a name="6-count-days-since-last-purchase"></a><a name="Count"></a><span data-ttu-id="a9aca-268">6. 前回の購入からの日数をカウントする</span><span class="sxs-lookup"><span data-stu-id="a9aca-268">6. Count Days Since Last Purchase</span></span>  
 <span data-ttu-id="a9aca-269">列を追加し、 **Now**関数または組み込みグローバル変数を使用して、 `ExecutionTime` ユーザーが前回購入した日から今日までの日数を計算します。</span><span class="sxs-lookup"><span data-stu-id="a9aca-269">Add a column and then use the **Now** function or the `ExecutionTime` built-in global variable to calculate the number of days from today since a person's last purchases.</span></span>  
  
#### <a name="to-add-the-days-ago-column"></a><span data-ttu-id="a9aca-270">Days Ago 列を追加するには</span><span class="sxs-lookup"><span data-stu-id="a9aca-270">To add the Days Ago column</span></span>  
  
1.  <span data-ttu-id="a9aca-271">**[デザイン]** をクリックしてデザイン ビューに戻ります。</span><span class="sxs-lookup"><span data-stu-id="a9aca-271">Click **Design** to return to design view.</span></span>  
  
2.  <span data-ttu-id="a9aca-272">**[Last Purchase]** 列を右クリックし、 **[列の挿入]** をポイントして、 **[右]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-272">Right-click the **Last Purchase** column, point to **Insert Column**, and then click **Right**.</span></span>  
  
     <span data-ttu-id="a9aca-273">**[Last Purchase]** 列の右側に、新しい列が追加されます。</span><span class="sxs-lookup"><span data-stu-id="a9aca-273">A new column is added to the right of the **Last Purchase** column.</span></span>  
  
3.  <span data-ttu-id="a9aca-274">列ヘッダーに「 **Days Ago**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="a9aca-274">In the column header, type **Days Ago**</span></span>  
  
4.  <span data-ttu-id="a9aca-275">**[Days Ago]** 列のデータ セルを右クリックし、 **[式]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-275">Right-click the data cell for the **Days Ago** column and click **Expression**.</span></span>  
  
5.  <span data-ttu-id="a9aca-276">**[式]** ダイアログ ボックスで、**[共通の関数]** を展開し、**[日付と時刻]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-276">In the **Expression** dialog box, expand **Common Functions**, and then click **Date & Time**.</span></span>  
  
6.  <span data-ttu-id="a9aca-277">**[アイテム]** ボックスの一覧の **[DateDiff]** をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-277">In the **Item** list, double-click **DateDiff**.</span></span>  
  
7.  <span data-ttu-id="a9aca-278">カーソルが別の位置にある場合は、`DateDiff(` の直後に置きます。</span><span class="sxs-lookup"><span data-stu-id="a9aca-278">If the cursor is not already immediately after `DateDiff(`, place it there.</span></span>  
  
8.  <span data-ttu-id="a9aca-279">「**"d",**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="a9aca-279">Type **"d",**</span></span>  
  
9. <span data-ttu-id="a9aca-280">**[カテゴリ]** ボックスの一覧の **[フィールド (Expressions)]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-280">In the **Category** list, click **Fields (Expressions)**.</span></span>  
  
10. <span data-ttu-id="a9aca-281">[**値**] ボックスの一覧の [ **lastpurchase**] をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-281">In the **Values** list, double-click **LastPurchase**.</span></span>  
  
11. <span data-ttu-id="a9aca-282">カーソルが別の位置にある場合は、`Fields!LastPurchase.Value` の直後に置きます。</span><span class="sxs-lookup"><span data-stu-id="a9aca-282">If the cursor is not already immediately after `Fields!LastPurchase.Value`, place it there.</span></span>  
  
12. <span data-ttu-id="a9aca-283">型 **、**</span><span class="sxs-lookup"><span data-stu-id="a9aca-283">Type **,**</span></span>  
  
13. <span data-ttu-id="a9aca-284">[**カテゴリ**] ボックスの一覧で、[**日付 & 時刻**] をもう一度クリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-284">In the **Category** list, click **Date & Time** again.</span></span>  
  
14. <span data-ttu-id="a9aca-285">[**アイテム**] ボックスの一覧の [ **Now**] をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-285">In the **Item** list, double-click **Now**.</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="a9aca-286">運用環境のレポートでは、レポートのレンダリングごとに何度も評価される式に **Now** 関数を使用しないでください (レポートの詳細行内など)。</span><span class="sxs-lookup"><span data-stu-id="a9aca-286">In production reports you should not use the **Now** function in expressions that are evaluated multiple times as the report renders (for example, in the detail rows of a report).</span></span> <span data-ttu-id="a9aca-287">**Now** の値が行ごとに変わり、それが式の評価に影響して、微妙に一貫性に欠ける結果を招きます。</span><span class="sxs-lookup"><span data-stu-id="a9aca-287">The value of **Now** changes from row to row and the different values affect the evaluation results of expressions, which leads to results that are subtly inconsistent.</span></span> <span data-ttu-id="a9aca-288">代わりに、に `ExecutionTime` よって提供されるグローバル変数を使用する必要があり [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="a9aca-288">Instead, you should use the `ExecutionTime` global variable that [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] provides.</span></span>  
  
15. <span data-ttu-id="a9aca-289">カーソルが別の位置にある場合は、`Now(` の直後に置きます。</span><span class="sxs-lookup"><span data-stu-id="a9aca-289">If the cursor is not already immediately after `Now(`, place it there.</span></span>  
  
16. <span data-ttu-id="a9aca-290">左かっこを削除し、「**)**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="a9aca-290">Delete the left parenthesis and then type **)**</span></span>  
  
     <span data-ttu-id="a9aca-291">完成した式は、次のようになります。 `=DateDiff("d", Fields!LastPurchase.Value, Now)`</span><span class="sxs-lookup"><span data-stu-id="a9aca-291">The completed expression: `=DateDiff("d", Fields!LastPurchase.Value, Now)`</span></span>  
  
17. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
##  <a name="7-use-an-indicator-to-show-sales-comparison"></a><a name="Indicator"></a><span data-ttu-id="a9aca-292">7. インジケーターを使用して売上比較を表示する</span><span class="sxs-lookup"><span data-stu-id="a9aca-292">7. Use an Indicator to Show Sales Comparison</span></span>  
 <span data-ttu-id="a9aca-293">新しい列を追加し、インジケーターを使用して、ユーザーの年度累計 (YTD) 購入額が平均 YTD 購入額を上回るか下回っているかを示します。</span><span class="sxs-lookup"><span data-stu-id="a9aca-293">Add a new column and use an indicator to show whether a person's year-to-date (YTD) purchases are above or below the average YTD purchases.</span></span> <span data-ttu-id="a9aca-294">**Round** 関数では、値から小数が除去されます。</span><span class="sxs-lookup"><span data-stu-id="a9aca-294">The **Round** function removes decimals from values.</span></span>  
  
 <span data-ttu-id="a9aca-295">インジケーターとその状態を構成するには、多数の手順が必要です。</span><span class="sxs-lookup"><span data-stu-id="a9aca-295">The configuration of the indicator and its states requires many steps.</span></span> <span data-ttu-id="a9aca-296">必要に応じて、「インジケーターを構成するには」の手順に進んで、このチュートリアルの完成した式をコピーして [**式**] ダイアログボックスに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="a9aca-296">If you want to, in the "To configure the indicator" procedure, you can skip ahead and copy/paste the completed expressions from this tutorial into the **Expression** dialog box.</span></span>  
  
#### <a name="to-add-the--or---avg-sales-column"></a><span data-ttu-id="a9aca-297">+ or - AVG Sales 列を追加するには</span><span class="sxs-lookup"><span data-stu-id="a9aca-297">To add the + or - AVG Sales column</span></span>  
  
1.  <span data-ttu-id="a9aca-298">**[YTD Purchase]** 列を右クリックし、 **[列の挿入]** をポイントして、 **[右]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-298">Right-click the **YTD Purchase** column, point to **Insert Column**, and then click **Right**.</span></span>  
  
     <span data-ttu-id="a9aca-299">**[YTD Purchase]** 列の右側に、新しい列が追加されます。</span><span class="sxs-lookup"><span data-stu-id="a9aca-299">A new column is added to the right of the **YTD Purchase** column.</span></span>  
  
2.  <span data-ttu-id="a9aca-300">新しい列のタイトルをクリックし、「**+ or - AVG Sales**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="a9aca-300">Click the title of the column and type **+ or - AVG Sales**</span></span>  
  
#### <a name="to-add-an-indicator"></a><span data-ttu-id="a9aca-301">インジケーターを追加するには</span><span class="sxs-lookup"><span data-stu-id="a9aca-301">To add an indicator</span></span>  
  
1.  <span data-ttu-id="a9aca-302">リボンの [**挿入**] タブで [**インジケーター**] をクリックし、[ **+ or-AVG Sales** ] 列のデータセルをクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-302">On the **Insert** tab of the ribbon, click **Indicator**, and then click the data cell for the **+ or - AVG Sales** column.</span></span>  
  
     <span data-ttu-id="a9aca-303">**[インジケーターの種類の選択]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a9aca-303">The **Select Indicator Type** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="a9aca-304">アイコン セットの **[指向性]** グループ内で、3 つの灰色の矢印のセットをクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-304">In the **Directional** group of icon sets, click the set of three gray arrows.</span></span>  
  
3.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
#### <a name="to-configure-the-indicator"></a><span data-ttu-id="a9aca-305">インジケーターを構成するには</span><span class="sxs-lookup"><span data-stu-id="a9aca-305">To configure the indicator</span></span>  
  
1.  <span data-ttu-id="a9aca-306">インジケーターを右クリックし、 **[インジケーターのプロパティ]** をクリックして、 **[値と状態]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-306">Right-click the indicator, click **Indicator Properties**, and then click **Value and States**.</span></span>  
  
2.  <span data-ttu-id="a9aca-307">**[値]** ボックスの横にある式 ( **[Fx]** ) ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-307">Click the expression **fx** button next to the **Value** text box.</span></span>  
  
3.  <span data-ttu-id="a9aca-308">**[式]** ダイアログ ボックスで、 **[共通の関数]** を展開し、 **[数学]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-308">In the **Expression** dialog box, expand **Common Functions**, and then click **Math**.</span></span>  
  
4.  <span data-ttu-id="a9aca-309">**[アイテム]** ボックスの一覧の **[Round]** をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-309">In the **Item** list, double-click **Round**.</span></span>  
  
5.  <span data-ttu-id="a9aca-310">**[カテゴリ]** ボックスの一覧の **[フィールド (Expressions)]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-310">In the **Category** list, click **Fields (Expressions)**.</span></span>  
  
6.  <span data-ttu-id="a9aca-311">[**値**] ボックスの一覧で、[ **YTDPurchase**] をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-311">In the **Values** list, double-click **YTDPurchase**.</span></span>  
  
7.  <span data-ttu-id="a9aca-312">カーソルが別の位置にある場合は、`Fields!YTDPurchase.Value` の直後に置きます。</span><span class="sxs-lookup"><span data-stu-id="a9aca-312">If the cursor is not already immediately after `Fields!YTDPurchase.Value`, place it there.</span></span>  
  
8.  <span data-ttu-id="a9aca-313">各種**-**</span><span class="sxs-lookup"><span data-stu-id="a9aca-313">Type  **-**</span></span>  
  
9. <span data-ttu-id="a9aca-314">[**共通の関数**] を再度展開し、[**集計**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-314">Expand **Common Functions** again and click **Aggregate**.</span></span>  
  
10. <span data-ttu-id="a9aca-315">[**アイテム**] ボックスの一覧の [ **Avg**] をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-315">In the **Item** list, double-click **Avg**.</span></span>  
  
11. <span data-ttu-id="a9aca-316">**[カテゴリ]** ボックスの一覧の **[フィールド (Expressions)]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-316">In the **Category** list, click **Fields (Expressions)**.</span></span>  
  
12. <span data-ttu-id="a9aca-317">[**値**] ボックスの一覧で、[ **YTDPurchase**] をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-317">In the **Values** list, double-click **YTDPurchase**.</span></span>  
  
13. <span data-ttu-id="a9aca-318">カーソルが別の位置にある場合は、`Fields!YTDPurchase.Value` の直後に置きます。</span><span class="sxs-lookup"><span data-stu-id="a9aca-318">If the cursor is not already immediately after `Fields!YTDPurchase.Value`, place it there.</span></span>  
  
14. <span data-ttu-id="a9aca-319">「**, "Expressions"))**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="a9aca-319">Type **, "Expressions"))**</span></span>  
  
     <span data-ttu-id="a9aca-320">完成した式は、次のようになります。 `=Round(Fields!YTDPurchase.Value - Avg(Fields!YTDPurchase.Value, "Expressions"))`</span><span class="sxs-lookup"><span data-stu-id="a9aca-320">The completed expression: `=Round(Fields!YTDPurchase.Value - Avg(Fields!YTDPurchase.Value, "Expressions"))`</span></span>  
  
15. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
16. <span data-ttu-id="a9aca-321">**[状態の単位]** ボックスの一覧の **[数値]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-321">In the **States Measurement Unit** box, select **Numeric**.</span></span>  
  
17. <span data-ttu-id="a9aca-322">下矢印のある行で、 **[開始]** 値のボックスの右にある **[fx]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-322">In the row with the down-pointing arrow, click the **fx** button to the right of the text box for the **Start** value.</span></span>  
  
18. <span data-ttu-id="a9aca-323">**[式]** ダイアログ ボックスで、 **[共通の関数]** を展開し、 **[数学]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-323">In the **Expression** dialog box, expand **Common Functions**, and then click **Math**.</span></span>  
  
19. <span data-ttu-id="a9aca-324">**[アイテム]** ボックスの一覧の **[Round]** をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-324">In the **Item** list, double-click **Round**.</span></span>  
  
20. <span data-ttu-id="a9aca-325">**[カテゴリ]** ボックスの一覧の **[フィールド (Expressions)]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-325">In the **Category** list, click **Fields (Expressions)**.</span></span>  
  
21. <span data-ttu-id="a9aca-326">[**値**] ボックスの一覧で、[ **YTDPurchase**] をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-326">In the **Values** list, double-click **YTDPurchase**.</span></span>  
  
22. <span data-ttu-id="a9aca-327">カーソルが別の位置にある場合は、`Fields!YTDPurchase.Value` の直後に置きます。</span><span class="sxs-lookup"><span data-stu-id="a9aca-327">If the cursor is not already immediately after `Fields!YTDPurchase.Value`, place it there.</span></span>  
  
23. <span data-ttu-id="a9aca-328">各種**-**</span><span class="sxs-lookup"><span data-stu-id="a9aca-328">Type  **-**</span></span>  
  
24. <span data-ttu-id="a9aca-329">[**共通の関数**] を再度展開し、[**集計**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-329">Expand **Common Functions** again and click **Aggregate**.</span></span>  
  
25. <span data-ttu-id="a9aca-330">[**アイテム**] ボックスの一覧の [ **Avg**] をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-330">In the **Item** list, double-click **Avg**.</span></span>  
  
26. <span data-ttu-id="a9aca-331">**[カテゴリ]** ボックスの一覧の **[フィールド (Expressions)]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-331">In the **Category** list, click **Fields (Expressions)**.</span></span>  
  
27. <span data-ttu-id="a9aca-332">[**値**] ボックスの一覧で、[ **YTDPurchase**] をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-332">In the **Values** list, double-click **YTDPurchase**.</span></span>  
  
28. <span data-ttu-id="a9aca-333">カーソルが別の位置にある場合は、`Fields!YTDPurchase.Value` の直後に置きます。</span><span class="sxs-lookup"><span data-stu-id="a9aca-333">If the cursor is not already immediately after `Fields!YTDPurchase.Value`, place it there.</span></span>  
  
29. <span data-ttu-id="a9aca-334">「**, "Expressions")) < 0**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="a9aca-334">Type **, "Expressions")) < 0**</span></span>  
  
     <span data-ttu-id="a9aca-335">完成した式は、次のようになります。 `=Round(Fields!YTDPurchase.Value - Avg(Fields!YTDPurchase.Value, "Expressions")) < 0`</span><span class="sxs-lookup"><span data-stu-id="a9aca-335">The completed expression: `=Round(Fields!YTDPurchase.Value - Avg(Fields!YTDPurchase.Value, "Expressions")) < 0`</span></span>  
  
30. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
31. <span data-ttu-id="a9aca-336">**[終了]** 値のボックスに「 **0**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="a9aca-336">In the text box for the **End** value, type **0**</span></span>  
  
32. <span data-ttu-id="a9aca-337">水平矢印のある行をクリックし、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-337">Click the row with the horizontal-pointing arrow and click **Delete**.</span></span>  
  
33. <span data-ttu-id="a9aca-338">上矢印のある行で、 **[開始]** ボックスに「 **0**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="a9aca-338">In the row with the up-pointing arrow, in the **Start** box, type **0**</span></span>  
  
34. <span data-ttu-id="a9aca-339">**[終了]** 値のボックスの右にある **[Fx]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-339">Click the **fx** button to the right of the text box for the **End** value.</span></span>  
  
35. <span data-ttu-id="a9aca-340">[**式**] ダイアログボックスで、次の式を作成します。`=Round(Fields!YTDPurchase.Value - Avg(Fields!YTDPurchase.Value, "Expressions")) >0`</span><span class="sxs-lookup"><span data-stu-id="a9aca-340">In the **Expression** dialog box, create the expression: `=Round(Fields!YTDPurchase.Value - Avg(Fields!YTDPurchase.Value, "Expressions")) >0`</span></span>  
  
36. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
37. <span data-ttu-id="a9aca-341">**[OK]** を再度クリックして、 **[インジケーターのプロパティ]** ダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="a9aca-341">Click **OK** again to close the **Indicator properties** dialog box.</span></span>  
  
38. <span data-ttu-id="a9aca-342">**[実行]** をクリックして、レポートをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-342">Click **Run** to preview the report.</span></span>  
  
##  <a name="8-make-the-report-a-green-bar-report"></a><a name="GreenBar"></a><span data-ttu-id="a9aca-343">8. レポートに "緑色のバー" レポートを作成する</span><span class="sxs-lookup"><span data-stu-id="a9aca-343">8. Make the Report a "Green Bar" Report</span></span>  
 <span data-ttu-id="a9aca-344">パラメーターを使用して、レポート内で 1 行おきに適用する色を指定し、レポートを縞状にします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-344">Use a parameter to specify the color to apply to alternating rows in the report, making it a barred report.</span></span>  
  
#### <a name="to-add-a-parameter"></a><span data-ttu-id="a9aca-345">パラメーターを追加するには</span><span class="sxs-lookup"><span data-stu-id="a9aca-345">To add a parameter</span></span>  
  
1.  <span data-ttu-id="a9aca-346">**[デザイン]** をクリックしてデザイン ビューに戻ります。</span><span class="sxs-lookup"><span data-stu-id="a9aca-346">Click **Design** to return to design view.</span></span>  
  
2.  <span data-ttu-id="a9aca-347">**レポート データ** ペインで、 **[パラメーター]** を右クリックし、 **[パラメーターの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-347">In the **Report Data** pane, right-click **Parameters** and click **Add Parameter**.</span></span>  
  
     <span data-ttu-id="a9aca-348">**[レポート パラメーターのプロパティ]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a9aca-348">The **Report Parameter Properties** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="a9aca-349">**[プロンプト]** に「 **Choose color**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="a9aca-349">In **Prompt**, type **Choose color**</span></span>  
  
4.  <span data-ttu-id="a9aca-350">**[名前]** に「 **RowColor**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="a9aca-350">In **Name**, type **RowColor**</span></span>  
  
5.  <span data-ttu-id="a9aca-351">左側のウィンドウで、[**使用可能な値**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-351">In the left pane, click **Available Values**.</span></span>  
  
6.  <span data-ttu-id="a9aca-352">[**値の指定] を**クリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-352">Click **Specify values**.</span></span>  
  
7.  <span data-ttu-id="a9aca-353">**[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-353">Click **Add**.</span></span>  
  
8.  <span data-ttu-id="a9aca-354">[**ラベル**] ボックスに「**黄**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="a9aca-354">In the **Label** box, type: **Yellow**</span></span>  
  
9. <span data-ttu-id="a9aca-355">**[値]** ボックスに「 **Yellow**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="a9aca-355">In the **Value** box, type **Yellow**</span></span>  
  
10. <span data-ttu-id="a9aca-356">**[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-356">Click **Add**.</span></span>  
  
11. <span data-ttu-id="a9aca-357">**[ラベル]** ボックスに「 **Green**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="a9aca-357">In the **Label** box, type **Green**</span></span>  
  
12. <span data-ttu-id="a9aca-358">**[値]** ボックスに「 **PaleGreen**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="a9aca-358">In the **Value** box, type **PaleGreen**</span></span>  
  
13. <span data-ttu-id="a9aca-359">**[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-359">Click **Add**.</span></span>  
  
14. <span data-ttu-id="a9aca-360">**[ラベル]** ボックスに「 **Blue**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="a9aca-360">In the **Label** box, type **Blue**</span></span>  
  
15. <span data-ttu-id="a9aca-361">**[値]** ボックスに「 **LightBlue**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="a9aca-361">In the **Value** box, type **LightBlue**</span></span>  
  
16. <span data-ttu-id="a9aca-362">**[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-362">Click **Add**.</span></span>  
  
17. <span data-ttu-id="a9aca-363">**[ラベル]** ボックスに「 **Pink**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="a9aca-363">In the **Label** box, type **Pink**</span></span>  
  
18. <span data-ttu-id="a9aca-364">**[値]** ボックスに「 **Pink**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="a9aca-364">In the **Value** box, type **Pink**</span></span>  
  
19. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
#### <a name="to-apply-alternating-colors-to-detail-rows"></a><span data-ttu-id="a9aca-365">詳細行に色を交互に適用する</span><span class="sxs-lookup"><span data-stu-id="a9aca-365">To apply alternating colors to detail rows</span></span>  
  
1.  <span data-ttu-id="a9aca-366">リボンの [**表示**] タブをクリックし、[**プロパティ**] が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="a9aca-366">Click the **View** tab on the ribbon and verify that **Properties** is selected.</span></span>  
  
2.  <span data-ttu-id="a9aca-367">[**名前**] 列のデータセルをクリックし、Shift キーを押します。</span><span class="sxs-lookup"><span data-stu-id="a9aca-367">Click the data cell for the **Name** column and press the Shift key.</span></span>  
  
3.  <span data-ttu-id="a9aca-368">行内のセルを 1 つおきにクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-368">One by one, click the other cells in the row.</span></span>  
  
4.  <span data-ttu-id="a9aca-369">プロパティ ペインで、 **[BackgroundColor]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-369">In the Properties pane, click **BackgroundColor**.</span></span>  
  
     <span data-ttu-id="a9aca-370">プロパティペインのプロパティがカテゴリ別に一覧表示されている場合は、[**塗りつぶし**] カテゴリの下に [ **BackgroundColor** ] が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a9aca-370">If your Properties pane lists properties by category, you will find the **BackgroundColor** under the **Fill** category.</span></span>  
  
5.  <span data-ttu-id="a9aca-371">下矢印をクリックし、 **[式]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-371">Click the down arrow and then click **Expression**.</span></span>  
  
6.  <span data-ttu-id="a9aca-372">**[式]** ダイアログ ボックスで、 **[共通の関数]** を展開し、 **[プログラム フロー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-372">In the **Expression** dialog box, expand **Common Functions**, and then click **Program Flow**.</span></span>  
  
7.  <span data-ttu-id="a9aca-373">**[アイテム]** ボックスの一覧の **[IIf]** をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-373">In the **Item** list, double-click **IIf**.</span></span>  
  
8.  <span data-ttu-id="a9aca-374">[**共通の関数**] を展開し、[**集計**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-374">Expand **Common Functions** and click **Aggregate**.</span></span>  
  
9. <span data-ttu-id="a9aca-375">[**アイテム**] ボックスの一覧の [ **RunningValue**] をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-375">In the **Item** list, double-click **RunningValue**.</span></span>  
  
10. <span data-ttu-id="a9aca-376">**[カテゴリ]** ボックスの一覧の **[フィールド (Expressions)]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-376">In the **Category** list, click **Fields (Expressions)**.</span></span>  
  
11. <span data-ttu-id="a9aca-377">**[値]** ボックスの一覧の **[FirstName]** をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-377">In the **Values** list, double-click **FirstName**.</span></span>  
  
12. <span data-ttu-id="a9aca-378">カーソルがまだの直後にない場合は、 `Fields!FirstName.Value` そこに配置し **、「」** と入力します。</span><span class="sxs-lookup"><span data-stu-id="a9aca-378">If the cursor is not already immediately after `Fields!FirstName.Value`, place it there and type **,**</span></span>  
  
13. <span data-ttu-id="a9aca-379">[**共通の関数**] を展開し、[**集計**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-379">Expand **Common Functions** and click **Aggregate**.</span></span>  
  
14. <span data-ttu-id="a9aca-380">[**アイテム**] ボックスの一覧の [ **Count**] をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-380">In the **Item** list, double-click **Count**.</span></span>  
  
15. <span data-ttu-id="a9aca-381">カーソルが別の位置にある場合は、`Count(` の直後に置きます。</span><span class="sxs-lookup"><span data-stu-id="a9aca-381">If the cursor is not already immediately after `Count(`, place it there.</span></span>  
  
16. <span data-ttu-id="a9aca-382">左かっこを削除し **、「式」** と入力します。</span><span class="sxs-lookup"><span data-stu-id="a9aca-382">Delete the left parenthesis and then type **,"Expressions")**</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a9aca-383">Expressions は、データ行をカウントするデータセットの名前です。</span><span class="sxs-lookup"><span data-stu-id="a9aca-383">Expressions is the name of the dataset in which to count data rows.</span></span>  
  
17. <span data-ttu-id="a9aca-384">[**演算子**] を展開し、[**算術**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-384">Expand **Operators** and click **Arithmetic**.</span></span>  
  
18. <span data-ttu-id="a9aca-385">[**アイテム**] ボックスの一覧の [ **Mod**] をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-385">In the **Item** list, double-click **Mod**.</span></span>  
  
19. <span data-ttu-id="a9aca-386">カーソルが別の位置にある場合は、`Mod` の直後に置きます。</span><span class="sxs-lookup"><span data-stu-id="a9aca-386">If the cursor is not already immediately after `Mod`, place it there.</span></span>  
  
20. <span data-ttu-id="a9aca-387">「**2 =0,**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="a9aca-387">Type  **2 =0,**</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="a9aca-388">2 という数値の前に、必ずスペースを入れてください。</span><span class="sxs-lookup"><span data-stu-id="a9aca-388">Be sure you include a space before you type the number 2.</span></span>  
  
21. <span data-ttu-id="a9aca-389">**[パラメーター]** をクリックし、 **[値]** ボックスの一覧の **[RowColor]** をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-389">Click **Parameters** and in the **Values** list, double-click **RowColor**.</span></span>  
  
22. <span data-ttu-id="a9aca-390">カーソルが別の位置にある場合は、`Parameters!RowColor.Value` の直後に置きます。</span><span class="sxs-lookup"><span data-stu-id="a9aca-390">If the cursor is not already immediately after `Parameters!RowColor.Value`, place it there.</span></span>  
  
23. <span data-ttu-id="a9aca-391">「 **, "白色")」と入力します。**</span><span class="sxs-lookup"><span data-stu-id="a9aca-391">Type **, "White")**</span></span>  
  
     <span data-ttu-id="a9aca-392">完成した式は、次のようになります。 `=IIf(RunningValue(Fields!FirstName.Value,Count, "Expressions") Mod 2 =0, Parameters!RowColor.Value, "White")`</span><span class="sxs-lookup"><span data-stu-id="a9aca-392">The completed expression: `=IIf(RunningValue(Fields!FirstName.Value,Count, "Expressions") Mod 2 =0, Parameters!RowColor.Value, "White")`</span></span>  
  
24. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
#### <a name="run-the-report"></a><span data-ttu-id="a9aca-393">レポートを実行する</span><span class="sxs-lookup"><span data-stu-id="a9aca-393">Run the Report</span></span>  
  
1.  <span data-ttu-id="a9aca-394">[**ホーム**] タブが表示されていない場合は、[**ホーム**] をクリックしてデザインビューに戻ります。</span><span class="sxs-lookup"><span data-stu-id="a9aca-394">If not on the **Home** tab, click **Home** to return to design view.</span></span>  
  
2.  <span data-ttu-id="a9aca-395">**[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-395">Click **Run**.</span></span>  
  
3.  <span data-ttu-id="a9aca-396">[**色の選択**] ドロップダウンリストで、レポートの白以外のバーの色を選択します。</span><span class="sxs-lookup"><span data-stu-id="a9aca-396">In the **Choose color** drop-down list, select the color of the non-white bars on the report.</span></span>  
  
4.  <span data-ttu-id="a9aca-397">**[レポートの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-397">Click **View Report**.</span></span>  
  
     <span data-ttu-id="a9aca-398">選択した背景色が 1 行おきに適用された状態でレポートが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a9aca-398">The report renders and alternating rows have the background that you chose.</span></span>  
  
##  <a name="optional-format-date-column"></a><a name="DateFormat"></a><span data-ttu-id="a9aca-399">optional日付列の書式を設定する</span><span class="sxs-lookup"><span data-stu-id="a9aca-399">(optional) Format Date Column</span></span>  
 <span data-ttu-id="a9aca-400">日付を含む、**最後に購入**した列の書式を設定します。</span><span class="sxs-lookup"><span data-stu-id="a9aca-400">Format the **Last Purchase** column, which contains dates.</span></span>  
  
#### <a name="to-format-date-column"></a><span data-ttu-id="a9aca-401">日付列の書式を設定するには</span><span class="sxs-lookup"><span data-stu-id="a9aca-401">To format date column</span></span>  
  
1.  <span data-ttu-id="a9aca-402">**[デザイン]** をクリックしてデザイン ビューに戻ります。</span><span class="sxs-lookup"><span data-stu-id="a9aca-402">Click **Design** to return to design view.</span></span>  
  
2.  <span data-ttu-id="a9aca-403">[ **Last Purchase** ] 列のデータセルを右クリックし、[**テキストボックスのプロパティ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-403">Right-click the data cell for the **Last Purchase** column and click **Text Box Properties**.</span></span>  
  
3.  <span data-ttu-id="a9aca-404">[**テキストボックスのプロパティ**] ダイアログボックスで、[**数値**] をクリックし、[**日付**] をクリックして、種類\*\* \* 1/31/2000\*\*をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-404">In the **Text Box Properties** dialog box, click **Number**, click **Date**, and then click the type **\*1/31/2000**.</span></span>  
  
4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
##  <a name="optional-add-a-report-title"></a><a name="Title"></a><span data-ttu-id="a9aca-405">optionalレポートタイトルを追加する</span><span class="sxs-lookup"><span data-stu-id="a9aca-405">(optional) Add a Report Title</span></span>  
 <span data-ttu-id="a9aca-406">レポートにタイトルを追加します。</span><span class="sxs-lookup"><span data-stu-id="a9aca-406">Add a title to the report.</span></span>  
  
#### <a name="to-add-a-report-title"></a><span data-ttu-id="a9aca-407">レポート タイトルを追加するには</span><span class="sxs-lookup"><span data-stu-id="a9aca-407">To add a report title</span></span>  
  
1.  <span data-ttu-id="a9aca-408">デザイン画面で、 **[クリックしてタイトルを追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-408">On the design surface, click **Click to add title**.</span></span>  
  
2.  <span data-ttu-id="a9aca-409">「 **Sales Comparison Summary**」と入力し、テキストボックスの外側をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-409">Type **Sales Comparison Summary**, and then click outside the text box.</span></span>  
  
3.  <span data-ttu-id="a9aca-410">**売上比較の概要**が含まれているテキストボックスを右クリックし、[**テキストボックスのプロパティ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-410">Right-click the text box that contains **Sales Comparison Summary** and click **Text Box Properties**.</span></span>  
  
4.  <span data-ttu-id="a9aca-411">**[テキスト ボックスのプロパティ]** ダイアログ ボックスで、 **[フォント]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-411">In the **Text Box Properties** dialog box, click **Font**.</span></span>  
  
5.  <span data-ttu-id="a9aca-412">**[サイズ]** ボックスの一覧の **[18pt]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="a9aca-412">In the **Size** list, select **18pt**.</span></span>  
  
6.  <span data-ttu-id="a9aca-413">[**色**] ボックスの一覧の [**灰色**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-413">In the **Color** list, select **Gray**.</span></span>  
  
7.  <span data-ttu-id="a9aca-414">[**太字**] と [**斜体**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="a9aca-414">Select  **Bold** and  **Italic**.</span></span>  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
##  <a name="optional-save-the-report"></a><a name="Save"></a><span data-ttu-id="a9aca-415">optionalレポートを保存する</span><span class="sxs-lookup"><span data-stu-id="a9aca-415">(optional) Save the Report</span></span>  
 <span data-ttu-id="a9aca-416">レポートは、レポート サーバー、SharePoint ライブラリ、またはコンピューターに保存することができます。</span><span class="sxs-lookup"><span data-stu-id="a9aca-416">You can save reports to a report server, SharePoint library, or your computer.</span></span> <span data-ttu-id="a9aca-417">詳細については、「[レポートの保存 &#40;レポート ビルダー&#41;](report-builder/saving-reports-report-builder.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a9aca-417">For more information, see [Saving Reports &#40;Report Builder&#41;](report-builder/saving-reports-report-builder.md).</span></span>  
  
 <span data-ttu-id="a9aca-418">このチュートリアルでは、レポートをレポート サーバーに保存します。</span><span class="sxs-lookup"><span data-stu-id="a9aca-418">In this tutorial, save the report to a report server.</span></span> <span data-ttu-id="a9aca-419">レポート サーバーにアクセスできない場合は、レポートをコンピューターに保存してください。</span><span class="sxs-lookup"><span data-stu-id="a9aca-419">If you do not have access to a report server, save the report to your computer.</span></span>  
  
#### <a name="to-save-the-report-to-a-report-server"></a><span data-ttu-id="a9aca-420">レポート サーバーにレポートを保存するには</span><span class="sxs-lookup"><span data-stu-id="a9aca-420">To save the report to a report server</span></span>  
  
1.  <span data-ttu-id="a9aca-421">**レポート ビルダー** のボタンの **[名前を付けて保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-421">From the **Report Builder** button, click **Save As**.</span></span>  
  
2.  <span data-ttu-id="a9aca-422">**[最近使ったサイトとサーバー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-422">Click **Recent Sites and Servers**.</span></span>  
  
3.  <span data-ttu-id="a9aca-423">レポートを保存する権限があるレポート サーバーの名前を入力するか選択します。</span><span class="sxs-lookup"><span data-stu-id="a9aca-423">Select or type the name of the report server where you have permission to save reports.</span></span>  
  
     <span data-ttu-id="a9aca-424">"レポート サーバーに接続しています" というメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a9aca-424">The message "Connecting to report server" appears.</span></span> <span data-ttu-id="a9aca-425">接続が完了すると、レポート サーバー管理者がレポートの既定の場所として指定したレポート フォルダーのコンテンツが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a9aca-425">When the connection is complete, you will see the contents of the report folder that the report server administrator specified as the default report location.</span></span>  
  
4.  <span data-ttu-id="a9aca-426">[**名前**] で、既定の名前を「 **Sales Comparison Summary**」に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="a9aca-426">In **Name**, replace the default name with **Sales Comparison Summary**.</span></span>  
  
5.  <span data-ttu-id="a9aca-427">**[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-427">Click **Save**.</span></span>  
  
 <span data-ttu-id="a9aca-428">レポートがレポート サーバーに保存されます。</span><span class="sxs-lookup"><span data-stu-id="a9aca-428">The report is saved to the report server.</span></span> <span data-ttu-id="a9aca-429">接続しているレポート サーバーの名前がウィンドウ下部のステータス バーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="a9aca-429">The name of report server that you are connected to appears in the status bar at the bottom of the window.</span></span>  
  
#### <a name="to-save-the-report-to-your-computer"></a><span data-ttu-id="a9aca-430">自分のコンピューターにレポートを保存するには</span><span class="sxs-lookup"><span data-stu-id="a9aca-430">To save the report to your computer</span></span>  
  
1.  <span data-ttu-id="a9aca-431">**レポート ビルダー** のボタンの **[名前を付けて保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-431">From the **Report Builder** button, click **Save As**.</span></span>  
  
2.  <span data-ttu-id="a9aca-432">**[デスクトップ]**、 **[マイ ドキュメント]**、または **[マイ コンピューター]** をクリックして、レポートを保存するフォルダーを参照します。</span><span class="sxs-lookup"><span data-stu-id="a9aca-432">Click **Desktop**, **My Documents**, or **My computer**, and then browse to the folder where you want to save the report.</span></span>  
  
3.  <span data-ttu-id="a9aca-433">[**名前**] で、既定の名前を「 **Sales Comparison Summary**」に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="a9aca-433">In **Name**, replace the default name with **Sales Comparison Summary**.</span></span>  
  
4.  <span data-ttu-id="a9aca-434">**[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9aca-434">Click **Save**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9aca-435">参照</span><span class="sxs-lookup"><span data-stu-id="a9aca-435">See Also</span></span>  
 <span data-ttu-id="a9aca-436">[式 &#40;レポート ビルダーおよび SSRS&#41;](report-design/expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="a9aca-436">[Expressions &#40;Report Builder and SSRS&#41;](report-design/expressions-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="a9aca-437">[式の例 (レポート ビルダーおよび SSRS)](report-design/expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="a9aca-437">[Expression Examples &#40;Report Builder and SSRS&#41;](report-design/expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="a9aca-438">[インジケーター &#40;レポートビルダーと SSRS&#41;](report-design/indicators-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="a9aca-438">[Indicators &#40;Report Builder and SSRS&#41;](report-design/indicators-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="a9aca-439">[画像、テキストボックス、四角形、および行 &#40;レポートビルダーと SSRS&#41;](report-design/rectangles-and-lines-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="a9aca-439">[Images, Text Boxes, Rectangles, and Lines &#40;Report Builder and SSRS&#41;](report-design/rectangles-and-lines-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="a9aca-440">[テーブル &#40;レポートビルダーと SSRS&#41;](report-design/tables-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="a9aca-440">[Tables &#40;Report Builder  and SSRS&#41;](report-design/tables-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="a9aca-441">レポート &#40;レポートビルダーおよび SSRS&#41;にデータを追加する</span><span class="sxs-lookup"><span data-stu-id="a9aca-441">Add Data to a Report &#40;Report Builder and SSRS&#41;</span></span>](report-data/report-datasets-ssrs.md)  
  
  
