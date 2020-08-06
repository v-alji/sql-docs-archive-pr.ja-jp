---
title: '[デザイン] ビュー | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.layoutview.f1
helpviewer_keywords:
- Layout View dialog box
ms.assetid: 6fa378aa-442f-4d2f-beab-02a0fb5cd3ce
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e4f8f3639318062bb36d650a57f63f9033a2ae73
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716049"
---
# <a name="design-view"></a><span data-ttu-id="dc548-102">デザイン ビュー</span><span class="sxs-lookup"><span data-stu-id="dc548-102">Design View</span></span>
  <span data-ttu-id="dc548-103">[デザイン] ビューを使用すると、レポートにレポート アイテムを配置できます。</span><span class="sxs-lookup"><span data-stu-id="dc548-103">Use Design view to arrange report items in the report.</span></span> <span data-ttu-id="dc548-104">[デザイン] ビューは、デザイン画面またはレイアウト ビューと呼ばれることもあります。</span><span class="sxs-lookup"><span data-stu-id="dc548-104">Design view is sometimes called the design surface or layout view.</span></span>  
  
## <a name="report-design-surface"></a><span data-ttu-id="dc548-105">レポート デザイン画面</span><span class="sxs-lookup"><span data-stu-id="dc548-105">Report Design Surface</span></span>  
 <span data-ttu-id="dc548-106">デザイン画面は、レポート本文、ページ ヘッダー、ページ フッターという 3 つのセクションで構成されています。</span><span class="sxs-lookup"><span data-stu-id="dc548-106">The design surface consists of three sections: report body, page header, and page footer.</span></span> <span data-ttu-id="dc548-107">これらの 3 つのセクションのいずれかに追加するアイテムを選択するには、[ツールボックス] を使用します。</span><span class="sxs-lookup"><span data-stu-id="dc548-107">Use the Toolbox to select items to place in any of these three sections.</span></span> <span data-ttu-id="dc548-108">[レポート データ] ペインを使用すると、画像、パラメーター、データ ソース、およびデータセット (データセット クエリやフィールド一覧を含む) を表示できます。</span><span class="sxs-lookup"><span data-stu-id="dc548-108">Use the Report Data pane to view images, parameters, data sources, and datasets, including dataset queries and field lists.</span></span> <span data-ttu-id="dc548-109">レポート アイテムをデザイン画面に追加したら、 **[レポート データ]** ペインから、テーブル、マトリックス、一覧などのデータ領域にデータセット フィールドをドラッグします。</span><span class="sxs-lookup"><span data-stu-id="dc548-109">After you add report items to the design surface, drag dataset fields from the **Report Data** pane onto data regions such as table, matrix, or list.</span></span> <span data-ttu-id="dc548-110">レポートのデザイン画面上の各アイテムには、プロパティ ダイアログ ボックスまたは [プロパティ] ペインを使用して管理できるプロパティが含まれています。</span><span class="sxs-lookup"><span data-stu-id="dc548-110">Each item on the report design surface contains properties that can be managed using a properties dialog box or the Properties pane.</span></span>  
  
## <a name="toolbox"></a><span data-ttu-id="dc548-111">ツールボックス</span><span class="sxs-lookup"><span data-stu-id="dc548-111">Toolbox</span></span>  
 <span data-ttu-id="dc548-112">[ツール ボックス] には、レポートに使用できるデータ領域およびその他のレポート アイテムが表示されます。</span><span class="sxs-lookup"><span data-stu-id="dc548-112">The Toolbox lists data regions and other report items that are available for your report.</span></span> <span data-ttu-id="dc548-113">[ツール ボックス] からレポート アイテムを追加するには、アイテムをダブルクリックするか、アイテムをデザイン画面にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="dc548-113">To add report items from the Toolbox, double-click the item or drag it to the design surface.</span></span> <span data-ttu-id="dc548-114">その後、オブジェクト ハンドルを使用して、形およびサイズを変更できます。</span><span class="sxs-lookup"><span data-stu-id="dc548-114">You can then change the shape and size by using the object handles.</span></span>  
  
