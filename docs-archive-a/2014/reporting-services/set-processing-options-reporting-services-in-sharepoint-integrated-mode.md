---
title: 処理オプションの設定 (SharePoint 統合モードでの Reporting Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- SharePoint integration [Reporting Services], content management
- snapshots [Reporting Services], creating
ms.assetid: 453b19a1-739a-4b67-aeea-2069b52204e1
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 8c33b205a702d4ab77abf74154232990da9840b6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716066"
---
# <a name="set-processing-options-reporting-services-in-sharepoint-integrated-mode"></a><span data-ttu-id="15ecb-102">処理オプションの設定 (Reporting Services の SharePoint 統合モード)</span><span class="sxs-lookup"><span data-stu-id="15ecb-102">Set Processing Options (Reporting Services in SharePoint Integrated Mode)</span></span>
  <span data-ttu-id="15ecb-103">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] レポートの処理オプションを設定することにより、データ処理のタイミングを決定することができます。</span><span class="sxs-lookup"><span data-stu-id="15ecb-103">You can set processing options on a [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] report to determine when data processing occurs.</span></span> <span data-ttu-id="15ecb-104">また、レポート処理のタイムアウト値や、現在のレポートでレポート履歴を有効にするかどうかを決定するオプションも設定できます。</span><span class="sxs-lookup"><span data-stu-id="15ecb-104">You can also set a time-out value for report processing, and options that determine whether report history is enabled for the current report.</span></span>  
  
-   <span data-ttu-id="15ecb-105">レポートが予定外に (たとえば、スケジュールされたバックアップ中に) 実行されないように、レポートをレポート スナップショットとして実行することができます。</span><span class="sxs-lookup"><span data-stu-id="15ecb-105">You can run a report as a report snapshot to prevent the report from being run at arbitrary times (for example, during a scheduled backup).</span></span> <span data-ttu-id="15ecb-106">レポート スナップショットは、通常はスケジュールに従って作成され、その後更新されます。これによって、正確な時間でレポートとデータ処理を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="15ecb-106">A report snapshot is usually created and subsequently refreshed on a schedule, allowing you to time exactly when report and data processing will occur.</span></span> <span data-ttu-id="15ecb-107">レポートが実行に長時間かかるクエリに基づいている場合や、クエリに使用されているデータのデータ ソースが、ある一定時間の間アクセスを避けたいものである場合は、レポートをスナップショットとして実行してください。</span><span class="sxs-lookup"><span data-stu-id="15ecb-107">If a report is based on queries that take a long time to run, or on queries that use data from a data source that you prefer no one access during certain hours, you should run the report as a snapshot.</span></span>  
  
-   <span data-ttu-id="15ecb-108">レポート サーバーでは、処理済みレポートのコピーをキャッシュして、ユーザーがレポートを開いたときにそのコピーを返すことができます。</span><span class="sxs-lookup"><span data-stu-id="15ecb-108">A report server can cache a copy of a processed report and return that copy when a user opens the report.</span></span> <span data-ttu-id="15ecb-109">キャッシュは、パフォーマンスを向上させる技法です。</span><span class="sxs-lookup"><span data-stu-id="15ecb-109">Caching is a performance-enhancement technique.</span></span> <span data-ttu-id="15ecb-110">レポートのサイズが大きい場合やレポートへのアクセスが頻繁に行われる場合、キャッシュを行うことでレポートの取得にかかる時間を短縮できます。</span><span class="sxs-lookup"><span data-stu-id="15ecb-110">Caching can shorten the time required to retrieve a report if the report is large or accessed frequently.</span></span>  
  
