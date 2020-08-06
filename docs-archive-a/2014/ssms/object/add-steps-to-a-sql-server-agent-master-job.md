---
title: SQL Server エージェントのマスター ジョブへのステップの追加 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: 9cc1e8ab-7ddc-427b-859e-203aa7e24642
author: stevestein
ms.author: sstein
ms.openlocfilehash: ccff8d6f4faa7bef549b5a179a957ce798250dbe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630781"
---
# <a name="add-steps-to-a-sql-server-agent-master-job"></a><span data-ttu-id="4dbdb-102">Add Steps to a SQL Server Agent Master Job</span><span class="sxs-lookup"><span data-stu-id="4dbdb-102">Add Steps to a SQL Server Agent Master Job</span></span>
  <span data-ttu-id="4dbdb-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して、 [!INCLUDE[tsql](../../includes/tsql-md.md)]で SQL Server エージェントのマスター ジョブにステップを追加する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4dbdb-103">This topic describes how to add steps to a SQL Server Agent master job in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="4dbdb-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="4dbdb-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="4dbdb-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="4dbdb-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="4dbdb-106">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="4dbdb-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="4dbdb-107">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="4dbdb-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="4dbdb-108">**以下を使用して SQL Server エージェントのマスター ジョブにステップを追加するには:**</span><span class="sxs-lookup"><span data-stu-id="4dbdb-108">**To add steps to a SQL Server Agent master job, using:**</span></span>  
  
     [<span data-ttu-id="4dbdb-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="4dbdb-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="4dbdb-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="4dbdb-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="4dbdb-111">はじめに</span><span class="sxs-lookup"><span data-stu-id="4dbdb-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="4dbdb-112">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="4dbdb-112">Limitations and Restrictions</span></span>  
 <span data-ttu-id="4dbdb-113">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのマスター ジョブの対象サーバーを、ローカル サーバーとリモート サーバーの両方に設定することはできません。</span><span class="sxs-lookup"><span data-stu-id="4dbdb-113">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent master job cannot be targeted at both local and remote servers.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="4dbdb-114">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="4dbdb-114">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="4dbdb-115">Permissions</span><span class="sxs-lookup"><span data-stu-id="4dbdb-115">Permissions</span></span>  
 <span data-ttu-id="4dbdb-116">**sysadmin** 固定サーバー ロールのメンバー以外は、所有しているジョブしか変更できません。</span><span class="sxs-lookup"><span data-stu-id="4dbdb-116">Unless you are a member of the **sysadmin** fixed server role, you can only modify jobs that you own.</span></span> <span data-ttu-id="4dbdb-117">詳細については、「 [SQL Server エージェントのセキュリティの実装](../agent/implement-sql-server-agent-security.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="4dbdb-117">For detailed information, see [Implement SQL Server Agent Security](../agent/implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="4dbdb-118">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="4dbdb-118">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-add-steps-to-a-sql-server-agent-master-job"></a><span data-ttu-id="4dbdb-119">SQL Server エージェントのマスター ジョブにステップを追加するには</span><span class="sxs-lookup"><span data-stu-id="4dbdb-119">To add steps to a SQL Server Agent master job</span></span>  
  
1.  <span data-ttu-id="4dbdb-120">**オブジェクト エクスプローラー** で、ステップを追加するジョブを含むサーバーをプラス記号をクリックして展開します。</span><span class="sxs-lookup"><span data-stu-id="4dbdb-120">In **Object Explorer,** click the plus sign to expand the server that contains the job to which you want to add steps.</span></span>  
  
2.  <span data-ttu-id="4dbdb-121">プラス記号をクリックして **[SQL Server エージェント]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="4dbdb-121">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="4dbdb-122">プラス記号をクリックして **[ジョブ]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="4dbdb-122">Click the plus sign to expand the **Jobs** folder.</span></span>  
  
4.  <span data-ttu-id="4dbdb-123">ステップを追加するジョブを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4dbdb-123">Right-click the job to which you want to add steps and select **Properties**.</span></span>  
  
5.  <span data-ttu-id="4dbdb-124">**[ジョブのプロパティ -** _<ジョブ名>]_ ダイアログ ボックスで、 **[ページの選択]** の **[ステップ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="4dbdb-124">In the **Job Properties -**_job_name_ dialog box, under **Select a page**, select **Steps**.</span></span> <span data-ttu-id="4dbdb-125">このページで使用可能なオプションの詳細については、「[ジョブのプロパティ: 新しいジョブ &#40;ステップページ&#41;](../agent/job-properties-new-job-steps-page.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4dbdb-125">For more information on the available options on this page, see [Job Properties:New Job &#40;Steps Page&#41;](../agent/job-properties-new-job-steps-page.md).</span></span>  

6.  <span data-ttu-id="4dbdb-126">完了したら、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4dbdb-126">When finished, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="4dbdb-127">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="4dbdb-127">Using Transact-SQL</span></span>  
  
#### <a name="to-add-steps-to-a-sql-server-agent-master-job"></a><span data-ttu-id="4dbdb-128">SQL Server エージェントのマスター ジョブにステップを追加するには</span><span class="sxs-lookup"><span data-stu-id="4dbdb-128">To add steps to a SQL Server Agent master job</span></span>  
  
1.  <span data-ttu-id="4dbdb-129">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="4dbdb-129">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="4dbdb-130">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4dbdb-130">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="4dbdb-131">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4dbdb-131">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- creates a job step that changes database access to read-only for the Sales database.   
    -- specifies 5 retry attempts, with each retry to occur after a 5 minute wait.   
    -- assumes that the Weekly Sales Data Backup job already exists  
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
  
 <span data-ttu-id="4dbdb-132">詳細については、「 [sp_add_jobstep &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4dbdb-132">For more information, see [sp_add_jobstep &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql).</span></span>  
  
  
