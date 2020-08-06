---
title: データマイニングの準備のチェックリスト |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 0e056c95-ba06-413e-8dc1-4d411a447c3b
author: minewiskan
ms.author: owend
ms.openlocfilehash: e37b1adb6aebe5d5f8fd23f5289f52425f752a6e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634163"
---
# <a name="checklist-of-preparation-for-data-mining"></a><span data-ttu-id="f0ebf-102">データ マイニングの準備のチェック リスト</span><span class="sxs-lookup"><span data-stu-id="f0ebf-102">Checklist of Preparation for Data Mining</span></span>
  <span data-ttu-id="f0ebf-103">データ マイニング アドインを使うと、モデルの作成およびテストをかなり容易に楽しく行うことができますが、反復可能で実用的な結果を得る必要がある場合は、十分な時間をかけて基本的なビジネス要件を明確にし、データの取得と準備を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f0ebf-103">Although the Data Mining Add-ins make it fairly easy and fun to create and experiment with models, when you need to get repeatable, actionable results, you must allow adequate time for formulating basic business requirements, and for obtaining and preparing data.</span></span> <span data-ttu-id="f0ebf-104">ここでは、調査を計画するために役立つチェックリストを提供し、一般的な問題について説明します。</span><span class="sxs-lookup"><span data-stu-id="f0ebf-104">This section provides a checklist to help you plan your investigation, and describes common problems.</span></span>  
  
## <a name="checklist-of-data-preparation"></a><span data-ttu-id="f0ebf-105">データ準備のチェック リスト</span><span class="sxs-lookup"><span data-stu-id="f0ebf-105">Checklist of Data Preparation</span></span>  
 <span data-ttu-id="f0ebf-106">**明確に定義された出力を特定しました。**</span><span class="sxs-lookup"><span data-stu-id="f0ebf-106">**I have identified a clearly defined output.**</span></span>  
 <span data-ttu-id="f0ebf-107">結果の使用方法の計画を立てます。</span><span class="sxs-lookup"><span data-stu-id="f0ebf-107">Have a plan for how you will use the results.</span></span> <span data-ttu-id="f0ebf-108">モデルの種類が異なれば、出力も異なります。</span><span class="sxs-lookup"><span data-stu-id="f0ebf-108">Different types of models have different outputs.</span></span> <span data-ttu-id="f0ebf-109">タイム シリーズ モデルは、簡単に理解し、実施することができる将来のシリーズの値を生成します。</span><span class="sxs-lookup"><span data-stu-id="f0ebf-109">A time series model generates values for a series in the future, which are easily understood and acted on.</span></span> <span data-ttu-id="f0ebf-110">他のモデルは、最大限の価値を引き出すために、その分野の専門家によって分析される必要のある複雑なセットを生成します。</span><span class="sxs-lookup"><span data-stu-id="f0ebf-110">Other models generate complex sets that must be analyzed by subject matter experts to yield the most value.</span></span>  
  
-   <span data-ttu-id="f0ebf-111">どのような出力が必要であるか。</span><span class="sxs-lookup"><span data-stu-id="f0ebf-111">What output do you want?</span></span>  
  
-   <span data-ttu-id="f0ebf-112">出力を 1 つの列または値として、あるいは他の実用的な結果として定義できるか。</span><span class="sxs-lookup"><span data-stu-id="f0ebf-112">Can you define the output as a single column or value, or other actionable result?</span></span>  
  
-   <span data-ttu-id="f0ebf-113">モデルが役に立つかどうかを判断する基準は何か。</span><span class="sxs-lookup"><span data-stu-id="f0ebf-113">What are your criteria for knowing that the model was useful?</span></span>  
  
-   <span data-ttu-id="f0ebf-114">これらの結果をどのように使用し、解釈するか。</span><span class="sxs-lookup"><span data-stu-id="f0ebf-114">How will you use and interpret those results?</span></span>  
  
