---
title: 'データ型の強制変換と sql: datatype 注釈 (SQLXML 4.0) |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- mapping data types [SQLXML]
- type attribute
- sql:datatype
- data types [SQLXML], converting
- annotated XSD schemas, mapping data types
- xsd:type
- datatype annotation
- converting data types [SQLXML]
- data types [SQLXML], mapping data types
- XSD schemas [SQLXML], mapping data types
ms.assetid: db192105-e8aa-4392-b812-9d727918c005
author: rothja
ms.author: jroth
ms.openlocfilehash: 22f1b0af93e3b596d74bc107ab6947b9855a2cf6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640866"
---
# <a name="data-type-coercions-and-the-sqldatatype-annotation-sqlxml-40"></a><span data-ttu-id="ae15e-102">データ型の強制型変換と sql:datatype 注釈 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="ae15e-102">Data Type Coercions and the sql:datatype Annotation (SQLXML 4.0)</span></span>
  <span data-ttu-id="ae15e-103">XSD スキーマでは、`xsd:type` 属性を使用して、要素または属性の XSD データ型を指定できます。</span><span class="sxs-lookup"><span data-stu-id="ae15e-103">In an XSD schema, the `xsd:type` attribute specifies the XSD data type of an element or attribute.</span></span> <span data-ttu-id="ae15e-104">XSD スキーマを使用したデータベースからのデータの抽出では、指定されているデータ型を使用して、データが書式設定されます。</span><span class="sxs-lookup"><span data-stu-id="ae15e-104">When an XSD schema is used to extract data from the database, the data type specified is used to format the data.</span></span>  
  
 <span data-ttu-id="ae15e-105">スキーマでは、XSD 型を指定する他に、`sql:datatype` 注釈を使用して、Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型を指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="ae15e-105">In addition to specifying an XSD type in a schema, you can also specify a Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type by using the `sql:datatype` annotation.</span></span> <span data-ttu-id="ae15e-106">これらの `xsd:type` および `sql:datatype` 属性では、XSD データ型と [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型の間のマッピングが制御されます。</span><span class="sxs-lookup"><span data-stu-id="ae15e-106">The `xsd:type` and `sql:datatype` attributes control the mapping between XSD data types and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types.</span></span>  
  
## <a name="xsdtype-attribute"></a><span data-ttu-id="ae15e-107">xsd:type 属性</span><span class="sxs-lookup"><span data-stu-id="ae15e-107">xsd:type Attribute</span></span>  
 <span data-ttu-id="ae15e-108">`xsd:type` 属性を使用すると、列にマップする属性や要素の XML データ型を指定できます。</span><span class="sxs-lookup"><span data-stu-id="ae15e-108">You can use the `xsd:type` attribute to specify the XML data type of an attribute or element that maps to a column.</span></span> <span data-ttu-id="ae15e-109">`xsd:type` はサーバーから返されるドキュメントだけでなく、実行される XPath クエリにも影響します。</span><span class="sxs-lookup"><span data-stu-id="ae15e-109">The `xsd:type` affects the document that is returned from the server and also the XPath query that is executed.</span></span> <span data-ttu-id="ae15e-110">`xsd:type` を含むマッピング スキーマに対して XPath クエリを実行すると、XPath でクエリが処理されるときに、指定されたデータ型が使用されます。</span><span class="sxs-lookup"><span data-stu-id="ae15e-110">When an XPath query is executed against a mapping schema that contains `xsd:type`, XPath uses the specified data type when it processes the query.</span></span> <span data-ttu-id="ae15e-111">XPath の使用方法の詳細については `xsd:type` 、「 [&#41;の Xpath データ型への XSD データ型のマッピング &#40;SQLXML 4.0 ](../sqlxml-annotated-xsd-schemas-xpath-queries/xpath-data-types-sqlxml-4-0.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ae15e-111">For more information about how XPath uses `xsd:type`, see [Mapping XSD Data Types to XPath Data Types &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-xpath-queries/xpath-data-types-sqlxml-4-0.md).</span></span>  
  
 <span data-ttu-id="ae15e-112">返されるドキュメントでは、すべての [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型は文字列表記に変換されます。</span><span class="sxs-lookup"><span data-stu-id="ae15e-112">In a returned document, all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types are converted into string representations.</span></span> <span data-ttu-id="ae15e-113">また、データ型によっては追加の変換が必要です。</span><span class="sxs-lookup"><span data-stu-id="ae15e-113">Some data types require additional conversions.</span></span> <span data-ttu-id="ae15e-114">次の表は、さまざまな `xsd:type` 値とそれに対して使用される変換の一覧です。</span><span class="sxs-lookup"><span data-stu-id="ae15e-114">The following table lists the conversions that are used for various `xsd:type` values.</span></span>  
  
|<span data-ttu-id="ae15e-115">XSD データ型</span><span class="sxs-lookup"><span data-stu-id="ae15e-115">XSD data type</span></span>|<span data-ttu-id="ae15e-116">SQL Server の変換</span><span class="sxs-lookup"><span data-stu-id="ae15e-116">SQL Server conversion</span></span>|  
|-------------------|---------------------------|  
|<span data-ttu-id="ae15e-117">Boolean</span><span class="sxs-lookup"><span data-stu-id="ae15e-117">Boolean</span></span>|<span data-ttu-id="ae15e-118">CONVERT(bit, COLUMN)</span><span class="sxs-lookup"><span data-stu-id="ae15e-118">CONVERT(bit, COLUMN)</span></span>|  
|<span data-ttu-id="ae15e-119">Date</span><span class="sxs-lookup"><span data-stu-id="ae15e-119">Date</span></span>|<span data-ttu-id="ae15e-120">LEFT(CONVERT(nvarchar(4000), COLUMN, 126), 10)</span><span class="sxs-lookup"><span data-stu-id="ae15e-120">LEFT(CONVERT(nvarchar(4000), COLUMN, 126), 10)</span></span>|  
|<span data-ttu-id="ae15e-121">decimal</span><span class="sxs-lookup"><span data-stu-id="ae15e-121">decimal</span></span>|<span data-ttu-id="ae15e-122">CONVERT(money, COLUMN)</span><span class="sxs-lookup"><span data-stu-id="ae15e-122">CONVERT(money, COLUMN)</span></span>|  
|<span data-ttu-id="ae15e-123">id/idref/idrefs</span><span class="sxs-lookup"><span data-stu-id="ae15e-123">id/idref/idrefs</span></span>|<span data-ttu-id="ae15e-124">id-prefix + CONVERT(nvarchar(4000), COLUMN, 126)</span><span class="sxs-lookup"><span data-stu-id="ae15e-124">id-prefix + CONVERT(nvarchar(4000), COLUMN, 126)</span></span>|  
|<span data-ttu-id="ae15e-125">nmtoken/nmtokens</span><span class="sxs-lookup"><span data-stu-id="ae15e-125">nmtoken/nmtokens</span></span>|<span data-ttu-id="ae15e-126">id-prefix + CONVERT(nvarchar(4000), COLUMN, 126)</span><span class="sxs-lookup"><span data-stu-id="ae15e-126">id-prefix + CONVERT(nvarchar(4000), COLUMN, 126)</span></span>|  
|<span data-ttu-id="ae15e-127">Time</span><span class="sxs-lookup"><span data-stu-id="ae15e-127">Time</span></span>|<span data-ttu-id="ae15e-128">SUBSTRING(CONVERT(nvarchar(4000), COLUMN, 126), 1+CHARINDEX(N'T', CONVERT(nvarchar(4000), COLUMN, 126)), 24)</span><span class="sxs-lookup"><span data-stu-id="ae15e-128">SUBSTRING(CONVERT(nvarchar(4000), COLUMN, 126), 1+CHARINDEX(N'T', CONVERT(nvarchar(4000), COLUMN, 126)), 24)</span></span>|  
|<span data-ttu-id="ae15e-129">その他すべて</span><span class="sxs-lookup"><span data-stu-id="ae15e-129">All others</span></span>|<span data-ttu-id="ae15e-130">追加の変換はありません。</span><span class="sxs-lookup"><span data-stu-id="ae15e-130">No additional conversion</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="ae15e-131">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] から、`xsd:type` で指定される XML データ型と互換性のない値が返される場合もあります。たとえば、"XYZ" は `decimal` データ型に変換できない値であり、-100,000 は `UnsignedShort` XSD 型に変換するとデータ型の範囲を超える値となるためです。</span><span class="sxs-lookup"><span data-stu-id="ae15e-131">Some of the values returned by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] might not be compatible with the XML data types that are specified by using `xsd:type`, either because the conversion is not possible (for example, converting "XYZ" to a `decimal` data type) or because the value exceeds the range of that data type (for example, -100000 converted to an `UnsignedShort` XSD type).</span></span> <span data-ttu-id="ae15e-132">互換性のない型を変換しようとすると、無効な XML ドキュメントが生成されるか、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラーになる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ae15e-132">Incompatible type conversions might result in XML documents that are not valid, or in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] errors.</span></span>  
  
## <a name="mapping-from-sql-server-data-types-to-xsd-data-types"></a><span data-ttu-id="ae15e-133">SQL Server データ型から XSD データ型へのマッピング</span><span class="sxs-lookup"><span data-stu-id="ae15e-133">Mapping from SQL Server Data Types to XSD Data Types</span></span>  
 <span data-ttu-id="ae15e-134">次の表は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型から XSD データ型への明確なマッピングです。</span><span class="sxs-lookup"><span data-stu-id="ae15e-134">The following table shows an obvious mapping from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types to XSD data types.</span></span> <span data-ttu-id="ae15e-135">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 型がわかっている場合は、XSD スキーマで指定できる、対応する XSD 型をこの表で確認してください。</span><span class="sxs-lookup"><span data-stu-id="ae15e-135">If you know the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] type, this table provides the corresponding XSD type that you can specify in the XSD schema.</span></span>  
  
