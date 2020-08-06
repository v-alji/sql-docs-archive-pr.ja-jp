---
title: リモート サーバー上での SQL Server エージェントを使用したパッケージの負荷分散 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- load-balancing [Integration Services]
- parent packages [Integration Services]
- SQL Server Agent [Integration Services]
ms.assetid: 9281c5f8-8da3-4ae8-8142-53c5919a4cfe
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ea7b132d8cf86d2f211da25989df937d0db34ab2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642156"
---
# <a name="load-balancing-packages-on-remote-servers-by-using-sql-server-agent"></a><span data-ttu-id="a8ab5-102">リモート サーバー上での SQL Server エージェントを使用したパッケージの負荷分散</span><span class="sxs-lookup"><span data-stu-id="a8ab5-102">Load-Balancing Packages on Remote Servers by Using SQL Server Agent</span></span>
  <span data-ttu-id="a8ab5-103">実行する必要のあるパッケージが数多くある場合、使用可能な他のサーバーでパッケージを実行すると便利です。</span><span class="sxs-lookup"><span data-stu-id="a8ab5-103">When many packages have to be run, it is convenient to use other servers that are available.</span></span> <span data-ttu-id="a8ab5-104">すべてのパッケージを 1 つの親パッケージで管理している場合に、他のサーバーを使用してパッケージを実行するこの方法を、負荷分散といいます。</span><span class="sxs-lookup"><span data-stu-id="a8ab5-104">This method of using other servers to run packages when the packages are all under the control of one parent package is called load balancing.</span></span> <span data-ttu-id="a8ab5-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] の負荷分散は、手動による方法であり、パッケージの所有者が構築する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a8ab5-105">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], load balancing is a manual procedure that must be architected by the owners of the packages.</span></span> <span data-ttu-id="a8ab5-106">負荷分散は、サーバーで自動的には実行されません。</span><span class="sxs-lookup"><span data-stu-id="a8ab5-106">Load balancing is not performed automatically by the servers.</span></span> <span data-ttu-id="a8ab5-107">また、リモート サーバーで実行するパッケージは、他のパッケージ内の個別のタスクではなく、完全なパッケージである必要があります。</span><span class="sxs-lookup"><span data-stu-id="a8ab5-107">Also, the packages that are run on the remote servers must be whole packages, not individual tasks in other packages.</span></span>  
  
 <span data-ttu-id="a8ab5-108">負荷分散は、次のようなシナリオで役に立ちます。</span><span class="sxs-lookup"><span data-stu-id="a8ab5-108">Load balancing is useful in the following scenarios:</span></span>  
  
-   <span data-ttu-id="a8ab5-109">複数のパッケージを同時実行できる。</span><span class="sxs-lookup"><span data-stu-id="a8ab5-109">Packages can run at the same time.</span></span>  
  
-   <span data-ttu-id="a8ab5-110">個々のパッケージが大きく、順番に実行すると、処理許容時間を超えて実行される可能性がある。</span><span class="sxs-lookup"><span data-stu-id="a8ab5-110">Packages are large and, if run sequentially, can run longer than the time allowed for processing.</span></span>  
  
 <span data-ttu-id="a8ab5-111">管理者や設計者は、処理に他のサーバーを使用することに利点があるかどうかを判断できます。</span><span class="sxs-lookup"><span data-stu-id="a8ab5-111">Administrators and architects can determine whether using additional servers for processing would benefit their processes.</span></span>  
  
