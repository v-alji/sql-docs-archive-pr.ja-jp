---
title: ジョブ カテゴリのメンバーシップを変更する | Microsoft Docs
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
- members [SQL Server], job categories
ms.assetid: 6a18f7f0-eb50-485f-a9c7-df31ae0f994e
author: stevestein
ms.author: sstein
ms.openlocfilehash: d9ed0db394f63594937ad923734b07fed8050955
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645347"
---
# <a name="change-the-membership-of-a-job-category"></a><span data-ttu-id="0d32b-102">Change the Membership of a Job Category</span><span class="sxs-lookup"><span data-stu-id="0d32b-102">Change the Membership of a Job Category</span></span>
  <span data-ttu-id="0d32b-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、または SQL Server 管理オブジェクトを使用して、 [!INCLUDE[tsql](../../includes/tsql-md.md)]でジョブ カテゴリのメンバーシップを変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="0d32b-103">This topic describes how to change the membership of the job category in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or SQL Server Management Objects.</span></span>  
  
 <span data-ttu-id="0d32b-104">ジョブ カテゴリを使用してジョブを管理すると、フィルター操作やグループ化を簡単に行うことができます。</span><span class="sxs-lookup"><span data-stu-id="0d32b-104">Job categories help you organize your jobs for easy filtering and grouping.</span></span> <span data-ttu-id="0d32b-105">ジョブ カテゴリは、独自に作成できます。</span><span class="sxs-lookup"><span data-stu-id="0d32b-105">You can create your own job categories.</span></span> <span data-ttu-id="0d32b-106">さらに、ジョブ カテゴリの Microsoft SQL Server エージェント ジョブのメンバーシップを変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="0d32b-106">You can also change Microsoft SQL Server Agent jobs membership in job categories.</span></span>  
  
 <span data-ttu-id="0d32b-107">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="0d32b-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="0d32b-108">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="0d32b-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="0d32b-109">Security</span><span class="sxs-lookup"><span data-stu-id="0d32b-109">Security</span></span>](#Security)  
  
-   <span data-ttu-id="0d32b-110">**ジョブ カテゴリのメンバーシップを変更する方法:**</span><span class="sxs-lookup"><span data-stu-id="0d32b-110">**To change the membership of a job category, using:**</span></span>  
  
     [<span data-ttu-id="0d32b-111">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="0d32b-111">SQL Server Management Studio</span></span>](#SSMS)  
  
     [<span data-ttu-id="0d32b-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="0d32b-112">Transact-SQL</span></span>](#TSQL)  
  
     [<span data-ttu-id="0d32b-113">SQL Server 管理オブジェクト</span><span class="sxs-lookup"><span data-stu-id="0d32b-113">SQL Server Management Objects</span></span>](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="0d32b-114">はじめに</span><span class="sxs-lookup"><span data-stu-id="0d32b-114">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="0d32b-115">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="0d32b-115">Security</span></span>  
 <span data-ttu-id="0d32b-116">詳細については、「 [SQL Server エージェントのセキュリティの実装](implement-sql-server-agent-security.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="0d32b-116">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="0d32b-117">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="0d32b-117">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-change-the-membership-of-a-job-category"></a><span data-ttu-id="0d32b-118">ジョブ カテゴリのメンバーシップを変更するには</span><span class="sxs-lookup"><span data-stu-id="0d32b-118">To change the membership of a job category</span></span>  
  
1.  <span data-ttu-id="0d32b-119">**オブジェクト エクスプ ローラー**で、プラス記号をクリックして、ジョブ カテゴリを編集するサーバーを展開します。</span><span class="sxs-lookup"><span data-stu-id="0d32b-119">In **Object Explorer**, click the plus sign to expand the server where you want to edit a job category.</span></span>  
  
2.  <span data-ttu-id="0d32b-120">プラス記号をクリックして **[SQL Server エージェント]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="0d32b-120">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="0d32b-121">**[ジョブ]** フォルダーを右クリックし、 **[ジョブ カテゴリの管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0d32b-121">Right-click the **Jobs** folder and select **Manage Job Categories**.</span></span>  
  
4.  <span data-ttu-id="0d32b-122">**server_name**_]_ ダイアログ ボックスで、編集するジョブ カテゴリを選択し、 **[ジョブの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0d32b-122">In the **Manage Job Categories**_server_name_ dialog box, select the job category that you want to edit, and then click **View Jobs**.</span></span>  
  
5.  <span data-ttu-id="0d32b-123">**[すべてのジョブを表示]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="0d32b-123">Select the **Show all jobs** check box.</span></span>  
  
6.  <span data-ttu-id="0d32b-124">カテゴリにジョブを追加するには、メイン グリッドで、ジョブに対応する **[選択]** 列のチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="0d32b-124">To add a job to the category, in the main grid, select the check box in the **Select** column corresponding to the job.</span></span> <span data-ttu-id="0d32b-125">カテゴリからジョブを削除するには、チェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="0d32b-125">To remove a job from the category, clear the box.</span></span> <span data-ttu-id="0d32b-126">完了したら、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0d32b-126">When finished, click **OK**.</span></span>  
  
7.  <span data-ttu-id="0d32b-127">[**ジョブカテゴリ**の_server_name_の管理] ダイアログボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="0d32b-127">Close the **Manage Job Categories**_server_name_ dialog box.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="0d32b-128">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="0d32b-128">Using Transact-SQL</span></span>  
  
#### <a name="to-change-the-membership-of-a-job-category"></a><span data-ttu-id="0d32b-129">ジョブ カテゴリのメンバーシップを変更するには</span><span class="sxs-lookup"><span data-stu-id="0d32b-129">To change the membership of a job category</span></span>  
  
1.  <span data-ttu-id="0d32b-130">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="0d32b-130">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="0d32b-131">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0d32b-131">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="0d32b-132">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0d32b-132">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```sql
    -- adding a new job category to the "NightlyBackups" job  
    USE msdb ;  
    GO  
    EXEC dbo.sp_update_job  
        @job_name = N'NightlyBackups',  
        @category_name = N'[Uncategorized (Local)]';  
    GO  
    ```  
  
 <span data-ttu-id="0d32b-133">詳細については、「 [sp_update_job &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-update-job-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0d32b-133">For more information, see [sp_update_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-update-job-transact-sql).</span></span>  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="0d32b-134">SQL Server 管理オブジェクトの使用</span><span class="sxs-lookup"><span data-stu-id="0d32b-134">Using SQL Server Management Objects</span></span>  
 <span data-ttu-id="0d32b-135">**ジョブ カテゴリのメンバーシップを変更するには**</span><span class="sxs-lookup"><span data-stu-id="0d32b-135">**To change the membership of a job category**</span></span>  
  
 <span data-ttu-id="0d32b-136">`JobCategory`Visual Basic、Visual C#、PowerShell など、選択したプログラミング言語でクラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="0d32b-136">Use the `JobCategory` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span>  
