---
title: クライアント側の XML 書式設定 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- FOR XML clause, formatting
- middle tier XML formatting [SQLXML]
- client-side XML formatting
- client-side-xml attribute
ms.assetid: 9630a21d-a93b-4d3b-8a25-c4b32399f993
author: rothja
ms.author: jroth
ms.openlocfilehash: bf4a680d79a25d24ebdf779b41fd3be5a5d6a605
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642672"
---
# <a name="client-side-xml-formatting-sqlxml-40"></a><span data-ttu-id="117a4-102">クライアント側の XML 書式設定 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="117a4-102">Client-side XML Formatting (SQLXML 4.0)</span></span>
  <span data-ttu-id="117a4-103">ここでは、クライアント側の XML 書式設定に関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="117a4-103">This topic provides information about client-side XML formatting.</span></span> <span data-ttu-id="117a4-104">クライアント側の書式設定とは、中間層での XML の書式設定を指します。</span><span class="sxs-lookup"><span data-stu-id="117a4-104">Client-side formatting refers to the formatting of XML on the middle tier.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="117a4-105">ここでは、クライアント側での FOR XML 句の使用に関する追加情報を提供します。ここでは、FOR XML 句について理解していることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="117a4-105">This topic provides additional information about using the FOR XML clause on the client side, and assumes you are already familiar with the FOR XML clause.</span></span> <span data-ttu-id="117a4-106">FOR XML の詳細については、「 [for Xml を使用した xml の構築](../../xml/for-xml-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="117a4-106">For more information about FOR XML, see [Constructing XML Using FOR XML](../../xml/for-xml-sql-server.md).</span></span>  
  
 <span data-ttu-id="117a4-107">**重要**新しいデータ型でクライアント側の FOR XML 機能を使用するには `xml` 、クライアントが [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] SQLOLEDB プロバイダーではなく Native CLIENT (SQLNCLI11) データプロバイダーを常に使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="117a4-107">**Important** To use client-side FOR XML functionality with the new `xml` data type, clients should always use the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client (SQLNCLI11) data provider instead of the SQLOLEDB provider.</span></span> <span data-ttu-id="117a4-108">SQLNCLI11 は、最新バージョンの SQL Server プロバイダーであり、[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] で導入されたデータ型を完全に認識します。</span><span class="sxs-lookup"><span data-stu-id="117a4-108">SQLNCLI11 is the latest version of the SQL Server provider and fully understands data types introduced in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].</span></span> <span data-ttu-id="117a4-109">クライアント側の FOR XML に SQLOLEDB プロバイダーを使用すると、`xml` データ型は文字列として扱われます。</span><span class="sxs-lookup"><span data-stu-id="117a4-109">The behavior for client side FOR XML with the SQLOLEDB provider will treat `xml` data types as strings.</span></span>  
  
## <a name="formatting-xml-documents-on-the-client-side"></a><span data-ttu-id="117a4-110">クライアント側での XML ドキュメントの書式設定</span><span class="sxs-lookup"><span data-stu-id="117a4-110">Formatting XML Documents on the Client Side</span></span>  
 <span data-ttu-id="117a4-111">クライアント アプリケーションで次のクエリを実行するとします。</span><span class="sxs-lookup"><span data-stu-id="117a4-111">When a client application executes the following query:</span></span>  
  
```  
SELECT FirstName, LastName  
FROM   Person.Contact  
FOR XML RAW  
```  
  
 <span data-ttu-id="117a4-112">この場合、クエリの次の部分だけがサーバーに送信されます。</span><span class="sxs-lookup"><span data-stu-id="117a4-112">...only this part of the query is sent to the server:</span></span>  
  
