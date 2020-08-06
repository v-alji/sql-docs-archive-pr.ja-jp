---
title: アイテムの移動または削除 (レポート マネージャー) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- moving items
- items [Reporting Services], moving
ms.assetid: 980a66c7-a18b-4af7-8954-45726fa517d6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3a61ad56ea9e20e7fdf38d5acf05529b685ee896
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711605"
---
# <a name="move-or-delete-an-item-report-manager"></a><span data-ttu-id="e74d5-102">アイテムの移動または削除 (レポート マネージャー)</span><span class="sxs-lookup"><span data-stu-id="e74d5-102">Move or Delete an Item (Report Manager)</span></span>
  <span data-ttu-id="e74d5-103">レポート サーバーにパブリッシュしたレポートやレポート関連アイテムは、フォルダーに格納されます。</span><span class="sxs-lookup"><span data-stu-id="e74d5-103">Reports and report-related items that you publish to a report server are stored in folders.</span></span> <span data-ttu-id="e74d5-104">アイテムは異なるフォルダーに移動でき、それらのアイテムへの参照はレポート サーバーによって自動的に保持されます。</span><span class="sxs-lookup"><span data-stu-id="e74d5-104">You can move items to a different folder and references to those items are maintained automatically by the report server.</span></span> <span data-ttu-id="e74d5-105">アイテムを削除する前に、そのアイテムに依存しているアイテムが他に存在しないか確認してください。</span><span class="sxs-lookup"><span data-stu-id="e74d5-105">Before you delete an item, consider whether other items depend on it.</span></span>  
  
## <a name="move-an-item"></a><span data-ttu-id="e74d5-106">アイテムの移動</span><span class="sxs-lookup"><span data-stu-id="e74d5-106">Move an Item</span></span>  
 <span data-ttu-id="e74d5-107">レポート サーバー アイテムは、レポート サーバー フォルダー階層内の異なるフォルダーに移動できます。</span><span class="sxs-lookup"><span data-stu-id="e74d5-107">You can move report server items to different folder locations in the report server folder hierarchy.</span></span> <span data-ttu-id="e74d5-108">アイテムを移動すると、セキュリティ設定などのすべてのプロパティが、アイテムと共に新しい場所に移動します。</span><span class="sxs-lookup"><span data-stu-id="e74d5-108">When you move an item, all properties (including security settings) move with the item to the new location.</span></span> <span data-ttu-id="e74d5-109">フォルダーを移動すると、そのフォルダーに含まれるすべてのアイテムも移動します。</span><span class="sxs-lookup"><span data-stu-id="e74d5-109">When you move a folder, all the items in the folder move with it.</span></span>  
  
 <span data-ttu-id="e74d5-110">レポート マネージャーでは、移動できるアイテムがフォルダー階層で示されています。</span><span class="sxs-lookup"><span data-stu-id="e74d5-110">In Report Manager, the items that you can move are indicated in the folder hierarchy.</span></span> <span data-ttu-id="e74d5-111">移動可能な各アイテムのアイコンを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="e74d5-111">The following table shows the icon for each movable item.</span></span>  
  
