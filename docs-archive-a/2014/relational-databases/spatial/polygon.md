---
title: 多角形 | Microsoft Docs
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- geometry subtypes [SQL Server]
- Polygon geometry subtype [SQL Server]
ms.assetid: b6a21c3c-fdb8-4187-8229-1c488454fdfb
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 040bb8a2558cc57b1b99a3ce984bec3c8925bc0d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644920"
---
# <a name="polygon"></a><span data-ttu-id="34f06-102">多角形</span><span class="sxs-lookup"><span data-stu-id="34f06-102">Polygon</span></span>
  <span data-ttu-id="34f06-103">は、 `Polygon` 外部境界リングと0個以上の内部リングを定義する一連の点として格納される2次元サーフェイスです。</span><span class="sxs-lookup"><span data-stu-id="34f06-103">A `Polygon` is a two-dimensional surface stored as a sequence of points defining an exterior bounding ring and zero or more interior rings.</span></span>

## <a name="polygon-instances"></a><span data-ttu-id="34f06-104">Polygon インスタンス</span><span class="sxs-lookup"><span data-stu-id="34f06-104">Polygon instances</span></span>
 <span data-ttu-id="34f06-105">`Polygon` インスタンスは、3 つ以上の異なる点を持つリングで形成され、</span><span class="sxs-lookup"><span data-stu-id="34f06-105">A `Polygon` instance can be formed from a ring that has at least three distinct points.</span></span> <span data-ttu-id="34f06-106">`Polygon` インスタンスは空にすることもできます。</span><span class="sxs-lookup"><span data-stu-id="34f06-106">A `Polygon` instance can also be empty.</span></span>

 <span data-ttu-id="34f06-107">`Polygon` の外部および内部のリングは、その境界を定義します。</span><span class="sxs-lookup"><span data-stu-id="34f06-107">The exterior and any interior rings of a `Polygon` define its boundary.</span></span> <span data-ttu-id="34f06-108">リング内の空間は `Polygon` の内部を定義します。</span><span class="sxs-lookup"><span data-stu-id="34f06-108">The space within the rings defines the interior of the `Polygon`.</span></span>

 <span data-ttu-id="34f06-109">次の図は、`Polygon` インスタンスの例です。</span><span class="sxs-lookup"><span data-stu-id="34f06-109">The illustration below shows examples of `Polygon` instances.</span></span>

 <span data-ttu-id="34f06-110">![geometry Polygon インスタンスの例](../../database-engine/media/polygon.gif "geometry Polygon インスタンスの例")</span><span class="sxs-lookup"><span data-stu-id="34f06-110">![Examples of geometry Polygon instances](../../database-engine/media/polygon.gif "Examples of geometry Polygon instances")</span></span>

 <span data-ttu-id="34f06-111">この図は次のことを示しています。</span><span class="sxs-lookup"><span data-stu-id="34f06-111">As shown in the illustration:</span></span>

1.  <span data-ttu-id="34f06-112">図 1 は、外部リングによって境界が定義されている `Polygon` インスタンスです。</span><span class="sxs-lookup"><span data-stu-id="34f06-112">Figure 1 is a `Polygon` instance whose boundary is defined by an exterior ring.</span></span>

2.  <span data-ttu-id="34f06-113">図 2 は、1 つの外部リングと 2 つの内部リングによって境界が定義されている `Polygon` インスタンスです。</span><span class="sxs-lookup"><span data-stu-id="34f06-113">Figure 2 is a `Polygon` instance whose boundary is defined by an exterior ring and two interior rings.</span></span> <span data-ttu-id="34f06-114">内部リングの内側の領域は、`Polygon` インスタンスの外部の一部です。</span><span class="sxs-lookup"><span data-stu-id="34f06-114">The area inside the interior rings is part of the exterior of the `Polygon` instance.</span></span>

3.  <span data-ttu-id="34f06-115">図 3 の `Polygon` インスタンスは、内部リングが 1 つの接点で交差しているため有効です。</span><span class="sxs-lookup"><span data-stu-id="34f06-115">Figure 3 is a valid `Polygon` instance because its interior rings intersect at a single tangent point.</span></span>

