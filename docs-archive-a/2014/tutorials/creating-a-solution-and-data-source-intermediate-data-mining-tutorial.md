---
title: ソリューションとデータソースの作成 (中級者向けデータマイニングチュートリアル) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 0488b231-1045-4169-aabb-c1005d86ca30
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 48009fae653c4c1a231380e8d286363168ae28d6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633708"
---
# <a name="creating-a-solution-and-data-source-intermediate-data-mining-tutorial"></a><span data-ttu-id="f51bc-102">ソリューションとデータ ソースの作成 (中級者向けデータ マイニング チュートリアル)</span><span class="sxs-lookup"><span data-stu-id="f51bc-102">Creating a Solution and Data Source (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="f51bc-103">データ マイニングを使用するには、最初に [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] で **[Analysis Services 多次元およびデータ マイニング プロジェクト]** テンプレートを使用して、プロジェクトを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f51bc-103">To work with data mining, you must first create a project in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] using the template, **Analysis Services Multidimensional and Data Mining Project**.</span></span> <span data-ttu-id="f51bc-104">テンプレートを開くと、データ ソース、マイニング構造、マイニング モデル、さらにマイニング構造で多次元データが使用される場合はキューブまで、データ マイニングに必要なすべてのスキーマがデザイナーに読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="f51bc-104">When you open the template, it loads into the designer all the schemas that you might need for data mining: data sources, mining structures and mining models, and even cubes if your mining structure uses multidimensional data.</span></span>  
  
 <span data-ttu-id="f51bc-105">プロジェクトを作成すると、ソリューションは配置されるまでローカル ファイルとして保存されます。</span><span class="sxs-lookup"><span data-stu-id="f51bc-105">When you create the project, your solution is stored as a local file until the solution is deployed.</span></span> <span data-ttu-id="f51bc-106">ソリューションを配置すると、プロジェクトのプロパティに指定された [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] サーバーが [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] によって検索され、プロジェクトと同じ名前の新しい [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベースが作成されます。</span><span class="sxs-lookup"><span data-stu-id="f51bc-106">When you deploy the solution, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] looks for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] server specified in the project properties, and creates a new [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database with the same name as the project.</span></span> <span data-ttu-id="f51bc-107">既定では、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] は新しいプロジェクトに対して **localhost** インスタンスを使用します。</span><span class="sxs-lookup"><span data-stu-id="f51bc-107">By default, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] uses the **localhost** instance for new projects.</span></span> <span data-ttu-id="f51bc-108">名前付きインスタンスを使用している場合、または既定のインスタンスに別の名前を指定した場合は、プロジェクトの配置データベース プロパティを、データ マイニング オブジェクトを作成する場所に変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f51bc-108">If you are using a named instance, or if you specified a different name for the default instance, you must change the deployment database property of the project to the location where you want to create your data mining objects.</span></span>  
  
 <span data-ttu-id="f51bc-109">プロジェクトの詳細については [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 、「 [Create a Analysis Services PROJECT &#40;SSDT&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/create-an-analysis-services-project-ssdt)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f51bc-109">For more information about [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] projects, see [Create an Analysis Services Project &#40;SSDT&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/create-an-analysis-services-project-ssdt).</span></span>  
  
### <a name="to-create-a-new-analysis-services-project-for-this-tutorial"></a><span data-ttu-id="f51bc-110">このチュートリアル用の新しい Analysis Services プロジェクトを作成するには</span><span class="sxs-lookup"><span data-stu-id="f51bc-110">To create a new Analysis Services project for this tutorial</span></span>  
  
1.  <span data-ttu-id="f51bc-111">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]を開きます。</span><span class="sxs-lookup"><span data-stu-id="f51bc-111">Open [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="f51bc-112">**[ファイル]** メニューの **[新規作成]** をポイントし、 **[プロジェクト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f51bc-112">On the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
3.  <span data-ttu-id="f51bc-113">**[インストールされているテンプレート]** ペインの **[Analysis Services 多次元およびデータ マイニング プロジェクト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f51bc-113">Select **Analysis Services Multidimensional and Data Mining Project** from the **Installed Templates** pane.</span></span>  
  
4.  <span data-ttu-id="f51bc-114">**[名前]** ボックスに、新しいプロジェクトの名前「 **DM Intermediate**」を入力します。</span><span class="sxs-lookup"><span data-stu-id="f51bc-114">In the **Name** box, name the new project **DM Intermediate**.</span></span>  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
### <a name="to-change-the-instance-where-data-mining-objects-are-stored-optional"></a><span data-ttu-id="f51bc-115">データ マイニング オブジェクトを格納するインスタンスを変更するには (オプション)</span><span class="sxs-lookup"><span data-stu-id="f51bc-115">To change the instance where data mining objects are stored (optional)</span></span>  
  
1.  <span data-ttu-id="f51bc-116">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で、 **[プロジェクト]** メニューの **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f51bc-116">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], on the **Project** menu, click **Properties**.</span></span>  
  
2.  <span data-ttu-id="f51bc-117">**[プロパティ ページ]** ペインの左側で、 **[配置]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f51bc-117">In the left side of the **Property Pages** pane, click **Deployment**.</span></span>  
  
3.  <span data-ttu-id="f51bc-118">サーバー名 \*\*\*\* が **localhost**であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="f51bc-118">Verify that the **Server** name is **localhost**.</span></span> <span data-ttu-id="f51bc-119">別のインスタンスを使用する場合は、インスタンスの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="f51bc-119">If you are using a different instance, type the name of the instance.</span></span> <span data-ttu-id="f51bc-120">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]の名前付きインスタンスを使用する場合は、コンピューター名とインスタンス名を入力します。</span><span class="sxs-lookup"><span data-stu-id="f51bc-120">If you are using a named instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], type the machine name and then the instance name.</span></span> [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
### <a name="to-change-the-deployment-properties-for-a-project-optional"></a><span data-ttu-id="f51bc-121">プロジェクトの配置プロパティを変更するには (オプション)</span><span class="sxs-lookup"><span data-stu-id="f51bc-121">To change the deployment properties for a project (optional)</span></span>  
  
1.  <span data-ttu-id="f51bc-122">ソリューション エクスプローラーで、プロジェクトを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f51bc-122">In Solution Explorer, right-click the project, and then select **Properties**.</span></span>  
  
     <span data-ttu-id="f51bc-123">-- または --</span><span class="sxs-lookup"><span data-stu-id="f51bc-123">-- or --</span></span>  
  
     <span data-ttu-id="f51bc-124">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で、 **[プロジェクト]** メニューの **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f51bc-124">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], on the **Project** menu, select **Properties**.</span></span>  
  
2.  <span data-ttu-id="f51bc-125">**[プロパティ ページ]** ペインの左側で、 **[配置]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f51bc-125">In the left side of the **Property Pages** pane, click **Deployment**.</span></span>  
  
     <span data-ttu-id="f51bc-126">**[オプション]** ペインで **[配置モード]** をクリックし、上書きする場合はオプションを **[すべて配置]** に設定し、オブジェクトを更新するかオブジェクトを追加する場合は **[変更のみを配置]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="f51bc-126">In the **Options** pane, select **Deployment Mode**, and set the options to **Deploy All** to overwrite, or to **Deploy Changes Only** to update objects or add objects.</span></span>  
  
## <a name="creating-a-data-source"></a><span data-ttu-id="f51bc-127">データ ソースの作成</span><span class="sxs-lookup"><span data-stu-id="f51bc-127">Creating a Data Source</span></span>  
 <span data-ttu-id="f51bc-128">「基本的なデータ マイニング チュートリアル」では、 *データベースの接続情報を格納する* データ ソース [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] を作成しました。</span><span class="sxs-lookup"><span data-stu-id="f51bc-128">In the Basic Data Mining Tutorial, you created a *data source* that stores connection information for the [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] database.</span></span> <span data-ttu-id="f51bc-129">このソリューションでは、同じ手順で [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] データ ソースを作成します。</span><span class="sxs-lookup"><span data-stu-id="f51bc-129">Follow the same steps to create the [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] data source in this solution.</span></span>  
  
#### <a name="to-create-a-data-source"></a><span data-ttu-id="f51bc-130">データ ソースを作成するには</span><span class="sxs-lookup"><span data-stu-id="f51bc-130">To create a data source</span></span>  
  
-   [<span data-ttu-id="f51bc-131">データソースの作成 &#40;基本的なデータマイニングチュートリアル&#41;</span><span class="sxs-lookup"><span data-stu-id="f51bc-131">Creating a Data Source &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/creating-a-data-source-basic-data-mining-tutorial.md)  
  
 <span data-ttu-id="f51bc-132">1 つのデータ ソースで複数のデータ ソース ビューをサポートできます。また、各データ ソース ビューには複数のテーブルを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="f51bc-132">A single data source can support multiple data source views, and each data source view can have multiple tables.</span></span> <span data-ttu-id="f51bc-133">ただし、データソースとデータソースビューは、作成するデータマイニングモデルと共にデータベースに配置されるため、 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ベストプラクティスとして、各データソースビューにはデータマイニングモデルまたはモデルのグループごとに必要なテーブルのみを含めることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="f51bc-133">However, because the data source and data source view are deployed to your [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database together with the data mining models that you create, as a best practice you should include in each data source view only those tables that are required for each data mining model or group of models.</span></span>  
  
 <span data-ttu-id="f51bc-134">以降のレッスンでは、それぞれの新しいシナリオをサポートするデータ ソース ビューを追加します。</span><span class="sxs-lookup"><span data-stu-id="f51bc-134">In the following lessons, you will add data source views to support each of the new scenarios.</span></span> <span data-ttu-id="f51bc-135">マーケット バスケットのレッスンとシーケンス クラスターのレッスンのみ、同じデータ ソース ビューを使用します。それ以外は、各シナリオは異なるデータ ソース ビューを使用するため、各レッスンは互いに無関係であり、別々に実行できます。</span><span class="sxs-lookup"><span data-stu-id="f51bc-135">Only the market basket and sequence clustering lessons use the same data source view; otherwise, each scenario uses a different data source view, so the lessons are independent of each other and can be completed separately.</span></span>  
  
|<span data-ttu-id="f51bc-136">シナリオ</span><span class="sxs-lookup"><span data-stu-id="f51bc-136">Scenario</span></span>|<span data-ttu-id="f51bc-137">データ ソース ビューに含まれているデータ</span><span class="sxs-lookup"><span data-stu-id="f51bc-137">Data included in the data source view</span></span>|  
|--------------|-------------------------------------------|  
|[<span data-ttu-id="f51bc-138">レッスン 2: 予測シナリオの構築中級者向けデータマイニングチュートリアル &#40;&#41;</span><span class="sxs-lookup"><span data-stu-id="f51bc-138">Lesson 2: Building a Forecasting Scenario &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)|<span data-ttu-id="f51bc-139">単一のビューとして収集された、各地域での各自転車モデルの月間の売上レポート。</span><span class="sxs-lookup"><span data-stu-id="f51bc-139">Monthly sales reports for bicycle models in different regions, collected as a single view.</span></span>|  
|[<span data-ttu-id="f51bc-140">レッスン 3: マーケット バスケット シナリオの作成 (中級者向けデータ マイニング チュートリアル)</span><span class="sxs-lookup"><span data-stu-id="f51bc-140">Lesson 3: Building a Market Basket Scenario &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md)|<span data-ttu-id="f51bc-141">顧客注文の一覧を含むテーブルと、各顧客の購入記録を示す入れ子になったテーブル。</span><span class="sxs-lookup"><span data-stu-id="f51bc-141">A table containing a list of customer orders, and a nested table showing the individual purchases for each customer.</span></span>|  
|[<span data-ttu-id="f51bc-142">レッスン 4: シーケンスクラスターシナリオの構築中級者向けデータマイニングチュートリアル &#40;&#41;</span><span class="sxs-lookup"><span data-stu-id="f51bc-142">Lesson 4: Building a Sequence Clustering Scenario &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-4-build-sequence-clustering-scenario-intermediate-data-mining.md)|<span data-ttu-id="f51bc-143">マーケット バスケット分析に使用したものと同じデータに、品目の購入順序を示す識別子が追加されています。</span><span class="sxs-lookup"><span data-stu-id="f51bc-143">The same data that is used for the market basket analysis, with the addition of an identifier that shows the order in which items were purchased.</span></span>|  
|[<span data-ttu-id="f51bc-144">レッスン 5: ニューラル ネットワークおよびロジスティック回帰モデルの作成 &#40;中級者向けデータ マイニング チュートリアル&#41;</span><span class="sxs-lookup"><span data-stu-id="f51bc-144">Lesson 5: Building Neural Network and Logistic Regression Models &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md)|<span data-ttu-id="f51bc-145">コール センターのいくつかの事前パフォーマンス追跡データを含む単一のテーブル。</span><span class="sxs-lookup"><span data-stu-id="f51bc-145">A single table containing some preliminary performance tracking data from a call center.</span></span>|  
  
## <a name="next-lesson"></a><span data-ttu-id="f51bc-146">次のレッスン</span><span class="sxs-lookup"><span data-stu-id="f51bc-146">Next Lesson</span></span>  
 [<span data-ttu-id="f51bc-147">レッスン 2: 予測シナリオの構築中級者向けデータマイニングチュートリアル &#40;&#41;</span><span class="sxs-lookup"><span data-stu-id="f51bc-147">Lesson 2: Building a Forecasting Scenario &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="f51bc-148">参照</span><span class="sxs-lookup"><span data-stu-id="f51bc-148">See Also</span></span>  
 <span data-ttu-id="f51bc-149">[データマイニングプロジェクト](../../2014/analysis-services/data-mining/data-mining-projects.md) </span><span class="sxs-lookup"><span data-stu-id="f51bc-149">[Data Mining Projects](../../2014/analysis-services/data-mining/data-mining-projects.md) </span></span>  
 [<span data-ttu-id="f51bc-150">多次元モデル内のデータ ソース ビュー</span><span class="sxs-lookup"><span data-stu-id="f51bc-150">Data Source Views in Multidimensional Models</span></span>](https://docs.microsoft.com/analysis-services/multidimensional-models/data-source-views-in-multidimensional-models)  
  
  