## <a name="illustration-of-load-balancing"></a><span data-ttu-id="a8ab5-112">負荷分散の図</span><span class="sxs-lookup"><span data-stu-id="a8ab5-112">Illustration of Load-Balancing</span></span>  
 <span data-ttu-id="a8ab5-113">次の図は、サーバー上の親パッケージを示します。</span><span class="sxs-lookup"><span data-stu-id="a8ab5-113">The following diagram shows a parent package on a server.</span></span> <span data-ttu-id="a8ab5-114">親パッケージには、SQL Server エージェント ジョブの実行タスクが複数含まれています。</span><span class="sxs-lookup"><span data-stu-id="a8ab5-114">The parent package contains multiple Execute SQL Job Agent tasks.</span></span> <span data-ttu-id="a8ab5-115">親パッケージ内の各タスクは、リモート サーバー上の SQL Server エージェントを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="a8ab5-115">Each task in the parent package calls a SQL Server Agent on a remote server.</span></span> <span data-ttu-id="a8ab5-116">これらのリモート サーバーには、そのサーバー上のパッケージを呼び出すステップを含む SQL Server エージェント ジョブがあります。</span><span class="sxs-lookup"><span data-stu-id="a8ab5-116">Those remote servers contain SQL Server Agent jobs that include a step that calls a package on that server.</span></span>  
  
 <span data-ttu-id="a8ab5-117">![SSIS 負荷分散アーキテクチャの概要](../media/loadbalancingoverview.gif "SSIS 負荷分散アーキテクチャの概要")</span><span class="sxs-lookup"><span data-stu-id="a8ab5-117">![Overview of SSIS load balancing architecture](../media/loadbalancingoverview.gif "Overview of SSIS load balancing architecture")</span></span>  
  
 <span data-ttu-id="a8ab5-118">このアーキテクチャで負荷分散に必要な手順は、新しい概念ではありません。</span><span class="sxs-lookup"><span data-stu-id="a8ab5-118">The steps required for load balancing in this architecture are not new concepts.</span></span> <span data-ttu-id="a8ab5-119">負荷分散は、既存の概念と一般的な SSIS オブジェクトを新しい方法で使用して実現されています。</span><span class="sxs-lookup"><span data-stu-id="a8ab5-119">Instead, load balancing is achieved by using existing concepts and common SSIS objects in a new way.</span></span>  
  
## <a name="execution-of-packages-on-a-remote-instance-by-using-sql-server-agent"></a><span data-ttu-id="a8ab5-120">リモート インスタンスで SQL Server エージェントを使用したパッケージの実行</span><span class="sxs-lookup"><span data-stu-id="a8ab5-120">Execution of Packages on a Remote Instance by using SQL Server Agent</span></span>  
 <span data-ttu-id="a8ab5-121">リモート パッケージの実行の基本的なアーキテクチャでは、中心となるパッケージは、他のリモート パッケージを制御する SQL Server のインスタンスに常駐します。</span><span class="sxs-lookup"><span data-stu-id="a8ab5-121">In the basic architecture for remote package execution, a central package resides on the instance of SQL Server that controls the other remote packages.</span></span> <span data-ttu-id="a8ab5-122">図では、SSIS Parent という名前の中心となるパッケージを示しています。</span><span class="sxs-lookup"><span data-stu-id="a8ab5-122">The diagram shows this central package, named the SSIS Parent.</span></span> <span data-ttu-id="a8ab5-123">この親パッケージが常駐するインスタンスによって、子パッケージを実行する SQL Server エージェント ジョブの実行が制御されます。</span><span class="sxs-lookup"><span data-stu-id="a8ab5-123">The instance where this parent package resides controls execution of the SQL Server Agent jobs that run the child packages.</span></span> <span data-ttu-id="a8ab5-124">子パッケージの実行は、リモート サーバーの SQL Server エージェントで制御される固定的なスケジュールに基づくわけではありません。</span><span class="sxs-lookup"><span data-stu-id="a8ab5-124">The child packages are not run according to a fixed schedule controlled by the SQL Server Agent on the remote server.</span></span> <span data-ttu-id="a8ab5-125">子パッケージは、親パッケージから呼び出されたときに SQL Server エージェントによって開始され、SQL Server エージェントが常駐している同じ SQL Server のインスタンスで実行されます。</span><span class="sxs-lookup"><span data-stu-id="a8ab5-125">Instead, the child packages are started by the SQL Server Agent when called by the parent package and are run on the same instance of SQL Server on which the SQL Server Agent resides.</span></span>  
  
 <span data-ttu-id="a8ab5-126">SQL Server エージェントを使用してリモート パッケージを実行するには、あらかじめ親パッケージと子パッケージを構成し、子パッケージを制御する SQL Server エージェント ジョブをセットアップしておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="a8ab5-126">Before you can run a remote package by using SQL Server Agent, you must configure the parent and child packages and set up the SQL Server Agent jobs that control the child packages.</span></span> <span data-ttu-id="a8ab5-127">次のセクションでは、リモート サーバーで実行するパッケージの作成、構成、実行、および管理方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a8ab5-127">The following sections provide more information about how to create, configure, run, and maintain packages that run on remote servers.</span></span> <span data-ttu-id="a8ab5-128">このプロセスには、いくつかの手順があります。</span><span class="sxs-lookup"><span data-stu-id="a8ab5-128">There are several steps to this process:</span></span>  
  
