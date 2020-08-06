---
title: SqlXmlCommand オブジェクト (SQLXML マネージクラス) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- void ExecuteNonQuery() method
- namespaces property
- Stream ExecuteStream() method
- CommandType property
- RootTag property
- OutputEncoding property
- XmlReader ExecuteXmlReader() method
- Managed Classes [SQLXML], SqlXmlCommand object
- SQLXML Managed Classes, SqlXmlCommand object
- Base Path property
- void ClearParameters() method
- public void ExecuteToStream(Stream outputStream) method
- SqlXmlCommand object
- CommandText property
- XslPath property
- SchemaPath property
- SqlXmlParameter CreateParameter() method
- ClientSideXML property
- CommandStream property
ms.assetid: c1f9e0bb-a89d-4d6a-a96e-289ef516a3a6
author: rothja
ms.author: jroth
ms.openlocfilehash: 78b72581f549ea007dae0cdc7044fd9a809920af
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641533"
---
# <a name="sqlxmlcommand-object-sqlxml-managed-classes"></a><span data-ttu-id="cf51e-102">SqlXmlCommand オブジェクト (SQLXML マネージド クラス)</span><span class="sxs-lookup"><span data-stu-id="cf51e-102">SqlXmlCommand Object (SQLXML Managed Classes)</span></span>
  <span data-ttu-id="cf51e-103">SqlXmlCommand オブジェクトのコンストラクターを次に示します。</span><span class="sxs-lookup"><span data-stu-id="cf51e-103">This is the constructor for the SqlXmlCommand object:</span></span>  
  
