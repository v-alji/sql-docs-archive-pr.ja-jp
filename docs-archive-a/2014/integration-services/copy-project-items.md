---
title: プロジェクト項目のコピー |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- data sources [Integration Services], copying
- packages [Integration Services], copying
- copying data source views
- copying data sources
- copying packages
- data source views [Integration Services], copying
ms.assetid: 1606c54d-20f9-49f3-a4ef-caad83a772aa
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3456209c467c3b8474e130181d02304911098d2c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641798"
---
# <a name="copy-project-items"></a><span data-ttu-id="eaf86-102">プロジェクト アイテムをコピーする</span><span class="sxs-lookup"><span data-stu-id="eaf86-102">Copy Project Items</span></span>
  <span data-ttu-id="eaf86-103">このトピックでは、[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクト内のオブジェクトをコピーする方法、または [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクト間でオブジェクトをコピーする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="eaf86-103">This topic describes how to copy objects within an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project or between [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] projects.</span></span> <span data-ttu-id="eaf86-104">他の種類の [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] プロジェクト、[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]、および [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] の間でオブジェクトをコピーすることもできます。</span><span class="sxs-lookup"><span data-stu-id="eaf86-104">You can also copy objects between the other types of [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] projects, [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] and [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="eaf86-105">プロジェクト間でコピーするには、プロジェクトが同じ [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] ソリューションに含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="eaf86-105">To copy between projects, the project must be part of the same [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] solution.</span></span> <span data-ttu-id="eaf86-106">詳細については、「[Integration Services (SSIS) プロジェクト](integration-services-ssis-projects-and-solutions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eaf86-106">For more information, see [Integration Services &#40;SSIS&#41; Projects](integration-services-ssis-projects-and-solutions.md).</span></span>  
  
### <a name="to-copy-project-level-items"></a><span data-ttu-id="eaf86-107">プロジェクト レベルのアイテムをコピーするには</span><span class="sxs-lookup"><span data-stu-id="eaf86-107">To copy project level items</span></span>  
  
1.  <span data-ttu-id="eaf86-108">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] で、作業対象とする [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトまたはソリューションを開きます。</span><span class="sxs-lookup"><span data-stu-id="eaf86-108">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project or solution that you want to work with.</span></span>  
  
2.  <span data-ttu-id="eaf86-109">コピー元のプロジェクトとアイテム フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="eaf86-109">Expand the project and item folder to copy from.</span></span>  
  
3.  <span data-ttu-id="eaf86-110">アイテムを右クリックし、**[コピー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eaf86-110">Right-click the item and click **Copy**.</span></span>  
  
4.  <span data-ttu-id="eaf86-111">コピー先の [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを右クリックし、**[貼り付け]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eaf86-111">Right-click the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project to copy to and click **Paste**.</span></span>  
  
     <span data-ttu-id="eaf86-112">アイテムが適切なフォルダーに自動的にコピーされます。</span><span class="sxs-lookup"><span data-stu-id="eaf86-112">The items are automatically copied to the correct folder.</span></span> <span data-ttu-id="eaf86-113">パッケージではない [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトにアイテムをコピーする場合は、アイテムが **[その他]** フォルダーにコピーされます。</span><span class="sxs-lookup"><span data-stu-id="eaf86-113">If you copy items to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that are not packages, the items are copied to the **Miscellaneous** folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eaf86-114">参照</span><span class="sxs-lookup"><span data-stu-id="eaf86-114">See Also</span></span>  
 <span data-ttu-id="eaf86-115">[SSIS&#41; パッケージ &#40;Integration Services](../../2014/integration-services/integration-services-ssis-packages.md) </span><span class="sxs-lookup"><span data-stu-id="eaf86-115">[Integration Services &#40;SSIS&#41; Packages](../../2014/integration-services/integration-services-ssis-packages.md) </span></span>  
 [<span data-ttu-id="eaf86-116">パッケージ オブジェクトをコピーする</span><span class="sxs-lookup"><span data-stu-id="eaf86-116">Copy Package Objects</span></span>](../../2014/integration-services/copy-package-objects.md)  
  
  
