---
title: 分類ウィザード (Excel 用データマイニングアドイン) |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data modeling [data mining]
- classification [data mining]
ms.assetid: 409c5076-c4c3-4f09-8f30-d3297df45f13
author: minewiskan
ms.author: owend
ms.openlocfilehash: b82fc98df10ae2e6754a378dacea108f9f3379ca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633528"
---
# <a name="classify-wizard-data-mining-add-ins-for-excel"></a><span data-ttu-id="f0aea-102">分類ウィザード (Excel 用データ マイニング アドイン)</span><span class="sxs-lookup"><span data-stu-id="f0aea-102">Classify Wizard (Data Mining Add-ins for Excel)</span></span>
  <span data-ttu-id="f0aea-103">![[データ マイニング] リボンの分類ウィザード](media/dmc-classify.gif "[データ マイニング] リボンの分類ウィザード")</span><span class="sxs-lookup"><span data-stu-id="f0aea-103">![Classify wizard in Data Mining ribbon](media/dmc-classify.gif "Classify wizard in Data Mining ribbon")</span></span>  
  
 <span data-ttu-id="f0aea-104">**分類**ウィザードを使用すると、excel テーブル、excel 範囲、または外部データソースの既存のデータに基づいて分類モデルを作成できます。</span><span class="sxs-lookup"><span data-stu-id="f0aea-104">The **Classify** wizard helps you build a classification model based on existing data in an Excel table, an Excel range, or an external data source.</span></span>  
  
 <span data-ttu-id="f0aea-105">分類モデルはデータから共通のパターンを抽出します。そのため、分類モデルを使用すると、グループ化された値に基づいて予測を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="f0aea-105">A classification model extracts patterns in your data that indicate similarities and helps you make predictions based on groupings of values.</span></span> <span data-ttu-id="f0aea-106">たとえば、分類モデルを使用して、収入パターンまたは支出パターンに基づくリスクを予測できます。</span><span class="sxs-lookup"><span data-stu-id="f0aea-106">For example, a classification model might be used to predict risk based on income or spending patterns.</span></span>  
  
## <a name="using-the-classify-wizard"></a><span data-ttu-id="f0aea-107">分類ウィザードの使用</span><span class="sxs-lookup"><span data-stu-id="f0aea-107">Using the Classify Wizard</span></span>  
  
