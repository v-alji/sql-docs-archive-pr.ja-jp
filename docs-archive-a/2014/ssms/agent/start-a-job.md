---
title: ジョブの開始 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], starting
- SQL Server Agent jobs, starting
- starting jobs
ms.assetid: cec9f7f7-d0a7-4239-9dc5-a69c011ebaa0
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4d5af895df518a915dacd953331b9139471933aa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737416"
---
# <a name="start-a-job"></a><span data-ttu-id="bd5ea-102">Start a Job</span><span class="sxs-lookup"><span data-stu-id="bd5ea-102">Start a Job</span></span>
  <span data-ttu-id="bd5ea-103">このトピック [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] は、または SQL Server 管理オブジェクトを使用して、でエージェントジョブの実行を開始する方法について説明し [!INCLUDE[tsql](../../includes/tsql-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="bd5ea-103">This topic describes how to start running a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)] or SQL Server Management Objects.</span></span>  
  
 <span data-ttu-id="bd5ea-104">ジョブとは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントで実行される特定の一連の処理のことです。</span><span class="sxs-lookup"><span data-stu-id="bd5ea-104">A job is a specified series of actions that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent performs.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="bd5ea-105">エージェント ジョブは、1 つのローカル サーバーで実行することも、複数のリモート サーバーで実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="bd5ea-105">Agent jobs can run on one local server or on multiple remote servers.</span></span>  
  