```  
SELECT FirstName, LastName  
FROM   Person.Contact  
```  
  
 <span data-ttu-id="117a4-113">サーバーはクエリを実行し、クライアントへの行セット (FirstName と LastNamecolumns を含む) を返します。</span><span class="sxs-lookup"><span data-stu-id="117a4-113">The server executes the query and returns a rowset (which contains FirstName and LastNamecolumns) to the client.</span></span> <span data-ttu-id="117a4-114">次に、中間層で、行セットに FOR XML 変換が適用され、XML の書式設定がクライアントに返されます。</span><span class="sxs-lookup"><span data-stu-id="117a4-114">The middle tier then applies the FOR XML transformation to the rowset and returns XML formatting to the client.</span></span>  
  
 <span data-ttu-id="117a4-115">同様に、XPath クエリを実行すると、サーバーからクライアントに行セットが返され、クライアント側で行セットに FOR XML EXPLICIT 変換が適用されて、目的の XML の書式設定が生成されます。</span><span class="sxs-lookup"><span data-stu-id="117a4-115">Similarly, when you execute an XPath query, the server returns the rowset to the client and the FOR XML EXPLICIT transformation is applied to the rowset on the client, generating the desired XML formatting.</span></span>  
  
 <span data-ttu-id="117a4-116">次の表は、クライアント側の FOR XML で指定できるモードです。</span><span class="sxs-lookup"><span data-stu-id="117a4-116">The following table shows the modes you can specify with client-side FOR XML.</span></span>  
  
