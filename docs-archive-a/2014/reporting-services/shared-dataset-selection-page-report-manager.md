---
title: '[共有データセットの選択] ページ (レポートマネージャー) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: a67dc03e-f838-4ec2-9ef6-f04895bab3c7
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ad26246f04c741c186b61967e3e71aa4d5dd55f5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713749"
---
# <a name="shared-dataset-selection-page-report-manager"></a><span data-ttu-id="5c352-102">[共有データセットの選択] ページ (レポート マネージャー)</span><span class="sxs-lookup"><span data-stu-id="5c352-102">Shared Dataset Selection Page (Report Manager)</span></span>
  <span data-ttu-id="5c352-103">[共有データセットの選択] ページでは、現在レポートに関連付けられている共有データセットを確認および変更できます。</span><span class="sxs-lookup"><span data-stu-id="5c352-103">Use the Shared Dataset Selection page to review and modify the shared datasets that are currently associated with a report.</span></span>  
  
 <span data-ttu-id="5c352-104">このページを使用して、レポートにさらに共有データセットを追加したり、レポートから共有データセットを削除したりすることはできません。</span><span class="sxs-lookup"><span data-stu-id="5c352-104">You cannot use this page to add more shared datasets to a report or remove shared datasets from a report.</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="5c352-105">ナビゲーション</span><span class="sxs-lookup"><span data-stu-id="5c352-105">Navigation</span></span>  
 <span data-ttu-id="5c352-106">ユーザー インターフェイス (UI) のこの場所に移動するには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="5c352-106">Use the following procedure to navigate to this location in the user interface (UI).</span></span>  
  
###### <a name="to-open-the-shared-dataset-selection-page"></a><span data-ttu-id="5c352-107">[共有データセットの選択] ページを開くには</span><span class="sxs-lookup"><span data-stu-id="5c352-107">To open the Shared Dataset Selection page</span></span>  
  
1.  <span data-ttu-id="5c352-108">レポート マネージャーを開き、共有データセットを確認するレポートを探します。</span><span class="sxs-lookup"><span data-stu-id="5c352-108">Open Report Manager, and locate the report for which you want to review the shared datasets.</span></span>  
  
2.  <span data-ttu-id="5c352-109">レポートの上にマウス ポインターを移動し、下矢印をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5c352-109">Hover over the report, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="5c352-110">ドロップダウン メニューの **[管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5c352-110">In the drop-down menu, click **Manage**.</span></span> <span data-ttu-id="5c352-111">この操作により、レポートの [全般] プロパティ ページが開きます。</span><span class="sxs-lookup"><span data-stu-id="5c352-111">This opens the General properties page for the report.</span></span>  
  
4.  <span data-ttu-id="5c352-112">**[共有データセット]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="5c352-112">Select the **Shared Datasets** tab.</span></span>  
  
## <a name="options"></a><span data-ttu-id="5c352-113">Options</span><span class="sxs-lookup"><span data-stu-id="5c352-113">Options</span></span>  
 <span data-ttu-id="5c352-114">**[参照]**</span><span class="sxs-lookup"><span data-stu-id="5c352-114">**Browse**</span></span>  
 <span data-ttu-id="5c352-115">レポートの共有データセット名ごとに、対象になる共有データセットの現在のフォルダー パスと名前を確認できます。</span><span class="sxs-lookup"><span data-stu-id="5c352-115">For each shared dataset name in a report, you can review the current folder path and name for the target shared dataset.</span></span>  
  
 <span data-ttu-id="5c352-116">データセット名によって参照される共有データセットを変更するには、 **[参照]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="5c352-116">To change the shared dataset referenced by a dataset name, click the **Browse** button.</span></span>  
  
 <span data-ttu-id="5c352-117">**[参照]** ボタンにより、レポート サーバーのフォルダー構造が開きます。</span><span class="sxs-lookup"><span data-stu-id="5c352-117">The **Browse** button opens the folder structure of the report server.</span></span> <span data-ttu-id="5c352-118">共有データセットをクリックすると、 **[場所]** フィールドに完全なパスが追加されます。</span><span class="sxs-lookup"><span data-stu-id="5c352-118">Click a shared dataset to add the full path to the **Location** field.</span></span>  
  
 <span data-ttu-id="5c352-119">**[OK]** ボタンをクリックして共有データセットの選択を完了するか、または **[キャンセル]** をクリックして共有データセットの参照を取り消します。</span><span class="sxs-lookup"><span data-stu-id="5c352-119">Click the **OK** button to finish selecting a shared dataset or click **Cancel** to cancel browsing for a shared dataset.</span></span>  
  
 <span data-ttu-id="5c352-120">**[適用]**</span><span class="sxs-lookup"><span data-stu-id="5c352-120">**Apply**</span></span>  
 <span data-ttu-id="5c352-121">変更を保存します。</span><span class="sxs-lookup"><span data-stu-id="5c352-121">Save your changes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c352-122">参照</span><span class="sxs-lookup"><span data-stu-id="5c352-122">See Also</span></span>  
 <span data-ttu-id="5c352-123">[レポート マネージャー &#40;SSRS ネイティブ モード&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="5c352-123">[Report Manager  &#40;SSRS Native Mode&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="5c352-124">[[コンテンツ] ページ &#40;レポートマネージャー&#41;](../../2014/reporting-services/contents-page-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="5c352-124">[Contents Page &#40;Report Manager&#41;](../../2014/reporting-services/contents-page-report-manager.md) </span></span>  
 <span data-ttu-id="5c352-125">[共有データセットの管理](report-data/manage-shared-datasets.md) </span><span class="sxs-lookup"><span data-stu-id="5c352-125">[Manage Shared Datasets](report-data/manage-shared-datasets.md) </span></span>  
 <span data-ttu-id="5c352-126">[レポートマネージャーの F1 ヘルプ](../../2014/reporting-services/report-manager-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="5c352-126">[Report Manager F1 Help](../../2014/reporting-services/report-manager-f1-help.md) </span></span>  
 <span data-ttu-id="5c352-127">[レポートビルダー内のレポートパーツとデータセット](report-data/report-parts-and-datasets-in-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="5c352-127">[Report Parts and Datasets in Report Builder](report-data/report-parts-and-datasets-in-report-builder.md) </span></span>  
 [<span data-ttu-id="5c352-128">埋め込みデータセットと共有データセット &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="5c352-128">Embedded and Shared Datasets &#40;Report Builder and SSRS&#41;</span></span>](report-data/embedded-and-shared-datasets-report-builder-and-ssrs.md)  
  
  
