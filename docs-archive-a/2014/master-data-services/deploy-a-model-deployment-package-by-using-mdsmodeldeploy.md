---
title: MDSModelDeploy を使用したモデルの配置パッケージの配置 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: fb2a4df4-5e0d-4b34-818f-383dbde1b15c
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: c23dcc592c2de34fa87703c8ba58d949dfec455c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642844"
---
# <a name="deploy-a-model-deployment-package-by-using-mdsmodeldeploy"></a><span data-ttu-id="670c6-102">MDSModelDeploy を使用したモデルの配置パッケージの配置</span><span class="sxs-lookup"><span data-stu-id="670c6-102">Deploy a Model Deployment Package by Using MDSModelDeploy</span></span>
  <span data-ttu-id="670c6-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]では、MDSModelDeploy ツールを使用して、次のどちらかを含むパッケージを配置します。</span><span class="sxs-lookup"><span data-stu-id="670c6-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], use the MDSModelDeploy tool to deploy a package that contains either:</span></span>  
  
-   <span data-ttu-id="670c6-104">モデル オブジェクトのみ。</span><span class="sxs-lookup"><span data-stu-id="670c6-104">Model objects only.</span></span>  
  
-   <span data-ttu-id="670c6-105">モデル オブジェクトとデータ。</span><span class="sxs-lookup"><span data-stu-id="670c6-105">Model objects and data.</span></span>  
  
 <span data-ttu-id="670c6-106">モデル オブジェクトのみを含むパッケージを配置する必要がある場合は、代わりに、 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Web アプリケーションのモデル配置ウィザードを使用できます。</span><span class="sxs-lookup"><span data-stu-id="670c6-106">If you want to deploy a package that contains model objects only, you can use the model deployment wizard in the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] web application instead.</span></span> <span data-ttu-id="670c6-107">詳細については、「 [ウィザードを使用したモデルの配置パッケージの展開](../../2014/master-data-services/deploy-a-model-deployment-package-by-using-the-wizard.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="670c6-107">For more information, see [Deploy a Model Deployment Package by Using the Wizard](../../2014/master-data-services/deploy-a-model-deployment-package-by-using-the-wizard.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="670c6-108">パッケージは、そのパッケージが作成されたエディションの [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] にのみ配置できます。</span><span class="sxs-lookup"><span data-stu-id="670c6-108">Packages can be deployed to the edition of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] they were created in only.</span></span> <span data-ttu-id="670c6-109">つまり、 [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] で作成されたパッケージを [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] 以降に配置することはできません。</span><span class="sxs-lookup"><span data-stu-id="670c6-109">This means that packages created in [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] cannot be deployed to [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] or higher.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="670c6-110">前提条件</span><span class="sxs-lookup"><span data-stu-id="670c6-110">Prerequisites</span></span>  
 <span data-ttu-id="670c6-111">この手順を実行するには</span><span class="sxs-lookup"><span data-stu-id="670c6-111">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="670c6-112">ターゲット **環境の** [システム管理] [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 機能領域にアクセスする権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="670c6-112">You must have permission to access the **System Administration** functional area in the target [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] environment.</span></span>  
  
-   <span data-ttu-id="670c6-113">モデルの配置パッケージが必要です。</span><span class="sxs-lookup"><span data-stu-id="670c6-113">A model deployment package must exist.</span></span> <span data-ttu-id="670c6-114">詳細については、「  [MDSModelDeploy を使用したモデルの配置パッケージの作成](../../2014/master-data-services/create-a-model-deployment-package-by-using-mdsmodeldeploy.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="670c6-114">For more information, see  [Create a Model Deployment Package by Using MDSModelDeploy](../../2014/master-data-services/create-a-model-deployment-package-by-using-mdsmodeldeploy.md).</span></span>  
  
-   <span data-ttu-id="670c6-115">モデルを配置する環境の管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="670c6-115">You must be an administrator in the environment where you are deploying the model.</span></span> <span data-ttu-id="670c6-116">詳細については、「[管理者 &#40;マスターデータサービス&#41;](administrators-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="670c6-116">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="670c6-117">データを使用してモデルを更新する場合、配置先のバージョンを**ロック**または**コミット**することはできません。</span><span class="sxs-lookup"><span data-stu-id="670c6-117">If you are updating a model with data, the version you're deploying to cannot be **Locked** or **Committed**.</span></span>  
  
### <a name="to-deploy-a-model-deployment-package"></a><span data-ttu-id="670c6-118">モデルの配置パッケージを配置するには</span><span class="sxs-lookup"><span data-stu-id="670c6-118">To deploy a model deployment package</span></span>  
  
1.  <span data-ttu-id="670c6-119">新しいモデルを配置するのか、モデルを複製するのか、以前に複製したモデルを更新するのかを決定します。</span><span class="sxs-lookup"><span data-stu-id="670c6-119">Determine whether you are deploying a new model, a clone of a model, or updating a previously-cloned model.</span></span> <span data-ttu-id="670c6-120">詳細については、「[モデル配置オプション (マスター データ サービス)](../../2014/master-data-services/model-deployment-options-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="670c6-120">For more information, see [Model Deployment Options &#40;Master Data Services&#41;](../../2014/master-data-services/model-deployment-options-master-data-services.md).</span></span>  
  
2.  <span data-ttu-id="670c6-121">コマンド プロンプトを開き、MDSModelDeploy.exe のある場所に移動します。</span><span class="sxs-lookup"><span data-stu-id="670c6-121">Open a command prompt and navigate to MDSModelDeploy.exe.</span></span>  
  
    -   <span data-ttu-id="670c6-122">MDS が既定の場所にインストールされている場合、このツールは*ドライブ*:、または、マスターデータ Services\Configuration\MDSModelDeploy.exe</span><span class="sxs-lookup"><span data-stu-id="670c6-122">If MDS is installed at the default location, the tool is available at *drive*:\Program Files\Microsoft SQL Server\120\Master Data Services\Configuration\MDSModelDeploy.exe</span></span>  
  
    -   <span data-ttu-id="670c6-123">MDS を既定の場所にインストールしなかった場合は、ローカル コンピューター内で MDSModelDeploy.exe を検索します。</span><span class="sxs-lookup"><span data-stu-id="670c6-123">If MDS is not installed at the default location, search the local computer for MDSModelDeploy.exe.</span></span>  
  
3.  <span data-ttu-id="670c6-124">省略可能。</span><span class="sxs-lookup"><span data-stu-id="670c6-124">Optional.</span></span> <span data-ttu-id="670c6-125">オプションおよびヘルプを表示します。</span><span class="sxs-lookup"><span data-stu-id="670c6-125">View options and help.</span></span>  
  
    -   <span data-ttu-id="670c6-126">使用可能なすべてのオプションを表示するには、「 `MDSModelDeploy` 」と入力し、Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="670c6-126">To display all available options, type `MDSModelDeploy` and press Enter.</span></span>  
  
    -   <span data-ttu-id="670c6-127">オプションのヘルプを表示するには、「 *」と入力します。* OptionName `MDSModelDeploy help OptionName`はオプションの名前です。</span><span class="sxs-lookup"><span data-stu-id="670c6-127">To display help for an option, type the following, where *OptionName* is the name of the option: `MDSModelDeploy help OptionName`.</span></span>  
  
4.  <span data-ttu-id="670c6-128">省略可能。</span><span class="sxs-lookup"><span data-stu-id="670c6-128">Optional.</span></span> <span data-ttu-id="670c6-129">Web アプリケーションが複数ある場合、次のコマンドを入力し、Enter キーを押して、配置するサービスの名前を確認します。</span><span class="sxs-lookup"><span data-stu-id="670c6-129">If you have multiple web applications, determine the name of the service you will deploy to by typing this command and pressing Enter:</span></span>  
  
    ```  
    MDSModelDeploy listservices  
    ```  
  
     <span data-ttu-id="670c6-130">値の一覧が返されます (例: `MDS1, Default Web Site, MDS`)。</span><span class="sxs-lookup"><span data-stu-id="670c6-130">A list of values is returned, for example `MDS1, Default Web Site, MDS`.</span></span> <span data-ttu-id="670c6-131">モデルを配置するには、この一覧の最初の値 (この例では、 `MDS1`) が必要です。</span><span class="sxs-lookup"><span data-stu-id="670c6-131">The first value in this list (in this case, `MDS1`) is needed to deploy the model.</span></span>  
  
5.  <span data-ttu-id="670c6-132">モデルを配置するのか、モデルを複製するのか、以前に複製したモデルを更新するのかに応じて、コマンド プロンプトに次のコマンドを入力し、Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="670c6-132">Depending on whether you are creating a model, cloning a model, or updating a model, at the command prompt, type the following and press Enter.</span></span>  
  
    -   <span data-ttu-id="670c6-133">新しいモデルを作成するには</span><span class="sxs-lookup"><span data-stu-id="670c6-133">To create a new model:</span></span>  
  
        ```  
        MDSModelDeploy deploynew -package PackageName -model ModelName -service ServiceName  
        ```  
  
    -   <span data-ttu-id="670c6-134">モデルの複製を作成するには</span><span class="sxs-lookup"><span data-stu-id="670c6-134">To create a clone of a model:</span></span>  
  
        ```  
        MDSModelDeploy deployclone -package PackageName  
        ```  
  
    -   <span data-ttu-id="670c6-135">既存のモデルとそのデータを更新するには</span><span class="sxs-lookup"><span data-stu-id="670c6-135">To update an existing model and its data:</span></span>  
  
        ```  
        MDSModelDeploy deployupdate -package PackageName -version VersionName  
        ```  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="670c6-136">MDSModelDeploy ツールを使用して既存のモデルとそのデータを更新するときに、配置先モデルに存在するエンティティ、属性、またはメンバーがパッケージに含まれていない場合は、MDSModelDeploy によって、そのエンティティ、属性、またはメンバーがモデルから削除されることはありません。</span><span class="sxs-lookup"><span data-stu-id="670c6-136">If you use the MDSModelDeploy tool to update an existing model and its data, and the package does not contain an entity, attribute, or member that exists in the destination model, MDSModelDeploy will not delete that entity, attribute, or member from the model.</span></span>  
  
     <span data-ttu-id="670c6-137">*PackageName* はパッケージ (.pkg) ファイルの名前、 *ModelName* は新しいモデルの名前、 *VersionName* はバージョンの名前、 *ServiceName* は前の手順で返されたサービスの名前です。</span><span class="sxs-lookup"><span data-stu-id="670c6-137">Where *PackageName* is the name of the package (.pkg) file, *ModelName* is the name of the new model, *VersionName* is the name of the version, and *ServiceName* is the name of the service that you returned in the previous step.</span></span> <span data-ttu-id="670c6-138">モデル名とバージョン名は大文字と小文字の違いも含めて正確に指定してください。</span><span class="sxs-lookup"><span data-stu-id="670c6-138">Ensure that the model and version names match the exact case-sensitive names.</span></span>  
  
6.  <span data-ttu-id="670c6-139">パッケージが正常に配置されると、"MDSModelDeploy 操作は正常に完了しました" というメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="670c6-139">When the package is successfully deployed, a message stating "MDSModelDeploy operation completed successfully" is displayed.</span></span>  
  
 <span data-ttu-id="670c6-140">**注:**</span><span class="sxs-lookup"><span data-stu-id="670c6-140">**Notes:**</span></span>  
  
-   <span data-ttu-id="670c6-141">パッケージ内のサブスクリプションビューの名前が、既存のモデル内のサブスクリプションビューと同じである場合、ビューは modelname として作成され*ます。 subscriptionviewname*です。</span><span class="sxs-lookup"><span data-stu-id="670c6-141">If a subscription view in the package has the same name as a subscription view in an existing model, the view is created as *modelname.subscriptionviewname*.</span></span> <span data-ttu-id="670c6-142">この名前が既に使用されている場合、サブスクリプション ビューは作成されません。</span><span class="sxs-lookup"><span data-stu-id="670c6-142">If this name is already in use, the subscription view is not created.</span></span>  
  
-   <span data-ttu-id="670c6-143">配置プロセスには、次の 4 つの手順があります。</span><span class="sxs-lookup"><span data-stu-id="670c6-143">The deployment process has four steps:</span></span>  
  
    1.  <span data-ttu-id="670c6-144">モデル オブジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="670c6-144">The model objects are created.</span></span>  
  
    2.  <span data-ttu-id="670c6-145">ビジネス ルールが作成されます。</span><span class="sxs-lookup"><span data-stu-id="670c6-145">Business rules are created.</span></span>  
  
    3.  <span data-ttu-id="670c6-146">サブスクリプション ビューが作成されます。</span><span class="sxs-lookup"><span data-stu-id="670c6-146">Subscription views are created.</span></span>  
  
    4.  <span data-ttu-id="670c6-147">マスター データが設定されます。</span><span class="sxs-lookup"><span data-stu-id="670c6-147">Master data is populated.</span></span>  
  
-   <span data-ttu-id="670c6-148">新しいモデルまたは複製モデルを作成する場合、いずれかの手順の実行中にプロセスが失敗すると、モデルは削除されます。</span><span class="sxs-lookup"><span data-stu-id="670c6-148">When creating a new or cloned model, if the process fails during any step, the model is deleted.</span></span>  
  
     <span data-ttu-id="670c6-149">モデルを更新する場合、最初の 3 つの手順の実行中にプロセスが失敗すると、そのプロセスは続行されません。ただし、既に行われた変更はロールバックされません。</span><span class="sxs-lookup"><span data-stu-id="670c6-149">When updating a model, if the process fails during the first three steps, it does not proceed; however, changes that are already made are not rolled back.</span></span> <span data-ttu-id="670c6-150">手順 4. でプロセスが失敗すると、更新可能なメンバーが更新されます。</span><span class="sxs-lookup"><span data-stu-id="670c6-150">If the process fails in step 4, members that can be updated are updated.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="670c6-151">次の手順</span><span class="sxs-lookup"><span data-stu-id="670c6-151">Next Steps</span></span>  
 <span data-ttu-id="670c6-152">ユーザー定義メタデータ、ファイル属性、ユーザーおよびグループの権限はモデル配置パッケージに含まれていません。</span><span class="sxs-lookup"><span data-stu-id="670c6-152">User-defined metadata, file attributes, and user and group permissions are not included in model deployment packages.</span></span> <span data-ttu-id="670c6-153">モデルを配置した後、これらを手動で更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="670c6-153">After you deploy a model, you must update these manually.</span></span> <span data-ttu-id="670c6-154">詳細については、次を参照してください。</span><span class="sxs-lookup"><span data-stu-id="670c6-154">For more information, see:</span></span>  
  
-   [<span data-ttu-id="670c6-155">メタデータの追加 &#40;マスターデータサービス&#41;</span><span class="sxs-lookup"><span data-stu-id="670c6-155">Add Metadata &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/add-metadata-master-data-services.md)  
  
-   [<span data-ttu-id="670c6-156">モデル オブジェクト権限を割り当てる (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="670c6-156">Assign Model Object Permissions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/assign-model-object-permissions-master-data-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="670c6-157">参照</span><span class="sxs-lookup"><span data-stu-id="670c6-157">See Also</span></span>  
 [<span data-ttu-id="670c6-158">モデルの配置 (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="670c6-158">Deploying Models &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/deploying-models-master-data-services.md)  
  
  
