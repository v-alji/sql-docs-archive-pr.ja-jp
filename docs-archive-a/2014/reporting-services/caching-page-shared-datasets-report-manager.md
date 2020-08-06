---
title: 共有データセットの [キャッシュ] ページ (レポートマネージャー) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: eac372e9-d2a1-48a8-bbe5-09d101df16ea
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 62d899964911a6f2d35e59d49d925ff80013af42
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640773"
---
# <a name="caching-page-shared-datasets-report-manager"></a><span data-ttu-id="97efe-102">共有データセットの [キャッシュ] ページ (レポート マネージャー)</span><span class="sxs-lookup"><span data-stu-id="97efe-102">Caching Page, Shared Datasets (Report Manager)</span></span>
  <span data-ttu-id="97efe-103">共有データセットのキャッシュ オプションを設定するには、[キャッシュ] プロパティ ページを使用します。</span><span class="sxs-lookup"><span data-stu-id="97efe-103">Use the Caching properties page to set the cache options for a shared dataset.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="97efe-104">この機能は、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]のすべてのエディションで使用できるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="97efe-104">This feature is not available in every edition of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="97efe-105">の各エディションでサポートされる機能の一覧につい [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ては、「 [SQL Server 2014 の各エディションがサポートする機能](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="97efe-105">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="97efe-106">ナビゲーション</span><span class="sxs-lookup"><span data-stu-id="97efe-106">Navigation</span></span>  
 <span data-ttu-id="97efe-107">このページに移動するには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="97efe-107">Use the following procedure to navigate to this location in the user interface.</span></span>  
  
### <a name="to-open-the-caching-properties-page-for-a-shared-dataset"></a><span data-ttu-id="97efe-108">共有データセットの [キャッシュ] プロパティ ページを開くには</span><span class="sxs-lookup"><span data-stu-id="97efe-108">To open the Caching properties page for a shared dataset</span></span>  
  
1.  <span data-ttu-id="97efe-109">レポート マネージャーを開き、共有データセットのプロパティを構成するレポートを探します。</span><span class="sxs-lookup"><span data-stu-id="97efe-109">Open Report Manager, and locate the report for which you want to configure shared dataset properties.</span></span>  
  
2.  <span data-ttu-id="97efe-110">共有データセットの上にマウス ポインターを移動し、下矢印をクリックします。</span><span class="sxs-lookup"><span data-stu-id="97efe-110">Point to the shared dataset, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="97efe-111">ドロップダウン リストの **[管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="97efe-111">In the drop-down list, click **Manage**.</span></span> <span data-ttu-id="97efe-112">レポートの [全般] プロパティ ページが開きます。</span><span class="sxs-lookup"><span data-stu-id="97efe-112">The General properties page for the report opens.</span></span>  
  
4.  <span data-ttu-id="97efe-113">**[キャッシュ]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="97efe-113">Click the **Caching** tab.</span></span>  
  
## <a name="options"></a><span data-ttu-id="97efe-114">Options</span><span class="sxs-lookup"><span data-stu-id="97efe-114">Options</span></span>  
 <span data-ttu-id="97efe-115">**[共有データセットをキャッシュする]**</span><span class="sxs-lookup"><span data-stu-id="97efe-115">**Cache shared dataset**</span></span>  
 <span data-ttu-id="97efe-116">この共有データセットを使用するレポートをユーザーが最初に開いたときに、データの一時コピーをキャッシュに配置します。</span><span class="sxs-lookup"><span data-stu-id="97efe-116">Places a temporary copy of the data in a cache when a user first opens a report that uses this shared dataset.</span></span> <span data-ttu-id="97efe-117">キャッシュ期間内にレポートを実行する後続のユーザーは、データのキャッシュされたコピーを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="97efe-117">Subsequent users who run the report within the caching period receive the cached copy of the data.</span></span> <span data-ttu-id="97efe-118">再度データセット クエリを実行することなくデータがキャッシュから返されるので、通常はキャッシュによってパフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="97efe-118">Caching usually improves performance because the data is returned from the cache instead of running the dataset query again.</span></span>  
  
 <span data-ttu-id="97efe-119">**[キャッシュが期限切れになるまでの時間 (分)]**</span><span class="sxs-lookup"><span data-stu-id="97efe-119">**Expire the cache after a number of minutes**</span></span>  
 <span data-ttu-id="97efe-120">キャッシュされたデータのコピーを保存する時間 (分単位) を指定します。</span><span class="sxs-lookup"><span data-stu-id="97efe-120">Specify the number of minutes to save the cached copy of the data.</span></span> <span data-ttu-id="97efe-121">一時コピーの有効期限が切れると、データはキャッシュから返されなくなります。</span><span class="sxs-lookup"><span data-stu-id="97efe-121">As soon as a temporary copy expires, the data is no longer returned from the cache.</span></span> <span data-ttu-id="97efe-122">次にこの共有データセットを使用するレポートをユーザーが開いたときに、データセット クエリが実行され、レポート サーバーによって、更新されたデータのコピーがキャッシュに配置されます。</span><span class="sxs-lookup"><span data-stu-id="97efe-122">The next time a user opens a report that uses this shared dataset, the dataset query runs and the report server places a copy of the refreshed data back in the cache.</span></span>  
  
 <span data-ttu-id="97efe-123">**[次のスケジュールでキャッシュを期限切れにします]**</span><span class="sxs-lookup"><span data-stu-id="97efe-123">**Expire the cache on the following schedule**</span></span>  
 <span data-ttu-id="97efe-124">キャッシュされたデータを無効にしてキャッシュから削除するタイミングを示すスケジュールを設定します。</span><span class="sxs-lookup"><span data-stu-id="97efe-124">Schedule the time when the cached data is no longer valid and is removed from the cache.</span></span> <span data-ttu-id="97efe-125">このスケジュールは、共有スケジュールにすることも、現在の共有データセットのみに固有のスケジュールにすることもできます。</span><span class="sxs-lookup"><span data-stu-id="97efe-125">The schedule can be a shared schedule or one that is specific for only the current shared dataset.</span></span>  
  
 <span data-ttu-id="97efe-126">**[データセット固有のスケジュール]**</span><span class="sxs-lookup"><span data-stu-id="97efe-126">**Dataset-specific schedule**</span></span>  
 <span data-ttu-id="97efe-127">このデータセットのみによって使用されるスケジュールを指定します。</span><span class="sxs-lookup"><span data-stu-id="97efe-127">Specify a schedule that is used only by this dataset.</span></span>  
  
 <span data-ttu-id="97efe-128">**共有スケジュール**</span><span class="sxs-lookup"><span data-stu-id="97efe-128">**Shared schedule**</span></span>  
 <span data-ttu-id="97efe-129">レポート、サブスクリプション、および他の共有データセットによって共有されるスケジュールを指定します。</span><span class="sxs-lookup"><span data-stu-id="97efe-129">Specify a schedule that is shared among reports, subscriptions, and other shared datasets.</span></span>  
  
 <span data-ttu-id="97efe-130">**[適用]**</span><span class="sxs-lookup"><span data-stu-id="97efe-130">**Apply**</span></span>  
 <span data-ttu-id="97efe-131">変更を保存します。</span><span class="sxs-lookup"><span data-stu-id="97efe-131">Save your changes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97efe-132">参照</span><span class="sxs-lookup"><span data-stu-id="97efe-132">See Also</span></span>  
 <span data-ttu-id="97efe-133">[レポート マネージャー &#40;SSRS ネイティブ モード&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="97efe-133">[Report Manager  &#40;SSRS Native Mode&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="97efe-134">[レポートマネージャーの F1 ヘルプ](../../2014/reporting-services/report-manager-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="97efe-134">[Report Manager F1 Help](../../2014/reporting-services/report-manager-f1-help.md) </span></span>  
 <span data-ttu-id="97efe-135">[SSRS&#41;&#40;共有データセットをキャッシュする](report-server/cache-shared-datasets-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="97efe-135">[Cache Shared Datasets &#40;SSRS&#41;](report-server/cache-shared-datasets-ssrs.md) </span></span>  
 [<span data-ttu-id="97efe-136">スケジュール</span><span class="sxs-lookup"><span data-stu-id="97efe-136">Schedules</span></span>](subscriptions/schedules.md)  
  
  
