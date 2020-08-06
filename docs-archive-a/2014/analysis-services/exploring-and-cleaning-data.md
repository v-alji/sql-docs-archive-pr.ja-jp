---
title: データの探索とクリーニング |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 7c888c95-8986-461e-9f11-2395044b9d97
author: minewiskan
ms.author: owend
ms.openlocfilehash: 154c711f735bcbb472e49654139fd16a036a0dd5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631321"
---
# <a name="exploring-and-cleaning-data"></a><span data-ttu-id="68d0e-102">データの探索とクリーニング</span><span class="sxs-lookup"><span data-stu-id="68d0e-102">Exploring and Cleaning Data</span></span>
  <span data-ttu-id="68d0e-103">データの準備は、データのクレンジングよりはるかに大きな概念です。</span><span class="sxs-lookup"><span data-stu-id="68d0e-103">Data preparation is much more than data cleansing.</span></span> <span data-ttu-id="68d0e-104">データの準備方法によって、最終的な結果の解釈も影響を受けることを忘れないでください。</span><span class="sxs-lookup"><span data-stu-id="68d0e-104">Remember that how data is prepared also affects how results are interpreted in the end.</span></span> <span data-ttu-id="68d0e-105">データの準備には、次のようなタスクがあります。</span><span class="sxs-lookup"><span data-stu-id="68d0e-105">Data preparation involves these tasks:</span></span>  
  
-   <span data-ttu-id="68d0e-106">データの分布を探索し確認します。</span><span class="sxs-lookup"><span data-stu-id="68d0e-106">Exploring and checking the distribution of data.</span></span>  
  
-   <span data-ttu-id="68d0e-107">不良レコードをクリーニングして、データ マイニング用の列を選択します。</span><span class="sxs-lookup"><span data-stu-id="68d0e-107">Cleaning bad records, and choosing columns for data mining.</span></span>  
  
-   <span data-ttu-id="68d0e-108">null 値を適切に処理します。</span><span class="sxs-lookup"><span data-stu-id="68d0e-108">Handling nulls appropriately.</span></span>  
  
-   <span data-ttu-id="68d0e-109">異なる期間によって、値のビン分割または値の集計を実行します。</span><span class="sxs-lookup"><span data-stu-id="68d0e-109">Binning values, or aggregating values by different chunks of time.</span></span>  
  
-   <span data-ttu-id="68d0e-110">ラベルを追加して、結果を使いやすくします。</span><span class="sxs-lookup"><span data-stu-id="68d0e-110">Adding labels to improve the usability of the results.</span></span>  
  
-   <span data-ttu-id="68d0e-111">分析の必要に応じて、データ型の変換または値のカテゴリ分類を実行します。</span><span class="sxs-lookup"><span data-stu-id="68d0e-111">Converting data types or categorizing values where necessary for analysis.</span></span>  
  
 <span data-ttu-id="68d0e-112">データ モデリングについて詳しくない場合は、関連トピック「[データ マイニングの準備のチェック リスト](checklist-of-preparation-for-data-mining.md)」を参照することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="68d0e-112">If you are new to data modeling, we recommend that you read the related topic, [Checklist of Preparation for Data Mining](checklist-of-preparation-for-data-mining.md).</span></span>  
  
## <a name="data-preparation-tools"></a><span data-ttu-id="68d0e-113">データ準備ツール</span><span class="sxs-lookup"><span data-stu-id="68d0e-113">Data Preparation Tools</span></span>  
 <span data-ttu-id="68d0e-114">Office 用データ マイニング アドインには、データのクレンジングおよび準備を行う次のツールが含まれています。</span><span class="sxs-lookup"><span data-stu-id="68d0e-114">The Data Mining Add-ins for Office includes the following tools for data cleansing and preparation:</span></span>  
  
### <a name="explore-data"></a><span data-ttu-id="68d0e-115">データの探索</span><span class="sxs-lookup"><span data-stu-id="68d0e-115">Explore Data</span></span>  
 <span data-ttu-id="68d0e-116">次のデータ準備タスクを行うには、**データの探索**ウィザードを使用します。</span><span class="sxs-lookup"><span data-stu-id="68d0e-116">Use the **Explore Data** wizard for these data preparation tasks:</span></span>  
  
