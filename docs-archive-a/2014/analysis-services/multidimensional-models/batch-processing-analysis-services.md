---
title: バッチ処理 (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- batches [Analysis Services]
ms.assetid: ba4dcf72-0667-41d0-816b-ab8ff9a7d9cb
author: minewiskan
ms.author: owend
ms.openlocfilehash: c777339f41f5f9029e4d03d47cc7f682e00032b8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632159"
---
# <a name="batch-processing-analysis-services"></a><span data-ttu-id="5f810-102">バッチ処理 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="5f810-102">Batch Processing (Analysis Services)</span></span>
  <span data-ttu-id="5f810-103">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]では、Batch コマンドを使用して、1 つの要求で複数の処理コマンドをサーバーに送信することができます。</span><span class="sxs-lookup"><span data-stu-id="5f810-103">In [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], you can use the Batch command to send multiple processing commands to the server in a single request.</span></span> <span data-ttu-id="5f810-104">バッチ処理では、どのオブジェクトがどの順序で処理されるのかを制御できます。</span><span class="sxs-lookup"><span data-stu-id="5f810-104">Batch processing gives you a way to control which objects are to be processed, and in what order.</span></span> <span data-ttu-id="5f810-105">また、バッチは、一連のスタンドアロン ジョブとして実行するか、1 つのプロセスが失敗したときにバッチ全体をロールバックするトランザクションとして実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="5f810-105">Also, a batch can run as a series of stand-alone jobs, or as a transaction in which the failure of one process causes a rollback of the complete batch.</span></span>  
  
 <span data-ttu-id="5f810-106">バッチ処理では、変更をコミットするのに必要な時間をまとめることで短縮し、データの可用性を最大にします。</span><span class="sxs-lookup"><span data-stu-id="5f810-106">Batch processing maximizes data availability by consolidating and reducing the amount of time taken to commit changes.</span></span> <span data-ttu-id="5f810-107">ディメンションを完全に処理すると、そのディメンションを使用するパーティションには未処理のマークが付きます。</span><span class="sxs-lookup"><span data-stu-id="5f810-107">When you fully process a dimension, any partition using that dimension is marked as unprocessed.</span></span> <span data-ttu-id="5f810-108">その結果、未処理のパーティションを含むキューブは参照できなくなります。</span><span class="sxs-lookup"><span data-stu-id="5f810-108">As a result, cubes that contain the unprocessed partitions are unavailable for browsing.</span></span> <span data-ttu-id="5f810-109">この問題は、バッチ処理ジョブを使用し、影響を受けるパーティションと共にディメンションを処理することで対処できます。</span><span class="sxs-lookup"><span data-stu-id="5f810-109">You can address this with a batch processing job by processing the dimensions together with the affected partitions.</span></span> <span data-ttu-id="5f810-110">バッチ処理ジョブをトランザクションとして実行すると、すべての処理が完了するまで、そのトランザクションに含まれるすべてのオブジェクトをクエリ用に使用できます。</span><span class="sxs-lookup"><span data-stu-id="5f810-110">Running the batch processing job as a transaction makes sure that all objects included in the transaction remain available for queries until all processing is completed.</span></span> <span data-ttu-id="5f810-111">トランザクションが変更をコミットするときに、影響を受けるオブジェクトはロックされるため、オブジェクトは一時的に使用できなくなります。ただし、変更をコミットするために必要な全体の時間は、オブジェクトを個々に処理した場合よりも短縮されます。</span><span class="sxs-lookup"><span data-stu-id="5f810-111">As the transaction commits the changes, locks are put on the affected objects, making the objects temporarily unavailable, but overall the amount of time used to commit the changes is less than if you processed objects individually.</span></span>  
  
 <span data-ttu-id="5f810-112">このトピックでは、ディメンションおよびパーティションを完全に処理する手順を示します。</span><span class="sxs-lookup"><span data-stu-id="5f810-112">The procedures in this topic show the steps for fully processing dimensions and partitions.</span></span> <span data-ttu-id="5f810-113">バッチ処理には、増分処理などの他の処理オプションを含めることもできます。</span><span class="sxs-lookup"><span data-stu-id="5f810-113">Batch processing can also include other processing options, such as incremental processing.</span></span> <span data-ttu-id="5f810-114">この手順を正しく実行するためには、少なくとも 2 つのディメンションと 1 つのパーティションを含む既存の [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5f810-114">For these procedures to work correctly, you should use an existing [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database that contains at least two dimensions and one partition.</span></span>  
  
 <span data-ttu-id="5f810-115">このトピックのセクションは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="5f810-115">This topic includes the following sections:</span></span>  
  
 [<span data-ttu-id="5f810-116">SQL Server データ ツールでのバッチ処理</span><span class="sxs-lookup"><span data-stu-id="5f810-116">Batch Processing in SQL Server Data Tools</span></span>](#bkmk_ssdt)  
  
 [<span data-ttu-id="5f810-117">Management Studio での XMLA を使用したバッチ処理</span><span class="sxs-lookup"><span data-stu-id="5f810-117">Batch Processing using XMLA in Management Studio</span></span>](#bkmk_xmla)  
  
##  <a name="batch-processing-in-sql-server-data-tools"></a><a name="bkmk_ssdt"></a><span data-ttu-id="5f810-118">SQL Server Data Tools でのバッチ処理</span><span class="sxs-lookup"><span data-stu-id="5f810-118">Batch Processing in SQL Server Data Tools</span></span>  
 <span data-ttu-id="5f810-119">[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]でオブジェクトを処理するには、そのオブジェクトを含んでいるプロジェクトを配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5f810-119">Before objects can be processed in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], the project that contains the objects must be deployed.</span></span> <span data-ttu-id="5f810-120">詳細については、「[Analysis Services プロジェクトの配置 &#40;SSDT&#41;](deploy-analysis-services-projects-ssdt.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5f810-120">For more information, see [Deploy Analysis Services Projects &#40;SSDT&#41;](deploy-analysis-services-projects-ssdt.md).</span></span>  
  
1.  <span data-ttu-id="5f810-121">[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]を開きます。</span><span class="sxs-lookup"><span data-stu-id="5f810-121">Open [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].</span></span>  
  
2.  <span data-ttu-id="5f810-122">配置されているプロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="5f810-122">Open a project that has been deployed.</span></span>  
  
3.  <span data-ttu-id="5f810-123">ソリューション エクスプローラーで、配置されたプロジェクトの **[ディメンション]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="5f810-123">In Solution Explorer, under the deployed project, expand the **Dimensions** folder.</span></span>  
  
4.  <span data-ttu-id="5f810-124">Ctrl キーを押しながら、 **[ディメンション]** フォルダーに一覧表示されている各ディメンションをクリックします。</span><span class="sxs-lookup"><span data-stu-id="5f810-124">Holding the Ctrl key, click each dimension listed in the **Dimensions** folder.</span></span>  
  
5.  <span data-ttu-id="5f810-125">選択したディメンションを右クリックし、 **[処理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5f810-125">Right-click the selected dimensions, and then click **Process**.</span></span>  
  
6.  <span data-ttu-id="5f810-126">Ctrl キーを押しながら、 **[オブジェクト一覧]** に表示されている各ディメンションをクリックします。</span><span class="sxs-lookup"><span data-stu-id="5f810-126">Holding the Ctrl key, click each dimension listed in the **Object list**.</span></span>  
  
7.  <span data-ttu-id="5f810-127">選択したディメンションを右クリックし、 **[完全処理]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="5f810-127">Right-click the selected dimensions and select **Process Full**.</span></span>  
  
8.  <span data-ttu-id="5f810-128">バッチ処理ジョブをカスタマイズするには、 **[設定の変更]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5f810-128">To customize the batch process job, click **Change Settings.**</span></span>  
  
9. <span data-ttu-id="5f810-129">**[処理オプション]** で、以下の設定を行います。</span><span class="sxs-lookup"><span data-stu-id="5f810-129">Under **Processing options**, mark the following settings:</span></span>  
  
    -   <span data-ttu-id="5f810-130">**[処理順序]** を **[シーケンシャル]** に、 **[トランザクション モード]** を **[1 つのトランザクション]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="5f810-130">**Processing Order** is set to **Sequential**, and **Transaction mode** is set to **One Transaction**.</span></span>  
  
    -   <span data-ttu-id="5f810-131">**[書き戻しテーブル オプション]** を **[既存のデータを使用する]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="5f810-131">**Writeback Table Option** is set to **Use existing**.</span></span>  
  
    -   <span data-ttu-id="5f810-132">**[影響を受けたオブジェクト]** の **[影響を受けたオブジェクトを処理する]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="5f810-132">Under **Affected Objects**, select the **Process affected objects** check box.</span></span>  
  
10. <span data-ttu-id="5f810-133">[**ディメンションキーのエラー** ] タブをクリックします。 [**既定のエラー構成を使用**する] が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="5f810-133">Click the **Dimension key errors** tab. Verify that **Use default error configuration** is selected.</span></span>  
  
11. <span data-ttu-id="5f810-134">**[OK]** をクリックし、 **[設定の変更]** 画面を閉じます。</span><span class="sxs-lookup"><span data-stu-id="5f810-134">Click **OK** to close the **Change Settings** screen.</span></span>  
  
12. <span data-ttu-id="5f810-135">**[ディメンションの処理]** 画面で **[実行]** をクリックし、処理ジョブを開始します。</span><span class="sxs-lookup"><span data-stu-id="5f810-135">Click **Run** in the **Process Objects** screen to start the processing job.</span></span>  
  
13. <span data-ttu-id="5f810-136">**[状態]** ボックスに **"処理が成功しました"** と表示されたら、 **[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5f810-136">When the **Status** box shows **Process succeeded**, click **Close**.</span></span>  
  
14. <span data-ttu-id="5f810-137">**[ディメンションの処理]** 画面で **[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5f810-137">Click **Close** on the **Process Objects** screen.</span></span>  
  
##  <a name="batch-processing-using-xmla-in-management-studio"></a><a name="bkmk_xmla"></a><span data-ttu-id="5f810-138">Management Studio の XMLA を使用したバッチ処理</span><span class="sxs-lookup"><span data-stu-id="5f810-138">Batch Processing using XMLA in Management Studio</span></span>  
 <span data-ttu-id="5f810-139">バッチ処理を実行する XMLA スクリプトを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="5f810-139">You can create an XMLA script that performs batch processing.</span></span> <span data-ttu-id="5f810-140">まず、各オブジェクトに対して、 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] で XMLA スクリプトを生成し、次にそれらを対話形式で、またはスケジュールされているタスク内で実行する単一の XMLA クエリに統合します。</span><span class="sxs-lookup"><span data-stu-id="5f810-140">Start by generating an XMLA script in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] for each object, and then combine them into a single XMLA Query that you run interactively or inside a scheduled task.</span></span>  
  
 <span data-ttu-id="5f810-141">詳細な手順については、「 [SQL Server エージェントを使用した SSAS 管理タスクのスケジュール](../instances/schedule-ssas-administrative-tasks-with-sql-server-agent.md)」の**例 2**を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5f810-141">For step by step instructions, see **Example 2** in [Schedule SSAS Administrative Tasks with SQL Server Agent](../instances/schedule-ssas-administrative-tasks-with-sql-server-agent.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f810-142">参照</span><span class="sxs-lookup"><span data-stu-id="5f810-142">See Also</span></span>  
 [<span data-ttu-id="5f810-143">多次元モデルのオブジェクト処理</span><span class="sxs-lookup"><span data-stu-id="5f810-143">Multidimensional Model Object Processing</span></span>](processing-a-multidimensional-model-analysis-services.md)  
  
  
