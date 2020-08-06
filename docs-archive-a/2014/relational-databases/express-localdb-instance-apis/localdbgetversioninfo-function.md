---
title: LocalDBGetVersionInfo 関数 |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
api_name:
- LocalDBGetVersionInfo
api_location:
- sqluserinstance.dll
topic_type:
- apiref
ms.assetid: d4aaea30-1d0d-4436-bcdc-5c101d27b1c1
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: e30bb4dcd4c258db899883f650dbfe7100171ef8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742149"
---
# <a name="localdbgetversioninfo-function"></a><span data-ttu-id="2948f-102">LocalDBGetVersionInfo 関数</span><span class="sxs-lookup"><span data-stu-id="2948f-102">LocalDBGetVersionInfo Function</span></span>
  <span data-ttu-id="2948f-103">指定した SQL Server Express LocalDB バージョンの情報を返します。たとえば、存在するかどうか、LocalDB 完全バージョン番号 (ビルド番号やリリース番号を含む) などです。</span><span class="sxs-lookup"><span data-stu-id="2948f-103">Returns information for the specified SQL Server Express LocalDB version, such as whether it exists and the full LocalDB version number (including build and release numbers).</span></span>  
  
 <span data-ttu-id="2948f-104">この情報は、 `struct` 次の定義を含む、 **LocalDBVersionInfo**という名前の形式で返されます。</span><span class="sxs-lookup"><span data-stu-id="2948f-104">The information is returned in the form of a `struct` named **LocalDBVersionInfo**, which has the following definition.</span></span>  
  
```  
typedef struct _LocalDBVersionInfo  
{  
      // Contains the size of the LocalDBVersionInfo struct  
      DWORD  cbLocalDBVersionInfoSize;  
  
      // Holds the version name  
      TLocalDBVersionwszVersion;  
  
      // TRUE if the instance files exist on disk, FALSE otherwise  
      BOOL   bExists;  
  
      // Holds the LocalDB version for the instance in the format: major.minor.build.revision  
      DWORD  dwMajor;  
      DWORD  dwMinor;  
      DWORD  dwBuild;  
      DWORD  dwRevision;  
} LocalDBVersionInfo;  
  
```  
  
 <span data-ttu-id="2948f-105">**ヘッダーファイル:** sqlncli</span><span class="sxs-lookup"><span data-stu-id="2948f-105">**Header file:** sqlncli.h</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2948f-106">構文</span><span class="sxs-lookup"><span data-stu-id="2948f-106">Syntax</span></span>  
  
