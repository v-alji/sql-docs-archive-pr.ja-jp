---
title: Transactions イベント カテゴリ | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- SQL Server event classes, Transactions event category
- event classes [SQL Server], Transactions event category
- Transactions event category [SQL Server]
ms.assetid: bfc75c5b-7115-49d8-9148-a0c84ee66a9a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3b68a91fb166797c220cb0c4f5cf2607ca267538
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643373"
---
# <a name="transactions-event-category"></a><span data-ttu-id="5082a-102">Transactions イベント カテゴリ</span><span class="sxs-lookup"><span data-stu-id="5082a-102">Transactions Event Category</span></span>
  <span data-ttu-id="5082a-103">**Transactions** イベント カテゴリのイベント クラスを使用すると、トランザクションの状態を監視できます。</span><span class="sxs-lookup"><span data-stu-id="5082a-103">The **Transactions** event classes can be used to monitor the status of transactions.</span></span> <span data-ttu-id="5082a-104">**TM:** というプレフィックスが付いたイベント クラス名は、トランザクション管理のインターフェイス経由で送信されたトランザクション関連の操作を追跡する場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="5082a-104">The event class names that are prefixed with **TM:** are used to track the transaction-related operations that are sent through the transaction management interface.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5082a-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="5082a-105">In This Section</span></span>  
  
