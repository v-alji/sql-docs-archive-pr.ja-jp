---
title: SQL Server 拡張イベント セッション | Microsoft Docs
ms.custom: ''
ms.date: 05/26/2020
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xevents
ms.topic: conceptual
helpviewer_keywords:
- xe
- sessions
- extend events [SQL Server]
ms.assetid: c3c92544-351a-4bce-a06a-1f2a47e494e9
author: rothja
ms.author: jroth
ms.openlocfilehash: 3aab8c57a578ea60829514b575e168bc5a1dd8c7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631912"
---
# <a name="sql-server-extended-events-sessions"></a><span data-ttu-id="f265f-102">SQL Server 拡張イベント セッション</span><span class="sxs-lookup"><span data-stu-id="f265f-102">SQL Server Extended Events Sessions</span></span>
  <span data-ttu-id="f265f-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 拡張イベント セッションは、拡張イベント エンジンをホストしている [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] プロセス内で作成されます。</span><span class="sxs-lookup"><span data-stu-id="f265f-103">A [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Extended Events session is created in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] process hosting the Extended Events engine.</span></span> <span data-ttu-id="f265f-104">拡張イベント インフラストラクチャとその全体的な処理を理解するには、拡張イベント セッションの次の側面に注目します。</span><span class="sxs-lookup"><span data-stu-id="f265f-104">The following aspects of an Extended Events session provide a context for understanding the Extended Events infrastructure and the general processing that takes place:</span></span>  
  
-   <span data-ttu-id="f265f-105">セッション状態。</span><span class="sxs-lookup"><span data-stu-id="f265f-105">Session states.</span></span> <span data-ttu-id="f265f-106">CREATE EVENT SESSION ステートメントおよび ALTER EVENT SESSION ステートメントを実行したときの拡張イベント セッションの各種の状態を表します。</span><span class="sxs-lookup"><span data-stu-id="f265f-106">The different states that an Extended Events session is in when CREATE EVENT SESSION and ALTER EVENT SESSION statements are executed.</span></span>  
  
-   <span data-ttu-id="f265f-107">セッションの内容と特性。</span><span class="sxs-lookup"><span data-stu-id="f265f-107">Session content and characteristics.</span></span> <span data-ttu-id="f265f-108">拡張イベント セッションの内容 (ターゲット、イベントなど) と、これらのオブジェクトがセッション内またはセッション間でどのように関係しているかを表します。</span><span class="sxs-lookup"><span data-stu-id="f265f-108">The content of an Extended Events session, such as targets and events, and how these objects are related in a session or between sessions.</span></span>  
  
## <a name="session-states"></a><span data-ttu-id="f265f-109">セッション状態</span><span class="sxs-lookup"><span data-stu-id="f265f-109">Session States</span></span>  
 <span data-ttu-id="f265f-110">拡張イベント セッションの各種の状態を次の図に示します。</span><span class="sxs-lookup"><span data-stu-id="f265f-110">The following illustration shows the various states of an Extended Events session.</span></span>  

<span data-ttu-id="f265f-111">![拡張イベント セッションの状態](../../database-engine/media/xesessionstate.png "拡張イベント セッションの状態")</span><span class="sxs-lookup"><span data-stu-id="f265f-111">![Extended event session state](../../database-engine/media/xesessionstate.png "Extended event session state")</span></span>

 <span data-ttu-id="f265f-112">前の図を見ると、イベント セッションに対して異なる DDL コマンドが発行されたときに、セッション状態が変化していることがわかります。</span><span class="sxs-lookup"><span data-stu-id="f265f-112">Referring to the preceding figure, note that session state changes as the different DDL commands are issued for an event session.</span></span> <span data-ttu-id="f265f-113">このような状態の変化について次の表で説明します。</span><span class="sxs-lookup"><span data-stu-id="f265f-113">The following table describes these changes in state.</span></span>  
  
