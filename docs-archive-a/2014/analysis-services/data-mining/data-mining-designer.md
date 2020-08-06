---
title: データマイニングデザイナー |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data mining [Analysis Services], structure
- mining structures [Analysis Services], modifying
- data mining editor [Analysis Services]
- Data Mining Designer
- data mining [Analysis Services], modifying
ms.assetid: 2540db5b-2bf3-4b6c-87c8-79c48d71acce
author: minewiskan
ms.author: owend
ms.openlocfilehash: 820cde158dfabff525081060369daace0e83c8dc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632186"
---
# <a name="data-mining-designer"></a><span data-ttu-id="a073e-102">Data Mining Designer</span><span class="sxs-lookup"><span data-stu-id="a073e-102">Data Mining Designer</span></span>
  <span data-ttu-id="a073e-103">データマイニングデザイナーは、でマイニングモデルを操作するための主要な環境です [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="a073e-103">Data Mining Designer is the primary environment in which you work with mining models in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="a073e-104">データ マイニング デザイナーにアクセスするには、既存のマイニング構造を選択するか、またはデータ マイニング ウィザードを使用して新しいマイニング構造とマイニング モデルを作成します。</span><span class="sxs-lookup"><span data-stu-id="a073e-104">You can access the designer either by selecting an existing mining structure, or by using the Data Mining Wizard to create a new mining structure and mining model.</span></span> <span data-ttu-id="a073e-105">データ マイニング デザイナーを使用すると、次の作業を実行できます。</span><span class="sxs-lookup"><span data-stu-id="a073e-105">You can use Data Mining Designer to perform the following tasks:</span></span>  
  
-   <span data-ttu-id="a073e-106">最初にデータ マイニング ウィザードで作成したマイニング構造とマイニング モデルを変更する。</span><span class="sxs-lookup"><span data-stu-id="a073e-106">Modify the mining structure and the mining model that were initially created by the Data Mining Wizard.</span></span>  
  
-   <span data-ttu-id="a073e-107">既存のマイニング構造に基づいて新しいモデルを作成する。</span><span class="sxs-lookup"><span data-stu-id="a073e-107">Create new models based on an existing mining structure.</span></span>  
  
-   <span data-ttu-id="a073e-108">マイニング モデルをトレーニングして参照する。</span><span class="sxs-lookup"><span data-stu-id="a073e-108">Train and browse mining models.</span></span>  
  
-   <span data-ttu-id="a073e-109">精度チャートを使用してモデルを比較する。</span><span class="sxs-lookup"><span data-stu-id="a073e-109">Compare models by using accuracy charts.</span></span>  
  
-   <span data-ttu-id="a073e-110">マイニング モデルに基づいて予測クエリを作成する。</span><span class="sxs-lookup"><span data-stu-id="a073e-110">Create prediction queries based on mining models.</span></span>  
  
## <a name="mining-structure-tab"></a><span data-ttu-id="a073e-111">[マイニング構造] タブ</span><span class="sxs-lookup"><span data-stu-id="a073e-111">Mining Structure Tab</span></span>  
 <span data-ttu-id="a073e-112">**[マイニング構造]** タブを使用すると、列を追加したり、既存のマイニング構造のプロパティを変更したりできます。</span><span class="sxs-lookup"><span data-stu-id="a073e-112">Use the **Mining Structure** tab to add columns and modify the properties of an existing mining structure.</span></span> <span data-ttu-id="a073e-113">次のタスクおよびトピックでは、マイニング構造の操作の詳細について説明します。</span><span class="sxs-lookup"><span data-stu-id="a073e-113">The following tasks and topics provide more information about working with mining structures:</span></span>  
  
 [<span data-ttu-id="a073e-114">マイニング構造 (Analysis Services - データ マイニング)</span><span class="sxs-lookup"><span data-stu-id="a073e-114">Mining Structures &#40;Analysis Services - Data Mining&#41;</span></span>](mining-structures-analysis-services-data-mining.md)  
  
 [<span data-ttu-id="a073e-115">マイニング構造のタスクと操作方法</span><span class="sxs-lookup"><span data-stu-id="a073e-115">Mining Structure Tasks and How-tos</span></span>](mining-structure-tasks-and-how-tos.md)  
  
## <a name="mining-models-tab"></a><span data-ttu-id="a073e-116">[マイニング モデル] タブ</span><span class="sxs-lookup"><span data-stu-id="a073e-116">Mining Models Tab</span></span>  
 <span data-ttu-id="a073e-117">**[マイニング モデル]** タブを使用すると、既存のマイニング モデルを管理したり、新しいモデルを作成したりできます。</span><span class="sxs-lookup"><span data-stu-id="a073e-117">Use the **Mining Models** tab to manage existing mining models and to create new models.</span></span> <span data-ttu-id="a073e-118">マイニング モデルは、常に既存のマイニング構造に基づきます。</span><span class="sxs-lookup"><span data-stu-id="a073e-118">Mining models are always based on an existing mining structure .</span></span>  
  
 <span data-ttu-id="a073e-119">**[マイニング モデル]** タブでは、アルゴリズムの種類の変更、モデル構造に関連付けられている列の追加または削除、アルゴリズム固有の列プロパティの調整、マイニング モデル列の使用法の指定、およびマイニング モデルに関連付けられているアルゴリズム パラメーターの調整を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="a073e-119">In the **Mining Models** tab, you can change the algorithm type, add or remove columns that are associated with the model structure, adjust algorithm-specific column properties, specify the mining model column usage, and adjust algorithm parameters that are associated with the mining model.</span></span> <span data-ttu-id="a073e-120">また、マイニング構造は、選択したモデルまたは関連付けられているすべてのモデルと共に処理することもできます。</span><span class="sxs-lookup"><span data-stu-id="a073e-120">You can also process the mining structure together with selected models or with all the associated models.</span></span>  
  
 <span data-ttu-id="a073e-121">マイニング モデルの操作の詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="a073e-121">See the following topics for more information about working with mining models:</span></span>  
  
 [<span data-ttu-id="a073e-122">マイニング モデル (Analysis Services - データ マイニング)</span><span class="sxs-lookup"><span data-stu-id="a073e-122">Mining Models &#40;Analysis Services - Data Mining&#41;</span></span>](mining-models-analysis-services-data-mining.md)  
  
 [<span data-ttu-id="a073e-123">マイニング モデル タスクと操作方法</span><span class="sxs-lookup"><span data-stu-id="a073e-123">Mining Model Tasks and How-tos</span></span>](mining-model-tasks-and-how-tos.md)  
  
## <a name="mining-model-viewer-tab"></a><span data-ttu-id="a073e-124">[マイニング モデル ビューアー] タブ</span><span class="sxs-lookup"><span data-stu-id="a073e-124">Mining Model Viewer Tab</span></span>  
 <span data-ttu-id="a073e-125">**[マイニング モデル ビューアー]** タブは、マイニング モデルを視覚的に調べるときに使用します。</span><span class="sxs-lookup"><span data-stu-id="a073e-125">Use the **Mining Model Viewer** tab to visually explore your mining models.</span></span> <span data-ttu-id="a073e-126">各マイニング モデルは、そのモデルに固有のコンテンツを表示するカスタム ビューアーに関連付けられています。</span><span class="sxs-lookup"><span data-stu-id="a073e-126">Each mining model is associated with a custom viewer that displays content that is specific to that model.</span></span> <span data-ttu-id="a073e-127">また、コンテンツ ビューアーを使用して、マイニング モデル コンテンツを表示することもできます。</span><span class="sxs-lookup"><span data-stu-id="a073e-127">You can also view mining model content by using the content viewer.</span></span>  
  
 <span data-ttu-id="a073e-128">データ マイニング ビューアーを使用したマイニング モデルの調査の詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="a073e-128">See the following topics for more information about exploring mining models with the data mining viewers:</span></span>  
  
 [<span data-ttu-id="a073e-129">データ マイニング モデル ビューアー</span><span class="sxs-lookup"><span data-stu-id="a073e-129">Data Mining Model Viewers</span></span>](data-mining-model-viewers.md)  
  
 [<span data-ttu-id="a073e-130">マイニング モデル ビューアーのタスクと操作方法</span><span class="sxs-lookup"><span data-stu-id="a073e-130">Mining Model Viewer Tasks and How-tos</span></span>](mining-model-viewer-tasks-and-how-tos.md)  
  
## <a name="mining-accuracy-chart-tab"></a><span data-ttu-id="a073e-131">[マイニング精度チャート] タブ</span><span class="sxs-lookup"><span data-stu-id="a073e-131">Mining Accuracy Chart Tab</span></span>  
 <span data-ttu-id="a073e-132">**[マイニング精度チャート]** タブは、1 つのマイニング モデルの予測精度をテストしたり、マイニング構造内に含まれている複数のマイニング モデルの効果を比較したりするときに使用します。</span><span class="sxs-lookup"><span data-stu-id="a073e-132">Use the **Mining Accuracy Chart** tab to test the predictive accuracy of a single mining model, or to compare the effectiveness of multiple mining models contained within a mining structure.</span></span> <span data-ttu-id="a073e-133">このタブには、データのフィルター選択、マイニング モデルの選択、およびリフト チャート、利益チャート、または分類マトリックスへの結果の表示を行うためのツールがあります。</span><span class="sxs-lookup"><span data-stu-id="a073e-133">The tab contains tools for filtering the data, selecting mining models, and displaying the results in a lift chart, profit chart, or classification matrix.</span></span>  
  
 <span data-ttu-id="a073e-134">マイニング モデルのテストおよび検証の詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="a073e-134">See the following topics for more information about testing and validating mining models:</span></span>  
  
 [<span data-ttu-id="a073e-135">テストおよび検証 &#40;データ マイニング&#41;</span><span class="sxs-lookup"><span data-stu-id="a073e-135">Testing and Validation &#40;Data Mining&#41;</span></span>](testing-and-validation-data-mining.md)  
  
 [<span data-ttu-id="a073e-136">テストおよび検証タスク、および操作方法 (データ マイニング)</span><span class="sxs-lookup"><span data-stu-id="a073e-136">Testing and Validation Tasks and How-tos &#40;Data Mining&#41;</span></span>](testing-and-validation-tasks-and-how-tos-data-mining.md)  
  
## <a name="mining-model-prediction-tab"></a><span data-ttu-id="a073e-137">[マイニング モデル予測] タブ</span><span class="sxs-lookup"><span data-stu-id="a073e-137">Mining Model Prediction Tab</span></span>  
 <span data-ttu-id="a073e-138">**[マイニング モデル予測]** タブには予測クエリ ビルダーがあり、これを使用してデータ マイニング拡張機能 (DMX) の予測クエリを作成できます。</span><span class="sxs-lookup"><span data-stu-id="a073e-138">The **Mining Model Prediction** tab includes Prediction Query Builder, which you can use to create a Data Mining Extensions (DMX) prediction query.</span></span> <span data-ttu-id="a073e-139">このタブには、マイニング モデルと入力テーブルの指定、入力テーブル内の列へのマイニング モデル内の列のマッピング、クエリへの機能の追加、および各列の条件の指定を行うためのツールがあります。</span><span class="sxs-lookup"><span data-stu-id="a073e-139">The tab contains tools for specifying mining models and input tables, mapping the columns in the mining model to columns in the input table, adding functions to a query, and specifying criteria for each column.</span></span>  
  
 <span data-ttu-id="a073e-140">クエリをデザインした後、タブのさまざまなビューを使用して、クエリの結果を表示したり、クエリを手動で変更したりできます。</span><span class="sxs-lookup"><span data-stu-id="a073e-140">After you design a query, you can use different views in the tab to display the results of the query and to modify the query manually.</span></span> <span data-ttu-id="a073e-141">また、クエリの結果をデータベースのテーブルに保存することもできます。</span><span class="sxs-lookup"><span data-stu-id="a073e-141">You can also save the results of the query to a table in a database.</span></span>  
  
 <span data-ttu-id="a073e-142">データ マイニング クエリの作成の詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="a073e-142">See the following topics for more information about creating data mining queries:</span></span>  
  
 [<span data-ttu-id="a073e-143">データマイニングクエリ</span><span class="sxs-lookup"><span data-stu-id="a073e-143">Data Mining Queries</span></span>](data-mining-queries.md)  
  
 [<span data-ttu-id="a073e-144">データ マイニングのクエリ タスクと操作方法</span><span class="sxs-lookup"><span data-stu-id="a073e-144">Data Mining Query Tasks and How-tos</span></span>](data-mining-query-tasks-and-how-tos.md)  
  
## <a name="see-also"></a><span data-ttu-id="a073e-145">参照</span><span class="sxs-lookup"><span data-stu-id="a073e-145">See Also</span></span>  
 [<span data-ttu-id="a073e-146">データ マイニング ソリューション</span><span class="sxs-lookup"><span data-stu-id="a073e-146">Data Mining Solutions</span></span>](data-mining-solutions.md)  
  
  
