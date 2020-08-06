---
title: MSSQLSERVER_41325 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41325 (Database Engine error)
ms.assetid: 97c6a8bb-139a-44f3-9ed5-f46d047e8ed3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a512d7db6529876259d889d04aabf3d07747cafe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716373"
---
# <a name="mssqlserver_41325"></a><span data-ttu-id="d3e07-102">MSSQLSERVER_41325</span><span class="sxs-lookup"><span data-stu-id="d3e07-102">MSSQLSERVER_41325</span></span>
    
## <a name="details"></a><span data-ttu-id="d3e07-103">詳細</span><span class="sxs-lookup"><span data-stu-id="d3e07-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d3e07-104">製品名</span><span class="sxs-lookup"><span data-stu-id="d3e07-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="d3e07-105">イベント ID</span><span class="sxs-lookup"><span data-stu-id="d3e07-105">Event ID</span></span>|<span data-ttu-id="d3e07-106">41325</span><span class="sxs-lookup"><span data-stu-id="d3e07-106">41325</span></span>|  
|<span data-ttu-id="d3e07-107">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="d3e07-107">Event Source</span></span>|<span data-ttu-id="d3e07-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="d3e07-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="d3e07-109">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="d3e07-109">Component</span></span>|<span data-ttu-id="d3e07-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="d3e07-110">SQLEngine</span></span>|  
|<span data-ttu-id="d3e07-111">シンボル名</span><span class="sxs-lookup"><span data-stu-id="d3e07-111">Symbolic Name</span></span>|<span data-ttu-id="d3e07-112">HK_TX_COMMIT_SR_VALIDATION</span><span class="sxs-lookup"><span data-stu-id="d3e07-112">HK_TX_COMMIT_SR_VALIDATION</span></span>|  
|<span data-ttu-id="d3e07-113">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="d3e07-113">Message Text</span></span>|<span data-ttu-id="d3e07-114">現在のトランザクションは、SERIALIZABLE の検証の失敗が原因でコミットされませんでした。</span><span class="sxs-lookup"><span data-stu-id="d3e07-114">The current transaction failed to commit due to a serializable validation failure.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="d3e07-115">説明</span><span class="sxs-lookup"><span data-stu-id="d3e07-115">Explanation</span></span>  
 <span data-ttu-id="d3e07-116">検証エラーが発生したため、トランザクションに失敗しました。</span><span class="sxs-lookup"><span data-stu-id="d3e07-116">The transaction encountered a validation failure and is now doomed.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d3e07-117">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="d3e07-117">User Action</span></span>  
 <span data-ttu-id="d3e07-118">エラーが発生したトランザクションを再試行してください。</span><span class="sxs-lookup"><span data-stu-id="d3e07-118">Retry the failed transaction.</span></span> <span data-ttu-id="d3e07-119">詳細については、「[インメモリ OLTP &#40;インメモリ最適化&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d3e07-119">For more information, see [In-Memory OLTP &#40;In-Memory Optimization&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3e07-120">参照</span><span class="sxs-lookup"><span data-stu-id="d3e07-120">See Also</span></span>  
 [<span data-ttu-id="d3e07-121">インメモリ OLTP &#40;インメモリ最適化&#41;</span><span class="sxs-lookup"><span data-stu-id="d3e07-121">In-Memory OLTP &#40;In-Memory Optimization&#41;</span></span>](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
