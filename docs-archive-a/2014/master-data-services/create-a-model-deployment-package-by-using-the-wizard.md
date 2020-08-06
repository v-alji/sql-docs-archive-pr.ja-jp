---
title: ウィザードを使用したモデルの配置パッケージの作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- deployment packages [Master Data Services], creating
- models [Master Data Services], creating a deployment package
- creating packages [Master Data Services]
ms.assetid: b24ec4c2-1378-4c72-ac69-4ec2647030f0
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: abb30f9d8e08d8eec8e04960b61575da3a1dbcc0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645152"
---
# <a name="create-a-model-deployment-package-by-using-the-wizard"></a><span data-ttu-id="a6858-102">ウィザードを使用したモデルの配置パッケージの作成</span><span class="sxs-lookup"><span data-stu-id="a6858-102">Create a Model Deployment Package by Using the Wizard</span></span>
  <span data-ttu-id="a6858-103">モデル オブジェクトのみのパッケージを作成するには、 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] のモデル配置ウィザードを使用します。</span><span class="sxs-lookup"><span data-stu-id="a6858-103">Use the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] model deployment wizard to create a package of the model objects only.</span></span> <span data-ttu-id="a6858-104">パッケージにデータを含める必要がある場合は、「 [MDSModelDeploy を使用したモデルの配置パッケージの作成](../../2014/master-data-services/create-a-model-deployment-package-by-using-mdsmodeldeploy.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a6858-104">If you need to include data in the package, see [Create a Model Deployment Package by Using MDSModelDeploy](../../2014/master-data-services/create-a-model-deployment-package-by-using-mdsmodeldeploy.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="a6858-105">前提条件</span><span class="sxs-lookup"><span data-stu-id="a6858-105">Prerequisites</span></span>  
 <span data-ttu-id="a6858-106">この手順を実行するには</span><span class="sxs-lookup"><span data-stu-id="a6858-106">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="a6858-107">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Web アプリケーションで、 **[システム管理]** 機能領域にアクセスする権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="a6858-107">In the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] web application, you must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="a6858-108">モデル管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="a6858-108">You must be a model administrator.</span></span> <span data-ttu-id="a6858-109">詳細については、「[管理者 &#40;マスターデータサービス&#41;](administrators-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a6858-109">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="a6858-110">モデルのパッケージを作成するには、そのモデルが存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a6858-110">A model must exist for you to create a package of.</span></span> <span data-ttu-id="a6858-111">詳細については、「[モデルを作成する (マスター データ サービス)](../../2014/master-data-services/create-a-model-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a6858-111">For more information, see [Create a Model &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-model-master-data-services.md).</span></span>  
  
### <a name="to-create-a-model-deployment-package"></a><span data-ttu-id="a6858-112">モデルの配置パッケージを作成するには</span><span class="sxs-lookup"><span data-stu-id="a6858-112">To create a model deployment package</span></span>  
  
1.  <span data-ttu-id="a6858-113">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[システム管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a6858-113">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="a6858-114">**[モデル ビュー]** ページのメニュー バーから **[システム]** をポイントして **[配置]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a6858-114">On the **Model View** page, from the menu bar, point to **System** and click **Deployment**.</span></span>  
  
3.  <span data-ttu-id="a6858-115">**[モデル配置ウィザード]** で **[作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a6858-115">On the **Model Deployment Wizard**, click **Create**.</span></span>  
  
4.  <span data-ttu-id="a6858-116">**[パッケージの作成]** ページで **[モデル]** ボックスの一覧からモデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="a6858-116">On the **Create Package** page, select a model from the **Model** list.</span></span>  
  
5.  <span data-ttu-id="a6858-117">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a6858-117">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="a6858-118">**[Download]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a6858-118">Click **Download**.</span></span>  
  
7.  <span data-ttu-id="a6858-119">ファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="a6858-119">Save the file.</span></span>  
  
8.  <span data-ttu-id="a6858-120">**[閉じる]** をクリックしてウィザードを閉じます。</span><span class="sxs-lookup"><span data-stu-id="a6858-120">Click **Close** to close the wizard.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="a6858-121">次の手順</span><span class="sxs-lookup"><span data-stu-id="a6858-121">Next Steps</span></span>  
  
-   [<span data-ttu-id="a6858-122">ウィザードを使用したモデルの配置パッケージの展開</span><span class="sxs-lookup"><span data-stu-id="a6858-122">Deploy a Model Deployment Package by Using the Wizard</span></span>](../../2014/master-data-services/deploy-a-model-deployment-package-by-using-the-wizard.md)  
  
## <a name="see-also"></a><span data-ttu-id="a6858-123">参照</span><span class="sxs-lookup"><span data-stu-id="a6858-123">See Also</span></span>  
 [<span data-ttu-id="a6858-124">モデルの配置 (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="a6858-124">Deploying Models &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/deploying-models-master-data-services.md)  
  
  
