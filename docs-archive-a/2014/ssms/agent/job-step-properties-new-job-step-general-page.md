---
title: '[ジョブステップのプロパティ]: [新しいジョブステップ] ([全般] ページ)Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.job.stepgeneral.f1
ms.assetid: 8d1885ba-4386-4528-8f2b-68c16852720c
author: stevestein
ms.author: sstein
ms.openlocfilehash: c76e1ecb69a1475ec102f143a6a1ca34fbf91e3f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643072"
---
# <a name="job-step-properties-new-job-step-general-page"></a><span data-ttu-id="e7b7d-102">[ジョブ ステップのプロパティ]:[新しいジョブ ステップ] ([全般] ページ)</span><span class="sxs-lookup"><span data-stu-id="e7b7d-102">Job Step Properties: New Job Step (General Page)</span></span>
  <span data-ttu-id="e7b7d-103">このページを使用すると、エージェントジョブステップのプロパティを表示および変更し [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] たり、新しいジョブステップを定義したりできます。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-103">Use this page to view and change the properties of a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job step, or to define a new job step.</span></span>  
  
 <span data-ttu-id="e7b7d-104">このページに移動するには、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] のオブジェクト エクスプローラーで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントを展開します。次に **[ジョブ]** を右クリックし、 **[新しいジョブ]** をクリックして **[ステップ]** ページを選択し、 **[新規作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-104">To navigate to this page, in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Object Explorer, expand [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, right-click **Jobs**, click **New Jobs**, select the **Steps** page, and click **New**.</span></span> <span data-ttu-id="e7b7d-105">または、オブジェクト エクスプローラーでジョブを右クリックし、 **[プロパティ]** をクリックして **[ステップ]** ページを選択し、 **[新規作成]**、 **[挿入]**、または **[編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-105">You can also navigate to this page by right-clicking a job in Object Explorer, clicking **Properties**, selecting the **Steps** page, and clicking **New**, **Insert**, or **Edit**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="e7b7d-106">Options</span><span class="sxs-lookup"><span data-stu-id="e7b7d-106">Options</span></span>  
 <span data-ttu-id="e7b7d-107">**[ステップ名]**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-107">**Step name**</span></span>  
 <span data-ttu-id="e7b7d-108">ジョブ ステップの名前を設定します。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-108">Set the name of the job step.</span></span>  
  
 <span data-ttu-id="e7b7d-109">**Type**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-109">**Type**</span></span>  
 <span data-ttu-id="e7b7d-110">ジョブ ステップが使用するサブシステムを設定します。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-110">Set the subsystem that the job step uses.</span></span> <span data-ttu-id="e7b7d-111">選択したサブシステムに基づいて、ジョブ ステップを定義するために表示されるオプションが変更されます。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-111">Based on the subsystem you choose, the options displayed for defining the job step change.</span></span>  
  
 <span data-ttu-id="e7b7d-112">**[実行するアカウント名]**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-112">**Run as**</span></span>  
 <span data-ttu-id="e7b7d-113">ジョブ ステップのプロキシ アカウントを設定します。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-113">Set the proxy account for the job step.</span></span> <span data-ttu-id="e7b7d-114">sysadmin 固定サーバー ロールのメンバーは、 **[SQL Server エージェント サービスのアカウント]** を指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-114">Members of the sysadmin fixed server role may also specify the **SQL Agent Service Account**.</span></span>  
  
 <span data-ttu-id="e7b7d-115">**[データベース]**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-115">**Database**</span></span>  
 <span data-ttu-id="e7b7d-116">ジョブ ステップを実行するデータベースを設定します。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-116">Set the database that the job step runs in.</span></span> <span data-ttu-id="e7b7d-117">このオプションは、すべてのジョブ ステップの種類で使用できるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-117">This option is not available for all job step types.</span></span>  
  
 <span data-ttu-id="e7b7d-118">**コマンド**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-118">**Command**</span></span>  
 <span data-ttu-id="e7b7d-119">ジョブ ステップが実行するコマンドを設定します。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-119">Set the command that the job step runs.</span></span>  
  
## <a name="options-for-transact-sql-job-steps"></a><span data-ttu-id="e7b7d-120">Transact-SQL ジョブ ステップのオプション</span><span class="sxs-lookup"><span data-stu-id="e7b7d-120">Options for Transact-SQL Job Steps</span></span>  
 <span data-ttu-id="e7b7d-121">**[ファイル]**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-121">**Open**</span></span>  
 <span data-ttu-id="e7b7d-122">コマンドをファイルから読み込みます。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-122">Load the command from a file.</span></span>  
  
 <span data-ttu-id="e7b7d-123">**[すべて選択]**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-123">**Select All**</span></span>  
 <span data-ttu-id="e7b7d-124">コマンドのテキストを選択します。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-124">Select the text of the command.</span></span>  
  
 <span data-ttu-id="e7b7d-125">**コピー**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-125">**Copy**</span></span>  
 <span data-ttu-id="e7b7d-126">選択されたテキストをクリップボードにコピーします。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-126">Copy the selected text to the Clipboard.</span></span>  
  
 <span data-ttu-id="e7b7d-127">**貼り付け**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-127">**Paste**</span></span>  
 <span data-ttu-id="e7b7d-128">クリップボードの内容を貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-128">Paste the contents of the Clipboard.</span></span>  
  
 <span data-ttu-id="e7b7d-129">**Parse**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-129">**Parse**</span></span>  
 <span data-ttu-id="e7b7d-130">コマンドの構文をチェックします。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-130">Check the syntax of the command.</span></span>  
  
## <a name="options-for-activex-script-job-steps"></a><span data-ttu-id="e7b7d-131">ActiveX スクリプト ジョブ ステップのオプション</span><span class="sxs-lookup"><span data-stu-id="e7b7d-131">Options for ActiveX Script Job Steps</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="e7b7d-132">ActiveX スクリプティング サブシステムは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の将来のバージョンで [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エージェントから削除される予定です。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-132">The ActiveX Scripting subsystem will be removed from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent in a future version of [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="e7b7d-133">新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-133">Avoid using this feature in new development work, and plan to modify applications that currently use this feature.</span></span>  
  
 <span data-ttu-id="e7b7d-134">**[VBScript]**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-134">**VBScript**</span></span>  
 <span data-ttu-id="e7b7d-135">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic Scripting Edition をジョブ ステップの言語として指定します。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-135">Specify [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic Scripting Edition as the language for the job steps.</span></span>  
  
 <span data-ttu-id="e7b7d-136">**JScript**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-136">**JScript**</span></span>  
 <span data-ttu-id="e7b7d-137">JScript をジョブ ステップの言語として指定します。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-137">Specify JScript as the language for the job steps.</span></span>  
  
 <span data-ttu-id="e7b7d-138">**その他**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-138">**Other**</span></span>  
 <span data-ttu-id="e7b7d-139">別のスクリプト言語で記述されたジョブ ステップの言語の名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-139">Type the name of the language for job steps written in another scripting language.</span></span>  
  
 <span data-ttu-id="e7b7d-140">**[ファイル]**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-140">**Open**</span></span>  
 <span data-ttu-id="e7b7d-141">コマンドをファイルから読み込みます。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-141">Load the command from a file.</span></span>  
  
 <span data-ttu-id="e7b7d-142">**[すべて選択]**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-142">**Select All**</span></span>  
 <span data-ttu-id="e7b7d-143">コマンドのテキストを選択します。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-143">Select the text of the command.</span></span>  
  
 <span data-ttu-id="e7b7d-144">**コピー**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-144">**Copy**</span></span>  
 <span data-ttu-id="e7b7d-145">選択したテキストをコピーします。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-145">Copy the selected text.</span></span>  
  
 <span data-ttu-id="e7b7d-146">**貼り付け**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-146">**Paste**</span></span>  
 <span data-ttu-id="e7b7d-147">クリップボードの内容を貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-147">Paste the contents of the Clipboard.</span></span>  
  
## <a name="options-for-operating-system-cmdexec-job-steps"></a><span data-ttu-id="e7b7d-148">オペレーティング システム (CmdExec) ジョブ ステップのオプション</span><span class="sxs-lookup"><span data-stu-id="e7b7d-148">Options for Operating System (CmdExec) Job Steps</span></span>  
 <span data-ttu-id="e7b7d-149">**[コマンド成功時のプロセス終了コード]**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-149">**Process exit code of a successful command**</span></span>  
 <span data-ttu-id="e7b7d-150">成功を示すためにコマンドが返す終了コードを入力します。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-150">Type the exit code that the command returns to indicate success.</span></span>  
  
 <span data-ttu-id="e7b7d-151">**[ファイル]**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-151">**Open**</span></span>  
 <span data-ttu-id="e7b7d-152">コマンドをファイルから読み込みます。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-152">Load the command from a file.</span></span>  
  
 <span data-ttu-id="e7b7d-153">**[すべて選択]**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-153">**Select All**</span></span>  
 <span data-ttu-id="e7b7d-154">コマンドのテキストを選択します。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-154">Select the text of the command.</span></span>  
  
 <span data-ttu-id="e7b7d-155">**コピー**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-155">**Copy**</span></span>  
 <span data-ttu-id="e7b7d-156">選択したテキストをコピーします。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-156">Copy the selected text.</span></span>  
  
 <span data-ttu-id="e7b7d-157">**貼り付け**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-157">**Paste**</span></span>  
 <span data-ttu-id="e7b7d-158">クリップボードの内容を貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-158">Paste the contents of the Clipboard.</span></span>  
  
## <a name="options-for-powershell-job-steps"></a><span data-ttu-id="e7b7d-159">PowerShell ジョブ ステップのオプション</span><span class="sxs-lookup"><span data-stu-id="e7b7d-159">Options for PowerShell Job Steps</span></span>  
 <span data-ttu-id="e7b7d-160">**[ファイル]**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-160">**Open**</span></span>  
 <span data-ttu-id="e7b7d-161">ファイルからスクリプトを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-161">Load the script from a file.</span></span>  
  
 <span data-ttu-id="e7b7d-162">**[すべて選択]**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-162">**Select All**</span></span>  
 <span data-ttu-id="e7b7d-163">スクリプトのテキストを選択します。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-163">Select the text of the script.</span></span>  
  
 <span data-ttu-id="e7b7d-164">**コピー**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-164">**Copy**</span></span>  
 <span data-ttu-id="e7b7d-165">選択したテキストをコピーします。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-165">Copy the selected text.</span></span>  
  
 <span data-ttu-id="e7b7d-166">**貼り付け**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-166">**Paste**</span></span>  
 <span data-ttu-id="e7b7d-167">クリップボードの内容を貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-167">Paste the contents of the Clipboard.</span></span>  
  
## <a name="options-for-replication-distributor-job-steps"></a><span data-ttu-id="e7b7d-168">レプリケーション ディストリビューター ジョブ ステップのオプション</span><span class="sxs-lookup"><span data-stu-id="e7b7d-168">Options for Replication Distributor Job Steps</span></span>  
 <span data-ttu-id="e7b7d-169">**[すべて選択]**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-169">**Select All**</span></span>  
 <span data-ttu-id="e7b7d-170">コマンドのテキストを選択します。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-170">Select the text of the command.</span></span>  
  
 <span data-ttu-id="e7b7d-171">**コピー**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-171">**Copy**</span></span>  
 <span data-ttu-id="e7b7d-172">選択したテキストをコピーします。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-172">Copy the selected text.</span></span>  
  
 <span data-ttu-id="e7b7d-173">**貼り付け**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-173">**Paste**</span></span>  
 <span data-ttu-id="e7b7d-174">クリップボードの内容を貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-174">Paste the contents of the Clipboard.</span></span>  
  
## <a name="options-for-replication-merge-job-steps"></a><span data-ttu-id="e7b7d-175">レプリケーション マージ ジョブ ステップのオプション</span><span class="sxs-lookup"><span data-stu-id="e7b7d-175">Options for Replication Merge Job Steps</span></span>  
 <span data-ttu-id="e7b7d-176">**[すべて選択]**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-176">**Select All**</span></span>  
 <span data-ttu-id="e7b7d-177">コマンドのテキストを選択します。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-177">Select the text of the command.</span></span>  
  
 <span data-ttu-id="e7b7d-178">**コピー**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-178">**Copy**</span></span>  
 <span data-ttu-id="e7b7d-179">選択したテキストをコピーします。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-179">Copy the selected text.</span></span>  
  
 <span data-ttu-id="e7b7d-180">**貼り付け**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-180">**Paste**</span></span>  
 <span data-ttu-id="e7b7d-181">クリップボードの内容を貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-181">Paste the contents of the Clipboard.</span></span>  
  
## <a name="options-for-replication-queue-reader-job-steps"></a><span data-ttu-id="e7b7d-182">レプリケーション キュー リーダーのジョブ ステップのオプション</span><span class="sxs-lookup"><span data-stu-id="e7b7d-182">Options for Replication Queue Reader Job Steps</span></span>  
 <span data-ttu-id="e7b7d-183">**[データベース]**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-183">**Database**</span></span>  
 <span data-ttu-id="e7b7d-184">ジョブ ステップに使用するデータベースです。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-184">The database to use for the job step.</span></span>  
  
 <span data-ttu-id="e7b7d-185">**[すべて選択]**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-185">**Select All**</span></span>  
 <span data-ttu-id="e7b7d-186">コマンドのテキストを選択します。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-186">Select the text of the command.</span></span>  
  
 <span data-ttu-id="e7b7d-187">**コピー**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-187">**Copy**</span></span>  
 <span data-ttu-id="e7b7d-188">選択したテキストをコピーします。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-188">Copy the selected text.</span></span>  
  
 <span data-ttu-id="e7b7d-189">**貼り付け**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-189">**Paste**</span></span>  
 <span data-ttu-id="e7b7d-190">クリップボードの内容を貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-190">Paste the contents of the Clipboard.</span></span>  
  
## <a name="options-for-replication-snapshot-job-steps"></a><span data-ttu-id="e7b7d-191">レプリケーション スナップショット ジョブ ステップのオプション</span><span class="sxs-lookup"><span data-stu-id="e7b7d-191">Options for Replication Snapshot Job Steps</span></span>  
 <span data-ttu-id="e7b7d-192">**[すべて選択]**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-192">**Select All**</span></span>  
 <span data-ttu-id="e7b7d-193">コマンドのテキストを選択します。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-193">Select the text of the command.</span></span>  
  
 <span data-ttu-id="e7b7d-194">**コピー**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-194">**Copy**</span></span>  
 <span data-ttu-id="e7b7d-195">選択したテキストをコピーします。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-195">Copy the selected text.</span></span>  
  
 <span data-ttu-id="e7b7d-196">**貼り付け**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-196">**Paste**</span></span>  
 <span data-ttu-id="e7b7d-197">クリップボードの内容を貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-197">Paste the contents of the Clipboard.</span></span>  
  
## <a name="options-for-replication-transaction-log-reader-job-steps"></a><span data-ttu-id="e7b7d-198">レプリケーション トランザクション ログ リーダー ジョブ ステップのオプション</span><span class="sxs-lookup"><span data-stu-id="e7b7d-198">Options for Replication Transaction-Log Reader Job Steps</span></span>  
 <span data-ttu-id="e7b7d-199">**[すべて選択]**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-199">**Select All**</span></span>  
 <span data-ttu-id="e7b7d-200">コマンドのテキストを選択します。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-200">Select the text of the command.</span></span>  
  
 <span data-ttu-id="e7b7d-201">**コピー**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-201">**Copy**</span></span>  
 <span data-ttu-id="e7b7d-202">選択したテキストをコピーします。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-202">Copy the selected text.</span></span>  
  
 <span data-ttu-id="e7b7d-203">**貼り付け**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-203">**Paste**</span></span>  
 <span data-ttu-id="e7b7d-204">クリップボードの内容を貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-204">Paste the contents of the Clipboard.</span></span>  
  
## <a name="options-for-sql-server-analysis-services-command-job-steps"></a><span data-ttu-id="e7b7d-205">SQL Server Analysis Services コマンド ジョブ ステップのオプション</span><span class="sxs-lookup"><span data-stu-id="e7b7d-205">Options for SQL Server Analysis Services Command Job Steps</span></span>  
 <span data-ttu-id="e7b7d-206">**[サーバー]**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-206">**Server**</span></span>  
 <span data-ttu-id="e7b7d-207">ジョブ ステップを実行するサーバーを選択します。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-207">Select the server where the job step runs.</span></span>  
  
 <span data-ttu-id="e7b7d-208">**[ファイル]**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-208">**Open**</span></span>  
 <span data-ttu-id="e7b7d-209">コマンドをファイルから読み込みます。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-209">Load the command from a file.</span></span>  
  
 <span data-ttu-id="e7b7d-210">**[すべて選択]**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-210">**Select All**</span></span>  
 <span data-ttu-id="e7b7d-211">コマンドのテキストを選択します。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-211">Select the text of the command.</span></span>  
  
 <span data-ttu-id="e7b7d-212">**コピー**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-212">**Copy**</span></span>  
 <span data-ttu-id="e7b7d-213">選択したテキストをコピーします。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-213">Copy the selected text.</span></span>  
  
 <span data-ttu-id="e7b7d-214">**貼り付け**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-214">**Paste**</span></span>  
 <span data-ttu-id="e7b7d-215">クリップボードの内容を貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-215">Paste the contents of the Clipboard.</span></span>  
  
## <a name="options-for-sql-server-analysis-services-query-job-steps"></a><span data-ttu-id="e7b7d-216">SQL Server Analysis Services クエリ ジョブ ステップのオプション</span><span class="sxs-lookup"><span data-stu-id="e7b7d-216">Options for SQL Server Analysis Services Query Job Steps</span></span>  
 <span data-ttu-id="e7b7d-217">**[サーバー]**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-217">**Server**</span></span>  
 <span data-ttu-id="e7b7d-218">ジョブ ステップを実行するサーバーを選択します。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-218">Select the server where the job step runs.</span></span>  
  
 <span data-ttu-id="e7b7d-219">**[データベース]**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-219">**Database**</span></span>  
 <span data-ttu-id="e7b7d-220">ジョブ ステップに使用するデータベースです。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-220">The database to use for the job step.</span></span>  
  
 <span data-ttu-id="e7b7d-221">**[ファイル]**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-221">**Open**</span></span>  
 <span data-ttu-id="e7b7d-222">コマンドをファイルから読み込みます。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-222">Load the command from a file.</span></span>  
  
 <span data-ttu-id="e7b7d-223">**[すべて選択]**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-223">**Select All**</span></span>  
 <span data-ttu-id="e7b7d-224">コマンドのテキストを選択します。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-224">Select the text of the command.</span></span>  
  
 <span data-ttu-id="e7b7d-225">**コピー**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-225">**Copy**</span></span>  
 <span data-ttu-id="e7b7d-226">選択したテキストをコピーします。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-226">Copy the selected text.</span></span>  
  
 <span data-ttu-id="e7b7d-227">**貼り付け**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-227">**Paste**</span></span>  
 <span data-ttu-id="e7b7d-228">クリップボードの内容を貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-228">Paste the contents of the Clipboard.</span></span>  
  
## <a name="options-for-integration-services-package-execution-job-steps"></a><span data-ttu-id="e7b7d-229">Integration Services パッケージ実行ジョブ ステップのオプション</span><span class="sxs-lookup"><span data-stu-id="e7b7d-229">Options for Integration Services Package Execution Job Steps</span></span>  
  
### <a name="general-tab"></a><span data-ttu-id="e7b7d-230">全般タブ</span><span class="sxs-lookup"><span data-stu-id="e7b7d-230">General Tab</span></span>  
 <span data-ttu-id="e7b7d-231">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ([!INCLUDE[ssIS](../../includes/ssis-md.md)]) パッケージの場所と、使用する認証方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-231">Specify where the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ([!INCLUDE[ssIS](../../includes/ssis-md.md)]) package is located and what authentication method to use.</span></span> <span data-ttu-id="e7b7d-232">このタブを選択するとき、次のオプションを利用できます。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-232">The following options are available when you select this tab.</span></span>  
  
 <span data-ttu-id="e7b7d-233">**パッケージソース**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-233">**Package source**</span></span>  
 <span data-ttu-id="e7b7d-234">[!INCLUDE[ssIS](../../includes/ssis-md.md)] パッケージが格納されている場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-234">Specify where the [!INCLUDE[ssIS](../../includes/ssis-md.md)] package is stored.</span></span> <span data-ttu-id="e7b7d-235">次のいずれかを選択します。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-235">Choose one of the following:</span></span>  
  
-   <span data-ttu-id="e7b7d-236">**SQL Server**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-236">**SQL Server**</span></span>  
  
-   <span data-ttu-id="e7b7d-237">**ファイル システム**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-237">**File system**</span></span>  
  
-   <span data-ttu-id="e7b7d-238">**[SSIS パッケージ ストア]**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-238">**SSIS Package Store**</span></span>  
  
 <span data-ttu-id="e7b7d-239">**[サーバー]**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-239">**Server**</span></span>  
 <span data-ttu-id="e7b7d-240">[!INCLUDE[ssIS](../../includes/ssis-md.md)] パッケージが格納されているサーバーの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-240">Type the server name where the [!INCLUDE[ssIS](../../includes/ssis-md.md)] package is stored.</span></span> <span data-ttu-id="e7b7d-241">このオプションは、 **[パッケージ ソース]** に **[SQL Server]** または **[SSIS パッケージ ストア]** が指定されている場合のみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-241">This option is only available when **SQL Server** or **SSIS Package Store** is specified for **Package Source**.</span></span>  
  
 <span data-ttu-id="e7b7d-242">**[Windows 認証を使用する]**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-242">**Use Windows Authentication**</span></span>  
 <span data-ttu-id="e7b7d-243">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] へのログインに [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 認証を使用します。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-243">Logins to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] use [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Authentication.</span></span>  
  
 <span data-ttu-id="e7b7d-244">**[SQL Server 認証を使用する]**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-244">**Use SQL Server Authentication**</span></span>  
 <span data-ttu-id="e7b7d-245">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] へのログインに [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用します。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-245">Logins to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="e7b7d-246">この認証方法を選択した場合は、適切な **[ユーザー名]** および **[パスワード]** を入力してください。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-246">If this method of authentication is selected, enter the appropriate **User name** and **Password**.</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="e7b7d-247">認証は旧バージョンとの互換性を維持するために提供されます。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-247">Authentication is provided for backward compatibility.</span></span> <span data-ttu-id="e7b7d-248">セキュリティを向上させるためには、可能な限り、Windows 認証を使用してください。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-248">For improved security, use Windows Authentication if possible.</span></span>  
  
 <span data-ttu-id="e7b7d-249">**Package**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-249">**Package**</span></span>  
 <span data-ttu-id="e7b7d-250">パッケージの場所を入力します。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-250">Type the location of the package.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="e7b7d-251">パスワードで保護された [!INCLUDE[ssIS](../../includes/ssis-md.md)] パッケージについては、 **[構成]** タブをクリックし、 **[パッケージ パスワード]** ダイアログ ボックスにパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-251">For password-protected [!INCLUDE[ssIS](../../includes/ssis-md.md)] packages, click the **Configurations** tab to enter the password in the **Package Password** dialog box.</span></span> <span data-ttu-id="e7b7d-252">入力しないと、パスワードで保護されたパッケージを実行する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブは失敗します。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-252">Otherwise, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job that executes the password-protected package will fail.</span></span>  
  
### <a name="configurations-tab"></a><span data-ttu-id="e7b7d-253">[構成] タブ</span><span class="sxs-lookup"><span data-stu-id="e7b7d-253">Configurations Tab</span></span>  
 <span data-ttu-id="e7b7d-254">[!INCLUDE[ssIS](../../includes/ssis-md.md)] パッケージの構成オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-254">Specify configuration options for the [!INCLUDE[ssIS](../../includes/ssis-md.md)] package.</span></span> <span data-ttu-id="e7b7d-255">このタブを選択すると、次のオプションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-255">The following options are available when this tab is selected.</span></span>  
  
 <span data-ttu-id="e7b7d-256">**構成ファイル**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-256">**Configuration files**</span></span>  
 <span data-ttu-id="e7b7d-257">パッケージの構成ファイルを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-257">Lists the configuration files for the package.</span></span>  
  
 <span data-ttu-id="e7b7d-258">**[追加]**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-258">**Add**</span></span>  
 <span data-ttu-id="e7b7d-259">パッケージの構成ファイルを追加します。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-259">Add a configuration file for the package.</span></span>  
  
 <span data-ttu-id="e7b7d-260">**削除**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-260">**Remove**</span></span>  
 <span data-ttu-id="e7b7d-261">パッケージの構成ファイルを削除します。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-261">Remove a configuration file for the package.</span></span>  
  
 <span data-ttu-id="e7b7d-262">**[上へ移動]**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-262">**Move Up**</span></span>  
 <span data-ttu-id="e7b7d-263">選択された構成ファイルを上へ移動します。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-263">Move the selected configuration file up.</span></span>  
  
 <span data-ttu-id="e7b7d-264">**[下へ移動]**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-264">**Move Down**</span></span>  
 <span data-ttu-id="e7b7d-265">選択された構成ファイルを下へ移動します。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-265">Move the selected configuration file down.</span></span>  
  
### <a name="command-files-tab"></a><span data-ttu-id="e7b7d-266">[コマンド ファイル] タブ</span><span class="sxs-lookup"><span data-stu-id="e7b7d-266">Command Files Tab</span></span>  
 <span data-ttu-id="e7b7d-267">パッケージのコマンド ファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-267">Select command files for the package.</span></span> <span data-ttu-id="e7b7d-268">コマンド ファイルは、一覧に表示されている順番で処理されます。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-268">Command files are processed in the order in which they appear in the list.</span></span> <span data-ttu-id="e7b7d-269">このタブを選択するとき、次のオプションを利用できます。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-269">The following options are available when you select this tab.</span></span>  
  
 <span data-ttu-id="e7b7d-270">**[コマンド ファイル]**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-270">**Command files**</span></span>  
 <span data-ttu-id="e7b7d-271">パッケージのコマンド ファイルを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-271">Lists the command files for the package.</span></span>  
  
 <span data-ttu-id="e7b7d-272">**[追加]**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-272">**Add**</span></span>  
 <span data-ttu-id="e7b7d-273">コマンド ファイルを追加します。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-273">Add a command file.</span></span>  
  
 <span data-ttu-id="e7b7d-274">**削除**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-274">**Remove**</span></span>  
 <span data-ttu-id="e7b7d-275">選択されたコマンド ファイルを削除します。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-275">Remove the selected command file.</span></span>  
  
 <span data-ttu-id="e7b7d-276">**[上へ移動]**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-276">**Move Up**</span></span>  
 <span data-ttu-id="e7b7d-277">選択されたコマンド ファイルを上へ移動します。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-277">Move the selected command file up.</span></span>  
  
 <span data-ttu-id="e7b7d-278">**[下へ移動]**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-278">**Move Down**</span></span>  
 <span data-ttu-id="e7b7d-279">選択されたコマンド ファイルを下へ移動します。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-279">Move the selected command file down.</span></span>  
  
### <a name="data-sources-tab"></a><span data-ttu-id="e7b7d-280">[データ ソース] タブ</span><span class="sxs-lookup"><span data-stu-id="e7b7d-280">Data Sources Tab</span></span>  
 <span data-ttu-id="e7b7d-281">パッケージの指定されたデータ ソースを表示します。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-281">View the data sources specified in the package on this tab.</span></span>  
  
 <span data-ttu-id="e7b7d-282">**接続マネージャー**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-282">**Connection Manager**</span></span>  
 <span data-ttu-id="e7b7d-283">データ ソースの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-283">View the name of the data source.</span></span>  
  
 <span data-ttu-id="e7b7d-284">**説明**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-284">**Description**</span></span>  
 <span data-ttu-id="e7b7d-285">データ ソースの記述を表示します。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-285">View the description of the data source.</span></span>  
  
 <span data-ttu-id="e7b7d-286">**接続文字列**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-286">**Connection String**</span></span>  
 <span data-ttu-id="e7b7d-287">データ ソースの接続文字列を表示します。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-287">View the connection string for the data source.</span></span>  
  
### <a name="execution-options-tab"></a><span data-ttu-id="e7b7d-288">[実行オプション] タブ</span><span class="sxs-lookup"><span data-stu-id="e7b7d-288">Execution Options Tab</span></span>  
 <span data-ttu-id="e7b7d-289">パッケージの実行オプションを表示または変更します。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-289">View or change the execution options for the package on this tab.</span></span>  
  
 <span data-ttu-id="e7b7d-290">**[検証時に警告が発生したらパッケージを失敗とする]**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-290">**Fail package on validation warnings**</span></span>  
 <span data-ttu-id="e7b7d-291">このオプションをオンにした場合、検証時に警告が発生するとパッケージの実行は失敗となります。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-291">Select this option for package execution to fail if validation warnings occur.</span></span>  
  
 <span data-ttu-id="e7b7d-292">**[パッケージを実行せずに検証する]**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-292">**Validate package without executing**</span></span>  
 <span data-ttu-id="e7b7d-293">このオプションをジョブ ステップに設定すると、パッケージは検証されますが実行されません。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-293">Select this option for the job step to validate, but not execute, the package.</span></span>  
  
 <span data-ttu-id="e7b7d-294">**[同時実行するファイルの最大数]**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-294">**Maximum concurrent executables**</span></span>  
 <span data-ttu-id="e7b7d-295">一度に実行できる実行ファイルの最大数です。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-295">Maximum number of executable files that can run at one time.</span></span>  
  
 <span data-ttu-id="e7b7d-296">**[パッケージのチェックポイントを有効にする]**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-296">**Enable package checkpoints**</span></span>  
 <span data-ttu-id="e7b7d-297">このオプションをジョブ ステップに設定すると、パッケージのチェックポイントが使用されます。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-297">Select this option for the job step to use package checkpoints.</span></span>  
  
 <span data-ttu-id="e7b7d-298">**[チェックポイント ファイル]**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-298">**Checkpoint file**</span></span>  
 <span data-ttu-id="e7b7d-299">パッケージ チェックポイント ファイルの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-299">Type the name of the package checkpoint file.</span></span>  
  
 <span data-ttu-id="e7b7d-300">**...**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-300">**...**</span></span>  
 <span data-ttu-id="e7b7d-301">パッケージ チェックポイント ファイルを参照して指定します。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-301">Browse to find the package checkpoint file.</span></span>  
  
 <span data-ttu-id="e7b7d-302">**[再開オプションをオーバーライドする]**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-302">**Override restart options**</span></span>  
 <span data-ttu-id="e7b7d-303">このオプションをオンにすると、このジョブ ステップに対して、パッケージに指定された再開オプションと異なる再開オプションを指定できます。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-303">Select this option to specify restart options for this job step that are different from the restart options specified in the package.</span></span>  
  
 <span data-ttu-id="e7b7d-304">**[再開オプション]**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-304">**Restart option**</span></span>  
 <span data-ttu-id="e7b7d-305">パッケージを再開するときに実行するアクションを選択します。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-305">Select the action to take when the package restarts.</span></span>  
  
### <a name="logging-tab"></a><span data-ttu-id="e7b7d-306">[ログ記録] タブ</span><span class="sxs-lookup"><span data-stu-id="e7b7d-306">Logging Tab</span></span>  
 <span data-ttu-id="e7b7d-307">パッケージのログ プロバイダーを表示または変更します。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-307">View or change the log providers for the package on this tab.</span></span>  
  
 <span data-ttu-id="e7b7d-308">**ログプロバイダー**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-308">**Log Provider**</span></span>  
 <span data-ttu-id="e7b7d-309">ログ プロバイダーの ClassID を選択します。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-309">Select the ClassID for the log provider.</span></span>  
  
 <span data-ttu-id="e7b7d-310">**[構成文字列]**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-310">**Configuration String**</span></span>  
 <span data-ttu-id="e7b7d-311">ログ プロバイダーの構成文字列を入力します。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-311">Type the configuration string for the log provider.</span></span>  
  
 <span data-ttu-id="e7b7d-312">**削除**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-312">**Remove**</span></span>  
 <span data-ttu-id="e7b7d-313">ログ プロバイダーを削除します。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-313">Removes the log provider.</span></span>  
  
### <a name="set-values-tab"></a><span data-ttu-id="e7b7d-314">[値の設定] タブ</span><span class="sxs-lookup"><span data-stu-id="e7b7d-314">Set Values Tab</span></span>  
 <span data-ttu-id="e7b7d-315">パッケージのプロパティ値を表示または変更します。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-315">View or change property values for the package on this tab.</span></span>  
  
 <span data-ttu-id="e7b7d-316">**[プロパティのパス]**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-316">**Property path**</span></span>  
 <span data-ttu-id="e7b7d-317">プロパティのパスを表示または変更します。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-317">View or change the path for the property.</span></span>  
  
 <span data-ttu-id="e7b7d-318">**Value**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-318">**Value**</span></span>  
 <span data-ttu-id="e7b7d-319">プロパティの値を表示または変更します。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-319">View or change the value for the property.</span></span>  
  
 <span data-ttu-id="e7b7d-320">**削除**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-320">**Remove**</span></span>  
 <span data-ttu-id="e7b7d-321">プロパティを削除します。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-321">Removes the property.</span></span>  
  
### <a name="verification-tab"></a><span data-ttu-id="e7b7d-322">[検証] タブ</span><span class="sxs-lookup"><span data-stu-id="e7b7d-322">Verification Tab</span></span>  
 <span data-ttu-id="e7b7d-323">ジョブ ステップの検証オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-323">Select the verification options for the job step on this tab.</span></span>  
  
 <span data-ttu-id="e7b7d-324">**[署名付きパッケージのみ実行する]**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-324">**Execute only signed packages**</span></span>  
 <span data-ttu-id="e7b7d-325">署名されたパッケージのみ実行します。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-325">Run only packages that have been signed.</span></span> <span data-ttu-id="e7b7d-326">このオプションがオンになっていると、パッケージが署名されていない場合はジョブ ステップが失敗します。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-326">When this option is selected, the job step fails if the package is unsigned.</span></span>  
  
 <span data-ttu-id="e7b7d-327">**パッケージのビルドを検証する**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-327">**Verify package build**</span></span>  
 <span data-ttu-id="e7b7d-328">特定のビルド番号のパッケージのみを実行します。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-328">Run only packages with a specific build number.</span></span> <span data-ttu-id="e7b7d-329">このオプションがオンになっていると、パッケージのビルド番号が指定された番号と異なる場合は、ジョブ ステップが失敗します。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-329">When this option is selected, the job step fails if the package does not have the specified build number.</span></span>  
  
 <span data-ttu-id="e7b7d-330">**ビルド**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-330">**Build**</span></span>  
 <span data-ttu-id="e7b7d-331">パッケージのビルド番号を入力します。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-331">Type the build number of the package.</span></span>  
  
 <span data-ttu-id="e7b7d-332">**[パッケージ ID を確認する]**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-332">**Verify package ID**</span></span>  
 <span data-ttu-id="e7b7d-333">特定の ID を持つパッケージのみ実行します。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-333">Run only packages with a specific ID.</span></span> <span data-ttu-id="e7b7d-334">このオプションがオンになっていると、パッケージの ID が指定の ID と異なる場合は、ジョブ ステップが失敗します。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-334">When this option is selected, the job step fails if the package does not have the specified ID.</span></span>  
  
 <span data-ttu-id="e7b7d-335">**[パッケージ ID]**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-335">**Package ID**</span></span>  
 <span data-ttu-id="e7b7d-336">パッケージ ID を入力します。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-336">Type the package ID.</span></span>  
  
 <span data-ttu-id="e7b7d-337">**[バージョン ID を確認する]**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-337">**Verify version ID**</span></span>  
 <span data-ttu-id="e7b7d-338">特定のバージョン ID を持つパッケージのみ実行します。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-338">Run only packages with a specific version ID.</span></span> <span data-ttu-id="e7b7d-339">このオプションがオンになっていると、パッケージのバージョン ID が指定の ID と異なる場合は、ジョブ ステップが失敗します。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-339">When this option is selected, the job step fails if the package does not have the specified version ID.</span></span>  
  
 <span data-ttu-id="e7b7d-340">**バージョン ID**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-340">**Version ID**</span></span>  
 <span data-ttu-id="e7b7d-341">バージョン ID を入力します。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-341">Type the version ID.</span></span>  
  
### <a name="command-line-tab"></a><span data-ttu-id="e7b7d-342">[コマンド ライン] タブ</span><span class="sxs-lookup"><span data-stu-id="e7b7d-342">Command Line Tab</span></span>  
 <span data-ttu-id="e7b7d-343">パッケージのコマンド ライン オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-343">Specify command-line options for the package.</span></span> <span data-ttu-id="e7b7d-344">このタブを選択すると、次のオプションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-344">The following options are available when this tab is selected.</span></span>  
  
 <span data-ttu-id="e7b7d-345">**[元のオプションを復元する]**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-345">**Restore the original options**</span></span>  
 <span data-ttu-id="e7b7d-346">このダイアログで設定したコマンド ライン オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-346">Use the command-line options set in this dialog.</span></span>  
  
 <span data-ttu-id="e7b7d-347">**[コマンド ラインを手動で編集する]**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-347">**Edit the command line manually**</span></span>  
 <span data-ttu-id="e7b7d-348">コマンド ライン ウィンドウでオプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-348">Specify options in the command-line window.</span></span>  
  
 <span data-ttu-id="e7b7d-349">**コマンド ライン**</span><span class="sxs-lookup"><span data-stu-id="e7b7d-349">**Command line**</span></span>  
 <span data-ttu-id="e7b7d-350">このパッケージに使用するコマンド ライン オプションを入力します。</span><span class="sxs-lookup"><span data-stu-id="e7b7d-350">Type the command line options to use for this package.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7b7d-351">参照</span><span class="sxs-lookup"><span data-stu-id="e7b7d-351">See Also</span></span>  
 <span data-ttu-id="e7b7d-352">[ジョブ ステップの管理](manage-job-steps.md) </span><span class="sxs-lookup"><span data-stu-id="e7b7d-352">[Manage Job Steps](manage-job-steps.md) </span></span>  
 <span data-ttu-id="e7b7d-353">[パッケージの SQL Server エージェントジョブ](../../integration-services/packages/sql-server-agent-jobs-for-packages.md) </span><span class="sxs-lookup"><span data-stu-id="e7b7d-353">[SQL Server Agent Jobs for Packages](../../integration-services/packages/sql-server-agent-jobs-for-packages.md) </span></span>  
 [<span data-ttu-id="e7b7d-354">レプリケーション エージェントの管理</span><span class="sxs-lookup"><span data-stu-id="e7b7d-354">Replication Agent Administration</span></span>](../../relational-databases/replication/agents/replication-agent-administration.md)  
  
  
