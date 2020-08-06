---
title: フォーマット ファイルを使用したデータ フィールドのスキップ (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- format files [SQL Server], skipping data fields
- skipping data fields when importing
ms.assetid: 6a76517e-983b-47a1-8f02-661b99859a8b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2d3f78c3c97c5bbe862867d5f51ff35f57d147df
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646159"
---
# <a name="use-a-format-file-to-skip-a-data-field-sql-server"></a><span data-ttu-id="c0881-102">フォーマット ファイルを使用したデータ フィールドのスキップ (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="c0881-102">Use a Format File to Skip a Data Field (SQL Server)</span></span>
  <span data-ttu-id="c0881-103">データ ファイルには、テーブルの列数よりも多くのフィールドを格納できます。</span><span class="sxs-lookup"><span data-stu-id="c0881-103">A data file can contain more fields than the number of columns in the table.</span></span> <span data-ttu-id="c0881-104">このトピックでは、XML 以外のフォーマット ファイルと XML フォーマット ファイルの両方を変更し、データ ファイルに多くのフィールドを格納する方法について説明します。この操作は、テーブル列を対応するデータ フィールドにマップし、余分なフィールドを無視することによって行います。</span><span class="sxs-lookup"><span data-stu-id="c0881-104">This topic describes modifying both non-XML and XML format files to accommodate a data file with more fields by mapping the table columns to the corresponding data fields and ignoring the extra fields.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c0881-105">XML 以外のフォーマットファイルまたは XML フォーマットファイルを使用して、データファイルをテーブルに一括インポートするには、 **bcp**コマンド、BULK INSERT ステートメント、または INSERT...SELECT \* FROM OPENROWSET (BULK...) ステートメント。</span><span class="sxs-lookup"><span data-stu-id="c0881-105">Either a non-XML or XML format file can be used to bulk import a data file into the table by using a **bcp** command, BULK INSERT statement, or INSERT ... SELECT \* FROM OPENROWSET(BULK...) statement.</span></span> <span data-ttu-id="c0881-106">詳細については、「[データの一括インポートでのフォーマット ファイルの使用 &#40;SQL Server&#41;](use-a-format-file-to-bulk-import-data-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c0881-106">For more information, see [Use a Format File to Bulk Import Data &#40;SQL Server&#41;](use-a-format-file-to-bulk-import-data-sql-server.md).</span></span>  
  
## <a name="sample-data-file-and-table"></a><span data-ttu-id="c0881-107">サンプル データ ファイルとサンプル テーブル</span><span class="sxs-lookup"><span data-stu-id="c0881-107">Sample Data File and Table</span></span>  
 <span data-ttu-id="c0881-108">このトピックで例として変更するフォーマット ファイルは、次のテーブルとデータ ファイルに基づいています。</span><span class="sxs-lookup"><span data-stu-id="c0881-108">The examples of modified format files in this topic are based on the following table and data file.</span></span>  
  
### <a name="sample-table"></a><span data-ttu-id="c0881-109">サンプル テーブル</span><span class="sxs-lookup"><span data-stu-id="c0881-109">Sample Table</span></span>  
 <span data-ttu-id="c0881-110">以下の例を実行するには、`myTestSkipField` スキーマに基づいて、`dbo` という名前のテーブルを [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] サンプル データベース内に作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c0881-110">The examples require that a table named `myTestSkipField` be created in the [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] sample database under the `dbo` schema.</span></span> <span data-ttu-id="c0881-111">このテーブルを作成するには、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] クエリエディターで次のコードを実行します。</span><span class="sxs-lookup"><span data-stu-id="c0881-111">To create this table, in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Query Editor, run the following code:</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
CREATE TABLE myTestSkipField   
   (  
   PersonID smallint,  
   FirstName nvarchar(50) ,  
   LastName nvarchar(50)   
   );  
GO  
```  
  
### <a name="sample-data-file"></a><span data-ttu-id="c0881-112">サンプル データ ファイル</span><span class="sxs-lookup"><span data-stu-id="c0881-112">Sample Data File</span></span>  
 <span data-ttu-id="c0881-113">データ ファイル `myTestSkipField-c.dat` には、次のレコードが含まれています。</span><span class="sxs-lookup"><span data-stu-id="c0881-113">The data file, `myTestSkipField-c.dat`, contains the following records:</span></span>  
  
```  
1,Skipme,DataField3,DataField4  
1,Skipme,DataField3,DataField4  
1,Skipme,DataField3,DataField4  
```  
  
 <span data-ttu-id="c0881-114">`myTestSkipField-c.dat` から `myTestSkipField` テーブルにデータを一括インポートするには、フォーマット ファイルで次の操作を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="c0881-114">To bulk import data from `myTestSkipField-c.dat` into the `myTestSkipField` table, the format file must do the following:</span></span>  
  
-   <span data-ttu-id="c0881-115">最初のデータ フィールドを最初の列 `PersonID`にマップします。</span><span class="sxs-lookup"><span data-stu-id="c0881-115">Map the first data field to the first column, `PersonID`.</span></span>  
  
-   <span data-ttu-id="c0881-116">2 番目のデータ フィールドをスキップします。</span><span class="sxs-lookup"><span data-stu-id="c0881-116">Skip the second data field.</span></span>  
  
-   <span data-ttu-id="c0881-117">3 番目のデータ フィールドを 2 番目の列 `FirstName`にマップします。</span><span class="sxs-lookup"><span data-stu-id="c0881-117">Map the third data field to the second column, `FirstName`.</span></span>  
  
-   <span data-ttu-id="c0881-118">4 番目のデータ フィールドを 3 番目の列 `LastName`にマップします。</span><span class="sxs-lookup"><span data-stu-id="c0881-118">Map the fourth data field to the third column, `LastName`.</span></span>  
  
## <a name="non-xml-format-file-for-more-data-fields"></a><span data-ttu-id="c0881-119">より多くのデータ フィールドを格納するための XML 以外のフォーマット ファイル</span><span class="sxs-lookup"><span data-stu-id="c0881-119">Non-XML Format File for More Data Fields</span></span>  
 <span data-ttu-id="c0881-120">次のフォーマット ファイル `myTestSkipField.fmt` は、`myTestSkipField-c.dat` のフィールドを `myTestSkipField` テーブルの列にマップします。</span><span class="sxs-lookup"><span data-stu-id="c0881-120">The following format file, `myTestSkipField.fmt`, maps the fields in `myTestSkipField-c.dat` to the columns of the `myTestSkipField` table.</span></span> <span data-ttu-id="c0881-121">このフォーマット ファイルでは、文字データ形式が使用されます。</span><span class="sxs-lookup"><span data-stu-id="c0881-121">The format file uses character data format.</span></span> <span data-ttu-id="c0881-122">列マッピングをスキップするには、フォーマット ファイルの `ExtraField` 列に示すように、その列の順序の値を 0 に変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c0881-122">Skipping a column mapping requires changing its column order value to 0, as shown for the `ExtraField` column in the format file.</span></span>  
  
 <span data-ttu-id="c0881-123">`myTestSkipField.fmt` フォーマット ファイルには、次の情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="c0881-123">The `myTestSkipField.fmt` format file contains the following information:</span></span>  
  
```  
9.0  
4  
1       SQLCHAR       0       7       ","      1     PersonID               ""  
2       SQLCHAR       0       100       ","    0     ExtraField             SQL_Latin1_General_CP1_CI_AS  
3       SQLCHAR       0       100     ","      2     FirstName              SQL_Latin1_General_CP1_CI_AS  
4       SQLCHAR       0       100     "\r\n"   3     LastName               SQL_Latin1_General_CP1_CI_AS  
  
```  
  
> [!NOTE]  
>  <span data-ttu-id="c0881-124">XML 以外のフォーマット ファイルの詳細については、「[XML以外のフォーマット ファイル &#40;SQL Server&#41;](xml-format-files-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c0881-124">For information about the syntax of non-XML format files, see [Non-XML Format Files &#40;SQL Server&#41;](xml-format-files-sql-server.md).</span></span>  
  
### <a name="examples"></a><span data-ttu-id="c0881-125">例</span><span class="sxs-lookup"><span data-stu-id="c0881-125">Examples</span></span>  
 <span data-ttu-id="c0881-126">次の例では、`INSERT ... SELECT * FROM OPENROWSET(BULK...)` フォーマット ファイルを使用して、`myTestSkipField.fmt` を使用します。</span><span class="sxs-lookup"><span data-stu-id="c0881-126">The following example uses `INSERT ... SELECT * FROM OPENROWSET(BULK...)` using the `myTestSkipField.fmt` format file.</span></span> <span data-ttu-id="c0881-127">この例では、 `myTestSkipField-c.dat` データ ファイルを `myTestSkipField` テーブルに一括インポートします。</span><span class="sxs-lookup"><span data-stu-id="c0881-127">The example bulk imports the `myTestSkipField-c.dat` data file into the `myTestSkipField` table.</span></span> <span data-ttu-id="c0881-128">サンプルのテーブルとデータ ファイルを作成するには、このトピックの「サンプル データ ファイルとサンプル テーブル」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c0881-128">To create the sample table and data file, see "Sample Data File and Table," earlier in this topic.</span></span>  
  
 <span data-ttu-id="c0881-129">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] クエリ エディターで、次のコードを実行します。</span><span class="sxs-lookup"><span data-stu-id="c0881-129">In the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Query Editor, run the following code:</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
INSERT INTO myTestSkipField   
   SELECT *  
      FROM  OPENROWSET(BULK  'C:\myTestSkipField-c.dat',  
      FORMATFILE='C:\myTestSkipField.fmt'    
       ) AS t1;  
GO   
```  
  
## <a name="xml-format-file-for-more-data-fields"></a><span data-ttu-id="c0881-130">より多くのデータ フィールドを格納するための XML フォーマット ファイル</span><span class="sxs-lookup"><span data-stu-id="c0881-130">XML Format File for More Data Fields</span></span>  
 <span data-ttu-id="c0881-131">この例で提供されるフォーマット ファイルは、別のフォーマット ファイルである `myTestSkipField.xml` に基づいています。このフォーマット ファイル全体では、文字データ形式が使用されます。また、フィールドの数と順序は `myTestSkipField` テーブルの列と完全に一致しています。</span><span class="sxs-lookup"><span data-stu-id="c0881-131">The format file presented in this example is based on another format file, `myTestSkipField.xml`, which uses character data format throughout and whose fields correspond exactly in number and order to the columns in the `myTestSkipField` table.</span></span> <span data-ttu-id="c0881-132">フォーマット ファイルの内容を確認するには、「[フォーマット ファイルの作成 &#40;SQL Server&#41;](create-a-format-file-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c0881-132">To view the contents of that format file, see [Create a Format File &#40;SQL Server&#41;](create-a-format-file-sql-server.md).</span></span>  
  
 <span data-ttu-id="c0881-133">次のフォーマット ファイル `myTestSkipField.xml` は、`myTestSkipField-c.dat` のフィールドを `myTestSkipField` テーブルの列にマップします。</span><span class="sxs-lookup"><span data-stu-id="c0881-133">The following format file, `myTestSkipField.xml`, maps the fields in `myTestSkipField-c.dat` to the columns of the `myTestSkipField` table.</span></span> <span data-ttu-id="c0881-134">このフォーマット ファイルでは、文字データ形式が使用されます。</span><span class="sxs-lookup"><span data-stu-id="c0881-134">The format file uses character data format.</span></span>  
  
 <span data-ttu-id="c0881-135">`myTestSkipField.xml` フォーマット ファイルには、次の情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="c0881-135">The `myTestSkipField.xml` format file contains the following information:</span></span>  
  
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
  <COLUMN SOURCE="1" NAME="PersonID" xsi:type="SQLSMALLINT"/>  
  <COLUMN SOURCE="3" NAME="FirstName" xsi:type="SQLNVARCHAR"/>  
  <COLUMN SOURCE="4" NAME="LastName" xsi:type="SQLNVARCHAR"/>  
 </ROW>  
</BCPFORMAT>  
```  
  
### <a name="examples"></a><span data-ttu-id="c0881-136">例</span><span class="sxs-lookup"><span data-stu-id="c0881-136">Examples</span></span>  
 <span data-ttu-id="c0881-137">次の例では、`INSERT ... SELECT * FROM OPENROWSET(BULK...)` フォーマット ファイルを使用して、`myTestSkipField.Xml` を使用します。</span><span class="sxs-lookup"><span data-stu-id="c0881-137">The following example uses `INSERT ... SELECT * FROM OPENROWSET(BULK...)` using the `myTestSkipField.Xml` format file.</span></span> <span data-ttu-id="c0881-138">この例では、 `myTestSkipField-c.dat` データ ファイルを `myTestSkipField` テーブルに一括インポートします。</span><span class="sxs-lookup"><span data-stu-id="c0881-138">The example bulk imports the `myTestSkipField-c.dat` data file into the `myTestSkipField` table.</span></span> <span data-ttu-id="c0881-139">サンプルのテーブルとデータ ファイルを作成するには、このトピックの「サンプル データ ファイルとサンプル テーブル」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c0881-139">To create the sample table and data file, see "Sample Data File and Table," earlier in this topic.</span></span>  
  
 <span data-ttu-id="c0881-140">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] クエリ エディターで、次のコードを実行します。</span><span class="sxs-lookup"><span data-stu-id="c0881-140">In the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Query Editor, run the following code:</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
INSERT INTO myTestSkipField   
  SELECT *  
      FROM  OPENROWSET(BULK  'C:\myTestSkipField-c.dat',  
      FORMATFILE='C:\myTestSkipField.xml'    
       ) AS t1;  
GO  
  
```  
  
> [!NOTE]  
>  <span data-ttu-id="c0881-141">XML スキーマの構文と XML フォーマット ファイルのその他のサンプルに関する詳細については、「[XML フォーマット ファイル &#40;SQL Server&#41;](xml-format-files-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c0881-141">For information about the syntax of the XML Schema and additional samples of XML format files, see [XML Format Files &#40;SQL Server&#41;](xml-format-files-sql-server.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0881-142">参照</span><span class="sxs-lookup"><span data-stu-id="c0881-142">See Also</span></span>  
 <span data-ttu-id="c0881-143">[bcp ユーティリティ](../../tools/bcp-utility.md) </span><span class="sxs-lookup"><span data-stu-id="c0881-143">[bcp Utility](../../tools/bcp-utility.md) </span></span>  
 <span data-ttu-id="c0881-144">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c0881-144">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span></span>  
 <span data-ttu-id="c0881-145">[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c0881-145">[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span></span>  
 <span data-ttu-id="c0881-146">[フォーマット ファイルを使用したテーブル列のスキップ &#40;SQL Server&#41;](use-a-format-file-to-skip-a-table-column-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="c0881-146">[Use a Format File to Skip a Table Column &#40;SQL Server&#41;](use-a-format-file-to-skip-a-table-column-sql-server.md) </span></span>  
 [<span data-ttu-id="c0881-147">フォーマット ファイルを使用したテーブル列とデータ ファイル フィールドのマッピング &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="c0881-147">Use a Format File to Map Table Columns to Data-File Fields &#40;SQL Server&#41;</span></span>](use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)  
  
  
