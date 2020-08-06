---
title: データセットへのフィルターの追加 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: eed37e74-6a43-4d7c-9959-2d5fa6a6aba9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f51411d31d8ee29bf0f163085077dcee8fd79bdd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631599"
---
# <a name="add-a-filter-to-a-dataset-report-builder-and-ssrs"></a><span data-ttu-id="e683e-102">データセットへのフィルターの追加 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="e683e-102">Add a Filter to a Dataset (Report Builder and SSRS)</span></span>
  <span data-ttu-id="e683e-103">データが外部データ ソースから取得された後に、データセットにフィルターを追加してレポート内のデータを制限できます。</span><span class="sxs-lookup"><span data-stu-id="e683e-103">Add a filter to a dataset to limit the data in a report after the data is retrieved from an external data source.</span></span> <span data-ttu-id="e683e-104">データセットにフィルターを追加すると、すべてのレポート パーツまたはデータ領域では、フィルター条件に一致するデータのみが使用されます。</span><span class="sxs-lookup"><span data-stu-id="e683e-104">When you add a filter to a dataset, all report parts or data regions use only data that matches the filter conditions.</span></span>  
  
 <span data-ttu-id="e683e-105">共有データセットの場合、すべての依存アイテムに適用されるフィルターは、レポート サーバー上の共有データセット定義の一部である必要があります。</span><span class="sxs-lookup"><span data-stu-id="e683e-105">For a shared dataset, a filter that applies to all dependent items must be part of the shared dataset definition on the report server.</span></span> <span data-ttu-id="e683e-106">共有データセットのインスタンスを含むレポートまたはレポート パーツは、インスタンスにのみ適用される追加のフィルターを作成できます。</span><span class="sxs-lookup"><span data-stu-id="e683e-106">A report or report part that contains an instance of a shared dataset can create an additional filter that applies only to the instance.</span></span>  
  
 <span data-ttu-id="e683e-107">フィルターを追加するには、フィルター式となる 1 つ以上の条件を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e683e-107">To add a filter, you must specify one or more conditions that are filter equations.</span></span> <span data-ttu-id="e683e-108">フィルター式は、フィルターの対象となるデータを識別する式、演算子、および、比較対象の値で構成されます。</span><span class="sxs-lookup"><span data-stu-id="e683e-108">A filter equation consists of an expression that identifies the data that you want to filter, an operator, and the value to compare to.</span></span> <span data-ttu-id="e683e-109">フィルターの対象となるデータとその比較対象となる値とでは、データ型を一致させる必要があります。</span><span class="sxs-lookup"><span data-stu-id="e683e-109">The data types of the filtered data and the value must match.</span></span> <span data-ttu-id="e683e-110">データセットの集計値に対するフィルター処理はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="e683e-110">Filtering on aggregate values for a dataset is not supported.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-filter-to-a-shared-dataset"></a><span data-ttu-id="e683e-111">共有データセットにフィルターを追加するには</span><span class="sxs-lookup"><span data-stu-id="e683e-111">To add a filter to a shared dataset</span></span>  
  
1.  <span data-ttu-id="e683e-112">共有データセット モードで共有データセットを開きます。</span><span class="sxs-lookup"><span data-stu-id="e683e-112">Open a shared dataset in shared dataset mode.</span></span>  
  
2.  <span data-ttu-id="e683e-113">**[ホーム]** タブの **[共有データセット]** グループで、[データセット] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e683e-113">On the **Home** tab, in the **Shared Datasets** group, click Datasets.</span></span> <span data-ttu-id="e683e-114">**[データセットのプロパティ]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e683e-114">The **Dataset Properties** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="e683e-115">**[フィルター]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e683e-115">Click **Filters**.</span></span> <span data-ttu-id="e683e-116">現在のフィルター式の一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="e683e-116">This displays the current list of filter equations.</span></span> <span data-ttu-id="e683e-117">既定では、何も表示されません。</span><span class="sxs-lookup"><span data-stu-id="e683e-117">By default, the list is empty.</span></span>  
  
