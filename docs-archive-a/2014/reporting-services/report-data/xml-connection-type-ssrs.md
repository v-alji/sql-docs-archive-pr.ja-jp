---
title: XML の接続の種類 (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 5b55fff2-1b15-4156-83ef-15ad9cf9f509
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 141f6449e0493ba7a12e9270bedab967b7795ee0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739397"
---
# <a name="xml-connection-type-ssrs"></a><span data-ttu-id="65af6-102">XML の接続の種類 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="65af6-102">XML Connection Type (SSRS)</span></span>
  <span data-ttu-id="65af6-103">XML データ ソースのデータをレポートに含めるには、種類が XML のレポート データ ソースに基づいたデータセットが必要です。</span><span class="sxs-lookup"><span data-stu-id="65af6-103">To include data from an XML data source in your report, you must have a dataset that is based on a report data source of type XML.</span></span> <span data-ttu-id="65af6-104">このビルトイン データ ソースの種類は、XML データ拡張機能に基づいています。</span><span class="sxs-lookup"><span data-stu-id="65af6-104">This built-in data source type is based on the XML data extension.</span></span> <span data-ttu-id="65af6-105">このデータ ソースの種類を使用して、XML ドキュメント、Web サービス、またはクエリに埋め込まれた XML に接続し、データを取得します。</span><span class="sxs-lookup"><span data-stu-id="65af6-105">Use this data source type to connect to and retrieve data from XML documents, Web services, or XML that is embedded in the query.</span></span>  
  
 <span data-ttu-id="65af6-106">このデータ拡張機能は、接続文字列とは別に管理される資格情報およびパラメーターをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="65af6-106">This data extension supports parameters and credentials managed separately from the connection string.</span></span>  
  
 <span data-ttu-id="65af6-107">このトピックの情報を使用して、データ ソースを構築してください。</span><span class="sxs-lookup"><span data-stu-id="65af6-107">Use the information in this topic to build a data source.</span></span> <span data-ttu-id="65af6-108">詳細な手順については、「[データ接続またはデータソース &#40;レポートビルダーと SSRS&#41;の追加と検証](add-and-verify-a-data-connection-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="65af6-108">For step-by-step instructions, see [Add and Verify a Data Connection or Data Source &#40;Report Builder and SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md).</span></span>  
  
##  <a name="connection-string"></a><a name="Connection"></a> <span data-ttu-id="65af6-109">接続文字列</span><span class="sxs-lookup"><span data-stu-id="65af6-109">Connection String</span></span>  
 <span data-ttu-id="65af6-110">接続文字列を、HTTP 経由でアクセス可能な Web サービス、Web ベース アプリケーション、または XML ドキュメントを指す URL に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="65af6-110">The connection string must be a URL that points to the Web service, Web-based application, or XML document available through HTTP.</span></span> <span data-ttu-id="65af6-111">XML ドキュメントの拡張子は XML にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="65af6-111">XML documents must have the XML extension.</span></span> <span data-ttu-id="65af6-112">データセット クエリに埋め込まれた XML データに対し、空の接続文字列を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="65af6-112">You can also use an empty connection string for XML data embedded in the dataset query.</span></span>  
  
 <span data-ttu-id="65af6-113">次の例に、それぞれ Web サービスと XML ドキュメントに対する接続文字列の構文を示します。</span><span class="sxs-lookup"><span data-stu-id="65af6-113">The following examples illustrate the connection string syntax for a Web service and XML document, respectively.</span></span> <span data-ttu-id="65af6-114">`file://` プロトコルはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="65af6-114">The `file://` protocol is not supported.</span></span>  
  
|<span data-ttu-id="65af6-115">XML ドキュメントの種類</span><span class="sxs-lookup"><span data-stu-id="65af6-115">XML document type</span></span>|<span data-ttu-id="65af6-116">接続文字列の例</span><span class="sxs-lookup"><span data-stu-id="65af6-116">Connection String Example</span></span>|  
|-----------------------|-------------------------------|  
|<span data-ttu-id="65af6-117">Web サービス</span><span class="sxs-lookup"><span data-stu-id="65af6-117">Web service</span></span>|`http://adventure-works.com/results.aspx`|  
|<span data-ttu-id="65af6-118">XML ドキュメント</span><span class="sxs-lookup"><span data-stu-id="65af6-118">XML document</span></span>|`http://localhost/XML/Customers.xml`|  
|<span data-ttu-id="65af6-119">埋め込み XML ドキュメント</span><span class="sxs-lookup"><span data-stu-id="65af6-119">Embedded XML document</span></span>|<span data-ttu-id="65af6-120">*空*</span><span class="sxs-lookup"><span data-stu-id="65af6-120">*Empty*</span></span>|  
  
 <span data-ttu-id="65af6-121">接続文字列の例について詳しくは、「 [レポート ビルダーでのデータ接続、データ ソース、および接続文字列](../data-connections-data-sources-and-connection-strings-in-report-builder.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="65af6-121">For more connection string examples, see [Data Connections, Data Sources, and Connection Strings in Report Builder](../data-connections-data-sources-and-connection-strings-in-report-builder.md).</span></span>  
  
##  <a name="credentials"></a><a name="Credentials"></a> <span data-ttu-id="65af6-122">[資格情報]</span><span class="sxs-lookup"><span data-stu-id="65af6-122">Credentials</span></span>  
 <span data-ttu-id="65af6-123">クエリの実行、ローカルでのレポートのプレビュー、およびレポート サーバーからのレポートのプレビューには、資格情報が必要です。</span><span class="sxs-lookup"><span data-stu-id="65af6-123">Credentials are required to run queries, to preview the report locally, and to preview the report from the report server.</span></span>  
  
 <span data-ttu-id="65af6-124">レポートをパブリッシュした後、レポートをレポート サーバーで実行するときに、データを取得するための権限が有効な状態になるように、データ ソースの資格情報を変更する必要が生じる場合があります。</span><span class="sxs-lookup"><span data-stu-id="65af6-124">After you publish your report, you may need to change the credentials for the data source so that when the report runs on the report server, the permissions to retrieve the data are valid.</span></span>  
  
 <span data-ttu-id="65af6-125">レポート作成クライアントから、次のオプションを使用して資格情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="65af6-125">From a report authoring client, the following options are available to specify credentials:</span></span>  
  
-   <span data-ttu-id="65af6-126">現在の Windows ユーザー (統合セキュリティとも呼ばれます)。</span><span class="sxs-lookup"><span data-stu-id="65af6-126">Current Windows user (also known as integrated security).</span></span>  
  
-   <span data-ttu-id="65af6-127">資格情報を必要としない。</span><span class="sxs-lookup"><span data-stu-id="65af6-127">No credentials are required.</span></span> <span data-ttu-id="65af6-128">資格情報を選択しない場合には、匿名アクセスが使用されます。</span><span class="sxs-lookup"><span data-stu-id="65af6-128">If you select no credentials, Anonymous access is used.</span></span> <span data-ttu-id="65af6-129">レポート サーバーが外部データ ソースに接続するための自動実行アカウントが定義済みであることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="65af6-129">Make sure that you have defined the unattended execution account for the report server to connect to an external data source.</span></span> <span data-ttu-id="65af6-130">XML データ処理拡張機能は、対象 URL または Web サービスに資格情報を渡しません。したがって、自動実行アカウントが定義されていないと接続に失敗します。</span><span class="sxs-lookup"><span data-stu-id="65af6-130">The XML data processing extension does not pass credentials to the target URL or the Web service; the connection will be unsuccessful unless you have defined the unattended execution account.</span></span> <span data-ttu-id="65af6-131">詳細については、msdn.microsoft.com の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [オンライン ブック](https://go.microsoft.com/fwlink/?linkid=121312)にある [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ドキュメントの「[自動実行アカウントの構成 (SSRS 構成マネージャー)](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="65af6-131">For more information, see [Configure the Unattended Execution Account &#40;SSRS Configuration Manager&#41;](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md) in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] documentation in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312) on msdn.microsoft.com.</span></span>  
  
 <span data-ttu-id="65af6-132">保存された資格情報や要求された資格情報はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="65af6-132">Stored and prompted credentials are not supported.</span></span> <span data-ttu-id="65af6-133">Windows 統合セキュリティが無効になっていると、データの取得に Windows 統合セキュリティを使用できないので注意してください。</span><span class="sxs-lookup"><span data-stu-id="65af6-133">Remember that if you disable Windows integrated security, you cannot use it to retrieve data.</span></span> <span data-ttu-id="65af6-134">保存された資格情報や要求された資格情報を指定すると、実行時にエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="65af6-134">If you specify stored or prompted credentials, an error will occur at run time.</span></span>  
  
 <span data-ttu-id="65af6-135">詳細については、「 [Reporting Services のデータ接続、データソース、および接続文字列](../data-connections-data-sources-and-connection-strings-in-reporting-services.md)」または「[レポートビルダーで資格情報を指定する](../specify-credentials-in-report-builder.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="65af6-135">For more information, see [Data Connections, Data Sources, and Connection Strings in Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) or [Specify Credentials in Report Builder](../specify-credentials-in-report-builder.md).</span></span>  
  
##  <a name="queries"></a><a name="Query"></a> <span data-ttu-id="65af6-136">クエリ</span><span class="sxs-lookup"><span data-stu-id="65af6-136">Queries</span></span>  
 <span data-ttu-id="65af6-137">クエリでは、レポート データセット用に取得するデータを指定します。</span><span class="sxs-lookup"><span data-stu-id="65af6-137">A query specifies which data to retrieve for a report dataset.</span></span> <span data-ttu-id="65af6-138">クエリの結果セットの列には、データセットのフィールド コレクションが設定されます。</span><span class="sxs-lookup"><span data-stu-id="65af6-138">The columns in the result set for a query populate the field collection for a dataset.</span></span> <span data-ttu-id="65af6-139">レポートによって処理されるのは、クエリから取得された最初の結果セットだけです。</span><span class="sxs-lookup"><span data-stu-id="65af6-139">A report processes only the first result set retrieved by a query.</span></span>  
  
 <span data-ttu-id="65af6-140">クエリを作成するにはテキスト ベースのクエリ デザイナーを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="65af6-140">You must use the text-based query designer to create the query.</span></span> <span data-ttu-id="65af6-141">クエリでは XML データを返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="65af6-141">The query must return XML data.</span></span>  
  
 <span data-ttu-id="65af6-142">テキスト ベースのクエリ デザイナーについては、「[テキストベースのクエリ デザイナーのユーザー インターフェイス (レポート ビルダー)](text-based-query-designer-user-interface-report-builder.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="65af6-142">For more information about the text-based query designer, see [Text-based Query Designer User Interface &#40;Report Builder&#41;](text-based-query-designer-user-interface-report-builder.md).</span></span>  
  
 <span data-ttu-id="65af6-143">XML データ ソースに対して使用できるデータセット クエリの値を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="65af6-143">The possible values for a dataset query for a data source that is type XML are shown below.</span></span>  
  
-   <span data-ttu-id="65af6-144">*Empty*: 空のクエリを使用して、既定の結果セットを作成します。</span><span class="sxs-lookup"><span data-stu-id="65af6-144">*Empty*: Use an empty query to create a default result set.</span></span> <span data-ttu-id="65af6-145">既定のクエリは、データ ソースを読み取り、最初のリーフ コレクションまで XML ノード階層をたどることによって作成されます。</span><span class="sxs-lookup"><span data-stu-id="65af6-145">The default query is created by reading the data source and traversing the XML node hierarchy to the first leaf collection.</span></span> <span data-ttu-id="65af6-146">結果セットには、テキスト値を持つすべてのノード、および、そのパス上に存在するすべてのノード属性が格納されます。</span><span class="sxs-lookup"><span data-stu-id="65af6-146">The result set includes all nodes with text values and all node attributes along that path.</span></span> <span data-ttu-id="65af6-147">結果セットの列は、データセットのフィールドにマップされます。</span><span class="sxs-lookup"><span data-stu-id="65af6-147">Columns in the result set are mapped to fields for the dataset.</span></span>  
  
-   <span data-ttu-id="65af6-148">要素パス: データソースから XML データを取得するときに使用するノードのシーケンスを指定します。</span><span class="sxs-lookup"><span data-stu-id="65af6-148">An element path: Specifies the sequence of nodes to use when retrieving XML data from the data source.</span></span>  
  
-   <span data-ttu-id="65af6-149">XML Query 要素: 次のオプションの要素を含む XML クエリの仕様。</span><span class="sxs-lookup"><span data-stu-id="65af6-149">An XML Query element: An XML query specification with the following optional elements:</span></span>  
  
    -   <span data-ttu-id="65af6-150">**Web サービスの場合:**</span><span class="sxs-lookup"><span data-stu-id="65af6-150">**For a Web service:**</span></span>  
  
         <span data-ttu-id="65af6-151">必須の XML 要素:</span><span class="sxs-lookup"><span data-stu-id="65af6-151">Required XML Elements:</span></span>  
  
         <span data-ttu-id="65af6-152">`<Method Namespace=`*"namespace"*  `Name="MethodName" />`</span><span class="sxs-lookup"><span data-stu-id="65af6-152">`<Method Namespace=` *"namespace"*  `Name="MethodName" />`</span></span>  
  
         `-- or --`  
  
         <span data-ttu-id="65af6-153">`<SoapAction>` *SOAP アクション* `</SoapAction>`</span><span class="sxs-lookup"><span data-stu-id="65af6-153">`<SoapAction>` *soap action* `</SoapAction>`</span></span>  
  
         <span data-ttu-id="65af6-154">省略可能な XML 要素:</span><span class="sxs-lookup"><span data-stu-id="65af6-154">Optional XML Elements:</span></span>  
  
         <span data-ttu-id="65af6-155">`<ElementPath>`  *要素パス*  `</ElementPath>`</span><span class="sxs-lookup"><span data-stu-id="65af6-155">`<ElementPath>`  *element path*  `</ElementPath>`</span></span>  
  
         <span data-ttu-id="65af6-156">`<Method Namespace=`*"namespace"*  `Name="MethodName" />`</span><span class="sxs-lookup"><span data-stu-id="65af6-156">`<Method Namespace=` *"namespace"*  `Name="MethodName" />`</span></span>  
  
         `-- or --`  
  
         <span data-ttu-id="65af6-157">`<SoapAction>` *SOAP アクション* `</SoapAction>`</span><span class="sxs-lookup"><span data-stu-id="65af6-157">`<SoapAction>` *soap action* `</SoapAction>`</span></span>  
  
    -   <span data-ttu-id="65af6-158">**XML ドキュメントの場合:**</span><span class="sxs-lookup"><span data-stu-id="65af6-158">**For an XML document:**</span></span>  
  
         <span data-ttu-id="65af6-159">省略可能な XML 要素:</span><span class="sxs-lookup"><span data-stu-id="65af6-159">Optional XML Elements:</span></span>  
  
         <span data-ttu-id="65af6-160">`<ElementPath>`  *要素パス*  `</ElementPath>`</span><span class="sxs-lookup"><span data-stu-id="65af6-160">`<ElementPath>`  *element path*  `</ElementPath>`</span></span>  
  
    -   <span data-ttu-id="65af6-161">**埋め込み XML ドキュメントの場合:**</span><span class="sxs-lookup"><span data-stu-id="65af6-161">**For an embedded XML document:**</span></span>  
  
         <span data-ttu-id="65af6-162">必須の XML 要素:</span><span class="sxs-lookup"><span data-stu-id="65af6-162">Required XML Elements:</span></span>  
  
         <span data-ttu-id="65af6-163">`<XmlData>` 内部 XML `</XmlData>`</span><span class="sxs-lookup"><span data-stu-id="65af6-163">`<XmlData>` inner XML `</XmlData>`</span></span>  
  
         <span data-ttu-id="65af6-164">省略可能な XML 要素:</span><span class="sxs-lookup"><span data-stu-id="65af6-164">Optional XML Elements:</span></span>  
  
         <span data-ttu-id="65af6-165">`<ElementPath>`  *要素パス*  `</ElementPath>`</span><span class="sxs-lookup"><span data-stu-id="65af6-165">`<ElementPath>`  *element path*  `</ElementPath>`</span></span>  
  
         `-- or --`  
  
         <span data-ttu-id="65af6-166">`<ElementPath IgnoreNamespaces="true">`  *要素パス*  `</ElementPath>`</span><span class="sxs-lookup"><span data-stu-id="65af6-166">`<ElementPath IgnoreNamespaces="true">`  *element path*  `</ElementPath>`</span></span>  
  
 <span data-ttu-id="65af6-167">クエリ構文の詳細については、msdn.microsoft.com にある [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ドキュメント ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [オンライン ブック](https://go.microsoft.com/fwlink/?linkid=121312)) の「[XML レポート データの XML クエリ構文 (SSRS)](report-data-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="65af6-167">For more information about query syntax, see [XML Query Syntax for XML Report Data &#40;SSRS&#41;](report-data-ssrs.md) in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] documentation in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312) on msdn.microsoft.com.</span></span>  
  
 <span data-ttu-id="65af6-168">例については、「 [Reporting Services: XML と Web サービス データ ソースの使用](https://go.microsoft.com/fwlink/?LinkId=81654)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="65af6-168">For examples, see [Reporting Services: Using XML and Web Service Data Sources](https://go.microsoft.com/fwlink/?LinkId=81654).</span></span>  
  
### <a name="requirements-for-retrieving-xml-web-service-data"></a><span data-ttu-id="65af6-169">XML Web サービスのデータを取得するための要件</span><span class="sxs-lookup"><span data-stu-id="65af6-169">Requirements for Retrieving XML Web Service Data</span></span>  
 <span data-ttu-id="65af6-170">これらは XML データ処理拡張機能では検出されません。</span><span class="sxs-lookup"><span data-stu-id="65af6-170">The XML data processing extension does not detect the schema for you.</span></span> <span data-ttu-id="65af6-171">そのため、必要なデータを取得する SOAP メソッドを検索するための、なんらかの手段が必要です。</span><span class="sxs-lookup"><span data-stu-id="65af6-171">Therefore, you must have some way of discovering which SOAP methods will retrieve the data that you want.</span></span> <span data-ttu-id="65af6-172">また、Web サービスがそのデータに対して使用するアドレス指定スキームや名前空間を把握しておく必要もあります。</span><span class="sxs-lookup"><span data-stu-id="65af6-172">You must also understand the addressing scheme or namespace that the Web service uses for its data.</span></span>  
  
 <span data-ttu-id="65af6-173">Web サービスの場合 `Query` は、または SOAP アクションを呼び出すメソッドを指定する <> 要素を提供できます。</span><span class="sxs-lookup"><span data-stu-id="65af6-173">For a Web service, you can provide a <`Query`> element that specifies a method to call or SOAP action.</span></span> <span data-ttu-id="65af6-174">XML データ ソースが、レポートに必要なデータを取得できるような階層構造になっていれば、クエリを空にして、既定のクエリを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="65af6-174">You can leave the query empty and use the default query if the XML data source has a hierarchical structure that produces the data that you want to use for your report.</span></span> <span data-ttu-id="65af6-175">クエリの実行時に取得される XML 要素ノードの値および属性は、レポートに使用されているデータセットのフィールドにマップされます。</span><span class="sxs-lookup"><span data-stu-id="65af6-175">XML element node values and attributes retrieved when the query runs map to the dataset fields you use in your report.</span></span>  
  
### <a name="requirements-for-retrieving-xml-document-data"></a><span data-ttu-id="65af6-176">XML ドキュメントのデータを取得するための要件</span><span class="sxs-lookup"><span data-stu-id="65af6-176">Requirements for Retrieving XML Document Data</span></span>  
 <span data-ttu-id="65af6-177">サーバーから HTTP プロトコルを使って XML データを取得するか、XML データを XML `Query` 要素に埋め込む必要があります。</span><span class="sxs-lookup"><span data-stu-id="65af6-177">Using the http protocol, the server must return XML data or the XML data must be embedded in the XML `Query` element.</span></span> <span data-ttu-id="65af6-178">XML ドキュメントを HTTP プロトコルを使って直接参照する場合、拡張子を .xml にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="65af6-178">If you refer to an XML document directly using the http protocol, the extension must be .xml.</span></span>  
  
 <span data-ttu-id="65af6-179">必要なすべてのデータを取得するための XML クエリの作成方法を理解しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="65af6-179">You must know how to create an XML query that retrieves all the data you need.</span></span> <span data-ttu-id="65af6-180">要素パスを指定しない場合、XML ドキュメントを解析するときの既定の動作では、XML ドキュメントのリーフノード コレクションへの使用可能な最初のパスが選択されます。</span><span class="sxs-lookup"><span data-stu-id="65af6-180">If you do not specify an element path, the default behavior for parsing an XML document is to select the first available path to a leaf-node collection in the XML document.</span></span> <span data-ttu-id="65af6-181">XML ドキュメントに他の兄弟リーフノード コレクションへのパスが含まれている場合、クエリでパスを指定しない限り、それらのノードは無視されます。</span><span class="sxs-lookup"><span data-stu-id="65af6-181">If the XML document includes additional paths to other sibling leaf-node collections, those nodes will be ignored unless you specify a path in your query.</span></span>  
  
 <span data-ttu-id="65af6-182">XQuery と似た XML 構文を使って要素パスを指定できます。</span><span class="sxs-lookup"><span data-stu-id="65af6-182">You can provide an element path using XML syntax similar to XQuery.</span></span>  
  
 <span data-ttu-id="65af6-183">詳細については、msdn.microsoft.com にある [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ドキュメント ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [オンライン ブック](https://go.microsoft.com/fwlink/?linkid=121312)) の「[XML レポート データの要素パス構文 (SSRS)](element-path-syntax-for-xml-report-data-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="65af6-183">For more information, see [Element Path Syntax for XML Report Data &#40;SSRS&#41;](element-path-syntax-for-xml-report-data-ssrs.md) in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] documentation in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312) on msdn.microsoft.com.</span></span>  
  
##  <a name="parameters"></a><a name="Parameters"></a> <span data-ttu-id="65af6-184">パラメーター</span><span class="sxs-lookup"><span data-stu-id="65af6-184">Parameters</span></span>  
 <span data-ttu-id="65af6-185">クエリの解析時にパラメーターは識別されません。</span><span class="sxs-lookup"><span data-stu-id="65af6-185">The query is not analyzed to identify parameters.</span></span>  
  
 <span data-ttu-id="65af6-186">パラメーターを追加するには、 **[データセットのプロパティ]** ダイアログ ボックスの [[パラメーター]](../dataset-properties-dialog-box-parameters-report-builder.md) ページを使用して手動で作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="65af6-186">To add parameters, you must create them manually through the **Parameter** page on the [Dataset Properties](../dataset-properties-dialog-box-parameters-report-builder.md) dialog box.</span></span>  
  
##  <a name="remarks"></a><a name="Remarks"></a> <span data-ttu-id="65af6-187">解説</span><span class="sxs-lookup"><span data-stu-id="65af6-187">Remarks</span></span>  
 <span data-ttu-id="65af6-188">XML データ拡張機能は、階層構造でない表形式の XML データからのレポート作成をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="65af6-188">The XML data extension supports reporting from XML data that is tabular and not hierarchical.</span></span> <span data-ttu-id="65af6-189">詳細については、「[外部データ ソースのデータを追加する (SSRS)](add-data-from-external-data-sources-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="65af6-189">For more information, see [Add Data from External Data Sources &#40;SSRS&#41;](add-data-from-external-data-sources-ssrs.md).</span></span>  
  
 <span data-ttu-id="65af6-190">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースから XML ドキュメントを取得するためのサポートは組み込まれていません。</span><span class="sxs-lookup"><span data-stu-id="65af6-190">There is no built-in support for retrieving XML documents from a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span>  
  
##  <a name="how-to-topics"></a><a name="HowTo"></a><span data-ttu-id="65af6-191">操作方法に関するトピック</span><span class="sxs-lookup"><span data-stu-id="65af6-191">How-To Topics</span></span>  
 <span data-ttu-id="65af6-192">データ接続、データ ソース、およびデータセットを操作する手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="65af6-192">This section contains step-by-step instructions for working with data connections, data sources, and datasets.</span></span>  
  
 [<span data-ttu-id="65af6-193">データ接続またはデータソース &#40;レポートビルダーと SSRS&#41;に追加して検証する</span><span class="sxs-lookup"><span data-stu-id="65af6-193">Add and Verify a Data Connection or Data Source &#40;Report Builder and SSRS&#41;</span></span>](add-and-verify-a-data-connection-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="65af6-194">共有データセットまたは埋め込みデータセットの作成 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="65af6-194">Create a Shared Dataset or Embedded Dataset &#40;Report Builder and SSRS&#41;</span></span>](create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="65af6-195">データセットへのフィルターの追加 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="65af6-195">Add a Filter to a Dataset &#40;Report Builder and SSRS&#41;</span></span>](add-a-filter-to-a-dataset-report-builder-and-ssrs.md)  
  
##  <a name="related-sections"></a><a name="Related"></a> <span data-ttu-id="65af6-196">関連セクション</span><span class="sxs-lookup"><span data-stu-id="65af6-196">Related Sections</span></span>  
 <span data-ttu-id="65af6-197">次に示すセクションでは、レポート データの概念が詳細に説明されているほか、データに関連するレポートのパーツを定義し、カスタマイズし、使用する方法が説明されています。</span><span class="sxs-lookup"><span data-stu-id="65af6-197">These sections of the documentation provide in-depth conceptual information about report data, as well as procedural information about how to define, customize, and use parts of a report that are related to data.</span></span>  
  
 [<span data-ttu-id="65af6-198">レポート &#40;レポートビルダーおよび SSRS&#41;にデータを追加する</span><span class="sxs-lookup"><span data-stu-id="65af6-198">Add Data to a Report &#40;Report Builder and SSRS&#41;</span></span>](report-datasets-ssrs.md)  
 <span data-ttu-id="65af6-199">レポートのデータへのアクセスの概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="65af6-199">Provides an overview of accessing data for your report.</span></span>  
  
 [<span data-ttu-id="65af6-200">レポート ビルダーでのデータ接続、データ ソース、および接続文字列</span><span class="sxs-lookup"><span data-stu-id="65af6-200">Data Connections, Data Sources, and Connection Strings in Report Builder</span></span>](../data-connections-data-sources-and-connection-strings-in-report-builder.md)  
 <span data-ttu-id="65af6-201">データ接続とデータ ソースについて説明します。</span><span class="sxs-lookup"><span data-stu-id="65af6-201">Provides information about data connections and data sources.</span></span>  
  
 [<span data-ttu-id="65af6-202">レポート埋め込みデータセットと共有データセット &#40;レポートビルダーと SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="65af6-202">Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;</span></span>](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
 <span data-ttu-id="65af6-203">埋め込みデータセットと共有データセットについて説明します。</span><span class="sxs-lookup"><span data-stu-id="65af6-203">Provides information about embedded and shared datasets.</span></span>  
  
 [<span data-ttu-id="65af6-204">データセット フィールド コレクション &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="65af6-204">Dataset Fields Collection &#40;Report Builder and SSRS&#41;</span></span>](dataset-fields-collection-report-builder-and-ssrs.md)  
 <span data-ttu-id="65af6-205">クエリによって生成されるデータセット フィールド コレクションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="65af6-205">Provides information about the dataset field collection generated by the query.</span></span>  
  
 <span data-ttu-id="65af6-206">[Reporting Services でサポートされるデータ ソース &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md) ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [オンライン ブックの [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ドキュメント](https://go.microsoft.com/fwlink/?linkid=121312))。</span><span class="sxs-lookup"><span data-stu-id="65af6-206">[Data Sources Supported by Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md) in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] documentation in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312).</span></span>  
 <span data-ttu-id="65af6-207">各データ拡張機能のプラットフォームおよびバージョン サポートに関する詳細な情報です。</span><span class="sxs-lookup"><span data-stu-id="65af6-207">Provides in-depth information about platform and version support for each data extension.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65af6-208">参照</span><span class="sxs-lookup"><span data-stu-id="65af6-208">See Also</span></span>  
 <span data-ttu-id="65af6-209">[レポートパラメーター &#40;レポートビルダーとレポートデザイナー&#41;](../report-design/report-parameters-report-builder-and-report-designer.md) </span><span class="sxs-lookup"><span data-stu-id="65af6-209">[Report Parameters &#40;Report Builder and Report Designer&#41;](../report-design/report-parameters-report-builder-and-report-designer.md) </span></span>  
 <span data-ttu-id="65af6-210">[データのフィルター処理、グループ化、並べ替え &#40;レポートビルダーと SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="65af6-210">[Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="65af6-211">式 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="65af6-211">Expressions &#40;Report Builder and SSRS&#41;</span></span>](../report-design/expressions-report-builder-and-ssrs.md)  
  
  
