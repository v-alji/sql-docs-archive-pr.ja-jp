---
title: SSRS サービス アプリケーションを使用するためのサブスクリプションと警告の準備 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Reporting Services Shared Service
- SharePoint Mode [Reporting Services]
- SharePoint Mode
- Reporting Services Service Application
- SSRS service application
ms.assetid: d0de3f1f-4887-47fb-bacf-46aaad74c4be
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9c09033b6a31295b8fbe42058cba9059f5d05629
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742941"
---
# <a name="provision-subscriptions-and-alerts-for-ssrs-service-applications"></a><span data-ttu-id="ede45-102">SSRS サービス アプリケーションを使用するためのサブスクリプションと警告の準備</span><span class="sxs-lookup"><span data-stu-id="ede45-102">Provision Subscriptions and Alerts for SSRS Service Applications</span></span>
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="ede45-103">のサブスクリプションとデータ警告を利用するには、SQL Server エージェントが必要です。また、SQL Server エージェントに対する権限を構成する必要もあります。</span><span class="sxs-lookup"><span data-stu-id="ede45-103">subscriptions and data alerts require SQL Server Agent and require the configuration of permissions for SQL Server Agent.</span></span> <span data-ttu-id="ede45-104">SQL Server エージェントが実行中であるにもかかわらず、SQL Server エージェントが必要であることを示すエラー メッセージが表示された場合は、権限を更新または確認してください。</span><span class="sxs-lookup"><span data-stu-id="ede45-104">If you see error messages that indicate SQL Server Agent is required and you have verified SQL Server Agent is running, then update or verify permissions.</span></span> <span data-ttu-id="ede45-105">このトピックでは、SharePoint モードの [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] を対象とし、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サブスクリプションを使用して SQL Server エージェントの権限を更新する 3 つの方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ede45-105">The scope of this topic is [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in SharePoint mode and the topic describes three ways you can update the permissions of SQL Server Agent with [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] subscriptions.</span></span> <span data-ttu-id="ede45-106">このトピックの手順で使用する資格情報には、サービス アプリケーション データベース、msdb データベース、および master データベースのオブジェクトに対する実行権限を RSExecRole に許可するための十分な権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="ede45-106">The credentials you use for the steps in this topic need to have sufficient permissions to grant execute permissions to the RSExecRole for objects in the service application, msdb, and master databases.</span></span>

||
|-|
|<span data-ttu-id="ede45-107">**[!INCLUDE[applies](../../includes/applies-md.md)]** Sharepoint 2013 &#124; sharepoint 2010</span><span class="sxs-lookup"><span data-stu-id="ede45-107">**[!INCLUDE[applies](../../includes/applies-md.md)]**  SharePoint 2013 &#124; SharePoint 2010</span></span>|

 <span data-ttu-id="ede45-108">![サービス アプリケーション データベースに対する SQL エージェント権限](../../../2014/sql-server/install/media/rs-provisionsqlagent.gif "サービス アプリケーション データベースに対する SQL エージェント権限")</span><span class="sxs-lookup"><span data-stu-id="ede45-108">![SQL Agent permissions to Service Application DBs](../../../2014/sql-server/install/media/rs-provisionsqlagent.gif "SQL Agent permissions to Service Application DBs")</span></span>