|<span data-ttu-id="ae15e-136">SQL Server のデータ型</span><span class="sxs-lookup"><span data-stu-id="ae15e-136">SQL Server data type</span></span>|<span data-ttu-id="ae15e-137">XSD データ型</span><span class="sxs-lookup"><span data-stu-id="ae15e-137">XSD data type</span></span>|  
|--------------------------|-------------------|  
|`bigint`|`long`|  
|`binary`|`base64Binary`|  
|`bit`|`boolean`|  
|`char`|`string`|  
|`datetime`|`dateTime`|  
|`decimal`|`decimal`|  
|`float`|`double`|  
|`image`|`base64Binary`|  
|`int`|`int`|  
|`money`|`decimal`|  
|`nchar`|`string`|  
|`ntext`|`string`|  
|`nvarchar`|`string`|  
|`numeric`|`decimal`|  
|`real`|`float`|  
|`smalldatetime`|`dateTime`|  
|`smallint`|`short`|  
|`smallmoney`|`decimal`|  
|`sql_variant`|`string`|  
|`sysname`|`string`|  
|`text`|`string`|  
|`timestamp`|`dateTime`|  
|`tinyint`|`unsignedByte`|  
|`varbinary`|`base64Binary`|  
|`varchar`|`string`|  
|`uniqueidentifier`|`string`|  
  
