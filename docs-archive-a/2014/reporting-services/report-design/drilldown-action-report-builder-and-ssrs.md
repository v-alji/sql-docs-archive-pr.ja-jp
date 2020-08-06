---
title: ドリルダウン アクション (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10249"
- "10186"
- sql12.rtp.rptdesigner.calculatedseriesproperties.visibility.f1
- sql12.rtp.rptdesigner.seriesproperties.visibility.f1
- sql12.rtp.rptdesigner.chartareaproperties.visibility.f1
- "10092"
- sql12.rtp.rptdesigner.textboxproperties.visibility.f1
- sql12.rtp.rptdesigner.charttitleproperties.visibility.f1
- "10167"
- sql12.rtp.rptdesigner.rectangleproperties.visibility.f1
- "10174"
- sql12.rtp.rptdesigner.majorgridlineproperties.visibility.f1
- "10155"
- "10123"
- sql12.rtp.rptdesigner.subreportproperties.visibility.f1
- "10425"
- sql12.rtp.rptdesigner.minorgridlineproperties.visibility.f1
- "10217"
- sql12.rtp.rptdesigner.axisproperties.visibility.f1
- sql12.rtp.rptdesigner.serieslabelproperties.visibility.f1
- "10161"
- sql12.rtp.rptdesigner.chartproperties.visibility.f1
- sql12.rtp.rptdesigner.legendproperties.visibility.f1
- sql12.rtp.rptdesigner.pictureproperties.visibility.f1
- "10215"
- "10258"
- "10144"
- "10062"
- "10053"
ms.assetid: 1f8d1ef2-0daf-40c6-9ba7-3b391249bcd4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2fe3d55dc70a606df759c049b7b147820f0e3110
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644319"
---
# <a name="drilldown-action-report-builder-and-ssrs"></a><span data-ttu-id="1e9bb-102">ドリルダウン アクション (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="1e9bb-102">Drilldown Action (Report Builder and SSRS)</span></span>
  <span data-ttu-id="1e9bb-103">テキスト ボックスに正符号と負符号のアイコンを組み込むことによって、アイテムの表示/非表示をユーザーが対話的に切り替えられるように設定できます。</span><span class="sxs-lookup"><span data-stu-id="1e9bb-103">B providing plus and minus icons on a text box, you can enable users to hide and display items interactively.</span></span> <span data-ttu-id="1e9bb-104">これを *ドリルダウン* アクションと呼びます。</span><span class="sxs-lookup"><span data-stu-id="1e9bb-104">This is called a *drilldown* action.</span></span> <span data-ttu-id="1e9bb-105">テーブルまたはマトリックスの場合、静的な行や列、またはグループに関連付けられている行や列の表示と非表示を切り替えることができます。</span><span class="sxs-lookup"><span data-stu-id="1e9bb-105">For a table or matrix, you can show or hide static rows and columns, or rows and columns that are associated with groups.</span></span>  
  
 <span data-ttu-id="1e9bb-106">![rs_drilldown](../media/rs-drilldown.gif "rs_drilldown")</span><span class="sxs-lookup"><span data-stu-id="1e9bb-106">![rs_drilldown](../media/rs-drilldown.gif "rs_drilldown")</span></span>  
  
 <span data-ttu-id="1e9bb-107">この図では、レポートの正符号 (+) をクリックして詳細データを表示しています。</span><span class="sxs-lookup"><span data-stu-id="1e9bb-107">In this illustration, the user clicks the plus signs (+) in the report to show detail data.</span></span>  
  
 <span data-ttu-id="1e9bb-108">たとえば、行グループのあるテーブルの場合、外側のグループの概要行を除いて、最初にすべての行を非表示にすることができます。</span><span class="sxs-lookup"><span data-stu-id="1e9bb-108">For example, you can initially hide all the rows except the outer group summary row for a table with row groups.</span></span> <span data-ttu-id="1e9bb-109">それぞれの内部グループ (詳細グループを含む) に対して、グループ化セルの展開/折りたたみを切り替えるアイコンを対象グループに追加します。</span><span class="sxs-lookup"><span data-stu-id="1e9bb-109">For each inner group (including the details group), add an expand/collapse icon to the grouping cell of the containing group.</span></span> <span data-ttu-id="1e9bb-110">レポートが表示されると、ユーザーはこのテキスト ボックスをクリックして、詳細データを展開したり折りたたんだりすることができます。</span><span class="sxs-lookup"><span data-stu-id="1e9bb-110">When the report is rendered, the user can click the text box to expand and collapse the detail data.</span></span> <span data-ttu-id="1e9bb-111">詳細については、「[テーブル &#40;レポート ビルダーおよび SSRS& #41;](tables-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1e9bb-111">For more information, see [Tables &#40;Report Builder  and SSRS&#41;](tables-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="1e9bb-112">アイテムの展開と折りたたみをユーザーが行うようにするには、アイテムの表示プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="1e9bb-112">To allow users to expand or collapse an item, you set the visibility properties for that item.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1e9bb-113">ドリルダウン アクションを使用してレポートを作成する場合は、非表示にする行や列内の単一のテキスト ボックスではなく、非表示にするグループ、列、または行に、表示情報を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1e9bb-113">When you create a report with a drilldown action, the visibility information must be set on the group, column, or row that you want to hide, not just a single text box in the row or column.</span></span> <span data-ttu-id="1e9bb-114">さらに、トグル ボタンに使用するテキスト ボックスが、表示と非表示を切り替えるアイテムを制御するコンテナー スコープの範囲内にある必要があります。</span><span class="sxs-lookup"><span data-stu-id="1e9bb-114">In addition, the text box that you use for the toggle must be in a containing scope that controls the item that you want to show or hide.</span></span>  
>   
>  <span data-ttu-id="1e9bb-115">たとえば、入れ子構造のグループに関連付けられている行を非表示にするには、テキスト ボックスが、親グループに関連付けられている行にあるか、包含階層の上位にある必要があります。</span><span class="sxs-lookup"><span data-stu-id="1e9bb-115">For example, to hide a row associated with a nested group, the text box must be in a row associated with the parent group or higher in the containment hierarchy.</span></span>  
>   
>  <span data-ttu-id="1e9bb-116">グループ、列、または行の可視化の設定については、「[アイテムへの展開または折りたたみアクションの追加 &#40;レポート ビルダーおよび SSRS&#41;](add-an-expand-or-collapse-action-to-an-item-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1e9bb-116">For information on setting visibility information on the group, column or row, see [Add an Expand or Collapse Action to an Item &#40;Report Builder and SSRS&#41;](add-an-expand-or-collapse-action-to-an-item-report-builder-and-ssrs.md)</span></span>  
  
 <span data-ttu-id="1e9bb-117">レポート アイテムを非表示にする方法については、「[アイテムを非表示にする &#40;レポート ビルダーおよび SSRS&#41;](../report-builder/hide-an-item-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1e9bb-117">For more information about hiding report items, see [Hide an Item &#40;Report Builder and SSRS&#41;](../report-builder/hide-an-item-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="comparing-drilldown-and-drillthrough-reports"></a><span data-ttu-id="1e9bb-118">ドリルダウン レポートと詳細レポートの比較</span><span class="sxs-lookup"><span data-stu-id="1e9bb-118">Comparing Drilldown and Drillthrough Reports</span></span>  
 <span data-ttu-id="1e9bb-119">ドリルダウン レポートでは、ユーザーが正符号または負符号のボタンをクリックすると、レポートのセクションが展開または折りたたまれ、詳細データがその場所に表示されます。</span><span class="sxs-lookup"><span data-stu-id="1e9bb-119">In a drilldown report, a user clicks a plus or minus button to expand or collapse a section of a report to show detail data in place.</span></span> <span data-ttu-id="1e9bb-120">詳細レポートでは、ユーザーが集計値のリンクをクリックすると、別の関連レポートが開き、詳細データが表示されます。</span><span class="sxs-lookup"><span data-stu-id="1e9bb-120">In a drillthrough report, the user clicks a link for a summary value, and this opens a separate, related report to show detail data.</span></span> <span data-ttu-id="1e9bb-121">詳細データは、詳細レポートの実行時にのみ取得されます。</span><span class="sxs-lookup"><span data-stu-id="1e9bb-121">The detail data is only retrieved when the detail report runs.</span></span> <span data-ttu-id="1e9bb-122">通常詳細レポートには、ドリルダウン レポートほどリソースが必要ありません。</span><span class="sxs-lookup"><span data-stu-id="1e9bb-122">Drillthrough reports typically require fewer resources than drilldown reports.</span></span> <span data-ttu-id="1e9bb-123">詳細については、「 [ドリルスルー、ドリルダウン、サブレポート、および入れ子になったデータ領域 (レポート ビルダーおよび SSRS)](drillthrough-drilldown-subreports-and-nested-data-regions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1e9bb-123">For more information, see [Drillthrough, Drilldown, Subreports, and Nested Data Regions &#40;Report Builder and SSRS&#41;](drillthrough-drilldown-subreports-and-nested-data-regions.md).</span></span>  
  
## <a name="rendering-extension-support-for-hidden-report-items"></a><span data-ttu-id="1e9bb-124">非表示レポート アイテムに対する表示拡張機能のサポート</span><span class="sxs-lookup"><span data-stu-id="1e9bb-124">Rendering Extension Support for Hidden Report Items</span></span>  
 <span data-ttu-id="1e9bb-125">レポート アイテムの表示と非表示の切り替えは、レポート ビルダーやレポート マネージャーでレポートを実行するときに使用する HTML 表示拡張機能など、ユーザー対話機能をサポートする表示拡張機能でのみサポートされます。</span><span class="sxs-lookup"><span data-stu-id="1e9bb-125">The show-and-hide toggle on report items is supported only by rendering extensions that support user interactivity, such as the HTML rendering extension that is used when you run a report in Report Builder and in Report Manager, for example.</span></span> <span data-ttu-id="1e9bb-126">一部の表示拡張機能では非表示アイテムが表示されます。</span><span class="sxs-lookup"><span data-stu-id="1e9bb-126">Other rendering extensions display hidden items.</span></span> <span data-ttu-id="1e9bb-127">条件に応じて表示/非表示を切り替えるレポート アイテムのサポートは、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="1e9bb-127">The following list describes support for report items with conditional visibility:</span></span>  
  
-   <span data-ttu-id="1e9bb-128">HTML では、非表示に設定されている場合、アイテムは HTML ソース内に表示されません。</span><span class="sxs-lookup"><span data-stu-id="1e9bb-128">In HTML, if items are hidden, they are not visible in the HTML source.</span></span>  
  
-   <span data-ttu-id="1e9bb-129">XML 表示拡張機能では、非表示に設定されているかどうかに関係なく、すべてのレポート アイテムが表示されます。</span><span class="sxs-lookup"><span data-stu-id="1e9bb-129">The XML rendering extension displays all report items, regardless of whether they are hidden.</span></span>  
  
-   <span data-ttu-id="1e9bb-130">Excel 表示拡張機能では、テーブル、マトリックス、または一覧の非表示の行および列が表示され展開されます。</span><span class="sxs-lookup"><span data-stu-id="1e9bb-130">The Excel rendering extension displays and expands hidden rows and columns for a table, matrix, or list.</span></span> <span data-ttu-id="1e9bb-131">行と列がすべて表示されます。</span><span class="sxs-lookup"><span data-stu-id="1e9bb-131">All rows and columns are visible.</span></span>  
  
 <span data-ttu-id="1e9bb-132">詳しくは、「[レンダリングの動作 &#40;レポート ビルダーおよび SSRS&#41;](rendering-behaviors-report-builder-and-ssrs.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="1e9bb-132">For more information, see [Rendering Behaviors &#40;Report Builder  and SSRS&#41;](rendering-behaviors-report-builder-and-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e9bb-133">参照</span><span class="sxs-lookup"><span data-stu-id="1e9bb-133">See Also</span></span>  
 <span data-ttu-id="1e9bb-134">[ドリルスルー、ドリルダウン、サブレポート、および入れ子になったデータ領域 (レポート ビルダーおよび SSRS)](drillthrough-drilldown-subreports-and-nested-data-regions.md) </span><span class="sxs-lookup"><span data-stu-id="1e9bb-134">[Drillthrough, Drilldown, Subreports, and Nested Data Regions &#40;Report Builder and SSRS&#41;](drillthrough-drilldown-subreports-and-nested-data-regions.md) </span></span>  
 <span data-ttu-id="1e9bb-135">[対話的な並べ替え、ドキュメント マップ、およびリンク &#40;レポート ビルダーおよび SSRS&#41;](interactive-sort-document-maps-and-links-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="1e9bb-135">[Interactive Sort, Document Maps, and Links &#40;Report Builder and SSRS&#41;](interactive-sort-document-maps-and-links-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="1e9bb-136">式の例 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="1e9bb-136">Expression Examples &#40;Report Builder and SSRS&#41;</span></span>](expression-examples-report-builder-and-ssrs.md)  
  
  