-   <span data-ttu-id="15ecb-111">レポート履歴は、以前実行したレポートの一連のコピーです。</span><span class="sxs-lookup"><span data-stu-id="15ecb-111">Report history is a collection of previously run copies of a report.</span></span> <span data-ttu-id="15ecb-112">レポート履歴を使用すると、長期にわたりレポートの記録を管理できます。</span><span class="sxs-lookup"><span data-stu-id="15ecb-112">You can use report history to maintain a record of a report over time.</span></span> <span data-ttu-id="15ecb-113">秘密情報または個人データを含むレポートは、レポート履歴の対象ではありません。</span><span class="sxs-lookup"><span data-stu-id="15ecb-113">Report history is not intended for reports that contain confidential or personal data.</span></span> <span data-ttu-id="15ecb-114">このため、レポート履歴に含めることができるのは、レポートを実行するすべてのユーザーが使用できる資格情報 (格納された資格情報、または自動的にレポートを実行するために使用する資格情報のいずれか) でデータ ソースへのクエリを行うレポートのみです。</span><span class="sxs-lookup"><span data-stu-id="15ecb-114">For this reason, report history can include only those reports that query a data source using a single set of credentials (either stored credentials or credentials used for unattended report execution) that are available to all users who run a report.</span></span>  
  
    > [!NOTE]  
    >  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] <span data-ttu-id="15ecb-115">の統合では、SharePoint のコンテンツのチェックアウトおよびチェックイン管理機能を使用して、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] のコンテンツの種類への更新を保存します。</span><span class="sxs-lookup"><span data-stu-id="15ecb-115">integration with SharePoint uses the check out and check in content management features of SharePoint to save updates to [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] content types.</span></span> <span data-ttu-id="15ecb-116">これには、レポート スナップショットの作成が含まれます。</span><span class="sxs-lookup"><span data-stu-id="15ecb-116">This includes the creation of report snapshots.</span></span> <span data-ttu-id="15ecb-117">したがって、ドキュメント ライブラリでのバージョン管理を有効にしている場合は、新しいレポート履歴スナップショットが作成されたときに、レポート バージョンが更新されます。</span><span class="sxs-lookup"><span data-stu-id="15ecb-117">Therefore if you have enabled versioning on a document library, you will see the report version updated when a new report history snapshot is created.</span></span> <span data-ttu-id="15ecb-118">この動作は、スナップショットの更新による副作用です。</span><span class="sxs-lookup"><span data-stu-id="15ecb-118">This is a side-effect of updating snapshots.</span></span> <span data-ttu-id="15ecb-119">スナップショットが更新されると、レポートの LastExecution プロパティが変更され、それによってレポートのバージョンが変更されます。</span><span class="sxs-lookup"><span data-stu-id="15ecb-119">When a snapshot is updated it causes the LastExecution property of the report to change and that will cause a change in the version of the report.</span></span>  
  
-   <span data-ttu-id="15ecb-120">タイムアウト値を指定して、システム リソースの使用に制限を設定できます。</span><span class="sxs-lookup"><span data-stu-id="15ecb-120">You can specify time-out values to set limits on how system resources are used.</span></span>  
  
