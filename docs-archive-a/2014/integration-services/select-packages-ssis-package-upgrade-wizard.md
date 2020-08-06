---
title: '[パッケージの選択] (SSIS パッケージアップグレードウィザード) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.is.upgradewizard.selectpackages.f1
ms.assetid: 224100f1-51f6-4f1f-91a2-054819c76ae8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1d1b1380fe8932033e750ef7da8cdeaa630abe98
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645733"
---
# <a name="select-packages-ssis-package-upgrade-wizard"></a><span data-ttu-id="00c2b-102">[パッケージの選択] (SSIS パッケージ アップグレード ウィザード)</span><span class="sxs-lookup"><span data-stu-id="00c2b-102">Select Packages (SSIS Package Upgrade Wizard)</span></span>
  <span data-ttu-id="00c2b-103">**[パッケージの選択]** ページを使用すると、アップグレードするパッケージを選択できます。</span><span class="sxs-lookup"><span data-stu-id="00c2b-103">Use the **Select Packages** page to select the packages to upgrade.</span></span> <span data-ttu-id="00c2b-104">このページには、ウィザードの **[ソースの場所を選択]** ページで指定した場所に格納されているパッケージが一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="00c2b-104">This page lists the packages that are stored in the location that was specified on the **Select Source Location** page of the wizard.</span></span>  
  
 <span data-ttu-id="00c2b-105">**SSIS パッケージ アップグレード ウィザードを実行するには**</span><span class="sxs-lookup"><span data-stu-id="00c2b-105">**To run the SSIS Package Upgrade Wizard**</span></span>  
  
-   [<span data-ttu-id="00c2b-106">SSIS パッケージ アップグレード ウィザードを使用した Integration Services パッケージのアップグレード</span><span class="sxs-lookup"><span data-stu-id="00c2b-106">Upgrade Integration Services Packages Using the SSIS Package Upgrade Wizard</span></span>](install-windows/upgrade-integration-services-packages-using-the-ssis-package-upgrade-wizard.md)  
  
## <a name="options"></a><span data-ttu-id="00c2b-107">Options</span><span class="sxs-lookup"><span data-stu-id="00c2b-107">Options</span></span>  
 <span data-ttu-id="00c2b-108">**[既存のパッケージ名]**</span><span class="sxs-lookup"><span data-stu-id="00c2b-108">**Existing package name**</span></span>  
 <span data-ttu-id="00c2b-109">アップグレードする 1 つ以上のパッケージを選択します。</span><span class="sxs-lookup"><span data-stu-id="00c2b-109">Select one or more packages to upgrade.</span></span>  
  
 <span data-ttu-id="00c2b-110">**[アップグレード パッケージ名]**</span><span class="sxs-lookup"><span data-stu-id="00c2b-110">**Upgrade package name**</span></span>  
 <span data-ttu-id="00c2b-111">アップグレード先パッケージ名を指定するか、ウィザードによって提供される既定の名前を使用します。</span><span class="sxs-lookup"><span data-stu-id="00c2b-111">Provide the destination package name, or use the default name that the wizard provides.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="00c2b-112">パッケージのアップグレード後に、アップグレード先パッケージ名を変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="00c2b-112">You can also change the destination package name after upgrading the package.</span></span> <span data-ttu-id="00c2b-113">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] または [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]でアップグレード済みのパッケージを開き、パッケージ名を変更します。</span><span class="sxs-lookup"><span data-stu-id="00c2b-113">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] or [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], open the upgraded package and change the package name.</span></span>  
  
 <span data-ttu-id="00c2b-114">**パスワード**</span><span class="sxs-lookup"><span data-stu-id="00c2b-114">**Password**</span></span>  
 <span data-ttu-id="00c2b-115">選択したアップグレード パッケージの複号化に使用するパスワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="00c2b-115">Specify the password that is used to decrypt the selected upgrade packages.</span></span>  
  
 <span data-ttu-id="00c2b-116">**[選択項目に適用]**</span><span class="sxs-lookup"><span data-stu-id="00c2b-116">**Apply to selection**</span></span>  
 <span data-ttu-id="00c2b-117">選択したアップグレード パッケージの復号化に、指定したパスワードを適用します。</span><span class="sxs-lookup"><span data-stu-id="00c2b-117">Apply the specified password to decrypt the selected upgrade packages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00c2b-118">参照</span><span class="sxs-lookup"><span data-stu-id="00c2b-118">See Also</span></span>  
 <span data-ttu-id="00c2b-119">[[ソースの場所] &#40;SSIS パッケージアップグレードウィザードを選択し&#41;](../../2014/integration-services/select-source-location-ssis-package-upgrade-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="00c2b-119">[Select Source Location &#40;SSIS Package Upgrade Wizard&#41;](../../2014/integration-services/select-source-location-ssis-package-upgrade-wizard.md) </span></span>  
 [<span data-ttu-id="00c2b-120">Integration Services パッケージのアップグレード</span><span class="sxs-lookup"><span data-stu-id="00c2b-120">Upgrade Integration Services Packages</span></span>](install-windows/upgrade-integration-services-packages.md)  
  
  
