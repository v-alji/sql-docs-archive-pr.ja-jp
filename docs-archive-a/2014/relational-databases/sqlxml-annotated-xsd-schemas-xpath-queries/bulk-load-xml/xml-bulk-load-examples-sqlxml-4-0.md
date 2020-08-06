---
title: XML 一括読み込みの例 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- overflow-field annotation
- ConnectionCommand property
- XMLFragment property
- relationship chains [SQLXML]
- multiple table bulk loading
- examples [SQLXML], XML Bulk Load
- overflow data [SQLXML]
- sql:datatype
- transaction mode [SQLXML]
- CheckConstraints property
- sql:overflow-field
- XML Bulk Load [SQLXML], examples
- TempFilePath property
- datatype annotation
- Transaction property
- KeepIdentity property
- Execute method
- streaming XML data
- xml data type [SQL Server], SQLXML
- bulk load [SQLXML], examples
ms.assetid: 970e4553-b41d-4a12-ad50-0ee65d1f305d
author: rothja
ms.author: jroth
ms.openlocfilehash: c7eaec77ef068efd28c4da65833afa5047b222f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711809"
---
# <a name="xml-bulk-load-examples-sqlxml-40"></a><span data-ttu-id="1e4ad-102">XML 一括読み込みの例 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="1e4ad-102">XML Bulk Load Examples (SQLXML 4.0)</span></span>
  <span data-ttu-id="1e4ad-103">以下の例では、Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の XML 一括読み込み機能について示します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-103">The following examples illustrate the XML Bulk Load functionality in Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="1e4ad-104">それぞれの例では、XSD スキーマと、同等の XDR スキーマを提供します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-104">Each example provides an XSD schema and its equivalent XDR schema.</span></span>  
  
## <a name="bulk-loader-script-validateandbulkloadvbs"></a><span data-ttu-id="1e4ad-105">一括読み込みスクリプト (ValidateAndBulkload.vbs)</span><span class="sxs-lookup"><span data-stu-id="1e4ad-105">Bulk Loader Script (ValidateAndBulkload.vbs)</span></span>  
 <span data-ttu-id="1e4ad-106">Visual Basic Scripting Edition (VBScript) で記述された次のスクリプトは、xml [!INCLUDE[msCoName](../../../includes/msconame-md.md)] DOM に xml ドキュメントを読み込み、スキーマに対して xml ドキュメントを検証します。ドキュメントが有効な場合、は xml 一括読み込みを実行して xml をテーブルに読み込みます。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1e4ad-106">The following script, written in the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic Scripting Edition (VBScript), loads an XML document into the XML DOM; validates it against a schema; and, if the document is valid, executes an XML bulk load to load the XML into a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] table.</span></span> <span data-ttu-id="1e4ad-107">このスクリプトは、後に示す個々の例で使用できます。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-107">This script can be used with each of the individual examples that refer to it later in this topic.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1e4ad-108">XML 一括読み込みでは、データ ファイルから内容がアップロードされなくても警告またはエラーは返されません。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-108">XML Bulk Load does not throw a warning or an error if no content is uploaded from the data file.</span></span> <span data-ttu-id="1e4ad-109">このため、一括読み込み操作を実行する前に XML データ ファイルを検証することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-109">Therefore, it is a good practice to validate your XML data file prior to executing a bulk load operation.</span></span>  
  
```  
Dim FileValid  
  
set objBL = CreateObject("SQLXMLBulkLoad.SQLXMLBulkload.4.0")  
objBL.ConnectionString = "provider=SQLOLEDB;data source=MyServer;database=tempdb;integrated security=SSPI"  
objBL.ErrorLogFile = "c:\error.log"  
  
'Validate the data file prior to bulkload  
Dim sOutput   
sOutput = ValidateFile("SampleXMLData.xml", "", "SampleSchema.xml")  
WScript.Echo sOutput  
  
If FileValid Then  
   ' Check constraints and initiate transaction (if needed)  
   ' objBL.CheckConstraints = True  
   ' objBL.Transaction=True  
  'Execute XML bulkload using file.  
  objBL.Execute "SampleSchema.xml", "SampleXMLData.xml"  
  set objBL=Nothing  
End If  
  
Function ValidateFile(strXmlFile,strUrn,strXsdFile)  
  
   ' Create a schema cache and add SampleSchema.xml to it.  
   Dim xs, fso, sAppPath  
   Set fso = CreateObject("Scripting.FileSystemObject")   
   Set xs = CreateObject("MSXML2.XMLSchemaCache.6.0")  
   sAppPath = fso.GetFolder(".")   
   xs.Add strUrn, sAppPath & "\" & strXsdFile  
  
   ' Create an XML DOMDocument object.  
   Dim xd   
   Set xd = CreateObject("MSXML2.DOMDocument.6.0")  
  
   ' Assign the schema cache to the DOM document.  
   ' schemas collection.  
   Set xd.schemas = xs  
  
   ' Load XML document as DOM document.  
   xd.async = False  
   xd.Load sAppPath & "\" & strXmlFile  
  
   ' Return validation results in message to the user.  
   If xd.parseError.errorCode <> 0 Then  
        ValidateFile = "Validation failed on " & _  
             strXmlFile & vbCrLf & _  
             "=======" & vbCrLf & _  
             "Reason: " & xd.parseError.reason & _  
             vbCrLf & "Source: " & _  
             xd.parseError.srcText & _  
             vbCrLf & "Line: " & _  
             xd.parseError.Line & vbCrLf  
             FileValid = False  
    Else  
        ValidateFile = "Validation succeeded for " & _  
             strXmlFile & vbCrLf & _  
             "========" & _  
             vbCrLf & "Contents to be bulkloaded" & vbCrLf  
             FileValid = True  
    End If  
End Function  
```  
  
## <a name="a-bulk-loading-xml-in-a-table"></a><span data-ttu-id="1e4ad-110">A.</span><span class="sxs-lookup"><span data-stu-id="1e4ad-110">A.</span></span> <span data-ttu-id="1e4ad-111">単一テーブルでの XML の一括読み込み</span><span class="sxs-lookup"><span data-stu-id="1e4ad-111">Bulk loading XML in a table</span></span>  
 <span data-ttu-id="1e4ad-112">この例 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] では、ConnectionString プロパティ (MyServer) で指定されているのインスタンスへの接続を確立します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-112">This example establishes a connection to the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that is specified in the ConnectionString property (MyServer).</span></span> <span data-ttu-id="1e4ad-113">この例では、ErrorLogFile プロパティも指定しています。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-113">The example also specifies the ErrorLogFile property.</span></span> <span data-ttu-id="1e4ad-114">エラー出力は指定したファイル ("C:\error.log") に保存されます。ファイルの保存場所は変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-114">Therefore, the error output is saved in the specified file ("C:\error.log"), which you might also decide to change to a different location.</span></span> <span data-ttu-id="1e4ad-115">また、Execute メソッドのパラメーターは、マッピングスキーマファイル (SampleSchema.xml) と XML データファイル (SampleXMLData.xml) の両方であることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-115">Notice also that the Execute method has as its parameters both the mapping schema file (SampleSchema.xml) and the XML data file (SampleXMLData.xml).</span></span> <span data-ttu-id="1e4ad-116">一括読み込みを実行すると、 **tempdb**データベースで作成した Cust テーブルには、XML データファイルの内容に基づく新しいレコードが格納されます。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-116">When the bulk load executes, the Cust table you have created in **tempdb** database will contain new records based upon the contents of the XML data file.</span></span>  
  
#### <a name="to-test-a-sample-bulk-load"></a><span data-ttu-id="1e4ad-117">一括読み込みのサンプルをテストするには</span><span class="sxs-lookup"><span data-stu-id="1e4ad-117">To test a sample bulk load</span></span>  
  
1.  <span data-ttu-id="1e4ad-118">次のテーブルを作成します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-118">Create this table:</span></span>  
  
    ```  
    CREATE TABLE Cust(CustomerID  int PRIMARY KEY,  
                      CompanyName varchar(20),  
                      City        varchar(20));  
    GO  
    ```  
  
2.  <span data-ttu-id="1e4ad-119">任意のテキスト エディターまたは XML エディターでファイルを作成し、SampleSchema.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-119">Create a file in your preferred text or XML editor, and save it as SampleSchema.xml.</span></span> <span data-ttu-id="1e4ad-120">このファイルに次の XSD スキーマを追加します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-120">To this file, add the following XSD schema:</span></span>  
  
    ```  
    <xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
                xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
       <xsd:element name="ROOT" sql:is-constant="1" >  
         <xsd:complexType>  
           <xsd:sequence>  
             <xsd:element name="Customers" sql:relation="Cust" maxOccurs="unbounded">  
               <xsd:complexType>  
                 <xsd:sequence>  
                   <xsd:element name="CustomerID"  type="xsd:integer" />  
                   <xsd:element name="CompanyName" type="xsd:string" />  
                   <xsd:element name="City"        type="xsd:string" />  
                 </xsd:sequence>  
               </xsd:complexType>  
             </xsd:element>  
           </xsd:sequence>  
          </xsd:complexType>  
         </xsd:element>  
    </xsd:schema>  
    ```  
  
3.  <span data-ttu-id="1e4ad-121">任意のテキスト エディターまたは XML エディターでファイルを作成し、SampleXMLData.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-121">Create a file in your preferred text or XML editor, and save it as SampleXMLData.xml.</span></span> <span data-ttu-id="1e4ad-122">このファイルに、次の XML ドキュメントを追加します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-122">To this file, add the following XML document:</span></span>  
  
    ```  
    <ROOT>  
      <Customers>  
        <CustomerID>1111</CustomerID>  
        <CompanyName>Sean Chai</CompanyName>  
        <City>New York</City>  
      </Customers>  
      <Customers>  
        <CustomerID>1112</CustomerID>  
        <CompanyName>Tom Johnston</CompanyName>  
         <City>Los Angeles</City>  
      </Customers>  
      <Customers>  
        <CustomerID>1113</CustomerID>  
        <CompanyName>Institute of Art</CompanyName>  
        <City>Chicago</City>  
      </Customers>  
    </ROOT>  
    ```  
  
4.  <span data-ttu-id="1e4ad-123">任意のテキスト エディターまたは XML エディターでファイルを作成し、ValidateAndBulkload.vbs として保存します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-123">Create a file in your preferred text or XML editor, and save it as ValidateAndBulkload.vbs.</span></span> <span data-ttu-id="1e4ad-124">このファイルに、このトピックの冒頭で示した VBScript コードを追加します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-124">To this file, add the VBScript code that is provided above at the beginning of this topic.</span></span> <span data-ttu-id="1e4ad-125">接続文字列は、適切なサーバー名に変更します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-125">Modify the connection string to provide the appropriate server name.</span></span> <span data-ttu-id="1e4ad-126">Execute メソッドのパラメーターとして指定されたファイルの適切なパスを指定します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-126">Specify the appropriate path for the files that are specified as parameters to the Execute method.</span></span>  
  
5.  <span data-ttu-id="1e4ad-127">VBScript コードを実行します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-127">Execute the VBScript code.</span></span> <span data-ttu-id="1e4ad-128">XML 一括読み込みによって、XML が Cust テーブルに読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-128">XML Bulk Load loads the XML into the Cust table.</span></span>  
  
 <span data-ttu-id="1e4ad-129">これは、これと同等の XDR スキーマです。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-129">This is the equivalent XDR schema:</span></span>  
  
