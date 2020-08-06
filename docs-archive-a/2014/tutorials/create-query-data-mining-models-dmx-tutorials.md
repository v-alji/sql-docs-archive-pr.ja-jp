---
title: 'DMX を使用したデータマイニングモデルの作成とクエリ: チュートリアル (Analysis Services-データマイニング) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- content queries [DMX]
ms.assetid: 145b81a7-c0c3-4ca3-bb32-0b482423b9a0
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 22ed01105a32f460bcbeb2c067299fdf62af2eed
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630719"
---
# <a name="creating-and-querying-data-mining-models-with-dmx-tutorials-analysis-services---data-mining"></a><span data-ttu-id="1c037-102">DMX を使用したデータ マイニング モデルの作成とクエリ : チュートリアル (Analysis Services - データ マイニング)</span><span class="sxs-lookup"><span data-stu-id="1c037-102">Creating and Querying Data Mining Models with DMX: Tutorials (Analysis Services - Data Mining)</span></span>
  <span data-ttu-id="1c037-103">を使用してデータマイニングソリューションを作成した後、 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データマイニングモデルに対するクエリを作成して、傾向を予測し、データ内のパターンを取得し、マイニングモデルの精度を測定することができます。</span><span class="sxs-lookup"><span data-stu-id="1c037-103">After you have created a data mining solution by using [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], you can create queries against the data mining models to predict trends, retrieve patterns in the data, and measure the accuracy of the mining models.</span></span>  
  
 <span data-ttu-id="1c037-104">次の一覧の手順を追ったチュートリアルでは、データを最大限に活用できるように、を使用してデータマイニングクエリを構築および実行する方法について説明し [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="1c037-104">The step-by-step tutorials in the following list will help you learn how to build and run data mining queries by using [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] so that you can get the most from your data.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1c037-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="1c037-105">In This Section</span></span>  
  
-   [<span data-ttu-id="1c037-106">Bike Buyer DMX のチュートリアル</span><span class="sxs-lookup"><span data-stu-id="1c037-106">Bike Buyer DMX Tutorial</span></span>](../../2014/tutorials/bike-buyer-dmx-tutorial.md)  
  
     <span data-ttu-id="1c037-107">このチュートリアルでは、データ マイニング拡張機能 (DMX) 言語を使用して、新しいマイニング構造とマイニング モデルを作成する手順を紹介します。また、DMX 予測クエリの作成方法についても説明します。</span><span class="sxs-lookup"><span data-stu-id="1c037-107">This tutorial walks you through the creation of a new mining structure and mining models by using the Data Mining Extensions (DMX) language, and explains how to create DMX prediction queries.</span></span>  
  
-   [<span data-ttu-id="1c037-108">マーケット バスケット DMX のチュートリアル</span><span class="sxs-lookup"><span data-stu-id="1c037-108">Market Basket DMX Tutorial</span></span>](../../2014/tutorials/market-basket-dmx-tutorial.md)  
  
     <span data-ttu-id="1c037-109">このチュートリアルでは、一般的なマーケット バスケット シナリオを使用します。このシナリオでは、顧客が一緒に購入する製品間の関連性を検出します。</span><span class="sxs-lookup"><span data-stu-id="1c037-109">This tutorial uses a typical market basket scenario, where you find associations between the products that customers purchase together.</span></span> <span data-ttu-id="1c037-110">また、マイニング構造を作成する場合の入れ子になったテーブルの使用方法についても説明します。</span><span class="sxs-lookup"><span data-stu-id="1c037-110">This tutorial also demonstrates how to use nested tables when you create a mining structure.</span></span> <span data-ttu-id="1c037-111">この構造に基づいてモデルの作成とトレーニングを行い、DMX を使用して予測を作成します。</span><span class="sxs-lookup"><span data-stu-id="1c037-111">You build and train a model based on this structure, and then create predictions using DMX.</span></span>  
  
-   [<span data-ttu-id="1c037-112">時系列予測の DMX のチュートリアル</span><span class="sxs-lookup"><span data-stu-id="1c037-112">Time Series Prediction DMX Tutorial</span></span>](../../2014/tutorials/time-series-prediction-dmx-tutorial.md)  
  
     <span data-ttu-id="1c037-113">このチュートリアルでは、予測モデルを作成して CREATE MODEL (DMX) ステートメントの使用方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="1c037-113">This tutorial creates a forecasting model to illustrate the use of the CREATE MODEL (DMX) statement.</span></span> <span data-ttu-id="1c037-114">次に、関連するモデルを追加し、Microsoft Time Series アルゴリズムのパラメーターを変更して各モデルの動作をカスタマイズします。</span><span class="sxs-lookup"><span data-stu-id="1c037-114">You then add related models and customize the behavior of each by changing the parameters of the Microsoft Time Series algorithm.</span></span> <span data-ttu-id="1c037-115">最後に、予測を作成し、新しいデータで予測を更新します。</span><span class="sxs-lookup"><span data-stu-id="1c037-115">Finally you create predictions and update the predictions with new data.</span></span> <span data-ttu-id="1c037-116">予測の際に時系列を更新する機能は、[!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] で追加されました。</span><span class="sxs-lookup"><span data-stu-id="1c037-116">The ability to update a time series while making predictions was added in [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)].</span></span>  
  
