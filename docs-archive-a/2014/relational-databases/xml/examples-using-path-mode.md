---
title: '例 : PATH モードの使用 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- PATH FOR XML mode, examples
ms.assetid: 3564e13b-9b97-49ef-8cf9-6a78677b09a3
author: rothja
ms.author: jroth
ms.openlocfilehash: 0876d93ffe246b6129a3838f8dbae47f3be7ffaf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743102"
---
# <a name="examples-using-path-mode"></a><span data-ttu-id="c9c23-102">例 :PATH モードの使用</span><span class="sxs-lookup"><span data-stu-id="c9c23-102">Examples: Using PATH Mode</span></span>
  <span data-ttu-id="c9c23-103">次の例では、PATH モードで SELECT クエリから XML を生成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="c9c23-103">The following examples illustrate the use of PATH mode in generating XML from a SELECT query.</span></span> <span data-ttu-id="c9c23-104">これらのクエリの多くは、ProductModel テーブルの Instructions 列に格納されている、自転車製造手順の XML ドキュメントに対して指定されています。</span><span class="sxs-lookup"><span data-stu-id="c9c23-104">Many of these queries are specified against the bicycle manufacturing instructions XML documents that are stored in the Instructions column of the ProductModel table.</span></span>  
  
## <a name="specifying-a-simple-path-mode-query"></a><span data-ttu-id="c9c23-105">PATH モードの単純なクエリの指定</span><span class="sxs-lookup"><span data-stu-id="c9c23-105">Specifying a simple PATH mode query</span></span>  
 <span data-ttu-id="c9c23-106">次のクエリには FOR XML PATH モードが指定されています。</span><span class="sxs-lookup"><span data-stu-id="c9c23-106">This query specifies a FOR XML PATH mode.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT   
       ProductModelID,  
       Name  
FROM Production.ProductModel  
WHERE ProductModelID=122 OR ProductModelID=119  
FOR XML PATH;  
GO  
```  
  
 <span data-ttu-id="c9c23-107">次の結果は、要素中心の XML です。結果の行セットの列値は、それぞれ 1 つの要素に格納されています。</span><span class="sxs-lookup"><span data-stu-id="c9c23-107">The following result is element-centric XML where each column value in the resulting rowset is wrapped in an element.</span></span> <span data-ttu-id="c9c23-108">`SELECT` 句に列の別名が指定されていないので、生成される子要素の名前は `SELECT` 句の対応する列名と同じになっています。</span><span class="sxs-lookup"><span data-stu-id="c9c23-108">Because the `SELECT` clause does not specify any aliases for the column names, the child element names generated are the same as the corresponding column names in the `SELECT` clause.</span></span> <span data-ttu-id="c9c23-109">行セットの各行には <`row`> タグが追加されます。</span><span class="sxs-lookup"><span data-stu-id="c9c23-109">For each row in the rowset a <`row`> tag is added.</span></span>  
  
 `<row>`  
  
 `<ProductModelID>122</ProductModelID>`  
  
 `<Name>All-Purpose Bike Stand</Name>`  
  
 `</row>`  
  
 `<row>`  
  
 `<ProductModelID>119</ProductModelID>`  
  
 `<Name>Bike Wash</Name>`  
  
 `</row>`  
  
 <span data-ttu-id="c9c23-110">次の結果は、 `RAW` オプションを指定した `ELEMENTS` モードのクエリと同じです。</span><span class="sxs-lookup"><span data-stu-id="c9c23-110">The following result is the same as the `RAW` mode query with the `ELEMENTS` option specified.</span></span> <span data-ttu-id="c9c23-111">返される結果は、結果セットの各行に既定の <`row`> 要素が追加された要素中心の XML です。</span><span class="sxs-lookup"><span data-stu-id="c9c23-111">It returns element-centric XML with a default <`row`> element for each row in the result set.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID,  
       Name  
FROM Production.ProductModel  
WHERE ProductModelID=122 OR ProductModelID=119  
FOR XML RAW, ELEMENTS;  
```  
  
 <span data-ttu-id="c9c23-112">必要に応じて、行要素の名前を指定して既定の <`row`> を上書きできます。</span><span class="sxs-lookup"><span data-stu-id="c9c23-112">You can optionally specify the row element name to overwrite the default <`row`>.</span></span> <span data-ttu-id="c9c23-113">たとえば、次のクエリは行セットの行ごとに <`ProductModel`> 要素を返します。</span><span class="sxs-lookup"><span data-stu-id="c9c23-113">For example, the following query returns the <`ProductModel`> element for each row in the rowset.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID,  
       Name  
