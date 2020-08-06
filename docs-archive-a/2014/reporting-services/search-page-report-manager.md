---
title: '[検索] ページ (レポートマネージャー) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 51ffdc07-e1b9-4ed7-acb3-dd98d7cce273
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2528133f5b2ecc4bed4c16fdd476591b3bab52d2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641451"
---
# <a name="search-page-report-manager"></a><span data-ttu-id="3c823-102">[検索] ページ (レポート マネージャー)</span><span class="sxs-lookup"><span data-stu-id="3c823-102">Search Page (Report Manager)</span></span>
  <span data-ttu-id="3c823-103">レポート、リンク レポート、レポート モデル、共有データ ソース、フォルダー、またはリソースに対して指定された検索操作の結果を表示するには、[検索結果] ページを使用します。</span><span class="sxs-lookup"><span data-stu-id="3c823-103">Use the Search Results page to view the results of a search operation specified for a report, linked report, report model, shared data source, folder, or resource.</span></span> <span data-ttu-id="3c823-104">検索結果はアルファベット順に表示されます。</span><span class="sxs-lookup"><span data-stu-id="3c823-104">Search results are listed alphabetically.</span></span> <span data-ttu-id="3c823-105">型、名前、または説明で並べ替えることができます。</span><span class="sxs-lookup"><span data-stu-id="3c823-105">You can sort by type, name, or description.</span></span>  
  
 <span data-ttu-id="3c823-106">レポート履歴に含まれるレポート スナップショット、サブスクリプション、および共有スケジュールは、検索操作から除外されます。</span><span class="sxs-lookup"><span data-stu-id="3c823-106">The following items are excluded from a search operation: report snapshots contained in report history, subscriptions, and shared schedules.</span></span> <span data-ttu-id="3c823-107">同様に、フォルダーまたはレポートの表示権限が不十分な場合も、そのアイテムは検索対象から除外されます。</span><span class="sxs-lookup"><span data-stu-id="3c823-107">Similarly, insufficient permission to view a folder or report excludes that item from a search.</span></span>  
  
 <span data-ttu-id="3c823-108">レポートまたはモデル内のテキストを検索することはできません。</span><span class="sxs-lookup"><span data-stu-id="3c823-108">You cannot search for text within a report or model.</span></span> <span data-ttu-id="3c823-109">レポート内の特定のテキストを検索するには、レポートの最上部にあるツール バーを使用します。</span><span class="sxs-lookup"><span data-stu-id="3c823-109">To search for specific text within a report, use the toolbar at the top of the report.</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="3c823-110">ナビゲーション</span><span class="sxs-lookup"><span data-stu-id="3c823-110">Navigation</span></span>  
 <span data-ttu-id="3c823-111">ユーザー インターフェイス (UI) のこの場所に移動するには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="3c823-111">Use the following procedure to navigate to this location in the user interface (UI).</span></span>  
  
###### <a name="to-open-the-search-results-page"></a><span data-ttu-id="3c823-112">[検索結果] ページを開くには</span><span class="sxs-lookup"><span data-stu-id="3c823-112">To open the Search Results page</span></span>  
  
1.  <span data-ttu-id="3c823-113">レポート マネージャーを開きます。</span><span class="sxs-lookup"><span data-stu-id="3c823-113">Open Report Manager.</span></span>  
  
2.  <span data-ttu-id="3c823-114">ページ上部の **[検索]** ボックスに検索条件を入力します。</span><span class="sxs-lookup"><span data-stu-id="3c823-114">At the top of the page, type your search criteria in the **Search** box.</span></span> <span data-ttu-id="3c823-115">Enter キーを押し、検索の矢印をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3c823-115">Then press Enter or click the Search arrow.</span></span>  
  
