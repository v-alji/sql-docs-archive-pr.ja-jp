---
title: SQL Server 拡張イベント パッケージ | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xevents
ms.topic: conceptual
helpviewer_keywords:
- extended events [SQL Server], packages
- xe
ms.assetid: 6bcb04fc-ca04-48f4-b96a-20b604973447
author: rothja
ms.author: jroth
ms.openlocfilehash: 45c452300c008d486bd1f4ab4c92b5f76b96ecd8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631914"
---
# <a name="sql-server-extended-events-packages"></a><span data-ttu-id="ce57a-102">SQL Server 拡張イベント パッケージ</span><span class="sxs-lookup"><span data-stu-id="ce57a-102">SQL Server Extended Events Packages</span></span>
  <span data-ttu-id="ce57a-103">パッケージは、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 拡張イベント オブジェクトのコンテナーです。</span><span class="sxs-lookup"><span data-stu-id="ce57a-103">A package is a container for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Extended Events objects.</span></span> <span data-ttu-id="ce57a-104">拡張イベント パッケージには、次の 3 種類があります。</span><span class="sxs-lookup"><span data-stu-id="ce57a-104">There are three kinds of Extended Events packages, which include the following:</span></span>  
  
-   <span data-ttu-id="ce57a-105">package0 : 拡張イベント システム オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="ce57a-105">package0 - Extended Events system objects.</span></span> <span data-ttu-id="ce57a-106">既定のパッケージです。</span><span class="sxs-lookup"><span data-stu-id="ce57a-106">This is the default package.</span></span>  
  
