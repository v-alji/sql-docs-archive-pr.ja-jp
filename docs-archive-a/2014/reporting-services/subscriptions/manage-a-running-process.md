---
title: 実行中の処理を管理する | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- report processing [Reporting Services], status information
- jobs [Reporting Services]
- viewing jobs
- canceling jobs
- user jobs [Reporting Services]
- system jobs [Reporting Services]
- report processing [Reporting Services], managing running processes
- processes [Reporting Services]
- scanning processes [Reporting Services]
- status information [Reporting Services]
- report processing [Reporting Services]
- canceling subscriptions
- report servers [Reporting Services], jobs
- data-driven subscriptions
- displaying jobs
- subscriptions [Reporting Services], running processes
ms.assetid: 473e574e-f1ff-4ef9-bda6-7028b357ac42
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 002dda5a9708b68c6bbf978fb00e85f27b493da2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644816"
---
# <a name="manage-a-running-process"></a><span data-ttu-id="ba622-102">Manage a Running Process</span><span class="sxs-lookup"><span data-stu-id="ba622-102">Manage a Running Process</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="ba622-103">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] では、レポート サーバーで実行中のジョブの状態を監視します。</span><span class="sxs-lookup"><span data-stu-id="ba622-103">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] monitors the status of jobs that are running on the report server.</span></span> <span data-ttu-id="ba622-104">レポート サーバーは、一定の間隔で、実行中のジョブをスキャンし、レポート サーバー データベース (SharePoint モードの場合はサービス アプリケーション データベース) に状態情報を書き込みます。</span><span class="sxs-lookup"><span data-stu-id="ba622-104">At regular intervals, the report server does a scan of in-progress jobs and writes the status information to the report server database or the service application databases for SharePoint mode.</span></span> <span data-ttu-id="ba622-105">リモートまたはローカル データベース サーバーでのクエリの実行、レポート処理、およびレポート表示のいずれかが行われている場合、ジョブは実行中です。</span><span class="sxs-lookup"><span data-stu-id="ba622-105">A job is in progress if any of the following processes are underway: query execution on a remote or local database server, report processing, and report rendering.</span></span>  
  
 <span data-ttu-id="ba622-106">*ユーザー ジョブ* と *システム ジョブ*の両方を管理できます。</span><span class="sxs-lookup"><span data-stu-id="ba622-106">You can manage both *user jobs* and *system jobs*.</span></span>  
  
-   <span data-ttu-id="ba622-107">ユーザー ジョブは、各ユーザーまたはサブスクリプションによって開始されます。</span><span class="sxs-lookup"><span data-stu-id="ba622-107">User jobs are initiated by an individual user or subscription.</span></span> <span data-ttu-id="ba622-108">このジョブには、要求時のレポートの実行、レポート履歴スナップショットの要求、レポート スナップショットの手動作成、および標準のサブスクリプションの処理が含まれます。</span><span class="sxs-lookup"><span data-stu-id="ba622-108">This includes running a report on demand, requesting a report history snapshot, manually creating a report snapshot, and processing a standard subscription.</span></span>  
  
