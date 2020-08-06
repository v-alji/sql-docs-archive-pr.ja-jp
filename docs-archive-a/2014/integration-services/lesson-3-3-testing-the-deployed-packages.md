---
title: '手順 3: 配置したパッケージのテスト | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 9159da3f-c9ca-4015-9e85-3bf4373a1349
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d11ae071d97d9fdadec6ee144813c91519b54ea4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640145"
---
# <a name="step-3-testing-the-deployed-packages"></a><span data-ttu-id="1dc0c-102">手順 3:配置したパッケージのテスト</span><span class="sxs-lookup"><span data-stu-id="1dc0c-102">Step 3: Testing the Deployed Packages</span></span>
  <span data-ttu-id="1dc0c-103">このタスクでは、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]のインスタンスに配置したパッケージをテストします。</span><span class="sxs-lookup"><span data-stu-id="1dc0c-103">In this task, you will test the packages that you deployed to an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>

 <span data-ttu-id="1dc0c-104">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] の他のチュートリアルでは、 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)][デバッグ] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]メニューの **[デバッグ開始]** オプションを使用して、 **の配置環境である** でパッケージを実行しました。</span><span class="sxs-lookup"><span data-stu-id="1dc0c-104">In other [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] tutorials, you ran packages in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], the development environment for [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], using the **Start Debugging** option on the **Debug** menu.</span></span> <span data-ttu-id="1dc0c-105">今度は別の方法でパッケージを実行します。</span><span class="sxs-lookup"><span data-stu-id="1dc0c-105">This time you will run the packages differently.</span></span>

 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="1dc0c-106">には、テスト環境と運用環境でパッケージを実行するときに使用できるコマンド プロンプト ユーティリティ `dtexec` やパッケージ実行ユーティリティなどのツールが付属しています。</span><span class="sxs-lookup"><span data-stu-id="1dc0c-106">provides several tools that you can use to run packages in the test and production environment: the command prompt utility `dtexec` and the Execute Package Utility.</span></span> <span data-ttu-id="1dc0c-107">パッケージ実行ユーティリティは、`dtexec` を基に構築されたグラフィカル ツールです。</span><span class="sxs-lookup"><span data-stu-id="1dc0c-107">The Execute Package Utility is a graphical tool that is built on `dtexec`.</span></span> <span data-ttu-id="1dc0c-108">この 2 つのツールはパッケージを即座に実行します。</span><span class="sxs-lookup"><span data-stu-id="1dc0c-108">Both of these tools execute the package immediately.</span></span> <span data-ttu-id="1dc0c-109">さらに、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] には、SQL Server エージェントのジョブの一工程としてパッケージの実行をスケジュールするように設計された SQL Server エージェントのサブシステムがあります。</span><span class="sxs-lookup"><span data-stu-id="1dc0c-109">In addition, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] provides a subsystem of SQL Server Agent that is especially designed for scheduling package execution as a step in a SQL Server Agent job.</span></span>

 <span data-ttu-id="1dc0c-110">パッケージ実行ユーティリティは、配置したパッケージを実行するために使用します。</span><span class="sxs-lookup"><span data-stu-id="1dc0c-110">You will use the Execute Package Utility to run the deployed packages.</span></span> <span data-ttu-id="1dc0c-111">パッケージはそのままの状態で使用されるため、ダイアログ ボックスのページで情報を更新する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="1dc0c-111">The packages will be used as is; therefore, you do not have to update information on any pages in the dialog box.</span></span> <span data-ttu-id="1dc0c-112">パッケージ実行ユーティリティで最初に表示される [全般] ページからパッケージを実行します。</span><span class="sxs-lookup"><span data-stu-id="1dc0c-112">You will run the packages from the General page, which is the first page in the Execute Package Utility.</span></span> <span data-ttu-id="1dc0c-113">必要に応じて、他のページもクリックして、各パッケージに関する情報を表示できます。</span><span class="sxs-lookup"><span data-stu-id="1dc0c-113">If you like, you can click the other pages too see the information that they contain for each package.</span></span>

