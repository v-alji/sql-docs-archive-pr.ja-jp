---
title: 多次元モデリング (Adventure Works チュートリアル) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- tutorials [Analysis Services]
- Analysis Services, tutorials
ms.assetid: db55e226-601a-4026-8651-573195555a59
author: minewiskan
ms.author: owend
ms.openlocfilehash: cd2e8f856d36cab045e6cbc4d34f7cfeffac3c3c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642995"
---
# <a name="multidimensional-modeling-adventure-works-tutorial"></a><span data-ttu-id="2b0ee-102">多次元モデリング (Adventure Works チュートリアル)</span><span class="sxs-lookup"><span data-stu-id="2b0ee-102">Multidimensional Modeling (Adventure Works Tutorial)</span></span>
  <span data-ttu-id="2b0ee-103">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] のチュートリアルへようこそ。</span><span class="sxs-lookup"><span data-stu-id="2b0ee-103">Welcome to the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial.</span></span> <span data-ttu-id="2b0ee-104">このチュートリアルでは、架空の会社 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] の例を使用しながら、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] で [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] プロジェクトの開発と配置を行う方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="2b0ee-104">This tutorial describes how to use [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] to develop and deploy an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project, using the fictitious company [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] for all examples.</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="2b0ee-105">学習する内容</span><span class="sxs-lookup"><span data-stu-id="2b0ee-105">What You Will Learn</span></span>  
 <span data-ttu-id="2b0ee-106">このチュートリアルでは、次の内容を学習します。</span><span class="sxs-lookup"><span data-stu-id="2b0ee-106">In this tutorial, you will learn the following:</span></span>  
  
-   <span data-ttu-id="2b0ee-107">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] の [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]プロジェクトにおいて、データ ソース、データ ソース ビュー、ディメンション、属性、属性リレーションシップ、階層、およびキューブを定義する方法</span><span class="sxs-lookup"><span data-stu-id="2b0ee-107">How to define data sources, data source views, dimensions, attributes, attribute relationships, hierarchies, and cubes in an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project within [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)].</span></span>  
  
-   <span data-ttu-id="2b0ee-108">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] プロジェクトを [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]のインスタンスに配置してキューブとディメンションのデータを表示する方法と、配置したオブジェクトを処理して、基になるデータ ソースからのデータをオブジェクトに格納する方法</span><span class="sxs-lookup"><span data-stu-id="2b0ee-108">How to view cube and dimension data by deploying the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project to an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], and how to then process the deployed objects to populate them with data from the underlying data source.</span></span>  
  
-   <span data-ttu-id="2b0ee-109">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] プロジェクトのメジャー、ディメンション、階層、属性、メジャー グループを変更する方法と、変更した差分を開発サーバーの配置済みキューブに配置する方法</span><span class="sxs-lookup"><span data-stu-id="2b0ee-109">How to modify the measures, dimensions, hierarchies, attributes, and measure groups in the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project, and how to then deploy the incremental changes to the deployed cube on the development server.</span></span>  
  