```  
public SqlXmlCommand(string cnString)  
```  
  
 <span data-ttu-id="cf51e-104">ここで、 `cnString` は、サーバー、データベース、およびログイン情報を識別する ADO または OLEDB の接続文字列です (例:) `Provider=SQLOLEDB; Server=(local); database=AdventureWorks; Integrated Security=SSPI"` 。</span><span class="sxs-lookup"><span data-stu-id="cf51e-104">Where `cnString` is the ADO or OLEDB connection string that identifies the server, database, and the login information-for example, `Provider=SQLOLEDB; Server=(local); database=AdventureWorks; Integrated Security=SSPI"`.</span></span>  
  
 <span data-ttu-id="cf51e-105">接続文字列では、`Provider` に SQLOLEDB を指定する必要があります。プロバイダーの文字列に `Data Provider` は使用できません。</span><span class="sxs-lookup"><span data-stu-id="cf51e-105">In the connection string, the `Provider` must be SQLOLEDB and the `Data Provider` should not be included in the provider string).</span></span>  
  
 <span data-ttu-id="cf51e-106">実際のサンプルについては、「 [SQL クエリの実行 &#40;SQLXML マネージクラス&#41;](sqlxml-4-0-net-framework-support-managed-classes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cf51e-106">For a working sample, see [Executing SQL Queries &#40;SQLXML Managed Classes&#41;](sqlxml-4-0-net-framework-support-managed-classes.md).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cf51e-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="cf51e-107">Methods</span></span>  
 <span data-ttu-id="cf51e-108">コマンドを実行するための次のメソッドを含む、複数のメソッドがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="cf51e-108">TheSqlXmlCommand object supports several methods, including the following methods for executing a command:</span></span>  
  
 <span data-ttu-id="cf51e-109">void ExecuteNonQuery ()</span><span class="sxs-lookup"><span data-stu-id="cf51e-109">void ExecuteNonQuery()</span></span>  
 <span data-ttu-id="cf51e-110">コマンドを実行しますが、何も返しません。</span><span class="sxs-lookup"><span data-stu-id="cf51e-110">Executes the command, but does not return anything.</span></span> <span data-ttu-id="cf51e-111">このメソッドは、クエリ以外のコマンド (何も返さないコマンド) を実行する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="cf51e-111">This method is useful if you want to execute a nonquery command (that is, a command that does not return anything).</span></span> <span data-ttu-id="cf51e-112">たとえば、アップデートグラムや DiffGram でレコードを更新し、何も返さない場合に使用できます。</span><span class="sxs-lookup"><span data-stu-id="cf51e-112">An example is executing an updategram or a DiffGram that updates records but returns nothing.</span></span>  
  
 <span data-ttu-id="cf51e-113">Stream ExecuteStream ()</span><span class="sxs-lookup"><span data-stu-id="cf51e-113">Stream ExecuteStream()</span></span>  
 <span data-ttu-id="cf51e-114">新しいストリームオブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="cf51e-114">Returns a new Stream object.</span></span> <span data-ttu-id="cf51e-115">このメソッドは、クエリ結果を新しいストリームで返す場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="cf51e-115">This method is useful when you want the query results returned to you in a new stream.</span></span> <span data-ttu-id="cf51e-116">実際のサンプルについては、「 [SQL クエリの実行 &#40;SQLXML マネージクラス&#41;](sqlxml-4-0-net-framework-support-managed-classes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cf51e-116">For a working sample, see [Executing SQL Queries &#40;SQLXML Managed Classes&#41;](sqlxml-4-0-net-framework-support-managed-classes.md).</span></span>  
  
 <span data-ttu-id="cf51e-117">public void ExecuteToStream (Stream outputStream)</span><span class="sxs-lookup"><span data-stu-id="cf51e-117">public void ExecuteToStream(Stream outputStream)</span></span>  
 <span data-ttu-id="cf51e-118">クエリ結果を既存のストリームに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="cf51e-118">Writes the query results to an existing stream.</span></span> <span data-ttu-id="cf51e-119">このメソッドは、結果を追加する必要があるストリームがある場合に便利です (たとえば、クエリ結果が Httpresponse.cache に書き込まれるようにする場合など)。</span><span class="sxs-lookup"><span data-stu-id="cf51e-119">This method is useful when you have a stream to which you need the results appended (for example, to have the query results written to the System.Web.HttpResponse.OutputStream).</span></span> <span data-ttu-id="cf51e-120">実際のサンプルについては、「 [SQL クエリの実行 &#40;SQLXML マネージクラス&#41;](sqlxml-4-0-net-framework-support-managed-classes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cf51e-120">For a working sample, see [Executing SQL Queries &#40;SQLXML Managed Classes&#41;](sqlxml-4-0-net-framework-support-managed-classes.md).</span></span>  
  
 <span data-ttu-id="cf51e-121">XmlReader ExecuteXmlReader ()</span><span class="sxs-lookup"><span data-stu-id="cf51e-121">XmlReader ExecuteXmlReader()</span></span>  
 <span data-ttu-id="cf51e-122">XmlReader オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="cf51e-122">Returns an XmlReader object.</span></span> <span data-ttu-id="cf51e-123">このメソッドを使用すると、XmlReader オブジェクトのデータを直接操作したり、System.Xml の chainable アーキテクチャにプラグインしたりすることができます。</span><span class="sxs-lookup"><span data-stu-id="cf51e-123">You can use this method to either manipulate data in the XmlReader object directly or plug in the chainable architecture of System.Xml.</span></span> <span data-ttu-id="cf51e-124">詳細については、[!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework のドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="cf51e-124">For more information, see the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework documentation.</span></span> <span data-ttu-id="cf51e-125">実際のサンプルについては、「 [ExecuteXMLReader メソッドを使用した SQL クエリの実行](executing-sql-queries-by-using-the-executexmlreader-method.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cf51e-125">For a working sample, see [Executing SQL Queries by Using the ExecuteXMLReader Method](executing-sql-queries-by-using-the-executexmlreader-method.md).</span></span>  
  
 <span data-ttu-id="cf51e-126">また、次の追加メソッドもサポートしています。</span><span class="sxs-lookup"><span data-stu-id="cf51e-126">TheSqlXmlCommand object also supports these additional methods:</span></span>  
  
 <span data-ttu-id="cf51e-127">SqlXmlParameter CreateParameter ()</span><span class="sxs-lookup"><span data-stu-id="cf51e-127">SqlXmlParameter CreateParameter()</span></span>  
 <span data-ttu-id="cf51e-128">SqlXmlParameter オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="cf51e-128">Creates an SqlXmlParameter object.</span></span> <span data-ttu-id="cf51e-129">このオブジェクトの*名前*と*値*のパラメーターの値を設定できます。</span><span class="sxs-lookup"><span data-stu-id="cf51e-129">You can set values for the *Name* and *Value* parameters of this object.</span></span> <span data-ttu-id="cf51e-130">このメソッドは、コマンドにパラメーターを渡す場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="cf51e-130">This method is useful if you want to pass parameters to a command.</span></span> <span data-ttu-id="cf51e-131">実際のサンプルについては、「 [SQL クエリの実行 &#40;SQLXML マネージクラス&#41;](sqlxml-4-0-net-framework-support-managed-classes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cf51e-131">For a working sample, see [Executing SQL Queries &#40;SQLXML Managed Classes&#41;](sqlxml-4-0-net-framework-support-managed-classes.md).</span></span>  
  
 <span data-ttu-id="cf51e-132">void ClearParameters ()</span><span class="sxs-lookup"><span data-stu-id="cf51e-132">void ClearParameters()</span></span>  
 <span data-ttu-id="cf51e-133">指定したコマンド オブジェクトに作成されたパラメーターを消去します。</span><span class="sxs-lookup"><span data-stu-id="cf51e-133">Clears parameter(s) that were created for a given command object.</span></span> <span data-ttu-id="cf51e-134">このメソッドは、同一のコマンド オブジェクトで複数のクエリを実行する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="cf51e-134">This method is useful if you want to execute multiple queries on the same command object.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="cf51e-135">Properties</span><span class="sxs-lookup"><span data-stu-id="cf51e-135">Properties</span></span>  
 <span data-ttu-id="cf51e-136">SqlXmlCommand オブジェクトは、次のプロパティもサポートしています。</span><span class="sxs-lookup"><span data-stu-id="cf51e-136">The SqlXmlCommand object also supports these properties:</span></span>  
  
 <span data-ttu-id="cf51e-137">ClientSideXml</span><span class="sxs-lookup"><span data-stu-id="cf51e-137">ClientSideXml</span></span>  
 <span data-ttu-id="cf51e-138">True に設定すると、サーバーではなくクライアント側で、行セットが XML に変換されます。</span><span class="sxs-lookup"><span data-stu-id="cf51e-138">When set to True, specifies that conversion of the rowset to XML is to occur on the client instead of on the server.</span></span> <span data-ttu-id="cf51e-139">このプロパティは、パフォーマンスの負荷を中間層に移す場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="cf51e-139">This property is useful when you want to move the performance load to the middle tier.</span></span> <span data-ttu-id="cf51e-140">このプロパティを使用すると、既存のストアド プロシージャを FOR XML でラップして XML に出力することもできます。</span><span class="sxs-lookup"><span data-stu-id="cf51e-140">The property also allows you to wrap the existing stored procedures with FOR XML to get XML output.</span></span>  
  
 <span data-ttu-id="cf51e-141">SchemaPath</span><span class="sxs-lookup"><span data-stu-id="cf51e-141">SchemaPath</span></span>  
 <span data-ttu-id="cf51e-142">マッピング スキーマの名前とディレクトリ パス (C:\x\y\MySchema.xml など) を指定します。</span><span class="sxs-lookup"><span data-stu-id="cf51e-142">The name of the mapping schema along with the directory path (for example, C:\x\y\MySchema.xml).</span></span> <span data-ttu-id="cf51e-143">このプロパティは、XPath クエリにマッピング スキーマを指定するときに便利です。</span><span class="sxs-lookup"><span data-stu-id="cf51e-143">This property is useful for specifying a mapping schema for XPath queries.</span></span> <span data-ttu-id="cf51e-144">パスは、相対パスまたは絶対パスで指定できます。</span><span class="sxs-lookup"><span data-stu-id="cf51e-144">The path that is specified can be absolute or relative.</span></span> <span data-ttu-id="cf51e-145">パスが相対パスの場合は、ベースパスに指定されているベースパスを使用して相対パスが解決されます。</span><span class="sxs-lookup"><span data-stu-id="cf51e-145">If the path is relative, the base path that is specified in Base Path is used to resolve the relative path.</span></span> <span data-ttu-id="cf51e-146">基本パスが指定されていない場合、相対パスは現在のディレクトリからのパスになります。</span><span class="sxs-lookup"><span data-stu-id="cf51e-146">If no base path is specified, the relative path is relative to the current directory.</span></span> <span data-ttu-id="cf51e-147">実際のサンプルについては、「 [.Net 環境での SQLXML 機能へのアクセス](accessing-sqlxml-functionality-in-the-net-environment.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cf51e-147">For a working sample, see [Accessing SQLXML Functionality in the .NET Environment](accessing-sqlxml-functionality-in-the-net-environment.md).</span></span>  
  
 <span data-ttu-id="cf51e-148">XslPath</span><span class="sxs-lookup"><span data-stu-id="cf51e-148">XslPath</span></span>  
 <span data-ttu-id="cf51e-149">XSL ファイルの名前とディレクトリ パスを指定します。</span><span class="sxs-lookup"><span data-stu-id="cf51e-149">The name of the XSL file along with the directory path.</span></span> <span data-ttu-id="cf51e-150">パスは、相対パスまたは絶対パスで指定できます。</span><span class="sxs-lookup"><span data-stu-id="cf51e-150">The path that is specified can be absolute or relative.</span></span> <span data-ttu-id="cf51e-151">パスが相対パスの場合は、ベースパスに指定されているベースパスを使用して相対パスが解決されます。</span><span class="sxs-lookup"><span data-stu-id="cf51e-151">If the path is relative, the base path that is specified in Base Path is used to resolve the relative path.</span></span> <span data-ttu-id="cf51e-152">基本パスが指定されていない場合、相対パスは現在のディレクトリからのパスになります。</span><span class="sxs-lookup"><span data-stu-id="cf51e-152">If no base path is specified, the relative path is relative to the current directory.</span></span> <span data-ttu-id="cf51e-153">実際のサンプルについては、「 [&#40;SQLXML マネージクラス&#41;の XSL 変換の適用](applying-an-xsl-transformation-sqlxml-managed-classes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cf51e-153">For a working sample, see [Applying an XSL Transformation &#40;SQLXML Managed Classes&#41;](applying-an-xsl-transformation-sqlxml-managed-classes.md).</span></span>  
  
 <span data-ttu-id="cf51e-154">基本パス</span><span class="sxs-lookup"><span data-stu-id="cf51e-154">Base Path</span></span>  
 <span data-ttu-id="cf51e-155">基本パス (ディレクトリ パス) を指定します。</span><span class="sxs-lookup"><span data-stu-id="cf51e-155">The base path (a directory path).</span></span> <span data-ttu-id="cf51e-156">このプロパティは、(XslPath プロパティを使用して) XSL ファイルに指定されている相対パス、マッピングスキーマファイル (SchemaPath プロパティを使用)、または XML テンプレート内の外部スキーマ参照 (属性を使用して指定) を解決するのに役立ち `mapping-schema` ます。</span><span class="sxs-lookup"><span data-stu-id="cf51e-156">This property is useful for resolving a relative path that is specified for an XSL file (by using the XslPath property), a mapping schema file (by using the SchemaPath property), or an external schema reference in an XML template (specified by using the `mapping-schema` attribute).</span></span>  
  
 <span data-ttu-id="cf51e-157">OutputEncoding</span><span class="sxs-lookup"><span data-stu-id="cf51e-157">OutputEncoding</span></span>  
 <span data-ttu-id="cf51e-158">コマンドを実行したときに返されるストリームのエンコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="cf51e-158">Specifies the encoding for the stream that is returned when the command executes.</span></span> <span data-ttu-id="cf51e-159">このプロパティは、返されるストリームに特定のエンコードを要求する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="cf51e-159">This property is useful for requesting a specific encoding for the stream that is returned.</span></span> <span data-ttu-id="cf51e-160">一般的に使用されるエンコードには、UTF-8、ANSI、Unicode などがあります。</span><span class="sxs-lookup"><span data-stu-id="cf51e-160">Some commonly used encodings are UTF-8, ANSI, and Unicode.</span></span> <span data-ttu-id="cf51e-161">既定のエンコードは UTF-8 です。</span><span class="sxs-lookup"><span data-stu-id="cf51e-161">UTF-8 is the default encoding.</span></span>  
  
 <span data-ttu-id="cf51e-162">名前空間</span><span class="sxs-lookup"><span data-stu-id="cf51e-162">Namespaces</span></span>  
 <span data-ttu-id="cf51e-163">名前空間を使用する XPath クエリの実行を有効にします。</span><span class="sxs-lookup"><span data-stu-id="cf51e-163">Enables the execution of XPath queries that use namespaces.</span></span> <span data-ttu-id="cf51e-164">名前空間を使用した XPath クエリの詳細については、「[名前空間を使用した Xpath クエリの実行 &#40;SQLXML マネージクラス&#41;](executing-xpath-queries-with-namespaces-sqlxml-managed-classes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cf51e-164">For more information about XPath queries with namespaces, see [Executing XPath Queries with Namespaces &#40;SQLXML Managed Classes&#41;](executing-xpath-queries-with-namespaces-sqlxml-managed-classes.md).</span></span> <span data-ttu-id="cf51e-165">実際のサンプルについては、「 [&#40;SQLXML マネージクラス&#41;の XPath クエリの実行](executing-xpath-queries-sqlxml-managed-classes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cf51e-165">For a working sample, see [Executing XPath Queries &#40;SQLXML Managed Classes&#41;](executing-xpath-queries-sqlxml-managed-classes.md).</span></span>  
  
 <span data-ttu-id="cf51e-166">RootTag</span><span class="sxs-lookup"><span data-stu-id="cf51e-166">RootTag</span></span>  
 <span data-ttu-id="cf51e-167">コマンドを実行して生成される XML の、単一のルート要素を指定します。</span><span class="sxs-lookup"><span data-stu-id="cf51e-167">Provides the single root element for XML generated by command execution.</span></span> <span data-ttu-id="cf51e-168">有効な XML ドキュメントには、単一のルートレベルのタグが必要です。</span><span class="sxs-lookup"><span data-stu-id="cf51e-168">A valid XML document requires a single root-level tag.</span></span> <span data-ttu-id="cf51e-169">このプロパティでは、コマンドを実行して単一の最上位要素のない XML フラグメントが生成された場合に、返される XML のルート要素を指定できます。</span><span class="sxs-lookup"><span data-stu-id="cf51e-169">If the command executed generates an XML fragment (without a single top-level element) you can specify a root element for the returning XML.</span></span> <span data-ttu-id="cf51e-170">実際のサンプルについては、「 [&#40;SQLXML マネージクラス&#41;の XSL 変換の適用](applying-an-xsl-transformation-sqlxml-managed-classes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cf51e-170">For a working sample, see [Applying an XSL Transformation &#40;SQLXML Managed Classes&#41;](applying-an-xsl-transformation-sqlxml-managed-classes.md).</span></span>  
  
 <span data-ttu-id="cf51e-171">CommandText</span><span class="sxs-lookup"><span data-stu-id="cf51e-171">CommandText</span></span>  
 <span data-ttu-id="cf51e-172">コマンドのテキストを指定します。</span><span class="sxs-lookup"><span data-stu-id="cf51e-172">The text of the command.</span></span> <span data-ttu-id="cf51e-173">このプロパティは、実行するコマンドのテキストを指定するときに使用します。</span><span class="sxs-lookup"><span data-stu-id="cf51e-173">This property is used for specifying the text of the command you want to execute.</span></span> <span data-ttu-id="cf51e-174">実際のサンプルについては、「 [SQL クエリの実行 &#40;SQLXML マネージクラス&#41;](sqlxml-4-0-net-framework-support-managed-classes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cf51e-174">For a working sample, see [Executing SQL Queries &#40;SQLXML Managed Classes&#41;](sqlxml-4-0-net-framework-support-managed-classes.md).</span></span>  
  
 <span data-ttu-id="cf51e-175">CommandStream</span><span class="sxs-lookup"><span data-stu-id="cf51e-175">CommandStream</span></span>  
 <span data-ttu-id="cf51e-176">コマンド ストリームを指定します。</span><span class="sxs-lookup"><span data-stu-id="cf51e-176">The command stream.</span></span> <span data-ttu-id="cf51e-177">このプロパティは、XML テンプレートなどのファイルからコマンドを実行する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="cf51e-177">This property is useful if you want to execute a command from a file (for example, an XML template).</span></span> <span data-ttu-id="cf51e-178">CommandStream を使用している場合は、 **"Template"**、 **"アップデートグラム"** 、および **"DiffGram" の CommandType**値のみがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="cf51e-178">When you are using CommandStream, only **"Template"**, **"UpdateGram"** and **"DiffGram"CommandType** values are supported.</span></span> <span data-ttu-id="cf51e-179">実際のサンプルについては、「 [CommandStream プロパティを使用したテンプレートファイルの実行](executing-template-files-by-using-the-commandstream-property.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cf51e-179">For a working sample, see [Executing Template Files by Using the CommandStream Property](executing-template-files-by-using-the-commandstream-property.md).</span></span>  
  
 <span data-ttu-id="cf51e-180">CommandType</span><span class="sxs-lookup"><span data-stu-id="cf51e-180">CommandType</span></span>  
 <span data-ttu-id="cf51e-181">コマンドの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="cf51e-181">Identifies the type of command.</span></span> <span data-ttu-id="cf51e-182">このプロパティは、実行するコマンドの種類を指定するときに使用します。</span><span class="sxs-lookup"><span data-stu-id="cf51e-182">This property is used for specifying the type of command you want to execute.</span></span> <span data-ttu-id="cf51e-183">コマンドの種類の値を、次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="cf51e-183">The values in the following table determine the type of the command.</span></span> <span data-ttu-id="cf51e-184">実際のサンプルについては、「 [.Net 環境での SQLXML 機能へのアクセス](accessing-sqlxml-functionality-in-the-net-environment.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cf51e-184">For a working sample, see [Accessing SQLXML Functionality in the .NET Environment](accessing-sqlxml-functionality-in-the-net-environment.md).</span></span>  
  
|<span data-ttu-id="cf51e-185">値</span><span class="sxs-lookup"><span data-stu-id="cf51e-185">Value</span></span>|<span data-ttu-id="cf51e-186">説明</span><span class="sxs-lookup"><span data-stu-id="cf51e-186">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="cf51e-187">SqlXmlCommandType .Sql</span><span class="sxs-lookup"><span data-stu-id="cf51e-187">SqlXmlCommandType.Sql</span></span>|<span data-ttu-id="cf51e-188">SQL コマンド (`SELECT * FROM Employees FOR XML AUTO` など) を実行します。</span><span class="sxs-lookup"><span data-stu-id="cf51e-188">Executes an SQL command (for example, `SELECT * FROM Employees FOR XML AUTO`).</span></span>|  
|<span data-ttu-id="cf51e-189">SqlXmlCommandType. XPath</span><span class="sxs-lookup"><span data-stu-id="cf51e-189">SqlXmlCommandType.XPath</span></span>|<span data-ttu-id="cf51e-190">XPath コマンド (`Employees[@EmployeeID=1]` など) を実行します。</span><span class="sxs-lookup"><span data-stu-id="cf51e-190">Executes an XPath command (for example, `Employees[@EmployeeID=1]`).</span></span>|  
|<span data-ttu-id="cf51e-191">SqlXmlCommandType. テンプレート</span><span class="sxs-lookup"><span data-stu-id="cf51e-191">SqlXmlCommandType.Template</span></span>|<span data-ttu-id="cf51e-192">XML テンプレートを実行します。</span><span class="sxs-lookup"><span data-stu-id="cf51e-192">Executes an XML template.</span></span>|  
|<span data-ttu-id="cf51e-193">SqlXmlCommandType. TemplateFile</span><span class="sxs-lookup"><span data-stu-id="cf51e-193">SqlXmlCommandType.TemplateFile</span></span>|<span data-ttu-id="cf51e-194">指定したパスにあるテンプレート ファイルを実行します。</span><span class="sxs-lookup"><span data-stu-id="cf51e-194">Executes a template file at the specified path.</span></span>|  
|<span data-ttu-id="cf51e-195">SqlXmlCommandType. アップデートグラム</span><span class="sxs-lookup"><span data-stu-id="cf51e-195">SqlXmlCommandType.UpdateGram</span></span>|<span data-ttu-id="cf51e-196">アップデートグラムを実行します。</span><span class="sxs-lookup"><span data-stu-id="cf51e-196">Executes an updategram.</span></span>|  
|<span data-ttu-id="cf51e-197">SqlXmlCommandType. Diffgram</span><span class="sxs-lookup"><span data-stu-id="cf51e-197">SqlXmlCommandType.Diffgram</span></span>|<span data-ttu-id="cf51e-198">DiffGram を実行します。</span><span class="sxs-lookup"><span data-stu-id="cf51e-198">Executes a DiffGram.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cf51e-199">参照</span><span class="sxs-lookup"><span data-stu-id="cf51e-199">See Also</span></span>  
 <span data-ttu-id="cf51e-200">[SqlXmlParameter オブジェクト &#40;SQLXML マネージクラス&#41;](sqlxml-managed-classes-sqlxmlparameter-object.md) </span><span class="sxs-lookup"><span data-stu-id="cf51e-200">[SqlXmlParameter Object &#40;SQLXML Managed Classes&#41;](sqlxml-managed-classes-sqlxmlparameter-object.md) </span></span>  
 [<span data-ttu-id="cf51e-201">SqlXmlAdapter オブジェクト &#40;SQLXML マネージクラス&#41;</span><span class="sxs-lookup"><span data-stu-id="cf51e-201">SqlXmlAdapter Object &#40;SQLXML Managed Classes&#41;</span></span>](sqlxml-managed-classes-sqlxmladapter-object.md)  
  
  
