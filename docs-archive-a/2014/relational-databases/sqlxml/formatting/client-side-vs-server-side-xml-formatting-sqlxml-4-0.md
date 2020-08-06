---
title: クライアント側とサーバー側の XML 書式設定 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- NESTED mode
- FOR XML clause, formatting
- client-side XML formatting
- server-side XPath
- server-side XML formatting
- AUTO mode
- client-side XPath
ms.assetid: f807ab7a-c5f8-4e61-9b00-23aebfabc47e
author: rothja
ms.author: jroth
ms.openlocfilehash: fa155fc6d346cb90de54e5599aca1c296623faa7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642674"
---
# <a name="client-side-vs-server-side-xml-formatting-sqlxml-40"></a><span data-ttu-id="30754-102">クライアント側とサーバー側の XML 書式設定 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="30754-102">Client-side vs. Server-side XML Formatting (SQLXML 4.0)</span></span>
  <span data-ttu-id="30754-103">ここでは、SQLXML における、クライアント側とサーバー側の XML 書式設定の一般的な違いについて説明します。</span><span class="sxs-lookup"><span data-stu-id="30754-103">This topic describes the general differences between client-side and server-side XML formatting in SQLXML.</span></span>  
  
## <a name="multiple-rowset-queries-not-supported-in-client-side-formatting"></a><span data-ttu-id="30754-104">クライアント側の書式設定では複数の行セット クエリがサポートされない</span><span class="sxs-lookup"><span data-stu-id="30754-104">Multiple Rowset Queries Not Supported in Client-side Formatting</span></span>  
 <span data-ttu-id="30754-105">複数の行セットを生成するクエリは、クライアント側の XML 書式設定を使用するときにはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="30754-105">Queries that generate multiple rowsets are not supported when you use client-side XML formatting.</span></span> <span data-ttu-id="30754-106">たとえば、クライアント側の書式設定が指定されている仮想ディレクトリがあるとし、</span><span class="sxs-lookup"><span data-stu-id="30754-106">For example, assume you have a virtual directory in which you have client-side formatting specified.</span></span> <span data-ttu-id="30754-107">次のサンプルテンプレートを考えてみましょう。このテンプレートには、ブロックに2つの SELECT ステートメントがあり **\<sql:query>** ます。</span><span class="sxs-lookup"><span data-stu-id="30754-107">Consider this sample template, which has two SELECT statements in a **\<sql:query>** block:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <sql:query>  
     SELECT FirstName FROM Person.Contact FOR XML Nested;   
     SELECT LastName FROM Person.Contact FOR XML Nested    
  </sql:query>  
