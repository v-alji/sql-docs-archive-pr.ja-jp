---
title: MDSModelDeploy を使用したモデルの配置パッケージの作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: c2687e39-dc20-494f-a707-2aa29f4c329e
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: c546d6398234dd43103d0e6c75822377e11de61a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645714"
---
# <a name="create-a-model-deployment-package-by-using-mdsmodeldeploy"></a><span data-ttu-id="8a75f-102">MDSModelDeploy を使用したモデルの配置パッケージの作成</span><span class="sxs-lookup"><span data-stu-id="8a75f-102">Create a Model Deployment Package by Using MDSModelDeploy</span></span>
  <span data-ttu-id="8a75f-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]では、MDSModelDeploy ツールを使用して、パッケージを作成します。</span><span class="sxs-lookup"><span data-stu-id="8a75f-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], use the MDSModelDeploy tool to create a package.</span></span> <span data-ttu-id="8a75f-104">指定するコマンドに応じて、次のどちらかを含むパッケージを作成できます。</span><span class="sxs-lookup"><span data-stu-id="8a75f-104">Depending on the commands you specify, the package can contain either:</span></span>  
  
-   <span data-ttu-id="8a75f-105">モデル オブジェクトのみ。</span><span class="sxs-lookup"><span data-stu-id="8a75f-105">Model objects only.</span></span>  
  
