---
title: データマイニングツール |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- tools [Analysis Services]
- mining models [Analysis Services], tools
- data mining [Analysis Services], tools
- data mining [Analysis Services], development
ms.assetid: 003ada6a-0bcd-4f16-8c34-1a9ffc75cd2c
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4be2f343f0fb7969f76b63ec1eb1677c1c9e589f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645925"
---
# <a name="data-mining-tools"></a><span data-ttu-id="ed64e-102">データ マイニング ツール</span><span class="sxs-lookup"><span data-stu-id="ed64e-102">Data Mining Tools</span></span>
  [!INCLUDE[msCoName](../../includes/msconame-md.md)]<span data-ttu-id="ed64e-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] には、データマイニングソリューションの作成に使用できる次のツールが用意されています。</span><span class="sxs-lookup"><span data-stu-id="ed64e-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] provides the following tools that you can use to create data mining solutions:</span></span>  
  
-   <span data-ttu-id="ed64e-104">**では、** データ マイニング ウィザード [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] によって、リレーショナル データ ソースまたはキューブの多次元データを使用して、マイニング構造およびマイニング モデルを簡単に作成できます。</span><span class="sxs-lookup"><span data-stu-id="ed64e-104">The **Data Mining Wizard** in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] makes it easy to create mining structures and mining models, using either relational data sources or multidimensional data in cubes.</span></span>  
  
     <span data-ttu-id="ed64e-105">このウィザードでは、使用するデータを選択してから、クラスタリング、ニューラル ネットワーク、タイム シリーズ モデルなど、特定のデータ マイニング技法を適用します。</span><span class="sxs-lookup"><span data-stu-id="ed64e-105">In the wizard, you choose data to use, and then apply specific data mining techniques, such as clustering, neural networks, or time series modeling.</span></span>  
  
-   <span data-ttu-id="ed64e-106">**と** の両方では、マイニング モデルを作成した後で調べるために [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] モデル ビューアー [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]が提供されます。</span><span class="sxs-lookup"><span data-stu-id="ed64e-106">**Model viewers** are provided in both [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], for exploring your mining models after they are created.</span></span>  <span data-ttu-id="ed64e-107">各アルゴリズムに合わせて調整されたビューアーを使用してモデルを参照したり、モデル コンテンツ ビューアーを使用して詳しい分析を行ったりすることができます。</span><span class="sxs-lookup"><span data-stu-id="ed64e-107">You can browse models using viewers tailored to each algorithm, or go deeper into analysis by using the model content viewer.</span></span>  
  
