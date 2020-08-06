---
title: 分類済みの列 (データマイニング) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- content types [data mining]
- STDEV column
- VARIANCE column
- PROBABLILITY column
- PROBABILITY_STDEV column
- columns [data mining], classified
- classified columns [data mining]
- PROBABILITY_VARIANCE column
- SUPPORT column
ms.assetid: 68bf3b78-dc12-497c-898f-b43a45646123
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5c264dfb6a97b8b8f576966e8929f6b0dc51e4ed
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643641"
---
# <a name="classified-columns-data-mining"></a><span data-ttu-id="c8caa-102">分類済みの列 (データ マイニング)</span><span class="sxs-lookup"><span data-stu-id="c8caa-102">Classified Columns (Data Mining)</span></span>
  <span data-ttu-id="c8caa-103">分類済みの列を定義する場合は、マイニング構造内の現在の列と別の列の間でリレーションシップを作成します。</span><span class="sxs-lookup"><span data-stu-id="c8caa-103">When you define a classified column, you create a relationship between the current column and another column in the mining structure.</span></span> <span data-ttu-id="c8caa-104">マイニング構造内で分類済みの列として指定した列のデータには、その構造内の別の列の値について説明した分類情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="c8caa-104">The data in the mining structure column that you designate as the classified column contains categorical information that describes the values in another column in the mining structure.</span></span>  
  
 <span data-ttu-id="c8caa-105">たとえば、数値データを含んだ 2 つの列があるとします。一方の列 [Yearly Purchases] には、特定の暦年における顧客ごとの年間合計購入金額が格納され、もう一方の [Standard Deviations] 列には、これらの値の標準偏差が格納されます。</span><span class="sxs-lookup"><span data-stu-id="c8caa-105">For example, suppose you have two columns with numerical data: one column, [Yearly Purchases], contains the total yearly purchases per customer for a specific calendar year, and the other column, [Standard Deviations], contains the standard deviations for those values.</span></span> <span data-ttu-id="c8caa-106">この場合、[Yearly Purchases] 列を分類済みの列に指定すると、モデルはこのリレーションシップを分析で使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="c8caa-106">In this case you could designate the [Yearly Purchases] column as the classified column, and the model would be able to use this relationship in analysis.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c8caa-107">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] に用意されているアルゴリズムでは、分類済みの列の使用がサポートされていません。この機能はカスタム アルゴリズムの作成用に提供されています。</span><span class="sxs-lookup"><span data-stu-id="c8caa-107">The algorithms provided in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] do not support the use of classified columns; this feature is provided for use in creating custom algorithms.</span></span>  
  
## <a name="defining-a-classified-column"></a><span data-ttu-id="c8caa-108">分類済みの列の定義</span><span class="sxs-lookup"><span data-stu-id="c8caa-108">Defining a Classified Column</span></span>  
 <span data-ttu-id="c8caa-109">分類済みの列のデータ型は、`Long` または `Double` にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="c8caa-109">The data type of a classified column must be either `Long` or `Double`.</span></span>  
  
 <span data-ttu-id="c8caa-110">次の一覧では、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] で分類済みの列に対してサポートされているコンテンツの種類について説明します。</span><span class="sxs-lookup"><span data-stu-id="c8caa-110">The following list describes the content types that [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] supports for classified columns.</span></span>  
  
 <span data-ttu-id="c8caa-111">**確率**</span><span class="sxs-lookup"><span data-stu-id="c8caa-111">**PROBABILITY**</span></span>  
 <span data-ttu-id="c8caa-112">この列の値は、関連付けられている値の確率であり、0 から 1 までの数値です。</span><span class="sxs-lookup"><span data-stu-id="c8caa-112">The value in the column is the probability of the associated value, and is a number between 0 and 1.</span></span>  
  
 <span data-ttu-id="c8caa-113">**SV**</span><span class="sxs-lookup"><span data-stu-id="c8caa-113">**VARIANCE**</span></span>  
 <span data-ttu-id="c8caa-114">この列の値は、関連付けられている値の分散です。</span><span class="sxs-lookup"><span data-stu-id="c8caa-114">The value in the column is the variance of the associated value.</span></span>  
  
 <span data-ttu-id="c8caa-115">**STDEV**</span><span class="sxs-lookup"><span data-stu-id="c8caa-115">**STDEV**</span></span>  
 <span data-ttu-id="c8caa-116">この列の値は、関連付けられている値の標準偏差です。</span><span class="sxs-lookup"><span data-stu-id="c8caa-116">The value in the column is the standard deviation of the associated value.</span></span>  
  
 <span data-ttu-id="c8caa-117">**PROBABILITY_VARIANCE**</span><span class="sxs-lookup"><span data-stu-id="c8caa-117">**PROBABILITY_VARIANCE**</span></span>  
 <span data-ttu-id="c8caa-118">この列の値は、関連付けられている値の確率の分散です。</span><span class="sxs-lookup"><span data-stu-id="c8caa-118">The value in the column is the variance of the probability for the associated value.</span></span>  
  
 <span data-ttu-id="c8caa-119">**PROBABILITY_STDEV**</span><span class="sxs-lookup"><span data-stu-id="c8caa-119">**PROBABILITY_STDEV**</span></span>  
 <span data-ttu-id="c8caa-120">この列の値は、関連付けられている値の確率の標準偏差です。</span><span class="sxs-lookup"><span data-stu-id="c8caa-120">The value in the column is the standard deviation of the probability for the associated value.</span></span>  
  
 <span data-ttu-id="c8caa-121">**ご**</span><span class="sxs-lookup"><span data-stu-id="c8caa-121">**SUPPORT**</span></span>  
 <span data-ttu-id="c8caa-122">この列の値は、関連付けられている値の重み (ケース レプリケーション係数) です。</span><span class="sxs-lookup"><span data-stu-id="c8caa-122">The value in the column is the weight, or case replication factor, of the associated value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8caa-123">参照</span><span class="sxs-lookup"><span data-stu-id="c8caa-123">See Also</span></span>  
 <span data-ttu-id="c8caa-124">[コンテンツの種類 &#40;データマイニング&#41;](content-types-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="c8caa-124">[Content Types &#40;Data Mining&#41;](content-types-data-mining.md) </span></span>  
 <span data-ttu-id="c8caa-125">[マイニング構造 &#40;Analysis Services-データマイニング&#41;](mining-structures-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="c8caa-125">[Mining Structures &#40;Analysis Services - Data Mining&#41;](mining-structures-analysis-services-data-mining.md) </span></span>  
 [<span data-ttu-id="c8caa-126">データ型 (データ マイニング)</span><span class="sxs-lookup"><span data-stu-id="c8caa-126">Data Types &#40;Data Mining&#41;</span></span>](data-types-data-mining.md)  
  
  
