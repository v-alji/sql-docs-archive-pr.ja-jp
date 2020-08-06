---
title: 'レッスン 2: キューブの定義と配置 |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: bb62e3c9-462f-4ad2-ac8e-92e2f9e9cc28
author: minewiskan
ms.author: owend
ms.openlocfilehash: a2c043920ac646ec4da9eaa2aace4bf6f48e694c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643603"
---
# <a name="lesson-2-defining-and-deploying-a-cube"></a><span data-ttu-id="42132-102">レッスン 2: キューブの定義と配置</span><span class="sxs-lookup"><span data-stu-id="42132-102">Lesson 2: Defining and Deploying a Cube</span></span>
  <span data-ttu-id="42132-103">プロジェクトでデータソースビューを定義したら [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 、初期キューブを定義でき [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="42132-103">After you define a data source view in your [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project, you are ready to define an initial [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] cube.</span></span>  
  
 <span data-ttu-id="42132-104">キューブ ウィザードでは、キューブとそのディメンションを一度に定義できます。</span><span class="sxs-lookup"><span data-stu-id="42132-104">You can define a cube and its dimensions in a single pass using the Cube Wizard.</span></span> <span data-ttu-id="42132-105">1 つ以上のディメンションを定義してから、キューブ ウィザードを使用して、そのディメンションを使用するキューブを定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="42132-105">Alternatively, you can define one or more dimensions and then use the Cube Wizard to define a cube that uses those dimensions.</span></span> <span data-ttu-id="42132-106">複雑なソリューションを設計する場合は、通常、ディメンションの定義から始めます。</span><span class="sxs-lookup"><span data-stu-id="42132-106">If you are designing a complex solution, you generally start by defining the dimensions.</span></span> <span data-ttu-id="42132-107">詳細については、 [「多次元モデル内のディメンション」](multidimensional-models/dimensions-in-multidimensional-models.md) または [「多次元モデルのキューブ」](multidimensional-models/cubes-in-multidimensional-models.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="42132-107">For more information, see [Dimensions in Multidimensional Models](multidimensional-models/dimensions-in-multidimensional-models.md) or [Cubes in Multidimensional Models](multidimensional-models/cubes-in-multidimensional-models.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="42132-108">このチュートリアルの各レッスンの操作内容が反映されたプロジェクトを、オンラインで入手できます。</span><span class="sxs-lookup"><span data-stu-id="42132-108">Completed projects for all of the lessons in this tutorial are available online.</span></span> <span data-ttu-id="42132-109">途中のレッスンから開始する場合は、前のレッスンの操作内容が反映されたプロジェクトを作業の開始点として使用できます。</span><span class="sxs-lookup"><span data-stu-id="42132-109">You can jump ahead to any lesson by using the completed project from the previous lesson as a starting point.</span></span> <span data-ttu-id="42132-110">このチュートリアルのサンプル プロジェクトをダウンロードするには、[ここ](https://go.microsoft.com/fwlink/?LinkID=221866) をクリックしてください。</span><span class="sxs-lookup"><span data-stu-id="42132-110">[Click here](https://go.microsoft.com/fwlink/?LinkID=221866) to download the sample projects that go with this tutorial.</span></span>  
  
 <span data-ttu-id="42132-111">このレッスンの内容は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="42132-111">This lesson contains the following tasks:</span></span>  
  
 [<span data-ttu-id="42132-112">ディメンションの定義</span><span class="sxs-lookup"><span data-stu-id="42132-112">Defining a Dimension</span></span>](lesson-2-1-defining-a-dimension.md)  
 <span data-ttu-id="42132-113">この実習では、ディメンション ウィザードを使用してディメンションを定義します。</span><span class="sxs-lookup"><span data-stu-id="42132-113">In this task, you use the Dimension Wizard to define a dimension.</span></span>  
  
 [<span data-ttu-id="42132-114">キューブの定義</span><span class="sxs-lookup"><span data-stu-id="42132-114">Defining a Cube</span></span>](lesson-2-2-defining-a-cube.md)  
 <span data-ttu-id="42132-115">この実習では、キューブ ウィザードを使用して最初の [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] キューブを定義します。</span><span class="sxs-lookup"><span data-stu-id="42132-115">In this task, you use the Cube Wizard to define an initial [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] cube.</span></span>  
  
 [<span data-ttu-id="42132-116">ディメンションへの属性の追加</span><span class="sxs-lookup"><span data-stu-id="42132-116">Adding Attributes to Dimensions</span></span>](lesson-2-3-adding-attributes-to-dimensions.md)  
 <span data-ttu-id="42132-117">この実習では、作成したディメンションに属性を追加します。</span><span class="sxs-lookup"><span data-stu-id="42132-117">In this task, you add attributes to the dimensions that you created.</span></span>  
  
 [<span data-ttu-id="42132-118">キューブとディメンションのプロパティの確認</span><span class="sxs-lookup"><span data-stu-id="42132-118">Reviewing Cube and Dimension Properties</span></span>](lesson-2-4-reviewing-cube-and-dimension-properties.md)  
 <span data-ttu-id="42132-119">この実習では、キューブ ウィザードで定義したキューブの構造を確認します。</span><span class="sxs-lookup"><span data-stu-id="42132-119">In this task, you review the structure of the cube that you defined by using the Cube Wizard.</span></span>  
  
 [<span data-ttu-id="42132-120">Analysis Services プロジェクトの配置</span><span class="sxs-lookup"><span data-stu-id="42132-120">Deploying an Analysis Services Project</span></span>](lesson-2-5-deploying-an-analysis-services-project.md)  
 <span data-ttu-id="42132-121">この実習では、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] プロジェクトを [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]のローカル インスタンスに配置し、配置プロパティについて学習します。</span><span class="sxs-lookup"><span data-stu-id="42132-121">In this task, you deploy the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project to your local instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], and learn about certain deployment properties.</span></span>  
  
 [<span data-ttu-id="42132-122">キューブの表示</span><span class="sxs-lookup"><span data-stu-id="42132-122">Browsing the Cube</span></span>](lesson-2-6-browsing-the-cube.md)  
 <span data-ttu-id="42132-123">この実習では、Excel または MDX クエリ デザイナーを使用して、キューブとディメンションのデータを表示します。</span><span class="sxs-lookup"><span data-stu-id="42132-123">In this task, you browse the cube and dimension data by using Excel or the MDX query designer.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="42132-124">次のレッスン</span><span class="sxs-lookup"><span data-stu-id="42132-124">Next Lesson</span></span>  
 [<span data-ttu-id="42132-125">レッスン 3:メジャー、属性、および階層の修正</span><span class="sxs-lookup"><span data-stu-id="42132-125">Lesson 3: Modifying Measures, Attributes and Hierarchies</span></span>](lesson-3-modifying-measures-attributes-and-hierarchies.md)  
  
## <a name="see-also"></a><span data-ttu-id="42132-126">参照</span><span class="sxs-lookup"><span data-stu-id="42132-126">See Also</span></span>  
 <span data-ttu-id="42132-127">[Analysis Services チュートリアルのシナリオ](analysis-services-tutorial-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="42132-127">[Analysis Services Tutorial Scenario](analysis-services-tutorial-scenario.md) </span></span>  
 <span data-ttu-id="42132-128">[Adventure Works チュートリアル &#40;の多次元モデリング&#41;](multidimensional-modeling-adventure-works-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="42132-128">[Multidimensional Modeling &#40;Adventure Works Tutorial&#41;](multidimensional-modeling-adventure-works-tutorial.md) </span></span>  
 <span data-ttu-id="42132-129">[多次元モデル内のディメンション](multidimensional-models/dimensions-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="42132-129">[Dimensions in Multidimensional Models](multidimensional-models/dimensions-in-multidimensional-models.md) </span></span>  
 <span data-ttu-id="42132-130">[多次元モデルのキューブ](multidimensional-models/cubes-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="42132-130">[Cubes in Multidimensional Models](multidimensional-models/cubes-in-multidimensional-models.md) </span></span>  
 <span data-ttu-id="42132-131">[SSDT&#41;&#40;Analysis Services プロジェクトのプロパティを構成する](multidimensional-models/configure-analysis-services-project-properties-ssdt.md) </span><span class="sxs-lookup"><span data-stu-id="42132-131">[Configure Analysis Services Project Properties &#40;SSDT&#41;](multidimensional-models/configure-analysis-services-project-properties-ssdt.md) </span></span>  
 <span data-ttu-id="42132-132">[ビルド Analysis Services プロジェクト &#40;SSDT&#41;](multidimensional-models/build-analysis-services-projects-ssdt.md) </span><span class="sxs-lookup"><span data-stu-id="42132-132">[Build Analysis Services Projects &#40;SSDT&#41;](multidimensional-models/build-analysis-services-projects-ssdt.md) </span></span>  
 [<span data-ttu-id="42132-133">Analysis Services プロジェクトの配置 &#40;SSDT&#41;</span><span class="sxs-lookup"><span data-stu-id="42132-133">Deploy Analysis Services Projects &#40;SSDT&#41;</span></span>](multidimensional-models/deploy-analysis-services-projects-ssdt.md)  
  
  
