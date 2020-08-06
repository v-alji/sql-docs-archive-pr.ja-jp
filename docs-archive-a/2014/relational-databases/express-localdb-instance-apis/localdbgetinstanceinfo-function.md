---
title: LocalDBGetInstanceInfo 関数 |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
api_name:
- LocalDBGetInstanceInfo
api_location:
- sqluserinstance.dll
topic_type:
- apiref
ms.assetid: 231706f5-26c6-42eb-ab47-315df6b8f824
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: dc7cbe2c59a7502a1fd0c8b4f92fb14e5defd50b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633856"
---
# <a name="localdbgetinstanceinfo-function"></a><span data-ttu-id="78b2b-102">LocalDBGetInstanceInfo 関数</span><span class="sxs-lookup"><span data-stu-id="78b2b-102">LocalDBGetInstanceInfo Function</span></span>
  <span data-ttu-id="78b2b-103">指定した SQL Server Express LocalDB インスタンスの情報を返します。たとえば、存在するかどうか、使用する LocalDB バージョン、実行中かどうかなどです。</span><span class="sxs-lookup"><span data-stu-id="78b2b-103">Returns information for the specified SQL Server Express LocalDB instance, such as whether it exists, the LocalDB version it uses, whether it is running, and so on.</span></span>  
  
 <span data-ttu-id="78b2b-104">この情報は、 `struct` 次の定義を持つ**Localdbinstanceinfo**という名前で返されます。</span><span class="sxs-lookup"><span data-stu-id="78b2b-104">The information is returned in a `struct` named **LocalDBInstanceInfo**, which has the following definition.</span></span>  
  
```  
typedef struct _LocalDBInstanceInfo  
{  
      // Contains the size of the LocalDBInstanceInfo struct  
      DWORD  cbLocalDBInstanceInfoSize;  
  
      // Holds the instance name  
      TLocalDBInstanceNamewszInstanceName;  
  
      // TRUE if the instance files exist on disk, FALSE otherwise  
      BOOL   bExists;  
  
      // TRUE if the instance configuration registry is corrupted, FALSE otherwise  
      BOOLbConfigurationCorrupted;  
  
      // TRUE if the instance is running at the moment, FALSE otherwise  
      BOOL   bIsRunning;  
  
      // Holds the LocalDB version for the instance in the format: major.minor.build.revision  
      DWORD  dwMajor;  
      DWORD  dwMinor;  
      DWORD  dwBuild;  
      DWORD  dwRevision;  
  
      // Holds the date and time when the instance was started for the last time  
      FILETIME ftLastStartUTC;  
  
      // Holds the name of the TDS named pipe to connect to the instance  
      WCHARwszConnection;  
  
      // TRUE if the instance is shared, FALSE otherwise  
      BOOLbIsShared;  
  
      // Holds the shared name for the instance (if the instance is shared)  
      TLocalDBInstanceNamewszSharedInstanceName;  
  
      // Holds the SID of the instance owner (if the instance is shared)  
      WCHARwszOwnerSID;   
  
      // TRUE if the instance is Automatic, FALSE otherwise  
      BOOLbIsAutomatic;  
} LocalDBInstanceInfo;  
  
```  
  
 <span data-ttu-id="78b2b-105">**ヘッダーファイル:** sqlncli</span><span class="sxs-lookup"><span data-stu-id="78b2b-105">**Header file:** sqlncli.h</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78b2b-106">構文</span><span class="sxs-lookup"><span data-stu-id="78b2b-106">Syntax</span></span>  
  
