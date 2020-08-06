---
title: データマイニング (SSAS) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data mining [Analysis Services], about data mining
ms.assetid: b1c912da-72f6-4d96-89c8-55a2c4f19e88
author: minewiskan
ms.author: owend
ms.openlocfilehash: 7044ee397d457f7924d0db99dbec6659f969f104
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643637"
---
# <a name="data-mining-ssas"></a><span data-ttu-id="680a6-102">データ マイニング (SSAS)</span><span class="sxs-lookup"><span data-stu-id="680a6-102">Data Mining (SSAS)</span></span>
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="680a6-103">は、データ マイニングを取り入れたソリューションのための統合プラットフォームを提供します。</span><span class="sxs-lookup"><span data-stu-id="680a6-103">provides an integrated platform for solutions that incorporate data mining.</span></span> <span data-ttu-id="680a6-104">リレーショナル データまたはキューブ データを使用して、予測分析を含むビジネス インテリジェンス ソリューションを作成できます。</span><span class="sxs-lookup"><span data-stu-id="680a6-104">You can use either relational or cube data to create business intelligence solutions with predictive analytics.</span></span>  
  
## <a name="benefits-of-data-mining"></a><span data-ttu-id="680a6-105">データ マイニングの利点</span><span class="sxs-lookup"><span data-stu-id="680a6-105">Benefits of Data Mining</span></span>  
 <span data-ttu-id="680a6-106">データ マイニングでは、詳細な研究に基づいた統計原則を使用してデータ内のパターンを検出します。複雑な問題に関して合理的な意思決定を行う場合に、この情報を役立てることができます。</span><span class="sxs-lookup"><span data-stu-id="680a6-106">Data mining uses well-researched statistical principles to discover patterns in your data, helping you make intelligent decisions about complex problems.</span></span> <span data-ttu-id="680a6-107">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のデータ マイニング アルゴリズムをデータに適用することにより、傾向の予測、パターンの識別、およびルールや提案の作成を行い、複雑なデータ セット内でイベントの順序を分析し、新しい見識を得ることができます。</span><span class="sxs-lookup"><span data-stu-id="680a6-107">By applying the data mining algorithms in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] to your data, you can forecast trends, identify patterns, create rules and recommendations, analyze the sequence of events in complex data sets, and gain new insights.</span></span>  
  
 <span data-ttu-id="680a6-108">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]のデータ マイニングは、強力でありながら使いやすく、分析用やレポート作成用として多くの人に使用されているツールに統合されています。</span><span class="sxs-lookup"><span data-stu-id="680a6-108">In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], data mining is powerful, accessible, and integrated with the tools that many people prefer to use for analysis and reporting.</span></span> <span data-ttu-id="680a6-109">データ マイニングの使用を開始するために必要な全体像を把握するには、このセクションのリンクを参照してください。</span><span class="sxs-lookup"><span data-stu-id="680a6-109">See the links in this section to get the broad background about data mining that you need to get started.</span></span>  
  
## <a name="key-data-mining-features"></a><span data-ttu-id="680a6-110">データ マイニングの主要機能</span><span class="sxs-lookup"><span data-stu-id="680a6-110">Key Data Mining Features</span></span>  
 <span data-ttu-id="680a6-111">SQL Server では、統合データ マイニング ソリューションをサポートするために次の機能が提供されています。</span><span class="sxs-lookup"><span data-stu-id="680a6-111">SQL Server provides the following features in support of integrated data mining solutions:</span></span>  
  
