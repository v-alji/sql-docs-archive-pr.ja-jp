---
title: '[データセットフィルター] または [モデルフィルター] ダイアログボックス |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a9602174-b7e2-4e16-8ded-dfd8eb9264d7
author: minewiskan
ms.author: owend
ms.openlocfilehash: afa796cd8cb23894c059deba411b3e1d6676e3b9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87717013"
---
# <a name="data-set-filter-or-model-filter-dialog-box"></a><span data-ttu-id="c396b-102">[データセット フィルター] または [モデル フィルター] ダイアログ ボックス</span><span class="sxs-lookup"><span data-stu-id="c396b-102">Data Set Filter or Model Filter Dialog Box</span></span>
  <span data-ttu-id="c396b-103">このダイアログ ボックスを使用すると、データセットに適用できるフィルターを作成できます。</span><span class="sxs-lookup"><span data-stu-id="c396b-103">This dialog box helps you build the filters that you can apply to a data set.</span></span>  <span data-ttu-id="c396b-104">データセットとして、テスト用の外部データセット、またはマイニング モデルのケース データを使用できます。</span><span class="sxs-lookup"><span data-stu-id="c396b-104">The data set can be an external data set used for testing, or the case data for a mining model.</span></span> <span data-ttu-id="c396b-105">フィルターの対象が外部データセットかマイニング モデルかによって、ダイアログ ボックスの名前が異なります。</span><span class="sxs-lookup"><span data-stu-id="c396b-105">The name of the dialog box changes depending on whether the filter is for an external data set or for a mining model.</span></span>  
  
 <span data-ttu-id="c396b-106">フィルターを新しいデータセットに適用した場合、データセット内で条件を満たすケースのみを使用してデータ マイニング モデルが評価されます。</span><span class="sxs-lookup"><span data-stu-id="c396b-106">If you apply the filter to a new data set, the data mining model is evaluated by using only those cases in the data set that meet the conditions.</span></span> <span data-ttu-id="c396b-107">フィルターをマイニング モデル自体に適用した場合、既存のテスト データセット内でフィルター条件を満たすケースのみを使用してモデルがトレーニングおよびテストされます。</span><span class="sxs-lookup"><span data-stu-id="c396b-107">If you apply the filter to the mining model itself, the model will be trained and tested by using only the cases in the existing test data set that meet the filter criteria.</span></span>  
  
-   <span data-ttu-id="c396b-108">**[データセット フィルター]** ダイアログ ボックスは、 **[マイニング精度チャート]** デザイナーの **[入力の選択]** タブから開くことができます。</span><span class="sxs-lookup"><span data-stu-id="c396b-108">The **Data Set Filter** dialog box is available from the **Input Selection** tab of the **Mining Accuracy Chart** designer.</span></span>  
  
-   <span data-ttu-id="c396b-109">**[モデル フィルター]** ダイアログ ボックスは、データ マイニング デザイナーの **[マイニング モデル]** タブから開くことができます。</span><span class="sxs-lookup"><span data-stu-id="c396b-109">The **Model Filter** dialog box is available from the **Mining Models** tab of the Data Miningdesigner.</span></span>  
  
