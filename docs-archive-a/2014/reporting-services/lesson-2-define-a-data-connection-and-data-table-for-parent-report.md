---
title: 'レッスン 2: 親レポートのデータ接続とデータ テーブルを定義する | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: f02dee0c-85ad-45d4-b707-10e9e8541db9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 045ff576061bf12d163668cb9a57651e591768a4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632291"
---
# <a name="lesson-2-define-a-data-connection-and-data-table-for-parent-report"></a><span data-ttu-id="2dc09-102">レッスン 2: 親レポートのデータ接続とデータ テーブルを定義する</span><span class="sxs-lookup"><span data-stu-id="2dc09-102">Lesson 2: Define a Data Connection and Data Table for Parent Report</span></span>
  <span data-ttu-id="2dc09-103">Visual C# 用の ASP.NET Web サイト テンプレートを使用して新しい Web サイト プロジェクトを作成した後は、親レポートのデータ接続とデータ テーブルを作成します。</span><span class="sxs-lookup"><span data-stu-id="2dc09-103">After you create a new website project using the ASP.NET website template for Visual C#, your next step is to create a data connection and a data table for the parent report.</span></span> <span data-ttu-id="2dc09-104">このチュートリアルでは、データ接続先として AdventureWorks2008 データベースを使用しますが、</span><span class="sxs-lookup"><span data-stu-id="2dc09-104">In this tutorial the data connection is to the AdventureWorks2008 database.</span></span> <span data-ttu-id="2dc09-105">AdventureWorks2012 データベースに接続することもできます。</span><span class="sxs-lookup"><span data-stu-id="2dc09-105">You also have the option of connecting to the AdventureWorks2012 database.</span></span>  
  
### <a name="to-define-a-data-connection-and-data-table-by-adding-a-dataset-for-parent-report"></a><span data-ttu-id="2dc09-106">DataSet を追加してデータ接続とデータ テーブルを定義するには (親レポート用)</span><span class="sxs-lookup"><span data-stu-id="2dc09-106">To define a data connection and Data Table by adding a DataSet (for parent report)</span></span>  
  
