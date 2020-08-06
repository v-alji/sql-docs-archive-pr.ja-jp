---
title: ジョブの作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], creating
- SQL Server Agent jobs, creating
ms.assetid: b35af2b6-6594-40d1-9861-4d5dd906048c
author: stevestein
ms.author: sstein
ms.openlocfilehash: de74f032924fbb0b6643bd8f3d482481ffb1f983
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631478"
---
# <a name="create-a-job"></a><span data-ttu-id="c3bd1-102">ジョブを作成する</span><span class="sxs-lookup"><span data-stu-id="c3bd1-102">Create a Job</span></span>
  <span data-ttu-id="c3bd1-103">このトピックでは、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、または SQL Server 管理オブジェクト (SMO) を使用して、[!INCLUDE[tsql](../../includes/tsql-md.md)] で SQL Server エージェント ジョブを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c3bd1-103">This topic describes how to create a SQL Server Agent job in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or SQL Server Management Objects (SMO).</span></span>  
  
 <span data-ttu-id="c3bd1-104">オペレーターに送信できるジョブ ステップ、スケジュール、警告、および通知を追加するには、「参照」セクションのトピックをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="c3bd1-104">To add job steps, schedules, alerts, and notifications that can be sent to operators, see the links to topics in the See Also section.</span></span>  
  