```  
HRESULT LocalDBGetInstanceInfo(  
           PCWSTR wszInstanceName,  
           PLocalDBInstanceInfo pInstanceInfo,  
           DWORD dwInstanceInfoSize   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="78b2b-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="78b2b-107">Parameters</span></span>  
 <span data-ttu-id="78b2b-108">*wszInstanceName*</span><span class="sxs-lookup"><span data-stu-id="78b2b-108">*wszInstanceName*</span></span>  
 <span data-ttu-id="78b2b-109">[入力] インスタンス名。</span><span class="sxs-lookup"><span data-stu-id="78b2b-109">[Input] The instance name.</span></span>  
  
 <span data-ttu-id="78b2b-110">*pInstanceInfo*</span><span class="sxs-lookup"><span data-stu-id="78b2b-110">*pInstanceInfo*</span></span>  
 <span data-ttu-id="78b2b-111">[出力] LocalDB インスタンスについての情報を格納するバッファー。</span><span class="sxs-lookup"><span data-stu-id="78b2b-111">[Output] The buffer to store the information about the LocalDB instance.</span></span>  
  
 <span data-ttu-id="78b2b-112">*dwInstanceInfoSize*</span><span class="sxs-lookup"><span data-stu-id="78b2b-112">*dwInstanceInfoSize*</span></span>  
 <span data-ttu-id="78b2b-113">代入*Instanceinfo*バッファーのサイズを保持します。</span><span class="sxs-lookup"><span data-stu-id="78b2b-113">[Input] Holds the size of the *InstanceInfo* buffer.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="78b2b-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="78b2b-114">Returns</span></span>  
 <span data-ttu-id="78b2b-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="78b2b-115">S_OK</span></span>  
 <span data-ttu-id="78b2b-116">関数が正常に実行されました。</span><span class="sxs-lookup"><span data-stu-id="78b2b-116">The function succeeded.</span></span>  
  
 [<span data-ttu-id="78b2b-117">LOCALDB_ERROR_NOT_INSTALLED</span><span class="sxs-lookup"><span data-stu-id="78b2b-117">LOCALDB_ERROR_NOT_INSTALLED</span></span>](../express-localdb-error-messages/localdb-error-not-installed.md)  
 <span data-ttu-id="78b2b-118">SQL Server Express LocalDB は、コンピューターにインストールされていません。</span><span class="sxs-lookup"><span data-stu-id="78b2b-118">SQL Server Express LocalDB is not installed on the computer.</span></span>  
  
 [<span data-ttu-id="78b2b-119">LOCALDB_ERROR_INVALID_PARAMETER</span><span class="sxs-lookup"><span data-stu-id="78b2b-119">LOCALDB_ERROR_INVALID_PARAMETER</span></span>](../express-localdb-error-messages/localdb-error-invalid-parameter.md)  
 <span data-ttu-id="78b2b-120">指定した 1 つまたは複数の入力パラメーターが無効です。</span><span class="sxs-lookup"><span data-stu-id="78b2b-120">One or more specified input parameters are invalid.</span></span>  
  
 [<span data-ttu-id="78b2b-121">LOCALDB_ERROR_INVALID_INSTANCE_NAME</span><span class="sxs-lookup"><span data-stu-id="78b2b-121">LOCALDB_ERROR_INVALID_INSTANCE_NAME</span></span>](../express-localdb-error-messages/localdb-error-invalid-instance-name.md)  
 <span data-ttu-id="78b2b-122">指定したインスタンス名は無効です。</span><span class="sxs-lookup"><span data-stu-id="78b2b-122">The specified instance name is invalid.</span></span>  
  
 [<span data-ttu-id="78b2b-123">LOCALDB_ERROR_UNKNOWN_INSTANCE</span><span class="sxs-lookup"><span data-stu-id="78b2b-123">LOCALDB_ERROR_UNKNOWN_INSTANCE</span></span>](../express-localdb-error-messages/localdb-error-unknown-instance.md)  
 <span data-ttu-id="78b2b-124">インスタンスは存在しません。</span><span class="sxs-lookup"><span data-stu-id="78b2b-124">The instance does not exist.</span></span>  
  
 [<span data-ttu-id="78b2b-125">LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG</span><span class="sxs-lookup"><span data-stu-id="78b2b-125">LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG</span></span>](../express-localdb-error-messages/localdb-error-instance-folder-path-too-long.md)  
 <span data-ttu-id="78b2b-126">インスタンスを格納するパスの長さが MAX_PATH を超過しています。</span><span class="sxs-lookup"><span data-stu-id="78b2b-126">The path where the instance should be stored is longer than MAX_PATH.</span></span>  
  
 [<span data-ttu-id="78b2b-127">LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_FOLDER</span><span class="sxs-lookup"><span data-stu-id="78b2b-127">LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_FOLDER</span></span>](../express-localdb-error-messages/localdb-error-cannot-access-instance-folder.md)  
 <span data-ttu-id="78b2b-128">インスタンス フォルダーにアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="78b2b-128">An instance folder cannot be accessed.</span></span>  
  
 [<span data-ttu-id="78b2b-129">LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_REGISTRY</span><span class="sxs-lookup"><span data-stu-id="78b2b-129">LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_REGISTRY</span></span>](../express-localdb-error-messages/localdb-error-cannot-access-instance-registry.md)  
 <span data-ttu-id="78b2b-130">インスタンス レジストリにアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="78b2b-130">An instance registry cannot be accessed.</span></span>  
  
 [<span data-ttu-id="78b2b-131">LOCALDB_ERROR_INSTANCE_CONFIGURATION_CORRUPT</span><span class="sxs-lookup"><span data-stu-id="78b2b-131">LOCALDB_ERROR_INSTANCE_CONFIGURATION_CORRUPT</span></span>](../express-localdb-error-messages/localdb-error-instance-configuration-corrupt.md)  
 <span data-ttu-id="78b2b-132">インスタンス構成が破損しています。</span><span class="sxs-lookup"><span data-stu-id="78b2b-132">An instance configuration is corrupted.</span></span>  
  
 [<span data-ttu-id="78b2b-133">LOCALDB_ERROR_INTERNAL_ERROR</span><span class="sxs-lookup"><span data-stu-id="78b2b-133">LOCALDB_ERROR_INTERNAL_ERROR</span></span>](../express-localdb-error-messages/localdb-error-internal-error.md)  
 <span data-ttu-id="78b2b-134">予期しないエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="78b2b-134">An unexpected error occurred.</span></span> <span data-ttu-id="78b2b-135">詳細をイベント ログで確認してください。</span><span class="sxs-lookup"><span data-stu-id="78b2b-135">See the event log for details.</span></span>  
  
## <a name="details"></a><span data-ttu-id="78b2b-136">詳細</span><span class="sxs-lookup"><span data-stu-id="78b2b-136">Details</span></span>  
 <span data-ttu-id="78b2b-137">`struct`サイズ引数 (*Lpinstanceinfosize*) の導入の背後にある原理は、API が異なるバージョンの**Localdbinstanceinfostruct**を返すことができるようにすることです。これにより、上位互換性と下位互換性が効果的に有効になります。</span><span class="sxs-lookup"><span data-stu-id="78b2b-137">The rationale behind the introduction of the `struct` size argument (*lpInstanceInfoSize*) is to enable the API to return different versions of the **LocalDBInstanceInfostruct**, effectively enabling forward and backward compatibility.</span></span>  
  
 <span data-ttu-id="78b2b-138">`struct`サイズ引数 (*Lpinstanceinfosize*) が既知のバージョンの**Localdbinstanceinfostruct**のサイズと一致する場合、そのバージョンの `struct` が返されます。</span><span class="sxs-lookup"><span data-stu-id="78b2b-138">If the `struct` size argument (*lpInstanceInfoSize*) matches the size of a known version of the **LocalDBInstanceInfostruct**, that version of the `struct` is returned.</span></span> <span data-ttu-id="78b2b-139">それ以外の場合、LOCALDB_ERROR_INVALID_PARAMETER が返されます。</span><span class="sxs-lookup"><span data-stu-id="78b2b-139">Otherwise, LOCALDB_ERROR_INVALID_PARAMETER is returned.</span></span>  
  
 <span data-ttu-id="78b2b-140">**Localdbgetinstanceinfo** API の一般的な使用例は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="78b2b-140">A typical example of **LocalDBGetInstanceInfo** API usage looks like this:</span></span>  
  
```  
LocalDBInstanceInfo ii;  
LocalDBInstanceInfo(L"Test", &ii, sizeof(LocalDBInstanceInfo));  
  
```  
  
 <span data-ttu-id="78b2b-141">LocalDB API を使用するコードサンプルについては、 [Localdb リファレンスの SQL Server Express](../sql-server-express-localdb-reference.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="78b2b-141">For a code sample that uses LocalDB API, see [SQL Server Express LocalDB Reference](../sql-server-express-localdb-reference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78b2b-142">参照</span><span class="sxs-lookup"><span data-stu-id="78b2b-142">See Also</span></span>  
 [<span data-ttu-id="78b2b-143">SQL Server Express LocalDB ヘッダーとバージョン情報</span><span class="sxs-lookup"><span data-stu-id="78b2b-143">SQL Server Express LocalDB Header and Version Information</span></span>](sql-server-express-localdb-header-and-version-information.md)  
  
  
