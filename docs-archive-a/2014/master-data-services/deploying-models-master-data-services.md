---
title: モデルの配置 (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- deployment packages [Master Data Services], about deployment packages
- deployment packages [Master Data Services]
ms.assetid: 30085c08-034f-4efe-80fe-408f9091ff5c
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: a9cc99112ec874e89ae07faa575235d9a041a972
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646194"
---
# <a name="deploying-models-master-data-services"></a><span data-ttu-id="fc485-102">モデルの配置 (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="fc485-102">Deploying Models (Master Data Services)</span></span>
  <span data-ttu-id="fc485-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]におけるパッケージは、配置可能なモデル構造と (必要に応じて) モデル データを含んだ XML ファイルです。</span><span class="sxs-lookup"><span data-stu-id="fc485-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], a package is an XML file that contains a deployable model structure, and optionally, data from the model.</span></span> <span data-ttu-id="fc485-104">モデル パッケージを使用して、モデルのコピーを MDS 環境間で移動したり、既存の MDS 環境に新しいモデルを作成したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="fc485-104">Use model packages to move copies of models from one MDS environment to another, or to create new models in your existing MDS environment.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="fc485-105">パッケージは、そのパッケージが作成されたエディションの [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] にのみ配置できます。</span><span class="sxs-lookup"><span data-stu-id="fc485-105">Packages can be deployed to the edition of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] they were created in only.</span></span> <span data-ttu-id="fc485-106">つまり、 [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] で作成されたパッケージを [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] 以降に配置することはできません。</span><span class="sxs-lookup"><span data-stu-id="fc485-106">This means that packages created in [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] cannot be deployed to [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] or higher.</span></span>  
  
## <a name="tools-for-deploying-models"></a><span data-ttu-id="fc485-107">モデルを展開するためのツール</span><span class="sxs-lookup"><span data-stu-id="fc485-107">Tools for Deploying Models</span></span>  
 <span data-ttu-id="fc485-108">モデル パッケージを使用するには、3 つのツールをニーズに応じて使い分けることができます。</span><span class="sxs-lookup"><span data-stu-id="fc485-108">To work with model packages, you can use one of three tools, depending on your needs.</span></span>  
  
-   <span data-ttu-id="fc485-109">**MDSModelDeploy ツール**: モデル オブジェクトとデータを作成して配置するには、MDSModelDeploy.exe ツールを使用します。</span><span class="sxs-lookup"><span data-stu-id="fc485-109">**MDSModelDeploy tool**: To create and deploy model objects and data, use the MDSModelDeploy.exe tool.</span></span> <span data-ttu-id="fc485-110">MDS のインストール時に既定のパスを選択した場合、このツールは*ドライブ*: services\configuration にあります。</span><span class="sxs-lookup"><span data-stu-id="fc485-110">If you selected the default path when installing MDS, this tool is located on *drive*:\Program Files\Microsoft SQL Server\120\Master Data Services\Configuration.</span></span>  
  
-   <span data-ttu-id="fc485-111">**モデル配置ウィザード**: モデルの構造のみのパッケージを作成して配置するには、 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Web アプリケーションのウィザードを使用します。</span><span class="sxs-lookup"><span data-stu-id="fc485-111">**Model Deployment wizard**: To create and deploy packages of the model structure only, use the wizard in the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] web application.</span></span> <span data-ttu-id="fc485-112">このウィザードを使用して、データを配置することはできません。</span><span class="sxs-lookup"><span data-stu-id="fc485-112">You cannot use this wizard to deploy data.</span></span>  
  
