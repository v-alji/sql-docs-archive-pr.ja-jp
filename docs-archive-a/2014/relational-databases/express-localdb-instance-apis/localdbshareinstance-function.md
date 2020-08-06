---
title: Localdbのインスタンス関数 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
api_name:
- LocalDBShareInstance
api_location:
- sqluserinstance.dll
topic_type:
- apiref
ms.assetid: 21eb3b9a-7d32-455b-89bb-f624198cd202
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 238bff0b3512ceb03ead186dc001165274bd4e30
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639963"
---
# <a name="localdbshareinstance-function"></a><span data-ttu-id="26e9e-102">LocalDBShareInstance 関数</span><span class="sxs-lookup"><span data-stu-id="26e9e-102">LocalDBShareInstance Function</span></span>
  <span data-ttu-id="26e9e-103">指定した共有名を使用して、指定した SQL Server Express LocalDB インスタンスをコンピューターの他のユーザーと共有します。</span><span class="sxs-lookup"><span data-stu-id="26e9e-103">Shares the specified SQL Server Express LocalDB instance with other users of the computer, using the specified shared name.</span></span>  
  
 <span data-ttu-id="26e9e-104">**ヘッダーファイル:** sqlncli</span><span class="sxs-lookup"><span data-stu-id="26e9e-104">**Header file:** sqlncli.h</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26e9e-105">構文</span><span class="sxs-lookup"><span data-stu-id="26e9e-105">Syntax</span></span>  
  
