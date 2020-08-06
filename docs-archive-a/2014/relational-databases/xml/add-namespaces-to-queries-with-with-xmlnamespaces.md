---
title: WITH XMLNAMESPACES を使用したクエリへの名前空間の追加 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- ELEMENTS XSINIL directive
- adding namespaces
- XSINIL directive
- default namespaces
- queries [XML in SQL Server], WITH XMLNAMESPACES clause
- predefined namespaces [XML in SQL Server]
- FOR XML clause, WITH XMLNAMESPACES clause
- namespaces [XML in SQL Server]
- xml data type [SQL Server], WITH XMLNAMESPACES clause
- WITH XMLNAMESPACES clause
ms.assetid: 2189cb5e-4460-46c5-a254-20c833ebbfec
author: rothja
ms.author: jroth
ms.openlocfilehash: ed5d719a845996215fffc18af64401779f848cd0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631707"
---
# <a name="add-namespaces-to-queries-with-with-xmlnamespaces"></a><span data-ttu-id="a601f-102">WITH XMLNAMESPACES を使用したクエリへの名前空間の追加</span><span class="sxs-lookup"><span data-stu-id="a601f-102">Add Namespaces to Queries with WITH XMLNAMESPACES</span></span>
  <span data-ttu-id="a601f-103">[WITH XMLNAMESPACES (Transact-SQL)](/sql/t-sql/xml/with-xmlnamespaces) は、次の方法で名前空間 URI のサポートを提供します。</span><span class="sxs-lookup"><span data-stu-id="a601f-103">[WITH XMLNAMESPACES (Transact-SQL)](/sql/t-sql/xml/with-xmlnamespaces) provides namespace URI support in the following way:</span></span>  
  
-   <span data-ttu-id="a601f-104">[FOR XML クエリを使用した XML の構築](for-xml-sql-server.md) の際に、URI マッピングの名前空間プレフィックスを使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="a601f-104">It makes the namespace prefix to URI mapping available when [Constructing XML Using FOR XML](for-xml-sql-server.md) queries.</span></span>  
  
-   <span data-ttu-id="a601f-105">[xml データ型メソッド](/sql/t-sql/xml/xml-data-type-methods)の静的な名前空間コンテキストに、URI マッピングの名前空間を使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="a601f-105">It makes the namespace to URI mapping available to the static namespace context of the [xml Data Type Methods](/sql/t-sql/xml/xml-data-type-methods).</span></span>  
  
## <a name="using-with-xmlnamespaces-in-the-for-xml-queries"></a><span data-ttu-id="a601f-106">FOR XML クエリでの WITH XMLNAMESPACES の使用</span><span class="sxs-lookup"><span data-stu-id="a601f-106">Using WITH XMLNAMESPACES in the FOR XML Queries</span></span>  
 <span data-ttu-id="a601f-107">WITH XMLNAMESPACES を使用すると、FOR XML クエリに XML 名前空間を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="a601f-107">WITH XMLNAMESPACES lets you include XML namespaces in FOR XML queries.</span></span> <span data-ttu-id="a601f-108">たとえば、次の FOR XML クエリについて考えてみます。</span><span class="sxs-lookup"><span data-stu-id="a601f-108">For example, consider the following FOR XML query:</span></span>  
  
```  
SELECT ProductID, Name, Color  
FROM   Production.Product  
WHERE  ProductID=316 or ProductID=317  
FOR XML RAW  
```  
  
 <span data-ttu-id="a601f-109">結果を次に示します。</span><span class="sxs-lookup"><span data-stu-id="a601f-109">This is the result:</span></span>  
  
