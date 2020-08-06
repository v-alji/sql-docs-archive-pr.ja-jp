---
title: データマイニングソリューションの関連プロジェクト |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: dc26489a-4c27-4b89-8215-6d245427c350
author: minewiskan
ms.author: owend
ms.openlocfilehash: fc0f235871607363b436867d44affd561876bf1e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645257"
---
# <a name="related-projects-for-data-mining-solutions"></a><span data-ttu-id="bc014-102">データ マイニング ソリューションの関連プロジェクト</span><span class="sxs-lookup"><span data-stu-id="bc014-102">Related Projects for Data Mining Solutions</span></span>
  <span data-ttu-id="bc014-103">データ マイニング ソリューションに最低限必要なのは、データ ソース、データ ソース ビュー、マイニング構造、およびマイニング モデルを定義した、データ マイニング プロジェクトです。</span><span class="sxs-lookup"><span data-stu-id="bc014-103">The minimum that is required for a data mining solution is the data mining project, which defines data sources, data source views, mining structures and mining models.</span></span> <span data-ttu-id="bc014-104">ただし、データ マイニング モデルを日々の意志決定に使用する場合は、データ マイニングを予測分析ソリューションの他の部分と統合し、次のプロセスやコンポーネントを含めることが重要です。</span><span class="sxs-lookup"><span data-stu-id="bc014-104">However, when data mining models are used in daily decision making, it is important that data mining be integrated with other part of a predictive analytics solution, which can include these processes and components:</span></span>  
  
-   <span data-ttu-id="bc014-105">データと変数の準備および選択。</span><span class="sxs-lookup"><span data-stu-id="bc014-105">Preparation and selection of data and of variables.</span></span> <span data-ttu-id="bc014-106">データ クレンジング、複数のデータ ソースのメタデータ管理と統合のほか、データの変換、マージ、およびデータ ウェアハウスへのアップロードが含まれます。</span><span class="sxs-lookup"><span data-stu-id="bc014-106">Includes data cleansing, metadata management and integration of multiple data sources, and the conversion, merging, and uploading of data into a data warehouse.</span></span>  
  
-   <span data-ttu-id="bc014-107">分析のレポート、予測の提示、データ マイニング アクティビティの監査と追跡。</span><span class="sxs-lookup"><span data-stu-id="bc014-107">Reporting of analysis, presentation of predictions, and auditing/tracking of data mining activities.</span></span>  
  
-   <span data-ttu-id="bc014-108">多次元モデルまたはテーブル モデルを使用した、結果の調査。</span><span class="sxs-lookup"><span data-stu-id="bc014-108">Using multidimensional models or tabular models to explore findings.</span></span>  
  
