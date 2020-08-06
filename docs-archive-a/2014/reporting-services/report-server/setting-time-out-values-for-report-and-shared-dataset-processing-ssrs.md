---
title: レポートおよび共有データセット処理のタイムアウト値の設定 (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- time-outs [Reporting Services]
- query time-outs [Reporting Services]
- report processing [Reporting Services], time-outs
- report execution time-outs [Reporting Services]
ms.assetid: 0f9dc61d-d03c-4bbf-8090-7a53844350f8
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c891b4911994ba2814a612439f141d16e4ad12a6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640593"
---
# <a name="setting-time-out-values-for-report-and-shared-dataset-processing-ssrs"></a><span data-ttu-id="9a54e-102">レポートおよび共有データセット処理のタイムアウト値の設定 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="9a54e-102">Setting Time-out Values for Report and Shared Dataset Processing (SSRS)</span></span>
  <span data-ttu-id="9a54e-103">タイムアウト値を指定して、システム リソースの使用に制限を設定できます。</span><span class="sxs-lookup"><span data-stu-id="9a54e-103">You can specify time-out values to set limits on how system resources are used.</span></span> <span data-ttu-id="9a54e-104">レポート サーバーでは、2 つのタイムアウト値がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="9a54e-104">Report server supports two time-out values:</span></span>  
  
-   <span data-ttu-id="9a54e-105">埋め込みデータセットのクエリ タイムアウト値は、レポート サーバーがデータベースからの応答を待機する秒数です。</span><span class="sxs-lookup"><span data-stu-id="9a54e-105">An embedded dataset query time-out value is the number of seconds that the report server waits for a response from the database.</span></span> <span data-ttu-id="9a54e-106">この値はレポートの中で定義されます。</span><span class="sxs-lookup"><span data-stu-id="9a54e-106">This value is defined in a report.</span></span>  
  
-   <span data-ttu-id="9a54e-107">共有データセットのクエリ タイムアウト値は、レポート サーバーがデータベースからの応答を待機する秒数です。</span><span class="sxs-lookup"><span data-stu-id="9a54e-107">A shared dataset query time-out value is the number of seconds that the report server waits for a response from the database.</span></span> <span data-ttu-id="9a54e-108">この値は共有データセット定義の一部であり、レポート サーバー上で共有データセットを管理するときに変更できます。</span><span class="sxs-lookup"><span data-stu-id="9a54e-108">This value is part of the shared dataset definition and can be changed when you manage the shared dataset on the report server.</span></span>  
  
-   <span data-ttu-id="9a54e-109">レポート実行タイムアウト値は、レポート処理を停止するまでに続行できる最大秒数です。</span><span class="sxs-lookup"><span data-stu-id="9a54e-109">A report execution time-out value is the maximum number of seconds that report processing can continue before it is stopped.</span></span> <span data-ttu-id="9a54e-110">この値はシステムレベルで定義されます。</span><span class="sxs-lookup"><span data-stu-id="9a54e-110">This value is defined at the system level.</span></span> <span data-ttu-id="9a54e-111">この設定は、レポートごとに変えることができます。</span><span class="sxs-lookup"><span data-stu-id="9a54e-111">You can vary this setting for individual reports.</span></span>  
  
 <span data-ttu-id="9a54e-112">タイムアウト エラーの大半は、クエリ処理中に発生します。</span><span class="sxs-lookup"><span data-stu-id="9a54e-112">Most time-out errors occur during query processing.</span></span> <span data-ttu-id="9a54e-113">タイムアウト エラーが発生する場合は、クエリ タイムアウト値を増やしてください。</span><span class="sxs-lookup"><span data-stu-id="9a54e-113">If you are encountering time-out errors, try increasing the query time-out value.</span></span> <span data-ttu-id="9a54e-114">レポート実行タイムアウト値は、クエリタイムアウトよりも大きくなるように調整してください。クエリとレポート処理の両方を完了するのに十分な期間を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9a54e-114">Make sure to adjust the report execution time-out value so that it is larger than the query time-out. The time period should be sufficient to complete both query and report processing.</span></span>  
  
## <a name="setting-a-query-time-out-for-an-embedded-dataset-in-a-report"></a><span data-ttu-id="9a54e-115">レポートの埋め込みデータセットに対するクエリ タイムアウトの設定</span><span class="sxs-lookup"><span data-stu-id="9a54e-115">Setting a Query Time-Out for an Embedded Dataset in a Report</span></span>  
 <span data-ttu-id="9a54e-116">クエリ タイムアウト値は、レポートの作成中、埋め込みデータセットを定義するときに指定します。</span><span class="sxs-lookup"><span data-stu-id="9a54e-116">Query time-out values are specified during report authoring when you define an embedded dataset.</span></span> <span data-ttu-id="9a54e-117">タイムアウト値は、レポート定義の `Timeout` 要素の中にレポートと一緒に格納されます。</span><span class="sxs-lookup"><span data-stu-id="9a54e-117">The time-out value is stored with the report, in the `Timeout` element of the report definition.</span></span> <span data-ttu-id="9a54e-118">既定では、この値は 30 秒に設定されます。</span><span class="sxs-lookup"><span data-stu-id="9a54e-118">By default, this value is set to 30 seconds.</span></span> <span data-ttu-id="9a54e-119">詳細については、「 [レポート埋め込みデータセットと共有データセット &#40;レポート ビルダーおよび SSRS&#41;](../report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="9a54e-119">For more information, see [Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](../report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="9a54e-120">パブリッシュ済みレポートのプロパティを変更する権限を持っているユーザーは、レポート定義ファイルを編集することでこの値を再設定できます。</span><span class="sxs-lookup"><span data-stu-id="9a54e-120">Users who have permission to modify the properties of a published report can reset this value by editing the report definition file.</span></span>  
  
 <span data-ttu-id="9a54e-121">また、データ ドリブン サブスクリプションのクエリ タイムアウト値を指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="9a54e-121">You can also specify a query time-out value for data-driven subscriptions.</span></span> <span data-ttu-id="9a54e-122">クエリのタイムアウト値は、[データ ドリブン サブスクリプション] ページで指定します。</span><span class="sxs-lookup"><span data-stu-id="9a54e-122">The query time-out value is specified in the Data-Driven Subscription pages.</span></span> <span data-ttu-id="9a54e-123">ここで指定した値によって、サブスクライバーのデータ ソースからデータを取得する際に、クエリ処理が完了するまでのレポート サーバーが待機する時間が決定されます。</span><span class="sxs-lookup"><span data-stu-id="9a54e-123">The value you specify determines how long the report server waits for query processing to complete when retrieving data from the subscriber data source.</span></span>  
  
## <a name="setting-a-query-time-out-for-a-shared-dataset"></a><span data-ttu-id="9a54e-124">共有データセットに対するクエリ タイムアウトの設定</span><span class="sxs-lookup"><span data-stu-id="9a54e-124">Setting a Query Time-Out for a Shared Dataset</span></span>  
 <span data-ttu-id="9a54e-125">クエリ タイムアウト値は、共有データセットを作成または管理するときに、レポート サーバー上で秒単位で指定します。</span><span class="sxs-lookup"><span data-stu-id="9a54e-125">Query time-out values are specified in seconds on the report server when you create or manage a shared dataset.</span></span> <span data-ttu-id="9a54e-126">既定でこの値は 0 秒に設定されています。0 秒を指定すると、タイムアウト値を指定していない場合と同じ意味になります。</span><span class="sxs-lookup"><span data-stu-id="9a54e-126">By default, this value is set to 0 seconds, which is the equivalent of no time-out value.</span></span> <span data-ttu-id="9a54e-127">詳細については、「 [共有データセットの管理](../report-data/manage-shared-datasets.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9a54e-127">For more information, see [Manage Shared Datasets](../report-data/manage-shared-datasets.md).</span></span>  
  
## <a name="setting-a-report-execution-time-out"></a><span data-ttu-id="9a54e-128">レポート実行タイムアウトの設定</span><span class="sxs-lookup"><span data-stu-id="9a54e-128">Setting a Report Execution Time-Out</span></span>  
 <span data-ttu-id="9a54e-129">レポート実行タイムアウト値を設定して、レポート サーバーがレポート処理に使用する時間を制限することができます。</span><span class="sxs-lookup"><span data-stu-id="9a54e-129">You can set the report execution time-out value to limit the amount of time that a report server uses to process a report.</span></span> <span data-ttu-id="9a54e-130">レポート実行タイムアウト値は、レポート マネージャーで指定できます。</span><span class="sxs-lookup"><span data-stu-id="9a54e-130">Report execution time-out values can be specified in Report Manager.</span></span> <span data-ttu-id="9a54e-131">[サイトの設定] ページですべてのレポートの既定値を設定してから、特定のレポートの [実行] プロパティ ページでその値をオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="9a54e-131">You can set a default value for all reports in the Site Settings page, and then override that value in the Execution properties page for a specific report.</span></span> <span data-ttu-id="9a54e-132">既定では、この値は 1,800 秒に設定されます。</span><span class="sxs-lookup"><span data-stu-id="9a54e-132">By default, the value is set to 1800 seconds.</span></span> <span data-ttu-id="9a54e-133">詳細については、「 [レポート処理プロパティの設定](set-report-processing-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9a54e-133">For more information, see [Set Report Processing Properties](set-report-processing-properties.md).</span></span>  
  
## <a name="how-report-execution-time-out-values-are-evaluated"></a><span data-ttu-id="9a54e-134">レポート実行タイムアウト値の評価方法</span><span class="sxs-lookup"><span data-stu-id="9a54e-134">How Report Execution Time-Out Values are Evaluated</span></span>  
 <span data-ttu-id="9a54e-135">レポート サーバーでは、60 秒ごとに実行中のジョブが評価されます。</span><span class="sxs-lookup"><span data-stu-id="9a54e-135">The report server evaluates running jobs at 60 second intervals.</span></span> <span data-ttu-id="9a54e-136">レポート サーバーでは、60 秒ごとに、レポート実行タイムアウト値に対して実際の処理時間が比較されます。</span><span class="sxs-lookup"><span data-stu-id="9a54e-136">At each 60 second interval, the report server compares actual process time against the report execution time-out value.</span></span> <span data-ttu-id="9a54e-137">レポートの処理時間がレポート実行タイムアウト値を超えた場合、レポートの処理が停止します。</span><span class="sxs-lookup"><span data-stu-id="9a54e-137">If the processing time for a report exceeds the report execution time-out value, report processing will stop.</span></span>  
  
 <span data-ttu-id="9a54e-138">タイムアウト値を 60 秒未満に指定した場合、サイクルの静止期間、つまりレポート サーバーで実行中のジョブが評価されていない期間に、レポートが、開始から終了まで完全に実行されることがあります。</span><span class="sxs-lookup"><span data-stu-id="9a54e-138">Note that if you specify a time-out value that is smaller than 60 seconds, the report may execute in full if processing starts and completes during the quiet part of the cycle when the report server is not evaluating running jobs.</span></span> <span data-ttu-id="9a54e-139">たとえば、実行に 20 秒かかるレポートのタイムアウト値を 10 秒に設定した場合、レポートの実行が 60 秒サイクルの早期に開始されると、レポートは完全に処理されます。</span><span class="sxs-lookup"><span data-stu-id="9a54e-139">For example, if you set a time-out value of 10 seconds for a report that takes 20 seconds to run, the report will process in full if report execution starts early in the 60 second cycle.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9a54e-140">RSReportServer.config ファイルの `RunningRequestsDbCycle` 設定で、実行中のジョブが評価される頻度を変更できます。</span><span class="sxs-lookup"><span data-stu-id="9a54e-140">You can set the `RunningRequestsDbCycle` setting in the RSReportServer.config file to change the frequency of how often running jobs are evaluated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a54e-141">参照</span><span class="sxs-lookup"><span data-stu-id="9a54e-141">See Also</span></span>  
 <span data-ttu-id="9a54e-142">[SharePoint 統合モードで Reporting Services &#40;処理オプションを設定&#41;](../set-processing-options-reporting-services-in-sharepoint-integrated-mode.md) </span><span class="sxs-lookup"><span data-stu-id="9a54e-142">[Set Processing Options &#40;Reporting Services in SharePoint Integrated Mode&#41;](../set-processing-options-reporting-services-in-sharepoint-integrated-mode.md) </span></span>  
 <span data-ttu-id="9a54e-143">[Reporting Services レポート サーバー (ネイティブ モード)](reporting-services-report-server-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="9a54e-143">[Reporting Services Report Server &#40;Native Mode&#41;](reporting-services-report-server-native-mode.md) </span></span>  
 <span data-ttu-id="9a54e-144">[実行中のプロセスを管理する](../subscriptions/manage-a-running-process.md) </span><span class="sxs-lookup"><span data-stu-id="9a54e-144">[Manage a Running Process](../subscriptions/manage-a-running-process.md) </span></span>  
 [<span data-ttu-id="9a54e-145">レポート マネージャー &#40;SSRS ネイティブ モード&#41;</span><span class="sxs-lookup"><span data-stu-id="9a54e-145">Report Manager  &#40;SSRS Native Mode&#41;</span></span>](../report-manager-ssrs-native-mode.md)  
  
  
