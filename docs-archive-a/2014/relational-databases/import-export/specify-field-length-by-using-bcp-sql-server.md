---
title: bcp を使用したフィールド長の指定 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- native data format [SQL Server]
- default field lengths
- field length [SQL Server]
- data formats [SQL Server], field length
- bcp utility [SQL Server], field length
ms.assetid: 240f33ca-ef4a-413a-a4de-831885cb505b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 13343b4f3778df1bbe7ef1c99b3d06338f18631c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713162"
---
# <a name="specify-field-length-by-using-bcp-sql-server"></a><span data-ttu-id="7a4ae-102">bcp を使用したフィールド長の指定 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="7a4ae-102">Specify Field Length by Using bcp (SQL Server)</span></span>
  <span data-ttu-id="7a4ae-103">フィールド長は、文字形式でデータを表現するために必要な文字の最大数を示します。</span><span class="sxs-lookup"><span data-stu-id="7a4ae-103">The field length indicates the maximum number of characters that are required to represent data in character format.</span></span> <span data-ttu-id="7a4ae-104">データがネイティブ形式で格納されている場合、フィールド長は既にわかっています。たとえば、`int` データ型では 4 バイトになります。</span><span class="sxs-lookup"><span data-stu-id="7a4ae-104">The field length is already known if the data is stored in the native format; for example, the `int` data type takes 4 bytes.</span></span> <span data-ttu-id="7a4ae-105">プレフィックス長に0を指定した場合、 **bcp**コマンドを実行すると、フィールド長、既定のフィールド長、およびデータを格納するデータファイル内のデータストレージに対するフィールド長の影響を確認するプロンプトが表示され `char` ます。</span><span class="sxs-lookup"><span data-stu-id="7a4ae-105">If you have indicated 0 for the prefix length, the **bcp** command prompts you for field length, the default field lengths, and the impact of field-length on data storage in data files that contain `char` data.</span></span>  
  
