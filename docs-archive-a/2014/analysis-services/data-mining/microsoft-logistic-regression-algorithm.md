---
title: Microsoft ロジスティック回帰アルゴリズム |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- logical regression algorithms [Analysis Services]
- algorithms [data mining]
- neural network algorithms [Analysis Services]
- regression algorithms [Analysis Services]
ms.assetid: 3dd54d07-1c3b-4b87-b7f0-b962ed8cf844
author: minewiskan
ms.author: owend
ms.openlocfilehash: 56a1b0b82f82b62e55d0c7fdd528195b5713fcf9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645258"
---
# <a name="microsoft-logistic-regression-algorithm"></a><span data-ttu-id="8a7c4-102">Microsoft ロジスティック回帰アルゴリズム</span><span class="sxs-lookup"><span data-stu-id="8a7c4-102">Microsoft Logistic Regression Algorithm</span></span>
  <span data-ttu-id="8a7c4-103">ロジスティック回帰は、バイナリ結果のモデリングに使用される代表的な統計手法です。</span><span class="sxs-lookup"><span data-stu-id="8a7c4-103">Logistic regression is a well-known statistical technique that is used for modeling binary outcomes.</span></span>  
  
 <span data-ttu-id="8a7c4-104">ロジスティック回帰は、異なる学習技法を使用してさまざまな方法で統計研究に実装されます。</span><span class="sxs-lookup"><span data-stu-id="8a7c4-104">There are various implementations of logistic regression in statistics research, using different learning techniques.</span></span> <span data-ttu-id="8a7c4-105">[!INCLUDE[msCoName](../../includes/msconame-md.md)] ロジスティック回帰アルゴリズムは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] ニューラル ネットワーク アルゴリズムの一種を使用して実装されました。</span><span class="sxs-lookup"><span data-stu-id="8a7c4-105">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Logistic Regression algorithm has been implemented by using a variation of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network algorithm.</span></span> <span data-ttu-id="8a7c4-106">このアルゴリズムは、ニューラル ネットワークの特性の多くを共有しますが、トレーニングはニューラル ネットワークよりも容易です。</span><span class="sxs-lookup"><span data-stu-id="8a7c4-106">This algorithm shares many of the qualities of neural networks but is easier to train.</span></span>  
  
 <span data-ttu-id="8a7c4-107">ロジスティック回帰の利点の 1 つは、このアルゴリズムはあらゆる種類の入力を取得するほど柔軟性が高く、次に示すいくつかの分析タスクをサポートすることです。</span><span class="sxs-lookup"><span data-stu-id="8a7c4-107">One advantage of logistic regression is that the algorithm is highly flexible, taking any kind of input, and supports several different analytical tasks:</span></span>  
  
-   <span data-ttu-id="8a7c4-108">人口統計を使用して、特定の病気のリスクなど、結果に関する予測を行う。</span><span class="sxs-lookup"><span data-stu-id="8a7c4-108">Use demographics to make predictions about outcomes, such as risk for a certain disease.</span></span>  
  
-   <span data-ttu-id="8a7c4-109">結果に影響する要素を探索し、重み付けを行う。</span><span class="sxs-lookup"><span data-stu-id="8a7c4-109">Explore and weight the factors that contribute to a result.</span></span> <span data-ttu-id="8a7c4-110">たとえば、顧客が店舗を繰り返し訪れる要因となる要素を求める。</span><span class="sxs-lookup"><span data-stu-id="8a7c4-110">For example, find the factors that influence customers to make a repeat visit to a store.</span></span>  
  
-   <span data-ttu-id="8a7c4-111">多くの属性を持つドキュメント、電子メール、またはその他のオブジェクトを分類する。</span><span class="sxs-lookup"><span data-stu-id="8a7c4-111">Classify documents, e-mail, or other objects that have many attributes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8a7c4-112">例</span><span class="sxs-lookup"><span data-stu-id="8a7c4-112">Example</span></span>  
 <span data-ttu-id="8a7c4-113">類似の人口統計情報を共有し、Adventure Works 社から製品を購入する人々のグループがあるとします。</span><span class="sxs-lookup"><span data-stu-id="8a7c4-113">Consider a group of people who share similar demographic information and who buy products from the Adventure Works company.</span></span> <span data-ttu-id="8a7c4-114">データをモデリング特定の結果 (対象製品の購入など) に関連付けると、人工統計情報が人々の対象製品を購入する確率にどのようにかかわるかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="8a7c4-114">By modeling the data to relate to a specific outcome, such as purchase of a target product, you can see how the demographic information contributes to someone's likelihood of buying the target product.</span></span>  
  