-   <span data-ttu-id="f0ebf-115">期待される結果に新しい入力データをマップできるか。</span><span class="sxs-lookup"><span data-stu-id="f0ebf-115">Can you map new input data to the expected results?</span></span>  
  
 <span data-ttu-id="f0ebf-116">**入力データの意味、データ型、分布がわかっています。**</span><span class="sxs-lookup"><span data-stu-id="f0ebf-116">**I know the meaning, data types, and distribution of the input data.**</span></span>  
 <span data-ttu-id="f0ebf-117">ある程度の時間をかけてソース データについて調べ、理解しておきます。</span><span class="sxs-lookup"><span data-stu-id="f0ebf-117">Take some time to explore and understand your source data.</span></span> <span data-ttu-id="f0ebf-118">モデルを調べる人が、どのような種類の入力データが使用されたかを把握していること、そして、データ型と可変性、バランスと品質の解釈方法を知っていることが重要です。</span><span class="sxs-lookup"><span data-stu-id="f0ebf-118">It is important that people who review the model understand what kind of input data was used and know how to interpret the data types and the variability, as well as the balance and the quality.</span></span>  
  
-   <span data-ttu-id="f0ebf-119">どれほどの量のデータがあるか。</span><span class="sxs-lookup"><span data-stu-id="f0ebf-119">How much data do you have?</span></span> <span data-ttu-id="f0ebf-120">モデリングを行うために十分なデータがあるか </span><span class="sxs-lookup"><span data-stu-id="f0ebf-120">Is there sufficient data for modeling?</span></span>  
  
     <span data-ttu-id="f0ebf-121">サイズが小さく、バランスが取れている必要があります。</span><span class="sxs-lookup"><span data-stu-id="f0ebf-121">It need not be a huge amount - smaller and balanced can be better.</span></span>  
  
-   <span data-ttu-id="f0ebf-122">データのソースは複数あるか 1 つだけであるか。</span><span class="sxs-lookup"><span data-stu-id="f0ebf-122">Is the data from multiple sources, or a single source?</span></span>  
  
-   <span data-ttu-id="f0ebf-123">データは既に処理されていてクリーンであるか。</span><span class="sxs-lookup"><span data-stu-id="f0ebf-123">Is the data already processed and clean?</span></span> <span data-ttu-id="f0ebf-124">使用できる入力データがもっとあるか。</span><span class="sxs-lookup"><span data-stu-id="f0ebf-124">Is more input data available?</span></span>  
  
-   <span data-ttu-id="f0ebf-125">データがどのように切り捨てられたか、集計されたか、または変換されたかを確認してください。</span><span class="sxs-lookup"><span data-stu-id="f0ebf-125">Do you know how it was manipulated before you received it - how data might have been truncated, summarized, or converted?</span></span>  
  
-   <span data-ttu-id="f0ebf-126">トレーニングに使用できる結果の例が入力データに付随しているか。</span><span class="sxs-lookup"><span data-stu-id="f0ebf-126">Does the input data have some example results that can be used for training?</span></span>  
  
 <span data-ttu-id="f0ebf-127">**データ整合性の現在のレベルと必要なレベルを理解しています。**</span><span class="sxs-lookup"><span data-stu-id="f0ebf-127">**I understand the level of data integrity we have and the level we need.**</span></span>  
 <span data-ttu-id="f0ebf-128">データが不適切であると、モデルの品質が低くなる可能性があり、モデルを構築できない場合もあります。</span><span class="sxs-lookup"><span data-stu-id="f0ebf-128">Bad data can affect the quality of the model, or prevent the model from being built at all.</span></span> <span data-ttu-id="f0ebf-129">データの分布と意味、そして、この状態になった経緯の両方をよく理解している必要があります。</span><span class="sxs-lookup"><span data-stu-id="f0ebf-129">You should have a good understanding of both the distribution and meaning of the data, and how it came to this state.</span></span> <span data-ttu-id="f0ebf-130">ラベル付け、数値データ型の切り捨て、または集計によってデータを簡略化することが可能か、または適切かを理解する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f0ebf-130">You'll need to understand if it is possible or appropriate to simplify the data by labeling, truncating numeric data types, or by summarizing.</span></span>  
  