</ROOT>  
```  
  
 <span data-ttu-id="30754-108">このテンプレートはアプリケーション コードで実行できます。実行すると、クライアント側の XML 書式設定では複数の行セットの書式設定がサポートされていないため、エラーが返されます。</span><span class="sxs-lookup"><span data-stu-id="30754-108">You can execute this template in application code and an error is returned, because client-side XML formatting does not support formatting of multiple rowsets.</span></span> <span data-ttu-id="30754-109">2つの個別のブロックでクエリを指定した場合は、 **\<sql:query>** 目的の結果が得られます。</span><span class="sxs-lookup"><span data-stu-id="30754-109">If you specify the queries in two separate **\<sql:query>** blocks, you will get the desired results.</span></span>  
  
## <a name="timestamp-maps-differently-in-client--vs-server-side-formatting"></a><span data-ttu-id="30754-110">クライアント側とサーバー側の XML 書式設定では timestamp 型のマッピングが異なる</span><span class="sxs-lookup"><span data-stu-id="30754-110">timestamp Maps Differently in Client- vs. Server-side Formatting</span></span>  
 <span data-ttu-id="30754-111">サーバー側の XML 書式設定では、XMLDATA オプションがクエリで指定される場合、`timestamp` 型のデータベース列が i8 XDR 型にマップされます。</span><span class="sxs-lookup"><span data-stu-id="30754-111">In server-side XML formatting, the database column of `timestamp` type maps to the i8 XDR type (when the XMLDATA option is specified in the query).</span></span>  
  
 <span data-ttu-id="30754-112">クライアント側の XML 書式設定では、バイナリの base64 オプションがクエリで指定されているかどうかに従って、`timestamp` 型のデータベース列が `uri` または `bin.base64` XDR 型にマップされます。</span><span class="sxs-lookup"><span data-stu-id="30754-112">In client-side XML formatting, the database column of `timestamp` type maps to either the `uri` or the `bin.base64` XDR type (depending on whether the binary base64 option is specified in the query).</span></span> <span data-ttu-id="30754-113">`bin.base64`この型は型に変換されるため、アップデートグラムと bulkload 機能を使用する場合は、XDR 型が役立ち [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] `timestamp` ます。</span><span class="sxs-lookup"><span data-stu-id="30754-113">The `bin.base64` XDR type is useful if you use the updategram and bulkload features, because this type is converted to the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] `timestamp` type.</span></span> <span data-ttu-id="30754-114">この方法で、挿入、更新、または削除操作が成功します。</span><span class="sxs-lookup"><span data-stu-id="30754-114">This way, the insert, update, or delete operation succeeds.</span></span>  
  
## <a name="deep-variants-are-used-in-server-side-formatting"></a><span data-ttu-id="30754-115">サーバー側の書式設定ではサブタイプの VARIANT 型も使用される</span><span class="sxs-lookup"><span data-stu-id="30754-115">Deep VARIANTs Are Used in Server-side Formatting</span></span>  
 <span data-ttu-id="30754-116">サーバー側の XML 書式設定では、サブタイプの VARIANT 型も使用されます。</span><span class="sxs-lookup"><span data-stu-id="30754-116">In server-side XML formatting, the deep types of a VARIANT type are used.</span></span> <span data-ttu-id="30754-117">クライアント側の XML 書式設定を使用する場合、variant は Unicode 文字列に変換され、サブタイプの VARIANT は使用されません。</span><span class="sxs-lookup"><span data-stu-id="30754-117">If you use client-side XML formatting, the variants are converted to Unicode string, and the subtypes of VARIANT are not used.</span></span>  
  
## <a name="nested-mode-vs-auto-mode"></a><span data-ttu-id="30754-118">NESTED モードと AUTO モード</span><span class="sxs-lookup"><span data-stu-id="30754-118">NESTED Mode vs. AUTO Mode</span></span>  
 <span data-ttu-id="30754-119">クライアント側の FOR XML の NESTED モードは、サーバー側の FOR XML の AUTO モードに似ていますが、次の点が異なります。</span><span class="sxs-lookup"><span data-stu-id="30754-119">The NESTED mode of the client-side FOR XML is similar to the AUTO mode of server-side FOR XML, with the following exceptions:</span></span>  
  
### <a name="when-you-query-views-using-auto-mode-on-the-server-side-the-view-name-is-returned-as-the-element-name-in-the-resulting-xml"></a><span data-ttu-id="30754-120">サーバー側で AUTO モードを使用してビューにクエリを実行すると、ビュー名が結果の XML 内の要素名として返されます。</span><span class="sxs-lookup"><span data-stu-id="30754-120">When you query views using AUTO mode on the server-side, the view name is returned as the element name in the resulting XML.</span></span>  
 <span data-ttu-id="30754-121">たとえば、次のビューが AdventureWorksdatabase の Person テーブルに作成されているとします。</span><span class="sxs-lookup"><span data-stu-id="30754-121">For example, assume that the following view is created on the Person.Contact table in the AdventureWorksdatabase:</span></span>  
  
```  
CREATE VIEW ContactView AS (SELECT ContactID as CID,  
                               FirstName  as FName,  
                               LastName  as LName  
                        FROM Person.Contact)  
```  
  
 <span data-ttu-id="30754-122">次のテンプレートでは、ContactView ビューに対するクエリと、サーバー側の XML 書式設定が指定されています。</span><span class="sxs-lookup"><span data-stu-id="30754-122">The following template specifies a query against the ContactView view, and also specifies server-side XML formatting:</span></span>  
  
```  
 <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <sql:query client-side-xml="0">  
    SELECT *  
    FROM   ContactView  
    FOR XML AUTO  
  </sql:query>  
