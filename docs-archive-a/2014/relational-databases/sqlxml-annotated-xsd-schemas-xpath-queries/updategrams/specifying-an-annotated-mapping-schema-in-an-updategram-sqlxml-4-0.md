---
title: アップデートグラムでの注釈付きマッピングスキーマの指定 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- annotated XSD schemas, updategrams
- data types [SQLXML], mapping schema in updategrams
- updategrams [SQLXML], annotated mapping schemas
- annotated XDR schemas, updategrams
- inverse attribute
- parent-child relationships [SQLXML]
- mapping-schema attribute
- mapping schema [SQLXML], updategrams
- sql:inverse
ms.assetid: 2e266ed9-4cfb-434a-af55-d0839f64bb9a
author: rothja
ms.author: jroth
ms.openlocfilehash: a181b3081b51cca160709703364c248e495e0214
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642701"
---
# <a name="specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-40"></a><span data-ttu-id="5b79e-102">アップデートグラムでの注釈付きマッピング スキーマの指定 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="5b79e-102">Specifying an Annotated Mapping Schema in an Updategram (SQLXML 4.0)</span></span>
  <span data-ttu-id="5b79e-103">ここでは、アップデートグラムで指定したマッピング スキーマ (XSD または XDR) が、更新の処理にどのように使用されるかについて説明します。</span><span class="sxs-lookup"><span data-stu-id="5b79e-103">This topic explains how the mapping schema (XSD or XDR) that is specified in an updategram is used to process the updates.</span></span> <span data-ttu-id="5b79e-104">アップデートグラムでは、アップデートグラムの要素と属性をのテーブルと列にマップするときに使用する、注釈付きマッピングスキーマの名前を指定でき [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="5b79e-104">In an updategram, you can provide the name of an annotated mapping schema to use in mapping the elements and attributes in the updategram to tables and columns in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="5b79e-105">アップデートグラムでマッピング スキーマを指定する場合、アップデートグラムで指定する要素と属性名は、マッピング スキーマ内の要素と属性にマップされる必要があります。</span><span class="sxs-lookup"><span data-stu-id="5b79e-105">When a mapping schema is specified in an updategram, the element and attribute names that are specified in the updategram must map to the elements and attributes in the mapping schema.</span></span>  
  
 <span data-ttu-id="5b79e-106">マッピングスキーマを指定するには、 `mapping-schema` 要素の属性を使用し **\<sync>** ます。</span><span class="sxs-lookup"><span data-stu-id="5b79e-106">To specify a mapping schema, you use the `mapping-schema` attribute of the **\<sync>** element.</span></span> <span data-ttu-id="5b79e-107">次の例では、単純なマッピング スキーマを使用するアップデートグラムと、より複雑なスキーマを使用するアップデートグラムの 2 つのアップデートグラムを示します。</span><span class="sxs-lookup"><span data-stu-id="5b79e-107">The following examples show two updategrams: one that uses a simple mapping schema, and one that uses a more complex schema.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5b79e-108">このドキュメントは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] でサポートされるテンプレートとマッピング スキーマについて理解していることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="5b79e-108">This documentation assumes that you are familiar with templates and mapping schema support in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="5b79e-109">詳細については、「[注釈付き XSD スキーマの概要 &#40;SQLXML 4.0&#41;](../../sqlxml/annotated-xsd-schemas/introduction-to-annotated-xsd-schemas-sqlxml-4-0.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5b79e-109">For more information, see [Introduction to Annotated XSD Schemas &#40;SQLXML 4.0&#41;](../../sqlxml/annotated-xsd-schemas/introduction-to-annotated-xsd-schemas-sqlxml-4-0.md).</span></span> <span data-ttu-id="5b79e-110">XDR を使用するレガシアプリケーションでは、 [SQLXML 4.0&#41;では、注釈付き Xdr スキーマ &#40;非推奨](../../sqlxml/annotated-xsd-schemas/annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md)とされています。</span><span class="sxs-lookup"><span data-stu-id="5b79e-110">For legacy applications that use XDR, see [Annotated XDR Schemas &#40;Deprecated in SQLXML 4.0&#41;](../../sqlxml/annotated-xsd-schemas/annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md).</span></span>  
  
## <a name="dealing-with-data-types"></a><span data-ttu-id="5b79e-111">データ型の扱い</span><span class="sxs-lookup"><span data-stu-id="5b79e-111">Dealing with Data Types</span></span>  
 <span data-ttu-id="5b79e-112">スキーマで、、、 `image` `binary` またはのいずれかのデータ型を指定し、 `varbinary` [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] xml データ型を指定しない場合 `sql:datatype` 、アップデートグラムでは xml データ型がであると想定され `binary base 64` ます。</span><span class="sxs-lookup"><span data-stu-id="5b79e-112">If the schema specifies the `image`, `binary`, or `varbinary`[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] data type (by using `sql:datatype`) and does not specify an XML data type, the updategram assumes that the XML data type is `binary base 64`.</span></span> <span data-ttu-id="5b79e-113">データが `bin.base` 型の場合は、明示的に型 (`dt:type=bin.base` または `type="xsd:hexBinary"`) を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5b79e-113">If your data is `bin.base` type, you must explicitly specify the type (`dt:type=bin.base` or `type="xsd:hexBinary"`).</span></span>  
  
 <span data-ttu-id="5b79e-114">`dateTime`、`date`、または `time` の XSD データ型を指定する場合は、`sql:datatype="dateTime"` を使用して、対応する [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データ型も指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5b79e-114">If the schema specifies the `dateTime`, `date`, or `time` XSD data type, you must also specify the corresponding [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] data type by using `sql:datatype="dateTime"`.</span></span>  
  
 <span data-ttu-id="5b79e-115">型のパラメーターを処理する場合は [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] `money` 、 `sql:datatype="money"` マッピングスキーマの適切なノードに明示的にを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5b79e-115">When handling parameters of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] `money` type, you must explicitly specify `sql:datatype="money"` on the appropriate node in the mapping schema.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="5b79e-116">例</span><span class="sxs-lookup"><span data-stu-id="5b79e-116">Examples</span></span>  
 <span data-ttu-id="5b79e-117">次の例を使用して実際のサンプルを作成するには、 [SQLXML の例を実行するための要件](../../sqlxml/requirements-for-running-sqlxml-examples.md)を満たす必要があります。</span><span class="sxs-lookup"><span data-stu-id="5b79e-117">To create working samples using the following examples, you must meet the requirements specified in [Requirements for Running SQLXML Examples](../../sqlxml/requirements-for-running-sqlxml-examples.md).</span></span>  
  
### <a name="a-creating-an-updategram-with-a-simple-mapping-schema"></a><span data-ttu-id="5b79e-118">A.</span><span class="sxs-lookup"><span data-stu-id="5b79e-118">A.</span></span> <span data-ttu-id="5b79e-119">単純なマッピング スキーマを使用するアップデートグラムを作成する</span><span class="sxs-lookup"><span data-stu-id="5b79e-119">Creating an updategram with a simple mapping schema</span></span>  
 <span data-ttu-id="5b79e-120">次の XSD スキーマ (SampleSchema.xml) は、 **\<Customer>** 要素を Sales. Customer テーブルにマップするマッピングスキーマです。</span><span class="sxs-lookup"><span data-stu-id="5b79e-120">The following XSD schema (SampleSchema.xml) is a mapping schema that maps the **\<Customer>** element to the Sales.Customer table:</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Customer" sql:relation="Sales.Customer" >  
   <xsd:complexType>  
        <xsd:attribute name="CustID"    
                       sql:field="CustomerID"   
                       type="xsd:string" />  
        <xsd:attribute name="RegionID"    
                       sql:field="TerritoryID"    
                       type="xsd:string" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 <span data-ttu-id="5b79e-121">次のアップデートグラムでは、Sales.Customer テーブルにレコードを挿入します。ここでは上のマッピング スキーマに従って、このデータをテーブルに適切にマップします。</span><span class="sxs-lookup"><span data-stu-id="5b79e-121">The following updategram inserts a record into the Sales.Customer table and relies on the previous mapping schema to properly map this data to the table.</span></span> <span data-ttu-id="5b79e-122">アップデートグラムでは、 **\<Customer>** スキーマで定義されているのと同じ要素名が使用されていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="5b79e-122">Notice that the updategram uses the same element name, **\<Customer>**, as defined in the schema.</span></span> <span data-ttu-id="5b79e-123">アップデートグラムで特定のスキーマを指定するときには、これが必須となります。</span><span class="sxs-lookup"><span data-stu-id="5b79e-123">This is mandatory because the updategram specifies a particular schema.</span></span>  
  
##### <a name="to-test-the-updategram"></a><span data-ttu-id="5b79e-124">アップデートグラムをテストするには</span><span class="sxs-lookup"><span data-stu-id="5b79e-124">To test the updategram</span></span>  
  
1.  <span data-ttu-id="5b79e-125">上のスキーマのコードをコピーして、テキスト ファイルに貼り付け、</span><span class="sxs-lookup"><span data-stu-id="5b79e-125">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="5b79e-126">SampleUpdateSchema.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="5b79e-126">Save the file as SampleUpdateSchema.xml.</span></span>  
  
2.  <span data-ttu-id="5b79e-127">下のアップデートグラムのテンプレートをコピーして、テキスト ファイルに貼り付け、</span><span class="sxs-lookup"><span data-stu-id="5b79e-127">Copy the updategram template below and paste it into a text file.</span></span> <span data-ttu-id="5b79e-128">SampleUpdateSchema.xml を保存したディレクトリに SampleUpdategram.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="5b79e-128">Save the file as SampleUpdategram.xml in the same directory where you saved SampleUpdateSchema.xml.</span></span>  
  
    ```  
    <ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
      <updg:sync mapping-schema="SampleUpdateSchema.xml">  
        <updg:before>  
          <Customer CustID="1" RegionID="1"  />  
        </updg:before>  
        <updg:after>  
          <Customer CustID="1" RegionID="2" />  
        </updg:after>  
      </updg:sync>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="5b79e-129">マッピング スキーマ (SampleUpdateSchema.xml) に指定するディレクトリ パスは、テンプレートを保存するディレクトリに対する相対パスです。</span><span class="sxs-lookup"><span data-stu-id="5b79e-129">The directory path specified for the mapping schema (SampleUpdateSchema.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="5b79e-130">次のように、絶対パスを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="5b79e-130">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\SqlXmlTest\SampleUpdateSchema.xml"  
    ```  
  
3.  <span data-ttu-id="5b79e-131">SQLXML 4.0 テスト スクリプト (sqlxml4test.vbs) を作成し、それを使用してテンプレートを実行します。</span><span class="sxs-lookup"><span data-stu-id="5b79e-131">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="5b79e-132">詳細については、「ADO を使用した[SQLXML 4.0 クエリの実行](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5b79e-132">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="5b79e-133">これは、これと同等の XDR スキーマです。</span><span class="sxs-lookup"><span data-stu-id="5b79e-133">This is the equivalent XDR schema:</span></span>  
  
```  
<?xml version="1.0" ?>  
   <Schema xmlns="urn:schemas-microsoft-com:xml-data"   
         xmlns:dt="urn:schemas-microsoft-com:datatypes"   
         xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
     <ElementType name="Customer" sql:relation="Sales.Customer" >  
       <AttributeType name="CustID" />  
       <AttributeType name="RegionID" />  
  
       <attribute type="CustID" sql:field="CustomerID" />  
       <attribute type="RegionID" sql:field="TerritoryID" />  
     </ElementType>  
   </Schema>   
```  
  
### <a name="b-inserting-a-record-by-using-the-parent-child-relationship-specified-in-the-mapping-schema"></a><span data-ttu-id="5b79e-134">B.</span><span class="sxs-lookup"><span data-stu-id="5b79e-134">B.</span></span> <span data-ttu-id="5b79e-135">マッピング スキーマに指定されている親子リレーションシップを使用して、レコードを挿入する</span><span class="sxs-lookup"><span data-stu-id="5b79e-135">Inserting a record by using the parent-child relationship specified in the mapping schema</span></span>  
 <span data-ttu-id="5b79e-136">スキーマ要素は関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="5b79e-136">Schema elements can be related.</span></span> <span data-ttu-id="5b79e-137">要素は、 **\<sql:relationship>** スキーマ要素間の親子リレーションシップを指定します。</span><span class="sxs-lookup"><span data-stu-id="5b79e-137">The **\<sql:relationship>** element specifies the parent-child relationship between the schema elements.</span></span> <span data-ttu-id="5b79e-138">この情報は、主キー/外部キーのリレーションシップがある対応するテーブルを更新するときに使用されます。</span><span class="sxs-lookup"><span data-stu-id="5b79e-138">This information is used to update corresponding tables that have primary-key/foreign-key relationship.</span></span>  
  
 <span data-ttu-id="5b79e-139">次のマッピングスキーマ (SampleSchema.xml) は、との2つの要素で構成されてい **\<Order>** **\<OD>** ます。</span><span class="sxs-lookup"><span data-stu-id="5b79e-139">The following mapping schema (SampleSchema.xml) consists of two elements, **\<Order>** and **\<OD>**:</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="OrderOD"  
          parent="Sales.SalesOrderHeader"  
          parent-key="SalesOrderID"  
          child="Sales.SalesOrderDetail"  
          child-key="SalesOrderID" />  
  </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="Order" sql:relation="Sales.SalesOrderHeader" >  
   <xsd:complexType>  
     <xsd:sequence>  
        <xsd:element name="OD"   
                     sql:relation="Sales.SalesOrderDetail"  
                     sql:relationship="OrderOD" >  
           <xsd:complexType>  
              <xsd:attribute name="SalesOrderID"   type="xsd:integer" />  
              <xsd:attribute name="ProductID" type="xsd:integer" />  
             <xsd:attribute name="UnitPrice"  type="xsd:decimal" />  
             <xsd:attribute name="OrderQty"   type="xsd:integer" />  
             <xsd:attribute name="UnitPriceDiscount"   type="xsd:decimal" />  
  
           </xsd:complexType>  
        </xsd:element>  
     </xsd:sequence>  
        <xsd:attribute name="CustomerID"   type="xsd:string" />   
        <xsd:attribute name="SalesOrderID"  type="xsd:integer" />  
        <xsd:attribute name="OrderDate"  type="xsd:date" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 <span data-ttu-id="5b79e-140">次のアップデートグラムでは、この XSD スキーマを使用して、注文43860の新しい注文明細レコード ( **\<OD>** ブロック内の要素) を追加し **\<after>** ます。</span><span class="sxs-lookup"><span data-stu-id="5b79e-140">The following updategram uses this XSD schema to add a new order detail record (an **\<OD>** element in the **\<after>** block) for order 43860.</span></span> <span data-ttu-id="5b79e-141">`mapping-schema` 属性は、アップデートグラム内でマッピング スキーマを指定するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="5b79e-141">The `mapping-schema` attribute is used to specify the mapping schema in the updategram.</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync mapping-schema="SampleUpdateSchema.xml" >  
    <updg:before>  
       <Order SalesOrderID="43860" />  
    </updg:before>  
    <updg:after>  
      <Order SalesOrderID="43860" >  
           <OD ProductID="753" UnitPrice="$10.00"  
               Quantity="5" Discount="0.0" />  
      </Order>  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
##### <a name="to-test-the-updategram"></a><span data-ttu-id="5b79e-142">アップデートグラムをテストするには</span><span class="sxs-lookup"><span data-stu-id="5b79e-142">To test the updategram</span></span>  
  
1.  <span data-ttu-id="5b79e-143">上のスキーマのコードをコピーして、テキスト ファイルに貼り付け、</span><span class="sxs-lookup"><span data-stu-id="5b79e-143">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="5b79e-144">SampleUpdateSchema.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="5b79e-144">Save the file as SampleUpdateSchema.xml.</span></span>  
  
2.  <span data-ttu-id="5b79e-145">上のアップデートグラムのテンプレートをコピーして、テキスト ファイルに貼り付け、</span><span class="sxs-lookup"><span data-stu-id="5b79e-145">Copy the updategram template above and paste it into a text file.</span></span> <span data-ttu-id="5b79e-146">SampleUpdateSchema.xml を保存したディレクトリに SampleUpdategram.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="5b79e-146">Save the file as SampleUpdategram.xml in the same directory where you saved SampleUpdateSchema.xml.</span></span>  
  
     <span data-ttu-id="5b79e-147">マッピング スキーマ (SampleUpdateSchema.xml) に指定するディレクトリ パスは、テンプレートを保存するディレクトリに対する相対パスです。</span><span class="sxs-lookup"><span data-stu-id="5b79e-147">The directory path specified for the mapping schema (SampleUpdateSchema.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="5b79e-148">次のように、絶対パスを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="5b79e-148">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\SqlXmlTest\SampleUpdateSchema.xml"  
    ```  
  
3.  <span data-ttu-id="5b79e-149">SQLXML 4.0 テスト スクリプト (sqlxml4test.vbs) を作成し、それを使用してテンプレートを実行します。</span><span class="sxs-lookup"><span data-stu-id="5b79e-149">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="5b79e-150">詳細については、「ADO を使用した[SQLXML 4.0 クエリの実行](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5b79e-150">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="5b79e-151">これは、これと同等の XDR スキーマです。</span><span class="sxs-lookup"><span data-stu-id="5b79e-151">This is the equivalent XDR schema:</span></span>  
  
```  
<?xml version="1.0" ?>  
<Schema xmlns="urn:schemas-microsoft-com:xml-data"  
        xmlns:dt="urn:schemas-microsoft-com:datatypes"  
        xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  
<ElementType name="OD" sql:relation="Sales.SalesOrderDetail" >  
    <AttributeType name="SalesOrderID" />  
    <AttributeType name="ProductID" />  
    <AttributeType name="UnitPrice"  dt:type="fixed.14.4" />  
    <AttributeType name="OrderQty" />  
    <AttributeType name="UnitPriceDiscount" />  
  
    <attribute type="SalesOrderID" />  
    <attribute type="ProductID" />  
    <attribute type="UnitPrice" />  
    <attribute type="OrderQty" />  
    <attribute type="UnitPriceDiscount" />  
</ElementType>  
  
<ElementType name="Order" sql:relation="Sales.SalesOrderHeader" >  
    <AttributeType name="CustomerID" />  
    <AttributeType name="SalesOrderID" />  
    <AttributeType name="OrderDate" />  
  
    <attribute type="CustomerID" />  
    <attribute type="SalesOrderID" />  
    <attribute type="OrderDate" />  
    <element type="OD" >  
             <sql:relationship   
                   key-relation="Sales.SalesOrderHeader"  
                   key="SalesOrderID"  
                   foreign-key="SalesOrderID"  
                   foreign-relation="Sales.SalesOrderDetail" />  
    </element>  
</ElementType>  
</Schema>  
```  
  
### <a name="c-inserting-a-record-by-using-the-parent-child-relationship-and-inverse-annotation-specified-in-the-xsd-schema"></a><span data-ttu-id="5b79e-152">C.</span><span class="sxs-lookup"><span data-stu-id="5b79e-152">C.</span></span> <span data-ttu-id="5b79e-153">XSD スキーマで指定されている親子リレーションシップと inverse 注釈を使用して、レコードを挿入する</span><span class="sxs-lookup"><span data-stu-id="5b79e-153">Inserting a record by using the parent-child relationship and inverse annotation specified in the XSD schema</span></span>  
 <span data-ttu-id="5b79e-154">この例では、XSD で指定される親子リレーションシップがアップデートグラム ロジックでどのように使用され、更新が処理されるかと、`inverse` 注釈がどのように使用されるかを示します。</span><span class="sxs-lookup"><span data-stu-id="5b79e-154">This example illustrates how the updategram logic uses the parent-child relationship specified in the XSD to process updates, and how the `inverse` annotation is used.</span></span> <span data-ttu-id="5b79e-155">注釈の詳細につい `inverse` ては、「 [sql: relationship での sql: 逆属性の指定 &#40;SQLXML 4.0&#41;](../../sqlxml-annotated-xsd-schemas-using/specifying-the-sql-inverse-attribute-on-sql-relationship-sqlxml-4-0.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5b79e-155">For more information about the `inverse` annotation, see [Specifying the sql:inverse Attribute on sql:relationship &#40;SQLXML 4.0&#41;](../../sqlxml-annotated-xsd-schemas-using/specifying-the-sql-inverse-attribute-on-sql-relationship-sqlxml-4-0.md).</span></span>  
  
 <span data-ttu-id="5b79e-156">この例では、次のテーブルが**tempdb**データベースにあることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="5b79e-156">This example assumes that the following tables are in the **tempdb** database:</span></span>  
  
-   <span data-ttu-id="5b79e-157">`Cust (CustomerID, CompanyName)`。ここでは `CustomerID` は主キーです。</span><span class="sxs-lookup"><span data-stu-id="5b79e-157">`Cust (CustomerID, CompanyName)`, where `CustomerID` is the primary key</span></span>  
  
-   <span data-ttu-id="5b79e-158">`Ord (OrderID, CustomerID)`。ここでは `CustomerID` は外部キーで、`CustomerID` テーブル内の `Cust` 主キーを参照します。</span><span class="sxs-lookup"><span data-stu-id="5b79e-158">`Ord (OrderID, CustomerID)`, where `CustomerID` is a foreign key that refers to the `CustomerID` primary key in the `Cust` table.</span></span>  
  
 <span data-ttu-id="5b79e-159">このアップデートグラムでは次の XSD スキーマを使用して、Cust および Ord テーブルにレコードを挿入します。</span><span class="sxs-lookup"><span data-stu-id="5b79e-159">The updategram uses the following XSD schema to insert records into the Cust and Ord tables :</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
       <sql:relationship name="OrdCust" inverse="true"  
                  parent="Ord"  
                  parent-key="CustomerID"  
                  child-key="CustomerID"  
                  child="Cust"/>  
  </xsd:appinfo>  
</xsd:annotation>  
  
<xsd:element name="Order" sql:relation="Ord">  
  <xsd:complexType>  
    <xsd:sequence>  
      <xsd:element ref="Customer" sql:relationship="OrdCust"/>  
    </xsd:sequence>  
    <xsd:attribute name="OrderID"   type="xsd:int"/>  
    <xsd:attribute name="CustomerID" type="xsd:string"/>  
  </xsd:complexType>  
</xsd:element>  
  
<xsd:element name="Customer" sql:relation="Cust">  
  <xsd:complexType>  
     <xsd:attribute name="CustomerID"  type="xsd:string"/>  
    <xsd:attribute name="CompanyName" type="xsd:string"/>  
  </xsd:complexType>  
</xsd:element>  
  
</xsd:schema>  
```  
  
 <span data-ttu-id="5b79e-160">この例の XSD スキーマには、 **\<Customer>** 要素と要素があり、 **\<Order>** 2 つの要素間の親子リレーションシップを指定します。</span><span class="sxs-lookup"><span data-stu-id="5b79e-160">The XSD schema in this example has **\<Customer>** and **\<Order>** elements, and it specifies a parent-child relationship between the two elements.</span></span> <span data-ttu-id="5b79e-161">**\<Order>** 親要素として、および子要素としてを識別し **\<Customer>** ます。</span><span class="sxs-lookup"><span data-stu-id="5b79e-161">It identifies **\<Order>** as the parent element and **\<Customer>** as the child element.</span></span>  
  
 <span data-ttu-id="5b79e-162">アップデートグラム処理ロジックでは、親子リレーションシップに関する情報に基づいて、レコードがテーブルに挿入される順序が決定されます。</span><span class="sxs-lookup"><span data-stu-id="5b79e-162">The updategram processing logic uses the information about the parent-child relationship to determine the order in which records are inserted into tables.</span></span> <span data-ttu-id="5b79e-163">この例では、アップデートグラムロジックはまず、Ord テーブルにレコードを挿入しようとし (は親であるため **\<Order>** )、Cust テーブルにレコードを挿入しようとします (は子であるため) **\<Customer>** 。</span><span class="sxs-lookup"><span data-stu-id="5b79e-163">In this example, the updategram logic first attempts to insert a record into the Ord table (because **\<Order>** is the parent) and then attempts to insert a record into the Cust table (because **\<Customer>** is the child).</span></span> <span data-ttu-id="5b79e-164">しかし、データベース テーブル スキーマに含まれる主キー/外部キーの情報に対して、この挿入操作はデータベースの外部キー違反となるため、挿入は失敗します。</span><span class="sxs-lookup"><span data-stu-id="5b79e-164">However, because of the primary key/foreign key information that is contained in the database table schema, this insert operation causes a foreign key violation in the database and the insert fails.</span></span>  
  
 <span data-ttu-id="5b79e-165">アップデートグラムロジックに対して、更新操作中に親子関係を反転するように指示するに `inverse` は、要素に注釈を指定し **\<relationship>** ます。</span><span class="sxs-lookup"><span data-stu-id="5b79e-165">To instruct the updategram logic to reverse the parent-child relationship during the update operation, the `inverse` annotation is specified on the **\<relationship>** element.</span></span> <span data-ttu-id="5b79e-166">こうすると、最初に Cust テーブル、次に Ord テーブルにレコードが追加され、操作は成功します。</span><span class="sxs-lookup"><span data-stu-id="5b79e-166">As a result, records are added first in the Cust table and then in the Ord table, and the operation succeeds.</span></span>  
  
 <span data-ttu-id="5b79e-167">次のアップデートグラムでは、指定された XSD スキーマを使用して、Ord テーブルに注文 (OrderID=2)、Cust テーブルに顧客 (CustomerID='AAAAA') を挿入します。</span><span class="sxs-lookup"><span data-stu-id="5b79e-167">The following updategram inserts an order (OrderID=2) in the Ord table and a customer (CustomerID='AAAAA') in the Cust table by using the specified XSD schema:</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync mapping-schema="SampleUpdateSchema.xml" >  
    <updg:before/>  
    <updg:after>  
      <Order OrderID="2" CustomerID="AAAAA" >  
        <Customer CustomerID="AAAAA" CompanyName="AAAAA Company" />  
      </Order>  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
##### <a name="to-test-the-updategram"></a><span data-ttu-id="5b79e-168">アップデートグラムをテストするには</span><span class="sxs-lookup"><span data-stu-id="5b79e-168">To test the updategram</span></span>  
  
1.  <span data-ttu-id="5b79e-169">次のテーブルを**tempdb**データベースに作成します。</span><span class="sxs-lookup"><span data-stu-id="5b79e-169">Create these tables in the **tempdb** database:</span></span>  
  
    ```  
    USE tempdb  
    CREATE TABLE Cust(CustomerID varchar(5) primary key,   
                      CompanyName varchar(20))  
    GO  
    CREATE TABLE Ord (OrderID int primary key,   
                      CustomerID varchar(5) references Cust(CustomerID))  
    GO  
    ```  
  
2.  <span data-ttu-id="5b79e-170">上のスキーマのコードをコピーして、テキスト ファイルに貼り付け、</span><span class="sxs-lookup"><span data-stu-id="5b79e-170">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="5b79e-171">SampleUpdateSchema.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="5b79e-171">Save the file as SampleUpdateSchema.xml.</span></span>  
  
3.  <span data-ttu-id="5b79e-172">上のアップデートグラムのテンプレートをコピーして、テキスト ファイルに貼り付け、</span><span class="sxs-lookup"><span data-stu-id="5b79e-172">Copy the updategram template above and paste it into a text file.</span></span> <span data-ttu-id="5b79e-173">SampleUpdateSchema.xml を保存したディレクトリに SampleUpdategram.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="5b79e-173">Save the file as SampleUpdategram.xml in the same directory where you saved SampleUpdateSchema.xml.</span></span>  
  
     <span data-ttu-id="5b79e-174">マッピング スキーマ (SampleUpdateSchema.xml) に指定するディレクトリ パスは、テンプレートを保存するディレクトリに対する相対パスです。</span><span class="sxs-lookup"><span data-stu-id="5b79e-174">The directory path specified for the mapping schema (SampleUpdateSchema.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="5b79e-175">次のように、絶対パスを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="5b79e-175">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\SqlXmlTest\SampleUpdateSchema.xml"  
    ```  
  
4.  <span data-ttu-id="5b79e-176">SQLXML 4.0 テスト スクリプト (sqlxml4test.vbs) を作成し、それを使用してテンプレートを実行します。</span><span class="sxs-lookup"><span data-stu-id="5b79e-176">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="5b79e-177">詳細については、「ADO を使用した[SQLXML 4.0 クエリの実行](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5b79e-177">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b79e-178">参照</span><span class="sxs-lookup"><span data-stu-id="5b79e-178">See Also</span></span>  
 [<span data-ttu-id="5b79e-179">SQLXML 4.0&#41;&#40;アップデートグラムのセキュリティに関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="5b79e-179">Updategram Security Considerations &#40;SQLXML 4.0&#41;</span></span>](../security/updategram-security-considerations-sqlxml-4-0.md)  
  
  
