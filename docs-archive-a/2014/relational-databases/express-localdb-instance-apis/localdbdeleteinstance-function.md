---
title: LocalDBDeleteInstance 関数 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
api_name:
- LocalDBDeleteInstance
api_location:
- sqluserinstance.dll
topic_type:
- apiref
ms.assetid: 37cb2a7e-672a-4223-b6f3-a94d7b8d58cd
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 8d4c873e045c5effed476ca9d147270d159ec3b2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643367"
---
# <a name="localdbdeleteinstance-function"></a><span data-ttu-id="1580a-102">LocalDBDeleteInstance 関数</span><span class="sxs-lookup"><span data-stu-id="1580a-102">LocalDBDeleteInstance Function</span></span>
  <span data-ttu-id="1580a-103">指定した SQL Server Express LocalDB インスタンスを削除します。</span><span class="sxs-lookup"><span data-stu-id="1580a-103">Removes the specified SQL Server Express LocalDB instance.</span></span>  
  
 <span data-ttu-id="1580a-104">**ヘッダーファイル:** sqlncli</span><span class="sxs-lookup"><span data-stu-id="1580a-104">**Header file:** sqlncli.h</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1580a-105">構文</span><span class="sxs-lookup"><span data-stu-id="1580a-105">Syntax</span></span>  
  
