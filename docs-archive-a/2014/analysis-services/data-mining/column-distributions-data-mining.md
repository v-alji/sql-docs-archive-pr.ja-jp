---
title: 列の分布 (データマイニング) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- normal distribution type [data mining]
- uniform distribution type [data mining]
- columns [data mining], distributions
- log normal distribution type [data mining]
- continuous columns
- distributions [data mining]
ms.assetid: 87e700de-32be-4bc8-b01d-ba4ee1ab48de
author: minewiskan
ms.author: owend
ms.openlocfilehash: 29aad33535c4cc4d9baf4c453249ce3b51595e78
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645931"
---
# <a name="column-distributions-data-mining"></a><span data-ttu-id="c2e9c-102">列の分布 (データ マイニング)</span><span class="sxs-lookup"><span data-stu-id="c2e9c-102">Column Distributions (Data Mining)</span></span>
  <span data-ttu-id="c2e9c-103">では [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 、マイニングモデルの作成時にアルゴリズムがこれらの列のデータを処理する方法に影響を与えるように、マイニング構造で列の分布を定義できます。</span><span class="sxs-lookup"><span data-stu-id="c2e9c-103">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], you can define column distributions in a mining structure, to affect how algorithms process the data in those columns when you create mining models.</span></span> <span data-ttu-id="c2e9c-104">いくつかのアルゴリズムは、列が値の一般的な分布を含むことが認識された場合、モデルを処理する前にすべての連続列の分布を定義するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="c2e9c-104">For some algorithms, it is useful to define the distribution of any continuous columns before you process the model, if the columns are known to contain common distributions of values.</span></span> <span data-ttu-id="c2e9c-105">分布が定義されない場合、アルゴリズムが持つデータを解釈するための情報が少ないため、分布が定義されたときよりも、マイニング モデルの結果が実際の予測より小さくなる場合があります。</span><span class="sxs-lookup"><span data-stu-id="c2e9c-105">If you do not define the distributions, the resulting mining models may produce less accurate predictions than if the distributions were defined, because the algorithms will have less information from which to interpret the data.</span></span>

 <span data-ttu-id="c2e9c-106">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] で使用できるアルゴリズムでは、次の分布の種類がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="c2e9c-106">The algorithms that are available in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] support the following distribution types:</span></span>

 <span data-ttu-id="c2e9c-107">`Normal`連続列の値は、正規分布のヒストグラムを形成します。</span><span class="sxs-lookup"><span data-stu-id="c2e9c-107">`Normal` The values for the continuous column form a histogram with a normal distribution.</span></span>

 <span data-ttu-id="c2e9c-108">![正規分布のヒストグラム](../media/normal-distribution.gif "正規分布のヒストグラム")</span><span class="sxs-lookup"><span data-stu-id="c2e9c-108">![Histogram with normal distribution](../media/normal-distribution.gif "Histogram with normal distribution")</span></span>

 <span data-ttu-id="c2e9c-109">`Log Normal`連続列の値は、曲線が上端に長くなり、下側に傾斜するヒストグラムを形成します。</span><span class="sxs-lookup"><span data-stu-id="c2e9c-109">`Log Normal` The values for the continuous column form a histogram, where the curve is elongated at the upper end and is skewed toward the lower end.</span></span>

 <span data-ttu-id="c2e9c-110">![対数正規分布のヒストグラム](../media/log-normal-distribution.gif "対数正規分布のヒストグラム")</span><span class="sxs-lookup"><span data-stu-id="c2e9c-110">![Histogram with log normal distribution](../media/log-normal-distribution.gif "Histogram with log normal distribution")</span></span>

 <span data-ttu-id="c2e9c-111">`Uniform`連続列の値は、すべての値が等しくなる可能性があるフラットな曲線を形成します。</span><span class="sxs-lookup"><span data-stu-id="c2e9c-111">`Uniform` The values for the continuous column form a flat curve, in which all values are equally likely.</span></span>

 <span data-ttu-id="c2e9c-112">![単一ディストリビューションのヒストグラム](../media/uniform-distribution.gif "単一ディストリビューションのヒストグラム")</span><span class="sxs-lookup"><span data-stu-id="c2e9c-112">![Histogram with uniform distribution](../media/uniform-distribution.gif "Histogram with uniform distribution")</span></span>

 <span data-ttu-id="c2e9c-113">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] が提供するアルゴリズムの詳細については、「[データ マイニング アルゴリズム &#40;Analysis Services - データ マイニング&#41;](data-mining-algorithms-analysis-services-data-mining.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c2e9c-113">For more information about the algorithms that [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] provides, see [Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining-algorithms-analysis-services-data-mining.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c2e9c-114">参照</span><span class="sxs-lookup"><span data-stu-id="c2e9c-114">See Also</span></span>
 <span data-ttu-id="c2e9c-115">[コンテンツの種類 &#40;データマイニング&#41;](content-types-data-mining.md) [マイニング構造 &#40;Analysis Services データマイニング](mining-structures-analysis-services-data-mining.md)&#41;データマイニング &#40;&#41;の[分離方法](discretization-methods-data-mining.md)&#40;[DMX](/sql/dmx/distributions-dmx)&#41;[マイニング構造列](mining-structure-columns.md)</span><span class="sxs-lookup"><span data-stu-id="c2e9c-115">[Content Types &#40;Data Mining&#41;](content-types-data-mining.md) [Mining Structures &#40;Analysis Services - Data Mining&#41;](mining-structures-analysis-services-data-mining.md) [Discretization Methods &#40;Data Mining&#41;](discretization-methods-data-mining.md) [Distributions &#40;DMX&#41;](/sql/dmx/distributions-dmx) [Mining Structure Columns](mining-structure-columns.md)</span></span>


