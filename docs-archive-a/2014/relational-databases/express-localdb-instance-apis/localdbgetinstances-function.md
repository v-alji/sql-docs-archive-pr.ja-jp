---
title: LocalDBGetInstances 関数 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
api_name:
- LocalDBGetInstances
api_location:
- sqluserinstance.dll
topic_type:
- apiref
ms.assetid: f95a9980-8bc0-426c-8aa1-e2660b6784cf
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 4a6f758bd647fd69a14f72a0651bb3e2e33a7c79
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711937"
---
# <a name="localdbgetinstances-function"></a><span data-ttu-id="dfdf3-102">LocalDBGetInstances 関数</span><span class="sxs-lookup"><span data-stu-id="dfdf3-102">LocalDBGetInstances Function</span></span>
  <span data-ttu-id="dfdf3-103">指定したバージョンのすべての SQL Server Express LocalDB インスタンスを返します。</span><span class="sxs-lookup"><span data-stu-id="dfdf3-103">Returns all SQL Server Express LocalDB instances with the given version.</span></span>  
  
 <span data-ttu-id="dfdf3-104">**ヘッダーファイル:** sqlncli</span><span class="sxs-lookup"><span data-stu-id="dfdf3-104">**Header file:** sqlncli.h</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dfdf3-105">構文</span><span class="sxs-lookup"><span data-stu-id="dfdf3-105">Syntax</span></span>  
  
