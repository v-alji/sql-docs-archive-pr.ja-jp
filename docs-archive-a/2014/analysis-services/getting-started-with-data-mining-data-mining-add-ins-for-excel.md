---
title: データマイニングを使用したはじめに (Excel 用データマイニングアドイン) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: cbe10a19-e194-408e-a65b-5fdf3fb1e880
author: minewiskan
ms.author: owend
ms.openlocfilehash: 066fc72fa0570d56376cc73478a68e42d20ffbc4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633425"
---
# <a name="getting-started-with-data-mining-data-mining-add-ins-for-excel"></a><span data-ttu-id="a9aac-102">データ マイニングの概要 (Excel 用データ マイニング アドイン)</span><span class="sxs-lookup"><span data-stu-id="a9aac-102">Getting Started with Data Mining (Data Mining Add-ins for Excel)</span></span>
  <span data-ttu-id="a9aac-103">データ マイニングとは、"データ内で有意なパターンを見つけるプロセス" を指しています。</span><span class="sxs-lookup"><span data-stu-id="a9aac-103">Data mining is the process of discovering meaningful patterns in data.</span></span> <span data-ttu-id="a9aac-104">データ マイニングは、従来の BI を使用してデータの探索と理解を深めるプロセスに対する、自然な補足手段です。</span><span class="sxs-lookup"><span data-stu-id="a9aac-104">Data mining is a natural complement to the process of exploring and understanding your data through traditional BI.</span></span> <span data-ttu-id="a9aac-105">コンピューター アルゴリズムでは、大量のデータを処理し、その中に隠れたパターンや傾向を見つけ出すことができます。</span><span class="sxs-lookup"><span data-stu-id="a9aac-105">Machine algorithms can process very large amounts of data and discover patterns and trends that would otherwise be hidden.</span></span>  
  
 <span data-ttu-id="a9aac-106">データマイニングを行うには、"だれが顧客か" など、特定の質問に関連するデータを収集します。</span><span class="sxs-lookup"><span data-stu-id="a9aac-106">To do data mining, you collect data that is relevant to a specific question, such as "Who are my customers?"</span></span> <span data-ttu-id="a9aac-107">または、どの製品を購入したか。</span><span class="sxs-lookup"><span data-stu-id="a9aac-107">or "what products were purchased?"</span></span> <span data-ttu-id="a9aac-108">次に、アルゴリズムを適用して、データ内の統計的相関関係を検索します。</span><span class="sxs-lookup"><span data-stu-id="a9aac-108">and then apply an algorithm to find statistical correlations in the data.</span></span> <span data-ttu-id="a9aac-109">分析によって検出されたパターンと傾向は、マイニング モデルとして保存されます。</span><span class="sxs-lookup"><span data-stu-id="a9aac-109">The patterns and trends found through analysis are stored as a mining model.</span></span> <span data-ttu-id="a9aac-110">その後、次のようなビジネス シナリオで、新しいデータに対してマイニング モデルを適用することができます。</span><span class="sxs-lookup"><span data-stu-id="a9aac-110">You can then apply the mining model to new data, in business scenarios such as these:</span></span>  
  
-   <span data-ttu-id="a9aac-111">過去のトレンドを使用して、次の四半期の売上、必要な在庫、または顧客満足度を予測します。</span><span class="sxs-lookup"><span data-stu-id="a9aac-111">Use past trends to forecast sales for the next quarter, inventory requirements, or customer satisfaction.</span></span>  
  
-   <span data-ttu-id="a9aac-112">現在の顧客に関する知識を適用して、新しい顧客をプロファイルし、新しい製品やビジネス チャンスを推奨します。</span><span class="sxs-lookup"><span data-stu-id="a9aac-112">Apply knowledge of current customers to profile new customers and recommend new products or opportunities.</span></span>  
  
-   <span data-ttu-id="a9aac-113">過去の複数のイベントの間に見られる相関関係を探索し、サーバーの障害やダウンタイムを予測します。</span><span class="sxs-lookup"><span data-stu-id="a9aac-113">Find correlations among past events to predict server failures or downtime.</span></span>  
  
