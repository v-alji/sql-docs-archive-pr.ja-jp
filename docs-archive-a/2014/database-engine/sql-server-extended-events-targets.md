---
title: SQL Server 拡張イベントターゲット |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- targets [SQL Server extended events]
- extended events [SQL Server], targets
ms.assetid: e281684c-40d1-4cf9-a0d4-7ea1ecffa384
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 010b7cc29543f266b77aaf180c50173ef9f70346
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632068"
---
# <a name="sql-server-extended-events-targets"></a><span data-ttu-id="5712b-102">SQL Server 拡張イベント ターゲット</span><span class="sxs-lookup"><span data-stu-id="5712b-102">SQL Server Extended Events Targets</span></span>
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="5712b-103">拡張イベント ターゲットは、イベントのコンシューマーです。</span><span class="sxs-lookup"><span data-stu-id="5712b-103">Extended Events targets are event consumers.</span></span> <span data-ttu-id="5712b-104">ターゲットは、ファイルに書き込んだり、イベント データをメモリ バッファーに格納したり、イベント データを集計することができます。</span><span class="sxs-lookup"><span data-stu-id="5712b-104">Targets can write to a file, store event data in a memory buffer, or aggregate event data.</span></span> <span data-ttu-id="5712b-105">ターゲットは、データを同期的または非同期的に処理できます。</span><span class="sxs-lookup"><span data-stu-id="5712b-105">Targets can process data synchronously or asynchronously.</span></span>  
  
 <span data-ttu-id="5712b-106">拡張イベントの設計上、ターゲットは、セッションごとに 1 回だけイベントを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="5712b-106">The Extended Events design ensures that targets are guaranteed to receive events once and only once per session.</span></span>  
  
 <span data-ttu-id="5712b-107">拡張イベント セッションで使用できる、拡張イベントに用意されたターゲットは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="5712b-107">Extended Events provide the following targets that you can use for an Extended Events session:</span></span>  
  
-   [<span data-ttu-id="5712b-108">イベント カウンター</span><span class="sxs-lookup"><span data-stu-id="5712b-108">Event counter</span></span>](../../2014/database-engine/event-counter-target.md)  
  
     <span data-ttu-id="5712b-109">拡張イベント セッション中に発生した、すべての指定されたイベントをカウントします。</span><span class="sxs-lookup"><span data-stu-id="5712b-109">Counts all specified events that occur during an Extended Events session.</span></span> <span data-ttu-id="5712b-110">完全なイベント コレクションのオーバーヘッドを追加しなくても、負荷の特性に関する情報を取得できます。</span><span class="sxs-lookup"><span data-stu-id="5712b-110">Use to obtain information about workload characteristics without adding the overhead of full event collection.</span></span> <span data-ttu-id="5712b-111">これは、同期ターゲットです。</span><span class="sxs-lookup"><span data-stu-id="5712b-111">This is a synchronous target.</span></span>  
  
-   [<span data-ttu-id="5712b-112">イベントファイル</span><span class="sxs-lookup"><span data-stu-id="5712b-112">Event file</span></span>](../../2014/database-engine/event-file-target.md)  
  
     <span data-ttu-id="5712b-113">イベント セッション出力を、メモリ バッファー全体からディスクに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="5712b-113">Use to write event session output from complete memory buffers to disk.</span></span> <span data-ttu-id="5712b-114">これは、非同期ターゲットです。</span><span class="sxs-lookup"><span data-stu-id="5712b-114">This is an asynchronous target.</span></span>  
  
-   [<span data-ttu-id="5712b-115">イベント ペアリング</span><span class="sxs-lookup"><span data-stu-id="5712b-115">Event pairing</span></span>](../../2014/database-engine/event-pairing-target.md)  
  
     <span data-ttu-id="5712b-116">ロックの取得とロックの解放など、対で発生するイベントが数多く存在します。</span><span class="sxs-lookup"><span data-stu-id="5712b-116">Many kinds of events occur in pairs, such as lock acquires and lock releases.</span></span> <span data-ttu-id="5712b-117">指定された 1 対のイベントの組み合わせが一致するかどうかを判定します。</span><span class="sxs-lookup"><span data-stu-id="5712b-117">Use to determine when a specified paired event does not occur in a matched set.</span></span> <span data-ttu-id="5712b-118">これは、非同期ターゲットです。</span><span class="sxs-lookup"><span data-stu-id="5712b-118">This is an asynchronous target.</span></span>  
  
