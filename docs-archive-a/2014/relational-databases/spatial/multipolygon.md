---
title: MultiPolygon | Microsoft Docs
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- MultiPolygon geometry subtype [SQL Server]
- geometry subtypes [SQL Server]
ms.assetid: 2c5db358-2a16-49d9-aac5-a74e86813932
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: f18fd2485c9b2e62586d9f3e81f76f6cf680dbfc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644924"
---
# <a name="multipolygon"></a><span data-ttu-id="6cd35-102">MultiPolygon</span><span class="sxs-lookup"><span data-stu-id="6cd35-102">MultiPolygon</span></span>
  <span data-ttu-id="6cd35-103">`MultiPolygon` インスタンスは、0 個以上の `Polygon` インスタンスのコレクションです。</span><span class="sxs-lookup"><span data-stu-id="6cd35-103">A `MultiPolygon` instance is a collection of zero or more `Polygon` instances.</span></span>

## <a name="polygon-instances"></a><span data-ttu-id="6cd35-104">Polygon インスタンス</span><span class="sxs-lookup"><span data-stu-id="6cd35-104">Polygon Instances</span></span>
 <span data-ttu-id="6cd35-105">次の図は、`MultiPolygon` インスタンスの例です。</span><span class="sxs-lookup"><span data-stu-id="6cd35-105">The illustration below shows examples of `MultiPolygon` instances.</span></span>

 <span data-ttu-id="6cd35-106">![geometry MultiPolygon インスタンスの例](../../database-engine/media/multipolygon.gif "geometry MultiPolygon インスタンスの例")</span><span class="sxs-lookup"><span data-stu-id="6cd35-106">![Examples of geometry MultiPolygon instances](../../database-engine/media/multipolygon.gif "Examples of geometry MultiPolygon instances")</span></span>

 <span data-ttu-id="6cd35-107">この図は次のことを示しています。</span><span class="sxs-lookup"><span data-stu-id="6cd35-107">As shown in the illustration:</span></span>

-   <span data-ttu-id="6cd35-108">図 1 は、2 つの `Polygon` 要素を持つ `MultiPolygon` インスタンスです。</span><span class="sxs-lookup"><span data-stu-id="6cd35-108">Figure 1 is a `MultiPolygon` instance with two `Polygon` elements.</span></span> <span data-ttu-id="6cd35-109">境界は、2 つの外部リングと 3 つの内部リングによって定義されています。</span><span class="sxs-lookup"><span data-stu-id="6cd35-109">The boundary is defined by the two exterior rings and the three interior rings.</span></span>

-   <span data-ttu-id="6cd35-110">図 2 は、2 つの `MultiPolygon` 要素を持つ `Polygon` インスタンスです。</span><span class="sxs-lookup"><span data-stu-id="6cd35-110">Figure 2 is a `MultiPolygon` instance with two `Polygon` elements.</span></span> <span data-ttu-id="6cd35-111">境界は、2 つの外部リングと 3 つの内部リングによって定義されています。</span><span class="sxs-lookup"><span data-stu-id="6cd35-111">The boundary is defined by the two exterior rings and the three interior rings.</span></span> <span data-ttu-id="6cd35-112">2 つの `Polygon` 要素は接点で交差しています。</span><span class="sxs-lookup"><span data-stu-id="6cd35-112">The two `Polygon` elements intersect at a tangent point.</span></span>

### <a name="accepted-instances"></a><span data-ttu-id="6cd35-113">許容されるインスタンス</span><span class="sxs-lookup"><span data-stu-id="6cd35-113">Accepted Instances</span></span>
 <span data-ttu-id="6cd35-114">次のいずれかの条件が満たされている場合、`MultiPolygon` インスタンスは許容されます。</span><span class="sxs-lookup"><span data-stu-id="6cd35-114">A `MultiPolygon` instance is accepted one of the following conditions is met.</span></span>

-   <span data-ttu-id="6cd35-115">空の `MultiPolygon` インスタンスである。</span><span class="sxs-lookup"><span data-stu-id="6cd35-115">It is an empty `MultiPolygon` instance.</span></span>

