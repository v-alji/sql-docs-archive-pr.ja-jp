---
title: 入れ子になった FOR XML クエリの使用 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- FOR XML clause, nested FOR XML queries
- queries [XML in SQL Server], nested FOR XML
- nested FOR XML queries
ms.assetid: 7604161a-a958-446d-b102-7dee432979d0
author: rothja
ms.author: jroth
ms.openlocfilehash: 60c4198697f8d19c9b2e5bc1b415e0787861d40a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738058"
---
# <a name="use-nested-for-xml-queries"></a><span data-ttu-id="45efd-102">入れ子になった FOR XML クエリの使用</span><span class="sxs-lookup"><span data-stu-id="45efd-102">Use Nested FOR XML Queries</span></span>
  <span data-ttu-id="45efd-103">`xml`データ型と[for xml クエリの type ディレクティブ](type-directive-in-for-xml-queries.md)を使用すると、for xml クエリによって返された xml を、サーバーとクライアントの両方で処理できます。</span><span class="sxs-lookup"><span data-stu-id="45efd-103">The `xml` data type and the [TYPE directive in FOR XML queries](type-directive-in-for-xml-queries.md) enable the XML returned by the FOR XML queries to be processed on the server as well as on the client.</span></span>  
  
## <a name="processing-with-xml-type-variables"></a><span data-ttu-id="45efd-104">xml 型の変数を使用した処理</span><span class="sxs-lookup"><span data-stu-id="45efd-104">Processing with xml Type Variables</span></span>  
 <span data-ttu-id="45efd-105">FOR XML クエリの結果を `xml` 型の変数に代入できます。また、XQuery を使用して結果にクエリを実行し、その結果を `xml` 型の変数に代入してからさらに処理を加えることができます。</span><span class="sxs-lookup"><span data-stu-id="45efd-105">You can assign the FOR XML query result to an `xml` type variable, or use XQuery to query the result, and assign that result to an `xml` type variable for more processing.</span></span>  
  
```  
DECLARE @x xml  
SET @x=(SELECT ProductModelID, Name  
        FROM Production.ProductModel  
        WHERE ProductModelID=122 or ProductModelID=119  
        FOR XML RAW, TYPE)  
SELECT @x  
-- Result  
--<row ProductModelID="122" Name="All-Purpose Bike Stand" />  
--<row ProductModelID="119" Name="Bike Wash" />  
```  
  
 <span data-ttu-id="45efd-106">いずれかの `xml` データ型メソッドを使用して、変数 `@x` に返された XML にさらに処理を加えることができます。</span><span class="sxs-lookup"><span data-stu-id="45efd-106">You can additionally process the XML returned in the variable, `@x`, by using one of the `xml` data type methods.</span></span> <span data-ttu-id="45efd-107">たとえば、 `ProductModelID` value() メソッド [を使用して、](/sql/t-sql/xml/value-method-xml-data-type)属性の値を取得できます。</span><span class="sxs-lookup"><span data-stu-id="45efd-107">For example, you can retrieve the `ProductModelID` attribute value by using the [value() method](/sql/t-sql/xml/value-method-xml-data-type).</span></span>  
  
```  
DECLARE @i int;  
SET @i = (SELECT @x.value('/row[1]/@ProductModelID[1]', 'int'));  
SELECT @i;  
```  
  
 <span data-ttu-id="45efd-108">次の例では、`FOR XML` 句に `TYPE` ディレクティブが指定されているので、`FOR XML` クエリの結果が `xml` 型で返されます。</span><span class="sxs-lookup"><span data-stu-id="45efd-108">In the following example, the `FOR XML` query result is returned as an `xml` type, because the `TYPE` directive is specified in the `FOR XML` clause.</span></span>  
  
```  
SELECT ProductModelID, Name  
FROM Production.ProductModel  
WHERE ProductModelID=119 or ProductModelID=122  
FOR XML RAW, TYPE,ROOT('myRoot');  
  
```  
  
 <span data-ttu-id="45efd-109">結果を次に示します。</span><span class="sxs-lookup"><span data-stu-id="45efd-109">This is the result:</span></span>  
  
```  
<myRoot>  
  <row ProductModelID="122" Name="All-Purpose Bike Stand" />  
  <row ProductModelID="119" Name="Bike Wash" />  
</myRoot>  
```  
  
 <span data-ttu-id="45efd-110">結果は `xml` 型なので、次のクエリのように、この XML に対していずれかの `xml` データ型メソッドを直接指定することができます。</span><span class="sxs-lookup"><span data-stu-id="45efd-110">Because the result is of `xml` type, you can specify one of the `xml` data type methods directly against this XML, as shown in the following query.</span></span> <span data-ttu-id="45efd-111">クエリでは、[query() メソッド (xml データ型)](/sql/t-sql/xml/query-method-xml-data-type) が使用され、<`row`> 要素の最初の <`myRoot`> 子要素が取得されます。</span><span class="sxs-lookup"><span data-stu-id="45efd-111">In the query, the [query() method (xml Data Type)](/sql/t-sql/xml/query-method-xml-data-type) is used to retrieve the first <`row`> element child of the <`myRoot`> element.</span></span>  
  
