---
title: データベース、テーブル、またはパーティションの処理 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- SQL12.ASVS.SSMS.PARTITIONS.PROCESSINGOPTIONS.IMBI.F1
ms.assetid: 307d69c3-cabb-4dfa-b90c-9852492c1213
author: minewiskan
ms.author: owend
ms.openlocfilehash: b5d3840be43798536f1bb517007a7974a1e08728
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712445"
---
# <a name="process-database-table-or-partition"></a><span data-ttu-id="25528-102">データベース、テーブル、またはパーティションの処理</span><span class="sxs-lookup"><span data-stu-id="25528-102">Process Database, Table, or Partition</span></span>
  <span data-ttu-id="25528-103">このトピックのタスクでは、の [ \*\* \<object> 処理\*\*] ダイアログボックスを使用して、テーブルモデルデータベース、テーブル、またはパーティションを手動で処理する方法について説明し [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="25528-103">The tasks in this topic describe how to process a tabular model database, table, or partitions manually by using the **Process \<object>** dialog box in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="25528-104">テーブル モデルの処理の詳細については、[「データの処理 (SSAS テーブル)」](../process-data-ssas-tabular.md) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="25528-104">For more information about tabular model processing, see [Process Data &#40;SSAS Tabular&#41;](../process-data-ssas-tabular.md).</span></span>  
  
##  <a name="tasks"></a><a name="bkmk_process_tasks"></a> <span data-ttu-id="25528-105">タスク</span><span class="sxs-lookup"><span data-stu-id="25528-105">Tasks</span></span>  
  
###  <a name="to-process-a-database"></a><a name="bkmk_process_db"></a><span data-ttu-id="25528-106">データベースを処理するには</span><span class="sxs-lookup"><span data-stu-id="25528-106">To process a database</span></span>  
  
1.  <span data-ttu-id="25528-107">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で処理対象のデータベースを右クリックし、 **[データベースの処理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="25528-107">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], right-click on the database you want to process, and then click **Process Database**.</span></span>  
  
2.  <span data-ttu-id="25528-108">**[データベースの処理]** ダイアログ ボックスの **[モード]** ボックスの一覧で、次のプロセス モードのいずれかを選択します。</span><span class="sxs-lookup"><span data-stu-id="25528-108">In the **Process Database** dialog box, in the **Mode** listbox, select one of the following process modes:</span></span>  
  
    |<span data-ttu-id="25528-109">モード</span><span class="sxs-lookup"><span data-stu-id="25528-109">Mode</span></span>|<span data-ttu-id="25528-110">説明</span><span class="sxs-lookup"><span data-stu-id="25528-110">Description</span></span>|  
    |----------|-----------------|  
    |<span data-ttu-id="25528-111">**既定の処理**</span><span class="sxs-lookup"><span data-stu-id="25528-111">**Process Default**</span></span>|<span data-ttu-id="25528-112">データベース オブジェクトの処理状態を検出し、処理されていないオブジェクトや部分的に処理されたオブジェクトを完全処理状態にするために必要な処理を行います。</span><span class="sxs-lookup"><span data-stu-id="25528-112">Detects the process state of database objects, and performs processing necessary to deliver unprocessed or partially processed objects to a fully processed state.</span></span> <span data-ttu-id="25528-113">空のテーブルとパーティションのデータが読み込まれ、階層、計算列、およびリレーションシップが構築または再構築 (再計算) されます。</span><span class="sxs-lookup"><span data-stu-id="25528-113">Data for empty tables and partitions is loaded; hierarchies, calculated columns, and relationships are built or rebuilt (recalculated).</span></span>|  
    |<span data-ttu-id="25528-114">**完全処理**</span><span class="sxs-lookup"><span data-stu-id="25528-114">**Process Full**</span></span>|<span data-ttu-id="25528-115">データベースとそのデータベースに含まれるすべてのオブジェクトを処理します。</span><span class="sxs-lookup"><span data-stu-id="25528-115">Processes a database and all the objects that it contains.</span></span> <span data-ttu-id="25528-116">既に処理されたオブジェクトに対して完全処理を実行すると、そのオブジェクト内のすべてのデータが [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] によって削除されてから、オブジェクトが処理されます。</span><span class="sxs-lookup"><span data-stu-id="25528-116">When Process Full is run for an object that has already been processed, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] drops all data in the object, and then processes the object.</span></span> <span data-ttu-id="25528-117">この種の処理は、構造上の変更をオブジェクトに加えた場合に必要となります。</span><span class="sxs-lookup"><span data-stu-id="25528-117">This kind of processing is required when a structural change has been made to an object.</span></span> <span data-ttu-id="25528-118">このオプションは最も多くのリソースを必要とします。</span><span class="sxs-lookup"><span data-stu-id="25528-118">This option requires the most resources.</span></span>|  
    |<span data-ttu-id="25528-119">**消去の処理**</span><span class="sxs-lookup"><span data-stu-id="25528-119">**Process Clear**</span></span>|<span data-ttu-id="25528-120">データベース オブジェクトからすべてのデータを削除します。</span><span class="sxs-lookup"><span data-stu-id="25528-120">Removes all data from database objects.</span></span>|  
    |<span data-ttu-id="25528-121">**再計算の処理**</span><span class="sxs-lookup"><span data-stu-id="25528-121">**Process Recalc**</span></span>|<span data-ttu-id="25528-122">階層、リレーションシップ、および計算列を更新して再計算します。</span><span class="sxs-lookup"><span data-stu-id="25528-122">Updates and recalculates hierarchies, relationships, and calculated columns.</span></span>|  
  
3.  <span data-ttu-id="25528-123">**[処理]** チェックボックス列で、選択したモードで処理するパーティションを選択し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="25528-123">In the **Process** checkbox column, select the partitions you want to process with the selected mode, and then click **Ok**.</span></span>  
  
###  <a name="to-process-a-table"></a><a name="bkmk_process_table"></a><span data-ttu-id="25528-124">テーブルを処理するには</span><span class="sxs-lookup"><span data-stu-id="25528-124">To process a table</span></span>  
  
1.  <span data-ttu-id="25528-125">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、処理対象のテーブルを含むテーブル モデル データベースの **[テーブル]** ノードを展開し、処理対象のテーブルを右クリックしてから **[テーブルの処理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="25528-125">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], in the tabular model database which contains the table you want to process, expand the **Tables** node, then right-click on the table you want to process, and then click **Process Table**.</span></span>  
  
2.  <span data-ttu-id="25528-126">**[テーブルの処理]** ダイアログ ボックスの **[モード]** ボックスの一覧で、次のプロセス モードのいずれかを選択します。</span><span class="sxs-lookup"><span data-stu-id="25528-126">In the **Process Table** dialog box, in the **Mode** listbox, select one of the following process modes:</span></span>  
  
    |<span data-ttu-id="25528-127">モード</span><span class="sxs-lookup"><span data-stu-id="25528-127">Mode</span></span>|<span data-ttu-id="25528-128">説明</span><span class="sxs-lookup"><span data-stu-id="25528-128">Description</span></span>|  
    |----------|-----------------|  
    |<span data-ttu-id="25528-129">**既定の処理**</span><span class="sxs-lookup"><span data-stu-id="25528-129">**Process Default**</span></span>|<span data-ttu-id="25528-130">テーブル オブジェクトの処理状態を検出し、処理されていないオブジェクトや部分的に処理されたオブジェクトを完全処理状態にするために必要な処理を行います。</span><span class="sxs-lookup"><span data-stu-id="25528-130">Detects the process state of a table object, and performs processing necessary to deliver unprocessed or partially processed objects to a fully processed state.</span></span> <span data-ttu-id="25528-131">空のテーブルとパーティションのデータが読み込まれ、階層、計算列、およびリレーションシップが構築または再構築 (再計算) されます。</span><span class="sxs-lookup"><span data-stu-id="25528-131">Data for empty tables and partitions is loaded; hierarchies, calculated columns, and relationships are built or rebuilt (recalculated).</span></span>|  
    |<span data-ttu-id="25528-132">**完全処理**</span><span class="sxs-lookup"><span data-stu-id="25528-132">**Process Full**</span></span>|<span data-ttu-id="25528-133">テーブル オブジェクトとそこに含まれているすべてのオブジェクトを処理します。</span><span class="sxs-lookup"><span data-stu-id="25528-133">Processes a table object and all the objects that it contains.</span></span> <span data-ttu-id="25528-134">既に処理されたオブジェクトに対して完全処理を実行すると、そのオブジェクト内のすべてのデータが [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] によって削除されてから、オブジェクトが処理されます。</span><span class="sxs-lookup"><span data-stu-id="25528-134">When Process Full is run for an object that has already been processed, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] drops all data in the object, and then processes the object.</span></span> <span data-ttu-id="25528-135">この種の処理は、構造上の変更をオブジェクトに加えた場合に必要となります。</span><span class="sxs-lookup"><span data-stu-id="25528-135">This kind of processing is required when a structural change has been made to an object.</span></span> <span data-ttu-id="25528-136">このオプションは最も多くのリソースを必要とします。</span><span class="sxs-lookup"><span data-stu-id="25528-136">This option requires the most resources.</span></span>|  
    |<span data-ttu-id="25528-137">**データの処理**</span><span class="sxs-lookup"><span data-stu-id="25528-137">**Process Data**</span></span>|<span data-ttu-id="25528-138">階層またはリレーションシップを再構築したり、計算列とメジャーを再計算したりせずに、テーブルにデータを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="25528-138">Load data into a table without rebuilding hierarchies or relationships or recalculating calculated columns and measures.</span></span>|  
    |<span data-ttu-id="25528-139">**消去の処理**</span><span class="sxs-lookup"><span data-stu-id="25528-139">**Process Clear**</span></span>|<span data-ttu-id="25528-140">テーブルおよびテーブル パーティションからすべてのデータを削除します。</span><span class="sxs-lookup"><span data-stu-id="25528-140">Removes all data from a table and any table partitions.</span></span>|  
    |<span data-ttu-id="25528-141">**デフラグの処理**</span><span class="sxs-lookup"><span data-stu-id="25528-141">**Process Defrag**</span></span>|<span data-ttu-id="25528-142">補助テーブルのインデックスをデフラグします。</span><span class="sxs-lookup"><span data-stu-id="25528-142">Defragments the auxiliary table indexes.</span></span>|  
  
