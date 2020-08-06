---
title: '[フィルター] ページ (グラフのダイアログボックス) (レポートビルダーおよび SSRS) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.categorygroupproperties.filters.f1
- "10409"
- sql12.rtp.rptdesigner.seriesgroupproperties.filters.f1
- "10401"
- sql12.rtp.rptdesigner.chartproperties.filters.f1
- "10165"
ms.assetid: fab97b2f-d53f-42f2-900c-c159653d89ed
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 01d5054ce7d0c3e02d960885f149bd0ef209dc34
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716125"
---
# <a name="filters-page-chart-dialog-boxes-report-builder-and-ssrs"></a><span data-ttu-id="846df-102">[フィルター] ページ (グラフのダイアログ ボックス) (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="846df-102">Filters page, Chart Dialog Boxes (Report Builder and SSRS)</span></span>
  <span data-ttu-id="846df-103">で [**フィルター** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="846df-103">Click **Filters** in the:</span></span>  
  
-   <span data-ttu-id="846df-104">**[カテゴリ グループのプロパティ]** ダイアログ ボックス。カテゴリ別にグループ化された系列内のデータ ポイントをフィルターできます。</span><span class="sxs-lookup"><span data-stu-id="846df-104">**Category Group Properties** dialog box to filter data points in a series that has been grouped by category.</span></span>  
  
-   <span data-ttu-id="846df-105">**[グラフのプロパティ]** ダイアログ ボックス。グラフのフィルター処理オプションを定義できます。</span><span class="sxs-lookup"><span data-stu-id="846df-105">**Chart Properties** dialog box to define filtering options for the chart.</span></span>  
  
-   <span data-ttu-id="846df-106">**[系列グループのプロパティ]** ダイアログ ボックス。選択したグループの系列の数を制限できます。</span><span class="sxs-lookup"><span data-stu-id="846df-106">**Series Group Properties** dialog box to limit the number of series in the selected group.</span></span>  
  
## <a name="options"></a><span data-ttu-id="846df-107">Options</span><span class="sxs-lookup"><span data-stu-id="846df-107">Options</span></span>  
 <span data-ttu-id="846df-108">**追加**</span><span class="sxs-lookup"><span data-stu-id="846df-108">**Add**</span></span>  
 <span data-ttu-id="846df-109">クリックして、一覧に新しいフィルター句を追加します。</span><span class="sxs-lookup"><span data-stu-id="846df-109">Click to add a new filter clause to the list.</span></span>  
  
 <span data-ttu-id="846df-110">**削除**</span><span class="sxs-lookup"><span data-stu-id="846df-110">**Delete**</span></span>  
 <span data-ttu-id="846df-111">選択したフィルター句を一覧から削除します。</span><span class="sxs-lookup"><span data-stu-id="846df-111">Click to delete the selected filter clause from the list.</span></span>  
  
 <span data-ttu-id="846df-112">**上矢印**</span><span class="sxs-lookup"><span data-stu-id="846df-112">**Up arrow**</span></span>  
 <span data-ttu-id="846df-113">クリックして、選択したフィルターを一覧内で上に移動します。</span><span class="sxs-lookup"><span data-stu-id="846df-113">Click to move the selected filter up in the list.</span></span>  
  
 <span data-ttu-id="846df-114">**下方向キー**</span><span class="sxs-lookup"><span data-stu-id="846df-114">**Down arrow**</span></span>  
 <span data-ttu-id="846df-115">クリックして、選択したフィルターを一覧内で下に移動します。</span><span class="sxs-lookup"><span data-stu-id="846df-115">Click to move the selected filter down in the list.</span></span>  
  
 <span data-ttu-id="846df-116">**[式]**</span><span class="sxs-lookup"><span data-stu-id="846df-116">**Expression**</span></span>  
 <span data-ttu-id="846df-117">フィルターを適用する式を入力または選択します。</span><span class="sxs-lookup"><span data-stu-id="846df-117">Type or choose the expression to which you want to apply a filter.</span></span> <span data-ttu-id="846df-118">式を編集するには、式 ([**fx**]) ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="846df-118">Click the Expression (**fx**) button to edit the expression.</span></span>  
  
 <span data-ttu-id="846df-119">**データの種類**</span><span class="sxs-lookup"><span data-stu-id="846df-119">**Data type**</span></span>  
 <span data-ttu-id="846df-120">**[値]** のデータ型を選択します。</span><span class="sxs-lookup"><span data-stu-id="846df-120">Choose the data type for **Value**.</span></span> <span data-ttu-id="846df-121">可能であれば、 **[式]** のデータ型と一致するデータ型を選択します。</span><span class="sxs-lookup"><span data-stu-id="846df-121">When possible, choose a data type that matches the data type for **Expression**.</span></span>  
  
 <span data-ttu-id="846df-122">**[式]** および **[値]** の値は、同じデータ型に評価される必要があります。</span><span class="sxs-lookup"><span data-stu-id="846df-122">The values in **Expression** and **Value** must evaluate to the same data type.</span></span> <span data-ttu-id="846df-123">たとえば、 **[式]** が System.Int32 データ型のフィールドに設定され、 **[値]** が 7 に設定されている場合、ドロップダウン リストから **Integer**を選択します。</span><span class="sxs-lookup"><span data-stu-id="846df-123">For example, if **Expression** is set to a field that has the data type System.Int32 and **Value** is set to 7, from the drop-down list, choose **Integer**.</span></span>  
  
 <span data-ttu-id="846df-124">必要なデータ型のオプションがドロップダウン リストにない場合は、値を正しいデータ型に変換する式を作成します。</span><span class="sxs-lookup"><span data-stu-id="846df-124">If the data type option you need is not in the drop-down list, write an expression to convert the value to the correct data type.</span></span> <span data-ttu-id="846df-125">詳細については、「[フィルター式の例 &#40;レポート ビルダーおよび SSRS&#41;](report-design/filter-equation-examples-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="846df-125">For more information, see [Filter Equation Examples &#40;Report Builder and SSRS&#41;](report-design/filter-equation-examples-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="846df-126">**[オペレーター]**</span><span class="sxs-lookup"><span data-stu-id="846df-126">**Operator**</span></span>  
 <span data-ttu-id="846df-127">式と値の比較に使用する演算子を選択します。</span><span class="sxs-lookup"><span data-stu-id="846df-127">Choose the operator to use to compare the expression and the value.</span></span>  
  
 <span data-ttu-id="846df-128">**Value**</span><span class="sxs-lookup"><span data-stu-id="846df-128">**Value**</span></span>  
 <span data-ttu-id="846df-129">**[式]** で指定した式の評価対象となる式または値を入力します。</span><span class="sxs-lookup"><span data-stu-id="846df-129">Type the expression or value against which to evaluate the expression in **Expression**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="846df-130">参照</span><span class="sxs-lookup"><span data-stu-id="846df-130">See Also</span></span>  
 <span data-ttu-id="846df-131">[データセットフィルター、データ領域フィルター、およびグループフィルターを追加 &#40;レポートビルダーと SSRS&#41;](report-design/add-dataset-filters-data-region-filters-and-group-filters.md) </span><span class="sxs-lookup"><span data-stu-id="846df-131">[Add Dataset Filters, Data Region Filters, and Group Filters &#40;Report Builder and SSRS&#41;](report-design/add-dataset-filters-data-region-filters-and-group-filters.md) </span></span>  
 <span data-ttu-id="846df-132">[式の例 (レポート ビルダーおよび SSRS)](report-design/expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="846df-132">[Expression Examples &#40;Report Builder and SSRS&#41;](report-design/expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="846df-133">[式 &#40;レポート ビルダーおよび SSRS&#41;](report-design/expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="846df-133">[Expressions &#40;Report Builder and SSRS&#41;](report-design/expressions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="846df-134">データのフィルター、グループ化、および並べ替え &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="846df-134">Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;</span></span>](report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)  
  
  
