---
title: マイニングモデルのプロパティの変更 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models [Analysis Services], properties
- properties [data mining]
ms.assetid: aefaeb7f-d174-48d1-a188-0987a3b1196b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 395e6a4cb9c0f0dac0f0c717dfe0695033cad050
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632187"
---
# <a name="change-the-properties-of-a-mining-model"></a><span data-ttu-id="b4d5c-102">マイニング モデルのプロパティの変更</span><span class="sxs-lookup"><span data-stu-id="b4d5c-102">Change the Properties of a Mining Model</span></span>
  <span data-ttu-id="b4d5c-103">マイニング モデルのプロパティには、モデル全体に適用されるものと個別の列に適用されるものがあります。</span><span class="sxs-lookup"><span data-stu-id="b4d5c-103">Some mining model properties apply to the model as a whole, and other model properties apply to individual columns.</span></span> <span data-ttu-id="b4d5c-104">モデル全体に適用されるプロパティの例は、ケース データをクエリで使用可能にする必要があるかどうかを指定する `Drillthrough` プロパティと、`Description` プロパティです。</span><span class="sxs-lookup"><span data-stu-id="b4d5c-104">Examples of properties that apply to the entire model would be the `Drillthrough` property, which specifies whether the case data should be available for querying, and the `Description` property.</span></span> <span data-ttu-id="b4d5c-105">列に適用されるプロパティには、モデル内で列のデータが使用される方法を制御する `Usage` および `ModelingFlags` があります。</span><span class="sxs-lookup"><span data-stu-id="b4d5c-105">Properties that apply to the column include `Usage` and `ModelingFlags`, which control how data in the column is used within the model.</span></span>  
  
 <span data-ttu-id="b4d5c-106">次のモデル プロパティには、式の作成または複雑なモデル プロパティの構成に使用できる高度なエディターがあります。</span><span class="sxs-lookup"><span data-stu-id="b4d5c-106">The following model properties have advanced editors that you can use to create expressions or configure complex model properties.</span></span> <span data-ttu-id="b4d5c-107">プロパティには次の機能があります。</span><span class="sxs-lookup"><span data-stu-id="b4d5c-107">The following properties provide:</span></span>  
  
-   <span data-ttu-id="b4d5c-108">`Filter`[プロパティ]: [[データセットフィルター] または [モデルフィルター] ダイアログボックス](../data-set-filter-or-model-filter-dialog-box.md)を開きます。</span><span class="sxs-lookup"><span data-stu-id="b4d5c-108">`Filter` property: Opens the [Data Set Filter or Model Filter Dialog Box](../data-set-filter-or-model-filter-dialog-box.md).</span></span>  
  
-   <span data-ttu-id="b4d5c-109">`AlgorithmParameters`[プロパティ]: [[マイニングモデルビュー&#41;&#40;[アルゴリズムパラメーター] ダイアログボックス](../algorithm-parameters-dialog-box-mining-models-view.md)が表示されます。</span><span class="sxs-lookup"><span data-stu-id="b4d5c-109">`AlgorithmParameters` property: Opens the [Algorithm Parameters Dialog Box &#40;Mining Models View&#41;](../algorithm-parameters-dialog-box-mining-models-view.md).</span></span>  
  
 <span data-ttu-id="b4d5c-110">マイニング モデルのプロパティを設定する方法については、「 [マイニング モデル列](mining-model-columns.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b4d5c-110">For information about how to set the properties in a mining model, see [Mining Model Columns](mining-model-columns.md).</span></span>  
  
### <a name="to-change-the-properties-of-a-mining-model"></a><span data-ttu-id="b4d5c-111">マイニング モデルのプロパティを変更するには</span><span class="sxs-lookup"><span data-stu-id="b4d5c-111">To change the properties of a mining model</span></span>  
  
1.  <span data-ttu-id="b4d5c-112">データ マイニング デザイナーの **[マイニング モデル]** タブで、マイニング モデル名を含む列ヘッダーか、マイニング アルゴリズム名を含むグリッドの行のいずれかを右クリックし、 **[プロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="b4d5c-112">In the **Mining Models** tab in Data Mining Designer, right-click either the column header that contains the name of the mining model, or the row in the grid that contains the name of the mining algorithm, and then select **Properties**.</span></span>  
  
2.  <span data-ttu-id="b4d5c-113">画面の右側の **[プロパティ]** ウィンドウで、変更するプロパティに対応する値を強調表示し、新しい値を入力します。</span><span class="sxs-lookup"><span data-stu-id="b4d5c-113">In the **Properties** window on the right side of the screen, highlight the value that corresponds to the property that you want to change, and enter the new value.</span></span>  
  
     <span data-ttu-id="b4d5c-114">新しい値は、デザイナーで別の要素を選択したときに有効になります。</span><span class="sxs-lookup"><span data-stu-id="b4d5c-114">The new value will take effect when you select a different element in the designer.</span></span>  
  
### <a name="to-change-the-properties-of-a-mining-model-column"></a><span data-ttu-id="b4d5c-115">マイニング モデル列のプロパティを変更するには</span><span class="sxs-lookup"><span data-stu-id="b4d5c-115">To change the properties of a mining model column</span></span>  
  
1.  <span data-ttu-id="b4d5c-116">データ マイニング デザイナーの **[マイニング モデル]** タブで、マイニング構造列とマイニング モデルが交差するグリッド内のセルを右クリックし、 **[プロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="b4d5c-116">In the **Mining Models** tab in Data Mining Designer, right-click the cell in the grid at the intersection of the mining structure column and the mining model, and then select **Properties**.</span></span>  
  
2.  <span data-ttu-id="b4d5c-117">画面の右側の **[プロパティ]** ウィンドウで、変更するプロパティに対応する値を強調表示し、新しい値を入力します。</span><span class="sxs-lookup"><span data-stu-id="b4d5c-117">In the **Properties** window on the right side of the screen, highlight the value that corresponds to the property that you want to change, and enter the new value.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b4d5c-118">列の使用法がに設定されている場合 `Ignore` 、列の [**プロパティ**] ウィンドウは空白になります。</span><span class="sxs-lookup"><span data-stu-id="b4d5c-118">If the column usage is set to `Ignore`, the **Properties** window for the column is blank.</span></span>  
  
     <span data-ttu-id="b4d5c-119">新しい値は、デザイナーで別の要素を選択したときに有効になります。</span><span class="sxs-lookup"><span data-stu-id="b4d5c-119">The new value will take effect when you select a different element in the designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4d5c-120">参照</span><span class="sxs-lookup"><span data-stu-id="b4d5c-120">See Also</span></span>  
 [<span data-ttu-id="b4d5c-121">マイニング モデル タスクと操作方法</span><span class="sxs-lookup"><span data-stu-id="b4d5c-121">Mining Model Tasks and How-tos</span></span>](mining-model-tasks-and-how-tos.md)  
  
  
