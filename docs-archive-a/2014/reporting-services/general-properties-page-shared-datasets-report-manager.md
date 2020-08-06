---
title: '[全般] プロパティページ、共有データセット (レポートマネージャー) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 10798e41-24c3-4e69-893b-7ee6af7fc958
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 31825e61cb40505e9167cc2b930a5b79e5aaa013
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646026"
---
# <a name="general-properties-page-shared-datasets-report-manager"></a><span data-ttu-id="ddefb-102">[全般] プロパティ ページ、共有データセット (レポート マネージャー)</span><span class="sxs-lookup"><span data-stu-id="ddefb-102">General Properties Page, Shared Datasets (Report Manager)</span></span>
  <span data-ttu-id="ddefb-103">共有データセット アイテムのプロパティを表示および管理するには、[共有データセット] ページを使用します。</span><span class="sxs-lookup"><span data-stu-id="ddefb-103">Use the Shared Dataset page to view and manage properties for a shared dataset item.</span></span>  
  
 <span data-ttu-id="ddefb-104">レポート マネージャーから、共有データセット定義 (クエリを含む) を表示または変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="ddefb-104">From Report Manager, you cannot view or change the shared dataset definition, including the query.</span></span> <span data-ttu-id="ddefb-105">共有データセット定義を変更するには、レポート作成ツールを使用して定義を開いて変更し、レポート サーバーに保存する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ddefb-105">To change the definition, you must use an authoring tool to open and modify the definition and then save it to the report server.</span></span>  
  
 <span data-ttu-id="ddefb-106">共有データセットを使用すると、データセットを使用するレポート、コンポーネント、および他のカタログ アイテムとは別にデータセットの設定を管理できます。</span><span class="sxs-lookup"><span data-stu-id="ddefb-106">With a shared dataset, you can manage the settings for a dataset separately from reports, components, and other catalog items that use it.</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="ddefb-107">ナビゲーション</span><span class="sxs-lookup"><span data-stu-id="ddefb-107">Navigation</span></span>  
 <span data-ttu-id="ddefb-108">ユーザー インターフェイス (UI) のこの場所に移動するには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="ddefb-108">Use the following procedure to navigate to this location in the user interface (UI).</span></span>  
  
###### <a name="to-open-the-shared-dataset-properties-page-for-a-shared-dataset"></a><span data-ttu-id="ddefb-109">共有データセットの [共有データセット] プロパティ ページを開くには</span><span class="sxs-lookup"><span data-stu-id="ddefb-109">To open the Shared Dataset properties page for a shared dataset</span></span>  
  
1.  <span data-ttu-id="ddefb-110">レポート マネージャーを開き、プロパティを構成する共有データセットを探します。</span><span class="sxs-lookup"><span data-stu-id="ddefb-110">Open Report Manager, and locate shared dataset for which you want to configure properties.</span></span>  
  
2.  <span data-ttu-id="ddefb-111">目的の共有データセットの上にマウス ポインターを移動し、下矢印をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ddefb-111">Hover over the shared dataset, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="ddefb-112">ドロップダウン リストの **[管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ddefb-112">In the drop-down list, click **Manage**.</span></span> <span data-ttu-id="ddefb-113">[全般] プロパティ ページが開きます。</span><span class="sxs-lookup"><span data-stu-id="ddefb-113">The General properties page opens.</span></span>  
  