|<span data-ttu-id="e74d5-112">アイコン</span><span class="sxs-lookup"><span data-stu-id="e74d5-112">Icon</span></span>|<span data-ttu-id="e74d5-113">移動可能なアイテム</span><span class="sxs-lookup"><span data-stu-id="e74d5-113">Moveable item</span></span>|  
|----------|-------------------|  
|<span data-ttu-id="e74d5-114">![Report icon](../media/hlp-16doc.gif "レポート アイコン")</span><span class="sxs-lookup"><span data-stu-id="e74d5-114">![Report icon](../media/hlp-16doc.gif "Report icon")</span></span>|<span data-ttu-id="e74d5-115">レポート</span><span class="sxs-lookup"><span data-stu-id="e74d5-115">Report</span></span>|  
|<span data-ttu-id="e74d5-116">![リンク レポート アイコン](../media/hlp-16linked.gif "リンク レポート アイコン")</span><span class="sxs-lookup"><span data-stu-id="e74d5-116">![Linked report icon](../media/hlp-16linked.gif "Linked report icon")</span></span>|<span data-ttu-id="e74d5-117">リンク レポート</span><span class="sxs-lookup"><span data-stu-id="e74d5-117">Linked report</span></span>|  
|<span data-ttu-id="e74d5-118">![フォルダー アイコン](../media/hlp-16folder.gif "フォルダー アイコン")</span><span class="sxs-lookup"><span data-stu-id="e74d5-118">![Folder icon](../media/hlp-16folder.gif "Folder icon")</span></span>|<span data-ttu-id="e74d5-119">Folder</span><span class="sxs-lookup"><span data-stu-id="e74d5-119">Folder</span></span>|  
|<span data-ttu-id="e74d5-120">![汎用リソース アイコン](../media/hlp-16file.gif "汎用リソース アイコン")</span><span class="sxs-lookup"><span data-stu-id="e74d5-120">![generic resource icon](../media/hlp-16file.gif "generic resource icon")</span></span>|<span data-ttu-id="e74d5-121">汎用リソース</span><span class="sxs-lookup"><span data-stu-id="e74d5-121">Generic resource</span></span>|  
|<span data-ttu-id="e74d5-122">![Shared data source icon](../media/hlp-16datasource.png "共有データ ソースのアイコン")</span><span class="sxs-lookup"><span data-stu-id="e74d5-122">![Shared data source icon](../media/hlp-16datasource.png "Shared data source icon")</span></span>|<span data-ttu-id="e74d5-123">[共有データ ソース]</span><span class="sxs-lookup"><span data-stu-id="e74d5-123">Shared data source</span></span>|  
||<span data-ttu-id="e74d5-124">共有データセット</span><span class="sxs-lookup"><span data-stu-id="e74d5-124">Shared dataset</span></span>|  
  
 <span data-ttu-id="e74d5-125">作業に使用するすべてのアイテムを移動できるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="e74d5-125">Not all items that you work with can be moved.</span></span> <span data-ttu-id="e74d5-126">サブスクリプションまたはレポート履歴など、レポートに関連付けられたアイテムを移動することはできません。</span><span class="sxs-lookup"><span data-stu-id="e74d5-126">You cannot move items that are associated with a report, such as subscriptions or report history.</span></span> <span data-ttu-id="e74d5-127">これらのアイテムは、関連するレポートと共に移動します。</span><span class="sxs-lookup"><span data-stu-id="e74d5-127">Those items move with their associated reports.</span></span> <span data-ttu-id="e74d5-128">同様に、フォルダー階層の外部にある、共有スケジュールなどのアイテムは移動できません。</span><span class="sxs-lookup"><span data-stu-id="e74d5-128">Similarly, you cannot move items, such as shared schedules, that exist outside of the folder hierarchy.</span></span> <span data-ttu-id="e74d5-129">操作を行うための権限がない場合は、アイテムを移動できません。</span><span class="sxs-lookup"><span data-stu-id="e74d5-129">You cannot move items if you lack permission to do so.</span></span> <span data-ttu-id="e74d5-130">アイテムを移動するための権限は、当該アイテムのロールの割り当てで "レポートの管理"、"モデルの管理"、"フォルダーの管理、および "データ ソースの管理" のタスクを選択した場合に許可されます。</span><span class="sxs-lookup"><span data-stu-id="e74d5-130">Permission to move an item is conveyed when the following tasks are selected in your role assignment for the item in question: "Manage reports," "Manage models", "Manage folders," and "Manage data sources."</span></span>  
  
#### <a name="to-move-an-item-from-within-the-contents-page"></a><span data-ttu-id="e74d5-131">[コンテンツ] ページでアイテムを移動するには</span><span class="sxs-lookup"><span data-stu-id="e74d5-131">To move an item from within the Contents page</span></span>  
  
