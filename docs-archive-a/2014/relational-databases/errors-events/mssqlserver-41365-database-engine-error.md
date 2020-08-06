---
title: MSSQLSERVER_41365 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41365 (Database Engine error)
ms.assetid: 4fc7ec15-b722-4e3d-b7f9-3d39d171e96e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1382a6395f1929a5d5552113e07376bcbf80bf35
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642104"
---
# <a name="mssqlserver_41365"></a><span data-ttu-id="2a02b-102">MSSQLSERVER_41365</span><span class="sxs-lookup"><span data-stu-id="2a02b-102">MSSQLSERVER_41365</span></span>
    
## <a name="details"></a><span data-ttu-id="2a02b-103">詳細</span><span class="sxs-lookup"><span data-stu-id="2a02b-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2a02b-104">製品名</span><span class="sxs-lookup"><span data-stu-id="2a02b-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="2a02b-105">イベント ID</span><span class="sxs-lookup"><span data-stu-id="2a02b-105">Event ID</span></span>|<span data-ttu-id="2a02b-106">41365</span><span class="sxs-lookup"><span data-stu-id="2a02b-106">41365</span></span>|  
|<span data-ttu-id="2a02b-107">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="2a02b-107">Event Source</span></span>|<span data-ttu-id="2a02b-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="2a02b-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="2a02b-109">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="2a02b-109">Component</span></span>|<span data-ttu-id="2a02b-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="2a02b-110">SQLEngine</span></span>|  
|<span data-ttu-id="2a02b-111">シンボル名</span><span class="sxs-lookup"><span data-stu-id="2a02b-111">Symbolic Name</span></span>|<span data-ttu-id="2a02b-112">HK_MERGE_SCHEDULE_ERROR</span><span class="sxs-lookup"><span data-stu-id="2a02b-112">HK_MERGE_SCHEDULE_ERROR</span></span>|  
|<span data-ttu-id="2a02b-113">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="2a02b-113">Message Text</span></span>|<span data-ttu-id="2a02b-114">データベース %.\*ls のトランザクション範囲 [%ld, %ld] に対するマージ要求がスケジュールされませんでした。</span><span class="sxs-lookup"><span data-stu-id="2a02b-114">Merge request for transaction range [%ld, %ld] on database %.\*ls was not scheduled.</span></span> <span data-ttu-id="2a02b-115">範囲を表すチェックポイント ファイルは、マージに使用できないか、実行中のマージの一部です。</span><span class="sxs-lookup"><span data-stu-id="2a02b-115">The checkpoint files representing the range are either not available for merge or part of an ongoing merge.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="2a02b-116">説明</span><span class="sxs-lookup"><span data-stu-id="2a02b-116">Explanation</span></span>  
 <span data-ttu-id="2a02b-117">範囲を表すチェックポイント ファイルは、マージに使用できないか、実行中のマージの一部です。</span><span class="sxs-lookup"><span data-stu-id="2a02b-117">The checkpoint files representing the range are either not available for merge or part of an ongoing merge.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="2a02b-118">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="2a02b-118">User Action</span></span>  
 <span data-ttu-id="2a02b-119">同じ要求を再度発行する前に、マージ/待機にもっと適したトランザクション範囲を指定します。</span><span class="sxs-lookup"><span data-stu-id="2a02b-119">Provide a better transaction range for merge/wait before issuing the same request again.</span></span> <span data-ttu-id="2a02b-120">詳細については、「[インメモリ OLTP &#40;インメモリ最適化&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2a02b-120">For more information, see [In-Memory OLTP &#40;In-Memory Optimization&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a02b-121">参照</span><span class="sxs-lookup"><span data-stu-id="2a02b-121">See Also</span></span>  
 [<span data-ttu-id="2a02b-122">インメモリ OLTP &#40;インメモリ最適化&#41;</span><span class="sxs-lookup"><span data-stu-id="2a02b-122">In-Memory OLTP &#40;In-Memory Optimization&#41;</span></span>](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
