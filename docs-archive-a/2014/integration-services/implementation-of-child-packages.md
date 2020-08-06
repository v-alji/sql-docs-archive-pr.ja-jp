---
title: 子パッケージの実装 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- child packages
ms.assetid: ab0c09d7-ce2e-487d-a1ed-a4b5adb6cc01
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f4fa4fa7c523c55c595341c7aee6a530c5918a34
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714522"
---
# <a name="implementation-of-child-packages"></a><span data-ttu-id="97b36-102">子パッケージの実装</span><span class="sxs-lookup"><span data-stu-id="97b36-102">Implementation of Child Packages</span></span>
  <span data-ttu-id="97b36-103">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]を使用して負荷分散を実装すると、子パッケージが他のサーバーにインストールされ、利用可能な CPU 時間またはサーバー時間を活用することができます。</span><span class="sxs-lookup"><span data-stu-id="97b36-103">When you implement load balancing using [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], child packages are installed on other servers to take advantage of the available CPU or server time.</span></span> <span data-ttu-id="97b36-104">子パッケージを作成および実行するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="97b36-104">To create and run the child packages requires the following steps:</span></span>  
  
-   <span data-ttu-id="97b36-105">子パッケージをデザインします。</span><span class="sxs-lookup"><span data-stu-id="97b36-105">Designing the child packages.</span></span>  
  
-   <span data-ttu-id="97b36-106">パッケージをリモート サーバーに移動します。</span><span class="sxs-lookup"><span data-stu-id="97b36-106">Moving the packages to the remote server.</span></span>  
  
-   <span data-ttu-id="97b36-107">子パッケージを実行するステップを含む SQL Server エージェント ジョブをリモート サーバー上に作成します。</span><span class="sxs-lookup"><span data-stu-id="97b36-107">Creating a SQL Server Agent Job on the remote server that contains a step that runs the child package.</span></span>  
  
-   <span data-ttu-id="97b36-108">SQL Server エージェント ジョブと子パッケージをテストおよびデバッグします。</span><span class="sxs-lookup"><span data-stu-id="97b36-108">Testing and debugging the SQL Server Agent Job and child packages.</span></span>  
  
 <span data-ttu-id="97b36-109">子パッケージをデザインする際、子パッケージにはデザイン上の制限がないため、目的の機能をすべて追加できます。</span><span class="sxs-lookup"><span data-stu-id="97b36-109">When you design the child packages, the packages have no limitations in their design, and you can put in any functionality you desire.</span></span> <span data-ttu-id="97b36-110">ただし、パッケージからデータにアクセスする場合は、パッケージを実行するサーバーからそのデータにアクセスできなければなりません。</span><span class="sxs-lookup"><span data-stu-id="97b36-110">However, if the package accesses data, you must ensure that the server that runs the package has access to the data.</span></span>  
  
 <span data-ttu-id="97b36-111">子パッケージを実行する親パッケージを識別するには、 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] のソリューション エクスプローラーでパッケージを右クリックし、 **[エントリ ポイント パッケージ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="97b36-111">To identify the parent package that executes child packages, in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] right click the package in Solution Explorer and then click **Entry-point Package**.</span></span>  
  
 <span data-ttu-id="97b36-112">子パッケージをデザインしたら、次に、そのパッケージをリモート サーバーに配置します。</span><span class="sxs-lookup"><span data-stu-id="97b36-112">After the child packages have been designed, the next step is to deploy them on the remote servers.</span></span>  
  
## <a name="moving-the-child-package-to-the-remote-instance"></a><span data-ttu-id="97b36-113">リモート インスタンスへの子パッケージの移動</span><span class="sxs-lookup"><span data-stu-id="97b36-113">Moving the Child Package to the Remote Instance</span></span>  
 <span data-ttu-id="97b36-114">パッケージを他のサーバーに移動する方法は何種類かあります。</span><span class="sxs-lookup"><span data-stu-id="97b36-114">There are multiple ways to move packages to other servers.</span></span> <span data-ttu-id="97b36-115">次の 2 つの方法をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="97b36-115">The two suggested methods are:</span></span>  
  
