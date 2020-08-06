---
title: コマンドプロンプトからの PowerPivot のインストール |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 7f1f2b28-c9f5-49ad-934b-02f2fa6b9328
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 54f30142cdc2e39b3ec565d4f965fdad675405e4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644788"
---
# <a name="install-powerpivot-from-the-command-prompt"></a><span data-ttu-id="0ff00-102">コマンド プロンプトからの PowerPivot のインストール</span><span class="sxs-lookup"><span data-stu-id="0ff00-102">Install PowerPivot from the Command Prompt</span></span>
  <span data-ttu-id="0ff00-103">コマンド ラインからセットアップを実行して、SQL Server PowerPivot for SharePoint をインストールすることができます。</span><span class="sxs-lookup"><span data-stu-id="0ff00-103">You can run Setup from the command line to install SQL Server PowerPivot for SharePoint.</span></span> <span data-ttu-id="0ff00-104">コマンドには `/ROLE` パラメーターを含め、`/FEATURES` パラメーターを除外する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0ff00-104">You must include the `/ROLE` parameter in your command and exclude the `/FEATURES` parameter.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="0ff00-105">前提条件</span><span class="sxs-lookup"><span data-stu-id="0ff00-105">Prerequisites</span></span>  
 <span data-ttu-id="0ff00-106">SharePoint Server 2010 Enterprise Edition Service Pack 1 (SP1) をインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="0ff00-106">SharePoint Server 2010 enterprise edition with Service Pack 1 (SP1) must be installed.</span></span>  
  
 <span data-ttu-id="0ff00-107">Analysis Services を準備するには、ドメイン アカウントを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0ff00-107">You must use domain accounts to provision Analysis Services.</span></span>  
  
 <span data-ttu-id="0ff00-108">コンピューターが SharePoint ファームと同じドメインに参加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0ff00-108">The computer must be joined to the same domain as the SharePoint farm.</span></span>  
  
##  <a name="role-based-installation-options"></a><a name="Commands"></a><span data-ttu-id="0ff00-109">/ROLE ベースのインストールオプション</span><span class="sxs-lookup"><span data-stu-id="0ff00-109">/ROLE based installation options</span></span>  
 <span data-ttu-id="0ff00-110">PowerPivot for SharePoint の配置では `/ROLE` パラメーターの代わりに `/FEATURES` パラメーターが使用されます。</span><span class="sxs-lookup"><span data-stu-id="0ff00-110">For PowerPivot for SharePoint deployments, the `/ROLE` parameter is used in place of the `/FEATURES` parameter.</span></span> <span data-ttu-id="0ff00-111">有効な値は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="0ff00-111">Valid values include:</span></span>  
  
-   `SPI_AS_ExistingFarm`  
  
-   `SPI_AS_NewFarm`  
  
 <span data-ttu-id="0ff00-112">どちらのロールを指定しても、アプリケーション、構成、および配置のファイルがインストールされて、SharePoint ファームで PowerPivot for SharePoint を実行できるようになります。</span><span class="sxs-lookup"><span data-stu-id="0ff00-112">Both roles install application, configuration, and deployment files that enable a PowerPivot for SharePoint to run in a SharePoint farm.</span></span> <span data-ttu-id="0ff00-113">指定したロールに基づいて、SharePoint 統合のハードウェアおよびソフトウェアの要件がチェックされます。</span><span class="sxs-lookup"><span data-stu-id="0ff00-113">Specifying either role will cause Setup to check for hardware and software requirements necessary for SharePoint integration.</span></span>  
  
 <span data-ttu-id="0ff00-114">既存のファーム オプションでは、SharePoint ファームが既に存在することが想定されます。</span><span class="sxs-lookup"><span data-stu-id="0ff00-114">The existing farm option assumes that a SharePoint farm is already in place.</span></span> <span data-ttu-id="0ff00-115">新しいファームのオプションでは、新しいファームを作成することを前提としています。データベースエンジンインスタンスをファームのデータベースサーバーとして使用できるように、コマンドライン構文にデータベースエンジンインスタンスを追加する機能がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="0ff00-115">The new farm option assumes that you will create a new farm; it supports the addition of a Database Engine instance in the command line syntax so that you can use the Database Engine instance as the farm's database server.</span></span>  
  
 <span data-ttu-id="0ff00-116">以前のリリースとは異なり、すべてのサーバー構成タスクはインストール後のタスクとして実行されます。</span><span class="sxs-lookup"><span data-stu-id="0ff00-116">In contrast with the previous releases, all server configuration tasks are performed as post-installation tasks.</span></span> <span data-ttu-id="0ff00-117">インストールと構成の手順を自動化している場合は、PowerShell を使用してサーバーを構成できます。</span><span class="sxs-lookup"><span data-stu-id="0ff00-117">If you are automating installation and configuration steps, you can use PowerShell to configure the server.</span></span> <span data-ttu-id="0ff00-118">詳細については、「 [Windows PowerShell を使用した PowerPivot の構成](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/power-pivot-configuration-using-windows-powershell)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0ff00-118">For more information, see [PowerPivot Configuration using Windows PowerShell](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/power-pivot-configuration-using-windows-powershell).</span></span>  
  
