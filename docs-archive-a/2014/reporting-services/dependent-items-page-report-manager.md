---
title: '[依存アイテム] ページ (レポートマネージャー) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 4dcfb311-e9c3-4c5d-b2e0-018d79f37d2e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 488b10d7d7985972274340897ee3975618a12639
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632990"
---
# <a name="dependent-items-page-report-manager"></a><span data-ttu-id="7dc98-102">[依存アイテム] ページ (レポート マネージャー)</span><span class="sxs-lookup"><span data-stu-id="7dc98-102">Dependent Items Page (Report Manager)</span></span>
  <span data-ttu-id="7dc98-103">[依存アイテム] ページには、共有データ ソースを参照するレポートおよびモデルの一覧を表示できます。</span><span class="sxs-lookup"><span data-stu-id="7dc98-103">Use the Dependent Items page to view a list of reports and models that reference a shared data source.</span></span> <span data-ttu-id="7dc98-104">各アイテムの種類のアイコンはそのアイテムがレポートであるか、またはモデルであるかを示します。</span><span class="sxs-lookup"><span data-stu-id="7dc98-104">The icon for each item type indicates whether it is a report or a model.</span></span> <span data-ttu-id="7dc98-105">このページはリスト ビューまたは詳細ビューで表示できます。</span><span class="sxs-lookup"><span data-stu-id="7dc98-105">This page can be viewed in list view or details view.</span></span> <span data-ttu-id="7dc98-106">アイテムごとの詳細な情報を表示するには詳細ビューを使用します。</span><span class="sxs-lookup"><span data-stu-id="7dc98-106">Use details view to show more information about each item.</span></span> <span data-ttu-id="7dc98-107">詳細ビューでは、より多くのページ オプションを利用できます。</span><span class="sxs-lookup"><span data-stu-id="7dc98-107">Additional page options are available in details view.</span></span> <span data-ttu-id="7dc98-108">共有データ ソースを管理しやすくするために、このページには、データ ソースを使用するレポートおよびモデルへのリンク、レポートやモデルを最後に実行または変更した時点の基準、使用しないレポートやモデルを簡単に削除できる [削除] ボタン、レポートやモデルが必要かどうかを判断する間それらを別の場所に移動できる [移動] ボタンがあります。</span><span class="sxs-lookup"><span data-stu-id="7dc98-108">To help you manage the shared data source, this page provides links to reports and models that use the data source, metrics on when the report or model was last run or modified, and Delete and Move buttons so that you can easily remove reports and models that are no longer used, or move them to a different location while you determine whether they are still needed.</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="7dc98-109">ナビゲーション</span><span class="sxs-lookup"><span data-stu-id="7dc98-109">Navigation</span></span>  
 <span data-ttu-id="7dc98-110">ユーザー インターフェイス (UI) のこの場所に移動するには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="7dc98-110">Use the following procedure to navigate to this location in the user interface (UI).</span></span>  
  
###### <a name="to-open-the-dependent-items-page"></a><span data-ttu-id="7dc98-111">[依存アイテム] ページを開くには</span><span class="sxs-lookup"><span data-stu-id="7dc98-111">To open the Dependent Items page</span></span>  
  
1.  <span data-ttu-id="7dc98-112">レポート マネージャーを開き、依存アイテムを表示する共有データ ソースを探します。</span><span class="sxs-lookup"><span data-stu-id="7dc98-112">Open Report Manager, and locate the shared data source for which you want to view dependent items.</span></span>  
  
2.  <span data-ttu-id="7dc98-113">アイテムの上にマウス ポインターを移動し、下矢印をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7dc98-113">Hover over the item, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="7dc98-114">ドロップダウン メニューの **[管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7dc98-114">In the drop-down menu, click **Manage**.</span></span> <span data-ttu-id="7dc98-115">この操作により、データ ソースの [全般] プロパティ ページが開きます。</span><span class="sxs-lookup"><span data-stu-id="7dc98-115">This opens the General properties page for the data source.</span></span>  
  
4.  <span data-ttu-id="7dc98-116">**[依存アイテム]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="7dc98-116">Select the **Dependent Items** tab.</span></span>  
  