```  
SELECT  (SELECT ProductModelID, Name  
         FROM Production.ProductModel  
         WHERE ProductModelID=119 or ProductModelID=122  
         FOR XML RAW, TYPE,ROOT('myRoot')).query('/myRoot[1]/row[1]');  
  
```  
  
 <span data-ttu-id="45efd-112">結果を次に示します。</span><span class="sxs-lookup"><span data-stu-id="45efd-112">This is the result:</span></span>  
  
```  
<row ProductModelID="122" Name="All-Purpose Bike Stand" />  
```  
  
## <a name="returning-inner-for-xml-query-results-to-outer-queries-as-xml-type-instances"></a><span data-ttu-id="45efd-113">内側の FOR XML クエリの結果を外側のクエリに xml 型インスタンスとして返す</span><span class="sxs-lookup"><span data-stu-id="45efd-113">Returning Inner FOR XML Query Results to Outer Queries as xml Type Instances</span></span>  
 <span data-ttu-id="45efd-114">入れ子構造の `FOR XML` クエリを記述して、内側のクエリの結果を `xml` 型で外側のクエリに返すことができます。</span><span class="sxs-lookup"><span data-stu-id="45efd-114">You can write nested `FOR XML` queries where the result of the inner query is returned as an `xml` type to the outer query.</span></span> <span data-ttu-id="45efd-115">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="45efd-115">For example:</span></span>  
  
```  
SELECT Col1,   
       Col2,   
       ( SELECT Col3, Col4   
        FROM  T2  
        WHERE T2.Col = T1.Col  
        ...  
        FOR XML AUTO, TYPE )  
FROM T1  
WHERE ...  
FOR XML AUTO, TYPE;  
```  
  
 <span data-ttu-id="45efd-116">上のクエリに関して、次の点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="45efd-116">Note the following from the previous query:</span></span>  
  
-   <span data-ttu-id="45efd-117">内側の `FOR XML` クエリで生成された XML は、外側の `FOR XML`で生成された XML に追加されます。</span><span class="sxs-lookup"><span data-stu-id="45efd-117">The XML generated by the inner `FOR XML` query is added to the XML generated by the outer `FOR XML`.</span></span>  
  
-   <span data-ttu-id="45efd-118">内側のクエリでは、 `TYPE` ディレクティブが指定されています。</span><span class="sxs-lookup"><span data-stu-id="45efd-118">The inner query specifies the `TYPE` directive.</span></span> <span data-ttu-id="45efd-119">このため、内側のクエリから返される XML データは、`xml` 型になります。</span><span class="sxs-lookup"><span data-stu-id="45efd-119">Therefore, the XML data returned by the inner query is of `xml` type.</span></span> <span data-ttu-id="45efd-120">TYPE ディレクティブを指定しなかった場合、内側の `FOR XML` クエリの結果は `nvarchar(max)` 型として返され、XML データはエンティティ化されます。</span><span class="sxs-lookup"><span data-stu-id="45efd-120">If the TYPE directive is not specified, the result of the inner `FOR XML` query is returned as `nvarchar(max)` and the XML data is entitized.</span></span>  
  
