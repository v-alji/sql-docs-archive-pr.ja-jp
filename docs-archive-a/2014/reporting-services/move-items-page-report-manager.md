---
title: '[アイテムの移動] ページ (レポートマネージャー) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: fc83b8d2-bc79-4b56-8970-34a1cbbcc176
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 98ff306caf634a5f0478e2eba03c2313b24be274
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739528"
---
# <a name="move-items-page-report-manager"></a><span data-ttu-id="44b69-102">[<ItemName> を移動] ページ (レポート マネージャー)</span><span class="sxs-lookup"><span data-stu-id="44b69-102">Move Items Page (Report Manager)</span></span>
  <span data-ttu-id="44b69-103">[アイテムの移動] ページは、レポート、フォルダー、またはその他のアイテムを、レポート サーバー上の新しい場所に移動するときに使用します。</span><span class="sxs-lookup"><span data-stu-id="44b69-103">Use the Move Items page to move a report, folder, or other item to a new location on the report server.</span></span> <span data-ttu-id="44b69-104">レポート サーバーの名前空間内の移動先を参照する際は、移動先のパスを入力することも、ツリー ビューを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="44b69-104">You can type the path of the new location or use a tree view to browse to a new location in the report server namespace.</span></span> <span data-ttu-id="44b69-105">移動できるアイテムは、移動する権限を持っていて、現在のレポート サーバーに保存されているアイテムに限ります。</span><span class="sxs-lookup"><span data-stu-id="44b69-105">You can only move items that you have permission to move and that are stored on the current report server.</span></span>  
  
 <span data-ttu-id="44b69-106">別のアイテムによって参照されるアイテム (たとえば、多数のレポートによって参照される共有データ ソースまたはモデル) を移動すると、そのアイテムのパス情報は自動的に更新されます。</span><span class="sxs-lookup"><span data-stu-id="44b69-106">When you move an item that is referenced by another item (for example, a shared data source or model that is referenced by many reports), the path information for that item is updated automatically.</span></span> <span data-ttu-id="44b69-107">共有データ ソースを移動しても、それを使用するレポートおよびモデルへのデータ ソース接続は切断されません。</span><span class="sxs-lookup"><span data-stu-id="44b69-107">Moving a shared data source does not disrupt a data source connection to the reports and models that use it.</span></span> <span data-ttu-id="44b69-108">共有データ ソースやモデルの移動先がユーザーに権限のないフォルダーであっても、ユーザーは引き続きそのデータ ソースやモデルを参照するレポートを実行できます。ただし、権限のないユーザーに対してはフォルダー階層にアイテムが表示されなくなります。</span><span class="sxs-lookup"><span data-stu-id="44b69-108">If you move a shared data source or model to a folder for which users do not have permission, they will still be able to run any report that references the data source or model, however the item will not be visible to them in the folder hierarchy.</span></span>  
  
 <span data-ttu-id="44b69-109">**[場所]** にはフォルダーへの完全なパスを、ルート フォルダー名から指定します。</span><span class="sxs-lookup"><span data-stu-id="44b69-109">For **Location**, specify the full path to folder, beginning with the root folder name.</span></span> <span data-ttu-id="44b69-110">フォルダーを参照する際は、パス名を入力することも、ツリー ビューを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="44b69-110">You can type the path name or use the tree view to navigate to the folder you want.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="44b69-111">すべてのアイテムを移動できるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="44b69-111">Not all items are movable.</span></span> <span data-ttu-id="44b69-112">[ホーム]、[個人用レポート]、[Users フォルダー] などの予約済みフォルダーは移動できません。</span><span class="sxs-lookup"><span data-stu-id="44b69-112">You cannot move reserved folders such as Home, My Reports, or Users Folders.</span></span> <span data-ttu-id="44b69-113">レポート履歴またはスナップショットは他の場所に移動できません。</span><span class="sxs-lookup"><span data-stu-id="44b69-113">You cannot move report history or snapshots to different locations.</span></span> <span data-ttu-id="44b69-114">履歴およびスナップショットは、基になるレポートと同じ場所に常に配置し、そのレポートからアクセスします。</span><span class="sxs-lookup"><span data-stu-id="44b69-114">History and snapshots are always located with, and accessed through, the report on which they are based.</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="44b69-115">ナビゲーション</span><span class="sxs-lookup"><span data-stu-id="44b69-115">Navigation</span></span>  
 <span data-ttu-id="44b69-116">ユーザー インターフェイス (UI) のこの場所に移動するには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="44b69-116">Use the following procedures to navigate to this location in the user interface (UI).</span></span>  
  
###### <a name="to-open-the-move-items-page-from-the-contents-page-in-details-view"></a><span data-ttu-id="44b69-117">詳細ビューの [コンテンツ] ページから [<ItemName> を移動] ページを開くには</span><span class="sxs-lookup"><span data-stu-id="44b69-117">To open the Move Items page from the Contents page in Details View</span></span>  
  
1.  <span data-ttu-id="44b69-118">レポート マネージャーを開き、移動するアイテムが含まれるフォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="44b69-118">Open Report Manager, and navigate to the folder that contains an item you want to move.</span></span> <span data-ttu-id="44b69-119">レポート マネージャーのホーム ページからアイテムを移動することもできます。</span><span class="sxs-lookup"><span data-stu-id="44b69-119">You can also move items from the Report Manager Home page.</span></span>  
  
