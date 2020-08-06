---
title: DAC パッケージの検証 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- data-tier application [SQL Server], validate
- data-tier application [SQL Server], compare
- validate DAC
- compare DACs
- data-tier application [SQL Server], view
- view DAC
ms.assetid: 726ffcc2-9221-424a-8477-99e3f85f03bd
author: stevestein
ms.author: sstein
ms.openlocfilehash: 078c7bfeef2ff8636243f4853c03de252c7b9289
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645128"
---
# <a name="validate-a-dac-package"></a><span data-ttu-id="fbb11-102">DAC パッケージの検証</span><span class="sxs-lookup"><span data-stu-id="fbb11-102">Validate a DAC Package</span></span>
  <span data-ttu-id="fbb11-103">DAC パッケージを運用環境に配置する前にパッケージの内容を確認し、既存の DAC をアップグレードする前にアップグレード処理を検証するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="fbb11-103">It is a good practice to review the contents of a DAC package before deploying it in production, and to validate the upgrade actions before upgrading an existing DAC.</span></span> <span data-ttu-id="fbb11-104">これは、特に、外部で開発されたパッケージを配置する場合に当てはまります。</span><span class="sxs-lookup"><span data-stu-id="fbb11-104">This is especially true when deploying packages that were not developed in your organization.</span></span>  
  
1.  <span data-ttu-id="fbb11-105">**作業を開始する準備:** [前提条件](#Prerequisites)</span><span class="sxs-lookup"><span data-stu-id="fbb11-105">**Before you begin:**  [Prerequisites](#Prerequisites)</span></span>  
  
2.  <span data-ttu-id="fbb11-106">**DAC のアップグレード:** [DAC の内容の表示](#ViewDACContents)、[データベースの変更の表示](#ViewDBChanges)、[アップグレード処理の表示](#ViewUpgradeActions)、[Compare DACs](#CompareDACs)</span><span class="sxs-lookup"><span data-stu-id="fbb11-106">**To upgrade a DAC, using:**  [View the Contents of a DAC](#ViewDACContents), [View Database Changes](#ViewDBChanges), [View Upgrade Actions](#ViewUpgradeActions), [Compare DACs](#CompareDACs)</span></span>  
  
##  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="fbb11-107">前提条件</span><span class="sxs-lookup"><span data-stu-id="fbb11-107">Prerequisites</span></span>  
 <span data-ttu-id="fbb11-108">ソースが不明または信頼されていない DAC パッケージは配置しないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="fbb11-108">We recommend that you do not deploy a DAC package from unknown or untrusted sources.</span></span> <span data-ttu-id="fbb11-109">こうした DAC には、意図しない [!INCLUDE[tsql](../../includes/tsql-md.md)] コードを実行したり、スキーマを変更してエラーを発生させるような、悪意のあるコードが含まれている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="fbb11-109">Such DACs could contain malicious code that might execute unintended [!INCLUDE[tsql](../../includes/tsql-md.md)] code or cause errors by modifying the schema.</span></span> <span data-ttu-id="fbb11-110">DAC のソースが不明または信頼されていない場合は、使用する前に、[!INCLUDE[ssDE](../../includes/ssde-md.md)]の隔離されたテスト インスタンスに DAC を配置し、データベースに対して [DBCC CHECKDB &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) を実行してください。また、ストアド プロシージャやその他のユーザー定義コードなど、データベースのコードを確認してください。</span><span class="sxs-lookup"><span data-stu-id="fbb11-110">Before you use a DAC from an unknown or untrusted source, deploy it on an isolated test instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)], run [DBCC CHECKDB &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) on the database, and also examine the code, such as stored procedures or other user-defined code, in the database.</span></span>  
  
