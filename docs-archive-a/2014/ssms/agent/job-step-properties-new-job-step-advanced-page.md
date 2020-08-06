---
title: '[ジョブステップのプロパティ]: [新しいジョブステップ] ([詳細設定] ページ)Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.job.stepadvanced.f1
ms.assetid: bdecfd4f-bcd8-4ba2-8ada-fbb636314f40
author: stevestein
ms.author: sstein
ms.openlocfilehash: 42820ffbdbb89261e839b5d1011f3a91b5841c86
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737428"
---
# <a name="job-step-properties-new-job-step-advanced-page"></a><span data-ttu-id="e25bc-102">[ジョブ ステップのプロパティ]:[新しいジョブ ステップ] ([詳細] ページ)</span><span class="sxs-lookup"><span data-stu-id="e25bc-102">Job Step Properties: New Job Step (Advanced Page)</span></span>
  <span data-ttu-id="e25bc-103">このページを使用すると、エージェントジョブステップのプロパティを表示したり、変更したり [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] できます。</span><span class="sxs-lookup"><span data-stu-id="e25bc-103">Use this page to view and change the properties of a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job step.</span></span>  
  
## <a name="options"></a><span data-ttu-id="e25bc-104">Options</span><span class="sxs-lookup"><span data-stu-id="e25bc-104">Options</span></span>  
 <span data-ttu-id="e25bc-105">**[成功した場合のアクション]**</span><span class="sxs-lookup"><span data-stu-id="e25bc-105">**On success action**</span></span>  
 <span data-ttu-id="e25bc-106">ジョブ ステップが成功した場合に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントが実行するアクションを設定します。</span><span class="sxs-lookup"><span data-stu-id="e25bc-106">Sets the action for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to perform if the job step succeeds.</span></span>  
  
 <span data-ttu-id="e25bc-107">**再試行**</span><span class="sxs-lookup"><span data-stu-id="e25bc-107">**Retry attempts**</span></span>  
 <span data-ttu-id="e25bc-108">失敗したジョブ ステップを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントで再試行する回数を設定します。</span><span class="sxs-lookup"><span data-stu-id="e25bc-108">Sets the number of times that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent attempts to retry a failed job step.</span></span>  
  
 <span data-ttu-id="e25bc-109">**[再試行間隔 (分)]**</span><span class="sxs-lookup"><span data-stu-id="e25bc-109">**Retry interval (minutes)**</span></span>  
 <span data-ttu-id="e25bc-110">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントが再試行する間隔を設定します。</span><span class="sxs-lookup"><span data-stu-id="e25bc-110">Sets the amount of time for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to wait between retry attempts.</span></span>  
  
 <span data-ttu-id="e25bc-111">**[失敗した場合のアクション]**</span><span class="sxs-lookup"><span data-stu-id="e25bc-111">**On failure action**</span></span>  
 <span data-ttu-id="e25bc-112">ジョブ ステップが失敗した場合に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントが実行するアクションを設定します。</span><span class="sxs-lookup"><span data-stu-id="e25bc-112">Sets the action for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to perform if the job step fails.</span></span>  
  