2.  <span data-ttu-id="44b69-120">ツール バーの **[詳細ビュー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="44b69-120">In the toolbar, click **Details View**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="44b69-121">**[タイル ビュー]** しか表示されない場合は、既に **[詳細ビュー]** になっています。</span><span class="sxs-lookup"><span data-stu-id="44b69-121">If you see only **Tiles View**, you are already in **Details View**.</span></span>  
  
3.  <span data-ttu-id="44b69-122">アイテムの横にあるチェック ボックスをオンにし、ツール バーの **[移動]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="44b69-122">Select the box next to an item, and then click **Move** in the toolbar.</span></span> <span data-ttu-id="44b69-123">複数のアイテムを同じ新規の場所に移動する場合は、複数のチェック ボックスをオンにできます。</span><span class="sxs-lookup"><span data-stu-id="44b69-123">You can select more than one box if you want to move multiple items to the same new location.</span></span>  
  
###### <a name="to-open-the-move-items-page-from-the-contents-page-in-tiles-view"></a><span data-ttu-id="44b69-124">タイル ビューの [コンテンツ] ページから [<ItemName> を移動] ページを開くには</span><span class="sxs-lookup"><span data-stu-id="44b69-124">To open the Move Items page from the Contents page in Tiles View</span></span>  
  
1.  <span data-ttu-id="44b69-125">レポート マネージャーを開き、移動するアイテムが含まれるフォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="44b69-125">Open Report Manager, and navigate to the folder that contains an item you want to move.</span></span> <span data-ttu-id="44b69-126">レポート マネージャーのホーム ページからアイテムを移動することもできます。</span><span class="sxs-lookup"><span data-stu-id="44b69-126">You can also move items from the Report Manager Home page.</span></span>  
  
2.  <span data-ttu-id="44b69-127">ツール バーの **[タイル ビュー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="44b69-127">In the toolbar, click **Tiles View**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="44b69-128">**[詳細ビュー]** しか表示されない場合は、既に **[タイル ビュー]** になっています。</span><span class="sxs-lookup"><span data-stu-id="44b69-128">If you see only **Details View**, you are already in **Tiles View**.</span></span>  
  
3.  <span data-ttu-id="44b69-129">アイテムの上にマウス ポインターを移動し、下矢印をクリックします。</span><span class="sxs-lookup"><span data-stu-id="44b69-129">Hover over an item, and click the drop-down arrow.</span></span>  
  
4.  <span data-ttu-id="44b69-130">ドロップダウン メニューの **[移動]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="44b69-130">In the drop-down menu, click **Move**.</span></span>  
  
###### <a name="to-open-the-move-items-page-from-the-general-properties-page-of-an-item"></a><span data-ttu-id="44b69-131">アイテムの [全般] プロパティ ページから [<ItemName> を移動] ページを開くには</span><span class="sxs-lookup"><span data-stu-id="44b69-131">To open the Move Items page from the General Properties page of an item</span></span>  
  
1.  <span data-ttu-id="44b69-132">レポート マネージャーを開き、移動するアイテムが含まれるフォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="44b69-132">Open Report Manager, and navigate to the folder that contains an item you want to move.</span></span> <span data-ttu-id="44b69-133">レポート マネージャーのホーム ページからアイテムを移動することもできます。</span><span class="sxs-lookup"><span data-stu-id="44b69-133">You can also move items from the Report Manager Home page.</span></span>  
  
2.  <span data-ttu-id="44b69-134">アイテムの上にマウス ポインターを移動し、下矢印をクリックします。</span><span class="sxs-lookup"><span data-stu-id="44b69-134">Hover over an item, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="44b69-135">ドロップダウン メニューの **[管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="44b69-135">In the drop-down menu, click **Manage**.</span></span> <span data-ttu-id="44b69-136">この操作により、アイテムの [全般] プロパティ ページが開きます。</span><span class="sxs-lookup"><span data-stu-id="44b69-136">This opens the General properties page for an item.</span></span>  
  
4.  <span data-ttu-id="44b69-137">アイテムのツール バーの **[移動]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="44b69-137">In the item toolbar, click **Move**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44b69-138">参照</span><span class="sxs-lookup"><span data-stu-id="44b69-138">See Also</span></span>  
 <span data-ttu-id="44b69-139">[レポート マネージャー &#40;SSRS ネイティブ モード&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="44b69-139">[Report Manager  &#40;SSRS Native Mode&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="44b69-140">[[全般] プロパティページ、フォルダー &#40;レポートマネージャー&#41;](../../2014/reporting-services/general-properties-page-folders-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="44b69-140">[General Properties Page, Folders &#40;Report Manager&#41;](../../2014/reporting-services/general-properties-page-folders-report-manager.md) </span></span>  
 <span data-ttu-id="44b69-141">[[全般] プロパティページ、レポート &#40;レポートマネージャー&#41;](../../2014/reporting-services/general-properties-page-reports-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="44b69-141">[General Properties Page, Reports &#40;Report Manager&#41;](../../2014/reporting-services/general-properties-page-reports-report-manager.md) </span></span>  
 <span data-ttu-id="44b69-142">[[全般] プロパティページ、リソース &#40;レポートマネージャー&#41;](../../2014/reporting-services/general-properties-page-resources-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="44b69-142">[General Properties Page, Resources &#40;Report Manager&#41;](../../2014/reporting-services/general-properties-page-resources-report-manager.md) </span></span>  
 <span data-ttu-id="44b69-143">[[全般] プロパティページ、共有データソース &#40;レポートマネージャー&#41;](../../2014/reporting-services/general-properties-page-shared-data-sources-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="44b69-143">[General Properties Page, Shared Data Sources &#40;Report Manager&#41;](../../2014/reporting-services/general-properties-page-shared-data-sources-report-manager.md) </span></span>  
 [<span data-ttu-id="44b69-144">レポート マネージャー F1 ヘルプ</span><span class="sxs-lookup"><span data-stu-id="44b69-144">Report Manager F1 Help</span></span>](../../2014/reporting-services/report-manager-f1-help.md)  
  
  
