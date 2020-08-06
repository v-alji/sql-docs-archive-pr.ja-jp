---
title: キャッシュの事前読み込み (レポート マネージャー) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- cache [Reporting Services]
- preloading cache
ms.assetid: 152a1051-8aa5-4c01-bc85-f8be8971b0cd
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b60b74f7ab5c0c843b848c09ee574fd59a99c682
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716086"
---
# <a name="preload-the-cache-report-manager"></a><span data-ttu-id="b9b21-102">キャッシュの事前読み込み (レポート マネージャー)</span><span class="sxs-lookup"><span data-stu-id="b9b21-102">Preload the Cache (Report Manager)</span></span>
  <span data-ttu-id="b9b21-103">共有データセットのキャッシュ更新計画を作成することによって、共有データセットのキャッシュを事前に読み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="b9b21-103">You can preload the cache for a shared dataset by creating a cache refresh plan for the shared dataset.</span></span>  
  
 <span data-ttu-id="b9b21-104">レポートのキャッシュを事前に読み込むには 2 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="b9b21-104">You can preload the cache for a report in two ways:</span></span>  
  
1.  <span data-ttu-id="b9b21-105">レポートのキャッシュ更新計画を作成します。</span><span class="sxs-lookup"><span data-stu-id="b9b21-105">Create a cache refresh plan for the report.</span></span> <span data-ttu-id="b9b21-106">可能であればこの方法の使用をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="b9b21-106">This is the preferred method.</span></span>  
  