-   <span data-ttu-id="a9aac-114">顧客が同時に購入する複数の製品を分析し、その情報を使用して、バンドルを推奨するか、製品陳列の計画を立てます。</span><span class="sxs-lookup"><span data-stu-id="a9aac-114">Analyze which products customers purchase together and use the information to recommend bundles or plan product placement.</span></span>  
  
 <span data-ttu-id="a9aac-115">選択する分析手法は、目標に応じて変化します。</span><span class="sxs-lookup"><span data-stu-id="a9aac-115">The method of analysis you choose depends on your goals.</span></span> <span data-ttu-id="a9aac-116">データ マイニング アドインは、次のような種類の分析をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="a9aac-116">The Data Mining Add-ins support these types of analysis:</span></span>  
  
-   <span data-ttu-id="a9aac-117">教師あり学習と教師なし学習</span><span class="sxs-lookup"><span data-stu-id="a9aac-117">Supervised and unsupervised learning</span></span>  
  
-   <span data-ttu-id="a9aac-118">クラスタリング (セグメント化)</span><span class="sxs-lookup"><span data-stu-id="a9aac-118">Clustering (segmentation)</span></span>  
  
-   <span data-ttu-id="a9aac-119">ベイズ定理とニューラル ネットワークを使用した因子分析</span><span class="sxs-lookup"><span data-stu-id="a9aac-119">Factor analysis, using Bayesian and neural networks</span></span>  
  
-   <span data-ttu-id="a9aac-120">時系列分析</span><span class="sxs-lookup"><span data-stu-id="a9aac-120">Time series analysis</span></span>  
  
-   <span data-ttu-id="a9aac-121">アソシエーション分析、推奨事項、買い物かご分析</span><span class="sxs-lookup"><span data-stu-id="a9aac-121">Association analysis, recommendations, and shopping basket analysis</span></span>  
  
-   <span data-ttu-id="a9aac-122">バイナリ結果のスコアリング</span><span class="sxs-lookup"><span data-stu-id="a9aac-122">Scoring binary outcomes</span></span>  
  
-   <span data-ttu-id="a9aac-123">Linear regression (線形回帰)</span><span class="sxs-lookup"><span data-stu-id="a9aac-123">Linear regression</span></span>  
  
 <span data-ttu-id="a9aac-124">さらにアドインでは、データ準備フェーズ、データの選択、探索、データ クレンジングに関する支援も用意されています。</span><span class="sxs-lookup"><span data-stu-id="a9aac-124">In addition, the add-ins provide help the data preparation phase: data selection, exploration, and data cleansing.</span></span>  
  
## <a name="define-your-goal"></a><span data-ttu-id="a9aac-125">目標を定義する</span><span class="sxs-lookup"><span data-stu-id="a9aac-125">Define Your Goal</span></span>  
 <span data-ttu-id="a9aac-126">始める前に、本当に回答が必要な疑問について少し時間をかけて検討します。</span><span class="sxs-lookup"><span data-stu-id="a9aac-126">Before you get started, take a minute to consider the question you really want to answer.</span></span> <span data-ttu-id="a9aac-127">探索自体は明快ですが、探索の結果を新しいデータに適用しようとする場合は、モデルを使用して何を達成することを予期しているのか、およびモデルが目標を達成したかどうかをどのように測定するかを明確に説明できるようにしておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="a9aac-127">Exploration for its own sake is illuminating, but if you want to apply your findings to new data, you should be able to state clearly what you expect the model to produce, and how you will measure whether the model accomplishes your goals.</span></span>  
  
 <span data-ttu-id="a9aac-128">たとえば、"新しい顧客を検索する" の目標ではなく、"製品を購入する可能性の高い顧客の人口統計を、65% 以上の確率で特定する" など、より具体的な目標を明確にすることを目的としています。</span><span class="sxs-lookup"><span data-stu-id="a9aac-128">For example, rather than a goal of "finding new customers", clarify your objective to something more concrete, such as "identify the demographics of customers that are likely to buy our product, with a probability of at least 65%".</span></span>  
  
-   <span data-ttu-id="a9aac-129">データセットには、トレーニングと予測に使用できる "result" 属性が少なくとも1つ含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="a9aac-129">Your dataset should contain at least one "result" attribute that you can use for training and prediction.</span></span> <span data-ttu-id="a9aac-130">このような属性が存在しない場合は、トレーニング用のいずれかのデータに対して手動でラベルを付けること、または他の列を使用して、結果に対応する代替データを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="a9aac-130">If there is no such attribute, you can manually label some training data, or use other columns to create a proxy for the outcome.</span></span>  
  
     <span data-ttu-id="a9aac-131">たとえば、"最適な見込み客" を予測する場合は、既存の顧客にラベルを付けるために事前にいくつかのビジネスルールを適用し、データマイニングが指定した例から学習できるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a9aac-131">For example, if you want to predict "the best prospects", you should apply some business rule beforehand to label existing customers, so that data mining can learn from the examples you provide.</span></span>  
  
