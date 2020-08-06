---
title: 配置スクリプトを作成するために使用する入力ファイルについてMicrosoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- input files [Analysis Services]
- Analysis Services Deployment Wizard, scripts
- deploying [Analysis Services], input files
- Analysis Services Deployment Wizard, input files
- scripts [Analysis Services], deployment
- Analysis Services deployments, input files
- modifying input files
ms.assetid: 20e080cd-6a0e-4591-b022-ea4cd3638e36
author: minewiskan
ms.author: owend
ms.openlocfilehash: 34695993d4f153c6c0b97fef744d92c682517c99
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641341"
---
# <a name="understanding-the-input-files-used-to-create-the-deployment-script"></a><span data-ttu-id="f05ca-102">配置スクリプトを作成するための入力ファイルについて</span><span class="sxs-lookup"><span data-stu-id="f05ca-102">Understanding the Input Files Used to Create the Deployment Script</span></span>
  <span data-ttu-id="f05ca-103">プロジェクトをビルドすると [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 、に [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] よってプロジェクトの XML ファイルが生成されます。</span><span class="sxs-lookup"><span data-stu-id="f05ca-103">When you build a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project, [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] generates XML files for the project.</span></span> [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] <span data-ttu-id="f05ca-104">では、これらの XML ファイルは [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトの出力フォルダーに保存されます。</span><span class="sxs-lookup"><span data-stu-id="f05ca-104">puts these XML files in the Output folder of the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project.</span></span> <span data-ttu-id="f05ca-105">既定では、出力は \Bin フォルダーに対して行われます。</span><span class="sxs-lookup"><span data-stu-id="f05ca-105">By default output is out in the \Bin folder.</span></span> <span data-ttu-id="f05ca-106">次の表は、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] で作成される XML ファイルを示しています。</span><span class="sxs-lookup"><span data-stu-id="f05ca-106">The following table lists the XML files that [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] creates.</span></span>  
  
|<span data-ttu-id="f05ca-107">XMLA ファイル</span><span class="sxs-lookup"><span data-stu-id="f05ca-107">XMLA file</span></span>|<span data-ttu-id="f05ca-108">説明</span><span class="sxs-lookup"><span data-stu-id="f05ca-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f05ca-109">\<*project name*>. asdatabase</span><span class="sxs-lookup"><span data-stu-id="f05ca-109">\<*project name*>.asdatabase</span></span>|<span data-ttu-id="f05ca-110">プロジェクト内のすべての [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] オブジェクトの宣言定義が含まれています。</span><span class="sxs-lookup"><span data-stu-id="f05ca-110">Contains the declarative definitions for all the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] objects in the project.</span></span>|  
|<span data-ttu-id="f05ca-111">\<*project name*>。 deploymenttargets</span><span class="sxs-lookup"><span data-stu-id="f05ca-111">\<*project name*>.deploymenttargets</span></span>|<span data-ttu-id="f05ca-112">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] オブジェクトが作成される [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスおよびデータベースの名前が含まれています。</span><span class="sxs-lookup"><span data-stu-id="f05ca-112">Contains the name of the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance and database in which the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] objects will be created.</span></span>|  
|<span data-ttu-id="f05ca-113">\<*project name*>. configsettings</span><span class="sxs-lookup"><span data-stu-id="f05ca-113">\<*project name*>.configsettings</span></span>|<span data-ttu-id="f05ca-114">データ ソース接続情報やオブジェクト格納場所など、環境に固有の設定が含まれています。</span><span class="sxs-lookup"><span data-stu-id="f05ca-114">Contains environment specific settings, such as data source connection information and object storage locations.</span></span> <span data-ttu-id="f05ca-115">このファイルの設定は、. asdatabase ファイルの設定よりも優先され \<*project name*> ます。</span><span class="sxs-lookup"><span data-stu-id="f05ca-115">Settings in this file override settings in the \<*project name*>.asdatabase file.</span></span>|  
|<span data-ttu-id="f05ca-116">\<*project name*>. deploymentoptions</span><span class="sxs-lookup"><span data-stu-id="f05ca-116">\<*project name*>.deploymentoptions</span></span>|<span data-ttu-id="f05ca-117">配置がトランザクションであるかどうかや、配置したオブジェクトを配置後に処理するかどうかなどの配置オプションが含まれています。</span><span class="sxs-lookup"><span data-stu-id="f05ca-117">Contains deployment options, such as whether deployment is transactional and whether deployed objects should be processed after deployment.</span></span>|  
  