1.  <span data-ttu-id="f0aea-108">[**データマイニング**] リボンで、[**分類**] をクリックし、[**次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f0aea-108">In the **Data Mining** ribbon, click **Classify**, and then click **Next**.</span></span>  
  
2.  <span data-ttu-id="f0aea-109">**[ソースデータの選択**] ページで、分析するデータを選択します。</span><span class="sxs-lookup"><span data-stu-id="f0aea-109">In the **Select Source Data** page, choose the data to analyze.</span></span>  
  
     <span data-ttu-id="f0aea-110">このウィザードは、複数の種類のデータ (Excel テーブル、Excel 範囲、および外部データ ソース) をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="f0aea-110">This wizard supports multiple kinds of data: Excel tables, Excel ranges, and external data sources.</span></span> <span data-ttu-id="f0aea-111">外部データを使用する場合、外部データを Excel に追加するか、Analysis Services データ ソース内の一連のテーブルまたはビューを選択することができます。</span><span class="sxs-lookup"><span data-stu-id="f0aea-111">With external data, you can either add it into Excel, or choose a set of tables or views in an Analysis Services data source.</span></span> <span data-ttu-id="f0aea-112">また、テーブルを追加したり列を変更したりして、アドホック データ ソースを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="f0aea-112">You can also add tables and change columns to create ad hoc data sources.</span></span>  
  
3.  <span data-ttu-id="f0aea-113">[**分類**] ページで、分類する列を選択します。</span><span class="sxs-lookup"><span data-stu-id="f0aea-113">On the **Classification** page, choose the column that you want to classify.</span></span>  
  
     <span data-ttu-id="f0aea-114">リスト内の列、**入力列**を確認し、一意の値を持つ列を選択解除し、ID 番号や顧客名などのパターンを作成するには役に立ちません。</span><span class="sxs-lookup"><span data-stu-id="f0aea-114">Review the columns in the list, **Input columns**, and deselect any columns that have unique values and thus aren't useful for creating patterns, such as ID numbers, customer names, and so on.</span></span> <span data-ttu-id="f0aea-115">また、実質的に分類可能な列と重複する列も削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f0aea-115">You should also remove columns that essentially duplicate the classifiable column.</span></span>  
  
     <span data-ttu-id="f0aea-116">たとえば、製品カテゴリの予測を分類する場合、既知のビジネス ルールがある場合はサブカテゴリ フィールドを除外する必要があります。そうしないと、そのルールの強度によって、他の相関関係を発見できなくなる場合があります。</span><span class="sxs-lookup"><span data-stu-id="f0aea-116">For example, if you are classifying predicting the category of a product, you should exclude the subcategory field if there is a known business rule, or else the strength of that rule might prevent you from discovering other correlations.</span></span>  
  
4.  <span data-ttu-id="f0aea-117">必要に応じて、[**パラメーター** ] をクリックして、アルゴリズムパラメーターを変更し、クラスターモデルの動作をカスタマイズします。</span><span class="sxs-lookup"><span data-stu-id="f0aea-117">Optionally, click **Parameters** to change the algorithm parameters and customize the behavior of the clustering model.</span></span>  
  
5.  <span data-ttu-id="f0aea-118">[**データをトレーニングセットとテストセットに分割**] ページで、テスト用に保持するデータの量を指定します。</span><span class="sxs-lookup"><span data-stu-id="f0aea-118">In the **Split data into training and testing sets** page, specify how much data to hold out for testing.</span></span> <span data-ttu-id="f0aea-119">残りのデータは、常にモデルのトレーニングに使用されます。</span><span class="sxs-lookup"><span data-stu-id="f0aea-119">The remainder is always used for training the model.</span></span>  
  
     <span data-ttu-id="f0aea-120">既定の設定では、30% がテスト データ、70% がトレーニング データです。</span><span class="sxs-lookup"><span data-stu-id="f0aea-120">The default setting is 30% testing data and 70% training data.</span></span>  
  
6.  <span data-ttu-id="f0aea-121">[**完了**] ページで、データセットとモデルのわかりやすい名前を指定し、完成したモデルの操作方法を制御する次のオプションを設定します。</span><span class="sxs-lookup"><span data-stu-id="f0aea-121">On the **Finish** page, provide a descriptive name for your data set and model, and set the following options that control how you work with the finished model:</span></span>  
  
    -   <span data-ttu-id="f0aea-122">**モデルを参照**します。</span><span class="sxs-lookup"><span data-stu-id="f0aea-122">**Browse model**.</span></span> <span data-ttu-id="f0aea-123">このオプションを選択すると、ウィザードがモデルの処理を終了するとすぐに、[**参照**] ウィンドウが開き、結果を調べることができます。</span><span class="sxs-lookup"><span data-stu-id="f0aea-123">When this option is selected, as soon as the wizard finishes processing the model, it opens a **Browse** window to help you explore the results.</span></span> <span data-ttu-id="f0aea-124">ビューアーの内容は、構築したモデルの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="f0aea-124">The contents of the viewer depend on the type of model you built.</span></span> <span data-ttu-id="f0aea-125">詳細については、「[デシジョンツリーモデルの参照](browsing-a-decision-trees-model.md)」および「[ニューラルネットワークモデルの参照](browsing-a-neural-network-model.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f0aea-125">For more information, see [Browsing a Decision Trees Model](browsing-a-decision-trees-model.md) and [Browsing a Neural Network Model](browsing-a-neural-network-model.md).</span></span>  
  
    -   <span data-ttu-id="f0aea-126">**ドリルスルーを有効に**します。</span><span class="sxs-lookup"><span data-stu-id="f0aea-126">**Enable drillthrough**.</span></span> <span data-ttu-id="f0aea-127">このチェック ボックスをオンにすると、完成したモデルから基になるデータを表示できます。</span><span class="sxs-lookup"><span data-stu-id="f0aea-127">Select this option to view the underlying data from the finished model.</span></span> <span data-ttu-id="f0aea-128">このオプションは、デシジョン ツリー モデルを構築する場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="f0aea-128">This option is only available if you build a Decision Tree model.</span></span>  
  
    -   <span data-ttu-id="f0aea-129">**一時的なモデルを使用**します。</span><span class="sxs-lookup"><span data-stu-id="f0aea-129">**Use temporary model**.</span></span> <span data-ttu-id="f0aea-130">このチェック ボックスをオンにすると、モデルがサーバーに保存されません。</span><span class="sxs-lookup"><span data-stu-id="f0aea-130">If you select this option, the model will not be saved to the server.</span></span> <span data-ttu-id="f0aea-131">一時的なモデルは、Excel の終了時に削除されます。</span><span class="sxs-lookup"><span data-stu-id="f0aea-131">Temporary models are deleted when you close Excel.</span></span>  
  
## <a name="more-about-classification-models"></a><span data-ttu-id="f0aea-132">分類モデルの詳細</span><span class="sxs-lookup"><span data-stu-id="f0aea-132">More About Classification Models</span></span>  
 <span data-ttu-id="f0aea-133">[**アルゴリズムパラメーター** ] ダイアログボックスでは、Analysis Services に用意されている次のアルゴリズムの中から分類方法を選択することもできます。</span><span class="sxs-lookup"><span data-stu-id="f0aea-133">In the **Algorithm Parameters** dialog box, you can also choose the classification method from among these algorithms provided in Analysis Services:</span></span>  
  
-   <span data-ttu-id="f0aea-134">Microsoft デシジョン ツリー</span><span class="sxs-lookup"><span data-stu-id="f0aea-134">Microsoft Decision Tree</span></span>  
  
-   <span data-ttu-id="f0aea-135">Microsoft ロジスティック回帰</span><span class="sxs-lookup"><span data-stu-id="f0aea-135">Microsoft Logistic Regression</span></span>  
  
-   <span data-ttu-id="f0aea-136">Microsoft Naïve Bayes</span><span class="sxs-lookup"><span data-stu-id="f0aea-136">Microsoft Naïve Bayes</span></span>  
  
-   <span data-ttu-id="f0aea-137">Microsoft ニューラル ネットワーク</span><span class="sxs-lookup"><span data-stu-id="f0aea-137">Microsoft Neural Network</span></span>  
  
 <span data-ttu-id="f0aea-138">複数のアルゴリズムで同様の結果が生じる場合がありますが、アルゴリズムによってデータの分析方法は異なるため、いくつかのアルゴリズムを試して結果を比較することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="f0aea-138">Although the algorithms might yield similar results, they analyze the data differently, so we recommend trying several algorithms and comparing the results.</span></span> <span data-ttu-id="f0aea-139">既定の方法は、Microsoft デシジョン ツリーです。</span><span class="sxs-lookup"><span data-stu-id="f0aea-139">The default method is Microsoft Decision Trees.</span></span>  
  
 <span data-ttu-id="f0aea-140">[**パラメーター** ] ボックスの一覧では、選択したアルゴリズムの種類に応じて、詳細設定オプションを変更できます。</span><span class="sxs-lookup"><span data-stu-id="f0aea-140">In the **Parameters** list, you can change advanced options, which depend on the type of algorithm you choose.</span></span> <span data-ttu-id="f0aea-141">各アルゴリズムのパラメーターについては、SQL Server オンライン ブックで詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="f0aea-141">The parameters for each algorithm are described in more detail in SQL Server Books Online.</span></span>  
  
 [<span data-ttu-id="f0aea-142">Microsoft デシジョン ツリー アルゴリズム テクニカル リファレンス</span><span class="sxs-lookup"><span data-stu-id="f0aea-142">Microsoft Decision Trees Algorithm Technical Reference</span></span>](data-mining/microsoft-decision-trees-algorithm-technical-reference.md)  
  
 [<span data-ttu-id="f0aea-143">Microsoft ロジスティック回帰アルゴリズム テクニカル リファレンス</span><span class="sxs-lookup"><span data-stu-id="f0aea-143">Microsoft Logistic Regression Algorithm Technical Reference</span></span>](data-mining/microsoft-logistic-regression-algorithm-technical-reference.md)  
  
 [<span data-ttu-id="f0aea-144">Microsoft Naive Bayes アルゴリズム テクニカル リファレンス</span><span class="sxs-lookup"><span data-stu-id="f0aea-144">Microsoft Naive Bayes Algorithm Technical Reference</span></span>](data-mining/microsoft-naive-bayes-algorithm-technical-reference.md)  
  
 [<span data-ttu-id="f0aea-145">Microsoft Neural Network Algorithm Technical Reference</span><span class="sxs-lookup"><span data-stu-id="f0aea-145">Microsoft Neural Network Algorithm Technical Reference</span></span>](data-mining/microsoft-neural-network-algorithm-technical-reference.md)  
  
### <a name="requirements"></a><span data-ttu-id="f0aea-146">必要条件</span><span class="sxs-lookup"><span data-stu-id="f0aea-146">Requirements</span></span>  
 <span data-ttu-id="f0aea-147">**分類**ウィザードを使用するには、データベースに接続している必要があり [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="f0aea-147">To use the **Classify** wizard, you must be connected to an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.</span></span> <span data-ttu-id="f0aea-148">接続を作成する方法の詳細については、「 [Connect To Source data &#40;Excel 用データマイニングクライアント&#41;](connect-to-source-data-data-mining-client-for-excel.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f0aea-148">For information about how to create a connection, see [Connect to Source Data &#40;Data Mining Client for Excel&#41;](connect-to-source-data-data-mining-client-for-excel.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0aea-149">参照</span><span class="sxs-lookup"><span data-stu-id="f0aea-149">See Also</span></span>  
 [<span data-ttu-id="f0aea-150">データ マイニング モデルの作成</span><span class="sxs-lookup"><span data-stu-id="f0aea-150">Creating a Data Mining Model</span></span>](creating-a-data-mining-model.md)  
  
  
