---
title: データの一括インポートでのフォーマット ファイルの使用 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- bulk importing [SQL Server], format files
- format files [SQL Server], importing data using
ms.assetid: 2956df78-833f-45fa-8a10-41d6522562b9
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c6d9779209b3ffb317658243c168d74740f6731b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646160"
---
# <a name="use-a-format-file-to-bulk-import-data-sql-server"></a><span data-ttu-id="bc253-102">データの一括インポートでのフォーマット ファイルの使用 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="bc253-102">Use a Format File to Bulk Import Data (SQL Server)</span></span>
  <span data-ttu-id="bc253-103">このトピックでは、一括インポート操作でのフォーマット ファイルの使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="bc253-103">This topic illustrates the use of a format file in bulk-import operations.</span></span> <span data-ttu-id="bc253-104">フォーマット ファイルでは、データ ファイルのフィールドがテーブルの列にマップされます。</span><span class="sxs-lookup"><span data-stu-id="bc253-104">The format file maps the fields of the data file to the columns of the table.</span></span>  <span data-ttu-id="bc253-105">XML 以外のフォーマットファイルまたは XML フォーマットファイルを使用してデータを一括インポートするには、 **bcp**コマンド、または BULK INSERT または INSERT...SELECT \* FROM OPENROWSET (BULK...) [!INCLUDE[tsql](../../includes/tsql-md.md)]メニュー.</span><span class="sxs-lookup"><span data-stu-id="bc253-105">You can use a non-XML or XML format file to bulk import data when using a **bcp** command or a BULK INSERT or INSERT ... SELECT \* FROM OPENROWSET(BULK...) [!INCLUDE[tsql](../../includes/tsql-md.md)] command.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="bc253-106">Unicode 文字データ ファイルを操作するフォーマット ファイルの場合、すべての入力フィールドが Unicode テキスト文字列 (つまり、固定サイズの Unicode 文字列または終端文字が指定された Unicode 文字列) でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="bc253-106">For a format file to work with a Unicode character data file, all the input fields must be Unicode text strings (that is, either fixed-size or character-terminated Unicode strings).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bc253-107">フォーマットファイルの詳細については、「 [Xml 以外のフォーマットファイル &#40;SQL Server&#41;](xml-format-files-sql-server.md)および[xml フォーマットファイル &#40;SQL Server&#41;](xml-format-files-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bc253-107">If you are unfamiliar with format files, see [Non-XML Format Files &#40;SQL Server&#41;](xml-format-files-sql-server.md) and [XML Format Files &#40;SQL Server&#41;](xml-format-files-sql-server.md).</span></span>  
  
## <a name="format-file-options-for-bulk-import-commands"></a><span data-ttu-id="bc253-108">一括インポート コマンドのフォーマット ファイル オプション</span><span class="sxs-lookup"><span data-stu-id="bc253-108">Format File Options for Bulk-Import Commands</span></span>  
 <span data-ttu-id="bc253-109">次の表は、各一括インポート コマンドのフォーマット ファイル オプションを示しています。</span><span class="sxs-lookup"><span data-stu-id="bc253-109">The following table summarizes the format-file option of for each of the bulk-import commands.</span></span>  
  
|<span data-ttu-id="bc253-110">一括読み込みコマンド</span><span class="sxs-lookup"><span data-stu-id="bc253-110">Bulk-load Command</span></span>|<span data-ttu-id="bc253-111">フォーマット ファイル オプションの使用方法</span><span class="sxs-lookup"><span data-stu-id="bc253-111">Using the Format-File Option</span></span>|  
|------------------------|-----------------------------------|  
|<span data-ttu-id="bc253-112">BULK INSERT</span><span class="sxs-lookup"><span data-stu-id="bc253-112">BULK INSERT</span></span>|<span data-ttu-id="bc253-113">FORMATFILE = '*format_file_path*'</span><span class="sxs-lookup"><span data-stu-id="bc253-113">FORMATFILE = '*format_file_path*'</span></span>|  
|<span data-ttu-id="bc253-114">INSERT ...SELECT \* FROM OPENROWSET(BULK...)</span><span class="sxs-lookup"><span data-stu-id="bc253-114">INSERT ... SELECT \* FROM OPENROWSET(BULK...)</span></span>|<span data-ttu-id="bc253-115">FORMATFILE = '*format_file_path*'</span><span class="sxs-lookup"><span data-stu-id="bc253-115">FORMATFILE = '*format_file_path*'</span></span>|  
|<span data-ttu-id="bc253-116">**bcp** ...**in**</span><span class="sxs-lookup"><span data-stu-id="bc253-116">**bcp** ... **in**</span></span>|<span data-ttu-id="bc253-117">**-f** *format_file*</span><span class="sxs-lookup"><span data-stu-id="bc253-117">**-f** *format_file*</span></span>|  
  
 <span data-ttu-id="bc253-118">詳細については、「[bcp ユーティリティ](../../tools/bcp-utility.md)」、「[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql)」、または「[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bc253-118">For more information, see [bcp Utility](../../tools/bcp-utility.md), [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql), or [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bc253-119">SQLXML データを一括エクスポートまたは一括インポートするには、フォーマット ファイルで次のいずれかのデータ型を使用します。SQLCHAR または SQLVARYCHAR (データはクライアント コード ページまたは照合順序で暗黙的に指定されるコード ページで送られます)、SQLNCHAR または SQLNVARCHAR (データは Unicode として送られます)、SQLBINARY または SQLVARYBIN (データは変換なしで送られます)。</span><span class="sxs-lookup"><span data-stu-id="bc253-119">To bulk export or import SQLXML data, use one of the following data types in your format file: SQLCHAR or SQLVARYCHAR (the data is sent in the client code page or in the code page implied by the collation), SQLNCHAR or SQLNVARCHAR (the data is sent as Unicode), or SQLBINARY or SQLVARYBIN (the data is sent without any conversion).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="bc253-120">例</span><span class="sxs-lookup"><span data-stu-id="bc253-120">Examples</span></span>  
 <span data-ttu-id="bc253-121">このセクションの例では、 **bcp**コマンドと BULK INSERT を使用して、フォーマットファイルを使用してデータを一括インポートする方法について説明します。SELECT \* FROM OPENROWSET (BULK...) ステートメント。</span><span class="sxs-lookup"><span data-stu-id="bc253-121">The examples in this section illustrate how to use format files to bulk-import data by using the **bcp** command and the BULK INSERT, and INSERT ... SELECT \* FROM OPENROWSET(BULK...) statements.</span></span> <span data-ttu-id="bc253-122">一括インポートの例を実行する前に、サンプル テーブル、データ ファイル、およびフォーマット ファイルを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bc253-122">Before you can run one of the bulk-import examples, you need to create a sample table, data file, and a format file.</span></span>  
  
### <a name="sample-table"></a><span data-ttu-id="bc253-123">サンプル テーブル</span><span class="sxs-lookup"><span data-stu-id="bc253-123">Sample Table</span></span>  
 <span data-ttu-id="bc253-124">次の例では、 **dbo** スキーマ内の [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] myTestFormatFiles **という名前のテーブルを** サンプル データベースに作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bc253-124">The examples require that a table named **myTestFormatFiles** table be created in the [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] sample database under the **dbo** schema.</span></span> <span data-ttu-id="bc253-125">このテーブルを作成するには、 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] クエリ エディターで、次のコードを実行します。</span><span class="sxs-lookup"><span data-stu-id="bc253-125">To create this table, in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] Query Editor, execute:</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
CREATE TABLE myTestFormatFiles (  
   Col1 smallint,  
   Col2 nvarchar(50),  
   Col3 nvarchar(50),  
   Col4 nvarchar(50)  
   );  
GO  
```  
  
### <a name="sample-data-file"></a><span data-ttu-id="bc253-126">サンプル データ ファイル</span><span class="sxs-lookup"><span data-stu-id="bc253-126">Sample Data File</span></span>  
 <span data-ttu-id="bc253-127">この例では、次のレコードが含まれているサンプル データ ファイル `myTestFormatFiles-c.Dat`を使用します。</span><span class="sxs-lookup"><span data-stu-id="bc253-127">The examples use a sample data file, `myTestFormatFiles-c.Dat`, which contains the following records.</span></span> <span data-ttu-id="bc253-128">このデータ ファイルを作成するには、[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows のコマンド プロンプトで次のように入力します。</span><span class="sxs-lookup"><span data-stu-id="bc253-128">To create the data file, at the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows command prompt, enter:</span></span>  
  
```  
10,Field2,Field3,Field4  
15,Field2,Field3,Field4  
46,Field2,Field3,Field4  
58,Field2,Field3,Field4  
```  
  
### <a name="sample-format-files"></a><span data-ttu-id="bc253-129">サンプル フォーマット ファイル</span><span class="sxs-lookup"><span data-stu-id="bc253-129">Sample Format Files</span></span>  
 <span data-ttu-id="bc253-130">このセクションの例では、XML フォーマット ファイル `myTestFormatFiles-f-x-c.Xml` を使用する場合と、XML 形式以外のフォーマット ファイルを使用する場合があります。</span><span class="sxs-lookup"><span data-stu-id="bc253-130">Some of the examples in this section use an XML format file, `myTestFormatFiles-f-x-c.Xml`, and other examples use a non-XML format file.</span></span> <span data-ttu-id="bc253-131">どちらのフォーマット ファイルでも、文字データの形式と既定外のフィールド ターミネータ (,) を使用します。</span><span class="sxs-lookup"><span data-stu-id="bc253-131">Both format files use character data formats and a non-default field terminator (,).</span></span>  
  
#### <a name="the-sample-non-xml-format-file"></a><span data-ttu-id="bc253-132">XML 形式以外のフォーマット ファイルのサンプル</span><span class="sxs-lookup"><span data-stu-id="bc253-132">The Sample Non-XML Format File</span></span>  
 <span data-ttu-id="bc253-133">次の例では、 **bcp** を使用して、 `myTestFormatFiles` テーブルから XML フォーマット ファイルを生成します。</span><span class="sxs-lookup"><span data-stu-id="bc253-133">The following example uses **bcp** to generate an XML format file from the `myTestFormatFiles` table.</span></span> <span data-ttu-id="bc253-134">`myTestFormatFiles.Fmt` ファイルには、次の情報が格納されます。</span><span class="sxs-lookup"><span data-stu-id="bc253-134">The `myTestFormatFiles.Fmt` file contains the following information:</span></span>  
  
```  
9.0  
4  
1       SQLCHAR       0       7       ","      1     Col1         ""  
2       SQLCHAR       0       100     ","      2     Col2         SQL_Latin1_General_CP1_CI_AS  
3       SQLCHAR       0       100     ","      3     Col3         SQL_Latin1_General_CP1_CI_AS  
4       SQLCHAR       0       100     "\r\n"   4     Col4         SQL_Latin1_General_CP1_CI_AS  
```  
  
 <span data-ttu-id="bc253-135">**format** オプションと共に **bcp** を使用して、このフォーマット ファイルを作成するには、Windows のコマンド プロンプトで次のように入力します。</span><span class="sxs-lookup"><span data-stu-id="bc253-135">To use **bcp** with the **format** option to create this format file, at the Windows command prompt, enter:</span></span>  
  
```  
bcp AdventureWorks2012..MyTestFormatFiles format nul -c -t, -f myTestFormatFiles.Fmt -T  
  
```  
  
 <span data-ttu-id="bc253-136">フォーマット ファイルの作成方法の詳細については、「[フォーマット ファイルの作成 &#40;SQL Server&#41;](create-a-format-file-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bc253-136">For more information about creating a format file, see [Create a Format File &#40;SQL Server&#41;](create-a-format-file-sql-server.md).</span></span>  
  
#### <a name="the-sample-xml-format-file"></a><span data-ttu-id="bc253-137">XML 形式のフォーマット ファイルのサンプル</span><span class="sxs-lookup"><span data-stu-id="bc253-137">The Sample XML Format File</span></span>  
 <span data-ttu-id="bc253-138">次の例では、 **bcp** を使用して、 `myTestFormatFiles` テーブルから XML フォーマット ファイルを生成します。</span><span class="sxs-lookup"><span data-stu-id="bc253-138">The following example uses **bcp** to create to generate an XML format file from the `myTestFormatFiles` table.</span></span> <span data-ttu-id="bc253-139">`myTestFormatFiles.Xml` ファイルには、次の情報が格納されます。</span><span class="sxs-lookup"><span data-stu-id="bc253-139">The `myTestFormatFiles.Xml` file contains the following information:</span></span>  
  
```  
<?xml version="1.0"?>  
<BCPFORMAT xmlns="https://schemas.microsoft.com/sqlserver/2004/bulkload/format" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
 <RECORD>  
  <FIELD ID="1" xsi:type="CharTerm" TERMINATOR="," MAX_LENGTH="7"/>  
  <FIELD ID="2" xsi:type="CharTerm" TERMINATOR="," MAX_LENGTH="100" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
  <FIELD ID="3" xsi:type="CharTerm" TERMINATOR="," MAX_LENGTH="100" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
  <FIELD ID="4" xsi:type="CharTerm" TERMINATOR="\r\n" MAX_LENGTH="100" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
 </RECORD>  
 <ROW>  
  <COLUMN SOURCE="1" NAME="Col1" xsi:type="SQLSMALLINT"/>  
  <COLUMN SOURCE="2" NAME="Col2" xsi:type="SQLNVARCHAR"/>  
  <COLUMN SOURCE="3" NAME="Col3" xsi:type="SQLNVARCHAR"/>  
  <COLUMN SOURCE="4" NAME="Col4" xsi:type="SQLNVARCHAR"/>  
 </ROW>  
</BCPFORMAT>  
```  
  
 <span data-ttu-id="bc253-140">**format** オプションと共に **bcp** を使用して、このフォーマット ファイルを作成するには、Windows のコマンド プロンプトで次のように入力します。</span><span class="sxs-lookup"><span data-stu-id="bc253-140">To use **bcp** with the **format** option to create this format file, at the Windows command prompt, enter:</span></span>  
  
```  
bcp AdventureWorks2012..MyTestFormatFiles format nul -c -t, -x -f myTestFormatFiles.Xml -T  
```  
  
### <a name="using-bcp"></a><span data-ttu-id="bc253-141">bcp の使用</span><span class="sxs-lookup"><span data-stu-id="bc253-141">Using bcp</span></span>  
 <span data-ttu-id="bc253-142">次の例では、 **bcp** を使用して、 `myTestFormatFiles-c.Dat` データ ファイルのデータをサンプル データベース内の `HumanResources.myTestFormatFiles` テーブルに一括インポートします。</span><span class="sxs-lookup"><span data-stu-id="bc253-142">The following example uses **bcp** to bulk import data from the `myTestFormatFiles-c.Dat` data file into `HumanResources.myTestFormatFiles` table in the  sample database.</span></span> <span data-ttu-id="bc253-143">この例では、XML 形式のフォーマット ファイル `MyTestFormatFiles.Xml`を使用します。</span><span class="sxs-lookup"><span data-stu-id="bc253-143">This example uses an XML format file, `MyTestFormatFiles.Xml`.</span></span> <span data-ttu-id="bc253-144">既存のテーブル行は、データ ファイルのインポート前に削除されます。</span><span class="sxs-lookup"><span data-stu-id="bc253-144">The example deletes any existing table rows before importing the data file.</span></span>  
  
 <span data-ttu-id="bc253-145">Windows のコマンド プロンプトで、次のように入力します。</span><span class="sxs-lookup"><span data-stu-id="bc253-145">At the Windows command prompt, enter:</span></span>  
  
```  
bcp AdventureWorks2012..myTestFormatFiles in C:\myTestFormatFiles-c.Dat -f C:\myTestFormatFiles.Xml -T  
```  
  
> [!NOTE]  
>  <span data-ttu-id="bc253-146"> このコマンドの詳細については、「 [bcp Utility](../../tools/bcp-utility.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bc253-146">For more information about this command, see [bcp Utility](../../tools/bcp-utility.md).</span></span>  
  
### <a name="using-bulk-insert"></a><span data-ttu-id="bc253-147">BULK INSERT の使用</span><span class="sxs-lookup"><span data-stu-id="bc253-147">Using BULK INSERT</span></span>  
 <span data-ttu-id="bc253-148">次の例では、BULK INSERT を使用して、`myTestFormatFiles-c.Dat` データ ファイルから [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] サンプル データベース内の `HumanResources.myTestFormatFiles` テーブルにデータを一括インポートします。</span><span class="sxs-lookup"><span data-stu-id="bc253-148">The following example uses BULK INSERT to bulk import data from the `myTestFormatFiles-c.Dat` data file into `HumanResources.myTestFormatFiles` table in the [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] sample database.</span></span> <span data-ttu-id="bc253-149">この例では、XML 形式以外のフォーマット ファイル `MyTestFormatFiles.Fmt` を使用します。</span><span class="sxs-lookup"><span data-stu-id="bc253-149">This example uses a non-XML format file, `MyTestFormatFiles.Fmt`.</span></span> <span data-ttu-id="bc253-150">既存のテーブル行は、データ ファイルのインポート前に削除されます。</span><span class="sxs-lookup"><span data-stu-id="bc253-150">The example deletes any existing table rows before importing the data file.</span></span>  
  
 <span data-ttu-id="bc253-151">[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] クエリ エディターで、次のコードを実行します。</span><span class="sxs-lookup"><span data-stu-id="bc253-151">In [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] Query Editor, execute:</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
DELETE myTestFormatFiles;  
GO  
BULK INSERT myTestFormatFiles   
   FROM 'C:\myTestFormatFiles-c.Dat'   
   WITH (FORMATFILE = 'C:\myTestFormatFiles.Fmt');  
GO  
SELECT * FROM myTestFormatFiles;  
GO  
```  
  
> [!NOTE]  
>  <span data-ttu-id="bc253-152">この句の詳細については、「[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bc253-152">For more information about this statement, see [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql).</span></span>  
  
### <a name="using-the-openrowset-bulk-rowset-provider"></a><span data-ttu-id="bc253-153">OPENROWSET 一括行セット プロバイダーの使用</span><span class="sxs-lookup"><span data-stu-id="bc253-153">Using the OPENROWSET Bulk Rowset Provider</span></span>  
 <span data-ttu-id="bc253-154">次の例では、`INSERT ... SELECT * FROM OPENROWSET(BULK...)` を使用して、`myTestFormatFiles-c.Dat` データ ファイルのデータを `HumanResources.myTestFormatFiles` サンプル データベース内の `AdventureWorks` テーブルに一括インポートします。</span><span class="sxs-lookup"><span data-stu-id="bc253-154">The following example uses `INSERT ... SELECT * FROM OPENROWSET(BULK...)` to bulk import data from the `myTestFormatFiles-c.Dat` data file into `HumanResources.myTestFormatFiles` table in the `AdventureWorks` sample database.</span></span> <span data-ttu-id="bc253-155">この例では、XML 形式のフォーマット ファイル `MyTestFormatFiles.Xml`を使用します。</span><span class="sxs-lookup"><span data-stu-id="bc253-155">This example uses an XML format file, `MyTestFormatFiles.Xml`.</span></span> <span data-ttu-id="bc253-156">既存のテーブル行は、データ ファイルのインポート前に削除されます。</span><span class="sxs-lookup"><span data-stu-id="bc253-156">The example deletes any existing table rows before importing the data file.</span></span>  
  
 <span data-ttu-id="bc253-157">[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] クエリ エディターで、次のコードを実行します。</span><span class="sxs-lookup"><span data-stu-id="bc253-157">In [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] Query Editor, execute:</span></span>  
  
```  
USE AdventureWorks2012;  
DELETE myTestFormatFiles;  
GO  
INSERT INTO myTestFormatFiles  
    SELECT *  
      FROM  OPENROWSET(BULK  'C:\myTestFormatFiles-c.Dat',  
      FORMATFILE='C:\myTestFormatFiles.Xml'       
      ) as t1 ;  
GO  
SELECT * FROM myTestFormatFiles;  
GO  
```  
  
 <span data-ttu-id="bc253-158">サンプル テーブルを使用し終わったら、次のステートメントを使用してテーブルを削除できます。</span><span class="sxs-lookup"><span data-stu-id="bc253-158">When you finish using the sample table, you can drop it using the following statement:</span></span>  
  
```  
DROP TABLE myTestFormatFiles  
```  
  
> [!NOTE]  
>  <span data-ttu-id="bc253-159">OPENROWSET BULK 句の詳細については、「 [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql)を使用) を示すことができます。</span><span class="sxs-lookup"><span data-stu-id="bc253-159">For more information about the OPENROWSET BULK clause, see [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql).</span></span>  
  
## <a name="additional-examples"></a><span data-ttu-id="bc253-160">その他の例</span><span class="sxs-lookup"><span data-stu-id="bc253-160">Additional Examples</span></span>  
 [<span data-ttu-id="bc253-161">フォーマット ファイルの作成 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="bc253-161">Create a Format File &#40;SQL Server&#41;</span></span>](create-a-format-file-sql-server.md)  
  
 [<span data-ttu-id="bc253-162">フォーマット ファイルを使用したテーブル列のスキップ &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="bc253-162">Use a Format File to Skip a Table Column &#40;SQL Server&#41;</span></span>](use-a-format-file-to-skip-a-table-column-sql-server.md)  
  
 [<span data-ttu-id="bc253-163">フォーマット ファイルを使用したデータ フィールドのスキップ &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="bc253-163">Use a Format File to Skip a Data Field &#40;SQL Server&#41;</span></span>](use-a-format-file-to-skip-a-data-field-sql-server.md)  
  
 [<span data-ttu-id="bc253-164">フォーマット ファイルを使用したテーブル列とデータ ファイル フィールドのマッピング &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="bc253-164">Use a Format File to Map Table Columns to Data-File Fields &#40;SQL Server&#41;</span></span>](use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="bc253-165">参照</span><span class="sxs-lookup"><span data-stu-id="bc253-165">See Also</span></span>  
 <span data-ttu-id="bc253-166">[bcp ユーティリティ](../../tools/bcp-utility.md) </span><span class="sxs-lookup"><span data-stu-id="bc253-166">[bcp Utility](../../tools/bcp-utility.md) </span></span>  
 <span data-ttu-id="bc253-167">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="bc253-167">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span></span>  
 <span data-ttu-id="bc253-168">[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="bc253-168">[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span></span>  
 <span data-ttu-id="bc253-169">[XML 以外のフォーマット ファイル &#40;SQL Server&#41;](xml-format-files-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="bc253-169">[Non-XML Format Files &#40;SQL Server&#41;](xml-format-files-sql-server.md) </span></span>  
 [<span data-ttu-id="bc253-170">XML フォーマット ファイル &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="bc253-170">XML Format Files &#40;SQL Server&#41;</span></span>](xml-format-files-sql-server.md)  
  
  
