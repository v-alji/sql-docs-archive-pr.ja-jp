---
title: データマイニングソリューションおよびオブジェクトの管理 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data mining [Analysis Services], managing
- managing mining models
ms.assetid: 06fc61dd-925c-4347-8677-7046ee5d2f6f
author: minewiskan
ms.author: owend
ms.openlocfilehash: ae3e672932dd320c6b369f23f03c1f056d30d4ba
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631357"
---
# <a name="management-of-data-mining-solutions-and-objects"></a><span data-ttu-id="b3284-102">データ マイニング ソリューションおよびオブジェクトの管理</span><span class="sxs-lookup"><span data-stu-id="b3284-102">Management of Data Mining Solutions and Objects</span></span>
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="b3284-103">には、既存のマイニング構造とマイニング モデルの管理に使用できるクライアント ツールがあります。</span><span class="sxs-lookup"><span data-stu-id="b3284-103">provides client tools that you can use to manage existing mining structures and mining models.</span></span> <span data-ttu-id="b3284-104">ここでは、それぞれの環境を使用して実行できる管理操作について説明します。</span><span class="sxs-lookup"><span data-stu-id="b3284-104">This section describes the management operations that you can perform using each environment.</span></span>  
  
 <span data-ttu-id="b3284-105">これらのツールに加え、AMO や [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースに接続する他のクライアント (たとえば [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] 2007 用データ マイニング アドイン) を使用することで、プログラムでデータ マイニング オブジェクトを管理できます。</span><span class="sxs-lookup"><span data-stu-id="b3284-105">In addition to these tools, you can manage data mining objects programmatically, by using AMO, or use other clients that connect to an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database, such as the Data Mining Add-ins for [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] 2007.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b3284-106">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="b3284-106">In this Section</span></span>  
 [<span data-ttu-id="b3284-107">データ マイニング オブジェクトの移動</span><span class="sxs-lookup"><span data-stu-id="b3284-107">Moving Data Mining Objects</span></span>](moving-data-mining-objects.md)  
  
 [<span data-ttu-id="b3284-108">処理の要件および注意事項 &#40;データ マイニング&#41;</span><span class="sxs-lookup"><span data-stu-id="b3284-108">Processing Requirements and Considerations &#40;Data Mining&#41;</span></span>](processing-requirements-and-considerations-data-mining.md)  
  
 [<span data-ttu-id="b3284-109">SQL Server Profiler を使用したデータ マイニングの監視 (Analysis Services - データ マイニング)</span><span class="sxs-lookup"><span data-stu-id="b3284-109">Using SQL Server Profiler to Monitor Data Mining &#40;Analysis Services - Data Mining&#41;</span></span>](using-sql-server-profiler-to-monitor-data-mining-analysis-services-data-mining.md)  
  
## <a name="location-of-data-mining-objects"></a><span data-ttu-id="b3284-110">データ マイニング オブジェクトの場所</span><span class="sxs-lookup"><span data-stu-id="b3284-110">Location of Data Mining Objects</span></span>  
 <span data-ttu-id="b3284-111">処理されたマイニング構造およびマイニング モデルは、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]のインスタンスに格納されます。</span><span class="sxs-lookup"><span data-stu-id="b3284-111">Mining structures and models that have been processed are stored in an instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="b3284-112">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]データマイニングオブジェクトの開発時にモードでデータベースへの接続を作成すると `Immediate` 、作成したオブジェクトは、作業中にサーバーにすぐに追加されます。</span><span class="sxs-lookup"><span data-stu-id="b3284-112">If you create a connection to an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database in `Immediate` mode when developing your data mining objects, any objects that you create are immediately added to the server as you work.</span></span> <span data-ttu-id="b3284-113">一方、 **の既定の動作である** オフライン [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]モードでデータ マイニング オブジェクトを設計した場合、作成したマイニング オブジェクトは、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]のインスタンスに配置されるまでは単なるメタデータ コンテナーです。</span><span class="sxs-lookup"><span data-stu-id="b3284-113">However, if you design data mining objects in **Offline** mode, which is the default when you work in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], the mining objects that you create are only metadata containers until you deploy them to an instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="b3284-114">そのため、オブジェクトに変更を加えた場合は、オブジェクトを [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] サーバーに再配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b3284-114">Therefore, any time that you make a change to an object, you must redeploy the object to the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] server.</span></span> <span data-ttu-id="b3284-115">データ マイニングのアーキテクチャの詳細については、「[物理アーキテクチャ (Analysis Services - データ マイニング)](physical-architecture-analysis-services-data-mining.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b3284-115">For more information about data mining architecture, see [Physical Architecture &#40;Analysis Services - Data Mining&#41;](physical-architecture-analysis-services-data-mining.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b3284-116">[!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] 2007 用データ マイニング アドインなどの一部のクライアントでは、インスタンスへの接続を使用する一方でマイニング構造およびマイニング モデルをセッション中のみサーバー上に格納する、セッション マイニング モデルおよびセッション マイニング構造を作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="b3284-116">Some clients, such as the Data Mining Add-ins for [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] 2007, also let you create session mining models and mining structures, which use a connection to an instance but store the mining structure and models on the server only for the duration of the session.</span></span> <span data-ttu-id="b3284-117">これらのモデルは、クライアントを使用して、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースに格納されている構造およびモデルの場合と同じ方法で管理できますが、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]のインスタンスとの接続を解除したときにオブジェクトは保持されません。</span><span class="sxs-lookup"><span data-stu-id="b3284-117">You can still manage these models through the client, the same as you would structures and models stored in an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database, but the objects are not persisted after you disconnect from the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
## <a name="managing-data-mining-objects-in-sql-server-data-tools"></a><span data-ttu-id="b3284-118">SQL Server データ ツールでのデータ マイニング オブジェクトの管理</span><span class="sxs-lookup"><span data-stu-id="b3284-118">Managing Data Mining Objects in SQL Server Data Tools</span></span>  
 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] <span data-ttu-id="b3284-119">には、データ マイニング オブジェクトの作成、参照、および編集を容易にする機能が用意されています。</span><span class="sxs-lookup"><span data-stu-id="b3284-119">offers features that make it easy to create, browse, and edit data mining objects.</span></span>  
  
 <span data-ttu-id="b3284-120">次のリンクでは、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]を使用してデータ マイニング オブジェクトを変更する方法について説明しています。</span><span class="sxs-lookup"><span data-stu-id="b3284-120">The following links provide information on how you can modify data mining objects by using [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]:</span></span>  
  
