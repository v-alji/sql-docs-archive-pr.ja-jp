---
title: アプリケーションでの XML データの使用 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- parameters [XML in SQL Server]
- XML [SQL Server], ADO
- columns [XML in SQL Server], ADO.NET
- ADO [XML in SQL Server]
- columns [XML in SQL Server], SQL Server Native Client
- xml data type [SQL Server], ADO
- SQLNCLI, XML
- xml data type [SQL Server], SQL Server Native Client
- SQL Server Native Client, XML
- ADO.NET [XML in SQL Server]
- XML [SQL Server], ADO.NET
- columns [XML in SQL Server], ADO
- xml data type [SQL Server], ADO.NET
- XML [SQL Server], SQL Server Native Client
ms.assetid: 5dabf7e0-c6df-451d-a070-4661f84607fd
author: rothja
ms.author: jroth
ms.openlocfilehash: 79dd4f4d2ff3cd61bc33c632f499bfb8e8817f0f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711769"
---
# <a name="use-xml-data-in-applications"></a><span data-ttu-id="62515-102">アプリケーションでの XML データの使用</span><span class="sxs-lookup"><span data-stu-id="62515-102">Use XML Data in Applications</span></span>
  <span data-ttu-id="62515-103">このトピックでは、アプリケーションで `xml` データ型を操作する際のオプションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="62515-103">This topic describes the options that are available to you for working with the `xml` data type in your application.</span></span> <span data-ttu-id="62515-104">このトピックには、次の項目に関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="62515-104">The topic includes information about the following:</span></span>  
  
-   <span data-ttu-id="62515-105">ADO および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client を使用した、`xml` 型の列に含まれている XML の操作</span><span class="sxs-lookup"><span data-stu-id="62515-105">Handling XML from an `xml` type column by using ADO and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client</span></span>  
  
-   <span data-ttu-id="62515-106">ADO.NET を使用した、`xml` 型の列に含まれている XML の操作</span><span class="sxs-lookup"><span data-stu-id="62515-106">Handling XML from an `xml` type column by using ADO.NET</span></span>  
  
-   <span data-ttu-id="62515-107">ADO.NET を使用した、パラメーターに含まれている `xml` 型の操作</span><span class="sxs-lookup"><span data-stu-id="62515-107">Handling `xml` type in parameters by using ADO.NET</span></span>  
  
## <a name="handling-xml-from-an-xml-type-column-by-using-ado-and-sql-server-native-client"></a><span data-ttu-id="62515-108">ADO および SQL Server Native Client を使用した、xml 型の列に含まれている XML の操作</span><span class="sxs-lookup"><span data-stu-id="62515-108">Handling XML from an xml Type Column by Using ADO and SQL Server Native Client</span></span>  
 <span data-ttu-id="62515-109">MDAC コンポーネントを使用して、 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]に導入された型や機能にアクセスするためには、DataTypeCompatibility 初期化プロパティを ADO 接続文字列で設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="62515-109">To use MDAC components to access the types and features that were introduced in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], you must set the DataTypeCompatibility initialization property in the ADO connection string.</span></span>  
  
 <span data-ttu-id="62515-110">たとえば、次の Visual Basic Scripting Edition (VBScript) サンプルは、`Demographics` サンプル データベースの `Sales.Store` テーブルにある、`xml` データ型の列である `AdventureWorks2012` に対するクエリの結果を示しています。</span><span class="sxs-lookup"><span data-stu-id="62515-110">For example, the following Visual Basic Scripting Edition (VBScript) sample shows the results of querying an `xml` data type column, `Demographics`, in the `Sales.Store` table of the `AdventureWorks2012` sample database.</span></span> <span data-ttu-id="62515-111">具体的には、クエリは `CustomerID` が `3`と等しい行のこの列のインスタンス値を検索します。</span><span class="sxs-lookup"><span data-stu-id="62515-111">Specifically, the query looks for the instance value of this column for the row where the `CustomerID` is equal to `3`.</span></span>  
  
