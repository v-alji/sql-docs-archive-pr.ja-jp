---
title: スケジュールの作成とジョブへのアタッチ | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server]
- scheduling jobs [SQL Server]
- jobs [SQL Server], scheduling
- CPU [SQL Server], idle conditions
- automatic job processing
- SQL Server Agent jobs, scheduling
- idle time [SQL Server]
ms.assetid: 079c2984-0052-4a37-a2b8-4ece56e6b6b5
author: stevestein
ms.author: sstein
ms.openlocfilehash: ced47013b6552725e6350b113a3722b066016a6b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715061"
---
# <a name="create-and-attach-schedules-to-jobs"></a><span data-ttu-id="0af4c-102">スケジュールの作成とジョブへのアタッチ</span><span class="sxs-lookup"><span data-stu-id="0af4c-102">Create and Attach Schedules to Jobs</span></span>
  <span data-ttu-id="0af4c-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブのスケジュール設定とは、ユーザーの操作なしでジョブの実行が開始される条件を定義することです。</span><span class="sxs-lookup"><span data-stu-id="0af4c-103">Scheduling [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs means defining the condition or conditions that cause the job to begin running without user interaction.</span></span> <span data-ttu-id="0af4c-104">ジョブのスケジュールを設定して自動的に実行するには、ジョブの新しいスケジュールを作成するか、既存のスケジュールをジョブにアタッチします。</span><span class="sxs-lookup"><span data-stu-id="0af4c-104">You can schedule a job to run automatically by creating a new schedule for the job, or by attaching an existing schedule to the job.</span></span>  
  
 <span data-ttu-id="0af4c-105">スケジュールを作成するには、次の 2 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="0af4c-105">There are two ways to create a schedule:</span></span>  
  
-   <span data-ttu-id="0af4c-106">ジョブの作成時にスケジュールを作成する。</span><span class="sxs-lookup"><span data-stu-id="0af4c-106">Create the schedule while you are creating a job.</span></span>  
  
-   <span data-ttu-id="0af4c-107">オブジェクト エクスプローラーでスケジュールを作成する。</span><span class="sxs-lookup"><span data-stu-id="0af4c-107">Create the schedule in Object Explorer.</span></span>  
  
 <span data-ttu-id="0af4c-108">スケジュールを作成したら、特定のジョブに対して作成した場合でも、そのスケジュールを複数のジョブにアタッチすることができます。</span><span class="sxs-lookup"><span data-stu-id="0af4c-108">After a schedule has been created, you can attach that schedule to multiple jobs, even if the schedule was created for a specific job.</span></span> <span data-ttu-id="0af4c-109">また、ジョブからスケジュールをデタッチすることもできます。</span><span class="sxs-lookup"><span data-stu-id="0af4c-109">You can also detach schedules from jobs.</span></span>  
  
 <span data-ttu-id="0af4c-110">スケジュールは、時刻またはイベントに基づいて作成できます。</span><span class="sxs-lookup"><span data-stu-id="0af4c-110">A schedule can be based upon time or an event.</span></span> <span data-ttu-id="0af4c-111">たとえば、次のタイミングで実行するようにジョブをスケジュールできます。</span><span class="sxs-lookup"><span data-stu-id="0af4c-111">For example, you can schedule a job to run at the following times:</span></span>  
  