-   <span data-ttu-id="ed64e-108">**と** の両方では、予測クエリを作成するために [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 予測クエリ ビルダー [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] が提供されます。</span><span class="sxs-lookup"><span data-stu-id="ed64e-108">The **Prediction Query Builder** is provided in both [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] to help you create prediction queries.</span></span> <span data-ttu-id="ed64e-109">また、予約データセットまたは外部データに対してモデルの精度をテストしたり、クロス検証を使用してデータセットの品質を調査したりすることもできます。</span><span class="sxs-lookup"><span data-stu-id="ed64e-109">You can also test the accuracy of models against a holdout data set or external data, or use cross-validation to assess the quality of your data set.</span></span>  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="ed64e-110">は、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]のインスタンスに配置された既存のデータ マイニング ソリューションを管理するためのインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="ed64e-110">is the interface where you manage existing data mining solutions that have been deployed to an instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="ed64e-111">構造とモデルを再処理して、データを更新することができます。</span><span class="sxs-lookup"><span data-stu-id="ed64e-111">You can reprocess structures and models to update the data in them.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="ed64e-112">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]には、データのクリーンアップ、予測の作成やモデルの更新、テキストマイニングソリューションの作成などのタスクを自動化するために使用できるツールが含まれています。</span><span class="sxs-lookup"><span data-stu-id="ed64e-112">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] contains tools that you can use to clean data, to automate tasks such as creating predictions and updating models, and to create text mining solutions.</span></span>  
  
 <span data-ttu-id="ed64e-113">次のセクションでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のデータ マイニング ツールの詳細について説明します。</span><span class="sxs-lookup"><span data-stu-id="ed64e-113">The following sections provide more information about the data mining tools in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="data-mining-wizard"></a><span data-ttu-id="ed64e-114">では、</span><span class="sxs-lookup"><span data-stu-id="ed64e-114">Data Mining Wizard</span></span>  
 <span data-ttu-id="ed64e-115">データ マイニング ウィザードを使用して、データ マイニング ソリューションの作成を開始します。</span><span class="sxs-lookup"><span data-stu-id="ed64e-115">Use the Data Mining Wizard to get started creating data mining solutions.</span></span> <span data-ttu-id="ed64e-116">このウィザードはすぐに簡単に使用でき、データ マイニング構造および初期関連マイニング モデルを順を追って作成する方法が示されます。また、アルゴリズムの種類やデータ ソースの選択と、分析に使用されるケース データの定義も行うことができます。</span><span class="sxs-lookup"><span data-stu-id="ed64e-116">The wizard is quick and easy, and guides you through the process of creating a data mining structure and an initial related mining model, and includes the tasks of selecting an algorithm type and a data source, and defining the case data used for analysis.</span></span>  
  
 <span data-ttu-id="ed64e-117">**詳細:** [データ マイニング ウィザード (Analysis Services - データ マイニング)](data-mining-wizard-analysis-services-data-mining.md)</span><span class="sxs-lookup"><span data-stu-id="ed64e-117">**For More Information:** [Data Mining Wizard &#40;Analysis Services - Data Mining&#41;](data-mining-wizard-analysis-services-data-mining.md)</span></span>  
  
## <a name="data-mining-designer"></a><span data-ttu-id="ed64e-118">Data Mining Designer</span><span class="sxs-lookup"><span data-stu-id="ed64e-118">Data Mining Designer</span></span>  
 <span data-ttu-id="ed64e-119">データ マイニング ウィザードを使用してマイニング構造およびマイニング モデルを作成したら、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] のデータ マイニング デザイナーを使用して、既存のモデルと構造に対する操作を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="ed64e-119">After you have created a mining structure and mining model by using the Data Mining Wizard, you can use the Data Mining Designer from either [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] or [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to work with existing models and structures.</span></span>  
  
 <span data-ttu-id="ed64e-120">デザイナーには次のタスクのためのツールが含まれます。</span><span class="sxs-lookup"><span data-stu-id="ed64e-120">The designer includes tools for these tasks:</span></span>  
  
-   <span data-ttu-id="ed64e-121">マイニング構造のプロパティの変更、列の追加、列の別名の作成、ビン分割方法または予想される値分布の変更。</span><span class="sxs-lookup"><span data-stu-id="ed64e-121">Modify the properties of mining structures, add columns and create column aliases, change the binning method or expected distribution of values.</span></span>  
  
-   <span data-ttu-id="ed64e-122">既存の構造への新しいモデルの追加。モデルのコピー、モデル プロパティまたはメタデータの変更、またはマイニング モデルへのフィルターの定義。</span><span class="sxs-lookup"><span data-stu-id="ed64e-122">Add new models to an existing structure; copy models, change model properties or metadata, or define filters on a mining model.</span></span>  
  
-   <span data-ttu-id="ed64e-123">モデル内のパターンとルールの参照。関連付けまたはデシジョン ツリーの調査。</span><span class="sxs-lookup"><span data-stu-id="ed64e-123">Browse the patterns and rules within the model; explore associations or decision trees.</span></span> <span data-ttu-id="ed64e-124">詳細な統計情報の取得。</span><span class="sxs-lookup"><span data-stu-id="ed64e-124">Get detailed statistics about</span></span>  
  
     <span data-ttu-id="ed64e-125">データの分析や、データ マイニングで明らかになるパターンの調査のために、各種のモデルに対してカスタム ビューアーが提供されます。</span><span class="sxs-lookup"><span data-stu-id="ed64e-125">Custom viewers are provided for each different time of model, to help you analyze your data and explore the patterns revealed by data mining.</span></span>  
  
-   <span data-ttu-id="ed64e-126">リフト チャートの作成またはモデルの利益曲線の分析による、モデルの検証。</span><span class="sxs-lookup"><span data-stu-id="ed64e-126">Validate models by creating lift charts, or analyzing the profit curve for models.</span></span> <span data-ttu-id="ed64e-127">分類マトリックスを使用したモデルの比較、またはクロス検証を使用したデータセットとモデルの検証。</span><span class="sxs-lookup"><span data-stu-id="ed64e-127">Compare models using classification matrices, or validate a data set and its models by using cross-validation.</span></span>  
  
-   <span data-ttu-id="ed64e-128">既存のマイニング モデルに対する予測とコンテンツ クエリの作成。</span><span class="sxs-lookup"><span data-stu-id="ed64e-128">Create predictions and content queries against existing mining models.</span></span> <span data-ttu-id="ed64e-129">1 回限りのクエリの作成、または外部データのテーブル全体の予測を生成するクエリの設定。</span><span class="sxs-lookup"><span data-stu-id="ed64e-129">Build one-off queries, or set up queries to generate predictions for entire tables of external data.</span></span>  
  
 <span data-ttu-id="ed64e-130">**詳細については、「** [データマイニングデザイナー](data-mining-designer.md) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ed64e-130">**For More Information:** [Data Mining Designer](data-mining-designer.md)</span></span>  
  
## <a name="sql-server-management-studio"></a><span data-ttu-id="ed64e-131">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ed64e-131">SQL Server Management Studio</span></span>  
 <span data-ttu-id="ed64e-132">マイニング モデルを作成してサーバーに配置したら、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して、データ マイニング オブジェクトをホストする [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースを管理できます。</span><span class="sxs-lookup"><span data-stu-id="ed64e-132">After you create and deploy mining models to a server, you can use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to manage the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database that hosts the data mining objects.</span></span> <span data-ttu-id="ed64e-133">また、モデルの調査、新しいデータの処理、予測の作成など、モデルを使用するタスクの実行を続けることもできます。</span><span class="sxs-lookup"><span data-stu-id="ed64e-133">You can also continue to perform tasks that use the model, such as exploring the models, processing new data, and creating predictions.</span></span>  
  
 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] <span data-ttu-id="ed64e-134">にはクエリ エディターも含まれ、データ マイニング拡張機能 (DMX) クエリの設計と実行や、XMLA を使用するデータ マイニング オブジェクトの操作に使用できます。</span><span class="sxs-lookup"><span data-stu-id="ed64e-134">also contains query editors that you can use to design and execute Data Mining Extensions (DMX) queries, or ot work with data mining objects by using XMLA.</span></span>  
  
## <a name="integration-services-data-mining-tasks-and-transformations"></a><span data-ttu-id="ed64e-135">Integration Services のデータ マイニング タスクおよび変換</span><span class="sxs-lookup"><span data-stu-id="ed64e-135">Integration Services Data Mining Tasks and Transformations</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="ed64e-136">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]には、データマイニングをサポートする多くのコンポーネントが用意されています。</span><span class="sxs-lookup"><span data-stu-id="ed64e-136">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] provides many components that support data mining.</span></span>  
  
 <span data-ttu-id="ed64e-137">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] には、一般的なデータ マイニング タスク (予測、モデル作成、処理など) を自動化するためのツールが含まれます。</span><span class="sxs-lookup"><span data-stu-id="ed64e-137">Some tools in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] are designed to help automate common data mining tasks, including prediction, model building, and processing.</span></span> <span data-ttu-id="ed64e-138">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="ed64e-138">For example:</span></span>  
  