-   [<span data-ttu-id="b3284-121">マイニング構造に使用されるデータ ソース ビューの編集</span><span class="sxs-lookup"><span data-stu-id="b3284-121">Edit the Data Source View used for a Mining Structure</span></span>](edit-the-data-source-view-used-for-a-mining-structure.md)  
  
-   [<span data-ttu-id="b3284-122">マイニング構造のプロパティの変更</span><span class="sxs-lookup"><span data-stu-id="b3284-122">Change the Properties of a Mining Structure</span></span>](change-the-properties-of-a-mining-structure.md)  
  
-   [<span data-ttu-id="b3284-123">マイニング モデルのプロパティの変更</span><span class="sxs-lookup"><span data-stu-id="b3284-123">Change the Properties of a Mining Model</span></span>](change-the-properties-of-a-mining-model.md)  
  
-   [<span data-ttu-id="b3284-124">モデリング フラグの表示または変更 &#40;データ マイニング&#41;</span><span class="sxs-lookup"><span data-stu-id="b3284-124">View or Change Modeling Flags &#40;Data Mining&#41;</span></span>](modeling-flags-data-mining.md)  
  
-   [<span data-ttu-id="b3284-125">アルゴリズム パラメーターの表示または変更</span><span class="sxs-lookup"><span data-stu-id="b3284-125">View or Change Algorithm Parameters</span></span>](view-or-change-algorithm-parameters.md)  
  
 <span data-ttu-id="b3284-126">通常は、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] をツールとして使用して、新しいプロジェクトの開発と既存のプロジェクトへの追加を行い、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]などのツールを使用して配置されたプロジェクトとオブジェクトを管理します。</span><span class="sxs-lookup"><span data-stu-id="b3284-126">Typically you will use [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] as a tool for developing new projects and adding to existing projects, and then manage projects and objects that have been deployed by using tools such as [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="b3284-127">ただし、`Immediate` オプションを使用し、オンライン モードでサーバーに接続することで、ssASnoversion のインスタンスに既に配置されているオブジェクトを直接変更できます。</span><span class="sxs-lookup"><span data-stu-id="b3284-127">However, you can directly modify objects that are already deployed to an instance of ssASnoversion by using the `Immediate` option and connecting to the server in Online mode.</span></span> <span data-ttu-id="b3284-128">詳細については、「 [Analysis Services データベースへのオンライン モードでの接続](../multidimensional-models/connect-in-online-mode-to-an-analysis-services-database.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b3284-128">For more information, see [Connect in Online Mode to an Analysis Services Database](../multidimensional-models/connect-in-online-mode-to-an-analysis-services-database.md).</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="b3284-129">名前や説明などのメタデータの変更を含め、マイニング構造またはマイニング モデルに対して変更を加えた場合は、構造またはモデルを再処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b3284-129">All changes to a mining structure or mining model, including changes to metadata such as a name or description, require that the structure or model be reprocessed.</span></span>  
  
 <span data-ttu-id="b3284-130">データ マイニング プロジェクトまたはオブジェクトの作成に使用したソリューション ファイルがない場合は、Analysis Services のインポート ウィザードを使用してサーバーから既存のプロジェクトをインポートし、オブジェクトに変更を加え、`Incremental` オプションを使用して再配置できます。</span><span class="sxs-lookup"><span data-stu-id="b3284-130">If you do not have the solution file that was used to create the data mining project or objects, you can import the existing project from the server using the Analysis Services Import wizard, make modifications to the objects, and then redeploy using the `Incremental` option.</span></span> <span data-ttu-id="b3284-131">詳細については、「 [Analysis Services インポート ウィザードを使用したデータ マイニング プロジェクトのインポート](import-a-data-mining-project-using-the-analysis-services-import-wizard.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b3284-131">For more information, see [Import a Data Mining Project using the Analysis Services Import Wizard](import-a-data-mining-project-using-the-analysis-services-import-wizard.md).</span></span>  
  
## <a name="managing-data-mining-objects-in-sql-server-management-studio"></a><span data-ttu-id="b3284-132">SQL Server Management Studio でのデータ マイニング オブジェクトの管理</span><span class="sxs-lookup"><span data-stu-id="b3284-132">Managing Data Mining Objects in SQL Server Management Studio</span></span>  
 <span data-ttu-id="b3284-133">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]では、マイニング構造とマイニング モデルのスクリプト処理、処理、または削除を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="b3284-133">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], you can script, process, or delete mining structures and mining models.</span></span> <span data-ttu-id="b3284-134">オブジェクト エクスプローラーを使用した場合はプロパティ セットの一部のみが表示されます。ただし、 **[DMX クエリ]** ウィンドウを開き、マイニング構造を選択すると、マイニング モデルに関する追加のメタデータを表示できます。</span><span class="sxs-lookup"><span data-stu-id="b3284-134">You can view only a limited set of properties by using Object Explorer; however, you can view additional metadata about mining models by opening a **DMX Query** window and selecting a mining structure.</span></span>  
  
-   [<span data-ttu-id="b3284-135">SQL Server Management Studio で DMX クエリを作成する</span><span class="sxs-lookup"><span data-stu-id="b3284-135">Create a DMX Query in SQL Server Management Studio</span></span>](create-a-dmx-query-in-sql-server-management-studio.md)  
  
## <a name="managing-data-mining-objects-programmatically"></a><span data-ttu-id="b3284-136">データ マイニング オブジェクトのプログラムによる管理</span><span class="sxs-lookup"><span data-stu-id="b3284-136">Managing Data Mining Objects Programmatically</span></span>  
 <span data-ttu-id="b3284-137">次のプログラミング言語を使用すると、データ マイニング オブジェクトの作成、変更、処理、および削除の操作を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="b3284-137">You can create, alter, process, and delete data mining objects by using the following programming languages.</span></span> <span data-ttu-id="b3284-138">各言語は別々のタスクを対象として設計されています。結果として、実行できる操作の種類に制限があります。</span><span class="sxs-lookup"><span data-stu-id="b3284-138">Each language is designed for different tasks and as a result, there might be restrictions on the type of operations that you can perform.</span></span> <span data-ttu-id="b3284-139">たとえば、データ マイニング オブジェクトの一部のプロパティはデータ マイニング拡張機能 (DMX) では変更できず、XMLA または AMO を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b3284-139">For example, some properties of data mining objects cannot be changed by using Data Mining Extensions (DMX); you must use XMLA or AMO.</span></span>  
  
### <a name="analysis-management-objects-amo"></a><span data-ttu-id="b3284-140">分析管理オブジェクト (AMO)</span><span class="sxs-lookup"><span data-stu-id="b3284-140">Analysis Management Objects (AMO)</span></span>  
 <span data-ttu-id="b3284-141">分析管理オブジェクト (AMO) は、データ マイニング オブジェクトを完全に制御できる、XMLA に基づいて構築されたオブジェクト モデルです。</span><span class="sxs-lookup"><span data-stu-id="b3284-141">Analysis Management Objects (AMO) is an object model built on top of XMLA that gives you full control over data mining objects.</span></span> <span data-ttu-id="b3284-142">AMO を使用して、マイニング構造とマイニング モデルを作成、配置、および監視できます。</span><span class="sxs-lookup"><span data-stu-id="b3284-142">By using AMO, you can create, deploy, and monitor mining structures and mining models</span></span>  
  
-   [<span data-ttu-id="b3284-143">AMO の概念とオブジェクトモデル</span><span class="sxs-lookup"><span data-stu-id="b3284-143">AMO Concepts and Object Model</span></span>](https://docs.microsoft.com/bi-reference/amo/amo-concepts-and-object-model)  
  
-   <xref:Microsoft.AnalysisServices>  
  
 <span data-ttu-id="b3284-144">**制限事項:** なし。</span><span class="sxs-lookup"><span data-stu-id="b3284-144">**Restrictions:** None.</span></span>  
  
### <a name="data-mining-extensions-dmx"></a><span data-ttu-id="b3284-145">データ マイニング拡張機能 (DMX)</span><span class="sxs-lookup"><span data-stu-id="b3284-145">Data Mining Extensions (DMX)</span></span>  
 <span data-ttu-id="b3284-146">データ マイニング拡張機能 (DMX) は、 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] や ADOMD.Net などの他のコマンド インターフェイスと組み合わせて、マイニング構造とマイニング モデルを作成、削除、およびクエリできます。</span><span class="sxs-lookup"><span data-stu-id="b3284-146">Data Mining Extensions (DMX) can be used with other command interfaces such as [!INCLUDE[vstecado](../../includes/vstecado-md.md)] or ADOMD.Net to create, delete, and query mining structures and mining models.</span></span>  
  
-   [<span data-ttu-id="b3284-147">データ マイニング拡張機能 (DMX) データ定義ステートメント</span><span class="sxs-lookup"><span data-stu-id="b3284-147">Data Mining Extensions &#40;DMX&#41; Data Definition Statements</span></span>](/sql/dmx/dmx-statements-data-definition)  
  
 <span data-ttu-id="b3284-148">**制限事項:** DMX を使用した場合、一部のプロパティを変更できません。</span><span class="sxs-lookup"><span data-stu-id="b3284-148">**Restrictions:** Some properties cannot be changed by using DMX.</span></span>  
  
### <a name="xml-for-analysis-xmla"></a><span data-ttu-id="b3284-149">XML for Analysis (XMLA)</span><span class="sxs-lookup"><span data-stu-id="b3284-149">XML for Analysis (XMLA)</span></span>  
 <span data-ttu-id="b3284-150">XML for Analysis (XMLA) は、すべての Analysis Services 用のデータ定義言語です。</span><span class="sxs-lookup"><span data-stu-id="b3284-150">XML for Analysis (XMLA) is the data definition language for all of Analysis Services.</span></span> <span data-ttu-id="b3284-151">XMLA を使用して、ほとんどのデータ マイニング オブジェクトとサーバーの動作を制御できます。</span><span class="sxs-lookup"><span data-stu-id="b3284-151">XMLA gives you control over most data mining objects and server operations.</span></span> <span data-ttu-id="b3284-152">XMLA を使用すると、クライアントとサーバーの間で行うすべての管理操作を実行できます。</span><span class="sxs-lookup"><span data-stu-id="b3284-152">All management operations between the client and the server can be performed by using XMLA.</span></span> <span data-ttu-id="b3284-153">便宜上、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] スクリプト言語 (ASSL) を使用して XML をラップできます。</span><span class="sxs-lookup"><span data-stu-id="b3284-153">For convenience, you can use the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Scripting Language (ASSL) to wrap the XML.</span></span>  
  
 <span data-ttu-id="b3284-154">**制限事項:** [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] は、内部使用の目的でのみサポートされ XMLA DDL スクリプト内では使用できない XML ステートメントを生成する場合があります。</span><span class="sxs-lookup"><span data-stu-id="b3284-154">**Restrictions:** [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] generates some XMLA statements that are supported for internal use only, and cannot be used in XML DDL scripts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3284-155">参照</span><span class="sxs-lookup"><span data-stu-id="b3284-155">See Also</span></span>  
 [<span data-ttu-id="b3284-156">開発者ガイド &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="b3284-156">Developer's Guide &#40;Analysis Services&#41;</span></span>](../analysis-services-developer-documentation.md)  
  
  
