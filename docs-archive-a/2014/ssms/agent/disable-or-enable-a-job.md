---
title: ジョブの有効化または無効化 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- stopping jobs
- disabling jobs
- SQL Server Agent jobs, disabling
- jobs [SQL Server Agent], disabling
ms.assetid: 5041261f-0c32-4d4a-8bee-59a6c16200dd
author: stevestein
ms.author: sstein
ms.openlocfilehash: 42fe7cbeed1e2ff3f93b1afef52b165a7d660ddd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631479"
---
# <a name="disable-or-enable-a-job"></a><span data-ttu-id="3ff2c-102">Disable or Enable a Job</span><span class="sxs-lookup"><span data-stu-id="3ff2c-102">Disable or Enable a Job</span></span>
  <span data-ttu-id="3ff2c-103">このトピックでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] または [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] を使用して、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] で [!INCLUDE[tsql](../../includes/tsql-md.md)]エージェント ジョブを無効にする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="3ff2c-103">This topic describes how to disable a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="3ff2c-104">ジョブを無効にしても、ジョブは削除されるわけではなく、必要に応じて再び有効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="3ff2c-104">When you disable a job, it is not deleted and can be enabled again when necessary.</span></span>  
  
 <span data-ttu-id="3ff2c-105">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="3ff2c-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="3ff2c-106">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="3ff2c-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="3ff2c-107">Security</span><span class="sxs-lookup"><span data-stu-id="3ff2c-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="3ff2c-108">**ジョブを無効または有効にする方法:**</span><span class="sxs-lookup"><span data-stu-id="3ff2c-108">**To disable or enable a job, using:**</span></span>  
  
     [<span data-ttu-id="3ff2c-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="3ff2c-109">SQL Server Management Studio</span></span>](#SSMS)  
  
     [<span data-ttu-id="3ff2c-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="3ff2c-110">Transact-SQL</span></span>](#TSQL)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="3ff2c-111">はじめに</span><span class="sxs-lookup"><span data-stu-id="3ff2c-111">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="3ff2c-112">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="3ff2c-112">Security</span></span>  
 <span data-ttu-id="3ff2c-113">詳細については、「 [SQL Server エージェントのセキュリティの実装](implement-sql-server-agent-security.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="3ff2c-113">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="3ff2c-114">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="3ff2c-114">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-disable-or-enable-a-job"></a><span data-ttu-id="3ff2c-115">ジョブを無効または有効にするには</span><span class="sxs-lookup"><span data-stu-id="3ff2c-115">To disable or enable a job</span></span>  
  
1.  <span data-ttu-id="3ff2c-116">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]のインスタンスに接続し、そのインスタンスを展開します。</span><span class="sxs-lookup"><span data-stu-id="3ff2c-116">In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="3ff2c-117">**[SQL Server エージェント]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="3ff2c-117">Expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="3ff2c-118">**[ジョブ]** を展開し、無効または有効にするジョブを右クリックします。</span><span class="sxs-lookup"><span data-stu-id="3ff2c-118">Expand **Jobs**, and then right-click the job that you want to disable or enable.</span></span>  
  
4.  <span data-ttu-id="3ff2c-119">ジョブを無効にするには、 **[無効化]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3ff2c-119">To disable a job, click **Disable**.</span></span> <span data-ttu-id="3ff2c-120">ジョブを有効にするには、 **[有効化]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3ff2c-120">To enable a job, click **Enable**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="3ff2c-121">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="3ff2c-121">Using Transact-SQL</span></span>  
  
#### <a name="to-disable-or-enable-a-job"></a><span data-ttu-id="3ff2c-122">ジョブを無効または有効にするには</span><span class="sxs-lookup"><span data-stu-id="3ff2c-122">To disable or enable a job</span></span>  
  
1.  <span data-ttu-id="3ff2c-123">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="3ff2c-123">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="3ff2c-124">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3ff2c-124">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="3ff2c-125">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3ff2c-125">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- changes the name, description, and enables status of the job NightlyBackups.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_update_job  
        @job_name = N'NightlyBackups',  
        @new_name = N'NightlyBackups -- Disabled',  
        @description = N'Nightly backups disabled during server migration.',  
        @enabled = 1 ;  
    GO  
    ```  
  
 <span data-ttu-id="3ff2c-126">詳細については、「 [sp_update_job &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-update-job-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3ff2c-126">For more information, see [sp_update_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-update-job-transact-sql).</span></span>  
  
  
