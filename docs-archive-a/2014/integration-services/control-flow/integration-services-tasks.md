---
title: Integration Services タスク | Microsoft Docs
ms.custom: ''
ms.date: 08/22/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- scripts [Integration Services], tasks
- files [Integration Services], task options
- workflow tasks [Integration Services]
- Integration Services, tasks
- adding package tasks
- tasks [Integration Services], listed
- SSIS tasks
- SSIS, tasks
- control flow [Integration Services], tasks
- tasks [Integration Services]
- grouping tasks
- tasks [Integration Services], about tasks
- SQL Server Integration Services tasks
- data preparation tasks [Integration Services]
- directory operations [Integration Services]
ms.assetid: 75c8901d-6966-4af3-abe5-10af6dd9313b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5fa58dec1e05a0333c295efc7f00a1d6df935792
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639587"
---
# <a name="integration-services-tasks"></a><span data-ttu-id="6ad05-102">Integration Services タスク</span><span class="sxs-lookup"><span data-stu-id="6ad05-102">Integration Services Tasks</span></span>
  <span data-ttu-id="6ad05-103">タスクとは、パッケージ制御フローで実行される作業の単位を定義する、制御フローの要素のことです。</span><span class="sxs-lookup"><span data-stu-id="6ad05-103">Tasks are control flow elements that define units of work that are performed in a package control flow.</span></span> <span data-ttu-id="6ad05-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージは、1 つ以上のタスクで構成されます。</span><span class="sxs-lookup"><span data-stu-id="6ad05-104">An [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package is made up of one or more tasks.</span></span> <span data-ttu-id="6ad05-105">パッケージに複数のタスクが含まれる場合、それらのタスクは優先順位制約によって順序が決定され、制御フロー内で連結されます。</span><span class="sxs-lookup"><span data-stu-id="6ad05-105">If the package contains more than one task, they are connected and sequenced in the control flow by precedence constraints.</span></span>  
  
 <span data-ttu-id="6ad05-106">また、COM をサポートする Visual Basic などのプログラミング言語や、C# などの .NET プログラミング言語を使用して、カスタム タスクを記述することもできます。</span><span class="sxs-lookup"><span data-stu-id="6ad05-106">You can also write custom tasks using a programming language that supports COM, such as Visual Basic, or a .NET programming language, such as C#.</span></span>  
  
 <span data-ttu-id="6ad05-107">[!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーは、パッケージを操作するための [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のグラフィック ツールであり、パッケージ制御フローを作成するためのデザイン画面、およびタスクを構成するためのカスタム エディターが用意されています。</span><span class="sxs-lookup"><span data-stu-id="6ad05-107">The [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, the graphical tool in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] for working with packages, provides the design surface for creating package control flow, and provides custom editors for configuring tasks.</span></span> <span data-ttu-id="6ad05-108">また、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] オブジェクト モデルをプログラムし、プログラムによってパッケージを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="6ad05-108">You can also program the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] object model to create packages programmatically.</span></span>  
  
