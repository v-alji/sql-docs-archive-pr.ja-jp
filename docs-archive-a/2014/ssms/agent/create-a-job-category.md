---
title: ジョブ カテゴリの作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, categories
- jobs [SQL Server Agent], categories
- categories [SQL Server Agent jobs]
ms.assetid: e24a6d38-d231-4f64-ab89-2d1ef6f5792c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1f6daeeca6253861e8a9dcbb72faa2bd55eb2761
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720804"
---
# <a name="create-a-job-category"></a><span data-ttu-id="35706-102">ジョブ カテゴリの作成</span><span class="sxs-lookup"><span data-stu-id="35706-102">Create a Job Category</span></span>
  <span data-ttu-id="35706-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、 [!INCLUDE[tsql](../../includes/tsql-md.md)] 、または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理オブジェクトを使用して、ジョブ カテゴリを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="35706-103">This topic describes how to create a job category in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)] or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Objects.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="35706-104">エージェントには、ジョブを割り当てることができる組み込みのジョブ カテゴリが用意されています。また、ジョブ カテゴリを作成してジョブを割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="35706-104">Agent provides built-in job categories that you can assign jobs to, or you can create a job category and assign jobs to it.</span></span> <span data-ttu-id="35706-105">ジョブ カテゴリを使用してジョブを管理すると、フィルター操作やグループ化を簡単に行うことができます。</span><span class="sxs-lookup"><span data-stu-id="35706-105">Job categories help you organize your jobs for easy filtering and grouping.</span></span> <span data-ttu-id="35706-106">たとえば、データベース バックアップに関するすべてのジョブを [データベースのメンテナンス] カテゴリとしてまとめます。</span><span class="sxs-lookup"><span data-stu-id="35706-106">For example, you can organize all your database backup jobs in the Database Maintenance category.</span></span> <span data-ttu-id="35706-107">ジョブ カテゴリは、独自に作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="35706-107">You can also create your own job categories.</span></span>  
  
 
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="35706-108">はじめに</span><span class="sxs-lookup"><span data-stu-id="35706-108">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="35706-109">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="35706-109">Limitations and Restrictions</span></span>  
 <span data-ttu-id="35706-110">マルチサーバー カテゴリは、マスター サーバー上だけに存在します。</span><span class="sxs-lookup"><span data-stu-id="35706-110">Multiserver categories exist only on a master server.</span></span> <span data-ttu-id="35706-111">マスター サーバー上で使用できるのは、**[未カテゴリ化 (マルチサーバー)]** という既定のジョブ カテゴリだけです。</span><span class="sxs-lookup"><span data-stu-id="35706-111">There is only one default job category available on a master server: [**Uncategorized (Multi-Server)**].</span></span> <span data-ttu-id="35706-112">マルチサーバー ジョブがダウンロードされると、ターゲット サーバー上ではそのカテゴリが **[MSX からのジョブ]** に変更されます。</span><span class="sxs-lookup"><span data-stu-id="35706-112">When a multiserver job is downloaded, its category is changed to **Jobs From MSX** at the target server.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="35706-113">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="35706-113">Security</span></span>  
 <span data-ttu-id="35706-114">詳細については、「 [SQL Server エージェントのセキュリティの実装](implement-sql-server-agent-security.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="35706-114">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="35706-115">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="35706-115">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-job-category"></a><span data-ttu-id="35706-116">ジョブ カテゴリを作成するには</span><span class="sxs-lookup"><span data-stu-id="35706-116">To create a job category</span></span>  
  
1.  <span data-ttu-id="35706-117">**オブジェクト エクスプ ローラー**で、プラス記号をクリックして、ジョブ カテゴリを作成するサーバーを展開します。</span><span class="sxs-lookup"><span data-stu-id="35706-117">In **Object Explorer**, click the plus sign to expand the server where you want to create a job category.</span></span>  
  
2.  <span data-ttu-id="35706-118">プラス記号をクリックして **[SQL Server エージェント]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="35706-118">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="35706-119">**[ジョブ]** フォルダーを右クリックし、 **[ジョブ カテゴリの管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="35706-119">Right-click the **Jobs** folder and select **Manage Job Categories**.</span></span>  
  
4.  <span data-ttu-id="35706-120">[**ジョブカテゴリ**_server_name_の管理] ダイアログボックスで、[**追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="35706-120">In the **Manage Job Categories**_server_name_ dialog box, click **Add**.</span></span>  
  
5.  <span data-ttu-id="35706-121">新しいダイアログ ボックスで、 **[名前]** ボックスに新しいジョブ カテゴリの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="35706-121">In the new dialog box, in the **Name** box, enter a name for the new job category.</span></span>  
  
6.  <span data-ttu-id="35706-122">**[すべてのジョブを表示]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="35706-122">Select the **Show all jobs** check box.</span></span> <span data-ttu-id="35706-123">ジョブに対応するチェック ボックスをオンにして、新しいカテゴリのジョブを 1 つ以上選択します。</span><span class="sxs-lookup"><span data-stu-id="35706-123">Select one or more jobs for the new category by checking the boxes corresponding to the jobs.</span></span>  
  
7.  <span data-ttu-id="35706-124">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="35706-124">Click **OK**.</span></span>  
  
8.  <span data-ttu-id="35706-125">[**ジョブカテゴリ**_server_name_の管理] ダイアログボックスで、[最新の状態に**更新**] をクリックして、新しいジョブカテゴリが [アクティブ] になっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="35706-125">In the **Manage Job Categories**_server_name_ dialog box, click **Refresh** to ensure that the new job category is active.</span></span> <span data-ttu-id="35706-126">すべての設定が適切であることを確認したら、このダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="35706-126">If everything looks as expected, close this dialog box.</span></span>  
  
 <span data-ttu-id="35706-127">これらのダイアログボックスの詳細については、「[ジョブカテゴリ:](job-categories-manage-job-categories.md)ジョブカテゴリの管理」および「ジョブカテゴリのプロパティ」、[および「新しいジョブカテゴリ](job-categories-properties-new-job-category.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="35706-127">For more information on these dialog boxes, see [Job Categories: Manage Job Categories](job-categories-manage-job-categories.md) and [Job Categories Properties and New Job Category](job-categories-properties-new-job-category.md).</span></span>  

##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="35706-128">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="35706-128">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-job-category"></a><span data-ttu-id="35706-129">ジョブ カテゴリを作成するには</span><span class="sxs-lookup"><span data-stu-id="35706-129">To create a job category</span></span>  
  
1.  <span data-ttu-id="35706-130">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="35706-130">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="35706-131">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="35706-131">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="35706-132">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="35706-132">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```sql
    -- creates a local job category named AdminJobs   
    USE msdb ;  
    GO  
    EXEC dbo.sp_add_category  
        @class=N'JOB',  
        @type=N'LOCAL',  
        @name=N'AdminJobs' ;  
    GO  
    ```  
  
 <span data-ttu-id="35706-133">詳細については、「 [sp_add_category &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-add-category-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="35706-133">For more information, see [sp_add_category &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-category-transact-sql).</span></span>  

##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="35706-134">SQL Server 管理オブジェクトの使用</span><span class="sxs-lookup"><span data-stu-id="35706-134">Using SQL Server Management Objects</span></span>  
 <span data-ttu-id="35706-135">**ジョブ カテゴリを作成するには**</span><span class="sxs-lookup"><span data-stu-id="35706-135">**To create a job category**</span></span>  
  
 <span data-ttu-id="35706-136">Visual Basic、Visual C#、PowerShell などのプログラミング言語で `JobCategory` クラスを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="35706-136">Call the `JobCategory` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span> <span data-ttu-id="35706-137">コード例については、「 [SQL Server エージェントでの自動管理タスクのスケジュール設定](sql-server-agent.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="35706-137">For example code, see [Scheduling Automatic Administrative Tasks in SQL Server Agent](sql-server-agent.md).</span></span>  