```  
<?xml version="1.0" ?>  
<Schema xmlns="urn:schemas-microsoft-com:xml-data"   
        xmlns:dt="urn:schemas-microsoft-com:xml:datatypes"    
        xmlns:sql="urn:schemas-microsoft-com:xml-sql" >   
  
   <ElementType name="CustomerID" dt:type="int" />  
   <ElementType name="CompanyName" dt:type="string" />  
   <ElementType name="City" dt:type="string" />  
  
   <ElementType name="ROOT" sql:is-constant="1">  
      <element type="Customers" />  
   </ElementType>  
  
   <ElementType name="Customers"  sql:relation="Cust" >  
      <element type="CustomerID"  sql:field="CustomerID" />  
      <element type="CompanyName" sql:field="CompanyName" />  
      <element type="City"        sql:field="City" />  
  
   </ElementType>  
</Schema>  
```  
  
## <a name="b-bulk-loading-xml-data-in-multiple-tables"></a><span data-ttu-id="1e4ad-130">B.</span><span class="sxs-lookup"><span data-stu-id="1e4ad-130">B.</span></span> <span data-ttu-id="1e4ad-131">複数テーブルでの XML データの一括読み込み</span><span class="sxs-lookup"><span data-stu-id="1e4ad-131">Bulk loading XML data in multiple tables</span></span>  
 <span data-ttu-id="1e4ad-132">この例では、XML ドキュメントは要素と要素で構成されて **\<Customer>** **\<Order>** います。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-132">In this example, the XML document consists of the **\<Customer>** and **\<Order>** elements.</span></span>  
  
```  
<ROOT>  
  <Customers>  
    <CustomerID>1111</CustomerID>  
    <CompanyName>Sean Chai</CompanyName>  
    <City>NY</City>  
    <Order OrderID="1" />  
    <Order OrderID="2" />  
  </Customers>  
  <Customers>  
    <CustomerID>1112</CustomerID>  
    <CompanyName>Tom Johnston</CompanyName>  
     <City>LA</City>    
    <Order OrderID="3" />  
  </Customers>  
  <Customers>  
    <CustomerID>1113</CustomerID>  
    <CompanyName>Institute of Art</CompanyName>  
    <Order OrderID="4" />  
  </Customers>  
</ROOT>  
```  
  
 <span data-ttu-id="1e4ad-133">この例では、XML データを**Cust**および**custorder**という2つのテーブルに一括読み込みします。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-133">This example bulk loads the XML data into two tables, **Cust** and **CustOrder**:</span></span>  
  
```  
Cust(CustomerID, CompanyName, City)  
CustOrder(OrderID, CustomerID)  
```  
  
 <span data-ttu-id="1e4ad-134">次の XSD スキーマでは、これらのテーブルの XML ビューが定義されています。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-134">The following XSD schema defines the XML view of these tables.</span></span> <span data-ttu-id="1e4ad-135">スキーマでは、要素と要素の間の親子リレーションシップを指定し **\<Customer>** **\<Order>** ます。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-135">The schema specifies the parent-child relationship between the **\<Customer>** and **\<Order>** elements.</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:annotation>  
    <xsd:appinfo>  
      <sql:relationship name="CustCustOrder"  
          parent="Cust"  
          parent-key="CustomerID"  
          child="CustOrder"  
          child-key="CustomerID" />  
    </xsd:appinfo>  
  </xsd:annotation>  
  <xsd:element name="ROOT" sql:is-constant="1" >  
    <xsd:complexType>  
      <xsd:sequence>  
        <xsd:element name="Customers" sql:relation="Cust" >  
          <xsd:complexType>  
            <xsd:sequence>  
              <xsd:element name="CustomerID"  type="xsd:integer" />  
              <xsd:element name="CompanyName" type="xsd:string" />  
              <xsd:element name="City"        type="xsd:string" />  
              <xsd:element name="Order"   
                          sql:relation="CustOrder"  
                          sql:relationship="CustCustOrder" >  
                <xsd:complexType>  
                  <xsd:attribute name="OrderID" type="xsd:integer" />  
                </xsd:complexType>  
              </xsd:element>  
             </xsd:sequence>  
          </xsd:complexType>  
        </xsd:element>  
      </xsd:sequence>  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 <span data-ttu-id="1e4ad-136">XML 一括読み込みでは、上で指定された要素と要素の間の主キー/外部キーのリレーションシップを使用して、 **\<Cust>** **\<CustOrder>** データを両方のテーブルに一括読み込みします。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-136">XML Bulk Load uses the primary key/foreign key relationship specified above between the **\<Cust>** and **\<CustOrder>** elements to bulk load the data into both tables.</span></span>  
  
#### <a name="to-test-a-sample-bulk-load"></a><span data-ttu-id="1e4ad-137">一括読み込みのサンプルをテストするには</span><span class="sxs-lookup"><span data-stu-id="1e4ad-137">To test a sample bulk load</span></span>  
  
1.  <span data-ttu-id="1e4ad-138">**Tempdb**データベースに2つのテーブルを作成します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-138">Create two tables in **tempdb** database:</span></span>  
  
    ```  
    USE tempdb;  
    CREATE TABLE Cust(  
           CustomerID  int PRIMARY KEY,  
           CompanyName varchar(20),  
           City        varchar(20));  
    CREATE TABLE CustOrder(        OrderID     int PRIMARY KEY,   
            CustomerID int FOREIGN KEY REFERENCES Cust(CustomerID));  
    ```  
  
2.  <span data-ttu-id="1e4ad-139">任意のテキスト エディターまたは XML エディターでファイルを作成し、SampleSchema.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-139">Create a file in your preferred text or XML editor, and save it as SampleSchema.xml.</span></span> <span data-ttu-id="1e4ad-140">このファイルに、この例で示した XSD スキーマを追加します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-140">Add the XSD schema that is provided in this example to the file.</span></span>  
  
3.  <span data-ttu-id="1e4ad-141">任意のテキスト エディターまたは XML エディターでファイルを作成し、SampleData.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-141">Create a file in your preferred text or XML editor, and save it as SampleData.xml.</span></span> <span data-ttu-id="1e4ad-142">このファイルに、この例で前に示した XML ドキュメントを追加します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-142">Add the XML document that was provided earlier in this example to the file.</span></span>  
  
4.  <span data-ttu-id="1e4ad-143">任意のテキスト エディターまたは XML エディターでファイルを作成し、ValidateAndBulkload.vbs として保存します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-143">Create a file in your preferred text or XML editor, and save it as ValidateAndBulkload.vbs.</span></span> <span data-ttu-id="1e4ad-144">このファイルに、このトピックの冒頭で示した VBScript コードを追加します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-144">To this file, add the VBScript code that is provided above at the beginning of this topic.</span></span> <span data-ttu-id="1e4ad-145">接続文字列は、適切なサーバー名とデータベース名に変更します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-145">Modify the connection string to provide the appropriate server and database name.</span></span> <span data-ttu-id="1e4ad-146">Execute メソッドのパラメーターとして指定されたファイルの適切なパスを指定します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-146">Specify the appropriate path for the files that are specified as parameters to the Execute method.</span></span>  
  
5.  <span data-ttu-id="1e4ad-147">上の VBScript コードを実行します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-147">Execute the VBScript code above.</span></span> <span data-ttu-id="1e4ad-148">XML 一括読み込みによって、XML ドキュメントが Cust テーブルと CustOrder テーブルに読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-148">XML Bulk Load loads the XML document into the Cust and CustOrder tables.</span></span>  
  
 <span data-ttu-id="1e4ad-149">これは、これと同等の XDR スキーマです。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-149">This is the equivalent XDR schema:</span></span>  
  
```  
<?xml version="1.0" ?>  
<Schema xmlns="urn:schemas-microsoft-com:xml-data"   
        xmlns:dt="urn:schemas-microsoft-com:xml:datatypes"    
        xmlns:sql="urn:schemas-microsoft-com:xml-sql" >   
   <ElementType name="CustomerID" dt:type="int" />  
   <ElementType name="CompanyName" dt:type="string" />  
   <ElementType name="City" dt:type="string" />  
  
   <ElementType name="ROOT" sql:is-constant="1">  
      <element type="Customers" />  
   </ElementType>  
  
   <ElementType name="Customers" sql:relation="Cust" >  
      <element type="CustomerID" sql:field="CustomerID" />  
      <element type="CompanyName" sql:field="CompanyName" />  
      <element type="City" sql:field="City" />  
      <element type="Order" >  
<sql:relationship  
                key-relation="Cust"  
                key="CustomerID"  
                foreign-key="CustomerID"  
                foreign-relation="CustOrder" />  
      </element>  
   </ElementType>  
    <ElementType name="Order" sql:relation="CustOrder" >  
      <AttributeType name="OrderID" />  
      <AttributeType name="CustomerID" />  
      <attribute type="OrderID" />  
      <attribute type="CustomerID" />  
    </ElementType>  
</Schema>  
```  
  
## <a name="c-using-chain-relationships-in-the-schema-to-bulk-load-xml"></a><span data-ttu-id="1e4ad-150">C.</span><span class="sxs-lookup"><span data-stu-id="1e4ad-150">C.</span></span> <span data-ttu-id="1e4ad-151">スキーマでチェーン リレーションシップを使用して XML の一括読み込みを行う</span><span class="sxs-lookup"><span data-stu-id="1e4ad-151">Using chain relationships in the schema to bulk load XML</span></span>  
 <span data-ttu-id="1e4ad-152">この例では、XML 一括読み込みにおいて、マッピング スキーマで指定されている M:N リレーションシップを使用し、M:N リレーションシップを表すテーブルにデータを読み込む方法を示します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-152">This example illustrates how the M:N relationship that is specified in the mapping schema is used by XML Bulk Load to load data in a table that represents an M:N relationship.</span></span>  
  
 <span data-ttu-id="1e4ad-153">たとえば、次の XSD スキーマを考えてみます。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-153">For example, consider this XSD schema:</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="OrderOD"  
          parent="Ord"  
          parent-key="OrderID"  
          child="OrderDetail"  
          child-key="OrderID" />  
  
    <sql:relationship name="ODProduct"  
          parent="OrderDetail"  
          parent-key="ProductID"  
          child="Product"  
          child-key="ProductID"   
          inverse="true"/>  
  </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="ROOT" sql:is-constant="1" >  
    <xsd:complexType>  
      <xsd:sequence>  
        <xsd:element name="Order"   
                     sql:relation="Ord"   
                     sql:key-fields="OrderID" >  
          <xsd:complexType>  
            <xsd:sequence>  
             <xsd:element name="Product"  
                          sql:relation="Product"   
                          sql:key-fields="ProductID"  
                          sql:relationship="OrderOD ODProduct">  
               <xsd:complexType>  
                 <xsd:attribute name="ProductID" type="xsd:int" />  
                 <xsd:attribute name="ProductName" type="xsd:string" />  
               </xsd:complexType>  
             </xsd:element>  
           </xsd:sequence>  
           <xsd:attribute name="OrderID"   type="xsd:integer" />   
           <xsd:attribute name="CustomerID"   type="xsd:string" />  
         </xsd:complexType>  
       </xsd:element>  
      </xsd:sequence>  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 <span data-ttu-id="1e4ad-154">スキーマでは、 **\<Order>** 子要素を持つ要素を指定し **\<Product>** ます。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-154">The schema specifies an **\<Order>** element with a **\<Product>** child element.</span></span> <span data-ttu-id="1e4ad-155">**\<Order>** 要素は Ord テーブルにマップされ、 **\<Product>** 要素はデータベースの Product テーブルにマップされます。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-155">The **\<Order>** element maps to Ord table and the **\<Product>** element maps to the Product table in the database.</span></span> <span data-ttu-id="1e4ad-156">要素に指定されたチェーンリレーションシップは、 **\<Product>** OrderDetail テーブルによって表される M:N リレーションシップを識別します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-156">The chain relationship specified on the **\<Product>** element identifies a M:N relationship represented by the OrderDetail table.</span></span> <span data-ttu-id="1e4ad-157">つまり、1 つの注文には複数の製品が含まれ、1 つの製品は複数の注文に含まれるという関係です。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-157">(An order can include many products, and a product can be included in many orders.)</span></span>  
  
 <span data-ttu-id="1e4ad-158">このスキーマで XML ドキュメントの一括読み込みを行うと、Ord テーブル、Product テーブル、および OrderDetail テーブルにレコードが追加されます。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-158">When you are bulk loading an XML document with this schema, records are added to the Ord, Product, and OrderDetail tables.</span></span>  
  
