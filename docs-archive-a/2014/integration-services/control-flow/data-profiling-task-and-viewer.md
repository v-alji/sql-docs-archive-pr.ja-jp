---
title: データ プロファイル タスクとビューアー | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Data Profiling task [Integration Services], about data profiling
- data profiling
- profiling data
ms.assetid: 756840e3-aa09-45cd-9951-1a17af4b5925
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ae15d1cc75f8db04c36a830e44d07800c5aecf75
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639593"
---
# <a name="data-profiling-task-and-viewer"></a><span data-ttu-id="576e2-102">データ プロファイル タスクとビューアー</span><span class="sxs-lookup"><span data-stu-id="576e2-102">Data Profiling Task and Viewer</span></span>
  <span data-ttu-id="576e2-103">データ プロファイル タスクを使用すると、データの抽出、変換、および読み込みを行うプロセス内でデータのプロファイルを実行できます。</span><span class="sxs-lookup"><span data-stu-id="576e2-103">The Data Profiling task provides data profiling functionality inside the process of extracting, transforming, and loading data.</span></span> <span data-ttu-id="576e2-104">データ プロファイル タスクを使用することによって、次のような利点があります。</span><span class="sxs-lookup"><span data-stu-id="576e2-104">By using the Data Profiling task, you can achieve the following benefits:</span></span>  
  
-   <span data-ttu-id="576e2-105">ソース データをより効果的に分析できます。</span><span class="sxs-lookup"><span data-stu-id="576e2-105">Analyze the source data more effectively</span></span>  
  
-   <span data-ttu-id="576e2-106">ソース データに関する理解を深めることができます。</span><span class="sxs-lookup"><span data-stu-id="576e2-106">Understand the source data better</span></span>  
  
-   <span data-ttu-id="576e2-107">データ ウェアハウスに読み込まれる前にデータ品質の問題を回避できます。</span><span class="sxs-lookup"><span data-stu-id="576e2-107">Prevent data quality problems before they are introduced into the data warehouse.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="576e2-108">データ プロファイル タスクは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に格納されているデータでのみ機能します。</span><span class="sxs-lookup"><span data-stu-id="576e2-108">The Data Profiling task works only with data that is stored in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="576e2-109">サードパーティまたはファイル ベースのデータ ソースでは機能しません。</span><span class="sxs-lookup"><span data-stu-id="576e2-109">It does not work with third-party or file-based data sources.</span></span>  
  
## <a name="data-profiling-overview"></a><span data-ttu-id="576e2-110">データ プロファイルの概要</span><span class="sxs-lookup"><span data-stu-id="576e2-110">Data Profiling Overview</span></span>  
 <span data-ttu-id="576e2-111">データ品質は、すべてのビジネスにとって重要です。</span><span class="sxs-lookup"><span data-stu-id="576e2-111">Data quality is important to every business.</span></span> <span data-ttu-id="576e2-112">企業はトランザクション システム上に分析システムおよびビジネス インテリジェンス システムを構築するので、主要業績評価指標とデータ マイニング予測の信頼性は、基になるデータの有効性に完全に依存します。</span><span class="sxs-lookup"><span data-stu-id="576e2-112">As enterprises build analytical and business intelligence systems on top of their transactional systems, the reliability of key performance indicators and of data mining predictions depends completely on the validity of the data on which they are based.</span></span> <span data-ttu-id="576e2-113">ただし、ビジネス上の意思決定における有効なデータの重要性は高まっていますが、このデータの有効性を確保することも難しくなっています。</span><span class="sxs-lookup"><span data-stu-id="576e2-113">But although the importance of valid data for business decision-making is increasing, the challenge of making sure of this data's validity is also increasing.</span></span> <span data-ttu-id="576e2-114">データはさまざまなシステムやソースおよび多くのユーザーから企業に絶えず流れ込んできています。</span><span class="sxs-lookup"><span data-stu-id="576e2-114">Data is streaming into the enterprise constantly from diverse systems and sources, and a large numbers of users.</span></span>  
  
 <span data-ttu-id="576e2-115">データ品質の基準はドメインまたはアプリケーションに固有であるため、定義が困難な場合があります。</span><span class="sxs-lookup"><span data-stu-id="576e2-115">Metrics for data quality can be difficult to define because they are specific to the domain or the application.</span></span> <span data-ttu-id="576e2-116">データ品質を定義する一般的な方法の 1 つとして、データのプロファイルが挙げられます。</span><span class="sxs-lookup"><span data-stu-id="576e2-116">One common approach to defining data quality is data profiling.</span></span>  
  
 <span data-ttu-id="576e2-117">データ プロファイルは、次のようなデータに関する集計統計のコレクションです。</span><span class="sxs-lookup"><span data-stu-id="576e2-117">A data profile is a collection of aggregate statistics about data that might include the following:</span></span>  
  