-   <span data-ttu-id="2b0ee-110">キューブ内で計算、主要業績評価指標 (KPI)、アクション、パースペクティブ、翻訳、およびセキュリティ ロールを定義する方法</span><span class="sxs-lookup"><span data-stu-id="2b0ee-110">How to define calculations, Key Performance Indicators (KPIs), actions, perspectives, translations, and security roles within a cube.</span></span>  
  
 <span data-ttu-id="2b0ee-111">これらのレッスンのコンテキストをよりよく理解できるように、このチュートリアルにはシナリオの説明が付属しています。</span><span class="sxs-lookup"><span data-stu-id="2b0ee-111">A scenario description accompanies this tutorial so that you can better understand the context for these lessons.</span></span> <span data-ttu-id="2b0ee-112">詳細については、「 [Analysis Services のチュートリアル シナリオ](analysis-services-tutorial-scenario.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2b0ee-112">For more information, see [Analysis Services Tutorial Scenario](analysis-services-tutorial-scenario.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="2b0ee-113">前提条件</span><span class="sxs-lookup"><span data-stu-id="2b0ee-113">Prerequisites</span></span>  
 <span data-ttu-id="2b0ee-114">このチュートリアルのすべてのレッスンを完了するには、サンプル データ、サンプル プロジェクト ファイル、およびソフトウェアが必要です。</span><span class="sxs-lookup"><span data-stu-id="2b0ee-114">You will need sample data, sample project files, and software to complete all of the lessons in this tutorial.</span></span> <span data-ttu-id="2b0ee-115">このチュートリアルの必要条件を入手およびインストールする方法については、「 [Analysis Services 多次元モデリング チュートリアル用のサンプル データおよびプロジェクトのインストール](install-sample-data-and-projects.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2b0ee-115">For instructions on how to find and install the prerequisites for this tutorial, see [Install Sample Data and Projects for the Analysis Services Multidimensional Modeling Tutorial](install-sample-data-and-projects.md).</span></span>  
  
 <span data-ttu-id="2b0ee-116">また、このチュートリアルを正常に完了するには、次の権限が付与されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="2b0ee-116">Additionally, the following permissions must be in place to successfully complete this tutorial:</span></span>  
  
-   <span data-ttu-id="2b0ee-117">作業者が、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] コンピューターの Administrators ローカル グループのメンバーであるか、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]インスタンスのサーバー管理ロールのメンバーである。</span><span class="sxs-lookup"><span data-stu-id="2b0ee-117">You must be a member of the Administrators local group on the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] computer or be a member of the server administration role in the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="2b0ee-118">作業者が、 **AdventureWorksDW2012** サンプル データベースでの読み取り権限を持っている。</span><span class="sxs-lookup"><span data-stu-id="2b0ee-118">You must have Read permissions in the **AdventureWorksDW2012** sample database.</span></span> <span data-ttu-id="2b0ee-119">このサンプル データベースは、 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] リリースで有効です。</span><span class="sxs-lookup"><span data-stu-id="2b0ee-119">This sample database is valid for the [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] release.</span></span>  
  
## <a name="lessons"></a><span data-ttu-id="2b0ee-120">レッスン</span><span class="sxs-lookup"><span data-stu-id="2b0ee-120">Lessons</span></span>  
 <span data-ttu-id="2b0ee-121">このチュートリアルには次のレッスンが含まれています。</span><span class="sxs-lookup"><span data-stu-id="2b0ee-121">This tutorial includes the following lessons.</span></span>  
  
