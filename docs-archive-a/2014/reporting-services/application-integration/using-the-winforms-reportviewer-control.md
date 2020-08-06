---
title: WinForms ReportViewer コントロールの使用 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- ReportViewer controls
ms.assetid: 29fb9f7d-ba65-49fd-9cbc-4c380869de96
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3e4eda5218a91b3c8286177607034da230ff7cc2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640786"
---
# <a name="using-the-winforms-reportviewer-control"></a><span data-ttu-id="a45f1-102">WinForms ReportViewer コントロールの使用</span><span class="sxs-lookup"><span data-stu-id="a45f1-102">Using the WinForms ReportViewer Control</span></span>
  <span data-ttu-id="a45f1-103">レポート サーバーに配置されたレポートまたはローカル ファイル システムにあるレポートを表示するには、WinForms ReportViewer コントロールを使用して Windows アプリケーションでレポートを表示します。</span><span class="sxs-lookup"><span data-stu-id="a45f1-103">To view reports that have been deployed to a report server or reports that exist on the local file system, you can use the WinForms ReportViewer control to render them in a Windows application.</span></span>  
  
###### <a name="to-add-the-reportviewer-control-to-a-windows-application"></a><span data-ttu-id="a45f1-104">Windows アプリケーションに ReportViewer コントロールを追加するには</span><span class="sxs-lookup"><span data-stu-id="a45f1-104">To add the ReportViewer Control to a Windows application</span></span>  
  
1.  <span data-ttu-id="a45f1-105">またはを使用して、新しい Windows アプリケーションを作成し [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[csprcs](../../includes/csprcs-md.md)] [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="a45f1-105">Create a new Windows application using either [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[csprcs](../../includes/csprcs-md.md)] or [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)].</span></span>  
  
     <span data-ttu-id="a45f1-106">\- または -</span><span class="sxs-lookup"><span data-stu-id="a45f1-106">\- Or -</span></span>  
  
     <span data-ttu-id="a45f1-107">既存の Windows アプリケーション プロジェクトを開いて新しいフォームを追加します。</span><span class="sxs-lookup"><span data-stu-id="a45f1-107">Open an exiting Windows application project and add a new form.</span></span>  
  
2.  <span data-ttu-id="a45f1-108">**ツールボックス**で ReportViewer コントロールを探します。</span><span class="sxs-lookup"><span data-stu-id="a45f1-108">Locate the ReportViewer control in the **Toolbox**.</span></span> <span data-ttu-id="a45f1-109">**ツールボックス**が表示されていない場合は、**[表示]** メニューの **[ツールボックス]** をクリックするとアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="a45f1-109">If the **Toolbox** is not visible, you can access it from the **View** menu by selecting **Toolbox**.</span></span>  
  
     <span data-ttu-id="a45f1-110">![ReportViewer コントロールの選択](../../../2014/reporting-services/media/windowsapp-toolboxreportviewer.png "ReportViewer コントロールの選択")</span><span class="sxs-lookup"><span data-stu-id="a45f1-110">![Selecting ReportViewer control](../../../2014/reporting-services/media/windowsapp-toolboxreportviewer.png "Selecting ReportViewer control")</span></span>  
  
