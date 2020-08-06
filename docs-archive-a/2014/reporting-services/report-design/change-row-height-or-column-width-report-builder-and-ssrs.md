---
title: 行の高さまたは列の幅の変更 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: f061c204-5cd5-4467-9a9c-8a12803d93ba
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b5d75a8101d07d7d6e81c624d08cd951277936eb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643177"
---
# <a name="change-row-height-or-column-width-report-builder-and-ssrs"></a><span data-ttu-id="7ed61-102">行の高さまたは列の幅の変更 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="7ed61-102">Change Row Height or Column Width (Report Builder and SSRS)</span></span>
  <span data-ttu-id="7ed61-103">行の高さを設定することは、表示されるレポートの行の最大の高さを指定することです。</span><span class="sxs-lookup"><span data-stu-id="7ed61-103">When you set a row height, you are specifying the maximum height for the row in the rendered report.</span></span> <span data-ttu-id="7ed61-104">ただし、既定では、行のテキスト ボックスは実行時に格納するデータに合わせて縦方向に拡張されるように設定されているので、行の高さが指定した高さを超える場合があります。</span><span class="sxs-lookup"><span data-stu-id="7ed61-104">However, by default, text boxes in the row are set to grow vertically to accommodate their data at run-time, and this can cause a row to expand beyond the height that you specify.</span></span> <span data-ttu-id="7ed61-105">行の高さを固定するには、行の高さが自動的に拡張されないようにテキスト ボックスのプロパティを変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7ed61-105">To set a fixed row height, you must change the text box properties so they do not automatically expand.</span></span>  
  
 <span data-ttu-id="7ed61-106">列の幅を設定することは、表示されるレポートの列の最大の幅を指定することです。</span><span class="sxs-lookup"><span data-stu-id="7ed61-106">When you set a column width, you are specifying the maximum width for the column in the rendered report.</span></span> <span data-ttu-id="7ed61-107">列の幅は、格納するテキストに合わせて自動的に調整されたりはしません。</span><span class="sxs-lookup"><span data-stu-id="7ed61-107">Columns do not automatically adjust horizontally to accommodate text.</span></span>  
  
 <span data-ttu-id="7ed61-108">行または列のセルに四角形領域またはデータ領域が含まれる場合、セルの最小の高さおよび幅は、セルに含まれるアイテムの高さおよび幅によって決定されます。</span><span class="sxs-lookup"><span data-stu-id="7ed61-108">If a cell in a row or column contains a rectangle or data region, the minimum height and width of the cell is determined by the height and width of the contained item.</span></span> <span data-ttu-id="7ed61-109">詳しくは、「[レンダリングの動作 &#40;レポート ビルダーおよび SSRS&#41;](rendering-behaviors-report-builder-and-ssrs.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="7ed61-109">For more information, see [Rendering Behaviors &#40;Report Builder  and SSRS&#41;](rendering-behaviors-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-change-row-height-by-moving-row-handles"></a><span data-ttu-id="7ed61-110">行ハンドルを移動して行の高さを変更するには</span><span class="sxs-lookup"><span data-stu-id="7ed61-110">To change row height by moving row handles</span></span>  
  
1.  <span data-ttu-id="7ed61-111">[デザイン] ビューで、Tablix データ領域の任意の場所をクリックして選択します。</span><span class="sxs-lookup"><span data-stu-id="7ed61-111">In Design view, click anywhere in the tablix data region to select it.</span></span> <span data-ttu-id="7ed61-112">Tablix データ領域の外側の境界線に灰色の行ハンドルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="7ed61-112">Gray row handles appear on the outside border of the tablix data region.</span></span>  
  
2.  <span data-ttu-id="7ed61-113">拡張する行ハンドルの端の上にマウス ポインターを移動します。</span><span class="sxs-lookup"><span data-stu-id="7ed61-113">Hover over the row handle edge that you want to expand.</span></span> <span data-ttu-id="7ed61-114">両方向矢印が表示されます。</span><span class="sxs-lookup"><span data-stu-id="7ed61-114">A double-headed arrow appears.</span></span>  
  
3.  <span data-ttu-id="7ed61-115">行の端をクリックしてつかみ、上または下に動かして行の高さを調整します。</span><span class="sxs-lookup"><span data-stu-id="7ed61-115">Click to grab the edge of the row and move it higher or lower to adjust the row height.</span></span>  
  
### <a name="to-change-row-height-by-setting-cell-properties"></a><span data-ttu-id="7ed61-116">セル プロパティを設定して行の高さを変更するには</span><span class="sxs-lookup"><span data-stu-id="7ed61-116">To change row height by setting cell properties</span></span>  
  
1.  <span data-ttu-id="7ed61-117">[デザイン] ビューで、テーブル行のセルをクリックします。</span><span class="sxs-lookup"><span data-stu-id="7ed61-117">In Design view, click a cell in the table row.</span></span>  
  
     <span data-ttu-id="7ed61-118">![テーブル内の選択されたセル](../media/table-selectcell.png "テーブル内の選択されたセル")</span><span class="sxs-lookup"><span data-stu-id="7ed61-118">![Selected Cell in a Table](../media/table-selectcell.png "Selected Cell in a Table")</span></span>  
  
2.  <span data-ttu-id="7ed61-119">表示された **[プロパティ]** ペインで **[高さ]** プロパティを変更し、 **[プロパティ]** ペインの外側の任意の場所をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7ed61-119">In the **Properties** pane that displays, modify the **Height** property, and then click anywhere outside the **Properties** pane.</span></span>  
  
     <span data-ttu-id="7ed61-120">![選択したテーブルのセルの [プロパティ] ペイン](../media/cell-propertiespane.png "選択したテーブルのセルの [プロパティ] ペイン")</span><span class="sxs-lookup"><span data-stu-id="7ed61-120">![Properties Pane for selected table cell](../media/cell-propertiespane.png "Properties Pane for selected table cell")</span></span>  
  
### <a name="to-prevent-a-row-from-automatically-expanding-vertically"></a><span data-ttu-id="7ed61-121">行の高さが自動的に拡張されないようにするには</span><span class="sxs-lookup"><span data-stu-id="7ed61-121">To prevent a row from automatically expanding vertically</span></span>  
  
1.  <span data-ttu-id="7ed61-122">[デザイン] ビューで、Tablix データ領域の任意の場所をクリックして選択します。</span><span class="sxs-lookup"><span data-stu-id="7ed61-122">In Design view, click anywhere in the tablix data region to select it.</span></span> <span data-ttu-id="7ed61-123">Tablix データ領域の外側の境界線に灰色の行ハンドルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="7ed61-123">Gray row handles appear on the outside border of the tablix data region.</span></span>  
  
2.  <span data-ttu-id="7ed61-124">行ハンドルをクリックして行を選択します。</span><span class="sxs-lookup"><span data-stu-id="7ed61-124">Click the row handle to select the row.</span></span>  
  
3.  <span data-ttu-id="7ed61-125">プロパティ ペインで、CanGrow を **False**に設定します。</span><span class="sxs-lookup"><span data-stu-id="7ed61-125">In the Properties pane, set CanGrow to **False**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="7ed61-126">プロパティ ペインが表示されない場合は、 **[表示]** メニューの **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7ed61-126">If you cannot see the Properties pane, from the **View** menu, click **Properties**.</span></span>  
  
### <a name="to-change-column-width"></a><span data-ttu-id="7ed61-127">列の幅を変更するには</span><span class="sxs-lookup"><span data-stu-id="7ed61-127">To change column width</span></span>  
  
1.  <span data-ttu-id="7ed61-128">[デザイン] ビューで、Tablix データ領域の任意の場所をクリックして選択します。</span><span class="sxs-lookup"><span data-stu-id="7ed61-128">In Design view, click anywhere in the tablix data region to select it.</span></span> <span data-ttu-id="7ed61-129">Tablix データ領域の外側の境界線に灰色の列ハンドルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="7ed61-129">Gray column handles appear on the outside border of the tablix data region.</span></span>  
  
2.  <span data-ttu-id="7ed61-130">拡張する列ハンドルの端の上にマウス ポインターを移動します。</span><span class="sxs-lookup"><span data-stu-id="7ed61-130">Hover over the column handle edge that you want to expand.</span></span> <span data-ttu-id="7ed61-131">両方向矢印が表示されます。</span><span class="sxs-lookup"><span data-stu-id="7ed61-131">A double-headed arrow appears.</span></span>  
  
3.  <span data-ttu-id="7ed61-132">列の端をクリックしてつかみ、左または右に動かして列の幅を調整します。</span><span class="sxs-lookup"><span data-stu-id="7ed61-132">Click to grab the edge of the column and move it left or right to adjust the column width.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ed61-133">参照</span><span class="sxs-lookup"><span data-stu-id="7ed61-133">See Also</span></span>  
 <span data-ttu-id="7ed61-134">[Tablix データ領域 &#40;レポートビルダーと SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="7ed61-134">[Tablix Data Region &#40;Report Builder and SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="7ed61-135">[Tablix データ領域のセル、行、および列 &#40;レポートビルダー&#41; および SSRS](tablix-data-region-cells-rows-and-columns-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="7ed61-135">[Tablix Data Region Cells, Rows, and Columns &#40;Report Builder&#41; and SSRS](tablix-data-region-cells-rows-and-columns-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="7ed61-136">[テーブル &#40;レポートビルダーと SSRS&#41;](tables-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="7ed61-136">[Tables &#40;Report Builder  and SSRS&#41;](tables-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="7ed61-137">[マトリックス &#40;レポートビルダーと SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="7ed61-137">[Matrices &#40;Report Builder and SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="7ed61-138">[&#40;レポートビルダーと SSRS の一覧を表示&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="7ed61-138">[Lists &#40;Report Builder and SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="7ed61-139">テーブル、マトリックス、および一覧 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="7ed61-139">Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;</span></span>](tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
