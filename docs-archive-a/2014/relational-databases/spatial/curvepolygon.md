---
title: CurvePolygon | Microsoft Docs
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: e000a1d8-a049-4542-bfeb-943fd6ab3969
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: b90fdbd9a0bc80dfc6a82416d0193b2951fe13ef
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632314"
---
# <a name="curvepolygon"></a><span data-ttu-id="0bc25-102">CurvePolygon</span><span class="sxs-lookup"><span data-stu-id="0bc25-102">CurvePolygon</span></span>
  <span data-ttu-id="0bc25-103">は、 `CurvePolygon` 外部境界リングおよび0個以上の内部リングによって定義された位相的閉じサーフェイスです。</span><span class="sxs-lookup"><span data-stu-id="0bc25-103">A `CurvePolygon` is a topologically closed surface defined by an exterior bounding ring and zero or more interior rings</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="0bc25-104">サブタイプを含め、で導入された空間機能の詳細な説明と例については、 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] `CurvePolygon` ホワイトペーパー「 [SQL Server 2012 の新しい空間機能](https://go.microsoft.com/fwlink/?LinkId=226407)」をダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="0bc25-104">For a detailed description and examples of spatial features introduced in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], including the `CurvePolygon` subtype, download the white paper, [New Spatial Features in SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=226407).</span></span>  
  
 <span data-ttu-id="0bc25-105">次の条件では、インスタンスの属性を定義し `CurvePolygon` ます。</span><span class="sxs-lookup"><span data-stu-id="0bc25-105">The following criteria define attributes of a `CurvePolygon` instance:</span></span>  
  
-   <span data-ttu-id="0bc25-106">`CurvePolygon` インスタンスの境界は、外部リングとすべての内部リングによって定義されます。</span><span class="sxs-lookup"><span data-stu-id="0bc25-106">The boundary of the `CurvePolygon` instance is defined by the exterior ring and all interior rings.</span></span>  
  
-   <span data-ttu-id="0bc25-107">`CurvePolygon` インスタンスの内部は、外部リングとすべての内部リングとの間にある空間です。</span><span class="sxs-lookup"><span data-stu-id="0bc25-107">The interior of the `CurvePolygon` instance is the space between the exterior ring and all of the interior rings.</span></span>  
  
 <span data-ttu-id="0bc25-108">`CurvePolygon` インスタンスが `Polygon` インスタンスと異なるのは、`CurvePolygon` インスタンスは円弧 (`CircularString` および `CompoundCurve`) を含む場合があるという点です。</span><span class="sxs-lookup"><span data-stu-id="0bc25-108">A `CurvePolygon` instance differs from a `Polygon` instance in that a `CurvePolygon` instance may contain the following circular arc segments: `CircularString` and `CompoundCurve`.</span></span>  
  
## <a name="compoundcurve-instances"></a><span data-ttu-id="0bc25-109">CompoundCurve インスタンス</span><span class="sxs-lookup"><span data-stu-id="0bc25-109">CompoundCurve instances</span></span>  
 <span data-ttu-id="0bc25-110">有効な `CurvePolygon` の図を次に示します。</span><span class="sxs-lookup"><span data-stu-id="0bc25-110">Illustration below shows valid `CurvePolygon` figures:</span></span>  
  
### <a name="accepted-instances"></a><span data-ttu-id="0bc25-111">許容されるインスタンス</span><span class="sxs-lookup"><span data-stu-id="0bc25-111">Accepted instances</span></span>  
 <span data-ttu-id="0bc25-112">`CurvePolygon` インスタンスが許容されるためには、空であるか、または許容される円弧リングのみを含んでいる必要があります。</span><span class="sxs-lookup"><span data-stu-id="0bc25-112">For a `CurvePolygon` instance to be accepted, it needs to be either empty or contain only circular arc rings that are accepted.</span></span> <span data-ttu-id="0bc25-113">許容される円弧リングは、次の要件を満たしています。</span><span class="sxs-lookup"><span data-stu-id="0bc25-113">An accepted circular arc ring meets the following requirements.</span></span>  
  
1.  <span data-ttu-id="0bc25-114">許容される `LineString` インスタンス、`CircularString` インスタンス、または `CompoundCurve` インスタンスであること。</span><span class="sxs-lookup"><span data-stu-id="0bc25-114">Is an accepted `LineString`, `CircularString`, or `CompoundCurve` instance.</span></span> <span data-ttu-id="0bc25-115">許容されるインスタンスの詳細については、「 [LineString](linestring.md)」、「 [CircularString](circularstring.md)」、および「 [CompoundCurve](compoundcurve.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0bc25-115">For more information on accepted instances, see [LineString](linestring.md), [CircularString](circularstring.md), and [CompoundCurve](compoundcurve.md).</span></span>  
  
2.  <span data-ttu-id="0bc25-116">4 つ以上の点があること。</span><span class="sxs-lookup"><span data-stu-id="0bc25-116">Has at least four points.</span></span>  
  
3.  <span data-ttu-id="0bc25-117">始点および終点の X 座標と Y 座標が同じであること。</span><span class="sxs-lookup"><span data-stu-id="0bc25-117">The start and end point have the same X and Y coordinates.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="0bc25-118">Z 値および M 値は無視されます。</span><span class="sxs-lookup"><span data-stu-id="0bc25-118">Z and M values are ignored.</span></span>  
  
 <span data-ttu-id="0bc25-119">次の例は、許容される `CurvePolygon` インスタンスを示しています。</span><span class="sxs-lookup"><span data-stu-id="0bc25-119">The following example shows accepted `CurvePolygon` instances.</span></span>  
  
```  
DECLARE @g1 geometry = 'CURVEPOLYGON EMPTY';  
DECLARE @g2 geometry = 'CURVEPOLYGON((0 0, 0 0, 0 0, 0 0))';  
DECLARE @g3 geometry = 'CURVEPOLYGON((0 0 1, 0 0 2, 0 0 3, 0 0 3))'  
DECLARE @g4 geometry = 'CURVEPOLYGON(CIRCULARSTRING(1 3, 3 5, 4 7, 7 3, 1 3))';  
DECLARE @g5 geography = 'CURVEPOLYGON((-122.3 47, 122.3 -47, 125.7 -49, 121 -38, -122.3 47))';  
```  
  
 <span data-ttu-id="0bc25-120">`@g3` 始点と終点の Z 値が異なりますが Z 値は無視されるため、許容されます。</span><span class="sxs-lookup"><span data-stu-id="0bc25-120">`@g3` is accepted even though the start and end points have different Z values because Z values are ignored.</span></span> <span data-ttu-id="0bc25-121">`@g5` は、`geography` 型インスタンスは無効ですが、許容されます。</span><span class="sxs-lookup"><span data-stu-id="0bc25-121">`@g5` is accepted even though the `geography` type instance is not valid.</span></span>  
  
 <span data-ttu-id="0bc25-122">次の例では、 `System.FormatException`がスローされます。</span><span class="sxs-lookup"><span data-stu-id="0bc25-122">The following examples throw `System.FormatException`.</span></span>  
  
```  
DECLARE @g1 geometry = 'CURVEPOLYGON((0 5, 0 0, 0 0, 0 0))';  
DECLARE @g2 geometry = 'CURVEPOLYGON((0 0, 0 0, 0 0))';  
```  
  
 <span data-ttu-id="0bc25-123">`@g1` 始点と終点の Y 値が同じでないため、許容されません。</span><span class="sxs-lookup"><span data-stu-id="0bc25-123">`@g1` is not accepted because the start and end points do not have the same Y value.</span></span> <span data-ttu-id="0bc25-124">`@g2` リングに十分な数の点が含まれていないため、許容されません。</span><span class="sxs-lookup"><span data-stu-id="0bc25-124">`@g2` is not accepted because the ring does not have enough points.</span></span>  
  
### <a name="valid-instances"></a><span data-ttu-id="0bc25-125">有効なインスタンス</span><span class="sxs-lookup"><span data-stu-id="0bc25-125">Valid instances</span></span>  
 <span data-ttu-id="0bc25-126">`CurvePolygon` インスタンスを有効にするためには、外部リングと内部リングの両方が次の条件を満たす必要があります。</span><span class="sxs-lookup"><span data-stu-id="0bc25-126">For a `CurvePolygon` instance to be valid both exterior and interior rings must meet the following criteria:</span></span>  
  
1.  <span data-ttu-id="0bc25-127">1 つの接点でのみ接していること。</span><span class="sxs-lookup"><span data-stu-id="0bc25-127">They may only touch at single tangent points.</span></span>  
  
2.  <span data-ttu-id="0bc25-128">互いに交差していないこと。</span><span class="sxs-lookup"><span data-stu-id="0bc25-128">They cannot cross each other.</span></span>  
  
3.  <span data-ttu-id="0bc25-129">それぞれのリングに 4 つ以上の点が含まれていること。</span><span class="sxs-lookup"><span data-stu-id="0bc25-129">Each ring must contain at least four points.</span></span>  
  
4.  <span data-ttu-id="0bc25-130">それぞれのリングは許容される curve 型であること。</span><span class="sxs-lookup"><span data-stu-id="0bc25-130">Each ring must be an acceptable curve type.</span></span>  
  
 <span data-ttu-id="0bc25-131">さらに、`CurvePolygon` インスタンスは、`geometry` データ型であるかまたは `geography` データ型であるかに応じて、特定の条件を満たす必要があります。</span><span class="sxs-lookup"><span data-stu-id="0bc25-131">`CurvePolygon` instances also need to meet specific criteria depending on whether they are `geometry` or `geography` data types.</span></span>  
  
#### <a name="geometry-data-type"></a><span data-ttu-id="0bc25-132">geometry データ型</span><span class="sxs-lookup"><span data-stu-id="0bc25-132">Geometry data type</span></span>  
 <span data-ttu-id="0bc25-133">有効な **geometryCurvePolygon** インスタンスは、次の属性を持つ必要があります。</span><span class="sxs-lookup"><span data-stu-id="0bc25-133">A valid **geometryCurvePolygon** instance must have the following attributes:</span></span>  
  
1.  <span data-ttu-id="0bc25-134">すべての内部リングが外部リング内に含まれていること。</span><span class="sxs-lookup"><span data-stu-id="0bc25-134">All the interior rings must be contained within the exterior ring.</span></span>  
  
2.  <span data-ttu-id="0bc25-135">複数の内部リングを含むことはできますが、内部リング内に別の内部リングを含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="0bc25-135">May have multiple interior rings, but an interior ring cannot contain another interior ring.</span></span>  
  
3.  <span data-ttu-id="0bc25-136">リングがそれ自体または別のリングと交差していないこと。</span><span class="sxs-lookup"><span data-stu-id="0bc25-136">No ring can cross itself or another ring.</span></span>  
  
4.  <span data-ttu-id="0bc25-137">リングどうしは、1 つの接点でのみ接することができます (リングが接する点の数は有限であることが必要です)。</span><span class="sxs-lookup"><span data-stu-id="0bc25-137">Rings can only touch at single tangent points (number of points where rings touch must be finite).</span></span>  
  
5.  <span data-ttu-id="0bc25-138">多角形の内部が接続されていること。</span><span class="sxs-lookup"><span data-stu-id="0bc25-138">The interior of the polygon must be connected.</span></span>  
  
 <span data-ttu-id="0bc25-139">次の例は、有効な **geometryCurvePolygon** インスタンスを示しています。</span><span class="sxs-lookup"><span data-stu-id="0bc25-139">The following example shows valid **geometryCurvePolygon** instances.</span></span>  
  
```  
DECLARE @g1 geometry = 'CURVEPOLYGON EMPTY';  
DECLARE @g2 geometry = 'CURVEPOLYGON(CIRCULARSTRING(1 3, 3 5, 4 7, 7 3, 1 3))';  
SELECT @g1.STIsValid(), @g2.STIsValid();  
```  
  
 <span data-ttu-id="0bc25-140">CurvePolygon インスタンスには Polygon インスタンスと同じ妥当性規則が適用されますが、例外として、CurvePolygon インスタンスでは新しい円弧型が許容されます。</span><span class="sxs-lookup"><span data-stu-id="0bc25-140">CurvePolygon instances have the same validity rules as Polygon instances with the exception that CurvePolygon instances may accept the new circular arc segment types.</span></span> <span data-ttu-id="0bc25-141">他の有効または無効なインスタンスの例については、「 [Polygon](polygon.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0bc25-141">For more examples of instances that are valid or not valid, see [Polygon](polygon.md).</span></span>  
  
#### <a name="geography-data-type"></a><span data-ttu-id="0bc25-142">geography データ型</span><span class="sxs-lookup"><span data-stu-id="0bc25-142">Geography data type</span></span>  
 <span data-ttu-id="0bc25-143">有効な **geographyCurvePolygon** インスタンスは、次の属性を持つ必要があります。</span><span class="sxs-lookup"><span data-stu-id="0bc25-143">A valid **geographyCurvePolygon** instance must have the following attributes:</span></span>  
  
1.  <span data-ttu-id="0bc25-144">多角形の内部が左辺ルールを使用して接続されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="0bc25-144">The interior of the polygon is connected using the left-hand rule.</span></span>  
  
2.  <span data-ttu-id="0bc25-145">リングがそれ自体または別のリングと交差していないこと。</span><span class="sxs-lookup"><span data-stu-id="0bc25-145">No ring can cross itself or another ring.</span></span>  
  
3.  <span data-ttu-id="0bc25-146">リングどうしは、1 つの接点でのみ接することができます (リングが接する点の数は有限であることが必要です)。</span><span class="sxs-lookup"><span data-stu-id="0bc25-146">Rings can only touch at single tangent points (number of points where rings touch must be finite).</span></span>  
  
4.  <span data-ttu-id="0bc25-147">多角形の内部が接続されていること。</span><span class="sxs-lookup"><span data-stu-id="0bc25-147">The interior of the polygon must be connected.</span></span>  
  
 <span data-ttu-id="0bc25-148">次の例は、有効な geography CurvePolygon インスタンスを示しています。</span><span class="sxs-lookup"><span data-stu-id="0bc25-148">The following example shows a valid geography CurvePolygon instance.</span></span>  
  
```  
DECLARE @g geography = 'CURVEPOLYGON((-122.3 47, 122.3 47, 125.7 49, 121 38, -122.3 47))';  
SELECT @g.STIsValid();  
```  
  
## <a name="examples"></a><span data-ttu-id="0bc25-149">例</span><span class="sxs-lookup"><span data-stu-id="0bc25-149">Examples</span></span>  
  
### <a name="a-instantiating-a-geometry-instance-with-an-empty-curvepolygon"></a><span data-ttu-id="0bc25-150">A.</span><span class="sxs-lookup"><span data-stu-id="0bc25-150">A.</span></span> <span data-ttu-id="0bc25-151">空の CurvePolygon を使用して geometry インスタンスをインスタンス化する</span><span class="sxs-lookup"><span data-stu-id="0bc25-151">Instantiating a Geometry Instance with an Empty CurvePolygon</span></span>  
 <span data-ttu-id="0bc25-152">次の例は、空の `CurvePolygon` インスタンスを作成する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="0bc25-152">This example shows how to create an empty `CurvePolygon` instance:</span></span>  
  
```sql  
DECLARE @g geometry;  
SET @g = geometry::Parse('CURVEPOLYGON EMPTY');  
```  
  
### <a name="b-declaring-and-instantiating-a-geometry-instance-with-a-curvepolygon-in-the-same-statement"></a><span data-ttu-id="0bc25-153">B.</span><span class="sxs-lookup"><span data-stu-id="0bc25-153">B.</span></span> <span data-ttu-id="0bc25-154">CurvePolygon を同じステートメント内で使用して geometry インスタンスを宣言およびインスタンス化する</span><span class="sxs-lookup"><span data-stu-id="0bc25-154">Declaring and Instantiating a Geometry Instance with a CurvePolygon in the Same Statement</span></span>  
 <span data-ttu-id="0bc25-155">このコード スニペットは、`CurvePolygon` を同じステートメント内で使用して geometry インスタンスを宣言およびインスタンス化する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="0bc25-155">This code snippet shows how to declare and initialize a geometry instance with a `CurvePolygon` in the same statement:</span></span>  
  
```sql  
DECLARE @g geometry = 'CURVEPOLYGON(CIRCULARSTRING(2 4, 4 2, 6 4, 4 6, 2 4))'  
```  
  
### <a name="c-instantiating-a-geography-instance-with-a-curvepolygon"></a><span data-ttu-id="0bc25-156">C.</span><span class="sxs-lookup"><span data-stu-id="0bc25-156">C.</span></span> <span data-ttu-id="0bc25-157">CurvePolygon を使用して geography インスタンスをインスタンス化する</span><span class="sxs-lookup"><span data-stu-id="0bc25-157">Instantiating a Geography Instance with a CurvePolygon</span></span>  
 <span data-ttu-id="0bc25-158">このコード スニペットは、`geography` を使用して `CurvePolygon` インスタンスを宣言およびインスタンス化する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="0bc25-158">This code snippet shows how to declare and initialize a `geography` instance with a `CurvePolygon`:</span></span>  
  
```sql  
DECLARE @g geography = 'CURVEPOLYGON(CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))';  
```  
  
### <a name="d-storing-a-curvepolygon-with-only-an-exterior-bounding-ring"></a><span data-ttu-id="0bc25-159">D.</span><span class="sxs-lookup"><span data-stu-id="0bc25-159">D.</span></span> <span data-ttu-id="0bc25-160">外部境界リングのみを含む CurvePolygon を格納する</span><span class="sxs-lookup"><span data-stu-id="0bc25-160">Storing a CurvePolygon with Only an Exterior Bounding Ring</span></span>  
 <span data-ttu-id="0bc25-161">この例は、単純な円を `CurvePolygon` インスタンスに格納する方法を示しています (外部境界リングのみを使用して円が定義されています)。</span><span class="sxs-lookup"><span data-stu-id="0bc25-161">This example shows how to store a simple circle in a `CurvePolygon` instance (only an exterior bounding ring is used to define the circle):</span></span>  
  
```sql  
DECLARE @g geometry;  
SET @g = geometry::Parse('CURVEPOLYGON(CIRCULARSTRING(2 4, 4 2, 6 4, 4 6, 2 4))');  
SELECT @g.STArea() AS Area;  
```  
  
### <a name="e-storing-a-curvepolygon-containing-interior-rings"></a><span data-ttu-id="0bc25-162">E.</span><span class="sxs-lookup"><span data-stu-id="0bc25-162">E.</span></span> <span data-ttu-id="0bc25-163">内部リングを含む CurvePolygon を格納する</span><span class="sxs-lookup"><span data-stu-id="0bc25-163">Storing a CurvePolygon Containing Interior Rings</span></span>  
 <span data-ttu-id="0bc25-164">この例では、`CurvePolygon` インスタンス内にドーナツを作成しています (ドーナツは外部境界リングと内部リングの両方を使用して定義されています)。</span><span class="sxs-lookup"><span data-stu-id="0bc25-164">This example creates a donut in a `CurvePolygon` instance (both an exterior bounding ring and an interior ring is used to define the donut):</span></span>  
  
```sql  
DECLARE @g geometry;  
SET @g = geometry::Parse('CURVEPOLYGON(CIRCULARSTRING(0 4, 4 0, 8 4, 4 8, 0 4), CIRCULARSTRING(2 4, 4 2, 6 4, 4 6, 2 4))');  
SELECT @g.STArea() AS Area;  
```  
  
 <span data-ttu-id="0bc25-165">次の例は、内部リングを使用した場合の有効な `CurvePolygon` インスタンスと無効なインスタンスの両方を示しています。</span><span class="sxs-lookup"><span data-stu-id="0bc25-165">This example shows both a valid `CurvePolygon` instance and an invalid instance when using interior rings:</span></span>  
  
```sql  
DECLARE @g1 geometry, @g2 geometry;  
SET @g1 = geometry::Parse('CURVEPOLYGON(CIRCULARSTRING(0 5, 5 0, 0 -5, -5 0, 0 5), (-2 2, 2 2, 2 -2, -2 -2, -2 2))');  
IF @g1.STIsValid() = 1  
  BEGIN  
     SELECT @g1.STArea();  
  END  
SET @g2 = geometry::Parse('CURVEPOLYGON(CIRCULARSTRING(0 5, 5 0, 0 -5, -5 0, 0 5), (0 5, 5 0, 0 -5, -5 0, 0 5))');  
IF @g2.STIsValid() = 1  
  BEGIN  
     SELECT @g2.STArea();  
  END  
SELECT @g1.STIsValid() AS G1, @g2.STIsValid() AS G2;  
```  
  
 <span data-ttu-id="0bc25-166">@g1 と @g2 はどちらも同じ外部境界リング (半径 5 の円) を使用し、内部リングに正方形を使用しています。</span><span class="sxs-lookup"><span data-stu-id="0bc25-166">Both @g1 and @g2 use the same exterior bounding ring: a circle with a radius of 5 and they both use a square for an interior ring.</span></span>  <span data-ttu-id="0bc25-167">しかし、インスタンス @g1 は有効ですが、インスタンス @g2 は無効です。</span><span class="sxs-lookup"><span data-stu-id="0bc25-167">However, the instance @g1 is valid, but the instance @g2 is invalid.</span></span>  <span data-ttu-id="0bc25-168">@g2 が無効な理由は、外部リングによって範囲指定された内部空間が内部リングによって 4 つの別個の領域に分割されているためです。</span><span class="sxs-lookup"><span data-stu-id="0bc25-168">The reason that @g2 is invalid is that the interior ring splits the interior space bounded by the exterior ring into four separate regions.</span></span>  <span data-ttu-id="0bc25-169">この状況を次の図に示します。</span><span class="sxs-lookup"><span data-stu-id="0bc25-169">The following drawing shows what occurred:</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bc25-170">参照</span><span class="sxs-lookup"><span data-stu-id="0bc25-170">See Also</span></span>  
 <span data-ttu-id="0bc25-171">[Polygon](polygon.md) </span><span class="sxs-lookup"><span data-stu-id="0bc25-171">[Polygon](polygon.md) </span></span>  
 <span data-ttu-id="0bc25-172">[CircularString](circularstring.md) </span><span class="sxs-lookup"><span data-stu-id="0bc25-172">[CircularString](circularstring.md) </span></span>  
 <span data-ttu-id="0bc25-173">[CompoundCurve](compoundcurve.md) </span><span class="sxs-lookup"><span data-stu-id="0bc25-173">[CompoundCurve](compoundcurve.md) </span></span>  
 <span data-ttu-id="0bc25-174">[geometry データ型メソッド リファレンス](/sql/t-sql/spatial-geometry/spatial-types-geometry-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0bc25-174">[geometry Data Type Method Reference](/sql/t-sql/spatial-geometry/spatial-types-geometry-transact-sql) </span></span>  
 <span data-ttu-id="0bc25-175">[geography データ型メソッド リファレンス](/sql/t-sql/spatial-geography/spatial-types-geography) </span><span class="sxs-lookup"><span data-stu-id="0bc25-175">[geography Data Type Method Reference](/sql/t-sql/spatial-geography/spatial-types-geography) </span></span>  
 [<span data-ttu-id="0bc25-176">空間データ型の概要</span><span class="sxs-lookup"><span data-stu-id="0bc25-176">Spatial Data Types Overview</span></span>](spatial-data-types-overview.md)  
  
  
