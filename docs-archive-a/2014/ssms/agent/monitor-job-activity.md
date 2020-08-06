---
title: ジョブの利用状況の監視 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, monitoring
- jobs [SQL Server Agent], monitoring
- monitoring [SQL Server], jobs
- activity monitoring [SQL Server Agent]
- monitoring [SQL Server], SQL Server Agent
- monitoring [SQL Server Agent]
- SQL Server Agent Job Activity Monitor
- SQL Server Agent jobs, monitoring
- performance [SQL Server], jobs
- current activity
ms.assetid: 71cb432b-631d-4b8b-9965-e731b3d8266d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5088e029e90b4556c1559f8c948e8a8734762749
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634792"
---
# <a name="monitor-job-activity"></a><span data-ttu-id="1c55d-102">ジョブの利用状況の監視</span><span class="sxs-lookup"><span data-stu-id="1c55d-102">Monitor Job Activity</span></span>
  <span data-ttu-id="1c55d-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのジョブの利用状況モニターを使用すると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスで定義されているすべてのジョブの現在の利用状況を監視できます。</span><span class="sxs-lookup"><span data-stu-id="1c55d-103">You can monitor the current activity of all defined jobs on an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent Job Activity Monitor.</span></span>  
  
## <a name="sql-server-agent-sessions"></a><span data-ttu-id="1c55d-104">SQL Server エージェント セッション</span><span class="sxs-lookup"><span data-stu-id="1c55d-104">SQL Server Agent Sessions</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="1c55d-105">エージェントでは、サービスが開始されるたびに新しいセッションが作成されます。</span><span class="sxs-lookup"><span data-stu-id="1c55d-105">Agent creates a new session each time the service starts.</span></span> <span data-ttu-id="1c55d-106">新しいセッションが作成されると、すべての既存の定義済みジョブが、 **msdb** データベースの **sysjobactivity** テーブルに設定されます。</span><span class="sxs-lookup"><span data-stu-id="1c55d-106">When a new session is created, the **sysjobactivity** table in the **msdb** database is populated with all the existing defined jobs.</span></span> <span data-ttu-id="1c55d-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントを再起動したときには、ジョブの前回の利用状況がこのテーブルに保持されています。</span><span class="sxs-lookup"><span data-stu-id="1c55d-107">This table preserves the last activity for jobs when [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent is restarted.</span></span> <span data-ttu-id="1c55d-108">各セッションでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントの通常のジョブの利用状況が、開始から終了まで記録されます。</span><span class="sxs-lookup"><span data-stu-id="1c55d-108">Each session records [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent normal job activity from the start of the job to its finish.</span></span> <span data-ttu-id="1c55d-109">これらのセッションに関する情報は、 **msdb** データベースの **syssessions** テーブルに格納されます。</span><span class="sxs-lookup"><span data-stu-id="1c55d-109">Information about these sessions is stored in the **syssessions** table of the **msdb** database.</span></span>  
  
## <a name="job-activity-monitor"></a><span data-ttu-id="1c55d-110">[ジョブの利用状況モニター]</span><span class="sxs-lookup"><span data-stu-id="1c55d-110">Job Activity Monitor</span></span>  
 <span data-ttu-id="1c55d-111">ジョブの利用状況モニターを使用すると、 **で** sysjobactivity [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]テーブルを表示できるようになります。</span><span class="sxs-lookup"><span data-stu-id="1c55d-111">The Job Activity Monitor allows you to view the **sysjobactivity** table by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="1c55d-112">サーバーのすべてのジョブを表示するか、またはフィルターを定義して表示されるジョブの数を制限できます。</span><span class="sxs-lookup"><span data-stu-id="1c55d-112">You can view all jobs on the server, or you can define filters to limit the number of jobs displayed.</span></span> <span data-ttu-id="1c55d-113">また、 **[エージェント ジョブの利用状況]** グリッドの列見出しをクリックすることによって、ジョブ情報を並べ替えることもできます。</span><span class="sxs-lookup"><span data-stu-id="1c55d-113">You can also sort the job information by clicking on a column heading in the **Agent Job Activity** grid.</span></span> <span data-ttu-id="1c55d-114">たとえば、 **[最終実行]** 列見出しをクリックすると、最後に実行された順にジョブを並べ替えることができます。</span><span class="sxs-lookup"><span data-stu-id="1c55d-114">For example, when you select the **Last Run** column heading, you can view the jobs in the order that they were last run.</span></span> <span data-ttu-id="1c55d-115">もう一度この列見出しをクリックすると、最終実行日時に基づいて、ジョブの昇順と降順が切り替わります。</span><span class="sxs-lookup"><span data-stu-id="1c55d-115">Clicking the column heading again toggles the jobs in ascending and descending order based on their last run date.</span></span>  
  
 <span data-ttu-id="1c55d-116">ジョブの利用状況モニターで実行できる操作は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="1c55d-116">Using the Job Activity Monitor you can perform the following tasks:</span></span>  
  
