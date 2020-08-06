---
title: パラメーターを作成する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.parameterwindow.f1
ms.assetid: cd5d675b-dd5d-49cc-8b1f-dc717a973f99
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a26ae08c08a32b0593be8c9a2777b7cfe9c884fa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633247"
---
# <a name="create-parameters"></a><span data-ttu-id="0072f-102">パラメーターを作成する</span><span class="sxs-lookup"><span data-stu-id="0072f-102">Create Parameters</span></span>
  <span data-ttu-id="0072f-103">プロジェクト パラメーターおよびパッケージ パラメーターを作成するには、[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] を使用します。</span><span class="sxs-lookup"><span data-stu-id="0072f-103">You use [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to create project parameters and package parameters.</span></span> <span data-ttu-id="0072f-104">以下の手順では、パッケージ/プロジェクト パラメーターを作成する方法を詳細に説明します。</span><span class="sxs-lookup"><span data-stu-id="0072f-104">The following procedures provide step-by-step instructions for creating package/project parameters.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0072f-105">以前のバージョンの [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] を使用して作成したプロジェクトをプロジェクトの配置モデルに変換する場合は、**Integration Services プロジェクト変換ウィザード**を使用して、構成に基づいたパラメーターを作成できます。</span><span class="sxs-lookup"><span data-stu-id="0072f-105">If you are converting a project that you created using an earlier version of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] to the project deployment model, you can use the **Integration Services Project Conversion Wizard** to create parameters based on configurations.</span></span> <span data-ttu-id="0072f-106">詳細については、「 [Integration Services サーバーへのプロジェクトの配置](../../2014/integration-services/deploy-projects-to-integration-services-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0072f-106">For more information, see [Deploy Projects to Integration Services Server](../../2014/integration-services/deploy-projects-to-integration-services-server.md).</span></span>  
  
### <a name="to-create-package-parameters"></a><span data-ttu-id="0072f-107">パッケージ パラメーターを作成するには</span><span class="sxs-lookup"><span data-stu-id="0072f-107">To create package parameters</span></span>  
  
1.  <span data-ttu-id="0072f-108">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] でパッケージを開き、SSIS デザイナーの **[パラメーター]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="0072f-108">Open the package in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], and then click the **Parameters** tab in the SSIS Designer.</span></span>  
  
     <span data-ttu-id="0072f-109">![パッケージの [パラメーター] タブ](media/denali-package-parameters.gif "パッケージの [パラメーター] タブ")</span><span class="sxs-lookup"><span data-stu-id="0072f-109">![Package Parameters Tab](media/denali-package-parameters.gif "Package Parameters Tab")</span></span>  
  
2.  <span data-ttu-id="0072f-110">ツール バーの **[パラメーターの追加]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="0072f-110">Click the **Add Parameter** button on the toolbar.</span></span>  
  
     <span data-ttu-id="0072f-111">![ツールバーボタンの追加](media/denali-parameter-add.gif "[追加] ツール バー ボタン")</span><span class="sxs-lookup"><span data-stu-id="0072f-111">![Add Toolbar Button](media/denali-parameter-add.gif "Add Toolbar Button")</span></span>  
  
