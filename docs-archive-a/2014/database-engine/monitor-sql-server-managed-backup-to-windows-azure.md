---
title: Azure へのマネージバックアップを監視 SQL Server |Microsoft Docs
description: この記事では、Azure への管理されたバックアップ SQL Server 使用してバックアップの全体的な正常性を判断し、エラーを特定するために使用できるツールについて説明します。
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: cfb9e431-7d4c-457c-b090-6f2528b2f315
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: baec99e63c70befde0cfce76e42dd6202ebc0bad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644632"
---
# <a name="monitor-sql-server-managed-backup-to-azure"></a><span data-ttu-id="50707-103">Azure への SQL Server マネージド バックアップの監視</span><span class="sxs-lookup"><span data-stu-id="50707-103">Monitor SQL Server Managed Backup to Azure</span></span>
  [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]<span data-ttu-id="50707-104">では、バックアップ プロセス中に問題やエラーを特定し、可能な限り修正措置によって解消するための方法が組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="50707-104">has built-in measures to identify problems and errors during backup processes and remedy with corrective action when possible.</span></span>  <span data-ttu-id="50707-105">ただし、ユーザーの介入が必要になる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="50707-105">However there are certain situations where user intervention is required.</span></span> <span data-ttu-id="50707-106">このトピックでは、バックアップの全体的な正常性状態を判定し、解決する必要があるエラーを特定するために使用できるツールについて説明します。</span><span class="sxs-lookup"><span data-stu-id="50707-106">This topic describes the tools that you can use to determine the overall health status of backups, and identify any errors that need to be addressed.</span></span>  
  
## <a name="overview-of-ss_smartbackup-built-in-debugging"></a><span data-ttu-id="50707-107">[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]の組み込みデバッグの概要</span><span class="sxs-lookup"><span data-stu-id="50707-107">Overview of [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] Built-in Debugging</span></span>  
 <span data-ttu-id="50707-108">[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]は、スケジュールされたバックアップを定期的に確認して、失敗したバックアップのスケジュールを組み直します。</span><span class="sxs-lookup"><span data-stu-id="50707-108">The [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] periodically reviews scheduled backups and attempts to reschedule any failed backups.</span></span> <span data-ttu-id="50707-109">ストレージアカウントを定期的にポーリングして、データベースの復旧に影響するログチェーンの中断を特定し、それに応じて新しいバックアップをスケジュールします。</span><span class="sxs-lookup"><span data-stu-id="50707-109">It polls the storage account periodically to identify breaks in log chains affecting recoverability of the database, and schedules new backups accordingly.</span></span> <span data-ttu-id="50707-110">また、Azure の調整ポリシーを考慮し、複数のデータベースのバックアップを管理するためのメカニズムが用意されています。</span><span class="sxs-lookup"><span data-stu-id="50707-110">It also takes into account Azure throttling policies, and has mechanisms in place to manage multiple database backups.</span></span> [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]<span data-ttu-id="50707-111">では、拡張イベントを使用してすべてのアクティビティを追跡します。</span><span class="sxs-lookup"><span data-stu-id="50707-111">uses extended events to track all activity.</span></span> <span data-ttu-id="50707-112">[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] エージェントで使用される拡張イベント チャネルには、管理、運用、分析、およびデバッグが含まれます。</span><span class="sxs-lookup"><span data-stu-id="50707-112">The Extended Event channels used by [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] agent include, Admin, Operational, Analytical, and Debug.</span></span> <span data-ttu-id="50707-113">管理カテゴリに分類されるイベントは、通常、エラーに関連しているため、ユーザーの介入を必要とし、既定で有効になっています。</span><span class="sxs-lookup"><span data-stu-id="50707-113">Events that fall under the Admin category usually are related to errors and require user intervention and are enabled by default.</span></span> <span data-ttu-id="50707-114">分析イベントも既定で有効になっていますが、通常、ユーザーの介入を必要とするエラーには関連していません。</span><span class="sxs-lookup"><span data-stu-id="50707-114">Analytical events are also turned on by default, but usually are not related to errors that require user intervention.</span></span> <span data-ttu-id="50707-115">一般的に、運用イベントは情報イベントです。</span><span class="sxs-lookup"><span data-stu-id="50707-115">Operation events are typically informational.</span></span> <span data-ttu-id="50707-116">たとえば、運用イベントには、バックアップのスケジュール設定、バックアップの正常な完了などがあります。デバッグは最も詳細であり、によって内部的に使用され、 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 問題を特定し、必要に応じて修正します。</span><span class="sxs-lookup"><span data-stu-id="50707-116">For example, operational events include scheduling a backup, a successful completion of backup, etc. The Debug is the most verbose and is used internally by [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] to determine issues and correct them if required.</span></span>  
  
