---
title: モデルでリグレッサーとして使用する列を指定します |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: d8e0cb8e-302a-4166-9ed0-e2d9e2919b0a
author: minewiskan
ms.author: owend
ms.openlocfilehash: 86899d3793985b5e3c07618360d7b6a540935a54
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631342"
---
# <a name="specify-a-column-to-use-as-regressor-in-a-model"></a><span data-ttu-id="69edc-102">モデルでリグレッサーとして使用する列の指定</span><span class="sxs-lookup"><span data-stu-id="69edc-102">Specify a Column to Use as Regressor in a Model</span></span>
  <span data-ttu-id="69edc-103">線形回帰モデルでは、予測可能な属性の値が、データをできる限り推定回帰直線に近づけるように入力を組み合わせる式の結果として表されます。</span><span class="sxs-lookup"><span data-stu-id="69edc-103">A linear regression model represents the value of the predictable attribute as the result of a formula that combines the inputs in such a way that the data is fitted as a closely as possible to an estimated regression line.</span></span> <span data-ttu-id="69edc-104">このアルゴリズムでは、入力として使用できるのは数値だけであり、最適な入力が自動的に検出されます。</span><span class="sxs-lookup"><span data-stu-id="69edc-104">The algorithm accepts only numeric values as inputs, and automatically detects the inputs that provide the best fit.</span></span>  
  
 <span data-ttu-id="69edc-105">ただし、リグレッサーとして含める列を指定することもできます。その場合は、モデルに FORCE_REGRESSOR パラメーターを追加して、使用するリグレッサーを指定します。</span><span class="sxs-lookup"><span data-stu-id="69edc-105">However, you can specify that a column be included as a regressor by adding the FORCE_REGRESSOR parameter to the model and specifying the regressors to use.</span></span> <span data-ttu-id="69edc-106">この方法は、影響が小さすぎてモデルで検出されない場合にも意味を持つ属性や、確実に式に含まれるようにしたい属性がある場合に使用できます。</span><span class="sxs-lookup"><span data-stu-id="69edc-106">You might want to do this in cases where the attribute has meaning even if the effect is too small to be detected by the model, or when you want to ensure that the attribute is included in the formula.</span></span>  
  
 <span data-ttu-id="69edc-107">[次の手順では、ニューラル ネットワークのチュートリアル](../../tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md)で使用したのと同じサンプル データを使用して、単純な線形回帰モデルを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="69edc-107">The following procedure describes how to create a simple linear regression model, using the same sample data that is used for the [neural networks tutorial](../../tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md).</span></span> <span data-ttu-id="69edc-108">このモデルは必ずしも堅牢ではありませんが、データ マイニング デザイナーを使用して線形回帰モデルをカスタマイズする方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="69edc-108">The model is not necessarily robust, but demonstrates how to use the Data Mining Designer to customize a linear regression model.</span></span>  
  
### <a name="how-to-create-a-simple-linear-regression-model"></a><span data-ttu-id="69edc-109">単純な線形回帰モデルを作成する方法</span><span class="sxs-lookup"><span data-stu-id="69edc-109">How to create a simple linear regression model</span></span>  
  
1.  <span data-ttu-id="69edc-110">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]の **ソリューション エクスプローラーで**、 **[マイニング構造]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="69edc-110">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], in **Solution Explorer**, expand **Mining Structures**.</span></span>  
  
2.  <span data-ttu-id="69edc-111">Call Center.dmm をダブルクリックしてデザイナーで開きます。</span><span class="sxs-lookup"><span data-stu-id="69edc-111">Double-click Call Center.dmm to open it in the designer.</span></span>  
  
3.  <span data-ttu-id="69edc-112">**[マイニング モデル]** メニューの **[新しいマイニング モデル]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="69edc-112">From the **Mining Model** menu, select **New Mining Model**.</span></span>  
  
4.  <span data-ttu-id="69edc-113">アルゴリズムとして **[Microsoft 線形回帰]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="69edc-113">For the algorithm, select **Microsoft Linear Regression**.</span></span> <span data-ttu-id="69edc-114">名前として「 **Call Center Regression**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="69edc-114">For the name, type **Call Center Regression**.</span></span>  
  