3.  <span data-ttu-id="0072f-112">一覧で直接、または **[プロパティ]** ウィンドウを使用して、**[名前]**、**[データ型]**、**[値]**、**[区別する]**、**[必須]** の各プロパティに値を入力します。</span><span class="sxs-lookup"><span data-stu-id="0072f-112">Enter values for the **Name**, **Data Type**, **Value**, **Sensitive**, and **Required** properties in the list itself or in the **Properties** window.</span></span> <span data-ttu-id="0072f-113">次の表では、これらのプロパティについて説明します。</span><span class="sxs-lookup"><span data-stu-id="0072f-113">The following table describes these properties.</span></span>  
  
    |<span data-ttu-id="0072f-114">プロパティ</span><span class="sxs-lookup"><span data-stu-id="0072f-114">Property</span></span>|<span data-ttu-id="0072f-115">説明</span><span class="sxs-lookup"><span data-stu-id="0072f-115">Description</span></span>|  
    |--------------|-----------------|  
    |<span data-ttu-id="0072f-116">名前</span><span class="sxs-lookup"><span data-stu-id="0072f-116">Name</span></span>|<span data-ttu-id="0072f-117">パラメーターの名前。</span><span class="sxs-lookup"><span data-stu-id="0072f-117">The name of the parameter.</span></span>|  
    |<span data-ttu-id="0072f-118">データ型</span><span class="sxs-lookup"><span data-stu-id="0072f-118">Data type</span></span>|<span data-ttu-id="0072f-119">パラメーターのデータ型です。</span><span class="sxs-lookup"><span data-stu-id="0072f-119">The data type of the parameter.</span></span>|  
    |<span data-ttu-id="0072f-120">既定値</span><span class="sxs-lookup"><span data-stu-id="0072f-120">Default value</span></span>|<span data-ttu-id="0072f-121">設計時に割り当てられたパラメーターの既定値。</span><span class="sxs-lookup"><span data-stu-id="0072f-121">The default value for the parameter assigned at design time.</span></span> <span data-ttu-id="0072f-122">これは設計時の既定値とも呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="0072f-122">This is also known as the design default.</span></span>|  
    |<span data-ttu-id="0072f-123">重要</span><span class="sxs-lookup"><span data-stu-id="0072f-123">Sensitive</span></span>|<span data-ttu-id="0072f-124">機密性の高いパラメーター値はカタログ内で暗号化され、Transact-SQL または SQL Server Management Studio で表示する際は NULL 値として表示されます。</span><span class="sxs-lookup"><span data-stu-id="0072f-124">Sensitive parameter values are encrypted in the catalog and appear as a NULL value when viewed with Transact-SQL or SQL Server Management Studio.</span></span>|  
    |<span data-ttu-id="0072f-125">必須</span><span class="sxs-lookup"><span data-stu-id="0072f-125">Required</span></span>|<span data-ttu-id="0072f-126">パッケージを実行する前に、設計上の既定値以外の値を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0072f-126">Requires that a value, other than the design default, is specified before the package can execute.</span></span>|  
    |<span data-ttu-id="0072f-127">説明</span><span class="sxs-lookup"><span data-stu-id="0072f-127">Description</span></span>|<span data-ttu-id="0072f-128">管理しやすさを考慮した、パラメーターの説明。</span><span class="sxs-lookup"><span data-stu-id="0072f-128">For maintainability, the description of the parameter.</span></span> <span data-ttu-id="0072f-129">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] では、該当するパラメーター ウィンドウでパラメーターを選択したときに、Visual Studio プロパティ ウィンドウでパラメーターの説明を設定します。</span><span class="sxs-lookup"><span data-stu-id="0072f-129">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], set the parameter description in the Visual Studio Properties window when the parameter is selected in the applicable parameters window.</span></span>|  
  
    > [!NOTE]  
    >  <span data-ttu-id="0072f-130">プロジェクトをカタログに配置すると、いくつかのプロパティがプロジェクトに関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="0072f-130">When you deploy a project to the catalog, several more properties become associated with the project.</span></span> <span data-ttu-id="0072f-131">カタログ内のすべてのパラメーターのすべてのプロパティを表示するには、[catalog.object_parameters &#40;SSISDB Database&#41;](/sql/integration-services/system-views/catalog-object-parameters-ssisdb-database) ビューを使用します。</span><span class="sxs-lookup"><span data-stu-id="0072f-131">To see all properties for all parameters in the catalog, use the [catalog.object_parameters &#40;SSISDB Database&#41;](/sql/integration-services/system-views/catalog-object-parameters-ssisdb-database) view.</span></span>  
  
4.  <span data-ttu-id="0072f-132">プロジェクトを保存して、変更をパラメーターに保存します。</span><span class="sxs-lookup"><span data-stu-id="0072f-132">Save the project to save changes to parameters.</span></span> <span data-ttu-id="0072f-133">パラメーターの値はプロジェクト ファイルに格納されます。</span><span class="sxs-lookup"><span data-stu-id="0072f-133">Parameter values are stored in the project file.</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="0072f-134">リストで直接編集することも、**[プロパティ]** ウィンドウを使用してパラメーターのプロパティの値を変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="0072f-134">You can in-place edit in the list or use the **Properties** window to modify the values of parameter properties.</span></span> <span data-ttu-id="0072f-135">**[削除] \(X)** ツール バー ボタンを使用して、パラメーターを削除できます。</span><span class="sxs-lookup"><span data-stu-id="0072f-135">You can delete a parameter by using the **Delete (X)** toolbar button.</span></span> <span data-ttu-id="0072f-136">ツール バーの最後のボタンを使用すると、[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] でパッケージを実行するときにのみ使用されるパラメーターの値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="0072f-136">Using the last toolbar button, you can specify a value for a parameter that is used only when you execute the package in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)].</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="0072f-137">プロジェクトを [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] で開かずにパッケージ ファイルを再度開くと、**[パラメーター]** タブは空になり、無効になります。</span><span class="sxs-lookup"><span data-stu-id="0072f-137">If you re-open the package file without opening the project in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], the **Parameters** tab will be empty and disabled.</span></span>  
  
