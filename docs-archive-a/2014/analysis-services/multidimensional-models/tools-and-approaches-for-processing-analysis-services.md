---
title: 処理のためのツールと方法 (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- process [Analysis Services]
- processing [Analysis Services]
ms.assetid: 82347a16-4145-4655-8adf-2a300f1fdf99
author: minewiskan
ms.author: owend
ms.openlocfilehash: d2b28ecf29adc8240f76ec9888f9d4cb06dda887
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641314"
---
# <a name="tools-and-approaches-for-processing-analysis-services"></a><span data-ttu-id="643d4-102">処理するためのツールと方法 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="643d4-102">Tools and Approaches for Processing (Analysis Services)</span></span>
  <span data-ttu-id="643d4-103">"処理" とは、Analysis Services がリレーショナル データ ソースにクエリを実行し、そのデータを使用して Analysis Services オブジェクトを設定する操作です。</span><span class="sxs-lookup"><span data-stu-id="643d4-103">Processing is an operation in which Analysis Services queries a relational data source and populates Analysis Services objects using that data.</span></span>  
  
 <span data-ttu-id="643d4-104">Analysis Services のシステム管理者は、以下の方法で [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] オブジェクトの処理の実行と監視を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="643d4-104">As an Analysis Services system administrator, you can execute and monitor the processing of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] objects using these approaches:</span></span>  
  
-   <span data-ttu-id="643d4-105">オブジェクトの依存関係や操作のスコープを理解する影響分析の実行</span><span class="sxs-lookup"><span data-stu-id="643d4-105">Run Impact Analysis to understand object dependencies and scope of operations</span></span>  
  
-   <span data-ttu-id="643d4-106">SQL Server Management Studio の個々のオブジェクトの処理 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]</span><span class="sxs-lookup"><span data-stu-id="643d4-106">Process individual objects in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]</span></span>  
  
-   <span data-ttu-id="643d4-107">SQL Server Data Tools (SSDT) の個々のオブジェクトまたは複数のオブジェクトの処理 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]</span><span class="sxs-lookup"><span data-stu-id="643d4-107">Process individual or multiple objects in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]</span></span>  
  
-   <span data-ttu-id="643d4-108">現在のアクションの結果として未処理となる関連オブジェクトの一覧を確認する影響分析の実行</span><span class="sxs-lookup"><span data-stu-id="643d4-108">Run Impact Analysis to review a list of related objects that will be unprocessed as result of the current action.</span></span>  
  
-   <span data-ttu-id="643d4-109">個々のオブジェクトまたは複数のオブジェクトを処理するために、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] の [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] XMLA クエリ ウィンドウでスクリプトを生成し、実行</span><span class="sxs-lookup"><span data-stu-id="643d4-109">Generate and run a script in an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] XMLA Query window in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] to process individual or multiple objects</span></span>  
  
-   <span data-ttu-id="643d4-110">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] PowerShell コマンドレットの使用</span><span class="sxs-lookup"><span data-stu-id="643d4-110">Use [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] PowerShell cmdlets</span></span>  
  
-   <span data-ttu-id="643d4-111">制御フローとタスクで使用する [!INCLUDE[ssIS](../../includes/ssis-md.md)] パッケージの使用</span><span class="sxs-lookup"><span data-stu-id="643d4-111">Use control flows and tasks in [!INCLUDE[ssIS](../../includes/ssis-md.md)] packages</span></span>  
  
-   <span data-ttu-id="643d4-112">SQL Server Profiler の処理の監視</span><span class="sxs-lookup"><span data-stu-id="643d4-112">Monitor processing with SQL Server Profiler</span></span>  
  