-   <span data-ttu-id="c3bd1-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="c3bd1-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="c3bd1-106">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="c3bd1-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="c3bd1-107">Security</span><span class="sxs-lookup"><span data-stu-id="c3bd1-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="c3bd1-108">**ジョブを作成する方法:**</span><span class="sxs-lookup"><span data-stu-id="c3bd1-108">**To create a job, using:**</span></span>  
  
     <span data-ttu-id="c3bd1-109">[SQL Server Management Studio](#SSMSProcedure)、</span><span class="sxs-lookup"><span data-stu-id="c3bd1-109">[SQL Server Management Studio](#SSMSProcedure),</span></span>  
  
     [<span data-ttu-id="c3bd1-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="c3bd1-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="c3bd1-111">SQL Server 管理オブジェクト</span><span class="sxs-lookup"><span data-stu-id="c3bd1-111">SQL Server Management Objects</span></span>](#SMOProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="c3bd1-112">はじめに</span><span class="sxs-lookup"><span data-stu-id="c3bd1-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="c3bd1-113">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="c3bd1-113">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="c3bd1-114">ジョブを作成するには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント固定データベース ロールか **sysadmin** 固定サーバー ロールのメンバーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="c3bd1-114">To create a job, a user must be a member of one of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent fixed database roles or the **sysadmin** fixed server role.</span></span> <span data-ttu-id="c3bd1-115">ジョブの編集は、ジョブの所有者または **sysadmin** ロールのメンバーのみが行うことができます。</span><span class="sxs-lookup"><span data-stu-id="c3bd1-115">A job can be edited only by its owner or members of the **sysadmin** role.</span></span> <span data-ttu-id="c3bd1-116">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント固定データベース ロールの詳細については、「 [SQL Server エージェントの固定データベース ロール](sql-server-agent-fixed-database-roles.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c3bd1-116">For more information about the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent fixed database roles, see [SQL Server Agent Fixed Database Roles](sql-server-agent-fixed-database-roles.md).</span></span>  
  
-   <span data-ttu-id="c3bd1-117">別のログインにジョブを割り当てた場合に、新しい所有者がそのジョブを正常に実行できる十分な権限を持っていないこともあります。</span><span class="sxs-lookup"><span data-stu-id="c3bd1-117">Assigning a job to another login does not guarantee that the new owner has sufficient permission to run the job successfully.</span></span>  
  
-   <span data-ttu-id="c3bd1-118">ローカル ジョブはローカル [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントによってキャッシュに格納されます。</span><span class="sxs-lookup"><span data-stu-id="c3bd1-118">Local jobs are cached by the local [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span> <span data-ttu-id="c3bd1-119">したがって、ジョブを変更すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントは暗黙的にジョブをキャッシュに再登録します。</span><span class="sxs-lookup"><span data-stu-id="c3bd1-119">Therefore, any modifications implicitly force [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to re-cache the job.</span></span> <span data-ttu-id="c3bd1-120">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sp_add_jobserver **が呼び出されるまで** エージェントはジョブをキャッシュに格納しないので、 **sp_add_jobserver** を最後に呼び出す方が効率的です。</span><span class="sxs-lookup"><span data-stu-id="c3bd1-120">Because [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent does not cache the job until **sp_add_jobserver** is called, it is more efficient to call **sp_add_jobserver** last.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="c3bd1-121">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="c3bd1-121">Security</span></span>  
  
-   <span data-ttu-id="c3bd1-122">ジョブの所有者を変更するには、システム管理者でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="c3bd1-122">You must be a system administrator to change the owner of a job.</span></span>  
  
-   <span data-ttu-id="c3bd1-123">セキュリティを確保するため、ジョブの所有者または **sysadmin** ロールのメンバーだけがジョブの定義を変更できます。</span><span class="sxs-lookup"><span data-stu-id="c3bd1-123">For security reasons, only the job owner or a member of the **sysadmin** role can change the definition of the job.</span></span> <span data-ttu-id="c3bd1-124">**sysadmin** 固定サーバー ロールのメンバーのみが別のユーザーにジョブの所有権を割り当てることができ、ジョブの所有者とは無関係にジョブを実行できます。</span><span class="sxs-lookup"><span data-stu-id="c3bd1-124">Only members of the **sysadmin** fixed server role can assign job ownership to other users, and they can run any job, regardless of the job owner.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c3bd1-125">ジョブの所有権を **sysadmin** 固定サーバー ロールのメンバーでないユーザーに変更し、そのジョブがプロキシ アカウントを必要とするジョブ ステップを実行する ( [!INCLUDE[ssIS](../../includes/ssis-md.md)] パッケージの実行など) 場合は、ユーザーがそのプロキシ アカウントにアクセスできることを確認してください。アクセスできない場合、ジョブは失敗します。</span><span class="sxs-lookup"><span data-stu-id="c3bd1-125">If you change job ownership to a user who is not a member of the **sysadmin** fixed server role, and the job is executing job steps that require proxy accounts (for example, [!INCLUDE[ssIS](../../includes/ssis-md.md)] package execution), make sure that the user has access to that proxy account or else the job will fail.</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="c3bd1-126">Permissions</span><span class="sxs-lookup"><span data-stu-id="c3bd1-126">Permissions</span></span>  
 <span data-ttu-id="c3bd1-127">詳細については、「 [SQL Server エージェントのセキュリティの実装](implement-sql-server-agent-security.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="c3bd1-127">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="c3bd1-128">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="c3bd1-128">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-sql-server-agent-job"></a><span data-ttu-id="c3bd1-129">SQL Server エージェントのジョブを作成するには</span><span class="sxs-lookup"><span data-stu-id="c3bd1-129">To create a SQL Server Agent job</span></span>  
  
1.  <span data-ttu-id="c3bd1-130">**オブジェクト エクスプローラー**で、SQL Server エージェント ジョブを作成するサーバーをプラス記号をクリックして展開します。</span><span class="sxs-lookup"><span data-stu-id="c3bd1-130">In the **Object Explorer**, click the plus sign to expand the server where you want to create a SQL Server Agent job.</span></span>  
  
2.  <span data-ttu-id="c3bd1-131">プラス記号をクリックして **[SQL Server エージェント]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="c3bd1-131">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="c3bd1-132">**[ジョブ]** フォルダーを右クリックし、**[新しいジョブ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="c3bd1-132">Right-click the **Jobs** folder and select **New Job...**.</span></span>  
  
4.  <span data-ttu-id="c3bd1-133">**[新しいジョブ]** ダイアログ ボックスの **[全般]** ページで、ジョブの全般的なプロパティを変更します。</span><span class="sxs-lookup"><span data-stu-id="c3bd1-133">In the **New Job** dialog box, on the **General** page, modify the general properties of the job.</span></span> <span data-ttu-id="c3bd1-134">このページで利用可能なオプションの詳細については、「[ジョブのプロパティ」および「[新しいジョブ &#40;全般] ページ](../../integration-services/general-page-of-integration-services-designers-options.md)」を参照してください&#41;</span><span class="sxs-lookup"><span data-stu-id="c3bd1-134">For more information on the available options on this page, see [Job Properties and New Job &#40;General Page&#41;](../../integration-services/general-page-of-integration-services-designers-options.md)</span></span>  
  
5.  <span data-ttu-id="c3bd1-135">**[ステップ]** ページで、ジョブ ステップを編成します。</span><span class="sxs-lookup"><span data-stu-id="c3bd1-135">On the **Steps** page, organize the job steps.</span></span> <span data-ttu-id="c3bd1-136">このページで使用可能なオプションの詳細については、「[ジョブのプロパティ: 新しいジョブ &#40;ステップ」ページ](job-properties-new-job-steps-page.md)を参照してください&#41;</span><span class="sxs-lookup"><span data-stu-id="c3bd1-136">For more information on the available options on this page, see [Job Properties:New Job &#40;Steps Page&#41;](job-properties-new-job-steps-page.md)</span></span>  
  
6.  <span data-ttu-id="c3bd1-137">**[スケジュール** ] ページで、ジョブのスケジュールを編成します。</span><span class="sxs-lookup"><span data-stu-id="c3bd1-137">On the **Schedules** page, organize schedules for the job.</span></span> <span data-ttu-id="c3bd1-138">このページで使用可能なオプションの詳細については、「[ジョブのプロパティ: [新しいジョブ &#40;スケジュール] ページ](job-properties-new-job-schedules-page.md)」を参照してください&#41;</span><span class="sxs-lookup"><span data-stu-id="c3bd1-138">For more information on the available options on this page, see [Job Properties: New Job &#40;Schedules Page&#41;](job-properties-new-job-schedules-page.md)</span></span>  
  
7.  <span data-ttu-id="c3bd1-139">**[警告]** ページで、ジョブの警告を編成します。</span><span class="sxs-lookup"><span data-stu-id="c3bd1-139">On the **Alerts** page, organize the alerts for the job.</span></span> <span data-ttu-id="c3bd1-140">このページで利用可能なオプションの詳細については、「[ジョブのプロパティ: 新しいジョブ &#40;アラート」ページ](job-properties-new-job-alerts-page.md)を参照してください&#41;</span><span class="sxs-lookup"><span data-stu-id="c3bd1-140">For more information on the available options on this page, see [Job Properties: New Job &#40;Alerts Page&#41;](job-properties-new-job-alerts-page.md)</span></span>  
  
8.  <span data-ttu-id="c3bd1-141">**[通知]** ページで、ジョブの完了時に [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントが実行するアクションを設定します。</span><span class="sxs-lookup"><span data-stu-id="c3bd1-141">On the **Notifications** page, set actions for [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to perform when the job completes.</span></span> <span data-ttu-id="c3bd1-142">このページで利用可能なオプションの詳細については、「[ジョブのプロパティ: 新しいジョブ &#40;通知」ページ&#41;](job-properties-new-job-notifications-page.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c3bd1-142">For more information on the available options on this page, see [Job Properties: New Job &#40;Notifications Page&#41;](job-properties-new-job-notifications-page.md).</span></span>  
  
9. <span data-ttu-id="c3bd1-143">**[ターゲット]** ページで、ジョブのターゲット サーバーを管理します。</span><span class="sxs-lookup"><span data-stu-id="c3bd1-143">On the **Targets** page, manage the target servers for the job.</span></span> <span data-ttu-id="c3bd1-144">このページで使用可能なオプションの詳細については、「[ジョブのプロパティ: 新しいジョブ &#40;ターゲットページ&#41;](job-properties-new-job-targets-page.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c3bd1-144">For more information on the available options on this page, see [Job Properties: New Job &#40;Targets Page&#41;](job-properties-new-job-targets-page.md).</span></span>  
  
10. <span data-ttu-id="c3bd1-145">完了したら、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c3bd1-145">When finished, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="c3bd1-146">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="c3bd1-146">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-sql-server-agent-job"></a><span data-ttu-id="c3bd1-147">SQL Server エージェントのジョブを作成するには</span><span class="sxs-lookup"><span data-stu-id="c3bd1-147">To create a SQL Server Agent job</span></span>  
  
1.  <span data-ttu-id="c3bd1-148">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="c3bd1-148">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="c3bd1-149">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c3bd1-149">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="c3bd1-150">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c3bd1-150">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```sql
    USE msdb ;  
    GO  
    EXEC dbo.sp_add_job  
        @job_name = N'Weekly Sales Data Backup' ;  
    GO  
    EXEC sp_add_jobstep  
        @job_name = N'Weekly Sales Data Backup',  
        @step_name = N'Set database to read only',  
        @subsystem = N'TSQL',  
        @command = N'ALTER DATABASE SALES SET READ_ONLY',   
        @retry_attempts = 5,  
        @retry_interval = 5 ;  
    GO  
    EXEC dbo.sp_add_schedule  
        @schedule_name = N'RunOnce',  
        @freq_type = 1,  
        @active_start_time = 233000 ;  
    USE msdb ;  
    GO  
    EXEC sp_attach_schedule  
       @job_name = N'Weekly Sales Data Backup',  
       @schedule_name = N'RunOnce';  
    GO  
    EXEC dbo.sp_add_jobserver  
        @job_name = N'Weekly Sales Data Backup';  
    GO  
    ```  
  
 <span data-ttu-id="c3bd1-151">詳細については、次を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c3bd1-151">For more information, see:</span></span>  
  
-   [<span data-ttu-id="c3bd1-152">sp_add_job &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="c3bd1-152">sp_add_job &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-add-job-transact-sql)  
  
-   [<span data-ttu-id="c3bd1-153">sp_add_jobstep &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="c3bd1-153">sp_add_jobstep &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql)  
  
-   [<span data-ttu-id="c3bd1-154">sp_add_schedule &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="c3bd1-154">sp_add_schedule &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-add-schedule-transact-sql)  
  
-   [<span data-ttu-id="c3bd1-155">sp_attach_schedule &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="c3bd1-155">sp_attach_schedule &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-attach-schedule-transact-sql)  
  
-   [<span data-ttu-id="c3bd1-156">sp_add_jobserver &#40;Transact-sql&#41;</span><span class="sxs-lookup"><span data-stu-id="c3bd1-156">sp_add_jobserver &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql)  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMOProcedure"></a><span data-ttu-id="c3bd1-157">SQL Server 管理オブジェクトの使用</span><span class="sxs-lookup"><span data-stu-id="c3bd1-157">Using SQL Server Management Objects</span></span>  
 <span data-ttu-id="c3bd1-158">**SQL Server エージェントのジョブを作成するには**</span><span class="sxs-lookup"><span data-stu-id="c3bd1-158">**To create a SQL Server Agent job**</span></span>  
  
 <span data-ttu-id="c3bd1-159">Visual Basic、Visual C#、PowerShell などのプログラミング言語で `Create` クラスの `Job` メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="c3bd1-159">Call the `Create` method of the `Job` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span> <span data-ttu-id="c3bd1-160">コード例については、「 [SQL Server エージェントでの自動管理タスクのスケジュール設定](sql-server-agent.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c3bd1-160">For example code, see [Scheduling Automatic Administrative Tasks in SQL Server Agent](sql-server-agent.md).</span></span>  
  
##  <a name="SSMSProc2"></a>  
