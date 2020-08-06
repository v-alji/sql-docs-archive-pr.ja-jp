---
title: ジョブの表示または変更 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], modifying
- jobs [SQL Server Agent], viewing
- modifying jobs
- viewing jobs
- SQL Server Agent jobs, viewing
- SQL Server Agent jobs, modifying
- displaying jobs
ms.assetid: 57f649b8-190c-4304-abd7-7ca5297deab7
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5d0d731d25c20597be3ac84adfacd8973e4a51cd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714981"
---
# <a name="view-or-modify-jobs"></a><span data-ttu-id="59db0-102">ジョブの表示または変更</span><span class="sxs-lookup"><span data-stu-id="59db0-102">View or Modify Jobs</span></span>
  <span data-ttu-id="59db0-103">作成したジョブはどのジョブでも表示できます。</span><span class="sxs-lookup"><span data-stu-id="59db0-103">You can view any job you have created.</span></span> <span data-ttu-id="59db0-104">ジョブの実行後は、履歴を表示することもできます。</span><span class="sxs-lookup"><span data-stu-id="59db0-104">After you have run a job, you can also view its history.</span></span> <span data-ttu-id="59db0-105">ジョブの履歴を表示すると、ジョブを実行した時間、ジョブ全体のステータス、およびジョブを構成するジョブ ステップごとのステータスを確認できます。</span><span class="sxs-lookup"><span data-stu-id="59db0-105">Viewing a job's history allows you to see when the job ran, the status of the job as a whole, and the status of each job step in the job.</span></span> <span data-ttu-id="59db0-106">これまでにジョブが失敗したことがあるかどうか、最後にジョブが正常に実行されたのはいつか、各ジョブの実行でジョブにより作成された出力はどのようなものかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="59db0-106">You can see whether the job ever failed in the past, when the job last completed successfully, and what output the job created each time the job ran.</span></span> <span data-ttu-id="59db0-107">**sysadmin** 固定サーバー ロールのメンバーは、ジョブの所有者がだれであるかにかかわらず、すべてのジョブを表示または変更できます。</span><span class="sxs-lookup"><span data-stu-id="59db0-107">Members of the **sysadmin** fixed server role can view or modify any job, regardless of the owner.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="59db0-108">一度も実行されていないジョブには、ジョブ履歴はありません。</span><span class="sxs-lookup"><span data-stu-id="59db0-108">A job must have been executed at least one time for there to be a job history.</span></span> <span data-ttu-id="59db0-109">ジョブ履歴ログ全体のサイズとジョブごとのサイズは制限できます。</span><span class="sxs-lookup"><span data-stu-id="59db0-109">You can limit the total size of the job history log and the size per job.</span></span>  
  
 <span data-ttu-id="59db0-110">また、新たな要件に合わせて、ジョブは変更できます。</span><span class="sxs-lookup"><span data-stu-id="59db0-110">Finally, you can modify a job to meet new requirements.</span></span> <span data-ttu-id="59db0-111">次の項目を変更できます。</span><span class="sxs-lookup"><span data-stu-id="59db0-111">You can modify:</span></span>  
  
-   <span data-ttu-id="59db0-112">応答オプション</span><span class="sxs-lookup"><span data-stu-id="59db0-112">Response options</span></span>  
  
-   <span data-ttu-id="59db0-113">スケジュール</span><span class="sxs-lookup"><span data-stu-id="59db0-113">Schedules</span></span>  
  
-   <span data-ttu-id="59db0-114">ジョブ ステップ</span><span class="sxs-lookup"><span data-stu-id="59db0-114">Job steps</span></span>  
  
-   <span data-ttu-id="59db0-115">所有権</span><span class="sxs-lookup"><span data-stu-id="59db0-115">Ownership</span></span>  
  
-   <span data-ttu-id="59db0-116">ジョブ カテゴリ</span><span class="sxs-lookup"><span data-stu-id="59db0-116">Job category</span></span>  
  