## <a name="the-bcp-prompt-for-field-length"></a><span data-ttu-id="7a4ae-106">フィールド長を要求する bcp プロンプト</span><span class="sxs-lookup"><span data-stu-id="7a4ae-106">The bcp Prompt for Field Length</span></span>  
 <span data-ttu-id="7a4ae-107">対話型の **bcp** コマンドで、フォーマット ファイル スイッチ ( **-f**) またはデータ形式スイッチ ( **-n**、 **-c**、 **-w** または **-N**) のどちらも付けずに **in** または **out** オプションを指定すると、次のように各データ フィールドの長さを要求するプロンプトが表示されます。</span><span class="sxs-lookup"><span data-stu-id="7a4ae-107">If an interactive **bcp** command contains the **in** or **out** option without either the format file switch (**-f**) or a data-format switch (**-n**, **-c**, **-w**, or **-N**), the command prompts for the field length of each data field, as follows:</span></span>  
  
 `Enter length of field <field_name> [<default>]:`  
  
 <span data-ttu-id="7a4ae-108">コンテキスト内でこのプロンプトが表示される例については、「[bcp を使用した互換性のためのデータ形式の指定 &#40;SQL Server&#41;](specify-data-formats-for-compatibility-when-using-bcp-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7a4ae-108">For an example that shows this prompt in context, see [Specify Data Formats for Compatibility when Using bcp &#40;SQL Server&#41;](specify-data-formats-for-compatibility-when-using-bcp-sql-server.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7a4ae-109">**bcp** コマンドですべてのフィールドを対話形式で指定すると、各フィールドへの応答を XML 形式以外のファイルに保存するように要求するプロンプトが表示されます。</span><span class="sxs-lookup"><span data-stu-id="7a4ae-109">After you interactively specify all of the fields in a **bcp** command, the command prompts you save your responses for each field in a non-XML format file.</span></span> <span data-ttu-id="7a4ae-110">XML 以外のフォーマット ファイルの詳細については、「[XML 以外のフォーマット ファイル &#40;SQL Server&#41;](xml-format-files-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7a4ae-110">For more information on non-XML format files, see [Non-XML Format Files &#40;SQL Server&#41;](xml-format-files-sql-server.md).</span></span>  
  
 <span data-ttu-id="7a4ae-111">**bcp** コマンドでフィールド長を要求するプロンプトが表示されるかどうかは、次のさまざまな要素によって決まります。</span><span class="sxs-lookup"><span data-stu-id="7a4ae-111">Whether a **bcp** command prompts for field length depends on several factors, as follows:</span></span>  
  
-   <span data-ttu-id="7a4ae-112">固定長でないデータ型のコピー時にプレフィックス長を 0 に指定した場合、 **bcp** によってフィールド長を要求するプロンプトが表示されます。</span><span class="sxs-lookup"><span data-stu-id="7a4ae-112">When you copy data types that are not of fixed length and you specify a prefix length of 0, **bcp** prompts for a field length.</span></span>  
  
-   <span data-ttu-id="7a4ae-113">非文字データを文字データに変換するとき、 **bcp** によってデータの保存に十分な長さの既定フィールド長が提示されます。</span><span class="sxs-lookup"><span data-stu-id="7a4ae-113">When converting noncharacter data to character data, **bcp** suggests a default field length large enough to store the data.</span></span>  
  
-   <span data-ttu-id="7a4ae-114">ファイル保存形式が非文字である場合、 **bcp** コマンドによってフィールド長を要求するプロンプトは表示されません。</span><span class="sxs-lookup"><span data-stu-id="7a4ae-114">If the file storage type is noncharacter, the **bcp** command does not prompt for a field length.</span></span> <span data-ttu-id="7a4ae-115">データは、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のネイティブ データ表現 (ネイティブ形式) で格納されます。</span><span class="sxs-lookup"><span data-stu-id="7a4ae-115">The data is stored in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native data representation (native format).</span></span>  
  
## <a name="using-default-field-lengths"></a><span data-ttu-id="7a4ae-116">既定のフィールド長の使用</span><span class="sxs-lookup"><span data-stu-id="7a4ae-116">Using Default Field Lengths</span></span>  
 <span data-ttu-id="7a4ae-117">通常、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] では、 **bcp**によって提示された既定値をフィールド長に使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="7a4ae-117">Generally, [!INCLUDE[msCoName](../../includes/msconame-md.md)] recommends that you accept the **bcp**-suggested default values for the field length.</span></span> <span data-ttu-id="7a4ae-118">キャラクター モードのデータ ファイルが作成された場合、既定のフィールド長を使用することによって、データの切り捨てや数値オーバーフロー エラーの発生を防止できます。</span><span class="sxs-lookup"><span data-stu-id="7a4ae-118">When a character mode data file is created, using the default field length ensures that data is not truncated and that numeric overflow errors do not occur.</span></span>  
  
 <span data-ttu-id="7a4ae-119">不適切なフィールド長を指定すると、問題が発生する場合があります。</span><span class="sxs-lookup"><span data-stu-id="7a4ae-119">If you specify a field length that is incorrect, problems can occur.</span></span> <span data-ttu-id="7a4ae-120">たとえば、数値データをコピーするときに、そのデータに対して短すぎるフィールド長を指定すると、 **bcp** ユーティリティによってオーバーフロー エラー メッセージが出力され、データはコピーされません。</span><span class="sxs-lookup"><span data-stu-id="7a4ae-120">For instance, if you copy numeric data and you specify a field length that is too short for the data, the **bcp** utility prints an overflow message and does not copy the data.</span></span> <span data-ttu-id="7a4ae-121">また、データをエクスポート `datetime` し、文字列に対して26バイト未満のフィールド長を指定すると、 **bcp**ユーティリティによってデータが切り捨てられ、エラーメッセージも表示されません。</span><span class="sxs-lookup"><span data-stu-id="7a4ae-121">Also, if you export `datetime` data and specify a field length of less than 26 bytes for the character string, the **bcp** utility truncates the data without an error message.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="7a4ae-122">既定のサイズ オプションを使用すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は文字列全体を読み取ります。</span><span class="sxs-lookup"><span data-stu-id="7a4ae-122">When the default size option is used, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] expects to read an entire string.</span></span> <span data-ttu-id="7a4ae-123">場合によっては、既定のフィールド長を使用すると、"予期しないファイルの終了" エラーが発生することもあります。</span><span class="sxs-lookup"><span data-stu-id="7a4ae-123">In some situations, use of a default field length can lead to an "unexpected end of file" error.</span></span> <span data-ttu-id="7a4ae-124">通常、このエラーは、データ `money` `datetime` ファイル内で予期されるフィールドの一部のみが発生した場合に、データ型およびデータ型で発生します。たとえば、 `datetime` *mm* / *dd* / *yy*の値が時刻部分なしで指定されている場合、は、形式の値の予期される24文字の長さよりも短くなり `datetime` `char` ます。</span><span class="sxs-lookup"><span data-stu-id="7a4ae-124">Typically, this error occurs with the `money` and `datetime` data types when only part of the expected field occurs in the data file; for example, when a `datetime` value of *mm*/*dd*/*yy* is specified without the time component and is, therefore, shorter than the expected 24 character length of a `datetime` value in `char` format.</span></span> <span data-ttu-id="7a4ae-125">この種類のエラーを防止するには、フィールド ターミネータまたは固定長データ フィールドを使用するか、既定のフィールド長を別の値に変更します。</span><span class="sxs-lookup"><span data-stu-id="7a4ae-125">To avoid this type of error, use field terminators or fixed-length data fields, or change the default field length by specifying another value.</span></span>  
  
