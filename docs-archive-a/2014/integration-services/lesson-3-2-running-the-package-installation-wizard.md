---
title: '手順 2: パッケージ インストール ウィザードの実行 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: f91fbb89-4626-4c47-b96d-56052dc45861
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9492f9ecc843ef475a3c5d32cde2952e0ff498fb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712170"
---
# <a name="step-2-running-the-package-installation-wizard"></a><span data-ttu-id="ab00a-102">手順 2:パッケージ インストール ウィザードの実行</span><span class="sxs-lookup"><span data-stu-id="ab00a-102">Step 2: Running the Package Installation Wizard</span></span>
  <span data-ttu-id="ab00a-103">この実習では、パッケージ インストール ウィザードを実行して、Deployment Tutorial プロジェクトから [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]のインスタンスにパッケージを配置します。</span><span class="sxs-lookup"><span data-stu-id="ab00a-103">In this task, you will run the Package Installation Wizard to deploy the packages from the Deployment Tutorial project to an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="ab00a-104">msdb [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] データベースの sysssispackages テーブルにインストールできるのはパッケージだけです。配置バンドルに含まれるサポート ファイルは、ファイル システムに配置されます。</span><span class="sxs-lookup"><span data-stu-id="ab00a-104">Only packages can be installed in the sysssispackages table in the msdb [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database, the supporting files that the deployment bundle includes will be deployed to the file system.</span></span>  
  
 <span data-ttu-id="ab00a-105">パッケージ インストール ウィザードを使用すると、手順に従ってパッケージのインストールと構成を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="ab00a-105">The Package Installation Wizard will guide you through the steps to install and configure the packages.</span></span> <span data-ttu-id="ab00a-106">配置先のコンピューター (配置バンドルをコピーするコンピューター) の [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインスタンスにパッケージをインストールします。</span><span class="sxs-lookup"><span data-stu-id="ab00a-106">You will install the packages to an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] on the destination computer (the computer to which you copied the deployment bundle.</span></span> <span data-ttu-id="ab00a-107">また、C:\DeploymentTutorialInstall フォルダーも作成します。このフォルダーには、パッケージ以外のファイルがインストールされます。</span><span class="sxs-lookup"><span data-stu-id="ab00a-107">You will also create a folder, C:\DeploymentTutorialInstall, in which the wizard will install the non-package files.</span></span>  
  
 <span data-ttu-id="ab00a-108">前のレッスンで、構成を使用するようにチュートリアルのパッケージを変更しました。</span><span class="sxs-lookup"><span data-stu-id="ab00a-108">In an earlier lesson, you modified the packages in the tutorial to use configurations.</span></span> <span data-ttu-id="ab00a-109">パッケージ インストール ウィザードを使用してこれらの構成を編集し、インストール先の環境でパッケージを正常に実行できるようにします。</span><span class="sxs-lookup"><span data-stu-id="ab00a-109">Using the Package Installation Wizard, you will edit these configurations to enable packages to run successfully in the installed-to environment.</span></span>  
  
### <a name="to-install-the-packages"></a><span data-ttu-id="ab00a-110">パッケージをインストールするには</span><span class="sxs-lookup"><span data-stu-id="ab00a-110">To install the packages</span></span>  
  
1.  <span data-ttu-id="ab00a-111">インストール先のコンピューターの配置バンドルを見つけます。</span><span class="sxs-lookup"><span data-stu-id="ab00a-111">On the destination computer, locate the deployment bundle.</span></span>  
  
     <span data-ttu-id="ab00a-112">配置ユーティリティの場所として既定値の bin\Deployment を使用した場合は、Deployment Tutorial プロジェクト内にある Deployment フォルダーが配置バンドルです。</span><span class="sxs-lookup"><span data-stu-id="ab00a-112">If you used the default value-bin\Deployment-as the location of the deployment utility, the deployment bundle is the Deployment folder in the Deployment Tutorial project.</span></span>  
  
2.  <span data-ttu-id="ab00a-113">Deployment フォルダーで、マニフェスト ファイルの Deployment Tutorial.SSISDeploymentManifest をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="ab00a-113">In the Deployment folder, double-click the manifest file, Deployment Tutorial.SSISDeploymentManifest.</span></span>  
  
3.  <span data-ttu-id="ab00a-114">パッケージ インストール ウィザードの初期画面で、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ab00a-114">On the Welcome page of the Package Installation Wizard, click **Next**.</span></span>  
  
4.  <span data-ttu-id="ab00a-115">[SSIS パッケージの配置] ページで、 **[SQL Server に配置]** オプションを選択し、 **[インストール後にパッケージを検証する]** チェック ボックスをオンにして、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ab00a-115">On the Deploy SSIS Packages page, select the **SQL Server deployment** option, select the **Validate packages after installation** check box, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="ab00a-116">[インストール先の SQL Server の指定] ページで、 **[サーバー名]** ボックスに **(local)** と指定します。</span><span class="sxs-lookup"><span data-stu-id="ab00a-116">On the Specify Target SQL Server page, specify **(local**), in the **Server name** box.</span></span>  
  
6.  <span data-ttu-id="ab00a-117">SQL Server のインスタンスが Windows 認証をサポートしている場合は、 **[Windows 認証を使用]** を選択します。サポートしていない場合は、 **[SQL Server 認証を使用]** を選択し、ユーザー名とパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="ab00a-117">If the instance of SQL Server supports Windows Authentication, select **Use Windows Authentication**; otherwise, select **Use SQL Server Authentication** and provide a user name and a password.</span></span>  
  
7.  <span data-ttu-id="ab00a-118">**[暗号化をサーバー ストレージに依存する]** チェック ボックスがオフになっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="ab00a-118">Verify that the **Rely on server storage for encryption** check box is cleared.</span></span>  
  
8.  <span data-ttu-id="ab00a-119">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ab00a-119">Click **Next.**</span></span>  
  
9. <span data-ttu-id="ab00a-120">[インストール フォルダーの選択] ページの **[参照]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ab00a-120">On the Select Installation Folder page, click **Browse.**</span></span>  
  
10. <span data-ttu-id="ab00a-121">**[フォルダーの参照]** ダイアログ ボックスで、 **[マイ コンピューター]** を展開し、 **[ローカル ディスク (C:)]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ab00a-121">In the **Browse For Folder** dialog box, expand **My Computer** and then click **Local Disk (C:)**.</span></span>  
  
11. <span data-ttu-id="ab00a-122">**[新しいフォルダーの作成]** をクリックし、新しいフォルダーの既定の名前 **[新しいフォルダー]** の代わりに「 **DeploymentTutorialInstall**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="ab00a-122">Click **Make New Folder** and replace the default name of the new folder, **New Folder**, with **DeploymentTutorialInstall**.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="ab00a-123">この名前は、構成が使用する環境変数の値で参照されます。</span><span class="sxs-lookup"><span data-stu-id="ab00a-123">This name is referenced in the value of the environment variables that configurations use.</span></span> <span data-ttu-id="ab00a-124">フォルダーと参照の名前が一致しなければ、パッケージを実行できません。</span><span class="sxs-lookup"><span data-stu-id="ab00a-124">The name of the folder and the reference must match or the package cannot run.</span></span>  
  
12. <span data-ttu-id="ab00a-125">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ab00a-125">Click **OK**.</span></span>  
  
13. <span data-ttu-id="ab00a-126">[インストール フォルダーの選択] ページで、[フォルダー] ボックスに **C:\DeploymentTutorialInstall** と表示されていることを確認し、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ab00a-126">On the Select Installation Folder page, verify that the Folder box contains **C:\DeploymentTutorialInstall** and then click **Next**.</span></span>  
  
14. <span data-ttu-id="ab00a-127">[インストールの確認] ページで、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ab00a-127">On the Confirm Installation page, click **Next**.</span></span>  
  
     <span data-ttu-id="ab00a-128">パッケージがインストールされます。</span><span class="sxs-lookup"><span data-stu-id="ab00a-128">The wizard installs the packages.</span></span> <span data-ttu-id="ab00a-129">インストールが完了すると、[パッケージの構成] ページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ab00a-129">After installation is completed, the Configure Packages page opens.</span></span>  
  
15. <span data-ttu-id="ab00a-130">[パッケージの構成] ページで、 **[構成ファイル]** ボックスに datatransferconfig.dtsconfig と loadxmldataconfig.dtsconfig が表示されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="ab00a-130">On the Configure Packages page, verify that the **Configuration file** box lists datatransferconfig.dtsconfig and loadxmldataconfig.dtsconfig.</span></span>  
  
16. <span data-ttu-id="ab00a-131">**[構成ファイル]** ボックスの一覧で、 **[datatransferconfig.dtsconfig]** をクリックし、 **[構成]** ボックスの **[パス]** 列のプロパティを展開して、 **[値]** 列を次の値で更新します。</span><span class="sxs-lookup"><span data-stu-id="ab00a-131">In the **Configuration file** list, click **datatransferconfig.dtsconfig**, expand Property in the **Path** column of the **Configurations** box, and update the **Value** column with the following values:</span></span>  
  
    |<span data-ttu-id="ab00a-132">プロパティ</span><span class="sxs-lookup"><span data-stu-id="ab00a-132">Property</span></span>|<span data-ttu-id="ab00a-133">値</span><span class="sxs-lookup"><span data-stu-id="ab00a-133">Value</span></span>|<span data-ttu-id="ab00a-134">更新後の値</span><span class="sxs-lookup"><span data-stu-id="ab00a-134">Updated Value</span></span>|  
    |--------------|-----------|-------------------|  
    |<span data-ttu-id="ab00a-135">\Package.Connections[Deployment Tutorial Log].Properties[ConnectionString]</span><span class="sxs-lookup"><span data-stu-id="ab00a-135">\Package.Connections[Deployment Tutorial Log].Properties[ConnectionString]</span></span>|<span data-ttu-id="ab00a-136">C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services\Tutorial\Deploying Packages\Completed Packages\Deployment Tutorial Log</span><span class="sxs-lookup"><span data-stu-id="ab00a-136">C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services\Tutorial\Deploying Packages\Completed Packages\Deployment Tutorial Log</span></span>|<span data-ttu-id="ab00a-137">C:\DeploymentTutorialInstall\Deployment Tutorial Log</span><span class="sxs-lookup"><span data-stu-id="ab00a-137">C:\DeploymentTutorialInstall\Deployment Tutorial Log</span></span>|  
    |<span data-ttu-id="ab00a-138">\Package.Connections[NewCustomers].Properties[ConnectionString]</span><span class="sxs-lookup"><span data-stu-id="ab00a-138">\Package.Connections[NewCustomers].Properties[ConnectionString]</span></span>|<span data-ttu-id="ab00a-139">C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services\Tutorial\Deploying Packages\Sample Data\NewCustomers.txt</span><span class="sxs-lookup"><span data-stu-id="ab00a-139">C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services\Tutorial\Deploying Packages\Sample Data\NewCustomers.txt</span></span>|<span data-ttu-id="ab00a-140">C:\DeploymentTutorialInstall\NewCustomers.txt</span><span class="sxs-lookup"><span data-stu-id="ab00a-140">C:\DeploymentTutorialInstall\NewCustomers.txt</span></span>|  
  
17. <span data-ttu-id="ab00a-141">**[構成ファイル]** ボックスの一覧で、[loadxmldataconfig.dtsconfig] をクリックし、 **[構成]** ボックスの **[パス]** 列のプロパティを展開して、 **[値]** 列を次の値で更新します。</span><span class="sxs-lookup"><span data-stu-id="ab00a-141">In the **Configuration file** list, click loadxmldataconfig.dtsconfig, expand Property in the **Path** column of the **Configurations** box, and update the **Value** column with the following values:</span></span>  
  
    |<span data-ttu-id="ab00a-142">プロパティ</span><span class="sxs-lookup"><span data-stu-id="ab00a-142">Property</span></span>|<span data-ttu-id="ab00a-143">値</span><span class="sxs-lookup"><span data-stu-id="ab00a-143">Value</span></span>|<span data-ttu-id="ab00a-144">更新後の値</span><span class="sxs-lookup"><span data-stu-id="ab00a-144">Updated Value</span></span>|  
    |--------------|-----------|-------------------|  
    |<span data-ttu-id="ab00a-145">\Package.LoadXMLData.Properties[[XML Source].[XMLData]]</span><span class="sxs-lookup"><span data-stu-id="ab00a-145">\Package.LoadXMLData.Properties[[XML Source].[XMLData]]</span></span>|<span data-ttu-id="ab00a-146">C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services\Tutorial\Deploying Packages\Sample Data\orders.xml</span><span class="sxs-lookup"><span data-stu-id="ab00a-146">C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services\Tutorial\Deploying Packages\Sample Data\orders.xml</span></span>|<span data-ttu-id="ab00a-147">C:\DeploymentTutorialInstall\orders.xml</span><span class="sxs-lookup"><span data-stu-id="ab00a-147">C:\DeploymentTutorialInstall\orders.xml</span></span>|  
    |<span data-ttu-id="ab00a-148">\Package.LoadXMLData.Properties[[XML Source].[XMLSchemaDefinition]]</span><span class="sxs-lookup"><span data-stu-id="ab00a-148">\Package.LoadXMLData.Properties[[XML Source].[XMLSchemaDefinition]]</span></span>|<span data-ttu-id="ab00a-149">C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services\Tutorial\Deploying Packages\Sample Data\orders.xsd</span><span class="sxs-lookup"><span data-stu-id="ab00a-149">C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services\Tutorial\Deploying Packages\Sample Data\orders.xsd</span></span>|<span data-ttu-id="ab00a-150">C:\DeploymentTutorialInstall\orders.xsd</span><span class="sxs-lookup"><span data-stu-id="ab00a-150">C:\DeploymentTutorialInstall\orders.xsd</span></span>|  
  
18. <span data-ttu-id="ab00a-151">[パッケージの検証] ページで、インストールされた各パッケージの検証結果を表示し、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ab00a-151">On the Package Validation page, view the validation results of each package installed and then click **Next**.</span></span>  
  
     <span data-ttu-id="ab00a-152">配置先コンピューターの環境変数の値は開発用コンピューターの環境変数の値と異なるため、[パッケージの検証] ページに複数の警告が表示されます。</span><span class="sxs-lookup"><span data-stu-id="ab00a-152">Because the values of the environment variables on the destination computer differ from the values of the environment variables on the development computer, several warnings appear on the Package Validation page.</span></span> <span data-ttu-id="ab00a-153">次の 4 つの警告が表示されます。</span><span class="sxs-lookup"><span data-stu-id="ab00a-153">You should expect four warnings:</span></span>  
  
    -   <span data-ttu-id="ab00a-154">構成ファイル : "C:\DeploymentTutorial\DataTransferConfig.dtsConfig" は有効ではありません。</span><span class="sxs-lookup"><span data-stu-id="ab00a-154">The configuration file: "C:\DeploymentTutorial\DataTransferConfig.dtsConfig" is not valid.</span></span> <span data-ttu-id="ab00a-155">構成ファイルの名前を確認してください。</span><span class="sxs-lookup"><span data-stu-id="ab00a-155">Check the configuration file name.</span></span>  
  
    -   <span data-ttu-id="ab00a-156">パッケージの少なくとも 1 つの構成エントリを読み込めませんでした。</span><span class="sxs-lookup"><span data-stu-id="ab00a-156">Failed to load at least one of the configuration entries in the package.</span></span> <span data-ttu-id="ab00a-157">構成エントリとそれ以前に発生した警告を確認して、読み込めなかった構成に関する説明を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ab00a-157">Check configuration entries and previous warnings to see description of which configuration failed.</span></span>  
  
    -   <span data-ttu-id="ab00a-158">構成ファイル : "C:\DeploymentTutorial\LoadXMLDataConfig.dtsConfig は有効ではありません。</span><span class="sxs-lookup"><span data-stu-id="ab00a-158">The configuration file: "C:\DeploymentTutorial\LoadXMLDataConfig.dtsConfig is not valid.</span></span> <span data-ttu-id="ab00a-159">構成ファイルの名前を確認してください。</span><span class="sxs-lookup"><span data-stu-id="ab00a-159">Check the configuration file name.</span></span>  
  
    -   <span data-ttu-id="ab00a-160">パッケージの少なくとも 1 つの構成エントリを読み込めませんでした。</span><span class="sxs-lookup"><span data-stu-id="ab00a-160">Failed to load at least one of the configuration entries in the package.</span></span> <span data-ttu-id="ab00a-161">構成エントリとそれ以前に発生した警告を確認して、読み込めなかった構成に関する説明を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ab00a-161">Check configuration entries and previous warnings to see description of which configuration failed.</span></span>  
  
     <span data-ttu-id="ab00a-162">これらの警告は、パッケージのインストールに影響しません。</span><span class="sxs-lookup"><span data-stu-id="ab00a-162">These warnings do not affect package installation.</span></span>  
  
     <span data-ttu-id="ab00a-163">[SSIS パッケージの配置] ページで **[インストール後にパッケージを検証する]** オプションを選択しなかった場合、[パッケージの検証] ページは表示されず、検証に関するインストール後の情報も表示されません。</span><span class="sxs-lookup"><span data-stu-id="ab00a-163">If you did not select the **Validate packages after installation** option on the Deploy SSIS Packages page, the Package Validation pages does not open and the wizard does not display post-installation information about validation.</span></span>  
  
19. <span data-ttu-id="ab00a-164">[パッケージ インストール ウィザードの完了] ページでインストールの概要を確認してから、 **[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ab00a-164">On the Finish the Package Installation Wizard page, read the installation summary and then click **Finish**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ab00a-165">パッケージの検証に使用する一時ログ ファイルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="ab00a-165">A temporary log file is created to use in the package validation.</span></span> <span data-ttu-id="ab00a-166">このファイルは、パッケージの実行時には使用されません。</span><span class="sxs-lookup"><span data-stu-id="ab00a-166">This file is not used when the package runs.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="ab00a-167">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="ab00a-167">Next Task in Lesson</span></span>  
 [<span data-ttu-id="ab00a-168">手順 3: 配置したパッケージのテスト</span><span class="sxs-lookup"><span data-stu-id="ab00a-168">Step 3: Testing the Deployed Packages</span></span>](../integration-services/lesson-3-3-testing-the-deployed-packages.md)  
  
<span data-ttu-id="ab00a-169">![Integration Services アイコン (小)](media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="ab00a-169">![Integration Services icon (small)](media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="ab00a-170">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ab00a-170">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="ab00a-171">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="ab00a-171">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="ab00a-172">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="ab00a-172">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab00a-173">参照</span><span class="sxs-lookup"><span data-stu-id="ab00a-173">See Also</span></span>  
 <span data-ttu-id="ab00a-174">[Integration Services サービス &#40;SSIS サービス&#41;](service/integration-services-service-ssis-service.md) </span><span class="sxs-lookup"><span data-stu-id="ab00a-174">[Integration Services Service &#40;SSIS Service&#41;](service/integration-services-service-ssis-service.md) </span></span>  
 [<span data-ttu-id="ab00a-175">Integration Services サービスを管理する</span><span class="sxs-lookup"><span data-stu-id="ab00a-175">Manage the Integration Services Service</span></span>](../../2014/integration-services/manage-the-integration-services-service.md)  
  
  
