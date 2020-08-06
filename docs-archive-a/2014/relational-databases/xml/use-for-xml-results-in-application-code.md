---
title: アプリケーション コードでの FOR XML の結果の使用 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- FOR XML clause, application code usage
- XML [SQL Server], FOR XML clause
- ASP.NET [SQL Server]
- .NET Framework [SQL Server], FOR XML data
- ADO [SQL Server]
- XML data islands [SQL Server]
- data islands [SQL Server]
ms.assetid: 41ae67bd-ece9-49ea-8062-c8d658ab4154
author: rothja
ms.author: jroth
ms.openlocfilehash: 3cabe7e65cb53a28a370615ed84e38ba2b8db44c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644348"
---
# <a name="use-for-xml-results-in-application-code"></a><span data-ttu-id="020d0-102">アプリケーション コードでの FOR XML の結果の使用</span><span class="sxs-lookup"><span data-stu-id="020d0-102">Use FOR XML Results in Application Code</span></span>
  <span data-ttu-id="020d0-103">SQL クエリで FOR XML 句を使用することにより、クエリの結果を XML データで取得したり、XML データにキャストすることができます。</span><span class="sxs-lookup"><span data-stu-id="020d0-103">By using FOR XML clauses with SQL queries, you can retrieve and even cast query results as XML data.</span></span> <span data-ttu-id="020d0-104">この機能により、FOR XML のクエリの結果を XML アプリケーション コードで使用するときに、次のことが可能になります。</span><span class="sxs-lookup"><span data-stu-id="020d0-104">This functionality allows you to do the following when FOR XML query results can be used in XML application code:</span></span>  
  
