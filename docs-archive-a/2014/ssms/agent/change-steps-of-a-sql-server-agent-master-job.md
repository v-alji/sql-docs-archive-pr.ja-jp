---
title: SQL Server エージェントのマスター ジョブのステップの変更 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: 8f1a0ee6-49ff-4080-94ca-d661daeff2a6
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7a9defc17b5b39ab8a322b6da29960eb9968c2e0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645348"
---
# <a name="change-steps-of-a-sql-server-agent-master-job"></a><span data-ttu-id="5398c-102">Change Steps of a SQL Server Agent Master Job</span><span class="sxs-lookup"><span data-stu-id="5398c-102">Change Steps of a SQL Server Agent Master Job</span></span>
  <span data-ttu-id="5398c-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して、 [!INCLUDE[tsql](../../includes/tsql-md.md)]で SQL Server エージェントのマスター ジョブのステップに変更を加える方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5398c-103">This topic describes how to make changes to the steps of a SQL Server Agent master job in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="5398c-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="5398c-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="5398c-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="5398c-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="5398c-106">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="5398c-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="5398c-107">Security</span><span class="sxs-lookup"><span data-stu-id="5398c-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="5398c-108">**以下を使用して SQL Server エージェントのマスター ジョブのステップに変更を加えるには:**</span><span class="sxs-lookup"><span data-stu-id="5398c-108">**To make changes to the steps of a SQL Server Agent master job, using:**</span></span>  
  
     [<span data-ttu-id="5398c-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="5398c-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="5398c-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="5398c-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="5398c-111">はじめに</span><span class="sxs-lookup"><span data-stu-id="5398c-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="5398c-112">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="5398c-112">Limitations and Restrictions</span></span>  
 <span data-ttu-id="5398c-113">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのマスター ジョブの対象サーバーを、ローカル サーバーとリモート サーバーの両方に設定することはできません。</span><span class="sxs-lookup"><span data-stu-id="5398c-113">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent master job cannot be targeted at both local and remote servers.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="5398c-114">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="5398c-114">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="5398c-115">Permissions</span><span class="sxs-lookup"><span data-stu-id="5398c-115">Permissions</span></span>  
 <span data-ttu-id="5398c-116">**sysadmin** 固定サーバー ロールのメンバー以外は、所有しているジョブしか変更できません。</span><span class="sxs-lookup"><span data-stu-id="5398c-116">Unless you are a member of the **sysadmin** fixed server role, you can only modify jobs that you own.</span></span> <span data-ttu-id="5398c-117">詳細については、「 [SQL Server エージェントのセキュリティの実装](implement-sql-server-agent-security.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="5398c-117">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="5398c-118">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="5398c-118">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-make-changes-to-the-steps-of-a-sql-server-agent-master-job"></a><span data-ttu-id="5398c-119">SQL Server エージェントのマスター ジョブのステップに変更を加えるには</span><span class="sxs-lookup"><span data-stu-id="5398c-119">To make changes to the steps of a SQL Server Agent master job</span></span>  
  
1.  <span data-ttu-id="5398c-120">**オブジェクト エクスプローラー** で、ステップを変更するジョブを含むサーバーをプラス記号をクリックして展開します。</span><span class="sxs-lookup"><span data-stu-id="5398c-120">In **Object Explorer,** click the plus sign to expand the server that contains the job where you want to modify steps.</span></span>  
  
2.  <span data-ttu-id="5398c-121">プラス記号をクリックして **[SQL Server エージェント]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="5398c-121">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="5398c-122">プラス記号をクリックして **[ジョブ]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="5398c-122">Click the plus sign to expand the **Jobs** folder.</span></span>  
  
4.  <span data-ttu-id="5398c-123">ステップを変更するジョブを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5398c-123">Right-click the job where you want to modify steps and select **Properties**.</span></span>  
  
5.  <span data-ttu-id="5398c-124">[**ジョブのプロパティ-**_job_name_ ] ダイアログボックスの [**ページの選択**] で、[**ステップ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="5398c-124">In the **Job Properties -**_job_name_ dialog box, under **Select a page**, select **Steps**.</span></span>  
  
6.  <span data-ttu-id="5398c-125">[**編集**] をクリックして、[**ジョブステップのプロパティ-**_job_step_name_ ] ダイアログボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="5398c-125">Click **Edit** to open the **Job Step Properties -**_job_step_name_ dialog box.</span></span> <span data-ttu-id="5398c-126">このダイアログボックスで使用可能なオプションの詳細については、「[ジョブステップのプロパティ: 新しいジョブステップ &#40;全般ページ&#41;](../../integration-services/general-page-of-integration-services-designers-options.md) 」と「[ジョブステップのプロパティ: 新しいジョブステップ &#40;詳細設定ページ&#41;](job-step-properties-new-job-step-advanced-page.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5398c-126">For more information on the available options in this dialog box, see [Job Step Properties: New Job Step &#40;General Page&#41;](../../integration-services/general-page-of-integration-services-designers-options.md) and [Job Step Properties: New Job Step &#40;Advanced Page&#41;](job-step-properties-new-job-step-advanced-page.md).</span></span>  
  
7.  <span data-ttu-id="5398c-127">完了したら、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5398c-127">When finished, click **OK**.</span></span>  
  
8.  <span data-ttu-id="5398c-128">[**ジョブのプロパティ-**_job_name_ ] ダイアログボックスで、[ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5398c-128">In the **Job Properties -**_job_name_ dialog box, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="5398c-129">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="5398c-129">Using Transact-SQL</span></span>  
  
#### <a name="to-make-changes-to-the-steps-of-a-sql-server-agent-master-job"></a><span data-ttu-id="5398c-130">SQL Server エージェントのマスター ジョブのステップに変更を加えるには</span><span class="sxs-lookup"><span data-stu-id="5398c-130">To make changes to the steps of a SQL Server Agent master job</span></span>  
  
1.  <span data-ttu-id="5398c-131">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="5398c-131">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="5398c-132">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5398c-132">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="5398c-133">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5398c-133">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- changes the number of retry attempts for the first step of the Weekly Sales Data Backup job.   
    -- After running this example, the number of retry attempts is 10   
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_update_jobstep  
        @job_name = N'Weekly Sales Data Backup',  
        @step_id = 1,  
        @retry_attempts = 10 ;  
    GO  
    ```  
  
 <span data-ttu-id="5398c-134">詳細については、「 [sp_update_jobstep &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-update-jobstep-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5398c-134">For more information, see [sp_update_jobstep &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-update-jobstep-transact-sql).</span></span>  
  
  
