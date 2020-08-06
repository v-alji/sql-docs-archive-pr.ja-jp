---
title: XML 一括読み込みの概要 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- nontransacted XML Bulk Load operations
- XML Bulk Load [SQLXML], about XML Bulk Load
- bulk load [SQLXML], about bulk load
- transacted XML Bulk Load operations
- streaming XML data
ms.assetid: 38bd3cbd-65ef-4c23-9ef3-e70ecf6bb88a
author: rothja
ms.author: jroth
ms.openlocfilehash: 4f3e0e78edd967e5fcb7377312c1811d34cb1ef8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711821"
---
# <a name="introduction-to-xml-bulk-load-sqlxml-40"></a><span data-ttu-id="6c6d7-102">XML 一括読み込みの概要 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="6c6d7-102">Introduction to XML Bulk Load (SQLXML 4.0)</span></span>
  <span data-ttu-id="6c6d7-103">XML 一括読み込みは、半構造化 XML データを Microsoft テーブルに読み込むことができるスタンドアロンの COM オブジェクトです [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="6c6d7-103">XML Bulk Load is a stand-alone COM object that allows you to load semistructured XML data into Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tables.</span></span>  
  
 <span data-ttu-id="6c6d7-104">INSERT ステートメントと OPENXML 関数を使用すれば、XML データを [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データベースに挿入できますが、大量の XML データを挿入する必要があるときには、一括読み込みユーティリティを使用すると効率的です。</span><span class="sxs-lookup"><span data-stu-id="6c6d7-104">You can insert XML data into a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database by using an INSERT statement and the OPENXML function; however, the Bulk Load utility provides better performance when you need to insert large amounts of XML data.</span></span>  
  
 <span data-ttu-id="6c6d7-105">XML 一括読み込みオブジェクトモデルの Execute メソッドには、次の2つのパラメーターがあります。</span><span class="sxs-lookup"><span data-stu-id="6c6d7-105">The Execute method of the XML Bulk Load object model takes two parameters:</span></span>  
  
-   <span data-ttu-id="6c6d7-106">注釈付き XML Schema Definition (XSD) または XML-Data Reduced (XDR) スキーマ。</span><span class="sxs-lookup"><span data-stu-id="6c6d7-106">An annotated XML Schema Definition (XSD) or XML-Data Reduced (XDR) schema.</span></span> <span data-ttu-id="6c6d7-107">XML 一括読み込みユーティリティでは、このスキーマで指定されたマッピング スキーマと注釈が解釈され、XML データを挿入する SQL Server テーブルが特定されます。</span><span class="sxs-lookup"><span data-stu-id="6c6d7-107">The XML Bulk Load utility interprets this mapping schema and the annotations that are specified in the schema in identifying the SQL Server tables into which the XML data is to be inserted.</span></span>  
  
-   <span data-ttu-id="6c6d7-108">XML ドキュメント、またはドキュメント フラグメント (単一の最上位要素がないドキュメント)。</span><span class="sxs-lookup"><span data-stu-id="6c6d7-108">An XML document or document fragment (a document fragment is a document without a single top-level element).</span></span> <span data-ttu-id="6c6d7-109">XML 一括読み込みで読み込むことができるファイル名またはストリームを指定できます。</span><span class="sxs-lookup"><span data-stu-id="6c6d7-109">A file name or a stream from which XML Bulk Load can read can be specified.</span></span>  
  
 <span data-ttu-id="6c6d7-110">XML 一括読み込みではマッピング スキーマが解釈されて、XML データを挿入するテーブルが特定されます。</span><span class="sxs-lookup"><span data-stu-id="6c6d7-110">XML Bulk Load interprets the mapping schema and identifies the table(s) into which the XML data is to be inserted.</span></span>  
  
 <span data-ttu-id="6c6d7-111">ユーザーは、次の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 機能について理解していることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="6c6d7-111">It is assumed that you are familiar with the following [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] features:</span></span>  
  
-   <span data-ttu-id="6c6d7-112">注釈付き XSD および XDR スキーマ。</span><span class="sxs-lookup"><span data-stu-id="6c6d7-112">Annotated XSD and XDR schemas.</span></span> <span data-ttu-id="6c6d7-113">注釈付き XSD スキーマの詳細については、「[注釈付き Xsd スキーマの概要 &#40;SQLXML 4.0&#41;](../../sqlxml/annotated-xsd-schemas/introduction-to-annotated-xsd-schemas-sqlxml-4-0.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6c6d7-113">For more information about annotated XSD schemas, see [Introduction to Annotated XSD Schemas &#40;SQLXML 4.0&#41;](../../sqlxml/annotated-xsd-schemas/introduction-to-annotated-xsd-schemas-sqlxml-4-0.md).</span></span> <span data-ttu-id="6c6d7-114">注釈付き XDR スキーマの詳細については、「 [SQLXML 4.0&#41;で非推奨とされた注釈付き Xdr スキーマ &#40;](../../sqlxml/annotated-xsd-schemas/annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6c6d7-114">For information about annotated XDR schemas, see [Annotated XDR Schemas &#40;Deprecated in SQLXML 4.0&#41;](../../sqlxml/annotated-xsd-schemas/annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md).</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="6c6d7-115">の BULK INSERT ステートメント、bcp ユーティリティなどの [!INCLUDE[tsql](../../../includes/tsql-md.md)] 一括挿入メカニズム。</span><span class="sxs-lookup"><span data-stu-id="6c6d7-115">bulk insert mechanisms, such as the [!INCLUDE[tsql](../../../includes/tsql-md.md)] BULK INSERT statement and the bcp utility.</span></span> <span data-ttu-id="6c6d7-116">詳細については、「 [BULK INSERT &#40;transact-sql&#41;](/sql/t-sql/statements/bulk-insert-transact-sql)および[bcp ユーティリティ](../../../tools/bcp-utility.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6c6d7-116">For more information, see [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) and [bcp Utility](../../../tools/bcp-utility.md).</span></span>  
  
## <a name="streaming-of-xml-data"></a><span data-ttu-id="6c6d7-117">XML データのストリーミング</span><span class="sxs-lookup"><span data-stu-id="6c6d7-117">Streaming of XML Data</span></span>  
 <span data-ttu-id="6c6d7-118">ソースの XML ドキュメントは大きい可能性があるため、一括読み込み処理では、メモリにドキュメント全体は読み込まれません。</span><span class="sxs-lookup"><span data-stu-id="6c6d7-118">Because the source XML document can be large, the entire document is not read into memory for bulk load processing.</span></span> <span data-ttu-id="6c6d7-119">代わりに、XML 一括読み込みでは XML データがストリームとして解釈され読み取られます。</span><span class="sxs-lookup"><span data-stu-id="6c6d7-119">Instead, XML Bulk Load interprets the XML data as a stream and reads it.</span></span> <span data-ttu-id="6c6d7-120">データが読み取られるとき、このユーティリティではデータベース テーブルが特定され、XML データ ソースを基に適切なレコードが生成された後、そのレコードが挿入のため [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] に送信されます。</span><span class="sxs-lookup"><span data-stu-id="6c6d7-120">As the utility reads the data, it identifies the database table(s), generates the appropriate record(s) from the XML data source, and then sends the record(s) to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] for insertion.</span></span>  
  
 <span data-ttu-id="6c6d7-121">たとえば、次のソース XML ドキュメントは、 **\<Customer>** 要素と子要素で構成されてい **\<Order>** ます。</span><span class="sxs-lookup"><span data-stu-id="6c6d7-121">For example, the following source XML document consists of **\<Customer>** elements and **\<Order>** child elements:</span></span>  
  
```  
<Customer ...>  
    <Order.../>  
    <Order .../>  
     ...  
</Customer>  
...  
```  
  
 <span data-ttu-id="6c6d7-122">XML 一括読み込みで要素が読み取られると、 **\<Customer>** 顧客テーブルのレコードが生成されます。</span><span class="sxs-lookup"><span data-stu-id="6c6d7-122">As XML Bulk Load reads the **\<Customer>** element, it generates a record for the Customertable.</span></span> <span data-ttu-id="6c6d7-123">**\</Customer>** XML 一括読み込みで終了タグを読み取ると、そのレコードがのテーブルに挿入さ [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] れます。</span><span class="sxs-lookup"><span data-stu-id="6c6d7-123">When it reads the **\</Customer>** end tag, XML Bulk Load inserts that record into the table in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="6c6d7-124">同様に、要素を読み取るときに **\<Order>** 、XML 一括読み込みでは Ordertable のレコードが生成され、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 終了タグの読み取り時にそのレコードがテーブルに挿入され **\</Order>** ます。</span><span class="sxs-lookup"><span data-stu-id="6c6d7-124">In the same way, when it reads the **\<Order>** element, XML Bulk Load generates a record for the Ordertable, and then inserts that record into the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] table upon reading the **\</Order>** end tag.</span></span>  
  
## <a name="transacted-and-nontransacted-xml-bulk-load-operations"></a><span data-ttu-id="6c6d7-125">トランザクション モードとトランザクション以外のモードでの XML 一括読み込みの操作</span><span class="sxs-lookup"><span data-stu-id="6c6d7-125">Transacted and Nontransacted XML Bulk Load Operations</span></span>  
 <span data-ttu-id="6c6d7-126">XML 一括読み込みは、トランザクション モードまたはトランザクション以外のモードで操作できます。</span><span class="sxs-lookup"><span data-stu-id="6c6d7-126">XML Bulk Load can operate in either a transacted or a nontransacted mode.</span></span> <span data-ttu-id="6c6d7-127">トランザクション以外のモードで一括読み込みを行う場合は、通常、次のいずれかの条件に該当する場合に、パフォーマンスが最適です。</span><span class="sxs-lookup"><span data-stu-id="6c6d7-127">Performance is usually optimal if you are bulk loading in a nontransacted mode: that is, the Transaction property is set to FALSE) and either of the following conditions is true:</span></span>  
  
