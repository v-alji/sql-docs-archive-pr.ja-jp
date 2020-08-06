---
title: パッケージ構成オーガナイザー |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.packageconfigurationorganizer.f1
helpviewer_keywords:
- Package Configurations Organizer dialog box
ms.assetid: f20ae6cb-9e6a-4d24-88ff-d7a903a4e8d3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 67fdc9ca0faeff57c18fdb6e4d10acca3e9963f1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736523"
---
# <a name="package-configurations-organizer"></a><span data-ttu-id="87209-102">[パッケージ構成オーガナイザー]</span><span class="sxs-lookup"><span data-stu-id="87209-102">Package Configurations Organizer</span></span>
  <span data-ttu-id="87209-103">**[パッケージ構成オーガナイザー]** ダイアログ ボックスを使用すると、パッケージ構成を有効にし、現在のパッケージの構成の一覧を表示して、構成の優先読み込み順序を指定できます。</span><span class="sxs-lookup"><span data-stu-id="87209-103">Use the **Package Configurations Organizer** dialog box to enable package configurations, view a list of configurations for the current package, and specify the preferred order in which the configurations should be loaded.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="87209-104">パッケージ配置モデルの構成を使用できます。</span><span class="sxs-lookup"><span data-stu-id="87209-104">Configurations are available for the package deployment model.</span></span> <span data-ttu-id="87209-105">パラメーターは、プロジェクト配置モデルの構成の代わりに使用します。</span><span class="sxs-lookup"><span data-stu-id="87209-105">Parameters are used in place of configurations for the project deployment model.</span></span> <span data-ttu-id="87209-106">プロジェクト配置モデルを使用すると、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サーバーに [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを配置できます。</span><span class="sxs-lookup"><span data-stu-id="87209-106">The project deployment model enables you to deploy [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] projects to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server.</span></span> <span data-ttu-id="87209-107">配置モデルの詳細については、「 [Deployment of Projects and Packages](packages/deploy-integration-services-ssis-projects-and-packages.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="87209-107">For more information about the deployment models, see [Deployment of Projects and Packages](packages/deploy-integration-services-ssis-projects-and-packages.md).</span></span>  
  
 <span data-ttu-id="87209-108">複数の構成で同じプロパティを更新した場合、構成の一覧内で上の方にある構成の値は、一覧内で下の方にある構成の値に置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="87209-108">If multiple configurations update the same property, values from configurations listed lower in the configuration list will replace values from configurations higher in the list.</span></span> <span data-ttu-id="87209-109">パッケージを実行するときに使用される値は、プロパティに最後に読み込まれた値です。</span><span class="sxs-lookup"><span data-stu-id="87209-109">The last value loaded into the property is the value that is used when the package runs.</span></span> <span data-ttu-id="87209-110">また、パッケージで XML 構成ファイルなどの直接構成と環境変数などの間接構成の組み合わせを使用している場合は、直接構成の場所を指す間接構成を一覧の上の方に置く必要があります。</span><span class="sxs-lookup"><span data-stu-id="87209-110">Also, if the package uses a combination of direct configuration such as an XML configuration file and an indirect configuration such as an environment variable, the indirect configuration that points to the location of the direct configuration must be higher in the list.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="87209-111">パッケージ構成を優先順序で読み込むと、 **[パッケージ構成オーガナイザー]** ダイアログ ボックスに表示された一覧の上から下へと構成が読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="87209-111">When package configurations load in the preferred order, configurations load from the top of the list shown in the **Package Configuration Organizer** dialog box to the bottom of the list.</span></span> <span data-ttu-id="87209-112">ただし、実行時にパッケージ構成が優先順序で読み込まれるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="87209-112">However, at run time, package configurations might not load in the preferred order.</span></span> <span data-ttu-id="87209-113">具体的には、親のパッケージ構成は他の種類の構成の後に読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="87209-113">In particular, Parent Package Configurations load after configurations of other types.</span></span>  
  
 <span data-ttu-id="87209-114">パッケージ オブジェクトのプロパティの値は、パッケージ構成によって実行時に更新されます。</span><span class="sxs-lookup"><span data-stu-id="87209-114">Package configurations update the values of properties of package objects at run time.</span></span> <span data-ttu-id="87209-115">パッケージが読み込まれると、パッケージの開発時に設定された値は、構成の値に置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="87209-115">When a package is loaded, the values from the configurations replace the values that were set when the package was developed.</span></span> [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="87209-116">では、さまざまな種類の構成がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="87209-116">supports different configuration types.</span></span> <span data-ttu-id="87209-117">たとえば、複数の構成を含むことができる XML ファイルや、単一の構成を含む環境変数を使用できます。</span><span class="sxs-lookup"><span data-stu-id="87209-117">For example, you can use an XML file that can contain multiple configurations, or an environment variable that contains a single configuration.</span></span> <span data-ttu-id="87209-118">詳細については、「 [パッケージ構成](../../2014/integration-services/package-configurations.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="87209-118">For more information, see [Package Configurations](../../2014/integration-services/package-configurations.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="87209-119">Options</span><span class="sxs-lookup"><span data-stu-id="87209-119">Options</span></span>  
 <span data-ttu-id="87209-120">**[パッケージの構成を有効にする]**</span><span class="sxs-lookup"><span data-stu-id="87209-120">**Enable package configurations**</span></span>  
 <span data-ttu-id="87209-121">パッケージで使用する構成を選択します。</span><span class="sxs-lookup"><span data-stu-id="87209-121">Select to use configurations with the package.</span></span>  
  
 <span data-ttu-id="87209-122">**[構成名]**</span><span class="sxs-lookup"><span data-stu-id="87209-122">**Configuration Name**</span></span>  
 <span data-ttu-id="87209-123">構成の名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="87209-123">View the name of the configuration.</span></span>  
  
 <span data-ttu-id="87209-124">**[構成の種類]**</span><span class="sxs-lookup"><span data-stu-id="87209-124">**Configuration Type**</span></span>  
 <span data-ttu-id="87209-125">構成を格納する場所の種類を表示します。</span><span class="sxs-lookup"><span data-stu-id="87209-125">View the type of the location where configurations are stored.</span></span>  
  
 <span data-ttu-id="87209-126">**[構成文字列]**</span><span class="sxs-lookup"><span data-stu-id="87209-126">**Configuration String**</span></span>  
 <span data-ttu-id="87209-127">構成値を格納する場所を表示します。</span><span class="sxs-lookup"><span data-stu-id="87209-127">View the location where the configuration values are stored.</span></span> <span data-ttu-id="87209-128">場所には、ファイルのパス、環境変数の名前、親パッケージ変数の名前、レジストリ キー、または [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] テーブルの名前を使用できます。</span><span class="sxs-lookup"><span data-stu-id="87209-128">The location can be the path of a file, the name of an environment variable, the name of a parent package variable, a Registry key, or the name of a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] table.</span></span>  
  
 <span data-ttu-id="87209-129">**[対象になるオブジェクト]**</span><span class="sxs-lookup"><span data-stu-id="87209-129">**Target Object**</span></span>  
 <span data-ttu-id="87209-130">構成を更新するオブジェクトの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="87209-130">View the name of the object that the configuration updates.</span></span> <span data-ttu-id="87209-131">構成が XML 構成ファイルまたは SQL Server テーブルである場合は、構成に複数のオブジェクトを含むことができるため、この列は空白になります。</span><span class="sxs-lookup"><span data-stu-id="87209-131">If the configuration is an XML configuration file or a SQL Server table, the column is blank because the configuration can include multiple objects.</span></span>  
  
 <span data-ttu-id="87209-132">**[対象になるプロパティ]**</span><span class="sxs-lookup"><span data-stu-id="87209-132">**Target Property**</span></span>  
 <span data-ttu-id="87209-133">構成によって変更されるプロパティの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="87209-133">View the name of the property modified by the configuration.</span></span> <span data-ttu-id="87209-134">構成の種類が複数の構成をサポートしている場合、この列は空白になります。</span><span class="sxs-lookup"><span data-stu-id="87209-134">This column is blank if the configuration type supports multiple configurations.</span></span>  
  
 <span data-ttu-id="87209-135">**追加**</span><span class="sxs-lookup"><span data-stu-id="87209-135">**Add**</span></span>  
 <span data-ttu-id="87209-136">パッケージ構成ウィザードを使用して構成を追加します。</span><span class="sxs-lookup"><span data-stu-id="87209-136">Add a configuration by using the Package Configuration Wizard.</span></span>  
  
 <span data-ttu-id="87209-137">**[編集]**</span><span class="sxs-lookup"><span data-stu-id="87209-137">**Edit**</span></span>  
 <span data-ttu-id="87209-138">パッケージ構成ウィザードを再実行することにより、既存の構成を編集します。</span><span class="sxs-lookup"><span data-stu-id="87209-138">Edit an existing configuration by rerunning the Package Configuration Wizard.</span></span>  
  
 <span data-ttu-id="87209-139">**Remove**</span><span class="sxs-lookup"><span data-stu-id="87209-139">**Remove**</span></span>  
 <span data-ttu-id="87209-140">構成を選択してから、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="87209-140">Select a configuration, and then click **Remove**.</span></span>  
  
 <span data-ttu-id="87209-141">**矢印**</span><span class="sxs-lookup"><span data-stu-id="87209-141">**Arrows**</span></span>  
 <span data-ttu-id="87209-142">構成を選択し、上矢印および下矢印を使用して、構成を一覧の上または下に移動します。</span><span class="sxs-lookup"><span data-stu-id="87209-142">Select a configuration and use the up and down arrows to move it up or down in the list.</span></span> <span data-ttu-id="87209-143">構成は、一覧に表示された順序で読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="87209-143">Configurations are loaded in the sequence in which they appear in the list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87209-144">参照</span><span class="sxs-lookup"><span data-stu-id="87209-144">See Also</span></span>  
 [<span data-ttu-id="87209-145">パッケージ構成を作成する</span><span class="sxs-lookup"><span data-stu-id="87209-145">Create Package Configurations</span></span>](../../2014/integration-services/create-package-configurations.md)  
  
  
