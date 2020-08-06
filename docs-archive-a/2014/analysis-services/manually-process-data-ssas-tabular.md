---
title: データの手動処理 (SSAS テーブル) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.datarefreshprogressdb.f1
ms.assetid: 0918c04c-c1e6-45b4-acfa-96fa578e684b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 51bdb1b9535685db4fc35dbdd791e6b4d9bed1b6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643589"
---
# <a name="manually-process-data-ssas-tabular"></a><span data-ttu-id="b6a75-102">データの手動処理 (SSAS テーブル)</span><span class="sxs-lookup"><span data-stu-id="b6a75-102">Manually Process Data (SSAS Tabular)</span></span>
  <span data-ttu-id="b6a75-103">このトピックでは、 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]のワークスペースのデータを手動で処理する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b6a75-103">This topic describes how to manually process workspace data in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="b6a75-104">外部データを使用するテーブル モデルを作成すると、[処理] コマンドを使用してデータを手動で更新できます。</span><span class="sxs-lookup"><span data-stu-id="b6a75-104">When you author a tabular model that uses external data, you can manually refresh the data by using the Process command.</span></span> <span data-ttu-id="b6a75-105">1 つのテーブル、モデル内のすべてのテーブル、または 1 つ以上のパーティションを処理できます。</span><span class="sxs-lookup"><span data-stu-id="b6a75-105">You can process a single table, all tables in the model, or one or more partitions.</span></span> <span data-ttu-id="b6a75-106">データを処理するときには、データの再計算も必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="b6a75-106">Whenever you process data, you may also need to recalculate data.</span></span>  <span data-ttu-id="b6a75-107">データの処理とは、外部ソースから最新のデータを取得することです。</span><span class="sxs-lookup"><span data-stu-id="b6a75-107">Processing data means getting the latest data from external sources.</span></span> <span data-ttu-id="b6a75-108">再計算とは、データを使用する数式の結果を更新することです。</span><span class="sxs-lookup"><span data-stu-id="b6a75-108">Recalculating means updating the result of any formula that uses the data.</span></span>  
  
 <span data-ttu-id="b6a75-109">このトピックのセクション:</span><span class="sxs-lookup"><span data-stu-id="b6a75-109">Sections in this topic:</span></span>  
  
