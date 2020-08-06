---
title: MSSQLSERVER_41305 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41305 (Database Engine error)
ms.assetid: a96e5083-ff97-4003-a900-07942454151d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 9c00e20ec220d7fcee0da4e99c2ef35817dae67f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642105"
---
# <a name="mssqlserver_41305"></a><span data-ttu-id="3a719-102">MSSQLSERVER_41305</span><span class="sxs-lookup"><span data-stu-id="3a719-102">MSSQLSERVER_41305</span></span>
    
## <a name="details"></a><span data-ttu-id="3a719-103">詳細</span><span class="sxs-lookup"><span data-stu-id="3a719-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3a719-104">製品名</span><span class="sxs-lookup"><span data-stu-id="3a719-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="3a719-105">イベント ID</span><span class="sxs-lookup"><span data-stu-id="3a719-105">Event ID</span></span>|<span data-ttu-id="3a719-106">41305</span><span class="sxs-lookup"><span data-stu-id="3a719-106">41305</span></span>|  
|<span data-ttu-id="3a719-107">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="3a719-107">Event Source</span></span>|<span data-ttu-id="3a719-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="3a719-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="3a719-109">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="3a719-109">Component</span></span>|<span data-ttu-id="3a719-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="3a719-110">SQLEngine</span></span>|  
|<span data-ttu-id="3a719-111">シンボル名</span><span class="sxs-lookup"><span data-stu-id="3a719-111">Symbolic Name</span></span>|<span data-ttu-id="3a719-112">HK_TX_COMMIT_RR_VALIDATION</span><span class="sxs-lookup"><span data-stu-id="3a719-112">HK_TX_COMMIT_RR_VALIDATION</span></span>|  
|<span data-ttu-id="3a719-113">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="3a719-113">Message Text</span></span>|<span data-ttu-id="3a719-114">現在のトランザクションは、REPEATABLE READ の検証の失敗が原因でコミットされませんでした。</span><span class="sxs-lookup"><span data-stu-id="3a719-114">The current transaction failed to commit due to a repeatable read validation failure.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="3a719-115">説明</span><span class="sxs-lookup"><span data-stu-id="3a719-115">Explanation</span></span>  
 <span data-ttu-id="3a719-116">検証エラーが発生したため、トランザクションに失敗しました。</span><span class="sxs-lookup"><span data-stu-id="3a719-116">The transaction encountered a validation failure and is now doomed.</span></span>  
  
 <span data-ttu-id="3a719-117">詳細については、「[インメモリ OLTP &#40;インメモリ最適化&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3a719-117">For more information, see [In-Memory OLTP &#40;In-Memory Optimization&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="3a719-118">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="3a719-118">User Action</span></span>  
 <span data-ttu-id="3a719-119">エラーが発生したトランザクションを再試行してください。</span><span class="sxs-lookup"><span data-stu-id="3a719-119">Retry the failed transaction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a719-120">参照</span><span class="sxs-lookup"><span data-stu-id="3a719-120">See Also</span></span>  
 [<span data-ttu-id="3a719-121">インメモリ OLTP &#40;インメモリ最適化&#41;</span><span class="sxs-lookup"><span data-stu-id="3a719-121">In-Memory OLTP &#40;In-Memory Optimization&#41;</span></span>](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
