---
title: '[スナップショットオプション] プロパティページ (レポートマネージャー) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: f6641f59-5267-4f57-8957-63b93d1a9679
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3025b23dfe498a92c2ce1d8535229d8d23dfd429
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712693"
---
# <a name="snapshot-options-properties-page-report-manager"></a><span data-ttu-id="0fc8d-102">[スナップショット オプション] プロパティ ページ (レポート マネージャー)</span><span class="sxs-lookup"><span data-stu-id="0fc8d-102">Snapshot Options Properties Page (Report Manager)</span></span>
  <span data-ttu-id="0fc8d-103">[スナップショット オプション] プロパティ ページを使用すると、レポート スナップショットをレポート履歴に追加するスケジュールを設定したり、レポート履歴に保存するレポート スナップショットの件数の上限を設定したりできます。</span><span class="sxs-lookup"><span data-stu-id="0fc8d-103">Use the Snapshot Options properties page to schedule report snapshots to be added to report history, and to set limits on the number of report snapshots that are stored in report history.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0fc8d-104">この機能は、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]のすべてのエディションで使用できるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="0fc8d-104">This feature is not available in every edition of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="0fc8d-105">の各エディションでサポートされる機能の一覧につい [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ては、「[その他のデータベースサービス](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md#Add_DBServices)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0fc8d-105">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], see [Additional Database Services](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md#Add_DBServices).</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="0fc8d-106">ナビゲーション</span><span class="sxs-lookup"><span data-stu-id="0fc8d-106">Navigation</span></span>  
 <span data-ttu-id="0fc8d-107">ユーザー インターフェイス (UI) のこの場所に移動するには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="0fc8d-107">Use the following procedure to navigate to this location in the user interface (UI).</span></span>  
  
### <a name="to-open-the-snapshot-options-properties-page-for-a-report"></a><span data-ttu-id="0fc8d-108">レポートの [スナップショット オプション] プロパティ ページを開くには</span><span class="sxs-lookup"><span data-stu-id="0fc8d-108">To open the Snapshot Options properties page for a report</span></span>  
  
1.  <span data-ttu-id="0fc8d-109">レポート マネージャーを開き、レポート スナップショットのプロパティを構成するレポートを探します。</span><span class="sxs-lookup"><span data-stu-id="0fc8d-109">Open Report Manager, and locate the report for which you want to configure report snapshot properties.</span></span>  
  
2.  <span data-ttu-id="0fc8d-110">レポートの上にマウス ポインターを移動し、下矢印をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0fc8d-110">Hover over the report, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="0fc8d-111">ドロップダウン メニューの **[管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0fc8d-111">In the drop-down menu, click **Manage**.</span></span> <span data-ttu-id="0fc8d-112">この操作により、レポートの [全般] プロパティ ページが開きます。</span><span class="sxs-lookup"><span data-stu-id="0fc8d-112">This opens the General properties page for the report.</span></span>  
  
4.  <span data-ttu-id="0fc8d-113">**[スナップショット オプション]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="0fc8d-113">Select the **Snapshot Options** tab.</span></span>  
  
## <a name="options"></a><span data-ttu-id="0fc8d-114">Options</span><span class="sxs-lookup"><span data-stu-id="0fc8d-114">Options</span></span>  
 <span data-ttu-id="0fc8d-115">**[レポート履歴の手動作成を許可する]**</span><span class="sxs-lookup"><span data-stu-id="0fc8d-115">**Allow report history to be created manually**</span></span>  
 <span data-ttu-id="0fc8d-116">このチェック ボックスをオンにすると、必要に応じてレポートの履歴にスナップショットを追加できます。</span><span class="sxs-lookup"><span data-stu-id="0fc8d-116">Select this check box to add snapshots to report history as needed.</span></span> <span data-ttu-id="0fc8d-117">このチェック ボックスをオンにすると、[履歴] ページに **[新しいスナップショット]** ボタンが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0fc8d-117">Selecting this check box causes the **New Snapshot** button to appear on the History page.</span></span>  
  
 <span data-ttu-id="0fc8d-118">**[すべてのレポート実行スナップショットをヒストリに格納します]**</span><span class="sxs-lookup"><span data-stu-id="0fc8d-118">**Store all report execution snapshots in report history**</span></span>  
 <span data-ttu-id="0fc8d-119">このチェック ボックスをオンにすると、レポート実行プロパティを基に生成したレポート スナップショットがレポート ヒストリにコピーされます。</span><span class="sxs-lookup"><span data-stu-id="0fc8d-119">Select this check box to copy a report snapshot that you generate based on report execution properties to report history.</span></span> <span data-ttu-id="0fc8d-120">生成したスナップショットからレポートを実行するようにレポート実行プロパティを設定できます。</span><span class="sxs-lookup"><span data-stu-id="0fc8d-120">You can set report execution properties to run a report from a generated snapshot.</span></span> <span data-ttu-id="0fc8d-121">このレポート ヒストリのプロパティを設定すると、一定期間に生成されたすべてのレポート スナップショットのコピーをレポート ヒストリに配置することで、その記録を保存できます。</span><span class="sxs-lookup"><span data-stu-id="0fc8d-121">By setting this report history property, you can keep a record of all reports snapshots that are generated over time by placing copies of them in report history.</span></span>  
  
 <span data-ttu-id="0fc8d-122">**[次のスケジュールを使用して、スナップショットをレポート ヒストリに追加します]**</span><span class="sxs-lookup"><span data-stu-id="0fc8d-122">**Use the following schedule to add snapshots to report history**</span></span>  
 <span data-ttu-id="0fc8d-123">このチェック ボックスをオンにすると、スケジュールを基にしてスナップショットがレポート履歴に追加されます。</span><span class="sxs-lookup"><span data-stu-id="0fc8d-123">Select this check box to add snapshots to report history on a scheduled basis.</span></span> <span data-ttu-id="0fc8d-124">この目的にのみ使用されるスケジュールを作成することも、また、定義済みの共有スケジュールのうち、必要な情報が含まれているものがあればそれを選択することもできます。</span><span class="sxs-lookup"><span data-stu-id="0fc8d-124">You can create a schedule that is used exclusively for this purpose, or you can select a predefined shared schedule if one contains the schedule information you want.</span></span>  
  
 <span data-ttu-id="0fc8d-125">**[保持するスナップショットの数を選択してください]**</span><span class="sxs-lookup"><span data-stu-id="0fc8d-125">**Select the number of snapshots to keep**</span></span>  
 <span data-ttu-id="0fc8d-126">以下のオプションから、レポート ヒストリに保存しておくレポートの数を制御するオプションを選択してください。</span><span class="sxs-lookup"><span data-stu-id="0fc8d-126">Select from the following options to control the number of reports that are kept in report history.</span></span> <span data-ttu-id="0fc8d-127">レポート ヒストリの設定は、レポートごとに異なります。</span><span class="sxs-lookup"><span data-stu-id="0fc8d-127">Report history settings can vary for each report.</span></span>  
  
-   <span data-ttu-id="0fc8d-128">既定の設定から変更しない場合、 **[既定の設定を使用する]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0fc8d-128">Select **Use default setting** to retain the default setting.</span></span> <span data-ttu-id="0fc8d-129">レポート ヒストリ記憶域のマスター設定は、レポート サーバー管理者が制御しています。</span><span class="sxs-lookup"><span data-stu-id="0fc8d-129">The report server administrator controls a master setting for report history storage.</span></span> <span data-ttu-id="0fc8d-130">このオプションを選択した場合、そのマスター設定から保存するスナップショットの数が取得されます。</span><span class="sxs-lookup"><span data-stu-id="0fc8d-130">If you choose this option, the number of snapshots that are retained is obtained from this master setting.</span></span>  
  
-   <span data-ttu-id="0fc8d-131">すべてのレポート履歴スナップショットを保存するには、 **[レポート履歴に無制限の数のスナップショットを保持する]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="0fc8d-131">Select **Keep an unlimited number of snapshots in report history** to retain all report history snapshots.</span></span> <span data-ttu-id="0fc8d-132">このレポート ヒストリのサイズを減らすには、スナップショットを手動で削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0fc8d-132">You must manually delete snapshots to reduce the size of report history.</span></span>  
  
-   <span data-ttu-id="0fc8d-133">一定数のスナップショットを保持するには、 **[レポート履歴のコピーの数を制限する]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="0fc8d-133">Select **Limit the copies of report history** to retain a set number of snapshots.</span></span> <span data-ttu-id="0fc8d-134">制限値に達すると、古いコピーはレポート ヒストリから順次削除され、空いた領域に新しいコピーが保存されます。</span><span class="sxs-lookup"><span data-stu-id="0fc8d-134">When the limit is reached, older copies are removed from report history to make room for newer copies.</span></span>  
  
 <span data-ttu-id="0fc8d-135">レポート履歴は、レポート サーバー データベースに格納されます。</span><span class="sxs-lookup"><span data-stu-id="0fc8d-135">Report history is stored in the report server database.</span></span> <span data-ttu-id="0fc8d-136">履歴を保持するレポートのサイズが大きい場合や数が多い場合は、レポート サーバー データベースのディスク領域の要件を管理するためにレポート履歴の量を制限することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="0fc8d-136">If you have large reports or numerous reports for which you want to maintain history, consider limiting the amount of report history to help manage the disk space requirements of the report server database.</span></span>  
  
 <span data-ttu-id="0fc8d-137">**[適用]**</span><span class="sxs-lookup"><span data-stu-id="0fc8d-137">**Apply**</span></span>  
 <span data-ttu-id="0fc8d-138">変更を保存する場合にクリックします。</span><span class="sxs-lookup"><span data-stu-id="0fc8d-138">Click to save your changes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fc8d-139">参照</span><span class="sxs-lookup"><span data-stu-id="0fc8d-139">See Also</span></span>  
 <span data-ttu-id="0fc8d-140">[レポート履歴へのスナップショットの追加 &#40;レポートマネージャー&#41;](report-server/add-a-snapshot-to-report-history-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="0fc8d-140">[Add a Snapshot to Report History &#40;Report Manager&#41;](report-server/add-a-snapshot-to-report-history-report-manager.md) </span></span>  
 <span data-ttu-id="0fc8d-141">[レポート マネージャー &#40;SSRS ネイティブ モード&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="0fc8d-141">[Report Manager  &#40;SSRS Native Mode&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="0fc8d-142">[レポート履歴のスナップショットの作成、変更および削除](report-server/create-modify-and-delete-snapshots-in-report-history.md) </span><span class="sxs-lookup"><span data-stu-id="0fc8d-142">[Create, Modify, and Delete Snapshots in Report History](report-server/create-modify-and-delete-snapshots-in-report-history.md) </span></span>  
 [<span data-ttu-id="0fc8d-143">レポート マネージャー F1 ヘルプ</span><span class="sxs-lookup"><span data-stu-id="0fc8d-143">Report Manager F1 Help</span></span>](../../2014/reporting-services/report-manager-f1-help.md)  
  
  