## <a name="options-for-transact-sql-job-steps"></a><span data-ttu-id="e25bc-113">Transact-SQL ジョブ ステップのオプション</span><span class="sxs-lookup"><span data-stu-id="e25bc-113">Options for Transact-SQL Job Steps</span></span>  
 <span data-ttu-id="e25bc-114">**[出力ファイル]**</span><span class="sxs-lookup"><span data-stu-id="e25bc-114">**Output file**</span></span>  
 <span data-ttu-id="e25bc-115">ジョブ ステップからの出力に使用するファイルを設定します。</span><span class="sxs-lookup"><span data-stu-id="e25bc-115">Sets the file to use for output from the job step.</span></span> <span data-ttu-id="e25bc-116">このオプションは、 **sysadmin** 固定サーバー ロールのメンバーである場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="e25bc-116">This option is available only to members of the **sysadmin** fixed server role.</span></span>  
  
 <span data-ttu-id="e25bc-117">**...**</span><span class="sxs-lookup"><span data-stu-id="e25bc-117">**...**</span></span>  
 <span data-ttu-id="e25bc-118">ジョブ ステップからの出力に使用するファイルを参照します。</span><span class="sxs-lookup"><span data-stu-id="e25bc-118">Browse to the file to use for output from the job step.</span></span>  
  
 <span data-ttu-id="e25bc-119">**表示**</span><span class="sxs-lookup"><span data-stu-id="e25bc-119">**View**</span></span>  
 <span data-ttu-id="e25bc-120">で [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] は、このボタンを使用して出力ファイルを表示することはできません。</span><span class="sxs-lookup"><span data-stu-id="e25bc-120">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], this button is disabled for viewing output files.</span></span> <span data-ttu-id="e25bc-121">代わりに、メモ帳を使用してジョブ ステップの出力ファイルを表示します。</span><span class="sxs-lookup"><span data-stu-id="e25bc-121">Instead, use Notepad to view job step output files.</span></span>  
  
 <span data-ttu-id="e25bc-122">**[既存のファイルに出力を追加する]**</span><span class="sxs-lookup"><span data-stu-id="e25bc-122">**Append output to existing file**</span></span>  
 <span data-ttu-id="e25bc-123">ファイルの既存の内容に出力を追加します。</span><span class="sxs-lookup"><span data-stu-id="e25bc-123">Append output to the existing contents of the file.</span></span> <span data-ttu-id="e25bc-124">このオプションを指定しなければ、ジョブ ステップが実行されるたびに前のファイルの内容が上書きされます。</span><span class="sxs-lookup"><span data-stu-id="e25bc-124">Otherwise, the previous file contents are overwritten each time the job step runs.</span></span>  
  
 <span data-ttu-id="e25bc-125">**[テーブルにログ記録する]**</span><span class="sxs-lookup"><span data-stu-id="e25bc-125">**Log to table**</span></span>  
 <span data-ttu-id="e25bc-126">**msdb** データベースの **sysjobstepslogs** テーブルに、ジョブ ステップの出力のログを記録します。</span><span class="sxs-lookup"><span data-stu-id="e25bc-126">Logs job step output to the **sysjobstepslogs** table in the **msdb** database.</span></span>  
  
 <span data-ttu-id="e25bc-127">**表示**</span><span class="sxs-lookup"><span data-stu-id="e25bc-127">**View**</span></span>  
 <span data-ttu-id="e25bc-128">ジョブ ステップを 1 回以上実行した後で **[表示]** をクリックすると、出力がテーブルに表示されます。</span><span class="sxs-lookup"><span data-stu-id="e25bc-128">After the job step has run at least once, click **View** to view its output in the table.</span></span>  
  
 <span data-ttu-id="e25bc-129">**[テーブル内の既存のエントリに出力を追加する]**</span><span class="sxs-lookup"><span data-stu-id="e25bc-129">**Append output to existing entry in table**</span></span>  
 <span data-ttu-id="e25bc-130">テーブルの既存の内容に出力を追加します。</span><span class="sxs-lookup"><span data-stu-id="e25bc-130">Appends output to the existing contents of the table.</span></span> <span data-ttu-id="e25bc-131">このオプションを指定しなければ、ジョブ ステップが実行されるたびに前のテーブルの内容が上書きされます。</span><span class="sxs-lookup"><span data-stu-id="e25bc-131">Otherwise, the previous table contents are overwritten each time the job step runs.</span></span>  
  
 <span data-ttu-id="e25bc-132">**[履歴にステップ出力を含める]**</span><span class="sxs-lookup"><span data-stu-id="e25bc-132">**Include step output in history**</span></span>  
 <span data-ttu-id="e25bc-133">このオプションを選択すると、ジョブ ステップの出力がジョブ履歴に含められます。</span><span class="sxs-lookup"><span data-stu-id="e25bc-133">Select this option to include output from the job step in the job history.</span></span>  
  
 <span data-ttu-id="e25bc-134">**[実行時のユーザー]**</span><span class="sxs-lookup"><span data-stu-id="e25bc-134">**Run as user**</span></span>  
 <span data-ttu-id="e25bc-135">**sysadmin** 固定サーバー ロールのメンバーであれば、別の SQL ログインを選択してこのジョブ ステップを実行できます。</span><span class="sxs-lookup"><span data-stu-id="e25bc-135">If you are a member of the **sysadmin** fixed server role, you can select another SQL login to run this job step.</span></span>  
  
