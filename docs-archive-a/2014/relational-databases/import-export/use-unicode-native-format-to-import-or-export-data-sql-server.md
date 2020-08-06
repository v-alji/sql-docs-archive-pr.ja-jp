---
title: Unicode ネイティブ形式を使用したデータのインポートまたはエクスポート (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- Unicode [SQL Server], bulk importing and exporting
- data formats [SQL Server], Unicode native
ms.assetid: a6213308-f3d5-406e-9029-19d8bb3367f3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: beae2f836de16dedf3be6d8c196910c53be02266
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741022"
---
# <a name="use-unicode-native-format-to-import-or-export-data-sql-server"></a><span data-ttu-id="98a6e-102">Unicode ネイティブ形式を使用したデータのインポートまたはエクスポート (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="98a6e-102">Use Unicode Native Format to Import or Export Data (SQL Server)</span></span>
  <span data-ttu-id="98a6e-103">Unicode ネイティブ形式は、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインストール環境間で情報をコピーする必要がある場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="98a6e-103">Unicode native format is helpful when information must be copied from one [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation to another.</span></span> <span data-ttu-id="98a6e-104">非文字データに対してネイティブ形式を使用すると、時間を節約でき、文字形式との間でデータ型の不要な変換が行われなくなります。</span><span class="sxs-lookup"><span data-stu-id="98a6e-104">The use of native format for noncharacter data saves time, eliminating unnecessary conversion of data types to and from character format.</span></span> <span data-ttu-id="98a6e-105">すべての文字データに対して Unicode 文字形式を使用すると、異なるコード ページを使用している複数のサーバー間でデータを一括転送するときに、拡張文字の損失を防ぐことができます。</span><span class="sxs-lookup"><span data-stu-id="98a6e-105">The use of Unicode character format for all character data prevents loss of any extended characters during bulk transfer of data between servers using different code pages.</span></span> <span data-ttu-id="98a6e-106">Unicode ネイティブ形式のデータ ファイルは、すべての一括インポート方法で読み取ることができます。</span><span class="sxs-lookup"><span data-stu-id="98a6e-106">A data file in Unicode native format can be read by any bulk-import method.</span></span>  
  
 <span data-ttu-id="98a6e-107">拡張文字や DBCS 文字を含むデータ ファイルを使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の複数のインスタンス間でデータを一括転送する場合は、Unicode ネイティブ形式を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="98a6e-107">Unicode native format is recommended for the bulk transfer of data between multiple instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using a data file that contains extended or DBCS characters.</span></span> <span data-ttu-id="98a6e-108">非文字データの場合、Unicode ネイティブ形式ではネイティブ (データベース) データ型が使用されます。</span><span class="sxs-lookup"><span data-stu-id="98a6e-108">For noncharacter data, Unicode native format uses native (database) data types.</span></span> <span data-ttu-id="98a6e-109">`char`、`nchar`、`varchar`、`nvarchar`、`text`、`varchar(max)`、`nvarchar(max)`、`ntext` などの文字データの場合、Unicode ネイティブ形式では Unicode 文字データ形式が使用されます。</span><span class="sxs-lookup"><span data-stu-id="98a6e-109">For character data, such as `char`, `nchar`, `varchar`, `nvarchar`, `text`, `varchar(max)`, `nvarchar(max)`, and `ntext`, the Unicode native format uses Unicode character data format.</span></span>  
  
 <span data-ttu-id="98a6e-110">Unicode ネイティブ形式のデータ ファイルに SQLVARIANT として格納される `sql_variant` データは、ネイティブ形式のデータ ファイルに格納される場合と同様に動作します。ただし、`char` と `varchar` の値がそれぞれ `nchar` と `nvarchar` に変換される点を除きます。この場合、影響を受ける列で 2 倍のストレージが必要になります。</span><span class="sxs-lookup"><span data-stu-id="98a6e-110">The `sql_variant` data that is stored as a SQLVARIANT in a Unicode native-format data file operates in the same manner as it does in a native-format data file, except that `char` and `varchar` values are converted to `nchar` and `nvarchar`, which doubles the amount of storage required for the affected columns.</span></span> <span data-ttu-id="98a6e-111">元のメタデータは保持され、値はテーブル列に一括インポートされるときに、元の `char` データ型や `varchar` データ型に再び変換されます。</span><span class="sxs-lookup"><span data-stu-id="98a6e-111">The original metadata is preserved, and the values are converted back to their original `char` and `varchar` data type when bulk imported into a table column.</span></span>  
  
## <a name="command-options-for-unicode-native-format"></a><span data-ttu-id="98a6e-112">Unicode ネイティブ形式のコマンド オプション</span><span class="sxs-lookup"><span data-stu-id="98a6e-112">Command Options for Unicode Native Format</span></span>  
 <span data-ttu-id="98a6e-113">Unicode ネイティブ形式のデータをテーブルにインポートするには、 **bcp**、BULK INSERT または INSERT...SELECT \* FROM OPENROWSET (BULK...) を選択します。**Bcp**コマンドまたは BULK INSERT ステートメントの場合は、コマンドラインでデータ形式を指定できます。</span><span class="sxs-lookup"><span data-stu-id="98a6e-113">You can import Unicode native format data into a table using **bcp**, BULK INSERT or INSERT ... SELECT \* FROM OPENROWSET(BULK...). For a **bcp** command or BULK INSERT statement, you can specify the data format on the command line.</span></span> <span data-ttu-id="98a6e-114">INSERT ...SELECT \* FROM OPENROWSET(BULK...) ステートメントの場合は、フォーマット ファイルでデータ形式を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="98a6e-114">For an INSERT ... SELECT \* FROM OPENROWSET(BULK...) statement, you must specify the data format in a format file.</span></span>  
  
 <span data-ttu-id="98a6e-115">Unicode ネイティブ形式は、次のオプションでサポートされています。</span><span class="sxs-lookup"><span data-stu-id="98a6e-115">Unicode native format is supported by the following options:</span></span>  
  
|<span data-ttu-id="98a6e-116">command</span><span class="sxs-lookup"><span data-stu-id="98a6e-116">Command</span></span>|<span data-ttu-id="98a6e-117">オプション</span><span class="sxs-lookup"><span data-stu-id="98a6e-117">Option</span></span>|<span data-ttu-id="98a6e-118">[説明]</span><span class="sxs-lookup"><span data-stu-id="98a6e-118">Description</span></span>|  
|-------------|------------|-----------------|  
|<span data-ttu-id="98a6e-119">**bcp**</span><span class="sxs-lookup"><span data-stu-id="98a6e-119">**bcp**</span></span>|<span data-ttu-id="98a6e-120">**-N**</span><span class="sxs-lookup"><span data-stu-id="98a6e-120">**-N**</span></span>|<span data-ttu-id="98a6e-121">**Bcp**ユーティリティで unicode ネイティブ形式が使用されるようにします。 unicode ネイティブ形式では、すべての非文字データに対してネイティブ (データベース) データ型が使用され、すべての文字 (、、、、 `char` `nchar` `varchar` `nvarchar` `text` 、および) データに対して unicode 文字データ形式が使用さ `ntext` れます。</span><span class="sxs-lookup"><span data-stu-id="98a6e-121">Causes the **bcp** utility to use the Unicode native format, which uses native (database) data types for all noncharacter data and Unicode character data format for all character (`char`, `nchar`, `varchar`, `nvarchar`, `text`, and `ntext`) data.</span></span>|  
|<span data-ttu-id="98a6e-122">BULK INSERT</span><span class="sxs-lookup"><span data-stu-id="98a6e-122">BULK INSERT</span></span>|<span data-ttu-id="98a6e-123">DATAFILETYPE **= '** widenative **'**</span><span class="sxs-lookup"><span data-stu-id="98a6e-123">DATAFILETYPE **='** widenative **'**</span></span>|<span data-ttu-id="98a6e-124">データの一括インポート時に Unicode ネイティブ形式を使用します。</span><span class="sxs-lookup"><span data-stu-id="98a6e-124">Use Unicode native format when bulk importing data.</span></span>|  
  
 <span data-ttu-id="98a6e-125">詳細については、「[bcp ユーティリティ](../../tools/bcp-utility.md)」、「[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql)」、または「[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="98a6e-125">For more information, see [bcp Utility](../../tools/bcp-utility.md), [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql), or [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="98a6e-126">また、フォーマット ファイルでフィールドごとに形式を指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="98a6e-126">Alternatively, you can specify formatting on a per-field basis in a format file.</span></span> <span data-ttu-id="98a6e-127">詳細については、「 [データのインポートまたはエクスポート用のフォーマット ファイル &#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="98a6e-127">For more information, see [Format Files for Importing or Exporting Data &#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="98a6e-128">例</span><span class="sxs-lookup"><span data-stu-id="98a6e-128">Examples</span></span>  
 <span data-ttu-id="98a6e-129">次の例では、**bcp** を使用してネイティブ データを一括エクスポートする方法と、BULK INSERT を使用して同じデータを一括インポートする方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="98a6e-129">The following examples demonstrate how to bulk export native data using **bcp** and bulk import the same data using BULK INSERT.</span></span>  
  
### <a name="sample-table"></a><span data-ttu-id="98a6e-130">サンプル テーブル</span><span class="sxs-lookup"><span data-stu-id="98a6e-130">Sample Table</span></span>  
 <span data-ttu-id="98a6e-131">次の例を実行するには、**dbo** スキーマに基づいて、**myTestUniNativeData** という名前のテーブルを **AdventureWorks** サンプル データベース内に作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="98a6e-131">The examples require that a table named **myTestUniNativeData** table be created in the **AdventureWorks** sample database under the **dbo** schema.</span></span> <span data-ttu-id="98a6e-132">このテーブルを作成しないと、例を実行できません。</span><span class="sxs-lookup"><span data-stu-id="98a6e-132">Before you can run the examples, you must create this table.</span></span> <span data-ttu-id="98a6e-133">[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] クエリ エディターで、次のコードを実行します。</span><span class="sxs-lookup"><span data-stu-id="98a6e-133">In [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] Query Editor, execute:</span></span>  
  
```  
USE AdventureWorks;  
GO  
CREATE TABLE myTestUniNativeData (  
   Col1 smallint,  
   Col2 nvarchar(50),  
   Col3 nvarchar(50)  
   );   
```  
  
 <span data-ttu-id="98a6e-134">このテーブルを作成し、上記のコードにより生成された内容を表示するには、次のステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="98a6e-134">To populate this table and view the resulting contents execute the following statements:</span></span>  
  
```  
INSERT INTO myTestUniNativeData(Col1,Col2,Col3)  
   VALUES(1,'DataField2','DataField3');  
INSERT INTO myTestUniNativeData(Col1,Col2,Col3)  
   VALUES(2,'DataField2','DataField3');  
GO  
SELECT Col1,Col2,Col3 FROM myTestUniNativeData  
  
```  
  
### <a name="using-bcp-to-bulk-export-native-data"></a><span data-ttu-id="98a6e-135">bcp を使用したネイティブ データの一括エクスポート</span><span class="sxs-lookup"><span data-stu-id="98a6e-135">Using bcp to Bulk Export Native Data</span></span>  
 <span data-ttu-id="98a6e-136">テーブルからデータ ファイルにデータをエクスポートするには、 **bcp** で **out** オプションと次の修飾子を組み合わせて使用します。</span><span class="sxs-lookup"><span data-stu-id="98a6e-136">To export data from the table to the data file, use **bcp** with the **out** option and the following qualifiers:</span></span>  
  
|<span data-ttu-id="98a6e-137">修飾子</span><span class="sxs-lookup"><span data-stu-id="98a6e-137">Qualifiers</span></span>|<span data-ttu-id="98a6e-138">説明</span><span class="sxs-lookup"><span data-stu-id="98a6e-138">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="98a6e-139">**-N**</span><span class="sxs-lookup"><span data-stu-id="98a6e-139">**-N**</span></span>|<span data-ttu-id="98a6e-140">ネイティブ データ型を指定します。</span><span class="sxs-lookup"><span data-stu-id="98a6e-140">Specifies native data types.</span></span>|  
|<span data-ttu-id="98a6e-141">**-T**</span><span class="sxs-lookup"><span data-stu-id="98a6e-141">**-T**</span></span>|<span data-ttu-id="98a6e-142">**bcp** ユーティリティが統合セキュリティを使用した信頼関係接続を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続することを指定します。</span><span class="sxs-lookup"><span data-stu-id="98a6e-142">Specifies that the **bcp** utility connects to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] with a trusted connection using integrated security.</span></span> <span data-ttu-id="98a6e-143">**-T** を指定しない場合、正常にログインするには **-U** と **-P** を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="98a6e-143">If **-T** is not specified, you need to specify **-U** and **-P** to successfully log in.</span></span>|  
  
 <span data-ttu-id="98a6e-144">次の例では、ネイティブ形式のデータを `myTestUniNativeData` テーブルから `myTestUniNativeData-N.Dat` という名前の新しいデータ ファイルに一括エクスポートします。</span><span class="sxs-lookup"><span data-stu-id="98a6e-144">The following example bulk exports data in native format from the `myTestUniNativeData` table into a new data file named `myTestUniNativeData-N.Dat` data file.</span></span> <span data-ttu-id="98a6e-145">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows コマンド プロンプトで、次のように入力します。</span><span class="sxs-lookup"><span data-stu-id="98a6e-145">At the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows command prompt, enter:</span></span>  
  
```  
bcp AdventureWorks..myTestUniNativeData out C:\myTestUniNativeData-N.Dat -N -T  
  
```  
  
### <a name="using-bulk-insert-to-bulk-import-native-data"></a><span data-ttu-id="98a6e-146">BULK INSERT を使用したネイティブ データの一括インポート</span><span class="sxs-lookup"><span data-stu-id="98a6e-146">Using BULK INSERT to Bulk Import Native Data</span></span>  
 <span data-ttu-id="98a6e-147">次の例では、BULK INSERT を使用して、`myTestUniNativeData-N.Dat` データ ファイルのデータを `myTestUniNativeData` テーブルにインポートします。</span><span class="sxs-lookup"><span data-stu-id="98a6e-147">The following example uses BULK INSERT to import the data in the `myTestUniNativeData-N.Dat` data file into the `myTestUniNativeData` table.</span></span> <span data-ttu-id="98a6e-148">[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] クエリ エディターで、次のコードを実行します。</span><span class="sxs-lookup"><span data-stu-id="98a6e-148">In [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] Query Editor, execute:</span></span>  
  
```  
USE AdventureWorks;  
GO  
BULK INSERT myTestUniNativeData   
    FROM 'C:\myTestUniNativeData-N.Dat'   
   WITH (DATAFILETYPE='widenative');   
GO  
SELECT Col1,Col2,Col3 FROM myTestUniNativeData;  
GO  
  
```  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="98a6e-149">関連タスク</span><span class="sxs-lookup"><span data-stu-id="98a6e-149">Related Tasks</span></span>  
 <span data-ttu-id="98a6e-150">**一括インポートまたは一括エクスポートのデータ形式を使用するには**</span><span class="sxs-lookup"><span data-stu-id="98a6e-150">**To use data formats for bulk import or bulk export**</span></span>  
  
-   [<span data-ttu-id="98a6e-151">以前のバージョンの SQL Server からのネイティブ形式データおよび文字形式データのインポート</span><span class="sxs-lookup"><span data-stu-id="98a6e-151">Import Native and Character Format Data from Earlier Versions of SQL Server</span></span>](import-native-and-character-format-data-from-earlier-versions-of-sql-server.md)  
  
-   [<span data-ttu-id="98a6e-152">文字形式を使用したデータのインポートまたはエクスポート &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="98a6e-152">Use Character Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="98a6e-153">ネイティブ形式を使用したデータのインポートまたはエクスポート &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="98a6e-153">Use Native Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-native-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="98a6e-154">Unicode 文字形式を使用したデータのインポートまたはエクスポート &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="98a6e-154">Use Unicode Character Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-unicode-character-format-to-import-or-export-data-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="98a6e-155">参照</span><span class="sxs-lookup"><span data-stu-id="98a6e-155">See Also</span></span>  
 <span data-ttu-id="98a6e-156">[bcp ユーティリティ](../../tools/bcp-utility.md) </span><span class="sxs-lookup"><span data-stu-id="98a6e-156">[bcp Utility](../../tools/bcp-utility.md) </span></span>  
 <span data-ttu-id="98a6e-157">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="98a6e-157">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span></span>  
 <span data-ttu-id="98a6e-158">[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="98a6e-158">[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span></span>  
 [<span data-ttu-id="98a6e-159">データ型 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="98a6e-159">Data Types &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/data-types-transact-sql)  
  
  
