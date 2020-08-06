---
title: パッケージの配置 (SSIS) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services packages, deploying
- deploying packages [Integration Services]
- SQL Server Integration Services packages, deploying
- deploying packages [Integration Services], about deploying packages
- packages [Integration Services], deploying
- SSIS packages, deploying
ms.assetid: 0f5fc7be-e37e-4ecd-ba99-697c8ae3436f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 32627eddf5e7a696decd549e9b87ebb5c3b9d031
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642160"
---
# <a name="package-deployment-ssis"></a><span data-ttu-id="67f1c-102">パッケージの配置 (SSIS)</span><span class="sxs-lookup"><span data-stu-id="67f1c-102">Package Deployment (SSIS)</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="67f1c-103">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] には、開発コンピューターから実稼働サーバーまたは他のコンピューターへのパッケージの配置を簡素化するツールとウィザードが含まれています。</span><span class="sxs-lookup"><span data-stu-id="67f1c-103">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] includes tools and wizards that make it simple to deploy packages from the development computer to the production server or to other computers.</span></span>  
  
 <span data-ttu-id="67f1c-104">パッケージ配置プロセスは、次の 4 段階で行います。</span><span class="sxs-lookup"><span data-stu-id="67f1c-104">There are four steps in the package deployment process:</span></span>  
  
1.  <span data-ttu-id="67f1c-105">最初の手順は省略可能です。この手順では、実行時にパッケージのプロパティ要素を更新するパッケージ構成を作成します。</span><span class="sxs-lookup"><span data-stu-id="67f1c-105">The first optional step is optional and involves creating package configurations that update properties of package elements at run time.</span></span> <span data-ttu-id="67f1c-106">この構成は、パッケージを配置する際に自動的に適用されます。</span><span class="sxs-lookup"><span data-stu-id="67f1c-106">The configurations are automatically included when you deploy the packages.</span></span>  
  
2.  <span data-ttu-id="67f1c-107">2 番目の手順は、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] プロジェクトをビルドして、パッケージ配置ユーティリティを作成することです。</span><span class="sxs-lookup"><span data-stu-id="67f1c-107">The second step is to build the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project to create a package deployment utility.</span></span> <span data-ttu-id="67f1c-108">プロジェクトの配置ユーティリティには、配置するパッケージが含まれます。</span><span class="sxs-lookup"><span data-stu-id="67f1c-108">The deployment utility for the project contains the packages that you want to deploy</span></span>  
  
3.  <span data-ttu-id="67f1c-109">3 番目の手順は、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] プロジェクトのビルド時に作成された配置フォルダーをターゲット コンピューターにコピーすることです。</span><span class="sxs-lookup"><span data-stu-id="67f1c-109">The third step is to copy the deployment folder that was created when you built the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project to the target computer.</span></span>  
  
4.  <span data-ttu-id="67f1c-110">4 番目の手順は、ターゲット コンピューターでパッケージ インストール ウィザードを実行し、ファイル システムまたは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスにパッケージをインストールすることです。</span><span class="sxs-lookup"><span data-stu-id="67f1c-110">The fourth step is to run, on the target computer, the Package Installation Wizard to install the packages to the file system or to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="67f1c-111">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="67f1c-111">Related Tasks</span></span>  
 <span data-ttu-id="67f1c-112">配置ユーティリティを作成する方法については、「 [Create a Deployment Utility](../create-a-deployment-utility.md)」 (配置ユーティリティの作成) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="67f1c-112">For information about how to create a deployment utility, see [Create a Deployment Utility](../create-a-deployment-utility.md).</span></span>  
  
 <span data-ttu-id="67f1c-113">配置ユーティリティを使用してパッケージを配置する方法については、「 [配置ユーティリティを使用してパッケージを配置する](../deploy-packages-by-using-the-deployment-utility.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="67f1c-113">For information about how to deploy packages using the deployment utility, see [Deploy Packages by Using the Deployment Utility](../deploy-packages-by-using-the-deployment-utility.md).</span></span>  
  
 <span data-ttu-id="67f1c-114">パッケージ構成を作成する方法の詳細については、「 [パッケージ構成を作成する](../create-package-configurations.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="67f1c-114">For information about how to create package configurations, see [Create Package Configurations](../create-package-configurations.md).</span></span>  
  
  
