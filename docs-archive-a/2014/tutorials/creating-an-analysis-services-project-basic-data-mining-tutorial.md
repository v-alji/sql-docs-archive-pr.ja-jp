---
title: Analysis Services プロジェクトの作成 (基本的なデータマイニングチュートリアル) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 784c0401-0358-4117-9c85-4e8220ce71d9
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 83eb808bc7d18ebe715d309d9f911c010ee172d1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632231"
---
# <a name="creating-an-analysis-services-project-basic-data-mining-tutorial"></a><span data-ttu-id="92e59-102">Analysis Services プロジェクトの作成 (基本的なデータ マイニング チュートリアル)</span><span class="sxs-lookup"><span data-stu-id="92e59-102">Creating an Analysis Services Project (Basic Data Mining Tutorial)</span></span>
  <span data-ttu-id="92e59-103">各 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] プロジェクトは、1つのデータベース内のオブジェクトを定義 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] します。</span><span class="sxs-lookup"><span data-stu-id="92e59-103">Each [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project defines the objects in a single [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.</span></span> <span data-ttu-id="92e59-104">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベースには、さまざまな種類のオブジェクトが含まれています。</span><span class="sxs-lookup"><span data-stu-id="92e59-104">An [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database can contains many different types of objects</span></span>  
  
-   <span data-ttu-id="92e59-105">多次元モデル (キューブ)</span><span class="sxs-lookup"><span data-stu-id="92e59-105">Multidimensional models (cubes)</span></span>  
  
-   <span data-ttu-id="92e59-106">マイニング構造とマイニング モデル</span><span class="sxs-lookup"><span data-stu-id="92e59-106">Mining structures and mining models</span></span>  
  
-   <span data-ttu-id="92e59-107">データ ソース、データ ソース ビューとカスタム アセンブリなどのサポート オブジェクト</span><span class="sxs-lookup"><span data-stu-id="92e59-107">Supporting objects such as data sources, data source views, and custom assemblies</span></span>  
  
 <span data-ttu-id="92e59-108">データ マイニングを実行するうえで、キューブは **必須ではない** ことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="92e59-108">Note that you **do not** require a cube to do data mining.</span></span> <span data-ttu-id="92e59-109">既存のキューブに対してデータ マイニングを実行する必要がある場合は、キューブを作成したときに使用したのと同じプロジェクトに対して、データ マイニング モデルを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="92e59-109">If you need to perform data mining on an existing cube, you should add the data mining models to the same project you used to build the cube.</span></span> <span data-ttu-id="92e59-110">ただし、キューブが関係していない場合は、ほとんどの目的でデータ ウェアハウスなどのリレーショナル データ ソースに対してモデルを作成することができ、より高いパフォーマンスを達成できます。</span><span class="sxs-lookup"><span data-stu-id="92e59-110">However, for most purposes you can build your models on relational data sources, such as a data warehouse, and get better performance if a cube is not involved.</span></span>  
  
 <span data-ttu-id="92e59-111">このチュートリアルでは、データ ソースとして、 [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)]というリレーショナル データ ウェアハウスを使用します。</span><span class="sxs-lookup"><span data-stu-id="92e59-111">In this tutorial you will use a relational data warehouse, [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)], as the data source.</span></span> <span data-ttu-id="92e59-112">データ マイニングの目的のみで使用する `BasicDataMining` という名前の [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベースに、すべてのデータ マイニング オブジェクトを配置します。</span><span class="sxs-lookup"><span data-stu-id="92e59-112">You will deploy all your data mining objects to an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database named `BasicDataMining`, used just for data mining.</span></span>  
  
 <span data-ttu-id="92e59-113">既定では、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] は新しいプロジェクトに対して **localhost** インスタンスを使用します。</span><span class="sxs-lookup"><span data-stu-id="92e59-113">By default, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] uses the **localhost** instance for new projects.</span></span> <span data-ttu-id="92e59-114">名前付きインスタンスまたは別のサーバーを使用している場合は、まずプロジェクトを作成して開き、その後でインスタンス名を変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="92e59-114">If you are using a named instance or a different server, you must first create and open the project and then change the instance name.</span></span>  
  
 <span data-ttu-id="92e59-115">プロジェクトの詳細については [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 、「 [Analysis Services プロジェクトの作成](../analysis-services/lesson-1-1-creating-an-analysis-services-project.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="92e59-115">For more information about [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] projects, see [Creating an Analysis Services Project](../analysis-services/lesson-1-1-creating-an-analysis-services-project.md).</span></span>  
  
### <a name="to-create-an-analysis-services-project"></a><span data-ttu-id="92e59-116">Analysis Services プロジェクトを作成するには</span><span class="sxs-lookup"><span data-stu-id="92e59-116">To create an Analysis Services project</span></span>  
  
1.  <span data-ttu-id="92e59-117">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]を開きます。</span><span class="sxs-lookup"><span data-stu-id="92e59-117">Open [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="92e59-118">**[ファイル]** メニューの **[新規作成]** をポイントし、 **[プロジェクト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="92e59-118">On the **File** menu, point to **New**, and then select **Project**.</span></span>  
  
3.  <span data-ttu-id="92e59-119">**[プロジェクトの種類]** ペインで、 **[ビジネス インテリジェンス プロジェクト]** が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="92e59-119">Verify that **Business Intelligence Projects** is selected in the **Project types** pane.</span></span>  
  
4.  <span data-ttu-id="92e59-120">**[テンプレート]** ペインで、 **[Analysis Services 多次元およびデータ マイニング プロジェクト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="92e59-120">In the **Templates** pane, select **Analysis Services Multidimensional and Data Mining Project**.</span></span>  
  
5.  <span data-ttu-id="92e59-121">[**名前**] ボックスに、新しいプロジェクトの名前を指定し `BasicDataMining` ます。</span><span class="sxs-lookup"><span data-stu-id="92e59-121">In the **Name** box, name the new project `BasicDataMining`.</span></span>  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
### <a name="to-change-the-instance-where-data-mining-objects-are-stored"></a><span data-ttu-id="92e59-122">データ マイニング オブジェクトを格納するインスタンスを変更するには</span><span class="sxs-lookup"><span data-stu-id="92e59-122">To change the instance where data mining objects are stored</span></span>  
  
1.  <span data-ttu-id="92e59-123">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で、 **[プロジェクト]** メニューの **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="92e59-123">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], on the **Project** menu, select **Properties**.</span></span>  
  
2.  <span data-ttu-id="92e59-124">**[プロパティ ページ]** ペインの左側にある **[構成プロパティ]** で、 **[配置]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="92e59-124">On the left side of the **Property Pages** pane, under **Configuration Properties**, click **Deployment**.</span></span>  
  
3.  <span data-ttu-id="92e59-125">**[プロパティ ページ]** ペインの右側にある **[対象]** で、 **[サーバー]** の名前が **localhost**になっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="92e59-125">On the right side of the **Property Pages** pane, under **Target**, verify that the **Server** name is **localhost**.</span></span> <span data-ttu-id="92e59-126">別のインスタンスを使用する場合は、インスタンスの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="92e59-126">If you are using a different instance, type the name of the instance.</span></span> [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="92e59-127">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="92e59-127">Next Task in Lesson</span></span>  
 [<span data-ttu-id="92e59-128">データソースの作成 &#40;基本的なデータマイニングチュートリアル&#41;</span><span class="sxs-lookup"><span data-stu-id="92e59-128">Creating a Data Source &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/creating-a-data-source-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="92e59-129">参照</span><span class="sxs-lookup"><span data-stu-id="92e59-129">See Also</span></span>  
 <span data-ttu-id="92e59-130">[ビルド Analysis Services プロジェクト &#40;SSDT&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/build-analysis-services-projects-ssdt) </span><span class="sxs-lookup"><span data-stu-id="92e59-130">[Build Analysis Services Projects &#40;SSDT&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/build-analysis-services-projects-ssdt) </span></span>  
 [<span data-ttu-id="92e59-131">Analysis Services プロジェクトの作成 (SSDT)</span><span class="sxs-lookup"><span data-stu-id="92e59-131">Create an Analysis Services Project &#40;SSDT&#41;</span></span>](https://docs.microsoft.com/analysis-services/multidimensional-models/create-an-analysis-services-project-ssdt)  
  
  
