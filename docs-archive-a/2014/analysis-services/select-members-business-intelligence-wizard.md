---
title: '[メンバーの選択] (ビジネスインテリジェンスウィザード)Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.biwizard.currencyconversion.memberconversion.f1
ms.assetid: 1a147461-d594-41e7-a41d-09d2d003e1e0
author: minewiskan
ms.author: owend
ms.openlocfilehash: fd5f184e0d9670725609531b6d0a101f8e7f8647
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634085"
---
# <a name="select-members-business-intelligence-wizard"></a><span data-ttu-id="4fc55-102">[メンバーの選択] (ビジネス インテリジェンス ウィザード)</span><span class="sxs-lookup"><span data-stu-id="4fc55-102">Select Members (Business Intelligence Wizard)</span></span>
  <span data-ttu-id="4fc55-103">**[メンバーの選択]** ページを使用すると、ビジネス インテリジェンス ウィザードの **[通貨換算オプションの設定]** ページで指定された通貨換算機能を適用するメンバーを指定できます。</span><span class="sxs-lookup"><span data-stu-id="4fc55-103">Use the **Select Members** page to determine to which members the Business Intelligence Wizard should apply the currency conversion functionality specified on the **Set Currency Conversion Options** page.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4fc55-104">ビジネス インテリジェンス ウィザードをディメンション デザイナーから起動した場合や、 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]のソリューション エクスプローラーでディメンションを右クリックして起動した場合、このページは表示されません。</span><span class="sxs-lookup"><span data-stu-id="4fc55-104">This page does not appear if the Business Intelligence Wizard was started from Dimension Designer or by right-clicking a dimension in Solution Explorer in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
## <a name="options"></a><span data-ttu-id="4fc55-105">Options</span><span class="sxs-lookup"><span data-stu-id="4fc55-105">Options</span></span>  
 <span data-ttu-id="4fc55-106">**[メジャー ディメンション]**</span><span class="sxs-lookup"><span data-stu-id="4fc55-106">**Measures dimension**</span></span>  
 <span data-ttu-id="4fc55-107">選択すると、キューブ内の 1 つ以上のメジャーに通貨換算機能を適用します。</span><span class="sxs-lookup"><span data-stu-id="4fc55-107">Select to apply the currency conversion functionality to one or more measures in the cube.</span></span>  
  
 <span data-ttu-id="4fc55-108">このオプションを選択すると、次の表に示すオプションがグリッドに表示されます。</span><span class="sxs-lookup"><span data-stu-id="4fc55-108">If selected, the grid displays the options listed in the following table.</span></span>  
  
|<span data-ttu-id="4fc55-109">オプション</span><span class="sxs-lookup"><span data-stu-id="4fc55-109">Option</span></span>|<span data-ttu-id="4fc55-110">説明</span><span class="sxs-lookup"><span data-stu-id="4fc55-110">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="4fc55-111">**[ビルトイン メジャーの種類]**</span><span class="sxs-lookup"><span data-stu-id="4fc55-111">**Built-in Measure Types**</span></span>|<span data-ttu-id="4fc55-112">選択すると、指定したメジャーに通貨換算機能を含めます。</span><span class="sxs-lookup"><span data-stu-id="4fc55-112">Select to include currency conversion functionality for the specified measure.</span></span>|  
|<span data-ttu-id="4fc55-113">**直径**</span><span class="sxs-lookup"><span data-stu-id="4fc55-113">**Measures**</span></span>|<span data-ttu-id="4fc55-114">レート メジャー グループから、 **[ビルトイン メジャーの種類]** で選択したメジャーを変換するときに使用する、換算レートを含むメジャーを選択します。</span><span class="sxs-lookup"><span data-stu-id="4fc55-114">Select the measure from the rate measure group that contains the exchange rate to use when the measure selected in **Built-in Measure Types** is converted.</span></span>|  
  
 <span data-ttu-id="4fc55-115">**[勘定科目の階層]**</span><span class="sxs-lookup"><span data-stu-id="4fc55-115">**Account hierarchy**</span></span>  
 <span data-ttu-id="4fc55-116">選択すると、キューブに含まれている勘定科目ディメンションの、勘定科目の階層のメンバーに通貨換算機能を適用します。</span><span class="sxs-lookup"><span data-stu-id="4fc55-116">Select to apply the currency conversion functionality to one or more members in the account hierarchy of the account dimension included in the cube.</span></span> <span data-ttu-id="4fc55-117">勘定科目階層は、 `Type` プロパティが*account*に設定されている account ディメンション内の階層です。</span><span class="sxs-lookup"><span data-stu-id="4fc55-117">The account hierarchy is the hierarchy within the account dimension whose `Type` property is set to *Account*.</span></span>  
  
 <span data-ttu-id="4fc55-118">このオプションを選択すると、次の表に示すオプションがグリッドに表示されます。</span><span class="sxs-lookup"><span data-stu-id="4fc55-118">If selected, the grid displays the options listed in the following table.</span></span>  
  
