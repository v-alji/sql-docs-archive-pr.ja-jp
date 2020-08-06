---
title: マイニングモデルのテストに使用する列を選択してください |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- columns [data mining], predictable mining columns
- Mining Accuracy Chart [Analysis Services], columns
- predictable mining columns [Analysis Services]
ms.assetid: c6a8f23a-da21-4f31-9521-99460d624649
author: minewiskan
ms.author: owend
ms.openlocfilehash: 326a7084600695d95d3a132f633041e9abad045b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642421"
---
# <a name="choose-the-column-to-use-for-testing-a-mining-model"></a><span data-ttu-id="702d9-102">マイニング モデルのテストに使用する列の選択</span><span class="sxs-lookup"><span data-stu-id="702d9-102">Choose the Column to Use for Testing a Mining Model</span></span>
  <span data-ttu-id="702d9-103">マイニング モデルの精度を測定する前に、評価するのがどの結果なのかを決定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="702d9-103">Before you can measure the accuracy of a mining model, you must decide which outcome it is that you want to assess.</span></span> <span data-ttu-id="702d9-104">多くのデータ マイニング モデルでは、モデルの作成時に、予測可能な属性として使用する少なくとも 1 つの列を選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="702d9-104">Most data mining models require that you choose at least one column to use as the predictable attribute when you create the model.</span></span> <span data-ttu-id="702d9-105">そのため、モデルの精度をテストするときに、通常はその属性をテスト対象として選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="702d9-105">Therefore, when you test the accuracy of the model, you generally must select that attribute to test.</span></span>  
  
 <span data-ttu-id="702d9-106">次の一覧では、テストに使用する予測可能な属性を選択する際のいくつかの追加の考慮事項について説明します。</span><span class="sxs-lookup"><span data-stu-id="702d9-106">The following list describes some additional considerations for choosing the predictable attribute to use in testing:</span></span>  
  
-   <span data-ttu-id="702d9-107">一部の種類のデータマイニングモデルでは、複数の属性 (ニューラルネットワークなど) を予測できます。これにより、多くの属性間の関係を調べることができます。</span><span class="sxs-lookup"><span data-stu-id="702d9-107">Some types of data mining models can predict multiple attributes-such as neural networks, which can explore the relationships between many attributes.</span></span>  
  
-   <span data-ttu-id="702d9-108">クラスターモデルなど、他の種類のマイニングモデルには、予測可能な属性が含まれているとは限りません。</span><span class="sxs-lookup"><span data-stu-id="702d9-108">Other types of mining models-such as clustering models-do not necessarily have a predictable attribute.</span></span> <span data-ttu-id="702d9-109">予測可能な属性がない場合、クラスター モデルはテストできません。</span><span class="sxs-lookup"><span data-stu-id="702d9-109">Clustering models cannot be tested unless they have a predictable attribute.</span></span>  
  
-   <span data-ttu-id="702d9-110">散布図を作成するか、回帰モデルの精度を測定するには、連続する予測可能な属性を結果として選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="702d9-110">To create a scatter plot or measure the accuracy of a regression model requires that you choose a continuous predictable attribute as the outcome.</span></span> <span data-ttu-id="702d9-111">その場合、対象の値は指定できません。</span><span class="sxs-lookup"><span data-stu-id="702d9-111">In that case, you cannot specify a target value.</span></span> <span data-ttu-id="702d9-112">散布図以外のものを作成する場合は、基になるマイニング構造列のコンテンツの種類も、 **[不連続]** または **[分離]** である必要があります。</span><span class="sxs-lookup"><span data-stu-id="702d9-112">If you are creating anything other than a scatter plot, the underlying mining structure column must also have a content type of **Discrete** or **Discretized**.</span></span>  
  
-   <span data-ttu-id="702d9-113">不連続属性を予測可能な結果として選択した場合は、対象の値を指定することも、 **[予測値]** フィールドを空のままにすることもできます。</span><span class="sxs-lookup"><span data-stu-id="702d9-113">If you choose a discrete attribute as the predictable outcome, you can also specify a target value, or you can leave the **Predict Value** field blank.</span></span> <span data-ttu-id="702d9-114">**予測値**を含める場合、グラフでは、目標値の予測におけるモデルの有効性のみが測定されます。</span><span class="sxs-lookup"><span data-stu-id="702d9-114">If you include a **Predict Value**, the chart will measure only the model's effectiveness at predicting the target value.</span></span> <span data-ttu-id="702d9-115">対象となる結果を指定しない場合、モデルはすべての結果の予測で精度が測定されます。</span><span class="sxs-lookup"><span data-stu-id="702d9-115">If you do not specify a target outcome, the model is measured for its accuracy in predicting all outcomes.</span></span>  
  
