---
title: Transact-SQL ジョブ ステップの作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- Transact-SQL job step
- job steps [Transact-SQL]
- SQL Server Agent jobs, Transact-SQL step
ms.assetid: 69c571a7-debe-4063-9d38-e4b6a1e8e84c
author: stevestein
ms.author: sstein
ms.openlocfilehash: b83ee944d2ca5c10ff1b77f3e6e6da6054b5c99a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737471"
---
# <a name="create-a-transact-sql-job-step"></a><span data-ttu-id="bf849-102">Create a Transact-SQL Job Step</span><span class="sxs-lookup"><span data-stu-id="bf849-102">Create a Transact-SQL Job Step</span></span>
  <span data-ttu-id="bf849-103">このトピック [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] では [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 、、、または SQL Server 管理オブジェクトを使用して、でスクリプトを実行するエージェントジョブステップを作成する方法について説明し [!INCLUDE[tsql](../../includes/tsql-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="bf849-103">This topic describes how to create a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job step that executes [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or SQL Server Management Objects.</span></span>  
  
 <span data-ttu-id="bf849-104">ここで作成するジョブ ステップ スクリプトは、ストアド プロシージャおよび拡張ストアド プロシージャを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="bf849-104">These job step scripts may call stored procedures and extended stored procedures.</span></span> <span data-ttu-id="bf849-105">1 つの [!INCLUDE[tsql](../../includes/tsql-md.md)] ジョブ ステップに、複数のバッチおよび埋め込み GO コマンドを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="bf849-105">A single [!INCLUDE[tsql](../../includes/tsql-md.md)] job step can contain multiple batches and embedded GO commands.</span></span> <span data-ttu-id="bf849-106">ジョブの作成の詳細については、「 [ジョブの作成](create-jobs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bf849-106">For more information on creating a job, see [Creating Jobs](create-jobs.md).</span></span>  
  
 <span data-ttu-id="bf849-107">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="bf849-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="bf849-108">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="bf849-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="bf849-109">Security</span><span class="sxs-lookup"><span data-stu-id="bf849-109">Security</span></span>](#Security)  
  
-   <span data-ttu-id="bf849-110">**Transact-SQL ジョブ ステップを作成する方法:**</span><span class="sxs-lookup"><span data-stu-id="bf849-110">**To create a Transact-SQL job step, using:**</span></span>  
  
     [<span data-ttu-id="bf849-111">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="bf849-111">SQL Server Management Studio</span></span>](#SSMS)  
  
     [<span data-ttu-id="bf849-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="bf849-112">Transact-SQL</span></span>](#TSQL)  
  
     [<span data-ttu-id="bf849-113">SQL Server 管理オブジェクト</span><span class="sxs-lookup"><span data-stu-id="bf849-113">SQL Server Management Objects</span></span>](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="bf849-114">はじめに</span><span class="sxs-lookup"><span data-stu-id="bf849-114">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="bf849-115">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="bf849-115">Security</span></span>  
 <span data-ttu-id="bf849-116">詳細については、「 [SQL Server エージェントのセキュリティの実装](implement-sql-server-agent-security.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="bf849-116">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="bf849-117">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="bf849-117">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-transact-sql-job-step"></a><span data-ttu-id="bf849-118">Transact-SQL ジョブ テップを作成するには</span><span class="sxs-lookup"><span data-stu-id="bf849-118">To create a Transact-SQL job step</span></span>  
  
1.  <span data-ttu-id="bf849-119">**オブジェクトエクスプローラー**で、のインスタンスに接続し、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] そのインスタンスを展開します。</span><span class="sxs-lookup"><span data-stu-id="bf849-119">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="bf849-120">**[SQL Server エージェント]** を展開し、新しいジョブを作成するか、既存のジョブを右クリックして **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bf849-120">Expand **SQL Server Agent**, create a new job or right-click an existing job, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="bf849-121">**[ジョブのプロパティ]** ダイアログで **[ステップ]** ページをクリックし、 **[新規作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bf849-121">In the **Job Properties** dialog, click the **Steps** page, and then click **New**.</span></span>  
  
4.  <span data-ttu-id="bf849-122">**[新しいジョブ ステップ]** ダイアログの **[ステップ名]** ボックスにジョブ ステップ名を入力します。</span><span class="sxs-lookup"><span data-stu-id="bf849-122">In the **New Job Step** dialog, type a job **Step name**.</span></span>  
  
5.  <span data-ttu-id="bf849-123">**[種類]** ボックスの **[Transact-SQL スクリプト (T-SQL)]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bf849-123">In the **Type** list, click **Transact-SQL Script (TSQL)**.</span></span>  
  
6.  <span data-ttu-id="bf849-124">**[コマンド]** ボックスに、 [!INCLUDE[tsql](../../includes/tsql-md.md)] コマンド バッチを入力するか、または **[開く]** をクリックしてコマンドとして使用する [!INCLUDE[tsql](../../includes/tsql-md.md)] ファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="bf849-124">In the **Command** box, type the [!INCLUDE[tsql](../../includes/tsql-md.md)] command batches, or click **Open** to select a [!INCLUDE[tsql](../../includes/tsql-md.md)] file to use as the command.</span></span>  
  
7.  <span data-ttu-id="bf849-125">**[解析]** をクリックして構文をチェックします。</span><span class="sxs-lookup"><span data-stu-id="bf849-125">Click **Parse** to check your syntax.</span></span>  
  
8.  <span data-ttu-id="bf849-126">構文が正しい場合は、成功を示すメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="bf849-126">The message "Parse succeeded" is displayed when your syntax is correct.</span></span> <span data-ttu-id="bf849-127">エラーが見つかった場合は、構文を訂正しないと先に進めません。</span><span class="sxs-lookup"><span data-stu-id="bf849-127">If an error is found, correct the syntax before continuing.</span></span>  
  
9. <span data-ttu-id="bf849-128">**[詳細設定]** ページをクリックして、ジョブ ステップが成功または失敗した場合の操作、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントによるジョブ ステップ実行の試行回数、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントでジョブ ステップの出力を書き込むファイルまたはテーブルなど、ジョブ ステップのオプションを設定します。</span><span class="sxs-lookup"><span data-stu-id="bf849-128">Click the **Advanced** page to set job step options, such as: what action to take if the job step succeeds or fails, how many times [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent should try to execute the job step, and the file or table where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent can write the job step output.</span></span> <span data-ttu-id="bf849-129">**sysadmin** 固定サーバー ロールのメンバーだけが、オペレーティング システム ファイルにジョブ ステップの出力を書き込むことができます。</span><span class="sxs-lookup"><span data-stu-id="bf849-129">Only members of the **sysadmin** fixed server role can write job step output to an operating system file.</span></span> <span data-ttu-id="bf849-130">SQL Server エージェントのすべてのユーザーがテーブルにログを書き込むことができます。</span><span class="sxs-lookup"><span data-stu-id="bf849-130">All SQL Server Agent users can log output to a table.</span></span>  
  
10. <span data-ttu-id="bf849-131">**sysadmin** 固定サーバー ロールのメンバーで、このジョブ ステップを別の SQL ログインで実行する場合は、 **[実行時のユーザー]** ボックスで SQL ログインを選択します。</span><span class="sxs-lookup"><span data-stu-id="bf849-131">If you are a member of the **sysadmin** fixed server role and you want to run this job step as a different SQL login, select the SQL login from the **Run as user** list.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="bf849-132">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="bf849-132">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-transact-sql-job-step"></a><span data-ttu-id="bf849-133">Transact-SQL ジョブ テップを作成するには</span><span class="sxs-lookup"><span data-stu-id="bf849-133">To create a Transact-SQL job step</span></span>  
  
1.  <span data-ttu-id="bf849-134">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="bf849-134">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="bf849-135">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bf849-135">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="bf849-136">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bf849-136">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```sql
    -- creates a job step that uses Transact-SQL  
    USE msdb;  
    GO  
    EXEC sp_add_jobstep  
        @job_name = N'Weekly Sales Data Backup',  
        @step_name = N'Set database to read only',  
        @subsystem = N'TSQL',  
        @command = N'ALTER DATABASE SALES SET READ_ONLY',   
        @retry_attempts = 5,  
        @retry_interval = 5 ;  
    GO  
    ```  
  
 <span data-ttu-id="bf849-137">詳細については、「 [sp_add_jobstep &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bf849-137">For more information, see [sp_add_jobstep &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql).</span></span>  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="bf849-138">SQL Server 管理オブジェクトの使用</span><span class="sxs-lookup"><span data-stu-id="bf849-138">Using SQL Server Management Objects</span></span>  
 <span data-ttu-id="bf849-139">**Transact-SQL ジョブ テップを作成するには**</span><span class="sxs-lookup"><span data-stu-id="bf849-139">**To create a Transact-SQL job step**</span></span>  
  
 <span data-ttu-id="bf849-140">`JobStep`Visual Basic、Visual C#、PowerShell など、選択したプログラミング言語でクラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="bf849-140">Use the `JobStep` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span>  
