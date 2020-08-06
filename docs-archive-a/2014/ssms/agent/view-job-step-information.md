---
title: ジョブ ステップ情報の表示 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- displaying job step information
- jobs [SQL Server Agent], viewing
- SQL Server Agent jobs, viewing
- viewing job step information
ms.assetid: e3f06492-dc86-4e06-b186-ea58aff6d591
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5d9fc6a006884bc564b5db2bfa8b168c8ae59149
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630791"
---
# <a name="view-job-step-information"></a><span data-ttu-id="9404c-102">View Job Step Information</span><span class="sxs-lookup"><span data-stu-id="9404c-102">View Job Step Information</span></span>
  <span data-ttu-id="9404c-103">このトピックでは、[ジョブ ステップのプロパティ] ダイアログ ボックスにジョブ ステップの詳細を表示する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9404c-103">This topic describes how to view job step details in the Job Step Properties dialog.</span></span> <span data-ttu-id="9404c-104">さらに、ジョブ ステップの出力の表示についても説明します。</span><span class="sxs-lookup"><span data-stu-id="9404c-104">It also includes information about viewing job step output.</span></span>  
  
-   <span data-ttu-id="9404c-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="9404c-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="9404c-106">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="9404c-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="9404c-107">Security</span><span class="sxs-lookup"><span data-stu-id="9404c-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="9404c-108">**ジョブ ステップの情報を表示する方法:**</span><span class="sxs-lookup"><span data-stu-id="9404c-108">**To view job step information, using:**</span></span>  
  
     [<span data-ttu-id="9404c-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="9404c-109">SQL Server Management Studio</span></span>](#SSMS)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="9404c-110">はじめに</span><span class="sxs-lookup"><span data-stu-id="9404c-110">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="9404c-111">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="9404c-111">Limitations and Restrictions</span></span>  
 <span data-ttu-id="9404c-112">テーブルまたはファイルに出力を書き込むようにジョブ ステップが構成され、ジョブが 1 回でも実行されている場合は、 **[ジョブ ステップのプロパティ]** ダイアログ ボックスの **[詳細設定]** ページでジョブ ステップの出力を表示できます。</span><span class="sxs-lookup"><span data-stu-id="9404c-112">If the job step has been configured to write its output to a table or file and the job has run at least once, you can view its output on the **Advanced** page of the **Job Step Properties** dialog.</span></span> <span data-ttu-id="9404c-113">ジョブまたはジョブ ステップが削除されると、出力ログは自動的に削除されます。</span><span class="sxs-lookup"><span data-stu-id="9404c-113">When a job or job step is deleted, the output log is automatically deleted.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="9404c-114">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="9404c-114">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="9404c-115">Permissions</span><span class="sxs-lookup"><span data-stu-id="9404c-115">Permissions</span></span>  
 <span data-ttu-id="9404c-116">**sysadmin** 固定サーバー ロールのメンバー以外は、所有するジョブしか表示できません。</span><span class="sxs-lookup"><span data-stu-id="9404c-116">You can view only those jobs that you own, unless you are a member of the **sysadmin** fixed server role.</span></span> <span data-ttu-id="9404c-117">このロールのメンバーは、すべてのジョブとジョブ ステップの詳細を表示できます。</span><span class="sxs-lookup"><span data-stu-id="9404c-117">Members of this role can view all jobs and job step details.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="9404c-118">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="9404c-118">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-job-step-information"></a><span data-ttu-id="9404c-119">ジョブ ステップの情報を表示するには</span><span class="sxs-lookup"><span data-stu-id="9404c-119">To view job step information</span></span>  
  
1.  <span data-ttu-id="9404c-120">**オブジェクトエクスプローラー**で、のインスタンスに接続し、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] そのインスタンスを展開します。</span><span class="sxs-lookup"><span data-stu-id="9404c-120">In **Object Explorer,** connect to an instance of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="9404c-121">**[SQL Server エージェント]**、 **[ジョブ]** の順に展開し、表示するジョブ ステップが含まれているジョブを右クリックします。次に、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9404c-121">Expand **SQL Server Agent**, expand **Jobs**, right-click the job that contains the job step to be viewed, and click **Properties**.</span></span>  
  
3.  <span data-ttu-id="9404c-122">**[ジョブのプロパティ]** ダイアログ ボックスで、 **[ステップ]** ページをクリックします。</span><span class="sxs-lookup"><span data-stu-id="9404c-122">In the **Job Properties** dialog, click the **Steps** page.</span></span>  
  
4.  <span data-ttu-id="9404c-123">表示するジョブ ステップをクリックし、 **[編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9404c-123">Click the job step to be viewed, and click **Edit**.</span></span>  
  
5.  <span data-ttu-id="9404c-124">**[ジョブ ステップのプロパティ]** ダイアログ ボックスの **[全般]** ページで、ジョブ ステップの種類や説明を表示できます。</span><span class="sxs-lookup"><span data-stu-id="9404c-124">On the **General** page of the **Job Step Properties** dialog, you can view the type of job step and what it does.</span></span>  
  
6.  <span data-ttu-id="9404c-125">**[詳細設定]** ページをクリックすると、ジョブ ステップが正常終了または異常終了した場合に、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントによって行われる操作、ジョブ ステップの試行回数、ジョブ ステップの出力の書き込み先、およびジョブ ステップを実行するユーザーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="9404c-125">Click the **Advanced** page to view the actions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent takes if the job step succeeds or fails, how many times the job step should be attempted, where the job step output is written, and the user the job step runs as.</span></span>  
  
#### <a name="to-view-job-step-output"></a><span data-ttu-id="9404c-126">ジョブ ステップの出力を表示するには</span><span class="sxs-lookup"><span data-stu-id="9404c-126">To view job step output</span></span>  
  
1.  <span data-ttu-id="9404c-127">**[ジョブ ステップのプロパティ]** ダイアログ ボックスで、 **[詳細設定]** ページをクリックします。</span><span class="sxs-lookup"><span data-stu-id="9404c-127">In the **Job Step Properties** dialog, click the **Advanced** page.</span></span>  
  
2.  <span data-ttu-id="9404c-128">接続している [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のバージョンに応じて、ジョブ ステップの出力ファイルまたは出力テーブルのいずれかを次のように表示できます。</span><span class="sxs-lookup"><span data-stu-id="9404c-128">Depending on the version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] you are connected to, you can view either the job step output file or table as follows:</span></span>  
  
    -   <span data-ttu-id="9404c-129">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 以降に接続しているときは、 **[テーブルにログ記録する]** チェック ボックスがオンになっている場合のみ **[表示]** をクリックできます。</span><span class="sxs-lookup"><span data-stu-id="9404c-129">When you are connected to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or later, you can click **View** only when **Log to table** is checked.</span></span> <span data-ttu-id="9404c-130">この場合、 **msdb** データベースの **sysjobstepslogs** テーブルにジョブ ステップの出力が書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="9404c-130">In this case, the job step output is written to the **sysjobstepslogs** table in the **msdb** database.</span></span>  
  
    -   <span data-ttu-id="9404c-131">ジョブ ステップの出力がファイルに書き込まれるときは **[表示]** ボタンが無効になります。</span><span class="sxs-lookup"><span data-stu-id="9404c-131">The **View** button is disabled when job step output is written to a file.</span></span> <span data-ttu-id="9404c-132">ジョブ ステップの出力ファイルを表示するには、メモ帳を使用します。</span><span class="sxs-lookup"><span data-stu-id="9404c-132">To view a job step output file, use Notepad.</span></span>  
  
  