-   <span data-ttu-id="576e2-118">Customer テーブルの行数。</span><span class="sxs-lookup"><span data-stu-id="576e2-118">The number of rows in the Customer table.</span></span>  
  
-   <span data-ttu-id="576e2-119">State 列の個別の値の数。</span><span class="sxs-lookup"><span data-stu-id="576e2-119">The number of distinct values in the State column.</span></span>  
  
-   <span data-ttu-id="576e2-120">Zip 列の NULL 値または不足値の数。</span><span class="sxs-lookup"><span data-stu-id="576e2-120">The number of null or missing values in the Zip column.</span></span>  
  
-   <span data-ttu-id="576e2-121">City 列の値の分布。</span><span class="sxs-lookup"><span data-stu-id="576e2-121">The distribution of values in the City column.</span></span>  
  
-   <span data-ttu-id="576e2-122">Zip 列に対する State 列の機能依存の強さ。つまり、都道府県は特定の郵便番号の値に対して常に同じである必要があります。</span><span class="sxs-lookup"><span data-stu-id="576e2-122">The strength of the functional dependency of the State column on the Zip column-that is, the state should always be the same for a given zip value.</span></span>  
  
 <span data-ttu-id="576e2-123">データ プロファイルに示される統計によって、ソース データを使用することで生じる可能性がある品質の問題を効果的に最小限に抑えるために必要な情報を得ることができます。</span><span class="sxs-lookup"><span data-stu-id="576e2-123">The statistics that a data profile provides gives you the information that you need in order to effectively minimize the quality issues that might occur from using the source data.</span></span>  
  
