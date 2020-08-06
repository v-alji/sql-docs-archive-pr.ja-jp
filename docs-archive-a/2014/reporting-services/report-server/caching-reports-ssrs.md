---
title: レポートのキャッシュ (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- report execution properties [Reporting Services]
- cache [Reporting Services]
- report processing [Reporting Services], caching
- cached instances [Reporting Services]
- refreshing cache
- cached reports [Reporting Services]
- preloading cache
- invalid cached reports [Reporting Services]
- performance [Reporting Services]
- expiration [Reporting Services]
- snapshots [Reporting Services], caching
ms.assetid: 146542c3-8efd-4b89-a8d8-77d22896630e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e1af19dd3848ba39f91c2fc640a57ca53c35a4fb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642575"
---
# <a name="caching-reports-ssrs"></a><span data-ttu-id="57674-102">複数のレポートのキャッシュ (SSRS)</span><span class="sxs-lookup"><span data-stu-id="57674-102">Caching Reports (SSRS)</span></span>
  <span data-ttu-id="57674-103">レポート サーバーでは、処理済みレポートのコピーをキャッシュして、ユーザーがレポートを開いたときにそのコピーを返すことができます。</span><span class="sxs-lookup"><span data-stu-id="57674-103">A report server can cache a copy of a processed report and return that copy when a user opens the report.</span></span> <span data-ttu-id="57674-104">レポートがキャッシュされたコピーかどうかをユーザーが判断できる唯一の方法は、レポートが実行された日時を確認することです。</span><span class="sxs-lookup"><span data-stu-id="57674-104">To a user, the only evidence available to indicate the report is a cached copy is the date and time that the report ran.</span></span> <span data-ttu-id="57674-105">その日時が現在の日時ではなく、レポートがスナップショットでない場合、そのレポートはキャッシュから取得されたレポートです。</span><span class="sxs-lookup"><span data-stu-id="57674-105">If the date or time is not current and the report is not a snapshot, the report was retrieved from cache.</span></span>  
  
 <span data-ttu-id="57674-106">レポートのサイズが大きい場合やレポートへのアクセスが頻繁に行われる場合、キャッシュを行うことでレポートの取得にかかる時間を短縮できます。</span><span class="sxs-lookup"><span data-stu-id="57674-106">Caching can shorten the time required to retrieve a report if the report is large or accessed frequently.</span></span> <span data-ttu-id="57674-107">サーバーを再起動した場合、レポート サーバー Web サービスをオンラインに戻すと、キャッシュされたすべてのインスタンスが修復されます。</span><span class="sxs-lookup"><span data-stu-id="57674-107">If the server is rebooted, all cached instances are reinstated when the Report Server Web service comes back online.</span></span>  
  
 <span data-ttu-id="57674-108">キャッシュは、パフォーマンスを向上させる技法です。</span><span class="sxs-lookup"><span data-stu-id="57674-108">Caching is a performance-enhancement technique.</span></span> <span data-ttu-id="57674-109">キャッシュのコンテンツは変動するので、レポートを追加、置換、または削除すると変更できます。</span><span class="sxs-lookup"><span data-stu-id="57674-109">The contents of the cache are volatile and can change as reports are added, replaced, or removed.</span></span> <span data-ttu-id="57674-110">より予測可能なキャッシュ方法が必要な場合、レポート スナップショットを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="57674-110">If you require a more predictable caching strategy, you should create a report snapshot.</span></span> <span data-ttu-id="57674-111">詳細については、「 [レポート処理プロパティの設定](set-report-processing-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="57674-111">For more information, see [Set Report Processing Properties](set-report-processing-properties.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="57674-112">では、データベースに一時ファイルが保持され、ユーザー セッションやレポート処理のサポートに使用されます。</span><span class="sxs-lookup"><span data-stu-id="57674-112">stores temporary files in a database to support user sessions and report processing.</span></span> <span data-ttu-id="57674-113">これらのファイルは内部使用を目的にキャッシュされ、単一のブラウザー セッションの間、表示状態の整合性を保つために使用されます。</span><span class="sxs-lookup"><span data-stu-id="57674-113">These files are cached for internal use and to support a consistent viewing experience during a single browser session.</span></span> <span data-ttu-id="57674-114">内部使用を目的とした一時ファイルのキャッシュ方法の詳細については、「[レポート サーバー データベース &#40;SSRS ネイティブ モード&#41;](report-server-database-ssrs-native-mode.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="57674-114">For more information about how internal-use temporary files are cached, see [Report Server Database &#40;SSRS Native Mode&#41;](report-server-database-ssrs-native-mode.md).</span></span>  
  
## <a name="cached-instances"></a><span data-ttu-id="57674-115">キャッシュされたインスタンス</span><span class="sxs-lookup"><span data-stu-id="57674-115">Cached Instances</span></span>  
 <span data-ttu-id="57674-116">キャッシュされたレポートのインスタンスは、レポートの中間形式に基づいています。</span><span class="sxs-lookup"><span data-stu-id="57674-116">A cached instance of a report is based on the intermediate format of a report.</span></span> <span data-ttu-id="57674-117">通常、レポート サーバーでは、レポート名に基づいてレポートのインスタンスが 1 つキャッシュされます。</span><span class="sxs-lookup"><span data-stu-id="57674-117">The report server generally caches one instance of a report based on the report name.</span></span> <span data-ttu-id="57674-118">ただし、クエリ パラメーターに基づいてレポートに別のデータを含めることができる場合、任意の指定された時間に複数のバージョンのレポートがキャッシュされることがあります。</span><span class="sxs-lookup"><span data-stu-id="57674-118">However, if a report can contain different data based on query parameters, multiple versions of the report may be cached at any given time.</span></span> <span data-ttu-id="57674-119">たとえば、パラメーター値として地域コードを取得するパラメーター化されたレポートがあるとします。</span><span class="sxs-lookup"><span data-stu-id="57674-119">For example, suppose you have a parameterized report that takes a region code as a parameter value.</span></span> <span data-ttu-id="57674-120">4 人の異なるユーザーが、4 つの一意の地域コードを指定した場合、キャッシュされたコピーが 4 つ作成されます。</span><span class="sxs-lookup"><span data-stu-id="57674-120">If four different users specify four unique region codes, four cached copies are created.</span></span>  
  
 <span data-ttu-id="57674-121">一意の地域コードを含んだレポートを実行する最初のユーザーは、その地域のデータを含むキャッシュされたレポートを作成します。</span><span class="sxs-lookup"><span data-stu-id="57674-121">The first user who runs the report with a unique region code creates a cached report that contains data for that region.</span></span> <span data-ttu-id="57674-122">同じ地域コードを使用してレポートを要求する後続のユーザーは、キャッシュされたコピーを取得します。</span><span class="sxs-lookup"><span data-stu-id="57674-122">Subsequent users who request the report using the same region code get the cached copy.</span></span>  
  
 <span data-ttu-id="57674-123">すべてのレポートをキャッシュできるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="57674-123">Not all reports can be cached.</span></span> <span data-ttu-id="57674-124">レポートにユーザー依存データが含まれる場合、レポートで資格情報の入力が必要となる場合、またはレポートで Windows 認証が使用される場合は、レポートをキャッシュできません。</span><span class="sxs-lookup"><span data-stu-id="57674-124">If a report includes user-dependent data, prompts users for credentials, or uses Windows Authentication, it cannot be cached.</span></span>  
  
## <a name="refreshing-the-cache"></a><span data-ttu-id="57674-125">キャッシュの更新</span><span class="sxs-lookup"><span data-stu-id="57674-125">Refreshing the Cache</span></span>  
 <span data-ttu-id="57674-126">以前にキャッシュされたコピーの有効期限が切れた後でユーザーがレポートを選択すると、キャッシュされたレポートが新しいバージョンに置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="57674-126">A cached report is replaced with a newer version when a user selects the report after the previously cached copy has expired.</span></span> <span data-ttu-id="57674-127">キャッシュされたインスタンスとして実行するように構成されたレポートは、有効期限の設定に基づいてキャッシュから定期的に削除されます。</span><span class="sxs-lookup"><span data-stu-id="57674-127">Reports that are configured to run as cached instances are removed from the cache at regular intervals based on expiration settings.</span></span> <span data-ttu-id="57674-128">レポートの有効期限は分単位で設定することも、スケジュールされた時間に設定することもできます。どちらの設定を使用するかは、データに要求される即時性に基づいて決定します。</span><span class="sxs-lookup"><span data-stu-id="57674-128">You can set a report's expiration in minutes or at a scheduled time, as determined by the data's immediacy requirement.</span></span> <span data-ttu-id="57674-129">SOAP API を使用する以外の方法で、キャッシュからレポートを直接削除することはできません。</span><span class="sxs-lookup"><span data-stu-id="57674-129">You cannot delete reports from the cache directly unless you use the SOAP API.</span></span>  
  
 <span data-ttu-id="57674-130">キャッシュの有効期限を構成するには、共有スケジュールまたはレポート固有スケジュールを使用します。</span><span class="sxs-lookup"><span data-stu-id="57674-130">To configure cache expiration, you can use a shared schedule or report-specific schedule.</span></span> <span data-ttu-id="57674-131">共有スケジュールを使用し、その後に続けて共有スケジュールを一時停止した場合、スケジュールが停止している間はキャッシュ期限が切れることはありません。</span><span class="sxs-lookup"><span data-stu-id="57674-131">If you use a shared schedule and it is subsequently paused, the cache does not expire while the schedule is inoperative.</span></span> <span data-ttu-id="57674-132">続けて共有スケジュールを削除した場合、スケジュール設定のコピーがレポート固有スケジュールとして保存されます。</span><span class="sxs-lookup"><span data-stu-id="57674-132">If the shared schedule is subsequently deleted, a copy of the schedule settings is saved as a report-specific schedule.</span></span>  
  
 <span data-ttu-id="57674-133">スケジュールの有効期限が切れた場合、またはキャッシュの有効期限日にスケジュール エンジンを利用できない場合は、スケジュールを延長するか、スケジュールされているサービスを開始することで、スケジュールされた操作を再開できるまでレポート サーバーでアクティブなレポートが実行されます。</span><span class="sxs-lookup"><span data-stu-id="57674-133">If a schedule expires or if the scheduling engine is unavailable at a cache expiration date, the report server runs a live report until scheduled operations can be resumed (by either extending the schedule or starting the scheduling service).</span></span>  
  
## <a name="preloading-the-cache"></a><span data-ttu-id="57674-134">キャッシュを事前に読み込む</span><span class="sxs-lookup"><span data-stu-id="57674-134">Preloading the Cache</span></span>  
 <span data-ttu-id="57674-135">キャッシュの事前読み込みを使用すると、サーバーのパフォーマンスを向上できます。</span><span class="sxs-lookup"><span data-stu-id="57674-135">To improve server performance, you can preload the cache.</span></span> <span data-ttu-id="57674-136">パラメーター化されたレポートのインスタンスのコレクションをキャッシュに事前に読み込むには、次の 2 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="57674-136">You can preload the cache with a collection of parameterized report instances in two ways:</span></span>  
  
1.  <span data-ttu-id="57674-137">キャッシュの更新プランを作成します。</span><span class="sxs-lookup"><span data-stu-id="57674-137">Create a cache refresh plan.</span></span> <span data-ttu-id="57674-138">更新プランを作成すると、1 つのレポートのスケジュールや共有スケジュールを指定できます。</span><span class="sxs-lookup"><span data-stu-id="57674-138">When you create a refresh plan, you can specify a schedule for a single report or specify a shared schedule.</span></span>  
  
2.  <span data-ttu-id="57674-139">NULL 配信プロバイダーを使用するデータ ドリブン サブスクリプションを作成します。</span><span class="sxs-lookup"><span data-stu-id="57674-139">Create a data-driven subscription that uses the Null Delivery Provider.</span></span> <span data-ttu-id="57674-140">NULL 配信プロバイダーを配信方法としてサブスクリプションに指定すると、レポート サーバーはレポート サーバー データベースを配信先に設定し、NULL 表示拡張機能と呼ばれる特殊な表示拡張機能を使用します。</span><span class="sxs-lookup"><span data-stu-id="57674-140">When you specify the Null Delivery Provider as the method of delivery in the subscription, the report server targets the report server database as the delivery destination and uses a specialized rendering extension called the null rendering extension.</span></span> <span data-ttu-id="57674-141">NULL 配信プロバイダーでは、他の配信拡張機能とは異なり、サブスクリプションの定義から構成できる配信設定がありません。</span><span class="sxs-lookup"><span data-stu-id="57674-141">In contrast with other delivery extensions, the Null Delivery Provider does not have delivery settings that you can configure through a subscription definition.</span></span>  
  
 <span data-ttu-id="57674-142">レポートのキャッシュは、パラメーター化されたレポートの複数のインスタンスをキャッシュする場合に特に役立ちます。この場合、さまざまなレポートのインスタンスを生成するために個別のパラメーター値が使用されます。</span><span class="sxs-lookup"><span data-stu-id="57674-142">Caching a report is especially useful if you want to cache multiple instances of a parameterized report where different parameter values are used to produce different report instances.</span></span> <span data-ttu-id="57674-143">レポートには、クエリ ベースのパラメーターのみを指定できることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="57674-143">Note that you can only specify query-based parameters on the report.</span></span>  
  
 <span data-ttu-id="57674-144">スケジュールを指定する場合や、データ ドリブン サブスクリプションを作成する場合は、キャッシュに対するレポートの配信頻度をスケジュールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="57674-144">When you specify a schedule or when you create the data-driven subscription, you schedule how often the reports are delivered to the cache.</span></span> <span data-ttu-id="57674-145">古いコピーの有効期限が切れていない場合、新しいコピーはキャッシュに配信されません。</span><span class="sxs-lookup"><span data-stu-id="57674-145">In order for new copies to be delivered to the cache, the old copies must have expired.</span></span> <span data-ttu-id="57674-146">したがって、レポートの実行プロパティの構成には、キャッシュの有効期限の設定を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="57674-146">Therefore, the Execution properties of the report must be configured to include cache expiration settings.</span></span> <span data-ttu-id="57674-147">この有効期限の設定には、定義するサブスクリプションのスケジュールとの一貫性が必要です。</span><span class="sxs-lookup"><span data-stu-id="57674-147">The expiration setting must be consistent with the subscription schedule that you define.</span></span> <span data-ttu-id="57674-148">たとえば、毎晩実行されるサブスクリプションを作成する場合、サブスクリプションが実行される前に、キャッシュも毎晩、有効期限切れになる必要があります。</span><span class="sxs-lookup"><span data-stu-id="57674-148">For example, if you create a subscription that runs every night, the cache should also expire every night prior to the subscription's run time.</span></span> <span data-ttu-id="57674-149">実行プロパティに有効期限の日時が含まれていない場合、新しい配信が無視されます。</span><span class="sxs-lookup"><span data-stu-id="57674-149">If the Execution properties do not include expiration times, newer deliveries are disregarded.</span></span> <span data-ttu-id="57674-150">キャッシュの更新の詳細については、「 [スケジュール](../subscriptions/schedules.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="57674-150">For more information about cache refresh plans, see [Schedules](../subscriptions/schedules.md).</span></span> <span data-ttu-id="57674-151">プロパティの設定方法については、「 [レポート処理プロパティの設定](set-report-processing-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="57674-151">For more information about setting properties, see [Set Report Processing Properties](set-report-processing-properties.md).</span></span> <span data-ttu-id="57674-152">データ ドリブン サブスクリプションの使用に関する詳細については、「 [データ ドリブン サブスクリプション](../subscriptions/data-driven-subscriptions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="57674-152">For more information about using data-driven subscriptions, see [Data-Driven Subscriptions](../subscriptions/data-driven-subscriptions.md).</span></span>  
  
## <a name="conditions-that-cause-cache-expiration"></a><span data-ttu-id="57674-153">キャッシュが有効期限切れとなる条件</span><span class="sxs-lookup"><span data-stu-id="57674-153">Conditions That Cause Cache Expiration</span></span>  
 <span data-ttu-id="57674-154">レポート定義の変更、レポート パラメーターの変更、データ ソースの資格情報の変更、レポート実行オプションの変更などのイベントが発生すると、キャッシュされたレポートが無効になります。</span><span class="sxs-lookup"><span data-stu-id="57674-154">A cached report is invalidated in response to the following events: the report definition is modified, report parameters are modified, data source credentials change, or report execution options change.</span></span> <span data-ttu-id="57674-155">キャッシュに格納されたレポートを削除する場合、キャッシュされたバージョンのレポートも削除されます。</span><span class="sxs-lookup"><span data-stu-id="57674-155">If you delete a report that is stored in the cache, the cached version is also deleted.</span></span>  
  
 <span data-ttu-id="57674-156">何らかの理由で、キャッシュされたインスタンスでレポートを実行できない場合 (たとえば、ユーザーが指定したパラメーター値が、キャッシュされたレポートの生成に使用するパラメーター値と異なる場合)、レポート サーバーでレポートが再実行されます。</span><span class="sxs-lookup"><span data-stu-id="57674-156">If a report cannot be rendered from a cached instance for any reason (for example, if the parameter values that a user specifies are different from those used to produce the cached report), the report server reruns the report.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57674-157">参照</span><span class="sxs-lookup"><span data-stu-id="57674-157">See Also</span></span>  
 <span data-ttu-id="57674-158">[処理オプションの設定 &#40;Reporting Services の SharePoint 統合モード&#41;](../set-processing-options-reporting-services-in-sharepoint-integrated-mode.md) </span><span class="sxs-lookup"><span data-stu-id="57674-158">[Set Processing Options &#40;Reporting Services in SharePoint Integrated Mode&#41;](../set-processing-options-reporting-services-in-sharepoint-integrated-mode.md) </span></span>  
 <span data-ttu-id="57674-159">[レポート処理プロパティの設定](set-report-processing-properties.md) </span><span class="sxs-lookup"><span data-stu-id="57674-159">[Set Report Processing Properties](set-report-processing-properties.md) </span></span>  
 <span data-ttu-id="57674-160">[Reporting Services の概念 &#40;SSRS&#41;](../reporting-services-concepts-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="57674-160">[Reporting Services Concepts &#40;SSRS&#41;](../reporting-services-concepts-ssrs.md) </span></span>  
 <span data-ttu-id="57674-161">[キャッシュ &#40;レポートマネージャーを事前に読み込む&#41;](preload-the-cache-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="57674-161">[Preload the Cache &#40;Report Manager&#41;](preload-the-cache-report-manager.md) </span></span>  
 <span data-ttu-id="57674-162">[[スケジュール]](../subscriptions/schedules.md) </span><span class="sxs-lookup"><span data-stu-id="57674-162">[Schedules](../subscriptions/schedules.md) </span></span>  
 <span data-ttu-id="57674-163">[SSRS&#41;&#40;共有データセットをキャッシュする](cache-shared-datasets-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="57674-163">[Cache Shared Datasets &#40;SSRS&#41;](cache-shared-datasets-ssrs.md) </span></span>  
 <span data-ttu-id="57674-164">[[キャッシュ更新オプション] &#40;レポート マネージャー&#41;](../cache-refresh-options-report-manager.md)</span><span class="sxs-lookup"><span data-stu-id="57674-164">[Cache Refresh Options &#40;Report Manager&#41;](../cache-refresh-options-report-manager.md)</span></span>  
  
  