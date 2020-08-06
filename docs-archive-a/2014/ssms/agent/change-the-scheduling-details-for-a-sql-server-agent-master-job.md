---
title: SQL Server エージェントのマスター ジョブのスケジューリングの詳細の変更 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: f5414451-4d8e-464b-bd9e-f2b70c6899b3
author: stevestein
ms.author: sstein
ms.openlocfilehash: 85546bc93e6626bfcc85a28f06a4c2fe24fe9fd1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645346"
---
# <a name="change-the-scheduling-details-for-a-sql-server-agent-master-job"></a><span data-ttu-id="9b35e-102">Change the Scheduling Details for a SQL Server Agent Master Job</span><span class="sxs-lookup"><span data-stu-id="9b35e-102">Change the Scheduling Details for a SQL Server Agent Master Job</span></span>
  <span data-ttu-id="9b35e-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して、 [!INCLUDE[tsql](../../includes/tsql-md.md)]でジョブ定義のスケジューリングの詳細を変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9b35e-103">This topic describes how to change the scheduling details for a job definition in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="9b35e-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="9b35e-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="9b35e-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="9b35e-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="9b35e-106">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="9b35e-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="9b35e-107">Security</span><span class="sxs-lookup"><span data-stu-id="9b35e-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="9b35e-108">**以下を使用してジョブ定義のスケジューリングの詳細を変更するには:**</span><span class="sxs-lookup"><span data-stu-id="9b35e-108">**To change the scheduling details for a job definition, using:**</span></span>  
  
     [<span data-ttu-id="9b35e-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="9b35e-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="9b35e-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="9b35e-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="9b35e-111">はじめに</span><span class="sxs-lookup"><span data-stu-id="9b35e-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="9b35e-112">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="9b35e-112">Limitations and Restrictions</span></span>  
 <span data-ttu-id="9b35e-113">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのマスター ジョブの対象サーバーを、ローカル サーバーとリモート サーバーの両方に設定することはできません。</span><span class="sxs-lookup"><span data-stu-id="9b35e-113">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent master job cannot be targeted at both local and remote servers.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="9b35e-114">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="9b35e-114">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="9b35e-115">Permissions</span><span class="sxs-lookup"><span data-stu-id="9b35e-115">Permissions</span></span>  
 <span data-ttu-id="9b35e-116">**sysadmin** 固定サーバー ロールのメンバー以外は、所有しているジョブしか変更できません。</span><span class="sxs-lookup"><span data-stu-id="9b35e-116">Unless you are a member of the **sysadmin** fixed server role, you can only modify jobs that you own.</span></span> <span data-ttu-id="9b35e-117">詳細については、「 [SQL Server エージェントのセキュリティの実装](implement-sql-server-agent-security.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="9b35e-117">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="9b35e-118">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="9b35e-118">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-change-the-scheduling-details-for-a-job-definition"></a><span data-ttu-id="9b35e-119">ジョブ定義のスケジューリングの詳細を変更するには</span><span class="sxs-lookup"><span data-stu-id="9b35e-119">To change the scheduling details for a job definition</span></span>  
  
1.  <span data-ttu-id="9b35e-120">**オブジェクト エクスプローラー** で、スケジュールを編集するジョブを含むサーバーをプラス記号をクリックして展開します。</span><span class="sxs-lookup"><span data-stu-id="9b35e-120">In **Object Explorer,** click the plus sign to expand the server that contains the job whose schedule you want to edit.</span></span>  
  
2.  <span data-ttu-id="9b35e-121">プラス記号をクリックして **[SQL Server エージェント]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="9b35e-121">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="9b35e-122">プラス記号をクリックして **[ジョブ]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="9b35e-122">Click the plus sign to expand the **Jobs** folder.</span></span>  
  
4.  <span data-ttu-id="9b35e-123">スケジュールを編集するジョブを右クリックして、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9b35e-123">Right-click the job whose schedule you want to edit and select **Properties**.</span></span>  
  
5.  <span data-ttu-id="9b35e-124">[**ジョブのプロパティ-**_job_name_ ] ダイアログボックスの [**ページの選択**] で、[**スケジュール**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="9b35e-124">In the **Job Properties -**_job_name_ dialog box, under **Select a page**, select **Schedules**.</span></span> <span data-ttu-id="9b35e-125">このページで使用可能なオプションの詳細については、「[ジョブのプロパティ: [新しいジョブ &#40;スケジュール] ページ&#41;](job-properties-new-job-schedules-page.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9b35e-125">For more information on the available options on this page, see [Job Properties: New Job &#40;Schedules Page&#41;](job-properties-new-job-schedules-page.md).</span></span>  
  
6.  <span data-ttu-id="9b35e-126">完了したら、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9b35e-126">When finished, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="9b35e-127">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="9b35e-127">Using Transact-SQL</span></span>  
  
#### <a name="to-change-the-scheduling-details-for-a-job-definition"></a><span data-ttu-id="9b35e-128">ジョブ定義のスケジューリングの詳細を変更するには</span><span class="sxs-lookup"><span data-stu-id="9b35e-128">To change the scheduling details for a job definition</span></span>  
  
1.  <span data-ttu-id="9b35e-129">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="9b35e-129">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="9b35e-130">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9b35e-130">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="9b35e-131">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9b35e-131">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- changes the enabled status of the NightlyJobs schedule to 0   
    -- and sets the owner to terrid.   
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_update_schedule  
        @name = 'NightlyJobs',  
        @enabled = 0,  
        @owner_login_name = 'terrid' ;  
    GO  
    ```  
  
 <span data-ttu-id="9b35e-132">詳細については、「 [sp_update_schedule &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-update-schedule-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9b35e-132">For more information, see [sp_update_schedule &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-update-schedule-transact-sql).</span></span>  
  
  
