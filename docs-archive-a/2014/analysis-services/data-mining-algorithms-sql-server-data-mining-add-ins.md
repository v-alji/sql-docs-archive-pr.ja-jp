---
title: データマイニングアルゴリズム (SQL Server データマイニングアドイン) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- segmentation
- data mining algorithms
- clustering [data mining]
- linear regression
- association [data mining]
- neural networks
- logistic regression
- regression
- sequence analysis
- decision tree [data mining]
- Naive Bayes
- time series [data mining]
ms.assetid: 3a1a62e4-9fb5-4cdb-a6c6-1b8b30d417ef
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3a73ce5a538756a740afd2db72d585fa54f03cae
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644242"
---
# <a name="data-mining-algorithms-sql-server-data-mining-add-ins"></a><span data-ttu-id="f99bf-102">データ マイニング アルゴリズム (SQL Server データ マイニング アドイン)</span><span class="sxs-lookup"><span data-stu-id="f99bf-102">Data Mining Algorithms (SQL Server Data Mining Add-ins)</span></span>
  <span data-ttu-id="f99bf-103">Office 用データ マイニング アドインは、次のデータ マイニング アルゴリズムを使用して分析モデルの作成をサポートします。</span><span class="sxs-lookup"><span data-stu-id="f99bf-103">The Data Mining Add-ins for Office supports creation of analytical models using the following data mining algorithms.</span></span> <span data-ttu-id="f99bf-104">すべてのアルゴリズムは、よく知られている機械学習メソッドに基づいており、Microsoft Research によって実装されたものです。</span><span class="sxs-lookup"><span data-stu-id="f99bf-104">All algorithms are based on well-known machine learning methods and have been implemented by Microsoft Research.</span></span>  
  
## <a name="algorithms"></a><span data-ttu-id="f99bf-105">アルゴリズム</span><span class="sxs-lookup"><span data-stu-id="f99bf-105">Algorithms</span></span>  
  