```  
<row ProductID="316" Name="Blade" />  
<row ProductID="317" Name="LL Crankarm" Color="Black" />  
  
```  
  
 <span data-ttu-id="a601f-110">FOR XML クエリにより構築された XML に名前空間を追加するには、まず WITH NAMESPACES 句を使用して URI マッピングの名前空間プレフィックスを指定します。</span><span class="sxs-lookup"><span data-stu-id="a601f-110">To add namespaces to the XML constructed by the FOR XML query, first specify the namespace prefix to URI mappings by using the WITH NAMESPACES clause.</span></span> <span data-ttu-id="a601f-111">次に、名前空間プレフィックスを使用して、次に示す変更後のクエリのように、クエリに名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="a601f-111">Then, use the namespace prefixes in specifying the names in the query as shown in the following modified query.</span></span> <span data-ttu-id="a601f-112">WITH XMLNAMESPACES 句で URI (`ns1`) マッピングの名前空間プレフィックス (`uri`) を指定していることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="a601f-112">Note that the WITH XMLNAMESPACES clause specifies the namespace prefix (`ns1`) to URI (`uri`) mapping.</span></span> <span data-ttu-id="a601f-113">FOR XML クエリにより構築された要素名と属性名を指定する際に `ns1` プレフィックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="a601f-113">The `ns1` prefix is then used in specifying the element and attribute names to be constructed by the FOR XML query.</span></span>  
  
```  
WITH XMLNAMESPACES ('uri' as ns1)  
SELECT ProductID as 'ns1:ProductID',  
       Name      as 'ns1:Name',   
       Color     as 'ns1:Color'  
FROM Production.Product  
WHERE ProductID=316 or ProductID=317  
FOR XML RAW ('ns1:Prod'), ELEMENTS  
  
```  
  
 <span data-ttu-id="a601f-114">結果の XML には、指定した名前空間プレフィックスが含まれています。</span><span class="sxs-lookup"><span data-stu-id="a601f-114">The XML result includes the namespace prefixes:</span></span>  
  
```  
<ns1:Prod xmlns:ns1="uri">  
  <ns1:ProductID>316</ns1:ProductID>  
  <ns1:Name>Blade</ns1:Name>  
</ns1:Prod>  
<ns1:Prod xmlns:ns1="uri">  
  <ns1:ProductID>317</ns1:ProductID>  
  <ns1:Name>LL Crankarm</ns1:Name>  
  <ns1:Color>Black</ns1:Color>  
</ns1:Prod>  
  
```  
  
 <span data-ttu-id="a601f-115">WITH XMLNAMESPACES 句には、次の制約があります。</span><span class="sxs-lookup"><span data-stu-id="a601f-115">The following applies to the WITH XMLNAMESPACES clause:</span></span>  
  
-   <span data-ttu-id="a601f-116">FOR XML クエリの RAW、AUTO、PATH モードしかサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="a601f-116">It is supported only on the RAW, AUTO, and PATH modes of the FOR XML queries.</span></span> <span data-ttu-id="a601f-117">EXPLICIT モードはサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="a601f-117">The EXPLICIT mode is not supported.</span></span>  
  
-   <span data-ttu-id="a601f-118">FOR XML クエリの名前空間プレフィックスおよび **xml** データ型メソッドにしか影響しません。XML パーサーには影響しません。</span><span class="sxs-lookup"><span data-stu-id="a601f-118">It only affects the namespace prefixes of FOR XML queries and the **xml** data type methods, but not the XML parser.</span></span> <span data-ttu-id="a601f-119">たとえば、次のクエリは、XML ドキュメントで myNS プレフィックスの名前空間が宣言されていないため、エラーを返します。</span><span class="sxs-lookup"><span data-stu-id="a601f-119">For example, the following query returns an error, because the XML document has no namespace declaration for the myNS prefix.</span></span>  
  
-   <span data-ttu-id="a601f-120">WITH XMLNAMESPACES 句が使用されている場合、FOR XML の XMLSCHEMA ディレクティブおよび XMLDATA ディレクティブは使用できません。</span><span class="sxs-lookup"><span data-stu-id="a601f-120">The FOR XML directives, XMLSCHEMA and XMLDATA cannot be used when a WITH XMLNAMESPACES clause is being used.</span></span>  
  
    ```  
    CREATE TABLE T (x xml)  
    go  
    WITH XMLNAMESPACES ('http://abc' as myNS )  
    INSERT INTO T VALUES('<myNS:root/>')  
    ```  
  