## <a name="sqldatatype-annotation"></a><span data-ttu-id="ae15e-138">sql:datatype 注釈</span><span class="sxs-lookup"><span data-stu-id="ae15e-138">sql:datatype Annotation</span></span>  
 <span data-ttu-id="ae15e-139">`sql:datatype` 注釈を使用すると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型を指定できます。この注釈は、次の場合に指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ae15e-139">The `sql:datatype` annotation is used to specify the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type; this annotation must be specified when:</span></span>  
  
-   <span data-ttu-id="ae15e-140">`dateTime` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] XSD `dateTime` 、 `date` 、または型の列 `time` に一括読み込みを行う場合。</span><span class="sxs-lookup"><span data-stu-id="ae15e-140">You are bulk loading into a `dateTime`[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] column from an XSD `dateTime`, `date`, or `time` type.</span></span> <span data-ttu-id="ae15e-141">この場合、`sql:datatype="dateTime"` を使って [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 列のデータ型を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ae15e-141">In this case, you must identify the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] column data type by using `sql:datatype="dateTime"`.</span></span> <span data-ttu-id="ae15e-142">この規則はアップデートグラムにも当てはまります。</span><span class="sxs-lookup"><span data-stu-id="ae15e-142">This rule also applies to updategrams.</span></span>  
  
-   <span data-ttu-id="ae15e-143">型の列に一括読み込みを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `uniqueidentifier` 行い、XSD 値は、中かっこ ({および}) を含む GUID です。</span><span class="sxs-lookup"><span data-stu-id="ae15e-143">You are bulk loading into a column of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `uniqueidentifier` type and the XSD value is a GUID that includes braces ({ and }).</span></span> <span data-ttu-id="ae15e-144">`sql:datatype="uniqueidentifier"` を指定すると、値が列に挿入される前に中かっこが削除されます。</span><span class="sxs-lookup"><span data-stu-id="ae15e-144">When you specify `sql:datatype="uniqueidentifier"`, the braces are removed from the value before it is inserted in the column.</span></span> <span data-ttu-id="ae15e-145">`sql:datatype` を指定しないと、値が中かっこ付きのまま送信され、挿入または更新は失敗します。</span><span class="sxs-lookup"><span data-stu-id="ae15e-145">If `sql:datatype` is not specified, the value is sent with the braces, and the insert or update fails.</span></span>  
  
-   <span data-ttu-id="ae15e-146">XML データ型 `base64Binary` は、さまざまな [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型 (`binary`、`image`、または `varbinary`) にマップされます。</span><span class="sxs-lookup"><span data-stu-id="ae15e-146">The XML data type `base64Binary` maps to various [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types (`binary`, `image`, or `varbinary`).</span></span> <span data-ttu-id="ae15e-147">XML データ型 `base64Binary` を特定の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型にマップするには、`sql:datatype` 注釈を使用します。</span><span class="sxs-lookup"><span data-stu-id="ae15e-147">To map the XML data type `base64Binary` to a specific [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type, use the `sql:datatype` annotation.</span></span> <span data-ttu-id="ae15e-148">この注釈では、属性のマップ先列の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型を明示的に指定できます。</span><span class="sxs-lookup"><span data-stu-id="ae15e-148">This annotation specifies the explicit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type of the column to which the attribute maps.</span></span> <span data-ttu-id="ae15e-149">これは、データをデータベースに格納する場合に便利で、</span><span class="sxs-lookup"><span data-stu-id="ae15e-149">This is useful when data is being stored in the databases.</span></span> <span data-ttu-id="ae15e-150">`sql:datatype` 注釈を指定することにより、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型を明示的に識別できます。</span><span class="sxs-lookup"><span data-stu-id="ae15e-150">By specifying the `sql:datatype` annotation, you can identify the explicit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type.</span></span>  
  
 <span data-ttu-id="ae15e-151">一般に、スキーマでは `sql:datatype` を指定することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ae15e-151">It is generally recommended that you specify `sql:datatype` in the schema.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="ae15e-152">例</span><span class="sxs-lookup"><span data-stu-id="ae15e-152">Examples</span></span>  
 <span data-ttu-id="ae15e-153">次の例を使用した実際のサンプルを作成するには、特定の条件を満たす必要があります。</span><span class="sxs-lookup"><span data-stu-id="ae15e-153">To create working samples using the following examples, you must meet certain requirements.</span></span> <span data-ttu-id="ae15e-154">詳細については、「 [SQLXML の例を実行するための要件](../sqlxml/requirements-for-running-sqlxml-examples.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ae15e-154">For more information, see [Requirements for Running SQLXML Examples](../sqlxml/requirements-for-running-sqlxml-examples.md).</span></span>  
  
### <a name="a-specifying-xsdtype"></a><span data-ttu-id="ae15e-155">A.</span><span class="sxs-lookup"><span data-stu-id="ae15e-155">A.</span></span> <span data-ttu-id="ae15e-156">xsd:type を指定する</span><span class="sxs-lookup"><span data-stu-id="ae15e-156">Specifying xsd:type</span></span>  
 <span data-ttu-id="ae15e-157">この例では、スキーマ内で `date` 属性を使って指定した XSD `xsd:type` 型が、結果の XML ドキュメントにどのように影響するかを示します。</span><span class="sxs-lookup"><span data-stu-id="ae15e-157">This example shows how an XSD `date` type that is specified by using the `xsd:type` attribute in the schema affects the resulting XML document.</span></span> <span data-ttu-id="ae15e-158">このスキーマでは、AdventureWorks データベース内の Sales.SalesOrderHeader テーブルの XML ビューが提供されます。</span><span class="sxs-lookup"><span data-stu-id="ae15e-158">The schema provides an XML view of the Sales.SalesOrderHeader table in the AdventureWorks database.</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Order" sql:relation="Sales.SalesOrderHeader">  
     <xsd:complexType>  
       <xsd:attribute name="SalesOrderID" type="xsd:string" />   
       <xsd:attribute name="CustomerID"   type="xsd:string" />   
       <xsd:attribute name="OrderDate"    type="xsd:date" />   
       <xsd:attribute name="DueDate"  />   
       <xsd:attribute name="ShipDate"  type="xsd:time" />   
     </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 <span data-ttu-id="ae15e-159">この XSD スキーマには、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] から日付値を返す 3 つの属性が含まれています。</span><span class="sxs-lookup"><span data-stu-id="ae15e-159">In this XSD schema, there are three attributes that return a date value from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="ae15e-160">それぞれの属性は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="ae15e-160">When the schema:</span></span>  
  
-   <span data-ttu-id="ae15e-161">`xsd:type=date` **Orderdate**属性にを指定します。 orderdate 属性に対してによって返される値の日付部分 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が表示されます。 **OrderDate**</span><span class="sxs-lookup"><span data-stu-id="ae15e-161">Specifies `xsd:type=date` on the **OrderDate** attribute, the date part of the value returned by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] for the **OrderDate** attribute is displayed.</span></span>  
  
-   <span data-ttu-id="ae15e-162">`xsd:type=time` **ShipDate**属性でを指定します。 ShipDate 属性に対してによって返される値の時刻部分 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が表示されます。 **ShipDate**</span><span class="sxs-lookup"><span data-stu-id="ae15e-162">Specifies `xsd:type=time` on the **ShipDate** attribute, the time part of the value that is returned by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] for the **ShipDate** attribute is displayed.</span></span>  
  
-   <span data-ttu-id="ae15e-163">では、DueDate 属性にが指定されていません `xsd:type` 。によって返されるのと同じ**DueDate**値 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が表示されます。</span><span class="sxs-lookup"><span data-stu-id="ae15e-163">Does not specify `xsd:type` on the **DueDate** attribute, the same value that is returned by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is displayed.</span></span>  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a><span data-ttu-id="ae15e-164">スキーマに対してサンプル XPath クエリをテストするには</span><span class="sxs-lookup"><span data-stu-id="ae15e-164">To test a sample XPath query against the schema</span></span>  
  
1.  <span data-ttu-id="ae15e-165">上のスキーマのコードをコピーして、テキスト ファイルに貼り付け、</span><span class="sxs-lookup"><span data-stu-id="ae15e-165">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="ae15e-166">xsdType.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="ae15e-166">Save the file as xsdType.xml.</span></span>  
  
2.  <span data-ttu-id="ae15e-167">次のテンプレートをコピーして、テキスト ファイルに貼り付け、</span><span class="sxs-lookup"><span data-stu-id="ae15e-167">Copy the following template and paste it into a text file.</span></span> <span data-ttu-id="ae15e-168">xsdType.xml を保存したディレクトリに xsdTypeT.xml として保存します。</span><span class="sxs-lookup"><span data-stu-id="ae15e-168">Save the file as xsdTypeT.xml in the same directory where you saved xsdType.xml.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="xsdType.xml">  
        /Order  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="ae15e-169">マッピング スキーマ (xsdType.xml) に指定するディレクトリ パスは、テンプレートを保存するディレクトリに対する相対パスです。</span><span class="sxs-lookup"><span data-stu-id="ae15e-169">The directory path specified for the mapping schema (xsdType.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="ae15e-170">次のように、絶対パスを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="ae15e-170">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\SqlXmlTest\xsdType.xml"  
    ```  
  
3.  <span data-ttu-id="ae15e-171">SQLXML 4.0 テスト スクリプト (sqlxml4test.vbs) を作成し、それを使用してテンプレートを実行します。</span><span class="sxs-lookup"><span data-stu-id="ae15e-171">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="ae15e-172">詳細については、「ADO を使用した[SQLXML 4.0 クエリの実行](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ae15e-172">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="ae15e-173">次に結果セットの一部を示します。</span><span class="sxs-lookup"><span data-stu-id="ae15e-173">Here is the partial result set:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Order SalesOrderID="43659"   
         CustomerID="676"   
         OrderDate="2001-07-01"   
         DueDate="2001-07-13T00:00:00"   
         ShipDate="00:00:00" />   
  <Order SalesOrderID="43660"   
         CustomerID="117"   
         OrderDate="2001-07-01"   
         DueDate="2001-07-13T00:00:00"   
         ShipDate="00:00:00" />   
 ...  
</ROOT>  
```  
  
 <span data-ttu-id="ae15e-174">これは、これと同等の XDR スキーマです。</span><span class="sxs-lookup"><span data-stu-id="ae15e-174">This is the equivalent XDR schema:</span></span>  
  
```  
<?xml version="1.0" ?>  
<Schema xmlns="urn:schemas-microsoft-com:xml-data"  
        xmlns:dt="urn:schemas-microsoft-com:datatypes"  
        xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  
<ElementType name="Order" sql:relation="Sales.SalesOrderHeader">  
    <AttributeType name="SalesOrderID" />  
    <AttributeType name="CustomerID"  />  
    <AttributeType name="OrderDate" dt:type="date" />  
    <AttributeType name="DueDate" />  
    <AttributeType name="ShipDate" dt:type="time" />  
  
    <attribute type="SalesOrderID" sql:field="OrderID" />  
    <attribute type="CustomerID" sql:field="CustomerID" />  
    <attribute type="OrderDate" sql:field="OrderDate" />  
    <attribute type="DueDate" sql:field="DueDate" />  
    <attribute type="ShipDate" sql:field="ShipDate" />  
</ElementType>  
</Schema>  
```  
  
### <a name="b-specifying-sql-data-type-using-sqldatatype"></a><span data-ttu-id="ae15e-175">B.</span><span class="sxs-lookup"><span data-stu-id="ae15e-175">B.</span></span> <span data-ttu-id="ae15e-176">sql:datatype を使用して SQL データ型を指定する</span><span class="sxs-lookup"><span data-stu-id="ae15e-176">Specifying SQL data type using sql:datatype</span></span>  
 <span data-ttu-id="ae15e-177">実際のサンプルについては、「 [XML 一括読み込みの例 &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/xml-bulk-load-examples-sqlxml-4-0.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ae15e-177">For a working sample, see Example G in [XML Bulk Load Examples &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/xml-bulk-load-examples-sqlxml-4-0.md).</span></span> <span data-ttu-id="ae15e-178">この例では、"{" および "}" を含む GUID 値の一括読み込みが行われます。</span><span class="sxs-lookup"><span data-stu-id="ae15e-178">In this example, a GUID value including "{" and "}" is bulk loaded.</span></span> <span data-ttu-id="ae15e-179">この例のスキーマでは、`sql:datatype` を指定し、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型を `uniqueidentifier` として識別します。</span><span class="sxs-lookup"><span data-stu-id="ae15e-179">The schema in this example specifies `sql:datatype` to identify the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type as `uniqueidentifier`.</span></span> <span data-ttu-id="ae15e-180">この例は、どのような場合にスキーマで `sql:datatype` を指定する必要があるかを示すものです。</span><span class="sxs-lookup"><span data-stu-id="ae15e-180">This example illustrate when `sql:datatype` must be specified in the schema.</span></span>  
  
  
