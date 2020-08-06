---
title: クラスターウィザード (Excel 用データマイニングアドイン) |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- clustering [data mining]
ms.assetid: 85b25625-a7ab-4960-9f9c-df22e8ecae37
author: minewiskan
ms.author: owend
ms.openlocfilehash: 90500ae627bcafd1ca5ce17114dac9df9939691d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634144"
---
# <a name="cluster-wizard-data-mining-add-ins-for-excel"></a><span data-ttu-id="133dd-102">クラスター ウィザード (Excel 用データ マイニング アドイン)</span><span class="sxs-lookup"><span data-stu-id="133dd-102">Cluster Wizard (Data Mining Add-ins for Excel)</span></span>
  <span data-ttu-id="133dd-103">![[データ マイニング] リボンのクラスター ウィザード](media/dmc-cluster.gif "[データ マイニング] リボンのクラスター ウィザード")</span><span class="sxs-lookup"><span data-stu-id="133dd-103">![Cluster wizard in Data Mining ribbon](media/dmc-cluster.gif "Cluster wizard in Data Mining ribbon")</span></span>  
  
 <span data-ttu-id="133dd-104">クラスター ウィザードでは、似た特性を共有する行を検出し、それらをグループ化してグループ間の距離を最大化するモデルを構築できます。</span><span class="sxs-lookup"><span data-stu-id="133dd-104">The Cluster wizard helps you build a model that detects rows that share similar characteristics and groups them to maximize the distance between groups.</span></span> <span data-ttu-id="133dd-105">このウィザードは、あらゆる種類のデータのパターンを検索する場合に有用です。</span><span class="sxs-lookup"><span data-stu-id="133dd-105">This wizard is useful for finding patterns in all kinds of data.</span></span>  
  
 <span data-ttu-id="133dd-106">クラスター ウィザードは、Microsoft クラスタリング アルゴリズムを使用しており、広範なカスタマイズが可能です。</span><span class="sxs-lookup"><span data-stu-id="133dd-106">The Cluster wizard uses the Microsoft Clustering algorithm and can be extensively customized.</span></span> <span data-ttu-id="133dd-107">このウィザードは、Excel テーブル、Excel 範囲、または [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] クエリからの既存のデータで動作します。</span><span class="sxs-lookup"><span data-stu-id="133dd-107">It works on existing data from an Excel table, an Excel range, or an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] query.</span></span> <span data-ttu-id="133dd-108">同様の機能は、Excel 用のテーブル分析ツールに用意されている[カテゴリの検出](detect-categories-table-analysis-tools-for-excel.md)ツールによって提供されます。</span><span class="sxs-lookup"><span data-stu-id="133dd-108">Similar functionality is provided by the [Detect Categories](detect-categories-table-analysis-tools-for-excel.md) tool, provided in the Table Analysis Tools for Excel.</span></span> <span data-ttu-id="133dd-109">ただし、カテゴリの検出ツールはカスタマイズできないため、Excel テーブルのデータを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="133dd-109">However, the Detect Categories tool cannot be customized and must use data in Excel tables.</span></span>  
  
## <a name="using-the-cluster-wizard"></a><span data-ttu-id="133dd-110">クラスター ウィザードの使用</span><span class="sxs-lookup"><span data-stu-id="133dd-110">Using the Cluster Wizard</span></span>  
  
