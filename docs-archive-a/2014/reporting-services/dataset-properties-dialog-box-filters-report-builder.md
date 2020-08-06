---
title: '[フィルター] ([データセットのプロパティ] ダイアログボックス) (レポートビルダー) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10025"
ms.assetid: 933a6f44-4eb7-4e73-9c40-ac0fd17b23d3
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7bc13b0eeff1eaf27fb0ec0c4279ff00d0809e4d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632992"
---
# <a name="dataset-properties-dialog-box-filters-report-builder"></a><span data-ttu-id="db17c-102">[フィルター] ([データセットのプロパティ] ダイアログ ボックス) (レポート ビルダー)</span><span class="sxs-lookup"><span data-stu-id="db17c-102">Dataset Properties Dialog Box, Filters (Report Builder)</span></span>
  <span data-ttu-id="db17c-103">**[データセットのプロパティ]** ダイアログ ボックスの **[フィルター]** を選択すると、データセットに対するフィルターを作成できます。</span><span class="sxs-lookup"><span data-stu-id="db17c-103">Select **Filters** on the **Dataset Properties** dialog box to create filters for the dataset.</span></span>  
  
 <span data-ttu-id="db17c-104">レポート サーバー上の共有データセット定義の一部であるフィルターは、共有データセットを使用するすべてのレポートに影響を及ぼします。</span><span class="sxs-lookup"><span data-stu-id="db17c-104">Filters that are part of a shared dataset definition on the report server affect all reports that use the shared dataset.</span></span> <span data-ttu-id="db17c-105">共有データセットの追加フィルターは、レポートに追加してから指定できます。</span><span class="sxs-lookup"><span data-stu-id="db17c-105">Additional filters for the shared dataset can be specified after it is added to a report.</span></span> <span data-ttu-id="db17c-106">これらのフィルターは、フィルターが定義されているレポートのみに影響を及ぼします。</span><span class="sxs-lookup"><span data-stu-id="db17c-106">These filters affect only the report in which they are defined.</span></span>  
  
 <span data-ttu-id="db17c-107">埋め込みデータセットのフィルターは、フィルターが定義されているレポートのみに影響を及ぼします。</span><span class="sxs-lookup"><span data-stu-id="db17c-107">Filters for an embedded dataset affect only the report in which they are defined.</span></span>  
  
 <span data-ttu-id="db17c-108">詳細については、「 [データのフィルター、グループ化、および並べ替え (レポート ビルダーおよび SSRS)](report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="db17c-108">For more information, see [Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](report-design/filter-group-and-sort-data-report-builder-and-ssrs.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="db17c-109">Options</span><span class="sxs-lookup"><span data-stu-id="db17c-109">Options</span></span>  
 <span data-ttu-id="db17c-110">**追加**</span><span class="sxs-lookup"><span data-stu-id="db17c-110">**Add**</span></span>  
 <span data-ttu-id="db17c-111">一覧に新しいフィルター句を追加します。</span><span class="sxs-lookup"><span data-stu-id="db17c-111">Add a new filter clause to the list.</span></span>  
  
 <span data-ttu-id="db17c-112">**削除**</span><span class="sxs-lookup"><span data-stu-id="db17c-112">**Delete**</span></span>  
 <span data-ttu-id="db17c-113">選択したフィルター句を一覧から削除します。</span><span class="sxs-lookup"><span data-stu-id="db17c-113">Delete the selected filter clause from the list.</span></span>  
  
 <span data-ttu-id="db17c-114">**上矢印**</span><span class="sxs-lookup"><span data-stu-id="db17c-114">**Up arrow**</span></span>  
 <span data-ttu-id="db17c-115">選択したフィルターを一覧内で上に移動します。</span><span class="sxs-lookup"><span data-stu-id="db17c-115">Move the selected filter up in the list.</span></span>  
  
 <span data-ttu-id="db17c-116">**下方向キー**</span><span class="sxs-lookup"><span data-stu-id="db17c-116">**Down arrow**</span></span>  
 <span data-ttu-id="db17c-117">選択したフィルターを一覧内で下に移動します。</span><span class="sxs-lookup"><span data-stu-id="db17c-117">Move the selected filter down in the list</span></span>  
  
 <span data-ttu-id="db17c-118">**[式]**</span><span class="sxs-lookup"><span data-stu-id="db17c-118">**Expression**</span></span>  
 <span data-ttu-id="db17c-119">フィルターを適用する式を入力または選択します。</span><span class="sxs-lookup"><span data-stu-id="db17c-119">Type or choose the expression to which you want to apply a filter.</span></span> <span data-ttu-id="db17c-120">式を編集するには、式 ([**fx**]) ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="db17c-120">Click the Expression (**fx**) button to edit the expression.</span></span>  
  
 <span data-ttu-id="db17c-121">**データの種類**</span><span class="sxs-lookup"><span data-stu-id="db17c-121">**Data type**</span></span>  
 <span data-ttu-id="db17c-122">**[値]** のデータ型を選択します。</span><span class="sxs-lookup"><span data-stu-id="db17c-122">Choose the data type for **Value**.</span></span> <span data-ttu-id="db17c-123">可能であれば、 **[式]** のデータ型と一致するデータ型を選択します。</span><span class="sxs-lookup"><span data-stu-id="db17c-123">When possible, choose a data type that matches the data type for **Expression**.</span></span>  
  
 <span data-ttu-id="db17c-124">**[式]** および **[値]** の値は、同じデータ型に評価される必要があります。</span><span class="sxs-lookup"><span data-stu-id="db17c-124">The values in **Expression** and **Value** must evaluate to the same data type.</span></span> <span data-ttu-id="db17c-125">たとえば、 **[式]** が System.Int32 データ型のフィールドに設定され、 **[値]** が 7 に設定されている場合、ドロップダウン リストから **Integer**を選択します。</span><span class="sxs-lookup"><span data-stu-id="db17c-125">For example, if **Expression** is set to a field that has the data type System.Int32 and **Value** is set to 7, from the drop-down list, choose **Integer**.</span></span>  
  
 <span data-ttu-id="db17c-126">必要なデータ型のオプションがドロップダウン リストにない場合は、値を正しいデータ型に変換する式を作成します。</span><span class="sxs-lookup"><span data-stu-id="db17c-126">If the data type option you need is not in the drop-down list, write an expression to convert the value to the correct data type.</span></span> <span data-ttu-id="db17c-127">詳細については、「[フィルター式の例 &#40;レポート ビルダーおよび SSRS&#41;](report-design/filter-equation-examples-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="db17c-127">For more information, see [Filter Equation Examples &#40;Report Builder and SSRS&#41;](report-design/filter-equation-examples-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="db17c-128">**[オペレーター]**</span><span class="sxs-lookup"><span data-stu-id="db17c-128">**Operator**</span></span>  
 <span data-ttu-id="db17c-129">式と値の比較に使用する演算子を選択します。</span><span class="sxs-lookup"><span data-stu-id="db17c-129">Choose the operator to use to compare the expression and the value.</span></span>  
  
 <span data-ttu-id="db17c-130">**Value**</span><span class="sxs-lookup"><span data-stu-id="db17c-130">**Value**</span></span>  
 <span data-ttu-id="db17c-131">**[式]** ボックスに指定された式を評価する際に使用する式または値を入力します。</span><span class="sxs-lookup"><span data-stu-id="db17c-131">Type the expression or value to use when evaluating the expression specified in the **Expression** box.</span></span> <span data-ttu-id="db17c-132">式を編集するには、式 ([**fx**]) ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="db17c-132">Click the Expression (**fx**) button to edit the expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db17c-133">参照</span><span class="sxs-lookup"><span data-stu-id="db17c-133">See Also</span></span>  
 <span data-ttu-id="db17c-134">[レポート埋め込みデータセットと共有データセット &#40;レポートビルダーと SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="db17c-134">[Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="db17c-135">[レポートパラメーター &#40;レポートビルダーとレポートデザイナー&#41;](report-design/report-parameters-report-builder-and-report-designer.md) </span><span class="sxs-lookup"><span data-stu-id="db17c-135">[Report Parameters &#40;Report Builder and Report Designer&#41;](report-design/report-parameters-report-builder-and-report-designer.md) </span></span>  
 <span data-ttu-id="db17c-136">[データセット &#40;レポートビルダーと SSRS&#41;にフィルターを追加する](report-data/add-a-filter-to-a-dataset-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="db17c-136">[Add a Filter to a Dataset &#40;Report Builder and SSRS&#41;](report-data/add-a-filter-to-a-dataset-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="db17c-137">レポートでの式の使用 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="db17c-137">Expression Uses in Reports &#40;Report Builder and SSRS&#41;</span></span>](report-design/expression-uses-in-reports-report-builder-and-ssrs.md)  
  
  
