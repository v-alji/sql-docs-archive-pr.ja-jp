---
title: Microsoft ニューラルネットワークアルゴリズム |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- training neural networks
- output neurons [Analysis Services]
- algorithms [data mining]
- neural network algorithms [Analysis Services]
- neurons [Analysis Services]
- classification algorithms [Analysis Services]
- neural networks
- multilayer perceptron network of neurons [Analysis Services]
- hidden neurons
- Back-Propagated Delta Rule network
- input neurons [Analysis Services]
- regression algorithms [Analysis Services]
ms.assetid: 61eb4861-8a6a-4214-a4b8-1dd278ad7a68
author: minewiskan
ms.author: owend
ms.openlocfilehash: 389df77299bbf357e1b8b0f0695f03a74420f786
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631354"
---
# <a name="microsoft-neural-network-algorithm"></a><span data-ttu-id="d947f-102">Microsoft Neural Network Algorithm</span><span class="sxs-lookup"><span data-stu-id="d947f-102">Microsoft Neural Network Algorithm</span></span>
  <span data-ttu-id="d947f-103">では [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] ニューラルネットワークアルゴリズムは、入力属性の考えられる各状態と予測可能な属性の各状態を組み合わせ、トレーニングデータを使用して確率を計算します。</span><span class="sxs-lookup"><span data-stu-id="d947f-103">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network algorithm combines each possible state of the input attribute with each possible state of the predictable attribute, and uses the training data to calculate probabilities.</span></span> <span data-ttu-id="d947f-104">これらの確率は、分類や回帰で使用することも、入力属性に基づいて予測属性の結果を予測するために使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="d947f-104">You can later use these probabilities for classification or regression, and to predict an outcome of the predicted attribute, based on the input attributes.</span></span>  
  
 <span data-ttu-id="d947f-105">[!INCLUDE[msCoName](../../includes/msconame-md.md)] ニューラル ネットワーク アルゴリズムで作成されたマイニング モデルには、入力と予測の両方に使用する列の数または予測のみに使用する列の数に応じて、複数のネットワークを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="d947f-105">A mining model that is constructed with the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network algorithm can contain multiple networks, depending on the number of columns that are used for both input and prediction, or that are used only for prediction.</span></span> <span data-ttu-id="d947f-106">1 つのマイニング モデルに含まれるネットワークの数は、マイニング モデルで使用される入力列および予測可能列に含まれる状態の数によって異なります。</span><span class="sxs-lookup"><span data-stu-id="d947f-106">The number of networks that a single mining model contains depends on the number of states that are contained by the input columns and predictable columns that the mining model uses.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d947f-107">例</span><span class="sxs-lookup"><span data-stu-id="d947f-107">Example</span></span>  
 <span data-ttu-id="d947f-108">[!INCLUDE[msCoName](../../includes/msconame-md.md)] ニューラル ネットワーク アルゴリズムは、製造または商業活動などからの複雑な入力データの分析や、大量のトレーニング データが利用できるが他のアルゴリズムではルールを簡単に導き出すことができない業務上の問題の分析に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="d947f-108">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network algorithm is useful for analyzing complex input data, such as from a manufacturing or commercial process, or business problems for which a significant quantity of training data is available but for which rules cannot be easily derived by using other algorithms.</span></span>  
  
 <span data-ttu-id="d947f-109">[!INCLUDE[msCoName](../../includes/msconame-md.md)] ニューラル ネットワーク アルゴリズムを使用する推奨シナリオは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="d947f-109">Suggested scenarios for using the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network algorithm include the following:</span></span>  
  
-   <span data-ttu-id="d947f-110">ダイレクト メール宣伝やラジオ広告キャンペーンの成功度の測定など、マーケティングおよび宣伝に関する分析</span><span class="sxs-lookup"><span data-stu-id="d947f-110">Marketing and promotion analysis, such as measuring the success of a direct mail promotion or a radio advertising campaign.</span></span>  
  
-   <span data-ttu-id="d947f-111">履歴データからの、株価の動向、通貨の騰落、その他の流動性の高い金融情報の予測</span><span class="sxs-lookup"><span data-stu-id="d947f-111">Predicting stock movement, currency fluctuation, or other highly fluid financial information from historical data.</span></span>  
  