## <a name="example-commands"></a><span data-ttu-id="0ff00-119">コマンドの例</span><span class="sxs-lookup"><span data-stu-id="0ff00-119">Example Commands</span></span>  
 <span data-ttu-id="0ff00-120">次の例では、各オプションの使用方法を示します。</span><span class="sxs-lookup"><span data-stu-id="0ff00-120">The following examples illustrate the usage of each option.</span></span> <span data-ttu-id="0ff00-121">例1は `SPI_AS_ExistingFarm` を示しています。</span><span class="sxs-lookup"><span data-stu-id="0ff00-121">Example 1 shows `SPI_AS_ExistingFarm`.</span></span>  
  
```cmd
Setup.exe /q /IAcceptSQLServerLicenseTerms /ACTION=install /ROLE=SPI_AS_ExistingFarm /INSTANCENAME=PowerPivot /INDICATEPROGRESS/ASSVCACCOUNT=<DomainName\UserName> /ASSVCPASSWORD=<StrongPassword> /ASSYSADMINACCOUNTS=<DomainName\UserName>   
```  
  
 <span data-ttu-id="0ff00-122">例 2 は `SPI_AS_NewFarm` を示します。</span><span class="sxs-lookup"><span data-stu-id="0ff00-122">Example 2 shows `SPI_AS_NewFarm`.</span></span> <span data-ttu-id="0ff00-123">データベース エンジンを準備するパラメーターが含まれています。</span><span class="sxs-lookup"><span data-stu-id="0ff00-123">Notice that it includes parameters for provisioning the Database Engine.</span></span>  
  
```cmd
Setup.exe /q /IAcceptSQLServerLicenseTerms /ACTION=install /ROLE=SPI_AS_NewFarm /INSTANCENAME=PowerPivot /INDICATEPROGRESS/SQLSVCACCOUNT=<DomainName\UserName> /SQLSVCPASSWORD=<StrongPassword> /SQLSYSADMINACCOUNTS=<DomainName\UserName> /AGTSVCACCOUNT=<DomainName\UserName> /AGTSVCPASSWORD=<StrongPassword> /ASSVCACCOUNT=<DomainName\UserName> /ASSVCPASSWORD=<StrongPassword> /ASSYSADMINACCOUNTS=<DomainName\UserName>   
```  
  
##  <a name="modifying-the-command-syntax"></a><a name="Join"></a><span data-ttu-id="0ff00-124">コマンドの構文の変更</span><span class="sxs-lookup"><span data-stu-id="0ff00-124">Modifying the command syntax</span></span>  
 <span data-ttu-id="0ff00-125">次の手順に従って、コマンド構文の例を変更します。</span><span class="sxs-lookup"><span data-stu-id="0ff00-125">Use the following steps to modify the example command syntax.</span></span>  
  
