---
title: ディメンションの属性の構成 (ビジネスインテリジェンスウィザード)Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.biwizard.acctintelligence.selectattributes.f1
ms.assetid: 3d046e63-bcb1-4ab1-9c37-652463fa68c3
author: minewiskan
ms.author: owend
ms.openlocfilehash: 1d2e9bc83b7a6d83b6d2808b472d67169266ff07
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633502"
---
# <a name="configure-dimension-attributes-business-intelligence-wizard"></a><span data-ttu-id="c19f4-102">[ディメンションの属性の構成] (ビジネス インテリジェンス ウィザード)</span><span class="sxs-lookup"><span data-stu-id="c19f4-102">Configure Dimension Attributes (Business Intelligence Wizard)</span></span>
  <span data-ttu-id="c19f4-103">**[ディメンションの属性の構成]** ページでは、 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] で勘定科目ディメンションの属性の識別に使用される属性の種類に、ディメンションの属性をマップできます。</span><span class="sxs-lookup"><span data-stu-id="c19f4-103">Use the **Configure Dimension Attributes** page to map the dimension attributes to the attribute types that [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] uses to identify attributes for account dimensions.</span></span>  
  
## <a name="options"></a><span data-ttu-id="c19f4-104">Options</span><span class="sxs-lookup"><span data-stu-id="c19f4-104">Options</span></span>  
 <span data-ttu-id="c19f4-105">**[ディメンションの種類]**</span><span class="sxs-lookup"><span data-stu-id="c19f4-105">**Dimension type**</span></span>  
 <span data-ttu-id="c19f4-106">選択したディメンションの種類が表示されます。</span><span class="sxs-lookup"><span data-stu-id="c19f4-106">Displays the selected dimension type.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c19f4-107">`Type`勘定科目ディメンションの*勘定科目*以外の値にディメンションのプロパティを変更することはできないため、このオプションは使用できません。</span><span class="sxs-lookup"><span data-stu-id="c19f4-107">This option is not available because the `Type` property of the dimension cannot be changed to a value other than *Account* for account dimensions.</span></span>  
  
 <span data-ttu-id="c19f4-108">**[ディメンションの属性]**</span><span class="sxs-lookup"><span data-stu-id="c19f4-108">**Dimension attributes**</span></span>  
 <span data-ttu-id="c19f4-109">ディメンションに含まれる既存のディメンションの属性にマップできる、有効な属性の型が表示されます。</span><span class="sxs-lookup"><span data-stu-id="c19f4-109">Displays the valid attribute types that can be mapped to existing dimension attributes in the dimension.</span></span>  
  
 <span data-ttu-id="c19f4-110">**用意**</span><span class="sxs-lookup"><span data-stu-id="c19f4-110">**Include**</span></span>  
 <span data-ttu-id="c19f4-111">チェック ボックスをオンにすると、対応する属性の型がディメンションに追加されます。</span><span class="sxs-lookup"><span data-stu-id="c19f4-111">Select a check box to include the corresponding attribute type in the dimension.</span></span>  
  
 <span data-ttu-id="c19f4-112">**属性の型**</span><span class="sxs-lookup"><span data-stu-id="c19f4-112">**Attribute Type**</span></span>  
 <span data-ttu-id="c19f4-113">ディメンションに含まれる既存のディメンションの属性にマップできる、属性の型が一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="c19f4-113">Lists the attribute types that can be mapped to existing dimension attributes in the dimension.</span></span>  
  
 <span data-ttu-id="c19f4-114">**[ディメンションの属性]**</span><span class="sxs-lookup"><span data-stu-id="c19f4-114">**Dimension Attribute**</span></span>  
 <span data-ttu-id="c19f4-115">対応する属性の型にマップするディメンションの属性を選択します。</span><span class="sxs-lookup"><span data-stu-id="c19f4-115">Select the dimension attribute that should be mapped to the corresponding attribute type.</span></span>  
  
 <span data-ttu-id="c19f4-116">**[勘定科目の種類に基づいた準加法となるメジャーを設定する]**</span><span class="sxs-lookup"><span data-stu-id="c19f4-116">**Set measures to be semiadditive based on account type**</span></span>  
 <span data-ttu-id="c19f4-117">これをオンにすると、このディメンションに関連付けられているメジャーがすべて変更され、勘定科目の種類によって集計されるようになります。</span><span class="sxs-lookup"><span data-stu-id="c19f4-117">Select to change every measure associated with this dimension to be aggregated by account type.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c19f4-118">ビジネス インテリジェンス ウィザードをディメンション デザイナーから起動した場合や、 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]のソリューション エクスプローラーでディメンションを右クリックして起動した場合、このオプションは表示されません。</span><span class="sxs-lookup"><span data-stu-id="c19f4-118">This option does not appear if the Business Intelligence Wizard was started from Dimension Designer or by right-clicking a dimension in Solution Explorer in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c19f4-119">参照</span><span class="sxs-lookup"><span data-stu-id="c19f4-119">See Also</span></span>  
 <span data-ttu-id="c19f4-120">[ビジネスインテリジェンスウィザードの F1 ヘルプ](business-intelligence-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="c19f4-120">[Business Intelligence Wizard F1 Help](business-intelligence-wizard-f1-help.md) </span></span>  
 <span data-ttu-id="c19f4-121">[キューブデザイナー &#40;Analysis Services-多次元データ&#41;](cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="c19f4-121">[Cube Designer &#40;Analysis Services - Multidimensional Data&#41;](cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="c19f4-122">ディメンションデザイナー &#40;Analysis Services-多次元データ&#41;</span><span class="sxs-lookup"><span data-stu-id="c19f4-122">Dimension Designer &#40;Analysis Services - Multidimensional Data&#41;</span></span>](dimension-designer-analysis-services-multidimensional-data.md)  
  
  