## <a name="controlling-the-shape-of-resulting-xml-data"></a><span data-ttu-id="45efd-121">結果の XML データ構造の制御</span><span class="sxs-lookup"><span data-stu-id="45efd-121">Controlling the Shape of Resulting XML Data</span></span>  
 <span data-ttu-id="45efd-122">入れ子構造の FOR XML クエリを使用すると、結果の XML データ構造の定義を制御しやすくなります。</span><span class="sxs-lookup"><span data-stu-id="45efd-122">Nested FOR XML queries give you more control in defining the shape of the resulting XML data.</span></span> <span data-ttu-id="45efd-123">入れ子構造の FOR XML クエリを使用して、一部が属性中心で、一部が要素中心の XML を作成できます。</span><span class="sxs-lookup"><span data-stu-id="45efd-123">You can use nested FOR XML queries to construct XML that is partly attribute-centric and partly element-centric.</span></span>  
  
 <span data-ttu-id="45efd-124">入れ子構造の FOR XML クエリを使用して属性中心と要素中心の両方の XML を指定する方法の詳細については、「 [FOR XML クエリと入れ子になった FOR XML クエリの比較](../xml/for-xml-query-compared-to-nested-for-xml-query.md) 」および「 [入れ子になった FOR XML クエリを使用した XML の構造化](../xml/shape-xml-with-nested-for-xml-queries.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="45efd-124">For more information about specifying both attribute-centric and element-centric XML with nested FOR XML queries, see [FOR XML Query Compared to Nested FOR XML Query](../xml/for-xml-query-compared-to-nested-for-xml-query.md) and [Shape XML with Nested FOR XML Queries](../xml/shape-xml-with-nested-for-xml-queries.md).</span></span>  
  
 <span data-ttu-id="45efd-125">入れ子構造で AUTO モードの FOR XML クエリを指定することで、兄弟を含む XML 階層を生成できます。</span><span class="sxs-lookup"><span data-stu-id="45efd-125">You can generate XML hierarchies that include siblings by specifying nested AUTO mode FOR XML queries.</span></span> <span data-ttu-id="45efd-126">詳細については、「 [入れ子になった AUTO モードのクエリを使用した兄弟の生成](../xml/generate-siblings-with-a-nested-auto-mode-query.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="45efd-126">For more information, see [Generate Siblings with a Nested AUTO Mode Query](../xml/generate-siblings-with-a-nested-auto-mode-query.md).</span></span>  
  
 <span data-ttu-id="45efd-127">使用するモードに関係なく、入れ子構造の FOR XML クエリを使用すると、結果の XML の構造の定義を制御しやすくなります。</span><span class="sxs-lookup"><span data-stu-id="45efd-127">Regardless of which mode you use, nested FOR XML queries provide more control in describing the shape of the resulting XML.</span></span> <span data-ttu-id="45efd-128">入れ子構造の FOR XML クエリは、EXPLICIT モードのクエリの代わりに使用できます。</span><span class="sxs-lookup"><span data-stu-id="45efd-128">They can be used in the place of EXPLICIT mode queries.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="45efd-129">例</span><span class="sxs-lookup"><span data-stu-id="45efd-129">Examples</span></span>  
 <span data-ttu-id="45efd-130">ここでは、入れ子になった FOR XML クエリの例を紹介します。</span><span class="sxs-lookup"><span data-stu-id="45efd-130">The following topics provide examples of nested FOR XML queries.</span></span>  
  
 [<span data-ttu-id="45efd-131">FOR XML クエリと入れ子になった FOR XML クエリの比較</span><span class="sxs-lookup"><span data-stu-id="45efd-131">FOR XML Query Compared to Nested FOR XML Query</span></span>](../xml/for-xml-query-compared-to-nested-for-xml-query.md)  
 <span data-ttu-id="45efd-132">単一レベルの FOR XML クエリと入れ子になった FOR XML クエリを比較します。</span><span class="sxs-lookup"><span data-stu-id="45efd-132">Compares a single-level FOR XML query to a nested FOR XML query.</span></span> <span data-ttu-id="45efd-133">この例には、属性中心と要素中心の両方の XML をクエリの結果として指定する方法が示されています。</span><span class="sxs-lookup"><span data-stu-id="45efd-133">This example includes a demonstration of how to specify both attribute-centric and element-centric XML as the result of the query.</span></span>  
  
 [<span data-ttu-id="45efd-134">入れ子になった AUTO モードのクエリを使用した兄弟の生成</span><span class="sxs-lookup"><span data-stu-id="45efd-134">Generate Siblings with a Nested AUTO Mode Query</span></span>](../xml/generate-siblings-with-a-nested-auto-mode-query.md)  
 <span data-ttu-id="45efd-135">入れ子構造で AUTO モードのクエリを使用して兄弟を生成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="45efd-135">Shows how to generate siblings by using a nested AUTO mode query</span></span>  
  
 [<span data-ttu-id="45efd-136">ASP.NET における入れ子になった FOR XML クエリの使用</span><span class="sxs-lookup"><span data-stu-id="45efd-136">Use Nested FOR XML Queries in ASP.NET</span></span>](use-nested-for-xml-queries-in-asp-net.md)  
 <span data-ttu-id="45efd-137">ASPX アプリケーションで FOR XML を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]から XML を返す方法を示します。</span><span class="sxs-lookup"><span data-stu-id="45efd-137">Demonstrates how an ASPX application can use FOR XML to return XML from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="45efd-138">入れ子になった FOR XML クエリを使用した XML の構造化</span><span class="sxs-lookup"><span data-stu-id="45efd-138">Shape XML with Nested FOR XML Queries</span></span>](../xml/shape-xml-with-nested-for-xml-queries.md)  
 <span data-ttu-id="45efd-139">入れ子になった FOR XML クエリを使用して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]によって作成される XML ドキュメントの構造を制御する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="45efd-139">Shows how to use nested FOR XML queries to control the structure of an XML document created by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
  
