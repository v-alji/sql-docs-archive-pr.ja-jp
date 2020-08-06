---
title: フィールド ターミネータと行ターミネータの指定 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- bcp utility [SQL Server], terminators
- field terminators [SQL Server]
- data formats [SQL Server], terminators
- row terminators [SQL Server]
- terminators [SQL Server]
ms.assetid: f68b6782-f386-4947-93c4-e89110800704
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 548beeae68f5585c5cf2ba56b67027532ab43b71
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741042"
---
# <a name="specify-field-and-row-terminators-sql-server"></a><span data-ttu-id="4bebc-102">フィールド ターミネータと行ターミネータの指定 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="4bebc-102">Specify Field and Row Terminators (SQL Server)</span></span>
  <span data-ttu-id="4bebc-103">文字列データ フィールドでは、省略可能なターミネータ文字を使用して、データ ファイルの各フィールドの末尾 ( *フィールド ターミネータ* を使用) と各行の末尾 ( *行ターミネータ*を使用) を示すことができます。</span><span class="sxs-lookup"><span data-stu-id="4bebc-103">For character data fields, optional terminating characters allow you to mark the end of each field in a data file with a *field terminator* and the end of each row with a *row terminator*.</span></span> <span data-ttu-id="4bebc-104">ターミネータ文字は、フィールドや行の終了位置と次のフィールドや行の開始位置を、データ ファイルを読み取るプログラムに示す方法の 1 つです。</span><span class="sxs-lookup"><span data-stu-id="4bebc-104">Terminating characters are one way to indicate to programs that read the data file where one field or row ends and another field or row begins.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="4bebc-105">ネイティブ形式または Unicode ネイティブ形式を使用するときは、フィールド ターミネータではなくプレフィックス長を使用します。</span><span class="sxs-lookup"><span data-stu-id="4bebc-105">When you use native or Unicode native format, use length prefixes rather than field terminators.</span></span> <span data-ttu-id="4bebc-106">ネイティブ形式のデータ ファイルは [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の内部バイナリ データ形式で格納されるので、ネイティブ形式のデータがターミネータと競合することがあります。</span><span class="sxs-lookup"><span data-stu-id="4bebc-106">Native format data can conflict with terminators because a native-format data file is stored in the [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] internal binary data format.</span></span>  
  
## <a name="characters-supported-as-terminators"></a><span data-ttu-id="4bebc-107">ターミネータとしてサポートされる文字</span><span class="sxs-lookup"><span data-stu-id="4bebc-107">Characters Supported As Terminators</span></span>  
 <span data-ttu-id="4bebc-108">**bcp** コマンド、BULK INSERT ステートメント、および OPENROWSET 一括行セット プロバイダーでは、フィールド ターミネータまたは行ターミネータとしてさまざまな文字がサポートされます。また、常に、各ターミネータの最初のインスタンスが検索されます。</span><span class="sxs-lookup"><span data-stu-id="4bebc-108">The **bcp** command, BULK INSERT statement, and the OPENROWSET bulk rowset provider support a variety of characters as field or row terminators and always look for the first instance of each terminator.</span></span> <span data-ttu-id="4bebc-109">ターミネータ用にサポートされる文字を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="4bebc-109">The following table lists the supported characters for terminators.</span></span>  
  
|<span data-ttu-id="4bebc-110">ターミネータ文字</span><span class="sxs-lookup"><span data-stu-id="4bebc-110">Terminating character</span></span>|<span data-ttu-id="4bebc-111">指定方法</span><span class="sxs-lookup"><span data-stu-id="4bebc-111">Indicated by</span></span>|  
|---------------------------|------------------|  
|<span data-ttu-id="4bebc-112">タブ</span><span class="sxs-lookup"><span data-stu-id="4bebc-112">Tab</span></span>|<span data-ttu-id="4bebc-113">\t</span><span class="sxs-lookup"><span data-stu-id="4bebc-113">\t</span></span><br /><br /> <span data-ttu-id="4bebc-114">既定のフィールド ターミネータです。</span><span class="sxs-lookup"><span data-stu-id="4bebc-114">This is the default field terminator.</span></span>|  
|<span data-ttu-id="4bebc-115">改行文字</span><span class="sxs-lookup"><span data-stu-id="4bebc-115">Newline character</span></span>|<span data-ttu-id="4bebc-116">\n</span><span class="sxs-lookup"><span data-stu-id="4bebc-116">\n</span></span><br /><br /> <span data-ttu-id="4bebc-117">既定の行ターミネータです。</span><span class="sxs-lookup"><span data-stu-id="4bebc-117">This is the default row terminator.</span></span>|  
|<span data-ttu-id="4bebc-118">キャリッジ リターン/ライン フィード</span><span class="sxs-lookup"><span data-stu-id="4bebc-118">Carriage return/line feed</span></span>|<span data-ttu-id="4bebc-119">\r</span><span class="sxs-lookup"><span data-stu-id="4bebc-119">\r</span></span>|  
|<span data-ttu-id="4bebc-120">円記号<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="4bebc-120">Backslash<sup>1</sup></span></span>|\\\|  
|<span data-ttu-id="4bebc-121">Null ターミネータ (非表示ターミネータ)<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="4bebc-121">Null terminator (nonvisible terminator)<sup>2</sup></span></span>|<span data-ttu-id="4bebc-122">\0</span><span class="sxs-lookup"><span data-stu-id="4bebc-122">\0</span></span>|  
|<span data-ttu-id="4bebc-123">任意の印刷可能な文字 (NULL、タブ、改行、およびキャリッジ リターンを除き、制御文字は印刷可能ではありません)</span><span class="sxs-lookup"><span data-stu-id="4bebc-123">Any printable character (control characters are not printable, except null, tab, newline, and carriage return)</span></span>|<span data-ttu-id="4bebc-124">(\*、A、t、l など)</span><span class="sxs-lookup"><span data-stu-id="4bebc-124">(\*, A, t, l, and so on)</span></span>|  
|<span data-ttu-id="4bebc-125">上に列挙したターミネータ文字の一部または全部を含む 10 文字までの印刷可能な文字列</span><span class="sxs-lookup"><span data-stu-id="4bebc-125">String of up to 10 printable characters, including some or all of the terminators listed earlier</span></span>|<span data-ttu-id="4bebc-126">(\*\*\t\*\*、end、!!!!!!!!!!、\t-\n など)</span><span class="sxs-lookup"><span data-stu-id="4bebc-126">(\*\*\t\*\*, end, !!!!!!!!!!, \t-\n, and so on)</span></span>|  
  
 <span data-ttu-id="4bebc-127"><sup>1</sup>制御文字を生成するために、円記号のエスケープ文字と共に使用できるのは、t、n、r、0および ' \ 0 ' の文字だけです。</span><span class="sxs-lookup"><span data-stu-id="4bebc-127"><sup>1</sup> Only the t, n, r, 0 and '\0' characters work with the backslash escape character to produce a control character.</span></span>  
  
 <span data-ttu-id="4bebc-128"><sup>2</sup>出力時には null 制御文字 (\ 0) は表示されませんが、データファイル内の個別の文字です。</span><span class="sxs-lookup"><span data-stu-id="4bebc-128"><sup>2</sup> Even though the null control character (\0) is not visible when printed, it is a distinct character in the data file.</span></span> <span data-ttu-id="4bebc-129">つまり、フィールド ターミネータまたは行ターミネータとして NULL 制御文字を使用することと、フィールド ターミネータまたは行ターミネータをまったく使用しないことは異なります。</span><span class="sxs-lookup"><span data-stu-id="4bebc-129">This means that using the null control character as a field or row terminator is different than having no field or row terminator at all.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="4bebc-130">データ内にターミネータ文字が出現すると、データではなく、ターミネータとして解釈されます。その文字に続くデータは、次のフィールドまたは次のレコードに属すると解釈されます。</span><span class="sxs-lookup"><span data-stu-id="4bebc-130">If a terminator character occurs within the data, it is interpreted as a terminator, not as data, and the data after that character is interpreted as belonging to the next field or record.</span></span> <span data-ttu-id="4bebc-131">したがって、ターミネータがデータに出現することがないように、注意深くターミネータを選択してください。</span><span class="sxs-lookup"><span data-stu-id="4bebc-131">Therefore, choose your terminators carefully to make sure that they never appear in your data.</span></span> <span data-ttu-id="4bebc-132">たとえば、データに下位サロゲートが含まれている場合、フィールド ターミネータには下位サロゲート フィールド ターミネータは適していません。</span><span class="sxs-lookup"><span data-stu-id="4bebc-132">For example, a low surrogate field terminator would not be a good choice for a field terminator if the data contains that low surrogate.</span></span>  
  
## <a name="using-row-terminators"></a><span data-ttu-id="4bebc-133">行ターミネータの使用</span><span class="sxs-lookup"><span data-stu-id="4bebc-133">Using Row Terminators</span></span>  
 <span data-ttu-id="4bebc-134">行ターミネータと最後のフィールドのターミネータを兼用できます。</span><span class="sxs-lookup"><span data-stu-id="4bebc-134">The row terminator can be the same character as the terminator for the last field.</span></span> <span data-ttu-id="4bebc-135">ただし、通常は、行ターミネータを別に指定する方が便利です。</span><span class="sxs-lookup"><span data-stu-id="4bebc-135">Generally, however, a distinct row terminator is useful.</span></span> <span data-ttu-id="4bebc-136">たとえば、表形式の出力を生成するには、各行の最後のフィールドを改行文字 (\n) で終了し、他のすべてのフィールドをタブ文字 (\t) で終了します。</span><span class="sxs-lookup"><span data-stu-id="4bebc-136">For example, to produce tabular output, terminate the last field in each row with the newline character (\n) and all other fields with the tab character (\t).</span></span> <span data-ttu-id="4bebc-137">各データ レコードをデータ ファイル内の独自の行に配置するには、行ターミネータに \r\n の組み合わせを指定します。</span><span class="sxs-lookup"><span data-stu-id="4bebc-137">To place each data record on its own line in the data file, specify the combination \r\n as the row terminator.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4bebc-138">**bcp** を対話的に使用し、\n (改行) を行ターミネータとして指定すると、 **bcp** によって自動的に \r (キャリッジ リターン) 文字が前に付加され、結果的には行ターミネータが \r\n になります。</span><span class="sxs-lookup"><span data-stu-id="4bebc-138">When you use **bcp** interactively and specify \n (newline) as the row terminator, **bcp** automatically prefixes it with a \r (carriage return) character, which results in a row terminator of \r\n.</span></span>  
  
## <a name="specifying-terminators-for-bulk-export"></a><span data-ttu-id="4bebc-139">一括エクスポートのターミネータの指定</span><span class="sxs-lookup"><span data-stu-id="4bebc-139">Specifying Terminators for Bulk Export</span></span>  
 <span data-ttu-id="4bebc-140">またはデータを一括エクスポートするときに、既定以外のターミネータを使用する場合は、 `char` `nchar` **bcp**コマンドに対してターミネータを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4bebc-140">When you bulk export `char` or `nchar` data, and want to use a non-default terminator, you must specify the terminator to the **bcp** command.</span></span> <span data-ttu-id="4bebc-141">次のいずれかの方法で、ターミネータを指定できます。</span><span class="sxs-lookup"><span data-stu-id="4bebc-141">You can specify terminators in any of the following ways:</span></span>  
  
-   <span data-ttu-id="4bebc-142">フォーマット ファイルで、フィールドごとにターミネータを指定します。</span><span class="sxs-lookup"><span data-stu-id="4bebc-142">With a format file that specifies the terminator on a field-by-field basis.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4bebc-143">フォーマット ファイルの使用方法の詳細は、「[データのインポートまたはエクスポート用のフォーマット ファイル &#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4bebc-143">For information about how to use format files, see [Format Files for Importing or Exporting Data &#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md).</span></span>  
  
-   <span data-ttu-id="4bebc-144">フォーマット ファイルを使用しない場合には、次の方法があります。</span><span class="sxs-lookup"><span data-stu-id="4bebc-144">Without a format file, the following alternatives exist:</span></span>  
  
    -   <span data-ttu-id="4bebc-145">**-t** スイッチを使用して、行内の最後のフィールドを除くすべてのフィールドのフィールド ターミネータを指定します。および、**-r** スイッチを使用して、行ターミネータを指定します。</span><span class="sxs-lookup"><span data-stu-id="4bebc-145">Using the **-t** switch to specify the row terminator for all the fields except the last field in the row and using the **-r** switch to specify a row terminator.</span></span>  
  
    -   <span data-ttu-id="4bebc-146">**-t** スイッチを指定しないで、文字形式のスイッチ ( **-c**または **-w** ) を使用すると、フィールド ターミネータがタブ文字 \t に設定されます。</span><span class="sxs-lookup"><span data-stu-id="4bebc-146">Using a character-format switch (**-c** or **-w**) without the **-t** switch, which sets the field terminator to the tab character, \t.</span></span> <span data-ttu-id="4bebc-147">これは、 **-t**\t を指定することと同じです。</span><span class="sxs-lookup"><span data-stu-id="4bebc-147">This is the same as specifying **-t**\t.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="4bebc-148">**-n** (ネイティブ データ) スイッチまたは **-N** (Unicode ネイティブ) スイッチを指定すると、ターミネータは挿入されません。</span><span class="sxs-lookup"><span data-stu-id="4bebc-148">If you specify the **-n** (native data) or **-N** (Unicode native) switch, terminators are not inserted.</span></span>  
  
    -   <span data-ttu-id="4bebc-149">対話的な **bcp** コマンドに、 **in** オプションまたは **out** オプションが含まれていて、フォーマット ファイル スイッチ ( **-f**) またはデータ形式スイッチ ( **-n**、 **-c**、 **-w**、または **-N**) のいずれも含まれていない場合に、プレフィックス長とフィールド長の指定をしないと、各フィールドのフィールド ターミネータが要求されます。既定ではターミネータは "なし" になっています。</span><span class="sxs-lookup"><span data-stu-id="4bebc-149">If an interactive **bcp** command contains the **in** or **out** option without either the format file switch (**-f**) or a data-format switch (**-n**, **-c**, **-w**, or **-N**), and you have chosen not to specify prefix length and field length, the command prompts for the field terminator of each field, with a default of none:</span></span>  
  
         `Enter field terminator [none]:`  
  
         <span data-ttu-id="4bebc-150">通常は、既定値を選択することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="4bebc-150">Generally, the default is a suitable choice.</span></span> <span data-ttu-id="4bebc-151">ただし、`char` データ フィールドまたは `nchar` データ フィールドについては、次の「ターミネータ使用のガイドライン」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4bebc-151">However, for `char` or `nchar` data fields, see the following subsection, "Guidelines for Using Terminators."</span></span> <span data-ttu-id="4bebc-152">コンテキスト内でこのプロンプトが表示される例については、「[bcp を使用した互換性のためのデータ形式の指定 &#40;SQL Server&#41;](specify-data-formats-for-compatibility-when-using-bcp-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4bebc-152">For an example that shows this prompt in context, see [Specify Data Formats for Compatibility when Using bcp &#40;SQL Server&#41;](specify-data-formats-for-compatibility-when-using-bcp-sql-server.md).</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="4bebc-153">**bcp** コマンドですべてのフィールドを対話形式で指定すると、各フィールドへの応答を XML 形式以外のファイルに保存するように要求するプロンプトが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4bebc-153">After you interactively specify all of the fields in a **bcp** command, the command prompts you save your responses for each field in a non-XML format file.</span></span> <span data-ttu-id="4bebc-154">XML 以外のフォーマット ファイルの詳細については、「[XML 以外のフォーマット ファイル &#40;SQL Server&#41;](xml-format-files-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4bebc-154">For more information about non-XML format files, see [Non-XML Format Files &#40;SQL Server&#41;](xml-format-files-sql-server.md).</span></span>  
  
### <a name="guidelines-for-using-terminators"></a><span data-ttu-id="4bebc-155">ターミネータ使用のガイドライン</span><span class="sxs-lookup"><span data-stu-id="4bebc-155">Guidelines for Using Terminators</span></span>  
 <span data-ttu-id="4bebc-156">状況によっては、`char` データ フィールドまたは `nchar` データ フィールドには、ターミネータが役に立つ場合があります。</span><span class="sxs-lookup"><span data-stu-id="4bebc-156">In some situations, a terminator is useful for a `char` or `nchar` data field.</span></span> <span data-ttu-id="4bebc-157">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="4bebc-157">For example:</span></span>  
  
-   <span data-ttu-id="4bebc-158">プレフィックス長がわからないプログラムにインポートされるデータ ファイル内で NULL 値が含まれるデータ列。</span><span class="sxs-lookup"><span data-stu-id="4bebc-158">For a data column that contains a null value in a data file that will be imported into a program that does not understand the prefix length information.</span></span>  
  
     <span data-ttu-id="4bebc-159">NULL 値が含まれているすべてのデータ列は、可変長と見なされます。</span><span class="sxs-lookup"><span data-stu-id="4bebc-159">Any data column that contains a null value is considered variable length.</span></span> <span data-ttu-id="4bebc-160">プレフィックス長がない場合、ターミネータは、データが正しく解釈されるように NULL 値の末尾を識別する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4bebc-160">In the absence of prefix lengths, a terminator is necessary to identify the end of a null field, making sure that the data is correctly interpreted.</span></span>  
  
-   <span data-ttu-id="4bebc-161">多くの列によって領域が部分的にのみ使用されている、長い固定長の列。</span><span class="sxs-lookup"><span data-stu-id="4bebc-161">For a long fixed-length column whose space is only partially used by many rows.</span></span>  
  
     <span data-ttu-id="4bebc-162">この状況では、ターミネータを指定することで記憶領域が最小限になり、フィールドが可変長として処理されます。</span><span class="sxs-lookup"><span data-stu-id="4bebc-162">In this situation, specifying a terminator can minimize storage space allowing the field to be treated as a variable-length field.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="4bebc-163">例</span><span class="sxs-lookup"><span data-stu-id="4bebc-163">Examples</span></span>  
 <span data-ttu-id="4bebc-164">この例では、フィールド ターミネータにコンマ、行ターミネータに改行文字 (\n) を使用して、文字形式で `AdventureWorks``HumanResources.Department` テーブルから `Department-c-t.txt` データ ファイルにデータが一括エクスポートされます。</span><span class="sxs-lookup"><span data-stu-id="4bebc-164">This example bulk exports the data from the `AdventureWorks``HumanResources.Department` table to the `Department-c-t.txt` data file using character format, with a comma as a field terminator and the newline character (\n) as the row terminator.</span></span>  
  
 <span data-ttu-id="4bebc-165">**bcp** コマンドには、次のスイッチがあります。</span><span class="sxs-lookup"><span data-stu-id="4bebc-165">The **bcp** command contains the following switches.</span></span>  
  
|<span data-ttu-id="4bebc-166">Switch</span><span class="sxs-lookup"><span data-stu-id="4bebc-166">Switch</span></span>|<span data-ttu-id="4bebc-167">説明</span><span class="sxs-lookup"><span data-stu-id="4bebc-167">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="4bebc-168">**-c**</span><span class="sxs-lookup"><span data-stu-id="4bebc-168">**-c**</span></span>|<span data-ttu-id="4bebc-169">データ フィールドが文字データとして読み込まれることを指定します。</span><span class="sxs-lookup"><span data-stu-id="4bebc-169">Specifies that the data fields be loaded as character data.</span></span>|  
|<span data-ttu-id="4bebc-170">**-t** `,`</span><span class="sxs-lookup"><span data-stu-id="4bebc-170">**-t** `,`</span></span>|<span data-ttu-id="4bebc-171">コンマ (,) をフィールド ターミネータとして指定します。</span><span class="sxs-lookup"><span data-stu-id="4bebc-171">Specifies a comma (,) as the field terminator.</span></span>|  
|<span data-ttu-id="4bebc-172">**-r** \n</span><span class="sxs-lookup"><span data-stu-id="4bebc-172">**-r** \n</span></span>|<span data-ttu-id="4bebc-173">改行文字を行ターミネータとして指定します。</span><span class="sxs-lookup"><span data-stu-id="4bebc-173">Specifies the row terminator as a newline character.</span></span> <span data-ttu-id="4bebc-174">改行文字は既定の行ターミネータなので省略できます。</span><span class="sxs-lookup"><span data-stu-id="4bebc-174">This is the default row terminator, so specifying it is optional.</span></span>|  
|<span data-ttu-id="4bebc-175">**-T**</span><span class="sxs-lookup"><span data-stu-id="4bebc-175">**-T**</span></span>|<span data-ttu-id="4bebc-176">**bcp** ユーティリティが統合セキュリティを使用した信頼関係接続を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続することを指定します。</span><span class="sxs-lookup"><span data-stu-id="4bebc-176">Specifies that the **bcp** utility connects to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] with a trusted connection using integrated security.</span></span> <span data-ttu-id="4bebc-177">**-T** を指定しない場合、正常にログインするには **-U** と **-P** を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4bebc-177">If **-T** is not specified, you need to specify **-U** and **-P** to successfully log in.</span></span>|  
  
 <span data-ttu-id="4bebc-178">詳細については、「 [bcp Utility](../../tools/bcp-utility.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4bebc-178">For more information, see [bcp Utility](../../tools/bcp-utility.md).</span></span>  
  
 <span data-ttu-id="4bebc-179">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows コマンド プロンプトで、次のように入力します。</span><span class="sxs-lookup"><span data-stu-id="4bebc-179">At the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows command prompt enter:</span></span>  
  
```  
bcp AdventureWorks.HumanResources.Department out C:\myDepartment-c-t.txt -c -t, -r \n -T  
```  
  
 <span data-ttu-id="4bebc-180">このコマンドにより、それぞれ 4 つのフィールドを持つ 16 個のレコードが含まれる `Department-c-t.txt`が作成されます。</span><span class="sxs-lookup"><span data-stu-id="4bebc-180">This creates `Department-c-t.txt`, which contains 16 records with four fields each.</span></span> <span data-ttu-id="4bebc-181">各フィールドはコンマで区切られています。</span><span class="sxs-lookup"><span data-stu-id="4bebc-181">The fields are separated by a comma.</span></span>  
  
## <a name="specifying-terminators-for-bulk-import"></a><span data-ttu-id="4bebc-182">一括インポートのターミネータの指定</span><span class="sxs-lookup"><span data-stu-id="4bebc-182">Specifying Terminators for Bulk Import</span></span>  
 <span data-ttu-id="4bebc-183">`char` データまたは `nchar` データを一括インポートするときに、一括インポート コマンドではデータ ファイルで使用されているターミネータが認識される必要があります。</span><span class="sxs-lookup"><span data-stu-id="4bebc-183">When you bulk import `char` or `nchar` data, the bulk-import command must recognize the terminators that are used in the data file.</span></span> <span data-ttu-id="4bebc-184">次のように、ターミネータの指定方法は一括インポート コマンドによって異なります。</span><span class="sxs-lookup"><span data-stu-id="4bebc-184">How terminators can be specified depends on the bulk-import command, as follows:</span></span>  
  
-   <span data-ttu-id="4bebc-185">**bcp**</span><span class="sxs-lookup"><span data-stu-id="4bebc-185">**bcp**</span></span>  
  
     <span data-ttu-id="4bebc-186">インポート操作のターミネータの指定には、エクスポート操作と同じ構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="4bebc-186">Specifying terminators for an import operation uses the same syntax as for an export operation.</span></span> <span data-ttu-id="4bebc-187">詳細については、このトピックの「一括エクスポートのターミネータの指定」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4bebc-187">For more information, see "Specifying Terminators for Bulk Export," earlier in this topic.</span></span>  
  
-   <span data-ttu-id="4bebc-188">BULK INSERT</span><span class="sxs-lookup"><span data-stu-id="4bebc-188">BULK INSERT</span></span>  
  
     <span data-ttu-id="4bebc-189">次の表に示す修飾子を使用して、フォーマット ファイル内の個別のフィールドまたはデータ ファイル全体にターミネータを指定できます。</span><span class="sxs-lookup"><span data-stu-id="4bebc-189">Terminators can be specified for individual fields in a format file or for the whole data file by using the qualifiers shown in the following table.</span></span>  
  
    |<span data-ttu-id="4bebc-190">Qualifier</span><span class="sxs-lookup"><span data-stu-id="4bebc-190">Qualifier</span></span>|<span data-ttu-id="4bebc-191">説明</span><span class="sxs-lookup"><span data-stu-id="4bebc-191">Description</span></span>|  
    |---------------|-----------------|  
    |<span data-ttu-id="4bebc-192">FIELDTERMINATOR **= ' *`field_terminator`* '**</span><span class="sxs-lookup"><span data-stu-id="4bebc-192">FIELDTERMINATOR **='*`field_terminator`*'**</span></span>|<span data-ttu-id="4bebc-193">文字データ ファイルや Unicode 文字データ ファイルに使用されるフィールド ターミネータを指定します。</span><span class="sxs-lookup"><span data-stu-id="4bebc-193">Specifies the field terminator to be used for character and Unicode character data files.</span></span><br /><br /> <span data-ttu-id="4bebc-194">既定値は \t (タブ文字) です。</span><span class="sxs-lookup"><span data-stu-id="4bebc-194">The default is \t (tab character).</span></span>|  
    |<span data-ttu-id="4bebc-195">ROWTERMINATOR **= ' *`row_terminator`* '**</span><span class="sxs-lookup"><span data-stu-id="4bebc-195">ROWTERMINATOR **='*`row_terminator`*'**</span></span>|<span data-ttu-id="4bebc-196">文字データ ファイルや Unicode 文字データ ファイルに使用される行ターミネータを指定します。</span><span class="sxs-lookup"><span data-stu-id="4bebc-196">Specifies the row terminator to be used for character and Unicode character data files.</span></span><br /><br /> <span data-ttu-id="4bebc-197">既定値は \n (改行記号) です。</span><span class="sxs-lookup"><span data-stu-id="4bebc-197">The default is \n (newline character).</span></span>|  
  
     <span data-ttu-id="4bebc-198">詳細については、「[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4bebc-198">For more information, see [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql).</span></span>  
  
-   <span data-ttu-id="4bebc-199">INSERT ...SELECT \* FROM OPENROWSET(BULK...)</span><span class="sxs-lookup"><span data-stu-id="4bebc-199">INSERT ... SELECT \* FROM OPENROWSET(BULK...)</span></span>  
  
     <span data-ttu-id="4bebc-200">OPENROWSET 一括行セット プロバイダーでは、ターミネータを指定できるのはフォーマット ファイルのみです (Large Object データ型を除き、これは必須です)。</span><span class="sxs-lookup"><span data-stu-id="4bebc-200">For the OPENROWSET bulk rowset provider, terminators can be specified only in the format file (which is required except for large-object data types).</span></span> <span data-ttu-id="4bebc-201">文字データ ファイルで既定以外のターミネータが使用されている場合、フォーマット ファイルで定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4bebc-201">If a character data file uses a non-default terminator, it must be defined in the format file.</span></span> <span data-ttu-id="4bebc-202">詳細については、「[フォーマット ファイルの作成 &#40;SQL Server&#41;](create-a-format-file-sql-server.md) および [データの一括インポートでのフォーマット ファイルの使用 &#40;SQL Server&#41;](use-a-format-file-to-bulk-import-data-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4bebc-202">For more information, see [Create a Format File &#40;SQL Server&#41;](create-a-format-file-sql-server.md) and [Use a Format File to Bulk Import Data &#40;SQL Server&#41;](use-a-format-file-to-bulk-import-data-sql-server.md).</span></span>  
  
     <span data-ttu-id="4bebc-203">OPENROWSET BULK 句の詳細については、「 [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql)を使用) を示すことができます。</span><span class="sxs-lookup"><span data-stu-id="4bebc-203">For more information about the OPENROWSET BULK clause, see [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql).</span></span>  
  
### <a name="examples"></a><span data-ttu-id="4bebc-204">例</span><span class="sxs-lookup"><span data-stu-id="4bebc-204">Examples</span></span>  
 <span data-ttu-id="4bebc-205">この例では、前述の例で作成された `Department-c-t.txt` データ ファイルから、 `myDepartment` サンプル データベースの [!INCLUDE[ssSampleDBUserInputNonLocal](../../includes/sssampledbuserinputnonlocal-md.md)] テーブルに、文字データを一括インポートします。</span><span class="sxs-lookup"><span data-stu-id="4bebc-205">The examples in this section bulk import character data form the `Department-c-t.txt` data file created in the preceding example into the `myDepartment` table in the [!INCLUDE[ssSampleDBUserInputNonLocal](../../includes/sssampledbuserinputnonlocal-md.md)] sample database.</span></span> <span data-ttu-id="4bebc-206">このテーブルを作成しないと、例を実行できません。</span><span class="sxs-lookup"><span data-stu-id="4bebc-206">Before you can run the examples, you must create this table.</span></span> <span data-ttu-id="4bebc-207">**dbo** スキーマでこのテーブルを作成するには、 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] のクエリ エディターで次のコードを実行します。</span><span class="sxs-lookup"><span data-stu-id="4bebc-207">To create this table under the **dbo** schema, in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] Query Editor, execute the following code:</span></span>  
  
```  
USE AdventureWorks;  
GO  
DROP TABLE myDepartment;  
CREATE TABLE myDepartment   
(DepartmentID smallint,  
Name nvarchar(50),  
GroupName nvarchar(50) NULL,  
ModifiedDate datetime not NULL CONSTRAINT DF_AddressType_ModifiedDate DEFAULT (GETDATE())  
);  
GO  
  
```  
  
#### <a name="a-using-bcp-to-interactively-specify-terminators"></a><span data-ttu-id="4bebc-208">A.</span><span class="sxs-lookup"><span data-stu-id="4bebc-208">A.</span></span> <span data-ttu-id="4bebc-209">bcp を使用した対話的なターミネータの指定</span><span class="sxs-lookup"><span data-stu-id="4bebc-209">Using bcp to interactively specify terminators</span></span>  
 <span data-ttu-id="4bebc-210">次の例では、 `Department-c-t.txt` コマンドを使用して、 `bcp` データ ファイルを一括インポートします。</span><span class="sxs-lookup"><span data-stu-id="4bebc-210">The following example bulk imports the `Department-c-t.txt` data file using a `bcp` command.</span></span> <span data-ttu-id="4bebc-211">このコマンドでは、一括エクスポート コマンドと同じコマンド スイッチを使用します。</span><span class="sxs-lookup"><span data-stu-id="4bebc-211">This command uses the same command switches as the bulk export command.</span></span> <span data-ttu-id="4bebc-212">詳細については、このトピックの「一括エクスポートのターミネータの指定」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4bebc-212">For more information, see "Specifying Terminators for Bulk Export," earlier in this topic.</span></span>  
  
 <span data-ttu-id="4bebc-213">Windows コマンド プロンプトで、次のように入力します。</span><span class="sxs-lookup"><span data-stu-id="4bebc-213">At the Windows command prompt enter:</span></span>  
  
```  
bcp AdventureWorks..myDepartment in C:\myDepartment-c-t.txt -c -t , -r \n -T  
```  
  
#### <a name="b-using-bulk-insert-to-interactively-specify-terminators"></a><span data-ttu-id="4bebc-214">B.</span><span class="sxs-lookup"><span data-stu-id="4bebc-214">B.</span></span> <span data-ttu-id="4bebc-215">BULK INSERT を使用した対話的なターミネータの指定</span><span class="sxs-lookup"><span data-stu-id="4bebc-215">Using BULK INSERT to interactively specify terminators</span></span>  
 <span data-ttu-id="4bebc-216">次の例では、次の表に示す修飾子を指定した `Department-c-t.txt` ステートメントを使用して、 `BULK INSERT` データ ファイルを一括インポートします。</span><span class="sxs-lookup"><span data-stu-id="4bebc-216">The following example bulk imports the `Department-c-t.txt` data file using a `BULK INSERT` statement that uses the qualifiers shown in the following table.</span></span>  
  
|<span data-ttu-id="4bebc-217">オプション</span><span class="sxs-lookup"><span data-stu-id="4bebc-217">Option</span></span>|<span data-ttu-id="4bebc-218">属性</span><span class="sxs-lookup"><span data-stu-id="4bebc-218">Attribute</span></span>|  
|------------|---------------|  
|<span data-ttu-id="4bebc-219">DATAFILETYPE **= ' `char` '**</span><span class="sxs-lookup"><span data-stu-id="4bebc-219">DATAFILETYPE **='`char`'**</span></span>|<span data-ttu-id="4bebc-220">データ フィールドが文字データとして読み込まれることを指定します。</span><span class="sxs-lookup"><span data-stu-id="4bebc-220">Specifies that the data fields be loaded as character data.</span></span>|  
|<span data-ttu-id="4bebc-221">FIELDTERMINATOR **='** `,` **'**</span><span class="sxs-lookup"><span data-stu-id="4bebc-221">FIELDTERMINATOR **='**`,`**'**</span></span>|<span data-ttu-id="4bebc-222">コンマ (`,`) をフィールド ターミネータとして指定します。</span><span class="sxs-lookup"><span data-stu-id="4bebc-222">Specifies a comma (`,`) as the field terminator.</span></span>|  
|<span data-ttu-id="4bebc-223">ROWTERMINATOR **='** `\n` **'**</span><span class="sxs-lookup"><span data-stu-id="4bebc-223">ROWTERMINATOR **='**`\n`**'**</span></span>|<span data-ttu-id="4bebc-224">改行文字を行ターミネータとして指定します。</span><span class="sxs-lookup"><span data-stu-id="4bebc-224">Specifies the row terminator as a newline character.</span></span>|  
  
 <span data-ttu-id="4bebc-225">[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] のクエリ エディターで、次のコードを実行します。</span><span class="sxs-lookup"><span data-stu-id="4bebc-225">In [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] Query Editor, execute the following code:</span></span>  
  
```  
USE AdventureWorks;  
GO  
BULK INSERT myDepartment FROM 'C:\myDepartment-c-t.txt'  
   WITH (  
      DATAFILETYPE = 'char',  
      FIELDTERMINATOR = ',',  
      ROWTERMINATOR = '\n'  
);  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="4bebc-226">参照</span><span class="sxs-lookup"><span data-stu-id="4bebc-226">See Also</span></span>  
 <span data-ttu-id="4bebc-227">[bcp ユーティリティ](../../tools/bcp-utility.md) </span><span class="sxs-lookup"><span data-stu-id="4bebc-227">[bcp Utility](../../tools/bcp-utility.md) </span></span>  
 <span data-ttu-id="4bebc-228">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="4bebc-228">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span></span>  
 <span data-ttu-id="4bebc-229">[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="4bebc-229">[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span></span>  
 <span data-ttu-id="4bebc-230">[bcp を使用したフィールド長の指定 &#40;SQL Server&#41;](specify-field-length-by-using-bcp-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="4bebc-230">[Specify Field Length by Using bcp &#40;SQL Server&#41;](specify-field-length-by-using-bcp-sql-server.md) </span></span>  
 <span data-ttu-id="4bebc-231">[bcp を使用したデータ ファイルのプレフィックス長の指定 &#40;SQL Server&#41;](specify-prefix-length-in-data-files-by-using-bcp-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="4bebc-231">[Specify Prefix Length in Data Files by Using bcp &#40;SQL Server&#41;](specify-prefix-length-in-data-files-by-using-bcp-sql-server.md) </span></span>  
 [<span data-ttu-id="4bebc-232">bcp を使用したファイル ストレージ型の指定 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="4bebc-232">Specify File Storage Type by Using bcp &#40;SQL Server&#41;</span></span>](specify-file-storage-type-by-using-bcp-sql-server.md)  
  
  
