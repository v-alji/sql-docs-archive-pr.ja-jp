---
title: '[データソースの選択] ページ (レポートマネージャー) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 7f7e8b19-0c0b-4b1f-9cc1-057099aa07eb
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 03c5558397786b02b764b78d47584d9b190290cd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642598"
---
# <a name="data-source-selection-page-report-manager"></a><span data-ttu-id="35665-102">[データ ソースの選択] ページ (レポート マネージャー)</span><span class="sxs-lookup"><span data-stu-id="35665-102">Data Source Selection Page (Report Manager)</span></span>
  <span data-ttu-id="35665-103">[データ ソースの選択] ページを使用すると、レポートまたはレポート モデルで使用する既存の共有データ ソース アイテムを選択できます。</span><span class="sxs-lookup"><span data-stu-id="35665-103">Use the Data Source Selection page to select an existing shared data source item to use with a report or a report model.</span></span> <span data-ttu-id="35665-104">このページは、異なるデータ ソースを選択する場合も使用します。</span><span class="sxs-lookup"><span data-stu-id="35665-104">You can also use this page to select a different data source.</span></span> <span data-ttu-id="35665-105">データ ソースの種類または接続文字列を表示するには、共有データ ソースに移動してプロパティ ページを開く必要があります。</span><span class="sxs-lookup"><span data-stu-id="35665-105">To view the data source type or connection string, you must navigate to the shared data source and open the property pages.</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="35665-106">ナビゲーション</span><span class="sxs-lookup"><span data-stu-id="35665-106">Navigation</span></span>  
 <span data-ttu-id="35665-107">ユーザー インターフェイス (UI) のこの場所に移動するには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="35665-107">Use the following procedure to navigate to this location in the user interface (UI).</span></span>  
  
###### <a name="to-open-the-data-source-selection-page"></a><span data-ttu-id="35665-108">[データ ソースの選択] ページを開くには</span><span class="sxs-lookup"><span data-stu-id="35665-108">To open the Data Source Selection page</span></span>  
  
1.  <span data-ttu-id="35665-109">レポート マネージャーを開き、データ ソースの選択対象のレポートまたはモデルを探します。</span><span class="sxs-lookup"><span data-stu-id="35665-109">Open Report Manager, and locate the report or model for which you want to select a data source.</span></span>  
  
2.  <span data-ttu-id="35665-110">レポートの上にマウス ポインターを移動し、下矢印をクリックします。</span><span class="sxs-lookup"><span data-stu-id="35665-110">Hover over the report, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="35665-111">ドロップダウン メニューの **[管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="35665-111">In the drop-down menu, click **Manage**.</span></span> <span data-ttu-id="35665-112">この操作により、レポートまたはモデルの [全般] プロパティ ページが開きます。</span><span class="sxs-lookup"><span data-stu-id="35665-112">This opens the General properties page for the report or model.</span></span>  
  
4.  <span data-ttu-id="35665-113">**[データ ソース]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="35665-113">Select the **Data Sources** tab.</span></span>  
  
5.  <span data-ttu-id="35665-114">プロパティ ペインで **[共有データ ソース]** を選択し、 **[参照]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="35665-114">In the properties pane, select **A shared data source** and then click **Browse**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="35665-115">Options</span><span class="sxs-lookup"><span data-stu-id="35665-115">Options</span></span>  
 <span data-ttu-id="35665-116">**場所**</span><span class="sxs-lookup"><span data-stu-id="35665-116">**Location**</span></span>  
 <span data-ttu-id="35665-117">共有データ ソース アイテムへの完全パスを、ルート フォルダー名から指定します。</span><span class="sxs-lookup"><span data-stu-id="35665-117">Specify the full path to the shared data source item, beginning with the root folder name.</span></span> <span data-ttu-id="35665-118">共有データ ソース アイテムを参照する際は、パス名を入力することも、ツリー ビューを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="35665-118">You can type the path name or use the tree view to navigate to the shared data source you want.</span></span>  
  
 <span data-ttu-id="35665-119">**ツリー ビュー**</span><span class="sxs-lookup"><span data-stu-id="35665-119">**Tree view**</span></span>  
 <span data-ttu-id="35665-120">レポート サーバー名前空間のフォルダー構造が表示されます。</span><span class="sxs-lookup"><span data-stu-id="35665-120">Shows the folder structure of the report server namespace.</span></span> <span data-ttu-id="35665-121">共有データ ソース アイテムをクリックすると、 **[場所]** フィールドに完全なパスが追加されます。</span><span class="sxs-lookup"><span data-stu-id="35665-121">Click a shared data source item to add the full path to the **Location** field.</span></span>  
  
 <span data-ttu-id="35665-122">**[OK]**</span><span class="sxs-lookup"><span data-stu-id="35665-122">**OK**</span></span>  
 <span data-ttu-id="35665-123">クリックすると、選択したデータ ソースが [データ ソース] プロパティ ページにコピーされます。</span><span class="sxs-lookup"><span data-stu-id="35665-123">Click to copy the data source selection to the Data Sources properties page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35665-124">参照</span><span class="sxs-lookup"><span data-stu-id="35665-124">See Also</span></span>  
 <span data-ttu-id="35665-125">[レポートデータソースの管理](report-data/manage-report-data-sources.md) </span><span class="sxs-lookup"><span data-stu-id="35665-125">[Manage Report Data Sources](report-data/manage-report-data-sources.md) </span></span>  
 <span data-ttu-id="35665-126">[レポート データ ソースに関する資格情報と接続情報を指定する](report-data/specify-credential-and-connection-information-for-report-data-sources.md) </span><span class="sxs-lookup"><span data-stu-id="35665-126">[Specify Credential and Connection Information for Report Data Sources](report-data/specify-credential-and-connection-information-for-report-data-sources.md) </span></span>  
 <span data-ttu-id="35665-127">[[データソース] プロパティページ &#40;レポートマネージャー&#41;](../../2014/reporting-services/data-sources-properties-page-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="35665-127">[Data Sources Properties Page &#40;Report Manager&#41;](../../2014/reporting-services/data-sources-properties-page-report-manager.md) </span></span>  
 <span data-ttu-id="35665-128">[[新しいデータソース] ページ &#40;レポートマネージャー&#41;](../../2014/reporting-services/new-data-source-page-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="35665-128">[New Data Source Page &#40;Report Manager&#41;](../../2014/reporting-services/new-data-source-page-report-manager.md) </span></span>  
 [<span data-ttu-id="35665-129">レポート マネージャー F1 ヘルプ</span><span class="sxs-lookup"><span data-stu-id="35665-129">Report Manager F1 Help</span></span>](../../2014/reporting-services/report-manager-f1-help.md)  
  
  
