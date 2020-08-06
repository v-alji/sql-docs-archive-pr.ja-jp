---
title: ストアドプロシージャを使用した SSIS パッケージの配置と実行 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 60914b0c-1f65-45f8-8132-0ca331749fcc
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1570207dca6e944b54c553a1d83256d8f4fa3244
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740165"
---
# <a name="deploy-and-execute-ssis-packages-using-stored-procedures"></a><span data-ttu-id="dc6c3-102">ストアド プロシージャを使用した SSIS パッケージの配置と実行</span><span class="sxs-lookup"><span data-stu-id="dc6c3-102">Deploy and Execute SSIS Packages using Stored Procedures</span></span>
  <span data-ttu-id="dc6c3-103">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを、プロジェクト配置モデルを使用するように構成すると、 [!INCLUDE[ssIS](../includes/ssis-md.md)] カタログのストアド プロシージャを使用して、プロジェクトの配置とパッケージの実行を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="dc6c3-103">When you configure an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project to use the project deployment model, you can use stored procedures in the [!INCLUDE[ssIS](../includes/ssis-md.md)] catalog to deploy the project and execute the packages.</span></span> <span data-ttu-id="dc6c3-104">プロジェクト配置モデルの詳細については、「 [プロジェクトとパッケージの展開](packages/deploy-integration-services-ssis-projects-and-packages.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dc6c3-104">For information about the project deployment model, see [Deployment of Projects and Packages](packages/deploy-integration-services-ssis-projects-and-packages.md).</span></span>  
  
 <span data-ttu-id="dc6c3-105">また、 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] または [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] を使用して、プロジェクトの配置とパッケージの実行を行うこともできます。</span><span class="sxs-lookup"><span data-stu-id="dc6c3-105">You can also use [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] or [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to deploy the project and execute the packages.</span></span> <span data-ttu-id="dc6c3-106">詳細については、「 **関連項目** 」セクションのトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="dc6c3-106">For more information, see the topics in the **See Also** section.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="dc6c3-107">次の手順を実行することにより、catalog.deploy_project を除き、次の手順に示されるストアド プロシージャの Transact-SQL ステートメントを簡単に生成できます。</span><span class="sxs-lookup"><span data-stu-id="dc6c3-107">You can easily generate the Transact-SQL statements for the stored procedures listed in the procedure below, with the exception of catalog.deploy_project, by doing the following:</span></span>  
> 
>  1.  <span data-ttu-id="dc6c3-108">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]で、オブジェクト エクスプローラーの **[Integration Services カタログ]** ノードを展開し、実行するパッケージに移動します。</span><span class="sxs-lookup"><span data-stu-id="dc6c3-108">In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], expand the **Integration Services Catalogs** node in Object Explorer and navigate to the package you want to execute.</span></span>  
> 2.  <span data-ttu-id="dc6c3-109">パッケージを右クリックし、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dc6c3-109">Right-click the package, and then click **Execute**.</span></span>  
> 3.  <span data-ttu-id="dc6c3-110">必要に応じて、パラメーター値、接続マネージャー プロパティ、 **[詳細設定]** タブのオプション (ログ記録レベルなど) を設定します。</span><span class="sxs-lookup"><span data-stu-id="dc6c3-110">As needed, set parameters values, connection manager properties, and options in the **Advanced** tab such as the logging level.</span></span>  
> 
>      <span data-ttu-id="dc6c3-111">詳細については、「 [SSIS サーバーでのパッケージ実行のログ記録を有効にする](../../2014/integration-services/enable-logging-for-package-execution-on-the-ssis-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dc6c3-111">For more information about logging levels, see [Enable Logging for Package Execution on the SSIS Server](../../2014/integration-services/enable-logging-for-package-execution-on-the-ssis-server.md).</span></span>  
> 4.  <span data-ttu-id="dc6c3-112">**[OK]** をクリックしてパッケージを実行する前に、 **[スクリプト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dc6c3-112">Before clicking **OK** to execute the package, click **Script**.</span></span> <span data-ttu-id="dc6c3-113">Transact-SQL が [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]のクエリ エディター ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="dc6c3-113">The Transact-SQL appears in a Query Editor window in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
## <a name="to-deploy-and-execute-a-package-using-stored-procedures"></a><span data-ttu-id="dc6c3-114">ストアド プロシージャを使用してパッケージの配置と実行を行うには</span><span class="sxs-lookup"><span data-stu-id="dc6c3-114">To deploy and execute a package using stored procedures</span></span>  
  
1.  <span data-ttu-id="dc6c3-115">[catalog.deploy_project (SSISDB データベース)](/sql/integration-services/system-stored-procedures/catalog-deploy-project-ssisdb-database) を呼び出して、パッケージを含む [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サーバーに配置します。</span><span class="sxs-lookup"><span data-stu-id="dc6c3-115">Call [catalog.deploy_project &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-deploy-project-ssisdb-database) to deploy the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server.</span></span>  
  
     <span data-ttu-id="dc6c3-116">プロジェクト配置ファイルのバイナリコンテンツを取得するには [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 、 \* \@ project_stream\*パラメーターとして、OPENROWSET 関数と一括行セットプロバイダーで SELECT ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="dc6c3-116">To retrieve the binary contents of the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project deployment file, for the *\@project_stream* parameter, use a SELECT statement with the OPENROWSET function and the BULK rowset provider.</span></span> <span data-ttu-id="dc6c3-117">BULK 行セット プロバイダーを使用すると、ファイルからデータを読み取ることができます。</span><span class="sxs-lookup"><span data-stu-id="dc6c3-117">The BULK rowset provider enables you to read data from a file.</span></span> <span data-ttu-id="dc6c3-118">BULK 行セット プロバイダーの SINGLE_BLOB 引数は、データ ファイルの内容を、varbinary(max) 型の単一行、単一列の行セットとして返します。</span><span class="sxs-lookup"><span data-stu-id="dc6c3-118">The SINGLE_BLOB argument for the BULK rowset provider returns the contents of the data file as a single-row, single-column rowset of type varbinary(max).</span></span> <span data-ttu-id="dc6c3-119">詳細については、「[OPENROWSET (Transact-SQL)](/sql/t-sql/functions/openrowset-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dc6c3-119">For more information, see [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql).</span></span>  
  
     <span data-ttu-id="dc6c3-120">次の例では、SSISPackages_ProjectDeployment プロジェクトを、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サーバーの SSIS パッケージ フォルダーに配置します。</span><span class="sxs-lookup"><span data-stu-id="dc6c3-120">In the following example, the SSISPackages_ProjectDeployment project is deployed to the SSIS Packages folder on the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server.</span></span> <span data-ttu-id="dc6c3-121">バイナリデータは、プロジェクトファイル (SSISPackage_ProjectDeployment ispac) から読み取られ、varbinary (max) 型の\* \@ projectbinary\*パラメーターに格納されます。</span><span class="sxs-lookup"><span data-stu-id="dc6c3-121">The binary data is read from the project file (SSISPackage_ProjectDeployment.ispac) and is stored in the *\@ProjectBinary* parameter of type varbinary(max).</span></span> <span data-ttu-id="dc6c3-122">\* \@ Projectbinary*パラメーター値は* \@ project_stream\*パラメーターに割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="dc6c3-122">The *\@ProjectBinary* parameter value is assigned to the *\@project_stream* parameter.</span></span>  
  
    ```  
    DECLARE @ProjectBinary as varbinary(max)  
    DECLARE @operation_id as bigint  
    Set @ProjectBinary = (SELECT * FROM OPENROWSET(BULK 'C:\MyProjects\ SSISPackage_ProjectDeployment.ispac', SINGLE_BLOB) as BinaryData)  
  
    Exec catalog.deploy_project @folder_name = 'SSIS Packages', @project_name = 'DeployViaStoredProc_SSIS', @Project_Stream = @ProjectBinary, @operation_id = @operation_id out  
  
    ```  
  
2.  <span data-ttu-id="dc6c3-123">[catalog.create_execution (SSISDB データベース)](/sql/integration-services/system-stored-procedures/catalog-create-execution-ssisdb-database) を呼び出してパッケージ実行のインスタンスを作成し、必要に応じて、[catalog.set_execution_parameter_value (SSISDB データベース)](/sql/integration-services/system-stored-procedures/catalog-set-execution-parameter-value-ssisdb-database) を呼び出してランタイム パラメーター値を設定します。</span><span class="sxs-lookup"><span data-stu-id="dc6c3-123">Call [catalog.create_execution &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-create-execution-ssisdb-database) to create an instance of the package execution, and optionally call [catalog.set_execution_parameter_value &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-set-execution-parameter-value-ssisdb-database) to set runtime parameter values.</span></span>  
  
     <span data-ttu-id="dc6c3-124">次の例では、catalog.create_execution は、SSISPackage_ProjectDeployment プロジェクトに含まれる package.dtsx の実行のインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="dc6c3-124">In the following example, catalog.create_execution creates an instance of execution for package.dtsx that is contained in the SSISPackage_ProjectDeployment project.</span></span> <span data-ttu-id="dc6c3-125">このプロジェクトは SSIS パッケージ フォルダーに配置されます。</span><span class="sxs-lookup"><span data-stu-id="dc6c3-125">The project is located in the SSIS Packages folder.</span></span> <span data-ttu-id="dc6c3-126">ストアド プロシージャから返される execution_id は、catalog.set_execution_parameter_value の呼び出しに使用されます。</span><span class="sxs-lookup"><span data-stu-id="dc6c3-126">The execution_id returned by the stored procedure is used in the call to catalog.set_execution_parameter_value.</span></span> <span data-ttu-id="dc6c3-127">この 2 番目のストアド プロシージャは、LOGGING_LEVEL パラメーターを 3 (詳細ログ) に、Parameter1 という名前のパッケージ パラメーターを 1 に設定します。</span><span class="sxs-lookup"><span data-stu-id="dc6c3-127">This second stored procedure sets the LOGGING_LEVEL parameter to 3 (verbose logging) and sets a package parameter named Parameter1 to a value of 1.</span></span>  
  
     <span data-ttu-id="dc6c3-128">LOGGING_LEVEL などのパラメーターの場合、object_type 値は 50 です。</span><span class="sxs-lookup"><span data-stu-id="dc6c3-128">For parameters such as LOGGING_LEVEL the object_type value is 50.</span></span> <span data-ttu-id="dc6c3-129">パッケージ パラメーターの場合、object_type 値は 30 になります。</span><span class="sxs-lookup"><span data-stu-id="dc6c3-129">For package parameters the object_type value is 30.</span></span>  
  
    ```  
    Declare @execution_id bigint  
    EXEC [SSISDB].[catalog].[create_execution] @package_name=N'Package.dtsx', @execution_id=@execution_id OUTPUT, @folder_name=N'SSIS Packages', @project_name=N'SSISPackage_ProjectDeployment', @use32bitruntime=False, @reference_id=1  
  
    Select @execution_id  
    DECLARE @var0 smallint = 3  
    EXEC [SSISDB].[catalog].[set_execution_parameter_value] @execution_id,  @object_type=50, @parameter_name=N'LOGGING_LEVEL', @parameter_value=@var0  
  
    DECLARE @var1 int = 1  
    EXEC [SSISDB].[catalog].[set_execution_parameter_value] @execution_id,  @object_type=30, @parameter_name=N'Parameter1', @parameter_value=@var1  
  
    GO  
  
    ```  
  
3.  <span data-ttu-id="dc6c3-130">[catalog.start_execution (SSISDB データベース)](/sql/integration-services/system-stored-procedures/catalog-start-execution-ssisdb-database) を呼び出してパッケージを実行します。</span><span class="sxs-lookup"><span data-stu-id="dc6c3-130">Call [catalog.start_execution &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-start-execution-ssisdb-database) to execute the package.</span></span>  
  
     <span data-ttu-id="dc6c3-131">次の例では、catalog.start_execution の呼び出しを Transact-SQL に追加して、パッケージの実行を開始します。</span><span class="sxs-lookup"><span data-stu-id="dc6c3-131">In the following example, a call to catalog.start_execution is added to the Transact-SQL to start the package execution.</span></span> <span data-ttu-id="dc6c3-132">catalog.create_execution ストアド プロシージャによって返される execution_id が使用されます。</span><span class="sxs-lookup"><span data-stu-id="dc6c3-132">The execution_id returned by the catalog.create_execution stored procedure is used.</span></span>  
  
    ```  
    Declare @execution_id bigint  
    EXEC [SSISDB].[catalog].[create_execution] @package_name=N'Package.dtsx', @execution_id=@execution_id OUTPUT, @folder_name=N'SSIS Packages', @project_name=N'SSISPackage_ProjectDeployment', @use32bitruntime=False, @reference_id=1  
  
    Select @execution_id  
    DECLARE @var0 smallint = 3  
    EXEC [SSISDB].[catalog].[set_execution_parameter_value] @execution_id,  @object_type=50, @parameter_name=N'LOGGING_LEVEL', @parameter_value=@var0  
  
    DECLARE @var1 int = 1  
    EXEC [SSISDB].[catalog].[set_execution_parameter_value] @execution_id,  @object_type=30, @parameter_name=N'Parameter1', @parameter_value=@var1  
  
    EXEC [SSISDB].[catalog].[start_execution] @execution_id  
    GO  
  
    ```  
  
## <a name="to-deploy-a-project-from-server-to-server-using-stored-procedures"></a><span data-ttu-id="dc6c3-133">ストアド プロシージャを使用してサーバー間でプロジェクトを配置するには</span><span class="sxs-lookup"><span data-stu-id="dc6c3-133">To deploy a project from server to server using stored procedures</span></span>  
 <span data-ttu-id="dc6c3-134">[catalog.get_project (SSISDB データベース)](/sql/integration-services/system-stored-procedures/catalog-get-project-ssisdb-database) と [catalog.deploy_project (SSISDB データベース)](/sql/integration-services/system-stored-procedures/catalog-deploy-project-ssisdb-database) ストアド プロシージャを使用して、サーバー間でプロジェクトを配置できます。</span><span class="sxs-lookup"><span data-stu-id="dc6c3-134">You can deploy a project from server to server by using the [catalog.get_project &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-get-project-ssisdb-database) and [catalog.deploy_project &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-deploy-project-ssisdb-database) stored procedures.</span></span>  
  
 <span data-ttu-id="dc6c3-135">ストアド プロシージャを実行する前に次の操作を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="dc6c3-135">You need to do the following before running the stored procedures.</span></span>  
  
-   <span data-ttu-id="dc6c3-136">リンク サーバー オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="dc6c3-136">Create a linked server object.</span></span> <span data-ttu-id="dc6c3-137">詳細については、「[リンク サーバーの作成 (SQL Server データベース エンジン)](../database-engine/sql-server-database-engine-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dc6c3-137">For more information, see [Create Linked Servers &#40;SQL Server Database Engine&#41;](../database-engine/sql-server-database-engine-overview.md).</span></span>  
  
     <span data-ttu-id="dc6c3-138">**[リンク サーバーのプロパティ]** ダイアログ ボックスの **[サーバー オプション]** ページで、 **[RPC]** および **[RPC 出力]** を **[True]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="dc6c3-138">On the **Server Options** page of the **Linked Server Properties** dialog box, set **RPC** and **RPC Out** to **True**.</span></span> <span data-ttu-id="dc6c3-139">そして、 **[分散トランザクションのプロモーションを RPC に対して有効化]** を **[False]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="dc6c3-139">Also, set **Enable Promotion of Distributed Transactions for RPC** to **False**.</span></span>  
  
-   <span data-ttu-id="dc6c3-140">オブジェクト エクスプローラーの **[リンク サーバー]** にある **[プロバイダー]** ノードを展開し、プロバイダーを右クリックして **[プロパティ]** をクリックすることで、リンク サーバーに対して選択したプロバイダーの動的パラメーターを有効にします。</span><span class="sxs-lookup"><span data-stu-id="dc6c3-140">Enable dynamic parameters for the provider you selected for the linked server, by expanding the **Providers** node under **Linked Servers** in Object Explorer, right-clicking the provider, and then clicking **Properties**.</span></span> <span data-ttu-id="dc6c3-141">**[動的パラメーター]** の横にある **[有効化]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="dc6c3-141">Select **Enable** next to **Dynamic parameter.**</span></span>  
  
-   <span data-ttu-id="dc6c3-142">分散トランザクション コーディネーター (DTC) が両方のサーバーで起動していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="dc6c3-142">Confirm that the Distributed Transaction Coordinator (DTC) is started on both servers.</span></span>  
  
 <span data-ttu-id="dc6c3-143">プロジェクトのバイナリを返す catalog.get_project を呼び出したら、catalog.deploy_project を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="dc6c3-143">Call catalog.get_project to return the binary for the project, and then call catalog.deploy_project.</span></span> <span data-ttu-id="dc6c3-144">catalog.get_project によって返される値は、varbinary(max) 型のテーブル変数に挿入されます。</span><span class="sxs-lookup"><span data-stu-id="dc6c3-144">The value returned by catalog.get_project is inserted into a table variable of type varbinary(max).</span></span> <span data-ttu-id="dc6c3-145">リンク サーバーは varbinary(max) 型の結果を返すことができません。</span><span class="sxs-lookup"><span data-stu-id="dc6c3-145">The linked server can't return results that are varbinary(max).</span></span>  
  
 <span data-ttu-id="dc6c3-146">次の例では、catalog.get_project は、リンク サーバーで SSISPackages プロジェクトのバイナリを返します。</span><span class="sxs-lookup"><span data-stu-id="dc6c3-146">In the following example, catalog.get_project returns a binary for the SSISPackages project on the linked server.</span></span> <span data-ttu-id="dc6c3-147">catalog.deploy_project は、ローカル サーバーの DestFolder という名前のフォルダーにプロジェクトを配置します。</span><span class="sxs-lookup"><span data-stu-id="dc6c3-147">The catalog.deploy_project deploys the project to the local server, to the folder named DestFolder.</span></span>  
  
```  
declare @resultsTableVar table (  
project_binary varbinary(max)  
)  
  
INSERT @resultsTableVar (project_binary)  
EXECUTE [MyLinkedServer].[SSISDB].[catalog].[get_project] 'Packages', 'SSISPackages'  
  
declare @project_binary varbinary(max)  
select @project_binary = project_binary from @resultsTableVar  
  
exec [SSISDB].[CATALOG].[deploy_project] 'DestFolder', 'SSISPackages', @project_binary  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="dc6c3-148">参照</span><span class="sxs-lookup"><span data-stu-id="dc6c3-148">See Also</span></span>  
 <span data-ttu-id="dc6c3-149">[Integration Services サーバーへのプロジェクトの配置](../../2014/integration-services/deploy-projects-to-integration-services-server.md) </span><span class="sxs-lookup"><span data-stu-id="dc6c3-149">[Deploy Projects to Integration Services Server](../../2014/integration-services/deploy-projects-to-integration-services-server.md) </span></span>  
 <span data-ttu-id="dc6c3-150">[SQL Server Data Tools でパッケージを実行する](../../2014/integration-services/run-a-package-in-sql-server-data-tools.md) </span><span class="sxs-lookup"><span data-stu-id="dc6c3-150">[Run a Package in SQL Server Data Tools](../../2014/integration-services/run-a-package-in-sql-server-data-tools.md) </span></span>  
 [<span data-ttu-id="dc6c3-151">SQL Server Management Studio を使用した SSIS サーバーでのパッケージの実行</span><span class="sxs-lookup"><span data-stu-id="dc6c3-151">Run a Package on the SSIS Server Using SQL Server Management Studio</span></span>](run-a-package-on-the-ssis-server-using-sql-server-management-studio.md)  
  
  
