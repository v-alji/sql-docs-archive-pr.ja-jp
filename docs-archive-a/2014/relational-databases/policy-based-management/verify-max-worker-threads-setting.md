---
title: max worker threads 設定の検証 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 2d94adfd-3ba1-493a-b29a-b436f9d583df
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 5dbffb87f58d2beb633f43ff18680222ea62cf5e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634442"
---
# <a name="verify-max-worker-threads-setting"></a><span data-ttu-id="53d7a-102">max worker threads 設定の検証</span><span class="sxs-lookup"><span data-stu-id="53d7a-102">Verify Max Worker Threads Setting</span></span>
  <span data-ttu-id="53d7a-103">このルールでは、max worker threads サーバー オプションに不適切な設定がないかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="53d7a-103">This rule checks the max worker threads server option for potentially incorrect settings.</span></span> <span data-ttu-id="53d7a-104">max worker threads オプションに小さい値を設定すると、必要な数のスレッドを確保できなくて着信クライアント要求に適切なタイミングで対応できず、"スレッド不足" に陥る可能性があります。</span><span class="sxs-lookup"><span data-stu-id="53d7a-104">Setting the max worker threads option to a small value may prevent enough threads from servicing incoming client requests in a timely manner and could lead to "thread starvation".</span></span> <span data-ttu-id="53d7a-105">その半面、アクティブな各スレッドは、32 ビット サーバー上で 512 KB、64 ビット サーバー上で最大 4 MB を消費するので、このオプションを大きい値に設定すると、アドレス空間が無駄に使用される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="53d7a-105">However, setting the option to a large value can waste address space, because each active thread consumes 512 KB on 32-bit servers and up to 4 MB on 64-bit servers.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="53d7a-106">ベスト プラクティスと推奨事項</span><span class="sxs-lookup"><span data-stu-id="53d7a-106">Best Practices Recommendations</span></span>  
 <span data-ttu-id="53d7a-107">max worker threads オプションを 0 に設定します。</span><span class="sxs-lookup"><span data-stu-id="53d7a-107">Set the max worker threads option to 0.</span></span> <span data-ttu-id="53d7a-108">この設定により、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、ユーザー要求に基づいてアクティブなワーカー スレッドの適切な数が自動的に決定されます。</span><span class="sxs-lookup"><span data-stu-id="53d7a-108">This enables [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to automatically determine the correct number of active worker threads based on user requests.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="53d7a-109">詳細情報</span><span class="sxs-lookup"><span data-stu-id="53d7a-109">For More Information</span></span>  
 [<span data-ttu-id="53d7a-110">max worker threads サーバー構成オプションの構成</span><span class="sxs-lookup"><span data-stu-id="53d7a-110">Configure the max worker threads Server Configuration Option</span></span>](../../database-engine/configure-windows/configure-the-max-worker-threads-server-configuration-option.md)  
  
## <a name="see-also"></a><span data-ttu-id="53d7a-111">参照</span><span class="sxs-lookup"><span data-stu-id="53d7a-111">See Also</span></span>  
 [<span data-ttu-id="53d7a-112">ポリシーベースの管理を使用したベスト プラクティスの監視と実行</span><span class="sxs-lookup"><span data-stu-id="53d7a-112">Monitor and Enforce Best Practices by Using Policy-Based Management</span></span>](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
