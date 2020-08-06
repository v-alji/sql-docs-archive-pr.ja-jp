---
title: LocalDBFormatMessage 関数 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
api_name:
- LocalDBFormatMessage
api_location:
- sqluserinstance.dll
topic_type:
- apiref
ms.assetid: 31b3152a-94cf-4f75-a31b-296d7dd16dbe
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: ece28f19e3488fae248bf26c3a54a018ba6efd0c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743262"
---
# <a name="localdbformatmessage-function"></a><span data-ttu-id="38c8d-102">LocalDBFormatMessage 関数</span><span class="sxs-lookup"><span data-stu-id="38c8d-102">LocalDBFormatMessage Function</span></span>
  <span data-ttu-id="38c8d-103">指定した SQL Server Express LocalDB エラーについてのローカライズされた説明テキストを返します。</span><span class="sxs-lookup"><span data-stu-id="38c8d-103">Returns the localized textual description for the specified SQL Server Express LocalDB error.</span></span>  
  
 <span data-ttu-id="38c8d-104">**ヘッダーファイル:** sqlncli</span><span class="sxs-lookup"><span data-stu-id="38c8d-104">**Header file:** sqlncli.h</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38c8d-105">構文</span><span class="sxs-lookup"><span data-stu-id="38c8d-105">Syntax</span></span>  
  
