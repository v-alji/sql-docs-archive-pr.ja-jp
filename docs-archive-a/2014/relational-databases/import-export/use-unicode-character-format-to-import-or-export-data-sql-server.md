---
title: Unicode 文字形式を使用したデータのインポートまたはエクスポート (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- data formats [SQL Server], Unicode character
- Unicode [SQL Server], bulk importing and exporting
ms.assetid: 74342a11-c1c0-4746-b482-7f3537744a70
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 520ce1b4eed8dc11d6d3fe038969257aea1e90fd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741033"
---
# <a name="use-unicode-character-format-to-import-or-export-data-sql-server"></a><span data-ttu-id="923c4-102">Unicode 文字形式を使用したデータのインポートまたはエクスポート (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="923c4-102">Use Unicode Character Format to Import or Export Data (SQL Server)</span></span>
  <span data-ttu-id="923c4-103">拡張文字や DBCS 文字を含むデータ ファイルを使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の複数のインスタンス間でデータを一括転送する場合は、Unicode 文字形式を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="923c4-103">Unicode character format is recommended for bulk transfer of data between multiple instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using a data file that contains extended/DBCS characters.</span></span> <span data-ttu-id="923c4-104">Unicode 文字データ形式を使用すると、操作を実行するクライアントで使用しているコード ページとは異なるコード ページを使用して、サーバーからデータをエクスポートできます。</span><span class="sxs-lookup"><span data-stu-id="923c4-104">The Unicode character data format allows data to be exported from a server by using a code page that differs from the code page used by the client that is performing the operation.</span></span> <span data-ttu-id="923c4-105">このような場合、Unicode 文字形式を使用すると、次の利点があります。</span><span class="sxs-lookup"><span data-stu-id="923c4-105">In such cases, use of Unicode character format has the following advantages:</span></span>  
  
-   <span data-ttu-id="923c4-106">転送元のデータと転送先のデータが Unicode データ型の場合、Unicode 文字形式を使用するとすべての文字データが保持されます。</span><span class="sxs-lookup"><span data-stu-id="923c4-106">If the source and destination data are Unicode data types, use of Unicode character format preserves all of the character data.</span></span>  
  
-   <span data-ttu-id="923c4-107">転送元のデータと転送先のデータが Unicode 以外のデータ型の場合、Unicode 文字形式を使用すると、転送先のデータで表現できない転送元のデータに含まれる拡張文字の損失を最小限に抑えられます。</span><span class="sxs-lookup"><span data-stu-id="923c4-107">if the source and destination data are not Unicode data types, use of Unicode character format minimizes the loss of extended characters in the source data that cannot be represented at the destination.</span></span>  
  
 <span data-ttu-id="923c4-108">Unicode 文字形式のデータ ファイルは、Unicode ファイルの規則に従います。</span><span class="sxs-lookup"><span data-stu-id="923c4-108">Unicode character format data files follow the conventions for Unicode files.</span></span> <span data-ttu-id="923c4-109">ファイルの先頭の 2 バイトは、16 進数の 0xFFFE です。</span><span class="sxs-lookup"><span data-stu-id="923c4-109">The first two bytes of the file are hexadecimal numbers, 0xFFFE.</span></span> <span data-ttu-id="923c4-110">これらのバイトは、バイト順マークとしての役割を果たし、高位のバイトをファイルの先頭に格納するか、最後に格納するかを指定します。</span><span class="sxs-lookup"><span data-stu-id="923c4-110">These bytes serve as byte-order marks, specifying whether the high-order byte is stored first or last in the file.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="923c4-111">Unicode 文字データ ファイルを操作するフォーマット ファイルの場合、すべての入力フィールドが Unicode テキスト文字列 (つまり、固定サイズの Unicode 文字列または終端文字が指定された Unicode 文字列) でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="923c4-111">For a format file to work with a Unicode character data file, all the input fields must be Unicode text strings (that is, either fixed-size or character-terminated Unicode strings).</span></span>  
  
 <span data-ttu-id="923c4-112">Unicode 文字形式のデータ ファイルに格納されている `sql_variant` データの動作は、`nchar` データではなく `char` データとして格納されている点を除いて、文字形式のデータ ファイルの場合と同様になります。</span><span class="sxs-lookup"><span data-stu-id="923c4-112">The `sql_variant` data that is stored in a Unicode character-format data file operates in the same way it operates in a character-format data file, except that the data is stored as `nchar` instead of `char` data.</span></span> <span data-ttu-id="923c4-113">文字形式の詳細については、「 [Collation and Unicode Support](../collations/collation-and-unicode-support.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="923c4-113">For more information about character format, see [Collation and Unicode Support](../collations/collation-and-unicode-support.md).</span></span>  
  
 <span data-ttu-id="923c4-114">Unicode 文字形式に用意されている既定以外のフィールド ターミネータまたは行ターミネータを使用するには、「[フィールド ターミネータと行ターミネータの指定 &#40;SQL Server&#41;](specify-field-and-row-terminators-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="923c4-114">To use a field or row terminator other than the default that is provided with Unicode character format, see [Specify Field and Row Terminators &#40;SQL Server&#41;](specify-field-and-row-terminators-sql-server.md).</span></span>  
  
## <a name="command-options-for-unicode-character-format"></a><span data-ttu-id="923c4-115">Unicode 文字形式のコマンド オプション</span><span class="sxs-lookup"><span data-stu-id="923c4-115">Command Options for Unicode Character Format</span></span>  
 <span data-ttu-id="923c4-116">Unicode 文字形式のデータは、 **bcp**、BULK INSERT または INSERT...SELECT \* FROM OPENROWSET (BULK...) を選択します。**Bcp**コマンドまたは BULK INSERT ステートメントの場合は、コマンドラインでデータ形式を指定できます。</span><span class="sxs-lookup"><span data-stu-id="923c4-116">You can import Unicode character format data into a table using **bcp**, BULK INSERT or INSERT ... SELECT \* FROM OPENROWSET(BULK...). For a **bcp** command or BULK INSERT statement, you can specify the data format on the command line.</span></span> <span data-ttu-id="923c4-117">INSERT ...SELECT \* FROM OPENROWSET(BULK...) ステートメントの場合は、フォーマット ファイルでデータ形式を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="923c4-117">For an INSERT ... SELECT \* FROM OPENROWSET(BULK...) statement, you must specify the data format in a format file.</span></span>  
  
 <span data-ttu-id="923c4-118">Unicode 文字形式は、次のコマンド ライン オプションでサポートされています。</span><span class="sxs-lookup"><span data-stu-id="923c4-118">Unicode character format is supported by the following command line options:</span></span>  
  
|<span data-ttu-id="923c4-119">command</span><span class="sxs-lookup"><span data-stu-id="923c4-119">Command</span></span>|<span data-ttu-id="923c4-120">オプション</span><span class="sxs-lookup"><span data-stu-id="923c4-120">Option</span></span>|<span data-ttu-id="923c4-121">[説明]</span><span class="sxs-lookup"><span data-stu-id="923c4-121">Description</span></span>|  
|-------------|------------|-----------------|  
|<span data-ttu-id="923c4-122">**bcp**</span><span class="sxs-lookup"><span data-stu-id="923c4-122">**bcp**</span></span>|<span data-ttu-id="923c4-123">**-w**</span><span class="sxs-lookup"><span data-stu-id="923c4-123">**-w**</span></span>|<span data-ttu-id="923c4-124">Unicode 文字形式を使用します。</span><span class="sxs-lookup"><span data-stu-id="923c4-124">Uses the Unicode character format.</span></span>|  
|<span data-ttu-id="923c4-125">BULK INSERT</span><span class="sxs-lookup"><span data-stu-id="923c4-125">BULK INSERT</span></span>|<span data-ttu-id="923c4-126">DATAFILETYPE **= '** widechar **'**</span><span class="sxs-lookup"><span data-stu-id="923c4-126">DATAFILETYPE **='** widechar **'**</span></span>|<span data-ttu-id="923c4-127">データの一括インポート時に Unicode 文字形式を使用します。</span><span class="sxs-lookup"><span data-stu-id="923c4-127">Uses Unicode character format when bulk importing data.</span></span>|  
  
 <span data-ttu-id="923c4-128">詳細については、「[bcp ユーティリティ](../../tools/bcp-utility.md)」、「[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql)」、または「[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="923c4-128">For more information, see [bcp Utility](../../tools/bcp-utility.md), [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql), or [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="923c4-129">また、フォーマット ファイルでフィールドごとに形式を指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="923c4-129">Alternatively, you can specify formatting on a per-field basis in a format file.</span></span> <span data-ttu-id="923c4-130">詳細については、「 [データのインポートまたはエクスポート用のフォーマット ファイル &#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="923c4-130">For more information, see [Format Files for Importing or Exporting Data &#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="923c4-131">例</span><span class="sxs-lookup"><span data-stu-id="923c4-131">Examples</span></span>  
 <span data-ttu-id="923c4-132">次の例は、 **bcp** を使用して Unicode 文字データを一括エクスポートする方法と、BULK INSERT を使用して Unicode 文字データを一括インポートする方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="923c4-132">The following examples demonstrate how to bulk export Unicode character data using **bcp** and to bulk import the same data using BULK INSERT.</span></span>  
  
### <a name="sample-table"></a><span data-ttu-id="923c4-133">サンプル テーブル</span><span class="sxs-lookup"><span data-stu-id="923c4-133">Sample Table</span></span>  
 <span data-ttu-id="923c4-134">次の例を実行するには、 `myTestUniCharData` スキーマに基づいて、 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] という名前のテーブルを `dbo` サンプル データベース内に作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="923c4-134">The examples require that a table named `myTestUniCharData` table be created in the [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] sample database under the `dbo` schema.</span></span> <span data-ttu-id="923c4-135">このテーブルを作成しないと、例を実行できません。</span><span class="sxs-lookup"><span data-stu-id="923c4-135">Before you can run the examples, you must create this table.</span></span> <span data-ttu-id="923c4-136">このテーブルを作成するには、 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] クエリ エディターで、次のコードを実行します。</span><span class="sxs-lookup"><span data-stu-id="923c4-136">To create this table, in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] Query Editor, execute:</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
CREATE TABLE myTestUniCharData (  
   Col1 smallint,  
   Col2 nvarchar(50),  
   Col3 nvarchar(50)  
   );   
```  
  
 <span data-ttu-id="923c4-137">このテーブルを作成し、上記のコードにより生成された内容を表示するには、次のステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="923c4-137">To populate this table and view the resulting contents execute the following statements:</span></span>  
  
```  
INSERT INTO myTestUniCharData(Col1,Col2,Col3)  
   VALUES(1,'DataField2','DataField3')   
        ,(2,'DataField2','DataField3');  
GO  
SELECT Col1,Col2,Col3 FROM myTestUniCharData;  
  
```  
  
### <a name="using-bcp-to-bulk-export-unicode-character-data"></a><span data-ttu-id="923c4-138">bcp を使用した Unicode 文字データの一括エクスポート</span><span class="sxs-lookup"><span data-stu-id="923c4-138">Using bcp to Bulk Export Unicode Character Data</span></span>  
 <span data-ttu-id="923c4-139">テーブルからデータ ファイルにデータをエクスポートするには、 **bcp** で **out** オプションと次の修飾子を組み合わせて使用します。</span><span class="sxs-lookup"><span data-stu-id="923c4-139">To export data from the table to the data file, use **bcp** with the **out** option and the following qualifiers:</span></span>  
  
|<span data-ttu-id="923c4-140">修飾子</span><span class="sxs-lookup"><span data-stu-id="923c4-140">Qualifiers</span></span>|<span data-ttu-id="923c4-141">説明</span><span class="sxs-lookup"><span data-stu-id="923c4-141">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="923c4-142">**-w**</span><span class="sxs-lookup"><span data-stu-id="923c4-142">**-w**</span></span>|<span data-ttu-id="923c4-143">Unicode 文字形式を指定します。</span><span class="sxs-lookup"><span data-stu-id="923c4-143">Specifies Unicode character format.</span></span>|  
|<span data-ttu-id="923c4-144">**-t** `,`</span><span class="sxs-lookup"><span data-stu-id="923c4-144">**-t** `,`</span></span>|<span data-ttu-id="923c4-145">コンマ (`,`) をフィールド ターミネータとして指定します。</span><span class="sxs-lookup"><span data-stu-id="923c4-145">Specifies a comma (`,`) as the field terminator.</span></span><br /><br /> <span data-ttu-id="923c4-146">注: 既定のフィールドターミネータは、タブ Unicode 文字 (\t) です。</span><span class="sxs-lookup"><span data-stu-id="923c4-146">Note: The default field terminator is the tab Unicode character (\t).</span></span> <span data-ttu-id="923c4-147">詳細については、「 [フィールド ターミネータと行ターミネータの指定 &#40;SQL Server&#41;](specify-field-and-row-terminators-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="923c4-147">For more information, see [Specify Field and Row Terminators &#40;SQL Server&#41;](specify-field-and-row-terminators-sql-server.md).</span></span>|  
|<span data-ttu-id="923c4-148">**-T**</span><span class="sxs-lookup"><span data-stu-id="923c4-148">**-T**</span></span>|<span data-ttu-id="923c4-149">**bcp** ユーティリティが統合セキュリティを使用した信頼関係接続を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続することを指定します。</span><span class="sxs-lookup"><span data-stu-id="923c4-149">Specifies that the **bcp** utility connects to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] with a trusted connection using integrated security.</span></span> <span data-ttu-id="923c4-150">**-T** を指定しない場合、正常にログインするには **-U** と **-P** を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="923c4-150">If **-T** is not specified, you need to specify **-U** and **-P** to successfully log in.</span></span>|  
  
 <span data-ttu-id="923c4-151">次の例では、Unicode 文字形式のデータを `myTestUniCharData` テーブルから `myTestUniCharData-w.Dat` という名前の新しいデータ ファイルに一括エクスポートします。このデータ ファイルでは、フィールド ターミネータとしてコンマ (`,`) が使用されます。</span><span class="sxs-lookup"><span data-stu-id="923c4-151">The following example bulk exports data in Unicode character format from the `myTestUniCharData` table into a new data file named `myTestUniCharData-w.Dat` data file that uses the comma (`,`) as the field terminator.</span></span> <span data-ttu-id="923c4-152">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows コマンド プロンプトで、次のように入力します。</span><span class="sxs-lookup"><span data-stu-id="923c4-152">At the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows command prompt, enter:</span></span>  
  
```  
bcp AdventureWorks2012..myTestUniCharData out C:\myTestUniCharData-w.Dat -w -t, -T  
  
```  
  
### <a name="using-bulk-insert-to-bulk-import-unicode-character-data"></a><span data-ttu-id="923c4-153">BULK INSERT を使用した Unicode 文字データの一括インポート</span><span class="sxs-lookup"><span data-stu-id="923c4-153">Using BULK INSERT to Bulk Import Unicode Character Data</span></span>  
 <span data-ttu-id="923c4-154">次の例では、`BULK INSERT` を使用して、`myTestUniCharData-w.Dat` データ ファイルのデータを `myTestUniCharData` テーブルにインポートします。</span><span class="sxs-lookup"><span data-stu-id="923c4-154">The following example uses `BULK INSERT` to import the data in the `myTestUniCharData-w.Dat` data file into the `myTestUniCharData` table.</span></span> <span data-ttu-id="923c4-155">既定以外のフィールド ターミネータ (`,`) は、ステートメントで宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="923c4-155">The nondefault field terminator (`,`) must be declared in the statement.</span></span> <span data-ttu-id="923c4-156">[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] クエリ エディターで、次のコードを実行します。</span><span class="sxs-lookup"><span data-stu-id="923c4-156">In [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] Query Editor, execute:</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
BULK INSERT myTestUniCharData   
   FROM 'C:\myTestUniCharData-w.Dat'   
   WITH (  
      DATAFILETYPE='widechar',  
      FIELDTERMINATOR=','  
   );   
GO  
SELECT Col1,Col2,Col3 FROM myTestUniCharData;  
GO  
  
```  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="923c4-157">関連タスク</span><span class="sxs-lookup"><span data-stu-id="923c4-157">Related Tasks</span></span>  
 <span data-ttu-id="923c4-158">**一括インポートまたは一括エクスポートのデータ形式を使用するには**</span><span class="sxs-lookup"><span data-stu-id="923c4-158">**To use data formats for bulk import or bulk export**</span></span>  
  
-   [<span data-ttu-id="923c4-159">以前のバージョンの SQL Server からのネイティブ形式データおよび文字形式データのインポート</span><span class="sxs-lookup"><span data-stu-id="923c4-159">Import Native and Character Format Data from Earlier Versions of SQL Server</span></span>](import-native-and-character-format-data-from-earlier-versions-of-sql-server.md)  
  
-   [<span data-ttu-id="923c4-160">文字形式を使用したデータのインポートまたはエクスポート &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="923c4-160">Use Character Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="923c4-161">ネイティブ形式を使用したデータのインポートまたはエクスポート &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="923c4-161">Use Native Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-native-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="923c4-162">Unicode ネイティブ形式を使用したデータのインポートまたはエクスポート &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="923c4-162">Use Unicode Native Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-unicode-native-format-to-import-or-export-data-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="923c4-163">参照</span><span class="sxs-lookup"><span data-stu-id="923c4-163">See Also</span></span>  
 <span data-ttu-id="923c4-164">[bcp ユーティリティ](../../tools/bcp-utility.md) </span><span class="sxs-lookup"><span data-stu-id="923c4-164">[bcp Utility](../../tools/bcp-utility.md) </span></span>  
 <span data-ttu-id="923c4-165">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="923c4-165">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span></span>  
 <span data-ttu-id="923c4-166">[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="923c4-166">[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span></span>  
 <span data-ttu-id="923c4-167">[データ型 &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="923c4-167">[Data Types &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql) </span></span>  
 [<span data-ttu-id="923c4-168">照合順序と Unicode のサポート</span><span class="sxs-lookup"><span data-stu-id="923c4-168">Collation and Unicode Support</span></span>](../collations/collation-and-unicode-support.md)  
  
  