-   <span data-ttu-id="1c55d-117">ジョブを開始および停止を行う。</span><span class="sxs-lookup"><span data-stu-id="1c55d-117">Start and stop jobs.</span></span>  
  
-   <span data-ttu-id="1c55d-118">ジョブのプロパティを表示する。</span><span class="sxs-lookup"><span data-stu-id="1c55d-118">View job properties.</span></span>  
  
-   <span data-ttu-id="1c55d-119">特定のジョブの履歴を表示する。</span><span class="sxs-lookup"><span data-stu-id="1c55d-119">View the history for a specific job.</span></span>  
  
-   <span data-ttu-id="1c55d-120">**[エージェント ジョブの利用状況]** グリッドの情報を手動で更新したり、 **[更新の設定を表示します]** をクリックして自動更新間隔を設定したりする。</span><span class="sxs-lookup"><span data-stu-id="1c55d-120">Refresh the information in the **Agent Job Activity** grid manually or set an automatic refresh interval by clicking **View refresh settings**.</span></span>  
  
 <span data-ttu-id="1c55d-121">ジョブの利用状況モニターは、実行のスケジュールが設定されているジョブ、現在のセッション中に実行されたジョブの最終結果、および現在実行中であるかまたはアイドル状態のジョブを確認する場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="1c55d-121">Use the Job Activity Monitor when you want to find out what jobs are scheduled to run, the last outcome of jobs that have run during the current session, and to find out which jobs are currently running or idle.</span></span> <span data-ttu-id="1c55d-122">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービスが予期せず停止した場合、ジョブの利用状況モニターで以前のセッションを参照することにより、サービスが停止したときに実行中であったジョブを確認できます。</span><span class="sxs-lookup"><span data-stu-id="1c55d-122">If the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service fails unexpectedly, you can determine which jobs were in the middle of being executed by looking at the previous session in the Job Activity Monitor.</span></span>  
  
 <span data-ttu-id="1c55d-123">ジョブの利用状況モニターを開くには、 **のオブジェクト エクスプローラーで** [SQL Server エージェント] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] を展開します。次に、 **[ジョブの利用状況モニター]** を右クリックして、 **[ジョブの利用状況の表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1c55d-123">To open the Job Activity Monitor, expand **SQL Server Agent** in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] Object Explorer, right-click **Job Activity Monitor**, and click **View Job Activity**.</span></span>  
  
 <span data-ttu-id="1c55d-124">ストアド プロシージャ **sp_help_jobactivity**を使用することによって、現在のセッションのジョブの利用状況を表示することもできます。</span><span class="sxs-lookup"><span data-stu-id="1c55d-124">You can also view job activity for the current session by using the stored procedure **sp_help_jobactivity**.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="1c55d-125">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="1c55d-125">Related Tasks</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1c55d-126">**説明**</span><span class="sxs-lookup"><span data-stu-id="1c55d-126">**Description**</span></span>|<span data-ttu-id="1c55d-127">**トピック**</span><span class="sxs-lookup"><span data-stu-id="1c55d-127">**Topic**</span></span>|  
|<span data-ttu-id="1c55d-128">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブの実行状態を表示する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="1c55d-128">Describes how to view the runtime state of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs.</span></span>|<span data-ttu-id="1c55d-129">[[ジョブの利用状況の表示]](view-job-activity.md)</span><span class="sxs-lookup"><span data-stu-id="1c55d-129">[View Job Activity](view-job-activity.md)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1c55d-130">参照</span><span class="sxs-lookup"><span data-stu-id="1c55d-130">See Also</span></span>  
 <span data-ttu-id="1c55d-131">[ジョブの利用状況の表示](view-job-activity.md) </span><span class="sxs-lookup"><span data-stu-id="1c55d-131">[View Job Activity](view-job-activity.md) </span></span>  
 <span data-ttu-id="1c55d-132">[dbo.sysjobactivity &#40;Transact-sql&#41;](/sql/relational-databases/system-tables/dbo-sysjobactivity-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="1c55d-132">[dbo.sysjobactivity &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/dbo-sysjobactivity-transact-sql) </span></span>  
 <span data-ttu-id="1c55d-133">[dbo.sysセッション &#40;Transact-sql&#41;](/sql/relational-databases/system-tables/dbo-syssessions-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="1c55d-133">[dbo.syssessions &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/dbo-syssessions-transact-sql) </span></span>  
 [<span data-ttu-id="1c55d-134">sp_help_jobactivity &#40;Transact-sql&#41;</span><span class="sxs-lookup"><span data-stu-id="1c55d-134">sp_help_jobactivity &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-help-jobactivity-transact-sql)  
  
  
