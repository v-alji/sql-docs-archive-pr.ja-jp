---
title: ActiveX スクリプト ジョブ ステップの作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- ActiveX scripting jobs [SQL Server]
- job steps [Analysis Services]
ms.assetid: e6c46c6b-2d61-4571-bc8e-a831cd6e6302
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6604ba75af7acdd5bd2521433e8310c74150ce8f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711582"
---
# <a name="create-an-activex-script-job-step"></a><span data-ttu-id="7cccc-102">Create an ActiveX Script Job Step</span><span class="sxs-lookup"><span data-stu-id="7cccc-102">Create an ActiveX Script Job Step</span></span>
  <span data-ttu-id="7cccc-103">このトピック [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 、で、、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または SQL Server 管理オブジェクトを使用して、ActiveX スクリプトを実行するエージェントジョブステップを作成および定義する方法について説明し [!INCLUDE[tsql](../../includes/tsql-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="7cccc-103">This topic describes how to create and define a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job step in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] that executes an ActiveX script by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or SQL Server Management Objects.</span></span>  
  
-   <span data-ttu-id="7cccc-104">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="7cccc-104">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="7cccc-105">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="7cccc-105">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="7cccc-106">Security</span><span class="sxs-lookup"><span data-stu-id="7cccc-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="7cccc-107">**Transact-SQL ジョブ ステップを作成する方法:**</span><span class="sxs-lookup"><span data-stu-id="7cccc-107">**To create a Transact-SQL job step, using:**</span></span>  
  
     [<span data-ttu-id="7cccc-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="7cccc-108">SQL Server Management Studio</span></span>](#SSMS)  
  
     [<span data-ttu-id="7cccc-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="7cccc-109">Transact-SQL</span></span>](#TSQL)  
  
     [<span data-ttu-id="7cccc-110">SQL Server 管理オブジェクト</span><span class="sxs-lookup"><span data-stu-id="7cccc-110">SQL Server Management Objects</span></span>](#SMO)  
  
## <a name="before-you-begin"></a><span data-ttu-id="7cccc-111">はじめに</span><span class="sxs-lookup"><span data-stu-id="7cccc-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="7cccc-112">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="7cccc-112">Limitations and Restrictions</span></span>  
 [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="7cccc-113">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="7cccc-113">Security</span></span>  
 <span data-ttu-id="7cccc-114">詳細については、「 [SQL Server エージェントのセキュリティの実装](implement-sql-server-agent-security.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="7cccc-114">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="7cccc-115">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="7cccc-115">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-an-activex-script-job-step"></a><span data-ttu-id="7cccc-116">ActiveX スクリプト ジョブ ステップを作成するには</span><span class="sxs-lookup"><span data-stu-id="7cccc-116">To create an ActiveX Script job step</span></span>  
  
1.  <span data-ttu-id="7cccc-117">**オブジェクトエクスプローラー**で、のインスタンスに接続し、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] そのインスタンスを展開します。</span><span class="sxs-lookup"><span data-stu-id="7cccc-117">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="7cccc-118">**[SQL Server エージェント]** を展開し、新しいジョブを作成するか、既存のジョブを右クリックして **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7cccc-118">Expand **SQL Server Agent**, create a new job or right-click an existing job, and then click **Properties**.</span></span> <span data-ttu-id="7cccc-119">ジョブの作成の詳細については、「 [ジョブの作成](create-jobs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7cccc-119">For more information on creating a job, see [Creating Jobs](create-jobs.md).</span></span>  
  
3.  <span data-ttu-id="7cccc-120">**[ジョブのプロパティ]** ダイアログで **[ステップ]** ページをクリックし、 **[新規作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7cccc-120">In the **Job Properties** dialog, click the **Steps** page, and then click **New**.</span></span>  
  
4.  <span data-ttu-id="7cccc-121">**[新しいジョブ ステップ]** ダイアログの **[ステップ名]** ボックスにジョブ ステップ名を入力します。</span><span class="sxs-lookup"><span data-stu-id="7cccc-121">In the **New Job Step** dialog, type a job **Step name**.</span></span>  
  
5.  <span data-ttu-id="7cccc-122">**[種類]** ボックスの一覧で **[ActiveX スクリプト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7cccc-122">In the **Type** list, click **ActiveX Script**.</span></span>  
  
6.  <span data-ttu-id="7cccc-123">**[実行するアカウント名]** ボックスの一覧で、ジョブで使用する資格情報を備えたプロキシ アカウントをクリックします。</span><span class="sxs-lookup"><span data-stu-id="7cccc-123">In the **Run as** list, select the proxy account with the credentials that the job will use.</span></span>  
  
7.  <span data-ttu-id="7cccc-124">**[言語]** でスクリプトを記述する言語を選択します。</span><span class="sxs-lookup"><span data-stu-id="7cccc-124">Select the **Language** in which the script was written.</span></span> <span data-ttu-id="7cccc-125">または、 **[その他]** をクリックして、スクリプトの記述に使用する [!INCLUDE[msCoName](../../includes/msconame-md.md)] ActiveX スクリプティング言語の名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="7cccc-125">Alternatively, click **Other** and then enter the name of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] ActiveX scripting language in which the script will be written.</span></span>  
  
8.  <span data-ttu-id="7cccc-126">**[コマンド]** ボックスに、ジョブ ステップで実行するスクリプト構文を入力します。</span><span class="sxs-lookup"><span data-stu-id="7cccc-126">In the **Command** box, enter the script syntax that will be executed for the job step.</span></span> <span data-ttu-id="7cccc-127">または、 **[開く]** をクリックしてスクリプト構文が記述されたファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="7cccc-127">Alternately, click **Open** and select a file containing the script syntax.</span></span>  
  
9. <span data-ttu-id="7cccc-128">**[詳細設定]** ページをクリックして、ジョブ ステップのオプションのうち、ジョブ ステップが成功または失敗した場合のアクション、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントによるジョブ ステップの再試行回数、および再試行間隔を設定します。</span><span class="sxs-lookup"><span data-stu-id="7cccc-128">Click the **Advanced** page to set the following job step options: what action to take if the job step succeeds or fails, how many times [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent should try to execute the job step, and how often retry attempts should be made.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="7cccc-129">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="7cccc-129">Using Transact-SQL</span></span>  
  
#### <a name="to-create-an-activex-script-job-step"></a><span data-ttu-id="7cccc-130">ActiveX スクリプト ジョブ ステップを作成するには</span><span class="sxs-lookup"><span data-stu-id="7cccc-130">To create an ActiveX Script job step</span></span>  
  
1.  <span data-ttu-id="7cccc-131">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="7cccc-131">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="7cccc-132">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7cccc-132">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="7cccc-133">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7cccc-133">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```sql
    -- create an ActiveX Script job step written in VBScript that creates a restore point  
    USE msdb;  
    GO  
    EXEC sp_add_jobstep  
        @job_name = N'Weekly Sales Data Backup',  
        @step_name = N'Create a restore point',  
        @subsystem = N'ACTIVESCRIPTING',  
        @command = N'Const RESTORE_POINT = 20  
  
    strComputer = "."  
    Set objWMIService = GetObject("winmgmts:" _  
        & "{impersonationLevel=impersonate}!\\" & strComputer & "\root\default")  
  
    Set objItem = objWMIService.Get("SystemRestore")  
    errResults = objItem.Restore(RESTORE_POINT)',   
        @retry_attempts = 5,  
        @retry_interval = 5 ;  
    GO  
    ```  
  
 <span data-ttu-id="7cccc-134">詳細については、「 [sp_add_jobstep &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7cccc-134">For more information, see [sp_add_jobstep &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql).</span></span>  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="7cccc-135">SQL Server 管理オブジェクトの使用</span><span class="sxs-lookup"><span data-stu-id="7cccc-135">Using SQL Server Management Objects</span></span>  
 <span data-ttu-id="7cccc-136">**ActiveX スクリプト ジョブ ステップを作成するには**</span><span class="sxs-lookup"><span data-stu-id="7cccc-136">**To create an ActiveX Script job step**</span></span>  
  
 <span data-ttu-id="7cccc-137">`JobStep`Visual Basic、Visual C#、PowerShell など、選択したプログラミング言語でクラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="7cccc-137">Use the `JobStep` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span>  