||<span data-ttu-id="ede45-109">説明</span><span class="sxs-lookup"><span data-stu-id="ede45-109">Description</span></span>|
|------|-----------------|
|<span data-ttu-id="ede45-110">**1**</span><span class="sxs-lookup"><span data-stu-id="ede45-110">**1**</span></span>|<span data-ttu-id="ede45-111">Reporting Services サービス アプリケーション データベースをホストしている SQL Server データベース エンジンのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="ede45-111">The instance of SQL Server Database engine that is hosting the Reporting Services service application databases.</span></span>|
|<span data-ttu-id="ede45-112">**2**</span><span class="sxs-lookup"><span data-stu-id="ede45-112">**2**</span></span>|<span data-ttu-id="ede45-113">SQL データベース エンジンのインスタンスに対応する SQL Server エージェントのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="ede45-113">The instance of SQL Server agent for the instance of the SQL database engine.</span></span>|
|<span data-ttu-id="ede45-114">**3**</span><span class="sxs-lookup"><span data-stu-id="ede45-114">**3**</span></span>|<span data-ttu-id="ede45-115">Reporting Services サービス アプリケーション データベース。</span><span class="sxs-lookup"><span data-stu-id="ede45-115">The Reporting Services service application databases.</span></span> <span data-ttu-id="ede45-116">名前は、サービス アプリケーションの作成時に使用された情報に基づいて付けられます。</span><span class="sxs-lookup"><span data-stu-id="ede45-116">The names are based on the information used for creating the service application.</span></span> <span data-ttu-id="ede45-117">データベース名の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="ede45-117">The following are example database names:</span></span><br /><br /> <span data-ttu-id="ede45-118">ReportingService_2fbae157295d49df86d0b85760c704b0</span><span class="sxs-lookup"><span data-stu-id="ede45-118">ReportingService_2fbae157295d49df86d0b85760c704b0</span></span><br /><br /> <span data-ttu-id="ede45-119">ReportingService_2fbae157295d49df86d0b85760c704b0_Alerting</span><span class="sxs-lookup"><span data-stu-id="ede45-119">ReportingService_2fbae157295d49df86d0b85760c704b0_Alerting</span></span><br /><br /> <span data-ttu-id="ede45-120">ReportingService_2fbae157295d49df86d0b85760c704b0TempDB</span><span class="sxs-lookup"><span data-stu-id="ede45-120">ReportingService_2fbae157295d49df86d0b85760c704b0TempDB</span></span>|
|<span data-ttu-id="ede45-121">**4**</span><span class="sxs-lookup"><span data-stu-id="ede45-121">**4**</span></span>|<span data-ttu-id="ede45-122">SQL Server データベース エンジンのインスタンスの master および MSDB データベース。</span><span class="sxs-lookup"><span data-stu-id="ede45-122">The master and MSDB database of the instance of the SQL Server Database engine.</span></span>|

 <span data-ttu-id="ede45-123">権限を更新するには、次の 3 つの方法のいずれかを使用してください。</span><span class="sxs-lookup"><span data-stu-id="ede45-123">Use one the following three methods to update the permissions:</span></span>

1.  <span data-ttu-id="ede45-124">**[サブスクリプションと警告の準備]** ページで資格情報を入力し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ede45-124">From the **Provisions and Subscriptions and Alerts** page, type credentials and click **ok**.</span></span>

2.  <span data-ttu-id="ede45-125">[サブスクリプションと警告の準備] ページの **[スクリプトのダウンロード]** をクリックして、権限の構成に使用できる Transact-SQL スクリプトをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="ede45-125">From the Provisions and Subscriptions and Alerts page, click the **Download Script** button to download a transact SQL script that can be used to configure permissions.</span></span>

3.  <span data-ttu-id="ede45-126">PowerShell コマンドレットを実行して、権限の構成に使用できる Transact-SQL スクリプトを作成します。</span><span class="sxs-lookup"><span data-stu-id="ede45-126">Run a PowerShell cmdlet to build a transact SQL script that can be used to configure permissions.</span></span>

### <a name="to-update-permissions-using-the-provision-page"></a><span data-ttu-id="ede45-127">準備ページを使用して権限を更新するには</span><span class="sxs-lookup"><span data-stu-id="ede45-127">To update permissions using the provision page</span></span>

