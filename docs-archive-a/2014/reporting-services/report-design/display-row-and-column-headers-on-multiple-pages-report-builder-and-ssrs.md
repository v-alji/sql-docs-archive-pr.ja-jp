---
title: 複数のページへの行および列ヘッダーの表示 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 2422b1e2-822f-4379-9d7f-9afebb350e3f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2e3b38aa0faab267a0cd71feafe600829237b55c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87721171"
---
# <a name="display-row-and-column-headers-on-multiple-pages-report-builder-and-ssrs"></a><span data-ttu-id="a2d12-102">複数のページへの行および列ヘッダーの表示 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="a2d12-102">Display Row and Column Headers on Multiple Pages (Report Builder and SSRS)</span></span>
  <span data-ttu-id="a2d12-103">Tablix データ領域が複数のページにわたる場合、各ページで行ヘッダーおよび列ヘッダーを繰り返すかどうかを制御できます。</span><span class="sxs-lookup"><span data-stu-id="a2d12-103">You can control whether to repeat row and column headers on every page for a tablix data region that spans multiple pages.</span></span> <span data-ttu-id="a2d12-104">Tablix データ領域は、テーブル、マトリックス、または一覧のいずれかです。</span><span class="sxs-lookup"><span data-stu-id="a2d12-104">A tablix data region can be a table, matrix, or list.</span></span>  
  
 <span data-ttu-id="a2d12-105">行および列を制御する方法は、Tablix データ領域にグループ ヘッダーがあるかどうかによって異なります。</span><span class="sxs-lookup"><span data-stu-id="a2d12-105">How you control the rows and columns depends on whether the tablix data region has group headers.</span></span> <span data-ttu-id="a2d12-106">グループ ヘッダーを含む Tablix データ領域内でクリックすると、次の図に示すように点線で Tablix 領域が示されます。</span><span class="sxs-lookup"><span data-stu-id="a2d12-106">When you click in a tablix data region that has group headers, a dotted line shows the tablix areas, as shown in the following figure:</span></span>  
  
 <span data-ttu-id="a2d12-107">![Tablix データ領域部分](../media/rs-tablixareas.gif "Tablix データ領域部分")</span><span class="sxs-lookup"><span data-stu-id="a2d12-107">![Tablix data region areas](../media/rs-tablixareas.gif "Tablix data region areas")</span></span>  
  
 <span data-ttu-id="a2d12-108">行グループ ヘッダーと列グループ ヘッダーは、テーブルまたはマトリックスの新規作成ウィザードかグラフの新規作成ウィザードでグループを追加するときに、フィールドをグループ化ペインに追加するか、コンテキスト メニューを使用すると、自動的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="a2d12-108">Row and column group headers are created automatically when you add groups by using the New Table or Matrix wizard or the New Chart wizard, by adding fields to the Grouping pane, or by using context menus.</span></span> <span data-ttu-id="a2d12-109">Tablix データ領域に Tablix 本体領域のみがあり、グループ ヘッダーがない場合、行および列は Tablix メンバーになります。</span><span class="sxs-lookup"><span data-stu-id="a2d12-109">If the tablix data region has only a tablix body area and no group headers, the rows and columns are tablix members.</span></span>  
  
 <span data-ttu-id="a2d12-110">静的メンバーの場合、上部にある隣接する行または横にある隣接する列を複数のページに表示できます。</span><span class="sxs-lookup"><span data-stu-id="a2d12-110">For static members, you can display the top adjacent rows or the side adjacent columns on multiple pages.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-display-row-headers-on-multiple-pages"></a><span data-ttu-id="a2d12-111">複数のページに行ヘッダーを表示するには</span><span class="sxs-lookup"><span data-stu-id="a2d12-111">To display row headers on multiple pages</span></span>  
  
