---
title: bcp_control |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_control
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_control function
ms.assetid: 32187282-1385-4c52-9134-09f061eb44f5
author: rothja
ms.author: jroth
ms.openlocfilehash: 7ea5d60da8069707a53f3bdf2de53345cd11090f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630993"
---
# <a name="bcp_control"></a><span data-ttu-id="03dd4-102">bcp_control</span><span class="sxs-lookup"><span data-stu-id="03dd4-102">bcp_control</span></span>
  <span data-ttu-id="03dd4-103">ファイルと [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の間の一括コピーに使用するさまざまな制御パラメーターの既定の設定を変更します。</span><span class="sxs-lookup"><span data-stu-id="03dd4-103">Changes the default settings for various control parameters for a bulk copy between a file and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03dd4-104">構文</span><span class="sxs-lookup"><span data-stu-id="03dd4-104">Syntax</span></span>  
  
```  
  
RETCODE bcp_control (  
HDBC   
hdbc  
,  
INT   
eOption  
,  
void*   
iValue  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="03dd4-105">引数</span><span class="sxs-lookup"><span data-stu-id="03dd4-105">Arguments</span></span>  
 <span data-ttu-id="03dd4-106">*hdbc*</span><span class="sxs-lookup"><span data-stu-id="03dd4-106">*hdbc*</span></span>  
 <span data-ttu-id="03dd4-107">一括コピーが有効な ODBC 接続ハンドルです。</span><span class="sxs-lookup"><span data-stu-id="03dd4-107">Is the bulk copy-enabled ODBC connection handle.</span></span>  
  
 <span data-ttu-id="03dd4-108">*eOption*</span><span class="sxs-lookup"><span data-stu-id="03dd4-108">*eOption*</span></span>  
 <span data-ttu-id="03dd4-109">は次のいずれかです。</span><span class="sxs-lookup"><span data-stu-id="03dd4-109">Is one of the following:</span></span>  
  
 <span data-ttu-id="03dd4-110">BCPABORT </span><span class="sxs-lookup"><span data-stu-id="03dd4-110">BCPABORT</span></span>  
 <span data-ttu-id="03dd4-111">既に実行中の一括コピー操作を停止します。</span><span class="sxs-lookup"><span data-stu-id="03dd4-111">Stops a bulk-copy operation that is already in progress.</span></span> <span data-ttu-id="03dd4-112">別のスレッドからの BCPABORT の*eOption*を使用して**bcp_control**を呼び出し、実行中の一括コピー操作を停止します。</span><span class="sxs-lookup"><span data-stu-id="03dd4-112">Call **bcp_control** with an *eOption* of BCPABORT from another thread to stop a running bulk copy operation.</span></span> <span data-ttu-id="03dd4-113">*Ivalue*パラメーターは無視されます。</span><span class="sxs-lookup"><span data-stu-id="03dd4-113">The *iValue* parameter is ignored.</span></span>  
  
 <span data-ttu-id="03dd4-114">BCPBATCH </span><span class="sxs-lookup"><span data-stu-id="03dd4-114">BCPBATCH</span></span>  
 <span data-ttu-id="03dd4-115">バッチごとの行数を指定します。</span><span class="sxs-lookup"><span data-stu-id="03dd4-115">Is the number of rows per batch.</span></span> <span data-ttu-id="03dd4-116">既定値は 0 です。既定値を指定すると、データを抽出するときはテーブル内のすべての行が抽出されることを示し、データを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] にコピーするときはユーザー データ ファイル内のすべての行がコピーされることを示します。</span><span class="sxs-lookup"><span data-stu-id="03dd4-116">The default is 0, which indicates either all rows in a table, when data is being extracted, or all rows in the user data file, when data is being copied to an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="03dd4-117">1 より小さい値を指定すると、BCPBATCH は既定値にリセットされます。</span><span class="sxs-lookup"><span data-stu-id="03dd4-117">A value less than 1 resets BCPBATCH to the default.</span></span>  
  
 <span data-ttu-id="03dd4-118">BCPDELAYREADFMT</span><span class="sxs-lookup"><span data-stu-id="03dd4-118">BCPDELAYREADFMT</span></span>  
 <span data-ttu-id="03dd4-119">ブール値を true に設定すると、 [bcp_readfmt](bcp-readfmt.md)が実行時に読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="03dd4-119">A Boolean, if set to true, will cause [bcp_readfmt](bcp-readfmt.md) to read at execution.</span></span> <span data-ttu-id="03dd4-120">False (既定値) の場合、bcp_readfmt はすぐにフォーマットファイルを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="03dd4-120">If false (the default), bcp_readfmt will immediately read the format file.</span></span> <span data-ttu-id="03dd4-121">BCPDELAYREADFMT が true で bcp_columns または bcp_setcolfmt を呼び出すと、シーケンスエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="03dd4-121">A sequence error will occur if BCPDELAYREADFMT is true and you call bcp_columns or bcp_setcolfmt.</span></span>  
  
 <span data-ttu-id="03dd4-122">`bcp_control(hdbc,` `, (void *)FALSE)` Bcpdelayreadfmt および bcp_writefmt を呼び出した後に bcpdelayreadfmt を呼び出した場合も、シーケンスエラーが発生し `bcp_control(hdbc,` `, (void *)TRUE)` ます。</span><span class="sxs-lookup"><span data-stu-id="03dd4-122">A sequence error will also occur if you call `bcp_control(hdbc,` BCPDELAYREADFMT`, (void *)FALSE)` after calling `bcp_control(hdbc,` BCPDELAYREADFMT`, (void *)TRUE)` and bcp_writefmt.</span></span>  
  
 <span data-ttu-id="03dd4-123">詳細については、「[メタデータの検出](../native-client/features/metadata-discovery.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="03dd4-123">For more information, see [Metadata Discovery](../native-client/features/metadata-discovery.md).</span></span>  
  
 <span data-ttu-id="03dd4-124">BCPFILECP</span><span class="sxs-lookup"><span data-stu-id="03dd4-124">BCPFILECP</span></span>  
 <span data-ttu-id="03dd4-125">*Ivalue*には、データファイルのコードページの番号が含まれています。</span><span class="sxs-lookup"><span data-stu-id="03dd4-125">*iValue* contains the number of the code page for the data file.</span></span> <span data-ttu-id="03dd4-126">1252 や 850 などのコード ページ番号を指定するか、次のいずれかの値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="03dd4-126">You can specify the number of the code page, such as 1252 or 850, or one of these values:</span></span>  
  
 <span data-ttu-id="03dd4-127">BCPFILE_ACP: ファイル内のデータは Microsoft Windows にありますか?</span><span class="sxs-lookup"><span data-stu-id="03dd4-127">BCPFILE_ACP: data in the file is in the Microsoft Windows??</span></span> <span data-ttu-id="03dd4-128">クライアントのコードページ。</span><span class="sxs-lookup"><span data-stu-id="03dd4-128">code page of the client.</span></span>  
  
 <span data-ttu-id="03dd4-129">BCPFILE_OEMCP を指定すると、ファイル内のデータには、クライアントの OEM コード ページ (既定) が使用されます。</span><span class="sxs-lookup"><span data-stu-id="03dd4-129">BCPFILE_OEMCP: data in the file is in the OEM code page of the client (default).</span></span>  
  
 <span data-ttu-id="03dd4-130">BCPFILE_RAW を指定すると、ファイル内のデータには、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のコード ページが使用されます。</span><span class="sxs-lookup"><span data-stu-id="03dd4-130">BCPFILE_RAW: data in the file is in the code page of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="03dd4-131">BCPFILEFMT</span><span class="sxs-lookup"><span data-stu-id="03dd4-131">BCPFILEFMT</span></span>  
 <span data-ttu-id="03dd4-132">データ ファイル形式のバージョン番号を指定します。</span><span class="sxs-lookup"><span data-stu-id="03dd4-132">The version number of the data file format.</span></span> <span data-ttu-id="03dd4-133">80 ( [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] )、90 ( [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] )、100 ( [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] または [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] )、110 ( [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] )、または 120 () [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] を指定できます。</span><span class="sxs-lookup"><span data-stu-id="03dd4-133">This can be 80 ([!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]), 90 ([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]), 100 ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] or [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]), 110 ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]), or 120 ([!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]).</span></span> <span data-ttu-id="03dd4-134">120 が既定値です。</span><span class="sxs-lookup"><span data-stu-id="03dd4-134">120 is the default.</span></span> <span data-ttu-id="03dd4-135">このオプションは、以前のバージョンのサーバーでサポートされていた形式でデータをエクスポートおよびインポートする際に便利です。</span><span class="sxs-lookup"><span data-stu-id="03dd4-135">This is useful for exporting and importing data in formats that were supported by earlier version of the server.</span></span> <span data-ttu-id="03dd4-136">たとえば、サーバーのテキスト列から取得したデータを、以降の [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] サーバーの**varchar (max)** 列にインポートするには、 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 80 を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="03dd4-136">For example, to import data that was obtained from a text column in a [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] server into a **varchar(max)** column in a [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] or later server, you should specify 80.</span></span> <span data-ttu-id="03dd4-137">同様に、 **varchar (max)** 列からデータをエクスポートするときに80を指定した場合は、テキスト列が形式で保存され、 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] サーバーのテキスト列にインポートできるのと同じように保存され [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="03dd4-137">Similarly, if you specify 80 when exporting data from a **varchar(max)** column, it will be saved just like text columns are saved in the [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] format, and can be imported into a text column of a [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] server.</span></span>  
  
 <span data-ttu-id="03dd4-138">BCPFIRST </span><span class="sxs-lookup"><span data-stu-id="03dd4-138">BCPFIRST</span></span>  
 <span data-ttu-id="03dd4-139">ファイルまたはテーブルにコピーする最初のデータ行を指定します。</span><span class="sxs-lookup"><span data-stu-id="03dd4-139">Is the first row of data to file or table to copy.</span></span> <span data-ttu-id="03dd4-140">既定値は 1 です。1 未満の値を指定すると、このオプションは既定値にリセットされます。</span><span class="sxs-lookup"><span data-stu-id="03dd4-140">The default is 1; a value less than 1 resets this option to its default.</span></span>  
  
 <span data-ttu-id="03dd4-141">BCPFIRSTEX</span><span class="sxs-lookup"><span data-stu-id="03dd4-141">BCPFIRSTEX</span></span>  
 <span data-ttu-id="03dd4-142">BCP out 操作の場合は、データ ファイルにコピーするための、データベース テーブルの最初の行を指定します。</span><span class="sxs-lookup"><span data-stu-id="03dd4-142">For BCP out operations, specifies the first row of the database table to copy into the data file.</span></span>  
  
 <span data-ttu-id="03dd4-143">BCP in 操作の場合は、データベース テーブルにコピーするための、データ ファイルの最初の行を指定します。</span><span class="sxs-lookup"><span data-stu-id="03dd4-143">For BCP in operations, specifies the first row of the data file to copy into the database table.</span></span>  
  
 <span data-ttu-id="03dd4-144">*Ivalue*パラメーターは、値を含む符号付き64ビット整数のアドレスである必要があります。</span><span class="sxs-lookup"><span data-stu-id="03dd4-144">The *iValue* parameter is expected to be the address of a signed 64-bit integer containing the value.</span></span> <span data-ttu-id="03dd4-145">BCPFIRSTEX に渡すことができる最大値は 2 ^ 63-1 です。</span><span class="sxs-lookup"><span data-stu-id="03dd4-145">The maximum value that can be passed to BCPFIRSTEX is 2^63-1.</span></span>  
  
 <span data-ttu-id="03dd4-146">BCPFMTXML</span><span class="sxs-lookup"><span data-stu-id="03dd4-146">BCPFMTXML</span></span>  
 <span data-ttu-id="03dd4-147">XML 形式のフォーマット ファイルが生成されることを指定します。</span><span class="sxs-lookup"><span data-stu-id="03dd4-147">Specifies that the format file generated should be in XML format.</span></span> <span data-ttu-id="03dd4-148">既定では無効になっています。</span><span class="sxs-lookup"><span data-stu-id="03dd4-148">It is off by default.</span></span>  
  
 <span data-ttu-id="03dd4-149">XML フォーマットファイルには柔軟性がありますが、制約が追加されています。</span><span class="sxs-lookup"><span data-stu-id="03dd4-149">XML format files provide greater flexibility but with some added constraints.</span></span> <span data-ttu-id="03dd4-150">たとえば、フィールドのプレフィックスとターミネータを同時に指定することはできません。これは以前のフォーマットファイルでは可能でした。</span><span class="sxs-lookup"><span data-stu-id="03dd4-150">For example, you can not specify the prefix and terminator for a field simultaneously, which was possible in older format files.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="03dd4-151">XML フォーマット ファイルがサポートされるのは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client と共にインストールした場合だけです。</span><span class="sxs-lookup"><span data-stu-id="03dd4-151">XML format files are only supported when [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is installed along with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.</span></span>  
  
 <span data-ttu-id="03dd4-152">BCPHINTS</span><span class="sxs-lookup"><span data-stu-id="03dd4-152">BCPHINTS</span></span>  
 <span data-ttu-id="03dd4-153">*Ivalue*には、sqltchar 文字列ポインターが含まれています。</span><span class="sxs-lookup"><span data-stu-id="03dd4-153">*iValue* contains an SQLTCHAR character string pointer.</span></span> <span data-ttu-id="03dd4-154">ポインターが指す文字列には、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 一括コピー処理ヒント、または結果セットを返す Transact-SQL ステートメントを指定します。</span><span class="sxs-lookup"><span data-stu-id="03dd4-154">The string addressed specifies either [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bulk-copy processing hints or a Transact-SQL statement that returns a result set.</span></span> <span data-ttu-id="03dd4-155">複数の結果セットを返す Transact-SQL ステートメントを指定すると、1 つ目以外の結果セットはすべて無視されます。</span><span class="sxs-lookup"><span data-stu-id="03dd4-155">If a Transact-SQL statement is specified that returns more than one result set, all result sets after the first are ignored.</span></span> <span data-ttu-id="03dd4-156">一括コピー処理のヒントの詳細については、「 [Bcp ユーティリティ](../../tools/bcp-utility.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="03dd4-156">For more information about bulk-copy processing hints, see [bcp Utility](../../tools/bcp-utility.md).</span></span>  
  
 <span data-ttu-id="03dd4-157">BCPKEEPIDENTITY</span><span class="sxs-lookup"><span data-stu-id="03dd4-157">BCPKEEPIDENTITY</span></span>  
 <span data-ttu-id="03dd4-158">*Ivalue*が TRUE の場合、一括コピー関数は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] id 制約で定義された列に対して指定されたデータ値を挿入するように指定します。</span><span class="sxs-lookup"><span data-stu-id="03dd4-158">When *iValue* is TRUE, specifies that bulk copy functions insert data values supplied for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] columns defined with an identity constraint.</span></span> <span data-ttu-id="03dd4-159">入力ファイルには ID 列の値を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="03dd4-159">The input file must supply values for the identity columns.</span></span> <span data-ttu-id="03dd4-160">このオプションを設定しないと、挿入される行に対して新しい ID 値が生成されます。</span><span class="sxs-lookup"><span data-stu-id="03dd4-160">If this is not set, new identity values are generated for the inserted rows.</span></span> <span data-ttu-id="03dd4-161">ファイル内に存在する ID 列用のデータはすべて無視されます。</span><span class="sxs-lookup"><span data-stu-id="03dd4-161">Any data present in the file for the identity columns is ignored.</span></span>  
  
 <span data-ttu-id="03dd4-162">BCPKEEPNULLS </span><span class="sxs-lookup"><span data-stu-id="03dd4-162">BCPKEEPNULLS</span></span>  
 <span data-ttu-id="03dd4-163">ファイル内の空のデータ値を [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルで NULL 値に変換するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="03dd4-163">Specifies whether empty data values in the file will be converted to NULL values in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span> <span data-ttu-id="03dd4-164">*Ivalue*が TRUE の場合、空の値はテーブルで NULL に変換され [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="03dd4-164">When *iValue* is TRUE, empty values will be converted to NULL in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span> <span data-ttu-id="03dd4-165">既定では、空の値は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブル内の列の既定値 (存在する場合) に変換されます。</span><span class="sxs-lookup"><span data-stu-id="03dd4-165">The default is for empty values to be converted to a default value for the column in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table if a default exists.</span></span>  
  
 <span data-ttu-id="03dd4-166">BCPLAST </span><span class="sxs-lookup"><span data-stu-id="03dd4-166">BCPLAST</span></span>  
 <span data-ttu-id="03dd4-167">コピーする最後の行を示します。</span><span class="sxs-lookup"><span data-stu-id="03dd4-167">Is the last row to copy.</span></span> <span data-ttu-id="03dd4-168">既定では、すべての行がコピーされます。1 より小さい値を指定すると、このオプションは既定値にリセットされます。</span><span class="sxs-lookup"><span data-stu-id="03dd4-168">The default is to copy all rows; a value less than 1 resets this option to its default.</span></span>  
  
 <span data-ttu-id="03dd4-169">BCPLASTEX</span><span class="sxs-lookup"><span data-stu-id="03dd4-169">BCPLASTEX</span></span>  
 <span data-ttu-id="03dd4-170">BCP out 操作の場合は、データ ファイルにコピーするための、データベース テーブルの最後の行を指定します。</span><span class="sxs-lookup"><span data-stu-id="03dd4-170">For BCP out operations, specifies the last row of the database table to copy into the data file.</span></span>  
  
 <span data-ttu-id="03dd4-171">BCP in 操作の場合は、データベース テーブルにコピーするための、データ ファイルの最後の行を指定します。</span><span class="sxs-lookup"><span data-stu-id="03dd4-171">For BCP in operations, specifies the last row of the data file to copy into the database table.</span></span>  
  
 <span data-ttu-id="03dd4-172">*Ivalue*パラメーターは、値を含む符号付き64ビット整数のアドレスである必要があります。</span><span class="sxs-lookup"><span data-stu-id="03dd4-172">The *iValue* parameter is expected to be the address of a signed 64-bit integer containing the value.</span></span> <span data-ttu-id="03dd4-173">BCPLASTEX に渡すことができる最大値は 2^63-1 です。</span><span class="sxs-lookup"><span data-stu-id="03dd4-173">The maximum value that can be passed to BCPLASTEX is 2^63-1.</span></span>  
  
 <span data-ttu-id="03dd4-174">BCPMAXERRS </span><span class="sxs-lookup"><span data-stu-id="03dd4-174">BCPMAXERRS</span></span>  
 <span data-ttu-id="03dd4-175">一括コピー操作が失敗するまでに発生してもかまわないエラーの数です。</span><span class="sxs-lookup"><span data-stu-id="03dd4-175">Is the number of errors allowed before the bulk copy operation fails.</span></span> <span data-ttu-id="03dd4-176">既定値は10です。1未満の値を指定すると、このオプションが既定値にリセットされます。</span><span class="sxs-lookup"><span data-stu-id="03dd4-176">The default is 10; a value less than 1 resets this option to its default.</span></span> <span data-ttu-id="03dd4-177">一括コピーでは、最大 65,535 個のエラーが許容されます。</span><span class="sxs-lookup"><span data-stu-id="03dd4-177">Bulk copy imposes a maximum of 65,535 errors.</span></span> <span data-ttu-id="03dd4-178">このオプションに 65,535 を超える値を設定しようとすると、65,535 が設定されます。</span><span class="sxs-lookup"><span data-stu-id="03dd4-178">An attempt to set this option to a value larger than 65,535 results in the option being set to 65,535.</span></span>  
  
 <span data-ttu-id="03dd4-179">BCPODBC</span><span class="sxs-lookup"><span data-stu-id="03dd4-179">BCPODBC</span></span>  
 <span data-ttu-id="03dd4-180">TRUE の場合、文字形式で保存される**datetime**と**smalldatetime**の値が、ODBC タイムスタンプエスケープシーケンスのプレフィックスとサフィックスを使用するように指定します。</span><span class="sxs-lookup"><span data-stu-id="03dd4-180">When TRUE, specifies that **datetime** and **smalldatetime** values saved in character format will use the ODBC timestamp escape sequence prefix and suffix.</span></span> <span data-ttu-id="03dd4-181">BCPODBC オプションは、BCP_OUT にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="03dd4-181">The BCPODBC option only applies to BCP_OUT.</span></span>  
  
 <span data-ttu-id="03dd4-182">FALSE の場合、1997年1月1日を表す**datetime**値は、1997-01-01 00:00: 00.000 という文字列に変換されます。</span><span class="sxs-lookup"><span data-stu-id="03dd4-182">When FALSE, a **datetime** value representing January 1, 1997 is converted to the character string: 1997-01-01 00:00:00.000.</span></span> <span data-ttu-id="03dd4-183">TRUE の場合、同じ**datetime**値は {ts ' 1997-01-01 00:00: 00.000 '} と表されます。</span><span class="sxs-lookup"><span data-stu-id="03dd4-183">When TRUE, the same **datetime** value is represented as: {ts '1997-01-01 00:00:00.000'}.</span></span>  
  
 <span data-ttu-id="03dd4-184">BCPROWCOUNT</span><span class="sxs-lookup"><span data-stu-id="03dd4-184">BCPROWCOUNT</span></span>  
 <span data-ttu-id="03dd4-185">現在 (または最後) の BCP 操作で処理された行数を返します。</span><span class="sxs-lookup"><span data-stu-id="03dd4-185">Returns the number of rows affected by the current (or last) BCP operation.</span></span>  
  
 <span data-ttu-id="03dd4-186">BCPTEXTFILE</span><span class="sxs-lookup"><span data-stu-id="03dd4-186">BCPTEXTFILE</span></span>  
 <span data-ttu-id="03dd4-187">TRUE の場合、データ ファイルがバイナリ ファイルではなくテキスト ファイルであることを示します。</span><span class="sxs-lookup"><span data-stu-id="03dd4-187">When TRUE, specifies that the data file is a text file, rather than a binary file.</span></span> <span data-ttu-id="03dd4-188">ファイルがテキスト ファイルの場合、BCP では、データ ファイルの先頭 2 バイトに含まれる Unicode バイト マーカーをチェックして、そのファイルが Unicode 形式かどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="03dd4-188">If the file is a text file, BCP determines whether or not it is Unicode by checking the Unicode byte marker in the first two bytes of the data file.</span></span>  
  
 <span data-ttu-id="03dd4-189">BCPUNICODEFILE</span><span class="sxs-lookup"><span data-stu-id="03dd4-189">BCPUNICODEFILE</span></span>  
 <span data-ttu-id="03dd4-190">TRUE の場合、入力ファイルが Unicode ファイルであることを指定します。</span><span class="sxs-lookup"><span data-stu-id="03dd4-190">When TRUE, specifies the input file is a Unicode file.</span></span>  
  
 <span data-ttu-id="03dd4-191">*iValue*</span><span class="sxs-lookup"><span data-stu-id="03dd4-191">*iValue*</span></span>  
 <span data-ttu-id="03dd4-192">指定した*eOption*の値を指定します。</span><span class="sxs-lookup"><span data-stu-id="03dd4-192">Is the value for the specified *eOption*.</span></span> <span data-ttu-id="03dd4-193">*Ivalue*は、後で64ビット値に拡張できるように void ポインターにキャストされた整数 (longlong) 値です。</span><span class="sxs-lookup"><span data-stu-id="03dd4-193">*iValue* is an integer (LONGLONG) value cast to a void pointer to allow for future expansion to 64 bit values.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="03dd4-194">戻り値</span><span class="sxs-lookup"><span data-stu-id="03dd4-194">Returns</span></span>  
 <span data-ttu-id="03dd4-195">SUCCEED または FAIL。</span><span class="sxs-lookup"><span data-stu-id="03dd4-195">SUCCEED or FAIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="03dd4-196">解説</span><span class="sxs-lookup"><span data-stu-id="03dd4-196">Remarks</span></span>  
 <span data-ttu-id="03dd4-197">この関数では、一括コピー操作のさまざまな制御パラメーターを設定します。たとえば、一括コピーが取り消されるまでに発生してもかまわないエラーの数、データ ファイルから最初にコピーする行番号や最後にコピーする行番号、バッチ サイズなどを設定します。</span><span class="sxs-lookup"><span data-stu-id="03dd4-197">This function sets various control parameters for bulk-copy operations, including the number of errors allowed before canceling a bulk copy, the numbers of the first and last rows to copy from a data file, and the batch size.</span></span>  
  
 <span data-ttu-id="03dd4-198">また、この関数は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] から SELECT ステートメントの結果セットを一括コピーするときに、その SELECT ステートメントを指定するためにも使用します。</span><span class="sxs-lookup"><span data-stu-id="03dd4-198">This function is also used to specify the SELECT statement when bulk copying out from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] the result set of a SELECT.</span></span> <span data-ttu-id="03dd4-199">*EOption*を BCPHINTS に設定し、 *ivalue*を SET ステートメントを含む sqltchar 文字列へのポインターを持つように設定します。</span><span class="sxs-lookup"><span data-stu-id="03dd4-199">Set *eOption* to BCPHINTS and set *iValue* to have a pointer to an SQLTCHAR string containing the SELECT statement.</span></span>  
  
 <span data-ttu-id="03dd4-200">これらの制御パラメーターは、ユーザー ファイルと [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルの間でコピーを行う場合のみ意味があります。</span><span class="sxs-lookup"><span data-stu-id="03dd4-200">These control parameters are only meaningful when copying between a user file and an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span> <span data-ttu-id="03dd4-201">コントロールパラメーターの設定は、bcp_sendrow でにコピーされる行には影響しません [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。 [bcp_sendrow](bcp-sendrow.md)</span><span class="sxs-lookup"><span data-stu-id="03dd4-201">Control parameter settings have no effect on rows copied to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] with [bcp_sendrow](bcp-sendrow.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="03dd4-202">例</span><span class="sxs-lookup"><span data-stu-id="03dd4-202">Example</span></span>  
  
```  
// Variables like henv not specified.  
SQLHDBC      hdbc;  
DBINT      nRowsProcessed;  
  
// Application initiation, get an ODBC environment handle, allocate the  
// hdbc, and so on.  
...   
  
// Enable bulk copy prior to connecting on allocated hdbc.  
SQLSetConnectAttr(hdbc, SQL_COPT_SS_BCP, (SQLPOINTER) SQL_BCP_ON,  
   SQL_IS_INTEGER);  
  
// Connect to the data source, return on error.  
if (!SQL_SUCCEEDED(SQLConnect(hdbc, _T("myDSN"), SQL_NTS,  
   _T("myUser"), SQL_NTS, _T("myPwd"), SQL_NTS)))  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Initialize bulk copy.   
if (bcp_init(hdbc, _T("address"), _T("address.add"), _T("addr.err"),  
   DB_IN) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Set the number of rows per batch.   
if (bcp_control(hdbc, BCPBATCH, (void*) 1000) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Set file column count.   
if (bcp_columns(hdbc, 1) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Set the file format.   
if (bcp_colfmt(hdbc, 1, 0, 0, SQL_VARLEN_DATA, '\n', 1, 1)  
   == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Execute the bulk copy.   
if (bcp_exec(hdbc, &nRowsProcessed) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
printf_s("%ld rows processed by bulk copy.", nRowsProcessed);  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="03dd4-203">参照</span><span class="sxs-lookup"><span data-stu-id="03dd4-203">See Also</span></span>  
 [<span data-ttu-id="03dd4-204">一括コピー関数</span><span class="sxs-lookup"><span data-stu-id="03dd4-204">Bulk Copy Functions</span></span>](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
