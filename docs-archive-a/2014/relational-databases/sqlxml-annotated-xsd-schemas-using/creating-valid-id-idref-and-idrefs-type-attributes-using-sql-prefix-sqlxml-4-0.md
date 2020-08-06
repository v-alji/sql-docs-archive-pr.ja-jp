---
title: 'Sql: prefix を使用した有効な ID、IDREF、IDREFS 型の属性の作成 (SQLXML 4.0) |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- IDREFS relationships [SQLXML]
- annotated XSD schemas, ID type attribute
- IDREF type attribute [SQLXML]
- annotated XSD schemas, IDREFS type attribute
- ID type attribute [SQLXML]
- sql:prefix
- prefix annotation
- IDREF relationships [SQLXML]
- IDREFS type attribute [SQLXML]
- annotated XSD schemas, IDREF type attribute
- ID relationships [SQLXML]
ms.assetid: 1c7f77d3-81f3-4820-bb63-c4aaa4ea9aa1
author: rothja
ms.author: jroth
ms.openlocfilehash: cb9e63bebd0cebbfeed75ea5cbe2ea62683234fc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640865"
---
# <a name="creating-valid-id-idref-and-idrefs-type-attributes-using-sqlprefix-sqlxml-40"></a><span data-ttu-id="284a5-102">sql:prefix を使用した、有効な ID 型、IDREF 型、IDREFS 型の属性の作成 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="284a5-102">Creating Valid ID, IDREF, and IDREFS Type Attributes Using sql:prefix (SQLXML 4.0)</span></span>
  <span data-ttu-id="284a5-103">属性を ID 型属性として指定することができます。</span><span class="sxs-lookup"><span data-stu-id="284a5-103">An attribute can be specified to be an ID type attribute.</span></span> <span data-ttu-id="284a5-104">ID 型属性を指定すると、IDREF または IDREFS として指定した属性から ID 型属性を参照でき、ドキュメント間をリンクできるようになります。</span><span class="sxs-lookup"><span data-stu-id="284a5-104">Attributes specified as IDREF or IDREFS can then be used to refer to the ID type attributes, enabling links between documents.</span></span>  
  
 <span data-ttu-id="284a5-105">ID、IDREF、IDREFS は、データベースの PK と FK (主キーと外部キー) のリレーションシップにほぼ対応し、ほとんど違いはありません。</span><span class="sxs-lookup"><span data-stu-id="284a5-105">ID, IDREF, and IDREFS correspond to PK/FK (primary key/foreign key) relationships in the database, with few differences.</span></span> <span data-ttu-id="284a5-106">XML ドキュメントでは、ID 型の属性の値は一意である必要があります。</span><span class="sxs-lookup"><span data-stu-id="284a5-106">In an XML document, the values of ID type attributes must be distinct.</span></span> <span data-ttu-id="284a5-107">**CustomerID**属性と**ORDERID**属性が XML ドキュメントで ID 型として指定されている場合、これらの値は個別である必要があります。</span><span class="sxs-lookup"><span data-stu-id="284a5-107">If **CustomerID** and **OrderID** attributes are specified as ID type in an XML document, these values must be distinct.</span></span> <span data-ttu-id="284a5-108">一方データベースでは、CustomerID 列と OrderID 列の値は同じにできます。</span><span class="sxs-lookup"><span data-stu-id="284a5-108">However, in a database, CustomerID and OrderID columns can have the same values.</span></span> <span data-ttu-id="284a5-109">たとえば、CustomerID = 1、OrderID = 1 はデータベース内で有効です。</span><span class="sxs-lookup"><span data-stu-id="284a5-109">(For example, CustomerID = 1 and OrderID = 1 are valid in the database).</span></span>  
  
 <span data-ttu-id="284a5-110">ID 属性、IDREF 属性、および IDREFS 属性が有効であるためには、次の条件を満たしている必要があります。</span><span class="sxs-lookup"><span data-stu-id="284a5-110">For the ID, IDREF, and IDREFS attributes to be valid:</span></span>  
  
-   <span data-ttu-id="284a5-111">ID の値が XML ドキュメント内で一意であること。</span><span class="sxs-lookup"><span data-stu-id="284a5-111">The value of ID must be unique within the XML document.</span></span>  
  