|<span data-ttu-id="f265f-114">図ラベル</span><span class="sxs-lookup"><span data-stu-id="f265f-114">Illustration label</span></span>|<span data-ttu-id="f265f-115">DDL ステートメント</span><span class="sxs-lookup"><span data-stu-id="f265f-115">DDL statement</span></span>|<span data-ttu-id="f265f-116">説明</span><span class="sxs-lookup"><span data-stu-id="f265f-116">Description</span></span>|  
|------------------------|-------------------|-----------------|  
|<span data-ttu-id="f265f-117">作成</span><span class="sxs-lookup"><span data-stu-id="f265f-117">Create</span></span>|<span data-ttu-id="f265f-118">CREATE EVENT SESSION</span><span class="sxs-lookup"><span data-stu-id="f265f-118">CREATE EVENT SESSION</span></span>|<span data-ttu-id="f265f-119">CREATE EVENT SESSION によって提供されたメタデータを含むセッション オブジェクトがホスト プロセスによって作成されます。</span><span class="sxs-lookup"><span data-stu-id="f265f-119">The host process creates a session object that contains the metadata provided by CREATE EVENT SESSION.</span></span> <span data-ttu-id="f265f-120">ホスト プロセスは、セッション定義を検証し、ユーザーの権限レベルを検証した後、メタデータを master データベースに格納します。</span><span class="sxs-lookup"><span data-stu-id="f265f-120">The host process validates the session definition, validates the user permission level, and stores the metadata in the master database.</span></span> <span data-ttu-id="f265f-121">このときセッションはまだアクティブではありません。</span><span class="sxs-lookup"><span data-stu-id="f265f-121">At this point the session is not active.</span></span>|  
|<span data-ttu-id="f265f-122">Alter</span><span class="sxs-lookup"><span data-stu-id="f265f-122">Alter</span></span>|<span data-ttu-id="f265f-123">ALTER EVENT SESSION, STATE=START</span><span class="sxs-lookup"><span data-stu-id="f265f-123">ALTER EVENT SESSION, STATE=START</span></span>|<span data-ttu-id="f265f-124">ホスト プロセスによってセッションが開始されます。</span><span class="sxs-lookup"><span data-stu-id="f265f-124">The host process starts the session.</span></span> <span data-ttu-id="f265f-125">ホスト プロセスは、格納されているメタデータを読み取って、セッション定義を検証し、ユーザーの権限レベルを検証して、セッションを作成します。</span><span class="sxs-lookup"><span data-stu-id="f265f-125">The host process reads the stored metadata, validates the session definition, verifies the level of user permission level, and creates the session.</span></span> <span data-ttu-id="f265f-126">イベントやターゲットなどのセッション オブジェクトが読み込まれ、イベント処理がアクティブになります。</span><span class="sxs-lookup"><span data-stu-id="f265f-126">Session objects, such as events and targets, are loaded and event handling is active.</span></span>|  
|<span data-ttu-id="f265f-127">Alter</span><span class="sxs-lookup"><span data-stu-id="f265f-127">Alter</span></span>|<span data-ttu-id="f265f-128">ALTER EVENT SESSION, STATE=STOP</span><span class="sxs-lookup"><span data-stu-id="f265f-128">ALTER EVENT SESSION, STATE=STOP</span></span>|<span data-ttu-id="f265f-129">ホスト プロセスによってアクティブなセッションが停止されます。ただし、メタデータは保持されます。</span><span class="sxs-lookup"><span data-stu-id="f265f-129">The host process stops the active session but retains the metadata.</span></span>|  
|<span data-ttu-id="f265f-130">Drop</span><span class="sxs-lookup"><span data-stu-id="f265f-130">Drop</span></span>|<span data-ttu-id="f265f-131">DROP EVENT SESSION</span><span class="sxs-lookup"><span data-stu-id="f265f-131">DROP EVENT SESSION</span></span>|<span data-ttu-id="f265f-132">Drop (DROP SESSION) では、セッションがアクティブかどうかに応じて、セッションのメタデータを削除するか、メタデータを削除した上でアクティブなセッションを終了します。</span><span class="sxs-lookup"><span data-stu-id="f265f-132">Depending on whether or not the session is active, Drop (DROP SESSION) will delete the metadata and close the active session, or delete the session metadata.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="f265f-133">ALTER EVENT SESSION と DROP EVENT SESSION は、メタデータに適用される場合と、アクティブ セッションとメタデータに適用される場合とがあります。</span><span class="sxs-lookup"><span data-stu-id="f265f-133">Both ALTER EVENT SESSION and DROP EVENT SESSION can be applied to the metadata or to an active session and the metadata.</span></span>  
  