### <a name="configure-monitoring-parameters-for-ss_smartbackup"></a><span data-ttu-id="50707-117">[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]の監視パラメーターの構成</span><span class="sxs-lookup"><span data-stu-id="50707-117">Configure Monitoring Parameters for [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]</span></span>  
 <span data-ttu-id="50707-118">**Smart_admin sp_set_parameter**システムストアドプロシージャを使用すると、監視設定を指定できます。</span><span class="sxs-lookup"><span data-stu-id="50707-118">The **smart_admin.sp_set_parameter** system stored procedure allows you to specify monitoring settings.</span></span> <span data-ttu-id="50707-119">以下のセクションでは、拡張イベントの有効化、およびエラーと警告の電子メール通知の有効化の手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="50707-119">The following sections walks through the process of enabling Extended Events,  and enabling email notification for errors and warnings.</span></span>  
  
 <span data-ttu-id="50707-120">**Smart_admin fn_get_parameter**関数を使用すると、特定のパラメーターまたはすべての構成済みパラメーターの現在の設定を取得できます。</span><span class="sxs-lookup"><span data-stu-id="50707-120">The **smart_admin.fn_get_parameter** function can be used to get the current setting for a specific parameter or all configured parameters.</span></span> <span data-ttu-id="50707-121">パラメーターがまだ構成されていない場合は、この関数は何も値を返しません。</span><span class="sxs-lookup"><span data-stu-id="50707-121">If the parameters have never been configured, the function does not return any values.</span></span>  
  
