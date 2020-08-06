---
title: データマイニングモデルを作成する |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data mining models, creating
- forecasting [data mining]
- mining models, creating
- clustering [data mining]
- association [data mining]
- data modeling [data mining]
- estimation
- classification [data mining]
ms.assetid: 804b7db3-1f6a-4f73-a81d-bbe02520d7c6
author: minewiskan
ms.author: owend
ms.openlocfilehash: 1e27739d3733c0b48dc6cff3e83e01f9cb12bce7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641907"
---
# <a name="creating-a-data-mining-model"></a><span data-ttu-id="8b344-102">データ マイニング モデルの作成</span><span class="sxs-lookup"><span data-stu-id="8b344-102">Creating a Data Mining Model</span></span>
  <span data-ttu-id="8b344-103">データモデリングは、*アルゴリズム*をデータに適用してパターンや傾向を構築するデータマイニングの手順です。</span><span class="sxs-lookup"><span data-stu-id="8b344-103">Data modeling is the step of data mining where you build patterns and trends by applying *algorithms* to data.</span></span> <span data-ttu-id="8b344-104">その後、それらのデータを使って追加の分析を行ったり、予測を立てたりすることができます。</span><span class="sxs-lookup"><span data-stu-id="8b344-104">Later you can use those patterns for analysis, or to make predictions.</span></span>  
  
 <span data-ttu-id="8b344-105">Office 用データ マイニング アドインは、ウィザードによるデータ マイニングをサポートすることで、モデルの作成を簡素化しています。</span><span class="sxs-lookup"><span data-stu-id="8b344-105">The Data Mining Add-ins for Office support data mining through wizards that make it easy to create models.</span></span> <span data-ttu-id="8b344-106">ウィザードでは、データの分析、相関関係の特定、あらゆる変数の統計的有意性の計算、最適なモデルの自動選択が実行されます。</span><span class="sxs-lookup"><span data-stu-id="8b344-106">The wizards analyze the data, identify correlations, compute statistical significance of all variables, and automatically select the best model.</span></span>  
  
 <span data-ttu-id="8b344-107">この機能は、およびによって提供されるデータマイニングツールと同様に、すべての機能を備えていますが、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] ウィザードと使い慣れた Excel インターフェイスを組み合わせることにより、データマイニングの作成、変更、および使用が簡単になります。</span><span class="sxs-lookup"><span data-stu-id="8b344-107">Although this functionality is every bit as powerful as the data mining tools provided by [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] and [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], the combination of wizards and the familiar Excel interface makes it easy to create, modify, and use data mining.</span></span>  
  
