---
title: MSSQLSERVER_33128 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 33128 (Database Engine error)
ms.assetid: 12c1096f-d120-439b-85f3-f794859503c9
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 158cc609a18cf3fe7b76708e351b78263cd80a9e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640020"
---
# <a name="mssqlserver_33128"></a><span data-ttu-id="7e09b-102">MSSQLSERVER_33128</span><span class="sxs-lookup"><span data-stu-id="7e09b-102">MSSQLSERVER_33128</span></span>
    
## <a name="details"></a><span data-ttu-id="7e09b-103">詳細</span><span class="sxs-lookup"><span data-stu-id="7e09b-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7e09b-104">製品名</span><span class="sxs-lookup"><span data-stu-id="7e09b-104">Product Name</span></span>|<span data-ttu-id="7e09b-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="7e09b-105">SQL Server</span></span>|  
|<span data-ttu-id="7e09b-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="7e09b-106">Event ID</span></span>|<span data-ttu-id="7e09b-107">33128</span><span class="sxs-lookup"><span data-stu-id="7e09b-107">33128</span></span>|  
|<span data-ttu-id="7e09b-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="7e09b-108">Event Source</span></span>|<span data-ttu-id="7e09b-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="7e09b-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="7e09b-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="7e09b-110">Component</span></span>|<span data-ttu-id="7e09b-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="7e09b-111">SQLEngine</span></span>|  
|<span data-ttu-id="7e09b-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="7e09b-112">Symbolic Name</span></span>|<span data-ttu-id="7e09b-113">SEC_DEPRECATED_ALGO</span><span class="sxs-lookup"><span data-stu-id="7e09b-113">SEC_DEPRECATED_ALGO</span></span>|  
|<span data-ttu-id="7e09b-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="7e09b-114">Message Text</span></span>|<span data-ttu-id="7e09b-115">暗号化は失敗しました。</span><span class="sxs-lookup"><span data-stu-id="7e09b-115">Encryption failed.</span></span> <span data-ttu-id="7e09b-116">キーでは非推奨のアルゴリズム '%.\*ls' が使用されていますが、このアルゴリズムはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="7e09b-116">Key uses deprecated algorithm '%.\*ls' which is no longer supported.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="7e09b-117">説明</span><span class="sxs-lookup"><span data-stu-id="7e09b-117">Explanation</span></span>  
 <span data-ttu-id="7e09b-118">このメッセージは、RC4 (または RC4_128) 暗号化アルゴリズムを参照した場合に表示されます。</span><span class="sxs-lookup"><span data-stu-id="7e09b-118">This message occurs when referencing the RC4 (or RC4_128) encryption algorithm.</span></span> <span data-ttu-id="7e09b-119">RC4 および RC4_128 は、弱いアルゴリズムなので非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="7e09b-119">RC4 and RC4_128 are weak algorithms and are deprecated.</span></span> <span data-ttu-id="7e09b-120">AES アルゴリズムのいずれかなど、強力なアルゴリズムを使用してください</span><span class="sxs-lookup"><span data-stu-id="7e09b-120">Use a stronger algorithm such as one of the AES algorithms instead.</span></span>  
  
 <span data-ttu-id="7e09b-121">データベースの互換性レベルが 90 または 100 の場合、操作は成功し、今後廃止予定のイベントが発生し、メッセージがリング バッファーにのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="7e09b-121">When the database compatibility level is 90 or 100, the operation succeeds, the deprecation event is raised, and the message appears only in the ring buffer.</span></span>  
  
 <span data-ttu-id="7e09b-122">データベースの互換性レベルが 110 以上の場合、暗号化解除操作は成功し、今後廃止予定のイベントが発生して、メッセージがリング バッファーにのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="7e09b-122">When the database compatibility level is 110 or higher, decryption operations succeed, the deprecation event is raised, and the message appears only in the ring buffer.</span></span> <span data-ttu-id="7e09b-123">暗号化操作は失敗し、今後廃止予定のイベントが発生し、ユーザーにメッセージが表示されます。また、メッセージがリング バッファーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="7e09b-123">Encryption operations will fail, the deprecation event is raised, and the message is displayed for the user, and the message appears in the ring buffer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7e09b-124">リング バッファーは完全には文書にまとめられていない内部コンポーネントであり、ユーザーが使用するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="7e09b-124">The ring buffer is an internal component which is not fully documented and is not intended to be used by customers.</span></span> <span data-ttu-id="7e09b-125">リング バッファーからのメッセージは、[!INCLUDE[msCoName](../../includes/msconame-md.md)] カスタマー サポートに問い合わせる際に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="7e09b-125">Messages from the ring buffer are useful when contacting [!INCLUDE[msCoName](../../includes/msconame-md.md)] Customer Support.</span></span> <span data-ttu-id="7e09b-126">リング バッファーを表示するには、sys.dm_os_ring_buffers 動的管理ビューに対してクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="7e09b-126">To view the ring buffer, query the sys.dm_os_ring_buffers dynamic management view.</span></span>  
  