|<span data-ttu-id="f99bf-106">機械学習メソッド</span><span class="sxs-lookup"><span data-stu-id="f99bf-106">Machine learning method</span></span>|<span data-ttu-id="f99bf-107">しくみ</span><span class="sxs-lookup"><span data-stu-id="f99bf-107">How it works</span></span>|  
|-----------------------------|------------------|  
|<span data-ttu-id="f99bf-108">Microsoft アソシエーションルールアルゴリズム</span><span class="sxs-lookup"><span data-stu-id="f99bf-108">Microsoft Association Rules  algorithm</span></span>|<span data-ttu-id="f99bf-109">どの製品がともに購入されているか、またはどのイベントがともに発生するかを検出し、おすすめを作成するためのモデルを使用します。</span><span class="sxs-lookup"><span data-stu-id="f99bf-109">Discover which products are purchased together or which events occur together, and use the model to create recommendations.</span></span><br /><br /> [https://msdn.microsoft.com/library/ms174916.aspx](https://msdn.microsoft.com/library/ms174916.aspx)|  
|<span data-ttu-id="f99bf-110">Microsoft クラスタリング アルゴリズム</span><span class="sxs-lookup"><span data-stu-id="f99bf-110">Microsoft Clustering algorithm</span></span>|<span data-ttu-id="f99bf-111">市場セグメントを定義し、関連のある複数の顧客を自動的にグループ化するか、データ内のリレーションシップを見つけてそれ以降のマイニングで使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="f99bf-111">Define market segments, automatically group related customers together, or find relationships in data to use in further mining.</span></span><br /><br /> [https://msdn.microsoft.com/library/ms174879.aspx](https://msdn.microsoft.com/library/ms174879.aspx)|  
|<span data-ttu-id="f99bf-112">Microsoft デシジョン ツリー アルゴリズム</span><span class="sxs-lookup"><span data-stu-id="f99bf-112">Microsoft Decision Trees algorithm</span></span>|<span data-ttu-id="f99bf-113">データ内のさまざまな要素間で、従来は不明だったリレーションシップを識別し、意思決定を下すためにより適切な情報を提供するか、特定の結果につながる要因を見つけます。</span><span class="sxs-lookup"><span data-stu-id="f99bf-113">Identify previously unknown relationships between various elements of your data to better inform your decisions, or find the factors that lead to specific outcomes.</span></span><br /><br /> [https://msdn.microsoft.com/library/ms174923.aspx](https://msdn.microsoft.com/library/ms174923.aspx)|  
|<span data-ttu-id="f99bf-114">Microsoft 線形回帰アルゴリズム</span><span class="sxs-lookup"><span data-stu-id="f99bf-114">Microsoft Linear Regression algorithm</span></span>|<span data-ttu-id="f99bf-115">数値形式の結果に寄与する要因を表す算術式を見つけます。</span><span class="sxs-lookup"><span data-stu-id="f99bf-115">Find a mathematical formula that describes factors that contribute to a numeric outcome.</span></span><br /><br /> [https://msdn.microsoft.com/library/ms174824.aspx](https://msdn.microsoft.com/library/ms174824.aspx)|  
|<span data-ttu-id="f99bf-116">Microsoft ロジスティック回帰アルゴリズム</span><span class="sxs-lookup"><span data-stu-id="f99bf-116">Microsoft Logistic Regression algorithm</span></span>|<span data-ttu-id="f99bf-117">バイナリ結果に寄与する要素を見つけ、それらの要素が結果にどのような影響を及ぼすかを研究します。</span><span class="sxs-lookup"><span data-stu-id="f99bf-117">Identify the factors that contribute to binary outcomes, and learn how to use those to affect results.</span></span><br /><br /> [https://msdn.microsoft.com/library/ms174828.aspx](https://msdn.microsoft.com/library/ms174828.aspx)|  
|<span data-ttu-id="f99bf-118">Microsoft Naïve Bayes アルゴリズム</span><span class="sxs-lookup"><span data-stu-id="f99bf-118">Microsoft Naïve Bayes algorithm</span></span>|<span data-ttu-id="f99bf-119">データ内のリレーションシップを探索し、結果との関連性が最も強いリレーションシップを見つけます。</span><span class="sxs-lookup"><span data-stu-id="f99bf-119">Explore relationships in your data and find those mostly closely correlated with an outcome.</span></span><br /><br /> [https://msdn.microsoft.com/library/ms174806.aspx](https://msdn.microsoft.com/library/ms174806.aspx)|  
|<span data-ttu-id="f99bf-120">Microsoft ニューラルネットワークアルゴリズム</span><span class="sxs-lookup"><span data-stu-id="f99bf-120">Microsoft Neural Networks algorithm</span></span>|<span data-ttu-id="f99bf-121">複数の入力と複数の出力の間に存在する隠されたリレーションシップを見つけます。</span><span class="sxs-lookup"><span data-stu-id="f99bf-121">Find hidden relationships among multiple inputs and even multiple outputs.</span></span> <span data-ttu-id="f99bf-122">探索または予測の目的で使用します。</span><span class="sxs-lookup"><span data-stu-id="f99bf-122">Use for exploration or for prediction.</span></span><br /><br /> [https://msdn.microsoft.com/library/ms174941.aspx](https://msdn.microsoft.com/library/ms174941.aspx)|  
|<span data-ttu-id="f99bf-123">Microsoft Time Series アルゴリズム</span><span class="sxs-lookup"><span data-stu-id="f99bf-123">Microsoft Time Series algorithm</span></span>|<span data-ttu-id="f99bf-124">履歴データを使用して将来の値を予測します。</span><span class="sxs-lookup"><span data-stu-id="f99bf-124">Use historical data to forecast future values.</span></span><br /><br /> [https://msdn.microsoft.com/library/ms174923.aspx](https://msdn.microsoft.com/library/ms174923.aspx)|  
  
## <a name="advanced-options"></a><span data-ttu-id="f99bf-125">詳細オプション</span><span class="sxs-lookup"><span data-stu-id="f99bf-125">Advanced Options</span></span>  
 <span data-ttu-id="f99bf-126">Excel 用のデータ マイニング クライアントを使用する場合は、独自のデータ マイニング構造およびモデルを作成したり、アルゴリズムのパラメーターを調整したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="f99bf-126">When you use the Data Mining Client for Excel, you have the option to create your own data mining structures and models, or to fine-tune the parameters of the algorithms.</span></span>  
  
 [<span data-ttu-id="f99bf-127">データマイニングアドイン SQL Server &#40;のアルゴリズムパラメーター&#41;</span><span class="sxs-lookup"><span data-stu-id="f99bf-127">Algorithm Parameters &#40;SQL Server Data Mining Add-ins&#41;</span></span>](algorithm-parameters-sql-server-data-mining-add-ins.md)  
  
 <span data-ttu-id="f99bf-128">これらの詳細オプションを使用してモデルをカスタマイズする方法は 2 つあります。</span><span class="sxs-lookup"><span data-stu-id="f99bf-128">There are two ways to customize your models using these advanced options:</span></span>  
  
-   <span data-ttu-id="f99bf-129">**データマイニングクエリ**ウィザードを使用して、モデルを作成します。</span><span class="sxs-lookup"><span data-stu-id="f99bf-129">Use the **Data Mining Query** wizard to create your model.</span></span>  
  
-   <span data-ttu-id="f99bf-130">**データマイニングクライアント**で、ウィザードを開始した後、[**パラメーター**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f99bf-130">In the **Data Mining Client**, after you start the wizard, click **Parameters**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f99bf-131">参照</span><span class="sxs-lookup"><span data-stu-id="f99bf-131">See Also</span></span>  
 <span data-ttu-id="f99bf-132">[クエリ &#40;SQL Server データマイニングアドイン&#41;](query-sql-server-data-mining-add-ins.md) </span><span class="sxs-lookup"><span data-stu-id="f99bf-132">[Query &#40;SQL Server Data Mining Add-ins&#41;](query-sql-server-data-mining-add-ins.md) </span></span>  
 [<span data-ttu-id="f99bf-133">高度なモデリング &#40;Excel 用データマイニングアドイン&#41;</span><span class="sxs-lookup"><span data-stu-id="f99bf-133">Advanced Modeling &#40;Data Mining Add-ins for Excel&#41;</span></span>](advanced-modeling-data-mining-add-ins-for-excel.md)  
  
  
