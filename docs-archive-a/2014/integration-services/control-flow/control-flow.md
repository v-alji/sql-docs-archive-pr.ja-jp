---
title: 制御フロー | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- control flow [Integration Services], elements
- SSIS control flow elements
- SQL Server Integration Services control flow elements
ms.assetid: 0cc042a9-1a7f-49ed-9f47-091653d5ef6e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 81ace5d285a67c6fee8a3a568ed89bc564193c42
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640185"
---
# <a name="control-flow"></a><span data-ttu-id="95cf7-102">制御フロー</span><span class="sxs-lookup"><span data-stu-id="95cf7-102">Control Flow</span></span>
  <span data-ttu-id="95cf7-103">パッケージは、制御フローと、オプションで含まれる 1 つ以上のデータ フローから構成されます。</span><span class="sxs-lookup"><span data-stu-id="95cf7-103">A package consists of a control flow and, optionally, one or more data flows.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="95cf7-104">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] に用意されている制御フロー要素は、パッケージ内の構造を提供するコンテナー、機能を提供するタスク、および優先順位制約の 3 種類です。優先順位制約は、実行ファイル、コンテナー、タスクを連結して正しく順序付けされた制御フローを作成するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="95cf7-104">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] provides three different types of control flow elements: containers that provide structures in packages, tasks that provide functionality, and precedence constraints that connect the executables, containers, and tasks into an ordered control flow.</span></span>

 <span data-ttu-id="95cf7-105">詳細については、「 [優先順位制約](precedence-constraints.md)」、「 [Integration Services コンテナー](integration-services-containers.md)」、および「 [Integration Services タスク](integration-services-tasks.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="95cf7-105">For more information, see [Precedence Constraints](precedence-constraints.md), [Integration Services Containers](integration-services-containers.md), and [Integration Services Tasks](integration-services-tasks.md).</span></span>

 <span data-ttu-id="95cf7-106">次の図は、1 つのコンテナーと 6 つのタスクで構成される制御フローを示しています。</span><span class="sxs-lookup"><span data-stu-id="95cf7-106">The following diagram shows a control flow that has one container and six tasks.</span></span> <span data-ttu-id="95cf7-107">タスクのうち 5 つはパッケージ レベルで定義され、残りの 1 つのタスクはコンテナー レベルで定義されています。</span><span class="sxs-lookup"><span data-stu-id="95cf7-107">Five of the tasks are defined at the package level, and one task is defined at the container level.</span></span> <span data-ttu-id="95cf7-108">タスクは、コンテナーの内部にあります。</span><span class="sxs-lookup"><span data-stu-id="95cf7-108">The task is inside a container.</span></span>

 <span data-ttu-id="95cf7-109">![6 つのタスクと 1 つのコンテナーで構成される制御フロー](../media/ssis-controlflowelmt.gif "6 つのタスクと 1 つのコンテナーとで構成される制御フロー")</span><span class="sxs-lookup"><span data-stu-id="95cf7-109">![Control flow with six tasks and a container](../media/ssis-controlflowelmt.gif "Control flow with six tasks and a container")</span></span>

 <span data-ttu-id="95cf7-110">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] のアーキテクチャでは入れ子のコンテナーがサポートされており、制御フローには複数のレベルで入れ子になったコンテナーを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="95cf7-110">The [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] architecture supports the nesting of containers, and a control flow can include multiple levels of nested containers.</span></span> <span data-ttu-id="95cf7-111">たとえば、パッケージには Foreach ループ コンテナーなどのコンテナーを含めることができ、Foreach ループ コンテナーには、さらに別の Foreach ループ コンテナーなどを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="95cf7-111">For example, a package could contain a container such as a Foreach Loop container, which in turn could contain another Foreach Loop container and so on.</span></span>

 <span data-ttu-id="95cf7-112">また、イベント ハンドラーにも、同じ種類の制御フローの要素を使用して作成される制御フローが含まれます。</span><span class="sxs-lookup"><span data-stu-id="95cf7-112">Event handlers also have control flows, which are built using the same kinds of control flow elements.</span></span>

