---
title: テーブルモデリング (Adventure Works チュートリアル) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 140d0b43-9455-4907-9827-16564a904268
author: minewiskan
ms.author: owend
ms.openlocfilehash: 840e8fe04309486d1583bc46161a4fc66ca7b1bf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643491"
---
# <a name="tabular-modeling-adventure-works-tutorial"></a><span data-ttu-id="4eb44-102">テーブル モデリング (Adventure Works チュートリアル)</span><span class="sxs-lookup"><span data-stu-id="4eb44-102">Tabular Modeling (Adventure Works Tutorial)</span></span>
  <span data-ttu-id="4eb44-103">このチュートリアルでは、 [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] を使用して、 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]Analysis Services テーブル モデルを作成する方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="4eb44-103">This tutorial provides lessons on how to create a [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] Analysis Services tabular model by using [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="4eb44-104">学習する内容</span><span class="sxs-lookup"><span data-stu-id="4eb44-104">What You Will Learn</span></span>  
 <span data-ttu-id="4eb44-105">このチュートリアルでは次のことを学習します。</span><span class="sxs-lookup"><span data-stu-id="4eb44-105">During the course of this tutorial, you will learn the following:</span></span>  
  
-   <span data-ttu-id="4eb44-106">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]で新しいテーブル モデル プロジェクトを作成する方法。</span><span class="sxs-lookup"><span data-stu-id="4eb44-106">How to create a new tabular model project in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)].</span></span>  
  
-   <span data-ttu-id="4eb44-107">SQLServer リレーショナル データベースからテーブル モデル プロジェクトにデータをインポートする方法。</span><span class="sxs-lookup"><span data-stu-id="4eb44-107">How to import data from a SQL Server relational database into a tabular model project.</span></span>  
  
-   <span data-ttu-id="4eb44-108">モデルに含まれるテーブル間のリレーションシップを作成および管理する方法。</span><span class="sxs-lookup"><span data-stu-id="4eb44-108">How to create and manage relationships between tables in the model.</span></span>  
  
-   <span data-ttu-id="4eb44-109">モデル データの分析を支援するための、計算、計測、および主要業績評価指標を作成および管理する方法。</span><span class="sxs-lookup"><span data-stu-id="4eb44-109">How to create and manage calculations, measures, and Key Performance Indicators that help users analyze model data.</span></span>  
  
-   <span data-ttu-id="4eb44-110">ビジネスおよびアプリケーション固有のビューポイントを提供して、ユーザーがモデル データをより簡単に参照できるようにするためのパースペクティブや階層を作成および管理する方法。</span><span class="sxs-lookup"><span data-stu-id="4eb44-110">How to create and manage perspectives and hierarchies that help users more easily browse model data by providing business and application specific viewpoints.</span></span>  
  
-   <span data-ttu-id="4eb44-111">パーティションを作成してテーブル データをより小さな論理部分に分割し、他のパーティションと分離して処理できるようにする方法。</span><span class="sxs-lookup"><span data-stu-id="4eb44-111">How to create partitions that divide table data into smaller logical parts that can be processed independent from other partitions.</span></span>  
  
-   <span data-ttu-id="4eb44-112">ユーザー メンバーのロールを作成して、モデル オブジェクトとデータを保護する方法。</span><span class="sxs-lookup"><span data-stu-id="4eb44-112">How to secure model objects and data by creating roles with user members.</span></span>  
  
-   <span data-ttu-id="4eb44-113">テーブル モデルを、サンドボックスや、テーブル モードで実行されている Analysis Services の実稼働インスタンスに配置する方法。</span><span class="sxs-lookup"><span data-stu-id="4eb44-113">How to deploy a tabular model to a sandbox or production instance of Analysis Services running in Tabular mode.</span></span>  
  
