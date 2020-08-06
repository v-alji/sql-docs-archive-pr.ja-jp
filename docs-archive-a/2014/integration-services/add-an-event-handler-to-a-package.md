---
title: パッケージにイベントハンドラーを追加する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- event handlers [Integration Services], creating
ms.assetid: 5e56885d-8658-480a-bed9-3f2f8003fd78
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 007d81a395e06ac5a97210cd3e3ed6eea91aee57
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640222"
---
# <a name="add-an-event-handler-to-a-package"></a><span data-ttu-id="b68a3-102">パッケージにイベント ハンドラーを追加する</span><span class="sxs-lookup"><span data-stu-id="b68a3-102">Add an Event Handler to a Package</span></span>
  <span data-ttu-id="b68a3-103">コンテナーとタスクは実行時にイベントを発生させます。</span><span class="sxs-lookup"><span data-stu-id="b68a3-103">At run time, containers and tasks raise events.</span></span> <span data-ttu-id="b68a3-104">こうしたイベントが発生したときにワークフローを実行して、イベントに応答するカスタム イベント ハンドラーを作成できます。</span><span class="sxs-lookup"><span data-stu-id="b68a3-104">You can create custom event handlers that respond to these events by running a workflow when the event is raised.</span></span> <span data-ttu-id="b68a3-105">たとえば、タスクが失敗したときに電子メール メッセージを送信するイベント ハンドラーを作成できます。</span><span class="sxs-lookup"><span data-stu-id="b68a3-105">For example, you can create an event handler that sends an e-mail message when a task fails.</span></span>  
  
 <span data-ttu-id="b68a3-106">イベント ハンドラーは、パッケージと同様です。</span><span class="sxs-lookup"><span data-stu-id="b68a3-106">An event handler is similar to a package.</span></span> <span data-ttu-id="b68a3-107">イベント ハンドラーでは、パッケージと同様に変数のスコープが用意され、制御フローとオプションのデータ フローが含まれています。</span><span class="sxs-lookup"><span data-stu-id="b68a3-107">Like a package, an event handler can provide scope for variables, and includes a control flow and optional data flows.</span></span> <span data-ttu-id="b68a3-108">パッケージ、Foreach ループ コンテナー、For ループ コンテナー、シーケンス コンテナー、およびすべてのタスクに対してイベント ハンドラーを作成できます。</span><span class="sxs-lookup"><span data-stu-id="b68a3-108">You can build event handlers for packages, the Foreach Loop container, the For Loop container, the Sequence container, and all tasks.</span></span>  
  
 <span data-ttu-id="b68a3-109">イベント ハンドラーを作成するには、 **デザイナーにある** [イベント ハンドラー] [!INCLUDE[ssIS](../includes/ssis-md.md)] タブのデザイン画面を使用します。</span><span class="sxs-lookup"><span data-stu-id="b68a3-109">You create event handlers by using the design surface of the **Event Handlers** tab in [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="b68a3-110">**[イベント ハンドラー]** タブがアクティブな場合、 **デザイナーにあるツールボックスの** [制御フロー項目] **および** [メンテナンス プランのタスク] [!INCLUDE[ssIS](../includes/ssis-md.md)] ノードには、イベント ハンドラーで制御フローを作成するためのタスクとコンテナーが含まれます。</span><span class="sxs-lookup"><span data-stu-id="b68a3-110">When the **Event Handlers** tab is active, the **Control Flow Items** and **Maintenance Plan Tasks** nodes of the Toolbox in [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer contain the task and containers for building the control flow in the event handler.</span></span> <span data-ttu-id="b68a3-111">**[データ フローの変換元]**、 **[変換]**、および **[データ フローの変換先]** ノードには、イベント ハンドラーでデータ フローを作成するためのデータ ソース、変換、および変換先が含まれます。</span><span class="sxs-lookup"><span data-stu-id="b68a3-111">The **Data Flow Sources**, **Transformations**, **and Data Flow Destinations** nodes contain the data sources, transformations, and destinations for building the data flows in the event handler.</span></span> <span data-ttu-id="b68a3-112">詳細については、「 [制御フロー](control-flow/control-flow.md) 」と「 [データ フロー](data-flow/data-flow.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b68a3-112">For more information, see [Control Flow](control-flow/control-flow.md) and [Data Flow](data-flow/data-flow.md).</span></span>  
  
 <span data-ttu-id="b68a3-113">**[イベント ハンドラー]** タブには、 **[接続マネージャー]** 領域も含まれ、イベント ハンドラーがサーバーおよびデータ ソースに接続するために使用する、接続マネージャーの作成および変更を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="b68a3-113">The **Event Handlers** tab also includes the **Connections** Managers area where you can create and modify the connection managers that event handlers use to connect to servers and data sources.</span></span> <span data-ttu-id="b68a3-114">詳細については、「 [接続マネージャーを作成する](../../2014/integration-services/create-connection-managers.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b68a3-114">For more information, see [Create Connection Managers](../../2014/integration-services/create-connection-managers.md).</span></span>  
  
### <a name="to-create-an-event-handler"></a><span data-ttu-id="b68a3-115">イベント ハンドラーを作成するには</span><span class="sxs-lookup"><span data-stu-id="b68a3-115">To create an event handler</span></span>  
  
1.  <span data-ttu-id="b68a3-116">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で、目的のパッケージが含まれている [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="b68a3-116">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="b68a3-117">ソリューション エクスプローラーで、パッケージをダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="b68a3-117">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="b68a3-118">**[イベント ハンドラー]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="b68a3-118">Click the **Event Handlers** tab.</span></span>  
  
     <span data-ttu-id="b68a3-119">![イベント ハンドラーのデザイン画面のスクリーン ショット](media/eventhandlers.gif "イベント ハンドラーのデザイン画面のスクリーン ショット")</span><span class="sxs-lookup"><span data-stu-id="b68a3-119">![Screenshot of design surface with event handler](media/eventhandlers.gif "Screenshot of design surface with event handler")</span></span>  
  
     <span data-ttu-id="b68a3-120">イベント ハンドラー内で制御フローとデータ フローを作成する手順は、パッケージ内で制御フローとデータ フローを作成する手順と同様です。</span><span class="sxs-lookup"><span data-stu-id="b68a3-120">Creating the control flow and data flows in an event handler is similar to creating the control flow and data flows in a package.</span></span> <span data-ttu-id="b68a3-121">詳細については、「 [制御フロー](control-flow/control-flow.md) 」と「 [データ フロー](data-flow/data-flow.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b68a3-121">For more information, see [Control Flow](control-flow/control-flow.md) and [Data Flow](data-flow/data-flow.md).</span></span>  
  
4.  <span data-ttu-id="b68a3-122">**[実行可能ファイル]** の一覧から、イベント ハンドラーを作成する実行可能ファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="b68a3-122">In the **Executable** list, select the executable for which you want to create an event handler.</span></span>  
  
5.  <span data-ttu-id="b68a3-123">**[イベント ハンドラー]** の一覧から、作成するイベント ハンドラーを選択します。</span><span class="sxs-lookup"><span data-stu-id="b68a3-123">In the **Event handler** list, select the event handler you want to build.</span></span>  
  
6.  <span data-ttu-id="b68a3-124">**[イベント ハンドラー]** タブのデザイン画面のリンクをクリックします。</span><span class="sxs-lookup"><span data-stu-id="b68a3-124">Click the link on the design surface of the **Event Handler** tab.</span></span>  
  
7.  <span data-ttu-id="b68a3-125">制御フロー アイテムをイベント ハンドラーに追加し、優先順位制約を使用してアイテムを接続します。これは、制御フロー アイテムから別の制御フロー アイテムに制約をドラッグして行います。</span><span class="sxs-lookup"><span data-stu-id="b68a3-125">Add control flow items to the event handler, and connect items using a precedence constraint by dragging the constraint from one control flow item to another.</span></span> <span data-ttu-id="b68a3-126">詳細については、「 [Control Flow](control-flow/control-flow.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b68a3-126">For more information, see [Control Flow](control-flow/control-flow.md).</span></span>  
  
8.  <span data-ttu-id="b68a3-127">必要に応じてデータ フロー タスクを追加し、 **[データ フロー]** タブのデザイン画面で、イベント ハンドラーのデータ フローを作成します。</span><span class="sxs-lookup"><span data-stu-id="b68a3-127">Optionally, add a Data Flow task, and on the design surface of the **Data Flow** tab, create a data flow for the event handler.</span></span> <span data-ttu-id="b68a3-128">詳細については、「 [Data Flow](data-flow/data-flow.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b68a3-128">For more information, see [Data Flow](data-flow/data-flow.md).</span></span>  
  
9. <span data-ttu-id="b68a3-129">**[ファイル]** メニューの **[選択されたファイルを上書き保存]** をクリックし、新しいパッケージを保存します。</span><span class="sxs-lookup"><span data-stu-id="b68a3-129">On the **File** menu, click **Save Selected Items** to save the package.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b68a3-130">参照</span><span class="sxs-lookup"><span data-stu-id="b68a3-130">See Also</span></span>  
 <span data-ttu-id="b68a3-131">[SQL Server Integration Services](../../2014/integration-services/sql-server-integration-services.md) </span><span class="sxs-lookup"><span data-stu-id="b68a3-131">[SQL Server Integration Services](../../2014/integration-services/sql-server-integration-services.md) </span></span>  
 [<span data-ttu-id="b68a3-132">Integration Services &#40;SSIS&#41; のログ記録</span><span class="sxs-lookup"><span data-stu-id="b68a3-132">Integration Services &#40;SSIS&#41; Logging</span></span>](performance/integration-services-ssis-logging.md)  
  
  
