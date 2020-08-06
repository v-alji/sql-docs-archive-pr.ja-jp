---
title: モデルの検証と予測用のモデルの使用 (Excel 用データマイニングアドイン) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models, validating
- mining models, charting
- validation [data mining]
- mining models, testing
ms.assetid: e245ac1f-1230-48e9-9091-e70b131aa2a8
author: minewiskan
ms.author: owend
ms.openlocfilehash: c1dd4f9bab977a90579076b824d2c0aa525c84af
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634663"
---
# <a name="validating-models-and-using-models-for-prediction-data-mining-add-ins-for-excel"></a><span data-ttu-id="7c09f-102">モデルの検証と予測用モデルの使用 (Excel 用データ マイニング アドイン)</span><span class="sxs-lookup"><span data-stu-id="7c09f-102">Validating Models and Using Models for Prediction (Data Mining Add-ins for Excel)</span></span>
  <span data-ttu-id="7c09f-103">モデルのテストと検証は、データ マイニング プロセスにおける重要な手順です。</span><span class="sxs-lookup"><span data-stu-id="7c09f-103">Testing and validating your model is an important step in the data mining process.</span></span> <span data-ttu-id="7c09f-104">実際のデータに対するマイニング モデルの性能を、運用環境に配置する前に知っておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="7c09f-104">You must know how well your mining models perform against real data before you deploy the models into a production environment.</span></span>  
  
 <span data-ttu-id="7c09f-105">データ マイニング アドインには、構築したモデルをテストし、そのモデルを使用して予測と提案を作成するためのツールが含まれています。</span><span class="sxs-lookup"><span data-stu-id="7c09f-105">The Data Mining Add-ins include tools that help you test the models you built, and create predictions and recommendations using the models.</span></span>  
  