-   <span data-ttu-id="680a6-112">複数のデータ ソース: データ マイニングを行うためにデータ ウェアハウスや OLAP キューブを作成する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="680a6-112">Multiple data sources: You do not have to create a data warehouse or an OLAP cube to do data mining.</span></span> <span data-ttu-id="680a6-113">外部プロバイダー、スプレッドシート、テキスト ファイルから、表形式のデータを使用できます。</span><span class="sxs-lookup"><span data-stu-id="680a6-113">You can use tabular data from external providers, spreadsheets, and even text files.</span></span> <span data-ttu-id="680a6-114">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]で作成した OLAP キューブを簡単にマイニングすることもできます。</span><span class="sxs-lookup"><span data-stu-id="680a6-114">You can also easily mine OLAP cubes created in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="680a6-115">ただし、インメモリ データベースからのデータは使用できません。</span><span class="sxs-lookup"><span data-stu-id="680a6-115">However, you cannot use data from an in-memory database.</span></span>  
  
-   <span data-ttu-id="680a6-116">統合されたデータ クレンジング、データ管理、および ETL: データのプロファイリングおよびクレンジングのための高度なツールが Data Quality Services によって提供されます。</span><span class="sxs-lookup"><span data-stu-id="680a6-116">Integrated data cleansing, data management, and ETL: Data Quality Services provides advanced tools for profiling and cleansing data.</span></span> <span data-ttu-id="680a6-117">Integration Services を使用して、データのクレンジングおよびモデルの構築、処理、トレーニング、および更新のために、ETL プロセスを構築できます。</span><span class="sxs-lookup"><span data-stu-id="680a6-117">Integration Services can be used to build ETL processes for cleaning data, and also for building, processing, training, and updating models.</span></span>  
  
-   <span data-ttu-id="680a6-118">複数のカスタマイズ可能なアルゴリズム: クラスタリング、ニューラル ネットワーク、デシジョン ツリーなどのアルゴリズムの提供に加え、このプラットフォームは、独自のカスタム プラグイン アルゴリズムの開発をサポートします。</span><span class="sxs-lookup"><span data-stu-id="680a6-118">Multiple customizable algorithms: In addition to providing algorithms such as clustering, neural networks, and decisions trees, the platform supports development of your own custom plug-in algorithms.</span></span>  
  
-   <span data-ttu-id="680a6-119">モデル テスト用インフラストラクチャ: 相互検証、分類マトリックス、リフト チャート、散布図などの重要な統計ツールを使用して、モデルおよびデータ セットをテストできます。</span><span class="sxs-lookup"><span data-stu-id="680a6-119">Model testing infrastructure: Test your models and data sets using important statistical tools as cross-validation, classification matrices, lift charts, and scatter plots.</span></span> <span data-ttu-id="680a6-120">テストおよびトレーニングのセットを容易に作成および管理できます。</span><span class="sxs-lookup"><span data-stu-id="680a6-120">Easily create and manage testing and training sets.</span></span>  
  
-   <span data-ttu-id="680a6-121">クエリおよびドリルスルー: 予測クエリを作成し、モデルのパターンおよび統計情報を取得し、ケース データにドリルスルーします。</span><span class="sxs-lookup"><span data-stu-id="680a6-121">Querying and drillthrough: Create prediction queries, retrieve model patterns and statistics, and drill through to case data.</span></span>  
  
-   <span data-ttu-id="680a6-122">クライアント ツール: SQL Server で提供される開発および設計スタジオに加え、Excel 用データ マイニング アドインを使用して、モデルの作成、照会、および参照を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="680a6-122">Client tools: In addition to the development and design studios provided by SQL Server, you can use the Data Mining Add-ins for Excel to create, query, and browse models.</span></span> <span data-ttu-id="680a6-123">Web サービスなど、カスタムのクライアントを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="680a6-123">Or, create custom clients, including Web services.</span></span>  
  