3.  <span data-ttu-id="a45f1-111">ReportViewer コントロールを Windows フォームのデザイン画面にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="a45f1-111">Drag the ReportViewer control onto the design surface of the Windows Form.</span></span>  
  
     <span data-ttu-id="a45f1-112">reportViewer1 という名前の ReportViewer コントロールがフォームに追加されます。</span><span class="sxs-lookup"><span data-stu-id="a45f1-112">A ReportViewer control named reportViewer1 is added to the form.</span></span>  
  
 <span data-ttu-id="a45f1-113">コントロールがフォームに追加されると、**[ReportViewer タスク]** スマート タグが表示され、レポートの選択を求めるメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a45f1-113">After the control is added to the form, the **ReportViewer Tasks** smart tag appears and prompts you to select a report.</span></span>  
  
 <span data-ttu-id="a45f1-114">表示するレポートがレポートサーバーに配置されている場合は、[ **\<Server Report>** **レポートの選択**] ドロップダウンリストからオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="a45f1-114">If the report you wish to view has been deployed to a report server, select the **\<Server Report>** option from the **Choose Report** drop-down list.</span></span> <span data-ttu-id="a45f1-115">この **\<Server Report>** オプションを選択すると、[**レポートサーバーの Url** ] および [**レポートのパス**] という2つのプロパティが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a45f1-115">After the **\<Server Report>** option is selected, two additional properties appear: **Report Server Url** and **Report Path**.</span></span> <span data-ttu-id="a45f1-116">**[レポート サーバー URL]** はレポート サーバーのアドレスで、**[レポートのパス]** は表示するレポートへの完全なパスです。</span><span class="sxs-lookup"><span data-stu-id="a45f1-116">The **Report Server Url** is the address to the report server and the **Report Path** is the full path to the report to render.</span></span>  
  
 <span data-ttu-id="a45f1-117">![サーバー レポートの選択](../../../2014/reporting-services/media/windowsapp-serverreportsettings.png "サーバー レポートの選択")</span><span class="sxs-lookup"><span data-stu-id="a45f1-117">![Select server report](../../../2014/reporting-services/media/windowsapp-serverreportsettings.png "Select server report")</span></span>  
  
 <span data-ttu-id="a45f1-118">レポートをローカル モードで表示する場合は、**[新しいレポートのデザイン]** オプションを選択してレポート デザイナーを起動するか、または既存のプロジェクトに既に含まれているレポートを選択します。</span><span class="sxs-lookup"><span data-stu-id="a45f1-118">If the report you wish to view a report in local mode, select either the **Design a new report** option to launch the report designer or select a report that is already part of the existing project.</span></span>  
  
 <span data-ttu-id="a45f1-119">![ローカル レポートの選択](../../../2014/reporting-services/media/windowsapp-localreportsettings.png "ローカル レポートの選択")</span><span class="sxs-lookup"><span data-stu-id="a45f1-119">![Select local report](../../../2014/reporting-services/media/windowsapp-localreportsettings.png "Select local report")</span></span>  
  
## <a name="viewing-reports-in-remote-processing-mode"></a><span data-ttu-id="a45f1-120">リモート処理モードでのレポートの表示</span><span class="sxs-lookup"><span data-stu-id="a45f1-120">Viewing Reports in Remote Processing Mode</span></span>  
 <span data-ttu-id="a45f1-121">次の例では、WinForms ReportViewer コントロールを使用して、レポート サーバーに配置されているレポートを表示する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="a45f1-121">The following example demonstrates how to render a report that has been deployed to a report server using the WinForms ReportViewer control.</span></span> <span data-ttu-id="a45f1-122">この例では、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] サンプル レポート プロジェクトに含まれている Sales Order Detail レポートを使用します。</span><span class="sxs-lookup"><span data-stu-id="a45f1-122">This example uses the Sales Order Detail report that is included with the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample reports project.</span></span>  
  
```csharp  
public partial class Form1 : Form  
{  
    private void Form1_Load(object sender, EventArgs e)  
    {  
        // Set the processing mode for the ReportViewer to Remote  
        reportViewer1.ProcessingMode = ProcessingMode.Remote;  
  
        ServerReport serverReport = reportViewer1.ServerReport;  
  
        // Get a reference to the default credentials  
        System.Net.ICredentials credentials =  
            System.Net.CredentialCache.DefaultCredentials;  
  
        // Get a reference to the report server credentials  
        ReportServerCredentials rsCredentials =  
            serverReport.ReportServerCredentials;  
  
        // Set the credentials for the server report  
        rsCredentials.NetworkCredentials = credentials;  
  
        // Set the report server URL and report path  
        serverReport.ReportServerUrl =   
            new Uri("http:// <Server Name>/reportserver");  
        serverReport.ReportPath =   
            "/AdventureWorks Sample Reports/Sales Order Detail";  
  
        // Create the sales order number report parameter  
        ReportParameter salesOrderNumber = new ReportParameter();  
        salesOrderNumber.Name = "SalesOrderNumber";  
        salesOrderNumber.Values.Add("SO43661");  
  
        // Set the report parameters for the report  
        reportViewer1.ServerReport.SetParameters(  
            new ReportParameter[] { salesOrderNumber });  
  
        // Refresh the report  
        reportViewer1.RefreshReport();  
    }  
}  
```  
  
