---
title: ジョブの表示 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], viewing
- viewing jobs
- SQL Server Agent jobs, viewing
- displaying jobs
ms.assetid: d2241a3f-dbcf-433c-b7bc-f96bdf0eac8c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 26406aaf2ba0ac4809eb7ac2c84799469d0468d4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645982"
---
# <a name="view-a-job"></a><span data-ttu-id="f5c62-102">View a Job</span><span class="sxs-lookup"><span data-stu-id="f5c62-102">View a Job</span></span>
  <span data-ttu-id="f5c62-103">このトピック [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] は、またはを使用して、でエージェントジョブを表示する方法について説明し [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="f5c62-103">This topic describes how to view [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="f5c62-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="f5c62-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="f5c62-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="f5c62-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="f5c62-106">Security</span><span class="sxs-lookup"><span data-stu-id="f5c62-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="f5c62-107">**ジョブを表示する方法:**</span><span class="sxs-lookup"><span data-stu-id="f5c62-107">**To view a job, using:**</span></span>  
  
     [<span data-ttu-id="f5c62-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="f5c62-108">SQL Server Management Studio</span></span>](#SSMS)  
  
     [<span data-ttu-id="f5c62-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="f5c62-109">Transact-SQL</span></span>](#TSQL)  
  
     [<span data-ttu-id="f5c62-110">SQL Server 管理オブジェクト</span><span class="sxs-lookup"><span data-stu-id="f5c62-110">SQL Server Management Objects</span></span>](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="f5c62-111">はじめに</span><span class="sxs-lookup"><span data-stu-id="f5c62-111">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="f5c62-112">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="f5c62-112">Security</span></span>  
 <span data-ttu-id="f5c62-113">**sysadmin** 固定サーバー ロールのメンバー以外は、所有するジョブしか表示できません。</span><span class="sxs-lookup"><span data-stu-id="f5c62-113">You can only view jobs that you own, unless you are a member of the **sysadmin** fixed server role.</span></span> <span data-ttu-id="f5c62-114">このロールのメンバーは、すべてのジョブを表示できます。</span><span class="sxs-lookup"><span data-stu-id="f5c62-114">Members of this role can view all jobs.</span></span> <span data-ttu-id="f5c62-115">詳細については、「 [SQL Server エージェントのセキュリティの実装](implement-sql-server-agent-security.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f5c62-115">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="f5c62-116">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="f5c62-116">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-a-job"></a><span data-ttu-id="f5c62-117">ジョブを表示するには</span><span class="sxs-lookup"><span data-stu-id="f5c62-117">To view a job</span></span>  
  
1.  <span data-ttu-id="f5c62-118">**オブジェクトエクスプローラー**で、のインスタンスに接続し、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] そのインスタンスを展開します。</span><span class="sxs-lookup"><span data-stu-id="f5c62-118">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="f5c62-119">**[SQL Server エージェント]** を展開し、 **[ジョブ]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="f5c62-119">Expand **SQL Server Agent**, and then expand **Jobs**.</span></span>  
  
3.  <span data-ttu-id="f5c62-120">ジョブを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f5c62-120">Right-click a job, and then click **Properties**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="f5c62-121">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="f5c62-121">Using Transact-SQL</span></span>  
  
#### <a name="to-view-a-job"></a><span data-ttu-id="f5c62-122">ジョブを表示するには</span><span class="sxs-lookup"><span data-stu-id="f5c62-122">To view a job</span></span>  
  
1.  <span data-ttu-id="f5c62-123">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="f5c62-123">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="f5c62-124">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f5c62-124">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="f5c62-125">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f5c62-125">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```sql
    -- lists all aspects of the information for the job NightlyBackups.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_help_job  
        @job_name = N'NightlyBackups',  
        @job_aspect = N'ALL' ;  
    GO  
    ```  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="f5c62-126">SQL Server 管理オブジェクトの使用</span><span class="sxs-lookup"><span data-stu-id="f5c62-126">Using SQL Server Management Objects</span></span>  
 <span data-ttu-id="f5c62-127">**ジョブを表示するには**</span><span class="sxs-lookup"><span data-stu-id="f5c62-127">**To view a job**</span></span>  
  
 <span data-ttu-id="f5c62-128">`Job`Visual Basic、Visual C#、PowerShell など、選択したプログラミング言語でクラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="f5c62-128">Use the `Job` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span> <span data-ttu-id="f5c62-129">詳細については、「 [SQL Server 管理オブジェクト (SMO) プログラミング ガイド](https://msdn.microsoft.com/library/ms162169.aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f5c62-129">For more information, see [SQL Server Management Objects (SMO)](https://msdn.microsoft.com/library/ms162169.aspx).</span></span>  
