---
title: SQL Server Profiler の実行に必要なアクセス許可 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- Profiler [SQL Server Profiler], permissions
- traces [SQL Server], replaying
- replaying traces
- SQL Server Profiler, permissions
- security [SQL Server], SQL Server Profiler
ms.assetid: 5c580a87-88ae-4314-8fe1-54ade83f227f
author: stevestein
ms.author: sstein
ms.openlocfilehash: e73ffe2e127299db9a9e37e48f089aab2cccca52
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737279"
---
# <a name="permissions-required-to-run-sql-server-profiler"></a><span data-ttu-id="6a5c5-102">SQL Server Profiler の実行に必要な権限</span><span class="sxs-lookup"><span data-stu-id="6a5c5-102">Permissions Required to Run SQL Server Profiler</span></span>
  <span data-ttu-id="6a5c5-103">既定では、 [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] の実行には、トレースの作成に使用した Transact-SQL ストアド プロシージャと同じユーザー権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="6a5c5-103">By default, running [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] requires the same user permissions as the Transact-SQL stored procedures that are used to create traces.</span></span> <span data-ttu-id="6a5c5-104">[!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)]を実行するには、ユーザーに ALTER TRACE アクセス権を許可する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6a5c5-104">To run [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)], users must be granted the ALTER TRACE permission.</span></span> <span data-ttu-id="6a5c5-105">詳細については、「[GRANT (サーバーの権限の許可) &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-server-permissions-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6a5c5-105">For more information, see [GRANT Server Permissions &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-server-permissions-transact-sql).</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="6a5c5-106">SHOWPLAN 権限、ALTER TRACE 権限、または VIEW SERVER STATE 権限を持つユーザーは、プラン表示出力にキャプチャされたクエリを表示できます。</span><span class="sxs-lookup"><span data-stu-id="6a5c5-106">Users who have the SHOWPLAN, the ALTER TRACE, or the VIEW SERVER STATE permission can view queries that are captured in Showplan output.</span></span> <span data-ttu-id="6a5c5-107">これらのクエリには、パスワードなどの機密情報が含まれている場合があります。</span><span class="sxs-lookup"><span data-stu-id="6a5c5-107">These queries may contain sensitive information such as passwords.</span></span> <span data-ttu-id="6a5c5-108">したがって、これらの権限は、機密情報を表示することが認められているユーザー (たとえば db_owner 固定データベース ロールのメンバーや sysadmin 固定サーバー ロールのメンバー) のみに付与することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="6a5c5-108">Therefore, we recommend that you only grant these permissions to users who are authorized to view sensitive information, such as members of the db_owner fixed database role, or members of the sysadmin fixed server role.</span></span> <span data-ttu-id="6a5c5-109">また、プラン表示ファイルまたはプラン表示関連のイベントを含むトレース ファイルのみを保存すること、保存先は NTFS ファイル システムが使用されている場所とすること、および機密情報を表示する権限を持つユーザーのみにアクセスを制限することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="6a5c5-109">Additionally, we recommend that you only save Showplan files or trace files that contain Showplan-related events to a location that uses the NTFS file system, and that you restrict access to users who are authorized to view sensitive information.</span></span>

## <a name="permissions-used-to-replay-traces"></a><span data-ttu-id="6a5c5-110">トレースの再生に使用される権限</span><span class="sxs-lookup"><span data-stu-id="6a5c5-110">Permissions Used to Replay Traces</span></span>
 <span data-ttu-id="6a5c5-111">トレースを再生するには、トレースを再生するユーザーに ALTER TRACE 権限が許可されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="6a5c5-111">Replaying traces also requires that the user who is replaying the trace have the ALTER TRACE permission.</span></span>

 <span data-ttu-id="6a5c5-112">ただし、再生中に、再生されるトレース内で Audit Login イベントが検出されると、 [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] によって EXECUTE AS コマンドが使用されます。</span><span class="sxs-lookup"><span data-stu-id="6a5c5-112">However, during replay, [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] uses the EXECUTE AS command if an Audit Login event is encountered in the trace that is being replayed.</span></span> [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] <span data-ttu-id="6a5c5-113">はログイン イベントに関連付けられたユーザーの権限を借用するために、EXECUTE AS コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="6a5c5-113">uses the EXECUTE AS command to impersonate the user who is associated with the login event.</span></span>

 <span data-ttu-id="6a5c5-114">[!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] によって再生されるトレース内でログイン イベントが検出されると、次の権限のチェックが実行されます。</span><span class="sxs-lookup"><span data-stu-id="6a5c5-114">If [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] encounters a login event in a trace that is being replayed, the following permission checks are performed:</span></span>

1.  <span data-ttu-id="6a5c5-115">ALTER TRACE 権限のある User1 が、トレースの再生を開始します。</span><span class="sxs-lookup"><span data-stu-id="6a5c5-115">User1, who has the ALTER TRACE permission, starts replaying a trace.</span></span>

2.  <span data-ttu-id="6a5c5-116">再生されるトレースで、User2 のログイン イベントが検出されます。</span><span class="sxs-lookup"><span data-stu-id="6a5c5-116">A login event for User2 is encountered in the replayed trace.</span></span>

