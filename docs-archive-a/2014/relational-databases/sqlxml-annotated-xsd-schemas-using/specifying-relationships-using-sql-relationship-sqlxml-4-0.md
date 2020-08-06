---
title: 'Sql: relationship を使用したリレーションシップの指定 (SQLXML 4.0) |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- IDREFS relationships [SQLXML]
- parent attribute [SQLXML]
- element relationships [SQLXML]
- multiple element relationships
- attribute relationships [SQLXML]
- sql:relationship
- relationship chains [SQLXML]
- IDREF relationships [SQLXML]
- parent-child relationships [SQLXML]
- relationship annotation
- XSD schemas [SQLXML], relationships
- annotated XSD schemas, relationships
- relationships [SQLXML], specifying
- unnamed relationships
- ID relationships [SQLXML]
- hierarchical relationships [SQLXML]
- named relationships [SQLXML]
ms.assetid: 98820afa-74e1-4e62-b336-6111a3dede4c
author: rothja
ms.author: jroth
ms.openlocfilehash: 42c703de9d564580eb0baa1349a45b193109c87a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640861"
---
# <a name="specifying-relationships-using-sqlrelationship-sqlxml-40"></a><span data-ttu-id="212d2-102">sql:relationship を使用した、リレーションシップの指定 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="212d2-102">Specifying Relationships Using sql:relationship (SQLXML 4.0)</span></span>
  <span data-ttu-id="212d2-103">XML ドキュメント内の要素は関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="212d2-103">The elements in an XML document can be related.</span></span> <span data-ttu-id="212d2-104">要素は階層的に入れ子にでき、要素間に ID、IDREF、または IDREFS のリレーションシップを指定することができます。</span><span class="sxs-lookup"><span data-stu-id="212d2-104">The elements can be nested hierarchically, and ID, IDREF, or IDREFS relationships can be specified between the elements.</span></span>  
  
 <span data-ttu-id="212d2-105">たとえば、XSD スキーマでは、要素に **\<Customer>** 子要素が含まれてい **\<Order>** ます。</span><span class="sxs-lookup"><span data-stu-id="212d2-105">For example, in an XSD schema, a **\<Customer>** element contains **\<Order>** child elements.</span></span> <span data-ttu-id="212d2-106">スキーマを AdventureWorks データベースにマップすると、要素は **\<Customer>** sales. Customer テーブルにマップされ、 **\<Order>** 要素は SalesOrderHeader テーブルにマップされます。</span><span class="sxs-lookup"><span data-stu-id="212d2-106">When the schema is mapped to the AdventureWorks database, the **\<Customer>** element maps to the Sales.Customer table and the **\<Order>** element maps to the Sales.SalesOrderHeader table.</span></span> <span data-ttu-id="212d2-107">これらの基になるテーブル (Sales. Customer および SalesOrderHeader) は、顧客が注文を配置するため、関連付けられています。</span><span class="sxs-lookup"><span data-stu-id="212d2-107">These underlying tables, Sales.Customer and Sales.SalesOrderHeader, are related because customers place orders.</span></span> <span data-ttu-id="212d2-108">ここで、Sales.SalesOrderHeader テーブル内の CustomerID は、Sales.Customer テーブル内の CustomerID 主キーを参照する外部キーです。</span><span class="sxs-lookup"><span data-stu-id="212d2-108">The CustomerID in the Sales.SalesOrderHeader table is a foreign key referring to the CustomerID primary key in the Sales.Customer table.</span></span> <span data-ttu-id="212d2-109">注釈を使用すると、マッピングスキーマ要素間にこれらのリレーションシップを設定でき `sql:relationship` ます。</span><span class="sxs-lookup"><span data-stu-id="212d2-109">You can establish these relationships among mapping schema elements by using the `sql:relationship` annotation.</span></span>  
  
 <span data-ttu-id="212d2-110">注釈付き XSD スキーマでは、`sql:relationship` 注釈を使用して、要素のマップ先テーブルにおける主キーと外部キーのリレーションシップを基にスキーマ要素を階層的に入れ子にできます。</span><span class="sxs-lookup"><span data-stu-id="212d2-110">In the annotated XSD schema, the `sql:relationship` annotation is used to nest the schema elements hierarchically, on the basis of primary key and foreign key relationships among the underlying tables to which the elements map.</span></span> <span data-ttu-id="212d2-111">注釈を指定するときは、 `sql:relationship` 次のことを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="212d2-111">In specifying the `sql:relationship` annotation, you must identify the following:</span></span>  
  
-   <span data-ttu-id="212d2-112">親テーブル (Sales.Customer) と子テーブル (Sales.SalesOrderHeader)。</span><span class="sxs-lookup"><span data-stu-id="212d2-112">The parent table (Sales.Customer) and the child table (Sales.SalesOrderHeader).</span></span>  
  