-   <span data-ttu-id="ba622-109">システム ジョブは、レポート サーバーによって開始されます。</span><span class="sxs-lookup"><span data-stu-id="ba622-109">System jobs are initiated by the report server.</span></span> <span data-ttu-id="ba622-110">システム ジョブには、スケジュールされたレポート実行スナップショット、スケジュールされたレポート履歴スナップショット、およびデータ ドリブン サブスクリプションが含まれます。</span><span class="sxs-lookup"><span data-stu-id="ba622-110">System jobs include scheduled report execution snapshots, scheduled report history snapshots, and data-driven subscriptions.</span></span>  
  
 <span data-ttu-id="ba622-111">レポートの処理時間およびリソースの使用は、レポート、クエリの複雑さ、データ量、およびレポートに対して指定された表示形式により、大きく異なります。</span><span class="sxs-lookup"><span data-stu-id="ba622-111">Report processing time and resource use varies considerably depending on the report, the query complexity, the amount of data, and the rendering format that is specified for the report.</span></span> <span data-ttu-id="ba622-112">ローカル データ ソースに対する単純なクエリを有するレポートは、通常、ミリ秒単位で完了し、管理または調整の必要はありません。</span><span class="sxs-lookup"><span data-stu-id="ba622-112">Reports that have simple queries against a local data source will often complete in milliseconds and never require management or tuning.</span></span> <span data-ttu-id="ba622-113">これに対し、PDF または Excel で表示されるサイズの大きいレポートでは、ハードウェア リソース、配信オプション、および並行して他の処理が実行されているかどうかにより、相当な処理時間を要する場合があります。</span><span class="sxs-lookup"><span data-stu-id="ba622-113">In contrast, a large report that is rendered in PDF or Excel might require significant processing time depending on hardware resources, delivery options, and whether other processes are running concurrently.</span></span> <span data-ttu-id="ba622-114">レポート サーバーでは、時間のかかる処理の多くは、レポートの表示操作処理と、クエリ処理の完了を待機している処理です。</span><span class="sxs-lookup"><span data-stu-id="ba622-114">On a report server, most long-running processes are report rendering operations and processes that are waiting for query processing to conclude.</span></span> <span data-ttu-id="ba622-115">コンピューターをオフラインにしたり、完了までに長時間かかっている実行中のジョブを停止する場合、レポート処理を取り消すことが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="ba622-115">Occasionally, you might need to cancel a report process if you want to take a computer offline, or stop a running job that is taking too long to complete.</span></span>  
  
 <span data-ttu-id="ba622-116">キャンセルできる処理は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="ba622-116">The following processes can be cancelled:</span></span>  
  
-   <span data-ttu-id="ba622-117">オンデマンドのレポート処理。</span><span class="sxs-lookup"><span data-stu-id="ba622-117">On-demand report processing.</span></span>  
  
-   <span data-ttu-id="ba622-118">スケジュールされたレポート処理。</span><span class="sxs-lookup"><span data-stu-id="ba622-118">Scheduled report processing.</span></span>  
  