## <a name="using-the-xsinil-directive"></a><span data-ttu-id="a601f-121">XSINIL ディレクティブの使用</span><span class="sxs-lookup"><span data-stu-id="a601f-121">Using the XSINIL Directive</span></span>  
 <span data-ttu-id="a601f-122">ELEMENTS XSINIL ディレクティブを使用している場合は、WITH XMLNAMESPACES 句に xsi プレフィックスは定義できません。</span><span class="sxs-lookup"><span data-stu-id="a601f-122">You cannot define the xsi prefix in the WITH XMLNAMESPACES clause if you are using the ELEMENTS XSINIL directive.</span></span> <span data-ttu-id="a601f-123">代わりに、ELEMENTS XSINIL を使用すると、自動的に xsi プレフィックスが追加されます。</span><span class="sxs-lookup"><span data-stu-id="a601f-123">Instead, it is added automatically when you use ELEMENTS XSINIL.</span></span> <span data-ttu-id="a601f-124">次のクエリは、要素中心型の XML を生成する ELEMENTS XSINIL を使用しています。生成された XML では、NULL 値が **xsi:nil** 属性が True に設定されている要素にマップされます。</span><span class="sxs-lookup"><span data-stu-id="a601f-124">The following query uses ELEMENTS XSINIL that generates element-centric XML where null values are mapped to elements that have the **xsi:nil** attribute set to True.</span></span>  
  
```  
WITH XMLNAMESPACES ('uri' as ns1)  
SELECT ProductID as 'ns1:ProductID',  
       Name      as 'ns1:Name',   
       Color     as 'ns1:Color'  
FROM Production.Product  
WHERE ProductID=316   
FOR XML RAW, ELEMENTS XSINIL  
```  
  
 <span data-ttu-id="a601f-125">結果を次に示します。</span><span class="sxs-lookup"><span data-stu-id="a601f-125">This is the result:</span></span>  
  
```  
<row xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:ns1="uri">  
  <ns1:ProductID>316</ns1:ProductID>  
  <ns1:Name>Blade</ns1:Name>  
  <ns1:Color xsi:nil="true" />  
</row>  
```  
  
## <a name="specifying-default-namespaces"></a><span data-ttu-id="a601f-126">既定の名前空間の指定</span><span class="sxs-lookup"><span data-stu-id="a601f-126">Specifying Default Namespaces</span></span>  
 <span data-ttu-id="a601f-127">名前空間プレフィックスを宣言する代わりに、DEFAULT キーワードを使用して既定の名前空間を宣言することもできます。</span><span class="sxs-lookup"><span data-stu-id="a601f-127">Instead of declaring a namespace prefix, you can declare a default namespace by using a DEFAULT keyword.</span></span> <span data-ttu-id="a601f-128">DEFAULT キーワードは、FOR XML クエリ中で、既定の名前空間を結果の XML の XML ノードにバインドします。</span><span class="sxs-lookup"><span data-stu-id="a601f-128">In the FOR XML query, it will bind the default namespace to XML nodes in the resulting XML.</span></span> <span data-ttu-id="a601f-129">次の例では、WITH XMLNAMESPACES によって、2 つの名前空間プレフィックスを同時に 1 つの既定の名前空間に定義しています。</span><span class="sxs-lookup"><span data-stu-id="a601f-129">In the following example, the WITH XMLNAMESPACES defines two namespace prefixes that are defined together with a default namespace.</span></span>  
  