-   <span data-ttu-id="680a6-124">スクリプト言語サポートとマネージド API: データ マイニング オブジェクトはすべて、プログラム可能です。</span><span class="sxs-lookup"><span data-stu-id="680a6-124">Scripting language support and managed API: All data mining objects are fully programmable.</span></span> <span data-ttu-id="680a6-125">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]用の MDX 拡張機能、XMLA 拡張機能、または、PowerShell 拡張機能により、スクリプトの作成が可能です。</span><span class="sxs-lookup"><span data-stu-id="680a6-125">Scripting is possible through MDX, XMLA, or the PowerShell extensions for [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="680a6-126">データ マイニング拡張機能 (DMX) 言語を使用すると、クエリとスクリプト作成を迅速に行うことができます。</span><span class="sxs-lookup"><span data-stu-id="680a6-126">Use the Data Mining Extensions (DMX) language for fast querying and scripting.</span></span>  
  
-   <span data-ttu-id="680a6-127">セキュリティおよび配置: [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]により、ロール ベースのセキュリティが提供されます (モデルと構造データへのドリルスルーに、別々の権限を使用できるなど)。</span><span class="sxs-lookup"><span data-stu-id="680a6-127">Security and deployment: Provides role-based security through [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], including separate permissions for drillthrough to model and structure data.</span></span> <span data-ttu-id="680a6-128">他のサーバーへのモデルの配置が容易であるため、ユーザーがパターンにアクセスし、予測を実行することが可能になります。</span><span class="sxs-lookup"><span data-stu-id="680a6-128">Easy deployment of models to other servers, so that users can access the patterns or perform predictions</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="680a6-129">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="680a6-129">In This Section</span></span>  
 <span data-ttu-id="680a6-130">このセクションのトピックでは、SQL Server データ マイニングの主要機能および関連タスクについて説明します。</span><span class="sxs-lookup"><span data-stu-id="680a6-130">The topics in this section introduce the principal features of SQL Server Data Mining and related tasks.</span></span>  
  
-   [<span data-ttu-id="680a6-131">データマイニングの概念</span><span class="sxs-lookup"><span data-stu-id="680a6-131">Data Mining Concepts</span></span>](data-mining-concepts.md)  
  
-   [<span data-ttu-id="680a6-132">データ マイニング アルゴリズム &#40;Analysis Services - データ マイニング&#41;</span><span class="sxs-lookup"><span data-stu-id="680a6-132">Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;</span></span>](data-mining-algorithms-analysis-services-data-mining.md)  
  
-   [<span data-ttu-id="680a6-133">マイニング構造 (Analysis Services - データ マイニング)</span><span class="sxs-lookup"><span data-stu-id="680a6-133">Mining Structures &#40;Analysis Services - Data Mining&#41;</span></span>](mining-structures-analysis-services-data-mining.md)  
  
-   [<span data-ttu-id="680a6-134">マイニング モデル (Analysis Services - データ マイニング)</span><span class="sxs-lookup"><span data-stu-id="680a6-134">Mining Models &#40;Analysis Services - Data Mining&#41;</span></span>](mining-models-analysis-services-data-mining.md)  
  
-   [<span data-ttu-id="680a6-135">テストおよび検証 &#40;データ マイニング&#41;</span><span class="sxs-lookup"><span data-stu-id="680a6-135">Testing and Validation &#40;Data Mining&#41;</span></span>](testing-and-validation-data-mining.md)  
  
-   [<span data-ttu-id="680a6-136">データマイニングクエリ</span><span class="sxs-lookup"><span data-stu-id="680a6-136">Data Mining Queries</span></span>](data-mining-queries.md)  
  
-   [<span data-ttu-id="680a6-137">データ マイニング ソリューション</span><span class="sxs-lookup"><span data-stu-id="680a6-137">Data Mining Solutions</span></span>](data-mining-solutions.md)  
  
-   [<span data-ttu-id="680a6-138">データ マイニング ツール</span><span class="sxs-lookup"><span data-stu-id="680a6-138">Data Mining Tools</span></span>](data-mining-tools.md)  
  
-   [<span data-ttu-id="680a6-139">データ マイニングのアーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="680a6-139">Data Mining Architecture</span></span>](data-mining-architecture.md)  
  
-   [<span data-ttu-id="680a6-140">セキュリティの概要 &#40;データ マイニング&#41;</span><span class="sxs-lookup"><span data-stu-id="680a6-140">Security Overview &#40;Data Mining&#41;</span></span>](security-overview-data-mining.md)  
  
  