-   <span data-ttu-id="020d0-105">[XML Data &#40;SQL Server&#41;](xml-data-sql-server.md) 値のインスタンスの SQL テーブルにクエリを実行する</span><span class="sxs-lookup"><span data-stu-id="020d0-105">Query SQL tables for instances of [XML Data &#40;SQL Server&#41;](xml-data-sql-server.md) values</span></span>  
  
-   <span data-ttu-id="020d0-106">text 型や image 型のデータが含まれているクエリ結果を XML として返すために [FOR XML クエリの TYPE ディレクティブ](type-directive-in-for-xml-queries.md) を適用する</span><span class="sxs-lookup"><span data-stu-id="020d0-106">Apply the [TYPE Directive in FOR XML Queries](type-directive-in-for-xml-queries.md) to return the result of queries that contain text or image typed data as XML</span></span>  
  
 <span data-ttu-id="020d0-107">このトピックでは、これらの方法を示す例を提供します。</span><span class="sxs-lookup"><span data-stu-id="020d0-107">This topic provides examples that demonstrate these approaches.</span></span>  
  
## <a name="retrieving-for-xml-data-with-ado-and-xml-data-islands"></a><span data-ttu-id="020d0-108">ADO と XML データ アイランドによる、FOR XML データの取得</span><span class="sxs-lookup"><span data-stu-id="020d0-108">Retrieving FOR XML Data with ADO and XML Data Islands</span></span>  
 <span data-ttu-id="020d0-109">FOR XML クエリで作業を行っているときに、ADO `Stream` オブジェクト、または ASP (Active Server Page) `IStream` オブジェクトや `Request` オブジェクトなどの、COM `Response` インターフェイスをサポートする他のオブジェクトを使用して、結果を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="020d0-109">The ADO `Stream` object or other objects that support the COM `IStream` interface, such as the Active Server Pages (ASP) `Request` and `Response` objects, can be used to contain the results when you are working with FOR XML queries.</span></span>  
  
 <span data-ttu-id="020d0-110">たとえば、次の ASP コードは、AdventureWorks サンプル データベースの Sales.Store テーブルにある、`xml` データ型の列である Demographics のクエリ結果を示しています。</span><span class="sxs-lookup"><span data-stu-id="020d0-110">For example, the following ASP code shows the results of querying an `xml` data type column, Demographics, in the Sales.Store table of the AdventureWorks sample database.</span></span> <span data-ttu-id="020d0-111">具体的には、クエリは CustomerID が 3 の行で、この列のインスタンス値を検索します。</span><span class="sxs-lookup"><span data-stu-id="020d0-111">Specifically, the query looks for the instance value of this column for the row where the CustomerID is equal to 3.</span></span>  
  
```  
<!-- BeginRecordAndStreamVBS -->  
<%@ LANGUAGE = VBScript %>  
<!-- %  Option Explicit      % -->  
<!-- 'Request.ServerVariables("SERVER_NAME") & ";" & _ -->  
<HTML>  
<HEAD>  
<META NAME="GENERATOR" Content="Microsoft Developer Studio"/>  
<META HTTP-EQUIV="Content-Type" content="text/html"; charset="iso-8859-1">  
<TITLE>FOR XML Query Example</TITLE>  
<STYLE>  
   BODY  
   {  
      FONT-FAMILY: Tahoma;  
      FONT-SIZE: 8pt;  
      OVERFLOW: auto  
   }  
   H3  
   {  
      FONT-FAMILY: Tahoma;  
      FONT-SIZE: 8pt;  
      OVERFLOW: auto  
   }  
</STYLE>  
  
<!-- #include file="adovbs.inc" -->  
<%  
   Response.Write "<H3>Server-side processing</H3>"  
   Response.Write "Page Generated @ " & Now() & "<BR/>"  
   Dim adoConn  
   Set adoConn = Server.CreateObject("ADODB.Connection")  
   Dim sConn  
   sConn = "Provider=SQLOLEDB;Data Source=(local);" & _  
            "Initial Catalog=AdventureWorks;Integrated Security=SSPI;"  
   Response.write "Connect String = " & sConn & "<BR/>"  
   adoConn.ConnectionString = sConn  
   adoConn.CursorLocation = adUseClient  
   adoConn.Open  
   Response.write "ADO Version = " & adoConn.Version & "<BR/>"  
   Response.write "adoConn.State = " & adoConn.State & "<BR/>"  
   Dim adoCmd  
   Set adoCmd = Server.CreateObject("ADODB.Command")  
   Set adoCmd.ActiveConnection = adoConn  
   Dim sQuery  
   sQuery = "<ROOT xmlns:sql='urn:schemas-microsoft-com:xml-sql'><sql:query>SELECT Demographics from Sales.Store WHERE CustomerID = 3 FOR XML AUTO</sql:query></ROOT>"  
   Response.write "Query String = " & sQuery & "<BR/>"  
   Dim adoStreamQuery  
   Set adoStreamQuery = Server.CreateObject("ADODB.Stream")  
   adoStreamQuery.Open  
   adoStreamQuery.WriteText sQuery, adWriteChar  
   adoStreamQuery.Position = 0  
   adoCmd.CommandStream = adoStreamQuery  
   adoCmd.Dialect = "{5D531CB2-E6Ed-11D2-B252-00C04F681B71}"  
   Response.write "Pushing XML to client for processing "  & "<BR/>"  
   adoCmd.Properties("Output Stream") = Response  
   Response.write "<XML ID='MyDataIsle'>"  
   adoCmd.Execute , , 1024  
   Response.write "</XML>"  
%>  
<SCRIPT language="VBScript" For="window" Event="onload">  
   Dim xmlDoc  
   Set xmlDoc = MyDataIsle.XMLDocument  
   Dim root  
   Set root = xmlDoc.documentElement.childNodes.Item(0).childNodes.Item(0).childNodes.Item(0)  
   For each child in root.childNodes  
      dim OutputXML  
      OutputXML = document.all("log").innerHTML  
      document.all("log").innerHTML = OutputXML & "<LI><B>" & child.nodeName &  ":</B>  " & child.Text  & "</LI>"  
   Next  
   MsgBox xmlDoc.xml  
</SCRIPT>  
</HEAD>  
<BODY>  
   <H3>Client-side processing of XML Document MyDataIsle</H3>  
   <UL id=log>  
   </UL>  
</BODY>  
</HTML>  
<!-- EndRecordAndStreamVBS -->  
```  
  
 <span data-ttu-id="020d0-112">この例の ASP ページには、ADO を使用して FOR XML クエリを実行し、XML データ アイランドの MyDataIsle に XML の結果を返す、サーバー側の VBScript が含まれています。</span><span class="sxs-lookup"><span data-stu-id="020d0-112">This example ASP page contains server-side VBScript that uses ADO to execute the FOR XML query and return the XML results in an XML data island, MyDataIsle.</span></span> <span data-ttu-id="020d0-113">次に、クライアント側の追加処理用に、この XML データ アイランドがブラウザーに返されます。</span><span class="sxs-lookup"><span data-stu-id="020d0-113">This XML data island is then returned in the browser for additional client-side processing.</span></span> <span data-ttu-id="020d0-114">その後、クライアント側の追加の VBScript コードを使用して、XML データ アイランドのコンテンツが処理されます。</span><span class="sxs-lookup"><span data-stu-id="020d0-114">Additional client-side VBScript code is then used to process the contents of the XML data island.</span></span> <span data-ttu-id="020d0-115">この処理が実行されてから、結果の DHTML の一部としてコンテンツを表示し、メッセージ ボックスを開いて XML データ アイランドの前処理されたコンテンツを示します。</span><span class="sxs-lookup"><span data-stu-id="020d0-115">This process is performed before displaying the contents as part of the resultant DHTML and opening a message box to show the preprocessed contents of the XML data island.</span></span>  
  
#### <a name="to-test-this-example"></a><span data-ttu-id="020d0-116">この例をテストするには</span><span class="sxs-lookup"><span data-stu-id="020d0-116">To test this example</span></span>  
  
1.  <span data-ttu-id="020d0-117">IIS がインストールされ、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の AdventureWorks サンプル データベースがインストールされていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="020d0-117">Verify that IIS is installed and that the AdventureWorks sample database for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] has been installed.</span></span>  
  
     <span data-ttu-id="020d0-118">この例では、IIS (インターネット インフォメーション サービス) Version 5.0 以降がインストールされていて、ASP のサポートが有効になっている必要があります。</span><span class="sxs-lookup"><span data-stu-id="020d0-118">This example requires that Internet Information Services (IIS) version 5.0, or later versions, are installed with ASP support enabled.</span></span> <span data-ttu-id="020d0-119">また、AdventureWorks サンプル データベースがインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="020d0-119">Also, the AdventureWorks sample database has to be installed.</span></span>  
  
