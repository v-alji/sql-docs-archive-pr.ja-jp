---
title: レポート履歴へのスナップショットの追加 (レポート マネージャー) | Microsoft Docs
ms.prod: sql-server-2014
ms.technology: reporting-services
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
helpviewer_keywords:
- report history [Reporting Services], adding snapshots
- historical data [Reporting Services]
- snapshots [Reporting Services], adding report snapshots
- adding snapshots to report history
- report snapshots [Reporting Services], adding
ms.custom: ''
ms.date: 06/13/2017
ms.openlocfilehash: 84d4c264ab0b82fca2a34e6356b53113d63e6994
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642589"
---
# <a name="add-a-snapshot-to-report-history-report-manager"></a><span data-ttu-id="1e2aa-102">レポート履歴へのスナップショットの追加 (レポート マネージャー)</span><span class="sxs-lookup"><span data-stu-id="1e2aa-102">Add a Snapshot to Report History (Report Manager)</span></span>

<span data-ttu-id="1e2aa-103">レポート履歴とは、時間の経過と共に作成されるレポート スナップショットの集まりです。</span><span class="sxs-lookup"><span data-stu-id="1e2aa-103">Report history is a collection of report snapshots that you create over time.</span></span> <span data-ttu-id="1e2aa-104">レポート スナップショットは、特定の時点で取得されたレイアウト情報およびクエリ結果を含むレポートです。</span><span class="sxs-lookup"><span data-stu-id="1e2aa-104">A report snapshot is a report that contains layout information and query results that were retrieved at a specific point in time.</span></span> <span data-ttu-id="1e2aa-105">レポートを選択したときに最新のクエリ結果を取得する要求時レポートとは異なり、レポート スナップショットはスケジュールに従って処理され、その後、レポート サーバーに保存されます。</span><span class="sxs-lookup"><span data-stu-id="1e2aa-105">Unlike on-demand reports, which get up-to-date query results when you select the report, report snapshots are processed on a schedule and then saved to a report server.</span></span> <span data-ttu-id="1e2aa-106">表示するレポート スナップショットを選択すると、レポート サーバーによってレポート サーバー データベースに格納されたレポートが取得され、スナップショット作成時点のレポートで最新だったデータとレイアウトを表示します。</span><span class="sxs-lookup"><span data-stu-id="1e2aa-106">When you select a report snapshot for viewing, the report server retrieves the stored report from the report server database and shows the data and layout that were current for the report at the time the snapshot was created.</span></span>  
  
<span data-ttu-id="1e2aa-107">レポート スナップショットは、特定の表示形式では保存されません。</span><span class="sxs-lookup"><span data-stu-id="1e2aa-107">Report snapshots are not saved in a particular rendering format.</span></span> <span data-ttu-id="1e2aa-108">その代わりに、レポート スナップショットは、ユーザーまたはアプリケーションが要求したときのみ、最終的な表示形式 (HTML など) で表示されます。</span><span class="sxs-lookup"><span data-stu-id="1e2aa-108">Instead, report snapshots are rendered in a final viewing format (such as HTML) only when a user or an application requests it.</span></span> <span data-ttu-id="1e2aa-109">遅延表示により、スナップショットの移植性が実現します。</span><span class="sxs-lookup"><span data-stu-id="1e2aa-109">Deferred rendering makes a snapshot portable.</span></span> <span data-ttu-id="1e2aa-110">レポートは、要求元のデバイスまたは Web ブラウザーの適切な形式で表示できます。</span><span class="sxs-lookup"><span data-stu-id="1e2aa-110">The report can be rendered in the correct format for the requesting device or Web browser.</span></span>  
  
## <a name="to-manually-add-snapshots-to-report-history"></a><span data-ttu-id="1e2aa-111">レポート履歴にスナップショットを手動で追加するには</span><span class="sxs-lookup"><span data-stu-id="1e2aa-111">To manually add snapshots to report history</span></span>

1. <span data-ttu-id="1e2aa-112">レポート マネージャーで、 **[コンテンツ]** ページに移動し、履歴を表示するアイテムの上にマウス ポインターを移動して、下矢印をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1e2aa-112">In Report Manager, navigate to the **Contents** page, and hover over the item that you want to view history for, and click the drop-down arrow.</span></span>
  