-   <span data-ttu-id="fc485-113">**モデル パッケージ エディター**: モデル パッケージを編集するには、ModelPackageEditor.exe を使用してモデル パッケージ エディター ウィザードを起動します。</span><span class="sxs-lookup"><span data-stu-id="fc485-113">**Model Package Editor**: To edit a model package, use the ModelPackageEditor.exe that launches the Model Package Editor wizard.</span></span> <span data-ttu-id="fc485-114">このウィザードを使用して、MDSModelDeploy ツールまたはモデル配置ウィザードによって作成されたパッケージを編集します。</span><span class="sxs-lookup"><span data-stu-id="fc485-114">You use this wizard to edit a package that was created by the MDSModelDeploy tool or the Model Deployment wizard.</span></span> <span data-ttu-id="fc485-115">MDS のインストール時に既定のパスを選択した場合、このツールは*ドライブ*: services\configuration にあります。</span><span class="sxs-lookup"><span data-stu-id="fc485-115">If you selected the default path when installing MDS, this tool is located on *drive*:\Program Files\Microsoft SQL Server\120\Master Data Services\Configuration.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="fc485-116">MDSDeployModel を使用すると、新しいモデルの作成、モデルの複製の作成、または既存のモデルとそのデータの更新を実行できます。</span><span class="sxs-lookup"><span data-stu-id="fc485-116">You can use the MDSDeployModel to create a new model, create a clone of a model, or update an existing model and its data.</span></span> <span data-ttu-id="fc485-117">MDSModelDeploy ツールを使用して既存のモデルとそのデータを更新するときに、配置先モデルに存在するエンティティ、属性、またはメンバーがパッケージに含まれていない場合は、MDSModelDeploy によって、そのエンティティ、属性、またはメンバーがモデルから削除されることはありません。</span><span class="sxs-lookup"><span data-stu-id="fc485-117">If you use the MDSModelDeploy tool to update an existing model and its data, and the package does not contain an entity, attribute, or member that exists in the destination model, MDSModelDeploy will not delete that entity, attribute, or member from the model.</span></span>  
  
## <a name="what-packages-contain"></a><span data-ttu-id="fc485-118">パッケージに含められるもの</span><span class="sxs-lookup"><span data-stu-id="fc485-118">What Packages Contain</span></span>  
 <span data-ttu-id="fc485-119">モデル パッケージは、.pkg 拡張子付きで保存される XML ファイルです。</span><span class="sxs-lookup"><span data-stu-id="fc485-119">A model package is an XML file that is saved with the .pkg extension.</span></span> <span data-ttu-id="fc485-120">配置パッケージを作成する場合、データを含めるかどうかを決定できます。</span><span class="sxs-lookup"><span data-stu-id="fc485-120">When you create a deployment package, you can decide whether or not to include data.</span></span> <span data-ttu-id="fc485-121">データを含める場合は、含めるデータのバージョンを選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fc485-121">If you decide to include data, you must select a version of the data to include.</span></span>  
  
 <span data-ttu-id="fc485-122">パッケージには、すべてのモデル オブジェクトが含まれています。</span><span class="sxs-lookup"><span data-stu-id="fc485-122">All model objects are included in a package.</span></span> <span data-ttu-id="fc485-123">オブジェクトを次に示します。</span><span class="sxs-lookup"><span data-stu-id="fc485-123">These objects are:</span></span>  
  
-   <span data-ttu-id="fc485-124">エンティティ</span><span class="sxs-lookup"><span data-stu-id="fc485-124">Entities</span></span>  
  
-   <span data-ttu-id="fc485-125">属性</span><span class="sxs-lookup"><span data-stu-id="fc485-125">Attributes</span></span>  
  
-   <span data-ttu-id="fc485-126">属性グループ</span><span class="sxs-lookup"><span data-stu-id="fc485-126">Attribute groups</span></span>  
  
-   <span data-ttu-id="fc485-127">階層</span><span class="sxs-lookup"><span data-stu-id="fc485-127">Hierarchies</span></span>  
  
-   <span data-ttu-id="fc485-128">コレクション</span><span class="sxs-lookup"><span data-stu-id="fc485-128">Collections</span></span>  
  
-   <span data-ttu-id="fc485-129">ビジネス ルール</span><span class="sxs-lookup"><span data-stu-id="fc485-129">Business rules</span></span>  
  
-   <span data-ttu-id="fc485-130">バージョン フラグ</span><span class="sxs-lookup"><span data-stu-id="fc485-130">Version flags</span></span>  
  
-   <span data-ttu-id="fc485-131">サブスクリプション ビュー</span><span class="sxs-lookup"><span data-stu-id="fc485-131">Subscription views</span></span>  
  
 <span data-ttu-id="fc485-132">ユーザー定義メタデータ、ファイル属性、ユーザーの権限、およびグループの権限は含めることができません。</span><span class="sxs-lookup"><span data-stu-id="fc485-132">User-defined metadata, file attributes, and user and group permissions are not included.</span></span> <span data-ttu-id="fc485-133">モデルを配置した後、これらを手動で更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fc485-133">After you deploy a model, you must update these manually.</span></span>  
  
