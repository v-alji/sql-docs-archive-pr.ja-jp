---
title: OpenSqlFilestream による FILESTREAM データへのアクセス | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
api_name:
- OpenSqlFilestream
api_location:
- sqlncli11.dll
helpviewer_keywords:
- OpenSqlFilestream
ms.assetid: d8205653-93dd-4599-8cdf-f9199074025f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 1a1416c0104e07c7bd228a723192ecb35bbe9216
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718285"
---
# <a name="access-filestream-data-with-opensqlfilestream"></a><span data-ttu-id="3312e-102">OpenSqlFilestream による FILESTREAM データへのアクセス</span><span class="sxs-lookup"><span data-stu-id="3312e-102">Access FILESTREAM Data with OpenSqlFilestream</span></span>
  <span data-ttu-id="3312e-103">OpenSqlFilestream API は、ファイルシステムに格納されている FILESTREAM バイナリラージオブジェクト (BLOB) の Win32 互換ファイルハンドルを取得します。</span><span class="sxs-lookup"><span data-stu-id="3312e-103">The OpenSqlFilestream API obtains a Win32 compatible file handle for a FILESTREAM binary large object (BLOB) that is stored in the file system.</span></span> <span data-ttu-id="3312e-104">このハンドルは、次のいずれかの Win32 API に渡すことができます。[ReadFile](https://go.microsoft.com/fwlink/?LinkId=86422)、[WriteFile](https://go.microsoft.com/fwlink/?LinkId=86423)、[TransmitFile](https://go.microsoft.com/fwlink/?LinkId=86424)、[SetFilePointer](https://go.microsoft.com/fwlink/?LinkId=86425)、[SetEndOfFile](https://go.microsoft.com/fwlink/?LinkId=86426)、[FlushFileBuffers](https://go.microsoft.com/fwlink/?LinkId=86427)。</span><span class="sxs-lookup"><span data-stu-id="3312e-104">The handle can be passed to any of the following Win32 APIs: [ReadFile](https://go.microsoft.com/fwlink/?LinkId=86422), [WriteFile](https://go.microsoft.com/fwlink/?LinkId=86423), [TransmitFile](https://go.microsoft.com/fwlink/?LinkId=86424), [SetFilePointer](https://go.microsoft.com/fwlink/?LinkId=86425), [SetEndOfFile](https://go.microsoft.com/fwlink/?LinkId=86426), or [FlushFileBuffers](https://go.microsoft.com/fwlink/?LinkId=86427).</span></span> <span data-ttu-id="3312e-105">このハンドルをその他の Win32 API に渡すと、ERROR_ACCESS_DENIED エラーが返されます。</span><span class="sxs-lookup"><span data-stu-id="3312e-105">If you pass this handle to any other Win32 API, the error ERROR_ACCESS_DENIED is returned.</span></span> <span data-ttu-id="3312e-106">このハンドルは、トランザクションをコミットまたはロールバックする前に Win32 [CloseHandle](https://go.microsoft.com/fwlink/?LinkId=86428) API に渡して閉じる必要があります。</span><span class="sxs-lookup"><span data-stu-id="3312e-106">The handle must be closed by passing it to the Win32 [CloseHandle](https://go.microsoft.com/fwlink/?LinkId=86428) API before the transaction is committed or rolled back.</span></span> <span data-ttu-id="3312e-107">ハンドルを閉じないと、サーバー側でリソースのリークが発生します。</span><span class="sxs-lookup"><span data-stu-id="3312e-107">Failing to close the handle will cause server-side resource leaks.</span></span>  
  
 <span data-ttu-id="3312e-108">すべての FILESTREAM データ コンテナー アクセスは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] トランザクションで実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3312e-108">All FILESTREAM data container access must be performed in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] transaction.</span></span> [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="3312e-109">ステートメントを同じトランザクションで実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="3312e-109">statements can also be executed in the same transaction.</span></span> <span data-ttu-id="3312e-110">これにより、SQL データと FILESTREAM BLOB データの一貫性が維持されます。</span><span class="sxs-lookup"><span data-stu-id="3312e-110">This maintains consistency between the SQL data and FILESTREAM BLOB data.</span></span>  
  
 <span data-ttu-id="3312e-111">Win32 を使用して FILESTREAM BLOB にアクセスするには、 [Windows 認証](../security/choose-an-authentication-mode.md) を有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="3312e-111">To access the FILESTREAM BLOB by using Win32, [Windows Authorization](../security/choose-an-authentication-mode.md) must be enabled.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="3312e-112">ファイルを書き込みアクセス用に開くと、トランザクションは FILESTREAM エージェントによって所有されます。</span><span class="sxs-lookup"><span data-stu-id="3312e-112">When the file is opened for write access, the transaction is owned by the FILESTREAM agent.</span></span> <span data-ttu-id="3312e-113">トランザクションが解放されるまで、Win32 ファイル I/O だけが許可されます。</span><span class="sxs-lookup"><span data-stu-id="3312e-113">Only Win32 file I/O is allowed until the transaction is released.</span></span> <span data-ttu-id="3312e-114">トランザクションを解放するには、書き込みハンドルを閉じる必要があります。</span><span class="sxs-lookup"><span data-stu-id="3312e-114">To release the transaction, the write handle must be closed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3312e-115">構文</span><span class="sxs-lookup"><span data-stu-id="3312e-115">Syntax</span></span>  
  
