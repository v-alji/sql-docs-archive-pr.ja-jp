---
title: MSSQLSERVER_33085 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 33085 (Database Engine error)
ms.assetid: c27b8d1d-668a-4ba8-8b61-25a5ebbc5485
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8d774ab115c2d0ddbbd7b35c7e32db17e39fcb2e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640021"
---
# <a name="mssqlserver_33085"></a><span data-ttu-id="4f6b4-102">MSSQLSERVER_33085</span><span class="sxs-lookup"><span data-stu-id="4f6b4-102">MSSQLSERVER_33085</span></span>
    
## <a name="details"></a><span data-ttu-id="4f6b4-103">詳細</span><span class="sxs-lookup"><span data-stu-id="4f6b4-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4f6b4-104">製品名</span><span class="sxs-lookup"><span data-stu-id="4f6b4-104">Product Name</span></span>|<span data-ttu-id="4f6b4-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="4f6b4-105">SQL Server</span></span>|  
|<span data-ttu-id="4f6b4-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="4f6b4-106">Event ID</span></span>|<span data-ttu-id="4f6b4-107">33085</span><span class="sxs-lookup"><span data-stu-id="4f6b4-107">33085</span></span>|  
|<span data-ttu-id="4f6b4-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="4f6b4-108">Event Source</span></span>|<span data-ttu-id="4f6b4-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="4f6b4-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="4f6b4-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="4f6b4-110">Component</span></span>|<span data-ttu-id="4f6b4-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="4f6b4-111">SQLEngine</span></span>|  
|<span data-ttu-id="4f6b4-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="4f6b4-112">Symbolic Name</span></span>|<span data-ttu-id="4f6b4-113">SEC_CRYPTOPROVE_METHOD_CANNOT_FOUND</span><span class="sxs-lookup"><span data-stu-id="4f6b4-113">SEC_CRYPTOPROVE_METHOD_CANNOT_FOUND</span></span>|  
|<span data-ttu-id="4f6b4-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="4f6b4-114">Message Text</span></span>|<span data-ttu-id="4f6b4-115">1 つ以上のメソッドが暗号化サービス プロバイダー ライブラリ '%.\*ls' で見つかりませんでした。</span><span class="sxs-lookup"><span data-stu-id="4f6b4-115">One or more methods cannot be found in cryptographic provider library '%.\*ls'.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="4f6b4-116">説明</span><span class="sxs-lookup"><span data-stu-id="4f6b4-116">Explanation</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="4f6b4-117">は、エラー メッセージに表示されている暗号化サービス プロバイダーを使用できませんでした。</span><span class="sxs-lookup"><span data-stu-id="4f6b4-117">was unable to use the cryptographic provider listed in the error message.</span></span> <span data-ttu-id="4f6b4-118">該当する暗号化サービス プロバイダーでは、必要なメソッドがサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="4f6b4-118">The cryptographic provider did not support a required method.</span></span> <span data-ttu-id="4f6b4-119">エラーの状態によって、見つからなかったメソッドを確認できます。</span><span class="sxs-lookup"><span data-stu-id="4f6b4-119">The state of the error indicates which method was not found.</span></span>  
  
