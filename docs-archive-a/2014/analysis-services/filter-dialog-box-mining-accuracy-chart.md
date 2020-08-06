---
title: '[フィルター] ダイアログボックス (マイニング精度チャート) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 71e884a9-7ec4-4459-a4c4-87f6c796d478
author: minewiskan
ms.author: owend
ms.openlocfilehash: dcdfb7cd7b425c3f8c4711e8b1812afc12898e1d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643010"
---
# <a name="filter-dialog-box-mining-accuracy-chart"></a><span data-ttu-id="49021-102">[フィルター] ダイアログ ボックス (マイニング精度チャート)</span><span class="sxs-lookup"><span data-stu-id="49021-102">Filter Dialog Box (Mining Accuracy Chart)</span></span>
  <span data-ttu-id="49021-103">**[フィルター]** ダイアログ ボックスを使用すると、データセットに適用できる条件を作成できます。</span><span class="sxs-lookup"><span data-stu-id="49021-103">The **Filter** dialog box helps you build conditions that you can apply to a data set.</span></span> <span data-ttu-id="49021-104">データセットとして、テスト用の外部データセット、またはマイニング モデルのトレーニング用のケース データを使用できます。</span><span class="sxs-lookup"><span data-stu-id="49021-104">The data set can be an external data set used for testing, or the case data used to train a mining model.</span></span> <span data-ttu-id="49021-105">このダイアログ ボックスで作成する条件は、 **[データセット フィルター]** ダイアログ ボックスまたは **[モデル フィルター]** ダイアログ ボックスで複雑なフィルター条件の一部として保存できます。</span><span class="sxs-lookup"><span data-stu-id="49021-105">This dialog box helps you build criteria that you can save as part of more complex filter criteria in either the **Data Set Filter** dialog box or the **Model Filter** dialog box.</span></span>  
  
-   <span data-ttu-id="49021-106">**[データセット フィルター]** ダイアログ ボックスは、 **[マイニング精度チャート]** デザイナーの **[入力の選択]** タブから開くことができます。</span><span class="sxs-lookup"><span data-stu-id="49021-106">The **Data Set Filter** dialog box is available from the **Input Selection** tab of the **Mining Accuracy Chart** designer.</span></span>  
  