2.  <span data-ttu-id="020d0-120">前述のコード例をコピーし、XML エディターまたはテキスト エディターに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="020d0-120">Copy the code example that was previously provided and paste it into the XML or text editor that you use.</span></span> <span data-ttu-id="020d0-121">ファイルに RetrieveResults.asp という名前を付けて、IIS で使用されているルート ディレクトリに保存します。</span><span class="sxs-lookup"><span data-stu-id="020d0-121">Save the file as RetrieveResults.asp in the root directory that is used for IIS.</span></span> <span data-ttu-id="020d0-122">通常、ルート ディレクトリは C:\Inetpub\wwwroot です。</span><span class="sxs-lookup"><span data-stu-id="020d0-122">Typically, this is C:Inetpub\wwwroot.</span></span>  
  
3.  <span data-ttu-id="020d0-123">次の URL を使用して、ブラウザー ウィンドウで ASP ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="020d0-123">Open the ASP page in a browser window by using the following URL.</span></span> <span data-ttu-id="020d0-124">まず、"MyServer" を "localhost" または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] と IIS がインストールされている実際のサーバー名に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="020d0-124">First, replace 'MyServer' with either "localhost" or the actual name of the server where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and IIS are installed.</span></span>  
  
    ```  
    http://MyServer/RetrieveResults.asp  
    ```  
  
 <span data-ttu-id="020d0-125">表示される生成後の HTML ページの結果は、次のサンプル出力のようになります。</span><span class="sxs-lookup"><span data-stu-id="020d0-125">The generated HTML page results that appear will be similar to the following sample output:</span></span>  
  
