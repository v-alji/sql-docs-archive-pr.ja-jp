---
title: モデル配置オプション (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: cf1b17b4-47d5-4eba-83f9-fb0555806867
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 25af38deef2a5476f64f364116dc5e9168345fb2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740122"
---
# <a name="model-deployment-options-master-data-services"></a><span data-ttu-id="f9e23-102">モデル配置オプション (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="f9e23-102">Model Deployment Options (Master Data Services)</span></span>
  <span data-ttu-id="f9e23-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]でモデル パッケージ ファイルを配置するとき、新しいモデルまたは複製モデルを配置するのか、以前に複製したモデルを更新するのかを決定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f9e23-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], when you deploy a model package file, you must decide whether to deploy a new or cloned model, or to update a model that was previously cloned.</span></span>  
  
## <a name="workflows"></a><span data-ttu-id="f9e23-104">ワークフロー</span><span class="sxs-lookup"><span data-stu-id="f9e23-104">Workflows</span></span>  
 <span data-ttu-id="f9e23-105">モデル パッケージを操作する場合、2 つの主要なワークフローがあります。</span><span class="sxs-lookup"><span data-stu-id="f9e23-105">When working with model packages, there are two primary workflows.</span></span>  
  
-   <span data-ttu-id="f9e23-106">テスト環境でモデルのパッケージを作成し、そのモデルの複製を運用環境に配置します。</span><span class="sxs-lookup"><span data-stu-id="f9e23-106">Create a package of a model in a test environment and deploy a clone of the model to a production environment.</span></span> <span data-ttu-id="f9e23-107">後で、テスト環境から運用環境に更新を配置します。</span><span class="sxs-lookup"><span data-stu-id="f9e23-107">Over time, deploy updates from the test environment to the production environment.</span></span>  
  
-   <span data-ttu-id="f9e23-108">モデルのパッケージを作成し、同じ環境に新しいモデルとして配置します。</span><span class="sxs-lookup"><span data-stu-id="f9e23-108">Create a package of a model and deploy it as a new model to the same environment.</span></span> <span data-ttu-id="f9e23-109">この場合、モデルに新しい名前を付ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="f9e23-109">In this case, you must give the model a new name.</span></span>  
  
## <a name="options"></a><span data-ttu-id="f9e23-110">Options</span><span class="sxs-lookup"><span data-stu-id="f9e23-110">Options</span></span>  
 <span data-ttu-id="f9e23-111">MDS データベースでは、各モデル オブジェクトに一意の識別子 (ID) があります。</span><span class="sxs-lookup"><span data-stu-id="f9e23-111">In the MDS database, each model object has a unique identifier (ID).</span></span> <span data-ttu-id="f9e23-112">これらの ID は、モデルの配置パッケージに含まれます。</span><span class="sxs-lookup"><span data-stu-id="f9e23-112">These IDs are included in model deployment packages.</span></span> <span data-ttu-id="f9e23-113">パッケージを配置する際、これらの ID をどのように処理するかを選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f9e23-113">When you deploy the package, you must choose what to do with these IDs.</span></span>  
  
 <span data-ttu-id="f9e23-114">次の表は、システム管理のモデル配置ウィザードまたは MDSModelDeploy ツールのいずれかを使用してモデルを配置する際に何を選択すればよいかを決定するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="f9e23-114">The following table should help you determine which choice to make when deploying a model by using either the System Administration model deployment wizard or the MDSModelDeploy tool.</span></span>  
  
|<span data-ttu-id="f9e23-115">オプション</span><span class="sxs-lookup"><span data-stu-id="f9e23-115">Option</span></span>|<span data-ttu-id="f9e23-116">説明</span><span class="sxs-lookup"><span data-stu-id="f9e23-116">Description</span></span>|<span data-ttu-id="f9e23-117">Notes</span><span class="sxs-lookup"><span data-stu-id="f9e23-117">Notes</span></span>|  
|------------|-----------------|-----------|  
|<span data-ttu-id="f9e23-118">新規作成</span><span class="sxs-lookup"><span data-stu-id="f9e23-118">New</span></span>|<span data-ttu-id="f9e23-119">一意の名前を持つ新しいモデルを作成します。</span><span class="sxs-lookup"><span data-stu-id="f9e23-119">Create a new model with a unique name.</span></span> <span data-ttu-id="f9e23-120">すべてのモデル オブジェクトに新しい識別子が作成されます。</span><span class="sxs-lookup"><span data-stu-id="f9e23-120">New identifiers are created for all model objects.</span></span>|<span data-ttu-id="f9e23-121">新しい識別子を持つ新しいモデルを作成した場合、後でモデル配置ツールを使用してモデルに更新を適用することはできません。</span><span class="sxs-lookup"><span data-stu-id="f9e23-121">If you create a new model with new identifiers, you cannot use model deployment tools to apply updates to the model later.</span></span> <span data-ttu-id="f9e23-122">Web アプリケーションのウィザードを使用してモデル パッケージを配置ときに、同じ名前または ID を持つモデルが既に存在している場合、選択できるのは新しいモデルの作成のみです。</span><span class="sxs-lookup"><span data-stu-id="f9e23-122">When using the wizard in the web application to deploy a model package, you have the option to create a new model only if a model with the same name or ID already exists.</span></span>|  
|<span data-ttu-id="f9e23-123">複製</span><span class="sxs-lookup"><span data-stu-id="f9e23-123">Clone</span></span>|<span data-ttu-id="f9e23-124">パッケージ内のモデルの正確な複製である新しいモデルを作成します。</span><span class="sxs-lookup"><span data-stu-id="f9e23-124">Create a new model that is an exact clone of the model in the package.</span></span> <span data-ttu-id="f9e23-125">このオプションは、名前または識別子が同じモデルがターゲット環境内に存在しない場合にのみ機能します。</span><span class="sxs-lookup"><span data-stu-id="f9e23-125">This works only if the model does not exist (by name or identifier) in the target environment.</span></span> <span data-ttu-id="f9e23-126">複数の環境に同じモデルがあり、複製したモデルを後で更新する場合は、"複製" を使用します。</span><span class="sxs-lookup"><span data-stu-id="f9e23-126">Use "clone" when you want to have the same model in multiple environments and update the cloned model over time.</span></span>|<span data-ttu-id="f9e23-127">これは、Web アプリケーションのウィザードの既定の動作です。</span><span class="sxs-lookup"><span data-stu-id="f9e23-127">This is the default behavior of the wizard in the web application.</span></span> <span data-ttu-id="f9e23-128">同じ名前または ID を持つモデルが既に存在する場合は、代わりに新しいモデルを作成するよう求められます。</span><span class="sxs-lookup"><span data-stu-id="f9e23-128">If a model with the same name or ID already exists, you are prompted to create a new model instead.</span></span>|  
|<span data-ttu-id="f9e23-129">更新</span><span class="sxs-lookup"><span data-stu-id="f9e23-129">Update</span></span>|<span data-ttu-id="f9e23-130">パッケージ内のモデルを使用して、既存のモデルを更新します。</span><span class="sxs-lookup"><span data-stu-id="f9e23-130">Update an existing model with the model in the package.</span></span> <span data-ttu-id="f9e23-131">両方のモデルの識別子が同じである必要があります。</span><span class="sxs-lookup"><span data-stu-id="f9e23-131">The identifiers must be the same in both models.</span></span> <span data-ttu-id="f9e23-132">このオプションは、以前に複製したモデルを更新するために使用します。</span><span class="sxs-lookup"><span data-stu-id="f9e23-132">This is used to update a model that you previously cloned.</span></span>|<span data-ttu-id="f9e23-133">以前に複製したモデルのみを更新できます</span><span class="sxs-lookup"><span data-stu-id="f9e23-133">You can only update models that were previously cloned.</span></span> <span data-ttu-id="f9e23-134">(名前と ID が一致する必要があります)。</span><span class="sxs-lookup"><span data-stu-id="f9e23-134">(The names and IDs must match.)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f9e23-135">参照</span><span class="sxs-lookup"><span data-stu-id="f9e23-135">See Also</span></span>  
 <span data-ttu-id="f9e23-136">[MDSModelDeploy を使用してモデルの配置パッケージを配置する](../../2014/master-data-services/deploy-a-model-deployment-package-by-using-mdsmodeldeploy.md) </span><span class="sxs-lookup"><span data-stu-id="f9e23-136">[Deploy a Model Deployment Package by Using MDSModelDeploy](../../2014/master-data-services/deploy-a-model-deployment-package-by-using-mdsmodeldeploy.md) </span></span>  
 <span data-ttu-id="f9e23-137">[ウィザードを使用してモデルの配置パッケージを配置する](../../2014/master-data-services/deploy-a-model-deployment-package-by-using-the-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="f9e23-137">[Deploy a Model Deployment Package by Using the Wizard](../../2014/master-data-services/deploy-a-model-deployment-package-by-using-the-wizard.md) </span></span>  
 [<span data-ttu-id="f9e23-138">モデルの配置 (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="f9e23-138">Deploying Models &#40;Master Data Services&#41;</span></span>](deploying-models-master-data-services.md)  
  
  
