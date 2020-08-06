---
title: 参照変換用のキャッシュを作成および配置する | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- creating cache files for Lookup transformation
- deploying cache files for Lookup transformation
- Lookup transformation cache files
ms.assetid: cedf5cad-2fac-42d0-ad91-9461e117d330
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b33b00b84f1f1448c2ee80882aedc3a330ba0a5a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631158"
---
# <a name="create-and-deploy-a-cache-for-the-lookup-transformation"></a><span data-ttu-id="00c11-102">参照変換用のキャッシュを作成および配置する</span><span class="sxs-lookup"><span data-stu-id="00c11-102">Create and Deploy a Cache for the Lookup Transformation</span></span>
  <span data-ttu-id="00c11-103">参照変換用のキャッシュ ファイル (.caw) を作成および配置できます。</span><span class="sxs-lookup"><span data-stu-id="00c11-103">You can create and deploy a cache file (.caw) for the Lookup transformation.</span></span> <span data-ttu-id="00c11-104">参照データセットはキャッシュ ファイルに格納されます。</span><span class="sxs-lookup"><span data-stu-id="00c11-104">The reference dataset is stored in the cache file.</span></span>  
  
 <span data-ttu-id="00c11-105">参照変換は、接続されているデータ ソースの入力列のデータを参照データセットの列と結合することにより参照を実行します。</span><span class="sxs-lookup"><span data-stu-id="00c11-105">The Lookup transformation performs lookups by joining data in input columns from a connected data source with columns in the reference dataset.</span></span>  
  
 <span data-ttu-id="00c11-106">キャッシュ接続マネージャーおよびキャッシュ変換を使用して、キャッシュ ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="00c11-106">You create a cache file by using a Cache connection manager and a Cache Transform transformation.</span></span> <span data-ttu-id="00c11-107">詳細については、「 [キャッシュ接続マネージャー](../../connection-manager/cache-connection-manager.md) 」および「 [キャッシュ変換](cache-transform.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="00c11-107">For more information, see [Cache Connection Manager](../../connection-manager/cache-connection-manager.md) and [Cache Transform](cache-transform.md).</span></span>  
  
 <span data-ttu-id="00c11-108">参照変換とキャッシュ ファイルの詳細については、「 [参照変換](lookup-transformation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="00c11-108">To learn more about the Lookup transformation and cache files, see [Lookup Transformation](lookup-transformation.md).</span></span>  
  
### <a name="to-create-a-cache-file"></a><span data-ttu-id="00c11-109">キャッシュ ファイルを作成するには</span><span class="sxs-lookup"><span data-stu-id="00c11-109">To create a cache file</span></span>  
  
1.  <span data-ttu-id="00c11-110">[!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]で、目的のパッケージが含まれている [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] プロジェクトを開き、そのパッケージを開きます。</span><span class="sxs-lookup"><span data-stu-id="00c11-110">In [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] project that contains the package you want, and then open the package.</span></span>  
  
2.  <span data-ttu-id="00c11-111">**[制御フロー]** タブで、データ フロー タスクを追加します。</span><span class="sxs-lookup"><span data-stu-id="00c11-111">On the **Control Flow** tab, add a Data Flow task.</span></span>  
  
3.  <span data-ttu-id="00c11-112">**[データ フロー]** タブで、データ フローにキャッシュ変換を追加し、変換をデータ ソースに接続します。</span><span class="sxs-lookup"><span data-stu-id="00c11-112">On the **Data Flow** tab, add a Cache Transform transformation to the data flow, and then connect the transformation to a data source.</span></span>  
  
     <span data-ttu-id="00c11-113">必要に応じて、データ ソースを構成します。</span><span class="sxs-lookup"><span data-stu-id="00c11-113">Configure the data source as needed.</span></span>  
  
4.  <span data-ttu-id="00c11-114">キャッシュ変換をダブルクリックし、 **[キャッシュ変換エディター]** の **[接続マネージャー]** ページで **[新規作成]** をクリックして、新しい接続マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="00c11-114">Double-click the Cache Transform, and then in the **Cache Transformation Editor**, on the **Connection Manager** page, click **New** to create a new Cache connection manager.</span></span>  
  
5.  <span data-ttu-id="00c11-115">**[キャッシュ接続マネージャー エディター]** ダイアログ ボックスの **[全般]** タブで、次のオプションを選択してキャッシュを保存するようにキャッシュ接続マネージャーを構成します。</span><span class="sxs-lookup"><span data-stu-id="00c11-115">In the **Cache Connection Manager Editor**, on the **General** tab, configure the Cache connection manager to save the cache by selecting the following options:</span></span>  
  
    1.  <span data-ttu-id="00c11-116">**[ファイル キャッシュを使用する]** をオンにします。</span><span class="sxs-lookup"><span data-stu-id="00c11-116">Select **Use file cache**.</span></span>  
  
    2.  <span data-ttu-id="00c11-117">**[ファイル名]** に、ファイル パスを入力します。</span><span class="sxs-lookup"><span data-stu-id="00c11-117">For **File name**, type the file path.</span></span>  
  
     <span data-ttu-id="00c11-118">パッケージを実行すると、ファイルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="00c11-118">The system creates the file when you run the package.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="00c11-119">パッケージの保護レベルは、キャッシュ ファイルに適用されません。</span><span class="sxs-lookup"><span data-stu-id="00c11-119">The protection level of the package does not apply to the cache file.</span></span> <span data-ttu-id="00c11-120">キャッシュ ファイルに機密情報が含まれている場合は、アクセス制御リスト (ACL) を使用して、ファイルを格納している場所またはフォルダーへのアクセスを制限します。</span><span class="sxs-lookup"><span data-stu-id="00c11-120">If the cache file contains sensitive information, use an access control list (ACL) to restrict access to the location or folder in which you store the file.</span></span> <span data-ttu-id="00c11-121">特定のアカウントに対してのみアクセスを有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="00c11-121">You should enable access only to certain accounts.</span></span> <span data-ttu-id="00c11-122">詳細については、「 [パッケージで使用されるファイルへのアクセス](../../access-to-files-used-by-packages.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="00c11-122">For more information, see [Access to Files Used by Packages](../../access-to-files-used-by-packages.md).</span></span>  
  
6.  <span data-ttu-id="00c11-123">**[列]** タブをクリックし、 **[インデックス位置]** オプションを使用して、インデックス列として使用する列を指定します。</span><span class="sxs-lookup"><span data-stu-id="00c11-123">Click the **Columns** tab, and then specify which columns are the index columns by using the **Index Position** option.</span></span>  
  
     <span data-ttu-id="00c11-124">インデックス以外の列の場合、インデックス位置は 0 です。</span><span class="sxs-lookup"><span data-stu-id="00c11-124">For non-index columns, the index position is 0.</span></span> <span data-ttu-id="00c11-125">インデックス列の場合、インデックスの位置は連続した正の数になります。</span><span class="sxs-lookup"><span data-stu-id="00c11-125">For index columns, the index position is a sequential, positive number.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="00c11-126">参照変換がキャッシュ接続マネージャーを使用するように構成されている場合、参照データセット内のインデックス列のみ入力列にマップできます。</span><span class="sxs-lookup"><span data-stu-id="00c11-126">When the Lookup transformation is configured to use a Cache connection manager, only index columns in the reference dataset can be mapped to input columns.</span></span> <span data-ttu-id="00c11-127">また、すべてのインデックス列をマップする必要があります。</span><span class="sxs-lookup"><span data-stu-id="00c11-127">Also all index columns must be mapped.</span></span>  
  
     <span data-ttu-id="00c11-128">詳細については、「 [キャッシュ接続マネージャー エディター](../../cache-connection-manager-editor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="00c11-128">For more information, see [Cache Connection Manager Editor](../../cache-connection-manager-editor.md).</span></span>  
  
7.  <span data-ttu-id="00c11-129">必要に応じてキャッシュ変換を構成します。</span><span class="sxs-lookup"><span data-stu-id="00c11-129">Configure the Cache Transform as needed.</span></span>  
  
     <span data-ttu-id="00c11-130">詳細については、「[キャッシュ変換エディター &#40;[接続マネージャー] ページ&#41;](../../cache-transformation-editor-connection-manager-page.md)」および「[キャッシュ変換エディター &#40;[マッピング] ページ&#41;](../../cache-transformation-editor-mappings-page.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="00c11-130">For more information, see [Cache Transformation Editor &#40;Connection Manager Page&#41;](../../cache-transformation-editor-connection-manager-page.md) and [Cache Transformation Editor &#40;Mappings Page&#41;](../../cache-transformation-editor-mappings-page.md).</span></span>  
  
8.  <span data-ttu-id="00c11-131">パッケージを実行します。</span><span class="sxs-lookup"><span data-stu-id="00c11-131">Run the package.</span></span>  
  
### <a name="to-deploy-a-cache-file"></a><span data-ttu-id="00c11-132">キャッシュ ファイルを配置するには</span><span class="sxs-lookup"><span data-stu-id="00c11-132">To deploy a cache file</span></span>  
  
1.  <span data-ttu-id="00c11-133">[!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]で、目的のパッケージが含まれている [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] プロジェクトを開き、そのパッケージを開きます。</span><span class="sxs-lookup"><span data-stu-id="00c11-133">In [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] project that contains the package you want, and then open the package.</span></span>  
  
2.  <span data-ttu-id="00c11-134">必要に応じて、パッケージ構成を作成します。</span><span class="sxs-lookup"><span data-stu-id="00c11-134">Optionally, create a package configuration.</span></span> <span data-ttu-id="00c11-135">詳細については、「 [パッケージ構成を作成する](../../create-package-configurations.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="00c11-135">For more information, see [Create Package Configurations](../../create-package-configurations.md).</span></span>  
  
3.  <span data-ttu-id="00c11-136">次の操作を行って、キャッシュ ファイルをプロジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="00c11-136">Add the cache file to the project by doing the following:</span></span>  
  
    1.  <span data-ttu-id="00c11-137">ソリューション エクスプローラーで、手順 1. で開いたプロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="00c11-137">In Solution Explorer, select the project you opened in step 1.</span></span>  
  
    2.  <span data-ttu-id="00c11-138">**[プロジェクト]** メニューの **[既存項目の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="00c11-138">On the **Project** menu, click **AddExisting Item**.</span></span>  
  
    3.  <span data-ttu-id="00c11-139">キャッシュ ファイルを選択し、 **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="00c11-139">Select the cache file, and then click **Add**.</span></span>  
  
     <span data-ttu-id="00c11-140">ソリューション エクスプローラーの **[その他]** フォルダーに、選択したキャッシュ ファイルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="00c11-140">The file appears in the **Miscellaneous** folder in Solution Explorer.</span></span>  
  
4.  <span data-ttu-id="00c11-141">配置ユーティリティを作成するようにプロジェクトを構成し、プロジェクトをビルドします。</span><span class="sxs-lookup"><span data-stu-id="00c11-141">Configure the project to create a deployment utility, and then build the project.</span></span> <span data-ttu-id="00c11-142">詳細については、「 [配置ユーティリティを作成する](../../create-a-deployment-utility.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="00c11-142">For more information, see [Create a Deployment Utility](../../create-a-deployment-utility.md).</span></span>  
  
     <span data-ttu-id="00c11-143">マニフェスト ファイル \<*project name*>.SSISDeploymentManifest.xml が作成され、プロジェクトに含まれるその他のファイル、パッケージ、およびパッケージ構成の一覧が示されます。</span><span class="sxs-lookup"><span data-stu-id="00c11-143">A manifest file, \<*project name*>.SSISDeploymentManifest.xml, is created that lists the miscellaneous files in the project, the packages, and the package configurations.</span></span>  
  
5.  <span data-ttu-id="00c11-144">パッケージをファイル システムに配置します。</span><span class="sxs-lookup"><span data-stu-id="00c11-144">Deploy the package to the file system.</span></span> <span data-ttu-id="00c11-145">詳細については、「 [配置ユーティリティを使用してパッケージを配置する](../../deploy-packages-by-using-the-deployment-utility.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="00c11-145">For more information, see [Deploy Packages by Using the Deployment Utility](../../deploy-packages-by-using-the-deployment-utility.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00c11-146">参照</span><span class="sxs-lookup"><span data-stu-id="00c11-146">See Also</span></span>  
 [<span data-ttu-id="00c11-147">配置ユーティリティを作成する</span><span class="sxs-lookup"><span data-stu-id="00c11-147">Create a Deployment Utility</span></span>](../../create-a-deployment-utility.md)  
  
  
