---
title: パッケージの再展開 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- redeploying packages [Integration Services]
- deploying packages [Integration Services], redeploying
ms.assetid: 86806efb-8cf4-4f9d-9824-1152cb4c495c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4c5286d406d96f62fc74eb619f7e7a6064fde2a3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713270"
---
# <a name="redeployment-of-packages"></a><span data-ttu-id="d30ec-102">パッケージの再配置</span><span class="sxs-lookup"><span data-stu-id="d30ec-102">Redeployment of Packages</span></span>
  <span data-ttu-id="d30ec-103">プロジェクトの配置後に、パッケージの機能を更新または拡張し、更新したパッケージを含む [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを再配置する必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="d30ec-103">After a project is deployed, you may need to update or extend package functionality and then redeploy the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the updated packages.</span></span> <span data-ttu-id="d30ec-104">パッケージの再配置プロセスの一環として、配置ユーティリティに含まれている構成プロパティを見直す必要があります。</span><span class="sxs-lookup"><span data-stu-id="d30ec-104">As part of the process of redeploying packages, you should review the configuration properties that are included in the deployment utility.</span></span> <span data-ttu-id="d30ec-105">たとえば、パッケージの再配置後に構成が変更されないようにする場合などがあります。</span><span class="sxs-lookup"><span data-stu-id="d30ec-105">For example, you may not want to allow configuration changes after the package is redeployed.</span></span>  
  
## <a name="process-for-redeployment"></a><span data-ttu-id="d30ec-106">再配置のプロセス</span><span class="sxs-lookup"><span data-stu-id="d30ec-106">Process for Redeployment</span></span>  
 <span data-ttu-id="d30ec-107">パッケージの更新の終了後、プロジェクトを再構築し、ターゲット コンピューターに配置フォルダーをコピーしてから、パッケージ インストール ウィザードを再度実行します。</span><span class="sxs-lookup"><span data-stu-id="d30ec-107">After you finish updating the packages, you rebuild the project, copy the deployment folder to the target computer, and then rerun the Package Installation Wizard.</span></span>  
  
 <span data-ttu-id="d30ec-108">プロジェクトのパッケージの一部だけを更新した場合、プロジェクト全体を再配置する必要がないことがあります。</span><span class="sxs-lookup"><span data-stu-id="d30ec-108">If you update only a few packages in the project, you may not want to redeploy the entire project.</span></span> <span data-ttu-id="d30ec-109">パッケージの一部だけを配置するために、新しい [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを作成して、このプロジェクトに更新したパッケージを追加し、プロジェクトをビルドして配置できます。</span><span class="sxs-lookup"><span data-stu-id="d30ec-109">To deploy only a few packages, you can create a new [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project, add the updated packages to the new project, and then build and deploy the project.</span></span> <span data-ttu-id="d30ec-110">パッケージの構成は、パッケージを別のプロジェクトに追加する際に、自動的にパッケージと共にコピーされます。</span><span class="sxs-lookup"><span data-stu-id="d30ec-110">Package configurations are automatically copied with the package when you add the package to a different project.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="d30ec-111">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="d30ec-111">Related Tasks</span></span>  
 [<span data-ttu-id="d30ec-112">配置ユーティリティを使用してパッケージを配置する</span><span class="sxs-lookup"><span data-stu-id="d30ec-112">Deploy Packages by Using the Deployment Utility</span></span>](../../2014/integration-services/deploy-packages-by-using-the-deployment-utility.md)  
  
  