-   <span data-ttu-id="ba622-119">個々のユーザーが所有する標準サブスクリプション。</span><span class="sxs-lookup"><span data-stu-id="ba622-119">Standard subscriptions owned by individual users.</span></span>  
  
 <span data-ttu-id="ba622-120">ジョブのキャンセルでは、レポート サーバーで実行中の処理だけが取り消されます。</span><span class="sxs-lookup"><span data-stu-id="ba622-120">Canceling a job only cancels the processes that are running on the report server.</span></span> <span data-ttu-id="ba622-121">レポート サーバーは、他のコンピューター上のデータ処理を管理しないため、他のシステム上で孤立したそれ以降のクエリ処理については、手動で取り消す必要があります。</span><span class="sxs-lookup"><span data-stu-id="ba622-121">Because the report server does not manage data processing that occurs on other computers, you must manually cancel query processes that are subsequently orphaned on other systems.</span></span> <span data-ttu-id="ba622-122">実行に長時間かかるクエリが自動的にシャットダウンされるようなクエリのタイムアウト値を指定することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="ba622-122">Consider specifying query time-out values to automatically shut down queries that are taking too long to execute.</span></span> <span data-ttu-id="ba622-123">詳細については、「[レポートおよび共有データセット処理のタイムアウト値の設定 (SSRS)](../report-server/setting-time-out-values-for-report-and-shared-dataset-processing-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ba622-123">For more information, see [Setting Time-out Values for Report and Shared Dataset Processing &#40;SSRS&#41;](../report-server/setting-time-out-values-for-report-and-shared-dataset-processing-ssrs.md).</span></span> <span data-ttu-id="ba622-124">一時的にレポートを一時停止する方法の詳細については、「[レポートとサブスクリプション処理の一時停止](disable-or-pause-report-and-subscription-processing.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ba622-124">For more information about temporarily pausing a report, see [Pause Report and Subscription Processing](disable-or-pause-report-and-subscription-processing.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ba622-125">まれに、サーバーを再起動して処理を取り消す必要が生じる場合があります。</span><span class="sxs-lookup"><span data-stu-id="ba622-125">In rare circumstances, you may need to restart the server to cancel a process.</span></span> <span data-ttu-id="ba622-126">SharePoint モードの場合、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービス アプリケーションをホストしているアプリケーション プールの再起動が必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="ba622-126">For SharePoint mode, you may need to restart the application pool hosting the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service application.</span></span> <span data-ttu-id="ba622-127">詳細については、「 [レポート サーバー サービスの開始と停止](../report-server/start-and-stop-the-report-server-service.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ba622-127">For more information, see [Start and Stop the Report Server Service](../report-server/start-and-stop-the-report-server-service.md).</span></span>  
  
 <span data-ttu-id="ba622-128">このトピックの内容</span><span class="sxs-lookup"><span data-stu-id="ba622-128">In this Topic:</span></span>  
  
-   [<span data-ttu-id="ba622-129">ジョブの表示とキャンセル (ネイティブ モード)</span><span class="sxs-lookup"><span data-stu-id="ba622-129">View and Cancel Jobs (Native Mode)</span></span>](#bkmk_native)  
  
-   [<span data-ttu-id="ba622-130">ジョブの表示とキャンセル (SharePoint モード)</span><span class="sxs-lookup"><span data-stu-id="ba622-130">View and Cancel Jobs (SharePoint Mode)</span></span>](#bkmk_sharepoint)  
  
-   [<span data-ttu-id="ba622-131">プログラムによるジョブの管理</span><span class="sxs-lookup"><span data-stu-id="ba622-131">Managing Jobs Programmatically</span></span>](#bkmk_programmatically)  
  
##  <a name="view-and-cancel-jobs-native-mode"></a><a name="bkmk_native"></a> <span data-ttu-id="ba622-132">ジョブの表示とキャンセル (ネイティブ モード)</span><span class="sxs-lookup"><span data-stu-id="ba622-132">View and Cancel Jobs (Native Mode)</span></span>  
 <span data-ttu-id="ba622-133">レポート サーバーで実行中のジョブは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] を使用して表示したり取り消したりできます。</span><span class="sxs-lookup"><span data-stu-id="ba622-133">You can use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] to view or cancel a job that is running on the report server.</span></span> <span data-ttu-id="ba622-134">現在実行中のジョブの一覧を取得したり、最新のジョブ ステータスをレポート サーバー データベースから取得したりするには、ページを更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ba622-134">You must refresh the page to retrieve a list of jobs that are currently running or to get up-to-date job status from the report server database.</span></span> <span data-ttu-id="ba622-135">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]からレポート サーバーに接続する際、[ジョブ] フォルダーを開くと、現在レポート サーバー コンピューターで処理中のレポートを一覧表示できます。</span><span class="sxs-lookup"><span data-stu-id="ba622-135">When you connect to a report server in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], you can open a Jobs folder to view a list of reports that are currently processing on the report server computer.</span></span> <span data-ttu-id="ba622-136">[ジョブのプロパティ] ページに、各ジョブのステータス情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="ba622-136">Status information for each job is displayed in the Job Properties page.</span></span> <span data-ttu-id="ba622-137">[レポート サーバー ジョブのキャンセル] ダイアログ ボックスを開くことによって、すべてのジョブのステータス情報を確認できます。</span><span class="sxs-lookup"><span data-stu-id="ba622-137">You can view status information for all jobs by opening the Cancel Report Server Jobs dialog box.</span></span>  
  
 <span data-ttu-id="ba622-138">レポート サーバーで実行中のジョブは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] を使用して表示したり取り消したりできます。</span><span class="sxs-lookup"><span data-stu-id="ba622-138">You can use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] to view or cancel a job that is running on the report server.</span></span> <span data-ttu-id="ba622-139">現在実行中のジョブの一覧を取得したり、最新のジョブ ステータスをレポート サーバー データベースから取得したりするには、ページを更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ba622-139">You must refresh the page to retrieve a list of jobs that are currently running or to get up-to-date job status from the report server database.</span></span> <span data-ttu-id="ba622-140">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]からレポート サーバーに接続する際、[ジョブ] フォルダーを開くと、現在レポート サーバー コンピューターで処理中のレポートを一覧表示できます。</span><span class="sxs-lookup"><span data-stu-id="ba622-140">When you connect to a report server in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], you can open a Jobs folder to view a list of reports that are currently processing on the report server computer.</span></span> <span data-ttu-id="ba622-141">[ジョブのプロパティ] ページに、各ジョブのステータス情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="ba622-141">Status information for each job is displayed in the Job Properties page.</span></span> <span data-ttu-id="ba622-142">[レポート サーバー ジョブのキャンセル] ダイアログ ボックスを開くことによって、すべてのジョブのステータス情報を確認できます。</span><span class="sxs-lookup"><span data-stu-id="ba622-142">You can view status information for all jobs by opening the Cancel Report Server Jobs dialog box.</span></span>  
  
 <span data-ttu-id="ba622-143">モデルの生成、モデルの処理、またはデータ ドリブン サブスクリプションについては、 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] で一覧表示したり取り消したりすることはできません。</span><span class="sxs-lookup"><span data-stu-id="ba622-143">You cannot use [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] to list or cancel model generation, model processing, or data-driven subscriptions.</span></span> <span data-ttu-id="ba622-144">モデルの生成またはモデルの処理を取り消す手段は、Reporting Services には用意されていません。</span><span class="sxs-lookup"><span data-stu-id="ba622-144">Reporting a Services does not provide a way to cancel model generation or processing.</span></span> <span data-ttu-id="ba622-145">ただし、このトピックで紹介している手順に従うことによって、データ ドリブン サブスクリプションをキャンセルできます。</span><span class="sxs-lookup"><span data-stu-id="ba622-145">However, you can cancel data-driven subscriptions using the instructions provided in this topic.</span></span>  
  
