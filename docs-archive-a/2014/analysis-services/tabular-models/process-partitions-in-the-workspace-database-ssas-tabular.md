---
title: ワークスペースデータベースのパーティションの処理 (SSAS テーブル)Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 3a369705-43fa-4961-9045-32e06fbdde33
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4a996e90b30794882535327ea3192d7e72818422
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712441"
---
# <a name="process-partitions-in-the-workspace-database-ssas-tabular"></a><span data-ttu-id="60bfc-102">ワークスペースデータベースのパーティションの処理 (SSAS テーブル)</span><span class="sxs-lookup"><span data-stu-id="60bfc-102">Process Partitions in the Workspace Database (SSAS Tabular)</span></span>
  <span data-ttu-id="60bfc-103">パーティションは、テーブルを論理的な部分に分割します。</span><span class="sxs-lookup"><span data-stu-id="60bfc-103">Partitions divide a table into logical parts.</span></span> <span data-ttu-id="60bfc-104">各パーティションは、他のパーティションとは個別に処理 (更新) できます。</span><span class="sxs-lookup"><span data-stu-id="60bfc-104">Each partition can then be processed (Refreshed) independent of other partitions.</span></span> <span data-ttu-id="60bfc-105">このトピックのタスクでは、 **で** [パーティションの処理] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]ダイアログ ボックスを使用して、モデル ワークスペース データベースでパーティションを処理する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="60bfc-105">The tasks in this topic describe how to process partitions in the model workspace database by using the **Process Partitions** dialog box in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="60bfc-106">別の Analysis Services インスタンスにモデルが配置された後、データベース管理者は、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を使用するか、スクリプトによって、または IS パッケージを使用して (配置済みの) モデルでパーティションを作成し管理できます。</span><span class="sxs-lookup"><span data-stu-id="60bfc-106">After a model has been deployed to another Analysis Services instance, database administrators can create and manage partitions in the (deployed) model by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], by script, or by using an IS package.</span></span> <span data-ttu-id="60bfc-107">詳細については、「[テーブル モデル パーティションの作成および管理 (SSAS テーブル)](partitions-ssas-tabular.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="60bfc-107">For more information, see [Create and Manage Tabular Model Partitions &#40;SSAS Tabular&#41;](partitions-ssas-tabular.md).</span></span>  
  
###  <a name="to-process-a-partition"></a><a name="bkmk_create_new"></a> <span data-ttu-id="60bfc-108">パーティションを処理するには</span><span class="sxs-lookup"><span data-stu-id="60bfc-108">To process a partition</span></span>  
  
1.  <span data-ttu-id="60bfc-109">[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]の **[モデル]** メニューをクリックし、 **[処理]** ([更新])、 **[パーティションの処理]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="60bfc-109">In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], click the **Model** menu, and then click **Process** (Refresh), and then click **Process Partitions**.</span></span>  
  
2.  <span data-ttu-id="60bfc-110">**[モード]** ボックスの一覧で、次のプロセス モードのいずれかを選択します。</span><span class="sxs-lookup"><span data-stu-id="60bfc-110">In the **Mode** listbox, select one of the following process modes:</span></span>  
  
    |<span data-ttu-id="60bfc-111">モード</span><span class="sxs-lookup"><span data-stu-id="60bfc-111">Mode</span></span>|<span data-ttu-id="60bfc-112">説明</span><span class="sxs-lookup"><span data-stu-id="60bfc-112">Description</span></span>|  
    |----------|-----------------|  
    |<span data-ttu-id="60bfc-113">**既定の処理**</span><span class="sxs-lookup"><span data-stu-id="60bfc-113">**Process Default**</span></span>|<span data-ttu-id="60bfc-114">パーティション オブジェクトの処理状態を検出して、未処理または部分的に処理されたパーティション オブジェクトを完全に処理された状態にするために必要な処理を実行します。</span><span class="sxs-lookup"><span data-stu-id="60bfc-114">Detects the process state of a partition object, and performs processing necessary to deliver unprocessed or partially processed partition objects to a fully processed state.</span></span> <span data-ttu-id="60bfc-115">空のテーブルとパーティションのデータが読み込まれ、階層、計算列、およびリレーションシップが構築または再構築されます。</span><span class="sxs-lookup"><span data-stu-id="60bfc-115">Data for empty tables and partitions is loaded; hierarchies, calculated columns, and relationships are built or rebuilt.</span></span>|  
    |<span data-ttu-id="60bfc-116">**完全処理**</span><span class="sxs-lookup"><span data-stu-id="60bfc-116">**Process Full**</span></span>|<span data-ttu-id="60bfc-117">パーティション オブジェクトとそこに含まれているすべてのオブジェクトを処理します。</span><span class="sxs-lookup"><span data-stu-id="60bfc-117">Processes a partition object and all the objects that it contains.</span></span> <span data-ttu-id="60bfc-118">既に処理されたオブジェクトに対して完全処理を実行すると、そのオブジェクト内のすべてのデータが [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] によって削除されてから、オブジェクトが処理されます。</span><span class="sxs-lookup"><span data-stu-id="60bfc-118">When Process Full is run for an object that has already been processed, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] drops all data in the object, and then processes the object.</span></span> <span data-ttu-id="60bfc-119">この種の処理は、構造上の変更をオブジェクトに加えた場合に必要となります。</span><span class="sxs-lookup"><span data-stu-id="60bfc-119">This kind of processing is required when a structural change has been made to an object.</span></span>|  
    |<span data-ttu-id="60bfc-120">**データの処理**</span><span class="sxs-lookup"><span data-stu-id="60bfc-120">**Process Data**</span></span>|<span data-ttu-id="60bfc-121">階層またはリレーションシップを再構築したり、計算列とメジャーを再計算したりせずに、パーティションまたはテーブルにデータを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="60bfc-121">Load data into a partition or a table without rebuilding hierarchies or relationships or recalculating calculated columns and measures.</span></span>|  
    |<span data-ttu-id="60bfc-122">**消去の処理**</span><span class="sxs-lookup"><span data-stu-id="60bfc-122">**Process Clear**</span></span>|<span data-ttu-id="60bfc-123">パーティションからすべてのデータを削除します。</span><span class="sxs-lookup"><span data-stu-id="60bfc-123">Removes all data from a partition.</span></span>|  
    |<span data-ttu-id="60bfc-124">**追加の処理**</span><span class="sxs-lookup"><span data-stu-id="60bfc-124">**Process Add**</span></span>|<span data-ttu-id="60bfc-125">パーティションを新しいデータで増分更新します。</span><span class="sxs-lookup"><span data-stu-id="60bfc-125">Incrementally update partition with new data.</span></span>|  
  
3.  <span data-ttu-id="60bfc-126">**[処理]** チェックボックス列で、選択したモードで処理するパーティションを選択し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="60bfc-126">In the **Process** checkbox column, select the partitions you want to process with the selected mode, and then click **Ok**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60bfc-127">参照</span><span class="sxs-lookup"><span data-stu-id="60bfc-127">See Also</span></span>  
 <span data-ttu-id="60bfc-128">[SSAS 表形式のパーティション &#40;&#41;](partitions-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="60bfc-128">[Partitions &#40;SSAS Tabular&#41;](partitions-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="60bfc-129">ワークスペース データベースのパーティションの作成と管理 (SSAS テーブル)</span><span class="sxs-lookup"><span data-stu-id="60bfc-129">Create and Manage Partitions in the Workspace Database &#40;SSAS Tabular&#41;</span></span>](workspace-database-ssas-tabular.md)  
  
  
