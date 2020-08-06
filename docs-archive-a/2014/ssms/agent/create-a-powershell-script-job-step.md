---
title: PowerShell スクリプト ジョブ ステップの作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- PowerShell [SQL Server], job steps
- jobs [SQL Server Agent], PowerShell
- job steps [PowerShell]
- SQL Server Agent jobs, PowerShell steps
ms.assetid: 50afcf84-fae0-4eb5-9b0f-f2cf144c1433
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4232cdfa584fdcc2e13786ecc9bd00f0c6fe7066
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640322"
---
# <a name="create-a-powershell-script-job-step"></a><span data-ttu-id="2a377-102">Create a PowerShell Script Job Step</span><span class="sxs-lookup"><span data-stu-id="2a377-102">Create a PowerShell Script Job Step</span></span>
  <span data-ttu-id="2a377-103">このトピックでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] または [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] を使用して、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] で PowerShell スクリプトを実行する [!INCLUDE[tsql](../../includes/tsql-md.md)]エージェント ジョブ ステップを作成して定義する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="2a377-103">This topic describes how to create and define a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job step that executes a PowerShell script in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="2a377-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="2a377-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="2a377-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="2a377-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="2a377-106">Security</span><span class="sxs-lookup"><span data-stu-id="2a377-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="2a377-107">**PowerShell スクリプト ジョブ ステップを作成する方法:**</span><span class="sxs-lookup"><span data-stu-id="2a377-107">**To create a PowerShell Script job step, using:**</span></span>  
  
     [<span data-ttu-id="2a377-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="2a377-108">SQL Server Management Studio</span></span>](#SSMS)  
  
     [<span data-ttu-id="2a377-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="2a377-109">Transact-SQL</span></span>](#TSQL)  
  
     [<span data-ttu-id="2a377-110">SQL Server 管理オブジェクト</span><span class="sxs-lookup"><span data-stu-id="2a377-110">SQL Server Management Objects</span></span>](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="2a377-111">はじめに</span><span class="sxs-lookup"><span data-stu-id="2a377-111">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="2a377-112">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="2a377-112">Security</span></span>  
 <span data-ttu-id="2a377-113">詳細については、「 [SQL Server エージェントのセキュリティの実装](implement-sql-server-agent-security.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="2a377-113">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="2a377-114">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="2a377-114">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-powershell-script-job-step"></a><span data-ttu-id="2a377-115">PowerShell スクリプト ジョブ ステップを作成するには</span><span class="sxs-lookup"><span data-stu-id="2a377-115">To create a PowerShell Script job step</span></span>  
  
1.  <span data-ttu-id="2a377-116">**オブジェクトエクスプローラー**で、のインスタンスに接続し、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] そのインスタンスを展開します。</span><span class="sxs-lookup"><span data-stu-id="2a377-116">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="2a377-117">**[SQL Server エージェント]** を展開し、新しいジョブを作成するか、既存のジョブを右クリックして **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2a377-117">Expand **SQL Server Agent**, create a new job or right-click an existing job, and then click **Properties**.</span></span> <span data-ttu-id="2a377-118">ジョブの作成の詳細については、「 [ジョブの作成](create-jobs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2a377-118">For more information on creating a job, see [Creating Jobs](create-jobs.md).</span></span>  
  
3.  <span data-ttu-id="2a377-119">**[ジョブのプロパティ]** ダイアログで **[ステップ]** ページをクリックし、 **[新規作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2a377-119">In the **Job Properties** dialog, click the **Steps** page, and then click **New**.</span></span>  
  
4.  <span data-ttu-id="2a377-120">**[新しいジョブ ステップ]** ダイアログの **[ステップ名]** ボックスにジョブ ステップ名を入力します。</span><span class="sxs-lookup"><span data-stu-id="2a377-120">In the **New Job Step** dialog, type a job **Step name**.</span></span>  
  
5.  <span data-ttu-id="2a377-121">**[種類]** ボックスの一覧で **[PowerShell]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2a377-121">In the **Type** list, click **PowerShell**.</span></span>  
  
6.  <span data-ttu-id="2a377-122">**[実行するアカウント名]** ボックスの一覧で、ジョブで使用する資格情報を備えたプロキシ アカウントをクリックします。</span><span class="sxs-lookup"><span data-stu-id="2a377-122">In the **Run as** list, select the proxy account with the credentials that the job will use.</span></span>  
  
7.  <span data-ttu-id="2a377-123">**[コマンド]** ボックスに、ジョブ ステップで実行する PowerShell スクリプト構文を入力します。</span><span class="sxs-lookup"><span data-stu-id="2a377-123">In the **Command** box, enter the PowerShell script syntax that will be executed for the job step.</span></span> <span data-ttu-id="2a377-124">または、 **[開く]** をクリックしてスクリプト構文が記述されたファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="2a377-124">Alternately, click **Open** and select a file containing the script syntax.</span></span> <span data-ttu-id="2a377-125">PowerShell スクリプトの例については、以下の「 **Transact-SQL の使用** 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2a377-125">For an example of a PowerShell script, see **Using Transact-SQL** below.</span></span>  
  
8.  <span data-ttu-id="2a377-126">**[詳細設定]** ページをクリックして、ジョブ ステップのオプションのうち、ジョブ ステップが成功または失敗した場合のアクション、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントによるジョブ ステップの再試行回数、および再試行間隔を設定します。</span><span class="sxs-lookup"><span data-stu-id="2a377-126">Click the **Advanced** page to set the following job step options: what action to take if the job step succeeds or fails, how many times [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent should try to execute the job step, and how often retry attempts should be made.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="2a377-127">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="2a377-127">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-powershell-script-job-step"></a><span data-ttu-id="2a377-128">PowerShell スクリプト ジョブ ステップを作成するには</span><span class="sxs-lookup"><span data-stu-id="2a377-128">To create a PowerShell Script job step</span></span>  
  
1.  <span data-ttu-id="2a377-129">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="2a377-129">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="2a377-130">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2a377-130">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="2a377-131">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2a377-131">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```sql
    -- creates a PowerShell job step that finds the processes that use more than 1000 MB of memory and kills them  
    USE msdb;  
    GO  
    EXEC sp_add_jobstep  
        @job_name = N'Weekly Sales Data Backup',  
        @step_name = N'Kills all processes that use more than 1000 MB of memory',  
        @subsystem = N'PowerShell',  
        @command = N'Get-Process | Where-Object { $_.WS -gt 1000MB } | Stop-Process',   
        @retry_attempts = 5,  
        @retry_interval = 5 ;  
    GO  
    ```  
  
 <span data-ttu-id="2a377-132">詳細については、「 [sp_add_jobstep &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2a377-132">For more information, see [sp_add_jobstep &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql).</span></span>  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="2a377-133">SQL Server 管理オブジェクトの使用</span><span class="sxs-lookup"><span data-stu-id="2a377-133">Using SQL Server Management Objects</span></span>  
 <span data-ttu-id="2a377-134">**PowerShell スクリプト ジョブ ステップを作成するには**</span><span class="sxs-lookup"><span data-stu-id="2a377-134">**To create a PowerShell Script job step**</span></span>  
  
 <span data-ttu-id="2a377-135">`JobStep`Visual Basic、Visual C#、PowerShell など、選択したプログラミング言語でクラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="2a377-135">Use the `JobStep` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span>  