## <a name="types-of-tasks"></a><span data-ttu-id="6ad05-109">タスクの種類</span><span class="sxs-lookup"><span data-stu-id="6ad05-109">Types of Tasks</span></span>  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="6ad05-110">には、次の種類のタスクが含まれます。</span><span class="sxs-lookup"><span data-stu-id="6ad05-110">includes the following types of tasks.</span></span>  
  
 <span data-ttu-id="6ad05-111">[データ フロー タスク]</span><span class="sxs-lookup"><span data-stu-id="6ad05-111">Data Flow Task</span></span>  
 <span data-ttu-id="6ad05-112">データ フローを実行して、データの抽出、列レベルの変換の適用、およびデータの読み込みを行うタスクです。</span><span class="sxs-lookup"><span data-stu-id="6ad05-112">The task that runs data flows to extract data, apply column level transformations, and load data.</span></span>  
  
 <span data-ttu-id="6ad05-113">データ準備タスク</span><span class="sxs-lookup"><span data-stu-id="6ad05-113">Data Preparation Tasks</span></span>  
 <span data-ttu-id="6ad05-114">ファイルやディレクトリのコピー、ファイルやデータのダウンロード、Web メソッドの実行、XML ドキュメントへの操作の適用、および最適化のためのデータのプロファイルを行うタスクです。</span><span class="sxs-lookup"><span data-stu-id="6ad05-114">These tasks do the following processes: copy files and directories; download files and data; run Web methods; apply operations to XML documents; and profile data for cleansing.</span></span>  
  
 <span data-ttu-id="6ad05-115">ワークフロー タスク</span><span class="sxs-lookup"><span data-stu-id="6ad05-115">Workflow Tasks</span></span>  
 <span data-ttu-id="6ad05-116">別のプロセスと通信して、パッケージの実行、プログラムまたはバッチ ファイルの実行、パッケージ間のメッセージの送受信、電子メール メッセージの送信、Windows Management Instrumentation (WMI) データの読み取り、および WMI イベントの監視を行うタスクです。</span><span class="sxs-lookup"><span data-stu-id="6ad05-116">The tasks that communicate with other processes to run packages, run programs or batch files, send and receive messages between packages, send e-mail messages, read Windows Management Instrumentation (WMI) data, and watch for WMI events.</span></span>  
  
 <span data-ttu-id="6ad05-117">SQL Server のタスク</span><span class="sxs-lookup"><span data-stu-id="6ad05-117">SQL Server Tasks</span></span>  
 <span data-ttu-id="6ad05-118">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のオブジェクトとデータにアクセスし、コピー、挿入、削除、および変更を行うタスクです。</span><span class="sxs-lookup"><span data-stu-id="6ad05-118">The tasks that access, copy, insert, delete, and modify [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] objects and data.</span></span>  
  
 <span data-ttu-id="6ad05-119">スクリプト タスク</span><span class="sxs-lookup"><span data-stu-id="6ad05-119">Scripting Tasks</span></span>  
 <span data-ttu-id="6ad05-120">スクリプトを使用して、パッケージ機能を拡張するタスクです。</span><span class="sxs-lookup"><span data-stu-id="6ad05-120">The tasks that extend package functionality by using scripts.</span></span>  
  
 <span data-ttu-id="6ad05-121">Analysis Services のタスク</span><span class="sxs-lookup"><span data-stu-id="6ad05-121">Analysis Services Tasks</span></span>  
 <span data-ttu-id="6ad05-122">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] オブジェクトを作成、変更、削除、および処理するタスクです。</span><span class="sxs-lookup"><span data-stu-id="6ad05-122">The tasks that create, modify, delete, and process [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] objects.</span></span>  
  
 <span data-ttu-id="6ad05-123">メンテナンス タスク</span><span class="sxs-lookup"><span data-stu-id="6ad05-123">Maintenance Tasks</span></span>  
 <span data-ttu-id="6ad05-124">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースのバックアップと圧縮、インデックスの再構築と再編成、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブの実行などの管理機能を実行するタスクです。</span><span class="sxs-lookup"><span data-stu-id="6ad05-124">The tasks that perform administrative functions such as backing up and shrinking [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases, rebuilding and reorganizing indexes, and running [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs.</span></span>  
  
 <span data-ttu-id="6ad05-125">カスタム タスク</span><span class="sxs-lookup"><span data-stu-id="6ad05-125">Custom Tasks</span></span>  
 <span data-ttu-id="6ad05-126">COM をサポートする Visual Basic などのプログラミング言語や、C# などの .NET プログラミング言語を使用して、カスタム タスクを記述することもできます。</span><span class="sxs-lookup"><span data-stu-id="6ad05-126">Additionally, you can write custom tasks using a programming language that supports COM, such as Visual Basic, or a .NET programming language, such as C#.</span></span> <span data-ttu-id="6ad05-127">[!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーでカスタム タスクにアクセスする場合、タスク用のユーザー インターフェイスを作成して登録できます。</span><span class="sxs-lookup"><span data-stu-id="6ad05-127">If you want to access your custom task in the [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, you can create and register a user interface for the task.</span></span> <span data-ttu-id="6ad05-128">詳細については、「 [カスタム タスクの開発](../extending-packages-custom-objects/task/developing-a-custom-task.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6ad05-128">For more information, see [Developing a Custom Task](../extending-packages-custom-objects/task/developing-a-custom-task.md).</span></span>  
  
## <a name="configuration-of-tasks"></a><span data-ttu-id="6ad05-129">タスクの構成</span><span class="sxs-lookup"><span data-stu-id="6ad05-129">Configuration of Tasks</span></span>  
 <span data-ttu-id="6ad05-130">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージには、1 つのタスクを含めることができます。たとえば、パッケージの実行時にデータベース テーブルのレコードを削除する、SQL 実行タスクを含めます。</span><span class="sxs-lookup"><span data-stu-id="6ad05-130">An [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package can contain a single task, such as an Execute SQL task that deletes records in a database table when the package runs.</span></span> <span data-ttu-id="6ad05-131">ただし、通常のパッケージには複数のタスクが含まれており、各タスクはパッケージ制御フローのコンテキスト内で実行されるように設定されます。</span><span class="sxs-lookup"><span data-stu-id="6ad05-131">However, packages typically contain several tasks, and each task is set to run within the context of the package control flow.</span></span> <span data-ttu-id="6ad05-132">イベント ハンドラーは、ランタイム イベントに応答して実行されるワークフローであり、ここにも複数のタスクを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="6ad05-132">Event handlers, which are workflows that run in response to run-time events, can also have tasks.</span></span>  
  
 <span data-ttu-id="6ad05-133">[!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーを使用してパッケージにタスクを追加する方法の詳細については、「 [制御フローのタスクまたはコンテナーを追加または削除する](add-or-delete-a-task-or-a-container-in-a-control-flow.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6ad05-133">For more information about adding a task to a package using [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, see [Add or Delete a Task or a Container in a Control Flow](add-or-delete-a-task-or-a-container-in-a-control-flow.md).</span></span>  
  
 <span data-ttu-id="6ad05-134">プログラムによってパッケージにタスクを追加する方法の詳細については、「 [プログラムによるタスクの追加](../building-packages-programmatically/adding-tasks-programmatically.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6ad05-134">For more information about adding a task to a package programmatically, see [Adding Tasks Programmatically](../building-packages-programmatically/adding-tasks-programmatically.md).</span></span>  
  
 <span data-ttu-id="6ad05-135">各タスクは、 [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで用意されている、各タスク用のカスタム ダイアログ ボックスを使用して、個別に構成できます。または、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]に含まれる [プロパティ] ウィンドウから構成できます。</span><span class="sxs-lookup"><span data-stu-id="6ad05-135">Each task can be configured individually using the custom dialog boxes for each task that [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer provides, or the Properties window included in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="6ad05-136">パッケージには、6 つの SQL 実行タスクなど、同じ種類の複数のタスクを含めることができ、各タスクは個別に構成できます。</span><span class="sxs-lookup"><span data-stu-id="6ad05-136">A package can include multiple tasks of the same type-for example, six Execute SQL tasks-and each task can be configured differently.</span></span> <span data-ttu-id="6ad05-137">詳細については、「 [タスクまたはコンテナーのプロパティを設定する](../set-the-properties-of-a-task-or-container.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6ad05-137">For more information, see [Set the Properties of a Task or Container](../set-the-properties-of-a-task-or-container.md).</span></span>  
  
## <a name="tasks-connections-and-groups"></a><span data-ttu-id="6ad05-138">タスクの連結とグループ</span><span class="sxs-lookup"><span data-stu-id="6ad05-138">Tasks Connections and Groups</span></span>  
 <span data-ttu-id="6ad05-139">タスクに複数のタスクが含まれる場合、それらのタスクは優先順位制約によって順序が決定され、制御フロー内で連結されます。</span><span class="sxs-lookup"><span data-stu-id="6ad05-139">If the task contains more than one task, they are connected and sequenced in the control flow by precedence constraints.</span></span> <span data-ttu-id="6ad05-140">詳細については、「 [優先順位制約](precedence-constraints.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6ad05-140">For more information, see [Precedence Constraints](precedence-constraints.md).</span></span>  
  
 <span data-ttu-id="6ad05-141">タスクをグループ化して 1 つの作業単位として実行したり、ループ内で繰り返すことができます。</span><span class="sxs-lookup"><span data-stu-id="6ad05-141">Tasks can be grouped together and performed as a single unit of work, or repeated in a loop.</span></span> <span data-ttu-id="6ad05-142">詳細については、「 [Foreach ループ コンテナー](foreach-loop-container.md)」、「 [For ループ コンテナー](for-loop-container.md)」、および「 [シーケンス コンテナー](sequence-container.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6ad05-142">For more information, see [Foreach Loop Container](foreach-loop-container.md), [For Loop Container](for-loop-container.md), and [Sequence Container](sequence-container.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="6ad05-143">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="6ad05-143">Related Tasks</span></span>  
 [<span data-ttu-id="6ad05-144">制御フローのタスクまたはコンテナーを追加または削除する</span><span class="sxs-lookup"><span data-stu-id="6ad05-144">Add or Delete a Task or a Container in a Control Flow</span></span>](add-or-delete-a-task-or-a-container-in-a-control-flow.md)  
  
  
