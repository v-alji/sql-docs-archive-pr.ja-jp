---
title: データの操作 (MDX) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- MDX [Analysis Services], data manipulation
- data manipulation [MDX]
- Multidimensional Expressions [Analysis Services], data manipulation
ms.assetid: 4865192e-f46b-4ce5-b51c-9e08dbad5b85
author: minewiskan
ms.author: owend
ms.openlocfilehash: 1a1de8b9a3431d79573cd916fa7273b6d8fa7f0b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641323"
---
# <a name="manipulating-data-mdx"></a><span data-ttu-id="8cb3f-102">データの操作 (MDX)</span><span class="sxs-lookup"><span data-stu-id="8cb3f-102">Manipulating Data (MDX)</span></span>

<span data-ttu-id="8cb3f-103">多次元式 (MDX) を使用すると、さまざまな方法でデータを操作できます。</span><span class="sxs-lookup"><span data-stu-id="8cb3f-103">Multidimensional Expressions (MDX) can be used to manipulate the data in a variety of ways.</span></span> <span data-ttu-id="8cb3f-104">この記事に記載されている記事では、MDX 言語でのデータ操作の高度な概念をいくつか取り上げています。</span><span class="sxs-lookup"><span data-stu-id="8cb3f-104">The article listed in this article cover some of the more advanced concepts of data manipulation in the MDX language.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="8cb3f-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="8cb3f-105">In This Section</span></span>

|<span data-ttu-id="8cb3f-106">トピック</span><span class="sxs-lookup"><span data-stu-id="8cb3f-106">Topic</span></span>|<span data-ttu-id="8cb3f-107">説明</span><span class="sxs-lookup"><span data-stu-id="8cb3f-107">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="8cb3f-108">DRILLTHROUGH を使用したソース データの取得 (MDX)</span><span class="sxs-lookup"><span data-stu-id="8cb3f-108">Using DRILLTHROUGH to Retrieve Source Data &#40;MDX&#41;</span></span>](mdx-data-manipulation-retrieve-source-data-using-drillthrough.md)|<span data-ttu-id="8cb3f-109">MDX の [DRILLTHROUGH](/sql/mdx/mdx-data-manipulation-drillthrough) ステートメントを使用して、多次元データ ソースのセルに適用できる変換元データの行セットを取得する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="8cb3f-109">Discusses the use of the MDX [DRILLTHROUGH](/sql/mdx/mdx-data-manipulation-drillthrough) statement to retrieve the rowsets of source data applicable to a cell in a multidimensional data source</span></span>|  
|[<span data-ttu-id="8cb3f-110">RollupChildren 関数の操作 (MDX)</span><span class="sxs-lookup"><span data-stu-id="8cb3f-110">Working with the RollupChildren Function &#40;MDX&#41;</span></span>](mdx-data-manipulation-rollupchildren-function.md)|<span data-ttu-id="8cb3f-111">MDX [Rollupchildren](/sql/mdx/rollupchildren-mdx)の影響について説明します。</span><span class="sxs-lookup"><span data-stu-id="8cb3f-111">Discusses the impact of the MDX [RollupChildren](/sql/mdx/rollupchildren-mdx)</span></span>
|[<span data-ttu-id="8cb3f-112">パス順序と解決順序の概要 (MDX)</span><span class="sxs-lookup"><span data-stu-id="8cb3f-112">Understanding Pass Order and Solve Order &#40;MDX&#41;</span></span>](mdx-data-manipulation-understanding-pass-order-and-solve-order.md)|<span data-ttu-id="8cb3f-113">解決順序の概念を詳しく説明し、その機能がどのように MDX 式、ステートメント、およびスクリプトに影響するかについても説明します。</span><span class="sxs-lookup"><span data-stu-id="8cb3f-113">Details the concepts of solve order, and how this feature affects MDX expressions, statements, and scripts.</span></span>|  

<!-- ??

|[Script for Search and Replace] function on the analysis of multidimensional data.|

GeneMi is removing this commented row because it is unclear what article its link meant to link to.
Also, I had to add its leading '|' character, for consistency to aid bulk automated updated to our markdown source code.

GeneMi , 2019/01/19
-->

## <a name="see-also"></a><span data-ttu-id="8cb3f-114">参照</span><span class="sxs-lookup"><span data-stu-id="8cb3f-114">See Also</span></span>

[<span data-ttu-id="8cb3f-115">MDX クエリの基礎 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="8cb3f-115">MDX Query Fundamentals (Analysis Services)</span></span>](mdx-query-fundamentals-analysis-services.md)
