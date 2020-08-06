---
title: データ型 (データマイニング) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data types [data mining]
- columns [data mining], data types
- data mining [Analysis Services], data types
ms.assetid: 4af5b7db-790b-459c-b2b4-00f0cf6b5ce4
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9027ff3928f40d43f16bb31b52e0c1d52e072847
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645921"
---
# <a name="data-types-data-mining"></a><span data-ttu-id="3f86c-102">データ型 (データ マイニング)</span><span class="sxs-lookup"><span data-stu-id="3f86c-102">Data Types (Data Mining)</span></span>
  <span data-ttu-id="3f86c-103">でマイニングモデルまたはマイニング構造を作成する場合は、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] マイニング構造の各列のデータ型を定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3f86c-103">When you create a mining model or a mining structure in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], you must define the data types for each of the columns in the mining structure.</span></span> <span data-ttu-id="3f86c-104">データ マイニング エンジンは、データ型に基づいて、データ ソース内のデータが数値とテキストのどちらであるか、およびデータをどのように処理するかを判断します。</span><span class="sxs-lookup"><span data-stu-id="3f86c-104">The data type tells the data mining engine whether the data in the data source is numerical or text, and how the data should be processed.</span></span> <span data-ttu-id="3f86c-105">たとえば、ソース データに数値データが含まれる場合、数値を整数として扱うかまたは小数点を使用して扱うかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="3f86c-105">For example, if your source data contains numerical data, you can specify whether the numbers be treated as integers or by using decimal places.</span></span>  
  
 <span data-ttu-id="3f86c-106">各データ型では、1 つまたは複数のコンテンツの種類がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="3f86c-106">Each data type supports one or more content types.</span></span> <span data-ttu-id="3f86c-107">コンテンツの種類を設定することで、マイニング モデルで列のデータをどのように処理または計算するかをカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="3f86c-107">By setting the content type, you can customize the way that data in the column is processed or calculated in the mining model.</span></span>  
  
 <span data-ttu-id="3f86c-108">たとえば、列に数値データが含まれる場合、数値データ型またはテキスト データ型のどちらとしてそのデータを処理するかを選択できます。</span><span class="sxs-lookup"><span data-stu-id="3f86c-108">For example, if you have numeric data in a column, you can choose to handle it either as a numeric or text data type.</span></span> <span data-ttu-id="3f86c-109">数値データ型を選択した場合は、いくつかの異なるコンテンツの種類を設定できます。数値を分離することも、連続値として処理することもできます。</span><span class="sxs-lookup"><span data-stu-id="3f86c-109">If you choose the numeric data type, you can set several different content types: you can discretize the numbers, or handle them as continuous values.</span></span> <span data-ttu-id="3f86c-110">すべてのコンテンツの種類の一覧については、「 [コンテンツの種類 (データ マイニング)](content-types-data-mining.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3f86c-110">For a list of all the content types, see [Content Types &#40;Data Mining&#41;](content-types-data-mining.md).</span></span>  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="3f86c-111">では、では、マイニング構造列に対して次のデータ型がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="3f86c-111">supports the following data types for mining structure columns:</span></span>  
  
|<span data-ttu-id="3f86c-112">データ型</span><span class="sxs-lookup"><span data-stu-id="3f86c-112">Data Type</span></span>|<span data-ttu-id="3f86c-113">サポートされているコンテンツの種類</span><span class="sxs-lookup"><span data-stu-id="3f86c-113">Supported Content Types</span></span>|  
|---------------|-----------------------------|  
|`Text`|<span data-ttu-id="3f86c-114">Cyclical、Discrete、Discretized、Key Sequence、Ordered、Sequence</span><span class="sxs-lookup"><span data-stu-id="3f86c-114">Cyclical, Discrete, Discretized, Key Sequence, Ordered, Sequence</span></span>|  
|`Long`|<span data-ttu-id="3f86c-115">Continuous、Cyclical、Discrete、Discretized、Key、Key Sequence、Key Time、Ordered、Sequence、Time</span><span class="sxs-lookup"><span data-stu-id="3f86c-115">Continuous, Cyclical, Discrete, Discretized, Key, Key Sequence, Key Time, Ordered, Sequence, Time</span></span><br /><br /> <span data-ttu-id="3f86c-116">分類済み</span><span class="sxs-lookup"><span data-stu-id="3f86c-116">Classified</span></span>|  
|`Boolean`|<span data-ttu-id="3f86c-117">Cyclical、Discrete、Ordered</span><span class="sxs-lookup"><span data-stu-id="3f86c-117">Cyclical, Discrete, Ordered</span></span>|  
|`Double`|<span data-ttu-id="3f86c-118">Continuous、Cyclical、Discrete、Discretized、Key、Key Sequence、Key Time、Ordered、Sequence、Time</span><span class="sxs-lookup"><span data-stu-id="3f86c-118">Continuous, Cyclical, Discrete, Discretized, Key, Key Sequence, Key Time, Ordered, Sequence, Time</span></span><br /><br /> <span data-ttu-id="3f86c-119">分類済み</span><span class="sxs-lookup"><span data-stu-id="3f86c-119">Classified</span></span>|  
|`Date`|<span data-ttu-id="3f86c-120">Continuous、Cyclical、Discrete、Discretized、Key、Key Sequence、Key Time、Ordered</span><span class="sxs-lookup"><span data-stu-id="3f86c-120">Continuous, Cyclical, Discrete, Discretized, Key, Key Sequence, Key Time, Ordered</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="3f86c-121">コンテンツの種類のうち Time および Sequence は、サード パーティのアルゴリズムでのみサポートされています。</span><span class="sxs-lookup"><span data-stu-id="3f86c-121">The Time and Sequence content types are only supported by third-party algorithms.</span></span> <span data-ttu-id="3f86c-122">コンテンツの種類 Cyclical および Ordered はサポートされますが、多くのアルゴリズムはこれらを不連続の値として扱い、特別な処理は行いません。</span><span class="sxs-lookup"><span data-stu-id="3f86c-122">The Cyclical and Ordered content types are supported, but most algorithms treat them as discrete values and do not perform special processing.</span></span>  
  
## <a name="specifying-a-data-type"></a><span data-ttu-id="3f86c-123">データ型の指定</span><span class="sxs-lookup"><span data-stu-id="3f86c-123">Specifying a Data Type</span></span>  
 <span data-ttu-id="3f86c-124">データ マイニング拡張機能 (DMX) を使用してマイニング モデルを直接作成する場合は、モデルを定義するときにそれぞれの列のデータ型を定義できます。Analysis Services は、指定されたデータ型を持つ対応するマイニング構造を同時に作成します。</span><span class="sxs-lookup"><span data-stu-id="3f86c-124">If you create the mining model directly by using Data Mining Extensions (DMX), you can define the data type for each column as you define the model, and Analysis Services will create the corresponding mining structure with the specified data types at the same time.</span></span> <span data-ttu-id="3f86c-125">ウィザードを使用してマイニング モデルまたはマイニング構造を作成する場合は、Analysis Services によってデータ型が提案されます。一覧からデータ型を選択することもできます。</span><span class="sxs-lookup"><span data-stu-id="3f86c-125">If you create the mining model or mining structure by using a wizard, Analysis Services will suggest a data type, or you can choose a data type from a list.</span></span>  
  
## <a name="changing-a-data-type"></a><span data-ttu-id="3f86c-126">データ型の変更</span><span class="sxs-lookup"><span data-stu-id="3f86c-126">Changing a Data Type</span></span>  
 <span data-ttu-id="3f86c-127">列のデータ型を変更する場合は、マイニング構造およびその構造に基づくすべてのマイニング モデルを必ず再処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3f86c-127">If you change the data type of a column, you must always reprocess the mining structure and any mining models that are based on that structure.</span></span> <span data-ttu-id="3f86c-128">データ型を変更する場合、特定のモデルでその列を使用できない場合があります。</span><span class="sxs-lookup"><span data-stu-id="3f86c-128">Sometimes if you change the data type, that column can no longer be used in a particular model.</span></span> <span data-ttu-id="3f86c-129">その場合、Analysis Services は、モデルの再処理時にエラーを発生するか、またはその特定の列を除外してモデルを処理します。</span><span class="sxs-lookup"><span data-stu-id="3f86c-129">In that case, Analysis Services will either raise an error when you reprocess the model, or will process the model but leave out that particular column.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f86c-130">参照</span><span class="sxs-lookup"><span data-stu-id="3f86c-130">See Also</span></span>  
 <span data-ttu-id="3f86c-131">[コンテンツの種類 &#40;データマイニング&#41;](content-types-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="3f86c-131">[Content Types &#40;Data Mining&#41;](content-types-data-mining.md) </span></span>  
 <span data-ttu-id="3f86c-132">[DMX&#41;&#40;コンテンツの種類](/sql/dmx/content-types-dmx) </span><span class="sxs-lookup"><span data-stu-id="3f86c-132">[Content Types &#40;DMX&#41;](/sql/dmx/content-types-dmx) </span></span>  
 <span data-ttu-id="3f86c-133">[データマイニングアルゴリズム &#40;Analysis Services-データマイニング&#41;](data-mining-algorithms-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="3f86c-133">[Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining-algorithms-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="3f86c-134">[マイニング構造 &#40;Analysis Services-データマイニング&#41;](mining-structures-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="3f86c-134">[Mining Structures &#40;Analysis Services - Data Mining&#41;](mining-structures-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="3f86c-135">[DMX&#41;&#40;データ型](/sql/dmx/data-types-dmx) </span><span class="sxs-lookup"><span data-stu-id="3f86c-135">[Data Types &#40;DMX&#41;](/sql/dmx/data-types-dmx) </span></span>  
 <span data-ttu-id="3f86c-136">[マイニングモデル列](mining-model-columns.md) </span><span class="sxs-lookup"><span data-stu-id="3f86c-136">[Mining Model Columns](mining-model-columns.md) </span></span>  
 [<span data-ttu-id="3f86c-137">マイニング構造列</span><span class="sxs-lookup"><span data-stu-id="3f86c-137">Mining Structure Columns</span></span>](mining-structure-columns.md)  
  
  
