---
title: CircularString | Microsoft Docs
ms.custom: ''
ms.date: 10/18/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: 9fe06b03-d98c-4337-9f89-54da98f49f9f
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: c701cdc2e8538a5b91093e17714fd9f6508d1c4c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632321"
---
# <a name="circularstring"></a><span data-ttu-id="aad83-102">CircularString</span><span class="sxs-lookup"><span data-stu-id="aad83-102">CircularString</span></span>
  <span data-ttu-id="aad83-103">`CircularString` は、0 個以上の連続する円弧セグメントのコレクションです。</span><span class="sxs-lookup"><span data-stu-id="aad83-103">A `CircularString` is a collection of zero or more continuous circular arc segments.</span></span> <span data-ttu-id="aad83-104">円弧セグメントは、2 次元平面内の 3 つの点によって定義された曲線セグメントです。最初のポイントを 3 番目のポイントと同じにすることはできません。</span><span class="sxs-lookup"><span data-stu-id="aad83-104">A circular arc segment is a curved segment defined by three points in a two-dimensional plane; the first point cannot be the same as the third point.</span></span> <span data-ttu-id="aad83-105">円弧セグメントの 3 つのポイントすべてが同一線上にある場合は、円弧セグメントが直線セグメントとして扱われます。</span><span class="sxs-lookup"><span data-stu-id="aad83-105">If all three points of a circular arc segment are collinear, the arc segment is treated as a line segment.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="aad83-106">サブタイプを含め、で導入された新しい空間機能の詳細な説明と例については、 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] `CircularString` ホワイトペーパー「 [SQL Server 2012 の新しい空間機能](https://go.microsoft.com/fwlink/?LinkId=226407)」をダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="aad83-106">For a detailed description and examples of the new spatial features introduced in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], including the `CircularString` subtype, download the white paper, [New Spatial Features in SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=226407).</span></span>

## <a name="circularstring-instances"></a><span data-ttu-id="aad83-107">CircularString インスタンス</span><span class="sxs-lookup"><span data-stu-id="aad83-107">CircularString instances</span></span>
 <span data-ttu-id="aad83-108">次の図は有効な `CircularString` インスタンスを示しています。</span><span class="sxs-lookup"><span data-stu-id="aad83-108">The drawing below shows valid `CircularString` instances:</span></span>

 ![](../../database-engine/media/5ff17e34-b578-4873-9d33-79500940d0bc.png "5ff17e34-b578-4873-9d33-79500940d0bc")

### <a name="accepted-instances"></a><span data-ttu-id="aad83-109">許容されるインスタンス</span><span class="sxs-lookup"><span data-stu-id="aad83-109">Accepted instances</span></span>
 <span data-ttu-id="aad83-110">インスタンスは、空であるか、 `CircularString` または奇数 (n > 1) である場合に許容されます。</span><span class="sxs-lookup"><span data-stu-id="aad83-110">A `CircularString` instance is accepted if it is either empty or contains an odd number of points, n, where n > 1.</span></span> <span data-ttu-id="aad83-111">次の `CircularString` インスタンスが受け入れられます。</span><span class="sxs-lookup"><span data-stu-id="aad83-111">The following `CircularString` instances are accepted.</span></span>

```sql
DECLARE @g1 geometry = 'CIRCULARSTRING EMPTY';
DECLARE @g2 geometry = 'CIRCULARSTRING(1 1, 2 0, -1 1)';
DECLARE @g3 geometry = 'CIRCULARSTRING(1 1, 2 0, 2 0, 2 0, 1 1)';
```

 <span data-ttu-id="aad83-112">`@g3` の場合、`CircularString` インスタンスは許容されることがありますが、有効ではありません。</span><span class="sxs-lookup"><span data-stu-id="aad83-112">`@g3` shows that `CircularString` instance may be accepted, but not valid.</span></span> <span data-ttu-id="aad83-113">次に示す CircularString インスタンスの宣言は許容されません。</span><span class="sxs-lookup"><span data-stu-id="aad83-113">The following CircularString instance declaration is not accepted.</span></span> <span data-ttu-id="aad83-114">この宣言は `System.FormatException`をスローします。</span><span class="sxs-lookup"><span data-stu-id="aad83-114">This declaration throws a `System.FormatException`.</span></span>

```sql
DECLARE @g geometry = 'CIRCULARSTRING(1 1, 2 0, 2 0, 1 1)';
```

### <a name="valid-instances"></a><span data-ttu-id="aad83-115">有効なインスタンス</span><span class="sxs-lookup"><span data-stu-id="aad83-115">Valid instances</span></span>
 <span data-ttu-id="aad83-116">有効な `CircularString` インスタンスは、空であるか、または次の属性を持つ必要があります。</span><span class="sxs-lookup"><span data-stu-id="aad83-116">A valid `CircularString` instance must be empty or have the following attributes:</span></span>

-   <span data-ttu-id="aad83-117">少なくとも 1 つの円弧のセグメントが含まれている (つまり、最低限 3 つのポイントがある)。</span><span class="sxs-lookup"><span data-stu-id="aad83-117">It must contain at least one circular arc segment (that is, have a minimum of three points).</span></span>

-   <span data-ttu-id="aad83-118">最後のセグメントを除き、シーケンス内の各円弧セグメントの最後エンドポイントが、シーケンス内の次のセグメントの最初のエンドポイントになっている。</span><span class="sxs-lookup"><span data-stu-id="aad83-118">The last endpoint for each circular arc segment in the sequence, except for the last segment, must be the first endpoint for the next segment in the sequence.</span></span>

-   <span data-ttu-id="aad83-119">ポイントの数が奇数である。</span><span class="sxs-lookup"><span data-stu-id="aad83-119">It must have an odd number of points.</span></span>

-   <span data-ttu-id="aad83-120">このインスタンス自体を間隔に重ねることはできない。</span><span class="sxs-lookup"><span data-stu-id="aad83-120">It cannot overlap itself over an interval.</span></span>

-   <span data-ttu-id="aad83-121">`CircularString` が直線セグメントを含んでいてもかまわないが、これらの直線セグメントは、3 つ同一線上のポイントで定義する。</span><span class="sxs-lookup"><span data-stu-id="aad83-121">Although `CircularString` instances may contain line segments, these line segments must be defined by three collinear points.</span></span>

 <span data-ttu-id="aad83-122">次の例は、有効な `CircularString` インスタンスを示しています。</span><span class="sxs-lookup"><span data-stu-id="aad83-122">The following example shows valid `CircularString` instances.</span></span>

```sql
DECLARE @g1 geometry = 'CIRCULARSTRING EMPTY';
DECLARE @g2 geometry = 'CIRCULARSTRING(1 1, 2 0, -1 1)';
DECLARE @g3 geometry = 'CIRCULARSTRING(1 1, 2 0, 2 0, 1 1, 0 1)';
DECLARE @g4 geometry = 'CIRCULARSTRING(1 1, 2 2, 2 2)';
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid(),@g4.STIsValid();
```

 <span data-ttu-id="aad83-123">`CircularString` インスタンスでは、完全な円を定義するためには、少なくとも 2 つの円弧セグメントを含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="aad83-123">A `CircularString` instance must contain at least two circular arc segments to define a complete circle.</span></span> <span data-ttu-id="aad83-124">`CircularString` インスタンスでは、(1 1, 3 1, 1 1) など 1 つの円弧セグメントを使用して完全な円を定義することはできません。</span><span class="sxs-lookup"><span data-stu-id="aad83-124">A `CircularString` instance cannot use a single circular arc segment (such as (1 1, 3 1, 1 1)) to define a complete circle.</span></span> <span data-ttu-id="aad83-125">(1 1, 2 2, 3 1, 2 0, 1 1) を使用して円を定義してください。</span><span class="sxs-lookup"><span data-stu-id="aad83-125">Use (1 1, 2 2, 3 1, 2 0, 1 1) to define the circle.</span></span>

 <span data-ttu-id="aad83-126">次の例は、無効な CircularString インスタンスを示しています。</span><span class="sxs-lookup"><span data-stu-id="aad83-126">The following example shows CircularString instances that are not valid.</span></span>

```sql
DECLARE @g1 geometry = 'CIRCULARSTRING(1 1, 2 0, 1 1)';
DECLARE @g2 geometry = 'CIRCULARSTRING(0 0, 0 0, 0 0)';
SELECT @g1.STIsValid(), @g2.STIsValid();
```

### <a name="instances-with-collinear-points"></a><span data-ttu-id="aad83-127">同一線上のポイントを持つインスタンス</span><span class="sxs-lookup"><span data-stu-id="aad83-127">Instances with collinear points</span></span>
 <span data-ttu-id="aad83-128">次の場合、円弧セグメントは直線セグメントとして扱われます。</span><span class="sxs-lookup"><span data-stu-id="aad83-128">In the following cases a circular arc segment will be treated as a line segment:</span></span>

-   <span data-ttu-id="aad83-129">3 つのすべてのポイントが同一直線上にある場合 (例: (1 3, 4 4, 7 5))。</span><span class="sxs-lookup"><span data-stu-id="aad83-129">When all three points are collinear (for example, (1 3, 4 4, 7 5)).</span></span>

-   <span data-ttu-id="aad83-130">最初のポイントと中間のポイントは同一だが、3 番目のポイントが異なる場合 (例: (1 3, 1 3, 7 5))。</span><span class="sxs-lookup"><span data-stu-id="aad83-130">When the first and middle point are the same, but the third point is different (for example, (1 3, 1 3, 7 5)).</span></span>

-   <span data-ttu-id="aad83-131">中間のポイントと最後のポイントは同一だが、最初のポイントが異なる場合 (例: (1 3, 4 4, 4 4))。</span><span class="sxs-lookup"><span data-stu-id="aad83-131">When the middle and last point are the same, but the first point is different (for example, (1 3, 4 4, 4 4)).</span></span>

## <a name="examples"></a><span data-ttu-id="aad83-132">例</span><span class="sxs-lookup"><span data-stu-id="aad83-132">Examples</span></span>

### <a name="a-instantiating-a-geometry-instance-with-an-empty-circularstring"></a><span data-ttu-id="aad83-133">A.</span><span class="sxs-lookup"><span data-stu-id="aad83-133">A.</span></span> <span data-ttu-id="aad83-134">空の CircularString を使用して geometry インスタンスをインスタンス化する</span><span class="sxs-lookup"><span data-stu-id="aad83-134">Instantiating a Geometry Instance with an Empty CircularString</span></span>
 <span data-ttu-id="aad83-135">次の例は、空の `CircularString` インスタンスを作成する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="aad83-135">This example shows how to create an empty `CircularString` instance:</span></span>

```sql
DECLARE @g geometry;
SET @g = geometry::Parse('CIRCULARSTRING EMPTY');
```

### <a name="b-instantiating-a-geometry-instance-using-a-circularstring-with-one-circular-arc-segment"></a><span data-ttu-id="aad83-136">B.</span><span class="sxs-lookup"><span data-stu-id="aad83-136">B.</span></span> <span data-ttu-id="aad83-137">1 つの CircularString を含む CircularString を使用して geometry インスタンスをインスタンス化する</span><span class="sxs-lookup"><span data-stu-id="aad83-137">Instantiating a Geometry Instance Using a CircularString with One Circular Arc Segment</span></span>
 <span data-ttu-id="aad83-138">次の例は、1 つの円弧のセグメント (半円) を持つ `CircularString`インスタンスを作成する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="aad83-138">The following example shows how to create a `CircularString` instance with a single circular arc segment (half-circle):</span></span>

```sql
DECLARE @g geometry;
SET @g = geometry:: STGeomFromText('CIRCULARSTRING(2 0, 1 1, 0 0)', 0);
SELECT @g.ToString();
```

### <a name="c-instantiating-a-geometry-instance-using-a-circularstring-with-multiple-circular-arc-segments"></a><span data-ttu-id="aad83-139">C.</span><span class="sxs-lookup"><span data-stu-id="aad83-139">C.</span></span> <span data-ttu-id="aad83-140">複数の円弧セグメントを含む CircularString を使用して geometry インスタンスをインスタンス化する</span><span class="sxs-lookup"><span data-stu-id="aad83-140">Instantiating a Geometry Instance Using a CircularString with Multiple Circular Arc Segments</span></span>
 <span data-ttu-id="aad83-141">次の例は、1 つ以上の円弧のセグメント (完全な円) を持つ `CircularString` インスタンスを作成する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="aad83-141">The following example shows how to create a `CircularString` instance with more than one circular arc segment (full circle):</span></span>

```sql
DECLARE @g geometry;
SET @g = geometry::Parse('CIRCULARSTRING(2 1, 1 2, 0 1, 1 0, 2 1)');
SELECT 'Circumference = ' + CAST(@g.STLength() AS NVARCHAR(10));  
```

 <span data-ttu-id="aad83-142">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="aad83-142">This produces the following output:</span></span>

```
Circumference = 6.28319
```

 <span data-ttu-id="aad83-143">`LineString` の代わりに `CircularString` が使用される場合は出力結果を比較してください。</span><span class="sxs-lookup"><span data-stu-id="aad83-143">Compare the output when `LineString` is used instead of `CircularString`:</span></span>

```sql
DECLARE @g geometry;
SET @g = geometry::STGeomFromText('LINESTRING(2 1, 1 2, 0 1, 1 0, 2 1)', 0);
SELECT 'Perimeter = ' + CAST(@g.STLength() AS NVARCHAR(10));
```

 <span data-ttu-id="aad83-144">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="aad83-144">This produces the following output:</span></span>

```
Perimeter = 5.65685
```

 <span data-ttu-id="aad83-145">この例の値は、 `CircularString` 円の実際の円周である 2&#x03c0; (2 \* pi) に近いことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="aad83-145">Notice that the value for the `CircularString` example is close to 2&#x03c0; (2 \* pi), which is the actual circumference of the circle.</span></span>

### <a name="d-declaring-and-instantiating-a-geometry-instance-with-a-circularstring-in-the-same-statement"></a><span data-ttu-id="aad83-146">D.</span><span class="sxs-lookup"><span data-stu-id="aad83-146">D.</span></span> <span data-ttu-id="aad83-147">CircularString を同じステートメント内で使用して geometry インスタンスを宣言およびインスタンス化する</span><span class="sxs-lookup"><span data-stu-id="aad83-147">Declaring and Instantiating a Geometry Instance with a CircularString in the Same Statement</span></span>
 <span data-ttu-id="aad83-148">このコード スニペットは、`geometry` を同じステートメント内で使用して `CircularString` インスタンスを宣言およびインスタンス化する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="aad83-148">This snippet shows how to declare and instantiate a `geometry` instance with a `CircularString` in the same statement:</span></span>

```sql
DECLARE @g geometry = 'CIRCULARSTRING(0 0, 1 2.1082, 3 6.3246, 0 7, -3 6.3246, -1 2.1082, 0 0)';
```

### <a name="e-instantiating-a-geography-instance-with-a-circularstring"></a><span data-ttu-id="aad83-149">E.</span><span class="sxs-lookup"><span data-stu-id="aad83-149">E.</span></span> <span data-ttu-id="aad83-150">CircularString を使用して geometry インスタンスをインスタンス化する</span><span class="sxs-lookup"><span data-stu-id="aad83-150">Instantiating a Geography Instance with a CircularString</span></span>
 <span data-ttu-id="aad83-151">次の例は、`geography` を使用して `CircularString` インスタンスを宣言およびインスタンス化する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="aad83-151">The following example shows how to declare and instantiate a `geography` instance with a `CircularString`:</span></span>

```sql
DECLARE @g geography = 'CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)';
```

### <a name="f-instantiating-a-geometry-instance-with-a-circularstring-that-is-a-straight-line"></a><span data-ttu-id="aad83-152">F.</span><span class="sxs-lookup"><span data-stu-id="aad83-152">F.</span></span> <span data-ttu-id="aad83-153">直線の CircularString を使用して geometry インスタンスをインスタンス化する</span><span class="sxs-lookup"><span data-stu-id="aad83-153">Instantiating a Geometry Instance with a CircularString that is a Straight Line</span></span>
 <span data-ttu-id="aad83-154">次の例は、直線の `CircularString` インスタンスを作成する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="aad83-154">The following example shows how to create a `CircularString` instance that is a straight line:</span></span>

```sql
DECLARE @g geometry;
SET @g = geometry::STGeomFromText('CIRCULARSTRING(0 0, 1 2, 2 4)', 0);
```

## <a name="see-also"></a><span data-ttu-id="aad83-155">参照</span><span class="sxs-lookup"><span data-stu-id="aad83-155">See Also</span></span>
 <span data-ttu-id="aad83-156">[空間データ型の概要](spatial-data-types-overview.md) [CompoundCurve](compoundcurve.md) [makevalid &#40;geography データ型&#41;](/sql/t-sql/spatial-geography/makevalid-geography-data-type) [makevalid &#40;geometry データ型&#41;](/sql/t-sql/spatial-geometry/makevalid-geometry-data-type) [stisvalid &#40;geometry データ型&#41;](/sql/t-sql/spatial-geometry/stisvalid-geometry-data-type) [Stisvalid &#40;geography データ](/sql/t-sql/spatial-geography/stisvalid-geography-data-type)型&#41;[stisvalid &#40;geometry データ型&#41;](/sql/t-sql/spatial-geometry/stlength-geometry-data-type) [STStartPoint &#40;geometry データ型&#41;](/sql/t-sql/spatial-geometry/ststartpoint-geometry-data-type) [stisvalid &#40;geometry データ型&#41;](/sql/t-sql/spatial-geometry/stendpoint-geometry-data-type) [stpointn &#40;geometry データ型&#41;](/sql/t-sql/spatial-geometry/stpointn-geometry-data-type) [stnumpoints](/sql/t-sql/spatial-geometry/stnumpoints-geometry-data-type) &#40;geometry データ型&#41;stisring &#40;geometry データ型&#41;[STIsRing &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stisring-geometry-data-type) [stisclosed](/sql/t-sql/spatial-geometry/stisclosed-geometry-data-type) &#40;geometry データ型&#41;[stpointonsurface &#40;geometry](/sql/t-sql/spatial-geometry/stpointonsurface-geometry-data-type)データ型&#41;[LineString](linestring.md)</span><span class="sxs-lookup"><span data-stu-id="aad83-156">[Spatial Data Types Overview](spatial-data-types-overview.md) [CompoundCurve](compoundcurve.md) [MakeValid &#40;geography Data Type&#41;](/sql/t-sql/spatial-geography/makevalid-geography-data-type) [MakeValid &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/makevalid-geometry-data-type) [STIsValid &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stisvalid-geometry-data-type) [STIsValid &#40;geography Data Type&#41;](/sql/t-sql/spatial-geography/stisvalid-geography-data-type) [STLength &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stlength-geometry-data-type) [STStartPoint &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/ststartpoint-geometry-data-type) [STEndpoint &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stendpoint-geometry-data-type) [STPointN &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stpointn-geometry-data-type) [STNumPoints &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stnumpoints-geometry-data-type) [STIsRing &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stisring-geometry-data-type) [STIsClosed &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stisclosed-geometry-data-type) [STPointOnSurface &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stpointonsurface-geometry-data-type) [LineString](linestring.md)</span></span>


