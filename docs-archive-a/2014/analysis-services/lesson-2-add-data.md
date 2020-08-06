---
title: 'レッスン 2: データの追加 |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 13c3a8cc-b1db-4aba-ad9b-038b7971be8d
author: minewiskan
ms.author: owend
ms.openlocfilehash: c844ea6558949407ca9b8206601ff7fe802ec399
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634122"
---
# <a name="lesson-2-add-data"></a><span data-ttu-id="a13e8-102">レッスン 2: データを追加する</span><span class="sxs-lookup"><span data-stu-id="a13e8-102">Lesson 2: Add Data</span></span>
  <span data-ttu-id="a13e8-103">このレッスンでは、 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] のテーブルのインポート ウィザードを使用して、AdventureWorksDW SQL データベースに接続し、データを選択し、プレビューして、データをフィルター処理した後、それらのデータをモデル ワークスペース内にインポートします。</span><span class="sxs-lookup"><span data-stu-id="a13e8-103">In this lesson, you will use the Table Import Wizard in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] to connect to the AdventureWorksDW SQL database, select data, preview, and filter the data, and then import the data into your model workspace.</span></span>  
  
 <span data-ttu-id="a13e8-104">テーブルのインポート ウィザードを使用すると、Access、SQL、Oracle、Sybase、Informix、DB2、Teradata など、さまざまなリレーショナル ソースからデータをインポートできます。</span><span class="sxs-lookup"><span data-stu-id="a13e8-104">By using the Table Import Wizard, you can import data from a variety of relational sources: Access, SQL, Oracle, Sybase, Informix, DB2, Teradata, and more.</span></span> <span data-ttu-id="a13e8-105">それぞれのリレーショナル ソースからデータをインポートする手順は、以下で説明する手順とそれほど変わりません。</span><span class="sxs-lookup"><span data-stu-id="a13e8-105">The steps for importing data from each of these relational sources are very similar to what is described below.</span></span> <span data-ttu-id="a13e8-106">また、データはストアド プロシージャを使用して選択できます。</span><span class="sxs-lookup"><span data-stu-id="a13e8-106">Additionally, data can be selected using a stored procedure.</span></span>  
  
 <span data-ttu-id="a13e8-107">データのインポートと、インポート可能なデータ ソースの種類に関する詳細については、「[データ ソース (SSAS テーブル)](data-sources-ssas-tabular.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a13e8-107">To learn more about importing data and the different types of data sources you can import from, see [Data Sources &#40;SSAS Tabular&#41;](data-sources-ssas-tabular.md).</span></span>  
  
 <span data-ttu-id="a13e8-108">このレッスンの推定所要時間: **20 分**</span><span class="sxs-lookup"><span data-stu-id="a13e8-108">Estimated time to complete this lesson: **20 minutes**</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="a13e8-109">前提条件</span><span class="sxs-lookup"><span data-stu-id="a13e8-109">Prerequisites</span></span>  
 <span data-ttu-id="a13e8-110">このトピックは、表形式モデルのチュートリアルの一部であり、チュートリアルでの順番に従って実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a13e8-110">This topic is part of a tabular modeling tutorial, which should be completed in order.</span></span> <span data-ttu-id="a13e8-111">このレッスンの実習を行う前に、前の「 [レッスン 1: 新しいテーブル モデル プロジェクトの作成](lesson-1-create-a-new-tabular-model-project.md)」を完了している必要があります。</span><span class="sxs-lookup"><span data-stu-id="a13e8-111">Before performing the tasks in this lesson, you should have completed the previous lesson: [Lesson 1: Create a New Tabular Model Project](lesson-1-create-a-new-tabular-model-project.md).</span></span>  
  
## <a name="create-a-connection"></a><span data-ttu-id="a13e8-112">接続の作成</span><span class="sxs-lookup"><span data-stu-id="a13e8-112">Create a Connection</span></span>  
  
#### <a name="to-create-a-connection-to-a-the-adventureworksdw2012-database"></a><span data-ttu-id="a13e8-113">AdventureWorksDW2012 データベースへの接続を作成するには</span><span class="sxs-lookup"><span data-stu-id="a13e8-113">To create a connection to a the AdventureWorksDW2012 database</span></span>  
  
1.  <span data-ttu-id="a13e8-114">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]で **[モデル]** メニューをクリックし、 **[データ ソースからのインポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a13e8-114">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], click on the **Model** menu, and then click **Import from Data Source**.</span></span>  
  
     <span data-ttu-id="a13e8-115">テーブルのインポート ウィザードが起動し、その指示に従ってデータ ソースへの接続を設定することができます。</span><span class="sxs-lookup"><span data-stu-id="a13e8-115">This launches the Table Import Wizard which guides you through setting up a connection to a data source.</span></span> <span data-ttu-id="a13e8-116">**[データ ソースからのインポート]** がグレーで表示されている場合は、 **[ソリューション エクスプローラー]** で **Model.bim** をダブルクリックして、モデルをデザイナーで開きます。</span><span class="sxs-lookup"><span data-stu-id="a13e8-116">If **Import from Data Source** is greyed out, double click **Model.bim** in **Solution Explorer** to open the model in the designer.</span></span>  
  
2.  <span data-ttu-id="a13e8-117">**テーブルのインポート ウィザード**の **[リレーショナル データベース]** で **[Microsoft SQL Server]** をクリックし、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a13e8-117">In the **Table Import Wizard**, under **Relational Databases**, click **Microsoft SQL Server**, and then click **Next**.</span></span>  
  
3.  <span data-ttu-id="a13e8-118">[ **Microsoft SQL Server データベースへの接続**] ページで、[接続の表示**名**] に「」と入力 `Adventure Works DB from SQL` します。</span><span class="sxs-lookup"><span data-stu-id="a13e8-118">In the **Connect to a Microsoft SQL Server Database** page, in **Friendly Connection Name**, type `Adventure Works DB from SQL`.</span></span>  
  
4.  <span data-ttu-id="a13e8-119">**[サーバー名]** に、AdventureWorksDW データベースをインストールしたサーバーの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="a13e8-119">In **Server name**, type the name of the server you installed the AdventureWorksDW database.</span></span>  
  
5.  <span data-ttu-id="a13e8-120">**[データベース名]** フィールドで、下矢印をクリックして **[AdventureWorksDW]** を選択し、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a13e8-120">In the **Database name** field, click the down arrow and select **AdventureWorksDW**, and then click **Next**.</span></span>  
  
6.  <span data-ttu-id="a13e8-121">**[権限借用情報]** ページで、データをインポートおよび処理する際、Analysis Services がデータ ソースへの接続のために使用する資格情報を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a13e8-121">In the **Impersonation Information** page, you need to specify the credentials Analysis Services will use to connect to the data source when importing and processing data.</span></span> <span data-ttu-id="a13e8-122">**[特定の Windows ユーザー名とパスワード]** が選択されていることを確認し、 **[ユーザー名]** と **[パスワード]** に Windows のログオン資格情報を入力して、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a13e8-122">Verify **Specific Windows user name and password** is selected, and then in **User Name** and **Password**, enter your Windows logon credentials, and then click **Next**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a13e8-123">Windows のユーザー アカウントとパスワードを使用することで、最も安全なデータ ソース接続方法が提供されます。</span><span class="sxs-lookup"><span data-stu-id="a13e8-123">Using a Windows user account and password provides the most secure method of connecting to a data source.</span></span> <span data-ttu-id="a13e8-124">詳細については、「[権限借用 (SSAS テーブル)](tabular-models/impersonation-ssas-tabular.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a13e8-124">For more information, see [Impersonation &#40;SSAS Tabular&#41;](tabular-models/impersonation-ssas-tabular.md).</span></span>  
  
7.  <span data-ttu-id="a13e8-125">**[データのインポート方法の選択]** ページで、 **[インポートするデータをテーブルとビューの一覧から選択する]** が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="a13e8-125">In the **Choose How to Import the Data** page, verify **Select from a list of tables and views to choose the data to import** is selected.</span></span> <span data-ttu-id="a13e8-126">テーブルとビューの一覧から選択するには、 **[次へ]** をクリックして、ソース データベース内のすべてのソース テーブルの一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="a13e8-126">You want to select from a list of tables and views, so click **Next** to display a list of all the source tables in the source database.</span></span>  
  
8.  <span data-ttu-id="a13e8-127">**[テーブルとビューの選択]** ページで、 **DimCustomer**、 **DimDate**、 **DimGeography**、 **DimProduct**、 **DimProductCategory**、 **DimProductSubcategory**、および **FactInternetSales**の各テーブルのチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="a13e8-127">In the **Select Tables and Views** page, select the check box for the following tables: **DimCustomer**, **DimDate**, **DimGeography**, **DimProduct**, **DimProductCategory**, **DimProductSubcategory**, and **FactInternetSales**.</span></span>  
  
9. <span data-ttu-id="a13e8-128">モデル内のテーブルによりわかりやすい名前を付けましょう。</span><span class="sxs-lookup"><span data-stu-id="a13e8-128">We want to give the tables in the model more easily understood names.</span></span> <span data-ttu-id="a13e8-129">**DimCustomer** の **[表示名]** 列内にあるセルをクリックします。</span><span class="sxs-lookup"><span data-stu-id="a13e8-129">Click on the cell in the **Friendly Name** column for **DimCustomer**.</span></span> <span data-ttu-id="a13e8-130">DimCustomer から "Dim" を削除して、テーブルの名前を変更します。</span><span class="sxs-lookup"><span data-stu-id="a13e8-130">Rename the table by removing "Dim" from DimCustomer.</span></span>  
  
10. <span data-ttu-id="a13e8-131">その他のテーブルの名前を次のように変更します。</span><span class="sxs-lookup"><span data-stu-id="a13e8-131">Rename the other tables:</span></span>  
  
    |<span data-ttu-id="a13e8-132">ソース名</span><span class="sxs-lookup"><span data-stu-id="a13e8-132">Source name</span></span>|<span data-ttu-id="a13e8-133">フレンドリ名</span><span class="sxs-lookup"><span data-stu-id="a13e8-133">Friendly Name</span></span>|  
    |-----------------|-------------------|  
    |<span data-ttu-id="a13e8-134">DimDate</span><span class="sxs-lookup"><span data-stu-id="a13e8-134">DimDate</span></span>|<span data-ttu-id="a13e8-135">Date</span><span class="sxs-lookup"><span data-stu-id="a13e8-135">Date</span></span>|  
    |<span data-ttu-id="a13e8-136">DimGeography</span><span class="sxs-lookup"><span data-stu-id="a13e8-136">DimGeography</span></span>|<span data-ttu-id="a13e8-137">[地理的な場所]</span><span class="sxs-lookup"><span data-stu-id="a13e8-137">Geography</span></span>|  
    |<span data-ttu-id="a13e8-138">DimProduct</span><span class="sxs-lookup"><span data-stu-id="a13e8-138">DimProduct</span></span>|<span data-ttu-id="a13e8-139">Product</span><span class="sxs-lookup"><span data-stu-id="a13e8-139">Product</span></span>|  
    |<span data-ttu-id="a13e8-140">DimProductCategory</span><span class="sxs-lookup"><span data-stu-id="a13e8-140">DimProductCategory</span></span>|<span data-ttu-id="a13e8-141">製品カテゴリ</span><span class="sxs-lookup"><span data-stu-id="a13e8-141">Product Category</span></span>|  
    |<span data-ttu-id="a13e8-142">DimProductSubcategory</span><span class="sxs-lookup"><span data-stu-id="a13e8-142">DimProductSubcategory</span></span>|<span data-ttu-id="a13e8-143">Product Subcategory</span><span class="sxs-lookup"><span data-stu-id="a13e8-143">Product Subcategory</span></span>|  
    |<span data-ttu-id="a13e8-144">FactInternetSales</span><span class="sxs-lookup"><span data-stu-id="a13e8-144">FactInternetSales</span></span>|<span data-ttu-id="a13e8-145">Internet Sales</span><span class="sxs-lookup"><span data-stu-id="a13e8-145">Internet Sales</span></span>|  
  
     <span data-ttu-id="a13e8-146">**[完了]** をクリック **しないでください**。</span><span class="sxs-lookup"><span data-stu-id="a13e8-146">**DO NOT** click **Finish**.</span></span>  
  
 <span data-ttu-id="a13e8-147">データベースに接続し、インポートするテーブルを選択し、テーブルに表示名を付けたので、次のセクション「 [インポート前のテーブル データに対するフィルターの適用](#FilterData)」に進んでください。</span><span class="sxs-lookup"><span data-stu-id="a13e8-147">Now that you have connected to the database, selected the tables to import, and given the tables friendly names, go to the next section, [Filter the Table Data prior to Importing](#FilterData).</span></span>  
  
##  <a name="filter-the-table-data"></a><a name="FilterData"></a><span data-ttu-id="a13e8-148">テーブルデータのフィルター処理</span><span class="sxs-lookup"><span data-stu-id="a13e8-148">Filter the Table Data</span></span>  
 <span data-ttu-id="a13e8-149">データベースからインポートしようとしている DimCustomer テーブルには、元の SQL Server Adventure Works データベースから取得されたデータのサブセットが含まれています。</span><span class="sxs-lookup"><span data-stu-id="a13e8-149">The DimCustomer table that you are importing from the database contains a subset of the data from the original SQL Server Adventure Works database.</span></span> <span data-ttu-id="a13e8-150">必要のない DimCustomer テーブルの一部の列を除外します。</span><span class="sxs-lookup"><span data-stu-id="a13e8-150">You will filter out some of the columns from the DimCustomer table that aren't necessary.</span></span> <span data-ttu-id="a13e8-151">可能な場合は、モデルによって使用されるメモリ内領域を節約するために、使用されないデータを除外します。</span><span class="sxs-lookup"><span data-stu-id="a13e8-151">When possible, you will want to filter out data that will not be used in order to save in-memory space used by the model.</span></span>  
  
#### <a name="to-filter-the-table-data-prior-to-importing"></a><span data-ttu-id="a13e8-152">インポート前のテーブル データにフィルターを適用するには</span><span class="sxs-lookup"><span data-stu-id="a13e8-152">To filter the table data prior to importing</span></span>  
  
1.  <span data-ttu-id="a13e8-153">**Customer** テーブルの行を選択し、**[プレビューとフィルター]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a13e8-153">Select the row for the **Customer** table, and then click **Preview & Filter**.</span></span> <span data-ttu-id="a13e8-154">**[選択したテーブルのプレビュー]** ウィンドウが開き、DimCustomer ソース テーブルのすべての列が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a13e8-154">The **Preview Selected Table** window opens with all the columns in the DimCustomer source table displayed.</span></span>  
  
2.  <span data-ttu-id="a13e8-155">次の列の上部にあるチェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="a13e8-155">Clear the checkbox at the top of the following columns:</span></span>  
  
    |<span data-ttu-id="a13e8-156">Customer</span><span class="sxs-lookup"><span data-stu-id="a13e8-156">Customer</span></span>|  
    |--------------|  
    |<span data-ttu-id="a13e8-157">**SpanishEducation**</span><span class="sxs-lookup"><span data-stu-id="a13e8-157">**SpanishEducation**</span></span>|  
    |<span data-ttu-id="a13e8-158">**FrenchEducation**</span><span class="sxs-lookup"><span data-stu-id="a13e8-158">**FrenchEducation**</span></span>|  
    |<span data-ttu-id="a13e8-159">**SpanishOccupation**</span><span class="sxs-lookup"><span data-stu-id="a13e8-159">**SpanishOccupation**</span></span>|  
    |<span data-ttu-id="a13e8-160">**FrenchOccupation**</span><span class="sxs-lookup"><span data-stu-id="a13e8-160">**FrenchOccupation**</span></span>|  
  
     <span data-ttu-id="a13e8-161">これらの列の値はインターネット売上分析と関連がないので、これらの列をインポートする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="a13e8-161">Since the values for these columns are not relevant to Internet sales analysis, there is no need to import these columns.</span></span> <span data-ttu-id="a13e8-162">不要な列を削除することで、モデルのサイズを減らせます。</span><span class="sxs-lookup"><span data-stu-id="a13e8-162">Eliminating unnecessary columns will make your model smaller.</span></span>  
  
3.  <span data-ttu-id="a13e8-163">他の列がすべてオンになっていることを確認し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a13e8-163">Verify that all other columns are checked, and then click **OK**.</span></span>  
  
     <span data-ttu-id="a13e8-164">"**適用さ**れたフィルター" という単語が**Customer**行の [**フィルターの詳細**列に表示されることに注意してください。そのリンクをクリックすると、適用したフィルターの説明テキストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a13e8-164">Notice the words **Applied filters** are now displayed in the **Filter Details** column in the **Customer** row; if you click on that link you'll see a text description of the filters you just applied.</span></span>  
  
4.  <span data-ttu-id="a13e8-165">各テーブル内の次の列のチェック ボックスをオフにして、残りのテーブルをフィルター処理します。</span><span class="sxs-lookup"><span data-stu-id="a13e8-165">Filter the remaining tables by clearing the checkboxes for the following columns in each table:</span></span>  
  
    |<span data-ttu-id="a13e8-166">Date</span><span class="sxs-lookup"><span data-stu-id="a13e8-166">Date</span></span>|  
    |----------|  
    |<span data-ttu-id="a13e8-167">**DateKey**</span><span class="sxs-lookup"><span data-stu-id="a13e8-167">**DateKey**</span></span>|  
    |<span data-ttu-id="a13e8-168">**SpanishDayNameOfWeek**</span><span class="sxs-lookup"><span data-stu-id="a13e8-168">**SpanishDayNameOfWeek**</span></span>|  
    |<span data-ttu-id="a13e8-169">**FrenchDayNameOfWeek**</span><span class="sxs-lookup"><span data-stu-id="a13e8-169">**FrenchDayNameOfWeek**</span></span>|  
    |<span data-ttu-id="a13e8-170">**SpanishMonthName**</span><span class="sxs-lookup"><span data-stu-id="a13e8-170">**SpanishMonthName**</span></span>|  
    |<span data-ttu-id="a13e8-171">**FrenchMonthName**</span><span class="sxs-lookup"><span data-stu-id="a13e8-171">**FrenchMonthName**</span></span>|  
  
    |<span data-ttu-id="a13e8-172">[地理的な場所]</span><span class="sxs-lookup"><span data-stu-id="a13e8-172">Geography</span></span>|  
    |---------------|  
    |<span data-ttu-id="a13e8-173">**SpanishCountryRegionName**</span><span class="sxs-lookup"><span data-stu-id="a13e8-173">**SpanishCountryRegionName**</span></span>|  
    |<span data-ttu-id="a13e8-174">**FrenchCountryRegionName**</span><span class="sxs-lookup"><span data-stu-id="a13e8-174">**FrenchCountryRegionName**</span></span>|  
    |<span data-ttu-id="a13e8-175">**IpAddressLocator**</span><span class="sxs-lookup"><span data-stu-id="a13e8-175">**IpAddressLocator**</span></span>|  
  
    |<span data-ttu-id="a13e8-176">Product</span><span class="sxs-lookup"><span data-stu-id="a13e8-176">Product</span></span>|  
    |-------------|  
    |<span data-ttu-id="a13e8-177">**SpanishProductName**</span><span class="sxs-lookup"><span data-stu-id="a13e8-177">**SpanishProductName**</span></span>|  
    |<span data-ttu-id="a13e8-178">**FrenchProductName**</span><span class="sxs-lookup"><span data-stu-id="a13e8-178">**FrenchProductName**</span></span>|  
    |<span data-ttu-id="a13e8-179">**FrenchDescription**</span><span class="sxs-lookup"><span data-stu-id="a13e8-179">**FrenchDescription**</span></span>|  
    |<span data-ttu-id="a13e8-180">**ChineseDescription**</span><span class="sxs-lookup"><span data-stu-id="a13e8-180">**ChineseDescription**</span></span>|  
    |<span data-ttu-id="a13e8-181">**ArabicDescription**</span><span class="sxs-lookup"><span data-stu-id="a13e8-181">**ArabicDescription**</span></span>|  
    |<span data-ttu-id="a13e8-182">**HebrewDescription**</span><span class="sxs-lookup"><span data-stu-id="a13e8-182">**HebrewDescription**</span></span>|  
    |<span data-ttu-id="a13e8-183">**ThaiDescription**</span><span class="sxs-lookup"><span data-stu-id="a13e8-183">**ThaiDescription**</span></span>|  
    |<span data-ttu-id="a13e8-184">**GermanDescription**</span><span class="sxs-lookup"><span data-stu-id="a13e8-184">**GermanDescription**</span></span>|  
    |<span data-ttu-id="a13e8-185">**JapaneseDescription**</span><span class="sxs-lookup"><span data-stu-id="a13e8-185">**JapaneseDescription**</span></span>|  
    |<span data-ttu-id="a13e8-186">**TurkishDescription**</span><span class="sxs-lookup"><span data-stu-id="a13e8-186">**TurkishDescription**</span></span>|  
  
    |<span data-ttu-id="a13e8-187">製品カテゴリ</span><span class="sxs-lookup"><span data-stu-id="a13e8-187">Product Category</span></span>|  
    |----------------------|  
    |<span data-ttu-id="a13e8-188">**SpanishProductCategoryName**</span><span class="sxs-lookup"><span data-stu-id="a13e8-188">**SpanishProductCategoryName**</span></span>|  
    |<span data-ttu-id="a13e8-189">**FrenchProductCategoryName**</span><span class="sxs-lookup"><span data-stu-id="a13e8-189">**FrenchProductCategoryName**</span></span>|  
  
    |<span data-ttu-id="a13e8-190">Product Subcategory</span><span class="sxs-lookup"><span data-stu-id="a13e8-190">Product Subcategory</span></span>|  
    |-------------------------|  
    |<span data-ttu-id="a13e8-191">**SpanishProductSubcategoryName**</span><span class="sxs-lookup"><span data-stu-id="a13e8-191">**SpanishProductSubcategoryName**</span></span>|  
    |<span data-ttu-id="a13e8-192">**FrenchProductSubcategoryName**</span><span class="sxs-lookup"><span data-stu-id="a13e8-192">**FrenchProductSubcategoryName**</span></span>|  
  
    |<span data-ttu-id="a13e8-193">Internet Sales</span><span class="sxs-lookup"><span data-stu-id="a13e8-193">Internet Sales</span></span>|  
    |--------------------|  
    |<span data-ttu-id="a13e8-194">**OrderDateKey**</span><span class="sxs-lookup"><span data-stu-id="a13e8-194">**OrderDateKey**</span></span>|  
    |<span data-ttu-id="a13e8-195">**DueDateKey**</span><span class="sxs-lookup"><span data-stu-id="a13e8-195">**DueDateKey**</span></span>|  
    |<span data-ttu-id="a13e8-196">**ShipDateKey**</span><span class="sxs-lookup"><span data-stu-id="a13e8-196">**ShipDateKey**</span></span>|  
  
 <span data-ttu-id="a13e8-197">不要なデータをプレビューして除外したので、データをインポートする準備が整いました。</span><span class="sxs-lookup"><span data-stu-id="a13e8-197">Now that you have previewed and filtered out unnecessary data, you can import the data.</span></span> <span data-ttu-id="a13e8-198">次のセクション「 **選択したテーブルと列のデータのインポート**」に進んでください。</span><span class="sxs-lookup"><span data-stu-id="a13e8-198">Go to the next section **Import the Selected Tables and Column Data**.</span></span>  
  
##  <a name="import-the-selected-tables-and-column-data"></a><a name="Import"></a><span data-ttu-id="a13e8-199">選択したテーブルと列のデータをインポートします</span><span class="sxs-lookup"><span data-stu-id="a13e8-199">Import the Selected Tables and Column Data</span></span>  
 <span data-ttu-id="a13e8-200">選択したデータをインポートします。</span><span class="sxs-lookup"><span data-stu-id="a13e8-200">You can now import the selected data.</span></span> <span data-ttu-id="a13e8-201">ウィザードでは、テーブル データと、各テーブル間のリレーションシップがインポートされます。</span><span class="sxs-lookup"><span data-stu-id="a13e8-201">The wizard imports the table data along with any relationships between tables.</span></span> <span data-ttu-id="a13e8-202">指定した表示名を使用して、モデル内に新しいテーブルと列が作成されます。除外したデータはインポートされません。</span><span class="sxs-lookup"><span data-stu-id="a13e8-202">New tables and columns are created in the model using the friendly names you specified, and data that you filtered out will not be imported.</span></span>  
  
#### <a name="to-import-the-selected-tables-and-column-data"></a><span data-ttu-id="a13e8-203">選択したテーブルと列のデータをインポートする</span><span class="sxs-lookup"><span data-stu-id="a13e8-203">To import the selected tables and column data</span></span>  
  
1.  <span data-ttu-id="a13e8-204">選択内容を確認します｡</span><span class="sxs-lookup"><span data-stu-id="a13e8-204">Review your selections.</span></span> <span data-ttu-id="a13e8-205">問題がなければ **[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a13e8-205">If everything looks OK, click **Finish**.</span></span>  
  
     <span data-ttu-id="a13e8-206">データのインポート中、フェッチされた行数が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a13e8-206">While importing the data, the wizard displays how many rows have been fetched.</span></span> <span data-ttu-id="a13e8-207">すべてのデータがインポートされると、成功を示すメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a13e8-207">When all the data has been imported, a message indicating success is displayed.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="a13e8-208">インポートしたテーブル間に自動的に作成されたリレーションシップを表示するために、 **[データ準備]** 行で、 **[詳細]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a13e8-208">To see the relationships that were automatically created between the imported tables, on the **Data preparation** row, click **Details**.</span></span>  
  
2.  <span data-ttu-id="a13e8-209">**[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a13e8-209">Click **Close**.</span></span>  
  
     <span data-ttu-id="a13e8-210">ウィザードが閉じ、モデル デザイナーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a13e8-210">The wizard closes and the model designer is visible.</span></span> <span data-ttu-id="a13e8-211">各テーブルが新しいタブとしてモデル デザイナーに追加されています。</span><span class="sxs-lookup"><span data-stu-id="a13e8-211">Each table has been added as a new tab in the model designer.</span></span>  
  
## <a name="save-the-model-project"></a><span data-ttu-id="a13e8-212">モデル プロジェクトの保存</span><span class="sxs-lookup"><span data-stu-id="a13e8-212">Save the Model Project</span></span>  
 <span data-ttu-id="a13e8-213">モデル プロジェクトは頻繁に保存することが重要です。</span><span class="sxs-lookup"><span data-stu-id="a13e8-213">It is important to frequently save your model project.</span></span>  
  
#### <a name="to-save-the-model-project"></a><span data-ttu-id="a13e8-214">モデル プロジェクトを保存する</span><span class="sxs-lookup"><span data-stu-id="a13e8-214">To save the model project</span></span>  
  
-   <span data-ttu-id="a13e8-215">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]で、 **[ファイル]** メニューをクリックし、 **[すべてを保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a13e8-215">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], click on the **File** menu, and then click **Save All**.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="a13e8-216">次の手順</span><span class="sxs-lookup"><span data-stu-id="a13e8-216">Next Step</span></span>  
 <span data-ttu-id="a13e8-217">このチュートリアルを続行するには、次のレッスン「 [レッスン 3: 列名の変更](rename-columns.md)」に進んでください。</span><span class="sxs-lookup"><span data-stu-id="a13e8-217">To continue this tutorial, go to the next lesson: [Lesson 3: Rename Columns](rename-columns.md).</span></span>  
  
  
