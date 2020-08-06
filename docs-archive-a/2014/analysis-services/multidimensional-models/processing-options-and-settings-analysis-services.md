---
title: 処理オプションと設定 (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- process data option [Analysis Services]
- processing objects [Analysis Services]
- unprocess option [Analysis Services]
- process full option [Analysis Services]
- process index option [Analysis Services]
- process structure option [Analysis Services]
- process incremental option [Analysis Services]
- process update option [Analysis Services]
- process clear structure option [Analysis Services]
- process default option [Analysis Services]
ms.assetid: 2e858c74-ad3e-45f1-8745-efe2c0c3a7fa
author: minewiskan
ms.author: owend
ms.openlocfilehash: 00efad4483be1d4e646b33485f5fddf01dfb74b8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633404"
---
# <a name="processing-options-and-settings-analysis-services"></a><span data-ttu-id="3c33c-102">処理オプションと設定 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="3c33c-102">Processing Options and Settings (Analysis Services)</span></span>
  <span data-ttu-id="3c33c-103">でオブジェクトを処理するときに [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 、処理オプションを選択して、各オブジェクトに対して発生する処理の種類を制御できます。</span><span class="sxs-lookup"><span data-stu-id="3c33c-103">When you process objects in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], you can select a processing option to control the type of processing that occurs for each object.</span></span> <span data-ttu-id="3c33c-104">処理の種類はオブジェクトごとに異なるほか、オブジェクトに対する変更内容 (オブジェクトが前回処理されたことによって発生した変更) によっても異なります。</span><span class="sxs-lookup"><span data-stu-id="3c33c-104">Processing types differ from one object to another, and by changes that have occurred to the object since it was last processed.</span></span> <span data-ttu-id="3c33c-105">処理方法を自動的に選択する [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] の機能を有効にすると、オブジェクトを完全処理状態に最短時間で戻す方法が使用されます。</span><span class="sxs-lookup"><span data-stu-id="3c33c-105">If you enable [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] to automatically select a processing method, it will use the method that returns the object to a fully processed state in the least time.</span></span>  
  
 <span data-ttu-id="3c33c-106">処理オプションを設定することにより、処理されるオブジェクト、およびオブジェクトの処理方法を制御できます。</span><span class="sxs-lookup"><span data-stu-id="3c33c-106">Processing settings let you control the objects that are processed, and the methods that are used to process those objects.</span></span> <span data-ttu-id="3c33c-107">このような設定のいくつかは、主にバッチ処理ジョブで使用されます。</span><span class="sxs-lookup"><span data-stu-id="3c33c-107">Some processing settings are primarily used for batch processing jobs.</span></span> <span data-ttu-id="3c33c-108">バッチ処理の詳細については、「[バッチ処理 (Analysis Services)](batch-processing-analysis-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3c33c-108">For more information about batch processing, see [Batch Processing &#40;Analysis Services&#41;](batch-processing-analysis-services.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3c33c-109">このトピックは、多次元、およびデータ マイニングの各ソリューションに適用されます。</span><span class="sxs-lookup"><span data-stu-id="3c33c-109">This topic applies to multidimensional and data mining solutions.</span></span> <span data-ttu-id="3c33c-110">テーブルソリューションの詳細については、「[データベース、テーブル、またはパーティションの処理](../tabular-models/process-database-table-or-partition-analysis-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3c33c-110">For information about tabular solutions, see [Process Database, Table, or Partition](../tabular-models/process-database-table-or-partition-analysis-services.md).</span></span>  
  
## <a name="processing-options"></a><span data-ttu-id="3c33c-111">処理オプション</span><span class="sxs-lookup"><span data-stu-id="3c33c-111">Processing Options</span></span>  
 <span data-ttu-id="3c33c-112">次の表に、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]で使用できる処理方法と、それぞれの方法でサポートされているオブジェクトを示します。</span><span class="sxs-lookup"><span data-stu-id="3c33c-112">The following table describes the processing methods that are available in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], and identifies the objects for which each method is supported.</span></span>  
  
|<span data-ttu-id="3c33c-113">モード</span><span class="sxs-lookup"><span data-stu-id="3c33c-113">Mode</span></span>|<span data-ttu-id="3c33c-114">適用対象</span><span class="sxs-lookup"><span data-stu-id="3c33c-114">Applies to</span></span>|<span data-ttu-id="3c33c-115">説明</span><span class="sxs-lookup"><span data-stu-id="3c33c-115">Description</span></span>|  
|----------|----------------|-----------------|  
|<span data-ttu-id="3c33c-116">**既定の処理**</span><span class="sxs-lookup"><span data-stu-id="3c33c-116">**Process Default**</span></span>|<span data-ttu-id="3c33c-117">キューブ、データベース、ディメンション、メジャー グループ、マイニング モデル、マイニング構造、パーティション</span><span class="sxs-lookup"><span data-stu-id="3c33c-117">Cubes, databases, dimensions, measure groups, mining models, mining structures, and partitions.</span></span>|<span data-ttu-id="3c33c-118">データベース オブジェクトの処理状態を検出し、処理されていないオブジェクトや部分的に処理されたオブジェクトを完全処理状態にするために必要な処理を行います。</span><span class="sxs-lookup"><span data-stu-id="3c33c-118">Detects the process state of database objects, and performs processing necessary to deliver unprocessed or partially processed objects to a fully processed state.</span></span> <span data-ttu-id="3c33c-119">データ バインドを変更した場合、"既定の処理" では、影響を受けるオブジェクトに対して "完全処理" が実行されます。</span><span class="sxs-lookup"><span data-stu-id="3c33c-119">If you change a data binding, Process Default will do a Process Full on the affected object.</span></span>|  
|<span data-ttu-id="3c33c-120">**完全処理**</span><span class="sxs-lookup"><span data-stu-id="3c33c-120">**Process Full**</span></span>|<span data-ttu-id="3c33c-121">キューブ、データベース、ディメンション、メジャー グループ、マイニング モデル、マイニング構造、パーティション</span><span class="sxs-lookup"><span data-stu-id="3c33c-121">Cubes, databases, dimensions, measure groups, mining models, mining structures, and partitions.</span></span>|<span data-ttu-id="3c33c-122">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] オブジェクトとそのオブジェクトに含まれるすべてのオブジェクトを処理します。</span><span class="sxs-lookup"><span data-stu-id="3c33c-122">Processes an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] object and all the objects that it contains.</span></span> <span data-ttu-id="3c33c-123">既に処理済みのオブジェクトに対して Process Full を実行した場合、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] はオブジェクト内のすべてのデータを削除してからオブジェクトを処理します。</span><span class="sxs-lookup"><span data-stu-id="3c33c-123">When Process Full is executed against an object that has already been processed, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] drops all data in the object, and then processes the object.</span></span> <span data-ttu-id="3c33c-124">この種類の処理は、属性階層の追加、削除、または名前変更など、構造上の変更がオブジェクトに加えられた場合に必要です。</span><span class="sxs-lookup"><span data-stu-id="3c33c-124">This kind of processing is required when a structural change has been made to an object, for example, when an attribute hierarchy is added, deleted, or renamed.</span></span>|  
|<span data-ttu-id="3c33c-125">**消去の処理**</span><span class="sxs-lookup"><span data-stu-id="3c33c-125">**Process Clear**</span></span>|<span data-ttu-id="3c33c-126">キューブ、データベース、ディメンション、メジャー グループ、マイニング モデル、マイニング構造、パーティション</span><span class="sxs-lookup"><span data-stu-id="3c33c-126">Cubes, databases, dimensions, measure groups, mining models, mining structures, and partitions.</span></span>|<span data-ttu-id="3c33c-127">指定されたオブジェクトとその下位オブジェクトに含まれているデータを削除します。</span><span class="sxs-lookup"><span data-stu-id="3c33c-127">Drops the data in the object specified and any lower-level constituent objects.</span></span> <span data-ttu-id="3c33c-128">削除されたデータは、再読み込みされません。</span><span class="sxs-lookup"><span data-stu-id="3c33c-128">After the data is dropped, it is not reloaded.</span></span>|  
|<span data-ttu-id="3c33c-129">**データの処理**</span><span class="sxs-lookup"><span data-stu-id="3c33c-129">**Process Data**</span></span>|<span data-ttu-id="3c33c-130">ディメンション、キューブ、メジャー グループ、パーティション</span><span class="sxs-lookup"><span data-stu-id="3c33c-130">Dimensions, cubes, measure groups, and partitions.</span></span>|<span data-ttu-id="3c33c-131">集計またはインデックスを構築することなくデータのみを処理します。</span><span class="sxs-lookup"><span data-stu-id="3c33c-131">Processes data only without building aggregations or indexes.</span></span> <span data-ttu-id="3c33c-132">パーティション内にデータが存在する場合、そのパーティションにソース データを再設定する前にデータが削除されます。</span><span class="sxs-lookup"><span data-stu-id="3c33c-132">If there is data is in the partitions, it will be dropped before re-populating the partition with source data.</span></span>|  
|<span data-ttu-id="3c33c-133">**追加の処理**</span><span class="sxs-lookup"><span data-stu-id="3c33c-133">**Process Add**</span></span>|<span data-ttu-id="3c33c-134">ディメンション、メジャー グループ、パーティション</span><span class="sxs-lookup"><span data-stu-id="3c33c-134">Dimensions, measure groups, and partitions</span></span><br /><br /> <span data-ttu-id="3c33c-135">注: 追加の処理 は [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]でのディメンション処理には使用できませんが、この処理を実行する XMLA スクリプトを記述できます。</span><span class="sxs-lookup"><span data-stu-id="3c33c-135">Note: Process Add is not available for dimension processing in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], but you can write XMLA script performs this action.</span></span>|<span data-ttu-id="3c33c-136">ディメンションの場合、新しいメンバーを追加したり、ディメンション属性のキャプションや説明を更新します。</span><span class="sxs-lookup"><span data-stu-id="3c33c-136">For dimensions, adds new members and updates dimension attribute captions and descriptions.</span></span><br /><br /> <span data-ttu-id="3c33c-137">メジャー グループおよびパーティションの場合、新しく使用できるようになったファクト データとプロセスを、関連するパーティションにのみ追加します。</span><span class="sxs-lookup"><span data-stu-id="3c33c-137">For measure groups and partitions, adds newly available fact data and process only to the relevant partitions.</span></span>|  
|<span data-ttu-id="3c33c-138">**更新の処理**</span><span class="sxs-lookup"><span data-stu-id="3c33c-138">**Process Update**</span></span>|<span data-ttu-id="3c33c-139">Dimensions</span><span class="sxs-lookup"><span data-stu-id="3c33c-139">Dimensions</span></span>|<span data-ttu-id="3c33c-140">強制的にデータを再読み込みし、ディメンション属性を更新します。</span><span class="sxs-lookup"><span data-stu-id="3c33c-140">Forces a re-read of data and an update of dimension attributes.</span></span> <span data-ttu-id="3c33c-141">関連するパーティション上の柔軟な集計とインデックスが削除されます。</span><span class="sxs-lookup"><span data-stu-id="3c33c-141">Flexible aggregations and indexes on related partitions will be dropped.</span></span>|  
|<span data-ttu-id="3c33c-142">**インデックスの処理**</span><span class="sxs-lookup"><span data-stu-id="3c33c-142">**Process Index**</span></span>|<span data-ttu-id="3c33c-143">キューブ、ディメンション、メジャー グループ、パーティション</span><span class="sxs-lookup"><span data-stu-id="3c33c-143">Cubes, dimensions, measure groups, and partitions</span></span>|<span data-ttu-id="3c33c-144">処理済みのすべてのパーティションに対するインデックスおよび集計を作成または再構築します。</span><span class="sxs-lookup"><span data-stu-id="3c33c-144">Creates or rebuilds indexes and aggregations for all processed partitions.</span></span> <span data-ttu-id="3c33c-145">未処理のオブジェクトではエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="3c33c-145">For unprocessed objects, this option generates an error.</span></span><br /><br /> <span data-ttu-id="3c33c-146">"レイジー処理" をオフにした場合、このオプションでの処理が必要となります。</span><span class="sxs-lookup"><span data-stu-id="3c33c-146">Processing with this option is needed if you turn off Lazy Processing.</span></span>|  
|<span data-ttu-id="3c33c-147">**構造の処理**</span><span class="sxs-lookup"><span data-stu-id="3c33c-147">**Process Structure**</span></span>|<span data-ttu-id="3c33c-148">キューブ、マイニング構造</span><span class="sxs-lookup"><span data-stu-id="3c33c-148">Cubes and mining structures</span></span>|<span data-ttu-id="3c33c-149">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] では、キューブが処理されていない場合、必要に応じてキューブのすべてのディメンションが処理されます。</span><span class="sxs-lookup"><span data-stu-id="3c33c-149">If the cube is unprocessed, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] will process, if it is necessary, all the cube's dimensions.</span></span> <span data-ttu-id="3c33c-150">その後、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は、キューブ定義だけを作成します。</span><span class="sxs-lookup"><span data-stu-id="3c33c-150">After that, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] will create only cube definitions.</span></span> <span data-ttu-id="3c33c-151">このオプションをマイニング構造に適用すると、マイニング構造にソース データが設定されます。</span><span class="sxs-lookup"><span data-stu-id="3c33c-151">If this option is applied to a mining structure, it populates the mining structure with source data.</span></span> <span data-ttu-id="3c33c-152">このオプションと完全処理オプションの違いは、このオプションでは、マイニング モデル自体まで処理が繰り返されないという点です。</span><span class="sxs-lookup"><span data-stu-id="3c33c-152">The difference between this option and the Process Full option is that this option does not iterate the processing down to the mining models themselves.</span></span>|  
|<span data-ttu-id="3c33c-153">**構造消去の処理**</span><span class="sxs-lookup"><span data-stu-id="3c33c-153">**Process Clear Structure**</span></span>|<span data-ttu-id="3c33c-154">マイニング構造</span><span class="sxs-lookup"><span data-stu-id="3c33c-154">Mining structures</span></span>|<span data-ttu-id="3c33c-155">マイニング構造からすべてのトレーニング データを削除します。</span><span class="sxs-lookup"><span data-stu-id="3c33c-155">Removes all training data from a mining structure.</span></span>|  
  