1.  <span data-ttu-id="50707-122">[!INCLUDE[ssDE](../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="50707-122">Connect to the [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="50707-123">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="50707-123">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="50707-124">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="50707-124">Copy and paste the following example into the query window and then click **Execute**.</span></span> <span data-ttu-id="50707-125">これにより、拡張イベントの現在の構成、および電子メール通知が返されます。</span><span class="sxs-lookup"><span data-stu-id="50707-125">This will return the current configuration for Extended Events, and e-mail notifications.</span></span>  
  
```sql
Use msdb  
Go  
SELECT * FROM smart_admin.fn_get_parameter (NULL)  
GO  
```  
  
 <span data-ttu-id="50707-126">詳細については、「smart_admin」を参照してください[。 fn_get_parameter &#40;transact-sql&#41;](/sql/relational-databases/system-functions/managed-backup-fn-get-parameter-transact-sql)</span><span class="sxs-lookup"><span data-stu-id="50707-126">For more information, see [smart_admin.fn_get_parameter &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/managed-backup-fn-get-parameter-transact-sql)</span></span>  
  
### <a name="extended-events-for-monitoring"></a><span data-ttu-id="50707-127">監視のための拡張イベント</span><span class="sxs-lookup"><span data-stu-id="50707-127">Extended Events for Monitoring</span></span>  
 <span data-ttu-id="50707-128">既定では、管理、運用、および分析イベントが有効になっています。</span><span class="sxs-lookup"><span data-stu-id="50707-128">By default, Admin, Operational and Analytical events are turned on.</span></span> <span data-ttu-id="50707-129">問題を解決するために手動による介入が必要なエラーを特定する場合は、管理イベントが最も重大かつ有用です。</span><span class="sxs-lookup"><span data-stu-id="50707-129">Admin events are most critical, useful when identifying errors that require manual intervention to solve the problem.</span></span> <span data-ttu-id="50707-130">運用イベントおよびデバッグ イベントを有効にすることもできますが、これらのイベントは詳細で、フィルターの適用が必要になる可能性がある点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="50707-130">You may want to turn on the operational and debug events but consider that these events are verbose and may require some filtering.</span></span> <span data-ttu-id="50707-131">次の手順では、拡張イベントを使用してログに記録されたイベントを監視する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="50707-131">The following procedures describe how to monitor events logged through Extended Events.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="50707-132">SQL エンジンの拡張イベントとは異なり、[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]では、拡張イベント セッションの概念がサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="50707-132">Unlike Extended Events for SQL Engine, [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] does not support Extended Event session concepts.</span></span> <span data-ttu-id="50707-133">拡張イベントとの対話には、ツールとしてシステム ストアド プロシージャおよびシステム関数を使用します。</span><span class="sxs-lookup"><span data-stu-id="50707-133">System stored procedures and functions are the tools used to interact with extended events.</span></span> <span data-ttu-id="50707-134">また、ログ ディレクトリから拡張イベント ログを表示することもできます。</span><span class="sxs-lookup"><span data-stu-id="50707-134">You can also view the extended event log from the log directory.</span></span>  
  
##### <a name="to-configure-and-view-extended-events"></a><span data-ttu-id="50707-135">拡張イベントを構成および表示するには</span><span class="sxs-lookup"><span data-stu-id="50707-135">To Configure and View Extended Events</span></span>  
  
1.  <span data-ttu-id="50707-136">使用可能な拡張イベント チャネルとその現在の状態を表示するには、次のクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="50707-136">To view available Extended Event channels and their current status by running the following query:</span></span>  
  
    ```sql
    SELECT * FROM smart_admin.fn_get_current_xevent_settings()  
    ```  
  
     <span data-ttu-id="50707-137">このクエリの出力には、イベント名、イベントが構成可能かどうか、およびイベントが現在有効になっているかどうかが表示されます。</span><span class="sxs-lookup"><span data-stu-id="50707-137">The output from this query will display the event_name, whether it is configurable or not, and whether it is currently enabled.</span></span>  <span data-ttu-id="50707-138">詳細については、「smart_admin」を参照してください[。 transact-sql&#41;&#40;fn_get_current_xevent_settings ](/sql/relational-databases/system-functions/managed-backup-fn-get-current-xevent-settings-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="50707-138">For more information, see [smart_admin.fn_get_current_xevent_settings &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/managed-backup-fn-get-current-xevent-settings-transact-sql).</span></span>  
  
2.  <span data-ttu-id="50707-139">デバッグ イベントを有効にするには、次のクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="50707-139">To enable debug events, run the following query:</span></span>  
  
    ```sql
    --  to enable debug events  
    Use msdb;  
    GO 
    EXEC smart_admin.sp_set_parameter 'FileRetentionDebugXevent', 'True'  
    ```  
  
     <span data-ttu-id="50707-140">ストアドプロシージャの詳細については、「smart_admin」を参照してください[。 sp_set_parameter &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/managed-backup-sp-set-parameter-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="50707-140">For more information about the stored procedure, see [smart_admin.sp_set_parameter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/managed-backup-sp-set-parameter-transact-sql).</span></span>  
  
3.  <span data-ttu-id="50707-141">ログに記録されたイベントを表示するには、次のクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="50707-141">To view the logged events run the following query:</span></span>  
  
    ```sql
    --  View all events in the current week  
    Use msdb;  
    Go  
    DECLARE @startofweek datetime  
    DECLARE @endofweek datetime  
    SET @startofweek = DATEADD(Day, 1-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)
    SET @endofweek = DATEADD(Day, 7-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)  
  
    EXEC smart_admin.sp_get_backup_diagnostics @begin_time = @startofweek, @end_time = @endofweek;
    ```  
  
    ```sql
    --  view all admin events  
    Use msdb;  
    Go  
    DECLARE @startofweek datetime  
    DECLARE @endofweek datetime  
    SET @startofweek = DATEADD(Day, 1-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)   
    SET @endofweek = DATEADD(Day, 7-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)  
  
    DECLARE @eventresult TABLE  
    (event_type nvarchar(512),  
    event nvarchar (512),  
    timestamp datetime  
    )  
  
    INSERT INTO @eventresult  
  
    EXEC smart_admin.sp_get_backup_diagnostics @begin_time = @startofweek, @end_time = @endofweek  
  
    SELECT * from @eventresult  
    WHERE event_type LIKE '%admin%'
    ```  
  
### <a name="aggregated-error-countshealth-status"></a><span data-ttu-id="50707-142">集計されたエラー数/正常性状態</span><span class="sxs-lookup"><span data-stu-id="50707-142">Aggregated Error Counts/Health Status</span></span>  
 <span data-ttu-id="50707-143">**Smart_admin fn_get_health_status**関数は、の正常性状態の監視に使用できる各カテゴリの集計されたエラー数のテーブルを返し [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="50707-143">The **smart_admin.fn_get_health_status** function returns a table of aggregated error counts for each category that can be used to monitor the health status of [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)].</span></span> <span data-ttu-id="50707-144">この関数は、このトピックの後半で説明する、システムで構成された電子メール通知メカニズムでも使用されます。</span><span class="sxs-lookup"><span data-stu-id="50707-144">This same function is also used by the system configured e-mail notification mechanism described later in this topic.</span></span>   
<span data-ttu-id="50707-145">これらの集計数は、システムの正常性を監視するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="50707-145">These aggregated counts can be used to monitor system health.</span></span> <span data-ttu-id="50707-146">たとえば、number_of_retention_loops 列が 30 分間 0 だった場合、保有期間の管理に長時間がかかる可能性や保有期間の管理が正常に動作しない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="50707-146">For example, if the number_ of_retention_loops column is 0 in 30 minutes, it is possible that retention management is taking long time or even not working correctly.</span></span> <span data-ttu-id="50707-147">エラー列が 0 以外の場合は問題を示す可能性があるため、拡張イベント ログで問題がないかどうかをチェックする必要があります。</span><span class="sxs-lookup"><span data-stu-id="50707-147">Non-zero error columns may indicate problems and Extended Events logs should be checked to discover the problem.</span></span> <span data-ttu-id="50707-148">または、 **smart_admin. sp_get_backup_diagnostics**ストアドプロシージャを呼び出して、エラーの詳細を確認します。</span><span class="sxs-lookup"><span data-stu-id="50707-148">Alternatively, call **smart_admin.sp_get_backup_diagnostics** stored procedure to find the details of the error.</span></span>  
  
### <a name="using-agent-notification-for-assessing-backup-status-and-health"></a><span data-ttu-id="50707-149">バックアップ状態と正常性の評価にエージェント通知を使用する</span><span class="sxs-lookup"><span data-stu-id="50707-149">Using Agent Notification for Assessing Backup Status and Health</span></span>  
 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]<span data-ttu-id="50707-150">には、SQL Server ポリシー ベースの管理ポリシーに基づく通知メカニズムが含まれています。</span><span class="sxs-lookup"><span data-stu-id="50707-150">includes a notification mechanism that is based on SQL Server policy based management policies.</span></span>  
  
 <span data-ttu-id="50707-151">**前提条件:**</span><span class="sxs-lookup"><span data-stu-id="50707-151">**Prerequisites:**</span></span>  
  
-   <span data-ttu-id="50707-152">この機能を使用するには、データベース メールが必要です。</span><span class="sxs-lookup"><span data-stu-id="50707-152">Database Mail is required to use this functionality.</span></span> <span data-ttu-id="50707-153">SQL Server のインスタンスの DB メールを有効にする方法の詳細については、「 [Configure データベースメール](../relational-databases/database-mail/configure-database-mail.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="50707-153">For more information, about how to enable DB Mail for the instance of SQL Server, see [Configure Database Mail](../relational-databases/database-mail/configure-database-mail.md).</span></span>  
  
-   <span data-ttu-id="50707-154">SQL Server エージェントの警告システムのプロパティは、データベース メールを使用するように設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="50707-154">SQL Server Agent Alert System properties should be set to use Database Mail.</span></span>  
  
 <span data-ttu-id="50707-155">**通知のアーキテクチャ:**</span><span class="sxs-lookup"><span data-stu-id="50707-155">**Notification Architecture:**</span></span>  
  
-   <span data-ttu-id="50707-156">**ポリシーベースの管理:** バックアップの正常性を監視するために、 **Smart Admin システム正常性ポリシー**と**Smart Admin ユーザー操作正常性ポリシー**という2つのポリシーが設定されています。</span><span class="sxs-lookup"><span data-stu-id="50707-156">**Policy Based Management:** Two policies are set to monitor backup health: **Smart Admin System Health Policy**, and the **Smart Admin User Action Health Policy**.</span></span> <span data-ttu-id="50707-157">Smart Admin システム正常性ポリシーは、重大なエラー (SQL 資格情報が存在しない、無効な SQL 資格情報、接続エラーなど) を評価して、システムの正常性を報告します。</span><span class="sxs-lookup"><span data-stu-id="50707-157">The Smart Admin System Health Policy evaluates critical errors like lack of or invalid SQL Credentials, connectivity errors and reports the health of the system.</span></span> <span data-ttu-id="50707-158">これらは、通常、根本的な問題を修正するために手動による操作を必要とします。</span><span class="sxs-lookup"><span data-stu-id="50707-158">These typically require a manual action to correct the underlying issue.</span></span> <span data-ttu-id="50707-159">Smart Admin ユーザー操作正常性ポリシーは、バックアップの破損などの警告を評価します。</span><span class="sxs-lookup"><span data-stu-id="50707-159">The Smart Admin User Action Health Policy evaluates warnings such as corrupted backups, and such.</span></span>  <span data-ttu-id="50707-160">これらは、操作を必要とせず、単なる警告だけの場合もあります。</span><span class="sxs-lookup"><span data-stu-id="50707-160">These may not require any action but just a warning of an event.</span></span> <span data-ttu-id="50707-161">このような問題は [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] エージェントによって自動的に対処されることが予想されます。</span><span class="sxs-lookup"><span data-stu-id="50707-161">It is expected that such issues will be automatically taken care of by [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] agent.</span></span>  
  
-   <span data-ttu-id="50707-162">**SQL Server エージェント**Job: 通知は、3つのジョブステップを持つ SQL Server エージェントジョブを使用して実行されます。</span><span class="sxs-lookup"><span data-stu-id="50707-162">**SQL Server Agent** Job: The notification is performed using a SQL Server Agent job that has three job steps.</span></span> <span data-ttu-id="50707-163">最初のジョブ ステップでは、[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]がデータベースまたはインスタンスに対して構成されているかどうかが検出されます。</span><span class="sxs-lookup"><span data-stu-id="50707-163">In the first job step it detects to see whether [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] is configured for a database or instance.</span></span> <span data-ttu-id="50707-164">[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]が有効であり構成済みであることが検出されると、2 番目のステップが実行されます。これにより、SQL Server ポリシー ベースの管理ポリシーを評価して正常性状態を判断する PowerShell コマンドレットが実行されます。</span><span class="sxs-lookup"><span data-stu-id="50707-164">If it finds [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] enabled and configured, it executes the second step: executes a PowerShell cmdlet that assess the health status by evaluating the SQL Server policy based management policies.</span></span> <span data-ttu-id="50707-165">エラーまたは警告が検出されると失敗になり、これによって 3 番目の手順が開始されます。3 番目の手順では、エラー/警告レポートが含まれた電子メール通知が送信されます。</span><span class="sxs-lookup"><span data-stu-id="50707-165">If it finds either an error or warning, it fails which then triggers the third step: The third step sends out an e-mail notification with the error/warning report.</span></span>  <span data-ttu-id="50707-166">ただし、この SQL Server エージェント ジョブは、既定では有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="50707-166">However this SQL Server Agent job is not enabled by default.</span></span> <span data-ttu-id="50707-167">電子メール通知ジョブを有効にするには、 **smart_admin sp_set_backup_parameter**システムストアドプロシージャを使用します。</span><span class="sxs-lookup"><span data-stu-id="50707-167">To enable the e-mail notification job, use the **smart_admin.sp_set_backup_parameter** system stored procedure.</span></span>  <span data-ttu-id="50707-168">手順については、次で詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="50707-168">The following procedure describes the steps in more detail:</span></span>  
  
##### <a name="enabling-email-notification"></a><span data-ttu-id="50707-169">電子メール通知を有効にする</span><span class="sxs-lookup"><span data-stu-id="50707-169">Enabling Email Notification</span></span>  
  
1.  <span data-ttu-id="50707-170">データベースメールがまだ構成されていない場合は、「 [Configure データベースメール](../relational-databases/database-mail/configure-database-mail.md)」で説明されている手順を使用します。</span><span class="sxs-lookup"><span data-stu-id="50707-170">If Database Mail is not already configured, use the steps described in [Configure Database Mail](../relational-databases/database-mail/configure-database-mail.md).</span></span>  
  
2.  <span data-ttu-id="50707-171">SQL Server 警告システムのメールシステムとしてデータベースを設定する: **SQL Server エージェント**を右クリックし、[**警告システム**] を選択し、[**メールプロファイルを有効にする**] チェックボックス**データベースメール**をオンにして、以前に作成**したメール**プロファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="50707-171">Set database as the Mail System for SQL Server Alert System: Right Click on **SQL Server Agent**, select **Alert System**, check the **Enable mail profile** box, Select **Database Mail** as the **Mail System**, and select a previously created Mail profile.</span></span>  
  
3.  <span data-ttu-id="50707-172">クエリ ウィンドウで次のクエリを実行し、通知の送信先となる電子メール アドレスを指定します。</span><span class="sxs-lookup"><span data-stu-id="50707-172">Run the following query in a query window and provide the e-mail address where you want the notification to be sent to:</span></span>  
  
    ```sql
    Use msdb  
    Go  
    EXEC smart_admin.sp_set_parameter @parameter_name = 'SSMBackup2WANotificationEmailIds', @parameter_value = '<email address>'
    ```  
  
     <span data-ttu-id="50707-173">これにより、SQL Server エージェント ジョブが作成されます。このジョブは、正常性状態を収集し、バックアップでエラーまたは問題が発生しているときに通知を送信するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="50707-173">This creates a SQL Server Agent job that is used to gather health status and send notifications when there is an error or an issue with backups.</span></span>  
  
 <span data-ttu-id="50707-174">データベース メールを有効にして、SQL Server エージェント ジョブによる電子メール通知を設定するサンプル スクリプトを次に示します。</span><span class="sxs-lookup"><span data-stu-id="50707-174">Following is a sample script  to enable DB Mail and set up the e-mail notification through SQL Server Agent Job</span></span>  
  
```sql
-- Prereq: Make sure that SQL Server service runs in a service account that has  
--  access to SMTP Server   
-- set SQL Server service account as domain account   
  
EXEC sp_configure 'show advanced', 1  
RECONFIGURE  
GO  
  
-- Enable DBMail  
EXEC sp_configure 'Database Mail XPs',1  
GO  
RECONFIGURE  
GO  
  
-- Configure DBMail  
DECLARE @emailid NVARCHAR(255)  
-- Note: change this email to your own email id  
SET @emailid = N'emailalias@mycompany.com'  
  
DECLARE @smtpserver NVARCHAR(255)  
SET @smtpserver = N'smtphost.domainname.com'  
  
DECLARE @mailprofile NVARCHAR(255)  
SET @mailprofile = N'my_profile'  
  
EXEC msdb.dbo.sysmail_add_account_sp @account_name=N'myaccount',  
                @email_address = @emailid,  
                @replyto_address = @emailid,  
                @mailserver_name = @smtpserver,  
                @use_default_credentials = 1  
  
EXEC msdb.dbo.sysmail_add_profile_sp @profile_name=@mailprofile  
EXEC msdb.dbo.sysmail_add_profileaccount_sp @profile_name=@mailprofile, @account_name=N'myaccount', @sequence_number=1  
  
-- Set SQL Agent to use DBMail profile  
EXEC msdb.dbo.sp_set_sqlagent_properties @databasemail_profile = @mailprofile  
  
-- Configure Notifications   
EXEC msdb.smart_admin.sp_set_parameter  
@parameter_name = 'SSMBackup2WANotificationEmailIds',  
@parameter_value = @emailid  
  
-- To test is you are receiving notifications  
-- delete few backup files from your storage container, Wait for 15 minutes & see if you get any email notification
```  
  
### <a name="using-powershell-to-setup-custom-health-monitoring"></a><span data-ttu-id="50707-175">PowerShell を使用してカスタムの正常性状態の監視を設定する</span><span class="sxs-lookup"><span data-stu-id="50707-175">Using PowerShell to Setup Custom Health Monitoring</span></span>  
 <span data-ttu-id="50707-176">**Get-sqlsmartadmin**コマンドレットを使用すると、カスタムの正常性監視を作成できます。</span><span class="sxs-lookup"><span data-stu-id="50707-176">The **Test-SqlSmartAdmin** cmdlet can be used to create custom health monitoring.</span></span> <span data-ttu-id="50707-177">たとえば、前のセクションで説明した通知オプションは、インスタンス レベルで構成できます。</span><span class="sxs-lookup"><span data-stu-id="50707-177">For example, the notification option described in the previous section can be configured at the instance level.</span></span>  <span data-ttu-id="50707-178">[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]を使用するよう構成された SQL Server インスタンスが複数ある場合は、PowerShell コマンドレットを使用して、すべてのインスタンスのバックアップの状態と正常性を収集するためのスクリプトを作成できます。</span><span class="sxs-lookup"><span data-stu-id="50707-178">If you have several instances of SQL Server configured to use [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)], the PowerShell cmdlet can be used to create scripts in gather the status and health of backups for all the instances.</span></span>  
  
 <span data-ttu-id="50707-179">**Get-sqlsmartadmin**コマンドレットは、SQL Server ポリシーベースの管理ポリシーによって返されたエラーと警告を評価し、ロールアップされたステータスを報告します。</span><span class="sxs-lookup"><span data-stu-id="50707-179">The **Test-SqlSmartAdmin** cmdlet assesses the errors and warnings returned by the SQL Server Policy Based Management policies and reports out a rolled up status.</span></span>  <span data-ttu-id="50707-180">既定では、このコマンドレットはシステム ポリシーを使用します。</span><span class="sxs-lookup"><span data-stu-id="50707-180">By default this cmdlet uses the system policies.</span></span> <span data-ttu-id="50707-181">カスタム ポリシーを含めるには、`-AllowUserPolicies` パラメーターを使用します。</span><span class="sxs-lookup"><span data-stu-id="50707-181">To include any custom policy use the `-AllowUserPolicies` parameter.</span></span>  
  
 <span data-ttu-id="50707-182">システム ポリシーと作成されたユーザー ポリシーに基づいてエラーと警告のレポートを返す PowerShell のサンプル スクリプトを次に示します。</span><span class="sxs-lookup"><span data-stu-id="50707-182">Following is a sample PowerShell script that returns a report of errors and warnings based on the system policies and any user policies created:</span></span>  
  
```powershell
$policyResults = Get-SqlSmartAdmin | Test-SqlSmartAdmin -AllowUserPolicies  
$policyResults.PolicyEvaluationDetails | Select Name, Category, Expression, Result, Exception | fl
```  
  
 <span data-ttu-id="50707-183">次のスクリプトは、既定のインスタンス () のエラーと警告の詳細レポートを返し `\SQL\COMPUTER\DEFAULT` ます。</span><span class="sxs-lookup"><span data-stu-id="50707-183">The following script returns a detailed report of the errors and warnings for the default instance (`\SQL\COMPUTER\DEFAULT`):</span></span>  
  
```powershell
(Get-SqlSmartAdmin ).EnumHealthStatus()  
```  
  
### <a name="objects-in-msdb-database"></a><span data-ttu-id="50707-184">MSDB データベース内のオブジェクト</span><span class="sxs-lookup"><span data-stu-id="50707-184">Objects in MSDB database</span></span>  
 <span data-ttu-id="50707-185">機能を実装するためにインストールされているオブジェクトがあります。</span><span class="sxs-lookup"><span data-stu-id="50707-185">There are objects that are installed to implement the functionality.</span></span> <span data-ttu-id="50707-186">これらのオブジェクトは内部使用のために予約されています。</span><span class="sxs-lookup"><span data-stu-id="50707-186">These objects are reserved for internal use.</span></span> <span data-ttu-id="50707-187">ただし、バックアップの状態を監視する際に役立つ smart_backup_files というシステム テーブルが 1 つあります。</span><span class="sxs-lookup"><span data-stu-id="50707-187">However, there is one system table that can be useful in monitoring the backup status: smart_backup_files.</span></span> <span data-ttu-id="50707-188">このテーブルに格納されている、バックアップの種類、データベース名、最初と最後の lsn、バックアップの有効期限日などの監視に関連する情報の大部分は、システム関数 smart_admin によって公開され[ます。 fn_available_backups &#40;transact-sql&#41;](/sql/relational-databases/system-functions/managed-backup-fn-available-backups-transact-sql)です。</span><span class="sxs-lookup"><span data-stu-id="50707-188">Most of the Information   stored in this table relevant to monitoring like the type of backup, database name, first and last lsn, backup expiry dates are exposed through the system function [smart_admin.fn_available_backups &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/managed-backup-fn-available-backups-transact-sql).</span></span> <span data-ttu-id="50707-189">ただし、この関数を使用して、バックアップ ファイルの状態を示す smart_backup_files テーブルの状態列を利用することはできません。</span><span class="sxs-lookup"><span data-stu-id="50707-189">However the status column in the smart_backup_files table which indicates the status of the backup file is not available using the function.</span></span> <span data-ttu-id="50707-190">状態などの一部の情報は、次に示すサンプル クエリを使用してシステム テーブルから取得できます。</span><span class="sxs-lookup"><span data-stu-id="50707-190">Following is a sample query you can use to retrieve the some information including the status from the system table:</span></span>  
  
```sql
USE msdb  
GO  
SELECT  
 database_name AS [Database Name] ,backup_path AS [Backup Destination and File]  
,[Backup Type] =  
CASE backup_type  
WHEN 1 THEN 'FULL'  
WHEN 2 THEN 'LOG'  
END  
,[Backup Status] =  
CASE [status]  
WHEN 'A' THEN 'Available'  
WHEN 'B' THEN 'Copy In Progress'  
WHEN 'C' THEN 'Corrupted'  
WHEN 'D' THEN 'Deleted'  
WHEN 'F' THEN 'Copy Failed'  
WHEN 'U' THEN 'Unknown'  
END  
,first_lsn AS [First LSN]  
,last_lsn AS [Last LSN]  
,backup_start_date AS [Backup Start Time]  
,backup_finish_date AS [Backup Completion Time]  
,expiration_date AS [Backup Expiry Date/Time]  
FROM  
smart_backup_files;
```  
  
 <span data-ttu-id="50707-191">返される各種状態の詳細を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="50707-191">Following is a detailed explanation of the different status returned:</span></span>  
  
-   <span data-ttu-id="50707-192">**利用可能-A:** これは通常のバックアップファイルです。</span><span class="sxs-lookup"><span data-stu-id="50707-192">**Available - A:** This is a normal backup file.</span></span> <span data-ttu-id="50707-193">バックアップが完了し、Azure storage で使用できることが確認されました。</span><span class="sxs-lookup"><span data-stu-id="50707-193">The backup has been completed, and also verified that it is available in the Azure storage.</span></span>  
  
-   <span data-ttu-id="50707-194">**コピーが進行中です-B:** この状態は、可用性グループデータベース専用です。</span><span class="sxs-lookup"><span data-stu-id="50707-194">**Copy in Progress -B:** This status is specifically for Availability Group databases.</span></span> <span data-ttu-id="50707-195">[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]は、バックアップ ログ チェーンの中断を検出すると、バックアップ チェーンの中断の原因になったと考えられるバックアップの特定をまず試みます。</span><span class="sxs-lookup"><span data-stu-id="50707-195">If [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] detects a break in the backup log chain, it will first attempt identify the  backup that might have caused the break in backup chain.</span></span> <span data-ttu-id="50707-196">バックアップファイルの検索時に、Azure storage にファイルをコピーしようとします。</span><span class="sxs-lookup"><span data-stu-id="50707-196">On finding the backup file it attempts to copy the file to Azure storage.</span></span> <span data-ttu-id="50707-197">コピー プロセスの実行中にこの状態が表示されます。</span><span class="sxs-lookup"><span data-stu-id="50707-197">When the copying process is in progress it will display this status.</span></span>  
  
-   <span data-ttu-id="50707-198">**コピーに失敗しました-F:** コピーの進行状況と同様に、これは可用性グループの特定のデータベースです。</span><span class="sxs-lookup"><span data-stu-id="50707-198">**Copy Failed - F:** Similar to Copy In Progress, this is specific t Availability Group databases.</span></span> <span data-ttu-id="50707-199">コピー プロセスが失敗した場合、状態は F としてマークされます。</span><span class="sxs-lookup"><span data-stu-id="50707-199">If the copy process fails, the status is marked as F.</span></span>  
  
-   <span data-ttu-id="50707-200">**破損-C:**[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]が複数回試行された後でも [RESTORE HEADER_ONLY] コマンドを実行して記憶域のバックアップファイルを確認できない場合、このファイルは破損しているとマークされます。</span><span class="sxs-lookup"><span data-stu-id="50707-200">**Corrupted - C:** If [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] is unable to verify the backup file in the storage by performing a RESTORE HEADER_ONLY command even after multiple attempts, it marks this file as corrupted.</span></span> [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]<span data-ttu-id="50707-201">は、破損したファイルによってバックアップ チェーンが中断されないように、バックアップをスケジュールします。</span><span class="sxs-lookup"><span data-stu-id="50707-201">will schedule a backup to ensure that the corrupted file does not result in a break of the backup chain.</span></span>  
  
-   <span data-ttu-id="50707-202">**削除済み-D:** 対応するファイルが Azure storage に見つかりません。</span><span class="sxs-lookup"><span data-stu-id="50707-202">**Deleted - D:** The corresponding file cannot be found in the Azure storage.</span></span> <span data-ttu-id="50707-203">ファイルの削除によってバックアップ チェーンが中断された場合、[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]はバックアップをスケジュールします。</span><span class="sxs-lookup"><span data-stu-id="50707-203">[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] will schedule a backup if the deleted file results in a break in the backup chain.</span></span>  
  
-   <span data-ttu-id="50707-204">**不明-U:** この状態 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] は、Azure storage 内のファイルの存在とそのプロパティをまだ確認できていないことを示しています。</span><span class="sxs-lookup"><span data-stu-id="50707-204">**Unknown - U:** This status indicated that [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] has not yet been able to verify file existence and its properties in the Azure storage.</span></span> <span data-ttu-id="50707-205">プロセスが次回実行されたときに (約 15 分間隔)、この状態が更新されます。</span><span class="sxs-lookup"><span data-stu-id="50707-205">The next time the process runs, which is approximately every 15 minutes, this status will be updated.</span></span>  
