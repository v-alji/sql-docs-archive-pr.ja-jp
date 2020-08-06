---
title: Microsoft シーケンスクラスターアルゴリズムテクニカルリファレンス |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- MAXIMUM_SEQUENCE_STATES parameter
- MINIMUM_SUPPORT parameter
- MAXIMUM_STATES parameter
- sequence clustering algorithms [Analysis Services]
- CLUSTER_COUNT parameter
ms.assetid: 251c369d-6b02-4687-964e-39bf55c9b009
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3e09018fad9c291ec1f47bbb776797d634950381
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631355"
---
# <a name="microsoft-sequence-clustering-algorithm-technical-reference"></a><span data-ttu-id="25ff4-102">Microsoft シーケンス クラスタリング アルゴリズム テクニカル リファレンス</span><span class="sxs-lookup"><span data-stu-id="25ff4-102">Microsoft Sequence Clustering Algorithm Technical Reference</span></span>
  <span data-ttu-id="25ff4-103">Microsoft シーケンス クラスター アルゴリズムは、複合的なアルゴリズムです。このアルゴリズムでは、Markov 連鎖分析を使用して順序付けられたシーケンスを特定し、この分析結果とクラスタリング技法を組み合わせて、シーケンスおよびモデル内のその他の属性に基づいてクラスターを生成します。</span><span class="sxs-lookup"><span data-stu-id="25ff4-103">The Microsoft Sequence Clustering algorithm is a hybrid algorithm that uses Markov chain analysis to identify ordered sequences, and combines the results of this analysis with clustering techniques to generate clusters based on the sequences and other attributes in the model.</span></span> <span data-ttu-id="25ff4-104">このトピックでは、アルゴリズムの実装、アルゴリズムをカスタマイズする方法、およびシーケンス クラスター モデルの特別な要件について説明します。</span><span class="sxs-lookup"><span data-stu-id="25ff4-104">This topic describes the implementation of the algorithm, how to customize the algorithm, and special requirements for sequence clustering models.</span></span>  
  
 <span data-ttu-id="25ff4-105">シーケンス クラスター モデルの参照およびクエリを行う方法を含む、アルゴリズムに関する一般的な情報については、「 [Microsoft Sequence Clustering Algorithm](microsoft-sequence-clustering-algorithm.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="25ff4-105">For more general information about the algorithm, including how to browse and query sequence clustering models, see [Microsoft Sequence Clustering Algorithm](microsoft-sequence-clustering-algorithm.md).</span></span>  
  
## <a name="implementation-of-the-microsoft-sequence-clustering-algorithm"></a><span data-ttu-id="25ff4-106">Microsoft シーケンス クラスター アルゴリズムの実装</span><span class="sxs-lookup"><span data-stu-id="25ff4-106">Implementation of the Microsoft Sequence Clustering Algorithm</span></span>  
 <span data-ttu-id="25ff4-107">Microsoft シーケンス クラスター モデルでは、Markov モデルを使用して、シーケンスの特定やシーケンスの確率の決定を行います。</span><span class="sxs-lookup"><span data-stu-id="25ff4-107">The Microsoft Sequence Clustering model uses Markov models to identify sequences and determine the probability of sequences.</span></span> <span data-ttu-id="25ff4-108">Markov モデルは、さまざまな状態の間の遷移を格納する有向グラフです。</span><span class="sxs-lookup"><span data-stu-id="25ff4-108">A Markov model is a directed graph that stores the transitions between different states.</span></span> <span data-ttu-id="25ff4-109">Microsoft シーケンス クラスター アルゴリズムでは n 次 Markov 連鎖を使用します。隠れ Markov モデルは使用しません。</span><span class="sxs-lookup"><span data-stu-id="25ff4-109">The Microsoft Sequence Clustering algorithm uses n-order Markov chains, not a Hidden Markov model.</span></span>  
  
 <span data-ttu-id="25ff4-110">Markov 連鎖の次数は、現在の状態の確率を決定するために使用される状態の数を示しています。</span><span class="sxs-lookup"><span data-stu-id="25ff4-110">The number of orders in a Markov chain tells you how many states are used to determine the probability of the current states.</span></span> <span data-ttu-id="25ff4-111">1 次 Markov モデルでは、現在の状態の確率は直前の状態のみに依存します。</span><span class="sxs-lookup"><span data-stu-id="25ff4-111">In a first-order Markov model, the probability of the current state depends only on the previous state.</span></span> <span data-ttu-id="25ff4-112">2 次 Markov 連鎖では、状態の確率は前の 2 つの状態に依存し、以下同様に増えていきます。</span><span class="sxs-lookup"><span data-stu-id="25ff4-112">In a second-order Markov chain, the probability of a state depends on the previous two states, and so forth.</span></span> <span data-ttu-id="25ff4-113">Markov 連鎖ごとに、状態の各組み合わせの遷移が遷移マトリックスに格納されます。</span><span class="sxs-lookup"><span data-stu-id="25ff4-113">For each Markov chain, a transition matrix stores the transitions for each combination of states.</span></span> <span data-ttu-id="25ff4-114">Markov 連鎖が長くなるにつれ、マトリックスのサイズも指数関数的に大きくなり、マトリックスが非常に疎になります。</span><span class="sxs-lookup"><span data-stu-id="25ff4-114">As the length of the Markov chain increases, the size of the matrix also increases exponentially, and the matrix becomes extremely sparse.</span></span> <span data-ttu-id="25ff4-115">処理時間も比例して長くなります。</span><span class="sxs-lookup"><span data-stu-id="25ff4-115">Processing time also increases proportionally.</span></span>  
  
 <span data-ttu-id="25ff4-116">特定のサイトの Web ページへのアクセスを分析するクリックストリーム分析の例を使用して、連鎖がどうなるかを思い浮かべてみるとわかりやすくなります。</span><span class="sxs-lookup"><span data-stu-id="25ff4-116">It might be helpful to visualize the chain by using the example of clickstream analysis, which analyzes visits to Web pages on a site.</span></span> <span data-ttu-id="25ff4-117">各ユーザーによって、セッションごとにクリックの長いシーケンスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="25ff4-117">Each user creates a long sequence of clicks for each session.</span></span> <span data-ttu-id="25ff4-118">Web サイトでのユーザーの行動を分析するモデルを作成する場合、トレーニングに使用するデータセットは、同じクリック パスのインスタンスの総数を含むグラフに変換される URL のシーケンスです。</span><span class="sxs-lookup"><span data-stu-id="25ff4-118">When you create a model to analyze user behavior on a Web site, the data set used for training is a sequence of URLs, converted to a graph that includes the count of all instances of the same click path.</span></span> <span data-ttu-id="25ff4-119">たとえば、このグラフには、ユーザーがページ 1 からページ 2 に移動する確率 (10%)、ユーザーがページ 1 からページ 3 に移動する確率 (20%) などが含まれます。</span><span class="sxs-lookup"><span data-stu-id="25ff4-119">For example, the graph contains the probability that the user moves from page 1 to page 2 (10%), the probability that the user moves from page 1 to page 3 (20%), and so forth.</span></span> <span data-ttu-id="25ff4-120">すべての有効なパスおよび部分的なパスを合わせると、いずれか 1 つのパスを監視する場合よりもずっと長く複雑なグラフになります。</span><span class="sxs-lookup"><span data-stu-id="25ff4-120">When you put all the possible paths and pieces of the paths together, you obtain a graph that might be much longer and more complex than any single observed path.</span></span>  
  
 <span data-ttu-id="25ff4-121">既定では、Microsoft シーケンス クラスター アルゴリズムではクラスタリングの Expectation Maximization (EM) 手法を使用します。</span><span class="sxs-lookup"><span data-stu-id="25ff4-121">By default, the Microsoft Sequence Clustering algorithm uses the Expectation Maximization (EM) method of clustering.</span></span> <span data-ttu-id="25ff4-122">詳細については、「 [Microsoft クラスタリング アルゴリズム テクニカル リファレンス](microsoft-clustering-algorithm-technical-reference.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="25ff4-122">For more information, see [Microsoft Clustering Algorithm Technical Reference](microsoft-clustering-algorithm-technical-reference.md).</span></span>  
  
 <span data-ttu-id="25ff4-123">クラスタリングの対象の属性は、シーケンシャルかどうかに依存しません。</span><span class="sxs-lookup"><span data-stu-id="25ff4-123">The targets of clustering are both the sequential and nonsequential attributes.</span></span> <span data-ttu-id="25ff4-124">各クラスターは、確率分布を使用してランダムに選択されます。</span><span class="sxs-lookup"><span data-stu-id="25ff4-124">Each cluster is randomly selected using a probability distribution.</span></span> <span data-ttu-id="25ff4-125">各クラスターには、パスの完全なセットを表す Markov 連鎖、およびシーケンスの状態遷移と確率を含むマトリックスがあります。</span><span class="sxs-lookup"><span data-stu-id="25ff4-125">Each cluster has a Markov chain that represents the complete set of paths, and a matrix that contains the sequence state transitions and probabilities.</span></span> <span data-ttu-id="25ff4-126">初期分布に基づいて、特定のクラスターで、シーケンスなど任意の属性の確率が Bayes ルールを使用して計算されます。</span><span class="sxs-lookup"><span data-stu-id="25ff4-126">Based on the initial distribution, Bayes rule is used to calculate the probability of any attribute, including a sequence, in a specific cluster.</span></span>  
  
 <span data-ttu-id="25ff4-127">Microsoft シーケンス クラスター アルゴリズムでは、モデルへの非シーケンシャル属性の追加がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="25ff4-127">The Microsoft Sequence Clustering algorithm supports the additional of nonsequential attributes to the model.</span></span> <span data-ttu-id="25ff4-128">つまり、一般的なクラスター モデルの場合と同様に、追加属性をシーケンス属性と組み合わせて、類似する属性を含むケースのクラスターを作成できます。</span><span class="sxs-lookup"><span data-stu-id="25ff4-128">This means that these additional attributes are combined with the sequence attributes to create clusters of cases with similar attributes, just like in a typical clustering model.</span></span>  
  
 <span data-ttu-id="25ff4-129">傾向として、シーケンス クラスター モデルでは、一般的なクラスター モデルより多くのクラスターを作成します。</span><span class="sxs-lookup"><span data-stu-id="25ff4-129">A sequence clustering model tends to create many more clusters than a typical clustering model.</span></span> <span data-ttu-id="25ff4-130">そのため、Microsoft シーケンス クラスター アルゴリズムでは、 *クラスター分解*を実行して、シーケンスやその他の属性に基づいてクラスターを分割します。</span><span class="sxs-lookup"><span data-stu-id="25ff4-130">Therefore, the Microsoft Sequence Clustering algorithm performs *cluster decomposition*to separate clusters based on sequences and other attributes.</span></span>  
  
### <a name="feature-selection-in-a-sequence-clustering-model"></a><span data-ttu-id="25ff4-131">シーケンス クラスター モデルでの機能の選択</span><span class="sxs-lookup"><span data-stu-id="25ff4-131">Feature Selection in a Sequence Clustering Model</span></span>  
 <span data-ttu-id="25ff4-132">シーケンスの作成時には機能の選択は実行されません。ただし、クラスタリングの段階で機能の選択が適用されます。</span><span class="sxs-lookup"><span data-stu-id="25ff4-132">Feature selection is not invoked when building sequences; however, feature selection applies at the clustering stage.</span></span>  
  
|<span data-ttu-id="25ff4-133">モデルの種類</span><span class="sxs-lookup"><span data-stu-id="25ff4-133">Model type</span></span>|<span data-ttu-id="25ff4-134">機能の選択の方法</span><span class="sxs-lookup"><span data-stu-id="25ff4-134">Feature Selection Method</span></span>|<span data-ttu-id="25ff4-135">説明</span><span class="sxs-lookup"><span data-stu-id="25ff4-135">Comments</span></span>|  
|----------------|------------------------------|--------------|  
|<span data-ttu-id="25ff4-136">シーケンス クラスター</span><span class="sxs-lookup"><span data-stu-id="25ff4-136">Sequence Clustering</span></span>|<span data-ttu-id="25ff4-137">使用されていない</span><span class="sxs-lookup"><span data-stu-id="25ff4-137">Not used</span></span>|<span data-ttu-id="25ff4-138">機能の選択は実行されません。ただし、パラメーター MINIMUM_SUPPORT および MINIMUM_PROBABILIITY の値を設定することによってアルゴリズムの動作を制御できます。</span><span class="sxs-lookup"><span data-stu-id="25ff4-138">Feature selection is not invoked; however, you can control the behavior of the algorithm by setting the value of the parameters MINIMUM_SUPPORT and MINIMUM_PROBABILIITY.</span></span>|  
|<span data-ttu-id="25ff4-139">クラスタリング</span><span class="sxs-lookup"><span data-stu-id="25ff4-139">Clustering</span></span>|<span data-ttu-id="25ff4-140">興味深さのスコア</span><span class="sxs-lookup"><span data-stu-id="25ff4-140">Interestingness score</span></span>|<span data-ttu-id="25ff4-141">クラスタリング アルゴリズムでは不連続のアルゴリズムや分離されたアルゴリズムを使用できますが、各属性のスコアは距離として計算されるため連続値です。したがって、興味深さのスコアが使用されます。</span><span class="sxs-lookup"><span data-stu-id="25ff4-141">Although the clustering algorithm may use discrete or discretized algorithms, the score of each attribute is calculated as a distance and is continuous; therefore the interestingness score is used.</span></span>|  
  
 <span data-ttu-id="25ff4-142">詳しくは、「 [Feature Selection](../../sql-server/install/feature-selection.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="25ff4-142">For more information, see [Feature Selection](../../sql-server/install/feature-selection.md).</span></span>  
  
### <a name="optimizing-performance"></a><span data-ttu-id="25ff4-143">パフォーマンスの最適化</span><span class="sxs-lookup"><span data-stu-id="25ff4-143">Optimizing Performance</span></span>  
 <span data-ttu-id="25ff4-144">Microsoft シーケンス クラスター アルゴリズムでは、処理を最適化するさまざまな方法がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="25ff4-144">The Microsoft Sequence Clustering algorithm supports various ways to optimize processing:</span></span>  
  
-   <span data-ttu-id="25ff4-145">CLUSTER_COUNT パラメーターの値を設定すると、生成されるクラスターの数を制御できます。</span><span class="sxs-lookup"><span data-stu-id="25ff4-145">Controlling the number of clusters generated, by setting a value for the CLUSTER_COUNT parameter.</span></span>  
  
-   <span data-ttu-id="25ff4-146">MINIMUM_SUPPORT パラメーターの値を増やすと、属性として含まれるシーケンスの数を減らすことができます。</span><span class="sxs-lookup"><span data-stu-id="25ff4-146">Reducing the number of sequences included as attributes, by increasing the value of the MINIMUM_SUPPORT parameter.</span></span> <span data-ttu-id="25ff4-147">その結果、頻度の低いシーケンスが除外されます。</span><span class="sxs-lookup"><span data-stu-id="25ff4-147">As a result, rare sequences are eliminated.</span></span>  
  
-   <span data-ttu-id="25ff4-148">関連属性をグループ化すると、モデルを処理する前に複雑さを軽減できます。</span><span class="sxs-lookup"><span data-stu-id="25ff4-148">Reducing complexity before processing the model, by grouping related attributes.</span></span>  
  
 <span data-ttu-id="25ff4-149">通常、いくつかの方法で、n 次 Markov 連鎖モードのパフォーマンスを最適化できます。</span><span class="sxs-lookup"><span data-stu-id="25ff4-149">In general, you can optimize the performance of an n-order Markov chain mode in several ways:</span></span>  
  
-   <span data-ttu-id="25ff4-150">可能なシーケンスの長さを制御します。</span><span class="sxs-lookup"><span data-stu-id="25ff4-150">Controlling the length of the possible sequences.</span></span>  
  
-   <span data-ttu-id="25ff4-151">n の値をプログラムによって小さくします。</span><span class="sxs-lookup"><span data-stu-id="25ff4-151">Programmatically reducing the value of n.</span></span>  
  
-   <span data-ttu-id="25ff4-152">指定したしきい値を超える確率のみを格納します。</span><span class="sxs-lookup"><span data-stu-id="25ff4-152">Storing only probabilities that exceed a specified threshold.</span></span>  
  
 <span data-ttu-id="25ff4-153">これらの方法の詳細については、このトピックでは説明しません。</span><span class="sxs-lookup"><span data-stu-id="25ff4-153">A complete discussion of these methods is beyond the scope of this topic.</span></span>  
  
## <a name="customizing-the-sequence-clustering-algorithm"></a><span data-ttu-id="25ff4-154">シーケンス クラスター アルゴリズムのカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="25ff4-154">Customizing the Sequence Clustering Algorithm</span></span>  
 <span data-ttu-id="25ff4-155">[!INCLUDE[msCoName](../../includes/msconame-md.md)] シーケンス クラスター アルゴリズムでは、結果として得られるマイニング モデルの動作、パフォーマンス、および精度に影響を与えるパラメーターがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="25ff4-155">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Sequence Clustering algorithm supports parameters that affect the behavior, performance, and accuracy of the resulting mining model.</span></span> <span data-ttu-id="25ff4-156">また、アルゴリズムによるトレーニング データの処理方法を制御するモデリング フラグを設定して、完成したモデルの動作を変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="25ff4-156">You can also modify the behavior of the completed model by setting modeling flags that control the way the algorithm processes training data.</span></span>  
  
### <a name="setting-algorithm-parameters"></a><span data-ttu-id="25ff4-157">アルゴリズム パラメーターの設定</span><span class="sxs-lookup"><span data-stu-id="25ff4-157">Setting Algorithm Parameters</span></span>  
 <span data-ttu-id="25ff4-158">次の表は、Microsoft シーケンス クラスター アルゴリズムで使用できるパラメーターを示しています。</span><span class="sxs-lookup"><span data-stu-id="25ff4-158">The following table describes the parameters that can be used with the Microsoft Sequence Clustering algorithm.</span></span>  
  
 <span data-ttu-id="25ff4-159">CLUSTER_COUNT</span><span class="sxs-lookup"><span data-stu-id="25ff4-159">CLUSTER_COUNT</span></span>  
 <span data-ttu-id="25ff4-160">アルゴリズムによって作成されるクラスターの概数を指定します。</span><span class="sxs-lookup"><span data-stu-id="25ff4-160">Specifies the approximate number of clusters to be built by the algorithm.</span></span> <span data-ttu-id="25ff4-161">その数のクラスターをデータから作成できない場合は、可能な限り多数のクラスターが作成されます。</span><span class="sxs-lookup"><span data-stu-id="25ff4-161">If the approximate number of clusters cannot be built from the data, the algorithm builds as many clusters as possible.</span></span> <span data-ttu-id="25ff4-162">CLUSTER_COUNT パラメーターを 0 に設定すると、アルゴリズムではヒューリスティックを使用して、作成するクラスターの数が最適に決定されます。</span><span class="sxs-lookup"><span data-stu-id="25ff4-162">Setting the CLUSTER_COUNT parameter to 0 causes the algorithm to use heuristics to best determine the number of clusters to build.</span></span>  
  
 <span data-ttu-id="25ff4-163">既定値は 10 です。</span><span class="sxs-lookup"><span data-stu-id="25ff4-163">The default is 10.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="25ff4-164">0 以外の数値を指定すると、アルゴリズムへのヒントとして機能します。アルゴリズムでは指定の数を取得することを目標に処理が進められますが、指定の数以外になる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="25ff4-164">Specifying a non-zero number acts as a hint to the algorithm, which proceeds with the goal of finding the specified number, but may end up finding more or less.</span></span>  
  
 <span data-ttu-id="25ff4-165">MINIMUM_SUPPORT</span><span class="sxs-lookup"><span data-stu-id="25ff4-165">MINIMUM_SUPPORT</span></span>  
 <span data-ttu-id="25ff4-166">クラスターの作成に必要とされる、属性をサポートするケースの最小数を指定します。</span><span class="sxs-lookup"><span data-stu-id="25ff4-166">Specifies the minimum number of cases that is required in support of an attribute to create a cluster.</span></span>  
  
 <span data-ttu-id="25ff4-167">既定値は 10 です。</span><span class="sxs-lookup"><span data-stu-id="25ff4-167">The default is 10.</span></span>  
  
 <span data-ttu-id="25ff4-168">MAXIMUM_SEQUENCE_STATES</span><span class="sxs-lookup"><span data-stu-id="25ff4-168">MAXIMUM_SEQUENCE_STATES</span></span>  
 <span data-ttu-id="25ff4-169">シーケンスの状態の最大数を指定します。</span><span class="sxs-lookup"><span data-stu-id="25ff4-169">Specifies the maximum number of states that a sequence can have.</span></span>  
  
 <span data-ttu-id="25ff4-170">この値を 100 より大きい数値に設定すると、アルゴリズムは意味のある情報を提供するモデルを作成できなくなります。</span><span class="sxs-lookup"><span data-stu-id="25ff4-170">Setting this value to a number greater than 100 may cause the algorithm to create a model that does not provide meaningful information.</span></span>  
  
 <span data-ttu-id="25ff4-171">既定値は、64 です。</span><span class="sxs-lookup"><span data-stu-id="25ff4-171">The default is 64.</span></span>  
  
 <span data-ttu-id="25ff4-172">MAXIMUM_STATES</span><span class="sxs-lookup"><span data-stu-id="25ff4-172">MAXIMUM_STATES</span></span>  
 <span data-ttu-id="25ff4-173">アルゴリズムによってサポートされる非シーケンス属性用の状態の最大数を指定します。</span><span class="sxs-lookup"><span data-stu-id="25ff4-173">Specifies the maximum number of states for a non-sequence attribute that the algorithm supports.</span></span> <span data-ttu-id="25ff4-174">非シーケンス属性の状態の数が状態の最大数よりも大きい場合、アルゴリズムでは属性の最も一般的な状態が使用され、残りの状態はとして扱われ `Missing` ます。</span><span class="sxs-lookup"><span data-stu-id="25ff4-174">If the number of states for a non-sequence attribute is greater than the maximum number of states, the algorithm uses the attribute's most popular states and treats the remaining states as `Missing`.</span></span>  
  
 <span data-ttu-id="25ff4-175">既定値は、100 です。</span><span class="sxs-lookup"><span data-stu-id="25ff4-175">The default is 100.</span></span>  
  
### <a name="modeling-flags"></a><span data-ttu-id="25ff4-176">ModelingFlags</span><span class="sxs-lookup"><span data-stu-id="25ff4-176">Modeling Flags</span></span>  
 <span data-ttu-id="25ff4-177">[!INCLUDE[msCoName](../../includes/msconame-md.md)] シーケンス クラスター アルゴリズムでは、次のモデリング フラグを使用できます。</span><span class="sxs-lookup"><span data-stu-id="25ff4-177">The following modeling flags are supported for use with the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Sequence Clustering algorithm.</span></span>  
  
 <span data-ttu-id="25ff4-178">NOT NULL</span><span class="sxs-lookup"><span data-stu-id="25ff4-178">NOT NULL</span></span>  
 <span data-ttu-id="25ff4-179">列に NULL を含めることはできないことを示します。</span><span class="sxs-lookup"><span data-stu-id="25ff4-179">Indicates that the column cannot contain a null.</span></span> <span data-ttu-id="25ff4-180">モデルのトレーニング中に NULL が検出された場合はエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="25ff4-180">An error will result if Analysis Services encounters a null during model training.</span></span>  
  
 <span data-ttu-id="25ff4-181">マイニング構造列に適用されます。</span><span class="sxs-lookup"><span data-stu-id="25ff4-181">Applies to the mining structure column.</span></span>  
  
 <span data-ttu-id="25ff4-182">MODEL_EXISTENCE_ONLY</span><span class="sxs-lookup"><span data-stu-id="25ff4-182">MODEL_EXISTENCE_ONLY</span></span>  
 <span data-ttu-id="25ff4-183">列が、`Missing` および `Existing` の 2 つの可能な状態を持つ列として扱われることを示します。</span><span class="sxs-lookup"><span data-stu-id="25ff4-183">Means that the column will be treated as having two possible states: `Missing` and `Existing`.</span></span> <span data-ttu-id="25ff4-184">NULL は `Missing` 値として扱われます。</span><span class="sxs-lookup"><span data-stu-id="25ff4-184">A null is treated as a `Missing` value.</span></span>  
  
 <span data-ttu-id="25ff4-185">マイニング モデル列に適用されます。</span><span class="sxs-lookup"><span data-stu-id="25ff4-185">Applies to the mining model column.</span></span>  
  
 <span data-ttu-id="25ff4-186">マイニング モデルでの Missing 値の使用、および確率スコアへの Missing 値の影響の詳細については、「[不足値 (Analysis Services - データ マイニング)](missing-values-analysis-services-data-mining.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="25ff4-186">For more information about the use of Missing values in mining models, and how missing values affect probability scores, see [Missing Values &#40;Analysis Services - Data Mining&#41;](missing-values-analysis-services-data-mining.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25ff4-187">必要条件</span><span class="sxs-lookup"><span data-stu-id="25ff4-187">Requirements</span></span>  
 <span data-ttu-id="25ff4-188">ケース テーブルにはケース ID 列が必要です。</span><span class="sxs-lookup"><span data-stu-id="25ff4-188">The case table must have a case ID column.</span></span> <span data-ttu-id="25ff4-189">オプションで、ケースに関する属性を格納する他の列をケース テーブルに含めることができます。</span><span class="sxs-lookup"><span data-stu-id="25ff4-189">Optionally the case table can contain other columns that store attributes about the case.</span></span>  
  
 <span data-ttu-id="25ff4-190">Microsoft シーケンス クラスター アルゴリズムには、入れ子になったテーブルとして格納されるシーケンス情報が必要です。</span><span class="sxs-lookup"><span data-stu-id="25ff4-190">The Microsoft Sequence Clustering algorithm requires sequence information, stored as a nested table.</span></span> <span data-ttu-id="25ff4-191">入れ子になったテーブルには、1 つの Key Sequence 列が必要です。</span><span class="sxs-lookup"><span data-stu-id="25ff4-191">The nested table must have a single Key Sequence column.</span></span> <span data-ttu-id="25ff4-192">`Key Sequence` 列には、文字列データ型など、並べ替え可能な任意の型のデータを含めることができますが、ケースごとに一意の値を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="25ff4-192">A `Key Sequence` column can contain any type of data that can be sorted, including string data types, but the column must contain unique values for each case.</span></span> <span data-ttu-id="25ff4-193">さらに、モデルを処理する前に、ケース テーブルと入れ子になったテーブルの両方が、テーブルを関連付けるキーに基づいて昇順に並べ替えられていることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="25ff4-193">Moreover, before you process the model, you must ensure that both the case table and the nested table are sorted in ascending order on the key that relates the tables.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="25ff4-194">Microsoft シーケンス アルゴリズムを使用するがシーケンス列は使用しないモデルを作成する場合、結果として得られるモデルでは、シーケンスが含まれるのではなく、モデルに含まれている他の属性に基づいてケースがクラスター化されるだけです。</span><span class="sxs-lookup"><span data-stu-id="25ff4-194">If you create a model that uses the Microsoft Sequence algorithm but do not use a sequence column, the resulting model will not contain any sequences, but will simply cluster cases based on other attributes that are included in the model.</span></span>  
  
### <a name="input-and-predictable-columns"></a><span data-ttu-id="25ff4-195">入力列と予測可能列</span><span class="sxs-lookup"><span data-stu-id="25ff4-195">Input and Predictable Columns</span></span>  
 <span data-ttu-id="25ff4-196">[!INCLUDE[msCoName](../../includes/msconame-md.md)] シーケンス クラスター アルゴリズムでは、次の表に示す特定の入力列と予測可能列がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="25ff4-196">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Sequence Clustering algorithm supports the specific input columns and predictable columns that are listed in the following table.</span></span> <span data-ttu-id="25ff4-197">マイニング モデルにおけるコンテンツの種類の意味については、「[コンテンツの種類 &#40;データ マイニング&#41;](content-types-data-mining.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="25ff4-197">For more information about what the content types mean when used in a mining model, see [Content Types &#40;Data Mining&#41;](content-types-data-mining.md).</span></span>  
  
|<span data-ttu-id="25ff4-198">列</span><span class="sxs-lookup"><span data-stu-id="25ff4-198">Column</span></span>|<span data-ttu-id="25ff4-199">コンテンツの種類</span><span class="sxs-lookup"><span data-stu-id="25ff4-199">Content types</span></span>|  
|------------|-------------------|  
|<span data-ttu-id="25ff4-200">入力属性</span><span class="sxs-lookup"><span data-stu-id="25ff4-200">Input attribute</span></span>|<span data-ttu-id="25ff4-201">Continuous、Cyclical、Discrete、Discretized、Key、Key Sequence、Table、Ordered</span><span class="sxs-lookup"><span data-stu-id="25ff4-201">Continuous, Cyclical, Discrete, Discretized, Key, Key Sequence, Table, and Ordered</span></span>|  
|<span data-ttu-id="25ff4-202">予測可能な属性</span><span class="sxs-lookup"><span data-stu-id="25ff4-202">Predictable attribute</span></span>|<span data-ttu-id="25ff4-203">Continuous、Cyclical、Discrete、Discretized、Table、Ordered</span><span class="sxs-lookup"><span data-stu-id="25ff4-203">Continuous, Cyclical, Discrete, Discretized, Table, and Ordered</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="25ff4-204">解説</span><span class="sxs-lookup"><span data-stu-id="25ff4-204">Remarks</span></span>  
  
-   <span data-ttu-id="25ff4-205">シーケンスの予測には [PredictSequence (DMX)](/sql/dmx/predictsequence-dmx) 関数を使用します。</span><span class="sxs-lookup"><span data-stu-id="25ff4-205">Use the [PredictSequence &#40;DMX&#41;](/sql/dmx/predictsequence-dmx) function for Prediction of Sequences.</span></span> <span data-ttu-id="25ff4-206">シーケンス予測をサポートするのエディションの詳細につい [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ては、「 [SQL Server 2012 の各エディションがサポートする機能](https://go.microsoft.com/fwlink/?linkid=232473)」 (を参照してください https://go.microsoft.com/fwlink/?linkid=232473) 。</span><span class="sxs-lookup"><span data-stu-id="25ff4-206">For more information about the editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that support Sequence Prediction, see [Features Supported by the Editions of SQL Server 2012](https://go.microsoft.com/fwlink/?linkid=232473) (https://go.microsoft.com/fwlink/?linkid=232473).</span></span>  
  
-   <span data-ttu-id="25ff4-207">[!INCLUDE[msCoName](../../includes/msconame-md.md)] シーケンス クラスター アルゴリズムでは、Predictive Model Markup Language (PMML) を使用したマイニング モデルの作成はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="25ff4-207">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Sequence Clustering algorithm does not support using the Predictive Model Markup Language (PMML) to create mining models.</span></span>  
  
-   <span data-ttu-id="25ff4-208">[!INCLUDE[msCoName](../../includes/msconame-md.md)] シーケンス クラスター アルゴリズムでは、ドリルスルー、OLAP マイニング モデルの使用、およびデータ マイニング ディメンションの使用がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="25ff4-208">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Sequence Clustering algorithm supports drillthrough, the use of OLAP mining models, and the use of data mining dimensions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25ff4-209">参照</span><span class="sxs-lookup"><span data-stu-id="25ff4-209">See Also</span></span>  
 <span data-ttu-id="25ff4-210">[Microsoft シーケンスクラスターアルゴリズム](microsoft-sequence-clustering-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="25ff4-210">[Microsoft Sequence Clustering Algorithm](microsoft-sequence-clustering-algorithm.md) </span></span>  
 <span data-ttu-id="25ff4-211">[シーケンスクラスターモデルのクエリ例](clustering-model-query-examples.md) </span><span class="sxs-lookup"><span data-stu-id="25ff4-211">[Sequence Clustering Model Query Examples](clustering-model-query-examples.md) </span></span>  
 [<span data-ttu-id="25ff4-212">シーケンス クラスター モデルのマイニング モデル コンテンツ (Analysis Services - データ マイニング)</span><span class="sxs-lookup"><span data-stu-id="25ff4-212">Mining Model Content for Sequence Clustering Models &#40;Analysis Services - Data Mining&#41;</span></span>](mining-model-content-for-sequence-clustering-models.md)  
  
  
