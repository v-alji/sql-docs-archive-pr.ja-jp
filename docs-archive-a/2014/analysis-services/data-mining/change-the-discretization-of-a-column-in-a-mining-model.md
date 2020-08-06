---
title: マイニングモデルの列の分離を変更する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- discretization [Analysis Services]
- mining structures [Analysis Services], how-to topics
- discretized columns [data mining]
- bucketing problems [Analysis Services]
ms.assetid: 3c49862b-595d-4fa4-b890-e2e1bde1d74f
author: minewiskan
ms.author: owend
ms.openlocfilehash: 25b20d6428afac5c1492fdc74aafd4d0c010159d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644238"
---
# <a name="change-the-discretization-of-a-column-in-a-mining-model"></a><span data-ttu-id="de2cc-102">マイニング モデルでの列の分離の変更</span><span class="sxs-lookup"><span data-stu-id="de2cc-102">Change the Discretization of a Column in a Mining Model</span></span>
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]<span data-ttu-id="de2cc-103">値を自動的に分離します。つまり、特定のシナリオでは、数値列にデータをビン分割します。</span><span class="sxs-lookup"><span data-stu-id="de2cc-103">automatically discretizes values-that is to say, it bins data in numeric column-in certain scenarios.</span></span> <span data-ttu-id="de2cc-104">たとえば、データに連続する数値データが含まれている場合にデシジョン ツリー モデルを作成すると、データの分布に応じて、連続するデータの各列が自動的にビン分割されます。</span><span class="sxs-lookup"><span data-stu-id="de2cc-104">For example, if your data contains continuous numeric data and you create a decision tree model, each column of continuous data will be automatically binned, depending on the distribution of the data.</span></span> <span data-ttu-id="de2cc-105">データの分離方法を制御するには、モデルでのデータの使用方法を制御するマイニング構造列のプロパティを変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="de2cc-105">If you want to control how the data is discretized, you must change the properties on the mining structure column that control how the data is used in the model.</span></span>  
  
 <span data-ttu-id="de2cc-106">マイニング モデルでプロパティを設定する方法については、 [「マイニング モデル列」](mining-model-columns.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="de2cc-106">For general information about how to set the properties in a mining model, see [Mining Model Columns](mining-model-columns.md).</span></span>  
  
### <a name="to-display-the-properties-for-a-mining-model-column"></a><span data-ttu-id="de2cc-107">マイニング モデル列のプロパティを表示するには</span><span class="sxs-lookup"><span data-stu-id="de2cc-107">To display the properties for a mining model column</span></span>  
  
1.  <span data-ttu-id="de2cc-108">データ マイニング デザイナーの **[マイニング モデル]** タブで、マイニング モデル名を含む列ヘッダーか、マイニング アルゴリズム名を含むグリッドの行を右クリックし、 **[プロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="de2cc-108">In the **Mining Models** tab in Data Mining Designer, right-click the column header that contains the name of the mining model, or the row in the grid that contains the name of the mining algorithm, and then select **Properties**.</span></span>  
  
     <span data-ttu-id="de2cc-109">マイニング モデル全体に関連付けられているプロパティが、 **[プロパティ]** ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="de2cc-109">The **Properties** window displays the properties that are associated with the mining model as a whole.</span></span>  
  
2.  <span data-ttu-id="de2cc-110">画面の左側にある **[構造]** 列で、分離の対象となる連続する数値データを含んだ列をクリックします。</span><span class="sxs-lookup"><span data-stu-id="de2cc-110">In the **Structure** column near the left side of the screen, click the column that contains the continuous numeric data you want to discretize.</span></span>  
  
     <span data-ttu-id="de2cc-111">クリックした列に関連付けられているプロパティのみが **[プロパティ]** ウィンドウに表示されるようになります。</span><span class="sxs-lookup"><span data-stu-id="de2cc-111">The **Properties** window changes to display just the properties associated with that column.</span></span>  
  
### <a name="to-change-the-discretization-method"></a><span data-ttu-id="de2cc-112">分離メソッドを変更するには</span><span class="sxs-lookup"><span data-stu-id="de2cc-112">To change the discretization method</span></span>  
  
1.  <span data-ttu-id="de2cc-113">[**マイニングプロパティ**] ウィンドウで、[**コンテンツ**] の横にあるテキストボックスをクリックし、 `Discretized` ドロップダウンリストからを選択します。</span><span class="sxs-lookup"><span data-stu-id="de2cc-113">In the **Mining Properties** window, click the text box next to **Content**, and select `Discretized` from the dropdown list.</span></span>  
  
     <span data-ttu-id="de2cc-114">マイニング モデル全体に関連付けられているプロパティが、 <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationBucketCount%2A> プロパティと <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationMethod%2A> プロパティが有効になりました。</span><span class="sxs-lookup"><span data-stu-id="de2cc-114">The <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationBucketCount%2A> and <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationMethod%2A> properties are now enabled.</span></span>  
  
2.  <span data-ttu-id="de2cc-115">[**プロパティ**] ウィンドウで、の横にあるテキストボックスをクリックし、 <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationMethod%2A> 、、 `Automatic` またはのいずれかの値を選択します `EqualAreas` `Cluster` 。</span><span class="sxs-lookup"><span data-stu-id="de2cc-115">In the **Properties** window, click the text box next to <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationMethod%2A> and select one of the following values: `Automatic`, `EqualAreas`, or `Cluster`.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="de2cc-116">列の使用法がに設定されている場合 `Ignore` 、列の [**プロパティ**] ウィンドウは空白になります。</span><span class="sxs-lookup"><span data-stu-id="de2cc-116">If the column usage is set to `Ignore`, the **Properties** window for the column is blank.</span></span>  
  
     <span data-ttu-id="de2cc-117">新しい値は、デザイナーで別の要素を選択したときに有効になります。</span><span class="sxs-lookup"><span data-stu-id="de2cc-117">The new value will take effect when you select a different element in the designer.</span></span>  
  
3.  <span data-ttu-id="de2cc-118">データ マイニング デザイナーの **[プロパティ]** ウィンドウで、 <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationBucketCount%2A> の横にあるテキスト ボックスをクリックし、数値を入力します。</span><span class="sxs-lookup"><span data-stu-id="de2cc-118">In the **Properties** window, click the text box next to <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationBucketCount%2A> and type a numeric value.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="de2cc-119">これらのプロパティを変更した場合は、新しい設定を使用するモデルと共に構造を再処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="de2cc-119">If you change these properties, the structure must be reprocessed, along with any models that you want to use the new setting.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de2cc-120">参照</span><span class="sxs-lookup"><span data-stu-id="de2cc-120">See Also</span></span>  
 [<span data-ttu-id="de2cc-121">マイニング モデル タスクと操作方法</span><span class="sxs-lookup"><span data-stu-id="de2cc-121">Mining Model Tasks and How-tos</span></span>](mining-model-tasks-and-how-tos.md)  
  
  
