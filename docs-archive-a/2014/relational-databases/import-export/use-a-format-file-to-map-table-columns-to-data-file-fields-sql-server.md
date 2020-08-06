---
title: フォーマット ファイルを使用したテーブル列とデータ ファイル フィールドのマッピング (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- mapping columns to fields during import [SQL Server]
- format files [SQL Server], mapping columns to fields
ms.assetid: e7ee4f7e-24c4-4eb7-84d2-41e57ccc1ef1
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c7de0b5ce486f187a1bdd27197984aa3c411f4a1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633847"
---
# <a name="use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server"></a><span data-ttu-id="26c9d-102">フォーマット ファイルを使用したテーブル列とデータ ファイル フィールドのマッピング (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="26c9d-102">Use a Format File to Map Table Columns to Data-File Fields (SQL Server)</span></span>
  <span data-ttu-id="26c9d-103">データ ファイルに含めるフィールドは、対応するテーブル内の列とは異なる順序に並べ替えることができます。</span><span class="sxs-lookup"><span data-stu-id="26c9d-103">A data file can contain fields arranged in a different order from the corresponding columns in the table.</span></span> <span data-ttu-id="26c9d-104">このトピックでは、テーブル列とは異なる順序にフィールドを並べ替えたデータ ファイルを格納できるように変更した XML フォーマット ファイルと XML 以外のフォーマット ファイルについて説明します。</span><span class="sxs-lookup"><span data-stu-id="26c9d-104">This topic presents both non-XML and XML format files that have been modified to accommodate a data file whose fields are arranged in a different order from the table columns.</span></span> <span data-ttu-id="26c9d-105">変更したフォーマット ファイルのデータ フィールドは、対応するテーブル列にマッピングされます。</span><span class="sxs-lookup"><span data-stu-id="26c9d-105">The modified format file maps the data fields to their corresponding table columns.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="26c9d-106">XML 以外のフォーマットファイルまたは XML フォーマットファイルを使用して、データファイルをテーブルに一括インポートできます。そのためには、 **bcp**コマンド、BULK INSERT ステートメント、または INSERT...SELECT \* FROM OPENROWSET (BULK...) ステートメント。</span><span class="sxs-lookup"><span data-stu-id="26c9d-106">Either a non-XML format file or an XML format file can be used to bulk import a data file into the table by using a **bcp** command, BULK INSERT statement, or INSERT ... SELECT \* FROM OPENROWSET(BULK...) statement.</span></span> <span data-ttu-id="26c9d-107">詳細については、「[データの一括インポートでのフォーマット ファイルの使用 &#40;SQL Server&#41;](use-a-format-file-to-bulk-import-data-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="26c9d-107">For more information, see [Use a Format File to Bulk Import Data &#40;SQL Server&#41;](use-a-format-file-to-bulk-import-data-sql-server.md).</span></span>  
  
## <a name="sample-table-and-data-file"></a><span data-ttu-id="26c9d-108">サンプル テーブルとデータ ファイル</span><span class="sxs-lookup"><span data-stu-id="26c9d-108">Sample Table and Data File</span></span>  
 <span data-ttu-id="26c9d-109">このトピックで例として変更するフォーマット ファイルは、次のテーブルとデータ ファイルに基づいています。</span><span class="sxs-lookup"><span data-stu-id="26c9d-109">The examples of modified format files in this topic are based on the following table and data file.</span></span>  
  
### <a name="sample-table"></a><span data-ttu-id="26c9d-110">サンプル テーブル</span><span class="sxs-lookup"><span data-stu-id="26c9d-110">Sample Table</span></span>  
 <span data-ttu-id="26c9d-111">このトピックの例を実行するには、`dbo` スキーマに基づいて、`myTestOrder` という名前のテーブルを [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] サンプル データベース内に作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="26c9d-111">The examples in this topic require that a table named `myTestOrder` be created in the [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] sample database under the `dbo` schema.</span></span> <span data-ttu-id="26c9d-112">このテーブルを作成するには、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] クエリ エディターで、次のコードを実行します。</span><span class="sxs-lookup"><span data-stu-id="26c9d-112">To create this table, in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Query Editor, execute the following code:</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
CREATE TABLE myTestOrder   
   (  
   Col1 smallint,  
   Col2 nvarchar(50) ,  
   Col3 nvarchar(50) ,   
   Col4 nvarchar(50)   
   );  
GO  
  
```  
  
### <a name="data-file"></a><span data-ttu-id="26c9d-113">データ ファイル</span><span class="sxs-lookup"><span data-stu-id="26c9d-113">Data File</span></span>  
 <span data-ttu-id="26c9d-114">データ ファイル `myTestOrder-c.txt` には、次のレコードが含まれています。</span><span class="sxs-lookup"><span data-stu-id="26c9d-114">The data file, `myTestOrder-c.txt`, contains the following records:</span></span>  
  
```  
DataField3,DataField2,1,DataField4  
DataField3,DataField2,1,DataField4  
DataField3,DataField2,1,DataField4  
  
```  
  
 <span data-ttu-id="26c9d-115">`myTestSkipCol2-c.dat` から `myTestSkipCol` テーブルにデータを一括インポートするには、フォーマット ファイルで 1 番目のデータ フィールドを `Col3`、2 番目のデータ フィールドを `Col2`、3 番目のデータ フィールドを `Col1`、4 番目のデータ フィールドを `Col4` にそれぞれマップする必要があります。</span><span class="sxs-lookup"><span data-stu-id="26c9d-115">To bulk import data from `myTestSkipCol2-c.dat` into the `myTestSkipCol` table, the format file must map the first data field to `Col3`, the second data field to `Col2`, the third data field to `Col1`, and the fourth data field to `Col4`.</span></span>  
  
## <a name="using-a-non-xml-format-file"></a><span data-ttu-id="26c9d-116">XML 以外のフォーマット ファイルの使用</span><span class="sxs-lookup"><span data-stu-id="26c9d-116">Using a Non-XML Format File</span></span>  
 <span data-ttu-id="26c9d-117">列の順序を表す値を、対応するデータ フィールドの位置を指すように変更することにより、列マッピングの順序を変更できます。</span><span class="sxs-lookup"><span data-stu-id="26c9d-117">You can change the order of a column mapping by changing the order value for the column to indicate the position of the corresponding data field.</span></span>  
  
 <span data-ttu-id="26c9d-118">次の XML 以外のフォーマット ファイルのサンプルは、`myTestOrder.fmt` のフィールドを `myTestOrder-c.txt` テーブルの列にマップするフォーマット ファイル `myTestOrder` を示しています。</span><span class="sxs-lookup"><span data-stu-id="26c9d-118">The following sample non-XML format file presents a format file, `myTestOrder.fmt`, that maps the fields in `myTestOrder-c.txt` to the columns of the `myTestOrder` table.</span></span> <span data-ttu-id="26c9d-119">データ ファイルとテーブルの作成方法の詳細については、このトピックの「サンプル テーブルとデータ ファイル」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="26c9d-119">For information about how to create the data file and table, see "Sample Table and Data File," earlier in this topic.</span></span> <span data-ttu-id="26c9d-120">このフォーマット ファイルでは、文字データ形式が使用されます。</span><span class="sxs-lookup"><span data-stu-id="26c9d-120">The format file uses character data format.</span></span>  
  
 <span data-ttu-id="26c9d-121">フォーマット ファイルには、次の情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="26c9d-121">The format file contains the following information:</span></span>  
  
```  
9.0  
4  
1       SQLCHAR       0       100     ","     3     Col3               SQL_Latin1_General_CP1_CI_AS  
2       SQLCHAR       0       100     ","     2     Col2               SQL_Latin1_General_CP1_CI_AS  
3       SQLCHAR       0       7       ","     1     Col1               ""  
4       SQLCHAR       0       100     "\r\n"  4     Col4               SQL_Latin1_General_CP1_CI_AS  
  
```  
  
> [!NOTE]  
>  <span data-ttu-id="26c9d-122">XML 以外のフォーマット ファイルのレイアウトについての詳細は、「[XML 以外のフォーマット ファイル &#40;SQL Server&#41;](xml-format-files-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="26c9d-122">For more information about the layout of non-XML format files, see [Non-XML Format Files &#40;SQL Server&#41;](xml-format-files-sql-server.md).</span></span>  
  
### <a name="example"></a><span data-ttu-id="26c9d-123">例</span><span class="sxs-lookup"><span data-stu-id="26c9d-123">Example</span></span>  
 <span data-ttu-id="26c9d-124">次の例では `BULK INSERT` ステートメントを実行し、XML 以外のフォーマット ファイル `myTestOrder-c.txt` を使用して `myTestOrder` データ ファイルから `myTestOrder.fmt` サンプル テーブルにデータを一括インポートします。</span><span class="sxs-lookup"><span data-stu-id="26c9d-124">The following example uses a `BULK INSERT` statement to bulk import data from the `myTestOrder-c.txt` data file into the `myTestOrder` sample table by using the `myTestOrder.fmt` non-XML format file.</span></span>  
  
 <span data-ttu-id="26c9d-125">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] クエリ エディターで、次のように実行します。</span><span class="sxs-lookup"><span data-stu-id="26c9d-125">In the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Query Editor, execute:</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
BULK INSERT myTestOrder  
FROM 'C:\myTestOrder-c.txt'   
WITH (formatfile='C:\myTestOrder.fmt');  
GO  
  
```  
  
## <a name="using-an-xml-format-file"></a><span data-ttu-id="26c9d-126">XML フォーマット ファイルの使用</span><span class="sxs-lookup"><span data-stu-id="26c9d-126">Using an XML Format File</span></span>  
 <span data-ttu-id="26c9d-127">次の XML 以外のフォーマット ファイルのサンプルは、`myTestOrder.xml` のフィールドを `myTestOrder-c.txt` テーブルの列にマップするフォーマット ファイル `myTestOrder` を示しています。データ ファイルとテーブルの作成方法の詳細については、このトピックの「サンプル テーブルとデータ ファイル」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="26c9d-127">The following sample non-XML format file presents a format file, `myTestOrder.xml`, that maps the fields in `myTestOrder-c.txt` to the columns of the `myTestOrder` table For information about how to create the data file and table, see "Sample Table and Data File," earlier in this topic.</span></span>  
  
 <span data-ttu-id="26c9d-128">`myTestOrder.xml` フォーマット ファイルには、次の情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="26c9d-128">The `myTestOrder.xml` format file contains the following information:</span></span>  
  
```  
<?xml version="1.0"?>  
<BCPFORMAT xmlns="https://schemas.microsoft.com/sqlserver/2004/bulkload/format"   
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
 <RECORD>  
  <FIELD ID="1" xsi:type="CharTerm" TERMINATOR="," MAX_LENGTH="100" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
  <FIELD ID="2" xsi:type="CharTerm" TERMINATOR="," MAX_LENGTH="100" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
  <FIELD ID="3" xsi:type="CharTerm" TERMINATOR="," MAX_LENGTH="7"/>  
  <FIELD ID="4" xsi:type="CharTerm" TERMINATOR="\r\n" MAX_LENGTH="100" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
 </RECORD>  
 <ROW>  
  <COLUMN SOURCE="3" NAME="Col1" xsi:type="SQLSMALLINT"/>  
  <COLUMN SOURCE="2" NAME="Col2" xsi:type="SQLNVARCHAR"/>  
  <COLUMN SOURCE="1" NAME="Col3" xsi:type="SQLNVARCHAR"/>  
  <COLUMN SOURCE="4" NAME="Col4" xsi:type="SQLNVARCHAR"/>  
 </ROW>  
</BCPFORMAT>  
  
```  
  
> [!NOTE]  
>  <span data-ttu-id="26c9d-129">XML スキーマの構文と XML フォーマット ファイルのその他のサンプルに関する詳細については、「[XML フォーマット ファイル &#40;SQL Server&#41;](xml-format-files-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="26c9d-129">For information about the syntax of the XML Schema and additional samples of XML format files, see [XML Format Files &#40;SQL Server&#41;](xml-format-files-sql-server.md).</span></span>  
  
### <a name="example"></a><span data-ttu-id="26c9d-130">例</span><span class="sxs-lookup"><span data-stu-id="26c9d-130">Example</span></span>  
 <span data-ttu-id="26c9d-131">次の例では `OPENROWSET` 一括行セット プロバイダーを実行し、XML フォーマット ファイル `myTestOrder-c.txt` を使用して `myTestOrder` データ ファイルから `myTestOrder.xml` サンプル テーブルにデータをインポートします。</span><span class="sxs-lookup"><span data-stu-id="26c9d-131">The following example uses the `OPENROWSET` bulk rowset provider to import data from the `myTestOrder-c.txt` data file into the `myTestOrder` sample table by using the `myTestOrder.xml` XML format file.</span></span> <span data-ttu-id="26c9d-132">`INSERT... SELECT` ステートメントの選択リストには、列リストを指定します。</span><span class="sxs-lookup"><span data-stu-id="26c9d-132">The `INSERT... SELECT` statement specifies the column list in the select list.</span></span>  
  
 <span data-ttu-id="26c9d-133">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] のクエリ エディターで、次のコードを実行します。</span><span class="sxs-lookup"><span data-stu-id="26c9d-133">In the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Query Editor, execute the following code:</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
INSERT INTO myTestOrder   
  SELECT Col1, Col2, Col3, Col4  
      FROM  OPENROWSET(BULK  'C:\myTestOrder-c.txt',  
      FORMATFILE='C:\myTestOrder.Xml'    
       ) AS t1;  
GO  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="26c9d-134">参照</span><span class="sxs-lookup"><span data-stu-id="26c9d-134">See Also</span></span>  
 <span data-ttu-id="26c9d-135">[フォーマット ファイルを使用したテーブル列のスキップ &#40;SQL Server&#41;](use-a-format-file-to-skip-a-table-column-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="26c9d-135">[Use a Format File to Skip a Table Column &#40;SQL Server&#41;](use-a-format-file-to-skip-a-table-column-sql-server.md) </span></span>  
 [<span data-ttu-id="26c9d-136">フォーマット ファイルを使用したデータ フィールドのスキップ &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="26c9d-136">Use a Format File to Skip a Data Field &#40;SQL Server&#41;</span></span>](use-a-format-file-to-skip-a-data-field-sql-server.md)  
  
  