## <a name="session-content-and-characteristics"></a><span data-ttu-id="f265f-134">セッションの内容と特性</span><span class="sxs-lookup"><span data-stu-id="f265f-134">Session Content and Characteristics</span></span>  
 <span data-ttu-id="f265f-135">拡張イベント セッションには暗黙的な境界があり、あるセッションの構成によって、別のセッションの構成が変更されることはありません。</span><span class="sxs-lookup"><span data-stu-id="f265f-135">Extended Event sessions have implied boundaries in that the configuration of one session does not change the configuration of another session.</span></span> <span data-ttu-id="f265f-136">ただし、イベントまたはターゲットを複数のセッションで使用することは可能です。</span><span class="sxs-lookup"><span data-stu-id="f265f-136">However, these boundaries do not prevent an event or target from being used in more than one session.</span></span>  
  
 <span data-ttu-id="f265f-137">次の図は、セッションの内容、およびパッケージとセッションの関係を示しています。</span><span class="sxs-lookup"><span data-stu-id="f265f-137">The following illustration shows session content and the relationship between packages and sessions.</span></span>  
  
 <span data-ttu-id="f265f-138">![セッション内でのオブジェクトの共存と共有です。](../../database-engine/media/xesessions.gif "セッション内でのオブジェクトの共存と共有です。")</span><span class="sxs-lookup"><span data-stu-id="f265f-138">![Object co-existance and sharing in sessions.](../../database-engine/media/xesessions.gif "Object co-existance and sharing in sessions.")</span></span>  
  
 <span data-ttu-id="f265f-139">次の点に注目してください。</span><span class="sxs-lookup"><span data-stu-id="f265f-139">Referring to the preceding illustration, note that:</span></span>  
  
-   <span data-ttu-id="f265f-140">パッケージ オブジェクトとセッション間のマッピングが多対多である。これは、1 つのオブジェクトが複数のセッションに存在できること、および、1 つのセッションに複数のオブジェクトが存在できることを意味します。</span><span class="sxs-lookup"><span data-stu-id="f265f-140">The mapping between package objects and sessions is many to many, which means that an object can appear in several sessions, and a session can contain several objects.</span></span>  
  
-   <span data-ttu-id="f265f-141">同じイベント (イベント 1) またはターゲット (ターゲット 1) を複数のセッションで使用できる。</span><span class="sxs-lookup"><span data-stu-id="f265f-141">The same event (Event 1) or target (Target 1) can be enabled in more than one session.</span></span>  
  
 <span data-ttu-id="f265f-142">セッションには次の特徴があります。</span><span class="sxs-lookup"><span data-stu-id="f265f-142">Sessions have the following characteristics:</span></span>  
  
-   <span data-ttu-id="f265f-143">アクションおよび述語は、セッション単位でイベントにバインドされる。</span><span class="sxs-lookup"><span data-stu-id="f265f-143">Actions and predicates are bound to events on a per-session basis.</span></span> <span data-ttu-id="f265f-144">たとえば、アクション 1 および述語 Z を持つセッション A のイベント 1 は、アクション 2 とアクション 3 を持ち、述語を持たないセッション B のイベント 1 には一切影響しません。</span><span class="sxs-lookup"><span data-stu-id="f265f-144">If you have Event 1 in Session A with Action 1 and Predicate Z, this will not in any way affect having Event 1 in Session B with Action 2 and Action 3 with no predicate.</span></span>  
  
