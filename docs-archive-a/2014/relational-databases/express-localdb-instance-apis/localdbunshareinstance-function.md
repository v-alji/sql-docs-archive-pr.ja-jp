---
title: Localdbunのインスタンス関数 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
api_name:
- LocalDBUnshareInstance
api_location:
- sqluserinstance.dll
topic_type:
- apiref
ms.assetid: 54012ccb-eded-43f7-8ea5-da5ce79224c6
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 77ebf8cad9d410b047fccede4360ca0041637986
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632484"
---
# <a name="localdbunshareinstance-function"></a><span data-ttu-id="169ad-102">LocalDBUnshareInstance 関数</span><span class="sxs-lookup"><span data-stu-id="169ad-102">LocalDBUnshareInstance Function</span></span>
  <span data-ttu-id="169ad-103">指定した SQL Server Express LocalDB インスタンスの共有を停止します。</span><span class="sxs-lookup"><span data-stu-id="169ad-103">Stops the sharing of the specified SQL Server Express LocalDB instance.</span></span>  
  
 <span data-ttu-id="169ad-104">**ヘッダーファイル:** sqlncli</span><span class="sxs-lookup"><span data-stu-id="169ad-104">**Header file:** sqlncli.h</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="169ad-105">構文</span><span class="sxs-lookup"><span data-stu-id="169ad-105">Syntax</span></span>  
  
```  
HRESULT LocalDBUnShareInstance(  
           PCWSTR pInstanceSharedName,   
           DWORD dwFlags   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="169ad-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="169ad-106">Parameters</span></span>  
 <span data-ttu-id="169ad-107">*pInstanceSharedName*</span><span class="sxs-lookup"><span data-stu-id="169ad-107">*pInstanceSharedName*</span></span>  
 <span data-ttu-id="169ad-108">[入力] 共有を解除する LocalDB インスタンスの共有名。</span><span class="sxs-lookup"><span data-stu-id="169ad-108">[Input] The shared name for the LocalDB instance to unshare.</span></span>  
  
 <span data-ttu-id="169ad-109">*dwFlags*</span><span class="sxs-lookup"><span data-stu-id="169ad-109">*dwFlags*</span></span>  
 <span data-ttu-id="169ad-110">[入力] 将来の使用のために予約されています。</span><span class="sxs-lookup"><span data-stu-id="169ad-110">[Input] Reserved for future use.</span></span> <span data-ttu-id="169ad-111">現時点では、0 に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="169ad-111">Currently should be set to 0.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="169ad-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="169ad-112">Returns</span></span>  
 <span data-ttu-id="169ad-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="169ad-113">S_OK</span></span>  
 <span data-ttu-id="169ad-114">関数が正常に実行されました。</span><span class="sxs-lookup"><span data-stu-id="169ad-114">The function succeeded.</span></span>  
  
 [<span data-ttu-id="169ad-115">LOCALDB_ERROR_NOT_INSTALLED</span><span class="sxs-lookup"><span data-stu-id="169ad-115">LOCALDB_ERROR_NOT_INSTALLED</span></span>](../express-localdb-error-messages/localdb-error-not-installed.md)  
 <span data-ttu-id="169ad-116">SQL Server Express LocalDB は、コンピューターにインストールされていません。</span><span class="sxs-lookup"><span data-stu-id="169ad-116">SQL Server Express LocalDB is not installed on the computer.</span></span>  
  
 [<span data-ttu-id="169ad-117">LOCALDB_ERROR_INVALID_PARAMETER</span><span class="sxs-lookup"><span data-stu-id="169ad-117">LOCALDB_ERROR_INVALID_PARAMETER</span></span>](../express-localdb-error-messages/localdb-error-invalid-parameter.md)  
 <span data-ttu-id="169ad-118">指定した 1 つまたは複数の入力パラメーターが無効です。</span><span class="sxs-lookup"><span data-stu-id="169ad-118">One or more specified input parameters are invalid.</span></span>  
  
 [<span data-ttu-id="169ad-119">LOCALDB_ERROR_INVALID_INSTANCE_NAME</span><span class="sxs-lookup"><span data-stu-id="169ad-119">LOCALDB_ERROR_INVALID_INSTANCE_NAME</span></span>](../express-localdb-error-messages/localdb-error-invalid-instance-name.md)  
 <span data-ttu-id="169ad-120">指定したインスタンス名は無効です。</span><span class="sxs-lookup"><span data-stu-id="169ad-120">The specified instance name is invalid.</span></span>  
  
 [<span data-ttu-id="169ad-121">LOCALDB_ERROR_UNKNOWN_INSTANCE</span><span class="sxs-lookup"><span data-stu-id="169ad-121">LOCALDB_ERROR_UNKNOWN_INSTANCE</span></span>](../express-localdb-error-messages/localdb-error-unknown-instance.md)  
 <span data-ttu-id="169ad-122">指定したインスタンスは存在しません。</span><span class="sxs-lookup"><span data-stu-id="169ad-122">The specified instance does not exist.</span></span>  
  
 [<span data-ttu-id="169ad-123">LOCALDB_ERROR_ADMIN_RIGHTS_REQUIRED</span><span class="sxs-lookup"><span data-stu-id="169ad-123">LOCALDB_ERROR_ADMIN_RIGHTS_REQUIRED</span></span>](../express-localdb-error-messages/localdb-error-admin-rights-required.md)  
 <span data-ttu-id="169ad-124">この操作を実行するためには、管理者権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="169ad-124">Administrator privileges are required in order to execute this operation.</span></span>  
  
 [<span data-ttu-id="169ad-125">LOCALDB_ERROR_INTERNAL_ERROR</span><span class="sxs-lookup"><span data-stu-id="169ad-125">LOCALDB_ERROR_INTERNAL_ERROR</span></span>](../express-localdb-error-messages/localdb-error-internal-error.md)  
 <span data-ttu-id="169ad-126">予期しないエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="169ad-126">An unexpected error occurred.</span></span> <span data-ttu-id="169ad-127">詳細をイベント ログで確認してください。</span><span class="sxs-lookup"><span data-stu-id="169ad-127">See the event log for details.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="169ad-128">解説</span><span class="sxs-lookup"><span data-stu-id="169ad-128">Remarks</span></span>  
 <span data-ttu-id="169ad-129">LocalDB API を使用するコードサンプルについては、 [Localdb リファレンスの SQL Server Express](../sql-server-express-localdb-reference.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="169ad-129">For a code sample that uses LocalDB API, see [SQL Server Express LocalDB Reference](../sql-server-express-localdb-reference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="169ad-130">参照</span><span class="sxs-lookup"><span data-stu-id="169ad-130">See Also</span></span>  
 [<span data-ttu-id="169ad-131">SQL Server Express LocalDB ヘッダーとバージョン情報</span><span class="sxs-lookup"><span data-stu-id="169ad-131">SQL Server Express LocalDB Header and Version Information</span></span>](sql-server-express-localdb-header-and-version-information.md)  
  
  