## <a name="accuracy-chart"></a><span data-ttu-id="7c09f-106">精度チャート</span><span class="sxs-lookup"><span data-stu-id="7c09f-106">Accuracy Chart</span></span>  
 <span data-ttu-id="7c09f-107">**精度チャート**ウィザードを使用すると、予測クエリを作成し、リフトチャートまたは散布図を作成することによって、データマイニングモデルのパフォーマンスを評価できます。</span><span class="sxs-lookup"><span data-stu-id="7c09f-107">The **Accuracy Chart** wizard helps you create a prediction query and assess the performance of a data mining model by creating a lift chart or scatter plot chart.</span></span> <span data-ttu-id="7c09f-108">ほぼ同じ構造を持つ 2 つのモデルを区別し、どちらの予測精度が高いかを調べるにはリフト チャートが有効です。</span><span class="sxs-lookup"><span data-stu-id="7c09f-108">The lift chart helps distinguish between models in a structure that are almost the same, to help you determine which model provides the best predictions.</span></span>  
  
 [<span data-ttu-id="7c09f-109">精度チャート &#40;SQL Server データマイニングアドイン&#41;</span><span class="sxs-lookup"><span data-stu-id="7c09f-109">Accuracy Chart &#40;SQL Server Data Mining Add-ins&#41;</span></span>](accuracy-chart-sql-server-data-mining-add-ins.md)  
  
## <a name="classification-matrix"></a><span data-ttu-id="7c09f-110">分類マトリックス</span><span class="sxs-lookup"><span data-stu-id="7c09f-110">Classification Matrix</span></span>  
 <span data-ttu-id="7c09f-111">**分類マトリックス**ウィザードを使用すると、予測クエリを作成して分類モデルのパフォーマンスを評価できます。</span><span class="sxs-lookup"><span data-stu-id="7c09f-111">The **Classification Matrix** wizard helps you create a prediction query to assess the performance of a classification model.</span></span> <span data-ttu-id="7c09f-112">モデルによって生成された正確な予測と不正確な予測を両方示す概要グラフが出力されます。</span><span class="sxs-lookup"><span data-stu-id="7c09f-112">The output is a chart that summarizes both accurate and inaccurate predictions made by the model.</span></span> <span data-ttu-id="7c09f-113">分類マトリックスは、モデルによって値が正しく予測された頻度だけでなく、モデルによって最も頻繁に誤って予測された値も示されるので、非常に便利なツールです。</span><span class="sxs-lookup"><span data-stu-id="7c09f-113">The matrix is a valuable tool because it not only shows how frequently the model correctly predicted a value, but also shows which values the model most frequently predicted incorrectly.</span></span>  
  
 [<span data-ttu-id="7c09f-114">分類マトリックス &#40;SQL Server データマイニングアドイン&#41;</span><span class="sxs-lookup"><span data-stu-id="7c09f-114">Classification Matrix &#40;SQL Server Data Mining Add-ins&#41;</span></span>](classification-matrix-sql-server-data-mining-add-ins.md)  
  
## <a name="profit-chart"></a><span data-ttu-id="7c09f-115">利益チャート</span><span class="sxs-lookup"><span data-stu-id="7c09f-115">Profit Chart</span></span>  
 <span data-ttu-id="7c09f-116">**利益チャート**ウィザードを使用すると、データマイニングモデルを使用する利点を比較し、誤検知と誤否定の両方のコストを評価することができます。</span><span class="sxs-lookup"><span data-stu-id="7c09f-116">The **Profit Chart** wizard helps you weigh the benefits of using a data mining model and assess the costs of both false positives and false negatives</span></span>  
  
 <span data-ttu-id="7c09f-117">この種類のチャートでは、モデルの予測精度が測定され、単位あたりのコストと全体のコストが組み込まれます。</span><span class="sxs-lookup"><span data-stu-id="7c09f-117">This chart type measures the prediction accuracy of the model and incorporates unit and overall costs that you specify.</span></span>  
  
 <span data-ttu-id="7c09f-118">[利益チャート &#40;データマイニングアドイン&#41;SQL Server](profit-chart-sql-server-data-mining-add-ins.md)ます。</span><span class="sxs-lookup"><span data-stu-id="7c09f-118">[Profit Chart &#40;SQL Server Data Mining Add-ins&#41;](profit-chart-sql-server-data-mining-add-ins.md).</span></span>  
  
## <a name="cross-validation"></a><span data-ttu-id="7c09f-119">クロス検証</span><span class="sxs-lookup"><span data-stu-id="7c09f-119">Cross-Validation</span></span>  
 <span data-ttu-id="7c09f-120">クロス検証は、データ セットの妥当性を評価しデータ セットに対するマイニング モデルの精度を評価するための、データ マイニング コミュニティで確立された方法です。</span><span class="sxs-lookup"><span data-stu-id="7c09f-120">Cross-validation is an established technique in the data mining community for assessing the validity of a data set and the accuracy of a mining model on that data set.</span></span> <span data-ttu-id="7c09f-121">クロス検証では、データ セットをサブセットに分割し、モデルの作成、トレーニング、およびテストを各サブセットに対して繰り返し実行します。</span><span class="sxs-lookup"><span data-stu-id="7c09f-121">It divides a set of data into subsets, and then iteratively creates, trains, and tests models on each subset.</span></span>  
  
 <span data-ttu-id="7c09f-122">**クロス検証**ウィザードでは、でデータを分割するフォールドの数を指定できます。また、クロス検証レポートを使用して、これらのセクション間の違いを統計的に説明します。</span><span class="sxs-lookup"><span data-stu-id="7c09f-122">The **Cross-Validation** wizard lets you specify the number of folds to divide your data by, and then provides a cross-validation report that statistically describes the differences among these cross-sections.</span></span> <span data-ttu-id="7c09f-123">これに基づいて、モデルが、すべてのトレーニング データに対して適切に機能しているか、特定のサブセットに偏っているかを判断できます。</span><span class="sxs-lookup"><span data-stu-id="7c09f-123">From this you can determine whether the model performs well on all training data, or might be skewed to a particular subset.</span></span>  
  
 [<span data-ttu-id="7c09f-124">相互検証 &#40;SQL Server データマイニングアドイン&#41;</span><span class="sxs-lookup"><span data-stu-id="7c09f-124">Cross-Validation &#40;SQL Server Data Mining Add-ins&#41;</span></span>](cross-validation-sql-server-data-mining-add-ins.md)  
  
## <a name="query-wizard"></a><span data-ttu-id="7c09f-125">クエリ ウィザード</span><span class="sxs-lookup"><span data-stu-id="7c09f-125">Query Wizard</span></span>  
 <span data-ttu-id="7c09f-126">**クエリ**ウィザードは、予測クエリの作成に役立つ対話型のツールです。</span><span class="sxs-lookup"><span data-stu-id="7c09f-126">The **Query** wizard is an interactive tool that helps you build a prediction query.</span></span> <span data-ttu-id="7c09f-127">クエリによって、提案や将来の予測などを生成する方法が定義されます。</span><span class="sxs-lookup"><span data-stu-id="7c09f-127">Queries are how you generate recommendations, future forecasts, and so forth.</span></span>  
  
 <span data-ttu-id="7c09f-128">**クエリ**ウィザードでは、モデルを選択し、単一の値またはテーブルまたは範囲の入力データを指定します。このウィザードを使用して、出力する列を選択できます。</span><span class="sxs-lookup"><span data-stu-id="7c09f-128">In the **Query** wizard, you pick a model, and then provide input data, either as single values or from a table or range, and the wizard helps you select columns to output.</span></span> <span data-ttu-id="7c09f-129">また、確率スコアやその他の有用な統計情報を生成する関数をクエリに追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="7c09f-129">You can also add functions to your query to generate probability scores and other useful statistics.</span></span>  
  
 [<span data-ttu-id="7c09f-130">クエリ &#40;SQL Server データマイニングアドイン&#41;</span><span class="sxs-lookup"><span data-stu-id="7c09f-130">Query &#40;SQL Server Data Mining Add-ins&#41;</span></span>](query-sql-server-data-mining-add-ins.md)  
  
## <a name="advanced-query-editor"></a><span data-ttu-id="7c09f-131">詳細クエリ エディター</span><span class="sxs-lookup"><span data-stu-id="7c09f-131">Advanced Query Editor</span></span>  
 <span data-ttu-id="7c09f-132">**詳細クエリエディター**は、ダイアログボックスの対話型セットであり、カスタムクエリの実行から、新しいモデルの作成とトレーニング、モデルの削除、新しいデータセットの作成まで、あらゆる種類の DMX ステートメントを作成するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="7c09f-132">The **Advanced Query Editor** is an interactive set of dialog boxes that helps you build all kinds of DMX statements, anything from running custom queries to creating and training new models, deleting models, or creating new data sets.</span></span>  
  
 [<span data-ttu-id="7c09f-133">詳細データ マイニング クエリ エディター</span><span class="sxs-lookup"><span data-stu-id="7c09f-133">Advanced Data Mining Query Editor</span></span>](advanced-data-mining-query-editor.md)  
  
## <a name="see-also"></a><span data-ttu-id="7c09f-134">参照</span><span class="sxs-lookup"><span data-stu-id="7c09f-134">See Also</span></span>  
 <span data-ttu-id="7c09f-135">[データの探索とクリーンアップ](exploring-and-cleaning-data.md) </span><span class="sxs-lookup"><span data-stu-id="7c09f-135">[Exploring and Cleaning Data](exploring-and-cleaning-data.md) </span></span>  
 <span data-ttu-id="7c09f-136">[データマイニングモデルの作成](creating-a-data-mining-model.md) </span><span class="sxs-lookup"><span data-stu-id="7c09f-136">[Creating a Data Mining Model](creating-a-data-mining-model.md) </span></span>  
 [<span data-ttu-id="7c09f-137">Excel 用データマイニングアドイン &#40;のマイニングモデルの配置とスケーリング&#41;</span><span class="sxs-lookup"><span data-stu-id="7c09f-137">Deploying and Scaling Mining Models &#40;Data Mining Add-ins for Excel&#41;</span></span>](deploying-and-scaling-mining-models-data-mining-add-ins-for-excel.md)  
  
  