##### <a name="server-side-processing"></a><span data-ttu-id="020d0-126">サーバー側の処理</span><span class="sxs-lookup"><span data-stu-id="020d0-126">Server-side processing</span></span>  
 <span data-ttu-id="020d0-127">Page Generated \@ 3/11/2006 3:36:02 PM</span><span class="sxs-lookup"><span data-stu-id="020d0-127">Page Generated \@ 3/11/2006 3:36:02 PM</span></span>  
  
 <span data-ttu-id="020d0-128">Connect String = Provider=SQLOLEDB;Data Source=MyServer;Initial Catalog=AdventureWorks;Integrated Security=SSPI;</span><span class="sxs-lookup"><span data-stu-id="020d0-128">Connect String = Provider=SQLOLEDB;Data Source=MyServer;Initial Catalog=AdventureWorks;Integrated Security=SSPI;</span></span>  
  
 <span data-ttu-id="020d0-129">ADO Version = 2.8</span><span class="sxs-lookup"><span data-stu-id="020d0-129">ADO Version = 2.8</span></span>  
  
 <span data-ttu-id="020d0-130">adoConn.State = 1</span><span class="sxs-lookup"><span data-stu-id="020d0-130">adoConn.State = 1</span></span>  
  
 <span data-ttu-id="020d0-131">Query String = SELECT Demographics from Sales.Store WHERE CustomerID = 3 FOR XML AUTO</span><span class="sxs-lookup"><span data-stu-id="020d0-131">Query String = SELECT Demographics from Sales.Store WHERE CustomerID = 3 FOR XML AUTO</span></span>  
  
 <span data-ttu-id="020d0-132">Pushing XML to client for processing</span><span class="sxs-lookup"><span data-stu-id="020d0-132">Pushing XML to client for processing</span></span>  
  
##### <a name="client-side-processing-of-xml-document-mydataisle"></a><span data-ttu-id="020d0-133">XML ドキュメント MyDataIsle のクライアント側の処理</span><span class="sxs-lookup"><span data-stu-id="020d0-133">Client-side processing of XML Document MyDataIsle</span></span>  
  
-   <span data-ttu-id="020d0-134">**AnnualSales:** 1500000</span><span class="sxs-lookup"><span data-stu-id="020d0-134">**AnnualSales:** 1500000</span></span>  
  
-   <span data-ttu-id="020d0-135">**AnnualRevenue:** 150000</span><span class="sxs-lookup"><span data-stu-id="020d0-135">**AnnualRevenue:** 150000</span></span>  
  
-   <span data-ttu-id="020d0-136">**BankName:** Primary International</span><span class="sxs-lookup"><span data-stu-id="020d0-136">**BankName:** Primary International</span></span>  
  
-   <span data-ttu-id="020d0-137">**BusinessType:** OS</span><span class="sxs-lookup"><span data-stu-id="020d0-137">**BusinessType:** OS</span></span>  
  
-   <span data-ttu-id="020d0-138">**YearOpened:** 1974</span><span class="sxs-lookup"><span data-stu-id="020d0-138">**YearOpened:** 1974</span></span>  
  
-   <span data-ttu-id="020d0-139">**Specialty:** 道路</span><span class="sxs-lookup"><span data-stu-id="020d0-139">**Specialty:** Road</span></span>  
  