-   <span data-ttu-id="f265f-145">セッションには、バッファリングとディスパッチおよび因果関係の追跡を処理するためのポリシーがアタッチされる。</span><span class="sxs-lookup"><span data-stu-id="f265f-145">Policies are attached to sessions to handle buffering and dispatch, and causality tracking.</span></span>  
  
 <span data-ttu-id="f265f-146">**バッファリングとディスパッチ**</span><span class="sxs-lookup"><span data-stu-id="f265f-146">**Buffering and dispatch**</span></span>  
  
 <span data-ttu-id="f265f-147">バッファリングとは、イベント セッションの実行中にイベント データをどのように格納するかをいいます。</span><span class="sxs-lookup"><span data-stu-id="f265f-147">Buffering refers to how event data is stored while an event session is running.</span></span>  <span data-ttu-id="f265f-148">イベント データに使用するメモリ サイズやイベントの削除ポリシーは、バッファリング ポリシーによって指定されます。</span><span class="sxs-lookup"><span data-stu-id="f265f-148">Buffering policies specify how much memory to use for event data, and the loss policy for the events.</span></span> <span data-ttu-id="f265f-149">ディスパッチとは、ターゲットによって処理される前のイベントがバッファー内に存続する時間のことです。</span><span class="sxs-lookup"><span data-stu-id="f265f-149">Dispatch refers to the amount of time events will stay in buffers before being served to targets for processing.</span></span>  
  
 <span data-ttu-id="f265f-150">**因果関係の追跡**</span><span class="sxs-lookup"><span data-stu-id="f265f-150">**Causality tracking**</span></span>  
  
 <span data-ttu-id="f265f-151">因果関係の追跡は、複数のタスクにわたって作業を追跡する機能です。</span><span class="sxs-lookup"><span data-stu-id="f265f-151">Causality tracking provides the ability to track work across multiple tasks.</span></span> <span data-ttu-id="f265f-152">因果関係の追跡を有効にした場合、発生したイベントには、それぞれシステム全体を通じて一意のアクティビティ ID が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="f265f-152">When causality tracking is enabled, each event fired has a unique activity ID across the system.</span></span> <span data-ttu-id="f265f-153">アクティビティ ID は、GUID 値 (特定のタスクに対して割り当てられ、すべてのイベントを通じて変化しない) とシーケンス番号 (イベントが発生するたびにインクリメントされる) の組み合わせです。</span><span class="sxs-lookup"><span data-stu-id="f265f-153">The activity ID is a combination of a GUID value that remains constant across all events for a task, and a sequence number that is incremented each time an event is fired.</span></span> <span data-ttu-id="f265f-154">あるタスクが原因で別のタスクで作業が必要になった場合、親のアクティビティ ID が子のタスクに送信されます。</span><span class="sxs-lookup"><span data-stu-id="f265f-154">When one task causes work to be done on another, the activity ID of the parent is sent to the child task.</span></span> <span data-ttu-id="f265f-155">子のタスクは、イベントの初回発生時に親のアクティビティ ID を出力します。</span><span class="sxs-lookup"><span data-stu-id="f265f-155">The child task outputs the parent's activity ID the first time it fires an event.</span></span>  
  
 <span data-ttu-id="f265f-156">拡張イベント アーキテクチャは、さまざまなオブジェクトを組み合わせて特定の問題を解決できる柔軟なシステムを提供します。</span><span class="sxs-lookup"><span data-stu-id="f265f-156">The Extended Events architecture provides a flexible system that allows a variety of objects to be used together to solve specific problems.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f265f-157">参照</span><span class="sxs-lookup"><span data-stu-id="f265f-157">See Also</span></span>  
 [<span data-ttu-id="f265f-158">拡張イベント</span><span class="sxs-lookup"><span data-stu-id="f265f-158">Extended Events</span></span>](extended-events.md)  
  
  
