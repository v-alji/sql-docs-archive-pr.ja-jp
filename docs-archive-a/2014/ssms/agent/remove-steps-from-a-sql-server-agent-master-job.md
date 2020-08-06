---
title: SQL Server エージェントのマスター ジョブからのステップの削除 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: 871e6162-1221-464d-8f7f-7e454dcd9edb
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5996971225ee0b300b307c5af24dec464dbfd43c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645316"
---
# <a name="remove-steps-from-a-sql-server-agent-master-job"></a><span data-ttu-id="0dfa8-102">Remove Steps from a SQL Server Agent Master Job</span><span class="sxs-lookup"><span data-stu-id="0dfa8-102">Remove Steps from a SQL Server Agent Master Job</span></span>
  <span data-ttu-id="0dfa8-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して、 [!INCLUDE[tsql](../../includes/tsql-md.md)]で SQL Server エージェントのマスター ジョブからステップを削除する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="0dfa8-103">This topic describes how to remove steps from a SQL Server Agent master job in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="0dfa8-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="0dfa8-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="0dfa8-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="0dfa8-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="0dfa8-106">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="0dfa8-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="0dfa8-107">Security</span><span class="sxs-lookup"><span data-stu-id="0dfa8-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="0dfa8-108">**以下を使用して SQL Server エージェントのマスター ジョブからステップを削除するには:**</span><span class="sxs-lookup"><span data-stu-id="0dfa8-108">**To remove steps from a SQL Server Agent master job, using:**</span></span>  
  
     [<span data-ttu-id="0dfa8-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="0dfa8-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="0dfa8-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="0dfa8-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="0dfa8-111">はじめに</span><span class="sxs-lookup"><span data-stu-id="0dfa8-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="0dfa8-112">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="0dfa8-112">Limitations and Restrictions</span></span>  
 <span data-ttu-id="0dfa8-113">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのマスター ジョブの対象サーバーを、ローカル サーバーとリモート サーバーの両方に設定することはできません。</span><span class="sxs-lookup"><span data-stu-id="0dfa8-113">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent master job cannot be targeted at both local and remote servers.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="0dfa8-114">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="0dfa8-114">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="0dfa8-115">Permissions</span><span class="sxs-lookup"><span data-stu-id="0dfa8-115">Permissions</span></span>  
 <span data-ttu-id="0dfa8-116">**sysadmin** 固定サーバー ロールのメンバー以外は、所有しているジョブしか変更できません。</span><span class="sxs-lookup"><span data-stu-id="0dfa8-116">Unless you are a member of the **sysadmin** fixed server role, you can only modify jobs that you own.</span></span> <span data-ttu-id="0dfa8-117">詳細については、「 [SQL Server エージェントのセキュリティの実装](implement-sql-server-agent-security.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="0dfa8-117">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="0dfa8-118">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="0dfa8-118">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-remove-steps-from-a-sql-server-agent-master-job"></a><span data-ttu-id="0dfa8-119">SQL Server エージェントのマスター ジョブからステップを削除するには</span><span class="sxs-lookup"><span data-stu-id="0dfa8-119">To remove steps from a SQL Server Agent master job</span></span>  
  
1.  <span data-ttu-id="0dfa8-120">**オブジェクト エクスプローラー** で、ステップを削除するジョブを含むサーバーをプラス記号をクリックして展開します。</span><span class="sxs-lookup"><span data-stu-id="0dfa8-120">In **Object Explorer,** click the plus sign to expand the server that contains the job where you want to delete steps.</span></span>  
  
2.  <span data-ttu-id="0dfa8-121">プラス記号をクリックして **[SQL Server エージェント]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="0dfa8-121">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="0dfa8-122">プラス記号をクリックして **[ジョブ]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="0dfa8-122">Click the plus sign to expand the **Jobs** folder.</span></span>  
  
4.  <span data-ttu-id="0dfa8-123">ステップを削除するジョブを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0dfa8-123">Right-click the job where you want to delete steps and select **Properties**.</span></span>  
  
5.  <span data-ttu-id="0dfa8-124">[**ジョブのプロパティ-**_job_name_ ] ダイアログボックスの [**ページの選択**] で、[**ステップ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="0dfa8-124">In the **Job Properties -**_job_name_ dialog box, under **Select a page**, select **Steps**.</span></span>  
  
6.  <span data-ttu-id="0dfa8-125">**[ジョブ ステップの一覧]** で削除するジョブ ステップを選択し、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0dfa8-125">Under **Job step list**, select the job step you want to delete and click **Delete**.</span></span>  
  
7.  <span data-ttu-id="0dfa8-126">完了したら、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0dfa8-126">When finished, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="0dfa8-127">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="0dfa8-127">Using Transact-SQL</span></span>  
  
#### <a name="to-remove-steps-from-a-sql-server-agent-master-job"></a><span data-ttu-id="0dfa8-128">SQL Server エージェントのマスター ジョブからステップを削除するには</span><span class="sxs-lookup"><span data-stu-id="0dfa8-128">To remove steps from a SQL Server Agent master job</span></span>  
  
1.  <span data-ttu-id="0dfa8-129">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="0dfa8-129">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="0dfa8-130">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0dfa8-130">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="0dfa8-131">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0dfa8-131">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- removes job step 1 from the job Weekly Sales Data Backup   
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_delete_jobstep  
        @job_name = N'Weekly Sales Data Backup',  
        @step_id = 1 ;  
    GO  
    ```  
  
 <span data-ttu-id="0dfa8-132">詳細については、「 [sp_delete_jobstep &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-jobstep-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0dfa8-132">For more information, see [sp_delete_jobstep &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-jobstep-transact-sql).</span></span>  
  
  