</ROOT>  
```  
  
 <span data-ttu-id="30754-123">テンプレートを実行すると、次の XML が返されます。</span><span class="sxs-lookup"><span data-stu-id="30754-123">When you execute the template, the following XML is returned.</span></span> <span data-ttu-id="30754-124">(部分的な結果のみが表示されます)。要素名は、クエリの実行対象となるビューの名前であることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="30754-124">(Only partial results are shown.) Note that the element names are the names of the views against which the query is executed.</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <ContactView CID="1" FName="Gustavo" LName="Achong" />   
  <ContactView CID="2" FName="Catherine" LName="Abel" />   
...  
</ROOT>  
```  
  
 <span data-ttu-id="30754-125">クライアント側の書式設定を、対応する NESTED モードで指定すると、ベース テーブル名が結果の XML 内の要素名として返されます。</span><span class="sxs-lookup"><span data-stu-id="30754-125">When you specify client-side XML formatting by using the corresponding NESTED mode, the base table name(s) are returned as the element name(s) in the resulting XML.</span></span> <span data-ttu-id="30754-126">たとえば、次の変更後のテンプレートでは、同じ SELECT ステートメントが実行されますが、XML の書式設定はクライアント側で実行されます (つまり、テンプレートでは、**クライアント側の xml**は true に設定されます)。</span><span class="sxs-lookup"><span data-stu-id="30754-126">For example, the following revised template executes the same SELECT statement, but the XML formatting is performed on the client-side (that is, **client-side-xml** is set to true in the template):</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <sql:query client-side-xml="1">  
    SELECT *  
    FROM   ContactView  
    FOR XML NESTED  
  </sql:query>  
</ROOT>  
```  
  
 <span data-ttu-id="30754-127">このテンプレートを実行すると、次の XML が生成されます。</span><span class="sxs-lookup"><span data-stu-id="30754-127">Executing this template produces the following XML.</span></span> <span data-ttu-id="30754-128">この場合、ベース テーブル名が要素名になっていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="30754-128">Note that the element name is the base table name in this case.</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Person.Contact CID="1" FName="Gustavo" LName="Achong" />   
  <Person.Contact CID="2" FName="Catherine" LName="Abel" />   
...  
</ROOT>  
```  
  
### <a name="when-you-use-auto-mode-of-the-server-side-for-xml-the-table-aliases-specified-in-the-query-are-returned-as-element-names-in-the-resulting-xml"></a><span data-ttu-id="30754-129">サーバー側の FOR XML を AUTO モードで使用すると、クエリで指定されたテーブルの別名が、結果の XML 内の要素名として返されます。</span><span class="sxs-lookup"><span data-stu-id="30754-129">When you use AUTO mode of the server-side FOR XML, the table aliases specified in the query are returned as element names in the resulting XML.</span></span>  
 <span data-ttu-id="30754-130">たとえば、次のテンプレートを考えてみます。</span><span class="sxs-lookup"><span data-stu-id="30754-130">For example, consider this template:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <sql:query client-side-xml="0">  
    SELECT FirstName as fname,  
           LastName as lname  
    FROM   Person.Contact C  
    FOR XML AUTO  
  </sql:query>  
</ROOT>  
```  
  
 <span data-ttu-id="30754-131">このテンプレートを実行すると、次の XML が生成されます。</span><span class="sxs-lookup"><span data-stu-id="30754-131">Executing the template produces the following XML:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <C fname="Gustavo" lname="Achong" />   
  <C fname="Catherine" lname="Abel" />   
...  
</ROOT>   
```  
  
 <span data-ttu-id="30754-132">クライアント側の FOR XML を NESTED モードで使用すると、テーブル名が、結果の XML 内の要素名として返されます。</span><span class="sxs-lookup"><span data-stu-id="30754-132">When you use the NESTED mode of the client-side FOR XML, the table names are returned as element names in the resulting XML.</span></span> <span data-ttu-id="30754-133">(クエリで指定されたテーブルの別名は使用されません)。たとえば、次のテンプレートを考えてみます。</span><span class="sxs-lookup"><span data-stu-id="30754-133">(Table aliases that are specified in the query are not used.) For example, consider this template:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <sql:query client-side-xml="1">  
    SELECT FirstName as fname,  
           LastName as lname  
    FROM   Person.Contact C  
    FOR XML NESTED  
  </sql:query>  