#### <a name="to-test-a-working-sample"></a><span data-ttu-id="1e4ad-159">実際のサンプルをテストするには</span><span class="sxs-lookup"><span data-stu-id="1e4ad-159">To test a working sample</span></span>  
  
1.  <span data-ttu-id="1e4ad-160">次の 3 つのテーブルを作成します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-160">Create three tables:</span></span>  
  
    ```  
    CREATE TABLE Ord (  
             OrderID     int  PRIMARY KEY,  
             CustomerID  varchar(5));  
    GO  
    CREATE TABLE Product (  
             ProductID   int PRIMARY KEY,  
             ProductName varchar(20));  
    GO  
    CREATE TABLE OrderDetail (  
           OrderID     int FOREIGN KEY REFERENCES Ord(OrderID),  
           ProductID   int FOREIGN KEY REFERENCES Product(ProductID),  
                       CONSTRAINT OD_key PRIMARY KEY (OrderID, ProductID));  
    GO  
    ```  
  
2.  <span data-ttu-id="1e4ad-161">この例の最初で提供されているスキーマを SampleSchema.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-161">Save the schema that is provided above in this example as SampleSchema.xml.</span></span>  
  
3.  <span data-ttu-id="1e4ad-162">次のサンプル XML データを SampleXMLData.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-162">Save the following sample XML data as SampleXMLData.xml:</span></span>  
  
    ```  
    <ROOT>    
      <Order OrderID="1" CustomerID="ALFKI">  
        <Product ProductID="1" ProductName="Chai" />  
        <Product ProductID="2" ProductName="Chang" />  
      </Order>  
      <Order OrderID="2" CustomerID="ANATR">  
        <Product ProductID="3" ProductName="Aniseed Syrup" />  
        <Product ProductID="4" ProductName="Gumbo Mix" />  
      </Order>  
    </ROOT>  
    ```  
  
4.  <span data-ttu-id="1e4ad-163">任意のテキスト エディターまたは XML エディターでファイルを作成し、ValidateAndBulkload.vbs として保存します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-163">Create a file in your preferred text or XML editor, and save it as ValidateAndBulkload.vbs.</span></span> <span data-ttu-id="1e4ad-164">このファイルに、このトピックの冒頭で示した VBScript コードを追加します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-164">To this file, add the VBScript code that is provided above at the beginning of this topic.</span></span> <span data-ttu-id="1e4ad-165">接続文字列は、適切なサーバー名とデータベース名に変更します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-165">Modify the connection string to provide the appropriate server and database name.</span></span> <span data-ttu-id="1e4ad-166">この例のソース コードで、次の行のコメント指定をはずします。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-166">Uncomment the following lines from the source code for this example.</span></span>  
  
    ```  
    objBL.CheckConstraints = True  
    objBL.Transaction=True  
    ```  
  
5.  <span data-ttu-id="1e4ad-167">VBScript コードを実行します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-167">Execute the VBScript code.</span></span> <span data-ttu-id="1e4ad-168">XML 一括読み込みによって、XML ドキュメントが Ord テーブルと Product テーブルに読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-168">XML Bulk Load loads the XML document into the Ord and Product tables.</span></span>  
  
## <a name="d-bulk-loading-in-identity-type-columns"></a><span data-ttu-id="1e4ad-169">D.</span><span class="sxs-lookup"><span data-stu-id="1e4ad-169">D.</span></span> <span data-ttu-id="1e4ad-170">ID 型の列に一括読み込みを行う</span><span class="sxs-lookup"><span data-stu-id="1e4ad-170">Bulk loading in identity type columns</span></span>  
 <span data-ttu-id="1e4ad-171">この例では、一括読み込みでの ID 型列の扱いについて説明します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-171">This example illustrates how bulk load handles identity type columns.</span></span> <span data-ttu-id="1e4ad-172">この例では、3 つのテーブル (Ord、Product、OrderDetail) にデータの一括読み込みが行われます。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-172">In the example, data is bulk loaded into three tables (Ord, Product, and OrderDetail).</span></span>  
  
 <span data-ttu-id="1e4ad-173">これらのテーブルには、次の条件が設定されています。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-173">In these tables:</span></span>  
  
-   <span data-ttu-id="1e4ad-174">Ord テーブルの OrderID は ID 型の列です。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-174">OrderID in the Ord table is an identity type column</span></span>  
  
-   <span data-ttu-id="1e4ad-175">Product テーブルの ProductID は ID 型の列です。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-175">ProductID in the Product table is an identity type column.</span></span>  
  
-   <span data-ttu-id="1e4ad-176">OrderDetail の OrderID および ProductID 列は、Ord テーブルおよび Product テーブル内の対応する主キー列を参照する外部キー列です。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-176">OrderID and ProductID columns in the OrderDetail are foreign key columns referring to corresponding primary key columns in the Ord and Product tables.</span></span>  
  
 <span data-ttu-id="1e4ad-177">この例のテーブル スキーマを次に示します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-177">The following are the table schemas for this example:</span></span>  
  