## <a name="advanced-data-mining"></a><span data-ttu-id="8b344-108">詳細設定 (データ マイニング)</span><span class="sxs-lookup"><span data-stu-id="8b344-108">Advanced (Data Mining)</span></span>  
 <span data-ttu-id="8b344-109">詳細設定ウィザードでは、のデータマイニングアルゴリズムの1つを使用して、Excel に格納されているデータに基づいて新しいデータマイニングモデルを作成でき [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="8b344-109">The Advanced wizards let you create new data mining models, based on data stored in Excel, by using one of the data mining algorithms in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>  
  
### <a name="create-mining-structure"></a><span data-ttu-id="8b344-110">マイニング構造の作成</span><span class="sxs-lookup"><span data-stu-id="8b344-110">Create Mining Structure</span></span>  
 <span data-ttu-id="8b344-111">マイニング構造の作成ウィザードを使用すると、新しいデータ マイニング構造を構築し、複数のマイニング モデルの基礎として使用できます。</span><span class="sxs-lookup"><span data-stu-id="8b344-111">The Create Mining Structure wizard helps you build a new data mining structure, which you can use as the basis for multiple mining models.</span></span> <span data-ttu-id="8b344-112">このウィザードには、テスト セットとして使用するデータの一部を確保するオプションが用意されているので、一貫したテスト標準に従って同じデータを使用するすべてのモデルを評価できます。</span><span class="sxs-lookup"><span data-stu-id="8b344-112">The wizard gives you the option to set aside a portion of the data to use as a testing set, so that you can evaluate all models that use the same data according to a consistent testing standard.</span></span>  
  
 [<span data-ttu-id="8b344-113">SQL Server データマイニングアドイン &#40;マイニング構造の作成&#41;</span><span class="sxs-lookup"><span data-stu-id="8b344-113">Create Mining Structure &#40;SQL Server Data Mining Add-ins&#41;</span></span>](create-mining-structure-sql-server-data-mining-add-ins.md)  
  
### <a name="add-model-to-structure"></a><span data-ttu-id="8b344-114">構造へのモデルの追加</span><span class="sxs-lookup"><span data-stu-id="8b344-114">Add Model to Structure</span></span>  
 <span data-ttu-id="8b344-115">構造へのモデルの追加ウィザードを使用すると、既存のデータ マイニング構造を選択して、その構造に使用する新しいデータ マイニング モデルを作成できます。</span><span class="sxs-lookup"><span data-stu-id="8b344-115">The Add Model to Structure wizard lets you choose an existing data mining structure and create a new data mining model for it.</span></span> <span data-ttu-id="8b344-116">複数のマイニング モデルを構造に追加し、パラメーターを変更するか、別のデータ マイニング アルゴリズムを選択して、出力をカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="8b344-116">You can add multiple mining models to a structure, changing the parameters or choosing different data mining algorithms, and customize the output.</span></span>  
  
 [<span data-ttu-id="8b344-117">Excel 用データマイニングアドイン &#40;構造へのモデルの追加&#41;</span><span class="sxs-lookup"><span data-stu-id="8b344-117">Add Model to Structure &#40;Data Mining Add-ins for Excel&#41;</span></span>](add-model-to-structure-data-mining-add-ins-for-excel.md)  
  
## <a name="analyze-key-influencers-analyze"></a><span data-ttu-id="8b344-118">主要な影響元の分析 (分析)</span><span class="sxs-lookup"><span data-stu-id="8b344-118">Analyze Key Influencers (Analyze)</span></span>  
 <span data-ttu-id="8b344-119">目的の列または出力値を選択すると、アルゴリズムがすべての入力データを分析して、対象に最大の影響を与えている要因を特定します。</span><span class="sxs-lookup"><span data-stu-id="8b344-119">You choose a column or output value of interest, and then the algorithm analyzes all the input data to identify the factors that have the most influence on the target.</span></span> <span data-ttu-id="8b344-120">必要に応じて、2 つの値を比較するレポートを作成できます。これにより、影響元がどのように変化するかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="8b344-120">Optionally, you can create a report that compares any two values, so that you can see how the influencers change.</span></span>  
  
 <span data-ttu-id="8b344-121">**主要影響**元の分析ツールでは、Microsoft の単純 Bayes アルゴリズムが使用されます。</span><span class="sxs-lookup"><span data-stu-id="8b344-121">The **Analyze Key Influencers** tool uses the Microsoft Naïve Bayes algorithm.</span></span>  
  
 [<span data-ttu-id="8b344-122">Excel 用のテーブル分析ツール &#40;主要な影響元の分析&#41;</span><span class="sxs-lookup"><span data-stu-id="8b344-122">Analyze Key Influencers &#40;Table Analysis Tools for Excel&#41;</span></span>](analyze-key-influencers-table-analysis-tools-for-excel.md)  
  
## <a name="associate-data-mining"></a><span data-ttu-id="8b344-123">アソシエーション (データ マイニング)</span><span class="sxs-lookup"><span data-stu-id="8b344-123">Associate (Data Mining)</span></span>  
 <span data-ttu-id="8b344-124">**関連付け**ウィザードでは、マーケットバスケット分析などで、複数のトランザクションに出現する項目間の関連付けを検出するアソシエーションモデルを構築します。</span><span class="sxs-lookup"><span data-stu-id="8b344-124">The **Associate** wizard builds an association model that detects associations between items that appear in multiple transactions: for example, in market basket analysis.</span></span>  
  
 [<span data-ttu-id="8b344-125">関連付けウィザード &#40;Excel 用データマイニングクライアント&#41;</span><span class="sxs-lookup"><span data-stu-id="8b344-125">Associate Wizard &#40;Data Mining Client for Excel&#41;</span></span>](associate-wizard-data-mining-client-for-excel.md)  
  
## <a name="classify-data-mining"></a><span data-ttu-id="8b344-126">分類 (データ マイニング)</span><span class="sxs-lookup"><span data-stu-id="8b344-126">Classify (Data Mining)</span></span>  
 <span data-ttu-id="8b344-127">**分類**ウィザードでは、ターゲットの結果に寄与する要因を分析する分類モデルを構築します。</span><span class="sxs-lookup"><span data-stu-id="8b344-127">The  **Classify** wizard builds a classification model that analyzes the factors that contributed to a target outcome.</span></span> <span data-ttu-id="8b344-128">このウィザードでは、デシジョン ツリー、Naïve Bayes、ニューラル ネットワークを含む複数のアルゴリズムを使用できます。</span><span class="sxs-lookup"><span data-stu-id="8b344-128">You can use multiple algorithms with this wizard, including Decision Trees, Naïve Bayes, and Neural Networks.</span></span>  
  
 [<span data-ttu-id="8b344-129">分類ウィザード &#40;Excel 用データマイニングアドイン&#41;</span><span class="sxs-lookup"><span data-stu-id="8b344-129">Classify Wizard &#40;Data Mining Add-ins for Excel&#41;</span></span>](classify-wizard-data-mining-add-ins-for-excel.md)  
  
## <a name="cluster-data-mining"></a><span data-ttu-id="8b344-130">クラスター (データ マイニング)</span><span class="sxs-lookup"><span data-stu-id="8b344-130">Cluster (Data Mining)</span></span>  
 <span data-ttu-id="8b344-131">**クラスター**ウィザードは、類似した特性を共有する行グループを検出するクラスターモデルを構築します。</span><span class="sxs-lookup"><span data-stu-id="8b344-131">The **Cluster** wizard builds a clustering model that detects groups of rows that share similar characteristics.</span></span> <span data-ttu-id="8b344-132">クラスタリング (*セグメンテーション*と呼ばれることもあります) は、新しいデータのパターンとグループ化について理解する際に非常に役立つ教師なし学習手法です。</span><span class="sxs-lookup"><span data-stu-id="8b344-132">Clustering (sometimes called *segmentation*) is an unsupervised learning technique that is very useful when trying to understand patterns and groupings in new data.</span></span>  
  
 <span data-ttu-id="8b344-133">Microsoft クラスタリング アルゴリズムは、K-Means および Expectation Maximization (EM) クラスタリング両方について、複数の種類をサポートします。</span><span class="sxs-lookup"><span data-stu-id="8b344-133">The Microsoft Clustering algorithm supports several varieties of both K-means and Expectation maximization (EM) clustering</span></span>  
  
 <span data-ttu-id="8b344-134">[クラスターウィザードでは、Excel 用データマイニングアドイン &#40;&#41;](cluster-wizard-data-mining-add-ins-for-excel.md)ます。</span><span class="sxs-lookup"><span data-stu-id="8b344-134">[Cluster Wizard &#40;Data Mining Add-ins for Excel&#41;](cluster-wizard-data-mining-add-ins-for-excel.md).</span></span>  
  
## <a name="detect-categories-analyze"></a><span data-ttu-id="8b344-135">カテゴリの検出 (分析)</span><span class="sxs-lookup"><span data-stu-id="8b344-135">Detect Categories (Analyze)</span></span>  
 <span data-ttu-id="8b344-136">**カテゴリの検出**ツールを使用すると、データセットを追加し、クラスタリングを適用してデータのグループを検索できます。</span><span class="sxs-lookup"><span data-stu-id="8b344-136">The **Detect Categories** tool lets you add any data set and apply clustering to find groupings of data.</span></span> <span data-ttu-id="8b344-137">類似点を見つけて、さらに分析するグループを作成する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="8b344-137">It's useful for finding similarities and for creating groups to further analyze.</span></span>  
  
 <span data-ttu-id="8b344-138">**カテゴリの検出**ツールは、Microsoft クラスタリングアルゴリズムを使用します。</span><span class="sxs-lookup"><span data-stu-id="8b344-138">The **Detect Categories** tool uses the Microsoft Clustering algorithm.</span></span>  
  
 [<span data-ttu-id="8b344-139">Excel 用のテーブル分析ツール &#40;のカテゴリの検出&#41;</span><span class="sxs-lookup"><span data-stu-id="8b344-139">Detect Categories &#40;Table Analysis Tools for Excel&#41;</span></span>](detect-categories-table-analysis-tools-for-excel.md)  
  
## <a name="estimate-data-mining"></a><span data-ttu-id="8b344-140">推定 (データ マイニング)</span><span class="sxs-lookup"><span data-stu-id="8b344-140">Estimate (Data Mining)</span></span>  
 <span data-ttu-id="8b344-141">推定ウィザードを使用すると、データのパターンを抽出し、そのパターンを基に、連続する数値、日付、または時刻の値を予測する推定モデルを構築できます。</span><span class="sxs-lookup"><span data-stu-id="8b344-141">The Estimate wizard builds an estimation model that extracts data patterns and uses the patterns to predict continuous numeric, date, or time values.</span></span> <span data-ttu-id="8b344-142">[!INCLUDE[msCoName](../includes/msconame-md.md)] のデシジョン ツリー アルゴリズムが使用されます。</span><span class="sxs-lookup"><span data-stu-id="8b344-142">It uses the [!INCLUDE[msCoName](../includes/msconame-md.md)] Decision Trees algorithm.</span></span>  
  
 [<span data-ttu-id="8b344-143">推定ウィザード &#40;Excel 用データマイニングアドイン&#41;</span><span class="sxs-lookup"><span data-stu-id="8b344-143">Estimate Wizard &#40;Data Mining Add-ins for Excel&#41;</span></span>](estimate-wizard-data-mining-add-ins-for-excel.md)  
  
## <a name="fill-from-example-analyze"></a><span data-ttu-id="8b344-144">自動推論 (分析)</span><span class="sxs-lookup"><span data-stu-id="8b344-144">Fill From Example (Analyze)</span></span>  
 <span data-ttu-id="8b344-145">**Fill From サンプル**ツールを使用すると、欠損値を埋め込むことができます。</span><span class="sxs-lookup"><span data-stu-id="8b344-145">The **Fill From Example** tool helps you impute missing values.</span></span> <span data-ttu-id="8b344-146">不足値の例をいくつか指定すると、このツールはテーブル内のすべてのデータに基づいてパターンを作成し、データのパターンに基づいて新しい値を推奨します。</span><span class="sxs-lookup"><span data-stu-id="8b344-146">You provide some examples of what the missing values should be, and the tool builds patterns based on all data in the table, and then recommends new values based on patterns in the data.</span></span>  
  
 <span data-ttu-id="8b344-147">**Fill From サンプル**ツールは、Microsoft ロジスティック回帰アルゴリズムを使用します。</span><span class="sxs-lookup"><span data-stu-id="8b344-147">The **Fill From Example** tool uses the Microsoft Logistic Regression algorithm.</span></span>  
  
 [<span data-ttu-id="8b344-148">例 &#40;Excel 用のテーブル分析ツール&#41;</span><span class="sxs-lookup"><span data-stu-id="8b344-148">Fill From Example &#40;Table Analysis Tools for Excel&#41;</span></span>](fill-from-example-table-analysis-tools-for-excel.md)  
  
## <a name="forecast-analyze"></a><span data-ttu-id="8b344-149">予測 (分析)</span><span class="sxs-lookup"><span data-stu-id="8b344-149">Forecast (Analyze)</span></span>  
 <span data-ttu-id="8b344-150">**予測**ツールは、時間の経過と共に変化するデータを取得し、将来の値を予測します。</span><span class="sxs-lookup"><span data-stu-id="8b344-150">The **Forecast** tool takes data that changes over time, and predicts future values.</span></span>  
  
 <span data-ttu-id="8b344-151">**予測**ツールでは、Microsoft タイムシリーズアルゴリズムが使用されます。</span><span class="sxs-lookup"><span data-stu-id="8b344-151">The **Forecast** tool uses the Microsoft Time Series algorithm.</span></span>  
  
 [<span data-ttu-id="8b344-152">Excel 用のテーブル分析ツールの予測 &#40;&#41;</span><span class="sxs-lookup"><span data-stu-id="8b344-152">Forecast &#40;Table Analysis Tools for Excel&#41;</span></span>](forecast-table-analysis-tools-for-excel.md)  
  
## <a name="forecast-data-mining"></a><span data-ttu-id="8b344-153">予測 (データ マイニング)</span><span class="sxs-lookup"><span data-stu-id="8b344-153">Forecast (Data Mining)</span></span>  
 <span data-ttu-id="8b344-154">**予測**ウィザードでは、一連のセルのパターンを検出し、追加の値を予測する予測モデルを作成します。</span><span class="sxs-lookup"><span data-stu-id="8b344-154">The **Forecast** wizard builds a forecasting model that detects patterns in a series of cells, and then forecasts additional values.</span></span>  
  
 [<span data-ttu-id="8b344-155">予測ウィザード &#40;Excel 用データマイニングアドイン&#41;</span><span class="sxs-lookup"><span data-stu-id="8b344-155">Forecast Wizard &#40;Data Mining Add-ins for Excel&#41;</span></span>](forecast-wizard-data-mining-add-ins-for-excel.md)  
  
## <a name="highlight-exceptions-analyze"></a><span data-ttu-id="8b344-156">例外の強調表示 (分析)</span><span class="sxs-lookup"><span data-stu-id="8b344-156">Highlight Exceptions (Analyze)</span></span>  
 <span data-ttu-id="8b344-157">**例外の強調表示**ツールは、データのテーブル内のパターンを分析し、パターンに合わない行と値を見つけます。</span><span class="sxs-lookup"><span data-stu-id="8b344-157">The **Highlight Exceptions** tool analyzes patterns in a table of data and finds rows and values that don't fit the pattern.</span></span> <span data-ttu-id="8b344-158">ユーザーは、これらの値を確認し、修正してモデルを再実行することも、後で処理するためにこれらの値にフラグを設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="8b344-158">You can then review and correct them and rerun the model, or flag values for later action.</span></span>  
  
 <span data-ttu-id="8b344-159">**例外の強調表示**ツールは、Microsoft クラスタリングアルゴリズムを使用します。</span><span class="sxs-lookup"><span data-stu-id="8b344-159">The **Highlight Exceptions** tool uses the Microsoft Clustering algorithm.</span></span>  
  
 [<span data-ttu-id="8b344-160">Excel 用のテーブル分析ツール &#40;例外を強調表示&#41;</span><span class="sxs-lookup"><span data-stu-id="8b344-160">Highlight Exceptions &#40;Table Analysis Tools for Excel&#41;</span></span>](highlight-exceptions-table-analysis-tools-for-excel.md)  
  
## <a name="prediction-calculator-analyze"></a><span data-ttu-id="8b344-161">予測計算ツール (分析)</span><span class="sxs-lookup"><span data-stu-id="8b344-161">Prediction Calculator (Analyze)</span></span>  
 <span data-ttu-id="8b344-162">このツールは、目標の結果の達成につながる要因を分析し、これらのパターンから派生した基準に基づいて新しい入力の結果を予測するモデルを作成します。また、新しい入力を簡単にスコアするために役立つ対話形式の意思決定ワークシートを生成します。</span><span class="sxs-lookup"><span data-stu-id="8b344-162">This tool creates a model that analyzes the factors leading to target outcomes, and then predicts a result for any new input, based on criteria derived from these patterns It also generates an interactive decision making worksheet that lets you easily score new inputs.</span></span> <span data-ttu-id="8b344-163">ユーザーは、オフラインで使用できるスコアリング ワークシートの印刷バージョンを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="8b344-163">You can also create a printed version of the scoring worksheet for offline use.</span></span>  
  
 <span data-ttu-id="8b344-164">**予測計算**ツールでは、Microsoft ロジスティック回帰アルゴリズムが使用されます。</span><span class="sxs-lookup"><span data-stu-id="8b344-164">The **Prediction Calculator** tool uses the Microsoft Logistic Regression algorithm.</span></span>  
  
 [<span data-ttu-id="8b344-165">予測計算 &#40;Excel 用のテーブル分析ツール&#41;</span><span class="sxs-lookup"><span data-stu-id="8b344-165">Prediction Calculator &#40;Table Analysis Tools for Excel&#41;</span></span>](prediction-calculator-table-analysis-tools-for-excel.md)  
  
## <a name="scenario-goal-seek-analyze"></a><span data-ttu-id="8b344-166">シナリオ: ゴール シーク (分析)</span><span class="sxs-lookup"><span data-stu-id="8b344-166">Scenario: Goal Seek (Analyze)</span></span>  
 <span data-ttu-id="8b344-167">**ゴールシーク**ツールでは、ターゲット値を指定します。このツールは、そのターゲットを満たすために変更する必要がある基になる要因を識別します。</span><span class="sxs-lookup"><span data-stu-id="8b344-167">In the **Goal Seek** tool, you specify a target value, and the tool identifies the underlying factors that must change to meet that target.</span></span> <span data-ttu-id="8b344-168">たとえば、電話対応満足度を 20% 向上させる必要がある場合、その目標を達成するために変更する必要のある要因を予測するようモデルに要求できます。</span><span class="sxs-lookup"><span data-stu-id="8b344-168">For example, if you know that you must increase call satisfaction by 20%, you can ask the model to predict the factors that should change to produce that goal.</span></span>  
  
 <span data-ttu-id="8b344-169">**ゴールシーク**ツールは、Microsoft ロジスティック回帰アルゴリズムを使用します。</span><span class="sxs-lookup"><span data-stu-id="8b344-169">The **Goal Seek** tool uses the Microsoft Logistic Regression algorithm.</span></span>  
  
 <span data-ttu-id="8b344-170">details</span><span class="sxs-lookup"><span data-stu-id="8b344-170">details</span></span>  
  
 [<span data-ttu-id="8b344-171">ゴールシークシナリオ &#40;Excel 用のテーブル分析ツール&#41;</span><span class="sxs-lookup"><span data-stu-id="8b344-171">Goal Seek Scenario &#40;Table Analysis Tools for Excel&#41;</span></span>](goal-seek-scenario-table-analysis-tools-for-excel.md)  
  
## <a name="scenario-what-if-scenario-analyze"></a><span data-ttu-id="8b344-172">シナリオ: What-If シナリオ(分析)</span><span class="sxs-lookup"><span data-stu-id="8b344-172">Scenario: What-If Scenario (Analyze)</span></span>  
 <span data-ttu-id="8b344-173">**What-if 分析**ツールは、**ゴールシーク**ツールを補完します。</span><span class="sxs-lookup"><span data-stu-id="8b344-173">The **What-If Analysis** tool complements the **Goal Seek** tool.</span></span> <span data-ttu-id="8b344-174">このツールで変更する必要のある値を入力すると、モデルはその変更が目標の結果を達成するために十分であるかどうかを予測します。</span><span class="sxs-lookup"><span data-stu-id="8b344-174">With this tool, you entered the value you want to change, and the model predicts whether that change will be sufficient to achieve the desired outcome.</span></span> <span data-ttu-id="8b344-175">たとえば、電話オペレーターを 1 人追加することによって顧客満足度が 1 ポイント向上するかどうかを推測するようモデルに要求できます。</span><span class="sxs-lookup"><span data-stu-id="8b344-175">For example, you might ask the model to infer whether adding one extra call operator would increase customer satisfaction by one point.</span></span>  
  
 <span data-ttu-id="8b344-176">**What-if**ツールは、Microsoft ロジスティック回帰アルゴリズムを使用します。</span><span class="sxs-lookup"><span data-stu-id="8b344-176">The **What-If** tool uses the Microsoft Logistic Regression algorithm.</span></span>  
  
 [<span data-ttu-id="8b344-177">What-if シナリオ &#40;Excel 用のテーブル分析ツール&#41;</span><span class="sxs-lookup"><span data-stu-id="8b344-177">What-If Scenario &#40;Table Analysis Tools for Excel&#41;</span></span>](what-if-scenario-table-analysis-tools-for-excel.md)  
  
## <a name="shopping-basket-analysis-analyze"></a><span data-ttu-id="8b344-178">買い物かご分析 (分析)</span><span class="sxs-lookup"><span data-stu-id="8b344-178">Shopping Basket Analysis (Analyze)</span></span>  
 <span data-ttu-id="8b344-179">**買い物かご分析**ツールでは、同時に購入される頻度の高い製品のグループを作成して、クロスセルやアップセルで使用できるパターンを特定します。</span><span class="sxs-lookup"><span data-stu-id="8b344-179">The **Shopping Basket Analysis** tool creates groups of products that are frequently purchased together, to identify patterns that can be used in cross-selling or up-selling.</span></span> <span data-ttu-id="8b344-180">また、意思決定の際に役立つ、関連する製品バンドルの価格とコストに基づくレポートを生成します。</span><span class="sxs-lookup"><span data-stu-id="8b344-180">It also generates reports based on the price and cost of related product bundles, to aid in decision-making.</span></span>  
  
 <span data-ttu-id="8b344-181">このツールは、頻繁に同時発生するイベント、診断につながる要因、またはその他の考えられる原因と結果のセットを特定するために使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="8b344-181">You can also use this tool for events that frequently occur together, factors leading to a diagnosis, or any other set of potential causes and outcomes.</span></span>  
  
 <span data-ttu-id="8b344-182">**買い物かご分析**ツールでは、Microsoft アソシエーションアルゴリズムが使用されます。</span><span class="sxs-lookup"><span data-stu-id="8b344-182">The **Shopping Basket Analysis** tool uses the Microsoft Association algorithm.</span></span>  
  
 [<span data-ttu-id="8b344-183">買い物かご分析 &#40;テーブル AnalysisTools for Excel&#41;</span><span class="sxs-lookup"><span data-stu-id="8b344-183">Shopping Basket Analysis &#40;Table AnalysisTools for Excel&#41;</span></span>](shopping-basket-analysis-table-analysistools-for-excel.md)  
  
## <a name="see-also"></a><span data-ttu-id="8b344-184">参照</span><span class="sxs-lookup"><span data-stu-id="8b344-184">See Also</span></span>  
 <span data-ttu-id="8b344-185">[データの探索とクリーンアップ](exploring-and-cleaning-data.md) </span><span class="sxs-lookup"><span data-stu-id="8b344-185">[Exploring and Cleaning Data](exploring-and-cleaning-data.md) </span></span>  
 <span data-ttu-id="8b344-186">[Excel 用データマイニングアドインのモデルを検証し、モデルを使用して予測 &#40;する&#41;](validating-models-and-using-models-for-prediction-data-mining-add-ins-for-excel.md) </span><span class="sxs-lookup"><span data-stu-id="8b344-186">[Validating Models and Using Models for Prediction &#40;Data Mining Add-ins for Excel&#41;](validating-models-and-using-models-for-prediction-data-mining-add-ins-for-excel.md) </span></span>  
 [<span data-ttu-id="8b344-187">Excel 用データマイニングアドイン &#40;のマイニングモデルの配置とスケーリング&#41;</span><span class="sxs-lookup"><span data-stu-id="8b344-187">Deploying and Scaling Mining Models &#40;Data Mining Add-ins for Excel&#41;</span></span>](deploying-and-scaling-mining-models-data-mining-add-ins-for-excel.md)  
  
  