-   <span data-ttu-id="a9aac-132">時間の経過と共に変化する値を扱っていて、将来の動向を予測する場合は、必要とする結果に関する粒度を検討します。</span><span class="sxs-lookup"><span data-stu-id="a9aac-132">If you are working with a value that changes over time, and want to predict future trends, think about the granularity of the results you need.</span></span> <span data-ttu-id="a9aac-133">予測は月、日、または年のどの単位で行いますか?</span><span class="sxs-lookup"><span data-stu-id="a9aac-133">Do you want predictions for a month, day, or yearly basis?</span></span> <span data-ttu-id="a9aac-134">データは、予測と同じ単位を使用して分析する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a9aac-134">Your data has to be analyzed using the same units that you want to predict.</span></span>  
  
     <span data-ttu-id="a9aac-135">周期的なパターンでは、毎日のデータで良好な結果が得られない場合は、別のタイムスライスを試すか、曜日、月、または休日を使用してみてください。</span><span class="sxs-lookup"><span data-stu-id="a9aac-135">With cyclical patterns, if you don't get good results with daily data, try different time slices, or try using week days, months, or even holidays.</span></span>  
  
-   <span data-ttu-id="a9aac-136">ウィザードを起動してデータ内の新しい相関関係を見つけようとする前に、データ全体をよく見渡し、どのような種類の既存のリレーションシップがデータセット内に存在している可能性があるかを検討します。</span><span class="sxs-lookup"><span data-stu-id="a9aac-136">Before you launch a wizard to find new correlations in your data, take one more look at your data and consider what sort of existing relationships might be present in the dataset.</span></span> <span data-ttu-id="a9aac-137">困惑するような変数がありますか? </span><span class="sxs-lookup"><span data-stu-id="a9aac-137">Are there confounding variables?</span></span> <span data-ttu-id="a9aac-138">重複またはプロキシがありますか?</span><span class="sxs-lookup"><span data-stu-id="a9aac-138">Are there duplicates or proxies?</span></span>  
  
-   <span data-ttu-id="a9aac-139">モデルの成功を評価するためのメトリックは何ですか?</span><span class="sxs-lookup"><span data-stu-id="a9aac-139">What are the metrics by which the model's success will be evaluated?</span></span> <span data-ttu-id="a9aac-140">モデルが "良好な" ことをどのように知ることができるでしょうか。</span><span class="sxs-lookup"><span data-stu-id="a9aac-140">How will you know that the model is "good enough"?</span></span>  
  
-   <span data-ttu-id="a9aac-141">データ マイニング モデルから予測しますか、または興味のあるパターンおよび関連付けを検索するだけですか?</span><span class="sxs-lookup"><span data-stu-id="a9aac-141">Do you want to make predictions from the data mining model or just look for interesting patterns and associations?</span></span>  
  
## <a name="explore-your-data-and-explore-the-model"></a><span data-ttu-id="a9aac-142">データの探索とモデルの探索</span><span class="sxs-lookup"><span data-stu-id="a9aac-142">Explore Your Data and Explore the Model</span></span>  
 <span data-ttu-id="a9aac-143">既にデータとドメインについては十分理解していると思いますが、</span><span class="sxs-lookup"><span data-stu-id="a9aac-143">Perhaps you already thoroughly understand the data and the domain.</span></span> <span data-ttu-id="a9aac-144">既に理解している場合でも、モデリングを実施することを想定し、ある程度の時間を費やしてデータをプロファイルする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a9aac-144">Even if you do, you should take some time to profile your data with modeling in mind.</span></span>  
  
 <span data-ttu-id="a9aac-145">ある程度の時間を確保して値の分布を観察し、不足値やプレースホルダーが使用されているなどの問題を識別します。</span><span class="sxs-lookup"><span data-stu-id="a9aac-145">Take a minute to view the distribution of values, and identify potential problems such as missing values or placeholders.</span></span>  
  
 <span data-ttu-id="a9aac-146">他の方法では分析できない大規模または複雑なデータセットに対してデータマイニングを実行する場合は、サンプリングまたはデータの削減を検討してください。</span><span class="sxs-lookup"><span data-stu-id="a9aac-146">If you are planning to perform data mining against a data set that was so large or complex that you couldn't analyze it with other methods, consider sampling or data reduction.</span></span>  
  
