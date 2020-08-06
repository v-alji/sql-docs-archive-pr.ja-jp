---
title: Excel 用のテーブル分析ツール |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Table Analysis tools
- getting started
ms.assetid: 6d9d1481-18e4-4108-9efa-68152b0940c9
author: minewiskan
ms.author: owend
ms.openlocfilehash: e566f5213f1ecd98685a3199c57b962be96c5aa7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736810"
---
# <a name="table-analysis-tools-for-excel"></a><span data-ttu-id="1dd84-102">Excel 用テーブル分析ツール</span><span class="sxs-lookup"><span data-stu-id="1dd84-102">Table Analysis Tools for Excel</span></span>
  <span data-ttu-id="1dd84-103">[**分析**] ツールバーのデータマイニングツールは、データマイニングを開始する最も簡単な方法です。</span><span class="sxs-lookup"><span data-stu-id="1dd84-103">The data mining tools in the **Analyze** toolbar are the easiest way to get started with data mining.</span></span> <span data-ttu-id="1dd84-104">これらのツールは、自動的にデータの分布と型を分析し、有効な結果を取得できるようパラメーターを設定します。</span><span class="sxs-lookup"><span data-stu-id="1dd84-104">Each tool automatically analyzes the distribution and type of your data, and sets the parameters to ensure that results are valid.</span></span> <span data-ttu-id="1dd84-105">アルゴリズムを選択したり、複雑なパラメーターを構成したりする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="1dd84-105">You do not have to select an algorithm or configure complex parameters.</span></span>  
  
 <span data-ttu-id="1dd84-106">![DM](media/dm-tabletoolsanalyze.gif "DM")</span><span class="sxs-lookup"><span data-stu-id="1dd84-106">![DM](media/dm-tabletoolsanalyze.gif "DM")</span></span>  
  
 <span data-ttu-id="1dd84-107">[**分析**リボンには、次のツールがあります。</span><span class="sxs-lookup"><span data-stu-id="1dd84-107">The **Analyze** ribbon includes the following tools:</span></span>  
  
 [<span data-ttu-id="1dd84-108">Excel 用のテーブル分析ツール &#40;主要な影響元の分析&#41;</span><span class="sxs-lookup"><span data-stu-id="1dd84-108">Analyze Key Influencers &#40;Table Analysis Tools for Excel&#41;</span></span>](analyze-key-influencers-table-analysis-tools-for-excel.md)  
 <span data-ttu-id="1dd84-109">目的の列または出力値を選択すると、アルゴリズムがすべての入力データを分析して、対象に最大の影響を与えている要因を特定します。</span><span class="sxs-lookup"><span data-stu-id="1dd84-109">You choose a column or output value of interest, and then the algorithm analyzes all the input data to identify the factors that have the most influence on the target.</span></span> <span data-ttu-id="1dd84-110">必要に応じて、2 つの値を比較するレポートを作成できます。これにより、影響元がどのように変化するかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="1dd84-110">Optionally, you can create a report that compares any two values, so that you can see how the influencers change.</span></span>  
  
 <span data-ttu-id="1dd84-111">**主要影響**元の分析ツールでは、Microsoft の単純 Bayes アルゴリズムが使用されます。</span><span class="sxs-lookup"><span data-stu-id="1dd84-111">The **Analyze Key Influencers** tool uses the Microsoft Naïve Bayes algorithm.</span></span>  
  
 [<span data-ttu-id="1dd84-112">Excel 用のテーブル分析ツール &#40;のカテゴリの検出&#41;</span><span class="sxs-lookup"><span data-stu-id="1dd84-112">Detect Categories &#40;Table Analysis Tools for Excel&#41;</span></span>](detect-categories-table-analysis-tools-for-excel.md)  
 <span data-ttu-id="1dd84-113">このツールを使用すると、任意のデータセットを追加し、クラスタリングを適用することによって、データのグループ化を検出できます。</span><span class="sxs-lookup"><span data-stu-id="1dd84-113">This tool lets you add any data set and apply clustering to find groupings of data.</span></span> <span data-ttu-id="1dd84-114">類似点を見つけて、さらに分析するグループを作成する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="1dd84-114">It's useful for finding similarities and for creating groups to further analyze.</span></span>  
  
 <span data-ttu-id="1dd84-115">**カテゴリの検出**ツールは、Microsoft クラスタリングアルゴリズムを使用します。</span><span class="sxs-lookup"><span data-stu-id="1dd84-115">The **Detect Categories** tool uses the Microsoft Clustering algorithm.</span></span>  
  
 [<span data-ttu-id="1dd84-116">例 &#40;Excel 用のテーブル分析ツール&#41;</span><span class="sxs-lookup"><span data-stu-id="1dd84-116">Fill From Example &#40;Table Analysis Tools for Excel&#41;</span></span>](fill-from-example-table-analysis-tools-for-excel.md)  
 <span data-ttu-id="1dd84-117">このツールは、不足値を帰属させるために役立ちます。</span><span class="sxs-lookup"><span data-stu-id="1dd84-117">This tool helps you impute missing values.</span></span> <span data-ttu-id="1dd84-118">不足値の例をいくつか指定すると、このツールはテーブル内のすべてのデータに基づいてパターンを作成し、データのパターンに基づいて新しい値を推奨します。</span><span class="sxs-lookup"><span data-stu-id="1dd84-118">You provide some examples of what the missing values should be, and the tool builds patterns based on all data in the table, and then recommends new values based on patterns in the data.</span></span>  
  
 <span data-ttu-id="1dd84-119">**Fill From サンプル**ツールは、Microsoft ロジスティック回帰アルゴリズムを使用します。</span><span class="sxs-lookup"><span data-stu-id="1dd84-119">The **Fill From Example** tool uses the Microsoft Logistic Regression algorithm.</span></span>  
  
 [<span data-ttu-id="1dd84-120">Excel 用のテーブル分析ツールの予測 &#40;&#41;</span><span class="sxs-lookup"><span data-stu-id="1dd84-120">Forecast &#40;Table Analysis Tools for Excel&#41;</span></span>](forecast-table-analysis-tools-for-excel.md)  
 <span data-ttu-id="1dd84-121">このツールは、時間の経過と共に変化するデータを取得し、将来の値を予測します。</span><span class="sxs-lookup"><span data-stu-id="1dd84-121">This tool takes data that changes over time, and predicts future values.</span></span>  
  
 <span data-ttu-id="1dd84-122">**予測**ツールでは、Microsoft タイムシリーズアルゴリズムが使用されます。</span><span class="sxs-lookup"><span data-stu-id="1dd84-122">The **Forecast** tool uses the Microsoft Time Series algorithm.</span></span>  
  
 [<span data-ttu-id="1dd84-123">Excel 用のテーブル分析ツール &#40;例外を強調表示&#41;</span><span class="sxs-lookup"><span data-stu-id="1dd84-123">Highlight Exceptions &#40;Table Analysis Tools for Excel&#41;</span></span>](highlight-exceptions-table-analysis-tools-for-excel.md)  
 <span data-ttu-id="1dd84-124">このツールでは、データテーブル内のパターンを分析し、パターンに合わない行と値を検索します。</span><span class="sxs-lookup"><span data-stu-id="1dd84-124">This tool analyzes patterns in a table of data and finds rows and values that don't fit the pattern.</span></span> <span data-ttu-id="1dd84-125">ユーザーは、これらの値を確認し、修正してモデルを再実行することも、後で処理するためにこれらの値にフラグを設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="1dd84-125">You can then review and correct them and rerun the model, or flag values for later action.</span></span>  
  
 <span data-ttu-id="1dd84-126">**例外の強調表示**ツールは、Microsoft クラスタリングアルゴリズムを使用します。</span><span class="sxs-lookup"><span data-stu-id="1dd84-126">The **Highlight Exceptions** tool uses the Microsoft Clustering algorithm.</span></span>  
  
 [<span data-ttu-id="1dd84-127">ゴールシークシナリオ &#40;Excel 用のテーブル分析ツール&#41;</span><span class="sxs-lookup"><span data-stu-id="1dd84-127">Goal Seek Scenario &#40;Table Analysis Tools for Excel&#41;</span></span>](goal-seek-scenario-table-analysis-tools-for-excel.md)  
 <span data-ttu-id="1dd84-128">**ゴールシーク**ツールでは、ターゲット値を指定します。このツールは、そのターゲットを満たすために変更する必要がある基になる要因を識別します。</span><span class="sxs-lookup"><span data-stu-id="1dd84-128">In the **Goal Seek** tool, you specify a target value, and the tool identifies the underlying factors that must change to meet that target.</span></span> <span data-ttu-id="1dd84-129">たとえば、電話対応満足度を 20% 向上させる必要がある場合、その目標を達成するために変更する必要のある要因を予測するようモデルに要求できます。</span><span class="sxs-lookup"><span data-stu-id="1dd84-129">For example, if you know that you must increase call satisfaction by 20%, you can ask the model to predict the factors that should change to produce that goal.</span></span>  
  
 <span data-ttu-id="1dd84-130">**ゴールシーク**ツールは、Microsoft ロジスティック回帰アルゴリズムを使用します。</span><span class="sxs-lookup"><span data-stu-id="1dd84-130">The **Goal Seek** tool uses the Microsoft Logistic Regression algorithm.</span></span>  
  
 [<span data-ttu-id="1dd84-131">What-if シナリオ &#40;Excel 用のテーブル分析ツール&#41;</span><span class="sxs-lookup"><span data-stu-id="1dd84-131">What-If Scenario &#40;Table Analysis Tools for Excel&#41;</span></span>](what-if-scenario-table-analysis-tools-for-excel.md)  
 <span data-ttu-id="1dd84-132">**What-if 分析**ツールは、**ゴールシーク**ツールを補完します。</span><span class="sxs-lookup"><span data-stu-id="1dd84-132">The **What-If Analysis** tool complements the **Goal Seek** tool.</span></span> <span data-ttu-id="1dd84-133">このツールで変更する必要のある値を入力すると、モデルはその変更が目標の結果を達成するために十分であるかどうかを予測します。</span><span class="sxs-lookup"><span data-stu-id="1dd84-133">With this tool, you entered the value you want to change, and the model predicts whether that change will be sufficient to achieve the desired outcome.</span></span> <span data-ttu-id="1dd84-134">たとえば、電話オペレーターを 1 人追加することによって顧客満足度が 1 ポイント向上するかどうかを推測するようモデルに要求できます。</span><span class="sxs-lookup"><span data-stu-id="1dd84-134">For example, you might ask the model to infer whether adding one extra call operator would increase customer satisfaction by one point.</span></span>  
  
 <span data-ttu-id="1dd84-135">**What-if**ツールは、Microsoft ロジスティック回帰アルゴリズムを使用します。</span><span class="sxs-lookup"><span data-stu-id="1dd84-135">The **What-If** tool uses the Microsoft Logistic Regression algorithm.</span></span>  
  
 [<span data-ttu-id="1dd84-136">予測計算 &#40;Excel 用のテーブル分析ツール&#41;</span><span class="sxs-lookup"><span data-stu-id="1dd84-136">Prediction Calculator &#40;Table Analysis Tools for Excel&#41;</span></span>](prediction-calculator-table-analysis-tools-for-excel.md)  
 <span data-ttu-id="1dd84-137">このツールは、目標となる結果につながる要因を分析するモデルを作成し、データから派生したスコア ルールに基づいて新しい入力の結果を予測します。</span><span class="sxs-lookup"><span data-stu-id="1dd84-137">This tool creates a model that analyzes the factors leading to the target outcome, and then predicts a result for any new inputs, based on scoring rules derived from the data.</span></span> <span data-ttu-id="1dd84-138">また、このツールは、新しい入力のスコアを簡単に記録できる対話的な意思決定ワークシートも生成します。</span><span class="sxs-lookup"><span data-stu-id="1dd84-138">This tool also generates an interactive decision-making worksheet that lets you easily score new inputs.</span></span> <span data-ttu-id="1dd84-139">ユーザーは、オフラインで使用できるスコアリング ワークシートの印刷バージョンを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="1dd84-139">You can also create a printed version of the scoring worksheet for offline use.</span></span>  
  
 <span data-ttu-id="1dd84-140">**予測計算**ツールでは、Microsoft ロジスティック回帰アルゴリズムが使用されます。</span><span class="sxs-lookup"><span data-stu-id="1dd84-140">The **Prediction Calculator** tool uses the Microsoft Logistic Regression algorithm.</span></span>  
  
 [<span data-ttu-id="1dd84-141">買い物かご分析 &#40;テーブル AnalysisTools for Excel&#41;</span><span class="sxs-lookup"><span data-stu-id="1dd84-141">Shopping Basket Analysis &#40;Table AnalysisTools for Excel&#41;</span></span>](shopping-basket-analysis-table-analysistools-for-excel.md)  
 <span data-ttu-id="1dd84-142">このツールは、クロスセルやアップセルで使用できるパターンを特定します。</span><span class="sxs-lookup"><span data-stu-id="1dd84-142">This tool identifies patterns that can be used in cross-selling or up-selling.</span></span> <span data-ttu-id="1dd84-143">同時に購入される頻度が高い製品グループを特定し、関連製品バンドルの価格およびコストに基づいてレポートも生成して、意思決定を支援します。</span><span class="sxs-lookup"><span data-stu-id="1dd84-143">It identifies groups of products that are frequently purchased together, and also generates reports based on the price and cost of related product bundles, to aid in decision-making.</span></span>  
  
 <span data-ttu-id="1dd84-144">ツールの機能は、マーケット バスケット分析に限られません。アソシエーション分析に向いているすべての問題に対して適用できます。</span><span class="sxs-lookup"><span data-stu-id="1dd84-144">The tool is not limited to market basket analysis; you can apply it to any problem that lends itself to association analysis.</span></span> <span data-ttu-id="1dd84-145">たとえば、頻繁に同時発生するイベント、診断につながる要因、またはその他の考えられる原因と結果のセットを探すこともできます。</span><span class="sxs-lookup"><span data-stu-id="1dd84-145">For example, you might look for events that frequently occur together, factors leading to a diagnosis, or any other set of potential causes and outcomes.</span></span>  
  
 <span data-ttu-id="1dd84-146">**買い物かご分析**ツールでは、Microsoft アソシエーションアルゴリズムが使用されます。</span><span class="sxs-lookup"><span data-stu-id="1dd84-146">The **Shopping Basket Analysis** tool uses the Microsoft Association algorithm.</span></span>  
  
## <a name="requirements-for-the-table-analysis-tools-for-excel"></a><span data-ttu-id="1dd84-147">Excel 用のテーブル分析ツールの要件</span><span class="sxs-lookup"><span data-stu-id="1dd84-147">Requirements for the Table Analysis Tools for Excel</span></span>  
 <span data-ttu-id="1dd84-148">Excel 用のテーブル分析ツールを使用するには、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] インスタンスへの接続を作成しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="1dd84-148">To use the Table Analysis Tools for Excel, you must first create a connection to an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="1dd84-149">データの分析に使用される Microsoft データ マイニング アルゴリズムには、この接続を介してアクセスします。</span><span class="sxs-lookup"><span data-stu-id="1dd84-149">This connection gives you access to the Microsoft data mining algorithms that are used to analyze your data.</span></span> <span data-ttu-id="1dd84-150">インスタンスにアクセスできない場合、データ マイニングを試すときに使用できるインスタンスを設定するよう管理者に依頼することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="1dd84-150">If you do not have access to an instance, we recommend that you ask your administrator to set up an instance that you can use for experimenting with data mining.</span></span> <span data-ttu-id="1dd84-151">詳細については、「 [Connect To Source data &#40;Excel 用データマイニングクライアント&#41;](connect-to-source-data-data-mining-client-for-excel.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1dd84-151">For more information, see [Connect to Source Data &#40;Data Mining Client for Excel&#41;](connect-to-source-data-data-mining-client-for-excel.md).</span></span>  
  
 <span data-ttu-id="1dd84-152">テーブル分析ツールでデータを操作するには、使用する一連のデータを Excel テーブルに変換する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1dd84-152">To work with data using the Table Analysis Tools, you must convert the range of data you want to use to Excel tables.</span></span>  
  
 <span data-ttu-id="1dd84-153">[**分析**] リボンが表示されない場合は、まずデータテーブル内をクリックしてください。</span><span class="sxs-lookup"><span data-stu-id="1dd84-153">If you cannot see the **Analyze** ribbon, try clicking inside a data table first.</span></span> <span data-ttu-id="1dd84-154">メニューは、データ テーブルを選択するまでアクティブになりません。</span><span class="sxs-lookup"><span data-stu-id="1dd84-154">The menu is not activated until a data table is selected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1dd84-155">参照</span><span class="sxs-lookup"><span data-stu-id="1dd84-155">See Also</span></span>  
 <span data-ttu-id="1dd84-156">[Excel 用のデータマイニングクライアント &#40;SQL Server データマイニングアドイン&#41;](data-mining-client-for-excel-sql-server-data-mining-add-ins.md) </span><span class="sxs-lookup"><span data-stu-id="1dd84-156">[Data Mining Client for Excel &#40;SQL Server Data Mining Add-ins&#41;](data-mining-client-for-excel-sql-server-data-mining-add-ins.md) </span></span>  
 <span data-ttu-id="1dd84-157">[データマイニングアドインの &#40;SQL Server Visio データマイニングダイアグラムのトラブルシューティング&#41;](troubleshooting-visio-data-mining-diagrams-sql-server-data-mining-add-ins.md) </span><span class="sxs-lookup"><span data-stu-id="1dd84-157">[Troubleshooting Visio Data Mining Diagrams &#40;SQL Server Data Mining Add-ins&#41;](troubleshooting-visio-data-mining-diagrams-sql-server-data-mining-add-ins.md) </span></span>  
 [<span data-ttu-id="1dd84-158">Office 用データ マイニング アドインの内容</span><span class="sxs-lookup"><span data-stu-id="1dd84-158">What's Included in the Data Mining Add-Ins for Office</span></span>](what-s-included-in-the-data-mining-add-ins-for-office.md)  
  
  
