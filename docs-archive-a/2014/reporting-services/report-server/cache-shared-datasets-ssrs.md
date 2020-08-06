---
title: 複数の共有データセットのキャッシュ (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 4acb1bbe-1c04-4979-b893-dc1b1c5039b6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5b08149b075ae3fd267baf2dad0ca342457958c5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642576"
---
# <a name="cache-shared-datasets-ssrs"></a><span data-ttu-id="ef5e9-102">複数の共有データセットのキャッシュ (SSRS)</span><span class="sxs-lookup"><span data-stu-id="ef5e9-102">Cache Shared Datasets (SSRS)</span></span>
  <span data-ttu-id="ef5e9-103">共有データセットのクエリ結果をキャッシュにコピーしておくと、複数のレポートに一貫性のあるデータを提供し、データセット クエリの応答時間を短縮できます。</span><span class="sxs-lookup"><span data-stu-id="ef5e9-103">Query results for a shared dataset can be copied to a cache to provide consistent data for multiple reports and to improve response time for the dataset query.</span></span> <span data-ttu-id="ef5e9-104">レポートと同様に、初回使用時または指定されたスケジュールによってキャッシュされるように共有データセットを構成できます。</span><span class="sxs-lookup"><span data-stu-id="ef5e9-104">Like reports, you can configure a shared dataset to be cached on first use or by specifying a schedule.</span></span>  
  
 <span data-ttu-id="ef5e9-105">共有データセットは、複数のレポートに組み込んだり、コンポーネント定義の一部として含めたりすることができます。</span><span class="sxs-lookup"><span data-stu-id="ef5e9-105">A shared dataset can be included in multiple reports or as part of component definitions.</span></span> <span data-ttu-id="ef5e9-106">共有データセットをキャッシュすることによって、その共有データセットを使用するすべてのレポートに対して一貫したデータを提供すると共に、外部データ ソースに対してデータセット クエリが実行される回数を減らすことができます。</span><span class="sxs-lookup"><span data-stu-id="ef5e9-106">By caching the shared dataset, you provide a consistent set of data for all reports that use it, and also reduce the number of times that the dataset query runs against the external data source.</span></span>  
  
 <span data-ttu-id="ef5e9-107">次に、共有データセットをキャッシュする場合の例を示します。</span><span class="sxs-lookup"><span data-stu-id="ef5e9-107">The following list provides examples of when to cache a shared dataset:</span></span>  
  
-   <span data-ttu-id="ef5e9-108">クエリの実行にかなりの時間がかかる場合。</span><span class="sxs-lookup"><span data-stu-id="ef5e9-108">The query takes a substantial amount of time to run.</span></span>  
  
-   <span data-ttu-id="ef5e9-109">クエリにパラメーターがあるが、ほとんどの場合にパラメーターの組み合わせの数が少ない場合。</span><span class="sxs-lookup"><span data-stu-id="ef5e9-109">The query takes parameters, but most of the time, the number of parameter combinations is small.</span></span> <span data-ttu-id="ef5e9-110">各組み合わせに対してクエリ結果のキャッシュが作成されます。</span><span class="sxs-lookup"><span data-stu-id="ef5e9-110">Each combination creates cached query results.</span></span>  
  
-   <span data-ttu-id="ef5e9-111">1 日、1 週間、または 1 か月のうちの決まった時間や日付にクエリが実行される場合。</span><span class="sxs-lookup"><span data-stu-id="ef5e9-111">The query runs at predictable times of the day, week, or month.</span></span>  
  
-   <span data-ttu-id="ef5e9-112">電子メールで配信されたレポート内の共有データセット参照によってクエリが実行される場合で、短時間の間に多数のユーザーがそのリンクをクリックする可能性があるとき。</span><span class="sxs-lookup"><span data-stu-id="ef5e9-112">The query runs as the result of a shared dataset reference in a report that is delivered via e-mail, where a large number of people are likely to click the link in a short span of time.</span></span>  
  
-   <span data-ttu-id="ef5e9-113">次に、共有データセットをキャッシュしない場合の例を示します。</span><span class="sxs-lookup"><span data-stu-id="ef5e9-113">The following list provides examples of when not to cache a shared dataset:</span></span>  
  
-   <span data-ttu-id="ef5e9-114">クエリ結果に常に最新のデータを含める必要がある場合。</span><span class="sxs-lookup"><span data-stu-id="ef5e9-114">The query results must always include the most recent data.</span></span>  
  
-   <span data-ttu-id="ef5e9-115">クエリの実行時間が短い場合。</span><span class="sxs-lookup"><span data-stu-id="ef5e9-115">The query runs quickly.</span></span>  
  
-   <span data-ttu-id="ef5e9-116">クエリが頻繁には実行されない場合。</span><span class="sxs-lookup"><span data-stu-id="ef5e9-116">The query runs infrequently.</span></span>  
  
-   <span data-ttu-id="ef5e9-117">クエリにパラメーターがあり、パラメーターの組み合わせの数が多く、頻繁に使用される組み合わせも見つからない場合。</span><span class="sxs-lookup"><span data-stu-id="ef5e9-117">The query takes parameters, the number of parameter combinations is large, and no combination is more likely than another.</span></span>  
  
-   <span data-ttu-id="ef5e9-118">共有データセットの基礎となるデータ ソースにおいて、プロンプトまたは Windows 統合資格情報が使用されている場合。</span><span class="sxs-lookup"><span data-stu-id="ef5e9-118">The data source that the shared dataset is based on has Prompt or Windows Integrated credentials.</span></span>  
  
-   <span data-ttu-id="ef5e9-119">共有データセットのフィルターまたはクエリに、グローバル コレクション User を参照する式が含まれている場合。</span><span class="sxs-lookup"><span data-stu-id="ef5e9-119">The shared dataset filter or the query contains an expression with a reference to the global collection User.</span></span>  
  
 <span data-ttu-id="ef5e9-120">キャッシュされた結果セットに指定されている既定値とは異なるレポート パラメーター値をユーザーが選択した場合は、データセット クエリが実際に実行され、そのクエリではキャッシュされた結果は使用されません。</span><span class="sxs-lookup"><span data-stu-id="ef5e9-120">If a user chooses report parameter values that differ from the default values that are specified for the cached result set, the dataset query runs actively and the cached results are not used for that query.</span></span>  
  
## <a name="caching-shared-datasets"></a><span data-ttu-id="ef5e9-121">共有データセットをキャッシュする</span><span class="sxs-lookup"><span data-stu-id="ef5e9-121">Caching Shared Datasets</span></span>  
 <span data-ttu-id="ef5e9-122">共有データセットのキャッシュを有効にするには、共有データセットでキャッシュ オプションを選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ef5e9-122">To enable caching for a shared dataset, you must select the cache option on the shared dataset.</span></span> <span data-ttu-id="ef5e9-123">キャッシュが有効化されると、初回使用時に共有データセットのクエリ結果がキャッシュにコピーされます。</span><span class="sxs-lookup"><span data-stu-id="ef5e9-123">After caching is enabled, the query results for a shared dataset are copied to the cache on first use.</span></span> <span data-ttu-id="ef5e9-124">共有データセットにパラメーターがある場合は、パラメーターの各組み合わせに対して、キャッシュ内に新たなエントリが作成されます。</span><span class="sxs-lookup"><span data-stu-id="ef5e9-124">If the shared dataset has parameters, each combination of parameters creates a new entry in the cache.</span></span>  
  
 <span data-ttu-id="ef5e9-125">パラメーターの特定の組み合わせに対するクエリ結果がキャッシュ内にある間、それらのパラメーター値を持つ共有データセットを参照するレポートが起動されて処理されると、キャッシュされたデータが使用されます。</span><span class="sxs-lookup"><span data-stu-id="ef5e9-125">While the query results for a specific parameter combination are in the cache, each report that is launched for processing and that includes a reference to the shared dataset with those parameter values will use the cached data.</span></span>  
  
 <span data-ttu-id="ef5e9-126">キャッシュ内にデータを保持する有効期限が切れるまでの期間を指定できます。</span><span class="sxs-lookup"><span data-stu-id="ef5e9-126">You can specify how long to keep data in the cache before it expires.</span></span> <span data-ttu-id="ef5e9-127">詳細については、「[共有データセットの [キャッシュ] ページ &#40;レポート マネージャー&#41;](../caching-page-shared-datasets-report-manager.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ef5e9-127">For more information, see [Caching Page, Shared Datasets &#40;Report Manager&#41;](../caching-page-shared-datasets-report-manager.md).</span></span>  
  
## <a name="preloading-the-cache"></a><span data-ttu-id="ef5e9-128">キャッシュを事前に読み込む</span><span class="sxs-lookup"><span data-stu-id="ef5e9-128">Preloading the Cache</span></span>  
 <span data-ttu-id="ef5e9-129">キャッシュ更新計画を作成することによって、キャッシュを事前に読み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="ef5e9-129">You can preload the cache by creating a cache refresh plan.</span></span> <span data-ttu-id="ef5e9-130">更新計画を使用すると、アイテム固有のスケジュールまたは共有スケジュールを使用して、キャッシュを更新する頻度を指定できます。</span><span class="sxs-lookup"><span data-stu-id="ef5e9-130">With a refresh plan, you can specify how often to refresh the cache by using an item-specific schedule or a shared schedule.</span></span> <span data-ttu-id="ef5e9-131">同一アイテムに対して複数のキャッシュ エントリが作成されることを防ぐため、スケジュールでは、外部データ ソースに対するクエリ処理が実行されるのに十分な時間を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ef5e9-131">To avoid multiple cache entries for the same item, the schedule that you specify should allow enough time for query processing on the external data source.</span></span> <span data-ttu-id="ef5e9-132">たとえば、クエリの実行に 20 分かかる場合は、更新スケジュール間隔も 20 分より長くする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ef5e9-132">For example, if the query takes 20 minutes to run, the refresh schedule should be greater than 20 minutes.</span></span> <span data-ttu-id="ef5e9-133">詳細については、「 [Schedules](../subscriptions/schedules.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ef5e9-133">For more information, see [Schedules](../subscriptions/schedules.md).</span></span>  
  
 <span data-ttu-id="ef5e9-134">共有データセットに対してキャッシュ更新計画を作成する場合は、次の条件が満たされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="ef5e9-134">To create a cache refresh plan for a shared dataset, the following conditions apply.</span></span>  
  
-   <span data-ttu-id="ef5e9-135">共有データセットでキャッシュが有効化されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="ef5e9-135">The shared dataset must be enabled for caching.</span></span>  
  
-   <span data-ttu-id="ef5e9-136">共有データセットが依存する共有データ ソースにおいて、プロンプトまたは Windows 統合資格情報が使用されていない必要があります。</span><span class="sxs-lookup"><span data-stu-id="ef5e9-136">The shared data source that the shared dataset depends on cannot use Prompt or Windows Integrated credentials.</span></span>  
  
-   <span data-ttu-id="ef5e9-137">共有データセットにパラメーターがある場合は、読み取り専用とマークされていない各パラメーターに対して、静的な既定値を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ef5e9-137">If the shared dataset has parameters, you must specify static default values for each parameter that is not marked read-only.</span></span> <span data-ttu-id="ef5e9-138">読み取り専用パラメーターでは、常に既定値が使用されます。</span><span class="sxs-lookup"><span data-stu-id="ef5e9-138">Read-only parameters will always use the default value.</span></span> <span data-ttu-id="ef5e9-139">パラメーターの複数の組み合わせに対して共有データセットをキャッシュするには、値の各組み合わせに対して別々のキャッシュ更新計画を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ef5e9-139">To cache a shared dataset for multiple combinations of parameters, you must create a separate cache refresh plan for each combination of values.</span></span> <span data-ttu-id="ef5e9-140">パラメーターには、他のデータセットへの参照を含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="ef5e9-140">Parameters cannot contain references to other datasets.</span></span>  
  
-   <span data-ttu-id="ef5e9-141">各キャッシュ更新計画は、1 つの共有データセットまたはレポートにのみ関連付けられている必要があります。</span><span class="sxs-lookup"><span data-stu-id="ef5e9-141">Each cache refresh plan is associated with only one shared dataset or report.</span></span>  
  
-   <span data-ttu-id="ef5e9-142">共有データセットに対して ReadPolicy 権限および UpdatePolicy 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="ef5e9-142">You must have ReadPolicy and UpdatePolicy permissions on the shared dataset.</span></span>  
  
 <span data-ttu-id="ef5e9-143">キャッシュ更新計画は、共有データセットおよびレポートの両方に適用されます。</span><span class="sxs-lookup"><span data-stu-id="ef5e9-143">Cache refresh plans apply to both shared datasets and reports.</span></span> <span data-ttu-id="ef5e9-144">詳細については、「[キャッシュ更新オプション &#40;レポート マネージャー&#41;](../cache-refresh-options-report-manager.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ef5e9-144">For more information, see [Cache Refresh Options &#40;Report Manager&#41;](../cache-refresh-options-report-manager.md).</span></span>  
  
## <a name="conditions-that-cause-cache-expiration"></a><span data-ttu-id="ef5e9-145">キャッシュが有効期限切れとなる条件</span><span class="sxs-lookup"><span data-stu-id="ef5e9-145">Conditions that Cause Cache Expiration</span></span>  
 <span data-ttu-id="ef5e9-146">次の状況においては、共有データセット キャッシュが無効になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ef5e9-146">The following conditions can cause a shared dataset cache to become not valid.</span></span>  
  
-   <span data-ttu-id="ef5e9-147">スケジュール条件の期限が切れた場合。</span><span class="sxs-lookup"><span data-stu-id="ef5e9-147">A schedule condition expires.</span></span> <span data-ttu-id="ef5e9-148">キャッシュ タイムアウトまたは有効期限切れが発生します。</span><span class="sxs-lookup"><span data-stu-id="ef5e9-148">The cache times out or the expiration time occurs.</span></span>  
  
-   <span data-ttu-id="ef5e9-149">共有スケジュールが削除された場合。</span><span class="sxs-lookup"><span data-stu-id="ef5e9-149">A shared schedule is deleted.</span></span>  
  
-   <span data-ttu-id="ef5e9-150">共有スケジュールが変更された場合。</span><span class="sxs-lookup"><span data-stu-id="ef5e9-150">Changes to a shared schedule.</span></span> <span data-ttu-id="ef5e9-151">共有スケジュールは一時停止することができますが、これによってもキャッシュの有効期限が影響を受けます。</span><span class="sxs-lookup"><span data-stu-id="ef5e9-151">Shared schedules can be paused, which also affects when a cache expires.</span></span>  
  
-   <span data-ttu-id="ef5e9-152">共有データセットのクエリ定義が変更された場合。</span><span class="sxs-lookup"><span data-stu-id="ef5e9-152">The query definition for the shared dataset changes.</span></span>  
  
-   <span data-ttu-id="ef5e9-153">共有データセットが依存する共有データ ソースの資格情報が変更された場合。</span><span class="sxs-lookup"><span data-stu-id="ef5e9-153">The credentials for the shared data source that the shared dataset depends on change.</span></span>  
  
-   <span data-ttu-id="ef5e9-154">共有データセットのキャッシュ オプションが変更された場合。</span><span class="sxs-lookup"><span data-stu-id="ef5e9-154">The cache options for the shared dataset change.</span></span>  
  
-   <span data-ttu-id="ef5e9-155">共有データセットの読み取り専用パラメーターの既定値が変更された場合。</span><span class="sxs-lookup"><span data-stu-id="ef5e9-155">The default values for read-only parameters for the shared dataset change.</span></span>  
  
-   <span data-ttu-id="ef5e9-156">共有データセット定義の一部であるフィルターが変更された場合。</span><span class="sxs-lookup"><span data-stu-id="ef5e9-156">The filters that are part of the shared dataset definition change.</span></span>  
  
-   <span data-ttu-id="ef5e9-157">レポート サーバーから共有データセットが削除された場合。</span><span class="sxs-lookup"><span data-stu-id="ef5e9-157">The shared dataset is deleted from the report server.</span></span> <span data-ttu-id="ef5e9-158">共有データセットが削除されると、関連するキャッシュされたコピーおよびキャッシュ更新計画も削除されます。</span><span class="sxs-lookup"><span data-stu-id="ef5e9-158">When a shared dataset is deleted, associated cached copies and cache refresh plans are also deleted.</span></span>  
  
 <span data-ttu-id="ef5e9-159">共有データセットのキャッシュ更新計画を更新しても、既に処理中のレポートには影響がありません。</span><span class="sxs-lookup"><span data-stu-id="ef5e9-159">Updates to cache refresh plans for shared datasets do not affect reports that are already being processed.</span></span> <span data-ttu-id="ef5e9-160">キャッシュ更新計画の更新は、共有データセットを参照する、これから起動されるレポートにのみ影響があります。</span><span class="sxs-lookup"><span data-stu-id="ef5e9-160">Updating a cache refresh plan affects only future launches of reports that reference the shared dataset.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef5e9-161">参照</span><span class="sxs-lookup"><span data-stu-id="ef5e9-161">See Also</span></span>  
 [<span data-ttu-id="ef5e9-162">共有データセットを管理する</span><span class="sxs-lookup"><span data-stu-id="ef5e9-162">Manage Shared Datasets</span></span>](../report-data/manage-shared-datasets.md)  
  
  