-   <span data-ttu-id="284a5-112">各 IDREF および IDREFS について、XML ドキュメント内に参照される ID が存在すること。</span><span class="sxs-lookup"><span data-stu-id="284a5-112">For every IDREF and IDREFS, the referenced ID values must be in the XML document.</span></span>  
  
-   <span data-ttu-id="284a5-113">ID、IDREF、IDREFS の値が名前付きトークンであること。</span><span class="sxs-lookup"><span data-stu-id="284a5-113">The value of an ID, IDREF, and IDREFS must be a named token.</span></span> <span data-ttu-id="284a5-114">たとえば、整数値 101 は ID 値にできません。</span><span class="sxs-lookup"><span data-stu-id="284a5-114">(For example, the integer value 101 cannot be an ID value.)</span></span>  
  
-   <span data-ttu-id="284a5-115">ID、IDREF、および IDREFS 型の属性は、型、型、また `text` `ntext` `image` はその他のバイナリデータ型 (たとえば、) の列にマップできません `timestamp` 。</span><span class="sxs-lookup"><span data-stu-id="284a5-115">The attributes of ID, IDREF, and IDREFS type cannot be mapped to columns of the type `text`, `ntext`, or `image` or any other binary data type (for example, `timestamp`).</span></span>  
  
 <span data-ttu-id="284a5-116">XML ドキュメントに複数の Id が含まれている場合は、注釈を使用し `sql:prefix` て、値が一意であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="284a5-116">If an XML document contains multiple IDs, use the `sql:prefix` annotation to ensure that the values are unique.</span></span>  
  
 <span data-ttu-id="284a5-117">`sql:prefix` 注釈は、XSD 固定属性では使用できないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="284a5-117">Note that `sql:prefix` annotation cannot be used with XSD fixed attribute.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="284a5-118">例</span><span class="sxs-lookup"><span data-stu-id="284a5-118">Examples</span></span>  
 <span data-ttu-id="284a5-119">次の例を使用した実際のサンプルを作成するには、特定の条件を満たす必要があります。</span><span class="sxs-lookup"><span data-stu-id="284a5-119">To create working samples using the following examples, you must meet certain requirements.</span></span> <span data-ttu-id="284a5-120">詳細については、「 [SQLXML の例を実行するための要件](../sqlxml/requirements-for-running-sqlxml-examples.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="284a5-120">For more information, see [Requirements for Running SQLXML Examples](../sqlxml/requirements-for-running-sqlxml-examples.md).</span></span>  
  
### <a name="a-specifying-id-and-idrefs-types"></a><span data-ttu-id="284a5-121">A.</span><span class="sxs-lookup"><span data-stu-id="284a5-121">A.</span></span> <span data-ttu-id="284a5-122">ID 型と IDREFS 型を指定する</span><span class="sxs-lookup"><span data-stu-id="284a5-122">Specifying ID and IDREFS types</span></span>  
 <span data-ttu-id="284a5-123">次のスキーマでは、 **\<Customer>** 要素は子要素で構成されて **\<Order>** います。</span><span class="sxs-lookup"><span data-stu-id="284a5-123">In the following schema, the **\<Customer>** element consists of the **\<Order>** child element.</span></span> <span data-ttu-id="284a5-124">要素には、 **\<Order>** 子要素である要素もあり **\<OrderDetail>** ます。</span><span class="sxs-lookup"><span data-stu-id="284a5-124">The **\<Order>** element also has a child element, the **\<OrderDetail>** element.</span></span>  
  
 <span data-ttu-id="284a5-125">の**Orderidlist**属性 **\<Customer>** は、要素の**OrderID**属性を参照する IDREFS 型の属性です **\<Order>** 。</span><span class="sxs-lookup"><span data-stu-id="284a5-125">The **OrderIDList** attribute of **\<Customer>** is an IDREFS type attribute that refers to the **OrderID** attribute of the **\<Order>** element.</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="CustOrders"  
                 parent="Sales.Customer"  
                 parent-key="CustomerID"  
                 child="Sales.SalesOrderHeader"  
                 child-key="CustomerID" />  
    <sql:relationship name="OrderOrderDetail"  
                 parent="Sales.SalesOrderHeader"  
                 parent-key="SalesOrderID"  
                 child="Sales.SalesOrderDetail"  
                 child-key="SalesOrderID" />  
  </xsd:appinfo>  
</xsd:annotation>  
  <xsd:element name="Customer" sql:relation="Sales.Customer" >  
   <xsd:complexType>  
     <xsd:sequence>  
        <xsd:element name="Order" sql:relation="Sales.SalesOrderHeader"    
               sql:relationship="CustOrders" maxOccurs="unbounded" >  
          <xsd:complexType>  
              <xsd:sequence>  
                <xsd:element name="OrderDetail"   
                             sql:relation="Sales.SalesOrderDetail"   
                   sql:relationship="OrderOrderDetail"   
                   maxOccurs="unbounded" >  
                  <xsd:complexType>  
                   <xsd:attribute name="SalesOrderID" type="xsd:integer" />  
                   <xsd:attribute name="ProductID" type="xsd:string" />  
                   <xsd:attribute name="OrderQty" type="xsd:integer" />  
                  </xsd:complexType>  
               </xsd:element>  
             </xsd:sequence>  
             <xsd:attribute name="SalesOrderID"   
                            type="xsd:ID" sql:prefix="ord-" />  
             <xsd:attribute name="OrderDate" type="xsd:date" />  
             <xsd:attribute name="CustomerID" type="xsd:string" />  
          </xsd:complexType>  
      </xsd:element>  
    </xsd:sequence>  
    <xsd:attribute name="CustomerID" type="xsd:string" />  
    <xsd:attribute name="OrderIDList" type="xsd:IDREFS"   
                   sql:relation="Sales.SalesOrderHeader" sql:field="SalesOrderID"  
                   sql:relationship="CustOrders" sql:prefix="ord-">  
    </xsd:attribute>  
  </xsd:complexType>  
</xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a><span data-ttu-id="284a5-126">スキーマに対してサンプル XPath クエリをテストするには</span><span class="sxs-lookup"><span data-stu-id="284a5-126">To test a sample XPath query against the schema</span></span>  
  
1.  <span data-ttu-id="284a5-127">上のスキーマのコードをコピーして、テキスト ファイルに貼り付け、</span><span class="sxs-lookup"><span data-stu-id="284a5-127">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="284a5-128">sqlPrefix.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="284a5-128">Save the file as sqlPrefix.xml.</span></span>  
  
2.  <span data-ttu-id="284a5-129">次のテンプレートをコピーして、テキスト ファイルに貼り付け、</span><span class="sxs-lookup"><span data-stu-id="284a5-129">Copy the following template and paste it into a text file.</span></span> <span data-ttu-id="284a5-130">sqlPrefix.xml を保存したディレクトリに sqlPrefixT.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="284a5-130">Save the file as sqlPrefixT.xml in the same directory where you saved sqlPrefix.xml.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="sqlPrefix.xml">  
        /Customer[@CustomerID=1]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="284a5-131">マッピング スキーマ (sqlPrefix.xml) に指定するディレクトリ パスは、テンプレートを保存するディレクトリに対する相対パスです。</span><span class="sxs-lookup"><span data-stu-id="284a5-131">The directory path specified for the mapping schema (sqlPrefix.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="284a5-132">次のように、絶対パスを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="284a5-132">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\SqlXmlTest\sqlPrefix.xml"  
    ```  
  
3.  <span data-ttu-id="284a5-133">SQLXML 4.0 テスト スクリプト (sqlxml4test.vbs) を作成し、それを使用してテンプレートを実行します。</span><span class="sxs-lookup"><span data-stu-id="284a5-133">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="284a5-134">詳細については、「ADO を使用した[SQLXML クエリの実行](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="284a5-134">For more information, see [Using ADO to Execute SQLXML Queries](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="284a5-135">結果の一部を次に示します。</span><span class="sxs-lookup"><span data-stu-id="284a5-135">This is the partial result:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Customer CustomerID="1" OrderIDList="ord-43860 ord-44501 ord-45283 ord-46042">  
    <Order SalesOrderID="ord-43860" OrderDate="2001-08-01" CustomerID="1">  
      <OrderDetail SalesOrderID="43860" ProductID="729" OrderQty="1" />   
      <OrderDetail SalesOrderID="43860" ProductID="732" OrderQty="1" />   
      <OrderDetail SalesOrderID="43860" ProductID="738" OrderQty="1" />   
      <OrderDetail SalesOrderID="43860" ProductID="753" OrderQty="2" />   
      ...  
    </Order>  
    ...  
 </Customer>  
</ROOT>  
```  
  
  
