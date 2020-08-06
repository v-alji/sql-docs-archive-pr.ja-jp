---
title: CmdExec ジョブ ステップの作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- CmdExec jobs
ms.assetid: b48da5b4-6fe7-4eb7-bade-dc7d697c6d5c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 48c557b8ea4228d27b73d361c50aac62232d1e00
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640320"
---
# <a name="create-a-cmdexec-job-step"></a><span data-ttu-id="70c05-102">CmdExec ジョブ ステップの作成</span><span class="sxs-lookup"><span data-stu-id="70c05-102">Create a CmdExec Job Step</span></span>
  <span data-ttu-id="70c05-103">このトピック [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] は、で、、または SQL Server 管理オブジェクトを使用して、実行可能なプログラムまたはオペレーティングシステムコマンドを使用するエージェントジョブステップを作成および定義する方法について説明し [!INCLUDE[tsql](../../includes/tsql-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="70c05-103">This topic describes how to create and define a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job step in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] that uses an executable program or operating system command by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)] or SQL Server Management Objects.</span></span>  
  
 <span data-ttu-id="70c05-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="70c05-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="70c05-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="70c05-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="70c05-106">Security</span><span class="sxs-lookup"><span data-stu-id="70c05-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="70c05-107">**CmdExec ジョブ ステップを作成する方法:**</span><span class="sxs-lookup"><span data-stu-id="70c05-107">**To create a CmdExec job step, using:**</span></span>  
  
     [<span data-ttu-id="70c05-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="70c05-108">SQL Server Management Studio</span></span>](#SSMS)  
  
     [<span data-ttu-id="70c05-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="70c05-109">Transact-SQL</span></span>](#TSQL)  
  
     [<span data-ttu-id="70c05-110">SQL Server 管理オブジェクト</span><span class="sxs-lookup"><span data-stu-id="70c05-110">SQL Server Management Objects</span></span>](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="70c05-111">はじめに</span><span class="sxs-lookup"><span data-stu-id="70c05-111">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="70c05-112">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="70c05-112">Security</span></span>  
 <span data-ttu-id="70c05-113">既定では、 **sysadmin** 固定サーバー ロールのメンバーだけが CmdExec ジョブ ステップを作成できます。</span><span class="sxs-lookup"><span data-stu-id="70c05-113">By default, only members of the **sysadmin** fixed server role can create CmdExec job steps.</span></span> <span data-ttu-id="70c05-114">これらのジョブ ステップは、 **sysadmin** ユーザーがプロキシ アカウントを作成しない限り、SQL Server エージェント サービス アカウントのコンテキストで実行されます。</span><span class="sxs-lookup"><span data-stu-id="70c05-114">These job steps run under the context of the SQL Server Agent service account unless the **sysadmin** user creates a proxy account.</span></span> <span data-ttu-id="70c05-115">**sysadmin** ロールのメンバーではないユーザーでも、CmdExec プロキシ アカウントにアクセスできる場合は CmdExec ジョブ ステップを作成できます。</span><span class="sxs-lookup"><span data-stu-id="70c05-115">Users who are not members of the **sysadmin** role can create CmdExec job steps if they have access to a CmdExec proxy account.</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="70c05-116">Permissions</span><span class="sxs-lookup"><span data-stu-id="70c05-116">Permissions</span></span>  
 <span data-ttu-id="70c05-117">詳細については、「 [SQL Server エージェントのセキュリティの実装](implement-sql-server-agent-security.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="70c05-117">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="70c05-118">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="70c05-118">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-cmdexec-job-step"></a><span data-ttu-id="70c05-119">CmdExec ジョブ ステップを作成するには</span><span class="sxs-lookup"><span data-stu-id="70c05-119">To create a CmdExec job step</span></span>  
  
1.  <span data-ttu-id="70c05-120">**オブジェクトエクスプローラー**で、のインスタンスに接続し、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] そのインスタンスを展開します。</span><span class="sxs-lookup"><span data-stu-id="70c05-120">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="70c05-121">**[SQL Server エージェント]** を展開し、新しいジョブを作成するか、既存のジョブを右クリックして **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="70c05-121">Expand **SQL Server Agent**, create a new job or right-click an existing job, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="70c05-122">**[ジョブのプロパティ]** ダイアログで **[ステップ]** ページをクリックし、 **[新規作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="70c05-122">In the **Job Properties** dialog, click the **Steps** page, and then click **New**.</span></span>  
  
4.  <span data-ttu-id="70c05-123">**[新しいジョブ ステップ]** ダイアログの **[ステップ名]** ボックスにジョブ ステップ名を入力します。</span><span class="sxs-lookup"><span data-stu-id="70c05-123">In the **New Job Step** dialog, type a job **Step name**.</span></span>  
  
5.  <span data-ttu-id="70c05-124">**[種類]** ボックスの一覧の **[オペレーティング システム (CmdExec)]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="70c05-124">In the **Type** list, choose **Operating system (CmdExec)**.</span></span>  
  
6.  <span data-ttu-id="70c05-125">**[実行するアカウント名]** ボックスの一覧で、ジョブで使用する資格情報を備えたプロキシ アカウントをクリックします。</span><span class="sxs-lookup"><span data-stu-id="70c05-125">In **Run as** list, select the proxy account with the credentials that the job will use.</span></span> <span data-ttu-id="70c05-126">既定では、CmdExec ジョブ ステップは SQL Server エージェント サービス アカウントのコンテキストで実行されます。</span><span class="sxs-lookup"><span data-stu-id="70c05-126">By default, CmdExec job steps run under the context of the SQL Server Agent service account.</span></span>  
  
7.  <span data-ttu-id="70c05-127">**[コマンド成功時のプロセス終了コード]** ボックスに、0 ～ 999999 の値を入力します。</span><span class="sxs-lookup"><span data-stu-id="70c05-127">In the **Process exit code of a successful command** box, enter a value from 0 to 999999.</span></span>  
  
8.  <span data-ttu-id="70c05-128">**[コマンド]** ボックスに、オペレーティング システム コマンドまたは実行可能プログラムを入力します。</span><span class="sxs-lookup"><span data-stu-id="70c05-128">In the **Command** box, enter the operating system command or executable program.</span></span> <span data-ttu-id="70c05-129">例については、「Transact T-SQL の使用」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="70c05-129">See "Using Transact T-SQL for an example.</span></span>  
  
9. <span data-ttu-id="70c05-130">**[詳細設定]** ページをクリックして、ジョブが成功または失敗した場合の操作、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントによるジョブ ステップ実行の試行回数、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントでジョブ ステップの出力を書き込むファイルなど、ジョブ ステップのオプションを設定します。</span><span class="sxs-lookup"><span data-stu-id="70c05-130">Click the **Advanced** page to set job step options, such as: what action to take if the job step succeeds or fails, how many times [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent should try to execute the job step, and the file where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent can write the job step output.</span></span> <span data-ttu-id="70c05-131">**sysadmin** 固定サーバー ロールのメンバーだけが、オペレーティング システム ファイルにジョブ ステップの出力を書き込むことができます。</span><span class="sxs-lookup"><span data-stu-id="70c05-131">Only members of the **sysadmin** fixed server role can write job step output to an operating system file.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="70c05-132">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="70c05-132">Using Transact-SQL</span></span>  
  
### <a name="to-create-a-cmdexec-job-step"></a><span data-ttu-id="70c05-133">CmdExec ジョブ ステップを作成するには</span><span class="sxs-lookup"><span data-stu-id="70c05-133">To create a CmdExec job step</span></span>  
  
1.  <span data-ttu-id="70c05-134">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="70c05-134">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="70c05-135">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="70c05-135">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="70c05-136">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="70c05-136">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```sql
    -- creates a job step that uses CmdExec  
    USE msdb;  
    GO  
    EXEC sp_add_jobstep  
        @job_name = N'Weekly Sales Data Backup',  
        @step_name = N'Set database to read only',  
        @subsystem = N'CMDEXEC',  
        @command = C:\clickme_scripts\SQL11\PostBOLReorg GetHsX.exe',   
        @retry_attempts = 5,  
        @retry_interval = 5 ;  
    GO  
    ```  
  
 <span data-ttu-id="70c05-137">詳細については、「 [sp_add_jobstep &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="70c05-137">For more information, see [sp_add_jobstep &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql)</span></span>  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="70c05-138">SQL Server 管理オブジェクトの使用</span><span class="sxs-lookup"><span data-stu-id="70c05-138">Using SQL Server Management Objects</span></span>  

### <a name="to-create-a-cmdexec-job-step"></a><span data-ttu-id="70c05-139">CmdExec ジョブ ステップを作成するには</span><span class="sxs-lookup"><span data-stu-id="70c05-139">To create a CmdExec job step</span></span>
  
 <span data-ttu-id="70c05-140">`JobStep`Visual Basic、Visual C#、PowerShell など、選択したプログラミング言語でクラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="70c05-140">Use the `JobStep` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span>  
