---
title: SQL Server エージェントのマスター ジョブの作成 | Microsoft Docs
ms.custom: ''
ms.date: 04/26/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], master jobs
- jobs [SQL Server Agent], creating
- master SQL Server Agent job [SQL Server]
ms.assetid: c12ab23f-d7ee-43a5-8cd2-0a9121292bcd
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8a6503caec3f153878e360ee29ce09a5c099ade5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715930"
---
# <a name="create-a-sql-server-agent-master-job"></a><span data-ttu-id="fb164-102">SQL Server エージェントのマスター ジョブの作成</span><span class="sxs-lookup"><span data-stu-id="fb164-102">Create a SQL Server Agent Master Job</span></span>
  <span data-ttu-id="fb164-103">このトピック [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] は、またはを使用して、でマスターエージェントジョブを作成する方法について説明し [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="fb164-103">This topic describes how to create a master [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="fb164-104">はじめに</span><span class="sxs-lookup"><span data-stu-id="fb164-104">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="fb164-105">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="fb164-105">Limitations and Restrictions</span></span>  
 <span data-ttu-id="fb164-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのマスター ジョブの変更は、関係するすべてのターゲット サーバーに伝達する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fb164-106">Changes to master [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs must be propagated to all involved target servers.</span></span> <span data-ttu-id="fb164-107">これらのターゲットが指定されるまでターゲット サーバーはジョブをダウンロードしないので、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] では、ターゲット サーバーを指定する前に、特定のジョブのすべてのジョブ ステップとジョブ スケジュールを完了しておくことをお勧めしています。</span><span class="sxs-lookup"><span data-stu-id="fb164-107">Because target servers do not initially download a job until those targets are specified, [!INCLUDE[msCoName](../../includes/msconame-md.md)] recommends that you complete all job steps and job schedules for a particular job before you specify any target servers.</span></span> <span data-ttu-id="fb164-108">この順序に従わなかった場合は、 **sp_post_msx_operation** ストアド プロシージャを実行するか、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を使用してジョブを変更することによって、変更されたジョブをターゲット サーバーが再びダウンロードするように手動で要求する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fb164-108">Otherwise, you must manual request that the target servers download the modified job again, either by executing the **sp_post_msx_operation** stored procedure or modifying the job using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="fb164-109">詳細については、「 [transact-sql&#41;&#40;sp_post_msx_operation](/sql/relational-databases/system-stored-procedures/sp-post-msx-operation-transact-sql) 」または「[ジョブの変更](modify-a-job.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fb164-109">For more information, see [sp_post_msx_operation &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-post-msx-operation-transact-sql) or [Modify a Job](modify-a-job.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="fb164-110">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="fb164-110">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="fb164-111">Permissions</span><span class="sxs-lookup"><span data-stu-id="fb164-111">Permissions</span></span>  
 <span data-ttu-id="fb164-112">プロキシに関連付けられているステップがある分散ジョブは、ターゲット サーバーのプロキシ アカウントのコンテキストで実行されます。</span><span class="sxs-lookup"><span data-stu-id="fb164-112">Distributed jobs that have steps which are associated with a proxy run under the context of the proxy account on the target server.</span></span> <span data-ttu-id="fb164-113">次の条件を満たしていることを確認してください。満たしていないと、プロキシに関連付けられているジョブ ステップがマスター サーバーから対象サーバーにダウンロードされません。</span><span class="sxs-lookup"><span data-stu-id="fb164-113">Make sure that the following conditions are met or job steps that are associated with a proxy will not be downloaded from the master server to the target:</span></span>  
  
-   <span data-ttu-id="fb164-114">レジストリサブキー **\ HKEY_LOCAL_MACHINE \software\microsoft\microsoft SQL Server \\ < *instance_name*> \ SQL Server Agent\AllowDownloadedJobsToMatchProxyName** (REG_DWORD) が 1 (true) に設定されています。</span><span class="sxs-lookup"><span data-stu-id="fb164-114">The registry subkey **\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<*instance_name*>\SQL Server Agent\AllowDownloadedJobsToMatchProxyName** (REG_DWORD) is set to 1 (true).</span></span> <span data-ttu-id="fb164-115">既定では、この値は 0 (false) に設定されます。</span><span class="sxs-lookup"><span data-stu-id="fb164-115">By default, this subkey is set to 0 (false).</span></span>  
  
-   <span data-ttu-id="fb164-116">ジョブ ステップを実行するマスター サーバー プロキシ アカウントと同じ名前を持つターゲット サーバーにプロキシ アカウントが存在すること。</span><span class="sxs-lookup"><span data-stu-id="fb164-116">A proxy account exists on the target server that has the same name as the master server proxy account under which the job step runs.</span></span>  
  
 <span data-ttu-id="fb164-117">マスター サーバーからターゲット サーバーにプロキシ アカウントをダウンロード中に、これらのアカウントを使用するジョブ ステップが失敗した場合は、**msdb** データベースの **sysdownloadlist** テーブルの **error_message** 列を参照して、以下のエラー メッセージの有無を確認します。</span><span class="sxs-lookup"><span data-stu-id="fb164-117">If job steps that use proxy accounts fail when downloading them from the master server to the target server, you can check the **error_message** column in the **sysdownloadlist** table in the **msdb** database for the following error messages:</span></span>  
  
-   <span data-ttu-id="fb164-118">"ジョブ ステップではプロキシ アカウントが必要ですが、ターゲット サーバーで一致するプロキシが無効です。"</span><span class="sxs-lookup"><span data-stu-id="fb164-118">"The job step requires a proxy account, however proxy matching is disabled on the target server."</span></span> <span data-ttu-id="fb164-119">このエラーを解決するには、 **AllowDownloadedJobsToMatchProxyName** レジストリ サブキーを 1 に設定します。</span><span class="sxs-lookup"><span data-stu-id="fb164-119">To resolve this error, set the **AllowDownloadedJobsToMatchProxyName** registry subkey to 1.</span></span>  
  
-   <span data-ttu-id="fb164-120">"プロキシ アカウントが見つかりませんでした。"</span><span class="sxs-lookup"><span data-stu-id="fb164-120">"Proxy not found."</span></span> <span data-ttu-id="fb164-121">このエラーを解決するには、ターゲット サーバー上にプロキシ アカウントが存在し、ジョブ ステップを実行するマスター サーバー プロキシ アカウントと同じ名前が付けられているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="fb164-121">To resolve this error, make sure a proxy account exists on the target server that has the same name as the master server proxy account under which the job step runs.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="fb164-122">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="fb164-122">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-master-sql-server-agent-job"></a><span data-ttu-id="fb164-123">SQL Server エージェントのマスター ジョブを作成するには</span><span class="sxs-lookup"><span data-stu-id="fb164-123">To create a master SQL Server Agent job</span></span>  
  
1.  <span data-ttu-id="fb164-124">**オブジェクト エクスプローラー**で、SQL Server エージェント ジョブを作成するサーバーをプラス記号をクリックして展開します。</span><span class="sxs-lookup"><span data-stu-id="fb164-124">In the **Object Explorer**, click the plus sign to expand the server where you want to create a SQL Server Agent job.</span></span>  
  
2.  <span data-ttu-id="fb164-125">プラス記号をクリックして **[SQL Server エージェント]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="fb164-125">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="fb164-126">**[ジョブ]** フォルダーを右クリックし、**[新しいジョブ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="fb164-126">Right-click the **Jobs** folder and select **New Job...**.</span></span>  
  
4.  <span data-ttu-id="fb164-127">**[新しいジョブ]** ダイアログ ボックスの **[全般]** ページで、ジョブの全般的なプロパティを変更します。</span><span class="sxs-lookup"><span data-stu-id="fb164-127">In the **New Job** dialog box, on the **General** page, modify the general properties of the job.</span></span> <span data-ttu-id="fb164-128">このページで利用可能なオプションの詳細については、「[ジョブのプロパティ」および「[新しいジョブ &#40;全般] ページ](../../integration-services/general-page-of-integration-services-designers-options.md)」を参照してください&#41;</span><span class="sxs-lookup"><span data-stu-id="fb164-128">For more information on the available options on this page, see [Job Properties and New Job &#40;General Page&#41;](../../integration-services/general-page-of-integration-services-designers-options.md)</span></span>  
  
5.  <span data-ttu-id="fb164-129">**[ステップ]** ページで、ジョブ ステップを編成します。</span><span class="sxs-lookup"><span data-stu-id="fb164-129">On the **Steps** page, organize the job steps.</span></span> <span data-ttu-id="fb164-130">このページで使用可能なオプションの詳細については、「[ジョブのプロパティ: 新しいジョブ &#40;ステップ」ページ](job-properties-new-job-steps-page.md)を参照してください&#41;</span><span class="sxs-lookup"><span data-stu-id="fb164-130">For more information on the available options on this page, see [Job Properties:New Job &#40;Steps Page&#41;](job-properties-new-job-steps-page.md)</span></span>  
  
6.  <span data-ttu-id="fb164-131">**[スケジュール** ] ページで、ジョブのスケジュールを編成します。</span><span class="sxs-lookup"><span data-stu-id="fb164-131">On the **Schedules** page, organize schedules for the job.</span></span> <span data-ttu-id="fb164-132">このページで使用可能なオプションの詳細については、「[ジョブのプロパティ: [新しいジョブ &#40;スケジュール] ページ](job-properties-new-job-schedules-page.md)」を参照してください&#41;</span><span class="sxs-lookup"><span data-stu-id="fb164-132">For more information on the available options on this page, see [Job Properties: New Job &#40;Schedules Page&#41;](job-properties-new-job-schedules-page.md)</span></span>  
  
7.  <span data-ttu-id="fb164-133">**[警告]** ページで、ジョブの警告を編成します。</span><span class="sxs-lookup"><span data-stu-id="fb164-133">On the **Alerts** page, organize the alerts for the job.</span></span> <span data-ttu-id="fb164-134">このページで利用可能なオプションの詳細については、「[ジョブのプロパティ: 新しいジョブ &#40;アラート」ページ](job-properties-new-job-alerts-page.md)を参照してください&#41;</span><span class="sxs-lookup"><span data-stu-id="fb164-134">For more information on the available options on this page, see [Job Properties: New Job &#40;Alerts Page&#41;](job-properties-new-job-alerts-page.md)</span></span>  
  
8.  <span data-ttu-id="fb164-135">**[通知]** ページで、ジョブの完了時に [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントが実行するアクションを設定します。</span><span class="sxs-lookup"><span data-stu-id="fb164-135">On the **Notifications** page, set actions for [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to perform when the job completes.</span></span> <span data-ttu-id="fb164-136">このページで利用可能なオプションの詳細については、「[ジョブのプロパティ: 新しいジョブ &#40;通知」ページ&#41;](job-properties-new-job-notifications-page.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fb164-136">For more information on the available options on this page, see [Job Properties: New Job &#40;Notifications Page&#41;](job-properties-new-job-notifications-page.md).</span></span>  
  
9. <span data-ttu-id="fb164-137">**[ターゲット]** ページで、ジョブのターゲット サーバーを管理します。</span><span class="sxs-lookup"><span data-stu-id="fb164-137">On the **Targets** page, manage the target servers for the job.</span></span> <span data-ttu-id="fb164-138">このページで使用可能なオプションの詳細については、「[ジョブのプロパティ: 新しいジョブ &#40;ターゲットページ&#41;](job-properties-new-job-targets-page.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fb164-138">For more information on the available options on this page, see [Job Properties: New Job &#40;Targets Page&#41;](job-properties-new-job-targets-page.md).</span></span>  
  
10. <span data-ttu-id="fb164-139">完了したら、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fb164-139">When finished, click **OK**.</span></span>  
  

  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="fb164-140">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="fb164-140">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-master-sql-server-agent-job"></a><span data-ttu-id="fb164-141">SQL Server エージェントのマスター ジョブを作成するには</span><span class="sxs-lookup"><span data-stu-id="fb164-141">To create a master SQL Server Agent job</span></span>  
  
1.  <span data-ttu-id="fb164-142">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="fb164-142">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="fb164-143">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fb164-143">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="fb164-144">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fb164-144">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE msdb ;  
    GO  
    -- Adds a new job executed by the SQLServerAgent service called 'Weekly Sales Data Backup'  
    EXEC dbo.sp_add_job  
        @job_name = N'Weekly Sales Data Backup' ;  
    GO  
    -- Adds a step (operation) to the 'Weekly Sales Data Backup' job.  
    EXEC sp_add_jobstep  
        @job_name = N'Weekly Sales Data Backup',  
        @step_name = N'Set database to read only',  
        @subsystem = N'TSQL',  
        @command = N'ALTER DATABASE SALES SET READ_ONLY',   
        @retry_attempts = 5,  
        @retry_interval = 5 ;  
    GO  
    -- Creates a schedule called RunOnce  
    EXEC dbo.sp_add_schedule  
        @schedule_name = N'RunOnce',  
        @freq_type = 1,  
        @active_start_time = 233000 ;  
    USE msdb ;  
    GO  
    -- Sets the 'RunOnce' schedule to the "Weekly Sales Data Backup' Job  
    EXEC sp_attach_schedule  
       @job_name = N'Weekly Sales Data Backup',  
       @schedule_name = N'RunOnce';  
    GO  
    -- assigns the multiserver job Weekly Sales Backups to the server SEATTLE2  
    -- assumes that SEATTLE2 is registered as a target server for the current instance.  
    EXEC dbo.sp_add_jobserver  
        @job_name = N'Weekly Sales Data Backups',  
        @server_name = N'SEATTLE2' ;  
    GO  
    ```  
  
 <span data-ttu-id="fb164-145">詳細については、次を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fb164-145">For more information, see:</span></span>  
  
-   [<span data-ttu-id="fb164-146">sp_add_job &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="fb164-146">sp_add_job &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-add-job-transact-sql)  
  
-   [<span data-ttu-id="fb164-147">sp_add_jobstep &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="fb164-147">sp_add_jobstep &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql)  
  
-   [<span data-ttu-id="fb164-148">sp_add_schedule &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="fb164-148">sp_add_schedule &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-add-schedule-transact-sql)  
  
-   [<span data-ttu-id="fb164-149">sp_attach_schedule &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="fb164-149">sp_attach_schedule &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-attach-schedule-transact-sql)  
  
-   [<span data-ttu-id="fb164-150">sp_add_jobserver &#40;Transact-sql&#41;</span><span class="sxs-lookup"><span data-stu-id="fb164-150">sp_add_jobserver &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql)  
  

  
  