1.  <span data-ttu-id="a2d12-112">Tablix データ領域の行、列、またはコーナー ハンドルを右クリックし、 **[Tablix のプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a2d12-112">Right-click the row, column, or corner handle of a tablix data region, and then click **Tablix Properties**.</span></span>  
  
2.  <span data-ttu-id="a2d12-113">**[行のヘッダー]** の **[すべてのページにヘッダー行を表示する]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="a2d12-113">In **Row Headers**, select **Repeat header rows on each page**.</span></span>  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### <a name="to-display-column-headers-on-multiple-pages"></a><span data-ttu-id="a2d12-114">複数のページに列ヘッダーを表示するには</span><span class="sxs-lookup"><span data-stu-id="a2d12-114">To display column headers on multiple pages</span></span>  
  
1.  <span data-ttu-id="a2d12-115">Tablix データ領域の行、列、またはコーナー ハンドルを右クリックし、 **[Tablix のプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a2d12-115">Right-click the row, column, or corner handle of a tablix data region, and then click **Tablix Properties**.</span></span>  
  
2.  <span data-ttu-id="a2d12-116">**[列のヘッダー]** の **[すべてのページにヘッダー列を表示する]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="a2d12-116">In **Column Headers**, select **Repeat header columns on each page**.</span></span>  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### <a name="to-display-a-static-tablix-member-row-or-column-on-multiple-pages"></a><span data-ttu-id="a2d12-117">複数のページに静的な Tablix メンバー (行または列) を表示するには</span><span class="sxs-lookup"><span data-stu-id="a2d12-117">To display a static tablix member (row or column) on multiple pages</span></span>  
  
1.  <span data-ttu-id="a2d12-118">デザイン画面で、Tablix データ領域の行ハンドルまたは列ハンドルをクリックして選択します。</span><span class="sxs-lookup"><span data-stu-id="a2d12-118">On the design surface, click the row or column handle of the tablix data region to select it.</span></span> <span data-ttu-id="a2d12-119">グループ化ペインに行グループと列グループが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a2d12-119">The Grouping pane displays the row and column groups.</span></span>  
  
2.  <span data-ttu-id="a2d12-120">グループ化ペインの右側にある下矢印をクリックし、 **[詳細設定モード]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a2d12-120">On the right side of the Grouping pane, click the down arrow, and then click **Advanced Mode**.</span></span> <span data-ttu-id="a2d12-121">行グループ ペインに、行グループ階層の静的メンバーおよび動的メンバーが階層的に表示され、列グループ ペインに、列グループ階層のメンバーが同様に表示されます。</span><span class="sxs-lookup"><span data-stu-id="a2d12-121">The Row Groups pane displays the hierarchical static and dynamic members for the row groups hierarchy and the Column groups pane shows a similar display for the column groups hierarchy.</span></span>  
  
3.  <span data-ttu-id="a2d12-122">スクロール中も表示したままにする静的メンバー (行または列) に対応する静的メンバーをクリックします。</span><span class="sxs-lookup"><span data-stu-id="a2d12-122">Click the static member that corresponds to the static member (row or column) that you want to remain visible while scrolling.</span></span> <span data-ttu-id="a2d12-123">プロパティ ペインに **[Tablix メンバー]** プロパティが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a2d12-123">The Properties pane displays the **Tablix Member** properties.</span></span>  
  
     <span data-ttu-id="a2d12-124">プロパティ ペインが表示されない場合は、レポート ビルダー ウィンドウの上部にある **[表示]** タブをクリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a2d12-124">If you don't see the Properties pane, click the **View** tab at the top of the Report Builder window and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="a2d12-125">プロパティ ペインで、 **RepeatOnNewPage** を True に設定します。</span><span class="sxs-lookup"><span data-stu-id="a2d12-125">In the Properties pane, set **RepeatOnNewPage** to True.</span></span>  
  
5.  <span data-ttu-id="a2d12-126">**KeepWithGroup** を After に設定します。</span><span class="sxs-lookup"><span data-stu-id="a2d12-126">Set **KeepWithGroup** to After.</span></span>  
  
6.  <span data-ttu-id="a2d12-127">繰り返し表示するすべての隣接するメンバーに対して、この手順を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="a2d12-127">Repeat this for as many adjacent members as you want to repeat.</span></span>  
  
7.  <span data-ttu-id="a2d12-128">レポートをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="a2d12-128">Preview the report.</span></span>  
  
 <span data-ttu-id="a2d12-129">Tablix データ領域が複数のページにわたるレポートで各ページを表示したときに、静的な Tablix メンバーが各ページに繰り返し表示されます。</span><span class="sxs-lookup"><span data-stu-id="a2d12-129">As you view each page of the report that the tablix data region spans, the static tablix members repeat on each page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2d12-130">参照</span><span class="sxs-lookup"><span data-stu-id="a2d12-130">See Also</span></span>  
 <span data-ttu-id="a2d12-131">[レポートの検索、表示、管理 (レポート ビルダーおよび SSRS)](../report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="a2d12-131">[Finding, Viewing, and Managing Reports &#40;Report Builder and SSRS &#41;](../report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="a2d12-132">[レポートのエクスポート &#40;レポートビルダーと SSRS&#41;](../report-builder/export-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="a2d12-132">[Exporting Reports &#40;Report Builder and SSRS&#41;](../report-builder/export-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="a2d12-133">[改ページ、見出し、列、および行の制御 (レポート ビルダーおよび SSRS)](controlling-page-breaks-headings-columns-and-rows-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="a2d12-133">[Controlling Page Breaks, Headings, Columns, and Rows &#40;Report Builder and SSRS&#41;](controlling-page-breaks-headings-columns-and-rows-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="a2d12-134">[グループ単位でのヘッダーとフッターの表示 &#40;レポート ビルダーおよび SSRS&#41;](display-headers-and-footers-with-a-group-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="a2d12-134">[Display Headers and Footers with a Group &#40;Report Builder and SSRS&#41;](display-headers-and-footers-with-a-group-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="a2d12-135">レポートのスクロール時にヘッダーを表示したままにする (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="a2d12-135">Keep Headers Visible When Scrolling Through a Report &#40;Report Builder and SSRS&#41;</span></span>](keep-headers-visible-when-scrolling-through-a-report-report-builder-and-ssrs.md)  
  
  