-   <span data-ttu-id="49021-107">**[モデル フィルター]** ダイアログ ボックスは、データ マイニング デザイナーの **[マイニング モデル]** タブから開くことができます。</span><span class="sxs-lookup"><span data-stu-id="49021-107">The **Model Filter** dialog box is available from the **Mining Models** tab of the Data Mining designer.</span></span>  
  
 <span data-ttu-id="49021-108">フィルターをマイニング モデルに適用する場合、最初に **[モデル フィルター]** ダイアログ ボックスでテーブルを選択します。</span><span class="sxs-lookup"><span data-stu-id="49021-108">If you are applying a filter to a mining model, first you use the **Model Filter** dialog box to choose a table.</span></span> <span data-ttu-id="49021-109">次に **[フィルター]** ダイアログ ボックスで、そのテーブルのみに適用する条件を作成できます。</span><span class="sxs-lookup"><span data-stu-id="49021-109">Then, you can use the **Filter** dialog box to build conditions that apply only to that table.</span></span>  
  
 <span data-ttu-id="49021-110">外部テスト データセットに適用するフィルターを作成する場合、最初に **[データセット フィルター]** ダイアログ ボックスで、データ ソース ビュー内のテーブルの一覧からテーブルを選択します。</span><span class="sxs-lookup"><span data-stu-id="49021-110">If you are creating a filter to apply to an external test data set, first you use the **Data Set Filter** dialog box to choose a table from the list of tables in a data source view.</span></span> <span data-ttu-id="49021-111">次に **[フィルター]** ダイアログ ボックスで、そのテーブルのみに適用する条件を作成します。</span><span class="sxs-lookup"><span data-stu-id="49021-111">Then, you use the **Filter** dialog box to build conditions that apply only to that table.</span></span>  
  
 <span data-ttu-id="49021-112">1 つのテーブルに適用する条件のセットを作成したら、 [!INCLUDE[clickOK](../includes/clickok-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="49021-112">After you have created a set of conditions that apply to a single table, [!INCLUDE[clickOK](../includes/clickok-md.md)].</span></span> <span data-ttu-id="49021-113">**[フィルター]** ダイアログ ボックスで行った変更内容は、親ダイアログ ボックスである **[データセット フィルター]** または **[モデル フィルター]** のフィルター式に自動的に追加されます。</span><span class="sxs-lookup"><span data-stu-id="49021-113">The changes that you made in the **Filter** dialog box are automatically added to the filter expression in the parent dialog box, **Data Set Filter** or **Model Filter**.</span></span>  
  
 <span data-ttu-id="49021-114">フィルターを新しいデータセットに適用した場合、データセット内で条件を満たすケースのみを評価するために、既存のデータ マイニング モデルが使用されます。</span><span class="sxs-lookup"><span data-stu-id="49021-114">If you apply the filter to the new data set, the existing data mining model is used to evaluate only those cases in the data set that meet the conditions.</span></span> <span data-ttu-id="49021-115">ただし、フィルターをマイニング モデル自体に適用した場合、モデルの精度はマイニング モデル内で条件を満たすケースについてのみ評価されます。</span><span class="sxs-lookup"><span data-stu-id="49021-115">However, if you apply the filter to the mining model itself, the accuracy of the model is assessed for only those cases within the mining model that meet those criteria.</span></span>  
  
 <span data-ttu-id="49021-116">**詳細情報: 「** [テストおよび検証 &#40;データ マイニング&#41;](data-mining/testing-and-validation-data-mining.md)」</span><span class="sxs-lookup"><span data-stu-id="49021-116">**For more information:** [Testing and Validation &#40;Data Mining&#41;](data-mining/testing-and-validation-data-mining.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="49021-117">Options</span><span class="sxs-lookup"><span data-stu-id="49021-117">Options</span></span>  
 <span data-ttu-id="49021-118">**条件**</span><span class="sxs-lookup"><span data-stu-id="49021-118">**Conditions**</span></span>  
 <span data-ttu-id="49021-119">グリッドには、 **[データセット フィルター]** ダイアログ ボックスで選択したテーブルの列に対して条件を指定するための列があります。</span><span class="sxs-lookup"><span data-stu-id="49021-119">A grid that contains columns where you specify conditions on columns from the table that you selected in the **Data Set Filter** dialog box.</span></span>  
  
|<span data-ttu-id="49021-120">値</span><span class="sxs-lookup"><span data-stu-id="49021-120">Value</span></span>|<span data-ttu-id="49021-121">説明</span><span class="sxs-lookup"><span data-stu-id="49021-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="49021-122">**And/Or**</span><span class="sxs-lookup"><span data-stu-id="49021-122">**And/Or**</span></span>|<span data-ttu-id="49021-123">この行の条件に AND 演算子または OR 演算子を適用するかどうかを指定する場合にクリックします。</span><span class="sxs-lookup"><span data-stu-id="49021-123">Click to specify whether to apply the AND operator or the OR operator to the condition on this line.</span></span> <span data-ttu-id="49021-124">この値は **[マイニング構造列]** リストで列を選択すると有効になります。</span><span class="sxs-lookup"><span data-stu-id="49021-124">These values become available only after you have selected a column from the **Mining Structure Column** list.</span></span>|  
|<span data-ttu-id="49021-125">**[マイニング構造列]**</span><span class="sxs-lookup"><span data-stu-id="49021-125">**Mining Structure Column**</span></span>|<span data-ttu-id="49021-126">**[データセット フィルター]** ダイアログ ボックスでデータ ソースから選択したテーブルに含まれる列の一覧から列を選択する場合にクリックします。</span><span class="sxs-lookup"><span data-stu-id="49021-126">Click to select a column from the list of the columns contained in the table that you selected from the data source in the **Data Set Filter** dialog box.</span></span>|  
|<span data-ttu-id="49021-127">**[オペレーター]**</span><span class="sxs-lookup"><span data-stu-id="49021-127">**Operator**</span></span>|<span data-ttu-id="49021-128">一覧から演算子を選択します。</span><span class="sxs-lookup"><span data-stu-id="49021-128">Select an operator from the list.</span></span> <span data-ttu-id="49021-129">使用できる演算子は、列のデータ型によって異なります。</span><span class="sxs-lookup"><span data-stu-id="49021-129">The operators that are available depend on the data type of the column.</span></span><br /><br /> <span data-ttu-id="49021-130">列に不連続値が含まれる場合は、次の演算子のみを指定できます。</span><span class="sxs-lookup"><span data-stu-id="49021-130">If the column contains discrete values, only the following operators are available:</span></span><br /><br /> <span data-ttu-id="49021-131">= (等しい)、<> (等しくない)、IS NOT NULL、IS NULL.</span><span class="sxs-lookup"><span data-stu-id="49021-131">= (equal to), <> (not equal to), IS NOT NULL, IS NULL.</span></span><br /><br /> <span data-ttu-id="49021-132">列に連続値が含まれる場合は、より大きい、より小さいの演算子もサポートされます。</span><span class="sxs-lookup"><span data-stu-id="49021-132">If the column contains continuous values, operators for greater than and less than operations are also supported.</span></span>|  
|<span data-ttu-id="49021-133">**Value**</span><span class="sxs-lookup"><span data-stu-id="49021-133">**Value**</span></span>|<span data-ttu-id="49021-134">条件として使用する値を入力します。</span><span class="sxs-lookup"><span data-stu-id="49021-134">Type a value to use as a condition.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="49021-135">参照</span><span class="sxs-lookup"><span data-stu-id="49021-135">See Also</span></span>  
 <span data-ttu-id="49021-136">[テストと検証のタスクと操作方法 &#40;データマイニング&#41;](data-mining/testing-and-validation-tasks-and-how-tos-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="49021-136">[Testing and Validation Tasks and How-tos &#40;Data Mining&#41;](data-mining/testing-and-validation-tasks-and-how-tos-data-mining.md) </span></span>  
 [<span data-ttu-id="49021-137">マイニング精度チャートデザイナー &#40;データマイニング&#41;</span><span class="sxs-lookup"><span data-stu-id="49021-137">Mining Accuracy Chart Designer &#40;Data Mining&#41;</span></span>](mining-accuracy-chart-designer-data-mining.md)  
  
  
