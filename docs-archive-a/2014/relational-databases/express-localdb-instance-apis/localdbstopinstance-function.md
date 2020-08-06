---
title: LocalDBStopInstance 関数 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
api_name:
- LocalDBStopInstance
api_location:
- sqluserinstance.dll
topic_type:
- apiref
ms.assetid: 4bd73187-0aac-4f03-ac54-2b78e41917e5
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 48b014e65e0a02a5f866e5301b12dae3cd255b95
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711934"
---
# <a name="localdbstopinstance-function"></a><span data-ttu-id="48d93-102">LocalDBStopInstance 関数</span><span class="sxs-lookup"><span data-stu-id="48d93-102">LocalDBStopInstance Function</span></span>
  <span data-ttu-id="48d93-103">指定した SQL Server Express LocalDB インスタンスの実行を停止します。</span><span class="sxs-lookup"><span data-stu-id="48d93-103">Stops the specified SQL Server Express LocalDB instance from running.</span></span>  
  
 <span data-ttu-id="48d93-104">**ヘッダーファイル:** sqlncli</span><span class="sxs-lookup"><span data-stu-id="48d93-104">**Header file:** sqlncli.h</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48d93-105">構文</span><span class="sxs-lookup"><span data-stu-id="48d93-105">Syntax</span></span>  
  
