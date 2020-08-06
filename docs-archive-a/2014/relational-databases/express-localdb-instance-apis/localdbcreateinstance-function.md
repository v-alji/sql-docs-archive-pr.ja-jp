---
title: LocalDBCreateInstance 関数 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
api_name:
- LocalDBCreateInstance
api_location:
- sqluserinstance.dll
topic_type:
- apiref
ms.assetid: 3eebb485-8a53-4a79-82a9-57b8de9f8e84
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: ff822c552176ad8c083a1c8ea6c0f2430f72972f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643372"
---
# <a name="localdbcreateinstance-function"></a><span data-ttu-id="15db0-102">LocalDBCreateInstance 関数</span><span class="sxs-lookup"><span data-stu-id="15db0-102">LocalDBCreateInstance Function</span></span>
  <span data-ttu-id="15db0-103">新しい SQL Server Express LocalDB インスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="15db0-103">Creates a new SQL Server Express LocalDB instance.</span></span>  
  
 <span data-ttu-id="15db0-104">**ヘッダーファイル:** sqlncli</span><span class="sxs-lookup"><span data-stu-id="15db0-104">**Header file:** sqlncli.h</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15db0-105">構文</span><span class="sxs-lookup"><span data-stu-id="15db0-105">Syntax</span></span>  
  