## <a name="options"></a><span data-ttu-id="ddefb-114">Options</span><span class="sxs-lookup"><span data-stu-id="ddefb-114">Options</span></span>  
 <span data-ttu-id="ddefb-115">**名前**</span><span class="sxs-lookup"><span data-stu-id="ddefb-115">**Name**</span></span>  
 <span data-ttu-id="ddefb-116">共有データセットの名前を入力します。この名前は、レポート サーバーのフォルダー階層内のアイテムを識別するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="ddefb-116">Type a name for the shared dataset that is used to identify the item within the report server folder hierarchy.</span></span>  
  
 <span data-ttu-id="ddefb-117">**説明**</span><span class="sxs-lookup"><span data-stu-id="ddefb-117">**Description**</span></span>  
 <span data-ttu-id="ddefb-118">共有データセットに関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="ddefb-118">Provide information about the shared dataset.</span></span> <span data-ttu-id="ddefb-119">この説明は、[コンテンツ] ページに表示されます。</span><span class="sxs-lookup"><span data-stu-id="ddefb-119">This description appears on the Contents page.</span></span>  
  
 <span data-ttu-id="ddefb-120">**[リスト ビューで非表示にする]**</span><span class="sxs-lookup"><span data-stu-id="ddefb-120">**Hide in list view**</span></span>  
 <span data-ttu-id="ddefb-121">レポート マネージャーでリスト ビュー モードを使用しているユーザーに共有データセットを表示しません。</span><span class="sxs-lookup"><span data-stu-id="ddefb-121">Hide the shared dataset from users who are using list view mode in Report Manager.</span></span> <span data-ttu-id="ddefb-122">リスト ビュー モードは、レポート サーバー フォルダー階層を参照するときの既定のビュー形式です。</span><span class="sxs-lookup"><span data-stu-id="ddefb-122">List view mode is the default view format when browsing the report server folder hierarchy.</span></span> <span data-ttu-id="ddefb-123">リスト ビューでは、アイテム名および説明がページに表示されます。</span><span class="sxs-lookup"><span data-stu-id="ddefb-123">In list view, item names and descriptions flow across the page.</span></span> <span data-ttu-id="ddefb-124">別の形式として詳細ビューがあります。</span><span class="sxs-lookup"><span data-stu-id="ddefb-124">The alternative format is details view.</span></span> <span data-ttu-id="ddefb-125">詳細ビューでは説明が省略されますが、そのアイテムに関するその他の情報は含まれます。</span><span class="sxs-lookup"><span data-stu-id="ddefb-125">Details view omits descriptions, but includes other information about the item.</span></span> <span data-ttu-id="ddefb-126">リスト ビューのアイテムは非表示にできますが、詳細ビューのアイテムは非表示にできません。</span><span class="sxs-lookup"><span data-stu-id="ddefb-126">Although you can hide an item in list view, you cannot hide an item in details view.</span></span> <span data-ttu-id="ddefb-127">アイテムへのアクセスを制限する場合は、ロールの割り当てを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ddefb-127">If you want to restrict access to an item, you must create a role assignment.</span></span>  
  
 <span data-ttu-id="ddefb-128">**[クエリ実行タイムアウト]**</span><span class="sxs-lookup"><span data-stu-id="ddefb-128">**Query execution timeout**</span></span>  
 <span data-ttu-id="ddefb-129">クエリがタイムアウトするまでの秒数を入力します。0の場合、クエリはタイムアウトしません。</span><span class="sxs-lookup"><span data-stu-id="ddefb-129">Type the number of seconds until the query times out. If it is 0, the query does not time out.</span></span>  
  
 <span data-ttu-id="ddefb-130">**[適用]**</span><span class="sxs-lookup"><span data-stu-id="ddefb-130">**Apply**</span></span>  
 <span data-ttu-id="ddefb-131">変更を保存します。</span><span class="sxs-lookup"><span data-stu-id="ddefb-131">Save your changes.</span></span>  
  
 <span data-ttu-id="ddefb-132">**削除**</span><span class="sxs-lookup"><span data-stu-id="ddefb-132">**Delete**</span></span>  
 <span data-ttu-id="ddefb-133">レポート サーバー データベースから共有データセットを削除します。</span><span class="sxs-lookup"><span data-stu-id="ddefb-133">Remove the shared dataset from the report server database.</span></span> <span data-ttu-id="ddefb-134">共有データセットを削除すると、レポートまたはキャッシュされたバージョンすべてが非アクティブ化されます。</span><span class="sxs-lookup"><span data-stu-id="ddefb-134">Deleting a shared dataset deactivates any reports or cached versions.</span></span> <span data-ttu-id="ddefb-135">レポートを再びアクティブ化するには、レポート作成ツールでレポートを 1 つずつ開き、同じ名前および同じフィールド コレクションでデータセットを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ddefb-135">To reactivate a report, you must open each one in a report authoring tool, and specify a dataset with the same name and the same field collection.</span></span> <span data-ttu-id="ddefb-136">別の方法として、各データ領域の参照を更新し、同じフィールド コレクションで異なるデータセットを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="ddefb-136">Alternatively, you can update each data region reference to use a different dataset with the same field collection.</span></span>  
  
 <span data-ttu-id="ddefb-137">**移動**</span><span class="sxs-lookup"><span data-stu-id="ddefb-137">**Move**</span></span>  
 <span data-ttu-id="ddefb-138">レポート サーバーのフォルダー階層内の共有データセットを再配置します。</span><span class="sxs-lookup"><span data-stu-id="ddefb-138">Relocate a shared dataset within the report server folder hierarchy.</span></span> <span data-ttu-id="ddefb-139">このボタンをクリックすると、アイテムの移動ページが表示され、フォルダーを参照して新しい場所を選択できます。</span><span class="sxs-lookup"><span data-stu-id="ddefb-139">Clicking this button opens the Move Items page, on which you can browse through folders for a new folder location.</span></span> <span data-ttu-id="ddefb-140">詳細については、「[[アイテムの移動] ページ &#40;レポートマネージャー&#41;](../../2014/reporting-services/move-items-page-report-manager.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ddefb-140">For more information, see [Move Items Page &#40;Report Manager&#41;](../../2014/reporting-services/move-items-page-report-manager.md).</span></span>  
  
 <span data-ttu-id="ddefb-141">**ダウンロード**</span><span class="sxs-lookup"><span data-stu-id="ddefb-141">**Download**</span></span>  
 <span data-ttu-id="ddefb-142">共有データセット定義のコピーを抽出します。</span><span class="sxs-lookup"><span data-stu-id="ddefb-142">Extract a copy of the shared dataset definition.</span></span> <span data-ttu-id="ddefb-143">このファイルは、コンピューターに定義されているファイルの関連付けに応じて、Visual Studio または他のアプリケーションで開きます。</span><span class="sxs-lookup"><span data-stu-id="ddefb-143">Depending on the file associations defined on your computer, the file will open in Visual Studio or a different application.</span></span> <span data-ttu-id="ddefb-144">ほとんどの場合、共有データセットは XML ファイルとして開きます。</span><span class="sxs-lookup"><span data-stu-id="ddefb-144">In most cases, the shared dataset opens as an XML file.</span></span>  
  
 <span data-ttu-id="ddefb-145">**Replace**</span><span class="sxs-lookup"><span data-stu-id="ddefb-145">**Replace**</span></span>  
 <span data-ttu-id="ddefb-146">共有データセット定義を、ファイル システム上の .rsd ファイルに記述された別の定義に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="ddefb-146">Replace the shared dataset definition with a different one from an .rsd file located on the file system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddefb-147">参照</span><span class="sxs-lookup"><span data-stu-id="ddefb-147">See Also</span></span>  
 <span data-ttu-id="ddefb-148">[レポート マネージャー &#40;SSRS ネイティブ モード&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="ddefb-148">[Report Manager  &#40;SSRS Native Mode&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="ddefb-149">[[コンテンツ] ページ &#40;レポートマネージャー&#41;](../../2014/reporting-services/contents-page-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="ddefb-149">[Contents Page &#40;Report Manager&#41;](../../2014/reporting-services/contents-page-report-manager.md) </span></span>  
 <span data-ttu-id="ddefb-150">[レポートマネージャーの F1 ヘルプ](../../2014/reporting-services/report-manager-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="ddefb-150">[Report Manager F1 Help](../../2014/reporting-services/report-manager-f1-help.md) </span></span>  
 <span data-ttu-id="ddefb-151">[キャッシュ更新オプション &#40;レポートマネージャー&#41;](../../2014/reporting-services/cache-refresh-options-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="ddefb-151">[Cache Refresh Options &#40;Report Manager&#41;](../../2014/reporting-services/cache-refresh-options-report-manager.md) </span></span>  
 <span data-ttu-id="ddefb-152">[[キャッシュ] ページ、共有データセット &#40;レポートマネージャー&#41;](../../2014/reporting-services/caching-page-shared-datasets-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="ddefb-152">[Caching Page, Shared Datasets &#40;Report Manager&#41;](../../2014/reporting-services/caching-page-shared-datasets-report-manager.md) </span></span>  
 <span data-ttu-id="ddefb-153">[共有データセットの管理](report-data/manage-shared-datasets.md) </span><span class="sxs-lookup"><span data-stu-id="ddefb-153">[Manage Shared Datasets](report-data/manage-shared-datasets.md) </span></span>  
 [<span data-ttu-id="ddefb-154">共有データセットのキャッシュ &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="ddefb-154">Cache Shared Datasets &#40;SSRS&#41;</span></span>](report-server/cache-shared-datasets-ssrs.md)  
  
  