```  
WITH XMLNAMESPACES ('uri1' as ns1,   
                    'uri2' as ns2,  
                    DEFAULT 'uri2')  
SELECT ProductID,   
      Name,  
      Color  
FROM Production.Product   
WHERE ProductID=316 or ProductID=317  
FOR XML RAW ('ns1:Product'), ROOT('ns2:root'), ELEMENTS  
```  
  
 <span data-ttu-id="a601f-130">この FOR XML クエリは、要素中心の XML を生成します。</span><span class="sxs-lookup"><span data-stu-id="a601f-130">The FOR XML query generates element-centric XML.</span></span> <span data-ttu-id="a601f-131">このクエリでは、どちらの名前空間プレフィックスもノードの命名に使用されていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="a601f-131">Note that the query uses both the namespace prefixes in naming nodes.</span></span> <span data-ttu-id="a601f-132">SELECT 句内では、ProductID、Name、Color のいずれもプレフィックスを使った名前を指定していません。</span><span class="sxs-lookup"><span data-stu-id="a601f-132">In the SELECT clause, the ProductID, Name, and Color do not specify a name with any prefix.</span></span> <span data-ttu-id="a601f-133">その結果、結果の XML の対応する要素は、既定の名前空間に属することになります。</span><span class="sxs-lookup"><span data-stu-id="a601f-133">Therefore, the corresponding elements in the resulting XML belong to the default namespace.</span></span>  
  
```  
<ns2:root xmlns="uri2" xmlns:ns2="uri2" xmlns:ns1="uri1">  
  <ns1:Product>  
    <ProductID>316</ProductID>  
    <Name>Blade</Name>  
  </ns1:Product>  
  <ns1:Product>  
    <ProductID>317</ProductID>  
    <Name>LL Crankarm</Name>  
    <Color>Black</Color>  
  </ns1:Product>  
</ns2:root>  
```  
  
 <span data-ttu-id="a601f-134">次のクエリは前のクエリとほぼ同じですが、FOR XML AUTO モードが指定されています。</span><span class="sxs-lookup"><span data-stu-id="a601f-134">The following query is similar to the previous one, except that the FOR XML AUTO mode is specified.</span></span>  
  
```  
WITH XMLNAMESPACES ('uri1' as ns1,  'uri2' as ns2,DEFAULT 'uri2')  
SELECT ProductID,   
      Name,  
      Color  
FROM Production.Product as "ns1:Product"  
WHERE ProductID=316 or ProductID=317  
FOR XML AUTO, ROOT('ns2:root'), ELEMENTS  
```  
  
## <a name="using-predefined-namespaces"></a><span data-ttu-id="a601f-135">事前定義された名前空間の使用</span><span class="sxs-lookup"><span data-stu-id="a601f-135">Using Predefined Namespaces</span></span>  
 <span data-ttu-id="a601f-136">事前定義された名前空間を使用する場合は、ELEMENTS XSINIL 使用時の xml 名前空間と xsi 名前空間を除き、WITH XMLNAMESPACES を使用して名前空間のバインドを明示的に指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a601f-136">When you use predefined namespaces, except the xml namespace and the xsi namespace when ELEMENTS XSINIL is used, you must explicitly specify the namespace binding by using WITH XMLNAMESPACES.</span></span> <span data-ttu-id="a601f-137">次のクエリは、事前定義された名前空間 (`urn:schemas-microsoft-com:xml-sql`) 用に、URI の名前空間プレフィックスのバインドを明示的に定義しています。</span><span class="sxs-lookup"><span data-stu-id="a601f-137">The following query explicitly defines the namespace prefix to URI binding for the predefined namespace (`urn:schemas-microsoft-com:xml-sql`).</span></span>  
  
