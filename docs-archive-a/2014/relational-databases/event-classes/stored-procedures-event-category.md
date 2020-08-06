---
title: Stored Procedures イベント カテゴリ | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Stored Procedures event category [SQL Server]
- SQL Server event classes, Stored Procedures event category
- event classes [SQL Server], Stored Procedures event category
ms.assetid: 71bebaa3-a05a-4695-b349-078cecd0949a
author: stevestein
ms.author: sstein
ms.openlocfilehash: df2e0d9a4c077ff16eba09bc5ebb6447d5d27595
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743286"
---
# <a name="stored-procedures-event-category"></a><span data-ttu-id="72b5c-102">Stored Procedures イベント カテゴリ</span><span class="sxs-lookup"><span data-stu-id="72b5c-102">Stored Procedures Event Category</span></span>
  <span data-ttu-id="72b5c-103">**Stored Procedures** イベント カテゴリには、一般的なストアド プロシージャ イベントが含まれています。</span><span class="sxs-lookup"><span data-stu-id="72b5c-103">The **Stored Procedures** event category contains general stored procedure events.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="72b5c-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="72b5c-104">In This Section</span></span>  
  
|<span data-ttu-id="72b5c-105">トピック</span><span class="sxs-lookup"><span data-stu-id="72b5c-105">Topic</span></span>|<span data-ttu-id="72b5c-106">説明</span><span class="sxs-lookup"><span data-stu-id="72b5c-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="72b5c-107">RPC:Completed イベント クラス</span><span class="sxs-lookup"><span data-stu-id="72b5c-107">RPC:Completed Event Class</span></span>](rpc-completed-event-class.md)|<span data-ttu-id="72b5c-108">リモート プロシージャ コール (RPC) が完了したことを示します。</span><span class="sxs-lookup"><span data-stu-id="72b5c-108">Indicates that a remote procedure call (RPC) has been completed.</span></span>|  
|[<span data-ttu-id="72b5c-109">PreConnect:Completed イベント クラス</span><span class="sxs-lookup"><span data-stu-id="72b5c-109">PreConnect:Completed Event Class</span></span>](preconnect-completed-event-class.md)|<span data-ttu-id="72b5c-110">リソース ガバナー分類子関数の実行が終了したことを示します。</span><span class="sxs-lookup"><span data-stu-id="72b5c-110">Indicates when the Resource Governor classifier function finishes execution.</span></span>|  
|[<span data-ttu-id="72b5c-111">PreConnect:Starting イベント クラス</span><span class="sxs-lookup"><span data-stu-id="72b5c-111">PreConnect:Starting Event Class</span></span>](preconnect-starting-event-class.md)|<span data-ttu-id="72b5c-112">リソース ガバナー分類子関数の実行が開始されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="72b5c-112">Indicates when the Resource Governor classifier function starts execution.</span></span>|  
|[<span data-ttu-id="72b5c-113">RPC Output Parameter イベント クラス</span><span class="sxs-lookup"><span data-stu-id="72b5c-113">RPC Output Parameter Event Class</span></span>](rpc-output-parameter-event-class.md)|<span data-ttu-id="72b5c-114">リモート プロシージャ コールの実行後に、その出力パラメーターの値をトレースします。</span><span class="sxs-lookup"><span data-stu-id="72b5c-114">Traces the output parameter values of remote procedure calls after execution.</span></span>|  
|[<span data-ttu-id="72b5c-115">RPC:Starting イベント クラス</span><span class="sxs-lookup"><span data-stu-id="72b5c-115">RPC:Starting Event Class</span></span>](rpc-starting-event-class.md)|<span data-ttu-id="72b5c-116">リモート プロシージャ コールが開始されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="72b5c-116">Indicates that a remote procedure call is starting.</span></span>|  
|[<span data-ttu-id="72b5c-117">SP:CacheHit イベント クラス</span><span class="sxs-lookup"><span data-stu-id="72b5c-117">SP:CacheHit Event Class</span></span>](sp-cachehit-event-class.md)|<span data-ttu-id="72b5c-118">ストアド プロシージャがキャッシュに存在することを示します。</span><span class="sxs-lookup"><span data-stu-id="72b5c-118">Indicates that the stored procedure is in the cache.</span></span>|  
|[<span data-ttu-id="72b5c-119">SP:CacheInsert イベント クラス</span><span class="sxs-lookup"><span data-stu-id="72b5c-119">SP:CacheInsert Event Class</span></span>](sp-cacheinsert-event-class.md)|<span data-ttu-id="72b5c-120">ストアド プロシージャがキャッシュに挿入されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="72b5c-120">Indicates that the stored procedure has been brought into the cache.</span></span>|  
|[<span data-ttu-id="72b5c-121">SP:CacheMiss イベント クラス</span><span class="sxs-lookup"><span data-stu-id="72b5c-121">SP:CacheMiss Event Class</span></span>](sp-cachemiss-event-class.md)|<span data-ttu-id="72b5c-122">ストアド プロシージャがキャッシュで見つからなかったことを示します。</span><span class="sxs-lookup"><span data-stu-id="72b5c-122">Indicates that the stored procedure was not found in the cache.</span></span>|  
|[<span data-ttu-id="72b5c-123">SP:CacheRemove イベント クラス</span><span class="sxs-lookup"><span data-stu-id="72b5c-123">SP:CacheRemove Event Class</span></span>](sp-cacheremove-event-class.md)|<span data-ttu-id="72b5c-124">ストアド プロシージャがキャッシュから削除されていることを示します。</span><span class="sxs-lookup"><span data-stu-id="72b5c-124">Indicates that the stored procedure has been removed from the cache.</span></span>|  
|[<span data-ttu-id="72b5c-125">SP:Completed イベント クラス</span><span class="sxs-lookup"><span data-stu-id="72b5c-125">SP:Completed Event Class</span></span>](sp-completed-event-class.md)|<span data-ttu-id="72b5c-126">ストアド プロシージャの実行が完了したことを示します。</span><span class="sxs-lookup"><span data-stu-id="72b5c-126">Indicates that execution of the stored procedure has completed.</span></span>|  
|[<span data-ttu-id="72b5c-127">SP:Recompile イベント クラス</span><span class="sxs-lookup"><span data-stu-id="72b5c-127">SP:Recompile Event Class</span></span>](sp-recompile-event-class.md)|<span data-ttu-id="72b5c-128">ストアド プロシージャが再コンパイルされたことを示します。</span><span class="sxs-lookup"><span data-stu-id="72b5c-128">Indicates that the stored procedure has been recompiled.</span></span>|  
|[<span data-ttu-id="72b5c-129">SP:Starting イベント クラス</span><span class="sxs-lookup"><span data-stu-id="72b5c-129">SP:Starting Event Class</span></span>](sp-starting-event-class.md)|<span data-ttu-id="72b5c-130">ストアド プロシージャの実行が開始されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="72b5c-130">Indicates that execution of the stored procedure is starting.</span></span>|  
|[<span data-ttu-id="72b5c-131">SP:StmtCompleted イベント クラス</span><span class="sxs-lookup"><span data-stu-id="72b5c-131">SP:StmtCompleted Event Class</span></span>](sp-stmtcompleted-event-class.md)|<span data-ttu-id="72b5c-132">ストアド プロシージャ内の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントが完了したことを示します。</span><span class="sxs-lookup"><span data-stu-id="72b5c-132">Indicates that a [!INCLUDE[tsql](../../includes/tsql-md.md)] statement within a stored procedure has completed.</span></span>|  
|[<span data-ttu-id="72b5c-133">SP:StmtStarting イベント クラス</span><span class="sxs-lookup"><span data-stu-id="72b5c-133">SP:StmtStarting Event Class</span></span>](sp-stmtstarting-event-class.md)|<span data-ttu-id="72b5c-134">ストアド プロシージャ内の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントが開始されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="72b5c-134">Indicates that a [!INCLUDE[tsql](../../includes/tsql-md.md)] statement within a stored procedure has started.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="72b5c-135">参照</span><span class="sxs-lookup"><span data-stu-id="72b5c-135">See Also</span></span>  
 <span data-ttu-id="72b5c-136">[拡張イベント](../extended-events/extended-events.md) </span><span class="sxs-lookup"><span data-stu-id="72b5c-136">[Extended Events](../extended-events/extended-events.md) </span></span>  
 [<span data-ttu-id="72b5c-137">sp_trace_setevent &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="72b5c-137">sp_trace_setevent &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
  
