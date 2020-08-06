---
title: 'Sql: overflow フィールドを使用した未使用データの取得 (SQLXML 4.0) |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- unconsumed data
- storing unconsumed data
- retrieving unconsumed data
- annotated XSD schemas, unconsumed data
- overflow data [SQLXML]
- sql:overflow-field
ms.assetid: 8526998d-b47d-4a32-8dc2-7f50a8d11097
author: rothja
ms.author: jroth
ms.openlocfilehash: 796fda9428954c5f18c5d37b353de9fd4122551e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644388"
---
# <a name="retrieving-unconsumed-data-using-the-sqloverflow-field-sqlxml-40"></a><span data-ttu-id="759f9-102">sql:overflow-field を使用した、未使用データの取得 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="759f9-102">Retrieving Unconsumed Data Using the sql:overflow-field (SQLXML 4.0)</span></span>
  <span data-ttu-id="759f9-103">[!INCLUDE[tsql](../../includes/tsql-md.md)] OPENXML 関数を使用して XML ドキュメントからデータベースにレコードを挿入するときに、ソース XML ドキュメントのすべての未使用データを 1 つの列に格納することができます。</span><span class="sxs-lookup"><span data-stu-id="759f9-103">When records are inserted in a database from an XML document by using the [!INCLUDE[tsql](../../includes/tsql-md.md)] OPENXML function, all the unconsumed data from the source XML document can be stored in a column.</span></span> <span data-ttu-id="759f9-104">注釈付きスキーマを使用してデータベースからデータを取得するときには、`sql:overflow-field` 属性を指定して、オーバーフロー データを格納するテーブルの列を指定できます。</span><span class="sxs-lookup"><span data-stu-id="759f9-104">When you retrieve data from a database by using annotated schemas, you can specify the `sql:overflow-field` attribute to identify the column in the table in which the overflow data is stored.</span></span> <span data-ttu-id="759f9-105">`sql:overflow-field`属性はで指定でき **\<element>** ます。</span><span class="sxs-lookup"><span data-stu-id="759f9-105">The `sql:overflow-field` attribute can be specified on **\<element>**.</span></span>  
  
 <span data-ttu-id="759f9-106">データは次のように取得されます。</span><span class="sxs-lookup"><span data-stu-id="759f9-106">This data is then retrieved in these ways:</span></span>  
  
-   <span data-ttu-id="759f9-107">オーバーフロー列に格納された属性が、`sql:overflow-field` 注釈を含む要素に追加されます。</span><span class="sxs-lookup"><span data-stu-id="759f9-107">Attributes stored in the overflow column are added to the element that contains the `sql:overflow-field` annotation.</span></span>  
  
-   <span data-ttu-id="759f9-108">データベースのオーバーフロー列に格納された子要素とその子孫が、スキーマで明示的に指定されたコンテンツの後に子要素として追加されます。</span><span class="sxs-lookup"><span data-stu-id="759f9-108">The child elements and their descendents, stored in the overflow column in the database, are added as child elements following the content that is explicitly specified in the schema.</span></span> <span data-ttu-id="759f9-109">このとき、順序は維持されません。</span><span class="sxs-lookup"><span data-stu-id="759f9-109">(No order is preserved.)</span></span>  
  
