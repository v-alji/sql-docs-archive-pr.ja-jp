---
title: 単純な例でのクエリ軸とスライサー軸の使用 (MDX) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- slicer axis
- query axis [MDX]
ms.assetid: 85bcb26f-5971-4153-b334-61f8d8b475b5
author: minewiskan
ms.author: owend
ms.openlocfilehash: 324f082fd6659592e56af65680bd4aa623c625d9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642990"
---
# <a name="using-query-and-slicer-axes-in-a-simple-example-mdx"></a><span data-ttu-id="98337-102">クエリ軸とスライサー軸を使用する簡単な例 (MDX)</span><span class="sxs-lookup"><span data-stu-id="98337-102">Using Query and Slicer Axes in a Simple Example (MDX)</span></span>
  <span data-ttu-id="98337-103">このトピックでは、簡単な例を使って、クエリ軸とスライサー軸の基本的な指定方法および使用方法を示します。</span><span class="sxs-lookup"><span data-stu-id="98337-103">The simple example presented in this topic illustrates the basics of specifying and using query and slicer axes.</span></span>  
  
## <a name="the-cube"></a><span data-ttu-id="98337-104">キューブ</span><span class="sxs-lookup"><span data-stu-id="98337-104">The Cube</span></span>  
 <span data-ttu-id="98337-105">Route と Time という 2 つの単純なディメンションを持つ TestCube という名前のキューブがあるとします。</span><span class="sxs-lookup"><span data-stu-id="98337-105">A cube, named TestCube, has two simple dimensions named Route and Time.</span></span> <span data-ttu-id="98337-106">各ディメンションには、それぞれ Route および Time という名前のユーザー階層が 1 つずつあります。</span><span class="sxs-lookup"><span data-stu-id="98337-106">Each dimension has only one user hierarchy, named Route and Time respectively.</span></span> <span data-ttu-id="98337-107">キューブのメジャーは Measures ディメンションの一部なので、このキューブには全部で 3 つのディメンションがあります。</span><span class="sxs-lookup"><span data-stu-id="98337-107">Because the measures of the cube are part of the Measures dimension, this cube has three dimensions in all.</span></span>  
  
## <a name="the-query"></a><span data-ttu-id="98337-108">クエリ</span><span class="sxs-lookup"><span data-stu-id="98337-108">The Query</span></span>  
 <span data-ttu-id="98337-109">クエリでは、Packages メジャーを各 Route や Time と比較できるマトリックスが用意されます。</span><span class="sxs-lookup"><span data-stu-id="98337-109">The query is to provide a matrix in which the Packages measure can be compared across routes and times.</span></span>  
  
 <span data-ttu-id="98337-110">以下の MDX クエリの例では、Route および Time 階層がクエリ軸で、Measures ディメンションがスライサー軸です。</span><span class="sxs-lookup"><span data-stu-id="98337-110">In the following MDX query example, the Route and Time hierarchies are the query axes, and the Measures dimension is the slicer axis.</span></span> <span data-ttu-id="98337-111">[Members](/sql/mdx/members-set-mdx) 関数は、MDX が階層またはレベルのメンバーを使ってセットを構築することを示します。</span><span class="sxs-lookup"><span data-stu-id="98337-111">The [Members](/sql/mdx/members-set-mdx) function indicates that MDX will use the members of the hierarchy or level to construct a set.</span></span> <span data-ttu-id="98337-112">`Members` 関数を使用する場合、特定の階層またはレベルの各メンバーを MDX クエリ内で明示的に記述する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="98337-112">The use of the `Members` function means that you do not have to explicitly state each member of a specific hierarchy or level in an MDX query.</span></span>  
  
```  
SELECT  
   { Route.nonground.Members } ON COLUMNS,  
   { Time.[1st half].Members } ON ROWS  
FROM TestCube  
WHERE ( [Measures].[Packages] )  
```  
  
## <a name="the-results"></a><span data-ttu-id="98337-113">結果</span><span class="sxs-lookup"><span data-stu-id="98337-113">The Results</span></span>  
 <span data-ttu-id="98337-114">結果は、COLUMNS 軸ディメンションと ROWS 軸ディメンションの各交差部分に Packages メジャーの値を表示するグリッドになります。</span><span class="sxs-lookup"><span data-stu-id="98337-114">The result is a grid that identifies the value of the Packages measure at each intersection of the COLUMNS and ROWS axis dimensions.</span></span> <span data-ttu-id="98337-115">このグリッドは、以下の表のようになります。</span><span class="sxs-lookup"><span data-stu-id="98337-115">The following table shows how this grid would look.</span></span>  
  
||<span data-ttu-id="98337-116">air</span><span class="sxs-lookup"><span data-stu-id="98337-116">air</span></span>|<span data-ttu-id="98337-117">sea</span><span class="sxs-lookup"><span data-stu-id="98337-117">sea</span></span>|  
|-|---------|---------|  
|<span data-ttu-id="98337-118">1st quarter</span><span class="sxs-lookup"><span data-stu-id="98337-118">1st quarter</span></span>|<span data-ttu-id="98337-119">60</span><span class="sxs-lookup"><span data-stu-id="98337-119">60</span></span>|<span data-ttu-id="98337-120">50</span><span class="sxs-lookup"><span data-stu-id="98337-120">50</span></span>|  
|<span data-ttu-id="98337-121">2nd quarter</span><span class="sxs-lookup"><span data-stu-id="98337-121">2nd quarter</span></span>|<span data-ttu-id="98337-122">45</span><span class="sxs-lookup"><span data-stu-id="98337-122">45</span></span>|<span data-ttu-id="98337-123">45</span><span class="sxs-lookup"><span data-stu-id="98337-123">45</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="98337-124">参照</span><span class="sxs-lookup"><span data-stu-id="98337-124">See Also</span></span>  
 <span data-ttu-id="98337-125">[MDX&#41;&#40;クエリ軸の内容の指定](mdx-query-and-slicer-axes-specify-the-contents-of-a-query-axis.md) </span><span class="sxs-lookup"><span data-stu-id="98337-125">[Specifying the Contents of a Query Axis &#40;MDX&#41;](mdx-query-and-slicer-axes-specify-the-contents-of-a-query-axis.md) </span></span>  
 [<span data-ttu-id="98337-126">スライサー軸の内容の指定 &#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="98337-126">Specifying the Contents of a Slicer Axis &#40;MDX&#41;</span></span>](mdx-query-and-slicer-axes-specify-the-contents-of-a-slicer-axis.md)  
  
  