4.  <span data-ttu-id="e683e-118">**[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e683e-118">Click **Add**.</span></span> <span data-ttu-id="e683e-119">新しい空のフィルター式が表示されます。</span><span class="sxs-lookup"><span data-stu-id="e683e-119">A new blank filter equation appears.</span></span>  
  
5.  <span data-ttu-id="e683e-120">**[式]** で、フィルター処理の対象となるフィールドの式を入力するか、選択します。</span><span class="sxs-lookup"><span data-stu-id="e683e-120">In **Expression**, type or select the expression for the field to filter.</span></span> <span data-ttu-id="e683e-121">式を編集するには、式 ( *[fx]* ) ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="e683e-121">To edit the expression, click the expression (*fx*) button.</span></span>  
  
6.  <span data-ttu-id="e683e-122">リスト ボックスから、手順 5. で作成した式のデータ型と同じデータ型を選択します。</span><span class="sxs-lookup"><span data-stu-id="e683e-122">From the list box, select the data type that matches the type of data in the expression you created in step 5.</span></span>  
  
7.  <span data-ttu-id="e683e-123">**[演算子]** ボックスで、 **[式]** ボックスの値と **[値]** ボックスの値とを比較するための演算子を選択します。</span><span class="sxs-lookup"><span data-stu-id="e683e-123">In the **Operator** box, select the operator that you want the filter to use to compare the values in the **Expression** box and the **Value** box.</span></span> <span data-ttu-id="e683e-124">選択した演算子によって、次の手順で使用する値の数が異なります。</span><span class="sxs-lookup"><span data-stu-id="e683e-124">The operator you choose determines the number of values that are used from the next step.</span></span>  
  
8.  <span data-ttu-id="e683e-125">**[値]** ボックスで、 **[式]** の値を評価するフィルター用の式または値を入力します。</span><span class="sxs-lookup"><span data-stu-id="e683e-125">In the **Value** box, type the expression or value against which you want the filter to evaluate the value in **Expression**.</span></span>  
  
     <span data-ttu-id="e683e-126">フィルター式の例については、「[フィルター式の例 &#40;レポート ビルダーおよび SSRS&#41;](../report-design/filter-equation-examples-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e683e-126">For examples of filter equations, see [Filter Equation Examples &#40;Report Builder and SSRS&#41;](../report-design/filter-equation-examples-report-builder-and-ssrs.md).</span></span>  
  
9. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-add-a-filter-to-an-embedded-dataset-or-a-shared-dataset-instance"></a><span data-ttu-id="e683e-127">埋め込みデータセットまたは共有データセットのインスタンスにフィルターを追加するには</span><span class="sxs-lookup"><span data-stu-id="e683e-127">To add a filter to an embedded dataset or a shared dataset instance</span></span>  
  
1.  <span data-ttu-id="e683e-128">レポート デザイン モードでレポートを開きます。</span><span class="sxs-lookup"><span data-stu-id="e683e-128">Open a report in report design mode.</span></span>  
  
2.  <span data-ttu-id="e683e-129">**レポート データ** ペインでデータセットを右クリックし、 **[データセットのプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e683e-129">Right-click a dataset in the **Report Data** pane and then click **Dataset Properties**.</span></span> <span data-ttu-id="e683e-130">**[データセットのプロパティ]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e683e-130">The **Dataset Properties** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="e683e-131">**[フィルター]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e683e-131">Click **Filters**.</span></span> <span data-ttu-id="e683e-132">現在のフィルター式の一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="e683e-132">This displays the current list of filter equations.</span></span> <span data-ttu-id="e683e-133">既定では、何も表示されません。</span><span class="sxs-lookup"><span data-stu-id="e683e-133">By default, the list is empty.</span></span>  
  
4.  <span data-ttu-id="e683e-134">**[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e683e-134">Click **Add**.</span></span> <span data-ttu-id="e683e-135">新しい空のフィルター式が表示されます。</span><span class="sxs-lookup"><span data-stu-id="e683e-135">A new blank filter equation appears.</span></span>  
  
5.  <span data-ttu-id="e683e-136">**[式]** で、フィルター処理の対象となるフィールドの式を入力するか、選択します。</span><span class="sxs-lookup"><span data-stu-id="e683e-136">In **Expression**, type or select the expression for the field to filter.</span></span> <span data-ttu-id="e683e-137">式を編集するには、式 ( *[fx]* ) ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="e683e-137">To edit the expression, click the expression (*fx*) button.</span></span>  
  
6.  <span data-ttu-id="e683e-138">ドロップダウン ボックスから、手順 5. で作成した式のデータ型と同じデータ型を選択します。</span><span class="sxs-lookup"><span data-stu-id="e683e-138">From the drop-down box, select the data type that matches the type of data in the expression you created in step 5.</span></span>  
  
7.  <span data-ttu-id="e683e-139">**[演算子]** ボックスで、 **[式]** ボックスの値と **[値]** ボックスの値とを比較するための演算子を選択します。</span><span class="sxs-lookup"><span data-stu-id="e683e-139">In the **Operator** box, select the operator that you want the filter to use to compare the values in the **Expression** box and the **Value** box.</span></span> <span data-ttu-id="e683e-140">選択した演算子によって、次の手順で使用する値の数が異なります。</span><span class="sxs-lookup"><span data-stu-id="e683e-140">The operator you choose determines the number of values that are used from the next step.</span></span>  
  
8.  <span data-ttu-id="e683e-141">**[値]** ボックスで、 **[式]** の値を評価するフィルター用の式または値を入力します。</span><span class="sxs-lookup"><span data-stu-id="e683e-141">In the **Value** box, type the expression or value against which you want the filter to evaluate the value in **Expression**.</span></span>  
  
     <span data-ttu-id="e683e-142">フィルター式の例については、「[フィルター式の例 &#40;レポート ビルダーおよび SSRS&#41;](../report-design/filter-equation-examples-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e683e-142">For examples of filter equations, see [Filter Equation Examples &#40;Report Builder and SSRS&#41;](../report-design/filter-equation-examples-report-builder-and-ssrs.md).</span></span>  
  
9. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e683e-143">参照</span><span class="sxs-lookup"><span data-stu-id="e683e-143">See Also</span></span>  
 <span data-ttu-id="e683e-144">[データセット フィルター、データ領域フィルター、およびグループ フィルターの追加 (レポート ビルダーおよび SSRS)](../report-design/add-dataset-filters-data-region-filters-and-group-filters.md) </span><span class="sxs-lookup"><span data-stu-id="e683e-144">[Add Dataset Filters, Data Region Filters, and Group Filters &#40;Report Builder and SSRS&#41;](../report-design/add-dataset-filters-data-region-filters-and-group-filters.md) </span></span>  
 <span data-ttu-id="e683e-145">[式の例 (レポート ビルダーおよび SSRS)](../report-design/expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="e683e-145">[Expression Examples &#40;Report Builder and SSRS&#41;](../report-design/expression-examples-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="e683e-146">フィルターの追加 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="e683e-146">Add a Filter &#40;Report Builder and SSRS&#41;</span></span>](../report-design/add-a-filter-report-builder-and-ssrs.md)  
  
  