-   <span data-ttu-id="6c6d7-128">データの一括読み込みの対象テーブルが空で、インデックスが作成されていない。</span><span class="sxs-lookup"><span data-stu-id="6c6d7-128">The tables into which the data is bulk loaded are empty with no indexes.</span></span>  
  
-   <span data-ttu-id="6c6d7-129">テーブルにデータと一意のインデックスが格納されている。</span><span class="sxs-lookup"><span data-stu-id="6c6d7-129">The tables have data and unique indexes.</span></span>  
  
 <span data-ttu-id="6c6d7-130">トランザクション以外のモードで一括読み込みを実行する場合は、一括読み込み中に問題が発生したとしてもロールバックは保証されません (ただし、部分ロールバックは実行されることがあります)。</span><span class="sxs-lookup"><span data-stu-id="6c6d7-130">The nontransacted approach does not guarantee a rollback if something goes wrong in the bulk load process (although partial rollbacks can happen).</span></span> <span data-ttu-id="6c6d7-131">トランザクション以外のモードでの一括読み込みは、データベースが空の場合に適しています。</span><span class="sxs-lookup"><span data-stu-id="6c6d7-131">The nontransacted bulk load is appropriate when the database is empty.</span></span> <span data-ttu-id="6c6d7-132">この場合、問題が発生したらデータベースの内容を消去して、XML 一括読み込みを再実行できます。</span><span class="sxs-lookup"><span data-stu-id="6c6d7-132">Therefore, if something does go wrong, you can clean the database and start XML Bulk Load again.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6c6d7-133">トランザクション以外のモードの場合、XML 一括読み込みでは既定の内部トランザクションが使用され、そのトランザクションがコミットされます。</span><span class="sxs-lookup"><span data-stu-id="6c6d7-133">In nontransacted mode, XML Bulk Load uses a default internal transaction and commits it.</span></span> <span data-ttu-id="6c6d7-134">Transaction プロパティが TRUE に設定されている場合、XML 一括読み込みではこのトランザクションで commit が呼び出されません。</span><span class="sxs-lookup"><span data-stu-id="6c6d7-134">When the Transaction property is set to TRUE, XML Bulk Load does not call commit on this transaction.</span></span>  
  
 <span data-ttu-id="6c6d7-135">Transaction プロパティが TRUE に設定されている場合、XML 一括読み込みでは、マッピングスキーマで指定されている各テーブルに1つずつ、一時ファイルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="6c6d7-135">If the Transaction property is set to TRUE, XML Bulk Load creates temporary files, one for each table that is identified in the mapping schema.</span></span> <span data-ttu-id="6c6d7-136">ソース XML ドキュメントからのレコードは、最初に XML 一括読み込みによってこれらの一時ファイルに保存され、</span><span class="sxs-lookup"><span data-stu-id="6c6d7-136">XML Bulk Load first stores the records from the source XML document in these temporary files.</span></span> <span data-ttu-id="6c6d7-137">次に [!INCLUDE[tsql](../../../includes/tsql-md.md)] BULK INSERT ステートメントによって一時ファイルから取得されて、対応するテーブルに保存されます。</span><span class="sxs-lookup"><span data-stu-id="6c6d7-137">Then, a [!INCLUDE[tsql](../../../includes/tsql-md.md)] BULK INSERT statement retrieves these records from the files and stores them in the corresponding tables.</span></span> <span data-ttu-id="6c6d7-138">一時ファイルの場所は、TempFilePath プロパティを使用して指定できます。</span><span class="sxs-lookup"><span data-stu-id="6c6d7-138">You can specify the location for these temporary files by using the TempFilePath property.</span></span> <span data-ttu-id="6c6d7-139">XML 一括読み込みで使用される [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] アカウントからは、このパスにアクセスできる必要があります。</span><span class="sxs-lookup"><span data-stu-id="6c6d7-139">You must ensure that the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] account used with XML Bulk Load has access to this path.</span></span> <span data-ttu-id="6c6d7-140">TempFilePath プロパティが指定されていない場合は、TEMP 環境変数で指定されている既定のファイルパスを使用して一時ファイルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="6c6d7-140">If the TempFilePath property is not specified, the default file path that is specified in the TEMP environment variable is used to create the temporary files.</span></span>  
  
 <span data-ttu-id="6c6d7-141">Transaction プロパティが FALSE (既定の設定) に設定されている場合、XML 一括読み込みでは OLE DB インターフェイス IRowsetFastLoad を使用してデータの一括読み込みを行います。</span><span class="sxs-lookup"><span data-stu-id="6c6d7-141">If the Transaction property is set to FALSE (the default setting), XML Bulk Load uses the OLE DB interface IRowsetFastLoad to bulk load the data.</span></span>  
  
 <span data-ttu-id="6c6d7-142">ConnectionString プロパティによって接続文字列が設定され、Transaction プロパティが TRUE に設定されている場合、XML 一括読み込みは独自のトランザクションコンテキストで動作します。</span><span class="sxs-lookup"><span data-stu-id="6c6d7-142">If the ConnectionString property sets the connection string, and the Transaction property is set to TRUE, XML Bulk Load operates in its own transaction context.</span></span> <span data-ttu-id="6c6d7-143">たとえば、XML 一括読み込みでは自身のトランザクションが開始され、必要に応じてコミットまたはロールバックが行われます。</span><span class="sxs-lookup"><span data-stu-id="6c6d7-143">(For example, XML Bulk Load starts its own transaction, and commits or rolls back as appropriate.)</span></span>  
  
 <span data-ttu-id="6c6d7-144">ConnectionCommand プロパティによって接続が既存の接続オブジェクトに設定されていて、Transaction プロパティが TRUE に設定されている場合、XML 一括読み込みでは、成功または失敗の場合、それぞれ COMMIT ステートメントまたは ROLLBACK ステートメントは発行されません。</span><span class="sxs-lookup"><span data-stu-id="6c6d7-144">If the ConnectionCommand property sets the connection with an existing connection object and the Transaction property is set to TRUE, XML Bulk Load does not issue a COMMIT or ROLLBACK statement in the case of a success or a failure, respectively.</span></span> <span data-ttu-id="6c6d7-145">エラーが発生した場合、XML 一括読み込みでは適切なエラー メッセージが返されます。</span><span class="sxs-lookup"><span data-stu-id="6c6d7-145">If there is an error, XML Bulk Load returns the appropriate error message.</span></span> <span data-ttu-id="6c6d7-146">COMMIT または ROLLBACK ステートメントを発行するかどうかは、一括読み込みを実行したクライアントで決定されます。</span><span class="sxs-lookup"><span data-stu-id="6c6d7-146">The decision to issue a COMMIT or ROLLBACK statement is left to the client that initiated the bulk load.</span></span> <span data-ttu-id="6c6d7-147">XML 一括読み込みに使用される接続オブジェクトは、ICommand 型であるか、または ADO コマンドオブジェクトである必要があります。</span><span class="sxs-lookup"><span data-stu-id="6c6d7-147">The connection object that is used for XML Bulk Load should be of type ICommand or be an ADO command object.</span></span>  
  
 <span data-ttu-id="6c6d7-148">SQLXML 4.0 では、ConnectionObject は、Transaction プロパティを FALSE に設定して使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="6c6d7-148">In SQLXML 4.0, a ConnectionObject cannot be used with the Transaction property set to FALSE.</span></span> <span data-ttu-id="6c6d7-149">非トランザクションモードは、渡されたセッションで複数の IRowsetFastLoad インターフェイスを開くことができないため、ConnectionObject ではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="6c6d7-149">The nontransacted mode is not supported with a ConnectionObject because it is impossible to open more than one IRowsetFastLoad interface on a passed-in session.</span></span>  
  
  
