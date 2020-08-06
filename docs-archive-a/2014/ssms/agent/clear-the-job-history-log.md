---
title: ジョブ履歴ログのクリア | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], history
- clearing job history log
- logs [SQL Server], jobs
- SQL Server Agent jobs, history
- historical information [SQL Server], jobs
ms.assetid: 34b9398a-c409-4040-8ea1-0deceb18f961
author: stevestein
ms.author: sstein
ms.openlocfilehash: 813c2c7c86a769eea09a093f2de999460d78ef54
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645343"
---
# <a name="clear-the-job-history-log"></a><span data-ttu-id="3382e-102">Clear the Job History Log</span><span class="sxs-lookup"><span data-stu-id="3382e-102">Clear the Job History Log</span></span>
  <span data-ttu-id="3382e-103">このトピック [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 、、、または SQL Server 管理オブジェクトを使用して、でエージェントのジョブ履歴ログの内容を削除する方法について説明し [!INCLUDE[tsql](../../includes/tsql-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="3382e-103">This topic describes how to delete the contents of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job history log in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or SQL Server Management Objects.</span></span>  
  
 <span data-ttu-id="3382e-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="3382e-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="3382e-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="3382e-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="3382e-106">Security</span><span class="sxs-lookup"><span data-stu-id="3382e-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="3382e-107">**ジョブ履歴ログを消去する方法:**</span><span class="sxs-lookup"><span data-stu-id="3382e-107">**To clear the job history log, using:**</span></span>  
  
     [<span data-ttu-id="3382e-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="3382e-108">SQL Server Management Studio</span></span>](#SSMS)  
  
     [<span data-ttu-id="3382e-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="3382e-109">Transact-SQL</span></span>](#TSQL)  
  
     [<span data-ttu-id="3382e-110">SQL Server 管理オブジェクト</span><span class="sxs-lookup"><span data-stu-id="3382e-110">SQL Server Management Objects</span></span>](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="3382e-111">はじめに</span><span class="sxs-lookup"><span data-stu-id="3382e-111">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="3382e-112">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="3382e-112">Security</span></span>  
 <span data-ttu-id="3382e-113">詳細については、「 [SQL Server エージェントのセキュリティの実装](implement-sql-server-agent-security.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="3382e-113">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="3382e-114">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="3382e-114">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-clear-the-job-history-log"></a><span data-ttu-id="3382e-115">ジョブ履歴ログを消去するには</span><span class="sxs-lookup"><span data-stu-id="3382e-115">To clear the job history log</span></span>  
  
1.  <span data-ttu-id="3382e-116">**オブジェクトエクスプローラー**で、のインスタンスに接続し、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] そのインスタンスを展開します。</span><span class="sxs-lookup"><span data-stu-id="3382e-116">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="3382e-117">**[SQL Server エージェント]** を展開し、 **[ジョブ]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="3382e-117">Expand **SQL Server Agent**, and then expand **Jobs**.</span></span>  
  
3.  <span data-ttu-id="3382e-118">ジョブを右クリックし、 **[履歴の表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3382e-118">Right-click a job and click **View history**.</span></span>  
  
4.  <span data-ttu-id="3382e-119">**[ログ ファイルの表示]** ダイアログ ボックスで、履歴を消去するジョブを選択し、次のいずれかの手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="3382e-119">In the **Log File Viewer**, select the job for which you want to clear history, and then do one of the following:</span></span>  
  
    -   <span data-ttu-id="3382e-120">**[削除]** をクリックし、 **[履歴の削除]** ダイアログ ボックスの **[すべての履歴を削除する]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3382e-120">Click **Delete**, and then click **Delete all history** in the **Delete History** dialog.</span></span> <span data-ttu-id="3382e-121">すべてのジョブ履歴を削除することも、指定日よりも古い履歴のみを削除することもできます。</span><span class="sxs-lookup"><span data-stu-id="3382e-121">You can delete all job history or only history that is older than a specified date.</span></span> <span data-ttu-id="3382e-122">すべてのジョブ履歴を削除するには、 **[すべての履歴を削除する]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3382e-122">If you want to remove all job history, click **Delete all history**.</span></span> <span data-ttu-id="3382e-123">指定日よりも古いジョブ履歴ログを削除するには、 **[次の日付以前の履歴を削除する]** をクリックしてから日付を指定します。</span><span class="sxs-lookup"><span data-stu-id="3382e-123">If you only want to remove older job history logs, click **Delete history before**, and then specify a date.</span></span>  
  
    -   <span data-ttu-id="3382e-124">マルチサーバー ジョブの履歴ログを消去するには、 **[ジョブ ステータス]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3382e-124">Click **Job status** if you want to clear the history log of a multiserver job.</span></span> <span data-ttu-id="3382e-125">**[ジョブ]** をクリックしてからジョブ名をクリックし、 **[ジョブ履歴の表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3382e-125">Click **Job**, click a job name, and then click **View Remote Job History**.</span></span>  
  
5.  <span data-ttu-id="3382e-126">**[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3382e-126">Click **Delete**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="3382e-127">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="3382e-127">Using Transact-SQL</span></span>  
  
#### <a name="to-clear-the-job-history-log"></a><span data-ttu-id="3382e-128">ジョブ履歴ログを消去するには</span><span class="sxs-lookup"><span data-stu-id="3382e-128">To clear the job history log</span></span>  
  
1.  <span data-ttu-id="3382e-129">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="3382e-129">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="3382e-130">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3382e-130">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="3382e-131">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3382e-131">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```sql
    -- example removes the history for a job named NightlyBackups.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_purge_jobhistory  
        @job_name = N'NightlyBackups' ;  
    GO  
    ```  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="3382e-132">SQL Server 管理オブジェクトの使用</span><span class="sxs-lookup"><span data-stu-id="3382e-132">Using SQL Server Management Objects</span></span>  
 <span data-ttu-id="3382e-133">**ジョブ履歴ログを消去するには**</span><span class="sxs-lookup"><span data-stu-id="3382e-133">**To clear the job history log**</span></span>  
  
 <span data-ttu-id="3382e-134">`PurgeJobHistory` `JobServer` Visual Basic、Visual C#、PowerShell など、選択したプログラミング言語を使用して、クラスのメソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="3382e-134">Use the `PurgeJobHistory` method of the `JobServer` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span> <span data-ttu-id="3382e-135">詳細については、「 [SQL Server 管理オブジェクト (SMO) プログラミング ガイド](https://msdn.microsoft.com/library/ms162169.aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3382e-135">For more information, see [SQL Server Management Objects (SMO)](https://msdn.microsoft.com/library/ms162169.aspx).</span></span>  
  
  
