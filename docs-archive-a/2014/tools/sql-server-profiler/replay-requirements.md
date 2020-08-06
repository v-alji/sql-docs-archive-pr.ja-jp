---
title: 再生要件 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- event classes [SQL Server], replaying traces
- traces [SQL Server], replaying
- replaying traces
- TSQL_Replay template [SQL Server]
ms.assetid: 0e01dfc7-84b9-47f6-8bf7-b0656df4fa7d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 65546f6820765286b558d2043e0155a79a07eb58
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737237"
---
# <a name="replay-requirements"></a><span data-ttu-id="4656e-102">再生を実行するための必要条件</span><span class="sxs-lookup"><span data-stu-id="4656e-102">Replay Requirements</span></span>
  <span data-ttu-id="4656e-103">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] または Distributed Replay Utility を使用してトレース データを再生するには、特定のイベント クラスと列のセットがトレースにキャプチャされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="4656e-103">In order to replay trace data with [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] or the Distributed Replay Utility, a specific set of event classes and columns must be captured in the trace.</span></span> <span data-ttu-id="4656e-104">**TSQL_Replay** トレース テンプレートを使用して、後で再生に使用するトレースを構成した場合、これらの設定は既定で有効になります。</span><span class="sxs-lookup"><span data-stu-id="4656e-104">These settings are enabled by default if the **TSQL_Replay** trace template is used to configure a trace that is later used for replay.</span></span> <span data-ttu-id="4656e-105">このトピックでは、これらの設定と、再生を実行するためのその他の必要条件について説明します。</span><span class="sxs-lookup"><span data-stu-id="4656e-105">This topic describes these settings and other replay requirements.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4656e-106">(アクティブなコンカレント接続が多数ある、またはスループットが高い) 集中型の OLTP アプリケーションを再生する場合は、Distributed Replay Utility を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="4656e-106">We recommend using the Distributed Replay Utility for replaying an intensive OLTP application (with many active concurrent connections or high throughput).</span></span> <span data-ttu-id="4656e-107">Distributed Replay Utility では、複数のコンピューターからのトレース データを再生し、ミッションクリティカルなワークロードをより正確にシミュレートできます。</span><span class="sxs-lookup"><span data-stu-id="4656e-107">The Distributed Replay Utility can replay trace data from multiple computers, better simulating a mission-critical workload.</span></span> <span data-ttu-id="4656e-108">詳細については、「 [SQL Server Distributed Replay](../distributed-replay/sql-server-distributed-replay.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4656e-108">For more information, see [SQL Server Distributed Replay](../distributed-replay/sql-server-distributed-replay.md).</span></span>  
  
## <a name="event-classes-required-for-replay"></a><span data-ttu-id="4656e-109">再生に必要なイベント クラス</span><span class="sxs-lookup"><span data-stu-id="4656e-109">Event Classes Required for Replay</span></span>  
 <span data-ttu-id="4656e-110">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]で再生するには、監視するイベント クラスのほかに、以下の一連のイベント クラスをトレースにキャプチャする必要があります。</span><span class="sxs-lookup"><span data-stu-id="4656e-110">To be replayed by [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], the following set of event classes, in addition to any other event classes you want to monitor, must be captured in the trace:</span></span>  
  
-   <span data-ttu-id="4656e-111">**CursorClose**(サーバー側のカーソルを再生する場合のみ必要)</span><span class="sxs-lookup"><span data-stu-id="4656e-111">**CursorClose (** only required when replaying server-side cursors)</span></span>  
  
-   <span data-ttu-id="4656e-112">**CursorExecute** (サーバー側のカーソルを再生する場合のみ必要)</span><span class="sxs-lookup"><span data-stu-id="4656e-112">**CursorExecute** (only required when replaying server-side cursors)</span></span>  
  
-   <span data-ttu-id="4656e-113">**CursorOpen** (サーバー側のカーソルを再生する場合のみ必要)</span><span class="sxs-lookup"><span data-stu-id="4656e-113">**CursorOpen** (only required when replaying server-side cursors)</span></span>  
  
-   <span data-ttu-id="4656e-114">**CursorPrepare** (サーバー側のカーソルを再生する場合のみ必要)</span><span class="sxs-lookup"><span data-stu-id="4656e-114">**CursorPrepare** (only required when replaying server-side cursors)</span></span>  
  
