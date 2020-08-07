---
title: クエリ軸とスライサー軸を使用したクエリの制限 (MDX) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Multidimensional Expressions [Analysis Services], axes
- queries [MDX], axes
- axes [MDX]
- MDX [Analysis Services], axes
ms.assetid: a64b8172-cd73-42f9-8847-52e967b9697a
author: minewiskan
ms.author: owend
ms.openlocfilehash: ed4d50aa40d2915c60f887e64cdc3ef8a6d52c5c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718765"
---
# <a name="restricting-the-query-with-query-and-slicer-axes-mdx"></a><span data-ttu-id="c4240-102">クエリ軸とスライサー軸によるクエリの制限 (MDX)</span><span class="sxs-lookup"><span data-stu-id="c4240-102">Restricting the Query with Query and Slicer Axes (MDX)</span></span>
  <span data-ttu-id="c4240-103">多次元式 (MDX) の SELECT ステートメントを作成する場合、アプリケーションでは通常、キューブを調べ、階層のセットを以下の 2 つのサブセットに分けます。</span><span class="sxs-lookup"><span data-stu-id="c4240-103">When formulating a Multidimensional Expressions (MDX) SELECT statement, an application typically examines a cube and divides the set of hierarchies into two subsets:</span></span>  
  
-   <span data-ttu-id="c4240-104">**クエリ軸**-複数のメンバーについてデータを取得する階層のセット。</span><span class="sxs-lookup"><span data-stu-id="c4240-104">**Query axes**-the set of hierarchies from which data is retrieved for multiple members.</span></span> <span data-ttu-id="c4240-105">クエリ軸の詳細については、「[クエリ軸の内容の指定 &#40;MDX&#41;](mdx-query-and-slicer-axes-specify-the-contents-of-a-query-axis.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c4240-105">For more information about query axes, see [Specifying the Contents of a Query Axis &#40;MDX&#41;](mdx-query-and-slicer-axes-specify-the-contents-of-a-query-axis.md).</span></span>  
  
-   <span data-ttu-id="c4240-106">**スライサー軸**-1 つのメンバーについてデータを取得する階層のセット。</span><span class="sxs-lookup"><span data-stu-id="c4240-106">**Slicer axis**-the set of hierarchies from which data is retrieved for a single member.</span></span> <span data-ttu-id="c4240-107">スライサー軸の詳細については、「[スライサー軸の内容の指定 &#40;MDX&#41;](mdx-query-and-slicer-axes-specify-the-contents-of-a-slicer-axis.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c4240-107">For more information about the slicer axis, see [Specifying the Contents of a Slicer Axis &#40;MDX&#41;](mdx-query-and-slicer-axes-specify-the-contents-of-a-slicer-axis.md).</span></span>  
  
 <span data-ttu-id="c4240-108">クエリ軸とスライサー軸は、クエリの実行対象であるキューブの複数の階層で構成できるため、これらの用語によって、クエリの実行対象であるキューブで使用される階層と、MDX クエリで返されたキューブで作成される階層とを区別しています。</span><span class="sxs-lookup"><span data-stu-id="c4240-108">Because query and slicer axes can be constructed from multiple hierarchies of the cube to be queried, these terms are used to differentiate the hierarchies used by the cube that is to be queried from the hierarchies created in the cube returned by an MDX query.</span></span>  
  
 <span data-ttu-id="c4240-109">クエリ軸のスライサー軸を使用する単純な例については、「[Using Query and Slicer Axes in a Simple Example &#40;MDX&#41;](mdx-query-and-slicer-axes-using-axes-in-a-simple-example.md)」(クエリ軸とスライサー軸を使用する簡単な例) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c4240-109">To see a simple example using query and slicer axes, see [Using Query and Slicer Axes in a Simple Example &#40;MDX&#41;](mdx-query-and-slicer-axes-using-axes-in-a-simple-example.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4240-110">参照</span><span class="sxs-lookup"><span data-stu-id="c4240-110">See Also</span></span>  
 <span data-ttu-id="c4240-111">[MDX&#41;&#40;メンバー、組、およびセットの操作](working-with-members-tuples-and-sets-mdx.md) </span><span class="sxs-lookup"><span data-stu-id="c4240-111">[Working with Members, Tuples, and Sets &#40;MDX&#41;](working-with-members-tuples-and-sets-mdx.md) </span></span>  
 [<span data-ttu-id="c4240-112">MDX クエリの基礎 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="c4240-112">MDX Query Fundamentals &#40;Analysis Services&#41;</span></span>](mdx-query-fundamentals-analysis-services.md)  
  
  