-   <span data-ttu-id="59db0-117">ターゲット サーバー (マルチサーバー ジョブの場合のみ)</span><span class="sxs-lookup"><span data-stu-id="59db0-117">Target servers (multiserver jobs only)</span></span>  
  
 <span data-ttu-id="59db0-118">マルチサーバー ジョブに対する変更を確実に有効にするには、ターゲット サーバーが更新されたジョブをダウンロードできるように、変更をダウンロード一覧に適用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="59db0-118">To make sure that changes to multiserver jobs take effect, you must post the changes to the download list so that target servers can download the updated job.</span></span> <span data-ttu-id="59db0-119">ターゲット サーバーが最新のジョブ定義を保持するようにするには、マルチサーバー ジョブの更新後に、次のような INSERT 命令を通知します。</span><span class="sxs-lookup"><span data-stu-id="59db0-119">To ensure that target servers have the most current job definitions, post an INSERT instruction after you update the multiserver job as follows:</span></span>  
  
```  
EXECUTE sp_post_msx_operation 'INSERT', 'JOB', '<job id>'  
```  
  
 <span data-ttu-id="59db0-120">詳細については、「 [sp_purge_jobhistory &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-purge-jobhistory-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="59db0-120">For more information, see [sp_purge_jobhistory &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-purge-jobhistory-transact-sql).</span></span>  
  
 <span data-ttu-id="59db0-121">**sysadmin** 固定サーバー ロールのメンバーは、あらゆるジョブに対して、ジョブの定義や履歴を表示したり、ジョブを変更したりできます。</span><span class="sxs-lookup"><span data-stu-id="59db0-121">Members of the **sysadmin** fixed server role can view the definition or history of any job, and can modify any job.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="59db0-122">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="59db0-122">Related Tasks</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="59db0-123">**説明**</span><span class="sxs-lookup"><span data-stu-id="59db0-123">**Description**</span></span>|<span data-ttu-id="59db0-124">**トピック**</span><span class="sxs-lookup"><span data-stu-id="59db0-124">**Topic**</span></span>|  
|<span data-ttu-id="59db0-125">[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] エージェント ジョブを表示する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="59db0-125">Describes how to view [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent jobs.</span></span>|[<span data-ttu-id="59db0-126">View a Job</span><span class="sxs-lookup"><span data-stu-id="59db0-126">View a Job</span></span>](view-a-job.md)|  
|<span data-ttu-id="59db0-127">[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] エージェントのジョブ履歴ログを表示する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="59db0-127">Describes how to view the [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent job history log.</span></span>|[<span data-ttu-id="59db0-128">ジョブ履歴を表示する</span><span class="sxs-lookup"><span data-stu-id="59db0-128">View the Job History</span></span>](view-the-job-history.md)|  
|<span data-ttu-id="59db0-129">[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] エージェントのジョブ履歴ログの内容を削除する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="59db0-129">Describes how to delete the contents of the [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent job history log.</span></span>|[<span data-ttu-id="59db0-130">Clear the Job History Log</span><span class="sxs-lookup"><span data-stu-id="59db0-130">Clear the Job History Log</span></span>](clear-the-job-history-log.md)|  
|<span data-ttu-id="59db0-131">[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] エージェントのジョブ履歴ログのサイズ制限を設定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="59db0-131">Describes how to set size limits for [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent job history logs.</span></span>|[<span data-ttu-id="59db0-132">Resize the Job History Log</span><span class="sxs-lookup"><span data-stu-id="59db0-132">Resize the Job History Log</span></span>](resize-the-job-history-log.md)|  
|<span data-ttu-id="59db0-133">[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のエージェント ジョブのプロパティを変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="59db0-133">Describes how to change the properties of [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent jobs.</span></span>|[<span data-ttu-id="59db0-134">Modify a Job</span><span class="sxs-lookup"><span data-stu-id="59db0-134">Modify a Job</span></span>](modify-a-job.md)|  
  
## <a name="see-also"></a><span data-ttu-id="59db0-135">参照</span><span class="sxs-lookup"><span data-stu-id="59db0-135">See Also</span></span>  
 [<span data-ttu-id="59db0-136">dbo.sysjobhistory &#40;Transact-sql&#41;</span><span class="sxs-lookup"><span data-stu-id="59db0-136">dbo.sysjobhistory &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-tables/dbo-sysjobhistory-transact-sql)  
  
  
