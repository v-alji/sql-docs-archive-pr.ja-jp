---
title: 集計の使用状況の確認 (使用法に基づく最適化ウィザード) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.storagedesignwizard.reviewaggregationusage.f1
ms.assetid: 49ce2094-c4dc-4e46-8cef-c17c5db084ca
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5ef9f900e64858515db226d1f9b864874a4ba827
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633387"
---
# <a name="review-aggregation-usage-usage-based-optimiation-wizard"></a><span data-ttu-id="e44ce-102">[集計使用法の確認] (使用法に基づく最適化ウィザード)</span><span class="sxs-lookup"><span data-stu-id="e44ce-102">Review Aggregation Usage (Usage-Based Optimiation Wizard)</span></span>
  <span data-ttu-id="e44ce-103">**[集計使用法の確認]** ページを使用すると、集計使用法の設定を構成できます。</span><span class="sxs-lookup"><span data-stu-id="e44ce-103">Use the **Review Aggregation Usage** page to configure aggregation usage settings.</span></span>  
  
## <a name="options"></a><span data-ttu-id="e44ce-104">Options</span><span class="sxs-lookup"><span data-stu-id="e44ce-104">Options</span></span>  
 <span data-ttu-id="e44ce-105">**[Default]**</span><span class="sxs-lookup"><span data-stu-id="e44ce-105">**Default**</span></span>  
 <span data-ttu-id="e44ce-106">属性の集計使用法の設定を Default に設定する場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="e44ce-106">Select to set the aggregation usage setting for the attribute to Default.</span></span> <span data-ttu-id="e44ce-107">この設定を使用すると、属性およびディメンションの型に基づいて既定のルールが適用されます。</span><span class="sxs-lookup"><span data-stu-id="e44ce-107">By using this setting, the designer applies a default rule based on the type of attribute and dimension.</span></span>  
  
 <span data-ttu-id="e44ce-108">**完全**</span><span class="sxs-lookup"><span data-stu-id="e44ce-108">**Full**</span></span>  
 <span data-ttu-id="e44ce-109">属性の集計使用法の設定を Full に設定する場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="e44ce-109">Select to set the aggregation usage setting for the attribute to Full.</span></span> <span data-ttu-id="e44ce-110">この設定を使用した場合、この属性または属性チェーンで下位にある関連属性をキューブの各集計に含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="e44ce-110">By using this setting, every aggregation for the cube must include this attribute or a related attribute that is lower in the attribute chain.</span></span> <span data-ttu-id="e44ce-111">属性に多くのメンバーが含まれる場合は、集計使用法を Full に設定しないでください。</span><span class="sxs-lookup"><span data-stu-id="e44ce-111">The Full aggregation usage setting should be avoided when an attribute contains many members.</span></span> <span data-ttu-id="e44ce-112">複数の属性または多くのメンバーが含まれる属性に対してこの設定を指定すると、サイズが大きくなりすぎて集計のデザインを行えない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e44ce-112">If specified for multiple attributes or attributes that have many members, this setting might prevent aggregations from being designed because of excessive size.</span></span>  
  
 <span data-ttu-id="e44ce-113">**なし**</span><span class="sxs-lookup"><span data-stu-id="e44ce-113">**None**</span></span>  
 <span data-ttu-id="e44ce-114">属性の集計使用法の設定を None に設定する場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="e44ce-114">Select to set the aggregation usage setting for the attribute to None.</span></span> <span data-ttu-id="e44ce-115">この設定を使用した場合、この属性をキューブの集計に含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="e44ce-115">By using this setting, no aggregation for the cube can include this attribute.</span></span>  
  
 <span data-ttu-id="e44ce-116">**有無**</span><span class="sxs-lookup"><span data-stu-id="e44ce-116">**Unrestricted**</span></span>  
 <span data-ttu-id="e44ce-117">属性の集計使用法の設定を Unrestricted に設定する場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="e44ce-117">Select to set the aggregation usage setting for the attribute to Unrestricted.</span></span> <span data-ttu-id="e44ce-118">この設定を使用すると、集計デザイナーに対する制限は行われません。</span><span class="sxs-lookup"><span data-stu-id="e44ce-118">By using this setting, no restrictions are put on the aggregation designer.</span></span> <span data-ttu-id="e44ce-119">ただし、この設定でも、属性を評価して属性が重要な集計候補であるかどうかを判断する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e44ce-119">However, the attribute must still be evaluated to determine whether it is a valuable aggregation candidate.</span></span>  
  
 <span data-ttu-id="e44ce-120">**[すべて既定値に設定]**</span><span class="sxs-lookup"><span data-stu-id="e44ce-120">**Set All to Default**</span></span>  
 <span data-ttu-id="e44ce-121">すべての属性の集計使用法の設定を Default に設定する場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="e44ce-121">Select to set the aggregation usage settings for all attributes to Default.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e44ce-122">参照</span><span class="sxs-lookup"><span data-stu-id="e44ce-122">See Also</span></span>  
 <span data-ttu-id="e44ce-123">[集計のデザインウィザードの F1 ヘルプ](aggregation-design-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="e44ce-123">[Aggregation Design Wizard F1 Help](aggregation-design-wizard-f1-help.md) </span></span>  
 [<span data-ttu-id="e44ce-124">Analysis Services のウィザード &#40;多次元データ&#41;</span><span class="sxs-lookup"><span data-stu-id="e44ce-124">Analysis Services Wizards &#40;Multidimensional Data&#41;</span></span>](analysis-services-wizards-multidimensional-data.md)  
  
  
