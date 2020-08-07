---
title: Windows アプリケーション ログへのジョブ状態の書き込み | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- status information [SQL Server], jobs
- SQL Server Agent jobs, status
- writing job status to log
- jobs [SQL Server Agent], status
- logs [SQL Server], jobs
ms.assetid: 3b813702-8f61-40ec-bf3b-ce9deb7e68be
author: stevestein
ms.author: sstein
ms.openlocfilehash: 67bdd7948d1722e49976d5e48b571c684431cd1c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719359"
---
# <a name="write-the-job-status-to-the-windows-application-log"></a><span data-ttu-id="a975d-102">Write the Job Status to the Windows Application Log</span><span class="sxs-lookup"><span data-stu-id="a975d-102">Write the Job Status to the Windows Application Log</span></span>
  <span data-ttu-id="a975d-103">このトピック [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 、、、または SQL Server 管理オブジェクトを使用して、でジョブの状態を Windows アプリケーションのイベントログに書き込むようにエージェントを構成する方法について説明し [!INCLUDE[tsql](../../includes/tsql-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="a975d-103">This topic describes how to configure [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] to write job status to the Windows application event log by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or SQL Server Management Objects.</span></span>  
  
 <span data-ttu-id="a975d-104">ジョブ応答により、データベース管理者はジョブの完了日時や実行頻度を確認できます。</span><span class="sxs-lookup"><span data-stu-id="a975d-104">Job responses ensure that database administrators know when jobs complete and how frequently they run.</span></span> <span data-ttu-id="a975d-105">以下に、一般的なジョブ応答を示します。</span><span class="sxs-lookup"><span data-stu-id="a975d-105">Typical job responses include:</span></span>  
  
-   <span data-ttu-id="a975d-106">電子メール、ポケットベル、または **net send** メッセージによってオペレーターに通知します。</span><span class="sxs-lookup"><span data-stu-id="a975d-106">Notifying the operator by using e-mail, electronic paging, or a **net send** message.</span></span> <span data-ttu-id="a975d-107">オペレーターが事後の作業を実行する必要がある場合に、これらのジョブ応答のいずれかを使用します。</span><span class="sxs-lookup"><span data-stu-id="a975d-107">Use one of these job responses if the operator must perform a follow-up action.</span></span> <span data-ttu-id="a975d-108">たとえば、バックアップ ジョブが正常に終了した場合、オペレーターは、バックアップ テープを取り出して、安全な場所に保管するように通知を受ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="a975d-108">For example, if a backup job completes successfully, the operator must be notified to remove the backup tape and store it in a safe location.</span></span>  
  
-   <span data-ttu-id="a975d-109">Windows アプリケーション ログにイベント メッセージを書き込みます。</span><span class="sxs-lookup"><span data-stu-id="a975d-109">Writing an event message to the Windows application log.</span></span> <span data-ttu-id="a975d-110">この応答は、失敗したジョブに対してのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="a975d-110">You can use this response only for failed jobs.</span></span>  
  
-   <span data-ttu-id="a975d-111">ジョブを自動的に削除します。</span><span class="sxs-lookup"><span data-stu-id="a975d-111">Automatically deleting the job.</span></span> <span data-ttu-id="a975d-112">このジョブを再実行する必要がないことが明らかな場合に、このジョブ応答を使用します。</span><span class="sxs-lookup"><span data-stu-id="a975d-112">Use this job response if you are certain that you do not need to rerun this job.</span></span>  
  
 <span data-ttu-id="a975d-113">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="a975d-113">**In This Topic**</span></span>  
  
-   <span data-ttu-id="a975d-114">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="a975d-114">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="a975d-115">Security</span><span class="sxs-lookup"><span data-stu-id="a975d-115">Security</span></span>](#Security)  
  
-   <span data-ttu-id="a975d-116">**ジョブの状態を Windows アプリケーション ログに書き込む方法:**</span><span class="sxs-lookup"><span data-stu-id="a975d-116">**To write the job status to the Windows application log, using:**</span></span>  
  
     [<span data-ttu-id="a975d-117">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="a975d-117">SQL Server Management Studio</span></span>](#SSMS)  
  
     [<span data-ttu-id="a975d-118">SQL Server 管理オブジェクト</span><span class="sxs-lookup"><span data-stu-id="a975d-118">SQL Server Management Objects</span></span>](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="a975d-119">はじめに</span><span class="sxs-lookup"><span data-stu-id="a975d-119">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="a975d-120">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="a975d-120">Security</span></span>  
 <span data-ttu-id="a975d-121">詳細については、「 [SQL Server エージェントのセキュリティの実装](implement-sql-server-agent-security.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a975d-121">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="a975d-122">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="a975d-122">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-write-job-status-to-the-windows-application-log"></a><span data-ttu-id="a975d-123">ジョブの状態を Windows アプリケーション ログに書き込むには</span><span class="sxs-lookup"><span data-stu-id="a975d-123">To write job status to the Windows application log</span></span>  
  
1.  <span data-ttu-id="a975d-124">**オブジェクトエクスプローラー**で、のインスタンスに接続し、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] そのインスタンスを展開します。</span><span class="sxs-lookup"><span data-stu-id="a975d-124">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="a975d-125">**[SQL Server エージェント]** を展開し、 **[ジョブ]** を展開します。次に、編集するジョブを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a975d-125">Expand **SQL Server Agent**, expand **Jobs**, right-click the job you want to edit, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="a975d-126">**[通知]** ページをクリックします。</span><span class="sxs-lookup"><span data-stu-id="a975d-126">Select the **Notifications** page.</span></span>  
  
4.  <span data-ttu-id="a975d-127">**[Windows アプリケーション イベント ログに書き込む]** チェック ボックスをオンにし、次のいずれかを選択します。</span><span class="sxs-lookup"><span data-stu-id="a975d-127">Check **Write to Windows application event log**, and choose one of the following:</span></span>  
  
    -   <span data-ttu-id="a975d-128">ジョブが正常終了したときにジョブの状態をログに記録する場合は、**[ジョブ成功時]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a975d-128">Click**When the job succeeds**to log the job status when the job completes successfully.</span></span>  
  
    -   <span data-ttu-id="a975d-129">ジョブが異常終了したときにジョブの状態をログに記録する場合は、**[ジョブ失敗時]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a975d-129">Click**When the job fails**to log the job status when the job completes unsuccessfully.</span></span>  
  
    -   <span data-ttu-id="a975d-130">終了の状態にかかわらずジョブの状態をログに記録する場合は、**[ジョブ完了時]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a975d-130">Click**When the job completes** to log the job status regardless of completion status.</span></span>  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="a975d-131">SQL Server 管理オブジェクトの使用</span><span class="sxs-lookup"><span data-stu-id="a975d-131">Using SQL Server Management Objects</span></span>  

### <a name="to-write-job-status-to-the-windows-application-log"></a><span data-ttu-id="a975d-132">ジョブの状態を Windows アプリケーション ログに書き込むには</span><span class="sxs-lookup"><span data-stu-id="a975d-132">To write job status to the Windows application log</span></span>
  
 <span data-ttu-id="a975d-133">Visual Basic、Visual C#、PowerShell などのプログラミング言語で `EventLogLevel` クラスの `Job` プロパティを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="a975d-133">Call the `EventLogLevel` property of the `Job` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span>  
  
 <span data-ttu-id="a975d-134">次のコード例では、ジョブの実行の終了時に、オペレーティング システムのイベント ログ エントリを生成するようにジョブを設定します。</span><span class="sxs-lookup"><span data-stu-id="a975d-134">The following code example sets the job to generate an operating system event log entry when the job execution finishes.</span></span>  
  
```powershell
$srv = new-object Microsoft.SqlServer.Management.Smo.Server("(local)")  
$jb = new-object Microsoft.SqlServer.Management.Smo.Agent.Job($srv.JobServer, "Test Job")  
$jb.EventLogLevel = [Microsoft.SqlServer.Management.Smo.Agent.CompletionAction]::Always  
```  