-   <span data-ttu-id="a9aac-147">データはどのように分布していますか?</span><span class="sxs-lookup"><span data-stu-id="a9aac-147">How is the data distributed?</span></span>  
  
-   <span data-ttu-id="a9aac-148">列はどのように関連していますか、または複数のテーブルがある場合、テーブルはどのように関連していますか?</span><span class="sxs-lookup"><span data-stu-id="a9aac-148">How are the columns related, or if there are multiple tables, how are the tables related?</span></span>  
  
-   <span data-ttu-id="a9aac-149">不足値がありますか? </span><span class="sxs-lookup"><span data-stu-id="a9aac-149">Are any values missing?</span></span> <span data-ttu-id="a9aac-150">変換や前処理が必要な値がありますか?</span><span class="sxs-lookup"><span data-stu-id="a9aac-150">Are there values that need conversion or preprocessing?</span></span>  
  
-   <span data-ttu-id="a9aac-151">データは主にテキストですか、数値ですか、またはその組み合わせですか?</span><span class="sxs-lookup"><span data-stu-id="a9aac-151">Is the data mostly text, mostly numbers, or a mix?</span></span>  
  
-   <span data-ttu-id="a9aac-152">対象となる結果の分析をサポートするのに十分なデータはありますか? </span><span class="sxs-lookup"><span data-stu-id="a9aac-152">Do you have enough data to support analysis of the targeted outcomes?</span></span> <span data-ttu-id="a9aac-153">製品間の関連付けを分析する場合は、もっと多くのデータが必要になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a9aac-153">If you are analyzing associations among products, you might need lots more data.</span></span> <span data-ttu-id="a9aac-154">バイナリ結果を予測している場合は、データセットのバランスが取れていることを前提に、より少ないデータで対応できます。</span><span class="sxs-lookup"><span data-stu-id="a9aac-154">If you are predicting a binary outcome, you can get by with much less, assuming the dataset is balanced.</span></span>  
  
 <span data-ttu-id="a9aac-155">モデルが完成した後、ある程度の時間を費やして結果を検討し、より良い結果を得るためにデータに変更を加えるいくつかの方法を識別します。</span><span class="sxs-lookup"><span data-stu-id="a9aac-155">After your model is complete, take some time to review the results and identify ways to amend the data or get better results.</span></span> <span data-ttu-id="a9aac-156">最初のモデルであらゆる答えが得られることはめったにありません。</span><span class="sxs-lookup"><span data-stu-id="a9aac-156">It is exceedingly rare that your first model provides all the answers.</span></span> <span data-ttu-id="a9aac-157">一般に、データ マイニングは反復的なプロセスです。</span><span class="sxs-lookup"><span data-stu-id="a9aac-157">Data mining is typically an iterative process.</span></span>  
  
 <span data-ttu-id="a9aac-158">データをさまざまな方法で分割したり、新しい列を追加したりする場合は、**モデルのドキュメント**化ウィザードを使用して、各モデルのメタデータと結果のスナップショットをキャプチャすることを忘れないでください。</span><span class="sxs-lookup"><span data-stu-id="a9aac-158">As you try binning your data different ways, or adding new columns, remember to use the **Document Model** wizard to capture a snapshot of each model's metadata and results.</span></span> <span data-ttu-id="a9aac-159">記録を作成しておくと、探索の進行状況を追跡しやすくなります。</span><span class="sxs-lookup"><span data-stu-id="a9aac-159">Having a record will make it easier to track progress in your exploration.</span></span>  
  
 [<span data-ttu-id="a9aac-160">データの探索とクリーニング</span><span class="sxs-lookup"><span data-stu-id="a9aac-160">Exploring and Cleaning Data</span></span>](exploring-and-cleaning-data.md)  
  
