---
title: MSSQLSERVER_33028 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 33028 (Database Engine error)
ms.assetid: c5cec0e4-0bcd-4907-826f-e7d835cfcb37
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 555dcf0220793abc0e8af81b3f56867f9960c5f0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640023"
---
# <a name="mssqlserver_33028"></a><span data-ttu-id="d5503-102">MSSQLSERVER_33028</span><span class="sxs-lookup"><span data-stu-id="d5503-102">MSSQLSERVER_33028</span></span>
    
## <a name="details"></a><span data-ttu-id="d5503-103">詳細</span><span class="sxs-lookup"><span data-stu-id="d5503-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d5503-104">製品名</span><span class="sxs-lookup"><span data-stu-id="d5503-104">Product Name</span></span>|<span data-ttu-id="d5503-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="d5503-105">SQL Server</span></span>|  
|<span data-ttu-id="d5503-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="d5503-106">Event ID</span></span>|<span data-ttu-id="d5503-107">33028</span><span class="sxs-lookup"><span data-stu-id="d5503-107">33028</span></span>|  
|<span data-ttu-id="d5503-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="d5503-108">Event Source</span></span>|<span data-ttu-id="d5503-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="d5503-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="d5503-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="d5503-110">Component</span></span>|<span data-ttu-id="d5503-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="d5503-111">SQLEngine</span></span>|  
|<span data-ttu-id="d5503-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="d5503-112">Symbolic Name</span></span>|<span data-ttu-id="d5503-113">SEC_CRYPTOPROV_CANTOPENSESSION</span><span class="sxs-lookup"><span data-stu-id="d5503-113">SEC_CRYPTOPROV_CANTOPENSESSION</span></span>|  
|<span data-ttu-id="d5503-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="d5503-114">Message Text</span></span>|<span data-ttu-id="d5503-115">%S_MSG '%.\*ls' のセッションを開くことができません。</span><span class="sxs-lookup"><span data-stu-id="d5503-115">Cannot open session for %S_MSG '%.\*ls'.</span></span> <span data-ttu-id="d5503-116">プロバイダー エラー コード: %d。</span><span class="sxs-lookup"><span data-stu-id="d5503-116">Provider error code: %d.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="d5503-117">説明</span><span class="sxs-lookup"><span data-stu-id="d5503-117">Explanation</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="d5503-118">は、エラー メッセージに表示されている暗号化サービス プロバイダーを開くことができませんでした。</span><span class="sxs-lookup"><span data-stu-id="d5503-118">was unable to open the cryptographic provider listed in the error message.</span></span> <span data-ttu-id="d5503-119">暗号化サービス プロバイダーは、表示されているエラー コードを返しました。</span><span class="sxs-lookup"><span data-stu-id="d5503-119">The cryptographic provider supplied the error code listed.</span></span> <span data-ttu-id="d5503-120">エラーの詳細については、暗号化サービス プロバイダーに問い合わせる必要があります。</span><span class="sxs-lookup"><span data-stu-id="d5503-120">You may need to contact your cryptographic provider for more information about the error.</span></span>  
  
