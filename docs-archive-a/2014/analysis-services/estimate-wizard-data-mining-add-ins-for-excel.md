---
title: 推定ウィザード (Excel 用データマイニングアドイン) |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data modeling [data mining]
- estimation
ms.assetid: 7f2b1d5f-c9b3-4939-b35a-34ae099af15f
author: minewiskan
ms.author: owend
ms.openlocfilehash: ace9fa3a62690061677312d4f7dbb6b8a1d0ea5a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718879"
---
# <a name="estimate-wizard-data-mining-add-ins-for-excel"></a><span data-ttu-id="603a1-102">推定ウィザード (Excel 用データ マイニング アドイン)</span><span class="sxs-lookup"><span data-stu-id="603a1-102">Estimate Wizard (Data Mining Add-ins for Excel)</span></span>
  <span data-ttu-id="603a1-103">![[データ マイニング] リボンの推定ウィザード](media/dmc-estimate.gif "[データ マイニング] リボンの推定ウィザード")</span><span class="sxs-lookup"><span data-stu-id="603a1-103">![Estimate wizard in Data Mining ribbon](media/dmc-estimate.gif "Estimate wizard in Data Mining ribbon")</span></span>  
  
 <span data-ttu-id="603a1-104">**推定**ウィザードを使用すると、推定モデルを作成できます。</span><span class="sxs-lookup"><span data-stu-id="603a1-104">The **Estimate** wizard helps you create an estimation model.</span></span> <span data-ttu-id="603a1-105">推定モデルは、データからパターンを抽出し、そのパターンを使用して結果に影響を与える要因を予測します。</span><span class="sxs-lookup"><span data-stu-id="603a1-105">An estimation model extracts patterns from data and uses the patterns to predict the factors that affect outcomes.</span></span>  
  
 <span data-ttu-id="603a1-106">推定は数値の結果を予測するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="603a1-106">Estimation is used for predicting numeric outcomes.</span></span> <span data-ttu-id="603a1-107">たとえば、教育機関の卒業率をパーセンテージで表した値が対象列に格納されている場合、教育機関ごとの生徒数、生徒と教員の比率、教員数など、卒業率の増減に関係する可能性がある要因を分析できます。</span><span class="sxs-lookup"><span data-stu-id="603a1-107">For example, if your target column contains graduation rates for schools, with graduation rates expressed as percentages, you could analyze factors that potentially increase or decrease graduation rates, such as the number of students per school, the student-teacher ratio, and the number of teachers.</span></span>  
  
## <a name="using-the-estimate-data-wizard"></a><span data-ttu-id="603a1-108">データ推定ウィザードの使用</span><span class="sxs-lookup"><span data-stu-id="603a1-108">Using the Estimate Data Wizard</span></span>  
  