## <a name="validate-your-model"></a><span data-ttu-id="a9aac-161">モデルの検証</span><span class="sxs-lookup"><span data-stu-id="a9aac-161">Validate Your Model</span></span>  
 <span data-ttu-id="a9aac-162">各ウィザードまたはツールを実行すると、アルゴリズムによってデータの内容が分析され、統計的に有効なパターンが存在するかどうかが示されます。</span><span class="sxs-lookup"><span data-stu-id="a9aac-162">As you run each wizard or tool, the algorithm analyzes the contents of the data and determines whether a statistically valid pattern exists.</span></span> <span data-ttu-id="a9aac-163">アルゴリズムで有効なパターンが見つからない場合は、エラーメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a9aac-163">If the algorithm cannot find valid patterns, you'll get an error message.</span></span> <span data-ttu-id="a9aac-164">ただし、モデルが正常に作成された場合でも、モデルをテストして、想定が検証されるかどうかを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a9aac-164">However, even if a model was successfully created, you'll want to test the model to see if it validates your assumptions.</span></span> <span data-ttu-id="a9aac-165">精度チャートなどのツールを使用して、[データマイニングアドイン&#41;](accuracy-chart-sql-server-data-mining-add-ins.md)または[クロス検証 &#40;SQL Server データマイニングアドイン&#41;](cross-validation-sql-server-data-mining-add-ins.md)を使用して、モデルの品質の統計的尺度を生成することができ SQL Server &#40;ます。</span><span class="sxs-lookup"><span data-stu-id="a9aac-165">You can use tools such as the [Accuracy Chart &#40;SQL Server Data Mining Add-ins&#41;](accuracy-chart-sql-server-data-mining-add-ins.md) or [Cross-Validation &#40;SQL Server Data Mining Add-ins&#41;](cross-validation-sql-server-data-mining-add-ins.md) to produce statistical measures of model quality.</span></span>  
  
 <span data-ttu-id="a9aac-166">最初のモデルから得られた結果を評価する際に、次の点を自問してください。</span><span class="sxs-lookup"><span data-stu-id="a9aac-166">As you assess the results of your first model, ask yourself questions such as these:</span></span>  
  
-   <span data-ttu-id="a9aac-167">どのようなパターンが検出されましたか?</span><span class="sxs-lookup"><span data-stu-id="a9aac-167">What kinds of patterns were found?</span></span> <span data-ttu-id="a9aac-168">どのような確率が得られ、それらは何を裏付けていますか?</span><span class="sxs-lookup"><span data-stu-id="a9aac-168">What are the probabilities and support values?</span></span>  
  
-   <span data-ttu-id="a9aac-169">傾向に関する予想は正しかったですか、または予想外の相関関係がありましたか?</span><span class="sxs-lookup"><span data-stu-id="a9aac-169">Were our guesses about trends correct, or were there surprising correlations?</span></span>  
  
-   <span data-ttu-id="a9aac-170">十分なデータを収集しましたか?</span><span class="sxs-lookup"><span data-stu-id="a9aac-170">Did we collect enough data?</span></span> <span data-ttu-id="a9aac-171">データをビン分割すると、より明確なパターンが生成されますか?</span><span class="sxs-lookup"><span data-stu-id="a9aac-171">Would binning the data produce clearer patterns?</span></span>  
  