-   <span data-ttu-id="0af4c-112">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントが開始されるたびに、ジョブを実行する。</span><span class="sxs-lookup"><span data-stu-id="0af4c-112">Whenever [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent starts.</span></span>  
  
-   <span data-ttu-id="0af4c-113">コンピューターの CPU 使用率がアイドルとして定義したレベルになったときに、ジョブを実行する。</span><span class="sxs-lookup"><span data-stu-id="0af4c-113">Whenever CPU utilization of the computer is at a level you have defined as idle.</span></span>  
  
-   <span data-ttu-id="0af4c-114">指定した日時に 1 回だけジョブを実行する。</span><span class="sxs-lookup"><span data-stu-id="0af4c-114">One time, at a specific date and time.</span></span>  
  
-   <span data-ttu-id="0af4c-115">定期的なスケジュール。</span><span class="sxs-lookup"><span data-stu-id="0af4c-115">On a recurring schedule.</span></span>  
  
 <span data-ttu-id="0af4c-116">また、ジョブ スケジュールの代わりとして、ジョブの実行によってイベントに応答する警告を作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="0af4c-116">As an alternative to job schedules, you can also create an alert that responds to an event by running a job.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0af4c-117">一度にジョブの 1 つのインスタンスだけを実行できます。</span><span class="sxs-lookup"><span data-stu-id="0af4c-117">Only one instance of the job can be run at a time.</span></span> <span data-ttu-id="0af4c-118">スケジュールどおりに実行されているときに、手動でジョブを実行しようとすると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントはその要求を拒否します。</span><span class="sxs-lookup"><span data-stu-id="0af4c-118">If you try to run a job manually while it is running as scheduled, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent refuses the request.</span></span>  
  
 <span data-ttu-id="0af4c-119">スケジュールされたジョブが実行されないようにするには、次のいずれかの操作を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="0af4c-119">To prevent a scheduled job from running, you must do one of the following:</span></span>  
  
-   <span data-ttu-id="0af4c-120">スケジュールを無効にする。</span><span class="sxs-lookup"><span data-stu-id="0af4c-120">Disable the schedule.</span></span>  
  
-   <span data-ttu-id="0af4c-121">ジョブを無効にする。</span><span class="sxs-lookup"><span data-stu-id="0af4c-121">Disable the job.</span></span>  
  
-   <span data-ttu-id="0af4c-122">ジョブからスケジュールをデタッチする。</span><span class="sxs-lookup"><span data-stu-id="0af4c-122">Detach the schedule from the job.</span></span>  
  
-   <span data-ttu-id="0af4c-123">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービスを停止する。</span><span class="sxs-lookup"><span data-stu-id="0af4c-123">Stop the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service.</span></span>  
  
-   <span data-ttu-id="0af4c-124">スケジュールを削除する。</span><span class="sxs-lookup"><span data-stu-id="0af4c-124">Delete the schedule.</span></span>  
  
 <span data-ttu-id="0af4c-125">スケジュールが無効になっている場合でも、ジョブは警告に応答したときやユーザーが手動で実行したときに実行されます。</span><span class="sxs-lookup"><span data-stu-id="0af4c-125">If the schedule is not enabled, the job can still run in response to an alert or when a user runs the job manually.</span></span> <span data-ttu-id="0af4c-126">ジョブ スケジュールが無効になっているときは、スケジュールを使用するすべてのジョブのスケジュールが無効になります。</span><span class="sxs-lookup"><span data-stu-id="0af4c-126">When a job schedule is not enabled, the schedule is not enabled for any job that uses the schedule.</span></span>  
  
 <span data-ttu-id="0af4c-127">無効になっているスケジュールは、明示的に有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="0af4c-127">You must explicitly re-enable a schedule that has been disabled.</span></span> <span data-ttu-id="0af4c-128">スケジュールを編集しても、スケジュールは自動的に有効になりません。</span><span class="sxs-lookup"><span data-stu-id="0af4c-128">Editing the schedule does not automatically re-enable the schedule.</span></span>  
  
## <a name="scheduling-start-dates"></a><span data-ttu-id="0af4c-129">開始日のスケジュール設定</span><span class="sxs-lookup"><span data-stu-id="0af4c-129">Scheduling Start Dates</span></span>  
 <span data-ttu-id="0af4c-130">スケジュールの開始日は 19900101 以降にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="0af4c-130">The start date of a schedule must be greater than or equal to 19900101.</span></span>  
  
 <span data-ttu-id="0af4c-131">スケジュールをジョブにアタッチする場合は、スケジュールでジョブを最初に実行する際に使用する開始日を確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0af4c-131">When you are attaching a schedule to a job, you should review the start date that the schedule uses to run the job for the first time.</span></span> <span data-ttu-id="0af4c-132">開始日は、スケジュールをジョブにアタッチする日時によって決まります。</span><span class="sxs-lookup"><span data-stu-id="0af4c-132">The start date depends upon the day and time when you attach the schedule to the job.</span></span> <span data-ttu-id="0af4c-133">たとえば、隔週月曜日の午前 8 時に実行されるスケジュールを作成するとします。</span><span class="sxs-lookup"><span data-stu-id="0af4c-133">For example, you create a schedule that runs every other Monday at 8:00 A.M.</span></span> <span data-ttu-id="0af4c-134">2008 年 3 月 3 日月曜日の午前 10 時にジョブを作成した場合、</span><span class="sxs-lookup"><span data-stu-id="0af4c-134">If you create a job at 10:00 A.M.</span></span> <span data-ttu-id="0af4c-135">スケジュールの開始日は 2008 年 3 月 17 日月曜日になります。</span><span class="sxs-lookup"><span data-stu-id="0af4c-135">on Monday, March 3, 2008, the schedule start date is Monday, March 17, 2008.</span></span> <span data-ttu-id="0af4c-136">2008 年 3 月 4 日火曜日に別のジョブを作成した場合、スケジュールの開始日は 2008 年 3 月 10 日月曜日になります。</span><span class="sxs-lookup"><span data-stu-id="0af4c-136">If you create another job on Tuesday, March 4, 2008, the schedule start date is Monday, March 10, 2008.</span></span>  
  
 <span data-ttu-id="0af4c-137">スケジュールの開始日は、スケジュールをジョブにアタッチした後でも変更できます。</span><span class="sxs-lookup"><span data-stu-id="0af4c-137">You can change the schedule start date after you attach the schedule to a job.</span></span>  
  
## <a name="cpu-idle-schedules"></a><span data-ttu-id="0af4c-138">CPU アイドル スケジュール</span><span class="sxs-lookup"><span data-stu-id="0af4c-138">CPU Idle Schedules</span></span>  
 <span data-ttu-id="0af4c-139">CPU リソースを最大限に使用するために、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントに対して CPU アイドル条件を定義できます。</span><span class="sxs-lookup"><span data-stu-id="0af4c-139">To maximize CPU resources, you can define a CPU idle condition for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="0af4c-140">エージェントは、CPU アイドル条件の設定に基づいて、ジョブの実行に最適な時期を決定します。</span><span class="sxs-lookup"><span data-stu-id="0af4c-140">Agent uses the CPU idle condition setting to determine the best time to run jobs.</span></span> <span data-ttu-id="0af4c-141">たとえば、CPU アイドル時と処理量の少ない時期に、インデックスを再構築するジョブをスケジュールできます。</span><span class="sxs-lookup"><span data-stu-id="0af4c-141">For example, you can schedule a job to rebuild indexes during CPU idle time and slow production periods.</span></span>  
  
 <span data-ttu-id="0af4c-142">CPU アイドル時に実行するジョブを定義する前に、通常処理時の CPU の負荷を調べてください。</span><span class="sxs-lookup"><span data-stu-id="0af4c-142">Before you define jobs to run during CPU idle time, determine the load on the CPU during normal processing.</span></span> <span data-ttu-id="0af4c-143">CPU の負荷を調べるには、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] またはパフォーマンス モニターを使用して、サーバー トラフィックを監視し、統計情報を収集します。</span><span class="sxs-lookup"><span data-stu-id="0af4c-143">To do this, use [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] or Performance Monitor to monitor server traffic and collect statistics.</span></span> <span data-ttu-id="0af4c-144">収集した情報を参考にして、CPU アイドル時の比率および時間を設定します。</span><span class="sxs-lookup"><span data-stu-id="0af4c-144">You can then use the information you gather to set the CPU idle time percentage and duration.</span></span>  
  
 <span data-ttu-id="0af4c-145">CPU アイドル条件は、特定の時間にわたり、CPU 使用率が一定の割合を下回っている状態として定義します。</span><span class="sxs-lookup"><span data-stu-id="0af4c-145">Define the CPU idle condition as a percentage below which CPU usage must remain for a specified time.</span></span> <span data-ttu-id="0af4c-146">次に、この時間の長さを設定します。</span><span class="sxs-lookup"><span data-stu-id="0af4c-146">Next, set the amount of time.</span></span> <span data-ttu-id="0af4c-147">指定された長さの時間にわたって CPU 使用率が指定の率を下回ると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントは、CPU アイドル時スケジュールが設定されているすべてのジョブを開始します。</span><span class="sxs-lookup"><span data-stu-id="0af4c-147">When the CPU usage is below the specified percentage for the specified amount of time, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent starts all jobs that have a CPU idle time schedule.</span></span> <span data-ttu-id="0af4c-148">またはパフォーマンスモニターを使用して CPU 使用率を監視する方法の詳細につい [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] ては、「 [Cpu 使用率の監視](../../relational-databases/performance-monitor/monitor-cpu-usage.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0af4c-148">For more information on using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] or Performance Monitor to monitor CPU usage, see [Monitor CPU Usage](../../relational-databases/performance-monitor/monitor-cpu-usage.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="0af4c-149">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="0af4c-149">Related Tasks</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0af4c-150">**説明**</span><span class="sxs-lookup"><span data-stu-id="0af4c-150">**Description**</span></span>|<span data-ttu-id="0af4c-151">**トピック**</span><span class="sxs-lookup"><span data-stu-id="0af4c-151">**Topic**</span></span>|  
|<span data-ttu-id="0af4c-152">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブのスケジュールを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="0af4c-152">Describes how to create a schedule for a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job.</span></span>|[<span data-ttu-id="0af4c-153">スケジュールを作成する</span><span class="sxs-lookup"><span data-stu-id="0af4c-153">Create a Schedule</span></span>](create-a-schedule.md)|  
|<span data-ttu-id="0af4c-154">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブのスケジュールを設定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="0af4c-154">Describes how to schedule a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job.</span></span>|[<span data-ttu-id="0af4c-155">ジョブのスケジュール設定</span><span class="sxs-lookup"><span data-stu-id="0af4c-155">Schedule a Job</span></span>](schedule-a-job.md)|  
|<span data-ttu-id="0af4c-156">使用しているサーバーの CPU アイドル状態を定義する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="0af4c-156">Explains how to define the CPU idle condition for your server.</span></span>|[<span data-ttu-id="0af4c-157">CPU のアイドル時間と期間の設定 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="0af4c-157">Set CPU Idle Time and Duration &#40;SQL Server Management Studio&#41;</span></span>](set-cpu-idle-time-and-duration-sql-server-management-studio.md)|  
  
## <a name="see-also"></a><span data-ttu-id="0af4c-158">参照</span><span class="sxs-lookup"><span data-stu-id="0af4c-158">See Also</span></span>  
 <span data-ttu-id="0af4c-159">[sp_help_jobschedule &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-help-jobschedule-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0af4c-159">[sp_help_jobschedule &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-jobschedule-transact-sql) </span></span>  
 [<span data-ttu-id="0af4c-160">dbo.sysjobschedules &#40;Transact-sql&#41;</span><span class="sxs-lookup"><span data-stu-id="0af4c-160">dbo.sysjobschedules &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-tables/dbo-sysjobschedules-transact-sql)  
  
  