-   [<span data-ttu-id="5712b-119">Windows イベント トレーシング (ETW)</span><span class="sxs-lookup"><span data-stu-id="5712b-119">Event Tracing for Windows (ETW)</span></span>](../relational-databases/extended-events/event-tracing-for-windows-target.md)  
  
     <span data-ttu-id="5712b-120">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] イベントを、Windows オペレーティング システムまたはアプリケーション イベント データと関連付けます。</span><span class="sxs-lookup"><span data-stu-id="5712b-120">Use to correlate [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] events with Windows operating system or application event data.</span></span> <span data-ttu-id="5712b-121">これは、同期ターゲットです。</span><span class="sxs-lookup"><span data-stu-id="5712b-121">This is a synchronous target.</span></span>  
  
-   [<span data-ttu-id="5712b-122">ヒストグラム</span><span class="sxs-lookup"><span data-stu-id="5712b-122">Histogram</span></span>](../../2014/database-engine/histogram-target.md)  
  
     <span data-ttu-id="5712b-123">指定されたイベント列またはアクションに基づいて、指定されたイベントが発生する回数をカウントします。</span><span class="sxs-lookup"><span data-stu-id="5712b-123">Use to count the number of times that a specified event occurs, based on a specified event column or action.</span></span> <span data-ttu-id="5712b-124">これは、非同期ターゲットです。</span><span class="sxs-lookup"><span data-stu-id="5712b-124">This is an asynchronous target.</span></span>  
  
-   [<span data-ttu-id="5712b-125">リングバッファー</span><span class="sxs-lookup"><span data-stu-id="5712b-125">Ring buffer</span></span>](../../2014/database-engine/ring-buffer-target.md)  
  
     <span data-ttu-id="5712b-126">先入れ先出し (FIFO) 順またはイベントごとの FIFO に基づいて、イベント データをメモリに格納します。</span><span class="sxs-lookup"><span data-stu-id="5712b-126">Use to hold the event data in memory on a first-in first-out (FIFO) basis, or on a per-event FIFO basis.</span></span> <span data-ttu-id="5712b-127">これは、非同期ターゲットです。</span><span class="sxs-lookup"><span data-stu-id="5712b-127">This is an asynchronous target.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5712b-128">参照</span><span class="sxs-lookup"><span data-stu-id="5712b-128">See Also</span></span>  
 <span data-ttu-id="5712b-129">[拡張イベント](../relational-databases/extended-events/extended-events.md) </span><span class="sxs-lookup"><span data-stu-id="5712b-129">[Extended Events](../relational-databases/extended-events/extended-events.md) </span></span>  
 <span data-ttu-id="5712b-130">[拡張イベントパッケージの SQL Server](../relational-databases/extended-events/sql-server-extended-events-packages.md) </span><span class="sxs-lookup"><span data-stu-id="5712b-130">[SQL Server Extended Events Packages](../relational-databases/extended-events/sql-server-extended-events-packages.md) </span></span>  
 <span data-ttu-id="5712b-131">[拡張イベントセッションの SQL Server](../relational-databases/extended-events/sql-server-extended-events-sessions.md) </span><span class="sxs-lookup"><span data-stu-id="5712b-131">[SQL Server Extended Events Sessions](../relational-databases/extended-events/sql-server-extended-events-sessions.md) </span></span>  
 [<span data-ttu-id="5712b-132">SQL Server 拡張イベント エンジン</span><span class="sxs-lookup"><span data-stu-id="5712b-132">SQL Server Extended Events Engine</span></span>](../relational-databases/extended-events/sql-server-extended-events-engine.md)  
  
  