```  
#define MAX_LOCALDB_INSTANCE_NAME_LENGTH 128typedef WCHAR TLocalDBInstanceName[MAX_LOCALDB_INSTANCE_NAME_LENGTH + 1];typedef TLocalDBInstanceName* PTLocalDBInstanceName;  
HRESULT LocalDBGetInstances(  
           PTLocalDBInstanceName pInstanceNames,  
           LPDWORD lpdwNumberOfInstances  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dfdf3-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="dfdf3-106">Parameters</span></span>  
 <span data-ttu-id="dfdf3-107">*pInstanceNames*</span><span class="sxs-lookup"><span data-stu-id="dfdf3-107">*pInstanceNames*</span></span>  
 <span data-ttu-id="dfdf3-108">Outputこの関数から制御が戻るときに、ユーザーのワークステーション上の名前付き LocalDB インスタンスと既定の LocalDB インスタンスの両方の名前が含まれています。</span><span class="sxs-lookup"><span data-stu-id="dfdf3-108">[Output] When this function returns, contains the names of both named and default LocalDB instances on the user's workstation.</span></span>  
  
 <span data-ttu-id="dfdf3-109">*lpdwNumberOfInstances*</span><span class="sxs-lookup"><span data-stu-id="dfdf3-109">*lpdwNumberOfInstances*</span></span>  
 <span data-ttu-id="dfdf3-110">[入力/出力]入力時には、 *pInstanceNames*バッファー内のインスタンス名のスロット数が格納されます。</span><span class="sxs-lookup"><span data-stu-id="dfdf3-110">[Input/Output] On input, contains the number of slots for instance names in the *pInstanceNames* buffer.</span></span> <span data-ttu-id="dfdf3-111">出力時には、ユーザーのワークステーションで見つかった LocalDB インスタンスの数が含まれます。</span><span class="sxs-lookup"><span data-stu-id="dfdf3-111">On output, contains the number of LocalDB instances found on the user's workstation.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="dfdf3-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="dfdf3-112">Returns</span></span>  
 <span data-ttu-id="dfdf3-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="dfdf3-113">S_OK</span></span>  
 <span data-ttu-id="dfdf3-114">関数が正常に実行されました。</span><span class="sxs-lookup"><span data-stu-id="dfdf3-114">The function succeeded.</span></span>  
  
 [<span data-ttu-id="dfdf3-115">LOCALDB_ERROR_NOT_INSTALLED</span><span class="sxs-lookup"><span data-stu-id="dfdf3-115">LOCALDB_ERROR_NOT_INSTALLED</span></span>](../express-localdb-error-messages/localdb-error-not-installed.md)  
 <span data-ttu-id="dfdf3-116">SQL Server Express LocalDB は、コンピューターにインストールされていません。</span><span class="sxs-lookup"><span data-stu-id="dfdf3-116">SQL Server Express LocalDB is not installed on the computer.</span></span>  
  
 [<span data-ttu-id="dfdf3-117">LOCALDB_ERROR_INVALID_PARAMETER</span><span class="sxs-lookup"><span data-stu-id="dfdf3-117">LOCALDB_ERROR_INVALID_PARAMETER</span></span>](../express-localdb-error-messages/localdb-error-invalid-parameter.md)  
 <span data-ttu-id="dfdf3-118">指定した 1 つまたは複数の入力パラメーターが無効です。</span><span class="sxs-lookup"><span data-stu-id="dfdf3-118">One or more specified input parameters are invalid.</span></span>  
  
 [<span data-ttu-id="dfdf3-119">LOCALDB_ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="dfdf3-119">LOCALDB_ERROR_INSUFFICIENT_BUFFER</span></span>](../express-localdb-error-messages/localdb-error-insufficient-buffer.md)  
 <span data-ttu-id="dfdf3-120">入力バッファーが短かすぎますが、切り捨ては要求されませんでした。</span><span class="sxs-lookup"><span data-stu-id="dfdf3-120">The input buffer is too short, and truncation was not requested.</span></span>  
  
 [<span data-ttu-id="dfdf3-121">LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG</span><span class="sxs-lookup"><span data-stu-id="dfdf3-121">LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG</span></span>](../express-localdb-error-messages/localdb-error-instance-folder-path-too-long.md)  
 <span data-ttu-id="dfdf3-122">インスタンスを格納するパスの長さが MAX_PATH を超過しています。</span><span class="sxs-lookup"><span data-stu-id="dfdf3-122">The path where the instance should be stored is longer than MAX_PATH.</span></span>  
  
 [<span data-ttu-id="dfdf3-123">LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_REGISTRY</span><span class="sxs-lookup"><span data-stu-id="dfdf3-123">LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_REGISTRY</span></span>](../express-localdb-error-messages/localdb-error-cannot-access-instance-registry.md)  
 <span data-ttu-id="dfdf3-124">インスタンス レジストリにアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="dfdf3-124">An instance registry cannot be accessed.</span></span>  
  
 [<span data-ttu-id="dfdf3-125">LOCALDB_ERROR_INSTANCE_CONFIGURATION_CORRUPT</span><span class="sxs-lookup"><span data-stu-id="dfdf3-125">LOCALDB_ERROR_INSTANCE_CONFIGURATION_CORRUPT</span></span>](../express-localdb-error-messages/localdb-error-instance-configuration-corrupt.md)  
 <span data-ttu-id="dfdf3-126">インスタンス構成が破損しています。</span><span class="sxs-lookup"><span data-stu-id="dfdf3-126">An instance configuration is corrupted.</span></span>  
  
 [<span data-ttu-id="dfdf3-127">LOCALDB_ERROR_INTERNAL_ERROR</span><span class="sxs-lookup"><span data-stu-id="dfdf3-127">LOCALDB_ERROR_INTERNAL_ERROR</span></span>](../express-localdb-error-messages/localdb-error-internal-error.md)  
 <span data-ttu-id="dfdf3-128">予期しないエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="dfdf3-128">An unexpected error occurred.</span></span> <span data-ttu-id="dfdf3-129">詳細をイベント ログで確認してください。</span><span class="sxs-lookup"><span data-stu-id="dfdf3-129">See the event log for details.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dfdf3-130">解説</span><span class="sxs-lookup"><span data-stu-id="dfdf3-130">Remarks</span></span>  
 <span data-ttu-id="dfdf3-131">LocalDB API を使用するコードサンプルについては、 [Localdb リファレンスの SQL Server Express](../sql-server-express-localdb-reference.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dfdf3-131">For a code sample that uses LocalDB API, see [SQL Server Express LocalDB Reference](../sql-server-express-localdb-reference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfdf3-132">参照</span><span class="sxs-lookup"><span data-stu-id="dfdf3-132">See Also</span></span>  
 [<span data-ttu-id="dfdf3-133">SQL Server Express LocalDB ヘッダーとバージョン情報</span><span class="sxs-lookup"><span data-stu-id="dfdf3-133">SQL Server Express LocalDB Header and Version Information</span></span>](sql-server-express-localdb-header-and-version-information.md)  
  
  
