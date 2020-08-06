---
title: 集計の使用状況の確認 (集計のデザインウィザード)Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.aggregationdesignwizard.reviewusage.f1
ms.assetid: 107ee872-3df2-4931-b56c-af11e38f6745
author: minewiskan
ms.author: owend
ms.openlocfilehash: afbb02dae64f3f7ebd57065c3ff8a7d1e202dcf2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633388"
---
# <a name="review-aggregation-usage-aggregation-design-wizard"></a><span data-ttu-id="044d3-102">[集計使用法の確認] (集計のデザイン ウィザード)</span><span class="sxs-lookup"><span data-stu-id="044d3-102">Review Aggregation Usage (Aggregation Design Wizard)</span></span>
  <span data-ttu-id="044d3-103">**[集計使用法の確認]** ページを使用すると、集計使用法の設定を構成できます。</span><span class="sxs-lookup"><span data-stu-id="044d3-103">Use the **Review Aggregation Usage** page to configure aggregation usage settings.</span></span>  
  
## <a name="options"></a><span data-ttu-id="044d3-104">Options</span><span class="sxs-lookup"><span data-stu-id="044d3-104">Options</span></span>  
 <span data-ttu-id="044d3-105">**[Default]**</span><span class="sxs-lookup"><span data-stu-id="044d3-105">**Default**</span></span>  
 <span data-ttu-id="044d3-106">属性の集計使用法の設定を Default に設定する場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="044d3-106">Select to set the aggregation usage setting for the attribute to Default.</span></span> <span data-ttu-id="044d3-107">この設定を使用すると、属性およびディメンションの型に基づいて既定のルールが適用されます。</span><span class="sxs-lookup"><span data-stu-id="044d3-107">By using this setting, the designer applies a default rule based on the type of attribute and dimension.</span></span>  
  
 `Full`  
 <span data-ttu-id="044d3-108">属性の集計使用法の設定を `Full` に設定する場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="044d3-108">Select to set the aggregation usage setting for the attribute to `Full`.</span></span> <span data-ttu-id="044d3-109">この設定を使用した場合、この属性または属性チェーンで下位にある関連属性をキューブの各集計に含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="044d3-109">By using this setting, every aggregation for the cube must include this attribute or a related attribute that is lower in the attribute chain.</span></span> <span data-ttu-id="044d3-110">属性に多くのメンバーが含まれる場合は、集計使用法を `Full` に設定しないでください。</span><span class="sxs-lookup"><span data-stu-id="044d3-110">The `Full` aggregation usage setting should be avoided when an attribute contains many members.</span></span> <span data-ttu-id="044d3-111">複数の属性または多くのメンバーが含まれる属性に対してこの設定を指定すると、サイズが大きくなりすぎて集計のデザインを行えない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="044d3-111">If specified for multiple attributes or attributes that have many members, this setting might prevent aggregations from being designed because of excessive size.</span></span>  
  
 <span data-ttu-id="044d3-112">**なし**</span><span class="sxs-lookup"><span data-stu-id="044d3-112">**None**</span></span>  
 <span data-ttu-id="044d3-113">属性の集計使用法の設定を None に設定する場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="044d3-113">Select to set the aggregation usage setting for the attribute to None.</span></span> <span data-ttu-id="044d3-114">この設定を使用した場合、この属性をキューブの集計に含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="044d3-114">By using this setting, no aggregation for the cube can include this attribute.</span></span>  
  
 `Unrestricted`  
 <span data-ttu-id="044d3-115">属性の集計使用法の設定を `Unrestricted` に設定する場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="044d3-115">Select to set the aggregation usage setting for the attribute to `Unrestricted`.</span></span> <span data-ttu-id="044d3-116">この設定を使用した場合、集計デザイナーに対する制限は行われません。ただし、この設定でも、属性を評価して属性が重要な集計候補であるかどうかを判断する必要があります。</span><span class="sxs-lookup"><span data-stu-id="044d3-116">By using this setting, no restrictions are put on the aggregation designer; however, the attribute must still be evaluated to determine whether it is a valuable aggregation candidate.</span></span>  
  
 <span data-ttu-id="044d3-117">**[すべて既定値に設定]**</span><span class="sxs-lookup"><span data-stu-id="044d3-117">**Set All to Default**</span></span>  
 <span data-ttu-id="044d3-118">すべての属性の集計使用法の設定を Default に設定する場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="044d3-118">Select to set the aggregation usage settings for all attributes to Default.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="044d3-119">参照</span><span class="sxs-lookup"><span data-stu-id="044d3-119">See Also</span></span>  
 <span data-ttu-id="044d3-120">[集計のデザインウィザードの F1 ヘルプ](aggregation-design-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="044d3-120">[Aggregation Design Wizard F1 Help](aggregation-design-wizard-f1-help.md) </span></span>  
 [<span data-ttu-id="044d3-121">Analysis Services のウィザード &#40;多次元データ&#41;</span><span class="sxs-lookup"><span data-stu-id="044d3-121">Analysis Services Wizards &#40;Multidimensional Data&#41;</span></span>](analysis-services-wizards-multidimensional-data.md)  
  
  
