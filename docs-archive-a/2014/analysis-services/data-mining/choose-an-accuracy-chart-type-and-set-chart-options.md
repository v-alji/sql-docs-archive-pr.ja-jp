---
title: 精度チャートの種類の選択とグラフのオプションの設定 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Mining Accuracy Chart [Analysis Services]
- mining models [Analysis Services], validating
- classification accuracy [data mining]
- accuracy testing [data mining]
ms.assetid: bd24dd4a-624f-478a-9c94-b1361e857680
author: minewiskan
ms.author: owend
ms.openlocfilehash: 33c2b5e8a1e228a86328ef6df1b636742d3614ff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639815"
---
# <a name="choose-an-accuracy-chart-type-and-set-chart-options"></a><span data-ttu-id="049b8-102">精度チャートの種類の選択とグラフのオプションの設定</span><span class="sxs-lookup"><span data-stu-id="049b8-102">Choose an Accuracy Chart Type and Set Chart Options</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="049b8-103">に [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は、マイニングモデルの有効性を判断するための複数の方法が用意されています。</span><span class="sxs-lookup"><span data-stu-id="049b8-103">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] provides multiple methods for determining the validity of your mining models.</span></span> <span data-ttu-id="049b8-104">各モデルまたは構造に対して作成できる精度チャートの種類は、以下の要因によって異なります。</span><span class="sxs-lookup"><span data-stu-id="049b8-104">The type of accuracy chart that you can create for each model or structure depends on these factors:</span></span>  
  
-   <span data-ttu-id="049b8-105">モデルの作成に使用したアルゴリズムの種類</span><span class="sxs-lookup"><span data-stu-id="049b8-105">The type of algorithm that was used to create the model</span></span>  
  
-   <span data-ttu-id="049b8-106">予測可能な属性のデータ型</span><span class="sxs-lookup"><span data-stu-id="049b8-106">The data type of the predictable attribute</span></span>  
  
-   <span data-ttu-id="049b8-107">測定する予測可能な属性の数</span><span class="sxs-lookup"><span data-stu-id="049b8-107">The number of predictable attributes to measure</span></span>  
  
 <span data-ttu-id="049b8-108">このトピックでは、各種の精度チャートの概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="049b8-108">This topic provides an overview of the different accuracy charts.</span></span>  
  
 <span data-ttu-id="049b8-109">**注:** グラフとその定義は保存されません。</span><span class="sxs-lookup"><span data-stu-id="049b8-109">**Note** Charts and their definitions are not saved.</span></span> <span data-ttu-id="049b8-110">グラフが含まれているウィンドウを閉じた場合は、グラフを作成し直す必要があります。</span><span class="sxs-lookup"><span data-stu-id="049b8-110">If you close the window that contains a chart, you must create the chart again.</span></span>  
  
## <a name="accuracy-chart-types"></a><span data-ttu-id="049b8-111">精度チャートの種類</span><span class="sxs-lookup"><span data-stu-id="049b8-111">Accuracy Chart Types</span></span>  
 <span data-ttu-id="049b8-112">選択するグラフの種類によっては、さらにオプションを構成したり、グラフを参照したり、グラフをクリップボードにコピーして Excel でデータを操作したりできます。</span><span class="sxs-lookup"><span data-stu-id="049b8-112">Depending on the chart type that you choose, you have the ability to further configure options, to browse the chart, or copy the chart to the Clipboard and work with the data in Excel.</span></span>  
  
#### <a name="lift-chart"></a><span data-ttu-id="049b8-113">リフト チャート</span><span class="sxs-lookup"><span data-stu-id="049b8-113">Lift chart</span></span>  
 <span data-ttu-id="049b8-114">モデルおよびテスト用データのオプションを構成した後、 **[リフト チャート]** タブをクリックすると、結果が表示されます。</span><span class="sxs-lookup"><span data-stu-id="049b8-114">After you have configured the options for the models and the testing data, click the **Lift Chart** tab to view the results.</span></span> <span data-ttu-id="049b8-115">グラフをクリップボードにコピーしたり、個々の傾向線やデータ ポイントの詳細をマイニング凡例で確認したりすることもできます。</span><span class="sxs-lookup"><span data-stu-id="049b8-115">You can also copy the chart to the Clipboard, or view details of individual trend lines or data points in the Mining Legend.</span></span>  
  