##  <a name="view-the-contents-of-a-dac"></a><a name="ViewDACContents"></a> <span data-ttu-id="fbb11-111">DAC の内容の表示</span><span class="sxs-lookup"><span data-stu-id="fbb11-111">View the Contents of a DAC</span></span>  
 <span data-ttu-id="fbb11-112">データ層アプリケーション (DAC) パッケージの内容を表示する方法は 2 つあります。</span><span class="sxs-lookup"><span data-stu-id="fbb11-112">There are two mechanisms for viewing the contents of a data-tier application (DAC) package.</span></span> <span data-ttu-id="fbb11-113">1 つは、SQL Server 開発者ツールの DAC プロジェクトに DAC パッケージをインポートする方法です。</span><span class="sxs-lookup"><span data-stu-id="fbb11-113">You can import the DAC package to a DAC project in SQL Server Developer Tools.</span></span> <span data-ttu-id="fbb11-114">もう 1 つは、パッケージの内容をフォルダーにアンパックする方法です。</span><span class="sxs-lookup"><span data-stu-id="fbb11-114">You can unpack the contents of the package to a folder.</span></span>  
  
 <span data-ttu-id="fbb11-115">**SQL Server 開発者ツールでの DAC の表示**</span><span class="sxs-lookup"><span data-stu-id="fbb11-115">**View a DAC in SQL Server Developer Tools**</span></span>  
  