```  
Const DS = "MyServer"  
Const DB = "AdventureWorks2012"  
  
Set objConn = CreateObject("ADODB.Connection")  
Set objRs = CreateObject("ADODB.Recordset")  
  
CommandText = "SELECT Demographics" & _  
              " FROM Sales.Store" & _  
              " INNER JOIN Sales.Customer" & _  
              " ON Sales.Store.BusinessEntityID = sales.customer.StoreID" & _  
              " WHERE Sales.Customer.CustomerID = 3" & _  
              " OR Sales.Customer.CustomerID = 4"  
  
ConnectionString = "Provider=SQLNCLI11" & _  
                   ";Data Source=" & DS & _  
                   ";Initial Catalog=" & DB & _  
                   ";Integrated Security=SSPI;" & _  
                   "DataTypeCompatibility=80"  
  
'Connect to the data source.  
objConn.Open ConnectionString  
  
'Execute command through the connection and display  
Set objRs = objConn.Execute(CommandText)  
  
Dim rowcount  
rowcount = 0  
Do While Not objRs.EOF  
   rowcount = rowcount + 1  
   MsgBox "Row " & rowcount & _  
           vbCrLf & vbCrLf & objRs(0)  
   objRs.MoveNext  
Loop  
  
'Clean up.  
objRs.Close  
objConn.Close  
Set objRs = Nothing  
Set objConn = Nothing  
```  
  
 <span data-ttu-id="62515-112">この例は、DataTypeCompatibility を設定する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="62515-112">This example shows how to set the data type compatibility property.</span></span> <span data-ttu-id="62515-113">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client を使用している場合、このプロパティには既定値の 0 が設定されています。</span><span class="sxs-lookup"><span data-stu-id="62515-113">By default, this is set to 0 when you are using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.</span></span> <span data-ttu-id="62515-114">値を80に設定すると、Native Client プロバイダーによって、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `xml` ユーザー定義型の列がデータ型として表示され [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="62515-114">If you set the value to 80, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client provider will make `xml` and user-defined type columns appear as [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] data types.</span></span> <span data-ttu-id="62515-115">それぞれのデータ型は、DBTYPE_WSTR および DBTYPE_BYTES になります。</span><span class="sxs-lookup"><span data-stu-id="62515-115">This would be DBTYPE_WSTR and DBTYPE_BYTES, respectively.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="62515-116">Native Client はクライアント コンピューターにもインストールし、データ プロバイダーとして使用するために、"`Provider=SQLNCLI11;...`" を含む接続文字列を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="62515-116">Native Client must also be installed on the client computer and the connection string must specify it for use as the data provider with "`Provider=SQLNCLI11;...`".</span></span>  
  
#### <a name="to-test-this-example"></a><span data-ttu-id="62515-117">この例をテストするには</span><span class="sxs-lookup"><span data-stu-id="62515-117">To test this example</span></span>  
  
1.  <span data-ttu-id="62515-118">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client がクライアント コンピューターにインストールされており、クライアント コンピューターで MDAC 2.6.0 以降のバージョンを使用できることを確認します。</span><span class="sxs-lookup"><span data-stu-id="62515-118">Verify that the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client is installed and that MDAC 2.6.0or later is available on the client computer.</span></span>  
  
     <span data-ttu-id="62515-119">詳細については、「 [SQL Server Native Client プログラミング](../native-client/sql-server-native-client-programming.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="62515-119">For more information, see [SQL Server Native Client Programming](../native-client/sql-server-native-client-programming.md).</span></span>  
  
2.  <span data-ttu-id="62515-120">[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サンプル データベースがインストールされていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="62515-120">Verify that the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is installed.</span></span>  
  
     <span data-ttu-id="62515-121">この例では [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] サンプル データベースが必要です。</span><span class="sxs-lookup"><span data-stu-id="62515-121">This example requires the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database.</span></span>  
  
3.  <span data-ttu-id="62515-122">このトピックの前半に示したコードをコピーし、テキスト エディターまたはコード エディターに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="62515-122">Copy the code shown previously in this topic and paste the code into your text or code editor.</span></span> <span data-ttu-id="62515-123">HandlingXmlDataType.vbs という名前でファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="62515-123">Save the file as HandlingXmlDataType.vbs.</span></span>  
  
4.  <span data-ttu-id="62515-124">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インストールでの必要性に応じてスクリプトを変更し、変更を保存します。</span><span class="sxs-lookup"><span data-stu-id="62515-124">Modify the script as required for your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation and save your changes.</span></span>  
  
     <span data-ttu-id="62515-125">たとえば、 `MyServer` が指定されている箇所は、 `(local)` または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がインストールされているサーバーの実際の名前のいずれかに置き換える必要があります。</span><span class="sxs-lookup"><span data-stu-id="62515-125">For example, where `MyServer` is specified, you should replace it with either `(local)` or the actual name of the server on which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is installed.</span></span>  
  
5.  <span data-ttu-id="62515-126">HandlingXmlDataType.vbs を実行し、スクリプトを実行します。</span><span class="sxs-lookup"><span data-stu-id="62515-126">Run HandlingXmlDataType.vbs and execute the script.</span></span>  
  
 <span data-ttu-id="62515-127">結果は次のサンプル出力に似たものになります。</span><span class="sxs-lookup"><span data-stu-id="62515-127">The results should be similar to the following sample output:</span></span>  
  
```  
Row 1  
  
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
  
Row 2  
  
<StoreSurvey xmlns="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/StoreSurvey">  
  <AnnualSales>300000</AnnualSales>  
  <AnnualRevenue>30000</AnnualRevenue>  
  <BankName>United Security</BankName>  
  <BusinessType>BM</BusinessType>  
  <YearOpened>1976</YearOpened>  
  <Specialty>Road</Specialty>  
  <SquareFeet>6000</SquareFeet>  
  <Brands>2</Brands>  
  <Internet>DSL</Internet>  
  <NumberEmployees>5</NumberEmployees>  
</StoreSurvey>  
```  
  
## <a name="handling-xml-from-an-xml-type-column-by-using-adonet"></a><span data-ttu-id="62515-128">ADO.NET を使用した、xml 型の列に含まれている XML の操作</span><span class="sxs-lookup"><span data-stu-id="62515-128">Handling XML from an xml Type Column by Using ADO.NET</span></span>  
 <span data-ttu-id="62515-129">ADO.NET およびを使用してデータ型の列の XML を処理するには、 `xml` [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] クラスの標準動作を使用し `SqlCommand` ます。</span><span class="sxs-lookup"><span data-stu-id="62515-129">To handle XML from an `xml` data type column by using ADO.NET and the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] you can use the standard behavior of the `SqlCommand` class.</span></span> <span data-ttu-id="62515-130">たとえば、`xml` データ型の列とその値は、`SqlDataReader` を使用して SQL 列を取得するときと同じ方法で取得できます。ただし、XML として `xml` データ型の列のコンテンツを使用して作業を行う場合は、最初にそのコンテンツを `XmlReader` 型に割り当てる必要があります。</span><span class="sxs-lookup"><span data-stu-id="62515-130">For example, an `xml` data type column and its values can be retrieved in the same way any SQL column is retrieved by using a `SqlDataReader`.However, if you want to work with the contents of an `xml` data type column as XML, you will first have to assign the contents to an `XmlReader` type.</span></span>  
  
 <span data-ttu-id="62515-131">詳細とコード例については、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnlong](../../includes/dnprdnlong-md.md)] SDK ドキュメントの「データ リーダーの XML 列の値」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="62515-131">For more information and example code, see "XML Column Values in a Data Reader" in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnlong](../../includes/dnprdnlong-md.md)] SDK documentation.</span></span>  
  