-   <span data-ttu-id="a9aac-172">データセットは均衡のとれたものですか?</span><span class="sxs-lookup"><span data-stu-id="a9aac-172">Is the data set balanced?</span></span> <span data-ttu-id="a9aac-173">クロス検証を実施すると、データの代表性をテストできます。</span><span class="sxs-lookup"><span data-stu-id="a9aac-173">Cross-validation can test the representativeness of your data.</span></span>  
  
 [<span data-ttu-id="a9aac-174">Excel 用テーブル分析ツール</span><span class="sxs-lookup"><span data-stu-id="a9aac-174">Table Analysis Tools for Excel</span></span>](table-analysis-tools-for-excel.md)  
  
 [<span data-ttu-id="a9aac-175">Excel 用のデータマイニングクライアント &#40;SQL Server データマイニングアドイン&#41;</span><span class="sxs-lookup"><span data-stu-id="a9aac-175">Data Mining Client for Excel &#40;SQL Server Data Mining Add-ins&#41;</span></span>](data-mining-client-for-excel-sql-server-data-mining-add-ins.md)  
  
 [<span data-ttu-id="a9aac-176">モデルの選択</span><span class="sxs-lookup"><span data-stu-id="a9aac-176">Choosing a Model</span></span>](choosing-a-model.md)  
  
## <a name="explore-and-refine"></a><span data-ttu-id="a9aac-177">探索と修正</span><span class="sxs-lookup"><span data-stu-id="a9aac-177">Explore and Refine</span></span>  
 <span data-ttu-id="a9aac-178">モデルが有効と考えられる場合は、そのモデルを使用して予測や提案、洞察の派生、またはビジネス戦略の立案を実行できます。</span><span class="sxs-lookup"><span data-stu-id="a9aac-178">If the model appears to be valid, you can use the model for prediction, recommendation, deriving insights, or planning business strategies..</span></span>  
  
-   <span data-ttu-id="a9aac-179">Excel 用のデータ マイニング クライアントに付属するデータ マイニング ブラウザーを使用して、モデルの探索と操作を行います。</span><span class="sxs-lookup"><span data-stu-id="a9aac-179">Use the data mining browser in the Data Mining Client for Excel to explore and interact with the model.</span></span>  
  
-   <span data-ttu-id="a9aac-180">Excel を使用して、結果の並べ替えやフィルター処理を実行します。</span><span class="sxs-lookup"><span data-stu-id="a9aac-180">Use Excel to rearrange and filter the results.</span></span>  
  
-   <span data-ttu-id="a9aac-181">Visio を使用して、プレゼンテーションを作成し、データ内で見つかったリレーションシップを強調表示します。</span><span class="sxs-lookup"><span data-stu-id="a9aac-181">Use Visio to create presentations and highlight the relationships found in the data.</span></span>  
  
 <span data-ttu-id="a9aac-182">多くの場合、最初の分析結果では、分析を改善するための方法が見つかったり、新しいデータやより良いデータを取得する必要があることを認識したりできます。</span><span class="sxs-lookup"><span data-stu-id="a9aac-182">Often, the first result of analysis is that you see ways to improve the analysis, or realize that you need to get new and better data.</span></span> <span data-ttu-id="a9aac-183">Excel 用データ マイニング アドインを使用して作成したモデルは Analysis Service のインスタンスに保存できるため、比較的簡単に新しいデータを使用してモデルを更新し、引き続き、成功したモデルを修正して再利用することができます。</span><span class="sxs-lookup"><span data-stu-id="a9aac-183">Because the models that you create using the Data Mining Add-ins for Excel can be saved to an instance of Analysis Service, it is relatively easy to update the model with new data, and continue to refine and re-use successful models.</span></span>  
  
 <span data-ttu-id="a9aac-184">データ マイニング モデルの重要な用途は、予測や提案を作成することです。</span><span class="sxs-lookup"><span data-stu-id="a9aac-184">An important use of data mining models is to create predictions and recommendations.</span></span> <span data-ttu-id="a9aac-185">Excel 用データ マイニング アドインには、洞察を実用的な結果に変換するために、複雑な予測クエリでも簡単に生成できるツールが含まれています。</span><span class="sxs-lookup"><span data-stu-id="a9aac-185">The Data Mining Add-ins for Excel includes tools that make it easy to generate even complex prediction queries, for converting insights into actionable results.</span></span> <span data-ttu-id="a9aac-186">これらのツールはすべて Excel に完全に統合されています。</span><span class="sxs-lookup"><span data-stu-id="a9aac-186">All of these tools are fully integrated with Excel.</span></span>  
  
 [<span data-ttu-id="a9aac-187">Office 用データマイニングアドイン &#40;モデルの表示&#41;</span><span class="sxs-lookup"><span data-stu-id="a9aac-187">Viewing Models &#40;Data Mining Add-ins for Office&#41;</span></span>](viewing-models-data-mining-add-ins-for-office.md)  
  
 [<span data-ttu-id="a9aac-188">Excel 用データマイニングアドインのモデルを検証し、モデルを使用して予測 &#40;する&#41;</span><span class="sxs-lookup"><span data-stu-id="a9aac-188">Validating Models and Using Models for Prediction &#40;Data Mining Add-ins for Excel&#41;</span></span>](validating-models-and-using-models-for-prediction-data-mining-add-ins-for-excel.md)  
  
## <a name="see-also"></a><span data-ttu-id="a9aac-189">参照</span><span class="sxs-lookup"><span data-stu-id="a9aac-189">See Also</span></span>  
 <span data-ttu-id="a9aac-190">[Office 用データマイニングアドインに含まれる内容](what-s-included-in-the-data-mining-add-ins-for-office.md) </span><span class="sxs-lookup"><span data-stu-id="a9aac-190">[What's Included in the Data Mining Add-Ins for Office](what-s-included-in-the-data-mining-add-ins-for-office.md) </span></span>  
 [<span data-ttu-id="a9aac-191">Excel 用データマイニングアドイン &#40;テクニカルリファレンス&#41;</span><span class="sxs-lookup"><span data-stu-id="a9aac-191">Technical Reference &#40;Data Mining Add-ins for Excel&#41;</span></span>](technical-reference-data-mining-add-ins-for-excel.md)  
  
  