3.  <span data-ttu-id="25528-143">テーブルのチェックボックス列でテーブルを確認し、必要に応じて処理対象の追加のテーブルを選択し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="25528-143">In the table checkbox column, verify the table and optionally select any additional tables you want to process, and then click **Ok**.</span></span>  
  
###  <a name="to-process-one-or-more-partitions"></a><a name="bkmk_process_partition"></a><span data-ttu-id="25528-144">1つ以上のパーティションを処理するには</span><span class="sxs-lookup"><span data-stu-id="25528-144">To process one or more partitions</span></span>  
  
1.  <span data-ttu-id="25528-145">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、処理対象のパーティションが存在するテーブルを右クリックして **[パーティション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="25528-145">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], right-click on the table that has the partitions you want to process, and then click **Partitions**.</span></span>  
  
2.  <span data-ttu-id="25528-146">**[パーティション]** ダイアログ ボックスの **[パーティション]** で、[処理] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="25528-146">In the **Partitions** dialog box, in **Partitions**, click the Process button.</span></span>  
  
3.  <span data-ttu-id="25528-147">**[パーティションの処理]** ダイアログ ボックスの **[モード]** ボックスの一覧で、次のプロセス モードのいずれかを選択します。</span><span class="sxs-lookup"><span data-stu-id="25528-147">In the **Process Partition** dialog box, in the **Mode** listbox, select one of the following process modes:</span></span>  
  
    |<span data-ttu-id="25528-148">モード</span><span class="sxs-lookup"><span data-stu-id="25528-148">Mode</span></span>|<span data-ttu-id="25528-149">説明</span><span class="sxs-lookup"><span data-stu-id="25528-149">Description</span></span>|  
    |----------|-----------------|  
    |<span data-ttu-id="25528-150">**既定の処理**</span><span class="sxs-lookup"><span data-stu-id="25528-150">**Process Default**</span></span>|<span data-ttu-id="25528-151">パーティション オブジェクトの処理状態を検出して、未処理または部分的に処理されたパーティション オブジェクトを完全に処理された状態にするために必要な処理を実行します。</span><span class="sxs-lookup"><span data-stu-id="25528-151">Detects the process state of a partition object, and performs processing necessary to deliver unprocessed or partially processed partition objects to a fully processed state.</span></span> <span data-ttu-id="25528-152">空のテーブルとパーティションのデータが読み込まれ、階層、計算列、およびリレーションシップが構築または再構築 (再計算) されます。</span><span class="sxs-lookup"><span data-stu-id="25528-152">Data for empty tables and partitions is loaded; hierarchies, calculated columns, and relationships are built or rebuilt (recalculated).</span></span>|  
    |<span data-ttu-id="25528-153">**完全処理**</span><span class="sxs-lookup"><span data-stu-id="25528-153">**Process Full**</span></span>|<span data-ttu-id="25528-154">パーティション オブジェクトとそこに含まれているすべてのオブジェクトを処理します。</span><span class="sxs-lookup"><span data-stu-id="25528-154">Processes a partition object and all the objects that it contains.</span></span> <span data-ttu-id="25528-155">既に処理されたオブジェクトに対して完全処理を実行すると、そのオブジェクト内のすべてのデータが [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] によって削除されてから、オブジェクトが処理されます。</span><span class="sxs-lookup"><span data-stu-id="25528-155">When Process Full is run for an object that has already been processed, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] drops all data in the object, and then processes the object.</span></span> <span data-ttu-id="25528-156">この種の処理は、構造上の変更をオブジェクトに加えた場合に必要となります。</span><span class="sxs-lookup"><span data-stu-id="25528-156">This kind of processing is required when a structural change has been made to an object.</span></span>|  
    |<span data-ttu-id="25528-157">**データの処理**</span><span class="sxs-lookup"><span data-stu-id="25528-157">**Process Data**</span></span>|<span data-ttu-id="25528-158">階層またはリレーションシップを再構築したり、計算列とメジャーを再計算したりせずに、パーティションまたはテーブルにデータを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="25528-158">Load data into a partition or a table without rebuilding hierarchies or relationships or recalculating calculated columns and measures.</span></span>|  
    |<span data-ttu-id="25528-159">**消去の処理**</span><span class="sxs-lookup"><span data-stu-id="25528-159">**Process Clear**</span></span>|<span data-ttu-id="25528-160">パーティションからすべてのデータを削除します。</span><span class="sxs-lookup"><span data-stu-id="25528-160">Removes all data from a partition.</span></span>|  
    |<span data-ttu-id="25528-161">**追加の処理**</span><span class="sxs-lookup"><span data-stu-id="25528-161">**Process Add**</span></span>|<span data-ttu-id="25528-162">パーティションを新しいデータで増分更新します。</span><span class="sxs-lookup"><span data-stu-id="25528-162">Incrementally update partition with new data.</span></span>|  
  
4.  <span data-ttu-id="25528-163">**[処理]** チェックボックス列で、選択したモードで処理するパーティションを選択し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="25528-163">In the **Process** checkbox column, select the partitions you want to process with the selected mode, and then click **Ok**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25528-164">参照</span><span class="sxs-lookup"><span data-stu-id="25528-164">See Also</span></span>  
 <span data-ttu-id="25528-165">[SSAS 表形式&#41;&#40;テーブルモデルパーティション](tabular-model-partitions-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="25528-165">[Tabular Model Partitions &#40;SSAS Tabular&#41;](tabular-model-partitions-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="25528-166">テーブル モデル パーティションの作成および管理 (SSAS テーブル)</span><span class="sxs-lookup"><span data-stu-id="25528-166">Create and Manage Tabular Model Partitions &#40;SSAS Tabular&#41;</span></span>](create-and-manage-tabular-model-partitions-ssas-tabular.md)  
  
  
