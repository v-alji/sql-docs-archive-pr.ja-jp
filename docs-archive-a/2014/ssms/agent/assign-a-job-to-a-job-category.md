---
title: ジョブ カテゴリへのジョブの割り当て | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], assigning
- SQL Server Agent jobs, categories
- jobs [SQL Server Agent], categories
- categories [SQL Server Agent jobs]
- SQL Server Agent jobs, assigning
- assigning job to category
ms.assetid: a9ea65a2-1d73-4582-a335-63adeb450cb6
author: stevestein
ms.author: sstein
ms.openlocfilehash: 208ff6722a9c18fd4dd0d061575f0d496af27810
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645350"
---
# <a name="assign-a-job-to-a-job-category"></a><span data-ttu-id="7fd54-102">ジョブ カテゴリへのジョブの割り当て</span><span class="sxs-lookup"><span data-stu-id="7fd54-102">Assign a Job to a Job Category</span></span>
  <span data-ttu-id="7fd54-103">このトピック [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] は、で、、または SQL Server 管理オブジェクトを使用して、エージェントジョブをジョブカテゴリに割り当てる方法について説明し [!INCLUDE[tsql](../../includes/tsql-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="7fd54-103">This topic describes how to assign [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs to job categories in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)] or SQL Server Management Objects.</span></span>  
  
 <span data-ttu-id="7fd54-104">ジョブ カテゴリを使用してジョブを管理すると、フィルター操作やグループ化を簡単に行うことができます。</span><span class="sxs-lookup"><span data-stu-id="7fd54-104">Job categories help you organize your jobs for easy filtering and grouping.</span></span> <span data-ttu-id="7fd54-105">たとえば、データベース バックアップに関するすべてのジョブを [データベースのメンテナンス] カテゴリとしてまとめます。</span><span class="sxs-lookup"><span data-stu-id="7fd54-105">For example, you can organize all your database backup jobs in the Database Maintenance category.</span></span> <span data-ttu-id="7fd54-106">ジョブは、ビルトイン ジョブ カテゴリに割り当てたり、ユーザー定義ジョブ カテゴリを作成し、そこに割り当てたりすることができます。</span><span class="sxs-lookup"><span data-stu-id="7fd54-106">You can assign jobs to built-in job categories, or you can create a user-defined job category and then assign jobs to that.</span></span>  
  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="7fd54-107">はじめに</span><span class="sxs-lookup"><span data-stu-id="7fd54-107">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="7fd54-108">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="7fd54-108">Security</span></span>  
 <span data-ttu-id="7fd54-109">詳細については、「 [SQL Server エージェントのセキュリティの実装](implement-sql-server-agent-security.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="7fd54-109">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="7fd54-110">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="7fd54-110">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-assign-a-job-to-a-job-category"></a><span data-ttu-id="7fd54-111">ジョブ カテゴリにジョブを割り当てるには</span><span class="sxs-lookup"><span data-stu-id="7fd54-111">To assign a job to a job category</span></span>  
  
1.  <span data-ttu-id="7fd54-112">**オブジェクト エクスプ ローラー**で、プラス記号をクリックして、ジョブ カテゴリにジョブを割り当てるサーバーを展開します。</span><span class="sxs-lookup"><span data-stu-id="7fd54-112">In **Object Explorer**, click the plus sign to expand the server where you want to assign a job to a job category.</span></span>  
  
2.  <span data-ttu-id="7fd54-113">プラス記号をクリックして **[SQL Server エージェント]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="7fd54-113">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="7fd54-114">プラス記号をクリックして **[ジョブ]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="7fd54-114">Click the plus sign to expand the **Jobs** folder.</span></span>  
  
4.  <span data-ttu-id="7fd54-115">編集するジョブを右クリックし、 **[プロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="7fd54-115">Right-click the job you want to edit and select **Properties**.</span></span>  
  
5.  <span data-ttu-id="7fd54-116">[ **ジョブのプロパティ -**_job_name_ ] ダイアログ ボックスの **[カテゴリ]** 一覧で、ジョブに割り当てるジョブ カテゴリを選択します。</span><span class="sxs-lookup"><span data-stu-id="7fd54-116">In the **Job Properties -**_job_name_ dialog box, in the **Category** list, select the job category you want to assign to the job.</span></span>  
  
6.  <span data-ttu-id="7fd54-117">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7fd54-117">Click **OK**.</span></span>  
  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="7fd54-118">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="7fd54-118">Using Transact-SQL</span></span>  
  
#### <a name="to-assign-a-job-to-a-job-category"></a><span data-ttu-id="7fd54-119">ジョブ カテゴリにジョブを割り当てるには</span><span class="sxs-lookup"><span data-stu-id="7fd54-119">To assign a job to a job category</span></span>  
  
1.  <span data-ttu-id="7fd54-120">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="7fd54-120">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="7fd54-121">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7fd54-121">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="7fd54-122">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7fd54-122">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- adding a new job category to the "NightlyBackups" job  
    USE msdb ;  
    GO  
    EXEC dbo.sp_update_job  
        @job_name = N'NightlyBackups',  
        @category_name = N'[Uncategorized (Local)]';  
    GO  
    ```  
  
 <span data-ttu-id="7fd54-123">詳細については、「 [sp_update_job &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-update-job-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7fd54-123">For more information, see [sp_update_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-update-job-transact-sql).</span></span>  
  
  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="7fd54-124">SQL Server 管理オブジェクトの使用</span><span class="sxs-lookup"><span data-stu-id="7fd54-124">Using SQL Server Management Objects</span></span>  
 <span data-ttu-id="7fd54-125">**ジョブ カテゴリにジョブを割り当てるには**</span><span class="sxs-lookup"><span data-stu-id="7fd54-125">**To assign a job to a job category**</span></span>  
  
 <span data-ttu-id="7fd54-126">`JobCategory`Visual Basic、Visual C#、PowerShell など、選択したプログラミング言語でクラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="7fd54-126">Use the `JobCategory` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span>  
  
  
  
  
