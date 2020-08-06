---
title: 入れ子になった FOR XML クエリを使用した XML の構造化 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- FOR XML query
- queries [XML in SQL Server], nested FOR XML
- XML [SQL Server], FOR XML queries
ms.assetid: 8dc42c05-16e8-4b7b-a5d3-550b55acae26
author: rothja
ms.author: jroth
ms.openlocfilehash: 738b5b3ec67dada90c851d284ccc8b3009a51aa7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642639"
---
# <a name="shape-xml-with-nested-for-xml-queries"></a><span data-ttu-id="30032-102">入れ子になった FOR XML クエリを使用した XML の構造化</span><span class="sxs-lookup"><span data-stu-id="30032-102">Shape XML with Nested FOR XML Queries</span></span>
  <span data-ttu-id="30032-103">次の例では、`Production.Product` テーブルにクエリを実行し、特定の製品の `ListPrice` 値と `StandardCost` 値を取得します。</span><span class="sxs-lookup"><span data-stu-id="30032-103">The following example queries the `Production.Product` table to retrieve the `ListPrice` and `StandardCost` values of a specific product.</span></span> <span data-ttu-id="30032-104">ここでは、例示を目的として、両方の価格を <`Price`> 要素に返します。各 <`Price`> 要素には、`PriceType` 属性があります。</span><span class="sxs-lookup"><span data-stu-id="30032-104">To make the query interesting, both prices are returned in a <`Price`> element, and each <`Price`> element has a `PriceType` attribute.</span></span>  
  
## <a name="example"></a><span data-ttu-id="30032-105">例</span><span class="sxs-lookup"><span data-stu-id="30032-105">Example</span></span>  
 <span data-ttu-id="30032-106">次に、想定する XML の構造を示します。</span><span class="sxs-lookup"><span data-stu-id="30032-106">This is the expected shape of the XML:</span></span>  
  
```  
<xsd:schema xmlns:schema="urn:schemas-microsoft-com:sql:SqlRowSet2" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:sqltypes="https://schemas.microsoft.com/sqlserver/2004/sqltypes" targetNamespace="urn:schemas-microsoft-com:sql:SqlRowSet2" elementFormDefault="qualified">  
  <xsd:import namespace="https://schemas.microsoft.com/sqlserver/2004/sqltypes" schemaLocation="https://schemas.microsoft.com/sqlserver/2004/sqltypes/sqltypes.xsd" />  
  <xsd:element name="Production.Product" type="xsd:anyType" />  
</xsd:schema>  
<Production.Product xmlns="urn:schemas-microsoft-com:sql:SqlRowSet2" ProductID="520">  
  <Price xmlns="" PriceType="ListPrice">133.34</Price>  
  <Price xmlns="" PriceType="StandardCost">98.77</Price>  
</Production.Product>  
```  
  
 <span data-ttu-id="30032-107">次に、入れ子になった FOR XML クエリを示します。</span><span class="sxs-lookup"><span data-stu-id="30032-107">This is the nested FOR XML query:</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT Product.ProductID,   
          (SELECT 'ListPrice' as PriceType,   
                   CAST(CAST(ListPrice as NVARCHAR(40)) as XML)   
           FROM    Production.Product Price   
           WHERE   Price.ProductID=Product.ProductID   
           FOR XML AUTO, TYPE),  
          (SELECT  'StandardCost' as PriceType,   
                   CAST(CAST(StandardCost as NVARCHAR(40)) as XML)   
           FROM    Production.Product Price   
           WHERE   Price.ProductID=Product.ProductID   
           FOR XML AUTO, TYPE)  
FROM Production.Product  
WHERE ProductID=520  
for XML AUTO, TYPE, XMLSCHEMA  
```  
  
 <span data-ttu-id="30032-108">上のクエリに関して、次の点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="30032-108">Note the following from the previous query:</span></span>  
  
-   <span data-ttu-id="30032-109">外側の SELECT ステートメントで <`Product`> 要素が構築されます。この要素には **ProductID** 属性と 2 つの <`Price`> 子要素があります。</span><span class="sxs-lookup"><span data-stu-id="30032-109">The outer SELECT statement constructs the <`Product`> element that has a **ProductID** attribute and two <`Price`> child elements.</span></span>  
  
-   <span data-ttu-id="30032-110">2 つの内側の SELECT ステートメントで <`Price`> 要素が 2 つ構築されます。各要素には **PriceType** 属性と製品価格を返す XML があります。</span><span class="sxs-lookup"><span data-stu-id="30032-110">The two inner SELECT statements construct two <`Price`> elements, each with a **PriceType** attribute and XML that returns the product price.</span></span>  
  
-   <span data-ttu-id="30032-111">外側の SELECT ステートメントの XMLSCHEMA ディレクティブで、結果の XML の構造を記述するインライン XSD スキーマが生成されます。</span><span class="sxs-lookup"><span data-stu-id="30032-111">The XMLSCHEMA directive in the outer SELECT statement generates the inline XSD schema that describes the shape of the resulting XML.</span></span>  
  
 <span data-ttu-id="30032-112">サンプルとして効果の高いクエリにするには、次のクエリに示すように、FOR XML クエリを記述し、その結果に対して XQuery を記述して、XML の構造を変更します。</span><span class="sxs-lookup"><span data-stu-id="30032-112">To make the query interesting, you can write the FOR XML query and then write an XQuery against the result to reshape the XML, as shown in the following query:</span></span>  
  
```  
SELECT ProductID,   
 ( SELECT p2.ListPrice, p2.StandardCost  
   FROM Production.Product p2   
   WHERE Product.ProductID = p2.ProductID  
   FOR XML AUTO, ELEMENTS XSINIL, type ).query('  
                                   for $p in /p2/*  
                                   return   
                                    <Price PriceType = "{local-name($p)}">  
                                     { data($p) }  
                                    </Price>  
                                  ')  
FROM Production.Product  
WHERE ProductID = 520  
FOR XML AUTO, TYPE  
```  
  
 <span data-ttu-id="30032-113">上の例では `query()` データ型の `xml` メソッドを使用し、内側の FOR XML クエリで返される XML に対してクエリを実行し、必要な結果を構築しています。</span><span class="sxs-lookup"><span data-stu-id="30032-113">The previous example uses the `query()` method of the `xml` data type to query the XML returned by the inner FOR XML query and construct the expected result.</span></span>  
  
 <span data-ttu-id="30032-114">結果を次に示します。</span><span class="sxs-lookup"><span data-stu-id="30032-114">This is the result:</span></span>  
  
```  
<Production.Product ProductID="520">  
  <Price PriceType="ListPrice">133.3400</Price>  
  <Price PriceType="StandardCost">98.7700</Price>  
</Production.Product>  
```  
  
## <a name="see-also"></a><span data-ttu-id="30032-115">参照</span><span class="sxs-lookup"><span data-stu-id="30032-115">See Also</span></span>  
 [<span data-ttu-id="30032-116">入れ子になった FOR XML クエリの使用</span><span class="sxs-lookup"><span data-stu-id="30032-116">Use Nested FOR XML Queries</span></span>](use-nested-for-xml-queries.md)  
  
  
