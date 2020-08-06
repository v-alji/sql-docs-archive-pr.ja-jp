---
title: ジョブ カテゴリの削除 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, categories
- deleting job category
- jobs [SQL Server Agent], categories
- categories [SQL Server Agent jobs]
- removing job category
ms.assetid: 47a7640b-20b3-4639-ab37-b6fc73575e6c
author: stevestein
ms.author: sstein
ms.openlocfilehash: e96dd0461f3dace138b7822cdbaaa2fa242e2cb1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712689"
---
# <a name="delete-a-job-category"></a><span data-ttu-id="3fbbc-102">ジョブ カテゴリの削除</span><span class="sxs-lookup"><span data-stu-id="3fbbc-102">Delete a Job Category</span></span>
  <span data-ttu-id="3fbbc-103">このトピック [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] は、または SQL Server 管理オブジェクトを使用して、でエージェントジョブカテゴリを削除する方法について説明し [!INCLUDE[tsql](../../includes/tsql-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="3fbbc-103">This topic describes how to delete a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job category in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)] or SQL Server Management Objects.</span></span>  
  
 <span data-ttu-id="3fbbc-104">ジョブ カテゴリを使用してジョブを管理すると、フィルター操作やグループ化を簡単に行うことができます。</span><span class="sxs-lookup"><span data-stu-id="3fbbc-104">Job categories help you organize your jobs for easy filtering and grouping.</span></span> <span data-ttu-id="3fbbc-105">たとえば、データベース バックアップに関するすべてのジョブを [データベースのメンテナンス] カテゴリとしてまとめます。</span><span class="sxs-lookup"><span data-stu-id="3fbbc-105">For example, you can organize all your database backup jobs in the Database Maintenance category.</span></span>  

##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="3fbbc-106">はじめに</span><span class="sxs-lookup"><span data-stu-id="3fbbc-106">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="3fbbc-107">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="3fbbc-107">Limitations and Restrictions</span></span>  
 <span data-ttu-id="3fbbc-108">ユーザー定義のジョブ カテゴリを削除するとき、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントはそのカテゴリに割り当てられているジョブを別のジョブ カテゴリに再割り当てするように要求します。</span><span class="sxs-lookup"><span data-stu-id="3fbbc-108">When you delete a user-defined job category, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent prompts you to reassign the jobs that are assigned to it to another job category.</span></span> <span data-ttu-id="3fbbc-109">削除できるのはユーザー定義のジョブ カテゴリのみです。</span><span class="sxs-lookup"><span data-stu-id="3fbbc-109">You can only delete user-defined job categories.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="3fbbc-110">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="3fbbc-110">Security</span></span>  
 <span data-ttu-id="3fbbc-111">詳細については、「 [SQL Server エージェントのセキュリティの実装](implement-sql-server-agent-security.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="3fbbc-111">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  

##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="3fbbc-112">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="3fbbc-112">Using SQL Server Management Studio</span></span>  
  
### <a name="to-delete-a-job-category"></a><span data-ttu-id="3fbbc-113">ジョブ カテゴリを削除するには</span><span class="sxs-lookup"><span data-stu-id="3fbbc-113">To delete a job category</span></span>  
  
1.  <span data-ttu-id="3fbbc-114">**オブジェクト エクスプ ローラー**で、プラス記号をクリックして、ジョブ カテゴリを削除するサーバーを展開します。</span><span class="sxs-lookup"><span data-stu-id="3fbbc-114">In **Object Explorer**, click the plus sign to expand the server where you want to delete a job category.</span></span>  
  
2.  <span data-ttu-id="3fbbc-115">プラス記号をクリックして **[SQL Server エージェント]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="3fbbc-115">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="3fbbc-116">**[ジョブ]** フォルダーを右クリックし、 **[ジョブ カテゴリの管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3fbbc-116">Right-click the **Jobs** folder and select **Manage Job Categories**.</span></span>  
  
4.  <span data-ttu-id="3fbbc-117">[**ジョブカテゴリ**_server_name_の管理] ダイアログボックスで、削除するジョブカテゴリを選択します。</span><span class="sxs-lookup"><span data-stu-id="3fbbc-117">In the **Manage Job Categories**_server_name_ dialog box, select the job category to delete.</span></span>  
  
5.  <span data-ttu-id="3fbbc-118">**[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3fbbc-118">Click **Delete**.</span></span>  
  
6.  <span data-ttu-id="3fbbc-119">**[ジョブ カテゴリ]** ダイアログ ボックスで **[はい]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3fbbc-119">In the **Job Categories** dialog box, click **Yes**.</span></span>  
  
7.  <span data-ttu-id="3fbbc-120">[**ジョブカテゴリ**の_server_name_の管理] ダイアログボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="3fbbc-120">Close the **Manage Job Categories**_server_name_ dialog box.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="3fbbc-121">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="3fbbc-121">Using Transact-SQL</span></span>  
  
### <a name="to-delete-a-job-category"></a><span data-ttu-id="3fbbc-122">ジョブ カテゴリを削除するには</span><span class="sxs-lookup"><span data-stu-id="3fbbc-122">To delete a job category</span></span>  
  
1.  <span data-ttu-id="3fbbc-123">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="3fbbc-123">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="3fbbc-124">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3fbbc-124">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="3fbbc-125">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3fbbc-125">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```sql
    -- deletes the job category named AdminJobs.  
    USE msdb ;  
    GO   
    EXEC dbo.sp_delete_category  
        @name = N'AdminJobs',  
        @class = N'JOB' ;  
    GO  
    ```  
  
 <span data-ttu-id="3fbbc-126">詳細については、「 [sp_delete_category &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-category-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3fbbc-126">For more information, see [sp_delete_category &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-category-transact-sql).</span></span>  

  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="3fbbc-127">SQL Server 管理オブジェクトの使用</span><span class="sxs-lookup"><span data-stu-id="3fbbc-127">Using SQL Server Management Objects</span></span>  

### <a name="to-delete-a-job-category"></a><span data-ttu-id="3fbbc-128">ジョブ カテゴリを削除するには</span><span class="sxs-lookup"><span data-stu-id="3fbbc-128">To delete a job category</span></span>
  
 <span data-ttu-id="3fbbc-129">Visual Basic、Visual C#、PowerShell などのプログラミング言語で `JobCategory` クラスを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="3fbbc-129">Call the `JobCategory` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span>  