1.  <span data-ttu-id="603a1-109">[**データマイニング**] リボンで、[**推定**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="603a1-109">On the **Data Mining** ribbon, click **Estimate**.</span></span>  
  
2.  <span data-ttu-id="603a1-110">**[ソースデータの選択**] ダイアログボックスで、使用するソースデータを選択します。</span><span class="sxs-lookup"><span data-stu-id="603a1-110">In the **Select Source Data** dialog box, select the source data to use.</span></span> <span data-ttu-id="603a1-111">Excel**テーブル**、Excel**データ範囲**、または**外部データソース**のデータを使用できます。</span><span class="sxs-lookup"><span data-stu-id="603a1-111">You can use data in an Excel **Table**, an Excel **Data Range**, or from an **External data source**.</span></span>  
  
     <span data-ttu-id="603a1-112">外部データ ソースを使用する場合、カスタム ビューまたはカスタム クエリを作成し、それを [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データ ソースとして保存できます。</span><span class="sxs-lookup"><span data-stu-id="603a1-112">If you use an external data source, you can create custom views or queries and save them as an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] data source.</span></span>  
  
3.  <span data-ttu-id="603a1-113">[**推定**] ダイアログボックスで、**分析する列**を選択します。</span><span class="sxs-lookup"><span data-stu-id="603a1-113">In the **Estimation** dialog box, select the **Column to analyze**.</span></span>  
  
     <span data-ttu-id="603a1-114">対象列には、連続する数値データが格納されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="603a1-114">The target column must contain continuous numeric data.</span></span>  
  
4.  <span data-ttu-id="603a1-115">[**入力列**] チェックボックスをオンにして、入力として使用する列を選択します。</span><span class="sxs-lookup"><span data-stu-id="603a1-115">Select columns to use as input by checking the **Input columns** checkbox.</span></span>  
  
     <span data-ttu-id="603a1-116">選択した列は、パターンの作成に使用されます。</span><span class="sxs-lookup"><span data-stu-id="603a1-116">These columns will be used to create the patterns.</span></span> <span data-ttu-id="603a1-117">分析には不要と思われる ID 番号などの列や、分析とは無関係なデータを含んだ列は、除外する必要があります。</span><span class="sxs-lookup"><span data-stu-id="603a1-117">You should eliminate from analysis any columns that are not likely to help, such as ID numbers, or columns that contain irrelevant data.</span></span>  
  
5.  <span data-ttu-id="603a1-118">**推定**ウィザードでは、データセットに最適なアルゴリズムが選択されます。</span><span class="sxs-lookup"><span data-stu-id="603a1-118">The **Estimate** wizard selects the optimum algorithm for your data set.</span></span> <span data-ttu-id="603a1-119">ただし、[**パラメーター** ] をクリックして [**アルゴリズムパラメーター** ] ダイアログボックスを開き、詳細オプションを設定することができます。</span><span class="sxs-lookup"><span data-stu-id="603a1-119">However, you can click **Parameters** to open the **Algorithm Parameters** dialog box and set advanced options.</span></span>  
  
6.  <span data-ttu-id="603a1-120">データが数値であり、Microsoft 線形回帰方式を使用できる場合、予測可能な値と関連付けられていることがわかっている (または非常に疑わしい) 数値列について、[**リグレッサー** ] ボックスをオンにすることができます。</span><span class="sxs-lookup"><span data-stu-id="603a1-120">If your data is numeric and you can use the Microsoft Linear Regression method, you can check the **Regressor** box for any numeric columns that you know (or strongly suspect) to be correlated with the predictable value.</span></span>  
  
     <span data-ttu-id="603a1-121">そうすると、アルゴリズムによって、その列の値がテストされ、値が出力に影響するかどうかが判断されます。</span><span class="sxs-lookup"><span data-stu-id="603a1-121">The algorithm will then test the values in that column to determine if they affect the outcomes.</span></span> <span data-ttu-id="603a1-122">わからない場合は、[**提案**] をクリックすると、アルゴリズムによってすべての列がテストされ、リグレッサーとして使用する最適な値が自動的に検出されます。</span><span class="sxs-lookup"><span data-stu-id="603a1-122">If you are unsure, click **Suggest** and the algorithm will test all column and automatically detect the best values to use as regressors.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="603a1-123">推定を作成するにはリグレッサーが必要です。</span><span class="sxs-lookup"><span data-stu-id="603a1-123">A regressor is required to create an estimate.</span></span> <span data-ttu-id="603a1-124">ウィザードでは、データに対する最初のパスに基づいて、常に最適なリグレッサーが提示されます。</span><span class="sxs-lookup"><span data-stu-id="603a1-124">The wizard always recommends the best regressor, based on an initial pass over the data.</span></span> <span data-ttu-id="603a1-125">このため、どれを選択すればよいかわからない場合は、推奨された選択内容を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="603a1-125">Therefore, if you are not sure, it is best to accept the recommended selections.</span></span>  
  
7.  <span data-ttu-id="603a1-126">[**データをトレーニングセットとテストセットに分割**] ページで、テスト用にデータの小さなサブセットを作成するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="603a1-126">On the **Split data into training and testing sets** page, specify whether you want to create a small subset of the data for testing.</span></span>  
  
8.  <span data-ttu-id="603a1-127">[**完了**] ページで、新しいマイニング構造とマイニングモードの名前を指定するか、既定の名前をそのまま使用します。</span><span class="sxs-lookup"><span data-stu-id="603a1-127">On the **Finish** page, provide names for the new mining structure and mining mode, or accept the default names that are provided.</span></span>  
  
9. <span data-ttu-id="603a1-128">モデルを使用するためのオプションを設定します。</span><span class="sxs-lookup"><span data-stu-id="603a1-128">Set options for using the model.</span></span>  
  
    -   <span data-ttu-id="603a1-129">[**参照**] を選択して、すぐにビューアーでモデルを開きます。</span><span class="sxs-lookup"><span data-stu-id="603a1-129">Select **Browse** to immediately open the model in a viewer.</span></span>  
  
         <span data-ttu-id="603a1-130">このグラフィカルなビューアーには、依存関係ネットワーク グラフやアルゴリズムによって生成されたデジション ツリーなどが表示されます。</span><span class="sxs-lookup"><span data-stu-id="603a1-130">This graphical viewer displays a dependency network graph and the decision tree generated by the algorithm.</span></span> <span data-ttu-id="603a1-131">この情報を調査することで、推測値をもたらした要因をより深く理解できます。</span><span class="sxs-lookup"><span data-stu-id="603a1-131">By exploring this information, you can better understand the factors that contribute to the estimated values.</span></span>  
  
    -   <span data-ttu-id="603a1-132">分析のユーザーが基になるデータを表示できるようにするには、[**ドリルスルーを有効**にする] を選択します。</span><span class="sxs-lookup"><span data-stu-id="603a1-132">Select **Enable drillthrough** to let users of your analysis view the underlying data.</span></span>  
  
         <span data-ttu-id="603a1-133">このオプションを使用できるのは、デシジョン ツリー アルゴリズムまたは線形回帰アルゴリズムを使用する場合だけです。</span><span class="sxs-lookup"><span data-stu-id="603a1-133">This option is available only if you use the Decision Trees opr Linear Regression algorithms.</span></span>  
  
    -   <span data-ttu-id="603a1-134">**一時的なモデルを使用**します。</span><span class="sxs-lookup"><span data-stu-id="603a1-134">**Use temporary model**.</span></span> <span data-ttu-id="603a1-135">このチェック ボックスをオンにすると、モデルがサーバーに保存されません。</span><span class="sxs-lookup"><span data-stu-id="603a1-135">If you select this option, the model will not be saved to the server.</span></span> <span data-ttu-id="603a1-136">一時的なモデルは、Excel の終了時に削除されます。</span><span class="sxs-lookup"><span data-stu-id="603a1-136">Temporary models are deleted when you close Excel.</span></span>  
  
## <a name="more-about-estimation-models"></a><span data-ttu-id="603a1-137">推定モデルの詳細</span><span class="sxs-lookup"><span data-stu-id="603a1-137">More About Estimation Models</span></span>  
 <span data-ttu-id="603a1-138">**推定**ウィザードでは、次のいずれかのアルゴリズムの使用がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="603a1-138">The **Estimate** wizard supports the use of any of the following algorithms:</span></span>  
  
-   <span data-ttu-id="603a1-139">Microsoft デシジョンツリーアルゴリズム</span><span class="sxs-lookup"><span data-stu-id="603a1-139">Microsoft Decision Tree algorithm</span></span>  
  
-   <span data-ttu-id="603a1-140">Microsoft 線形回帰アルゴリズム</span><span class="sxs-lookup"><span data-stu-id="603a1-140">Microsoft Linear Regression algorithm</span></span>  
  
-   <span data-ttu-id="603a1-141">Microsoft ロジスティック回帰アルゴリズム</span><span class="sxs-lookup"><span data-stu-id="603a1-141">Microsoft Logistic Regression algorithm</span></span>  
  
-   <span data-ttu-id="603a1-142">Microsoft ニューラルネットワークアルゴリズム</span><span class="sxs-lookup"><span data-stu-id="603a1-142">Microsoft Neural network algorithm</span></span>  
  
 <span data-ttu-id="603a1-143">[**アルゴリズムパラメーター** ] ダイアログボックスでは、選択したアルゴリズムに応じて、追加の詳細オプションを設定できます。</span><span class="sxs-lookup"><span data-stu-id="603a1-143">In the **Algorithm Parameters** dialog box, you can set additional advanced options, depending on which algorithm you chose.</span></span> <span data-ttu-id="603a1-144">各アルゴリズムのオプションの詳細については、SQL Server オンライン ブックの次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="603a1-144">For information on the options for each algorithm see these topics in SQL Server Books Online:</span></span>  
  
 [<span data-ttu-id="603a1-145">Microsoft デシジョン ツリー アルゴリズム テクニカル リファレンス</span><span class="sxs-lookup"><span data-stu-id="603a1-145">Microsoft Decision Trees Algorithm Technical Reference</span></span>](data-mining/microsoft-decision-trees-algorithm-technical-reference.md)  
  
 [<span data-ttu-id="603a1-146">Microsoft 線形回帰アルゴリズム テクニカル リファレンス</span><span class="sxs-lookup"><span data-stu-id="603a1-146">Microsoft Linear Regression Algorithm Technical Reference</span></span>](data-mining/microsoft-linear-regression-algorithm-technical-reference.md)  
  
 [<span data-ttu-id="603a1-147">Microsoft ロジスティック回帰アルゴリズム テクニカル リファレンス</span><span class="sxs-lookup"><span data-stu-id="603a1-147">Microsoft Logistic Regression Algorithm Technical Reference</span></span>](data-mining/microsoft-logistic-regression-algorithm-technical-reference.md)  
  
 [<span data-ttu-id="603a1-148">Microsoft Neural Network Algorithm Technical Reference</span><span class="sxs-lookup"><span data-stu-id="603a1-148">Microsoft Neural Network Algorithm Technical Reference</span></span>](data-mining/microsoft-neural-network-algorithm-technical-reference.md)  
  
### <a name="requirements"></a><span data-ttu-id="603a1-149">要件</span><span class="sxs-lookup"><span data-stu-id="603a1-149">Requirements</span></span>  
 <span data-ttu-id="603a1-150">データ推定ウィザードを使用するには、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベースに接続する必要があります。</span><span class="sxs-lookup"><span data-stu-id="603a1-150">To use the Estimate Data Wizard, you must be connected to a [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.</span></span>  
  
 <span data-ttu-id="603a1-151">接続を作成する方法の詳細については、「 [Connect To Source data &#40;Excel 用データマイニングクライアント&#41;](connect-to-source-data-data-mining-client-for-excel.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="603a1-151">For information about how to create a connection, see [Connect to Source Data &#40;Data Mining Client for Excel&#41;](connect-to-source-data-data-mining-client-for-excel.md).</span></span>  
  
 <span data-ttu-id="603a1-152">推定アルゴリズムを使用するには、予測しようとしている結果を、通貨、売上高、日付、時刻などの数値で表す必要があります。</span><span class="sxs-lookup"><span data-stu-id="603a1-152">To use the estimation algorithm, the outcome that you are trying to predict must be expressed as a numeric value, such as a currency, sales amount, date, or time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="603a1-153">参照</span><span class="sxs-lookup"><span data-stu-id="603a1-153">See Also</span></span>  
 <span data-ttu-id="603a1-154">[データマイニングモデルの作成](creating-a-data-mining-model.md) </span><span class="sxs-lookup"><span data-stu-id="603a1-154">[Creating a Data Mining Model](creating-a-data-mining-model.md) </span></span>  
 [<span data-ttu-id="603a1-155">デシジョンツリーダイアグラムのチュートリアル &#40;データマイニングアドイン&#41;</span><span class="sxs-lookup"><span data-stu-id="603a1-155">Decision Tree Diagram Walkthrough  &#40;Data Mining Add-ins&#41;</span></span>](decision-tree-diagram-walkthrough-data-mining-add-ins.md)  
  
  