### <a name="to-create-project-parameters"></a><span data-ttu-id="0072f-138">プロジェクト パラメーターを作成するには</span><span class="sxs-lookup"><span data-stu-id="0072f-138">To create project parameters</span></span>  
  
1.  <span data-ttu-id="0072f-139">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] でプロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="0072f-139">Open the project in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)].</span></span>  
  
2.  <span data-ttu-id="0072f-140">ソリューション エクスプローラーで **[Project.params]** を右クリックして **[開く]** をクリックするか、または **[Project.params]** をダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="0072f-140">Right-click **Project.params** in Solution Explorer, and then click **Open** (OR) double-click **Project.params** to open it.</span></span>  
  
     <span data-ttu-id="0072f-141">![[プロジェクト パラメーター] ウィンドウ](media/denali-project-parameters.gif "[プロジェクト パラメーター] ウィンドウ")</span><span class="sxs-lookup"><span data-stu-id="0072f-141">![Project Parameters Window](media/denali-project-parameters.gif "Project Parameters Window")</span></span>  
  
3.  <span data-ttu-id="0072f-142">ツール バーの **[パラメーターの追加]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="0072f-142">Click the **Add Parameter** button on the toolbar.</span></span>  
  
     <span data-ttu-id="0072f-143">![ツールバーボタンの追加](media/denali-parameter-add.gif "[追加] ツール バー ボタン")</span><span class="sxs-lookup"><span data-stu-id="0072f-143">![Add Toolbar Button](media/denali-parameter-add.gif "Add Toolbar Button")</span></span>  
  