```vb  
Imports Microsoft.Reporting.WinForms  
  
Public Class Form1  
  
    Private Sub Form1_Load(ByVal sender As System.Object, _  
                           ByVal e As System.EventArgs) _  
                           Handles MyBase.Load  
  
        'Set the processing mode for the ReportViewer to Remote  
        reportViewer1.ProcessingMode = ProcessingMode.Remote  
  
        Dim serverReport As ServerReport  
        serverReport = reportViewer1.ServerReport  
  
        'Get a reference to the default credentials  
        Dim credentials As System.Net.ICredentials  
        credentials = System.Net.CredentialCache.DefaultCredentials  
  
        'Get a reference to the report server credentials  
        Dim rsCredentials As ReportServerCredentials  
        rsCredentials = serverReport.ReportServerCredentials  
  
        'Set the credentials for the server report  
        rsCredentials.NetworkCredentials = credentials  
  
        'Set the report server URL and report path  
        serverReport.ReportServerUrl = _  
           New Uri("http://<Server Name>/reportserver")  
        serverReport.ReportPath = _  
           "/AdventureWorks Sample Reports/Sales Order Detail"  
  
        'Create the sales order number report parameter  
        Dim salesOrderNumber As New ReportParameter()  
        salesOrderNumber.Name = "SalesOrderNumber"  
        salesOrderNumber.Values.Add("SO43661")  
  
        'Set the report parameters for the report  
        Dim parameters() As ReportParameter = {salesOrderNumber}  
        serverReport.SetParameters(parameters)  
  
        'Refresh the report  
        reportViewer1.RefreshReport()  
    End Sub  
  
End Class  
```  
  
## <a name="viewing-reports-in-local-processing-mode"></a><span data-ttu-id="a45f1-123">ローカル処理モードでのレポートの表示</span><span class="sxs-lookup"><span data-stu-id="a45f1-123">Viewing Reports in Local Processing Mode</span></span>  
 <span data-ttu-id="a45f1-124">次の例では、Windows アプリケーションの一部であり、レポート サーバーに配置されていないレポートの表示方法を示します。</span><span class="sxs-lookup"><span data-stu-id="a45f1-124">The following example demonstrates how to render a report that is part of the Windows application and has not been deployed to a report server.</span></span>  
  
###### <a name="to-add-the-sales-order-detail-report-to-a-windows-application"></a><span data-ttu-id="a45f1-125">Sales Order Detail レポートを Windows アプリケーションに追加するには</span><span class="sxs-lookup"><span data-stu-id="a45f1-125">To add the Sales Order Detail report to a Windows application</span></span>  
  
1.  <span data-ttu-id="a45f1-126">レポートを追加する Windows プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="a45f1-126">Open the Windows project to which the report will be added.</span></span>  
  
2.  <span data-ttu-id="a45f1-127">**[プロジェクト]** メニューの **[既存項目の追加]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="a45f1-127">From the **Project** menu, select **Add Existing Item**.</span></span>  
  
