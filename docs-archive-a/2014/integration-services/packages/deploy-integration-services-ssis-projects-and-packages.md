---
title: プロジェクトとパッケージの配置 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: bea8ce8d-cf63-4257-840a-fc9adceade8c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: fc225cf962a127cbce91051a83d3c80cb20003eb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718542"
---
# <a name="deployment-of-projects-and-packages"></a><span data-ttu-id="47302-102">プロジェクトとパッケージの展開</span><span class="sxs-lookup"><span data-stu-id="47302-102">Deployment of Projects and Packages</span></span>
  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="47302-103">では、プロジェクト配置モデルとパッケージ配置モデルの 2 つの配置モデルがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="47302-103">supports two deployment models, the project deployment model and the package deployment model.</span></span> <span data-ttu-id="47302-104">プロジェクト配置モデルを使用すると、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サーバーにプロジェクトを配置できます。</span><span class="sxs-lookup"><span data-stu-id="47302-104">The project deployment model enables you to deploy your projects to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server.</span></span>  
  
 <span data-ttu-id="47302-105">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サーバーへのプロジェクトの配置の詳細については、「 [Integration Services サーバーへのプロジェクトの配置](../deploy-projects-to-integration-services-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="47302-105">For more information about deploying projects to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server, see [Deploy Projects to Integration Services Server](../deploy-projects-to-integration-services-server.md).</span></span>  
  
 <span data-ttu-id="47302-106">パッケージ配置モデルの詳細については、「[パッケージ配置 &#40;SSIS&#41;](legacy-package-deployment-ssis.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="47302-106">For more information about the package deployment model, see [Package Deployment &#40;SSIS&#41;](legacy-package-deployment-ssis.md).</span></span>  
  
## <a name="compare-project-deployment-and-package-deployment"></a><span data-ttu-id="47302-107">プロジェクト配置とパッケージ配置の比較</span><span class="sxs-lookup"><span data-stu-id="47302-107">Compare Project Deployment and Package Deployment</span></span>  
 <span data-ttu-id="47302-108">プロジェクトに対して選択する配置モデルの種類によって、そのプロジェクトに使用できる開発オプションと管理オプションが決まります。</span><span class="sxs-lookup"><span data-stu-id="47302-108">The type of deployment model that you choose for a project determines which development and administrative options are available for that project.</span></span> <span data-ttu-id="47302-109">次の表に、プロジェクト配置モデルを使用した場合とパッケージ配置モデルを使用した場合の相違点と共通点を示します。</span><span class="sxs-lookup"><span data-stu-id="47302-109">The following table shows the differences and similarities between using the project deployment model and using the package deployment model.</span></span>  
  
|<span data-ttu-id="47302-110">プロジェクト配置モデルを使用した場合</span><span class="sxs-lookup"><span data-stu-id="47302-110">When Using the Project Deployment Model</span></span>|<span data-ttu-id="47302-111">パッケージ配置モデルを使用した場合</span><span class="sxs-lookup"><span data-stu-id="47302-111">When Using the Package Deployment Model</span></span>|  
|---------------------------------------------|---------------------------------------------|  
|<span data-ttu-id="47302-112">配置の単位はプロジェクトです。</span><span class="sxs-lookup"><span data-stu-id="47302-112">A project is the unit of deployment.</span></span>|<span data-ttu-id="47302-113">パッケージは配置の 1 単位です。</span><span class="sxs-lookup"><span data-stu-id="47302-113">A package is the unit of deployment.</span></span>|  
|<span data-ttu-id="47302-114">パラメーターを使用して、値をパッケージ プロパティに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="47302-114">Parameters are used to assign values to package properties.</span></span>|<span data-ttu-id="47302-115">構成を使用して、値をパッケージ プロパティに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="47302-115">Configurations are used to assign values to package properties.</span></span>|  
|<span data-ttu-id="47302-116">プロジェクト (パッケージとパラメーターを含む) はプロジェクト配置ファイル (.ispac 拡張子) にビルドされます。</span><span class="sxs-lookup"><span data-stu-id="47302-116">A project, containing packages and parameters, is built to a project deployment file (.ispac extension).</span></span>|<span data-ttu-id="47302-117">パッケージ (.dtsx 拡張子) と構成 (.dtsConfig 拡張子) は、個別にファイル システムに保存されます。</span><span class="sxs-lookup"><span data-stu-id="47302-117">Packages (.dtsx extension) and configurations (.dtsConfig extension) are saved individually to the file system.</span></span>|  
|<span data-ttu-id="47302-118">パッケージとパラメーターを含むプロジェクトは、SQL Server のインスタンス上の SSISDB カタログに配置されます。</span><span class="sxs-lookup"><span data-stu-id="47302-118">A project, containing packages and parameters, is deployed to the SSISDB catalog on an instance of SQL Server.</span></span>|<span data-ttu-id="47302-119">パッケージと構成は、別のコンピューター上のファイル システムにコピーされます。</span><span class="sxs-lookup"><span data-stu-id="47302-119">Packages and configurations are copied to the file system on another computer.</span></span> <span data-ttu-id="47302-120">パッケージは、SQL Server のインスタンス上の MSDB データベースに保存することもできます。</span><span class="sxs-lookup"><span data-stu-id="47302-120">Packages can also be saved to the MSDB database on an instance of SQL Server.</span></span>|  
|<span data-ttu-id="47302-121">データベース エンジンでは CLR 統合が必要です。</span><span class="sxs-lookup"><span data-stu-id="47302-121">CLR integration is required on the database engine.</span></span>|<span data-ttu-id="47302-122">データベース エンジンでは CLR 統合は不要です。</span><span class="sxs-lookup"><span data-stu-id="47302-122">CLR integration is not required on the database engine.</span></span>|  
|<span data-ttu-id="47302-123">環境固有のパラメーター値は、環境変数に格納されます。</span><span class="sxs-lookup"><span data-stu-id="47302-123">Environment-specific parameter values are stored in environment variables.</span></span>|<span data-ttu-id="47302-124">環境固有の構成値は、構成ファイルに格納されます。</span><span class="sxs-lookup"><span data-stu-id="47302-124">Environment-specific configuration values are stored in configuration files.</span></span>|  
|<span data-ttu-id="47302-125">カタログ内のプロジェクトとパッケージは、実行前にサーバー上で検証できます。</span><span class="sxs-lookup"><span data-stu-id="47302-125">Projects and packages in the catalog can be validated on the server before execution.</span></span> <span data-ttu-id="47302-126">SQL Server Management Studio、ストアド プロシージャ、またはマネージド コードを使用して検証を実行できます。</span><span class="sxs-lookup"><span data-stu-id="47302-126">You can use SQL Server Management Studio, stored procedures, or managed code to perform the validation.</span></span>|<span data-ttu-id="47302-127">パッケージは実行の直前に検証されます。</span><span class="sxs-lookup"><span data-stu-id="47302-127">Packages are validated just before execution.</span></span> <span data-ttu-id="47302-128">dtExec またはマネージド コードを使用してパッケージを検証することもできます。</span><span class="sxs-lookup"><span data-stu-id="47302-128">You can also validate a package with dtExec or managed code.</span></span>|  
|<span data-ttu-id="47302-129">パッケージは、データベース エンジンで実行を開始することで実行されます。</span><span class="sxs-lookup"><span data-stu-id="47302-129">Packages are executed by starting an execution on the database engine.</span></span> <span data-ttu-id="47302-130">プロジェクト識別子、明示的なパラメーター値 (オプション)、および環境参照 (オプション) は、開始前に実行に割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="47302-130">A project identifier, explicit parameter values (optional), and environment references (optional) are assigned to an execution before it is started.</span></span><br /><br /> <span data-ttu-id="47302-131">`dtExec` を使用してパッケージを実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="47302-131">You can also execute packages using `dtExec`.</span></span>|<span data-ttu-id="47302-132">パッケージは、`dtExec` および `DTExecUI` 実行ユーティリティを使用して実行されます。</span><span class="sxs-lookup"><span data-stu-id="47302-132">Packages are executed using the `dtExec` and `DTExecUI` execution utilities.</span></span> <span data-ttu-id="47302-133">適切な構成が、コマンド プロンプトの引数で指定されます (オプション)。</span><span class="sxs-lookup"><span data-stu-id="47302-133">Applicable configurations are identified by command-prompt arguments (optional).</span></span>|  
|<span data-ttu-id="47302-134">実行時に、パッケージによって生成されたイベントが自動的にキャプチャされ、カタログに保存されます。</span><span class="sxs-lookup"><span data-stu-id="47302-134">During execution, events that are produced by the package are captured automatically and saved to the catalog.</span></span> <span data-ttu-id="47302-135">Transact-SQL ビューを使用して、これらのイベントに対してクエリを実行できます。</span><span class="sxs-lookup"><span data-stu-id="47302-135">You can query these events with Transact-SQL views.</span></span>|<span data-ttu-id="47302-136">実行時に、パッケージによって生成されたイベントは自動的にキャプチャされません。</span><span class="sxs-lookup"><span data-stu-id="47302-136">During execution, events that are produced by a package are not captured automatically.</span></span> <span data-ttu-id="47302-137">イベントをキャプチャするには、パッケージにログ プロバイダーを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="47302-137">A log provider must be added to the package to capture events.</span></span>|  
|<span data-ttu-id="47302-138">パッケージは、個別の Windows プロセスで実行されます。</span><span class="sxs-lookup"><span data-stu-id="47302-138">Packages are run in a separate Windows process.</span></span>|<span data-ttu-id="47302-139">パッケージは、個別の Windows プロセスで実行されます。</span><span class="sxs-lookup"><span data-stu-id="47302-139">Packages are run in a separate Windows process.</span></span>|  
|<span data-ttu-id="47302-140">SQL Server エージェントを使用してパッケージ実行がスケジュールされます。</span><span class="sxs-lookup"><span data-stu-id="47302-140">SQL Server Agent is used to schedule package execution.</span></span>|<span data-ttu-id="47302-141">SQL Server エージェントを使用してパッケージ実行がスケジュールされます。</span><span class="sxs-lookup"><span data-stu-id="47302-141">SQL Server Agent is used to schedule package execution.</span></span>|  
  
## <a name="features-of-project-deployment-model"></a><span data-ttu-id="47302-142">プロジェクト配置モデルの機能</span><span class="sxs-lookup"><span data-stu-id="47302-142">Features of Project Deployment Model</span></span>  
 <span data-ttu-id="47302-143">次の表に、プロジェクト配置モデル専用に開発されたプロジェクトで使用できる機能を示します。</span><span class="sxs-lookup"><span data-stu-id="47302-143">The following table lists the features that are available to projects developed only for the project deployment model.</span></span>  
  
|<span data-ttu-id="47302-144">特徴量</span><span class="sxs-lookup"><span data-stu-id="47302-144">Feature</span></span>|<span data-ttu-id="47302-145">説明</span><span class="sxs-lookup"><span data-stu-id="47302-145">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="47302-146">パラメーター</span><span class="sxs-lookup"><span data-stu-id="47302-146">Parameters</span></span>|<span data-ttu-id="47302-147">パラメーターは、パッケージで使用されるデータを指定します。</span><span class="sxs-lookup"><span data-stu-id="47302-147">A parameter specifies the data that will be used by a package.</span></span> <span data-ttu-id="47302-148">パラメーターは、パッケージ パラメーターとプロジェクト パラメーターを使用して、パッケージ レベルとプロジェクト レベルそれぞれにスコープを設定できます。</span><span class="sxs-lookup"><span data-stu-id="47302-148">You can scope parameters to the package level or project level with package parameters and project parameters, respectively.</span></span> <span data-ttu-id="47302-149">パラメーターは、式またはタスクで使用できます。</span><span class="sxs-lookup"><span data-stu-id="47302-149">Parameters can be used in expressions or tasks.</span></span> <span data-ttu-id="47302-150">プロジェクトをカタログに配置すると、パラメーターごとにリテラル値を割り当てることも、設計時に割り当てられた既定値を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="47302-150">When the project is deployed to the catalog, you can assign a literal value for each parameter or use the default value that was assigned at design time.</span></span> <span data-ttu-id="47302-151">リテラル値の代わりに、環境変数を参照することもできます。</span><span class="sxs-lookup"><span data-stu-id="47302-151">In place of a literal value, you can also reference an environment variable.</span></span> <span data-ttu-id="47302-152">環境変数値は、パッケージ実行時に解決されます。</span><span class="sxs-lookup"><span data-stu-id="47302-152">Environment variable values are resolved at the time of package execution.</span></span>|  
|<span data-ttu-id="47302-153">環境</span><span class="sxs-lookup"><span data-stu-id="47302-153">Environments</span></span>|<span data-ttu-id="47302-154">環境とは、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] プロジェクトが参照できる変数のコンテナーです。</span><span class="sxs-lookup"><span data-stu-id="47302-154">An environment is a container of variables that can be referenced by [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] projects.</span></span> <span data-ttu-id="47302-155">各プロジェクトには複数の環境参照を含めることができますが、1 回のパッケージ実行で参照できるのは、1 つの環境の変数のみです。</span><span class="sxs-lookup"><span data-stu-id="47302-155">Each project can have multiple environment references, but a single instance of package execution can only reference variables from a single environment.</span></span> <span data-ttu-id="47302-156">環境を使用すると、パッケージに割り当てる値をまとめることができます。</span><span class="sxs-lookup"><span data-stu-id="47302-156">Environments allow you to organize the values that you assign to a package.</span></span> <span data-ttu-id="47302-157">たとえば、"Dev"、"test"、"Production" という名前の環境を使用できます。</span><span class="sxs-lookup"><span data-stu-id="47302-157">For example, you might have environments named "Dev", "test", and "Production".</span></span>|  
|<span data-ttu-id="47302-158">環境変数</span><span class="sxs-lookup"><span data-stu-id="47302-158">Environment variables</span></span>|<span data-ttu-id="47302-159">環境変数は、パッケージの実行時にパラメーターに割り当てることができるリテラル値を定義します。</span><span class="sxs-lookup"><span data-stu-id="47302-159">An environment variable defines a literal value that can be assigned to a parameter during package execution.</span></span> <span data-ttu-id="47302-160">環境変数を使用するには、(パラメーターを持つ環境に対応するプロジェクト内に) 環境参照を作成し、環境変数の名前にパラメーター値を割り当て、個々の実行を構成するときに対応する環境参照を指定します。</span><span class="sxs-lookup"><span data-stu-id="47302-160">To use an environment variable, create an environment reference (in the project that corresponds to the environment having the parameter), assign a parameter value to the name of the environment variable, and specify the corresponding environment reference when you configure an instance of execution.</span></span>|  
|<span data-ttu-id="47302-161">SSISDB カタログ</span><span class="sxs-lookup"><span data-stu-id="47302-161">SSISDB catalog</span></span>|<span data-ttu-id="47302-162">すべての [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] オブジェクトは、SQL Server のインスタンス上で、SSISDB カタログと呼ばれるデータベースに格納され、管理されます。</span><span class="sxs-lookup"><span data-stu-id="47302-162">All [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] objects are stored and managed on an instance of SQL Server in a database referred to as the SSISDB catalog.</span></span> <span data-ttu-id="47302-163">カタログでは、フォルダーを使用してプロジェクトや環境を整理することができます。</span><span class="sxs-lookup"><span data-stu-id="47302-163">The catalog allows you to use folders to organize your projects and environments.</span></span> <span data-ttu-id="47302-164">SQL Server の各インスタンスに 1 つのカタログを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="47302-164">Each instance of SQL Server can have one catalog.</span></span> <span data-ttu-id="47302-165">各カタログには 0 個以上のフォルダーを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="47302-165">Each catalog can have zero or more folders.</span></span> <span data-ttu-id="47302-166">各フォルダーには、0 個以上のプロジェクトと 0 個以上の環境を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="47302-166">Each folder can have zero or more projects and zero or more environments.</span></span> <span data-ttu-id="47302-167">カタログ内のフォルダーは、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] オブジェクトに対する権限の境界として使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="47302-167">A folder in the catalog can also be used as a boundary for permissions to [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] objects.</span></span>|  
|<span data-ttu-id="47302-168">カタログのストアド プロシージャとビュー</span><span class="sxs-lookup"><span data-stu-id="47302-168">Catalog stored procedures and views</span></span>|<span data-ttu-id="47302-169">カタログ内の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] オブジェクトは、多数のストアド プロシージャとビューを使用して管理できます。</span><span class="sxs-lookup"><span data-stu-id="47302-169">A large number of stored procedures and views can be used to manage [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] objects in the catalog.</span></span> <span data-ttu-id="47302-170">たとえば、パラメーターおよび環境変数の値を指定し、実行を作成および開始して、カタログ操作を監視できます。</span><span class="sxs-lookup"><span data-stu-id="47302-170">For example, you can specify values to parameters and environment variables, create and start executions, and monitor catalog operations.</span></span> <span data-ttu-id="47302-171">実行が開始される前にパッケージで使用される値を確認することもできます。</span><span class="sxs-lookup"><span data-stu-id="47302-171">You can even see exactly which values will be used by a package before execution starts.</span></span>|  
  
