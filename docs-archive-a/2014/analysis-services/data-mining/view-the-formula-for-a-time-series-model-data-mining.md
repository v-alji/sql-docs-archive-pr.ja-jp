---
title: タイムシリーズモデルの式の表示 (データマイニング) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data mining [Analysis Services], how-to topics
- ARTXP
- time series algorithms [Analysis Services]
- ARIMA
- time series [Analysis Services]
- Time Series Viewer [Analysis Services]
ms.assetid: 825ef719-2f44-4979-be01-5a81f54e1a53
author: minewiskan
ms.author: owend
ms.openlocfilehash: eff61c469d34f084e6a0eb11c49a1c37c7cc97c4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631332"
---
# <a name="view-the-formula-for-a-time-series-model-data-mining"></a><span data-ttu-id="1018a-102">タイム シリーズ モデルの式の表示 (データ マイニング)</span><span class="sxs-lookup"><span data-stu-id="1018a-102">View the Formula for a Time Series Model (Data Mining)</span></span>
  <span data-ttu-id="1018a-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)]タイムシリーズビューアーの inData マイニングデザイナーでは、タイムシリーズモデルで使用される回帰式の詳細を最も簡単に表示できます。</span><span class="sxs-lookup"><span data-stu-id="1018a-103">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Time Series viewer inData Mining Designer provides the easiest way to view the details of the regression equation used in a time series model.</span></span>  
  
 <span data-ttu-id="1018a-104">モデル コンテンツのクエリを実行することで、タイム シリーズ モデルの回帰式を抽出できます。</span><span class="sxs-lookup"><span data-stu-id="1018a-104">You can extract the regression formula for a time series model by querying the model content.</span></span> <span data-ttu-id="1018a-105">ただし、ARTXP または ARIMA の完全な式を表示するには、 [Microsoft タイムシリーズビューアー](browse-a-model-using-the-microsoft-time-series-viewer.md)の [**マイニング凡例**] を使用することをお勧めします。これにより、すべての定数が読み取り可能な形式で表示されます。</span><span class="sxs-lookup"><span data-stu-id="1018a-105">However, to view the complete ARTXP or ARIMA formula, we recommend that you use the **Mining Legend** of the [Microsoft Time Series Viewer](browse-a-model-using-the-microsoft-time-series-viewer.md), which presents all the constants in a readable format.</span></span>  
  
 <span data-ttu-id="1018a-106">混合モデルを作成した場合は、ARIMA と ARTXP の分析が個別のツリーに作成され、モデルを表すルート ノードで結合されます。</span><span class="sxs-lookup"><span data-stu-id="1018a-106">If you create a mixed model, the ARIMA and ARTXP analyses are created in separate trees, joined at the root node representing the model.</span></span> <span data-ttu-id="1018a-107">ARIMA と ARTXP のツリーの構造は非常に異なります。</span><span class="sxs-lookup"><span data-stu-id="1018a-107">The structures of the ARIMA and ARTXP trees are very different.</span></span> <span data-ttu-id="1018a-108">たとえば、ARTXP ツリーは実際にはデシジョン ツリーのようなツリー構造ですが、ARIMA ツリーは一連の移動平均を表します。</span><span class="sxs-lookup"><span data-stu-id="1018a-108">For example, the ARTXP tree is in fact a tree structure, like a decision tree, whereas the ARIMA tree represents a series of moving averages.</span></span> <span data-ttu-id="1018a-109">したがって、この 2 つの表現は、便宜上 1 つのモデルで提示されていますが、2 つの独立したモデルとして扱う必要があります。</span><span class="sxs-lookup"><span data-stu-id="1018a-109">Therefore, although the two representations are presented in one model for convenience, they should be treated as two independent models.</span></span> <span data-ttu-id="1018a-110">式もまったく別のものであり、結合または比較することはできません。</span><span class="sxs-lookup"><span data-stu-id="1018a-110">The equations are also completely different and cannot be combined or compared.</span></span>  
  
 <span data-ttu-id="1018a-111">[Microsoft 汎用コンテンツツリービューアー](../microsoft-generic-content-tree-viewer-data-mining.md)を使用して、タイムシリーズモデルを表示することもできます。</span><span class="sxs-lookup"><span data-stu-id="1018a-111">You can also view time series models by using the [Microsoft Generic Content Tree Viewer](../microsoft-generic-content-tree-viewer-data-mining.md).</span></span> <span data-ttu-id="1018a-112">タイムシリーズモデルの内容の詳細については、「 [Analysis Services データマイニング&#41;&#40;タイムシリーズモデルのマイニングモデルコンテンツ](mining-model-content-for-time-series-models-analysis-services-data-mining.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1018a-112">For more information about the content of a time series model, see [Mining Model Content for Time Series Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-time-series-models-analysis-services-data-mining.md).</span></span>  
  
### <a name="to-view-the-artxp-regression-formula-for-a-time-series-model"></a><span data-ttu-id="1018a-113">タイム シリーズ モデルの ARTXP 回帰式を表示するには</span><span class="sxs-lookup"><span data-stu-id="1018a-113">To view the ARTXP regression formula for a time series model</span></span>  
  
1.  <span data-ttu-id="1018a-114">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、表示するタイム シリーズ モデルを選択して、 **[参照]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1018a-114">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], select the time series model that you want to view, and click **Browse**.</span></span>  
  
     <span data-ttu-id="1018a-115">-- または --</span><span class="sxs-lookup"><span data-stu-id="1018a-115">-- or --</span></span>  
  
     <span data-ttu-id="1018a-116">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、タイム シリーズ モデルを選択して、 **[マイニング モデル ビューアー]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="1018a-116">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], select the time series model, and then click the **Mining Model Viewer** tab.</span></span>  
  
