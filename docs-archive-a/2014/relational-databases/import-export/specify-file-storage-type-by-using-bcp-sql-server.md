---
title: bcp を使用したファイル ストレージ型の指定 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- bcp utility [SQL Server], file storage types
- importing data, file storage types
- native data format [SQL Server]
- file storage types [SQL Server]
- data formats [SQL Server], file storage types
ms.assetid: 85e12df8-1be7-4bdc-aea9-05aade085c06
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c1f3ad2a94ffe3e0f1db19a8e66f85497e7143dc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632469"
---
# <a name="specify-file-storage-type-by-using-bcp-sql-server"></a><span data-ttu-id="3f471-102">bcp を使用したファイル ストレージ型の指定 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="3f471-102">Specify File Storage Type by Using bcp (SQL Server)</span></span>
  <span data-ttu-id="3f471-103">*ファイル ストレージ型* は、データ ファイルへのデータの格納方法を記述します。</span><span class="sxs-lookup"><span data-stu-id="3f471-103">The *file storage type* describes how data is stored in the data file.</span></span> <span data-ttu-id="3f471-104">データ ファイルには、データベース テーブルの型 (ネイティブ形式)、文字表現 (文字形式)、または暗黙的な型変換がサポートされているデータ型のいずれかでデータをエクスポートできます。暗黙的な型変換では、たとえば、`smallint` は `int` としてコピーされます。</span><span class="sxs-lookup"><span data-stu-id="3f471-104">Data can be exported to a data file as its database table type (native format), in its character representation (character format), or as any data type where implicit conversion is supported; for example, copying a `smallint` as an `int`.</span></span> <span data-ttu-id="3f471-105">ユーザー定義のデータ型は、基本データ型としてエクスポートされます。</span><span class="sxs-lookup"><span data-stu-id="3f471-105">User-defined data types are exported as their base types.</span></span>  
  
## <a name="the-bcp-prompt-for-file-storage-type"></a><span data-ttu-id="3f471-106">ファイル ストレージ型の bcp プロンプト</span><span class="sxs-lookup"><span data-stu-id="3f471-106">The bcp Prompt for File Storage Type</span></span>  
 <span data-ttu-id="3f471-107">対話型の **bcp** コマンドで、フォーマット ファイル スイッチ ( **-f** ) またはデータ形式スイッチ ( **-n** 、 **-c**、 **-w**、または **-N**) のどちらも付けずに **in**または **out**オプションを指定すると、次のように各データ フィールドのファイル ストレージ型を要求するプロンプトが表示されます。</span><span class="sxs-lookup"><span data-stu-id="3f471-107">If an interactive **bcp** command contains the **in** or **out** option without either the format file switch (**-f**) or a data-format switch (**-n**, **-c**, **-w**, or **-N**), the command prompts for the file storage type of each data field, as follows:</span></span>  
  
 `Enter the file storage type of field <field_name> [<default>]:`  
  
 <span data-ttu-id="3f471-108">この要求への応答は、次のように、実行するタスクによって異なります。</span><span class="sxs-lookup"><span data-stu-id="3f471-108">Your response to this prompt depends on the task you perform, as follows:</span></span>  
  
