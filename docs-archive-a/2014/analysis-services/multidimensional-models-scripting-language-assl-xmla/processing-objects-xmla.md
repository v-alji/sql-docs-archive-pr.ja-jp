---
title: オブジェクトの処理 (XMLA) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- errors [XML for Analysis]
- objects [XML for Analysis]
- XML for Analysis, objects
- XMLA, partitions
- partitions [Analysis Services], XML for Analysis
- XML for Analysis, partitions
- writeback [Analysis Services], XML for Analysis
- out-of-line bindings
- processing objects [XML for Analysis]
- XMLA, objects
ms.assetid: a65b3249-303d-49c6-98af-6ac6eed11a03
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2e59c7953ae8fc7d3cfceafa7b0e9d8c7186daf8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738935"
---
# <a name="processing-objects-xmla"></a><span data-ttu-id="3e5e8-102">オブジェクトの処理 (XMLA)</span><span class="sxs-lookup"><span data-stu-id="3e5e8-102">Processing Objects (XMLA)</span></span>
  <span data-ttu-id="3e5e8-103">では [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 、ビジネス分析のためにデータを情報に変換するステップまたは一連の手順が処理されます。</span><span class="sxs-lookup"><span data-stu-id="3e5e8-103">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], processing is the step or series of steps that turn data into information for business analysis.</span></span> <span data-ttu-id="3e5e8-104">処理内容はオブジェクトの種類によって異なりますが、データを情報に変換する処理の一部として必ず実行されます。</span><span class="sxs-lookup"><span data-stu-id="3e5e8-104">Processing is different depending on the type of object, but processing is always part of turning data into information.</span></span>  
  
 <span data-ttu-id="3e5e8-105">オブジェクトを処理するには、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] [process](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/process-element-xmla)コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="3e5e8-105">To process an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] object, you can use the [Process](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/process-element-xmla) command.</span></span> <span data-ttu-id="3e5e8-106">`Process` コマンドでは、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスの以下のオブジェクトを処理できます。</span><span class="sxs-lookup"><span data-stu-id="3e5e8-106">The `Process` command can process the following objects on an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance:</span></span>  
  
-   <span data-ttu-id="3e5e8-107">キューブ</span><span class="sxs-lookup"><span data-stu-id="3e5e8-107">Cubes</span></span>  
  
-   <span data-ttu-id="3e5e8-108">データベース</span><span class="sxs-lookup"><span data-stu-id="3e5e8-108">Databases</span></span>  
  
-   <span data-ttu-id="3e5e8-109">Dimensions</span><span class="sxs-lookup"><span data-stu-id="3e5e8-109">Dimensions</span></span>  
  
-   <span data-ttu-id="3e5e8-110">メジャー グループ</span><span class="sxs-lookup"><span data-stu-id="3e5e8-110">Measure groups</span></span>  
  
-   <span data-ttu-id="3e5e8-111">[マイニング モデル]</span><span class="sxs-lookup"><span data-stu-id="3e5e8-111">Mining models</span></span>  
  
-   <span data-ttu-id="3e5e8-112">マイニング構造</span><span class="sxs-lookup"><span data-stu-id="3e5e8-112">Mining structures</span></span>  
  
-   <span data-ttu-id="3e5e8-113">メジャー グループ</span><span class="sxs-lookup"><span data-stu-id="3e5e8-113">Partitions</span></span>  
  
 <span data-ttu-id="3e5e8-114">`Process` コマンドには、オブジェクトの処理を制御するために設定できるさまざまなプロパティが用意されています。</span><span class="sxs-lookup"><span data-stu-id="3e5e8-114">To control the processing of objects, the `Process` command has various properties that can be set.</span></span> <span data-ttu-id="3e5e8-115">`Process` コマンドには、行う処理の程度、処理対象のオブジェクト、不一致バインドを使用するかどうか、エラー処理の方法、および書き戻しテーブルの管理方法を制御するプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="3e5e8-115">The `Process` command has properties that control: how much processing will be done, which objects will be processed, whether to use out-of-line bindings, how to handle errors, and how to manage writeback tables.</span></span>  
  
