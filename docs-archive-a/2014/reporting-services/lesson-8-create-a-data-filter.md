---
title: 'レッスン 8: データ フィルターを作成する | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 19ccbdba-e3da-40a4-b652-32c628cf32e5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9c11d4cf83619e53cd7e8f00091c66cc8e50ad76
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632962"
---
# <a name="lesson-8-create-a-data-filter"></a><span data-ttu-id="2b191-102">レッスン 8: データ フィルターを作成する</span><span class="sxs-lookup"><span data-stu-id="2b191-102">Lesson 8: Create a Data Filter</span></span>
  <span data-ttu-id="2b191-103">親レポートにドリルスルー アクションを追加した後は、子レポート用に定義したデータ テーブル用のデータ フィルターを作成します。</span><span class="sxs-lookup"><span data-stu-id="2b191-103">After you add a drillthrough action on the parent report, your next step is to create a data filter for the data table that you defined for the child report.</span></span>  
  
 <span data-ttu-id="2b191-104">詳細レポートに対しては、テーブルベースのフィルター **または** クエリ フィルターを作成できます。</span><span class="sxs-lookup"><span data-stu-id="2b191-104">You can create a table-based filter **or** a query filter for the drillthrough report.</span></span> <span data-ttu-id="2b191-105">このレッスンでは、両方のオプションの手順を説明します。</span><span class="sxs-lookup"><span data-stu-id="2b191-105">This lesson provides instructions for both options.</span></span>  
  
## <a name="table-based-filter"></a><span data-ttu-id="2b191-106">テーブルベースのフィルター</span><span class="sxs-lookup"><span data-stu-id="2b191-106">Table-Based Filter</span></span>  
 <span data-ttu-id="2b191-107">テーブルベースのフィルターを実装するには、次の操作を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2b191-107">You need to complete the following tasks to implement a table-based filter.</span></span>  
  
-   <span data-ttu-id="2b191-108">子レポートの Tablix にフィルター式を追加します。</span><span class="sxs-lookup"><span data-stu-id="2b191-108">Add a filter expression to the tablix in the child report.</span></span>  
  
-   <span data-ttu-id="2b191-109">`PurchaseOrderDetail` テーブルからフィルター選択されていないデータを選択する関数を作成します。</span><span class="sxs-lookup"><span data-stu-id="2b191-109">Create a function that selects unfiltered data from the `PurchaseOrderDetail` table.</span></span>  
  
-   <span data-ttu-id="2b191-110">子レポートに `PurchaseOrderDetail` DataTable をバインドするイベント ハンドラーを追加します。</span><span class="sxs-lookup"><span data-stu-id="2b191-110">Add an event handler that binds the `PurchaseOrderDetail` DataTable to the child report.</span></span>  
  
#### <a name="to-add-a-filter-expression-to-the-tablix-in-the-child-report"></a><span data-ttu-id="2b191-111">子レポートの Tablix にフィルター式を追加するには</span><span class="sxs-lookup"><span data-stu-id="2b191-111">To add a filter expression to the tablix in the child report</span></span>  
  
1.  <span data-ttu-id="2b191-112">子レポートを開きます。</span><span class="sxs-lookup"><span data-stu-id="2b191-112">Open the child report.</span></span>  
  