-   <span data-ttu-id="3f471-109">できるだけコンパクトなストレージ型 (ネイティブ データ形式) で [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスからデータ ファイルにデータを一括エクスポートするには、**bcp** によって提供される既定のファイル ストレージ型をそのまま使用します。</span><span class="sxs-lookup"><span data-stu-id="3f471-109">To bulk export data from an instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to a data file in the most compact storage possible (native data format), accept the default file storage types that are provided by **bcp**.</span></span> <span data-ttu-id="3f471-110">ネイティブのファイル ストレージ型の一覧については、このトピックの「ネイティブのファイル ストレージ型」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3f471-110">For a list of the native file storage types, see "Native File Storage Types," later in this topic.</span></span>  
  
-   <span data-ttu-id="3f471-111">文字形式で [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスからデータ ファイルにデータを一括エクスポートするには、テーブルのすべての列にファイル ストレージ型として `char` を指定します。</span><span class="sxs-lookup"><span data-stu-id="3f471-111">To bulk export data from an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to a data file in character format, specify `char` as the file storage type for all columns in the table.</span></span>  
  
-   <span data-ttu-id="3f471-112">データ ファイルから [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスにデータを一括インポートするには、文字形式で格納されたデータの場合はファイル ストレージ型として `char` を指定し、ネイティブ データ型形式で格納されたデータの場合は、必要に応じて次のファイル ストレージ型のいずれかを指定します。</span><span class="sxs-lookup"><span data-stu-id="3f471-112">To bulk import data to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from a data file, specify the file storage type as `char` for types stored in character format and, for data stored in native data type format, specify one of the file storage types, as appropriate:</span></span>  
  
    |<span data-ttu-id="3f471-113">ファイル ストレージ型</span><span class="sxs-lookup"><span data-stu-id="3f471-113">File storage type</span></span>|<span data-ttu-id="3f471-114">コマンド プロンプトで入力する文字</span><span class="sxs-lookup"><span data-stu-id="3f471-114">Enter at command prompt</span></span>|  
    |-----------------------|-----------------------------|  
    |<span data-ttu-id="3f471-115">`char` <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="3f471-115">`char` <sup>1</sup></span></span>|<span data-ttu-id="3f471-116">`c`[`har`]</span><span class="sxs-lookup"><span data-stu-id="3f471-116">`c`[`har`]</span></span>|  
    |`varchar`|`c[har]`|  
    |`nchar`|`w`|  
    |`nvarchar`|`w`|  
    |<span data-ttu-id="3f471-117">`text` <sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="3f471-117">`text` <sup>2</sup></span></span>|<span data-ttu-id="3f471-118">`T`[`ext`]</span><span class="sxs-lookup"><span data-stu-id="3f471-118">`T`[`ext`]</span></span>|  
    |`ntext2`|`W`|  
    |`binary`|`x`|  
    |`varbinary`|`x`|  
    |<span data-ttu-id="3f471-119">`image` <sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="3f471-119">`image` <sup>2</sup></span></span>|<span data-ttu-id="3f471-120">`I`[`mage`]</span><span class="sxs-lookup"><span data-stu-id="3f471-120">`I`[`mage`]</span></span>|  
    |`datetime`|<span data-ttu-id="3f471-121">**d[ate]**</span><span class="sxs-lookup"><span data-stu-id="3f471-121">**d[ate]**</span></span>|  
    |`smalldatetime`|`D`|  
    |`time`|`te`|  
    |`date`|`de`|  
    |`datetime2`|`d2`|  
    |`datetimeoffset`|`do`|  
    |`decimal`|`n`|  
    |`numeric`|`n`|  
    |`float`|<span data-ttu-id="3f471-122">**f[loat]**</span><span class="sxs-lookup"><span data-stu-id="3f471-122">**f[loat]**</span></span>|  
    |`real`|`r`|  
    |`Int`|<span data-ttu-id="3f471-123">**i[nt]**</span><span class="sxs-lookup"><span data-stu-id="3f471-123">**i[nt]**</span></span>|  
    |`bigint`|`B[igint]`|  
    |`smallint`|<span data-ttu-id="3f471-124">**s[mallint]**</span><span class="sxs-lookup"><span data-stu-id="3f471-124">**s[mallint]**</span></span>|  
    |`tinyint`|<span data-ttu-id="3f471-125">**t[inyint]**</span><span class="sxs-lookup"><span data-stu-id="3f471-125">**t[inyint]**</span></span>|  
    |`money`|<span data-ttu-id="3f471-126">**m[oney]**</span><span class="sxs-lookup"><span data-stu-id="3f471-126">**m[oney]**</span></span>|  
    |`smallmoney`|`M`|  
    |`bit`|`b[it]`|  
    |`uniqueidentifier`|`u`|  
    |`sql_variant`|`V[ariant]`|  
    |`timestamp`|`x`|  
    |<span data-ttu-id="3f471-127">`UDT` (ユーザー定義データ型)</span><span class="sxs-lookup"><span data-stu-id="3f471-127">`UDT` (a user-defined data type)</span></span>|`U`|  
    |`XML`|`X`|  
  
     <span data-ttu-id="3f471-128"><sup>1</sup>フィールド長、プレフィックス長、およびターミネータの相互作用によって、ファイルストレージ型としてエクスポートされた非文字データのデータファイルに割り当てられる記憶域の容量が決まり `char` ます。</span><span class="sxs-lookup"><span data-stu-id="3f471-128"><sup>1</sup> The interaction of field length, prefix length, and terminators determines the amount of storage space that is allocated in a data file for noncharacter data that is exported as the `char` file storage type.</span></span>  
  
     <span data-ttu-id="3f471-129"><sup>2</sup> `ntext` 、 `text` 、および `image` の各データ型は、の将来のバージョンで削除される予定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] です。</span><span class="sxs-lookup"><span data-stu-id="3f471-129"><sup>2</sup> The `ntext`, `text`, and `image` data types will be removed in a future version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="3f471-130">新しい開発作業ではこれらのデータ型の使用を避け、現在このデータ型を使用しているアプリケーションは変更を検討してください。</span><span class="sxs-lookup"><span data-stu-id="3f471-130">In new development work, avoid using these data types, and plan to modify applications that currently use them.</span></span> <span data-ttu-id="3f471-131">代わりに `nvarchar(max)`、`varchar(max)`、および `varbinary(max)` 型を使用してください。</span><span class="sxs-lookup"><span data-stu-id="3f471-131">Use `nvarchar(max)`, `varchar(max)`, and `varbinary(max)` instead.</span></span>  
  
## <a name="native-file-storage-types"></a><span data-ttu-id="3f471-132">ネイティブのファイル ストレージ型</span><span class="sxs-lookup"><span data-stu-id="3f471-132">Native File Storage Types</span></span>  
 <span data-ttu-id="3f471-133">各ネイティブのファイル ストレージ型は、対応するホスト ファイル データ型として、フォーマット ファイルに記録されます。</span><span class="sxs-lookup"><span data-stu-id="3f471-133">Each native file storage type is recorded in the format file as a corresponding host file data type.</span></span>  
  
|<span data-ttu-id="3f471-134">ファイル ストレージ型</span><span class="sxs-lookup"><span data-stu-id="3f471-134">File storage type</span></span>|<span data-ttu-id="3f471-135">ホスト ファイル データ型</span><span class="sxs-lookup"><span data-stu-id="3f471-135">Host file data type</span></span>|  
|-----------------------|-------------------------|  
|<span data-ttu-id="3f471-136">`char` <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="3f471-136">`char` <sup>1</sup></span></span>|<span data-ttu-id="3f471-137">SQLCHAR</span><span class="sxs-lookup"><span data-stu-id="3f471-137">SQLCHAR</span></span>|  
|`varchar`|<span data-ttu-id="3f471-138">SQLCHAR</span><span class="sxs-lookup"><span data-stu-id="3f471-138">SQLCHAR</span></span>|  
|`nchar`|<span data-ttu-id="3f471-139">SQLNCHAR</span><span class="sxs-lookup"><span data-stu-id="3f471-139">SQLNCHAR</span></span>|  
|`nvarchar`|<span data-ttu-id="3f471-140">SQLNCHAR</span><span class="sxs-lookup"><span data-stu-id="3f471-140">SQLNCHAR</span></span>|  
|<span data-ttu-id="3f471-141">`text` <sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="3f471-141">`text` <sup>2</sup></span></span>|<span data-ttu-id="3f471-142">SQLCHAR</span><span class="sxs-lookup"><span data-stu-id="3f471-142">SQLCHAR</span></span>|  
|<span data-ttu-id="3f471-143">`ntext` <sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="3f471-143">`ntext` <sup>2</sup></span></span>|<span data-ttu-id="3f471-144">SQLNCHAR</span><span class="sxs-lookup"><span data-stu-id="3f471-144">SQLNCHAR</span></span>|  
|`binary`|<span data-ttu-id="3f471-145">SQLBINARY</span><span class="sxs-lookup"><span data-stu-id="3f471-145">SQLBINARY</span></span>|  
|`varbinary`|<span data-ttu-id="3f471-146">SQLBINARY</span><span class="sxs-lookup"><span data-stu-id="3f471-146">SQLBINARY</span></span>|  
|<span data-ttu-id="3f471-147">`image` <sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="3f471-147">`image` <sup>2</sup></span></span>|<span data-ttu-id="3f471-148">SQLBINARY</span><span class="sxs-lookup"><span data-stu-id="3f471-148">SQLBINARY</span></span>|  
|`datetime`|<span data-ttu-id="3f471-149">SQLDATETIME</span><span class="sxs-lookup"><span data-stu-id="3f471-149">SQLDATETIME</span></span>|  
|`smalldatetime`|<span data-ttu-id="3f471-150">SQLDATETIM4</span><span class="sxs-lookup"><span data-stu-id="3f471-150">SQLDATETIM4</span></span>|  
|`decimal`|<span data-ttu-id="3f471-151">SQLDECIMAL</span><span class="sxs-lookup"><span data-stu-id="3f471-151">SQLDECIMAL</span></span>|  
|`numeric`|<span data-ttu-id="3f471-152">SQLNUMERIC</span><span class="sxs-lookup"><span data-stu-id="3f471-152">SQLNUMERIC</span></span>|  
|`float`|<span data-ttu-id="3f471-153">SQLFLT8</span><span class="sxs-lookup"><span data-stu-id="3f471-153">SQLFLT8</span></span>|  
|`real`|<span data-ttu-id="3f471-154">SQLFLT4</span><span class="sxs-lookup"><span data-stu-id="3f471-154">SQLFLT4</span></span>|  
|`int`|<span data-ttu-id="3f471-155">SQLINT</span><span class="sxs-lookup"><span data-stu-id="3f471-155">SQLINT</span></span>|  
|`bigint`|<span data-ttu-id="3f471-156">SQLBIGINT</span><span class="sxs-lookup"><span data-stu-id="3f471-156">SQLBIGINT</span></span>|  
|`smallint`|<span data-ttu-id="3f471-157">SQLSMALLINT</span><span class="sxs-lookup"><span data-stu-id="3f471-157">SQLSMALLINT</span></span>|  
|`tinyint`|<span data-ttu-id="3f471-158">SQLTINYINT</span><span class="sxs-lookup"><span data-stu-id="3f471-158">SQLTINYINT</span></span>|  
|`money`|<span data-ttu-id="3f471-159">SQLMONEY</span><span class="sxs-lookup"><span data-stu-id="3f471-159">SQLMONEY</span></span>|  
|`smallmoney`|<span data-ttu-id="3f471-160">SQLMONEY4</span><span class="sxs-lookup"><span data-stu-id="3f471-160">SQLMONEY4</span></span>|  
|`bit`|<span data-ttu-id="3f471-161">SQLBIT</span><span class="sxs-lookup"><span data-stu-id="3f471-161">SQLBIT</span></span>|  
|`uniqueidentifier`|<span data-ttu-id="3f471-162">SQLUNIQUEID</span><span class="sxs-lookup"><span data-stu-id="3f471-162">SQLUNIQUEID</span></span>|  
|`sql_variant`|<span data-ttu-id="3f471-163">SQLVARIANT</span><span class="sxs-lookup"><span data-stu-id="3f471-163">SQLVARIANT</span></span>|  
|`timestamp`|<span data-ttu-id="3f471-164">SQLBINARY</span><span class="sxs-lookup"><span data-stu-id="3f471-164">SQLBINARY</span></span>|  
|<span data-ttu-id="3f471-165">UDT (ユーザー定義データ型)</span><span class="sxs-lookup"><span data-stu-id="3f471-165">UDT (a user-defined data type)</span></span>|<span data-ttu-id="3f471-166">SQLUDT</span><span class="sxs-lookup"><span data-stu-id="3f471-166">SQLUDT</span></span>|  
  
 <span data-ttu-id="3f471-167">1文字形式で格納された<sup>1 つ</sup>のデータファイルは `char` 、ファイルストレージ型として使用されます。</span><span class="sxs-lookup"><span data-stu-id="3f471-167"><sup>1</sup> Data files that are stored in character format use `char` as the file storage type.</span></span> <span data-ttu-id="3f471-168">したがって、文字データ ファイルの場合、フォーマット ファイルに表示されるデータ型は SQLCHAR のみです。</span><span class="sxs-lookup"><span data-stu-id="3f471-168">Therefore, for character data files, SQLCHAR is the only data type that appears in a format file.</span></span>  
  
 <span data-ttu-id="3f471-169"><sup>2</sup> `text` `ntext` `image` 既定値が設定されている、、およびの各列にデータを一括インポートすることはできません。</span><span class="sxs-lookup"><span data-stu-id="3f471-169"><sup>2</sup> You cannot bulk import data into `text`, `ntext`, and `image` columns that have DEFAULT values.</span></span>  
  
## <a name="additional-considerations-for-file-storage-types"></a><span data-ttu-id="3f471-170">ファイル ストレージ型のその他の考慮事項</span><span class="sxs-lookup"><span data-stu-id="3f471-170">Additional Considerations for File Storage Types</span></span>  
 <span data-ttu-id="3f471-171">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスからデータ ファイルにデータを一括エクスポートするときは、次のことを考慮してください。</span><span class="sxs-lookup"><span data-stu-id="3f471-171">When you bulk export data from an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to a data file:</span></span>  
  
-   <span data-ttu-id="3f471-172">`char` 型は、常にファイル ストレージ型として指定できます。</span><span class="sxs-lookup"><span data-stu-id="3f471-172">You can always specify `char` as the file storage type.</span></span>  
  
-   <span data-ttu-id="3f471-173">無効な暗黙的な変換を表すファイルストレージ型を入力すると、 **bcp**は失敗します。たとえば、データにを指定することはできますが、 `int` `smallint` データにを指定すると `smallint` `int` 、オーバーフローエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="3f471-173">If you enter a file storage type that represents an invalid implicit conversion, **bcp** fails; for example, though you can specify `int` for `smallint` data, if you specify `smallint` for `int` data, overflow errors result.</span></span>  
  
-   <span data-ttu-id="3f471-174">`float`、`money`、`datetime`、または `int` などの非文字データ型をそれぞれのデータベース型として格納すると、データが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のネイティブ形式でデータ ファイルに書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="3f471-174">When noncharacter data types such as `float`, `money`, `datetime`, or `int` are stored as their database types, the data is written to the data file in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native format.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="3f471-175">**bcp** コマンドですべてのフィールドを対話形式で指定すると、各フィールドへの応答を XML 形式以外のファイルに保存するように要求するプロンプトが表示されます。</span><span class="sxs-lookup"><span data-stu-id="3f471-175">After you interactively specify all of the fields in a **bcp** command, the command prompts you save your responses for each field in a non-XML format file.</span></span> <span data-ttu-id="3f471-176">XML 以外のフォーマット ファイルの詳細については、「[XML 以外のフォーマット ファイル &#40;SQL Server&#41;](xml-format-files-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3f471-176">For more information on non-XML format files, see [Non-XML Format Files &#40;SQL Server&#41;](xml-format-files-sql-server.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f471-177">参照</span><span class="sxs-lookup"><span data-stu-id="3f471-177">See Also</span></span>  
 <span data-ttu-id="3f471-178">[bcp ユーティリティ](../../tools/bcp-utility.md) </span><span class="sxs-lookup"><span data-stu-id="3f471-178">[bcp Utility](../../tools/bcp-utility.md) </span></span>  
 <span data-ttu-id="3f471-179">[データ型 &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3f471-179">[Data Types &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql) </span></span>  
 <span data-ttu-id="3f471-180">[bcp を使用したフィールド長の指定 &#40;SQL Server&#41;](specify-field-length-by-using-bcp-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="3f471-180">[Specify Field Length by Using bcp &#40;SQL Server&#41;](specify-field-length-by-using-bcp-sql-server.md) </span></span>  
 <span data-ttu-id="3f471-181">[フィールド ターミネータと行ターミネータの指定 &#40;SQL Server&#41;](specify-field-and-row-terminators-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="3f471-181">[Specify Field and Row Terminators &#40;SQL Server&#41;](specify-field-and-row-terminators-sql-server.md) </span></span>  
 [<span data-ttu-id="3f471-182">bcp を使用したデータ ファイルのプレフィックス長の指定 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3f471-182">Specify Prefix Length in Data Files by Using bcp &#40;SQL Server&#41;</span></span>](specify-prefix-length-in-data-files-by-using-bcp-sql-server.md)  
  
  
