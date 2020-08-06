---
title: 'Sql: hide | を使用した要素と属性の非表示Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- hiding elements
- element mapping [SQLXML], hiding attributes and elements
- hide annotation
- sql:hide
- table/view mapping [SQLXML], hiding attributes and elements
- table mapping [SQLXML], hiding attributes and elements
- hiding attributes
- annotated XSD schemas, hiding attributes and elements
- attribute mapping [SQLXML], hiding attributes and elements
- column mapping [SQLXML]
- element hiding [SQLXML]
- XSD schemas [SQLXML], hiding attributes and elements
- attribute hiding [SQLXML]
ms.assetid: 0978301b-f068-46b6-82b9-dc555161f52e
author: rothja
ms.author: jroth
ms.openlocfilehash: 5a3beb48be1d9809b170faeafa964ba45156ac28
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741670"
---
# <a name="hiding-elements-and-attributes-by-using-sqlhide"></a><span data-ttu-id="3bb48-102">sql:hide による要素と属性の非表示</span><span class="sxs-lookup"><span data-stu-id="3bb48-102">Hiding Elements and Attributes by Using sql:hide</span></span>
  <span data-ttu-id="3bb48-103">XSD スキーマに対して XPath クエリを実行すると、結果の XML ドキュメントにはスキーマで指定された要素と属性が含められます。</span><span class="sxs-lookup"><span data-stu-id="3bb48-103">When an XPath query is executed against an XSD schema, the resulting XML document has elements and attributes that are specified in the schema.</span></span> <span data-ttu-id="3bb48-104">`sql:hide` 注釈を使用すると、スキーマでいくつかの要素と属性を非表示にするよう指定できます。</span><span class="sxs-lookup"><span data-stu-id="3bb48-104">You can specify that some elements and attributes be hidden in the schema by using the `sql:hide` annotation.</span></span> <span data-ttu-id="3bb48-105">この機能は、クエリの選択条件としてはスキーマ内の特定の要素または属性が必要でも、生成される XML ドキュメントではこれらを返したくない場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="3bb48-105">This is useful when the selection criteria of the query require particular elements or attributes in the schema, but you do not want them returned in the XML document that is generated.</span></span>  
  
 <span data-ttu-id="3bb48-106">`sql:hide` 注釈はブール値 (0 = false、1=true) をとります。</span><span class="sxs-lookup"><span data-stu-id="3bb48-106">The `sql:hide` annotation takes a Boolean value (0=false, 1=true).</span></span> <span data-ttu-id="3bb48-107">指定できる値は 0、1、true、false です。</span><span class="sxs-lookup"><span data-stu-id="3bb48-107">The acceptable values are 0, 1, true, and false.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="3bb48-108">例</span><span class="sxs-lookup"><span data-stu-id="3bb48-108">Examples</span></span>  
 <span data-ttu-id="3bb48-109">次の例を使用した実際のサンプルを作成するには、特定の条件を満たす必要があります。</span><span class="sxs-lookup"><span data-stu-id="3bb48-109">To create working samples using the following examples, you must meet certain requirements.</span></span> <span data-ttu-id="3bb48-110">詳細については、「 [SQLXML の例を実行するための要件](../sqlxml/requirements-for-running-sqlxml-examples.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3bb48-110">For more information, see [Requirements for Running SQLXML Examples](../sqlxml/requirements-for-running-sqlxml-examples.md).</span></span>  
  
### <a name="a-specifying-sqlhide-on-an-attribute"></a><span data-ttu-id="3bb48-111">A.</span><span class="sxs-lookup"><span data-stu-id="3bb48-111">A.</span></span> <span data-ttu-id="3bb48-112">属性に sql:hide を指定する</span><span class="sxs-lookup"><span data-stu-id="3bb48-112">Specifying sql:hide on an attribute</span></span>  
 <span data-ttu-id="3bb48-113">この例の XSD スキーマは、 **\<Person.Contact>** **ContactID**、 **FirstName**、および**LastName**属性を持つ要素で構成されています。</span><span class="sxs-lookup"><span data-stu-id="3bb48-113">The XSD schema in this example consists of an **\<Person.Contact>** element with **ContactID**, **FirstName**, and **LastName** attributes.</span></span>  
  
 <span data-ttu-id="3bb48-114">**\<Person.Contact>** 要素は複合型であるため、同じ名前のテーブルにマップされます (既定のマッピング)。</span><span class="sxs-lookup"><span data-stu-id="3bb48-114">The **\<Person.Contact>** element is of complex type and, therefore, maps to the table of the same name (default mapping).</span></span> <span data-ttu-id="3bb48-115">要素のすべての属性 **\<Person.Contact>** は単純型で、AdventureWorks データベースの Person. Contacttable 内の同じ名前の列にマップされます。</span><span class="sxs-lookup"><span data-stu-id="3bb48-115">All the attributes of **\<Person.Contact>** element are of simple type and map to columns with the same names in the Person.Contacttable in the AdventureWorks database.</span></span> <span data-ttu-id="3bb48-116">スキーマで `sql:hide` は、注釈は**ContactID**属性に指定されています。</span><span class="sxs-lookup"><span data-stu-id="3bb48-116">In the schema, the `sql:hide` annotation is specified on the **ContactID** attribute.</span></span> <span data-ttu-id="3bb48-117">このスキーマに対して XPath クエリを指定すると、XML ドキュメントで**ContactID**が返されません。</span><span class="sxs-lookup"><span data-stu-id="3bb48-117">When an XPath query is specified against this schema, the **ContactID** is not returned in the XML document.</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Person.Contact" >  
     <xsd:complexType>  
       <xsd:attribute name="ContactID"  sql:hide="true" />   
       <xsd:attribute name="FirstName"   type="xsd:string" />   
       <xsd:attribute name="LastName"    type="xsd:string" />   
     </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a><span data-ttu-id="3bb48-118">スキーマに対してサンプル XPath クエリをテストするには</span><span class="sxs-lookup"><span data-stu-id="3bb48-118">To test a sample XPath query against the schema</span></span>  
  
1.  <span data-ttu-id="3bb48-119">上のスキーマのコードをコピーして、テキスト ファイルに貼り付け、</span><span class="sxs-lookup"><span data-stu-id="3bb48-119">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="3bb48-120">Hide.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="3bb48-120">Save the file as Hide.xml.</span></span>  
  
2.  <span data-ttu-id="3bb48-121">次のテンプレートをコピーして、テキスト ファイルに貼り付け、</span><span class="sxs-lookup"><span data-stu-id="3bb48-121">Copy the following template and paste it into a text file.</span></span> <span data-ttu-id="3bb48-122">Hide.xml を保存したディレクトリに HideT.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="3bb48-122">Save the file as HideT.xml in the same directory where you saved Hide.xml.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="Hide.xml">  
            /Person.Contact[@ContactID="1"]  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="3bb48-123">マッピング スキーマ (Hide.xml) に指定するディレクトリ パスは、テンプレートを保存するディレクトリに対する相対パスです。</span><span class="sxs-lookup"><span data-stu-id="3bb48-123">The directory path specified for the mapping schema (Hide.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="3bb48-124">次のように、絶対パスを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="3bb48-124">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\Hide.xml"  
    ```  
  
3.  <span data-ttu-id="3bb48-125">SQLXML 4.0 テスト スクリプト (sqlxml4test.vbs) を作成し、それを使用してテンプレートを実行します。</span><span class="sxs-lookup"><span data-stu-id="3bb48-125">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="3bb48-126">詳細については、「ADO を使用した[SQLXML 4.0 クエリの実行](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3bb48-126">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="3bb48-127">結果セットは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="3bb48-127">Here is the result set:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
   <Person.Contact FirstName="Gustavo" LastName="Achong" />   
</ROOT>  
```  
  
 <span data-ttu-id="3bb48-128">要素に `sql:hide` を指定した場合、その要素とその属性または子要素は、生成される XML ドキュメント内に表示されません。</span><span class="sxs-lookup"><span data-stu-id="3bb48-128">When `sql:hide` is specified on an element, the element and its attributes or child elements do not appear in the XML document that is generated.</span></span> <span data-ttu-id="3bb48-129">次に `sql:hide` 、が要素に指定されている別の XSD スキーマを示し **\<OD>** ます。</span><span class="sxs-lookup"><span data-stu-id="3bb48-129">Here is another XSD schema in which `sql:hide` is specified on the **\<OD>** element:</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:dt="urn:schemas-microsoft-com:datatypes"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  
  <xsd:annotation>  
    <xsd:documentation>  
      Sales.Customer-Sales.SalesOrderHeader-Sales.SalesOrderDetail Schema  
      Copyright 2004 Microsoft. All rights reserved.  
    </xsd:documentation>  
    <xsd:appinfo>  
      <sql:relationship name="CustomerOrder"  
         parent="Sales.Customer"  
                  parent-key="CustomerID"  
                  child-key="CustomerID"  
                  child="Sales.SalesOrderHeader" />  
       <sql:relationship name="OrderOrderDetails"  
                  parent="Sales.SalesOrderHeader"  
                  parent-key="SalesOrderID"  
                  child-key="SalesOrderID"  
                  child="Sales.SalesOrderDetail"/>  
    </xsd:appinfo>  
  </xsd:annotation>  
  
  <xsd:element name="Customers" sql:relation="Sales.Customer">  
    <xsd:complexType>  
      <xsd:sequence>  
        <xsd:element name="Order" sql:relation="Sales.SalesOrderHeader"   
                     maxOccurs="unbounded"   
                     sql:relationship="CustomerOrder">  
          <xsd:complexType>  
            <xsd:sequence>  
               <xsd:element name="OD" sql:relation="Sales.SalesOrderDetail"                                       maxOccurs="unbounded"                                       sql:relationship="OrderOrderDetails"                                       sql:hide="1">  
                  <xsd:complexType>  
                    <xsd:attribute name="SalesOrderID" type="xsd:string"/>  
                    <xsd:attribute name="ProductID" type="xsd:string"/>  
                  </xsd:complexType>  
               </xsd:element>  
            </xsd:sequence>  
          <xsd:attribute name="CustomerID" type="xsd:string"/>  
          <xsd:attribute name="OID" sql:field="SalesOrderID"   
                                    type="xsd:string"/>  
          <xsd:attribute name="OrderDate" type="xsd:date"/>   
        </xsd:complexType>  
      </xsd:element>  
    </xsd:sequence>  
    <xsd:attribute name="CID" sql:field="CustomerID"   
                                type="xsd:string"/>  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 <span data-ttu-id="3bb48-130">このスキーマに対して XPath クエリ (たとえば) が指定されている場合 `/Customers[@CID="1"]` 、生成される XML ドキュメントには、 **\<OD>** 次の部分的な結果に示すように、要素とその子要素は含まれません。</span><span class="sxs-lookup"><span data-stu-id="3bb48-130">When an XPath query (for example `/Customers[@CID="1"]`) is specified against this schema, the XML document that is generated does not include the **\<OD>** element and its children, as shown in this partial result:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Customers CID="1">  
    <Order CustomerID="1" OID="43860" OrderDate="2001-08-01" />   
    <Order CustomerID="1" OID="44501" OrderDate="2001-11-01" />   
    <Order CustomerID="1" OID="45283" OrderDate="2002-02-01" />   
    <Order CustomerID="1" OID="46042" OrderDate="2002-05-01" />   
  </Customers>  
</ROOT>  
```  
  
  
