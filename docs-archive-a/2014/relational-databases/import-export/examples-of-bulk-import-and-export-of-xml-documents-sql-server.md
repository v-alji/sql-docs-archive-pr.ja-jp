---
title: XML ドキュメントの一括インポートと一括エクスポートの例 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- field terminators [SQL Server]
- bulk importing [SQL Server], data formats
- row terminators [SQL Server]
- OPENROWSET function, XML bulk load
- terminators [SQL Server]
- bulk exporting [SQL Server], data formats
- XML bulk load [SQL Server]
ms.assetid: dff99404-a002-48ee-910e-f37f013d946d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d72c84a7ed84503e0c88d2a46c808196903900b4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643353"
---
# <a name="examples-of-bulk-import-and-export-of-xml-documents-sql-server"></a><span data-ttu-id="51072-102">XML ドキュメントの一括インポートと一括エクスポートの例 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="51072-102">Examples of Bulk Import and Export of XML Documents (SQL Server)</span></span>
    
##  <a name="you-can-bulk-import-xml-documents-into-a-ssnoversion-database-or-bulk-export-them-from-a-ssnoversion-database-this-topic-provides-examples-of-both"></a><a name="top"></a><span data-ttu-id="51072-103">XML ドキュメントは、データベースに一括インポートすることも、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースから一括エクスポートすることもでき [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="51072-103">You can bulk import XML documents into a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database or bulk export them from a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span> <span data-ttu-id="51072-104">このトピックではその両方の例を示します。</span><span class="sxs-lookup"><span data-stu-id="51072-104">This topic provides examples of both.</span></span>  
  
 <span data-ttu-id="51072-105">データ ファイルから [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のテーブルまたはパーティション分割されていないビューにデータを一括インポートする場合、次の機能を使用できます。</span><span class="sxs-lookup"><span data-stu-id="51072-105">To bulk import data from a data file into a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table or non-partitioned view, you can use the following:</span></span>  
  
-   <span data-ttu-id="51072-106">**bcp** ユーティリティ</span><span class="sxs-lookup"><span data-stu-id="51072-106">**bcp** utility</span></span>  
  
     <span data-ttu-id="51072-107">**bcp** ユーティリティは、パーティション分割されたビューを含めて、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースで SELECT ステートメントが機能する任意の場所からデータをエクスポートするためにも使用できます。</span><span class="sxs-lookup"><span data-stu-id="51072-107">You can also use the **bcp** utility to export data from anywhere in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database that a SELECT statement works, including partitioned views.</span></span>  
  
-   <span data-ttu-id="51072-108">BULK INSERT</span><span class="sxs-lookup"><span data-stu-id="51072-108">BULK INSERT</span></span>  
  
-   <span data-ttu-id="51072-109">INSERT ...SELECT \* FROM OPENROWSET(BULK...)</span><span class="sxs-lookup"><span data-stu-id="51072-109">INSERT ... SELECT \* FROM OPENROWSET(BULK...)</span></span>  
  
 <span data-ttu-id="51072-110">詳細については、「 [Bcp ユーティリティ&#41;SQL Server &#40;使用した一括データのインポートとエクスポート](import-and-export-bulk-data-by-using-the-bcp-utility-sql-server.md)」を参照してください。[また、BULK INSERT または OPENROWSET&#40;bulk... &#41; &#40;SQL Server&#41;を使用](import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md)して一括データをインポートすることもできます。</span><span class="sxs-lookup"><span data-stu-id="51072-110">For more information, see [Import and Export Bulk Data by Using the bcp Utility &#40;SQL Server&#41;](import-and-export-bulk-data-by-using-the-bcp-utility-sql-server.md) and [Import Bulk Data by Using BULK INSERT or OPENROWSET&#40;BULK...&#41; &#40;SQL Server&#41;](import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="51072-111">例</span><span class="sxs-lookup"><span data-stu-id="51072-111">Examples</span></span>  
 <span data-ttu-id="51072-112">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="51072-112">The examples are the following:</span></span>  
  
-   <span data-ttu-id="51072-113">A.</span><span class="sxs-lookup"><span data-stu-id="51072-113">A.</span></span> [<span data-ttu-id="51072-114">バイナリバイトストリームとしての XML データの一括インポート</span><span class="sxs-lookup"><span data-stu-id="51072-114">BULK importing XML data as a binary byte stream</span></span>](#binary_byte_stream)  
  
-   <span data-ttu-id="51072-115">B.</span><span class="sxs-lookup"><span data-stu-id="51072-115">B.</span></span> [<span data-ttu-id="51072-116">既存の行への XML データの一括インポート</span><span class="sxs-lookup"><span data-stu-id="51072-116">Bulk importing XML data in an existing row</span></span>](#existing_row)  
  
-   <span data-ttu-id="51072-117">C.</span><span class="sxs-lookup"><span data-stu-id="51072-117">C.</span></span> [<span data-ttu-id="51072-118">DTD を含むファイルからの XML データの一括インポート</span><span class="sxs-lookup"><span data-stu-id="51072-118">Bulk importing XML data from a file that contains a DTD</span></span>](#file_contains_dtd)  
  
-   <span data-ttu-id="51072-119">D.</span><span class="sxs-lookup"><span data-stu-id="51072-119">D.</span></span> [<span data-ttu-id="51072-120">フォーマットファイルを使用してフィールドターミネータを明示的に指定する</span><span class="sxs-lookup"><span data-stu-id="51072-120">Specifying the field terminator explicitly using a format file</span></span>](#field_terminator_in_format_file)  
  
-   <span data-ttu-id="51072-121">E.</span><span class="sxs-lookup"><span data-stu-id="51072-121">E.</span></span> [<span data-ttu-id="51072-122">XML データの一括エクスポート</span><span class="sxs-lookup"><span data-stu-id="51072-122">Bulk exporting XML data</span></span>](#bulk_export_xml_data)  
  
###  <a name="a-bulk-importing-xml-data-as-a-binary-byte-stream"></a><a name="binary_byte_stream"></a> <span data-ttu-id="51072-123">A.</span><span class="sxs-lookup"><span data-stu-id="51072-123">A.</span></span> <span data-ttu-id="51072-124">バイナリ バイト ストリームとして XML の一括インポートを行う</span><span class="sxs-lookup"><span data-stu-id="51072-124">Bulk importing XML data as a binary byte stream</span></span>  
 <span data-ttu-id="51072-125">適用するエンコード宣言が含まれているファイルから XML データの一括インポートを行うときは、OPENROWSET(BULK...) 句で SINGLE_BLOB オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="51072-125">When you bulk import XML data from a file that contains an encoding declaration that you want to apply, specify the SINGLE_BLOB option in the OPENROWSET(BULK...) clause.</span></span> <span data-ttu-id="51072-126">SINGLE_BLOB オプションが指定されていると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の XML パーサーは XML 宣言で指定されたエンコード体系に従ってデータをインポートします。</span><span class="sxs-lookup"><span data-stu-id="51072-126">The SINGLE_BLOB option makes sure that the XML parser in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] imports the data according to the encoding scheme specified in the XML declaration.</span></span>  
  
#### <a name="sample-table"></a><span data-ttu-id="51072-127">サンプル テーブル</span><span class="sxs-lookup"><span data-stu-id="51072-127">Sample Table</span></span>  
 <span data-ttu-id="51072-128">例 A をテストするには、サンプル テーブル `T` を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="51072-128">To test example A, you must create sample table `T`.</span></span>  
  
```  
USE tempdb  
CREATE TABLE T (IntCol int, XmlCol xml);  
GO  
```  
  
#### <a name="sample-data-file"></a><span data-ttu-id="51072-129">サンプル データ ファイル</span><span class="sxs-lookup"><span data-stu-id="51072-129">Sample Data File</span></span>  
 <span data-ttu-id="51072-130">例 A を実行する前に、次のサンプル インスタンスが指定する`C:\SampleFolder\SampleData3.txt`エンコード体系を含む、UTF-8 エンコードのファイル ( `UTF-8` ) を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="51072-130">Before you can run example A, you must create a UTF-8 encoded file (`C:\SampleFolder\SampleData3.txt`) that contains the following sample instance that specifies the `UTF-8` encoding scheme.</span></span>  
  
```  
<?xml version="1.0" encoding="UTF-8"?>  
<Root>  
          <ProductDescription ProductModelID="5">  
             <Summary>Some Text</Summary>  
          </ProductDescription>  
</Root>  
```  
  
#### <a name="example-a"></a><span data-ttu-id="51072-131">例 A</span><span class="sxs-lookup"><span data-stu-id="51072-131">Example A</span></span>  
 <span data-ttu-id="51072-132">この例では、 `SINGLE_BLOB` オプションを `INSERT ... SELECT * FROM OPENROWSET(BULK...)` ステートメントで使用して、 `SampleData3.txt` という名前のファイルからデータをインポートし、XML インスタンスを 1 列のテーブル (サンプル テーブル `T`) に挿入します。</span><span class="sxs-lookup"><span data-stu-id="51072-132">This example uses the `SINGLE_BLOB` option in an `INSERT ... SELECT * FROM OPENROWSET(BULK...)` statement to import data from a file named `SampleData3.txt` and insert an XML instance in the single-column table, sample table `T`.</span></span>  
  
```  
INSERT INTO T(XmlCol)  
SELECT * FROM OPENROWSET(  
   BULK 'c:\SampleFolder\SampleData3.txt',  
   SINGLE_BLOB) AS x;  
```  
  
#### <a name="remarks"></a><span data-ttu-id="51072-133">解説</span><span class="sxs-lookup"><span data-stu-id="51072-133">Remarks</span></span>  
 <span data-ttu-id="51072-134">この場合に SINGLE_BLOB を使用すると、XML エンコード宣言で指定されている XML ドキュメントのエンコードと、サーバーによって暗黙的に示されている文字列のコード ページとの不一致を回避できます。</span><span class="sxs-lookup"><span data-stu-id="51072-134">By using SINGLE_BLOB in this case, you can avoid a mismatch between the encoding of the XML document (as specified by the XML encoding declaration) and the string codepage implied by the server.</span></span>  
  
 <span data-ttu-id="51072-135">NCLOB または CLOB データ型を使用した際にコード ページまたはエンコードの競合が発生する場合は、次のいずれかの操作を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="51072-135">If you use NCLOB or CLOB data types and run into a codepage or encoding conflict, you must do one of the following:</span></span>  
  
-   <span data-ttu-id="51072-136">XML データ ファイルの内容を正常にインポートできるように、XML 宣言を削除します。</span><span class="sxs-lookup"><span data-stu-id="51072-136">Remove the XML declaration to successfully import the contents of the XML data file.</span></span>  
  
-   <span data-ttu-id="51072-137">XML 宣言で使用されているエンコード体系に一致するコード ページを、クエリの CODEPAGE オプションに指定します。</span><span class="sxs-lookup"><span data-stu-id="51072-137">Specify a code page in the CODEPAGE option of the query that matches the encoding scheme that is used in the XML declaration.</span></span>  
  
-   <span data-ttu-id="51072-138">データベースの照合順序の設定を Unicode 以外の XML エンコード体系に一致 (解決) させます。</span><span class="sxs-lookup"><span data-stu-id="51072-138">Match, or resolve, the database collation settings with a non-Unicode XML encoding scheme.</span></span>  
  
 [<span data-ttu-id="51072-139">&#91;先頭に戻る&#93;</span><span class="sxs-lookup"><span data-stu-id="51072-139">&#91;Top&#93;</span></span>](#top)  
  
###  <a name="b-bulk-importing-xml-data-in-an-existing-row"></a><a name="existing_row"></a> <span data-ttu-id="51072-140">B.</span><span class="sxs-lookup"><span data-stu-id="51072-140">B.</span></span> <span data-ttu-id="51072-141">既存の行に XML データの一括インポートを行う</span><span class="sxs-lookup"><span data-stu-id="51072-141">Bulk importing XML data in an existing row</span></span>  
 <span data-ttu-id="51072-142">この例では `OPENROWSET` 一括行セット プロパイダを使用して、XML インスタンスを既存のサンプル テーブル `T`の 1 行または複数の行に追加します。</span><span class="sxs-lookup"><span data-stu-id="51072-142">This example uses the `OPENROWSET` bulk rowset provider to add an XML instance to an existing row or rows in sample table `T`.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="51072-143">この例を実行するには、まず例 A で提供されたテスト スクリプトを完了する必要があります。例 A では、 `tempdb.dbo.T` テーブルを作成し、 `SampleData3.txt`からデータを一括インポートをしています。</span><span class="sxs-lookup"><span data-stu-id="51072-143">To run this example, you must first complete the test script provided in example A. That example creates the `tempdb.dbo.T` table and bulk imports data from `SampleData3.txt`.</span></span>  
  
#### <a name="sample-data-file"></a><span data-ttu-id="51072-144">サンプル データ ファイル</span><span class="sxs-lookup"><span data-stu-id="51072-144">Sample Data File</span></span>  
 <span data-ttu-id="51072-145">例 B では、例 A の `SampleData3.txt` サンプル データ ファイルを変更したバージョンを使用します。</span><span class="sxs-lookup"><span data-stu-id="51072-145">Example B uses a modified version of the `SampleData3.txt` sample data file from the preceding example.</span></span> <span data-ttu-id="51072-146">例 B を実行するには、このファイルの内容を次のように修正します。</span><span class="sxs-lookup"><span data-stu-id="51072-146">To run this example, modify the content of this file as follows:</span></span>  
  
```  
<Root>  
          <ProductDescription ProductModelID="10">  
             <Summary>Some New Text</Summary>  
          </ProductDescription>  
</Root>  
```  
  
#### <a name="example-b"></a><span data-ttu-id="51072-147">例 B</span><span class="sxs-lookup"><span data-stu-id="51072-147">Example B</span></span>  
  
```  
-- Query before update shows initial state of XmlCol values.  
SELECT * FROM T  
UPDATE T  
SET XmlCol =(  
SELECT * FROM OPENROWSET(  
   BULK 'C:\SampleFolder\SampleData3.txt',  
           SINGLE_BLOB  
) AS x  
)  
WHERE IntCol = 1;  
GO  
```  
  
 [<span data-ttu-id="51072-148">&#91;先頭に戻る&#93;</span><span class="sxs-lookup"><span data-stu-id="51072-148">&#91;Top&#93;</span></span>](#top)  
  
###  <a name="c-bulk-importing-xml-data-from-a-file-that-contains-a-dtd"></a><a name="file_contains_dtd"></a> <span data-ttu-id="51072-149">C.</span><span class="sxs-lookup"><span data-stu-id="51072-149">C.</span></span> <span data-ttu-id="51072-150">DTD を含むファイルから XML データの一括インポートを行う</span><span class="sxs-lookup"><span data-stu-id="51072-150">Bulk importing XML data from a file that contains a DTD</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="51072-151">作業中の XML 環境で DTD (文書型定義) が特に必要ではない場合は、DTD のサポートを無効にしておくことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="51072-151">We recommended that you not enable support for Document Type Definitions (DTDs) if it is not required in your XML environment.</span></span> <span data-ttu-id="51072-152">DTD のサポートを有効にすると、使用しているサーバーが外部からの攻撃を受けやすくなり、サービス拒否攻撃の危険にさらされる場合があります。</span><span class="sxs-lookup"><span data-stu-id="51072-152">Turning on DTD support increases the attackable surface area of your server, and may expose it to a denial-of-service attack.</span></span> <span data-ttu-id="51072-153">DTD のサポートを有効にする必要がある場合は、信頼できる XML ドキュメントのみを処理することにより、このセキュリティ上のリスクを軽減できます。</span><span class="sxs-lookup"><span data-stu-id="51072-153">If you must enable DTD support, you can reduce this security risk by processing only trusted XML documents.</span></span>  
  
 <span data-ttu-id="51072-154">[bcp](../../tools/bcp-utility.md) コマンドを使用して、DTD を含むファイルから XML データのインポートを試みた場合に、次に示すようなエラーが表示されることがあります。</span><span class="sxs-lookup"><span data-stu-id="51072-154">During an attempt to use a [bcp](../../tools/bcp-utility.md) command to import XML data from a file that contains a DTD, an error similar to the following can occur:</span></span>  
  
 <span data-ttu-id="51072-155">"SQLState = 42000, NativeError = 6359"</span><span class="sxs-lookup"><span data-stu-id="51072-155">"SQLState = 42000, NativeError = 6359"</span></span>  
  
 <span data-ttu-id="51072-156">"エラー = [Microsoft][SQL Server Native Client][SQL Server]内部サブセット DTD を使用した XML の解析は許可されません。</span><span class="sxs-lookup"><span data-stu-id="51072-156">"Error = [Microsoft][SQL Server Native Client][ SQL Server]Parsing XML with internal subset DTDs not allowed.</span></span> <span data-ttu-id="51072-157">スタイル オプション 2 を設定して CONVERT を使用し、制限付きの内部サブセット DTD のサポートを有効にしてください。"</span><span class="sxs-lookup"><span data-stu-id="51072-157">Use CONVERT with style option 2 to enable limited internal subset DTD support."</span></span>  
  
 <span data-ttu-id="51072-158">"BCP コピー %s が失敗しました"</span><span class="sxs-lookup"><span data-stu-id="51072-158">"BCP copy %s failed"</span></span>  
  
 <span data-ttu-id="51072-159">この問題を回避するには、XML データを DTD を含むデータ ファイルからインポートする際に `OPENROWSET(BULK...)` 関数を使用し、コマンドの `CONVERT` 句内で `SELECT` オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="51072-159">To work around this problem, you can import XML data from a data file that contains a DTD by using the `OPENROWSET(BULK...)` function and then specifying the `CONVERT` option in the `SELECT` clause of the command.</span></span> <span data-ttu-id="51072-160">コマンドの基本構文を次に示します。</span><span class="sxs-lookup"><span data-stu-id="51072-160">The basic syntax for the command is:</span></span>  
  
 `INSERT ... SELECT CONVERT(...) FROM OPENROWSET(BULK...)`  
  
#### <a name="sample-data-file"></a><span data-ttu-id="51072-161">サンプル データ ファイル</span><span class="sxs-lookup"><span data-stu-id="51072-161">Sample Data File</span></span>  
 <span data-ttu-id="51072-162">一括インポートの例をテストする前に、次のサンプル インスタンスを含むファイル (`C:\temp\Dtdfile.xml`) を作成します。</span><span class="sxs-lookup"><span data-stu-id="51072-162">Before you can test this bulk import example, create a file (`C:\temp\Dtdfile.xml`) that contains the following sample instance:</span></span>  
  
```  
<!DOCTYPE DOC [<!ATTLIST elem1 attr1 CDATA "defVal1">]><elem1>January</elem1>  
```  
  
#### <a name="sample-table"></a><span data-ttu-id="51072-163">サンプル テーブル</span><span class="sxs-lookup"><span data-stu-id="51072-163">Sample Table</span></span>  
 <span data-ttu-id="51072-164">例 C では、次の `T1` ステートメントで作成した `CREATE TABLE` サンプル テーブルを使用します。</span><span class="sxs-lookup"><span data-stu-id="51072-164">Example C uses the `T1` sample table that is created by the following `CREATE TABLE` statement:</span></span>  
  
```  
USE tempdb;  
CREATE TABLE T1(XmlCol xml);  
GO  
```  
  
#### <a name="example-c"></a><span data-ttu-id="51072-165">例 C</span><span class="sxs-lookup"><span data-stu-id="51072-165">Example C</span></span>  
 <span data-ttu-id="51072-166">この例では `OPENROWSET(BULK...)` を使用して、 `CONVERT` 句内で `SELECT` オプションを指定し、 `Dtdfile.xml` から XML データをサンプル テーブル `T1`にインポートします。</span><span class="sxs-lookup"><span data-stu-id="51072-166">This example uses `OPENROWSET(BULK...)` and specifies the `CONVERT` option in the `SELECT` clause to import the XML data from `Dtdfile.xml` into sample table `T1`.</span></span>  
  
```  
INSERT T1  
  SELECT CONVERT(xml, BulkColumn, 2) FROM   
    OPENROWSET(Bulk 'c:\temp\Dtdfile.xml', SINGLE_BLOB) [rowsetresults];  
```  
  
 <span data-ttu-id="51072-167">`INSERT` ステートメントの実行後、DTD が XML から分離され、テーブル `T1` に格納されます。</span><span class="sxs-lookup"><span data-stu-id="51072-167">After the `INSERT` statement executes, the DTD is stripped from the XML and stored in the `T1` table.</span></span>  
  
 [<span data-ttu-id="51072-168">&#91;先頭に戻る&#93;</span><span class="sxs-lookup"><span data-stu-id="51072-168">&#91;Top&#93;</span></span>](#top)  
  
###  <a name="d-specifying-the-field-terminator-explicitly-using-a-format-file"></a><a name="field_terminator_in_format_file"></a> <span data-ttu-id="51072-169">D.</span><span class="sxs-lookup"><span data-stu-id="51072-169">D.</span></span> <span data-ttu-id="51072-170">フォーマット ファイルを使用してフィールド ターミネータを明示的に指定する</span><span class="sxs-lookup"><span data-stu-id="51072-170">Specifying the field terminator explicitly using a format file</span></span>  
 <span data-ttu-id="51072-171">次の例では、XML ドキュメント `Xmltable.dat`を一括インポートする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="51072-171">The following example shows how to bulk import the following XML document, `Xmltable.dat`.</span></span>  
  
#### <a name="sample-data-file"></a><span data-ttu-id="51072-172">サンプル データ ファイル</span><span class="sxs-lookup"><span data-stu-id="51072-172">Sample Data File</span></span>  
 <span data-ttu-id="51072-173">`Xmltable.dat` のドキュメントには 2 つの XML 値が、1 行に 1 つずつ含まれています。</span><span class="sxs-lookup"><span data-stu-id="51072-173">The document in `Xmltable.dat` contains two XML values, one for each row.</span></span> <span data-ttu-id="51072-174">最初の XML 値は UTF-16 でエンコードされており、2 番目の値は UTF-8 でエンコードされています。</span><span class="sxs-lookup"><span data-stu-id="51072-174">The first XML value is encoded with UTF-16, and the second value is encoded with UTF-8.</span></span>  
  
 <span data-ttu-id="51072-175">このデータの内容を 16 進形式でダンプすると次のようになります。</span><span class="sxs-lookup"><span data-stu-id="51072-175">The contents of this data file are shown in the following Hex dump:</span></span>  
  
```  
FF FE 3C 00 3F 00 78 00-6D 00 6C 00 20 00 76 00  *..<.?.x.m.l. .v.*  
65 00 72 00 73 00 69 00-6F 00 6E 00 3D 00 22 00  *e.r.s.i.o.n.=.".*  
31 00 2E 00 30 00 22 00-20 00 65 00 6E 00 63 00  *1...0.". .e.n.c.*  
6F 00 64 00 69 00 6E 00-67 00 3D 00 22 00 75 00  *o.d.i.n.g.=.".u.*  
74 00 66 00 2D 00 31 00-36 00 22 00 3F 00 3E 00  *t.f.-.1.6.".?.>.*  
3C 00 72 00 6F 00 6F 00-74 00 3E 00 A2 4F 9C 76  *<.r.o.o.t.>..O.v*  
0C FA 77 E4 80 00 89 00-00 06 90 06 91 2E 9B 2E  *..w.............*  
99 34 A2 34 86 00 83 02-92 20 7F 02 4E C5 E4 A3  *.4.4..... ..N...*  
34 B2 B7 B3 B7 FE F8 FF-F8 00 3C 00 2F 00 72 00  *4.........<./.r.*  
6F 00 6F 00 74 00 3E 00-00 00 00 00 7A EF BB BF  *o.o.t.>.....z...*  
3C 3F 78 6D 6C 20 76 65-72 73 69 6F 6E 3D 22 31  *<?xml version="1*  
2E 30 22 20 65 6E 63 6F-64 69 6E 67 3D 22 75 74  *.0" encoding="ut*  
66 2D 38 22 3F 3E 3C 72-6F 6F 74 3E E4 BE A2 E7  *f-8"?><root>....*  
9A 9C EF A8 8C EE 91 B7-C2 80 C2 89 D8 80 DA 90  *................*  
E2 BA 91 E2 BA 9B E3 92-99 E3 92 A2 C2 86 CA 83  *................*  
E2 82 92 C9 BF EC 95 8E-EA 8F A4 EB 88 B4 EB 8E  *................*  
B7 EF BA B7 EF BF B8 C3-B8 3C 2F 72 6F 6F 74 3E  *.........</root>*  
00 00 00 00 7A                                   *....z*  
```  
  
#### <a name="sample-table"></a><span data-ttu-id="51072-176">サンプル テーブル</span><span class="sxs-lookup"><span data-stu-id="51072-176">Sample Table</span></span>  
 <span data-ttu-id="51072-177">XML ドキュメントの一括インポートまたは一括エクスポートを行う際には、いずれのドキュメントにも記述されていない [フィールド ターミネータ](specify-field-and-row-terminators-sql-server.md) を使用する必要があります。たとえば、一連の 4 つの Null (`\0`) の後に文字 `z`を付けた、 `\0\0\0\0z`などです。</span><span class="sxs-lookup"><span data-stu-id="51072-177">When you bulk import or export an XML document, you should use a [field terminator](specify-field-and-row-terminators-sql-server.md) that cannot possibly appear in any of the documents; for example, a series of four nulls (`\0`) followed by the letter `z`: `\0\0\0\0z`.</span></span>  
  
 <span data-ttu-id="51072-178">この例では、サンプル テーブル `xTable` のフィールド ターミネータの使用方法を示します。</span><span class="sxs-lookup"><span data-stu-id="51072-178">This example shows how to use this field terminator for the `xTable` sample table.</span></span> <span data-ttu-id="51072-179">サンプル テーブルを作成するには、次の `CREATE TABLE` ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="51072-179">To create this sample table, use the following `CREATE TABLE` statement:</span></span>  
  
```  
USE tempdb;  
CREATE TABLE xTable (xCol xml);  
GO  
```  
  
#### <a name="sample-format-file"></a><span data-ttu-id="51072-180">サンプル フォーマット ファイル</span><span class="sxs-lookup"><span data-stu-id="51072-180">Sample Format File</span></span>  
 <span data-ttu-id="51072-181">フィールド ターミネータは、フォーマット ファイルで指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="51072-181">The field terminator must be specified in the format file.</span></span> <span data-ttu-id="51072-182">例 D では、次の内容を含む `Xmltable.fmt` という XML 以外のフォーマット ファイルを使用します。</span><span class="sxs-lookup"><span data-stu-id="51072-182">Example D uses a non-XML format file named `Xmltable.fmt` that contains the following:</span></span>  
  
```  
9.0  
1  
1       SQLBINARY     0       0       "\0\0\0\0z"    1     xCol         ""  
```  
  
 <span data-ttu-id="51072-183">このフォーマット ファイルを使用し、 `xTable` コマンドか、 `bcp` ステートメントまたは `BULK INSERT` ステートメントを使って、XML ドキュメントをテーブル `INSERT ... SELECT * FROM OPENROWSET(BULK...)` に一括インポートできます。</span><span class="sxs-lookup"><span data-stu-id="51072-183">You can use this format file to bulk import XML documents into the `xTable` table by using a `bcp` command or a `BULK INSERT` or `INSERT ... SELECT * FROM OPENROWSET(BULK...)` statement.</span></span>  
  
#### <a name="example-d"></a><span data-ttu-id="51072-184">例 D</span><span class="sxs-lookup"><span data-stu-id="51072-184">Example D</span></span>  
 <span data-ttu-id="51072-185">この例では、 `Xmltable.fmt` ステートメントで `BULK INSERT` フォーマット ファイルを使用して、 `Xmltable.dat`という XML データ ファイルの内容をインポートします。</span><span class="sxs-lookup"><span data-stu-id="51072-185">This example uses the `Xmltable.fmt` format file in a `BULK INSERT` statement to import the contents of an XML data file named `Xmltable.dat`.</span></span>  
  
```  
BULK INSERT xTable   
FROM 'C:\Xmltable.dat'  
WITH (FORMATFILE = 'C:\Xmltable.fmt');  
GO  
```  
  
 [<span data-ttu-id="51072-186">&#91;先頭に戻る&#93;</span><span class="sxs-lookup"><span data-stu-id="51072-186">&#91;Top&#93;</span></span>](#top)  
  
###  <a name="e-bulk-exporting-xml-data"></a><a name="bulk_export_xml_data"></a> <span data-ttu-id="51072-187">E.</span><span class="sxs-lookup"><span data-stu-id="51072-187">E.</span></span> <span data-ttu-id="51072-188">XML データの一括エクスポートを行う</span><span class="sxs-lookup"><span data-stu-id="51072-188">Bulk exporting XML data</span></span>  
 <span data-ttu-id="51072-189">次の例では、 `bcp` を使用し、同じ XML フォーマット ファイルを使用して、前の例で作成されたテーブルから XML データの一括エクスポートを行います。</span><span class="sxs-lookup"><span data-stu-id="51072-189">The following example uses `bcp` to bulk export XML data from the table that is created in the preceding example by using the same XML format file.</span></span> <span data-ttu-id="51072-190">次の `bcp` コマンドで、 `<server_name>` と `<instance_name>` はプレースホルダーであり、適切な値との差し替えが必要です。</span><span class="sxs-lookup"><span data-stu-id="51072-190">In the following `bcp` command, `<server_name>` and `<instance_name>` represent placeholders that must be replaced with appropriate values:</span></span>  
  
```  
bcp bulktest..xTable out a-wn.out -N -T -S<server_name>\<instance_name>  
```  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="51072-191">XML データがデータベース内に保存されるときに、 では XML エンコードが保存されません。</span><span class="sxs-lookup"><span data-stu-id="51072-191">does not save the XML encoding when XML data is persisted in the database.</span></span> <span data-ttu-id="51072-192">したがって、XML データをエクスポートするときは、XML フィールドの元のエンコードは使用できません。</span><span class="sxs-lookup"><span data-stu-id="51072-192">Therefore, the original encoding of XML fields is not available when XML data is exported.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="51072-193">は XML データをエクスポートする際に UTF-16 エンコードを使用します。</span><span class="sxs-lookup"><span data-stu-id="51072-193">uses UTF-16 encoding when exporting XML data.</span></span>  
  
 [<span data-ttu-id="51072-194">&#91;先頭に戻る&#93;</span><span class="sxs-lookup"><span data-stu-id="51072-194">&#91;Top&#93;</span></span>](#top)  
  
## <a name="see-also"></a><span data-ttu-id="51072-195">参照</span><span class="sxs-lookup"><span data-stu-id="51072-195">See Also</span></span>  
 <span data-ttu-id="51072-196">[INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="51072-196">[INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql) </span></span>  
 <span data-ttu-id="51072-197">[SELECT 句 &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-clause-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="51072-197">[SELECT Clause &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-clause-transact-sql) </span></span>  
 <span data-ttu-id="51072-198">[bcp ユーティリティ](../../tools/bcp-utility.md) </span><span class="sxs-lookup"><span data-stu-id="51072-198">[bcp Utility](../../tools/bcp-utility.md) </span></span>  
 <span data-ttu-id="51072-199">[データの一括インポートと一括エクスポート &#40;SQL Server&#41;](bulk-import-and-export-of-data-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="51072-199">[Bulk Import and Export of Data &#40;SQL Server&#41;](bulk-import-and-export-of-data-sql-server.md) </span></span>  
 <span data-ttu-id="51072-200">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="51072-200">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span></span>  
 [<span data-ttu-id="51072-201">OPENROWSET &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="51072-201">OPENROWSET &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/openrowset-transact-sql)  
  
  
