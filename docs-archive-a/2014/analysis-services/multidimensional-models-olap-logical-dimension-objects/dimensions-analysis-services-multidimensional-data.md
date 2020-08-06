---
title: ディメンション (Analysis Services-多次元データ) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- OLAP objects [Analysis Services], dimensions
- dimensions [Analysis Services]
- Analysis Services objects, dimensions
ms.assetid: 2b114135-2572-4479-8c81-3ccf0cfeb9f7
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2e0e15d4f74c2c6cec06edaf692199e48534c7e9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738952"
---
# <a name="dimensions-analysis-services---multidimensional-data"></a><span data-ttu-id="e350a-102">ディメンション (Analysis Services - 多次元データ)</span><span class="sxs-lookup"><span data-stu-id="e350a-102">Dimensions (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="e350a-103">で [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は、ディメンションはキューブの基本コンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="e350a-103">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], dimensions are a fundamental component of cubes.</span></span> <span data-ttu-id="e350a-104">ディメンションは、顧客、店舗、従業員など、ユーザーが関心のある分野に関するデータを編成します。</span><span class="sxs-lookup"><span data-stu-id="e350a-104">Dimensions organize data with relation to an area of interest, such as customers, stores, or employees, to users.</span></span> <span data-ttu-id="e350a-105">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のディメンションには、ディメンション テーブルの列に対応する属性が含まれています。</span><span class="sxs-lookup"><span data-stu-id="e350a-105">Dimensions in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] contain attributes that correspond to columns in dimension tables.</span></span> <span data-ttu-id="e350a-106">これらの属性は属性階層として表現されます。またこれらの属性は、ユーザー定義階層に編成したり、基になるディメンション テーブルの列に基づいた親子階層として定義できます。</span><span class="sxs-lookup"><span data-stu-id="e350a-106">These attributes appear as attribute hierarchies and can be organized into user-defined hierarchies, or can be defined as parent-child hierarchies based on columns in the underlying dimension table.</span></span> <span data-ttu-id="e350a-107">階層は、キューブに含まれるメジャーを編成するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="e350a-107">Hierarchies are used to organize measures that are contained in a cube.</span></span> <span data-ttu-id="e350a-108">次のトピックでは、ディメンション、属性、および階層の概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="e350a-108">The following topics provide an overview of dimensions, attributes, and hierarchies.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e350a-109">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="e350a-109">In This Section</span></span>  
  
|<span data-ttu-id="e350a-110">トピック</span><span class="sxs-lookup"><span data-stu-id="e350a-110">Topic</span></span>|<span data-ttu-id="e350a-111">説明</span><span class="sxs-lookup"><span data-stu-id="e350a-111">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="e350a-112">ディメンションの概要 &#40;Analysis Services - 多次元データ&#41;</span><span class="sxs-lookup"><span data-stu-id="e350a-112">Introduction to Dimensions &#40;Analysis Services - Multidimensional Data&#41;</span></span>](dimensions-analysis-services-multidimensional-data.md)|<span data-ttu-id="e350a-113">ディメンションの概念について説明します。</span><span class="sxs-lookup"><span data-stu-id="e350a-113">Provides an overview of dimension concepts.</span></span>|  
|[<span data-ttu-id="e350a-114">属性と属性階層</span><span class="sxs-lookup"><span data-stu-id="e350a-114">Attributes and Attribute Hierarchies</span></span>](attributes-and-attribute-hierarchies.md)|<span data-ttu-id="e350a-115">属性および属性階層について説明します。</span><span class="sxs-lookup"><span data-stu-id="e350a-115">Describes attributes and attribute hierarchies.</span></span>|  
|[<span data-ttu-id="e350a-116">ユーザー階層</span><span class="sxs-lookup"><span data-stu-id="e350a-116">User Hierarchies</span></span>](user-hierarchies.md)|<span data-ttu-id="e350a-117">属性のユーザー定義階層について説明します。</span><span class="sxs-lookup"><span data-stu-id="e350a-117">Describes user-defined hierarchies of attributes.</span></span>|  
|[<span data-ttu-id="e350a-118">書き込み許可ディメンション</span><span class="sxs-lookup"><span data-stu-id="e350a-118">Write-Enabled Dimensions</span></span>](write-enabled-dimensions.md)|<span data-ttu-id="e350a-119">書き込み許可ディメンションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="e350a-119">Describes write-enabled dimensions.</span></span>|  
|[<span data-ttu-id="e350a-120">ディメンションの翻訳</span><span class="sxs-lookup"><span data-stu-id="e350a-120">Dimension Translations</span></span>](dimension-translations.md)|<span data-ttu-id="e350a-121">ディメンション メタデータの翻訳について説明します。</span><span class="sxs-lookup"><span data-stu-id="e350a-121">Describes translations of dimension meta data.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e350a-122">参照</span><span class="sxs-lookup"><span data-stu-id="e350a-122">See Also</span></span>  
 <span data-ttu-id="e350a-123">[多次元モデル内のディメンション](../multidimensional-models/dimensions-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="e350a-123">[Dimensions in Multidimensional Models](../multidimensional-models/dimensions-in-multidimensional-models.md) </span></span>  
 [<span data-ttu-id="e350a-124">キューブオブジェクト &#40;Analysis Services-多次元データ&#41;</span><span class="sxs-lookup"><span data-stu-id="e350a-124">Cube Objects &#40;Analysis Services - Multidimensional Data&#41;</span></span>](../multidimensional-models-olap-logical-cube-objects/cube-objects-analysis-services-multidimensional-data.md)  
  
  