## <a name="options-for-operating-system-cmdexec-job-steps"></a><span data-ttu-id="e25bc-136">オペレーティング システム (CmdExec) ジョブ ステップのオプション</span><span class="sxs-lookup"><span data-stu-id="e25bc-136">Options for Operating System (CmdExec) Job Steps</span></span>  
 <span data-ttu-id="e25bc-137">**[出力ファイル]**</span><span class="sxs-lookup"><span data-stu-id="e25bc-137">**Output file**</span></span>  
 <span data-ttu-id="e25bc-138">ジョブ ステップからの出力に使用するファイルを設定します。</span><span class="sxs-lookup"><span data-stu-id="e25bc-138">Sets the file to use for output from the job step.</span></span>  
  
 <span data-ttu-id="e25bc-139">**...**</span><span class="sxs-lookup"><span data-stu-id="e25bc-139">**...**</span></span>  
 <span data-ttu-id="e25bc-140">ジョブ ステップからの出力に使用するファイルを参照します。</span><span class="sxs-lookup"><span data-stu-id="e25bc-140">Browse to the file to use for output from the job step.</span></span>  
  
 <span data-ttu-id="e25bc-141">**表示**</span><span class="sxs-lookup"><span data-stu-id="e25bc-141">**View**</span></span>  
 <span data-ttu-id="e25bc-142">で [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] は、このボタンを使用して出力ファイルを表示することはできません。</span><span class="sxs-lookup"><span data-stu-id="e25bc-142">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], this button is disabled for viewing output files.</span></span> <span data-ttu-id="e25bc-143">代わりに、メモ帳を使用してジョブ ステップの出力ファイルを表示します。</span><span class="sxs-lookup"><span data-stu-id="e25bc-143">Instead, use Notepad to view job step output files.</span></span>  
  
 <span data-ttu-id="e25bc-144">**[既存のファイルに出力を追加する]**</span><span class="sxs-lookup"><span data-stu-id="e25bc-144">**Append output to existing file**</span></span>  
 <span data-ttu-id="e25bc-145">ジョブ ステップを実行するたびに、その出力を前のファイルの内容に追加します。</span><span class="sxs-lookup"><span data-stu-id="e25bc-145">Appends the job step output to the previous file contents each time it runs.</span></span>  
  
 <span data-ttu-id="e25bc-146">**[テーブルにログ記録する]**</span><span class="sxs-lookup"><span data-stu-id="e25bc-146">**Log to table**</span></span>  
 <span data-ttu-id="e25bc-147">**msdb** データベースの **sysjobstepslogs** テーブルに、ジョブ ステップの出力のログを記録します。</span><span class="sxs-lookup"><span data-stu-id="e25bc-147">Logs job step output to the **sysjobstepslogs** table in the **msdb** database.</span></span>  
  
 <span data-ttu-id="e25bc-148">**表示**</span><span class="sxs-lookup"><span data-stu-id="e25bc-148">**View**</span></span>  
 <span data-ttu-id="e25bc-149">ジョブ ステップを 1 回以上実行した後で **[表示]** をクリックすると、出力がテーブルに表示されます。</span><span class="sxs-lookup"><span data-stu-id="e25bc-149">After the job step has run at least once, click **View** to view its output in the table.</span></span>  
  
 <span data-ttu-id="e25bc-150">**[テーブル内の既存のエントリに出力を追加する]**</span><span class="sxs-lookup"><span data-stu-id="e25bc-150">**Append output to existing entry in table**</span></span>  
 <span data-ttu-id="e25bc-151">テーブルの既存の内容に出力を追加します。</span><span class="sxs-lookup"><span data-stu-id="e25bc-151">Appends output to the existing contents of the table.</span></span> <span data-ttu-id="e25bc-152">このオプションを指定しなければ、ジョブ ステップが実行されるたびに前のテーブルの内容が上書きされます。</span><span class="sxs-lookup"><span data-stu-id="e25bc-152">Otherwise, the previous table contents are overwritten each time the job step runs.</span></span>  
  
 <span data-ttu-id="e25bc-153">**[履歴にステップ出力を含める]**</span><span class="sxs-lookup"><span data-stu-id="e25bc-153">**Include step output in history**</span></span>  
 <span data-ttu-id="e25bc-154">このオプションを選択すると、ジョブ ステップの出力がジョブ履歴に含められます。</span><span class="sxs-lookup"><span data-stu-id="e25bc-154">Select this option to include output from the job step in the job history.</span></span>  
  