1.  <span data-ttu-id="0ff00-126">次のコマンドをコピーして、メモ帳に貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="0ff00-126">Copy the following command into Notepad:</span></span>  
  
    ```cmd
    Setup.exe /q /IAcceptSQLServerLicenseTerms /ACTION=install /ROLE=SPI_AS_ExistingFarm /INSTANCENAME=PowerPivot /INDICATEPROGRESS/ASSVCACCOUNT=<DomainName\UserName> /ASSVCPASSWORD=<StrongPassword> /ASSYSADMINACCOUNTS=<DomainName\UserName>   
    ```  
  
     <span data-ttu-id="0ff00-127">`/q` パラメーターは、セットアップを非表示モードで実行します。この場合、ユーザー インターフェイスは表示されません。</span><span class="sxs-lookup"><span data-stu-id="0ff00-127">The `/q` parameter runs Setup in quiet mode, which suppresses the user interface.</span></span>  
  
     <span data-ttu-id="0ff00-128">`/IAcceptSQLServerLicenseTerms` は、自動インストールのために `/q` パラメーターまたは `/qs` パラメーターを指定する場合に必要です。</span><span class="sxs-lookup"><span data-stu-id="0ff00-128">The `/IAcceptSQLServerLicenseTerms` is required when the `/q` or `/qs` parameter is specified for un-attended installations.</span></span>  
  
     <span data-ttu-id="0ff00-129">`/action` パラメーターは、インストールを実行するようにセットアップに命令します。</span><span class="sxs-lookup"><span data-stu-id="0ff00-129">The `/action` parameter instructs Setup to perform an installation.</span></span>  
  
     <span data-ttu-id="0ff00-130">`/role` パラメーターは、PowerPivot for SharePoint に必要な Analysis Services のプログラム ファイルと構成ファイルをインストールするようにセットアップに命令します。</span><span class="sxs-lookup"><span data-stu-id="0ff00-130">The `/role` parameter instructs Setup to install the Analysis Services program and configuration files required for PowerPivot for SharePoint.</span></span> <span data-ttu-id="0ff00-131">また、既存のファーム接続情報を検出し、それを使用して SharePoint 構成データベースにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="0ff00-131">This role also detects and uses the existing farm connectivity information to access the SharePoint configuration database.</span></span> <span data-ttu-id="0ff00-132">このパラメーターは必須です。</span><span class="sxs-lookup"><span data-stu-id="0ff00-132">This parameter is required.</span></span> <span data-ttu-id="0ff00-133">`/features` パラメーターの代わりにこのパラメーターを使用して、インストールするコンポーネントを指定します。</span><span class="sxs-lookup"><span data-stu-id="0ff00-133">Use it instead of the `/features` parameter to specify the components to install.</span></span>  
  
     <span data-ttu-id="0ff00-134">`/instancename` パラメーターは、名前付きインスタンスとして 'PowerPivot' を指定します。</span><span class="sxs-lookup"><span data-stu-id="0ff00-134">The `/instancename` parameter specifies 'PowerPivot' as a named instance.</span></span> <span data-ttu-id="0ff00-135">この値はハードコードされていて変更できません。</span><span class="sxs-lookup"><span data-stu-id="0ff00-135">This value is hard-coded and cannot be changed.</span></span> <span data-ttu-id="0ff00-136">ここでは、サービスのインストール方法を示すために指定されています。</span><span class="sxs-lookup"><span data-stu-id="0ff00-136">It is specified in the command for educational purposes so that you know how the service is installed.</span></span>  
  
     <span data-ttu-id="0ff00-137">`/indicateprogress` パラメーターは、コマンド プロンプト ウィンドウで進行状況を監視できるようにします。</span><span class="sxs-lookup"><span data-stu-id="0ff00-137">The `/indicateprogress` parameter allows you to monitor progress in the command prompt window.</span></span>  
  
2.  <span data-ttu-id="0ff00-138">ここでは、`PID` パラメーターが省略されているため、Evaluation Edition がインストールされます。</span><span class="sxs-lookup"><span data-stu-id="0ff00-138">The `PID` parameter is omitted from the command, which causes the Evaluation edition to be installed.</span></span> <span data-ttu-id="0ff00-139">Enterprise Edition をインストールする場合は、セットアップ コマンドに PID を追加して、有効なプロダクト キーを指定します。</span><span class="sxs-lookup"><span data-stu-id="0ff00-139">If you want to install the Enterprise edition, add the PID to your Setup command and provide a valid product key.</span></span>  
  
    ```  
    /PID=<product key for an Enterprise installation>  
    ```  
  
3.  <span data-ttu-id="0ff00-140">とのプレースホルダーを \<domain\username> 、 \<StrongPassword> 有効なユーザーアカウントとパスワードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="0ff00-140">Replace the placeholders for \<domain\username> and \<StrongPassword>with valid user accounts and passwords.</span></span>  
  
     <span data-ttu-id="0ff00-141">`/assvaccount`および **/assvcpassword**パラメーターは、アプリケーションサーバーでインスタンスを構成するために使用され [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="0ff00-141">The `/assvaccount` and **/assvcpassword** parameters are used to configure the [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)] instance on the application server.</span></span> <span data-ttu-id="0ff00-142">これらのプレースホルダーを有効なアカウント情報に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="0ff00-142">Replace these placeholders with valid account information.</span></span>  
  
     <span data-ttu-id="0ff00-143">**/Assysadminaccounts**パラメーターは、SQL Server セットアップを実行しているユーザーの id に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0ff00-143">The **/assysadminaccounts** parameter must be set to the identity of the user who is running SQL Server Setup.</span></span> <span data-ttu-id="0ff00-144">システム管理者を少なくとも 1 人指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0ff00-144">You must specify at least one system administrator.</span></span> <span data-ttu-id="0ff00-145">SQL Server セットアップでは、あらかじめ登録された Administrators グループのメンバーに対して sysadmin 権限が自動的に付与されなくなったことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="0ff00-145">Note that SQL Server Setup no long grants automatic sysadmin permissions to members of the built-in Administrators group.</span></span>  
  
4.  <span data-ttu-id="0ff00-146">改行を削除します。</span><span class="sxs-lookup"><span data-stu-id="0ff00-146">Remove line breaks.</span></span>  
  
