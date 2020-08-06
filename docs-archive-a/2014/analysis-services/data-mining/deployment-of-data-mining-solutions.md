---
title: データマイニングソリューションの配置 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models [Analysis Services], deploying
- deploying [Analysis Services], production environments
- deploying [Analysis Services - data mining]
- solutions [Analysis Services], deploying
- models [Analysis Services], data mining
ms.assetid: d83effc7-437d-42e9-8ac3-b65f79e27043
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5764be2f7530add2fa4cb028b288be69598bb95c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644227"
---
# <a name="deployment-of-data-mining-solutions"></a><span data-ttu-id="b97a2-102">データ マイニング ソリューションの配置</span><span class="sxs-lookup"><span data-stu-id="b97a2-102">Deployment of Data Mining Solutions</span></span>
  <span data-ttu-id="b97a2-103">データ マイニング プロセスの最後の手順は、実稼働環境へのモデルの配置です。</span><span class="sxs-lookup"><span data-stu-id="b97a2-103">The last step in the data mining process is to deploy the models to a production environment.</span></span> <span data-ttu-id="b97a2-104">配置は、モデルをユーザーが使用できるようにし、次のようなタスクを実行できるようになるという点で重要です。</span><span class="sxs-lookup"><span data-stu-id="b97a2-104">Deployment is important because it makes the models available to users so that you can perform any of the following tasks:</span></span>  
  
