---
title: プログラムによるパッケージの実行と管理 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
ms.assetid: 1a08c75e-ce8c-45ee-81bd-32248bbdb2b2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0b07b0b98674fa17891dbbcb01ec42934c2a72e6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714518"
---
# <a name="running-and-managing-packages-programmatically"></a><span data-ttu-id="f126f-102">プログラムによるパッケージの実行と管理</span><span class="sxs-lookup"><span data-stu-id="f126f-102">Running and Managing Packages Programmatically</span></span>
  <span data-ttu-id="f126f-103">開発環境以外で [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージを管理および実行する必要がある場合は、プログラムでパッケージを操作できます。</span><span class="sxs-lookup"><span data-stu-id="f126f-103">If you need manage and run [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages outside the development environment, you can manipulate packages programmatically.</span></span> <span data-ttu-id="f126f-104">その場合、次に示すいくつかの方法があります。</span><span class="sxs-lookup"><span data-stu-id="f126f-104">In this approach, you have a range of options:</span></span>  
  
-   <span data-ttu-id="f126f-105">既存のパッケージを読み込んで、変更せずに実行します。</span><span class="sxs-lookup"><span data-stu-id="f126f-105">Load and run an existing package without modification.</span></span>  
  
-   <span data-ttu-id="f126f-106">既存のパッケージを読み込み、再構成 (異なるデータ ソースなどに対して) してから実行します。</span><span class="sxs-lookup"><span data-stu-id="f126f-106">Load an existing package, reconfigure it (for example, for a different data source), and run it.</span></span>  
  
-   <span data-ttu-id="f126f-107">新しいパッケージを作成し、オブジェクト単位やプロパティ単位でコンポーネントを追加および構成し、保存してから実行します。</span><span class="sxs-lookup"><span data-stu-id="f126f-107">Create a new package, add and configure components object by object and property by property, save it, and run it.</span></span>  
  
 <span data-ttu-id="f126f-108">数行のコードを記述するだけで、クライアント アプリケーションから既存のパッケージを読み込んで実行することができます。</span><span class="sxs-lookup"><span data-stu-id="f126f-108">You can load and run an existing package from a client application by writing only a few lines of code.</span></span>  
  
 <span data-ttu-id="f126f-109">ここでは、プログラムで既存のパッケージを実行する方法、および他のアプリケーションからデータ フローの出力にアクセスする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f126f-109">This section describes and demonstrates how to run an existing package programmatically and how to access the output of the data flow from other applications.</span></span> <span data-ttu-id="f126f-110">詳細なプログラミング オプションとして、「[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]プログラムによるパッケージの作成[」トピックの説明に従い、1 行ずつプログラムを指定して ](../building-packages-programmatically/building-packages-programmatically.md) パッケージを作成できます。</span><span class="sxs-lookup"><span data-stu-id="f126f-110">As an advanced programming option, you can programmatically create an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package line by line as described in the topic, [Building Packages Programmatically](../building-packages-programmatically/building-packages-programmatically.md).</span></span>  
  
 <span data-ttu-id="f126f-111">また、保存されているパッケージ、実行中のパッケージ、およびパッケージ ロールを管理するためにプログラムによって実行できる他の管理タスクについても説明します。</span><span class="sxs-lookup"><span data-stu-id="f126f-111">This section also discusses other administrative tasks that you can perform programmatically to manage stored packages, running packages, and package roles.</span></span>  
  
## <a name="running-packages-on-the-integration-services-server"></a><span data-ttu-id="f126f-112">Integration Services サーバー上のパッケージの実行</span><span class="sxs-lookup"><span data-stu-id="f126f-112">Running Packages on the Integration Services Server</span></span>  
 <span data-ttu-id="f126f-113">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サーバーにパッケージを配置するときに、<xref:Microsoft.SqlServer.Management.IntegrationServices> 名前空間を使用してパッケージをプログラムで実行できます。</span><span class="sxs-lookup"><span data-stu-id="f126f-113">When you deploy packages to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server, you can run the packages programmatically by using the <xref:Microsoft.SqlServer.Management.IntegrationServices> namespace.</span></span> <span data-ttu-id="f126f-114">Microsoft.SqlServer.Management.IntegrationServices アセンブリは、.NET Framework 3.5 でコンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="f126f-114">The Microsoft.SqlServer.Management.IntegrationServices assembly is compiled with .NET Framework 3.5.</span></span> <span data-ttu-id="f126f-115">.NET Framework 4.0 アプリケーションを構築する場合は、プロジェクト ファイルに直接アセンブリ参照を追加する必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="f126f-115">If you are building a .NET Framework 4.0 application, you might need to add the assembly reference directly to your project file.</span></span>  
  
 <span data-ttu-id="f126f-116">名前空間を使用して、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サーバーで [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] プロジェクトを配置および管理することもできます。</span><span class="sxs-lookup"><span data-stu-id="f126f-116">You can also use the namespace to deploy and manage [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] projects on the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server.</span></span> <span data-ttu-id="f126f-117">名前空間とコード スニペットの概要については、blogs.msdn.com のブログ エントリ「[SSIS カタログ マネージド オブジェクト モデルの概要](https://techcommunity.microsoft.com/t5/sql-server-integration-services/a-glimpse-of-the-ssis-catalog-managed-object-model/ba-p/387892)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f126f-117">For an overview of the namespace and code snippets, see the blog entry, [A Glimpse of the SSIS Catalog Managed Object Model](https://techcommunity.microsoft.com/t5/sql-server-integration-services/a-glimpse-of-the-ssis-catalog-managed-object-model/ba-p/387892), on blogs.msdn.com.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f126f-118">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="f126f-118">In This Section</span></span>  
 [<span data-ttu-id="f126f-119">ローカル実行とリモート実行の相違点について</span><span class="sxs-lookup"><span data-stu-id="f126f-119">Understanding the Differences between Local and Remote Execution</span></span>](../run-manage-packages-programmatically/understanding-the-differences-between-local-and-remote-execution.md)  
 <span data-ttu-id="f126f-120">パッケージをローカルで実行する場合とサーバーで実行する場合の重要な違いについて説明します。</span><span class="sxs-lookup"><span data-stu-id="f126f-120">Discusses critical differences between executing a package locally or on the server.</span></span>  
  
 [<span data-ttu-id="f126f-121">プログラムによるローカル パッケージの読み込みと実行</span><span class="sxs-lookup"><span data-stu-id="f126f-121">Loading and Running a Local Package Programmatically</span></span>](../run-manage-packages-programmatically/loading-and-running-a-local-package-programmatically.md)  
 <span data-ttu-id="f126f-122">ローカル コンピューターのクライアント アプリケーションから既存のパッケージを実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f126f-122">Describes how to execute an existing package from a client application on the local computer.</span></span>  
  
 [<span data-ttu-id="f126f-123">プログラムによるリモート パッケージの読み込みと実行</span><span class="sxs-lookup"><span data-stu-id="f126f-123">Loading and Running a Remote Package Programmatically</span></span>](../run-manage-packages-programmatically/loading-and-running-a-remote-package-programmatically.md)  
 <span data-ttu-id="f126f-124">クライアント アプリケーションから既存のパッケージを実行し、パッケージがサーバーで実行できるようにする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f126f-124">Describes how to execute an existing package from a client application and to ensure that the package runs on the server.</span></span>  
  
 [<span data-ttu-id="f126f-125">ローカル パッケージの出力の読み込み</span><span class="sxs-lookup"><span data-stu-id="f126f-125">Loading the Output of a Local Package</span></span>](../run-manage-packages-programmatically/loading-the-output-of-a-local-package.md)  
 <span data-ttu-id="f126f-126">ローカル コンピューターでパッケージを実行し、DataReader 変換先および DtsClient 名前空間を使用して、データ フローの出力をクライアント アプリケーションに読み込む方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f126f-126">Describes how to execute a package on the local computer and how to load the data flow output into a client application by using the DataReader destination and the DtsClient namespace.</span></span>  
  
 [<span data-ttu-id="f126f-127">プログラムによる使用可能なパッケージの列挙</span><span class="sxs-lookup"><span data-stu-id="f126f-127">Enumerating Available Packages Programmatically</span></span>](../run-manage-packages-programmatically/enumerating-available-packages-programmatically.md)  
 <span data-ttu-id="f126f-128">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サービスによって管理されている使用可能なパッケージを検出する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f126f-128">Describes how to discover available packages that are managed by the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] service.</span></span>  
  
 [<span data-ttu-id="f126f-129">プログラムによるパッケージとフォルダーの管理</span><span class="sxs-lookup"><span data-stu-id="f126f-129">Managing Packages and Folders Programmatically</span></span>](../run-manage-packages-programmatically/managing-packages-and-folders-programmatically.md)  
 <span data-ttu-id="f126f-130">パッケージとフォルダーを作成、名前変更、および削除する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f126f-130">Describes how to create, rename, and delete both packages and folders.</span></span>  
  
 [<span data-ttu-id="f126f-131">プログラムによるパッケージの実行の管理</span><span class="sxs-lookup"><span data-stu-id="f126f-131">Managing Running Packages Programmatically</span></span>](../run-manage-packages-programmatically/managing-running-packages-programmatically.md)  
 <span data-ttu-id="f126f-132">現在実行中のパッケージの一覧表示、プロパティの分析、および実行中のパッケージの停止方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f126f-132">Describes how to list packages that are currently running, examine their properties, and stop a running package.</span></span>  
  
 [<span data-ttu-id="f126f-133">プログラムによるパッケージのロールの管理 (SSIS Service)</span><span class="sxs-lookup"><span data-stu-id="f126f-133">Managing Package Roles Programmatically &#40;SSIS Service&#41;</span></span>](../run-manage-packages-programmatically/managing-package-roles-programmatically-ssis-service.md)  
 <span data-ttu-id="f126f-134">パッケージまたはフォルダーに割り当てられているロールに関する情報を取得または設定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f126f-134">Describes how to get or set information about the roles assigned to a package or a folder.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="f126f-135">リファレンス</span><span class="sxs-lookup"><span data-stu-id="f126f-135">Reference</span></span>  
 [<span data-ttu-id="f126f-136">Integration Services のエラーとメッセージのリファレンス</span><span class="sxs-lookup"><span data-stu-id="f126f-136">Integration Services Error and Message Reference</span></span>](../integration-services-error-and-message-reference.md)  
 <span data-ttu-id="f126f-137">事前に定義されている [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] エラー コードと、そのシンボル名および説明の一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="f126f-137">Lists the predefined [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] error codes with their symbolic names and descriptions.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="f126f-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="f126f-138">Related Sections</span></span>  
 [<span data-ttu-id="f126f-139">スクリプトによるパッケージの拡張</span><span class="sxs-lookup"><span data-stu-id="f126f-139">Extending Packages with Scripting</span></span>](../extending-packages-scripting/extending-packages-with-scripting.md)  
 <span data-ttu-id="f126f-140">スクリプト タスクを使用した制御フローの拡張方法と、スクリプト コンポーネントを使用したデータ フローの拡張方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f126f-140">Discusses how to extend the control flow by using the Script task, and how to extend the data flow by using the Script component.</span></span>  
  
 [<span data-ttu-id="f126f-141">カスタム オブジェクトを使用したパッケージの拡張</span><span class="sxs-lookup"><span data-stu-id="f126f-141">Extending Packages with Custom Objects</span></span>](../extending-packages-custom-objects/extending-packages-with-custom-objects.md)  
 <span data-ttu-id="f126f-142">複数のパッケージで使用するプログラム カスタム タスク、データ フロー コンポーネント、およびその他のパッケージ オブジェクトを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f126f-142">Discusses how to create program custom tasks, data flow components, and other package objects for use in multiple packages.</span></span>  
  
 [<span data-ttu-id="f126f-143">プログラムによるパッケージの作成</span><span class="sxs-lookup"><span data-stu-id="f126f-143">Building Packages Programmatically</span></span>](../building-packages-programmatically/building-packages-programmatically.md)  
 <span data-ttu-id="f126f-144">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージをプログラムで作成、構成、および保存する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f126f-144">Discusses how to create, configure, and save [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages programmatically.</span></span>  
  
<span data-ttu-id="f126f-145">![Integration Services アイコン (小)](../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="f126f-145">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="f126f-146">[!INCLUDE[msCoName](../../includes/msconame-md.md)] が提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="f126f-146">For the latest downloads, articles, samples, and videos from [!INCLUDE[msCoName](../../includes/msconame-md.md)], as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="f126f-147">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="f126f-147">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="f126f-148">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="f126f-148">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f126f-149">参照</span><span class="sxs-lookup"><span data-stu-id="f126f-149">See Also</span></span>  
 [<span data-ttu-id="f126f-150">SQL Server Integration Services</span><span class="sxs-lookup"><span data-stu-id="f126f-150">SQL Server Integration Services</span></span>](../sql-server-integration-services.md)  
  
  
