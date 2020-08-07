---
title: Errors and Warnings イベント カテゴリ (データベース エンジン) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Errors and Warnings event category [SQL Server]
- SQL Server event classes, Errors and Warnings event category
- event classes [SQL Server], Errors and Warnings event category
ms.assetid: 249c19b5-af68-4433-80f6-337395176641
author: stevestein
ms.author: sstein
ms.openlocfilehash: d55f37f5401f60ddfeec340af1ae6d532eb6ad01
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719886"
---
# <a name="errors-and-warnings-event-category-database-engine"></a><span data-ttu-id="c7765-102">Errors and Warnings イベント カテゴリ (データベース エンジン)</span><span class="sxs-lookup"><span data-stu-id="c7765-102">Errors and Warnings Event Category (Database Engine)</span></span>
  <span data-ttu-id="c7765-103">**Errors and Warnings** イベント カテゴリには、一般的なエラーおよび警告のイベントが含まれています。</span><span class="sxs-lookup"><span data-stu-id="c7765-103">The **Errors and Warnings** event category contains general error and warning events.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c7765-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="c7765-104">In This Section</span></span>  
  
|<span data-ttu-id="c7765-105">トピック</span><span class="sxs-lookup"><span data-stu-id="c7765-105">Topic</span></span>|<span data-ttu-id="c7765-106">説明</span><span class="sxs-lookup"><span data-stu-id="c7765-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="c7765-107">Attention イベント クラス</span><span class="sxs-lookup"><span data-stu-id="c7765-107">Attention Event Class</span></span>](attention-event-class.md)|<span data-ttu-id="c7765-108">**Attention** イベントが発生したことを示します。</span><span class="sxs-lookup"><span data-stu-id="c7765-108">Indicates that an **Attention** event has occurred.</span></span>|  
|[<span data-ttu-id="c7765-109">Background Job Error イベント クラス</span><span class="sxs-lookup"><span data-stu-id="c7765-109">Background Job Error Event Class</span></span>](background-job-error-event-class.md)|<span data-ttu-id="c7765-110">バックグラウンド ジョブが異常終了したことを示します。</span><span class="sxs-lookup"><span data-stu-id="c7765-110">Indicates that a background job has terminated abnormally.</span></span>|  
|[<span data-ttu-id="c7765-111">Bitmap Warning イベント クラス</span><span class="sxs-lookup"><span data-stu-id="c7765-111">Bitmap Warning Event Class</span></span>](bitmap-warning-event-class.md)|<span data-ttu-id="c7765-112">クエリでビットマップ フィルターが無効になっていることを示します。</span><span class="sxs-lookup"><span data-stu-id="c7765-112">Indicates that bitmap filtering has been disabled in a query.</span></span>|  
|[<span data-ttu-id="c7765-113">Blocked Process Report イベント クラス</span><span class="sxs-lookup"><span data-stu-id="c7765-113">Blocked Process Report Event Class</span></span>](blocked-process-report-event-class.md)|<span data-ttu-id="c7765-114">指定した時間より長い間タスクがブロックされていることを示します。</span><span class="sxs-lookup"><span data-stu-id="c7765-114">Indicates that a task has been blocked for more than a specified amount of time.</span></span>|  
|[<span data-ttu-id="c7765-115">CPU Threshold Exceeded イベント クラス</span><span class="sxs-lookup"><span data-stu-id="c7765-115">CPU Threshold Exceeded Event Class</span></span>](cpu-threshold-exceeded-event-class.md)|<span data-ttu-id="c7765-116">指定された CPU しきい値を超えるクエリがリソース ガバナーによって検出されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="c7765-116">Indicates that the Resource Governor detects a query that exceeds the specified CPU threshold.</span></span>|  
|[<span data-ttu-id="c7765-117">ErrorLog イベント クラス</span><span class="sxs-lookup"><span data-stu-id="c7765-117">ErrorLog Event Class</span></span>](errorlog-event-class.md)|<span data-ttu-id="c7765-118">エラー イベントが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラー ログに記録されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="c7765-118">Indicates that error events have been logged in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log.</span></span>|  
|[<span data-ttu-id="c7765-119">EventLog イベント クラス</span><span class="sxs-lookup"><span data-stu-id="c7765-119">EventLog Event Class</span></span>](eventlog-event-class.md)|<span data-ttu-id="c7765-120">イベントが Windows イベント ログに記録されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="c7765-120">Indicates that events have been logged in the Windows event log.</span></span>|  
|[<span data-ttu-id="c7765-121">Exception イベント クラス</span><span class="sxs-lookup"><span data-stu-id="c7765-121">Exception Event Class</span></span>](exception-event-class.md)|<span data-ttu-id="c7765-122">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]で例外が発生したことを示します。</span><span class="sxs-lookup"><span data-stu-id="c7765-122">Indicates that an exception has occurred in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>|  
|[<span data-ttu-id="c7765-123">Exchange Spill イベント クラス</span><span class="sxs-lookup"><span data-stu-id="c7765-123">Exchange Spill Event Class</span></span>](exchange-spill-event-class.md)|<span data-ttu-id="c7765-124">並列クエリ プランの通信バッファーが tempdb データベースに書き込まれたことを示します。</span><span class="sxs-lookup"><span data-stu-id="c7765-124">Indicates that communication buffers in a parallel query plan have been written to the tempdb database.</span></span>|  
|[<span data-ttu-id="c7765-125">Execution Warnings イベント クラス</span><span class="sxs-lookup"><span data-stu-id="c7765-125">Execution Warnings Event Class</span></span>](execution-warnings-event-class.md)|<span data-ttu-id="c7765-126">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ステートメントまたはストアド プロシージャの実行中にメモリ許可警告が発生したことを示します。</span><span class="sxs-lookup"><span data-stu-id="c7765-126">Indicates that memory grant warnings occurred during the execution of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] statement or stored procedure.</span></span>|  
|[<span data-ttu-id="c7765-127">Hash Warning イベント クラス</span><span class="sxs-lookup"><span data-stu-id="c7765-127">Hash Warning Event Class</span></span>](hash-warning-event-class.md)|<span data-ttu-id="c7765-128">ハッシュ処理中にハッシュの再帰またはハッシュの保留が発生したことを示します。</span><span class="sxs-lookup"><span data-stu-id="c7765-128">Indicates that a hash recursion or hash bailout has occurred during a hashing operation.</span></span>|  
|[<span data-ttu-id="c7765-129">Missing Column Statistics イベント クラス</span><span class="sxs-lookup"><span data-stu-id="c7765-129">Missing Column Statistics Event Class</span></span>](missing-column-statistics-event-class.md)|<span data-ttu-id="c7765-130">オプティマイザーに役立つ列統計が使用できないことを示します。</span><span class="sxs-lookup"><span data-stu-id="c7765-130">Indicates that column statistics that could have been useful for the optimizer are not available.</span></span>|  
|[<span data-ttu-id="c7765-131">Missing Join Predicate イベント クラス</span><span class="sxs-lookup"><span data-stu-id="c7765-131">Missing Join Predicate Event Class</span></span>](missing-join-predicate-event-class.md)|<span data-ttu-id="c7765-132">結合述語がないクエリが実行されていることを示します。</span><span class="sxs-lookup"><span data-stu-id="c7765-132">Indicates that a query is being executed that has no join predicate.</span></span>|  
|[<span data-ttu-id="c7765-133">Sort Warnings イベント クラス</span><span class="sxs-lookup"><span data-stu-id="c7765-133">Sort Warnings Event Class</span></span>](sort-warnings-event-class.md)|<span data-ttu-id="c7765-134">並べ替え操作をメモリ内で処理できないことを示します。</span><span class="sxs-lookup"><span data-stu-id="c7765-134">Indicates that sort operations do not fit into memory.</span></span>|  
|[<span data-ttu-id="c7765-135">User Error Message イベント クラス</span><span class="sxs-lookup"><span data-stu-id="c7765-135">User Error Message Event Class</span></span>](user-error-message-event-class.md)|<span data-ttu-id="c7765-136">ユーザーに対して表示されるエラー メッセージを表示します。</span><span class="sxs-lookup"><span data-stu-id="c7765-136">Displays error messages that are seen by the user.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c7765-137">参照</span><span class="sxs-lookup"><span data-stu-id="c7765-137">See Also</span></span>  
 [<span data-ttu-id="c7765-138">sp_trace_setevent &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="c7765-138">sp_trace_setevent &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
  