</ROOT>  
```  
  
 <span data-ttu-id="30754-134">このテンプレートを実行すると、次の XML が生成されます。</span><span class="sxs-lookup"><span data-stu-id="30754-134">Executing the template produces the following XML:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Person.Contact fname="Gustavo" lname="Achong" />   
  <Person.Contact fname="Catherine" lname="Abel" />   
...  
</ROOT>  
```  
  
### <a name="if-you-have-a-query-that-returns-columns-as-dbobject-queries-you-cannot-use-aliases-for-these-columns"></a><span data-ttu-id="30754-135">列を dbobject クエリとして返すクエリでは、これらの列に対して別名は使用できません。</span><span class="sxs-lookup"><span data-stu-id="30754-135">If you have a query that returns columns as dbobject queries, you cannot use aliases for these columns.</span></span>  
 <span data-ttu-id="30754-136">たとえば、次のテンプレートを考えてみます。このテンプレートには、製品写真 ID と写真を返すクエリが含まれています。</span><span class="sxs-lookup"><span data-stu-id="30754-136">For example, consider the following template, which executes a query that returns an employee ID and a photo.</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
<sql:query client-side-xml="1">  
   SELECT ProductPhotoID, LargePhoto as P  
   FROM   Production.ProductPhoto  
   WHERE  ProductPhotoID=5  
   FOR XML NESTED, elements  
</sql:query>  
</ROOT>  
```  
  
 <span data-ttu-id="30754-137">このテンプレートを実行すると、Photo 列が dbobject クエリとして返されます。</span><span class="sxs-lookup"><span data-stu-id="30754-137">Executing this template returns the Photo column as a dbobject query.</span></span> <span data-ttu-id="30754-138">この dbobject クエリでは、`@P` で存在しない列名が参照されています。</span><span class="sxs-lookup"><span data-stu-id="30754-138">In this dbobject query, `@P` refers to a column name that does not exist.</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Production.ProductPhoto>  
    <ProductPhotoID>5</ProductPhotoID>  
    <LargePhoto>dbobject/Production.ProductPhoto[@ProductPhotoID='5']/@P</LargePhoto>  
  </Production.ProductPhoto>  
</ROOT>  
```  
  
 <span data-ttu-id="30754-139">XML の書式設定がサーバーで実行されている場合 (**クライアント側 xml = "0"**)、列の別名を使用して、実際のテーブル名と列名が返される dbobject クエリ (別名が指定されている場合でも) を返すことができます。</span><span class="sxs-lookup"><span data-stu-id="30754-139">If the XML formatting is done on the server (**client-side-xml="0"**), you can use the alias for the columns that return dbobject queries in which actual table and column names are returned (even if you have aliases specified).</span></span> <span data-ttu-id="30754-140">たとえば、次のテンプレートはクエリを実行し、XML の書式設定はサーバーで実行されます (**クライアント側の xml**オプションが指定されておらず、仮想ルートに対して **[クライアントで実行**] オプションが選択されていません)。</span><span class="sxs-lookup"><span data-stu-id="30754-140">For example, the following template executes a query, and the XML formatting is done on the server (the **client-side-xml** option is not specified and the **Run On Client** option is not selected for the virtual root).</span></span> <span data-ttu-id="30754-141">このクエリでは、クライアント側の NESTED モードではなく AUTO モードも指定されています。</span><span class="sxs-lookup"><span data-stu-id="30754-141">The query also specifies AUTO mode (not the client-side NESTED mode).</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
<sql:query   
   SELECT ProductPhotoID, LargePhoto as P  
   FROM   Production.ProductPhoto  
   WHERE  ProductPhotoID=5  
   FOR XML AUTO, elements  
</sql:query>  
</ROOT>  
```  
  
 <span data-ttu-id="30754-142">このテンプレートを実行すると、次の XML ドキュメントが返されます。LargePhoto 列に対する dbobject クエリでは、別名が使用されていないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="30754-142">When this template is executed, the following XML document is returned (note that aliases are not used in the dbobject query for the LargePhoto column):</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Production.ProductPhoto>  
    <ProductPhotoID>5</ProductPhotoID>  
    <LargePhoto>dbobject/Production.ProductPhoto[@ProductPhotoID='5']/@LargePhoto</LargePhoto>  
  </Production.ProductPhoto>  
</ROOT>  
```  
  