## <a name="options"></a><span data-ttu-id="3c823-116">Options</span><span class="sxs-lookup"><span data-stu-id="3c823-116">Options</span></span>  
 <span data-ttu-id="3c823-117">**削除**</span><span class="sxs-lookup"><span data-stu-id="3c823-117">**Delete**</span></span>  
 <span data-ttu-id="3c823-118">レポート サーバー データベースからアイテムを削除する場合にクリックします。</span><span class="sxs-lookup"><span data-stu-id="3c823-118">Click to remove an item from a report server database.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3c823-119">このボタンは、 **[詳細ビュー]** でのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="3c823-119">This button is available only in **Details View**.</span></span> <span data-ttu-id="3c823-120">ただし、 **[詳細ビュー]** または **[リスト ビュー]** では、アイテムの上にマウス ポインターを移動し、メニューを使用して削除機能を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="3c823-120">However, you can hover over an item and use the menu to access the delete functionality in either **Details View** or in **List View**.</span></span>  
  
 <span data-ttu-id="3c823-121">**移動**</span><span class="sxs-lookup"><span data-stu-id="3c823-121">**Move**</span></span>  
 <span data-ttu-id="3c823-122">アイテムを再配置する場合にクリックします。</span><span class="sxs-lookup"><span data-stu-id="3c823-122">Click to relocate an item.</span></span> <span data-ttu-id="3c823-123">[アイテムの移動] ページが開き、別のフォルダーの場所を選択することができます。</span><span class="sxs-lookup"><span data-stu-id="3c823-123">This opens the Move Items page, where you can select a different folder location.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3c823-124">このボタンは、 **[詳細ビュー]** でのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="3c823-124">This button is available only in **Details View**.</span></span> <span data-ttu-id="3c823-125">ただし、 **[詳細ビュー]** または **[リスト ビュー]** では、アイテムの上にマウス ポインターを移動し、メニューを使用して移動機能を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="3c823-125">However, you can hover over an item and use the menu to access the move functionality in either **Details View** or in **List View**.</span></span>  
  
 <span data-ttu-id="3c823-126">検索ボックス</span><span class="sxs-lookup"><span data-stu-id="3c823-126">Search box</span></span>  
 <span data-ttu-id="3c823-127">検索するアイテムの名前の一部またはすべてを入力し、 **[実行]** をクリックして検索を開始します。</span><span class="sxs-lookup"><span data-stu-id="3c823-127">Type all or part of the name of an item that you want to locate, and then click **Go** to start the search.</span></span> <span data-ttu-id="3c823-128">検索できる文字列の長さは、128 文字までです。</span><span class="sxs-lookup"><span data-stu-id="3c823-128">The longest string you can search for is 128 characters.</span></span>  
  
 <span data-ttu-id="3c823-129">アイテムの名前または説明のテキスト値の中に検索文字列全体が含まれていると、それらが検索結果に表示されます。</span><span class="sxs-lookup"><span data-stu-id="3c823-129">Item names or descriptions that contain the entire search string anywhere in the text value are included in the search results.</span></span>  
  
 <span data-ttu-id="3c823-130">プラス記号 (+) などの論理演算子はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="3c823-130">Boolean operators such as the plus character (+) are not supported.</span></span>  
  
 <span data-ttu-id="3c823-131">**詳細ビュー**</span><span class="sxs-lookup"><span data-stu-id="3c823-131">**Details View**</span></span>  
 <span data-ttu-id="3c823-132">アイテムの種類、名前、説明、アイテムが格納されているフォルダー、最後に実行された時刻など、アイテムに関する詳細な情報が含まれる一覧として [検索結果] ページを表示する場合にクリックします。</span><span class="sxs-lookup"><span data-stu-id="3c823-132">Click to display the Search Results page in a list that contains additional information about items, such as the item type, name, description, the folder in which the item is located, and when it was last run.</span></span> <span data-ttu-id="3c823-133">**[詳細ビュー]** では、 **[削除]** ボタンと **[移動]** ボタンを使用して、フォルダー内のアイテムを削除および再配置することができます。</span><span class="sxs-lookup"><span data-stu-id="3c823-133">In **Details View**, you can use **Delete** and **Move** buttons to remove and relocate items in the folder.</span></span>  
  
 <span data-ttu-id="3c823-134">選択したアイテムのプロパティの表示と構成に使用するドロップダウン メニューを開くには、アイテムの上にマウス ポインターを移動し、下矢印をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3c823-134">Hover over an item and click the drop-down arrow to open the drop-down menu from which you can access and configure properties of the selected item.</span></span>  
  
 <span data-ttu-id="3c823-135">**リストビュー**</span><span class="sxs-lookup"><span data-stu-id="3c823-135">**List View**</span></span>  
 <span data-ttu-id="3c823-136">**[詳細ビュー]** に表示されるような詳細情報を省略して [検索結果] ページを表示する場合にクリックします。</span><span class="sxs-lookup"><span data-stu-id="3c823-136">Click to display the Search Results page without details as in **Details View**.</span></span> <span data-ttu-id="3c823-137">[検索結果] ページを開くとき、既定では [リスト ビュー] が使用されます。</span><span class="sxs-lookup"><span data-stu-id="3c823-137">List View is the default view when the Search Results page opens.</span></span>  
  
 <span data-ttu-id="3c823-138">選択したアイテムのプロパティの表示と構成に使用するドロップダウン メニューを開くには、アイテムの上にマウス ポインターを移動し、下矢印をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3c823-138">Hover over an item and click the drop-down arrow to open the drop-down menu from which you can access and configure properties of the selected item.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c823-139">参照</span><span class="sxs-lookup"><span data-stu-id="3c823-139">See Also</span></span>  
 <span data-ttu-id="3c823-140">[レポート マネージャー &#40;SSRS ネイティブ モード&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="3c823-140">[Report Manager  &#40;SSRS Native Mode&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span></span>  
 [<span data-ttu-id="3c823-141">レポート マネージャー F1 ヘルプ</span><span class="sxs-lookup"><span data-stu-id="3c823-141">Report Manager F1 Help</span></span>](../../2014/reporting-services/report-manager-f1-help.md)  
  
  
