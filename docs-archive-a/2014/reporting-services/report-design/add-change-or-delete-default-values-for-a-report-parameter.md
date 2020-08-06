---
title: レポートパラメーターの既定値の追加、変更、または削除 (レポートビルダーおよび SSRS) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10460"
- sql12.rtp.rptdesigner.reportparameters.defaultvalues.f1
- "10072"
ms.assetid: 6a87e069-b3a9-47b6-bcec-afcdd8aff65f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 1d50fdbbe42a656ef839785c0968b36c8c829e11
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640724"
---
# <a name="add-change-or-delete-default-values-for-a-report-parameter-report-builder-and-ssrs"></a><span data-ttu-id="51799-102">レポート パラメーターの既定値の追加、変更、または削除 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="51799-102">Add, Change, or Delete Default Values for a Report Parameter (Report Builder and SSRS)</span></span>
  <span data-ttu-id="51799-103">レポート パラメーターを作成した後、既定値のリストを指定できます。</span><span class="sxs-lookup"><span data-stu-id="51799-103">After you create a report parameter, you can provide a list of default values.</span></span> <span data-ttu-id="51799-104">すべてのパラメーターに有効な既定値がある場合、レポートは、最初に表示またはプレビューしたときに自動的に実行します。</span><span class="sxs-lookup"><span data-stu-id="51799-104">If all parameters have a valid default value, the report runs automatically when you first view or preview it.</span></span>  
  
 <span data-ttu-id="51799-105">レポート パラメーターは単一値または複数値を表すことができます。</span><span class="sxs-lookup"><span data-stu-id="51799-105">Report parameters can represent one value or multiple values.</span></span> <span data-ttu-id="51799-106">単一値については、リテラルまたは式を指定できます。</span><span class="sxs-lookup"><span data-stu-id="51799-106">For single values, you can provide a literal or expression.</span></span> <span data-ttu-id="51799-107">複数値については、静的リストまたはレポート データセットからのリストを指定できます。</span><span class="sxs-lookup"><span data-stu-id="51799-107">For multiple values, you can provide a static list or a list from a report dataset.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
 <span data-ttu-id="51799-108">レポートをパブリッシュした後、パラメーター プロパティの値をレポート サーバーに設定して、レポート作成ツールのレポートで定義される既定値をオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="51799-108">After you publish a report, you can override the default values that you define in the report in the report authoring tool, by setting parameter property values on the report server.</span></span> <span data-ttu-id="51799-109">リンク レポートを作成して、既定のパラメーター値の複数のセットを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="51799-109">You can also provide multiple sets of default parameter values by creating linked reports.</span></span> <span data-ttu-id="51799-110">詳細については、「  [レポート パラメーター (レポート ビルダーおよびレポート デザイナー)](report-parameters-report-builder-and-report-designer.md)</span><span class="sxs-lookup"><span data-stu-id="51799-110">For more information, see  [Report Parameters &#40;Report Builder and Report Designer&#41;](report-parameters-report-builder-and-report-designer.md)</span></span>  
  
### <a name="to-add-or-change-the-default-values-for-a-report-parameter"></a><span data-ttu-id="51799-111">レポート パラメーターの既定値を追加または変更するには</span><span class="sxs-lookup"><span data-stu-id="51799-111">To add or change the default values for a report parameter</span></span>  
  
1.  <span data-ttu-id="51799-112">レポート データ ペインで **[パラメーター]** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="51799-112">In the Report Data pane, expand the **Parameters** node.</span></span> <span data-ttu-id="51799-113">パラメーターを右クリックし、 **[編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="51799-113">Right-click the parameter and click **Edit**.</span></span> <span data-ttu-id="51799-114">**[レポート パラメーターのプロパティ]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="51799-114">The **Report Parameter Properties** dialog box opens.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="51799-115">レポート データ ペインが表示されていない場合は、 **[表示]** をクリックしてから **[レポート データ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="51799-115">If the Report Data pane is not visible, click **View** and then click **Report Data**.</span></span>  
  
2.  <span data-ttu-id="51799-116">**[既定値]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="51799-116">Click **Default Values**.</span></span>  
  
3.  <span data-ttu-id="51799-117">既定のオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="51799-117">Select a default option:</span></span>  
  
    -   <span data-ttu-id="51799-118">1 つの値または値のリストを手動で指定するには、 **[値の指定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="51799-118">To manually provide a value or list of values, click **Specify values**.</span></span> <span data-ttu-id="51799-119">**[追加]** をクリックして、 **[値]** ボックスに値を入力します。</span><span class="sxs-lookup"><span data-stu-id="51799-119">Click **Add** and then enter the value in the **Value** text box.</span></span> <span data-ttu-id="51799-120">値を求める式を記述することもできます。</span><span class="sxs-lookup"><span data-stu-id="51799-120">You can write an expression for a value.</span></span> <span data-ttu-id="51799-121">データ型はパラメーターのデータ型と一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="51799-121">The data type must match the data type of the parameter.</span></span> <span data-ttu-id="51799-122">フィールド名は、パラメーターの式では使用できません。</span><span class="sxs-lookup"><span data-stu-id="51799-122">Field names cannot be used in an expression for a parameter.</span></span>  
  
         <span data-ttu-id="51799-123">複数値パラメーターの場合は、指定する値の数だけこの手順を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="51799-123">For multivalue parameters, repeat this step for as many values as you want to provide.</span></span> <span data-ttu-id="51799-124">この一覧に表示されるアイテムの順序によって、ユーザーに表示されるドロップダウン リストのアイテムの順序が決まります。</span><span class="sxs-lookup"><span data-stu-id="51799-124">The order of items you see in this list determines the order that the user sees them in the drop-down list.</span></span> <span data-ttu-id="51799-125">一覧のアイテムの順序を変更するには、 **[値]** ボックスをクリックしてアイテムを選択し、上矢印および下矢印ボタンを使用して一覧内のアイテムを上下に移動します。</span><span class="sxs-lookup"><span data-stu-id="51799-125">To change the order of an item in the list, click the **Value** text box to select the item, and then use the up and down arrow buttons to move the item higher or lower in the list.</span></span>  
  
    -   <span data-ttu-id="51799-126">値を取得する既存のデータセットの名前を指定するには、 **[クエリから値を取得]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="51799-126">To provide the name of an existing dataset that retrieves the values, click **Get values from a query**.</span></span> <span data-ttu-id="51799-127">**[データセット]** で、データセットの名前を選択します。</span><span class="sxs-lookup"><span data-stu-id="51799-127">In **Dataset**, choose the name of the dataset.</span></span>  
  
         <span data-ttu-id="51799-128">**[値フィールド]** で、パラメーター値を指定するフィールドの名前を選択します。</span><span class="sxs-lookup"><span data-stu-id="51799-128">In **Value field**, choose the name of the field that provides parameter values.</span></span>  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-remove-the-default-values-for-a-report-parameter"></a><span data-ttu-id="51799-129">レポート パラメーターの既定値を削除するには</span><span class="sxs-lookup"><span data-stu-id="51799-129">To remove the default values for a report parameter</span></span>  
  
1.  <span data-ttu-id="51799-130">レポート データ ペインで **[パラメーター]** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="51799-130">In the Report Data pane, expand the **Parameters** node.</span></span> <span data-ttu-id="51799-131">パラメーターを右クリックし、 **[編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="51799-131">Right-click the parameter and click **Edit**.</span></span> <span data-ttu-id="51799-132">**[レポート パラメーターのプロパティ]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="51799-132">The **Report Parameter Properties** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="51799-133">**[既定値]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="51799-133">Click **Default Values**.</span></span>  
  
3.  <span data-ttu-id="51799-134">**[次のオプションから 1 つを選択]** で、 **[既定値なし]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="51799-134">In **Select from one of the following options**, click **No default value**.</span></span>  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="51799-135">参照</span><span class="sxs-lookup"><span data-stu-id="51799-135">See Also</span></span>  
 <span data-ttu-id="51799-136">[レポート パラメーター (レポート ビルダーおよびレポート デザイナー)](report-parameters-report-builder-and-report-designer.md) </span><span class="sxs-lookup"><span data-stu-id="51799-136">[Report Parameters &#40;Report Builder and Report Designer&#41;](report-parameters-report-builder-and-report-designer.md) </span></span>  
 <span data-ttu-id="51799-137">[カスケード型パラメーターのレポートへの追加 (レポート ビルダーおよび SSRS)](add-cascading-parameters-to-a-report-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="51799-137">[Add Cascading Parameters to a Report &#40;Report Builder and SSRS&#41;](add-cascading-parameters-to-a-report-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="51799-138">[チュートリアル: レポートへのパラメーターの追加 &#40;レポート ビルダー&#41;](../tutorial-add-a-parameter-to-your-report-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="51799-138">[Tutorial: Add a Parameter to Your Report &#40;Report Builder&#41;](../tutorial-add-a-parameter-to-your-report-report-builder.md) </span></span>  
 <span data-ttu-id="51799-139">[データセット フィルター、データ領域フィルター、およびグループ フィルターの追加 (レポート ビルダーおよび SSRS)](add-dataset-filters-data-region-filters-and-group-filters.md) </span><span class="sxs-lookup"><span data-stu-id="51799-139">[Add Dataset Filters, Data Region Filters, and Group Filters &#40;Report Builder and SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md) </span></span>  
 <span data-ttu-id="51799-140">[Parameters コレクションの参照 &#40;レポート ビルダーおよび SSRS&#41;](built-in-collections-parameters-collection-references-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="51799-140">[Parameters Collection References &#40;Report Builder and SSRS&#41;](built-in-collections-parameters-collection-references-report-builder.md) </span></span>  
 <span data-ttu-id="51799-141">[レポート パラメーターの順序の変更 &#40;レポート ビルダーおよび SSRS&#41;](change-the-order-of-a-report-parameter-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="51799-141">[Change the Order of a Report Parameter &#40;Report Builder and SSRS&#41;](change-the-order-of-a-report-parameter-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="51799-142">[レポート パラメーターの追加、変更、または削除 &#40;レポート ビルダーおよび SSRS&#41;](add-change-or-delete-a-report-parameter-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="51799-142">[Add, Change, or Delete a Report Parameter &#40;Report Builder and SSRS&#41;](add-change-or-delete-a-report-parameter-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="51799-143">式 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="51799-143">Expressions &#40;Report Builder and SSRS&#41;</span></span>](expressions-report-builder-and-ssrs.md)  
  
  
