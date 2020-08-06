---
title: インライン XSD スキーマの生成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- XSD schemas [SQL Server]
- XMLSCHEMA option
- schemas [SQL Server], XML
- XDR schemas
- FOR XML clause, inline XSD schema generation
- inline XSD schema generation [SQL Server]
- XMLDATA option
ms.assetid: 04b35145-1cca-45f4-9eb7-990abf2e647d
author: rothja
ms.author: jroth
ms.openlocfilehash: 2af748d4fc6ae67f57568be58ec7f59876098f52
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743073"
---
# <a name="generate-an-inline-xsd-schema"></a><span data-ttu-id="48a2b-102">インライン XSD スキーマの生成</span><span class="sxs-lookup"><span data-stu-id="48a2b-102">Generate an Inline XSD Schema</span></span>
  <span data-ttu-id="48a2b-103">FOR XML 句では、クエリからクエリ結果と共にインライン スキーマを返すように要求できます。</span><span class="sxs-lookup"><span data-stu-id="48a2b-103">In a FOR XML clause, you can request that your query return an inline schema together with the query results.</span></span> <span data-ttu-id="48a2b-104">XDR スキーマが必要な場合は、FOR XML 句に XMLDATA キーワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="48a2b-104">If you want an XDR schema, you use the XMLDATA keyword in the FOR XML clause.</span></span> <span data-ttu-id="48a2b-105">XSD スキーマが必要な場合は、XMLSCHEMA キーワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="48a2b-105">If you want an XSD schema, you use the XMLSCHEMA keyword.</span></span>  
  
 <span data-ttu-id="48a2b-106">このトピックでは、XMLSCHEMA キーワードとこのキーワードで生成されるインライン XSD スキーマについて説明します。</span><span class="sxs-lookup"><span data-stu-id="48a2b-106">This topic describes the XMLSCHEMA keyword and explains the structure of the resulting inline XSD schema.</span></span> <span data-ttu-id="48a2b-107">次に、インライン スキーマを要求するときの制限事項を示します。</span><span class="sxs-lookup"><span data-stu-id="48a2b-107">Following are the limitations when you are requesting inline schemas:</span></span>  
  
-   <span data-ttu-id="48a2b-108">XMLSCHEMA は、RAW モードと AUTO モードでのみ指定できます。EXPLICIT モードでは指定できません。</span><span class="sxs-lookup"><span data-stu-id="48a2b-108">You can specify XMLSCHEMA only in RAW and AUTO mode, not in EXPLICIT mode.</span></span>  
  