-   <span data-ttu-id="f0ebf-131">データ ラベル: 明確で正しいか。</span><span class="sxs-lookup"><span data-stu-id="f0ebf-131">Data labels: are they clear and correct?</span></span>  
  
-   <span data-ttu-id="f0ebf-132">データ型: 適切か、変更されているか。</span><span class="sxs-lookup"><span data-stu-id="f0ebf-132">Data types: are they appropriate, and have they been changed?</span></span>  
  
-   <span data-ttu-id="f0ebf-133">不適切なデータを選別したか、クリーンアップしたか、または破棄したか。</span><span class="sxs-lookup"><span data-stu-id="f0ebf-133">Have you sorted, cleaned up, or discarded wrong data?</span></span>  
  
     <span data-ttu-id="f0ebf-134">重複がないことを確認したか。</span><span class="sxs-lookup"><span data-stu-id="f0ebf-134">Have you verified there are no duplicates?</span></span>  
  
-   <span data-ttu-id="f0ebf-135">不足値をどのように処理するか。</span><span class="sxs-lookup"><span data-stu-id="f0ebf-135">How will you handle missing values?</span></span> <span data-ttu-id="f0ebf-136">不足値に意味があるか。</span><span class="sxs-lookup"><span data-stu-id="f0ebf-136">Do missing values have a meaning?</span></span>  
  
-   <span data-ttu-id="f0ebf-137">ソースを検証して、インポート処理でエラーが発生した可能性があるかどうかを確認したか。</span><span class="sxs-lookup"><span data-stu-id="f0ebf-137">Have you verified the sources to see if any errors might have been introduced in the import process?</span></span>  
  
     <span data-ttu-id="f0ebf-138">入力はどこに保存されているか。</span><span class="sxs-lookup"><span data-stu-id="f0ebf-138">Where is the input stored?</span></span> <span data-ttu-id="f0ebf-139">入力はどの程度の期間、使用できるか。</span><span class="sxs-lookup"><span data-stu-id="f0ebf-139">How long does it stay available?</span></span>  
  
     <span data-ttu-id="f0ebf-140">データ辞書はあるか。</span><span class="sxs-lookup"><span data-stu-id="f0ebf-140">Is there a data dictionary?</span></span> <span data-ttu-id="f0ebf-141">1 つ作成できるか。</span><span class="sxs-lookup"><span data-stu-id="f0ebf-141">Can you create one?</span></span>  
  
-   <span data-ttu-id="f0ebf-142">データセットを結合した場合、同じデータを表す列が複数あるかどうかを確認したか。</span><span class="sxs-lookup"><span data-stu-id="f0ebf-142">If you combined data sets, did you check for multiple columns representing the same data?</span></span>  
  
 <span data-ttu-id="f0ebf-143">**ソースデータがどこに格納されているか、どこから来たか、およびその処理方法がわかっています。プロセスは、必要に応じて簡単に繰り返すことができます。**</span><span class="sxs-lookup"><span data-stu-id="f0ebf-143">**I know where source data is stored, where it came from, and how it is processed. The process can be easily repeated if needed.**</span></span>  
 <span data-ttu-id="f0ebf-144">1回限りのデータセットは実験には適していますが、モデルを運用環境に移行する場合は、クリーニングプロセスを運用データにどのように適用できるかを事前に検討する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f0ebf-144">One-off data sets are fine for experiments, but if you ever want to move the model into production, you'll want to think in advance about how the cleaning process can be applied to operational data.</span></span> <span data-ttu-id="f0ebf-145">また、オペレーションデータがある場合は、それがどのように変更されているかを把握しておく必要があります。これは、それがどのように丸められたか、または要約されているかを知る必要があります。</span><span class="sxs-lookup"><span data-stu-id="f0ebf-145">Also, if you have operational data, you need to know how it might have been altered before you got it-you'll need to know how it was rounded, or summarized, certainly.</span></span>  
  
