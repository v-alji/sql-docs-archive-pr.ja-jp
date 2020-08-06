---
title: 'レッスン 4: 子レポートのデータ接続とデータ テーブルを定義する | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: a6aa2c56-227c-43c5-a28e-c7104131ac5e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6d9144d960ad933afa65f9d4483e96b5f732d944
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632970"
---
# <a name="lesson-4-define-a-data-connection-and-data-table-for-child-report"></a><span data-ttu-id="d68af-102">レッスン 4: 子レポートのデータ接続とデータ テーブルを定義する</span><span class="sxs-lookup"><span data-stu-id="d68af-102">Lesson 4: Define a Data Connection and Data Table for Child Report</span></span>
  <span data-ttu-id="d68af-103">親レポートを設計した後は、子レポートのデータ接続とデータ テーブルを作成します。</span><span class="sxs-lookup"><span data-stu-id="d68af-103">After you design the parent report, you next step is to create a data connection and a data table for the child report.</span></span> <span data-ttu-id="d68af-104">このチュートリアルでは、データ接続先として AdventureWorks2008 データベースを使用しますが、</span><span class="sxs-lookup"><span data-stu-id="d68af-104">In this tutorial the data connection is to the AdventureWorks2008 database.</span></span> <span data-ttu-id="d68af-105">AdventureWorks2012 データベースに接続することもできます。</span><span class="sxs-lookup"><span data-stu-id="d68af-105">You also have the option of connecting to the AdventureWorks2012 database.</span></span>  
  
### <a name="to-define-a-data-connection-and-datatable-by-adding-a-dataset-for-child-report"></a><span data-ttu-id="d68af-106">DataSet を追加してデータ接続と DataTable を定義するには (子レポート用)</span><span class="sxs-lookup"><span data-stu-id="d68af-106">To define a data connection and DataTable by adding a DataSet (for child report)</span></span>  
  