-   <span data-ttu-id="4656e-115">**CursorUnprepare** (サーバー側のカーソルを再生する場合のみ必要)</span><span class="sxs-lookup"><span data-stu-id="4656e-115">**CursorUnprepare** (only required when replaying server-side cursors)</span></span>  
  
-   <span data-ttu-id="4656e-116">**Audit Login**</span><span class="sxs-lookup"><span data-stu-id="4656e-116">**Audit Login**</span></span>  
  
-   <span data-ttu-id="4656e-117">**Audit Logout**</span><span class="sxs-lookup"><span data-stu-id="4656e-117">**Audit Logout**</span></span>  
  
-   <span data-ttu-id="4656e-118">**ExistingConnection**</span><span class="sxs-lookup"><span data-stu-id="4656e-118">**ExistingConnection**</span></span>  
  
-   <span data-ttu-id="4656e-119">**RPC Output Parameter**</span><span class="sxs-lookup"><span data-stu-id="4656e-119">**RPC Output Parameter**</span></span>  
  
-   <span data-ttu-id="4656e-120">**RPC:Completed**</span><span class="sxs-lookup"><span data-stu-id="4656e-120">**RPC:Completed**</span></span>  
  
-   <span data-ttu-id="4656e-121">**RPC:Starting**</span><span class="sxs-lookup"><span data-stu-id="4656e-121">**RPC:Starting**</span></span>  
  
-   <span data-ttu-id="4656e-122">**Exec Prepared SQL** (サーバー側の準備された SQL ステートメントを再生する場合のみ必要)</span><span class="sxs-lookup"><span data-stu-id="4656e-122">**Exec Prepared SQL** (only required when replaying server-side prepared SQL statements)</span></span>  
  
-   <span data-ttu-id="4656e-123">**Prepare SQL** (サーバー側の準備された SQL ステートメントを再生する場合のみ必要)</span><span class="sxs-lookup"><span data-stu-id="4656e-123">**Prepare SQL** (only required when replaying server-side prepared SQL statements)</span></span>  
  
-   <span data-ttu-id="4656e-124">**SQL:BatchCompleted**</span><span class="sxs-lookup"><span data-stu-id="4656e-124">**SQL:BatchCompleted**</span></span>  
  
-   <span data-ttu-id="4656e-125">**SQL:BatchStarting**</span><span class="sxs-lookup"><span data-stu-id="4656e-125">**SQL:BatchStarting**</span></span>  
  
## <a name="data-columns-required-for-replay"></a><span data-ttu-id="4656e-126">再生に必要なデータ列</span><span class="sxs-lookup"><span data-stu-id="4656e-126">Data Columns Required for Replay</span></span>  
 <span data-ttu-id="4656e-127">トレースを再生するには、キャプチャ対象となるデータ列のほかに、以下のデータ列をトレースにキャプチャする必要があります。</span><span class="sxs-lookup"><span data-stu-id="4656e-127">In addition to any other data columns you want to capture, the following data columns must be captured in a trace to allow the trace to be replayed:</span></span>  
  
-   <span data-ttu-id="4656e-128">**Event Class**</span><span class="sxs-lookup"><span data-stu-id="4656e-128">**Event Class**</span></span>  
  
-   <span data-ttu-id="4656e-129">**EventSequence**</span><span class="sxs-lookup"><span data-stu-id="4656e-129">**EventSequence**</span></span>  
  
-   <span data-ttu-id="4656e-130">**TextData**</span><span class="sxs-lookup"><span data-stu-id="4656e-130">**TextData**</span></span>  
  
-   <span data-ttu-id="4656e-131">**アプリケーション名**</span><span class="sxs-lookup"><span data-stu-id="4656e-131">**Application Name**</span></span>  
  
-   <span data-ttu-id="4656e-132">**LoginName**</span><span class="sxs-lookup"><span data-stu-id="4656e-132">**LoginName**</span></span>  
  
-   <span data-ttu-id="4656e-133">**DatabaseName**</span><span class="sxs-lookup"><span data-stu-id="4656e-133">**DatabaseName**</span></span>  
  
-   <span data-ttu-id="4656e-134">**[データベース ID]**</span><span class="sxs-lookup"><span data-stu-id="4656e-134">**Database ID**</span></span>  
  
