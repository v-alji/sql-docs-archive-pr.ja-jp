---
title: 配置ウィザードを使用したモデルソリューションの配置 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Analysis Services Deployment Wizard
- deploying [Analysis Services], Analysis Services Deployment Wizard
- Analysis Services deployments, Analysis Services Deployment Wizard
- Analysis Services Deployment Wizard, about Analysis Services Deployment Wizard
ms.assetid: ff711e8e-971c-43ba-b479-effc034af4a4
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6e3dfd0b727fd917c37aa44aa8fd1d29326aaaa1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711109"
---
# <a name="deploy-model-solutions-using-the-deployment-wizard"></a><span data-ttu-id="552f8-102">Deploy Model Solutions Using the Deployment Wizard</span><span class="sxs-lookup"><span data-stu-id="552f8-102">Deploy Model Solutions Using the Deployment Wizard</span></span>
  <span data-ttu-id="552f8-103">配置ウィザードでは、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトから生成された XML 出力ファイルを [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 入力ファイルとして使用します。</span><span class="sxs-lookup"><span data-stu-id="552f8-103">The [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Deployment Wizard uses the XML output files generated from a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project as input files.</span></span> <span data-ttu-id="552f8-104">このような入力ファイルは簡単に変更して、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトの配置をカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="552f8-104">These input files are easily modifiable to customize the deployment of an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project.</span></span> <span data-ttu-id="552f8-105">生成された配置スクリプトは直ちに実行することも、今後の配置のために保存することもできます。</span><span class="sxs-lookup"><span data-stu-id="552f8-105">The generated deployment script can then either be immediately run or saved for later deployment.</span></span>  
  
 <span data-ttu-id="552f8-106">配置を行うには、ここで説明するウィザードを使用します。</span><span class="sxs-lookup"><span data-stu-id="552f8-106">You can deploy by using the wizard as discussed here.</span></span> <span data-ttu-id="552f8-107">配置を自動化したり、同期機能を使用したりすることもできます。</span><span class="sxs-lookup"><span data-stu-id="552f8-107">You can also automate deployment or use the Synchronize capability.</span></span> <span data-ttu-id="552f8-108">配置するデータベースが大きい場合は、配置先のシステムでパーティションを使用することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="552f8-108">If the deployed database is large, consider using partitions on target systems.</span></span> <span data-ttu-id="552f8-109">分析管理オブジェクト (AMO) を使用してパーティションの作成および設定を自動化することもできます。</span><span class="sxs-lookup"><span data-stu-id="552f8-109">You can also automate partition creation and population by using Analysis Management Objects (AMO).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="552f8-110">XML 出力ファイルおよび配置スクリプトには、データ ソースへの接続文字列内または権限借用の目的で指定されたユーザー ID またはパスワードは含まれません。</span><span class="sxs-lookup"><span data-stu-id="552f8-110">Neither the XML output files nor the deployment script will contain the user id or password if these are specified in either the connection string for a data source or for impersonation purposes.</span></span> <span data-ttu-id="552f8-111">このシナリオの処理ではユーザー ID およびパスワードが必要であるため、この情報を手動で追加します。</span><span class="sxs-lookup"><span data-stu-id="552f8-111">Since these are required for processing purposes in this scenario, you will add this information manually.</span></span> <span data-ttu-id="552f8-112">配置の際に処理を行わない場合は、この接続および権限借用のための情報を必要に応じて配置後に追加できます。</span><span class="sxs-lookup"><span data-stu-id="552f8-112">If the deployment will not include processing, you can add this connection and impersonation information as needed after deployment.</span></span> <span data-ttu-id="552f8-113">配置の際に処理を行う場合は、この情報をウィザードで入力するか、保存した配置スクリプトに追加することができます。</span><span class="sxs-lookup"><span data-stu-id="552f8-113">If the deployment will include processing, you can either add this information within the wizard or in the deployment script after it is saved.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="552f8-114">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="552f8-114">In This Section</span></span>  
 <span data-ttu-id="552f8-115">次のトピックでは、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 配置ウィザードの操作方法、入力ファイル、および配置スクリプトについて説明します。</span><span class="sxs-lookup"><span data-stu-id="552f8-115">The following topics describe how to work with the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Deployment Wizard, the input files, and the deployment script:</span></span>  
  
|<span data-ttu-id="552f8-116">トピック</span><span class="sxs-lookup"><span data-stu-id="552f8-116">Topic</span></span>|<span data-ttu-id="552f8-117">説明</span><span class="sxs-lookup"><span data-stu-id="552f8-117">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="552f8-118">Analysis Services 配置ウィザードの実行</span><span class="sxs-lookup"><span data-stu-id="552f8-118">Running the Analysis Services Deployment Wizard</span></span>](running-the-analysis-services-deployment-wizard.md)|<span data-ttu-id="552f8-119">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 配置ウィザードを実行するさまざまな方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="552f8-119">Describes the various ways in which you can run the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Deployment Wizard.</span></span>|  
|[<span data-ttu-id="552f8-120">配置スクリプトを作成するための入力ファイルについて</span><span class="sxs-lookup"><span data-stu-id="552f8-120">Understanding the Input Files Used to Create the Deployment Script</span></span>](deployment-script-files-input-used-to-create-deployment-script.md)|<span data-ttu-id="552f8-121">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 配置ウィザードによって入力値として使用されるファイルと、その各ファイルに含まれる内容について説明し、各入力ファイル内の値の変更方法について説明するトピックへのリンクを提供します。</span><span class="sxs-lookup"><span data-stu-id="552f8-121">Describes which files the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Deployment Wizard uses as input values, what each of those files contains, and provides links to topics that describe how to modify the values in each of the input files.</span></span>|  
|[<span data-ttu-id="552f8-122">Analysis Services 配置スクリプトについて</span><span class="sxs-lookup"><span data-stu-id="552f8-122">Understanding the Analysis Services Deployment Script</span></span>](understanding-the-analysis-services-deployment-script.md)|<span data-ttu-id="552f8-123">配置スクリプトの内容とスクリプトの実行方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="552f8-123">Describes what the deployment script contains and how the script runs.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="552f8-124">参照</span><span class="sxs-lookup"><span data-stu-id="552f8-124">See Also</span></span>  
 <span data-ttu-id="552f8-125">[XMLA を使用したモデルソリューションの配置](deploy-model-solutions-using-xmla.md) </span><span class="sxs-lookup"><span data-stu-id="552f8-125">[Deploy Model Solutions Using XMLA](deploy-model-solutions-using-xmla.md) </span></span>  
 <span data-ttu-id="552f8-126">[Analysis Services データベースの同期](synchronize-analysis-services-databases.md) </span><span class="sxs-lookup"><span data-stu-id="552f8-126">[Synchronize Analysis Services Databases](synchronize-analysis-services-databases.md) </span></span>  
 <span data-ttu-id="552f8-127">[配置スクリプトの作成に使用される入力ファイルについて](deployment-script-files-input-used-to-create-deployment-script.md) </span><span class="sxs-lookup"><span data-stu-id="552f8-127">[Understanding the Input Files Used to Create the Deployment Script](deployment-script-files-input-used-to-create-deployment-script.md) </span></span>  
 [<span data-ttu-id="552f8-128">配置ユーティリティを使用したモデル ソリューションの配置</span><span class="sxs-lookup"><span data-stu-id="552f8-128">Deploy Model Solutions with the Deployment Utility</span></span>](deploy-model-solutions-with-the-deployment-utility.md)  
  
  