2.  <span data-ttu-id="2b191-113">Tablix の列見出しを選択し、列見出しの上に表示されている灰色のセルを右クリックして、[ **tablix のプロパティ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2b191-113">Select a column heading in the tablix, right-click the gray cell that appears above the column heading, and then click **Tablix Properties**.</span></span>  
  
3.  <span data-ttu-id="2b191-114">[**フィルター** ] ページをクリックし、[**追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2b191-114">Click on the **Filters** page, and then click **Add**.</span></span>  
  
4.  <span data-ttu-id="2b191-115">[**式**] フィールドで、 `ProductID` ドロップダウンリストからをクリックします。</span><span class="sxs-lookup"><span data-stu-id="2b191-115">In the **Expression** filed, click `ProductID` from the drop-down list.</span></span> <span data-ttu-id="2b191-116">これは、フィルターを適用する列です。</span><span class="sxs-lookup"><span data-stu-id="2b191-116">This is the column to which you apply the filter.</span></span>  
  
5.  <span data-ttu-id="2b191-117">[ **=** **演算子**] ボックスの一覧で、等号 () 演算子をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2b191-117">Click the equal (**=**) operator in the **Operator** drop-down list.</span></span>  
  
6.  <span data-ttu-id="2b191-118">[**値**] フィールドの横にある式ボタンをクリックし、[**カテゴリ**] 領域の [**パラメーター** ] をクリックして、[ `productid` **値**] 領域内をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="2b191-118">Click the expression button next to the **Value** field, click **Parameters** in the **Category** area, and then double-click `productid` in the **Values** area.</span></span> <span data-ttu-id="2b191-119">**[式の設定: 値]** フィールドに、 **=Parameters!productid.Value**のような式が表示されます。</span><span class="sxs-lookup"><span data-stu-id="2b191-119">The **Set expression for: Value** field should now contain expression similar to **=Parameters!productid.Value**.</span></span>  
  
7.  <span data-ttu-id="2b191-120">[ **Ok] を**クリックし、[ **Tablix のプロパティ**] ダイアログボックスでもう一度 [ **ok]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2b191-120">Click **OK,** and **OK** again in the **Tablix Properties** dialog box.</span></span>  
  
8.  <span data-ttu-id="2b191-121">.rdlc ファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="2b191-121">Save the .rdlc file.</span></span>  
  
#### <a name="to-create-a-function-that-selects-unfiltered-data-from-the-purchaseordedetail-table"></a><span data-ttu-id="2b191-122">PurchaseOrderDetail テーブルからフィルター選択されていないデータを選択する関数を作成するには</span><span class="sxs-lookup"><span data-stu-id="2b191-122">To create a function that selects unfiltered data from the PurchaseOrdeDetail table</span></span>  
  
1.  <span data-ttu-id="2b191-123">ソリューション エクスプローラーで、Default.aspx を展開し、Default.aspx.cs をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="2b191-123">In Solution Explorer, expand Default.aspx, and then double click Default.aspx.cs.</span></span>  
  
2.  <span data-ttu-id="2b191-124">Integer 型のパラメーターを受け取り、オブジェクトを返す新しい関数を作成し、次のようにし `productid` `datatable` ます。</span><span class="sxs-lookup"><span data-stu-id="2b191-124">Create a new function that accepts a parameter, `productid`, of type Integer and returns a `datatable` object, and does the following.</span></span>  
  
    1.  <span data-ttu-id="2b191-125">「 `DataSet2` [レッスン 4: 子レポートのデータ接続とデータテーブルを定義する](lesson-4-define-a-data-connection-and-data-table-for-child-report.md)」の手順2で作成したデータセットのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="2b191-125">Creates an instance of the dataset, `DataSet2`, which was created in Step 2 of [Lesson 4: Define a Data Connection and Data Table for Child Report](lesson-4-define-a-data-connection-and-data-table-for-child-report.md).</span></span>  
  
    2.  <span data-ttu-id="2b191-126">SqlServer データベースへの接続を作成し、 **「レッスン 4: 子レポートのデータ接続とデータ テーブルを定義する」** で定義されたクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="2b191-126">Create a connection to the SqlServer database to execute the query defined in **Lesson 4: Define a Data Connection and DataTable for Child Report**.</span></span>  
  
    3.  <span data-ttu-id="2b191-127">クエリにより、フィルター選択されていないデータが返されます。</span><span class="sxs-lookup"><span data-stu-id="2b191-127">The query will return unfiltered data.</span></span>  
  
    4.  <span data-ttu-id="2b191-128">クエリを実行して、フィルター選択されていないデータを DataSet インスタンスに入力します。</span><span class="sxs-lookup"><span data-stu-id="2b191-128">Fill the DataSet instance with the unfiltered data by executing the query.</span></span>  
  
    5.  <span data-ttu-id="2b191-129">`PurchaseOrderDetail` DataTable を返します。</span><span class="sxs-lookup"><span data-stu-id="2b191-129">Return the `PurchaseOrderDetail` DataTable.</span></span>  
  
         <span data-ttu-id="2b191-130">関数は次のようになります (これは単なる参考です。</span><span class="sxs-lookup"><span data-stu-id="2b191-130">The function will look similar to the one below, (This is just for your reference.</span></span> <span data-ttu-id="2b191-131">任意のパターンに従って、子レポートに必要なデータをフェッチできます)。</span><span class="sxs-lookup"><span data-stu-id="2b191-131">You can follow any pattern that you want, to fetch the necessary data for child report).</span></span>  
  
        ```  
        /// <summary>  
            /// Function to query PurchaseOrderDetail table, fetch the  
            /// unfiltered data and bind it with the Child report  
            /// </summary>  
            /// <returns>A dataTable of type PurchaseOrderDetail</returns>  
            private DataTable GetPurchaseOrderDetail()  
            {  
                try  
                {  
                    //Create the instance for the typed dataset, DataSet2 which will   
                    //hold the [PurchaseOrderDetail] table details.  
                    //The dataset was created as part of the tutorial in Step 4.  
                    DataSet2 ds = new DataSet2();  
  
                    //Create a SQL Connection to the AdventureWorks2008 database using Windows Authentication.  
                    using (SqlConnection sqlconn = new SqlConnection("Data Source=.;Initial Catalog=Adventureworks;Integrated Security=SSPI"))  
                    {  
                        //Building the dynamic query with the parameter ProductID.  
                        SqlDataAdapter adap = new SqlDataAdapter("SELECT PurchaseOrderID, PurchaseOrderDetailID, OrderQty, ProductID, ReceivedQty, RejectedQty, StockedQty FROM Purchasing.PurchaseOrderDetail ", sqlconn);  
                        //Executing the QUERY and fill the dataset with the PurchaseOrderDetail table data.  
                        adap.Fill(ds, "PurchaseOrderDetail");  
                    }  
  
                    //Return the PurchaseOrderDetail table for the Report Data Source.  
                    return ds.PurchaseOrderDetail;  
                }  
                catch  
                {  
                    throw;  
                }  
            }  
        ```  
  
#### <a name="to-add-an-event-handler-that-binds-the-purchaseorderdetail-datatable-to-the-child-report"></a><span data-ttu-id="2b191-132">子レポートに PurchaseOrderDetail DataTable をバインドするイベント ハンドラーを追加するには</span><span class="sxs-lookup"><span data-stu-id="2b191-132">To add an event handler that binds the PurchaseOrderDetail DataTable to the child report</span></span>  
  
1.  <span data-ttu-id="2b191-133">Default.aspx を開きます。</span><span class="sxs-lookup"><span data-stu-id="2b191-133">Open Default.aspx.</span></span>  
  
2.  <span data-ttu-id="2b191-134">ReportViewer コントロールを右クリックし、[プロパティ] をクリックし**ます。**</span><span class="sxs-lookup"><span data-stu-id="2b191-134">Right click the ReportViewer control, and then click **Properties.**</span></span>  
  
3.  <span data-ttu-id="2b191-135">[**プロパティ**] ページで、[**イベント**] アイコンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="2b191-135">On the **Properties** page, click the **Events** icon.</span></span>  
  
4.  <span data-ttu-id="2b191-136">[**ドリルスルー** ] イベントをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="2b191-136">Double click the **Drillthrough** event.</span></span>  
  
     <span data-ttu-id="2b191-137">次に示すブロックに似たイベント ハンドラー セクションがコードに追加されます。</span><span class="sxs-lookup"><span data-stu-id="2b191-137">This will add an event handler section in the code, which will look similar to the below block.</span></span>  
  
    ```  
    protected void ReportViewer1_Drillthrough(object sender, Microsoft.Reporting.WebForms.DrillthroughEventArgs e)  
    {  
    }  
    ```  
  
5.  <span data-ttu-id="2b191-138">イベント ハンドラーを完成させます。</span><span class="sxs-lookup"><span data-stu-id="2b191-138">Complete the event handler.</span></span> <span data-ttu-id="2b191-139">このイベント ハンドラーには、次の機能を含めます。</span><span class="sxs-lookup"><span data-stu-id="2b191-139">It should include the following functionalty.</span></span>  
  
    1.  <span data-ttu-id="2b191-140">*DrillthroughEventArgs* パラメーターから子レポート オブジェクト参照をフェッチする。</span><span class="sxs-lookup"><span data-stu-id="2b191-140">Fetch the child report object reference from the *DrillthroughEventArgs* parameter.</span></span>  
  
    2.  <span data-ttu-id="2b191-141">関数を呼び出します。`GetPurchaseOrderDetail`</span><span class="sxs-lookup"><span data-stu-id="2b191-141">Call the function, `GetPurchaseOrderDetail`</span></span>  
  
    3.  <span data-ttu-id="2b191-142">`PurchaseOrderDetail` DataTable をレポートの対応するデータ ソースにバインドする。</span><span class="sxs-lookup"><span data-stu-id="2b191-142">Bind the `PurchaseOrderDetail` DataTable with the report's corresponding data source.</span></span>  
  
         <span data-ttu-id="2b191-143">完成したイベント ハンドラーのコードは、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="2b191-143">The completed event handler code will look similar to the following.</span></span>  
  
        ```  
        protected void ReportViewer1_Drillthrough(object sender, Microsoft.Reporting.WebForms.DrillthroughEventArgs e)  
            {  
                try  
                {  
                     //Get the instance of the Target report, in our case the JumpReport.rdlc.  
                    LocalReport report = (LocalReport)e.Report;  
  
                     //Binding the DataTable to the Child report dataset.  
                    //The name DataSet1 which can be located from,   
                    //Go to Design view of Child.rdlc, Click View menu -> Report Data  
                    //You'll see this name under DataSet2.  
                    report.DataSources.Add(new ReportDataSource("DataSet1", GetPurchaseOrderDetail()));  
                }  
                catch (Exception ex)  
                {  
                    Response.Write(ex.Message);  
                }  
            }  
        ```  
  
6.  <span data-ttu-id="2b191-144">ファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="2b191-144">Save the file.</span></span>  
  
## <a name="query-filter"></a><span data-ttu-id="2b191-145">クエリ フィルター</span><span class="sxs-lookup"><span data-stu-id="2b191-145">Query Filter</span></span>  
 <span data-ttu-id="2b191-146">クエリ フィルターを実装するには、次の操作を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2b191-146">You need to complete the following tasks to implement a query filter.</span></span>  
  
-   <span data-ttu-id="2b191-147">`PurchaseOrderDetail` テーブルからフィルター選択されたデータを選択する関数を作成します。</span><span class="sxs-lookup"><span data-stu-id="2b191-147">Create a function that selected filtered data from the `PurchaseOrderDetail` table.</span></span>  
  
-   <span data-ttu-id="2b191-148">パラメーター値を取得し、その DataTable を子レポートにバインドするイベントハンドラーを追加し `PurchaseOrdeDetail` ます。</span><span class="sxs-lookup"><span data-stu-id="2b191-148">Add an event handler that retrieves parameter values and binds the `PurchaseOrdeDetail` DataTable to the child report.</span></span>  
  
#### <a name="to-create-a-function-that-selects-filtered-data-from-the-purchaseorderdetail-table"></a><span data-ttu-id="2b191-149">PurchaseOrderDetail テーブルからフィルター選択されたデータを選択する関数を作成するには</span><span class="sxs-lookup"><span data-stu-id="2b191-149">To create a function that selects filtered data from the PurchaseOrderDetail table</span></span>  
  
1.  <span data-ttu-id="2b191-150">ソリューション エクスプローラーで、Default.aspx を展開し、Default.aspx.cs をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="2b191-150">In Solution Explorer, expand Default.aspx, and then double click Default.aspx.cs.</span></span>  
  
2.  <span data-ttu-id="2b191-151">新しい関数を作成します。この関数は、Integer 型の `productid` パラメーターを受け取った後、`datatable` オブジェクトを返し、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="2b191-151">Create a new function that accepts a parameter, `productid`, of type Integer and returns a `datatable` object and does the following.</span></span>  
  
    1.  <span data-ttu-id="2b191-152">「 `DataSet2` [レッスン 4: 子レポートのデータ接続とデータテーブルを定義する](lesson-4-define-a-data-connection-and-data-table-for-child-report.md)」の手順2で作成したデータセットのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="2b191-152">Creates an instance of the dataset, `DataSet2`, which was created in Step 2 of [Lesson 4: Define a Data Connection and Data Table for Child Report](lesson-4-define-a-data-connection-and-data-table-for-child-report.md).</span></span>  
  
    2.  <span data-ttu-id="2b191-153">SqlServer データベースへの接続を作成し、 **「レッスン 4: 子レポートのデータ接続とデータ テーブルを定義する」** で定義したクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="2b191-153">Create a connection to the SqlServer database to execute the query defined **Lesson 4: Define a Data Connection and DataTable for Child Report**.</span></span>  
  
    3.  <span data-ttu-id="2b191-154">このクエリには、返されるデータを親レポートで選択された `productid` に基づいてフィルター選択するための `ProductID` パラメーターが含まれます。</span><span class="sxs-lookup"><span data-stu-id="2b191-154">The query will include a parameter, `productid`, to make sure the data returned is filtered based on the `ProductID` selected in the parent report.</span></span>  
  
    4.  <span data-ttu-id="2b191-155">クエリを実行して、フィルター選択されたデータを DataSet インスタンスに入力します。</span><span class="sxs-lookup"><span data-stu-id="2b191-155">Fill the DataSet instance with the filtered data by executing the query.</span></span>  
  
    5.  <span data-ttu-id="2b191-156">`PurchaseOrderDetail` DataTable を返します。</span><span class="sxs-lookup"><span data-stu-id="2b191-156">Return the `PurchaseOrderDetail` DataTable.</span></span>  
  
         <span data-ttu-id="2b191-157">関数は次のようになります (これは単なる参考です。</span><span class="sxs-lookup"><span data-stu-id="2b191-157">The function will look similar to the one below, (This is just for your reference.</span></span> <span data-ttu-id="2b191-158">任意のパターンに従って、子レポートに必要なデータをフェッチできます)。</span><span class="sxs-lookup"><span data-stu-id="2b191-158">You can follow any pattern that you want, to fetch the necessary data for child report).</span></span>  
  
        ```  
        /// <summary>  
            /// Function to query PurchaseOrderDetail table and filter the  
            /// data for a specific ProductID selected in the Parent report.  
            /// </summary>  
            /// <param name="productid">Parameter passed from the Parent report to filter data.</param>  
            /// <returns>A dataTable of type PurchaseOrderDetail</returns>  
            private DataTable GetPurchaseOrderDetail(int productid)  
            {  
                try  
                {  
                    //Create the instance for the typed dataset, DataSet2 which will   
                    //hold the [PurchaseOrderDetail] table details.  
                    //The dataset was created as part of the tutorial in Step 4.  
                    DataSet2 ds = new DataSet2();  
  
                    //Create a SQL Connection to the AdventureWorks2008 database using Windows Authentication.  
                    using (SqlConnection sqlconn = new SqlConnection("Data Source=.;Initial Catalog=Adventureworks;Integrated Security=SSPI"))  
                    {  
                        //Building the dynamic query with the parameter ProductID.  
                        SqlDataAdapter adap = new SqlDataAdapter("SELECT PurchaseOrderID, PurchaseOrderDetailID, OrderQty, ProductID, ReceivedQty, RejectedQty, StockedQty FROM Purchasing.PurchaseOrderDetail where ProductID = " + productid, sqlconn);  
                        //Executing the QUERY and fill the dataset with the PurchaseOrderDetail table data.  
                        adap.Fill(ds, "PurchaseOrderDetail");  
                    }  
  
                    //Return the PurchaseOrderDetail table for the Report Data Source.  
                    return ds.PurchaseOrderDetail;  
                }  
                catch  
                {  
                    throw;  
                }  
            }  
        ```  
  
#### <a name="to-add-an-event-handler-that-retrieves-parameter-values-and-binds-the-purchaseordedetail-datatable-to-the-child-report"></a><span data-ttu-id="2b191-159">パラメーター値を取得し、PurchaseOrderDetail DataTable を子レポートにバインドするイベント ハンドラーを追加するには</span><span class="sxs-lookup"><span data-stu-id="2b191-159">To add an event handler that retrieves parameter values and binds the PurchaseOrdeDetail DataTable to the child report</span></span>  
  
1.  <span data-ttu-id="2b191-160">Default.aspx を開きます。</span><span class="sxs-lookup"><span data-stu-id="2b191-160">Open Default.aspx.</span></span>  
  
2.  <span data-ttu-id="2b191-161">ReportViewer コントロールを右クリックし、[**プロパティ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2b191-161">Right-click the ReportViewer control, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="2b191-162">[**プロパティ**] ウィンドウで、[**イベント**] アイコンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="2b191-162">On the **Properties** pane, click the **Events** icon.</span></span>  
  
4.  <span data-ttu-id="2b191-163">[**ドリルスルー** ] イベントをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="2b191-163">Double click the **Drillthrough** event.</span></span>  
  
     <span data-ttu-id="2b191-164">次のようなイベント ハンドラー セクションがコードに追加されます。</span><span class="sxs-lookup"><span data-stu-id="2b191-164">This will add an event handler section in the code that will look similar to the following.</span></span>  
  
    ```  
    protected void ReportViewer1_Drillthrough(object sender, Microsoft.Reporting.WebForms.DrillthroughEventArgs e)  
    {  
    }  
    ```  
  
5.  <span data-ttu-id="2b191-165">イベント ハンドラーを完成させます。</span><span class="sxs-lookup"><span data-stu-id="2b191-165">Complete the event handler.</span></span> <span data-ttu-id="2b191-166">このイベント ハンドラーには、次の機能を含めます。</span><span class="sxs-lookup"><span data-stu-id="2b191-166">It should include the following functionality.</span></span>  
  
    1.  <span data-ttu-id="2b191-167">*DrillthroughEventArgs* パラメーターから子レポート オブジェクト参照をフェッチする。</span><span class="sxs-lookup"><span data-stu-id="2b191-167">Fetch the Child report object reference from the *DrillthroughEventArgs* parameter.</span></span>  
  
    2.  <span data-ttu-id="2b191-168">フェッチした子レポート オブジェクトから子レポート パラメーター リストを取得する。</span><span class="sxs-lookup"><span data-stu-id="2b191-168">Get the child report parameter list from the child report object fetched.</span></span>  
  
    3.  <span data-ttu-id="2b191-169">パラメーターのコレクションに対して反復処理を行い、親レポートから渡された `ProductID` パラメーターの値を取得する。</span><span class="sxs-lookup"><span data-stu-id="2b191-169">Iterate through the parameter's collection and retrieve the value for the parameter, `ProductID`, passed from the parent report.</span></span>  
  
    4.  <span data-ttu-id="2b191-170">`GetPurchaseOrderDetail` 関数を呼び出し、`ProductID` パラメーターの値を渡す。</span><span class="sxs-lookup"><span data-stu-id="2b191-170">Call the function, `GetPurchaseOrderDetail`, and pass the value for parameter `ProductID`.</span></span>  
  
    5.  <span data-ttu-id="2b191-171">DataTable を `PurchaseOrderDetail` レポートの対応するデータソースにバインドします。</span><span class="sxs-lookup"><span data-stu-id="2b191-171">Bind the `PurchaseOrderDetail` DataTable with the Report's corresponding data source.</span></span>  
  
         <span data-ttu-id="2b191-172">完成したイベント ハンドラーのコードは、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="2b191-172">The completed event handler code will look similar to the following.</span></span>  
  
        ```  
        protected void ReportViewer1_Drillthrough(object sender, Microsoft.Reporting.WebForms.DrillthroughEventArgs e)  
            {  
                try  
                {  
                    //Variable to store the parameter value passed from the MainReport.  
                    int productid = 0;  
  
                    //Get the instance of the Target report, in our case the JumpReport.rdlc.  
                    LocalReport report = (LocalReport)e.Report;  
  
                    //Get all the parameters passed from the main report to the target report.  
                    //OriginalParametersToDrillthrough actually returns a Generic list of   
                    //type ReportParameter.  
                    IList<ReportParameter> list = report.OriginalParametersToDrillthrough;  
  
                    //Parse through each parameters to fetch the values passed along with them.  
                    foreach (ReportParameter param in list)  
                    {  
                        //Since we know the report has only one parameter and it is not a multivalued,   
                        //we can directly fetch the first value from the Values array.  
                        productid = Convert.ToInt32(param.Values[0].ToString());  
                    }  
  
                    //Binding the DataTable to the Child report dataset.  
                    //The name DataSet1 which can be located from,   
                    //Go to Design view of Child.rdlc, Click View menu -> Report Data  
                    //You'll see this name under DataSet2.  
                    report.DataSources.Add(new ReportDataSource("DataSet1", GetPurchaseOrderDetail(productid)));  
                }  
                catch (Exception ex)  
                {  
                    Response.Write(ex.Message);  
                }  
            }  
        ```  
  
6.  <span data-ttu-id="2b191-173">ファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="2b191-173">Save the file.</span></span>  
  
## <a name="next-task"></a><span data-ttu-id="2b191-174">次の作業</span><span class="sxs-lookup"><span data-stu-id="2b191-174">Next Task</span></span>  
 <span data-ttu-id="2b191-175">これで、子レポートに対して定義したデータ テーブルのデータ フィルターを作成できました。</span><span class="sxs-lookup"><span data-stu-id="2b191-175">You have successfully created a data filter for the data table that you defined for the child report.</span></span> <span data-ttu-id="2b191-176">次は、Web サイト アプリケーションをビルドして実行します。</span><span class="sxs-lookup"><span data-stu-id="2b191-176">Next, you will build and run the website application.</span></span>  
  
  