### <a name="accepted-instances"></a><span data-ttu-id="34f06-116">許容されるインスタンス</span><span class="sxs-lookup"><span data-stu-id="34f06-116">Accepted instances</span></span>
 <span data-ttu-id="34f06-117">許容される `Polygon` インスタンスとは、例外をスローすることなく  `geometry` 変数または `geography` 変数に格納できるインスタンスです。</span><span class="sxs-lookup"><span data-stu-id="34f06-117">Accepted `Polygon` instances are instances that can be stored in a `geometry` or `geography` variable without throwing an exception.</span></span> <span data-ttu-id="34f06-118">次に示す `Polygon` インスタンスは許容されます。</span><span class="sxs-lookup"><span data-stu-id="34f06-118">The following are accepted `Polygon` instances:</span></span>

-   <span data-ttu-id="34f06-119">空の `Polygon` インスタンス。</span><span class="sxs-lookup"><span data-stu-id="34f06-119">An Empty `Polygon` instance</span></span>

-   <span data-ttu-id="34f06-120">1 つの許容される外部境界リングと 0 個以上の許容される内部リングを持つ `Polygon` インスタンス。</span><span class="sxs-lookup"><span data-stu-id="34f06-120">A `Polygon` instance that has an acceptable exterior ring and zero or more acceptable interior rings</span></span>

 <span data-ttu-id="34f06-121">リングが許容されるためには、次の条件を満たす必要があります。</span><span class="sxs-lookup"><span data-stu-id="34f06-121">The following criteria are needed for a ring to be acceptable.</span></span>

-   <span data-ttu-id="34f06-122">`LineString` インスタンスが許容されていること。</span><span class="sxs-lookup"><span data-stu-id="34f06-122">The `LineString` instance must be accepted.</span></span>

-   <span data-ttu-id="34f06-123">`LineString` インスタンスに 4 つ以上の点があること。</span><span class="sxs-lookup"><span data-stu-id="34f06-123">The `LineString` instance must have at least four points.</span></span>

-   <span data-ttu-id="34f06-124">`LineString` インスタンスの始点と終点が同じであること。</span><span class="sxs-lookup"><span data-stu-id="34f06-124">The starting and ending points of the `LineString` instance must be the same.</span></span>

 <span data-ttu-id="34f06-125">次の例は、許容される `Polygon` インスタンスを示しています。</span><span class="sxs-lookup"><span data-stu-id="34f06-125">The following example shows accepted `Polygon` instances.</span></span>

```
DECLARE @g1 geometry = 'POLYGON EMPTY';
DECLARE @g2 geometry = 'POLYGON((1 1, 3 3, 3 1, 1 1))';
DECLARE @g3 geometry = 'POLYGON((-5 -5, -5 5, 5 5, 5 -5, -5 -5),(0 0, 3 0, 3 3, 0 3, 0 0))';
DECLARE @g4 geometry = 'POLYGON((-5 -5, -5 5, 5 5, 5 -5, -5 -5),(3 0, 6 0, 6 3, 3 3, 3 0))';
DECLARE @g5 geometry = 'POLYGON((1 1, 1 1, 1 1, 1 1))';
```

 <span data-ttu-id="34f06-126">`@g4` および `@g5` が示すように、許容される `Polygon` インスタンスが有効な `Polygon` インスタンスではない場合があります。</span><span class="sxs-lookup"><span data-stu-id="34f06-126">As `@g4` and `@g5` show an accepted `Polygon` instance may not be a valid `Polygon` instance.</span></span> <span data-ttu-id="34f06-127">`@g5` また、Polygon インスタンスが許容されるためには、4 つの点を持つリングのみが含まれている必要があることを示しています。</span><span class="sxs-lookup"><span data-stu-id="34f06-127">`@g5` also shows that a Polygon instance needs to only contain a ring with any four points to be accepted.</span></span>

 <span data-ttu-id="34f06-128">次の例では、`Polygon` インスタンスが許容されないため、`System.FormatException` がスローされます。</span><span class="sxs-lookup"><span data-stu-id="34f06-128">The following examples throw a `System.FormatException` because the `Polygon` instances are not accepted.</span></span>