```  
HRESULT LocalDBDeleteInstance(  
           PCWSTR pInstanceName,  
           DWORD dwFlags   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1580a-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1580a-106">Parameters</span></span>  
 <span data-ttu-id="1580a-107">*pInstanceName*</span><span class="sxs-lookup"><span data-stu-id="1580a-107">*pInstanceName*</span></span>  
 <span data-ttu-id="1580a-108">[入力] 削除する LocalDB インスタンスの名前。</span><span class="sxs-lookup"><span data-stu-id="1580a-108">[Input] The name of the LocalDB instance to remove.</span></span>  
  
 <span data-ttu-id="1580a-109">*dwFlags*</span><span class="sxs-lookup"><span data-stu-id="1580a-109">*dwFlags*</span></span>  
 <span data-ttu-id="1580a-110">[入力] 将来の使用のために予約されています。</span><span class="sxs-lookup"><span data-stu-id="1580a-110">[Input] Reserved for future use.</span></span> <span data-ttu-id="1580a-111">現時点では、0 に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1580a-111">Currently should be set to 0.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="1580a-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="1580a-112">Returns</span></span>  
 <span data-ttu-id="1580a-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="1580a-113">S_OK</span></span>  
 <span data-ttu-id="1580a-114">関数が正常に実行されました。</span><span class="sxs-lookup"><span data-stu-id="1580a-114">The function succeeded.</span></span>  
  
 [<span data-ttu-id="1580a-115">LOCALDB_ERROR_NOT_INSTALLED</span><span class="sxs-lookup"><span data-stu-id="1580a-115">LOCALDB_ERROR_NOT_INSTALLED</span></span>](../express-localdb-error-messages/localdb-error-not-installed.md)  
 <span data-ttu-id="1580a-116">SQL Server Express LocalDB は、コンピューターにインストールされていません。</span><span class="sxs-lookup"><span data-stu-id="1580a-116">SQL Server Express LocalDB is not installed on the computer.</span></span>  
  
 [<span data-ttu-id="1580a-117">LOCALDB_ERROR_INVALID_PARAMETER</span><span class="sxs-lookup"><span data-stu-id="1580a-117">LOCALDB_ERROR_INVALID_PARAMETER</span></span>](../express-localdb-error-messages/localdb-error-invalid-parameter.md)  
 <span data-ttu-id="1580a-118">指定した 1 つまたは複数の入力パラメーターが無効です。</span><span class="sxs-lookup"><span data-stu-id="1580a-118">One or more specified input parameters are invalid.</span></span>  
  
 [<span data-ttu-id="1580a-119">LOCALDB_ERROR_INVALID_INSTANCE_NAME</span><span class="sxs-lookup"><span data-stu-id="1580a-119">LOCALDB_ERROR_INVALID_INSTANCE_NAME</span></span>](../express-localdb-error-messages/localdb-error-invalid-instance-name.md)  
 <span data-ttu-id="1580a-120">指定したインスタンス名は無効です。</span><span class="sxs-lookup"><span data-stu-id="1580a-120">The specified instance name is invalid.</span></span>  
  
 [<span data-ttu-id="1580a-121">LOCALDB_ERROR_UNKNOWN_INSTANCE</span><span class="sxs-lookup"><span data-stu-id="1580a-121">LOCALDB_ERROR_UNKNOWN_INSTANCE</span></span>](../express-localdb-error-messages/localdb-error-unknown-instance.md)  
 <span data-ttu-id="1580a-122">指定したインスタンスは存在しません。</span><span class="sxs-lookup"><span data-stu-id="1580a-122">The specified instance does not exist.</span></span>  
  
 [<span data-ttu-id="1580a-123">LOCALDB_ERROR_INSTANCE_BUSY</span><span class="sxs-lookup"><span data-stu-id="1580a-123">LOCALDB_ERROR_INSTANCE_BUSY</span></span>](../express-localdb-error-messages/localdb-error-instance-busy.md)  
 <span data-ttu-id="1580a-124">指定したインスタンスは実行中です。</span><span class="sxs-lookup"><span data-stu-id="1580a-124">The specified instance is running.</span></span>  
  
 [<span data-ttu-id="1580a-125">LOCALDB_ERROR_WAIT_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1580a-125">LOCALDB_ERROR_WAIT_TIMEOUT</span></span>](../express-localdb-error-messages/localdb-error-wait-timeout.md)  
 <span data-ttu-id="1580a-126">同期ロックを取得しようとしている間にタイムアウトが発生しました。</span><span class="sxs-lookup"><span data-stu-id="1580a-126">A time-out occurred while trying to acquire synchronization locks.</span></span>  
  
 [<span data-ttu-id="1580a-127">LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG</span><span class="sxs-lookup"><span data-stu-id="1580a-127">LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG</span></span>](../express-localdb-error-messages/localdb-error-instance-folder-path-too-long.md)  
 <span data-ttu-id="1580a-128">インスタンスを格納するパスの長さが MAX_PATH を超過しています。</span><span class="sxs-lookup"><span data-stu-id="1580a-128">The path where the instance should be stored is longer than MAX_PATH.</span></span>  
  
 [<span data-ttu-id="1580a-129">LOCALDB_ERROR_CANNOT_GET_USER_PROFILE_FOLDER</span><span class="sxs-lookup"><span data-stu-id="1580a-129">LOCALDB_ERROR_CANNOT_GET_USER_PROFILE_FOLDER</span></span>](../express-localdb-error-messages/localdb-error-cannot-get-user-profile-folder.md)  
 <span data-ttu-id="1580a-130">ユーザー プロファイル フォルダーを取得できません。</span><span class="sxs-lookup"><span data-stu-id="1580a-130">A user profile folder cannot be retrieved.</span></span>  
  
 [<span data-ttu-id="1580a-131">LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_FOLDER</span><span class="sxs-lookup"><span data-stu-id="1580a-131">LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_FOLDER</span></span>](../express-localdb-error-messages/localdb-error-cannot-access-instance-folder.md)  
 <span data-ttu-id="1580a-132">インスタンス フォルダーにアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="1580a-132">An instance folder cannot be accessed.</span></span>  
  
 [<span data-ttu-id="1580a-133">LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_REGISTRY</span><span class="sxs-lookup"><span data-stu-id="1580a-133">LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_REGISTRY</span></span>](../express-localdb-error-messages/localdb-error-cannot-access-instance-registry.md)  
 <span data-ttu-id="1580a-134">インスタンス レジストリにアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="1580a-134">An instance registry cannot be accessed.</span></span>  
  
 [<span data-ttu-id="1580a-135">LOCALDB_ERROR_CANNOT_MODIFY_INSTANCE_REGISTRY</span><span class="sxs-lookup"><span data-stu-id="1580a-135">LOCALDB_ERROR_CANNOT_MODIFY_INSTANCE_REGISTRY</span></span>](../express-localdb-error-messages/localdb-error-cannot-modify-instance-registry.md)  
 <span data-ttu-id="1580a-136">インスタンス レジストリを変更できません。</span><span class="sxs-lookup"><span data-stu-id="1580a-136">An instance registry cannot be modified.</span></span>  
  
 [<span data-ttu-id="1580a-137">LOCALDB_ERROR_INSTANCE_CONFIGURATION_CORRUPT</span><span class="sxs-lookup"><span data-stu-id="1580a-137">LOCALDB_ERROR_INSTANCE_CONFIGURATION_CORRUPT</span></span>](../express-localdb-error-messages/localdb-error-instance-configuration-corrupt.md)  
 <span data-ttu-id="1580a-138">インスタンス構成が破損しています。</span><span class="sxs-lookup"><span data-stu-id="1580a-138">An instance configuration is corrupted.</span></span>  
  
 [<span data-ttu-id="1580a-139">LOCALDB_ERROR_CALLER_IS_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1580a-139">LOCALDB_ERROR_CALLER_IS_NOT_OWNER</span></span>](../express-localdb-error-messages/localdb-error-caller-is-not-owner.md)  
 <span data-ttu-id="1580a-140">API 呼び出し元は、ローカル データベース インスタンスの所有者ではありません。</span><span class="sxs-lookup"><span data-stu-id="1580a-140">API caller is not Local Database instance owner.</span></span>  
  
 [<span data-ttu-id="1580a-141">LOCALDB_ERROR_INTERNAL_ERROR</span><span class="sxs-lookup"><span data-stu-id="1580a-141">LOCALDB_ERROR_INTERNAL_ERROR</span></span>](../express-localdb-error-messages/localdb-error-internal-error.md)  
 <span data-ttu-id="1580a-142">予期しないエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="1580a-142">An unexpected error occurred.</span></span> <span data-ttu-id="1580a-143">詳細をイベント ログで確認してください。</span><span class="sxs-lookup"><span data-stu-id="1580a-143">See the event log for details.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1580a-144">解説</span><span class="sxs-lookup"><span data-stu-id="1580a-144">Remarks</span></span>  
 <span data-ttu-id="1580a-145">LocalDB API を使用するコードサンプルについては、 [Localdb リファレンスの SQL Server Express](../sql-server-express-localdb-reference.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1580a-145">For a code sample that uses LocalDB API, see [SQL Server Express LocalDB Reference](../sql-server-express-localdb-reference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1580a-146">参照</span><span class="sxs-lookup"><span data-stu-id="1580a-146">See Also</span></span>  
 [<span data-ttu-id="1580a-147">SQL Server Express LocalDB ヘッダーとバージョン情報</span><span class="sxs-lookup"><span data-stu-id="1580a-147">SQL Server Express LocalDB Header and Version Information</span></span>](sql-server-express-localdb-header-and-version-information.md)  
  
  
