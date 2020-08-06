---
title: 配置ユーティリティを作成する |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- deploying packages [Integration Services], deployment utility
- deployment utility [Integration Services]
ms.assetid: 354322a4-ae8c-4d92-8e71-42d29dbd0614
author: chugugrace
ms.author: chugu
ms.openlocfilehash: bdf1328d440920fed98e5fa1d16024c5fec32cbb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641797"
---
# <a name="create-a-deployment-utility"></a><span data-ttu-id="3b0ae-102">Create a Deployment Utility</span><span class="sxs-lookup"><span data-stu-id="3b0ae-102">Create a Deployment Utility</span></span>
  <span data-ttu-id="3b0ae-103">パッケージ配置の最初の手順は、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトの配置ユーティリティを作成することです。</span><span class="sxs-lookup"><span data-stu-id="3b0ae-103">The first step in deploying packages is to create a deployment utility for an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project.</span></span> <span data-ttu-id="3b0ae-104">配置ユーティリティは、別のサーバーに [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトのパッケージを配置する際に必要となるファイルを格納したフォルダーです。</span><span class="sxs-lookup"><span data-stu-id="3b0ae-104">The deployment utility is a folder that contains the files you need to deploy the packages in an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project on a different server.</span></span> <span data-ttu-id="3b0ae-105">配置ユーティリティは [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトが格納されているコンピューター上に作成されます。</span><span class="sxs-lookup"><span data-stu-id="3b0ae-105">The deployment utility is created on the computer on which the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project is stored.</span></span>  
  
 <span data-ttu-id="3b0ae-106">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトのパッケージ配置ユーティリティを作成するには、最初に配置ユーティリティ作成用のビルド プロセスを設定してから、プロジェクトをビルドします。</span><span class="sxs-lookup"><span data-stu-id="3b0ae-106">You create a package deployment utility for an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project by first configuring the build process to create a deployment utility, and then building the project.</span></span> <span data-ttu-id="3b0ae-107">プロジェクトをビルドすると、プロジェクトのすべてのパッケージおよびパッケージの構成が自動的に追加されます。</span><span class="sxs-lookup"><span data-stu-id="3b0ae-107">When you build the project, all packages and package configurations in the project are automatically included.</span></span> <span data-ttu-id="3b0ae-108">Readme ファイルなどのファイルをプロジェクトに追加して配置するには、 **プロジェクトの** [その他] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] フォルダーにファイルを格納します。</span><span class="sxs-lookup"><span data-stu-id="3b0ae-108">To deploy additional files such as a Readme file with the project, place the files in the **Miscellaneous** folder of the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project.</span></span> <span data-ttu-id="3b0ae-109">プロジェクトのビルド時に、これらのファイルも自動的に追加されます。</span><span class="sxs-lookup"><span data-stu-id="3b0ae-109">When the project is built, these files are also automatically included.</span></span>  
  
 <span data-ttu-id="3b0ae-110">プロジェクト配置は個別に設定できます。</span><span class="sxs-lookup"><span data-stu-id="3b0ae-110">You can configure each project deployment differently.</span></span> <span data-ttu-id="3b0ae-111">プロジェクトをビルドしてパッケージ配置ユーティリティを作成する前に、配置ユーティリティのプロパティを設定して、プロジェクトのパッケージの配置方法をカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="3b0ae-111">Before you build the project and create the package deployment utility, you can set the properties on the deployment utility to customize the way the packages in the project will be deployed.</span></span> <span data-ttu-id="3b0ae-112">たとえば、プロジェクトの配置時にパッケージの構成を更新するかどうかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="3b0ae-112">For example, you can specify whether package configurations can be updated when the project is deployed.</span></span> <span data-ttu-id="3b0ae-113">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトのプロパティにアクセスするには、プロジェクトを右クリックして **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3b0ae-113">To access the properties of an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project, right-click the project and click **Properties**.</span></span>  
  
 <span data-ttu-id="3b0ae-114">次の表に、配置ユーティリティのプロパティの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="3b0ae-114">The following table lists the deployment utility properties.</span></span>  
  
|<span data-ttu-id="3b0ae-115">プロパティ</span><span class="sxs-lookup"><span data-stu-id="3b0ae-115">Property</span></span>|<span data-ttu-id="3b0ae-116">説明</span><span class="sxs-lookup"><span data-stu-id="3b0ae-116">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="3b0ae-117">AllowConfigurationChange</span><span class="sxs-lookup"><span data-stu-id="3b0ae-117">AllowConfigurationChange</span></span>|<span data-ttu-id="3b0ae-118">配置の際に構成を更新するかどうかを指定する値。</span><span class="sxs-lookup"><span data-stu-id="3b0ae-118">A value that specifies whether configurations can be updated during deployment.</span></span>|  
|<span data-ttu-id="3b0ae-119">CreateDeploymentUtility</span><span class="sxs-lookup"><span data-stu-id="3b0ae-119">CreateDeploymentUtility</span></span>|<span data-ttu-id="3b0ae-120">プロジェクトのビルド時にパッケージ配置ユーティリティを作成するかどうかを指定する値。</span><span class="sxs-lookup"><span data-stu-id="3b0ae-120">A value that specifies whether a package deployment utility is created when the project is built.</span></span> <span data-ttu-id="3b0ae-121">配置ユーティリティを作成するには、このプロパティが `True` である必要があります。</span><span class="sxs-lookup"><span data-stu-id="3b0ae-121">This property must be `True` to create a deployment utility.</span></span>|  
|<span data-ttu-id="3b0ae-122">DeploymentOutputPath</span><span class="sxs-lookup"><span data-stu-id="3b0ae-122">DeploymentOutputPath</span></span>|<span data-ttu-id="3b0ae-123">配置ユーティリティの場所。 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトから見た相対的な位置。</span><span class="sxs-lookup"><span data-stu-id="3b0ae-123">The location, relative to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project, of the deployment utility.</span></span>|  
  
 <span data-ttu-id="3b0ae-124">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトをビルドすると、\<project name>.SSISDeploymentManifest.xml というマニフェスト ファイルが作成され、プロジェクトのパッケージのコピーおよびパッケージの依存関係と共に、プロジェクトの bin\Deployment フォルダーまたは DeploymentOutputPath プロパティで指定された場所に格納されます。</span><span class="sxs-lookup"><span data-stu-id="3b0ae-124">When you build an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project, a manifest file, \<project name>.SSISDeploymentManifest.xml, is created and added, together with copies of the project packages and package dependencies, to the bin\Deployment folder in the project, or to the location specified in the DeploymentOutputPath property.</span></span> <span data-ttu-id="3b0ae-125">マニフェスト ファイルには、プロジェクトに含まれるパッケージ、パッケージの構成、およびその他のファイルの一覧が記述されます。</span><span class="sxs-lookup"><span data-stu-id="3b0ae-125">The manifest file lists the packages, the package configurations, and any miscellaneous files in the project.</span></span>  
  
 <span data-ttu-id="3b0ae-126">配置フォルダーの内容は、プロジェクトをビルドするたびに更新されます。</span><span class="sxs-lookup"><span data-stu-id="3b0ae-126">The content of the deployment folder is refreshed every time that you build the project.</span></span> <span data-ttu-id="3b0ae-127">つまり、このフォルダーに保存されているフォルダーのうち、ビルド プロセスで再度このフォルダーにコピーされなかったファイルはすべて、削除されます。</span><span class="sxs-lookup"><span data-stu-id="3b0ae-127">This means that any file saved to this folder that is not copied to the folder again by the build process will be deleted.</span></span> <span data-ttu-id="3b0ae-128">たとえば、配置フォルダーに保存されたパッケージ構成ファイルは削除されます。</span><span class="sxs-lookup"><span data-stu-id="3b0ae-128">For example, package configuration files saved to the deployment folders will be deleted.</span></span>  
  
### <a name="to-create-a-package-deployment-utility"></a><span data-ttu-id="3b0ae-129">パッケージ配置ユーティリティを作成するには</span><span class="sxs-lookup"><span data-stu-id="3b0ae-129">To create a package deployment utility</span></span>  
  
1.  <span data-ttu-id="3b0ae-130">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で、パッケージ配置ユーティリティを作成する [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトが含まれているソリューションを開きます。</span><span class="sxs-lookup"><span data-stu-id="3b0ae-130">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the solution that contains the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project for which you want to create a package deployment utility.</span></span>  
  
2.  <span data-ttu-id="3b0ae-131">プロジェクトを右クリックして、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3b0ae-131">Right-click the project and click **Properties**.</span></span>  
  
3.  <span data-ttu-id="3b0ae-132">**[\<project name> プロパティ ページ]** ダイアログ ボックスで、 **[配置ユーティリティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3b0ae-132">In the **\<project name> Property Pages** dialog box, click **Deployment Utility**.</span></span>  
  
4.  <span data-ttu-id="3b0ae-133">パッケージの配置時にパッケージの構成を更新するには、 **Allowconfigurationchanges**をに設定 `True` します。</span><span class="sxs-lookup"><span data-stu-id="3b0ae-133">To update package configurations when packages are deployed, set **AllowConfigurationChanges** to `True`.</span></span>  
  
5.  <span data-ttu-id="3b0ae-134">`CreateDeploymentUtility` を `True` に設定します。</span><span class="sxs-lookup"><span data-stu-id="3b0ae-134">Set `CreateDeploymentUtility` to `True`.</span></span>  
  
6.  <span data-ttu-id="3b0ae-135">必要に応じて、`DeploymentOutputPath` プロパティを変更して、配置ユーティリティの場所を更新します。</span><span class="sxs-lookup"><span data-stu-id="3b0ae-135">Optionally, update the location of the deployment utility by modifying the `DeploymentOutputPath` property.</span></span>  
  
7.  <span data-ttu-id="3b0ae-136">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3b0ae-136">Click **OK**.</span></span>  
  
8.  <span data-ttu-id="3b0ae-137">ソリューション エクスプローラーで、プロジェクトを右クリックし、 **[ビルド]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3b0ae-137">In Solution Explorer, right-click the project, and then click **Build**.</span></span>  
  
9. <span data-ttu-id="3b0ae-138">ビルドの進捗状況とエラーが **[出力]** ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="3b0ae-138">View the build progress and build errors in the **Output** window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b0ae-139">参照</span><span class="sxs-lookup"><span data-stu-id="3b0ae-139">See Also</span></span>  
 <span data-ttu-id="3b0ae-140">[パッケージの構成](../../2014/integration-services/package-configurations.md) </span><span class="sxs-lookup"><span data-stu-id="3b0ae-140">[Package Configurations](../../2014/integration-services/package-configurations.md) </span></span>  
 <span data-ttu-id="3b0ae-141">[パッケージ構成の作成](../../2014/integration-services/create-package-configurations.md) </span><span class="sxs-lookup"><span data-stu-id="3b0ae-141">[Create Package Configurations](../../2014/integration-services/create-package-configurations.md) </span></span>  
 <span data-ttu-id="3b0ae-142">[配置ユーティリティを使用してパッケージを配置する](../../2014/integration-services/deploy-packages-by-using-the-deployment-utility.md) </span><span class="sxs-lookup"><span data-stu-id="3b0ae-142">[Deploy Packages by Using the Deployment Utility](../../2014/integration-services/deploy-packages-by-using-the-deployment-utility.md) </span></span>  
 [<span data-ttu-id="3b0ae-143">SSIS&#41;&#40;パッケージの配置</span><span class="sxs-lookup"><span data-stu-id="3b0ae-143">Package Deployment &#40;SSIS&#41;</span></span>](packages/legacy-package-deployment-ssis.md)  
  
  
