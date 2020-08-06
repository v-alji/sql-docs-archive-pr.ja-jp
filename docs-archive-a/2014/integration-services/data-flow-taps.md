---
title: データフローのタップ |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 2d847adf-4b3d-4949-a195-ef43de275077
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 053b34add45354d0df71fa73a72f8786cc706d15
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713357"
---
# <a name="data-flow-taps"></a><span data-ttu-id="3438a-102">データ フロー タップ</span><span class="sxs-lookup"><span data-stu-id="3438a-102">Data Flow Taps</span></span>
  [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] <span data-ttu-id="3438a-103">の新機能を使用して、ランタイム時にパッケージのデータ フロー パスのデータ タップを追加し、データ タップから外部ファイルに出力できます。</span><span class="sxs-lookup"><span data-stu-id="3438a-103">introduces a new feature that allows you to add a data tap on a data flow path of a package at runtime and direct the output from the data tap to an external file.</span></span> <span data-ttu-id="3438a-104">この機能を使用するには、プロジェクト配置モデルを使用して、SSIS サーバーに SSIS プロジェクトを配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3438a-104">To use this feature, you must deploy your SSIS project using the project deployment model to an SSIS Server.</span></span> <span data-ttu-id="3438a-105">サーバーにパッケージを配置した後、そのパッケージを実行する前に、SSISDB データベースに対して T-SQL スクリプトを実行してデータ タップを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3438a-105">After you deploy the package to the server, you need to execute T-SQL scripts against the SSISDB database to add data taps before executing the package.</span></span> <span data-ttu-id="3438a-106">次にシナリオの例を示します。</span><span class="sxs-lookup"><span data-stu-id="3438a-106">Here is a sample scenario:</span></span>  
  
1.  <span data-ttu-id="3438a-107">[catalog.create_execution (SSISDB データベース)](/sql/integration-services/system-stored-procedures/catalog-create-execution-ssisdb-database) ストアド プロシージャを使用してパッケージ実行インスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="3438a-107">Create an execution instance of a package by using the [catalog.create_execution &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-create-execution-ssisdb-database) stored procedure.</span></span>  
  
2.  <span data-ttu-id="3438a-108">[catalog.add_data_tap](/sql/integration-services/system-stored-procedures/catalog-add-data-tap) または [catalog.add_data_tap_by_guid](/sql/integration-services/system-stored-procedures/catalog-add-data-tap-by-guid) ストアド プロシージャを使用してデータ タップを追加します。</span><span class="sxs-lookup"><span data-stu-id="3438a-108">Add a data tap by using either [catalog.add_data_tap](/sql/integration-services/system-stored-procedures/catalog-add-data-tap) or [catalog.add_data_tap_by_guid](/sql/integration-services/system-stored-procedures/catalog-add-data-tap-by-guid) stored procedure.</span></span>  
  
3.  <span data-ttu-id="3438a-109">[catalog.start_execution (SSISDB データベース)](/sql/integration-services/system-stored-procedures/catalog-start-execution-ssisdb-database) を使用してパッケージ実行インスタンスを開始します。</span><span class="sxs-lookup"><span data-stu-id="3438a-109">Start the execution instance of the package by using the [catalog.start_execution &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-start-execution-ssisdb-database).</span></span>  
  
 <span data-ttu-id="3438a-110">前のシナリオで説明されているステップを実行するサンプル SQL スクリプトを次に示します:</span><span class="sxs-lookup"><span data-stu-id="3438a-110">Here is a sample SQL script that performs the steps described in the above scenario:</span></span>  
  