-   <span data-ttu-id="4656e-135">**ClientProcessID**</span><span class="sxs-lookup"><span data-stu-id="4656e-135">**ClientProcessID**</span></span>  
  
-   <span data-ttu-id="4656e-136">**HostName**</span><span class="sxs-lookup"><span data-stu-id="4656e-136">**HostName**</span></span>  
  
-   <span data-ttu-id="4656e-137">**ServerName**</span><span class="sxs-lookup"><span data-stu-id="4656e-137">**ServerName**</span></span>  
  
-   <span data-ttu-id="4656e-138">**Binary Data**</span><span class="sxs-lookup"><span data-stu-id="4656e-138">**Binary Data**</span></span>  
  
-   <span data-ttu-id="4656e-139">**SPID**</span><span class="sxs-lookup"><span data-stu-id="4656e-139">**SPID**</span></span>  
  
-   <span data-ttu-id="4656e-140">**Start Time**</span><span class="sxs-lookup"><span data-stu-id="4656e-140">**Start Time**</span></span>  
  
-   <span data-ttu-id="4656e-141">**EndTime**</span><span class="sxs-lookup"><span data-stu-id="4656e-141">**EndTime**</span></span>  
  
-   <span data-ttu-id="4656e-142">**IsSystem**</span><span class="sxs-lookup"><span data-stu-id="4656e-142">**IsSystem**</span></span>  
  
-   <span data-ttu-id="4656e-143">**NTDomainName**</span><span class="sxs-lookup"><span data-stu-id="4656e-143">**NTDomainName**</span></span>  
  
-   <span data-ttu-id="4656e-144">**NTUserName**</span><span class="sxs-lookup"><span data-stu-id="4656e-144">**NTUserName**</span></span>  
  
-   <span data-ttu-id="4656e-145">**Error**</span><span class="sxs-lookup"><span data-stu-id="4656e-145">**Error**</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4656e-146">再生するデータをトレースにキャプチャする場合は、トレース テンプレート **TSQL_Replay** を使用します。</span><span class="sxs-lookup"><span data-stu-id="4656e-146">Use the trace template **TSQL_Replay** for traces that capture data for replay.</span></span>  
  
## <a name="other-replay-requirements"></a><span data-ttu-id="4656e-147">再生を実行するためのその他の必要条件</span><span class="sxs-lookup"><span data-stu-id="4656e-147">Other Replay Requirements</span></span>  
 <span data-ttu-id="4656e-148">Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]では、必要なイベントおよび列が存在するかどうかを再生時に調べます。</span><span class="sxs-lookup"><span data-stu-id="4656e-148">In Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], replay checks for the presence of required events and columns.</span></span> <span data-ttu-id="4656e-149">この変更によって再生の精度が上がり、必要なデータがない場合でも、再生のトラブルシューティング時に根拠のない作業をしなくて済みます。</span><span class="sxs-lookup"><span data-stu-id="4656e-149">This change helps improve the accuracy of replay and takes the guesswork out of troubleshooting replay when required data is missing.</span></span> <span data-ttu-id="4656e-150">必要なデータがトレースにない場合は、再生によってエラーが返され、ファイルの再生が停止します。</span><span class="sxs-lookup"><span data-stu-id="4656e-150">Replay returns an error and stops replaying a file when required data is missing from a trace.</span></span>  
  
 <span data-ttu-id="4656e-151">最初にトレースしたサーバー (ソース) 以外の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を実行しているサーバーに対してトレースを再生するには、次の条件を満たす必要があります。</span><span class="sxs-lookup"><span data-stu-id="4656e-151">To replay a trace against a server (the target) on which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is running other than the server originally traced (the source), make sure the following has been done:</span></span>  
  
-   <span data-ttu-id="4656e-152">トレースに含まれるすべてのログインとユーザーが、ターゲット コンピューター上の、ソースと同じデータベース内にあらかじめ作成されていること。</span><span class="sxs-lookup"><span data-stu-id="4656e-152">All logins and users contained in the trace must be created already on the target and in the same database as the source.</span></span>  
  
-   <span data-ttu-id="4656e-153">ターゲット コンピューターのすべてのログインとユーザーに、ソース コンピューター上と同じ権限が与えられていること。</span><span class="sxs-lookup"><span data-stu-id="4656e-153">All logins and users in the target must have the same permissions they had in the source.</span></span>  
  