FROM Production.ProductModel  
WHERE ProductModelID=122 or ProductModelID=119  
FOR XML PATH ('ProductModel');  
GO  
```  
  
 <span data-ttu-id="c9c23-114">結果の XML には指定した行要素名が使用されます。</span><span class="sxs-lookup"><span data-stu-id="c9c23-114">The resulting XML will have a specified row element name.</span></span>  
  
 `<ProductModel>`  
  
 `<ProductModelID>122</ProductModelID>`  
  
 `<Name>All-Purpose Bike Stand</Name>`  
  
 `</ProductModel>`  
  
 `<ProductModel>`  
  
 `<ProductModelID>119</ProductModelID>`  
  
 `<Name>Bike Wash</Name>`  
  
 `</ProductModel>`  
  
 <span data-ttu-id="c9c23-115">長さがゼロの文字列を指定すると、囲み要素は生成されません。</span><span class="sxs-lookup"><span data-stu-id="c9c23-115">If you specify a zero-length string, the wrapping element is not produced.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID,  
       Name  
FROM Production.ProductModel  
WHERE ProductModelID=122 OR ProductModelID=119  
FOR XML PATH ('');  
GO  
```  
  
 <span data-ttu-id="c9c23-116">結果を次に示します。</span><span class="sxs-lookup"><span data-stu-id="c9c23-116">This is the result:</span></span>  
  
 `<ProductModelID>122</ProductModelID>`  
  
 `<Name>All-Purpose Bike Stand</Name>`  
  
 `<ProductModelID>119</ProductModelID>`  
  
 `<Name>Bike Wash</Name>`  
  
## <a name="specifying-xpath-like-column-names"></a><span data-ttu-id="c9c23-117">XPath 形式の列名の指定</span><span class="sxs-lookup"><span data-stu-id="c9c23-117">Specifying XPath-like column names</span></span>  
 <span data-ttu-id="c9c23-118">次のクエリでは、`ProductModelID` 列に指定した名前が '\@' で始まり、スラッシュ ('/') を含んでいません。</span><span class="sxs-lookup"><span data-stu-id="c9c23-118">In the following query the `ProductModelID` column name specified starts with '\@' and does not contain a slash mark ('/').</span></span> <span data-ttu-id="c9c23-119">したがって、結果の XML では、<`row`> 要素の属性が生成され、対応する列値が設定されます。</span><span class="sxs-lookup"><span data-stu-id="c9c23-119">Therefore, an attribute of the <`row`> element that has the corresponding column value is created in the resulting XML.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID AS "@id",  
       Name  
FROM Production.ProductModel  
WHERE ProductModelID=122 OR ProductModelID=119  
FOR XML PATH ('ProductModelData');  
GO  
```  
  
 <span data-ttu-id="c9c23-120">結果を次に示します。</span><span class="sxs-lookup"><span data-stu-id="c9c23-120">This is the result:</span></span>  
  
 `< ProductModelData id="122">`  
  
 `<Name>All-Purpose Bike Stand</Name>`  
  
 `</ ProductModelData >`  
  
 `< ProductModelData id="119">`  
  
 `<Name>Bike Wash</Name>`  
  
 `</ ProductModelData >`  
  
 <span data-ttu-id="c9c23-121">`root` で `FOR XML`オプションを指定すると、単一の最上位要素を追加できます。</span><span class="sxs-lookup"><span data-stu-id="c9c23-121">You can add a single top-level element by specifying the `root` option in `FOR XML`.</span></span>  
  
```  
SELECT ProductModelID AS "@id",  
       Name  
