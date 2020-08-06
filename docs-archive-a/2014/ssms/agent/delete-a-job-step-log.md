---
title: ジョブ ステップのログの削除 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- job steps [SQL Server Agent]
- deleting job step logs
- logs [SQL Server], jobs
- removing job step logs
ms.assetid: ee20c6cd-0258-4550-bdb0-71e86a0fb330
author: stevestein
ms.author: sstein
ms.openlocfilehash: de7c64c4d7cf461eef563ae6989e043d125c6f5b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641959"
---
# <a name="delete-a-job-step-log"></a><span data-ttu-id="d02e3-102">Delete a Job Step Log</span><span class="sxs-lookup"><span data-stu-id="d02e3-102">Delete a Job Step Log</span></span>
  <span data-ttu-id="d02e3-103">このトピックでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのジョブ ステップのログを削除する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d02e3-103">This topic describes how to delete a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job step log.</span></span>  
  
-   <span data-ttu-id="d02e3-104">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="d02e3-104">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="d02e3-105">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="d02e3-105">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="d02e3-106">Security</span><span class="sxs-lookup"><span data-stu-id="d02e3-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="d02e3-107">**SQL Server エージェントのジョブ ステップのログを削除する方法:**</span><span class="sxs-lookup"><span data-stu-id="d02e3-107">**To delete a SQL Server Agent job step log, using:**</span></span>  
  
     [<span data-ttu-id="d02e3-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="d02e3-108">SQL Server Management Studio</span></span>](#SSMS)  
  
     [<span data-ttu-id="d02e3-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="d02e3-109">Transact-SQL</span></span>](#TSQL)  
  
     [<span data-ttu-id="d02e3-110">SQL Server 管理オブジェクト</span><span class="sxs-lookup"><span data-stu-id="d02e3-110">SQL Server Management Objects</span></span>](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="d02e3-111">はじめに</span><span class="sxs-lookup"><span data-stu-id="d02e3-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="d02e3-112">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="d02e3-112">Limitations and Restrictions</span></span>  
 <span data-ttu-id="d02e3-113">ジョブ ステップが削除されるときに、そのジョブ ステップの出力ログは自動的に削除されます。</span><span class="sxs-lookup"><span data-stu-id="d02e3-113">When job steps are deleted their output log is automatically deleted.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="d02e3-114">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="d02e3-114">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="d02e3-115">Permissions</span><span class="sxs-lookup"><span data-stu-id="d02e3-115">Permissions</span></span>  
 <span data-ttu-id="d02e3-116">**sysadmin** 固定サーバー ロールのメンバー以外は、所有しているジョブしか変更できません。</span><span class="sxs-lookup"><span data-stu-id="d02e3-116">Unless you are a member of the **sysadmin** fixed server role, you can only modify jobs that you own.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="d02e3-117">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="d02e3-117">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-delete-a-sql-server-agent-job-step-log"></a><span data-ttu-id="d02e3-118">SQL Server エージェントのジョブ ステップのログを削除するには</span><span class="sxs-lookup"><span data-stu-id="d02e3-118">To delete a SQL Server Agent job step log</span></span>  
  
1.  <span data-ttu-id="d02e3-119">**オブジェクトエクスプローラー**で、のインスタンスに接続し、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] そのインスタンスを展開します。</span><span class="sxs-lookup"><span data-stu-id="d02e3-119">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="d02e3-120">**[SQL Server エージェント]**、 **[ジョブ]** の順に展開し、変更するジョブを右クリックします。次に、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d02e3-120">Expand **SQL Server Agent**, expand **Jobs**, right-click the job you want to modify, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="d02e3-121">**[ジョブのプロパティ]** ダイアログ ボックスで、選択したジョブ ステップを削除します。</span><span class="sxs-lookup"><span data-stu-id="d02e3-121">In the **Job Properties** dialog box, delete the selected job step.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="d02e3-122">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="d02e3-122">Using Transact-SQL</span></span>  
  
#### <a name="to-delete-a-sql-server-agent-job-step-log"></a><span data-ttu-id="d02e3-123">SQL Server エージェントのジョブ ステップのログを削除するには</span><span class="sxs-lookup"><span data-stu-id="d02e3-123">To delete a SQL Server Agent job step log</span></span>  
  
1.  <span data-ttu-id="d02e3-124">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="d02e3-124">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="d02e3-125">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d02e3-125">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="d02e3-126">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d02e3-126">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```sql
    -- removes the job step log for step 2 in the job Weekly Sales Data Backup  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_delete_jobsteplog  
        @job_name = N'Weekly Sales Data Backup',  
        @step_id = 2;  
    GO  
    ```  
  
 <span data-ttu-id="d02e3-127">詳細については、「 [sp_delete_jobsteplog &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-jobsteplog-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d02e3-127">For more information, see [sp_delete_jobsteplog &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-jobsteplog-transact-sql).</span></span>  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="d02e3-128">SQL Server 管理オブジェクトの使用</span><span class="sxs-lookup"><span data-stu-id="d02e3-128">Using SQL Server Management Objects</span></span>  
 <span data-ttu-id="d02e3-129">Visual Basic、Visual C#、PowerShell などのプログラミング言語で `DeleteJobStepLogs` クラスの `Job` メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="d02e3-129">Use the `DeleteJobStepLogs` methods of the `Job` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span> <span data-ttu-id="d02e3-130">詳細については、「[SQL Server 管理オブジェクト (SMO) プログラミング ガイド](https://msdn.microsoft.com/library/ms162169.aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d02e3-130">For more information, see[SQL Server Management Objects (SMO)](https://msdn.microsoft.com/library/ms162169.aspx).</span></span>  
  
```powershell
# Delete all job step log files that have ID values larger than 5.  
$srv = New-Object Microsoft.SqlServer.Management.Smo.Server("(local)")  
$jb = $srv.JobServer.Jobs["Test Job"]  
$jb.DeleteJobStepLogs(5)  
```