1.  <span data-ttu-id="2dc09-107">[ **Web サイト** ] メニューの [ **新しい項目の追加**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="2dc09-107">On the **Website** menu, select **Add New Item**.</span></span>  
  
2.  <span data-ttu-id="2dc09-108">[**新しい項目の追加**] ダイアログボックスで、[**データセット**] を選択し、[**追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2dc09-108">In the **Add New Item** dialog box, select **DataSet** and click **Add**.</span></span> <span data-ttu-id="2dc09-109">メッセージが表示されたら、 **[はい]** をクリックして**App_Code**フォルダーに項目を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2dc09-109">When prompted you should add the item to the **App_Code** folder by clicking **Yes**.</span></span>  
  
     <span data-ttu-id="2dc09-110">これにより、 **DataSet1.xsd** という新しい XSD ファイルがプロジェクトに追加され、データセット デザイナーが開きます。</span><span class="sxs-lookup"><span data-stu-id="2dc09-110">This adds a new XSD file **DataSet1.xsd** to the project and opens the DataSet Designer.</span></span>  
  
3.  <span data-ttu-id="2dc09-111">[ツールボックス] ウィンドウから**[TableAdapter](https://msdn.microsoft.com/library/bz9tthwx\(v=vs.100\).aspx)** コントロールをデザイン画面にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="2dc09-111">From the Toolbox window, drag a **[TableAdapter](https://msdn.microsoft.com/library/bz9tthwx\(v=vs.100\).aspx)** control to the design surface.</span></span> <span data-ttu-id="2dc09-112">これにより、 **TableAdapter** の構成ウィザードが起動します。</span><span class="sxs-lookup"><span data-stu-id="2dc09-112">This launches the **TableAdapter** Configuration Wizard.</span></span>  
  
4.  <span data-ttu-id="2dc09-113">[**データ接続の選択**] ページで、[**新しい接続**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2dc09-113">On the **Choose Your Data Connection** page, click **New Connection**.</span></span>  
  
5.  <span data-ttu-id="2dc09-114">Visual Studio で初めてデータソースを作成する場合は、 **[データソースの選択**] ページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2dc09-114">If this is the first time you've created a data source in Visual Studio, you will see the **Choose Data Source** page.</span></span> <span data-ttu-id="2dc09-115">**[データ ソース]** ボックスで、 **[Microsoft SQL Server]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="2dc09-115">In the **Data Source** box, select **Microsoft SQL Server**.</span></span>  
  
6.  <span data-ttu-id="2dc09-116">[ **接続の追加** ] ダイアログ ボックスで、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="2dc09-116">In the **Add Connection** dialog box, perform the following steps:</span></span>  
  
    1.  <span data-ttu-id="2dc09-117">[**サーバー名**] ボックスに、 **AdventureWorks2008**データベースが配置されているサーバーを入力します。</span><span class="sxs-lookup"><span data-stu-id="2dc09-117">In the **Server name** box, enter the server where the **AdventureWorks2008** database is located.</span></span>  
  
         <span data-ttu-id="2dc09-118">既定の SQL Server Express インスタンスは **(local)\sqlexpress**です。</span><span class="sxs-lookup"><span data-stu-id="2dc09-118">The default SQL Server Express instance is **(local)\sqlexpress**.</span></span>  
  
    2.  <span data-ttu-id="2dc09-119">[ **サーバーへのログオン** ] セクションで、データへのアクセスを提供するオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="2dc09-119">In the **Log on to the server** section, select the option that provides you access to the data.</span></span> <span data-ttu-id="2dc09-120">既定は **[Windows 認証を使用する]** です。</span><span class="sxs-lookup"><span data-stu-id="2dc09-120">**Use Windows Authentication** is the default.</span></span>  
  
    3.  <span data-ttu-id="2dc09-121">[**データベース名の選択または入力**] ドロップダウンリストで、[ **AdventureWorks2008**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2dc09-121">From the **Select or enter a database name** drop-down list, click **AdventureWorks2008**.</span></span>  
  
    4.  <span data-ttu-id="2dc09-122">[**OK**] をクリックし、[**次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2dc09-122">Click **OK**, and then click **Next**.</span></span>  
  
7.  <span data-ttu-id="2dc09-123">手順 6. (b) で **[SQL Server 認証を使用する]** を選択した場合は、機密データを文字列に含めるか、またはその情報をアプリケーション コードで設定するかどうかを指定するオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="2dc09-123">If you selected **Use SQL Server Authentication** in the Step 6 (b), select the option whether to include the sensitive data in the string or set the information in your application code.</span></span>  
  
8.  <span data-ttu-id="2dc09-124">[**アプリケーション構成ファイルに接続文字列を保存**] ページで、接続文字列の名前を入力するか、既定の**AdventureWorks2008ConnectionString**をそのまま使用します。</span><span class="sxs-lookup"><span data-stu-id="2dc09-124">On the **Save the Connection String to the Application Configuration File** page, type in the name for the connection string or accept the default **AdventureWorks2008ConnectionString**.</span></span> <span data-ttu-id="2dc09-125">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2dc09-125">Click **Next**.</span></span>  
  
9. <span data-ttu-id="2dc09-126">[**コマンドの種類の選択**] ページで、[ **SQL ステートメントを使用する**] を選択し、[**次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2dc09-126">On the **Choose a Command Type** page, select **Use SQL Statements**, and then click **Next**.</span></span>  
  
10. <span data-ttu-id="2dc09-127">[ **Sql ステートメントの入力**] ページで、 **AdventureWorks2008**データベースからデータを取得するための次の transact-sql クエリを入力し、[**次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2dc09-127">On the **Enter a SQL Statement** page, enter the following Transact-SQL query to retrieve data from the **AdventureWorks2008** database, and then click **Next**.</span></span>  
  
    ```  
    SELECT ProductID, Name, ProductNumber, SafetyStockLevel, ReorderPoint FROM  Production.Product Order By ProductID  
    ```  
  
     <span data-ttu-id="2dc09-128">[**クエリビルダー**] をクリックしてクエリを作成し、[**クエリの実行**] をクリックしてクエリを確認することもできます。</span><span class="sxs-lookup"><span data-stu-id="2dc09-128">You can also create the query by clicking **Query Builder**, and then verify the query by clicking **Execute Query**.</span></span> <span data-ttu-id="2dc09-129">クエリを実行したときに期待したデータが返されない場合は、以前のバージョンの AdventureWorks を使用している可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2dc09-129">If the query does not return the expected data, you might be using an earlier version of AdventureWorks.</span></span> <span data-ttu-id="2dc09-130">AdventureWorks の**AdventureWorks2008**バージョンのインストールの詳細については、「[チュートリアル: Adventureworks データベースのインストール](https://msdn.microsoft.com/library/aa992075\(v=vs.100\).aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2dc09-130">For more information about installing the **AdventureWorks2008** version of AdventureWorks, see [Walkthrough: Installing the AdventureWorks Database](https://msdn.microsoft.com/library/aa992075\(v=vs.100\).aspx).</span></span>  
  
11. <span data-ttu-id="2dc09-131">[**生成するメソッドの選択**] ページで、[**更新を直接データベースに送信するためのメソッドを作成する (GenerateDBDirectMethods)**] チェックボックスをオフにして、[**完了**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2dc09-131">On the **Choose Methods to Generate** page, be sure to uncheck **Create methods to send updates directly to the database (GenerateDBDirectMethods)**, and then click **Finish**.</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="2dc09-132">必ずこのチェック ボックスをオフにしてください。</span><span class="sxs-lookup"><span data-stu-id="2dc09-132">Be sure to uncheck Create</span></span>  
  
     <span data-ttu-id="2dc09-133">これで、レポートのデータ ソースとしての ADO.NET DataTable オブジェクトの構成が完了しました。</span><span class="sxs-lookup"><span data-stu-id="2dc09-133">You have now completed configuring the ADO.NET DataTable object as the data source for your report.</span></span> <span data-ttu-id="2dc09-134">Visual Studio の [データセット デザイナー] ページに、追加した DataTable オブジェクトにクエリで指定した列が表示されます。</span><span class="sxs-lookup"><span data-stu-id="2dc09-134">On the DataSet Designer page in Visual Studio, you should see the DataTable object you added, listing the columns specified in the query.</span></span> <span data-ttu-id="2dc09-135">DataSet1 には、クエリに基づいて Product テーブルのデータが含まれています。</span><span class="sxs-lookup"><span data-stu-id="2dc09-135">DataSet1 contains the data from the Product table, based on the query.</span></span>  
  
12. <span data-ttu-id="2dc09-136">ファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="2dc09-136">Save the file.</span></span>  
  
13. <span data-ttu-id="2dc09-137">データをプレビューするには、[**データ**] メニューの [**データのプレビュー** ] をクリックし、[**プレビュー**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2dc09-137">To preview the data, click **Preview Data** on the **Data** menu, and then click **Preview**.</span></span>  
  
## <a name="next-task"></a><span data-ttu-id="2dc09-138">次の作業</span><span class="sxs-lookup"><span data-stu-id="2dc09-138">Next Task</span></span>  
 <span data-ttu-id="2dc09-139">これで、親レポートのデータ接続とデータ テーブルを作成できました。</span><span class="sxs-lookup"><span data-stu-id="2dc09-139">You have successfully created a data connection and a data table for the parent report.</span></span> <span data-ttu-id="2dc09-140">次は、レポート ウィザードを使用して親レポートを設計します。</span><span class="sxs-lookup"><span data-stu-id="2dc09-140">Next, you will design the parent report using the Report Wizard.</span></span>  
  
  
