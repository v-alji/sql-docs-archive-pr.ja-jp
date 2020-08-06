---
title: SSIS デザイナー | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Integration Services, SSIS Designer
- Business Intelligence Development Studio, Integration Services in
- tools [Integration Services], SSIS Designer
- SSIS, SSIS Designer
- SSIS Designer, about SSIS Designer
- Integration Services, SSIS Designer
ms.assetid: 006d68ea-1b5c-4c1e-8079-3910288e012c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a54a3b445317c59582b8dedcb162e244fda1b58d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718524"
---
# <a name="ssis-designer"></a><span data-ttu-id="0f202-102">SSIS デザイナー</span><span class="sxs-lookup"><span data-stu-id="0f202-102">SSIS Designer</span></span>
  [!INCLUDE[ssIS](../includes/ssis-md.md)] <span data-ttu-id="0f202-103">デザイナーは、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] パッケージの作成および管理に使用できるグラフィカル ツールです。</span><span class="sxs-lookup"><span data-stu-id="0f202-103">Designer is a graphical tool that you can use to create and maintain [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages.</span></span> [!INCLUDE[ssIS](../includes/ssis-md.md)] <span data-ttu-id="0f202-104">デザイナーは、 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] で [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトの一部として使用できます。</span><span class="sxs-lookup"><span data-stu-id="0f202-104">Designer is available in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] as part of an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project.</span></span>

 <span data-ttu-id="0f202-105">[!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーを使用すると、次のタスクを実行できます。</span><span class="sxs-lookup"><span data-stu-id="0f202-105">You can use [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer to perform the following tasks:</span></span>

-   <span data-ttu-id="0f202-106">パッケージ内に制御フローを構築します。</span><span class="sxs-lookup"><span data-stu-id="0f202-106">Constructing the control flow in a package.</span></span>

-   <span data-ttu-id="0f202-107">パッケージ内にデータ フローを構築します。</span><span class="sxs-lookup"><span data-stu-id="0f202-107">Constructing the data flows in a package.</span></span>

-   <span data-ttu-id="0f202-108">パッケージおよびパッケージ オブジェクトにイベント ハンドラーを追加します。</span><span class="sxs-lookup"><span data-stu-id="0f202-108">Adding event handlers to the package and package objects.</span></span>

-   <span data-ttu-id="0f202-109">パッケージの内容を表示します。</span><span class="sxs-lookup"><span data-stu-id="0f202-109">Viewing the package content.</span></span>

-   <span data-ttu-id="0f202-110">実行時に、パッケージの実行の進行状況を表示します。</span><span class="sxs-lookup"><span data-stu-id="0f202-110">At run time, viewing the execution progress of the package.</span></span>

 <span data-ttu-id="0f202-111">次の図は、 [!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーと **[ツールボックス]** ウィンドウを示しています。</span><span class="sxs-lookup"><span data-stu-id="0f202-111">The following diagram shows [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer and the **Toolbox** window.</span></span>

 <span data-ttu-id="0f202-112">![SSIS デザイナーおよびツールボックスのスクリーン ショット](media/denali-designerandtoolbox.gif "SSIS デザイナーおよびツールボックスのスクリーン ショット")</span><span class="sxs-lookup"><span data-stu-id="0f202-112">![Screenshot of SSIS Designer and Toolbox](media/denali-designerandtoolbox.gif "Screenshot of SSIS Designer and Toolbox")</span></span>

 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="0f202-113">には、さらに、パッケージに機能を追加するダイアログ ボックスとウィンドウが含まれており、 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] では、開発環境を構成しパッケージを使用するためのウィンドウとダイアログ ボックスが用意されています。</span><span class="sxs-lookup"><span data-stu-id="0f202-113">includes additional dialog boxes and windows for adding functionality to packages, and [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] provides windows and dialog boxes for configuring the development environment and working with packages.</span></span> <span data-ttu-id="0f202-114">詳細については、「 [Integration Services のユーザー インターフェイス](integration-services-user-interface.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0f202-114">For more information, see [Integration Services User Interface](integration-services-user-interface.md).</span></span>

 [!INCLUDE[ssIS](../includes/ssis-md.md)] <span data-ttu-id="0f202-115">デザイナーは、パッケージを管理および監視する [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サービスに対して依存関係はなく、 [!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーでパッケージを作成または変更するために、このサービスを実行する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="0f202-115">Designer has no dependency on the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service, the service that manages and monitors packages, and it is not required that the service be running to create or modify packages in [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="0f202-116">ただし、 [!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーが開いている間にサービスを停止すると、 [!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーで提供されるダイアログ ボックスを開くことができなくなり、"RPC サーバーを利用できません。" というエラー メッセージが返されます。</span><span class="sxs-lookup"><span data-stu-id="0f202-116">However, if you stop the service while [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer is open, you can no longer open the dialog boxes that [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer provides and you may receive the error message "RPC server is unavailable."</span></span> <span data-ttu-id="0f202-117">[!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーをリセットして引き続きパッケージを処理するには、デザイナーを閉じて [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]を終了し、次に [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクト、およびパッケージを再度開く必要があります。</span><span class="sxs-lookup"><span data-stu-id="0f202-117">To reset [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer and continue working with the package, you must close the designer, exit [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], and then reopen [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project, and the package.</span></span>

## <a name="undo-and-redo"></a><span data-ttu-id="0f202-118">元に戻す、やり直す</span><span class="sxs-lookup"><span data-stu-id="0f202-118">Undo and Redo</span></span>
 <span data-ttu-id="0f202-119">[!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーでの操作は、最大 20 件まで元に戻したり、やり直したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="0f202-119">You can undo and redo up to 20 actions in the [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="0f202-120">パッケージの場合、元に戻す/やり直すを使用できるのは、 **[制御フロー]** タブ、 **[データ フロー]** タブ、 **[イベント ハンドラー]** タブ、 **[パラメーター]** タブと、 **[変数]** ウィンドウです。</span><span class="sxs-lookup"><span data-stu-id="0f202-120">For a package, undo /redo is available in the **Control Flow**, **Data Flow**, **Event Handlers**, and **Parameters** tabs, and in the **Variables** window.</span></span> <span data-ttu-id="0f202-121">プロジェクトの場合、元に戻す/やり直すは **[プロジェクト パラメーター]** ウィンドウで使用できます。</span><span class="sxs-lookup"><span data-stu-id="0f202-121">For a project, undo/redo is available in the **Project Parameters** window.</span></span>

 <span data-ttu-id="0f202-122">**新しい SSIS ツールボックス**に対する変更を元に戻す/やり直すことはできません。</span><span class="sxs-lookup"><span data-stu-id="0f202-122">You can't undo/redo changes to the new **SSIS Toolbox**.</span></span>

 <span data-ttu-id="0f202-123">コンポーネント エディターを使用してコンポーネントを変更した場合、元に戻す/やり直す操作は個別の変更ではなく一連の変更に対して適用されます。</span><span class="sxs-lookup"><span data-stu-id="0f202-123">When you make changes to a component using the component editor, you undo and redo the changes as a set rather than undoing and redoing individual changes.</span></span> <span data-ttu-id="0f202-124">元に戻す/やり直す操作のドロップダウン リストでは、一連の変更が単一の操作として表示されます。</span><span class="sxs-lookup"><span data-stu-id="0f202-124">The set of changes appears as a single action in the undo and redo drop-down list.</span></span>

 <span data-ttu-id="0f202-125">操作を元に戻すには、元に戻すツール バー ボタンまたは **[編集]/[元に戻す]** メニュー項目をクリックするか、または Ctrl キーを押しながら Z キーを押します。</span><span class="sxs-lookup"><span data-stu-id="0f202-125">To undo an action, click the undo toolbar button, **Edit/Undo** menu item, or press CTRL+Z.</span></span> <span data-ttu-id="0f202-126">操作をやり直すには、やり直しツール バー ボタンまたは **[編集]/[やり直し]** メニュー項目をクリックするか、または Ctrl キーを押しながら Y キーを押します。複数の操作を元に戻したり、やり直したりするには、ツール バー ボタンの横にある矢印をクリックし、ドロップダウン リストで複数の操作を強調表示にして、リストをクリックします。</span><span class="sxs-lookup"><span data-stu-id="0f202-126">To redo an action, click the redo toolbar button, **Edit/Redo** menu item or press CTRL + Y. You can undo and redo multiple actions, by clicking the arrow next to the toolbar button, highlighting multiple actions in the drop-down list, and then clicking in the list.</span></span>

## <a name="parts-of-the-ssis-designer"></a><span data-ttu-id="0f202-127">SSIS デザイナーの構成要素</span><span class="sxs-lookup"><span data-stu-id="0f202-127">Parts of the SSIS Designer</span></span>
 [!INCLUDE[ssIS](../includes/ssis-md.md)] <span data-ttu-id="0f202-128">デザイナーには、パッケージ制御フロー、データ フロー、パラメーター、およびイベント ハンドラーを構築するタブが 1 つずつ、パッケージの内容を表示するタブが 1 つ、計 5 つのタブが常に表示されています。</span><span class="sxs-lookup"><span data-stu-id="0f202-128">Designer has five permanent tabs: one each for building package control flow, data flows, parameters, and event handlers, and one tab for viewing the contents of a package.</span></span> <span data-ttu-id="0f202-129">実行時には、6 番目のタブが表示され、実行中のパッケージの進行状況と実行完了後の実行結果を表示します。</span><span class="sxs-lookup"><span data-stu-id="0f202-129">At run time a sixth tab appears that shows the execution progress of a package while it is running and the execution results after it finishes.</span></span>

 <span data-ttu-id="0f202-130">また、 [!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーには、パッケージがデータに接続するために使用する接続マネージャーを追加および構成する、[接続マネージャー] 領域が含まれています。</span><span class="sxs-lookup"><span data-stu-id="0f202-130">In addition, [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer includes the Connection Managers area for adding and configuring the connection managers that a package uses to connect to data.</span></span>

### <a name="control-flow-tab"></a><span data-ttu-id="0f202-131">[制御フロー] タブ</span><span class="sxs-lookup"><span data-stu-id="0f202-131">Control Flow Tab</span></span>
 <span data-ttu-id="0f202-132">パッケージ内に制御フローを構築するには、 **[制御フロー]** タブのデザイン画面を使用します。アイテムを **[ツールボックス]** からデザイン画面にドラッグし、アイテムのアイコンをクリックして、矢印を別のアイテムにドラッグすると、アイテムが制御フローに連結されます。</span><span class="sxs-lookup"><span data-stu-id="0f202-132">You construct the control flow in a package on the design surface of the **Control Flow** tab. Drag items from **Toolbox** to the design surface and connect them into a control flow by clicking the icon for the item, and then dragging the arrow from one item to another.</span></span>

 <span data-ttu-id="0f202-133">詳細については、「 [Control Flow](control-flow/control-flow.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0f202-133">For more information, see [Control Flow](control-flow/control-flow.md).</span></span>

### <a name="data-flow-tab"></a><span data-ttu-id="0f202-134">[データ フロー] タブ</span><span class="sxs-lookup"><span data-stu-id="0f202-134">Data Flow Tab</span></span>
 <span data-ttu-id="0f202-135">パッケージ内にデータ フロー タスクが含まれている場合、データ フローをパッケージに追加できます。</span><span class="sxs-lookup"><span data-stu-id="0f202-135">If a package contains a Data flow task, you can add data flows to the package.</span></span> <span data-ttu-id="0f202-136">パッケージ内にデータ フローを構築するには、 **[データ フロー]** タブのデザイン画面を使用します。アイテムを **[ツールボックス]** からデザイン画面にドラッグし、アイテムのアイコンをクリックして、矢印を別のアイテムにドラッグすると、アイテムがデータ フローに連結されます。</span><span class="sxs-lookup"><span data-stu-id="0f202-136">You construct the data flows in a package on the design surface of the **Data Flow** tab. Drag items from **Toolbox** to the design surface and connect them into a data flow by clicking the icon for the item, and then dragging the arrow from one item to another.</span></span>

 <span data-ttu-id="0f202-137">詳細については、「 [Data Flow](data-flow/data-flow.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0f202-137">For more information, see [Data Flow](data-flow/data-flow.md).</span></span>

### <a name="parameters-tab"></a><span data-ttu-id="0f202-138">[パラメーター] タブ</span><span class="sxs-lookup"><span data-stu-id="0f202-138">Parameters Tab</span></span>
 <span data-ttu-id="0f202-139">Integration Services (SSIS) パラメーターを使用すると、パッケージの実行時にパッケージ内のプロパティに値を割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="0f202-139">Integration Services (SSIS) parameters allow you to assign values to properties within packages at the time of package execution.</span></span> <span data-ttu-id="0f202-140">プロジェクト パラメーターはプロジェクト レベル、パッケージ パラメーターはパッケージ レベルで作成できます。</span><span class="sxs-lookup"><span data-stu-id="0f202-140">You can create project parameters at the project level and package parameters at the package level.</span></span> <span data-ttu-id="0f202-141">プロジェクト パラメーターは、プロジェクトが受け取る外部入力をプロジェクト内の 1 つまたは複数のパッケージに指定するために使用します。</span><span class="sxs-lookup"><span data-stu-id="0f202-141">Project parameters are used to supply any external input the project receives to one or more packages in the project.</span></span> <span data-ttu-id="0f202-142">パッケージ パラメーターを使用すると、パッケージを編集したり再配置したりせずにパッケージ実行を変更できます。</span><span class="sxs-lookup"><span data-stu-id="0f202-142">Package parameters allow you to modify package execution without having to edit and redeploy the package.</span></span> <span data-ttu-id="0f202-143">このタブでは、パッケージ パラメーターを管理できます。</span><span class="sxs-lookup"><span data-stu-id="0f202-143">This tab allows you to manage package parameters.</span></span>

 <span data-ttu-id="0f202-144">パラメーターについて詳しくは、「[Integration Services &#40;SSIS&#41; パラメーター](integration-services-ssis-package-and-project-parameters.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="0f202-144">For more information about parameters, see [Integration Services &#40;SSIS&#41; Parameters](integration-services-ssis-package-and-project-parameters.md).</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="0f202-145">パラメーターを使用できるのは、プロジェクトの配置モデル用に開発したプロジェクトに対してのみです。</span><span class="sxs-lookup"><span data-stu-id="0f202-145">Parameters are available only to projects developed for the project deployment model.</span></span> <span data-ttu-id="0f202-146">したがって、プロジェクト配置モデルを使用するように構成されているプロジェクトの一部であるパッケージに対してのみ、[パラメーター] タブが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0f202-146">Therefore, you will see the Parameters tab only for packages that are part of a project configured to use the project deployment model.</span></span>

### <a name="event-handlers-tab"></a><span data-ttu-id="0f202-147">[イベント ハンドラー] タブ</span><span class="sxs-lookup"><span data-stu-id="0f202-147">Event Handlers Tab</span></span>
 <span data-ttu-id="0f202-148">パッケージ内にイベントを構築するには、 **[イベント ハンドラー]** タブのデザイン画面を使用します。 **[イベント ハンドラー]** タブで、イベント ハンドラーを作成するパッケージまたはパッケージ オブジェクトを選択し、次にイベント ハンドラーに関連付けるイベントを選択します。</span><span class="sxs-lookup"><span data-stu-id="0f202-148">You construct the events in a package on the design surface of the **Event Handlers** tab. On the **Event Handlers** tab, you select the package or package object that you want to create an event handler for, and then select the event to associate with the event handler.</span></span> <span data-ttu-id="0f202-149">イベント ハンドラーには制御フローと、オプションでデータ フローが含まれます。</span><span class="sxs-lookup"><span data-stu-id="0f202-149">An event handler has a control flow and optional data flows.</span></span>

 <span data-ttu-id="0f202-150">詳細については、「 [Add an Event Handler to a Package](../../2014/integration-services/add-an-event-handler-to-a-package.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0f202-150">For more information, see [Add an Event Handler to a Package](../../2014/integration-services/add-an-event-handler-to-a-package.md).</span></span>

### <a name="package-explorer-tab"></a><span data-ttu-id="0f202-151">[パッケージ エクスプローラー] タブ</span><span class="sxs-lookup"><span data-stu-id="0f202-151">Package Explorer Tab</span></span>
 <span data-ttu-id="0f202-152">パッケージは、タスク、接続マネージャー、変数、その他の要素が多数含まれていて複雑な場合があります。</span><span class="sxs-lookup"><span data-stu-id="0f202-152">Packages can be complex, including many tasks, connection managers, variables, and other elements.</span></span> <span data-ttu-id="0f202-153">パッケージをエクスプローラー ビューで表示すると、パッケージ要素の全一覧を確認できます。</span><span class="sxs-lookup"><span data-stu-id="0f202-153">The explorer view of the package lets you see a complete list of package elements.</span></span>

 <span data-ttu-id="0f202-154">詳細については、「 [パッケージ オブジェクトを表示する](view-package-objects.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0f202-154">For more information, see [View Package Objects](view-package-objects.md).</span></span>

#### <a name="progressexecution-result-tab"></a><span data-ttu-id="0f202-155">[進行状況] タブと [実行結果] タブ</span><span class="sxs-lookup"><span data-stu-id="0f202-155">Progress/Execution Result Tab</span></span>
 <span data-ttu-id="0f202-156">パッケージの実行中は、 **[進行状況]** タブにパッケージの実行の進行状況が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0f202-156">While a package is running, the **Progress** tab shows the execution progress of the package.</span></span> <span data-ttu-id="0f202-157">パッケージの実行が完了すると、 **[実行結果]** タブに実行結果が表示され、そのまま使用できます。</span><span class="sxs-lookup"><span data-stu-id="0f202-157">After the package has finished running, the execution results remain available on the **Execution Result** tab.</span></span>

> [!NOTE]
>  <span data-ttu-id="0f202-158">**[進行状況]** タブでのメッセージの表示を有効または無効にするには、 **[SSIS]** メニューの **[進行状況レポートのデバッグ]** オプションを切り替えます。</span><span class="sxs-lookup"><span data-stu-id="0f202-158">To enable or disable the display of messages on the **Progress** tab, toggle the **Debug Progress Reporting** option on the **SSIS** menu.</span></span>

##### <a name="connection-managers-area"></a><span data-ttu-id="0f202-159">[接続マネージャー] 領域</span><span class="sxs-lookup"><span data-stu-id="0f202-159">Connection Managers Area</span></span>
 <span data-ttu-id="0f202-160">パッケージで使用する接続マネージャーを追加および変更するには、 **[接続マネージャー]** 領域を使用します。</span><span class="sxs-lookup"><span data-stu-id="0f202-160">You add and modify the connection managers that a package uses in the **Connection Managers** area.</span></span> [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="0f202-161">には、テキスト ファイル、OLE DB データベース、.NET プロバイダーなど、さまざまなデータ ソースに接続するための接続マネージャーがあります。</span><span class="sxs-lookup"><span data-stu-id="0f202-161">includes connection managers to connect to a variety of data sources, such as text files, OLE DB databases, and .NET providers.</span></span>

 <span data-ttu-id="0f202-162">詳細については、「[Integration Services (SSIS) の接続](connection-manager/integration-services-ssis-connections.md)」および「[接続マネージャーを作成する](../../2014/integration-services/create-connection-managers.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0f202-162">For more information, see [Integration Services &#40;SSIS&#41; Connections](connection-manager/integration-services-ssis-connections.md) and [Create Connection Managers](../../2014/integration-services/create-connection-managers.md).</span></span>

## <a name="related-tasks"></a><span data-ttu-id="0f202-163">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="0f202-163">Related Tasks</span></span>

-   [<span data-ttu-id="0f202-164">SQL Server データ ツールでのパッケージの作成</span><span class="sxs-lookup"><span data-stu-id="0f202-164">Create Packages in SQL Server Data Tools</span></span>](create-packages-in-sql-server-data-tools.md)

## <a name="see-also"></a><span data-ttu-id="0f202-165">参照</span><span class="sxs-lookup"><span data-stu-id="0f202-165">See Also</span></span>
 [<span data-ttu-id="0f202-166">Integration Services のユーザー インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0f202-166">Integration Services User Interface</span></span>](integration-services-user-interface.md)