-   <span data-ttu-id="97b36-116">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]を使用してパッケージをエクスポートします。</span><span class="sxs-lookup"><span data-stu-id="97b36-116">Exporting packages by using [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
-   <span data-ttu-id="97b36-117">パッケージを配置します。パッケージを配置するには、配置するパッケージを含むプロジェクトの配置ユーティリティをビルドした後、パッケージ インストール ウィザードを実行し、パッケージをファイル システムまたは [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]のインスタンスにインストールします。</span><span class="sxs-lookup"><span data-stu-id="97b36-117">Deploying packages by building a deployment utility for the project that contains the packages you want to deploy, and then running the Package Installation Wizard to install the packages to the file system or to an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="97b36-118">詳細については、「[パッケージの配置 &#40;SSIS&#41;](packages/legacy-package-deployment-ssis.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="97b36-118">For more information, see [Package Deployment &#40;SSIS&#41;](packages/legacy-package-deployment-ssis.md).</span></span>  
  
 <span data-ttu-id="97b36-119">この配置は、使用する各リモート サーバーに対してそれぞれ行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="97b36-119">You must repeat the deployment to each remote server you want to use.</span></span>  
  
## <a name="creating-the-sql-server-agent-jobs"></a><span data-ttu-id="97b36-120">SQL Server エージェント ジョブの作成</span><span class="sxs-lookup"><span data-stu-id="97b36-120">Creating the SQL Server Agent Jobs</span></span>  
 <span data-ttu-id="97b36-121">子パッケージをさまざまなサーバーに配置した後、子パッケージを格納した各サーバー上に SQL Server エージェント ジョブを作成します。</span><span class="sxs-lookup"><span data-stu-id="97b36-121">After the child packages have been deployed to the various servers, create a SQL Server Agent job on each server that contains a child package.</span></span> <span data-ttu-id="97b36-122">SQL Server エージェント ジョブには、ジョブ エージェントの呼び出し時に子パッケージを実行するステップが含まれています。</span><span class="sxs-lookup"><span data-stu-id="97b36-122">The SQL Server Agent job contains a step that runs the child package when the job agent is called.</span></span> <span data-ttu-id="97b36-123">SQL Server エージェント ジョブは定期ジョブではありません。つまり、子パッケージは、親パッケージによって呼び出されたときだけ実行されます。</span><span class="sxs-lookup"><span data-stu-id="97b36-123">The SQL Server Agent jobs are not scheduled jobs; they run the child packages only when they are called by the parent package.</span></span> <span data-ttu-id="97b36-124">ジョブの成功や失敗に関する親パッケージへの通知は、SQL Server エージェント ジョブの成功や失敗、およびそのジョブが正常に呼び出されたかどうかを表すものであり、子パッケージが実行されたかどうかや、その成功や失敗については反映されません。</span><span class="sxs-lookup"><span data-stu-id="97b36-124">Notification of success or failure of the job back to the parent package reflects the success or failure of the SQL Server Agent job and whether it was called successfully, not the success or failure of the child package or whether it was executed.</span></span>  
  
## <a name="debugging-the-sql-server-agent-jobs-and-child-packages"></a><span data-ttu-id="97b36-125">SQL Server エージェント ジョブと子パッケージのデバッグ</span><span class="sxs-lookup"><span data-stu-id="97b36-125">Debugging the SQL Server Agent Jobs and Child Packages</span></span>  
 <span data-ttu-id="97b36-126">次のいずれかの方法を使用して、SQL Server エージェント ジョブとその子パッケージをテストできます。</span><span class="sxs-lookup"><span data-stu-id="97b36-126">You can test the SQL Server Agent jobs and their child packages by using one of the following methods:</span></span>  
  
-   <span data-ttu-id="97b36-127">[デバッグ **] [**  /  **デバッグなしで開始**] をクリックして、SSIS デザイナーで各子パッケージを実行します。</span><span class="sxs-lookup"><span data-stu-id="97b36-127">Running each child package in SSIS Designer, by clicking **Debug** / **Start Without Debugging**.</span></span>  
  
-   <span data-ttu-id="97b36-128">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]を使用してリモート コンピューター上の個別の SQL Server エージェント ジョブを実行し、パッケージが実行されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="97b36-128">Running the individual SQL Server Agent job on the remote computer by using [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], to make sure that the package runs.</span></span>  
  
 <span data-ttu-id="97b36-129">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エージェントのジョブから実行するパッケージのトラブルシューティング方法については、 [サポート技術情報の「](https://support.microsoft.com/kb/918760) SQL Server エージェントのジョブ ステップから SSIS パッケージを呼び出したときに SSIS パッケージが実行されない [!INCLUDE[msCoName](../includes/msconame-md.md)] 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="97b36-129">For information about how to troubleshoot packages that you run from [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent jobs, see [An SSIS package does not run when you call the SSIS package from a SQL Server Agent job step](https://support.microsoft.com/kb/918760) in the [!INCLUDE[msCoName](../includes/msconame-md.md)] Support Knowledge Base.</span></span>  
  
 <span data-ttu-id="97b36-130">SQL Server エージェントは、ジョブ ステップを実行するたびに、プロキシに対してサブシステムのアクセス許可を確認し、プロキシへのアクセスを確立します。</span><span class="sxs-lookup"><span data-stu-id="97b36-130">The SQL Server Agent checks subsystem access for a proxy and gives access to the proxy every time the job step runs.</span></span>  
  
 <span data-ttu-id="97b36-131">プロキシは、 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]で作成できます。</span><span class="sxs-lookup"><span data-stu-id="97b36-131">You can create a proxy in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="97b36-132">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="97b36-132">Related Tasks</span></span>  
  
-   [<span data-ttu-id="97b36-133">SQL Server Management Studio を使用した SSIS サーバーでのパッケージの実行</span><span class="sxs-lookup"><span data-stu-id="97b36-133">Run a Package on the SSIS Server Using SQL Server Management Studio</span></span>](run-a-package-on-the-ssis-server-using-sql-server-management-studio.md)  
  
## <a name="related-content"></a><span data-ttu-id="97b36-134">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="97b36-134">Related Content</span></span>  
  
-   <span data-ttu-id="97b36-135">ブログ記事「 [SSIS: 親パッケージの変数へのアクセス](https://andyleonard.blog/2015/08/ssis-design-pattern-access-parent-variables-from-a-child-package-in-the-ssis-catalog/)」 (andyleonard) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="97b36-135">Blog entry, [SSIS: Accessing variables in a parent package](https://andyleonard.blog/2015/08/ssis-design-pattern-access-parent-variables-from-a-child-package-in-the-ssis-catalog/), on andyleonard.blog.</span></span>  
  
-   <span data-ttu-id="97b36-136">記事「[パッケージ実行タスク](../integration-services/control-flow/execute-package-task.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="97b36-136">Article, [Execute Package Task](../integration-services/control-flow/execute-package-task.md).</span></span>  
  
  
