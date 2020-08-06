---
title: SQL Server エージェントでの Windows PowerShell ステップの実行 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: scripting
ms.topic: conceptual
ms.assetid: f25f7549-c9b3-4618-85f2-c9a08adbe0e3
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8c100e2eaf1f9b706087bd991fbc268540c29a46
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640107"
---
# <a name="run-windows-powershell-steps-in-sql-server-agent"></a><span data-ttu-id="b3c9a-102">SQL Server エージェントでの Windows PowerShell ステップの実行</span><span class="sxs-lookup"><span data-stu-id="b3c9a-102">Run Windows PowerShell Steps in SQL Server Agent</span></span>
  <span data-ttu-id="b3c9a-103">SQL Server エージェントを使用して、スケジュールされた時刻に SQL Server PowerShell スクリプトを実行します。</span><span class="sxs-lookup"><span data-stu-id="b3c9a-103">Use SQL Server Agent to run SQL Server PowerShell scripts at schedule times.</span></span>  
  
1.  <span data-ttu-id="b3c9a-104">**作業を開始する準備:**  [制限事項と制約事項](#LimitationsRestrictions)</span><span class="sxs-lookup"><span data-stu-id="b3c9a-104">**Before you begin:**  [Limitations and Restrictions](#LimitationsRestrictions)</span></span>  
  
2.  <span data-ttu-id="b3c9a-105">**SQL Server エージェントから PowerShell を実行するには:** [PowerShell ジョブ ステップ](#PShellJob)、[コマンド プロンプト ジョブ ステップ](#CmdExecJob)</span><span class="sxs-lookup"><span data-stu-id="b3c9a-105">**To run PowerShell from SQL Server Agent, using:**  [PowerShell Job Step](#PShellJob), [Command Prompt Job Step](#CmdExecJob)</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="b3c9a-106">はじめに</span><span class="sxs-lookup"><span data-stu-id="b3c9a-106">Before You Begin</span></span>  
 <span data-ttu-id="b3c9a-107">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エージェントのジョブ ステップにはいくつかの種類があります。</span><span class="sxs-lookup"><span data-stu-id="b3c9a-107">There are several types of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent job steps.</span></span> <span data-ttu-id="b3c9a-108">それぞれの種類は、レプリケーション エージェントやコマンド プロンプト環境など、特定の環境を実装するサブシステムに関連付けられています。</span><span class="sxs-lookup"><span data-stu-id="b3c9a-108">Each type is associated with a subsystem that implements a specific environment, such as a replication agent or command prompt environment.</span></span> <span data-ttu-id="b3c9a-109">Windows PowerShell スクリプトのコードを作成した後、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エージェントを使用して、スケジュールされた時刻に実行されるジョブや [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] イベントに応答して実行されるジョブにそのスクリプトを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="b3c9a-109">You can code Windows PowerShell scripts, and then use [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent to include the scripts in jobs that run at scheduled times or in response to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] events.</span></span> <span data-ttu-id="b3c9a-110">コマンド プロンプト ジョブ ステップまたは PowerShell ジョブ ステップを使用して、Windows PowerShell スクリプトを実行できます。</span><span class="sxs-lookup"><span data-stu-id="b3c9a-110">Windows PowerShell scripts can be run using either a command prompt job step or a PowerShell job step.</span></span>  
  
1.  <span data-ttu-id="b3c9a-111">PowerShell ジョブ ステップを使用して [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エージェント サブシステムに `sqlps` ユーティリティを実行させる。このユーティリティは、PowerShell 2.0 を起動し、`sqlps` モジュールをインポートする。</span><span class="sxs-lookup"><span data-stu-id="b3c9a-111">Use a PowerShell job step to have the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent subsystem run the `sqlps` utility, which launches PowerShell 2.0 and imports the `sqlps` module.</span></span>  
  
2.  <span data-ttu-id="b3c9a-112">コマンド プロンプト ジョブ ステップを使用して PowerShell.exe を実行し、`sqlps` モジュールをインポートするスクリプトを指定する。</span><span class="sxs-lookup"><span data-stu-id="b3c9a-112">Use a command prompt job step to run PowerShell.exe, and specify a script that imports the `sqlps` module.</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> <span data-ttu-id="b3c9a-113">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="b3c9a-113">Limitations and Restrictions</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="b3c9a-114">`sqlps` モジュールで PowerShell を実行する [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エージェント ジョブ ステップでは、それぞれ、約 20 MB のメモリを消費するプロセスが起動されます。</span><span class="sxs-lookup"><span data-stu-id="b3c9a-114">Each [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent job step that runs PowerShell with the `sqlps` module launches a process which consumes approximately 20 MB of memory.</span></span> <span data-ttu-id="b3c9a-115">大量の Windows PowerShell ジョブ ステップを同時実行すると、パフォーマンスに悪影響が及びます。</span><span class="sxs-lookup"><span data-stu-id="b3c9a-115">Running large numbers of concurrent Windows PowerShell job steps can adversely impact performance.</span></span>  
  
##  <a name="create-a-powershell-job-step"></a><a name="PShellJob"></a><span data-ttu-id="b3c9a-116">PowerShell ジョブステップの作成</span><span class="sxs-lookup"><span data-stu-id="b3c9a-116">Create a PowerShell Job Step</span></span>  
 <span data-ttu-id="b3c9a-117">**PowerShell ジョブ ステップを作成するには**</span><span class="sxs-lookup"><span data-stu-id="b3c9a-117">**To create a PowerShell job step**</span></span>  
  
1.  <span data-ttu-id="b3c9a-118">**[SQL Server エージェント]** を展開し、新しいジョブを作成するか、既存のジョブを右クリックして **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b3c9a-118">Expand **SQL Server Agent**, create a new job or right-click an existing job, and then click **Properties**.</span></span> <span data-ttu-id="b3c9a-119">ジョブの作成に関する詳細については、「 [ジョブの作成](../ssms/agent/create-jobs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b3c9a-119">For more information about creating a job, see [Creating Jobs](../ssms/agent/create-jobs.md).</span></span>  
  
2.  <span data-ttu-id="b3c9a-120">**[ジョブのプロパティ]** ダイアログで **[ステップ]** ページをクリックし、 **[新規作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b3c9a-120">In the **Job Properties** dialog, click the **Steps** page, and then click **New**.</span></span>  
  
3.  <span data-ttu-id="b3c9a-121">**[新しいジョブ ステップ]** ダイアログの **[ステップ名]** ボックスにジョブ ステップ名を入力します。</span><span class="sxs-lookup"><span data-stu-id="b3c9a-121">In the **New Job Step** dialog, type a job **Step name**.</span></span>  
  
4.  <span data-ttu-id="b3c9a-122">**[種類]** ボックスの一覧で **[PowerShell]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b3c9a-122">In the **Type** list, click **PowerShell**.</span></span>  
  
5.  <span data-ttu-id="b3c9a-123">**[実行するアカウント名]** ボックスの一覧で、ジョブで使用する資格情報を備えたプロキシ アカウントをクリックします。</span><span class="sxs-lookup"><span data-stu-id="b3c9a-123">In the **Run as** list, select the proxy account with the credentials that the job will use.</span></span>  
  
6.  <span data-ttu-id="b3c9a-124">**[コマンド]** ボックスに、ジョブ ステップで実行する PowerShell スクリプト構文を入力します。</span><span class="sxs-lookup"><span data-stu-id="b3c9a-124">In the **Command** box, enter the PowerShell script syntax that will be executed for the job step.</span></span> <span data-ttu-id="b3c9a-125">または、 **[開く]** をクリックしてスクリプト構文が記述されたファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="b3c9a-125">Alternately, click **Open** and select a file containing the script syntax.</span></span>  
  
7.  <span data-ttu-id="b3c9a-126">**[詳細設定]** ページをクリックして、ジョブ ステップのオプションのうち、ジョブ ステップが成功または失敗した場合のアクション、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エージェントによるジョブ ステップの再試行回数、および再試行間隔を設定します。</span><span class="sxs-lookup"><span data-stu-id="b3c9a-126">Click the **Advanced** page to set the following job step options: what action to take if the job step succeeds or fails, how many times [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent should try to execute the job step, and how often retry attempts should be made.</span></span>  
  
##  <a name="create-a-command-prompt-job-step"></a><a name="CmdExecJob"></a><span data-ttu-id="b3c9a-127">コマンドプロンプトジョブステップの作成</span><span class="sxs-lookup"><span data-stu-id="b3c9a-127">Create a Command Prompt Job Step</span></span>  
 <span data-ttu-id="b3c9a-128">**CmdExec ジョブ ステップを作成するには**</span><span class="sxs-lookup"><span data-stu-id="b3c9a-128">**To create a CmdExec job step**</span></span>  
  
1.  <span data-ttu-id="b3c9a-129">**[SQL Server エージェント]** を展開し、新しいジョブを作成するか、既存のジョブを右クリックして **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b3c9a-129">Expand **SQL Server Agent**, create a new job or right-click an existing job, and then click **Properties**.</span></span> <span data-ttu-id="b3c9a-130">ジョブの作成に関する詳細については、「 [ジョブの作成](../ssms/agent/create-jobs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b3c9a-130">For more information about creating a job, see [Creating Jobs](../ssms/agent/create-jobs.md).</span></span>  
  
2.  <span data-ttu-id="b3c9a-131">**[ジョブのプロパティ]** ダイアログで **[ステップ]** ページをクリックし、 **[新規作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b3c9a-131">In the **Job Properties** dialog, click the **Steps** page, and then click **New**.</span></span>  
  
3.  <span data-ttu-id="b3c9a-132">**[新しいジョブ ステップ]** ダイアログの **[ステップ名]** ボックスにジョブ ステップ名を入力します。</span><span class="sxs-lookup"><span data-stu-id="b3c9a-132">In the **New Job Step** dialog, type a job **Step name**.</span></span>  
  
4.  <span data-ttu-id="b3c9a-133">**[種類]** ボックスの一覧の **[オペレーティング システム (CmdExec)]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b3c9a-133">In the **Type** list, choose **Operating system (CmdExec)**.</span></span>  
  
5.  <span data-ttu-id="b3c9a-134">**[実行するアカウント名]** ボックスの一覧で、ジョブで使用する資格情報を備えたプロキシ アカウントをクリックします。</span><span class="sxs-lookup"><span data-stu-id="b3c9a-134">In **Run as** list, select the proxy account with the credentials that the job will use.</span></span> <span data-ttu-id="b3c9a-135">既定では、CmdExec ジョブ ステップは SQL Server エージェント サービス アカウントのコンテキストで実行されます。</span><span class="sxs-lookup"><span data-stu-id="b3c9a-135">By default, CmdExec job steps run under the context of the SQL Server Agent service account.</span></span>  
  
6.  <span data-ttu-id="b3c9a-136">**[コマンド成功時のプロセス終了コード]** ボックスに、0 ～ 999999 の値を入力します。</span><span class="sxs-lookup"><span data-stu-id="b3c9a-136">In the **Process exit code of a successful command** box, enter a value from 0 to 999999.</span></span>  
  
7.  <span data-ttu-id="b3c9a-137">**[コマンド]** ボックスに、実行する PowerShell スクリプトを指定するパラメーターと共に powershell.exe を入力します。</span><span class="sxs-lookup"><span data-stu-id="b3c9a-137">In the **Command** box, enter powershell.exe with parameters specifying the PowerShell script to be run.</span></span>  
  
8.  <span data-ttu-id="b3c9a-138">**[詳細設定]** ページをクリックして、ジョブが成功または失敗した場合の操作、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エージェントによるジョブ ステップ実行の試行回数、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エージェントでジョブ ステップの出力を書き込むファイルなど、ジョブ ステップのオプションを設定します。</span><span class="sxs-lookup"><span data-stu-id="b3c9a-138">Click the **Advanced** page to set job step options, such as: what action to take if the job step succeeds or fails, how many times [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent should try to execute the job step, and the file where [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent can write the job step output.</span></span> <span data-ttu-id="b3c9a-139">**sysadmin** 固定サーバー ロールのメンバーだけが、オペレーティング システム ファイルにジョブ ステップの出力を書き込むことができます。</span><span class="sxs-lookup"><span data-stu-id="b3c9a-139">Only members of the **sysadmin** fixed server role can write job step output to an operating system file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3c9a-140">参照</span><span class="sxs-lookup"><span data-stu-id="b3c9a-140">See Also</span></span>  
 [<span data-ttu-id="b3c9a-141">SQL Server PowerShell</span><span class="sxs-lookup"><span data-stu-id="b3c9a-141">SQL Server PowerShell</span></span>](sql-server-powershell.md)  
  
  
