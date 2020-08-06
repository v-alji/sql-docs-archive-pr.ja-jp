---
title: データマイニングオブジェクトの処理 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- processing objects [Analysis Services]
- mining structures [Analysis Services]
- process [Analysis Services]
- mining structures [Analysis Services], creating
- mining structures [Analysis Services], how-to topics
- mining structures [Analysis Services], processing
ms.assetid: 0f6993c0-0917-4935-82f9-7b8a8a7cc627
author: minewiskan
ms.author: owend
ms.openlocfilehash: a4a6693a46679badc068111a311bb82219e752cd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718945"
---
# <a name="processing-data-mining-objects"></a><span data-ttu-id="c667c-102">データ マイニング オブジェクトの処理</span><span class="sxs-lookup"><span data-stu-id="c667c-102">Processing Data Mining Objects</span></span>
  <span data-ttu-id="c667c-103">データ マイニング オブジェクトは、処理されるまでは単なる空のコンテナーです。</span><span class="sxs-lookup"><span data-stu-id="c667c-103">A data mining object is only an empty container until it has been processed.</span></span> <span data-ttu-id="c667c-104">データ マイニング モデルの*処理* は *トレーニング*とも呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="c667c-104">*Processing* a data mining model is also called *training*.</span></span>  
  
 <span data-ttu-id="c667c-105">**マイニング構造の処理:** マイニング構造は、列バインドと使用方法のメタデータの定義に従って外部のデータ ソースからデータを取得し、データを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="c667c-105">**Processing mining structures:** A mining structure gets data from an external data source, as defined by the column bindings and usage metadata, and reads the data.</span></span> <span data-ttu-id="c667c-106">このデータの全体が読み取られて分析され、さまざまな統計情報が抽出されます。</span><span class="sxs-lookup"><span data-stu-id="c667c-106">This data is read in full and then analyzed to extract various statistics.</span></span> <span data-ttu-id="c667c-107">Analysis Services では、データ マイニング アルゴリズムによる分析に適した、簡潔な表現のデータがローカル キャッシュに格納されます。</span><span class="sxs-lookup"><span data-stu-id="c667c-107">Analysis Services stores a compact representation of the data, which is suitable for analysis by data mining algorithms, in a local cache.</span></span> <span data-ttu-id="c667c-108">モデルを処理した後、このキャッシュを保持することも削除することもできます。</span><span class="sxs-lookup"><span data-stu-id="c667c-108">You can either keep this cache or delete it after your models have been processed.</span></span> <span data-ttu-id="c667c-109">既定では、キャッシュが保存されます。</span><span class="sxs-lookup"><span data-stu-id="c667c-109">By default, the cache is stored.</span></span> <span data-ttu-id="c667c-110">詳細については、「 [マイニング構造の処理](process-a-mining-structure.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c667c-110">For more information, see [Process a Mining Structure](process-a-mining-structure.md).</span></span>  
  
 <span data-ttu-id="c667c-111">**マイニング モデルの処理:** マイニング モデルは処理されるまで空で、定義だけが含まれています。</span><span class="sxs-lookup"><span data-stu-id="c667c-111">**Processing mining models:** A mining model is empty, containing definitions only, until it is processed.</span></span> <span data-ttu-id="c667c-112">マイニング モデルを処理するには、基になるマイニング構造の処理が完了している必要があります。</span><span class="sxs-lookup"><span data-stu-id="c667c-112">To process a mining model, the mining structure that it is based on must have been processed.</span></span> <span data-ttu-id="c667c-113">マイニング モデルは、マイニング構造のキャッシュからデータを取得し、モデルに対して作成されたフィルターがあれば適用した後、データセットをアルゴリズムに渡してパターンを検出します。</span><span class="sxs-lookup"><span data-stu-id="c667c-113">The mining model gets the data from the mining structure cache, applies any filters that may have been created on the model, and then passes the data set through the algorithm to detect patterns.</span></span> <span data-ttu-id="c667c-114">処理後のモデルには、データ自体ではなく処理結果だけが保存されます。</span><span class="sxs-lookup"><span data-stu-id="c667c-114">After the model is processed, the model stores only the results of processing, not the data itself.</span></span> <span data-ttu-id="c667c-115">詳細については、「 [マイニング モデルの処理](process-a-mining-model.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c667c-115">For more information, see [Process a Mining Model](process-a-mining-model.md).</span></span>  
  
 <span data-ttu-id="c667c-116">次の図は、マイニング構造とマイニング モデルの処理時のデータ フローを示しています。</span><span class="sxs-lookup"><span data-stu-id="c667c-116">The following diagram illustrates the flow of data when a mining structure is processed, and when a mining model is processed.</span></span>  
  
 <span data-ttu-id="c667c-117">![データの処理: ソース、構造、モデル](../media/dmcon-modelarch.gif "データの処理: ソース、構造、モデル")</span><span class="sxs-lookup"><span data-stu-id="c667c-117">![Processing of data: source to structure to model](../media/dmcon-modelarch.gif "Processing of data: source to structure to model")</span></span>  
  
## <a name="viewing-the-results-of-processing"></a><span data-ttu-id="c667c-118">処理結果の表示</span><span class="sxs-lookup"><span data-stu-id="c667c-118">Viewing the Results of Processing</span></span>  
 <span data-ttu-id="c667c-119">処理後のマイニング構造には、統計分析に使用できる、簡潔な表現のデータが含まれています。</span><span class="sxs-lookup"><span data-stu-id="c667c-119">After a mining structure has been processed, it contains a compact representation of the data for use in statistical analysis.</span></span> <span data-ttu-id="c667c-120">キャッシュが消去されていない場合、このキャッシュ内のデータには次の方法でアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="c667c-120">If the cache has not been cleared, you can access the data in this cache in the following ways:</span></span>  
  
-   <span data-ttu-id="c667c-121">モデルに対するデータ マイニング拡張機能 (DMX) クエリを作成し、構造にドリルスルーします。</span><span class="sxs-lookup"><span data-stu-id="c667c-121">Creating a Data Mining Extensions (DMX) query on the model and drilling through to the structure.</span></span> <span data-ttu-id="c667c-122">詳細については、「[SELECT FROM &#60;model&#62;.CASES (DMX)](/sql/dmx/select-from-model-content-dmx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c667c-122">For more information, see [SELECT FROM &#60;model&#62;.CASES &#40;DMX&#41;](/sql/dmx/select-from-model-content-dmx).</span></span>  
  
-   <span data-ttu-id="c667c-123">構造に基づいてモデルを参照し、ユーザー インターフェイスでいずれかのオプションを使用して構造ケースにドリルスルーします。</span><span class="sxs-lookup"><span data-stu-id="c667c-123">Browsing a model based on the structure, and using one of the options in the user interface to drill through to structure cases.</span></span> <span data-ttu-id="c667c-124">詳細については、「 [Data Mining Model Viewers](data-mining-model-viewers.md)」 (データ マイニング モデル ビューアー) または「 [マイニング モデルからケース データへのドリルスルー](drill-through-to-case-data-from-a-mining-model.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c667c-124">For more information, see [Data Mining Model Viewers](data-mining-model-viewers.md), or [Drill Through to Case Data from a Mining Model](drill-through-to-case-data-from-a-mining-model.md).</span></span>  
  
-   <span data-ttu-id="c667c-125">構造ケースに対する DMX クエリを作成します。</span><span class="sxs-lookup"><span data-stu-id="c667c-125">Creating a DMX query on the structure cases.</span></span> <span data-ttu-id="c667c-126">詳細については、「[SELECT FROM &#60;structure&#62;.CASES](/sql/dmx/select-from-structure-cases)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c667c-126">For more information, see [SELECT FROM &#60;structure&#62;.CASES](/sql/dmx/select-from-structure-cases).</span></span>  
  
 <span data-ttu-id="c667c-127">処理後のマイニング モデルには、分析によって生成されたパターンと、モデルの結果からキャッシュ内のトレーニング データへのマッピングだけが含まれています。</span><span class="sxs-lookup"><span data-stu-id="c667c-127">After a mining model has been processed, it contains only the patterns that were derived from analysis, and mappings from the model results to the cached training data.</span></span> <span data-ttu-id="c667c-128">モデルの結果 ( *モデル コンテンツ*) に対して参照やクエリを実行できます。また、キャッシュされている場合は、モデル ケースや構造ケースに対してクエリを実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="c667c-128">You can browse or query the model results, called *model content*, or you can query the model and structure cases, if they have been cached.</span></span>  
  
 <span data-ttu-id="c667c-129">各マイニング モデルのモデル コンテンツは、作成に使用されたアルゴリズムによって異なります。</span><span class="sxs-lookup"><span data-stu-id="c667c-129">The model content for each mining model depends on the algorithm that was used to create it.</span></span> <span data-ttu-id="c667c-130">たとえば、クラスター モデルとデシジョン ツリー モデルでは、まったく同じデータを使用した場合でも、モデル コンテンツが大きく異なります。</span><span class="sxs-lookup"><span data-stu-id="c667c-130">For example, if one model is a clustering model and another is a decision trees model, the model content is very different even though the models use exactly the same data.</span></span> <span data-ttu-id="c667c-131">詳細については、「[マイニング モデル コンテンツ (Analysis Services - データ マイニング)](mining-model-content-analysis-services-data-mining.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c667c-131">For more information, see [Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md).</span></span>  
  
## <a name="processing-requirements"></a><span data-ttu-id="c667c-132">処理の要件</span><span class="sxs-lookup"><span data-stu-id="c667c-132">Processing Requirements</span></span>  
 <span data-ttu-id="c667c-133">処理の要件は、マイニング モデルがリレーショナル データのみに基づいているか多次元データ ソースに基づいているかに応じて異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="c667c-133">Processing requirements may differ depending on whether your mining models are based solely on relational data, or on multidimensional data source.</span></span>  
  
 <span data-ttu-id="c667c-134">リレーショナル データソースの処理には、トレーニング データを作成し、そのデータでマイニング アルゴリズムを実行することだけが必要です。</span><span class="sxs-lookup"><span data-stu-id="c667c-134">For relational data source, processing requires only that you create training data and run mining algorithms on that data.</span></span> <span data-ttu-id="c667c-135">ただし、マイニング モデルがディメンション、メジャーなどの OLAP オブジェクトに基づいている場合は、基になるデータが処理済みの状態であることが必要です。</span><span class="sxs-lookup"><span data-stu-id="c667c-135">However, mining models that are based on OLAP objects, such as dimensions and measures, require that the underlying data be in a processed state.</span></span> <span data-ttu-id="c667c-136">これには、多次元オブジェクトを処理して、マイニング モデルを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c667c-136">This may requires that the multidimensional objects be processed to populate the mining model.</span></span>  
  
 <span data-ttu-id="c667c-137">詳細については、「[処理の要件および注意事項 (データ マイニング)](processing-requirements-and-considerations-data-mining.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c667c-137">For more information, see [Processing Requirements and Considerations &#40;Data Mining&#41;](processing-requirements-and-considerations-data-mining.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c667c-138">参照</span><span class="sxs-lookup"><span data-stu-id="c667c-138">See Also</span></span>  
 <span data-ttu-id="c667c-139">[データマイニング &#40;のドリルスルークエリ&#41;](drillthrough-queries-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="c667c-139">[Drillthrough Queries &#40;Data Mining&#41;](drillthrough-queries-data-mining.md) </span></span>  
 <span data-ttu-id="c667c-140">[マイニング構造 &#40;Analysis Services-データマイニング&#41;](mining-structures-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="c667c-140">[Mining Structures &#40;Analysis Services - Data Mining&#41;](mining-structures-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="c667c-141">[マイニングモデル &#40;Analysis Services-データマイニング&#41;](mining-models-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="c667c-141">[Mining Models &#40;Analysis Services - Data Mining&#41;](mining-models-analysis-services-data-mining.md) </span></span>  
 [<span data-ttu-id="c667c-142">論理アーキテクチャ (Analysis Services - データ マイニング)</span><span class="sxs-lookup"><span data-stu-id="c667c-142">Logical Architecture &#40;Analysis Services - Data Mining&#41;</span></span>](logical-architecture-analysis-services-data-mining.md)  
  
  