-   <span data-ttu-id="ce57a-107">sqlserver : [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 関連オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="ce57a-107">sqlserver - [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] related objects.</span></span>  
  
-   <span data-ttu-id="ce57a-108">sqlos : [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] オペレーティング システム (SQLOS) 関連オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="ce57a-108">sqlos - [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Operating System (SQLOS) related objects.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ce57a-109">SecAudit パッケージは [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 監査で使用されます。</span><span class="sxs-lookup"><span data-stu-id="ce57a-109">The SecAudit package is used by [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Audit.</span></span> <span data-ttu-id="ce57a-110">パッケージ内のオブジェクトは、拡張イベントのデータ定義言語 (DDL) を通じて提供されることはありません。</span><span class="sxs-lookup"><span data-stu-id="ce57a-110">None of the objects in the package are available through the Extended Events data definition language (DDL).</span></span>  
  
 <span data-ttu-id="ce57a-111">パッケージは、名前、GUID、および、パッケージを含んでいるバイナリ モジュールで識別されます。</span><span class="sxs-lookup"><span data-stu-id="ce57a-111">Packages are identified by a name, a GUID, and the binary module that contains the package.</span></span> <span data-ttu-id="ce57a-112">詳細については、「[sys.dm_xe_packages &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-packages-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ce57a-112">For more information, see [sys.dm_xe_packages &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-packages-transact-sql).</span></span>  
  
 <span data-ttu-id="ce57a-113">パッケージには、次のいずれかまたはすべてのオブジェクトを含めることができます。この点については、このトピックの後半で詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="ce57a-113">A package can contain any or all of the following objects, which are discussed in greater detail later in this topic:</span></span>  
  
-   <span data-ttu-id="ce57a-114">イベント</span><span class="sxs-lookup"><span data-stu-id="ce57a-114">Events</span></span>  
  
-   <span data-ttu-id="ce57a-115">ターゲット</span><span class="sxs-lookup"><span data-stu-id="ce57a-115">Targets</span></span>  
  
-   <span data-ttu-id="ce57a-116">操作</span><span class="sxs-lookup"><span data-stu-id="ce57a-116">Actions</span></span>  
  
-   <span data-ttu-id="ce57a-117">型</span><span class="sxs-lookup"><span data-stu-id="ce57a-117">Types</span></span>  
  
-   <span data-ttu-id="ce57a-118">述語</span><span class="sxs-lookup"><span data-stu-id="ce57a-118">Predicates</span></span>  
  
-   <span data-ttu-id="ce57a-119">マップ</span><span class="sxs-lookup"><span data-stu-id="ce57a-119">Maps</span></span>  
  
 <span data-ttu-id="ce57a-120">1 つのイベント セッションに異なるパッケージのオブジェクトを混在させることもできます。</span><span class="sxs-lookup"><span data-stu-id="ce57a-120">Objects from different packages can be mixed in an event session.</span></span> <span data-ttu-id="ce57a-121">詳細については、「 [SQL Server 拡張イベント セッション](sql-server-extended-events-sessions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ce57a-121">For more information, see [SQL Server Extended Events Sessions](sql-server-extended-events-sessions.md).</span></span>  
  
## <a name="package-contents"></a><span data-ttu-id="ce57a-122">パッケージの内容</span><span class="sxs-lookup"><span data-stu-id="ce57a-122">Package Contents</span></span>  
 <span data-ttu-id="ce57a-123">次の図は、パッケージ内に存在することのできるオブジェクトを示しています。これらは、モジュール内に格納されます。</span><span class="sxs-lookup"><span data-stu-id="ce57a-123">The following illustration shows the objects that can exist in packages, which are contained in a module.</span></span> <span data-ttu-id="ce57a-124">モジュールは、実行可能ファイルかダイナミック リンク ライブラリ (DLL) です。</span><span class="sxs-lookup"><span data-stu-id="ce57a-124">A module can be an executable or a dynamic link library.</span></span>  
  
 <span data-ttu-id="ce57a-125">![モジュール、パッケージ、およびオブジェクトの関係](../../database-engine/media/xepackagesobjects.gif "モジュール、パッケージ、およびオブジェクトの関係")</span><span class="sxs-lookup"><span data-stu-id="ce57a-125">![The relationship of a module, packages, and object](../../database-engine/media/xepackagesobjects.gif "The relationship of a module, packages, and object")</span></span>  
  
### <a name="events"></a><span data-ttu-id="ce57a-126">イベント</span><span class="sxs-lookup"><span data-stu-id="ce57a-126">Events</span></span>  
 <span data-ttu-id="ce57a-127">イベントは、プログラム ( [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]など) の実行パスにおける、監視対象となる地点です。</span><span class="sxs-lookup"><span data-stu-id="ce57a-127">Events are monitoring points of interest in the execution path of a program, such as [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="ce57a-128">イベントは、監視対象の地点まで到達したという事実のほか、イベントが生成された時点の状態情報を伴って発生します。</span><span class="sxs-lookup"><span data-stu-id="ce57a-128">An event firing carries with it the fact that the point of interest was reached, and state information from the time the event was fired.</span></span>  
  
 <span data-ttu-id="ce57a-129">イベントは、トレースを行う目的、またはアクションのトリガーを起動する目的でのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="ce57a-129">Events can be used solely for tracing purposes or for triggering actions.</span></span> <span data-ttu-id="ce57a-130">これらのアクションは同期的に実行される場合と非同期的に実行される場合とがあります。</span><span class="sxs-lookup"><span data-stu-id="ce57a-130">These actions can either be synchronous or asynchronous.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ce57a-131">イベントは、その発生に呼応して起動されるアクションについての情報は一切持ちません。</span><span class="sxs-lookup"><span data-stu-id="ce57a-131">An event does not have any knowledge of the actions that may be triggered in response to the event firing.</span></span>  
  
 <span data-ttu-id="ce57a-132">パッケージが拡張イベントに登録された後で、パッケージ内の一連のイベントを変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="ce57a-132">A set of events in a package cannot change after the package is registered with Extended Events.</span></span>  
  
 <span data-ttu-id="ce57a-133">すべてのイベントは、その内容を定義するバージョン管理されたスキーマを持ちます。</span><span class="sxs-lookup"><span data-stu-id="ce57a-133">All events have a versioned schema which defines their contents.</span></span> <span data-ttu-id="ce57a-134">このスキーマは、適切に定義された型を持つイベント列で構成されます。</span><span class="sxs-lookup"><span data-stu-id="ce57a-134">This schema is composed of event columns with well defined types.</span></span> <span data-ttu-id="ce57a-135">特定の型のイベントは、常にそのデータを、スキーマで指定された順序とまったく同じ順序で提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ce57a-135">An event of a specific type must always provide its data in exactly the same order that is specified in the schema.</span></span> <span data-ttu-id="ce57a-136">ただし、イベント ターゲットは、必ずしも提供されたすべてのデータを利用する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="ce57a-136">However, an event target does not have to consume all the data that is provided.</span></span>  
  
#### <a name="event-categorization"></a><span data-ttu-id="ce57a-137">イベントの分類</span><span class="sxs-lookup"><span data-stu-id="ce57a-137">Event Categorization</span></span>  
 <span data-ttu-id="ce57a-138">拡張イベントには、Event Tracing for Windows (ETW) に似たイベント分類モデルが使用されます。</span><span class="sxs-lookup"><span data-stu-id="ce57a-138">Extended Events uses an event categorization model similar to Event Tracing for Windows (ETW).</span></span> <span data-ttu-id="ce57a-139">分類には、チャネルとキーワードという 2 つのイベント プロパティが使用されます。</span><span class="sxs-lookup"><span data-stu-id="ce57a-139">Two event properties are used for categorization, channel and keyword.</span></span> <span data-ttu-id="ce57a-140">これらのプロパティを使用することにより、拡張イベントを ETW やそのツールと連携させることができます。</span><span class="sxs-lookup"><span data-stu-id="ce57a-140">Using these properties supports the integration of Extended Events with ETW and its tools.</span></span>  
  
 <span data-ttu-id="ce57a-141">**チャネル**</span><span class="sxs-lookup"><span data-stu-id="ce57a-141">**Channel**</span></span>  
  
 <span data-ttu-id="ce57a-142">チャネルは、イベントの対象ユーザーを識別します。</span><span class="sxs-lookup"><span data-stu-id="ce57a-142">A channel identifies the audience for an event.</span></span> <span data-ttu-id="ce57a-143">次の表でこれらのチャネルについて説明します。</span><span class="sxs-lookup"><span data-stu-id="ce57a-143">These channels are described in the following table.</span></span>  
  
|<span data-ttu-id="ce57a-144">期間</span><span class="sxs-lookup"><span data-stu-id="ce57a-144">Term</span></span>|<span data-ttu-id="ce57a-145">定義</span><span class="sxs-lookup"><span data-stu-id="ce57a-145">Definition</span></span>|  
|----------|----------------|  
|<span data-ttu-id="ce57a-146">[Admin]</span><span class="sxs-lookup"><span data-stu-id="ce57a-146">Admin</span></span>|<span data-ttu-id="ce57a-147">管理イベントの対象は、主にエンド ユーザー、管理者、およびサポートです。</span><span class="sxs-lookup"><span data-stu-id="ce57a-147">Admin events are primarily targeted to the end users, administrators, and support.</span></span> <span data-ttu-id="ce57a-148">管理チャネルのイベントは、管理者が対応できる明確な解決策が存在する問題を示します。</span><span class="sxs-lookup"><span data-stu-id="ce57a-148">The events that are found in the admin channels indicate a problem with a well-defined solution that an administrator can act on.</span></span> <span data-ttu-id="ce57a-149">たとえば、アプリケーションがプリンターに接続できなかった場合に発生するイベントなどがあります。</span><span class="sxs-lookup"><span data-stu-id="ce57a-149">An example of an admin event is when an application fails to connect to a printer.</span></span> <span data-ttu-id="ce57a-150">これらのイベントには、詳しい解説が付属するか、問題の解決方法をユーザーに伝えるメッセージが関連付けられています。</span><span class="sxs-lookup"><span data-stu-id="ce57a-150">These events are either well-documented or have a message associated with them that tells the reader what to do to rectify the problem.</span></span>|  
|<span data-ttu-id="ce57a-151">運用時</span><span class="sxs-lookup"><span data-stu-id="ce57a-151">Operational</span></span>|<span data-ttu-id="ce57a-152">運用イベントは、問題や事象の分析および診断のために使用されます。</span><span class="sxs-lookup"><span data-stu-id="ce57a-152">Operational events are used for analyzing and diagnosing a problem or occurrence.</span></span> <span data-ttu-id="ce57a-153">これらは、問題や現象に基づいてツールやタスクをトリガーするために使用できます。</span><span class="sxs-lookup"><span data-stu-id="ce57a-153">They can be used to trigger tools or tasks based on the problem or occurrence.</span></span> <span data-ttu-id="ce57a-154">たとえば、プリンターがシステムに追加されたり、システムから削除された場合に発生するイベントなどがあります。</span><span class="sxs-lookup"><span data-stu-id="ce57a-154">An example of an operational event is when a printer is added or removed from a system.</span></span>|  
|<span data-ttu-id="ce57a-155">分析</span><span class="sxs-lookup"><span data-stu-id="ce57a-155">Analytic</span></span>|<span data-ttu-id="ce57a-156">非常に多くの分析イベントが公開されています。</span><span class="sxs-lookup"><span data-stu-id="ce57a-156">Analytic events are published in high volume.</span></span> <span data-ttu-id="ce57a-157">プログラムの動作を説明するもので、主にパフォーマンス調査に用いられます。</span><span class="sxs-lookup"><span data-stu-id="ce57a-157">They describe program operation and are typically used in performance investigations.</span></span>|  
|<span data-ttu-id="ce57a-158">デバッグ</span><span class="sxs-lookup"><span data-stu-id="ce57a-158">Debug</span></span>|<span data-ttu-id="ce57a-159">デバッグ イベントは、開発者がデバッグ時に問題を診断する目的でのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="ce57a-159">Debug events are used solely by developers to diagnose a problem for debugging.</span></span><br /><br /> <span data-ttu-id="ce57a-160">注: デバッグチャネルのイベントは、実装固有の内部状態データを返します。</span><span class="sxs-lookup"><span data-stu-id="ce57a-160">Note: Events in the Debug channel return internal implementation-specific state data.</span></span> <span data-ttu-id="ce57a-161">スキーマ、およびこのイベントによって返されるデータは、SQL Server の将来のバージョンで変更または無効化される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ce57a-161">The schemas and data that the events return may change or become invalid in future versions of SQL Server.</span></span> <span data-ttu-id="ce57a-162">そのため、デバッグ チャネルのイベントは、SQL Server の将来のバージョンで予告なしに変更または削除されることがあります。</span><span class="sxs-lookup"><span data-stu-id="ce57a-162">Therefore, events in the Debug channel may change or be removed in future versions of SQL Server without notice.</span></span>|  
  
 <span data-ttu-id="ce57a-163">**キーワード**</span><span class="sxs-lookup"><span data-stu-id="ce57a-163">**Keyword**</span></span>  
  
 <span data-ttu-id="ce57a-164">キーワードはアプリケーション固有の情報です。キーワードを使用すると、関連するイベントをより詳細に分類でき、セッションで使用するイベントの指定や取得を簡単に行うことができます。</span><span class="sxs-lookup"><span data-stu-id="ce57a-164">A keyword is application specific and enables a finer-grained grouping of related events, which makes it easier for you to specify and retrieve an event that you want to use in a session.</span></span> <span data-ttu-id="ce57a-165">次のクエリを使用すると、キーワード情報を取得できます。</span><span class="sxs-lookup"><span data-stu-id="ce57a-165">You can use the following query to obtain keyword information.</span></span>  
  
```  
select map_value Keyword from sys.dm_xe_map_values  
where name = 'keyword_map'  
```  
  
> [!NOTE]  
>  <span data-ttu-id="ce57a-166">キーワードを使用すると、現在の SQL トレース イベントのグループを緊密に対応付けることができます。</span><span class="sxs-lookup"><span data-stu-id="ce57a-166">Keywords map closely to the current grouping of SQL Trace events.</span></span>  
  
### <a name="targets"></a><span data-ttu-id="ce57a-167">ターゲット</span><span class="sxs-lookup"><span data-stu-id="ce57a-167">Targets</span></span>  
 <span data-ttu-id="ce57a-168">ターゲットは、イベントのコンシューマーです。</span><span class="sxs-lookup"><span data-stu-id="ce57a-168">Targets are event consumers.</span></span> <span data-ttu-id="ce57a-169">ターゲットは、イベントを開始したスレッド上で同期的に、またはシステムによって提供されたスレッド上で非同期的に、イベントを処理します。</span><span class="sxs-lookup"><span data-stu-id="ce57a-169">Targets process events, either synchronously on the thread that fires the event or asynchronously on a system provided thread.</span></span> <span data-ttu-id="ce57a-170">拡張イベントには、複数のターゲットが用意されており、イベント出力を転送する目的で必要に応じて使用できます。</span><span class="sxs-lookup"><span data-stu-id="ce57a-170">Extended Events provides several targets that you can use as appropriate for directing event output.</span></span> <span data-ttu-id="ce57a-171">詳細については、「 [SQL Server 拡張イベント ターゲット](../../database-engine/sql-server-extended-events-targets.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ce57a-171">For more information, see [SQL Server Extended Events Targets](../../database-engine/sql-server-extended-events-targets.md).</span></span>  
  
### <a name="actions"></a><span data-ttu-id="ce57a-172">操作</span><span class="sxs-lookup"><span data-stu-id="ce57a-172">Actions</span></span>  
 <span data-ttu-id="ce57a-173">アクションは、プログラムがイベントに呼応して実行する特定の (または一連の) 応答です。</span><span class="sxs-lookup"><span data-stu-id="ce57a-173">An action is a programmatic response or series of responses to an event.</span></span> <span data-ttu-id="ce57a-174">アクションはイベントに関連付けられます。各イベントには、それぞれ異なる一連のアクションが関連付けられる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="ce57a-174">Actions are bound to an event, and each event may have a unique set of actions.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ce57a-175">特定のイベント セット用のアクションを、未知のイベントに関連付けることはできません。</span><span class="sxs-lookup"><span data-stu-id="ce57a-175">Actions that are intended for a specific set of events cannot bind to unknown events.</span></span>  
  
 <span data-ttu-id="ce57a-176">イベントに関連付けられたアクションは、そのイベントが発生したスレッドで同期的に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="ce57a-176">An action bound to an event is invoked synchronously on the thread that fired the event.</span></span> <span data-ttu-id="ce57a-177">アクションの種類と機能は多岐にわたります。</span><span class="sxs-lookup"><span data-stu-id="ce57a-177">There are many types of actions and they have a wide range of capabilities.</span></span> <span data-ttu-id="ce57a-178">アクションを使ってできることの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="ce57a-178">Actions can:</span></span>  
  
-   <span data-ttu-id="ce57a-179">スタック ダンプをキャプチャしてデータを検査する。</span><span class="sxs-lookup"><span data-stu-id="ce57a-179">Capture a stack dump and inspect data.</span></span>  
  
-   <span data-ttu-id="ce57a-180">変更可能なストレージを使って状態情報をローカル コンテキストに保存する。</span><span class="sxs-lookup"><span data-stu-id="ce57a-180">Store state information in a local context using variable storage.</span></span>  
  
-   <span data-ttu-id="ce57a-181">イベント データを集計する。</span><span class="sxs-lookup"><span data-stu-id="ce57a-181">Aggregate event data.</span></span>  
  
-   <span data-ttu-id="ce57a-182">イベント データにデータを追加する。</span><span class="sxs-lookup"><span data-stu-id="ce57a-182">Append data to event data.</span></span>  
  
 <span data-ttu-id="ce57a-183">アクションの代表的な使用例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="ce57a-183">Some typical and well known examples of actions are:</span></span>  
  
-   <span data-ttu-id="ce57a-184">スタック ダンプ機能</span><span class="sxs-lookup"><span data-stu-id="ce57a-184">Stack dumper</span></span>  
  
-   <span data-ttu-id="ce57a-185">実行プランの検出 ([!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のみ)</span><span class="sxs-lookup"><span data-stu-id="ce57a-185">Execution plan detection ([!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] only)</span></span>  
  
-   [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="ce57a-186">スタック コレクション ([!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のみ)</span><span class="sxs-lookup"><span data-stu-id="ce57a-186">stack collection ([!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] only)</span></span>  
  
-   <span data-ttu-id="ce57a-187">実行時の統計計算</span><span class="sxs-lookup"><span data-stu-id="ce57a-187">Run time statistics calculation</span></span>  
  
-   <span data-ttu-id="ce57a-188">例外時のユーザー入力の収集</span><span class="sxs-lookup"><span data-stu-id="ce57a-188">Gather user input on exception</span></span>  
  
### <a name="predicates"></a><span data-ttu-id="ce57a-189">述語</span><span class="sxs-lookup"><span data-stu-id="ce57a-189">Predicates</span></span>  
 <span data-ttu-id="ce57a-190">述語は、処理するイベントを評価するために使用される一連の論理規則です。</span><span class="sxs-lookup"><span data-stu-id="ce57a-190">Predicates are a set of logical rules that are used to evaluate events when they are processed.</span></span> <span data-ttu-id="ce57a-191">拡張イベントのユーザーは、特定の条件に基づいてイベント データを選択的にキャプチャできます。</span><span class="sxs-lookup"><span data-stu-id="ce57a-191">This enables the Extended Events user to selectively capture event data based on specific criteria.</span></span>  
  
 <span data-ttu-id="ce57a-192">述語ではデータをローカル コンテキストに保存できます。そのデータを使って、 *n* 分ごと、またはイベントが *n* 回発生するたびに true を返す述語を作成できます。</span><span class="sxs-lookup"><span data-stu-id="ce57a-192">Predicates can store data in a local context that can be used for creating predicates that return true once every *n* minutes or every *n* times that an event fires.</span></span> <span data-ttu-id="ce57a-193">さらに、このローカル コンテキストの格納域を使用して述語を動的に更新することにより、イベントに同様のデータが格納されていた場合に、それ以上のイベントの発生を抑制することもできます。</span><span class="sxs-lookup"><span data-stu-id="ce57a-193">This local context storage can also be used to dynamically update the predicate, thereby suppressing future event firing if the events contain similar data.</span></span>  
  
 <span data-ttu-id="ce57a-194">述語には、イベント固有のデータに加え、スレッド ID などのコンテキスト情報を取得する機能があります。</span><span class="sxs-lookup"><span data-stu-id="ce57a-194">Predicates have the ability to retrieve context information, such as the thread ID, as well as event specific data.</span></span> <span data-ttu-id="ce57a-195">述語は完全なブール式として評価され、式全体が false であると判明した時点ですぐに結果を返すことができます。</span><span class="sxs-lookup"><span data-stu-id="ce57a-195">Predicates are evaluated as full Boolean expressions, and support short circuiting at the first point where the entire expression is found to be false.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ce57a-196">二次的に作用する述語は、先行する述語が false と判定された場合、評価されない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ce57a-196">Predicates with side effects may not be evaluated if an earlier predicate check fails.</span></span>  
  
### <a name="types"></a><span data-ttu-id="ce57a-197">型</span><span class="sxs-lookup"><span data-stu-id="ce57a-197">Types</span></span>  
 <span data-ttu-id="ce57a-198">データは一連のバイトの集合であるため、そのバイト集合の長さと特性がわからなければ、データを解釈することはできません。</span><span class="sxs-lookup"><span data-stu-id="ce57a-198">Because data is a collection of bytes strung together, the length and characteristics of the byte collection are required in order to interpret the data.</span></span> <span data-ttu-id="ce57a-199">この情報は、Type オブジェクトにカプセル化されています。</span><span class="sxs-lookup"><span data-stu-id="ce57a-199">This information is encapsulated in the Type object.</span></span> <span data-ttu-id="ce57a-200">パッケージ オブジェクトには、次の型が用意されています。</span><span class="sxs-lookup"><span data-stu-id="ce57a-200">The following types are provided for package objects:</span></span>  
  
-   <span data-ttu-id="ce57a-201">event</span><span class="sxs-lookup"><span data-stu-id="ce57a-201">event</span></span>  
  
-   <span data-ttu-id="ce57a-202">action</span><span class="sxs-lookup"><span data-stu-id="ce57a-202">action</span></span>  
  
-   <span data-ttu-id="ce57a-203">ターゲット (target)</span><span class="sxs-lookup"><span data-stu-id="ce57a-203">target</span></span>  
  
-   <span data-ttu-id="ce57a-204">pred_source</span><span class="sxs-lookup"><span data-stu-id="ce57a-204">pred_source</span></span>  
  
-   <span data-ttu-id="ce57a-205">pred_compare</span><span class="sxs-lookup"><span data-stu-id="ce57a-205">pred_compare</span></span>  
  
-   <span data-ttu-id="ce57a-206">type</span><span class="sxs-lookup"><span data-stu-id="ce57a-206">type</span></span>  
  
 <span data-ttu-id="ce57a-207">詳細については、「[sys.dm_xe_objects &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-objects-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ce57a-207">For more information, see [sys.dm_xe_objects &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-objects-transact-sql).</span></span>  
  
### <a name="maps"></a><span data-ttu-id="ce57a-208">マップ</span><span class="sxs-lookup"><span data-stu-id="ce57a-208">Maps</span></span>  
 <span data-ttu-id="ce57a-209">内部値はマップ テーブルによって文字列に対応付けられます。これにより、ユーザーは、その値が何を表しているのかを知ることができます。</span><span class="sxs-lookup"><span data-stu-id="ce57a-209">A map table maps an internal value to a string, which enables a user to know what the value represents.</span></span> <span data-ttu-id="ce57a-210">内部値について単に数値を取得できるだけでなく、意味のある説明を取得できます。</span><span class="sxs-lookup"><span data-stu-id="ce57a-210">Instead of only being able to obtain a numeric value, a user can get a meaningful description of the internal value.</span></span> <span data-ttu-id="ce57a-211">次のクエリは、マップ値の取得方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="ce57a-211">The following query shows how to obtain map values.</span></span>  
  
```  
select map_key, map_value from sys.dm_xe_map_values  
where name = 'lock_mode'  
```  
  
 <span data-ttu-id="ce57a-212">以下は前述のクエリの出力結果です。</span><span class="sxs-lookup"><span data-stu-id="ce57a-212">The preceding query produces the following output.</span></span>  
  
 `map_key     map_value`  
  
 `---------------------`  
  
 `0           NL`  
  
 `1           SCH_S`  
  
 `2           SCH_M`  
  
 `3           S`  
  
 `4           U`  
  
 `5           X`  
  
 `6           IS`  
  
 `7           IU`  
  
 `8           IX`  
  
 `9           SIU`  
  
 `10          SIX`  
  
 `11          UIX`  
  
 `12          BU`  
  
 `13          RS_S`  
  
 `14          RS_U`  
  
 `15          RI_NL`  
  
 `16          RI_S`  
  
 `17          RI_U`  
  
 `18          RI_X`  
  
 `19          RX_S`  
  
 `20          RX_U`  
  
 `21          RX_X`  
  
 `21          RX_X`  
  
 <span data-ttu-id="ce57a-213">たとえば、このテーブルに mode という名前の列があり、その値が 5 であると仮定します。</span><span class="sxs-lookup"><span data-stu-id="ce57a-213">Using this table as an example, assume that you have a column named mode, and its value is 5.</span></span> <span data-ttu-id="ce57a-214">このテーブルによると、5 は X に対応しており、そこからロックの種類が Exclusive であることがわかります。</span><span class="sxs-lookup"><span data-stu-id="ce57a-214">The table indicates that 5 maps to X, which means the lock type is Exclusive.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce57a-215">参照</span><span class="sxs-lookup"><span data-stu-id="ce57a-215">See Also</span></span>  
 <span data-ttu-id="ce57a-216">[拡張イベントセッションの SQL Server](sql-server-extended-events-sessions.md) </span><span class="sxs-lookup"><span data-stu-id="ce57a-216">[SQL Server Extended Events Sessions](sql-server-extended-events-sessions.md) </span></span>  
 <span data-ttu-id="ce57a-217">[拡張イベントエンジンの SQL Server](sql-server-extended-events-engine.md) </span><span class="sxs-lookup"><span data-stu-id="ce57a-217">[SQL Server Extended Events Engine](sql-server-extended-events-engine.md) </span></span>  
 [<span data-ttu-id="ce57a-218">SQL Server 拡張イベント ターゲット</span><span class="sxs-lookup"><span data-stu-id="ce57a-218">SQL Server Extended Events Targets</span></span>](../../database-engine/sql-server-extended-events-targets.md)  
  
  