-   <span data-ttu-id="212d2-113">親テーブルと子テーブル間のリレーションシップを構成する列。</span><span class="sxs-lookup"><span data-stu-id="212d2-113">The column or columns that compose the relationship between the parent and child tables.</span></span> <span data-ttu-id="212d2-114">たとえば、親テーブルと子テーブル両方にある CustomerID 列を指定します。</span><span class="sxs-lookup"><span data-stu-id="212d2-114">For example, the CustomerID column, which appears in both the parent and child tables.</span></span>  
  
 <span data-ttu-id="212d2-115">これらの情報を使用して、適切な階層が生成されます。</span><span class="sxs-lookup"><span data-stu-id="212d2-115">This information is used to generate the proper hierarchy.</span></span>  
  
 <span data-ttu-id="212d2-116">テーブル名と必要な結合情報を指定するために、注釈には次の属性が指定されてい `sql:relationship` ます。</span><span class="sxs-lookup"><span data-stu-id="212d2-116">To provide the table names and the necessary join information, the following attributes are specified on the `sql:relationship` annotation.</span></span> <span data-ttu-id="212d2-117">これらの属性は、要素でのみ有効です **\<sql:relationship>** 。</span><span class="sxs-lookup"><span data-stu-id="212d2-117">These attributes are valid only with the **\<sql:relationship>** element:</span></span>  
  
 <span data-ttu-id="212d2-118">**名前**</span><span class="sxs-lookup"><span data-stu-id="212d2-118">**Name**</span></span>  
 <span data-ttu-id="212d2-119">リレーションシップの一意な名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="212d2-119">Specifies the unique name of the relationship.</span></span>  
  
 <span data-ttu-id="212d2-120">**Parent**</span><span class="sxs-lookup"><span data-stu-id="212d2-120">**Parent**</span></span>  
 <span data-ttu-id="212d2-121">親リレーション (テーブル) を指定します。</span><span class="sxs-lookup"><span data-stu-id="212d2-121">Specifies the parent relation (table).</span></span> <span data-ttu-id="212d2-122">これは省略可能な属性です。この属性を指定しない場合、親テーブル名はドキュメント内の子階層の情報から取得されます。</span><span class="sxs-lookup"><span data-stu-id="212d2-122">This is an optional attribute; if the attribute is not specified, the parent table name is obtained from information in the child hierarchy in the document.</span></span> <span data-ttu-id="212d2-123">同じでも異なる親要素を使用する2つの親子階層がスキーマで指定されている場合は、 **\<sql:relationship>** で親属性を指定しません **\<sql:relationship>** 。</span><span class="sxs-lookup"><span data-stu-id="212d2-123">If the schema specifies two parent-child hierarchies that use the same **\<sql:relationship>** but different parent elements, you do not specify the parent attribute in **\<sql:relationship>**.</span></span> <span data-ttu-id="212d2-124">この情報はスキーマ内の階層から取得されます。</span><span class="sxs-lookup"><span data-stu-id="212d2-124">This information is obtained from the hierarchy in the schema.</span></span>  
  
 <span data-ttu-id="212d2-125">**parent-key**</span><span class="sxs-lookup"><span data-stu-id="212d2-125">**parent-key**</span></span>  
 <span data-ttu-id="212d2-126">親の親キーを指定します。</span><span class="sxs-lookup"><span data-stu-id="212d2-126">Specifies the parent key of the parent.</span></span> <span data-ttu-id="212d2-127">親キーが複数の列で構成される場合は、値をスペースで区切って指定します。</span><span class="sxs-lookup"><span data-stu-id="212d2-127">If the parent key is composed of multiple columns, values are specified with a space between them.</span></span> <span data-ttu-id="212d2-128">複数列キーに指定される値と、それに対応する子キーに指定される値の間では、位置的なマッピングが行われます。</span><span class="sxs-lookup"><span data-stu-id="212d2-128">There is a positional mapping between the values that are specified for the multicolumn key and for the corresponding child key.</span></span>  
  
 <span data-ttu-id="212d2-129">**子供**</span><span class="sxs-lookup"><span data-stu-id="212d2-129">**Child**</span></span>  
 <span data-ttu-id="212d2-130">子リレーション (テーブル) を指定します。</span><span class="sxs-lookup"><span data-stu-id="212d2-130">Specifies the child relation (table).</span></span>  
  
 <span data-ttu-id="212d2-131">**child-key**</span><span class="sxs-lookup"><span data-stu-id="212d2-131">**child-key**</span></span>  
 <span data-ttu-id="212d2-132">親の parent-key を参照する子の、子キーを指定します。</span><span class="sxs-lookup"><span data-stu-id="212d2-132">Specifies the child key in the child referring to parent-key in parent.</span></span> <span data-ttu-id="212d2-133">子キーが複数の属性 (列) で構成される場合、child-key の値は、スペースで区切って指定します。</span><span class="sxs-lookup"><span data-stu-id="212d2-133">If the child key is composed of multiple attributes (columns), the child-key values are specified with a space between them.</span></span> <span data-ttu-id="212d2-134">複数列キーに指定される値と、それに対応する親キーに指定される値の間では、位置的なマッピングが行われます。</span><span class="sxs-lookup"><span data-stu-id="212d2-134">There is a positional mapping between the values that are specified for the multicolumn key and for the corresponding parent key.</span></span>  
  
 <span data-ttu-id="212d2-135">**逆条件**</span><span class="sxs-lookup"><span data-stu-id="212d2-135">**Inverse**</span></span>  
 <span data-ttu-id="212d2-136">で指定されたこの属性 **\<sql:relationship>** は、アップデートグラムによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="212d2-136">This attribute specified on **\<sql:relationship>** is used by updategrams.</span></span> <span data-ttu-id="212d2-137">詳細については、「sql [: relationship での sql: 逆属性の指定](specifying-the-sql-inverse-attribute-on-sql-relationship-sqlxml-4-0.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="212d2-137">For more information, see [Specifying the sql:inverse Attribute on sql:relationship](specifying-the-sql-inverse-attribute-on-sql-relationship-sqlxml-4-0.md).</span></span>  
  
 <span data-ttu-id="212d2-138">注釈は、 `sql:key-fields` 子要素を含む要素で指定する必要があります。この要素には、 **\<sql:relationship>** 要素と子の間にが定義され、親要素で指定されたテーブルの主キーは提供されません。</span><span class="sxs-lookup"><span data-stu-id="212d2-138">The `sql:key-fields` annotation must be specified in an element that contains a child element, that has a **\<sql:relationship>** defined between the element and the child, and that does not provide the primary key of the table specified in the parent element.</span></span> <span data-ttu-id="212d2-139">スキーマでが指定されていない場合でも **\<sql:relationship>** 、 `sql:key-fields` 適切な階層を生成するようにを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="212d2-139">Even if the schema does not specify **\<sql:relationship>**, you must specify `sql:key-fields` to produce the proper hierarchy.</span></span> <span data-ttu-id="212d2-140">詳細については、「 [sql: キーフィールドを使用したキー列の識別](identifying-key-columns-using-sql-key-fields-sqlxml-4-0.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="212d2-140">For more information, see [Identifying Key Columns by Using sql:key-fields](identifying-key-columns-using-sql-key-fields-sqlxml-4-0.md).</span></span>  
  
 <span data-ttu-id="212d2-141">結果に適切な入れ子を生成するには、すべてのスキーマでを指定することをお勧めし `sql:key-fields` ます。</span><span class="sxs-lookup"><span data-stu-id="212d2-141">To produce proper nesting in the result, it is recommended that `sql:key-fields` are specified in all schemas.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="212d2-142">例</span><span class="sxs-lookup"><span data-stu-id="212d2-142">Examples</span></span>  
 <span data-ttu-id="212d2-143">次の例を使用した実際のサンプルを作成するには、特定の条件を満たす必要があります。</span><span class="sxs-lookup"><span data-stu-id="212d2-143">To create working samples using the following examples, you must meet certain requirements.</span></span> <span data-ttu-id="212d2-144">詳細については、「 [SQLXML の例を実行するための要件](../sqlxml/requirements-for-running-sqlxml-examples.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="212d2-144">For more information, see [Requirements for Running SQLXML Examples](../sqlxml/requirements-for-running-sqlxml-examples.md).</span></span>  
  
### <a name="a-specifying-the-sqlrelationship-annotation-on-an-element"></a><span data-ttu-id="212d2-145">A.</span><span class="sxs-lookup"><span data-stu-id="212d2-145">A.</span></span> <span data-ttu-id="212d2-146">要素に sql:relationship 注釈を指定する</span><span class="sxs-lookup"><span data-stu-id="212d2-146">Specifying the sql:relationship annotation on an element</span></span>  
 <span data-ttu-id="212d2-147">次の注釈付き XSD スキーマには、要素と要素が含まれてい **\<Customer>** **\<Order>** ます。</span><span class="sxs-lookup"><span data-stu-id="212d2-147">The following annotated XSD schema includes **\<Customer>** and **\<Order>** elements.</span></span> <span data-ttu-id="212d2-148">**\<Order>** 要素は要素の子要素です **\<Customer>** 。</span><span class="sxs-lookup"><span data-stu-id="212d2-148">The **\<Order>** element is a child element of the **\<Customer>** element.</span></span>  
  
 <span data-ttu-id="212d2-149">スキーマで `sql:relationship` は、子要素に注釈が指定されて **\<Order>** います。</span><span class="sxs-lookup"><span data-stu-id="212d2-149">In the schema, the `sql:relationship` annotation is specified on the **\<Order>** child element.</span></span> <span data-ttu-id="212d2-150">リレーションシップ自体は、要素で定義され **\<xsd:appinfo>** ます。</span><span class="sxs-lookup"><span data-stu-id="212d2-150">The relationship itself is defined in the **\<xsd:appinfo>** element.</span></span>  
  
 <span data-ttu-id="212d2-151">要素は、 **\<relationship>** SalesOrderHeader テーブルの customerid を外部キーとして識別します。これは、sales. Customer テーブルの customerid 主キーを参照します。</span><span class="sxs-lookup"><span data-stu-id="212d2-151">The **\<relationship>** element identifies CustomerID in the Sales.SalesOrderHeader table as a foreign key that refers to the CustomerID primary key in the Sales.Customer table.</span></span> <span data-ttu-id="212d2-152">したがって、顧客に属する注文は、その要素の子要素として表示され **\<Customer>** ます。</span><span class="sxs-lookup"><span data-stu-id="212d2-152">Therefore, orders that belong to a customer appear as a child element of that **\<Customer>** element.</span></span>  
  
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
  </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="Customer" sql:relation="Sales.Customer" type="CustomerType" />  
   <xsd:complexType name="CustomerType" >  
     <xsd:sequence>  
        <xsd:element name="Order"   
                     sql:relation="Sales.SalesOrderHeader"  
                    sql:relationship="CustOrders" >  
           <xsd:complexType>  
              <xsd:attribute name="SalesOrderID" type="xsd:integer" />  
              <xsd:attribute name="CustomerID" type="xsd:string" />  
           </xsd:complexType>  
        </xsd:element>  
     </xsd:sequence>  
        <xsd:attribute name="CustomerID"   type="xsd:string" />   
    </xsd:complexType>  
  
</xsd:schema>  
```  
  
 <span data-ttu-id="212d2-153">上のスキーマでは名前付きリレーションシップを使用しましたが、</span><span class="sxs-lookup"><span data-stu-id="212d2-153">The previous schema uses a named relationship.</span></span> <span data-ttu-id="212d2-154">名前のないリレーションシップを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="212d2-154">You can also specify an unnamed relationship.</span></span> <span data-ttu-id="212d2-155">この結果は同じです。</span><span class="sxs-lookup"><span data-stu-id="212d2-155">The results are same.</span></span>  
  
 <span data-ttu-id="212d2-156">次は、スキーマを変更し、名前のないリレーションシップを指定した例です。</span><span class="sxs-lookup"><span data-stu-id="212d2-156">This is the revised schema in which an unnamed relationship is specified:</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  
  <xsd:element name="Customer" sql:relation="Sales.Customer"  type="CustomerType" />  
   <xsd:complexType name="CustomerType" >  
     <xsd:sequence>  
        <xsd:element name="Order"   
                     sql:relation="Sales.SalesOrderHeader">  
           <xsd:annotation>  
            <xsd:appinfo>  
              <sql:relationship   
                parent="Sales.Customer"  
                parent-key="CustomerID"  
                child="Sales.SalesOrderHeader"  
                child-key="CustomerID" />  
            </xsd:appinfo>  
           </xsd:annotation>  
           <xsd:complexType>  
              <xsd:attribute name="SalesOrderID" type="xsd:integer" />  
              <xsd:attribute name="CustomerID" type="xsd:string" />  
           </xsd:complexType>  
        </xsd:element>  
     </xsd:sequence>  
        <xsd:attribute name="CustomerID"   type="xsd:string" />   
    </xsd:complexType>  
  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a><span data-ttu-id="212d2-157">スキーマに対してサンプル XPath クエリをテストするには</span><span class="sxs-lookup"><span data-stu-id="212d2-157">To test a sample XPath query against the schema</span></span>  
  
1.  <span data-ttu-id="212d2-158">上のスキーマのコードをコピーして、テキスト ファイルに貼り付け、</span><span class="sxs-lookup"><span data-stu-id="212d2-158">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="212d2-159">sql-relationship.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="212d2-159">Save the file as sql-relationship.xml.</span></span>  
  
2.  <span data-ttu-id="212d2-160">次のテンプレートをコピーし、テキストファイルに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="212d2-160">Copy the following template below and paste it into a text file.</span></span> <span data-ttu-id="212d2-161">sql-relationship.xml を保存したディレクトリに sql-relationshipT.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="212d2-161">Save the file as sql-relationshipT.xml in the same directory where you saved sql-relationship.xml.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="sql-relationship.xml">  
            /Customer[@CustomerID=1]  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="212d2-162">マッピング スキーマ (sql-relationship.xml) に指定するディレクトリ パスは、テンプレートを保存するディレクトリに対する相対パスです。</span><span class="sxs-lookup"><span data-stu-id="212d2-162">The directory path specified for the mapping schema (sql-relationship.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="212d2-163">次のように、絶対パスを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="212d2-163">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\sql-relationship.xml"  
    ```  
  
3.  <span data-ttu-id="212d2-164">SQLXML 4.0 テスト スクリプト (sqlxml4test.vbs) を作成し、それを使用してテンプレートを実行します。</span><span class="sxs-lookup"><span data-stu-id="212d2-164">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="212d2-165">詳細については、「ADO を使用した[SQLXML クエリの実行](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="212d2-165">For more information, see [Using ADO to Execute SQLXML Queries](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="212d2-166">結果セットは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="212d2-166">Here is the result set:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">   
  <Customer CustomerID="1">   
    <Order OrderID="43860" CustomerID="1" />   
    <Order OrderID="44501" CustomerID="1" />   
    <Order OrderID="45283" CustomerID="1" />   
    <Order OrderID="46042" CustomerID="1" />   
  </Customer>   
</ROOT>  
```  
  
### <a name="b-specifying-a-relationship-chain"></a><span data-ttu-id="212d2-167">B.</span><span class="sxs-lookup"><span data-stu-id="212d2-167">B.</span></span> <span data-ttu-id="212d2-168">リレーションシップ チェーンを指定する</span><span class="sxs-lookup"><span data-stu-id="212d2-168">Specifying a relationship chain</span></span>  
 <span data-ttu-id="212d2-169">この例では、AdventureWorks データベースから取得したデータを使用して、次の XML ドキュメントを要求するとします。</span><span class="sxs-lookup"><span data-stu-id="212d2-169">For this example, assume that you want the following XML document using data obtained from the AdventureWorks database:</span></span>  
  
```  
<Order SalesOrderID="43659">  
  <Product Name="Mountain Bike Socks, M"/>   
  <Product Name="Sport-100 Helmet, Blue"/>  
  ...  
</Order>  
...  
```  
  
 <span data-ttu-id="212d2-170">SalesOrderHeader テーブル内の各注文に対して、XML ドキュメントには1つの要素があり **\<Order>** ます。</span><span class="sxs-lookup"><span data-stu-id="212d2-170">For each order in the Sales.SalesOrderHeader table, the XML document has one **\<Order>** element.</span></span> <span data-ttu-id="212d2-171">各 **\<Order>** 要素には **\<Product>** 、注文で要求された製品ごとに1つの子要素のリストがあります。</span><span class="sxs-lookup"><span data-stu-id="212d2-171">And each **\<Order>** element has a list of **\<Product>** child elements, one for each product requested in the order.</span></span>  
  
 <span data-ttu-id="212d2-172">この階層を生成する XSD スキーマを指定するには、OrderOD と ODProduct の 2 つのリレーションシップを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="212d2-172">To specify an XSD schema that will produce this hierarchy, you must specify two relationships: OrderOD and ODProduct.</span></span> <span data-ttu-id="212d2-173">OrderOD リレーションシップでは、Sales.SalesOrderHeader テーブルと Sales.SalesOrderDetail テーブル間の親子リレーションシップを指定します。</span><span class="sxs-lookup"><span data-stu-id="212d2-173">The OrderOD relationship specifies the parent-child relationship between the Sales.SalesOrderHeader and Sales.SalesOrderDetail tables.</span></span> <span data-ttu-id="212d2-174">ODProduct リレーションシップでは、Sales.SalesOrderDetail テーブルと Production.Product テーブル間のリレーションシップを指定します。</span><span class="sxs-lookup"><span data-stu-id="212d2-174">The ODProduct relationship specifies the relationship between the Sales.SalesOrderDetail and Production.Product tables.</span></span>  
  
 <span data-ttu-id="212d2-175">次のスキーマでは、 `msdata:relationship` 要素の注釈に **\<Product>** orderod と ODProduct の2つの値が指定されています。</span><span class="sxs-lookup"><span data-stu-id="212d2-175">In the following schema, the `msdata:relationship` annotation on the **\<Product>** element specifies two values: OrderOD and ODProduct.</span></span> <span data-ttu-id="212d2-176">これらの値の指定順序は重要です。</span><span class="sxs-lookup"><span data-stu-id="212d2-176">The order in which these values are specified is important.</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:msdata="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <msdata:relationship name="OrderOD"  
          parent="Sales.SalesOrderHeader"  
          parent-key="SalesOrderID"  
          child="Sales.SalesOrderDetail"  
          child-key="SalesOrderID" />  
  
    <msdata:relationship name="ODProduct"  
          parent="Sales.SalesOrderDetail"  
          parent-key="ProductID"  
          child="Production.Product"  
          child-key="ProductID" />  
  </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="Order" msdata:relation="Sales.SalesOrderHeader"   
               msdata:key-fields="SalesOrderID" type="OrderType" />  
   <xsd:complexType name="OrderType" >  
     <xsd:sequence>  
        <xsd:element name="Product" msdata:relation="Production.Product"   
                     msdata:key-fields="ProductID"  
                     msdata:relationship="OrderOD ODProduct">  
          <xsd:complexType>  
             <xsd:attribute name="Name" type="xsd:string" />  
          </xsd:complexType>  
        </xsd:element>  
     </xsd:sequence>  
        <xsd:attribute name="SalesOrderID"   type="xsd:integer" />   
    </xsd:complexType>  
</xsd:schema>  
```  
  
 <span data-ttu-id="212d2-177">名前付きリレーションシップを指定する代わりに、匿名のリレーションシップを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="212d2-177">Instead of specifying a named relationship, you can specify an anonymous relationship.</span></span> <span data-ttu-id="212d2-178">この場合、2つのリレーションシップを記述する... の内容全体が、 **\<annotation>** **\</annotation>** の子要素として表示されます。 **\<Product>**</span><span class="sxs-lookup"><span data-stu-id="212d2-178">In this case, the entire contents of **\<annotation>**...**\</annotation>**, which describes the two relationships, appear as a child element of **\<Product>**.</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:msdata="urn:schemas-microsoft-com:mapping-schema">  
  
  <xsd:element name="Order" msdata:relation="Sales.SalesOrderHeader"   
               msdata:key-fields="SalesOrderID" type="OrderType" />  
  
   <xsd:complexType name="OrderType" >  
     <xsd:sequence>  
        <xsd:element name="Product" msdata:relation="Production.Product"   
                     msdata:key-fields="ProductID" >  
         <xsd:annotation>  
          <xsd:appinfo>  
           <msdata:relationship   
               parent="Sales.SalesOrderHeader"  
               parent-key="SalesOrderID"  
               child="Sales.SalesOrderDetail"  
               child-key="SalesOrderID" />  
  
           <msdata:relationship   
               parent="Sales.SalesOrderDetail"  
               parent-key="ProductID"  
               child="Production.Product"  
               child-key="ProductID" />  
         </xsd:appinfo>  
       </xsd:annotation>  
       <xsd:complexType>  
          <xsd:attribute name="Name" type="xsd:string" />  
       </xsd:complexType>  
     </xsd:element>  
   </xsd:sequence>  
   <xsd:attribute name="SalesOrderID"   type="xsd:integer" />   
  </xsd:complexType>  
 </xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a><span data-ttu-id="212d2-179">スキーマに対してサンプル XPath クエリをテストするには</span><span class="sxs-lookup"><span data-stu-id="212d2-179">To test a sample XPath query against the schema</span></span>  
  
1.  <span data-ttu-id="212d2-180">上のスキーマのコードをコピーして、テキスト ファイルに貼り付け、</span><span class="sxs-lookup"><span data-stu-id="212d2-180">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="212d2-181">relationshipChain.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="212d2-181">Save the file as relationshipChain.xml.</span></span>  
  
2.  <span data-ttu-id="212d2-182">次のテンプレートをコピーし、テキストファイルに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="212d2-182">Copy the following template below and paste it into a text file.</span></span> <span data-ttu-id="212d2-183">relationshipChain.xml を保存したディレクトリに relationshipChainT.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="212d2-183">Save the file as relationshipChainT.xml in the same directory where you saved relationshipChain.xml.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="relationshipChain.xml">  
            /Order  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="212d2-184">マッピング スキーマ (relationshipChain.xml) に指定するディレクトリ パスは、テンプレートを保存するディレクトリに対する相対パスです。</span><span class="sxs-lookup"><span data-stu-id="212d2-184">The directory path specified for the mapping schema (relationshipChain.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="212d2-185">次のように、絶対パスを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="212d2-185">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\relationshipChain.xml"  
    ```  
  
3.  <span data-ttu-id="212d2-186">SQLXML 4.0 テスト スクリプト (sqlxml4test.vbs) を作成し、それを使用してテンプレートを実行します。</span><span class="sxs-lookup"><span data-stu-id="212d2-186">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="212d2-187">詳細については、「ADO を使用した[SQLXML クエリの実行](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="212d2-187">For more information, see [Using ADO to Execute SQLXML Queries](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="212d2-188">結果セットは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="212d2-188">Here is the result set:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">   
  <Order SalesOrderID="43659">  
    <Product Name="Mountain Bike Socks, M" />   
    <Product Name="Sport-100 Helmet, Blue" />   
    <Product Name="AWC Logo Cap" />   
    <Product Name="Long-Sleeve Logo Jersey, M" />   
    <Product Name="Long-Sleeve Logo Jersey, XL" />   
    ...  
  </Order>  
  ...  
</ROOT>  
```  
  
### <a name="c-specifying-the-relationship-annotation-on-an-attribute"></a><span data-ttu-id="212d2-189">C.</span><span class="sxs-lookup"><span data-stu-id="212d2-189">C.</span></span> <span data-ttu-id="212d2-190">属性にリレーションシップ注釈を指定する</span><span class="sxs-lookup"><span data-stu-id="212d2-190">Specifying the relationship annotation on an attribute</span></span>  
 <span data-ttu-id="212d2-191">この例のスキーマには、 \<Customer> 子要素を持ち、 \<CustomerID> IDREFS 型の OrderIDList 属性を持つ要素が含まれています。</span><span class="sxs-lookup"><span data-stu-id="212d2-191">The schema in this example includes a \<Customer> element with a \<CustomerID> child element and an OrderIDList attribute of IDREFS type.</span></span> <span data-ttu-id="212d2-192">要素は、 \<Customer> AdventureWorks データベースの Sales. Customer テーブルにマップされます。</span><span class="sxs-lookup"><span data-stu-id="212d2-192">The \<Customer> element maps to the Sales.Customer table in the AdventureWorks database.</span></span> <span data-ttu-id="212d2-193">既定では、このマッピングのスコープは、子要素または属性にが指定されていない限り、すべての子要素または属性に適用され `sql:relation` ます。この場合、要素を使用して、適切な主キー/外部キーのリレーションシップを定義する必要があり \<relationship> ます。</span><span class="sxs-lookup"><span data-stu-id="212d2-193">By default, the scope of this mapping applies to all the child elements or attributes unless `sql:relation` is specified on the child element or attribute, in which case, the appropriate primary-key/foreign-key relationship must be defined using the \<relationship> element.</span></span> <span data-ttu-id="212d2-194">子要素または属性で `relation` 注釈を使って異なるテーブルを指定する場合は、`relationship` 注釈も指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="212d2-194">And the child element or attribute, which specifies the different table using the `relation` annotation, must also specify the `relationship` annotation.</span></span>  
  
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
     </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="Customer" sql:relation="Sales.Customer" type="CustomerType" />  
   <xsd:complexType name="CustomerType" >  
     <xsd:sequence>  
        <xsd:element name="CustomerID"   type="xsd:string" />   
     </xsd:sequence>  
     <xsd:attribute name="OrderIDList"   
                     type="xsd:IDREFS"   
                     sql:relation="Sales.SalesOrderHeader"   
                     sql:field="SalesOrderID"  
                     sql:relationship="CustOrders" >  
        </xsd:attribute>  
    </xsd:complexType>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a><span data-ttu-id="212d2-195">スキーマに対してサンプル XPath クエリをテストするには</span><span class="sxs-lookup"><span data-stu-id="212d2-195">To test a sample XPath query against the schema</span></span>  
  
1.  <span data-ttu-id="212d2-196">上のスキーマのコードをコピーして、テキスト ファイルに貼り付け、</span><span class="sxs-lookup"><span data-stu-id="212d2-196">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="212d2-197">relationship-on-attribute.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="212d2-197">Save the file as relationship-on-attribute.xml.</span></span>  
  
2.  <span data-ttu-id="212d2-198">次のテンプレートをコピーして、ファイルに貼り付け、</span><span class="sxs-lookup"><span data-stu-id="212d2-198">Copy the following template and paste it into a file.</span></span> <span data-ttu-id="212d2-199">relationship-on-attribute.xml を保存したディレクトリに relationship-on-attributeT.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="212d2-199">Save the file as relationship-on-attributeT.xml in the same directory where you saved relationship-on-attribute.xml.</span></span> <span data-ttu-id="212d2-200">このテンプレートのクエリでは、CustomerID が 1 の顧客が選択されます。</span><span class="sxs-lookup"><span data-stu-id="212d2-200">The query in the template selects a customer with the CustomerID of 1.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="relationship-on-attribute.xml">  
        /Customer[CustomerID=1]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="212d2-201">マッピング スキーマ (relationship-on-attribute.xml) に指定するディレクトリ パスは、テンプレートを保存するディレクトリに対する相対パスです。</span><span class="sxs-lookup"><span data-stu-id="212d2-201">The directory path specified for the mapping schema (relationship-on-attribute.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="212d2-202">次のように、絶対パスを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="212d2-202">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\relationship-on-attribute.xml"  
    ```  
  
3.  <span data-ttu-id="212d2-203">SQLXML 4.0 テスト スクリプト (sqlxml4test.vbs) を作成し、それを使用してテンプレートを実行します。</span><span class="sxs-lookup"><span data-stu-id="212d2-203">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="212d2-204">詳細については、「ADO を使用した[SQLXML クエリの実行](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="212d2-204">For more information, see [Using ADO to Execute SQLXML Queries](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="212d2-205">結果セットは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="212d2-205">Here is the result set:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">   
  <Customer OrderIDList="43860 44501 45283 46042">  
    <CustomerID>1</CustomerID>   
  </Customer>  
</ROOT>  
```  
  
### <a name="d-specifying-sqlrelationship-on-multiple-elements"></a><span data-ttu-id="212d2-206">D.</span><span class="sxs-lookup"><span data-stu-id="212d2-206">D.</span></span> <span data-ttu-id="212d2-207">複数の要素に sql:relationship を指定する</span><span class="sxs-lookup"><span data-stu-id="212d2-207">Specifying sql:relationship on multiple elements</span></span>  
 <span data-ttu-id="212d2-208">この例では、注釈付き XSD スキーマには、、、およびの各要素が含まれてい **\<Customer>** **\<Order>** **\<OrderDetail>** ます。</span><span class="sxs-lookup"><span data-stu-id="212d2-208">In this example, the annotated XSD schema contains the **\<Customer>**, **\<Order>**, and **\<OrderDetail>** elements.</span></span>  
  
 <span data-ttu-id="212d2-209">**\<Order>** 要素は要素の子要素です **\<Customer>** 。</span><span class="sxs-lookup"><span data-stu-id="212d2-209">The **\<Order>** element is a child element of the **\<Customer>** element.</span></span> <span data-ttu-id="212d2-210">**\<sql:relationship>** は子要素で指定されます **\<Order>** 。したがって、顧客に属する注文は、の子要素として表示され **\<Customer>** ます。</span><span class="sxs-lookup"><span data-stu-id="212d2-210">**\<sql:relationship>** is specified on the **\<Order>** child element; therefore, orders that belong to a customer appear as child elements of **\<Customer>**.</span></span>  
  
 <span data-ttu-id="212d2-211">要素には **\<Order>** 、 **\<OrderDetail>** 子要素が含まれます。</span><span class="sxs-lookup"><span data-stu-id="212d2-211">The **\<Order>** element includes the **\<OrderDetail>** child element.</span></span> <span data-ttu-id="212d2-212">**\<sql:relationship>** は子要素で指定されているため、 **\<OrderDetail>** 注文に関連する注文の詳細は、その要素の子要素として表示され **\<Order>** ます。</span><span class="sxs-lookup"><span data-stu-id="212d2-212">**\<sql:relationship>** is specified on **\<OrderDetail>** child element, so the order details that pertain to an order appear as child elements of that **\<Order>** element.</span></span>  
  
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
              <xsd:attribute name="SalesOrderID" type="xsd:integer" />  
              <xsd:attribute name="OrderDate" type="xsd:date" />  
              <xsd:attribute name="CustomerID" type="xsd:string" />  
          </xsd:complexType>  
        </xsd:element>  
      </xsd:sequence>  
      <xsd:attribute name="CustomerID" type="xsd:string" />  
     </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a><span data-ttu-id="212d2-213">スキーマに対してサンプル XPath クエリをテストするには</span><span class="sxs-lookup"><span data-stu-id="212d2-213">To test a sample XPath query against the schema</span></span>  
  
1.  <span data-ttu-id="212d2-214">上のスキーマのコードをコピーして、テキスト ファイルに貼り付け、</span><span class="sxs-lookup"><span data-stu-id="212d2-214">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="212d2-215">relationship-multiple-elements.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="212d2-215">Save the file as relationship-multiple-elements.xml.</span></span>  
  
2.  <span data-ttu-id="212d2-216">次のテンプレートをコピーして、テキスト ファイルに貼り付け、</span><span class="sxs-lookup"><span data-stu-id="212d2-216">Copy the following template and paste it into a text file.</span></span> <span data-ttu-id="212d2-217">relationship-multiple-elements.xml を保存したディレクトリに relationship-multiple-elementsT.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="212d2-217">Save the file as relationship-multiple-elementsT.xml in the same directory where you saved relationship-multiple-elements.xml.</span></span> <span data-ttu-id="212d2-218">このテンプレート内のクエリでは、CustomerID が 1、SalesOrderID が 43860 の顧客の注文情報が返されます。</span><span class="sxs-lookup"><span data-stu-id="212d2-218">The query in the template returns order information for a customer with the CustomerID of 1 and SalesOrderID of 43860.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="relationship-multiple-elements.xml">  
        /Customer[@CustomerID=1]/Order[@SalesOrderID=43860]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="212d2-219">マッピング スキーマ (relationship-multiple-elements.xml) に指定するディレクトリ パスは、テンプレートを保存するディレクトリに対する相対パスです。</span><span class="sxs-lookup"><span data-stu-id="212d2-219">The directory path specified for the mapping schema (relationship-multiple-elements.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="212d2-220">次のように、絶対パスを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="212d2-220">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\relationship-multiple-elements.xml"  
    ```  
  
3.  <span data-ttu-id="212d2-221">SQLXML 4.0 テスト スクリプト (sqlxml4test.vbs) を作成し、それを使用してテンプレートを実行します。</span><span class="sxs-lookup"><span data-stu-id="212d2-221">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="212d2-222">詳細については、「ADO を使用した[SQLXML クエリの実行](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="212d2-222">For more information, see [Using ADO to Execute SQLXML Queries](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="212d2-223">結果セットは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="212d2-223">Here is the result set:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Order SalesOrderID="43860" OrderDate="2001-08-01" CustomerID="1">  
     <OrderDetail SalesOrderID="43860" ProductID="761" OrderQty="2" />   
     <OrderDetail SalesOrderID="43860" ProductID="770" OrderQty="1" />   
     <OrderDetail SalesOrderID="43860" ProductID="758" OrderQty="2" />   
     <OrderDetail SalesOrderID="43860" ProductID="765" OrderQty="2" />   
     <OrderDetail SalesOrderID="43860" ProductID="732" OrderQty="1" />   
     <OrderDetail SalesOrderID="43860" ProductID="762" OrderQty="1" />   
     <OrderDetail SalesOrderID="43860" ProductID="738" OrderQty="1" />   
     <OrderDetail SalesOrderID="43860" ProductID="768" OrderQty="1" />   
     <OrderDetail SalesOrderID="43860" ProductID="753" OrderQty="2" />   
     <OrderDetail SalesOrderID="43860" ProductID="729" OrderQty="1" />   
     <OrderDetail SalesOrderID="43860" ProductID="763" OrderQty="1" />   
     <OrderDetail SalesOrderID="43860" ProductID="756" OrderQty="1" />   
  </Order>  
</ROOT>  
```  
  
### <a name="e-specifying-the-sqlrelationship-without-the-parent-attribute"></a><span data-ttu-id="212d2-224">E.</span><span class="sxs-lookup"><span data-stu-id="212d2-224">E.</span></span> <span data-ttu-id="212d2-225">\<sql:relationship>親属性を指定せずにを指定する</span><span class="sxs-lookup"><span data-stu-id="212d2-225">Specifying the \<sql:relationship> without the parent attribute</span></span>  
 <span data-ttu-id="212d2-226">この例では、親属性を指定せずにを指定してい **\<sql:relationship>** ます。 **parent**</span><span class="sxs-lookup"><span data-stu-id="212d2-226">This example illustrates specifying the **\<sql:relationship>** without the **parent** attribute.</span></span> <span data-ttu-id="212d2-227">たとえば、次の従業員テーブルがあるとします。</span><span class="sxs-lookup"><span data-stu-id="212d2-227">For example, assume you have the following employee tables:</span></span>  
  
```  
Emp1(SalesPersonID, FirstName, LastName, ReportsTo)  
Emp2(SalesPersonID, FirstName, LastName, ReportsTo)  
```  
  
 <span data-ttu-id="212d2-228">次の XML ビューには **\<Emp1>** 、 **\<Emp2>** Emp1 テーブルと Emp2 テーブルにマッピングされる要素と要素があります。</span><span class="sxs-lookup"><span data-stu-id="212d2-228">The following XML view has the **\<Emp1>** and **\<Emp2>** elements mapping to the Sales.Emp1 and Sales.Emp2 tables:</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="EmpOrders"  
          parent-key="SalesPersonID"  
          child="Sales.SalesOrderHeader"  
          child-key="SalesPersonID" />  
     </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="Emp1" sql:relation="Sales.Emp1" type="EmpType" />  
  <xsd:element name="Emp2" sql:relation="Sales.Emp2" type="EmpType" />  
   <xsd:complexType name="EmpType" >  
     <xsd:sequence>  
        <xsd:element name="Order"   
                     sql:relation="Sales.SalesOrderHeader"   
                     sql:relationship="EmpOrders" >  
          <xsd:complexType>  
             <xsd:attribute name="SalesOrderID" type="xsd:integer" />  
             <xsd:attribute name="CustomerID" type="xsd:string" />  
          </xsd:complexType>  
        </xsd:element>  
     </xsd:sequence>  
        <xsd:attribute name="SalesPersonID"   type="xsd:integer" />   
        <xsd:attribute name="LastName"   type="xsd:string" />   
    </xsd:complexType>  
  
</xsd:schema>  
```  
  
 <span data-ttu-id="212d2-229">スキーマで **\<Emp1>** は、要素と要素の両方 **\<Emp2>** が型 `EmpType` です。</span><span class="sxs-lookup"><span data-stu-id="212d2-229">In the schema, both the **\<Emp1>** element and **\<Emp2>** element are of type `EmpType`.</span></span> <span data-ttu-id="212d2-230">この型は、 `EmpType` **\<Order>** 子要素とそれに対応するを表し **\<sql:relationship>** ます。</span><span class="sxs-lookup"><span data-stu-id="212d2-230">The type `EmpType` describes an **\<Order>** child element and the corresponding **\<sql:relationship>**.</span></span> <span data-ttu-id="212d2-231">この場合、 **\<sql:relationship>** **親**属性を使用してで特定できる1つの親がありません。</span><span class="sxs-lookup"><span data-stu-id="212d2-231">In this case, there is no single parent that can be identified in **\<sql:relationship>** by using the **parent** attribute.</span></span> <span data-ttu-id="212d2-232">この場合、で**親**属性を指定する必要はありません **\<sql:relationship>** 。**親**属性情報は、スキーマ内の階層から取得されます。</span><span class="sxs-lookup"><span data-stu-id="212d2-232">In this situation, you don't specify the **parent** attribute in **\<sql:relationship>**; the **parent** attribute information is obtained from the hierarchy in the schema.</span></span>  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a><span data-ttu-id="212d2-233">スキーマに対してサンプル XPath クエリをテストするには</span><span class="sxs-lookup"><span data-stu-id="212d2-233">To test a sample XPath query against the schema</span></span>  
  
1.  <span data-ttu-id="212d2-234">AdventureWorks データベース内に次のテーブルを作成します。</span><span class="sxs-lookup"><span data-stu-id="212d2-234">Create these tables in the AdventureWorks database:</span></span>  
  
    ```  
    USE AdventureWorks  
    CREATE TABLE Sales.Emp1 (  
           SalesPersonID int primary key,   
           FirstName  varchar(20),   
           LastName   varchar(20),   
           ReportsTo int)  
    Go  
    CREATE TABLE Sales.Emp2 (  
           SalesPersonID int primary key,   
           FirstName  varchar(20),   
           LastName   varchar(20),   
           ReportsTo int)  
    Go  
    ```  
  
2.  <span data-ttu-id="212d2-235">テーブルに次のサンプル データを追加します。</span><span class="sxs-lookup"><span data-stu-id="212d2-235">Add this sample data in the tables:</span></span>  
  
    ```  
    INSERT INTO Sales.Emp1 values (279, 'Nancy', 'Devolio',NULL)  
    INSERT INTO Sales.Emp1 values (282, 'Andrew', 'Fuller',1)  
    INSERT INTO Sales.Emp1 values (276, 'Janet', 'Leverling',1)  
    INSERT INTO Sales.Emp2 values (277, 'Margaret', 'Peacock',3)  
    INSERT INTO Sales.Emp2 values (283, 'Steven', 'Devolio',4)  
    INSERT INTO Sales.Emp2 values (275, 'Nancy', 'Buchanan',5)  
    INSERT INTO Sales.Emp2 values (281, 'Michael', 'Suyama',6)  
    ```  
  
3.  <span data-ttu-id="212d2-236">上のスキーマのコードをコピーして、テキスト ファイルに貼り付け、</span><span class="sxs-lookup"><span data-stu-id="212d2-236">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="212d2-237">relationship-noparent.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="212d2-237">Save the file as relationship-noparent.xml.</span></span>  
  
4.  <span data-ttu-id="212d2-238">次のテンプレートをコピーして、テキスト ファイルに貼り付け、</span><span class="sxs-lookup"><span data-stu-id="212d2-238">Copy the following template and paste it into a text file.</span></span> <span data-ttu-id="212d2-239">relationship-noparent.xml を保存したディレクトリに relationship-noparentT.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="212d2-239">Save the file as relationship-noparentT.xml in the same directory where you saved relationship-noparent.xml.</span></span> <span data-ttu-id="212d2-240">テンプレート内のクエリでは、すべての要素が選択 \<Emp1> されます (したがって、親は Emp1 です)。</span><span class="sxs-lookup"><span data-stu-id="212d2-240">The query in the template selects all the \<Emp1> elements (therefore, the parent is Emp1).</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="relationship-noparent.xml">  
            /Emp1  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="212d2-241">マッピング スキーマ (relationship-noparent.xml) に指定するディレクトリ パスは、テンプレートを保存するディレクトリに対する相対パスです。</span><span class="sxs-lookup"><span data-stu-id="212d2-241">The directory path specified for the mapping schema (relationship-noparent.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="212d2-242">次のように、絶対パスを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="212d2-242">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\relationship-noparent.xml"  
    ```  
  
5.  <span data-ttu-id="212d2-243">SQLXML 4.0 テスト スクリプト (sqlxml4test.vbs) を作成し、それを使用してテンプレートを実行します。</span><span class="sxs-lookup"><span data-stu-id="212d2-243">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="212d2-244">詳細については、「ADO を使用した[SQLXML クエリの実行](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="212d2-244">For more information, see [Using ADO to Execute SQLXML Queries](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="212d2-245">結果セットの一部を次に示します。</span><span class="sxs-lookup"><span data-stu-id="212d2-245">Here is a partial result set:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
<Emp1 SalesPersonID="276" LastName="Leverling">  
  <Order SalesOrderID="43663" CustomerID="510" />   
  <Order SalesOrderID="43666" CustomerID="511" />   
  <Order SalesOrderID="43859" CustomerID="259" />  
  ...  
</Emp1>  
```  
  
  