-   <span data-ttu-id="f0ebf-146">テストは反復可能である必要があるか。</span><span class="sxs-lookup"><span data-stu-id="f0ebf-146">Do you want to be able to repeat the experiment?</span></span>  
  
-   <span data-ttu-id="f0ebf-147">データ分析をサポートする形式でデータを準備するときに、どのツールを使用するか。</span><span class="sxs-lookup"><span data-stu-id="f0ebf-147">What tools will you use to prepare data in a format that supports data analysis?</span></span> <span data-ttu-id="f0ebf-148">それは自動化できるか、それとも、Excel で見直してクリーンアップする必要があるか。</span><span class="sxs-lookup"><span data-stu-id="f0ebf-148">Can it be automated or do you need someone to review and clean up in Excel?</span></span>  
  
-   <span data-ttu-id="f0ebf-149">データのソースとして別のシステムを使用する場合、適用されたフィルターをキャプチャし、追跡できるか。</span><span class="sxs-lookup"><span data-stu-id="f0ebf-149">If you are sourcing data from another system, will you be able to capture and track filters that were applied?</span></span>  
  
-   <span data-ttu-id="f0ebf-150">データ処理フレームワークは、機械学習アルゴリズムを適用し、テストを実行し、結果を表示することができるか。</span><span class="sxs-lookup"><span data-stu-id="f0ebf-150">Can your data processing framework also apply machine learning algorithms, perform tests, and visualize results?</span></span>  
  
 <span data-ttu-id="f0ebf-151">**予測の望ましいきめ細かさについて合意し、そのような単位で出力できるようにデータが修正されています。**</span><span class="sxs-lookup"><span data-stu-id="f0ebf-151">**We have agreed on the desired granularity of predictions and our data has been modified to output those units.**</span></span>  
 <span data-ttu-id="f0ebf-152">データを準備する前に結果のきめ細かさを決定します。たとえば、必要な売上予測は 1 日ごとか、四半期ごとかを決めます。</span><span class="sxs-lookup"><span data-stu-id="f0ebf-152">Decide on the granularity of the results you want before preparing data, For example, do you want sales predictions by the day, or for each quarter?</span></span> <span data-ttu-id="f0ebf-153">さまざまなレベルの集約を処理できるよう、同じデータについて複数の異なるデータ構造を設定することも検討します。</span><span class="sxs-lookup"><span data-stu-id="f0ebf-153">You might consider setting up different data structures for the same data, to handle different levels of summary.</span></span>  
  
-   <span data-ttu-id="f0ebf-154">現在の測定の単位または時間の単位は何か。</span><span class="sxs-lookup"><span data-stu-id="f0ebf-154">What is the current unit of measure or unit of time?</span></span>  
  
     <span data-ttu-id="f0ebf-155">どの単位を結果で使用するか。</span><span class="sxs-lookup"><span data-stu-id="f0ebf-155">What unit do you want to use in the results?</span></span>  
  
-   <span data-ttu-id="f0ebf-156">すべての入力データに対して基本単位 (例: 日/時間/分/命令呼び出し) を定義することはできますか。</span><span class="sxs-lookup"><span data-stu-id="f0ebf-156">Is it possible to define a basic unit (e.g. day/ hour / min / instruction call) for all input data?</span></span>  
  
     <span data-ttu-id="f0ebf-157">より上位の単位にロールアップする必要があるか。</span><span class="sxs-lookup"><span data-stu-id="f0ebf-157">Do you want to rollup to higher units?</span></span>  
  
