---
title: テーブルモデルパーティションの処理 (SSAS テーブル)Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 6c498d2b-22d6-4661-bc21-2ee708336c8b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 496874707bd4030a98b1794fe7513d1d857390ae
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712434"
---
# <a name="process-tabular-model-partitions-ssas-tabular"></a><span data-ttu-id="de9ab-102">テーブル モデル パーティションの処理 (SSAS テーブル)</span><span class="sxs-lookup"><span data-stu-id="de9ab-102">Process Tabular Model Partitions (SSAS Tabular)</span></span>
  <span data-ttu-id="de9ab-103">パーティションは、テーブルを論理的な部分に分割します。</span><span class="sxs-lookup"><span data-stu-id="de9ab-103">Partitions divide a table into logical parts.</span></span> <span data-ttu-id="de9ab-104">各パーティションは、他のパーティションとは個別に処理 (更新) できます。</span><span class="sxs-lookup"><span data-stu-id="de9ab-104">Each partition can then be processed (Refreshed) independent of other partitions.</span></span> <span data-ttu-id="de9ab-105">このトピックのタスクでは、 **で** [パーティションの処理] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]ダイアログ ボックスを使用して、モデル データベースでパーティションを処理する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="de9ab-105">The tasks in this topic describe how to process partitions in a model database by using the **Process Partitions** dialog box in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
###  <a name="to-process-a-partition"></a><a name="bkmk_create_new"></a> <span data-ttu-id="de9ab-106">パーティションを処理するには</span><span class="sxs-lookup"><span data-stu-id="de9ab-106">To process a partition</span></span>  
  
1.  <span data-ttu-id="de9ab-107">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、処理対象のパーティションが存在するテーブルを右クリックして **[パーティション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="de9ab-107">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], right-click on the table that has the partitions you want to process, and then click **Partitions**.</span></span>  
  
2.  <span data-ttu-id="de9ab-108">**[パーティション]** ダイアログ ボックスの **[パーティション]** で、[処理] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="de9ab-108">In the **Partitions** dialog box, in **Partitions**, click on the Process button.</span></span>  
  
3.  <span data-ttu-id="de9ab-109">[**パーティションの処理**] ダイアログボックスの [**モード**] ボックスのリストで、次のプロセスモードのいずれかを選択します。</span><span class="sxs-lookup"><span data-stu-id="de9ab-109">In the **Process Partition(s)** dialog box, in the **Mode** listbox, select one of the following process modes:</span></span>  
  
    |<span data-ttu-id="de9ab-110">モード</span><span class="sxs-lookup"><span data-stu-id="de9ab-110">Mode</span></span>|<span data-ttu-id="de9ab-111">説明</span><span class="sxs-lookup"><span data-stu-id="de9ab-111">Description</span></span>|  
    |----------|-----------------|  
    |<span data-ttu-id="de9ab-112">**既定の処理**</span><span class="sxs-lookup"><span data-stu-id="de9ab-112">**Process Default**</span></span>|<span data-ttu-id="de9ab-113">パーティション オブジェクトの処理状態を検出して、未処理または部分的に処理されたパーティション オブジェクトを完全に処理された状態にするために必要な処理を実行します。</span><span class="sxs-lookup"><span data-stu-id="de9ab-113">Detects the process state of a partition object, and performs processing necessary to deliver unprocessed or partially processed partition objects to a fully processed state.</span></span> <span data-ttu-id="de9ab-114">空のテーブルとパーティションのデータが読み込まれ、階層、計算列、およびリレーションシップが構築または再構築されます。</span><span class="sxs-lookup"><span data-stu-id="de9ab-114">Data for empty tables and partitions is loaded; hierarchies, calculated columns, and relationships are built or rebuilt.</span></span>|  
    |<span data-ttu-id="de9ab-115">**完全処理**</span><span class="sxs-lookup"><span data-stu-id="de9ab-115">**Process Full**</span></span>|<span data-ttu-id="de9ab-116">パーティション オブジェクトとそこに含まれているすべてのオブジェクトを処理します。</span><span class="sxs-lookup"><span data-stu-id="de9ab-116">Processes a partition object and all the objects that it contains.</span></span> <span data-ttu-id="de9ab-117">既に処理されたオブジェクトに対して完全処理を実行すると、そのオブジェクト内のすべてのデータが [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] によって削除されてから、オブジェクトが処理されます。</span><span class="sxs-lookup"><span data-stu-id="de9ab-117">When Process Full is run for an object that has already been processed, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] drops all data in the object, and then processes the object.</span></span> <span data-ttu-id="de9ab-118">この種の処理は、構造上の変更をオブジェクトに加えた場合に必要となります。</span><span class="sxs-lookup"><span data-stu-id="de9ab-118">This kind of processing is required when a structural change has been made to an object.</span></span>|  
    |<span data-ttu-id="de9ab-119">**データの処理**</span><span class="sxs-lookup"><span data-stu-id="de9ab-119">**Process Data**</span></span>|<span data-ttu-id="de9ab-120">階層またはリレーションシップを再構築したり、計算列とメジャーを再計算したりせずに、パーティションまたはテーブルにデータを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="de9ab-120">Load data into a partition or a table without rebuilding hierarchies or relationships or recalculating calculated columns and measures.</span></span>|  
    |<span data-ttu-id="de9ab-121">**消去の処理**</span><span class="sxs-lookup"><span data-stu-id="de9ab-121">**Process Clear**</span></span>|<span data-ttu-id="de9ab-122">パーティションからすべてのデータを削除します。</span><span class="sxs-lookup"><span data-stu-id="de9ab-122">Removes all data from a partition.</span></span>|  
    |<span data-ttu-id="de9ab-123">**追加の処理**</span><span class="sxs-lookup"><span data-stu-id="de9ab-123">**Process Add**</span></span>|<span data-ttu-id="de9ab-124">パーティションを新しいデータで増分更新します。</span><span class="sxs-lookup"><span data-stu-id="de9ab-124">Incrementally update partition with new data.</span></span>|  
  
4.  <span data-ttu-id="de9ab-125">**[処理]** チェックボックス列で、選択したモードで処理するパーティションを選択し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="de9ab-125">In the **Process** checkbox column, select the partitions you want to process with the selected mode, and then click **Ok**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de9ab-126">参照</span><span class="sxs-lookup"><span data-stu-id="de9ab-126">See Also</span></span>  
 <span data-ttu-id="de9ab-127">[SSAS 表形式&#41;&#40;テーブルモデルパーティション](partitions-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="de9ab-127">[Tabular Model Partitions &#40;SSAS Tabular&#41;](partitions-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="de9ab-128">テーブル モデル パーティションの作成および管理 (SSAS テーブル)</span><span class="sxs-lookup"><span data-stu-id="de9ab-128">Create and Manage Tabular Model Partitions &#40;SSAS Tabular&#41;</span></span>](create-and-manage-tabular-model-partitions-ssas-tabular.md)  
  
  
