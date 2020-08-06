---
title: スケジュールを作成する | Microsoft Docs
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
- schedules [SQL Server], jobs
ms.assetid: 8c7ef3b3-c06d-4a27-802d-ed329dc86ef3
author: stevestein
ms.author: sstein
ms.openlocfilehash: ac71a61163dceb06697b61ef24fce2117d57cf2f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644284"
---
# <a name="create-a-schedule"></a><span data-ttu-id="84167-102">Create a Schedule</span><span class="sxs-lookup"><span data-stu-id="84167-102">Create a Schedule</span></span>
  <span data-ttu-id="84167-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、または SQL Server 管理オブジェクトを使用して、 [!INCLUDE[tsql](../../includes/tsql-md.md)]エージェントのジョブのスケジュールを作成できます。</span><span class="sxs-lookup"><span data-stu-id="84167-103">You can create a schedule for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or SQL Server Management Objects.</span></span>  
  
-   <span data-ttu-id="84167-104">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="84167-104">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="84167-105">Security</span><span class="sxs-lookup"><span data-stu-id="84167-105">Security</span></span>](#Security)  
  
-   <span data-ttu-id="84167-106">**スケジュールを作成する方法:**</span><span class="sxs-lookup"><span data-stu-id="84167-106">**To create a schedule, using:**</span></span>  
  
     [<span data-ttu-id="84167-107">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="84167-107">SQL Server Management Studio</span></span>](#SSMS)  
  
     [<span data-ttu-id="84167-108">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="84167-108">Transact-SQL</span></span>](#TSQL)  
  
     [<span data-ttu-id="84167-109">SQL Server 管理オブジェクト</span><span class="sxs-lookup"><span data-stu-id="84167-109">SQL Server Management Objects</span></span>](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="84167-110">はじめに</span><span class="sxs-lookup"><span data-stu-id="84167-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="84167-111">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="84167-111">Security</span></span>  
 <span data-ttu-id="84167-112">詳細については、「 [SQL Server エージェントのセキュリティの実装](implement-sql-server-agent-security.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="84167-112">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="84167-113">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="84167-113">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-schedule"></a><span data-ttu-id="84167-114">スケジュールを作成するには</span><span class="sxs-lookup"><span data-stu-id="84167-114">To create a schedule</span></span>  
  
1.  <span data-ttu-id="84167-115">**オブジェクトエクスプローラー**で、のインスタンスに接続し、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] そのインスタンスを展開します。</span><span class="sxs-lookup"><span data-stu-id="84167-115">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="84167-116">**[SQL Server エージェント]** を展開し、 **[ジョブ]** を右クリックして、 **[スケジュールの管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="84167-116">Expand **SQL Server Agent**, right-click **Jobs**, and select **Manage Schedules**.</span></span>  
  
3.  <span data-ttu-id="84167-117">**[スケジュールの管理]** ダイアログ ボックスで **[新規作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="84167-117">In the **Manage Schedules** dialog box, click **New**.</span></span>  
  
4.  <span data-ttu-id="84167-118">**[名前]** ボックスに新しいスケジュールの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="84167-118">In the **Name** box, type a name for the new schedule.</span></span>  
  
5.  <span data-ttu-id="84167-119">スケジュールを作成してもすぐに有効にしない場合は、 **[有効]** チェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="84167-119">If you do not want the schedule to take effect immediately after it has been created, clear the **Enabled** check box.</span></span>  
  
6.  <span data-ttu-id="84167-120">**[スケジュールの種類]** ボックスの一覧で、次のいずれかを選択します。</span><span class="sxs-lookup"><span data-stu-id="84167-120">For **Schedule Type**, select one of the following:</span></span>  
  
    -   <span data-ttu-id="84167-121">CPU がアイドル状態になったときにジョブを開始するには、 **[CPU がアイドル状態になったときに開始]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="84167-121">To start the job when the CPUs reach an idle condition, click **Start whenever the CPUs become idle**.</span></span>  
  
    -   <span data-ttu-id="84167-122">スケジュールを繰り返し実行する場合は **[定期的]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="84167-122">If you want a schedule to run repeatedly, click **Recurring**.</span></span> <span data-ttu-id="84167-123">定期的なスケジュールを設定するには、ダイアログ ボックス上の **[頻度]**、 **[一日のうちの頻度]**、および **[実行時間]** のグループに値を指定します。</span><span class="sxs-lookup"><span data-stu-id="84167-123">To set the recurring schedule, complete the **Frequency**, **Daily Frequency**, and **Duration** groups on the dialog.</span></span>  
  
    -   <span data-ttu-id="84167-124">スケジュールを一度だけ実行するには、 **[指定日時]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="84167-124">If you want the schedule to run only one time, click **One time**.</span></span> <span data-ttu-id="84167-125">**指定日時** のスケジュールを設定するには、ダイアログ ボックス上の **[指定日時に発生]** グループに値を指定します。</span><span class="sxs-lookup"><span data-stu-id="84167-125">To set the **One time** schedule, complete the **One-time occurrence** group on the dialog box.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="84167-126">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="84167-126">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-schedule"></a><span data-ttu-id="84167-127">スケジュールを作成するには</span><span class="sxs-lookup"><span data-stu-id="84167-127">To create a schedule</span></span>  
  
1.  <span data-ttu-id="84167-128">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="84167-128">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="84167-129">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="84167-129">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="84167-130">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="84167-130">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```sql
    -- creates a schedule named RunOnce.   
    -- The schedule runs one time, at 23:30 on the day that the schedule is created.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_add_schedule  
        @schedule_name = N'RunOnce',  
        @freq_type = 1,  
        @active_start_time = 233000 ;  
  
    GO  
    ```  
  
 <span data-ttu-id="84167-131">詳細については、「 [sp_add_schedule &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-add-schedule-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="84167-131">For more information, see [sp_add_schedule &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-schedule-transact-sql).</span></span>  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="84167-132">SQL Server 管理オブジェクトの使用</span><span class="sxs-lookup"><span data-stu-id="84167-132">Using SQL Server Management Objects</span></span>  
 <span data-ttu-id="84167-133">**スケジュールを作成するには**</span><span class="sxs-lookup"><span data-stu-id="84167-133">**To create a schedule**</span></span>  
  
 <span data-ttu-id="84167-134">`JobSchedule`Visual Basic、Visual C#、PowerShell など、選択したプログラミング言語でクラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="84167-134">Use the `JobSchedule` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span> <span data-ttu-id="84167-135">詳細については、「 [SQL Server 管理オブジェクト (SMO) プログラミング ガイド](https://msdn.microsoft.com/library/ms162169.aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="84167-135">For more information, see [SQL Server Management Objects (SMO)](https://msdn.microsoft.com/library/ms162169.aspx).</span></span>  