```  
HRESULT LocalDBShareInstance(  
           PSID pOwnerSID,  
           PCWSTR pInstancePrivateName,  
           PCWSTR pInstanceSharedName,   
           DWORD dwFlags   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="26e9e-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="26e9e-106">Parameters</span></span>  
 <span data-ttu-id="26e9e-107">*pOwnerSID*</span><span class="sxs-lookup"><span data-stu-id="26e9e-107">*pOwnerSID*</span></span>  
 <span data-ttu-id="26e9e-108">[入力] インスタンスの所有者の SID。</span><span class="sxs-lookup"><span data-stu-id="26e9e-108">[Input] The SID of the instance owner.</span></span>  
  
 <span data-ttu-id="26e9e-109">*pInstancePrivateName*</span><span class="sxs-lookup"><span data-stu-id="26e9e-109">*pInstancePrivateName*</span></span>  
 <span data-ttu-id="26e9e-110">[入力] 共有する LocalDB インスタンスのプライベート名。</span><span class="sxs-lookup"><span data-stu-id="26e9e-110">[Input] The private name for the LocalDB instance to share.</span></span>  
  
 <span data-ttu-id="26e9e-111">*pInstanceSharedName*</span><span class="sxs-lookup"><span data-stu-id="26e9e-111">*pInstanceSharedName*</span></span>  
 <span data-ttu-id="26e9e-112">[入力] 共有する LocalDB インスタンスの共有名。</span><span class="sxs-lookup"><span data-stu-id="26e9e-112">[Input] The shared name for the LocalDB instance to share.</span></span>  
  
 <span data-ttu-id="26e9e-113">*dwFlags*</span><span class="sxs-lookup"><span data-stu-id="26e9e-113">*dwFlags*</span></span>  
 <span data-ttu-id="26e9e-114">[入力] 将来の使用のために予約されています。</span><span class="sxs-lookup"><span data-stu-id="26e9e-114">[Input] Reserved for future use.</span></span> <span data-ttu-id="26e9e-115">現時点では、0 に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="26e9e-115">Currently should be set to 0.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="26e9e-116">戻り値</span><span class="sxs-lookup"><span data-stu-id="26e9e-116">Returns</span></span>  
 <span data-ttu-id="26e9e-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="26e9e-117">S_OK</span></span>  
 <span data-ttu-id="26e9e-118">関数が正常に実行されました。</span><span class="sxs-lookup"><span data-stu-id="26e9e-118">The function succeeded.</span></span>  
  
 [<span data-ttu-id="26e9e-119">LOCALDB_ERROR_NOT_INSTALLED</span><span class="sxs-lookup"><span data-stu-id="26e9e-119">LOCALDB_ERROR_NOT_INSTALLED</span></span>](../express-localdb-error-messages/localdb-error-not-installed.md)  
 <span data-ttu-id="26e9e-120">SQL Server Express LocalDB は、コンピューターにインストールされていません。</span><span class="sxs-lookup"><span data-stu-id="26e9e-120">SQL Server Express LocalDB is not installed on the computer.</span></span>  
  
 [<span data-ttu-id="26e9e-121">LOCALDB_ERROR_INVALID_PARAMETER</span><span class="sxs-lookup"><span data-stu-id="26e9e-121">LOCALDB_ERROR_INVALID_PARAMETER</span></span>](../express-localdb-error-messages/localdb-error-invalid-parameter.md)  
 <span data-ttu-id="26e9e-122">指定した 1 つまたは複数の入力パラメーターが無効です。</span><span class="sxs-lookup"><span data-stu-id="26e9e-122">One or more specified input parameters are invalid.</span></span>  
  
 [<span data-ttu-id="26e9e-123">LOCALDB_ERROR_INVALID_INSTANCE_NAME</span><span class="sxs-lookup"><span data-stu-id="26e9e-123">LOCALDB_ERROR_INVALID_INSTANCE_NAME</span></span>](../express-localdb-error-messages/localdb-error-invalid-instance-name.md)  
 <span data-ttu-id="26e9e-124">指定したインスタンス名は無効です。</span><span class="sxs-lookup"><span data-stu-id="26e9e-124">The specified instance name is invalid.</span></span>  
  
 [<span data-ttu-id="26e9e-125">LOCALDB_ERROR_UNKNOWN_INSTANCE</span><span class="sxs-lookup"><span data-stu-id="26e9e-125">LOCALDB_ERROR_UNKNOWN_INSTANCE</span></span>](../express-localdb-error-messages/localdb-error-unknown-instance.md)  
 <span data-ttu-id="26e9e-126">指定したインスタンスは存在しません。</span><span class="sxs-lookup"><span data-stu-id="26e9e-126">The specified instance does not exist.</span></span>  
  
 [<span data-ttu-id="26e9e-127">LOCALDB_ERROR_ADMIN_RIGHTS_REQUIRED</span><span class="sxs-lookup"><span data-stu-id="26e9e-127">LOCALDB_ERROR_ADMIN_RIGHTS_REQUIRED</span></span>](../express-localdb-error-messages/localdb-error-admin-rights-required.md)  
 <span data-ttu-id="26e9e-128">この操作を実行するためには、管理者権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="26e9e-128">Administrator privileges are required in order to execute this operation.</span></span>  
  
 [<span data-ttu-id="26e9e-129">LOCALDB_ERROR_SHARED_NAME_TAKEN</span><span class="sxs-lookup"><span data-stu-id="26e9e-129">LOCALDB_ERROR_SHARED_NAME_TAKEN</span></span>](../express-localdb-error-messages/localdb-error-shared-name-taken.md)  
 <span data-ttu-id="26e9e-130">指定した共有名は既に使用されています。</span><span class="sxs-lookup"><span data-stu-id="26e9e-130">The specified shared name is already taken.</span></span>  
  
 [<span data-ttu-id="26e9e-131">LOCALDB_ERROR_INSTANCE_ALREADY_SHARED</span><span class="sxs-lookup"><span data-stu-id="26e9e-131">LOCALDB_ERROR_INSTANCE_ALREADY_SHARED</span></span>](../express-localdb-error-messages/localdb-error-instance-already-shared.md)  
 <span data-ttu-id="26e9e-132">指定したインスタンスは既に共有されています。</span><span class="sxs-lookup"><span data-stu-id="26e9e-132">The specified instance is already shared.</span></span>  
  
 [<span data-ttu-id="26e9e-133">LOCALDB_ERROR_INTERNAL_ERROR</span><span class="sxs-lookup"><span data-stu-id="26e9e-133">LOCALDB_ERROR_INTERNAL_ERROR</span></span>](../express-localdb-error-messages/localdb-error-internal-error.md)  
 <span data-ttu-id="26e9e-134">予期しないエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="26e9e-134">An unexpected error occurred.</span></span> <span data-ttu-id="26e9e-135">詳細をイベント ログで確認してください。</span><span class="sxs-lookup"><span data-stu-id="26e9e-135">See the event log for details.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="26e9e-136">解説</span><span class="sxs-lookup"><span data-stu-id="26e9e-136">Remarks</span></span>  
 <span data-ttu-id="26e9e-137">LocalDB API を使用するコードサンプルについては、 [Localdb リファレンスの SQL Server Express](../sql-server-express-localdb-reference.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="26e9e-137">For a code sample that uses LocalDB API, see [SQL Server Express LocalDB Reference](../sql-server-express-localdb-reference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26e9e-138">参照</span><span class="sxs-lookup"><span data-stu-id="26e9e-138">See Also</span></span>  
 [<span data-ttu-id="26e9e-139">SQL Server Express LocalDB ヘッダーとバージョン情報</span><span class="sxs-lookup"><span data-stu-id="26e9e-139">SQL Server Express LocalDB Header and Version Information</span></span>](sql-server-express-localdb-header-and-version-information.md)  
  
  
