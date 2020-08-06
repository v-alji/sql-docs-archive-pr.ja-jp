---
title: LocalDBStartInstance 関数 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
api_name:
- LocalDBStartInstance
api_location:
- sqluserinstance.dll
topic_type:
- apiref
ms.assetid: cb325f5d-10ee-4a56-ba28-db0074ab3926
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 748bc373e8b0dbad0a91247e068d21b67f2dbc1a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645087"
---
# <a name="localdbstartinstance-function"></a><span data-ttu-id="74036-102">LocalDBStartInstance 関数</span><span class="sxs-lookup"><span data-stu-id="74036-102">LocalDBStartInstance Function</span></span>
  <span data-ttu-id="74036-103">指定した名前の SQL Server Express LocalDB インスタンスを起動します。</span><span class="sxs-lookup"><span data-stu-id="74036-103">Starts the specified SQL Server Express LocalDB instance.</span></span>  
  
 <span data-ttu-id="74036-104">**ヘッダーファイル:** sqlncli</span><span class="sxs-lookup"><span data-stu-id="74036-104">**Header file:** sqlncli.h</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74036-105">構文</span><span class="sxs-lookup"><span data-stu-id="74036-105">Syntax</span></span>  
  
```  
HRESULT LocalDBStartInstance(  
           PCWSTR pInstanceName,  
           DWORD dwFlags,   
           LPWSTR wszSqlConnection,   
           LPDWORD lpcchSqlConnection   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="74036-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="74036-106">Parameters</span></span>  
 <span data-ttu-id="74036-107">*pInstanceName*</span><span class="sxs-lookup"><span data-stu-id="74036-107">*pInstanceName*</span></span>  
 <span data-ttu-id="74036-108">[入力] 起動する LocalDB インスタンスの名前。</span><span class="sxs-lookup"><span data-stu-id="74036-108">[Input] The name of the LocalDB instance to start.</span></span>  
  
 <span data-ttu-id="74036-109">*dwFlags*</span><span class="sxs-lookup"><span data-stu-id="74036-109">*dwFlags*</span></span>  
 <span data-ttu-id="74036-110">[入力] 将来の使用のために予約されています。</span><span class="sxs-lookup"><span data-stu-id="74036-110">[Input] Reserved for future use.</span></span> <span data-ttu-id="74036-111">現時点では、0 に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="74036-111">Currently should be set to 0.</span></span>  
  
 <span data-ttu-id="74036-112">*wszSqlConnection*</span><span class="sxs-lookup"><span data-stu-id="74036-112">*wszSqlConnection*</span></span>  
 <span data-ttu-id="74036-113">[出力] LocalDB インスタンスへの接続文字列を格納するバッファー。</span><span class="sxs-lookup"><span data-stu-id="74036-113">[Output] The buffer to store the connection string to the LocalDB instance.</span></span>  
  
 <span data-ttu-id="74036-114">*lpcchSqlConnection*</span><span class="sxs-lookup"><span data-stu-id="74036-114">*lpcchSqlConnection*</span></span>  
 <span data-ttu-id="74036-115">[入力/出力]入力時には、末尾の null を含め、 *wszSqlConnection*バッファーのサイズを文字数で格納します。</span><span class="sxs-lookup"><span data-stu-id="74036-115">[Input/Output] On input contains the size of the *wszSqlConnection* buffer in characters, including any trailing nulls.</span></span> <span data-ttu-id="74036-116">出力時に、指定されたバッファーサイズが小さすぎる場合、には、末尾の null を含め、必要なバッファーサイズが文字数で格納されます。</span><span class="sxs-lookup"><span data-stu-id="74036-116">On output, if the given buffer size is too small, contains the required buffer size in characters, including any trailing nulls.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="74036-117">戻り値</span><span class="sxs-lookup"><span data-stu-id="74036-117">Returns</span></span>  
 <span data-ttu-id="74036-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="74036-118">S_OK</span></span>  
 <span data-ttu-id="74036-119">関数が正常に実行されました。</span><span class="sxs-lookup"><span data-stu-id="74036-119">The function succeeded.</span></span>  
  
 [<span data-ttu-id="74036-120">LOCALDB_ERROR_NOT_INSTALLED</span><span class="sxs-lookup"><span data-stu-id="74036-120">LOCALDB_ERROR_NOT_INSTALLED</span></span>](../express-localdb-error-messages/localdb-error-not-installed.md)  
 <span data-ttu-id="74036-121">SQL Server Express LocalDB は、コンピューターにインストールされていません。</span><span class="sxs-lookup"><span data-stu-id="74036-121">SQL Server Express LocalDB is not installed on the computer.</span></span>  
  
 [<span data-ttu-id="74036-122">LOCALDB_ERROR_INVALID_PARAMETER</span><span class="sxs-lookup"><span data-stu-id="74036-122">LOCALDB_ERROR_INVALID_PARAMETER</span></span>](../express-localdb-error-messages/localdb-error-invalid-parameter.md)  
 <span data-ttu-id="74036-123">指定した 1 つまたは複数の入力パラメーターが無効です。</span><span class="sxs-lookup"><span data-stu-id="74036-123">One or more specified input parameters are invalid.</span></span>  
  
 [<span data-ttu-id="74036-124">LOCALDB_ERROR_INVALID_INSTANCE_NAME</span><span class="sxs-lookup"><span data-stu-id="74036-124">LOCALDB_ERROR_INVALID_INSTANCE_NAME</span></span>](../express-localdb-error-messages/localdb-error-invalid-instance-name.md)  
 <span data-ttu-id="74036-125">指定したインスタンス名は無効です。</span><span class="sxs-lookup"><span data-stu-id="74036-125">The specified instance name is invalid.</span></span>  
  
 [<span data-ttu-id="74036-126">LOCALDB_ERROR_UNKNOWN_INSTANCE</span><span class="sxs-lookup"><span data-stu-id="74036-126">LOCALDB_ERROR_UNKNOWN_INSTANCE</span></span>](../express-localdb-error-messages/localdb-error-unknown-instance.md)  
 <span data-ttu-id="74036-127">インスタンスは存在しません。</span><span class="sxs-lookup"><span data-stu-id="74036-127">The instance does not exist.</span></span>  
  
 [<span data-ttu-id="74036-128">LOCALDB_ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="74036-128">LOCALDB_ERROR_INSUFFICIENT_BUFFER</span></span>](../express-localdb-error-messages/localdb-error-insufficient-buffer.md)  
 <span data-ttu-id="74036-129">指定されたバッファー *wszSqlConnection*が小さすぎます。</span><span class="sxs-lookup"><span data-stu-id="74036-129">The specified buffer *wszSqlConnection* is too small.</span></span>  
  
 [<span data-ttu-id="74036-130">LOCALDB_ERROR_WAIT_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="74036-130">LOCALDB_ERROR_WAIT_TIMEOUT</span></span>](../express-localdb-error-messages/localdb-error-wait-timeout.md)  
 <span data-ttu-id="74036-131">同期ロックを取得しようとしているときにタイムアウトが発生しました。</span><span class="sxs-lookup"><span data-stu-id="74036-131">A time-out occurred while trying to acquire the synchronization locks.</span></span>  
  
 [<span data-ttu-id="74036-132">LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG</span><span class="sxs-lookup"><span data-stu-id="74036-132">LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG</span></span>](../express-localdb-error-messages/localdb-error-instance-folder-path-too-long.md)  
 <span data-ttu-id="74036-133">インスタンスを格納するパスの長さが MAX_PATH を超過しています。</span><span class="sxs-lookup"><span data-stu-id="74036-133">The path where the instance should be stored is longer than MAX_PATH.</span></span>  
  
 [<span data-ttu-id="74036-134">LOCALDB_ERROR_CANNOT_GET_USER_PROFILE_FOLDER</span><span class="sxs-lookup"><span data-stu-id="74036-134">LOCALDB_ERROR_CANNOT_GET_USER_PROFILE_FOLDER</span></span>](../express-localdb-error-messages/localdb-error-cannot-get-user-profile-folder.md)  
 <span data-ttu-id="74036-135">ユーザー プロファイル フォルダーを取得できません。</span><span class="sxs-lookup"><span data-stu-id="74036-135">A user profile folder cannot be retrieved.</span></span>  
  
 [<span data-ttu-id="74036-136">LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_FOLDER</span><span class="sxs-lookup"><span data-stu-id="74036-136">LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_FOLDER</span></span>](../express-localdb-error-messages/localdb-error-cannot-access-instance-folder.md)  
 <span data-ttu-id="74036-137">インスタンス フォルダーにアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="74036-137">An instance folder cannot be accessed.</span></span>  
  
 [<span data-ttu-id="74036-138">LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_REGISTRY</span><span class="sxs-lookup"><span data-stu-id="74036-138">LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_REGISTRY</span></span>](../express-localdb-error-messages/localdb-error-cannot-access-instance-registry.md)  
 <span data-ttu-id="74036-139">インスタンス レジストリにアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="74036-139">An instance registry cannot be accessed.</span></span>  
  
 [<span data-ttu-id="74036-140">LOCALDB_ERROR_CANNOT_MODIFY_INSTANCE_REGISTRY</span><span class="sxs-lookup"><span data-stu-id="74036-140">LOCALDB_ERROR_CANNOT_MODIFY_INSTANCE_REGISTRY</span></span>](../express-localdb-error-messages/localdb-error-cannot-modify-instance-registry.md)  
 <span data-ttu-id="74036-141">インスタンス レジストリを変更できません。</span><span class="sxs-lookup"><span data-stu-id="74036-141">An instance registry cannot be modified.</span></span>  
  
 [<span data-ttu-id="74036-142">LOCALDB_ERROR_CANNOT_CREATE_SQL_PROCESS</span><span class="sxs-lookup"><span data-stu-id="74036-142">LOCALDB_ERROR_CANNOT_CREATE_SQL_PROCESS</span></span>](../express-localdb-error-messages/localdb-error-cannot-create-sql-process.md)  
 <span data-ttu-id="74036-143">SQL Server のプロセスを作成できません。</span><span class="sxs-lookup"><span data-stu-id="74036-143">A process for SQL Server cannot be created.</span></span>  
  
 [<span data-ttu-id="74036-144">LOCALDB_ERROR_SQL_SERVER_STARTUP_FAILED</span><span class="sxs-lookup"><span data-stu-id="74036-144">LOCALDB_ERROR_SQL_SERVER_STARTUP_FAILED</span></span>](../express-localdb-error-messages/localdb-error-sql-server-startup-failed.md)  
 <span data-ttu-id="74036-145">SQL Server プロセスが開始されましたが、SQL Server の起動に失敗しました。</span><span class="sxs-lookup"><span data-stu-id="74036-145">A SQL Server process was started, but SQL Server startup failed.</span></span>  
  
 [<span data-ttu-id="74036-146">LOCALDB_ERROR_INSTANCE_CONFIGURATION_CORRUPT</span><span class="sxs-lookup"><span data-stu-id="74036-146">LOCALDB_ERROR_INSTANCE_CONFIGURATION_CORRUPT</span></span>](../express-localdb-error-messages/localdb-error-instance-configuration-corrupt.md)  
 <span data-ttu-id="74036-147">インスタンス構成が破損しました。</span><span class="sxs-lookup"><span data-stu-id="74036-147">An instance configuration was corrupted.</span></span>  
  
 [<span data-ttu-id="74036-148">LOCALDB_ERROR_AUTO_INSTANCE_CREATE_FAILED</span><span class="sxs-lookup"><span data-stu-id="74036-148">LOCALDB_ERROR_AUTO_INSTANCE_CREATE_FAILED</span></span>](../express-localdb-error-messages/localdb-error-auto-instance-create-failed.md)  
 <span data-ttu-id="74036-149">自動インスタンスを作成できません。</span><span class="sxs-lookup"><span data-stu-id="74036-149">Cannot create an automatic instance.</span></span> <span data-ttu-id="74036-150">エラーの詳細については、Windows アプリケーション イベント ログを参照してください。</span><span class="sxs-lookup"><span data-stu-id="74036-150">See the Windows Application event log for error details.</span></span>  
  
 [<span data-ttu-id="74036-151">LOCALDB_ERROR_INTERNAL_ERROR</span><span class="sxs-lookup"><span data-stu-id="74036-151">LOCALDB_ERROR_INTERNAL_ERROR</span></span>](../express-localdb-error-messages/localdb-error-internal-error.md)  
 <span data-ttu-id="74036-152">予期しないエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="74036-152">An unexpected error occurred.</span></span> <span data-ttu-id="74036-153">詳細をイベント ログで確認してください。</span><span class="sxs-lookup"><span data-stu-id="74036-153">See the event log for details.</span></span>  
  
## <a name="details"></a><span data-ttu-id="74036-154">詳細</span><span class="sxs-lookup"><span data-stu-id="74036-154">Details</span></span>  
 <span data-ttu-id="74036-155">接続バッファー引数 (*wszSqlConnection*) と接続バッファーサイズ引数 (*lpcchSqlConnection*) はどちらも省略可能です。</span><span class="sxs-lookup"><span data-stu-id="74036-155">Both the connection buffer argument (*wszSqlConnection*) and the connection buffer size argument (*lpcchSqlConnection*) are optional.</span></span> <span data-ttu-id="74036-156">次の表は、これらの引数を使用するためのオプションとその結果を示しています。</span><span class="sxs-lookup"><span data-stu-id="74036-156">The following table shows options for using these arguments and their results.</span></span>  
  
|<span data-ttu-id="74036-157">バッファー</span><span class="sxs-lookup"><span data-stu-id="74036-157">Buffer</span></span>|<span data-ttu-id="74036-158">バッファーサイズ</span><span class="sxs-lookup"><span data-stu-id="74036-158">Buffer size</span></span>|<span data-ttu-id="74036-159">理由</span><span class="sxs-lookup"><span data-stu-id="74036-159">Rationale</span></span>|<span data-ttu-id="74036-160">アクション</span><span class="sxs-lookup"><span data-stu-id="74036-160">Action</span></span>|  
|------------|-----------------|---------------|------------|  
|<span data-ttu-id="74036-161">NULL</span><span class="sxs-lookup"><span data-stu-id="74036-161">NULL</span></span>|<span data-ttu-id="74036-162">NULL</span><span class="sxs-lookup"><span data-stu-id="74036-162">NULL</span></span>|<span data-ttu-id="74036-163">ユーザーはインスタンスを起動しようとしますが、パイプ名は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="74036-163">User wants to start the instance and doesn't need a pipe name.</span></span>|<span data-ttu-id="74036-164">インスタンスを起動します (パイプの戻り値と必要なバッファー サイズの戻り値なし)。</span><span class="sxs-lookup"><span data-stu-id="74036-164">Starts an instance (no pipe return and no required buffer size return).</span></span>|  
|<span data-ttu-id="74036-165">NULL</span><span class="sxs-lookup"><span data-stu-id="74036-165">NULL</span></span>|<span data-ttu-id="74036-166">存在</span><span class="sxs-lookup"><span data-stu-id="74036-166">Present</span></span>|<span data-ttu-id="74036-167">ユーザーが出力バッファー サイズを要求します </span><span class="sxs-lookup"><span data-stu-id="74036-167">User asks for the output buffer size.</span></span> <span data-ttu-id="74036-168">(次の呼び出しで、ユーザーはおそらく実際の起動を要求します)。</span><span class="sxs-lookup"><span data-stu-id="74036-168">(In the next call the user will probably ask for an actual start.)</span></span>|<span data-ttu-id="74036-169">必要なバッファー サイズを返します (起動とパイプの戻り値なし)。</span><span class="sxs-lookup"><span data-stu-id="74036-169">Returns a required buffer size (no start and no pipe return).</span></span> <span data-ttu-id="74036-170">結果は S_OK です。</span><span class="sxs-lookup"><span data-stu-id="74036-170">Result is S_OK.</span></span>|  
|<span data-ttu-id="74036-171">存在</span><span class="sxs-lookup"><span data-stu-id="74036-171">Present</span></span>|<span data-ttu-id="74036-172">NULL</span><span class="sxs-lookup"><span data-stu-id="74036-172">NULL</span></span>|<span data-ttu-id="74036-173">許可されていません。入力に誤りがあります。</span><span class="sxs-lookup"><span data-stu-id="74036-173">Not allowed; incorrect input.</span></span>|<span data-ttu-id="74036-174">返される結果は、LOCALDB_ERROR_INVALID_PARAMETER です。</span><span class="sxs-lookup"><span data-stu-id="74036-174">Returned result is LOCALDB_ERROR_INVALID_PARAMETER.</span></span>|  
|<span data-ttu-id="74036-175">存在</span><span class="sxs-lookup"><span data-stu-id="74036-175">Present</span></span>|<span data-ttu-id="74036-176">存在</span><span class="sxs-lookup"><span data-stu-id="74036-176">Present</span></span>|<span data-ttu-id="74036-177">ユーザーはインスタンスを起動する必要があり、起動後に接続するパイプ名が必要です。</span><span class="sxs-lookup"><span data-stu-id="74036-177">User wants to start the instance and needs the pipe name to connect to it after it is started.</span></span>|<span data-ttu-id="74036-178">バッファー サイズを確認し、インスタンスを起動し、バッファーにあるパイプ名を返します。</span><span class="sxs-lookup"><span data-stu-id="74036-178">Checks the buffer size, starts the instance, and returns the pipe name in the buffer.</span></span> <br /><span data-ttu-id="74036-179">バッファーサイズ引数は、"server =" 文字列の長さを返します。終端の null は含まれません。</span><span class="sxs-lookup"><span data-stu-id="74036-179">The buffer size argument returns the length of the "server=" string, not including terminating nulls.</span></span>|  
  
 <span data-ttu-id="74036-180">LocalDB API を使用するコードサンプルについては、 [Localdb リファレンスの SQL Server Express](../sql-server-express-localdb-reference.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="74036-180">For a code sample that uses LocalDB API, see [SQL Server Express LocalDB Reference](../sql-server-express-localdb-reference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74036-181">参照</span><span class="sxs-lookup"><span data-stu-id="74036-181">See Also</span></span>  
 [<span data-ttu-id="74036-182">SQL Server Express LocalDB ヘッダーとバージョン情報</span><span class="sxs-lookup"><span data-stu-id="74036-182">SQL Server Express LocalDB Header and Version Information</span></span>](sql-server-express-localdb-header-and-version-information.md)  
  
  