```
DECLARE @g1 geometry = 'POLYGON((1 1, 3 3, 1 1))';
DECLARE @g2 geometry = 'POLYGON((1 1, 3 3, 3 1, 1 5))';
```

 <span data-ttu-id="34f06-129">`@g1` は、外部リングの `LineString` インスタンスが十分な数の点を含んでいないため、許容されません。</span><span class="sxs-lookup"><span data-stu-id="34f06-129">`@g1` is not accepted because the `LineString` instance for the exterior ring does not contain enough points.</span></span> <span data-ttu-id="34f06-130">`@g2` は、外部リングの `LineString` インスタンスの始点が終点と同じでないため、許容されません。</span><span class="sxs-lookup"><span data-stu-id="34f06-130">`@g2` is not accepted because the starting point of the exterior ring `LineString` instance is not the same as the ending point.</span></span> <span data-ttu-id="34f06-131">次の例では、外部リングは許容されますが、内部リングが許容されません。</span><span class="sxs-lookup"><span data-stu-id="34f06-131">The following example has an acceptable exterior ring, but the interior ring is not acceptable.</span></span> <span data-ttu-id="34f06-132">この場合も `System.FormatException`がスローされます。</span><span class="sxs-lookup"><span data-stu-id="34f06-132">This also throws a `System.FormatException`.</span></span>

```
DECLARE @g geometry = 'POLYGON((-5 -5, -5 5, 5 5, 5 -5, -5 -5),(0 0, 3 0, 0 0))';
```

### <a name="valid-instances"></a><span data-ttu-id="34f06-133">有効なインスタンス</span><span class="sxs-lookup"><span data-stu-id="34f06-133">Valid instances</span></span>
 <span data-ttu-id="34f06-134">`Polygon` の内部リングは、1 つの接点で自身および他の内部リングと接することができますが、`Polygon` の内部リングが互いに交差しているとインスタンスが無効になります。</span><span class="sxs-lookup"><span data-stu-id="34f06-134">The interior rings of a `Polygon` can touch both themselves and each other at single tangent points, but if the interior rings of a `Polygon` cross, the instance is not valid.</span></span>

 <span data-ttu-id="34f06-135">次の例は、有効な `Polygon` インスタンスを示しています。</span><span class="sxs-lookup"><span data-stu-id="34f06-135">The following example shows valid `Polygon` instances.</span></span>

```
DECLARE @g1 geometry = 'POLYGON((-20 -20, -20 20, 20 20, 20 -20, -20 -20))';
DECLARE @g2 geometry = 'POLYGON((-20 -20, -20 20, 20 20, 20 -20, -20 -20), (10 0, 0 10, 0 -10, 10 0))';
DECLARE @g3 geometry = 'POLYGON((-20 -20, -20 20, 20 20, 20 -20, -20 -20), (10 0, 0 10, 0 -10, 10 0), (-10 0, 0 10, -5 -10, -10 0))';
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid();
```

 <span data-ttu-id="34f06-136">`@g3` 2 つの内部リングが 1 つの点で接し、互いに交差していないため、有効です。</span><span class="sxs-lookup"><span data-stu-id="34f06-136">`@g3` is valid because the two interior rings touch at a single point and do not cross each other.</span></span> <span data-ttu-id="34f06-137">次の例は、無効な `Polygon` インスタンスを示しています。</span><span class="sxs-lookup"><span data-stu-id="34f06-137">The following example shows `Polygon` instances that are not valid.</span></span>