### <a name="client-side-vs-server-side-xpath"></a><span data-ttu-id="30754-143">クライアント側とサーバー側の XPath</span><span class="sxs-lookup"><span data-stu-id="30754-143">Client-side vs. Server-side XPath</span></span>  
 <span data-ttu-id="30754-144">クライアント側の XPath とサーバー側の XPath は類似していますが、次の点が異なります。</span><span class="sxs-lookup"><span data-stu-id="30754-144">Client-side XPath and server-side XPath work the same except for these differences:</span></span>  
  
-   <span data-ttu-id="30754-145">クライアント側の XPath クエリを使用するときに適用されるデータ変換は、サーバー側の XPath クエリを使用するときに適用されるものとは異なります。</span><span class="sxs-lookup"><span data-stu-id="30754-145">The data conversions that are applied when you use client-side XPath queries are different from those that are applied when you use server-side XPath queries.</span></span> <span data-ttu-id="30754-146">クライアント側の XPath では、CONVERT モード 126 の代わりに CAST が使用されます。</span><span class="sxs-lookup"><span data-stu-id="30754-146">Client-side XPath uses CAST instead of CONVERT mode 126.</span></span>  
  
-   <span data-ttu-id="30754-147">テンプレートで**クライアント側 xml = "0"** (false) を指定すると、サーバー側の xml 書式設定が要求されます。</span><span class="sxs-lookup"><span data-stu-id="30754-147">When you specify **client-side-xml="0"** (false) in a template, you are requesting server-side XML formatting.</span></span> <span data-ttu-id="30754-148">したがって、サーバーでは NESTED オプションが認識されないので、FOR XML NESTED は指定できません。</span><span class="sxs-lookup"><span data-stu-id="30754-148">Therefore, you cannot specify FOR XML NESTED because the server does not recognize the NESTED option.</span></span> <span data-ttu-id="30754-149">これにより、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="30754-149">This generates an error.</span></span> <span data-ttu-id="30754-150">この場合、サーバーで認識される AUTO、RAW、または EXPLICIT モードを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="30754-150">You must use the AUTO, RAW, or EXPLICIT modes, which the server does recognize.</span></span>  
  
-   <span data-ttu-id="30754-151">テンプレートで**クライアント側 xml = "1"** (true) を指定すると、クライアント側の xml 書式設定が要求されます。</span><span class="sxs-lookup"><span data-stu-id="30754-151">When you specify **client-side-xml="1"** (true) in a template, you are requesting client-side XML formatting.</span></span> <span data-ttu-id="30754-152">この場合、FOR XML NESTED を指定できます。</span><span class="sxs-lookup"><span data-stu-id="30754-152">In this case, you can specify FOR XML NESTED.</span></span> <span data-ttu-id="30754-153">FOR XML AUTO を指定した場合、XML の書式設定はサーバー側で行われますが、テンプレートには**クライアント側 xml = "1"** が指定されています。</span><span class="sxs-lookup"><span data-stu-id="30754-153">If you specify FOR XML AUTO, the XML formatting occurs on the server side although **client-side-xml="1"** is specified in the template.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30754-154">参照</span><span class="sxs-lookup"><span data-stu-id="30754-154">See Also</span></span>  
 <span data-ttu-id="30754-155">[XML のセキュリティに関する考慮事項 &#40;SQLXML 4.0&#41;](../../sqlxml-annotated-xsd-schemas-xpath-queries/security/for-xml-security-considerations-sqlxml-4-0.md) </span><span class="sxs-lookup"><span data-stu-id="30754-155">[FOR XML Security Considerations &#40;SQLXML 4.0&#41;](../../sqlxml-annotated-xsd-schemas-xpath-queries/security/for-xml-security-considerations-sqlxml-4-0.md) </span></span>  
 <span data-ttu-id="30754-156">[クライアント側の XML 書式設定 &#40;SQLXML 4.0&#41;](client-side-xml-formatting-sqlxml-4-0.md) </span><span class="sxs-lookup"><span data-stu-id="30754-156">[Client-side XML Formatting &#40;SQLXML 4.0&#41;](client-side-xml-formatting-sqlxml-4-0.md) </span></span>  
 [<span data-ttu-id="30754-157">サーバー側の XML 書式設定 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="30754-157">Server-side XML Formatting &#40;SQLXML 4.0&#41;</span></span>](server-side-xml-formatting-sqlxml-4-0.md)  
  
  
