---
title: Integration Services プロジェクト変換ウィザード |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.migrationwizard.f1
ms.assetid: a192b094-4d0f-4c21-b911-460ec844a49f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c47dc8ed1d0485a62128be732cc34de1dca35740
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641135"
---
# <a name="integration-services-project-conversion-wizard"></a><span data-ttu-id="3dda5-102">Integration Services プロジェクト変換ウィザード</span><span class="sxs-lookup"><span data-stu-id="3dda5-102">Integration Services Project Conversion Wizard</span></span>
  <span data-ttu-id="3dda5-103">**Integration Services プロジェクト変換ウィザード** で、プロジェクトをプロジェクト配置モデルに変換します。</span><span class="sxs-lookup"><span data-stu-id="3dda5-103">The **Integration Services Project Conversion Wizard** converts a project to the project deployment model.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3dda5-104">プロジェクトに含まれている 1 つ以上のデータ ソースは、プロジェクトの変換が完了すると削除されます。</span><span class="sxs-lookup"><span data-stu-id="3dda5-104">If the project contains one or more datasources, the datasources are removed when the project conversion is completed.</span></span> <span data-ttu-id="3dda5-105">プロジェクト内のパッケージで共有可能なデータ ソースへの接続を作成するには、プロジェクト レベルで接続マネージャーを追加します。</span><span class="sxs-lookup"><span data-stu-id="3dda5-105">To create a connection to a data source that can be shared by the packages in the project, add a connection manager at the project level.</span></span> <span data-ttu-id="3dda5-106">詳細については、「 [パッケージでの接続マネージャーの追加、削除、または共有](../../2014/integration-services/add-delete-or-share-a-connection-manager-in-a-package.md)」 を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3dda5-106">For more information, see [Add, Delete, or Share a Connection Manager in a Package](../../2014/integration-services/add-delete-or-share-a-connection-manager-in-a-package.md).</span></span>  
  
 <span data-ttu-id="3dda5-107">**目的に合ったトピックをクリックしてください**</span><span class="sxs-lookup"><span data-stu-id="3dda5-107">**What do you want to do?**</span></span>  
  
