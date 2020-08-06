---
title: Office 用データマイニングアドインの SQL Server |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: c9021a19-2c19-4f0a-a293-5f7e0ac2524c
author: minewiskan
ms.author: owend
ms.openlocfilehash: b64d0c8728e4752d0d5831562d43646e29f7d723
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631339"
---
# <a name="sql-server-data-mining-add-ins-for-office"></a><span data-ttu-id="2073e-102">Office 用 SQL Server データ マイニング アドイン</span><span class="sxs-lookup"><span data-stu-id="2073e-102">SQL Server Data Mining Add-Ins for Office</span></span>
  [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] <span data-ttu-id="2073e-103">Office 用データ マイニング アドインは、予測、推奨設定、または検索の分析モデルを構築するために Excel のデータを使用できるようにする軽量な一連の予測分析用ツールです。</span><span class="sxs-lookup"><span data-stu-id="2073e-103">Data Mining Add-ins for Office is a lightweight set of tools for predictive analytics that lets you use data in Excel to build analytical models for prediction, recommendation, or exploration.</span></span>  
  
 <span data-ttu-id="2073e-104">アドインのウィザードおよびデータ管理のツールでは、次の一般的なデータ マイニング タスクの実行手順を説明しています。</span><span class="sxs-lookup"><span data-stu-id="2073e-104">The wizards and data management tools in the add-ins provide step-by-step instruction for these common data mining tasks:</span></span>  
  
-   <span data-ttu-id="2073e-105">**モデリングの前のデータの整理とクレンジング。**</span><span class="sxs-lookup"><span data-stu-id="2073e-105">**Organize and clean your data prior to modeling.**</span></span> <span data-ttu-id="2073e-106">Excel またはあらゆる Excel データ ソースに格納されているデータを使用します。</span><span class="sxs-lookup"><span data-stu-id="2073e-106">Use data stored in Excel or any Excel data source.</span></span> <span data-ttu-id="2073e-107">データ ソースの再利用、実験の繰り返し、またはモデルの再トレーニングに利用する接続を作成して保存できます。</span><span class="sxs-lookup"><span data-stu-id="2073e-107">You can create and save connections to re-use data sources, repeat experiments, or re-train models.</span></span>  
  
-   <span data-ttu-id="2073e-108">**プロファイリング、サンプリング、および準備**</span><span class="sxs-lookup"><span data-stu-id="2073e-108">**Profile, sample, and prepare.**</span></span> <span data-ttu-id="2073e-109">多くの経験豊富なデータ マイニング担当者によれば、データ マイニング プロジェクトの 70 ～ 90% がデータの準備に費やされます。</span><span class="sxs-lookup"><span data-stu-id="2073e-109">Many experienced data miners say that as much as 70-90 percent of a data mining project is spent on data preparation.</span></span> <span data-ttu-id="2073e-110">アドインはこのタスクを高速化でき、Excel およびウィザードで視覚エフェクトを提供して、次の一般的なタスクを手助けします。</span><span class="sxs-lookup"><span data-stu-id="2073e-110">The add-ins can make this task go faster, by providing visualizations in Excel and wizards that help you with these common tasks:</span></span>  
  
    -   <span data-ttu-id="2073e-111">データをプロファイルし、その分布と特性を理解します。</span><span class="sxs-lookup"><span data-stu-id="2073e-111">Profile data and understand its distribution and characteristics.</span></span>  
  
    -   <span data-ttu-id="2073e-112">ランダム サンプリングまたはオーバーサンプリングによってトレーニング データ セットとテスト セットを作成します。</span><span class="sxs-lookup"><span data-stu-id="2073e-112">Create training and testing sets through random sampling or oversampling.</span></span>  
  
    -   <span data-ttu-id="2073e-113">外れ値を検出して、削除または置き換えます。</span><span class="sxs-lookup"><span data-stu-id="2073e-113">Find outliers and remove or replace them.</span></span>  
  
    -   <span data-ttu-id="2073e-114">データのラベルを変更して分析の質を高めます。</span><span class="sxs-lookup"><span data-stu-id="2073e-114">Re-label data to improve the quality of analysis.</span></span>  
  