```  
WITH XMLNAMESPACES ('urn:schemas-microsoft-com:xml-sql' as sql)  
SELECT 'SELECT * FROM Customers FOR XML AUTO, ROOT("a")' AS "sql:query"  
FOR XML PATH('sql:root')  
```  
  
 <span data-ttu-id="a601f-138">結果は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="a601f-138">This is the result.</span></span> <span data-ttu-id="a601f-139">SQLXML では、この XML テンプレートがよく使用されます。</span><span class="sxs-lookup"><span data-stu-id="a601f-139">SQLXML users are familiar with this XML template.</span></span> <span data-ttu-id="a601f-140">詳細については、「 [SQLXML 4.0 のプログラミング概念](../sqlxml/sqlxml-4-0-programming-concepts.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a601f-140">For more information, see [SQLXML 4.0 Programming Concepts](../sqlxml/sqlxml-4-0-programming-concepts.md).</span></span>  
  
```  
<sql:root xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <sql:query>SELECT * FROM Customers FOR XML AUTO, ROOT("a")</sql:query>  
</sql:root>  
```  
  
 <span data-ttu-id="a601f-141">次の PATH モード クエリで示すように、WITH XMLNAMESPACES を使用して明示的に定義せずに使用できる名前空間プレフィックスは xml のみです。</span><span class="sxs-lookup"><span data-stu-id="a601f-141">Only the xml namespace prefix can be used without explicitly defining it in WITH XMLNAMESPACES, as shown in the following PATH mode query.</span></span> <span data-ttu-id="a601f-142">また、プレフィックスが宣言されている場合は、 http://www.w3.org/XML/1998/namespace 名前空間にバインドする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a601f-142">Also, if the prefix is declared, it has to be bound to the namespace http://www.w3.org/XML/1998/namespace.</span></span> <span data-ttu-id="a601f-143">SELECT 句に指定されている名前は、WITH XMLNAMESPACES を使用して明示的に定義されていない xml 名前空間を参照します。</span><span class="sxs-lookup"><span data-stu-id="a601f-143">The names specified in the SELECT clause refer to the xml namespace prefix that is not explicitly defined by using WITH XMLNAMESPACES.</span></span>  
  
```  
SELECT 'en'    as "English/@xml:lang",  
       'food'  as "English",  
       'ger'   as "German/@xml:lang",  
       'Essen' as "German"  
FOR XML PATH ('Translation')  
go  
```  
  
 <span data-ttu-id="a601f-144">@xml:lang 属性は、事前定義された xml 名前空間を使用します。</span><span class="sxs-lookup"><span data-stu-id="a601f-144">The @xml:lang attributes use the predefined xml namespace.</span></span> <span data-ttu-id="a601f-145">XML のバージョン 1.0 では、xml 名前空間のバインドを明示的に宣言する必要がないので、結果には名前空間のバインドの明示的な宣言が含まれません。</span><span class="sxs-lookup"><span data-stu-id="a601f-145">Because XML version 1.0 does not require the explicit declaration of the xml namespace binding, the result will not include an explicit declaration of the namespace binding.</span></span>  
  
 <span data-ttu-id="a601f-146">結果を次に示します。</span><span class="sxs-lookup"><span data-stu-id="a601f-146">This is the result:</span></span>  
  
```  
<Translation>  
  <English xml:lang="en">food</English>  
  <German xml:lang="ger">Essen</German>  
</Translation>  
```  
  
## <a name="using-with-xmlnamespaces-with-the-xml-data-type-methods"></a><span data-ttu-id="a601f-147">xml データ型メソッドでの WITH XMLNAMESPACES の使用</span><span class="sxs-lookup"><span data-stu-id="a601f-147">Using WITH XMLNAMESPACES with the xml Data Type Methods</span></span>  
 <span data-ttu-id="a601f-148">SELECT クエリ ( [modify()](/sql/t-sql/xml/xml-data-type-methods) メソッドを使用している場合は UPDATE クエリ) に指定された **xml データ型メソッド** は、それぞれのプロローグの中で名前空間の宣言を個別に行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="a601f-148">The [xml Data Type Methods](/sql/t-sql/xml/xml-data-type-methods) specified in a SELECT query, or in UPDATE when it is the **modify()** method, all have to repeat the namespace declaration in their prolog.</span></span> <span data-ttu-id="a601f-149">この作業には時間のかかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="a601f-149">This can be time-consuming.</span></span> <span data-ttu-id="a601f-150">たとえば、次のクエリでは、カタログの説明に仕様が含まれる製品モデル ID を取得します。</span><span class="sxs-lookup"><span data-stu-id="a601f-150">For example, the following query retrieves product model IDs whose catalog descriptions do include specification.</span></span> <span data-ttu-id="a601f-151">つまり、<`Specifications`> 要素が含まれます。</span><span class="sxs-lookup"><span data-stu-id="a601f-151">That is, the <`Specifications`> element exists.</span></span>  
  
```  
SELECT ProductModelID, CatalogDescription.query('  
declare namespace pd="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
    <Product   
        ProductModelID= "{ sql:column("ProductModelID") }"   
        />  
') AS Result  
FROM Production.ProductModel  
WHERE CatalogDescription.exist('  
    declare namespace  pd="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
     /pd:ProductDescription[(pd:Specifications)]'  
    ) = 1  
```  
  
 <span data-ttu-id="a601f-152">上記のクエリでは、 **query()** メソッドと **exist()** メソッドのいずれのプロローグでも、同じ名前空間が宣言されています。</span><span class="sxs-lookup"><span data-stu-id="a601f-152">In the previous query, both the **query()** and **exist()** methods declare the same namespace in their prolog.</span></span> <span data-ttu-id="a601f-153">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="a601f-153">For example:</span></span>  
  
```  
declare namespace pd="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
```  
  
 <span data-ttu-id="a601f-154">代わりに、WITH XMLNAMESPACES を最初に宣言して、名前空間プレフィックスをクエリで使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="a601f-154">Alternatively, you can declare WITH XMLNAMESPACES first and use the namespace prefixes in the query.</span></span> <span data-ttu-id="a601f-155">この場合は、 **query()** メソッドと **exist()** メソッドでは、それぞれのプロローグに名前空間の宣言を含める必要はありません。</span><span class="sxs-lookup"><span data-stu-id="a601f-155">In this case, the **query()** and **exist()** methods  do not have to include namespace declarations in their prolog.</span></span>  
  
```  
WITH XMLNAMESPACES ('https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' as pd)  
SELECT ProductModelID, CatalogDescription.query('  
    <Product   
        ProductModelID= "{ sql:column("ProductModelID") }"   
        />  
') AS Result  
FROM Production.ProductModel  
WHERE CatalogDescription.exist('  
     /pd:ProductDescription[(pd:Specifications)]'  
    ) = 1  
Go  
```  
  
 <span data-ttu-id="a601f-156">XQuery プロローグの明示的な宣言が、WITH 句で定義されている名前空間プレフィックスと既定の要素名前空間をオーバーライドしていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="a601f-156">Note that an explicit declaration in the XQuery prolog overrides the namespace prefix and the default element namespace that are defined in the WITH clause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a601f-157">参照</span><span class="sxs-lookup"><span data-stu-id="a601f-157">See Also</span></span>  
 <span data-ttu-id="a601f-158">[xml データ型メソッド](/sql/t-sql/xml/xml-data-type-methods) </span><span class="sxs-lookup"><span data-stu-id="a601f-158">[xml Data Type Methods](/sql/t-sql/xml/xml-data-type-methods) </span></span>  
 <span data-ttu-id="a601f-159">[XQuery 言語リファレンス &#40;SQL Server&#41;](/sql/xquery/xquery-language-reference-sql-server) </span><span class="sxs-lookup"><span data-stu-id="a601f-159">[XQuery Language Reference &#40;SQL Server&#41;](/sql/xquery/xquery-language-reference-sql-server) </span></span>  
 <span data-ttu-id="a601f-160">[WITH XMLNAMESPACES &#40;Transact-SQL&#41;](/sql/t-sql/xml/with-xmlnamespaces) </span><span class="sxs-lookup"><span data-stu-id="a601f-160">[WITH XMLNAMESPACES &#40;Transact-SQL&#41;](/sql/t-sql/xml/with-xmlnamespaces) </span></span>  
 [<span data-ttu-id="a601f-161">FOR XML &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a601f-161">FOR XML &#40;SQL Server&#41;</span></span>](for-xml-sql-server.md)  
  
  