|<span data-ttu-id="117a4-117">クライアント側の FOR XML のモード</span><span class="sxs-lookup"><span data-stu-id="117a4-117">Client-side FOR XML mode</span></span>|<span data-ttu-id="117a4-118">コメント</span><span class="sxs-lookup"><span data-stu-id="117a4-118">Comment</span></span>|  
|-------------------------------|-------------|  
|<span data-ttu-id="117a4-119">RAW</span><span class="sxs-lookup"><span data-stu-id="117a4-119">RAW</span></span>|<span data-ttu-id="117a4-120">クライアント側とサーバー側のどちらの FOR XML で指定しても、同じ結果が生成されます。</span><span class="sxs-lookup"><span data-stu-id="117a4-120">Produces identical results when specified in client-side or server-side FOR XML.</span></span>|  
|<span data-ttu-id="117a4-121">NESTED</span><span class="sxs-lookup"><span data-stu-id="117a4-121">NESTED</span></span>|<span data-ttu-id="117a4-122">サーバー側で FOR XML AUTO モードを指定した場合と同様です。</span><span class="sxs-lookup"><span data-stu-id="117a4-122">Is similar to FOR XML AUTO mode on the server-side.</span></span>|  
|<span data-ttu-id="117a4-123">EXPLICIT</span><span class="sxs-lookup"><span data-stu-id="117a4-123">EXPLICIT</span></span>|<span data-ttu-id="117a4-124">サーバー側で FOR XML EXPLICIT モードを指定した場合と同様です。</span><span class="sxs-lookup"><span data-stu-id="117a4-124">Is similar to server-side FOR XML EXPLICIT mode.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="117a4-125">AUTO モードを指定してクライアント側の XML 書式設定を要求すると、クエリ全体がサーバーに送信され、XML 書式設定はサーバー側で実行されます。</span><span class="sxs-lookup"><span data-stu-id="117a4-125">If you specify AUTO mode and request client-side XML formatting, the entire query is sent to the server; that is, XML formatting occurs on the server.</span></span> <span data-ttu-id="117a4-126">このモードは便利ですが、NESTED モードを指定した場合は、生成される XML ドキュメント内の要素名としてベース テーブル名が返される点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="117a4-126">This is done for convenience, but note that the NESTED mode returns base table names as element names in the XML document that is generated.</span></span> <span data-ttu-id="117a4-127">使用するアプリケーションによっては、ベース テーブル名が必要です。</span><span class="sxs-lookup"><span data-stu-id="117a4-127">Some of the applications you write might require base table names.</span></span> <span data-ttu-id="117a4-128">たとえば、ストアド プロシージャを実行し、結果のデータを [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework のデータセットに読み込んだ後で、テーブルのデータを更新する DiffGram を生成するとします。</span><span class="sxs-lookup"><span data-stu-id="117a4-128">For example, you might execute a stored procedure and load the resulting data in a Dataset (in the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework), and then later generate a DiffGram to update data in the tables.</span></span> <span data-ttu-id="117a4-129">この場合、ベース テーブル情報が必要となるため、NESTED モードを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="117a4-129">In such a case, you would need the base table information and you would have to use the NESTED mode.</span></span>  
  
## <a name="benefits-of-client-side-xml-formatting"></a><span data-ttu-id="117a4-130">クライアント側の XML 書式設定の利点</span><span class="sxs-lookup"><span data-stu-id="117a4-130">Benefits of Client-side XML formatting</span></span>  
 <span data-ttu-id="117a4-131">次に、クライアント側の XML 書式設定の利点をいくつか紹介します。</span><span class="sxs-lookup"><span data-stu-id="117a4-131">The following are some benefits of formatting XML on the client.</span></span>  
  
### <a name="if-you-have-stored-procedures-on-the-server-that-return-a-single-rowset-you-can-request-client-side-for-xml-transformation-to-generate-an-xml"></a><span data-ttu-id="117a4-132">サーバーに単一の行セットを返すストアド プロシージャがある場合、クライアント側の FOR XML 変換を要求して XML を生成できる。</span><span class="sxs-lookup"><span data-stu-id="117a4-132">If you have stored procedures on the server that return a single rowset, you can request client-side FOR XML transformation to generate an XML.</span></span>  
 <span data-ttu-id="117a4-133">たとえば、次のストアド プロシージャを考えてみます。</span><span class="sxs-lookup"><span data-stu-id="117a4-133">For example, consider the following stored procedure.</span></span> <span data-ttu-id="117a4-134">このプロシージャでは、従業員の姓と名前が AdventureWorks データベースの Person.Contact テーブルから返されます。</span><span class="sxs-lookup"><span data-stu-id="117a4-134">This procedure returns the first and last names of employees from the Person.Contact table in the AdventureWorks database:</span></span>  
  
```  
IF EXISTS (SELECT name FROM sysobjects  
   WHERE name = 'GetContacts' AND type = 'P')  
   DROP PROCEDURE GetContacts  
GO  
CREATE PROCEDURE GetContacts  
AS  
    SELECT   FirstName, LastName  
    FROM     Person.Contact  
```  
  
 <span data-ttu-id="117a4-135">このストアド プロシージャを、次のサンプル XML テンプレートで実行します。</span><span class="sxs-lookup"><span data-stu-id="117a4-135">The following sample XML template executes the stored procedure.</span></span> <span data-ttu-id="117a4-136">このとき、FOR XML 句をストアド プロシージャ名の後に指定します。</span><span class="sxs-lookup"><span data-stu-id="117a4-136">The FOR XML clause is specified after the stored procedure name.</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <sql:query client-side-xml="1">  
    EXEC GetContacts FOR XML NESTED  
  </sql:query>  
</ROOT>  
```  
  
 <span data-ttu-id="117a4-137">テンプレートでは、**クライアント側の xml**属性が 1 (true) に設定されているので、ストアドプロシージャはサーバー上で実行され、サーバーによって返される2列の行セットは、中間層の xml に変換されてクライアントに返されます。</span><span class="sxs-lookup"><span data-stu-id="117a4-137">Because the **client-side-xml** attribute is set to 1 (true) in the template, the stored procedure is executed on the server and the two-column rowset that is returned by the server is transformed into XML on the middle tier and returned to the client.</span></span> <span data-ttu-id="117a4-138">次に示すのは結果の一部です。</span><span class="sxs-lookup"><span data-stu-id="117a4-138">(Only a partial result is shown here.)</span></span>  
  
```  
 <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Person.Contact FirstName="Gustavo" LastName="Achong" />   
  <Person.Contact FirstName="Catherine" LastName="Abel" />  
</ROOT>  
```  
  
> [!NOTE]  
>  <span data-ttu-id="117a4-139">SQLXMLOLEDB プロバイダー、または SQLXML マネージド クラスを使用している場合は、`ClientSideXml` プロパティを使用してクライアント側の XML 書式設定を要求できます。</span><span class="sxs-lookup"><span data-stu-id="117a4-139">When you are using the SQLXMLOLEDB Provider or SQLXML Managed Classes, you can use the `ClientSideXml` property to request client-side XML formatting.</span></span>  
  
### <a name="the-workload-is-more-balanced"></a><span data-ttu-id="117a4-140">ワークロードをより適切に分散できる。</span><span class="sxs-lookup"><span data-stu-id="117a4-140">The workload is more balanced.</span></span>  
 <span data-ttu-id="117a4-141">クライアントで XML 書式設定を行うため、サーバーとクライアント間でワークロードがより適切に分散され、サーバーで他の処理を実行できるようになります。</span><span class="sxs-lookup"><span data-stu-id="117a4-141">Because the client does the XML formatting, the workload is balanced between the server and client, freeing the server to do other things.</span></span>  
  
## <a name="supporting-client-side-xml-formatting"></a><span data-ttu-id="117a4-142">クライアント側の XML 書式設定のサポート</span><span class="sxs-lookup"><span data-stu-id="117a4-142">Supporting Client-side XML Formatting</span></span>  
 <span data-ttu-id="117a4-143">クライアント側の XML 書式設定機能をサポートするため、SQLXML では次のコンポーネントが提供されます。</span><span class="sxs-lookup"><span data-stu-id="117a4-143">To support the client-side XML formatting functionality, SQLXML provides:</span></span>  
  
-   <span data-ttu-id="117a4-144">SQLXMLOLEDB プロバイダー</span><span class="sxs-lookup"><span data-stu-id="117a4-144">SQLXMLOLEDB Provider</span></span>  
  
-   <span data-ttu-id="117a4-145">SQLXML マネージド クラス</span><span class="sxs-lookup"><span data-stu-id="117a4-145">SQLXML Managed Classes</span></span>  
  
-   <span data-ttu-id="117a4-146">拡張 XML テンプレートのサポート</span><span class="sxs-lookup"><span data-stu-id="117a4-146">Enhanced XML template support</span></span>  
  
-   <span data-ttu-id="117a4-147">SqlXmlCommand. ClientSideXml プロパティ</span><span class="sxs-lookup"><span data-stu-id="117a4-147">SqlXmlCommand.ClientSideXml property</span></span>  
  
     <span data-ttu-id="117a4-148">SQLXML マネージド クラスのこのプロパティを true に設定すると、クライアント側の書式設定を指定できます。</span><span class="sxs-lookup"><span data-stu-id="117a4-148">You can specify client-side formatting by setting this property of the SQLXML managed classes to true.</span></span>  
  
## <a name="enhanced-xml-template-support"></a><span data-ttu-id="117a4-149">拡張 XML テンプレートのサポート</span><span class="sxs-lookup"><span data-stu-id="117a4-149">Enhanced XML Template Support</span></span>  
 <span data-ttu-id="117a4-150">以降で [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] は、の xml テンプレートは、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **クライアント側の xml**属性を追加して拡張されています。</span><span class="sxs-lookup"><span data-stu-id="117a4-150">Beginning with [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], the XML template in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] has been enhanced with the addition of the **client-side-xml** attribute.</span></span> <span data-ttu-id="117a4-151">この属性を true に設定すると、XML がクライアント側で書式設定されます。</span><span class="sxs-lookup"><span data-stu-id="117a4-151">If this attribute is set to true, XML is formatted on the client.</span></span> <span data-ttu-id="117a4-152">このテンプレート属性は、SQLXMLOLEDB プロバイダー固有の ClientSideXML プロパティと同じ機能であることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="117a4-152">Note that this template attribute is identical in functionality to the SQLXMLOLEDB Provider-specific ClientSideXML property.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="117a4-153">SQLXMLOLEDB プロバイダーを使用する ADO アプリケーションで XML テンプレートを実行し、テンプレートと Provider ClientSideXML プロパティの両方で**クライアント側の xml**属性を指定すると、テンプレートで指定された値が優先されます。</span><span class="sxs-lookup"><span data-stu-id="117a4-153">If you execute an XML template in an ADO application that is using the SQLXMLOLEDB Provider, and you specify both the **client-side-xml** attribute in the template and the provider ClientSideXML property, the value specified in the template takes precedence.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="117a4-154">参照</span><span class="sxs-lookup"><span data-stu-id="117a4-154">See Also</span></span>  
 <span data-ttu-id="117a4-155">[クライアント側およびサーバー側の XML 書式設定のアーキテクチャ &#40;SQLXML 4.0&#41;](server-side-xml-formatting-sqlxml-4-0.md) </span><span class="sxs-lookup"><span data-stu-id="117a4-155">[Architecture of Client-side and Server-side XML Formatting &#40;SQLXML 4.0&#41;](server-side-xml-formatting-sqlxml-4-0.md) </span></span>  
 <span data-ttu-id="117a4-156">[FOR XML &#40;SQL Server&#41;](../../xml/for-xml-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="117a4-156">[FOR XML &#40;SQL Server&#41;](../../xml/for-xml-sql-server.md) </span></span>  
 <span data-ttu-id="117a4-157">[XML のセキュリティに関する考慮事項 &#40;SQLXML 4.0&#41;](../../sqlxml-annotated-xsd-schemas-xpath-queries/security/for-xml-security-considerations-sqlxml-4-0.md) </span><span class="sxs-lookup"><span data-stu-id="117a4-157">[FOR XML Security Considerations &#40;SQLXML 4.0&#41;](../../sqlxml-annotated-xsd-schemas-xpath-queries/security/for-xml-security-considerations-sqlxml-4-0.md) </span></span>  
 <span data-ttu-id="117a4-158">[SQLXML 4.0 での xml データ型のサポート](../xml-data-type-support-in-sqlxml-4-0.md) </span><span class="sxs-lookup"><span data-stu-id="117a4-158">[xml Data Type Support in SQLXML 4.0](../xml-data-type-support-in-sqlxml-4-0.md) </span></span>  
 <span data-ttu-id="117a4-159">[SQLXML マネージクラス](../../sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/sqlxml-4-0-net-framework-support-managed-classes.md) </span><span class="sxs-lookup"><span data-stu-id="117a4-159">[SQLXML Managed Classes](../../sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/sqlxml-4-0-net-framework-support-managed-classes.md) </span></span>  
 <span data-ttu-id="117a4-160">[クライアント側とサーバー側の XML 書式設定 &#40;SQLXML 4.0&#41;](client-side-vs-server-side-xml-formatting-sqlxml-4-0.md) </span><span class="sxs-lookup"><span data-stu-id="117a4-160">[Client-side vs. Server-side XML Formatting &#40;SQLXML 4.0&#41;](client-side-vs-server-side-xml-formatting-sqlxml-4-0.md) </span></span>  
 <span data-ttu-id="117a4-161">[SqlXmlCommand オブジェクト &#40;SQLXML マネージクラス&#41;](../../sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/sqlxml-managed-classes-sqlxmlcommand-object.md) </span><span class="sxs-lookup"><span data-stu-id="117a4-161">[SqlXmlCommand Object &#40;SQLXML Managed Classes&#41;](../../sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/sqlxml-managed-classes-sqlxmlcommand-object.md) </span></span>  
 [<span data-ttu-id="117a4-162">XML データ &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="117a4-162">XML Data &#40;SQL Server&#41;</span></span>](../../xml/xml-data-sql-server.md)  
  
  
