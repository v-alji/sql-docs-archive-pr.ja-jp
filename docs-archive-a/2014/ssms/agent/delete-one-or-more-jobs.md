---
title: 1 つまたは複数のジョブの削除 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, deleting
- dropping jobs
- jobs [SQL Server Agent], deleting
- deleting jobs
- removing jobs
ms.assetid: 67dcdad0-57b2-431c-b77f-4ffc926af93d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 436625f9ad629a6b0e574aa046059f4e7e9c2bf2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632270"
---
# <a name="delete-one-or-more-jobs"></a><span data-ttu-id="96447-102">1 つまたは複数のジョブの削除</span><span class="sxs-lookup"><span data-stu-id="96447-102">Delete One or More Jobs</span></span>
  <span data-ttu-id="96447-103">このトピック [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 、で、、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または SQL Server 管理オブジェクトを使用して、エージェントジョブを削除する方法について説明し [!INCLUDE[tsql](../../includes/tsql-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="96447-103">This topic describes how to delete [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or SQL Server Management Objects.</span></span>  
  
 
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="96447-104">はじめに</span><span class="sxs-lookup"><span data-stu-id="96447-104">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="96447-105">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="96447-105">Security</span></span>  
 <span data-ttu-id="96447-106">**sysadmin** 固定サーバー ロールのメンバー以外は、所有しているジョブしか削除できません。</span><span class="sxs-lookup"><span data-stu-id="96447-106">Unless you are a member of the **sysadmin** fixed server role, you can only delete jobs that you own.</span></span>  
  
 
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="96447-107">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="96447-107">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-delete-a-job"></a><span data-ttu-id="96447-108">ジョブを削除するには</span><span class="sxs-lookup"><span data-stu-id="96447-108">To delete a job</span></span>  
  
1.  <span data-ttu-id="96447-109">**オブジェクトエクスプローラー**で、のインスタンスに接続し、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] そのインスタンスを展開します。</span><span class="sxs-lookup"><span data-stu-id="96447-109">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="96447-110">**[SQL Server エージェント]** を展開し、 **[ジョブ]** を展開します。次に、削除するジョブを右クリックして、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="96447-110">Expand **SQL Server Agent**, expand **Jobs**, right-click the job you want to delete, and then click **Delete**.</span></span>  
  
3.  <span data-ttu-id="96447-111">**[オブジェクトの削除]** ダイアログ ボックスで、削除するジョブが選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="96447-111">In the **Delete Object** dialog box, confirm that the job you intend to delete is selected.</span></span>  
  
4.  <span data-ttu-id="96447-112">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="96447-112">Click **OK**.</span></span>  
  
#### <a name="to-delete-multiple-jobs"></a><span data-ttu-id="96447-113">複数のジョブを削除するには</span><span class="sxs-lookup"><span data-stu-id="96447-113">To delete multiple jobs</span></span>  
  
1.  <span data-ttu-id="96447-114">**オブジェクトエクスプローラー**で、のインスタンスに接続し、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] そのインスタンスを展開します。</span><span class="sxs-lookup"><span data-stu-id="96447-114">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="96447-115">**[SQL Server エージェント]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="96447-115">Expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="96447-116">**[ジョブの利用状況モニター]** を右クリックし、 **[ジョブの利用状況の表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="96447-116">Right-click **Job Activity Monitor**, and click **View Job Activity**.</span></span>  
  
4.  <span data-ttu-id="96447-117">ジョブの利用状況モニターで、削除する複数のジョブを選択します。次に、選択したジョブを右クリックして、 **[ジョブの削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="96447-117">In the Job Activity Monitor, select the jobs you want to delete, right-click your selection, and choose **Delete jobs**.</span></span>  
  

  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="96447-118">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="96447-118">Using Transact-SQL</span></span>  
  
#### <a name="to-delete-a-job"></a><span data-ttu-id="96447-119">ジョブを削除するには</span><span class="sxs-lookup"><span data-stu-id="96447-119">To delete a job</span></span>  
  
1.  <span data-ttu-id="96447-120">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="96447-120">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="96447-121">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="96447-121">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="96447-122">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="96447-122">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```sql
    USE msdb ;  
    GO  
  
    EXEC sp_delete_job  
        @job_name = N'NightlyBackups' ;  
    GO  
    ```  
  
 <span data-ttu-id="96447-123">詳細については、「 [sp_delete_job &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-job-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="96447-123">For more information, see [sp_delete_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-job-transact-sql).</span></span>  

##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="96447-124">SQL Server 管理オブジェクトの使用</span><span class="sxs-lookup"><span data-stu-id="96447-124">Using SQL Server Management Objects</span></span>  

### <a name="to-delete-multiple-jobs"></a><span data-ttu-id="96447-125">複数のジョブを削除するには</span><span class="sxs-lookup"><span data-stu-id="96447-125">To delete multiple jobs</span></span>
  
 <span data-ttu-id="96447-126">`JobCollection`Visual Basic、Visual C#、PowerShell など、選択したプログラミング言語でクラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="96447-126">Use the `JobCollection` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span> <span data-ttu-id="96447-127">詳細については、「 [SQL Server 管理オブジェクト (SMO) プログラミング ガイド](https://msdn.microsoft.com/library/ms162169.aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="96447-127">For more information, see [SQL Server Management Objects (SMO)](https://msdn.microsoft.com/library/ms162169.aspx).</span></span>  