## <a name="integration-services-and-data-profiling"></a><span data-ttu-id="576e2-124">Integration Services とデータ プロファイル</span><span class="sxs-lookup"><span data-stu-id="576e2-124">Integration Services and Data Profiling</span></span>  
 <span data-ttu-id="576e2-125">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]におけるデータのプロファイル処理は、次の手順で構成されています。</span><span class="sxs-lookup"><span data-stu-id="576e2-125">In [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], the data profiling process consist of the following steps:</span></span>  
  
 <span data-ttu-id="576e2-126">**ステップ 1:データ プロファイル タスクの設定**</span><span class="sxs-lookup"><span data-stu-id="576e2-126">**Step 1: Setting up the Data Profiling Task**</span></span>  
 <span data-ttu-id="576e2-127">データ プロファイル タスクは、計算するプロファイルを構成するために使用するタスクです。</span><span class="sxs-lookup"><span data-stu-id="576e2-127">The Data Profiling task is a task that you use to configure the profiles that you want to compute.</span></span> <span data-ttu-id="576e2-128">データ プロファイル タスクが含まれているパッケージを実行して、プロファイルを計算します。</span><span class="sxs-lookup"><span data-stu-id="576e2-128">You then run the package that contains the Data Profiling task to compute the profiles.</span></span> <span data-ttu-id="576e2-129">このタスクによって、XML 形式のプロファイル出力がファイルまたはパッケージ変数に保存されます。</span><span class="sxs-lookup"><span data-stu-id="576e2-129">The task saves the profile output in XML format to a file or a package variable.</span></span>  
  
 <span data-ttu-id="576e2-130">**詳細:** [データ プロファイル タスクのセットアップ](data-profiling-task.md)</span><span class="sxs-lookup"><span data-stu-id="576e2-130">**For more information:** [Setup of the Data Profiling Task](data-profiling-task.md)</span></span>  
  
 <span data-ttu-id="576e2-131">**手順 2:データ プロファイル タスクで計算されたプロファイルの確認**</span><span class="sxs-lookup"><span data-stu-id="576e2-131">**Step 2: Reviewing the Profiles that the Data Profiling Task Computes**</span></span>  
 <span data-ttu-id="576e2-132">データ プロファイル タスクで計算されたデータ プロファイルを表示するには、出力をファイルに送信して Data Profile Viewer を使用します。</span><span class="sxs-lookup"><span data-stu-id="576e2-132">To view the data profiles that the Data Profiling task computes, you send the output to a file, and then you use the Data Profile Viewer.</span></span> <span data-ttu-id="576e2-133">このビューアーは、サマリ形式とオプションのドリル ダウン機能を使用した詳細形式の両方でプロファイル出力を表示するスタンドアロンのユーティリティです。</span><span class="sxs-lookup"><span data-stu-id="576e2-133">This viewer is a stand-alone utility that displays the profile output in both summary and detail format with optional drilldown capability.</span></span>  
  
 <span data-ttu-id="576e2-134">**詳細:** [Data Profile Viewer](data-profile-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="576e2-134">**For more information:** [Data Profile Viewer](data-profile-viewer.md)</span></span>  
  
### <a name="addition-of-conditional-logic-to-the-data-profiling-workflow"></a><span data-ttu-id="576e2-135">データ プロファイル ワークフローへの条件ロジックの追加</span><span class="sxs-lookup"><span data-stu-id="576e2-135">Addition of Conditional Logic to the Data Profiling Workflow</span></span>  
 <span data-ttu-id="576e2-136">データ プロファイル タスクには、プロファイルの出力に基づいてこのタスクを下流のタスクに接続するための条件ロジックを使用できるようにする機能が組み込まれていません。</span><span class="sxs-lookup"><span data-stu-id="576e2-136">The Data Profiling task does not have built-in features that allow you to use conditional logic to connect this task to downstream tasks based on the profile output.</span></span> <span data-ttu-id="576e2-137">ただし、スクリプト タスクで少量のプログラミングを行って、このロジックを簡単に追加することができます。</span><span class="sxs-lookup"><span data-stu-id="576e2-137">However, you can easily add this logic, with a small amount of programming, in a Script task.</span></span> <span data-ttu-id="576e2-138">たとえば、スクリプト タスクでは、データ プロファイル タスクの出力ファイルに対して XPath クエリを実行できます。</span><span class="sxs-lookup"><span data-stu-id="576e2-138">For example, the Script task could perform an XPath query against the output file of the Data Profiling task.</span></span> <span data-ttu-id="576e2-139">このクエリによって、特定の列の NULL 値の比率が特定のしきい値を超えていないかどうかを判断できます。</span><span class="sxs-lookup"><span data-stu-id="576e2-139">The query could determine whether the percentage of null values in a particular column exceeds a certain threshold.</span></span> <span data-ttu-id="576e2-140">比率がしきい値を超えている場合は、パッケージを中断し、ソース データの問題を解決してから続行することができます。</span><span class="sxs-lookup"><span data-stu-id="576e2-140">If the percentage exceeds the threshold, you could interrupt the package and resolve the problem in the source data before continuing.</span></span> <span data-ttu-id="576e2-141">詳細については、「 [パッケージ ワークフローでデータ プロファイル タスクを使用する](incorporate-a-data-profiling-task-in-package-workflow.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="576e2-141">For more information, see [Incorporate a Data Profiling Task in Package Workflow](incorporate-a-data-profiling-task-in-package-workflow.md).</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="576e2-142">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="576e2-142">Related Content</span></span>  
 [<span data-ttu-id="576e2-143">Data Profiler スキーマ</span><span class="sxs-lookup"><span data-stu-id="576e2-143">Data Profiler Schema</span></span>](https://go.microsoft.com/fwlink/?LinkId=251524)  
  
  