4.  <span data-ttu-id="0072f-144">**[名前]**、**[データ型]**、**[値]**、**[区別する]**、**[必須]** の各プロパティに値を入力します。</span><span class="sxs-lookup"><span data-stu-id="0072f-144">Enter values for the **Name**, **Data Type**, **Value**, **Sensitive**, and **Required** properties.</span></span>  
  
    |<span data-ttu-id="0072f-145">プロパティ</span><span class="sxs-lookup"><span data-stu-id="0072f-145">Property</span></span>|<span data-ttu-id="0072f-146">説明</span><span class="sxs-lookup"><span data-stu-id="0072f-146">Description</span></span>|  
    |--------------|-----------------|  
    |<span data-ttu-id="0072f-147">名前</span><span class="sxs-lookup"><span data-stu-id="0072f-147">Name</span></span>|<span data-ttu-id="0072f-148">パラメーターの名前。</span><span class="sxs-lookup"><span data-stu-id="0072f-148">The name of the parameter.</span></span>|  
    |<span data-ttu-id="0072f-149">データ型</span><span class="sxs-lookup"><span data-stu-id="0072f-149">Data type</span></span>|<span data-ttu-id="0072f-150">パラメーターのデータ型です。</span><span class="sxs-lookup"><span data-stu-id="0072f-150">The data type of the parameter.</span></span>|  
    |<span data-ttu-id="0072f-151">既定値</span><span class="sxs-lookup"><span data-stu-id="0072f-151">Default value</span></span>|<span data-ttu-id="0072f-152">設計時に割り当てられたパラメーターの既定値。</span><span class="sxs-lookup"><span data-stu-id="0072f-152">The default value for the parameter assigned at design time.</span></span> <span data-ttu-id="0072f-153">これは設計時の既定値とも呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="0072f-153">This is also known as the design default.</span></span>|  
    |<span data-ttu-id="0072f-154">重要</span><span class="sxs-lookup"><span data-stu-id="0072f-154">Sensitive</span></span>|<span data-ttu-id="0072f-155">機密性の高いパラメーター値はカタログ内で暗号化され、Transact-SQL または SQL Server Management Studio で表示する際は NULL 値として表示されます。</span><span class="sxs-lookup"><span data-stu-id="0072f-155">Sensitive parameter values are encrypted in the catalog and appear as a NULL value when viewed with Transact-SQL or SQL Server Management Studio.</span></span>|  
    |<span data-ttu-id="0072f-156">必須</span><span class="sxs-lookup"><span data-stu-id="0072f-156">Required</span></span>|<span data-ttu-id="0072f-157">パッケージを実行する前に、設計上の既定値以外の値を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0072f-157">Requires that a value, other than the design default, is specified before the package can execute.</span></span>|  
    |<span data-ttu-id="0072f-158">説明</span><span class="sxs-lookup"><span data-stu-id="0072f-158">Description</span></span>|<span data-ttu-id="0072f-159">管理しやすさを考慮した、パラメーターの説明。</span><span class="sxs-lookup"><span data-stu-id="0072f-159">For maintainability, the description of the parameter.</span></span> <span data-ttu-id="0072f-160">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] では、該当するパラメーター ウィンドウでパラメーターを選択したときに、Visual Studio プロパティ ウィンドウでパラメーターの説明を設定します。</span><span class="sxs-lookup"><span data-stu-id="0072f-160">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], set the parameter description in the Visual Studio Properties window when the parameter is selected in the applicable parameters window.</span></span>|  
  
5.  <span data-ttu-id="0072f-161">プロジェクトを保存して、変更をパラメーターに保存します。</span><span class="sxs-lookup"><span data-stu-id="0072f-161">Save the project to save changes to parameters.</span></span> <span data-ttu-id="0072f-162">パラメーター値はプロジェクト ファイルの構成に格納されます。</span><span class="sxs-lookup"><span data-stu-id="0072f-162">Parameter values are stored in configurations in the project file.</span></span> <span data-ttu-id="0072f-163">プロジェクト ファイルを保存して、パラメーター値の変更をディスクにコミットしてください。</span><span class="sxs-lookup"><span data-stu-id="0072f-163">Save the project file to commit to disk any changes in the parameter values.</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="0072f-164">リストで直接編集することも、**[プロパティ]** ウィンドウを使用してパラメーターのプロパティの値を変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="0072f-164">You can in-place edit in the list or use the **Properties** window to modify the values of parameter properties.</span></span> <span data-ttu-id="0072f-165">**[削除] \(X)** ツール バー ボタンを使用して、パラメーターを削除できます。</span><span class="sxs-lookup"><span data-stu-id="0072f-165">You can delete a parameter by using the **Delete (X)** toolbar button.</span></span> <span data-ttu-id="0072f-166">ツール バーの最後のボタンを使用すると、**[パラメーター値の管理]** ダイアログ ボックスを開いて、[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] でパッケージを実行するときにのみ使用されるパラメーターの値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="0072f-166">Using the last toolbar button to open the **Manage Parameter Values** dialog box, you can specify a value for a parameter that is used only when you execute the package in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0072f-167">参照</span><span class="sxs-lookup"><span data-stu-id="0072f-167">See Also</span></span>  
 [<span data-ttu-id="0072f-168">SSIS&#41; パラメーターの Integration Services &#40;</span><span class="sxs-lookup"><span data-stu-id="0072f-168">Integration Services &#40;SSIS&#41; Parameters</span></span>](integration-services-ssis-package-and-project-parameters.md)  
  
  