## <a name="control-flow-implementation"></a><span data-ttu-id="95cf7-113">制御フローの実装</span><span class="sxs-lookup"><span data-stu-id="95cf7-113">Control Flow Implementation</span></span>
 <span data-ttu-id="95cf7-114">パッケージの制御フローを作成するには、 **デザイナーの** [制御フロー] [!INCLUDE[ssIS](../../../includes/ssis-md.md)] タブを使用します。</span><span class="sxs-lookup"><span data-stu-id="95cf7-114">You create the control flow in a package by using the **Control Flow** tab in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="95cf7-115">**[制御フロー]** タブがアクティブになっている場合、ツールボックスには、制御フローに追加できるタスクとコンテナーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="95cf7-115">When the **Control Flow** tab is active, the Toolbox lists the tasks and containers that you can add to the control flow.</span></span>

 <span data-ttu-id="95cf7-116">次の図は、制御フロー デザイナーに表示された、簡単なパッケージの制御フローを示しています。</span><span class="sxs-lookup"><span data-stu-id="95cf7-116">The following diagram shows the control flow of a simple package in the control flow designer.</span></span> <span data-ttu-id="95cf7-117">この図で表示されている制御フローは、パッケージレベルの 3 つのタスク、および 3 つのタスクが含まれるパッケージレベルの 1 つのコンテナーで構成されています。</span><span class="sxs-lookup"><span data-stu-id="95cf7-117">The control flow shown in the diagram is made up of three package-level tasks and one package-level container that contains three tasks.</span></span> <span data-ttu-id="95cf7-118">タスクとコンテナーは、優先順位制約を使用して連結されます。</span><span class="sxs-lookup"><span data-stu-id="95cf7-118">The tasks and container are connected by using precedence constraints.</span></span>

 <span data-ttu-id="95cf7-119">![パッケージの制御フロー デザイナーのスクリーンショット](../media/samplecontrolflow.gif "パッケージの制御フロー デザイナーのスクリーンショット")</span><span class="sxs-lookup"><span data-stu-id="95cf7-119">![Screenshot of control flow designer with package](../media/samplecontrolflow.gif "Screenshot of control flow designer with package")</span></span>

 <span data-ttu-id="95cf7-120">制御フローを作成するには、次の作業を行います。</span><span class="sxs-lookup"><span data-stu-id="95cf7-120">Creating a control flow includes the following tasks:</span></span>

-   <span data-ttu-id="95cf7-121">パッケージ内で繰り返すワークフローを実装するコンテナー、または制御フローをサブセットに分割するコンテナーを追加します。</span><span class="sxs-lookup"><span data-stu-id="95cf7-121">Adding containers that implement repeating workflows in a package or divide a control flow into subsets.</span></span>