-   <span data-ttu-id="c396b-110">**[条件]** グリッドには、テーブル名または列名、演算子、およびターゲット値を指定するための列があります。</span><span class="sxs-lookup"><span data-stu-id="c396b-110">The **Conditions** grid contains columns where you can specify a table or column name, an operator, and target values.</span></span> <span data-ttu-id="c396b-111">基本的に、このグリッドを使用することは、WHERE 句を作成することになります。</span><span class="sxs-lookup"><span data-stu-id="c396b-111">By using this grid you are essentially creating a WHERE clause.</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="c396b-112">元のトレーニング データのサブセットを使用して精度をテストするには、トレーニング セットを定義するときに使用したデータ ソース ビューを外部テスト データとして追加し、次に条件を **[データセット フィルター]** グリッドに追加します。</span><span class="sxs-lookup"><span data-stu-id="c396b-112">To test accuracy on a subset of the original training data, you can add the data source view that was used to define the training set as the external testing data, and then add conditions in the **Data Set Filter** grid.</span></span>  
  
 <span data-ttu-id="c396b-113">**詳細情報: 「** [テストおよび検証 &#40;データ マイニング&#41;](data-mining/testing-and-validation-data-mining.md)」</span><span class="sxs-lookup"><span data-stu-id="c396b-113">**For more information:** [Testing and Validation &#40;Data Mining&#41;](data-mining/testing-and-validation-data-mining.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="c396b-114">Options</span><span class="sxs-lookup"><span data-stu-id="c396b-114">Options</span></span>  
 <span data-ttu-id="c396b-115">**条件**</span><span class="sxs-lookup"><span data-stu-id="c396b-115">**Conditions**</span></span>  
 <span data-ttu-id="c396b-116">テーブル名に続いて列名と条件が表示されます。</span><span class="sxs-lookup"><span data-stu-id="c396b-116">Displays table names, followed by column names with conditions.</span></span>  
  
|<span data-ttu-id="c396b-117">値</span><span class="sxs-lookup"><span data-stu-id="c396b-117">Value</span></span>|<span data-ttu-id="c396b-118">説明</span><span class="sxs-lookup"><span data-stu-id="c396b-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c396b-119">**And/Or**</span><span class="sxs-lookup"><span data-stu-id="c396b-119">**And/Or**</span></span>|<span data-ttu-id="c396b-120">複数の条件を結合する演算子を選択します。</span><span class="sxs-lookup"><span data-stu-id="c396b-120">Choose an operator to join multiple conditions.</span></span>|  
|<span data-ttu-id="c396b-121">**[マイニング構造列]**</span><span class="sxs-lookup"><span data-stu-id="c396b-121">**Mining Structure Column**</span></span>|<span data-ttu-id="c396b-122">クリックして、データ ソースを選択します。次に、グリッド内の連続する行をクリックして、追加するデータ ソースの列を選択します。</span><span class="sxs-lookup"><span data-stu-id="c396b-122">Click to select a data source, and then click successive lines in the grid to add columns from the data source.</span></span><br /><br /> <span data-ttu-id="c396b-123">グリッドの最初の行は、データ ソース ビューを指定します。</span><span class="sxs-lookup"><span data-stu-id="c396b-123">The first line in the grid specifies the data source view.</span></span> <span data-ttu-id="c396b-124">データ ソース ビューを選択すると、 **[マイニング構造列]** にテーブル アイコンが表示され、 **[値]** フィールドにこのデータ ソースに対して定義されているすべての条件の組み合わせが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c396b-124">After you select a data source view, **Mining Structure Column** displays a table icon, and the **Value** field displays the combination of all criteria that you have defined for this data source.</span></span><br /><br /> <span data-ttu-id="c396b-125">データ ソースを選択すると、 **[マイニング構造列]** ボックスに、データ ソース内の個々の列を含むドロップダウン リストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c396b-125">After you have selected a data source, the **Mining Structure Column** box provides a dropdown list of individual columns in the data source.</span></span>|  
|<span data-ttu-id="c396b-126">**[オペレーター]**</span><span class="sxs-lookup"><span data-stu-id="c396b-126">**Operator**</span></span>|<span data-ttu-id="c396b-127">一覧から演算子を選択します。</span><span class="sxs-lookup"><span data-stu-id="c396b-127">Select an operator from the list.</span></span>|  
|<span data-ttu-id="c396b-128">**Value**</span><span class="sxs-lookup"><span data-stu-id="c396b-128">**Value**</span></span>|<span data-ttu-id="c396b-129">テーブルの場合、データ ソースに適用されるすべてのフィルターの組み合わせが **[値]** フィールドに表示されます。</span><span class="sxs-lookup"><span data-stu-id="c396b-129">For tables, the **Value** field shows the combination of all filters applied to the data source.</span></span> <span data-ttu-id="c396b-130">また、テキストボックスの右側にあるビルドボタン **([...])** をクリックして [**フィルター** ] ダイアログボックスを開き、条件を作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="c396b-130">You can also click the build **(...)** button at the right of the text box to open the **Filter** dialog box and build a condition.</span></span>|  
  
 <span data-ttu-id="c396b-131">**[式]**</span><span class="sxs-lookup"><span data-stu-id="c396b-131">**Expression**</span></span>  
 <span data-ttu-id="c396b-132">グリッドを使用して作成した条件のセットが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c396b-132">Displays the set of criteria that you built by using the grid.</span></span>  
  
 <span data-ttu-id="c396b-133">**クエリの編集**</span><span class="sxs-lookup"><span data-stu-id="c396b-133">**Edit Query**</span></span>  
 <span data-ttu-id="c396b-134">フィルター編集モードを変更して、フィルター式を **[式]** テキスト ボックスに直接入力できるようにします。</span><span class="sxs-lookup"><span data-stu-id="c396b-134">Changes the filter editing mode so that you can type a filter expression directly in the **Expression** text box.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c396b-135">フィルター式に手動で変更を加えた後は、[**入力の選択**] タブの [**フィルター式**] ボックスに式を保存した後でも、グリッド編集モードに戻ることはできません。グリッドを使用して式を作成する場合は、既存のフィルター式を削除してからやり直す必要があります。</span><span class="sxs-lookup"><span data-stu-id="c396b-135">After you have made manual changes to the filter expression, you cannot return to grid edit mode, even after you have saved the expression in the **Filter Expression** box on the **Input Selection** tab. If you want to build an expression by using the grid, you must delete the existing filter expression and start over.</span></span>  
  
 <span data-ttu-id="c396b-136">**[クエリの編集を元に戻す]**</span><span class="sxs-lookup"><span data-stu-id="c396b-136">**Revert Query Edits**</span></span>  
 <span data-ttu-id="c396b-137">グリッドを直前の状態に戻し、フィルター式に加えた変更を取り消します。</span><span class="sxs-lookup"><span data-stu-id="c396b-137">Restores the grid to its previous state and cancels any changes that you made to the filter expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c396b-138">参照</span><span class="sxs-lookup"><span data-stu-id="c396b-138">See Also</span></span>  
 <span data-ttu-id="c396b-139">[テストと検証のタスクと操作方法 &#40;データマイニング&#41;](data-mining/testing-and-validation-tasks-and-how-tos-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="c396b-139">[Testing and Validation Tasks and How-tos &#40;Data Mining&#41;](data-mining/testing-and-validation-tasks-and-how-tos-data-mining.md) </span></span>  
 [<span data-ttu-id="c396b-140">マイニング精度チャートデザイナー &#40;データマイニング&#41;</span><span class="sxs-lookup"><span data-stu-id="c396b-140">Mining Accuracy Chart Designer &#40;Data Mining&#41;</span></span>](mining-accuracy-chart-designer-data-mining.md)  
  
  
