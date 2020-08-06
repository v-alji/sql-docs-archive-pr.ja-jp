---
title: ジョブの利用状況の表示 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- viewing job activity
- jobs [SQL Server Agent], viewing
- SQL Server Agent jobs, viewing
- displaying job activity
ms.assetid: 5c284e5e-7775-435d-ac49-f3f12a27ddc7
author: stevestein
ms.author: sstein
ms.openlocfilehash: 56b159952c83ed243c4c5d8012c76e5a2a248519
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741545"
---
# <a name="view-job-activity"></a><span data-ttu-id="d5611-102">[ジョブの利用状況の表示]</span><span class="sxs-lookup"><span data-stu-id="d5611-102">View Job Activity</span></span>
  <span data-ttu-id="d5611-103">このトピックでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] または [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] を使用して、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] で [!INCLUDE[tsql](../../includes/tsql-md.md)]エージェント ジョブの実行状態を表示する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="d5611-103">This topic describes how to view the runtime state of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="d5611-104">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービスが開始されるときに、新しいセッションが作成され、すべての既存の定義済みジョブが **msdb** データベースの **sysjobactivity** テーブルに設定されます。</span><span class="sxs-lookup"><span data-stu-id="d5611-104">When the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service starts, a new session is created and the **sysjobactivity** table in the **msdb** database is populated with all the existing defined jobs.</span></span> <span data-ttu-id="d5611-105">このテーブルには、現在のジョブの利用状況と状態が記録されます。</span><span class="sxs-lookup"><span data-stu-id="d5611-105">This table records current job activity and status.</span></span> <span data-ttu-id="d5611-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのジョブの利用状況モニターを使用すると、ジョブの現在状態を表示できます。</span><span class="sxs-lookup"><span data-stu-id="d5611-106">You can use the Job Activity Monitor in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to view the current state of jobs.</span></span> <span data-ttu-id="d5611-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービスが予期せず終了した場合は、 **sysjobactivity** テーブルを参照して、サービスが終了したときにどのジョブが実行されていたかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="d5611-107">If the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service unexpectedly terminates, you can refer to the **sysjobactivity** table to see which jobs were being executed when the service terminated.</span></span>  
  
 <span data-ttu-id="d5611-108">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="d5611-108">**In This Topic**</span></span>  
  
-   <span data-ttu-id="d5611-109">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="d5611-109">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="d5611-110">Security</span><span class="sxs-lookup"><span data-stu-id="d5611-110">Security</span></span>](#Security)  
  
-   <span data-ttu-id="d5611-111">**ジョブの利用状況を表示する方法:**</span><span class="sxs-lookup"><span data-stu-id="d5611-111">**To view job activity, using:**</span></span>  
  
     [<span data-ttu-id="d5611-112">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="d5611-112">SQL Server Management Studio</span></span>](#SSMS)  
  
     [<span data-ttu-id="d5611-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="d5611-113">Transact-SQL</span></span>](#TSQL)  
  
## <a name="before-you-begin"></a><span data-ttu-id="d5611-114">はじめに</span><span class="sxs-lookup"><span data-stu-id="d5611-114">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="d5611-115">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="d5611-115">Security</span></span>  
 <span data-ttu-id="d5611-116">詳細については、「 [SQL Server エージェントのセキュリティの実装](implement-sql-server-agent-security.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="d5611-116">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="d5611-117">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="d5611-117">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-job-activity"></a><span data-ttu-id="d5611-118">ジョブの利用状況を表示するには</span><span class="sxs-lookup"><span data-stu-id="d5611-118">To view job activity</span></span>  
  
1.  <span data-ttu-id="d5611-119">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]のインスタンスに接続し、そのインスタンスを展開します。</span><span class="sxs-lookup"><span data-stu-id="d5611-119">In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="d5611-120">**[SQL Server エージェント]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="d5611-120">Expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="d5611-121">[ジョブの**利用状況モニター** ] を右クリックし、[**ジョブの利用状況の表示**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d5611-121">Right-click **Job Activity Monitor** and click **View Job Activity**.</span></span>  
  
4.  <span data-ttu-id="d5611-122">このサーバーに対して定義された各ジョブに関する詳細が、 **[ジョブの利用状況モニター]** に表示されます。</span><span class="sxs-lookup"><span data-stu-id="d5611-122">In the **Job Activity Monitor**, you can view details about each job that is defined for this server.</span></span>  
  
5.  <span data-ttu-id="d5611-123">ジョブの開始、ジョブの停止、ジョブの有効化や無効化、ジョブの利用状況モニターに表示されている状態の最新の情報への更新、ジョブの削除、ジョブの履歴やプロパティの表示などの操作を行うには、ジョブを右クリックします。</span><span class="sxs-lookup"><span data-stu-id="d5611-123">Right-click a job to start it, stop it, enable or disable it, refresh its status as displayed in the Job Activity Monitor, delete it, or view its history or properties.</span></span>  <span data-ttu-id="d5611-124">複数のジョブの開始、停止、有効化や無効化、または最新の情報への更新には、ジョブの利用状況モニターで複数の行を選択し、選択項目を右クリックします。</span><span class="sxs-lookup"><span data-stu-id="d5611-124">To start, stop, enable or disable, or refresh multiple jobs, select multiple rows in the Job Activity Monitor, and right-click your selection.</span></span>  
  
6.  <span data-ttu-id="d5611-125">ジョブの利用状況モニターを更新するには、 **[更新]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d5611-125">To update the Job Activity Monitor, click **Refresh**.</span></span> <span data-ttu-id="d5611-126">表示される行を少なくするには、 **[フィルター]** をクリックし、フィルターのパラメーターを入力します。</span><span class="sxs-lookup"><span data-stu-id="d5611-126">To view fewer rows, click **Filter** and enter filter parameters.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="d5611-127">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="d5611-127">Using Transact-SQL</span></span>  
  
#### <a name="to-view-job-activity"></a><span data-ttu-id="d5611-128">ジョブの利用状況を表示するには</span><span class="sxs-lookup"><span data-stu-id="d5611-128">To view job activity</span></span>  
  
1.  <span data-ttu-id="d5611-129">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="d5611-129">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="d5611-130">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d5611-130">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="d5611-131">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d5611-131">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- lists activity for all jobs that the current user has permission to view.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_help_jobactivity ;  
    GO  
    ```  
  
 <span data-ttu-id="d5611-132">詳細については、「 [sp_help_jobactivity &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-help-jobactivity-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d5611-132">For more information, see [sp_help_jobactivity &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-jobactivity-transact-sql).</span></span>  
  
  