FROM Production.ProductModel  
WHERE ProductModelID=122 or ProductModelID=119  
FOR XML PATH ('ProductModelData'), root ('Root');  
GO  
```  
  
 <span data-ttu-id="c9c23-122">階層を生成するには、PATH 形式の構文を使用できます。</span><span class="sxs-lookup"><span data-stu-id="c9c23-122">To generate a hierarchy, you can include PATH-like syntax.</span></span> <span data-ttu-id="c9c23-123">たとえば、 `Name` 列の列名を "SomeChild/ModelName" に変更すると、次に示すように階層を伴う XML が返されます。</span><span class="sxs-lookup"><span data-stu-id="c9c23-123">For example, change the column name for the `Name` column to "SomeChild/ModelName" and you will obtain XML with hierarchy, as shown in this result:</span></span>  
  
 `<Root>`  
  
 `<ProductModelData id="122">`  
  
 `<SomeChild>`  
  
 `<ModelName>All-Purpose Bike Stand</ModelName>`  
  
 `</SomeChild>`  
  
 `</ProductModelData>`  
  
 `<ProductModelData id="119">`  
  
 `<SomeChild>`  
  
 `<ModelName>Bike Wash</ModelName>`  
  
 `</SomeChild>`  
  
 `</ProductModelData>`  
  
 `</Root>`  
  
 <span data-ttu-id="c9c23-124">次のクエリは、指定した製品モデルの ID および名前以外に、その製品モデルに対応する製造手順書の場所を返します。</span><span class="sxs-lookup"><span data-stu-id="c9c23-124">Besides the product model ID and name, the following query retrieves the manufacturing instruction locations for the product model.</span></span> <span data-ttu-id="c9c23-125">Instructions 列が `xml` 型なので、`query()` データ型の `xml` メソッドを指定して場所を取得します。</span><span class="sxs-lookup"><span data-stu-id="c9c23-125">Because the Instructions column is of `xml` type, the `query()` method of `xml` data type is specified to retrieve the location.</span></span>  
  
```  
SELECT ProductModelID AS "@id",  
       Name,  
       Instructions.query('declare namespace MI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
                /MI:root/MI:Location   
              ') AS ManuInstr  
FROM Production.ProductModel  
WHERE ProductModelID = 7  
FOR XML PATH ('ProductModelData'), root ('Root');  
GO  
```  
  
 <span data-ttu-id="c9c23-126">次に結果の一部を示します。</span><span class="sxs-lookup"><span data-stu-id="c9c23-126">This is the partial result.</span></span> <span data-ttu-id="c9c23-127">クエリでは列名として ManuInstr が指定されているため、メソッドによって返される XML `query()` は、 `ManuInstr` 次に示すように <> タグでラップされます。</span><span class="sxs-lookup"><span data-stu-id="c9c23-127">Because the query specifies ManuInstr as the column name, the XML returned by the `query()` method is wrapped in a <`ManuInstr`> tag as shown in the following:</span></span>  
  
 `<Root>`  
  
 `<ProductModelData id="7">`  
  
 `<Name>HL Touring Frame</Name>`  
  
 `<ManuInstr>`  
  
 `<MI:Location xmlns:MI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions"`  
  
 `<MI:step>...</MI:step>...`  
  
 `</MI:Location>`  
  
 `...`  
  
 `</ManuInstr>`  
  
 `</ProductModelData>`  
  
 `</Root>`  
  
 <span data-ttu-id="c9c23-128">上記の FOR XML クエリで、<`Root`> 要素と <`ProductModelData`> 要素に対応する名前空間を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="c9c23-128">In the previous FOR XML query, you may want to include namespaces for the <`Root`> and <`ProductModelData`> elements.</span></span> <span data-ttu-id="c9c23-129">そのためには、WITH XMLNAMESPACES で名前空間のバインドのためのプレフィックスを定義しておき、FOR XML クエリで使用します。</span><span class="sxs-lookup"><span data-stu-id="c9c23-129">You can do this by first defining the prefix to namespace binding by using WITH XMLNAMESPACES and using prefixes in the FOR XML query.</span></span> <span data-ttu-id="c9c23-130">詳細については、「 [WITH XMLNAMESPACES を使用したクエリへの名前空間の追加](add-namespaces-to-queries-with-with-xmlnamespaces.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c9c23-130">For more information, see [Add Namespaces to Queries with WITH XMLNAMESPACES](add-namespaces-to-queries-with-with-xmlnamespaces.md).</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
WITH XMLNAMESPACES (  
   'uri1' AS ns1,    
   'uri2' AS ns2,  
   'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions' as MI)  
SELECT ProductModelID AS "ns1:ProductModelID",  
       Name           AS "ns1:Name",  
       Instructions.query('  
                /MI:root/MI:Location   
              ')   
FROM Production.ProductModel  
WHERE ProductModelID=7  
FOR XML PATH ('ns2:ProductInfo'), root('ns1:root');  
GO  
```  
  
 <span data-ttu-id="c9c23-131">`MI` では `WITH XMLNAMESPACES`プレフィックスも定義されています。</span><span class="sxs-lookup"><span data-stu-id="c9c23-131">Note that the `MI` prefix is also defined in the `WITH XMLNAMESPACES`.</span></span> <span data-ttu-id="c9c23-132">したがって、指定された `query()` 型の `xml` メソッドにおいて、クエリ プロローグでこのプレフィックスは定義されていません。</span><span class="sxs-lookup"><span data-stu-id="c9c23-132">As a result, the `query()` method of the `xml` type specified does not define the prefix in the query prolog.</span></span> <span data-ttu-id="c9c23-133">結果を次に示します。</span><span class="sxs-lookup"><span data-stu-id="c9c23-133">This is the result:</span></span>  
  
 `<ns1:root xmlns:MI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions" xmlns="uri2" xmlns:ns2="uri2" xmlns:ns1="uri1">`  
  
 `<ns2:ProductInfo>`  
  
 `<ns1:ProductModelID>7</ns1:ProductModelID>`  
  
 `<ns1:Name>HL Touring Frame</ns1:Name>`  
  
 `<MI:Location xmlns:MI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions"`  
  
 `LaborHours="2.5" LotSize="100" MachineHours="3" SetupHours="0.5" LocationID="10" xmlns="">`  
  
 `<MI:step>`  
  
 `Insert <MI:material>aluminum sheet MS-2341</MI:material> into the <MI:tool>T-85A framing tool</MI:tool>.`  
  
 `</MI:step>`  
  
 `...`  
  
 `</MI:Location>`  
  
 `...`  
  
 `</ns2:ProductInfo>`  
  
 `</ns1:root>`  
  
## <a name="generating-a-value-list-using-path-mode"></a><span data-ttu-id="c9c23-134">PATH モードを使用した値リストの生成</span><span class="sxs-lookup"><span data-stu-id="c9c23-134">Generating a value list using PATH mode</span></span>  
 <span data-ttu-id="c9c23-135">次のクエリは、製品モデルごとに製品 ID の値リストを生成します。</span><span class="sxs-lookup"><span data-stu-id="c9c23-135">For each product model, this query constructs a value list of product IDs.</span></span> <span data-ttu-id="c9c23-136">また、次の XML フラグメントで示すように製品 ID ごとに <`ProductName`> 子要素が生成されます。</span><span class="sxs-lookup"><span data-stu-id="c9c23-136">For each product ID, the query also constructs <`ProductName`> nested elements, as shown in this XML fragment:</span></span>  
  
 `<ProductModelData ProductModelID="7" ProductModelName="..."`  
  
 `ProductIDs="product id list in the product model" >`  
  
 `<ProductName>...</ProductName>`  
  
 `<ProductName>...</ProductName>`  
  
 `...`  
  
 `</ProductModelData>`  
  
 <span data-ttu-id="c9c23-137">求める XML を生成するクエリを次に示します。</span><span class="sxs-lookup"><span data-stu-id="c9c23-137">This is the query that produces the XML you want:</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID     AS "@ProductModelID",  
       Name               S "@ProductModelName",  
      (SELECT ProductID AS "data()"  
       FROM   Production.Product  
       WHERE  Production.Product.ProductModelID =   
              Production.ProductModel.ProductModelID  
       FOR XML PATH ('')) S "@ProductIDs",  
       (SELECT Name AS "ProductName"  
       FROM   Production.Product  
       WHERE  Production.Product.ProductModelID =   
              Production.ProductModel.ProductModelID  
        FOR XML PATH ('')) as "ProductNames"  
FROM   Production.ProductModel  
WHERE  ProductModelID= 7 or ProductModelID=9  
FOR XML PATH('ProductModelData');  
```  
  
 <span data-ttu-id="c9c23-138">上のクエリに関して、次の点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="c9c23-138">Note the following from the previous query:</span></span>  
  
-   <span data-ttu-id="c9c23-139">最初の `SELECT` サブクエリは、列名として `data()` を使用することで ProductID の一覧を返しています。</span><span class="sxs-lookup"><span data-stu-id="c9c23-139">The first nested `SELECT` returns a list of ProductIDs by using `data()` as the column name.</span></span> <span data-ttu-id="c9c23-140">`FOR XML PATH`の行要素名として空文字列が指定されているので、要素は生成されません。</span><span class="sxs-lookup"><span data-stu-id="c9c23-140">Because the query specifies an empty string as the row element name in `FOR XML PATH`, no element is generated.</span></span> <span data-ttu-id="c9c23-141">代わりに、値リストが `ProductID` 属性に割り当てられています。</span><span class="sxs-lookup"><span data-stu-id="c9c23-141">Instead, the value list is assigned to the `ProductID` attribute.</span></span>  
  
-   <span data-ttu-id="c9c23-142">2 番目の `SELECT` サブクエリは、該当する製品モデルに含まれる製品名を取得します。</span><span class="sxs-lookup"><span data-stu-id="c9c23-142">The second nested `SELECT` retrieves product names for products in the product model.</span></span> <span data-ttu-id="c9c23-143">列名として `ProductNames` を指定しているので、生成した <`ProductName`> 要素は <`ProductNames`> 要素に囲まれた状態で返しています。</span><span class="sxs-lookup"><span data-stu-id="c9c23-143">It generates <`ProductName`> elements that are returned wrapped in the <`ProductNames`> element, because the query specifies `ProductNames` as the column name.</span></span>  
  
 <span data-ttu-id="c9c23-144">結果の一部を次に示します。</span><span class="sxs-lookup"><span data-stu-id="c9c23-144">This is the partial result:</span></span>  
  
 `<ProductModelData PId="7"`  
  
 `ProductModelName="HL Touring Frame"`  
  
 `ProductIDs="885 887 ...">`  
  
 `<ProductNames>`  
  
 `<ProductName>HL Touring Frame - Yellow, 60</ProductName>`  
  
 `<ProductName>HL Touring Frame - Yellow, 46</ProductName></ProductNames>`  
  
 `...`  
  
 `</ProductModelData>`  
  
 `<ProductModelData PId="9"`  
  
 `ProductModelName="LL Road Frame"`  
  
 `ProductIDs="722 723 724 ...">`  
  
 `<ProductNames>`  
  
 `<ProductName>LL Road Frame - Black, 58</ProductName>`  
  
 `<ProductName>LL Road Frame - Black, 60</ProductName>`  
  
 `<ProductName>LL Road Frame - Black, 62</ProductName>`  
  
 `...`  
  
 `</ProductNames>`  
  
 `</ProductModelData>`  
  
 <span data-ttu-id="c9c23-145">製品名を構成するサブクエリは、結果として返す文字列をエンティティ表記に変換してから XML に追加しています。</span><span class="sxs-lookup"><span data-stu-id="c9c23-145">The subquery constructing the product names returns the result as a string that is entitized and then added to the XML.</span></span> <span data-ttu-id="c9c23-146">TYPE ディレクティブ `FOR XML PATH (''), type` を追加した場合、結果は `xml` 型で返され、エンティティ表記への変換は行われません。</span><span class="sxs-lookup"><span data-stu-id="c9c23-146">If you add the type directive, `FOR XML PATH (''), type`, the subquery returns the result as `xml` type and no entitization occurs.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID AS "@ProductModelID",  
      Name AS "@ProductModelName",  
      (SELECT ProductID AS "data()"  
       FROM   Production.Product  
       WHERE  Production.Product.ProductModelID =   
              Production.ProductModel.ProductModelID  
       FOR XML PATH ('')  
       ) AS "@ProductIDs",  
       (  
       SELECT Name AS "ProductName"  
       FROM   Production.Product  
       WHERE  Production.Product.ProductModelID =   
              Production.ProductModel.ProductModelID  
       FOR XML PATH (''), type  
       ) AS "ProductNames"  
  
FROM Production.ProductModel  
WHERE ProductModelID= 7 OR ProductModelID=9  
FOR XML PATH('ProductModelData');  
```  
  
## <a name="adding-namespaces-in-the-resulting-xml"></a><span data-ttu-id="c9c23-147">結果の XML への名前空間の追加</span><span class="sxs-lookup"><span data-stu-id="c9c23-147">Adding namespaces in the resulting XML</span></span>  
 <span data-ttu-id="c9c23-148">「 [WITH XMLNAMESPACES を使用した名前空間の追加](add-namespaces-to-queries-with-with-xmlnamespaces.md)」で説明したように、WITH XMLNAMESPACES を使用すると PATH モードのクエリに名前空間を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="c9c23-148">As described in [Adding Namespaces Using WITH XMLNAMESPACES](add-namespaces-to-queries-with-with-xmlnamespaces.md), you can use WITH XMLNAMESPACES to include namespaces in the PATH mode queries.</span></span> <span data-ttu-id="c9c23-149">たとえば、SELECT 句で指定する名前に名前空間のプレフィックスを追加できます。</span><span class="sxs-lookup"><span data-stu-id="c9c23-149">For example, names specified in the SELECT clause include namespace prefixes.</span></span> <span data-ttu-id="c9c23-150">次の `PATH` モードのクエリを実行すると、名前空間を伴った XML が生成されます。</span><span class="sxs-lookup"><span data-stu-id="c9c23-150">The following `PATH` mode query constructs XML with namespaces.</span></span>  
  
```  
SELECT 'en'    as "English/@xml:lang",  
       'food'  as "English",  
       'ger'   as "German/@xml:lang",  
       'Essen' as "German"  
FOR XML PATH ('Translation')  
GO  
```  
  
 <span data-ttu-id="c9c23-151"><`English`> 要素に追加されている `@xml:lang` 属性は、定義済みの XML 名前空間で定義されています。</span><span class="sxs-lookup"><span data-stu-id="c9c23-151">The `@xml:lang` attribute added to the <`English`> element is defined in the predefined xml namespace.</span></span>  
  
 <span data-ttu-id="c9c23-152">結果を次に示します。</span><span class="sxs-lookup"><span data-stu-id="c9c23-152">This is the result:</span></span>  
  
 `<Translation>`  
  
 `<English xml:lang="en">food</English>`  
  
 `<German xml:lang="ger">Essen</German>`  
  
 `</Translation>`  
  
 <span data-ttu-id="c9c23-153">次のクエリは例 C と似ていますが、結果の XML に名前空間を含めるために `WITH XMLNAMESPACES` を使用している点が異なります。</span><span class="sxs-lookup"><span data-stu-id="c9c23-153">The following query is similar to example C, except that it uses `WITH XMLNAMESPACES` to include namespaces in the XML result.</span></span> <span data-ttu-id="c9c23-154">詳細については、「 [WITH XMLNAMESPACES を使用したクエリへの名前空間の追加](add-namespaces-to-queries-with-with-xmlnamespaces.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c9c23-154">For more information, see [Add Namespaces to Queries with WITH XMLNAMESPACES](add-namespaces-to-queries-with-with-xmlnamespaces.md).</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
WITH XMLNAMESPACES ('uri1' AS ns1,  DEFAULT 'uri2')  
SELECT ProductModelID AS "@ns1:ProductModelID",  
      Name AS "@ns1:ProductModelName",  
      (SELECT ProductID AS "data()"  
       FROM   Production.Product  
       WHERE  Production.Product.ProductModelID =   
              Production.ProductModel.ProductModelID  
       FOR XML PATH ('')  
       ) AS "@ns1:ProductIDs",  
       (  
       SELECT ProductID AS "@ns1:ProductID",   
              Name AS "@ns1:ProductName"  
       FROM   Production.Product  
       WHERE  Production.Product.ProductModelID =   
              Production.ProductModel.ProductModelID  
       FOR XML PATH , type   
       ) AS "ns1:ProductNames"  
FROM Production.ProductModel  
WHERE ProductModelID= 7 OR ProductModelID=9  
FOR XML PATH('ProductModelData'), root('root');  
```  
  
 <span data-ttu-id="c9c23-155">結果を次に示します。</span><span class="sxs-lookup"><span data-stu-id="c9c23-155">This is the result:</span></span>  
  
 `<root xmlns="uri2" xmlns:ns1="uri1">`  
  
 `<ProductModelData ns1:ProductModelID="7" ns1:ProductModelName="HL Touring Frame" ns1:ProductIDs="885 887 888 889 890 891 892 893">`  
  
 `<ns1:ProductNames>`  
  
 `<row xmlns="uri2" xmlns:ns1="uri1" ns1:ProductID="885" ns1:ProductName="HL Touring Frame - Yellow, 60" />`  
  
 `<row xmlns="uri2" xmlns:ns1="uri1" ns1:ProductID="887" ns1:ProductName="HL Touring Frame - Yellow, 46" />`  
  
 `...`  
  
 `</ns1:ProductNames>`  
  
 `</ProductModelData>`  
  
 `<ProductModelData ns1:ProductModelID="9" ns1:ProductModelName="LL Road Frame" ns1:ProductIDs="722 723 724 725 726 727 728 729 730 736 737 738">`  
  
 `<ns1:ProductNames>`  
  
 `<row xmlns="uri2" xmlns:ns1="uri1" ns1:ProductID="722" ns1:ProductName="LL Road Frame - Black, 58" />`  
  
 `...`  
  
 `</ns1:ProductNames>`  
  
 `</ProductModelData>`  
  
 `</root>`  
  
## <a name="see-also"></a><span data-ttu-id="c9c23-156">参照</span><span class="sxs-lookup"><span data-stu-id="c9c23-156">See Also</span></span>  
 [<span data-ttu-id="c9c23-157">FOR XML での PATH モードの使用</span><span class="sxs-lookup"><span data-stu-id="c9c23-157">Use PATH Mode with FOR XML</span></span>](use-path-mode-with-for-xml.md)  
  
  