2.  <span data-ttu-id="1018a-117">**[Model (モデル)]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="1018a-117">Click the **Model** tab.</span></span>  
  
3.  <span data-ttu-id="1018a-118">モデルに複数のツリーが含まれる場合は、 **[ツリー]** ボックスの一覧で 1 つのツリーを選択します。</span><span class="sxs-lookup"><span data-stu-id="1018a-118">If the model contains multiple trees, select a single tree from the **Tree** drop-down list.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="1018a-119">複数のデータ系列がある場合、モデルには必ず複数のツリーが含まれます。</span><span class="sxs-lookup"><span data-stu-id="1018a-119">A model will always have multiple trees if you have more than one data series.</span></span> <span data-ttu-id="1018a-120">ただし、 **タイム シリーズ ビューアー** では、 [Microsoft 汎用コンテンツ ツリー ビューアー](../microsoft-generic-content-tree-viewer-data-mining.md)ほど多くのツリーは表示されません。</span><span class="sxs-lookup"><span data-stu-id="1018a-120">However, you will not see as many trees in the **Time Series viewer** as you will see in the [Microsoft Generic Content Tree Viewer](../microsoft-generic-content-tree-viewer-data-mining.md).</span></span> <span data-ttu-id="1018a-121">これは、タイム シリーズ ビューアーが、データ系列ごとに ARIMA と ARTXP の情報を 1 つの表現にまとめるためです。</span><span class="sxs-lookup"><span data-stu-id="1018a-121">That is because the Time Series viewer combines the ARIMA and ARTXP information for each data series into a single representation.</span></span>  
  
4.  <span data-ttu-id="1018a-122">ツリーの任意のリーフ ノードをクリックします。</span><span class="sxs-lookup"><span data-stu-id="1018a-122">Click any leaf node in the tree.</span></span>  
  
     <span data-ttu-id="1018a-123">**[データ系列]** というラベルのノードは常にリーフ ノードであり、式を含むことができます。</span><span class="sxs-lookup"><span data-stu-id="1018a-123">Nodes that are labeled as **Data Series** are always leaf nodes and can contain an equation.</span></span> <span data-ttu-id="1018a-124">**[(すべて)]** ノードに子ノードがない場合も、式を含むことができます。</span><span class="sxs-lookup"><span data-stu-id="1018a-124">If an **(All)** node has no child nodes, it can also contain an equation.</span></span>  
  