-   <span data-ttu-id="2073e-115">**教師あり学習または教師なし学習によるパターンの分析。**</span><span class="sxs-lookup"><span data-stu-id="2073e-115">**Analyze patterns through supervised or unsupervised learning.**</span></span> <span data-ttu-id="2073e-116">ウィザードをクリックで進みながら、クラスター分析、マーケット バスケット分析、予測など最も一般的なデータ マイニング タスクを実行できます。</span><span class="sxs-lookup"><span data-stu-id="2073e-116">Click through friendly wizards to perform some of the most popular data mining tasks, including clustering analysis, market basket analysis, and forecasting.</span></span>  
  
     <span data-ttu-id="2073e-117">このアドインには、Naïve Bayes、ロジスティック回帰、クラスタリング、時系列、ニューラル ネットワークなど広く利用されている機械学習アルゴリズムが含まれています。</span><span class="sxs-lookup"><span data-stu-id="2073e-117">Among the well-known machine learning algorithms included in the add-ins are Naïve Bayes, logistic regression, clustering, time series, and neural networks.</span></span>  
  
     <span data-ttu-id="2073e-118">データ マイニングを初めて使用する場合は、予測クエリの構築に関するヘルプを **クエリ** ウィザードから入手できます。</span><span class="sxs-lookup"><span data-stu-id="2073e-118">If you are new to data mining, get help building prediction queries from the **Query** wizard.</span></span>  
  
     <span data-ttu-id="2073e-119">上級ユーザーの場合、 **詳細クエリ エディター**を使用したドラッグ アンド ドロップによるカスタムの DMX クエリ作成や、Excel VBA を使用した予測の自動化が可能です。</span><span class="sxs-lookup"><span data-stu-id="2073e-119">Advanced users can build custom DMX queries with the drag-and-drop **Advanced Query Editor**, or automate predictions using Excel VBA.</span></span>  
  
-   <span data-ttu-id="2073e-120">**ドキュメントと管理。**</span><span class="sxs-lookup"><span data-stu-id="2073e-120">**Document and manage.**</span></span> <span data-ttu-id="2073e-121">データセットを作成し、いくつかのモデルを構築したら、データとモデルパラメーターの統計サマリーを生成して、作業と洞察を文書化します。</span><span class="sxs-lookup"><span data-stu-id="2073e-121">After you've created a data set and built some models, document your work and your insights by generating a statistical summary of the data and model parameters.</span></span>  
  
-   <span data-ttu-id="2073e-122">**調査と視覚化。**</span><span class="sxs-lookup"><span data-stu-id="2073e-122">**Explore and visualize.**</span></span> <span data-ttu-id="2073e-123">データマイニングは、完全に自動化できるアクティビティではありません。結果を調査して理解し、意味のあるアクションを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2073e-123">Data mining is not an activity that can be fully automated - you need to explore and understand your results to take meaningful action.</span></span> <span data-ttu-id="2073e-124">アドインは、Excel の対話的ビューアー、モデル ダイアグラムをカスタマイズできる Visio テンプレート、追加のフィルタリングまたは修正のためにグラフとテーブルを Excel にエクスポートする機能を備えており、調査に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="2073e-124">The add-ins help you with exploration by providing interactive viewers in Excel, Visio templates that let you customize model diagrams, and the ability to export charts and tables to Excel for additional filtering or modification.</span></span>  
  
