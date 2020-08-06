---
title: Locks イベント カテゴリ | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Locks event category [SQL Server]
- SQL Server event classes, Locks event category
- event classes [SQL Server], Locks event category
- lock escalation [SQL Server], locks event category
ms.assetid: 27d6afa2-7dab-4fe7-a1ad-064b879dc654
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3a202279021e3e6c7c3c44a167792bb9439567aa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633153"
---
# <a name="locks-event-category"></a><span data-ttu-id="4c34d-102">Locks イベント カテゴリ</span><span class="sxs-lookup"><span data-stu-id="4c34d-102">Locks Event Category</span></span>
  <span data-ttu-id="4c34d-103">**Locks** イベント カテゴリのイベント クラスを使用して、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] のインスタンスでのロックの利用状況を監視します。</span><span class="sxs-lookup"><span data-stu-id="4c34d-103">Use the event classes in the **Locks** event category to monitor locking activity in an instance of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span> <span data-ttu-id="4c34d-104">これらのイベント クラスを使用すると、複数のユーザーが同時にデータの読み取りや変更を行うことによって生じるロックの問題を調査できます。</span><span class="sxs-lookup"><span data-stu-id="4c34d-104">These event classes can help you investigate locking problems caused by multiple users reading and modifying data concurrently.</span></span>  
  
 <span data-ttu-id="4c34d-105">[!INCLUDE[ssDE](../../includes/ssde-md.md)] では多数のロックが処理されることが多いため、トレース時に **Locks** イベント クラスがキャプチャされると、大きなオーバーヘッドが発生し、結果としてトレース ファイルまたはトレース テーブルが大きくなります。</span><span class="sxs-lookup"><span data-stu-id="4c34d-105">Because the [!INCLUDE[ssDE](../../includes/ssde-md.md)] often processes many locks, capturing the **Locks** event classes during a trace can incur significant overhead and result in large trace files or tables.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4c34d-106">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="4c34d-106">In This Section</span></span>  
  
|<span data-ttu-id="4c34d-107">トピック</span><span class="sxs-lookup"><span data-stu-id="4c34d-107">Topic</span></span>|<span data-ttu-id="4c34d-108">説明</span><span class="sxs-lookup"><span data-stu-id="4c34d-108">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="4c34d-109">Deadlock Graph イベント クラス</span><span class="sxs-lookup"><span data-stu-id="4c34d-109">Deadlock Graph Event Class</span></span>](deadlock-graph-event-class.md)|<span data-ttu-id="4c34d-110">デッドロックについての XML の説明が提供されます。</span><span class="sxs-lookup"><span data-stu-id="4c34d-110">Provides an XML description of a deadlock.</span></span>|  
|[<span data-ttu-id="4c34d-111">Lock:Acquired イベント クラス</span><span class="sxs-lookup"><span data-stu-id="4c34d-111">Lock:Acquired Event Class</span></span>](lock-acquired-event-class.md)|<span data-ttu-id="4c34d-112">テーブルの行などのリソースに対してロックが取得されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="4c34d-112">Indicates that a lock has been acquired on a resource, such as a row in a table.</span></span>|  
|[<span data-ttu-id="4c34d-113">Lock:Cancel イベント クラス</span><span class="sxs-lookup"><span data-stu-id="4c34d-113">Lock:Cancel Event Class</span></span>](lock-cancel-event-class.md)|<span data-ttu-id="4c34d-114">デッドロックを防ぐなどの理由で、ロックが取得される前に取り消されたロックの要求を追跡します。</span><span class="sxs-lookup"><span data-stu-id="4c34d-114">Tracks requests for locks that were canceled before the lock was acquired (for example, to prevent a deadlock).</span></span>|  
|[<span data-ttu-id="4c34d-115">Lock:Deadlock Chain イベント クラス</span><span class="sxs-lookup"><span data-stu-id="4c34d-115">Lock:Deadlock Chain Event Class</span></span>](lock-deadlock-chain-event-class.md)|<span data-ttu-id="4c34d-116">デッドロック状態が発生した時点と、関与しているオブジェクトを監視します。</span><span class="sxs-lookup"><span data-stu-id="4c34d-116">Monitors when deadlock conditions occur and which objects are involved.</span></span>|  
|[<span data-ttu-id="4c34d-117">Lock:Deadlock イベント クラス</span><span class="sxs-lookup"><span data-stu-id="4c34d-117">Lock:Deadlock Event Class</span></span>](lock-deadlock-event-class.md)|<span data-ttu-id="4c34d-118">別のトランザクションによって既にロックされているリソースに対してトランザクションがロックを要求し、結果としてデッドロックが発生した時点を追跡します。</span><span class="sxs-lookup"><span data-stu-id="4c34d-118">Tracks when a transaction has requested a lock on a resource already locked by another transaction, resulting in a deadlock.</span></span>|  
|[<span data-ttu-id="4c34d-119">Lock:Escalation イベント クラス</span><span class="sxs-lookup"><span data-stu-id="4c34d-119">Lock:Escalation Event Class</span></span>](lock-escalation-event-class.md)|<span data-ttu-id="4c34d-120">細かい単位のロックが大きい単位のロックに変換されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="4c34d-120">Indicates that a finer-grained lock has been converted to a coarser-grained lock.</span></span>|  
|[<span data-ttu-id="4c34d-121">Lock:Released イベント クラス</span><span class="sxs-lookup"><span data-stu-id="4c34d-121">Lock:Released Event Class</span></span>](lock-released-event-class.md)|<span data-ttu-id="4c34d-122">ロックが解除された時点を追跡します。</span><span class="sxs-lookup"><span data-stu-id="4c34d-122">Tracks when a lock is released.</span></span>|  
|[<span data-ttu-id="4c34d-123">Lock:Timeout &#40;timeout &#62; 0&#41; イベント クラス</span><span class="sxs-lookup"><span data-stu-id="4c34d-123">Lock:Timeout &#40;timeout &#62; 0&#41; Event Class</span></span>](lock-timeout-timeout-0-event-class.md)|<span data-ttu-id="4c34d-124">要求されたリソースに対して別のトランザクションによるブロッキング ロックが存在するために、ロック要求が完了しなかった時点を追跡します。</span><span class="sxs-lookup"><span data-stu-id="4c34d-124">Tracks when lock requests cannot be completed because another transaction has a blocking lock on the requested resource.</span></span> <span data-ttu-id="4c34d-125">このイベントは、ロック タイムアウト値が 0 より大きい場合にのみ発生します。</span><span class="sxs-lookup"><span data-stu-id="4c34d-125">This event occurs only in situations where the lock time-out value is greater than zero.</span></span>|  
|[<span data-ttu-id="4c34d-126">Lock:Timeout イベント クラス</span><span class="sxs-lookup"><span data-stu-id="4c34d-126">Lock:Timeout Event Class</span></span>](lock-timeout-event-class.md)|<span data-ttu-id="4c34d-127">要求されたリソースに対して別のトランザクションによるブロッキング ロックが存在するために、ロック要求が完了しなかった時点を追跡します。</span><span class="sxs-lookup"><span data-stu-id="4c34d-127">Tracks when lock requests cannot be completed because another transaction has a blocking lock on the requested resource.</span></span>|  
  
  