1.  <span data-ttu-id="ede45-128">SharePoint サーバーの全体管理で、 **[アプリケーション構成の管理]** の **[サービス アプリケーションの管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ede45-128">From SharePoint Central Administration, in the **Application Management** group click **Manage Service Applications**</span></span>

2.  <span data-ttu-id="ede45-129">リストからサービス アプリケーションを探し、アプリケーションの名前をクリックするか、または **[種類]** 列をクリックしてサービス アプリケーションを選択し、SharePoint リボンで **[管理]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="ede45-129">Find your service application in the list and click the name of the application or click the **Type** column to select the services application and click the **Manage** button in the SharePoint ribbon.</span></span>

3.  <span data-ttu-id="ede45-130">**[Reporting Services アプリケーションの管理]** ページで、 **[サブスクリプションと警告の準備]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ede45-130">On the **Manage Reporting Services Application** page, click **Provision Subscriptions and Alerts**.</span></span>

4.  <span data-ttu-id="ede45-131">SharePoint 管理者がマスター データベースとサービス アプリケーション データベースに対する十分な権限を持っている場合は、それらの資格情報を入力します。</span><span class="sxs-lookup"><span data-stu-id="ede45-131">If the SharePoint administrator has enough privileges to the Master database and the service application databases, type those credentials.</span></span>

5.  <span data-ttu-id="ede45-132">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ede45-132">Click the **OK** button.</span></span>

##  <a name="to-download-the-transact-sql-script"></a><a name="bkmk_download"></a> <span data-ttu-id="ede45-133">Transact-SQL スクリプトをダウンロードするには</span><span class="sxs-lookup"><span data-stu-id="ede45-133">To download the Transact-SQL Script</span></span>

1.  <span data-ttu-id="ede45-134">SharePoint サーバーの全体管理で、 **[アプリケーション構成の管理]** の **[サービス アプリケーションの管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ede45-134">From SharePoint Central Administration, in the **Application Management** group click **Manage Service Applications**</span></span>

2.  <span data-ttu-id="ede45-135">リストからサービス アプリケーションを探し、アプリケーションの名前をクリックするか、または **[種類]** 列をクリックしてサービス アプリケーションを選択し、SharePoint リボンで **[管理]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="ede45-135">Find your service application in the list and click the name of the application or click the **Type** column to select the services application and click the **Manage** button in the SharePoint ribbon.</span></span>

3.  <span data-ttu-id="ede45-136">**[Reporting Services アプリケーションの管理]** ページで、 **[サブスクリプションと警告の準備]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ede45-136">On the **Manage Reporting Services Application** page, click **Provision Subscriptions and Alerts**.</span></span>

4.  <span data-ttu-id="ede45-137">**[状態の表示]** 領域で、SQL Server エージェントが実行中であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="ede45-137">In the **View Status** area, verify SQL Server Agent is running.</span></span>

5.  <span data-ttu-id="ede45-138">**[スクリプトのダウンロード]** をクリックして、SQL Server Management Studio 内で実行することにより権限を構成できる Transact-SQL スクリプトをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="ede45-138">Click **Download Script** to download a transact SQL script you can run in SQL Server Management studio to grant permissions.</span></span> <span data-ttu-id="ede45-139">作成されるスクリプト ファイル名には、Reporting Services サービス アプリケーションの名前が使用されます (例: **[サービス アプリケーションの名前]** -GrantRights.sql)。</span><span class="sxs-lookup"><span data-stu-id="ede45-139">The script file name that is created will contain the name of your Reporting Services service application name, for example **[name of the service application]-GrantRights.sql**.</span></span>

### <a name="to-generate-the-transact-sql-statement-with-powershell"></a><span data-ttu-id="ede45-140">PowerShell を使用して Transact-SQL ステートメントを生成するには</span><span class="sxs-lookup"><span data-stu-id="ede45-140">To generate the Transact-SQL statement with PowerShell</span></span>

1.  <span data-ttu-id="ede45-141">SharePoint 2010 管理シェルで Windows PowerShell コマンドレットを使用して、Transact-SQL スクリプトを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="ede45-141">You can also use a Windows PowerShell cmdlet in the SharePoint 2010 Management Shell to create the Transact-SQL script.</span></span>

2.  <span data-ttu-id="ede45-142">**[スタート]** ボタンをクリックし、 **[すべてのプログラム]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ede45-142">On the **Start** menu, click **All Programs**.</span></span>

3.  <span data-ttu-id="ede45-143">[ **Microsoft sharepoint 2010 製品**] を展開し、[ **Sharepoint 2010 管理シェル**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ede45-143">Expand **Microsoft SharePoint 2010 Products** and click **SharePoint 2010 Management Shell**.</span></span>

4.  <span data-ttu-id="ede45-144">次の PowerShell コマンドレットの、レポート サーバー データベース名、アプリケーション プール アカウント、およびステートメント パスを置き換えます。</span><span class="sxs-lookup"><span data-stu-id="ede45-144">Update the following PowerShell cmdlet by replacing the name of the report server database, application pool account, and the path of the statement.</span></span>

     <span data-ttu-id="ede45-145">**コマンドレットの構文:** `Get-SPRSDatabaseRightsScript -DatabaseName <ReportingServices database name> -UserName <app pool account> -IsWindowsUser | Out-File <path of statement>`</span><span class="sxs-lookup"><span data-stu-id="ede45-145">**Syntax of cmdlet:** `Get-SPRSDatabaseRightsScript -DatabaseName <ReportingServices database name> -UserName <app pool account> -IsWindowsUser | Out-File <path of statement>`</span></span>

     <span data-ttu-id="ede45-146">**サンプル コマンドレット:** `Get-SPRSDatabaseRightsScript -DatabaseName ReportingService_46fd00359f894b828907b254e3f6257c -UserName "NT AUTHORITY\NETWORK SERVICE" -IsWindowsUser | Out-File c:\SQLServerAgentrights.sql`</span><span class="sxs-lookup"><span data-stu-id="ede45-146">**Sample cmdlet:** `Get-SPRSDatabaseRightsScript -DatabaseName ReportingService_46fd00359f894b828907b254e3f6257c -UserName "NT AUTHORITY\NETWORK SERVICE" -IsWindowsUser | Out-File c:\SQLServerAgentrights.sql`</span></span>

## <a name="using-the-transact-sql-script"></a><span data-ttu-id="ede45-147">Transact-SQL スクリプトの使用</span><span class="sxs-lookup"><span data-stu-id="ede45-147">Using the Transact-SQL Script</span></span>
 <span data-ttu-id="ede45-148">次の手順は、準備ページからダウンロードしたスクリプトか、または PowerShell を使用して作成したスクリプトに対して使用できます。</span><span class="sxs-lookup"><span data-stu-id="ede45-148">The following procedures can be used with scripts download from the provisions page or scripts created using PowerShell.</span></span>

#### <a name="to-load-the-transact-sql-script-in-sql-server-management-studio"></a><span data-ttu-id="ede45-149">SQL Server Management Studio に Transact-SQL スクリプトを読み込むには</span><span class="sxs-lookup"><span data-stu-id="ede45-149">To load the Transact-SQL script in SQL Server Management Studio</span></span>

1.  <span data-ttu-id="ede45-150">SQL Server Management Studio を開くには、[**スタート**] メニューの [ **Microsoft SQL Server 2012** ] をクリックし、[ **SQL Server Management Studio**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ede45-150">To open SQL Server Management Studio, on the **Start** menu, click **Microsoft SQL Server 2012** and click **SQL Server Management Studio**.</span></span>

2.  <span data-ttu-id="ede45-151">**[サーバーへの接続]** ダイアログ ボックスで、次のオプションを設定します。</span><span class="sxs-lookup"><span data-stu-id="ede45-151">In the **Connect to Server** dialog box set the following options:</span></span>

    -   <span data-ttu-id="ede45-152">**[サーバーの種類]** ボックスの一覧で、 **[データベース エンジン]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ede45-152">In the **Server type** list, select **Database Engine**</span></span>

    -   <span data-ttu-id="ede45-153">**[サーバー名]** で、SQL Server エージェントの構成対象となる SQL Server インスタンスの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="ede45-153">In **Server Name**, type the name of the SQL Server instance on which you want to configure SQL Server Agent.</span></span>

    -   <span data-ttu-id="ede45-154">認証モードを選択します。</span><span class="sxs-lookup"><span data-stu-id="ede45-154">Select an authentication mode.</span></span>

    -   <span data-ttu-id="ede45-155">SQL Server 認証を使用して接続する場合は、ログイン名とパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="ede45-155">If connecting using SQL Server Authentication, provide a login and password.</span></span>

3.  <span data-ttu-id="ede45-156">**[接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ede45-156">Click **Connect**.</span></span>

#### <a name="to-run-the-transact-sql-statement"></a><span data-ttu-id="ede45-157">Transact-SQL ステートメントを実行するには</span><span class="sxs-lookup"><span data-stu-id="ede45-157">To run the Transact-SQL statement</span></span>

1.  <span data-ttu-id="ede45-158">SQL Server Management Studio のツール バーで、 **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ede45-158">On the toolbar of SQL Server Management Studio, click **New Query**.</span></span>

2.  <span data-ttu-id="ede45-159">**[ファイル]** メニューの **[開く]** をポイントし、 **[ファイル]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ede45-159">On the **File** menu, click **Open**, and then click **File**.</span></span>

3.  <span data-ttu-id="ede45-160">SharePoint 2010 管理シェルで生成した Transact-SQL ステートメントの保存先フォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="ede45-160">Navigate to the folder where you saved the Transact-SQL statement that you generated in SharePoint 2010 Management Shell.</span></span>

4.  <span data-ttu-id="ede45-161">ファイルをクリックし、 **[開く]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ede45-161">Click the file and then click **Open**.</span></span>

     <span data-ttu-id="ede45-162">ステートメントがクエリ ウィンドウに追加されます。</span><span class="sxs-lookup"><span data-stu-id="ede45-162">The statement is added to the query window.</span></span>

5.  <span data-ttu-id="ede45-163">**[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ede45-163">Click **Execute**.</span></span>