> [!NOTE]  
>  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] <span data-ttu-id="f05ca-118">では、プロジェクト ファイルにパスワードは保存されません。</span><span class="sxs-lookup"><span data-stu-id="f05ca-118">never stores passwords in its project files.</span></span>  
  
## <a name="modifying-the-input-files"></a><span data-ttu-id="f05ca-119">入力ファイルの変更</span><span class="sxs-lookup"><span data-stu-id="f05ca-119">Modifying the Input Files</span></span>  
 <span data-ttu-id="f05ca-120">入力ファイル内の値または入力ファイルから取得された値を変更することにより、配置先、構成設定、および配置オプションを変更できます。このとき、 \<*project name*> asdatabase ファイル全体 (または、既存のデータベースからスクリプトを生成する場合は、XMLA スクリプトファイル全体) を編集する必要がありません。 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f05ca-120">Modifying the values in the input files, or the values retrieved from the input files, makes it possible to change the deployment destination, the configuration settings, and deployment options without editing the whole \<*project name*>.asdatabase file (or a whole XMLA script file if you generate a script from an existing [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database).</span></span> <span data-ttu-id="f05ca-121">個々のファイルを変更できると、さまざまな目的に合わせてさまざまな配置スクリプトを簡単に作成できます。</span><span class="sxs-lookup"><span data-stu-id="f05ca-121">Being able to modify individual files lets you easily create different deployment scripts for different purposes.</span></span>  
  
 <span data-ttu-id="f05ca-122">次のトピックでは、さまざまな入力ファイル内の値を変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f05ca-122">The following topics explain how to modify values in the various input files:</span></span>  
  
-   [<span data-ttu-id="f05ca-123">インストール先の指定</span><span class="sxs-lookup"><span data-stu-id="f05ca-123">Specifying the Installation Target</span></span>](deployment-script-files-specifying-the-installation-target.md)  
  
-   [<span data-ttu-id="f05ca-124">パーティションおよびロールの配置オプションの指定</span><span class="sxs-lookup"><span data-stu-id="f05ca-124">Specifying Partition and Role Deployment Options</span></span>](deployment-script-files-partition-and-role-deployment-options.md)  
  
-   [<span data-ttu-id="f05ca-125">ソリューションの配置に関する構成設定の指定</span><span class="sxs-lookup"><span data-stu-id="f05ca-125">Specifying Configuration Settings for Solution Deployment</span></span>](deployment-script-files-solution-deployment-config-settings.md)  
  
-   [<span data-ttu-id="f05ca-126">処理オプションの指定</span><span class="sxs-lookup"><span data-stu-id="f05ca-126">Specifying Processing Options</span></span>](deployment-script-files-specifying-processing-options.md)  
  
## <a name="see-also"></a><span data-ttu-id="f05ca-127">参照</span><span class="sxs-lookup"><span data-stu-id="f05ca-127">See Also</span></span>  
 <span data-ttu-id="f05ca-128">[Analysis Services 配置ウィザードの実行](running-the-analysis-services-deployment-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="f05ca-128">[Running the Analysis Services Deployment Wizard](running-the-analysis-services-deployment-wizard.md) </span></span>  
 [<span data-ttu-id="f05ca-129">Analysis Services 配置スクリプトについて</span><span class="sxs-lookup"><span data-stu-id="f05ca-129">Understanding the Analysis Services Deployment Script</span></span>](understanding-the-analysis-services-deployment-script.md)  
  
  