-   <span data-ttu-id="ed64e-139">新しい顧客によってデータセットが更新されるたびに自動的にモデルを更新する、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージの作成。</span><span class="sxs-lookup"><span data-stu-id="ed64e-139">Create an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that automatically updates the model every time the dataset is updated with new customers</span></span>  
  
-   <span data-ttu-id="ed64e-140">ケース レコードのカスタム分割またはカスタム サンプリングの実行。</span><span class="sxs-lookup"><span data-stu-id="ed64e-140">Perform custom segmentation or custom sampling of case records.</span></span>  
  
-   <span data-ttu-id="ed64e-141">パラメーターで渡されたモデルの自動生成。</span><span class="sxs-lookup"><span data-stu-id="ed64e-141">Automatically generate models passed on parameters.</span></span>  
  
 <span data-ttu-id="ed64e-142">ただし、他のプロセスへの入力として、パッケージ ワークフローのデータ マイニングを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="ed64e-142">However, you can also use data mining in a package workflow, as an input to other processes.</span></span> <span data-ttu-id="ed64e-143">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="ed64e-143">For example:</span></span>  
  
-   <span data-ttu-id="ed64e-144">モデルで生成された確率値の使用。テキスト マイニングまたは他の分類タスクのスコアを重み付けします。</span><span class="sxs-lookup"><span data-stu-id="ed64e-144">Use probability values generated by the model to weight scores for text mining or other classification tasks.</span></span>  
  
-   <span data-ttu-id="ed64e-145">前のデータに基づく予測の自動生成、およびそれらの値を使用した新しいデータの有効性の調査。</span><span class="sxs-lookup"><span data-stu-id="ed64e-145">Automatically generate predictions based on prior data and use those values to assess the validity of new data.</span></span>  
  
-   <span data-ttu-id="ed64e-146">新たな顧客をリスク別にセグメント化する、ロジスティック回帰の使用。</span><span class="sxs-lookup"><span data-stu-id="ed64e-146">Using logistic regression to segment incoming customers by risk.</span></span>  
  
 <span data-ttu-id="ed64e-147">**詳細:** [データ マイニング ソリューションの関連プロジェクト](data-mining-solutions.md)</span><span class="sxs-lookup"><span data-stu-id="ed64e-147">**For More Information:** [Related Projects for Data Mining Solutions](data-mining-solutions.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed64e-148">参照</span><span class="sxs-lookup"><span data-stu-id="ed64e-148">See Also</span></span>  
 <span data-ttu-id="ed64e-149">[DMX&#41; リファレンス &#40;データマイニング拡張機能](/sql/dmx/data-mining-extensions-dmx-reference) </span><span class="sxs-lookup"><span data-stu-id="ed64e-149">[Data Mining Extensions &#40;DMX&#41; Reference](/sql/dmx/data-mining-extensions-dmx-reference) </span></span>  
 <span data-ttu-id="ed64e-150">[マイニングモデルタスクと操作方法](mining-model-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="ed64e-150">[Mining Model Tasks and How-tos](mining-model-tasks-and-how-tos.md) </span></span>  
 <span data-ttu-id="ed64e-151">[マイニングモデルビューアーのタスクと操作方法](mining-model-viewer-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="ed64e-151">[Mining Model Viewer Tasks and How-tos](mining-model-viewer-tasks-and-how-tos.md) </span></span>  
 [<span data-ttu-id="ed64e-152">データ マイニング ソリューション</span><span class="sxs-lookup"><span data-stu-id="ed64e-152">Data Mining Solutions</span></span>](data-mining-solutions.md)  
  
  
