---
title: ジョブの停止 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], stopping
- SQL Server Agent jobs, stopping
- stopping jobs
ms.assetid: 4249328a-24d8-4284-9d1d-7d04ed90e3d7
author: stevestein
ms.author: sstein
ms.openlocfilehash: 78986e85dd8ee808f5fb621182d903a94bbc5eb7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711566"
---
# <a name="stop-a-job"></a><span data-ttu-id="5a7b0-102">Stop a Job</span><span class="sxs-lookup"><span data-stu-id="5a7b0-102">Stop a Job</span></span>
  <span data-ttu-id="5a7b0-103">このトピックでは、エージェントジョブを停止する方法について説明し [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="5a7b0-103">This topic describes how to stop a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job.</span></span> <span data-ttu-id="5a7b0-104">ジョブとは、SQL Server エージェントで実行される特定の一連の処理のことです。</span><span class="sxs-lookup"><span data-stu-id="5a7b0-104">A job is a specified series of actions that SQL Server Agent performs.</span></span>  
  
-   <span data-ttu-id="5a7b0-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="5a7b0-105">**Before you begin:**  ,</span></span>  
  
     [<span data-ttu-id="5a7b0-106">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="5a7b0-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="5a7b0-107">Security</span><span class="sxs-lookup"><span data-stu-id="5a7b0-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="5a7b0-108">**ジョブを停止する方法:**</span><span class="sxs-lookup"><span data-stu-id="5a7b0-108">**To stop a job, using:**</span></span>  
  
     [<span data-ttu-id="5a7b0-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="5a7b0-109">SQL Server Management Studio</span></span>](#SSMS)  
  
     [<span data-ttu-id="5a7b0-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="5a7b0-110">Transact-SQL</span></span>](#TSQL)  
  
     [<span data-ttu-id="5a7b0-111">SQL Server 管理オブジェクト</span><span class="sxs-lookup"><span data-stu-id="5a7b0-111">SQL Server Management Objects</span></span>](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="5a7b0-112">はじめに</span><span class="sxs-lookup"><span data-stu-id="5a7b0-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="5a7b0-113">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="5a7b0-113">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="5a7b0-114">ジョブで **CmdExec** または **PowerShell**型のステップが現在実行されている場合、実行中のプロセス (MyProgram.exe など) は途中で強制終了されます。</span><span class="sxs-lookup"><span data-stu-id="5a7b0-114">If a job is currently executing a step of type **CmdExec** or **PowerShell**, the process that is being run (for example, MyProgram.exe) is forced to end prematurely.</span></span> <span data-ttu-id="5a7b0-115">途中で強制終了した場合、そのプロセスによって使用されていたファイルが開いたままになるなど、予期しない結果が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="5a7b0-115">This can cause unpredictable behavior, such as files that are being used by the process being held open.</span></span>  
  
-   <span data-ttu-id="5a7b0-116">マルチサーバー ジョブの場合、STOP 命令はそのジョブのすべてのターゲット サーバーに通知されます。</span><span class="sxs-lookup"><span data-stu-id="5a7b0-116">For a multiserver job, a STOP instruction for the job is posted to all target servers of the job.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="5a7b0-117">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="5a7b0-117">Security</span></span>  
 <span data-ttu-id="5a7b0-118">詳細については、「 [SQL Server エージェントのセキュリティの実装](implement-sql-server-agent-security.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="5a7b0-118">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="5a7b0-119">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="5a7b0-119">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-stop-a-job"></a><span data-ttu-id="5a7b0-120">ジョブを停止するには</span><span class="sxs-lookup"><span data-stu-id="5a7b0-120">To stop a job</span></span>  
  
1.  <span data-ttu-id="5a7b0-121">**オブジェクトエクスプローラー**で、のインスタンスに接続し、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] そのインスタンスを展開します。</span><span class="sxs-lookup"><span data-stu-id="5a7b0-121">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="5a7b0-122">**[SQL Server エージェント]**、 **[ジョブ]** の順に展開し、停止するジョブを右クリックして、 **[ジョブの停止]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5a7b0-122">Expand **SQL Server Agent**, expand **Jobs**, right-click the job you want to stop, and then click **Stop Job**.</span></span>  
  
3.  <span data-ttu-id="5a7b0-123">複数のジョブを停止するには、 **[ジョブの利用状況モニター]** を右クリックし、 **[ジョブの利用状況の表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5a7b0-123">If you want to stop multiple jobs, right-click **Job Activity Monitor**, and then click **View Job Activity**.</span></span> <span data-ttu-id="5a7b0-124">[ジョブの利用状況モニター] で、停止する複数のジョブを選択してから右クリックし、 **[ジョブの停止]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5a7b0-124">In the Job Activity Monitor, select the jobs you want to stop, right-click your selection, and then click **Stop Jobs**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="5a7b0-125">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="5a7b0-125">Using Transact-SQL</span></span>  
  
### <a name="to-stop-a-job"></a><span data-ttu-id="5a7b0-126">ジョブを停止するには</span><span class="sxs-lookup"><span data-stu-id="5a7b0-126">To stop a job</span></span>  
  
1.  <span data-ttu-id="5a7b0-127">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="5a7b0-127">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="5a7b0-128">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5a7b0-128">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="5a7b0-129">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5a7b0-129">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```sql
    -- stops a job named Weekly Sales Data Backup  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_stop_job  
        N'Weekly Sales Data Backup' ;  
    GO  
    ```  
  
 <span data-ttu-id="5a7b0-130">詳細については、「 [sp_stop_job &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-stop-job-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5a7b0-130">For more information, see [sp_stop_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-stop-job-transact-sql).</span></span>  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="5a7b0-131">SQL Server 管理オブジェクトの使用</span><span class="sxs-lookup"><span data-stu-id="5a7b0-131">Using SQL Server Management Objects</span></span>  

### <a name="to-stop-a-job"></a><span data-ttu-id="5a7b0-132">ジョブを停止するには</span><span class="sxs-lookup"><span data-stu-id="5a7b0-132">To stop a job</span></span>
  
 <span data-ttu-id="5a7b0-133">Visual Basic、Visual C#、PowerShell などのプログラミング言語で `Stop` クラスの `Job` メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="5a7b0-133">Call the `Stop` method of the `Job` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span> <span data-ttu-id="5a7b0-134">詳細については、「 [SQL Server 管理オブジェクト (SMO) プログラミング ガイド](https://msdn.microsoft.com/library/ms162169.aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5a7b0-134">For more information, see [SQL Server Management Objects (SMO)](https://msdn.microsoft.com/library/ms162169.aspx).</span></span>  