```  
HRESULT LocalDBCreateInstance(  
           PCWSTR wszVersion,  
           PCWSTR pInstanceName,   
           DWORD dwFlags   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="15db0-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="15db0-106">Parameters</span></span>  
 <span data-ttu-id="15db0-107">*wszVersion*</span><span class="sxs-lookup"><span data-stu-id="15db0-107">*wszVersion*</span></span>  
 <span data-ttu-id="15db0-108">[入力] LocalDB バージョン (11. 0 や 11.0.1094.2 など)。</span><span class="sxs-lookup"><span data-stu-id="15db0-108">[Input] The LocalDB version, for example 11.0 or 11.0.1094.2.</span></span>  
  
 <span data-ttu-id="15db0-109">*pInstanceName*</span><span class="sxs-lookup"><span data-stu-id="15db0-109">*pInstanceName*</span></span>  
 <span data-ttu-id="15db0-110">[入力] 作成する LocalDB インスタンスの名前。</span><span class="sxs-lookup"><span data-stu-id="15db0-110">[Input] The name for the LocalDB instance to create.</span></span>  
  
 <span data-ttu-id="15db0-111">*dwFlags*</span><span class="sxs-lookup"><span data-stu-id="15db0-111">*dwFlags*</span></span>  
 <span data-ttu-id="15db0-112">[入力] 将来の使用のために予約されています。</span><span class="sxs-lookup"><span data-stu-id="15db0-112">[Input] Reserved for future use.</span></span> <span data-ttu-id="15db0-113">現時点では、0 に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="15db0-113">Currently should be set to 0.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="15db0-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="15db0-114">Returns</span></span>  
 <span data-ttu-id="15db0-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="15db0-115">S_OK</span></span>  
 <span data-ttu-id="15db0-116">関数が正常に実行されました。</span><span class="sxs-lookup"><span data-stu-id="15db0-116">The function succeeded.</span></span>  
  
 [<span data-ttu-id="15db0-117">LOCALDB_ERROR_NOT_INSTALLED</span><span class="sxs-lookup"><span data-stu-id="15db0-117">LOCALDB_ERROR_NOT_INSTALLED</span></span>](../express-localdb-error-messages/localdb-error-not-installed.md)  
 <span data-ttu-id="15db0-118">SQL Server Express LocalDB は、コンピューターにインストールされていません。</span><span class="sxs-lookup"><span data-stu-id="15db0-118">SQL Server Express LocalDB is not installed on the computer.</span></span>  
  
 [<span data-ttu-id="15db0-119">LOCALDB_ERROR_INVALID_PARAMETER</span><span class="sxs-lookup"><span data-stu-id="15db0-119">LOCALDB_ERROR_INVALID_PARAMETER</span></span>](../express-localdb-error-messages/localdb-error-invalid-parameter.md)  
 <span data-ttu-id="15db0-120">指定した 1 つまたは複数の入力パラメーターが無効です。</span><span class="sxs-lookup"><span data-stu-id="15db0-120">One or more specified input parameters are invalid.</span></span>  
  
 [<span data-ttu-id="15db0-121">LOCALDB_ERROR_INVALID_INSTANCE_NAME</span><span class="sxs-lookup"><span data-stu-id="15db0-121">LOCALDB_ERROR_INVALID_INSTANCE_NAME</span></span>](../express-localdb-error-messages/localdb-error-invalid-instance-name.md)  
 <span data-ttu-id="15db0-122">指定したインスタンス名は無効です。</span><span class="sxs-lookup"><span data-stu-id="15db0-122">The specified instance name is invalid.</span></span>  
  
 [<span data-ttu-id="15db0-123">LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG</span><span class="sxs-lookup"><span data-stu-id="15db0-123">LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG</span></span>](../express-localdb-error-messages/localdb-error-instance-folder-path-too-long.md)  
 <span data-ttu-id="15db0-124">インスタンスを格納するパスの長さが MAX_PATH を超過しています。</span><span class="sxs-lookup"><span data-stu-id="15db0-124">The path where the instance should be stored is longer than MAX_PATH.</span></span>  
  
 [<span data-ttu-id="15db0-125">LOCALDB_ERROR_INSTANCE_EXISTS_WITH_LOWER_VERSION</span><span class="sxs-lookup"><span data-stu-id="15db0-125">LOCALDB_ERROR_INSTANCE_EXISTS_WITH_LOWER_VERSION</span></span>](../express-localdb-error-messages/localdb-error-instance-exists-with-lower-version.md)  
 <span data-ttu-id="15db0-126">指定したインスタンスは既に存在しますが、そのバージョンは要求よりも低いバージョンです。</span><span class="sxs-lookup"><span data-stu-id="15db0-126">The specified instance already exists but its version is lower than requested.</span></span>  
  
 [<span data-ttu-id="15db0-127">LOCALDB_ERROR_UNKNOWN_VERSION</span><span class="sxs-lookup"><span data-stu-id="15db0-127">LOCALDB_ERROR_UNKNOWN_VERSION</span></span>](../express-localdb-error-messages/localdb-error-unknown-version.md)  
 <span data-ttu-id="15db0-128">指定したバージョンは使用できません。</span><span class="sxs-lookup"><span data-stu-id="15db0-128">The specified version is not available.</span></span>  
  
 [<span data-ttu-id="15db0-129">LOCALDB_ERROR_VERSION_REQUESTED_NOT_INSTALLED</span><span class="sxs-lookup"><span data-stu-id="15db0-129">LOCALDB_ERROR_VERSION_REQUESTED_NOT_INSTALLED</span></span>](../express-localdb-error-messages/localdb-error-version-requested-not-installed.md)  
 <span data-ttu-id="15db0-130">指定したパッチ レベルはインストールされていません。</span><span class="sxs-lookup"><span data-stu-id="15db0-130">The specified patch level is not installed.</span></span>  
  
 [<span data-ttu-id="15db0-131">LOCALDB_ERROR_CANNOT_CREATE_INSTANCE_FOLDER</span><span class="sxs-lookup"><span data-stu-id="15db0-131">LOCALDB_ERROR_CANNOT_CREATE_INSTANCE_FOLDER</span></span>](../express-localdb-error-messages/localdb-error-cannot-create-instance-folder.md)  
 <span data-ttu-id="15db0-132">%userprofile% の下にはフォルダーを作成できません。</span><span class="sxs-lookup"><span data-stu-id="15db0-132">A folder cannot be created under %userprofile%.</span></span>  
  
 [<span data-ttu-id="15db0-133">LOCALDB_ERROR_CANNOT_GET_USER_PROFILE_FOLDER</span><span class="sxs-lookup"><span data-stu-id="15db0-133">LOCALDB_ERROR_CANNOT_GET_USER_PROFILE_FOLDER</span></span>](../express-localdb-error-messages/localdb-error-cannot-get-user-profile-folder.md)  
 <span data-ttu-id="15db0-134">ユーザー プロファイル フォルダーを取得できません。</span><span class="sxs-lookup"><span data-stu-id="15db0-134">A user profile folder cannot be retrieved.</span></span>  
  
 [<span data-ttu-id="15db0-135">LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_FOLDER</span><span class="sxs-lookup"><span data-stu-id="15db0-135">LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_FOLDER</span></span>](../express-localdb-error-messages/localdb-error-cannot-access-instance-folder.md)  
 <span data-ttu-id="15db0-136">インスタンス フォルダーにアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="15db0-136">An instance folder cannot be accessed.</span></span>  
  
 [<span data-ttu-id="15db0-137">LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_REGISTRY</span><span class="sxs-lookup"><span data-stu-id="15db0-137">LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_REGISTRY</span></span>](../express-localdb-error-messages/localdb-error-cannot-access-instance-registry.md)  
 <span data-ttu-id="15db0-138">インスタンス レジストリにアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="15db0-138">An instance registry cannot be accessed.</span></span>  
  
 [<span data-ttu-id="15db0-139">LOCALDB_ERROR_CANNOT_MODIFY_INSTANCE_REGISTRY</span><span class="sxs-lookup"><span data-stu-id="15db0-139">LOCALDB_ERROR_CANNOT_MODIFY_INSTANCE_REGISTRY</span></span>](../express-localdb-error-messages/localdb-error-cannot-modify-instance-registry.md)  
 <span data-ttu-id="15db0-140">インスタンス レジストリを変更できません。</span><span class="sxs-lookup"><span data-stu-id="15db0-140">An instance registry cannot be modified.</span></span>  
  
 [<span data-ttu-id="15db0-141">LOCALDB_ERROR_SQL_SERVER_STARTUP_FAILED</span><span class="sxs-lookup"><span data-stu-id="15db0-141">LOCALDB_ERROR_SQL_SERVER_STARTUP_FAILED</span></span>](../express-localdb-error-messages/localdb-error-sql-server-startup-failed.md)  
 <span data-ttu-id="15db0-142">SQL Server プロセスが開始されましたが、SQL Server の起動に失敗しました。</span><span class="sxs-lookup"><span data-stu-id="15db0-142">A SQL Server process is started but SQL Server startup failed.</span></span>  
  
 [<span data-ttu-id="15db0-143">LOCALDB_ERROR_INSTANCE_CONFIGURATION_CORRUPT</span><span class="sxs-lookup"><span data-stu-id="15db0-143">LOCALDB_ERROR_INSTANCE_CONFIGURATION_CORRUPT</span></span>](../express-localdb-error-messages/localdb-error-instance-configuration-corrupt.md)  
 <span data-ttu-id="15db0-144">インスタンス構成が破損しています。</span><span class="sxs-lookup"><span data-stu-id="15db0-144">An instance configuration is corrupted.</span></span>  
  
 [<span data-ttu-id="15db0-145">LOCALDB_ERROR_INTERNAL_ERROR</span><span class="sxs-lookup"><span data-stu-id="15db0-145">LOCALDB_ERROR_INTERNAL_ERROR</span></span>](../express-localdb-error-messages/localdb-error-internal-error.md)  
 <span data-ttu-id="15db0-146">予期しないエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="15db0-146">An unexpected error occurred.</span></span> <span data-ttu-id="15db0-147">詳細をイベント ログで確認してください。</span><span class="sxs-lookup"><span data-stu-id="15db0-147">See the event log for details.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="15db0-148">解説</span><span class="sxs-lookup"><span data-stu-id="15db0-148">Remarks</span></span>  
 <span data-ttu-id="15db0-149">指定の名前を持つ完全に機能する LocalDB インスタンスが既にあり、そのバージョンが要求されたバージョン以上である場合、結果は S_OK です。</span><span class="sxs-lookup"><span data-stu-id="15db0-149">If a fully functional LocalDB instance with the specified name already exists and its version is equal to or higher than requested, the result is S_OK.</span></span>  
  
 <span data-ttu-id="15db0-150">既存のインスタンスが破損した場合、`LocalDBCreateInstance` API メソッドのそれ以降の呼び出しは失敗します。</span><span class="sxs-lookup"><span data-stu-id="15db0-150">In cases when an existing instance becomes corrupted, subsequent calls to the `LocalDBCreateInstance` API method will fail.</span></span> <span data-ttu-id="15db0-151">破損したインスタンスは、手動で修正するか明示的に削除しないと、再度使用できるようになりません。</span><span class="sxs-lookup"><span data-stu-id="15db0-151">Corrupted instances must be fixed manually or explicitly deleted before they can be used again.</span></span>  
  
 <span data-ttu-id="15db0-152">LocalDB API を使用するコードサンプルについては、 [Localdb リファレンスの SQL Server Express](../sql-server-express-localdb-reference.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="15db0-152">For a code sample that uses LocalDB API, see [SQL Server Express LocalDB Reference](../sql-server-express-localdb-reference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15db0-153">参照</span><span class="sxs-lookup"><span data-stu-id="15db0-153">See Also</span></span>  
 [<span data-ttu-id="15db0-154">SQL Server Express LocalDB ヘッダーとバージョン情報</span><span class="sxs-lookup"><span data-stu-id="15db0-154">SQL Server Express LocalDB Header and Version Information</span></span>](sql-server-express-localdb-header-and-version-information.md)  
  
  