## <a name="tutorial-scenario"></a><span data-ttu-id="4eb44-114">チュートリアルのシナリオ</span><span class="sxs-lookup"><span data-stu-id="4eb44-114">Tutorial Scenario</span></span>  
 <span data-ttu-id="4eb44-115">このチュートリアルには、 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)]という架空の会社が登場します。</span><span class="sxs-lookup"><span data-stu-id="4eb44-115">This tutorial is based on [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)], a fictitious company.</span></span> [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] <span data-ttu-id="4eb44-116">は、特殊合金自転車を北米、ヨーロッパ、およびアジアの市場に供給する大規模な多国籍製造会社です。</span><span class="sxs-lookup"><span data-stu-id="4eb44-116">is a large, multinational manufacturing company that produces and distributes metal and composite bicycles to commercial markets in North America, Europe, and Asia.</span></span> <span data-ttu-id="4eb44-117">[!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] はワシントン州のボセルに本社を置き、500 名の従業員を抱えています。</span><span class="sxs-lookup"><span data-stu-id="4eb44-117">The headquarters for [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] is in Bothell, Washington, where the company employs 500 workers.</span></span> <span data-ttu-id="4eb44-118">さらに、 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] の各市場には、その地域を担当する販売チームがいます。</span><span class="sxs-lookup"><span data-stu-id="4eb44-118">Additionally, [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] employs several regional sales teams throughout its market base.</span></span>  
  
 <span data-ttu-id="4eb44-119">あなたは、販売チーム、マーケティング チーム、および上級管理職のデータ分析ニーズにより高度に対応するべく、AdventureWorksDW サンプル データベース内のインターネット販売データを分析するためのテーブル モデルを作成します。</span><span class="sxs-lookup"><span data-stu-id="4eb44-119">To better support the data analysis needs of sales and marketing teams and of senior management, you are tasked with creating a tabular model for users to analyze internet sales data in the AdventureWorksDW sample database.</span></span>  
  
 <span data-ttu-id="4eb44-120">このチュートリアル (および Adventure Works Internet Sales テーブル モデル) を完了するには、多数のレッスンを完了する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4eb44-120">In order to complete the tutorial, and the Adventure Works Internet Sales tabular model, you must complete a number of lessons.</span></span> <span data-ttu-id="4eb44-121">1 つのレッスンはいくつかのタスクから構成され､レッスンを終えるには､各タスクを順に終了する必要があります｡</span><span class="sxs-lookup"><span data-stu-id="4eb44-121">Within each lesson are a number of tasks; completing each task in order is necessary for completing the lesson.</span></span> <span data-ttu-id="4eb44-122">特定のレッスン内には、同様の結果を達成する実習もいくつか存在しますが、どのように完了するかは実習ごとに少しずつ違います。</span><span class="sxs-lookup"><span data-stu-id="4eb44-122">While in a particular lesson there may be several tasks that accomplish a similar outcome; however, how you complete each task is slightly different.</span></span> <span data-ttu-id="4eb44-123">これは、同じ実習を完了するのにも複数の方法が存在する場合がよくあるためです。また、前の実習で学習したスキルが身についているかどうかを確認するためでもあります。</span><span class="sxs-lookup"><span data-stu-id="4eb44-123">This is to show that there is often more than one way to complete a particular task, and to challenge you by using skills you learned in previous tasks.</span></span>  
  
 <span data-ttu-id="4eb44-124">各レッスンの目的は、 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]に含まれる多数の機能を使用して、インメモリ モードで実行される基本的なテーブル モデルを作成できるようになることです。</span><span class="sxs-lookup"><span data-stu-id="4eb44-124">The purpose of the lessons is to guide you through authoring a basic tabular model running in In-Memory mode by using many of the features included in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)].</span></span> <span data-ttu-id="4eb44-125">各レッスンは前のレッスンに基づいているので、順序どおりに完了する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4eb44-125">Because each lesson builds upon the previous lesson, you should complete the lessons in order.</span></span> <span data-ttu-id="4eb44-126">すべてのレッスンを完了すると、Analysis Services サーバー上に Adventure Works Internet Sales サンプル テーブル モデルが作成され、配置されます。</span><span class="sxs-lookup"><span data-stu-id="4eb44-126">Once you have completed all of the lessons, you will have authored and deployed the Adventure Works Internet Sales sample tabular model on an Analysis Services server.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4eb44-127">このチュートリアルでは、配置したテーブル モデル データベースを SQL Server Management Studio で管理する方法や、レポート クライアント アプリケーションを使用して配置済みのモデルに接続し、モデル データを参照する方法については説明しません。</span><span class="sxs-lookup"><span data-stu-id="4eb44-127">This tutorial does not provide lessons or information about managing a deployed tabular model database by using SQL Server Management Studio, or using a reporting client application to connect to a deployed model to browse model data.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="4eb44-128">前提条件</span><span class="sxs-lookup"><span data-stu-id="4eb44-128">Prerequisites</span></span>  
 <span data-ttu-id="4eb44-129">このチュートリアルを完了するには、以下が事前にインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="4eb44-129">In order to complete this tutorial, you must have the following prerequisites installed:</span></span>  
  