-   <span data-ttu-id="48a2b-109">入れ子になった FOR XML クエリで TYPE ディレクティブを指定すると、そのクエリ結果は `xml` 型になるので、この結果は型指定されていない XML データのインスタンスとして処理されます。</span><span class="sxs-lookup"><span data-stu-id="48a2b-109">If a nested FOR XML query specifies the TYPE directive, the query result is of `xml` type, and this result is treated as an instance of untyped XML data.</span></span> <span data-ttu-id="48a2b-110">詳細については、「[XML データ &#40;SQL Server&#41;](xml-data-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="48a2b-110">For more information, see [XML Data &#40;SQL Server&#41;](xml-data-sql-server.md).</span></span>  
  
 <span data-ttu-id="48a2b-111">FOR XML クエリに XMLSCHEMA を指定すると、クエリ結果としてスキーマと XML データの両方が返されます。</span><span class="sxs-lookup"><span data-stu-id="48a2b-111">When you specify XMLSCHEMA in a FOR XML query, you receive both a schema and XML data, the query result.</span></span> <span data-ttu-id="48a2b-112">データの最上位レベルの各要素が既定の名前空間宣言を使用して前のスキーマを参照し、次に、既定の名前空間宣言がインライン スキーマの対象の名前空間を参照します。</span><span class="sxs-lookup"><span data-stu-id="48a2b-112">Each top-level element of the data refers to the previous schema by using a default namespace declaration that, in turn, refers to the target namespace of the inline schema.</span></span>  
  
 <span data-ttu-id="48a2b-113">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="48a2b-113">For example:</span></span>  
  
```  
<xsd:schema targetNamespace="urn:schemas-microsoft-com:sql:SqlRowSet1" xmlns:schema="urn:schemas-microsoft-com:sql:SqlRowSet1" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:sqltypes="https://schemas.microsoft.com/sqlserver/2004/sqltypes" elementFormDefault="qualified">  
  <xsd:import namespace="https://schemas.microsoft.com/sqlserver/2004/sqltypes" schemaLocation="https://schemas.microsoft.com/sqlserver/2004/sqltypes/sqltypes.xsd" />  
  <xsd:element name="Production.ProductModel">  
    <xsd:complexType>  
      <xsd:attribute name="ProductModelID" type="sqltypes:int" use="required" />  
      <xsd:attribute name="Name" use="required">  
        <xsd:simpleType sqltypes:sqlTypeAlias="[AdventureWorks2012].[dbo].[Name]">  
          <xsd:restriction base="sqltypes:nvarchar" sqltypes:localeId="1033" sqltypes:sqlCompareOptions="IgnoreCase IgnoreKanaType IgnoreWidth" sqltypes:sqlSortId="52">  
            <xsd:maxLength value="50" />  
          </xsd:restriction>  
        </xsd:simpleType>  
      </xsd:attribute>  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
<Production.ProductModel xmlns="urn:schemas-microsoft-com:sql:SqlRowSet1" ProductModelID="1" Name="Classic Vest" />  
```  
  
 <span data-ttu-id="48a2b-114">クエリ結果には、XML スキーマと XML 結果が含まれます。</span><span class="sxs-lookup"><span data-stu-id="48a2b-114">The result includes XML schema and the XML result.</span></span> <span data-ttu-id="48a2b-115">結果内の最上位レベルにある <`ProductModel`> 要素では、既定の名前空間宣言 xmlns="urn:schemas-microsoft-com:sql:SqlRowSet1" を使用してスキーマが参照されます。</span><span class="sxs-lookup"><span data-stu-id="48a2b-115">The <`ProductModel`> top-level element in the result refers to the schema by using the default namespace declaration, xmlns="urn:schemas-microsoft-com:sql:SqlRowSet1" .</span></span>  
  
 <span data-ttu-id="48a2b-116">結果のスキーマ部分には、複数の名前空間を説明する複数のスキーマ ドキュメントが含まれることがあります。</span><span class="sxs-lookup"><span data-stu-id="48a2b-116">The schema part of the result may contain multiple schema documents that describe multiple namespaces.</span></span> <span data-ttu-id="48a2b-117">少なくとも次の 2 つのスキーマ ドキュメントが返されます。</span><span class="sxs-lookup"><span data-stu-id="48a2b-117">At a minimum, the following two schema documents are returned:</span></span>  
  
-   <span data-ttu-id="48a2b-118">**Sqltypes** 名前空間のスキーマ ドキュメント。このドキュメントには SQL の基本データ型が返されます。</span><span class="sxs-lookup"><span data-stu-id="48a2b-118">One schema document for the **Sqltypes** namespace, and for which the base SQL types are being returned.</span></span>  
  
-   <span data-ttu-id="48a2b-119">FOR XML クエリの結果の構造が記述されたスキーマ ドキュメント。</span><span class="sxs-lookup"><span data-stu-id="48a2b-119">Another schema document that describes the shape of the FOR XML query result.</span></span>  
  
 <span data-ttu-id="48a2b-120">型指定された `xml` データ型がクエリ結果に含まれている場合は、それらの型指定された `xml` データ型に関連付けられたスキーマも含まれます。</span><span class="sxs-lookup"><span data-stu-id="48a2b-120">Also, if any typed `xml` data types are included in the query result, the schemas associated with those typed `xml` data types are included.</span></span>  
  
 <span data-ttu-id="48a2b-121">FOR XML クエリ結果の構造が記述されたスキーマ ドキュメントの対象の名前空間には、固定部分と自動的に値が増加する数値部分があります。</span><span class="sxs-lookup"><span data-stu-id="48a2b-121">The target namespace of the schema document that describes the shape of the FOR XML result contains a fixed portion and a numeric portion that increments automatically.</span></span> <span data-ttu-id="48a2b-122">この名前空間の形式を次に示します。 *n* は正の整数です。</span><span class="sxs-lookup"><span data-stu-id="48a2b-122">The format of this namespace is shown in the following where *n* is a positive integer.</span></span> <span data-ttu-id="48a2b-123">たとえば、上記のクエリでは urn:schemas-microsoft-com:sql:SqlRowSet1 が対象の名前空間です。</span><span class="sxs-lookup"><span data-stu-id="48a2b-123">For example, in the previous query, urn:schemas-microsoft-com:sql:SqlRowSet1 is the target namespace.</span></span>  
  
```  
urn:schemas-microsoft-com:sql:SqlRowSetn  
```  
  
 <span data-ttu-id="48a2b-124">クエリを実行するたびに、返される結果の対象の名前空間が変化することは望ましくありません。</span><span class="sxs-lookup"><span data-stu-id="48a2b-124">The change in the target namespaces in the result that occurred from one execution to another may not be desirable.</span></span> <span data-ttu-id="48a2b-125">たとえば、返された XML へのクエリを実行する場合に、対象の名前空間が変化すると、クエリの更新が必要になります。</span><span class="sxs-lookup"><span data-stu-id="48a2b-125">For example, if you query the resulting XML, the change in target namespace will require that you update your query.</span></span> <span data-ttu-id="48a2b-126">XMLSCHEMA オプションを FOR XML 句に追加するときに、必要に応じて対象の名前空間を指定できます。</span><span class="sxs-lookup"><span data-stu-id="48a2b-126">You can optionally specify a target namespace when the XMLSCHEMA option is added in the FOR XML clause.</span></span> <span data-ttu-id="48a2b-127">返される XML には指定した名前空間が含まれ、何度そのクエリを実行しても変化しません。</span><span class="sxs-lookup"><span data-stu-id="48a2b-127">The resulting XML will include the namespace you provided and will remain the same, regardless of how many times you run the query.</span></span>  
  
```  
SELECT ProductModelID, Name  
FROM   Production.ProductModel  
WHERE ProductModelID=1  
FOR XML AUTO, XMLSCHEMA ('MyURI')  
```  
  
## <a name="entity-elements"></a><span data-ttu-id="48a2b-128">エンティティ要素</span><span class="sxs-lookup"><span data-stu-id="48a2b-128">Entity Elements</span></span>  
 <span data-ttu-id="48a2b-129">クエリ結果として生成される XSD スキーマ構造の詳細を説明するには、まずエンティティ要素について説明する必要があります。</span><span class="sxs-lookup"><span data-stu-id="48a2b-129">In order to discuss the details of the XSD schema structure generated for the query result, the entity element has to first be described</span></span>  
  
 <span data-ttu-id="48a2b-130">FOR XML クエリで返される XML データのエンティティ要素は、列ではなくテーブルから生成される要素です。</span><span class="sxs-lookup"><span data-stu-id="48a2b-130">An entity element in the XML data returned by FOR XML query is an element that is generated from a table and not from a column.</span></span> <span data-ttu-id="48a2b-131">たとえば、次の FOR XML クエリを実行すると、 `Person` データベースの `AdventureWorks2012` テーブルから連絡先に関する情報が返されます。</span><span class="sxs-lookup"><span data-stu-id="48a2b-131">For example, the following FOR XML query returns contact information from the `Person` table in the `AdventureWorks2012` database.</span></span>  
  
```  
SELECT BusinessEntityID, FirstName  
FROM Person.Person  
WHERE BusinessEntityID = 1  
FOR XML AUTO, ELEMENTS  
```  
  
 <span data-ttu-id="48a2b-132">結果を次に示します。</span><span class="sxs-lookup"><span data-stu-id="48a2b-132">This is the result:</span></span>  
  
 `<Person>`  
  
 `<BusinessEntityID>1</BusinessEntityID>`  
  
 `<FirstName>Ken</FirstName>`  
  
 `</Person>`  
  
 <span data-ttu-id="48a2b-133">この結果では、<`Person`> がエンティティ要素です。</span><span class="sxs-lookup"><span data-stu-id="48a2b-133">In this result, <`Person`> is the entity element.</span></span> <span data-ttu-id="48a2b-134">XML 結果には複数のエンティティ要素が含まれることもあります。各エンティティ要素のインライン XSD スキーマには、グローバル宣言が含まれます。</span><span class="sxs-lookup"><span data-stu-id="48a2b-134">There can be multiple entity elements in the XML result and each of these has a global declaration in the inline XSD schema.</span></span> <span data-ttu-id="48a2b-135">たとえば、次のクエリを実行すると、特定の注文の販売注文ヘッダーと詳細情報が取得されます。</span><span class="sxs-lookup"><span data-stu-id="48a2b-135">For example, the following query retrieves sales order header and detail information for a specific order.</span></span>  
  
```  
SELECT  SalesOrderHeader.SalesOrderID, ProductID, OrderQty  
FROM    Sales.SalesOrderHeader, Sales.SalesOrderDetail  
WHERE   SalesOrderHeader.SalesOrderID = SalesOrderDetail.SalesOrderID  
AND     SalesOrderHeader.SalesOrderID=5001  
FOR XML AUTO, ELEMENTS, XMLSCHEMA  
```  
  
 <span data-ttu-id="48a2b-136">このクエリには ELEMENTS ディレクティブが指定されているので、返される XML は要素中心になります。</span><span class="sxs-lookup"><span data-stu-id="48a2b-136">Because the query specifies the ELEMENTS directive, the resulting XML is element-centric.</span></span> <span data-ttu-id="48a2b-137">また、このクエリには XMLSCHEMA ディレクティブも指定されています。</span><span class="sxs-lookup"><span data-stu-id="48a2b-137">The query also specifies the XMLSCHEMA directive.</span></span> <span data-ttu-id="48a2b-138">したがって、インライン XSD スキーマが返されます。</span><span class="sxs-lookup"><span data-stu-id="48a2b-138">Therefore, an inline XSD schema is returned.</span></span> <span data-ttu-id="48a2b-139">結果を次に示します。</span><span class="sxs-lookup"><span data-stu-id="48a2b-139">This is the result:</span></span>  
  
 `<xsd:schema targetNamespace="urn:schemas-microsoft-com:sql:SqlRowSet1" xmlns:schema="urn:schemas-microsoft-com:sql:SqlRowSet1" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:sqltypes="https://schemas.microsoft.com/sqlserver/2004/sqltypes" elementFormDefault="qualified">`  
  
 `<xsd:import namespace="https://schemas.microsoft.com/sqlserver/2004/sqltypes" schemaLocation="https://schemas.microsoft.com/sqlserver/2004/sqltypes/sqltypes.xsd" />`  
  
 `<xsd:element name="Sales.SalesOrderHeader">`  
  
 `<xsd:complexType>`  
  
 `<xsd:sequence>`  
  
 `<xsd:element name="SalesOrderID" type="sqltypes:int" />`  
  
 `<xsd:element ref="schema:Sales.SalesOrderDetail" minOccurs="0" maxOccurs="unbounded" />`  
  
 `</xsd:sequence>`  
  
 `</xsd:complexType>`  
  
 `</xsd:element>`  
  
 `<xsd:element name="Sales.SalesOrderDetail">`  
  
 `<xsd:complexType>`  
  
 `<xsd:sequence>`  
  
 `<xsd:element name="ProductID" type="sqltypes:int" />`  
  
 `<xsd:element name="OrderQty" type="sqltypes:smallint" />`  
  
 `</xsd:sequence>`  
  
 `</xsd:complexType>`  
  
 `</xsd:element>`  
  
 `</xsd:schema>`  
  
 <span data-ttu-id="48a2b-140">上のクエリに関して、次の点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="48a2b-140">Note the following from the previous query:</span></span>  
  
-   <span data-ttu-id="48a2b-141">このクエリ結果では、<`SalesOrderHeader`> と <`SalesOrderDetail`> がエンティティ要素です。</span><span class="sxs-lookup"><span data-stu-id="48a2b-141">In the result, <`SalesOrderHeader`> and <`SalesOrderDetail`> are entity elements.</span></span> <span data-ttu-id="48a2b-142">したがって、これらの要素はスキーマ内でグローバルに宣言されます。</span><span class="sxs-lookup"><span data-stu-id="48a2b-142">Because of this, they are globally declared in the schema.</span></span> <span data-ttu-id="48a2b-143">つまり、宣言は <`Schema`> 要素内の最上位レベルに記述されます。</span><span class="sxs-lookup"><span data-stu-id="48a2b-143">That is, the declaration appears at the top level inside the <`Schema`> element.</span></span>  
  
-   <span data-ttu-id="48a2b-144"><`SalesOrderID`>、<`ProductID`>、および <`OrderQty`> は列にマップされるので、エンティティ要素ではありません。</span><span class="sxs-lookup"><span data-stu-id="48a2b-144">The <`SalesOrderID`>, <`ProductID`>, and <`OrderQty`> are not entity elements, because they map to columns.</span></span> <span data-ttu-id="48a2b-145">ELEMENTS ディレクティブを指定したので、列データは XML の要素として返されます。</span><span class="sxs-lookup"><span data-stu-id="48a2b-145">The column data is returned as elements in the XML, because of the ELEMENTS directive.</span></span> <span data-ttu-id="48a2b-146">これらの要素は、エンティティ要素の複合型のローカル要素にマップされます。</span><span class="sxs-lookup"><span data-stu-id="48a2b-146">These are mapped to local elements of the entity element's complex type.</span></span> <span data-ttu-id="48a2b-147">ELEMENTS ディレクティブを指定しないと、 `SalesOrderID`、 `ProductID` 、および `OrderQty` の各値は、対応するエンティティ要素の複合型のローカル属性にマップされることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="48a2b-147">Note that if the ELEMENTS directive is not specified, the `SalesOrderID`, `ProductID` and `OrderQty` values are mapped to local attributes of the corresponding entity element's complex type.</span></span>  
  
## <a name="attribute-name-clashes"></a><span data-ttu-id="48a2b-148">属性名の競合</span><span class="sxs-lookup"><span data-stu-id="48a2b-148">Attribute Name Clashes</span></span>  
 <span data-ttu-id="48a2b-149">次の説明は、 `CustOrder` テーブルと `CustOrderDetail` テーブルに基づいています。</span><span class="sxs-lookup"><span data-stu-id="48a2b-149">The following discussion is based on the `CustOrder` and `CustOrderDetail` tables.</span></span> <span data-ttu-id="48a2b-150">次のサンプルをテストするには、これらのテーブルを作成し、独自のサンプル データを追加してください。</span><span class="sxs-lookup"><span data-stu-id="48a2b-150">To test the following samples, create these tables and add your own sample data:</span></span>  
  
```  
CREATE TABLE CustOrder (OrderID int primary key, CustomerID int)  
GO  
CREATE TABLE CustOrderDetail (OrderID int, ProductID int, Qty int)  
GO  
```  
  
 <span data-ttu-id="48a2b-151">FOR XML では、同じ名前でさまざまなプロパティや属性が示されることがあります。</span><span class="sxs-lookup"><span data-stu-id="48a2b-151">In FOR XML, the same name is sometimes used to indicate different properties, attributes.</span></span> <span data-ttu-id="48a2b-152">たとえば、次の属性中心の RAW モードのクエリを実行すると、OrderID という同じ名前の 2 つの属性が生成されます。</span><span class="sxs-lookup"><span data-stu-id="48a2b-152">For example, the following attribute-centric RAW mode query generates two attributes that have the same name, OrderID.</span></span> <span data-ttu-id="48a2b-153">これにより、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="48a2b-153">This generates an error.</span></span>  
  
```  
SELECT CustOrder.OrderID,   
       CustOrderDetail.ProductID,   
       CustOrderDetail.OrderID  
FROM   dbo.CustOrder, dbo.CustOrderDetail  
WHERE  CustOrder.OrderID = CustOrderDetail.OrderID  
FOR XML RAW, XMLSCHEMA  
```  
  
 <span data-ttu-id="48a2b-154">ただし、2 つの要素が同じ名前になることは許容されるので、次のように ELEMENTS ディレクティブを追加することでこの問題を解決できます。</span><span class="sxs-lookup"><span data-stu-id="48a2b-154">However, because it is acceptable to have two elements that have the same name, you can eliminate the problem by adding the ELEMENTS directive:</span></span>  
  
```  
SELECT CustOrder.OrderID,  
       CustOrderDetail.ProductID,   
       CustOrderDetail.OrderID  
from   dbo.CustOrder, dbo.CustOrderDetail  
where  CustOrder.OrderID = CustOrderDetail.OrderID  
FOR XML RAW, XMLSCHEMA, ELEMENTS  
```  
  
 <span data-ttu-id="48a2b-155">結果は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="48a2b-155">This is the result.</span></span> <span data-ttu-id="48a2b-156">インライン XSD スキーマで OrderID 要素が 2 回定義されていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="48a2b-156">Note in the inline XSD schema, the OrderID element is defined two times.</span></span> <span data-ttu-id="48a2b-157">一方の宣言では、CustOrderDetail テーブルの OrderID に合わせて、minOccurs が 0 に設定されます。もう一方の宣言は、minOccurs が既定で 1 に設定される `CustOrder` テーブルの OrderID 主キー列にマップされます。</span><span class="sxs-lookup"><span data-stu-id="48a2b-157">One of the declarations has minOccurs set to 0, corresponding to the OrderID from the CustOrderDetail table, and the second one maps to the OrderID primary key column of the `CustOrder` table where minOccurs is 1 by default.</span></span>  
  
 `<xsd:schema targetNamespace="urn:schemas-microsoft-com:sql:SqlRowSet1" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:sqltypes="https://schemas.microsoft.com/sqlserver/2004/sqltypes" elementFormDefault="qualified">`  
  
 `<xsd:import namespace="https://schemas.microsoft.com/sqlserver/2004/sqltypes" schemaLocation="https://schemas.microsoft.com/sqlserver/2004/sqltypes/sqltypes.xsd" />`  
  
 `<xsd:element name="row">`  
  
 `<xsd:complexType>`  
  
 `<xsd:sequence>`  
  
 `<xsd:element name="OrderID" type="sqltypes:int" />`  
  
 `<xsd:element name="ProductID" type="sqltypes:int" minOccurs="0" />`  
  
 `<xsd:element name="OrderID" type="sqltypes:int" minOccurs="0" />`  
  
 `</xsd:sequence>`  
  
 `</xsd:complexType>`  
  
 `</xsd:element>`  
  
 `</xsd:schema>`  
  
## <a name="element-name-clashes"></a><span data-ttu-id="48a2b-158">要素名の競合</span><span class="sxs-lookup"><span data-stu-id="48a2b-158">Element Name Clashes</span></span>  
 <span data-ttu-id="48a2b-159">FOR XML では、同じ名前で 2 つのサブ要素を示すことができます。</span><span class="sxs-lookup"><span data-stu-id="48a2b-159">In FOR XML, the same name can be used to indicate two subelements.</span></span> <span data-ttu-id="48a2b-160">たとえば、次のクエリでは製品の ListPrice と DealerPrice の値が取得されますが、これら 2 つの列に Price という同じ別名が指定されます。</span><span class="sxs-lookup"><span data-stu-id="48a2b-160">For example, the following query retrieves ListPrice and DealerPrice values of products, but the query specifies the same alias, Price, for these two columns.</span></span> <span data-ttu-id="48a2b-161">したがって、返される行セットには同じ名前の列が 2 つ含まれます。</span><span class="sxs-lookup"><span data-stu-id="48a2b-161">Therefore, the resulting rowset will have two columns with same name.</span></span>  
  
### <a name="case-1-both-subelements-are-nonkey-columns-of-the-same-type-and-can-be-null"></a><span data-ttu-id="48a2b-162">ケース 1: 2 つのサブ要素が同じ型の非キー列でどちらも NULL 値が許容される場合</span><span class="sxs-lookup"><span data-stu-id="48a2b-162">Case 1: Both subelements are nonkey columns of the same type and can be NULL</span></span>  
 <span data-ttu-id="48a2b-163">次のクエリの 2 つのサブ要素は同じ型の非キー列で、どちらも NULL 値が許容されます。</span><span class="sxs-lookup"><span data-stu-id="48a2b-163">In the following query, both subelements are nonkey columns of the same type and can be NULL.</span></span>  
  
```  
DROP TABLE T  
go  
CREATE TABLE T (ProductID int primary key, ListPrice money, DealerPrice money)  
go  
INSERT INTO T values (1, 1.25, null)  
go  
  
SELECT ProductID, ListPrice Price, DealerPrice Price  
FROM   T  
for    XML RAW, ELEMENTS, XMLSCHEMA  
```  
  
 <span data-ttu-id="48a2b-164">このクエリを実行すると、次のような XML が生成されます。</span><span class="sxs-lookup"><span data-stu-id="48a2b-164">This is the corresponding XML generated.</span></span> <span data-ttu-id="48a2b-165">インライン XSD の一部のみを示します。</span><span class="sxs-lookup"><span data-stu-id="48a2b-165">Only a fraction of the inline XSD is shown:</span></span>  
  
 `...`  
  
 `<xsd:schema targetNamespace="urn:schemas-microsoft-com:sql:SqlRowSet1" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:sqltypes="https://schemas.microsoft.com/sqlserver/2004/sqltypes" elementFormDefault="qualified">`  
  
 `<xsd:import namespace="https://schemas.microsoft.com/sqlserver/2004/sqltypes" />`  
  
 `<xsd:element name="row">`  
  
 `<xsd:complexType>`  
  
 `<xsd:sequence>`  
  
 `<xsd:element name="ProductID" type="sqltypes:int" />`  
  
 `<xsd:element name="Price" type="sqltypes:money" minOccurs="0" maxOccurs="2" />`  
  
 `</xsd:sequence>`  
  
 `</xsd:complexType>`  
  
 `</xsd:element>`  
  
 `</xsd:schema>`  
  
 `<row xmlns="urn:schemas-microsoft-com:sql:SqlRowSet1">`  
  
 `<ProductID>1</ProductID>`  
  
 `<Price>1.2500</Price>`  
  
 `</row>`  
  
 <span data-ttu-id="48a2b-166">このインライン XSD スキーマでは、次の点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="48a2b-166">Note the following in the inline XSD schema:</span></span>  
  
-   <span data-ttu-id="48a2b-167">ListPrice と DealerPrice は `money`という同じ型で、テーブルではどちらも NULL 値が許容されます。</span><span class="sxs-lookup"><span data-stu-id="48a2b-167">Both the ListPrice and DealerPrice are of the same type, `money`, and both can be NULL in the table.</span></span> <span data-ttu-id="48a2b-168">したがって、これらの要素は返される XML に含まれないので、<`row`> 要素の複合型の宣言には、minOccurs が 0、maxOccurs が 2 に指定された 1 つの <`Price`> 子要素のみが含まれます。</span><span class="sxs-lookup"><span data-stu-id="48a2b-168">Therefore, because they may not be returned in the resulting XML, there is only one <`Price`> child element in the complex type declaration of the <`row`> element that has minOccurs=0 and maxOccurs=2.</span></span>  
  
-   <span data-ttu-id="48a2b-169">テーブルの `DealerPrice` の値が NULL なので、クエリ結果には、`ListPrice` のみが <`Price`> 要素として返されます。</span><span class="sxs-lookup"><span data-stu-id="48a2b-169">In the result, because the `DealerPrice` value is NULL in the table, only `ListPrice` is returned as a <`Price`> element.</span></span> <span data-ttu-id="48a2b-170">`XSINIL` パラメーターを ELEMENTS ディレクティブに追加すると、返される両方の要素で、DealerPrice に対応する <`Price`> 要素の `xsi:nil` の値が TRUE に設定されます。</span><span class="sxs-lookup"><span data-stu-id="48a2b-170">If you add the `XSINIL` parameter to the ELEMENTS directive, you will receive both of the elements that have the `xsi:nil` value set to TRUE for the<`Price`> element that corresponds to DealerPrice.</span></span> <span data-ttu-id="48a2b-171">また、インライン XSD スキーマの <`row`> の複合型の定義として 2 つの <`Price`> 子要素が返されます。どちらの要素でも `nillable` 属性が TRUE に設定されます。</span><span class="sxs-lookup"><span data-stu-id="48a2b-171">You will also receive two <`Price`> child elements in the <`row`> complex type definition in the inline XSD schema with the `nillable` attribute set to TRUE for both.</span></span> <span data-ttu-id="48a2b-172">結果の一部を次に示します。</span><span class="sxs-lookup"><span data-stu-id="48a2b-172">This fragment is a partial result:</span></span>  
  
 `...`  
  
 `<xsd:schema targetNamespace="urn:schemas-microsoft-com:sql:SqlRowSet1" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:sqltypes="https://schemas.microsoft.com/sqlserver/2004/sqltypes" elementFormDefault="qualified">`  
  
 `<xsd:import namespace="https://schemas.microsoft.com/sqlserver/2004/sqltypes" />`  
  
 `<xsd:element name="row">`  
  
 `<xsd:complexType>`  
  
 `<xsd:sequence>`  
  
 `<xsd:element name="ProductID" type="sqltypes:int" nillable="1" />`  
  
 `<xsd:element name="Price" type="sqltypes:money" nillable="1" />`  
  
 `<xsd:element name="Price" type="sqltypes:money" nillable="1" />`  
  
 `</xsd:sequence>`  
  
 `</xsd:complexType>`  
  
 `</xsd:element>`  
  
 `</xsd:schema>`  
  
 `<row xmlns="urn:schemas-microsoft-com:sql:SqlRowSet1" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">`  
  
 `<ProductID>1</ProductID>`  
  
 `<Price>1.2500</Price>`  
  
 `<Price xsi:nil="true" />`  
  
 `</row>`  
  
### <a name="case-2-one-key-and-one-nonkey-column-of-the-same-type"></a><span data-ttu-id="48a2b-173">ケース 2: 同じ型でも一方がキー列で他方が非キー列の場合</span><span class="sxs-lookup"><span data-stu-id="48a2b-173">Case 2: One key and one nonkey column of the same type</span></span>  
 <span data-ttu-id="48a2b-174">次のクエリでは、型が同じ型でも一方がキー列で他方が非キー列の場合について説明します。</span><span class="sxs-lookup"><span data-stu-id="48a2b-174">The following query illustrates one key and one nonkey column of the same type.</span></span>  
  
```  
CREATE TABLE T (Col1 int primary key, Col2 int, Col3 nvarchar(20))  
go  
INSERT INTO T VALUES (1, 1, 'test')  
go   
```  
  
 <span data-ttu-id="48a2b-175">テーブル **T** に対する次のクエリでは、Col1 と Col2 に同じ別名を指定します。主キー Col1 では NULL 値が許容されませんが、Col2 では NULL 値が許容されます。</span><span class="sxs-lookup"><span data-stu-id="48a2b-175">The following query against table **T** specifies the same alias for Col1 and Col2, where Col1 is a primary key and cannot be null, and Col2 can be null.</span></span> <span data-ttu-id="48a2b-176">このクエリを実行すると、<`row`> 要素の子要素である 2 つの兄弟要素が生成されます。</span><span class="sxs-lookup"><span data-stu-id="48a2b-176">This generates two sibling elements that are children of the <`row`> element.</span></span>  
  
```  
SELECT Col1 as Col, Col2 as Col, Col3  
FROM T  
FOR XML RAW, ELEMENTS, XMLSCHEMA  
```  
  
 <span data-ttu-id="48a2b-177">結果は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="48a2b-177">This is the result.</span></span> <span data-ttu-id="48a2b-178">インライン XSD スキーマの一部のみを示します。</span><span class="sxs-lookup"><span data-stu-id="48a2b-178">Only a fragment of the inline XSD schema is shown.</span></span>  
  
 `...`  
  
 `<xsd:schema targetNamespace="urn:schemas-microsoft-com:sql:SqlRowSet1" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:sqltypes="https://schemas.microsoft.com/sqlserver/2004/sqltypes" elementFormDefault="qualified">`  
  
 `<xsd:import namespace="https://schemas.microsoft.com/sqlserver/2004/sqltypes" />`  
  
 `<xsd:element name="row">`  
  
 `<xsd:complexType>`  
  
 `<xsd:sequence>`  
  
 `<xsd:element name="Col" type="sqltypes:int" />`  
  
 `<xsd:element name="Col" type="sqltypes:int" minOccurs="0" />`  
  
 `<xsd:element name="Col3" minOccurs="0">`  
  
 `<xsd:simpleType>`  
  
 `<xsd:restriction base="sqltypes:nvarchar"`  
  
 `sqltypes:localeId="1033"`  
  
 `sqltypes:sqlCompareOptions="IgnoreCase`  
  
 `IgnoreKanaType IgnoreWidth"`  
  
 `sqltypes:sqlSortId="52">`  
  
 `<xsd:maxLength value="20" />`  
  
 `</xsd:restriction>`  
  
 `</xsd:simpleType>`  
  
 `</xsd:element>`  
  
 `</xsd:sequence>`  
  
 `</xsd:complexType>`  
  
 `</xsd:element>`  
  
 `</xsd:schema>`  
  
 `<row xmlns="urn:schemas-microsoft-com:sql:SqlRowSet1">`  
  
 `<Col>1</Col>`  
  
 `<Col>1</Col>`  
  
 `<Col3>test</Col3>`  
  
 `</row>`  
  
 <span data-ttu-id="48a2b-179">インライン XSD スキーマで、Col2 に対応する <`Col`> 要素の minOccurs が 0 に設定されていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="48a2b-179">Note in the inline XSD schema that the <`Col`> element corresponding to the Col2 has minOccurs set to 0.</span></span>  
  
### <a name="case-3-both-elements-of-different-types-and-corresponding-columns-can-be-null"></a><span data-ttu-id="48a2b-180">ケース 3: 2 つの要素の型が異なり、対応する列で NULL 値が許容される場合</span><span class="sxs-lookup"><span data-stu-id="48a2b-180">Case 3: Both elements of different types and corresponding columns can be NULL</span></span>  
 <span data-ttu-id="48a2b-181">ケース 2 で示したサンプル テーブルに対して、次のクエリを指定します。</span><span class="sxs-lookup"><span data-stu-id="48a2b-181">The following query is specified against the sample table shown in case 2:</span></span>  
  
```  
SELECT Col1, Col2 as Col, Col3 as Col  
FROM T  
FOR XML RAW, ELEMENTS, XMLSCHEMA  
```  
  
 <span data-ttu-id="48a2b-182">次のクエリでは、Col2 と Col3 に同じ別名を指定します。</span><span class="sxs-lookup"><span data-stu-id="48a2b-182">In the following query, Col2 and Col3 are given the same aliases.</span></span> <span data-ttu-id="48a2b-183">このクエリを実行すると、同じ名前の 2 つの兄弟要素がクエリ結果として生成され、両方とも <`raw`> 要素の子要素になります。</span><span class="sxs-lookup"><span data-stu-id="48a2b-183">This generates two sibling elements that have the same name and that are both children of the <`raw`> element in the result.</span></span> <span data-ttu-id="48a2b-184">これらの列の型はそれぞれ異なり、どちらも NULL 値が許容されます。</span><span class="sxs-lookup"><span data-stu-id="48a2b-184">Both of these columns are of different types and both can be NULL.</span></span> <span data-ttu-id="48a2b-185">結果は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="48a2b-185">This is the result.</span></span> <span data-ttu-id="48a2b-186">インライン XSD スキーマの一部のみを示します。</span><span class="sxs-lookup"><span data-stu-id="48a2b-186">Only partial inline XSD schema is shown.</span></span>  
  
 `...`  
  
 `<xsd:schema targetNamespace="urn:schemas-microsoft-com:sql:SqlRowSet1" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:sqltypes="https://schemas.microsoft.com/sqlserver/2004/sqltypes" elementFormDefault="qualified">`  
  
 `<xsd:import namespace="https://schemas.microsoft.com/sqlserver/2004/sqltypes" />`  
  
 `<xsd:simpleType name="Col1">`  
  
 `<xsd:restriction base="sqltypes:int" />`  
  
 `</xsd:simpleType>`  
  
 `<xsd:simpleType name="Col2">`  
  
 `<xsd:restriction base="sqltypes:nvarchar" sqltypes:localeId="1033"`  
  
 `sqltypes:sqlCompareOptions="IgnoreCase`  
  
 `IgnoreKanaType IgnoreWidth" sqltypes:sqlSortId="52">`  
  
 `<xsd:maxLength value="20" />`  
  
 `</xsd:restriction>`  
  
 `</xsd:simpleType>`  
  
 `<xsd:element name="row">`  
  
 `<xsd:complexType>`  
  
 `<xsd:sequence>`  
  
 `<xsd:element name="Col1" type="sqltypes:int" />`  
  
 `<xsd:element name="Col" minOccurs="0" maxOccurs="2" type="xsd:anySimpleType" />`  
  
 `</xsd:sequence>`  
  
 `</xsd:complexType>`  
  
 `</xsd:element>`  
  
 `</xsd:schema>`  
  
 `<row xmlns="urn:schemas-microsoft-com:sql:SqlRowSet1">`  
  
 `<Col1>1</Col1>`  
  
 `<Col xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"`  
  
 `xsi:type="Col1">1</Col>`  
  
 `<Col xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"`  
  
 `xsi:type="Col2">test</Col>`  
  
 `</row>`  
  
 <span data-ttu-id="48a2b-187">このインライン XSD スキーマでは、次の点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="48a2b-187">Note the following in the inline XSD schema:</span></span>  
  
-   <span data-ttu-id="48a2b-188">Col2 と Col3 の両方で NULL 値が許容されるので、<`Col`> 要素の宣言により、minOccurs が 0、maxOccurs が 2 にそれぞれ指定されます。</span><span class="sxs-lookup"><span data-stu-id="48a2b-188">Because both Col2 and Col3 can be NULL, the <`Col`> element declaration specifies the minOccurs as 0 and maxOccurs as 2.</span></span>  
  
-   <span data-ttu-id="48a2b-189">これらの <`Col`> 要素は兄弟なので、スキーマに含まれる要素の宣言は 1 つです。</span><span class="sxs-lookup"><span data-stu-id="48a2b-189">Because both the <`Col`> elements are siblings, there is one element declaration in the schema.</span></span> <span data-ttu-id="48a2b-190">また、型は異なりますが、どちらの要素も単純型なので、スキーマ内の要素の型は `xsd:anySimpleType`になります。</span><span class="sxs-lookup"><span data-stu-id="48a2b-190">Also, because both of the elements are also of different types, though both are simple types, the type of the element in the schema is `xsd:anySimpleType`.</span></span> <span data-ttu-id="48a2b-191">結果では、 `xsi:type` 属性により、それぞれのインスタンスの型が識別されます。</span><span class="sxs-lookup"><span data-stu-id="48a2b-191">In the result, each instance type is identified by the `xsi:type` attribute.</span></span>  
  
-   <span data-ttu-id="48a2b-192">クエリ結果の <`Col`> 要素のインスタンスはすべて、`xsi:type` 属性を使用して、インスタンスの型を参照します。</span><span class="sxs-lookup"><span data-stu-id="48a2b-192">In the result, every instance of the <`Col`> element refers to its instance type by using the `xsi:type` attribute.</span></span>  
  
  