-   <span data-ttu-id="4656e-154">すべてのログイン パスワードが、再生を実行するユーザーと同じであること。</span><span class="sxs-lookup"><span data-stu-id="4656e-154">All login passwords must be the same as those of the user that executes the replay.</span></span>  
  
-   <span data-ttu-id="4656e-155">ターゲット コンピューター上のデータベース ID が、ソース コンピューター上のデータベース ID と同じであること。</span><span class="sxs-lookup"><span data-stu-id="4656e-155">The database IDs on the target ideally should be the same as those on the source.</span></span> <span data-ttu-id="4656e-156">ただし、これらが同じでない場合、トレース内に **DatabaseName** が存在すれば、それに基づいて一致させることができます。</span><span class="sxs-lookup"><span data-stu-id="4656e-156">However, if they are not the same, matching can be performed based on **DatabaseName** if it is present in the trace.</span></span>  
  
-   <span data-ttu-id="4656e-157">トレースに記録されている各ログインの既定データベースが、ターゲット コンピューター上で、ログインの対象データベースにそれぞれ設定されていること。</span><span class="sxs-lookup"><span data-stu-id="4656e-157">The default database for each login contained in the trace must be set (on the target) to the respective target database of the login.</span></span> <span data-ttu-id="4656e-158">たとえば、再生するトレースに、ソース コンピューター上の **Fred_Db**データベースに対する **Fred** というログインについての利用状況が含まれているとします。</span><span class="sxs-lookup"><span data-stu-id="4656e-158">For example, the trace to be replayed contains activity for the login, **Fred**, in the database **Fred_Db** on the source.</span></span> <span data-ttu-id="4656e-159">この場合、ターゲット コンピューター上では、ログイン **Fred**の既定データベースが、 **Fred_Db** に一致するデータベースに設定されていなければなりません (データベース名が異なる場合も同様)。</span><span class="sxs-lookup"><span data-stu-id="4656e-159">Therefore, on the target, the default database for the login, **Fred**, must be set to the database that matches **Fred_Db** (even if the database name is different).</span></span> <span data-ttu-id="4656e-160">ログインの既定データベースを設定するには、 **sp_defaultdb** システム ストアド プロシージャを使用します。</span><span class="sxs-lookup"><span data-stu-id="4656e-160">To set the default database of the login, use the **sp_defaultdb** system stored procedure.</span></span>  
  
 <span data-ttu-id="4656e-161">失われたログインや不正なログインに関連付けられたイベントを再生すると、再生エラーとなります。ただし、再生の処理は継続されます。</span><span class="sxs-lookup"><span data-stu-id="4656e-161">Replaying events associated with missing or incorrect logins results in replay errors, but the replay operation continues.</span></span>  
  
 <span data-ttu-id="4656e-162">トレースの再生に必要な権限の詳細については、「 [SQL Server Profiler の実行に必要な権限](sql-server-profiler.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4656e-162">For information about what permissions are required to replay a trace, see [Permissions Required to Run SQL Server Profiler](sql-server-profiler.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4656e-163">参照</span><span class="sxs-lookup"><span data-stu-id="4656e-163">See Also</span></span>  
 <span data-ttu-id="4656e-164">[トレース テーブルを再生する &#40;SQL Server Profiler&#41;](replay-a-trace-table-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="4656e-164">[Replay a Trace Table &#40;SQL Server Profiler&#41;](replay-a-trace-table-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="4656e-165">[トレース ファイルを再生する &#40;SQL Server Profiler&#41;](replay-a-trace-file-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="4656e-165">[Replay a Trace File &#40;SQL Server Profiler&#41;](replay-a-trace-file-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="4656e-166">[SQL Server イベント クラスの参照](../../relational-databases/event-classes/sql-server-event-class-reference.md) </span><span class="sxs-lookup"><span data-stu-id="4656e-166">[SQL Server Event Class Reference](../../relational-databases/event-classes/sql-server-event-class-reference.md) </span></span>  
 <span data-ttu-id="4656e-167">[sp_defaultdb &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-defaultdb-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="4656e-167">[sp_defaultdb &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-defaultdb-transact-sql) </span></span>  
 [<span data-ttu-id="4656e-168">SQL Server Distributed Replay</span><span class="sxs-lookup"><span data-stu-id="4656e-168">SQL Server Distributed Replay</span></span>](../distributed-replay/sql-server-distributed-replay.md)  
  
  