2.  <span data-ttu-id="b9b21-107">データ ドリブン サブスクリプションを使用して、パラメーター化されたレポートのインスタンスをキャッシュに事前に読み込みます。</span><span class="sxs-lookup"><span data-stu-id="b9b21-107">Use a data-driven subscription to preload the cache with instances of parameterized reports.</span></span> <span data-ttu-id="b9b21-108">これは、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] より前のバージョンの [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]でキャッシュを事前に読み込む唯一の方法でした。</span><span class="sxs-lookup"><span data-stu-id="b9b21-108">This was the only way to preload the cache in versions of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] earlier than [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)].</span></span> <span data-ttu-id="b9b21-109">詳細については、「 [レポートのキャッシュ (SSRS)](caching-reports-ssrs.md)でキャッシュを事前に読み込む唯一の方法でした。</span><span class="sxs-lookup"><span data-stu-id="b9b21-109">For more information, see [Caching Reports &#40;SSRS&#41;](caching-reports-ssrs.md).</span></span>  
  
 <span data-ttu-id="b9b21-110">レポートまたは共有データセットをキャッシュするには、次の条件を満たしている必要があります。</span><span class="sxs-lookup"><span data-stu-id="b9b21-110">The following conditions must be met before you can cache a report or a shared dataset:</span></span>  
  
-   <span data-ttu-id="b9b21-111">共有データセットまたはレポートでキャッシュが有効になっている。</span><span class="sxs-lookup"><span data-stu-id="b9b21-111">The shared dataset or the report must have caching enabled.</span></span>  
  
-   <span data-ttu-id="b9b21-112">共有データセットまたはレポートの共有データ ソースで、保存済みの資格情報を使用するか、または資格情報を使用しないように構成されている。</span><span class="sxs-lookup"><span data-stu-id="b9b21-112">The shared data sources for the shared dataset or the report must be configured to use stored credentials or no credentials.</span></span>  
  
-   <span data-ttu-id="b9b21-113">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービスが実行されている。</span><span class="sxs-lookup"><span data-stu-id="b9b21-113">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service must be running.</span></span>  
  
### <a name="to-preload-the-cache-by-creating-a-cache-refresh-plan"></a><span data-ttu-id="b9b21-114">キャッシュ更新計画を作成してキャッシュを事前に読み込むには</span><span class="sxs-lookup"><span data-stu-id="b9b21-114">To preload the cache by creating a cache refresh plan</span></span>  
  
1.  <span data-ttu-id="b9b21-115">[レポート マネージャー &#40;SSRS ネイティブ モード&#41;](../report-manager-ssrs-native-mode.md) を開始します。</span><span class="sxs-lookup"><span data-stu-id="b9b21-115">Start [Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md).</span></span>  
  
2.  <span data-ttu-id="b9b21-116">レポート マネージャーで、 **[コンテンツ]** ページに移動して、キャッシュするアイテムに移動します。</span><span class="sxs-lookup"><span data-stu-id="b9b21-116">In Report Manager, navigate to the **Contents** page, and then navigate to the item that you want to cache.</span></span>  
  
3.  <span data-ttu-id="b9b21-117">アイテムの上にマウス ポインターを移動し、ドロップダウン リストをクリックして、 **[管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b9b21-117">Hover over the item, click the drop-down list, and then click **Manage**.</span></span>  
  
4.  <span data-ttu-id="b9b21-118">**[キャッシュ更新オプション]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="b9b21-118">Click the **Cache Refresh Options** tab.</span></span>  
  
5.  <span data-ttu-id="b9b21-119">ツール バーの **[新しいキャッシュ更新計画]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b9b21-119">On the toolbar, click **New Cache Refresh Plan**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b9b21-120">アイテムでキャッシュが有効化されていない場合は、キャッシュを有効化するように求めるメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b9b21-120">If the item does not have caching enabled, you will be prompted to enable caching.</span></span> <span data-ttu-id="b9b21-121">キャッシュを有効化するには、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b9b21-121">To enable caching, click **OK**.</span></span>  
  
     <span data-ttu-id="b9b21-122">[キャッシュ更新計画] ページが開きます。</span><span class="sxs-lookup"><span data-stu-id="b9b21-122">The Cache Refresh Plan page opens.</span></span>  
  
6.  <span data-ttu-id="b9b21-123">必要に応じて、更新計画の説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="b9b21-123">Optionally type a description for the refresh plan.</span></span>  
  
7.  <span data-ttu-id="b9b21-124">共有スケジュールを使用する場合は、 **[共有スケジュール]** をクリックして、使用するスケジュールの名前を選択します。</span><span class="sxs-lookup"><span data-stu-id="b9b21-124">For a shared schedule, click **Shared schedule**, and then select the name of the schedule to use.</span></span>  
  
     <span data-ttu-id="b9b21-125">カスタム スケジュールを使用する場合は、 **[アイテム固有のスケジュール]**、 **[構成]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="b9b21-125">For a custom schedule, click **Item-specific schedule**, and then click **Configure**.</span></span>  
  
8.  <span data-ttu-id="b9b21-126">スケジュールを構成する</span><span class="sxs-lookup"><span data-stu-id="b9b21-126">Configure the schedule</span></span>  
  
9. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-preload-the-cache-with-a-user-specific-report-by-using-a-data-driven-subscription"></a><span data-ttu-id="b9b21-127">ユーザー固有のレポートでデータ ドリブン サブスクリプションを使用してキャッシュを事前に読み込むには</span><span class="sxs-lookup"><span data-stu-id="b9b21-127">To preload the cache with a user-specific report by using a data-driven subscription</span></span>  
  
1.  <span data-ttu-id="b9b21-128">[レポート マネージャー &#40;SSRS ネイティブ モード&#41;](../report-manager-ssrs-native-mode.md) を開始します。</span><span class="sxs-lookup"><span data-stu-id="b9b21-128">Start [Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md).</span></span>  
  
2.  <span data-ttu-id="b9b21-129">レポート マネージャーで **[コンテンツ]** ページに移動し、サブスクリプションを作成するレポートに移動します。</span><span class="sxs-lookup"><span data-stu-id="b9b21-129">In Report Manager, navigate to the **Contents** page, and then navigate to the report you want to create a subscription for.</span></span>  
  
3.  <span data-ttu-id="b9b21-130">レポートをクリックし、 **[サブスクリプション]** タブをクリックして、 **[新しいデータ ドリブン サブスクリプション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b9b21-130">Click the report, click the **Subscriptions** tab, and then click **New Data-Driven Subscription**.</span></span>  
  
4.  <span data-ttu-id="b9b21-131">必要に応じて、サブスクリプションの説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="b9b21-131">Optionally type a description for the subscription.</span></span>  
  
5.  <span data-ttu-id="b9b21-132">**[受信者への通知方法を指定します。]** の一覧から、 **[NULL 配信プロバイダー]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="b9b21-132">From the **Specify how recipients are notified** list, select **Null Delivery Provider**.</span></span>  
  
6.  <span data-ttu-id="b9b21-133">データ ソースの種類を指定し、 **[次へ]** をクリックしてデータ ソースを構成します。</span><span class="sxs-lookup"><span data-stu-id="b9b21-133">Specify a data source type and then click **Next** to configure the data source.</span></span>  
  
7.  <span data-ttu-id="b9b21-134">サブスクライバー データが格納されているデータ ソースへのアクセスに使用する接続の種類、接続文字列、および資格情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="b9b21-134">Specify the connection type, connection string, and credentials for accessing the data source that contains subscriber data.</span></span> <span data-ttu-id="b9b21-135">次に、Subscribers という [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースへの接続に使用する接続文字列の例を示します。</span><span class="sxs-lookup"><span data-stu-id="b9b21-135">The following example illustrates a connection string used to connect to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database called Subscribers:</span></span>  
  
    ```  
    data source=<servername>; initial catalog=Subscribers  
    ```  
  
8.  <span data-ttu-id="b9b21-136">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b9b21-136">Click **Next**.</span></span>  
  
9. <span data-ttu-id="b9b21-137">サブスクライバー データを取得するクエリまたはコマンドを指定します。</span><span class="sxs-lookup"><span data-stu-id="b9b21-137">Specify the query or command that retrieves subscriber data.</span></span> <span data-ttu-id="b9b21-138">必要に応じて、処理に時間のかかるクエリのタイムアウト値を増やします。</span><span class="sxs-lookup"><span data-stu-id="b9b21-138">Optionally increase the time-out period for queries that take a long time to process.</span></span> <span data-ttu-id="b9b21-139">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="b9b21-139">For example:</span></span>  
  
    ```  
    Select * from UserInfo  
    ```  
  
10. <span data-ttu-id="b9b21-140">**[検証]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b9b21-140">Click **Validate**.</span></span> <span data-ttu-id="b9b21-141">クエリを検証してから続行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b9b21-141">The query must be validated before you continue.</span></span> <span data-ttu-id="b9b21-142">**"クエリは正常に検証されました。"** というメッセージが表示されたら、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b9b21-142">When the **Query validated successfully** message appears, click **Next**.</span></span>  
  
11. <span data-ttu-id="b9b21-143">NULL 配信プロバイダーの配信拡張機能設定を構成することはできないので、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b9b21-143">Because you cannot configure delivery extension settings for the null delivery provider, click **Next**.</span></span>  
  
12. <span data-ttu-id="b9b21-144">サブスクリプションに対するレポートのパラメーター値を指定し、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b9b21-144">Specify report parameter values for the subscription, and click **Next**.</span></span>  
  
13. <span data-ttu-id="b9b21-145">サブスクリプションをいつ処理するかを指定します。</span><span class="sxs-lookup"><span data-stu-id="b9b21-145">Specify when the subscription is processed.</span></span> <span data-ttu-id="b9b21-146">**[レポート サーバーでのレポート データの更新時]** は選択しないでください。</span><span class="sxs-lookup"><span data-stu-id="b9b21-146">Do not choose **When the report data is updated on the report server**.</span></span> <span data-ttu-id="b9b21-147">この設定はスナップショットにのみ使用します。</span><span class="sxs-lookup"><span data-stu-id="b9b21-147">That setting is for snapshots only.</span></span> <span data-ttu-id="b9b21-148">既存のスケジュールを使用する場合は、 **[共有スケジュールで実行する]** を選択してください。</span><span class="sxs-lookup"><span data-stu-id="b9b21-148">If want to use a pre-existing schedule, select **On a shared schedule**.</span></span>  
  
     <span data-ttu-id="b9b21-149">カスタム スケジュールを作成する場合は、 **[このサブスクリプション用に作成されたスケジュールで実行します]** をクリックし、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b9b21-149">Or, to create a custom schedule, click **On a schedule created for this subscription** and then click **Next**.</span></span> <span data-ttu-id="b9b21-150">スケジュールを構成し、 **[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b9b21-150">Configure the schedule and then click **Finish**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b9b21-151">サブスクライバーが最新のレポートを受け取るには、構成するスケジュールが、サブスクライバーに対して定義したレポート配信スケジュールと一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b9b21-151">In order for the subscribers to receive the newest report, the schedule that you configure should be consistent with the report delivery schedule that you have defined for the subscribers.</span></span> <span data-ttu-id="b9b21-152">詳細については、「[レポート マネージャー &#40;SSRS ネイティブ モード&#41;](../report-manager-ssrs-native-mode.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b9b21-152">For more information, see [Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md).</span></span>  
  
14. <span data-ttu-id="b9b21-153">以下のように、レポートの実行オプションを構成します。</span><span class="sxs-lookup"><span data-stu-id="b9b21-153">Configure the Execution options for the report as follows.</span></span> <span data-ttu-id="b9b21-154">レポート ページで、 **[プロパティ]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="b9b21-154">On the report page, click the **Properties** tab.</span></span>  
  
15. <span data-ttu-id="b9b21-155">左フレームの **[実行]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="b9b21-155">In the left frame, click the **Execution** tab.</span></span>  
  
16. <span data-ttu-id="b9b21-156">このページで、 **[最新データを使用して、このレポートを表示する]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="b9b21-156">On the page, select **Render this report with the most recent data**.</span></span>  
  
17. <span data-ttu-id="b9b21-157">次の 2 つのキャッシュ オプションのいずれかを選択し、以下のように有効期限を構成します。</span><span class="sxs-lookup"><span data-stu-id="b9b21-157">Choose one of the following two cache options and configure the expiration as follows:</span></span>  
  
    -   <span data-ttu-id="b9b21-158">キャッシュされたコピーが、特定の期間が過ぎた後で有効期限が切れるようにするには、 **[レポートの一時コピーをキャッシュします。レポートのコピーの有効期限は数分後に切れます。]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b9b21-158">To make the cached copy expire after a particular time period, click **Cache a temporary copy of the report. Expire copy of report after a number of minutes.**</span></span> <span data-ttu-id="b9b21-159">レポートの有効期限を分単位で入力します。</span><span class="sxs-lookup"><span data-stu-id="b9b21-159">Type the number of minutes for report expiration.</span></span>  
  
    -   <span data-ttu-id="b9b21-160">キャッシュされたコピーが、スケジュールに基づいて有効期限が切れるようにするには、 **[レポートの一時コピーをキャッシュします。次のスケジュールでレポートのコピーの有効期限は切れます。]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b9b21-160">To make the cached copy expire on a schedule, click **Cache a temporary copy of the report. Expire copy of report on the following schedule.**</span></span> <span data-ttu-id="b9b21-161">**[構成]** をクリックするか、共有スケジュールを選択して、レポートの有効期限をスケジュールします。</span><span class="sxs-lookup"><span data-stu-id="b9b21-161">Click **Configure**, or select a shared schedule to set a schedule for report expiration.</span></span>  
  
18. <span data-ttu-id="b9b21-162">**[Apply]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b9b21-162">Click **Apply**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9b21-163">参照</span><span class="sxs-lookup"><span data-stu-id="b9b21-163">See Also</span></span>  
 <span data-ttu-id="b9b21-164">[Data-Driven Subscriptions](../subscriptions/data-driven-subscriptions.md) </span><span class="sxs-lookup"><span data-stu-id="b9b21-164">[Data-Driven Subscriptions](../subscriptions/data-driven-subscriptions.md) </span></span>  
 <span data-ttu-id="b9b21-165">[データ ドリブン サブスクリプションの作成 &#40;SSRS チュートリアル&#41;](../create-a-data-driven-subscription-ssrs-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="b9b21-165">[Create a Data-Driven Subscription &#40;SSRS Tutorial&#41;](../create-a-data-driven-subscription-ssrs-tutorial.md) </span></span>  
 <span data-ttu-id="b9b21-166">[パフォーマンス、スナップショット、キャッシュ &#40;Reporting Services&#41;](performance-snapshots-caching-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="b9b21-166">[Performance, Snapshots, Caching &#40;Reporting Services&#41;](performance-snapshots-caching-reporting-services.md) </span></span>  
 <span data-ttu-id="b9b21-167">[レポート処理プロパティの設定](set-report-processing-properties.md) </span><span class="sxs-lookup"><span data-stu-id="b9b21-167">[Set Report Processing Properties](set-report-processing-properties.md) </span></span>  
 [<span data-ttu-id="b9b21-168">レポートのキャッシュ (SSRS)</span><span class="sxs-lookup"><span data-stu-id="b9b21-168">Caching Reports &#40;SSRS&#41;</span></span>](caching-reports-ssrs.md)  
  
  