-   <span data-ttu-id="020d0-140">**SquareFeet:** 38000</span><span class="sxs-lookup"><span data-stu-id="020d0-140">**SquareFeet:** 38000</span></span>  
  
-   <span data-ttu-id="020d0-141">**Brands:** 3</span><span class="sxs-lookup"><span data-stu-id="020d0-141">**Brands:** 3</span></span>  
  
-   <span data-ttu-id="020d0-142">**Internet:** DSL</span><span class="sxs-lookup"><span data-stu-id="020d0-142">**Internet:** DSL</span></span>  
  
-   <span data-ttu-id="020d0-143">**NumberEmployees:** 40</span><span class="sxs-lookup"><span data-stu-id="020d0-143">**NumberEmployees:** 40</span></span>  
  
 <span data-ttu-id="020d0-144">次に、VBScript メッセージ ボックスに、元のフィルター処理されていない XML データ アイランドのコンテンツが次のように表示されます。これは、FOR XML のクエリ結果によって返されたデータです。</span><span class="sxs-lookup"><span data-stu-id="020d0-144">The VBScript message box will then show the following original, unfiltered XML data island contents that were returned by the FOR XML query results.</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Sales.Store>  
    <Demographics>  
      <StoreSurvey xmlns="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/StoreSurvey">  
        <AnnualSales>1500000</AnnualSales>  
        <AnnualRevenue>150000</AnnualRevenue>  
        <BankName>Primary International</BankName>  
        <BusinessType>OS</BusinessType>  
        <YearOpened>1974</YearOpened>  
        <Specialty>Road</Specialty>  
        <SquareFeet>38000</SquareFeet>  
        <Brands>3</Brands>  
        <Internet>DSL</Internet>  
        <NumberEmployees>40</NumberEmployees>  
      </StoreSurvey>  
    </Demographics>  
  </Sales.Store>  