## <a name="reference"></a><span data-ttu-id="1c037-117">リファレンス</span><span class="sxs-lookup"><span data-stu-id="1c037-117">Reference</span></span>  
 [<span data-ttu-id="1c037-118">データ マイニング アルゴリズム &#40;Analysis Services - データ マイニング&#41;</span><span class="sxs-lookup"><span data-stu-id="1c037-118">Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;</span></span>](../../2014/analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md)  
  
 [<span data-ttu-id="1c037-119">データ マイニング拡張機能 &#40;DMX&#41; リファレンス</span><span class="sxs-lookup"><span data-stu-id="1c037-119">Data Mining Extensions &#40;DMX&#41; Reference</span></span>](/sql/dmx/data-mining-extensions-dmx-reference)  
  
## <a name="related-sections"></a><span data-ttu-id="1c037-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="1c037-120">Related Sections</span></span>  
  
-   [<span data-ttu-id="1c037-121">基本的なデータ マイニング チュートリアル</span><span class="sxs-lookup"><span data-stu-id="1c037-121">Basic Data Mining Tutorial</span></span>](../../2014/tutorials/basic-data-mining-tutorial.md)  
  
     <span data-ttu-id="1c037-122">このチュートリアルでは、プロジェクトの作成方法、マイニング構造とマイニング モデルの作成方法など基本的な概念について説明します。</span><span class="sxs-lookup"><span data-stu-id="1c037-122">This tutorial introduces basic concepts, such as how to create a project and how to build mining structures and mining models.</span></span>  
  
-   [<span data-ttu-id="1c037-123">中級者向けデータマイニングチュートリアル &#40;Analysis Services データマイニング&#41;</span><span class="sxs-lookup"><span data-stu-id="1c037-123">Intermediate Data Mining Tutorial &#40;Analysis Services - Data Mining&#41;</span></span>](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)  
  
     <span data-ttu-id="1c037-124">このチュートリアルは複数の個別のレッスンをまとめたもので、それぞれのレッスンで異なる種類のモデルについて説明します。</span><span class="sxs-lookup"><span data-stu-id="1c037-124">This tutorial contains a number of independent lessons, each introducing you to a different model type.</span></span> <span data-ttu-id="1c037-125">各レッスンで、モデルを作成し、そのモデルを検証してから、モデルをカスタマイズして予測クエリを作成するまでの一連の手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="1c037-125">Each lesson walks you through the process of creating a model, exploring the model, and then customizing the model and creating prediction queries.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c037-126">参照</span><span class="sxs-lookup"><span data-stu-id="1c037-126">See Also</span></span>  
 <span data-ttu-id="1c037-127">[データマイニングソリューション](../../2014/analysis-services/data-mining/data-mining-solutions.md) </span><span class="sxs-lookup"><span data-stu-id="1c037-127">[Data Mining Solutions](../../2014/analysis-services/data-mining/data-mining-solutions.md) </span></span>  
 <span data-ttu-id="1c037-128">[データマイニングツール](../../2014/analysis-services/data-mining/data-mining-tools.md) </span><span class="sxs-lookup"><span data-stu-id="1c037-128">[Data Mining Tools](../../2014/analysis-services/data-mining/data-mining-tools.md) </span></span>  
 [<span data-ttu-id="1c037-129">データ マイニング プロジェクト</span><span class="sxs-lookup"><span data-stu-id="1c037-129">Data Mining Projects</span></span>](../../2014/analysis-services/data-mining/data-mining-projects.md)  
  
  