3.  [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] <span data-ttu-id="6a5c5-117">は User2 の権限を借用するために、EXECUTE AS コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="6a5c5-117">uses the EXECUTE AS command to impersonate User2.</span></span>

4.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="6a5c5-118">は User2 の認証を試みます。認証の結果に応じて、次のいずれかが行われます。</span><span class="sxs-lookup"><span data-stu-id="6a5c5-118">attempts to authenticate User2, and depending on the results, one of the following occurs:</span></span>

    1.  <span data-ttu-id="6a5c5-119">User2 を認証できない場合、 [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] はエラーを返し、User1 としてトレースの再生を続行します。</span><span class="sxs-lookup"><span data-stu-id="6a5c5-119">If User2 cannot be authenticated, [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] returns an error, and continues replaying the trace as User1.</span></span>

    2.  <span data-ttu-id="6a5c5-120">User2 を正しく認証できた場合、User2 としてのトレースの再生を続行します。</span><span class="sxs-lookup"><span data-stu-id="6a5c5-120">If User2 is successfully authenticated, replaying the trace as User2 continues.</span></span>

5.  <span data-ttu-id="6a5c5-121">対象のデータベースで User2 の権限がチェックされます。チェックの結果に応じて、次のいずれかが行われます。</span><span class="sxs-lookup"><span data-stu-id="6a5c5-121">Permissions for User2 are checked on the target database, and depending on the results, one of the following occurs:</span></span>

    1.  <span data-ttu-id="6a5c5-122">User2 が対象のデータベースに権限を所持している場合、権限の借用に成功し、User2 としてトレースが再生されます。</span><span class="sxs-lookup"><span data-stu-id="6a5c5-122">If User2 has permissions on the target database, impersonation has succeeded, and the trace is replayed as User2.</span></span>

    2.  <span data-ttu-id="6a5c5-123">User2 が対象のデータベースに権限を所持していない場合、サーバーではそのデータベースの Guest ユーザーがチェックされます。</span><span class="sxs-lookup"><span data-stu-id="6a5c5-123">If User2 does not have permissions on the target database, the server checks for a Guest user on that database.</span></span>

6.  <span data-ttu-id="6a5c5-124">対象のデータベースに Guest ユーザーが存在するかどうかがチェックされます。チェックの結果に応じて、次のいずれかが行われます。</span><span class="sxs-lookup"><span data-stu-id="6a5c5-124">Existence of a Guest user is checked on the target database, and depending on the results, one of the following occurs:</span></span>

    1.  <span data-ttu-id="6a5c5-125">Guest アカウントが存在する場合、Guest アカウントとしてトレースが再生されます。</span><span class="sxs-lookup"><span data-stu-id="6a5c5-125">If a Guest account exists, the trace is replayed as the Guest account.</span></span>

    2.  <span data-ttu-id="6a5c5-126">対象のデータベースに Guest アカウントが存在しない場合、エラーが返され、User1 としてトレースが再生されます。</span><span class="sxs-lookup"><span data-stu-id="6a5c5-126">If no Guest account exists on the target database, an error is returned and the trace is replayed as User1.</span></span>

 <span data-ttu-id="6a5c5-127">次の図に、トレース再生時の権限のチェック プロセスを示します。</span><span class="sxs-lookup"><span data-stu-id="6a5c5-127">The following diagram shows this process of checking permission when replaying traces:</span></span>

 <span data-ttu-id="6a5c5-128">![SQL Server プロファイラーのトレース再生の権限](../../database-engine/media/replaytracedecisiontree.gif "SQL Server プロファイラーのトレース再生の権限")</span><span class="sxs-lookup"><span data-stu-id="6a5c5-128">![SQL Server Profiler replay trace permissions](../../database-engine/media/replaytracedecisiontree.gif "SQL Server Profiler replay trace permissions")</span></span>

## <a name="see-also"></a><span data-ttu-id="6a5c5-129">参照</span><span class="sxs-lookup"><span data-stu-id="6a5c5-129">See Also</span></span>
 <span data-ttu-id="6a5c5-130">[ストアドプロシージャを SQL Server プロファイラー transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sql-server-profiler-stored-procedures-transact-sql) [replay](replay-traces.md)トレース &#40;トレース[&#40;を作成](create-a-trace-sql-server-profiler.md)SQL Server プロファイラートレース[テーブルを再生](replay-a-trace-table-sql-server-profiler.md)&#41;&#40;トレースファイル SQL Server プロファイラー&#41;[を](replay-a-trace-file-sql-server-profiler.md)再生 &#40;SQL Server プロファイラー</span><span class="sxs-lookup"><span data-stu-id="6a5c5-130">[SQL Server Profiler Stored Procedures &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sql-server-profiler-stored-procedures-transact-sql) [Replay Traces](replay-traces.md) [Create a Trace &#40;SQL Server Profiler&#41;](create-a-trace-sql-server-profiler.md) [Replay a Trace Table &#40;SQL Server Profiler&#41;](replay-a-trace-table-sql-server-profiler.md) [Replay a Trace File &#40;SQL Server Profiler&#41;](replay-a-trace-file-sql-server-profiler.md)</span></span>