||  
|-|  
|<span data-ttu-id="15ecb-121">**[!INCLUDE[applies](../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]SharePoint モード</span><span class="sxs-lookup"><span data-stu-id="15ecb-121">**[!INCLUDE[applies](../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint mode</span></span>|  
  
 <span data-ttu-id="15ecb-122">**このトピックの内容:**</span><span class="sxs-lookup"><span data-stu-id="15ecb-122">**In this topic:**</span></span>  
  
-   [<span data-ttu-id="15ecb-123">データ更新オプションを設定するには</span><span class="sxs-lookup"><span data-stu-id="15ecb-123">To set data refresh options</span></span>](#bkmk_set_data_refresh)  
  
-   [<span data-ttu-id="15ecb-124">レポート キャッシュ オプションを設定するには</span><span class="sxs-lookup"><span data-stu-id="15ecb-124">To set report caching options</span></span>](#bkmk_set_report_caching)  
  
-   [<span data-ttu-id="15ecb-125">処理のタイムアウト値を設定するには</span><span class="sxs-lookup"><span data-stu-id="15ecb-125">To set processing time-out values</span></span>](#bkmk_set_processing)  
  
-   [<span data-ttu-id="15ecb-126">レポート履歴のオプションと制限を設定するには</span><span class="sxs-lookup"><span data-stu-id="15ecb-126">To set report history options and limits</span></span>](#bkmk_set_report_history)  
  
-   [<span data-ttu-id="15ecb-127">データベースのタイムアウトを設定する</span><span class="sxs-lookup"><span data-stu-id="15ecb-127">Set database timeout</span></span>](#bkmk_set_database_timeout)  
  
##  <a name="to-set-data-refresh-options"></a><a name="bkmk_set_data_refresh"></a><span data-ttu-id="15ecb-128">データ更新オプションを設定するには</span><span class="sxs-lookup"><span data-stu-id="15ecb-128">To set data refresh options</span></span>  
  
1.  <span data-ttu-id="15ecb-129">ライブラリ内のレポートをポイントします。</span><span class="sxs-lookup"><span data-stu-id="15ecb-129">Point to a report in the library.</span></span>  
  
2.  <span data-ttu-id="15ecb-130">下矢印をクリックし、 **[処理の管理のオプション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="15ecb-130">Click the down arrow, and select **Manage processing options**.</span></span>  
  
3.  <span data-ttu-id="15ecb-131">**[データ更新オプション]** で、 **[スナップショット データを使用する]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="15ecb-131">In **Data Refresh Options**, click **Use snapshot data**.</span></span> <span data-ttu-id="15ecb-132">"データ ソースの資格情報が保存されていないため、このレポートをスナップショットから実行できません。" と表示される場合は、レポートが自動実行されるように構成されていないため、このオプションを設定する前に、保存されている資格情報が使用されるようにデータ ソースを変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="15ecb-132">If you see "This report can not run from a snapshot because one or more of the data sources credentials are not stored", the report is not configured to run unattended and you must modify the data sources to use stored credentials before setting this option.</span></span>  
  
4.  <span data-ttu-id="15ecb-133">**[データ スナップショットのオプション]** で、 **[データ処理をスケジュールする]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="15ecb-133">In **Data Snapshot Options**, select **Schedule data processing**.</span></span>  
  
5.  <span data-ttu-id="15ecb-134">使用できる既存の共有スケジュールがあれば、 **[次の共有スケジュールで実行する]** をクリックします。それ以外の場合は、 **[カスタム スケジュールで実行する]** をクリックし、 **[構成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="15ecb-134">Select **On a shared schedule** if you have an existing shared schedule that you want to use, otherwise click **On a custom schedule**, and then click **Configure**.</span></span>  
  
6.  <span data-ttu-id="15ecb-135">頻度、スケジュール、および開始日と終了日を選択し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="15ecb-135">Select frequency, schedule, and start and end dates, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="15ecb-136">スケジュールされたデータ処理の実行を待たずに、直ちにスナップショット データを作成してレポートに使用する必要がある場合は、 **[データ スナップショットのオプション]** で **[このページを保存するときにスナップショットを作成または更新する]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="15ecb-136">In **Data Snapshot Options**, select **Create or update the snapshot when this page is saved** if you want to immediately create snapshot data to use with the report, without waiting for the scheduled data processing to occur.</span></span>  
  
##  <a name="to-set-report-caching-options"></a><a name="bkmk_set_report_caching"></a><span data-ttu-id="15ecb-137">レポートキャッシュオプションを設定するには</span><span class="sxs-lookup"><span data-stu-id="15ecb-137">To set report caching options</span></span>  
  
1.  <span data-ttu-id="15ecb-138">ライブラリ内のレポートをポイントします。</span><span class="sxs-lookup"><span data-stu-id="15ecb-138">Point to a report in the library.</span></span>  
  
2.  <span data-ttu-id="15ecb-139">下矢印をクリックし、 **[処理の管理のオプション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="15ecb-139">Click the down arrow, and select **Manage processing options**.</span></span>  
  
3.  <span data-ttu-id="15ecb-140">**[データ更新オプション]** で、 **[キャッシュ データを使用する]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="15ecb-140">In **Data Refresh Options**, click **Use cached data**.</span></span> <span data-ttu-id="15ecb-141">"1 つ以上のデータ ソース資格情報が保存されていないため、このレポートをキャッシュできません。" と表示される場合は、レポートが自動実行されるように構成されていないため、このオプションを設定する前に、保存されている資格情報が使用されるようにデータ ソースを変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="15ecb-141">If you see "This report can not be cached because one or more of the data sources credentials are not stored", the report is not configured to run unattended and you must modify the data sources to use stored credentials before setting this option.</span></span>  
  
4.  <span data-ttu-id="15ecb-142">**[キャッシュ オプション]** で、キャッシュの有効期限を次のように指定します。</span><span class="sxs-lookup"><span data-stu-id="15ecb-142">In **Cache Options**, specify how the cache will expire:</span></span>  
  
    -   <span data-ttu-id="15ecb-143">キャッシュの有効期限が切れるまでの時間を分単位で入力します。</span><span class="sxs-lookup"><span data-stu-id="15ecb-143">Enter a number of minutes after which the cache will expire.</span></span>  
  
    -   <span data-ttu-id="15ecb-144">スケジュールで指定した時刻にキャッシュを消去するには、共有スケジュールを使用します。</span><span class="sxs-lookup"><span data-stu-id="15ecb-144">Use a shared schedule to clear the cache at times specified in the schedule.</span></span>  
  
    -   <span data-ttu-id="15ecb-145">指定した時刻にキャッシュを消去するには、カスタム スケジュールを作成します。</span><span class="sxs-lookup"><span data-stu-id="15ecb-145">Create a custom schedule to clear the cache at a time that you specify.</span></span>  
  
##  <a name="to-set-processing-time-out-values"></a><a name="bkmk_set_processing"></a><span data-ttu-id="15ecb-146">処理のタイムアウト値を設定するには</span><span class="sxs-lookup"><span data-stu-id="15ecb-146">To set processing time-out values</span></span>  
  
1.  <span data-ttu-id="15ecb-147">ライブラリ内のレポートをポイントします。</span><span class="sxs-lookup"><span data-stu-id="15ecb-147">Point to a report in the library.</span></span>  
  
2.  <span data-ttu-id="15ecb-148">下矢印をクリックし、 **[処理の管理のオプション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="15ecb-148">Click the down arrow, and select **Manage processing options**.</span></span>  
  
3.  <span data-ttu-id="15ecb-149">レポート サーバー レベルで指定された値を使用する必要がある場合は、 **[処理のタイムアウト]** で **[サイトの既定の設定を使用する]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="15ecb-149">In **Processing Time-out**, select **Use site default setting** if you want to use the value specified at the report server level.</span></span> <span data-ttu-id="15ecb-150">タイムアウトなしにするか、別のタイムアウト値にオーバーライドする必要がある場合は、**[レポート処理をタイムアウトしない]** または **[レポート処理を次の時間 (秒) に制限する]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="15ecb-150">Otherwise, select **Do not time out report processing** or **Limit report processing in seconds** if you want to override that value with no time-out or different time-out values.</span></span>  
  
##  <a name="to-set-report-history-options-and-limits"></a><a name="bkmk_set_report_history"></a><span data-ttu-id="15ecb-151">レポート履歴のオプションと制限を設定するには</span><span class="sxs-lookup"><span data-stu-id="15ecb-151">To set report history options and limits</span></span>  
  
1.  <span data-ttu-id="15ecb-152">ライブラリ内のレポートをポイントします。</span><span class="sxs-lookup"><span data-stu-id="15ecb-152">Point to a report in the library.</span></span>  
  
2.  <span data-ttu-id="15ecb-153">下矢印をクリックし、 **[処理の管理のオプション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="15ecb-153">Click the down arrow, and select **Manage processing options**.</span></span>  
  
3.  <span data-ttu-id="15ecb-154">**[履歴スナップショットのオプション]** で、データ処理を実行して保存する方法とタイミングを指定します。</span><span class="sxs-lookup"><span data-stu-id="15ecb-154">In **History Snapshot Options**, specify how and when data processing occurs and is saved.</span></span>  
  
4.  <span data-ttu-id="15ecb-155">レポート サーバー レベルで指定された値を使用する場合は、 **[履歴スナップショットの制限]** で **[サイトの既定の設定を使用する]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="15ecb-155">In **History Snapshot Limits**, select **Use site default setting** if you want to use the value specified at the report server level.</span></span> <span data-ttu-id="15ecb-156">それ以外の場合は、 **[スナップショット数を制限しない]** を選択するか、 **[スナップショットを次の数に制限する]** でカスタム値を指定します。</span><span class="sxs-lookup"><span data-stu-id="15ecb-156">Otherwise, select **Do not limit the number of snapshots** or **Limit number of snapshots** to specify a custom value.</span></span>  
  
##  <a name="set-database-timeout"></a><a name="bkmk_set_database_timeout"></a><span data-ttu-id="15ecb-157">データベースタイムアウトの設定</span><span class="sxs-lookup"><span data-stu-id="15ecb-157">Set database timeout</span></span>  
  
1.  <span data-ttu-id="15ecb-158">Windows PowerShell を使用すると、SharePoint レポート サーバーのデータベースのタイムアウト値を設定できます。</span><span class="sxs-lookup"><span data-stu-id="15ecb-158">Use Windows PowerShell to set the database timeout of a SharePoint report server.</span></span> <span data-ttu-id="15ecb-159">詳細については、「[Reporting Services SharePoint モード用の PowerShell コマンドレット](../../2014/reporting-services/powershell-cmdlets-for-reporting-services-sharepoint-mode.md)」の「Reporting Service アプリケーション データベースのプロパティの取得と設定」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="15ecb-159">For more information, see the "Get and set Properties of the Reporting Service Application Database" section of [PowerShell cmdlets for Reporting Services SharePoint Mode](../../2014/reporting-services/powershell-cmdlets-for-reporting-services-sharepoint-mode.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15ecb-160">参照</span><span class="sxs-lookup"><span data-stu-id="15ecb-160">See Also</span></span>  
 <span data-ttu-id="15ecb-161">[レポート処理プロパティの設定](report-server/set-report-processing-properties.md) </span><span class="sxs-lookup"><span data-stu-id="15ecb-161">[Set Report Processing Properties](report-server/set-report-processing-properties.md) </span></span>  
 <span data-ttu-id="15ecb-162">[レポートのキャッシュ &#40;SSRS&#41;](report-server/caching-reports-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="15ecb-162">[Caching Reports &#40;SSRS&#41;](report-server/caching-reports-ssrs.md) </span></span>  
 [<span data-ttu-id="15ecb-163">レポートおよび共有データセット処理のタイムアウト値の設定 &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="15ecb-163">Setting Time-out Values for Report and Shared Dataset Processing &#40;SSRS&#41;</span></span>](report-server/setting-time-out-values-for-report-and-shared-dataset-processing-ssrs.md)  
  
  