```
DECLARE @g1 geometry = 'POLYGON((-20 -20, -20 20, 20 20, 20 -20, -20 -20), (20 0, 0 10, 0 -20, 20 0))';
DECLARE @g2 geometry = 'POLYGON((-20 -20, -20 20, 20 20, 20 -20, -20 -20), (10 0, 0 10, 0 -10, 10 0), (5 0, 1 5, 1 -5, 5 0))';
DECLARE @g3 geometry = 'POLYGON((-20 -20, -20 20, 20 20, 20 -20, -20 -20), (10 0, 0 10, 0 -10, 10 0), (-10 0, 0 10, 0 -10, -10 0))';
DECLARE @g4 geometry = 'POLYGON((-20 -20, -20 20, 20 20, 20 -20, -20 -20), (10 0, 0 10, 0 -10, 10 0), (-10 0, 1 5, 0 -10, -10 0))';
DECLARE @g5 geometry = 'POLYGON((10 0, 0 10, 0 -10, 10 0), (-20 -20, -20 20, 20 20, 20 -20, -20 -20) )';
DECLARE @g6 geometry = 'POLYGON((1 1, 1 1, 1 1, 1 1))';
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid(), @g4.STIsValid(), @g5.STIsValid(), @g6.STIsValid();
```

 <span data-ttu-id="34f06-138">`@g1` 内部リングが 2 か所で外部リングに接しているため、無効です。</span><span class="sxs-lookup"><span data-stu-id="34f06-138">`@g1` is not valid because the inner ring touches the exterior ring in two places.</span></span> <span data-ttu-id="34f06-139">`@g2` 2 つ目の内部リングが 1 つ目の内部リングの内側にあるため、無効です。</span><span class="sxs-lookup"><span data-stu-id="34f06-139">`@g2` is not valid because the second inner ring in within the interior of the first inner ring.</span></span> <span data-ttu-id="34f06-140">`@g3` 2 つの内部リングが連続する複数の点で接しているため、無効です。</span><span class="sxs-lookup"><span data-stu-id="34f06-140">`@g3` is not valid because the two inner rings touch at multiple consecutive points.</span></span> <span data-ttu-id="34f06-141">`@g4` 2 つの内部リングの内部が交差しているため、無効です。</span><span class="sxs-lookup"><span data-stu-id="34f06-141">`@g4` is not valid because the interiors of the two inner rings overlap.</span></span> <span data-ttu-id="34f06-142">`@g5` 外部リングが 1 つ目のリングでないため、無効です。</span><span class="sxs-lookup"><span data-stu-id="34f06-142">`@g5` is not valid because the exterior ring is not the first ring.</span></span> <span data-ttu-id="34f06-143">`@g6` リングが 3 つ以上の異なる点を持たないため、無効です。</span><span class="sxs-lookup"><span data-stu-id="34f06-143">`@g6` is not valid because the ring does not have at least three distinct points.</span></span>

## <a name="examples"></a><span data-ttu-id="34f06-144">例</span><span class="sxs-lookup"><span data-stu-id="34f06-144">Examples</span></span>
 <span data-ttu-id="34f06-145">次の例では、1 つの穴を持つ単純な `geometry``Polygon` インスタンスを作成しています。このインスタンスの SRID は 10 です。</span><span class="sxs-lookup"><span data-stu-id="34f06-145">The following example creates a simple `geometry``Polygon` instance with a hole and SRID 10.</span></span>

```
DECLARE @g geometry;
SET @g = geometry::STPolyFromText('POLYGON((0 0, 0 3, 3 3, 3 0, 0 0), (1 1, 1 2, 2 1, 1 1))', 10);
```

 <span data-ttu-id="34f06-146">無効なインスタンスを入力して、有効な `geometry` インスタンスに変換することもできます。</span><span class="sxs-lookup"><span data-stu-id="34f06-146">Aninstance that is not valid may be entered and converted to a valid `geometry` instance.</span></span> <span data-ttu-id="34f06-147">次の例の `Polygon`は、内部と外部のリングが重なっているため無効です。</span><span class="sxs-lookup"><span data-stu-id="34f06-147">In the following example of a `Polygon`, the interior and exterior rings overlap and the instance is not valid.</span></span>

```
DECLARE @g geometry;
SET @g = geometry::Parse('POLYGON((1 0, 0 1, 1 2, 2 1, 1 0), (2 0, 1 1, 2 2, 3 1, 2 0))');
```

 <span data-ttu-id="34f06-148">次の例では、 `MakeValid()`を使用して、無効なインスタンスを有効なインスタンスにしています。</span><span class="sxs-lookup"><span data-stu-id="34f06-148">In the following example, the invalid instance is made valid with `MakeValid()`.</span></span>

