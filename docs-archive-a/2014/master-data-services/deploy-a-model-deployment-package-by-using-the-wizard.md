---
title: ウィザードを使用したモデルの配置パッケージの展開 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- deployment packages [Master Data Services], deploying
- models [Master Data Services], deploying a package
ms.assetid: 4f65dc60-0ff8-46e6-9988-5bc5b9603ad0
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 75af9f7c12d866c6d9707f62c898aa7601f94800
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736456"
---
# <a name="deploy-a-model-deployment-package-by-using-the-wizard"></a><span data-ttu-id="ea0f5-102">ウィザードを使用したモデルの配置パッケージの展開</span><span class="sxs-lookup"><span data-stu-id="ea0f5-102">Deploy a Model Deployment Package by Using the Wizard</span></span>
  <span data-ttu-id="ea0f5-103">モデル オブジェクトのみが含まれているパッケージを配置するには、 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] のモデル配置ウィザードを使用します。</span><span class="sxs-lookup"><span data-stu-id="ea0f5-103">Use the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] model deployment wizard to deploy packages that contain model objects only.</span></span> <span data-ttu-id="ea0f5-104">データを含むパッケージを配置する必要がある場合は、「 [MDSModelDeploy を使用したモデルの配置パッケージの配置](../../2014/master-data-services/deploy-a-model-deployment-package-by-using-mdsmodeldeploy.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ea0f5-104">If you need to deploy a package with data, see [Deploy a Model Deployment Package by Using MDSModelDeploy](../../2014/master-data-services/deploy-a-model-deployment-package-by-using-mdsmodeldeploy.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="ea0f5-105">パッケージは、そのパッケージが作成されたエディションの [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] にのみ配置できます。</span><span class="sxs-lookup"><span data-stu-id="ea0f5-105">Packages can be deployed to the edition of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] they were created in only.</span></span> <span data-ttu-id="ea0f5-106">つまり、 [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] で作成されたパッケージを [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]に配置することはできません。</span><span class="sxs-lookup"><span data-stu-id="ea0f5-106">This means that packages created in [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] cannot be deployed to [!INCLUDE[ssSQL11](../includes/sssql11-md.md)].</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="ea0f5-107">前提条件</span><span class="sxs-lookup"><span data-stu-id="ea0f5-107">Prerequisites</span></span>  
 <span data-ttu-id="ea0f5-108">この手順を実行するには</span><span class="sxs-lookup"><span data-stu-id="ea0f5-108">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="ea0f5-109">ターゲット **環境の** [システム管理] [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 機能領域にアクセスする権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="ea0f5-109">You must have permission to access the **System Administration** functional area in the target [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] environment.</span></span>  
  
-   <span data-ttu-id="ea0f5-110">モデルの配置パッケージが必要です。</span><span class="sxs-lookup"><span data-stu-id="ea0f5-110">A model deployment package must exist.</span></span> <span data-ttu-id="ea0f5-111">詳細については、「 [ウィザードを使用したモデルの配置パッケージの作成](../../2014/master-data-services/create-a-model-deployment-package-by-using-the-wizard.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ea0f5-111">For more information, see [Create a Model Deployment Package by Using the Wizard](../../2014/master-data-services/create-a-model-deployment-package-by-using-the-wizard.md).</span></span>  
  
-   <span data-ttu-id="ea0f5-112">モデルを配置する環境の管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="ea0f5-112">You must be an administrator in the environment where you are deploying the model.</span></span> <span data-ttu-id="ea0f5-113">詳細については、「[管理者 &#40;マスターデータサービス&#41;](administrators-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ea0f5-113">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-deploy-a-model-deployment-package-of-model-objects-only"></a><span data-ttu-id="ea0f5-114">モデル オブジェクトのみのパッケージを配置するには</span><span class="sxs-lookup"><span data-stu-id="ea0f5-114">To deploy a model deployment package of model objects only</span></span>  
  
1.  <span data-ttu-id="ea0f5-115">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[システム管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ea0f5-115">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="ea0f5-116">**[モデル ビュー]** ページのメニュー バーから **[システム]** をポイントして **[配置]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ea0f5-116">On the **Model View** page, from the menu bar, point to **System** and click **Deployment**.</span></span>  
  
3.  <span data-ttu-id="ea0f5-117">**[モデル配置ウィザード]** で **[配置]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ea0f5-117">On the **Model Deployment Wizard**, click **Deploy**.</span></span>  
  
4.  <span data-ttu-id="ea0f5-118">**[参照]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ea0f5-118">Click **Browse**.</span></span>  
  
5.  <span data-ttu-id="ea0f5-119">配置パッケージ (.pkg ファイル) を見つけて **[開く]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ea0f5-119">Find your deployment package (.pkg file) and click **Open**.</span></span>  
  
6.  <span data-ttu-id="ea0f5-120">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ea0f5-120">Click **Next**.</span></span>  
  
7.  <span data-ttu-id="ea0f5-121">パッケージが読み込まれたら **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ea0f5-121">After the package is loaded, click **Next**.</span></span>  
  
8.  <span data-ttu-id="ea0f5-122">モデルが既に存在する場合は、 **[既存のモデルを更新する]** を選択することによって、そのモデルを更新できます。</span><span class="sxs-lookup"><span data-stu-id="ea0f5-122">If the model already exists, you can update it by selecting **Update the existing model**.</span></span> <span data-ttu-id="ea0f5-123">新しいモデルを作成するには、 **[新しいモデルを作成する]** を選択し、 **[次へ]** をクリックした後に新しいモデルの名前を入力できます。</span><span class="sxs-lookup"><span data-stu-id="ea0f5-123">To create a new model, select **Create a new model** and after you click **Next** you can type a name for the new model.</span></span>  
  
9. <span data-ttu-id="ea0f5-124">**[完了]** をクリックして、ウィザードを終了します。</span><span class="sxs-lookup"><span data-stu-id="ea0f5-124">Click **Finish** to exit the wizard.</span></span>  
  
 <span data-ttu-id="ea0f5-125">**注:**</span><span class="sxs-lookup"><span data-stu-id="ea0f5-125">**Notes:**</span></span>  
  
-   <span data-ttu-id="ea0f5-126">パッケージ内のサブスクリプションビューの名前が、既存のモデル内のサブスクリプションビューと同じである場合、ビューは modelname として作成され*ます。 subscriptionviewname*です。</span><span class="sxs-lookup"><span data-stu-id="ea0f5-126">If a subscription view in the package has the same name as a subscription view in an existing model, the view is created as *modelname.subscriptionviewname*.</span></span> <span data-ttu-id="ea0f5-127">この名前が既に使用されている場合、サブスクリプション ビューは作成されません。</span><span class="sxs-lookup"><span data-stu-id="ea0f5-127">If this name is already in use, the subscription view is not created.</span></span>  
  
-   <span data-ttu-id="ea0f5-128">配置プロセスには、次の 4 つの手順があります。</span><span class="sxs-lookup"><span data-stu-id="ea0f5-128">The deployment process has four steps:</span></span>  
  
    1.  <span data-ttu-id="ea0f5-129">モデル オブジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="ea0f5-129">The model objects are created.</span></span>  
  
    2.  <span data-ttu-id="ea0f5-130">サブスクリプション ビューが作成されます。</span><span class="sxs-lookup"><span data-stu-id="ea0f5-130">Subscription views are created.</span></span>  
  
    3.  <span data-ttu-id="ea0f5-131">ビジネス ルールが作成されます。</span><span class="sxs-lookup"><span data-stu-id="ea0f5-131">Business rules are created.</span></span>  
  
    4.  <span data-ttu-id="ea0f5-132">マスター データが設定されます。</span><span class="sxs-lookup"><span data-stu-id="ea0f5-132">Master data is populated.</span></span>  
  
-   <span data-ttu-id="ea0f5-133">新しいモデルまたは複製モデルを作成する場合、いずれかの手順の実行中にプロセスが失敗すると、モデルは削除されます。</span><span class="sxs-lookup"><span data-stu-id="ea0f5-133">When creating a new or cloned model, if the process fails during any step, the model is deleted.</span></span>  
  
     <span data-ttu-id="ea0f5-134">モデルを更新する場合、最初の 3 つの手順のいずれかでプロセスが失敗すると、その手順から先のプロセスは続行されません。ただし、既に行われた変更はロールバックされません。</span><span class="sxs-lookup"><span data-stu-id="ea0f5-134">When updating a model, if the process fails during any of the first three steps, it does not proceed beyond that step; however, changes that are already made are not rolled back.</span></span> <span data-ttu-id="ea0f5-135">手順 4. でプロセスが失敗すると、更新可能なメンバーが更新されます。</span><span class="sxs-lookup"><span data-stu-id="ea0f5-135">If the process fails in step 4, members that can be updated are updated.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="ea0f5-136">次の手順</span><span class="sxs-lookup"><span data-stu-id="ea0f5-136">Next Steps</span></span>  
 <span data-ttu-id="ea0f5-137">ユーザー定義メタデータ、ファイル属性、ユーザーおよびグループの権限はモデル配置パッケージに含まれていません。</span><span class="sxs-lookup"><span data-stu-id="ea0f5-137">User-defined metadata, file attributes, and user and group permissions are not included in model deployment packages.</span></span> <span data-ttu-id="ea0f5-138">モデルを配置した後、これらを手動で更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ea0f5-138">After you deploy a model, you must update these manually.</span></span> <span data-ttu-id="ea0f5-139">詳細については、次を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ea0f5-139">For more information, see:</span></span>  
  
-   [<span data-ttu-id="ea0f5-140">メタデータの追加 &#40;マスターデータサービス&#41;</span><span class="sxs-lookup"><span data-stu-id="ea0f5-140">Add Metadata &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/add-metadata-master-data-services.md)  
  
-   [<span data-ttu-id="ea0f5-141">モデル オブジェクト権限を割り当てる (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="ea0f5-141">Assign Model Object Permissions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/assign-model-object-permissions-master-data-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="ea0f5-142">参照</span><span class="sxs-lookup"><span data-stu-id="ea0f5-142">See Also</span></span>  
 [<span data-ttu-id="ea0f5-143">モデルの配置 (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="ea0f5-143">Deploying Models &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/deploying-models-master-data-services.md)  
  
  
