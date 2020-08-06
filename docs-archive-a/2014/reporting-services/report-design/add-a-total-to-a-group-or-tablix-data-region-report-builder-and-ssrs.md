---
title: グループまたは Tablix データ領域への合計の追加 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: cf1b96c3-7f0f-4c94-ad08-5239c77ccfe4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f626621a37a327ae32664ab9444e72ce4931ac0e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631547"
---
# <a name="add-a-total-to-a-group-or-tablix-data-region-report-builder-and-ssrs"></a><span data-ttu-id="8cadc-102">グループまたは Tablix データ領域への合計の追加 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="8cadc-102">Add a Total to a Group or Tablix Data Region (Report Builder and SSRS)</span></span>
  <span data-ttu-id="8cadc-103">グループまたはデータ領域全体の Tablix データ領域に合計を追加できます。</span><span class="sxs-lookup"><span data-stu-id="8cadc-103">You can add totals in a tablix data region for a group or for the entire data region.</span></span> <span data-ttu-id="8cadc-104">既定では、合計は、フィルターを適用した後のグループまたはデータ領域内の NULL 以外の数値データの合計です。</span><span class="sxs-lookup"><span data-stu-id="8cadc-104">By default, a total is the sum of the numeric, non-null data in a group or in the data region, after filters are applied.</span></span> <span data-ttu-id="8cadc-105">グループに合計を追加するには、グループ化ペインでグループのショートカット メニューの **[合計の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8cadc-105">To add totals for a group, click **Add Total** on the shortcut menu for the group in the Grouping pane.</span></span> <span data-ttu-id="8cadc-106">Tablix 本体領域の個々のセルの合計を追加するには、セルのショートカット メニューの **[合計の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8cadc-106">To add totals for an individual cell in the tablix body area, click **Add Total** on the shortcut menu for the cell.</span></span> <span data-ttu-id="8cadc-107">**[合計の追加]** は状況依存のコマンドで、数値フィールドでのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="8cadc-107">The **Add Total** command is context-sensitive and enabled only for numeric fields.</span></span> <span data-ttu-id="8cadc-108">選択した Tablix セルに応じて、Tablix 本体領域のセルを選択して 1 つのセルの合計を追加することも、Tablix 行グループ領域または Tablix 列グループ領域のセルを選択してグループ全体の合計を追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="8cadc-108">Depending on the tablix cell that you select, you can add a total for a single cell by selecting a cell in the tablix body area or for the entire group by selecting a cell in the tablix row group area or the tablix column group area.</span></span> <span data-ttu-id="8cadc-109">Tablix 領域の詳細については、「 [Tablix データ領域 &#40;レポート ビルダーおよび SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8cadc-109">For more information about tablix areas, see [Tablix Data Region &#40;Report Builder and SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="8cadc-110">合計を追加した後、既定の関数 Sum を組み込みのレポート関数の一覧に含まれる別の集計関数に変更できます。</span><span class="sxs-lookup"><span data-stu-id="8cadc-110">After you add a total, you can change the default function Sum to a different aggregate function from the list of built-in report functions.</span></span> <span data-ttu-id="8cadc-111">詳細については、「[集計関数リファレンス &#40;レポートビルダーと SSRS&#41;](report-builder-functions-aggregate-functions-reference.md)」を参照してください。[!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8cadc-111">For more information, see [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md).[!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]</span></span>  
  
### <a name="to-add-a-total-for-an-individual-value-in-the-tablix-body-area"></a><span data-ttu-id="8cadc-112">Tablix 本体領域の個々の値の合計を追加するには</span><span class="sxs-lookup"><span data-stu-id="8cadc-112">To add a total for an individual value in the tablix body area</span></span>  
  
-   <span data-ttu-id="8cadc-113">Tablix データ領域の本体領域で、合計を追加するセルを右クリックします。</span><span class="sxs-lookup"><span data-stu-id="8cadc-113">In the tablix data region body area, right-click the cell where you want to add the total.</span></span> <span data-ttu-id="8cadc-114">そのセルには数値フィールドが含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="8cadc-114">The cell must contain a numeric field.</span></span> <span data-ttu-id="8cadc-115">**[合計の追加]** をポイントして **[行]** または **[列]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8cadc-115">Point to **Add Total**, and then click **Row** or **Column**.</span></span>  
  
     <span data-ttu-id="8cadc-116">現在のグループの外側の新しい行または列がデータ領域に追加され、クリックしたセルのフィールドの既定の合計が表示されます。</span><span class="sxs-lookup"><span data-stu-id="8cadc-116">A new row or column outside the current group is added to the data region, with a default total for the field in the cell you clicked.</span></span>  
  
     <span data-ttu-id="8cadc-117">Tablix データ領域がテーブルの場合は、行が自動的に追加されます。</span><span class="sxs-lookup"><span data-stu-id="8cadc-117">If the tablix data region is a table, a row is automatically added.</span></span>  
  
### <a name="to-add-totals-for-a-row-group"></a><span data-ttu-id="8cadc-118">行グループの合計を追加するには</span><span class="sxs-lookup"><span data-stu-id="8cadc-118">To add totals for a row group</span></span>  
  
-   <span data-ttu-id="8cadc-119">Tablix データ領域の行グループ領域で、合計する行グループ領域内のセルを右クリックし、 **[合計の追加]** をポイントして **[前]** または **[後]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8cadc-119">In the tablix data region row group area, right-click a cell in the row group area for which you want totals, point to **Add Total**, and then click **Before** or **After**.</span></span>  
  
     <span data-ttu-id="8cadc-120">現在のグループの外側の新しい行がデータ領域に追加され、行の各数値フィールドの既定の合計が追加されます。</span><span class="sxs-lookup"><span data-stu-id="8cadc-120">A new row outside the current group is added to the data region, and then a default total is added for each numeric field in the row.</span></span>  
  
### <a name="to-add-totals-for-a-column-group"></a><span data-ttu-id="8cadc-121">列グループの合計を追加するには</span><span class="sxs-lookup"><span data-stu-id="8cadc-121">To add totals for a column group</span></span>  
  
-   <span data-ttu-id="8cadc-122">Tablix データ領域の行グループ領域で、合計する列グループ領域内のセルを右クリックし、 **[合計の追加]** をポイントして **[前]** または **[後]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8cadc-122">In the tablix data region row group area, right-click a cell in the column group area for which you want totals, then point to **Add Total**, and click **Before** or **After**.</span></span>  
  
     <span data-ttu-id="8cadc-123">現在のグループの外側の新しい列がデータ領域に追加され、列の各数値フィールドの既定の合計が追加されます。</span><span class="sxs-lookup"><span data-stu-id="8cadc-123">A new column outside the current group is added to the data region, and then a default total is added for each numeric field in the column.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8cadc-124">参照</span><span class="sxs-lookup"><span data-stu-id="8cadc-124">See Also</span></span>  
 <span data-ttu-id="8cadc-125">[合計、集計、および組み込みコレクションの式のスコープ &#40;レポートビルダーと SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md) </span><span class="sxs-lookup"><span data-stu-id="8cadc-125">[Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md) </span></span>  
 <span data-ttu-id="8cadc-126">[Tablix データ領域 &#40;レポートビルダーと SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="8cadc-126">[Tablix Data Region &#40;Report Builder and SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="8cadc-127">[テーブル &#40;レポートビルダーと SSRS&#41;](tables-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="8cadc-127">[Tables &#40;Report Builder  and SSRS&#41;](tables-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="8cadc-128">[マトリックス &#40;レポートビルダーと SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="8cadc-128">[Matrices &#40;Report Builder and SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="8cadc-129">[&#40;レポートビルダーと SSRS の一覧を表示&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="8cadc-129">[Lists &#40;Report Builder and SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="8cadc-130">テーブル、マトリックス、および一覧 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="8cadc-130">Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;</span></span>](tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