2. <span data-ttu-id="1e2aa-113">ドロップダウン メニューの **[レポート履歴の表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1e2aa-113">In the drop-down menu, click **View Report History**.</span></span>  
  
3. <span data-ttu-id="1e2aa-114">**[新しいスナップショット]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1e2aa-114">Click **New Snapshot**.</span></span> <span data-ttu-id="1e2aa-115">**[実行時]** 列に新しいスナップショットが作成されます。</span><span class="sxs-lookup"><span data-stu-id="1e2aa-115">A new snapshot is created in the **When Run** column.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="1e2aa-116">レポート履歴にスナップショットを追加するには、管理者がレポート履歴の構成で **[履歴の手動作成を許可する]** に設定しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="1e2aa-116">In order to do this, the report history must be configured by the administrator to **Allow history to be created manually**.</span></span> <span data-ttu-id="1e2aa-117">詳細については、 [レポート履歴を制限する (レポート マネージャー)](../reports/limit-report-history-report-manager.md)をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1e2aa-117">For more information, see [Limit Report History &#40;Report Manager&#41;](../reports/limit-report-history-report-manager.md).</span></span>

4. <span data-ttu-id="1e2aa-118">**[Apply]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1e2aa-118">Click **Apply**.</span></span>

## <a name="to-automatically-add-all-snapshots-to-report-history"></a><span data-ttu-id="1e2aa-119">レポート履歴にすべてのスナップショットを自動で追加するには</span><span class="sxs-lookup"><span data-stu-id="1e2aa-119">To automatically add all snapshots to report history</span></span>  
  
1. <span data-ttu-id="1e2aa-120">既にレポート実行スナップショットとして実行するように構成されたレポートでは、追加のプロパティを設定することで、スナップショットが更新されるたびにスナップショットのコピーをレポート履歴に保存できます。</span><span class="sxs-lookup"><span data-stu-id="1e2aa-120">For a report that is already configured to run as a report execution snapshot, you can set additional properties to save a copy of the snapshot to report history each time the snapshot is refreshed.</span></span>  
  
2. <span data-ttu-id="1e2aa-121">レポート マネージャーで、 **[コンテンツ]** ページに移動し、履歴を表示するアイテムの上にマウス ポインターを移動して、下矢印をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1e2aa-121">In Report Manager, navigate to the **Contents** page, hover over the item that you want to view history for, and click the drop-down arrow.</span></span>  
  
3. <span data-ttu-id="1e2aa-122">ドロップダウン メニューの **[管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1e2aa-122">In the drop-down menu, click **Manage**.</span></span>  
  
4. <span data-ttu-id="1e2aa-123">**[スナップショット オプション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1e2aa-123">Click **Snapshot Options**.</span></span>  
  
5. <span data-ttu-id="1e2aa-124">**[すべてのレポート実行スナップショットを履歴に格納する]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="1e2aa-124">Select the check box for **Store all report execution snapshots in history**.</span></span>  
  
6. <span data-ttu-id="1e2aa-125">**[Apply]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1e2aa-125">Click **Apply**.</span></span>  
  
### <a name="to-automatically-add-snapshots-to-report-history-based-on-a-schedule"></a><span data-ttu-id="1e2aa-126">スケジュールを基にスナップショットを自動でレポート履歴に追加するには</span><span class="sxs-lookup"><span data-stu-id="1e2aa-126">To automatically add snapshots to report history based on a schedule</span></span>  
  
1. <span data-ttu-id="1e2aa-127">レポート マネージャーで、 **[コンテンツ]** ページに移動し、履歴を表示するアイテムの上にマウス ポインターを移動して、下矢印をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1e2aa-127">In Report Manager, navigate to the **Contents** page, and hover over the item that you want to view history for, and click the drop-down arrow.</span></span>  
  
2. <span data-ttu-id="1e2aa-128">ドロップダウン メニューの **[管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1e2aa-128">In the drop-down menu, click **Manage**.</span></span>  
  
3. <span data-ttu-id="1e2aa-129">**[スナップショット オプション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1e2aa-129">Click **Snapshot Options**.</span></span>  
  
4. <span data-ttu-id="1e2aa-130">**[次のスケジュールを使用して、スナップショットをレポート履歴に追加する]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="1e2aa-130">Select the check box for **Use the following schedule to add snapshots to report history**.</span></span> <span data-ttu-id="1e2aa-131">以下のいずれかを行います。</span><span class="sxs-lookup"><span data-stu-id="1e2aa-131">Perform one of the following:</span></span>  
  
    - <span data-ttu-id="1e2aa-132">**[レポート固有のスケジュール]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1e2aa-132">Select **Report-specific schedule**.</span></span> <span data-ttu-id="1e2aa-133">スケジュールの詳細を入力し、スケジュールの開始日と終了日を選択して、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1e2aa-133">Fill in the schedule details, select the start and end dates for the schedule, and then click **OK**.</span></span>  
  
    - <span data-ttu-id="1e2aa-134">**[共有スケジュール]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="1e2aa-134">Select **Shared schedule**.</span></span> <span data-ttu-id="1e2aa-135">一覧から適切なスケジュールを選択します。</span><span class="sxs-lookup"><span data-stu-id="1e2aa-135">From the list, select the preferred schedule.</span></span>  
  
5. <span data-ttu-id="1e2aa-136">**[Apply]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1e2aa-136">Click **Apply**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e2aa-137">参照</span><span class="sxs-lookup"><span data-stu-id="1e2aa-137">See Also</span></span>

- [<span data-ttu-id="1e2aa-138">レポートの実行プロパティを構成する &#40;レポート マネージャー&#41;</span><span class="sxs-lookup"><span data-stu-id="1e2aa-138">Configure Execution Properties for a Report  &#40;Report Manager&#41;</span></span>](../reports/configure-execution-properties-for-a-report-report-manager.md)
- [<span data-ttu-id="1e2aa-139">レポートを開閉する &#40;レポート マネージャー&#41;</span><span class="sxs-lookup"><span data-stu-id="1e2aa-139">Open and Close a Report &#40;Report Manager&#41;</span></span>](../reports/open-and-close-a-report-report-manager.md)
- [<span data-ttu-id="1e2aa-140">レポート履歴を制限する &#40;レポート マネージャー&#41;</span><span class="sxs-lookup"><span data-stu-id="1e2aa-140">Limit Report History &#40;Report Manager&#41;</span></span>](../reports/limit-report-history-report-manager.md)
- [<span data-ttu-id="1e2aa-141">スケジュール</span><span class="sxs-lookup"><span data-stu-id="1e2aa-141">Schedules</span></span>](../subscriptions/schedules.md)   
- [<span data-ttu-id="1e2aa-142">レポート マネージャー &#40;SSRS ネイティブ モード&#41;</span><span class="sxs-lookup"><span data-stu-id="1e2aa-142">Report Manager  &#40;SSRS Native Mode&#41;</span></span>](../report-manager-ssrs-native-mode.md)