### <a name="default-field-lengths-for-character-file-storage"></a><span data-ttu-id="7a4ae-126">文字ファイル保存の既定のフィールド長</span><span class="sxs-lookup"><span data-stu-id="7a4ae-126">Default Field Lengths for Character File Storage</span></span>  
 <span data-ttu-id="7a4ae-127">次の表は、文字ファイル保存形式として保存されるデータの既定のフィールド長を示しています。</span><span class="sxs-lookup"><span data-stu-id="7a4ae-127">The following table lists the default field lengths for data to be stored as a character-file storage type.</span></span> <span data-ttu-id="7a4ae-128">NULL 値を使用できるデータの長さは、NULL 値を使用できないデータの長さと同じです。</span><span class="sxs-lookup"><span data-stu-id="7a4ae-128">Nullable data is the same length as nonnull data.</span></span>  
  
|<span data-ttu-id="7a4ae-129">データ型</span><span class="sxs-lookup"><span data-stu-id="7a4ae-129">Data type</span></span>|<span data-ttu-id="7a4ae-130">既定の長さ (文字数)</span><span class="sxs-lookup"><span data-stu-id="7a4ae-130">Default length (characters)</span></span>|  
|---------------|-----------------------------------|  
|`char`|<span data-ttu-id="7a4ae-131">列に対して定義された長さ</span><span class="sxs-lookup"><span data-stu-id="7a4ae-131">Length defined for the column</span></span>|  
|`varchar`|<span data-ttu-id="7a4ae-132">列に対して定義された長さ</span><span class="sxs-lookup"><span data-stu-id="7a4ae-132">Length defined for the column</span></span>|  
|`nchar`|<span data-ttu-id="7a4ae-133">列に対して定義された長さの 2 倍</span><span class="sxs-lookup"><span data-stu-id="7a4ae-133">Twice the length defined for the column</span></span>|  
|`nvarchar`|<span data-ttu-id="7a4ae-134">列に対して定義された長さの 2 倍</span><span class="sxs-lookup"><span data-stu-id="7a4ae-134">Twice the length defined for the column</span></span>|  
|`Text`|<span data-ttu-id="7a4ae-135">0</span><span class="sxs-lookup"><span data-stu-id="7a4ae-135">0</span></span>|  
|`ntext`|<span data-ttu-id="7a4ae-136">0</span><span class="sxs-lookup"><span data-stu-id="7a4ae-136">0</span></span>|  
|`bit`|<span data-ttu-id="7a4ae-137">1</span><span class="sxs-lookup"><span data-stu-id="7a4ae-137">1</span></span>|  
|`binary`|<span data-ttu-id="7a4ae-138">列に対して定義された長さの 2 倍 + 1</span><span class="sxs-lookup"><span data-stu-id="7a4ae-138">Twice the length defined for the column + 1</span></span>|  
|`varbinary`|<span data-ttu-id="7a4ae-139">列に対して定義された長さの 2 倍 + 1</span><span class="sxs-lookup"><span data-stu-id="7a4ae-139">Twice the length defined for the column + 1</span></span>|  
|`image`|<span data-ttu-id="7a4ae-140">0</span><span class="sxs-lookup"><span data-stu-id="7a4ae-140">0</span></span>|  
|`datetime`|<span data-ttu-id="7a4ae-141">24</span><span class="sxs-lookup"><span data-stu-id="7a4ae-141">24</span></span>|  
|`smalldatetime`|<span data-ttu-id="7a4ae-142">24</span><span class="sxs-lookup"><span data-stu-id="7a4ae-142">24</span></span>|  
|`float`|<span data-ttu-id="7a4ae-143">30</span><span class="sxs-lookup"><span data-stu-id="7a4ae-143">30</span></span>|  
|`real`|<span data-ttu-id="7a4ae-144">30</span><span class="sxs-lookup"><span data-stu-id="7a4ae-144">30</span></span>|  
|`int`|<span data-ttu-id="7a4ae-145">12</span><span class="sxs-lookup"><span data-stu-id="7a4ae-145">12</span></span>|  
|`bigint`|<span data-ttu-id="7a4ae-146">19</span><span class="sxs-lookup"><span data-stu-id="7a4ae-146">19</span></span>|  
|`smallint`|<span data-ttu-id="7a4ae-147">7</span><span class="sxs-lookup"><span data-stu-id="7a4ae-147">7</span></span>|  
|`tinyint`|<span data-ttu-id="7a4ae-148">5</span><span class="sxs-lookup"><span data-stu-id="7a4ae-148">5</span></span>|  
|`money`|<span data-ttu-id="7a4ae-149">30</span><span class="sxs-lookup"><span data-stu-id="7a4ae-149">30</span></span>|  
|`smallmoney`|<span data-ttu-id="7a4ae-150">30</span><span class="sxs-lookup"><span data-stu-id="7a4ae-150">30</span></span>|  
|`decimal`|<span data-ttu-id="7a4ae-151">41\*</span><span class="sxs-lookup"><span data-stu-id="7a4ae-151">41\*</span></span>|  
|`numeric`|<span data-ttu-id="7a4ae-152">41\*</span><span class="sxs-lookup"><span data-stu-id="7a4ae-152">41\*</span></span>|  
|`uniqueidentifier`|<span data-ttu-id="7a4ae-153">37</span><span class="sxs-lookup"><span data-stu-id="7a4ae-153">37</span></span>|  
|`timestamp`|<span data-ttu-id="7a4ae-154">17</span><span class="sxs-lookup"><span data-stu-id="7a4ae-154">17</span></span>|  
|`varchar(max)`|<span data-ttu-id="7a4ae-155">0</span><span class="sxs-lookup"><span data-stu-id="7a4ae-155">0</span></span>|  
|`varbinary(max)`|<span data-ttu-id="7a4ae-156">0</span><span class="sxs-lookup"><span data-stu-id="7a4ae-156">0</span></span>|  
|`nvarchar(max)`|<span data-ttu-id="7a4ae-157">0</span><span class="sxs-lookup"><span data-stu-id="7a4ae-157">0</span></span>|  
|<span data-ttu-id="7a4ae-158">UDT</span><span class="sxs-lookup"><span data-stu-id="7a4ae-158">UDT</span></span>|<span data-ttu-id="7a4ae-159">ユーザー定義型 (UDT) 列の長さ</span><span class="sxs-lookup"><span data-stu-id="7a4ae-159">Length of the user-defined term (UDT) column</span></span>|  
|<span data-ttu-id="7a4ae-160">XML</span><span class="sxs-lookup"><span data-stu-id="7a4ae-160">XML</span></span>|<span data-ttu-id="7a4ae-161">0</span><span class="sxs-lookup"><span data-stu-id="7a4ae-161">0</span></span>|  
  
 <span data-ttu-id="7a4ae-162">\*およびデータ型の詳細につい `decimal` `numeric` ては、「 [decimal および numeric &#40;transact-sql&#41;](/sql/t-sql/data-types/decimal-and-numeric-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7a4ae-162">\*For more information about the `decimal` and `numeric` data types, see [decimal and numeric &#40;Transact-SQL&#41;](/sql/t-sql/data-types/decimal-and-numeric-transact-sql).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7a4ae-163">`tinyint` 型の列には、0 ～ 255 の値を入力できます。この範囲の任意の数を表現するために必要な最大文字数は 3 です。これは、100 ～ 255 に相当します。</span><span class="sxs-lookup"><span data-stu-id="7a4ae-163">A column of type `tinyint` can have values from 0 through 255; the maximum number of characters that are needed to represent any number in that range is three (representing values 100 through 255).</span></span>  
  
### <a name="default-field-lengths-for-native-file-storage"></a><span data-ttu-id="7a4ae-164">ネイティブ ファイル保存の既定のフィールド長</span><span class="sxs-lookup"><span data-stu-id="7a4ae-164">Default Field Lengths for Native File Storage</span></span>  
 <span data-ttu-id="7a4ae-165">次の表は、ネイティブ ファイル保存形式として保存されるデータの既定のフィールド長を示しています。</span><span class="sxs-lookup"><span data-stu-id="7a4ae-165">The following table lists the default field lengths for data to be stored as native file storage type.</span></span> <span data-ttu-id="7a4ae-166">NULL 値を使用できるデータの長さは、NULL 値を使用できないデータの長さと同じです。また、文字データは常に文字形式で保存されます。</span><span class="sxs-lookup"><span data-stu-id="7a4ae-166">Nullable data is the same length as nonnull data, and character data is always stored in character format.</span></span>  
  
|<span data-ttu-id="7a4ae-167">データ型</span><span class="sxs-lookup"><span data-stu-id="7a4ae-167">Data type</span></span>|<span data-ttu-id="7a4ae-168">既定の長さ (文字数)</span><span class="sxs-lookup"><span data-stu-id="7a4ae-168">Default length (characters)</span></span>|  
|---------------|-----------------------------------|  
|`bit`|<span data-ttu-id="7a4ae-169">1</span><span class="sxs-lookup"><span data-stu-id="7a4ae-169">1</span></span>|  
|`binary`|<span data-ttu-id="7a4ae-170">列に対して定義された長さ</span><span class="sxs-lookup"><span data-stu-id="7a4ae-170">Length defined for the column</span></span>|  
|`varbinary`|<span data-ttu-id="7a4ae-171">列に対して定義された長さ</span><span class="sxs-lookup"><span data-stu-id="7a4ae-171">Length defined for the column</span></span>|  
|`image`|<span data-ttu-id="7a4ae-172">0</span><span class="sxs-lookup"><span data-stu-id="7a4ae-172">0</span></span>|  
|`datetime`|<span data-ttu-id="7a4ae-173">8</span><span class="sxs-lookup"><span data-stu-id="7a4ae-173">8</span></span>|  
|`smalldatetime`|<span data-ttu-id="7a4ae-174">4</span><span class="sxs-lookup"><span data-stu-id="7a4ae-174">4</span></span>|  
|`float`|<span data-ttu-id="7a4ae-175">8</span><span class="sxs-lookup"><span data-stu-id="7a4ae-175">8</span></span>|  
|`real`|<span data-ttu-id="7a4ae-176">4</span><span class="sxs-lookup"><span data-stu-id="7a4ae-176">4</span></span>|  
|`int`|<span data-ttu-id="7a4ae-177">4</span><span class="sxs-lookup"><span data-stu-id="7a4ae-177">4</span></span>|  
|`bigint`|<span data-ttu-id="7a4ae-178">8</span><span class="sxs-lookup"><span data-stu-id="7a4ae-178">8</span></span>|  
|`smallint`|<span data-ttu-id="7a4ae-179">2</span><span class="sxs-lookup"><span data-stu-id="7a4ae-179">2</span></span>|  
|`tinyint`|<span data-ttu-id="7a4ae-180">1</span><span class="sxs-lookup"><span data-stu-id="7a4ae-180">1</span></span>|  
|`money`|<span data-ttu-id="7a4ae-181">8</span><span class="sxs-lookup"><span data-stu-id="7a4ae-181">8</span></span>|  
|`smallmoney`|<span data-ttu-id="7a4ae-182">4</span><span class="sxs-lookup"><span data-stu-id="7a4ae-182">4</span></span>|  
|<span data-ttu-id="7a4ae-183">`decimal` <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="7a4ae-183">`decimal` <sup>1</sup></span></span>|<sup>*</sup>|  
|<span data-ttu-id="7a4ae-184">`numeric` <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="7a4ae-184">`numeric` <sup>1</sup></span></span>|<sup>*</sup>|  
|`uniqueidentifier`|<span data-ttu-id="7a4ae-185">16</span><span class="sxs-lookup"><span data-stu-id="7a4ae-185">16</span></span>|  
|`timestamp`|<span data-ttu-id="7a4ae-186">8</span><span class="sxs-lookup"><span data-stu-id="7a4ae-186">8</span></span>|  
  
 <span data-ttu-id="7a4ae-187"><sup>1</sup>およびデータ型の詳細につい `decimal` ては `numeric` 、「 [decimal および numeric &#40;transact-sql&#41;](/sql/t-sql/data-types/decimal-and-numeric-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7a4ae-187"><sup>1</sup> For more information about the `decimal` and `numeric` data types, see [decimal and numeric &#40;Transact-SQL&#41;](/sql/t-sql/data-types/decimal-and-numeric-transact-sql).</span></span>  
  
 <span data-ttu-id="7a4ae-188">前述のすべての場合に、後で [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に再読み込みするためにデータ ファイルを作成して、保存領域を最小限に抑えるには、既定のファイル保存形式と既定のフィールド長と共に、フィールド長プレフィックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="7a4ae-188">In all of the preceding cases, to create a data file for later reloading into [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that keeps the storage space to a minimum, use a length prefix with the default file storage type and the default field length.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a4ae-189">参照</span><span class="sxs-lookup"><span data-stu-id="7a4ae-189">See Also</span></span>  
 <span data-ttu-id="7a4ae-190">[bcp ユーティリティ](../../tools/bcp-utility.md) </span><span class="sxs-lookup"><span data-stu-id="7a4ae-190">[bcp Utility](../../tools/bcp-utility.md) </span></span>  
 <span data-ttu-id="7a4ae-191">[データ型 &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="7a4ae-191">[Data Types &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql) </span></span>  
 <span data-ttu-id="7a4ae-192">[フィールド ターミネータと行ターミネータの指定 &#40;SQL Server&#41;](specify-field-and-row-terminators-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="7a4ae-192">[Specify Field and Row Terminators &#40;SQL Server&#41;](specify-field-and-row-terminators-sql-server.md) </span></span>  
 <span data-ttu-id="7a4ae-193">[bcp を使用したデータ ファイルのプレフィックス長の指定 &#40;SQL Server&#41;](specify-prefix-length-in-data-files-by-using-bcp-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="7a4ae-193">[Specify Prefix Length in Data Files by Using bcp &#40;SQL Server&#41;](specify-prefix-length-in-data-files-by-using-bcp-sql-server.md) </span></span>  
 <span data-ttu-id="7a4ae-194">[bcp を使用したファイル ストレージ型の指定 &#40;SQL Server&#41;](specify-file-storage-type-by-using-bcp-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="7a4ae-194">[Specify File Storage Type by Using bcp &#40;SQL Server&#41;](specify-file-storage-type-by-using-bcp-sql-server.md) </span></span>  
 [<span data-ttu-id="7a4ae-195">一括インポート中の NULL の保持または既定値の使用 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="7a4ae-195">Keep Nulls or Use Default Values During Bulk Import &#40;SQL Server&#41;</span></span>](keep-nulls-or-use-default-values-during-bulk-import-sql-server.md)  
  
  
