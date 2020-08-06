---
title: データのインポートまたはエクスポート用のフォーマット ファイル (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- bulk exporting [SQL Server], format files
- bulk importing [SQL Server], format files
- format files [SQL Server]
ms.assetid: b7b97d68-4336-4091-aee4-1941fab568e3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1143690f0322fef2612fde51eebcb7427ee237ce
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643347"
---
# <a name="format-files-for-importing-or-exporting-data-sql-server"></a><span data-ttu-id="25ff6-102">データのインポートまたはエクスポート用のフォーマット ファイル (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="25ff6-102">Format Files for Importing or Exporting Data (SQL Server)</span></span>
  <span data-ttu-id="25ff6-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルにデータを一括インポートしたり、テーブルからデータを一括エクスポートしたりする場合、 *フォーマット ファイル* を使用して、データの一括エクスポートと一括インポートに必要なすべてのフォーマット情報を格納できます。</span><span class="sxs-lookup"><span data-stu-id="25ff6-103">When you bulk import data into a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table or bulk export data from a table, you can use a *format file* to store all the format information that is required to bulk export or bulk import data.</span></span> <span data-ttu-id="25ff6-104">これには、そのテーブルに対応するデータ ファイル内の各フィールドのフォーマット情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="25ff6-104">This includes format information for each field in a data file relative to that table.</span></span>  
  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="25ff6-105">では、次の 2 種類のフォーマット ファイルがサポートされます: XML の形式と XML 以外のフォーマット ファイル。</span><span class="sxs-lookup"><span data-stu-id="25ff6-105">supports two types of format files: XML formats and non-XML format files.</span></span> <span data-ttu-id="25ff6-106">XML 以外のフォーマット ファイルにも XML フォーマット ファイルにもデータ ファイル内のすべてのフィールドの説明が含まれており、XML フォーマット ファイルには対応するテーブル列の説明も含まれています。</span><span class="sxs-lookup"><span data-stu-id="25ff6-106">Both non-XML format files and XML format files contain descriptions of every field in a data file, and XML format files also contain descriptions of the corresponding table columns.</span></span> <span data-ttu-id="25ff6-107">通常は、XML フォーマット ファイルと XML 以外のフォーマット ファイルの間には互換性があります。</span><span class="sxs-lookup"><span data-stu-id="25ff6-107">Generally, XML and non-XML format files are interchangeable.</span></span> <span data-ttu-id="25ff6-108">ただし、XML フォーマット ファイルの方が XML 以外のフォーマット ファイルよりも優れた点がいくつかあるので、新しいフォーマット ファイルには XML 構文を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="25ff6-108">However, we recommend that you use the XML syntax for new format files because they provide several advantages over non-XML format files.</span></span> <span data-ttu-id="25ff6-109">詳細については、「 [XML フォーマット ファイル &#40;SQL Server&#41;](xml-format-files-sql-server.md)です。</span><span class="sxs-lookup"><span data-stu-id="25ff6-109">For more information, see [XML Format Files &#40;SQL Server&#41;](xml-format-files-sql-server.md).</span></span>  
  
 
  
##  <a name="benefits-of-format-files"></a><a name="Benefits"></a> <span data-ttu-id="25ff6-110">フォーマット ファイルの利点</span><span class="sxs-lookup"><span data-stu-id="25ff6-110">Benefits of Format Files</span></span>  
  
-   <span data-ttu-id="25ff6-111">他のデータ形式に準拠したり、他のソフトウェアからデータ ファイルを読み取るための編集をほとんど (あるいはまったく) 行うことなく、データ ファイルを出力できる柔軟なシステムが実現します。</span><span class="sxs-lookup"><span data-stu-id="25ff6-111">Provides a flexible system for writing data files that requires little or no editing to comply with other data formats or to read data files from other software.</span></span>  
  
-   <span data-ttu-id="25ff6-112">不要なデータを追加または削除したり、データ ファイル内の既存のデータを並べ替えたりしなくても、データを一括インポートできます。</span><span class="sxs-lookup"><span data-stu-id="25ff6-112">Enables you to bulk import data without having to add or delete unnecessary data or to reorder existing data in the data file.</span></span> <span data-ttu-id="25ff6-113">フォーマット ファイルは、データ ファイルのフィールドとテーブルの列間に不一致がある場合に特に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="25ff6-113">Format files are particularly useful when a mismatch exists between fields in the data file and columns in the table.</span></span>  
  
##  <a name="examples-of-format-files"></a><a name="ExamplesOfFFs"></a> <span data-ttu-id="25ff6-114">フォーマット ファイルの例</span><span class="sxs-lookup"><span data-stu-id="25ff6-114">Examples of Format Files</span></span>  
 <span data-ttu-id="25ff6-115">次の例では、XML 以外のフォーマット ファイルと XML フォーマット ファイルのレイアウトを示します。</span><span class="sxs-lookup"><span data-stu-id="25ff6-115">The following examples show the layout of a non-XML format file and of an XML format file.</span></span> <span data-ttu-id="25ff6-116">これらのフォーマット ファイルは、 `HumanResources.myTeam` サンプル データベースの [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] テーブルに対応しています。</span><span class="sxs-lookup"><span data-stu-id="25ff6-116">These format files correspond to the `HumanResources.myTeam` table in the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database.</span></span> <span data-ttu-id="25ff6-117">このテーブルには、 `EmployeeID`、 `Name`、 `Title`、および `ModifiedDate`という 4 つの列があります。</span><span class="sxs-lookup"><span data-stu-id="25ff6-117">This table contains four columns: `EmployeeID`, `Name`, `Title`, and `ModifiedDate`.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="25ff6-118">このテーブルの詳細とテーブルを作成する方法については、「[HumanResources.myTeam サンプル テーブル &#40;SQL Server&#41;](humanresources-myteam-sample-table-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="25ff6-118">For information about this table and how to create it, see [HumanResources.myTeam Sample Table &#40;SQL Server&#41;](humanresources-myteam-sample-table-sql-server.md).</span></span>  
  
### <a name="a-using-a-non-xml-format-file"></a><span data-ttu-id="25ff6-119">A.</span><span class="sxs-lookup"><span data-stu-id="25ff6-119">A.</span></span> <span data-ttu-id="25ff6-120">XML 以外のフォーマット ファイルの使用</span><span class="sxs-lookup"><span data-stu-id="25ff6-120">Using a non-XML format file</span></span>  
 <span data-ttu-id="25ff6-121">次に示す XML 以外のフォーマット ファイルでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルに `HumanResources.myTeam` ネイティブ データ形式を使用します。</span><span class="sxs-lookup"><span data-stu-id="25ff6-121">The following non-XML format file uses the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native data format for the `HumanResources.myTeam` table.</span></span> <span data-ttu-id="25ff6-122">このフォーマット ファイルは、次の `bcp` コマンドを使用して作成されました。</span><span class="sxs-lookup"><span data-stu-id="25ff6-122">This format file was created by using the following `bcp` command.</span></span>  
  
```  
bcp AdventureWorks.HumanResources.myTeam format nul -f myTeam.Fmt -n -T   
The contents of this format file are as follows: 9.0  
4  
1       SQLSMALLINT   0       2       ""   1     EmployeeID               ""  
2       SQLNCHAR      2       100     ""   2     Name                     SQL_Latin1_General_CP1_CI_AS  
3       SQLNCHAR      2       100     ""   3     Title                    SQL_Latin1_General_CP1_CI_AS  
4       SQLNCHAR      2       100     ""   4     Background               SQL_Latin1_General_CP1_CI_AS  
```  
  
 <span data-ttu-id="25ff6-123">詳細については、「 [XML 以外のフォーマット ファイル &#40;SQL Server&#41;](non-xml-format-files-sql-server.md)でサポートされる従来のフォーマットです。</span><span class="sxs-lookup"><span data-stu-id="25ff6-123">For more information, see [Non-XML Format Files &#40;SQL Server&#41;](non-xml-format-files-sql-server.md).</span></span>  
  
 
  
### <a name="b-using-an-xml-format-file"></a><span data-ttu-id="25ff6-124">B.</span><span class="sxs-lookup"><span data-stu-id="25ff6-124">B.</span></span> <span data-ttu-id="25ff6-125">XML フォーマット ファイルの使用</span><span class="sxs-lookup"><span data-stu-id="25ff6-125">Using an XML format file</span></span>  
 <span data-ttu-id="25ff6-126">次に示す XML フォーマット ファイルでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルに `HumanResources.myTeam` ネイティブ データ形式を使用します。</span><span class="sxs-lookup"><span data-stu-id="25ff6-126">The following XML format file uses the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native data format for the `HumanResources.myTeam` table.</span></span> <span data-ttu-id="25ff6-127">このフォーマット ファイルは、次の `bcp` コマンドを使用して作成されました。</span><span class="sxs-lookup"><span data-stu-id="25ff6-127">This format file was created by using the following `bcp` command.</span></span>  
  
```  
bcp AdventureWorks.HumanResources.myTeam format nul -f myTeam.Xml -x -n -T   
```  
  
 <span data-ttu-id="25ff6-128">このフォーマット ファイルの内容を次に示します。</span><span class="sxs-lookup"><span data-stu-id="25ff6-128">The format file contains:</span></span>  
  
```  
 <?xml version="1.0"?>  
<BCPFORMAT xmlns="https://schemas.microsoft.com/sqlserver/2004/bulkload/format" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
 <RECORD>  
  <FIELD ID="1" xsi:type="NativePrefix" LENGTH="1"/>  
  <FIELD ID="2" xsi:type="NCharPrefix" PREFIX_LENGTH="2" MAX_LENGTH="100" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
  <FIELD ID="3" xsi:type="NCharPrefix" PREFIX_LENGTH="2" MAX_LENGTH="100" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
  <FIELD ID="4" xsi:type="NCharPrefix" PREFIX_LENGTH="2" MAX_LENGTH="100" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
 </RECORD>  
 <ROW>  
  <COLUMN SOURCE="1" NAME="EmployeeID" xsi:type="SQLSMALLINT"/>  
  <COLUMN SOURCE="2" NAME="Name" xsi:type="SQLNVARCHAR"/>  
  <COLUMN SOURCE="3" NAME="Title" xsi:type="SQLNVARCHAR"/>  
  <COLUMN SOURCE="4" NAME="Background" xsi:type="SQLNVARCHAR"/>  
 </ROW>  
</BCPFORMAT>  
```  
  
 <span data-ttu-id="25ff6-129">詳細については、「 [XML フォーマット ファイル &#40;SQL Server&#41;](xml-format-files-sql-server.md)です。</span><span class="sxs-lookup"><span data-stu-id="25ff6-129">For more information, see [XML Format Files &#40;SQL Server&#41;](xml-format-files-sql-server.md).</span></span>  
  

  
##  <a name="when-is-a-format-file-required"></a><a name="WhenFFrequired"></a> <span data-ttu-id="25ff6-130">フォーマット ファイルが必要になるケース</span><span class="sxs-lookup"><span data-stu-id="25ff6-130">When Is a Format File Required?</span></span>  
 <span data-ttu-id="25ff6-131">INSERT ...SELECT \* FROM OPENROWSET(BULK...) ステートメントでは、常にフォーマット ファイルが必要です。</span><span class="sxs-lookup"><span data-stu-id="25ff6-131">An INSERT ... SELECT \* FROM OPENROWSET(BULK...) statement always requires a format file.</span></span>  
  
-   <span data-ttu-id="25ff6-132">**bcp** または BULK INSERT の場合、単純な状況では、フォーマット ファイルを使用しなくてもかまいません。必要になることはほとんどありません。</span><span class="sxs-lookup"><span data-stu-id="25ff6-132">For **bcp** or BULK INSERT, in simple situations, using a format file is optional and rarely necessary.</span></span> <span data-ttu-id="25ff6-133">ただし、複雑な一括インポート操作を実行する場合は、頻繁にフォーマット ファイルが必要になります。</span><span class="sxs-lookup"><span data-stu-id="25ff6-133">However, for complex bulk-import situations, a format file is frequently required.</span></span>  
  
 <span data-ttu-id="25ff6-134">次の場合は、フォーマット ファイルが必要です。</span><span class="sxs-lookup"><span data-stu-id="25ff6-134">Format files are required if:</span></span>  
  
-   <span data-ttu-id="25ff6-135">1 つのデータ ファイルが、スキーマが異なる複数のテーブルのソースとして使用される場合。</span><span class="sxs-lookup"><span data-stu-id="25ff6-135">The same data file is used as a source for multiple tables that have different schemas.</span></span>  
  
-   <span data-ttu-id="25ff6-136">データ ファイルのフィールド数と対象のテーブルの列数が異なる場合。次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="25ff6-136">The data file has a different number of fields that the target table has columns; for example:</span></span>  
  
    -   <span data-ttu-id="25ff6-137">対象のテーブルに、既定値が定義されているか、NULL 値が許可されている列が 1 つ以上含まれている。</span><span class="sxs-lookup"><span data-stu-id="25ff6-137">The target table contains at least one column for which either a default value is defined or NULL is allowed.</span></span>  
  
    -   <span data-ttu-id="25ff6-138">ユーザーがテーブルの 1 つ以上の列に対する SELECT/INSERT 権限を持っていない。</span><span class="sxs-lookup"><span data-stu-id="25ff6-138">The users do not have SELECT/INSERT permissions on one or more columns in the table.</span></span>  
  
    -   <span data-ttu-id="25ff6-139">スキーマが異なる複数のテーブルで、1 つのデータ ファイルが使用されている。</span><span class="sxs-lookup"><span data-stu-id="25ff6-139">A single data file is used with two or more tables that have different schemas.</span></span>  
  
-   <span data-ttu-id="25ff6-140">列の順序がデータ ファイルとテーブルとの間で異なる場合。</span><span class="sxs-lookup"><span data-stu-id="25ff6-140">The column order is different for the data file and table.</span></span>  
  
-   <span data-ttu-id="25ff6-141">終了文字またはプレフィックス長がデータ ファイルの列によって異なる場合。</span><span class="sxs-lookup"><span data-stu-id="25ff6-141">The terminating characters or prefix lengths differ among the columns of the data file.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="25ff6-142">フォーマット ファイルが存在しない場合に、 **bcp** コマンドで data-format スイッチ ( **-n**、 **-c**、 **-w**、または **-N**) を指定するか、BULK INSERT 操作で DATAFILETYPE オプションを指定すると、指定したデータ形式がデータ ファイルのフィールドを解釈するための既定の方法として使用されます。</span><span class="sxs-lookup"><span data-stu-id="25ff6-142">In the absence of a format file, if a **bcp** command specifies a data-format switch (**-n**, **-c**, **-w**, or **-N**) or a BULK INSERT operation specifies the DATAFILETYPE option, the specified data format is used as the default method of interpreting the fields of the data file.</span></span>  
  
 
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="25ff6-143">関連タスク</span><span class="sxs-lookup"><span data-stu-id="25ff6-143">Related Tasks</span></span>  
  
-   [<span data-ttu-id="25ff6-144">フォーマット ファイルの作成 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="25ff6-144">Create a Format File &#40;SQL Server&#41;</span></span>](create-a-format-file-sql-server.md)  
  
-   [<span data-ttu-id="25ff6-145">データの一括インポートでのフォーマット ファイルの使用 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="25ff6-145">Use a Format File to Bulk Import Data &#40;SQL Server&#41;</span></span>](use-a-format-file-to-bulk-import-data-sql-server.md)  
  
-   [<span data-ttu-id="25ff6-146">フォーマット ファイルを使用したテーブル列のスキップ &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="25ff6-146">Use a Format File to Skip a Table Column &#40;SQL Server&#41;</span></span>](use-a-format-file-to-skip-a-table-column-sql-server.md)  
  
-   [<span data-ttu-id="25ff6-147">フォーマット ファイルを使用したデータ フィールドのスキップ &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="25ff6-147">Use a Format File to Skip a Data Field &#40;SQL Server&#41;</span></span>](use-a-format-file-to-skip-a-data-field-sql-server.md)  
  
-   [<span data-ttu-id="25ff6-148">フォーマット ファイルを使用したテーブル列とデータ ファイル フィールドのマッピング &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="25ff6-148">Use a Format File to Map Table Columns to Data-File Fields &#40;SQL Server&#41;</span></span>](use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)  
  

  
## <a name="see-also"></a><span data-ttu-id="25ff6-149">参照</span><span class="sxs-lookup"><span data-stu-id="25ff6-149">See Also</span></span>  
 <span data-ttu-id="25ff6-150">[XML 以外のフォーマット ファイル &#40;SQL Server&#41;](non-xml-format-files-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="25ff6-150">[Non-XML Format Files &#40;SQL Server&#41;](non-xml-format-files-sql-server.md) </span></span>  
 <span data-ttu-id="25ff6-151">[XML フォーマット ファイル &#40;SQL Server&#41;](xml-format-files-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="25ff6-151">[XML Format Files &#40;SQL Server&#41;](xml-format-files-sql-server.md) </span></span>  
 [<span data-ttu-id="25ff6-152">一括インポートまたは一括エクスポートのデータ形式 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="25ff6-152">Data Formats for Bulk Import or Bulk Export &#40;SQL Server&#41;</span></span>](data-formats-for-bulk-import-or-bulk-export-sql-server.md)  
  
  
