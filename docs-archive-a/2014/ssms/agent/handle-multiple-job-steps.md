---
title: 複数のジョブ ステップの処理 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- job steps [SQL Server Agent]
- ordering job steps [SQL Server]
- multiple job steps
- SQL Server Agent jobs, job steps
- control of flow for jobs [SQL Server]
ms.assetid: 7aba19ff-72b3-45f6-8e54-23f4988d63a8
author: stevestein
ms.author: sstein
ms.openlocfilehash: fef0fb69b5bfd028977276d8efabc333a21e0feb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631461"
---
# <a name="handle-multiple-job-steps"></a><span data-ttu-id="a18f5-102">複数のジョブ ステップの処理</span><span class="sxs-lookup"><span data-stu-id="a18f5-102">Handle Multiple Job Steps</span></span>
  <span data-ttu-id="a18f5-103">ジョブに複数のジョブ ステップがある場合、ジョブ ステップを実行する順序を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a18f5-103">If your job has more than one job step, you must specify the order in which the job steps run.</span></span> <span data-ttu-id="a18f5-104">この順序指定を*フロー制御*と呼びます。</span><span class="sxs-lookup"><span data-stu-id="a18f5-104">This is called *control of flow\*\*.*</span></span> <span data-ttu-id="a18f5-105">いつでも新しいジョブ ステップを追加して、フローを再構成できます。変更が有効になるのは、次にジョブを実行するときです。</span><span class="sxs-lookup"><span data-stu-id="a18f5-105">You can add new job steps and rearrange the flow of job steps at any time; the changes take effect the next time the job is run.</span></span> <span data-ttu-id="a18f5-106">次の図は、データベース バックアップ ジョブのフロー制御を示しています。</span><span class="sxs-lookup"><span data-stu-id="a18f5-106">This illustration shows the control of flow for a database backup job.</span></span>  
  
 <span data-ttu-id="a18f5-107">![SQL Server エージェントのジョブ ステップのフロー制御](../../database-engine/media/dbflow01.gif "SQL Server エージェントのジョブ ステップのフロー制御")</span><span class="sxs-lookup"><span data-stu-id="a18f5-107">![SQL Server Agent job steps control of flow](../../database-engine/media/dbflow01.gif "SQL Server Agent job steps control of flow")</span></span>  
  
 <span data-ttu-id="a18f5-108">最初のステップは "データベースのバックアップ" です。</span><span class="sxs-lookup"><span data-stu-id="a18f5-108">The first step is Backup Database.</span></span> <span data-ttu-id="a18f5-109">このステップが失敗すると、通知を受け取るオペレーターに [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントから失敗が報告されます。</span><span class="sxs-lookup"><span data-stu-id="a18f5-109">If this step fails, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent reports failure to the operator who is defined to receive notification.</span></span> <span data-ttu-id="a18f5-110">"データベースのバックアップ" ステップに成功すると、次のステップの "顧客データのスクラビング" に進みます。</span><span class="sxs-lookup"><span data-stu-id="a18f5-110">If the Backup Database step succeeds, the job proceeds to the next step, "Scrub" Customer Data.</span></span> <span data-ttu-id="a18f5-111">このステップに失敗すると、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] エージェントにより "データベースの復元" までスキップされます。</span><span class="sxs-lookup"><span data-stu-id="a18f5-111">If this step fails, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent skips forward to Restore Database.</span></span> <span data-ttu-id="a18f5-112">"顧客データのスクラビング" に成功すると、次のステップの "統計の更新" に進みます。以降、最後のステップが "レポート成功" または "レポート失敗" になるまで続きます。</span><span class="sxs-lookup"><span data-stu-id="a18f5-112">If "Scrub" Customer Data succeeds, the job proceeds to the next step, Update Statistics, and so on, until the final step either results in Report Success or Report Failure.</span></span>  
  
 <span data-ttu-id="a18f5-113">各ジョブ ステップの成功と失敗に対して、フロー制御アクションを定義します。</span><span class="sxs-lookup"><span data-stu-id="a18f5-113">You define a control-of-flow action for the success and failure of each job step.</span></span> <span data-ttu-id="a18f5-114">ジョブ ステップが成功した場合のアクション、およびジョブ ステップが失敗した場合のアクションを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a18f5-114">You must specify an action to be taken when a job step succeeds and an action to be taken when a job step fails.</span></span> <span data-ttu-id="a18f5-115">また、失敗したジョブ ステップに対して、再試行の回数とその間隔を定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="a18f5-115">You can also define the number of retry attempts for failed job steps and the interval between the retry attempts.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a18f5-116">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのグラフィカル ユーザー インターフェイス (GUI) を使用し、複数のステップのジョブから 1 つ以上のステップを削除する場合、GUI では、すべてのジョブ ステップを削除してから、修正された成功時または失敗時の参照で、残りのステップを戻します。</span><span class="sxs-lookup"><span data-stu-id="a18f5-116">When you use the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent graphical user interface (GUI) and delete one or more steps from a multistep job, the GUI removes all job steps and then adds the remaining steps back with the correct on-success or on-failure references.</span></span> <span data-ttu-id="a18f5-117">たとえば 5 つのステップのジョブがあり、最初のステップが正常に終了した場合には、ステップ 4 に移動するように構成されているとします。</span><span class="sxs-lookup"><span data-stu-id="a18f5-117">For example, suppose you have a job with five steps, and the first step is configured to jump to step 4 if it completes successfully.</span></span> <span data-ttu-id="a18f5-118">ステップ 3 を削除する場合、GUI ではこのジョブのすべてのステップを削除し、残りの 4 つのステップ (1、2、4、および 5) を修正した参照と共に追加します。</span><span class="sxs-lookup"><span data-stu-id="a18f5-118">If you delete step 3, the GUI removes all steps for this job and adds the remaining four steps (1, 2, 4, and 5) with corrected references.</span></span> <span data-ttu-id="a18f5-119">この場合、ステップ 1 の参照は、ステップ 1 が正常に終了したらステップ 3 に移動するように再構成されます。</span><span class="sxs-lookup"><span data-stu-id="a18f5-119">In this case, the reference in step 1 would be reconfigured to jump to step 3 if step 1 completes successfully.</span></span>  
  
 <span data-ttu-id="a18f5-120">ジョブ ステップは自己完結型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="a18f5-120">Job steps must be self-contained.</span></span> <span data-ttu-id="a18f5-121">つまり、ジョブ ステップ間でブール値、データ、または数値を受け渡すことはできません。</span><span class="sxs-lookup"><span data-stu-id="a18f5-121">That is, a job cannot pass Boolean values, data, or numeric values between job steps.</span></span> <span data-ttu-id="a18f5-122">ただし、パーマネント テーブルまたはグローバル一時テーブルを使用することで、 [!INCLUDE[tsql](../../includes/tsql-md.md)] ジョブ ステップ間で値を受け渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="a18f5-122">You can, however, pass values from one [!INCLUDE[tsql](../../includes/tsql-md.md)] job step to another by using permanent tables or global temporary tables.</span></span> <span data-ttu-id="a18f5-123">実行可能プログラムを実行するジョブ ステップの値をジョブ ステップ間で受け渡すには、ファイルを使用します。</span><span class="sxs-lookup"><span data-stu-id="a18f5-123">You can pass values from job steps that run executable programs from one job step to another job step by using files.</span></span> <span data-ttu-id="a18f5-124">たとえば、あるジョブ ステップで実行される実行可能プログラムでファイルに書き込み、後続のジョブ ステップで実行される実行可能プログラムでそのファイルを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="a18f5-124">For example, the executable run by one job step writes a file, and the executable run by a subsequent job step reads the file.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a18f5-125">ジョブ ステップ 1 の次にジョブ ステップ 2 が続き、ジョブ ステップ 2 の次にジョブ ステップ 1 に戻るような、ループするジョブ ステップを作成した場合は、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でそのジョブを作成したときに警告メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a18f5-125">If you create looping job steps (job step 1 is followed by job step 2, then job step 2 returns to job step 1), a warning message appears when the job is created using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="a18f5-126">エージェントにより、ジョブとジョブ ステップの情報がジョブ履歴に記録されます。</span><span class="sxs-lookup"><span data-stu-id="a18f5-126">Agent records job and job step information in the job history.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a18f5-127">参照</span><span class="sxs-lookup"><span data-stu-id="a18f5-127">See Also</span></span>  
 <span data-ttu-id="a18f5-128">[sp_add_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-job-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a18f5-128">[sp_add_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-job-transact-sql) </span></span>  
 <span data-ttu-id="a18f5-129">[dbo.sysjobhistory &#40;Transact-sql&#41;](/sql/relational-databases/system-tables/dbo-sysjobhistory-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a18f5-129">[dbo.sysjobhistory &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/dbo-sysjobhistory-transact-sql) </span></span>  
 <span data-ttu-id="a18f5-130">[Transact-sql&#41;&#40;ジョブのdbo.sys](/sql/relational-databases/system-tables/dbo-sysjobs-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a18f5-130">[dbo.sysjobs &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/dbo-sysjobs-transact-sql) </span></span>  
 <span data-ttu-id="a18f5-131">[dbo.sysjobsteps &#40;Transact-sql&#41;](/sql/relational-databases/system-tables/dbo-sysjobsteps-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a18f5-131">[dbo.sysjobsteps &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/dbo-sysjobsteps-transact-sql) </span></span>  
 <span data-ttu-id="a18f5-132">[ジョブの実装](implement-jobs.md) </span><span class="sxs-lookup"><span data-stu-id="a18f5-132">[Implement Jobs](implement-jobs.md) </span></span>  
 [<span data-ttu-id="a18f5-133">ジョブ ステップの管理</span><span class="sxs-lookup"><span data-stu-id="a18f5-133">Manage Job Steps</span></span>](manage-job-steps.md)  
  
  