1.  <span data-ttu-id="d68af-107">[ **Web サイト**] メニューの [**新しい項目の追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d68af-107">On the **Website** menu, click **Add New Item**.</span></span>  
  
2.  <span data-ttu-id="d68af-108">[**新しい項目の追加**] ダイアログボックスで、[**データセット**] をクリックし、[**追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d68af-108">In the **Add New Item** dialog box, click **DataSet** and then click **Add**.</span></span> <span data-ttu-id="d68af-109">メッセージが表示されたら、 **[はい]** をクリックして**App_Code**フォルダーに項目を追加します。</span><span class="sxs-lookup"><span data-stu-id="d68af-109">When prompted, you should add the item to the **App_Code** folder by clicking **Yes**.</span></span>  
  
     <span data-ttu-id="d68af-110">これにより、 **DataSet2.xsd** という新しい XSD ファイルがプロジェクトに追加され、データセット デザイナーが開きます。</span><span class="sxs-lookup"><span data-stu-id="d68af-110">This adds a new XSD file **DataSet2.xsd** to the project and opens the DataSet Designer.</span></span>  
  
3.  <span data-ttu-id="d68af-111">[ツールボックス] ウィンドウから **TableAdapter** コントロールをデザイン画面にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="d68af-111">From the Toolbox window, drag a **TableAdapter** control to the design surface.</span></span> <span data-ttu-id="d68af-112">これにより、 **TableAdapter** の構成ウィザードが起動します。</span><span class="sxs-lookup"><span data-stu-id="d68af-112">This launches the **TableAdapter** Configuration Wizard.</span></span>  
  
4.  <span data-ttu-id="d68af-113">[**データ接続の選択**] ページで、[**新しい接続**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d68af-113">On the **Choose Your Data Connection** page, click **New Connection**.</span></span>  
  
5.  <span data-ttu-id="d68af-114">[ **接続の追加** ] ダイアログ ボックスで、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="d68af-114">In the **Add Connection** dialog box, perform the following steps:</span></span>  
  
    1.  <span data-ttu-id="d68af-115">[**サーバー名**] ボックスに、 **AdventureWorks2008**データベースが配置されているサーバーを入力します。</span><span class="sxs-lookup"><span data-stu-id="d68af-115">In the **Server name** box, enter the server where the **AdventureWorks2008** database is located.</span></span>  
  
         <span data-ttu-id="d68af-116">既定の SQL Server Express インスタンスは **(local)\sqlexpress**です。</span><span class="sxs-lookup"><span data-stu-id="d68af-116">The default SQL Server Express instance is **(local)\sqlexpress**.</span></span>  
  
    2.  <span data-ttu-id="d68af-117">[ **サーバーへのログオン** ] セクションで、データへのアクセスを提供するオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="d68af-117">In the **Log on to the server** section, select the option that provides you access to the data.</span></span> <span data-ttu-id="d68af-118">既定は **[Windows 認証を使用する]** です。</span><span class="sxs-lookup"><span data-stu-id="d68af-118">**Use Windows Authentication** is the default.</span></span>  
  
    3.  <span data-ttu-id="d68af-119">[**データベース名の選択または入力**] ドロップダウンリストで、[ **AdventureWorks2008**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d68af-119">From the **Select or enter a database name** drop-down list, click **AdventureWorks2008**.</span></span>  
  
    4.  <span data-ttu-id="d68af-120">[**OK**] をクリックし、[**次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d68af-120">Click **OK**, and then click **Next**.</span></span>  
  
6.  <span data-ttu-id="d68af-121">手順 5. (b) で [ **SQL Server 認証を使用する** ] を選択した場合は、機密データを文字列に含めるか、またはその情報をアプリケーション コードで設定するかどうかを指定するオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="d68af-121">If you selected **Use SQL Server Authentication** in Step 5 (b), select the option whether to include the sensitive data in the string or set the information in your application code.</span></span>  
  
7.  <span data-ttu-id="d68af-122">[**アプリケーション構成ファイルに接続文字列を保存**] ページで、接続文字列の名前を入力するか、既定の**AdventureWorks2008ConnectionString**をそのまま使用します。</span><span class="sxs-lookup"><span data-stu-id="d68af-122">On the **Save the Connection String to the Application Configuration File** page, type in the name for the connection string or accept the default **AdventureWorks2008ConnectionString**.</span></span> <span data-ttu-id="d68af-123">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d68af-123">Click **Next**.</span></span>  
  
8.  <span data-ttu-id="d68af-124">[**コマンドの種類の選択**] ページで、[ **SQL ステートメントを使用する**] を選択し、[**次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d68af-124">On the **Choose a Command Type** page, select **Use SQL Statements**, and then click **Next**.</span></span>  
  
9. <span data-ttu-id="d68af-125">[ **Sql ステートメントの入力**] ページで、 **AdventureWorks2008**データベースからデータを取得するための次の transact-sql クエリを入力し、[**次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d68af-125">On the **Enter a SQL Statement** page, enter the following Transact-SQL query to retrieve data from the **AdventureWorks2008** database, and then click **Next**.</span></span>  
  
    ```  
    SELECT PurchaseOrderID, PurchaseOrderDetailID, OrderQty, ProductID, ReceivedQty, RejectedQty, StockedQty FROM Purchasing.PurchaseOrderDetail  
    ```  
  
     <span data-ttu-id="d68af-126">また、[**クエリビルダー**] をクリックしてクエリを作成し、[クエリの**実行**] ボタンをクリックしてクエリを確認することもできます。</span><span class="sxs-lookup"><span data-stu-id="d68af-126">You can also create the query by clicking **Query Builder**, and then verify the query by clicking **Execute Query** button.</span></span> <span data-ttu-id="d68af-127">クエリを実行したときに期待したデータが返されない場合は、以前のバージョンの AdventureWorks を使用している可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d68af-127">If the query does not return the expected data, you might be using an earlier version of AdventureWorks.</span></span> <span data-ttu-id="d68af-128">AdventureWorks の**AdventureWorks2008**バージョンのインストールの詳細については、「[チュートリアル: Adventureworks データベースのインストール](https://msdn.microsoft.com/library/aa992075\(v=vs.100\).aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d68af-128">For more information about installing the **AdventureWorks2008** version of AdventureWorks, see [Walkthrough: Installing the AdventureWorks Database](https://msdn.microsoft.com/library/aa992075\(v=vs.100\).aspx).</span></span>  
  
10. <span data-ttu-id="d68af-129">[**生成するメソッドの選択**] ページで、[**更新を直接データベースに送信するためのメソッドを作成する (GenerateDBDirectMethods)**] チェックボックスをオフにし、[**完了**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d68af-129">On the **Choose Methods to Generate** page, uncheck **Create methods to send updates directly to the database (GenerateDBDirectMethods)**, and then click **Finish**.</span></span>  
  
     <span data-ttu-id="d68af-130">これで、レポートのデータソースとしての ADO.NET [DataTable](https://msdn.microsoft.com/library/system.data.datatable\(v=vs.100\).aspx)の構成が完了しました。</span><span class="sxs-lookup"><span data-stu-id="d68af-130">You have now completed configuring the ADO.NET [DataTable](https://msdn.microsoft.com/library/system.data.datatable\(v=vs.100\).aspx) as data source for your report.</span></span> <span data-ttu-id="d68af-131">Visual Studio の [データセット デザイナー] ページに、追加した **DataTable** にクエリで指定した列が表示されます。</span><span class="sxs-lookup"><span data-stu-id="d68af-131">On the DataSet Designer page in Visual Studio, you should see the **DataTable** you added, listing the columns specified in the query.</span></span> <span data-ttu-id="d68af-132">DataSet2 には、クエリに基づいて PurhcaseOrderDetail テーブルのデータが含まれています。</span><span class="sxs-lookup"><span data-stu-id="d68af-132">DataSet2 contains the data from the PurhcaseOrderDetail table, based on the query.</span></span>  
  
11. <span data-ttu-id="d68af-133">ファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="d68af-133">Save the file.</span></span>  
  
12. <span data-ttu-id="d68af-134">データをプレビューするには、[**データ**] メニューの [**データのプレビュー** ] をクリックし、[**プレビュー**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d68af-134">To preview the data, click **Preview Data** on the **Data** menu, and then click **Preview**.</span></span>  
  
## <a name="next-task"></a><span data-ttu-id="d68af-135">次の作業</span><span class="sxs-lookup"><span data-stu-id="d68af-135">Next Task</span></span>  
 <span data-ttu-id="d68af-136">これで、子レポートのデータ接続とデータ テーブルを作成できました。</span><span class="sxs-lookup"><span data-stu-id="d68af-136">You have successfully created a data connection and data table for the child report.</span></span> <span data-ttu-id="d68af-137">次は、レポート ウィザードを使用して子レポートを設計します。</span><span class="sxs-lookup"><span data-stu-id="d68af-137">Next, you will design the child report using the Report Wizard.</span></span>  
  
  