-   <span data-ttu-id="f0ebf-158">カテゴリのラベル付けに一貫性があるか。</span><span class="sxs-lookup"><span data-stu-id="f0ebf-158">Are categories labeled consistently?</span></span> <span data-ttu-id="f0ebf-159">カテゴリを簡単に追加または削除できるか。</span><span class="sxs-lookup"><span data-stu-id="f0ebf-159">Is it easy to add or remove categories?</span></span>  
  
 <span data-ttu-id="f0ebf-160">**テスト設計が反復可能で再現可能です。**</span><span class="sxs-lookup"><span data-stu-id="f0ebf-160">**Our experimental design is repeatable and reproducible.**</span></span>  
 <span data-ttu-id="f0ebf-161">データへの影響を遡って調べることができるよう、結果を分析および検証する戦略と、データ スナップショットをキャプチャする計画を策定します。</span><span class="sxs-lookup"><span data-stu-id="f0ebf-161">Consider strategies for analyzing and validating your results and plan to capture a data snapshot, to make sure you can trace back effects to data.</span></span> <span data-ttu-id="f0ebf-162">ランダム シードを使用した場合、結果は微妙に異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="f0ebf-162">If a random seed is used, the results can differ subtly.</span></span> <span data-ttu-id="f0ebf-163">これにより、モデルを比較して検証することが難しくなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f0ebf-163">This can make it difficult to compare and validate models.</span></span>  
  
-   <span data-ttu-id="f0ebf-164">データに対して多くのカスタム変更を加えた場合、次回モデルを構築する必要があるときにどうなるか。</span><span class="sxs-lookup"><span data-stu-id="f0ebf-164">If you make a lot of custom changes to the data, what happens the next time you want to build the model?</span></span>  
  
-   <span data-ttu-id="f0ebf-165">入力を処理し、必要な出力を取得するために使用する必要のある手動プロシージャまたは承認済みプロセスが既に定義されているか。</span><span class="sxs-lookup"><span data-stu-id="f0ebf-165">Has a manual procedure or approved process already been defined that you should use to process input and get the desired outputs?</span></span>  
  
-   <span data-ttu-id="f0ebf-166">モデルのシードを使用することにしたか。</span><span class="sxs-lookup"><span data-stu-id="f0ebf-166">Have you decided to use a seed for the model?</span></span>  
  
 <span data-ttu-id="f0ebf-167">**自分たちにドメインのナレッジがあり結果を検証できるか、または、その分野の専門家に問い合わせて助言を得ることができます。**</span><span class="sxs-lookup"><span data-stu-id="f0ebf-167">**We have the domain knowledge to validate the results, or have access to subject matter experts who can advise.**</span></span>  
 <span data-ttu-id="f0ebf-168">時間をかけて変数、モデル、および結果を検証します。</span><span class="sxs-lookup"><span data-stu-id="f0ebf-168">Take time to validate the variables, the model, and the results.</span></span> <span data-ttu-id="f0ebf-169">専門家の補助のもとで対話と結果を評価します。</span><span class="sxs-lookup"><span data-stu-id="f0ebf-169">Get the help of experts to assess interactions and results.</span></span> <span data-ttu-id="f0ebf-170">ただし、前提によって証拠が誤って解釈されることはありません。</span><span class="sxs-lookup"><span data-stu-id="f0ebf-170">However, don't let assumptions overrule evidence.</span></span> <span data-ttu-id="f0ebf-171">新しい結果、予期しなかった結果も受け入れるようにします。</span><span class="sxs-lookup"><span data-stu-id="f0ebf-171">Be open to new and unexpected findings.</span></span>  
  
-   <span data-ttu-id="f0ebf-172">ドメインのナレッジをデータのフィルター処理と入力のノイズの削減に役立てるために使用できるか。</span><span class="sxs-lookup"><span data-stu-id="f0ebf-172">Is domain knowledge available to help in filtering data and reducing input noise?</span></span>  
  
-   <span data-ttu-id="f0ebf-173">ドメインの専門家は結果の解釈と理解を促し、改善点を提案することができるか。</span><span class="sxs-lookup"><span data-stu-id="f0ebf-173">Can domain experts help understand interpret the results and suggest improvements?</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0ebf-174">参照</span><span class="sxs-lookup"><span data-stu-id="f0ebf-174">See Also</span></span>  
 [<span data-ttu-id="f0ebf-175">データ マイニングで使用するデータの選択</span><span class="sxs-lookup"><span data-stu-id="f0ebf-175">Choosing Data for Data Mining</span></span>](choosing-data-for-data-mining.md)  
  
  
