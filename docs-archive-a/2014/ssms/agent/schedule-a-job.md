---
title: ジョブのスケジュール設定 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- scheduling jobs [SQL Server]
- SQL Server Agent jobs, scheduling
- jobs [SQL Server Agent], scheduling
ms.assetid: f626390a-a3df-4970-b7a7-a0529e4a109c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1077766d6853ed7c029b8eefa76515c89ad861fd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715005"
---
# <a name="schedule-a-job"></a><span data-ttu-id="868e1-102">Schedule a Job</span><span class="sxs-lookup"><span data-stu-id="868e1-102">Schedule a Job</span></span>
  <span data-ttu-id="868e1-103">このトピックでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブのスケジュールを設定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="868e1-103">This topic describes how to schedule a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job.</span></span>  
  
-   <span data-ttu-id="868e1-104">**作業を開始する準備:** 、</span><span class="sxs-lookup"><span data-stu-id="868e1-104">**Before you begin:** ,</span></span>  
  
     [<span data-ttu-id="868e1-105">Security</span><span class="sxs-lookup"><span data-stu-id="868e1-105">Security</span></span>](#Security)  
  
-   <span data-ttu-id="868e1-106">**ジョブのスケジュールを設定する方法:**</span><span class="sxs-lookup"><span data-stu-id="868e1-106">**To schedule a job, using:**</span></span>  
  
     [<span data-ttu-id="868e1-107">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="868e1-107">SQL Server Management Studio</span></span>](#SSMS)  
  
     [<span data-ttu-id="868e1-108">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="868e1-108">Transact-SQL</span></span>](#TSQL)  
  
     [<span data-ttu-id="868e1-109">SQL Server 管理オブジェクト</span><span class="sxs-lookup"><span data-stu-id="868e1-109">SQL Server Management Objects</span></span>](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="868e1-110">はじめに</span><span class="sxs-lookup"><span data-stu-id="868e1-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="868e1-111">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="868e1-111">Security</span></span>  
 <span data-ttu-id="868e1-112">詳細については、「 [SQL Server エージェントのセキュリティの実装](implement-sql-server-agent-security.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="868e1-112">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="868e1-113">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="868e1-113">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-and-attach-a-schedule-to-a-job"></a><span data-ttu-id="868e1-114">スケジュールを作成してジョブにアタッチするには</span><span class="sxs-lookup"><span data-stu-id="868e1-114">To create and attach a schedule to a job</span></span>  
  
1.  <span data-ttu-id="868e1-115">**オブジェクトエクスプローラー**で、のインスタンスに接続し、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] そのインスタンスを展開します。</span><span class="sxs-lookup"><span data-stu-id="868e1-115">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="868e1-116">**[SQL Server エージェント]**、 **[ジョブ]** の順に展開し、スケジュールを設定するジョブを右クリックします。次に、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="868e1-116">Expand **SQL Server Agent**, expand **Jobs**, right-click the job you want to schedule, and click **Properties**.</span></span>  
  
3.  <span data-ttu-id="868e1-117">**[スケジュール]** ページをクリックし、 **[新規作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="868e1-117">Select the **Schedules** page, and then click **New**.</span></span>  
  
4.  <span data-ttu-id="868e1-118">**[名前]** ボックスに新しいスケジュールの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="868e1-118">In the **Name** box, type a name for the new schedule.</span></span>  
  
5.  <span data-ttu-id="868e1-119">スケジュールを作成してもすぐに有効にしない場合は、 **[有効]** チェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="868e1-119">Clear the **Enabled** check box if you do not want the schedule to take effect immediately following its creation.</span></span>  
  
6.  <span data-ttu-id="868e1-120">**[スケジュールの種類]** ボックスの一覧で、次のいずれかを選択します。</span><span class="sxs-lookup"><span data-stu-id="868e1-120">For **Schedule Type**, select one of the following:</span></span>  
  
    -   <span data-ttu-id="868e1-121">**[SQL Server エージェントの開始時に自動的に開始]** 。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービスが開始されたときにジョブを開始します。</span><span class="sxs-lookup"><span data-stu-id="868e1-121">Click **Start automatically when SQL Server Agent starts** to start the job when the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service is started.</span></span>  
  
    -   <span data-ttu-id="868e1-122">**[CPU がアイドル状態になったときに開始]** 。CPU がアイドル状態になったときにジョブを開始します。</span><span class="sxs-lookup"><span data-stu-id="868e1-122">Click **Start whenever the CPUs become idle** to start the job when the CPUs reach an idle condition.</span></span>  
  
    -   <span data-ttu-id="868e1-123">**[定期的]** 。スケジュールを繰り返し実行します。</span><span class="sxs-lookup"><span data-stu-id="868e1-123">Click **Recurring** if you want a schedule to run repeatedly.</span></span> <span data-ttu-id="868e1-124">定期的なスケジュールを設定するには、ダイアログ ボックス上の **[頻度]**、 **[一日のうちの頻度]**、および **[実行時間]** のグループに値を指定します。</span><span class="sxs-lookup"><span data-stu-id="868e1-124">To set the recurring schedule, complete the **Frequency**, **Daily Frequency**, and **Duration** groups on the dialog.</span></span>  
  
    -   <span data-ttu-id="868e1-125">**[指定日時]** 。スケジュールを 1 回のみ実行します。</span><span class="sxs-lookup"><span data-stu-id="868e1-125">Click **One time** if you want the schedule to run only once.</span></span> <span data-ttu-id="868e1-126">**指定日時** のスケジュールを設定するには、ダイアログ ボックス上の **[指定日時に発生]** グループに値を指定します。</span><span class="sxs-lookup"><span data-stu-id="868e1-126">To set the **One time** schedule, complete the **One-time occurrence** group on the dialog.</span></span>  
  
#### <a name="to-attach-a-schedule-to-a-job"></a><span data-ttu-id="868e1-127">ジョブにスケジュールをアタッチするには</span><span class="sxs-lookup"><span data-stu-id="868e1-127">To attach a schedule to a job</span></span>  
  
1.  <span data-ttu-id="868e1-128">**オブジェクトエクスプローラー**で、のインスタンスに接続し、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] そのインスタンスを展開します。</span><span class="sxs-lookup"><span data-stu-id="868e1-128">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="868e1-129">**[SQL Server エージェント]**、 **[ジョブ]** の順に展開し、スケジュールを設定するジョブを右クリックして、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="868e1-129">Expand **SQL Server Agent**, expand **Jobs**, right-click the job that you want to schedule, and click **Properties**.</span></span>  
  
3.  <span data-ttu-id="868e1-130">**[スケジュール]** ページをクリックし、 **[選択]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="868e1-130">Select the **Schedules** page, and then click **Pick**.</span></span>  
  
4.  <span data-ttu-id="868e1-131">アタッチするスケジュールを選択して、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="868e1-131">Select the schedule that you want to attach, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="868e1-132">**[ジョブのプロパティ]** ダイアログ ボックスで、アタッチされたスケジュールをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="868e1-132">In the **Job Properties** dialog box, double-click the attached schedule.</span></span>  
  
6.  <span data-ttu-id="868e1-133">**[開始日]** が正しく設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="868e1-133">Verify that **Start date** is set correctly.</span></span> <span data-ttu-id="868e1-134">正しく設定されていない場合は、スケジュールの開始日を設定し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="868e1-134">If it is not, set the date when you want for the schedule to start, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="868e1-135">**[ジョブのプロパティ]** ダイアログ ボックスで、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="868e1-135">In the **Job Properties** dialog box, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="868e1-136">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="868e1-136">Using Transact-SQL</span></span>  
  
#### <a name="to-schedule-a-job"></a><span data-ttu-id="868e1-137">ジョブのスケジュールを設定するには</span><span class="sxs-lookup"><span data-stu-id="868e1-137">To schedule a job</span></span>  
  
1.  <span data-ttu-id="868e1-138">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="868e1-138">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="868e1-139">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="868e1-139">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="868e1-140">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="868e1-140">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```sql
    USE msdb ;  
    GO  
    -- creates a schedule named NightlyJobs.   
    -- Jobs that use this schedule execute every day when the time on the server is 01:00.   
    EXEC sp_add_schedule  
        @schedule_name = N'NightlyJobs' ,  
        @freq_type = 4,  
        @freq_interval = 1,  
        @active_start_time = 010000 ;  
    GO  
    -- attaches the schedule to the job BackupDatabase  
    EXEC sp_attach_schedule  
       @job_name = N'BackupDatabase',  
       @schedule_name = N'NightlyJobs' ;  
    GO  
    ```  
  
 <span data-ttu-id="868e1-141">詳細については、「 [sp_add_schedule &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-add-schedule-transact-sql) 」と「 [transact-sql &#40;の sp_attach_schedule ](/sql/relational-databases/system-stored-procedures/sp-attach-schedule-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="868e1-141">For more information, see [sp_add_schedule &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-schedule-transact-sql) and [sp_attach_schedule &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-attach-schedule-transact-sql).</span></span>  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="868e1-142">SQL Server 管理オブジェクトの使用</span><span class="sxs-lookup"><span data-stu-id="868e1-142">Using SQL Server Management Objects</span></span>  
 <span data-ttu-id="868e1-143">`JobSchedule`Visual Basic、Visual C#、PowerShell など、選択したプログラミング言語でクラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="868e1-143">Use the `JobSchedule` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span> <span data-ttu-id="868e1-144">詳細については、「[SQL Server 管理オブジェクト (SMO) プログラミング ガイド](https://msdn.microsoft.com/library/ms162169.aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="868e1-144">For more information, see[SQL Server Management Objects (SMO)](https://msdn.microsoft.com/library/ms162169.aspx).</span></span>  
