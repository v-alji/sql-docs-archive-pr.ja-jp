---
title: ジョブ履歴の表示 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], history
- viewing job history
- SQL Server Agent jobs, history
- historical information [SQL Server], jobs
- displaying job history
ms.assetid: 3bbd1556-abdb-48a3-b249-546eace76343
author: stevestein
ms.author: sstein
ms.openlocfilehash: e84fafdaeddb5748a8129cd5d71d667db7e5fa37
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719376"
---
# <a name="view-the-job-history"></a><span data-ttu-id="ed51b-102">View the Job History</span><span class="sxs-lookup"><span data-stu-id="ed51b-102">View the Job History</span></span>
  <span data-ttu-id="ed51b-103">このトピック [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 、、、または SQL Server 管理オブジェクトを使用して、でエージェントのジョブ履歴ログを表示する方法について説明し [!INCLUDE[tsql](../../includes/tsql-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="ed51b-103">This topic describes how to view the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job history log in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or SQL Server Management Objects.</span></span>  
  
-   <span data-ttu-id="ed51b-104">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="ed51b-104">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="ed51b-105">Security</span><span class="sxs-lookup"><span data-stu-id="ed51b-105">Security</span></span>](#Security)  
  
-   <span data-ttu-id="ed51b-106">**ジョブ履歴ログを表示する方法:**</span><span class="sxs-lookup"><span data-stu-id="ed51b-106">**To view the job history log, using:**</span></span>  
  
     [<span data-ttu-id="ed51b-107">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ed51b-107">SQL Server Management Studio</span></span>](#SSMS)  
  
     [<span data-ttu-id="ed51b-108">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ed51b-108">Transact-SQL</span></span>](#TSQL)  
  
     [<span data-ttu-id="ed51b-109">SQL Server 管理オブジェクト</span><span class="sxs-lookup"><span data-stu-id="ed51b-109">SQL Server Management Objects</span></span>](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="ed51b-110">はじめに</span><span class="sxs-lookup"><span data-stu-id="ed51b-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="ed51b-111">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="ed51b-111">Security</span></span>  
 <span data-ttu-id="ed51b-112">詳細については、「 [SQL Server エージェントのセキュリティの実装](implement-sql-server-agent-security.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="ed51b-112">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="ed51b-113">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="ed51b-113">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-the-job-history-log"></a><span data-ttu-id="ed51b-114">ジョブ履歴ログを表示するには</span><span class="sxs-lookup"><span data-stu-id="ed51b-114">To view the job history log</span></span>  
  
1.  <span data-ttu-id="ed51b-115">**オブジェクトエクスプローラー**で、のインスタンスに接続し、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] そのインスタンスを展開します。</span><span class="sxs-lookup"><span data-stu-id="ed51b-115">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="ed51b-116">**[SQL Server エージェント]** を展開し、 **[ジョブ]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="ed51b-116">Expand **SQL Server Agent**, and then expand **Jobs**.</span></span>  
  
3.  <span data-ttu-id="ed51b-117">ジョブを右クリックし、 **[履歴の表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ed51b-117">Right-click a job, and then click **View History**.</span></span>  
  
4.  <span data-ttu-id="ed51b-118">ログ ファイル ビューアーにジョブ履歴が表示されます。</span><span class="sxs-lookup"><span data-stu-id="ed51b-118">In the Log File Viewer, view the job history.</span></span>  
  
5.  <span data-ttu-id="ed51b-119">ジョブ履歴を更新するには、 **[最新の情報に更新]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ed51b-119">To update the job history, click **Refresh**.</span></span> <span data-ttu-id="ed51b-120">表示する列を少なくするには、 **[フィルター]** ボタンをクリックし、フィルターのパラメーターを入力します。</span><span class="sxs-lookup"><span data-stu-id="ed51b-120">To view fewer rows, click the **Filter** button and enter filter parameters.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="ed51b-121">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="ed51b-121">Using Transact-SQL</span></span>  
  
#### <a name="to-view-the-job-history-log"></a><span data-ttu-id="ed51b-122">ジョブ履歴ログを表示するには</span><span class="sxs-lookup"><span data-stu-id="ed51b-122">To view the job history log</span></span>  
  
1.  <span data-ttu-id="ed51b-123">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="ed51b-123">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="ed51b-124">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ed51b-124">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="ed51b-125">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ed51b-125">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```sql
    -- lists all job information for the NightlyBackups job.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_help_jobhistory   
        @job_name = N'NightlyBackups' ;  
    GO  
    ```  
  
 <span data-ttu-id="ed51b-126">詳細については、「 [sp_help_jobhistory &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-help-jobhistory-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ed51b-126">For more information, see [sp_help_jobhistory &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-jobhistory-transact-sql).</span></span>  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="ed51b-127">SQL Server 管理オブジェクトの使用</span><span class="sxs-lookup"><span data-stu-id="ed51b-127">Using SQL Server Management Objects</span></span>  
 <span data-ttu-id="ed51b-128">**ジョブ履歴ログを表示するには**</span><span class="sxs-lookup"><span data-stu-id="ed51b-128">**To view the job history log**</span></span>  
  
 <span data-ttu-id="ed51b-129">Visual Basic、Visual C#、PowerShell などのプログラミング言語で `EnumHistory` クラスの `Job` メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="ed51b-129">Call the `EnumHistory` method of the `Job` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span> <span data-ttu-id="ed51b-130">詳細については、「 [SQL Server 管理オブジェクト (SMO) プログラミング ガイド](https://msdn.microsoft.com/library/ms162169.aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ed51b-130">For more information, see [SQL Server Management Objects (SMO)](https://msdn.microsoft.com/library/ms162169.aspx).</span></span>  