```  
  
Declare @execid bigint  
EXEC [SSISDB].[catalog].[create_execution] @folder_name=N'ETL Folder', @project_name=N'ETL Project', @package_name=N'Package.dtsx', @execution_id=@execid OUTPUT  
EXEC [SSISDB].[catalog].add_data_tap @execution_id = @execid, @task_package_path = '\Package\Data Flow Task', @dataflow_path_id_string = 'Paths[Flat File Source.Flat File Source Output]', @data_filename = 'output.txt'  
EXEC [SSISDB].[catalog].[start_execution] @execid  
  
```  
  
 <span data-ttu-id="3438a-111">create_execution ストアド プロシージャのフォルダー名、プロジェクト名、およびパッケージ名パラメーターは、Integration Services カタログのフォルダー、プロジェクト、およびパッケージ名に対応しています。</span><span class="sxs-lookup"><span data-stu-id="3438a-111">The folder name, project name, and package name parameters of the create_execution stored procedure correspond to the folder, project, and package names in the Integration Services catalog.</span></span> <span data-ttu-id="3438a-112">次のイメージに示すように、create_execution 呼び出しで使用するフォルダー、プロジェクト、およびパッケージ名を SQL Server Management Studio から取得できます。</span><span class="sxs-lookup"><span data-stu-id="3438a-112">You can get the folder, project, and package names to use in the create_execution call from the SQL Server Management Studio as shown in the following image.</span></span> <span data-ttu-id="3438a-113">SSIS プロジェクトがここに表示されない場合は、プロジェクトを SSIS サーバーに配置していない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="3438a-113">If you do not see your SSIS project here, you may not have deployed the project to SSIS server yet.</span></span> <span data-ttu-id="3438a-114">Visual Studio の SSIS プロジェクトを右クリックした後 [配置] をクリックし、適切な SSIS サーバーにプロジェクトを配置します。</span><span class="sxs-lookup"><span data-stu-id="3438a-114">Right-click on SSIS project in Visual Studio and click Deploy to deploy the project to the expected SSIS server.</span></span>  
  
 <span data-ttu-id="3438a-115">SQL ステートメントを入力する代わりに、次のステップを実行し、実行パッケージのスクリプトを生成することができます:</span><span class="sxs-lookup"><span data-stu-id="3438a-115">Instead of typing the SQL statements, you can generate the execute package script by performing the following steps:</span></span>  
  
1.  <span data-ttu-id="3438a-116">**Package.dtsx** を右クリックし、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3438a-116">Right-click **Package.dtsx** and click **Execute**.</span></span>  
  
2.  <span data-ttu-id="3438a-117">**[スクリプト]** ツール バー ボタンをクリックしてスクリプトを生成します。</span><span class="sxs-lookup"><span data-stu-id="3438a-117">Click **Script** toolbar button to generate the script.</span></span>  
  