-   <span data-ttu-id="702d9-116">複数のモデルを含めて、それらを 1 つの精度チャートで比較する場合、すべてのモデルは同じ予測可能列を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="702d9-116">If you want to include multiple models and compare them in a single accuracy chart, all models must use the same predictable column.</span></span>  
  
-   <span data-ttu-id="702d9-117">クロス検証レポートを作成する場合は、同じ予測可能な属性を持つすべてのモデルが [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] によって自動的に分析されます。</span><span class="sxs-lookup"><span data-stu-id="702d9-117">When you create a cross-validation report, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] will automatically analyze all models that have the same predictable attribute.</span></span>  
  
-   <span data-ttu-id="702d9-118">オプションの **[予測列と値の同期]** が選択されている場合は、同じ名前および一致するデータ型を持つ予測可能列が [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] によって自動的に選択されます。</span><span class="sxs-lookup"><span data-stu-id="702d9-118">When the option, **Synchronize Prediction columns and Values**, is selected, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] automatically chooses predictable columns that have the same names and matching data types.</span></span> <span data-ttu-id="702d9-119">列がこれらの基準を満たさない場合は、このオプションをオフにして、手動で予測可能列を選択できます。</span><span class="sxs-lookup"><span data-stu-id="702d9-119">If your columns do not meet these criteria, you can turn off this option and manually choose a predictable column.</span></span> <span data-ttu-id="702d9-120">モデルとは異なる列を持つ外部データ セットのモデルをテストしている場合は、このように操作しなければならないことがあります。</span><span class="sxs-lookup"><span data-stu-id="702d9-120">You might need to do this if you are testing the model with an external data set that has different columns than the model.</span></span> <span data-ttu-id="702d9-121">ただし、不適切なデータ型の列を選択すると、エラーが発生するか、正しい結果を得ることができません。</span><span class="sxs-lookup"><span data-stu-id="702d9-121">However, if you choose a column with the wrong the type of data you will either get an error or bad results.</span></span>  
  
### <a name="specify-the-outcome-to-predict"></a><span data-ttu-id="702d9-122">予測する結果の指定</span><span class="sxs-lookup"><span data-stu-id="702d9-122">Specify the outcome to predict</span></span>  
  
1.  <span data-ttu-id="702d9-123">マイニング構造をダブルクリックしてデータ マイニング デザイナーで開きます。</span><span class="sxs-lookup"><span data-stu-id="702d9-123">Double-click the mining structure to open it in Data Mining Designer.</span></span>  
  
2.  <span data-ttu-id="702d9-124">**[マイニング精度チャート]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="702d9-124">Select the **Mining Accuracy Chart** tab.</span></span>  
  
3.  <span data-ttu-id="702d9-125">**[入力の選択]** タブを選択します。</span><span class="sxs-lookup"><span data-stu-id="702d9-125">Select the **Input Selection** tab.</span></span>  
  
4.  <span data-ttu-id="702d9-126">**[入力の選択]** タブの **[予測可能列名]** で、グラフに含めるモデルごとに予測可能列を選択します。</span><span class="sxs-lookup"><span data-stu-id="702d9-126">On the **Input Selection** tab, under **Predictable Column Name**, select a predictable column for each model that you include in the chart.</span></span>  
  
     <span data-ttu-id="702d9-127">**[予測可能列名]** ボックスに表示されるマイニング モデル列は、使用法が **[予測]** または **[予測のみ]** に設定されている列だけです。</span><span class="sxs-lookup"><span data-stu-id="702d9-127">The mining model columns that are available in the **Predictable Column Name** box are only those with the usage type set to **Predict** or **Predict Only**.</span></span>  
  
5.  <span data-ttu-id="702d9-128">モデルのリフト値を指定する場合は、 **[予測値]** の一覧から、測定する特定の結果値を選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="702d9-128">If you want to determine the lift for a model, you must select a specific outcome value to measure, for by choosing from the **Predict Value** list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="702d9-129">参照</span><span class="sxs-lookup"><span data-stu-id="702d9-129">See Also</span></span>  
 <span data-ttu-id="702d9-130">[モデルテストデータを選択してマップする](choose-and-map-model-testing-data.md) </span><span class="sxs-lookup"><span data-stu-id="702d9-130">[Choose and Map Model Testing Data](choose-and-map-model-testing-data.md) </span></span>  
 [<span data-ttu-id="702d9-131">精度チャートの種類の選択とグラフのオプションの設定</span><span class="sxs-lookup"><span data-stu-id="702d9-131">Choose an Accuracy Chart Type and Set Chart Options</span></span>](choose-an-accuracy-chart-type-and-set-chart-options.md)  
  
  