|<span data-ttu-id="2b0ee-122">レッスン</span><span class="sxs-lookup"><span data-stu-id="2b0ee-122">Lesson</span></span>|<span data-ttu-id="2b0ee-123">推定所要時間</span><span class="sxs-lookup"><span data-stu-id="2b0ee-123">Estimated time to complete</span></span>|  
|------------|--------------------------------|  
|[<span data-ttu-id="2b0ee-124">レッスン 1:Analysis Services プロジェクト内でのデータ ソース ビューの定義</span><span class="sxs-lookup"><span data-stu-id="2b0ee-124">Lesson 1: Defining a Data Source View within an Analysis Services Project</span></span>](lesson-1-defining-a-data-source-view-within-an-analysis-services-project.md)|<span data-ttu-id="2b0ee-125">約 15 分</span><span class="sxs-lookup"><span data-stu-id="2b0ee-125">15 minutes</span></span>|  
|[<span data-ttu-id="2b0ee-126">レッスン 2: キューブの定義と配置</span><span class="sxs-lookup"><span data-stu-id="2b0ee-126">Lesson 2: Defining and Deploying a Cube</span></span>](lesson-2-defining-and-deploying-a-cube.md)|<span data-ttu-id="2b0ee-127">30 分</span><span class="sxs-lookup"><span data-stu-id="2b0ee-127">30 minutes</span></span>|  
|[<span data-ttu-id="2b0ee-128">レッスン 3:メジャー、属性、および階層の修正</span><span class="sxs-lookup"><span data-stu-id="2b0ee-128">Lesson 3: Modifying Measures, Attributes and Hierarchies</span></span>](lesson-3-modifying-measures-attributes-and-hierarchies.md)|<span data-ttu-id="2b0ee-129">45 分</span><span class="sxs-lookup"><span data-stu-id="2b0ee-129">45 minutes</span></span>|  
|[<span data-ttu-id="2b0ee-130">レッスン 4:高度な属性およびディメンションのプロパティの定義</span><span class="sxs-lookup"><span data-stu-id="2b0ee-130">Lesson 4: Defining Advanced Attribute and Dimension Properties</span></span>](lesson-4-defining-advanced-attribute-and-dimension-properties.md)|<span data-ttu-id="2b0ee-131">120 分</span><span class="sxs-lookup"><span data-stu-id="2b0ee-131">120 minutes</span></span>|  
|[<span data-ttu-id="2b0ee-132">レッスン 5: ディメンションおよびメジャー グループ間のリレーションシップの定義</span><span class="sxs-lookup"><span data-stu-id="2b0ee-132">Lesson 5: Defining Relationships Between Dimensions and Measure Groups</span></span>](lesson-5-defining-relationships-between-dimensions-and-measure-groups.md)|<span data-ttu-id="2b0ee-133">45 分</span><span class="sxs-lookup"><span data-stu-id="2b0ee-133">45 minutes</span></span>|  
|[<span data-ttu-id="2b0ee-134">レッスン 6: 計算の定義</span><span class="sxs-lookup"><span data-stu-id="2b0ee-134">Lesson 6: Defining Calculations</span></span>](lesson-6-defining-calculations.md)|<span data-ttu-id="2b0ee-135">45 分</span><span class="sxs-lookup"><span data-stu-id="2b0ee-135">45 minutes</span></span>|  
|[<span data-ttu-id="2b0ee-136">レッスン 7: 主要業績評価指標 (KPI) の定義</span><span class="sxs-lookup"><span data-stu-id="2b0ee-136">Lesson 7: Defining Key Performance Indicators &#40;KPIs&#41;</span></span>](lesson-7-defining-key-performance-indicators-kpis.md)|<span data-ttu-id="2b0ee-137">30 分</span><span class="sxs-lookup"><span data-stu-id="2b0ee-137">30 minutes</span></span>|  
|[<span data-ttu-id="2b0ee-138">レッスン 8: アクションの定義</span><span class="sxs-lookup"><span data-stu-id="2b0ee-138">Lesson 8: Defining Actions</span></span>](lesson-8-defining-actions.md)|<span data-ttu-id="2b0ee-139">30 分</span><span class="sxs-lookup"><span data-stu-id="2b0ee-139">30 minutes</span></span>|  
|[<span data-ttu-id="2b0ee-140">レッスン 9: パースペクティブと翻訳の定義</span><span class="sxs-lookup"><span data-stu-id="2b0ee-140">Lesson 9: Defining Perspectives and Translations</span></span>](lesson-9-defining-perspectives-and-translations.md)|<span data-ttu-id="2b0ee-141">30 分</span><span class="sxs-lookup"><span data-stu-id="2b0ee-141">30 minutes</span></span>|  
|[<span data-ttu-id="2b0ee-142">レッスン 10: 管理ロールの定義</span><span class="sxs-lookup"><span data-stu-id="2b0ee-142">Lesson 10: Defining Administrative Roles</span></span>](lesson-10-defining-administrative-roles.md)|<span data-ttu-id="2b0ee-143">約 15 分</span><span class="sxs-lookup"><span data-stu-id="2b0ee-143">15 minutes</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="2b0ee-144">このチュートリアルで作成するキューブ データベースは、CodePlex サイトでダウンロードできる Adventure Works サンプル データベースの一部である [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 多次元モデル プロジェクトの簡易バージョンです。</span><span class="sxs-lookup"><span data-stu-id="2b0ee-144">The cube database that you will create in this tutorial is a simplified version of the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] multidimensional model project that is part of the Adventure Works sample databases available for download on the codeplex site.</span></span> <span data-ttu-id="2b0ee-145">Adventure Works 多次元データベースのチュートリアルバージョンは、すぐに改善する必要がある特定のスキルを重視するために簡略化されています。</span><span class="sxs-lookup"><span data-stu-id="2b0ee-145">The tutorial version of the Adventure Works multidimensional database is simplified to bring greater focus to the specific skills that you will want to improve right away.</span></span> <span data-ttu-id="2b0ee-146">チュートリアルの終了後は、自分で多次元モデル プロジェクトを用意してさまざまな操作を行うと、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 多次元モデリングの理解が深まります。</span><span class="sxs-lookup"><span data-stu-id="2b0ee-146">After you complete the tutorial, consider exploring the multidimensional model project on your own to further your understanding of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] multidimensional modeling.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="2b0ee-147">次の手順</span><span class="sxs-lookup"><span data-stu-id="2b0ee-147">Next Step</span></span>  
 <span data-ttu-id="2b0ee-148">チュートリアルを開始するには、最初のレッスン「 [レッスン 1: Analysis Services プロジェクト内でのデータ ソース ビューの定義](lesson-1-defining-a-data-source-view-within-an-analysis-services-project.md)」に進んでください。</span><span class="sxs-lookup"><span data-stu-id="2b0ee-148">To begin the tutorial, continue to the first lesson: [Lesson 1: Defining a Data Source View within an Analysis Services Project](lesson-1-defining-a-data-source-view-within-an-analysis-services-project.md).</span></span>  
  
  