## <a name="handling-an-xml-type-column-in-parameters-by-using-adonet"></a><span data-ttu-id="62515-132">ADO.NET を使用した、パラメーター内の xml 型の列の操作</span><span class="sxs-lookup"><span data-stu-id="62515-132">Handling an xml Type Column in Parameters by Using ADO.NET</span></span>  
 <span data-ttu-id="62515-133">ADO.NET および [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] でパラメーターとして渡された xml データ型を操作するには、`SqlXml` データ型のインスタンスとして値を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="62515-133">To handle an xml data type passed as a parameter in ADO.NET and the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], you can supply the value as an instance of the `SqlXml` data type.</span></span> <span data-ttu-id="62515-134">特殊な処理は必要ありません。[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の `xml` データ型の列は、`string` や `integer` などの他の列やデータ型と同じように、パラメーター値を受け取ることができます。</span><span class="sxs-lookup"><span data-stu-id="62515-134">No special handling is involved, because `xml` data type columns in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can accept parameter values in the same way as other columns and data types, such as `string` or `integer`.</span></span>  
  
 <span data-ttu-id="62515-135">詳細とコード例については、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnlong](../../includes/dnprdnlong-md.md)] SDK ドキュメントの「コマンド パラメーターとしての XML 値」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="62515-135">For more information and example code, see "XML Values as Command Parameters" in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnlong](../../includes/dnprdnlong-md.md)] SDK documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62515-136">参照</span><span class="sxs-lookup"><span data-stu-id="62515-136">See Also</span></span>  
 [<span data-ttu-id="62515-137">XML データ &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="62515-137">XML Data &#40;SQL Server&#41;</span></span>](xml-data-sql-server.md)  
  
  
