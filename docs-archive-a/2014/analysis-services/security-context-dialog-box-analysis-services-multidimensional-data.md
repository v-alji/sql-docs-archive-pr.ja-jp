---
title: '[セキュリティコンテキスト] ダイアログボックス (Analysis Services-多次元データ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.browsecube.securitycontext.f1
ms.assetid: 238a4a4b-84bd-4b3d-9f02-f3adf57fa3af
author: minewiskan
ms.author: owend
ms.openlocfilehash: 58d5f71172ac16087ecc342342e70ade234226a2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633363"
---
# <a name="security-context-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="f0acb-102">[セキュリティ コンテキスト] ダイアログ ボックス (Analysis Services - 多次元データ)</span><span class="sxs-lookup"><span data-stu-id="f0acb-102">Security Context Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="f0acb-103">**の** [セキュリティ コンテキスト] [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] ダイアログ ボックスを使用すると、 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] オブジェクトのデータまたはメタデータをチェックするために使用されるユーザーおよびロールを変更できます。</span><span class="sxs-lookup"><span data-stu-id="f0acb-103">Use the **Security Context** dialog box in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to change the user and role used to examine data or metadata for a [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] object.</span></span> <span data-ttu-id="f0acb-104">**[セキュリティ コンテキスト]** ダイアログ ボックスを表示するには、キューブ デザイナーの **[計算]** タブまたは **[ブラウザー]** タブのツール バー ペインにある **[セキュリティ コンテキスト]** をクリックします。 \*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="f0acb-104">You can display the **Security Context** dialog box by clicking **Security Context** in the **Toolbar** pane on either the **Calculations** tab or the **Browser** tab in Cube Designer.</span></span>  
  
## <a name="options"></a><span data-ttu-id="f0acb-105">Options</span><span class="sxs-lookup"><span data-stu-id="f0acb-105">Options</span></span>  
 <span data-ttu-id="f0acb-106">**現在のユーザー**</span><span class="sxs-lookup"><span data-stu-id="f0acb-106">**Current user**</span></span>  
 <span data-ttu-id="f0acb-107">選択すると、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] オブジェクトのデータおよびメタデータを表示するときに、現在のユーザーのドメインおよびユーザー名を使用できます。</span><span class="sxs-lookup"><span data-stu-id="f0acb-107">Select to use the domain and user name of the current user while viewing the data and metadata of the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] object.</span></span>  
  
 <span data-ttu-id="f0acb-108">**[その他のユーザー]**</span><span class="sxs-lookup"><span data-stu-id="f0acb-108">**Other user**</span></span>  
 <span data-ttu-id="f0acb-109">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] オブジェクトのデータおよびメタデータを表示するときに使用する、他のユーザーまたはグループのドメインおよびユーザー名を入力します。</span><span class="sxs-lookup"><span data-stu-id="f0acb-109">Type the domain and user name of another user or group to use while viewing the data and metadata of the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] object.</span></span>  
  
 <span data-ttu-id="f0acb-110">ユーザーまたはグループのドメインおよび名前の形式は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="f0acb-110">The domain and name of the user or group uses the following format:</span></span>  
  
 <span data-ttu-id="f0acb-111">*\<Domain name>* **\\** *\<User account name>*</span><span class="sxs-lookup"><span data-stu-id="f0acb-111">*\<Domain name>* **\\** *\<User account name>*</span></span>  
  
 <span data-ttu-id="f0acb-112">**ロール**</span><span class="sxs-lookup"><span data-stu-id="f0acb-112">**Roles**</span></span>  
 <span data-ttu-id="f0acb-113">選択すると、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] オブジェクトのデータおよびメタデータを表示するときに、指定した 1 つまたは複数のロールを使用できます。</span><span class="sxs-lookup"><span data-stu-id="f0acb-113">Select to use one or more specified roles when viewing the data and metadata of the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] object.</span></span> <span data-ttu-id="f0acb-114">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベースに複数のロールが定義されている場合は、使用するロールを選択できます。</span><span class="sxs-lookup"><span data-stu-id="f0acb-114">You can select the roles to use if multiple roles are defined in the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0acb-115">参照</span><span class="sxs-lookup"><span data-stu-id="f0acb-115">See Also</span></span>  
 <span data-ttu-id="f0acb-116">[Kpi &#40;キューブデザイナー&#41; &#40;Analysis Services-多次元データ&#41;](kpis-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="f0acb-116">[KPIs &#40;Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](kpis-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="f0acb-117">[ブラウザー &#40;キューブデザイナー&#41; &#40;Analysis Services-多次元データ&#41;](browser-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="f0acb-117">[Browser &#40;Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](browser-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="f0acb-118">多次元データ &#40;Analysis Services のデザイナーとダイアログボックス&#41;</span><span class="sxs-lookup"><span data-stu-id="f0acb-118">Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;</span></span>](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)  
  
  