3.  <span data-ttu-id="3438a-118">ここで、add_data_tap ステートメントを start_execution 呼び出しの前に追加します。</span><span class="sxs-lookup"><span data-stu-id="3438a-118">Now, add the add_data_tap statement before the start_execution call.</span></span>  
  
 <span data-ttu-id="3438a-119">add_data_tap ストアド プロシージャの task_package_path パラメーターは、Visual Studio のデータ フロー タスクの PackagePath プロパティに対応しています。</span><span class="sxs-lookup"><span data-stu-id="3438a-119">The task_package_path parameter of add_data_tap stored procedure corresponds to the PackagePath property of the data flow task in Visual Studio.</span></span> <span data-ttu-id="3438a-120">Visual Studio で **[データ フロー タスク]** を右クリックし、 **[プロパティ]** をクリックして [プロパティ] ウィンドウを起動します。</span><span class="sxs-lookup"><span data-stu-id="3438a-120">In Visual Studio, right-click the **Data Flow Task**, and click **Properties** to launch the Properties window.</span></span>  <span data-ttu-id="3438a-121">add_data_tap ストアド プロシージャ呼び出しの task_package_path パラメーターの値として使用する、 **PackagePath** プロパティの値を確認します。</span><span class="sxs-lookup"><span data-stu-id="3438a-121">Note the value of the **PackagePath** property to use it as a value for the task_package_path parameter for add_data_tap stored procedure call.</span></span>  
  
 <span data-ttu-id="3438a-122">add_data_tap ストアド プロシージャの dataflow_path_id_string パラメーターは、データ タップを追加するデータ フロー パスの IdentificationString プロパティに対応しています。</span><span class="sxs-lookup"><span data-stu-id="3438a-122">The dataflow_path_id_string  parameter of add_data_tap stored procedure corresponds to the IdentificationString property of the data flow path to which you want to add a data tap.</span></span> <span data-ttu-id="3438a-123">dataflow_path_id_string を取得するには、データ フロー パス (データ フローのタスク間の矢印) をクリックし、[プロパティ] ウィンドウで **IdentificationString** プロパティの値を確認します。</span><span class="sxs-lookup"><span data-stu-id="3438a-123">To get the dataflow_path_id_string, click the data flow path (arrow between tasks in the data flow), and note the value of the **IdentificationString** property in the Properties window.</span></span>  
  
 <span data-ttu-id="3438a-124">スクリプトを実行すると、出力ファイルは \<Program Files>\Microsoft SQL Server\110\DTS\DataDumps に格納されます。</span><span class="sxs-lookup"><span data-stu-id="3438a-124">When you execute the script, the output file is stored in \<Program Files>\Microsoft SQL Server\110\DTS\DataDumps.</span></span> <span data-ttu-id="3438a-125">その名前のファイルが既に存在する場合、新しいファイルはサフィックス付きで (例: output[1].txt) 作成されます。</span><span class="sxs-lookup"><span data-stu-id="3438a-125">If a file with the name already exists, a new file with a suffix (for example: output[1].txt)  is created.</span></span>  
  
 <span data-ttu-id="3438a-126">既に説明したように、add_data_tap ストアド プロシージャを使用する代わりに、 [catalog.add_data_tap_by_guid](/sql/integration-services/system-stored-procedures/catalog-add-data-tap-by-guid)ストアド プロシージャを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="3438a-126">As mentioned earlier, you can also use [catalog.add_data_tap_by_guid](/sql/integration-services/system-stored-procedures/catalog-add-data-tap-by-guid)stored procedure instead of using add_data_tap stored procedure.</span></span> <span data-ttu-id="3438a-127">このストアド プロシージャは、task_package_path の代わりにデータ フロー タスクの ID をパラメーターとして取得します。</span><span class="sxs-lookup"><span data-stu-id="3438a-127">This stored procedure takes the ID of data flow task as a parameter instead of task_package_path.</span></span> <span data-ttu-id="3438a-128">Visual Studio プロパティ ウィンドウからデータ フロー タスクの ID を取得できます。</span><span class="sxs-lookup"><span data-stu-id="3438a-128">You can get the ID of data flow task from the properties window in Visual Studio.</span></span>  
  
## <a name="removing-a-data-tap"></a><span data-ttu-id="3438a-129">データ タップの削除</span><span class="sxs-lookup"><span data-stu-id="3438a-129">Removing a data tap</span></span>  
 <span data-ttu-id="3438a-130">[catalog.remove_data_tap](/sql/integration-services/system-stored-procedures/catalog-remove-data-tap) ストアド プロシージャを使用して、実行開始前にデータ タップを削除できます。</span><span class="sxs-lookup"><span data-stu-id="3438a-130">You can remove a data tap before starting the execution by using the [catalog.remove_data_tap](/sql/integration-services/system-stored-procedures/catalog-remove-data-tap) stored procedure.</span></span> <span data-ttu-id="3438a-131">このストアド プロシージャは、add_data_tap ストアド プロシージャの出力として取得できるデータ タップの ID を、パラメーターとして取得します。</span><span class="sxs-lookup"><span data-stu-id="3438a-131">This stored procedure takes the ID of data tap as a parameter, which you can get as an output of the add_data_tap stored procedure.</span></span>  
  