## <a name="options-for-powershell-job-steps"></a><span data-ttu-id="e25bc-155">PowerShell ジョブ ステップのオプション</span><span class="sxs-lookup"><span data-stu-id="e25bc-155">Options for PowerShell Job Steps</span></span>  
 <span data-ttu-id="e25bc-156">**[出力ファイル]**</span><span class="sxs-lookup"><span data-stu-id="e25bc-156">**Output file**</span></span>  
 <span data-ttu-id="e25bc-157">ジョブ ステップからの出力に使用するファイルを設定します。</span><span class="sxs-lookup"><span data-stu-id="e25bc-157">Sets the file to use for output from the job step.</span></span>  
  
 <span data-ttu-id="e25bc-158">**...**</span><span class="sxs-lookup"><span data-stu-id="e25bc-158">**...**</span></span>  
 <span data-ttu-id="e25bc-159">ジョブ ステップからの出力に使用するファイルを参照します。</span><span class="sxs-lookup"><span data-stu-id="e25bc-159">Browse to the file to use for output from the job step.</span></span>  
  
 <span data-ttu-id="e25bc-160">**表示**</span><span class="sxs-lookup"><span data-stu-id="e25bc-160">**View**</span></span>  
 <span data-ttu-id="e25bc-161">で [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] は、このボタンを使用して出力ファイルを表示することはできません。</span><span class="sxs-lookup"><span data-stu-id="e25bc-161">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], this button is disabled for viewing output files.</span></span> <span data-ttu-id="e25bc-162">代わりに、メモ帳を使用してジョブ ステップの出力ファイルを表示します。</span><span class="sxs-lookup"><span data-stu-id="e25bc-162">Instead, use Notepad to view job step output files.</span></span>  
  
 <span data-ttu-id="e25bc-163">**[既存のファイルに出力を追加する]**</span><span class="sxs-lookup"><span data-stu-id="e25bc-163">**Append output to existing file**</span></span>  
 <span data-ttu-id="e25bc-164">ジョブ ステップを実行するたびに、その出力を前のファイルの内容に追加します。</span><span class="sxs-lookup"><span data-stu-id="e25bc-164">Appends the job step output to the previous file contents each time it runs.</span></span>  
  
 <span data-ttu-id="e25bc-165">**[テーブルにログ記録する]**</span><span class="sxs-lookup"><span data-stu-id="e25bc-165">**Log to table**</span></span>  
 <span data-ttu-id="e25bc-166">**msdb** データベースの **sysjobstepslogs** テーブルに、ジョブ ステップの出力のログを記録します。</span><span class="sxs-lookup"><span data-stu-id="e25bc-166">Logs job step output to the **sysjobstepslogs** table in the **msdb** database.</span></span>  
  
 <span data-ttu-id="e25bc-167">**表示**</span><span class="sxs-lookup"><span data-stu-id="e25bc-167">**View**</span></span>  
 <span data-ttu-id="e25bc-168">ジョブ ステップを 1 回以上実行した後で **[表示]** をクリックすると、出力がテーブルに表示されます。</span><span class="sxs-lookup"><span data-stu-id="e25bc-168">After the job step has run at least once, click **View** to view its output in the table.</span></span>  
  
 <span data-ttu-id="e25bc-169">**[テーブル内の既存のエントリに出力を追加する]**</span><span class="sxs-lookup"><span data-stu-id="e25bc-169">**Append output to existing entry in table**</span></span>  
 <span data-ttu-id="e25bc-170">テーブルの既存の内容に出力を追加します。</span><span class="sxs-lookup"><span data-stu-id="e25bc-170">Appends output to the existing contents of the table.</span></span> <span data-ttu-id="e25bc-171">このオプションを指定しなければ、ジョブ ステップが実行されるたびに前のテーブルの内容が上書きされます。</span><span class="sxs-lookup"><span data-stu-id="e25bc-171">Otherwise, the previous table contents are overwritten each time the job step runs.</span></span>  
  
 <span data-ttu-id="e25bc-172">**[履歴にステップ出力を含める]**</span><span class="sxs-lookup"><span data-stu-id="e25bc-172">**Include step output in history**</span></span>  
 <span data-ttu-id="e25bc-173">このオプションを選択すると、ジョブ ステップの出力がジョブ履歴に含められます。</span><span class="sxs-lookup"><span data-stu-id="e25bc-173">Select this option to include output from the job step in the job history.</span></span>  
  