-   <span data-ttu-id="643d4-113">AMO を使用した、カスタム ソリューションのプログラム</span><span class="sxs-lookup"><span data-stu-id="643d4-113">Program a custom solution using AMO.</span></span> <span data-ttu-id="643d4-114">詳細については、「 [AMO OLAP 基本オブジェクトのプログラミング](https://docs.microsoft.com/bi-reference/amo/programming-amo-olap-basic-objects)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="643d4-114">For more information, see [Programming AMO OLAP Basic Objects](https://docs.microsoft.com/bi-reference/amo/programming-amo-olap-basic-objects).</span></span>  
  
 <span data-ttu-id="643d4-115">処理は、柔軟に構成できる操作で、オブジェクト レベルで発生する完全処理や増分処理の一連の処理オプションを使用して制御します。</span><span class="sxs-lookup"><span data-stu-id="643d4-115">Processing is a highly configurable operation, controlled by a set of processing options that determine whether full or incremental processing occurs at the object level.</span></span> <span data-ttu-id="643d4-116">オプションとオブジェクトの処理に関する詳細については、「[処理オプションと設定 &#40;Analysis Services&#41;](processing-options-and-settings-analysis-services.md)」および「[Analysis Services オブジェクトの処理](processing-analysis-services-objects.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="643d4-116">For more information about processing options and objects, see [Processing Options and Settings &#40;Analysis Services&#41;](processing-options-and-settings-analysis-services.md) and [Processing Analysis Services Objects](processing-analysis-services-objects.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="643d4-117">このトピックでは、多次元モデルを処理するためのツールと方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="643d4-117">This topic describes the tools and approaches for processing multidimensional models.</span></span> <span data-ttu-id="643d4-118">テーブルモデルの処理の詳細については、「 [SSAS 表形式&#41;&#40;](../process-data-ssas-tabular.md)[データベース、テーブル、またはパーティション](../tabular-models/process-database-table-or-partition-analysis-services.md)の処理とデータの処理」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="643d4-118">For more information about processing tabular models, see [Process Database, Table, or Partition](../tabular-models/process-database-table-or-partition-analysis-services.md) and [Process Data &#40;SSAS Tabular&#41;](../process-data-ssas-tabular.md).</span></span>  
  
### <a name="processing-objects-in-sql-server-management-studio"></a><span data-ttu-id="643d4-119">SQL Server Management Studio でのオブジェクトの処理</span><span class="sxs-lookup"><span data-stu-id="643d4-119">Processing objects in SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="643d4-120">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] を起動し、Analysis Services に接続します。</span><span class="sxs-lookup"><span data-stu-id="643d4-120">Start [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] and connect to Analysis Services.</span></span>  
  
2.  <span data-ttu-id="643d4-121">処理対象の Analysis Services オブジェクトを右クリックし、 **[処理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="643d4-121">Right-click the Analysis Services object you want to process and then click **Process**.</span></span> <span data-ttu-id="643d4-122">データ処理は、以下のレベルで行うことができます。</span><span class="sxs-lookup"><span data-stu-id="643d4-122">You can process data at any of these levels:</span></span>  
  
    -   <span data-ttu-id="643d4-123">データベース</span><span class="sxs-lookup"><span data-stu-id="643d4-123">Databases</span></span>  
  
    -   <span data-ttu-id="643d4-124">キューブ</span><span class="sxs-lookup"><span data-stu-id="643d4-124">Cubes</span></span>  
  
    -   <span data-ttu-id="643d4-125">メジャー グループ (またはメジャー グループ内の個々のパーティション)</span><span class="sxs-lookup"><span data-stu-id="643d4-125">Measure Groups or individual partitions in the measure group</span></span>  
  
    -   <span data-ttu-id="643d4-126">Dimensions</span><span class="sxs-lookup"><span data-stu-id="643d4-126">Dimensions</span></span>  
  
    -   <span data-ttu-id="643d4-127">[マイニング モデル]</span><span class="sxs-lookup"><span data-stu-id="643d4-127">Mining Models</span></span>  
  
    -   <span data-ttu-id="643d4-128">マイニング構造</span><span class="sxs-lookup"><span data-stu-id="643d4-128">Mining Structures</span></span>  
  
     <span data-ttu-id="643d4-129">Analysis Services オブジェクトは階層構造になっています。</span><span class="sxs-lookup"><span data-stu-id="643d4-129">Analysis Services objects are hierarchical.</span></span> <span data-ttu-id="643d4-130">データベースを選択した場合、そのデータベースに格納されているすべてのオブジェクトに対して処理を適用することができます。</span><span class="sxs-lookup"><span data-stu-id="643d4-130">If you choose database, processing can occur for all of the objects contained in the database.</span></span> <span data-ttu-id="643d4-131">実際に処理が生じるかどうかは、選択した処理オプションとオブジェクトの状態によって異なります。</span><span class="sxs-lookup"><span data-stu-id="643d4-131">Whether processing actually occurs will vary depending on the process option you select and the state of the object.</span></span> <span data-ttu-id="643d4-132">具体的には、親を処理すると、その子である (未処理の) オブジェクトも処理の対象となります。</span><span class="sxs-lookup"><span data-stu-id="643d4-132">Specifically, if an object is unprocessed, processing its parent will result in that object getting processed.</span></span> <span data-ttu-id="643d4-133">オブジェクトの依存関係に関する詳細については、「 [Analysis Services オブジェクトの処理](processing-analysis-services-objects.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="643d4-133">For more information about object dependencies, see [Processing Analysis Services Objects](processing-analysis-services-objects.md).</span></span>  
  
3.  <span data-ttu-id="643d4-134">**[処理]** ダイアログ ボックスの **[処理オプション]** で、表示されている既定値をそのまま使用するか、別のオプションを一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="643d4-134">In the **Process** dialog box, in **Process Options**, use the default value provided or select a different option from the list.</span></span> <span data-ttu-id="643d4-135">各オプションの詳細については、「[処理オプションと設定 &#40;Analysis Services&#41;](processing-options-and-settings-analysis-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="643d4-135">For more information about each option, see [Processing Options and Settings &#40;Analysis Services&#41;](processing-options-and-settings-analysis-services.md).</span></span>  
  
4.  <span data-ttu-id="643d4-136">**[影響分析]** をクリックすると、[処理] ダイアログ ボックスに一覧表示されているオブジェクトが処理された場合に影響を受ける依存オブジェクトを識別し、オプションで処理できます。</span><span class="sxs-lookup"><span data-stu-id="643d4-136">Click **Impact Analysis** to identify and optionally process dependent objects that are affected if the objects listed in the Process dialog box are processed.</span></span>  
  
5.  <span data-ttu-id="643d4-137">必要に応じて、 **[設定の変更]** をクリックし、処理順序や特定の種類のエラーに関する処理の動作などの設定を変更します。</span><span class="sxs-lookup"><span data-stu-id="643d4-137">Optionally, click **Change Settings** to modify the processing order, processing behavior relative to specific types of errors, and other settings.</span></span>  
  
6.  <span data-ttu-id="643d4-138">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="643d4-138">Click **OK**.</span></span>  
  
     <span data-ttu-id="643d4-139">[処理の進行状況] ダイアログ ボックスに、各コマンドの進行状況が表示されます。</span><span class="sxs-lookup"><span data-stu-id="643d4-139">The Process Progress dialog box provides ongoing status for each command.</span></span> <span data-ttu-id="643d4-140">ステータス メッセージが切り詰められている場合は、 **[詳細表示]** をクリックすると、メッセージ全体を確認できます。</span><span class="sxs-lookup"><span data-stu-id="643d4-140">If a status message is truncated, you can click **View Details** to read the entire message.</span></span>  
  
### <a name="processing-objects-in-sql-server-data-tools"></a><span data-ttu-id="643d4-141">SQL Server データ ツールでのオブジェクトの処理</span><span class="sxs-lookup"><span data-stu-id="643d4-141">Processing Objects in SQL Server Data Tools</span></span>  
  
1.  <span data-ttu-id="643d4-142">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] を起動し、配置されているプロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="643d4-142">Start [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] and open a project that has been deployed.</span></span>  
  
2.  <span data-ttu-id="643d4-143">ソリューション エクスプローラーで、配置されたプロジェクトの **[ディメンション]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="643d4-143">In Solution Explorer, under the deployed project, expand the **Dimensions** folder.</span></span>  
  
3.  <span data-ttu-id="643d4-144">ディメンションを右クリックし、 **[プロセス]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="643d4-144">Right-click a dimension, and then click **Process**.</span></span> <span data-ttu-id="643d4-145">複数のディメンションを右クリックして、一度に複数のオブジェクトを処理することができます。</span><span class="sxs-lookup"><span data-stu-id="643d4-145">You can right-click multiple dimensions to process multiple objects at once.</span></span> <span data-ttu-id="643d4-146">詳細については、「 [バッチ処理 &#40;Analysis Services&#41;](batch-processing-analysis-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="643d4-146">For more information, see [Batch Processing &#40;Analysis Services&#41;](batch-processing-analysis-services.md).</span></span>  
  
4.  <span data-ttu-id="643d4-147">**[ディメンションの処理]** ダイアログ ボックスにある **[オブジェクト一覧]** の **[処理オプション]** 列で、この列のオプションが **[完全処理]** であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="643d4-147">In the **Process Dimension** dialog box, in the **Process Options** column under **Object list**, verify that the option for this column is **Process Full**.</span></span> <span data-ttu-id="643d4-148">別のオプションが設定されている場合、 **[処理オプション]** 列のオプションをクリックし、表示される一覧から **[完全処理]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="643d4-148">If it is not, under **Process Options**, click the option, and select **Process Full** from the drop-down list.</span></span>  
  
5.  <span data-ttu-id="643d4-149">**[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="643d4-149">Click **Run**.</span></span>  
  
6.  <span data-ttu-id="643d4-150">処理が完了したら、 **[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="643d4-150">When processing is finished, click **Close**.</span></span>  
  
##  <a name="run-impact-analysis-to-identify-object-dependencies-and-scope-of-operations"></a><a name="bkmk_impactanalysis"></a><span data-ttu-id="643d4-151">オブジェクトの依存関係と操作のスコープを識別する影響分析の実行</span><span class="sxs-lookup"><span data-stu-id="643d4-151">Run Impact Analysis to identify object dependencies and scope of operations</span></span>  
  
1.  <span data-ttu-id="643d4-152">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] または [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] のいずれかの [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]オブジェクトを処理する前に、 **[処理オブジェクト]** ダイアログ ボックスの **[影響分析]** をクリックして、関連オブジェクトへの影響を分析できます。</span><span class="sxs-lookup"><span data-stu-id="643d4-152">Before you process an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] object in either [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] or [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], you can analyze the effect on related objects by clicking **Impact Analysis** in one of the **Process Objects** dialog boxes.</span></span>  
  
2.  <span data-ttu-id="643d4-153">ディメンション、キューブ、メジャー グループ、またはパーティションを右クリックし、 **[処理オブジェクト]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="643d4-153">Right-click a dimension, cube, measure group, or partition to open a **Process Objects** dialog box.</span></span>  
  
3.  <span data-ttu-id="643d4-154">**[影響の分析]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="643d4-154">Click **Impact Analysis**.</span></span> [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="643d4-155">は、モデルをスキャンし、処理対象として選択したオブジェクトに関連するオブジェクトの再処理の要件をレポートします。</span><span class="sxs-lookup"><span data-stu-id="643d4-155">scans the model and reports on reprocessing requirements for objects that are related to the one you selected for processing.</span></span>  
  
### <a name="processing-objects-using-xmla"></a><span data-ttu-id="643d4-156">XMLA を使用したオブジェクトの処理</span><span class="sxs-lookup"><span data-stu-id="643d4-156">Processing objects using XMLA</span></span>  
  
1.  <span data-ttu-id="643d4-157">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] を起動し、Analysis Services に接続します。</span><span class="sxs-lookup"><span data-stu-id="643d4-157">Start [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] and connect to Analysis Services.</span></span>  
  
2.  <span data-ttu-id="643d4-158">処理するオブジェクトを右クリックし、 **[処理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="643d4-158">Right-click the object to be processed and then click **Process**.</span></span>  
  
3.  <span data-ttu-id="643d4-159">**[処理]** ダイアログ ボックスで、使用する処理オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="643d4-159">In the **Process** dialog box, select the process option you want to use.</span></span> <span data-ttu-id="643d4-160">必要に応じて他の設定も変更します。</span><span class="sxs-lookup"><span data-stu-id="643d4-160">Modify any other settings.</span></span> <span data-ttu-id="643d4-161">必要な変更は、影響分析を実行して特定できます。</span><span class="sxs-lookup"><span data-stu-id="643d4-161">Run Impact Analysis to identify any changes you might need to make.</span></span>  
  
4.  <span data-ttu-id="643d4-162">**[処理オブジェクト]** ダイアログ ボックスの **[スクリプト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="643d4-162">Click **Script** on the **Process Objects** screen.</span></span>  
  
     <span data-ttu-id="643d4-163">これにより、XMLA スクリプトが生成され、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] XMLA クエリ ウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="643d4-163">This generates an XMLA script and opens an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] XMLA Query window.</span></span>  
  
5.  <span data-ttu-id="643d4-164">ダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="643d4-164">Close the dialog box.</span></span> <span data-ttu-id="643d4-165">スクリプトには、処理コマンドとダイアログ ボックスで指定したオプションが含まれます。</span><span class="sxs-lookup"><span data-stu-id="643d4-165">The script contains the processing command and options that were specified in the dialog box.</span></span>  
  
6.  <span data-ttu-id="643d4-166">同じバッチ内で他のオブジェクトを処理する場合は、スクリプトに続けて追加できます。</span><span class="sxs-lookup"><span data-stu-id="643d4-166">Optionally, you can continue adding to the script if you want to process additional objects in the same batch.</span></span> <span data-ttu-id="643d4-167">続行するには、前の手順を繰り返し、生成されたスクリプトを追加します。それにより、すべての処理操作を行う 1 つのスクリプトを作成できます。</span><span class="sxs-lookup"><span data-stu-id="643d4-167">To continue, repeat the previous steps, appending the generated script so that you have a single script for all processing operations.</span></span> <span data-ttu-id="643d4-168">例を表示するには、「 [SQL Server エージェントで SSAS 管理タスクのスケジュール設定を行う](../instances/schedule-ssas-administrative-tasks-with-sql-server-agent.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="643d4-168">To view an example, see [Schedule SSAS Administrative Tasks with SQL Server Agent](../instances/schedule-ssas-administrative-tasks-with-sql-server-agent.md).</span></span>  
  
7.  <span data-ttu-id="643d4-169">メニュー バーの **[クエリ]** をクリックし、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="643d4-169">From the menu bar, click **Query**, and then click **Execute**.</span></span>  
  
### <a name="processing-objects-using-powershell"></a><span data-ttu-id="643d4-170">PowerShell を使用したオブジェクトの処理</span><span class="sxs-lookup"><span data-stu-id="643d4-170">Processing objects using PowerShell</span></span>  
  
1.  <span data-ttu-id="643d4-171">このリリースの SQL Server からは、オブジェクトの処理に、Analysis Services PowerShell コマンドレットを使用できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="643d4-171">Starting in this release of SQL Server, you can use Analysis Services PowerShell cmdlets to process objects.</span></span> <span data-ttu-id="643d4-172">対話形式またはスクリプトで、次のコマンドレットを実行できます。</span><span class="sxs-lookup"><span data-stu-id="643d4-172">The following cmdlets can be run interactively or in script:</span></span>  
  
    -   [<span data-ttu-id="643d4-173">Invoke-ProcessCube コマンドレット</span><span class="sxs-lookup"><span data-stu-id="643d4-173">Invoke-ProcessCube cmdlet</span></span>](/powershell/module/sqlserver/invoke-processcube)  
  
    -   [<span data-ttu-id="643d4-174">Invoke-ProcessDimension コマンドレット</span><span class="sxs-lookup"><span data-stu-id="643d4-174">Invoke-ProcessDimension cmdlet</span></span>](/powershell/module/sqlserver/invoke-processdimension)  
  
    -   [<span data-ttu-id="643d4-175">Invoke-ProcessPartition コマンドレット</span><span class="sxs-lookup"><span data-stu-id="643d4-175">Invoke-ProcessPartition cmdlet</span></span>](/powershell/module/sqlserver/invoke-processpartition)  
  
    -   <span data-ttu-id="643d4-176">[Invoke-ASCmd コマンドレット](/powershell/module/sqlserver/invoke-ascmd): 処理コマンドを含んだ XMLA、MDX、または DMX スクリプトを実行するときに使用します。</span><span class="sxs-lookup"><span data-stu-id="643d4-176">[Invoke-ASCmd cmdlet](/powershell/module/sqlserver/invoke-ascmd), which can be used to execute XMLA, MDX, or DMX script that includes processing commands.</span></span>  
  
### <a name="monitoring-object-processing-using-sql-server-profiler"></a><span data-ttu-id="643d4-177">SQL Server Profiler を使用したオブジェクトの処理の監視</span><span class="sxs-lookup"><span data-stu-id="643d4-177">Monitoring object processing using SQL Server Profiler</span></span>  
  
1.  <span data-ttu-id="643d4-178">SQL Server Profiler で Analysis Services インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="643d4-178">Connect to an Analysis Services instance in SQL Server Profiler.</span></span>  
  
2.  <span data-ttu-id="643d4-179">[イベントの選択] で、 **[すべてのイベントを表示する]** をクリックしてすべてのイベントをリストに追加します。</span><span class="sxs-lookup"><span data-stu-id="643d4-179">In Events Selection, click **Show all events** to add all events to the list.</span></span>  
  
3.  <span data-ttu-id="643d4-180">次のイベントを選択します。</span><span class="sxs-lookup"><span data-stu-id="643d4-180">Choose the following events:</span></span>  
  
    -   <span data-ttu-id="643d4-181">処理の開始時刻と停止時刻を表示するには、**[コマンド開始]** と **Commと End** to show when processing starts と stops</span><span class="sxs-lookup"><span data-stu-id="643d4-181">**Command Begin** and **Command End** to show when processing starts and stops</span></span>  
  
    -   <span data-ttu-id="643d4-182">すべてのエラーをキャプチャするには、**[エラー]**</span><span class="sxs-lookup"><span data-stu-id="643d4-182">**Error** to capture any errors</span></span>  
  
    -   <span data-ttu-id="643d4-183">処理の状態をレポートし、データを取得するために使用した SQL クエリを表示するには、**[進行状況レポートの開始]**, **[進行状況レポートの現在の状態]**、および **[進行状況レポートの終了]**</span><span class="sxs-lookup"><span data-stu-id="643d4-183">**Progress Report Begin**, **Progress Report Current**, and **Progress Report End** to report on process status and show the SQL queries used to retrieve the data</span></span>  
  
    -   <span data-ttu-id="643d4-184">キューブの計算を表示するには、**[MDX スクリプトの実行の開始]** および **[MDX スクリプトの実行の終了]**</span><span class="sxs-lookup"><span data-stu-id="643d4-184">**Execute MDX Script Begin** and **Execute MDX Script End** to show the cube calculations</span></span>  
  
    -   <span data-ttu-id="643d4-185">処理に関連するパフォーマンスの問題を診断する場合は、必要に応じて、ロック イベントを追加する</span><span class="sxs-lookup"><span data-stu-id="643d4-185">Optionally, add lock events if you are diagnosing performance problems related to processing</span></span>  
  
### <a name="process-analysis-services-objects-using-integration-services"></a><span data-ttu-id="643d4-186">Integration Services を使用して、Analysis Services オブジェクトを処理する</span><span class="sxs-lookup"><span data-stu-id="643d4-186">Process Analysis Services objects using Integration Services</span></span>  
  
1.  <span data-ttu-id="643d4-187">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]で Analysis Services 処理タスクを使用するパッケージを作成して、ソース リレーショナル データベースの定期更新を実行するときに、オブジェクトに新しいデータを自動的に設定できます。</span><span class="sxs-lookup"><span data-stu-id="643d4-187">In [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], create a package that uses the Analysis Services Processing Task to automatically populate objects with new data when you make regular updates to your source relational database.</span></span>  
  
2.  <span data-ttu-id="643d4-188">**[SSIS ツールボックス]** で **[Analysis Services 処理]** をダブルクリックしてパッケージに追加します。</span><span class="sxs-lookup"><span data-stu-id="643d4-188">In the **SSIS Toolbox**, double-click **Analysis Services Processing** to add it to the package.</span></span>  
  
3.  <span data-ttu-id="643d4-189">オブジェクトを処理するデータベースへの接続を指定するタスク、および処理のオプションを編集します。</span><span class="sxs-lookup"><span data-stu-id="643d4-189">Edit the task to specify a connection to the database, which objects to process, and the process option.</span></span> <span data-ttu-id="643d4-190">このタスクの実装方法については、「 [Analysis Services 処理タスク](../../integration-services/control-flow/analysis-services-processing-task.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="643d4-190">For more information about how to implement this task, see [Analysis Services Processing Task](../../integration-services/control-flow/analysis-services-processing-task.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="643d4-191">参照</span><span class="sxs-lookup"><span data-stu-id="643d4-191">See Also</span></span>  
 [<span data-ttu-id="643d4-192">多次元モデルのオブジェクト処理</span><span class="sxs-lookup"><span data-stu-id="643d4-192">Multidimensional Model Object Processing</span></span>](processing-a-multidimensional-model-analysis-services.md)  
  
  