## <a name="sample-packages"></a><span data-ttu-id="fc485-134">サンプル パッケージ</span><span class="sxs-lookup"><span data-stu-id="fc485-134">Sample Packages</span></span>  
 <span data-ttu-id="fc485-135">サンプル パッケージ ファイルは [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]のインストールに含まれています。</span><span class="sxs-lookup"><span data-stu-id="fc485-135">Sample package files are included when you install [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)].</span></span> <span data-ttu-id="fc485-136">このパッケージ ファイルは、 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]をインストールした Master Data Services\Samples\Packages ディレクトリにあります。</span><span class="sxs-lookup"><span data-stu-id="fc485-136">These package files are in the Master Data Services\Samples\Packages directory where you installed [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)].</span></span> <span data-ttu-id="fc485-137">MDSModelDeploy ツールを使用してサンプル パッケージを配置したときに、サンプル モデルが作成されデータが読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="fc485-137">When you deploy these sample packages by using the MDSModelDeploy tool, sample models are created and populated with data.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="fc485-138">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="fc485-138">Related Tasks</span></span>  
  
|<span data-ttu-id="fc485-139">タスクの説明</span><span class="sxs-lookup"><span data-stu-id="fc485-139">Task Description</span></span>|<span data-ttu-id="fc485-140">トピック</span><span class="sxs-lookup"><span data-stu-id="fc485-140">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="fc485-141">MDSModelDeploy ツールを使用して、モデル オブジェクトとデータの新しい配置パッケージを作成します。</span><span class="sxs-lookup"><span data-stu-id="fc485-141">Create a new deployment package of model objects and/or data by using the MDSModelDeploy tool.</span></span>|[<span data-ttu-id="fc485-142">MDSModelDeploy を使用したモデルの配置パッケージの作成</span><span class="sxs-lookup"><span data-stu-id="fc485-142">Create a Model Deployment Package by Using MDSModelDeploy</span></span>](../../2014/master-data-services/create-a-model-deployment-package-by-using-mdsmodeldeploy.md)|  
|<span data-ttu-id="fc485-143">ウィザードを使用して、モデル オブジェクトのみの新しい配置パッケージを作成します。</span><span class="sxs-lookup"><span data-stu-id="fc485-143">Create a new deployment package of model objects only by using the wizard.</span></span>|[<span data-ttu-id="fc485-144">ウィザードを使用したモデルの配置パッケージの作成</span><span class="sxs-lookup"><span data-stu-id="fc485-144">Create a Model Deployment Package by Using the Wizard</span></span>](../../2014/master-data-services/create-a-model-deployment-package-by-using-the-wizard.md)|  
|<span data-ttu-id="fc485-145">MDSModelDeploy ツールを使用して、モデル オブジェクトとデータのパッケージを配置します。</span><span class="sxs-lookup"><span data-stu-id="fc485-145">Deploy a package of model objects and data by using the MDSModelDeploy tool.</span></span>|[<span data-ttu-id="fc485-146">MDSModelDeploy を使用したモデルの配置パッケージの配置</span><span class="sxs-lookup"><span data-stu-id="fc485-146">Deploy a Model Deployment Package by Using MDSModelDeploy</span></span>](../../2014/master-data-services/deploy-a-model-deployment-package-by-using-mdsmodeldeploy.md)|  
|<span data-ttu-id="fc485-147">ウィザードを使用して、モデル オブジェクトのみのパッケージを配置します。</span><span class="sxs-lookup"><span data-stu-id="fc485-147">Deploy a package of model objects only by using the wizard.</span></span>|[<span data-ttu-id="fc485-148">ウィザードを使用したモデルの配置パッケージの展開</span><span class="sxs-lookup"><span data-stu-id="fc485-148">Deploy a Model Deployment Package by Using the Wizard</span></span>](../../2014/master-data-services/deploy-a-model-deployment-package-by-using-the-wizard.md)|  
|<span data-ttu-id="fc485-149">モデル全体ではなく、モデルの選択した部分を配置するには、モデルの配置パッケージを編集します。</span><span class="sxs-lookup"><span data-stu-id="fc485-149">Edit a model deployment package to deploy selected parts of a model, rather than the entire model.</span></span>|[<span data-ttu-id="fc485-150">モデルの配置パッケージの編集</span><span class="sxs-lookup"><span data-stu-id="fc485-150">Edit a Model Deployment Package</span></span>](../../2014/master-data-services/edit-a-model-deployment-package.md)|  
  
## <a name="related-content"></a><span data-ttu-id="fc485-151">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="fc485-151">Related Content</span></span>  
  
-   [<span data-ttu-id="fc485-152">モデル配置オプション (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="fc485-152">Model Deployment Options &#40;Master Data Services&#41;</span></span>](model-deployment-options-master-data-services.md)  
  
  
