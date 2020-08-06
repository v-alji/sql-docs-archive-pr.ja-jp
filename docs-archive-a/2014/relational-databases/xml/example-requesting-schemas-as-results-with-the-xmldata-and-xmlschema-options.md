---
title: '例: XMLDATA オプションと XMLSCHEMA オプションを使用した結果としてのスキーマの要求 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- RAW mode, requesting schema example
- RAW mode, with XMLDATA and XMLSCHEMA
ms.assetid: 3504ca38-be66-42b2-8dab-f499c9584840
author: rothja
ms.author: jroth
ms.openlocfilehash: af244e3436df4d8665079ce20fb749a44021fe04
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739625"
---
# <a name="example-requesting-schemas-as-results-with-the-xmldata-and-xmlschema-options"></a><span data-ttu-id="26153-102">例: XMLDATA オプションと XMLSCHEMA オプションを使用した結果としてのスキーマの要求</span><span class="sxs-lookup"><span data-stu-id="26153-102">Example: Requesting Schemas as Results with the XMLDATA and XMLSCHEMA Options</span></span>
  <span data-ttu-id="26153-103">次のクエリでは、ドキュメント構造を記述する XML-DATA スキーマが返されます。</span><span class="sxs-lookup"><span data-stu-id="26153-103">The following query returns the XML-DATA schema that describes the document structure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="26153-104">例</span><span class="sxs-lookup"><span data-stu-id="26153-104">Example</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID, Name  
FROM Production.ProductModel  
WHERE ProductModelID=122 or ProductModelID=119  
FOR XML RAW, XMLDATA  
GO  
```  
  
 <span data-ttu-id="26153-105">結果を次に示します。</span><span class="sxs-lookup"><span data-stu-id="26153-105">This is the result:</span></span>  
  
```  
<Schema name="Schema1" xmlns="urn:schemas-microsoft-com:xml-data"   
        xmlns:dt="urn:schemas-microsoft-com:datatypes">  
  <ElementType name="row" content="empty" model="closed">  
    <AttributeType name="ProductModelID" dt:type="i4" />  
    <AttributeType name="Name" dt:type="string" />  
    <attribute type="ProductModelID" />  
    <attribute type="Name" />  
  </ElementType>  
</Schema>  
<row xmlns="x-schema:#Schema1" ProductModelID="122" Name="All-Purpose Bike Stand" />  
<row xmlns="x-schema:#Schema1" ProductModelID="119" Name="Bike Wash" />  
```  
  
> [!NOTE]
>  <span data-ttu-id="26153-106"><`Schema`> は、名前空間として宣言されます。</span><span class="sxs-lookup"><span data-stu-id="26153-106">The <`Schema`> is declared as a namespace.</span></span> <span data-ttu-id="26153-107">異なる複数の FOR XML クエリで複数の XML-Data スキーマを要求するときに、名前空間の競合を避けるために、名前空間識別子 (この例では `Schema1` ) はクエリを実行するたびに変わります。</span><span class="sxs-lookup"><span data-stu-id="26153-107">To avoid namespace collisions when multiple XML-Data schemas are requested in different FOR XML queries, the namespace identifier, `Schema1` in this example, changes with every query execution.</span></span> <span data-ttu-id="26153-108">名前空間識別子は**Schema_n_** で構成されます。ここで、 **_n_** は整数です。</span><span class="sxs-lookup"><span data-stu-id="26153-108">The namespace identifier is made up of **Schema_n_** where **_n_** is an integer.</span></span>  
  
 <span data-ttu-id="26153-109">`XMLSCHEMA` オプションを指定することにより、結果の XSD スキーマを要求できます。</span><span class="sxs-lookup"><span data-stu-id="26153-109">By specifying the `XMLSCHEMA` option, you can request the XSD schema for the result.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID, Name  
FROM Production.ProductModel  
WHERE ProductModelID=122 or ProductModelID=119  
FOR XML RAW, XMLSCHEMA  
GO  
```  
  
 <span data-ttu-id="26153-110">結果を次に示します。</span><span class="sxs-lookup"><span data-stu-id="26153-110">This is the result:</span></span>  
  
