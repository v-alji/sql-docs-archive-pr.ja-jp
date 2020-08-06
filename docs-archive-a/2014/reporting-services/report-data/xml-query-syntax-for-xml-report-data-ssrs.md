---
title: XML レポート データの XML クエリ構文 (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- namespaces [Reporting Services]
- data processing extensions [Reporting Services], data sources
- xmldp [Reporting Services]
- XML [Reporting Services], data retrieval
ms.assetid: d203886f-faa1-4a02-88f5-dd4c217181ef
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 62dde2b3ab18b5edb5c3786d39173fea3a0854ac
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631563"
---
# <a name="xml-query-syntax-for-xml-report-data-ssrs"></a><span data-ttu-id="8336d-102">XML レポート データの XML クエリ構文 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="8336d-102">XML Query Syntax for XML Report Data (SSRS)</span></span>
  <span data-ttu-id="8336d-103">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]では、XML データ ソースのデータセットを作成できます。</span><span class="sxs-lookup"><span data-stu-id="8336d-103">In [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], you can create datasets for XML data sources.</span></span> <span data-ttu-id="8336d-104">データセットを取得するためのクエリは、データ ソースを定義した後で作成します。</span><span class="sxs-lookup"><span data-stu-id="8336d-104">After you define a data source, you create a query for the dataset.</span></span> <span data-ttu-id="8336d-105">データセット クエリを作成する際は、データ ソースが参照する XML データの種類に応じて、XML `Query` または要素パスを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8336d-105">Depending on the type of XML data pointed to by the data source, you create the dataset query by including an XML `Query` or an element path.</span></span> <span data-ttu-id="8336d-106">XML は `Query` タグで始まり、 **\<Query>** データソースによって異なる名前空間と xml 要素が含まれています。</span><span class="sxs-lookup"><span data-stu-id="8336d-106">An XML `Query` starts with a **\<Query>** tag and includes namespaces and XML elements that vary depending on the data source.</span></span> <span data-ttu-id="8336d-107">要素パスは、基になる XML データから取り出すノードおよびノード属性を XPath に似た構文で指定するもので、名前空間には依存しません。</span><span class="sxs-lookup"><span data-stu-id="8336d-107">An element path is namespace-independent and specifies which nodes and node attributes to use from the underlying XML data with an XPath-like syntax.</span></span> <span data-ttu-id="8336d-108">要素パスの詳細については、「[Element Path Syntax for XML Report Data &#40;SSRS&#41;](report-data-ssrs.md)」 (XML レポート データの要素パス構文 &#40;SSRS&#41;) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8336d-108">For more information about element paths, see [Element Path Syntax for XML Report Data &#40;SSRS&#41;](report-data-ssrs.md).</span></span>  
  
 <span data-ttu-id="8336d-109">次のような種類の XML データについて、XML データ ソースを作成できます。</span><span class="sxs-lookup"><span data-stu-id="8336d-109">You can create an XML data source for the following types of XML data:</span></span>  
  
-   <span data-ttu-id="8336d-110">HTTP プロトコルを使って URL で参照される XML ドキュメント</span><span class="sxs-lookup"><span data-stu-id="8336d-110">Xml documents pointed to by a URL using http protocol</span></span>  
  
-   <span data-ttu-id="8336d-111">XML データを返す Web サービスのエンドポイント</span><span class="sxs-lookup"><span data-stu-id="8336d-111">Web service endpoints that return XML data</span></span>  
  
-   <span data-ttu-id="8336d-112">埋め込み XML データ</span><span class="sxs-lookup"><span data-stu-id="8336d-112">Embedded XML data</span></span>  
  
 <span data-ttu-id="8336d-113">XML `Query` または要素パスの指定方法は、XML データの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="8336d-113">How you specify an XML `Query` or an element path depends on the type of XML data.</span></span>  
  
 <span data-ttu-id="8336d-114">XML ドキュメントの場合、XML `Query` は省略可能です。</span><span class="sxs-lookup"><span data-stu-id="8336d-114">For an XML document, the XML `Query` is optional.</span></span> <span data-ttu-id="8336d-115">省略しなかった場合、必要に応じて XML `ElementPath` を指定できます。</span><span class="sxs-lookup"><span data-stu-id="8336d-115">If it is included, it can contain an optional XML `ElementPath`.</span></span> <span data-ttu-id="8336d-116">XML `ElementPath` の値には、要素パスの構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="8336d-116">The value of the XML `ElementPath` uses the element path syntax.</span></span> <span data-ttu-id="8336d-117">XML `Query` および XML `ElementPath` を指定することにより、データ ソースから取得された XML データに対して名前空間を適切に適用できます。</span><span class="sxs-lookup"><span data-stu-id="8336d-117">You include the XML `Query` and XML `ElementPath` to process namespaces correctly when it is needed by the XML data from the data source.</span></span>  
  
 <span data-ttu-id="8336d-118">接続文字列の URL によって参照される Web サービスのエンドポイントの場合、XML `Query` には、Web サービス メソッドか SOAP アクション、またはその両方を定義します。</span><span class="sxs-lookup"><span data-stu-id="8336d-118">For a Web service endpoint pointed to by a connection string URL, the XML `Query` defines either the Web service method, the SOAP action, or both.</span></span> <span data-ttu-id="8336d-119">レポート用の XML データを取得するための Web サービス要求が XML データ プロバイダーによって作成されます。</span><span class="sxs-lookup"><span data-stu-id="8336d-119">The XML data provider creates a Web service request that retrieves XML data to use for the report.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8336d-120">Web サービスの名前空間にスラッシュ (`/)` 文字が含まれる場合は、XML データ処理拡張機能が名前空間を正確に取得できるように、Web サービス メソッドと SOAP アクションの両方を指定します。</span><span class="sxs-lookup"><span data-stu-id="8336d-120">When a Web service namespace includes a forward slash (`/)` character, include both the Web service method and the SOAP action so that the XML data processing extension can derive the namespace correctly.</span></span>  
  
 <span data-ttu-id="8336d-121">埋め込み XML ドキュメントの場合、XML `Query` には、使用する埋め込み XML データを定義します。名前空間と XML `ElementPath` を指定することもできます (省略可能)。</span><span class="sxs-lookup"><span data-stu-id="8336d-121">For an embedded XML document, the XML `Query` defines the embedded XML data to use, includes optional namespaces, and contains an optional XML `ElementPath`..</span></span>  
  
## <a name="specifying-query-parameters-for-xml-data"></a><span data-ttu-id="8336d-122">XML データに対するクエリ パラメーターの指定</span><span class="sxs-lookup"><span data-stu-id="8336d-122">Specifying Query Parameters for XML Data</span></span>  
 <span data-ttu-id="8336d-123">XML ドキュメントに対するクエリ パラメーターを指定することができます。</span><span class="sxs-lookup"><span data-stu-id="8336d-123">You can specify query parameters for XML documents.</span></span>  
  
-   <span data-ttu-id="8336d-124">URL 要求の場合、クエリ パラメーターは標準の URL パラメーターとして含まれます。</span><span class="sxs-lookup"><span data-stu-id="8336d-124">For URL requests, the query parameters are included as standard URL parameters.</span></span>  
  
-   <span data-ttu-id="8336d-125">Web サービス要求の場合、クエリ パラメーターは Web サービスのメソッドに渡されます。</span><span class="sxs-lookup"><span data-stu-id="8336d-125">For Web service requests, query parameters are passed to the Web service method.</span></span> <span data-ttu-id="8336d-126">クエリ パラメーターを定義するには、 **[データセットのプロパティ]** ダイアログ ボックスの **[パラメーター]** ページを使用します。</span><span class="sxs-lookup"><span data-stu-id="8336d-126">To define a query parameter, use the **Parameters** page of the **Dataset Properties** dialog box.</span></span> <span data-ttu-id="8336d-127">詳細については、「 [[パラメーター] ([データセットのプロパティ] ダイアログ ボックス)](dataset-properties-dialog-box-parameters.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8336d-127">For more information, see [Dataset Properties Dialog Box, Parameters](dataset-properties-dialog-box-parameters.md).</span></span>  
  
### <a name="example"></a><span data-ttu-id="8336d-128">例</span><span class="sxs-lookup"><span data-stu-id="8336d-128">Example</span></span>  
 <span data-ttu-id="8336d-129">次の表は、データの取得方法の例を、レポート サーバー Web サービス、XML ドキュメント、埋め込み XML データのそれぞれについて示したものです。</span><span class="sxs-lookup"><span data-stu-id="8336d-129">The examples in the following table illustrate how to retrieve data from the Report Server Web service, an XML document, and embedded XML data.</span></span>  
  
|<span data-ttu-id="8336d-130">XML データ ソース</span><span class="sxs-lookup"><span data-stu-id="8336d-130">XML data source</span></span>|<span data-ttu-id="8336d-131">クエリの例</span><span class="sxs-lookup"><span data-stu-id="8336d-131">Query example</span></span>|  
|---------------------|-------------------|  
|<span data-ttu-id="8336d-132">Web サービスの XML データ ( ListChildren メソッドから)</span><span class="sxs-lookup"><span data-stu-id="8336d-132">Web service XML data from ListChildren method.</span></span>|`<Query>`<br /><br /> `<Method Name="ListChildren" Namespace="https://schemas.microsoft.com/sqlserver/2005/06/30/reporting/reportingservices" />`<br /><br /> `</Query>`|  
|<span data-ttu-id="8336d-133">Web サービスの XML データ (SoapAction から)</span><span class="sxs-lookup"><span data-stu-id="8336d-133">Web service XML data from SoapAction.</span></span>|`<Query xmlns=namespace>`<br /><br /> `<SoapAction>http://schemas/microsoft.com/sqlserver/2005/03/23/reporting/reportingservices/ListChildren</SoapAction>`<br /><br /> `</Query>`|  
|<span data-ttu-id="8336d-134">XML ドキュメントまたは埋め込み XML データ (名前空間を使用)</span><span class="sxs-lookup"><span data-stu-id="8336d-134">XML Document or embedded XML data that uses namespaces.</span></span><br /><br /> <span data-ttu-id="8336d-135">Query 要素 (要素パスに名前空間を指定)</span><span class="sxs-lookup"><span data-stu-id="8336d-135">Query element specifying namespaces for an element path.</span></span>|`<Query xmlns:es="https://schemas.microsoft.com/StandardSchemas/ExtendedSales">`<br /><br /> `<ElementPath>/Customers/Customer/Orders/Order/es:LineItems/es:LineItem</ElementPath>`<br /><br /> `</Query>`|  
|<span data-ttu-id="8336d-136">埋め込み XML ドキュメント</span><span class="sxs-lookup"><span data-stu-id="8336d-136">Embedded XML document.</span></span>|`<Query>`<br /><br /> `<XmlData>`<br /><br /> `<Customers>`<br /><br /> `<Customer ID="1">Bobby</Customer>`<br /><br /> `</Customers>`<br /><br /> `</XmlData>`<br /><br /> `<ElementPath>Customer {@}</ElementPath>`<br /><br /> `</Query>`|  
|<span data-ttu-id="8336d-137">XML ドキュメント (既定)</span><span class="sxs-lookup"><span data-stu-id="8336d-137">XML document that uses default.</span></span>|<span data-ttu-id="8336d-138">*クエリなし*。</span><span class="sxs-lookup"><span data-stu-id="8336d-138">*No query*.</span></span><br /><br /> <span data-ttu-id="8336d-139">要素パスは XML ドキュメントそのものから取得され、名前空間には依存しません。</span><span class="sxs-lookup"><span data-stu-id="8336d-139">The element path is derived from the XML document itself and is namespace-independent.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="8336d-140">最初に挙げた Web サービスの例では、 <xref:ReportService2006.ReportingService2006.ListChildren%2A> メソッドから)</span><span class="sxs-lookup"><span data-stu-id="8336d-140">The first Web service example lists the contents of the report server that uses the <xref:ReportService2006.ReportingService2006.ListChildren%2A> method.</span></span> <span data-ttu-id="8336d-141">このクエリを実行するには、新しいデータ ソースを作成し、接続文字列を http://localhost/reportserver/reportservice2006.asmx に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8336d-141">To run this query, you must create a new data source and set the connection string to http://localhost/reportserver/reportservice2006.asmx.</span></span> <span data-ttu-id="8336d-142"><xref:ReportService2006.ReportingService2006.ListChildren%2A> メソッドは、`Item` と `Recursive` の 2 つのパラメーターを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="8336d-142">The <xref:ReportService2006.ReportingService2006.ListChildren%2A> method takes two parameters: `Item` and `Recursive`.</span></span> <span data-ttu-id="8336d-143">`Item` の既定値は `/` に、`Recursive` の既定値は `1` に設定されます。</span><span class="sxs-lookup"><span data-stu-id="8336d-143">Set the default value for `Item` to `/` and `Recursive` to `1`.</span></span>  
  
## <a name="specifying-namespaces"></a><span data-ttu-id="8336d-144">名前空間の指定</span><span class="sxs-lookup"><span data-stu-id="8336d-144">Specifying Namespaces</span></span>  
 <span data-ttu-id="8336d-145">データ ソースから取得された XML データに使用する名前空間を指定するには、XML `Query` 要素を使用します。</span><span class="sxs-lookup"><span data-stu-id="8336d-145">Use the XML `Query` element to specify the namespaces that are used in the XML data from the data source.</span></span> <span data-ttu-id="8336d-146">次の XML クエリには、名前空間 `sales` が使用されています。</span><span class="sxs-lookup"><span data-stu-id="8336d-146">The following XML query uses the namespace `sales`.</span></span> <span data-ttu-id="8336d-147">`sales:LineItems` および `sales:LineItem` の XML `ElementPath` ノードには、名前空間 `sales` が使用されています。</span><span class="sxs-lookup"><span data-stu-id="8336d-147">The XML `ElementPath` nodes for `sales:LineItems` and `sales:LineItem` use the namespace `sales`.</span></span>  
  
```  
<Query xmlns:sales=  
"https://schemas.microsoft.com/StandardSchemas/ExtendedSales">  
   <SoapAction>  
      https://schemas.microsoft.com/SalesWebService/ListOrders   
   </SoapAction>  
   <ElementPath>  
      Customers/Customer/Orders/Order/sales:LineItems/sales:LineItem  
   </ElementPath>  
</Query>  
```  
  
 <span data-ttu-id="8336d-148">データ プロバイダーの名前空間を指定して、既定の名前空間を空のままにするには、`xmldp` を使用します。</span><span class="sxs-lookup"><span data-stu-id="8336d-148">To specify the data provider namespace so that the default namespace remains empty, use `xmldp`.</span></span> <span data-ttu-id="8336d-149">これを次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="8336d-149">This is shown in the following example.</span></span>  
  
### <a name="example"></a><span data-ttu-id="8336d-150">例</span><span class="sxs-lookup"><span data-stu-id="8336d-150">Example</span></span>  
 <span data-ttu-id="8336d-151">次の例では、DPNamespace.xml (後述) という XML ドキュメントが使用されています。</span><span class="sxs-lookup"><span data-stu-id="8336d-151">The following examples use the XML document DPNamespace.xml, which is provided for illustration after the table.</span></span> <span data-ttu-id="8336d-152">この表では、名前空間プレフィックスを使用した XML ElementPath 構文として、2 つの例を紹介します。</span><span class="sxs-lookup"><span data-stu-id="8336d-152">This table shows two examples of XML ElementPath syntax that includes namespace prefixes.</span></span>  
  
|<span data-ttu-id="8336d-153">XML Query 要素</span><span class="sxs-lookup"><span data-stu-id="8336d-153">XML Query Element</span></span>|<span data-ttu-id="8336d-154">データセットとして取得されるフィールド</span><span class="sxs-lookup"><span data-stu-id="8336d-154">Resulting fields in the dataset</span></span>|  
|-----------------------|-------------------------------------|  
|\<Query/>|<span data-ttu-id="8336d-155">値 A: `https://schemas.microsoft.com/..` 。</span><span class="sxs-lookup"><span data-stu-id="8336d-155">Value A: `https://schemas.microsoft.com/..`.</span></span><br /><br /> <span data-ttu-id="8336d-156">値 B: `https://schemas.microsoft.com/..` 。</span><span class="sxs-lookup"><span data-stu-id="8336d-156">Value B: `https://schemas.microsoft.com/..`.</span></span><br /><br /> <span data-ttu-id="8336d-157">値 C: `https://schemas.microsoft.com/.` ..</span><span class="sxs-lookup"><span data-stu-id="8336d-157">Value C: `https://schemas.microsoft.com/.`..</span></span>|  
|\<xmldp:Query xmlns:xmldp="https://schemas.microsoft.com/sqlserver/2005/02/reporting/XmlDPQuery" xmlns:ns="https://schemas.microsoft.com/..."><br /><br /> <span data-ttu-id="8336d-158">\<xmldp:ElementPath>ルート {} /ns: Element2/Node\</xmldp:ElementPath></span><span class="sxs-lookup"><span data-stu-id="8336d-158">\<xmldp:ElementPath>Root {}/ns:Element2/Node\</xmldp:ElementPath></span></span><br /><br /> \</xmldp:Query>|<span data-ttu-id="8336d-159">Value D</span><span class="sxs-lookup"><span data-stu-id="8336d-159">Value D</span></span><br /><br /> <span data-ttu-id="8336d-160">Value E</span><span class="sxs-lookup"><span data-stu-id="8336d-160">Value E</span></span><br /><br /> <span data-ttu-id="8336d-161">Value F</span><span class="sxs-lookup"><span data-stu-id="8336d-161">Value F</span></span>|  
  
#### <a name="xml-document-dpnamespacexml"></a><span data-ttu-id="8336d-162">XML document: DPNamespace.xml</span><span class="sxs-lookup"><span data-stu-id="8336d-162">XML document: DPNamespace.xml</span></span>  
 <span data-ttu-id="8336d-163">この XML をコピーして、レポート デザイナーからアクセスできる URL (http://localhost/DPNamespace.xml など) に保存すると、XML データ ソースとして使用できます。</span><span class="sxs-lookup"><span data-stu-id="8336d-163">You can copy this XML and save it to a URL available for Report Designer to use as an XML data source: for example, http://localhost/DPNamespace.xml.</span></span>  
  
```  
<Root xmlns:ns="https://schemas.microsoft.com/...">  
   <ns:Element1>  
      <Node>Value A</Node>  
      <Node>Value B</Node>  
      <Node>Value C</Node>  
   </ns:Element1>  
   <ns:Element2>  
      <Node>Value D</Node>  
      <Node>Value E</Node>  
      <Node>Value F</Node>  
   </ns:Element2>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8336d-164">参照</span><span class="sxs-lookup"><span data-stu-id="8336d-164">See Also</span></span>  
 <span data-ttu-id="8336d-165">[XML 接続の種類 &#40;SSRS&#41;](xml-connection-type-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="8336d-165">[XML Connection Type &#40;SSRS&#41;](xml-connection-type-ssrs.md) </span></span>  
 [<span data-ttu-id="8336d-166">Reporting Services チュートリアル &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="8336d-166">Reporting Services Tutorials &#40;SSRS&#41;</span></span>](../reporting-services-tutorials-ssrs.md)  
  
  
