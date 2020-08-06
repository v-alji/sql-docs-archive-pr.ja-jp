---
title: ネイティブ形式を使用したデータのインポートまたはエクスポート (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- native data format [SQL Server]
- data formats [SQL Server], native
ms.assetid: eb279b2f-0f1f-428f-9b8f-2a7fc495b79f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ab42ba3eb6468aac3da2fa780d371818c8776690
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741037"
---
# <a name="use-native-format-to-import-or-export-data-sql-server"></a><span data-ttu-id="5e1ea-102">ネイティブ形式を使用したデータのインポートまたはエクスポート (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="5e1ea-102">Use Native Format to Import or Export Data (SQL Server)</span></span>
  <span data-ttu-id="5e1ea-103">ネイティブ形式は、拡張文字や 2 バイト文字セット (DBCS) の文字を含まないデータ ファイルを使用して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の複数のインスタンス間でデータを一括転送する場合に推奨します。</span><span class="sxs-lookup"><span data-stu-id="5e1ea-103">Native format is recommended when you bulk transfer data between multiple instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using a data file that does not contain any extended/double-byte character set (DBCS) characters.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5e1ea-104">拡張文字や DBCS 文字を含んだデータ ファイルを使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の複数のインスタンス間でデータを一括転送するには、Unicode ネイティブ形式を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5e1ea-104">To bulk transfer data between multiple instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using a data file that contains extended or DBCS characters, you should use the Unicode native format.</span></span> <span data-ttu-id="5e1ea-105">詳細については、「 [Unicode ネイティブ形式を使用したデータのインポートまたはエクスポート &#40;SQL Server&#41;](use-unicode-native-format-to-import-or-export-data-sql-server.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="5e1ea-105">For more information, see [Use Unicode Native Format to Import or Export Data &#40;SQL Server&#41;](use-unicode-native-format-to-import-or-export-data-sql-server.md).</span></span>  
  
 <span data-ttu-id="5e1ea-106">ネイティブ形式ではデータベースのネイティブ データ型が維持されます。</span><span class="sxs-lookup"><span data-stu-id="5e1ea-106">Native format maintains the native data types of a database.</span></span> <span data-ttu-id="5e1ea-107">ネイティブ形式は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブル間でデータを高速に転送できるようにデザインされています。</span><span class="sxs-lookup"><span data-stu-id="5e1ea-107">Native format is intended for high-speed data transfer of data between [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tables.</span></span> <span data-ttu-id="5e1ea-108">フォーマット ファイルを使用する場合は、転送元と転送先のテーブルは同じである必要はありません。</span><span class="sxs-lookup"><span data-stu-id="5e1ea-108">If you use a format file, the source and target tables do not need to be identical.</span></span> <span data-ttu-id="5e1ea-109">データ転送は、次の 2 つの手順で行われます。</span><span class="sxs-lookup"><span data-stu-id="5e1ea-109">The data transfer involves two steps:</span></span>  
  
1.  <span data-ttu-id="5e1ea-110">転送元テーブルからデータ ファイルへのデータの一括エクスポート</span><span class="sxs-lookup"><span data-stu-id="5e1ea-110">Bulk exporting the data from a source table into a data file</span></span>  
  
2.  <span data-ttu-id="5e1ea-111">データ ファイルから転送先テーブルへのデータの一括インポート</span><span class="sxs-lookup"><span data-stu-id="5e1ea-111">Bulk importing the data from the data file into the target table</span></span>  
  
 <span data-ttu-id="5e1ea-112">同一のテーブル間でネイティブ形式を使用すると、文字形式との間でデータ型の不必要な変換を防ぐことができ、時間と領域を節約できます。</span><span class="sxs-lookup"><span data-stu-id="5e1ea-112">The use of native format between identical tables avoids unnecessary conversion of data types to and from character format, saving time and space.</span></span> <span data-ttu-id="5e1ea-113">ただし、最適な転送速度を実現するために、データの形式設定に関するチェックはほとんど行われません。</span><span class="sxs-lookup"><span data-stu-id="5e1ea-113">To achieve the optimum transfer rate, however, few checks are performed regarding data formatting.</span></span> <span data-ttu-id="5e1ea-114">読み込まれたデータに関する問題を回避するには、次の制限事項の一覧を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5e1ea-114">To prevent problems with the loaded data, see the following restrictions list.</span></span>  
  
## <a name="restrictions"></a><span data-ttu-id="5e1ea-115">制限</span><span class="sxs-lookup"><span data-stu-id="5e1ea-115">Restrictions</span></span>  
 <span data-ttu-id="5e1ea-116">データをネイティブ形式で正常にインポートするには、次の条件を満たすようにします。</span><span class="sxs-lookup"><span data-stu-id="5e1ea-116">To import data in native format successfully, ensure that:</span></span>  
  
-   <span data-ttu-id="5e1ea-117">データ ファイルがネイティブ形式です。</span><span class="sxs-lookup"><span data-stu-id="5e1ea-117">The data file is in native format.</span></span>  
  
-   <span data-ttu-id="5e1ea-118">インポート先のテーブルは、(正しい列数、データ型、長さ、NULL 状態などが含まれた) データ ファイルと互換性を持つ必要があります。または、フォーマット ファイルを使用して、各フィールドを対応する各列にマップする必要があります。</span><span class="sxs-lookup"><span data-stu-id="5e1ea-118">Either the target table must be compatible with the data file (having the correct number of columns, data type, length, NULL status, and so forth), or you must use a format file to map each field to its corresponding columns.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="5e1ea-119">インポート先のテーブルと一致しないファイルからデータをインポートすると、インポート操作が成功する場合もありますが、多くの場合、インポート先のテーブルに挿入されるデータ値が不適切な値になります。</span><span class="sxs-lookup"><span data-stu-id="5e1ea-119">If you import data from a file that is mismatched with the target table, the import operation might succeed but the data values inserted into the target table are likely to be incorrect.</span></span> <span data-ttu-id="5e1ea-120">これは、インポート元のファイルのデータが、インポート先のテーブルの形式を使用して解釈されるためです。</span><span class="sxs-lookup"><span data-stu-id="5e1ea-120">This is because the data from the file is interpreted by using the format of the target table.</span></span> <span data-ttu-id="5e1ea-121">そのため、インポート先のテーブルと一致しない場合には、不適切な値が挿入されることになります。</span><span class="sxs-lookup"><span data-stu-id="5e1ea-121">Therefore, any mismatch results in the insertion of incorrect values.</span></span> <span data-ttu-id="5e1ea-122">ただし、このような不一致が原因で、データベース内で論理的または物理的に不一致が発生することはありません。</span><span class="sxs-lookup"><span data-stu-id="5e1ea-122">However, under no circumstances can such a mismatch cause logical or physical inconsistencies in the database.</span></span>  
  
     <span data-ttu-id="5e1ea-123">フォーマット ファイルの使用方法については、「[データのインポートまたはエクスポート用のフォーマット ファイル &#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5e1ea-123">For information on using format files, see [Format Files for Importing or Exporting Data &#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md).</span></span>  
  
 <span data-ttu-id="5e1ea-124">インポートが正常な場合、インポート先のテーブルは破損しません。</span><span class="sxs-lookup"><span data-stu-id="5e1ea-124">A successful import will not corrupt the target table.</span></span>  
  
## <a name="how-bcp-handles-data-in-native-format"></a><span data-ttu-id="5e1ea-125">bcp によるネイティブ形式でのデータ処理のしくみ</span><span class="sxs-lookup"><span data-stu-id="5e1ea-125">How bcp Handles Data in Native Format</span></span>  
 <span data-ttu-id="5e1ea-126">ここでは、 **bcp** ユーティリティによるネイティブ形式でのデータのエクスポートとインポートのしくみについて、特別な考慮事項を説明します。</span><span class="sxs-lookup"><span data-stu-id="5e1ea-126">This section discusses special considerations for how the **bcp** utility exports and imports data in native format.</span></span>  
  
-   <span data-ttu-id="5e1ea-127">非文字データ</span><span class="sxs-lookup"><span data-stu-id="5e1ea-127">Noncharacter data</span></span>  
  
     <span data-ttu-id="5e1ea-128">bcp ユーティリティでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 内部バイナリ データ形式を使用して、非文字データをテーブルからデータ ファイルに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="5e1ea-128">The bcp utility uses the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] internal binary data format to write noncharacter data from a table to a data file.</span></span>  
  
-   <span data-ttu-id="5e1ea-129">`char` データまたは `varchar` データ</span><span class="sxs-lookup"><span data-stu-id="5e1ea-129">`char` or `varchar` data</span></span>  
  
     <span data-ttu-id="5e1ea-130">`char`またはフィールドの先頭に `varchar` 、 **bcp**によってプレフィックス長が追加されます。</span><span class="sxs-lookup"><span data-stu-id="5e1ea-130">At the beginning of each `char` or `varchar` field, **bcp** adds the prefix length.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="5e1ea-131">ネイティブモードを使用すると、 **bcp**ユーティリティは、既定では文字を [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データファイルにコピーする前に、文字を OEM 文字に変換します。</span><span class="sxs-lookup"><span data-stu-id="5e1ea-131">When native mode is used, by default, the **bcp** utility converts characters from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to OEM characters before it copies them to a data file.</span></span> <span data-ttu-id="5e1ea-132">**Bcp**ユーティリティは、データファイルの文字をテーブルに一括インポートする前に、その文字を ANSI 文字に変換し [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="5e1ea-132">The **bcp** utility converts characters from a data file to ANSI characters before it bulk imports them into a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span> <span data-ttu-id="5e1ea-133">このような変換が行われている間、拡張文字のデータが失われる場合があります。</span><span class="sxs-lookup"><span data-stu-id="5e1ea-133">During these conversions, extended character data can be lost.</span></span> <span data-ttu-id="5e1ea-134">拡張文字については、Unicode ネイティブ形式を使用するか、コード ページを指定します。</span><span class="sxs-lookup"><span data-stu-id="5e1ea-134">For extended characters, either use Unicode native format or specify a code page.</span></span>  
  
-   <span data-ttu-id="5e1ea-135">`sql_variant` データ</span><span class="sxs-lookup"><span data-stu-id="5e1ea-135">`sql_variant` data</span></span>  
  
     <span data-ttu-id="5e1ea-136">`sql_variant` データが SQLVARIANT としてネイティブ形式のデータ ファイルに格納されている場合、そのデータのすべての特性が保持されます。</span><span class="sxs-lookup"><span data-stu-id="5e1ea-136">If `sql_variant` data is stored as a SQLVARIANT in a native-format data file, the data maintains all of its characteristics.</span></span> <span data-ttu-id="5e1ea-137">各データ値のデータ型を記録するメタデータが、そのデータ値と一緒に格納されます。</span><span class="sxs-lookup"><span data-stu-id="5e1ea-137">The metadata that records the data type of each data value is stored along with the data value.</span></span> <span data-ttu-id="5e1ea-138">このメタデータを使用して、インポート先の `sql_variant` 列に同じデータ型でデータ値を再作成します。</span><span class="sxs-lookup"><span data-stu-id="5e1ea-138">This metadata is used to re-create the data value with the same data type in a destination `sql_variant` column.</span></span>  
  
     <span data-ttu-id="5e1ea-139">インポート先の列のデータ型が `sql_variant` でない場合、各データ値は、暗黙的なデータ変換の通常の規則に従ってインポート先の列のデータ型に変換されます。</span><span class="sxs-lookup"><span data-stu-id="5e1ea-139">If the data type of the destination column is not `sql_variant`, each data value is converted to the data type of the destination column, following the normal rules of implicit data conversion.</span></span> <span data-ttu-id="5e1ea-140">データ変換中にエラーが発生すると、現在のバッチがロールバックされます。</span><span class="sxs-lookup"><span data-stu-id="5e1ea-140">If an error occurs during data conversion, the current batch is rolled back.</span></span> <span data-ttu-id="5e1ea-141">`char` 列間で転送される `varchar` 値と `sql_variant` 値で、コード ページの変換問題が生じている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="5e1ea-141">Any `char` and `varchar` values that are transferred between `sql_variant` columns may have code page conversion issues.</span></span>  
  
     <span data-ttu-id="5e1ea-142">詳細については、「[データ型の変換 &#40;データベース エンジン&#41;](/sql/t-sql/data-types/data-type-conversion-database-engine)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5e1ea-142">For more information about data conversion, see [Data Type Conversion &#40;Database Engine&#41;](/sql/t-sql/data-types/data-type-conversion-database-engine).</span></span>  
  
## <a name="command-options-for-native-format"></a><span data-ttu-id="5e1ea-143">ネイティブ形式用のコマンド オプション</span><span class="sxs-lookup"><span data-stu-id="5e1ea-143">Command Options for Native Format</span></span>  
 <span data-ttu-id="5e1ea-144">ネイティブ形式のデータをテーブルにインポートするには、 **bcp**、BULK INSERT または INSERT...SELECT \* FROM OPENROWSET (BULK...) を選択します。**Bcp**コマンドまたは BULK INSERT ステートメントの場合は、コマンドラインでデータ形式を指定できます。</span><span class="sxs-lookup"><span data-stu-id="5e1ea-144">You can import native format data into a table using **bcp**, BULK INSERT or INSERT ... SELECT \* FROM OPENROWSET(BULK...). For a **bcp** command or BULK INSERT statement, you can specify the data format on the command line.</span></span> <span data-ttu-id="5e1ea-145">INSERT ...SELECT \* FROM OPENROWSET(BULK...) ステートメントの場合は、フォーマット ファイルでデータ形式を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5e1ea-145">For an INSERT ... SELECT \* FROM OPENROWSET(BULK...) statement, you must specify the data format in a format file.</span></span>  
  
 <span data-ttu-id="5e1ea-146">ネイティブ形式は、次のコマンド ライン オプションでサポートされています。</span><span class="sxs-lookup"><span data-stu-id="5e1ea-146">Native format is supported by the following command line options:</span></span>  
  
|<span data-ttu-id="5e1ea-147">command</span><span class="sxs-lookup"><span data-stu-id="5e1ea-147">Command</span></span>|<span data-ttu-id="5e1ea-148">オプション</span><span class="sxs-lookup"><span data-stu-id="5e1ea-148">Option</span></span>|<span data-ttu-id="5e1ea-149">[説明]</span><span class="sxs-lookup"><span data-stu-id="5e1ea-149">Description</span></span>|  
|-------------|------------|-----------------|  
|<span data-ttu-id="5e1ea-150">**bcp**</span><span class="sxs-lookup"><span data-stu-id="5e1ea-150">**bcp**</span></span>|<span data-ttu-id="5e1ea-151">**-n**</span><span class="sxs-lookup"><span data-stu-id="5e1ea-151">**-n**</span></span>|<span data-ttu-id="5e1ea-152">**Bcp**ユーティリティによって、データのネイティブデータ型が使用されます。<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="5e1ea-152">Causes the **bcp** utility to use the native data types of the data.<sup>1</sup></span></span>|  
|<span data-ttu-id="5e1ea-153">BULK INSERT</span><span class="sxs-lookup"><span data-stu-id="5e1ea-153">BULK INSERT</span></span>|<span data-ttu-id="5e1ea-154">DATAFILETYPE **= '** native **'**</span><span class="sxs-lookup"><span data-stu-id="5e1ea-154">DATAFILETYPE **='** native **'**</span></span>|<span data-ttu-id="5e1ea-155">ネイティブ データ型またはワイド ネイティブ データ型のデータが使用されます。</span><span class="sxs-lookup"><span data-stu-id="5e1ea-155">Uses the native or wide native data types of the data.</span></span> <span data-ttu-id="5e1ea-156">フォーマット ファイルでデータ型を指定している場合、DATAFILETYPE は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="5e1ea-156">Note that DATAFILETYPE is not needed if a format file specifies the data types.</span></span>|  
  
 <span data-ttu-id="5e1ea-157"><sup>1</sup>ネイティブ (**-n**) データを以前のバージョンのクライアントと互換性のある形式に読み込むに [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、 **-V**スイッチを使用します。</span><span class="sxs-lookup"><span data-stu-id="5e1ea-157"><sup>1</sup> To load native (**-n**) data to a format compatible with earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] clients, use the **-V** switch.</span></span> <span data-ttu-id="5e1ea-158">詳細については、「 [以前のバージョンの SQL Server からのネイティブ形式データおよび文字形式データのインポート](import-native-and-character-format-data-from-earlier-versions-of-sql-server.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="5e1ea-158">For more information, see [Import Native and Character Format Data from Earlier Versions of SQL Server](import-native-and-character-format-data-from-earlier-versions-of-sql-server.md).</span></span>  
  
 <span data-ttu-id="5e1ea-159">詳細については、「[bcp ユーティリティ](../../tools/bcp-utility.md)」、「[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql)」、または「[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5e1ea-159">For more information, see [bcp Utility](../../tools/bcp-utility.md), [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql), or [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5e1ea-160">また、フォーマット ファイルでフィールドごとに形式を指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="5e1ea-160">Alternatively, you can specify formatting on a per-field basis in a format file.</span></span> <span data-ttu-id="5e1ea-161">詳細については、「 [データのインポートまたはエクスポート用のフォーマット ファイル &#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5e1ea-161">For more information, see [Format Files for Importing or Exporting Data &#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="5e1ea-162">例</span><span class="sxs-lookup"><span data-stu-id="5e1ea-162">Examples</span></span>  
 <span data-ttu-id="5e1ea-163">次の例では、**bcp** を使用してネイティブ データを一括エクスポートする方法と、BULK INSERT を使用して同じデータを一括インポートする方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="5e1ea-163">The following examples demonstrate how to bulk export native data using **bcp** and bulk import the same data using BULK INSERT.</span></span>  
  
### <a name="sample-table"></a><span data-ttu-id="5e1ea-164">サンプル テーブル</span><span class="sxs-lookup"><span data-stu-id="5e1ea-164">Sample Table</span></span>  
 <span data-ttu-id="5e1ea-165">次の例を実行するには、**dbo** スキーマに基づいて、**myTestNativeData** という名前のテーブルを **AdventureWorks** サンプル データベース内に作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5e1ea-165">The examples require that a table named **myTestNativeData** table be created in the **AdventureWorks** sample database under the **dbo** schema.</span></span> <span data-ttu-id="5e1ea-166">このテーブルを作成しないと、例を実行できません。</span><span class="sxs-lookup"><span data-stu-id="5e1ea-166">Before you can run the examples, you must create this table.</span></span> <span data-ttu-id="5e1ea-167">[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] クエリ エディターで、次のコードを実行します。</span><span class="sxs-lookup"><span data-stu-id="5e1ea-167">In [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] Query Editor, execute:</span></span>  
  
```  
USE AdventureWorks;  
GO  
CREATE TABLE myTestNativeData (  
   Col1 smallint,  
   Col2 nvarchar(50),  
   Col3 nvarchar(50)  
   );   
```  
  
 <span data-ttu-id="5e1ea-168">このテーブルを作成し、上記のコードにより生成された内容を表示するには、次のステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="5e1ea-168">To populate this table and view the resulting contents execute the following statements:</span></span>  
  
```  
INSERT INTO myTestNativeData(Col1,Col2,Col3)  
   VALUES(1,'DataField2','DataField3');  
INSERT INTO myTestNativeData(Col1,Col2,Col3)  
   VALUES(2,'DataField2','DataField3');  
GO  
SELECT Col1,Col2,Col3 FROM myTestNativeData  
  
```  
  
### <a name="using-bcp-to-bulk-export-native-data"></a><span data-ttu-id="5e1ea-169">bcp を使用したネイティブ データの一括エクスポート</span><span class="sxs-lookup"><span data-stu-id="5e1ea-169">Using bcp to Bulk Export Native Data</span></span>  
 <span data-ttu-id="5e1ea-170">テーブルからデータ ファイルにデータをエクスポートするには、 **bcp** で **out** オプションと次の修飾子を組み合わせて使用します。</span><span class="sxs-lookup"><span data-stu-id="5e1ea-170">To export data from the table to the data file, use **bcp** with the **out** option and the following qualifiers:</span></span>  
  
|<span data-ttu-id="5e1ea-171">修飾子</span><span class="sxs-lookup"><span data-stu-id="5e1ea-171">Qualifiers</span></span>|<span data-ttu-id="5e1ea-172">説明</span><span class="sxs-lookup"><span data-stu-id="5e1ea-172">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="5e1ea-173">**-n**</span><span class="sxs-lookup"><span data-stu-id="5e1ea-173">**-n**</span></span>|<span data-ttu-id="5e1ea-174">ネイティブ データ型を指定します。</span><span class="sxs-lookup"><span data-stu-id="5e1ea-174">Specifies native data types.</span></span>|  
|<span data-ttu-id="5e1ea-175">**-T**</span><span class="sxs-lookup"><span data-stu-id="5e1ea-175">**-T**</span></span>|<span data-ttu-id="5e1ea-176">**bcp** ユーティリティが統合セキュリティを使用した信頼関係接続を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続することを指定します。</span><span class="sxs-lookup"><span data-stu-id="5e1ea-176">Specifies that the **bcp** utility connects to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] with a trusted connection using integrated security.</span></span> <span data-ttu-id="5e1ea-177">**-T** を指定しない場合、正常にログインするには **-U** と **-P** を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5e1ea-177">If **-T** is not specified, you need to specify **-U** and **-P** to successfully log in.</span></span>|  
  
 <span data-ttu-id="5e1ea-178">次の例では、ネイティブ形式のデータを `myTestNativeData` テーブルから `myTestNativeData-n.Dat` という名前の新しいデータ ファイルに一括エクスポートします。</span><span class="sxs-lookup"><span data-stu-id="5e1ea-178">The following example bulk exports data in native format from the `myTestNativeData` table into a new data file named `myTestNativeData-n.Dat` data file.</span></span> <span data-ttu-id="5e1ea-179">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows コマンド プロンプトで、次のように入力します。</span><span class="sxs-lookup"><span data-stu-id="5e1ea-179">At the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows command prompt, enter:</span></span>  
  
```  
bcp AdventureWorks..myTestNativeData out C:\myTestNativeData-n.Dat -n -T  
  
```  
  
### <a name="using-bulk-insert-to-bulk-import-native-data"></a><span data-ttu-id="5e1ea-180">BULK INSERT を使用したネイティブ データの一括インポート</span><span class="sxs-lookup"><span data-stu-id="5e1ea-180">Using BULK INSERT to Bulk Import Native Data</span></span>  
 <span data-ttu-id="5e1ea-181">次の例では、BULK INSERT を使用して、`myTestNativeData-n.Dat` データ ファイルのデータを `myTestNativeData` テーブルにインポートします。</span><span class="sxs-lookup"><span data-stu-id="5e1ea-181">The following example uses BULK INSERT to import the data in the `myTestNativeData-n.Dat` data file into the `myTestNativeData` table.</span></span> <span data-ttu-id="5e1ea-182">[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] クエリ エディターで、次のコードを実行します。</span><span class="sxs-lookup"><span data-stu-id="5e1ea-182">In [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] Query Editor, execute:</span></span>  
  
```  
USE AdventureWorks;  
GO  
BULK INSERT myTestNativeData   
    FROM 'C:\myTestNativeData-n.Dat'   
   WITH (DATAFILETYPE='native');   
GO  
SELECT Col1,Col2,Col3 FROM myTestNativeData  
GO  
  
```  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="5e1ea-183">関連タスク</span><span class="sxs-lookup"><span data-stu-id="5e1ea-183">Related Tasks</span></span>  
 <span data-ttu-id="5e1ea-184">**一括インポートまたは一括エクスポートのデータ形式を使用するには**</span><span class="sxs-lookup"><span data-stu-id="5e1ea-184">**To use data formats for bulk import or bulk export**</span></span>  
  
-   [<span data-ttu-id="5e1ea-185">以前のバージョンの SQL Server からのネイティブ形式データおよび文字形式データのインポート</span><span class="sxs-lookup"><span data-stu-id="5e1ea-185">Import Native and Character Format Data from Earlier Versions of SQL Server</span></span>](import-native-and-character-format-data-from-earlier-versions-of-sql-server.md)  
  
-   [<span data-ttu-id="5e1ea-186">文字形式を使用したデータのインポートまたはエクスポート &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="5e1ea-186">Use Character Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="5e1ea-187">Unicode 文字形式を使用したデータのインポートまたはエクスポート &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="5e1ea-187">Use Unicode Character Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-unicode-character-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="5e1ea-188">Unicode ネイティブ形式を使用したデータのインポートまたはエクスポート &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="5e1ea-188">Use Unicode Native Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-unicode-native-format-to-import-or-export-data-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="5e1ea-189">参照</span><span class="sxs-lookup"><span data-stu-id="5e1ea-189">See Also</span></span>  
 <span data-ttu-id="5e1ea-190">[bcp ユーティリティ](../../tools/bcp-utility.md) </span><span class="sxs-lookup"><span data-stu-id="5e1ea-190">[bcp Utility](../../tools/bcp-utility.md) </span></span>  
 <span data-ttu-id="5e1ea-191">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="5e1ea-191">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span></span>  
 <span data-ttu-id="5e1ea-192">[データ型 &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="5e1ea-192">[Data Types &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql) </span></span>  
 <span data-ttu-id="5e1ea-193">[sql_variant &#40;Transact-SQL&#41;](/sql/t-sql/data-types/sql-variant-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="5e1ea-193">[sql_variant &#40;Transact-SQL&#41;](/sql/t-sql/data-types/sql-variant-transact-sql) </span></span>  
 <span data-ttu-id="5e1ea-194">[以前のバージョンの SQL Server からのネイティブ形式データおよび文字形式データのインポート](import-native-and-character-format-data-from-earlier-versions-of-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="5e1ea-194">[Import Native and Character Format Data from Earlier Versions of SQL Server](import-native-and-character-format-data-from-earlier-versions-of-sql-server.md) </span></span>  
 <span data-ttu-id="5e1ea-195">[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="5e1ea-195">[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span></span>  
 [<span data-ttu-id="5e1ea-196">Unicode ネイティブ形式を使用したデータのインポートまたはエクスポート &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="5e1ea-196">Use Unicode Native Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-unicode-native-format-to-import-or-export-data-sql-server.md)  
  
  
