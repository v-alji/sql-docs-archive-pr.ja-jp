---
title: MSSQLSERVER_41302 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41302 (Database Engine error)
ms.assetid: 01e75618-afec-4232-ba68-93ab7bc31003
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 751dac91378c002a7e6c6c619ddaf12be8173400
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639537"
---
# <a name="mssqlserver_41302"></a><span data-ttu-id="aae2d-102">MSSQLSERVER_41302</span><span class="sxs-lookup"><span data-stu-id="aae2d-102">MSSQLSERVER_41302</span></span>
    
## <a name="details"></a><span data-ttu-id="aae2d-103">詳細</span><span class="sxs-lookup"><span data-stu-id="aae2d-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="aae2d-104">製品名</span><span class="sxs-lookup"><span data-stu-id="aae2d-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="aae2d-105">イベント ID</span><span class="sxs-lookup"><span data-stu-id="aae2d-105">Event ID</span></span>|<span data-ttu-id="aae2d-106">41302</span><span class="sxs-lookup"><span data-stu-id="aae2d-106">41302</span></span>|  
|<span data-ttu-id="aae2d-107">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="aae2d-107">Event Source</span></span>|<span data-ttu-id="aae2d-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="aae2d-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="aae2d-109">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="aae2d-109">Component</span></span>|<span data-ttu-id="aae2d-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="aae2d-110">SQLEngine</span></span>|  
|<span data-ttu-id="aae2d-111">シンボル名</span><span class="sxs-lookup"><span data-stu-id="aae2d-111">Symbolic Name</span></span>|<span data-ttu-id="aae2d-112">WRITE_WRITE_CONFLICT</span><span class="sxs-lookup"><span data-stu-id="aae2d-112">WRITE_WRITE_CONFLICT</span></span>|  
|<span data-ttu-id="aae2d-113">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="aae2d-113">Message Text</span></span>|<span data-ttu-id="aae2d-114">現在のトランザクションが、このトランザクションが開始してから更新されたレコードを更新しようとしました。</span><span class="sxs-lookup"><span data-stu-id="aae2d-114">The current transaction attempted to update a record that has been updated since this transaction started.</span></span> <span data-ttu-id="aae2d-115">トランザクションは中止されました。</span><span class="sxs-lookup"><span data-stu-id="aae2d-115">The transaction was aborted.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="aae2d-116">説明</span><span class="sxs-lookup"><span data-stu-id="aae2d-116">Explanation</span></span>  
 <span data-ttu-id="aae2d-117">トランザクションで書き込み/書き込みの競合が発生したため、ステートメントが終了しました。</span><span class="sxs-lookup"><span data-stu-id="aae2d-117">The transaction encountered a write/write conflict and the statement terminated.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="aae2d-118">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="aae2d-118">User Action</span></span>  
 <span data-ttu-id="aae2d-119">別のトランザクションで、後で操作を再試行してください。</span><span class="sxs-lookup"><span data-stu-id="aae2d-119">Retry the operation later in a different transaction.</span></span> <span data-ttu-id="aae2d-120">詳細については、「[インメモリ OLTP &#40;インメモリ最適化&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aae2d-120">For more information, see [In-Memory OLTP &#40;In-Memory Optimization&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aae2d-121">参照</span><span class="sxs-lookup"><span data-stu-id="aae2d-121">See Also</span></span>  
 [<span data-ttu-id="aae2d-122">インメモリ OLTP &#40;インメモリ最適化&#41;</span><span class="sxs-lookup"><span data-stu-id="aae2d-122">In-Memory OLTP &#40;In-Memory Optimization&#41;</span></span>](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