## <a name="how-the-algorithm-works"></a><span data-ttu-id="8a7c4-115">アルゴリズムの動作</span><span class="sxs-lookup"><span data-stu-id="8a7c4-115">How the Algorithm Works</span></span>  
 <span data-ttu-id="8a7c4-116">ロジスティック回帰は、結果のペアに対する複数の要素の影響を確認するために使用される代表的な統計手法です。</span><span class="sxs-lookup"><span data-stu-id="8a7c4-116">Logistic regression is a well-known statistical method for determining the contribution of multiple factors to a pair of outcomes.</span></span> <span data-ttu-id="8a7c4-117">Microsoft による実装では、変更されたニューラル ネットワークを使用して入力と出力の関係をモデル化します。</span><span class="sxs-lookup"><span data-stu-id="8a7c4-117">The Microsoft implementation uses a modified neural network to model the relationships between inputs and outputs.</span></span> <span data-ttu-id="8a7c4-118">出力における各入力の影響が評価され、完成したモデルではさまざまな入力が重み付けされます。</span><span class="sxs-lookup"><span data-stu-id="8a7c4-118">The effect of each input on the output is measured, and the various inputs are weighted in the finished model.</span></span> <span data-ttu-id="8a7c4-119">ロジスティック回帰という名前は、極端な値の影響を最小限に抑えるためにロジスティック変換を使用してデータ曲線が圧縮されるという事実に基づいています。</span><span class="sxs-lookup"><span data-stu-id="8a7c4-119">The name logistic regression comes from the fact that the data curve is compressed by using a logistic transformation, to minimize the effect of extreme values.</span></span> <span data-ttu-id="8a7c4-120">実装の詳細とアルゴリズムのカスタマイズ方法については、「 [Microsoft ロジスティック回帰アルゴリズム テクニカル リファレンス](microsoft-logistic-regression-algorithm-technical-reference.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8a7c4-120">For more information about the implementation, and how to customize the algorithm, see [Microsoft Logistic Regression Algorithm Technical Reference](microsoft-logistic-regression-algorithm-technical-reference.md).</span></span>  
  
## <a name="data-required-for-logistic-regression-models"></a><span data-ttu-id="8a7c4-121">ロジスティック回帰モデルに必要なデータ</span><span class="sxs-lookup"><span data-stu-id="8a7c4-121">Data Required for Logistic Regression Models</span></span>  
 <span data-ttu-id="8a7c4-122">ロジスティック回帰モデルのトレーニングに使用するデータを用意する際には、必要なデータ量やデータの使用方法など、このアルゴリズムにおける要件を把握しておいてください。</span><span class="sxs-lookup"><span data-stu-id="8a7c4-122">When you prepare data for use in training a logistic regression model, you should understand the requirements for the particular algorithm, including how much data is needed, and how the data is used.</span></span>  
  
 <span data-ttu-id="8a7c4-123">ロジスティック回帰モデルの要件は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="8a7c4-123">The requirements for a logistic regression model are as follows:</span></span>  
  
 <span data-ttu-id="8a7c4-124">**単一キー列** : それぞれのモデルには、各レコードを一意に識別する数値列またはテキスト列が 1 つ含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="8a7c4-124">**A single key column** Each model must contain one numeric or text column that uniquely identifies each record.</span></span> <span data-ttu-id="8a7c4-125">複合キーは使用できません。</span><span class="sxs-lookup"><span data-stu-id="8a7c4-125">Compound keys are not allowed.</span></span>  
  
 <span data-ttu-id="8a7c4-126">**入力列** : 各モデルには、分析の要素として使用される値が含まれた入力列が 1 つ以上必要です。</span><span class="sxs-lookup"><span data-stu-id="8a7c4-126">**Input columns** Each model must contain at least one input column that contains the values that are used as factors in analysis.</span></span> <span data-ttu-id="8a7c4-127">入力列はいくつあってもかまいませんが、各列内の値の数によっては、列を追加するとモデルのトレーニングにかかる時間が長くなる場合があります。</span><span class="sxs-lookup"><span data-stu-id="8a7c4-127">You can have as many input columns as you want, but depending on the number of values in each column, the addition of extra columns can increase the time it takes to train the model.</span></span>  
  
 <span data-ttu-id="8a7c4-128">**1 つ以上の予測可能列** : モデルには、連続する数値データを含む任意のデータ型の予測可能列が 1 つ以上必要です。</span><span class="sxs-lookup"><span data-stu-id="8a7c4-128">**At least one predictable column** The model must contain at least one predictable column of any data type, including continuous numeric data.</span></span> <span data-ttu-id="8a7c4-129">予測可能列の値は、モデルへの入力として扱うことも、予測のみに使用するよう指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="8a7c4-129">The values of the predictable column can also be treated as inputs to the model, or you can specify that it be used for prediction only.</span></span> <span data-ttu-id="8a7c4-130">入れ子になったテーブルは予測可能列では使用できませんが、入力としては使用できます。</span><span class="sxs-lookup"><span data-stu-id="8a7c4-130">Nested tables are not allowed for predictable columns, but can be used as inputs.</span></span>  
  
 <span data-ttu-id="8a7c4-131">ロジスティック回帰モデルでサポートされるコンテンツの種類とデータ型の詳細については、「 [Microsoft ロジスティック回帰アルゴリズム テクニカル リファレンス](microsoft-logistic-regression-algorithm-technical-reference.md)」の「必要条件」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8a7c4-131">For more detailed information about the content types and data types supported for logistic regression models, see the Requirements section of [Microsoft Logistic Regression Algorithm Technical Reference](microsoft-logistic-regression-algorithm-technical-reference.md).</span></span>  
  
## <a name="viewing-a-logistic-regression-model"></a><span data-ttu-id="8a7c4-132">ロジスティック回帰モデルの表示</span><span class="sxs-lookup"><span data-stu-id="8a7c4-132">Viewing a Logistic Regression Model</span></span>  
 <span data-ttu-id="8a7c4-133">モデルを参照するには、Microsoft ニューラル ネットワーク ビューアーまたは Microsoft 汎用コンテンツ ツリー ビューアーを使用できます。</span><span class="sxs-lookup"><span data-stu-id="8a7c4-133">To explore the model, you can use the Microsoft Neural Network Viewer, or the Microsoft Generic Content Tree Viewer.</span></span>  
  
 <span data-ttu-id="8a7c4-134">Microsoft ニューラル ネットワーク ビューアーを使用してモデルを表示すると、Analysis Services には、特定の結果に影響する要素がその重要度で順位付けされて表示されます。</span><span class="sxs-lookup"><span data-stu-id="8a7c4-134">When you view the model by using the Microsoft Neural Network Viewer, Analysis Services shows you the factors that contribute to a particular outcome, ranked by their importance.</span></span> <span data-ttu-id="8a7c4-135">比較する属性と値を選択できます。</span><span class="sxs-lookup"><span data-stu-id="8a7c4-135">You can choose an attribute and values to compare.</span></span> <span data-ttu-id="8a7c4-136">詳細については、「 [Microsoft ニューラル ネットワーク ビューアーを使用したモデルの参照](browse-a-model-using-the-microsoft-neural-network-viewer.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8a7c4-136">For more information, see [Browse a Model Using the Microsoft Neural Network Viewer](browse-a-model-using-the-microsoft-neural-network-viewer.md).</span></span>  
  
 <span data-ttu-id="8a7c4-137">さらに詳細を知るには、Microsoft 汎用コンテンツ ツリー ビューアーを使用してモデルの詳細を参照できます。</span><span class="sxs-lookup"><span data-stu-id="8a7c4-137">If you want to know more, you can browse the model details by using the Microsoft Generic Content Tree Viewer.</span></span> <span data-ttu-id="8a7c4-138">ロジスティック回帰モデルのモデル コンテンツには、モデルに使用されるすべての入力を示すマージナル ノード、および予測可能な属性を表すサブネットワークが含まれます。</span><span class="sxs-lookup"><span data-stu-id="8a7c4-138">The model content for a logistic regression model includes a marginal node that shows you the all the inputs used for the model, and subnetworks for the predictable attributes.</span></span> <span data-ttu-id="8a7c4-139">詳細については、「 [ロジスティック回帰モデルのマイニング モデル コンテンツ (Analysis Services - データ マイニング)](mining-model-content-for-logistic-regression-models.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8a7c4-139">For more information, see [Mining Model Content for Logistic Regression Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-logistic-regression-models.md).</span></span>  
  
## <a name="creating-predictions"></a><span data-ttu-id="8a7c4-140">予測の作成</span><span class="sxs-lookup"><span data-stu-id="8a7c4-140">Creating Predictions</span></span>  
 <span data-ttu-id="8a7c4-141">モデルのトレーニング後、モデル コンテンツに対するクエリを作成して回帰係数およびその他の詳細を取得したり、モデルを使用して予測を作成したりできます。</span><span class="sxs-lookup"><span data-stu-id="8a7c4-141">After the model has been trained, you can create queries against the model content to get the regression coefficients and other details, or you can use the model to make predictions.</span></span>  
  
-   <span data-ttu-id="8a7c4-142">データ マイニング モデルに対するクエリの作成方法については、「 [データ マイニング クエリ](data-mining-queries.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8a7c4-142">For general information about how to create queries against a data mining model, see [Data Mining Queries](data-mining-queries.md).</span></span>  
  
-   <span data-ttu-id="8a7c4-143">ロジスティック回帰モデルでのクエリの例については、「 [クラスタリング モデルのクエリ例](clustering-model-query-examples.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8a7c4-143">For examples of queries on a logistic regression model, see [Clustering Model Query Examples](clustering-model-query-examples.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8a7c4-144">解説</span><span class="sxs-lookup"><span data-stu-id="8a7c4-144">Remarks</span></span>  
  
-   <span data-ttu-id="8a7c4-145">ドリルスルーはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="8a7c4-145">Does not support drillthrough.</span></span> <span data-ttu-id="8a7c4-146">これは、マイニング モデルのノードの構造がその基になるデータと必ずしも直接対応しているわけではないからです。</span><span class="sxs-lookup"><span data-stu-id="8a7c4-146">This is because the structure of nodes in the mining model does not necessarily correspond directly to the underlying data.</span></span>  
  
-   <span data-ttu-id="8a7c4-147">データ マイニング ディメンションの作成はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="8a7c4-147">Does not support the creation of data mining dimensions.</span></span>  
  
-   <span data-ttu-id="8a7c4-148">OLAP マイニング モデルの使用がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="8a7c4-148">Supports the use of OLAP mining models.</span></span>  
  
-   <span data-ttu-id="8a7c4-149">Predictive Model Markup Language (PMML) を使用したマイニング モデルの作成はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="8a7c4-149">Does not support the use of Predictive Model Markup Language (PMML) to create mining models.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a7c4-150">参照</span><span class="sxs-lookup"><span data-stu-id="8a7c4-150">See Also</span></span>  
 <span data-ttu-id="8a7c4-151">[ロジスティック回帰モデルのマイニングモデルコンテンツ &#40;Analysis Services データマイニング&#41;](mining-model-content-for-logistic-regression-models.md) </span><span class="sxs-lookup"><span data-stu-id="8a7c4-151">[Mining Model Content for Logistic Regression Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-logistic-regression-models.md) </span></span>  
 <span data-ttu-id="8a7c4-152">[Microsoft ロジスティック回帰アルゴリズムテクニカルリファレンス](microsoft-logistic-regression-algorithm-technical-reference.md) </span><span class="sxs-lookup"><span data-stu-id="8a7c4-152">[Microsoft Logistic Regression Algorithm Technical Reference](microsoft-logistic-regression-algorithm-technical-reference.md) </span></span>  
 [<span data-ttu-id="8a7c4-153">ロジスティック回帰モデルのクエリ例</span><span class="sxs-lookup"><span data-stu-id="8a7c4-153">Logistic Regression Model Query Examples</span></span>](logistic-regression-model-query-examples.md)  
  
  