-   [<span data-ttu-id="3dda5-108">Integration Services プロジェクト変換ウィザードを開く</span><span class="sxs-lookup"><span data-stu-id="3dda5-108">Open the Integration Services Project Conversion Wizard</span></span>](#open_dialog)  
  
-   <span data-ttu-id="3dda5-109">[[パッケージの場所の指定] ページのオプションの設定](#locate)</span><span class="sxs-lookup"><span data-stu-id="3dda5-109">[Set Options on the Locate Packages Page](#locate)</span></span>  
  
-   <span data-ttu-id="3dda5-110">[[パッケージの選択] ページのオプションの設定](#selectPackages)</span><span class="sxs-lookup"><span data-stu-id="3dda5-110">[Set Options on the Select Packages Page](#selectPackages)</span></span>  
  
-   <span data-ttu-id="3dda5-111">[[配置先の選択] ページのオプションの設定](#destination)</span><span class="sxs-lookup"><span data-stu-id="3dda5-111">[Set Options on the Select Destination Page](#destination)</span></span>  
  
-   <span data-ttu-id="3dda5-112">[[プロジェクト プロパティの指定] ページのオプションの設定](#projectProperties)</span><span class="sxs-lookup"><span data-stu-id="3dda5-112">[Set Options on the Specify Project Properties Page](#projectProperties)</span></span>  
  
-   <span data-ttu-id="3dda5-113">[[パッケージ実行タスクの更新] ページのオプションの設定](#executePackage)</span><span class="sxs-lookup"><span data-stu-id="3dda5-113">[Set Options on the Update Execute Package Task Page](#executePackage)</span></span>  
  
-   <span data-ttu-id="3dda5-114">[[構成の選択] ページのオプションの設定](#configurations)</span><span class="sxs-lookup"><span data-stu-id="3dda5-114">[Set Options on the Select Configurations Page](#configurations)</span></span>  
  
-   <span data-ttu-id="3dda5-115">[[パラメーターの作成] ページのオプションの設定](#createParameters)</span><span class="sxs-lookup"><span data-stu-id="3dda5-115">[Set Options on the Create Parameters Page](#createParameters)</span></span>  
  
-   <span data-ttu-id="3dda5-116">[[パラメーターの構成] ページのオプションの設定](#configureParameters)</span><span class="sxs-lookup"><span data-stu-id="3dda5-116">[Set Options on the Configure Parameters Page](#configureParameters)</span></span>  
  
-   <span data-ttu-id="3dda5-117">[[確認] ページのオプションの設定](#review)</span><span class="sxs-lookup"><span data-stu-id="3dda5-117">[Set the Options on the Review page](#review)</span></span>  
  
-   <span data-ttu-id="3dda5-118">[[変換の実行] のオプションの設定](#conversion)</span><span class="sxs-lookup"><span data-stu-id="3dda5-118">[Set the Options on the Perform Conversion](#conversion)</span></span>  
  
##  <a name="open-the-integration-services-project-conversion-wizard"></a><a name="open_dialog"></a><span data-ttu-id="3dda5-119">Integration Services プロジェクト変換ウィザードを開く</span><span class="sxs-lookup"><span data-stu-id="3dda5-119">Open the Integration Services Project Conversion Wizard</span></span>  
 <span data-ttu-id="3dda5-120">**Integration Services プロジェクト変換** ウィザードを開くには、次のいずれかの操作を行います。</span><span class="sxs-lookup"><span data-stu-id="3dda5-120">Do one of the following to open the **Integration Services Project Conversion** Wizard.</span></span>  
  
-   <span data-ttu-id="3dda5-121">[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]でプロジェクトを開き、ソリューション エクスプローラーでプロジェクトを右クリックし、 **[プロジェクト配置モデルに変換]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3dda5-121">Open the project in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], and then in Solution Explorer, right-click the project and click **Convert to Project Deployment Model**.</span></span>  
  
-   <span data-ttu-id="3dda5-122">オブジェクト エクスプローラーの [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]で、 **[プロジェクト]** ノードを右クリックし、 **[パッケージのインポート]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="3dda5-122">From Object Explorer in [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], right-click the **Projects** node and select **Import Packages**.</span></span>  
  
 <span data-ttu-id="3dda5-123">**Integration Services プロジェクト変換ウィザード** を [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] または [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]のいずれから実行するかによって、ウィザードが実行する変換タスクは異なります。</span><span class="sxs-lookup"><span data-stu-id="3dda5-123">Depending on whether you run the **Integration Services Project Conversion Wizard** from [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] or from [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], the wizard performs different conversion tasks.</span></span> <span data-ttu-id="3dda5-124">詳細については、「 [Integration Services サーバーへのプロジェクトの配置](../../2014/integration-services/deploy-projects-to-integration-services-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3dda5-124">For more information, see [Deploy Projects to Integration Services Server](../../2014/integration-services/deploy-projects-to-integration-services-server.md).</span></span>  
  
##  <a name="set-options-on-the-locate-packages-page"></a><a name="locate"></a><span data-ttu-id="3dda5-125">[パッケージの検索] ページのオプションの設定</span><span class="sxs-lookup"><span data-stu-id="3dda5-125">Set Options on the Locate Packages Page</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3dda5-126">**[パッケージの場所の指定]** ページは、ウィザードを [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]から実行した場合にのみ使用可能です。</span><span class="sxs-lookup"><span data-stu-id="3dda5-126">The **Locate Packages** page is available only when you run the wizard from [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)].</span></span>  
  
 <span data-ttu-id="3dda5-127">**[ソース]** ボックスの一覧の **[ファイル システム]** を選択すると、次のオプションがページに表示されます。</span><span class="sxs-lookup"><span data-stu-id="3dda5-127">The following option displays on the page when you select **File system** in the **Source** drop-down list.</span></span> <span data-ttu-id="3dda5-128">パッケージがファイル システムに存在する場合は、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="3dda5-128">Select this option when the package is resides in the file system.</span></span>  
  
 <span data-ttu-id="3dda5-129">**フォルダー**</span><span class="sxs-lookup"><span data-stu-id="3dda5-129">**Folder**</span></span>  
 <span data-ttu-id="3dda5-130">パッケージのパスを入力するか、 **[参照]** をクリックしてパッケージに移動します。</span><span class="sxs-lookup"><span data-stu-id="3dda5-130">Type the package path, or navigate to the package by clicking **Browse**.</span></span>  
  
 <span data-ttu-id="3dda5-131">**[ソース]** ボックスの一覧の **[SSIS パッケージ ストア]** を選択すると、次のオプションがページに表示されます。</span><span class="sxs-lookup"><span data-stu-id="3dda5-131">The following options display on the page when you select **SSIS Package Store** in the **Source** drop-down list.</span></span> <span data-ttu-id="3dda5-132">パッケージ ストアの詳細については、「[パッケージの管理 &#40;SSIS サービス&#41;](service/package-management-ssis-service.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3dda5-132">For more information about the package store, see [Package Management &#40;SSIS Service&#41;](service/package-management-ssis-service.md).</span></span>  
  
 <span data-ttu-id="3dda5-133">**[サーバー]**</span><span class="sxs-lookup"><span data-stu-id="3dda5-133">**Server**</span></span>  
 <span data-ttu-id="3dda5-134">サーバー名を入力するか、またはサーバーを選択します。</span><span class="sxs-lookup"><span data-stu-id="3dda5-134">Type the server name or select the server.</span></span>  
  
 <span data-ttu-id="3dda5-135">**フォルダー**</span><span class="sxs-lookup"><span data-stu-id="3dda5-135">**Folder**</span></span>  
 <span data-ttu-id="3dda5-136">パッケージのパスを入力するか、 **[参照]** をクリックしてパッケージに移動します。</span><span class="sxs-lookup"><span data-stu-id="3dda5-136">Type the package path, or navigate to the package by clicking **Browse**.</span></span>  
  
 <span data-ttu-id="3dda5-137">**[ソース]** ボックスの一覧の **[Microsoft SQL Server]** を選択すると、次のオプションがページに表示されます。</span><span class="sxs-lookup"><span data-stu-id="3dda5-137">The following options display on the page when you select **Microsoft SQL Server** in the **Source** drop-down list.</span></span> <span data-ttu-id="3dda5-138">パッケージが Microsoft [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]に存在する場合は、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="3dda5-138">Select this option when the package resides in Microsoft [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="3dda5-139">**[サーバー]**</span><span class="sxs-lookup"><span data-stu-id="3dda5-139">**Server**</span></span>  
 <span data-ttu-id="3dda5-140">サーバー名を入力するか、またはサーバーを選択します。</span><span class="sxs-lookup"><span data-stu-id="3dda5-140">Type the server name or select the server.</span></span>  
  
 <span data-ttu-id="3dda5-141">**Windows 認証を使用する**</span><span class="sxs-lookup"><span data-stu-id="3dda5-141">**Use Windows authentication**</span></span>  
 <span data-ttu-id="3dda5-142">Microsoft Windows 認証モードを使用すると、ユーザーは Windows ユーザー アカウントを使用して接続できます。</span><span class="sxs-lookup"><span data-stu-id="3dda5-142">Microsoft Windows Authentication mode allows a user to connect through a Windows user account.</span></span> <span data-ttu-id="3dda5-143">Windows 認証を使用すると、ユーザー名とパスワードを入力する必要がなくなります。</span><span class="sxs-lookup"><span data-stu-id="3dda5-143">If you use Windows Authentication, you do not need to provide a user name or password.</span></span>  
  
 <span data-ttu-id="3dda5-144">**SQL Server 認証を使用する**</span><span class="sxs-lookup"><span data-stu-id="3dda5-144">**Use SQL Server authentication**</span></span>  
 <span data-ttu-id="3dda5-145">指定されたログイン名とパスワードを使用して、信頼関係の低い接続から接続した場合、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] は [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ログイン アカウントが設定されているかどうか、指定されたパスワードが以前に記録されたパスワードと一致しているかどうかを確認することで接続の認証を行います。</span><span class="sxs-lookup"><span data-stu-id="3dda5-145">When a user connects with a specified login name and password from a non-trusted connection, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] authenticates the connection by checking to see if a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] login account has been set up and if the specified password matches the one previously recorded.</span></span> <span data-ttu-id="3dda5-146">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] にログイン アカウントが設定されていない場合、認証は失敗し、エラー メッセージが返されます。</span><span class="sxs-lookup"><span data-stu-id="3dda5-146">If [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] does not have a login account set, authentication fails, and the user receives an error message.</span></span>  
  
 <span data-ttu-id="3dda5-147">**ユーザー名**</span><span class="sxs-lookup"><span data-stu-id="3dda5-147">**User name**</span></span>  
 <span data-ttu-id="3dda5-148">SQL Server 認証を使用する場合に、ユーザー名を指定します。</span><span class="sxs-lookup"><span data-stu-id="3dda5-148">Specify a user name when you are using SQL Server Authentication.</span></span>  
  
 <span data-ttu-id="3dda5-149">**パスワード**</span><span class="sxs-lookup"><span data-stu-id="3dda5-149">**Password**</span></span>  
 <span data-ttu-id="3dda5-150">SQL Server 認証を使用する場合に、パスワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="3dda5-150">Provide the password when you are using SQL Server Authentication.</span></span>  
  
 <span data-ttu-id="3dda5-151">**フォルダー**</span><span class="sxs-lookup"><span data-stu-id="3dda5-151">**Folder**</span></span>  
 <span data-ttu-id="3dda5-152">パッケージのパスを入力するか、 **[参照]** をクリックしてパッケージに移動します。</span><span class="sxs-lookup"><span data-stu-id="3dda5-152">Type the package path, or navigate to the package by clicking **Browse**.</span></span>  
  
##  <a name="set-options-on-the-select-packages-page"></a><a name="selectPackages"></a><span data-ttu-id="3dda5-153">[パッケージの選択] ページのオプションの設定</span><span class="sxs-lookup"><span data-stu-id="3dda5-153">Set Options on the Select Packages Page</span></span>  
 <span data-ttu-id="3dda5-154">**パッケージ名**</span><span class="sxs-lookup"><span data-stu-id="3dda5-154">**Package Name**</span></span>  
 <span data-ttu-id="3dda5-155">パッケージ ファイルを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="3dda5-155">Lists the package file.</span></span>  
  
 <span data-ttu-id="3dda5-156">**状態**</span><span class="sxs-lookup"><span data-stu-id="3dda5-156">**Status**</span></span>  
 <span data-ttu-id="3dda5-157">パッケージをパッケージ配置モデルに変換する準備ができているかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="3dda5-157">Indicates whether a package is ready to convert to the project deployment model.</span></span>  
  
 <span data-ttu-id="3dda5-158">**Message**</span><span class="sxs-lookup"><span data-stu-id="3dda5-158">**Message**</span></span>  
 <span data-ttu-id="3dda5-159">パッケージに関連付けられているメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="3dda5-159">Displays a message associated with the package.</span></span>  
  
 <span data-ttu-id="3dda5-160">**パスワード**</span><span class="sxs-lookup"><span data-stu-id="3dda5-160">**Password**</span></span>  
 <span data-ttu-id="3dda5-161">パッケージに関連付けられているパスワードが表示されます。</span><span class="sxs-lookup"><span data-stu-id="3dda5-161">Displays a password associated with the package.</span></span> <span data-ttu-id="3dda5-162">パスワードのテキストは表示されません。</span><span class="sxs-lookup"><span data-stu-id="3dda5-162">The password text is hidden.</span></span>  
  
 <span data-ttu-id="3dda5-163">**[選択項目に適用]**</span><span class="sxs-lookup"><span data-stu-id="3dda5-163">**Apply to selection**</span></span>  
 <span data-ttu-id="3dda5-164">クリックすると、 **[パスワード]** ボックスのパスワードが選択したパッケージに適用されます。</span><span class="sxs-lookup"><span data-stu-id="3dda5-164">Click to apply the password in the **Password** text box, to the selected package or packages.</span></span>  
  
 <span data-ttu-id="3dda5-165">**[更新]**</span><span class="sxs-lookup"><span data-stu-id="3dda5-165">**Refresh**</span></span>  
 <span data-ttu-id="3dda5-166">パッケージの一覧を更新します。</span><span class="sxs-lookup"><span data-stu-id="3dda5-166">Refreshes the list of packages.</span></span>  
  
##  <a name="set-options-on-the-select-destination-page"></a><a name="destination"></a><span data-ttu-id="3dda5-167">[変換先の選択] ページのオプションの設定</span><span class="sxs-lookup"><span data-stu-id="3dda5-167">Set Options on the Select Destination Page</span></span>  
 <span data-ttu-id="3dda5-168">このページで、新規プロジェクト配置ファイル (.ispac) の名前とパスを指定するか、既存のファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="3dda5-168">On this page, specify the name and path for a new project deployment file (.ispac) or select an existing file.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3dda5-169">**[配置先の選択]** ページは、ウィザードを [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]から実行した場合にのみ使用可能です。</span><span class="sxs-lookup"><span data-stu-id="3dda5-169">The **Select Destination** page is available only when you run the wizard from [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)].</span></span>  
  
 <span data-ttu-id="3dda5-170">**出力パス**</span><span class="sxs-lookup"><span data-stu-id="3dda5-170">**Output path**</span></span>  
 <span data-ttu-id="3dda5-171">配置ファイルのパスを入力するか、 **[参照]** をクリックしてファイルに移動します。</span><span class="sxs-lookup"><span data-stu-id="3dda5-171">Type the path for the deployment file or navigate to the file by clicking **Browse**.</span></span>  
  
 <span data-ttu-id="3dda5-172">**プロジェクト名**</span><span class="sxs-lookup"><span data-stu-id="3dda5-172">**Project name**</span></span>  
 <span data-ttu-id="3dda5-173">プロジェクト名を入力します。</span><span class="sxs-lookup"><span data-stu-id="3dda5-173">Type the project name.</span></span>  
  
 <span data-ttu-id="3dda5-174">**保護レベル**</span><span class="sxs-lookup"><span data-stu-id="3dda5-174">**Protection level**</span></span>  
 <span data-ttu-id="3dda5-175">保護レベルを選択します。</span><span class="sxs-lookup"><span data-stu-id="3dda5-175">Select the protection level.</span></span> <span data-ttu-id="3dda5-176">詳しくは、「 [Access Control for Sensitive Data in Packages](security/access-control-for-sensitive-data-in-packages.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="3dda5-176">For more information, see [Access Control for Sensitive Data in Packages](security/access-control-for-sensitive-data-in-packages.md).</span></span>  
  
 <span data-ttu-id="3dda5-177">**プロジェクトの説明**</span><span class="sxs-lookup"><span data-stu-id="3dda5-177">**Project description**</span></span>  
 <span data-ttu-id="3dda5-178">プロジェクトの説明を入力します (省略可)。</span><span class="sxs-lookup"><span data-stu-id="3dda5-178">Type an optional description for the project.</span></span>  
  
##  <a name="set-options-on-the-specify-project-properties-page"></a><a name="projectProperties"></a><span data-ttu-id="3dda5-179">[プロジェクトのプロパティの指定] ページのオプションの設定</span><span class="sxs-lookup"><span data-stu-id="3dda5-179">Set Options on the Specify Project Properties Page</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3dda5-180">**[プロジェクト プロパティの指定]** ページは、ウィザードを [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]から実行した場合にのみ使用可能です。</span><span class="sxs-lookup"><span data-stu-id="3dda5-180">The **Specify Project Properties** page is available only when you run the wizard from [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].</span></span>  
  
 <span data-ttu-id="3dda5-181">**プロジェクト名**</span><span class="sxs-lookup"><span data-stu-id="3dda5-181">**Project name**</span></span>  
 <span data-ttu-id="3dda5-182">プロジェクト名を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="3dda5-182">Lists the project name.</span></span>  
  
 <span data-ttu-id="3dda5-183">**保護レベル**</span><span class="sxs-lookup"><span data-stu-id="3dda5-183">**Protection level**</span></span>  
 <span data-ttu-id="3dda5-184">プロジェクトに含まれるパッケージの保護レベルを選択します。</span><span class="sxs-lookup"><span data-stu-id="3dda5-184">Select a protection level for the packages contained in the project.</span></span> <span data-ttu-id="3dda5-185">保護レベルの詳細については、「 [パッケージ内の機微なデータへのアクセス制御](security/access-control-for-sensitive-data-in-packages.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3dda5-185">For more information about protection levels, see [Access Control for Sensitive Data in Packages](security/access-control-for-sensitive-data-in-packages.md).</span></span>  
  
 <span data-ttu-id="3dda5-186">**プロジェクトの説明**</span><span class="sxs-lookup"><span data-stu-id="3dda5-186">**Project description**</span></span>  
 <span data-ttu-id="3dda5-187">プロジェクトの説明 (省略可能) を入力します。</span><span class="sxs-lookup"><span data-stu-id="3dda5-187">Type an optional project description.</span></span>  
  
##  <a name="set-options-on-the-update-execute-package-task-page"></a><a name="executePackage"></a><span data-ttu-id="3dda5-188">[パッケージ実行タスクの更新] ページのオプションの設定</span><span class="sxs-lookup"><span data-stu-id="3dda5-188">Set Options on the Update Execute Package Task Page</span></span>  
 <span data-ttu-id="3dda5-189">プロジェクト ベースの参照を使用するには、パッケージに含まれているパッケージ実行タスクを更新します。</span><span class="sxs-lookup"><span data-stu-id="3dda5-189">Update Execute Package Tasks contain in the packages, to use a project-based reference.</span></span> <span data-ttu-id="3dda5-190">詳細については、「 [パッケージ実行タスク エディター](../../2014/integration-services/execute-package-task-editor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3dda5-190">For more information, see [Execute Package Task Editor](../../2014/integration-services/execute-package-task-editor.md).</span></span>  
  
 <span data-ttu-id="3dda5-191">**[親パッケージ]**</span><span class="sxs-lookup"><span data-stu-id="3dda5-191">**Parent Package**</span></span>  
 <span data-ttu-id="3dda5-192">パッケージ実行タスクを使用して子パッケージを実行するパッケージの名前を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="3dda5-192">Lists the name of the package that executes the child package using the Execute Package task.</span></span>  
  
 <span data-ttu-id="3dda5-193">**タスク名**</span><span class="sxs-lookup"><span data-stu-id="3dda5-193">**Task name**</span></span>  
 <span data-ttu-id="3dda5-194">パッケージ実行タスクの名前を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="3dda5-194">Lists the name of the Execute Package task.</span></span>  
  
 <span data-ttu-id="3dda5-195">**[元の参照]**</span><span class="sxs-lookup"><span data-stu-id="3dda5-195">**Original reference**</span></span>  
 <span data-ttu-id="3dda5-196">子パッケージの現在のパスを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="3dda5-196">Lists the current path of the child package.</span></span>  
  
 <span data-ttu-id="3dda5-197">**[参照の割り当て]**</span><span class="sxs-lookup"><span data-stu-id="3dda5-197">**Assign reference**</span></span>  
 <span data-ttu-id="3dda5-198">プロジェクトに格納されている子パッケージを選択します。</span><span class="sxs-lookup"><span data-stu-id="3dda5-198">Select a child package stored in the project.</span></span>  
  
##  <a name="set-options-on-the-select-configurations-page"></a><a name="configurations"></a><span data-ttu-id="3dda5-199">[構成の選択] ページのオプションの設定</span><span class="sxs-lookup"><span data-stu-id="3dda5-199">Set Options on the Select Configurations Page</span></span>  
 <span data-ttu-id="3dda5-200">パラメーターで置き換えるパッケージ構成を選択します。</span><span class="sxs-lookup"><span data-stu-id="3dda5-200">Select the package configurations that you want to replace with parameters.</span></span>  
  
 <span data-ttu-id="3dda5-201">**Package**</span><span class="sxs-lookup"><span data-stu-id="3dda5-201">**Package**</span></span>  
 <span data-ttu-id="3dda5-202">パッケージ ファイルを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="3dda5-202">Lists the package file.</span></span>  
  
 <span data-ttu-id="3dda5-203">**Type**</span><span class="sxs-lookup"><span data-stu-id="3dda5-203">**Type**</span></span>  
 <span data-ttu-id="3dda5-204">XML 構成ファイルなど、構成の種類を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="3dda5-204">Lists the type of configuration, such as an XML configuration file.</span></span>  
  
 <span data-ttu-id="3dda5-205">**[構成文字列]**</span><span class="sxs-lookup"><span data-stu-id="3dda5-205">**Configuration String**</span></span>  
 <span data-ttu-id="3dda5-206">構成ファイルのパスを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="3dda5-206">Lists the path of the configuration file.</span></span>  
  
 <span data-ttu-id="3dda5-207">**状態**</span><span class="sxs-lookup"><span data-stu-id="3dda5-207">**Status**</span></span>  
 <span data-ttu-id="3dda5-208">構成の状態メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="3dda5-208">Displays a status message for the configuration.</span></span> <span data-ttu-id="3dda5-209">メッセージ テキスト全体を表示するには、メッセージをクリックします。</span><span class="sxs-lookup"><span data-stu-id="3dda5-209">Click the message to view the entire message text.</span></span>  
  
 <span data-ttu-id="3dda5-210">**[構成の追加]**</span><span class="sxs-lookup"><span data-stu-id="3dda5-210">**Add Configurations**</span></span>  
 <span data-ttu-id="3dda5-211">他のプロジェクトに含まれているパッケージ構成を、パラメーターで置き換える (使用可能な) 構成の一覧に追加します。</span><span class="sxs-lookup"><span data-stu-id="3dda5-211">Add package configurations contained in other projects to the list of available configurations that you want to replace with parameters.</span></span> <span data-ttu-id="3dda5-212">ファイル システムまたは SQL Server に格納された構成を選択できます。</span><span class="sxs-lookup"><span data-stu-id="3dda5-212">You can select configurations stored in a file system or stored in SQL Server.</span></span>  
  
 <span data-ttu-id="3dda5-213">**[更新]**</span><span class="sxs-lookup"><span data-stu-id="3dda5-213">**Refresh**</span></span>  
 <span data-ttu-id="3dda5-214">構成の一覧を更新する場合にクリックします。</span><span class="sxs-lookup"><span data-stu-id="3dda5-214">Click to refresh the list of configurations.</span></span>  
  
 <span data-ttu-id="3dda5-215">**[変換後にすべてのパッケージから構成を削除する]**</span><span class="sxs-lookup"><span data-stu-id="3dda5-215">**Remove configurations from all packages after conversion**</span></span>  
 <span data-ttu-id="3dda5-216">このオプションを選択して、プロジェクトからすべての構成を削除することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="3dda5-216">It is recommended that you remove all configurations from the project by selecting this option.</span></span>  
  
 <span data-ttu-id="3dda5-217">このオプションを選択しない場合は、パラメーターで置き換えるために選択した構成のみが削除されます。</span><span class="sxs-lookup"><span data-stu-id="3dda5-217">If you don't select this option, only the configurations that you selected to replace with parameters are removed.</span></span>  
  
##  <a name="set-options-on-the-create-parameters-page"></a><a name="createParameters"></a><span data-ttu-id="3dda5-218">[パラメーターの作成] ページのオプションの設定</span><span class="sxs-lookup"><span data-stu-id="3dda5-218">Set Options on the Create Parameters Page</span></span>  
 <span data-ttu-id="3dda5-219">各構成プロパティのパラメーター名とスコープを選択します。</span><span class="sxs-lookup"><span data-stu-id="3dda5-219">Select the parameter name and scope for each configuration property.</span></span>  
  
 <span data-ttu-id="3dda5-220">**Package**</span><span class="sxs-lookup"><span data-stu-id="3dda5-220">**Package**</span></span>  
 <span data-ttu-id="3dda5-221">パッケージ ファイルを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="3dda5-221">Lists the package file.</span></span>  
  
 <span data-ttu-id="3dda5-222">**パラメーター名**</span><span class="sxs-lookup"><span data-stu-id="3dda5-222">**Parameter Name**</span></span>  
 <span data-ttu-id="3dda5-223">パラメーター名を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="3dda5-223">Lists the parameter name.</span></span>  
  
 <span data-ttu-id="3dda5-224">**スコープ**</span><span class="sxs-lookup"><span data-stu-id="3dda5-224">**Scope**</span></span>  
 <span data-ttu-id="3dda5-225">パラメーターのスコープ (パッケージまたはプロジェクト) を選択します。</span><span class="sxs-lookup"><span data-stu-id="3dda5-225">Select the scope of the parameter, either package or project.</span></span>  
  
##  <a name="set-options-on-the-configure-parameters-page"></a><a name="configureParameters"></a><span data-ttu-id="3dda5-226">[パラメーターの構成] ページのオプションの設定</span><span class="sxs-lookup"><span data-stu-id="3dda5-226">Set Options on the Configure Parameters Page</span></span>  
 <span data-ttu-id="3dda5-227">**名前**</span><span class="sxs-lookup"><span data-stu-id="3dda5-227">**Name**</span></span>  
 <span data-ttu-id="3dda5-228">パラメーター名を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="3dda5-228">Lists the parameter name.</span></span>  
  
 <span data-ttu-id="3dda5-229">**スコープ**</span><span class="sxs-lookup"><span data-stu-id="3dda5-229">**Scope**</span></span>  
 <span data-ttu-id="3dda5-230">パラメーターのスコープを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="3dda5-230">Lists the scope of the parameter.</span></span>  
  
 <span data-ttu-id="3dda5-231">**Value**</span><span class="sxs-lookup"><span data-stu-id="3dda5-231">**Value**</span></span>  
 <span data-ttu-id="3dda5-232">パラメーター値を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="3dda5-232">Lists the parameter value.</span></span>  
  
 <span data-ttu-id="3dda5-233">パラメーター プロパティを構成するには、値フィールドの横にある参照ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="3dda5-233">Click the ellipsis button next to the value field to configure the parameter properties.</span></span>  
  
 <span data-ttu-id="3dda5-234">**[パラメーターの詳細の設定]** ダイアログ ボックスで、パラメーター値を編集できます。</span><span class="sxs-lookup"><span data-stu-id="3dda5-234">In the **Set Parameter Details** dialog box, you can edit the parameter value.</span></span> <span data-ttu-id="3dda5-235">パッケージの実行時にパラメーター値を指定する必要があるかどうかを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="3dda5-235">You can also specify whether the parameter value must be provided when you run the package.</span></span>  
  
 <span data-ttu-id="3dda5-236">**の** [構成] **ダイアログ ボックスの** [パラメーター] [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]ページの値を変更するには、パラメーターの横にある参照ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="3dda5-236">You can modify value in the **Parameters** page of the **Configure** dialog box in [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], by clicking the browse button next to the parameter.</span></span> <span data-ttu-id="3dda5-237">**[パラメーター値の設定]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="3dda5-237">The **Set Parameter Value** dialog box appears.</span></span>  
  
 <span data-ttu-id="3dda5-238">また、 **[パラメーターの詳細の設定]** ダイアログ ボックスには、パラメーター値のデータ型や元のパラメーターが一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="3dda5-238">The **Set Parameter Details** dialog box also lists the data type of the parameter value and the origin of the parameter.</span></span>  
  
##  <a name="set-the-options-on-the-review-page"></a><a name="review"></a><span data-ttu-id="3dda5-239">[確認] ページのオプションの設定</span><span class="sxs-lookup"><span data-stu-id="3dda5-239">Set the Options on the Review page</span></span>  
 <span data-ttu-id="3dda5-240">プロジェクトの変換に関して選択したオプションを確認するには、**[確認]** ページを使用します。</span><span class="sxs-lookup"><span data-stu-id="3dda5-240">Use the **Review** page to confirm the options that you've selected for the conversion of the project.</span></span>  
  
 <span data-ttu-id="3dda5-241">**[戻る]**</span><span class="sxs-lookup"><span data-stu-id="3dda5-241">**Previous**</span></span>  
 <span data-ttu-id="3dda5-242">オプションを変更する場合にクリックします。</span><span class="sxs-lookup"><span data-stu-id="3dda5-242">Click to change an option.</span></span>  
  
 <span data-ttu-id="3dda5-243">**CONVERT**</span><span class="sxs-lookup"><span data-stu-id="3dda5-243">**Convert**</span></span>  
 <span data-ttu-id="3dda5-244">プロジェクトをプロジェクト配置モデルに変換する場合にクリックします。</span><span class="sxs-lookup"><span data-stu-id="3dda5-244">Click to convert the project to the project deployment model.</span></span>  
  
##  <a name="set-the-options-on-the-perform-conversion"></a><a name="conversion"></a><span data-ttu-id="3dda5-245">[変換の実行] のオプションの設定</span><span class="sxs-lookup"><span data-stu-id="3dda5-245">Set the Options on the Perform Conversion</span></span>  
 <span data-ttu-id="3dda5-246">[変換の実行] ページには、プロジェクトの変換の状態が表示されます。</span><span class="sxs-lookup"><span data-stu-id="3dda5-246">The Perform Conversion page shows status of the project conversion.</span></span>  
  
 <span data-ttu-id="3dda5-247">**操作**</span><span class="sxs-lookup"><span data-stu-id="3dda5-247">**Action**</span></span>  
 <span data-ttu-id="3dda5-248">特定の変換手順を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="3dda5-248">Lists a specific conversion step.</span></span>  
  
 <span data-ttu-id="3dda5-249">**結果**</span><span class="sxs-lookup"><span data-stu-id="3dda5-249">**Result**</span></span>  
 <span data-ttu-id="3dda5-250">各変換手順の状態を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="3dda5-250">Lists the status of each conversion step.</span></span> <span data-ttu-id="3dda5-251">状態メッセージをクリックすると、詳細が表示されます。</span><span class="sxs-lookup"><span data-stu-id="3dda5-251">Click the status message for more information.</span></span>  
  
 <span data-ttu-id="3dda5-252">プロジェクトの変換は、 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]でプロジェクトを保存しないと保存されません。</span><span class="sxs-lookup"><span data-stu-id="3dda5-252">The project conversion is not saved until the project is saved in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].</span></span>  
  
 <span data-ttu-id="3dda5-253">**レポートの保存**</span><span class="sxs-lookup"><span data-stu-id="3dda5-253">**Save report**</span></span>  
 <span data-ttu-id="3dda5-254">プロジェクトの変換の概要を .xml ファイルに保存する場合にクリックします。</span><span class="sxs-lookup"><span data-stu-id="3dda5-254">Click to save a summary of the project conversion in an .xml file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3dda5-255">参照</span><span class="sxs-lookup"><span data-stu-id="3dda5-255">See Also</span></span>  
 [<span data-ttu-id="3dda5-256">Integration Services サーバーへのプロジェクトの配置</span><span class="sxs-lookup"><span data-stu-id="3dda5-256">Deploy Projects to Integration Services Server</span></span>](../../2014/integration-services/deploy-projects-to-integration-services-server.md)  
  
  
