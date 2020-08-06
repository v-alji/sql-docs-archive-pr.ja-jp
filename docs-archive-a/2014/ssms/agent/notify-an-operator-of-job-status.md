---
title: オペレーターにジョブの状態を通知する方法 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- status information [SQL Server], jobs
- jobs [SQL Server Agent], notification options
- SQL Server Agent jobs, status
- jobs [SQL Server Agent], status
- SQL Server Agent jobs, notification options
- notifications [SQL Server], job status
ms.assetid: e7399505-27ac-48d9-a637-73bf92b9df49
author: stevestein
ms.author: sstein
ms.openlocfilehash: a202327ad63cf7ef8f51d3572b257816ee6d9419
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634789"
---
# <a name="notify-an-operator-of-job-status"></a><span data-ttu-id="bce69-102">Notify an Operator of Job Status</span><span class="sxs-lookup"><span data-stu-id="bce69-102">Notify an Operator of Job Status</span></span>
  <span data-ttu-id="bce69-103">このトピックでは [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 、、、または SQL Server 管理オブジェクトを使用して、 [!INCLUDE[tsql](../../includes/tsql-md.md)] [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントがジョブに関する通知をオペレーターに送信できるように、で通知オプションを設定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="bce69-103">This topic describes how to set notification options in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or SQL Server Management Objects, so [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent can send notifications to operators about jobs.</span></span>  
  
 <span data-ttu-id="bce69-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="bce69-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="bce69-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="bce69-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="bce69-106">Security</span><span class="sxs-lookup"><span data-stu-id="bce69-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="bce69-107">**オペレーターにジョブの状態を通知する方法:**</span><span class="sxs-lookup"><span data-stu-id="bce69-107">**To notify an operator of job status, using:**</span></span>  
  
     [<span data-ttu-id="bce69-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="bce69-108">SQL Server Management Studio</span></span>](#SSMS)  
  
     [<span data-ttu-id="bce69-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="bce69-109">Transact-SQL</span></span>](#TSQL)  
  
     [<span data-ttu-id="bce69-110">SQL Server 管理オブジェクト</span><span class="sxs-lookup"><span data-stu-id="bce69-110">SQL Server Management Objects</span></span>](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="bce69-111">はじめに</span><span class="sxs-lookup"><span data-stu-id="bce69-111">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="bce69-112">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="bce69-112">Security</span></span>  
 <span data-ttu-id="bce69-113">詳細については、「 [SQL Server エージェントのセキュリティの実装](implement-sql-server-agent-security.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="bce69-113">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="bce69-114">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="bce69-114">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-notify-an-operator-of-job-status"></a><span data-ttu-id="bce69-115">オペレーターにジョブの状態を通知するには</span><span class="sxs-lookup"><span data-stu-id="bce69-115">To notify an operator of job status</span></span>  
  
1.  <span data-ttu-id="bce69-116">**オブジェクトエクスプローラー**で、のインスタンスに接続し、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] そのインスタンスを展開します。</span><span class="sxs-lookup"><span data-stu-id="bce69-116">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="bce69-117">**[SQL Server エージェント]**、 **[ジョブ]** の順に展開し、編集するジョブを右クリックして、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bce69-117">Expand **SQL Server Agent**, expand **Jobs**, right-click the job you want to edit, and select **Properties**.</span></span>  
  
3.  <span data-ttu-id="bce69-118">**[ジョブのプロパティ]** ダイアログ ボックスで、 **[通知]** ページをクリックします。</span><span class="sxs-lookup"><span data-stu-id="bce69-118">In the **Job Properties** dialog box, select the **Notifications** page.</span></span>  
  
4.  <span data-ttu-id="bce69-119">オペレーターに電子メールで通知する場合、 **[電子メール]** チェック ボックスをオンにして一覧からオペレーターを選択し、次のいずれかをクリックします。</span><span class="sxs-lookup"><span data-stu-id="bce69-119">If you want to notify an operator by e-mail, check **E-mail**, select an operator from the list, and then select one of the following:</span></span>  
  
    -   <span data-ttu-id="bce69-120">**[ジョブ成功時]** : ジョブが正常に完了した場合にオペレーターに通知します。</span><span class="sxs-lookup"><span data-stu-id="bce69-120">**When the job succeeds** to notify the operator when the job completes successfully.</span></span>  
  
    -   <span data-ttu-id="bce69-121">**[ジョブ失敗時]** : ジョブが正常に完了しなかった場合にオペレーターに通知します。</span><span class="sxs-lookup"><span data-stu-id="bce69-121">**When the job fails** to notify the operator when the job completes unsuccessfully.</span></span>  
  
    -   <span data-ttu-id="bce69-122">**[ジョブ完了時]** : 完了時の状態とは関係なくオペレーターに通知します。</span><span class="sxs-lookup"><span data-stu-id="bce69-122">**When the job completes** to notify the operator regardless of completion status.</span></span>  
  
5.  <span data-ttu-id="bce69-123">オペレーターにポケットベルで通知する場合、 **[ポケットベル]** チェック ボックスをオンにして一覧からオペレーターを選択し、次のいずれかをクリックします。</span><span class="sxs-lookup"><span data-stu-id="bce69-123">If you want to notify an operator by pager, check **Page**, select an operator from the list, and then select one of the following:</span></span>  
  
    -   <span data-ttu-id="bce69-124">**[ジョブ成功時]** : ジョブが正常に完了した場合にオペレーターに通知します。</span><span class="sxs-lookup"><span data-stu-id="bce69-124">**When the job succeeds** to notify the operator when the job completes successfully.</span></span>  
  
    -   <span data-ttu-id="bce69-125">**[ジョブ失敗時]** : ジョブが正常に完了しなかった場合にオペレーターに通知します。</span><span class="sxs-lookup"><span data-stu-id="bce69-125">**When the job fails** to notify the operator when the job completes unsuccessfully.</span></span>  
  
    -   <span data-ttu-id="bce69-126">**[ジョブ完了時]** : 完了時の状態とは関係なくオペレーターに通知します。</span><span class="sxs-lookup"><span data-stu-id="bce69-126">**When the job completes** to notify the operator regardless of completion status.</span></span>  
  
6.  <span data-ttu-id="bce69-127">オペレーターに net send で通知する場合、 **[Net Send]** チェック ボックスをオンにして一覧からオペレーターを選択し、次のいずれかをクリックします。</span><span class="sxs-lookup"><span data-stu-id="bce69-127">If you want to notify an operator by net send, check **Net send**, select an operator from the list, and then select one of the following:</span></span>  
  
    -   <span data-ttu-id="bce69-128">**[ジョブ成功時]** : ジョブが正常に完了した場合にオペレーターに通知します。</span><span class="sxs-lookup"><span data-stu-id="bce69-128">**When the job succeeds** to notify the operator when the job completes successfully.</span></span>  
  
    -   <span data-ttu-id="bce69-129">**[ジョブ失敗時]** : ジョブが正常に完了しなかった場合にオペレーターに通知します。</span><span class="sxs-lookup"><span data-stu-id="bce69-129">**When the job fails** to notify the operator when the job completes unsuccessfully.</span></span>  
  
    -   <span data-ttu-id="bce69-130">**[ジョブ完了時]** : 完了時の状態とは関係なくオペレーターに通知します。</span><span class="sxs-lookup"><span data-stu-id="bce69-130">**When the job completes** to notify the operator regardless of completion status.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="bce69-131">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="bce69-131">Using Transact-SQL</span></span>  
  
#### <a name="to-notify-an-operator-of-job-status"></a><span data-ttu-id="bce69-132">オペレーターにジョブの状態を通知するには</span><span class="sxs-lookup"><span data-stu-id="bce69-132">To notify an operator of job status</span></span>  
  
1.  <span data-ttu-id="bce69-133">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="bce69-133">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="bce69-134">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bce69-134">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="bce69-135">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bce69-135">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```sql
    -- adds an e-mail notification for the specified alert (Test Alert).  
    -- This example assumes that Test Alert already exists and that Fran??ois Ajenstat is a valid operator name.  
    USE msdb ;  
    GO  
    EXEC dbo.sp_add_notification   
    @alert_name = N'Test Alert',   
    @operator_name = N'Fran??ois Ajenstat',   
    @notification_method = 1 ;  
    GO  
    ```  
  
 <span data-ttu-id="bce69-136">詳細については、「 [sp_add_notification &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-add-notification-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bce69-136">For more information, see [sp_add_notification &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-notification-transact-sql).</span></span>  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="bce69-137">SQL Server 管理オブジェクトの使用</span><span class="sxs-lookup"><span data-stu-id="bce69-137">Using SQL Server Management Objects</span></span>  
 <span data-ttu-id="bce69-138">**オペレーターにジョブの状態を通知するには**</span><span class="sxs-lookup"><span data-stu-id="bce69-138">**To notify an operator of job status**</span></span>  
  
 <span data-ttu-id="bce69-139">`Job`Visual Basic、Visual C#、PowerShell など、選択したプログラミング言語でクラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="bce69-139">Use the `Job` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span> <span data-ttu-id="bce69-140">詳細については、「 [SQL Server 管理オブジェクト (SMO) プログラミング ガイド](https://msdn.microsoft.com/library/ms162169.aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bce69-140">For more information, see [SQL Server Management Objects (SMO)](https://msdn.microsoft.com/library/ms162169.aspx).</span></span>  