```  
<xsd:schema targetNamespace="urn:schemas-microsoft-com:sql:SqlRowSet1" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:sqltypes="https://schemas.microsoft.com/sqlserver/2004/sqltypes" elementFormDefault="qualified">  
  <xsd:import namespace="https://schemas.microsoft.com/sqlserver/2004/sqltypes" schemaLocation="https://schemas.microsoft.com/sqlserver/2004/sqltypes/sqltypes.xsd" />  
  <xsd:element name="row">  
    <xsd:complexType>  
      <xsd:attribute name="ProductModelID" type="sqltypes:int" use="required" />  
      <xsd:attribute name="Name" use="required">  
        <xsd:simpleType sqltypes:sqlTypeAlias="[AdventureWorks].[dbo].[Name]">  
          <xsd:restriction base="sqltypes:nvarchar" sqltypes:localeId="1033" sqltypes:sqlCompareOptions="IgnoreCase IgnoreKanaType IgnoreWidth" sqltypes:sqlSortId="52">  
            <xsd:maxLength value="50" />  
          </xsd:restriction>  
        </xsd:simpleType>  
      </xsd:attribute>  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
<row xmlns="urn:schemas-microsoft-com:sql:SqlRowSet1" ProductModelID="122" Name="All-Purpose Bike Stand" />  
<row xmlns="urn:schemas-microsoft-com:sql:SqlRowSet1" ProductModelID="119" Name="Bike Wash" />  
  
```  
  
 <span data-ttu-id="26153-111">FOR XML の XMLSCHEMA には、省略可能な引数として対象名前空間 URI を指定できます。</span><span class="sxs-lookup"><span data-stu-id="26153-111">You can specify the target namespace URI as an optional argument to XMLSCHEMA in FOR XML.</span></span> <span data-ttu-id="26153-112">これにより、スキーマに指定した対象名前空間が返されます。</span><span class="sxs-lookup"><span data-stu-id="26153-112">This returns the specified target namespace in the schema.</span></span> <span data-ttu-id="26153-113">この対象名前空間はクエリを何回実行しても変わりません。</span><span class="sxs-lookup"><span data-stu-id="26153-113">This target namespace remains the same every time you execute the query.</span></span> <span data-ttu-id="26153-114">たとえば、上記のクエリを変更した次のクエリには、名前空間 URI である `'urn:example.com'`が引数として含まれています。</span><span class="sxs-lookup"><span data-stu-id="26153-114">For example, the following modified version of the previous query includes the namespace URI, `'urn:example.com'`, as an argument.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID, Name  
FROM Production.ProductModel  
WHERE ProductModelID=122 or ProductModelID=119  
FOR XML RAW, XMLSCHEMA ('urn:example.com')  
GO  
```  
  
 <span data-ttu-id="26153-115">結果を次に示します。</span><span class="sxs-lookup"><span data-stu-id="26153-115">This is the result:</span></span>  
  
```  
<xsd:schema targetNamespace="urn:example.com" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:sqltypes="https://schemas.microsoft.com/sqlserver/2004/sqltypes" elementFormDefault="qualified">  
  <xsd:import namespace="https://schemas.microsoft.com/sqlserver/2004/sqltypes" schemaLocation="https://schemas.microsoft.com/sqlserver/2004/sqltypes/sqltypes.xsd" />  
  <xsd:element name="row">  
    <xsd:complexType>  
      <xsd:attribute name="ProductModelID" type="sqltypes:int" use="required" />  
      <xsd:attribute name="Name" use="required">  
        <xsd:simpleType sqltypes:sqlTypeAlias="[AdventureWorks].[dbo].[Name]">  
          <xsd:restriction base="sqltypes:nvarchar" sqltypes:localeId="1033" sqltypes:sqlCompareOptions="IgnoreCase IgnoreKanaType IgnoreWidth" sqltypes:sqlSortId="52">  
            <xsd:maxLength value="50" />  
          </xsd:restriction>  
        </xsd:simpleType>  
      </xsd:attribute>  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
<row xmlns="urn:example.com" ProductModelID="122" Name="All-Purpose Bike Stand" />  
<row xmlns="urn:example.com" ProductModelID="119" Name="Bike Wash" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="26153-116">参照</span><span class="sxs-lookup"><span data-stu-id="26153-116">See Also</span></span>  
 [<span data-ttu-id="26153-117">FOR XML での RAW モードの使用</span><span class="sxs-lookup"><span data-stu-id="26153-117">Use RAW Mode with FOR XML</span></span>](use-raw-mode-with-for-xml.md)  
  
  