</ROOT>  
```  
  
## <a name="retrieving-for-xml-data-with-aspnet-and-the-net-framework"></a><span data-ttu-id="020d0-145">ASP.NET と .NET Framework を使用した、FOR XML データの取得</span><span class="sxs-lookup"><span data-stu-id="020d0-145">Retrieving FOR XML Data with ASP.NET and the .NET Framework</span></span>  
 <span data-ttu-id="020d0-146">前述の例と同様に、次の ASP.NET コードは、AdventureWorks サンプル データベースの Sales.Store テーブルにある、`xml` データ型の列である Demographics のクエリ結果を示しています。</span><span class="sxs-lookup"><span data-stu-id="020d0-146">As in the previous example, the following ASP.NET code shows the results of querying an `xml` data type column, Demographics, in the Sales.Store table of the AdventureWorks sample database.</span></span> <span data-ttu-id="020d0-147">前述の例と同様に、クエリは CustomerID が 3 の行で、この列のインスタンス値を検索します。</span><span class="sxs-lookup"><span data-stu-id="020d0-147">As in the previous example, the query looks for the instance value of this column for the row where the CustomerID is equal to 3.</span></span>  
  
 <span data-ttu-id="020d0-148">この例では、FOR XML のクエリ結果を返して表示するために、次の Microsoft .NET Framework マネージド API が使用されています。</span><span class="sxs-lookup"><span data-stu-id="020d0-148">In this example, the following Microsoft .NET Framework managed APIs are used to accomplish the return and rendering of the FOR XML query results:</span></span>  
  
1.  <span data-ttu-id="020d0-149">指定した接続文字列変数 strConn の内容に基づいて SQL Server への接続を開くために、`SqlConnection` が使用されます。</span><span class="sxs-lookup"><span data-stu-id="020d0-149">`SqlConnection` is used to open a connection to SQL Server, based on the contents of a specified connection string variable, strConn.</span></span>  
  
2.  <span data-ttu-id="020d0-150">次に、データ アダプターとして `SqlDataAdapter` が使用されます。また、FOR XML クエリを実行するために、SQL 接続および指定した SQL クエリ文字列を使用します。</span><span class="sxs-lookup"><span data-stu-id="020d0-150">`SqlDataAdapter` is then used as the data adapter and it uses the SQL connection and a specified SQL query string to execute the FOR XML query.</span></span>  
  
3.  <span data-ttu-id="020d0-151">クエリの実行後、`SqlDataAdapter.Fill` メソッドが呼び出され、FOR XML クエリの出力をデータセットに設定するために、`DataSet,` のインスタンスである MyDataSet が渡されます。</span><span class="sxs-lookup"><span data-stu-id="020d0-151">After the query has executed, the `SqlDataAdapter.Fill` method is then called and passed an instance of a `DataSet,` MyDataSet, in order to fill the data set with the output of the FOR XML query.</span></span>  
  
4.  <span data-ttu-id="020d0-152">その後、サーバーで生成される HTML ページに表示可能な文字列としてクエリ結果を返すために、`DataSet.GetXml` メソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="020d0-152">The `DataSet.GetXml` method is then called to return the query results as a string that can be displayed in the server-generated HTML page.</span></span>  
  
    ```  
    <%@ Page Language="VB" %>  
    <HTML>  
    <HEAD>  
    <TITLE>FOR XML Query Example</TITLE>  
    <STYLE>  
       BODY  
       {  
          FONT-FAMILY: Tahoma;  
          FONT-SIZE: 8pt;  
          OVERFLOW: auto  
       }  
       H3  
       {  
          FONT-FAMILY: Tahoma;  
          FONT-SIZE: 8pt;  
          OVERFLOW: auto  
       }  
    </STYLE>  
    </HEAD>  
    <BODY>  
    <%  
    Dim s as String  
    s = "<H3>Server-side processing</H3>" & _  
        "Page Generated @ " & Now() & "<BR/>"  
  
    Dim SQL As String   
    SQL = "SELECT Demographics from Sales.Store WHERE CustomerID = 3 FOR XML AUTO"  
  
    Dim strConn As String   
    strConn = "Server=(local);Database=AdventureWorks;Integrated Security=SSPI;"  
  
    Dim MySqlConn As New System.Data.SqlClient.SqlConnection(strConn)  
    Dim MySqlAdapter As New System.Data.SqlClient.SqlDataAdapter(SQL,MySqlConn)  
    Dim MyDataSet As New System.Data.DataSet  
  
    MySqlConn.Open()  
    s = s & "<P>SqlConnection opened.</P>"   
  
    MySqlAdapter.Fill(MyDataSet)  
    s = s & "<P>" & MyDataSet.GetXml  & "</P>"  
  
    MySqlConn.Close()  
    s = s & "<P>SqlConnection closed.</P>"   
  
    Message.InnerHtml=s  
    %>  
    <SPAN id="Message" runat=server />  
    </BODY>  
    </HTML>  
    ```  
  
#### <a name="to-test-this-example"></a><span data-ttu-id="020d0-153">この例をテストするには</span><span class="sxs-lookup"><span data-stu-id="020d0-153">To test this example</span></span>  
  
1.  <span data-ttu-id="020d0-154">IIS がインストールされ、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の AdventureWorks サンプル データベースがインストールされていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="020d0-154">Verify that IIS is installed and that the AdventureWorks sample database for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] has been installed.</span></span>  
  
     <span data-ttu-id="020d0-155">この例では、IIS (インターネット インフォメーション サービス) Version 5.0 以降がインストールされていて、ASP.NET のサポートが有効になっている必要があります。</span><span class="sxs-lookup"><span data-stu-id="020d0-155">This example requires that Internet Information Services (IIS) version 5.0, or later versions, are installed with ASP.NET support enabled.</span></span> <span data-ttu-id="020d0-156">また、AdventureWorks サンプル データベースがインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="020d0-156">Also, the AdventureWorks sample database has to be installed.</span></span>  
  
2.  <span data-ttu-id="020d0-157">前述のコードをコピーし、XML エディターまたはテキスト エディターに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="020d0-157">Copy the code that was previously provided and paste it into the XML or text editor that you use.</span></span> <span data-ttu-id="020d0-158">ファイルに RetrieveResults.aspx という名前を付けて、IIS で使用されているルート ディレクトリに保存します。</span><span class="sxs-lookup"><span data-stu-id="020d0-158">Save the file as RetrieveResults.aspx in the root directory used for IIS.</span></span> <span data-ttu-id="020d0-159">通常、ルート ディレクトリは C:\Inetpub\wwwroot です。</span><span class="sxs-lookup"><span data-stu-id="020d0-159">Typically, this is C:Inetpub\wwwroot.</span></span>  
  
3.  <span data-ttu-id="020d0-160">次の URL を使用して、ブラウザー ウィンドウで ASP.NET ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="020d0-160">Open the ASP.NET page in a browser window using the following URL.</span></span> <span data-ttu-id="020d0-161">まず、"MyServer" を "localhost" または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] と IIS がインストールされている実際のサーバー名に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="020d0-161">First, replace 'MyServer' with either "localhost" or the actual name of the server where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and IIS are installed.</span></span>  
  
    ```  
    http://MyServer/RetrieveResults.aspx  
    ```  
  
 <span data-ttu-id="020d0-162">表示される生成後の HTML ページの結果は、次のサンプル出力のようになります。</span><span class="sxs-lookup"><span data-stu-id="020d0-162">The generated HTML page results that appear will be similar to the following sample output:</span></span>  
  
##### <a name="server-side-processing"></a><span data-ttu-id="020d0-163">サーバー側の処理</span><span class="sxs-lookup"><span data-stu-id="020d0-163">Server-side processing</span></span>  
  
```  
Page Generated @ 3/11/2006 3:36:02 PM  
  