## <a name="options-for-replication-queue-reader-job-steps"></a><span data-ttu-id="e25bc-174">レプリケーション キュー リーダーのジョブ ステップのオプション</span><span class="sxs-lookup"><span data-stu-id="e25bc-174">Options for Replication Queue Reader Job Steps</span></span>  
 <span data-ttu-id="e25bc-175">**[サーバー]**</span><span class="sxs-lookup"><span data-stu-id="e25bc-175">**Server**</span></span>  
 <span data-ttu-id="e25bc-176">レプリケーション キュー リーダーのジョブ ステップを使用するように、サーバーを設定します。</span><span class="sxs-lookup"><span data-stu-id="e25bc-176">Sets the server to use for a replication queue reader job step.</span></span>  
  
 <span data-ttu-id="e25bc-177">**[データベース]**</span><span class="sxs-lookup"><span data-stu-id="e25bc-177">**Database**</span></span>  
 <span data-ttu-id="e25bc-178">レプリケーション キュー リーダーのジョブ ステップを使用するように、データベースを設定します。</span><span class="sxs-lookup"><span data-stu-id="e25bc-178">Sets the database to use for a replication queue reader job step.</span></span>  
  
## <a name="options-for-sql-server-analysis-services-job-steps"></a><span data-ttu-id="e25bc-179">SQL Server Analysis Services ジョブ ステップのオプション</span><span class="sxs-lookup"><span data-stu-id="e25bc-179">Options for SQL Server Analysis Services Job Steps</span></span>  
 <span data-ttu-id="e25bc-180">**[出力ファイル]**</span><span class="sxs-lookup"><span data-stu-id="e25bc-180">**Output file**</span></span>  
 <span data-ttu-id="e25bc-181">ジョブ ステップからの出力に使用するファイルを設定します。</span><span class="sxs-lookup"><span data-stu-id="e25bc-181">Sets the file to use for output from the job step.</span></span> <span data-ttu-id="e25bc-182">このオプションは、 **sysadmin** 固定サーバー ロールのメンバーである場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="e25bc-182">This option is available only to members of the **sysadmin** fixed server role.</span></span>  
  
 <span data-ttu-id="e25bc-183">**...**</span><span class="sxs-lookup"><span data-stu-id="e25bc-183">**...**</span></span>  
 <span data-ttu-id="e25bc-184">ジョブ ステップからの出力に使用するファイルを参照します。</span><span class="sxs-lookup"><span data-stu-id="e25bc-184">Browse to the file to use for output from the job step.</span></span>  
  
 <span data-ttu-id="e25bc-185">**表示**</span><span class="sxs-lookup"><span data-stu-id="e25bc-185">**View**</span></span>  
 <span data-ttu-id="e25bc-186">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]では、このボタンを使用して出力ファイルを表示することはできません。</span><span class="sxs-lookup"><span data-stu-id="e25bc-186">In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], this button is disabled for viewing output files.</span></span> <span data-ttu-id="e25bc-187">代わりに、メモ帳を使用してジョブ ステップの出力ファイルを表示します。</span><span class="sxs-lookup"><span data-stu-id="e25bc-187">Instead, use Notepad to view job step output files.</span></span>  
  
 <span data-ttu-id="e25bc-188">**[既存のファイルに出力を追加する]**</span><span class="sxs-lookup"><span data-stu-id="e25bc-188">**Append output to existing file**</span></span>  
 <span data-ttu-id="e25bc-189">ファイルの既存の内容に出力を追加します。</span><span class="sxs-lookup"><span data-stu-id="e25bc-189">Append output to the existing contents of the file.</span></span> <span data-ttu-id="e25bc-190">このオプションを指定しなければ、ジョブ ステップが実行されるたびに前のファイルの内容が上書きされます。</span><span class="sxs-lookup"><span data-stu-id="e25bc-190">Otherwise, the previous file contents are overwritten each time the job step runs.</span></span>  
  
 <span data-ttu-id="e25bc-191">**[テーブルにログ記録する]**</span><span class="sxs-lookup"><span data-stu-id="e25bc-191">**Log to table**</span></span>  
 <span data-ttu-id="e25bc-192">**msdb** データベースの **sysjobstepslogs** テーブルに、ジョブ ステップの出力のログを記録します。</span><span class="sxs-lookup"><span data-stu-id="e25bc-192">Logs job step output to the **sysjobstepslogs** table in the **msdb** database.</span></span>  
  
 <span data-ttu-id="e25bc-193">**表示**</span><span class="sxs-lookup"><span data-stu-id="e25bc-193">**View**</span></span>  
 <span data-ttu-id="e25bc-194">ジョブ ステップを 1 回以上実行した後で **[表示]** をクリックすると、出力がテーブルに表示されます。</span><span class="sxs-lookup"><span data-stu-id="e25bc-194">After the job step has run at least once, click **View** to view its output in the table.</span></span>  
  
 <span data-ttu-id="e25bc-195">**[テーブル内の既存のエントリに出力を追加する]**</span><span class="sxs-lookup"><span data-stu-id="e25bc-195">**Append output to existing entry in table**</span></span>  
 <span data-ttu-id="e25bc-196">テーブルの既存の内容に出力を追加します。</span><span class="sxs-lookup"><span data-stu-id="e25bc-196">Appends output to the existing contents of the table.</span></span> <span data-ttu-id="e25bc-197">このオプションを指定しなければ、ジョブ ステップが実行されるたびに前のテーブルの内容が上書きされます。</span><span class="sxs-lookup"><span data-stu-id="e25bc-197">Otherwise, the previous table contents are overwritten each time the job step runs.</span></span>  
  
 <span data-ttu-id="e25bc-198">**[履歴にステップ出力を含める]**</span><span class="sxs-lookup"><span data-stu-id="e25bc-198">**Include step output in history**</span></span>  
 <span data-ttu-id="e25bc-199">このオプションを選択すると、ジョブ ステップの出力がジョブ履歴に含められます。</span><span class="sxs-lookup"><span data-stu-id="e25bc-199">Select this option to include output from the job step in the job history.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e25bc-200">参照</span><span class="sxs-lookup"><span data-stu-id="e25bc-200">See Also</span></span>  
 [<span data-ttu-id="e25bc-201">ジョブ ステップの管理</span><span class="sxs-lookup"><span data-stu-id="e25bc-201">Manage Job Steps</span></span>](manage-job-steps.md)  
  
  