## <a name="examples"></a><span data-ttu-id="759f9-110">例</span><span class="sxs-lookup"><span data-stu-id="759f9-110">Examples</span></span>  
 <span data-ttu-id="759f9-111">次の例を使用した実際のサンプルを作成するには、特定の条件を満たす必要があります。</span><span class="sxs-lookup"><span data-stu-id="759f9-111">To create working samples using the following examples, you must meet certain requirements.</span></span> <span data-ttu-id="759f9-112">詳細については、「 [SQLXML の例を実行するための要件](../sqlxml/requirements-for-running-sqlxml-examples.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="759f9-112">For more information, see [Requirements for Running SQLXML Examples](../sqlxml/requirements-for-running-sqlxml-examples.md).</span></span>  
  
### <a name="a-specifying-sqloverflow-field-for-an-element"></a><span data-ttu-id="759f9-113">A.</span><span class="sxs-lookup"><span data-stu-id="759f9-113">A.</span></span> <span data-ttu-id="759f9-114">要素に sql:overflow-field を指定する</span><span class="sxs-lookup"><span data-stu-id="759f9-114">Specifying sql:overflow-field for an element</span></span>  
 <span data-ttu-id="759f9-115">この例では、次のスクリプトを実行して tempdb データベースにテーブル Customers2 が作成済みであることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="759f9-115">This example assumes that the following script has been run so that a table named Customers2 exists in the tempdb database:</span></span>  
  
```  
USE tempdb  
CREATE TABLE Customers2 (  
CustomerID       VARCHAR(10),   
ContactName    VARCHAR(30),   
AddressOverflow    NVARCHAR(500))  
  
GO  
INSERT INTO Customers2 VALUES (  
'ALFKI',   
'Joe',  
'<Address>  
  <Address1>Maple St.</Address1>  
  <Address2>Apt. E105</Address2>  
  <City>Seattle</City>  
  <State>WA</State>  
  <Zip>98147</Zip>  
 </Address>')  
GO  
```  
  
 <span data-ttu-id="759f9-116">さらに、tempdb データベースの仮想ディレクトリと、 `template` "template" という名前の種類のテンプレート仮想名を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="759f9-116">In addition, you must create a virtual directory for the tempdb database-and a template virtual name of `template` type named "template".</span></span>  
  
 <span data-ttu-id="759f9-117">次の例では、マッピング スキーマで、Customers2 テーブルの AddressOverflow 列に格納されている未使用データを取得します。</span><span class="sxs-lookup"><span data-stu-id="759f9-117">In the following example, the mapping schema retrieves the unconsumed data that is stored in the AddressOverflow column of the Customers2 table:</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  
  <xsd:element name="Customers2" sql:overflow-field="AddressOverflow" >  
    <xsd:complexType>  
      <xsd:attribute name="CustomerID"  type="xsd:integer"/>  
      <xsd:attribute name="ContactName"  type="xsd:string" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a><span data-ttu-id="759f9-118">スキーマに対してサンプル XPath クエリをテストするには</span><span class="sxs-lookup"><span data-stu-id="759f9-118">To test a sample XPath query against the schema</span></span>  
  
1.  <span data-ttu-id="759f9-119">上のスキーマのコードをコピーして、テキスト ファイルに貼り付け、</span><span class="sxs-lookup"><span data-stu-id="759f9-119">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="759f9-120">Overflow.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="759f9-120">Save the file as Overflow.xml.</span></span>  
  
2.  <span data-ttu-id="759f9-121">次のテンプレートをコピーして、テキスト ファイルに貼り付け、</span><span class="sxs-lookup"><span data-stu-id="759f9-121">Copy the following template and paste it into a text file.</span></span> <span data-ttu-id="759f9-122">Overflow.xml を保存したディレクトリに OverflowT.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="759f9-122">Save the file as OverflowT.xml in the same directory where you saved Overflow.xml.</span></span> <span data-ttu-id="759f9-123">このテンプレートのクエリでは、Customers2 テーブル内のレコードが選択されます。</span><span class="sxs-lookup"><span data-stu-id="759f9-123">The query in the template selects the records in the Customers2 table.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="Overflow.xml">  
            /Customers2  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="759f9-124">マッピング スキーマ (Overflow.xml) に指定するディレクトリ パスは、テンプレートを保存するディレクトリに対する相対パスです。</span><span class="sxs-lookup"><span data-stu-id="759f9-124">The directory path specified for the mapping schema (Overflow.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="759f9-125">次のように、絶対パスを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="759f9-125">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\SqlXmlTest\Overflow.xml"  
    ```  
  
3.  <span data-ttu-id="759f9-126">SQLXML 4.0 テスト スクリプト (sqlxml4test.vbs) を作成し、それを使用してテンプレートを実行します。</span><span class="sxs-lookup"><span data-stu-id="759f9-126">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="759f9-127">詳細については、「ADO を使用した[SQLXML 4.0 クエリの実行](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="759f9-127">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="759f9-128">結果セットは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="759f9-128">Here is the result set:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Customers2 CustomerID="ALFKI" ContactName="Joe">  
    <Address1>Maple St.</Address1>   
    <Address2>Apt. E105</Address2>   
    <City>Seattle</City>   
    <State>WA</State>   
    <Zip>98147</Zip>   
  </Customers2>  
</ROOT>  
```  
  
  