1.  <span data-ttu-id="133dd-111">[データマイニング] リボンで、[**クラスター**] をクリックし、[**次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="133dd-111">In the Data Mining ribbon, click **Cluster**, and then click **Next**.</span></span>  
  
2.  <span data-ttu-id="133dd-112">**[ソースデータの選択**] ページで、Excel のテーブルまたは範囲を選択します。</span><span class="sxs-lookup"><span data-stu-id="133dd-112">In the **Select Source Data** page, select an Excel table or range.</span></span> <span data-ttu-id="133dd-113">または、外部データ ソースを指定します。</span><span class="sxs-lookup"><span data-stu-id="133dd-113">Or specify and external data source.</span></span>  
  
     <span data-ttu-id="133dd-114">外部データ ソースを使用する場合、カスタム ビューを作成するかカスタム クエリ テキストを貼り付けて、データ セットを [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データ ソースとして保存できます。</span><span class="sxs-lookup"><span data-stu-id="133dd-114">If you use an external data source, you can create custom views or paste in custom query text, and save the data set as an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] data source.</span></span>  
  
3.  <span data-ttu-id="133dd-115">[**クラスタリング**] ページでは、モデルの構築方法をカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="133dd-115">On the **Clustering** page, you can customize the way the model is built.</span></span>  
  
    -   <span data-ttu-id="133dd-116">**セグメント**数については、ウィザードで固定数のカテゴリを作成したり、最適なグループ数を自動的に検出したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="133dd-116">For **Number of segments**, you can tell the wizard to create a fixed number of categories, or let it automatically detect the optimum number of groupings.</span></span>  
  
    -   <span data-ttu-id="133dd-117">[**入力列**] ボックスの一覧で列の一覧を確認し、パターンの作成に役立たない列を選択解除します。</span><span class="sxs-lookup"><span data-stu-id="133dd-117">Review the list of columns in the **Input columns** list, and deselect any columns that are not useful in creating patterns.</span></span> <span data-ttu-id="133dd-118">除外する必要のある列には、ID 番号や顧客名などがあります。</span><span class="sxs-lookup"><span data-stu-id="133dd-118">Columns you should exclude include ID numbers, customer names, and so on.</span></span>  
  
4.  <span data-ttu-id="133dd-119">必要に応じて、[**パラメーター** ] をクリックして、アルゴリズムパラメーターを変更し、クラスターモデルの動作をカスタマイズします。</span><span class="sxs-lookup"><span data-stu-id="133dd-119">Optionally, click **Parameters** to change the algorithm parameters and customize the behavior of the clustering model.</span></span>  
  
5.  <span data-ttu-id="133dd-120">[**データをトレーニングセットとテストセットに分割**] ページで、テスト用に保持するデータの量を指定します。</span><span class="sxs-lookup"><span data-stu-id="133dd-120">In the **Split data into training and testing sets** page, specify how much data to hold out for testing.</span></span> <span data-ttu-id="133dd-121">残りのデータは、常にモデルのトレーニングに使用されます。</span><span class="sxs-lookup"><span data-stu-id="133dd-121">The remainder is always used for training the model.</span></span>  
  
     <span data-ttu-id="133dd-122">既定の設定では、30% がテスト データ、70% がトレーニング データです。</span><span class="sxs-lookup"><span data-stu-id="133dd-122">The default setting is 30% testing data and 70% training data.</span></span>  
  
6.  <span data-ttu-id="133dd-123">[**完了**] ページで、データセットとモデルのわかりやすい名前を指定し、完成したモデルの操作方法を制御する次のオプションを設定します。</span><span class="sxs-lookup"><span data-stu-id="133dd-123">On the **Finish** page, provide a descriptive name for your data set and model, and set the following options that control how you work with the finished model:</span></span>  
  
    -   <span data-ttu-id="133dd-124">**モデルを参照**します。</span><span class="sxs-lookup"><span data-stu-id="133dd-124">**Browse model**.</span></span> <span data-ttu-id="133dd-125">このオプションを選択すると、ウィザードがモデルの処理を終了するとすぐに、[**参照**] ウィンドウが開き、結果を調べることができます。</span><span class="sxs-lookup"><span data-stu-id="133dd-125">When this option is selected, as soon as the wizard finishes processing the model, it opens a **Browse** window to help you explore the results.</span></span> <span data-ttu-id="133dd-126">ビューアーの内容は、構築したモデルの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="133dd-126">The contents of the viewer depend on the type of model you built.</span></span> <span data-ttu-id="133dd-127">詳細については、「[クラスターモデルの参照](browsing-a-clustering-model.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="133dd-127">For more information, see [Browsing a Clustering Model](browsing-a-clustering-model.md).</span></span>  
  
    -   <span data-ttu-id="133dd-128">**ドリルスルーを有効に**します。</span><span class="sxs-lookup"><span data-stu-id="133dd-128">**Enable drillthrough**.</span></span> <span data-ttu-id="133dd-129">このチェック ボックスをオンにすると、完成したモデルから基になるデータを表示できます。</span><span class="sxs-lookup"><span data-stu-id="133dd-129">Select this option to view the underlying data from the finished model.</span></span> <span data-ttu-id="133dd-130">このオプションは、デシジョン ツリー モデルを構築する場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="133dd-130">This option is only available if you build a Decision Tree model.</span></span>  
  
    -   <span data-ttu-id="133dd-131">**一時的なモデルを使用**します。</span><span class="sxs-lookup"><span data-stu-id="133dd-131">**Use temporary model**.</span></span> <span data-ttu-id="133dd-132">このチェック ボックスをオンにすると、モデルがサーバーに保存されません。</span><span class="sxs-lookup"><span data-stu-id="133dd-132">If you select this option, the model will not be saved to the server.</span></span> <span data-ttu-id="133dd-133">一時的なモデルは、Excel の終了時に削除されます。</span><span class="sxs-lookup"><span data-stu-id="133dd-133">Temporary models are deleted when you close Excel.</span></span>  
  
## <a name="more-about-clustering-models"></a><span data-ttu-id="133dd-134">クラスターモデルの詳細</span><span class="sxs-lookup"><span data-stu-id="133dd-134">More about Clustering Models</span></span>  
 <span data-ttu-id="133dd-135">このウィザードで使用するクラスタリングアルゴリズムを変更するには、[**詳細設定**] をクリックし、[**アルゴリズムパラメーター** ] ダイアログボックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="133dd-135">You can change the clustering algorithm used by this wizard by clicking **Advanced** and using the **Algorithm Parameters** dialog box.</span></span>  
  
 <span data-ttu-id="133dd-136">Microsoft クラスタリング アルゴリズムには、次のクラスタリング手法が用意されています。</span><span class="sxs-lookup"><span data-stu-id="133dd-136">The Microsoft Clustering algorithm provides these clustering methods:</span></span>  
  
-   <span data-ttu-id="133dd-137">K-Means - スケーラブルまたは非スケーリング。</span><span class="sxs-lookup"><span data-stu-id="133dd-137">K-means -  scalable or non-scaling.</span></span>  
  
-   <span data-ttu-id="133dd-138">Expectation Maximization (EM) - スケーラブルまたは非スケーリング。</span><span class="sxs-lookup"><span data-stu-id="133dd-138">Expectation Maximization (EM) - scalable or non-scaling.</span></span>  
  
 <span data-ttu-id="133dd-139">また、CLUSTER_SEED パラメーターを使用して開始値を制御し、同じデータ セットを使用して繰り返されるモデルは常に同じ結果になるようにできます。</span><span class="sxs-lookup"><span data-stu-id="133dd-139">You can also use the CLUSTER_SEED parameter to control the starting value and ensure that repeated models using the same data set have the same results.</span></span>  
  
### <a name="requirements"></a><span data-ttu-id="133dd-140">必要条件</span><span class="sxs-lookup"><span data-stu-id="133dd-140">Requirements</span></span>  
 <span data-ttu-id="133dd-141">クラスター ウィザードを使用するには、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベースに接続する必要があります。</span><span class="sxs-lookup"><span data-stu-id="133dd-141">To use the Cluster wizard, you must be connected to a [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.</span></span> <span data-ttu-id="133dd-142">詳細については、「 [Connect To Source data &#40;Excel 用データマイニングクライアント&#41;](connect-to-source-data-data-mining-client-for-excel.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="133dd-142">For more information, see [Connect to Source Data &#40;Data Mining Client for Excel&#41;](connect-to-source-data-data-mining-client-for-excel.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="133dd-143">参照</span><span class="sxs-lookup"><span data-stu-id="133dd-143">See Also</span></span>  
 <span data-ttu-id="133dd-144">[データマイニングモデルの作成](creating-a-data-mining-model.md) </span><span class="sxs-lookup"><span data-stu-id="133dd-144">[Creating a Data Mining Model](creating-a-data-mining-model.md) </span></span>  
 [<span data-ttu-id="133dd-145">Excel 用のテーブル分析ツール &#40;のカテゴリの検出&#41;</span><span class="sxs-lookup"><span data-stu-id="133dd-145">Detect Categories &#40;Table Analysis Tools for Excel&#41;</span></span>](detect-categories-table-analysis-tools-for-excel.md)  
  
  