1.  <span data-ttu-id="fbb11-116">**[ファイル]** メニューの **[新規作成]** をポイントし、 **[プロジェクト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fbb11-116">Open the **File** menu, select **New**, and then select **Project...**.</span></span>  
  
2.  <span data-ttu-id="fbb11-117">**[SQL Server]** プロジェクト テンプレートを選択し、 **[名前]** 、 **[場所]** 、および **[ソリューション名]** を指定します。</span><span class="sxs-lookup"><span data-stu-id="fbb11-117">Select the **SQL Server** project template, and specify a **Name**, **Location**, and **Solution name**.</span></span>  
  
3.  <span data-ttu-id="fbb11-118">**ソリューション エクスプローラー**でプロジェクト ノードを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fbb11-118">In **Solution Explorer**, right click the project node and select **Properties...**.</span></span>  
  
4.  <span data-ttu-id="fbb11-119">**[プロジェクトの設定]** タブの **[出力の種類]** セクションで **[データ層アプリケーション (.dacpac File)]** チェック ボックスをオンにし、プロパティ ダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="fbb11-119">On the **Project Settings** tab, in the **Output Types** section, select the **Data-tier Application (.dacpac File)** check box, and then close the properties dialog.</span></span>  
  
5.  <span data-ttu-id="fbb11-120">**ソリューション エクスプローラー**でプロジェクト ノードを右クリックし、 **[データ層アプリケーションのインポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fbb11-120">In **Solution Explorer**, right click the project node and select **Import Data-tier Application...**.</span></span>  
  
6.  <span data-ttu-id="fbb11-121">**ソリューション エクスプローラー** を使用して、サーバーの選択ポリシーや配置前スクリプトと配置後スクリプトなど、DAC 内のすべてのファイルを開くことができます。</span><span class="sxs-lookup"><span data-stu-id="fbb11-121">Use **Solution Explorer** to open all of the files in the DAC, such as the server selection policy and the pre- and post-deployment scripts.</span></span>  
  
7.  <span data-ttu-id="fbb11-122">**スキーマ ビュー** を使用すると、スキーマ内のすべてのオブジェクトを確認できます。特に、関数やストアド プロシージャなどのオブジェクトのコードを確認します。</span><span class="sxs-lookup"><span data-stu-id="fbb11-122">Use the **Schema View** to review all of the objects in the schema, particularly reviewing the code in objects such as functions or stored procedures.</span></span>  
  
 <span data-ttu-id="fbb11-123">**フォルダーでの DAC の表示**</span><span class="sxs-lookup"><span data-stu-id="fbb11-123">**View a DAC in a Folder**</span></span>  
  
-   <span data-ttu-id="fbb11-124">「 [Unpack a DAC Package](unpack-a-dac-package.md)」での指示に従って、DAC パッケージをフォルダーにアンパックします。</span><span class="sxs-lookup"><span data-stu-id="fbb11-124">Unpack the DAC package into a folder by following the instructions in [Unpack a DAC Package](unpack-a-dac-package.md).</span></span>  
  
-   <span data-ttu-id="fbb11-125">[!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプトの内容を表示するには、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] の [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]クエリ エディターでスクリプトを開きます。</span><span class="sxs-lookup"><span data-stu-id="fbb11-125">View the contents of the [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts by opening them in the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span>  
  
-   <span data-ttu-id="fbb11-126">テキスト ファイルの内容を表示するには、メモ帳などのツールを使用します。</span><span class="sxs-lookup"><span data-stu-id="fbb11-126">View the contents of the text files in tools such as notepad.</span></span>  
  
##  <a name="view-database-changes"></a><a name="ViewDBChanges"></a> <span data-ttu-id="fbb11-127">データベースの変更の表示</span><span class="sxs-lookup"><span data-stu-id="fbb11-127">View Database Changes</span></span>  
 <span data-ttu-id="fbb11-128">現在のバージョンの DAC を実稼働環境に配置した後で、関連付けられているデータベースが直接変更され、その変更内容が新しいバージョンの DAC で定義されているスキーマと矛盾する場合があります。</span><span class="sxs-lookup"><span data-stu-id="fbb11-128">After the current version of a DAC was deployed to production, changes may have been made directly to the associated database that might conflict with the schema defined in a new version of the DAC.</span></span> <span data-ttu-id="fbb11-129">新しいバージョンの DAC にアップグレードする前に、そのような変更がデータベースに対して行われたかどうかを確認してください。</span><span class="sxs-lookup"><span data-stu-id="fbb11-129">Before upgrading to a new version of the DAC, check to see if such changes have been made to the database.</span></span>  
  
 <span data-ttu-id="fbb11-130">**ウィザードの使用によるデータベースの変更の表示**</span><span class="sxs-lookup"><span data-stu-id="fbb11-130">**View Database Changes by Using a Wizard**</span></span>  
  
1.  <span data-ttu-id="fbb11-131">現在配置されている DAC と、新しいバージョンの DAC を含む DAC パッケージを指定して、 **データ層アプリケーションのアップグレード** ウィザードを実行します。</span><span class="sxs-lookup"><span data-stu-id="fbb11-131">Run the **Upgrade Data-tier Application** wizard, specifying the currently deployed DAC and the DAC package containing the new version of the DAC.</span></span>  
  
2.  <span data-ttu-id="fbb11-132">**[変更の検出]** ページで、データベースに対する変更のレポートを確認します。</span><span class="sxs-lookup"><span data-stu-id="fbb11-132">On the **Detect Change** page, review the report of the changes that have been made to the database.</span></span>  
  
3.  <span data-ttu-id="fbb11-133">アップグレードを続行しない場合は、 **[キャンセル]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fbb11-133">Select **Cancel** if you do not want to continue with the upgrade.</span></span>  
  
4.  <span data-ttu-id="fbb11-134">ウィザードの使用方法については、「 [データ層アプリケーションのアップグレード](upgrade-a-data-tier-application.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fbb11-134">For more information on using the wizard, see [Upgrade a Data-tier Application](upgrade-a-data-tier-application.md).</span></span>  
  
### <a name="view-database-changes-by-using-powershell"></a><span data-ttu-id="fbb11-135">PowerShell の使用によるデータベースの変更の表示</span><span class="sxs-lookup"><span data-stu-id="fbb11-135">View Database Changes by Using PowerShell</span></span>
  
1.  <span data-ttu-id="fbb11-136">SMO サーバー オブジェクトを作成し、表示する DAC を含んだインスタンスに設定します。</span><span class="sxs-lookup"><span data-stu-id="fbb11-136">Create a SMO Server object and set it to the instance that contains the DAC to be viewed.</span></span>  
  
2.  <span data-ttu-id="fbb11-137">`ServerConnection` オブジェクトを開いて、同じインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="fbb11-137">Open a `ServerConnection` object and connect to the same instance.</span></span>  
  
3.  <span data-ttu-id="fbb11-138">DAC の名前を変数で指定します。</span><span class="sxs-lookup"><span data-stu-id="fbb11-138">Specify the DAC name in a variable.</span></span>  
  
4.  <span data-ttu-id="fbb11-139">`GetDatabaseChanges()` メソッドを使用して `ChangeResults` オブジェクトを取得し、そのオブジェクトをテキスト ファイルにパイプして、新しいオブジェクト、削除したオブジェクト、および変更したオブジェクトを含む簡単なレポートを生成します。</span><span class="sxs-lookup"><span data-stu-id="fbb11-139">Use the `GetDatabaseChanges()` method to retrieve a `ChangeResults` object, and pipe the object to a text file to generate a simple report of new, deleted, and changed objects.</span></span>  
  
### <a name="view-database-changes-example-powershell"></a><span data-ttu-id="fbb11-140">データベースの変更の表示の例 (PowerShell)</span><span class="sxs-lookup"><span data-stu-id="fbb11-140">View Database Changes Example (PowerShell)</span></span>
  
 <span data-ttu-id="fbb11-141">次の例は、MyApplicaiton という名前の配置された DAC で行われた、データベースのすべての変更のレポートを生成します。</span><span class="sxs-lookup"><span data-stu-id="fbb11-141">The following example reports any database changes that have been made in a deployed DAC named MyApplicaiton.</span></span>  
  
```powershell
## Set a SMO Server object to the default instance on the local computer.  
CD SQLSERVER:\SQL\localhost\DEFAULT  
$srv = Get-Item .  
  
## Open a Common.ServerConnection to the same instance.  
$serverconnection = New-Object Microsoft.SqlServer.Management.Common.ServerConnection($srv.ConnectionContext.SqlConnectionObject)  
$serverconnection.Connect()  
$dacstore = New-Object Microsoft.SqlServer.Management.Dac.DacStore($serverconnection)  
  
## Specify the DAC instance name.  
$dacName  = "MyApplication"  
  
## Generate the change list and save to file.  
$dacChanges = $dacstore.GetDatabaseChanges($dacName) | Out-File -Filepath C:\DACScripts\MyApplicationChanges.txt  
```  
  
##  <a name="view-upgrade-actions"></a><a name="ViewUpgradeActions"></a> <span data-ttu-id="fbb11-142">アップグレード処理の表示</span><span class="sxs-lookup"><span data-stu-id="fbb11-142">View Upgrade Actions</span></span>  
 <span data-ttu-id="fbb11-143">DAC パッケージの新しいバージョンを使用して前の DAC パッケージから配置された DAC をアップグレードする前に、アップグレード中に実行される [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを含むレポートを生成して、ステートメントを確認することができます。</span><span class="sxs-lookup"><span data-stu-id="fbb11-143">Before using a new version of a DAC package to upgrade a DAC that was deployed from an earlier DAC package, you can generate a report that contains the [!INCLUDE[tsql](../../includes/tsql-md.md)] statements that will be run during the upgrade, and then review the statements.</span></span>  
  
 <span data-ttu-id="fbb11-144">**ウィザードの使用によるアップグレードの処理のレポート生成**</span><span class="sxs-lookup"><span data-stu-id="fbb11-144">**Report Upgrade Actions by Using a Wizard**</span></span>  
  
1.  <span data-ttu-id="fbb11-145">現在配置されている DAC と、新しいバージョンの DAC を含む DAC パッケージを指定して、 **データ層アプリケーションのアップグレード** ウィザードを実行します。</span><span class="sxs-lookup"><span data-stu-id="fbb11-145">Run the **Upgrade Data-tier Application** wizard, specifying the currently deployed DAC and the DAC package containing the new version of the DAC.</span></span>  
  
2.  <span data-ttu-id="fbb11-146">**[概要]** ページで、アップグレード処理のレポートを確認します。</span><span class="sxs-lookup"><span data-stu-id="fbb11-146">On the **Summary** page, review the report of the upgrade actions.</span></span>  
  
3.  <span data-ttu-id="fbb11-147">アップグレードを続行しない場合は、 **[キャンセル]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fbb11-147">Select **Cancel** if you do not want to continue with the upgrade.</span></span>  
  
4.  <span data-ttu-id="fbb11-148">ウィザードの使用方法については、「 [データ層アプリケーションのアップグレード](upgrade-a-data-tier-application.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fbb11-148">For more information on using the wizard, see [Upgrade a Data-tier Application](upgrade-a-data-tier-application.md).</span></span>  
  
 <span data-ttu-id="fbb11-149">**PowerShell の使用によるアップグレードの処理のレポート生成**</span><span class="sxs-lookup"><span data-stu-id="fbb11-149">**Report Upgrade Actions by Using PowerShell**</span></span>  
  
1.  <span data-ttu-id="fbb11-150">SMO サーバー オブジェクトを作成し、配置された DAC を含んだインスタンスに設定します。</span><span class="sxs-lookup"><span data-stu-id="fbb11-150">Create a SMO Server object and set it to the instance that contains the deployed DAC.</span></span>  
  
2.  <span data-ttu-id="fbb11-151">`ServerConnection` オブジェクトを開いて、同じインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="fbb11-151">Open a `ServerConnection` object and connect to the same instance.</span></span>  
  
3.  <span data-ttu-id="fbb11-152">`System.IO.File` を使用して、DAC パッケージ ファイルを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="fbb11-152">Use `System.IO.File` to load the DAC package file.</span></span>  
  
4.  <span data-ttu-id="fbb11-153">DAC の名前を変数で指定します。</span><span class="sxs-lookup"><span data-stu-id="fbb11-153">Specify the DAC name in a variable.</span></span>  
  
5.  <span data-ttu-id="fbb11-154">`GetIncrementalUpgradeScript()` メソッドを使用して、アップグレードで実行される Transact-SQL ステートメントのリストを取得し、リストをテキスト ファイルにパイプします。</span><span class="sxs-lookup"><span data-stu-id="fbb11-154">Use the `GetIncrementalUpgradeScript()` method to get a list of the Transact-SQL statements an upgrade would run, and pipe the list to a text file.</span></span>  
  
6.  <span data-ttu-id="fbb11-155">DAC パッケージ ファイルの読み取りに使用するファイル ストリームを閉じます。</span><span class="sxs-lookup"><span data-stu-id="fbb11-155">Close the file stream used to read the DAC package file.</span></span>  
  
### <a name="view-upgrade-actions-example-powershell"></a><span data-ttu-id="fbb11-156">アップグレード処理の表示の例 (PowerShell)</span><span class="sxs-lookup"><span data-stu-id="fbb11-156">View Upgrade Actions Example (PowerShell)</span></span>
  
 <span data-ttu-id="fbb11-157">次の例は、MyApplicaiton という名前の DAC を MyApplicationVNext.dacpac ファイルで定義されているスキーマにアップグレードするために実行される Transact-SQL ステートメントのレポートを生成します。</span><span class="sxs-lookup"><span data-stu-id="fbb11-157">The following example reports the Transact-SQL statements that would be run to upgrading a DAC named MyApplicaiton to the schema defined in a MyApplicationVNext.dacpac file.</span></span>  
  
```powershell
## Set a SMO Server object to the default instance on the local computer.  
CD SQLSERVER:\SQL\localhost\DEFAULT  
$srv = Get-Item .  
  
## Open a Common.ServerConnection to the same instance.  
$serverconnection = New-Object Microsoft.SqlServer.Management.Common.ServerConnection($srv.ConnectionContext.SqlConnectionObject)  
$serverconnection.Connect()  
$dacstore = New-Object Microsoft.SqlServer.Management.Dac.DacStore($serverconnection)  
  
## Load the DAC package file.  
$dacpacPath = "C:\MyDACs\MyApplicationVNext.dacpac"  
$fileStream = [System.IO.File]::Open($dacpacPath,[System.IO.FileMode]::OpenOrCreate)  
$dacType = [Microsoft.SqlServer.Management.Dac.DacType]::Load($fileStream)  
  
## Specify the DAC instance name.  
$dacName  = "MyApplication"  
  
## Generate the upgrade script and save to file.  
$dacstore.GetIncrementalUpgradeScript($dacName, $dacType) | Out-File -Filepath C:\DACScripts\MyApplicationUpgrade.sql  
  
## Close the filestream to the new DAC package.  
$fileStream.Close()  
```  
  
##  <a name="compare-dacs"></a><a name="CompareDACs"></a><span data-ttu-id="fbb11-158">Dac の比較</span><span class="sxs-lookup"><span data-stu-id="fbb11-158">Compare DACs</span></span>  
 <span data-ttu-id="fbb11-159">DAC をアップグレードする前に、現在の DAC と新しい DAC に、データベースレベルおよびインスタンスレベルでオブジェクトにどんな相違があるか確認してください。</span><span class="sxs-lookup"><span data-stu-id="fbb11-159">Before upgrading a DAC, it is a good practice to review the differences in the database and instance-level objects between the current and new DACs.</span></span> <span data-ttu-id="fbb11-160">現在の DAC パッケージのコピーがない場合は、現在のデータベースからパッケージを抽出できます。</span><span class="sxs-lookup"><span data-stu-id="fbb11-160">If you do not have a copy of the package for the current DAC, you can extract a package from the current database.</span></span>  
  
 <span data-ttu-id="fbb11-161">SQL Server 開発者ツールで両方の DAC パッケージを DAC プロジェクトにインポートする場合は、スキーマ比較ツールを使用して 2 つの DAC 間の相違を分析できます。</span><span class="sxs-lookup"><span data-stu-id="fbb11-161">If you import both DAC packages into DAC projects in SQL Server Developer Tools, you can use the Schema Compare tool to analyze the differences between the two DACs.</span></span>  
  
 <span data-ttu-id="fbb11-162">または、DAC を別々のフォルダーにアンパックします。</span><span class="sxs-lookup"><span data-stu-id="fbb11-162">Alternatively, unpack the DACs into separate folders.</span></span> <span data-ttu-id="fbb11-163">その後、WinDiff ユーティリティなどの比較ツールを使用して、相違を分析できます。</span><span class="sxs-lookup"><span data-stu-id="fbb11-163">You can then use a difference tool, such as the WinDiff utility, to analyze the differences.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbb11-164">参照</span><span class="sxs-lookup"><span data-stu-id="fbb11-164">See Also</span></span>  
 <span data-ttu-id="fbb11-165">[[データ層アプリケーション]](data-tier-applications.md) </span><span class="sxs-lookup"><span data-stu-id="fbb11-165">[Data-tier Applications](data-tier-applications.md) </span></span>  
 <span data-ttu-id="fbb11-166">[データ層アプリケーションの配置](deploy-a-data-tier-application.md) </span><span class="sxs-lookup"><span data-stu-id="fbb11-166">[Deploy a Data-tier Application](deploy-a-data-tier-application.md) </span></span>  
 [<span data-ttu-id="fbb11-167">データ層アプリケーションのアップグレード</span><span class="sxs-lookup"><span data-stu-id="fbb11-167">Upgrade a Data-tier Application</span></span>](upgrade-a-data-tier-application.md)  