## <a name="specifying-processing-options"></a><span data-ttu-id="3e5e8-116">処理オプションの指定</span><span class="sxs-lookup"><span data-stu-id="3e5e8-116">Specifying Processing Options</span></span>  
 <span data-ttu-id="3e5e8-117">コマンドの[Type](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/type-element-xmla)プロパティは、 `Process` オブジェクトを処理するときに使用する処理オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="3e5e8-117">The [Type](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/type-element-xmla) property of the `Process` command specifies the processing option to use when processing the object.</span></span> <span data-ttu-id="3e5e8-118">処理オプションの詳細については、「[処理オプションと設定 &#40;Analysis Services&#41;](../multidimensional-models/processing-options-and-settings-analysis-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3e5e8-118">For more information about processing options, see [Processing Options and Settings &#40;Analysis Services&#41;](../multidimensional-models/processing-options-and-settings-analysis-services.md).</span></span>  
  
 <span data-ttu-id="3e5e8-119">次の表は、`Type` プロパティの定数と、各定数を使用して処理できるさまざまなオブジェクトの一覧を示しています。</span><span class="sxs-lookup"><span data-stu-id="3e5e8-119">The following table lists the constants for the `Type` property and the various objects that can be processed using each constant.</span></span>  
  
|<span data-ttu-id="3e5e8-120">`Type` の値</span><span class="sxs-lookup"><span data-stu-id="3e5e8-120">`Type` value</span></span>|<span data-ttu-id="3e5e8-121">適用されるオブジェクト</span><span class="sxs-lookup"><span data-stu-id="3e5e8-121">Applicable objects</span></span>|  
|--------------------|------------------------|  
|<span data-ttu-id="3e5e8-122">*ProcessFull*</span><span class="sxs-lookup"><span data-stu-id="3e5e8-122">*ProcessFull*</span></span>|<span data-ttu-id="3e5e8-123">キューブ、データベース、ディメンション、メジャー グループ、マイニング モデル、マイニング構造、パーティション</span><span class="sxs-lookup"><span data-stu-id="3e5e8-123">Cube, database, dimension, measure group, mining model, mining structure, partition</span></span>|  
|<span data-ttu-id="3e5e8-124">*ProcessAdd*</span><span class="sxs-lookup"><span data-stu-id="3e5e8-124">*ProcessAdd*</span></span>|<span data-ttu-id="3e5e8-125">ディメンション、パーティション</span><span class="sxs-lookup"><span data-stu-id="3e5e8-125">Dimension, partition</span></span>|  
|<span data-ttu-id="3e5e8-126">*ProcessUpdate*</span><span class="sxs-lookup"><span data-stu-id="3e5e8-126">*ProcessUpdate*</span></span>|<span data-ttu-id="3e5e8-127">Dimension</span><span class="sxs-lookup"><span data-stu-id="3e5e8-127">Dimension</span></span>|  
|<span data-ttu-id="3e5e8-128">*ProcessIndexes*</span><span class="sxs-lookup"><span data-stu-id="3e5e8-128">*ProcessIndexes*</span></span>|<span data-ttu-id="3e5e8-129">ディメンション、キューブ、メジャーグループ、パーティション</span><span class="sxs-lookup"><span data-stu-id="3e5e8-129">Dimension, cube, measure group, partition</span></span>|  
|<span data-ttu-id="3e5e8-130">*ProcessData*</span><span class="sxs-lookup"><span data-stu-id="3e5e8-130">*ProcessData*</span></span>|<span data-ttu-id="3e5e8-131">ディメンション、キューブ、メジャーグループ、パーティション</span><span class="sxs-lookup"><span data-stu-id="3e5e8-131">Dimension, cube, measure group, partition</span></span>|  
|<span data-ttu-id="3e5e8-132">*ProcessDefault*</span><span class="sxs-lookup"><span data-stu-id="3e5e8-132">*ProcessDefault*</span></span>|<span data-ttu-id="3e5e8-133">キューブ、データベース、ディメンション、メジャー グループ、マイニング モデル、マイニング構造、パーティション</span><span class="sxs-lookup"><span data-stu-id="3e5e8-133">Cube, database, dimension, measure group, mining model, mining structure, partition</span></span>|  
|<span data-ttu-id="3e5e8-134">*ProcessClear*</span><span class="sxs-lookup"><span data-stu-id="3e5e8-134">*ProcessClear*</span></span>|<span data-ttu-id="3e5e8-135">キューブ、データベース、ディメンション、メジャー グループ、マイニング モデル、マイニング構造、パーティション</span><span class="sxs-lookup"><span data-stu-id="3e5e8-135">Cube, database, dimension, measure group, mining model, mining structure, partition</span></span>|  
|<span data-ttu-id="3e5e8-136">*ProcessStructure*</span><span class="sxs-lookup"><span data-stu-id="3e5e8-136">*ProcessStructure*</span></span>|<span data-ttu-id="3e5e8-137">キューブ、マイニング構造</span><span class="sxs-lookup"><span data-stu-id="3e5e8-137">Cube, mining structure</span></span>|  
|<span data-ttu-id="3e5e8-138">*ProcessClearStructureOnly*</span><span class="sxs-lookup"><span data-stu-id="3e5e8-138">*ProcessClearStructureOnly*</span></span>|<span data-ttu-id="3e5e8-139">マイニング構造</span><span class="sxs-lookup"><span data-stu-id="3e5e8-139">Mining structure</span></span>|  
|<span data-ttu-id="3e5e8-140">*ProcessScriptCache*</span><span class="sxs-lookup"><span data-stu-id="3e5e8-140">*ProcessScriptCache*</span></span>|<span data-ttu-id="3e5e8-141">キューブ</span><span class="sxs-lookup"><span data-stu-id="3e5e8-141">Cube</span></span>|  
  
 <span data-ttu-id="3e5e8-142">オブジェクトの処理の詳細について [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は、「[多次元モデルオブジェクトの処理](../multidimensional-models/processing-a-multidimensional-model-analysis-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3e5e8-142">For more information about processing [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] objects, see [Multidimensional Model Object Processing](../multidimensional-models/processing-a-multidimensional-model-analysis-services.md).</span></span>  
  
## <a name="specifying-objects-to-be-processed"></a><span data-ttu-id="3e5e8-143">処理対象のオブジェクトの指定</span><span class="sxs-lookup"><span data-stu-id="3e5e8-143">Specifying Objects to be Processed</span></span>  
 <span data-ttu-id="3e5e8-144">コマンドの[object](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla)プロパティには、 `Process` 処理するオブジェクトのオブジェクト識別子が含まれています。</span><span class="sxs-lookup"><span data-stu-id="3e5e8-144">The [Object](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla) property of the `Process` command contains the object identifier of the object to be processed.</span></span> <span data-ttu-id="3e5e8-145">`Process` コマンドで指定できるオブジェクトは 1 つだけですが、1 つのオブジェクトを処理すると、その子オブジェクトも処理されます。</span><span class="sxs-lookup"><span data-stu-id="3e5e8-145">Only one object can be specified in a `Process` command, but processing an object also processes any child objects.</span></span> <span data-ttu-id="3e5e8-146">たとえば、キューブ内のメジャー グループを処理すると、そのメジャー グループのすべてのパーティションが処理されます。また、データベースを処理すると、キューブ、ディメンション、およびマイニング構造など、そのデータベースに含まれるすべてのオブジェクトが処理されます。</span><span class="sxs-lookup"><span data-stu-id="3e5e8-146">For example, processing a measure group in a cube processes all the partitions for that measure group, while processing a database processes all the objects, including cubes, dimensions, and mining structures, that are contained by the database.</span></span>  
  
 <span data-ttu-id="3e5e8-147">`ProcessAffectedObjects` コマンドの `Process` 属性を true に設定すると、指定されたオブジェクトを処理することによって影響を受ける関連オブジェクトもすべて処理されます。</span><span class="sxs-lookup"><span data-stu-id="3e5e8-147">If you set the `ProcessAffectedObjects` attribute of the `Process` command to true, any related object affected by processing the specified object is also processed.</span></span> <span data-ttu-id="3e5e8-148">たとえば、コマンドで*Processupdate*処理オプションを使用してディメンションを増分更新する場合 `Process` 、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] `ProcessAffectedObjects` が true に設定されていると、メンバーの追加または削除によって集計が無効になるパーティションは、によっても処理されます。</span><span class="sxs-lookup"><span data-stu-id="3e5e8-148">For example, if a dimension is incrementally updated by using the *ProcessUpdate* processing option in the `Process` command, any partition whose aggregations are invalidated because of members being added or deleted is also processed by [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] if `ProcessAffectedObjects` is set to true.</span></span> <span data-ttu-id="3e5e8-149">この場合、1 つの `Process` コマンドで [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスの複数のオブジェクトを処理することができますが、`Process` コマンドで指定された単一のオブジェクトの他に処理する必要があるオブジェクトは、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] によって決定されます。</span><span class="sxs-lookup"><span data-stu-id="3e5e8-149">In this case, a single `Process` command can process multiple objects on an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance, but [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] determines which objects besides the single object specified in the `Process` command must also be processed.</span></span>  
  
 <span data-ttu-id="3e5e8-150">しかし、`Process` コマンドの中で複数の `Batch` コマンドを使用することによって、ディメンションなどの複数のオブジェクトを同時に処理することもできます。</span><span class="sxs-lookup"><span data-stu-id="3e5e8-150">However, you can process multiple objects, such as dimensions, at the same time by using multiple `Process` commands within a `Batch` command.</span></span> <span data-ttu-id="3e5e8-151">バッチ操作では、`ProcessAffectedObjects` 属性を使用する場合よりも詳細なレベルで、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスのオブジェクトの直列または並列処理を制御することができ、大規模な [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースの処理方法をチューニングすることができます。</span><span class="sxs-lookup"><span data-stu-id="3e5e8-151">Batch operations provide a finer level of control for serial or parallel processing of objects on an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance than using the `ProcessAffectedObjects` attribute, and let you to tune your processing approach for larger [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] databases.</span></span> <span data-ttu-id="3e5e8-152">バッチ操作の実行の詳細については、「 [XMLA&#41;&#40;のバッチ操作の実行](performing-batch-operations-xmla.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3e5e8-152">For more information about performing batch operations, see [Performing Batch Operations &#40;XMLA&#41;](performing-batch-operations-xmla.md).</span></span>  
  
## <a name="specifying-out-of-line-bindings"></a><span data-ttu-id="3e5e8-153">不一致バインドの指定</span><span class="sxs-lookup"><span data-stu-id="3e5e8-153">Specifying Out-of-Line Bindings</span></span>  
 <span data-ttu-id="3e5e8-154">コマンド `Process` がコマンドに含まれていない場合は、 `Batch` 必要に応じて、コマンドの[bindings](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/bindings-element-xmla)、 [DataSource](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/source-element-xmla)、および[DataSourceView](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/datasourceview-element-xmla)プロパティで不一致バインドを指定して、 `Process` 処理するオブジェクトを指定できます。</span><span class="sxs-lookup"><span data-stu-id="3e5e8-154">If the `Process` command is not contained by a `Batch` command, you can optionally specify out-of-line bindings in the [Bindings](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/bindings-element-xmla), [DataSource](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/source-element-xmla), and [DataSourceView](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/datasourceview-element-xmla) properties of the `Process` command for the objects to be processed.</span></span> <span data-ttu-id="3e5e8-155">不一致バインドは、バインドが `Process` コマンドの実行時のみに存在する、データ ソース、データ ソース ビュー、および他のオブジェクトへの参照であり、処理中のオブジェクトに関連付けられている既存のバインドをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="3e5e8-155">Out-of-line bindings are references to data sources, data source views, and other objects in which the binding exists only during the execution of the `Process` command, and which override any existing bindings associated with the objects being processed.</span></span> <span data-ttu-id="3e5e8-156">不一致バインドが指定されていない場合、処理対象のオブジェクトに現在関連付けられているバインドが使用されます。</span><span class="sxs-lookup"><span data-stu-id="3e5e8-156">If out-of-line bindings are not specified, the bindings currently associated with the objects to be processed are used.</span></span>  
  
 <span data-ttu-id="3e5e8-157">不一致バインドは以下の状況で使用されます。</span><span class="sxs-lookup"><span data-stu-id="3e5e8-157">Out-of-line bindings are used in the following circumstances:</span></span>  
  
-   <span data-ttu-id="3e5e8-158">パーティションの増分更新を行う。行が 2 回カウントされないように、代替のファクト テーブルか、既存のファクト テーブルに対するフィルターを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3e5e8-158">Incrementally processing a partition, in which an alternative fact table or a filter on the existing fact table must be specified to make sure that rows are not counted twice.</span></span>  
  
-   <span data-ttu-id="3e5e8-159">のデータフロータスクを使用して、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ディメンション、マイニングモデル、またはパーティションの処理中にデータを提供します。</span><span class="sxs-lookup"><span data-stu-id="3e5e8-159">Using a data flow task in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] to provide data while processing a dimension, mining model, or partition.</span></span>  
  
 <span data-ttu-id="3e5e8-160">不一致バインドは、Analysis Services Scripting Language (ASSL) の一部として記述されます。</span><span class="sxs-lookup"><span data-stu-id="3e5e8-160">Out-of-line bindings are described as part of the Analysis Services Scripting Language (ASSL).</span></span> <span data-ttu-id="3e5e8-161">ASSL での不一致バインドの詳細については、「 [SSAS 多次元&#41;&#40;データソースとバインド](../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3e5e8-161">For more information about out-of-line bindings in ASSL, see [Data Sources and Bindings &#40;SSAS Multidimensional&#41;](../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).</span></span>  
  
### <a name="incrementally-updating-partitions"></a><span data-ttu-id="3e5e8-162">パーティションの増分更新</span><span class="sxs-lookup"><span data-stu-id="3e5e8-162">Incrementally Updating Partitions</span></span>  
 <span data-ttu-id="3e5e8-163">通常、既に処理されているパーティションを増分更新する場合は、不一致バインドが必要です。これは、パーティションに対して指定されているバインドが、既にパーティション内で集計されているファクト テーブル データを参照するためです。</span><span class="sxs-lookup"><span data-stu-id="3e5e8-163">Incrementally updating an already processed partition typically requires an out-of-line binding because the binding specified for the partition references fact table data already aggregated within the partition.</span></span> <span data-ttu-id="3e5e8-164">既に処理されているパーティションを `Process` コマンドを使用して増分更新する場合、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は以下のアクションを実行します。</span><span class="sxs-lookup"><span data-stu-id="3e5e8-164">When incrementally updating an already processed partition by using the `Process` command, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] performs the following actions:</span></span>  
  
-   <span data-ttu-id="3e5e8-165">増分更新を行うパーティションと同じ構造の一時パーティションを作成します。</span><span class="sxs-lookup"><span data-stu-id="3e5e8-165">Creates a temporary partition with a structure identical to that of the partition to be incrementally updated.</span></span>  
  
-   <span data-ttu-id="3e5e8-166">`Process` コマンドで指定された不一致バインドを使用して、一時パーティションを処理します。</span><span class="sxs-lookup"><span data-stu-id="3e5e8-166">Processes the temporary partition, using the out-of-line binding specified in the `Process` command.</span></span>  
  
-   <span data-ttu-id="3e5e8-167">一時パーティションを、選択された既存のパーティションにマージします。</span><span class="sxs-lookup"><span data-stu-id="3e5e8-167">Merges the temporary partition with the existing selected partition.</span></span>  
  
 <span data-ttu-id="3e5e8-168">XML for Analysis (XMLA) を使用したパーティションのマージの詳細については、「 [xmla&#41;&#40;のパーティションのマージ](merging-partitions-xmla.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3e5e8-168">For more information about merging partitions using XML for Analysis (XMLA), see [Merging Partitions &#40;XMLA&#41;](merging-partitions-xmla.md).</span></span>  
  
## <a name="handling-processing-errors"></a><span data-ttu-id="3e5e8-169">処理エラーの処理</span><span class="sxs-lookup"><span data-stu-id="3e5e8-169">Handling Processing Errors</span></span>  
 <span data-ttu-id="3e5e8-170">コマンドの[Errorconfiguration](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/errorconfiguration-element-xmla)プロパティでは、 `Process` オブジェクトの処理中に発生したエラーの処理方法を指定できます。</span><span class="sxs-lookup"><span data-stu-id="3e5e8-170">The [ErrorConfiguration](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/errorconfiguration-element-xmla) property of the `Process` command lets you specify how to handle errors encountered while processing an object.</span></span> <span data-ttu-id="3e5e8-171">たとえば、ディメンションの処理時に、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] がキー属性のキー列で重複した値を検出したとします。</span><span class="sxs-lookup"><span data-stu-id="3e5e8-171">For example, while processing a dimension, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] encounters a duplicate value in the key column of the key attribute.</span></span> <span data-ttu-id="3e5e8-172">属性キーは一意である必要があるため、重複するレコードは [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] によって破棄されます。</span><span class="sxs-lookup"><span data-stu-id="3e5e8-172">Because attribute keys must be unique, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] discards the duplicate records.</span></span> <span data-ttu-id="3e5e8-173">の[Keyduplicate](https://docs.microsoft.com/bi-reference/assl/properties/keyduplicate-element-assl)プロパティに基づいて `ErrorConfiguration` 、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 次のことが考えられます。</span><span class="sxs-lookup"><span data-stu-id="3e5e8-173">Based on the [KeyDuplicate](https://docs.microsoft.com/bi-reference/assl/properties/keyduplicate-element-assl) property of `ErrorConfiguration`, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] could:</span></span>  
  
-   <span data-ttu-id="3e5e8-174">エラーを無視し、ディメンションの処理を続行する。</span><span class="sxs-lookup"><span data-stu-id="3e5e8-174">Ignore the error and continue processing the dimension.</span></span>  
  
-   <span data-ttu-id="3e5e8-175">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] が重複したキーを検出したことを示すメッセージを返し、処理を続行する。</span><span class="sxs-lookup"><span data-stu-id="3e5e8-175">Return a message that states [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] encountered a duplicate key and continue processing.</span></span>  
  
 <span data-ttu-id="3e5e8-176">`ErrorConfiguration` によって `Process` コマンドの実行時のオプションが指定される同様の状況は、他にも多くあります。</span><span class="sxs-lookup"><span data-stu-id="3e5e8-176">There are many similar conditions for which `ErrorConfiguration` provides options during a `Process` command.</span></span>  
  
## <a name="managing-writeback-tables"></a><span data-ttu-id="3e5e8-177">書き戻しテーブルの管理</span><span class="sxs-lookup"><span data-stu-id="3e5e8-177">Managing Writeback Tables</span></span>  
 <span data-ttu-id="3e5e8-178">`Process` コマンドで、まだ完全に処理されていない書き込み許可パーティション、または完全に処理されていない書き込み許可パーティションに対するキューブやメジャー グループが見つかった場合、そのパーティションには書き戻しテーブルがまだ存在していない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="3e5e8-178">If the `Process` command encounters a write-enabled partition, or a cube or measure group for such a partition, that is not already fully processed, a writeback table may not already exist for that partition.</span></span> <span data-ttu-id="3e5e8-179">コマンドの[WritebackTableCreation](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/writebacktablecreation-element-xmla)プロパティは、 `Process` [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] が書き戻しテーブルを作成するかどうかを決定します。</span><span class="sxs-lookup"><span data-stu-id="3e5e8-179">The [WritebackTableCreation](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/writebacktablecreation-element-xmla) property of the `Process` command determines whether [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] should create a writeback table.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="3e5e8-180">例</span><span class="sxs-lookup"><span data-stu-id="3e5e8-180">Examples</span></span>  
  
### <a name="description"></a><span data-ttu-id="3e5e8-181">説明</span><span class="sxs-lookup"><span data-stu-id="3e5e8-181">Description</span></span>  
 <span data-ttu-id="3e5e8-182">次の例は、[!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] の [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] サンプル データベースを完全に処理します。</span><span class="sxs-lookup"><span data-stu-id="3e5e8-182">The following example fully processes the [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] sample [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database.</span></span>  
  
### <a name="code"></a><span data-ttu-id="3e5e8-183">コード</span><span class="sxs-lookup"><span data-stu-id="3e5e8-183">Code</span></span>  
  
```  
<Process xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
  <Object>  
    <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
  </Object>  
  <Type>ProcessFull</Type>  
  <WriteBackTableCreation>UseExisting</WriteBackTableCreation>  
</Process>  
```  
  
### <a name="description"></a><span data-ttu-id="3e5e8-184">説明</span><span class="sxs-lookup"><span data-stu-id="3e5e8-184">Description</span></span>  
 <span data-ttu-id="3e5e8-185">次の例では、サンプルデータベースの**Adventure WORKS DW**キューブの**Internet Sales**メジャーグループの**Internet_Sales_2004**パーティションを増分処理し [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="3e5e8-185">The following example incrementally processes the **Internet_Sales_2004** partition in the **Internet Sales** measure group of the **Adventure Works DW** cube in the [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] sample [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database.</span></span> <span data-ttu-id="3e5e8-186">コマンドは、 `Process` コマンドのプロパティで不一致クエリバインドを使用して、パーティションに `Bindings` `Process` 追加する集計を生成するファクトテーブルの行を取得することにより、2006年12月31日より後の注文日の集計をパーティションに追加します。</span><span class="sxs-lookup"><span data-stu-id="3e5e8-186">The `Process` command is adding aggregations for order dates later than December 31, 2006 to the partition by using an out-of-line query binding in the `Bindings` property of the `Process` command to retrieve the fact table rows from which to generate aggregations to add to the partition.</span></span>  
  
### <a name="code"></a><span data-ttu-id="3e5e8-187">コード</span><span class="sxs-lookup"><span data-stu-id="3e5e8-187">Code</span></span>  
  
```  
<Process ProcessAffectedObjects="true" xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
  <Object>  
    <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
    <CubeID>Adventure Works DW</CubeID>  
    <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>  
    <PartitionID>Internet_Sales_2006</PartitionID>  
  </Object>  
  <Bindings>  
    <Binding>  
      <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
      <CubeID>Adventure Works DW</CubeID>  
      <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>  
      <PartitionID>Internet_Sales_2006</PartitionID>  
      <Source xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:type="QueryBinding">  
        <DataSourceID>Adventure Works DW</DataSourceID>  
        <QueryDefinition>  
          SELECT  
            [dbo].[FactInternetSales].[ProductKey],  
            [dbo].[FactInternetSales].[OrderDateKey],  
            [dbo].[FactInternetSales].[DueDateKey],  
            [dbo].[FactInternetSales].[ShipDateKey],   
            [dbo].[FactInternetSales].[CustomerKey],   
            [dbo].[FactInternetSales].[PromotionKey],  
            [dbo].[FactInternetSales].[CurrencyKey],  
            [dbo].[FactInternetSales].[SalesTerritoryKey],  
            [dbo].[FactInternetSales].[SalesOrderNumber],  
            [dbo].[FactInternetSales].[SalesOrderLineNumber],  
            [dbo].[FactInternetSales].[RevisionNumber],  
            [dbo].[FactInternetSales].[OrderQuantity],  
            [dbo].[FactInternetSales].[UnitPrice],  
            [dbo].[FactInternetSales].[ExtendedAmount],  
            [dbo].[FactInternetSales].[UnitPriceDiscountPct],  
            [dbo].[FactInternetSales].[DiscountAmount],  
            [dbo].[FactInternetSales].[ProductStandardCost],  
            [dbo].[FactInternetSales].[TotalProductCost],  
            [dbo].[FactInternetSales].[SalesAmount],  
            [dbo].[FactInternetSales].[TaxAmt],  
            [dbo].[FactInternetSales].[Freight],  
            [dbo].[FactInternetSales].[CarrierTrackingNumber],  
            [dbo].[FactInternetSales].[CustomerPONumber]  
          FROM [dbo].[FactInternetSales]  
          WHERE OrderDateKey > '1280'  
        </QueryDefinition>  
      </Source>  
    </Binding>  
  </Bindings>  
  <Type>ProcessAdd</Type>  
  <WriteBackTableCreation>UseExisting</WriteBackTableCreation>  
</Process>  
```  
  
  