```  
  
DECLARE @tap_id bigint  
EXEC [SSISDB].[catalog].add_data_tap @execution_id = @execid, @task_package_path = '\Package\Data Flow Task', @dataflow_path_id_string = 'Paths[Flat File Source.Flat File Source Output]', @data_filename = 'output.txt' @data_tap_id=@tap_id OUTPUT  
EXEC [SSISDB].[catalog].remove_data_tap @tap_id  
  
```  
  
## <a name="listing-all-data-taps"></a><span data-ttu-id="3438a-132">すべてのデータ タップを一覧表示する</span><span class="sxs-lookup"><span data-stu-id="3438a-132">Listing all data taps</span></span>  
 <span data-ttu-id="3438a-133">catalog.execution_data_taps ビューを使用して、すべてのデータ タップを一覧することもできます。</span><span class="sxs-lookup"><span data-stu-id="3438a-133">You can also list all the data taps by using the catalog.execution_data_taps view.</span></span> <span data-ttu-id="3438a-134">次の例は、指定の実行インスタンス (ID: 54) のデータ タップを抽出します。</span><span class="sxs-lookup"><span data-stu-id="3438a-134">The following example extracts data taps for a specification execution instance (ID: 54).</span></span>  
  
```  
select * from [SSISDB].[catalog].execution_data_taps where execution_id=@execid  
```  
  
## <a name="performance-consideration"></a><span data-ttu-id="3438a-135">パフォーマンスの注意点</span><span class="sxs-lookup"><span data-stu-id="3438a-135">Performance consideration</span></span>  
 <span data-ttu-id="3438a-136">詳細なログ記録レベルを有効にしてデータ タップを追加すると、データ統合ソリューションが実行する I/O 操作が増大します。</span><span class="sxs-lookup"><span data-stu-id="3438a-136">Enabling verbose logging level and adding data taps increase the I/O operations performed by your data integration solution.</span></span> <span data-ttu-id="3438a-137">そのためデータ タップは、トラブルシューティングの場合に限り追加することをお勧めします</span><span class="sxs-lookup"><span data-stu-id="3438a-137">Hence, we recommend that you add data taps only for troubleshooting purposes</span></span>  
  
## <a name="video"></a><span data-ttu-id="3438a-138">ビデオ</span><span class="sxs-lookup"><span data-stu-id="3438a-138">Video</span></span>  
 <span data-ttu-id="3438a-139">この [TechNet のビデオ](https://technet.microsoft.com/sqlserver/dn600163) は、データ タップを SQL Server 2012 SSISDB カタログに追加、使用する方法を紹介しています。パッケージをプログラム処理によってデバッグし、実行時に結果の一部をキャプチャしています。</span><span class="sxs-lookup"><span data-stu-id="3438a-139">This [video on TechNet](https://technet.microsoft.com/sqlserver/dn600163) demonstrates how to add/use data taps in SQL Server 2012 SSISDB catalog that help with debugging packages programmatically and capturing the partial results at the runtime.</span></span> <span data-ttu-id="3438a-140">また、データ タップの一覧および削除の方法、SSIS パッケージ内でのデータ タップの使用に関するベスト プラクティスについても説明しています。</span><span class="sxs-lookup"><span data-stu-id="3438a-140">It also discusses how to list/ remove these data taps and best practices for using data taps in SSIS packages.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="3438a-141">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="3438a-141">Related Tasks</span></span>  
 [<span data-ttu-id="3438a-142">データ フローのデバッグ</span><span class="sxs-lookup"><span data-stu-id="3438a-142">Debugging Data Flow</span></span>](troubleshooting/debugging-data-flow.md)  
  
 [<span data-ttu-id="3438a-143">パッケージ実行のトラブルシューティング ツール</span><span class="sxs-lookup"><span data-stu-id="3438a-143">Troubleshooting Tools for Package Execution</span></span>](troubleshooting/troubleshooting-tools-for-package-execution.md)  
  
  
