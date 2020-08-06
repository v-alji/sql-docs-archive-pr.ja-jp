---
title: パフォーマンス、スナップショット、キャッシュ (Reporting Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- performance [Reporting Services]
- Reporting Services, performance
ms.assetid: 85afd00f-e8d7-4ef7-9174-2ff84d82f960
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f171586e136b36bd694fa40b15272f62e1cb1378
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716090"
---
# <a name="performance-snapshots-caching-reporting-services"></a><span data-ttu-id="7b773-102">パフォーマンス、スナップショット、キャッシュ (Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="7b773-102">Performance, Snapshots, Caching (Reporting Services)</span></span>
  <span data-ttu-id="7b773-103">レポート サーバーのパフォーマンスには、ハードウェア、レポートに同時にアクセスするユーザー数、レポートのデータ量、出力形式など、さまざまな要因が絡み合って影響を与えます。</span><span class="sxs-lookup"><span data-stu-id="7b773-103">Report server performance is affected by a combination of factors that include hardware, number of concurrent users accessing reports, the amount of data in a report, and output format.</span></span> <span data-ttu-id="7b773-104">環境に固有のパフォーマンス要因を把握し、期待した結果を得るための対策を講じるには、ベースライン データを用意し、テストを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7b773-104">To understand the performance factors that are specific to your installation and which remedies will produce the results you want, you will need to get baseline data and run tests.</span></span> <span data-ttu-id="7b773-105">ツールとガイドラインの詳細については、MSDN の資料「 [Reporting Services のパフォーマンスの最適化](https://blogs.msdn.com/b/sqlcat/archive/2013/10/30/reporting-services-performance-and-optimization.aspx) 」および「 [Visual Studio 2005 を使用した SQL Server 2005 Reporting Services レポート サーバーのロード テスト](https://go.microsoft.com/fwlink/?LinkID=77519)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7b773-105">For more information about tools and guidelines, see the following publications on MSDN: [Reporting Services Performance Optimization](https://blogs.msdn.com/b/sqlcat/archive/2013/10/30/reporting-services-performance-and-optimization.aspx) and [Using Visual Studio 2005 to Perform Load Testing on a SQL Server 2005 Reporting Services Report Server](https://go.microsoft.com/fwlink/?LinkID=77519).</span></span>  
  
 <span data-ttu-id="7b773-106">考慮する必要がある一般的な原則は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="7b773-106">General principles to consider include the following:</span></span>  
  
-   <span data-ttu-id="7b773-107">レポートの処理と表示には、多くのメモリを必要とします。</span><span class="sxs-lookup"><span data-stu-id="7b773-107">Report processing and rendering are memory intensive operations.</span></span> <span data-ttu-id="7b773-108">搭載メモリ量ができるだけ多いコンピューターを選択してください。</span><span class="sxs-lookup"><span data-stu-id="7b773-108">When possible, choose a computer that has a lot of memory.</span></span>  
  
-   <span data-ttu-id="7b773-109">レポート サーバーとレポート サーバー データベースを別個のコンピューターでホストした方が、1 台のハイエンド コンピューターで両方をホストするよりも、パフォーマンスが高くなる傾向があります。</span><span class="sxs-lookup"><span data-stu-id="7b773-109">Hosting the report server and the report server database on separate computers tends to provide better performance than hosting both on a single high-end computer.</span></span>  
  
-   <span data-ttu-id="7b773-110">すべてのレポートの処理速度が低下している場合は、複数のレポート サーバー インスタンスで単一のレポート サーバー データベースをサポートするスケールアウト配置を検討します。</span><span class="sxs-lookup"><span data-stu-id="7b773-110">If all reports are processing slowly, consider a scale-out deployment where multiple report server instances support a single report server database.</span></span> <span data-ttu-id="7b773-111">最適な結果を得るには、負荷分散ソフトウェアを使用して、配置全体に対して要求を均等に分散させるようにします。</span><span class="sxs-lookup"><span data-stu-id="7b773-111">For best results, use load balancing software to distribute requests evenly across the deployment.</span></span>  
  
-   <span data-ttu-id="7b773-112">ある特定のレポートの処理速度だけが低下しているとき、そのレポートを要求時に実行する場合は、レポート データセット クエリをチューニングします。</span><span class="sxs-lookup"><span data-stu-id="7b773-112">If a single report is processing slowly, tune report dataset queries if the report must run on demand.</span></span> <span data-ttu-id="7b773-113">また、キャッシュできる共有データセットの使用、レポートのキャッシュ、またはスナップショットとしてのレポートの実行を検討してください。</span><span class="sxs-lookup"><span data-stu-id="7b773-113">You might also consider using shared datasets that you can cache, caching the report, or running the report as a snapshot.</span></span>  
  
-   <span data-ttu-id="7b773-114">特定の形式のすべてのレポートの処理速度が低下している場合 (PDF 形式で表示している場合など)、ファイル共有配信を検討するか、メモリを増設する、または、異なる形式を選択するようにします。</span><span class="sxs-lookup"><span data-stu-id="7b773-114">If all reports process slowly in a specific format (for example, while rendering to PDF), consider file share delivery, adding more memory, or choosing a different format.</span></span>  
  
-   <span data-ttu-id="7b773-115">レポート処理の所要時間など、使用状況のメトリックを調べるには、レポート サーバーの実行ログを参照します。</span><span class="sxs-lookup"><span data-stu-id="7b773-115">To find out how long it takes to process a report and other usage metrics, review the report server execution log.</span></span> <span data-ttu-id="7b773-116">詳細については、「[レポートサーバー実行ログと ExecutionLog3 ビュー](report-server-executionlog-and-the-executionlog3-view.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7b773-116">For more information, see [Report Server Execution Log and the ExecutionLog3 View](report-server-executionlog-and-the-executionlog3-view.md).</span></span>  
  
-   <span data-ttu-id="7b773-117">メモリ管理構成設定をチューニングすることによってパフォーマンスの問題を緩和する方法の詳細については、「 [レポート サーバー アプリケーションで利用可能なメモリの構成](../report-server/configure-available-memory-for-report-server-applications.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7b773-117">For more information about how to mitigate performance issues by tuning memory management configuration settings, see [Configure Available Memory for Report Server Applications](../report-server/configure-available-memory-for-report-server-applications.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7b773-118">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="7b773-118">In This Section</span></span>  
 [<span data-ttu-id="7b773-119">レポート サーバーのパフォーマンスの監視</span><span class="sxs-lookup"><span data-stu-id="7b773-119">Monitoring Report Server Performance</span></span>](monitoring-report-server-performance.md)  
 <span data-ttu-id="7b773-120">サーバー上の処理負荷を追跡する際に使用できるパフォーマンス オブジェクトについて説明します。</span><span class="sxs-lookup"><span data-stu-id="7b773-120">Describes the performance objects you can use to track the processing load on your server.</span></span>  
  
 [<span data-ttu-id="7b773-121">レポート処理プロパティの設定</span><span class="sxs-lookup"><span data-stu-id="7b773-121">Set Report Processing Properties</span></span>](set-report-processing-properties.md)  
 <span data-ttu-id="7b773-122">要求時にキャッシュから、またはスケジュールに従ってレポート スナップショットとして、実行するレポートを構成する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="7b773-122">Describes ways of configuring a report to run on demand, from cache, or on a schedule as a report snapshot.</span></span>  
  
 [<span data-ttu-id="7b773-123">レポート サーバー アプリケーションで利用可能なメモリの構成</span><span class="sxs-lookup"><span data-stu-id="7b773-123">Configure Available Memory for Report Server Applications</span></span>](../report-server/configure-available-memory-for-report-server-applications.md)  
 <span data-ttu-id="7b773-124">既定のメモリ管理動作をオーバーライドする方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="7b773-124">Describes how you can override default memory management behavior.</span></span>  
  
 [<span data-ttu-id="7b773-125">レポートのキャッシュ (SSRS)</span><span class="sxs-lookup"><span data-stu-id="7b773-125">Caching Reports &#40;SSRS&#41;</span></span>](caching-reports-ssrs.md)  
 <span data-ttu-id="7b773-126">レポート サーバー上でのレポートのキャッシュの動作を説明します。</span><span class="sxs-lookup"><span data-stu-id="7b773-126">Describes report caching behavior on a report server.</span></span>  
  
 [<span data-ttu-id="7b773-127">共有データセットのキャッシュ &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="7b773-127">Cache Shared Datasets &#40;SSRS&#41;</span></span>](cache-shared-datasets-ssrs.md)  
 <span data-ttu-id="7b773-128">レポート サーバー上での共有データセットのキャッシュの動作を説明します。</span><span class="sxs-lookup"><span data-stu-id="7b773-128">Describes shared dataset caching behavior on a report server.</span></span>  
  
 [<span data-ttu-id="7b773-129">サイズの大きなレポートの処理</span><span class="sxs-lookup"><span data-stu-id="7b773-129">Process Large Reports</span></span>](process-large-reports.md)  
 <span data-ttu-id="7b773-130">サイズの大きいレポートを構成および配布する際の推奨事項を記載しています。</span><span class="sxs-lookup"><span data-stu-id="7b773-130">Provides recommendations on how to configure and distribute a large report.</span></span>  
  
 [<span data-ttu-id="7b773-131">レポートおよび共有データセット処理のタイムアウト値の設定 &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="7b773-131">Setting Time-out Values for Report and Shared Dataset Processing &#40;SSRS&#41;</span></span>](setting-time-out-values-for-report-and-shared-dataset-processing-ssrs.md)  
 <span data-ttu-id="7b773-132">クエリとレポート処理にタイムアウトを設定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7b773-132">Explains how to set time outs on query and report processing.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b773-133">参照</span><span class="sxs-lookup"><span data-stu-id="7b773-133">See Also</span></span>  
 <span data-ttu-id="7b773-134">[Manage a Running Process](../subscriptions/manage-a-running-process.md) </span><span class="sxs-lookup"><span data-stu-id="7b773-134">[Manage a Running Process](../subscriptions/manage-a-running-process.md) </span></span>  
 [<span data-ttu-id="7b773-135">レポート実行の確認</span><span class="sxs-lookup"><span data-stu-id="7b773-135">Verifying a Report Run</span></span>](verifying-a-report-run.md)  
  
  
