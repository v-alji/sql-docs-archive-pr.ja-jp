---
title: '[新しいスケジュール]: [スケジュールの編集] ページ (レポートマネージャー) |Microsoft Docs'
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 52a4d250-e185-4116-a29c-d809940a00fb
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 701c1729eac1c2cf683c966dca58f47b88a2dd32
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738022"
---
# <a name="new-schedule-edit-schedule-page-report-manager"></a><span data-ttu-id="d092a-102">[新しいスケジュール]: [スケジュールの編集] ページ (レポートマネージャー)</span><span class="sxs-lookup"><span data-stu-id="d092a-102">New Schedule: Edit Schedule Page (Report Manager)</span></span>
  <span data-ttu-id="d092a-103">[新しいスケジュール] ページまたは [スケジュールの編集] ページを使用すると、レポートのスケジュールを作成できます。</span><span class="sxs-lookup"><span data-stu-id="d092a-103">Use the New Schedule / Edit Schedule page to create a schedule for a report.</span></span> <span data-ttu-id="d092a-104">スケジュールはサブスクリプションで使用されます。その用途は、キャッシュされたレポートを更新、スナップショットをスタンドアロン アイテムとして作成、スナップショットをレポート履歴で作成することです。</span><span class="sxs-lookup"><span data-stu-id="d092a-104">Schedules are used with subscriptions, to refresh cached reports, and to create snapshots as standalone items or in report history.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d092a-105">この機能は、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]のすべてのエディションで使用できるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="d092a-105">This feature is not available in every edition of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="d092a-106">の各エディションでサポートされる機能の一覧につい [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ては、「 [SQL Server 2014 の各エディションがサポートする機能](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d092a-106">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
 <span data-ttu-id="d092a-107">自動的に実行されるレポートに対してのみ、スケジュールを作成できます。</span><span class="sxs-lookup"><span data-stu-id="d092a-107">You can create schedules only for reports that can run unattended.</span></span> <span data-ttu-id="d092a-108">レポートを自動的に実行するには、レポート サーバー データベースにレポート データ ソース資格情報を保存しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="d092a-108">Running a report unattended requires that you store report data source credentials in the report server database.</span></span> <span data-ttu-id="d092a-109">詳細については、「[[データソース] プロパティページ &#40;レポートマネージャー&#41;](../../2014/reporting-services/data-sources-properties-page-report-manager.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d092a-109">For more information, see [Data Sources Properties Page &#40;Report Manager&#41;](../../2014/reporting-services/data-sources-properties-page-report-manager.md).</span></span>  
  
 <span data-ttu-id="d092a-110">1 つのスケジュールの中で、複数の頻度を組み合わせて使用することができない場合があります。</span><span class="sxs-lookup"><span data-stu-id="d092a-110">Not all frequency combinations can be supported in a single schedule.</span></span> <span data-ttu-id="d092a-111">たとえば、毎週金曜日の正午と</span><span class="sxs-lookup"><span data-stu-id="d092a-111">For example, if you want to run a report at 12:00 P.M.</span></span> <span data-ttu-id="d092a-112">午後 4 時 00 分まで</span><span class="sxs-lookup"><span data-stu-id="d092a-112">and 4:00 P.M.</span></span> <span data-ttu-id="d092a-113">レポートを実行する場合、実行日を金曜日に指定した日単位のスケジュールを 2 つ作成し、1 つは開始時刻を正午に、</span><span class="sxs-lookup"><span data-stu-id="d092a-113">every Friday, you must create two daily schedules that specify a Friday run date, one with a start time of 12:00 P.M.</span></span> <span data-ttu-id="d092a-114">もう 1 つは開始時刻を午後 4 時に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d092a-114">and another with a start time of 4:00 P.M.</span></span>  
  
 <span data-ttu-id="d092a-115">スケジュールは、そのスケジュールをホストおよび処理するレポート サーバーのローカル時間に基づいて処理されます。</span><span class="sxs-lookup"><span data-stu-id="d092a-115">Schedule processing is based on the local time of the report server that hosts and processes the schedule.</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="d092a-116">ナビゲーション</span><span class="sxs-lookup"><span data-stu-id="d092a-116">Navigation</span></span>  
 <span data-ttu-id="d092a-117">ユーザー インターフェイス (UI) のこの場所に移動するには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="d092a-117">Use the following procedures to navigate to this location in the user interface (UI).</span></span>  
  
### <a name="to-open-the-new-schedule-or-edit-schedule-page-from-the-execution-properties-page-of-a-report"></a><span data-ttu-id="d092a-118">レポートの [実行] プロパティ ページから [新しいスケジュール] ページまたは [スケジュールの編集] ページを開くには</span><span class="sxs-lookup"><span data-stu-id="d092a-118">To open the New Schedule or Edit Schedule page from the Execution properties page of a report</span></span>  
  
1.  <span data-ttu-id="d092a-119">レポート マネージャーを開き、スケジュールを構成するレポートを探します。</span><span class="sxs-lookup"><span data-stu-id="d092a-119">Open Report Manager, and locate the report for which you want configure a schedule.</span></span>  
  
2.  <span data-ttu-id="d092a-120">レポートの上にマウス ポインターを移動し、下矢印をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d092a-120">Hover over the report, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="d092a-121">ドロップダウン メニューの **[管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d092a-121">In the drop-down menu, click **Manage**.</span></span> <span data-ttu-id="d092a-122">この操作により、モデルの [全般] プロパティ ページが開きます。</span><span class="sxs-lookup"><span data-stu-id="d092a-122">This opens the General properties page for the model.</span></span>  
  
4.  <span data-ttu-id="d092a-123">**[実行]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="d092a-123">Select the **Execution** tab.</span></span>  
  
5.  <span data-ttu-id="d092a-124">**[このレポートをレポート実行スナップショットから表示する]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d092a-124">Select the **Render this report from a report execution snapshot option**.</span></span> <span data-ttu-id="d092a-125">次に、 **[次のスケジュールを使用して、スナップショットをレポート履歴に追加する]** チェック ボックスをオンにし、 **[レポート固有のスケジュール]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d092a-125">Then select **Use the following schedule to add snapshots to report history**, and select **Report-specific schedule**.</span></span> <span data-ttu-id="d092a-126">**[構成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d092a-126">Then click **Configure**.</span></span>  
  
### <a name="to-open-the-new-schedule-or-edit-schedule-page-from-the-history-properties-page-of-a-report"></a><span data-ttu-id="d092a-127">レポートの [履歴] プロパティ ページから [新しいスケジュール] ページまたは [スケジュールの編集] ページを開くには</span><span class="sxs-lookup"><span data-stu-id="d092a-127">To open the New Schedule or Edit Schedule page from the History properties page of a report</span></span>  
  
1.  <span data-ttu-id="d092a-128">レポート マネージャーを開き、スケジュールを構成するレポートを探します。</span><span class="sxs-lookup"><span data-stu-id="d092a-128">Open Report Manager, and locate the report for which you want configure a schedule.</span></span>  
  
2.  <span data-ttu-id="d092a-129">レポートの上にマウス ポインターを移動し、下矢印をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d092a-129">Hover over the report, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="d092a-130">ドロップダウン メニューの **[管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d092a-130">In the drop-down menu, click **Manage**.</span></span> <span data-ttu-id="d092a-131">この操作により、モデルの [全般] プロパティ ページが開きます。</span><span class="sxs-lookup"><span data-stu-id="d092a-131">This opens the General properties page for the model.</span></span>  
  
4.  <span data-ttu-id="d092a-132">**[履歴]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="d092a-132">Select the **History** tab.</span></span>  
  
5.  <span data-ttu-id="d092a-133">**[次のスケジュールを使用して、スナップショットをレポート履歴に追加する]** チェック ボックスをオンにし、 **[レポート固有のスケジュール]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d092a-133">Select **Use the following schedule to add snapshots to report history**, and select **Report-specific schedule**.</span></span> <span data-ttu-id="d092a-134">**[構成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d092a-134">Then click **Configure**.</span></span>  
  
### <a name="to-open-the-new-schedule-or-edit-schedule-page-from-the-subscriptions-page"></a><span data-ttu-id="d092a-135">[サブスクリプション] ページから [新しいスケジュール] ページまたは [スケジュールの編集] ページを開くには</span><span class="sxs-lookup"><span data-stu-id="d092a-135">To open the New Schedule or Edit Schedule page from the Subscriptions page</span></span>  
  
1.  <span data-ttu-id="d092a-136">レポート マネージャーを開き、スケジュールを構成するレポートを探します。</span><span class="sxs-lookup"><span data-stu-id="d092a-136">Open Report Manager, and locate the report for which you want configure a schedule.</span></span>  
  
2.  <span data-ttu-id="d092a-137">レポートの上にマウス ポインターを移動し、下矢印をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d092a-137">Hover over the report, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="d092a-138">ドロップダウン メニューで、次のどちらかの操作を行います。</span><span class="sxs-lookup"><span data-stu-id="d092a-138">In the drop-down menu,</span></span>  
  
    -   <span data-ttu-id="d092a-139">**Manage**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d092a-139">Click **Manage**.</span></span> <span data-ttu-id="d092a-140">この操作により、レポートの [全般] プロパティ ページが開きます。</span><span class="sxs-lookup"><span data-stu-id="d092a-140">This opens the General properties page for the report.</span></span> <span data-ttu-id="d092a-141">**[サブスクリプション]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="d092a-141">Then select the **Subscriptions** tab.</span></span>  
  
    -   <span data-ttu-id="d092a-142">**[サブスクライブ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d092a-142">Click **Subscribe**.</span></span> <span data-ttu-id="d092a-143">この操作により、レポートの **[サブスクリプション]** プロパティ ページが開きます。</span><span class="sxs-lookup"><span data-stu-id="d092a-143">This opens the **Subscriptions** properties page for the report.</span></span>  
  
4.  <span data-ttu-id="d092a-144">ツール バーで、 **[新しいサブスクリプション]** をクリックするか、編集する既存のサブスクリプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="d092a-144">In the toolbar, click **New Subscription** or select an existing subscription to edit.</span></span>  
  
5.  <span data-ttu-id="d092a-145">**[サブスクリプション処理のオプション]** で、 **[新しいスケジュール]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d092a-145">Under **Subscription Processing Options**, click **New Schedule**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="d092a-146">Options</span><span class="sxs-lookup"><span data-stu-id="d092a-146">Options</span></span>  
 <span data-ttu-id="d092a-147">**[スケジュールの詳細]**</span><span class="sxs-lookup"><span data-stu-id="d092a-147">**Schedule details**</span></span>  
 <span data-ttu-id="d092a-148">レポートを実行する日時と頻度を決定するオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="d092a-148">Select options that determine when and how often a report runs.</span></span> <span data-ttu-id="d092a-149">頻度を表すオプションは、階層化されています。</span><span class="sxs-lookup"><span data-stu-id="d092a-149">Frequency options are layered.</span></span> <span data-ttu-id="d092a-150">最初のオプション群で、頻度のカテゴリ (時間単位、日単位、週単位など) を指定します。</span><span class="sxs-lookup"><span data-stu-id="d092a-150">The first set of options specifies a category of frequency (hourly, daily, weekly, and so on).</span></span> <span data-ttu-id="d092a-151">2 番目のオプション群は、最初の選択に基づいて表示されます。</span><span class="sxs-lookup"><span data-stu-id="d092a-151">The second set of options that appears is based on your initial selection.</span></span>  
  
-   <span data-ttu-id="d092a-152">**[時間]** では、1 時間ごとに実行されるスケジュールを定義します。</span><span class="sxs-lookup"><span data-stu-id="d092a-152">**Hour** defines a schedule that runs at hourly intervals.</span></span> <span data-ttu-id="d092a-153">**[開始日および終了日]** セクションを使用して、スケジュールを実行する日を指定します。</span><span class="sxs-lookup"><span data-stu-id="d092a-153">Use the **Start and end dates** section to specify the day on which to run the schedule.</span></span>  
  
-   <span data-ttu-id="d092a-154">**[日]** では、選択した日の指定した時刻に実行されるスケジュールを定義します。</span><span class="sxs-lookup"><span data-stu-id="d092a-154">**Day** defines a schedule that runs on the days you select at a specific hour and minute.</span></span> <span data-ttu-id="d092a-155">曜日は、毎日、すべての \<*day*> 曜日、および \<*number*> 毎日のように指定できます。</span><span class="sxs-lookup"><span data-stu-id="d092a-155">You can specify days in the following ways: Every \<*day*>, Every weekday, and Every \<*number*> day.</span></span> <span data-ttu-id="d092a-156">いずれかのオプションを選択すると、それ以外のオプションは表示されていても無効になります。</span><span class="sxs-lookup"><span data-stu-id="d092a-156">Choosing one approach voids the others, even if the other days appear to be selected.</span></span>  
  
-   <span data-ttu-id="d092a-157">**[週]** では、1 週間ごとの指定した時刻に実行されるスケジュールを定義します。</span><span class="sxs-lookup"><span data-stu-id="d092a-157">**Week** defines a schedule that runs at weekly intervals at a specific hour and minute.</span></span> <span data-ttu-id="d092a-158">実行間隔は、2 週間ごとのようにちょうど 1 週間を単位としているものでも、週の複数の曜日を指定するものでもかまいません。</span><span class="sxs-lookup"><span data-stu-id="d092a-158">The interval can be a complete week (for example, every two weeks), or days within a week.</span></span>  
  
-   <span data-ttu-id="d092a-159">**[月]** では、1 か月ごとに実行されるスケジュールを定義します。</span><span class="sxs-lookup"><span data-stu-id="d092a-159">**Month** defines a schedule that runs on a monthly basis.</span></span> <span data-ttu-id="d092a-160">1 か月の中で、あるパターンを基にした日 (毎月最終日曜日など) か、特定の日付 (たとえば、1 と 15 を指定して毎月 1 日と 15 日) を選択できます。</span><span class="sxs-lookup"><span data-stu-id="d092a-160">Within a month, you can choose a day based on a pattern (for example, the last Sunday of every month) or specific calendar dates (such as 1 and 15 to indicate the first and fifteenth day of every month).</span></span> <span data-ttu-id="d092a-161">コンマおよびハイフンを使用して、複数の日や期間を指定できます (たとえば、1, 5, 7-12, 21)。</span><span class="sxs-lookup"><span data-stu-id="d092a-161">Using commas and hyphens, you can specify multiple days and ranges, for example, 1, 5, 7-12, 21.</span></span>  
  
-   <span data-ttu-id="d092a-162">**[一度だけ]** は、一度だけ実行されるスケジュールを定義します。</span><span class="sxs-lookup"><span data-stu-id="d092a-162">**Once** defines a schedule that runs only once.</span></span> <span data-ttu-id="d092a-163">**[開始日および終了日]** セクションを使用して、スケジュールを実行する日を指定します。</span><span class="sxs-lookup"><span data-stu-id="d092a-163">Use the **Start and end dates** section to specify the day on which to run the schedule.</span></span> <span data-ttu-id="d092a-164">このスケジュールは、処理が終了すると失効します。</span><span class="sxs-lookup"><span data-stu-id="d092a-164">This schedule expires as soon as it is processed.</span></span>  
  
 <span data-ttu-id="d092a-165">**[開始日および終了日]**</span><span class="sxs-lookup"><span data-stu-id="d092a-165">**Start and end dates**</span></span>  
 <span data-ttu-id="d092a-166">スケジュール タスクが発効する日を確定する開始日、およびスケジュールが失効する日を確定する終了日を指定します。</span><span class="sxs-lookup"><span data-stu-id="d092a-166">Specify a start date that determines when the schedule takes effect and an end date that determines when the schedule expires.</span></span>  
  
 <span data-ttu-id="d092a-167">スケジュールは予告なく失効します。</span><span class="sxs-lookup"><span data-stu-id="d092a-167">Schedules expire without notification.</span></span> <span data-ttu-id="d092a-168">終了日を過ぎると、スケジュールは実行されません。</span><span class="sxs-lookup"><span data-stu-id="d092a-168">After the end date, they no longer run.</span></span> <span data-ttu-id="d092a-169">期限切れのスケジュールは削除されません。</span><span class="sxs-lookup"><span data-stu-id="d092a-169">Expired schedules are not deleted.</span></span> <span data-ttu-id="d092a-170">スケジュールの削除は、手動によってのみ可能です。</span><span class="sxs-lookup"><span data-stu-id="d092a-170">Schedules can only be deleted manually.</span></span> <span data-ttu-id="d092a-171">したがって、スケジュールを続行することにした場合、終了日を延長できます。</span><span class="sxs-lookup"><span data-stu-id="d092a-171">That way, if you choose to continue the schedule, you can extend the end date.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d092a-172">参照</span><span class="sxs-lookup"><span data-stu-id="d092a-172">See Also</span></span>  
 <span data-ttu-id="d092a-173">[レポート マネージャー &#40;SSRS ネイティブ モード&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="d092a-173">[Report Manager  &#40;SSRS Native Mode&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="d092a-174">[Create, Modify, and Delete Schedules](subscriptions/create-modify-and-delete-schedules.md) </span><span class="sxs-lookup"><span data-stu-id="d092a-174">[Create, Modify, and Delete Schedules](subscriptions/create-modify-and-delete-schedules.md) </span></span>  
 [<span data-ttu-id="d092a-175">レポート マネージャー F1 ヘルプ</span><span class="sxs-lookup"><span data-stu-id="d092a-175">Report Manager F1 Help</span></span>](../../2014/reporting-services/report-manager-f1-help.md)  
  
  
