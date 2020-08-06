---
title: パッケージインストールウィザードの UI リファレンス |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.deploymentwizard.confirminstallation.f1
- sql12.dts.deploymentwizard.deploydtspackages.f1
- sql12.dts.deploymentwizard.selectinstfolder.f1
- sql12.dts.deploymentwizard.specifytargetsqlserver.f1
- sql12.dts.deploymentwizard.welcome.f1
- sql12.dts.deploymentwizard.finish.f1
- sql12.dts.deploymentwizard.configurepackages.f1
- sql12.dts.deploymentwizard.packagevalidation.f1
helpviewer_keywords:
- Package Installer Wizard
ms.assetid: 6fca44d9-5001-4644-bcf3-c2d10a674b97
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c15b423c66891e799f7f8dcd27682036dce6d8de
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713281"
---
# <a name="package-installation-wizard-ui-reference"></a><span data-ttu-id="673c4-102">パッケージ インストール ウィザードの UI リファレンス</span><span class="sxs-lookup"><span data-stu-id="673c4-102">Package Installation Wizard UI Reference</span></span>
  <span data-ttu-id="673c4-103">**パッケージ インストール ウィザード** を使用すると、プロジェクトに含まれるパッケージおよびその他のファイル、パッケージの従属ファイルを含む [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを配置できます。</span><span class="sxs-lookup"><span data-stu-id="673c4-103">Use the **Package Installation Wizard** to deploy a [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project, including the packages and miscellaneous files it contains and any package dependencies.</span></span>  
  
 <span data-ttu-id="673c4-104">パッケージを配置する前に、構成を作成してパッケージに配置できます。</span><span class="sxs-lookup"><span data-stu-id="673c4-104">Before you deploy packages, you can create configurations and then deploy them with the packages.</span></span> [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="673c4-105">は構成を使用して、パッケージのプロパティとパッケージ オブジェクトを実行時に動的に更新します。</span><span class="sxs-lookup"><span data-stu-id="673c4-105">uses configurations to dynamically update properties of packages and package objects at run time.</span></span> <span data-ttu-id="673c4-106">たとえば、接続文字列が含まれるプロパティに値をマップする構成を使用して、実行時に OLE DB 接続の接続文字列を動的に設定できます。</span><span class="sxs-lookup"><span data-stu-id="673c4-106">For example, the connection string of an OLE DB connection can be set dynamically at run time by providing a configuration that maps a value to the property that contains the connection string.</span></span>  
  
 <span data-ttu-id="673c4-107">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを構築して配置ユーティリティを作成するまでは、パッケージ インストール ウィザードは実行できません。</span><span class="sxs-lookup"><span data-stu-id="673c4-107">You cannot run the Package Installation Wizard until you build an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project and create a deployment utility.</span></span> <span data-ttu-id="673c4-108">詳細については、「 [配置ユーティリティを使用してパッケージを配置する](../../2014/integration-services/deploy-packages-by-using-the-deployment-utility.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="673c4-108">For more information, see [Deploy Packages by Using the Deployment Utility](../../2014/integration-services/deploy-packages-by-using-the-deployment-utility.md).</span></span>  
  
 <span data-ttu-id="673c4-109">ここでは、ウィザードの各ページについて説明します。</span><span class="sxs-lookup"><span data-stu-id="673c4-109">The following sections describe pages of the wizard.</span></span>  
  
## <a name="welcome-to-the-package-installation-wizard-page"></a><span data-ttu-id="673c4-110">[パッケージ インストール ウィザードへようこそ] ページ</span><span class="sxs-lookup"><span data-stu-id="673c4-110">Welcome to the Package Installation Wizard Page</span></span>  
 <span data-ttu-id="673c4-111">**パッケージ インストール ウィザード** を使用すると、パッケージ配置ユーティリティを作成する [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを配置できます。</span><span class="sxs-lookup"><span data-stu-id="673c4-111">Use the **Package Installation Wizard** to deploy an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project for which you built a package deployment utility.</span></span>  
  
 <span data-ttu-id="673c4-112">**[次回からこの開始ページを表示しない]**</span><span class="sxs-lookup"><span data-stu-id="673c4-112">**Do not show this starting page again**</span></span>  
 <span data-ttu-id="673c4-113">ウィザードを再度実行するときに開始ページをスキップします。</span><span class="sxs-lookup"><span data-stu-id="673c4-113">Select to skip the starting page when you run the wizard again.</span></span>  
  
 <span data-ttu-id="673c4-114">**Next**</span><span class="sxs-lookup"><span data-stu-id="673c4-114">**Next**</span></span>  
 <span data-ttu-id="673c4-115">ウィザードの次のページに進みます。</span><span class="sxs-lookup"><span data-stu-id="673c4-115">Go to the next page in the wizard.</span></span>  
  
 <span data-ttu-id="673c4-116">**[完了]**</span><span class="sxs-lookup"><span data-stu-id="673c4-116">**Finish**</span></span>  
 <span data-ttu-id="673c4-117">[パッケージ インストール ウィザードの完了] ページまでスキップします。</span><span class="sxs-lookup"><span data-stu-id="673c4-117">Skip to the Finish the Package Installation Wizard page.</span></span> <span data-ttu-id="673c4-118">ウィザードの前のページに戻って設定を変更する場合、必要なオプションの指定がすべて終わったらこのオプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="673c4-118">Use this option if you have backtracked through the wizard pages to revise your choices and have specified all of the required options.</span></span>  
  
## <a name="configure-packages-page"></a><span data-ttu-id="673c4-119">[パッケージの構成] ページ</span><span class="sxs-lookup"><span data-stu-id="673c4-119">Configure Packages Page</span></span>  
 <span data-ttu-id="673c4-120">**[パッケージの構成]** ページを使用すると、パッケージ構成を編集できます。</span><span class="sxs-lookup"><span data-stu-id="673c4-120">Use the **Configure Packages** page to edit package configurations.</span></span>  
  
### <a name="options"></a><span data-ttu-id="673c4-121">Options</span><span class="sxs-lookup"><span data-stu-id="673c4-121">Options</span></span>  
 <span data-ttu-id="673c4-122">**構成ファイル**</span><span class="sxs-lookup"><span data-stu-id="673c4-122">**Configuration file**</span></span>  
 <span data-ttu-id="673c4-123">一覧からファイルを選択して、構成ファイルの内容を編集します。</span><span class="sxs-lookup"><span data-stu-id="673c4-123">Edit the contents of a configuration file by selecting the file from the list.</span></span>  
  
 <span data-ttu-id="673c4-124">**関連トピック:** [パッケージ構成を作成する](../../2014/integration-services/create-package-configurations.md)</span><span class="sxs-lookup"><span data-stu-id="673c4-124">**Related Topics:** [Create Package Configurations](../../2014/integration-services/create-package-configurations.md)</span></span>  
  
 <span data-ttu-id="673c4-125">**パス**</span><span class="sxs-lookup"><span data-stu-id="673c4-125">**Path**</span></span>  
 <span data-ttu-id="673c4-126">構成するプロパティのパスを表示します。</span><span class="sxs-lookup"><span data-stu-id="673c4-126">View the path of the property to be configured.</span></span>  
  
 <span data-ttu-id="673c4-127">**Type**</span><span class="sxs-lookup"><span data-stu-id="673c4-127">**Type**</span></span>  
 <span data-ttu-id="673c4-128">プロパティのデータ型が表示されます。</span><span class="sxs-lookup"><span data-stu-id="673c4-128">View the data type of the property.</span></span>  
  
 <span data-ttu-id="673c4-129">**Value**</span><span class="sxs-lookup"><span data-stu-id="673c4-129">**Value**</span></span>  
 <span data-ttu-id="673c4-130">構成の値を指定します。</span><span class="sxs-lookup"><span data-stu-id="673c4-130">Specify the value of the configuration.</span></span>  
  
 <span data-ttu-id="673c4-131">**Next**</span><span class="sxs-lookup"><span data-stu-id="673c4-131">**Next**</span></span>  
 <span data-ttu-id="673c4-132">ウィザードの次のページに進みます。</span><span class="sxs-lookup"><span data-stu-id="673c4-132">Go to the next page in the wizard.</span></span>  
  
 <span data-ttu-id="673c4-133">**[完了]**</span><span class="sxs-lookup"><span data-stu-id="673c4-133">**Finish**</span></span>  
 <span data-ttu-id="673c4-134">[パッケージ インストール ウィザードの完了] ページまでスキップします。</span><span class="sxs-lookup"><span data-stu-id="673c4-134">Skip to the Finish the Package Installation Wizard page.</span></span> <span data-ttu-id="673c4-135">ウィザードの前のページに戻って設定を変更する場合、必要なオプションの指定がすべて終わったらこのオプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="673c4-135">Use this option if you have backtracked through the wizard pages to revise your choices and have specified all of the required options.</span></span>  
  
## <a name="confirm-installation-page"></a><span data-ttu-id="673c4-136">[インストールの確認] ページ</span><span class="sxs-lookup"><span data-stu-id="673c4-136">Confirm Installation Page</span></span>  
 <span data-ttu-id="673c4-137">**[インストールの確認]** ページを使用して、パッケージのインストールの開始、状態の表示、およびウィザードが指定されたプロジェクトからファイルをインストールするために使用する情報の表示を行います。</span><span class="sxs-lookup"><span data-stu-id="673c4-137">Use the **Confirm Installation** page to start the installation of packages, to view the status, and to view the information that the wizard will use to install files from the specified project.</span></span>  
  
 <span data-ttu-id="673c4-138">**Next**</span><span class="sxs-lookup"><span data-stu-id="673c4-138">**Next**</span></span>  
 <span data-ttu-id="673c4-139">パッケージとその依存関係をインストールし、インストールが完了したらウィザードの次のページへ移動します。</span><span class="sxs-lookup"><span data-stu-id="673c4-139">Install the packages and their dependencies and go to the next wizard page when installation is completed.</span></span>  
  
 <span data-ttu-id="673c4-140">**状態**</span><span class="sxs-lookup"><span data-stu-id="673c4-140">**Status**</span></span>  
 <span data-ttu-id="673c4-141">パッケージ インストールの進行状況を表示します。</span><span class="sxs-lookup"><span data-stu-id="673c4-141">Shows the progress of the package installation.</span></span>  
  
 <span data-ttu-id="673c4-142">**[完了]**</span><span class="sxs-lookup"><span data-stu-id="673c4-142">**Finish**</span></span>  
 <span data-ttu-id="673c4-143">[パッケージ インストール ウィザードの完了] ページに移動します。</span><span class="sxs-lookup"><span data-stu-id="673c4-143">Go to the Finish the Package Installation Wizard page.</span></span> <span data-ttu-id="673c4-144">ウィザード ページを戻って選択内容を変更し、必要なオプションをすべて指定した場合は、このオプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="673c4-144">Use this option if you have backtracked through the wizard pages to revise your choices and have specified all the required options.</span></span>  
  
## <a name="deploy-ssis-packages-page"></a><span data-ttu-id="673c4-145">[SSIS パッケージの配置] ページ</span><span class="sxs-lookup"><span data-stu-id="673c4-145">Deploy SSIS Packages Page</span></span>  
 <span data-ttu-id="673c4-146">**[SSIS パッケージの配置]** ページを使用して、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] パッケージとその従属ファイルをインストールする場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="673c4-146">Use the **Deploy SSIS Packages** page to specify where to install [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages and their dependencies.</span></span>  
  
### <a name="options"></a><span data-ttu-id="673c4-147">Options</span><span class="sxs-lookup"><span data-stu-id="673c4-147">Options</span></span>  
 <span data-ttu-id="673c4-148">**[ファイル システムに配置]**</span><span class="sxs-lookup"><span data-stu-id="673c4-148">**File system deployment**</span></span>  
 <span data-ttu-id="673c4-149">パッケージとその従属ファイルをファイル システム上の指定したフォルダーに配置します。</span><span class="sxs-lookup"><span data-stu-id="673c4-149">Deploy packages and dependencies in a specified folder in the file system.</span></span>  
  
 <span data-ttu-id="673c4-150">**[SQL Server に配置]**</span><span class="sxs-lookup"><span data-stu-id="673c4-150">**SQL Server deployment**</span></span>  
 <span data-ttu-id="673c4-151">パッケージとその従属ファイルを [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]のインスタンスに配置します。</span><span class="sxs-lookup"><span data-stu-id="673c4-151">Deploy packages and dependencies in an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="673c4-152">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] がサーバー間でパッケージを共有している場合に、このオプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="673c4-152">Use this option if [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] shares packages between servers.</span></span> <span data-ttu-id="673c4-153">パッケージの従属ファイルは、すべてファイル システムの指定フォルダーにインストールされます。</span><span class="sxs-lookup"><span data-stu-id="673c4-153">Any package dependencies are installed in the specified folder in the file system.</span></span>  
  
 <span data-ttu-id="673c4-154">**[インストール後にパッケージを検証する]**</span><span class="sxs-lookup"><span data-stu-id="673c4-154">**Validate packages after installation**</span></span>  
 <span data-ttu-id="673c4-155">インストール後にパッケージを検証するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="673c4-155">Indicate whether to validate packages after installation.</span></span>  
  
 <span data-ttu-id="673c4-156">**Next**</span><span class="sxs-lookup"><span data-stu-id="673c4-156">**Next**</span></span>  
 <span data-ttu-id="673c4-157">ウィザードの次のページに進みます。</span><span class="sxs-lookup"><span data-stu-id="673c4-157">Go to the next page in the wizard.</span></span>  
  
 <span data-ttu-id="673c4-158">**[完了]**</span><span class="sxs-lookup"><span data-stu-id="673c4-158">**Finish**</span></span>  
 <span data-ttu-id="673c4-159">[パッケージ インストール ウィザードの完了] ページまでスキップします。</span><span class="sxs-lookup"><span data-stu-id="673c4-159">Skip to the Finish the Package Installation Wizard page.</span></span> <span data-ttu-id="673c4-160">ウィザードの前のページに戻って設定を変更する場合、必要なオプションの指定がすべて終わったらこのオプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="673c4-160">Use this option if you have backtracked through the wizard pages to revise your choices and have specified all of the required options.</span></span>  
  
## <a name="packages-validation-page"></a><span data-ttu-id="673c4-161">[パッケージの検証] ページ</span><span class="sxs-lookup"><span data-stu-id="673c4-161">Packages Validation Page</span></span>  
 <span data-ttu-id="673c4-162">**[パッケージの検証]** ページを使用して、パッケージ検証の進行と結果を表示します。</span><span class="sxs-lookup"><span data-stu-id="673c4-162">Use the **Packages Validation** page to view the progress and results of the package validation.</span></span>  
  
 <span data-ttu-id="673c4-163">**Next**</span><span class="sxs-lookup"><span data-stu-id="673c4-163">**Next**</span></span>  
 <span data-ttu-id="673c4-164">ウィザードの次のページに進みます。</span><span class="sxs-lookup"><span data-stu-id="673c4-164">Go to the next page in the wizard.</span></span>  
  
## <a name="select-installation-folder-page"></a><span data-ttu-id="673c4-165">[インストール フォルダーの選択] ページ</span><span class="sxs-lookup"><span data-stu-id="673c4-165">Select Installation Folder Page</span></span>  
 <span data-ttu-id="673c4-166">**[インストール フォルダーの選択]** ページを使用して、パッケージとその従属ファイルをインストールするファイル システム フォルダーを指定します。</span><span class="sxs-lookup"><span data-stu-id="673c4-166">Use the **Select Installation Folder** page to specify the file system folder in which to install the packages and their dependencies.</span></span>  
  
### <a name="options"></a><span data-ttu-id="673c4-167">Options</span><span class="sxs-lookup"><span data-stu-id="673c4-167">Options</span></span>  
 <span data-ttu-id="673c4-168">**フォルダー**</span><span class="sxs-lookup"><span data-stu-id="673c4-168">**Folder**</span></span>  
 <span data-ttu-id="673c4-169">パッケージとその従属ファイルをコピーするパスとフォルダーを指定します。</span><span class="sxs-lookup"><span data-stu-id="673c4-169">Specify the path and folder in which to copy the package and its dependencies.</span></span>  
  
 <span data-ttu-id="673c4-170">**[参照]**</span><span class="sxs-lookup"><span data-stu-id="673c4-170">**Browse**</span></span>  
 <span data-ttu-id="673c4-171">**[フォルダーの参照]** ダイアログ ボックスを使用して、インストール先のフォルダーを参照します。</span><span class="sxs-lookup"><span data-stu-id="673c4-171">Browse to the target folder by using the **Browse For Folder** dialog box.</span></span>  
  
 <span data-ttu-id="673c4-172">**Next**</span><span class="sxs-lookup"><span data-stu-id="673c4-172">**Next**</span></span>  
 <span data-ttu-id="673c4-173">ウィザードの次のページに進みます。</span><span class="sxs-lookup"><span data-stu-id="673c4-173">Go to the next page in the wizard.</span></span>  
  
 <span data-ttu-id="673c4-174">**[完了]**</span><span class="sxs-lookup"><span data-stu-id="673c4-174">**Finish**</span></span>  
 <span data-ttu-id="673c4-175">[パッケージ インストール ウィザードの完了] ページまでスキップします。</span><span class="sxs-lookup"><span data-stu-id="673c4-175">Skip to the Finish the Package Installation Wizard page.</span></span> <span data-ttu-id="673c4-176">指定を変えるためにウィザードのページを戻った場合、必要なオプションをすべて指定したら、このオプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="673c4-176">Use this option if you have backtracked through the wizard pages to revise your choices and if have specified all of the required options.</span></span>  
  
## <a name="specify-target-sql-server-page"></a><span data-ttu-id="673c4-177">[インストール先の SQL Server の指定] ページ</span><span class="sxs-lookup"><span data-stu-id="673c4-177">Specify Target SQL Server Page</span></span>  
 <span data-ttu-id="673c4-178">**[インストール先の SQL Server の指定]** ページを使用して、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]のインスタンスへのパッケージ配置に関するオプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="673c4-178">Use the **Specify Target SQL Server** page to specify options for deploying the package to an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
### <a name="options"></a><span data-ttu-id="673c4-179">Options</span><span class="sxs-lookup"><span data-stu-id="673c4-179">Options</span></span>  
 <span data-ttu-id="673c4-180">**サーバー名**</span><span class="sxs-lookup"><span data-stu-id="673c4-180">**Server name**</span></span>  
 <span data-ttu-id="673c4-181">パッケージの配置先となるサーバーの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="673c4-181">Specify the name of the server to deploy the packages to.</span></span>  
  
 <span data-ttu-id="673c4-182">**[Windows 認証を使用する]**</span><span class="sxs-lookup"><span data-stu-id="673c4-182">**Use Windows Authentication**</span></span>  
 <span data-ttu-id="673c4-183">サーバーのログオンに Windows 認証を使用するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="673c4-183">Specify whether to use Windows Authentication to log on to the server.</span></span> <span data-ttu-id="673c4-184">より高いセキュリティのためには Windows 認証をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="673c4-184">Windows Authentication is recommended for better security.</span></span>  
  
 <span data-ttu-id="673c4-185">**[SQL Server 認証を使用する]**</span><span class="sxs-lookup"><span data-stu-id="673c4-185">**Use SQL Server Authentication**</span></span>  
 <span data-ttu-id="673c4-186">パッケージがサーバーのログオンに [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 認証を使用するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="673c4-186">Specify whether the package should use [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication to log on to the server.</span></span> <span data-ttu-id="673c4-187">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 認証を使用する場合は、ユーザー名とパスワードを入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="673c4-187">If you use [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication, you must provide a user name and password.</span></span>  
  
 <span data-ttu-id="673c4-188">**ユーザー名**</span><span class="sxs-lookup"><span data-stu-id="673c4-188">**User name**</span></span>  
 <span data-ttu-id="673c4-189">ユーザー名を指定します。</span><span class="sxs-lookup"><span data-stu-id="673c4-189">Specify a user name.</span></span>  
  
 <span data-ttu-id="673c4-190">**パスワード**</span><span class="sxs-lookup"><span data-stu-id="673c4-190">**Password**</span></span>  
 <span data-ttu-id="673c4-191">パスワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="673c4-191">Specify a password.</span></span>  
  
 <span data-ttu-id="673c4-192">**[パッケージのパス]**</span><span class="sxs-lookup"><span data-stu-id="673c4-192">**Package path**</span></span>  
 <span data-ttu-id="673c4-193">論理フォルダーの名前を指定するか、または既定フォルダーを使用する場合は「/」を入力します。</span><span class="sxs-lookup"><span data-stu-id="673c4-193">Specify the name of the logical folder, or enter "/" for the default folder.</span></span>  
  
 <span data-ttu-id="673c4-194">**[SSIS パッケージ]** ダイアログ ボックスでフォルダーを選択するには、参照ボタン ([...]) をクリックします。ただし、ダイアログ ボックスで既定フォルダーを選択することはできません。</span><span class="sxs-lookup"><span data-stu-id="673c4-194">To select the folder in the **SSIS Package** dialog box, click browse (...). However, the dialog box does not provide a means to select the default folder.</span></span> <span data-ttu-id="673c4-195">既定フォルダーを使用する場合は、テキスト ボックスに「/」を入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="673c4-195">If you want to use the default folder, you have to enter "/" in the text box.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="673c4-196">有効なパッケージ パスを入力しないと、"1 つ以上の引数が無効です。" というエラー メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="673c4-196">If you do not enter a valid package path, the following error message appears: "One or more arguments are invalid."</span></span>  
  
 <span data-ttu-id="673c4-197">**[暗号化をサーバー ストレージに依存する]**</span><span class="sxs-lookup"><span data-stu-id="673c4-197">**Rely on server storage for encryption**</span></span>  
 <span data-ttu-id="673c4-198">パッケージの安全を確保するために、 [!INCLUDE[ssDE](../includes/ssde-md.md)] のセキュリティ機能を使用する場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="673c4-198">Select to use security features of the [!INCLUDE[ssDE](../includes/ssde-md.md)] to help secure the packages.</span></span>  
  
 <span data-ttu-id="673c4-199">**Next**</span><span class="sxs-lookup"><span data-stu-id="673c4-199">**Next**</span></span>  
 <span data-ttu-id="673c4-200">ウィザードの次のページに進みます。</span><span class="sxs-lookup"><span data-stu-id="673c4-200">Go to the next page in the wizard.</span></span>  
  
 <span data-ttu-id="673c4-201">**[完了]**</span><span class="sxs-lookup"><span data-stu-id="673c4-201">**Finish**</span></span>  
 <span data-ttu-id="673c4-202">[パッケージ インストール ウィザードの完了] ページまでスキップします。</span><span class="sxs-lookup"><span data-stu-id="673c4-202">Skip to the Finish the Package Installation Wizard page.</span></span> <span data-ttu-id="673c4-203">ウィザードの前のページに戻って設定を変更する場合、必要なオプションの指定がすべて終わったらこのオプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="673c4-203">Use this option if you have backtracked through the wizard pages to revise your choices and have specified all of the required options.</span></span>  
  
## <a name="finish-the-package-installation-page"></a><span data-ttu-id="673c4-204">[パッケージ インストール ウィザードの完了] ページ</span><span class="sxs-lookup"><span data-stu-id="673c4-204">Finish the Package Installation Page</span></span>  
 <span data-ttu-id="673c4-205">**[パッケージ インストール ウィザードの完了]** ページを使用して、パッケージのインストール結果の要約を表示します。</span><span class="sxs-lookup"><span data-stu-id="673c4-205">Use the **Finish the Package Installation Wizard** page to view a summary of the package installation results.</span></span> <span data-ttu-id="673c4-206">このページでは、配置された [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトの名前、インストールされたパッケージ、構成ファイル、インストール場所などの詳細が表示されます。</span><span class="sxs-lookup"><span data-stu-id="673c4-206">This page provides details such as the name of the deployed [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project, the packages that were installed, the configuration files, and the installation location.</span></span>  
  
 <span data-ttu-id="673c4-207">**[完了]**</span><span class="sxs-lookup"><span data-stu-id="673c4-207">**Finish**</span></span>  
 <span data-ttu-id="673c4-208">**[完了]** をクリックすると、ウィザードが終了します。</span><span class="sxs-lookup"><span data-stu-id="673c4-208">Exit the wizard by clicking **Finish**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="673c4-209">参照</span><span class="sxs-lookup"><span data-stu-id="673c4-209">See Also</span></span>  
 [<span data-ttu-id="673c4-210">SSIS&#41;&#40;パッケージの配置</span><span class="sxs-lookup"><span data-stu-id="673c4-210">Package Deployment &#40;SSIS&#41;</span></span>](packages/legacy-package-deployment-ssis.md)  
  
  
