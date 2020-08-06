---
title: 処理オプションの指定 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Analysis Services deployments, processing options
- input files [Analysis Services]
- deploying [Analysis Services], processing options
- modifying processing options
- Analysis Services Deployment Wizard, processing options
ms.assetid: e9e50817-908e-4210-bc3d-8e2957568241
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9690aaa7e1d3b3870eb6ab01630b98027263655f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712562"
---
# <a name="specifying-processing-options"></a><span data-ttu-id="9d2ae-102">処理オプションの指定</span><span class="sxs-lookup"><span data-stu-id="9d2ae-102">Specifying Processing Options</span></span>
  <span data-ttu-id="9d2ae-103">配置ウィザードでは、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] deploymentoptions ファイルから処理オプションを読み取ります \<*project name*> 。</span><span class="sxs-lookup"><span data-stu-id="9d2ae-103">The [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Deployment Wizard reads the processing options from the \<*project name*>.deploymentoptions file.</span></span> [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]<span data-ttu-id="9d2ae-104">は、プロジェクトのビルド時にこのファイルを作成し [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="9d2ae-104">creates this file when you build the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project.</span></span> [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]<span data-ttu-id="9d2ae-105">では、[ **Deployment** *\<project name>* **プロパティページ**] ダイアログボックスの [配置] ページで指定された処理オプションを使用して、 \<*project name*> deploymentoptions ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="9d2ae-105">uses the processing options specified on the **Deployment** page of *\<project name>* **Properties Pages** dialog box to create the \<*project name*>.deploymentoptions file.</span></span>  
  
## <a name="reviewing-the-processing-options-for-deployment"></a><span data-ttu-id="9d2ae-106">配置に関する処理オプションの確認</span><span class="sxs-lookup"><span data-stu-id="9d2ae-106">Reviewing the Processing Options for Deployment</span></span>  
 <span data-ttu-id="9d2ae-107">Deploymentoptions ファイル内に格納され \<*project name*> ている構成設定は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="9d2ae-107">The configuration settings stored within the \<*project name*>.deploymentoptions file are as follows:</span></span>  
  
-   <span data-ttu-id="9d2ae-108">**処理方法** この設定では、配置するオブジェクトを配置後に処理するかどうかと、実行する処理の種類を制御します。</span><span class="sxs-lookup"><span data-stu-id="9d2ae-108">**Processing Method** This setting controls whether the deployed objects are processed after deployment and the type of processing that will be performed.</span></span> <span data-ttu-id="9d2ae-109">処理オプションには次の 3 つがあります。</span><span class="sxs-lookup"><span data-stu-id="9d2ae-109">There are three processing options:</span></span>  
  
    -   <span data-ttu-id="9d2ae-110">既定の処理 (既定)</span><span class="sxs-lookup"><span data-stu-id="9d2ae-110">Default processing (default)</span></span>  
  
    -   <span data-ttu-id="9d2ae-111">完全処理</span><span class="sxs-lookup"><span data-stu-id="9d2ae-111">Full processing</span></span>  
  
    -   <span data-ttu-id="9d2ae-112">なし</span><span class="sxs-lookup"><span data-stu-id="9d2ae-112">None</span></span>  
  
-   <span data-ttu-id="9d2ae-113">**書き戻しテーブル オプション**[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトで書き戻しが有効になっている場合、この設定では書き戻しの処理方法を定義します。</span><span class="sxs-lookup"><span data-stu-id="9d2ae-113">**Writeback Table Options** If writeback is enabled in the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project, this setting defines how writeback is handled.</span></span> <span data-ttu-id="9d2ae-114">書き戻しテーブル オプションには次の 3 つがあります。</span><span class="sxs-lookup"><span data-stu-id="9d2ae-114">There are three writeback table options:</span></span>  
  
    -   <span data-ttu-id="9d2ae-115">既定では、書き戻しテーブルが存在する場合、そのテーブルが使用されます。</span><span class="sxs-lookup"><span data-stu-id="9d2ae-115">By default, if a writeback table exists, it will be used.</span></span> <span data-ttu-id="9d2ae-116">書き戻しテーブルが存在しない場合は、新しい書き戻しテーブルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="9d2ae-116">If a writeback table does not exist, a new writeback table will be created.</span></span>  
  
    -   <span data-ttu-id="9d2ae-117">書き戻しテーブルが既に存在する場合、配置は失敗します。</span><span class="sxs-lookup"><span data-stu-id="9d2ae-117">If a writeback table already exists, the deployment fails.</span></span> <span data-ttu-id="9d2ae-118">書き戻しテーブルが存在しない場合は、新しい書き戻しテーブルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="9d2ae-118">If a writeback table does not exist, a new writeback table will be created.</span></span>  
  
    -   <span data-ttu-id="9d2ae-119">書き戻しテーブルが既に存在するかどうかにかかわらず、新しい書き戻しテーブルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="9d2ae-119">Regardless of whether a writeback table already exists, a new writeback table will be created.</span></span> <span data-ttu-id="9d2ae-120">この場合、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 配置ウィザードによって既存のテーブルが削除され、新しい書き戻しテーブルに置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="9d2ae-120">In this case, the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Deployment Wizard will delete any existing table and replace it with a new writeback table.</span></span>  
  
-   <span data-ttu-id="9d2ae-121">**トランザクション配置** この設定では、メタデータ変更および処理コマンドの配置を 1 つのトランザクションで行うか、別々のトランザクションで行うかを制御します。</span><span class="sxs-lookup"><span data-stu-id="9d2ae-121">**Transactional Deployment** This setting controls whether the deployment of metadata changes and process commands occurs in a single transaction or in separate transactions.</span></span>  
  
    -   <span data-ttu-id="9d2ae-122">このオプションが `True` (既定) の場合、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ではすべてのメタデータ変更およびすべての処理コマンドが 1 つのトランザクションで配置されます。</span><span class="sxs-lookup"><span data-stu-id="9d2ae-122">If this option is `True` (default), [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] deploys all metadata changes and all process commands within a single transaction.</span></span>  
  
    -   <span data-ttu-id="9d2ae-123">このオプションが `False` の場合、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ではメタデータ変更が 1 つのトランザクションで配置され、各処理コマンドがそれぞれ別個のトランザクションで配置されます。</span><span class="sxs-lookup"><span data-stu-id="9d2ae-123">If this option is `False`, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] deploys the metadata changes in a single transaction, and deploys each processing command in its own transaction.</span></span>  
  
## <a name="modifying-the-processing-options-for-deployment"></a><span data-ttu-id="9d2ae-124">配置に関する処理オプションの変更</span><span class="sxs-lookup"><span data-stu-id="9d2ae-124">Modifying the Processing Options for Deployment</span></span>  
 <span data-ttu-id="9d2ae-125">ただし、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] deploymentoptions ファイルに格納されているものとは異なる処理オプションを使用して、プロジェクトを配置することが必要になる場合があります。 \<*project name*></span><span class="sxs-lookup"><span data-stu-id="9d2ae-125">However, you may need to deploy the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project using different processing options than those stored in the \<*project name*>.deploymentoptions file.</span></span> <span data-ttu-id="9d2ae-126">たとえば、すべてのオブジェクトを完全に処理するか、既定の処理オプションを使用して処理するか、まったく処理しないようにする必要が生じることがあります。</span><span class="sxs-lookup"><span data-stu-id="9d2ae-126">For example, you may want to have all objects fully processed, or processed using the default processing option, or have no processing occur.</span></span> <span data-ttu-id="9d2ae-127">キューブまたはディメンションが書き込み可能である場合は、新しい書き戻しテーブルまたは既存の書き戻しテーブルのどちらを使用するかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="9d2ae-127">If the cubes or dimensions are write-enabled, you can specify whether a new or existing writeback table be used.</span></span>  
  
 <span data-ttu-id="9d2ae-128">配置時に使用する処理オプションを変更するには、プロジェクトを編集して再作成するか、次の手順のいずれかの方法に従って入力ファイル内の処理オプションを変更できます。</span><span class="sxs-lookup"><span data-stu-id="9d2ae-128">To modify the processing options used during deployment, you can either edit and rebuild the project, or change the processing options in the input file by using one of the methods as described in the following procedure.</span></span>  
  
#### <a name="to-change-processing-options-after-the-input-files-have-been-generated"></a><span data-ttu-id="9d2ae-129">入力ファイルの生成後に処理オプションを変更するには</span><span class="sxs-lookup"><span data-stu-id="9d2ae-129">To change processing options after the input files have been generated</span></span>  
  
-   <span data-ttu-id="9d2ae-130">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 配置ウィザードを対話形式で実行します。</span><span class="sxs-lookup"><span data-stu-id="9d2ae-130">Run the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Deployment Wizard interactively.</span></span> <span data-ttu-id="9d2ae-131">**[処理オプション]** ページで、配置するプロジェクトの処理オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="9d2ae-131">On the **Processing Options** page, specify the processing options for the project being deployed.</span></span>  
  
     <span data-ttu-id="9d2ae-132">または</span><span class="sxs-lookup"><span data-stu-id="9d2ae-132">-or-</span></span>  
  
-   <span data-ttu-id="9d2ae-133">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 配置ウィザードをコマンド プロンプトで実行し、ウィザードを応答ファイル モードで実行するように設定します。</span><span class="sxs-lookup"><span data-stu-id="9d2ae-133">Run the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Deployment Wizard at the command prompt and set the wizard to run in answer file mode.</span></span> <span data-ttu-id="9d2ae-134">応答ファイル モードの詳細については、「 [Analysis Services 配置ウィザードの実行](running-the-analysis-services-deployment-wizard.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9d2ae-134">For more information about answer file mode, see [Running the Analysis Services Deployment Wizard](running-the-analysis-services-deployment-wizard.md).</span></span>  
  
     <span data-ttu-id="9d2ae-135">または</span><span class="sxs-lookup"><span data-stu-id="9d2ae-135">-or-</span></span>  
  
-   <span data-ttu-id="9d2ae-136">任意の \<*project name*> テキストエディターを使用して、deploymentoptions ファイルを変更します。</span><span class="sxs-lookup"><span data-stu-id="9d2ae-136">Modify the \<*project name*>.deploymentoptions file by using any text editor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d2ae-137">参照</span><span class="sxs-lookup"><span data-stu-id="9d2ae-137">See Also</span></span>  
 <span data-ttu-id="9d2ae-138">[インストール先の指定](deployment-script-files-specifying-the-installation-target.md) </span><span class="sxs-lookup"><span data-stu-id="9d2ae-138">[Specifying the Installation Target](deployment-script-files-specifying-the-installation-target.md) </span></span>  
 <span data-ttu-id="9d2ae-139">[パーティションおよびロールの配置オプションの指定](deployment-script-files-partition-and-role-deployment-options.md) </span><span class="sxs-lookup"><span data-stu-id="9d2ae-139">[Specifying Partition and Role Deployment Options](deployment-script-files-partition-and-role-deployment-options.md) </span></span>  
 [<span data-ttu-id="9d2ae-140">ソリューションの配置に関する構成設定の指定</span><span class="sxs-lookup"><span data-stu-id="9d2ae-140">Specifying Configuration Settings for Solution Deployment</span></span>](deployment-script-files-solution-deployment-config-settings.md)  
  
  
