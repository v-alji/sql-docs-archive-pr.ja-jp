---
title: dtexec ユーティリティ | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 7b6867fa-1039-49b3-90fb-85b84678a612
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 45820aa673f31ae9cea7d1f2f4e8b61d63b8670c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718536"
---
# <a name="dtexec-utility"></a><span data-ttu-id="05655-102">dtexec ユーティリティ</span><span class="sxs-lookup"><span data-stu-id="05655-102">dtexec Utility</span></span>
  <span data-ttu-id="05655-103">`dtexec`コマンドプロンプトユーティリティは、パッケージの構成と実行に使用され [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="05655-103">The `dtexec` command prompt utility is used to configure and execute [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages.</span></span> <span data-ttu-id="05655-104">`dtexec` ユーティリティを使用すると、パラメーター、接続、プロパティ、変数、ログ記録、進行状況インジケーターなど、パッケージの構成と実行に関するすべての機能にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="05655-104">The `dtexec` utility provides access to all the package configuration and execution features, such as parameters, connections, properties, variables, logging, and progress indicators.</span></span> <span data-ttu-id="05655-105">`dtexec`ユーティリティを使用すると、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サーバー、ispac プロジェクトファイル、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベース、 [!INCLUDE[ssIS](../../includes/ssis-md.md)] パッケージストア、およびファイルシステムからパッケージを読み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="05655-105">The `dtexec` utility lets you load packages from these sources: the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server, an .ispac project file, a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database, the [!INCLUDE[ssIS](../../includes/ssis-md.md)] Package Store, and the file system.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="05655-106">[!INCLUDE[ssISversion11](../../includes/ssisversion11-md.md)] に付属するバージョンの `dtexec` ユーティリティを使用して [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] パッケージまたは [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] パッケージを実行すると、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] によってパッケージが一時的に [!INCLUDE[ssISversion11](../../includes/ssisversion11-md.md)] にアップグレードされます。</span><span class="sxs-lookup"><span data-stu-id="05655-106">When you use the version of the `dtexec` utility that comes with [!INCLUDE[ssISversion11](../../includes/ssisversion11-md.md)] to run a [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] or a [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] package, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] temporarily upgrades the package to [!INCLUDE[ssISversion11](../../includes/ssisversion11-md.md)].</span></span> <span data-ttu-id="05655-107">ただし、`dtexec` ユーティリティを使用して、このようなアップグレードによる変更を保存することはできません。</span><span class="sxs-lookup"><span data-stu-id="05655-107">However, you cannot use the `dtexec` utility to save these upgraded changes.</span></span> <span data-ttu-id="05655-108">パッケージをに永続的にアップグレードする方法の詳細について [!INCLUDE[ssISversion11](../../includes/ssisversion11-md.md)] は、「 [Integration Services パッケージのアップグレード](../install-windows/upgrade-integration-services-packages.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="05655-108">For more information about how to permanently upgrade a package to [!INCLUDE[ssISversion11](../../includes/ssisversion11-md.md)], see [Upgrade Integration Services Packages](../install-windows/upgrade-integration-services-packages.md).</span></span>  
  
 <span data-ttu-id="05655-109">このトピックのセクションは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="05655-109">This topic includes the following sections:</span></span>  
  
-   [<span data-ttu-id="05655-110">Integration Services サーバーとプロジェクト ファイル</span><span class="sxs-lookup"><span data-stu-id="05655-110">Integration Services Server and Project File</span></span>](#server)  
  
-   [<span data-ttu-id="05655-111">64 ビット コンピューターでのインストールに関する注意点</span><span class="sxs-lookup"><span data-stu-id="05655-111">Installation Considerations on 64-bit Computers</span></span>](#bit)  
  
-   [<span data-ttu-id="05655-112">サイド バイ サイド インストールを使用しているコンピューターに関する注意点</span><span class="sxs-lookup"><span data-stu-id="05655-112">Considerations on Computers with Side-by-Side Installations</span></span>](#side)  
  
-   [<span data-ttu-id="05655-113">実行のフェーズ</span><span class="sxs-lookup"><span data-stu-id="05655-113">Phases of Execution</span></span>](#phases)  
  
-   [<span data-ttu-id="05655-114">返される終了コード</span><span class="sxs-lookup"><span data-stu-id="05655-114">Exit Codes Returned</span></span>](#exit)  
  
-   [<span data-ttu-id="05655-115">構文規則</span><span class="sxs-lookup"><span data-stu-id="05655-115">Syntax Rules</span></span>](#syntaxRules)  
  
-   [<span data-ttu-id="05655-116">xp_cmdshell での dtexec の使用</span><span class="sxs-lookup"><span data-stu-id="05655-116">Using dtexec from the xp_cmdshell</span></span>](#cmdshell)  
  
-   [<span data-ttu-id="05655-117">構文</span><span class="sxs-lookup"><span data-stu-id="05655-117">Syntax</span></span>](#syntax)  
  
-   [<span data-ttu-id="05655-118">パラメーター</span><span class="sxs-lookup"><span data-stu-id="05655-118">Parameters</span></span>](#parameter)  
  
-   [<span data-ttu-id="05655-119">解説</span><span class="sxs-lookup"><span data-stu-id="05655-119">Remarks</span></span>](#remark)  
  
-   [<span data-ttu-id="05655-120">使用例</span><span class="sxs-lookup"><span data-stu-id="05655-120">Examples</span></span>](#example)  
  
##  <a name="integration-services-server-and-project-file"></a><a name="server"></a> <span data-ttu-id="05655-121">Integration Services サーバーとプロジェクト ファイル</span><span class="sxs-lookup"><span data-stu-id="05655-121">Integration Services Server and Project File</span></span>  
 <span data-ttu-id="05655-122">を使用して `dtexec` サーバーでパッケージを実行すると [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 、はカタログを `dtexec` 呼び出し[ます。 create_execution &#40;ssisdb データベース&#41;](/sql/integration-services/system-stored-procedures/catalog-create-execution-ssisdb-database)、 [catalog. set_execution_parameter_value &#40;ssisdb](/sql/integration-services/system-stored-procedures/catalog-set-execution-parameter-value-ssisdb-database)データベース&#41;および[catalog. start_execution &#40;ssisdb](/sql/integration-services/system-stored-procedures/catalog-start-execution-ssisdb-database)データベース&#41;ストアドプロシージャを実行して、パラメーター値を設定し、実行を開始します。</span><span class="sxs-lookup"><span data-stu-id="05655-122">When you use `dtexec` to run packages on the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server, `dtexec` calls the [catalog.create_execution &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-create-execution-ssisdb-database), [catalog.set_execution_parameter_value &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-set-execution-parameter-value-ssisdb-database) and [catalog.start_execution &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-start-execution-ssisdb-database) stored procedures to create an execution, set parameter values and start the execution.</span></span> <span data-ttu-id="05655-123">すべての実行ログは、関連するビューでサーバーから確認できます。また、 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]で利用可能な標準レポートを使用して確認することもできます。</span><span class="sxs-lookup"><span data-stu-id="05655-123">All execution logs can be seen from the server in the related views or by using standard reports available in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="05655-124">レポートの詳細については、「 [Integration Services サーバーのレポート](../reports-for-the-integration-services-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="05655-124">For more information about the reports, see [Reports for the Integration Services Server](../reports-for-the-integration-services-server.md).</span></span>  
  
 <span data-ttu-id="05655-125">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サーバーでのパッケージの実行例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="05655-125">The following is an example of executing a package on the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server.</span></span>  
  
```  
DTExec /ISSERVER "\SSISDB\folderB\Integration Services Project17\Package.dtsx" /SERVER "." /Envreference 2 /Par "$Project::ProjectParameter(Int32)";1 /Par "Parameter(Int32)";21 /Par "CM.sqlcldb2.SSIS_repro.InitialCatalog";ssisdb /Par "$ServerOption::SYNCHRONIZED(Boolean)";True  
```  
  
 <span data-ttu-id="05655-126">`dtexec` を使用して .ispac プロジェクト ファイルからパッケージを実行する場合の関連オプションは、/Proj[ect] と /Pack[age] です。これらは、プロジェクトのパスとパッケージのストリーム名を指定するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="05655-126">When you use `dtexec` to run a package from the .ispac project file, the related options are: /Proj[ect] and /Pack[age] that are used to specify the project path and package stream name.</span></span> <span data-ttu-id="05655-127">**から** Integration Services プロジェクト変換ウィザード [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]を実行してプロジェクトをプロジェクト配置モデルに変換する場合、ウィザードは .ispac プロジェクト ファイルを生成します。</span><span class="sxs-lookup"><span data-stu-id="05655-127">When you convert a project to the project deployment model by running the **Integration Services Project Conversion Wizard** from [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], the wizard generates an .ispac projec file.</span></span> <span data-ttu-id="05655-128">詳細については、「 [Integration Services サーバーへのプロジェクトの配置](../deploy-projects-to-integration-services-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="05655-128">For more information, see [Deploy Projects to Integration Services Server](../deploy-projects-to-integration-services-server.md).</span></span>  
  
 <span data-ttu-id="05655-129">を `dtexec` サードパーティのスケジューリングツールと共に使用して、サーバーに配置されるパッケージのスケジュールを設定でき [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="05655-129">You can use `dtexec` with third-party scheduling tools to schedule packages that are deployed to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server.</span></span>  
  
##  <a name="installation-considerations-on-64-bit-computers"></a><a name="bit"></a> <span data-ttu-id="05655-130">64 ビット コンピューターでのインストールに関する注意点</span><span class="sxs-lookup"><span data-stu-id="05655-130">Installation Considerations on 64-bit Computers</span></span>  
 <span data-ttu-id="05655-131">64 ビット コンピューターには、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] によって 64 ビット版の `dtexec` ユーティリティ (dtexec.exe) がインストールされます。</span><span class="sxs-lookup"><span data-stu-id="05655-131">On a 64-bit computer, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] installs a 64-bit version of the `dtexec` utility (dtexec.exe).</span></span> <span data-ttu-id="05655-132">特定のパッケージを 32 ビット モードで実行する必要がある場合は、32 ビット版の `dtexec` ユーティリティをインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="05655-132">If you have to run certain packages in 32-bit mode, you will have to install the 32-bit version of the `dtexec` utility.</span></span> <span data-ttu-id="05655-133">32 ビット版の `dtexec` ユーティリティをインストールするには、セットアップ中に [クライアント ツール] または [[!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]] を選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="05655-133">To install the 32-bit version of the `dtexec` utility, you must select either Client Tools or [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] during setup.</span></span>  
  
 <span data-ttu-id="05655-134">既定では、64 ビットと 32 ビットの両方のバージョンの [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] コマンド プロンプト ユーティリティがインストールされている 64 ビット コンピューターでは、コマンド プロンプトで 32 ビット バージョンが実行されます。</span><span class="sxs-lookup"><span data-stu-id="05655-134">By default, a 64-bit computer that has both the 64-bit and 32-bit versions of an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] command prompt utility installed will run the 32-bit version at the command prompt.</span></span> <span data-ttu-id="05655-135">これは、PATH 環境変数で、32 ビット バージョンのディレクトリ パスが 64 ビット バージョンのディレクトリ パスより前に配置されているためです</span><span class="sxs-lookup"><span data-stu-id="05655-135">The 32-bit version runs because the directory path for the 32-bit version appears in the PATH environment variable before the directory path for the 64-bit version.</span></span> <span data-ttu-id="05655-136">(通常、32 ビットのディレクトリ パスは *\<drive>* :\Program Files(x86)\Microsoft SQL Server\110\DTS\Binn で、64 ビットのディレクトリ パスは *\<drive>* :\Program Files\Microsoft SQL Server\110\DTS\Binn です)。</span><span class="sxs-lookup"><span data-stu-id="05655-136">(Typically, the 32-bit directory path is *\<drive>*:\Program Files(x86)\Microsoft SQL Server\110\DTS\Binn, while the 64-bit directory path is *\<drive>*:\Program Files\Microsoft SQL Server\110\DTS\Binn.)</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="05655-137">SQL Server エージェントを使用してユーティリティを実行する場合は、SQL Server エージェントによって 64 ビット バージョンのユーティリティが自動的に使用されます。</span><span class="sxs-lookup"><span data-stu-id="05655-137">If you use SQL Server Agent to run the utility, SQL Server Agent automatically uses the 64-bit version of the utility.</span></span> <span data-ttu-id="05655-138">SQL Server エージェントでは、PATH 環境変数ではなくレジストリを使用してユーティリティの適切な実行可能ファイルが特定されます。</span><span class="sxs-lookup"><span data-stu-id="05655-138">SQL Server Agent uses the registry, not the PATH environment variable, to locate the correct executable for the utility.</span></span>  
  
 <span data-ttu-id="05655-139">コマンド プロンプトで 64 ビット バージョンのユーティリティが実行されるようにするには、次のいずれかの操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="05655-139">To ensure that you run the 64-bit version of the utility at the command prompt, you can take one of the following actions:</span></span>  
  
-   <span data-ttu-id="05655-140">コマンド プロンプト ウィンドウを開いて、64 ビット バージョンのユーティリティが格納されたディレクトリ ( *\<drive>* :\Program Files\Microsoft SQL Server\110\DTS\Binn) に移動し、その場所からユーティリティを実行します。</span><span class="sxs-lookup"><span data-stu-id="05655-140">Open a Command Prompt window, change to the directory that contains the 64-bit version of the utility (*\<drive>*:\Program Files\Microsoft SQL Server\110\DTS\Binn), and then run the utility from that location.</span></span>  
  
-   <span data-ttu-id="05655-141">コマンド プロンプトで、64 ビット バージョンのユーティリティの完全なパス ( *\<drive>* :\Program Files\Microsoft SQL Server\110\DTS\Binn) を入力してユーティリティを実行します。</span><span class="sxs-lookup"><span data-stu-id="05655-141">At the command prompt, run the utility by entering the full path (*\<drive>*:\Program Files\Microsoft SQL Server\110\DTS\Binn) to the 64-bit version of the utility.</span></span>  
  
-   <span data-ttu-id="05655-142">PATH 環境変数で、64 ビットのパス ( *\<drive>* :\Program Files\Microsoft SQL Server\110\DTS\Binn) を、その変数内にある 32 ビットのパス ( *\<drive>* :\ Program Files(x86)\Microsoft SQL Server\110\DTS\Binn) より前に配置してパスの順序を永続的に変更します。</span><span class="sxs-lookup"><span data-stu-id="05655-142">Permanently change the order of the paths in the PATH environment variable by placing the 64-bit path (*\<drive>*:\Program Files\Microsoft SQL Server\110\DTS\Binn) before the 32-bit path (*\<drive>*:\ Program Files(x86)\Microsoft SQL Server\110\DTS\Binn) in the variable.</span></span>  
  
##  <a name="considerations-on-computers-with-side-by-side-installations"></a><a name="side"></a> <span data-ttu-id="05655-143">サイド バイ サイド インストールを使用しているコンピューターに関する注意点</span><span class="sxs-lookup"><span data-stu-id="05655-143">Considerations on Computers with Side-by-Side Installations</span></span>  
 <span data-ttu-id="05655-144">[!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] を、[!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] または [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] がインストールされているコンピューターにインストールすると、複数のバージョンの `dtexec` ユーティリティがインストールされます。</span><span class="sxs-lookup"><span data-stu-id="05655-144">When [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] is installed on a machine that has [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] or [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] installed, multiple versions of the `dtexec` utility are installed.</span></span>  
  
 <span data-ttu-id="05655-145">正しいバージョンのユーティリティを実行していることを確認するには、コマンド プロンプトで完全なパス ( *\<drive>* :\Program Files\Microsoft SQL Server\\<version\>\DTS\Binn) を入力してユーティリティを実行します。</span><span class="sxs-lookup"><span data-stu-id="05655-145">To ensure that you run the correct version of the utility, at the command prompt run the utility by entering the full path (*\<drive>*:\Program Files\Microsoft SQL Server\\<version\>\DTS\Binn).</span></span>  
  
##  <a name="phases-of-execution"></a><a name="phases"></a> <span data-ttu-id="05655-146">実行のフェーズ</span><span class="sxs-lookup"><span data-stu-id="05655-146">Phases of Execution</span></span>  
 <span data-ttu-id="05655-147">このユーティリティの実行には、4 つのフェーズがあります。</span><span class="sxs-lookup"><span data-stu-id="05655-147">The utility has four phases that it proceeds through as it executes.</span></span> <span data-ttu-id="05655-148">それらのフェーズを次に示します。</span><span class="sxs-lookup"><span data-stu-id="05655-148">The phases are as follows:</span></span>  
  
1.  <span data-ttu-id="05655-149">コマンド初期フェーズ:コマンド プロンプトによって、指定されたオプションおよび引数のリストが読み取られます。</span><span class="sxs-lookup"><span data-stu-id="05655-149">Command sourcing phase: The command prompt reads the list of options and arguments that have been specified.</span></span> <span data-ttu-id="05655-150">**/?** オプション</span><span class="sxs-lookup"><span data-stu-id="05655-150">All subsequent phases are skipped if a **/?**</span></span> <span data-ttu-id="05655-151">または **/HELP** オプションが指定されている場合、後続のフェーズはすべてスキップされます。</span><span class="sxs-lookup"><span data-stu-id="05655-151">or **/HELP** option is encountered.</span></span>  
  
2.  <span data-ttu-id="05655-152">パッケージ読み込みフェーズ: `/SQL` 、設定、またはオプション**で指定**されたパッケージ `/DTS` が読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="05655-152">Package load phase: The package specified by the `/SQL`, **/FILE**, or `/DTS` option is loaded.</span></span>  
  
3.  <span data-ttu-id="05655-153">構成フェーズ:オプションは次の順序で処理されます。</span><span class="sxs-lookup"><span data-stu-id="05655-153">Configuration phase: Options are processed in this order:</span></span>  
  
    -   <span data-ttu-id="05655-154">パッケージのフラグ、変数、およびプロパティを設定するオプション</span><span class="sxs-lookup"><span data-stu-id="05655-154">Options that set package flags, variables, and properties.</span></span>  
  
    -   <span data-ttu-id="05655-155">パッケージのバージョン番号およびビルドを確認するオプション</span><span class="sxs-lookup"><span data-stu-id="05655-155">Options that verify the package version and build.</span></span>  
  
    -   <span data-ttu-id="05655-156">レポートなど、ユーティリティの実行時の動作を構成するオプション</span><span class="sxs-lookup"><span data-stu-id="05655-156">Options that configure the run-time behavior of the utility, such as reporting.</span></span>  
  
4.  <span data-ttu-id="05655-157">検証および実行フェーズ:パッケージを実行します。 **/VALIDATE** オプションが指定された場合は、実行せずに検証を実行します。</span><span class="sxs-lookup"><span data-stu-id="05655-157">Validation and execution phase: The package is run, or validated without running if the **/VALIDATE** option was specified.</span></span>  
  
##  <a name="exit-codes-returned"></a><a name="exit"></a> <span data-ttu-id="05655-158">返される終了コード</span><span class="sxs-lookup"><span data-stu-id="05655-158">Exit Codes Returned</span></span>  
 <span data-ttu-id="05655-159">**dtexec ユーティリティから返される終了コード**</span><span class="sxs-lookup"><span data-stu-id="05655-159">**Exit codes returned from dtexec utility**</span></span>  
  
 <span data-ttu-id="05655-160">パッケージの実行時、`dtexec` は終了コードを返すことができます。</span><span class="sxs-lookup"><span data-stu-id="05655-160">When a package runs, `dtexec` can return an exit code.</span></span> <span data-ttu-id="05655-161">終了コードは、ERRORLEVEL 変数の値を設定する場合に使用されます。この変数の値は、バッチ ファイル内の条件ステートメントや分岐ロジックでテストできます。</span><span class="sxs-lookup"><span data-stu-id="05655-161">The exit code is used to populate the ERRORLEVEL variable, the value of which can then be tested in conditional statements or branching logic within a batch file.</span></span> <span data-ttu-id="05655-162">次の表は、終了時に `dtexec` ユーティリティが設定できる値を示しています。</span><span class="sxs-lookup"><span data-stu-id="05655-162">The following table lists the values that the `dtexec` utility can set when exiting.</span></span>  
  
|<span data-ttu-id="05655-163">値</span><span class="sxs-lookup"><span data-stu-id="05655-163">Value</span></span>|<span data-ttu-id="05655-164">説明</span><span class="sxs-lookup"><span data-stu-id="05655-164">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="05655-165">0</span><span class="sxs-lookup"><span data-stu-id="05655-165">0</span></span>|<span data-ttu-id="05655-166">パッケージが正常に実行されました。</span><span class="sxs-lookup"><span data-stu-id="05655-166">The package executed successfully.</span></span>|  
|<span data-ttu-id="05655-167">1</span><span class="sxs-lookup"><span data-stu-id="05655-167">1</span></span>|<span data-ttu-id="05655-168">パッケージが失敗しました。</span><span class="sxs-lookup"><span data-stu-id="05655-168">The package failed.</span></span>|  
|<span data-ttu-id="05655-169">3</span><span class="sxs-lookup"><span data-stu-id="05655-169">3</span></span>|<span data-ttu-id="05655-170">パッケージはユーザーによって取り消されました。</span><span class="sxs-lookup"><span data-stu-id="05655-170">The package was canceled by the user.</span></span>|  
|<span data-ttu-id="05655-171">4</span><span class="sxs-lookup"><span data-stu-id="05655-171">4</span></span>|<span data-ttu-id="05655-172">ユーティリティは要求されたパッケージを見つけられません。</span><span class="sxs-lookup"><span data-stu-id="05655-172">The utility was unable to locate the requested package.</span></span> <span data-ttu-id="05655-173">パッケージが見つかりませんでした。</span><span class="sxs-lookup"><span data-stu-id="05655-173">The package could not be found.</span></span>|  
|<span data-ttu-id="05655-174">5</span><span class="sxs-lookup"><span data-stu-id="05655-174">5</span></span>|<span data-ttu-id="05655-175">ユーティリティは要求されたパッケージを読み込めません。</span><span class="sxs-lookup"><span data-stu-id="05655-175">The utility was unable to load the requested package.</span></span> <span data-ttu-id="05655-176">パッケージを読み込めませんでした。</span><span class="sxs-lookup"><span data-stu-id="05655-176">The package could not be loaded.</span></span>|  
|<span data-ttu-id="05655-177">6</span><span class="sxs-lookup"><span data-stu-id="05655-177">6</span></span>|<span data-ttu-id="05655-178">ユーティリティは、コマンド ラインに構文の内部エラーまたはセマンティック エラーを検出しました。</span><span class="sxs-lookup"><span data-stu-id="05655-178">The utility encountered an internal error of syntactic or semantic errors in the command line.</span></span>|  
  
##  <a name="syntax-rules"></a><a name="syntaxRules"></a> <span data-ttu-id="05655-179">構文規則</span><span class="sxs-lookup"><span data-stu-id="05655-179">Syntax Rules</span></span>  
 <span data-ttu-id="05655-180">**ユーティリティの構文規則**</span><span class="sxs-lookup"><span data-stu-id="05655-180">**Utility syntax rules**</span></span>  
  
 <span data-ttu-id="05655-181">すべてのオプションは、スラッシュ (/) またはマイナス記号 (-) で始まる必要があります。</span><span class="sxs-lookup"><span data-stu-id="05655-181">All options must start with a slash (/) or a minus sign (-).</span></span> <span data-ttu-id="05655-182">ここに示すオプションはスラッシュ (/) で始まりますが、マイナス記号 (-) を代わりに使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="05655-182">The options that are shown here start with a slash (/), but the minus sign (-) can be substituted.</span></span>  
  
 <span data-ttu-id="05655-183">引数に空白文字を含めるには、引用符で囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="05655-183">An argument must be enclosed in quotation marks if it contains a space.</span></span> <span data-ttu-id="05655-184">引数を引用符で囲まないと、空白文字を引数に含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="05655-184">If the argument is not enclosed in quotation marks, the argument cannot contain white space.</span></span>  
  
 <span data-ttu-id="05655-185">引用符で囲まれた文字列内に二重引用符がある場合は、単一引用符がエスケープされていることを表します。</span><span class="sxs-lookup"><span data-stu-id="05655-185">Doubled quotation marks within quoted strings represent escaped single quotation marks.</span></span>  
  
 <span data-ttu-id="05655-186">パスワードを除いて、オプションおよび引数では大文字と小文字が区別されません。</span><span class="sxs-lookup"><span data-stu-id="05655-186">Options and arguments are not case-sensitive, except for passwords.</span></span>  
  
##  <a name="using-dtexec-from-the-xp_cmdshell"></a><a name="cmdshell"></a> <span data-ttu-id="05655-187">xp_cmdshell での dtexec の使用</span><span class="sxs-lookup"><span data-stu-id="05655-187">Using dtexec from the xp_cmdshell</span></span>  
 <span data-ttu-id="05655-188">**xp_cmdshell での dtexec の使用**</span><span class="sxs-lookup"><span data-stu-id="05655-188">**Using dtexec from the xp_cmdshell**</span></span>  
  
 <span data-ttu-id="05655-189">**xp_cmdshell** プロンプトから dtexec を実行できます。</span><span class="sxs-lookup"><span data-stu-id="05655-189">You can run dtexec from the **xp_cmdshell** prompt.</span></span> <span data-ttu-id="05655-190">次の例では、UpsertData.dtsx というパッケージを実行し、リターン コードを無視します。</span><span class="sxs-lookup"><span data-stu-id="05655-190">The following example shows how to run a package called UpsertData.dtsx and ignore the return code:</span></span>  
  
```  
EXEC xp_cmdshell 'dtexec /f "C:\UpsertData.dtsx"'  
```  
  
 <span data-ttu-id="05655-191">次の例では、同じパッケージを実行し、リターン コードを取得します。</span><span class="sxs-lookup"><span data-stu-id="05655-191">The following example shows how to run the same package and capture the return code:</span></span>  
  
```  
DECLARE @returncode int  
EXEC @returncode = xp_cmdshell 'dtexec /f "C:\UpsertData.dtsx"'  
```  
  
> [!IMPORTANT]  
>  <span data-ttu-id="05655-192">[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を新しくインストールした場合、 **xp_cmdshell** オプションは既定により無効になっています。</span><span class="sxs-lookup"><span data-stu-id="05655-192">In [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the **xp_cmdshell** option is disabled by default on new installations.</span></span> <span data-ttu-id="05655-193">オプションを有効にするには、 **sp_configure** システム ストアド プロシージャを実行します。</span><span class="sxs-lookup"><span data-stu-id="05655-193">The option can be enabled by running the **sp_configure** system stored procedure.</span></span> <span data-ttu-id="05655-194">詳細については、「 [xp_cmdshell サーバー構成オプション](../../database-engine/configure-windows/xp-cmdshell-server-configuration-option.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="05655-194">For more information, see [xp_cmdshell Server Configuration Option](../../database-engine/configure-windows/xp-cmdshell-server-configuration-option.md).</span></span>  
  
##  <a name="syntax"></a><a name="syntax"></a> <span data-ttu-id="05655-195">構文</span><span class="sxs-lookup"><span data-stu-id="05655-195">Syntax</span></span>  
  
```  
dtexec /option [value] [/option [value]]...  
```  
  
##  <a name="parameters"></a><a name="parameter"></a> <span data-ttu-id="05655-196">パラメーター</span><span class="sxs-lookup"><span data-stu-id="05655-196">Parameters</span></span>  
  
-   <span data-ttu-id="05655-197">**/?**</span><span class="sxs-lookup"><span data-stu-id="05655-197">**/?**</span></span> [*option_name*]: 省略可能。 <span data-ttu-id="05655-199">コマンド プロンプトのオプション、または指定された *option_name* のヘルプを表示して、ユーティリティを終了します。</span><span class="sxs-lookup"><span data-stu-id="05655-199">Displays the command prompt options, or displays help for the specified *option_name* and then closes the utility.</span></span>  
  
     <span data-ttu-id="05655-200">*Option_name*引数を指定した場合、は `dtexec` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンラインブックを開始し、dtexec ユーティリティのトピックを表示します。</span><span class="sxs-lookup"><span data-stu-id="05655-200">If you specify an *option_name* argument, `dtexec` starts [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online and displays the dtexec Utility topic.</span></span>  
  
-   <span data-ttu-id="05655-201">**/Ca [llerInfo]**:</span><span class="sxs-lookup"><span data-stu-id="05655-201">**/Ca[llerInfo]**:</span></span>   
                  <span data-ttu-id="05655-202">省略可能。</span><span class="sxs-lookup"><span data-stu-id="05655-202">Optional.</span></span> <span data-ttu-id="05655-203">パッケージ実行の追加情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="05655-203">Specifies additional information for a package execution.</span></span> <span data-ttu-id="05655-204">SQL Server エージェントを使用してパッケージを実行する場合、エージェントはこの引数を設定して、パッケージ実行が SQL Server エージェントによって呼び出されることを示します。</span><span class="sxs-lookup"><span data-stu-id="05655-204">When you run a package using SQL Server Agent, agent sets this argument to indicate that the package execution is invoked by SQL Server Agent.</span></span> <span data-ttu-id="05655-205">`dtexec` ユーティリティがコマンド ラインから実行される場合、このパラメーターは無視されます。</span><span class="sxs-lookup"><span data-stu-id="05655-205">This parameter is ignored when the `dtexec` utility is run from the command line.</span></span>  
  
-   <span data-ttu-id="05655-206">**/CheckF[ile]** _filespec_:</span><span class="sxs-lookup"><span data-stu-id="05655-206">**/CheckF[ile]** _filespec_:</span></span>   
                  <span data-ttu-id="05655-207">省略可能。</span><span class="sxs-lookup"><span data-stu-id="05655-207">Optional.</span></span> <span data-ttu-id="05655-208">Filespec の `CheckpointFileName` パスとファイル spemandcified にパッケージのプロパティを設定し*filespec*ます。</span><span class="sxs-lookup"><span data-stu-id="05655-208">Sets the `CheckpointFileName` property on the package to the path and file spemandcified in *filespec*.</span></span> <span data-ttu-id="05655-209">このファイルは、パッケージが再起動されたときに使用されます。</span><span class="sxs-lookup"><span data-stu-id="05655-209">This file is used when the package restarts.</span></span> <span data-ttu-id="05655-210">このオプションが指定されていて、ファイル名の値が指定されていない場合、パッケージの `CheckpointFileName` には空の文字列が設定されます。</span><span class="sxs-lookup"><span data-stu-id="05655-210">If this option is specified and no value is supplied for the file name, the `CheckpointFileName` for the package is set to an empty string.</span></span> <span data-ttu-id="05655-211">このオプションが指定されない場合、パッケージの値は保持されます。</span><span class="sxs-lookup"><span data-stu-id="05655-211">If this option is not specified, the values in the package are retained.</span></span>  
  
-   <span data-ttu-id="05655-212">**/CheckP [ointing]** _{on\ off}_:</span><span class="sxs-lookup"><span data-stu-id="05655-212">**/CheckP[ointing]** _{on\off}_:</span></span>   
                  <span data-ttu-id="05655-213">省略可能。</span><span class="sxs-lookup"><span data-stu-id="05655-213">Optional.</span></span> <span data-ttu-id="05655-214">パッケージの実行時にパッケージがチェックポイントを使用するかどうかを決定する値を設定します。</span><span class="sxs-lookup"><span data-stu-id="05655-214">Sets a value that determines whether the package will use checkpoints during package execution.</span></span> <span data-ttu-id="05655-215">値 **on** を指定すると、失敗したパッケージが再実行されます。</span><span class="sxs-lookup"><span data-stu-id="05655-215">The value **on** specifies that a failed package is to be rerun.</span></span> <span data-ttu-id="05655-216">失敗したパッケージが再実行される場合、ランタイム エンジンは、障害点からパッケージを再起動するためにチェックポイント ファイルを使用します。</span><span class="sxs-lookup"><span data-stu-id="05655-216">When the failed package is rerun, the run-time engine uses the checkpoint file to restart the package from the point of failure.</span></span>  
  
     <span data-ttu-id="05655-217">オプションが値なしで宣言されている場合、既定値は on です。</span><span class="sxs-lookup"><span data-stu-id="05655-217">The default value is on if the option is declared without a value.</span></span> <span data-ttu-id="05655-218">値が on に設定されていて、チェックポイント ファイルが見つからない場合、パッケージの実行は失敗します。</span><span class="sxs-lookup"><span data-stu-id="05655-218">Package execution will fail if the value is set to on and the checkpoint file cannot be found.</span></span> <span data-ttu-id="05655-219">このオプションが指定されない場合、パッケージの値セットは保持されます。</span><span class="sxs-lookup"><span data-stu-id="05655-219">If this option is not specified, the value set in the package is retained.</span></span> <span data-ttu-id="05655-220">詳細については、「 [Restart Packages by Using Checkpoints](restart-packages-by-using-checkpoints.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="05655-220">For more information, see [Restart Packages by Using Checkpoints](restart-packages-by-using-checkpoints.md).</span></span>  
  
     <span data-ttu-id="05655-221">Dtexec のチェック**ポイント**オプションは、 `SaveCheckpoints` パッケージのプロパティを True に設定し、プロパティを常にに設定することと同じです `CheckpointUsage` 。</span><span class="sxs-lookup"><span data-stu-id="05655-221">The **/CheckPointing on** option of dtexec is equivalent to setting the `SaveCheckpoints` property of the package to True, and the `CheckpointUsage` property to Always.</span></span>  
  
-   <span data-ttu-id="05655-222">**/Com[mandFile]** _filespec_:</span><span class="sxs-lookup"><span data-stu-id="05655-222">**/Com[mandFile]** _filespec_:</span></span>   
                  <span data-ttu-id="05655-223">(省略可能)。</span><span class="sxs-lookup"><span data-stu-id="05655-223">(Optional).</span></span> <span data-ttu-id="05655-224">`dtexec` で実行するコマンド オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="05655-224">Specifies the command options that run with `dtexec`.</span></span> <span data-ttu-id="05655-225">*filespec* で指定されたファイルが開き、ファイルに EOF が見つかるまでそのファイルからオプションを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="05655-225">The file specified in *filespec* is opened and options from the file are read until EOF is found in the file.</span></span> <span data-ttu-id="05655-226">*filespec* は、テキスト ファイルです。</span><span class="sxs-lookup"><span data-stu-id="05655-226">*filespec* is a text file.</span></span> <span data-ttu-id="05655-227">*filespec* 引数には、パッケージの実行に関連付けるコマンド ファイルのファイル名とパスを指定します。</span><span class="sxs-lookup"><span data-stu-id="05655-227">The *filespec* argument specifies the file name and path of the command file to associate with the execution of the package.</span></span>  
  
-   <span data-ttu-id="05655-228">**/Conf [igFile]** _filespec_: 省略可能。</span><span class="sxs-lookup"><span data-stu-id="05655-228">**/Conf[igFile]** _filespec_: Optional.</span></span> <span data-ttu-id="05655-229">値を抽出する構成ファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="05655-229">Specifies a configuration file to extract values from.</span></span> <span data-ttu-id="05655-230">このオプションを使用すると、パッケージのデザイン時に指定された構成と異なる実行時構成を設定できます。</span><span class="sxs-lookup"><span data-stu-id="05655-230">Using this option, you can set a run-time configuration that differs from the configuration that was specified at design time for the package.</span></span> <span data-ttu-id="05655-231">パッケージを実行するには、XML 構成ファイルに異なる構成設定を格納してから、 **/ConfigFile** オプションを使用して設定を読み込む必要があります。</span><span class="sxs-lookup"><span data-stu-id="05655-231">You can store different configuration settings in an XML configuration file and then load the settings before package execution by using the **/ConfigFile** option.</span></span>  
  
     <span data-ttu-id="05655-232">**/ConfigFile** オプションを使用すると、デザイン時に指定しなかった追加の構成を実行時に読み込むことができますが、</span><span class="sxs-lookup"><span data-stu-id="05655-232">You can use the **/ConfigFile** option to load additional configurations at run time that you did not specify at design time.</span></span> <span data-ttu-id="05655-233">**/ConfigFile** オプションを使用しても、デザイン時に指定した構成値を置き換えることはできません。</span><span class="sxs-lookup"><span data-stu-id="05655-233">However, you cannot use the **/ConfigFile** option to replace configured values that you also specified at design time.</span></span> <span data-ttu-id="05655-234">パッケージ構成が適用されるしくみについては、「 [Package Configurations](../package-configurations.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="05655-234">To understand how package configurations are applied, see [Package Configurations](../package-configurations.md).</span></span>  
  
-   <span data-ttu-id="05655-235">**/Conn[ection]** _id_or_name;connection_string [[;id_or_name;connection_string]...]_:</span><span class="sxs-lookup"><span data-stu-id="05655-235">**/Conn[ection]** _id_or_name;connection_string [[;id_or_name;connection_string]...]_:</span></span>   
                  <span data-ttu-id="05655-236">省略可能。</span><span class="sxs-lookup"><span data-stu-id="05655-236">Optional.</span></span> <span data-ttu-id="05655-237">指定した名前または GUID の接続マネージャーがパッケージ内にあり、接続文字列が指定されていることを示します。</span><span class="sxs-lookup"><span data-stu-id="05655-237">Specifies that the connection manager with the specified name or GUID is located in the package, and specifies a connection string.</span></span>  
  
     <span data-ttu-id="05655-238">このオプションでは、接続マネージャーの名前または GUID を指定する *id_or_name* 引数と、有効な接続文字列を指定する *connection_string* 引数の両方のパラメーターが必須です。</span><span class="sxs-lookup"><span data-stu-id="05655-238">This option requires that both parameters be specified: the connection manager name or GUID must be provided in the *id_or_name* argument, and a valid connection string must be specified in the *connection_string* argument.</span></span> <span data-ttu-id="05655-239">詳細については、「[Integration Services (SSIS) の接続](../connection-manager/integration-services-ssis-connections.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="05655-239">For more information, see [Integration Services &#40;SSIS&#41; Connections](../connection-manager/integration-services-ssis-connections.md).</span></span>  
  
     <span data-ttu-id="05655-240">実行時に **/Connection** オプションを使用すると、デザイン時に指定した場所とは別の場所からパッケージ構成を読み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="05655-240">At run time, you can use the **/Connection** option to load package configurations from a location other than the location that you specified at design time.</span></span> <span data-ttu-id="05655-241">デザイン時に指定した値は、それらの構成の値で置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="05655-241">The values of these configurations then replace the values that were originally specified.</span></span> <span data-ttu-id="05655-242">ただし、 **/Connection** オプションを使用できるのは、接続マネージャーを使用する構成 ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成など) だけです。</span><span class="sxs-lookup"><span data-stu-id="05655-242">However you can use the **/Connection** option only for configurations, such as [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] configurations, that use a connection manager.</span></span> <span data-ttu-id="05655-243">パッケージ構成の適用方法については、「[パッケージの構成](../package-configurations.md)と[動作の変更」を参照して SQL Server 2014 の Integration Services 機能を](../behavior-changes-to-integration-services-features-in-sql-server-2014.md)確認してください。</span><span class="sxs-lookup"><span data-stu-id="05655-243">To understand how package configurations are applied, see [Package Configurations](../package-configurations.md) and [Behavior Changes to Integration Services Features in SQL Server 2014](../behavior-changes-to-integration-services-features-in-sql-server-2014.md).</span></span>  
  
-   <span data-ttu-id="05655-244">**/短所 [oleLog]** [*displayoptions*]; [*list_options*;*src_name_or_guid*]...]: 省略可能。</span><span class="sxs-lookup"><span data-stu-id="05655-244">**/Cons[oleLog]** [[*displayoptions*];[*list_options*;*src_name_or_guid*]...]: Optional.</span></span> <span data-ttu-id="05655-245">パッケージの実行中に、指定されたログ エントリをコンソールに表示します。</span><span class="sxs-lookup"><span data-stu-id="05655-245">Displays specified log entries to the console during package execution.</span></span> <span data-ttu-id="05655-246">このオプションを省略した場合、ログ エントリはコンソールに表示されません。</span><span class="sxs-lookup"><span data-stu-id="05655-246">If this option is omitted, no log entries are shown in the console.</span></span> <span data-ttu-id="05655-247">表示を制限するパラメーターなしでオプションが指定された場合、すべてのログ エントリが表示されます。</span><span class="sxs-lookup"><span data-stu-id="05655-247">If the option is specified without parameters that limit the display, every log entry will display.</span></span> <span data-ttu-id="05655-248">コンソールに表示されるエントリを制限するには、 *displayoptions* パラメーターを使用して表示する列を指定し、 *list_options* パラメーターを使用してログ エントリの種類を制限します。</span><span class="sxs-lookup"><span data-stu-id="05655-248">To limit the entries that are displayed to the console, you can specify the columns to show by using the *displayoptions* parameter, and limit the log entry types by using the *list_options* parameter.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="05655-249">パラメーターを使用してサーバーでパッケージを実行すると [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] `/ISSERVER` 、コンソールの出力が制限され、 **[olelog]** オプションのほとんどは適用できません。</span><span class="sxs-lookup"><span data-stu-id="05655-249">When you run a package on the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server by using the `/ISSERVER` parameter, console output is limited and most of the **/Cons[oleLog]** options are not applicable.</span></span> <span data-ttu-id="05655-250">すべての実行ログは、関連するビューでサーバーから確認できます。また、 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]で利用可能な標準レポートを使用して確認することもできます。</span><span class="sxs-lookup"><span data-stu-id="05655-250">All execution logs can be seen from the server in the related views or by using standard reports available in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="05655-251">レポートの詳細については、「 [Integration Services サーバーのレポート](../reports-for-the-integration-services-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="05655-251">For more information about the reports, see [Reports for the Integration Services Server](../reports-for-the-integration-services-server.md).</span></span>  
  
     <span data-ttu-id="05655-252">*displayoptions* の値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="05655-252">The *displayoptions* values are as follows:</span></span>  
  
    -   <span data-ttu-id="05655-253">N (名前)</span><span class="sxs-lookup"><span data-stu-id="05655-253">N (Name)</span></span>  
  
    -   <span data-ttu-id="05655-254">C (コンピューター)</span><span class="sxs-lookup"><span data-stu-id="05655-254">C (Computer)</span></span>  
  
    -   <span data-ttu-id="05655-255">O (オペレーター)</span><span class="sxs-lookup"><span data-stu-id="05655-255">O (Operator)</span></span>  
  
    -   <span data-ttu-id="05655-256">S (変換元の名前)</span><span class="sxs-lookup"><span data-stu-id="05655-256">S (Source Name)</span></span>  
  
    -   <span data-ttu-id="05655-257">G (変換元の GUID)</span><span class="sxs-lookup"><span data-stu-id="05655-257">G (Source GUID)</span></span>  
  
    -   <span data-ttu-id="05655-258">X (実行 GUID)</span><span class="sxs-lookup"><span data-stu-id="05655-258">X (Execution GUID)</span></span>  
  
    -   <span data-ttu-id="05655-259">M (メッセージ)</span><span class="sxs-lookup"><span data-stu-id="05655-259">M (Message)</span></span>  
  
    -   <span data-ttu-id="05655-260">T (開始時刻および終了時刻)</span><span class="sxs-lookup"><span data-stu-id="05655-260">T (Time Start and End)</span></span>  
  
     <span data-ttu-id="05655-261">*list_options* の値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="05655-261">The *list_options* values are as follows:</span></span>  
  
    -   <span data-ttu-id="05655-262">*I* - 包含一覧を指定します。</span><span class="sxs-lookup"><span data-stu-id="05655-262">*I* - Specifies the inclusion list.</span></span> <span data-ttu-id="05655-263">指定された変換元の名または変換元の GUID のみがログに記録されます。</span><span class="sxs-lookup"><span data-stu-id="05655-263">Only the source names or GUIDs that are specified are logged.</span></span>  
  
    -   <span data-ttu-id="05655-264">*E* - 除外一覧を指定します。</span><span class="sxs-lookup"><span data-stu-id="05655-264">*E* - Specifies the exclusion list.</span></span> <span data-ttu-id="05655-265">指定された変換元の名前または変換元の GUID はログに記録されません。</span><span class="sxs-lookup"><span data-stu-id="05655-265">The source names or GUIDs that are specified are not logged.</span></span>  
  
    -   <span data-ttu-id="05655-266">*src_name_or_guid* パラメーターには、含めるまたは除外するイベント名、変換元の名前、変換元の GUID を指定します。</span><span class="sxs-lookup"><span data-stu-id="05655-266">The *src_name_or_guid* parameter specified for inclusion or exclusion is an event name, source name, or source GUID.</span></span>  
  
     <span data-ttu-id="05655-267">同じコマンド プロンプトで複数の **/ConsoleLog** オプションを使用する場合、次のような相互作用があります。</span><span class="sxs-lookup"><span data-stu-id="05655-267">If you use multiple **/ConsoleLog** options on the same command prompt, they interact as follows:</span></span>  
  
    -   <span data-ttu-id="05655-268">表示の順序には影響しません。</span><span class="sxs-lookup"><span data-stu-id="05655-268">Their order of appearance has no effect.</span></span>  
  
    -   <span data-ttu-id="05655-269">包含一覧がコマンド ラインに指定されていない場合、すべての種類のログ エントリに対して除外一覧が適用されます。</span><span class="sxs-lookup"><span data-stu-id="05655-269">If no inclusion lists are present on the command line, exclusion lists are applied against all kinds of log entries.</span></span>  
  
    -   <span data-ttu-id="05655-270">包含一覧がコマンド ラインに指定されている場合、すべての包含一覧の集合に対して除外一覧が適用されます。</span><span class="sxs-lookup"><span data-stu-id="05655-270">If any inclusion lists are present on the command line, exclusion lists are applied against the union of all inclusion lists.</span></span>  
  
     <span data-ttu-id="05655-271">**/Consolelog**オプションの例については、「**解説**」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="05655-271">For examples of the **/ConsoleLog** option, see the **Remarks** section.</span></span>  
  
-   <span data-ttu-id="05655-272">**/D[ts]** _package_path_:</span><span class="sxs-lookup"><span data-stu-id="05655-272">**/D[ts]** _package_path_:</span></span>   
                  <span data-ttu-id="05655-273">省略可能。</span><span class="sxs-lookup"><span data-stu-id="05655-273">Optional.</span></span> <span data-ttu-id="05655-274">SSIS パッケージ ストアからパッケージを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="05655-274">Loads a package from the SSIS Package Store.</span></span> <span data-ttu-id="05655-275">SSIS パッケージ ストアに格納されているパッケージは、従来のパッケージ配置モデルを使用して配置されます。</span><span class="sxs-lookup"><span data-stu-id="05655-275">Packages that are stored in the SSIS Package Store, are deployed using the legacy package deployment model.</span></span> <span data-ttu-id="05655-276">プロジェクト配置モデルを使用して、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サーバーに配置されているパッケージを実行するには、`/ISServer` オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="05655-276">To run packages that are deployed to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server using the project deployment model, use the `/ISServer` option.</span></span> <span data-ttu-id="05655-277">パッケージとプロジェクトの配置モデルの詳細については、「 [Deployment of Projects and Packages](deploy-integration-services-ssis-projects-and-packages.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="05655-277">For more information about the package and project deployment models, see [Deployment of Projects and Packages](deploy-integration-services-ssis-projects-and-packages.md).</span></span>  
  
     <span data-ttu-id="05655-278">*package_path* 引数には、 [!INCLUDE[ssIS](../../includes/ssis-md.md)] パッケージの相対パスを指定します。このパスは SSIS パッケージ ストアのルートから始まり、 [!INCLUDE[ssIS](../../includes/ssis-md.md)] パッケージの名前を含むパスです。</span><span class="sxs-lookup"><span data-stu-id="05655-278">The *package_path* argument specifies the relative path of the [!INCLUDE[ssIS](../../includes/ssis-md.md)] package, starting at the root of the SSIS Package Store, and includes the name of the [!INCLUDE[ssIS](../../includes/ssis-md.md)] package.</span></span> <span data-ttu-id="05655-279">*package_path* 引数に指定するパスまたはファイル名に空白文字を含める場合は、 *package_path* 引数を引用符で囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="05655-279">If the path or file name specified in the *package_path* argument contains a space, you must put quotation marks around the *package_path* argument.</span></span>  
  
     <span data-ttu-id="05655-280">`/DTS` オプションは、`/File` または `/SQL` オプションと共に使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="05655-280">The `/DTS` option cannot be used together with the `/File` or `/SQL` option.</span></span> <span data-ttu-id="05655-281">複数のオプションが指定された場合、`dtexec` は失敗します。</span><span class="sxs-lookup"><span data-stu-id="05655-281">If multiple options are specified, `dtexec` fails.</span></span>  
  
-   <span data-ttu-id="05655-282">**/De [crypt]**  _password_: 省略可能。</span><span class="sxs-lookup"><span data-stu-id="05655-282">**/De[crypt]**  _password_: Optional.</span></span> <span data-ttu-id="05655-283">パスワードが暗号化されているパッケージを読み込むときに使用する暗号化解除用パスワードを設定します。</span><span class="sxs-lookup"><span data-stu-id="05655-283">Sets the decryption password that is used when you load a package with password encryption.</span></span>  
  
-   <span data-ttu-id="05655-284">**/Dump** _error code_:</span><span class="sxs-lookup"><span data-stu-id="05655-284">**/Dump** _error code_:</span></span>  
                  <span data-ttu-id="05655-285">省略可能にすると、パッケージの実行中に1つ以上の指定したイベントが発生したときに、デバッグダンプファイル (mdmp と .tmp) が作成されます。</span><span class="sxs-lookup"><span data-stu-id="05655-285">Optional Creates the debug dump files, .mdmp and .tmp, when one or more specified events occur while the package is running.</span></span> <span data-ttu-id="05655-286">*error code* 引数では、システムによるデバッグ ダンプ ファイル作成のトリガーとなるイベント コードの種類 (エラー、警告、または情報) が指定されます。</span><span class="sxs-lookup"><span data-stu-id="05655-286">The *error code* argument specifies the type of event code-error, warning, or information-that will trigger the system to create the debug dump files.</span></span> <span data-ttu-id="05655-287">イベント コードを複数指定するには、各 *error code* 引数をセミコロン (;) で区切ります。</span><span class="sxs-lookup"><span data-stu-id="05655-287">To specify multiple event codes, separate each *error code* argument by a semi-colon (;).</span></span> <span data-ttu-id="05655-288">*error code* 引数に引用符を含めないでください。</span><span class="sxs-lookup"><span data-stu-id="05655-288">Do not include quotes with the *error code* argument.</span></span>  
  
     <span data-ttu-id="05655-289">次の例では、DTS_E_CANNOTACQUIRECONNECTIONFROMCONNECTIONMANAGER のエラーが発生したときにデバッグ ダンプ ファイルが生成されます。</span><span class="sxs-lookup"><span data-stu-id="05655-289">The following example generates the debug dump files when the DTS_E_CANNOTACQUIRECONNECTIONFROMCONNECTIONMANAGER error occurs.</span></span>  
  
    ```  
    /Dump 0xC020801C  
    ```  
  
     <span data-ttu-id="05655-290">既定では、は、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] デバッグダンプファイルを次のフォルダーに格納し *\<drive>* ます。</span><span class="sxs-lookup"><span data-stu-id="05655-290">By default, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] stores the debug dump files in the folder, *\<drive>*:\Program Files\Microsoft SQL Server\110\Shared\ErrorDumps.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="05655-291">デバッグ ダンプ ファイルには機密情報が含まれている場合があります。</span><span class="sxs-lookup"><span data-stu-id="05655-291">Debug dump files may contain sensitive information.</span></span> <span data-ttu-id="05655-292">アクセス制御リスト (ACL) を使用してファイルへのアクセスを制限するか、アクセスが制限されたフォルダーにファイルをコピーしてください。</span><span class="sxs-lookup"><span data-stu-id="05655-292">Use an access control list (ACL) to restrict access to the files, or copy the files to a folder with restricted access.</span></span> <span data-ttu-id="05655-293">たとえば、デバッグ ファイルを Microsoft サポート サービスに送信する前には、機密性の高い情報をすべて削除することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="05655-293">For example, before you send your debug files to Microsoft support services, we recommended that you remove any sensitive or confidential information.</span></span>  
  
     <span data-ttu-id="05655-294">このオプションをユーティリティで実行されるすべてのパッケージに適用するには `dtexec` 、 **Dumponcodes** REG_SZ 値を HKEY_LOCAL_MACHINE \software\microsoft\microsoft SQL server\110\ssis\setup\dtspath に追加レジストリキーに追加します。</span><span class="sxs-lookup"><span data-stu-id="05655-294">To apply this option to all packages that the `dtexec` utility runs, add a **DumpOnCodes** REG_SZ value to the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\110\SSIS\Setup\DtsPath registry key.</span></span> <span data-ttu-id="05655-295">**DumpOnCodes** のデータ値では、システムによるデバッグ ダンプ ファイル作成のトリガーとなるエラー コードを指定します。</span><span class="sxs-lookup"><span data-stu-id="05655-295">The data value in **DumpOnCodes** specifies the error code or codes that will trigger the system to create debug dump files.</span></span> <span data-ttu-id="05655-296">複数のエラー コードは、セミコロン (;) で区切る必要があります。</span><span class="sxs-lookup"><span data-stu-id="05655-296">Multiple error codes must be separated by a semi-colon (;).</span></span>  
  
     <span data-ttu-id="05655-297">**DumpOnCodes** 値をレジストリ キーに追加し、 **/Dump** オプションも使用した場合、両方の設定に基づくデバッグ ダンプ ファイルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="05655-297">If you add a **DumpOnCodes** value to the registry key, and use the **/Dump** option, the system will create debug dump files that are based on both settings.</span></span>  
  
     <span data-ttu-id="05655-298">デバッグ ダンプ ファイルの詳細については、「 [Generating Dump Files for Package Execution](../troubleshooting/generating-dump-files-for-package-execution.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="05655-298">For more information about debug dump files, see [Generating Dump Files for Package Execution](../troubleshooting/generating-dump-files-for-package-execution.md).</span></span>  
  
-   <span data-ttu-id="05655-299">**/Dumponerror**:</span><span class="sxs-lookup"><span data-stu-id="05655-299">**/DumpOnError**:</span></span>   
                  <span data-ttu-id="05655-300">省略可能。</span><span class="sxs-lookup"><span data-stu-id="05655-300">Optional.</span></span> <span data-ttu-id="05655-301">パッケージの実行中にエラーが発生した場合に、デバッグダンプファイル (mdmp と .tmp) を作成します。</span><span class="sxs-lookup"><span data-stu-id="05655-301">Creates the debug dump files, .mdmp and .tmp, when any error occurs while the package is running.</span></span>  
  
     <span data-ttu-id="05655-302">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] の既定では、デバッグ ダンプ ファイルは *\<drive>* :\Program Files\Microsoft SQL Server\110\Shared\ErrorDumps フォルダーに格納されます。</span><span class="sxs-lookup"><span data-stu-id="05655-302">By default, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] stores the debug dump files in the folder, *\<drive>*:\Program Files\Microsoft SQL Server\110\Shared\ErrorDumps folder.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="05655-303">デバッグ ダンプ ファイルには機密情報が含まれている場合があります。</span><span class="sxs-lookup"><span data-stu-id="05655-303">Debug dump files may contain sensitive information.</span></span> <span data-ttu-id="05655-304">アクセス制御リスト (ACL) を使用してファイルへのアクセスを制限するか、アクセスが制限されたフォルダーにファイルをコピーしてください。</span><span class="sxs-lookup"><span data-stu-id="05655-304">Use an access control list (ACL) to restrict access to the files, or copy the files to a folder with restricted access.</span></span> <span data-ttu-id="05655-305">たとえば、デバッグ ファイルを Microsoft サポート サービスに送信する前には、機密性の高い情報をすべて削除することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="05655-305">For example, before you send your debug files to Microsoft support services, we recommended that you remove any sensitive or confidential information.</span></span>  
  
     <span data-ttu-id="05655-306">このオプションをユーティリティで実行されるすべてのパッケージに適用するには、 `dtexec` **dumponerror** REG_DWORD 値を HKEY_LOCAL_MACHINE \software\microsoft\microsoft SQL server\110\ssis\setup\dtspath に追加レジストリキーに追加します。</span><span class="sxs-lookup"><span data-stu-id="05655-306">To apply this option to all packages that the `dtexec` utility runs, add a **DumpOnError** REG_DWORD value to the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\110\SSIS\Setup\DtsPath registry key.</span></span> <span data-ttu-id="05655-307">**Dumponerror** REG_DWORD 値の値によって、ユーティリティで **/dumponerror**オプションを使用する必要があるかどうかが決まり `dtexec` ます。</span><span class="sxs-lookup"><span data-stu-id="05655-307">The value of the **DumpOnError** REG_DWORD value determines whether the **/DumpOnError** option needs to be used with the `dtexec` utility:</span></span>  
  
    -   <span data-ttu-id="05655-308">0以外のデータ値は、ユーティリティで **/dumponerror**オプションを使用するかどうかに関係なく、エラーが発生したときにデバッグダンプファイルが作成されることを示し `dtexec` ます。</span><span class="sxs-lookup"><span data-stu-id="05655-308">A non-zero data value indicates that the system will create debug dump files when any error occurs, regardless of whether you use the **/DumpOnError** option with the `dtexec` utility.</span></span>  
  
    -   <span data-ttu-id="05655-309">データ値が0の場合は、ユーティリティで **/dumponerror**オプションを使用しない限り、デバッグダンプファイルは作成されません `dtexec` 。</span><span class="sxs-lookup"><span data-stu-id="05655-309">A zero data value indicates that the system will not create the debug dump files unless you use the **/DumpOnError** option with the `dtexec` utility.</span></span>  
  
     <span data-ttu-id="05655-310">デバッグ ダンプ ファイルの詳細については、「 [Generating Dump Files for Package Execution](../troubleshooting/generating-dump-files-for-package-execution.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="05655-310">For more information about debug dump files, see [Generating Dump Files for Package Execution](../troubleshooting/generating-dump-files-for-package-execution.md)</span></span>  
  
-   <span data-ttu-id="05655-311">`/Env[Reference]`*環境の参照 ID*:</span><span class="sxs-lookup"><span data-stu-id="05655-311">`/Env[Reference]` *environment reference ID*:</span></span>   
                  <span data-ttu-id="05655-312">省略可能。</span><span class="sxs-lookup"><span data-stu-id="05655-312">Optional.</span></span> <span data-ttu-id="05655-313">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サーバーに配置するパッケージ用に、パッケージ実行で使用される環境参照 (ID) を指定します。</span><span class="sxs-lookup"><span data-stu-id="05655-313">Specifies the environment reference (ID) that is used by the package execution, for a package that is deployed to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server.</span></span> <span data-ttu-id="05655-314">このパラメーターを変数にバインドするように構成すると、環境に含まれる変数の値が使用されます。</span><span class="sxs-lookup"><span data-stu-id="05655-314">The parameters configured to bind to variables will use the values of the variables that are contained in the environment.</span></span>  
  
     <span data-ttu-id="05655-315">`/Env[Reference]` オプションは、`/ISServer` オプションおよび `/Server` オプションと共に使用します。</span><span class="sxs-lookup"><span data-stu-id="05655-315">You use `/Env[Reference]` option together with the `/ISServer` and the `/Server` options.</span></span>  
  
     <span data-ttu-id="05655-316">このパラメーターは SQL Server エージェントによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="05655-316">This parameter is used by SQL Server Agent.</span></span>  
  
-   <span data-ttu-id="05655-317">**/F[ile]** _filespec_:</span><span class="sxs-lookup"><span data-stu-id="05655-317">**/F[ile]** _filespec_:</span></span>   
                  <span data-ttu-id="05655-318">省略可能。</span><span class="sxs-lookup"><span data-stu-id="05655-318">Optional.</span></span> <span data-ttu-id="05655-319">ファイル システムに保存されているパッケージを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="05655-319">Loads a package that is saved in the file system.</span></span> <span data-ttu-id="05655-320">ファイル システムに保存されているパッケージは、従来のパッケージ配置モデルを使用して配置されます。</span><span class="sxs-lookup"><span data-stu-id="05655-320">Packages that are saved in the file system, are deployed using the legacy package deployment model.</span></span> <span data-ttu-id="05655-321">プロジェクト配置モデルを使用して、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サーバーに配置されているパッケージを実行するには、`/ISServer` オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="05655-321">To run packages that are deployed to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server using the project deployment model, use the `/ISServer` option.</span></span> <span data-ttu-id="05655-322">パッケージとプロジェクトの配置モデルの詳細については、「 [Deployment of Projects and Packages](deploy-integration-services-ssis-projects-and-packages.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="05655-322">For more information about the package and project deployment models, see [Deployment of Projects and Packages](deploy-integration-services-ssis-projects-and-packages.md)</span></span>  
  
     <span data-ttu-id="05655-323">*filespec* 引数には、パッケージのパスとファイル名を指定します。</span><span class="sxs-lookup"><span data-stu-id="05655-323">The *filespec* argument specifies the path and file name of the package.</span></span> <span data-ttu-id="05655-324">汎用名前付け規則 (UNC) 形式のパス、またはローカル パスのどちらかでパスを指定できます。</span><span class="sxs-lookup"><span data-stu-id="05655-324">You can specify the path as either a Universal Naming Convention (UNC) path or a local path.</span></span> <span data-ttu-id="05655-325">*filespec* 引数に指定するパスまたはファイル名に空白文字を含める場合は、 *filespec* 引数を引用符で囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="05655-325">If the path or file name specified in the *filespec* argument contains a space, you must put quotation marks around the *filespec* argument.</span></span>  
  
     <span data-ttu-id="05655-326">`/File` オプションは、`/DTS` または `/SQL` オプションと共に使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="05655-326">The `/File` option cannot be used together with the `/DTS` or `/SQL` option.</span></span> <span data-ttu-id="05655-327">複数のオプションが指定された場合、`dtexec` は失敗します。</span><span class="sxs-lookup"><span data-stu-id="05655-327">If multiple options are specified, `dtexec` fails.</span></span>  
  
-   <span data-ttu-id="05655-328">**/H [elp]** [*Option_name*]: 省略可能。</span><span class="sxs-lookup"><span data-stu-id="05655-328">**/H[elp]** [*option_name*]: Optional.</span></span> <span data-ttu-id="05655-329">オプションのヘルプ、または指定された *option_name* のヘルプを表示して、ユーティリティを終了します。</span><span class="sxs-lookup"><span data-stu-id="05655-329">Displays help for the options, or displays help for the specified *option_name* and closes the utility.</span></span>  
  
     <span data-ttu-id="05655-330">*Option_name*引数を指定した場合、は `dtexec` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンラインブックを開始し、dtexec ユーティリティのトピックを表示します。</span><span class="sxs-lookup"><span data-stu-id="05655-330">If you specify an *option_name* argument, `dtexec` starts [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online and displays the dtexec Utility topic.</span></span>  
  
-   <span data-ttu-id="05655-331">`/ISServer`*packagepath*:</span><span class="sxs-lookup"><span data-stu-id="05655-331">`/ISServer` *packagepath*:</span></span>  
                  <span data-ttu-id="05655-332">省略可能。</span><span class="sxs-lookup"><span data-stu-id="05655-332">Optional.</span></span> <span data-ttu-id="05655-333">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サーバーに配置するパッケージを実行します。</span><span class="sxs-lookup"><span data-stu-id="05655-333">Runs a package that is deployed to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server.</span></span> <span data-ttu-id="05655-334">*PackagePath* 引数には、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サーバーに配置するパッケージの完全なパスとファイル名を指定します。</span><span class="sxs-lookup"><span data-stu-id="05655-334">The *PackagePath* argument specifies the full path and file name of the package deployed to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server.</span></span> <span data-ttu-id="05655-335">*PackagePath* 引数に指定するパスまたはファイル名に空白文字を含める場合は、 *PackagePath* 引数を引用符で囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="05655-335">If the path or file name specified in the *PackagePath* argument contains a space, you must put quotation marks around the *PackagePath* argument.</span></span>  
  
     <span data-ttu-id="05655-336">パッケージ形式は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="05655-336">The package format is as follows:</span></span>  
  
    ```  
    \<catalog name>\<folder name>\<project name>\package file name  
    ```  
  
     <span data-ttu-id="05655-337">`/Server` オプションは、`/ISSERVER` オプションと共に使用します。</span><span class="sxs-lookup"><span data-stu-id="05655-337">You use `/Server` option together with the `/ISSERVER` option.</span></span> <span data-ttu-id="05655-338">SSIS サーバーでパッケージを実行できるのは Windows 認証のみです。</span><span class="sxs-lookup"><span data-stu-id="05655-338">Only Windows Authentication can execute a package on the SSIS Server.</span></span> <span data-ttu-id="05655-339">現在の Windows ユーザーはパッケージへのアクセスに使用されます。</span><span class="sxs-lookup"><span data-stu-id="05655-339">The current Windows user is used to access the package.</span></span> <span data-ttu-id="05655-340">/Server オプションを省略した場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の既定のローカル インスタンスが使用されます。</span><span class="sxs-lookup"><span data-stu-id="05655-340">If the /Server option is omitted, the default local instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is assumed.</span></span>  
  
     <span data-ttu-id="05655-341">`/ISSERVER` オプションを、`/DTS`、`/SQL`、または `/File` の各オプションと共に使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="05655-341">The `/ISSERVER` option cannot be used together with the `/DTS`, `/SQL` or `/File` option.</span></span> <span data-ttu-id="05655-342">複数のオプションが指定された場合、dtexec は失敗します。</span><span class="sxs-lookup"><span data-stu-id="05655-342">If multiple options are specified, dtexec fails.</span></span>  
  
     <span data-ttu-id="05655-343">このパラメーターは SQL Server エージェントによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="05655-343">This parameter is used by SQL Server Agent.</span></span>  
  
-   <span data-ttu-id="05655-344">**/L[ogger]** _classid_orprogid;configstring_:</span><span class="sxs-lookup"><span data-stu-id="05655-344">**/L[ogger]** _classid_orprogid;configstring_:</span></span>  
                  <span data-ttu-id="05655-345">省略可能。</span><span class="sxs-lookup"><span data-stu-id="05655-345">Optional.</span></span> <span data-ttu-id="05655-346">1 つまたは複数のログ プロバイダーを [!INCLUDE[ssIS](../../includes/ssis-md.md)] パッケージの実行と関連付けます。</span><span class="sxs-lookup"><span data-stu-id="05655-346">Associates one or more log providers with the execution of an [!INCLUDE[ssIS](../../includes/ssis-md.md)] package.</span></span> <span data-ttu-id="05655-347">*classid_orprogid* パラメーターには、ログ プロバイダーを指定します。指定できるのはクラス GUID です。</span><span class="sxs-lookup"><span data-stu-id="05655-347">The *classid_orprogid* parameter specifies the log provider, and can be specified as a class GUID.</span></span> <span data-ttu-id="05655-348">*configstring* は、ログ プロバイダーを構成するために使用する文字列です。</span><span class="sxs-lookup"><span data-stu-id="05655-348">The *configstring* is the string that is used to configure the log provider.</span></span>  
  
     <span data-ttu-id="05655-349">使用できるログ プロバイダーは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="05655-349">The following list shows the available log providers:</span></span>  
  
    -   <span data-ttu-id="05655-350">テキスト ファイル:</span><span class="sxs-lookup"><span data-stu-id="05655-350">Text file:</span></span>  
  
        -   <span data-ttu-id="05655-351">ProgID:DTS.LogProviderTextFile.1</span><span class="sxs-lookup"><span data-stu-id="05655-351">ProgID: DTS.LogProviderTextFile.1</span></span>  
  
        -   <span data-ttu-id="05655-352">ClassID: {59B2C6A5-663F-4C20-8863-C83F9B72E2EB}</span><span class="sxs-lookup"><span data-stu-id="05655-352">ClassID: {59B2C6A5-663F-4C20-8863-C83F9B72E2EB}</span></span>  
  
    -   [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]<span data-ttu-id="05655-353">:</span><span class="sxs-lookup"><span data-stu-id="05655-353">:</span></span>  
  
        -   <span data-ttu-id="05655-354">ProgID:DTS.LogProviderSQLProfiler.1</span><span class="sxs-lookup"><span data-stu-id="05655-354">ProgID: DTS.LogProviderSQLProfiler.1</span></span>  
  
        -   <span data-ttu-id="05655-355">ClassID: {5C0B8D21-E9AA-462E-BA34-30FF5F7A42A1}</span><span class="sxs-lookup"><span data-stu-id="05655-355">ClassID: {5C0B8D21-E9AA-462E-BA34-30FF5F7A42A1}</span></span>  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="05655-356">:</span><span class="sxs-lookup"><span data-stu-id="05655-356">:</span></span>  
  
        -   <span data-ttu-id="05655-357">ProgID:DTS.LogProviderSQLServer.1</span><span class="sxs-lookup"><span data-stu-id="05655-357">ProgID: DTS.LogProviderSQLServer.1</span></span>  
  
        -   <span data-ttu-id="05655-358">ClassID: {6AA833A1-E4B2-4431-831B-DE695049DC61}</span><span class="sxs-lookup"><span data-stu-id="05655-358">ClassID: {6AA833A1-E4B2-4431-831B-DE695049DC61}</span></span>  
  
    -   <span data-ttu-id="05655-359">Windows イベント ログ:</span><span class="sxs-lookup"><span data-stu-id="05655-359">Windows Event Log:</span></span>  
  
        -   <span data-ttu-id="05655-360">ProgID:DTS.LogProviderEventLog.1</span><span class="sxs-lookup"><span data-stu-id="05655-360">ProgID: DTS.LogProviderEventLog.1</span></span>  
  
        -   <span data-ttu-id="05655-361">ClassID: {97634F75-1DC7-4F1F-8A4C-DAF0E13AAA22}</span><span class="sxs-lookup"><span data-stu-id="05655-361">ClassID: {97634F75-1DC7-4F1F-8A4C-DAF0E13AAA22}</span></span>  
  
    -   <span data-ttu-id="05655-362">XML ファイル:</span><span class="sxs-lookup"><span data-stu-id="05655-362">XML File:</span></span>  
  
        -   <span data-ttu-id="05655-363">ProgID:DTS.LogProviderXMLFile.1</span><span class="sxs-lookup"><span data-stu-id="05655-363">ProgID: DTS.LogProviderXMLFile.1</span></span>  
  
        -   <span data-ttu-id="05655-364">ClassID: {AFED6884-619C-484F-9A09-F42D56E1A7EA}</span><span class="sxs-lookup"><span data-stu-id="05655-364">ClassID: {AFED6884-619C-484F-9A09-F42D56E1A7EA}</span></span>  
  
-   <span data-ttu-id="05655-365">**/M[axConcurrent]** _concurrent_executables_:</span><span class="sxs-lookup"><span data-stu-id="05655-365">**/M[axConcurrent]** _concurrent_executables_:</span></span>  
                  <span data-ttu-id="05655-366">省略可能。</span><span class="sxs-lookup"><span data-stu-id="05655-366">Optional.</span></span> <span data-ttu-id="05655-367">パッケージが同時に実行できる実行可能ファイルの数を指定します。</span><span class="sxs-lookup"><span data-stu-id="05655-367">Specifies the number of executable files that the package can run concurrently.</span></span> <span data-ttu-id="05655-368">負以外の整数または -1 を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="05655-368">The value specified must be either a non-negative integer, or -1.</span></span> <span data-ttu-id="05655-369">値 -1 は、 [!INCLUDE[ssIS](../../includes/ssis-md.md)] が同時に実行できる実行可能ファイルの最大数が、パッケージを実行するコンピューターのプロセッサの合計数に 2 を加えたものと等しいことを意味します。</span><span class="sxs-lookup"><span data-stu-id="05655-369">A value of -1 means that [!INCLUDE[ssIS](../../includes/ssis-md.md)] will allow a maximum number of concurrently running executables that is equal to the total number of processors on the computer executing the package, plus two.</span></span>  
  
-   <span data-ttu-id="05655-370">**/Pack[age]** _PackageName_:</span><span class="sxs-lookup"><span data-stu-id="05655-370">**/Pack[age]** _PackageName_:</span></span>  
                  <span data-ttu-id="05655-371">省略可能。</span><span class="sxs-lookup"><span data-stu-id="05655-371">Optional.</span></span> <span data-ttu-id="05655-372">実行されるパッケージを指定します。</span><span class="sxs-lookup"><span data-stu-id="05655-372">Specifies the package that is executed.</span></span> <span data-ttu-id="05655-373">このパラメーターは、 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]からパッケージを実行する場合に主に使用されます。</span><span class="sxs-lookup"><span data-stu-id="05655-373">This parameter is used primarily when you execute the package from [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].</span></span>  
  
-   <span data-ttu-id="05655-374">**/P [assword]** _パスワード_:</span><span class="sxs-lookup"><span data-stu-id="05655-374">**/P[assword]** _password_:</span></span>  
                  <span data-ttu-id="05655-375">省略可能。</span><span class="sxs-lookup"><span data-stu-id="05655-375">Optional.</span></span> <span data-ttu-id="05655-376">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証によって保護されているパッケージの取得を可能にします。</span><span class="sxs-lookup"><span data-stu-id="05655-376">Allows the retrieval of a package that is protected by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="05655-377">このオプションは、 **/User** オプションと共に使用します。</span><span class="sxs-lookup"><span data-stu-id="05655-377">This option is used together with the **/User** option.</span></span> <span data-ttu-id="05655-378">**/Password** オプションを省略して **/User** オプションを使用する場合、空白のパスワードが使用されます。</span><span class="sxs-lookup"><span data-stu-id="05655-378">If the **/Password** option is omitted and the **/User** option is used, a blank password is used.</span></span> <span data-ttu-id="05655-379">*password* 値は引用符で囲むことができます。</span><span class="sxs-lookup"><span data-stu-id="05655-379">The *password* value may be quoted.</span></span>  
  
    > [!IMPORTANT]  
    >  [!INCLUDE[ssNoteWinAuthentication](../../../includes/ssnotewinauthentication-md.md)]  
  
-   <span data-ttu-id="05655-380">**/Par [ameter]** [$Package:: | $Project:: | $ServerOption::] *parameter_name* [(data_type)];*literal_value*: 省略可能。</span><span class="sxs-lookup"><span data-stu-id="05655-380">**/Par[ameter]** [$Package:: | $Project:: | $ServerOption::] *parameter_name* [(data_type)]; *literal_value*: Optional.</span></span> <span data-ttu-id="05655-381">パラメーター値を指定します。</span><span class="sxs-lookup"><span data-stu-id="05655-381">Specifies parameter values.</span></span> <span data-ttu-id="05655-382">複数の **/Parameter** オプションを指定できます。</span><span class="sxs-lookup"><span data-stu-id="05655-382">Multiple **/Parameter** options can be specified.</span></span> <span data-ttu-id="05655-383">データ型は、文字列としての CLR TypeCodes です。</span><span class="sxs-lookup"><span data-stu-id="05655-383">The data types are CLR TypeCodes as strings.</span></span> <span data-ttu-id="05655-384">文字列型でないパラメーターの場合、データ型をかっこで囲んで指定してから、続けてパラメーター名を指定します。</span><span class="sxs-lookup"><span data-stu-id="05655-384">For a non-string parameter, the data type is specified in parenthesis, following the parameter name.</span></span>  
  
     <span data-ttu-id="05655-385">**/パラメーター**オプションは、オプションと共にのみ使用でき `/ISServer` ます。</span><span class="sxs-lookup"><span data-stu-id="05655-385">The **/Parameter** option can be used only with the `/ISServer` option.</span></span>  
  
     <span data-ttu-id="05655-386">パッケージ パラメーター、プロジェクト パラメーター、およびサーバー オプション パラメーターを示すには、$Package、$Project、$ServerOption の各プレフィックスをそれぞれ使用します。</span><span class="sxs-lookup"><span data-stu-id="05655-386">You use the $Package, $Project, and $ServerOption prefixes to indicate a package parameter, project parameter, and a server option parameter, respectively.</span></span> <span data-ttu-id="05655-387">既定のパラメーターの型はパッケージです。</span><span class="sxs-lookup"><span data-stu-id="05655-387">The default parameter type is package.</span></span>  
  
     <span data-ttu-id="05655-388">パッケージを実行して、プロジェクト パラメーター (myparam) に myvalue を指定し、パッケージ パラメーター (anotherparam) に整数値 12 を指定する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="05655-388">The following is an example of executing a package and providing myvalue for the project parameter (myparam) and the integer value 12 for the package parameter (anotherparam).</span></span>  
  
     `Dtexec /isserver "SSISDB\MyFolder\MyProject\MyPackage.dtsx" /server "." /parameter $Project::myparam;myvalue /parameter anotherparam(int32);12`  
  
     <span data-ttu-id="05655-389">パラメーターを使用して、接続マネージャーのプロパティを設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="05655-389">You can also set connection manager properties by using parameters.</span></span> <span data-ttu-id="05655-390">接続マネージャーのパラメーターであることを示すには、CM プレフィックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="05655-390">You use the CM prefix to denote a connection manager parameter.</span></span>  
  
     <span data-ttu-id="05655-391">次の例では、SourceServer 接続マネージャーの InitialCatalog プロパティが `ssisdb`に設定されています。</span><span class="sxs-lookup"><span data-stu-id="05655-391">In the following example, InitialCatalog property of the SourceServer connection manager is set to `ssisdb`.</span></span>  
  
    ```  
    /parameter CM.SourceServer.InitialCatalog;ssisdb  
    ```  
  
     <span data-ttu-id="05655-392">次の例では、SourceServer 接続マネージャーの ServerName プロパティが、ローカル サーバーを示すためにピリオド (.) に設定されています。</span><span class="sxs-lookup"><span data-stu-id="05655-392">In the following example, ServerName property of the SourceServer connection manager is set to a period (.) to indicate the local server.</span></span>  
  
    ```  
    /parameter CM.SourceServer.ServerName;.  
    ```  
  
-   <span data-ttu-id="05655-393">**/Proj[ect]** _ProjectFile_:</span><span class="sxs-lookup"><span data-stu-id="05655-393">**/Proj[ect]** _ProjectFile_:</span></span>  
                  <span data-ttu-id="05655-394">省略可能。</span><span class="sxs-lookup"><span data-stu-id="05655-394">Optional.</span></span> <span data-ttu-id="05655-395">実行されるパッケージの取得元となるプロジェクトを指定します。</span><span class="sxs-lookup"><span data-stu-id="05655-395">Specifies the project from which to retrieve the package that is executed.</span></span> <span data-ttu-id="05655-396">*ProjectFile* 引数には、.ispac ファイル名を指定します。</span><span class="sxs-lookup"><span data-stu-id="05655-396">The *ProjectFile* argument specifies the .ispac file name.</span></span> <span data-ttu-id="05655-397">このパラメーターは、 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]からパッケージを実行する場合に主に使用されます。</span><span class="sxs-lookup"><span data-stu-id="05655-397">This parameter is used primarily when you execute the package from [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].</span></span>  
  
-   <span data-ttu-id="05655-398">**/Rem** _comment_:</span><span class="sxs-lookup"><span data-stu-id="05655-398">**/Rem** _comment_:</span></span>  
                  <span data-ttu-id="05655-399">省略可能。</span><span class="sxs-lookup"><span data-stu-id="05655-399">Optional.</span></span> <span data-ttu-id="05655-400">コマンド プロンプトまたはコマンド ファイルにコメントを含めます。</span><span class="sxs-lookup"><span data-stu-id="05655-400">Includes comments on the command prompt or in command files.</span></span> <span data-ttu-id="05655-401">引数は省略可能です。</span><span class="sxs-lookup"><span data-stu-id="05655-401">The argument is optional.</span></span> <span data-ttu-id="05655-402">*comment* の値は、引用符で囲むか、空白を含まない文字列を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="05655-402">The value of *comment* is a string that must be enclosed in quotation marks, or contain no white space.</span></span> <span data-ttu-id="05655-403">引数を指定しない場合、空白行が挿入されます。</span><span class="sxs-lookup"><span data-stu-id="05655-403">If no argument is specified, a blank line is inserted.</span></span> <span data-ttu-id="05655-404">*comment* の値はコマンド初期フェーズで破棄されます。</span><span class="sxs-lookup"><span data-stu-id="05655-404">*comment* values are discarded during the command sourcing phase.</span></span>  
  
-   <span data-ttu-id="05655-405">**/Rep [orting]** _level_ [*; event_guid_or_name*[*; event_guid_or_name*[...]]: 省略可能です。</span><span class="sxs-lookup"><span data-stu-id="05655-405">**/Rep[orting]** _level_ [*;event_guid_or_name*[*;event_guid_or_name*[...]]: Optional.</span></span> <span data-ttu-id="05655-406">レポートするメッセージの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="05655-406">Specifies what types of messages to report.</span></span> <span data-ttu-id="05655-407">*level* に使用できるレポート オプションは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="05655-407">The available reporting options for *level* are as follows:</span></span>  
  
     <span data-ttu-id="05655-408">**N** レポートしません。</span><span class="sxs-lookup"><span data-stu-id="05655-408">**N** No reporting.</span></span>  
  
     <span data-ttu-id="05655-409">`E`エラーが報告されます。</span><span class="sxs-lookup"><span data-stu-id="05655-409">`E` Errors are reported.</span></span>  
  
     <span data-ttu-id="05655-410">**W** 警告がレポートされます。</span><span class="sxs-lookup"><span data-stu-id="05655-410">**W** Warnings are reported.</span></span>  
  
     <span data-ttu-id="05655-411">`I`情報メッセージが報告されます。</span><span class="sxs-lookup"><span data-stu-id="05655-411">`I` Informational messages are reported.</span></span>  
  
     <span data-ttu-id="05655-412">**C** カスタム イベントがレポートされます。</span><span class="sxs-lookup"><span data-stu-id="05655-412">**C** Custom events are reported.</span></span>  
  
     <span data-ttu-id="05655-413">**D** データ フロー タスク イベントがレポートされます。</span><span class="sxs-lookup"><span data-stu-id="05655-413">**D** Data Flow task events are reported.</span></span>  
  
     <span data-ttu-id="05655-414">**P** 進行状況がレポートされます。</span><span class="sxs-lookup"><span data-stu-id="05655-414">**P** Progress is reported.</span></span>  
  
     <span data-ttu-id="05655-415">**V** 詳細がレポートされます。</span><span class="sxs-lookup"><span data-stu-id="05655-415">**V** Verbose reporting.</span></span>  
  
     <span data-ttu-id="05655-416">V および N の引数は、他のすべての引数と同時には使用できないため、単独で指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="05655-416">The arguments of V and N are mutually exclusive to all other arguments; they must be specified alone.</span></span> <span data-ttu-id="05655-417">**/レポート**オプションが指定されていない場合、既定のレベルは `E` (エラー)、 **W** (警告)、および**P** (進行状況) になります。</span><span class="sxs-lookup"><span data-stu-id="05655-417">If the **/Reporting** option is not specified then the default level is `E` (errors), **W** (warnings), and **P** (progress).</span></span>  
  
     <span data-ttu-id="05655-418">すべてのイベントの先頭には、"YY/MM/DD HH:MM:SS" の形式のタイムスタンプが付きます。また使用可能な場合は、GUID または表示名も付加されます。</span><span class="sxs-lookup"><span data-stu-id="05655-418">All events are preceded with a timestamp in the format "YY/MM/DD HH:MM:SS", and a GUID or friendly name if available.</span></span>  
  
     <span data-ttu-id="05655-419">省略可能なパラメーターの *event_guid_or_name* には、ログ プロバイダーに関する例外のリストを指定します。</span><span class="sxs-lookup"><span data-stu-id="05655-419">The optional parameter *event_guid_or_name* is a list of exceptions to the log providers.</span></span> <span data-ttu-id="05655-420">この例外で指定されるイベントは、ログに記録されません。指定されないイベントがログに記録されます。</span><span class="sxs-lookup"><span data-stu-id="05655-420">The exception specifies the events that are not logged that otherwise might have been logged.</span></span>  
  
     <span data-ttu-id="05655-421">既定でログに記録されないイベントは、除外する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="05655-421">You do not have to exclude an event if the event is not ordinarily logged by default</span></span>  
  
-   <span data-ttu-id="05655-422">**/Res [t)]** {*deny | Force | ifpossible ら*れます}: 省略可能です。</span><span class="sxs-lookup"><span data-stu-id="05655-422">**/Res[tart]** {*deny | force | ifPossible*}: Optional.</span></span> <span data-ttu-id="05655-423">パッケージの <xref:Microsoft.SqlServer.Dts.Runtime.Package.CheckpointUsage%2A> プロパティの新しい値を指定します。</span><span class="sxs-lookup"><span data-stu-id="05655-423">Specifies a new value for the <xref:Microsoft.SqlServer.Dts.Runtime.Package.CheckpointUsage%2A> property on the package.</span></span> <span data-ttu-id="05655-424">パラメーターの意味は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="05655-424">The meaning of the parameters are as follows:</span></span>  
  
     <span data-ttu-id="05655-425">*deny* ： <xref:Microsoft.SqlServer.Dts.Runtime.Package.CheckpointUsage%2A> プロパティを <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DTSCheckpointUsage.DTSCU_NEVER>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="05655-425">*Deny* Sets <xref:Microsoft.SqlServer.Dts.Runtime.Package.CheckpointUsage%2A> property to <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DTSCheckpointUsage.DTSCU_NEVER>.</span></span>  
  
     <span data-ttu-id="05655-426">*force* ： <xref:Microsoft.SqlServer.Dts.Runtime.Package.CheckpointUsage%2A> プロパティを <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DTSCheckpointUsage.DTSCU_ALWAYS>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="05655-426">*Force* Sets <xref:Microsoft.SqlServer.Dts.Runtime.Package.CheckpointUsage%2A> property to <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DTSCheckpointUsage.DTSCU_ALWAYS>.</span></span>  
  
     <span data-ttu-id="05655-427">*ifPossible* ： <xref:Microsoft.SqlServer.Dts.Runtime.Package.CheckpointUsage%2A> プロパティを <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DTSCheckpointUsage.DTSCU_IFEXISTS>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="05655-427">*ifPossible* Sets <xref:Microsoft.SqlServer.Dts.Runtime.Package.CheckpointUsage%2A> property to <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DTSCheckpointUsage.DTSCU_IFEXISTS>.</span></span>  
  
     <span data-ttu-id="05655-428">値が指定されない場合は、既定値の **force** が使用されます。</span><span class="sxs-lookup"><span data-stu-id="05655-428">The default value of **force** is used if no value is specified.</span></span>  
  
-   <span data-ttu-id="05655-429">**/Set** [$Sensitive::]*propertyPath; 値*: 省略可能。</span><span class="sxs-lookup"><span data-stu-id="05655-429">**/Set** [$Sensitive::]*propertyPath;value*: Optional.</span></span> <span data-ttu-id="05655-430">パッケージ内のパラメーター、変数、プロパティ、コンテナー、ログ プロバイダー、Foreach 列挙子、または接続の構成をオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="05655-430">Overrides the configuration of a parameter, variable, property, container, log provider, Foreach enumerator, or connection within a package.</span></span> <span data-ttu-id="05655-431">このオプションを指定すると、 **/Set** は *propertyPath* 引数を、指定された値に変更します。</span><span class="sxs-lookup"><span data-stu-id="05655-431">When this option is used, **/Set** changes the *propertyPath* argument to the value specified.</span></span> <span data-ttu-id="05655-432">複数の **/Set** オプションを指定できます。</span><span class="sxs-lookup"><span data-stu-id="05655-432">Multiple **/Set** options can be specified.</span></span>  
  
     <span data-ttu-id="05655-433">**/Set**オプションを **/f [** with the] オプションと共に使用することに加えて、 **/set**オプションをオプションまたはオプションと共に使用することもでき `/ISServer` `/Project` ます。</span><span class="sxs-lookup"><span data-stu-id="05655-433">In addition to using the **/Set** option with the **/F[ile]** option, you can also use the **/Set** option with the `/ISServer` option or the `/Project` option.</span></span> <span data-ttu-id="05655-434">**/Set**をと共に使用すると、/set によって `/Project` パラメーター値が設定されます。 **/Set**</span><span class="sxs-lookup"><span data-stu-id="05655-434">When you use **/Set** with `/Project`, **/Set** sets parameter values.</span></span> <span data-ttu-id="05655-435">**/Set**をと共に使用すると、/set によって `/ISServer` プロパティのオーバーライドが設定されます。 **/Set**</span><span class="sxs-lookup"><span data-stu-id="05655-435">When you use **/Set** with `/ISServer`, **/Set** sets property overrides.</span></span> <span data-ttu-id="05655-436">さらに、 **/set**をと共に使用すると、 `/ISServer` オプションの $Sensitive プレフィックスを使用して、プロパティをサーバーで機微な値として扱う必要があることを示すことができ [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="05655-436">In addition, when you use **/Set** with `/ISServer`, you can use the optional $Sensitive prefix to indicate that the property should be treated as sensitive on the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server.</span></span>  
  
     <span data-ttu-id="05655-437">パッケージ構成ウィザードを実行して、 *propertyPath* の値を確認できます。</span><span class="sxs-lookup"><span data-stu-id="05655-437">You can determine the value of *propertyPath* by running the Package Configuration Wizard.</span></span> <span data-ttu-id="05655-438">最後の **[ウィザードの完了]** ページに選択したアイテムのパスが表示されるので、これをコピーして貼り付けることができます。</span><span class="sxs-lookup"><span data-stu-id="05655-438">The paths for items that you select are displayed on the final **Completing the Wizard** page, and can be copied and pasted.</span></span> <span data-ttu-id="05655-439">この操作のみが目的でウィザードを使用した場合は、パスをコピーした後、ウィザードを取り消してください。</span><span class="sxs-lookup"><span data-stu-id="05655-439">If you have used the wizard only for this purpose, you can cancel the wizard after you copy the paths.</span></span>  
  
     <span data-ttu-id="05655-440">ファイル システムに保存されているパッケージを実行して、変数に新しい値を指定する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="05655-440">The following is an example of executing a package that is saved in the file system and providing a new value for a variable:</span></span>  
  
     `dtexec /f mypackage.dtsx /set \package.variables[myvariable].Value;myvalue`  
  
     <span data-ttu-id="05655-441">.ispac プロジェクト ファイルからパッケージを実行して、パッケージとプロジェクトのパラメーターを指定する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="05655-441">The following example of running a package from the .ispac project file and setting package and project parameters.</span></span>  
  
     `/Project c:\project.ispac /Package Package1.dtsx /SET \Package.Variables[$Package::Parameter];1 /SET \Package.Variables[$Project::Parameter];1`  
  
     <span data-ttu-id="05655-442">**/Set** オプションを使用すると、パッケージ構成を読み込む場所を変更することができます。</span><span class="sxs-lookup"><span data-stu-id="05655-442">You can use the **/Set** option to change the location from which package configurations are loaded.</span></span> <span data-ttu-id="05655-443">ただし、 **/Set** オプションを使用しても、デザイン時の構成で指定した値をオーバーライドすることはできません。</span><span class="sxs-lookup"><span data-stu-id="05655-443">However, you cannot use the **/Set** option to override a value that was specified by a configuration at design time.</span></span> <span data-ttu-id="05655-444">パッケージ構成の適用方法については、「[パッケージの構成](../package-configurations.md)と[動作の変更」を参照して SQL Server 2014 の Integration Services 機能を](../behavior-changes-to-integration-services-features-in-sql-server-2014.md)確認してください。</span><span class="sxs-lookup"><span data-stu-id="05655-444">To understand how package configurations are applied, see [Package Configurations](../package-configurations.md) and [Behavior Changes to Integration Services Features in SQL Server 2014](../behavior-changes-to-integration-services-features-in-sql-server-2014.md).</span></span>  
  
-   <span data-ttu-id="05655-445">`/Ser[ver]`*サーバー*:</span><span class="sxs-lookup"><span data-stu-id="05655-445">`/Ser[ver]` *server*:</span></span>  
                  <span data-ttu-id="05655-446">省略可能。</span><span class="sxs-lookup"><span data-stu-id="05655-446">Optional.</span></span> <span data-ttu-id="05655-447">`/SQL` オプションまたは `/DTS` オプションが指定されている場合、このオプションにはパッケージを取得するサーバーの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="05655-447">When the `/SQL` or `/DTS` option is specified, this option specifies the name of the server from which to retrieve the package.</span></span> <span data-ttu-id="05655-448">`/Server` オプションを省略して `/SQL` または `/DTS` オプションを指定した場合、ローカル サーバーに対してパッケージの実行が試行されます。</span><span class="sxs-lookup"><span data-stu-id="05655-448">If you omit the `/Server` option and the `/SQL` or `/DTS` option is specified, package execution is tried against the local server.</span></span> <span data-ttu-id="05655-449">*server_instance* 値は引用符で囲むことができます。</span><span class="sxs-lookup"><span data-stu-id="05655-449">The *server_instance* value may be quoted.</span></span>  
  
     <span data-ttu-id="05655-450">`/Ser[ver]` オプションが指定されている場合、`/ISServer` オプションは必須です。</span><span class="sxs-lookup"><span data-stu-id="05655-450">The `/Ser[ver]` option is required when the `/ISServer` option is specified.</span></span>  
  
-   <span data-ttu-id="05655-451">**/SQ[L]** _package_path_:</span><span class="sxs-lookup"><span data-stu-id="05655-451">**/SQ[L]** _package_path_:</span></span>  
                  <span data-ttu-id="05655-452">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の `msdb` データベースに格納されているパッケージを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="05655-452">Loads a package that is stored in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], in `msdb` database.</span></span> <span data-ttu-id="05655-453">`msdb` データベースに格納されているパッケージは、パッケージ配置モデルを使用して配置されます。</span><span class="sxs-lookup"><span data-stu-id="05655-453">Packages that are stored in the `msdb` database, are deployed using the package deployment model.</span></span> <span data-ttu-id="05655-454">プロジェクト配置モデルを使用して、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サーバーに配置されているパッケージを実行するには、`/ISServer` オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="05655-454">To run packages that are deployed to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server using the project deployment model, use the `/ISServer` option.</span></span> <span data-ttu-id="05655-455">パッケージとプロジェクトの配置モデルの詳細については、「 [Deployment of Projects and Packages](deploy-integration-services-ssis-projects-and-packages.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="05655-455">For more information about the package and project deployment models, see [Deployment of Projects and Packages](deploy-integration-services-ssis-projects-and-packages.md).</span></span>  
  
     <span data-ttu-id="05655-456">*package_path* 引数には、取得するパッケージの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="05655-456">The *package_path* argument specifies the name of the package to retrieve.</span></span> <span data-ttu-id="05655-457">パス名を指定する場合、パス内のフォルダーの最後には円記号 ("\\") を指定します。</span><span class="sxs-lookup"><span data-stu-id="05655-457">If folders are included in the path, they are terminated with backslashes ("\\").</span></span> <span data-ttu-id="05655-458">*Package_path* 値は引用符で囲むことができます。</span><span class="sxs-lookup"><span data-stu-id="05655-458">The *package_path* value can be quoted.</span></span> <span data-ttu-id="05655-459">*package_path* 引数に指定するパスまたはファイル名に空白文字を含める場合は、 *package_path* 引数を引用符で囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="05655-459">If the path or file name specified in the *package_path* argument contains a space, you must put quotation marks around the *package_path* argument.</span></span>  
  
     <span data-ttu-id="05655-460">**/User**、 **/password**、およびオプションをオプションと共に使用でき `/Server` `/SQL` ます。</span><span class="sxs-lookup"><span data-stu-id="05655-460">You can use the **/User**, **/Password**, and `/Server` options together with the `/SQL` option.</span></span>  
  
     <span data-ttu-id="05655-461">**/User** オプションを省略した場合、パッケージへのアクセスに Windows 認証が使用されます。</span><span class="sxs-lookup"><span data-stu-id="05655-461">If you omit the **/User** option, Windows Authentication is used to access the package.</span></span> <span data-ttu-id="05655-462">**/User** オプションを使用する場合、指定する **/User** ログイン名は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証に関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="05655-462">If you use the **/User** option, the **/User** login name specified is associated with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
     <span data-ttu-id="05655-463">**/Password** オプションは、 **/User** オプションと共に使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="05655-463">The **/Password** option is used only together with the **/User** option.</span></span> <span data-ttu-id="05655-464">**/Password** オプションを使用する場合、パッケージは指定されたユーザー名とパスワード情報を使用してアクセスされます。</span><span class="sxs-lookup"><span data-stu-id="05655-464">If you use the **/Password** option, the package is accessed with the user name and password information provided.</span></span> <span data-ttu-id="05655-465">**/Password** オプションを省略した場合、空白のパスワードが使用されます。</span><span class="sxs-lookup"><span data-stu-id="05655-465">If you omit the **/Password** option, a blank password is used.</span></span>  
  
    > [!IMPORTANT]  
    >  [!INCLUDE[ssNoteWinAuthentication](../../../includes/ssnotewinauthentication-md.md)]  
  
     <span data-ttu-id="05655-466">`/Server` オプションを省略した場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の既定のローカル インスタンスが使用されます。</span><span class="sxs-lookup"><span data-stu-id="05655-466">If the `/Server` option is omitted, the default local instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is assumed.</span></span>  
  
     <span data-ttu-id="05655-467">`/SQL` オプションは、`/DTS` または `/File` オプションと共に使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="05655-467">The `/SQL` option cannot be used together with the `/DTS` or `/File` option.</span></span> <span data-ttu-id="05655-468">複数のオプションが指定された場合、`dtexec` は失敗します。</span><span class="sxs-lookup"><span data-stu-id="05655-468">If multiple options are specified, `dtexec` fails.</span></span>  
  
-   <span data-ttu-id="05655-469">**/Su [m]**: 省略可能。</span><span class="sxs-lookup"><span data-stu-id="05655-469">**/Su[m]**: Optional.</span></span> <span data-ttu-id="05655-470">後続のコンポーネントが受け取る行数を示す増分カウンターを表示します。</span><span class="sxs-lookup"><span data-stu-id="05655-470">Shows an incremental counter that contains the number of rows that will be received by the next component.</span></span>  
  
-   <span data-ttu-id="05655-471">**/U [ser]** _user_name_:</span><span class="sxs-lookup"><span data-stu-id="05655-471">**/U[ser]** _user_name_:</span></span>  
                  <span data-ttu-id="05655-472">省略可能。</span><span class="sxs-lookup"><span data-stu-id="05655-472">Optional.</span></span> <span data-ttu-id="05655-473">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証によって保護されているパッケージの取得を可能にします。</span><span class="sxs-lookup"><span data-stu-id="05655-473">Allows the retrieval of a package that is protected by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="05655-474">このオプションは、`/SQL` オプションが指定されている場合にのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="05655-474">This option is used only when the `/SQL` option is specified.</span></span> <span data-ttu-id="05655-475">*User_name* 値は引用符で囲むことができます。</span><span class="sxs-lookup"><span data-stu-id="05655-475">The *user_name* value can be quoted.</span></span>  
  
    > [!IMPORTANT]  
    >  [!INCLUDE[ssNoteWinAuthentication](../../../includes/ssnotewinauthentication-md.md)]  
  
-   <span data-ttu-id="05655-476">**/Va [lidate]**:</span><span class="sxs-lookup"><span data-stu-id="05655-476">**/Va[lidate]**:</span></span>  
                  <span data-ttu-id="05655-477">省略可能。</span><span class="sxs-lookup"><span data-stu-id="05655-477">Optional.</span></span> <span data-ttu-id="05655-478">検証フェーズ後、パッケージの実行を停止します。パッケージは実際には実行されません。</span><span class="sxs-lookup"><span data-stu-id="05655-478">Stops the execution of the package after the validatation phase, without actually running the package.</span></span> <span data-ttu-id="05655-479">検証中に、 **/WarnAsError**オプションを使用すると、は `dtexec` 警告をエラーとして処理するため、検証中に警告が発生した場合、パッケージは失敗します。</span><span class="sxs-lookup"><span data-stu-id="05655-479">During validation, use of the **/WarnAsError** option causes `dtexec` to treat a warning as an error; therefore the package fails if a warning occurs during validation.</span></span>  
  
-   <span data-ttu-id="05655-480">**/Verifyb [u)]** _major_[*; minor*[*; build*]]: 省略可能。</span><span class="sxs-lookup"><span data-stu-id="05655-480">**/VerifyB[uild]** _major_[*;minor*[*;build*]]: Optional.</span></span> <span data-ttu-id="05655-481">検証フェーズ中に、パッケージのビルド番号を、 *major*、 *minor*、および *build* 引数に指定されたビルド番号に対して検証します。</span><span class="sxs-lookup"><span data-stu-id="05655-481">Verifies the build number of a package against the build numbers that were specified during the verification phase in the *major*, *minor*, and *build* arguments.</span></span> <span data-ttu-id="05655-482">不一致が発生した場合、パッケージは実行されません。</span><span class="sxs-lookup"><span data-stu-id="05655-482">If a mismatch occurs, the package will not execute.</span></span>  
  
     <span data-ttu-id="05655-483">値は長整数型です。</span><span class="sxs-lookup"><span data-stu-id="05655-483">The values are long integers.</span></span> <span data-ttu-id="05655-484">引数は次の 3 つの形式のいずれかになります。 *major* の値は必須です。</span><span class="sxs-lookup"><span data-stu-id="05655-484">The argument can have one of three forms, with a value for *major* always required:</span></span>  
  
    -   <span data-ttu-id="05655-485">*major*</span><span class="sxs-lookup"><span data-stu-id="05655-485">*major*</span></span>  
  
    -   <span data-ttu-id="05655-486">*major*;*minor*</span><span class="sxs-lookup"><span data-stu-id="05655-486">*major*;*minor*</span></span>  
  
    -   <span data-ttu-id="05655-487">*major*; *minor*; *build*</span><span class="sxs-lookup"><span data-stu-id="05655-487">*major*; *minor*; *build*</span></span>  
  
-   <span data-ttu-id="05655-488">**/VerifyP[ackageID]** _packageID_:</span><span class="sxs-lookup"><span data-stu-id="05655-488">**/VerifyP[ackageID]** _packageID_:</span></span>  
                  <span data-ttu-id="05655-489">省略可能。</span><span class="sxs-lookup"><span data-stu-id="05655-489">Optional.</span></span> <span data-ttu-id="05655-490">実行するパッケージの GUID を、 *package_id* 引数に指定された値と比較して検証します。</span><span class="sxs-lookup"><span data-stu-id="05655-490">Verifies the GUID of the package to be executed by comparing it to the value specified in the *package_id* argument.</span></span>  
  
-   <span data-ttu-id="05655-491">**/VerifyS[igned]**:</span><span class="sxs-lookup"><span data-stu-id="05655-491">**/VerifyS[igned]**:</span></span>  
                  <span data-ttu-id="05655-492">省略可能。</span><span class="sxs-lookup"><span data-stu-id="05655-492">Optional.</span></span> <span data-ttu-id="05655-493">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] でパッケージのデジタル署名を確認します。</span><span class="sxs-lookup"><span data-stu-id="05655-493">Causes [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] to check the digital signature of the package.</span></span> <span data-ttu-id="05655-494">パッケージが署名されていないか、署名が有効でない場合、パッケージは失敗します。</span><span class="sxs-lookup"><span data-stu-id="05655-494">If the package is not signed or the signature is not valid, the package fails.</span></span> <span data-ttu-id="05655-495">詳細については、「 [デジタル署名を使用してパッケージのソースを特定する](../security/identify-the-source-of-packages-with-digital-signatures.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="05655-495">For more information, see [Identify the Source of Packages with Digital Signatures](../security/identify-the-source-of-packages-with-digital-signatures.md).</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="05655-496">パッケージの署名を確認するように構成した場合、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] によって確認されるのは、デジタル署名が存在するかどうか、有効かどうか、および信頼関係のある発行元の署名であるかどうかのみです。</span><span class="sxs-lookup"><span data-stu-id="05655-496">When configured to check the signature of the package, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] only checks whether the digital signature is present, is valid, and is from a trusted source.</span></span> [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="05655-497">では、パッケージが変更されたかどうかは確認されません。</span><span class="sxs-lookup"><span data-stu-id="05655-497">does not check whether the package has been changed.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="05655-498">オプションの**BlockedSignatureStates**レジストリ値で [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] は、またはコマンドラインで設定されたデジタル署名オプションよりも制限が厳しい設定を指定でき `dtexec` ます。</span><span class="sxs-lookup"><span data-stu-id="05655-498">The optional **BlockedSignatureStates** registry value can specify a setting that is more restrictive than the digital signature option set in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] or at the `dtexec` command line.</span></span> <span data-ttu-id="05655-499">この場合、制限が厳しい方のレジストリ設定が他の設定をオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="05655-499">In this situation, the more restrictive registry setting overrides the other settings.</span></span>  
  
-   <span data-ttu-id="05655-500">**/Verifyv [Er、id]** _versionID_: 省略可能。</span><span class="sxs-lookup"><span data-stu-id="05655-500">**/VerifyV[ersionID]** _versionID_: Optional.</span></span> <span data-ttu-id="05655-501">パッケージの検証フェーズ中に、実行されるパッケージのバージョン GUID を *version_id* 引数に指定された値と比較して検証します。</span><span class="sxs-lookup"><span data-stu-id="05655-501">Verifies the version GUID of a package to be executed by comparing it to the value specified in the *version_id* argument during package Validation Phase.</span></span>  
  
-   <span data-ttu-id="05655-502">**/VLog** _[Filespec]_: 省略可能。</span><span class="sxs-lookup"><span data-stu-id="05655-502">**/VLog** _[Filespec]_: Optional.</span></span> <span data-ttu-id="05655-503">すべての Integration Services パッケージ イベントを、パッケージの設計時に有効にしたログ プロバイダーに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="05655-503">Writes all Integration Services package events to the log providers that were enabled when the package was designed.</span></span> <span data-ttu-id="05655-504">Integration Services でテキスト ファイルのログ プロバイダーを有効にし、指定したテキスト ファイルにログ イベントを書き込むには、パスとファイル名を *Filespec* パラメーターとして含めます。</span><span class="sxs-lookup"><span data-stu-id="05655-504">To have Integration Services enable a log provider for text files and write log events to a specified text file, include a path and file name as the *Filespec* parameter.</span></span>  
  
     <span data-ttu-id="05655-505">*Filespec* パラメーターを含めない場合、Integration Services でテキスト ファイルのログ プロバイダーが有効になりません。</span><span class="sxs-lookup"><span data-stu-id="05655-505">If you do not include the *Filespec* parameter, Integration Services will not enable a log provider for text files.</span></span> <span data-ttu-id="05655-506">Integration Services では、パッケージの設計時に有効にしたログ プロバイダーに対してのみ、ログ イベントが書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="05655-506">Integration Services will only write log events to the log providers that were enabled when the package was designed.</span></span>  
  
-   <span data-ttu-id="05655-507">**/W [arnAsError]**:</span><span class="sxs-lookup"><span data-stu-id="05655-507">**/W[arnAsError]**:</span></span>  
                  <span data-ttu-id="05655-508">省略可能。</span><span class="sxs-lookup"><span data-stu-id="05655-508">Optional.</span></span> <span data-ttu-id="05655-509">パッケージは警告をエラーと判断するので、検証中に警告が発生した場合にはパッケージが失敗します。</span><span class="sxs-lookup"><span data-stu-id="05655-509">Causes the package to consider a warning as an error; therefore, the package will fail if a warning occurs during validation.</span></span> <span data-ttu-id="05655-510">検証中に警告が発生せず、 **/Validate** オプションが指定されていない場合、パッケージは実行されます。</span><span class="sxs-lookup"><span data-stu-id="05655-510">If no warnings occur during validation and the **/Validate** option is not specified, the package is executed.</span></span>  
  
-   <span data-ttu-id="05655-511">**/X86**: 省略可能。</span><span class="sxs-lookup"><span data-stu-id="05655-511">**/X86**: Optional.</span></span> <span data-ttu-id="05655-512">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントは 64 ビット コンピューター上で 32 ビット モードでパッケージを実行します。</span><span class="sxs-lookup"><span data-stu-id="05655-512">Causes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to run the package in 32-bit mode on a 64-bit computer.</span></span> <span data-ttu-id="05655-513">このオプションは、次に示す条件が満たされた場合に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントによって設定されます。</span><span class="sxs-lookup"><span data-stu-id="05655-513">This option is set by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent when the following conditions are true:</span></span>  
  
    -   <span data-ttu-id="05655-514">ジョブ ステップの種類が **[SQL Server Integration Services パッケージ]** であること。</span><span class="sxs-lookup"><span data-stu-id="05655-514">The job step type is **SQL Server Integration Services package**.</span></span>  
  
    -   <span data-ttu-id="05655-515">**[新しいジョブ ステップ]** ダイアログ ボックスの **[実行オプション]** タブで **[32 ビット ランタイムを使用]** オプションが選択されていること。</span><span class="sxs-lookup"><span data-stu-id="05655-515">The **Use 32 bit runtime** option on the **Execution options** tab of the **New Job Step** dialog box is selected.</span></span>  
  
     <span data-ttu-id="05655-516">このオプションは、ストアド プロシージャまたは SQL Server 管理オブジェクト (SMO) を使用してジョブをプログラムにより作成することで、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブ ステップに設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="05655-516">You can also set this option for a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job step by using stored procedures or SQL Server Management Objects (SMO) to programmatically create the job.</span></span>  
  
     <span data-ttu-id="05655-517">このオプションは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのみに使用されます。</span><span class="sxs-lookup"><span data-stu-id="05655-517">This option is only used by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span> <span data-ttu-id="05655-518">コマンド プロンプトで `dtexec` ユーティリティを実行している場合、このオプションは無視されます。</span><span class="sxs-lookup"><span data-stu-id="05655-518">This option is ignored if you run the `dtexec` utility at the command prompt.</span></span>  
  
##  <a name="remarks"></a><a name="remark"></a> <span data-ttu-id="05655-519">解説</span><span class="sxs-lookup"><span data-stu-id="05655-519">Remarks</span></span>  
 <span data-ttu-id="05655-520">コマンド オプションの指定順序は、パッケージの実行方法に影響します。</span><span class="sxs-lookup"><span data-stu-id="05655-520">The order in which you specify command options can influence the way in which the package executes:</span></span>  
  
-   <span data-ttu-id="05655-521">オプションは、コマンド ライン上で指定されている順に処理されます。</span><span class="sxs-lookup"><span data-stu-id="05655-521">Options are processed in the order they are encountered on the command line.</span></span> <span data-ttu-id="05655-522">コマンド ファイルは、コマンド ラインで指定されているとおりに読み取られます。</span><span class="sxs-lookup"><span data-stu-id="05655-522">Command files are read in as they are encountered on the command line.</span></span> <span data-ttu-id="05655-523">コマンド ファイル内のコマンドも指定されている順に処理されます。</span><span class="sxs-lookup"><span data-stu-id="05655-523">The commands in the command file are also processed in the order they are encountered.</span></span>  
  
-   <span data-ttu-id="05655-524">同じオプション、パラメーター、または変数が、同じコマンド ライン ステートメントに複数指定されている場合は、最後に指定されているものが優先されます。</span><span class="sxs-lookup"><span data-stu-id="05655-524">If the same option, parameter, or variable appears in the same command line statement more than one time, the last instance of the option takes precedence.</span></span>  
  
-   <span data-ttu-id="05655-525">**/Set** オプションと **/ConfigFile** オプションは、指定されている順に処理されます。</span><span class="sxs-lookup"><span data-stu-id="05655-525">**/Set** and **/ConfigFile** options are processed in the order they are encountered.</span></span>  
  
##  <a name="examples"></a><a name="example"></a> <span data-ttu-id="05655-526">使用例</span><span class="sxs-lookup"><span data-stu-id="05655-526">Examples</span></span>  
 <span data-ttu-id="05655-527">次の例では、 `dtexec` コマンドプロンプトユーティリティを使用してパッケージを構成および実行する方法を示し [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="05655-527">The following examples demonstrate how to use the `dtexec` command prompt utility to configure and execute [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages.</span></span>  
  
 <span data-ttu-id="05655-528">**パッケージの実行**</span><span class="sxs-lookup"><span data-stu-id="05655-528">**Running Packages**</span></span>  
  
 <span data-ttu-id="05655-529">Windows 認証を使用する [!INCLUDE[ssIS](../../includes/ssis-md.md)] に保存されている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] パッケージを実行するには、次のコードを使用します。</span><span class="sxs-lookup"><span data-stu-id="05655-529">To execute an [!INCLUDE[ssIS](../../includes/ssis-md.md)] package saved to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using Windows Authentication, use the following code:</span></span>  
  
```  
dtexec /sq pkgOne /ser productionServer  
```  
  
 <span data-ttu-id="05655-530">SSIS パッケージ ストアの [ファイル システム] フォルダーに保存されている [!INCLUDE[ssIS](../../includes/ssis-md.md)] パッケージを実行するには、次のコードを使用します。</span><span class="sxs-lookup"><span data-stu-id="05655-530">To execute an [!INCLUDE[ssIS](../../includes/ssis-md.md)] package saved to the File System folder in the SSIS Package Store, use the following code:</span></span>  
  
```  
dtexec /dts "\File System\MyPackage"  
```  
  
 <span data-ttu-id="05655-531">Windows 認証が使用されていて、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に保存されているパッケージを実行せずに検証するには、次のコードを使用します。</span><span class="sxs-lookup"><span data-stu-id="05655-531">To validate a package that uses Windows Authentication and is saved in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] without executing the package, use the following code:</span></span>  
  
```  
dtexec /sq pkgOne /ser productionServer /va  
```  
  
 <span data-ttu-id="05655-532">ファイル システムに保存されている [!INCLUDE[ssIS](../../includes/ssis-md.md)] パッケージを実行するには、次のコードを使用します。</span><span class="sxs-lookup"><span data-stu-id="05655-532">To execute an [!INCLUDE[ssIS](../../includes/ssis-md.md)] package that is saved in the file system, use the following code:</span></span>  
  
```  
dtexec /f "c:\pkgOne.dtsx"   
```  
  
 <span data-ttu-id="05655-533">ファイル システムに保存されている [!INCLUDE[ssIS](../../includes/ssis-md.md)] パッケージの実行、およびログ オプションの指定を行うには、次のコードを使用します。</span><span class="sxs-lookup"><span data-stu-id="05655-533">To execute an [!INCLUDE[ssIS](../../includes/ssis-md.md)] package that is saved in the file system, and specify logging options, use the following code:</span></span>  
  
```  
dtexec /f "c:\pkgOne.dtsx" /l "DTS.LogProviderTextFile;c:\log.txt"  
```  
  
 <span data-ttu-id="05655-534">Windows 認証が使用され、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の既定のローカル インスタンスに保存されているパッケージの実行、および実行前にバージョンの確認を行うには、次のコードを使用します。</span><span class="sxs-lookup"><span data-stu-id="05655-534">To execute a package that uses Windows Authentication and is saved to the default local instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], and verify the version before it is executed, use the following code:</span></span>  
  
```  
dtexec /sq pkgOne /verifyv {c200e360-38c5-11c5-11ce-ae62-08002b2b79ef}  
```  
  
 <span data-ttu-id="05655-535">ファイル システムに保存されているが、外部で構成されている [!INCLUDE[ssIS](../../includes/ssis-md.md)] パッケージを実行するには、次のコードを使用します。</span><span class="sxs-lookup"><span data-stu-id="05655-535">To execute an [!INCLUDE[ssIS](../../includes/ssis-md.md)] package that is saved in the file system and configured externally, use the following code:</span></span>  
  
```  
dtexec /f "c:\pkgOne.dtsx" /conf "c:\pkgOneConfig.cfg"  
```  
  
> [!NOTE]  
>  <span data-ttu-id="05655-536">/SQL、/DTS、または /FILE オプションの *package_path* または *filespec* 引数は、パスまたはファイル名に空白文字が含まれる場合、引用符で囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="05655-536">The *package_path* or *filespec* arguments of the /SQL, /DTS, or /FILE options must be enclosed in quotation marks if the path or file name contains a space.</span></span> <span data-ttu-id="05655-537">引数を引用符で囲まないと、空白文字を引数に含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="05655-537">If the argument is not enclosed in quotation marks, the argument cannot contain white space.</span></span>  
  
 <span data-ttu-id="05655-538">**ログ オプション**</span><span class="sxs-lookup"><span data-stu-id="05655-538">**Logging Option**</span></span>  
  
 <span data-ttu-id="05655-539">ログ エントリの種類が A、B、C の 3 つある場合、次のように、パラメーターを指定せずに **ConsoleLog** オプションを使用すると、3 つすべてのログの種類がすべてのフィールドと共に表示されます。</span><span class="sxs-lookup"><span data-stu-id="05655-539">If there are three log entry types of A, B, and C, the following **ConsoleLog** option without a parameter displays all three log types with all fields:</span></span>  
  
```  
/CONSOLELOG  
```  
  
 <span data-ttu-id="05655-540">次のオプションを指定すると、すべてのログの種類が、Name 列および Message 列のみと共に表示されます。</span><span class="sxs-lookup"><span data-stu-id="05655-540">The following option displays all log types, but with the Name and Message columns only:</span></span>  
  
```  
/CONSOLELOG NM  
```  
  
 <span data-ttu-id="05655-541">次のオプションを指定すると、A の種類のログ エントリのみが、すべての列と共に表示されます。</span><span class="sxs-lookup"><span data-stu-id="05655-541">The following option displays all columns, but only for log entry type A:</span></span>  
  
```  
/CONSOLELOG I;LogEntryTypeA  
```  
  
 <span data-ttu-id="05655-542">次のオプションを指定すると、A の種類のログ エントリのみが Name 列および Message 列と共に表示されます。</span><span class="sxs-lookup"><span data-stu-id="05655-542">The following option displays only log entry type A, with Name and Message columns:</span></span>  
  
```  
/CONSOLELOG NM;I;LogEntryTypeA  
```  
  
 <span data-ttu-id="05655-543">次のオプションを指定すると、A および B の種類のログ エントリが表示されます。</span><span class="sxs-lookup"><span data-stu-id="05655-543">The following option displays log entries for log entry types A and B:</span></span>  
  
```  
/CONSOLELOG I;LogEntryTypeA;LogEntryTypeB  
```  
  
 <span data-ttu-id="05655-544">複数の **ConsoleLog** オプションを指定すると、同じ結果を得ることができます。</span><span class="sxs-lookup"><span data-stu-id="05655-544">You can achieve the same results by using multiple **ConsoleLog** options:</span></span>  
  
```  
/CONSOLELOG I;LogEntryTypeA /CONSOLELOG I;LogEntryTypeB  
```  
  
 <span data-ttu-id="05655-545">パラメーターなしで **ConsoleLog** オプションを指定すると、すべてのフィールドが表示されます。</span><span class="sxs-lookup"><span data-stu-id="05655-545">If the **ConsoleLog** option is used without parameters, all fields are displayed.</span></span> <span data-ttu-id="05655-546">次の指定に *list_options* パラメーターを含めると、A の種類のログ エントリのみがすべてのフィールドと共に表示されます。</span><span class="sxs-lookup"><span data-stu-id="05655-546">The inclusion of a *list_options* parameter causes the following to displays only log entry type A, with all fields:</span></span>  
  
```  
/CONSOLELOG NM;I;LogEntryTypeA /CONSOLELOG  
```  
  
 <span data-ttu-id="05655-547">次の例では、種類 A のログ エントリを除くすべてのログ エントリ (種類 B と C) が表示されます。</span><span class="sxs-lookup"><span data-stu-id="05655-547">The following displays all log entries except log entry type A: that is, it displays log entry types B and C:</span></span>  
  
```  
/CONSOLELOG E;LogEntryTypeA  
```  
  
 <span data-ttu-id="05655-548">次のように複数の **ConsoleLog** オプションを使用し、単一のログ エントリを除外することで、前の例と同じ結果が得られます。</span><span class="sxs-lookup"><span data-stu-id="05655-548">The following example achieves the same results by using multiple **ConsoleLog** options and a single exclusion:</span></span>  
  
```  
/CONSOLELOG E;LogEntryTypeA /CONSOLELOG  
/CONSOLELOG E;LogEntryTypeA /CONSOLELOG E;LogEntryTypeA  
/CONSOLELOG E;LogEntryTypeA;LogEntryTypeA  
```  
  
 <span data-ttu-id="05655-549">ログ ファイルの種類が包含一覧と除外一覧の両方に指定されている場合、そのログ ファイルは除外されるため、次の例ではログ メッセージは表示されません。</span><span class="sxs-lookup"><span data-stu-id="05655-549">The following example displays no log messages, because when a log file type is found in both the included and excluded lists, it will be excluded.</span></span>  
  
```  
/CONSOLELOG E;LogEntryTypeA /CONSOLELOG I;LogEntryTypeA  
```  
  
 <span data-ttu-id="05655-550">**SET オプション**</span><span class="sxs-lookup"><span data-stu-id="05655-550">**SET Option**</span></span>  
  
 <span data-ttu-id="05655-551">**/SET** オプションの使用方法の例を次に示します。これは、パッケージのプロパティ値または変数値をコマンド ラインからパッケージを起動するときに変更します。</span><span class="sxs-lookup"><span data-stu-id="05655-551">The following example shows how to use the **/SET** option, which lets you change the value of any package property or variable when you start the package from the command line.</span></span>  
  
```  
/SET \package\DataFlowTask.Variables[User::MyVariable].Value;newValue  
```  
  
 <span data-ttu-id="05655-552">**プロジェクトのオプション**</span><span class="sxs-lookup"><span data-stu-id="05655-552">**Project Option**</span></span>  
  
 <span data-ttu-id="05655-553">次の例は、`/Project` オプションと `/Package` オプションを使用する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="05655-553">The following example shows how to use the `/Project` and the `/Package` option.</span></span>  
  
```  
/Project c:\project.ispac /Package Package1.dtsx  
```  
  
 <span data-ttu-id="05655-554">次の例は、`/Project` オプションと `/Package` オプションを使用してパッケージとプロジェクトのパラメーターを設定する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="05655-554">The following example shows how to use the `/Project` and `/Package` options, and set package and project parameters.</span></span>  
  
```  
/Project c:\project.ispac /Package Package1.dtsx /SET \Package.Variables[$Package::Parameter];1 /SET \Package.Variables[$Project::Parameter];1  
  
```  
  
 <span data-ttu-id="05655-555">**ISServer のオプション**</span><span class="sxs-lookup"><span data-stu-id="05655-555">**ISServer Option**</span></span>  
  
 <span data-ttu-id="05655-556">次の例は `/ISServer` オプションを使用する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="05655-556">The following example shows how to use the `/ISServer` option.</span></span>  
  
```  
dtexec /isserver "\SSISDB\MyFolder\MyProject\MyPackage.dtsx" /server "."  
```  
  
 <span data-ttu-id="05655-557">次の例は、`/ISServer` オプションを使用してプロジェクトと接続マネージャーのパラメーターを設定する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="05655-557">The following example shows how to use the `/ISServer` option and set project and connection manager parameters.</span></span>  
  
```  
/Server localhost /ISServer "\SSISDB\MyFolder\Integration Services Project1\Package.dtsx" /Par "$Project::ProjectParameter(Int32)";1 /Par "CM.SourceServer.InitialCatalog";SourceDB  
  
```  
  
## <a name="related-tasks"></a><span data-ttu-id="05655-558">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="05655-558">Related Tasks</span></span>  
 [<span data-ttu-id="05655-559">SQL Server Data Tools でのパッケージの実行</span><span class="sxs-lookup"><span data-stu-id="05655-559">Run a Package in SQL Server Data Tools</span></span>](../run-a-package-in-sql-server-data-tools.md)  
  
## <a name="related-content"></a><span data-ttu-id="05655-560">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="05655-560">Related Content</span></span>  
 <span data-ttu-id="05655-561">[www.mattmasson.com](www.mattmasson.com) のブログ エントリ「 [終了コード、DTEXEC、および SSIS カタログ](https://www.mattmasson.com/2012/02/exit-codes-dtexec-and-ssis-catalog/)」</span><span class="sxs-lookup"><span data-stu-id="05655-561">Blog entry, [Exit Codes, DTEXEC, and SSIS Catalog](https://www.mattmasson.com/2012/02/exit-codes-dtexec-and-ssis-catalog/), on www.mattmasson.com.</span></span>  
  
  
