---
title: LocalDBGetVersions 関数 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
api_name:
- LocalDBGetVersions
api_location:
- sqluserinstance.dll
topic_type:
- apiref
ms.assetid: 033a9c6b-0d7f-4f8a-ab60-33cd6fee0d33
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 37d2a927346252f1b126f5e3a4ec78ea03cde0a6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741057"
---
# <a name="localdbgetversions-function"></a><span data-ttu-id="b6723-102">LocalDBGetVersions 関数</span><span class="sxs-lookup"><span data-stu-id="b6723-102">LocalDBGetVersions Function</span></span>
  <span data-ttu-id="b6723-103">コンピューターで使用できるすべての SQL Server Express LocalDB バージョンを返します。</span><span class="sxs-lookup"><span data-stu-id="b6723-103">Returns all SQL Server Express LocalDB versions available on the computer.</span></span>  
  
 <span data-ttu-id="b6723-104">**ヘッダーファイル:** sqlncli</span><span class="sxs-lookup"><span data-stu-id="b6723-104">**Header file:** sqlncli.h</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6723-105">構文</span><span class="sxs-lookup"><span data-stu-id="b6723-105">Syntax</span></span>  
  
```  
#define MAX_LOCALDB_VERSION_LENGTH 43typedef WCHAR TLocalDBVersion[MAX_LOCALDB_VERSION_LENGTH + 1];typedef TLocalDBVersion* PTLocalDBVersion;HRESULT LocalDBGetVersions(           PTLocalDBVersion pVersion,           LPDWORD lpdwNumberOfVersions);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b6723-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b6723-106">Parameters</span></span>  
 <span data-ttu-id="b6723-107">*pVersionNames*</span><span class="sxs-lookup"><span data-stu-id="b6723-107">*pVersionNames*</span></span>  
 <span data-ttu-id="b6723-108">Outputユーザーのワークステーションで使用可能な LocalDB バージョンの名前が含まれます。</span><span class="sxs-lookup"><span data-stu-id="b6723-108">[Output] Contains names of the LocalDB versions that are available on the user's workstation.</span></span>  
  
 <span data-ttu-id="b6723-109">*lpdwNumberOfVersions*</span><span class="sxs-lookup"><span data-stu-id="b6723-109">*lpdwNumberOfVersions*</span></span>  
 <span data-ttu-id="b6723-110">[入力/出力]入力時には、 *Pversionnames*バッファーにあるバージョンのスロットの数を保持します。</span><span class="sxs-lookup"><span data-stu-id="b6723-110">[Input/Output] On input holds the number of slots for versions in the *pVersionNames* buffer.</span></span>   
<span data-ttu-id="b6723-111">出力では、既存の LocalDB バージョンの数を保持します。</span><span class="sxs-lookup"><span data-stu-id="b6723-111">On output, holds the number of existing LocalDB versions.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="b6723-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="b6723-112">Returns</span></span>  
 <span data-ttu-id="b6723-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="b6723-113">S_OK</span></span>  
 <span data-ttu-id="b6723-114">関数が正常に実行されました。</span><span class="sxs-lookup"><span data-stu-id="b6723-114">The function succeeded.</span></span>  
  
 [<span data-ttu-id="b6723-115">LOCALDB_ERROR_NOT_INSTALLED</span><span class="sxs-lookup"><span data-stu-id="b6723-115">LOCALDB_ERROR_NOT_INSTALLED</span></span>](../express-localdb-error-messages/localdb-error-not-installed.md)  
 <span data-ttu-id="b6723-116">SQL Server Express LocalDB は、コンピューターにインストールされていません。</span><span class="sxs-lookup"><span data-stu-id="b6723-116">SQL Server Express LocalDB is not installed on the computer.</span></span>  
  
 [<span data-ttu-id="b6723-117">LOCALDB_ERROR_INVALID_PARAMETER</span><span class="sxs-lookup"><span data-stu-id="b6723-117">LOCALDB_ERROR_INVALID_PARAMETER</span></span>](../express-localdb-error-messages/localdb-error-invalid-parameter.md)  
 <span data-ttu-id="b6723-118">指定した 1 つまたは複数の入力パラメーターが無効です。</span><span class="sxs-lookup"><span data-stu-id="b6723-118">One or more specified input parameters are invalid.</span></span>  
  
 [<span data-ttu-id="b6723-119">LOCALDB_ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="b6723-119">LOCALDB_ERROR_INSUFFICIENT_BUFFER</span></span>](../express-localdb-error-messages/localdb-error-insufficient-buffer.md)  
 <span data-ttu-id="b6723-120">入力バッファーが短かすぎますが、切り捨ては要求されませんでした。</span><span class="sxs-lookup"><span data-stu-id="b6723-120">The input buffer is too short, and truncation was not requested.</span></span>  
  
 [<span data-ttu-id="b6723-121">LOCALDB_ERROR_INTERNAL_ERROR</span><span class="sxs-lookup"><span data-stu-id="b6723-121">LOCALDB_ERROR_INTERNAL_ERROR</span></span>](../express-localdb-error-messages/localdb-error-internal-error.md)  
 <span data-ttu-id="b6723-122">予期しないエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="b6723-122">An unexpected error occurred.</span></span> <span data-ttu-id="b6723-123">詳細をイベント ログで確認してください。</span><span class="sxs-lookup"><span data-stu-id="b6723-123">See the event log for details.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b6723-124">解説</span><span class="sxs-lookup"><span data-stu-id="b6723-124">Remarks</span></span>  
 <span data-ttu-id="b6723-125">LocalDB API を使用するコードサンプルについては、 [Localdb リファレンスの SQL Server Express](../sql-server-express-localdb-reference.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b6723-125">For a code sample that uses LocalDB API, see [SQL Server Express LocalDB Reference](../sql-server-express-localdb-reference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6723-126">参照</span><span class="sxs-lookup"><span data-stu-id="b6723-126">See Also</span></span>  
 [<span data-ttu-id="b6723-127">SQL Server Express LocalDB ヘッダーとバージョン情報</span><span class="sxs-lookup"><span data-stu-id="b6723-127">SQL Server Express LocalDB Header and Version Information</span></span>](sql-server-express-localdb-header-and-version-information.md)  
  
  