5.  <span data-ttu-id="69edc-115">**[マイニング モデル]** タブで、列の使用方法を次のように変更します。</span><span class="sxs-lookup"><span data-stu-id="69edc-115">In the **Mining Models** tab, change the column usage as follows.</span></span> <span data-ttu-id="69edc-116">これ以外の列はすべて **[無視]** に設定します (まだ設定されていない場合)。</span><span class="sxs-lookup"><span data-stu-id="69edc-116">All columns not in the following list should be set to **Ignore**, if they are not already.</span></span>  
  
     <span data-ttu-id="69edc-117">FactCallCenterID**Key**</span><span class="sxs-lookup"><span data-stu-id="69edc-117">FactCallCenterID**Key**</span></span>  
  
     <span data-ttu-id="69edc-118">ServiceGrade**PredictOnly**</span><span class="sxs-lookup"><span data-stu-id="69edc-118">ServiceGrade**PredictOnly**</span></span>  
  
     <span data-ttu-id="69edc-119">Total Operators**Input**</span><span class="sxs-lookup"><span data-stu-id="69edc-119">Total Operators**Input**</span></span>  
  
     <span data-ttu-id="69edc-120">AverageTimePerIssue**Input**</span><span class="sxs-lookup"><span data-stu-id="69edc-120">AverageTimePerIssue**Input**</span></span>  
  
6.  <span data-ttu-id="69edc-121">**[マイニング モデル]** メニューの **[モデル パラメーターの設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="69edc-121">From the **Mining Model** menu, select **Set Model Parameters**.</span></span>  
  
7.  <span data-ttu-id="69edc-122">パラメーター FORCE_REGRESSOR の **[値]** 列に、列の名前を入力します。次のように各かっこで囲み、コンマで区切って入力します。</span><span class="sxs-lookup"><span data-stu-id="69edc-122">For the parameter, FORCE_REGRESSOR, in the **Value** column, type the column names enclosed in brackets and separated by a comma, as follows:</span></span>  
  
    ```  
    [Average Time Per Issue],[Total Operators]  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="69edc-123">このアルゴリズムでは、リグレッサーとして最適な列が自動的に検出されます。</span><span class="sxs-lookup"><span data-stu-id="69edc-123">The algorithm will automatically detect which columns are the best regressors.</span></span> <span data-ttu-id="69edc-124">リグレッサーを強制する必要があるのは、最終的な式に確実に含まれるようにしたい列がある場合だけです。</span><span class="sxs-lookup"><span data-stu-id="69edc-124">You only need to force regressors when you want to ensure that a column is included in the final formula.</span></span>  
  
8.  <span data-ttu-id="69edc-125">**[マイニング モデル]** メニューの **[モデルの処理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="69edc-125">From the **Mining Model** menu, select **Process Model**.</span></span>  
  
     <span data-ttu-id="69edc-126">ビューアーでは、モデルが、回帰式を含む 1 つのノードとして表されます。</span><span class="sxs-lookup"><span data-stu-id="69edc-126">In the viewer, the model is represented a single node containing the regression formula.</span></span> <span data-ttu-id="69edc-127">その式を **マイニング凡例**に表示したり、クエリを使用して式の係数を抽出したりすることもできます。</span><span class="sxs-lookup"><span data-stu-id="69edc-127">You can view the formula in the **Mining Legend**, or you can extract the coefficients for the formula by using queries.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69edc-128">参照</span><span class="sxs-lookup"><span data-stu-id="69edc-128">See Also</span></span>  
 <span data-ttu-id="69edc-129">[Microsoft 線形回帰アルゴリズム](microsoft-linear-regression-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="69edc-129">[Microsoft Linear Regression Algorithm](microsoft-linear-regression-algorithm.md) </span></span>  
 <span data-ttu-id="69edc-130">[データマイニングクエリ](data-mining-queries.md) </span><span class="sxs-lookup"><span data-stu-id="69edc-130">[Data Mining Queries](data-mining-queries.md) </span></span>  
 <span data-ttu-id="69edc-131">[Microsoft 線形回帰アルゴリズムテクニカルリファレンス](microsoft-linear-regression-algorithm-technical-reference.md) </span><span class="sxs-lookup"><span data-stu-id="69edc-131">[Microsoft Linear Regression Algorithm Technical Reference](microsoft-linear-regression-algorithm-technical-reference.md) </span></span>  
 [<span data-ttu-id="69edc-132">線形回帰モデルのマイニング モデル コンテンツ &#40;Analysis Services - データ マイニング&#41;</span><span class="sxs-lookup"><span data-stu-id="69edc-132">Mining Model Content for Linear Regression Models &#40;Analysis Services - Data Mining&#41;</span></span>](mining-model-content-for-linear-regression-models-analysis-services-data-mining.md)  
  
  