|<span data-ttu-id="5082a-106">トピック</span><span class="sxs-lookup"><span data-stu-id="5082a-106">Topic</span></span>|<span data-ttu-id="5082a-107">説明</span><span class="sxs-lookup"><span data-stu-id="5082a-107">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="5082a-108">DTCTransaction イベント クラス</span><span class="sxs-lookup"><span data-stu-id="5082a-108">DTCTransaction Event Class</span></span>](dtctransaction-event-class.md)|<span data-ttu-id="5082a-109">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 分散トランザクション コーディネーター (MS DTC) によってコーディネートされたトランザクションを追跡します。</span><span class="sxs-lookup"><span data-stu-id="5082a-109">Tracks transactions coordinated by the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Distributed Transaction Coordinator (MS DTC).</span></span> <span data-ttu-id="5082a-110">これらは、複数のデータベース間または [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]のインスタンス間で分散されたトランザクションです。</span><span class="sxs-lookup"><span data-stu-id="5082a-110">These are transactions distributed between two or more databases or instances of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span>|  
|[<span data-ttu-id="5082a-111">SQLTransaction イベント クラス</span><span class="sxs-lookup"><span data-stu-id="5082a-111">SQLTransaction Event Class</span></span>](sqltransaction-event-class.md)|<span data-ttu-id="5082a-112">[!INCLUDE[tsql](../../includes/tsql-md.md)] の BEGIN TRAN、COMMIT TRAN、SAVE TRAN、および ROLLBACK TRAN の各ステートメントを追跡します。</span><span class="sxs-lookup"><span data-stu-id="5082a-112">Tracks [!INCLUDE[tsql](../../includes/tsql-md.md)] BEGIN TRAN, COMMIT TRAN, SAVE TRAN, and ROLLBACK TRAN statements.</span></span>|  
|[<span data-ttu-id="5082a-113">TM: Begin Tran Completed イベント クラス</span><span class="sxs-lookup"><span data-stu-id="5082a-113">TM: Begin Tran Completed Event Class</span></span>](tm-begin-tran-completed-event-class.md)|<span data-ttu-id="5082a-114">BEGIN TRANSACTION 要求が完了したことを示します。</span><span class="sxs-lookup"><span data-stu-id="5082a-114">Indicates that a BEGIN TRANSACTION request has completed.</span></span>|  
|[<span data-ttu-id="5082a-115">TM: Begin Tran Starting イベント クラス</span><span class="sxs-lookup"><span data-stu-id="5082a-115">TM: Begin Tran Starting Event Class</span></span>](tm-begin-tran-starting-event-class.md)|<span data-ttu-id="5082a-116">BEGIN TRANSACTION 要求が開始されていることを示します。</span><span class="sxs-lookup"><span data-stu-id="5082a-116">Indicates that a BEGIN TRANSACTION request is starting.</span></span>|  
|[<span data-ttu-id="5082a-117">TM: Commit Tran Completed イベント クラス</span><span class="sxs-lookup"><span data-stu-id="5082a-117">TM: Commit Tran Completed Event Class</span></span>](tm-commit-tran-completed-event-class.md)|<span data-ttu-id="5082a-118">COMMIT TRANSACTION 要求が完了したことを示します。</span><span class="sxs-lookup"><span data-stu-id="5082a-118">Indicates that a COMMIT TRANSACTION request has completed.</span></span>|  
|[<span data-ttu-id="5082a-119">TM: Commit Tran Starting イベント クラス</span><span class="sxs-lookup"><span data-stu-id="5082a-119">TM: Commit Tran Starting Event Class</span></span>](tm-commit-tran-starting-event-class.md)|<span data-ttu-id="5082a-120">COMMIT TRANSACTION 要求が開始されていることを示します。</span><span class="sxs-lookup"><span data-stu-id="5082a-120">Indicates that a COMMIT TRANSACTION request is starting.</span></span>|  
|[<span data-ttu-id="5082a-121">TM: Promote Tran Completed イベント クラス</span><span class="sxs-lookup"><span data-stu-id="5082a-121">TM: Promote Tran Completed Event Class</span></span>](tm-promote-tran-completed-event-class.md)|<span data-ttu-id="5082a-122">PROMOTE TRANSACTION 要求が完了したことを示します。</span><span class="sxs-lookup"><span data-stu-id="5082a-122">Indicates that a PROMOTE TRANSACTION request has completed.</span></span>|  
|[<span data-ttu-id="5082a-123">TM: Promote Tran Starting イベント クラス</span><span class="sxs-lookup"><span data-stu-id="5082a-123">TM: Promote Tran Starting Event Class</span></span>](tm-promote-tran-starting-event-class.md)|<span data-ttu-id="5082a-124">PROMOTE TRANSACTION 要求が開始されていることを示します。</span><span class="sxs-lookup"><span data-stu-id="5082a-124">Indicates that a PROMOTE TRANSACTION request is starting.</span></span>|  
|[<span data-ttu-id="5082a-125">TM: Rollback Tran Completed イベント クラス</span><span class="sxs-lookup"><span data-stu-id="5082a-125">TM: Rollback Tran Completed Event Class</span></span>](tm-rollback-tran-completed-event-class.md)|<span data-ttu-id="5082a-126">ROLLBACK TRANSACTION 要求が完了したことを示します。</span><span class="sxs-lookup"><span data-stu-id="5082a-126">Indicates that a ROLLBACK TRANSACTION request has completed.</span></span>|  
|[<span data-ttu-id="5082a-127">TM: Rollback Tran Starting イベント クラス</span><span class="sxs-lookup"><span data-stu-id="5082a-127">TM: Rollback Tran Starting Event Class</span></span>](tm-rollback-tran-starting-event-class.md)|<span data-ttu-id="5082a-128">ROLLBACK TRANSACTION 要求が開始されていることを示します。</span><span class="sxs-lookup"><span data-stu-id="5082a-128">Indicates that a ROLLBACK TRANSACTION request is starting.</span></span>|  
|[<span data-ttu-id="5082a-129">TM: Save Tran Completed イベント クラス</span><span class="sxs-lookup"><span data-stu-id="5082a-129">TM: Save Tran Completed Event Class</span></span>](tm-save-tran-completed-event-class.md)|<span data-ttu-id="5082a-130">SAVE TRANSACTION 要求が完了したことを示します。</span><span class="sxs-lookup"><span data-stu-id="5082a-130">Indicates that a SAVE TRANSACTION request has completed.</span></span>|  
|[<span data-ttu-id="5082a-131">TM: Save Tran Starting イベント クラス</span><span class="sxs-lookup"><span data-stu-id="5082a-131">TM: Save Tran Starting Event Class</span></span>](tm-save-tran-starting-event-class.md)|<span data-ttu-id="5082a-132">SAVE TRANSACTION 要求が開始されていることを示します。</span><span class="sxs-lookup"><span data-stu-id="5082a-132">Indicates that a SAVE TRANSACTION request is starting.</span></span>|  
|[<span data-ttu-id="5082a-133">TransactionLog イベント クラス</span><span class="sxs-lookup"><span data-stu-id="5082a-133">TransactionLog Event Class</span></span>](transactionlog-event-class.md)|<span data-ttu-id="5082a-134">トランザクションがデータベース トランザクション ログに書き込まれる時点を追跡します。</span><span class="sxs-lookup"><span data-stu-id="5082a-134">Tracks when transactions are written to a database transaction log.</span></span>|  
  
  