## <a name="project-deployment"></a><span data-ttu-id="47302-172">プロジェクト配置</span><span class="sxs-lookup"><span data-stu-id="47302-172">Project Deployment</span></span>  
 <span data-ttu-id="47302-173">プロジェクト配置モデルの中心にあるのは、プロジェクト配置ファイル (.ispac 拡張子) です。</span><span class="sxs-lookup"><span data-stu-id="47302-173">At the center of the project deployment model is the project deployment file (.ispac extension).</span></span> <span data-ttu-id="47302-174">プロジェクト配置ファイルは、プロジェクト内のパッケージおよびパラメーターに関する重要な情報のみを含む、自己完結型の配置単位です。</span><span class="sxs-lookup"><span data-stu-id="47302-174">The project deployment file is a self-contained unit of deployment that includes only the essential information about the packages and parameters in the project.</span></span> <span data-ttu-id="47302-175">プロジェクト配置ファイルは、Integration Services プロジェクト ファイル (.dtproj 拡張子) に含まれるすべての情報を取得するわけではありません。</span><span class="sxs-lookup"><span data-stu-id="47302-175">The project deployment file does not capture all of the information contained in the Integration Services project file (.dtproj extension).</span></span> <span data-ttu-id="47302-176">たとえば、メモの作成に使用する追加のテキスト ファイルは、プロジェクト配置ファイルには保存されないため、カタログには配置されません。</span><span class="sxs-lookup"><span data-stu-id="47302-176">For example, additional text files that you use for writing notes are not stored in the project deployment file and thus are not deployed to the catalog.</span></span>  
  