SqlConnection opened.  
  
<Sales.Store><Demographics><StoreSurvey xmlns="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/StoreSurvey"><AnnualSales>1500000</AnnualSales><AnnualRevenue>150000</AnnualRevenue><BankName>Primary International</BankName><BusinessType>OS</BusinessType><YearOpened>1974</YearOpened><Specialty>Road</Specialty><SquareFeet>38000</SquareFeet><Brands>3</Brands><Internet>DSL</Internet><NumberEmployees>40</NumberEmployees></StoreSurvey></Demographics></Sales.Store>  
  
SqlConnection closed.  
```  
  
> [!NOTE]  
>  <span data-ttu-id="020d0-164">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `xml` データ型のサポートにより、type ディレクティブを指定することにより、FOR XML クエリの結果を `xml` 、string 型または image 型のデータでは[TYPE directive](type-directive-in-for-xml-queries.md)なく、データ型として返すように要求できます。</span><span class="sxs-lookup"><span data-stu-id="020d0-164">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]`xml` data type support lets you request that the result of a FOR XML query be returned as `xml` data type, instead of as string or image typed data, by specifying the [TYPE directive](type-directive-in-for-xml-queries.md).</span></span> <span data-ttu-id="020d0-165">FOR XML クエリに TYPE ディレクティブを使用すると、「 [アプリケーションでの XML データの使用](use-xml-data-in-applications.md)」で示したのと同様に、プログラムから FOR XML の結果にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="020d0-165">When the TYPE directive is used in FOR XML queries, it provides programmatic access to the FOR XML results similar to that shown in [Use XML Data in Applications](use-xml-data-in-applications.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="020d0-166">参照</span><span class="sxs-lookup"><span data-stu-id="020d0-166">See Also</span></span>  
 [<span data-ttu-id="020d0-167">FOR XML &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="020d0-167">FOR XML &#40;SQL Server&#41;</span></span>](for-xml-sql-server.md)  
  
  
