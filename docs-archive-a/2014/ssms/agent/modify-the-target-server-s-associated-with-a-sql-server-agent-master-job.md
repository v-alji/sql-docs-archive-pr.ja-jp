---
title: SQL Server エージェントマスタージョブに関連付けられている対象サーバーの変更 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: 176e73b6-08aa-48ec-b349-e84b431e65cc
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6b7b5ab114366cdafe40b7a70f523fef43eb11d8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645332"
---
# <a name="modify-the-target-servers-associated-with-a-sql-server-agent-master-job"></a><span data-ttu-id="bfe6a-102">SQL Server エージェントのマスター ジョブに関連付けられているターゲット サーバーの変更</span><span class="sxs-lookup"><span data-stu-id="bfe6a-102">Modify the Target Server(s) Associated with a SQL Server Agent Master Job</span></span>
  <span data-ttu-id="bfe6a-103">このトピックでは、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)] を使用して、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で SQL Server エージェントのマスター ジョブに関連付けられているターゲット サーバーを変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="bfe6a-103">This topic describes how to modify the target server(s) associated with a SQL Server Agent master job in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="bfe6a-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="bfe6a-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="bfe6a-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="bfe6a-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="bfe6a-106">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="bfe6a-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="bfe6a-107">Security</span><span class="sxs-lookup"><span data-stu-id="bfe6a-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="bfe6a-108">**SQL Server エージェントのマスター ジョブに関連付けられているターゲット サーバーを変更するために使用するもの:**</span><span class="sxs-lookup"><span data-stu-id="bfe6a-108">**To modify the target server(s) associated with a SQL Server Agent master job, using:**</span></span>  
  
     [<span data-ttu-id="bfe6a-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="bfe6a-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="bfe6a-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="bfe6a-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="bfe6a-111">はじめに</span><span class="sxs-lookup"><span data-stu-id="bfe6a-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="bfe6a-112">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="bfe6a-112">Limitations and Restrictions</span></span>  
 <span data-ttu-id="bfe6a-113">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのマスター ジョブの対象サーバーを、ローカル サーバーとリモート サーバーの両方に設定することはできません。</span><span class="sxs-lookup"><span data-stu-id="bfe6a-113">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent master job cannot be targeted at both local and remote servers.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="bfe6a-114">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="bfe6a-114">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="bfe6a-115">Permissions</span><span class="sxs-lookup"><span data-stu-id="bfe6a-115">Permissions</span></span>  
 <span data-ttu-id="bfe6a-116">**sysadmin** 固定サーバー ロールのメンバー以外は、所有しているジョブしか変更できません。</span><span class="sxs-lookup"><span data-stu-id="bfe6a-116">Unless you are a member of the **sysadmin** fixed server role, you can only modify jobs that you own.</span></span> <span data-ttu-id="bfe6a-117">詳細については、「 [SQL Server エージェントのセキュリティの実装](implement-sql-server-agent-security.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="bfe6a-117">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="bfe6a-118">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="bfe6a-118">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-modify-the-target-servers-associated-with-a-sql-server-agent-master-job"></a><span data-ttu-id="bfe6a-119">SQL Server エージェントのマスター ジョブに関連付けられているターゲット サーバーを変更するには</span><span class="sxs-lookup"><span data-stu-id="bfe6a-119">To modify the target server(s) associated with a SQL Server Agent master job</span></span>  
  
1.  <span data-ttu-id="bfe6a-120">**オブジェクト エクスプローラー**で、ターゲット サーバーを変更するジョブを含むサーバーをプラス記号をクリックして展開します。</span><span class="sxs-lookup"><span data-stu-id="bfe6a-120">In **Object Explorer,** click the plus sign to expand the server that contains the job where you want to modify the target server.</span></span>  
  
2.  <span data-ttu-id="bfe6a-121">プラス記号をクリックして **[SQL Server エージェント]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="bfe6a-121">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="bfe6a-122">プラス記号をクリックして **[ジョブ]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="bfe6a-122">Click the plus sign to expand the **Jobs** folder.</span></span>  
  
4.  <span data-ttu-id="bfe6a-123">ターゲット サーバーを変更するジョブを右クリックし、**[プロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="bfe6a-123">Right-click the job where you want to modify the target server and select **Properties**.</span></span>  
  
5.  <span data-ttu-id="bfe6a-124">[**ジョブのプロパティ-**_job_name_ ] ダイアログボックスの [**ページの選択**] で、[**ターゲット**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="bfe6a-124">In the **Job Properties -**_job_name_ dialog box, under **Select a page**, select **Targets**.</span></span> <span data-ttu-id="bfe6a-125">このページで使用可能なオプションの詳細については、「[ジョブのプロパティ: 新しいジョブ &#40;ターゲットページ&#41;](job-properties-new-job-targets-page.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bfe6a-125">For more information on the available options on this page, see [Job Properties: New Job &#40;Targets Page&#41;](job-properties-new-job-targets-page.md).</span></span>  
  
6.  <span data-ttu-id="bfe6a-126">完了したら、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bfe6a-126">When finished, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="bfe6a-127">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="bfe6a-127">Using Transact-SQL</span></span>  
  
#### <a name="to-delete-a-target-server-currently-associated-with-a-sql-server-agent-master-job"></a><span data-ttu-id="bfe6a-128">SQL Server エージェントのマスター ジョブに現在関連付けられているターゲット サーバーを削除するには</span><span class="sxs-lookup"><span data-stu-id="bfe6a-128">To delete a target server currently associated with a SQL Server Agent master job</span></span>  
  
1.  <span data-ttu-id="bfe6a-129">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="bfe6a-129">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="bfe6a-130">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bfe6a-130">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="bfe6a-131">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bfe6a-131">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- removes the server SEATTLE2 from processing the Weekly Sales Backupsjob   
    -- assumes that the Weekly Sales Backups job exists  
    USE msdb ;  
    GO  
  
    EXEC sp_delete_jobserver  
        @job_name = N'Weekly Sales Backups',  
        @server_name = N'SEATTLE2' ;  
    GO  
    ```  
  
 <span data-ttu-id="bfe6a-132">詳細については、「 [sp_delete_jobserver &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-jobserver-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bfe6a-132">For more information, see [sp_delete_jobserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-jobserver-transact-sql).</span></span>  
  
#### <a name="to-associate-a-target-server-with-the-current-sql-server-agent-master-job"></a><span data-ttu-id="bfe6a-133">現在の SQL Server エージェントのマスター ジョブにターゲット サーバーを関連付けるには</span><span class="sxs-lookup"><span data-stu-id="bfe6a-133">To associate a target server with the current SQL Server Agent master job</span></span>  
  
1.  <span data-ttu-id="bfe6a-134">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="bfe6a-134">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="bfe6a-135">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bfe6a-135">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="bfe6a-136">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bfe6a-136">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- assigns the multiserver job Weekly Sales Backups to the server SEATTLE2   
    -- assumes that the Weekly Sales Backups job already exists and that   
    -- SEATTLE2 is registered as a target server for the current instance  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_add_jobserver  
        @job_name = N'Weekly Sales Backups',  
        @server_name = N'SEATTLE2' ;  
    GO  
    ```  
  
 <span data-ttu-id="bfe6a-137">詳細については、「 [sp_add_jobserver &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bfe6a-137">For more information, see [sp_add_jobserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql).</span></span>  
  
  
