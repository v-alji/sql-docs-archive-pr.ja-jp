---
title: データマイニングソリューション |Microsoft Docs
ms.custom: ''
ms.date: 07/17/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data mining [Analysis Services], about data mining
- data mining [Analysis Services], development
ms.assetid: 84f6548d-ebb0-4e10-9b29-66253fa0a04a
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0ab4b5ddcc9958fa36d6c8ecae0e7fd79585b4fa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639806"
---
# <a name="data-mining-solutions"></a><span data-ttu-id="fa4da-102">データ マイニング ソリューション</span><span class="sxs-lookup"><span data-stu-id="fa4da-102">Data Mining Solutions</span></span>
  <span data-ttu-id="fa4da-103">データ マイニング ソリューションとは、データ マイニング プロジェクトを少なくとも 1 つ含んだ [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ソリューションです。</span><span class="sxs-lookup"><span data-stu-id="fa4da-103">A data mining solution is an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] solution that contains one or more data mining projects.</span></span>  
  
 <span data-ttu-id="fa4da-104">このセクションのトピックでは、を使用して、統合データマイニングソリューションを設計および実装する方法について説明し [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="fa4da-104">The topics in this section provide information about how to design and implement an integrated data mining solution by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="fa4da-105">データ マイニング デザイン プロセスおよび関連ツールの概要については、「 [データ マイニングの概念](data-mining-concepts.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fa4da-105">For an overview of the data mining design process and related tools, see [Data Mining Concepts](data-mining-concepts.md).</span></span>  
  
 <span data-ttu-id="fa4da-106">データ マイニングに利用できるその他のプロジェクト タイプの詳細については、「 [データ マイニング ソリューションの関連プロジェクト](data-mining-solutions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fa4da-106">For more information about additional projects types that are useful for data mining, see [Related Projects for Data Mining Solutions](data-mining-solutions.md).</span></span>  
  
 [<span data-ttu-id="fa4da-107">リレーショナル データ ソースと多次元ソリューションの比較</span><span class="sxs-lookup"><span data-stu-id="fa4da-107">Relational vs. Multidimensional Solutions</span></span>](#bkmk_RelMD)  
  
 [<span data-ttu-id="fa4da-108">データ マイニング ソリューションの配置</span><span class="sxs-lookup"><span data-stu-id="fa4da-108">Deploying Data Mining Solutions</span></span>](#bkmk_Deploy)  
  
 [<span data-ttu-id="fa4da-109">ソリューションのチュートリアル</span><span class="sxs-lookup"><span data-stu-id="fa4da-109">Solution Walkthroughs</span></span>](#bkmk_Walkthru)  
  
##  <a name="relational-vs-multidimensional-solutions"></a><a name="bkmk_RelMD"></a><span data-ttu-id="fa4da-110">リレーショナルソリューションと多次元ソリューションの比較</span><span class="sxs-lookup"><span data-stu-id="fa4da-110">Relational vs. Multidimensional Solutions</span></span>  
 <span data-ttu-id="fa4da-111">データマイニングソリューションは、多次元データ (既存のキューブ)、純粋なリレーショナルデータ (データウェアハウスのテーブルとビューなど)、またはテキストファイル、Excel ブック、またはその他の外部データソースに基づいて作成できます。</span><span class="sxs-lookup"><span data-stu-id="fa4da-111">A data mining solution can be based either on multidimensional data-that is, an existing cube-or on purely relational data, such as the tables and views in a data warehouse, or on text files, Excel workbooks, or other external data sources.</span></span>  
  
-   <span data-ttu-id="fa4da-112">既存の多次元データベース ソリューション内でデータ マイニング オブジェクトを作成できます。</span><span class="sxs-lookup"><span data-stu-id="fa4da-112">You can create data mining objects within an existing multidimensional database solution.</span></span>  
  
     <span data-ttu-id="fa4da-113">通常、このようなソリューションは、既に作成済みのキューブが存在し、そのキューブをデータ ソースとしてデータ マイニングを実行する場合に作成します。</span><span class="sxs-lookup"><span data-stu-id="fa4da-113">Typically you would create a solution like this if you have already created a cube and want to perform data mining by using the cube as a data source.</span></span> <span data-ttu-id="fa4da-114">キューブに基づくモデルを移動したりバックアップしたりする際は、キューブも移動またはコピーする必要があります。</span><span class="sxs-lookup"><span data-stu-id="fa4da-114">When you move and backup models based on a cube, the cube must also be moved or copied.</span></span>  
  
-   <span data-ttu-id="fa4da-115">データ マイニング オブジェクト (補助的なデータ ソースやデータ ソース ビューを含む) だけを含み、リレーショナル データ ソースのみを使用するデータ マイニング ソリューションを作成できます。</span><span class="sxs-lookup"><span data-stu-id="fa4da-115">You can create a data mining solution that contains only data mining objects, including the supporting data sources and data source views, and that uses relational data source only.</span></span>  
  
     <span data-ttu-id="fa4da-116">これはデータ マイニング モデルの作成に適した方法です。一般に、処理やクエリは、リレーショナル データ ソースがその対象である場合に最も高速になります。</span><span class="sxs-lookup"><span data-stu-id="fa4da-116">This is the preferred method for creating data mining models, as processing and querying is generally fastest against relational data sources.</span></span> <span data-ttu-id="fa4da-117">また、サーバー間でのモデルの移動とバックアップも、EXPORT コマンドや IMPORT コマンドを使用して簡単に実行できます。</span><span class="sxs-lookup"><span data-stu-id="fa4da-117">You can also easily move and backup models between servers by using the EXPORT and IMPORT commands.</span></span>  
  
##  <a name="deploying-data-mining-solutions"></a><a name="bkmk_Deploy"></a><span data-ttu-id="fa4da-118">データマイニングソリューションの配置</span><span class="sxs-lookup"><span data-stu-id="fa4da-118">Deploying Data Mining Solutions</span></span>  
 <span data-ttu-id="fa4da-119">ソリューションの配置先となる [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンスは、多次元オブジェクトとデータ マイニング オブジェクトをサポートするモードで実行されている必要があります。つまり、テーブル モデルや PowerPivot データをホストするインスタンスにデータ マイニング オブジェクトを配置することはできません。</span><span class="sxs-lookup"><span data-stu-id="fa4da-119">The instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] to which you deploy the solution must be running in a mode that supports multidimensional objects and data mining objects; that is, you cannot deploy data mining objects to an instance that hosts tabular models or PowerPivot data.</span></span>  
  
 <span data-ttu-id="fa4da-120">したがって、Visual Studio でデータ マイニング ソリューションを作成するときは、 **[Analysis Services 多次元およびデータ マイニング プロジェクト]** テンプレートを必ず使用してください。</span><span class="sxs-lookup"><span data-stu-id="fa4da-120">Therefore, when you create a data mining solution in Visual Studio, be sure to use the template, **Analysis Services Multidimensional and Data Mining Project**.</span></span>  
  
 <span data-ttu-id="fa4da-121">ソリューションを配置すると、データ マイニングに使用されるオブジェクトが、指定された [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスに作成されます。作成先は、ソリューション ファイルと同じ名前のデータベースになります。</span><span class="sxs-lookup"><span data-stu-id="fa4da-121">When you deploy the solution, the objects used for data mining are created in the specified [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance, in a database with the same name as the solution file.</span></span>  
  
 <span data-ttu-id="fa4da-122">リレーショナル ソリューションと多次元ソリューションの両方を配置する方法の詳細については、「 [データ マイニング ソリューションの配置](deployment-of-data-mining-solutions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fa4da-122">For more information about how to deploy both relational and multidimensional solutions, see [Deployment of Data Mining Solutions](deployment-of-data-mining-solutions.md).</span></span>  
  
##  <a name="solution-walkthrough"></a><a name="bkmk_Walkthru"></a><span data-ttu-id="fa4da-123">ソリューションのチュートリアル</span><span class="sxs-lookup"><span data-stu-id="fa4da-123">Solution Walkthrough</span></span>  
 <span data-ttu-id="fa4da-124">データ マイニング ウィザードを使用してデータ マイニング ソリューションを作成する方法の概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="fa4da-124">Provides an overview of how to create data mining solutions by using the Data Mining Wizard.</span></span>  
  
 [<span data-ttu-id="fa4da-125">Create a Relational Mining Structure</span><span class="sxs-lookup"><span data-stu-id="fa4da-125">Create a Relational Mining Structure</span></span>](create-a-relational-mining-structure.md)  
 <span data-ttu-id="fa4da-126">マイニング構造は、リレーショナル データやテキスト ファイルのほか、データ ソース ビューに組み込むことのできる各種のソースから作成できます。</span><span class="sxs-lookup"><span data-stu-id="fa4da-126">Create a mining structure from relational data, text files, and other sources that can be combined in a data source view.</span></span>  
  
 [<span data-ttu-id="fa4da-127">Create an OLAP Mining Structure</span><span class="sxs-lookup"><span data-stu-id="fa4da-127">Create an OLAP Mining Structure</span></span>](create-an-olap-mining-structure.md)  
 <span data-ttu-id="fa4da-128">OLAP キューブのデータを基にマイニング構造を作成します。</span><span class="sxs-lookup"><span data-stu-id="fa4da-128">Create a mining structure based on data in an OLAP cube.</span></span> <span data-ttu-id="fa4da-129">OLAP データから作成したモデルは、データ マイニング ディメンションとして保存できるほか、データ セットやモデルを新しいキューブとして保存することもできます。</span><span class="sxs-lookup"><span data-stu-id="fa4da-129">Models that you create from OLAP data can be saved as a data mining dimension, or you can save the set of data and your models as a new cube.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fa4da-130">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="fa4da-130">In This Section</span></span>  
 [<span data-ttu-id="fa4da-131">データ マイニング プロジェクト</span><span class="sxs-lookup"><span data-stu-id="fa4da-131">Data Mining Projects</span></span>](data-mining-projects.md)  
  
 [<span data-ttu-id="fa4da-132">データ マイニング オブジェクトの処理</span><span class="sxs-lookup"><span data-stu-id="fa4da-132">Processing Data Mining Objects</span></span>](processing-data-mining-objects.md)  
  
 [<span data-ttu-id="fa4da-133">データ マイニング ソリューションの関連プロジェクト</span><span class="sxs-lookup"><span data-stu-id="fa4da-133">Related Projects for Data Mining Solutions</span></span>](data-mining-solutions.md)  
  
 [<span data-ttu-id="fa4da-134">データ マイニング ソリューションの配置</span><span class="sxs-lookup"><span data-stu-id="fa4da-134">Deployment of Data Mining Solutions</span></span>](deployment-of-data-mining-solutions.md)  
  
## <a name="related-tasks-and-topics"></a><span data-ttu-id="fa4da-135">関連タスクおよびトピック</span><span class="sxs-lookup"><span data-stu-id="fa4da-135">Related Tasks and Topics</span></span>  
 <span data-ttu-id="fa4da-136">データ ソースとマイニング構造を含む基本的なデータ マイニング ソリューションを作成したら、そのソリューションを基礎として、新しいモデルの追加、モデルのテストや比較、予測の作成、データのサブセットに対する実験などを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="fa4da-136">After you have created a basic data mining solution, including data sources and a mining structure, you can build on the solution by adding new models, testing and comparing models, creating predictions, and experimenting with subsets of data.</span></span>  
  
 <span data-ttu-id="fa4da-137">詳細については、次のリンクを参照してください。</span><span class="sxs-lookup"><span data-stu-id="fa4da-137">For more information, see the following links:</span></span>  
  
|<span data-ttu-id="fa4da-138">タスク</span><span class="sxs-lookup"><span data-stu-id="fa4da-138">Tasks</span></span>|<span data-ttu-id="fa4da-139">トピック</span><span class="sxs-lookup"><span data-stu-id="fa4da-139">Topics</span></span>|  
|-----------|------------|  
|<span data-ttu-id="fa4da-140">作成するモデルのテスト、トレーニング データの質の検証、データ マイニング モデルの精度を表すグラフの作成</span><span class="sxs-lookup"><span data-stu-id="fa4da-140">Test the models you create, validate the quality of your training data, and create charts that represent the accuracy of data mining models.</span></span>|[<span data-ttu-id="fa4da-141">テストおよび検証 &#40;データ マイニング&#41;</span><span class="sxs-lookup"><span data-stu-id="fa4da-141">Testing and Validation &#40;Data Mining&#41;</span></span>](testing-and-validation-data-mining.md)|  
|<span data-ttu-id="fa4da-142">構造および関連モデルにデータを取り込むことによるモデルのトレーニング</span><span class="sxs-lookup"><span data-stu-id="fa4da-142">Train the model by populating the structure and related models with data.</span></span> <span data-ttu-id="fa4da-143">(新しいデータでのモデルの更新と拡張)</span><span class="sxs-lookup"><span data-stu-id="fa4da-143">Update and extend models with new data.</span></span>|[<span data-ttu-id="fa4da-144">データ マイニング オブジェクトの処理</span><span class="sxs-lookup"><span data-stu-id="fa4da-144">Processing Data Mining Objects</span></span>](processing-data-mining-objects.md)|  
|<span data-ttu-id="fa4da-145">マイニング モデルのカスタマイズ (トレーニング データへのフィルターの適用、異なるアルゴリズムの選択、高度なアルゴリズム パラメーターの設定)</span><span class="sxs-lookup"><span data-stu-id="fa4da-145">Customize a mining model by applying filters to the training data, choosing a different algorithm, or setting advanced algorithm parameters.</span></span>|[<span data-ttu-id="fa4da-146">マイニング モデルとマイニング構造のカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="fa4da-146">Customize Mining Models and Structure</span></span>](customize-mining-models-and-structure.md)|  
|<span data-ttu-id="fa4da-147">モデルのトレーニング用データにフィルターを適用することによるマイニング モデルのカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="fa4da-147">Customize a mining model by applying filters to the data used in training the mode.</span></span>|[<span data-ttu-id="fa4da-148">マイニング モデルを構造に追加する &#40;Analysis Services - データ マイニング&#41;</span><span class="sxs-lookup"><span data-stu-id="fa4da-148">Add Mining Models to a Structure &#40;Analysis Services - Data Mining&#41;</span></span>](add-mining-models-to-a-structure-analysis-services-data-mining.md)|  
|<span data-ttu-id="fa4da-149">データ マイニング ソリューションの更新と管理</span><span class="sxs-lookup"><span data-stu-id="fa4da-149">Update and manage data mining solutions.</span></span>|<span data-ttu-id="fa4da-150">Link TBD</span><span class="sxs-lookup"><span data-stu-id="fa4da-150">Link TBD</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fa4da-151">参照</span><span class="sxs-lookup"><span data-stu-id="fa4da-151">See Also</span></span>  
 [<span data-ttu-id="fa4da-152">データ マイニングのチュートリアル &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="fa4da-152">Data Mining Tutorials &#40;Analysis Services&#41;</span></span>](../data-mining-tutorials-analysis-services.md)  
  
  