```  
  
  HANDLE OpenSqlFilestream (  
  LPCWSTR  
  FilestreamPath  
  ,  
  SQL_FILESTREAM_DESIRED_ACCESS  
  DesiredAccess,  
ULONGOpenOptions,LPBYTEFilestreamTransactionContext,SIZE_TFilestreamTransactionContextLength,PLARGE_INTEGERAllocationSize);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3312e-116">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3312e-116">Parameters</span></span>  
 <span data-ttu-id="3312e-117">*FilestreamPath*</span><span class="sxs-lookup"><span data-stu-id="3312e-117">*FilestreamPath*</span></span>  
 <span data-ttu-id="3312e-118">から`nvarchar(max)` [PathName](/sql/relational-databases/system-functions/pathname-transact-sql)関数によって返されるパスです。</span><span class="sxs-lookup"><span data-stu-id="3312e-118">[in] Is the `nvarchar(max)` path that is returned by the [PathName](/sql/relational-databases/system-functions/pathname-transact-sql) function.</span></span> <span data-ttu-id="3312e-119">PathName は、FILESTREAM のテーブルおよび列に対して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の SELECT または UPDATE の権限を持つアカウントのコンテキストから呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="3312e-119">PathName must be called from the context of an account that has [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SELECT or UPDATE permissions on the FILESTREAM table and column.</span></span>  
  
 <span data-ttu-id="3312e-120">*DesiredAccess*</span><span class="sxs-lookup"><span data-stu-id="3312e-120">*DesiredAccess*</span></span>  
 <span data-ttu-id="3312e-121">[in] FILESTREAM BLOB データへのアクセスに使用するモードを設定します。</span><span class="sxs-lookup"><span data-stu-id="3312e-121">[in] Sets the mode used to access FILESTREAM BLOB data.</span></span> <span data-ttu-id="3312e-122">この値は [DeviceIoControl 関数](https://go.microsoft.com/fwlink/?LinkId=105527)に渡されます。</span><span class="sxs-lookup"><span data-stu-id="3312e-122">This value is passed to the [DeviceIoControl Function](https://go.microsoft.com/fwlink/?LinkId=105527).</span></span>  
  
|<span data-ttu-id="3312e-123">名前</span><span class="sxs-lookup"><span data-stu-id="3312e-123">Name</span></span>|<span data-ttu-id="3312e-124">値</span><span class="sxs-lookup"><span data-stu-id="3312e-124">Value</span></span>|<span data-ttu-id="3312e-125">意味</span><span class="sxs-lookup"><span data-stu-id="3312e-125">Meaning</span></span>|  
|----------|-----------|-------------|  
|<span data-ttu-id="3312e-126">SQL_FILESTREAM_READ</span><span class="sxs-lookup"><span data-stu-id="3312e-126">SQL_FILESTREAM_READ</span></span>|<span data-ttu-id="3312e-127">0</span><span class="sxs-lookup"><span data-stu-id="3312e-127">0</span></span>|<span data-ttu-id="3312e-128">ファイルからデータを読み取ることができます。</span><span class="sxs-lookup"><span data-stu-id="3312e-128">Data can be read from the file.</span></span>|  
|<span data-ttu-id="3312e-129">SQL_FILESTREAM_WRITE</span><span class="sxs-lookup"><span data-stu-id="3312e-129">SQL_FILESTREAM_WRITE</span></span>|<span data-ttu-id="3312e-130">1</span><span class="sxs-lookup"><span data-stu-id="3312e-130">1</span></span>|<span data-ttu-id="3312e-131">ファイルにデータを書き込むことができます。</span><span class="sxs-lookup"><span data-stu-id="3312e-131">Data can be written to the file.</span></span>|  
|<span data-ttu-id="3312e-132">SQL_FILESTREAM_READWRITE</span><span class="sxs-lookup"><span data-stu-id="3312e-132">SQL_FILESTREAM_READWRITE</span></span>|<span data-ttu-id="3312e-133">2</span><span class="sxs-lookup"><span data-stu-id="3312e-133">2</span></span>|<span data-ttu-id="3312e-134">ファイルに対してデータを読み書きできます。</span><span class="sxs-lookup"><span data-stu-id="3312e-134">Data can be read and written from the file.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="3312e-135">これらの値は、sqlncli.h の SQL_FILESTREAM_DESIRED_ACCESS 列挙で定義されます。</span><span class="sxs-lookup"><span data-stu-id="3312e-135">These values are defined in the SQL_FILESTREAM_DESIRED_ACCESS enumeration in sqlncli.h.</span></span>  
  
 <span data-ttu-id="3312e-136">*OpenOptions*</span><span class="sxs-lookup"><span data-stu-id="3312e-136">*OpenOptions*</span></span>  
 <span data-ttu-id="3312e-137">[in] ファイルの属性とフラグです。</span><span class="sxs-lookup"><span data-stu-id="3312e-137">[in] The file attributes and flags.</span></span> <span data-ttu-id="3312e-138">このパラメーターでは、次のフラグを任意に組み合わせて指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="3312e-138">This parameter can also include any combination of the following flags.</span></span>  
  
|<span data-ttu-id="3312e-139">フラグ</span><span class="sxs-lookup"><span data-stu-id="3312e-139">Flag</span></span>|<span data-ttu-id="3312e-140">値</span><span class="sxs-lookup"><span data-stu-id="3312e-140">Value</span></span>|<span data-ttu-id="3312e-141">意味</span><span class="sxs-lookup"><span data-stu-id="3312e-141">Meaning</span></span>|  
|----------|-----------|-------------|  
|<span data-ttu-id="3312e-142">SQL_FILESTREAM_OPEN_NONE</span><span class="sxs-lookup"><span data-stu-id="3312e-142">SQL_FILESTREAM_OPEN_NONE</span></span>|<span data-ttu-id="3312e-143">0x00000000:</span><span class="sxs-lookup"><span data-stu-id="3312e-143">0x00000000:</span></span>|<span data-ttu-id="3312e-144">特にオプションを指定せずにファイルが開かれるか、または作成されます。</span><span class="sxs-lookup"><span data-stu-id="3312e-144">The file is being opened or created with no special options.</span></span>|  
|<span data-ttu-id="3312e-145">SQL_FILESTREAM_OPEN_FLAG_ASYNC</span><span class="sxs-lookup"><span data-stu-id="3312e-145">SQL_FILESTREAM_OPEN_FLAG_ASYNC</span></span>|<span data-ttu-id="3312e-146">0x00000001L</span><span class="sxs-lookup"><span data-stu-id="3312e-146">0x00000001L</span></span>|<span data-ttu-id="3312e-147">非同期 I/O 用にファイルが開かれるか、または作成されます。</span><span class="sxs-lookup"><span data-stu-id="3312e-147">The file is being opened or created for asynchronous I/O.</span></span>|  
|<span data-ttu-id="3312e-148">SQL_FILESTREAM_OPEN_FLAG_NO_BUFFERING</span><span class="sxs-lookup"><span data-stu-id="3312e-148">SQL_FILESTREAM_OPEN_FLAG_NO_BUFFERING</span></span>|<span data-ttu-id="3312e-149">0x00000002L</span><span class="sxs-lookup"><span data-stu-id="3312e-149">0x00000002L</span></span>|<span data-ttu-id="3312e-150">システム キャッシュを使用せずにファイルが開かれます。</span><span class="sxs-lookup"><span data-stu-id="3312e-150">The system opens the file by using no system caching.</span></span>|  
|<span data-ttu-id="3312e-151">SQL_FILESTREAM_OPEN_FLAG_NO_WRITE_THROUGH</span><span class="sxs-lookup"><span data-stu-id="3312e-151">SQL_FILESTREAM_OPEN_FLAG_NO_WRITE_THROUGH</span></span>|<span data-ttu-id="3312e-152">0x00000004L</span><span class="sxs-lookup"><span data-stu-id="3312e-152">0x00000004L</span></span>|<span data-ttu-id="3312e-153">中間キャッシュを使用せずに</span><span class="sxs-lookup"><span data-stu-id="3312e-153">The system does not write through an intermediate cache.</span></span> <span data-ttu-id="3312e-154">直接ディスクに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="3312e-154">Writes go directly to disk.</span></span>|  
|<span data-ttu-id="3312e-155">SQL_FILESTREAM_OPEN_FLAG_SEQUENTIAL_SCAN</span><span class="sxs-lookup"><span data-stu-id="3312e-155">SQL_FILESTREAM_OPEN_FLAG_SEQUENTIAL_SCAN</span></span>|<span data-ttu-id="3312e-156">0x00000008L</span><span class="sxs-lookup"><span data-stu-id="3312e-156">0x00000008L</span></span>|<span data-ttu-id="3312e-157">ファイルが先頭から末尾まで順次アクセスされます。</span><span class="sxs-lookup"><span data-stu-id="3312e-157">A file is accessed sequentially from beginning to end.</span></span> <span data-ttu-id="3312e-158">システムはこれをヒントとしてファイルのキャッシュを最適化します。</span><span class="sxs-lookup"><span data-stu-id="3312e-158">The system can use this as a hint to optimize file caching.</span></span> <span data-ttu-id="3312e-159">アプリケーションがランダム アクセスのファイル ポインターを移動させると、最適なキャッシングが行われなくなる場合があります。</span><span class="sxs-lookup"><span data-stu-id="3312e-159">If an application moves the file pointer for random access, optimal caching may not occur.</span></span>|  
|<span data-ttu-id="3312e-160">SQL_FILESTREAM_OPEN_FLAG_RANDOM_ACCESS</span><span class="sxs-lookup"><span data-stu-id="3312e-160">SQL_FILESTREAM_OPEN_FLAG_RANDOM_ACCESS</span></span>|<span data-ttu-id="3312e-161">0x00000010L</span><span class="sxs-lookup"><span data-stu-id="3312e-161">0x00000010L</span></span>|<span data-ttu-id="3312e-162">ファイルがランダムにアクセスされます。</span><span class="sxs-lookup"><span data-stu-id="3312e-162">A file is accessed randomly.</span></span> <span data-ttu-id="3312e-163">システムはこれをヒントとしてファイルのキャッシュを最適化します。</span><span class="sxs-lookup"><span data-stu-id="3312e-163">The system can use this as a hint to optimize file caching.</span></span>|  
  
 <span data-ttu-id="3312e-164">*FilestreamTransactionContext*</span><span class="sxs-lookup"><span data-stu-id="3312e-164">*FilestreamTransactionContext*</span></span>  
 <span data-ttu-id="3312e-165">[in] [GET_FILESTREAM_TRANSACTION_CONTEXT](/sql/t-sql/functions/get-filestream-transaction-context-transact-sql) 関数から返される値です。</span><span class="sxs-lookup"><span data-stu-id="3312e-165">[in] The value that is returned by the [GET_FILESTREAM_TRANSACTION_CONTEXT](/sql/t-sql/functions/get-filestream-transaction-context-transact-sql) function.</span></span>  
  
 <span data-ttu-id="3312e-166">*FilestreamTransactionContextLength*</span><span class="sxs-lookup"><span data-stu-id="3312e-166">*FilestreamTransactionContextLength*</span></span>  
 <span data-ttu-id="3312e-167">[in] GET_FILESTREAM_TRANSACTION_CONTEXT 関数から返される `varbinary(max)` データのバイト数です。</span><span class="sxs-lookup"><span data-stu-id="3312e-167">[in] Number of bytes in the `varbinary(max)` data that is returned by the GET_FILESTREAM_TRANSACTION_CONTEXT function.</span></span> <span data-ttu-id="3312e-168">この関数は、N バイトの配列を返します。</span><span class="sxs-lookup"><span data-stu-id="3312e-168">The function returns an array of N bytes.</span></span> <span data-ttu-id="3312e-169">N は関数によって決まる、返されるバイト配列のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="3312e-169">N is determined by the function and is a property of the byte array that is returned.</span></span>  
  
 <span data-ttu-id="3312e-170">*AllocationSize*</span><span class="sxs-lookup"><span data-stu-id="3312e-170">*AllocationSize*</span></span>  
 <span data-ttu-id="3312e-171">[in] データ ファイルの初期割り当てサイズをバイト単位で指定します。</span><span class="sxs-lookup"><span data-stu-id="3312e-171">[in] Specifies the initial allocation size of the data file in bytes.</span></span> <span data-ttu-id="3312e-172">読み取りモードでは無視されます。</span><span class="sxs-lookup"><span data-stu-id="3312e-172">It is ignored in read mode.</span></span> <span data-ttu-id="3312e-173">このパラメーターには NULL を指定できます。その場合、ファイル システムの既定の動作が使用されます。</span><span class="sxs-lookup"><span data-stu-id="3312e-173">This parameter can be NULL, in which case the default file system behavior is used.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3312e-174">戻り値</span><span class="sxs-lookup"><span data-stu-id="3312e-174">Return Value</span></span>  
 <span data-ttu-id="3312e-175">この関数の実行が成功した場合の戻り値は、指定したファイルへのオープン ハンドルです。</span><span class="sxs-lookup"><span data-stu-id="3312e-175">If the function succeeds, the return value is an open handle to a specified file.</span></span> <span data-ttu-id="3312e-176">失敗した場合の戻り値は、INVALID_HANDLE_VALUE です。</span><span class="sxs-lookup"><span data-stu-id="3312e-176">If the function fails, the return value is INVALID_HANDLE_VALUE.</span></span> <span data-ttu-id="3312e-177">詳細なエラー情報を取得するには、GetLastError() を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="3312e-177">For extended error information, call GetLastError().</span></span>  
  
## <a name="examples"></a><span data-ttu-id="3312e-178">例</span><span class="sxs-lookup"><span data-stu-id="3312e-178">Examples</span></span>  
 <span data-ttu-id="3312e-179">`OpenSqlFilestream` API を使用して Win32 ハンドルを取得する方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="3312e-179">The following examples show you how to use the `OpenSqlFilestream` API to obtain a Win32 handle.</span></span>  
  
 [!code-csharp[FILESTREAM#FS_CS_ReadAndWriteBLOB](../../snippets/tsql/SQL15/tsql/filestream/cs/filestream.cs#fs_cs_readandwriteblob)]  
  
 [!code-vb[FILESTREAM#FS_VB_ReadAndWriteBLOB](../../snippets/tsql/SQL15/tsql/filestream/vb/filestream.vb#fs_vb_readandwriteblob)]  
  
 [!code-cpp[FILESTREAM#FS_CPP_WriteBLOB](../../snippets/tsql/SQL15/tsql/filestream/cpp/filestream.cpp#fs_cpp_writeblob)]  
  
## <a name="remarks"></a><span data-ttu-id="3312e-180">解説</span><span class="sxs-lookup"><span data-stu-id="3312e-180">Remarks</span></span>  
 <span data-ttu-id="3312e-181">この API を使用するには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client をインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="3312e-181">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client must be installed to use this API.</span></span> <span data-ttu-id="3312e-182">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] クライアント ツールとともにインストールされます。</span><span class="sxs-lookup"><span data-stu-id="3312e-182">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client is installed with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client tools.</span></span> <span data-ttu-id="3312e-183">詳細については、「 [SQL Server Native Client のインストール](../native-client/applications/installing-sql-server-native-client.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3312e-183">For more information, see [Installing SQL Server Native Client](../native-client/applications/installing-sql-server-native-client.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3312e-184">参照</span><span class="sxs-lookup"><span data-stu-id="3312e-184">See Also</span></span>  
 <span data-ttu-id="3312e-185">[バイナリ ラージ オブジェクト &#40;Blob&#41; データ &#40;SQL Server&#41;](binary-large-object-blob-data-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="3312e-185">[Binary Large Object &#40;Blob&#41; Data &#40;SQL Server&#41;](binary-large-object-blob-data-sql-server.md) </span></span>  
 <span data-ttu-id="3312e-186">[FILESTREAM データの部分的な更新](make-partial-updates-to-filestream-data.md) </span><span class="sxs-lookup"><span data-stu-id="3312e-186">[Make Partial Updates to FILESTREAM Data](make-partial-updates-to-filestream-data.md) </span></span>  
 [<span data-ttu-id="3312e-187">FILESTREAM アプリケーションでのデータベース操作との競合の回避</span><span class="sxs-lookup"><span data-stu-id="3312e-187">Avoid Conflicts with Database Operations in FILESTREAM Applications</span></span>](avoid-conflicts-with-database-operations-in-filestream-applications.md)  
  
  
