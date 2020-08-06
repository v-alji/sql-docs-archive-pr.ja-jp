---
title: パッケージに対する SQL Server エージェント ジョブ | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- jobs [Integration Services]
- automatic package execution
- scheduling packages [Integration Services]
- SQL Server Agent [Integration Services]
ms.assetid: ecf7a5f9-b8a7-47f1-9ac0-bac07cb89e31
author: chugugrace
ms.author: chugu
ms.openlocfilehash: eb9c1cf39ab5120958c33dfeff24588d59f71307
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641047"
---
# <a name="sql-server-agent-jobs-for-packages"></a><span data-ttu-id="78ac2-102">パッケージに対する SQL Server エージェント ジョブ</span><span class="sxs-lookup"><span data-stu-id="78ac2-102">SQL Server Agent Jobs for Packages</span></span>
  <span data-ttu-id="78ac2-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントを使用して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージの実行を自動化およびスケジュール設定できます。</span><span class="sxs-lookup"><span data-stu-id="78ac2-103">You can automate and schedule the execution of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span> <span data-ttu-id="78ac2-104">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サーバーに配置されているパッケージ、および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、 [!INCLUDE[ssIS](../../includes/ssis-md.md)] パッケージ ストア、ファイル システムに格納されているパッケージのスケジュールを設定できます。</span><span class="sxs-lookup"><span data-stu-id="78ac2-104">You can schedule packages that are deployed to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server, and are stored in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the [!INCLUDE[ssIS](../../includes/ssis-md.md)] Package Store, and the file system.</span></span>  
  
## <a name="sections-in-this-topic"></a><span data-ttu-id="78ac2-105">このトピックのセクション</span><span class="sxs-lookup"><span data-stu-id="78ac2-105">Sections in This Topic</span></span>  
 <span data-ttu-id="78ac2-106">このトピックには、次のセクションが含まれます。</span><span class="sxs-lookup"><span data-stu-id="78ac2-106">This topic contains the following sections:</span></span>  
  