## <a name="report-data-pane"></a><span data-ttu-id="dc548-115">レポート データ ペイン</span><span class="sxs-lookup"><span data-stu-id="dc548-115">Report Data Pane</span></span>  
 <span data-ttu-id="dc548-116">[レポート データ] ペインを表示するには、 **[表示]** メニューの **[レポート データ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dc548-116">To view the Report Data pane, on the **View** menu, click **Report Data**.</span></span> <span data-ttu-id="dc548-117">このペインを使用すると、パラメーター、画像、データ ソース、およびデータセットを定義したり、ReportName などの組み込みフィールドを参照したりできます。</span><span class="sxs-lookup"><span data-stu-id="dc548-117">Use this pane to define parameters, images, data sources, and datasets, and to reference built-in fields such as ReportName.</span></span> <span data-ttu-id="dc548-118">新しいアイテムを追加するには、 **[新規]** メニューをクリックし、アイテムを選択します。</span><span class="sxs-lookup"><span data-stu-id="dc548-118">To add a new item, click the **New** menu and select an item.</span></span> <span data-ttu-id="dc548-119">既存のデータセットに計算フィールドを追加するには、 **[データセット]** をクリックし、 **[データセットのプロパティ]** ダイアログ ボックスの **[フィールド]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="dc548-119">To add calculated fields to an existing dataset, click **Dataset**, and in the **Dataset Properties** dialog box, select **Fields**.</span></span> <span data-ttu-id="dc548-120">アイテムを選択し、 **[編集]** をクリックして **[プロパティ]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="dc548-120">Select an item and click **Edit** to open the **Properties** dialog box.</span></span> <span data-ttu-id="dc548-121">また、[レポート データ] ペインでアイテムを右クリックして、アイテムを追加したりそのプロパティを変更したりすることもできます。</span><span class="sxs-lookup"><span data-stu-id="dc548-121">You can also right-click items in the Report Data pane to add items or update their properties.</span></span>  
  
 <span data-ttu-id="dc548-122">[レポート データ] ペインから、デザイン画面上のデータ領域やテキスト ボックスにアイテムをドラッグして、レポートにデータや画像を追加します。</span><span class="sxs-lookup"><span data-stu-id="dc548-122">Drag items from the Report Data pane to data regions and text boxes on the design surface to add data and images to a report.</span></span>  
  
 <span data-ttu-id="dc548-123">詳しくは、「 [Report Data Pane](../report-data/report-data-pane.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="dc548-123">For more information, see [Report Data Pane](../report-data/report-data-pane.md).</span></span>  
  
## <a name="grouping-pane"></a><span data-ttu-id="dc548-124">グループ化ペイン</span><span class="sxs-lookup"><span data-stu-id="dc548-124">Grouping Pane</span></span>  
 <span data-ttu-id="dc548-125">グループは、レポート データを整理して階層構造で表示したり、合計を計算したりする際に使用します。</span><span class="sxs-lookup"><span data-stu-id="dc548-125">Groups are used to organize your report data into a visual hierarchy and to calculate totals.</span></span> <span data-ttu-id="dc548-126">[グループ化] ペインを使用すると、テーブル、マトリックス、または一覧のデータ領域に対して定義されたグループを表示できます。</span><span class="sxs-lookup"><span data-stu-id="dc548-126">Use the Grouping pane to view the groups defined for a table, matrix, or list data region.</span></span> <span data-ttu-id="dc548-127">[グループ化] ペインには、既定で、選択したデータ領域のすべてのグループが、フラットな一覧として表示されます。</span><span class="sxs-lookup"><span data-stu-id="dc548-127">By default, the Grouping pane displays all the groups for the selected data region as a flattened list.</span></span> <span data-ttu-id="dc548-128">グラフおよびゲージのデータ領域では、[グループ化] ペインは無効になっています。</span><span class="sxs-lookup"><span data-stu-id="dc548-128">The Grouping pane is disabled for Chart and Gauge data regions.</span></span>  
  
 <span data-ttu-id="dc548-129">グループの相互関係を確認するには、[グループ化] ペインを詳細設定モードに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="dc548-129">To see the groups in relationship to one another, toggle the Grouping pane to Advanced mode.</span></span> <span data-ttu-id="dc548-130">このモードでは、グループ メンバーの階層が表示されます (各グループに対応するデータ領域のセルが視覚的に表示されます)。</span><span class="sxs-lookup"><span data-stu-id="dc548-130">This mode displays the hierarchy of group members, a visual display of cells in the data region that correspond to each group.</span></span>  
  
 <span data-ttu-id="dc548-131">詳細については、「 [グループ化ペイン](grouping-pane.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dc548-131">For more information, see [Grouping Pane](grouping-pane.md).</span></span>  
  
## <a name="page-header-and-page-footer"></a><span data-ttu-id="dc548-132">ページ ヘッダーおよびページ フッター</span><span class="sxs-lookup"><span data-stu-id="dc548-132">Page Header and Page Footer</span></span>  
 <span data-ttu-id="dc548-133">ページ ヘッダーおよびページ フッターはそれぞれ、各ページの上部と下部に配置されます。</span><span class="sxs-lookup"><span data-stu-id="dc548-133">A page header and page footer run along the top and bottom of each page, respectively.</span></span> <span data-ttu-id="dc548-134">ヘッダーおよびフッターには、静的なテキスト、画像、線、四角形、罫線、背景色、および背景画像を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="dc548-134">Headers and footers can contain static text, images, lines, rectangles, borders, background color, and background images.</span></span> <span data-ttu-id="dc548-135">ヘッダーまたはフッターにレポート アイテムを追加するには、デザイン画面を右クリックして、[ヘッダー] または [フッター] を選択します。</span><span class="sxs-lookup"><span data-stu-id="dc548-135">To add report items to the header or footer, right-click the design surface and select Header or Footer.</span></span> <span data-ttu-id="dc548-136">ヘッダー セクションとフッター セクションがデザイン画面に表示されます。</span><span class="sxs-lookup"><span data-stu-id="dc548-136">Header and footer sections appear on the design surface.</span></span>  
  
## <a name="properties-pane"></a><span data-ttu-id="dc548-137">[プロパティ] ペイン</span><span class="sxs-lookup"><span data-stu-id="dc548-137">Properties Pane</span></span>  
 <span data-ttu-id="dc548-138">[プロパティ] ペインを使用すると、デザイン画面で現在選択されているレポート アイテムのプロパティや、[グループ化] ペインで現在選択されているグループのプロパティを表示できます。</span><span class="sxs-lookup"><span data-stu-id="dc548-138">Use the Properties pane to view properties for the currently selected report item on the design surface or the currently selected group in the Grouping pane.</span></span> <span data-ttu-id="dc548-139">別の方法として、選択したレポート アイテムまたはグループを右クリックし、 **[プロパティ]** をクリックして、そのレポート アイテムまたはグループに対応する **[プロパティ]** ダイアログ ボックスを開くこともできます。</span><span class="sxs-lookup"><span data-stu-id="dc548-139">Alternatively, you can right-click on a selected report item or group and then click **Properties** to open the corresponding **Properties** dialog box for the report item or group.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc548-140">参照</span><span class="sxs-lookup"><span data-stu-id="dc548-140">See Also</span></span>  
 <span data-ttu-id="dc548-141">[ページヘッダーとページフッター &#40;レポートビルダーと SSRS&#41;](../report-design/page-headers-and-footers-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="dc548-141">[Page Headers and Footers &#40;Report Builder and SSRS&#41;](../report-design/page-headers-and-footers-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="dc548-142">レポート デザインに関するヒント &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="dc548-142">Report Design Tips &#40;Report Builder and SSRS&#41;</span></span>](../report-design/report-design-tips-report-builder-and-ssrs.md)  
  
  