-   <span data-ttu-id="95cf7-122">データ フローのサポート、データの準備、ワークフローとビジネス インテリジェンス機能の実行、およびスクリプトの実装を行うタスクを追加します。</span><span class="sxs-lookup"><span data-stu-id="95cf7-122">Adding tasks that support data flow, prepare data, perform workflow and business intelligence functions, and implement script.</span></span>

     [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] <span data-ttu-id="95cf7-123">には、パッケージのビジネス要件を満たす制御フローを作成するための、さまざまなタスクが含まれています。</span><span class="sxs-lookup"><span data-stu-id="95cf7-123">includes a variety of tasks that you can use to create control flow that meets the business requirements of the package.</span></span> <span data-ttu-id="95cf7-124">パッケージでデータを処理する必要がある場合、制御フローには少なくとも 1 つのデータ フロー タスクを含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="95cf7-124">If the package has to work with data, the control flow must include at least one Data Flow task.</span></span> <span data-ttu-id="95cf7-125">たとえば、データの抽出、データ値の集計、およびデータ ソースへの結果の書き込みをパッケージで行う必要がある場合などです。</span><span class="sxs-lookup"><span data-stu-id="95cf7-125">For example, a package might have to extract data, aggregate data values, and then write the results to a data source.</span></span>  <span data-ttu-id="95cf7-126">詳細については、「 [Integration Services タスク](integration-services-tasks.md) 」と「 [制御フローのタスクまたはコンテナーを追加または削除する](add-or-delete-a-task-or-a-container-in-a-control-flow.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="95cf7-126">For more information, see [Integration Services Tasks](integration-services-tasks.md) and [Add or Delete a Task or a Container in a Control Flow](add-or-delete-a-task-or-a-container-in-a-control-flow.md).</span></span>

-   <span data-ttu-id="95cf7-127">優先順位制約を使用してコンテナーとタスクを連結し、順序付けされた制御フローを作成します。</span><span class="sxs-lookup"><span data-stu-id="95cf7-127">Connecting containers and tasks into an ordered control flow by using precedence constraints.</span></span>

     <span data-ttu-id="95cf7-128">**[制御フロー]** タブのデザイン画面にタスクまたはコンテナーを追加すると、 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーは、アイテムにコネクタを自動的に追加します。</span><span class="sxs-lookup"><span data-stu-id="95cf7-128">After you add a task or container to the design surface of the **Control Flow** tab, [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer automatically adds a connector to the item.</span></span> <span data-ttu-id="95cf7-129">パッケージに 2 つ以上のアイテム、つまりタスクまたはコンテナーが含まれている場合、コネクタを 1 つのアイテムから別のアイテムにドラッグすると、それらを制御フローに結合できます。</span><span class="sxs-lookup"><span data-stu-id="95cf7-129">If a package includes two or more items, tasks or containers, you can join them into a control flow by dragging their connectors from one item to another.</span></span>

     <span data-ttu-id="95cf7-130">2 つのアイテム間のコネクタは、優先順位制約を表します。</span><span class="sxs-lookup"><span data-stu-id="95cf7-130">The connector between two items represents a precedence constraint.</span></span> <span data-ttu-id="95cf7-131">優先順位制約では、連結された 2 つのアイテムの関連性を定義します。</span><span class="sxs-lookup"><span data-stu-id="95cf7-131">A precedence constraint defines the relationship between the two connected items.</span></span> <span data-ttu-id="95cf7-132">ここでは、実行時にタスクとコンテナーが実行される順序、およびタスクとコンテナーが実行される条件を指定します。</span><span class="sxs-lookup"><span data-stu-id="95cf7-132">It specifies the order in which tasks and containers are executed at run time and the conditions under which tasks and containers run.</span></span> <span data-ttu-id="95cf7-133">たとえば、優先順位制約は、あるタスクが成功した場合にのみ、制御フロー内の次のタスクが実行されるように指定できます。</span><span class="sxs-lookup"><span data-stu-id="95cf7-133">For example, a precedence constraint can specify that a task must succeed for the next task in the control flow to run.</span></span> <span data-ttu-id="95cf7-134">詳細については、「 [優先順位制約](precedence-constraints.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="95cf7-134">For more information, see [Precedence Constraints](precedence-constraints.md).</span></span>

-   <span data-ttu-id="95cf7-135">接続マネージャーを追加します。</span><span class="sxs-lookup"><span data-stu-id="95cf7-135">Adding connection managers.</span></span>

     <span data-ttu-id="95cf7-136">多くのタスクではデータ ソースに接続する必要があるため、タスクに必要な接続マネージャーをパッケージに追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="95cf7-136">Many tasks require a connection to a data source, and you have to add the connection managers that the task requires to the package.</span></span> <span data-ttu-id="95cf7-137">使用する列挙子の型に応じて、Foreach ループ コンテナーにも接続マネージャーが必要となる場合があります。</span><span class="sxs-lookup"><span data-stu-id="95cf7-137">Depending on the enumerator type it uses, the Foreach Loop container may also require a connection manager.</span></span> <span data-ttu-id="95cf7-138">接続マネージャーは、制御フローをアイテム別に作成するときに追加できます。または、制御フローの作成を開始する前に追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="95cf7-138">You can add the connection managers as you construct the control flow item by item or before you start to construct the control flow.</span></span> <span data-ttu-id="95cf7-139">詳細については、「[Integration Services (SSIS) の接続](../connection-manager/integration-services-ssis-connections.md)」および「[接続マネージャーを作成する](../create-connection-managers.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="95cf7-139">For more information, see [Integration Services &#40;SSIS&#41; Connections](../connection-manager/integration-services-ssis-connections.md) and [Create Connection Managers](../create-connection-managers.md).</span></span>

 <span data-ttu-id="95cf7-140">また、[!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーには、デザイン画面を管理したり、制御フローを自己文書化するための、多数のデザイン時機能も含まれています。</span><span class="sxs-lookup"><span data-stu-id="95cf7-140">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer also includes many design-time features that you can use to manage the design surface and make the control flow self-documenting.</span></span>

## <a name="related-tasks"></a><span data-ttu-id="95cf7-141">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="95cf7-141">Related Tasks</span></span>

-   [<span data-ttu-id="95cf7-142">制御フローのタスクまたはコンテナーを追加または削除する</span><span class="sxs-lookup"><span data-stu-id="95cf7-142">Add or Delete a Task or a Container in a Control Flow</span></span>](add-or-delete-a-task-or-a-container-in-a-control-flow.md)

-   [<span data-ttu-id="95cf7-143">タスクまたはコンテナーのプロパティを設定する</span><span class="sxs-lookup"><span data-stu-id="95cf7-143">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)

-   [<span data-ttu-id="95cf7-144">コンポーネントのグループ化とグループの解除</span><span class="sxs-lookup"><span data-stu-id="95cf7-144">Group or Ungroup Components</span></span>](../group-or-ungroup-components.md)


