---
title: ジョブの所有権を他のユーザーに割り当てる | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], owners
- owners [SQL Server], jobs
- SQL Server Agent jobs, owners
ms.assetid: 2ded5e9c-4251-4fb1-a047-99f13d150b61
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2cf03fdc9031ce9761125d95619438837f2959bb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631466"
---
# <a name="give-others-ownership-of-a-job"></a><span data-ttu-id="71e00-102">Give Others Ownership of a Job</span><span class="sxs-lookup"><span data-stu-id="71e00-102">Give Others Ownership of a Job</span></span>
  <span data-ttu-id="71e00-103">このトピックでは、エージェントジョブの所有権を [!INCLUDE[msCoName](../../includes/msconame-md.md)] 別のユーザーに再割り当てする方法について説明し [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="71e00-103">This topic describes how to reassign ownership of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs to another user.</span></span>  
  
-   <span data-ttu-id="71e00-104">**作業を開始する準備:** [制限事項と制約事項](#Restrictions)、[セキュリティ](#Security)</span><span class="sxs-lookup"><span data-stu-id="71e00-104">**Before you begin:**  [Limitations and Restrictions](#Restrictions), [Security](#Security)</span></span>  
  
-   <span data-ttu-id="71e00-105">**ジョブの所有権を他のユーザーに割り当てる方法:**</span><span class="sxs-lookup"><span data-stu-id="71e00-105">**To give others ownership of a job, using:**</span></span>  
  
     [<span data-ttu-id="71e00-106">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="71e00-106">SQL Server Management Studio</span></span>](#SSMSProc2)  
  
     [<span data-ttu-id="71e00-107">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="71e00-107">Transact-SQL</span></span>](#TsqlProc2)  
  
     [<span data-ttu-id="71e00-108">SQL Server 管理オブジェクト</span><span class="sxs-lookup"><span data-stu-id="71e00-108">SQL Server Management Objects</span></span>](#SMOProc2)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="71e00-109">はじめに</span><span class="sxs-lookup"><span data-stu-id="71e00-109">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="71e00-110">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="71e00-110">Limitations and Restrictions</span></span>  
 <span data-ttu-id="71e00-111">ジョブを作成するには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント固定データベース ロールか **sysadmin** 固定サーバー ロールのメンバーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="71e00-111">To create a job, a user must be a member of one of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent fixed database roles or the **sysadmin** fixed server role.</span></span> <span data-ttu-id="71e00-112">ジョブの編集は、ジョブの所有者または **sysadmin** ロールのメンバーのみが行うことができます。</span><span class="sxs-lookup"><span data-stu-id="71e00-112">A job can be edited only by its owner or members of the **sysadmin** role.</span></span> <span data-ttu-id="71e00-113">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント固定データベース ロールの詳細については、「 [SQL Server エージェントの固定データベース ロール](sql-server-agent-fixed-database-roles.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="71e00-113">For more information about the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent fixed database roles, see [SQL Server Agent Fixed Database Roles](sql-server-agent-fixed-database-roles.md).</span></span>  
  
 <span data-ttu-id="71e00-114">ジョブの所有者を変更するには、システム管理者でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="71e00-114">You must be a system administrator to change the owner of a job.</span></span>  
  
 <span data-ttu-id="71e00-115">別のログインにジョブを割り当てた場合に、新しい所有者がそのジョブを正常に実行できる十分な権限を持っていないこともあります。</span><span class="sxs-lookup"><span data-stu-id="71e00-115">Assigning a job to another login does not guarantee that the new owner has sufficient permission to run the job successfully.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="71e00-116">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="71e00-116">Security</span></span>  
 <span data-ttu-id="71e00-117">セキュリティを確保するため、ジョブの所有者または **sysadmin** ロールのメンバーだけがジョブの定義を変更できます。</span><span class="sxs-lookup"><span data-stu-id="71e00-117">For security reasons, only the job owner or a member of the **sysadmin** role can change the definition of the job.</span></span> <span data-ttu-id="71e00-118">**sysadmin** 固定サーバー ロールのメンバーのみが別のユーザーにジョブの所有権を割り当てることができ、ジョブの所有者とは無関係にジョブを実行できます。</span><span class="sxs-lookup"><span data-stu-id="71e00-118">Only members of the **sysadmin** fixed server role can assign job ownership to other users, and they can run any job, regardless of the job owner.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="71e00-119">ジョブの所有権を **sysadmin** 固定サーバー ロールのメンバーでないユーザーに変更し、そのジョブがプロキシ アカウントを必要とするジョブ ステップを実行する ( [!INCLUDE[ssIS](../../includes/ssis-md.md)] パッケージの実行など) 場合は、ユーザーがそのプロキシ アカウントにアクセスできることを確認してください。アクセスできない場合、ジョブは失敗します。</span><span class="sxs-lookup"><span data-stu-id="71e00-119">If you change job ownership to a user who is not a member of the **sysadmin** fixed server role, and the job is executing job steps that require proxy accounts (for example, [!INCLUDE[ssIS](../../includes/ssis-md.md)] package execution), make sure that the user has access to that proxy account or else the job will fail.</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="71e00-120">Permissions</span><span class="sxs-lookup"><span data-stu-id="71e00-120">Permissions</span></span>  
 <span data-ttu-id="71e00-121">詳細については、「 [SQL Server エージェントのセキュリティの実装](implement-sql-server-agent-security.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="71e00-121">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProc2"></a> <span data-ttu-id="71e00-122">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="71e00-122">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="71e00-123">**ジョブの所有権を他のユーザーに割り当てるには**</span><span class="sxs-lookup"><span data-stu-id="71e00-123">**To give others ownership of a job**</span></span>  
  
1.  <span data-ttu-id="71e00-124">**オブジェクトエクスプローラー**で、のインスタンスに接続し、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] そのインスタンスを展開します。</span><span class="sxs-lookup"><span data-stu-id="71e00-124">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="71e00-125">**[SQL Server エージェント]**、 **[ジョブ]** の順に展開し、ジョブを右クリックして **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="71e00-125">Expand **SQL Server Agent**, expand **Jobs**, right-click the job, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="71e00-126">**[所有者]** ボックスの一覧で、ログインを選択します。</span><span class="sxs-lookup"><span data-stu-id="71e00-126">In the **Owner** list, select a login.</span></span> <span data-ttu-id="71e00-127">ジョブの所有者を変更するには、システム管理者でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="71e00-127">You must be a system administrator to change the owner of a job.</span></span>  
  
     <span data-ttu-id="71e00-128">別のログインにジョブを割り当てた場合に、新しい所有者がそのジョブを正常に実行できる十分な権限を持っていないこともあります。</span><span class="sxs-lookup"><span data-stu-id="71e00-128">Assigning a job to another login does not guarantee that the new owner has sufficient permission to run the job successfully.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProc2"></a> <span data-ttu-id="71e00-129">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="71e00-129">Using Transact-SQL</span></span>  
 <span data-ttu-id="71e00-130">**ジョブの所有権を他のユーザーに割り当てるには**</span><span class="sxs-lookup"><span data-stu-id="71e00-130">**To give others ownership of a job**</span></span>  
  
1.  <span data-ttu-id="71e00-131">オブジェクト エクスプローラーで、データベース エンジンのインスタンスに接続し、そのインスタンスを展開します。</span><span class="sxs-lookup"><span data-stu-id="71e00-131">In Object Explorer, connect to an instance of the Database Engine, and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="71e00-132">ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="71e00-132">On the toolbar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="71e00-133">クエリウィンドウで、 [sp_manage_jobs_by_login &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-manage-jobs-by-login-transact-sql)システムストアドプロシージャを使用する次のステートメントを入力します。</span><span class="sxs-lookup"><span data-stu-id="71e00-133">In the query window, enter the following statements that use the [sp_manage_jobs_by_login &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-manage-jobs-by-login-transact-sql) system stored procedure.</span></span> <span data-ttu-id="71e00-134">次の例では、 `danw` からのすべてのジョブを `fran??oisa`に再割り当てします。</span><span class="sxs-lookup"><span data-stu-id="71e00-134">The following example reassigns all jobs from `danw` to `fran??oisa`.</span></span>  
  
    ```sql
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_manage_jobs_by_login  
        @action = N'REASSIGN',  
        @current_owner_login_name = N'danw',  
        @new_owner_login_name = N'fran??oisa' ;  
    GO  
    ```  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMOProc2"></a><span data-ttu-id="71e00-135">SQL Server 管理オブジェクトの使用</span><span class="sxs-lookup"><span data-stu-id="71e00-135">Using SQL Server Management Objects</span></span>  

### <a name="to-give-others-ownership-of-a-job"></a><span data-ttu-id="71e00-136">ジョブの所有権を他のユーザーに割り当てるには</span><span class="sxs-lookup"><span data-stu-id="71e00-136">To give others ownership of a job</span></span>
  
1.  <span data-ttu-id="71e00-137">Visual Basic、Visual C#、PowerShell などのプログラミング言語で `Job` クラスを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="71e00-137">Call the `Job` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span> <span data-ttu-id="71e00-138">コード例については、「 [SQL Server エージェントでの自動管理タスクのスケジュール設定](sql-server-agent.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="71e00-138">For example code, see [Scheduling Automatic Administrative Tasks in SQL Server Agent](sql-server-agent.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71e00-139">参照</span><span class="sxs-lookup"><span data-stu-id="71e00-139">See Also</span></span>  
 <span data-ttu-id="71e00-140">[ジョブの実装](implement-jobs.md) </span><span class="sxs-lookup"><span data-stu-id="71e00-140">[Implement Jobs](implement-jobs.md) </span></span>  
 [<span data-ttu-id="71e00-141">ジョブの作成</span><span class="sxs-lookup"><span data-stu-id="71e00-141">Create Jobs</span></span>](create-jobs.md)  