1.  <span data-ttu-id="e74d5-132">Start [レポートマネージャー &#40;SSRS ネイティブモード&#41;]../report-manager-ssrs-native-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="e74d5-132">Start [Report Manager  &#40;SSRS Native Mode&#41;]../report-manager-ssrs-native-mode.md).</span></span>  
  
2.  <span data-ttu-id="e74d5-133">レポート マネージャーで、 **[コンテンツ]** ページに移動し、移動するアイテムを探します。</span><span class="sxs-lookup"><span data-stu-id="e74d5-133">In Report Manager, navigate to the **Contents** page, and locate the item that you want to move.</span></span>  
  
3.  <span data-ttu-id="e74d5-134">アイテムの上にマウス ポインターを移動し、下矢印をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e74d5-134">Hover over the item, and click the drop-down arrow.</span></span>  
  
4.  <span data-ttu-id="e74d5-135">ドロップダウン メニューの **[移動]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e74d5-135">In the drop-down menu, click **Move**.</span></span>  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
6.  <span data-ttu-id="e74d5-136">**[場所]** については、アイテムの移動先のフォルダーを指定します。</span><span class="sxs-lookup"><span data-stu-id="e74d5-136">For **Location**, specify the folder you want to move the item to.</span></span> <span data-ttu-id="e74d5-137">フォルダーの完全修飾名を入力するか、またはツリー コントロールを使用して目的のフォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="e74d5-137">You can type the fully qualified folder name or use the tree control to navigate to the folder.</span></span>  
  
7.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
 <span data-ttu-id="e74d5-138">または、移動するオブジェクトに移動して **[プロパティ]** をクリックし、ページの上部にある **[移動]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e74d5-138">Alternatively, you can navigate to the object you want to move, click **Properties**, and then click **Move** at the top of the page.</span></span>  
  
## <a name="delete-an-item"></a><span data-ttu-id="e74d5-139">項目を削除する</span><span class="sxs-lookup"><span data-stu-id="e74d5-139">Delete an item</span></span>  
 <span data-ttu-id="e74d5-140">アイテムを削除する前に、そのアイテムが他のアイテムによって使用されていないかどうかを確認してください。</span><span class="sxs-lookup"><span data-stu-id="e74d5-140">Before you delete an item, determine if it is used by other items.</span></span> <span data-ttu-id="e74d5-141">たとえば、共有データ ソースを削除した場合、そのデータ ソースを使用するレポートおよびモデルは実行できなくなります。</span><span class="sxs-lookup"><span data-stu-id="e74d5-141">For example, if you delete a shared data source, reports and models that use that data source will no longer run.</span></span> <span data-ttu-id="e74d5-142">レポートを削除すると、そのレポートに関連付けられているサブスクリプションおよびレポート履歴も削除されます。</span><span class="sxs-lookup"><span data-stu-id="e74d5-142">If you delete a report, subscriptions and report history associated with that report are also deleted.</span></span> <span data-ttu-id="e74d5-143">アイテムの依存アイテムを検索するには、[依存アイテム] ページ &#40;レポートマネージャー&#41;] を参照してください。/dependent-items-page-report-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="e74d5-143">To find dependent items for an item, see [Dependent Items Page &#40;Report Manager&#41;]../dependent-items-page-report-manager.md).</span></span>  
  
#### <a name="to-delete-a-report-or-item"></a><span data-ttu-id="e74d5-144">レポートまたはアイテムを削除するには</span><span class="sxs-lookup"><span data-stu-id="e74d5-144">To delete a report or item</span></span>  
  
1.  <span data-ttu-id="e74d5-145">Start [レポートマネージャー &#40;SSRS ネイティブモード&#41;]../report-manager-ssrs-native-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="e74d5-145">Start [Report Manager  &#40;SSRS Native Mode&#41;]../report-manager-ssrs-native-mode.md).</span></span>  
  
2.  <span data-ttu-id="e74d5-146">レポート マネージャーで、 **[コンテンツ]** ページに移動し、削除するアイテムを探します。</span><span class="sxs-lookup"><span data-stu-id="e74d5-146">In Report Manager, navigate to the **Contents** page, and locate the item that you want to delete.</span></span>  
  
3.  <span data-ttu-id="e74d5-147">アイテムの上にマウス ポインターを移動し、下矢印をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e74d5-147">Hover over the item, and click the drop-down arrow.</span></span>  
  
4.  <span data-ttu-id="e74d5-148">ドロップダウン メニューの **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e74d5-148">In the drop-down menu, click **Delete**.</span></span>  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e74d5-149">参照</span><span class="sxs-lookup"><span data-stu-id="e74d5-149">See Also</span></span>  
 <span data-ttu-id="e74d5-150">[コンテンツページ &#40;レポートマネージャー&#41;]../contents-page-report-manager.md)</span><span class="sxs-lookup"><span data-stu-id="e74d5-150">[Contents Page &#40;Report Manager&#41;]../contents-page-report-manager.md)</span></span>   
 [<span data-ttu-id="e74d5-151">レポートの検索、表示、管理 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="e74d5-151">Finding, Viewing, and Managing Reports &#40;Report Builder and SSRS &#41;</span></span>](../report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md)  
  
  