|<span data-ttu-id="7e09b-127">State</span><span class="sxs-lookup"><span data-stu-id="7e09b-127">State</span></span>|<span data-ttu-id="7e09b-128">説明</span><span class="sxs-lookup"><span data-stu-id="7e09b-128">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7e09b-129">1</span><span class="sxs-lookup"><span data-stu-id="7e09b-129">1</span></span>|<span data-ttu-id="7e09b-130">RC4 キーは、encryptbykey() 組み込み関数で使用されます。</span><span class="sxs-lookup"><span data-stu-id="7e09b-130">A RC4 key is used in the built-in encryptbykey() function.</span></span> <span data-ttu-id="7e09b-131">組み込み関数は NULL を返します。</span><span class="sxs-lookup"><span data-stu-id="7e09b-131">Built-in function returns NULL.</span></span> <span data-ttu-id="7e09b-132">このメッセージは、リング バッファーにのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="7e09b-132">This message only appears in the ring buffer.</span></span>|  
|<span data-ttu-id="7e09b-133">2</span><span class="sxs-lookup"><span data-stu-id="7e09b-133">2</span></span>|<span data-ttu-id="7e09b-134">RC4 キーは、decryptbykey() 組み込み関数で使用されます。</span><span class="sxs-lookup"><span data-stu-id="7e09b-134">A RC4 key is used in by the built-in decryptbykey() function.</span></span> <span data-ttu-id="7e09b-135">このメッセージは、リング バッファーにのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="7e09b-135">This message only appears in the ring buffer.</span></span>|  
|<span data-ttu-id="7e09b-136">3</span><span class="sxs-lookup"><span data-stu-id="7e09b-136">3</span></span>|<span data-ttu-id="7e09b-137">非推奨の RC4 キーは、対称キーを使用して暗号化されています。</span><span class="sxs-lookup"><span data-stu-id="7e09b-137">A deprecated RC4 key is being encrypted by a symmetric key.</span></span> <span data-ttu-id="7e09b-138">ユーザーとリング バッファーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="7e09b-138">Seen by users and in the ring buffer.</span></span> <span data-ttu-id="7e09b-139">非推奨の RC4 対称キーは、互換性レベル 110 では変更できません。</span><span class="sxs-lookup"><span data-stu-id="7e09b-139">Deprecated RC4 symmetric keys cannot be altered in compatibility level 110.</span></span> <span data-ttu-id="7e09b-140">暗号化操作には、RC4 以外のキーを使用してください。</span><span class="sxs-lookup"><span data-stu-id="7e09b-140">Try to use non-RC4 keys for crypto operations.</span></span> <span data-ttu-id="7e09b-141">必要に応じて、旧バージョンとの互換性レベルを 90 または 100 に設定してください。</span><span class="sxs-lookup"><span data-stu-id="7e09b-141">If necessary, set backward compatibility level to a 90 or 100.</span></span>|  
|<span data-ttu-id="7e09b-142">4</span><span class="sxs-lookup"><span data-stu-id="7e09b-142">4</span></span>|<span data-ttu-id="7e09b-143">RC4 以外のキーは、非推奨の RC4 対称キーを使用して暗号化されています。</span><span class="sxs-lookup"><span data-stu-id="7e09b-143">A non-RC4 key is being encrypted by a deprecated RC4 symmetric key.</span></span> <span data-ttu-id="7e09b-144">ユーザーとリング バッファーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="7e09b-144">Seen by users and in the ring buffer.</span></span> <span data-ttu-id="7e09b-145">RC4 以外の対称キーを使用するようにアプリケーションを変更するか、旧バージョンとの互換性レベルを 90 または 100 に設定してください。</span><span class="sxs-lookup"><span data-stu-id="7e09b-145">Modify the application to use non-RC4 symmetric keys or set backward compatibility level to 90 or 100.</span></span>|  
|<span data-ttu-id="7e09b-146">5</span><span class="sxs-lookup"><span data-stu-id="7e09b-146">5</span></span>|<span data-ttu-id="7e09b-147">非推奨の RC4 キーは、対称キーを使用して暗号化解除されています。</span><span class="sxs-lookup"><span data-stu-id="7e09b-147">A deprecated RC4 key is being decrypted by a symmetric key.</span></span> <span data-ttu-id="7e09b-148">このメッセージは、リング バッファーにのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="7e09b-148">This message only appears in the ring buffer.</span></span>|  
|<span data-ttu-id="7e09b-149">6</span><span class="sxs-lookup"><span data-stu-id="7e09b-149">6</span></span>|<span data-ttu-id="7e09b-150">RC4 以外のキーは、RC4 対称キーを使用して暗号化解除されています。</span><span class="sxs-lookup"><span data-stu-id="7e09b-150">A non-RC4 key is being decrypted by an RC4 symmetric key.</span></span> <span data-ttu-id="7e09b-151">このメッセージは、リング バッファーにのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="7e09b-151">This message only appears in the ring buffer.</span></span>|  
|<span data-ttu-id="7e09b-152">7</span><span class="sxs-lookup"><span data-stu-id="7e09b-152">7</span></span>|<span data-ttu-id="7e09b-153">RC4 対称キーは、証明書を使用して暗号化されています。</span><span class="sxs-lookup"><span data-stu-id="7e09b-153">A RC4 symmetric key is being encrypted by the certificate.</span></span> <span data-ttu-id="7e09b-154">ユーザーとリング バッファーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="7e09b-154">Seen by users and in the ring buffer.</span></span>|  
|<span data-ttu-id="7e09b-155">8</span><span class="sxs-lookup"><span data-stu-id="7e09b-155">8</span></span>|<span data-ttu-id="7e09b-156">RC4 対称キーは、証明書を使用して暗号化解除されています。</span><span class="sxs-lookup"><span data-stu-id="7e09b-156">A RC4 symmetric key is being decrypted by the certificate.</span></span> <span data-ttu-id="7e09b-157">このメッセージは、リング バッファーにのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="7e09b-157">This message only appears in the ring buffer.</span></span>|  
|<span data-ttu-id="7e09b-158">9</span><span class="sxs-lookup"><span data-stu-id="7e09b-158">9</span></span>|<span data-ttu-id="7e09b-159">RC4 対称キーは、EKM キーを使用して暗号化されています。</span><span class="sxs-lookup"><span data-stu-id="7e09b-159">A RC4 symmetric key is being encrypted by the EKM key.</span></span>|  
|<span data-ttu-id="7e09b-160">10</span><span class="sxs-lookup"><span data-stu-id="7e09b-160">10</span></span>|<span data-ttu-id="7e09b-161">RC4 対称キーは、EKM キーを使用して暗号化解除されています。</span><span class="sxs-lookup"><span data-stu-id="7e09b-161">A RC4 symmetric key is being decrypted by the EKM key.</span></span> <span data-ttu-id="7e09b-162">このメッセージは、リング バッファーにのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="7e09b-162">This message only appears in the ring buffer.</span></span>|  
  
## <a name="user-action"></a><span data-ttu-id="7e09b-163">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="7e09b-163">User Action</span></span>  
 <span data-ttu-id="7e09b-164">AES アルゴリズムのいずれかなど、強力なアルゴリズムを使用してください</span><span class="sxs-lookup"><span data-stu-id="7e09b-164">Use a stronger algorithm such as one of the AES algorithms instead.</span></span> <span data-ttu-id="7e09b-165">(推奨)</span><span class="sxs-lookup"><span data-stu-id="7e09b-165">(Recommended)</span></span>  
  
 <span data-ttu-id="7e09b-166">ALTER DATABASE SET COMPATIBILITY_LEVEL を使用して、データベースの互換性レベルを 100 に設定してください</span><span class="sxs-lookup"><span data-stu-id="7e09b-166">Use ALTER DATABASE SET COMPATIBILITY_LEVEL to set the database to compatibility level 100.</span></span> <span data-ttu-id="7e09b-167">(非推奨)。</span><span class="sxs-lookup"><span data-stu-id="7e09b-167">(Not recommended.)</span></span>  
  
  