-   <span data-ttu-id="bd5ea-106">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="bd5ea-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="bd5ea-107">Security</span><span class="sxs-lookup"><span data-stu-id="bd5ea-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="bd5ea-108">**ジョブを開始する方法:**</span><span class="sxs-lookup"><span data-stu-id="bd5ea-108">**To start a job, using:**</span></span>  
  
     [<span data-ttu-id="bd5ea-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="bd5ea-109">SQL Server Management Studio</span></span>](#SSMS)  
  
     [<span data-ttu-id="bd5ea-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="bd5ea-110">Transact-SQL</span></span>](#TSQL)  
  
     [<span data-ttu-id="bd5ea-111">SQL Server 管理オブジェクト</span><span class="sxs-lookup"><span data-stu-id="bd5ea-111">SQL Server Management Objects</span></span>](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="bd5ea-112">はじめに</span><span class="sxs-lookup"><span data-stu-id="bd5ea-112">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="bd5ea-113">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="bd5ea-113">Security</span></span>  
 <span data-ttu-id="bd5ea-114">詳細については、「 [SQL Server エージェントのセキュリティの実装](implement-sql-server-agent-security.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="bd5ea-114">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="bd5ea-115">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="bd5ea-115">Using SQL Server Management Studio</span></span>  
  
### <a name="to-start-a-job"></a><span data-ttu-id="bd5ea-116">ジョブを開始するには</span><span class="sxs-lookup"><span data-stu-id="bd5ea-116">To start a job</span></span>  
  
1.  <span data-ttu-id="bd5ea-117">**オブジェクトエクスプローラー**で、のインスタンスに接続し、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] そのインスタンスを展開します。</span><span class="sxs-lookup"><span data-stu-id="bd5ea-117">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="bd5ea-118">**[SQL Server エージェント]** を展開し、 **[ジョブ]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="bd5ea-118">Expand **SQL Server Agent,** and expand **Jobs**.</span></span> <span data-ttu-id="bd5ea-119">ジョブの開始方法に応じて、次のいずれかを行います。</span><span class="sxs-lookup"><span data-stu-id="bd5ea-119">Depending on how you want the job to start, do one of the following:</span></span>  
  
    -   <span data-ttu-id="bd5ea-120">単一のサーバーまたはターゲット サーバー上で作業を行っている場合、またはマスター サーバー上でローカル サーバー ジョブを実行している場合、開始するジョブを右クリックして、**[ジョブの開始]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bd5ea-120">If you are working on a single server, or working on a target server, or running a local server job on a master server, right-click the job you want to start, and then click **Start Job**.</span></span>  
  
    -   <span data-ttu-id="bd5ea-121">複数のジョブを開始するには、 **[ジョブの利用状況モニター]** を右クリックし、 **[ジョブの利用状況の表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bd5ea-121">If you want to start multiple jobs, right-click **Job Activity Monitor**, and then click **View Job Activity**.</span></span> <span data-ttu-id="bd5ea-122">ジョブの利用状況モニターでは、複数のジョブを選択し、選択内容を右クリックして、 **[ジョブの開始]** をクリックできます。</span><span class="sxs-lookup"><span data-stu-id="bd5ea-122">In the Job Activity Monitor you can select multiple jobs, right-click your selection, and click **Start Jobs**.</span></span>  
  
    -   <span data-ttu-id="bd5ea-123">マスター サーバー上で作業を行っていて、すべての対象サーバーで同時にジョブを実行する場合、開始するジョブを右クリックし、 **[ジョブの開始]** をクリックします。次に、 **[すべての対象サーバーで開始]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bd5ea-123">If you are working on a master server and want all targeted servers to run the job simultaneously, right-click the job you want to start, click **Start Job**, and then click **Start on all targeted servers**.</span></span>  
  
    -   <span data-ttu-id="bd5ea-124">マスター サーバー上で作業を行っていて、ジョブのターゲット サーバーを指定する場合、開始するジョブを右クリックし、**[ジョブの開始]** をクリックします。次に、**[特定のターゲット サーバーで開始]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bd5ea-124">If you are working on a master server and want to specify target servers for the job, right-click the job you want to start, click **Start Job**, and then click **Start on specific target servers**.</span></span> <span data-ttu-id="bd5ea-125">**[ダウンロード命令の通知]** ダイアログ ボックスの **[特定のターゲット サーバー]** チェック ボックスをオンにし、このジョブが実行される各ターゲット サーバーを選択します。</span><span class="sxs-lookup"><span data-stu-id="bd5ea-125">In the **Post Download Instructions** dialog box, select the **These target servers** check box, and then select each target server on which this job should run.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="bd5ea-126">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="bd5ea-126">Using Transact-SQL</span></span>  
  
### <a name="to-start-a-job"></a><span data-ttu-id="bd5ea-127">ジョブを開始するには</span><span class="sxs-lookup"><span data-stu-id="bd5ea-127">To start a job</span></span>  
  
1.  <span data-ttu-id="bd5ea-128">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="bd5ea-128">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="bd5ea-129">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bd5ea-129">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="bd5ea-130">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bd5ea-130">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```sql
    -- starts a job named Weekly Sales Data Backup.    
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_start_job N'Weekly Sales Data Backup' ;  
    GO  
    ```  
  
 <span data-ttu-id="bd5ea-131">詳細については、「[sp_start_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-start-job-transact-sql)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="bd5ea-131">For more information, see [sp_start_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-start-job-transact-sql).</span></span>  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="bd5ea-132">SQL Server 管理オブジェクトの使用</span><span class="sxs-lookup"><span data-stu-id="bd5ea-132">Using SQL Server Management Objects</span></span>  

### <a name="to-start-a-job"></a><span data-ttu-id="bd5ea-133">ジョブを開始するには</span><span class="sxs-lookup"><span data-stu-id="bd5ea-133">To start a job</span></span>
  
 <span data-ttu-id="bd5ea-134">Visual Basic、Visual C#、PowerShell などのプログラミング言語で `Start` クラスの `Job` メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="bd5ea-134">Call the `Start` method of the `Job` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span> <span data-ttu-id="bd5ea-135">詳細については、「 [SQL Server 管理オブジェクト (SMO) プログラミング ガイド](https://msdn.microsoft.com/library/ms162169.aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bd5ea-135">For more information, see [SQL Server Management Objects (SMO)](https://msdn.microsoft.com/library/ms162169.aspx).</span></span>  
