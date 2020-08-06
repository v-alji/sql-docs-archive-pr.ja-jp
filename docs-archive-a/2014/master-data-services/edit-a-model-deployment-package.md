---
title: モデルの配置パッケージの編集 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 6b0fdb7d-83dd-4392-9011-4ae642c471f1
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: b8bfd7083e2ba763d15a405266260b5a096c8378
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646177"
---
# <a name="edit-a-model-deployment-package"></a><span data-ttu-id="87235-102">モデルの配置パッケージの編集</span><span class="sxs-lookup"><span data-stu-id="87235-102">Edit a Model Deployment Package</span></span>
  <span data-ttu-id="87235-103">このトピックでは、モデル全体ではなく、モデルの選択した部分を MDS に配置する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="87235-103">This topic describes how to deploy selected parts of a model in MDS, rather than an entire model.</span></span> <span data-ttu-id="87235-104">これを行うには、モデル パッケージ エディターを使用して MDS モデル パッケージを編集します。</span><span class="sxs-lookup"><span data-stu-id="87235-104">To do so, you edit an MDS model package using the Model Package Editor.</span></span>  
  
 <span data-ttu-id="87235-105">モデル パッケージ エディター ウィザードを使用すると、MDS パッケージに含めるモデル内の特定のエンティティ、派生階層、サブスクリプション ビュー、およびビジネス ルールを選択して、後で配置することができます。</span><span class="sxs-lookup"><span data-stu-id="87235-105">The Model Package Editor wizard enables you to select the specific entities, derived hierarchies, subscription views, and business rules in a model that you want to include in an MDS package, and then later deploy.</span></span> <span data-ttu-id="87235-106">配置しないモデルの部分は除外できます。</span><span class="sxs-lookup"><span data-stu-id="87235-106">You can leave out those parts of the model that you do not want to deploy.</span></span> <span data-ttu-id="87235-107">エンティティを選択すると、そのエンティティの依存オブジェクトもすべて自動的に選択されます。</span><span class="sxs-lookup"><span data-stu-id="87235-107">When you select an entity, all of the dependent objects in that entity are also automatically selected.</span></span>  
  
 <span data-ttu-id="87235-108">モデル パッケージ エディターを使用して、MDSModelDeploy ツール (オブジェクトとデータを含むパッケージ ファイルを作成します) またはモデル配置ウィザード (モデル構造のみを含むファイルを作成します) で作成したパッケージ ファイル内のモデルの部分を選択します。</span><span class="sxs-lookup"><span data-stu-id="87235-108">You use the Model Package Editor to select parts of a model in a package file that was created by either the MDSModelDeploy tool (which creates a package file that includes objects and data) or the Model Deployment wizard (which creates a file that includes only the model structure).</span></span> <span data-ttu-id="87235-109">パッケージ内のモデルを編集したら、MDSModelDeploy ツールを使用してオブジェクトとデータを配置するか、モデル配置ウィザードを使用してモデル構造のみを配置します。</span><span class="sxs-lookup"><span data-stu-id="87235-109">After editing the model in the package, you use the MDSModelDeploy tool to deploy objects and data, or the Model Deployment wizard to deploy just the model structure.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="87235-110">前提条件</span><span class="sxs-lookup"><span data-stu-id="87235-110">Prerequisites</span></span>  
 <span data-ttu-id="87235-111">この手順を実行するには</span><span class="sxs-lookup"><span data-stu-id="87235-111">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="87235-112">モデル管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="87235-112">You must be a model administrator.</span></span> <span data-ttu-id="87235-113">詳細については、「[管理者 &#40;マスターデータサービス&#41;](administrators-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="87235-113">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="87235-114">モデル パッケージを編集するには、そのモデル パッケージが存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="87235-114">A model package must exist for you to edit.</span></span> <span data-ttu-id="87235-115">詳細については、「[モデルの配置 (マスター データ サービス)](../../2014/master-data-services/deploying-models-master-data-services.md)」と「[ウィザードを使用したモデルの配置パッケージの作成](../../2014/master-data-services/create-a-model-deployment-package-by-using-the-wizard.md)」、または「[MDSModelDeploy を使用したモデルの配置パッケージの作成](../../2014/master-data-services/create-a-model-deployment-package-by-using-mdsmodeldeploy.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="87235-115">For more information, see [Deploying Models &#40;Master Data Services&#41;](../../2014/master-data-services/deploying-models-master-data-services.md) and [Create a Model Deployment Package by Using the Wizard](../../2014/master-data-services/create-a-model-deployment-package-by-using-the-wizard.md) or [Create a Model Deployment Package by Using MDSModelDeploy](../../2014/master-data-services/create-a-model-deployment-package-by-using-mdsmodeldeploy.md).</span></span>  
  
### <a name="to-edit-a-model-deployment-package"></a><span data-ttu-id="87235-116">モデルの配置パッケージを編集するには</span><span class="sxs-lookup"><span data-stu-id="87235-116">To edit a model deployment package</span></span>  
  
1.  <span data-ttu-id="87235-117">MDS サーバーの Windows エクスプローラーで、*ドライブ*: 「services\configuration」に移動します。</span><span class="sxs-lookup"><span data-stu-id="87235-117">In Windows Explorer on the MDS server, move to *drive*:\Program Files\Microsoft SQL Server\120\Master Data Services\Configuration.</span></span>  
  
2.  <span data-ttu-id="87235-118">ModelPackageEditor.exe を実行します。</span><span class="sxs-lookup"><span data-stu-id="87235-118">Execute ModelPackageEditor.exe.</span></span>  
  
3.  <span data-ttu-id="87235-119">モデル パッケージ エディター ウィザードで、 **[参照]** をクリックしてパッケージが格納されているフォルダーに移動し、パッケージを選択して **[開く]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="87235-119">In the Model Package Editor wizard, click **Browse**, move to the folder containing your packages, select a package, and then click **Open**.</span></span> <span data-ttu-id="87235-120">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="87235-120">Click **Next**.</span></span>  
  
4.  <span data-ttu-id="87235-121">配置するエンティティ、派生階層、サブスクリプション ビュー、またはビジネス ルールを選択します。</span><span class="sxs-lookup"><span data-stu-id="87235-121">Select those entities, derived hierarchies, subscriptions views, or business rules that you want to deploy.</span></span> <span data-ttu-id="87235-122">配置しない項目は選択を解除します。</span><span class="sxs-lookup"><span data-stu-id="87235-122">Deselect those that you do not want to deploy.</span></span> <span data-ttu-id="87235-123">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="87235-123">Click **Next**.</span></span>  
  
5.  <span data-ttu-id="87235-124">配置する選択項目の一覧を確認します。</span><span class="sxs-lookup"><span data-stu-id="87235-124">Verify the list of selections to deploy.</span></span> <span data-ttu-id="87235-125">変更するには、 **[戻る]** をクリックして手順 4 を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="87235-125">To change, click **Back** and repeat step 4.</span></span>  
  
6.  <span data-ttu-id="87235-126">**[参照]** をクリックし、部分的なパッケージを保存するフォルダーに移動して、部分的なパッケージのファイル名を入力します (.pkg 拡張子を付けます)。</span><span class="sxs-lookup"><span data-stu-id="87235-126">Click **Browse**, move to the folder that you want to save the partial package in, and then enter the file name of the partial package (with a .pkg extension).</span></span> <span data-ttu-id="87235-127">**[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="87235-127">Click **Save**.</span></span>  
  
7.  <span data-ttu-id="87235-128">**[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="87235-128">Click **Finish**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="87235-129">次の手順</span><span class="sxs-lookup"><span data-stu-id="87235-129">Next Steps</span></span>  
  
-   [<span data-ttu-id="87235-130">ウィザードを使用したモデルの配置パッケージの展開</span><span class="sxs-lookup"><span data-stu-id="87235-130">Deploy a Model Deployment Package by Using the Wizard</span></span>](../../2014/master-data-services/deploy-a-model-deployment-package-by-using-the-wizard.md)  
  
-   [<span data-ttu-id="87235-131">MDSModelDeploy を使用したモデルの配置パッケージの配置</span><span class="sxs-lookup"><span data-stu-id="87235-131">Deploy a Model Deployment Package by Using MDSModelDeploy</span></span>](../../2014/master-data-services/deploy-a-model-deployment-package-by-using-mdsmodeldeploy.md)  
  
  