|<span data-ttu-id="d5503-121">エラー コード</span><span class="sxs-lookup"><span data-stu-id="d5503-121">Error code</span></span>|<span data-ttu-id="d5503-122">説明</span><span class="sxs-lookup"><span data-stu-id="d5503-122">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="d5503-123">0</span><span class="sxs-lookup"><span data-stu-id="d5503-123">0</span></span>|<span data-ttu-id="d5503-124">正常終了しました。</span><span class="sxs-lookup"><span data-stu-id="d5503-124">Success.</span></span> <span data-ttu-id="d5503-125">エラーなし。</span><span class="sxs-lookup"><span data-stu-id="d5503-125">No error.</span></span>|  
|<span data-ttu-id="d5503-126">1</span><span class="sxs-lookup"><span data-stu-id="d5503-126">1</span></span>|<span data-ttu-id="d5503-127">失敗しました。</span><span class="sxs-lookup"><span data-stu-id="d5503-127">Failure.</span></span> <span data-ttu-id="d5503-128">未定義のエラーまたは予期しないエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="d5503-128">An unspecified or unexpected error occurred.</span></span> <span data-ttu-id="d5503-129">追加情報は入手できません。</span><span class="sxs-lookup"><span data-stu-id="d5503-129">Additional information is not available.</span></span>|  
|<span data-ttu-id="d5503-130">2</span><span class="sxs-lookup"><span data-stu-id="d5503-130">2</span></span>|<span data-ttu-id="d5503-131">バッファーが不足しています。</span><span class="sxs-lookup"><span data-stu-id="d5503-131">Insufficient Buffer.</span></span> <span data-ttu-id="d5503-132">暗号化サービス プロバイダー用の領域を割り当てることができませんでした。</span><span class="sxs-lookup"><span data-stu-id="d5503-132">Space could not be allocated for the cryptographic provider.</span></span>|  
|<span data-ttu-id="d5503-133">3</span><span class="sxs-lookup"><span data-stu-id="d5503-133">3</span></span>|<span data-ttu-id="d5503-134">サポートされていません。</span><span class="sxs-lookup"><span data-stu-id="d5503-134">Not Supported.</span></span> <span data-ttu-id="d5503-135">問題となる暗号化サービス プロバイダーが、このリリースではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="d5503-135">The cryptographic provider is not supported by this release.</span></span> <span data-ttu-id="d5503-136">別の暗号化サービス プロバイダーを選択してください。</span><span class="sxs-lookup"><span data-stu-id="d5503-136">Select another cryptographic provider.</span></span>|  
|<span data-ttu-id="d5503-137">4</span><span class="sxs-lookup"><span data-stu-id="d5503-137">4</span></span>|<span data-ttu-id="d5503-138">Not Found. (見つかりませんでした。)</span><span class="sxs-lookup"><span data-stu-id="d5503-138">Not Found.</span></span> <span data-ttu-id="d5503-139">指定した暗号化サービス プロバイダーが存在しないか、ファイルにアクセスする承認を得ていません。</span><span class="sxs-lookup"><span data-stu-id="d5503-139">The specified cryptographic provider is not present or you do not have authorization to access the files.</span></span>|  
|<span data-ttu-id="d5503-140">5</span><span class="sxs-lookup"><span data-stu-id="d5503-140">5</span></span>|<span data-ttu-id="d5503-141">承認エラーです。</span><span class="sxs-lookup"><span data-stu-id="d5503-141">Authorization Failure.</span></span> <span data-ttu-id="d5503-142">資格情報の作成時に指定したパスワードまたはユーザー名が正しくないか、</span><span class="sxs-lookup"><span data-stu-id="d5503-142">Can result from providing an incorrect password or username when creating the credential.</span></span> <span data-ttu-id="d5503-143">資格情報が存在しない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d5503-143">Can result if the credential does not exist.</span></span>|  
|<span data-ttu-id="d5503-144">6</span><span class="sxs-lookup"><span data-stu-id="d5503-144">6</span></span>|<span data-ttu-id="d5503-145">引数が無効です。</span><span class="sxs-lookup"><span data-stu-id="d5503-145">Invalid Argument.</span></span> <span data-ttu-id="d5503-146">暗号化サービス プロバイダーに無効な引数が渡されました。</span><span class="sxs-lookup"><span data-stu-id="d5503-146">An invalid argument was passed to the cryptographic provider.</span></span>|  
  
## <a name="user-action"></a><span data-ttu-id="d5503-147">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="d5503-147">User Action</span></span>  
 <span data-ttu-id="d5503-148">エラーを解決するか、暗号化サービス プロバイダーに詳細を問い合わせてください。</span><span class="sxs-lookup"><span data-stu-id="d5503-148">Resolve the error, or contact the cryptographic provider for more information.</span></span>  
  
  