5.  <span data-ttu-id="0ff00-147">コマンド全体を選択し、[編集] メニューの [**コピー** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0ff00-147">Select the entire command and then click **Copy** on the Edit menu.</span></span>  
  
6.  <span data-ttu-id="0ff00-148">管理者のコマンド プロンプトを開きます。</span><span class="sxs-lookup"><span data-stu-id="0ff00-148">Open an administrator command prompt.</span></span> <span data-ttu-id="0ff00-149">これを行うには、[**スタート**] ボタンをクリックし、コマンドプロンプトを右クリックして、[**管理者として実行**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="0ff00-149">To do this, click **Start**, right-click the command prompt, and select **Run as administrator**.</span></span>  
  
7.  <span data-ttu-id="0ff00-150">SQL Server のインストール メディアを含むドライブまたは共有フォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="0ff00-150">Navigate to the drive or shared folder that contains the SQL Server installation media.</span></span>  
  
8.  <span data-ttu-id="0ff00-151">編集済みのコマンドをコマンド ラインに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="0ff00-151">Paste the revised command into the command line.</span></span> <span data-ttu-id="0ff00-152">これを行うには、コマンドプロンプトウィンドウの左上隅にあるアイコンをクリックし、[**編集**] をポイントして、[**貼り付け**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0ff00-152">To do this, click the icon in the top left corner of the command prompt window, point to **Edit**, and then click **Paste**.</span></span>  
  
9. <span data-ttu-id="0ff00-153">**Enter**キーを押してコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="0ff00-153">Press **Enter** to run the command.</span></span> <span data-ttu-id="0ff00-154">セットアップが完了するまで待ちます。</span><span class="sxs-lookup"><span data-stu-id="0ff00-154">Wait for setup to complete.</span></span> <span data-ttu-id="0ff00-155">コマンド プロンプト ウィンドウでセットアップの進行状況を監視できます。</span><span class="sxs-lookup"><span data-stu-id="0ff00-155">You can monitor Setup's progress in the command prompt window.</span></span>  
  
10. <span data-ttu-id="0ff00-156">インストールを確認するには、\Program Files\SQL Server\120\Setup Bootstrap\Log にある summary.txt ファイルを調べます。</span><span class="sxs-lookup"><span data-stu-id="0ff00-156">To verify installation, check the summary.txt file at \Program Files\SQL Server\120\Setup Bootstrap\Log.</span></span> <span data-ttu-id="0ff00-157">サーバーがエラーなしでインストールされていれば、最終結果が "Passed" になっています。</span><span class="sxs-lookup"><span data-stu-id="0ff00-157">Final result should say "Passed" if the server installed without errors.</span></span>  
  
11. <span data-ttu-id="0ff00-158">サーバーを構成します。</span><span class="sxs-lookup"><span data-stu-id="0ff00-158">Configure the server.</span></span> <span data-ttu-id="0ff00-159">少なくとも、ソリューションを配置し、サービス アプリケーションを作成して、各サイト コレクションで PowerPivot 機能を有効化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0ff00-159">At a minimum, you must deploy solutions, create a service application, and enable the feature for each site collection.</span></span> <span data-ttu-id="0ff00-160">詳細については、「サーバーの全体管理で PowerPivot 構成ツール&#41;または[Powerpivot サーバーの管理と構成](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/power-pivot-server-administration-and-configuration-in-central-administration)を[&#40;2010 PowerPivot for SharePoint の構成または修復](../../../2014/analysis-services/configure-repair-powerpivot-sharepoint-2010.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0ff00-160">For more information, see [Configure or Repair PowerPivot for SharePoint 2010 &#40;PowerPivot Configuration Tool&#41;](../../../2014/analysis-services/configure-repair-powerpivot-sharepoint-2010.md) or [PowerPivot Server Administration and Configuration in Central Administration](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/power-pivot-server-administration-and-configuration-in-central-administration).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ff00-161">参照</span><span class="sxs-lookup"><span data-stu-id="0ff00-161">See Also</span></span>  
 <span data-ttu-id="0ff00-162">[PowerPivot サービスアカウントの構成](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/configure-power-pivot-service-accounts) </span><span class="sxs-lookup"><span data-stu-id="0ff00-162">[Configure PowerPivot Service Accounts](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/configure-power-pivot-service-accounts) </span></span>  
 [<span data-ttu-id="0ff00-163">PowerPivot for SharePoint 2010 のインストール</span><span class="sxs-lookup"><span data-stu-id="0ff00-163">PowerPivot for SharePoint 2010 Installation</span></span>](../../../2014/sql-server/install/powerpivot-for-sharepoint-2010-installation.md)  