-   <span data-ttu-id="b97a2-105">モデルを使用して予測を作成し、業務上の意思決定を行います。</span><span class="sxs-lookup"><span data-stu-id="b97a2-105">Use the models to create predictions and make business decisions.</span></span> <span data-ttu-id="b97a2-106">クエリの作成に使用できるツールの詳細については、「[データマイニングクエリインターフェイス](data-mining-query-tools.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b97a2-106">For information about the tools you can use to create queries, see [Data Mining Query Interfaces](data-mining-query-tools.md).</span></span>  
  
-   <span data-ttu-id="b97a2-107">データ マイニング機能をアプリケーションに直接埋め込みます。</span><span class="sxs-lookup"><span data-stu-id="b97a2-107">Embed data mining functionality directly into an application.</span></span> <span data-ttu-id="b97a2-108">マイニング構造とマイニング モデルを作成、変更、処理、および削除するためにアプリケーションで使用できる一連のオブジェクトを含んでいる分析管理オブジェクト (AMO) またはアセンブリを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="b97a2-108">You can include Analysis Management Objects (AMO) or an assembly that contains a set of objects that your application can use to create, alter, process, and delete mining structures and mining models.</span></span>  
  
-   <span data-ttu-id="b97a2-109">ユーザーが予測の要求、傾向の表示、またはモデルの比較を行うことができるレポートを作成します。</span><span class="sxs-lookup"><span data-stu-id="b97a2-109">Create reports that let users request predictions, view trends, or compare models.</span></span>  
  
 <span data-ttu-id="b97a2-110">ここでは、配置オプションについて詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="b97a2-110">This section provides detailed information about deployment options.</span></span>  
  
 [<span data-ttu-id="b97a2-111">データマイニングソリューションを配置するための要件</span><span class="sxs-lookup"><span data-stu-id="b97a2-111">Requirements for Deployment of Data Mining Solutions</span></span>](#bkmk_Reqs)  
  
 [<span data-ttu-id="b97a2-112">リレーショナル ソリューションの配置</span><span class="sxs-lookup"><span data-stu-id="b97a2-112">Deploying a Relational Solution</span></span>](#bkmk_RelationalSltn)  
  
 [<span data-ttu-id="b97a2-113">多次元ソリューションの配置</span><span class="sxs-lookup"><span data-stu-id="b97a2-113">Deploying a Multidimensional Solution</span></span>](#bkmk_MDSltn)  
  
 [<span data-ttu-id="b97a2-114">関連リソース</span><span class="sxs-lookup"><span data-stu-id="b97a2-114">Related Resources</span></span>](#bkmk_Resources)  
  
## <a name="in-this-section"></a><span data-ttu-id="b97a2-115">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="b97a2-115">In This Section</span></span>  
 [<span data-ttu-id="b97a2-116">SQL Server の以前のバージョンへのデータ マイニング ソリューションの配置</span><span class="sxs-lookup"><span data-stu-id="b97a2-116">Deploy a Data Mining Solution to Previous Versions of SQL Server</span></span>](deploy-a-data-mining-solution-to-previous-versions-of-sql-server.md)  
  
 [<span data-ttu-id="b97a2-117">データ マイニング オブジェクトのエクスポートおよびインポート</span><span class="sxs-lookup"><span data-stu-id="b97a2-117">Export and Import Data Mining Objects</span></span>](export-and-import-data-mining-objects.md)  
  
##  <a name="requirements-for-deployment-of-data-mining-solutions"></a><a name="bkmk_Reqs"></a> <span data-ttu-id="b97a2-118">データ マイニング ソリューションの配置の要件</span><span class="sxs-lookup"><span data-stu-id="b97a2-118">Requirements for Deployment of Data Mining Solutions</span></span>  
 <span data-ttu-id="b97a2-119">ソリューションの配置先となる [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンスは、多次元オブジェクトとデータ マイニング オブジェクトをサポートするモードで実行されている必要があります。つまり、テーブル モデルや PowerPivot データをホストするインスタンスにデータ マイニング オブジェクトを配置することはできません。</span><span class="sxs-lookup"><span data-stu-id="b97a2-119">The instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] to which you deploy the solution must be running in a mode that supports multidimensional objects and data mining objects; that is, you cannot deploy data mining objects to an instance that hosts tabular models or PowerPivot data.</span></span>  
  
 <span data-ttu-id="b97a2-120">したがって、Visual Studio でデータ マイニング ソリューションを作成するときは、 **[Analysis Services 多次元およびデータ マイニング プロジェクト]** テンプレートを必ず使用してください。</span><span class="sxs-lookup"><span data-stu-id="b97a2-120">Therefore, when you create a data mining solution in Visual Studio, be sure to use the template, **Analysis Services Multidimensional and Data Mining Project**.</span></span>  
  
 <span data-ttu-id="b97a2-121">ソリューションを配置すると、データ マイニングに使用されるオブジェクトが、指定された [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスに作成されます。作成先は、ソリューション ファイルと同じ名前のデータベースになります。</span><span class="sxs-lookup"><span data-stu-id="b97a2-121">When you deploy the solution, the objects used for data mining are created in the specified [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance, in a database with the same name as the solution file.</span></span>  
  
###  <a name="deploying-a-relational-solution"></a><a name="bkmk_RelationalSltn"></a><span data-ttu-id="b97a2-122">リレーショナルソリューションの配置</span><span class="sxs-lookup"><span data-stu-id="b97a2-122">Deploying a Relational Solution</span></span>  
 <span data-ttu-id="b97a2-123">リレーショナル データ マイニング ソリューションを配置すると、必要なデータ マイニング オブジェクトが新しい [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベース内に作成され、それらのオブジェクトは既定の設定で処理されます。</span><span class="sxs-lookup"><span data-stu-id="b97a2-123">When you deploy a relational data mining solution, the required data mining objects are created within a new [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database, and the objects are processed by default.</span></span> <span data-ttu-id="b97a2-124">処理オプションは、構成プロパティの **[処理オプション]** を使用して変更できます。</span><span class="sxs-lookup"><span data-stu-id="b97a2-124">You can change processing options by using the configuration property, **Processing Option**.</span></span> <span data-ttu-id="b97a2-125">詳細については、「 [Analysis Services プロジェクトのプロパティの構成 &#40;SSDT&#41;](../multidimensional-models/configure-analysis-services-project-properties-ssdt.md)のインスタンスに定義済みオブジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="b97a2-125">For more information, see [Configure Analysis Services Project Properties &#40;SSDT&#41;](../multidimensional-models/configure-analysis-services-project-properties-ssdt.md).</span></span>  
  
 <span data-ttu-id="b97a2-126">既定では、増分変更だけが毎回配置されます。</span><span class="sxs-lookup"><span data-stu-id="b97a2-126">By default, only incremental changes are deployed each time.</span></span> <span data-ttu-id="b97a2-127">つまり、マイニング モデルを変更すると、プロジェクトを再配置するときに、そのマイニング モデルだけが更新されます。</span><span class="sxs-lookup"><span data-stu-id="b97a2-127">In other words, you can modify a mining model, and when you re-deploy the project, only that mining model would be updated.</span></span> <span data-ttu-id="b97a2-128">ただし、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースを複数のクライアントが編集する場合は、このためにエラーが発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="b97a2-128">However, if you have multiple clients editing the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database, this can lead to errors.</span></span> <span data-ttu-id="b97a2-129">既定の配置モードを変更して、ソリューションが配置されるときにデータベース全体が更新されるようにするには、 **[配置モード]** プロパティを変更します。</span><span class="sxs-lookup"><span data-stu-id="b97a2-129">To change the default deployment mode so that the entire database is refreshed when you deploy the solution, change the **Deployment Mode** property</span></span>  
  
 <span data-ttu-id="b97a2-130">リレーショナル データ マイニング ソリューションでは、配置しなければならないオブジェクトは、データ ソース定義、使用されたすべてのデータ ソース ビュー、マイニング構造、およびすべての依存マイニング モデルだけです。</span><span class="sxs-lookup"><span data-stu-id="b97a2-130">In a relational data mining solution, the only objects that must be deployed are the data source definition, any data source views that were used, the mining structures, and all dependent mining models.</span></span>  
  
###  <a name="deploying-a-multidimensional-solution"></a><a name="bkmk_MDSltn"></a><span data-ttu-id="b97a2-131">多次元ソリューションの配置</span><span class="sxs-lookup"><span data-stu-id="b97a2-131">Deploying a Multidimensional Solution</span></span>  
 <span data-ttu-id="b97a2-132">多次元データ マイニング ソリューションを配置すると、このソリューションによってデータ マイニング オブジェクトがソース キューブと同じデータベース内に作成されます。</span><span class="sxs-lookup"><span data-stu-id="b97a2-132">When you deploy a multidimensional data mining solution, this solution creates your data mining objects within the same database as the source cube.</span></span>  
  
 <span data-ttu-id="b97a2-133">マイニング構造またはマイニング モデルを処理するときには、ソース キューブも処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b97a2-133">When you process the mining structure or mining model, you must process the source cube as well.</span></span> <span data-ttu-id="b97a2-134">このため、OLAP マイニング モデルを使用するソリューションの配置には、リレーショナル データ マイニング ソリューションよりも時間がかかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="b97a2-134">For this reason, deploying a solution that uses OLAP mining models can take longer than relational data mining solutions.</span></span>  
  
 <span data-ttu-id="b97a2-135">通常、データ マイニング オブジェクトも、キューブに使用するのと同じデータ ソースおよびデータ ソース ビューを使用します。</span><span class="sxs-lookup"><span data-stu-id="b97a2-135">Typically data mining objects also use the same data sources and data source views that are used for the cube.</span></span> <span data-ttu-id="b97a2-136">ただし、データ マイニングの対象となるデータ ソースとデータ ソース ビューを明示的に追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="b97a2-136">However, you can add data sources and data source views that are targeted specifically to data mining.</span></span> <span data-ttu-id="b97a2-137">たとえば、通常、キューブは見込み顧客についてのデータや、多次元オブジェクトで使用されない外部データを含んでいません。</span><span class="sxs-lookup"><span data-stu-id="b97a2-137">For example, typically a cube would not contain data about prospective clients, or external data not used in the multidimensional objects.</span></span>  
  
##  <a name="related-resources"></a><a name="bkmk_Resources"></a><span data-ttu-id="b97a2-138">関連リソース</span><span class="sxs-lookup"><span data-stu-id="b97a2-138">Related Resources</span></span>  
 [<span data-ttu-id="b97a2-139">データ マイニング オブジェクトの移動</span><span class="sxs-lookup"><span data-stu-id="b97a2-139">Moving Data Mining Objects</span></span>](moving-data-mining-objects.md)  
  
 <span data-ttu-id="b97a2-140">モデルがリレーショナル データのみに基づいている場合、モデルを移動するための最も簡単な方法は、DMX を使用してオブジェクトをエクスポートおよびインポートすることです。</span><span class="sxs-lookup"><span data-stu-id="b97a2-140">If your model is based on relational data only, exporting and importing objects using DMX is the easiest way to move models.</span></span>  
  
 [<span data-ttu-id="b97a2-141">Analysis Services データベースの移動</span><span class="sxs-lookup"><span data-stu-id="b97a2-141">Move an Analysis Services Database</span></span>](../multidimensional-models/move-an-analysis-services-database.md)  
  
 <span data-ttu-id="b97a2-142">モデルがデータ ソースとしてキューブを使用している場合、モデルおよびそれをサポートしているキューブ データを移動する方法の詳細については、このトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="b97a2-142">When models use a cube as a data source, refer to this topic for more information about how to move models and their supporting cube data.</span></span>  
  
 [<span data-ttu-id="b97a2-143">Analysis Services プロジェクトの配置 &#40;SSDT&#41;</span><span class="sxs-lookup"><span data-stu-id="b97a2-143">Deploy Analysis Services Projects &#40;SSDT&#41;</span></span>](../multidimensional-models/deploy-analysis-services-projects-ssdt.md)  
  
 <span data-ttu-id="b97a2-144">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトの配置についての一般的な情報を提供し、プロジェクト構成の一部として設定できるプロパティについて説明しています。</span><span class="sxs-lookup"><span data-stu-id="b97a2-144">Provides general information about deployment of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] projects, and describes the properties that you can set as part of the project configuration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b97a2-145">参照</span><span class="sxs-lookup"><span data-stu-id="b97a2-145">See Also</span></span>  
 <span data-ttu-id="b97a2-146">[多次元モデルオブジェクトの処理](../multidimensional-models/processing-a-multidimensional-model-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="b97a2-146">[Multidimensional Model Object Processing](../multidimensional-models/processing-a-multidimensional-model-analysis-services.md) </span></span>  
 <span data-ttu-id="b97a2-147">[データマイニングクエリインターフェイス](data-mining-query-tools.md) </span><span class="sxs-lookup"><span data-stu-id="b97a2-147">[Data Mining Query Interfaces](data-mining-query-tools.md) </span></span>  
 [<span data-ttu-id="b97a2-148">処理の要件および注意事項 &#40;データ マイニング&#41;</span><span class="sxs-lookup"><span data-stu-id="b97a2-148">Processing Requirements and Considerations &#40;Data Mining&#41;</span></span>](processing-requirements-and-considerations-data-mining.md)  
  
  
