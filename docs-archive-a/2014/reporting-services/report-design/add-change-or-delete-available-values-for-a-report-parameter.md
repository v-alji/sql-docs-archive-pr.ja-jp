---
title: レポートパラメーターに使用できる値を追加、変更、または削除する (レポートビルダーおよび SSRS) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.reportparameters.availablevalues.f1
- "10455"
- "10071"
ms.assetid: 0e03264c-523f-4c59-b71b-ceef600f75f6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 985ab3e8dc1d74f94e7242ff57f46ffe4fba9586
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640718"
---
# <a name="add-change-or-delete-available-values-for-a-report-parameter-report-builder-and-ssrs"></a><span data-ttu-id="49d1d-102">レポート パラメーターの値の追加、変更、または削除 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="49d1d-102">Add, Change, or Delete Available Values for a Report Parameter (Report Builder and SSRS)</span></span>
  <span data-ttu-id="49d1d-103">レポート パラメーターを作成した後、ユーザーに対して表示する使用可能な値の一覧を指定できます。</span><span class="sxs-lookup"><span data-stu-id="49d1d-103">After you create a report parameter, you can specify a list of available values to display to the user.</span></span> <span data-ttu-id="49d1d-104">使用可能な値の一覧を使用すると、ユーザーがパラメーターに選択できる値が有効な値のみに制限されます。</span><span class="sxs-lookup"><span data-stu-id="49d1d-104">An available values list limits the choices a user can make to only valid values for the parameter.</span></span>  
  
 <span data-ttu-id="49d1d-105">使用可能な値は、レポートの実行時にツール バーのレポート パラメーターの横にあるドロップダウン リストに表示されます。</span><span class="sxs-lookup"><span data-stu-id="49d1d-105">Available values appear in a drop-down list next to the report parameter on the toolbar when the report runs.</span></span> <span data-ttu-id="49d1d-106">レポート パラメーターは単一値または複数値を表すことができます。</span><span class="sxs-lookup"><span data-stu-id="49d1d-106">Report parameters can represent one value or multiple values.</span></span> <span data-ttu-id="49d1d-107">値が複数ある場合は、一覧の先頭に **[すべて選択]** という項目が用意されるため、ユーザーは 1 回のクリックですべての値を選択またはクリアできます。</span><span class="sxs-lookup"><span data-stu-id="49d1d-107">For multiple values, the top of list begins with a **Select All** feature so the user can select or clear all values with a single click.</span></span>  
  
 <span data-ttu-id="49d1d-108">静的な値の一覧か、レポート データセットからの一覧を設定できます。</span><span class="sxs-lookup"><span data-stu-id="49d1d-108">You can provide a static list of values or a list from a report dataset.</span></span> <span data-ttu-id="49d1d-109">必要に応じてラベル フィールドを指定して、値の表示名を設定できます。</span><span class="sxs-lookup"><span data-stu-id="49d1d-109">You can optionally provide a friendly name for values by specifying a label field.</span></span> <span data-ttu-id="49d1d-110">たとえば、[ `ProductID` ] フィールドに基づくパラメーターの場合、パラメーター ラベルに [ `ProductName` ] フィールドを表示できます。</span><span class="sxs-lookup"><span data-stu-id="49d1d-110">For example, for a parameter based on a `ProductID` field, you can display the `ProductName` field in the parameter label.</span></span> <span data-ttu-id="49d1d-111">ユーザーはレポートの実行時に製品名から選択できますが、実際に選択される値は対応する [ `ProductID`] です。</span><span class="sxs-lookup"><span data-stu-id="49d1d-111">When the report runs, the user can choose from the product names, but the actual chosen value is the corresponding `ProductID`.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
 <span data-ttu-id="49d1d-112">レポートをパブリッシュした後、パラメーター プロパティの値をレポート サーバーに設定して、レポート作成ツールのレポートで定義される使用可能な値をオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="49d1d-112">After you publish a report, you can override the available values that you define in the report in the report authoring tool, by setting parameter property values on the report server.</span></span> <span data-ttu-id="49d1d-113">詳細については、「 [レポート パラメーター (レポート ビルダーおよびレポート デザイナー)](report-parameters-report-builder-and-report-designer.md)にあります。</span><span class="sxs-lookup"><span data-stu-id="49d1d-113">For more information, see [Report Parameters &#40;Report Builder and Report Designer&#41;](report-parameters-report-builder-and-report-designer.md).</span></span>  
  
### <a name="to-add-or-change-the-available-values-for-a-report-parameter"></a><span data-ttu-id="49d1d-114">レポート パラメーターに使用可能な値を追加または変更するには</span><span class="sxs-lookup"><span data-stu-id="49d1d-114">To add or change the available values for a report parameter</span></span>  
  
1.  <span data-ttu-id="49d1d-115">レポート データ ペインで [パラメーター] ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="49d1d-115">In the Report Data pane, expand the Parameters node.</span></span> <span data-ttu-id="49d1d-116">パラメーターを右クリックし、 **[パラメーターのプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="49d1d-116">Right-click the parameter and click **Parameter Properties**.</span></span> <span data-ttu-id="49d1d-117">**[レポート パラメーターのプロパティ]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="49d1d-117">The **Report Parameter Properties** dialog box opens.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="49d1d-118">レポート データ ペインが表示されていない場合は、 **[表示]** をクリックしてから **[レポート データ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="49d1d-118">If the Report Data pane is not visible, click **View** and then click **Report Data**.</span></span>  
  
2.  <span data-ttu-id="49d1d-119">**[使用できる値]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="49d1d-119">Click **Available Values**.</span></span> <span data-ttu-id="49d1d-120">使用可能な値のオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="49d1d-120">Select an available values option:</span></span>  
  
    -   <span data-ttu-id="49d1d-121">**[値の指定]** をクリックして値のリストを手動で設定し、必要に応じて値の表示名 (ラベル) を設定します。</span><span class="sxs-lookup"><span data-stu-id="49d1d-121">Click **Specify values** to manually provide a list of values, and optionally, friendly names (the labels) for the values.</span></span>  
  
         <span data-ttu-id="49d1d-122">**[追加]** をクリックし、 **[値]** ボックスに値を入力します。必要に応じて、 **[ラベル]** ボックスにラベルを入力します。</span><span class="sxs-lookup"><span data-stu-id="49d1d-122">Click **Add** and then enter the value in the **Value** text box, and optionally, the label in the **Label** text box.</span></span> <span data-ttu-id="49d1d-123">ラベルを指定しない場合は、値が使用されます。</span><span class="sxs-lookup"><span data-stu-id="49d1d-123">If you do not provide a label, the value is used.</span></span> <span data-ttu-id="49d1d-124">値を求める式を記述することもできます。</span><span class="sxs-lookup"><span data-stu-id="49d1d-124">You can write an expression for a value.</span></span> <span data-ttu-id="49d1d-125">データ型はパラメーターのデータ型と一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="49d1d-125">The data type must match the data type of the parameter.</span></span> <span data-ttu-id="49d1d-126">フィールド名は、パラメーターの式では使用できません。</span><span class="sxs-lookup"><span data-stu-id="49d1d-126">Field names cannot be used in an expression for a parameter.</span></span> <span data-ttu-id="49d1d-127">例については、「[一般的に使用されるフィルター &#40;レポート ビルダーおよび SSRS&#41;](commonly-used-filters-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="49d1d-127">For examples, see [Commonly Used Filters &#40;Report Builder and SSRS&#41;](commonly-used-filters-report-builder-and-ssrs.md).</span></span>  
  
         <span data-ttu-id="49d1d-128">設定するすべての値に対して、この手順を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="49d1d-128">Repeat this step for as many values as you want to provide.</span></span> <span data-ttu-id="49d1d-129">この一覧に表示されるアイテムの順序によって、ユーザーに表示されるドロップダウン リストのアイテムの順序が決まります。</span><span class="sxs-lookup"><span data-stu-id="49d1d-129">The order of items you see in this list determines the order that the user sees them in the drop-down list.</span></span> <span data-ttu-id="49d1d-130">一覧のアイテムの順序を変更するには、 **[値]** または **[ラベル]** ボックスをクリックしてアイテムを選択し、上矢印および下矢印ボタンを使用して一覧内のアイテムを上下に移動します。</span><span class="sxs-lookup"><span data-stu-id="49d1d-130">To change the order of an item in the list, click a **Value** or **Label** text box to select the item, and then use the up and down arrow buttons to move the item higher or lower in the list.</span></span>  
  
    -   <span data-ttu-id="49d1d-131">**[クエリから値を取得]** をクリックして、このパラメーターの値と必要に応じて表示名を取得する既存のデータセットの名前を設定します。</span><span class="sxs-lookup"><span data-stu-id="49d1d-131">Click **Get values from a query** to provide the name of an existing dataset that retrieves the values, and optionally, the friendly names for this parameter.</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="49d1d-132">同じデータセットに、レポート パラメーターに対応するクエリ パラメーターが含まれている場合は、レポートを実行しようとするとエラー メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="49d1d-132">If the same dataset contains the corresponding query parameter for the report parameter, the report will display an error message when you try to run it.</span></span> <span data-ttu-id="49d1d-133">このエラーを解決するには、別のデータセットを使用して値を取得します。</span><span class="sxs-lookup"><span data-stu-id="49d1d-133">You resolve this error by using a different dataset to retrieve the values.</span></span>  
  
         <span data-ttu-id="49d1d-134">**[データセット]** で、データセットの名前を選択します。</span><span class="sxs-lookup"><span data-stu-id="49d1d-134">In **Dataset**, choose the name of the dataset.</span></span>  
  
         <span data-ttu-id="49d1d-135">**[値フィールド]** で、パラメーター値を指定するフィールドの名前を選択します。</span><span class="sxs-lookup"><span data-stu-id="49d1d-135">In **Value field**, choose the name of the field that provides parameter values.</span></span>  
  
         <span data-ttu-id="49d1d-136">**[ラベル フィールド]** には、パラメーターの表示名を指定するフィールドの名前を選択します。</span><span class="sxs-lookup"><span data-stu-id="49d1d-136">In **Label field**, choose the name of the field that provides the friendly names for the parameter.</span></span> <span data-ttu-id="49d1d-137">表示名に個別のフィールドがない場合は、 **[値]** フィールドに選択したものと同じフィールドを選択します。</span><span class="sxs-lookup"><span data-stu-id="49d1d-137">If there is no separate field for friendly names, choose the same field as you chose for the **Value** field.</span></span>  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     <span data-ttu-id="49d1d-138">レポートをプレビューすると、パラメーターに使用可能な値のドロップダウン リストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="49d1d-138">When you preview the report, you see a drop-down list of available values for the parameter.</span></span>  
  
### <a name="to-remove-the-available-values-for-a-report-parameter"></a><span data-ttu-id="49d1d-139">レポート パラメーターに使用可能な値を削除するには</span><span class="sxs-lookup"><span data-stu-id="49d1d-139">To remove the available values for a report parameter</span></span>  
  
1.  <span data-ttu-id="49d1d-140">レポート データ ペインで [パラメーター] ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="49d1d-140">In the Report Data pane, expand the Parameters node.</span></span> <span data-ttu-id="49d1d-141">パラメーターを右クリックし、 **[パラメーターのプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="49d1d-141">Right-click the parameter and click **Parameter Properties**.</span></span> <span data-ttu-id="49d1d-142">**[レポート パラメーター]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="49d1d-142">The **Report Parameters** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="49d1d-143">**[使用できる値]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="49d1d-143">Click **Available Values**.</span></span>  
  
3.  <span data-ttu-id="49d1d-144">**[次のオプションから 1 つを選択]** で **[なし]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="49d1d-144">In **Select from one of the following options**, click **None**.</span></span>  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     <span data-ttu-id="49d1d-145">レポートをプレビューすると、パラメーターに使用可能な値のドロップダウン リストが表示されなくなります。</span><span class="sxs-lookup"><span data-stu-id="49d1d-145">When you preview the report, you the drop-down list of available values for the parameter no longer appears.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49d1d-146">参照</span><span class="sxs-lookup"><span data-stu-id="49d1d-146">See Also</span></span>  
 <span data-ttu-id="49d1d-147">[レポート パラメーターの順序の変更 &#40;レポート ビルダーおよび SSRS&#41;](change-the-order-of-a-report-parameter-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="49d1d-147">[Change the Order of a Report Parameter &#40;Report Builder and SSRS&#41;](change-the-order-of-a-report-parameter-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="49d1d-148">[レポート パラメーターの追加、変更、または削除 &#40;レポート ビルダーおよび SSRS&#41;](add-change-or-delete-a-report-parameter-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="49d1d-148">[Add, Change, or Delete a Report Parameter &#40;Report Builder and SSRS&#41;](add-change-or-delete-a-report-parameter-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="49d1d-149">[カスケード型パラメーターのレポートへの追加 (レポート ビルダーおよび SSRS)](add-cascading-parameters-to-a-report-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="49d1d-149">[Add Cascading Parameters to a Report &#40;Report Builder and SSRS&#41;](add-cascading-parameters-to-a-report-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="49d1d-150">[レポート パラメーターの既定値の追加、変更、または削除 &#40;レポート ビルダーおよび SSRS&#41;](add-change-or-delete-default-values-for-a-report-parameter.md) </span><span class="sxs-lookup"><span data-stu-id="49d1d-150">[Add, Change, or Delete Default Values for a Report Parameter &#40;Report Builder and SSRS&#41;](add-change-or-delete-default-values-for-a-report-parameter.md) </span></span>  
 <span data-ttu-id="49d1d-151">[Parameters コレクションの参照 &#40;レポート ビルダーおよび SSRS&#41;](built-in-collections-parameters-collection-references-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="49d1d-151">[Parameters Collection References &#40;Report Builder and SSRS&#41;](built-in-collections-parameters-collection-references-report-builder.md) </span></span>  
 <span data-ttu-id="49d1d-152">[チュートリアル: レポートへのパラメーターの追加 &#40;レポート ビルダー&#41;](../tutorial-add-a-parameter-to-your-report-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="49d1d-152">[Tutorial: Add a Parameter to Your Report &#40;Report Builder&#41;](../tutorial-add-a-parameter-to-your-report-report-builder.md) </span></span>  
 [<span data-ttu-id="49d1d-153">式 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="49d1d-153">Expressions &#40;Report Builder and SSRS&#41;</span></span>](expressions-report-builder-and-ssrs.md)  
  
  