```  
Ord (OrderID, CustomerID)  
Product (ProductID, ProductName)  
OrderDetail (OrderID, ProductID)  
```  
  
 <span data-ttu-id="1e4ad-178">この XML 一括読み込みの例では、BulkLoad オブジェクトモデルの KeepIdentity プロパティが false に設定されています。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-178">In this example of XML Bulk Load, the KeepIdentity property of the BulkLoad object model is set to false.</span></span> <span data-ttu-id="1e4ad-179">このため、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] では、Product テーブルおよび Ord テーブルの ProductID 列および OrderID 列に ID 値がそれぞれ生成されます。一括読み込みの対象ドキュメントで指定されている値は無視されます。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-179">Therefore, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] generates identity values for the ProductID and OrderID columns in the Product and Ord tables, respectively (any values provided in the documents to be bulk loaded are ignored).</span></span>  
  
 <span data-ttu-id="1e4ad-180">この場合、XML 一括読み込みでは、テーブル間の主キー/外部キーのリレーションシップが識別されます。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-180">In this case, XML Bulk Load identifies the primary key/foreign key relationship among tables.</span></span> <span data-ttu-id="1e4ad-181">一括読み込みでは、主キーのあるテーブルにレコードが挿入された後、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] で生成された ID 値が、外部キー列のあるテーブルに格納されます。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-181">Bulk Load first inserts records in the tables with the primary key, then propagates the identity value generated by [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to the tables with foreign key columns.</span></span> <span data-ttu-id="1e4ad-182">次の XML 一括読み込みの例では、次の順序でテーブルにデータが挿入されます。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-182">In the following example, XML Bulk Load inserts data in tables in this order:</span></span>  
  
1.  <span data-ttu-id="1e4ad-183">Product</span><span class="sxs-lookup"><span data-stu-id="1e4ad-183">Product</span></span>  
  
2.  <span data-ttu-id="1e4ad-184">Ord</span><span class="sxs-lookup"><span data-stu-id="1e4ad-184">Ord</span></span>  
  
3.  <span data-ttu-id="1e4ad-185">OrderDetail</span><span class="sxs-lookup"><span data-stu-id="1e4ad-185">OrderDetail</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="1e4ad-186">この処理ロジックでは、Products テーブルと Orders テーブルで生成された ID 値を後で OrderDetails テーブルに挿入できるよう、XML 一括読み込みによってこれらの値が保持されます。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-186">In order to propagate identity values generated in the Products and Orders tables, the processing logic requires XML Bulk Load to keep track of these values for later insertion into the OrderDetails table.</span></span> <span data-ttu-id="1e4ad-187">これにはまず、XML 一括読み込みで中間テーブルが作成され、このテーブルにデータが格納されます。格納された値は、後で削除されます。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-187">To do that, XML Bulk Load creates intermediate tables, populates the data in these tables, and later removes them.</span></span>  
  
#### <a name="to-test-a-working-sample"></a><span data-ttu-id="1e4ad-188">実際のサンプルをテストするには</span><span class="sxs-lookup"><span data-stu-id="1e4ad-188">To test a working sample</span></span>  
  
1.  <span data-ttu-id="1e4ad-189">次のテーブルを作成します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-189">Create these tables:</span></span>  
  
    ```  
    CREATE TABLE Ord (  
             OrderID     int identity(1,1)  PRIMARY KEY,  
             CustomerID  varchar(5));  
    GO  
    CREATE TABLE Product (  
             ProductID   int identity(1,1) PRIMARY KEY,  
             ProductName varchar(20));  
    GO  
    CREATE TABLE OrderDetail (  
           OrderID     int FOREIGN KEY REFERENCES Ord(OrderID),  
           ProductID   int FOREIGN KEY REFERENCES Product(ProductID),  
                       CONSTRAINT OD_key PRIMARY KEY (OrderID, ProductID));  
    GO  
    ```  
  
2.  <span data-ttu-id="1e4ad-190">任意のテキスト エディターまたは XML エディターでファイルを作成し、SampleSchema.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-190">Create a file in your preferred text or XML editor, and save it as SampleSchema.xml.</span></span> <span data-ttu-id="1e4ad-191">この XSD スキーマをこのファイルに追加します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-191">Add this XSD schema to this file.</span></span>  
  
    ```  
    <xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
                xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
     <xsd:annotation>  
       <xsd:appinfo>  
        <sql:relationship name="OrderOD"  
              parent="Ord"  
              parent-key="OrderID"  
              child="OrderDetail"  
              child-key="OrderID" />  
        <sql:relationship name="ODProduct"  
              parent="OrderDetail"  
              parent-key="ProductID"  
              child="Product"  
              child-key="ProductID"   
              inverse="true"/>  
       </xsd:appinfo>  
     </xsd:annotation>  
  
      <xsd:element name="Order" sql:relation="Ord"   
                                sql:key-fields="OrderID" >  
       <xsd:complexType>  
         <xsd:sequence>  
            <xsd:element name="Product" sql:relation="Product"   
                         sql:key-fields="ProductID"  
                         sql:relationship="OrderOD ODProduct">  
              <xsd:complexType>  
                 <xsd:attribute name="ProductID" type="xsd:int" />  
                 <xsd:attribute name="ProductName" type="xsd:string" />  
              </xsd:complexType>  
            </xsd:element>  
         </xsd:sequence>  
            <xsd:attribute name="OrderID"   type="xsd:integer" />   
            <xsd:attribute name="CustomerID"   type="xsd:string" />  
        </xsd:complexType>  
      </xsd:element>  
    </xsd:schema>  
    ```  
  
3.  <span data-ttu-id="1e4ad-192">任意のテキスト エディターまたは XML エディターでファイルを作成し、SampleXMLData.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-192">Create a file in your preferred text or XML editor, and save it as SampleXMLData.xml.</span></span> <span data-ttu-id="1e4ad-193">次の XML ドキュメントを追加します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-193">Add the following XML document.</span></span>  
  
    ```  
    <ROOT>    
      <Order OrderID="11" CustomerID="ALFKI">  
        <Product ProductID="11" ProductName="Chai" />  
        <Product ProductID="22" ProductName="Chang" />  
      </Order>  
      <Order OrderID="22" CustomerID="ANATR">  
         <Product ProductID="33" ProductName="Aniseed Syrup" />  
        <Product ProductID="44" ProductName="Gumbo Mix" />  
      </Order>  
    </ROOT>  
    ```  
  
4.  <span data-ttu-id="1e4ad-194">任意のテキスト エディターまたは XML エディターでファイルを作成し、ValidateAndBulkload.vbs として保存します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-194">Create a file in your preferred text or XML editor, and save it as ValidateAndBulkload.vbs.</span></span> <span data-ttu-id="1e4ad-195">このファイルに次の VBScript コードを追加します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-195">To this file, add the following VBScript code.</span></span> <span data-ttu-id="1e4ad-196">接続文字列は、適切なサーバー名とデータベース名に変更します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-196">Modify the connection string to provide the appropriate server and database name.</span></span> <span data-ttu-id="1e4ad-197">メソッドのパラメーターとして機能するファイルの適切なパスを指定し `Execute` ます。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-197">Specify the appropriate path for the files that serve as parameters to the `Execute` method.</span></span>  
  
    ```  
    Set objBL = CreateObject("SQLXMLBulkLoad.SQLXMLBulkload.4.0")  
    objBL.ConnectionString = "provider=SQLOLEDB;data source=localhost;database=tempdb;integrated security=SSPI"  
    objBL.ErrorLogFile = "C:\error.log"  
    objBL.CheckConstraints = True  
    objBL.Transaction = False  
    objBL.KeepIdentity = False  
    objBL.Execute "SampleSchema.xml", "SampleXMLData.xml"  
    Set objBL = Nothing  
    MsgBox "Done."  
    ```  
  
5.  <span data-ttu-id="1e4ad-198">VBScript コードを実行します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-198">Execute the VBScript code.</span></span> <span data-ttu-id="1e4ad-199">XML 一括読み込みによって、適切なテーブルにデータが読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-199">The XML Bulk Load will load the data into the appropriate tables.</span></span>  
  
## <a name="e-generating-table-schemas-before-bulk-loading"></a><span data-ttu-id="1e4ad-200">E.</span><span class="sxs-lookup"><span data-stu-id="1e4ad-200">E.</span></span> <span data-ttu-id="1e4ad-201">一括読み込み前にテーブル スキーマを生成する</span><span class="sxs-lookup"><span data-stu-id="1e4ad-201">Generating table schemas before bulk loading</span></span>  
 <span data-ttu-id="1e4ad-202">一括読み込み前にテーブルが存在しない場合、XML 一括読み込みでテーブルを作成するように指定できます。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-202">XML Bulk Load can optionally generate the tables if they do not exist before bulk loading.</span></span> <span data-ttu-id="1e4ad-203">SQLXMLBulkLoad オブジェクトの SchemaGen プロパティを TRUE に設定すると、これが行われます。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-203">Setting the SchemaGen property of the SQLXMLBulkLoad object to TRUE does this.</span></span> <span data-ttu-id="1e4ad-204">また、必要に応じて、SGDropTables プロパティを TRUE に設定して、既存のテーブルを削除して再作成するために、XML 一括読み込みを要求することもできます。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-204">You can also optionally request XML Bulk Load to drop any existing tables and re-create them by setting the SGDropTables property to TRUE.</span></span> <span data-ttu-id="1e4ad-205">次の VBScript の例では、これらのプロパティの使用法を示します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-205">The following VBScript example illustrates the use of these properties.</span></span>  
  
 <span data-ttu-id="1e4ad-206">また、この例では、これらの他に次の 2 つのプロパティを TRUE に設定します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-206">Also, this example sets two additional properties to TRUE:</span></span>  
  
-   <span data-ttu-id="1e4ad-207">CheckConstraints.</span><span class="sxs-lookup"><span data-stu-id="1e4ad-207">CheckConstraints.</span></span> <span data-ttu-id="1e4ad-208">: このプロパティを TRUE に設定すると、テーブルに指定されている制約違反が、テーブルに挿入されるデータによって発生するのを回避できます。この場合の制約は、Cust テーブルと CustOrder テーブル間に指定されている PRIMARY KEY/FOREIGN KEY 制約です。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-208">Setting this property to TRUE ensures that the data being inserted into the tables does not violate any constraints that have been specified on the tables (in this case the PRIMARY KEY/FOREIGN KEY constraints specified between the Cust and CustOrder tables).</span></span> <span data-ttu-id="1e4ad-209">制約違反が発生すると、一括読み込みは失敗します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-209">If there is a constraint violation, the bulk load fails.</span></span>  
  
-   <span data-ttu-id="1e4ad-210">XMLFragment.</span><span class="sxs-lookup"><span data-stu-id="1e4ad-210">XMLFragment.</span></span> <span data-ttu-id="1e4ad-211">: サンプル XML ドキュメント (データ ソース) はフラグメントであり、単一の最上位要素が含まれていません。したがって、このプロパティを TRUE に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-211">This property must be set to TRUE because the sample XML document (data source) contains no single, top-level element (and is thus a fragment).</span></span>  
  
 <span data-ttu-id="1e4ad-212">この VBScript コードは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-212">This is the VBScript code:</span></span>  
  
```  
Dim objBL   
Set objBL = CreateObject("SQLXMLBulkLoad.SQLXMLBulkload.4.0")  
objBL.ConnectionString = "provider=SQLOLEDB;data source=localhost;database=tempdb;integrated security=SSPI"  
objBL.ErrorLogFile = "c:\error.log"  
  
objBL.CheckConstraints=true  
objBL.XMLFragment = True  
objBL.SchemaGen = True  
objBL.SGDropTables = True  
  
objBL.Execute "SampleSchema.xml", "SampleXMLData.xml"  
Set objBL = Nothing  
```  
  
#### <a name="to-test-a-working-sample"></a><span data-ttu-id="1e4ad-213">実際のサンプルをテストするには</span><span class="sxs-lookup"><span data-stu-id="1e4ad-213">To test a working sample</span></span>  
  
1.  <span data-ttu-id="1e4ad-214">任意のテキスト エディターまたは XML エディターでファイルを作成し、SampleSchema.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-214">Create a file in your preferred text or XML editor, and save it as SampleSchema.xml.</span></span> <span data-ttu-id="1e4ad-215">このファイルに、前の例「スキーマでチェーン リレーションシップを使用して XML の一括読み込みを行う」で示した XSD スキーマを追加します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-215">Add the XSD schema that is provided in the earlier example, "Using chain relationships in the schema to bulk load XML", to the file.</span></span>  
  
2.  <span data-ttu-id="1e4ad-216">任意のテキスト エディターまたは XML エディターでファイルを作成し、SampleXMLData.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-216">Create a file in your preferred text or XML editor, and save it as SampleXMLData.xml.</span></span> <span data-ttu-id="1e4ad-217">このファイルに、前の例「スキーマでチェーン リレーションシップを使用して XML の一括読み込みを行う」で示した XML ドキュメントを追加します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-217">Add the XML document that is provided in the earlier example, "Using chain relationships in the schema to bulk load XML", to the file.</span></span> <span data-ttu-id="1e4ad-218">\<ROOT>ドキュメントから要素を削除します (フラグメントにするため)。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-218">Remove the \<ROOT> element from the document (to make it a fragment).</span></span>  
  
3.  <span data-ttu-id="1e4ad-219">任意のテキスト エディターまたは XML エディターでファイルを作成し、ValidateAndBulkload.vbs として保存します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-219">Create a file in your preferred text or XML editor, and save it as ValidateAndBulkload.vbs.</span></span> <span data-ttu-id="1e4ad-220">このファイルに、この例で示した VBScript コードを追加します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-220">To this file, add the VBScript code in this example.</span></span> <span data-ttu-id="1e4ad-221">接続文字列は、適切なサーバー名とデータベース名に変更します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-221">Modify the connection string to provide the appropriate server and database name.</span></span> <span data-ttu-id="1e4ad-222">Execute メソッドのパラメーターとして指定されたファイルの適切なパスを指定します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-222">Specify the appropriate path for the files that are specified as parameters to the Execute method.</span></span>  
  
4.  <span data-ttu-id="1e4ad-223">VBScript コードを実行します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-223">Execute the VBScript code.</span></span> <span data-ttu-id="1e4ad-224">XML 一括読み込みによって、指定されたマッピング スキーマを基に必要なテーブルが作成され、このテーブルにデータの一括読み込みが行われます。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-224">The XML Bulk Load creates the necessary tables on the basis of the mapping schema that is provided and bulk loads the data in it.</span></span>  
  
## <a name="f-bulk-loading-from-a-stream"></a><span data-ttu-id="1e4ad-225">F.</span><span class="sxs-lookup"><span data-stu-id="1e4ad-225">F.</span></span> <span data-ttu-id="1e4ad-226">ストリームから一括読み込みを行う</span><span class="sxs-lookup"><span data-stu-id="1e4ad-226">Bulk loading from a stream</span></span>  
 <span data-ttu-id="1e4ad-227">XML 一括読み込みオブジェクトモデルの Execute メソッドには、2つのパラメーターがあります。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-227">The Execute method of the XML Bulk Load object model takes two parameters.</span></span> <span data-ttu-id="1e4ad-228">最初のパラメーターはマッピング スキーマ ファイルであり、</span><span class="sxs-lookup"><span data-stu-id="1e4ad-228">The first parameter is the mapping schema file.</span></span> <span data-ttu-id="1e4ad-229">もう 1 つのパラメーターは、データベースに読み込まれる XML データを指定するものです。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-229">The second parameter provides the XML data that is to be loaded in the database.</span></span> <span data-ttu-id="1e4ad-230">Xml データを XML 一括読み込みの Execute メソッドに渡すには、次の2つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-230">There are two ways to pass the XML data to the Execute method of XML Bulk Load:</span></span>  
  
-   <span data-ttu-id="1e4ad-231">ファイル名をパラメーターとして指定する。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-231">Specify the file name as the parameter.</span></span>  
  
-   <span data-ttu-id="1e4ad-232">XML データを含むストリームを渡す。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-232">Pass a stream that contains the XML data.</span></span>  
  
 <span data-ttu-id="1e4ad-233">この例では、ストリームから一括読み込みを行う方法を示します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-233">This example illustrates how to bulk load from a stream.</span></span>  
  
 <span data-ttu-id="1e4ad-234">VBScript はまず SELECT ステートメントが実行され、Northwind データベースの Customers テーブルから顧客情報が取得されます。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-234">VBScript first executes a SELECT statement to retrieve customer information from the Customers table in the Northwind database.</span></span> <span data-ttu-id="1e4ad-235">SELECT ステートメントには、FOR XML 句 (と ELEMENTS オプション) が指定されているため、クエリを実行すると、次の形式の、要素中心の XML ドキュメントが返されます。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-235">Because the FOR XML clause is specified (with the ELEMENTS option) in the SELECT statement, the query returns an element-centric XML document of this form:</span></span>  
  
```  
<Customer>  
  <CustomerID>..</CustomerID>  
  <CompanyName>..</CompanyName>  
  <City>..</City>  
</Customer>  
...  
```  
  
 <span data-ttu-id="1e4ad-236">次に、スクリプトは、2番目のパラメーターとして XML をストリームとして Execute メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-236">The script then passes the XML as a stream to the Execute method as its second parameter.</span></span> <span data-ttu-id="1e4ad-237">Execute メソッドは、Cust テーブルにデータを一括読み込みします。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-237">The Execute method bulk loads the data into the Cust table.</span></span>  
  
 <span data-ttu-id="1e4ad-238">このスクリプトは、SchemaGen プロパティを TRUE に設定し、SGDropTables プロパティを TRUE に設定するため、XML 一括読み込みでは、指定されたデータベースに Cust テーブルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-238">Because this script sets the SchemaGen property to TRUE and SGDropTables property to TRUE, XML Bulk Load creates the Cust table in the specified database.</span></span> <span data-ttu-id="1e4ad-239">テーブルが存在する場合は、最初にテーブルが削除された後に再作成されます。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-239">(If the table already exists, it first drops the table and then re-creates it.)</span></span>  
  
 <span data-ttu-id="1e4ad-240">この VBScript の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-240">This is the VBScript example:</span></span>  
  
```  
Set objBL = CreateObject("SQLXMLBulkLoad.SQLXMLBulkload.4.0")  
Set objCmd = CreateObject("ADODB.Command")  
Set objConn = CreateObject("ADODB.Connection")  
Set objStrmOut = CreateObject ("ADODB.Stream")  
  
objBL.ConnectionString = "provider=SQLOLEDB;data source=localhost;database=tempdb;integrated security=SSPI"  
objBL.ErrorLogFile     = "c:\error.log"  
objBL.CheckConstraints = True  
objBL.SchemaGen        = True  
objBL.SGDropTables     = True  
objBL.XMLFragment      = True  
' Open a connection to the instance of SQL Server to get the source data.  
  
objConn.Open "provider=SQLOLEDB;server=(local);database=tempdb;integrated security=SSPI"  
Set objCmd.ActiveConnection = objConn  
objCmd.CommandText = "SELECT CustomerID, CompanyName, City FROM Customers FOR XML AUTO, ELEMENTS"  
  
' Open the return stream and execute the command.  
Const adCRLF = -1  
Const adExecuteStream = 1024  
objStrmOut.Open  
objStrmOut.LineSeparator = adCRLF  
objCmd.Properties("Output Stream").Value = objStrmOut  
objCmd.Execute , , adExecuteStream  
objStrmOut.Position = 0  
  
' Execute bulk load. Read source XML data from the stream.  
objBL.Execute "SampleSchema.xml", objStrmOut  
  
Set objBL = Nothing  
```  
  
 <span data-ttu-id="1e4ad-241">次の XSD マッピング スキーマでは、テーブルの作成に必要な情報が指定されます。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-241">The following XSD mapping schema provides the necessary information to create the table:</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:element name="ROOT" sql:is-constant="true" >  
  <xsd:complexType>  
    <xsd:sequence>  
      <xsd:element ref="Customers"/>  
    </xsd:sequence>  
  </xsd:complexType>  
</xsd:element>  
<xsd:element name="Customers" sql:relation="Cust" >  
  <xsd:complexType>  
    <xsd:sequence>  
      <xsd:element name="CustomerID"  
                   type="xsd:string"  
                   sql:datatype="nvarchar(5)"/>  
      <xsd:element name="CompanyName"  
                   type="xsd:string"  
                   sql:datatype="nvarchar(40)"/>  
      <xsd:element name="City"  
                   type="xsd:string"  
                   sql:datatype="nvarchar(40)"/>  
    </xsd:sequence>  
  </xsd:complexType>  
</xsd:element>  
</xsd:schema>  
```  
  
 <span data-ttu-id="1e4ad-242">XDR スキーマの場合は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-242">This is equivalent XDR schema:</span></span>  
  
```  
<?xml version="1.0" ?>  
<Schema xmlns="urn:schemas-microsoft-com:xml-data"   
        xmlns:dt="urn:schemas-microsoft-com:xml:datatypes"    
        xmlns:sql="urn:schemas-microsoft-com:xml-sql" >  
   <ElementType name="CustomerID" dt:type="int" />  
   <ElementType name="CompanyName" dt:type="string" />  
   <ElementType name="City" dt:type="string" />  
  
   <ElementType name="root" sql:is-constant="1">  
      <element type="Customers" />  
   </ElementType>  
  
   <ElementType name="Customers" sql:relation="Cust"  >  
      <element type="CustomerID" sql:field="CustomerID" />  
      <element type="CompanyName" sql:field="CompanyName" />  
      <element type="City" sql:field="City" />  
    </ElementType>  
</Schema>  
```  
  
### <a name="opening-a-stream-on-an-existing-file"></a><span data-ttu-id="1e4ad-243">既存のファイルのストリームを開く</span><span class="sxs-lookup"><span data-stu-id="1e4ad-243">Opening a Stream on an Existing File</span></span>  
 <span data-ttu-id="1e4ad-244">また、既存の XML データファイルでストリームを開き、パラメーターとしてストリームをパラメーターとして渡すこともできます (ファイル名をパラメーターとして渡すのではなく)。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-244">You can also open a stream on an existing XML data file and pass the stream as a parameter to the Execute method (instead of passing the file name as the parameter).</span></span>  
  
 <span data-ttu-id="1e4ad-245">ストリームをパラメーターとして渡す Visual Basic の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-245">This is a Visual Basic example of passing a stream as the parameter:</span></span>  
  
```  
Private Sub Form_Load()  
Dim objBL As New SQLXMLBulkLoad  
Dim objStrm As New ADODB.Stream  
Dim objFileSystem As New Scripting.FileSystemObject  
Dim objFile As Scripting.TextStream  
  
MsgBox "Begin BulkLoad..."  
objBL.ConnectionString = "provider=SQLOLEDB;data source=localhost;database=tempdb;integrated security=SSPI"  
objBL.ErrorLogFile = "c:\error.log"  
objBL.CheckConstraints = True  
objBL.SchemaGen = True  
objBL.SGDropTables = True  
' Here again a stream is specified that contains the source data   
' (instead of the file name). But this is just an illustration.  
' Usually this is useful if you have an XML data   
' stream that is created by some other means that you want to bulk   
' load. This example starts with an XML text file, so it may not be the   
' best to use a stream (you can specify the file name directly).  
' Here you could have specified the file name itself.   
Set objFile = objFileSystem.OpenTextFile("c:\SampleData.xml")  
objStrm.Open  
objStrm.WriteText objFile.ReadAll  
objStrm.Position = 0  
objBL.Execute "c:\SampleSchema.xml", objStrm  
  
Set objBL = Nothing  
MsgBox "Done."  
End Sub  
```  
  
 <span data-ttu-id="1e4ad-246">アプリケーションをテストするには、次の XML ドキュメントをファイル (SampleData.xml) に保存し、この例で提供されている XSD スキーマと共に使用します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-246">To test the application, use the following XML document in a file (SampleData.xml) and the XSD schema that is provided in this example:</span></span>  
  
 <span data-ttu-id="1e4ad-247">XML ソース データ (SampleData.xml) は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-247">This is the XML source data (SampleData.xml):</span></span>  
  
```  
<ROOT>  
  <Customers>  
    <CustomerID>1111</CustomerID>  
    <CompanyName>Hanari Carnes</CompanyName>  
    <City>NY</City>  
    <Order OrderID="1" />  
    <Order OrderID="2" />  
  </Customers>  
  
  <Customers>  
    <CustomerID>1112</CustomerID>  
    <CompanyName>Toms Spezialitten</CompanyName>  
     <City>LA</City>  
    <Order OrderID="3" />  
  </Customers>  
  <Customers>  
    <CustomerID>1113</CustomerID>  
    <CompanyName>Victuailles en stock</CompanyName>  
    <Order CustomerID= "4444" OrderID="4" />  
</Customers>  
</ROOT>  
```  
  
 <span data-ttu-id="1e4ad-248">これは、これと同等の XDR スキーマです。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-248">This is the equivalent XDR schema:</span></span>  
  
```  
<?xml version="1.0" ?>  
<Schema xmlns="urn:schemas-microsoft-com:xml-data"   
        xmlns:dt="urn:schemas-microsoft-com:xml:datatypes"    
        xmlns:sql="urn:schemas-microsoft-com:xml-sql" >  
  
    <ElementType name="Order" sql:relation="CustOrder" >  
      <AttributeType name="OrderID" />  
      <AttributeType name="CustomerID" />  
      <attribute type="OrderID" />  
      <attribute type="CustomerID" />  
    </ElementType>  
  
   <ElementType name="CustomerID" dt:type="int" />  
   <ElementType name="CompanyName" dt:type="string" />  
   <ElementType name="City" dt:type="string" />  
  
   <ElementType name="root" sql:is-constant="1">  
      <element type="Customers" />  
   </ElementType>  
  
   <ElementType name="Customers" sql:relation="Cust"  >  
      <element type="CustomerID" sql:field="CustomerID" />  
      <element type="CompanyName" sql:field="CompanyName" />  
      <element type="City" sql:field="City" />  
      <element type="Order" >  
             <sql:relationship  
                key-relation="Cust"  
                key="CustomerID"  
                foreign-key="CustomerID"  
                foreign-relation="CustOrder" />  
      </element>  
   </ElementType>  
</Schema>  
```  
  
## <a name="g-bulk-loading-in-overflow-columns"></a><span data-ttu-id="1e4ad-249">G.</span><span class="sxs-lookup"><span data-stu-id="1e4ad-249">G.</span></span> <span data-ttu-id="1e4ad-250">オーバーフロー列に一括読み込みを行う</span><span class="sxs-lookup"><span data-stu-id="1e4ad-250">Bulk loading in overflow columns</span></span>  
 <span data-ttu-id="1e4ad-251">マッピング スキーマで、`sql:overflow-field` 注釈によってオーバーフロー列が指定されている場合、XML 一括読み込みではソース ドキュメントからこの列にすべての未使用データがコピーされます。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-251">If the mapping schema specifies an overflow column by using the `sql:overflow-field` annotation, XML Bulk Load copies all unconsumed data from the source document into this column.</span></span>  
  
 <span data-ttu-id="1e4ad-252">次の XSD スキーマを考えてみます。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-252">Consider this XSD schema:</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="CustCustOrder"  
          parent="Cust"  
          parent-key="CustomerID"  
          child="CustOrder"  
          child-key="CustomerID" />  
  </xsd:appinfo>  
</xsd:annotation>  
  <xsd:element name="Customers" sql:relation="Cust"  
                                sql:overflow-field="OverflowColumn" >  
   <xsd:complexType>  
     <xsd:sequence>  
       <xsd:element name="CustomerID"  type="xsd:integer" />  
       <xsd:element name="CompanyName" type="xsd:string" />  
       <xsd:element name="City"        type="xsd:string" />  
       <xsd:element name="Order"   
                          sql:relation="CustOrder"  
                          sql:relationship="CustCustOrder" >  
         <xsd:complexType>  
          <xsd:attribute name="OrderID" type="xsd:integer" />  
          <xsd:attribute name="CustomerID" type="xsd:integer" />  
         </xsd:complexType>  
       </xsd:element>  
     </xsd:sequence>  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 <span data-ttu-id="1e4ad-253">このスキーマでは、Cust テーブルにオーバーフロー列 (OverflowColumn) が指定されています。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-253">The schema identifies an overflow column (OverflowColumn) for the Cust table.</span></span> <span data-ttu-id="1e4ad-254">その結果、各要素のすべての未使用 XML データ **\<Customer>** がこの列に追加されます。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-254">As a result, all unconsumed XML data for each **\<Customer>** element is added to this column.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1e4ad-255">すべての抽象要素 ( **abstract = "true"** が指定されている要素) と、禁止されているすべての属性 ( **"true"** が指定されている属性) は、XML 一括読み込みによってオーバーフローと見なされ、指定されている場合はオーバーフロー列に追加されます。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-255">All abstract elements (elements for which **abstract="true"** is specified) and all prohibited attributes (attributes for which **prohibited="true"** is specified) are considered overflow by XML Bulk Load and are added to the overflow column, if specified.</span></span> <span data-ttu-id="1e4ad-256">それ以外の場合は無視されます。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-256">(Otherwise, they are ignored.)</span></span>  
  
#### <a name="to-test-a-working-sample"></a><span data-ttu-id="1e4ad-257">実際のサンプルをテストするには</span><span class="sxs-lookup"><span data-stu-id="1e4ad-257">To test a working sample</span></span>  
  
1.  <span data-ttu-id="1e4ad-258">**Tempdb**データベースに2つのテーブルを作成します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-258">Create two tables in **tempdb** database:</span></span>  
  
    ```  
    USE tempdb;  
    CREATE TABLE Cust (  
                  CustomerID     int         PRIMARY KEY,  
                  CompanyName    varchar(20) NOT NULL,  
                  City           varchar(20) DEFAULT 'Seattle',  
                  OverflowColumn nvarchar(200));  
    GO  
    CREATE TABLE CustOrder (  
                  OrderID    int PRIMARY KEY,  
                  CustomerID int FOREIGN KEY   
                                 REFERENCES Cust(CustomerID));  
    GO  
    ```  
  
2.  <span data-ttu-id="1e4ad-259">任意のテキスト エディターまたは XML エディターでファイルを作成し、SampleSchema.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-259">Create a file in your preferred text or XML editor, and save it as SampleSchema.xml.</span></span> <span data-ttu-id="1e4ad-260">このファイルに、この例で示した XSD スキーマを追加します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-260">Add the XSD schema that is provided in this example to the file.</span></span>  
  
3.  <span data-ttu-id="1e4ad-261">任意のテキスト エディターまたは XML エディターでファイルを作成し、SampleXMLData.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-261">Create a file in your preferred text or XML editor, and save it as SampleXMLData.xml.</span></span> <span data-ttu-id="1e4ad-262">このファイルに次の XML ドキュメントを追加します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-262">Add the following XML document to the file:</span></span>  
  
    ```  
    <ROOT>  
      <Customers>  
        <CustomerID>1111</CustomerID>  
        <CompanyName>Hanari Carnes</CompanyName>  
        <City><![CDATA[NY]]> </City>  
        <Junk>garbage in overflow</Junk>  
        <Order OrderID="1" />  
        <Order OrderID="2" />  
      </Customers>  
  
      <Customers>  
        <CustomerID>1112</CustomerID>  
        <CompanyName>Toms Spezialitten</CompanyName>  
         <![CDATA[LA]]>   
        <!-- <xyz><address>111 Maple, Seattle</address></xyz>   -->  
        <Order OrderID="3" />  
      </Customers>  
      <Customers>  
        <CustomerID>1113</CustomerID>  
        <CompanyName>Victuailles en stock</CompanyName>  
        <Order OrderID="4" />  
    </Customers>  
    </ROOT>  
    ```  
  
4.  <span data-ttu-id="1e4ad-263">任意のテキスト エディターまたは XML エディターでファイルを作成し、ValidateAndBulkload.vbs として保存します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-263">Create a file in your preferred text or XML editor, and save it as ValidateAndBulkload.vbs.</span></span> <span data-ttu-id="1e4ad-264">このファイルに次の Microsoft Visual Basic Scripting Edition (VBScript) コードを追加します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-264">To this file, add the following Microsoft Visual Basic Scripting Edition (VBScript) code.</span></span> <span data-ttu-id="1e4ad-265">接続文字列は、適切なサーバー名とデータベース名に変更します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-265">Modify the connection string to provide the appropriate server and database name.</span></span> <span data-ttu-id="1e4ad-266">Execute メソッドのパラメーターとして指定されたファイルの適切なパスを指定します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-266">Specify the appropriate path for the files that are specified as parameters to the Execute method.</span></span>  
  
    ```  
    set objBL = CreateObject("SQLXMLBulkLoad.SQLXMLBulkload.4.0")  
    objBL.ConnectionString = "provider=SQLOLEDB;data source=localhost;database=tempdb;integrated security=SSPI"  
    objBL.ErrorLogFile = "c:\error.log"  
    objBL.CheckConstraints = True  
    objBL.Execute "SampleSchema.xml", "SampleXMLData.xml"  
    set objBL=Nothing  
    ```  
  
5.  <span data-ttu-id="1e4ad-267">VBScript コードを実行します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-267">Execute the VBScript code.</span></span>  
  
 <span data-ttu-id="1e4ad-268">これは、これと同等の XDR スキーマです。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-268">This is the equivalent XDR schema:</span></span>  
  
```  
<?xml version="1.0" ?>  
<Schema xmlns="urn:schemas-microsoft-com:xml-data"   
        xmlns:dt="urn:schemas-microsoft-com:xml:datatypes"    
        xmlns:sql="urn:schemas-microsoft-com:xml-sql" >  
  
    <ElementType name="Order" sql:relation="CustOrder" >  
      <AttributeType name="OrderID" />  
      <AttributeType name="CustomerID" />  
      <attribute type="OrderID" />  
      <attribute type="CustomerID" />  
    </ElementType>  
  
   <ElementType name="CustomerID" dt:type="int" />  
   <ElementType name="CompanyName" dt:type="string" />  
   <ElementType name="City" dt:type="string" />  
  
   <ElementType name="root" sql:is-constant="1">  
      <element type="Customers" />  
   </ElementType>  
  
   <ElementType name="Customers" sql:relation="Cust"   
                       sql:overflow-field="OverflowColumn"  >  
      <element type="CustomerID" sql:field="CustomerID" />  
      <element type="CompanyName" sql:field="CompanyName" />  
      <element type="City" sql:field="City" />  
      <element type="Order" >  
             <sql:relationship  
                key-relation="Cust"  
                key="CustomerID"  
                foreign-key="CustomerID"  
                foreign-relation="CustOrder" />  
      </element>  
   </ElementType>  
</Schema>  
```  
  
## <a name="h-specifying-the-file-path-for-temp-files-in-transaction-mode"></a><span data-ttu-id="1e4ad-269">H.</span><span class="sxs-lookup"><span data-stu-id="1e4ad-269">H.</span></span> <span data-ttu-id="1e4ad-270">トランザクション モードで一時ファイル用のファイル パスを指定する</span><span class="sxs-lookup"><span data-stu-id="1e4ad-270">Specifying the file path for temp files in transaction mode</span></span>  
 <span data-ttu-id="1e4ad-271">トランザクションモードで一括読み込みを行う場合 (つまり、Transaction プロパティが TRUE に設定されている場合)、次のいずれかの条件に該当する場合は、TempFilePath プロパティも設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-271">When you are bulk loading in transaction mode (that is, when the Transaction property is set to TRUE), you also must set the TempFilePath property when either of the following conditions is true:</span></span>  
  
-   <span data-ttu-id="1e4ad-272">リモート サーバーに一括読み込みを行う。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-272">You are bulk loading to a remote server.</span></span>  
  
-   <span data-ttu-id="1e4ad-273">トランザクション モードで作成される一時ファイルの格納に、TEMP 環境変数で指定されているパスとは別のローカル ドライブまたはフォルダーを使用する。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-273">You want to use an alternate local drive or folder (one other than the path that is specified by the TEMP environment variable) to store the temporary files that are created in the transaction mode.</span></span>  
  
 <span data-ttu-id="1e4ad-274">たとえば、次の VBScript コードでは、SampleXMLData.xml ファイルからデータベース テーブルに、トランザクション モードでデータの一括読み込みが行われます。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-274">For example, the following VBScript code bulk loads data from the SampleXMLData.xml file into the database tables in transaction mode.</span></span> <span data-ttu-id="1e4ad-275">TempFilePath プロパティは、トランザクションモードで生成される一時ファイルのパスを設定するために指定されます。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-275">The TempFilePath property is specified to set the path for the temporary files that are generated in transaction mode.</span></span>  
  
```  
set objBL = CreateObject("SQLXMLBulkLoad.SQLXMLBulkload.4.0")  
objBL.ConnectionString = "provider=SQLOLEDB;data source=localhost;database=tempdb;integrated security=SSPI"  
objBL.ErrorLogFile = "c:\error.log"  
objBL.CheckConstraints = True  
objBL.Transaction=True  
objBL.TempFilePath="\\Server\MyDir"  
objBL.Execute "SampleSchema.xml", "SampleXMLData.xml"  
set objBL=Nothing  
```  
  
> [!NOTE]  
>  <span data-ttu-id="1e4ad-276">一時ファイルのパスは、対象の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスのサービス アカウントと、一括読み込みアプリケーションを実行するアカウントからの共有アクセスが可能な場所にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-276">The temporary file path must be a shared location that is accessible to the service account of the target instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] and to the account that is running the bulk load application.</span></span> <span data-ttu-id="1e4ad-277">ローカルサーバーで一括読み込みを行う場合を除き、一時ファイルのパスは UNC パス (\servername\sharename など) である必要があり \\ ます。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-277">Unless you are bulk loading on a local server, the temporary file path must be a UNC path (such as \\\servername\sharename).</span></span>  
  
#### <a name="to-test-a-working-sample"></a><span data-ttu-id="1e4ad-278">実際のサンプルをテストするには</span><span class="sxs-lookup"><span data-stu-id="1e4ad-278">To test a working sample</span></span>  
  
1.  <span data-ttu-id="1e4ad-279">**Tempdb**データベースに次のテーブルを作成します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-279">Create this table in **tempdb** database:</span></span>  
  
    ```  
    USE tempdb;  
    CREATE TABLE Cust (     CustomerID uniqueidentifier,   
          LastName  varchar(20));  
    GO  
    ```  
  
2.  <span data-ttu-id="1e4ad-280">任意のテキスト エディターまたは XML エディターでファイルを作成し、SampleSchema.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-280">Create a file in your preferred text or XML editor, and save it as SampleSchema.xml.</span></span> <span data-ttu-id="1e4ad-281">次の XSD スキーマをファイルに追加します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-281">Add the following XSD schema to the file:</span></span>  
  
    ```  
    <xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
                xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
      <xsd:element name="ROOT" sql:is-constant="true" >  
        <xsd:complexType>  
          <xsd:sequence>  
            <xsd:element ref="Customers" />  
          </xsd:sequence>  
        </xsd:complexType>  
      </xsd:element>  
  
      <xsd:element name="Customers" sql:relation="Cust" >  
       <xsd:complexType>  
         <xsd:attribute name="CustomerID"  type="xsd:string" />  
         <xsd:attribute name="LastName" type="xsd:string" />  
       </xsd:complexType>  
      </xsd:element>  
    </xsd:schema>  
    ```  
  
3.  <span data-ttu-id="1e4ad-282">任意のテキスト エディターまたは XML エディターでファイルを作成し、SampleXMLData.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-282">Create a file in your preferred text or XML editor, and save it as SampleXMLData.xml.</span></span> <span data-ttu-id="1e4ad-283">このファイルに次の XML ドキュメントを追加します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-283">Add the following XML document to the file:</span></span>  
  
    ```  
    <ROOT>  
    <Customers CustomerID="6F9619FF-8B86-D011-B42D-00C04FC964FF"   
               LastName="Smith" />  
    </ROOT>  
    ```  
  
4.  <span data-ttu-id="1e4ad-284">任意のテキスト エディターまたは XML エディターでファイルを作成し、ValidateAndBulkload.vbs として保存します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-284">Create a file in your preferred text or XML editor, and save it as ValidateAndBulkload.vbs.</span></span> <span data-ttu-id="1e4ad-285">このファイルに次の VBScript コードを追加します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-285">To this file, add the following VBScript code.</span></span> <span data-ttu-id="1e4ad-286">接続文字列は、適切なサーバー名とデータベース名に変更します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-286">Modify the connection string to provide the appropriate server and database name.</span></span> <span data-ttu-id="1e4ad-287">Execute メソッドのパラメーターとして指定されたファイルの適切なパスを指定します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-287">Specify the appropriate path for the files that are specified as parameters to the Execute method.</span></span> <span data-ttu-id="1e4ad-288">また、TempFilePath プロパティに適切なパスを指定します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-288">Also specify the appropriate path for the TempFilePath property.</span></span>  
  
    ```  
    set objBL = CreateObject("SQLXMLBulkLoad.SQLXMLBulkload.4.0")  
    objBL.ConnectionString = "provider=SQLOLEDB;data source=localhost;database=tempdb;integrated security=SSPI"  
    objBL.ErrorLogFile = "c:\error.log"  
    objBL.CheckConstraints = True  
    objBL.Transaction=True  
    objBL.TempFilePath="\\server\folder"  
    objBL.Execute "SampleSchema.xml", "SampleXMLData.xml"  
    set objBL=Nothing  
    ```  
  
5.  <span data-ttu-id="1e4ad-289">VBScript コードを実行します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-289">Execute the VBScript code.</span></span>  
  
     <span data-ttu-id="1e4ad-290">`sql:datatype` **Customerid**の値が、次のような中かっこ ({および}) を含む GUID として指定されている場合は、スキーマで**customerid**属性に対応するを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-290">The schema must specify the corresponding `sql:datatype` for the **CustomerID** attribute when the value for **CustomerID** is specified as a GUID that includes braces ({ and }), such as:</span></span>  
  
    ```  
    <ROOT>  
    <Customers CustomerID="{6F9619FF-8B86-D011-B42D-00C04FC964FF}"   
               LastName="Smith" />  
    </ROOT>  
    ```  
  
     <span data-ttu-id="1e4ad-291">更新されたスキーマは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-291">This is the updated schema:</span></span>  
  
    ```  
    <xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
                xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
      <xsd:element name="ROOT" sql:is-constant="true" >  
        <xsd:complexType>  
          <xsd:sequence>  
            <xsd:element ref="Customers" />  
          </xsd:sequence>  
        </xsd:complexType>  
      </xsd:element>  
  
      <xsd:element name="Customers" sql:relation="Cust" >  
       <xsd:complexType>  
         <xsd:attribute name="CustomerID"  type="xsd:string"   
                        sql:datatype="uniqueidentifier" />  
         <xsd:attribute name="LastName" type="xsd:string" />  
       </xsd:complexType>  
      </xsd:element>  
    </xsd:schema>  
    ```  
  
     <span data-ttu-id="1e4ad-292">`sql:datatype`列の型がとして指定されている場合 `uniqueidentifier` 、一括読み込み操作では、列に挿入する前に、 **CustomerID**値から中かっこ ({および}) を削除します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-292">When `sql:datatype` is specified identifying the column type as `uniqueidentifier`, the bulk load operation removes the braces ({ and }) from the **CustomerID** value before inserting it in the column.</span></span>  
  
 <span data-ttu-id="1e4ad-293">これは、これと同等の XDR スキーマです。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-293">This is the equivalent XDR schema:</span></span>  
  
```  
<?xml version="1.0" ?>  
<Schema xmlns="urn:schemas-microsoft-com:xml-data"   
        xmlns:dt="urn:schemas-microsoft-com:datatypes"    
        xmlns:sql="urn:schemas-microsoft-com:xml-sql" >  
<ElementType name="ROOT" sql:is-constant="1">  
      <element type="Customers" />  
</ElementType>  
<ElementType name="Customers" sql:relation="Cust" >  
  <AttributeType name="CustomerID"  sql:datatype="uniqueidentifier" />  
  <AttributeType name="LastName"   />  
  
  <attribute type="CustomerID" />  
  <attribute type="LastName"   />  
</ElementType>  
</Schema>  
```  
  
## <a name="i-using-an-existing-database-connection-with-the-connectioncommand-property"></a><span data-ttu-id="1e4ad-294">I.</span><span class="sxs-lookup"><span data-stu-id="1e4ad-294">I.</span></span> <span data-ttu-id="1e4ad-295">既存のデータベース接続で ConnectionCommand プロパティを使用する</span><span class="sxs-lookup"><span data-stu-id="1e4ad-295">Using an existing database connection with the ConnectionCommand property</span></span>  
 <span data-ttu-id="1e4ad-296">既存の ADO 接続を使用して、XML の一括読み込みを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-296">You can use an existing ADO connection to bulk load XML.</span></span> <span data-ttu-id="1e4ad-297">これは、データ ソースに実行する多くの操作のうちの 1 つとして XML 一括読み込みを行う場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-297">This is useful if XML Bulk Load is just one of many operations that will be performed on a data source.</span></span>  
  
 <span data-ttu-id="1e4ad-298">ConnectionCommand プロパティを使用すると、ADO コマンドオブジェクトを使用して、既存の ADO 接続を使用できます。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-298">The ConnectionCommand property enables you to use an existing ADO connection by using an ADO command object.</span></span> <span data-ttu-id="1e4ad-299">この Visual Basic の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-299">This is illustrated in the following Visual Basic example:</span></span>  
  
```  
Private Sub Form_Load()  
Dim objBL As New SQLXMLBulkLoad4  
Dim objCmd As New ADODB.Command  
Dim objConn As New ADODB.Connection  
  
'Open a connection to an instance of SQL Server.  
objConn.Open "provider=SQLOLEDB;data source=(local);database=tempdb;integrated security=SSPI"  
'Ask the Command object to use the connection just established.  
Set objCmd.ActiveConnection = objConn  
  
'Tell Bulk Load to use the active command object that is using the Connection obj.  
objBL.ConnectionCommand = objCmd  
objBL.ErrorLogFile = "c:\error.log"  
objBL.CheckConstraints = True  
'The Transaction property must be set to True if you use ConnectionCommand.  
objBL.Transaction = True  
objBL.Execute "SampleSchema.xml", "SampleXMLData.xml"  
Set objBL = Nothing  
End Sub  
```  
  
#### <a name="to-test-a-working-sample"></a><span data-ttu-id="1e4ad-300">実際のサンプルをテストするには</span><span class="sxs-lookup"><span data-stu-id="1e4ad-300">To test a working sample</span></span>  
  
1.  <span data-ttu-id="1e4ad-301">**Tempdb**データベースに2つのテーブルを作成します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-301">Create two tables in **tempdb** database:</span></span>  
  
    ```  
    USE tempdb;  
    CREATE TABLE Cust(  
                   CustomerID   varchar(5) PRIMARY KEY,  
                   CompanyName  varchar(30),  
                   City         varchar(20));  
    GO  
    CREATE TABLE CustOrder(  
                   CustomerID  varchar(5) references Cust (CustomerID),  
                   OrderID     varchar(5) PRIMARY KEY);  
    GO  
    ```  
  
2.  <span data-ttu-id="1e4ad-302">任意のテキスト エディターまたは XML エディターでファイルを作成し、SampleSchema.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-302">Create a file in your preferred text or XML editor, and save it as SampleSchema.xml.</span></span> <span data-ttu-id="1e4ad-303">次の XSD スキーマをファイルに追加します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-303">Add the following XSD schema to the file:</span></span>  
  
    ```  
    <xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
                xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
    <xsd:annotation>  
      <xsd:appinfo>  
        <sql:relationship name="CustCustOrder"  
              parent="Cust"  
              parent-key="CustomerID"  
              child="CustOrder"  
              child-key="CustomerID" />  
      </xsd:appinfo>  
    </xsd:annotation>  
      <xsd:element name="ROOT" sql:is-constant="true" >  
        <xsd:complexType>  
          <xsd:sequence>  
            <xsd:element ref="Customers" />  
          </xsd:sequence>  
        </xsd:complexType>  
      </xsd:element>  
      <xsd:element name="Customers" sql:relation="Cust" >  
       <xsd:complexType>  
         <xsd:sequence>  
           <xsd:element name="CustomerID"  type="xsd:integer" />  
           <xsd:element name="CompanyName" type="xsd:string" />  
           <xsd:element name="City"        type="xsd:string" />  
           <xsd:element name="Order"   
                              sql:relation="CustOrder"  
                              sql:relationship="CustCustOrder" >  
             <xsd:complexType>  
              <xsd:attribute name="OrderID" type="xsd:integer" />  
              <xsd:attribute name="CustomerID" type="xsd:integer" />  
             </xsd:complexType>  
           </xsd:element>  
         </xsd:sequence>  
        </xsd:complexType>  
      </xsd:element>  
    </xsd:schema>  
    ```  
  
3.  <span data-ttu-id="1e4ad-304">任意のテキスト エディターまたは XML エディターでファイルを作成し、SampleXMLData.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-304">Create a file in your preferred text or XML editor, and save it as SampleXMLData.xml.</span></span> <span data-ttu-id="1e4ad-305">このファイルに次の XML ドキュメントを追加します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-305">Add the following XML document to the file:</span></span>  
  
    ```  
    <ROOT>  
      <Customers>  
        <CustomerID>1111</CustomerID>  
        <CompanyName>Hanari Carnes</CompanyName>  
        <City>NY</City>  
        <Order OrderID="1" />  
        <Order OrderID="2" />  
      </Customers>  
  
      <Customers>  
        <CustomerID>1112</CustomerID>  
        <CompanyName>Toms Spezialitten</CompanyName>  
         <City>LA</City>  
        <Order OrderID="3" />  
      </Customers>  
      <Customers>  
        <CustomerID>1113</CustomerID>  
        <CompanyName>Victuailles en stock</CompanyName>  
        <Order OrderID="4" />  
    </Customers>  
    </ROOT>  
    ```  
  
4.  <span data-ttu-id="1e4ad-306">Visual Basic (標準 EXE) アプリケーションと、上のコードを作成し、</span><span class="sxs-lookup"><span data-stu-id="1e4ad-306">Create a Visual Basic (Standard EXE) application and the preceding code.</span></span> <span data-ttu-id="1e4ad-307">プロジェクトに次の参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-307">Add these references to the project:</span></span>  
  
    ```  
    Microsoft XML BulkLoad for SQL Server 4.0 Type Library  
    Microsoft ActiveX Data objects 2.6 Library  
    ```  
  
5.  <span data-ttu-id="1e4ad-308">アプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-308">Execute the application.</span></span>  
  
 <span data-ttu-id="1e4ad-309">これは、これと同等の XDR スキーマです。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-309">This is the equivalent XDR schema:</span></span>  
  
```  
<?xml version="1.0" ?>  
<Schema xmlns="urn:schemas-microsoft-com:xml-data"   
        xmlns:dt="urn:schemas-microsoft-com:xml:datatypes"    
        xmlns:sql="urn:schemas-microsoft-com:xml-sql" >  
  
   <ElementType name="CustomerID" dt:type="int" />  
   <ElementType name="CompanyName" dt:type="string" />  
   <ElementType name="City" dt:type="string" />  
  
   <ElementType name="root" sql:is-constant="1">  
      <element type="Customers" />  
   </ElementType>  
  
   <ElementType name="Customers" sql:relation="Cust"  >  
      <element type="CustomerID" sql:field="CustomerID" />  
      <element type="CompanyName" sql:field="CompanyName" />  
      <element type="City" sql:field="City" />  
      <element type="Order" >  
         <sql:relationship  
                key-relation="Cust"  
                key="CustomerID"  
                foreign-key="CustomerID"  
                foreign-relation="CustOrder" />  
      </element>  
   </ElementType>  
    <ElementType name="Order" sql:relation="CustOrder" >  
      <AttributeType name="OrderID" />  
      <AttributeType name="CustomerID" />  
      <attribute type="OrderID" />  
      <attribute type="CustomerID" />  
    </ElementType>  
</Schema>  
```  
  
## <a name="j-bulk-loading-in-xml-data-type-columns"></a><span data-ttu-id="1e4ad-310">J.</span><span class="sxs-lookup"><span data-stu-id="1e4ad-310">J.</span></span> <span data-ttu-id="1e4ad-311">xml データ型の列に一括読み込みを行う</span><span class="sxs-lookup"><span data-stu-id="1e4ad-311">Bulk loading in xml Data Type columns</span></span>  
 <span data-ttu-id="1e4ad-312">マッピングスキーマで、注釈を使用して[xml データ型](/sql/t-sql/xml/xml-transact-sql)の列が指定されている場合 `sql:datatype="xml"` 、xml 一括読み込みでは、マップされたフィールドの xml 子要素をソースドキュメントからこの列にコピーできます。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-312">If the mapping schema specifies a [xml data type](/sql/t-sql/xml/xml-transact-sql) column by using the `sql:datatype="xml"` annotation, XML Bulk Load can copy XML child elements for the mapped field from the source document into this column.</span></span>  
  
 <span data-ttu-id="1e4ad-313">次の XSD スキーマを考えてみます。この XSD スキーマでは、サンプル データベース AdventureWorks の Production.ProductModel テーブルのビューがマップされます。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-313">Consider the following XSD schema, which maps a view of the Production.ProductModel table in the AdventureWorks sample database.</span></span> <span data-ttu-id="1e4ad-314">このテーブルでは、データ型の CatalogDescription フィールド `xml` は、 **\<Desc>** 注釈と注釈を使用して要素にマップされ `sql:field` `sql:datatype="xml"` ます。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-314">In this table, the CatalogDescription field of `xml` data type is mapped to a **\<Desc>** element using the `sql:field` and `sql:datatype="xml"` annotations.</span></span>  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
           xmlns:sql="urn:schemas-microsoft-com:mapping-schema"  
           xmlns="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription">   
  <xsd:element name="ProductModel"  sql:relation="Production.ProductModel" >  
    <xsd:complexType>  
      <xsd:sequence>  
        <xsd:element name="Name" type="xs:string"></xsd:element>  
        <xsd:element name="Desc" sql:field="CatalogDescription" sql:datatype="xml">  
        <xsd:complexType>  
          <xsd:sequence>  
            <xsd:element name="ProductDescription">  
              <xsd:complexType>  
                <xsd:sequence>  
                  <xsd:element name="Summary" type="xs:anyType"/>  
                </xsd:sequence>  
              </xsd:complexType>  
            </xsd:element>  
          </xsd:sequence>  
        </xsd:complexType>  
        </xsd:element>   
     </xsd:sequence>  
     <xsd:attribute name="ProductModelID" sql:field="ProductModelID" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
#### <a name="to-test-a-working-sample"></a><span data-ttu-id="1e4ad-315">実際のサンプルをテストするには</span><span class="sxs-lookup"><span data-stu-id="1e4ad-315">To test a working sample</span></span>  
  
1.  <span data-ttu-id="1e4ad-316">サンプル データベース AdventureWorks がインストールされていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-316">Verify that the AdventureWorks sample database is installed.</span></span>  
  
2.  <span data-ttu-id="1e4ad-317">任意のテキスト エディターまたは XML エディターでファイルを作成し、SampleSchema.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-317">Create a file in your preferred text or XML editor, and save it as SampleSchema.xml.</span></span> <span data-ttu-id="1e4ad-318">このファイルに上の XSD スキーマをコピーして貼り付け、ファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-318">Copy the XSD schema above and paste it into the file and save it.</span></span>  
  
3.  <span data-ttu-id="1e4ad-319">任意のテキスト エディターまたは XML エディターでファイルを作成し、SampleXMLData.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-319">Create a file in your preferred text or XML editor, and save it as SampleXMLData.xml.</span></span> <span data-ttu-id="1e4ad-320">このファイルに次の XML ドキュメントをコピーして貼り付け、前の手順と同じフォルダーに保存します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-320">Copy the following XML document below and paste it into the file and save it in the same folder as was used for the previous step.</span></span>  
  
    ```  
    <ProductModel ProductModelID="2005">  
        <Name>Mountain-100 (2005 model)</Name>  
        <Desc><?xml-stylesheet href="ProductDescription.xsl" type="text/xsl"?>  
            <p1:ProductDescription xmlns:p1="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription"   
                  xmlns:wm="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain"   
                  xmlns:wf="http://www.adventure-works.com/schemas/OtherFeatures"   
                  xmlns:html="http://www.w3.org/1999/xhtml"   
                  xmlns="">  
                <p1:Summary>  
                    <html:p>Our top-of-the-line competition mountain bike.   
          Performance-enhancing options include the innovative HL Frame,   
          super-smooth front suspension, and traction for all terrain.  
                            </html:p>  
                </p1:Summary>  
                <p1:Manufacturer>  
                    <p1:Name>AdventureWorks</p1:Name>  
                    <p1:Copyright>2002-2005</p1:Copyright>  
                    <p1:ProductURL>HTTP://www.Adventure-works.com</p1:ProductURL>  
                </p1:Manufacturer>  
                <p1:Features>These are the product highlights.   
                     <wm:Warranty>  
                        <wm:WarrantyPeriod>3 years</wm:WarrantyPeriod>  
                        <wm:Description>parts and labor</wm:Description>  
                    </wm:Warranty><wm:Maintenance>  
                        <wm:NoOfYears>10 years</wm:NoOfYears>  
                        <wm:Description>maintenance contract available through your dealer or any AdventureWorks retail store.</wm:Description>  
                    </wm:Maintenance><wf:wheel>High performance wheels.</wf:wheel><wf:saddle>  
                        <html:i>Anatomic design</html:i> and made from durable leather for a full-day of riding in comfort.</wf:saddle><wf:pedal>  
                        <html:b>Top-of-the-line</html:b> clipless pedals with adjustable tension.</wf:pedal><wf:BikeFrame>Each frame is hand-crafted in our Bothell facility to the optimum diameter   
          and wall-thickness required of a premium mountain frame.   
          The heat-treated welded aluminum frame has a larger diameter tube that absorbs the bumps.</wf:BikeFrame><wf:crankset> Triple crankset; alumunim crank arm; flawless shifting. </wf:crankset></p1:Features>  
                <!-- add one or more of these elements... one for each specific product in this product model -->  
                <p1:Picture>  
                    <p1:Angle>front</p1:Angle>  
                    <p1:Size>small</p1:Size>  
                    <p1:ProductPhotoID>118</p1:ProductPhotoID>  
                </p1:Picture>  
                <!-- add any tags in <specifications> -->  
                <p1:Specifications> These are the product specifications.  
                       <Material>Almuminum Alloy</Material><Color>Available in most colors</Color><ProductLine>Mountain bike</ProductLine><Style>Unisex</Style><RiderExperience>Advanced to Professional riders</RiderExperience></p1:Specifications>  
            </p1:ProductDescription>  
        </Desc>  
    </ProductModel>  
    ```  
  
4.  <span data-ttu-id="1e4ad-321">任意のテキスト エディターまたは XML エディターでファイルを作成し、BulkloadXml.vbs として保存します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-321">Create a file in your preferred text or XML editor, and save it as BulkloadXml.vbs.</span></span> <span data-ttu-id="1e4ad-322">このファイルに次の VBScript コードをコピーして貼り付け、</span><span class="sxs-lookup"><span data-stu-id="1e4ad-322">Copy the following VBScript code and paste it into the file.</span></span> <span data-ttu-id="1e4ad-323">前の XML データ ファイルとスキーマ ファイルを保存したフォルダーに保存します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-323">Save it in the same folder as was used for the previous XML data and schema files.</span></span>  
  
    ```  
    set objBL = CreateObject("SQLXMLBulkLoad.SQLXMLBulkload.4.0")  
    objBL.ConnectionString = "provider=SQLOLEDB;data source=MyServer;database=AdventureWorks;integrated security=SSPI"  
  
    Dim fso, sAppPath  
    Set fso = CreateObject("Scripting.FileSystemObject")   
    sAppPath = fso.GetFolder(".")   
  
    objBL.ErrorLogFile = sAppPath & "\error.log"  
  
    'Execute XML bulkload using file.  
    objBL.Execute "SampleSchema.xml", "SampleXMLData.xml"  
    set objBL=Nothing  
    ```  
  
5.  <span data-ttu-id="1e4ad-324">スクリプト BulkloadXml.vbs を実行します。</span><span class="sxs-lookup"><span data-stu-id="1e4ad-324">Execute the BulkloadXml.vbs script.</span></span>  
  
  