### <a name="how-to-cancel-report-processing-or-subscription"></a><span data-ttu-id="ba622-146">レポート処理またはサブスクリプションを取り消す方法</span><span class="sxs-lookup"><span data-stu-id="ba622-146">How to Cancel Report Processing or Subscription</span></span>  
  
1.  <span data-ttu-id="ba622-147">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]からレポート サーバーに接続します。</span><span class="sxs-lookup"><span data-stu-id="ba622-147">In [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], connect to the report server.</span></span> <span data-ttu-id="ba622-148">詳細については、「 [Management Studio でレポート サーバーに接続する方法](../tools/connect-to-a-report-server-in-management-studio.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ba622-148">For instructions, see [Connect to a Report Server in Management Studio](../tools/connect-to-a-report-server-in-management-studio.md).</span></span>  
  
2.  <span data-ttu-id="ba622-149">**[ジョブ]** フォルダーを開きます。</span><span class="sxs-lookup"><span data-stu-id="ba622-149">Open the **Jobs** folder.</span></span>  
  
3.  <span data-ttu-id="ba622-150">レポートを右クリックし、 **[ジョブの取り消し]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ba622-150">Right-click the report and then click **Cancel Jobs**.</span></span>  
  
### <a name="how-to-cancel-a-data-driven-subscription"></a><span data-ttu-id="ba622-151">データ ドリブン サブスクリプションを取り消す方法</span><span class="sxs-lookup"><span data-stu-id="ba622-151">How to Cancel a Data-driven Subscription</span></span>  
  
1.  <span data-ttu-id="ba622-152">テキスト エディターで RSReportServer.config ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="ba622-152">Open the RSReportServer.config file in a text editor.</span></span>  
  
2.  <span data-ttu-id="ba622-153">`IsNotificationService` を探します。</span><span class="sxs-lookup"><span data-stu-id="ba622-153">Find `IsNotificationService`.</span></span>  
  
3.  <span data-ttu-id="ba622-154">`False` に設定します。</span><span class="sxs-lookup"><span data-stu-id="ba622-154">Set it to `False`.</span></span>  
  
4.  <span data-ttu-id="ba622-155">ファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="ba622-155">Save the file.</span></span>  
  
5.  <span data-ttu-id="ba622-156">レポート マネージャーで、レポートの [サブスクリプション] タブまたは **[個人用サブスクリプション]** からデータ ドリブン サブスクリプションを削除します。</span><span class="sxs-lookup"><span data-stu-id="ba622-156">In Report Manager, delete the data-driven subscription from the Subscriptions tab of the report or from **My Subscriptions**.</span></span>  
  
6.  <span data-ttu-id="ba622-157">サブスクリプションを削除したら、RSReportServer.config ファイルで `IsNotificationService` を探し、`True` に設定します。</span><span class="sxs-lookup"><span data-stu-id="ba622-157">After you delete the subscription, in the RSReportServer.config file, find `IsNotificationService` and set it to `True`.</span></span>  
  
7.  <span data-ttu-id="ba622-158">ファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="ba622-158">Save the file.</span></span>  
  
### <a name="configuring-frequency-settings-for-retrieving-job-status"></a><span data-ttu-id="ba622-159">ジョブ ステータスの取得間隔の設定</span><span class="sxs-lookup"><span data-stu-id="ba622-159">Configuring Frequency Settings for Retrieving Job Status</span></span>  
 <span data-ttu-id="ba622-160">実行中のジョブは、レポート サーバーの一時データベースに格納されます。</span><span class="sxs-lookup"><span data-stu-id="ba622-160">A running job is stored in the report server temporary database.</span></span> <span data-ttu-id="ba622-161">RSReportServer.config ファイルで構成設定を変更し、レポート サーバーによる実行中のジョブをスキャンする頻度と実行ジョブの状態を新規から実行中に変更するまでの間隔を制御できます。</span><span class="sxs-lookup"><span data-stu-id="ba622-161">You can modify configuration settings in the RSReportServer.config file to control how often the report server scans for in-progress jobs and the interval after which the status of a running job changes from new to running.</span></span> <span data-ttu-id="ba622-162">`RunningRequestsDbCycle` 設定では、レポート サーバーによって実行中である処理のスキャンの頻度を指定します。</span><span class="sxs-lookup"><span data-stu-id="ba622-162">The `RunningRequestsDbCycle` setting specifies how often the report server scans for running processes.</span></span> <span data-ttu-id="ba622-163">既定では、状態情報は 60 秒ごとに記録されます。</span><span class="sxs-lookup"><span data-stu-id="ba622-163">By default, status information is recorded every 60 seconds.</span></span> <span data-ttu-id="ba622-164">`RunningRequestsAge` 設定では、ジョブが新規から実行中に遷移するまでの間隔を指定します。</span><span class="sxs-lookup"><span data-stu-id="ba622-164">The `RunningRequestsAge` setting specifies the interval at which a job is transitioned from new to running.</span></span>  
  
##  <a name="view-and-cancel-jobs-sharepoint-mode"></a><a name="bkmk_sharepoint"></a> <span data-ttu-id="ba622-165">ジョブの表示とキャンセル (SharePoint モード)</span><span class="sxs-lookup"><span data-stu-id="ba622-165">View and Cancel Jobs (SharePoint Mode)</span></span>  
 <span data-ttu-id="ba622-166">SharePoint モードでの配置のジョブの管理は、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービス アプリケーションごとに、SharePoint サーバーの全体管理を使用して行います。</span><span class="sxs-lookup"><span data-stu-id="ba622-166">Management of jobs in a SharePoint mode deployment is completed using SharePoint Central Administration, for each [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service application.</span></span>  
  
#### <a name="to-manage-jobs-in-sharepoint-mode"></a><span data-ttu-id="ba622-167">SharePoint モードでジョブを管理するには</span><span class="sxs-lookup"><span data-stu-id="ba622-167">To manage jobs in SharePoint mode</span></span>  
  
1.  <span data-ttu-id="ba622-168">SharePoint サーバーの全体管理で **[サービス アプリケーションの管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ba622-168">In SharePoint Central Administration, click **Manage service applications**.</span></span>  
  
2.  <span data-ttu-id="ba622-169">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービス アプリケーションの名前を見つけてクリックし、アプリケーションの管理ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="ba622-169">Find and click the name of your [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service application to open the manage application page.</span></span>  
  
3.  <span data-ttu-id="ba622-170">**[ジョブの管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ba622-170">Click **Manage Jobs**</span></span>  
  
4.  <span data-ttu-id="ba622-171">**[ジョブ ID]** をクリックして、ジョブの詳細を表示します。</span><span class="sxs-lookup"><span data-stu-id="ba622-171">Click the **Job Id** to see the details of the job.</span></span>  
  
5.  <span data-ttu-id="ba622-172">または、ジョブのボックスをクリックして **[削除]** をクリックし、ジョブをキャンセルします。</span><span class="sxs-lookup"><span data-stu-id="ba622-172">Or click the box for your job and click **Delete** to cancel the job.</span></span> <span data-ttu-id="ba622-173">ジョブを削除しても、サブスクリプションは削除されません。</span><span class="sxs-lookup"><span data-stu-id="ba622-173">Deleting the job does not delete the subscription.</span></span>  
  
##  <a name="managing-jobs-programmatically"></a><a name="bkmk_programmatically"></a> <span data-ttu-id="ba622-174">プログラムによるジョブの管理</span><span class="sxs-lookup"><span data-stu-id="ba622-174">Managing Jobs Programmatically</span></span>  
 <span data-ttu-id="ba622-175">ジョブは、プログラムまたはスクリプトを使用して管理できます。</span><span class="sxs-lookup"><span data-stu-id="ba622-175">You can manage jobs programmatically or by using a script.</span></span> <span data-ttu-id="ba622-176">詳細については、「 <xref:ReportService2010.ReportingService2010.ListJobs%2A>」と「 <xref:ReportService2010.ReportingService2010.CancelJob%2A>の両方を管理できます。</span><span class="sxs-lookup"><span data-stu-id="ba622-176">For more information, see <xref:ReportService2010.ReportingService2010.ListJobs%2A>, <xref:ReportService2010.ReportingService2010.CancelJob%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba622-177">参照</span><span class="sxs-lookup"><span data-stu-id="ba622-177">See Also</span></span>  
 <span data-ttu-id="ba622-178">[[レポート サーバー ジョブのキャンセル] (Management Studio)](../tools/cancel-report-server-jobs-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="ba622-178">[Cancel Report Server Jobs &#40;Management Studio&#41;](../tools/cancel-report-server-jobs-management-studio.md) </span></span>  
 <span data-ttu-id="ba622-179">[[ジョブのプロパティ] (Management Studio)](../tools/job-properties-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="ba622-179">[Job Properties &#40;Management Studio&#41;](../tools/job-properties-management-studio.md) </span></span>  
 <span data-ttu-id="ba622-180">[Reporting Services の構成ファイル &#40;RSreportserver.config&#41; の変更](../report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md) </span><span class="sxs-lookup"><span data-stu-id="ba622-180">[Modify a Reporting Services Configuration File &#40;RSreportserver.config&#41;](../report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md) </span></span>  
 <span data-ttu-id="ba622-181">[RSReportServer 構成ファイル](../report-server/rsreportserver-config-configuration-file.md) </span><span class="sxs-lookup"><span data-stu-id="ba622-181">[RSReportServer Configuration File](../report-server/rsreportserver-config-configuration-file.md) </span></span>  
 <span data-ttu-id="ba622-182">[レポート マネージャー &#40;SSRS ネイティブ モード&#41;](../report-manager-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="ba622-182">[Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md) </span></span>  
 [<span data-ttu-id="ba622-183">レポート サーバーのパフォーマンスの監視</span><span class="sxs-lookup"><span data-stu-id="ba622-183">Monitoring Report Server Performance</span></span>](../report-server/monitoring-report-server-performance.md)  
  
  