```  
HRESULT LocalDBGetVersionInfo(  
           PCWSTR wszVersionName,           PLocalDBVersionInfo pVersionInfo,           DWORD dwVersionInfoSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2948f-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2948f-107">Parameters</span></span>  
 <span data-ttu-id="2948f-108">*wszVersionName*</span><span class="sxs-lookup"><span data-stu-id="2948f-108">*wszVersionName*</span></span>  
 <span data-ttu-id="2948f-109">[入力] LocalDB バージョンの名前。</span><span class="sxs-lookup"><span data-stu-id="2948f-109">[Input] The LocalDB version name.</span></span>  
  
 <span data-ttu-id="2948f-110">*pVersionInfo*</span><span class="sxs-lookup"><span data-stu-id="2948f-110">*pVersionInfo*</span></span>  
 <span data-ttu-id="2948f-111">[出力] LocalDB バージョンについての情報を格納するバッファー。</span><span class="sxs-lookup"><span data-stu-id="2948f-111">[Output] The buffer to store the information about the LocalDB version.</span></span>  
  
 <span data-ttu-id="2948f-112">*dwVersionInfoSize*</span><span class="sxs-lookup"><span data-stu-id="2948f-112">*dwVersionInfoSize*</span></span>  
 <span data-ttu-id="2948f-113">代入*VersionInfo*バッファーのサイズを保持します。</span><span class="sxs-lookup"><span data-stu-id="2948f-113">[Input] Holds the size of the *VersionInfo* buffer.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="2948f-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="2948f-114">Returns</span></span>  
 <span data-ttu-id="2948f-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="2948f-115">S_OK</span></span>  
 <span data-ttu-id="2948f-116">関数が正常に実行されました。</span><span class="sxs-lookup"><span data-stu-id="2948f-116">The function succeeded.</span></span>  
  
 [<span data-ttu-id="2948f-117">LOCALDB_ERROR_NOT_INSTALLED</span><span class="sxs-lookup"><span data-stu-id="2948f-117">LOCALDB_ERROR_NOT_INSTALLED</span></span>](../express-localdb-error-messages/localdb-error-not-installed.md)  
 <span data-ttu-id="2948f-118">SQL Server Express LocalDB は、コンピューターにインストールされていません。</span><span class="sxs-lookup"><span data-stu-id="2948f-118">SQL Server Express LocalDB is not installed on the computer.</span></span>  
  
 [<span data-ttu-id="2948f-119">LOCALDB_ERROR_INVALID_PARAMETER</span><span class="sxs-lookup"><span data-stu-id="2948f-119">LOCALDB_ERROR_INVALID_PARAMETER</span></span>](../express-localdb-error-messages/localdb-error-invalid-parameter.md)  
 <span data-ttu-id="2948f-120">指定した 1 つまたは複数の入力パラメーターが無効です。</span><span class="sxs-lookup"><span data-stu-id="2948f-120">One or more specified input parameters are invalid.</span></span>  
  
 [<span data-ttu-id="2948f-121">LOCALDB_ERROR_UNKNOWN_VERSION</span><span class="sxs-lookup"><span data-stu-id="2948f-121">LOCALDB_ERROR_UNKNOWN_VERSION</span></span>](../express-localdb-error-messages/localdb-error-unknown-version.md)  
 <span data-ttu-id="2948f-122">指定された LocalDB バージョンが存在しません。</span><span class="sxs-lookup"><span data-stu-id="2948f-122">The specified LocalDB version does not exist.</span></span>  
  
 [<span data-ttu-id="2948f-123">LOCALDB_ERROR_INTERNAL_ERROR</span><span class="sxs-lookup"><span data-stu-id="2948f-123">LOCALDB_ERROR_INTERNAL_ERROR</span></span>](../express-localdb-error-messages/localdb-error-internal-error.md)  
 <span data-ttu-id="2948f-124">予期しないエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="2948f-124">An unexpected error occurred.</span></span> <span data-ttu-id="2948f-125">詳細をイベント ログで確認してください。</span><span class="sxs-lookup"><span data-stu-id="2948f-125">See the event log for details.</span></span>  
  
## <a name="details"></a><span data-ttu-id="2948f-126">詳細</span><span class="sxs-lookup"><span data-stu-id="2948f-126">Details</span></span>  
 <span data-ttu-id="2948f-127">サイズ引数の導入の背後にある論理的根拠 `struct` (*lpVersionInfoSize*) は、API がさまざまなバージョンの**LocalDBVersionInfostruct**を返すことができるようにし、上位互換性と下位互換性を効果的に有効にすることです。</span><span class="sxs-lookup"><span data-stu-id="2948f-127">The rationale behind the introduction of the `struct` size argument (*lpVersionInfoSize*) is to enable the API to return different versions of the **LocalDBVersionInfostruct**, effectively enabling forward and backward compatibility.</span></span>  
  
 <span data-ttu-id="2948f-128">`struct`サイズ引数 (*lpVersionInfoSize*) が既知のバージョンの**LocalDBVersionInfostruct**のサイズと一致する場合、そのバージョンの `struct` が返されます。</span><span class="sxs-lookup"><span data-stu-id="2948f-128">If the `struct` size argument (*lpVersionInfoSize*) matches the size of a known version of the **LocalDBVersionInfostruct**, that version of the `struct` is returned.</span></span> <span data-ttu-id="2948f-129">それ以外の場合、LOCALDB_ERROR_INVALID_PARAMETER が返されます。</span><span class="sxs-lookup"><span data-stu-id="2948f-129">Otherwise, LOCALDB_ERROR_INVALID_PARAMETER is returned.</span></span>  
  
 <span data-ttu-id="2948f-130">一般的な**LocalDBGetVersionInfo** API の使用例は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="2948f-130">A typical example of **LocalDBGetVersionInfo** API usage looks like this:</span></span>  
  
```  
LocalDBVersionInfo vi;  
LocalDBVersionInfo(L"11.0", &vi, sizeof(LocalDBVersionInfo));  
  
```  
  
## <a name="remarks"></a><span data-ttu-id="2948f-131">解説</span><span class="sxs-lookup"><span data-stu-id="2948f-131">Remarks</span></span>  
 <span data-ttu-id="2948f-132">LocalDB API を使用するコードサンプルについては、 [Localdb リファレンスの SQL Server Express](../sql-server-express-localdb-reference.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2948f-132">For a code sample that uses LocalDB API, see [SQL Server Express LocalDB Reference](../sql-server-express-localdb-reference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2948f-133">参照</span><span class="sxs-lookup"><span data-stu-id="2948f-133">See Also</span></span>  
 [<span data-ttu-id="2948f-134">SQL Server Express LocalDB ヘッダーとバージョン情報</span><span class="sxs-lookup"><span data-stu-id="2948f-134">SQL Server Express LocalDB Header and Version Information</span></span>](sql-server-express-localdb-header-and-version-information.md)  
  
  