-   <span data-ttu-id="4eb44-130">テーブル モードで実行されている [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] Analysis Services インスタンス。</span><span class="sxs-lookup"><span data-stu-id="4eb44-130">[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] Analysis Services instance running in Tabular mode.</span></span>  
  
-   [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]<span data-ttu-id="4eb44-131">.</span><span class="sxs-lookup"><span data-stu-id="4eb44-131">.</span></span>  
  
-   <span data-ttu-id="4eb44-132">AdventureWorksDW サンプル データベース</span><span class="sxs-lookup"><span data-stu-id="4eb44-132">AdventureWorksDW sample database.</span></span> <span data-ttu-id="4eb44-133">このサンプル データベースには、このチュートリアルを完了するのに必要なデータが含まれています。</span><span class="sxs-lookup"><span data-stu-id="4eb44-133">This sample database includes the data necessary to complete this tutorial.</span></span> <span data-ttu-id="4eb44-134">サンプルデータベースをダウンロードするには、「」を参照してください [https://github.com/microsoft/sql-server-samples/releases/tag/adventureworks](https://github.com/microsoft/sql-server-samples/releases/tag/adventureworks) 。</span><span class="sxs-lookup"><span data-stu-id="4eb44-134">To download the sample database, see [https://github.com/microsoft/sql-server-samples/releases/tag/adventureworks](https://github.com/microsoft/sql-server-samples/releases/tag/adventureworks).</span></span>  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] <span data-ttu-id="4eb44-135">Excel 2003 以降 (レッスン 11 で "Excel で分析" 機能を使用するため)</span><span class="sxs-lookup"><span data-stu-id="4eb44-135">Excel 2003 or later (for use with the Analyze in Excel feature in lesson 11)</span></span>  
  
## <a name="lessons"></a><span data-ttu-id="4eb44-136">レッスン</span><span class="sxs-lookup"><span data-stu-id="4eb44-136">Lessons</span></span>  
 <span data-ttu-id="4eb44-137">このチュートリアルには次のレッスンが含まれています。</span><span class="sxs-lookup"><span data-stu-id="4eb44-137">This tutorial includes the following lessons:</span></span>  
  
|<span data-ttu-id="4eb44-138">レッスン</span><span class="sxs-lookup"><span data-stu-id="4eb44-138">Lesson</span></span>|<span data-ttu-id="4eb44-139">推定所要時間</span><span class="sxs-lookup"><span data-stu-id="4eb44-139">Estimated time to complete</span></span>|  
|------------|--------------------------------|  
|[<span data-ttu-id="4eb44-140">レッスン 1:新しいテーブル モデル プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="4eb44-140">Lesson 1: Create a New Tabular Model Project</span></span>](lesson-1-create-a-new-tabular-model-project.md)|<span data-ttu-id="4eb44-141">10 分</span><span class="sxs-lookup"><span data-stu-id="4eb44-141">10 minutes</span></span>|  
|[<span data-ttu-id="4eb44-142">レッスン 2: データを追加する</span><span class="sxs-lookup"><span data-stu-id="4eb44-142">Lesson 2: Add Data</span></span>](lesson-2-add-data.md)|<span data-ttu-id="4eb44-143">20 分</span><span class="sxs-lookup"><span data-stu-id="4eb44-143">20 minutes</span></span>|  
|[<span data-ttu-id="4eb44-144">レッスン 3:列名の変更</span><span class="sxs-lookup"><span data-stu-id="4eb44-144">Lesson 3: Rename Columns</span></span>](rename-columns.md)|<span data-ttu-id="4eb44-145">20 分</span><span class="sxs-lookup"><span data-stu-id="4eb44-145">20 minutes</span></span>|  
|[<span data-ttu-id="4eb44-146">レッスン 4:日付テーブルとしてマーク</span><span class="sxs-lookup"><span data-stu-id="4eb44-146">Lesson 4: Mark as Date Table</span></span>](lesson-3-mark-as-date-table.md)|<span data-ttu-id="4eb44-147">3 分</span><span class="sxs-lookup"><span data-stu-id="4eb44-147">3 minutes</span></span>|  
|<span data-ttu-id="4eb44-148">[レッスン 5: [リレーションシップの作成]](lesson-4-create-relationships.md)</span><span class="sxs-lookup"><span data-stu-id="4eb44-148">[Lesson 5: Create Relationships](lesson-4-create-relationships.md)</span></span>|<span data-ttu-id="4eb44-149">10 分</span><span class="sxs-lookup"><span data-stu-id="4eb44-149">10 minutes</span></span>|  
|[<span data-ttu-id="4eb44-150">レッスン 6: 計算列の作成</span><span class="sxs-lookup"><span data-stu-id="4eb44-150">Lesson 6: Create Calculated Columns</span></span>](lesson-5-create-calculated-columns.md)|<span data-ttu-id="4eb44-151">約 15 分</span><span class="sxs-lookup"><span data-stu-id="4eb44-151">15 minutes</span></span>|  
|[<span data-ttu-id="4eb44-152">レッスン 7: メジャーを作成する</span><span class="sxs-lookup"><span data-stu-id="4eb44-152">Lesson 7: Create Measures</span></span>](lesson-6-create-measures.md)|<span data-ttu-id="4eb44-153">30 分</span><span class="sxs-lookup"><span data-stu-id="4eb44-153">30 minutes</span></span>|  
|[<span data-ttu-id="4eb44-154">レッスン 8: 主要業績評価指標を作成する</span><span class="sxs-lookup"><span data-stu-id="4eb44-154">Lesson 8: Create Key Performance Indicators</span></span>](lesson-7-create-key-performance-indicators.md)|<span data-ttu-id="4eb44-155">約 15 分</span><span class="sxs-lookup"><span data-stu-id="4eb44-155">15 minutes</span></span>|  
|[<span data-ttu-id="4eb44-156">レッスン 9: パースペクティブを作成する</span><span class="sxs-lookup"><span data-stu-id="4eb44-156">Lesson 9: Create Perspectives</span></span>](lesson-8-create-perspectives.md)|<span data-ttu-id="4eb44-157">5 分</span><span class="sxs-lookup"><span data-stu-id="4eb44-157">5 minutes</span></span>|  
|[<span data-ttu-id="4eb44-158">レッスン 10: 階層を作成する</span><span class="sxs-lookup"><span data-stu-id="4eb44-158">Lesson 10: Create Hierarchies</span></span>](lesson-9-create-hierarchies.md)|<span data-ttu-id="4eb44-159">20 分</span><span class="sxs-lookup"><span data-stu-id="4eb44-159">20 minutes</span></span>|  
|[<span data-ttu-id="4eb44-160">レッスン 11:パーティションの作成</span><span class="sxs-lookup"><span data-stu-id="4eb44-160">Lesson 11: Create Partitions</span></span>](lesson-10-create-partitions.md)|<span data-ttu-id="4eb44-161">約 15 分</span><span class="sxs-lookup"><span data-stu-id="4eb44-161">15 minutes</span></span>|  
|[<span data-ttu-id="4eb44-162">レッスン 12:ロールの作成</span><span class="sxs-lookup"><span data-stu-id="4eb44-162">Lesson 12: Create Roles</span></span>](lesson-11-create-roles.md)|<span data-ttu-id="4eb44-163">約 15 分</span><span class="sxs-lookup"><span data-stu-id="4eb44-163">15 minutes</span></span>|  
|<span data-ttu-id="4eb44-164">[レッスン 13:[Excel で分析]](lesson-12-analyze-in-excel.md)</span><span class="sxs-lookup"><span data-stu-id="4eb44-164">[Lesson 13: Analyze in Excel](lesson-12-analyze-in-excel.md)</span></span>|<span data-ttu-id="4eb44-165">20 分</span><span class="sxs-lookup"><span data-stu-id="4eb44-165">20 minutes</span></span>|  
|[<span data-ttu-id="4eb44-166">レッスン 14:配置</span><span class="sxs-lookup"><span data-stu-id="4eb44-166">Lesson 14: Deploy</span></span>](lesson-13-deploy.md)|<span data-ttu-id="4eb44-167">5 分</span><span class="sxs-lookup"><span data-stu-id="4eb44-167">5 minutes</span></span>|  
  
## <a name="supplemental-lessons"></a><span data-ttu-id="4eb44-168">補足のレッスン</span><span class="sxs-lookup"><span data-stu-id="4eb44-168">Supplemental Lessons</span></span>  
 <span data-ttu-id="4eb44-169">このチュートリアルには、 [補足レッスン](../tutorials/supplemental-lessons.md)も含まれています。</span><span class="sxs-lookup"><span data-stu-id="4eb44-169">This tutorial also includes [Supplemental Lessons](../tutorials/supplemental-lessons.md).</span></span> <span data-ttu-id="4eb44-170">このセクションのトピックはチュートリアルを完了するのに必須ではありませんが、高度なテーブル モデル作成機能をより深く理解するために役立ちます。</span><span class="sxs-lookup"><span data-stu-id="4eb44-170">Topics in this section are not required to complete the tutorial, but can be helpful in better understanding advanced tabular model authoring features.</span></span>  
  
 <span data-ttu-id="4eb44-171">このチュートリアルには次の補足レッスンが含まれています。</span><span class="sxs-lookup"><span data-stu-id="4eb44-171">This tutorial includes the following supplemental lessons:</span></span>  
  
|<span data-ttu-id="4eb44-172">レッスン</span><span class="sxs-lookup"><span data-stu-id="4eb44-172">Lesson</span></span>|<span data-ttu-id="4eb44-173">推定所要時間</span><span class="sxs-lookup"><span data-stu-id="4eb44-173">Estimated time to complete</span></span>|  
|------------|--------------------------------|  
|[<span data-ttu-id="4eb44-174">行フィルターを使用した動的なセキュリティの実装</span><span class="sxs-lookup"><span data-stu-id="4eb44-174">Implement Dynamic Security by Using Row Filters</span></span>](../tutorials/implement-dynamic-security-by-using-row-filters.md)|<span data-ttu-id="4eb44-175">30 分</span><span class="sxs-lookup"><span data-stu-id="4eb44-175">30 minutes</span></span>|  
|<span data-ttu-id="4eb44-176">[Power View レポートのレポートプロパティの構成](supplemental-lesson-configure-reporting-properties-for-power-view-reports.md)Power View レポートのレポートプロパティの構成</span><span class="sxs-lookup"><span data-stu-id="4eb44-176">[Configure Reporting Properties for Power View Reports](supplemental-lesson-configure-reporting-properties-for-power-view-reports.md)Configure Reporting Properties for Power View Reports</span></span>|<span data-ttu-id="4eb44-177">30 分</span><span class="sxs-lookup"><span data-stu-id="4eb44-177">30 minutes</span></span>|  
  
## <a name="next-step"></a><span data-ttu-id="4eb44-178">次の手順</span><span class="sxs-lookup"><span data-stu-id="4eb44-178">Next Step</span></span>  
 <span data-ttu-id="4eb44-179">チュートリアルを開始するには、 [「レッスン 1: 新しいテーブル モデル プロジェクトの作成」](lesson-1-create-a-new-tabular-model-project.md)に進みます。</span><span class="sxs-lookup"><span data-stu-id="4eb44-179">To begin the tutorial, continue to the first lesson: [Lesson 1: Create a New Tabular Model Project](lesson-1-create-a-new-tabular-model-project.md).</span></span>  
  
  