## <a name="options"></a><span data-ttu-id="7dc98-117">Options</span><span class="sxs-lookup"><span data-stu-id="7dc98-117">Options</span></span>  
 <span data-ttu-id="7dc98-118">**Name**</span><span class="sxs-lookup"><span data-stu-id="7dc98-118">**Name**</span></span>  
 <span data-ttu-id="7dc98-119">レポートまたはモデルの名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="7dc98-119">Shows the name of the report or model.</span></span> <span data-ttu-id="7dc98-120">レポート名をクリックして、レポートを開きます。</span><span class="sxs-lookup"><span data-stu-id="7dc98-120">Click the name of the report to open it.</span></span> <span data-ttu-id="7dc98-121">モデルの名前をクリックすると、対応するプロパティ ページが開きます。</span><span class="sxs-lookup"><span data-stu-id="7dc98-121">Click the name of the model to open its property pages.</span></span>  
  
 <span data-ttu-id="7dc98-122">**説明**</span><span class="sxs-lookup"><span data-stu-id="7dc98-122">**Description**</span></span>  
 <span data-ttu-id="7dc98-123">レポートまたはモデルの説明が表示されます。</span><span class="sxs-lookup"><span data-stu-id="7dc98-123">Shows the description of the report or model.</span></span>  
  
 <span data-ttu-id="7dc98-124">**削除**</span><span class="sxs-lookup"><span data-stu-id="7dc98-124">**Delete**</span></span>  
 <span data-ttu-id="7dc98-125">レポート サーバー データベースからレポートまたはモデルを削除する場合にクリックします。</span><span class="sxs-lookup"><span data-stu-id="7dc98-125">Click to delete the report or model from the report server database.</span></span> <span data-ttu-id="7dc98-126">削除する各アイテムの横のチェック ボックスをオンにしてから、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7dc98-126">Before clicking **Delete**, select the check box next to each item that you want to delete.</span></span>  
  
 <span data-ttu-id="7dc98-127">**移動**</span><span class="sxs-lookup"><span data-stu-id="7dc98-127">**Move**</span></span>  
 <span data-ttu-id="7dc98-128">フォルダー階層内でレポートまたはモデルを再配置する場合にクリックします。</span><span class="sxs-lookup"><span data-stu-id="7dc98-128">Click to relocate a report or model within the folder hierarchy.</span></span> <span data-ttu-id="7dc98-129">移動する各アイテムの横のチェック ボックスをオンにしてから、 **[移動]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7dc98-129">Before clicking **Move**, select the check box next to each item that you want to move.</span></span> <span data-ttu-id="7dc98-130">[アイテムの移動] ページが開き、フォルダーを参照して新しい場所を選択することができます。</span><span class="sxs-lookup"><span data-stu-id="7dc98-130">This opens the Move Items page, where you can browse through folders to select a new location.</span></span>  
  
 <span data-ttu-id="7dc98-131">**編集**</span><span class="sxs-lookup"><span data-stu-id="7dc98-131">**Edit**</span></span>  
 <span data-ttu-id="7dc98-132">[プロパティ] アイコンをクリックすると、レポートまたはモデルのプロパティ ページにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="7dc98-132">Click the Property icon to access the property pages of a report, or model.</span></span>  
  
 <span data-ttu-id="7dc98-133">**Type**</span><span class="sxs-lookup"><span data-stu-id="7dc98-133">**Type**</span></span>  
 <span data-ttu-id="7dc98-134">アイテムの種類を示すアイコンが表示されます。</span><span class="sxs-lookup"><span data-stu-id="7dc98-134">Shows the icon of the item type.</span></span>  
  
 <span data-ttu-id="7dc98-135">**更新日**</span><span class="sxs-lookup"><span data-stu-id="7dc98-135">**Modified Date**</span></span>  
 <span data-ttu-id="7dc98-136">前回レポートまたはモデルを変更した日時が表示されます。</span><span class="sxs-lookup"><span data-stu-id="7dc98-136">Shows the date and time when the report or model was last modified.</span></span>  
  
 <span data-ttu-id="7dc98-137">**更新者**</span><span class="sxs-lookup"><span data-stu-id="7dc98-137">**Modified By**</span></span>  
 <span data-ttu-id="7dc98-138">前回アイテムのプロパティを変更したユーザーの名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="7dc98-138">Shows the name of the user who last modified the item properties.</span></span>  
  
 <span data-ttu-id="7dc98-139">**[実行時]**</span><span class="sxs-lookup"><span data-stu-id="7dc98-139">**When Run**</span></span>  
 <span data-ttu-id="7dc98-140">レポート実行スナップショットとして実行するレポートの場合、前回レポートを更新した日時が表示されます。</span><span class="sxs-lookup"><span data-stu-id="7dc98-140">For reports that run as report execution snapshots, displays the date and time at which the report was last refreshed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7dc98-141">参照</span><span class="sxs-lookup"><span data-stu-id="7dc98-141">See Also</span></span>  
 <span data-ttu-id="7dc98-142">[レポートマネージャーの F1 ヘルプ](../../2014/reporting-services/report-manager-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="7dc98-142">[Report Manager F1 Help](../../2014/reporting-services/report-manager-f1-help.md) </span></span>  
 <span data-ttu-id="7dc98-143">[レポート マネージャー &#40;SSRS ネイティブ モード&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="7dc98-143">[Report Manager  &#40;SSRS Native Mode&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="7dc98-144">[[コンテンツ] ページ &#40;レポートマネージャー&#41;](../../2014/reporting-services/contents-page-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="7dc98-144">[Contents Page &#40;Report Manager&#41;](../../2014/reporting-services/contents-page-report-manager.md) </span></span>  
 [<span data-ttu-id="7dc98-145">レポート マネージャー F1 ヘルプ</span><span class="sxs-lookup"><span data-stu-id="7dc98-145">Report Manager F1 Help</span></span>](../../2014/reporting-services/report-manager-f1-help.md)  
  
  
