---
title: ジョブの変更 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], modifying
- modifying jobs
- SQL Server Agent jobs, modifying
ms.assetid: dd5e5f20-20c4-4ab9-a19a-db87577dcd43
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0d25830ad119a1f5f344a4dcf318c35bee5f86ca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634804"
---
# <a name="modify-a-job"></a><span data-ttu-id="a2509-102">Modify a Job</span><span class="sxs-lookup"><span data-stu-id="a2509-102">Modify a Job</span></span>
  <span data-ttu-id="a2509-103">このトピック [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 、で、、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] または SQL Server 管理オブジェクトを使用して、エージェントジョブのプロパティを変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a2509-103">This topic describes how to change the properties of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or SQL Server Management Objects.</span></span>  
  
 <span data-ttu-id="a2509-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="a2509-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="a2509-105">**作業を開始する準備:** 、</span><span class="sxs-lookup"><span data-stu-id="a2509-105">**Before you begin:** ,</span></span>  
  
     [<span data-ttu-id="a2509-106">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="a2509-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="a2509-107">Security</span><span class="sxs-lookup"><span data-stu-id="a2509-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="a2509-108">**ジョブを変更する方法:**</span><span class="sxs-lookup"><span data-stu-id="a2509-108">**To modify a job, using:**</span></span>  
  
     [<span data-ttu-id="a2509-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="a2509-109">SQL Server Management Studio</span></span>](#SSMS)  
  
     [<span data-ttu-id="a2509-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="a2509-110">Transact-SQL</span></span>](#TSQL)  
  
     [<span data-ttu-id="a2509-111">SQL Server 管理オブジェクト</span><span class="sxs-lookup"><span data-stu-id="a2509-111">SQL Server Management Objects</span></span>](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="a2509-112">はじめに</span><span class="sxs-lookup"><span data-stu-id="a2509-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="a2509-113">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="a2509-113">Limitations and Restrictions</span></span>  
 <span data-ttu-id="a2509-114">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのマスター ジョブの対象サーバーを、ローカル サーバーとリモート サーバーの両方に設定することはできません。</span><span class="sxs-lookup"><span data-stu-id="a2509-114">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent master job cannot be targeted at both local and remote servers.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="a2509-115">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="a2509-115">Security</span></span>  
 <span data-ttu-id="a2509-116">**sysadmin** 固定サーバー ロールのメンバー以外は、所有しているジョブしか変更できません。</span><span class="sxs-lookup"><span data-stu-id="a2509-116">Unless you are a member of the **sysadmin** fixed server role, you can only modify jobs that you own.</span></span> <span data-ttu-id="a2509-117">詳細については、「 [SQL Server エージェントのセキュリティの実装](implement-sql-server-agent-security.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a2509-117">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="a2509-118">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="a2509-118">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-modify-a-job"></a><span data-ttu-id="a2509-119">ジョブを変更するには</span><span class="sxs-lookup"><span data-stu-id="a2509-119">To modify a job</span></span>  
  
1.  <span data-ttu-id="a2509-120">**オブジェクトエクスプローラー**で、のインスタンスに接続し、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] そのインスタンスを展開します。</span><span class="sxs-lookup"><span data-stu-id="a2509-120">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="a2509-121">**[SQL Server エージェント]**、 **[ジョブ]** の順に展開し、変更するジョブを右クリックします。次に、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a2509-121">Expand **SQL Server Agent**, expand **Jobs**, right-click the job you want to modify, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="a2509-122">**[ジョブのプロパティ]** ダイアログ ボックスの対応するページを使用して、ジョブのプロパティ、ステップ、スケジュール、警告、および通知を変更します。</span><span class="sxs-lookup"><span data-stu-id="a2509-122">In the **Job Properties** dialog box, update the job's properties, steps, schedule, alerts, and notifications using the corresponding pages.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="a2509-123">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="a2509-123">Using Transact-SQL</span></span>  
  
#### <a name="to-modify-a-job"></a><span data-ttu-id="a2509-124">ジョブを変更するには</span><span class="sxs-lookup"><span data-stu-id="a2509-124">To modify a job</span></span>  
  
1.  <span data-ttu-id="a2509-125">オブジェクト エクスプローラーで、データベース エンジンのインスタンスに接続し、そのインスタンスを展開します。</span><span class="sxs-lookup"><span data-stu-id="a2509-125">In Object Explorer, connect to an instance of the Database Engine, and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="a2509-126">ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a2509-126">On the toolbar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="a2509-127">クエリ ウィンドウで、次のシステム ストアド プロシージャを使用してジョブを変更します。</span><span class="sxs-lookup"><span data-stu-id="a2509-127">In the query window, use the following system stored procedures to modify a job.</span></span>  
  
    -   <span data-ttu-id="a2509-128">[&#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-update-job-transact-sql)を実行 sp_update_job て、ジョブの属性を変更します。</span><span class="sxs-lookup"><span data-stu-id="a2509-128">Execute [sp_update_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-update-job-transact-sql) to change the attributes of a job.</span></span>  
  
    -   <span data-ttu-id="a2509-129">ジョブ定義のスケジューリングの詳細を変更するには[sp_update_schedule &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-update-schedule-transact-sql)を実行します。</span><span class="sxs-lookup"><span data-stu-id="a2509-129">Execute [sp_update_schedule &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-update-schedule-transact-sql) to change the scheduling details for a job definition.</span></span>  
  
    -   <span data-ttu-id="a2509-130">[&#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql)を実行 sp_add_jobstep て、新しいジョブステップを追加します。</span><span class="sxs-lookup"><span data-stu-id="a2509-130">Execute [sp_add_jobstep &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql) to add new job steps.</span></span>  
  
    -   <span data-ttu-id="a2509-131">[&#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-update-jobstep-transact-sql)を実行 sp_update_jobstep て、既存のジョブステップを変更します。</span><span class="sxs-lookup"><span data-stu-id="a2509-131">Execute [sp_update_jobstep &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-update-jobstep-transact-sql) to change pre-existing job steps.</span></span>  
  
    -   <span data-ttu-id="a2509-132">ジョブからジョブステップを削除するには[sp_delete_jobstep &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-jobstep-transact-sql)を実行します。</span><span class="sxs-lookup"><span data-stu-id="a2509-132">Execute [sp_delete_jobstep &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-jobstep-transact-sql) to remove a job step from a job.</span></span>  
  
    -   <span data-ttu-id="a2509-133">任意の SQL Server エージェント マスター ジョブを変更するための追加のストアド プロシージャ:</span><span class="sxs-lookup"><span data-stu-id="a2509-133">Additional stored procedures to modify any SQL Server Agent master job:</span></span>  
  
        -   <span data-ttu-id="a2509-134">[&#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-jobserver-transact-sql)を実行 sp_delete_jobserver て、現在ジョブに関連付けられているサーバーを削除します。</span><span class="sxs-lookup"><span data-stu-id="a2509-134">Execute [sp_delete_jobserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-jobserver-transact-sql) to delete a server currently associated with a job.</span></span>  
  
        -   <span data-ttu-id="a2509-135">[&#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql)を実行 sp_add_jobserver て、サーバーを現在のジョブに関連付けます。</span><span class="sxs-lookup"><span data-stu-id="a2509-135">Execute [sp_add_jobserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql) to associate a server with the current job.</span></span>  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="a2509-136">SQL Server 管理オブジェクトの使用</span><span class="sxs-lookup"><span data-stu-id="a2509-136">Using SQL Server Management Objects</span></span>  
 <span data-ttu-id="a2509-137">**ジョブを変更するには**</span><span class="sxs-lookup"><span data-stu-id="a2509-137">**To modify a job**</span></span>  
  
 <span data-ttu-id="a2509-138">`Job`Visual Basic、Visual C#、PowerShell など、選択したプログラミング言語でクラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="a2509-138">Use the `Job` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span> <span data-ttu-id="a2509-139">詳細については、「 [SQL Server 管理オブジェクト (SMO) プログラミング ガイド](https://msdn.microsoft.com/library/ms162169.aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a2509-139">For more information, see [SQL Server Management Objects (SMO)](https://msdn.microsoft.com/library/ms162169.aspx).</span></span>  
  
  