-   <span data-ttu-id="bc014-109">データ マイニング ソリューションの強化による新しいデータのサポート、最新の分析に基づくサポート インフラストラクチャの変更。</span><span class="sxs-lookup"><span data-stu-id="bc014-109">Refinement of the data mining solution to support new data, or changes in the support infrastructure driven by current analysis.</span></span>  
  
 <span data-ttu-id="bc014-110">このトピックでは、データ準備とデータ マイニングのプロセスをサポートするため、または、分析と処理のためのツールを提供してユーザーをサポートするために、予測分析ソリューションに組み込まれることの多い [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] のその他の機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="bc014-110">This topic describes the other features of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] that are often part of a predictive analytics solution, either to support the processes of data preparation and data mining, or to support users by providing tools for analysis and action.</span></span>  
  
 [<span data-ttu-id="bc014-111">統合サービス</span><span class="sxs-lookup"><span data-stu-id="bc014-111">Integration Services</span></span>](#bkmk_SSIS)  
  
 [<span data-ttu-id="bc014-112">Reporting Services</span><span class="sxs-lookup"><span data-stu-id="bc014-112">Reporting Services</span></span>](#bkmk_SSRS)  
  
 [<span data-ttu-id="bc014-113">Data Quality Services</span><span class="sxs-lookup"><span data-stu-id="bc014-113">Data Quality Service</span></span>](#bkmk_DQSetc)  
  
 [<span data-ttu-id="bc014-114">フルテキスト検索</span><span class="sxs-lookup"><span data-stu-id="bc014-114">Full-Text Search</span></span>](#bkmk_FTSetc)  
  
 [<span data-ttu-id="bc014-115">セマンティック インデックスの作成</span><span class="sxs-lookup"><span data-stu-id="bc014-115">Semantic Indexing</span></span>](#bkmk_SemSearch)  
  
##  <a name="sql-server-integration-services"></a><a name="bkmk_SSIS"></a><span data-ttu-id="bc014-116">SQL Server Integration Services</span><span class="sxs-lookup"><span data-stu-id="bc014-116">SQL Server Integration Services</span></span>  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="bc014-117">には、データ マイニング プロジェクトのデータ準備とトレーニングのフェーズに必要なコンポーネントと機能が用意されています。</span><span class="sxs-lookup"><span data-stu-id="bc014-117">provides components and features that are required for the data preparation and training phases of a data mining project.</span></span> <span data-ttu-id="bc014-118">さまざまなデータ クレンジング タスクやデータ準備タスクには、スクリプトをはじめとする他のツールを使用することもできますが、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] には、データ マイニングに関して多数の利点があります。</span><span class="sxs-lookup"><span data-stu-id="bc014-118">Although you can perform many data cleansing or preparation tasks by using other tools, such as scripts, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] has numerous advantages for data mining:</span></span>  
  
-   <span data-ttu-id="bc014-119">繰り返し、自動化、分岐、および拡張が可能なワークフローの一部としてタスクを表現できます。</span><span class="sxs-lookup"><span data-stu-id="bc014-119">Represents tasks as part of a workflow, which can be repeated, automated, branched, and extended.</span></span>  
  
-   <span data-ttu-id="bc014-120">監査が幅広くサポートされており、複数の方法でエラーをキャプチャし、イベントをログに記録できます。</span><span class="sxs-lookup"><span data-stu-id="bc014-120">Provides extensive support for auditing and multiple ways of capturing errors and logging events.</span></span>  
  
     <span data-ttu-id="bc014-121">データ系列のキャプチャに加えて、データ変換パイプライン全体でデータへの変更を監視できます。</span><span class="sxs-lookup"><span data-stu-id="bc014-121">In addition to capturing data lineage, you can monitor changes to the data throughout the data transformation pipeline.</span></span>  
  
     <span data-ttu-id="bc014-122">SQLServer の変更データ キャプチャ機能をサポートする機能に SSIS ワークフローを統合することもできます。</span><span class="sxs-lookup"><span data-stu-id="bc014-122">You can also integrate your SSIS workflows with the features that support Change Data Capture functionality in SQL Server.</span></span>  
  
-   <span data-ttu-id="bc014-123">データ マイニングを [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のワークフローに組み込み、入力されたデータを複数のテーブルに適切に分割できます。</span><span class="sxs-lookup"><span data-stu-id="bc014-123">Data mining can be incorporated in the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] workflow, to intelligently separate incoming data into multiple tables.</span></span> <span data-ttu-id="bc014-124">たとえば、予測クエリを使用して新しい顧客をさまざまなグループに分けることで、メーリング キャンペーンの対象者を絞り込むことができます。</span><span class="sxs-lookup"><span data-stu-id="bc014-124">For example, you could use a prediction query to split new customers into different groups for targeting in a mailing campaign.</span></span>  
  
 <span data-ttu-id="bc014-125">データ マイニングのサポートで最も幅広く使用されている [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] コンポーネントへのリンクを以下の一覧にまとめました。</span><span class="sxs-lookup"><span data-stu-id="bc014-125">The following lists provide links to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] components that are most widely used in support of data mining.</span></span>  
  
 <span data-ttu-id="bc014-126">**制御フロー コンポーネント**</span><span class="sxs-lookup"><span data-stu-id="bc014-126">**Control Flow Components**</span></span>  
  
-   [<span data-ttu-id="bc014-127">Analysis Services DDL 実行タスク</span><span class="sxs-lookup"><span data-stu-id="bc014-127">Analysis Services Execute DDL Task</span></span>](../../integration-services/control-flow/analysis-services-execute-ddl-task.md)  
  
-   [<span data-ttu-id="bc014-128">Analysis Services 処理タスク</span><span class="sxs-lookup"><span data-stu-id="bc014-128">Analysis Services Processing Task</span></span>](../../integration-services/control-flow/analysis-services-processing-task.md)  
  
-   [<span data-ttu-id="bc014-129">CDC Control Task</span><span class="sxs-lookup"><span data-stu-id="bc014-129">CDC Control Task</span></span>](../../integration-services/control-flow/cdc-control-task.md)  
  
-   [<span data-ttu-id="bc014-130">データクレンジング</span><span class="sxs-lookup"><span data-stu-id="bc014-130">Data Cleansing</span></span>](../../data-quality-services/data-cleansing.md)  
  
-   [<span data-ttu-id="bc014-131">データ マイニング クエリ タスク</span><span class="sxs-lookup"><span data-stu-id="bc014-131">Data Mining Query Task</span></span>](../../integration-services/control-flow/data-mining-query-task.md)  
  
-   [<span data-ttu-id="bc014-132">データ プロファイル タスク</span><span class="sxs-lookup"><span data-stu-id="bc014-132">Data Profiling Task</span></span>](../../integration-services/control-flow/data-profiling-task.md)  
  
 <span data-ttu-id="bc014-133">**データ フロー コンポーネント**</span><span class="sxs-lookup"><span data-stu-id="bc014-133">**Data Flow Components**</span></span>  
  
-   [<span data-ttu-id="bc014-134">CDC フロー コンポーネント</span><span class="sxs-lookup"><span data-stu-id="bc014-134">CDC Flow Components</span></span>](../../integration-services/data-flow/cdc-flow-components.md)  
  
-   [<span data-ttu-id="bc014-135">条件分割変換</span><span class="sxs-lookup"><span data-stu-id="bc014-135">Conditional Split Transformation</span></span>](../../integration-services/data-flow/transformations/conditional-split-transformation.md)  
  
-   [<span data-ttu-id="bc014-136">データ変換の変換</span><span class="sxs-lookup"><span data-stu-id="bc014-136">Data Conversion Transformation</span></span>](../../integration-services/data-flow/transformations/data-conversion-transformation.md)  
  
-   [<span data-ttu-id="bc014-137">データマイニングモデルトレーニング変換先</span><span class="sxs-lookup"><span data-stu-id="bc014-137">Data Mining Model Training Destination</span></span>](../../integration-services/data-flow/data-mining-model-training-destination.md)  
  
-   [<span data-ttu-id="bc014-138">データマイニングクエリ変換</span><span class="sxs-lookup"><span data-stu-id="bc014-138">Data Mining Query Transformation</span></span>](../../integration-services/data-flow/transformations/data-mining-query-transformation.md)  
  
-   [<span data-ttu-id="bc014-139">派生列変換</span><span class="sxs-lookup"><span data-stu-id="bc014-139">Derived Column Transformation</span></span>](../../integration-services/data-flow/transformations/derived-column-transformation.md)  
  
-   [<span data-ttu-id="bc014-140">比率サンプリング変換</span><span class="sxs-lookup"><span data-stu-id="bc014-140">Percentage Sampling Transformation</span></span>](../../integration-services/data-flow/transformations/percentage-sampling-transformation.md)  
  
-   [<span data-ttu-id="bc014-141">用語抽出変換</span><span class="sxs-lookup"><span data-stu-id="bc014-141">Term Extraction Transformation</span></span>](../../integration-services/data-flow/transformations/term-extraction-transformation.md)  
  
-   [<span data-ttu-id="bc014-142">用語参照変換</span><span class="sxs-lookup"><span data-stu-id="bc014-142">Term Lookup Transformation</span></span>](../../integration-services/data-flow/transformations/lookup-transformation.md)  
  
##  <a name="sql-server-reporting-services"></a><a name="bkmk_SSRS"></a> <span data-ttu-id="bc014-143">SQL Server Reporting Services</span><span class="sxs-lookup"><span data-stu-id="bc014-143">SQL Server Reporting Services</span></span>  
 <span data-ttu-id="bc014-144">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] は、データ マイニング ソリューションに欠かせないコンポーネントとは考えられていませんが、データ マイニング ソリューションのプレゼンテーションの面で役立つ次のような機能を備えています。</span><span class="sxs-lookup"><span data-stu-id="bc014-144">Although [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] is typically not seen as a critical component of data mining solutions, it provides the following features that are useful for presentation of data mining solutions.</span></span>  
  
-   <span data-ttu-id="bc014-145">複雑なレポートにおける、複数のソースからのデータの統合。</span><span class="sxs-lookup"><span data-stu-id="bc014-145">Integration of data from multiple sources in complex reports.</span></span> <span data-ttu-id="bc014-146">アナリスト用のモデル コンテンツに対するクエリや、エンド ユーザー用の予測と傾向を示すレポートを作成できます。</span><span class="sxs-lookup"><span data-stu-id="bc014-146">Create queries against the model content for analysts, and reports that show predictions and trends for end users.</span></span>  
  
-   <span data-ttu-id="bc014-147">ユーザーが既存のマイニング モデルに対して直接問い合わせできるレポートを作成する機能。</span><span class="sxs-lookup"><span data-stu-id="bc014-147">The ability to create a report that lets users directly query against an existing mining model.</span></span>  
  
-   <span data-ttu-id="bc014-148">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]との統合。これにより、OLAP モデルから作成されたデータ マイニング ディメンションとデータ マイニング キューブのドリルスルーと調査がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="bc014-148">Integration with [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], to support drillthrough and exploration of data mining dimensions and data mining cubes created from OLAP models.</span></span>  
  
-   <span data-ttu-id="bc014-149">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]に用意されているパラメーター化と書式設定の機能。</span><span class="sxs-lookup"><span data-stu-id="bc014-149">parameterization and formatting features that are available in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="bc014-150">DMX クエリで Reporting Services をデータ ソースとして使用する方法の詳細については、以下のリンクを参照してください。</span><span class="sxs-lookup"><span data-stu-id="bc014-150">For more information about how to use Reporting Services with DMX queries as a data source, see these links:</span></span>  
  
 [<span data-ttu-id="bc014-151">データ マイニング モデル &#40;DMX&#41; からデータを取得する &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="bc014-151">Retrieve Data from a Data Mining Model &#40;DMX&#41; &#40;SSRS&#41;</span></span>](../../reporting-services/report-data/retrieve-data-from-a-data-mining-model-dmx-ssrs.md)  
  
 [<span data-ttu-id="bc014-152">Analysis Services の DMX クエリ デザイナーのユーザー インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bc014-152">Analysis Services DMX Query Designer User Interface</span></span>](../../reporting-services/report-data/analysis-services-dmx-query-designer-user-interface.md)  
  
 [<span data-ttu-id="bc014-153">DMX のための Analysis Services の接続の種類 &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="bc014-153">Analysis Services Connection Type for DMX &#40;SSRS&#41;</span></span>](../../reporting-services/report-data/analysis-services-connection-type-for-dmx-ssrs.md)  
  
 <span data-ttu-id="bc014-154">ただし、DMX をデータ ソースとして使用する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="bc014-154">However, it is not necessary to use DMX as the data source.</span></span> <span data-ttu-id="bc014-155">データ マイニング用の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] コンポーネントでは、予測クエリの結果をリレーショナル データベースに保存することもできます。</span><span class="sxs-lookup"><span data-stu-id="bc014-155">The [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] components for data mining also support saving the results of a prediction query to a relational database.</span></span> <span data-ttu-id="bc014-156">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]を使用して、モデルを更新するためのワークフローを確立している場合は、予測をはじめとするデータ マイニング クエリの結果を SQL Server で保持することで、レポート用の [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] や、DMX とやり取りしないその他のツールを使用できます。</span><span class="sxs-lookup"><span data-stu-id="bc014-156">If you have an established workflow for updating models using [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], persisting predictions and other data mining query results to SQL Server enable you to use [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] for reporting, as well as other tools that do not interface with DMX.</span></span>  
  
 <span data-ttu-id="bc014-157">Reporting Services をデータ ソースのプレゼンテーション層として使用する方法の詳細については、「 [Integrating Reporting Services into Applications](../../reporting-services/application-integration/integrating-reporting-services-into-applications.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bc014-157">For more information about using Reporting Services as the presentation layer for data sources, see [Integrating Reporting Services into Applications](../../reporting-services/application-integration/integrating-reporting-services-into-applications.md).</span></span>  
  
##  <a name="data-quality-services"></a><a name="bkmk_DQSetc"></a><span data-ttu-id="bc014-158">Data Quality Services</span><span class="sxs-lookup"><span data-stu-id="bc014-158">Data Quality Services</span></span>  
 <span data-ttu-id="bc014-159">Data Quality Services (DQS) は [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]の新機能です。</span><span class="sxs-lookup"><span data-stu-id="bc014-159">Data Quality Services (DQS) is new in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="bc014-160">データに問題があるとデータ マイニングが不可能になる可能性があるため、繰り返し分析を行ったり、大規模な組織で複雑なデータ ソースを扱ったりするデータ マイニング担当者は、DQS を使用する計画的なデータ プロジェクトの方が、 [!INCLUDE[tsql](../../includes/tsql-md.md)] やその他のスクリプトを使用した場当たり的なデータ クレンジングよりも、データ マイニングをサポートするうえで信頼性の高いソリューションであることを認識する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bc014-160">Because data problems can make data mining impossible, data miners who perform repeated analysis or who work in large organizations with complex data sources are expected to find that a well-planned data project using DQS is a more reliable solution for support of data mining than ad hoc cleansing of data using [!INCLUDE[tsql](../../includes/tsql-md.md)] or other scripts.</span></span>  
  
 <span data-ttu-id="bc014-161">データ マイニング ソリューションでのデータ準備とデータ整合性のために、DQS の次の機能を考慮する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bc014-161">The following features of DQS should be considered for data preparation and data integrity in a data mining solution.</span></span>  
  
 <span data-ttu-id="bc014-162">**ソース データを分析し変更を提案するコンピューター支援型データ クレンジング プロセス。**</span><span class="sxs-lookup"><span data-stu-id="bc014-162">**A computer-assisted data cleansing process that analyzes source data and proposes changes.**</span></span>  
 <span data-ttu-id="bc014-163">DQS では、データ品質プロバイダーによって保守および保証されているクラウドベースの参照データとソース データを比較できます。</span><span class="sxs-lookup"><span data-stu-id="bc014-163">DQS can compare source data with cloud-based reference data maintained and guaranteed by data quality providers.</span></span>  
  
 <span data-ttu-id="bc014-164">また、生のソース データを分析し、ユーザー データからナレッジ ベースを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="bc014-164">DQS can also analyze raw source data and create a knowledge base from user data.</span></span> <span data-ttu-id="bc014-165">処理後のデータは分類されたうえでユーザーに表示され、さらに処理が行われます。</span><span class="sxs-lookup"><span data-stu-id="bc014-165">The processed data is categorized and then displayed to the user for further processing.</span></span> <span data-ttu-id="bc014-166">クレンジング プロセスは対話型です。つまり、データ スチュワードはコンピューター支援型データ クレンジング プロセスによって提案されたデータを承認、拒否、または変更できます。</span><span class="sxs-lookup"><span data-stu-id="bc014-166">The cleansing process is interactive, meaning the data steward can approve, reject, or modify the data proposed by the computer-assisted data cleansing process.</span></span>  
  
 <span data-ttu-id="bc014-167">プロセスの結果として、継続的に質を高めたり、複数のデータ強化フェーズで再利用したりできるナレッジ ベースを得ることができます。</span><span class="sxs-lookup"><span data-stu-id="bc014-167">The outcome of the process is a knowledge base that you can continuously improve, or reuse in multiple data-enhancement phases.</span></span>  
  
 <span data-ttu-id="bc014-168">詳しくは、「 [Data Cleansing](../../data-quality-services/data-cleansing.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="bc014-168">For more information, see [Data Cleansing](../../data-quality-services/data-cleansing.md).</span></span>  
  
 <span data-ttu-id="bc014-169">**ソース データを分析し変更を提案する、コンピューター支援型の照合プロセス。**</span><span class="sxs-lookup"><span data-stu-id="bc014-169">**A computer-assisted matching process that analyzes source data and proposes changes.**</span></span>  
 <span data-ttu-id="bc014-170">データの重複を防ぐために、データ ソースの追加クレンジングを実行して、完全一致とあいまい一致を識別できます。</span><span class="sxs-lookup"><span data-stu-id="bc014-170">To prevent data duplication, you can perform addition cleansing of the data source, to identify exact and approximate matches.</span></span> <span data-ttu-id="bc014-171">これらのコンポーネントでは、照合ルールに加えて、照合ルールを適用するしきい値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="bc014-171">These components let you specify the matching rules, and the thresholds at which to apply them.</span></span>  
  
 <span data-ttu-id="bc014-172">データの一致を検出することにより、データ マイニングの妨げとなり得る重複を削除できます。</span><span class="sxs-lookup"><span data-stu-id="bc014-172">By finding data matches, you can remove duplicates, which can be a problem for data mining.</span></span> <span data-ttu-id="bc014-173">データの重複除去は自動ではありません。データ スチュワードか IT プロフェッショナルが、ナレッジ ベース内のナレッジと、データに対する変更の両方を検証する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bc014-173">Data de-duplication is not automatic; the data steward or IT professional must verify both the knowledge in the knowledge base and the changes to be made to the data.</span></span>  
  
 <span data-ttu-id="bc014-174">初期 DQS プロジェクトを作成したら、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] コンポーネントを使用してタスクの多くを自動化できます。</span><span class="sxs-lookup"><span data-stu-id="bc014-174">After you have created the initial DQS project, you can automate many of the tasks by using [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] components.</span></span>  
  
 <span data-ttu-id="bc014-175">詳しくは、「 [Data Matching](../../data-quality-services/data-matching.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="bc014-175">For more information, see [Data Matching](../../data-quality-services/data-matching.md).</span></span>  
  
 <span data-ttu-id="bc014-176">データ品質プロジェクトでクレンジングおよび照合アクティビティを実行しながら、DQS で処理中のデータに関する統計と情報をリアルタイムに入手できます。</span><span class="sxs-lookup"><span data-stu-id="bc014-176">While performing cleansing and matching activities in a data quality project, you can get real-time statistics and information about the data that is being processed by DQS.</span></span> <span data-ttu-id="bc014-177">データ クレンジングまたは照合によりデータ品質がどの程度向上したかを評価したり、加えられた変更を把握したりするのには、データ プロファイルが役立ちます。</span><span class="sxs-lookup"><span data-stu-id="bc014-177">Data profiling helps you assess the extent to which data cleansing or matching helped improve the data quality, and understand the changes that were made.</span></span> <span data-ttu-id="bc014-178">データ プロファイルと通知の詳細については、「 [Data Profiling and Notifications in DQS](../../data-quality-services/data-profiling-and-notifications-in-dqs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bc014-178">For information about data profiling and notifications, see [Data Profiling and Notifications in DQS](../../data-quality-services/data-profiling-and-notifications-in-dqs.md).</span></span>  
  
 <span data-ttu-id="bc014-179">**3 種類のナレッジ (そのままの状態のナレッジ、DQS サーバーによって生成されるナレッジ、ユーザーが生成するナレッジ) があるナレッジ ベース。**</span><span class="sxs-lookup"><span data-stu-id="bc014-179">**A knowledge base that represents three types of knowledge: out-of-the-box knowledge, knowledge generated by the DQS server, and knowledge generated by the user.**</span></span>  
 <span data-ttu-id="bc014-180">ナレッジ ベースを作成した後は、それを繰り返し使用して、他のデータのクレンジングと検証を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="bc014-180">Once you have created a knowledge base, you can use it iteratively to cleanse and verify other data.</span></span>  
  
 <span data-ttu-id="bc014-181">新しいデータを複数のソースからナレッジ ベース データにインポートできます。参照プロバイダーからの既知のクリーン データも、ナレッジ ベース内の既存のデータに一致する生のデータもインポート可能です。</span><span class="sxs-lookup"><span data-stu-id="bc014-181">You can import new data into the knowledge base data from multiple sources, either known clean data from reference providers, or raw data that is matched to existing data in the knowledge base.</span></span>  
  
 <span data-ttu-id="bc014-182">データ品質プロジェクトでのクレンジング アクティビティの詳細については、「データ クレンジング (DQS)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bc014-182">For detailed information about the cleansing activity in a data quality project, see Data Cleansing (DQS).</span></span>  
  
 <span data-ttu-id="bc014-183">ナレッジ ベース内のナレッジを他のソースに適用して、他のプロセス内でデータ クレンジングを行うこともできます。</span><span class="sxs-lookup"><span data-stu-id="bc014-183">You can also apply the knowledge in the knowledge base to other sources, to perform data cleansing within other processes.</span></span> <span data-ttu-id="bc014-184">こうしたデータ クレンジングは、ユーザーの入力エラー、転送または格納時の破損、データ辞書定義の不一致などを見つけるのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="bc014-184">Such data cleansing can help identify user entry errors, corruption in transmission or storage, or mismatched data dictionary definitions.</span></span>  
  
 <span data-ttu-id="bc014-185">詳細については、「 [DQS Knowledge Bases and Domains](../../data-quality-services/dqs-knowledge-bases-and-domains.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="bc014-185">For more information, see [DQS Knowledge Bases and Domains](../../data-quality-services/dqs-knowledge-bases-and-domains.md).</span></span>  
  
##  <a name="full-text-search"></a><a name="bkmk_FTSetc"></a><span data-ttu-id="bc014-186">フルテキスト検索</span><span class="sxs-lookup"><span data-stu-id="bc014-186">Full-Text Search</span></span>  
 <span data-ttu-id="bc014-187">SQL Server のフルテキスト検索により、アプリケーションとユーザーは、SQL Server テーブル内の文字ベースのデータに対してフルテキスト クエリを実行できます。</span><span class="sxs-lookup"><span data-stu-id="bc014-187">Full-Text Search in SQL Server lets applications and users run full-text queries against character-based data in SQL Server tables.</span></span> <span data-ttu-id="bc014-188">フルテキスト検索が有効であれば、語句のさまざまな形式に関する言語固有のルールに基づいて強化された検索を、テキスト データに対して実行できます。</span><span class="sxs-lookup"><span data-stu-id="bc014-188">When full-text search is enabled, you can perform searches against text data that are enhanced by language-specific rules about the multiple forms of a word or phrase.</span></span> <span data-ttu-id="bc014-189">また、複数の用語間の距離などの検索条件を構成することも、尤度の順に返される結果を制限する関数を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="bc014-189">You can also configure search conditions, such as the distance between multiple terms, and use functions to constrain the results that are returned in order of likelihood.</span></span>  
  
 <span data-ttu-id="bc014-190">フルテキスト クエリは SQL Server エンジンによって提供される機能なので、パラメーター化クエリを作成したり、テキスト データ ソースでフルテキスト検索機能を使用してカスタム データ セットや用語のベクトルを生成したりできるほか、これらのソースをデータ マイニングで使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="bc014-190">Because full-text queries are a feature provided by the SQL Server engine, you can create parameterized queries, generate custom data sets or term vectors by using full-text search features on a text data source, and use these sources in data mining.</span></span>  
  
 <span data-ttu-id="bc014-191">フルテキスト クエリでフルテキスト インデックスを扱う方法の詳細については、「 [フルテキスト検索でのクエリ](../../relational-databases/search/query-with-full-text-search.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bc014-191">For more information about how full-text queries interact with the full-text index, see [Query with Full-Text Search](../../relational-databases/search/query-with-full-text-search.md).</span></span>  
  
 <span data-ttu-id="bc014-192">SQL Server のフルテキスト検索機能の利点は、すべての SQL Server 言語で提供されるワード ブレーカーとステマーに含まれる言語インテリジェンスを活用できるという点です。</span><span class="sxs-lookup"><span data-stu-id="bc014-192">An advantage of using the full-text search features of SQL Server is that you can leverage the linguistic intelligence that is contained in the word breakers and stemmers shipped for all SQL Server languages.</span></span> <span data-ttu-id="bc014-193">提供されたワード ブレーカーとステマーを使用すると、各言語に適した文字で単語を区切ることができるうえ、分音記号または表記のバリエーション (日本語における数の複数の形式など) に基づくシノニムを見落とさずに済みます。</span><span class="sxs-lookup"><span data-stu-id="bc014-193">By using the supplied word breakers and stemmers, you can ensure that words are separated using the characters appropriate for each language, and that synonyms based on diacritics or orthographic variations (such as the multiple number formats in Japanese) are not overlooked.</span></span>  
  
 <span data-ttu-id="bc014-194">単語の境界を決める言語インテリジェンスに加え、各言語のステマーでも、その言語の活用形や表記のバリエーションに関するルールのナレッジに基づいて、単語の変化形を 1 つの用語に絞り込むことができます。</span><span class="sxs-lookup"><span data-stu-id="bc014-194">In addition to linguistic intelligence that governs word boundaries, the stemmers for each language can reduce variants of a word to a single term, based on knowledge of the rules for conjugation and orthographic variation in that language.</span></span> <span data-ttu-id="bc014-195">言語分析のルールは言語ごとに異なり、実際のコーパスに関する幅広い研究に基づいて作成されます。</span><span class="sxs-lookup"><span data-stu-id="bc014-195">The rules for linguistic analysis differ for each language and are developed based on extensive research on real-life corpora.</span></span>  
  
 <span data-ttu-id="bc014-196">詳細については、「 [検索用のワード ブレーカーとステミング機能の構成と管理](../../relational-databases/search/configure-and-manage-word-breakers-and-stemmers-for-search.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bc014-196">For more information, see [Configure and Manage Word Breakers and Stemmers for Search](../../relational-databases/search/configure-and-manage-word-breakers-and-stemmers-for-search.md).</span></span>  
  
 <span data-ttu-id="bc014-197">フルテキスト インデックスの作成後に保存される単語のバージョンは、圧縮形式のトークンです。</span><span class="sxs-lookup"><span data-stu-id="bc014-197">The version of a word that is stored after full-text indexing is a token in compressed form.</span></span> <span data-ttu-id="bc014-198">フルテキスト インデックスに対する後続のクエリにより、その言語のルールに基づいて特定の単語の変化形が複数生成されるため、あいまい一致も漏らさず照合されます。</span><span class="sxs-lookup"><span data-stu-id="bc014-198">Subsequent queries to the full-text index generate multiple inflectional forms of a particular word based on the rules of that language, to ensure that all probable matches are made.</span></span> <span data-ttu-id="bc014-199">たとえば、格納されているトークンが "run" であっても、クエリエンジンは "実行中"、"実行済み"、"ランナー" という用語を検索します。これは、"run" という単語の原形バリエーションが定期的に派生しているためです。</span><span class="sxs-lookup"><span data-stu-id="bc014-199">For example, although the token that is stored might be "run", the query engine also looks for the terms "running", "ran", and "runner," because these are regularly derived morphological variations of the root word "run".</span></span>  
  
 <span data-ttu-id="bc014-200">ユーザー類義語辞典を作成および構築して、シノニムの格納、検索結果の精度の向上、用語の分類を行うこともできます。</span><span class="sxs-lookup"><span data-stu-id="bc014-200">You can also create and build a user thesaurus to store synonyms and enable better search results, or categorization of terms.</span></span> <span data-ttu-id="bc014-201">フルテキスト データに合わせた類義語辞典を作成すると、そのデータのフルテキスト クエリのスコープを効果的に拡張できます。</span><span class="sxs-lookup"><span data-stu-id="bc014-201">By developing a thesaurus tailored to your full-text data, you can effectively broaden the scope of full-text queries on that data.</span></span> <span data-ttu-id="bc014-202">詳細については、「 [フルテキスト検索に使用する類義語辞典ファイルの構成と管理](../../relational-databases/search/configure-and-manage-thesaurus-files-for-full-text-search.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bc014-202">For more information, see [Configure and Manage Thesaurus Files for Full-Text Search](../../relational-databases/search/configure-and-manage-thesaurus-files-for-full-text-search.md).</span></span>  
  
 <span data-ttu-id="bc014-203">フルテキスト検索を使用するうえでの要件は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="bc014-203">Requirements for using full-text search include the following:</span></span>  
  
-   <span data-ttu-id="bc014-204">データベース管理者がテーブル上にフルテキスト インデックスを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bc014-204">The database administrator must create a full-text index on the table.</span></span>  
  
-   <span data-ttu-id="bc014-205">1 つのテーブルに対し、1 つのフルテキスト インデックスしか使用できません。</span><span class="sxs-lookup"><span data-stu-id="bc014-205">Only one full-text index is allowed per table.</span></span>  
  
-   <span data-ttu-id="bc014-206">インデックスを作成する列ごとに一意のキーが必要です。</span><span class="sxs-lookup"><span data-stu-id="bc014-206">Each column that you index must have a unique key.</span></span>  
  
-   <span data-ttu-id="bc014-207">フルテキスト インデックスを作成できるのは、データ型が char、varchar、nchar、nvarchar、text、ntext、image、xml、varbinary、varbinary(max) の列のみです。</span><span class="sxs-lookup"><span data-stu-id="bc014-207">Full-text indexing is supported only for columns with these data types: char, varchar, nchar, nvarchar, text, ntext, image, xml, varbinary, and varbinary(max).</span></span> <span data-ttu-id="bc014-208">列が varbinary、varbinary(max)、image、または xml の場合は、インデックスを作成できるドキュメントのファイル拡張子 (.doc、.pdf、.xls など) を別の型列で指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bc014-208">If the column is varbinary, varbinary(max), image, or xml, you must specify the file extension of the indexable document (.doc, .pdf, .xls, and so forth), in a separate type column.</span></span>  
  
##  <a name="semantic-indexing"></a><a name="bkmk_SemSearch"></a><span data-ttu-id="bc014-209">セマンティックインデックス作成</span><span class="sxs-lookup"><span data-stu-id="bc014-209">Semantic Indexing</span></span>  
 <span data-ttu-id="bc014-210">セマンティック検索は SQL Server の既存のフルテキスト検索機能を基にして構築されていますが、追加の機能と統計を使用して、自動キーワード抽出や関連ドキュメントの検出などにも対応できます。</span><span class="sxs-lookup"><span data-stu-id="bc014-210">Semantic search builds upon the existing full-text search features in SQL Server, but uses additional capabilities and statistics to enable scenarios such as automatic keyword extraction and discovery of related documents.</span></span> <span data-ttu-id="bc014-211">たとえば、セマンティック検索を使用すると、編成用の基本分類を構築することも、ドキュメントのコーパスを分類することもできます。</span><span class="sxs-lookup"><span data-stu-id="bc014-211">For example, you might use semantic search to build a base taxonomy for an organization, or classify a corpus of documents.</span></span> <span data-ttu-id="bc014-212">また、クラスタリングまたはデシジョン ツリー モデルで、抽出した用語を組み合わせたものや、ドキュメントの類似スコアを使用することも可能です。</span><span class="sxs-lookup"><span data-stu-id="bc014-212">Or, you could use the combination of extracted terms and document similarity scores in clustering or decision tree models.</span></span>  
  
 <span data-ttu-id="bc014-213">セマンティック検索を正しく実装し、データ列にインデックスを設定したら、セマンティック インデックスの作成にネイティブに備わる関数を使用して、以下の処理が可能です。</span><span class="sxs-lookup"><span data-stu-id="bc014-213">After you have enabled semantic search successfully, and indexed your data columns, you can use the functions that are provided natively with semantic indexing to do the following:</span></span>  
  
-   <span data-ttu-id="bc014-214">スコアと共に 1 語のキー フレーズを返す。</span><span class="sxs-lookup"><span data-stu-id="bc014-214">Return single-word key phrases with their score.</span></span>  
  
-   <span data-ttu-id="bc014-215">指定したキー フレーズを含むドキュメントを返す。</span><span class="sxs-lookup"><span data-stu-id="bc014-215">Return documents that contain a specified key phrase.</span></span>  
  
-   <span data-ttu-id="bc014-216">類似性スコアと、そのスコアに関係する用語を返す。</span><span class="sxs-lookup"><span data-stu-id="bc014-216">Return similarity scores, and the terms that contribute to the score.</span></span>  
  
 <span data-ttu-id="bc014-217">詳細については、「 [セマンティック検索を使用したドキュメント内のキー フレーズの検索](../../relational-databases/search/find-key-phrases-in-documents-with-semantic-search.md) 」および「 [セマンティック検索による類似および関連したドキュメントの検索](../../relational-databases/search/find-similar-and-related-documents-with-semantic-search.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="bc014-217">For more information, see [Find Key Phrases in Documents with Semantic Search](../../relational-databases/search/find-key-phrases-in-documents-with-semantic-search.md) and [Find Similar and Related Documents with Semantic Search](../../relational-databases/search/find-similar-and-related-documents-with-semantic-search.md).</span></span>  
  
 <span data-ttu-id="bc014-218">セマンティック インデックスの作成をサポートするデータベース オブジェクトの詳細については、「 [テーブルおよび列に対するセマンティック検索の有効化](../../relational-databases/search/enable-semantic-search-on-tables-and-columns.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="bc014-218">For more information about the database objects that support semantic indexing, see [Enable Semantic Search on Tables and Columns](../../relational-databases/search/enable-semantic-search-on-tables-and-columns.md).</span></span>  
  
 <span data-ttu-id="bc014-219">セマンティック検索を使用するための要件は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="bc014-219">Requirements for using semantic search include the following:</span></span>  
  
-   <span data-ttu-id="bc014-220">フルテキスト検索も有効である必要があります。</span><span class="sxs-lookup"><span data-stu-id="bc014-220">Full-text search also be enabled.</span></span>  
  
-   <span data-ttu-id="bc014-221">セマンティック検索コンポーネントをインストールすると特殊なシステム データベースも作成されますが、名前の変更、修正、置き換えはできません。</span><span class="sxs-lookup"><span data-stu-id="bc014-221">Installation of the semantic search components also creates a special system database, which cannot be renamed, altered, or replaced.</span></span>  
  
-   <span data-ttu-id="bc014-222">サービスを使用してインデックスを作成するドキュメントは、SQL Server を使用して、フルテキスト インデックスの作成に対応した、テーブルとインデックス付きビューを含む任意のデータベース オブジェクトに格納する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bc014-222">Documents that you index using the service must be stored in SQL Server, in any of the database objects that are supported for full-text indexing, including tables and indexed views.</span></span>  
  
-   <span data-ttu-id="bc014-223">すべてのフルテキスト言語でセマンティック インデックスの作成がサポートされているわけではありません。</span><span class="sxs-lookup"><span data-stu-id="bc014-223">Not all of the full-text languages support semantic indexing.</span></span> <span data-ttu-id="bc014-224">サポートされている言語の一覧については、「[sys.fulltext_semantic_languages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-semantic-languages-transact-sql)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="bc014-224">For a list of supported languages, see [sys.fulltext_semantic_languages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-semantic-languages-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc014-225">参照</span><span class="sxs-lookup"><span data-stu-id="bc014-225">See Also</span></span>  
 <span data-ttu-id="bc014-226">[SSAS&#41;&#40;の多次元モデルソリューション](../multidimensional-models/multidimensional-model-solutions-ssas.md) </span><span class="sxs-lookup"><span data-stu-id="bc014-226">[Multidimensional Model Solutions &#40;SSAS&#41;](../multidimensional-models/multidimensional-model-solutions-ssas.md) </span></span>  
 [<span data-ttu-id="bc014-227">テーブル モデル ソリューション &#40;SSAS テーブル&#41;</span><span class="sxs-lookup"><span data-stu-id="bc014-227">Tabular Model Solutions &#40;SSAS Tabular&#41;</span></span>](../tabular-model-solutions-ssas-tabular.md)  
  
  