```  
HRESULT LocalDBFormatMessage(  
           HRESULT hrLocalDB,  
           DWORD dwFlags,   
           DWORD dwLanguageId,   
           LPWSTR wszMessage,   
           LPDWORD lpcchMessage   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="38c8d-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="38c8d-106">Parameters</span></span>  
 <span data-ttu-id="38c8d-107">*hrLocalDB*</span><span class="sxs-lookup"><span data-stu-id="38c8d-107">*hrLocalDB*</span></span>  
 <span data-ttu-id="38c8d-108">[入力] LocalDB のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="38c8d-108">[Input] The LocalDB error code.</span></span>  
  
 <span data-ttu-id="38c8d-109">*dwFlags*</span><span class="sxs-lookup"><span data-stu-id="38c8d-109">*dwFlags*</span></span>  
 <span data-ttu-id="38c8d-110">[入力] この関数の動作を指定するフラグ。</span><span class="sxs-lookup"><span data-stu-id="38c8d-110">[Input] The flags specifying the behavior of this function.</span></span>  
  
 <span data-ttu-id="38c8d-111">使用できるフラグ:</span><span class="sxs-lookup"><span data-stu-id="38c8d-111">Available flags:</span></span>  
  
 <span data-ttu-id="38c8d-112">LOCALDB_TRUNCATE_ERR_MESSAGE</span><span class="sxs-lookup"><span data-stu-id="38c8d-112">LOCALDB_TRUNCATE_ERR_MESSAGE</span></span>  
 <span data-ttu-id="38c8d-113">入力バッファーが短かすぎる場合、バッファーに合わせてエラー メッセージが切り捨てられます。</span><span class="sxs-lookup"><span data-stu-id="38c8d-113">If the input buffer is too short, the error message will be truncated to fit the buffer.</span></span>  
  
 <span data-ttu-id="38c8d-114">*dwLanguageId*</span><span class="sxs-lookup"><span data-stu-id="38c8d-114">*dwLanguageId*</span></span>  
 <span data-ttu-id="38c8d-115">[入力] 目的の言語 (LANGID) または 0。0 の場合、Win32 FormatMessage 言語順序が使用されます。</span><span class="sxs-lookup"><span data-stu-id="38c8d-115">[Input] The language desired (LANGID) or 0, in which case the Win32 FormatMessage language order is used.</span></span>  
  
 <span data-ttu-id="38c8d-116">*wszMessage*</span><span class="sxs-lookup"><span data-stu-id="38c8d-116">*wszMessage*</span></span>  
 <span data-ttu-id="38c8d-117">[出力] LocalDB エラー メッセージを格納するバッファー。</span><span class="sxs-lookup"><span data-stu-id="38c8d-117">[Output] The buffer to store the LocalDB error message.</span></span>  
  
 <span data-ttu-id="38c8d-118">*lpcchMessage*</span><span class="sxs-lookup"><span data-stu-id="38c8d-118">*lpcchMessage*</span></span>  
 <span data-ttu-id="38c8d-119">[入力/出力]入力時には、 *wszMessage*バッファーのサイズが文字数で格納されます。</span><span class="sxs-lookup"><span data-stu-id="38c8d-119">[Input/Output] On input contains the size of the *wszMessage* buffer in characters.</span></span> <span data-ttu-id="38c8d-120">出力側では、所定のバッファー サイズが小さすぎる場合、末尾の NULL も含め、必要なバッファー サイズ (単位は文字数) を格納します。</span><span class="sxs-lookup"><span data-stu-id="38c8d-120">On output, if the given buffer size is too small, contains the buffer size required in characters, including any trailing nulls.</span></span> <span data-ttu-id="38c8d-121">関数を正常に実行できた場合、このメッセージ内の文字数を格納します。ただし、末尾の NULL は除外します。</span><span class="sxs-lookup"><span data-stu-id="38c8d-121">If the function succeeds, contains the number of characters in the message, excluding any trailing nulls.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="38c8d-122">戻り値</span><span class="sxs-lookup"><span data-stu-id="38c8d-122">Returns</span></span>  
 <span data-ttu-id="38c8d-123">S_OK</span><span class="sxs-lookup"><span data-stu-id="38c8d-123">S_OK</span></span>  
 <span data-ttu-id="38c8d-124">関数が正常に実行されました。</span><span class="sxs-lookup"><span data-stu-id="38c8d-124">The function succeeded.</span></span>  
  
 [<span data-ttu-id="38c8d-125">LOCALDB_ERROR_NOT_INSTALLED</span><span class="sxs-lookup"><span data-stu-id="38c8d-125">LOCALDB_ERROR_NOT_INSTALLED</span></span>](../express-localdb-error-messages/localdb-error-not-installed.md)  
 <span data-ttu-id="38c8d-126">SQL Server Express LocalDB は、コンピューターにインストールされていません。</span><span class="sxs-lookup"><span data-stu-id="38c8d-126">SQL Server Express LocalDB is not installed on the computer.</span></span>  
  
 [<span data-ttu-id="38c8d-127">LOCALDB_ERROR_INVALID_PARAMETER</span><span class="sxs-lookup"><span data-stu-id="38c8d-127">LOCALDB_ERROR_INVALID_PARAMETER</span></span>](../express-localdb-error-messages/localdb-error-invalid-parameter.md)  
 <span data-ttu-id="38c8d-128">指定した 1 つまたは複数の入力パラメーターが無効です。</span><span class="sxs-lookup"><span data-stu-id="38c8d-128">One or more specified input parameters are invalid.</span></span>  
  
 [<span data-ttu-id="38c8d-129">LOCALDB_ERROR_UNKNOWN_ERROR_CODE</span><span class="sxs-lookup"><span data-stu-id="38c8d-129">LOCALDB_ERROR_UNKNOWN_ERROR_CODE</span></span>](../express-localdb-error-messages/localdb-error-unknown-error-code.md)  
 <span data-ttu-id="38c8d-130">要求されたメッセージは存在しません。</span><span class="sxs-lookup"><span data-stu-id="38c8d-130">The requested message does not exist.</span></span>  
  
 [<span data-ttu-id="38c8d-131">LOCALDB_ERROR_UNKNOWN_LANGUAGE_ID</span><span class="sxs-lookup"><span data-stu-id="38c8d-131">LOCALDB_ERROR_UNKNOWN_LANGUAGE_ID</span></span>](../express-localdb-error-messages/localdb-error-unknown-language-id.md)  
 <span data-ttu-id="38c8d-132">メッセージは、要求された言語では用意されていません。</span><span class="sxs-lookup"><span data-stu-id="38c8d-132">The message is not available in the requested language.</span></span>  
  
 [<span data-ttu-id="38c8d-133">LOCALDB_ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="38c8d-133">LOCALDB_ERROR_INSUFFICIENT_BUFFER</span></span>](../express-localdb-error-messages/localdb-error-insufficient-buffer.md)  
 <span data-ttu-id="38c8d-134">入力バッファー *wszMessage*が短すぎて、切り捨てが要求されていません。</span><span class="sxs-lookup"><span data-stu-id="38c8d-134">The input buffer *wszMessage* is too short, and truncation is not requested.</span></span>  
  
 [<span data-ttu-id="38c8d-135">LOCALDB_ERROR_INTERNAL_ERROR</span><span class="sxs-lookup"><span data-stu-id="38c8d-135">LOCALDB_ERROR_INTERNAL_ERROR</span></span>](../express-localdb-error-messages/localdb-error-internal-error.md)  
 <span data-ttu-id="38c8d-136">予期しないエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="38c8d-136">An unexpected error occurred.</span></span> <span data-ttu-id="38c8d-137">詳細をイベント ログで確認してください。</span><span class="sxs-lookup"><span data-stu-id="38c8d-137">See the event log for details.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="38c8d-138">解説</span><span class="sxs-lookup"><span data-stu-id="38c8d-138">Remarks</span></span>  
 <span data-ttu-id="38c8d-139">LocalDB API を使用するコードサンプルについては、 [Localdb リファレンスの SQL Server Express](../sql-server-express-localdb-reference.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="38c8d-139">For a code sample that uses LocalDB API, see [SQL Server Express LocalDB Reference](../sql-server-express-localdb-reference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38c8d-140">参照</span><span class="sxs-lookup"><span data-stu-id="38c8d-140">See Also</span></span>  
 [<span data-ttu-id="38c8d-141">SQL Server Express LocalDB ヘッダーとバージョン情報</span><span class="sxs-lookup"><span data-stu-id="38c8d-141">SQL Server Express LocalDB Header and Version Information</span></span>](sql-server-express-localdb-header-and-version-information.md)  
  
  