-   <span data-ttu-id="d947f-112">製造および工業プロセスに関する分析</span><span class="sxs-lookup"><span data-stu-id="d947f-112">Analyzing manufacturing and industrial processes.</span></span>  
  
-   <span data-ttu-id="d947f-113">テキスト マイニング</span><span class="sxs-lookup"><span data-stu-id="d947f-113">Text mining.</span></span>  
  
-   <span data-ttu-id="d947f-114">多数の入力と比較的少数の出力間の複雑なリレーションシップを分析する予測モデル。</span><span class="sxs-lookup"><span data-stu-id="d947f-114">Any prediction model that analyzes complex relationships between many inputs and relatively fewer outputs.</span></span>  
  
## <a name="how-the-algorithm-works"></a><span data-ttu-id="d947f-115">アルゴリズムの動作</span><span class="sxs-lookup"><span data-stu-id="d947f-115">How the Algorithm Works</span></span>  
 <span data-ttu-id="d947f-116">[!INCLUDE[msCoName](../../includes/msconame-md.md)] ニューラル ネットワーク アルゴリズムは、最大 3 層のニューロンで構成されるネットワークを作成します。</span><span class="sxs-lookup"><span data-stu-id="d947f-116">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network algorithm creates a network that is composed of up to three layers of neurons.</span></span> <span data-ttu-id="d947f-117">これらの層は、入力層、オプションの非表示層、および出力層です。</span><span class="sxs-lookup"><span data-stu-id="d947f-117">These layers are an input layer, an optional hidden layer, and an output layer.</span></span>  
  
 <span data-ttu-id="d947f-118">**入力層:** 入力ニューロンは、データマイニングモデルのすべての入力属性値とその確率を定義します。</span><span class="sxs-lookup"><span data-stu-id="d947f-118">**Input layer:** Input neurons define all the input attribute values for the data mining model, and their probabilities.</span></span>  
  
 <span data-ttu-id="d947f-119">**非表示層:** 非表示のニューロンは、入力ニューロンから入力を受け取り、出力をニューロンに出力します。</span><span class="sxs-lookup"><span data-stu-id="d947f-119">**Hidden layer:** Hidden neurons receive inputs from input neurons and provide outputs to output neurons.</span></span> <span data-ttu-id="d947f-120">非表示層では、入力のさまざまな確率に重みが割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="d947f-120">The hidden layer is where the various probabilities of the inputs are assigned weights.</span></span> <span data-ttu-id="d947f-121">重みは、非表示ニューロンに対する特定の入力の関連性または重要性を表します。</span><span class="sxs-lookup"><span data-stu-id="d947f-121">A weight describes the relevance or importance of a particular input to the hidden neuron.</span></span> <span data-ttu-id="d947f-122">入力に割り当てられている重みが大きいほど、その入力の値の重要性が増加します。</span><span class="sxs-lookup"><span data-stu-id="d947f-122">The greater the weight that is assigned to an input, the more important the value of that input is.</span></span> <span data-ttu-id="d947f-123">重みには負の値も使用できます。これは、その入力によって特定の結果が優先されるのではなく、抑制されることを意味します。</span><span class="sxs-lookup"><span data-stu-id="d947f-123">Weights can be negative, which means that the input can inhibit, rather than favor, a specific result.</span></span>  
  
 <span data-ttu-id="d947f-124">**出力層:** 出力ニューロンは、データマイニングモデルの予測可能な属性値を表します。</span><span class="sxs-lookup"><span data-stu-id="d947f-124">**Output layer:** Output neurons represent predictable attribute values for the data mining model.</span></span>  
  
 <span data-ttu-id="d947f-125">入力層、非表示層、および出力層の作成方法およびスコア計算方法の詳細については、「 [Microsoft Neural Network Algorithm Technical Reference](microsoft-neural-network-algorithm-technical-reference.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d947f-125">For a detailed explanation of how the input, hidden, and output layers are constructed and scored, see [Microsoft Neural Network Algorithm Technical Reference](microsoft-neural-network-algorithm-technical-reference.md).</span></span>  
  
## <a name="data-required-for-neural-network-models"></a><span data-ttu-id="d947f-126">ニューラル ネットワーク モデルに必要なデータ</span><span class="sxs-lookup"><span data-stu-id="d947f-126">Data Required for Neural Network Models</span></span>  
 <span data-ttu-id="d947f-127">ニューラル ネットワーク モデルには、単一のキー列、1 つ以上の入力列、および 1 つ以上の予測可能列が必要です。</span><span class="sxs-lookup"><span data-stu-id="d947f-127">A neural network model must contain a key column, one or more input columns, and one or more predictable columns.</span></span>  
  
 <span data-ttu-id="d947f-128">[!INCLUDE[msCoName](../../includes/msconame-md.md)] ニューラル ネットワーク アルゴリズムを使用するデータ マイニング モデルは、アルゴリズムで使用できるパラメーターに対して指定した値の影響を強く受けます。</span><span class="sxs-lookup"><span data-stu-id="d947f-128">Data mining models that use the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network algorithm are heavily influenced by the values that you specify for the parameters that are available to the algorithm.</span></span> <span data-ttu-id="d947f-129">パラメーターでは、データのサンプリング方法、各列へのデータの分散方法またはデータの分散が必要になる状況、および最終的なモデルで使用される値を制限するために機能選択を呼び出すタイミングを定義します。</span><span class="sxs-lookup"><span data-stu-id="d947f-129">The parameters define how data is sampled, how data is distributed or expected to be distributed in each column, and when feature selection is invoked to limit the values that are used in the final model.</span></span>  
  
 <span data-ttu-id="d947f-130">モデルの動作をカスタマイズするパラメーターを設定する方法の詳細については、「 [Microsoft Neural Network Algorithm Technical Reference](microsoft-neural-network-algorithm-technical-reference.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d947f-130">For more information about setting parameters to customize model behavior, see [Microsoft Neural Network Algorithm Technical Reference](microsoft-neural-network-algorithm-technical-reference.md).</span></span>  
  
## <a name="viewing-a-neural-network-model"></a><span data-ttu-id="d947f-131">ニューラル ネットワーク モデルの表示</span><span class="sxs-lookup"><span data-stu-id="d947f-131">Viewing a Neural Network Model</span></span>  
 <span data-ttu-id="d947f-132">データを操作したり、モデルと入力および出力との関係性を確認したりするには、 **Microsoft ニューラル ネットワーク ビューアー**を使用します。</span><span class="sxs-lookup"><span data-stu-id="d947f-132">To work with the data and see how the model correlates inputs with outputs, you can use the **Microsoft Neural Network Viewer**.</span></span> <span data-ttu-id="d947f-133">このカスタム ビューアーを使用すると、入力属性およびその値をフィルター処理することも、出力への影響を示すグラフを参照することもできます。</span><span class="sxs-lookup"><span data-stu-id="d947f-133">With this custom viewer, you can filter on input attributes and their values, and see graphs that show how they affect the outputs.</span></span> <span data-ttu-id="d947f-134">このビューアーのツールヒントには、入力値と出力値の各ペアに関連付けられている確率とリフトが示されます。</span><span class="sxs-lookup"><span data-stu-id="d947f-134">The tooltips in the viewer show you the probability and lift associated with each pair of input and output values.</span></span> <span data-ttu-id="d947f-135">詳細については、「 [Microsoft ニューラル ネットワーク ビューアーを使用したモデルの参照](browse-a-model-using-the-microsoft-neural-network-viewer.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d947f-135">For more information, see [Browse a Model Using the Microsoft Neural Network Viewer](browse-a-model-using-the-microsoft-neural-network-viewer.md).</span></span>  
  
 <span data-ttu-id="d947f-136">モデルの構造を参照するには、 **Microsoft 汎用コンテンツ ツリー ビューアー**を使用するのが最も簡単な方法です。</span><span class="sxs-lookup"><span data-stu-id="d947f-136">The easiest way to explore the structure of the model is to use the **Microsoft Generic Content Tree Viewer**.</span></span> <span data-ttu-id="d947f-137">モデルで作成された入力、出力、およびネットワークを表示したり、任意のノードをクリックして展開して入力層ノード、出力層ノード、または非表示層ノードに関連付けられている統計を参照したりできます。</span><span class="sxs-lookup"><span data-stu-id="d947f-137">You can view the inputs, outputs, and networks created by the model, and click on any node to expand it and see statistics related to the input, output, or hidden layer nodes.</span></span> <span data-ttu-id="d947f-138">詳細については、「 [Microsoft 汎用コンテンツ ツリー ビューアーを使用したモデルの参照](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="d947f-138">For more information, see [Browse a Model Using the Microsoft Generic Content Tree Viewer](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md).</span></span>  
  
## <a name="creating-predictions"></a><span data-ttu-id="d947f-139">予測の作成</span><span class="sxs-lookup"><span data-stu-id="d947f-139">Creating Predictions</span></span>  
 <span data-ttu-id="d947f-140">モデルの処理が完了したら、各ノード内に格納されているネットワークと重みを使用して予測を作成できます。</span><span class="sxs-lookup"><span data-stu-id="d947f-140">After the model has been processed, you can use the network and the weights stored within each node to make predictions.</span></span> <span data-ttu-id="d947f-141">ニューラル ネットワーク モデルは、回帰分析、アソシエーション分析、および分類分析をサポートします。そのため、各予測の意味は異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="d947f-141">A neural network model supports regression, association, and classification analysis, Therefore, the meaning of each prediction might be different.</span></span> <span data-ttu-id="d947f-142">またモデル自身に対してクエリを実行して、見つかった相関関係を確認することも、関連した統計を取得することもできます。</span><span class="sxs-lookup"><span data-stu-id="d947f-142">You can also query the model itself, to review the correlations that were found and retrieve related statistics.</span></span> <span data-ttu-id="d947f-143">ニューラル ネットワーク モデルに対するクエリの作成方法の例については、「 [ニューラル ネットワーク モデルのクエリ例](neural-network-model-query-examples.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d947f-143">For examples of how to create queries against a neural network model, see [Neural Network Model Query Examples](neural-network-model-query-examples.md).</span></span>  
  
 <span data-ttu-id="d947f-144">データ マイニング モデルに対するクエリの作成方法については、「 [データ マイニング クエリ](data-mining-queries.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d947f-144">For general information about how to create a query on a data mining model, see [Data Mining Queries](data-mining-queries.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d947f-145">解説</span><span class="sxs-lookup"><span data-stu-id="d947f-145">Remarks</span></span>  
  
-   <span data-ttu-id="d947f-146">ドリル スルーまたはデータ マイニング ディメンションはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="d947f-146">Does not support drillthrough or data mining dimensions.</span></span> <span data-ttu-id="d947f-147">これは、マイニング モデルのノードの構造がその基になるデータと必ずしも直接対応しているわけではないからです。</span><span class="sxs-lookup"><span data-stu-id="d947f-147">This is because the structure of the nodes in the mining model does not necessarily correspond directly to the underlying data.</span></span>  
  
-   <span data-ttu-id="d947f-148">Predictive Model Markup Language (PMML) 形式のモデルの作成はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="d947f-148">Does not support the creation of models in Predictive Model Markup Language (PMML) format.</span></span>  
  
-   <span data-ttu-id="d947f-149">OLAP マイニング モデルの使用がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="d947f-149">Supports the use of OLAP mining models.</span></span>  
  
-   <span data-ttu-id="d947f-150">データ マイニング ディメンションの作成はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="d947f-150">Does not support the creation of data mining dimensions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d947f-151">参照</span><span class="sxs-lookup"><span data-stu-id="d947f-151">See Also</span></span>  
 <span data-ttu-id="d947f-152">[Microsoft ニューラルネットワークアルゴリズムテクニカルリファレンス](microsoft-neural-network-algorithm-technical-reference.md) </span><span class="sxs-lookup"><span data-stu-id="d947f-152">[Microsoft Neural Network Algorithm Technical Reference](microsoft-neural-network-algorithm-technical-reference.md) </span></span>  
 <span data-ttu-id="d947f-153">[ニューラルネットワークモデルのマイニングモデルコンテンツ &#40;Analysis Services データマイニング&#41;](mining-model-content-for-neural-network-models-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="d947f-153">[Mining Model Content for Neural Network Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-neural-network-models-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="d947f-154">[ニューラルネットワークモデルのクエリ例](neural-network-model-query-examples.md) </span><span class="sxs-lookup"><span data-stu-id="d947f-154">[Neural Network Model Query Examples](neural-network-model-query-examples.md) </span></span>  
 [<span data-ttu-id="d947f-155">Microsoft ロジスティック回帰アルゴリズム</span><span class="sxs-lookup"><span data-stu-id="d947f-155">Microsoft Logistic Regression Algorithm</span></span>](microsoft-logistic-regression-algorithm.md)  
  
  