-   [<span data-ttu-id="78ac2-107">SQL Server エージェントでのジョブのスケジュール設定</span><span class="sxs-lookup"><span data-stu-id="78ac2-107">Scheduling jobs in SQL Server Agent</span></span>](#jobs)  
  
-   [<span data-ttu-id="78ac2-108">Integration Services パッケージのスケジュール設定</span><span class="sxs-lookup"><span data-stu-id="78ac2-108">Scheduling Integration Services packages</span></span>](#packages)  
  
-   [<span data-ttu-id="78ac2-109">スケジュールされたパッケージのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="78ac2-109">Troubleshooting scheduled packages</span></span>](#trouble)  
  
##  <a name="scheduling-jobs-in-sql-server-agent"></a><a name="jobs"></a> <span data-ttu-id="78ac2-110">Scheduling Jobs in SQL Server Agent</span><span class="sxs-lookup"><span data-stu-id="78ac2-110">Scheduling Jobs in SQL Server Agent</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="78ac2-111">エージェントとは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブを実行してタスクの自動化とスケジュール設定を可能にする、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によってインストールされるサービスです。</span><span class="sxs-lookup"><span data-stu-id="78ac2-111">Agent is the service installed by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that lets you automate and schedule tasks by running [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs.</span></span> <span data-ttu-id="78ac2-112">ジョブを自動的に実行できるようにするには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービスを実行している必要があります。</span><span class="sxs-lookup"><span data-stu-id="78ac2-112">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service must be running before jobs can run automatically.</span></span> <span data-ttu-id="78ac2-113">詳細については、「 [Configure SQL Server Agent](../../ssms/agent/configure-sql-server-agent.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="78ac2-113">For more information, see [Configure SQL Server Agent](../../ssms/agent/configure-sql-server-agent.md).</span></span>  
  
 <span data-ttu-id="78ac2-114">**のインスタンスに接続すると、** のオブジェクト エクスプローラーに [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [SQL Server エージェント] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]ノードが表示されます。</span><span class="sxs-lookup"><span data-stu-id="78ac2-114">The **SQL Server Agent** node appears in Object Explorer in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] when you connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span>  
  
 <span data-ttu-id="78ac2-115">定期的なタスクを自動化するには、 **[新しいジョブ]** ダイアログ ボックスを使用してジョブを作成します。</span><span class="sxs-lookup"><span data-stu-id="78ac2-115">To automate a recurring task, you create a job by using the **New Job** dialog box.</span></span> <span data-ttu-id="78ac2-116">詳細については、 [「ジョブの実装」](../../ssms/agent/implement-jobs.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="78ac2-116">For more information, see [Implement Jobs](../../ssms/agent/implement-jobs.md).</span></span>  
  
 <span data-ttu-id="78ac2-117">ジョブを作成した後は、少なくとも 1 つのステップを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="78ac2-117">After you create the job, you must add at least one step.</span></span> <span data-ttu-id="78ac2-118">1 つのジョブに複数のステップを含め、それぞれのステップで異なるタスクを実行できます。</span><span class="sxs-lookup"><span data-stu-id="78ac2-118">A job can include multiple steps, and each step can perform a different task.</span></span> <span data-ttu-id="78ac2-119">詳細については、 [ジョブ ステップの管理](../../ssms/agent/manage-job-steps.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="78ac2-119">For more information, see [Manage Job Steps](../../ssms/agent/manage-job-steps.md).</span></span>  
  
 <span data-ttu-id="78ac2-120">ジョブとジョブ ステップを作成した後は、ジョブを実行するためのスケジュールを作成できます。</span><span class="sxs-lookup"><span data-stu-id="78ac2-120">After you create the job and the job steps, you can create a schedule for running the job.</span></span> <span data-ttu-id="78ac2-121">また、手動で実行する、スケジュールされていないジョブも作成できます。</span><span class="sxs-lookup"><span data-stu-id="78ac2-121">However you can also create an unscheduled job that you run manually.</span></span> <span data-ttu-id="78ac2-122">詳細については、「 [スケジュールの作成とジョブへのアタッチ](../../ssms/agent/create-and-attach-schedules-to-jobs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="78ac2-122">For more information, see [Create and Attach Schedules to Jobs](../../ssms/agent/create-and-attach-schedules-to-jobs.md).</span></span>  
  
 <span data-ttu-id="78ac2-123">ジョブ完了時にオペレーターへ電子メール メッセージを送信する通知オプションなどの設定、警告の追加を行い、ジョブを拡張できます。</span><span class="sxs-lookup"><span data-stu-id="78ac2-123">You can enhance the job by setting notification options, such as specifying an operator to send an e-mail message to when the job finishes, or adding alerts.</span></span> <span data-ttu-id="78ac2-124">詳細については、「 [警告](../../ssms/agent/alerts.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="78ac2-124">For more information, see [Alerts](../../ssms/agent/alerts.md).</span></span>  
  
##  <a name="scheduling-integration-services-packages"></a><a name="packages"></a> <span data-ttu-id="78ac2-125">Scheduling Integration Services Packages</span><span class="sxs-lookup"><span data-stu-id="78ac2-125">Scheduling Integration Services Packages</span></span>  
 <span data-ttu-id="78ac2-126">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブを作成して [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージのスケジュールを設定する場合は、少なくとも 1 つのステップを追加し、ステップの種類を **[SQL Server Integration Services パッケージ]** に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="78ac2-126">When you create a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job to schedule [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages, you must add at least one step and set the type of the step to **SQL Server Integration Services Package**.</span></span> <span data-ttu-id="78ac2-127">1 つのジョブに複数のステップを含め、それぞれのステップで異なるパッケージを実行できます。</span><span class="sxs-lookup"><span data-stu-id="78ac2-127">A job can include multiple steps, and each step can run a different package.</span></span>  
  
 <span data-ttu-id="78ac2-128">ジョブ ステップからの [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージの実行は、 **dtexec** ユーティリティ (dtexec.exe) および **DTExecUI** (dtexecui.exe) を使用したパッケージの実行に似ています。</span><span class="sxs-lookup"><span data-stu-id="78ac2-128">Running an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package from a job step is like running a package by using the **dtexec** (dtexec.exe) and **DTExecUI** (dtexecui.exe) utilities.</span></span> <span data-ttu-id="78ac2-129">コマンド ライン オプションまたは **[パッケージ実行ユーティリティ]** ダイアログ ボックスを使用してパッケージの実行時オプションを設定する代わりに、 **[新しいジョブ ステップ]** ダイアログ ボックスで実行時オプションを設定します。</span><span class="sxs-lookup"><span data-stu-id="78ac2-129">Instead of setting the run-time options for a package by using command-line options or the **Execute Package Utility** dialog box, you set the run-time options in the **New Job Step** dialog box.</span></span> <span data-ttu-id="78ac2-130">パッケージを実行するためのオプションの詳細については、「 [dtexec ユーティリティ](dtexec-utility.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="78ac2-130">For more information about the options for running a package, see [dtexec Utility](dtexec-utility.md).</span></span>  
  
 <span data-ttu-id="78ac2-131">詳しくは、「 [SQL Server エージェントを使用してパッケージのスケジュールを設定する](../schedule-a-package-by-using-sql-server-agent.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="78ac2-131">For more information, see [Schedule a Package by using SQL Server Agent](../schedule-a-package-by-using-sql-server-agent.md).</span></span>  
  
 <span data-ttu-id="78ac2-132">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントを使用してパッケージを実行する方法を示しているビデオについては、MSDN ライブラリのビデオのホームページの「[SQL Server エージェントを使用してパッケージ実行を自動化する方法 (SQL Server ビデオ)](https://go.microsoft.com/fwlink/?LinkId=141771)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="78ac2-132">For a video that demonstrates how to use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to run a package, see the video home page, [How to: Automate Package Execution by Using the SQL Server Agent (SQL Server Video)](https://go.microsoft.com/fwlink/?LinkId=141771), in the MSDN Library.</span></span>  
  
##  <a name="troubleshooting"></a><a name="trouble"></a> <span data-ttu-id="78ac2-133">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="78ac2-133">Troubleshooting</span></span>  
 <span data-ttu-id="78ac2-134">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのジョブ ステップは、パッケージを [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] およびコマンド ラインで正常に実行できる場合でも、パッケージの開始に失敗することがあります。</span><span class="sxs-lookup"><span data-stu-id="78ac2-134">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job step may fail to start a package even though the package runs successfully in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] and from the command line.</span></span> <span data-ttu-id="78ac2-135">この問題には、いくつかの一般的な原因と、推奨されるソリューションがあります。</span><span class="sxs-lookup"><span data-stu-id="78ac2-135">There are some common reasons for this issue and several recommended solutions.</span></span> <span data-ttu-id="78ac2-136">詳細については、次のリソースを参照してください。</span><span class="sxs-lookup"><span data-stu-id="78ac2-136">For more information, see the following resources.</span></span>  
  
-   [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="78ac2-137">サポート技術情報の記事「 [SQL Server エージェントのジョブ ステップから SSIS パッケージを呼び出したときに SSIS パッケージが実行されません](https://support.microsoft.com/kb/918760)</span><span class="sxs-lookup"><span data-stu-id="78ac2-137">Knowledge Base article, [An SSIS package does not run when you call the SSIS package from a SQL Server Agent job step](https://support.microsoft.com/kb/918760)</span></span>  
  
-   <span data-ttu-id="78ac2-138">MSDN ライブラリのビデオ「[トラブルシューティング: SQL Server エージェントを使用した SSIS パッケージ実行 (SQL Server ビデオ)](https://go.microsoft.com/fwlink/?LinkId=141772)」</span><span class="sxs-lookup"><span data-stu-id="78ac2-138">Video, [Troubleshooting: Package Execution Using SQL Server Agent (SQL Server Video)](https://go.microsoft.com/fwlink/?LinkId=141772), in the MSDN Library.</span></span>  
  
 <span data-ttu-id="78ac2-139">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのジョブ ステップがパッケージを開始した後、パッケージの実行が失敗したり、正常に実行されても予期しない結果になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="78ac2-139">After a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job step starts a package, the package execution may fail or the package may run successfully but with unexpected results.</span></span> <span data-ttu-id="78ac2-140">これらの問題のトラブルシューティングには、次のツールを使用できます。</span><span class="sxs-lookup"><span data-stu-id="78ac2-140">You can use the following tools to troubleshoot these issues.</span></span>  
  
-   <span data-ttu-id="78ac2-141">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] MSDB データベース、 [!INCLUDE[ssIS](../../includes/ssis-md.md)] パッケージ ストア、またはローカル コンピューターのフォルダーに格納されているパッケージでは、 **[ログ ファイルの表示]** と、パッケージの実行中に生成されたログおよびデバッグ ダンプ ファイルを使用できます。</span><span class="sxs-lookup"><span data-stu-id="78ac2-141">For packages that are stored in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] MSDB database, the [!INCLUDE[ssIS](../../includes/ssis-md.md)] Package Store, or in a folder on your local machine, you can use the **Log File Viewer** as well as any logs and debug dump files that were generated during the execution of the package.</span></span>  
  
     <span data-ttu-id="78ac2-142">**[ログ ファイルの表示] を使用するには、次の操作を実行します。**</span><span class="sxs-lookup"><span data-stu-id="78ac2-142">**To use the Log File Viewer, do the following.**</span></span>  
  
    1.  <span data-ttu-id="78ac2-143">オブジェクト エクスプローラーで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブを右クリックし、 **[履歴の表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="78ac2-143">Right-click the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job in Object Explorer and then click **View History**.</span></span>  
  
    2.  <span data-ttu-id="78ac2-144">**[ログ ファイルの概要]** ボックスで、 **[メッセージ]** 列に **"ジョブが失敗しました"** というメッセージが含まれているジョブ実行を探します。</span><span class="sxs-lookup"><span data-stu-id="78ac2-144">Locate the job execution in the **Log file summary** box with the **job failed** message in the **Message** column.</span></span>  
  
    3.  <span data-ttu-id="78ac2-145">ジョブ ノードを展開し、ジョブ ステップをクリックして、メッセージの詳細を **[ログ ファイルの概要]** ボックスの下の領域に表示します。</span><span class="sxs-lookup"><span data-stu-id="78ac2-145">Expand the job node, and click the job step to view the details of the message in the area below the **Log file summary** box.</span></span>  
  
-   <span data-ttu-id="78ac2-146">SSISDB データベースに格納されているパッケージでも、 **[ログ ファイルの表示]** と、パッケージの実行中に生成されたログおよびデバッグ ダンプ ファイルを使用できます。</span><span class="sxs-lookup"><span data-stu-id="78ac2-146">For packages that are stored in the SSISDB database, you can also use the **Log File Viewer** as well as any logs and debug dump files that were generated during the execution of the package.</span></span> <span data-ttu-id="78ac2-147">また、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サーバーのレポートを使用できます。</span><span class="sxs-lookup"><span data-stu-id="78ac2-147">In addition, you can use the reports for the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server.</span></span>  
  
     <span data-ttu-id="78ac2-148">**レポートでジョブ実行に関連するパッケージ実行の情報を探すには、次の操作を行います。**</span><span class="sxs-lookup"><span data-stu-id="78ac2-148">**To find information in the reports for the package execution associated with a job execution, do the following.**</span></span>  
  
    1.  <span data-ttu-id="78ac2-149">上記の手順に従って、ジョブ ステップのメッセージの詳細を表示します。</span><span class="sxs-lookup"><span data-stu-id="78ac2-149">Follow the steps above to view the details of the message for the job step.</span></span>  
  
    2.  <span data-ttu-id="78ac2-150">メッセージに記載されている実行 ID を探します。</span><span class="sxs-lookup"><span data-stu-id="78ac2-150">Locate the Execution ID listed in the message.</span></span>  
  
    3.  <span data-ttu-id="78ac2-151">オブジェクト エクスプローラーで、[Integration Services カタログ] ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="78ac2-151">Expand the Integration Services Catalog node in Object Explorer.</span></span>  
  
    4.  <span data-ttu-id="78ac2-152">SSISDB を右クリックし、[レポート]、[標準レポート] の順にポイントして、[すべての実行] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="78ac2-152">Right-click SSISDB, point to Reports, then Standard Reports, and then click All Executions.</span></span>  
  
    5.  <span data-ttu-id="78ac2-153">**[すべての実行]** レポートの **[ID]** 列で、実行 ID を探します。</span><span class="sxs-lookup"><span data-stu-id="78ac2-153">In the **All Executions** report, locate the Execution ID in the **ID** column.</span></span> <span data-ttu-id="78ac2-154">**[概要]** 、 **[すべてのメッセージ]** 、または **[実行のパフォーマンス]** をクリックして、このパッケージ実行についての情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="78ac2-154">Click **Overview**, **All Messages**, or **Execution Performance** to view information about this package execution.</span></span>  
  
         <span data-ttu-id="78ac2-155">"概要"、"すべてのメッセージ"、および "実行のパフォーマンス" の各レポートの詳細については、「 [Integration Services サーバーのレポート](../reports-for-the-integration-services-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="78ac2-155">For more information about the Overview, All Messages, and Execution Performance reports, see [Reports for the Integration Services Server](../reports-for-the-integration-services-server.md).</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="78ac2-156">外部リソース</span><span class="sxs-lookup"><span data-stu-id="78ac2-156">External Resources</span></span>  
  
-   <span data-ttu-id="78ac2-157">[Web サイトのサポート技術情報の記事「](https://support.microsoft.com/kb/918760)SQL Server エージェントのジョブ ステップから SSIS パッケージを呼び出したときに SSIS パッケージが実行されません [!INCLUDE[msCoName](../../includes/msconame-md.md)] 」</span><span class="sxs-lookup"><span data-stu-id="78ac2-157">Knowledge Base article, [An SSIS package does not run when you call the SSIS package from a SQL Server Agent job step](https://support.microsoft.com/kb/918760), on the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Web site</span></span>  
  
-   <span data-ttu-id="78ac2-158">MSDN ライブラリのビデオ「[トラブルシューティング: SQL Server エージェントを使用した SSIS パッケージ実行 (SQL Server ビデオ)](https://go.microsoft.com/fwlink/?LinkId=141772)」</span><span class="sxs-lookup"><span data-stu-id="78ac2-158">Video, [Troubleshooting: Package Execution Using SQL Server Agent (SQL Server Video)](https://go.microsoft.com/fwlink/?LinkId=141772), in the MSDN Library</span></span>  
  
-   <span data-ttu-id="78ac2-159">MSDN ライブラリのビデオ「[SQL Server エージェントを使用してパッケージ実行を自動化する方法 (SQL Server ビデオ)](https://go.microsoft.com/fwlink/?LinkId=141771)」</span><span class="sxs-lookup"><span data-stu-id="78ac2-159">Video, [How to: Automate Package Execution by Using the SQL Server Agent (SQL Server Video)](https://go.microsoft.com/fwlink/?LinkId=141771), in the MSDN Library</span></span>  
  
-   <span data-ttu-id="78ac2-160">mssqltips.com の技術記事「 [Windows PowerShell を使用した SQL Server エージェント ジョブの確認](https://go.microsoft.com/fwlink/?LinkId=165675)」</span><span class="sxs-lookup"><span data-stu-id="78ac2-160">Technical article, [Checking SQL Server Agent jobs using Windows PowerShell](https://go.microsoft.com/fwlink/?LinkId=165675), on mssqltips.com</span></span>  
  
-   <span data-ttu-id="78ac2-161">mssqltips.com の技術記事「 [SQL エージェント ジョブを有効または無効にしたときの自動警告](https://go.microsoft.com/fwlink/?LinkId=165676)」</span><span class="sxs-lookup"><span data-stu-id="78ac2-161">Technical article, [Auto alert for SQL Agent jobs when they are enabled or disabled](https://go.microsoft.com/fwlink/?LinkId=165676), on mssqltips.com</span></span>  
  
-   <span data-ttu-id="78ac2-162">mssqltips.com のブログ「 [Windows イベント ログに書き込むための SQL エージェント ジョブの構成](https://go.microsoft.com/fwlink/?LinkId=220745)」</span><span class="sxs-lookup"><span data-stu-id="78ac2-162">Blog entry, [Configuring SQL Agent Jobs to Write to Windows Event Log](https://go.microsoft.com/fwlink/?LinkId=220745), on mssqltips.com.</span></span>  
  
  