|<span data-ttu-id="4fc55-119">オプション</span><span class="sxs-lookup"><span data-stu-id="4fc55-119">Option</span></span>|<span data-ttu-id="4fc55-120">説明</span><span class="sxs-lookup"><span data-stu-id="4fc55-120">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="4fc55-121">**[勘定科目メンバー]**</span><span class="sxs-lookup"><span data-stu-id="4fc55-121">**Account Member**</span></span>|<span data-ttu-id="4fc55-122">選択すると、勘定科目の階層の指定したメンバーに通貨換算機能を含めます。</span><span class="sxs-lookup"><span data-stu-id="4fc55-122">Select to include currency conversion functionality for the specified member of the account hierarchy.</span></span>|  
|<span data-ttu-id="4fc55-123">**直径**</span><span class="sxs-lookup"><span data-stu-id="4fc55-123">**Measures**</span></span>|<span data-ttu-id="4fc55-124">レート メジャー グループから、 **[勘定科目メンバー]** で選択したメンバーのメジャーを変換するときに使用する、換算レートを含むメジャーを選択します。</span><span class="sxs-lookup"><span data-stu-id="4fc55-124">Select the measure from the rate measure group that contains the exchange rate to use when the measures for the member selected in **Account Member** are converted.</span></span>|  
  
 <span data-ttu-id="4fc55-125">**[種類に基づいた勘定科目の階層]**</span><span class="sxs-lookup"><span data-stu-id="4fc55-125">**Account hierarchy based on type**</span></span>  
 <span data-ttu-id="4fc55-126">選択すると、`Type` プロパティが指定した種類の勘定科目に設定されている勘定科目の階層の属性の全メンバーに、通貨換算機能が適用されます。</span><span class="sxs-lookup"><span data-stu-id="4fc55-126">Select to apply the currency conversion functionality to all members of attributes in the account hierarchy whose `Type` property is set to a specified account type.</span></span>  
  
 <span data-ttu-id="4fc55-127">このオプションを選択すると、次の表に示すオプションがグリッドに表示されます。</span><span class="sxs-lookup"><span data-stu-id="4fc55-127">If selected, the grid displays the options listed in the following table.</span></span>  
  
|<span data-ttu-id="4fc55-128">オプション</span><span class="sxs-lookup"><span data-stu-id="4fc55-128">Option</span></span>|<span data-ttu-id="4fc55-129">説明</span><span class="sxs-lookup"><span data-stu-id="4fc55-129">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="4fc55-130">**アカウントの種類**</span><span class="sxs-lookup"><span data-stu-id="4fc55-130">**Account Type**</span></span>|<span data-ttu-id="4fc55-131">選択すると、指定した種類の勘定科目に通貨換算機能を含めます。</span><span class="sxs-lookup"><span data-stu-id="4fc55-131">Select to include currency conversion functionality for the specified account type.</span></span>|  
|<span data-ttu-id="4fc55-132">**直径**</span><span class="sxs-lookup"><span data-stu-id="4fc55-132">**Measures**</span></span>|<span data-ttu-id="4fc55-133">レート メジャー グループから、 **[勘定科目の種類]** で選択した種類の勘定科目を使用して、属性のメンバーのメジャーを変換するときに使用する、換算レートを含むメジャーを選択します。</span><span class="sxs-lookup"><span data-stu-id="4fc55-133">Select the measure from the rate measure group that contains the exchange rate to use when measures for the members of attributes using the account type selected in **Account Type** are converted.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4fc55-134">参照</span><span class="sxs-lookup"><span data-stu-id="4fc55-134">See Also</span></span>  
 <span data-ttu-id="4fc55-135">[ビジネスインテリジェンスウィザードの F1 ヘルプ](business-intelligence-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="4fc55-135">[Business Intelligence Wizard F1 Help](business-intelligence-wizard-f1-help.md) </span></span>  
 <span data-ttu-id="4fc55-136">[キューブデザイナー &#40;Analysis Services-多次元データ&#41;](cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="4fc55-136">[Cube Designer &#40;Analysis Services - Multidimensional Data&#41;](cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="4fc55-137">ディメンションデザイナー &#40;Analysis Services-多次元データ&#41;</span><span class="sxs-lookup"><span data-stu-id="4fc55-137">Dimension Designer &#40;Analysis Services - Multidimensional Data&#41;</span></span>](dimension-designer-analysis-services-multidimensional-data.md)  
  
  