```
SET @g = @g.MakeValid();
SELECT @g.ToString();
```

 <span data-ttu-id="34f06-149">上の例で返される `geometry` インスタンスは `MultiPolygon`です。</span><span class="sxs-lookup"><span data-stu-id="34f06-149">The `geometry` instance returned from the above example is a `MultiPolygon`.</span></span>

```
MULTIPOLYGON (((2 0, 3 1, 2 2, 1.5 1.5, 2 1, 1.5 0.5, 2 0)), ((1 0, 1.5 0.5, 1 1, 1.5 1.5, 1 2, 0 1, 1 0)))
```

 <span data-ttu-id="34f06-150">無効なインスタンスを有効なジオメトリ インスタンスに変換する別の例を示します。</span><span class="sxs-lookup"><span data-stu-id="34f06-150">Here is another example of converting an invalid instance to a valid geometry instance.</span></span> <span data-ttu-id="34f06-151">次の例では、まったく同じ 3 つの点を使用して `Polygon` インスタンスが作成されています。</span><span class="sxs-lookup"><span data-stu-id="34f06-151">In the following example the `Polygon` instance has been created using three points that are exactly the same:</span></span>

```sql
DECLARE @g geometry
SET @g = geometry::Parse('POLYGON((1 3, 1 3, 1 3, 1 3))');
SET @g = @g.MakeValid();
SELECT @g.ToString()
```

 <span data-ttu-id="34f06-152">上の例で返されるジオメトリ インスタンスは `Point(1 3)`です。</span><span class="sxs-lookup"><span data-stu-id="34f06-152">The geometry instance returned above is a `Point(1 3)`.</span></span>  <span data-ttu-id="34f06-153">`Polygon` が `POLYGON((1 3, 1 5, 1 3, 1 3))` の場合、 `MakeValid()` は `LINESTRING(1 3, 1 5)`を返します。</span><span class="sxs-lookup"><span data-stu-id="34f06-153">If the `Polygon` given is `POLYGON((1 3, 1 5, 1 3, 1 3))` then `MakeValid()` would return `LINESTRING(1 3, 1 5)`.</span></span>

## <a name="see-also"></a><span data-ttu-id="34f06-154">参照</span><span class="sxs-lookup"><span data-stu-id="34f06-154">See Also</span></span>
 <span data-ttu-id="34f06-155">[Starea &#40;Geometry データ型&#41;](/sql/t-sql/spatial-geometry/starea-geometry-data-type) [STExteriorRing &#40;](/sql/t-sql/spatial-geometry/stexteriorring-geometry-data-type) geometry データ型&#41;[STInteriorRingN](/sql/t-sql/spatial-geometry/stinteriorringn-geometry-data-type) &#40;geometry データ[型&#41;](/sql/t-sql/spatial-geometry/stnuminteriorring-geometry-data-type) [starea &#40;geometry](/sql/t-sql/spatial-geometry/stcentroid-geometry-data-type)データ型&#41;[stpointonsurface &#40;geometry データ](/sql/t-sql/spatial-geometry/stpointonsurface-geometry-data-type)型&#41;[multipolygon](../spatial/polygon.md) [空間データ &#40;](../spatial/spatial-data-sql-server.md)&#41;&#40;[starea SQL Server geography データ型&#41;](/sql/t-sql/spatial-geography/stisvalid-geography-data-type) [starea &#40;geometry データ型](/sql/t-sql/spatial-geometry/stisvalid-geometry-data-type)&#41;。 &#40;</span><span class="sxs-lookup"><span data-stu-id="34f06-155">[STArea &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/starea-geometry-data-type) [STExteriorRing &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stexteriorring-geometry-data-type) [STNumInteriorRing &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stnuminteriorring-geometry-data-type) [STInteriorRingN &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stinteriorringn-geometry-data-type) [STCentroid &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stcentroid-geometry-data-type) [STPointOnSurface &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stpointonsurface-geometry-data-type) [MultiPolygon](../spatial/polygon.md) [Spatial Data &#40;SQL Server&#41;](../spatial/spatial-data-sql-server.md) [STIsValid &#40;geography Data Type&#41;](/sql/t-sql/spatial-geography/stisvalid-geography-data-type) [STIsValid &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stisvalid-geometry-data-type)</span></span>