|<span data-ttu-id="4f6b4-120">State</span><span class="sxs-lookup"><span data-stu-id="4f6b4-120">State</span></span>|<span data-ttu-id="4f6b4-121">説明</span><span class="sxs-lookup"><span data-stu-id="4f6b4-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="4f6b4-122">1</span><span class="sxs-lookup"><span data-stu-id="4f6b4-122">1</span></span>|<span data-ttu-id="4f6b4-123">SqlCryptInitializeProvider</span><span class="sxs-lookup"><span data-stu-id="4f6b4-123">SqlCryptInitializeProvider</span></span>|  
|<span data-ttu-id="4f6b4-124">2</span><span class="sxs-lookup"><span data-stu-id="4f6b4-124">2</span></span>|<span data-ttu-id="4f6b4-125">SqlCryptFreeProvider</span><span class="sxs-lookup"><span data-stu-id="4f6b4-125">SqlCryptFreeProvider</span></span>|  
|<span data-ttu-id="4f6b4-126">3</span><span class="sxs-lookup"><span data-stu-id="4f6b4-126">3</span></span>|<span data-ttu-id="4f6b4-127">SqlCryptOpenSession</span><span class="sxs-lookup"><span data-stu-id="4f6b4-127">SqlCryptOpenSession</span></span>|  
|<span data-ttu-id="4f6b4-128">4</span><span class="sxs-lookup"><span data-stu-id="4f6b4-128">4</span></span>|<span data-ttu-id="4f6b4-129">SqlCryptCloseSession</span><span class="sxs-lookup"><span data-stu-id="4f6b4-129">SqlCryptCloseSession</span></span>|  
|<span data-ttu-id="4f6b4-130">5</span><span class="sxs-lookup"><span data-stu-id="4f6b4-130">5</span></span>|<span data-ttu-id="4f6b4-131">SqlCryptGetProviderInfo</span><span class="sxs-lookup"><span data-stu-id="4f6b4-131">SqlCryptGetProviderInfo</span></span>|  
|<span data-ttu-id="4f6b4-132">6</span><span class="sxs-lookup"><span data-stu-id="4f6b4-132">6</span></span>|<span data-ttu-id="4f6b4-133">SqlCryptGetNextAlgorithmId</span><span class="sxs-lookup"><span data-stu-id="4f6b4-133">SqlCryptGetNextAlgorithmId</span></span>|  
|<span data-ttu-id="4f6b4-134">7</span><span class="sxs-lookup"><span data-stu-id="4f6b4-134">7</span></span>|<span data-ttu-id="4f6b4-135">SqlCryptGetAlgorithmInfo</span><span class="sxs-lookup"><span data-stu-id="4f6b4-135">SqlCryptGetAlgorithmInfo</span></span>|  
|<span data-ttu-id="4f6b4-136">8</span><span class="sxs-lookup"><span data-stu-id="4f6b4-136">8</span></span>|<span data-ttu-id="4f6b4-137">SqlCryptCreateKey</span><span class="sxs-lookup"><span data-stu-id="4f6b4-137">SqlCryptCreateKey</span></span>|  
|<span data-ttu-id="4f6b4-138">9</span><span class="sxs-lookup"><span data-stu-id="4f6b4-138">9</span></span>|<span data-ttu-id="4f6b4-139">SqlCryptDropKey</span><span class="sxs-lookup"><span data-stu-id="4f6b4-139">SqlCryptDropKey</span></span>|  
|<span data-ttu-id="4f6b4-140">10</span><span class="sxs-lookup"><span data-stu-id="4f6b4-140">10</span></span>|<span data-ttu-id="4f6b4-141">SqlCryptGetNextKeyId</span><span class="sxs-lookup"><span data-stu-id="4f6b4-141">SqlCryptGetNextKeyId</span></span>|  
|<span data-ttu-id="4f6b4-142">11</span><span class="sxs-lookup"><span data-stu-id="4f6b4-142">11</span></span>|<span data-ttu-id="4f6b4-143">SqlCryptGetKeyInfoByKeyId</span><span class="sxs-lookup"><span data-stu-id="4f6b4-143">SqlCryptGetKeyInfoByKeyId</span></span>|  
|<span data-ttu-id="4f6b4-144">12</span><span class="sxs-lookup"><span data-stu-id="4f6b4-144">12</span></span>|<span data-ttu-id="4f6b4-145">SqlCryptGetKeyInfoByThumb</span><span class="sxs-lookup"><span data-stu-id="4f6b4-145">SqlCryptGetKeyInfoByThumb</span></span>|  
|<span data-ttu-id="4f6b4-146">13</span><span class="sxs-lookup"><span data-stu-id="4f6b4-146">13</span></span>|<span data-ttu-id="4f6b4-147">SqlCryptGetKeyInfoByName</span><span class="sxs-lookup"><span data-stu-id="4f6b4-147">SqlCryptGetKeyInfoByName</span></span>|  
|<span data-ttu-id="4f6b4-148">14</span><span class="sxs-lookup"><span data-stu-id="4f6b4-148">14</span></span>|<span data-ttu-id="4f6b4-149">SqlCryptExportKey</span><span class="sxs-lookup"><span data-stu-id="4f6b4-149">SqlCryptExportKey</span></span>|  
|<span data-ttu-id="4f6b4-150">15</span><span class="sxs-lookup"><span data-stu-id="4f6b4-150">15</span></span>|<span data-ttu-id="4f6b4-151">SqlCryptImportKey</span><span class="sxs-lookup"><span data-stu-id="4f6b4-151">SqlCryptImportKey</span></span>|  
|<span data-ttu-id="4f6b4-152">16</span><span class="sxs-lookup"><span data-stu-id="4f6b4-152">16</span></span>|<span data-ttu-id="4f6b4-153">SqlCryptEncrypt</span><span class="sxs-lookup"><span data-stu-id="4f6b4-153">SqlCryptEncrypt</span></span>|  
|<span data-ttu-id="4f6b4-154">17</span><span class="sxs-lookup"><span data-stu-id="4f6b4-154">17</span></span>|<span data-ttu-id="4f6b4-155">SqlCryptDecrypt</span><span class="sxs-lookup"><span data-stu-id="4f6b4-155">SqlCryptDecrypt</span></span>|  
  
## <a name="user-action"></a><span data-ttu-id="4f6b4-156">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="4f6b4-156">User Action</span></span>  
 <span data-ttu-id="4f6b4-157">暗号化サービス プロバイダーに詳細を問い合わせてください。</span><span class="sxs-lookup"><span data-stu-id="4f6b4-157">Contact the cryptographic provider for more information.</span></span>  
  
  