-   <span data-ttu-id="68d0e-117">データをプレビューし、分析前に解決する必要のあるエラーを特定します。</span><span class="sxs-lookup"><span data-stu-id="68d0e-117">Preview your data and identify errors that must be fixed prior to analysis.</span></span>  
  
-   <span data-ttu-id="68d0e-118">データのバランスと必要なクリーンアップ タスクを理解するうえで役に立つ統計情報を収集します。</span><span class="sxs-lookup"><span data-stu-id="68d0e-118">Gather statistical information that is useful for understanding the balance of data and the required clean-up tasks.</span></span>  
  
-   <span data-ttu-id="68d0e-119">分析に役立つ列を特定し、データ モデリング フェーズを計画します。</span><span class="sxs-lookup"><span data-stu-id="68d0e-119">Identify columns that are useful for analysis, and plan the data modeling phase.</span></span>  
  
 <span data-ttu-id="68d0e-120">[データの探索 &#40;SQL Server データ マイニング アドイン&#41;](explore-data-sql-server-data-mining-add-ins.md)。</span><span class="sxs-lookup"><span data-stu-id="68d0e-120">[Explore Data &#40;SQL Server Data Mining Add-ins&#41;](explore-data-sql-server-data-mining-add-ins.md).</span></span>  
  
### <a name="detect-and-handle-outliers"></a><span data-ttu-id="68d0e-121">外れ値の検出と処理</span><span class="sxs-lookup"><span data-stu-id="68d0e-121">Detect and Handle Outliers</span></span>  
 <span data-ttu-id="68d0e-122">**外れ値**ウィザードを使用して、データ内の値の分布をグラフ化し、極端な値を削除できます。</span><span class="sxs-lookup"><span data-stu-id="68d0e-122">The **Outliers** wizard graphs the distribution of values in your data and helps you remove extreme values.</span></span> <span data-ttu-id="68d0e-123">次のデータ準備タスクを行うには、**外れ値**ツールを使用します。</span><span class="sxs-lookup"><span data-stu-id="68d0e-123">Use the **Outliers** tool for the following data preparation tasks:</span></span>  
  
-   <span data-ttu-id="68d0e-124">データで検出されたパターンに基づいて、個々の値が信頼できるかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="68d0e-124">Determine whether individual values are reliable, based on patterns found in the data.</span></span>  
  
-   <span data-ttu-id="68d0e-125">通常とは異なる値を確認し、それらを削除または置換します。</span><span class="sxs-lookup"><span data-stu-id="68d0e-125">Review unusual values and take action by deleting or replacing them.</span></span>  
  
-   <span data-ttu-id="68d0e-126">モデルを特定の値の範囲にスコープします。</span><span class="sxs-lookup"><span data-stu-id="68d0e-126">Scope a model to a specific range of values.</span></span> <span data-ttu-id="68d0e-127">たとえば、特定の店舗に外れ値があることが判明している場合は、その値を除去することで、より正確に他の店舗の値を予測するモデルを取得することができます。</span><span class="sxs-lookup"><span data-stu-id="68d0e-127">For example, if you know that you have outliers at a particular store, you can eliminate that value and get a model that better predicts other stores.</span></span>  
  
 <span data-ttu-id="68d0e-128">[外れ値 &#40;SQL Server データ マイニング アドイン&#41;](outliers-sql-server-data-mining-add-ins.md)。</span><span class="sxs-lookup"><span data-stu-id="68d0e-128">[Outliers &#40;SQL Server Data Mining Add-ins&#41;](outliers-sql-server-data-mining-add-ins.md).</span></span>  
  
### <a name="relabel-and-bin-data"></a><span data-ttu-id="68d0e-129">データのラベル変更とビン分割</span><span class="sxs-lookup"><span data-stu-id="68d0e-129">Relabel and Bin Data</span></span>  
 <span data-ttu-id="68d0e-130">**ラベルの変更**ウィザードでは、データのラベルを変更できるように、データが値でグループ化されます。</span><span class="sxs-lookup"><span data-stu-id="68d0e-130">The **Relabel** wizard groups data by values so that you can change the labels on the data.</span></span> <span data-ttu-id="68d0e-131">次のデータ準備タスクを行うには、ラベルの変更ツールを使用します。</span><span class="sxs-lookup"><span data-stu-id="68d0e-131">Use the Relabel tool for these data preparation tasks:</span></span>  
  
-   <span data-ttu-id="68d0e-132">調査結果で使用されている数値コードを、そのコードの意味を示すテキストに変更します。</span><span class="sxs-lookup"><span data-stu-id="68d0e-132">Change numeric codes used in survey results to a text description of what the numeric code means.</span></span>  
  
     <span data-ttu-id="68d0e-133">たとえば、"性別 = 1" を "性別 = 女性" に置き換えるなど、データ エントリを置き換えることができます。</span><span class="sxs-lookup"><span data-stu-id="68d0e-133">For example, you might replace data entries such as Gender = 1 with Gender = Female.</span></span>  
  
-   <span data-ttu-id="68d0e-134">数値の範囲を表すグループを作成することで、データをビン分割します。</span><span class="sxs-lookup"><span data-stu-id="68d0e-134">Bin data, by creating groups to represents number ranges.</span></span>  
  
     <span data-ttu-id="68d0e-135">たとえば、数値の収入列を、**収入-** 中、**収入-高**などのラベルに置き換えることができます。</span><span class="sxs-lookup"><span data-stu-id="68d0e-135">For example, you might want to replace an Income column of numbers with labels such as **Income - Moderate** and **Income - High**.</span></span>  
  
-   <span data-ttu-id="68d0e-136">不連続値をカテゴリに分類して集約します。</span><span class="sxs-lookup"><span data-stu-id="68d0e-136">Collapse discrete values into categories.</span></span>  
  
     <span data-ttu-id="68d0e-137">たとえば、購入のパターンを検出するには個別の製品が多すぎる場合、製品をより幅広いカテゴリに割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="68d0e-137">For example, if you have too many individual products to detect a pattern among purchases, you could try assigning products into broader categories.</span></span>  
  
 [<span data-ttu-id="68d0e-138">&#40;SQL Server データマイニングアドインのラベルを再付け&#41;</span><span class="sxs-lookup"><span data-stu-id="68d0e-138">Relabel &#40;SQL Server Data Mining Add-ins&#41;</span></span>](relabel-sql-server-data-mining-add-ins.md)  
  
### <a name="cleanse-data"></a><span data-ttu-id="68d0e-139">データのクレンジング</span><span class="sxs-lookup"><span data-stu-id="68d0e-139">Cleanse Data</span></span>  
 <span data-ttu-id="68d0e-140">データ クレンジングでは、さまざまな処理が行われ、そのほとんどがアドインによってサポートされています。</span><span class="sxs-lookup"><span data-stu-id="68d0e-140">Data cleansing encompasses a wide range of activities, most of which are supported by the add-ins</span></span>  
  
-   <span data-ttu-id="68d0e-141">NULL 値を識別して、それを実際の値に変更するか、`Missing` 値として処理するかを決定します。</span><span class="sxs-lookup"><span data-stu-id="68d0e-141">Identify nulls and determine whether they should be changed to a real value or handled as `Missing` values.</span></span>  
  
-   <span data-ttu-id="68d0e-142">不足値を検出して削除するか、平均値や NULL などの適切な値を帰属させます。</span><span class="sxs-lookup"><span data-stu-id="68d0e-142">Detect missing values, and then remove them, or impute an appropriate value, such as a mean, null, or other value.</span></span>  
  
 [<span data-ttu-id="68d0e-143">データ &#40;SQL Server データマイニングアドインの探索&#41;</span><span class="sxs-lookup"><span data-stu-id="68d0e-143">Explore Data &#40;SQL Server Data Mining Add-ins&#41;</span></span>](explore-data-sql-server-data-mining-add-ins.md)  
  
 [<span data-ttu-id="68d0e-144">&#40;SQL Server データマイニングアドインのラベルを再付け&#41;</span><span class="sxs-lookup"><span data-stu-id="68d0e-144">Relabel &#40;SQL Server Data Mining Add-ins&#41;</span></span>](relabel-sql-server-data-mining-add-ins.md)  
  
 [<span data-ttu-id="68d0e-145">例の全体適用</span><span class="sxs-lookup"><span data-stu-id="68d0e-145">Fill From Example</span></span>](fill-from-example-table-analysis-tools-for-excel.md)  
  
### <a name="sample-data"></a><span data-ttu-id="68d0e-146">サンプル データ</span><span class="sxs-lookup"><span data-stu-id="68d0e-146">Sample Data</span></span>  
 <span data-ttu-id="68d0e-147">サンプル データ ウィザードでは、モデルのトレーニングとテストに使用する均衡の取れたデータ セットを 2 つの方法で作成できます。</span><span class="sxs-lookup"><span data-stu-id="68d0e-147">The Sample Data wizard provides two methods for creating balanced data sets for training and testing models.</span></span>  
  
-   <span data-ttu-id="68d0e-148">**ランダムサンプリング。**</span><span class="sxs-lookup"><span data-stu-id="68d0e-148">**Random sampling.**</span></span> <span data-ttu-id="68d0e-149">トレーニングやテストに使用するために、大きなデータ セットから対応するデータ セットを抽出する場合にこのオプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="68d0e-149">Use this option to extract a representative set of data from a larger data set, for use in either training or testing.</span></span> <span data-ttu-id="68d0e-150">データ マイニング アドインでは、*階層化されたサンプリング*を使用して、サンプリングされた各変数に対してバランスの取れた値のセットが取得されるようにします。</span><span class="sxs-lookup"><span data-stu-id="68d0e-150">The Data Mining Add-ins use *stratified sampling* to ensure that a balanced set of values is obtained for each variable sampled.</span></span>  
  
-   <span data-ttu-id="68d0e-151">**[オーバーサンプリング]。**</span><span class="sxs-lookup"><span data-stu-id="68d0e-151">**Oversampling.**</span></span> <span data-ttu-id="68d0e-152">対象となる結果に対してデータが不足しており、そのデータにより重みを付ける必要がある場合にこのオプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="68d0e-152">Use this option when you have less data than you would like for a target outcome, and need to weight that data more heavily.</span></span> <span data-ttu-id="68d0e-153">たとえば、詐欺行為は比較的まれにしか発生しませんが、詐欺行為に関連するケースをオーバーサンプリングして、モデリングするための最適化データを取得できます。</span><span class="sxs-lookup"><span data-stu-id="68d0e-153">For example, fraud might be relatively rare, but you can oversample cases involving fraud to get adequate data for modeling.</span></span>  
  
 <span data-ttu-id="68d0e-154">[サンプル データ &#40;SQL Server データ マイニング アドイン&#41;](sample-data-sql-server-data-mining-add-ins.md)。</span><span class="sxs-lookup"><span data-stu-id="68d0e-154">[Sample Data &#40;SQL Server Data Mining Add-ins&#41;](sample-data-sql-server-data-mining-add-ins.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68d0e-155">参照</span><span class="sxs-lookup"><span data-stu-id="68d0e-155">See Also</span></span>  
 <span data-ttu-id="68d0e-156">[データマイニングモデルの作成](creating-a-data-mining-model.md) </span><span class="sxs-lookup"><span data-stu-id="68d0e-156">[Creating a Data Mining Model](creating-a-data-mining-model.md) </span></span>  
 <span data-ttu-id="68d0e-157">[Excel 用データマイニングアドインのモデルを検証し、モデルを使用して予測 &#40;する&#41;](validating-models-and-using-models-for-prediction-data-mining-add-ins-for-excel.md) </span><span class="sxs-lookup"><span data-stu-id="68d0e-157">[Validating Models and Using Models for Prediction &#40;Data Mining Add-ins for Excel&#41;](validating-models-and-using-models-for-prediction-data-mining-add-ins-for-excel.md) </span></span>  
 [<span data-ttu-id="68d0e-158">Excel 用データマイニングアドイン &#40;のマイニングモデルの配置とスケーリング&#41;</span><span class="sxs-lookup"><span data-stu-id="68d0e-158">Deploying and Scaling Mining Models &#40;Data Mining Add-ins for Excel&#41;</span></span>](deploying-and-scaling-mining-models-data-mining-add-ins-for-excel.md)  
  
  