-   <span data-ttu-id="8a75f-106">モデル オブジェクトとデータ。</span><span class="sxs-lookup"><span data-stu-id="8a75f-106">Model objects and data.</span></span>  
  
 <span data-ttu-id="8a75f-107">モデル オブジェクトのみを含むパッケージを配置する必要がある場合は、代わりに、 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Web アプリケーションのモデル配置ウィザードを使用できます。</span><span class="sxs-lookup"><span data-stu-id="8a75f-107">If you want to deploy a package that contains model objects only, you can use the model deployment wizard in the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] web application instead.</span></span> <span data-ttu-id="8a75f-108">詳細については、「 [ウィザードを使用したモデルの配置パッケージの作成](../../2014/master-data-services/create-a-model-deployment-package-by-using-the-wizard.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8a75f-108">For more information, see [Create a Model Deployment Package by Using the Wizard](../../2014/master-data-services/create-a-model-deployment-package-by-using-the-wizard.md).</span></span>  
> [!NOTE]  
> <span data-ttu-id="8a75f-109">このバージョンの MDSModelDeploy ツールは、ギガバイト (GB) を超えるメモリを使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="8a75f-109">This version of the MDSModelDeploy tool cannot use more than gigabytes (GB) of memory.</span></span> <span data-ttu-id="8a75f-110">**モデルオブジェクトとデータ**オプションを使用して大規模なモデルを作成または配置すると、"メモリが不足しています" または "ストリームが長すぎます" というエラーが発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="8a75f-110">When you create or deploy large models by using **Model objects and data** option, you may experience "Out of Memory" or "Stream was too long" errors.</span></span> <span data-ttu-id="8a75f-111">この問題を解決するには、MDS ステージングを使用してデータをデプロイします。または、最新バージョンの MDSModelDeploy ツールを含む MDS 2016 以降のバージョンにアップグレードします。</span><span class="sxs-lookup"><span data-stu-id="8a75f-111">To resolve this issue, use MDS staging to deploy the data; or upgrade to MDS 2016 or a later version, which includes the updated version of the MDSModelDeploy tool.</span></span>
## <a name="prerequisites"></a><span data-ttu-id="8a75f-112">前提条件</span><span class="sxs-lookup"><span data-stu-id="8a75f-112">Prerequisites</span></span>  
 <span data-ttu-id="8a75f-113">この手順を実行するには</span><span class="sxs-lookup"><span data-stu-id="8a75f-113">To perform this procedure:</span></span>  
  
1.  <span data-ttu-id="8a75f-114">MDSModelDeploy ツールを実行するために必要な基本的な権限は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="8a75f-114">The basic permissions required to run the MDSModelDeploy tool are the following:</span></span>  
  
    -   <span data-ttu-id="8a75f-115">MDS 構成マネージャー (Windows の管理者) と同じ Windows 権限</span><span class="sxs-lookup"><span data-stu-id="8a75f-115">The same Windows permission as the MDS Configuration Manager (administrator of Windows)</span></span>  
  
    -   <span data-ttu-id="8a75f-116">MDS データベースに対する DBA 権限</span><span class="sxs-lookup"><span data-stu-id="8a75f-116">DBA permission on the MDS database.</span></span>  
  
2.  <span data-ttu-id="8a75f-117">MDSModelDeploy ツールを使用してパッケージを作成するために必要な権限は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="8a75f-117">The permissions required to create the package using the MDSModelDeploy tool are the following:</span></span>  
  
    -   <span data-ttu-id="8a75f-118">データ モデルに対する MDS モデル管理者権限</span><span class="sxs-lookup"><span data-stu-id="8a75f-118">MDS model administrator permission on the data model.</span></span>  
  
    -   <span data-ttu-id="8a75f-119">MDS 統合管理機能権限</span><span class="sxs-lookup"><span data-stu-id="8a75f-119">MDS Integration Management function permission.</span></span>  
  
3.  <span data-ttu-id="8a75f-120">MDSModelDeploy ツールを使用してモデルを配置するために必要な権限は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="8a75f-120">The permissions required to deploy a model using the MDSModelDeploy tool are the following:</span></span>  
  
    -   <span data-ttu-id="8a75f-121">MDS エクスプローラー機能権限</span><span class="sxs-lookup"><span data-stu-id="8a75f-121">MDS Explorer function permission</span></span>  
  
    -   <span data-ttu-id="8a75f-122">MDS 統合管理関数の権限</span><span class="sxs-lookup"><span data-stu-id="8a75f-122">MDS Integration Management function permission</span></span>  
  
    -   <span data-ttu-id="8a75f-123">MDS システム管理機能権限</span><span class="sxs-lookup"><span data-stu-id="8a75f-123">MDS System Administration function permission.</span></span>  
  
4.  <span data-ttu-id="8a75f-124">MDSModelDeploy ツールを使用してモデルをリストするために必要な権限は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="8a75f-124">The permissions required to list models using the MDSModelDeploy tool are the following:</span></span>  
  
    -   <span data-ttu-id="8a75f-125">MDS エクスプローラー機能権限</span><span class="sxs-lookup"><span data-stu-id="8a75f-125">MDS Explorer function permission</span></span>  
  
    -   <span data-ttu-id="8a75f-126">リスト内のモデルを表示するための、データ モデルに対する MDS モデル管理権限</span><span class="sxs-lookup"><span data-stu-id="8a75f-126">MDS model administrator permission on the data model on order to see the model in the list.</span></span>  
  
 <span data-ttu-id="8a75f-127">モデルのパッケージを作成するには、そのモデルが存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8a75f-127">A model must exist for you to create a package of.</span></span> <span data-ttu-id="8a75f-128">詳細については、「[モデルを作成する (マスター データ サービス)](create-a-model-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8a75f-128">For more information, see [Create a Model &#40;Master Data Services&#41;](create-a-model-master-data-services.md).</span></span>  
  
 <span data-ttu-id="8a75f-129">詳細については、「[管理者 &#40;マスターデータサービス&#41;](../../2014/master-data-services/administrators-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8a75f-129">For more information, see [Administrators &#40;Master Data Services&#41;](../../2014/master-data-services/administrators-master-data-services.md).</span></span>  
  
### <a name="to-create-a-model-deployment-package-by-using-mdsmodeldeploy"></a><span data-ttu-id="8a75f-130">MDSModelDeploy を使用してモデルの配置パッケージを作成するには</span><span class="sxs-lookup"><span data-stu-id="8a75f-130">To create a model deployment package by using MDSModelDeploy</span></span>  
  
1.  <span data-ttu-id="8a75f-131">コマンド プロンプトを開きます。</span><span class="sxs-lookup"><span data-stu-id="8a75f-131">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="8a75f-132">MDSModelDeploy.exe がある場所に移動します。</span><span class="sxs-lookup"><span data-stu-id="8a75f-132">Navigate to the location of MDSModelDeploy.exe.</span></span>  
  
    -   <span data-ttu-id="8a75f-133">MDS が既定の場所にインストールされている場合、ファイルは*ドライブ*: services\configuration にあります。</span><span class="sxs-lookup"><span data-stu-id="8a75f-133">If MDS was installed in the default location, the file is in *drive*:\Program Files\Microsoft SQL Server\120\Master Data Services\Configuration.</span></span>  
  
    -   <span data-ttu-id="8a75f-134">MDS を既定の場所にインストールしなかった場合は、ローカル コンピューター内で MDSModelDeploy.exe を検索します。</span><span class="sxs-lookup"><span data-stu-id="8a75f-134">If MDS was not installed in the default location, search the local computer for MDSModelDeploy.exe.</span></span>  
  
3.  <span data-ttu-id="8a75f-135">省略可能。</span><span class="sxs-lookup"><span data-stu-id="8a75f-135">Optional.</span></span> <span data-ttu-id="8a75f-136">オプションおよびヘルプを表示します。</span><span class="sxs-lookup"><span data-stu-id="8a75f-136">View options and help.</span></span>  
  
    -   <span data-ttu-id="8a75f-137">使用可能なすべてのオプションを表示するには、「 `MDSModelDeploy` 」と入力し、Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="8a75f-137">To display all available options, type `MDSModelDeploy` and press Enter.</span></span>  
  
    -   <span data-ttu-id="8a75f-138">オプションのヘルプを表示するには、「 *」と入力します。* OptionName `MDSModelDeploy help OptionName`はオプションの名前です。</span><span class="sxs-lookup"><span data-stu-id="8a75f-138">To display help for an option, type the following, where *OptionName* is the name of the option: `MDSModelDeploy help OptionName`.</span></span>  
  
4.  <span data-ttu-id="8a75f-139">省略可能。</span><span class="sxs-lookup"><span data-stu-id="8a75f-139">Optional.</span></span> <span data-ttu-id="8a75f-140">Web アプリケーションが複数ある場合、次のコマンドを入力し、Enter キーを押して、配置するサービスの名前を確認します。</span><span class="sxs-lookup"><span data-stu-id="8a75f-140">If you have multiple web applications, determine the name of the service you will deploy to by typing this command and pressing Enter:</span></span>  
  
    ```  
    MDSModelDeploy listservices  
    ```  
  
     <span data-ttu-id="8a75f-141">値の一覧が返されます (例: `MDS1, Default Web Site, MDS`)。</span><span class="sxs-lookup"><span data-stu-id="8a75f-141">A list of values is returned, for example `MDS1, Default Web Site, MDS`.</span></span> <span data-ttu-id="8a75f-142">モデルを配置するには、この一覧の最初の値 (この例では、 `MDS1`) が必要です。</span><span class="sxs-lookup"><span data-stu-id="8a75f-142">The first value in this list (in this case, `MDS1`) is needed to deploy the model.</span></span>  
  
5.  <span data-ttu-id="8a75f-143">モデル オブジェクトとデータを含むパッケージを作成するには、次のコマンドを入力します。 *ModelName*、 *VersionName*、 *ServiceName*、および *PackageName* は、それぞれモデル、バージョン、サービス、および .pkg 出力ファイルの名前です。</span><span class="sxs-lookup"><span data-stu-id="8a75f-143">To create a package that contains model objects and data, type the following, where *ModelName*, *VersionName*, *ServiceName*,  and *PackageName* are the names of the model, version, service, and of the .pkg output file respectively:</span></span>  
  
    ```  
    MDSModelDeploy createpackage -model ModelName -version VersionName -service ServiceName -package PackageName -includedata  
    ```  
  
     <span data-ttu-id="8a75f-144">データを含める必要がない場合は、 `-version` スイッチと `-includedata` スイッチを使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="8a75f-144">If you do not want to include data, do not use the `-version` and `-includedata` switches.</span></span>  
  
6.  <span data-ttu-id="8a75f-145">Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="8a75f-145">Press Enter.</span></span> <span data-ttu-id="8a75f-146">パッケージが正常に作成されると、「MDSModelDeploy 操作は正常に完了しました」というメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="8a75f-146">When the package is successfully created, a message stating "MDSModelDeploy operation completed successfully" is displayed.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="8a75f-147">次の手順</span><span class="sxs-lookup"><span data-stu-id="8a75f-147">Next Steps</span></span>  
  
-   [<span data-ttu-id="8a75f-148">MDSModelDeploy を使用したモデルの配置パッケージの配置</span><span class="sxs-lookup"><span data-stu-id="8a75f-148">Deploy a Model Deployment Package by Using MDSModelDeploy</span></span>](../../2014/master-data-services/deploy-a-model-deployment-package-by-using-mdsmodeldeploy.md)  
  
## <a name="see-also"></a><span data-ttu-id="8a75f-149">参照</span><span class="sxs-lookup"><span data-stu-id="8a75f-149">See Also</span></span>  
 <span data-ttu-id="8a75f-150">[モデル配置オプション &#40;マスターデータサービス&#41;](../../2014/master-data-services/model-deployment-options-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="8a75f-150">[Model Deployment Options &#40;Master Data Services&#41;](../../2014/master-data-services/model-deployment-options-master-data-services.md) </span></span>  
 [<span data-ttu-id="8a75f-151">モデルの配置 (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="8a75f-151">Deploying Models &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/deploying-models-master-data-services.md)  
  
  