5.  <span data-ttu-id="1018a-125">**[マイニング凡例]** が表示されない場合は、ノードを右クリックし、 **[凡例の表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1018a-125">If the **Mining Legend** is not available, right-click the node, and select **Show Legend**.</span></span>  
  
     <span data-ttu-id="1018a-126">ARTXP 式は、 **[マイニング凡例]** の前半に、 **[ツリー ノード式]** として表示されます。</span><span class="sxs-lookup"><span data-stu-id="1018a-126">The ARTXP formula is displayed in the first half of the **Mining Legend**, as the **Tree node equation**.</span></span>  
  
### <a name="to-view-the-arima-formula-for-a-time-series-model"></a><span data-ttu-id="1018a-127">タイム シリーズ モデルの ARIMA 式を表示するには</span><span class="sxs-lookup"><span data-stu-id="1018a-127">To view the ARIMA formula for a time series model</span></span>  
  
1.  <span data-ttu-id="1018a-128">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、表示するタイム シリーズ モデルを選択して、 **[参照]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1018a-128">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], select the time series model that you want to view, and click **Browse**.</span></span>  
  
     <span data-ttu-id="1018a-129">-- または --</span><span class="sxs-lookup"><span data-stu-id="1018a-129">-- or --</span></span>  
  
     <span data-ttu-id="1018a-130">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、タイム シリーズ モデルを選択して、 **[マイニング モデル ビューアー]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="1018a-130">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], select the time series model, and then click the **Mining Model Viewer** tab.</span></span>  
  
2.  <span data-ttu-id="1018a-131">**[Model (モデル)]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="1018a-131">Click the **Model** tab.</span></span>  
  
3.  <span data-ttu-id="1018a-132">モデルに複数のツリーが含まれる場合は、 **[ツリー]** ボックスの一覧で 1 つのツリーを選択します。</span><span class="sxs-lookup"><span data-stu-id="1018a-132">If the model contains multiple trees, select a single tree from the **Tree** drop-down list.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="1018a-133">複数のデータ系列がある場合、モデルには必ず複数のツリーが含まれます。</span><span class="sxs-lookup"><span data-stu-id="1018a-133">The model will always have multiple trees if you include more than one data series.</span></span>  
  
4.  <span data-ttu-id="1018a-134">ツリーの任意のノードをクリックします。</span><span class="sxs-lookup"><span data-stu-id="1018a-134">Click any node in the tree.</span></span>  
  
     <span data-ttu-id="1018a-135">ARIMA 式は、 **[マイニング凡例]** の後半に、 **[ARIMA 式]** として表示されます。</span><span class="sxs-lookup"><span data-stu-id="1018a-135">The ARIMA formula is displayed in the second half of the **Mining Legend**, as the **ARIMA equation**.</span></span>  
  
5.  <span data-ttu-id="1018a-136">**[マイニング凡例]** が表示されない場合は、ノードを右クリックし、 **[凡例の表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1018a-136">If the **Mining Legend** is not available, right-click the node, and select **Show Legend**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1018a-137">参照</span><span class="sxs-lookup"><span data-stu-id="1018a-137">See Also</span></span>  
 <span data-ttu-id="1018a-138">[マイニングモデルビューアーのタスクと操作方法](mining-model-viewer-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="1018a-138">[Mining Model Viewer Tasks and How-tos](mining-model-viewer-tasks-and-how-tos.md) </span></span>  
 <span data-ttu-id="1018a-139">[Microsoft タイムシリーズビューアーを使用したモデルの参照](browse-a-model-using-the-microsoft-time-series-viewer.md) </span><span class="sxs-lookup"><span data-stu-id="1018a-139">[Browse a Model Using the Microsoft Time Series Viewer](browse-a-model-using-the-microsoft-time-series-viewer.md) </span></span>  
 [<span data-ttu-id="1018a-140">Time Series Model Query Examples</span><span class="sxs-lookup"><span data-stu-id="1018a-140">Time Series Model Query Examples</span></span>](time-series-model-query-examples.md)  
  
  