## <a name="required-tasks"></a><span data-ttu-id="47302-177">必須のタスク</span><span class="sxs-lookup"><span data-stu-id="47302-177">Required Tasks</span></span>  
  
-   [<span data-ttu-id="47302-178">Integration Services サーバーへのプロジェクトの配置</span><span class="sxs-lookup"><span data-stu-id="47302-178">Deploy Projects to Integration Services Server</span></span>](../deploy-projects-to-integration-services-server.md)  
  
## <a name="related-content"></a><span data-ttu-id="47302-179">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="47302-179">Related Content</span></span>  
 <span data-ttu-id="47302-180">mattmasson.com のブログ「 [SSIS プロジェクトの分岐方法について](https://go.microsoft.com/fwlink/?LinkId=245739)」</span><span class="sxs-lookup"><span data-stu-id="47302-180">Blog entry, [Thoughts on Branching Strategies for SSIS Projects](https://go.microsoft.com/fwlink/?LinkId=245739), on mattmasson.com.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47302-181">参照</span><span class="sxs-lookup"><span data-stu-id="47302-181">See Also</span></span>  
 [<span data-ttu-id="47302-182">dtexec ユーティリティ</span><span class="sxs-lookup"><span data-stu-id="47302-182">dtexec Utility</span></span>](dtexec-utility.md)  
  
  