3.  <span data-ttu-id="a45f1-128">[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] Report Samples プロジェクトをインストールした場所を参照します。</span><span class="sxs-lookup"><span data-stu-id="a45f1-128">Browse to the location where you installed the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] Report Samples project.</span></span>  
  
     <span data-ttu-id="a45f1-129">レポート サンプルをダウンロードするには、「[AdventureWorks 2012 Report Samples](https://go.microsoft.com/fwlink/?LinkId=404153)」 (AdventureWorks 2012 のレポート サンプル) を参照してください</span><span class="sxs-lookup"><span data-stu-id="a45f1-129">The download the report samples, go to [AdventureWorks 2012 Report Samples](https://go.microsoft.com/fwlink/?LinkId=404153)</span></span>  
  
4.  <span data-ttu-id="a45f1-130">Sales Order Detail.rdl ファイルを選択して **[追加]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="a45f1-130">Select the Sales Order Detail.rdl file and click the **Add** button.</span></span>  
  
     <span data-ttu-id="a45f1-131">Sales Order Detail.rdl ファイルが、プロジェクトの一部になります。</span><span class="sxs-lookup"><span data-stu-id="a45f1-131">The Sales Order Detail.rdl file should now be part of the project.</span></span>  
  
     <span data-ttu-id="a45f1-132">![Sales Order Detail レポート](../../../2014/reporting-services/media/windowsapp-salesorderdetailreport.png "Sales Order Detail レポート")</span><span class="sxs-lookup"><span data-stu-id="a45f1-132">![Sales Order Detail Report](../../../2014/reporting-services/media/windowsapp-salesorderdetailreport.png "Sales Order Detail Report")</span></span>  
  
5.  <span data-ttu-id="a45f1-133">ソリューション エクスプローラーで Sales Order Detail.rdl ファイルを右クリックし、**[名前の変更]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="a45f1-133">Right-click the Sales Order Detail.rdl file in Solution Explorer and select **Rename**.</span></span> <span data-ttu-id="a45f1-134">レポートの名前を **Sales Order Detail.rdlc** に変更し、Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="a45f1-134">Rename the report to **Sales Order Detail.rdlc** and press ENTER.</span></span>  
  
     <span data-ttu-id="a45f1-135">ソリューション エクスプローラーが表示されていない場合は、**[表示]** メニューの **[ソリューション エクスプローラー]** を選択して開くことができます。</span><span class="sxs-lookup"><span data-stu-id="a45f1-135">If Solution Explorer is not visible, you can open it from the **View** menu by selecting **Solution Explorer**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a45f1-136">ファイルの拡張子を rdl から rdlc に変更することによって、[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[vsprvslong](../../includes/vsprvslong-md.md)] のレポート デザイナーでレポートを編集できるようになります。</span><span class="sxs-lookup"><span data-stu-id="a45f1-136">Renaming the file extension from rdl to rdlc will allow you to edit the report using report designer for [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[vsprvslong](../../includes/vsprvslong-md.md)].</span></span>  
  
6.  <span data-ttu-id="a45f1-137">レポートの名前を変更したら、ファイルを選択して [プロパティ] ウィンドウに置きます。</span><span class="sxs-lookup"><span data-stu-id="a45f1-137">After the report has been renamed, select the file and locate the Properties window.</span></span> <span data-ttu-id="a45f1-138">**[出力ディレクトリにコピー]** プロパティを **[新しい場合はコピーする]** に変更します。</span><span class="sxs-lookup"><span data-stu-id="a45f1-138">Change the **Copy to Output Directory** property to **Copy if Newer**.</span></span>  
  
     <span data-ttu-id="a45f1-139">![出力へのコピーの設定の構成](../../../2014/reporting-services/media/windowsapp-copytooutputsetting.png "出力へのコピーの設定の構成")</span><span class="sxs-lookup"><span data-stu-id="a45f1-139">![Configuring Copy To Output setting](../../../2014/reporting-services/media/windowsapp-copytooutputsetting.png "Configuring Copy To Output setting")</span></span>  
  
     <span data-ttu-id="a45f1-140">**[プロパティ]** ウィンドウが表示されていない場合は、**[表示]** メニューから **[プロパティ ウィンドウ]** を選択して開くことができます。</span><span class="sxs-lookup"><span data-stu-id="a45f1-140">If the **Properties** window is not visible, you can open it from the **View** menu by selecting **Properties Window**.</span></span>  
  
 <span data-ttu-id="a45f1-141">次のコード例では、販売注文データのデータセットが作成され、Sales Order Detail レポートがローカル モードで表示されます。</span><span class="sxs-lookup"><span data-stu-id="a45f1-141">The following code example will create a dataset for the sales order data and then render the Sales Order Detail report in local mode.</span></span>  
  
```csharp  
public partial class Form1 : Form  
{  
    private void Form1_Load(object sender, EventArgs e)  
    {  
        // Set the processing mode for the ReportViewer to Local  
        reportViewer1.ProcessingMode = ProcessingMode.Local;  
  
        LocalReport localReport = reportViewer1.LocalReport;  
  
        localReport.ReportPath = "Sales Order Detail.rdlc";  
  
        DataSet dataset = new DataSet("Sales Order Detail");  
  
        string salesOrderNumber = "SO43661";  
  
        // Get the sales order data  
        GetSalesOrderData(salesOrderNumber, ref dataset);  
  
        // Create a report data source for the sales order data  
        ReportDataSource dsSalesOrder = new ReportDataSource();  
        dsSalesOrder.Name = "SalesOrder";  
        dsSalesOrder.Value = dataset.Tables["SalesOrder"];  
  
        localReport.DataSources.Add(dsSalesOrder);  
  
        // Get the sales order detail data  
        GetSalesOrderDetailData(salesOrderNumber, ref dataset);  
  
        // Create a report data source for the sales order detail   
        // data  
        ReportDataSource dsSalesOrderDetail =  
            new ReportDataSource();  
        dsSalesOrderDetail.Name = "SalesOrderDetail";  
        dsSalesOrderDetail.Value =  
            dataset.Tables["SalesOrderDetail"];  
  
        localReport.DataSources.Add(dsSalesOrderDetail);  
  
        // Create a report parameter for the sales order number   
        ReportParameter rpSalesOrderNumber = new ReportParameter();  
        rpSalesOrderNumber.Name = "SalesOrderNumber";  
        rpSalesOrderNumber.Values.Add("SO43661");  
  
        // Set the report parameters for the report  
        localReport.SetParameters(  
            new ReportParameter[] { rpSalesOrderNumber });  
  
        // Refresh the report  
        reportViewer1.RefreshReport();  
    }  
  
    private void GetSalesOrderData(string salesOrderNumber,  
                                   ref DataSet dsSalesOrder)  
    {  
        string sqlSalesOrder =  
            "SELECT SOH.SalesOrderNumber, S.Name AS Store, " +  
            "       SOH.OrderDate, C.FirstName AS SalesFirstName, " +  
            "       C.LastName AS SalesLastName, E.Title AS " +  
            "       SalesTitle, SOH.PurchaseOrderNumber, " +  
            "       SM.Name AS ShipMethod, BA.AddressLine1 " +  
            "       AS BillAddress1, BA.AddressLine2 AS " +  
            "       BillAddress2, BA.City AS BillCity, " +  
            "       BA.PostalCode AS BillPostalCode, BSP.Name " +  
            "       AS BillStateProvince, BCR.Name AS " +  
            "       BillCountryRegion, SA.AddressLine1 AS " +  
            "       ShipAddress1, SA.AddressLine2 AS " +  
            "       ShipAddress2, SA.City AS ShipCity, " +  
            "       SA.PostalCode AS ShipPostalCode, SSP.Name " +  
            "       AS ShipStateProvince, SCR.Name AS " +  
            "       ShipCountryRegion, CC.Phone AS CustPhone, " +  
            "       CC.FirstName AS CustFirstName, CC.LastName " +  
            "       AS CustLastName " +  
            "FROM   Person.Address SA INNER JOIN " +  
            "       Person.StateProvince SSP ON " +  
            "       SA.StateProvinceID = SSP.StateProvinceID " +  
            "       INNER JOIN Person.CountryRegion SCR ON " +  
            "       SSP.CountryRegionCode = SCR.CountryRegionCode " +  
            "       RIGHT OUTER JOIN Sales.SalesOrderHeader SOH " +  
            "       LEFT OUTER JOIN  Person.Contact CC ON " +  
            "       SOH.ContactID = CC.ContactID LEFT OUTER JOIN" +  
            "       Person.Address BA INNER JOIN " +  
            "       Person.StateProvince BSP ON " +  
            "       BA.StateProvinceID = BSP.StateProvinceID " +  
            "       INNER JOIN Person.CountryRegion BCR ON " +  
            "       BSP.CountryRegionCode = " +  
            "       BCR.CountryRegionCode ON SOH.BillToAddressID " +  
            "       = BA.AddressID ON  SA.AddressID = " +  
            "       SOH.ShipToAddressID LEFT OUTER JOIN " +  
            "       Person.Contact C RIGHT OUTER JOIN " +  
            "       HumanResources.Employee E ON C.ContactID = " +  
            "       E.ContactID ON SOH.SalesPersonID = " +  
            "       E.EmployeeID LEFT OUTER JOIN " +  
            "       Purchasing.ShipMethod SM ON SOH.ShipMethodID " +  
            "       = SM.ShipMethodID LEFT OUTER JOIN Sales.Store" +  
            "        S ON SOH.CustomerID = S.CustomerID " +  
            "WHERE  (SOH.SalesOrderNumber = @SalesOrderNumber)";  
  
        SqlConnection connection = new  
            SqlConnection("Data Source=(local); " +  
                          "Initial Catalog=AdventureWorks; " +  
                          "Integrated Security=SSPI");  
  
        SqlCommand command =  
            new SqlCommand(sqlSalesOrder, connection);  
  
        command.Parameters.Add(  
            new SqlParameter("SalesOrderNumber",  
            salesOrderNumber));  
  
        SqlDataAdapter salesOrderAdapter = new  
            SqlDataAdapter(command);  
  
        salesOrderAdapter.Fill(dsSalesOrder, "SalesOrder");  
    }  
  
    private void GetSalesOrderDetailData(string salesOrderNumber,  
                           ref DataSet dsSalesOrder)  
    {  
        string sqlSalesOrderDetail =  
            "SELECT  SOD.SalesOrderDetailID, SOD.OrderQty, " +  
            "        SOD.UnitPrice, CASE WHEN " +  
            "        SOD.UnitPriceDiscount IS NULL THEN 0 " +  
            "        ELSE SOD.UnitPriceDiscount END AS " +  
            "        UnitPriceDiscount, SOD.LineTotal, " +  
            "        SOD.CarrierTrackingNumber, " +  
            "        SOD.SalesOrderID, P.Name, P.ProductNumber " +  
            "FROM    Sales.SalesOrderDetail SOD INNER JOIN " +  
            "        Production.Product P ON SOD.ProductID = " +  
            "        P.ProductID INNER JOIN " +  
            "        Sales.SalesOrderHeader SOH ON " +  
            "        SOD.SalesOrderID = SOH.SalesOrderID " +  
            "WHERE   (SOH.SalesOrderNumber = @SalesOrderNumber) " +  
            "ORDER BY SOD.SalesOrderDetailID";  
  
        using (SqlConnection connection = new  
            SqlConnection("Data Source=(local); " +  
                          "Initial Catalog=AdventureWorks; " +  
                          "Integrated Security=SSPI"))  
        {  
  
            SqlCommand command =  
                new SqlCommand(sqlSalesOrderDetail, connection);  
  
            command.Parameters.Add(  
                new SqlParameter("SalesOrderNumber",  
                salesOrderNumber));  
  
            SqlDataAdapter salesOrderDetailAdapter = new  
                SqlDataAdapter(command);  
  
            salesOrderDetailAdapter.Fill(dsSalesOrder,  
                "SalesOrderDetail");  
        }  
    }  
}  
```  
  
```vb  
Imports System.Data.SqlClient  
Imports Microsoft.Reporting.WinForms  
  
Public Class Form1  
  
    Private Sub Form1_Load(ByVal sender As System.Object, _  
                        ByVal e As System.EventArgs) _  
                        Handles MyBase.Load  
  
        'Set the processing mode for the ReportViewer to Local  
        reportViewer1.ProcessingMode = ProcessingMode.Local  
  
        Dim localReport As LocalReport  
        localReport = reportViewer1.LocalReport  
  
        localReport.ReportEmbeddedResource = _  
            "ReportViewerIntro.Sales Order Detail.rdlc"  
  
        Dim dataset As New DataSet("Sales Order Detail")  
  
        Dim salesOrderNumber As String = "SO43661"  
  
        'Get the sales order data  
        GetSalesOrderData(salesOrderNumber, dataset)  
  
        'Create a report data source for the sales order data  
        Dim dsSalesOrder As New ReportDataSource()  
        dsSalesOrder.Name = "SalesOrder"  
        dsSalesOrder.Value = dataset.Tables("SalesOrder")  
  
        localReport.DataSources.Add(dsSalesOrder)  
  
        'Get the sales order detail data  
        GetSalesOrderDetailData(salesOrderNumber, dataset)  
  
        'Create a report data source for the sales   
        'order detail data  
        Dim dsSalesOrderDetail As New ReportDataSource()  
        dsSalesOrderDetail.Name = "SalesOrderDetail"  
        dsSalesOrderDetail.Value = _  
            dataset.Tables("SalesOrderDetail")  
  
        localReport.DataSources.Add(dsSalesOrderDetail)  
  
        'Create a report parameter for the sales order number   
        Dim rpSalesOrderNumber As New ReportParameter()  
        rpSalesOrderNumber.Name = "SalesOrderNumber"  
        rpSalesOrderNumber.Values.Add("SO43661")  
  
        'Set the report parameters for the report  
        Dim parameters() As ReportParameter = {rpSalesOrderNumber}  
        localReport.SetParameters(parameters)  
  
        'Refresh the report  
        reportViewer1.RefreshReport()  
  
    End Sub  
  
    Private Sub GetSalesOrderData(ByVal salesOrderNumber As String, _  
                               ByRef dsSalesOrder As DataSet)  
  
        Dim sqlSalesOrder As String = _  
            "SELECT SOH.SalesOrderNumber, S.Name AS Store, " & _  
            "       SOH.OrderDate, C.FirstName AS SalesFirstName, " & _  
            "       C.LastName AS SalesLastName, E.Title AS " & _  
            "       SalesTitle, SOH.PurchaseOrderNumber, " & _  
            "       SM.Name AS ShipMethod, BA.AddressLine1 " & _  
            "       AS BillAddress1, BA.AddressLine2 AS " & _  
            "       BillAddress2, BA.City AS BillCity, " & _  
            "       BA.PostalCode AS BillPostalCode, BSP.Name " & _  
            "       AS BillStateProvince, BCR.Name AS " & _  
            "       BillCountryRegion, SA.AddressLine1 AS " & _  
            "       ShipAddress1, SA.AddressLine2 AS " & _  
            "       ShipAddress2, SA.City AS ShipCity, " & _  
            "       SA.PostalCode AS ShipPostalCode, SSP.Name " & _  
            "       AS ShipStateProvince, SCR.Name AS " & _  
            "       ShipCountryRegion, CC.Phone AS CustPhone, " & _  
            "       CC.FirstName AS CustFirstName, CC.LastName " & _  
            "       AS CustLastName " & _  
            "FROM   Person.Address SA INNER JOIN " & _  
            "       Person.StateProvince SSP ON " & _  
            "       SA.StateProvinceID = SSP.StateProvinceID " & _  
            "       INNER JOIN Person.CountryRegion SCR ON " & _  
            "       SSP.CountryRegionCode = SCR.CountryRegionCode " & _  
            "       RIGHT OUTER JOIN Sales.SalesOrderHeader SOH " & _  
            "       LEFT OUTER JOIN  Person.Contact CC ON " & _  
            "       SOH.ContactID = CC.ContactID LEFT OUTER JOIN" & _  
            "       Person.Address BA INNER JOIN " & _  
            "       Person.StateProvince BSP ON " & _  
            "       BA.StateProvinceID = BSP.StateProvinceID " & _  
            "       INNER JOIN Person.CountryRegion BCR ON " & _  
            "       BSP.CountryRegionCode = " & _  
            "       BCR.CountryRegionCode ON SOH.BillToAddressID " & _  
            "       = BA.AddressID ON  SA.AddressID = " & _  
            "       SOH.ShipToAddressID LEFT OUTER JOIN " & _  
            "       Person.Contact C RIGHT OUTER JOIN " & _  
            "       HumanResources.Employee E ON C.ContactID = " & _  
            "       E.ContactID ON SOH.SalesPersonID = " & _  
            "       E.EmployeeID LEFT OUTER JOIN " & _  
            "       Purchasing.ShipMethod SM ON SOH.ShipMethodID " & _  
            "       = SM.ShipMethodID LEFT OUTER JOIN Sales.Store" & _  
            "        S ON SOH.CustomerID = S.CustomerID " & _  
            "WHERE  (SOH.SalesOrderNumber = @SalesOrderNumber)"  
  
        Using connection As New SqlConnection( _  
                      "Data Source=(local); " & _  
                      "Initial Catalog=AdventureWorks; " & _  
                      "Integrated Security=SSPI")  
  
            Dim command As New SqlCommand(sqlSalesOrder, connection)  
  
            Dim parameter As New SqlParameter("SalesOrderNumber", _  
                salesOrderNumber)  
            command.Parameters.Add(parameter)  
  
            Dim salesOrderAdapter As New SqlDataAdapter(command)  
  
            salesOrderAdapter.Fill(dsSalesOrder, "SalesOrder")  
  
        End Using  
  
    End Sub  
  
    Private Sub GetSalesOrderDetailData( _  
                           ByVal salesOrderNumber As String, _  
                           ByRef dsSalesOrder As DataSet)  
  
        Dim sqlSalesOrderDetail As String = _  
            "SELECT  SOD.SalesOrderDetailID, SOD.OrderQty, " & _  
            "        SOD.UnitPrice, CASE WHEN " & _  
            "        SOD.UnitPriceDiscount IS NULL THEN 0 " & _  
            "        ELSE SOD.UnitPriceDiscount END AS " & _  
            "        UnitPriceDiscount, SOD.LineTotal, " & _  
            "        SOD.CarrierTrackingNumber, " & _  
            "        SOD.SalesOrderID, P.Name, P.ProductNumber " & _  
            "FROM    Sales.SalesOrderDetail SOD INNER JOIN " & _  
            "        Production.Product P ON SOD.ProductID = " & _  
            "        P.ProductID INNER JOIN " & _  
            "        Sales.SalesOrderHeader SOH ON " & _  
            "        SOD.SalesOrderID = SOH.SalesOrderID " & _  
            "WHERE   (SOH.SalesOrderNumber = @SalesOrderNumber) " & _  
            "ORDER BY SOD.SalesOrderDetailID"  
  
        Using connection As New SqlConnection( _  
                      "Data Source=(local); " & _  
                      "Initial Catalog=AdventureWorks; " & _  
                      "Integrated Security=SSPI")  
  
            Dim command As New SqlCommand(sqlSalesOrderDetail, _  
                                          connection)  
  
            Dim parameter As New SqlParameter("SalesOrderNumber", _  
                salesOrderNumber)  
            command.Parameters.Add(parameter)  
  
            Dim salesOrderDetailAdapter As New SqlDataAdapter(command)  
  
            salesOrderDetailAdapter.Fill(dsSalesOrder, _  
                "SalesOrderDetail")  
  
        End Using  
  
    End Sub  
  
End Class  
```  
  
## <a name="see-also"></a><span data-ttu-id="a45f1-142">参照</span><span class="sxs-lookup"><span data-stu-id="a45f1-142">See Also</span></span>  
 [<span data-ttu-id="a45f1-143">ReportViewer コントロールを使用した Reporting Services の統合</span><span class="sxs-lookup"><span data-stu-id="a45f1-143">Integrating Reporting Services Using the ReportViewer Controls</span></span>](../application-integration/integrating-reporting-services-using-reportviewer-controls.md)  
  
  
