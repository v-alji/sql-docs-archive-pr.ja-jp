---
title: メンテナンス プランの作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- maintenance plans [SQL Server], creating
ms.assetid: a945cb65-ba7a-42f4-bbd9-6ec675745523
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 3df0c1cd06427deb051a9c4214d03084b44c6f9b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643323"
---
# <a name="create-a-maintenance-plan"></a><span data-ttu-id="2e331-102">メンテナンス プランの作成</span><span class="sxs-lookup"><span data-stu-id="2e331-102">Create a Maintenance Plan</span></span>
  <span data-ttu-id="2e331-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して、単一サーバーまたはマルチサーバーのメンテナンス プランを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="2e331-103">This topic describes how to create a single server or multiserver maintenance plan in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="2e331-104">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]でメンテナンス プランを作成する方法には、メンテナンス プラン ウィザードを使用する方法とデザイン画面を使用する方法の 2 とおりがあります。</span><span class="sxs-lookup"><span data-stu-id="2e331-104">Using [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], you can create these maintenance plans in one of two ways: by either using the Maintenance Plan Wizard or the design surface.</span></span> <span data-ttu-id="2e331-105">基本的なメンテナンス プランを作成する場合は、ウィザードが最適です。それに対して、デザイン画面を使用してプランを作成すると、高度なワークフローを利用できます。</span><span class="sxs-lookup"><span data-stu-id="2e331-105">The Wizard is best for creating basic maintenance plans, while creating a plan using the design surface allows you to utilize enhanced workflow.</span></span>  
  
 <span data-ttu-id="2e331-106">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="2e331-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="2e331-107">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="2e331-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="2e331-108">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="2e331-108">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="2e331-109">Security</span><span class="sxs-lookup"><span data-stu-id="2e331-109">Security</span></span>](#Security)  
  
-   <span data-ttu-id="2e331-110">**メンテナンス プランを作成するために使用するもの:**</span><span class="sxs-lookup"><span data-stu-id="2e331-110">**To create a maintenance plan, using:**</span></span>  
  
     [<span data-ttu-id="2e331-111">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="2e331-111">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="2e331-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="2e331-112">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="2e331-113">はじめに</span><span class="sxs-lookup"><span data-stu-id="2e331-113">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="2e331-114">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="2e331-114">Limitations and Restrictions</span></span>  
 <span data-ttu-id="2e331-115">マルチサーバー メンテナンス プランを作成するには、1 台のマスター サーバーと 1 台以上のターゲット サーバーを含むマルチサーバー環境を構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2e331-115">To create a multiserver maintenance plan, a multiserver environment containing one master server and one or more target servers must be configured.</span></span> <span data-ttu-id="2e331-116">マルチサーバー メンテナンス プランは、マスター サーバー上で作成および管理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2e331-116">Multiserver maintenance plans must be created and maintained on the master server.</span></span> <span data-ttu-id="2e331-117">このプランはターゲット サーバー上でも表示できますが、ターゲット サーバーでは管理できません。</span><span class="sxs-lookup"><span data-stu-id="2e331-117">These plans can be viewed, but not maintained, on target servers.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="2e331-118">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="2e331-118">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="2e331-119">Permissions</span><span class="sxs-lookup"><span data-stu-id="2e331-119">Permissions</span></span>  
 <span data-ttu-id="2e331-120">メンテナンス プランを作成または管理するには、 **sysadmin** 固定サーバー ロールのメンバーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="2e331-120">To create or manage Maintenance Plans, you must be a member of the **sysadmin** fixed server role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="2e331-121">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="2e331-121">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-maintenance-plan-using-the-maintenance-plan-wizard"></a><span data-ttu-id="2e331-122">メンテナンス プラン ウィザードを使用してメンテナンス プランを作成するには</span><span class="sxs-lookup"><span data-stu-id="2e331-122">To create a maintenance plan using the Maintenance Plan Wizard</span></span>  
  
1.  <span data-ttu-id="2e331-123">オブジェクト エクスプローラーで、プラス記号をクリックして、メンテナンス プランを作成するサーバーを展開します。</span><span class="sxs-lookup"><span data-stu-id="2e331-123">In Object Explorer, click the plus sign to expand the server where you want to create a maintenance plan.</span></span>  
  
2.  <span data-ttu-id="2e331-124">プラス記号をクリックして **[管理]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="2e331-124">Click the plus sign to expand the **Management** folder.</span></span>  
  
3.  <span data-ttu-id="2e331-125">**[メンテナンス プラン]** フォルダーを右クリックし、 **[メンテナンス プラン ウィザード]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2e331-125">Right-click the **Maintenance Plans** folder and select **Maintenance Plan Wizard**.</span></span>  
  
4.  <span data-ttu-id="2e331-126">ウィザードの手順に従って、メンテナンス プランを作成します。</span><span class="sxs-lookup"><span data-stu-id="2e331-126">Follow the steps of the wizard to create a maintenance plan.</span></span> <span data-ttu-id="2e331-127">詳細については、「 [Use the Maintenance Plan Wizard](use-the-maintenance-plan-wizard.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="2e331-127">For more information, see [Use the Maintenance Plan Wizard](use-the-maintenance-plan-wizard.md).</span></span>  
  
#### <a name="to-create-a-maintenance-plan-using-the-design-surface"></a><span data-ttu-id="2e331-128">デザイン画面を使用してメンテナンス プランを作成するには</span><span class="sxs-lookup"><span data-stu-id="2e331-128">To create a maintenance plan using the design surface</span></span>  
  
1.  <span data-ttu-id="2e331-129">オブジェクト エクスプローラーで、プラス記号をクリックして、メンテナンス プランを作成するサーバーを展開します。</span><span class="sxs-lookup"><span data-stu-id="2e331-129">In Object Explorer, click the plus sign to expand the server where you want to create a maintenance plan.</span></span>  
  
2.  <span data-ttu-id="2e331-130">プラス記号をクリックして **[管理]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="2e331-130">Click the plus sign to expand the **Management** folder.</span></span>  
  
3.  <span data-ttu-id="2e331-131">**[メンテナンス プラン]** フォルダーを右クリックし、 **[新しいメンテナンス プラン]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2e331-131">Right-click the **Maintenance Plans** folder and select **New Maintenance Plan**.</span></span>  
  
4.  <span data-ttu-id="2e331-132">「[メンテナンス プランの作成 &#40;メンテナンス プラン デザイン画面&#41;](create-a-maintenance-plan-maintenance-plan-design-surface.md)」の手順に従って、メンテナンス プランを作成します。</span><span class="sxs-lookup"><span data-stu-id="2e331-132">Create a maintenance plan following the steps in [Create a Maintenance Plan &#40;Maintenance Plan Design Surface&#41;](create-a-maintenance-plan-maintenance-plan-design-surface.md).</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="2e331-133">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="2e331-133">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-maintenance-plan"></a><span data-ttu-id="2e331-134">メンテナンス プランを作成するには</span><span class="sxs-lookup"><span data-stu-id="2e331-134">To create a maintenance plan</span></span>  
  
1.  <span data-ttu-id="2e331-135">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="2e331-135">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="2e331-136">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2e331-136">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="2e331-137">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2e331-137">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE msdb;  
    GO  
    --  Adds a new job, executed by the SQL Server Agent service, called "HistoryCleanupTask_1".  
    EXEC dbo.sp_add_job  
       @job_name = N'HistoryCleanupTask_1',   
       @enabled = 1,   
       @description = N'Clean up old task history' ;   
    GO  
    -- Adds a job step for reorganizing all of the indexes in the HumanResources.Employee table to the HistoryCleanupTask_1 job.   
    EXEC dbo.sp_add_jobstep  
        @job_name = N'HistoryCleanupTask_1',   
        @step_name = N'Reorganize all indexes on HumanResources.Employee table',   
        @subsystem = N'TSQL',   
        @command = N'USE AdventureWorks2012  
    GO  
    ALTER INDEX AK_Employee_LoginID ON HumanResources.Employee REORGANIZE WITH ( LOB_COMPACTION = ON )   
    GO  
    USE AdventureWorks2012  
    GO  
    ALTER INDEX AK_Employee_NationalIDNumber ON HumanResources.Employee REORGANIZE WITH ( LOB_COMPACTION = ON )   
    GO  
    USE AdventureWorks2012  
    GO  
    ALTER INDEX AK_Employee_rowguid ON HumanResources.Employee REORGANIZE WITH ( LOB_COMPACTION = ON )   
    GO  
    USE AdventureWorks2012  
    GO  
    ALTER INDEX IX_Employee_OrganizationLevel_OrganizationNode ON HumanResources.Employee REORGANIZE WITH ( LOB_COMPACTION = ON )   
    GO  
    USE AdventureWorks2012  
    GO  
    ALTER INDEX IX_Employee_OrganizationNode ON HumanResources.Employee REORGANIZE WITH ( LOB_COMPACTION = ON )   
    GO  
    USE AdventureWorks2012  
    GO  
    ALTER INDEX PK_Employee_BusinessEntityID ON HumanResources.Employee REORGANIZE WITH ( LOB_COMPACTION = ON )   
    GO  
    ',   
        @retry_attempts = 5,   
        @retry_interval = 5 ;   
    GO  
    -- Creates a schedule named RunOnce that executes every day when the time on the server is 23:00.   
    EXEC dbo.sp_add_schedule  
        @schedule_name = N'RunOnce',   
        @freq_type = 4,   
        @freq_interval = 1,   
        @active_start_time = 233000 ;   
    GO  
    -- Attaches the RunOnce schedule to the job HistoryCleanupTask_1.   
    EXEC sp_attach_schedule  
       @job_name = N'HistoryCleanupTask_1'  
       @schedule_name = N'RunOnce' ;   
    GO  
  
    ```  
  
 <span data-ttu-id="2e331-138">詳細については、次を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2e331-138">For more information, see:</span></span>  
  
-   [<span data-ttu-id="2e331-139">sp_add_job &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="2e331-139">sp_add_job &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-add-job-transact-sql)  
  
-   [<span data-ttu-id="2e331-140">sp_add_jobstep &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="2e331-140">sp_add_jobstep &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql)  
  
-   [<span data-ttu-id="2e331-141">sp_add_schedule &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="2e331-141">sp_add_schedule &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-add-schedule-transact-sql)  
  
-   [<span data-ttu-id="2e331-142">sp_attach_schedule &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="2e331-142">sp_attach_schedule &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-attach-schedule-transact-sql)  
  
  