#### <a name="profit-chart"></a><span data-ttu-id="049b8-116">利益チャート</span><span class="sxs-lookup"><span data-stu-id="049b8-116">Profit Chart</span></span>  
 <span data-ttu-id="049b8-117">モデルおよびテスト用データのオプションを構成した後、 **[リフト チャート]** タブをクリックし、 **[グラフの種類]** ボックスの一覧の **[利益チャート]** を選択します。利益チャートのオプションを設定して **[OK]** をクリックすると、結果が表示されます。</span><span class="sxs-lookup"><span data-stu-id="049b8-117">After you have configured the options for the models and the testing data, click the **Lift Chart** tab, select **Profit Chart** from the **Chart Type** list to set profit chart options, and then click **OK** to view the results.</span></span>  
  
 <span data-ttu-id="049b8-118">必要に応じて **[利益チャートの設定]** ダイアログ ボックスを繰り返し使用して、別のコストでグラフを再表示してみることもできます。</span><span class="sxs-lookup"><span data-stu-id="049b8-118">You can use the **Profit Chart Settings** dialog box as many times as you want to try different cost options and redisplay the chart.</span></span> <span data-ttu-id="049b8-119">マイニング凡例には、各モデルの推定利益に関する詳細情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="049b8-119">The Mining Legend contains detailed information about the estimated profit for each model.</span></span> <span data-ttu-id="049b8-120">グラフとマイニング凡例の内容をクリップボードにコピーして、Excel で操作することもできます。</span><span class="sxs-lookup"><span data-stu-id="049b8-120">You can also copy the chart and the contents of the Mining Legend to the Clipboard to work with it in Excel.</span></span>  
  
#### <a name="scatter-plot"></a><span data-ttu-id="049b8-121">散布図</span><span class="sxs-lookup"><span data-stu-id="049b8-121">Scatter Plot</span></span>  
 <span data-ttu-id="049b8-122">適切な種類のモデルが選択されている場合に **[リフト チャート]** タブをクリックすると、グラフの種類が自動的に **[散布図]** に設定されて、散布図が表示されます。</span><span class="sxs-lookup"><span data-stu-id="049b8-122">If you have selected the appropriate type of model, when you click the **Lift Chart** tab, the chart type is automatically set to **Scatter Plot** and a scatter plot is displayed.</span></span> <span data-ttu-id="049b8-123">それ以上の構成はできません。</span><span class="sxs-lookup"><span data-stu-id="049b8-123">No further configuration is possible.</span></span> <span data-ttu-id="049b8-124">グラフをクリップボードにコピーして、Excel やその他のアプリケーションにグラフィックとして貼り付けることもできます。</span><span class="sxs-lookup"><span data-stu-id="049b8-124">You can also copy the chart to the Clipboard and paste the chart as a graphic into Excel or another application.</span></span>  
  
#### <a name="classification-matrix"></a><span data-ttu-id="049b8-125">分類マトリックス</span><span class="sxs-lookup"><span data-stu-id="049b8-125">Classification Matrix</span></span>  
 <span data-ttu-id="049b8-126">分類マトリックスの場合は、 **[入力の選択]** タブを使用してモデルおよびテスト用データを選択した後、 **[分類マトリックス]** タブをクリックすると、結果が表示されます。</span><span class="sxs-lookup"><span data-stu-id="049b8-126">For a classification matrix, use the **Input Selection** tab to choose the models and the testing data, and then click the **Classification Matrix** tab to view the results.</span></span>  
  
 <span data-ttu-id="049b8-127">分類マトリックスの内容はすべてのモデルの種類で同じであり、構成することはできません。</span><span class="sxs-lookup"><span data-stu-id="049b8-127">The contents of a classification matrix are the same for all model types, and cannot be configured.</span></span> <span data-ttu-id="049b8-128">グラフ内のデータをクリップボードにコピーして、Excel で操作することができます。</span><span class="sxs-lookup"><span data-stu-id="049b8-128">You can copy the data in the chart to the Clipboard and then work with it in Excel.</span></span>  
  
#### <a name="cross-validation-report"></a><span data-ttu-id="049b8-129">クロス検証レポート</span><span class="sxs-lookup"><span data-stu-id="049b8-129">Cross-Validation Report</span></span>  
 <span data-ttu-id="049b8-130">クロス検証レポートの場合は、ソリューション エクスプローラーでマイニング構造またはマイニング モデルを選択した後、 **[クロス検証]** タブをクリックして、関連するすべてのオプションを構成します。その後、 **[結果の取得]** をクリックすると、レポートが生成されます。</span><span class="sxs-lookup"><span data-stu-id="049b8-130">For a cross-validation report, after you have selected a mining structure or mining model in Solution Explorer, click the **Cross Validation** tab, configure all relevant options, and then click **Get Results** to generate the report.</span></span> <span data-ttu-id="049b8-131">それ以上の構成はできません。</span><span class="sxs-lookup"><span data-stu-id="049b8-131">No further configuration is possible.</span></span>  
  
 <span data-ttu-id="049b8-132">クロス検証レポートの形式はすべてのモデルの種類で同じであり、構成することはできません。</span><span class="sxs-lookup"><span data-stu-id="049b8-132">The format of the cross-validation report is the same for all model types, and cannot be configured.</span></span> <span data-ttu-id="049b8-133">ただし、レポートの内容は、分析するモデルの種類や、予測可能な属性のデータ型によって異なります。</span><span class="sxs-lookup"><span data-stu-id="049b8-133">However, the content of the report differs depending on the type of model that you are analyzing, and the data type of the predictable attribute.</span></span> <span data-ttu-id="049b8-134">レポートの結果をクリップボードにコピーして、データを Excel で操作することもできます。</span><span class="sxs-lookup"><span data-stu-id="049b8-134">You can also copy the results of the report to the Clipboard and work with the data in Excel.</span></span>  
  
  