-   <span data-ttu-id="6cd35-116">`MultiPolygon` インスタンスを構成するすべてのインスタンスが、許容される `Polygon` インスタンスである。</span><span class="sxs-lookup"><span data-stu-id="6cd35-116">All instances comprising the `MultiPolygon` instance are accepted `Polygon` instances.</span></span> <span data-ttu-id="6cd35-117">許容されるインスタンスの詳細につい `Polygon` ては、「 [Polygon](../spatial/polygon.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6cd35-117">For more information on accepted `Polygon` instances, see [Polygon](../spatial/polygon.md).</span></span>

 <span data-ttu-id="6cd35-118">次の例は、許容されるインスタンスを示して `MultiPolygon` います。</span><span class="sxs-lookup"><span data-stu-id="6cd35-118">The following examples show accepted `MultiPolygon` instances.</span></span>

```
DECLARE @g1 geometry = 'MULTIPOLYGON EMPTY';
DECLARE @g2 geometry = 'MULTIPOLYGON(((1 1, 1 -1, -1 -1, -1 1, 1 1)),((1 1, 3 1, 3 3, 1 3, 1 1)))';
DECLARE @g3 geometry = 'MULTIPOLYGON(((2 2, 2 -2, -2 -2, -2 2, 2 2)),((1 1, 3 1, 3 3, 1 3, 1 1)))';
```

 <span data-ttu-id="6cd35-119">次の例に、 `System.FormatException`をスローする MultiPolygon インスタンスを示します。</span><span class="sxs-lookup"><span data-stu-id="6cd35-119">The following example shows a MultiPolygon instance that will throw a `System.FormatException`.</span></span>

```
DECLARE @g geometry = 'MULTIPOLYGON(((1 1, 1 -1, -1 -1, -1 1, 1 1)),((1 1, 3 1, 3 3)))';
```

 <span data-ttu-id="6cd35-120">MultiPolygon の 2 番目のインスタンスは LineString インスタンスであり、許容される Polygon インスタンスではありません。</span><span class="sxs-lookup"><span data-stu-id="6cd35-120">The second instance in the MultiPolygon is a LineString instance and not an accepted Polygon instance.</span></span>

### <a name="valid-instances"></a><span data-ttu-id="6cd35-121">有効なインスタンス</span><span class="sxs-lookup"><span data-stu-id="6cd35-121">Valid Instances</span></span>
 <span data-ttu-id="6cd35-122">`MultiPolygon` インスタンスは、空の `MultiPolygon` インスタンスであるか、次の条件を満たす場合に有効です。</span><span class="sxs-lookup"><span data-stu-id="6cd35-122">A `MultiPolygon` instance is valid if it is an empty `MultiPolygon` instance or if it meets the following criteria.</span></span>

1.  <span data-ttu-id="6cd35-123">インスタンスを構成するすべてのインスタンス `MultiPolygon` が有効な `Polygon` インスタンスです。</span><span class="sxs-lookup"><span data-stu-id="6cd35-123">All of the instances comprising the `MultiPolygon` instance are valid `Polygon` instances.</span></span> <span data-ttu-id="6cd35-124">有効な `Polygon` インスタンスについては、「 [Polygon](../spatial/polygon.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6cd35-124">For valid `Polygon` instances, see [Polygon](../spatial/polygon.md).</span></span>

2.  <span data-ttu-id="6cd35-125">`Polygon` インスタンスを構成する `MultiPolygon` インスタンスが重なっていない。</span><span class="sxs-lookup"><span data-stu-id="6cd35-125">None of the `Polygon` instances comprising the `MultiPolygon` instance overlap.</span></span>

 <span data-ttu-id="6cd35-126">次の例に、2 つの有効な `MultiPolygon` インスタンスと 1 つの無効な `MultiPolygon` インスタンスを示します。</span><span class="sxs-lookup"><span data-stu-id="6cd35-126">The following example shows two valid `MultiPolygon` instances and one invalid `MultiPolygon` instance.</span></span>

```
DECLARE @g1 geometry = 'MULTIPOLYGON EMPTY';
DECLARE @g2 geometry = 'MULTIPOLYGON(((1 1, 1 -1, -1 -1, -1 1, 1 1)),((1 1, 3 1, 3 3, 1 3, 1 1)))';
DECLARE @g3 geometry = 'MULTIPOLYGON(((2 2, 2 -2, -2 -2, -2 2, 2 2)),((1 1, 3 1, 3 3, 1 3, 1 1)))';
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid();
```

 <span data-ttu-id="6cd35-127">`@g2` は、2 つの `Polygon` インスタンスが 1 つの接点のみで接しているため有効です。</span><span class="sxs-lookup"><span data-stu-id="6cd35-127">`@g2` is valid because the two `Polygon` instances touch only at a tangent point.</span></span> <span data-ttu-id="6cd35-128">`@g3` は、2 つの `Polygon` インスタンスの内部が互いに重なっているため無効です。</span><span class="sxs-lookup"><span data-stu-id="6cd35-128">`@g3` is not valid because the interiors of the two `Polygon` instances overlap each other.</span></span>

## <a name="examples"></a><span data-ttu-id="6cd35-129">例</span><span class="sxs-lookup"><span data-stu-id="6cd35-129">Examples</span></span>
 <span data-ttu-id="6cd35-130">次の例では、 `geometry``MultiPolygon` インスタンスを作成し、2 つ目の構成要素の Well-Known Text (WKT) を返します。</span><span class="sxs-lookup"><span data-stu-id="6cd35-130">The following example shows the creation of a `geometry``MultiPolygon` instance and returns the Well-Known Text (WKT) of the second component.</span></span>

```
DECLARE @g geometry;
SET @g = geometry::Parse('MULTIPOLYGON(((0 0, 0 3, 3 3, 3 0, 0 0), (1 1, 1 2, 2 1, 1 1)), ((9 9, 9 10, 10 9, 9 9)))');
SELECT @g.STGeometryN(2).STAsText();
```

 <span data-ttu-id="6cd35-131">次の例では、空の `MultiPolygon` インスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="6cd35-131">This example instantiates an empty `MultiPolygon` instance.</span></span>

```
DECLARE @g geometry;
SET @g = geometry::Parse('MULTIPOLYGON EMPTY');
```

## <a name="see-also"></a><span data-ttu-id="6cd35-132">参照</span><span class="sxs-lookup"><span data-stu-id="6cd35-132">See Also</span></span>
 <span data-ttu-id="6cd35-133">[Polygon](../spatial/polygon.md) [starea &#40;geometry データ型&#41;](/sql/t-sql/spatial-geometry/starea-geometry-data-type) [starea &#40;geometry データ型&#41;](/sql/t-sql/spatial-geometry/stcentroid-geometry-data-type) [stpointonsurface &#40;geometry データ型&#41;](/sql/t-sql/spatial-geometry/stpointonsurface-geometry-data-type) [空間データ &#40;](../spatial/spatial-data-sql-server.md) SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="6cd35-133">[Polygon](../spatial/polygon.md) [STArea &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/starea-geometry-data-type) [STCentroid &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stcentroid-geometry-data-type) [STPointOnSurface &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stpointonsurface-geometry-data-type) [Spatial Data &#40;SQL Server&#41;](../spatial/spatial-data-sql-server.md)</span></span>