> [!NOTE]
>  <span data-ttu-id="1dc0c-114">このチュートリアル内でパッケージが正しく実行されるように、オプションは変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="1dc0c-114">To ensure that the packages run successfully in the context of this tutorial, you should not modify any options.</span></span>

 <span data-ttu-id="1dc0c-115">パッケージ実行ユーティリティを使用して [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] でパッケージを実行する前に、Integration Services サービスが実行していることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="1dc0c-115">Before you run packages in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] by using the Execute Package Utility, ensure that the Integration Services service is running.</span></span> <span data-ttu-id="1dc0c-116">Integration Services サービスは、パッケージの保管と実行のサポートを提供します。</span><span class="sxs-lookup"><span data-stu-id="1dc0c-116">The Integration Services service provides support for package storage and execution.</span></span> <span data-ttu-id="1dc0c-117">このサービスが停止した場合は、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] に接続できず、実行するパッケージが [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] に表示されません。</span><span class="sxs-lookup"><span data-stu-id="1dc0c-117">If the service is stopped, you cannot connect to [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] and [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] does not list the packages to run.</span></span> <span data-ttu-id="1dc0c-118">また、パッケージを配置したインスタンスでパッケージを実行する権限も必要です。</span><span class="sxs-lookup"><span data-stu-id="1dc0c-118">You also must have permissions to run the package on the instance where the package has been deployed.</span></span> <span data-ttu-id="1dc0c-119">詳細については、「[Integration Services のロール &#40;SSIS サービス&#41;](security/integration-services-roles-ssis-service.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1dc0c-119">For more information, see [Integration Services Roles &#40;SSIS Service&#41;](security/integration-services-roles-ssis-service.md).</span></span>

 <span data-ttu-id="1dc0c-120">[格納されたパッケージ] フォルダー内の最上位フォルダーは、Integration Services サービスが監視するユーザー定義フォルダーです。</span><span class="sxs-lookup"><span data-stu-id="1dc0c-120">The top-level folders within the Stored Packages folder are the user-defined folders that Integration Services service monitors.</span></span> <span data-ttu-id="1dc0c-121">MsDtsSrvr.ini.xml ファイルで指定できるフォルダー数に制限はありません。</span><span class="sxs-lookup"><span data-stu-id="1dc0c-121">You can specify as many or few folders in the MsDtsSrvr.ini.xml file as you want.</span></span> <span data-ttu-id="1dc0c-122">このチュートリアルでは、既定の MsDtsSrvr.ini.xml ファイルを使用し、[格納されたパッケージ] 内の最上位フォルダーの名前は "File System" と "MSDB" であると想定しています。</span><span class="sxs-lookup"><span data-stu-id="1dc0c-122">This tutorial assumes that you are using the default MsDtsSrvr.ini.xml file, and that the names of the top-level folders within Stored Packages are File System and MSDB.</span></span>

### <a name="to-connect-to-integration-services-in-sql-server-management-studio"></a><span data-ttu-id="1dc0c-123">SQL Server Management Studio で Integration Services に接続するには</span><span class="sxs-lookup"><span data-stu-id="1dc0c-123">To connect to Integration Services in SQL Server Management Studio</span></span>

1.  <span data-ttu-id="1dc0c-124">**[スタート]** ボタンをクリックし、 **[すべてのプログラム]** 、 **[Microsoft SQL Server]** の順にポイントし、 **[SQL Server Management Studio]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1dc0c-124">Click **Start**, point to **All Programs**, point to **Microsoft SQL Server**, and then click **SQL Server Management Studio**.</span></span>

2.  <span data-ttu-id="1dc0c-125">**[サーバーへの接続]** ダイアログ ボックスで、 **[サーバーの種類]** ボックスの一覧から **[Integration Services]** を選択し、 **[サーバー名]** ボックスにサーバーの名前を入力して、 **[接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1dc0c-125">In the **Connect to Server** dialog box, select **Integration Services** in the **Server type** list, provide a server name in the **Server name** box, and click **Connect**.</span></span>

    > [!IMPORTANT]
    >  <span data-ttu-id="1dc0c-126">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]に接続できない場合は、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サービスが実行されていない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="1dc0c-126">If you cannot connect to [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service is likely not running.</span></span> <span data-ttu-id="1dc0c-127">このサービスの状態を調べるには、 **[スタート]** ボタンをクリックし、 **[すべてのプログラム]** 、 **[Microsoft SQL Server]** 、 **[構成ツール]** の順にポイントして、 **[SQL Server 構成マネージャー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1dc0c-127">To learn the status of the service, click **Start**, point to **All Programs**, point to **Microsoft SQL Server**, point to **Configuration Tools**, and then click **SQL Server Configuration Manager**.</span></span> <span data-ttu-id="1dc0c-128">左ペインで、 **[SQL Server のサービス]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1dc0c-128">In the left pane, click **SQL Server Services**.</span></span> <span data-ttu-id="1dc0c-129">右ペインで、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サービスを見つけます。</span><span class="sxs-lookup"><span data-stu-id="1dc0c-129">In the right pane, find the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service.</span></span> <span data-ttu-id="1dc0c-130">サービスがまだ実行されていない場合は開始します。</span><span class="sxs-lookup"><span data-stu-id="1dc0c-130">Start the service if it is not already running.</span></span>

     [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] <span data-ttu-id="1dc0c-131">が開きます。</span><span class="sxs-lookup"><span data-stu-id="1dc0c-131">opens.</span></span> <span data-ttu-id="1dc0c-132">既定では [オブジェクト エクスプローラー] ウィンドウが開き、 の右上に表示されます。</span><span class="sxs-lookup"><span data-stu-id="1dc0c-132">By default the Object Explorer window is open and placed in the upper right corner of the studio.</span></span> <span data-ttu-id="1dc0c-133">オブジェクト エクスプローラーが開いていない場合は、 **[表示]** メニューの **[オブジェクト エクスプローラー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1dc0c-133">If Object Explorer is not open, click **Object Explorer** on the **View** menu.</span></span>

### <a name="to-run-the-packages-using-the-execute-package-utility"></a><span data-ttu-id="1dc0c-134">パッケージ実行ユーティリティを使用してパッケージを実行するには</span><span class="sxs-lookup"><span data-stu-id="1dc0c-134">To run the packages using the Execute Package Utility</span></span>

1.  <span data-ttu-id="1dc0c-135">オブジェクト エクスプローラーで、[格納されたパッケージ] フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="1dc0c-135">In Object Explorer, expand the Stored Packages folder.</span></span>

2.  <span data-ttu-id="1dc0c-136">MSDB フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="1dc0c-136">Expand the MSDB folder.</span></span> <span data-ttu-id="1dc0c-137">パッケージを [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]に配置したため、配置したパッケージはすべて msdb [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] データベースに格納され、MSDB フォルダーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="1dc0c-137">Because you deployed the packages to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], all the deployed packages are stored in the msdb [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database, and all deployed packages appear in the MSDB folder.</span></span> <span data-ttu-id="1dc0c-138">Deployment Tutorial 以外のファイル システムにパッケージを配置した場合を除き、[File System] フォルダーは空です。</span><span class="sxs-lookup"><span data-stu-id="1dc0c-138">The File System folder is empty, unless you have deployed packages to the file system outside of the Deployment Tutorial.</span></span>

3.  <span data-ttu-id="1dc0c-139">パッケージ一覧の一番上から開始し、[DataTransfer] を右クリックして **[パッケージの実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1dc0c-139">Starting at the top of the package list, right-click DataTransfer, and click **Run Package**.</span></span>

4.  <span data-ttu-id="1dc0c-140">**[パッケージ実行ユーティリティ]** ダイアログ ボックスで **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1dc0c-140">In the **Execute Package Utility** dialog box, click **Execute**.</span></span>

5.  <span data-ttu-id="1dc0c-141">**[パッケージ実行ユーティリティ]** ダイアログ ボックスで、パッケージの進行状況と実行結果を表示します。</span><span class="sxs-lookup"><span data-stu-id="1dc0c-141">In the **Execute Package Utility** dialog box, view the progress and execution results of the package.</span></span> <span data-ttu-id="1dc0c-142">**[停止]** ボタンが無効の場合は、パッケージが完了したことを示すので、 **[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1dc0c-142">When the **Stop** button becomes unavailable, which indicates that the package has completed, click **Close**.</span></span>

    > [!IMPORTANT]
    >  <span data-ttu-id="1dc0c-143">パッケージの実行中に **[停止]** をクリックすると、パッケージは完了しません。</span><span class="sxs-lookup"><span data-stu-id="1dc0c-143">If you click **Stop** while the package is running, the package will not finish.</span></span>

6.  <span data-ttu-id="1dc0c-144">**[パッケージ実行ユーティリティ]** ダイアログ ボックスで **[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1dc0c-144">In the **Execute Package Utility** dialog box, click **Close**.</span></span>

7.  <span data-ttu-id="1dc0c-145">LoadXML パッケージに手順 3. ～ 6. を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="1dc0c-145">Repeat steps 3 - 6 for the LoadXML package.</span></span>

8.  <span data-ttu-id="1dc0c-146">**[ファイル]** メニューの **[終了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1dc0c-146">On the **File** menu, click **Exit**.</span></span>

### <a name="to-verify-the-results-of-the-datatransfer-package"></a><span data-ttu-id="1dc0c-147">DataTransfer パッケージの結果を確認するには</span><span class="sxs-lookup"><span data-stu-id="1dc0c-147">To verify the results of the DataTransfer package</span></span>

1.  <span data-ttu-id="1dc0c-148">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]のツール バーから **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1dc0c-148">On the toolbar in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], click **New Query**.</span></span>

2.  <span data-ttu-id="1dc0c-149">**[サーバーへの接続]** ダイアログ ボックスで、 **[サーバーの種類]** ボックスの一覧から **[データベース エンジン]** を選択し、チュートリアル パッケージをインストールしたサーバーの名前または種類 (local) を **[サーバー名]** ボックスに入力して、認証モードを選択します。</span><span class="sxs-lookup"><span data-stu-id="1dc0c-149">In the **Connect to Server** dialog box, select **Database Engine** in the **Server type** list, provide the name of the server name on which you installed the tutorial packages or type (local) in the **Server name** box, and select an authentication mode.</span></span> <span data-ttu-id="1dc0c-150">SQL Server 認証を使用する場合は、ユーザー名とパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="1dc0c-150">If using SQL Server Authentication, provide a user name and password.</span></span>

3.  <span data-ttu-id="1dc0c-151">**[接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1dc0c-151">Click **Connect**.</span></span>

4.  <span data-ttu-id="1dc0c-152">クエリ ウィンドウで、次の SQL ステートメントを入力するか貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="1dc0c-152">In the query window, type or paste the following SQL statement:</span></span>

     `USE AdventureWorks`

     `SELECT * FROM HighIncomeCustomers`

5.  <span data-ttu-id="1dc0c-153">**F5** キーを押すか、ツール バーの実行アイコンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="1dc0c-153">Press **F5** or click the Execute icon on the toolbar.</span></span>

     <span data-ttu-id="1dc0c-154">このクエリによって 31 行のデータが返されます。</span><span class="sxs-lookup"><span data-stu-id="1dc0c-154">The query returns 31 rows of data.</span></span> <span data-ttu-id="1dc0c-155">返された結果には、YearlyIncome 列の値が 100,000 より大きい Customers.txt テキスト ファイルの行が含まれています。</span><span class="sxs-lookup"><span data-stu-id="1dc0c-155">The return result contains any rows from the text file, Customers.txt, that have values larger than 100000 in the YearlyIncome column.</span></span>

6.  <span data-ttu-id="1dc0c-156">DeploymentTutorial フォルダーを見つけ、ログ XML ファイル [Deployment Tutorial Log] を右クリックして、 **[開く]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1dc0c-156">Locate the DeploymentTutorial folder, right-click the log XML file, Deployment Tutorial Log, and then click **Open**.</span></span> <span data-ttu-id="1dc0c-157">メモ帳やその他のテキスト エディターまたは XML エディターを使用してファイルを開くことができます。</span><span class="sxs-lookup"><span data-stu-id="1dc0c-157">You can open the file by using Notepad or the text/XML editor of choice.</span></span>

### <a name="to-verify-the-results-of-the-loadxmldata-package"></a><span data-ttu-id="1dc0c-158">LoadXMLData パッケージの結果を確認するには</span><span class="sxs-lookup"><span data-stu-id="1dc0c-158">To verify the results of the LoadXMLData package</span></span>

1.  <span data-ttu-id="1dc0c-159">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]のツール バーから **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1dc0c-159">On the toolbar in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], click **New Query**.</span></span>

2.  <span data-ttu-id="1dc0c-160">**[サーバーへの接続]** ダイアログ ボックスで、 **[サーバーの種類]** ボックスの一覧から **[データベース エンジン]** を選択し、チュートリアル パッケージをインストールしたサーバーの名前または「(local)」を **[サーバー名]** ボックスに入力して、認証モードを選択します。</span><span class="sxs-lookup"><span data-stu-id="1dc0c-160">If prompted to connect again, in the **Connect to Server** dialog box, select **Database Engine** in the **Server type** list, provide the name of the server on which you installed the tutorial packages or enter (local) in the **Server name** box, and select an authentication mode.</span></span> <span data-ttu-id="1dc0c-161">SQL Server 認証を使用する場合は、ユーザー名とパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="1dc0c-161">If using SQL Server Authentication, provide a user name and password.</span></span>

3.  <span data-ttu-id="1dc0c-162">**[接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1dc0c-162">Click **Connect**.</span></span>

4.  <span data-ttu-id="1dc0c-163">クエリ ウィンドウで、次の SQL ステートメントを入力するか貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="1dc0c-163">In the query window, type or paste the following SQL statement:</span></span>

     `USE AdventureWorks`

     `SELECT * FROM OrderDatesByCountryRegion`

5.  <span data-ttu-id="1dc0c-164">**F5** キーを押すか、ツール バーの実行アイコンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="1dc0c-164">Press **F5** or click the Execute icon on the toolbar.</span></span>

     <span data-ttu-id="1dc0c-165">このクエリによって 21 行のデータが返されます。</span><span class="sxs-lookup"><span data-stu-id="1dc0c-165">The query returns 21 rows of data.</span></span> <span data-ttu-id="1dc0c-166">返された結果は、XML データ ファイル orders.xml の行で構成されています。</span><span class="sxs-lookup"><span data-stu-id="1dc0c-166">The return result consists of the rows from the XML data file, orders.xml.</span></span> <span data-ttu-id="1dc0c-167">各行は国/地域別の要約であり、国名/地域名、国/地域ごとの注文数、および最新と最古の注文日が示されます。</span><span class="sxs-lookup"><span data-stu-id="1dc0c-167">Each row is a summary by country/region; the row lists the name of a country/region, the number of orders for each country/region and the dates of the newest and oldest orders.</span></span>

<span data-ttu-id="1dc0c-168">![Integration Services アイコン (小)](media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="1dc0c-168">![Integration Services icon (small)](media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="1dc0c-169">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="1dc0c-169">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="1dc0c-170">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="1dc0c-170">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="1dc0c-171">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="1dc0c-171">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="1dc0c-172">参照</span><span class="sxs-lookup"><span data-stu-id="1dc0c-172">See Also</span></span>
 [<span data-ttu-id="1dc0c-173">dtexec ユーティリティ</span><span class="sxs-lookup"><span data-stu-id="1dc0c-173">dtexec Utility</span></span>](packages/dtexec-utility.md)