-   [<span data-ttu-id="b6a75-110">データの手動処理</span><span class="sxs-lookup"><span data-stu-id="b6a75-110">Manually Process Data</span></span>](#bkmk_mahually_process)  
  
-   [<span data-ttu-id="b6a75-111">データ処理の進行状況</span><span class="sxs-lookup"><span data-stu-id="b6a75-111">Data Process Progress</span></span>](#bkmk_data_process_progress)  
  
##  <a name="manually-process-data"></a><a name="bkmk_mahually_process"></a><span data-ttu-id="b6a75-112">データを手動で処理する</span><span class="sxs-lookup"><span data-stu-id="b6a75-112">Manually Process Data</span></span>  
  
#### <a name="to-process-data-for-a-single-table-or-all-tables-in-a-model"></a><span data-ttu-id="b6a75-113">モデル内の 1 つまたはすべてのテーブルのデータを処理するには</span><span class="sxs-lookup"><span data-stu-id="b6a75-113">To process data for a single table or all tables in a model</span></span>  
  
1.  <span data-ttu-id="b6a75-114">モデル デザイナーで、処理するテーブルをクリックします。</span><span class="sxs-lookup"><span data-stu-id="b6a75-114">In the model designer, click the table you want to process.</span></span>  
  
2.  <span data-ttu-id="b6a75-115">**[モデル]** メニュー、 **[処理]** の順にクリックし、 **[処理]** または **[すべて処理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b6a75-115">Click on the **Model** menu, then click **Process**, and then click **Process** or **Process All**.</span></span>  
  
#### <a name="to-process-data-for-all-tables-using-the-same-connection"></a><span data-ttu-id="b6a75-116">同じ接続を使用するすべてのテーブルのデータを処理するには</span><span class="sxs-lookup"><span data-stu-id="b6a75-116">To process data for all tables using the same connection</span></span>  
  
1.  <span data-ttu-id="b6a75-117">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]で **[モデル]** メニューをクリックし、 **[既存の接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b6a75-117">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], click on the **Model** menu, and then click **Existing Connections**.</span></span>  
  
2.  <span data-ttu-id="b6a75-118">**[既存の接続]** ダイアログ ボックスで接続を選択し、 **[処理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b6a75-118">In the **Existing Connections** dialog box, select a connection, and then click **Process**.</span></span>  
  
#### <a name="to-process-data-for-one-or-more-partitions"></a><span data-ttu-id="b6a75-119">1 つ以上のパーティションのデータを処理するには</span><span class="sxs-lookup"><span data-stu-id="b6a75-119">To process data for one or more partitions</span></span>  
  
1.  <span data-ttu-id="b6a75-120">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]の **[モデル]** メニューをクリックし、 **[処理]** をポイントして **[パーティションの処理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b6a75-120">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], click the **Model** menu, then point to **Process**, and then click **Process Partitions**.</span></span>  
  
2.  <span data-ttu-id="b6a75-121">**[パーティションの処理]** ダイアログ ボックスの **[モード]** で、次のプロセス モードのいずれかを選択します。</span><span class="sxs-lookup"><span data-stu-id="b6a75-121">In the **Process Partitions** dialog box, in **Mode**, select one of the following process modes:</span></span>  
  
    |<span data-ttu-id="b6a75-122">モード</span><span class="sxs-lookup"><span data-stu-id="b6a75-122">Mode</span></span>|<span data-ttu-id="b6a75-123">説明</span><span class="sxs-lookup"><span data-stu-id="b6a75-123">Description</span></span>|  
    |----------|-----------------|  
    |<span data-ttu-id="b6a75-124">**既定の処理**</span><span class="sxs-lookup"><span data-stu-id="b6a75-124">**Process Default**</span></span>|<span data-ttu-id="b6a75-125">パーティション オブジェクトの処理状態を検出して、未処理または部分的に処理されたパーティション オブジェクトを完全に処理された状態にするために必要な処理を実行します。</span><span class="sxs-lookup"><span data-stu-id="b6a75-125">Detects the process state of a partition object, and performs processing necessary to deliver unprocessed or partially processed partition objects to a fully processed state.</span></span> <span data-ttu-id="b6a75-126">空のテーブルとパーティションのデータが読み込まれ、階層、計算列、およびリレーションシップが構築または再構築されます。</span><span class="sxs-lookup"><span data-stu-id="b6a75-126">Data for empty tables and partitions is loaded; hierarchies, calculated columns, and relationships are built or rebuilt.</span></span>|  
    |<span data-ttu-id="b6a75-127">**完全処理**</span><span class="sxs-lookup"><span data-stu-id="b6a75-127">**Process Full**</span></span>|<span data-ttu-id="b6a75-128">パーティション オブジェクトとそこに含まれているすべてのオブジェクトを処理します。</span><span class="sxs-lookup"><span data-stu-id="b6a75-128">Processes a partition object and all the objects that it contains.</span></span> <span data-ttu-id="b6a75-129">既に処理されたオブジェクトに対して完全処理を実行すると、そのオブジェクト内のすべてのデータが [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] によって削除されてから、オブジェクトが処理されます。</span><span class="sxs-lookup"><span data-stu-id="b6a75-129">When Process Full is run for an object that has already been processed, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] drops all data in the object, and then processes the object.</span></span> <span data-ttu-id="b6a75-130">この種の処理は、構造上の変更をオブジェクトに加えた場合に必要となります。</span><span class="sxs-lookup"><span data-stu-id="b6a75-130">This kind of processing is required when a structural change has been made to an object.</span></span>|  
    |<span data-ttu-id="b6a75-131">**データの処理**</span><span class="sxs-lookup"><span data-stu-id="b6a75-131">**Process Data**</span></span>|<span data-ttu-id="b6a75-132">階層またはリレーションシップを再構築したり、計算列とメジャーを再計算したりせずに、パーティションまたはテーブルにデータを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="b6a75-132">Load data into a partition or a table without rebuilding hierarchies or relationships or recalculating calculated columns and measures.</span></span>|  
    |<span data-ttu-id="b6a75-133">**消去の処理**</span><span class="sxs-lookup"><span data-stu-id="b6a75-133">**Process Clear**</span></span>|<span data-ttu-id="b6a75-134">パーティションからすべてのデータを削除します。</span><span class="sxs-lookup"><span data-stu-id="b6a75-134">Removes all data from a partition.</span></span>|  
    |<span data-ttu-id="b6a75-135">**追加の処理**</span><span class="sxs-lookup"><span data-stu-id="b6a75-135">**Process Add**</span></span>|<span data-ttu-id="b6a75-136">パーティションを新しいデータで増分更新します。</span><span class="sxs-lookup"><span data-stu-id="b6a75-136">Incrementally update partition with new data.</span></span>|  
  
3.  <span data-ttu-id="b6a75-137">[パーティション] リストで処理するパーティションを選択し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b6a75-137">In the partitions list, select the partitions you want to process, and then click **OK**.</span></span>  
  
##  <a name="data-process-progress"></a><a name="bkmk_data_process_progress"></a><span data-ttu-id="b6a75-138">データ処理の進行状況</span><span class="sxs-lookup"><span data-stu-id="b6a75-138">Data Process Progress</span></span>  
 <span data-ttu-id="b6a75-139">**[データ処理の進行状況]** ダイアログ ボックスを使用すると、外部ソースからモデルにインポートしたデータの処理を監視できます。</span><span class="sxs-lookup"><span data-stu-id="b6a75-139">The **Data Process Progress** dialog box enables you to monitor the processing of data that you have imported into the model from an external source.</span></span> <span data-ttu-id="b6a75-140">このダイアログ ボックスにアクセスするには、 **[モデル]** メニューの **[パーティションの処理]**、 **[テーブルの処理]** 、または **[すべて処理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b6a75-140">To access this dialog box, click on the **Model** menu, and then click **Process Partitions**, **Process Table** or **Process All**.</span></span>  
  
 <span data-ttu-id="b6a75-141">**状態**</span><span class="sxs-lookup"><span data-stu-id="b6a75-141">**Status**</span></span>  
 <span data-ttu-id="b6a75-142">処理の操作が正常に行われたかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="b6a75-142">Indicates whether the process operation was successful or not.</span></span>  
  
 <span data-ttu-id="b6a75-143">**詳細**</span><span class="sxs-lookup"><span data-stu-id="b6a75-143">**Details**</span></span>  
 <span data-ttu-id="b6a75-144">インポートされたテーブルやビュー、インポートされた行の数を一覧表示し、問題のあるレポートへのリンクを示します。</span><span class="sxs-lookup"><span data-stu-id="b6a75-144">Lists the tables and views that were imported, the number of rows that were imported, and provides a link to a report of any issues.</span></span>  
  
 <span data-ttu-id="b6a75-145">**[更新の停止]**</span><span class="sxs-lookup"><span data-stu-id="b6a75-145">**Stop Refresh**</span></span>  
 <span data-ttu-id="b6a75-146">処理の操作を停止します。</span><span class="sxs-lookup"><span data-stu-id="b6a75-146">Click to halt the process operation.</span></span> <span data-ttu-id="b6a75-147">このオプションは、操作に時間がかかりすぎる場合や、エラーが多すぎる場合に有効です。</span><span class="sxs-lookup"><span data-stu-id="b6a75-147">This option is useful if the operation is taking too long, or if there are too many errors.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6a75-148">参照</span><span class="sxs-lookup"><span data-stu-id="b6a75-148">See Also</span></span>  
 <span data-ttu-id="b6a75-149">[SSAS 表形式&#41;&#40;データを処理する](process-data-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="b6a75-149">[Process Data &#40;SSAS Tabular&#41;](process-data-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="b6a75-150">データの処理のトラブルシューティング &#40;SSAS テーブル&#41;</span><span class="sxs-lookup"><span data-stu-id="b6a75-150">Troubleshoot Process Data &#40;SSAS Tabular&#41;</span></span>](troubleshoot-process-data-ssas-tabular.md)  
  
  