-   <span data-ttu-id="2073e-125">**配置と統合。**</span><span class="sxs-lookup"><span data-stu-id="2073e-125">**Deploy and integrate.**</span></span> <span data-ttu-id="2073e-126">有用なモデルを作成したら、モデルを運用環境に配置します。そのためには、管理ツールを使用して、実験用サーバーからの別のインスタンスにモデルをエクスポートし [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="2073e-126">When you've created a useful model, put your model into production, by using the management tools to export the model from your experimental server to another instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
     <span data-ttu-id="2073e-127">また、作成時のサーバー上にモデルを残したまま、トレーニング データを更新し、Integration Services または DMX スクリプトを使用して予測を実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="2073e-127">You can also leave the model on the server where you created it, but refresh the training data and run predictions using Integration Services or DMX scripts.</span></span>  
  
     <span data-ttu-id="2073e-128">パワー ユーザーには、サーバーに送信した XMLA および DMX ステートメントを表示できる **トレース** 機能が役立ちます。</span><span class="sxs-lookup"><span data-stu-id="2073e-128">Power users will appreciate the **Trace** functionality, that lets you see the XMLA and DMX statements sent to the server.</span></span>  
  
## <a name="getting-started"></a><span data-ttu-id="2073e-129">はじめに</span><span class="sxs-lookup"><span data-stu-id="2073e-129">Getting Started</span></span>  
 <span data-ttu-id="2073e-130">ツールの説明を読んでツールを設定するには、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="2073e-130">See these topics to learn about the tools and to get set up:</span></span>  
  
-   [<span data-ttu-id="2073e-131">Excel 用のデータマイニングクライアント &#40;SQL Server データマイニングアドイン&#41;</span><span class="sxs-lookup"><span data-stu-id="2073e-131">Data Mining Client for Excel &#40;SQL Server Data Mining Add-ins&#41;</span></span>](../data-mining-client-for-excel-sql-server-data-mining-add-ins.md)  
  
-   [<span data-ttu-id="2073e-132">Excel 用テーブル分析ツール</span><span class="sxs-lookup"><span data-stu-id="2073e-132">Table Analysis Tools for Excel</span></span>](../table-analysis-tools-for-excel.md)  
  
-   [<span data-ttu-id="2073e-133">Visio 用のデータ マイニング図形</span><span class="sxs-lookup"><span data-stu-id="2073e-133">Data Mining Shapes for Visio</span></span>](../data-mining-shapes-for-visio.md)  
  
-   [<span data-ttu-id="2073e-134">データ マイニング サーバーへの接続</span><span class="sxs-lookup"><span data-stu-id="2073e-134">Connect to a Data Mining Server</span></span>](../connect-to-a-data-mining-server.md)  
  
## <a name="support-and-requirements"></a><span data-ttu-id="2073e-135">サポートと必要条件</span><span class="sxs-lookup"><span data-stu-id="2073e-135">Support and Requirements</span></span>  
 <span data-ttu-id="2073e-136">Office 用 SQL Server データ マイニング アドインは無料でダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="2073e-136">The SQL Server Data Mining Add-Ins for Office is a free download.</span></span> <span data-ttu-id="2073e-137">これらのツールを使用するには、次のいずれかのバージョンの Office が既にインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="2073e-137">You must have one of the following versions of Office already installed to use these tools:</span></span>  
  
-   <span data-ttu-id="2073e-138">Office 2010 (32 ビット版または 64 ビット版)</span><span class="sxs-lookup"><span data-stu-id="2073e-138">Office 2010, 32-bit or 64-bit version</span></span>  
  
-   <span data-ttu-id="2073e-139">Office 2013 (32 ビット版または 64 ビット版)</span><span class="sxs-lookup"><span data-stu-id="2073e-139">Office 2013, 32-bit or 64-bit version</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="2073e-140">現在の Excel のバージョンに対応するバージョンのアドインをダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="2073e-140">Be sure to download the version of the add-ins that matches your version of Excel.</span></span>  
  
 <span data-ttu-id="2073e-141">データ マイニング アドインを使用する場合は、以下のいずれかのエディションの SQL Server Analysis Services に接続する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2073e-141">The Data Mining Add-ins requires a connection to one of the following editions of SQL Server Analysis Services:</span></span>  
  
-   <span data-ttu-id="2073e-142">エンタープライズ</span><span class="sxs-lookup"><span data-stu-id="2073e-142">Enterprise</span></span>  
  
-   <span data-ttu-id="2073e-143">ビジネス インテリジェンス</span><span class="sxs-lookup"><span data-stu-id="2073e-143">Business Intelligence</span></span>  
  
-   <span data-ttu-id="2073e-144">Standard</span><span class="sxs-lookup"><span data-stu-id="2073e-144">Standard</span></span>  
  
 <span data-ttu-id="2073e-145">接続先の SQL Server Analysis Services のエディションによっては、高度なアルゴリズムの一部を使用できない場合があります。</span><span class="sxs-lookup"><span data-stu-id="2073e-145">Depending on the edition of SQL Server Analysis Services that you connect to, some of the advanced algorithms might not be available.</span></span> <span data-ttu-id="2073e-146">詳細については、「 [SQL Server 2014 の各エディションがサポートする機能](https://msdn.microsoft.com/library/cc645993.aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2073e-146">For information, see [Features Supported by the Editions of SQL Server 2014](https://msdn.microsoft.com/library/cc645993.aspx).</span></span>  
  
 <span data-ttu-id="2073e-147">インストールに関するその他のヘルプについては、ダウンロードセンターの次のページを参照してください。[https://www.microsoft.com/download/details.aspx?id=29061](https://www.microsoft.com/download/details.aspx?id=29061)</span><span class="sxs-lookup"><span data-stu-id="2073e-147">For additional help with installation, see this page on the Download Center: [https://www.microsoft.com/download/details.aspx?id=29061](https://www.microsoft.com/download/details.aspx?id=29061)</span></span>  
  
  