-   <span data-ttu-id="a8ab5-129">子パッケージを作成してリモート サーバーにインストールします。</span><span class="sxs-lookup"><span data-stu-id="a8ab5-129">Creating the child packages and installing them on remote servers.</span></span>  
  
-   <span data-ttu-id="a8ab5-130">パッケージを実行するリモート インスタンスで SQL Server エージェント ジョブを作成します。</span><span class="sxs-lookup"><span data-stu-id="a8ab5-130">Creating the SQL Server Agent jobs on the remote instances that will run the packages.</span></span>  
  
-   <span data-ttu-id="a8ab5-131">親パッケージを作成します。</span><span class="sxs-lookup"><span data-stu-id="a8ab5-131">Creating the parent package.</span></span>  
  
-   <span data-ttu-id="a8ab5-132">子パッケージ用のログ記録シナリオを決定します。</span><span class="sxs-lookup"><span data-stu-id="a8ab5-132">Determine the logging scenario for the child packages.</span></span>  
  
 <span data-ttu-id="a8ab5-133">次の表に、このプロセスを説明するトピックへのリンクを示します。</span><span class="sxs-lookup"><span data-stu-id="a8ab5-133">The following table provides links to topics that guide you through the process.</span></span>  
  
|<span data-ttu-id="a8ab5-134">トピック</span><span class="sxs-lookup"><span data-stu-id="a8ab5-134">Topic</span></span>|<span data-ttu-id="a8ab5-135">説明</span><span class="sxs-lookup"><span data-stu-id="a8ab5-135">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="a8ab5-136">子パッケージの実装</span><span class="sxs-lookup"><span data-stu-id="a8ab5-136">Implementation of Child Packages</span></span>](../implementation-of-child-packages.md)|<span data-ttu-id="a8ab5-137">パッケージのインストールおよびパッケージを実行する SQL Server エージェント ジョブの作成について説明します。</span><span class="sxs-lookup"><span data-stu-id="a8ab5-137">Describes the installation of packages, and creation of the SQL Server Agent jobs to run the packages.</span></span>|  
|[<span data-ttu-id="a8ab5-138">親パッケージの実装</span><span class="sxs-lookup"><span data-stu-id="a8ab5-138">Implementation of the Parent Package</span></span>](../implementation-of-the-parent-package.md)|<span data-ttu-id="a8ab5-139">SQL Server エージェント ジョブの実行タスクを多数含む親パッケージの作成について説明します。</span><span class="sxs-lookup"><span data-stu-id="a8ab5-139">Describes the creation of the parent package that contains many Execute SQL Server Agent Job tasks.</span></span> <span data-ttu-id="a8ab5-140">各タスクが子パッケージの 1 つを実行します。</span><span class="sxs-lookup"><span data-stu-id="a8ab5-140">Each task runs one of the child packages.</span></span>|  
|[<span data-ttu-id="a8ab5-141">リモート サーバー上の負荷分散パッケージのログ記録</span><span class="sxs-lookup"><span data-stu-id="a8ab5-141">Logging for Load Balanced Packages on Remote Servers</span></span>](../logging-for-load-balanced-packages-on-remote-servers.md)|<span data-ttu-id="a8ab5-142">リモート パッケージ用のログ記録シナリオについて説明します。</span><span class="sxs-lookup"><span data-stu-id="a8ab5-142">Describes the logging scenario for the remote packages.</span></span>|  
  
## <a name="related-tasks"></a><span data-ttu-id="a8ab5-143">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="a8ab5-143">Related Tasks</span></span>  
 [<span data-ttu-id="a8ab5-144">SQL Server エージェントを使用したパッケージのスケジュール設定</span><span class="sxs-lookup"><span data-stu-id="a8ab5-144">Schedule a Package by using SQL Server Agent</span></span>](../schedule-a-package-by-using-sql-server-agent.md)  
  
  