```  
HRESULT LocalDBStopInstance(  
           PCWSTR pInstanceName,  
           DWORD dwFlags,   
           ULONG ulTimeout   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="48d93-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="48d93-106">Parameters</span></span>  
 <span data-ttu-id="48d93-107">*pInstanceName*</span><span class="sxs-lookup"><span data-stu-id="48d93-107">*pInstanceName*</span></span>  
 <span data-ttu-id="48d93-108">[入力] 停止する LocalDB インスタンスの名前。</span><span class="sxs-lookup"><span data-stu-id="48d93-108">[Input] The name of the LocalDB instance to stop.</span></span>  
  
 <span data-ttu-id="48d93-109">*dwFlags*</span><span class="sxs-lookup"><span data-stu-id="48d93-109">*dwFlags*</span></span>  
 <span data-ttu-id="48d93-110">[入力] インスタンスを停止する方法を指定する 1 つのフラグ値または複数フラグ値の組み合わせ。</span><span class="sxs-lookup"><span data-stu-id="48d93-110">[Input] One or a combination of the flag values specifying the way to stop the instance.</span></span>  
  
 <span data-ttu-id="48d93-111">使用できるフラグ:</span><span class="sxs-lookup"><span data-stu-id="48d93-111">Available flags:</span></span>  
  
 <span data-ttu-id="48d93-112">LOCALDB_SHUTDOWN_KILL_PROCESS</span><span class="sxs-lookup"><span data-stu-id="48d93-112">LOCALDB_SHUTDOWN_KILL_PROCESS</span></span>  
 <span data-ttu-id="48d93-113">オペレーティング システム コマンド kill process を使用して、すぐにシャットダウンします。</span><span class="sxs-lookup"><span data-stu-id="48d93-113">Shut down immediately using the kill process operating system command.</span></span>  
  
 <span data-ttu-id="48d93-114">LOCALDB_SHUTDOWN_WITH_NOWAIT</span><span class="sxs-lookup"><span data-stu-id="48d93-114">LOCALDB_SHUTDOWN_WITH_NOWAIT</span></span>  
 <span data-ttu-id="48d93-115">WITH NOWAIT オプション Transact-SQL コマンドを使用して、シャットダウンします。</span><span class="sxs-lookup"><span data-stu-id="48d93-115">Shut down using the WITH NOWAIT option Transact-SQL command.</span></span>  
  
 <span data-ttu-id="48d93-116">どのフラグも設定しない場合、LocalDB インスタンスは SHUTDOWN Transact-SQL コマンドを使用してシャットダウンされます。</span><span class="sxs-lookup"><span data-stu-id="48d93-116">If none of the flags is set, the LocalDB instance will be shut down using the SHUTDOWN Transact-SQL command.</span></span> <span data-ttu-id="48d93-117">両方のフラグを設定した場合、LOCALDB_SHUTDOWN_KILL_PROCESS フラグが優先されます。</span><span class="sxs-lookup"><span data-stu-id="48d93-117">If both flags are set, the LOCALDB_SHUTDOWN_KILL_PROCESS flag takes precedence.</span></span>  
  
 <span data-ttu-id="48d93-118">*ulTimeout*</span><span class="sxs-lookup"><span data-stu-id="48d93-118">*ulTimeout*</span></span>  
 <span data-ttu-id="48d93-119">[入力] この操作の完了を待機する秒単位の時間。</span><span class="sxs-lookup"><span data-stu-id="48d93-119">[Input] The time in seconds to wait for this operation to complete.</span></span> <span data-ttu-id="48d93-120">この値が 0 の場合、この関数は LocalDB インスタンスの停止を待たずにすぐに値を返します。</span><span class="sxs-lookup"><span data-stu-id="48d93-120">If this value is 0, this function will return immediately without waiting for the LocalDB instance to stop.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="48d93-121">戻り値</span><span class="sxs-lookup"><span data-stu-id="48d93-121">Returns</span></span>  
 <span data-ttu-id="48d93-122">S_OK</span><span class="sxs-lookup"><span data-stu-id="48d93-122">S_OK</span></span>  
 <span data-ttu-id="48d93-123">関数が正常に実行されました。</span><span class="sxs-lookup"><span data-stu-id="48d93-123">The function succeeded.</span></span>  
  
 [<span data-ttu-id="48d93-124">LOCALDB_ERROR_NOT_INSTALLED</span><span class="sxs-lookup"><span data-stu-id="48d93-124">LOCALDB_ERROR_NOT_INSTALLED</span></span>](../express-localdb-error-messages/localdb-error-not-installed.md)  
 <span data-ttu-id="48d93-125">SQL Server Express LocalDB は、コンピューターにインストールされていません。</span><span class="sxs-lookup"><span data-stu-id="48d93-125">SQL Server Express LocalDB is not installed on the computer.</span></span>  
  
 [<span data-ttu-id="48d93-126">LOCALDB_ERROR_INVALID_PARAMETER</span><span class="sxs-lookup"><span data-stu-id="48d93-126">LOCALDB_ERROR_INVALID_PARAMETER</span></span>](../express-localdb-error-messages/localdb-error-invalid-parameter.md)  
 <span data-ttu-id="48d93-127">指定した 1 つまたは複数の入力パラメーターが無効です。</span><span class="sxs-lookup"><span data-stu-id="48d93-127">One or more specified input parameters are invalid.</span></span>  
  
 [<span data-ttu-id="48d93-128">LOCALDB_ERROR_INVALID_INSTANCE_NAME</span><span class="sxs-lookup"><span data-stu-id="48d93-128">LOCALDB_ERROR_INVALID_INSTANCE_NAME</span></span>](../express-localdb-error-messages/localdb-error-invalid-instance-name.md)  
 <span data-ttu-id="48d93-129">指定したインスタンス名は無効です。</span><span class="sxs-lookup"><span data-stu-id="48d93-129">The specified instance name is invalid.</span></span>  
  
 [<span data-ttu-id="48d93-130">LOCALDB_ERROR_UNKNOWN_INSTANCE</span><span class="sxs-lookup"><span data-stu-id="48d93-130">LOCALDB_ERROR_UNKNOWN_INSTANCE</span></span>](../express-localdb-error-messages/localdb-error-unknown-instance.md)  
 <span data-ttu-id="48d93-131">インスタンスは存在しません。</span><span class="sxs-lookup"><span data-stu-id="48d93-131">The instance does not exist.</span></span>  
  
 [<span data-ttu-id="48d93-132">LOCALDB_ERROR_WAIT_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="48d93-132">LOCALDB_ERROR_WAIT_TIMEOUT</span></span>](../express-localdb-error-messages/localdb-error-wait-timeout.md)  
 <span data-ttu-id="48d93-133">同期ロックを取得しようとしているときにタイムアウトが発生しました。</span><span class="sxs-lookup"><span data-stu-id="48d93-133">A time-out occurred while trying to acquire the synchronization locks.</span></span>  
  
 [<span data-ttu-id="48d93-134">LOCALDB_ERROR_INSTANCE_STOP_FAILED</span><span class="sxs-lookup"><span data-stu-id="48d93-134">LOCALDB_ERROR_INSTANCE_STOP_FAILED</span></span>](../express-localdb-error-messages/localdb-error-instance-stop-failed.md)  
 <span data-ttu-id="48d93-135">停止操作は、指定された時間内に完了できませんでした。</span><span class="sxs-lookup"><span data-stu-id="48d93-135">The stop operation failed to complete within the given time.</span></span>  
  
 [<span data-ttu-id="48d93-136">LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG</span><span class="sxs-lookup"><span data-stu-id="48d93-136">LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG</span></span>](../express-localdb-error-messages/localdb-error-instance-folder-path-too-long.md)  
 <span data-ttu-id="48d93-137">インスタンスを格納するパスの長さが MAX_PATH を超過しています。</span><span class="sxs-lookup"><span data-stu-id="48d93-137">The path where the instance should be stored is longer than MAX_PATH.</span></span>  
  
 [<span data-ttu-id="48d93-138">LOCALDB_ERROR_CANNOT_GET_USER_PROFILE_FOLDER</span><span class="sxs-lookup"><span data-stu-id="48d93-138">LOCALDB_ERROR_CANNOT_GET_USER_PROFILE_FOLDER</span></span>](../express-localdb-error-messages/localdb-error-cannot-get-user-profile-folder.md)  
 <span data-ttu-id="48d93-139">ユーザー プロファイル フォルダーを取得できません。</span><span class="sxs-lookup"><span data-stu-id="48d93-139">A user profile folder cannot be retrieved.</span></span>  
  
 [<span data-ttu-id="48d93-140">LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_FOLDER</span><span class="sxs-lookup"><span data-stu-id="48d93-140">LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_FOLDER</span></span>](../express-localdb-error-messages/localdb-error-cannot-access-instance-folder.md)  
 <span data-ttu-id="48d93-141">インスタンス フォルダーにアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="48d93-141">An instance folder cannot be accessed.</span></span>  
  
 [<span data-ttu-id="48d93-142">LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_REGISTRY</span><span class="sxs-lookup"><span data-stu-id="48d93-142">LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_REGISTRY</span></span>](../express-localdb-error-messages/localdb-error-cannot-access-instance-registry.md)  
 <span data-ttu-id="48d93-143">インスタンス レジストリにアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="48d93-143">An instance registry cannot be accessed.</span></span>  
  
 [<span data-ttu-id="48d93-144">LOCALDB_ERROR_INSTANCE_CONFIGURATION_CORRUPT</span><span class="sxs-lookup"><span data-stu-id="48d93-144">LOCALDB_ERROR_INSTANCE_CONFIGURATION_CORRUPT</span></span>](../express-localdb-error-messages/localdb-error-instance-configuration-corrupt.md)  
 <span data-ttu-id="48d93-145">インスタンス構成が破損しています。</span><span class="sxs-lookup"><span data-stu-id="48d93-145">An instance configuration is corrupted.</span></span>  
  
 [<span data-ttu-id="48d93-146">LOCALDB_ERROR_CALLER_IS_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="48d93-146">LOCALDB_ERROR_CALLER_IS_NOT_OWNER</span></span>](../express-localdb-error-messages/localdb-error-caller-is-not-owner.md)  
 <span data-ttu-id="48d93-147">API の呼び出し元は、LocalDB インスタンスの所有者ではありません。</span><span class="sxs-lookup"><span data-stu-id="48d93-147">API caller is not LocalDB instance owner.</span></span>  
  
 [<span data-ttu-id="48d93-148">LOCALDB_ERROR_INTERNAL_ERROR</span><span class="sxs-lookup"><span data-stu-id="48d93-148">LOCALDB_ERROR_INTERNAL_ERROR</span></span>](../express-localdb-error-messages/localdb-error-internal-error.md)  
 <span data-ttu-id="48d93-149">予期しないエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="48d93-149">An unexpected error occurred.</span></span> <span data-ttu-id="48d93-150">詳細をイベント ログで確認してください。</span><span class="sxs-lookup"><span data-stu-id="48d93-150">See the event log for details.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="48d93-151">解説</span><span class="sxs-lookup"><span data-stu-id="48d93-151">Remarks</span></span>  
 <span data-ttu-id="48d93-152">LocalDB API を使用するコードサンプルについては、 [Localdb リファレンスの SQL Server Express](../sql-server-express-localdb-reference.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="48d93-152">For a code sample that uses LocalDB API, see [SQL Server Express LocalDB Reference](../sql-server-express-localdb-reference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48d93-153">参照</span><span class="sxs-lookup"><span data-stu-id="48d93-153">See Also</span></span>  
 [<span data-ttu-id="48d93-154">SQL Server Express LocalDB ヘッダーとバージョン情報</span><span class="sxs-lookup"><span data-stu-id="48d93-154">SQL Server Express LocalDB Header and Version Information</span></span>](sql-server-express-localdb-header-and-version-information.md)  
  
  