## <a name="processing-settings"></a><span data-ttu-id="3c33c-156">処理の設定</span><span class="sxs-lookup"><span data-stu-id="3c33c-156">Processing Settings</span></span>  
 <span data-ttu-id="3c33c-157">次の表では、処理操作の作成時に使用できる処理オプションの設定について説明します。</span><span class="sxs-lookup"><span data-stu-id="3c33c-157">The following table describes the processing settings that are available for use when you create a process operation.</span></span>  
  
|<span data-ttu-id="3c33c-158">処理オプション</span><span class="sxs-lookup"><span data-stu-id="3c33c-158">Processing Option</span></span>|<span data-ttu-id="3c33c-159">説明</span><span class="sxs-lookup"><span data-stu-id="3c33c-159">Description</span></span>|  
|-----------------------|-----------------|  
|<span data-ttu-id="3c33c-160">**Parallel**</span><span class="sxs-lookup"><span data-stu-id="3c33c-160">**Parallel**</span></span>|<span data-ttu-id="3c33c-161">バッチ処理に使用します。</span><span class="sxs-lookup"><span data-stu-id="3c33c-161">Used for batch processing.</span></span> <span data-ttu-id="3c33c-162">この設定により、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は、処理タスクを分岐して 1 つのトランザクション内で同時に実行します。</span><span class="sxs-lookup"><span data-stu-id="3c33c-162">This setting causes [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] to fork off processing tasks to run in parallel inside a single transaction.</span></span> <span data-ttu-id="3c33c-163">エラーが発生した場合は、すべての変更がロールバックされます。</span><span class="sxs-lookup"><span data-stu-id="3c33c-163">If there is a failure, the result is a roll-back of all changes.</span></span> <span data-ttu-id="3c33c-164">並列タスクの最大数を明示的に設定するか、サーバーに最適な分散を自動的に判断させることもできます。</span><span class="sxs-lookup"><span data-stu-id="3c33c-164">You can set the maximum number of parallel tasks explicitly, or let the server decide the optimal distribution.</span></span> <span data-ttu-id="3c33c-165">並列オプションは、処理の高速化に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="3c33c-165">The Parallel option is useful for speeding up processing.</span></span>|  
|<span data-ttu-id="3c33c-166">**シーケンシャル (トランザクション モード)**</span><span class="sxs-lookup"><span data-stu-id="3c33c-166">**Sequential (Transaction Mode)**</span></span>|<span data-ttu-id="3c33c-167">処理ジョブの実行動作を制御します。</span><span class="sxs-lookup"><span data-stu-id="3c33c-167">Controls the execution behavior of the processing job.</span></span> <span data-ttu-id="3c33c-168">**[1 つのトランザクション]** を使用して処理する場合、処理ジョブが成功した後にすべての変更がコミットされます。</span><span class="sxs-lookup"><span data-stu-id="3c33c-168">When you process using **One Transaction**, all changes are committed after the processing job succeeds.</span></span> <span data-ttu-id="3c33c-169">つまり、コミット処理までは、特定の処理ジョブの影響を受けるすべての [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] オブジェクトをそのままクエリ用に使用できます。</span><span class="sxs-lookup"><span data-stu-id="3c33c-169">This means that all [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] objects affected by a particular processing job remain available for queries until the commit process.</span></span> <span data-ttu-id="3c33c-170">これにより、オブジェクトは一時的に使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="3c33c-170">This makes the objects temporarily unavailable.</span></span> <span data-ttu-id="3c33c-171">**[個別のトランザクション]** を使用した場合、処理ジョブ内の処理の影響を受けるすべてのオブジェクトは、その処理が成功するとすぐに、クエリ用に使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="3c33c-171">Using **Separate Transactions** causes all objects that are affected by a process in processing job to be taken unavailable for queries as soon as that process succeeds.</span></span> <span data-ttu-id="3c33c-172">次の2つのオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="3c33c-172">The two available options are:</span></span><br /><br /> <span data-ttu-id="3c33c-173">**[1 つのトランザクション]**。</span><span class="sxs-lookup"><span data-stu-id="3c33c-173">**One Transaction**.</span></span> <span data-ttu-id="3c33c-174">処理ジョブは 1 つのトランザクションとして実行されます。</span><span class="sxs-lookup"><span data-stu-id="3c33c-174">The processing job runs as a transaction.</span></span> <span data-ttu-id="3c33c-175">処理ジョブ内のすべての処理が成功すると、処理ジョブによる変更がすべてコミットされます。</span><span class="sxs-lookup"><span data-stu-id="3c33c-175">If all processes inside the processing job succeed, all changes by the processing job are committed.</span></span> <span data-ttu-id="3c33c-176">処理が 1 つ失敗すると、処理ジョブによる変更がすべてロールバックされます。</span><span class="sxs-lookup"><span data-stu-id="3c33c-176">If one process fails, all changes by the processing job are rolled back.</span></span> <span data-ttu-id="3c33c-177">**[1 つのトランザクション]** が既定値です。</span><span class="sxs-lookup"><span data-stu-id="3c33c-177">**One Transaction** is the default value.</span></span><br /><br /> <span data-ttu-id="3c33c-178">**[個別のトランザクション]**。</span><span class="sxs-lookup"><span data-stu-id="3c33c-178">**Separate Transactions**.</span></span> <span data-ttu-id="3c33c-179">処理ジョブ内の各処理はスタンドアロンのジョブとして実行されます。</span><span class="sxs-lookup"><span data-stu-id="3c33c-179">Each process in the processing job runs as a stand-alone job.</span></span> <span data-ttu-id="3c33c-180">処理が 1 つ失敗すると、その処理だけがロールバックされ、処理ジョブは続行されます。</span><span class="sxs-lookup"><span data-stu-id="3c33c-180">If one process fails, only that process is rolled back and the processing job continues.</span></span> <span data-ttu-id="3c33c-181">各ジョブでは、そのジョブの最後に処理の変更がすべてコミットされます。</span><span class="sxs-lookup"><span data-stu-id="3c33c-181">Each job commits all process changes at the end of the job.</span></span>|  
|<span data-ttu-id="3c33c-182">**書き戻しテーブルオプション**</span><span class="sxs-lookup"><span data-stu-id="3c33c-182">**Writeback Table Option**</span></span>|<span data-ttu-id="3c33c-183">処理中に書き戻しテーブルをどのように処理するかを制御します。</span><span class="sxs-lookup"><span data-stu-id="3c33c-183">Controls how writeback tables are handled during processing.</span></span> <span data-ttu-id="3c33c-184">このオプションは、キューブ内の書き戻しパーティションに適用され、次のオプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="3c33c-184">This option applies to writeback partitions in a cube, and uses the following options:</span></span><br /><br /> <span data-ttu-id="3c33c-185">**既存のを使用**します。</span><span class="sxs-lookup"><span data-stu-id="3c33c-185">**Use Existing**.</span></span> <span data-ttu-id="3c33c-186">既存の書き戻しテーブルを使用します。</span><span class="sxs-lookup"><span data-stu-id="3c33c-186">Uses the existing writeback table.</span></span> <span data-ttu-id="3c33c-187">これは既定値です。</span><span class="sxs-lookup"><span data-stu-id="3c33c-187">This is default value.</span></span><br /><br /> <span data-ttu-id="3c33c-188">**Create**。</span><span class="sxs-lookup"><span data-stu-id="3c33c-188">**Create**.</span></span> <span data-ttu-id="3c33c-189">新しい書き戻しテーブルを作成します。書き戻しテーブルが既に存在する場合、その処理は失敗します。</span><span class="sxs-lookup"><span data-stu-id="3c33c-189">Creates a new writeback table and causes the process to fail if one already exists.</span></span><br /><br /> <span data-ttu-id="3c33c-190">**[常に作成する]**。</span><span class="sxs-lookup"><span data-stu-id="3c33c-190">**Create Always**.</span></span> <span data-ttu-id="3c33c-191">書き戻しテーブルが既に存在する場合でも新しい書き戻しテーブルを作成します。</span><span class="sxs-lookup"><span data-stu-id="3c33c-191">Creates a new writeback table even if one already exists.</span></span> <span data-ttu-id="3c33c-192">既存のテーブルは削除されて置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="3c33c-192">An existing table is deleted and replaced.</span></span>|  
|<span data-ttu-id="3c33c-193">**影響を受けたオブジェクトの処理**</span><span class="sxs-lookup"><span data-stu-id="3c33c-193">**Process Affected Objects**</span></span>|<span data-ttu-id="3c33c-194">処理ジョブのオブジェクトのスコープを制御します。</span><span class="sxs-lookup"><span data-stu-id="3c33c-194">Controls the object scope of the processing job.</span></span> <span data-ttu-id="3c33c-195">影響を受けるオブジェクトは、オブジェクトの依存関係によって定義されます。</span><span class="sxs-lookup"><span data-stu-id="3c33c-195">An affected object is defined by object dependency.</span></span> <span data-ttu-id="3c33c-196">たとえば、パーティションは、集計を決定するディメンションに依存しますが、ディメンションはパーティションに依存しません。</span><span class="sxs-lookup"><span data-stu-id="3c33c-196">For example, partitions are dependent on the dimensions that determine aggregation, but dimensions are not dependent on partitions.</span></span> <span data-ttu-id="3c33c-197">以下のオプションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="3c33c-197">You can use the following options:</span></span><br /><br /> <span data-ttu-id="3c33c-198">**False**。</span><span class="sxs-lookup"><span data-stu-id="3c33c-198">**False**.</span></span> <span data-ttu-id="3c33c-199">ジョブは、そのジョブで明示的に指定されたオブジェクトとすべての依存オブジェクトを処理します。</span><span class="sxs-lookup"><span data-stu-id="3c33c-199">The job processes the objects explicitly named in the job and all dependent objects.</span></span> <span data-ttu-id="3c33c-200">たとえば、処理ジョブにディメンションしか含まれていない場合、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は、そのジョブで明示的に特定されたオブジェクトだけを処理します。</span><span class="sxs-lookup"><span data-stu-id="3c33c-200">For example, if the processing job contains only dimensions, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] processes just those objects explicitly identified in the job.</span></span> <span data-ttu-id="3c33c-201">処理ジョブにパーティションが含まれている場合は、パーティションを処理すると、影響を受けるディメンションに関する処理が自動的に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="3c33c-201">If the processing job contains partitions, partition processing automatically invokes processing of affected dimensions.</span></span> <span data-ttu-id="3c33c-202">**[False]** が既定の設定です。</span><span class="sxs-lookup"><span data-stu-id="3c33c-202">**False** is the default setting.</span></span><br /><br /> <span data-ttu-id="3c33c-203">**True**。</span><span class="sxs-lookup"><span data-stu-id="3c33c-203">**True**.</span></span> <span data-ttu-id="3c33c-204">ジョブによって処理されるのは、そのジョブで明示的に指定されたオブジェクト、すべての依存オブジェクト、および処理されるオブジェクトの影響を受けるすべてのオブジェクトです。ただし、影響を受けるオブジェクトの状態は変更されません。</span><span class="sxs-lookup"><span data-stu-id="3c33c-204">The job processes the objects explicitly named in the job, all dependent objects, and all objects affected by the objects being processed without changing the state of the affected objects.</span></span> <span data-ttu-id="3c33c-205">たとえば、処理ジョブにディメンションしか含まれていない場合、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は、現在処理済みの状態にあるパーティションに対してディメンション処理を行ったときに影響を受けるすべてのパーティションも処理します。</span><span class="sxs-lookup"><span data-stu-id="3c33c-205">For example, if the processing job contains only dimensions, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] also processes all partitions affected by the dimension processing for partitions that are currently in a processed state.</span></span> <span data-ttu-id="3c33c-206">影響を受けるパーティションのうち、現在未処理の状態にあるパーティションは処理されません。</span><span class="sxs-lookup"><span data-stu-id="3c33c-206">Affected partitions that are currently in an unprocessed state are not processed.</span></span> <span data-ttu-id="3c33c-207">ただし、パーティションはディメンションに依存するため、処理ジョブにパーティションしか含まれていない場合は、ディメンションが現在未処理の状態にあっても、パーティションを処理すると、影響を受けるディメンションの処理が自動的に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="3c33c-207">However, because partitions are dependent on dimensions, if the processing job contains only partitions, partition processing automatically invokes processing of affected dimensions, even when the dimension is currently in an unprocessed state.</span></span>|  
|<span data-ttu-id="3c33c-208">**ディメンション キーのエラー**</span><span class="sxs-lookup"><span data-stu-id="3c33c-208">**Dimension Key Errors**</span></span>|<span data-ttu-id="3c33c-209">処理中にエラーが発生した場合に [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] で実行されるアクションを決定します。</span><span class="sxs-lookup"><span data-stu-id="3c33c-209">Determines the action taken by [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] when errors occur during processing.</span></span> <span data-ttu-id="3c33c-210">[既定のエラー構成を使用する] を選択すると、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] では、処理される各オブジェクトに設定されているエラー構成が使用されます。</span><span class="sxs-lookup"><span data-stu-id="3c33c-210">When you select Use default error configuration, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] uses the error configuration that is set for each object being processed.</span></span> <span data-ttu-id="3c33c-211">既定の構成設定を使用するようにオブジェクトを設定すると、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] では、各オプションに指定されている既定の設定が使用されます。</span><span class="sxs-lookup"><span data-stu-id="3c33c-211">If an object is set to use default configuration settings, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] uses the default settings that are listed for each option.</span></span> <span data-ttu-id="3c33c-212">[**カスタムエラー構成を使用**する] を選択すると、次のアクションの値を選択して、エラー処理の動作を制御できます。</span><span class="sxs-lookup"><span data-stu-id="3c33c-212">When you select **Use custom error configuration**, you can select values for the following actions to control error-handling behavior:</span></span><br /><br /> <span data-ttu-id="3c33c-213">**キーエラーアクション**。</span><span class="sxs-lookup"><span data-stu-id="3c33c-213">**Key error action**.</span></span> <span data-ttu-id="3c33c-214">レコードにキー値がまだ存在していない場合、次のいずれかのアクションが行われるように選択します。</span><span class="sxs-lookup"><span data-stu-id="3c33c-214">If a key value does not yet exist in a record, one of these actions is selected to occur:</span></span><br /><br /> <span data-ttu-id="3c33c-215">**[不明な種類に変換]**。</span><span class="sxs-lookup"><span data-stu-id="3c33c-215">**Convert to unknown**.</span></span> <span data-ttu-id="3c33c-216">このキーは不明メンバーとして解釈されます。</span><span class="sxs-lookup"><span data-stu-id="3c33c-216">The key is interpreted as an unknown member.</span></span> <span data-ttu-id="3c33c-217">これが既定の設定です。</span><span class="sxs-lookup"><span data-stu-id="3c33c-217">This is the default setting.</span></span><br /><br /> <span data-ttu-id="3c33c-218">**[レコードの破棄]**。</span><span class="sxs-lookup"><span data-stu-id="3c33c-218">**Discard record**.</span></span> <span data-ttu-id="3c33c-219">レコードが破棄されます。</span><span class="sxs-lookup"><span data-stu-id="3c33c-219">The record is discarded.</span></span>|  
||<span data-ttu-id="3c33c-220">**[エラー処理の制限]**。</span><span class="sxs-lookup"><span data-stu-id="3c33c-220">**Processing error limit**.</span></span> <span data-ttu-id="3c33c-221">次のいずれかのオプションを選択して、処理されるエラー数を制御します。</span><span class="sxs-lookup"><span data-stu-id="3c33c-221">Controls the number of errors processed by selecting one of these options:</span></span><br /><br /> <span data-ttu-id="3c33c-222">**[エラー数を無視する]**。</span><span class="sxs-lookup"><span data-stu-id="3c33c-222">**Ignore errors count**.</span></span> <span data-ttu-id="3c33c-223">これにより、エラー数に関係なく、処理を続行できます。</span><span class="sxs-lookup"><span data-stu-id="3c33c-223">This will enable processing to continue regardless of the number of errors.</span></span> <br /><span data-ttu-id="3c33c-224">**[エラー時に停止**する。</span><span class="sxs-lookup"><span data-stu-id="3c33c-224">**Stop on error**.</span></span> <span data-ttu-id="3c33c-225">このオプションでは、さらに 2 つのオプションを設定します。</span><span class="sxs-lookup"><span data-stu-id="3c33c-225">With this option, you control two additional settings.</span></span> <span data-ttu-id="3c33c-226">**[エラー数]** では、特定の数のエラーに処理を制限できます。</span><span class="sxs-lookup"><span data-stu-id="3c33c-226">**Number of errors** lets you limit processing to the occurrence of a specific number of errors.</span></span> <span data-ttu-id="3c33c-227">**[エラー時のアクション]** では、 **[エラー数]** に到達したときのアクションを決定できます。</span><span class="sxs-lookup"><span data-stu-id="3c33c-227">**On error action** lets you determine the action when **Number of errors** is reached.</span></span> <span data-ttu-id="3c33c-228">**[処理の停止]**(処理ジョブが失敗した場合にすべての変更がロールバックされます) や **[ログ記録の停止]**(エラーをログに記録せずに処理を続行できます) を選択できます。</span><span class="sxs-lookup"><span data-stu-id="3c33c-228">You can select **Stop processing**, which causes the processing job to fail and roll back any changes, or **Stop logging**, which enables processing to continue without logging errors.</span></span> <span data-ttu-id="3c33c-229">**[エラー時に停止する]** は既定の設定で、 **[エラー数]** が **0** に設定され、 **[エラー時のアクション]** が **[処理の停止]** に設定されています。</span><span class="sxs-lookup"><span data-stu-id="3c33c-229">**Stop on error** is the default setting with **Number of errors** set to **0** and **On error action** set to **Stop processing**.</span></span>|  
||<span data-ttu-id="3c33c-230">[詳細なエラー条件]。</span><span class="sxs-lookup"><span data-stu-id="3c33c-230">Specific error conditions.</span></span> <span data-ttu-id="3c33c-231">次のオプションを設定して、詳細なエラー処理の動作を制御できます。</span><span class="sxs-lookup"><span data-stu-id="3c33c-231">You can set the following options to control specific error-handling behavior:</span></span><br /><br /> <span data-ttu-id="3c33c-232">**キーが見つかりません**。</span><span class="sxs-lookup"><span data-stu-id="3c33c-232">**Key not found**.</span></span> <span data-ttu-id="3c33c-233">キー値がパーティションに存在しても対応するディメンションに存在しない場合に使用されます。</span><span class="sxs-lookup"><span data-stu-id="3c33c-233">Occurs when a key value exists in a partition but does not exist in the corresponding dimension.</span></span> <span data-ttu-id="3c33c-234">既定の設定は **[報告して続行する]** です。</span><span class="sxs-lookup"><span data-stu-id="3c33c-234">The default setting is **Report and continue**.</span></span> <span data-ttu-id="3c33c-235">他に、 **[エラーを無視する]** および **[報告して停止する]** という設定もあります。</span><span class="sxs-lookup"><span data-stu-id="3c33c-235">Other settings are **Ignore error** and **Report and stop**.</span></span><br /><br /> <span data-ttu-id="3c33c-236">**[重複キー]**。</span><span class="sxs-lookup"><span data-stu-id="3c33c-236">**Duplicate key**.</span></span> <span data-ttu-id="3c33c-237">ディメンションに複数のキー値が存在する場合に使用されます。</span><span class="sxs-lookup"><span data-stu-id="3c33c-237">Occurs when more than one key value exists in a dimension.</span></span> <span data-ttu-id="3c33c-238">既定の設定は **[エラーを無視する]** です。</span><span class="sxs-lookup"><span data-stu-id="3c33c-238">The default setting is **Ignore error**.</span></span> <span data-ttu-id="3c33c-239">他に、 **[報告して続行する]** および **[報告して停止する]** という設定もあります。</span><span class="sxs-lookup"><span data-stu-id="3c33c-239">Other settings are **Report and continue** and **Report and stop**.</span></span><br /><br /> <span data-ttu-id="3c33c-240">**[不明な種類に変換された NULL キー]**。</span><span class="sxs-lookup"><span data-stu-id="3c33c-240">**Null key converted to unknown**.</span></span> <span data-ttu-id="3c33c-241">キー値が NULL で、 **[キー エラー アクション]** が **[不明な種類に変換]** に設定されている場合に使用されます。</span><span class="sxs-lookup"><span data-stu-id="3c33c-241">Occurs when a key value is null and the **Key error action** is set to **Convert to unknown**.</span></span> <span data-ttu-id="3c33c-242">既定の設定は **[エラーを無視する]** です。</span><span class="sxs-lookup"><span data-stu-id="3c33c-242">The default setting is **Ignore error**.</span></span> <span data-ttu-id="3c33c-243">他に、 **[報告して続行する]** および **[報告して停止する]** という設定もあります。</span><span class="sxs-lookup"><span data-stu-id="3c33c-243">Other settings are **Report and continue** and **Report and stop**.</span></span><br /><br /> <span data-ttu-id="3c33c-244">**[許可されていない NULL キー]**。</span><span class="sxs-lookup"><span data-stu-id="3c33c-244">**Null key not allowed**.</span></span> <span data-ttu-id="3c33c-245">**[キー エラー アクション]** が **[レコードの破棄]** に設定されている場合に使用されます。</span><span class="sxs-lookup"><span data-stu-id="3c33c-245">Occurs when **Key error action** is set to **Discard record**.</span></span> <span data-ttu-id="3c33c-246">既定の設定は **[報告して続行する]** です。</span><span class="sxs-lookup"><span data-stu-id="3c33c-246">The default setting is **Report and continue**.</span></span> <span data-ttu-id="3c33c-247">他に、 **[エラーを無視する]** および **[報告して停止する]** という設定もあります。</span><span class="sxs-lookup"><span data-stu-id="3c33c-247">Other settings are **Ignore error** and **Report and stop**.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3c33c-248">参照</span><span class="sxs-lookup"><span data-stu-id="3c33c-248">See Also</span></span>  
 [<span data-ttu-id="3c33c-249">多次元モデルのオブジェクト処理</span><span class="sxs-lookup"><span data-stu-id="3c33c-249">Multidimensional Model Object Processing</span></span>](processing-a-multidimensional-model-analysis-services.md)  
  
  