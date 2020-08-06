---
title: 空間データ型の概要 | Microsoft Docs
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- geometry data type [SQL Server], understanding
- geography data type [SQL Server], spatial data
- planar spatial data [SQL Server], geometry data type
- spatial data types [SQL Server]
ms.assetid: 1615db50-69de-4778-8be6-4e058c00ccd4
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: c0548d974e83bfe2b1e103d4458b17078fba8014
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719760"
---
# <a name="spatial-data-types-overview"></a><span data-ttu-id="23ba9-102">空間データ型の概要</span><span class="sxs-lookup"><span data-stu-id="23ba9-102">Spatial Data Types Overview</span></span>
  <span data-ttu-id="23ba9-103">空間データには 2 つの型があります。</span><span class="sxs-lookup"><span data-stu-id="23ba9-103">There are two types of spatial data.</span></span> <span data-ttu-id="23ba9-104">`geometry` データ型は平面 (ユークリッド (平面地球)) データをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="23ba9-104">The `geometry` data type supports planar, or Euclidean (flat-earth), data.</span></span> <span data-ttu-id="23ba9-105">`geometry` データ型 (平面) は、Open Geospatial Consortium (OGC) Simple Features for SQL Specification version 1.1.0 および SQL MM (ISO 標準) の両方に準拠しています。</span><span class="sxs-lookup"><span data-stu-id="23ba9-105">The `geometry` data type both conforms to the Open Geospatial Consortium (OGC) Simple Features for SQL Specification version 1.1.0 and is compliant with SQL MM (ISO standard).</span></span>

 <span data-ttu-id="23ba9-106">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ではそのほかに、`geography` データ型もサポートされています。このデータ型は、GPS の緯度経度座標などの楕円体 (球体地球) データを格納します。</span><span class="sxs-lookup"><span data-stu-id="23ba9-106">In addition, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] supports the `geography` data type, which stores ellipsoidal (round-earth) data, such as GPS latitude and longitude coordinates.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="23ba9-107">空間データ型の機能強化を含め、 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]に導入された空間機能の詳細な説明とサンプルについては、ホワイト ペーパー「 [SQL Server コードネーム "Denali" の新しい空間機能](https://go.microsoft.com/fwlink/?LinkId=226407)」をダウンロードして参照してください。</span><span class="sxs-lookup"><span data-stu-id="23ba9-107">For a detailed description and examples of spatial features introduced in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], including enhancements to the spatial data types, download the white paper, [New Spatial Features in SQL Server Code-Named "Denali"](https://go.microsoft.com/fwlink/?LinkId=226407).</span></span>

##  <a name="spatial-data-objects"></a><a name="objects"></a> <span data-ttu-id="23ba9-108">空間データ オブジェクト</span><span class="sxs-lookup"><span data-stu-id="23ba9-108">Spatial Data Objects</span></span>
 <span data-ttu-id="23ba9-109">`geometry` データ型と `geography` データ型は、16 の空間データ オブジェクト (インスタンス型) をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="23ba9-109">The `geometry` and `geography` data types support sixteen spatial data objects, or instance types.</span></span> <span data-ttu-id="23ba9-110">ただし、 *インスタンス化可能*なインスタンス型、つまりデータベース内でインスタンスを作成して使用することができる (インスタンス化できる) インスタンス型は、そのうちの 11 種類のみです。</span><span class="sxs-lookup"><span data-stu-id="23ba9-110">However, only eleven of these instance types are *instantiable*; you can create and work with these instances (or instantiate them) in a database.</span></span> <span data-ttu-id="23ba9-111">これらのインスタンスは、親データ型から `Points` 、 **linestrings、circularstring**、、 `CompoundCurves` `Polygons` 、、またはの複数のインスタンスとして区別される特定のプロパティを派生 `CurvePolygons` `geometry` `geography` `GeometryCollection` します。</span><span class="sxs-lookup"><span data-stu-id="23ba9-111">These instances derive certain properties from their parent data types that distinguish them as `Points`, **LineStrings, CircularStrings**, `CompoundCurves`, `Polygons`, `CurvePolygons` or as multiple `geometry` or `geography` instances in a `GeometryCollection`.</span></span> <span data-ttu-id="23ba9-112">`Geography` 型には、`FullGlobe` という追加のインスタンス型があります。</span><span class="sxs-lookup"><span data-stu-id="23ba9-112">`Geography` type has an additional instance type, `FullGlobe`.</span></span>

 <span data-ttu-id="23ba9-113">次の図は、`geometry` の階層を表しています。`geometry` データ型と `geography` データ型はこの階層に基づいています。</span><span class="sxs-lookup"><span data-stu-id="23ba9-113">The figure below depicts the `geometry` hierarchy upon which the `geometry` and `geography` data types are based.</span></span> <span data-ttu-id="23ba9-114">とのインスタンス化 `geometry` 可能 `geography` な型は、blue で示されています。</span><span class="sxs-lookup"><span data-stu-id="23ba9-114">The instantiable types of `geometry` and `geography` are indicated in blue.</span></span>

 <span data-ttu-id="23ba9-115">![geometry 型の階層](../../database-engine/media/geom-hierarchy.gif "geometry 型の階層")</span><span class="sxs-lookup"><span data-stu-id="23ba9-115">![Hierarchy of the geometry type](../../database-engine/media/geom-hierarchy.gif "Hierarchy of the geometry type")</span></span>

 <span data-ttu-id="23ba9-116">図が示すように、およびデータ型のインスタンス化可能な型は、、、、、、、、、 `geometry` `geography` `Point` `MultiPoint` `LineString` `CircularString` `MultiLineString` `CompoundCurve` `Polygon` `CurvePolygon` `MultiPolygon` および `GeometryCollection` です。</span><span class="sxs-lookup"><span data-stu-id="23ba9-116">As the figure indicates, the ten instantiable types of the `geometry` and `geography` data types are `Point`, `MultiPoint`, `LineString`, `CircularString`, `MultiLineString`, `CompoundCurve`, `Polygon`, `CurvePolygon`, `MultiPolygon`, and `GeometryCollection`.</span></span> <span data-ttu-id="23ba9-117">geography データ型には、もう 1 つ `FullGlobe` というインスタンス化可能な型があります。</span><span class="sxs-lookup"><span data-stu-id="23ba9-117">There is one additional instantiable type for the geography data type: `FullGlobe`.</span></span> <span data-ttu-id="23ba9-118">`geometry`型および `geography` 型は、インスタンスが明示的に定義されていない場合でも、適切な形式のインスタンスである限り、特定のインスタンスを認識できます。</span><span class="sxs-lookup"><span data-stu-id="23ba9-118">The `geometry` and `geography` types can recognize a specific instance as long as it is a well-formed instance, even if the instance is not defined explicitly.</span></span> <span data-ttu-id="23ba9-119">たとえば、 `Point` STPointFromText () メソッドを使用してインスタンスを明示的に定義し、 `geometry` `geography` メソッドの入力が適切な形式である限り、インスタンスをとして認識し `Point` ます。</span><span class="sxs-lookup"><span data-stu-id="23ba9-119">For example, if you define a `Point` instance explicitly using the STPointFromText() method, `geometry` and `geography` recognize the instance as a `Point`, as long as the method input is well-formed.</span></span> <span data-ttu-id="23ba9-120">`STGeomFromText()` メソッドを使用して同じインスタンスを定義した場合は、`geometry` データ型と `geography` データ型の両方で `Point` として認識されます。</span><span class="sxs-lookup"><span data-stu-id="23ba9-120">If you define the same instance using the `STGeomFromText()` method, both the `geometry` and `geography` data types recognize the instance as a `Point`.</span></span>

 <span data-ttu-id="23ba9-121">geometry 型および geography 型のサブタイプには、単純型とコレクション型があります。</span><span class="sxs-lookup"><span data-stu-id="23ba9-121">The subtypes for geometry and geography types are divided into simple and collection types.</span></span>  <span data-ttu-id="23ba9-122">`STNumCurves()` などのメソッドは、単純型でのみ機能します。</span><span class="sxs-lookup"><span data-stu-id="23ba9-122">Some methods like `STNumCurves()` work only with simple types.</span></span>

 <span data-ttu-id="23ba9-123">単純型は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="23ba9-123">Simple types include:</span></span>

-   [<span data-ttu-id="23ba9-124">Point</span><span class="sxs-lookup"><span data-stu-id="23ba9-124">Point</span></span>](../spatial/point.md)

-   [<span data-ttu-id="23ba9-125">LineString</span><span class="sxs-lookup"><span data-stu-id="23ba9-125">LineString</span></span>](../spatial/linestring.md)

-   [<span data-ttu-id="23ba9-126">CircularString</span><span class="sxs-lookup"><span data-stu-id="23ba9-126">CircularString</span></span>](../spatial/circularstring.md)

-   [<span data-ttu-id="23ba9-127">CompoundCurve</span><span class="sxs-lookup"><span data-stu-id="23ba9-127">CompoundCurve</span></span>](../spatial/compoundcurve.md)

-   [<span data-ttu-id="23ba9-128">Polygon</span><span class="sxs-lookup"><span data-stu-id="23ba9-128">Polygon</span></span>](../spatial/polygon.md)

-   [<span data-ttu-id="23ba9-129">CurvePolygon</span><span class="sxs-lookup"><span data-stu-id="23ba9-129">CurvePolygon</span></span>](../spatial/curvepolygon.md)

 <span data-ttu-id="23ba9-130">コレクション型は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="23ba9-130">Collection types include:</span></span>

-   [<span data-ttu-id="23ba9-131">MultiPoint</span><span class="sxs-lookup"><span data-stu-id="23ba9-131">MultiPoint</span></span>](../spatial/multipoint.md)

-   [<span data-ttu-id="23ba9-132">MultiLineString</span><span class="sxs-lookup"><span data-stu-id="23ba9-132">MultiLineString</span></span>](../spatial/multilinestring.md)

-   [<span data-ttu-id="23ba9-133">MultiPolygon</span><span class="sxs-lookup"><span data-stu-id="23ba9-133">MultiPolygon</span></span>](../spatial/multipolygon.md)

-   [<span data-ttu-id="23ba9-134">GeometryCollection</span><span class="sxs-lookup"><span data-stu-id="23ba9-134">GeometryCollection</span></span>](../spatial/geometrycollection.md)


##  <a name="differences-between-the-geometry-and-geography-data-types"></a><a name="differences"></a> <span data-ttu-id="23ba9-135">geometry データ型と geography データ型の違い</span><span class="sxs-lookup"><span data-stu-id="23ba9-135">Differences Between the geometry and geography Data Types</span></span>
 <span data-ttu-id="23ba9-136">2 つの空間データ型の動作はよく似ていますが、データの格納および操作の方法にいくつかの重要な違いがあります。</span><span class="sxs-lookup"><span data-stu-id="23ba9-136">The two types of spatial data often behave quite similarly, but there are some key differences in how the data is stored and manipulated.</span></span>

### <a name="how-connecting-edges-are-defined"></a><span data-ttu-id="23ba9-137">接続エッジの定義方法</span><span class="sxs-lookup"><span data-stu-id="23ba9-137">How connecting edges are defined</span></span>
 <span data-ttu-id="23ba9-138">`LineString` 型と `Polygon` 型の定義データは頂点のみです。</span><span class="sxs-lookup"><span data-stu-id="23ba9-138">The defining data for `LineString` and `Polygon` types are vertices only.</span></span>  <span data-ttu-id="23ba9-139">geometry 型の 2 つの頂点間の接続エッジは直線です。</span><span class="sxs-lookup"><span data-stu-id="23ba9-139">The connecting edge between two vertices in a geometry type is a straight line.</span></span>  <span data-ttu-id="23ba9-140">一方、geography 型の 2 つの頂点間の接続エッジは、2 つの頂点を結ぶ短い方の大楕円弧です。</span><span class="sxs-lookup"><span data-stu-id="23ba9-140">However, the connecting edge between two vertices in a geography type is a short great elliptic arc between the two vertices.</span></span>  <span data-ttu-id="23ba9-141">大楕円は、楕円体とその中心を通る平面との交線であり、大楕円弧は、大楕円の円弧セグメントです。</span><span class="sxs-lookup"><span data-stu-id="23ba9-141">A great ellipse is the intersection of the ellipsoid with a plane through its center and a great elliptic arc is an arc segment on the great ellipse.</span></span>

### <a name="how-circular-arc-segments-are-defined"></a><span data-ttu-id="23ba9-142">円弧セグメントの定義方法</span><span class="sxs-lookup"><span data-stu-id="23ba9-142">How circular arc segments are defined</span></span>
 <span data-ttu-id="23ba9-143">geometry 型の円弧セグメントは、XY デカルト座標平面上に定義されます (Z 値は無視されます)。</span><span class="sxs-lookup"><span data-stu-id="23ba9-143">Circular arc segments for geometry types are defined on the XY Cartesian coordinate plane (Z values are ignored).</span></span> <span data-ttu-id="23ba9-144">geography 型の円弧セグメントは、参照球の曲線セグメントによって定義されます。</span><span class="sxs-lookup"><span data-stu-id="23ba9-144">Circular arc segments for geography types are defined by curve segments on a reference sphere.</span></span> <span data-ttu-id="23ba9-145">参照球の平行線は、両方の円弧の点に一定の緯度角がある、2 つの補助的な円弧によって定義できます。</span><span class="sxs-lookup"><span data-stu-id="23ba9-145">Any parallel on the reference sphere can be defined by two complementary circular arcs where the points for both arcs have a constant latitude angle.</span></span>

### <a name="measurements-in-spatial-data-types"></a><span data-ttu-id="23ba9-146">空間データ型の測定</span><span class="sxs-lookup"><span data-stu-id="23ba9-146">Measurements in spatial data types</span></span>
 <span data-ttu-id="23ba9-147">平面 (平面地球) 座標系では、距離や面積の測定値は座標と同じ測定単位で表されます。</span><span class="sxs-lookup"><span data-stu-id="23ba9-147">In the planar, or flat-earth, system, measurements of distances and areas are given in the same unit of measurement as coordinates.</span></span> <span data-ttu-id="23ba9-148">`geometry` データ型を使用した場合、(2, 2) と (5, 6) の間の距離は、使用されている単位に関係なく 5 単位になります。</span><span class="sxs-lookup"><span data-stu-id="23ba9-148">Using the `geometry` data type, the distance between (2, 2) and (5, 6) is 5 units, regardless of the units used.</span></span>

 <span data-ttu-id="23ba9-149">楕円体 (球体地球) 座標系では、座標は緯度と経度で表されます。</span><span class="sxs-lookup"><span data-stu-id="23ba9-149">In the ellipsoidal, or round-earth system, coordinates are given in degrees of latitude and longitude.</span></span> <span data-ttu-id="23ba9-150">ただし、長さと面積は、`geography` インスタンスの SRID (Spatial Reference Identifier) によっても異なりますが、通常はメートルと平方メートルで測定されます。</span><span class="sxs-lookup"><span data-stu-id="23ba9-150">However, lengths and areas are usually measured in meters and square meters, though the measurement may depend on the spatial reference identifier (SRID) of the `geography` instance.</span></span> <span data-ttu-id="23ba9-151">メートルは、`geography` データ型の最も一般的な測定単位です。</span><span class="sxs-lookup"><span data-stu-id="23ba9-151">The most common unit of measurement for the `geography` data type is meters.</span></span>

### <a name="orientation-of-spatial-data"></a><span data-ttu-id="23ba9-152">空間データの方向</span><span class="sxs-lookup"><span data-stu-id="23ba9-152">Orientation of spatial data</span></span>
 <span data-ttu-id="23ba9-153">平面座標系では、ポリゴンのリングの方向は重要ではありません。</span><span class="sxs-lookup"><span data-stu-id="23ba9-153">In the planar system, the ring orientation of a polygon is not an important factor.</span></span> <span data-ttu-id="23ba9-154">たとえば、((0, 0), (10, 0), (0, 20), (0, 0)) によって表されるポリゴンは、((0, 0), (0, 20), (10, 0), (0, 0)) によって表されるポリゴンと同じです。</span><span class="sxs-lookup"><span data-stu-id="23ba9-154">For example, a polygon described by ((0, 0), (10, 0), (0, 20), (0, 0)) is the same as a polygon described by ((0, 0), (0, 20), (10, 0), (0, 0)).</span></span> <span data-ttu-id="23ba9-155">OGC Simple Features for SQL Specification では、リングの順序は定められていません。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] でもリングの順序は強制されません。</span><span class="sxs-lookup"><span data-stu-id="23ba9-155">The OGC Simple Features for SQL Specification does not dictate a ring ordering, and [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] does not enforce ring ordering.</span></span>

 <span data-ttu-id="23ba9-156">楕円体座標系では、ポリゴンは方向がないと意味がなくなります (あいまいになります)。</span><span class="sxs-lookup"><span data-stu-id="23ba9-156">In an ellipsoidal system, a polygon has no meaning, or is ambiguous, without an orientation.</span></span> <span data-ttu-id="23ba9-157">たとえば、赤道の周りのリングが北半球を表すのか南半球を表すのかがわからなくなります。</span><span class="sxs-lookup"><span data-stu-id="23ba9-157">For example, does a ring around the equator describe the northern or southern hemisphere?</span></span> <span data-ttu-id="23ba9-158">`geography` データ型を使用して空間インスタンスを格納する場合は、リングの方向を指定し、インスタンスの位置を正確に示す必要があります。</span><span class="sxs-lookup"><span data-stu-id="23ba9-158">If we use the `geography` data type to store the spatial instance, we must specify the orientation of the ring and accurately describe the location of the instance.</span></span> <span data-ttu-id="23ba9-159">楕円体座標系の多角形の内部は、左辺ルールによって定義されます。</span><span class="sxs-lookup"><span data-stu-id="23ba9-159">The interior of the polygon in an ellipsoidal system is defined by the left-hand rule.</span></span>

 <span data-ttu-id="23ba9-160">互換性レベルが100以下の場合、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] `geography` データ型には次の制限があります。</span><span class="sxs-lookup"><span data-stu-id="23ba9-160">When the compatibility level is 100 or below in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] then the `geography` data type has the following restrictions:</span></span>

-   <span data-ttu-id="23ba9-161">各 `geography` インスタンスが 1 つの半球に収まる必要があります。</span><span class="sxs-lookup"><span data-stu-id="23ba9-161">Each `geography` instance must fit inside a single hemisphere.</span></span> <span data-ttu-id="23ba9-162">半球よりも大きい空間オブジェクトを格納することはできません。</span><span class="sxs-lookup"><span data-stu-id="23ba9-162">No spatial objects larger than a hemisphere can be stored.</span></span>

-   <span data-ttu-id="23ba9-163">Open Geospatial Consortium (OGC) の Well-Known Text (WKT) 表現または Well-Known Binary (WKB) 表現の `geography` インスタンスでは、半球より大きいオブジェクトが生成される場合に `ArgumentException` がスローされます。</span><span class="sxs-lookup"><span data-stu-id="23ba9-163">Any `geography` instance from an Open Geospatial Consortium (OGC) Well-Known Text (WKT) or Well-Known Binary (WKB) representation that produces an object larger than a hemisphere throws an `ArgumentException`.</span></span>

-   <span data-ttu-id="23ba9-164">`geography`2 つのインスタンスの入力を必要とするデータ型メソッド ( `geography` stintersection ()、stintersection ()、stintersection ()、Stsym減法 () など) は、メソッドの結果が1つの格納範囲内に収まっていない場合に null を返します。</span><span class="sxs-lookup"><span data-stu-id="23ba9-164">The `geography` data type methods that require the input of two `geography` instances, such as STIntersection(), STUnion(), STDifference(), and STSymDifference(), will return null if the results from the methods do not fit inside a single hemisphere.</span></span> <span data-ttu-id="23ba9-165">STBuffer() でも、出力が 1 つの半球に収まらない場合に null が返されます。</span><span class="sxs-lookup"><span data-stu-id="23ba9-165">STBuffer() will also return null if the output exceeds a single hemisphere.</span></span>

 <span data-ttu-id="23ba9-166">[!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] の `FullGlobe` は、球全体を覆う特殊な多角形です。</span><span class="sxs-lookup"><span data-stu-id="23ba9-166">In [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], `FullGlobe` is a special type of Polygon that covers the entire globe.</span></span> <span data-ttu-id="23ba9-167">`FullGlobe` には領域がありますが、境界や頂点はありません。</span><span class="sxs-lookup"><span data-stu-id="23ba9-167">`FullGlobe` has an area, but no borders or vertices.</span></span>

### <a name="outer-and-inner-rings-not-important-in-geography-data-type"></a><span data-ttu-id="23ba9-168">geography データ型では外部リングと内部リングは重要ではない</span><span class="sxs-lookup"><span data-stu-id="23ba9-168">Outer and inner rings not important in geography data type</span></span>
 <span data-ttu-id="23ba9-169">OGC Simple Features for SQL Specification では外部リングと内部リングについて説明していますが、この区別はデータ型にとってはあまり意味がありませ [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] `geography` ん。ポリゴンのリングを外部リングとして使用できます。</span><span class="sxs-lookup"><span data-stu-id="23ba9-169">The OGC Simple Features for SQL Specification discusses outer rings and inner rings, but this distinction makes little sense for the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] `geography` data type; any ring of a polygon can be taken to be the outer ring.</span></span>

 <span data-ttu-id="23ba9-170">OGC の仕様の詳細については、以下を参照してください。</span><span class="sxs-lookup"><span data-stu-id="23ba9-170">For more information on OGC specifications, see the following:</span></span>

-   [<span data-ttu-id="23ba9-171">OGC の仕様、簡易機能アクセス Part 1 - 共通アーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="23ba9-171">OGC Specifications, Simple Feature Access Part 1 - Common Architecture</span></span>](https://go.microsoft.com/fwlink/?LinkId=93627)

-   [<span data-ttu-id="23ba9-172">OGC の仕様、簡易機能アクセス Part 2 - SQL オプション</span><span class="sxs-lookup"><span data-stu-id="23ba9-172">OGC Specifications, Simple Feature Access Part 2 - SQL Options</span></span>](https://go.microsoft.com/fwlink/?LinkId=93628)


##  <a name="circular-arc-segments"></a><a name="circular"></a> <span data-ttu-id="23ba9-173">円弧セグメント</span><span class="sxs-lookup"><span data-stu-id="23ba9-173">Circular Arc Segments</span></span>
 <span data-ttu-id="23ba9-174">円弧セグメントでは、`CircularString`、`CompoundCurve`、および `CurvePolygon` の 3 つのインスタンス化可能な型を使用できます。</span><span class="sxs-lookup"><span data-stu-id="23ba9-174">Three instantiable types can take circular arc segments: `CircularString`, `CompoundCurve`, and `CurvePolygon`.</span></span>  <span data-ttu-id="23ba9-175">円弧セグメントは、2 次元平面内の 3 つの点によって定義されます。3 番目のポイントを最初のポイントと同じにすることはできません。</span><span class="sxs-lookup"><span data-stu-id="23ba9-175">A circular arc segment is defined by three points in a two dimensional plane and the third point cannot be the same as the first point.</span></span>

 <span data-ttu-id="23ba9-176">図 A と図 B は、一般的な円弧のセグメントを示します。</span><span class="sxs-lookup"><span data-stu-id="23ba9-176">Figures A and B show typical circular arc segments.</span></span> <span data-ttu-id="23ba9-177">3 つの点が 1 つの円周上にあることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="23ba9-177">Note how each of the three points lie on the perimeter of a circle.</span></span>

 <span data-ttu-id="23ba9-178">図 C および図 D は、直線セグメントを円弧セグメントとして定義できる方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="23ba9-178">Figures C and D show how a line segment can be defined as a circular arc segment.</span></span>  <span data-ttu-id="23ba9-179">2 つの点のみによって定義できる通常の直線セグメントとは異なり、円弧セグメントを定義するには 3 つの点が必要であることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="23ba9-179">Note that three points are still needed to define the circular arc segment unlike a regular line segment which can be defined by just two points.</span></span>

 <span data-ttu-id="23ba9-180">円弧型を操作するメソッドは、直線セグメントを使用して大まかな円弧を作成します。大まかな円を作成するために使用される直線セグメントの数は、円弧の長さと曲率によって異なります。Z 値はそれぞれの円弧型で格納できますが、メソッドは計算に Z 値を使用しません。</span><span class="sxs-lookup"><span data-stu-id="23ba9-180">Methods operating on circular arc segment types use straight line segments to approximate the circular arc. The number of line segments used to approximate the arc will depend on the length and curvature of the arc. Z values can be stored for each of the circular arc segment types; however, methods will not use the Z values in their calculations.</span></span>

> [!NOTE]
>  <span data-ttu-id="23ba9-181">Z 値が円弧セグメントに指定されている場合、円弧セグメントが入力として許容されるようにするには、円弧セグメント内のすべての点で Z 値が同じである必要があります。</span><span class="sxs-lookup"><span data-stu-id="23ba9-181">If Z values are given for circular arc segments then they must be the same for all points in the circular arc segment for it to be accepted for input.</span></span> <span data-ttu-id="23ba9-182">たとえば、 `CIRCULARSTRING(0 0 1, 2 2 1, 4 0 1)` は許容されますが、 `CIRCULARSTRING(0 0 1, 2 2 2, 4 0 1)` は許容されません。</span><span class="sxs-lookup"><span data-stu-id="23ba9-182">For example: `CIRCULARSTRING(0 0 1, 2 2 1, 4 0 1)` is accepted, but `CIRCULARSTRING(0 0 1, 2 2 2, 4 0 1)` is not accepted.</span></span>

### <a name="linestring-and-circularstring-comparison"></a><span data-ttu-id="23ba9-183">LineString と CircularString の比較</span><span class="sxs-lookup"><span data-stu-id="23ba9-183">LineString and CircularString comparison</span></span>
 <span data-ttu-id="23ba9-184">次の図は、同一の二等辺三角形を示しています (三角形 A は直線セグメントを使用して三角形を定義し、三角形 B は円弧セグメントを使用して三角形を定義しています)。</span><span class="sxs-lookup"><span data-stu-id="23ba9-184">The following diagram shows identical isosceles triangles (triangle A uses line segments to define the triangle and triangle B uses circular arc segments to defined the triangle):</span></span>

 ![](../../database-engine/media/7e382f76-59da-4b62-80dc-caf93e637c14.png "7e382f76-59da-4b62-80dc-caf93e637c14")

 <span data-ttu-id="23ba9-185">この例は、`LineString` インスタンスと `CircularString` インスタンスの両方を使用して上の二等辺三角形を格納する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="23ba9-185">This example shows how to store the above isosceles triangles using both a `LineString` instance and `CircularString` instance:</span></span>

```sql
DECLARE @g1 geometry;
DECLARE @g2 geometry;
SET @g1 = geometry::STGeomFromText('LINESTRING(1 1, 5 1, 3 5, 1 1)', 0);
SET @g2 = geometry::STGeomFromText('CIRCULARSTRING(1 1, 3 1, 5 1, 4 3, 3 5, 2 3, 1 1)', 0);
IF @g1.STIsValid() = 1 AND @g2.STIsValid() = 1
  BEGIN
      SELECT @g1.ToString(), @g2.ToString()
      SELECT @g1.STLength() AS [LS Length], @g2.STLength() AS [CS Length]
  END
```

 <span data-ttu-id="23ba9-186">`CircularString` インスタンスでは、三角形を定義するために 7 つの点が必要ですが、`LineString` インスタンスでは、三角形を定義するために必要な点は 4 つだけです。</span><span class="sxs-lookup"><span data-stu-id="23ba9-186">Notice that a `CircularString` instance requires seven points to define the triangle, but a `LineString` instance requires only four points to define the triangle.</span></span> <span data-ttu-id="23ba9-187">その理由は、`CircularString` インスタンスは直線セグメントではなく円弧セグメントを格納するためです。</span><span class="sxs-lookup"><span data-stu-id="23ba9-187">The reason for this is that a `CircularString` instance stores circular arc segments and not line segments.</span></span> <span data-ttu-id="23ba9-188">したがって、`CircularString` インスタンスに格納される三角形の辺は ABC、CDE、および EFA であるのに対し、`LineString` インスタンスに格納される三角形の辺は AC、CE、および EA です。</span><span class="sxs-lookup"><span data-stu-id="23ba9-188">So the sides of the triangle stored in the `CircularString` instance are ABC, CDE, and EFA whereas the sides of the triangle stored in the `LineString` instance are AC, CE, and EA.</span></span>

 <span data-ttu-id="23ba9-189">次のコード スニペットを考えてみます。</span><span class="sxs-lookup"><span data-stu-id="23ba9-189">Consider the following code snippet:</span></span>

```sql
SET @g1 = geometry::STGeomFromText('LINESTRING(0 0, 2 2, 4 0)', 0);
SET @g2 = geometry::STGeomFromText('CIRCULARSTRING(0 0, 2 2, 4 0)', 0);
SELECT @g1.STLength() AS [LS Length], @g2.STLength() AS [CS Length];
```

 <span data-ttu-id="23ba9-190">このスニペットの結果は、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="23ba9-190">This snippet will produce the following results:</span></span>

```
LS LengthCS Length
5.65685...6.28318...
```

 <span data-ttu-id="23ba9-191">次の図は、各型がどのように格納されているかを示しています (赤い線 `LineString``@g1` の表示、青い線の表示 `CircularString``@g2` )。</span><span class="sxs-lookup"><span data-stu-id="23ba9-191">The following illustration shows how each type is stored (red line shows `LineString``@g1`, blue line shows `CircularString``@g2`):</span></span>

 ![](../../database-engine/media/e52157b5-5160-4a4b-8560-50cdcf905b76.png "e52157b5-5160-4a4b-8560-50cdcf905b76")

 <span data-ttu-id="23ba9-192">上の図が示すように、`CircularString` インスタンスでは `LineString` インスタンスよりも少ない点を使用して、さらに高い精度で曲面境界を格納します。</span><span class="sxs-lookup"><span data-stu-id="23ba9-192">As the illustration above shows, `CircularString` instances use fewer points to store curve boundaries with greater precision than `LineString` instances.</span></span> <span data-ttu-id="23ba9-193">`CircularString` インスタンスは、たとえば特定の点から半径 20 マイルの検索を行う際など、円形境界を格納する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="23ba9-193">`CircularString` instances are useful for storing circular boundaries like a twenty-mile search radius from a specific point.</span></span> <span data-ttu-id="23ba9-194">`LineString` インスタンスは、四角い都市区画のような直線的な境界を格納する場合に適しています。</span><span class="sxs-lookup"><span data-stu-id="23ba9-194">`LineString` instances are good for storing boundaries that are linear like a square city block.</span></span>

### <a name="linestring-and-compoundcurve-comparison"></a><span data-ttu-id="23ba9-195">LineString と CompoundCurve の比較</span><span class="sxs-lookup"><span data-stu-id="23ba9-195">LineString and CompoundCurve comparison</span></span>
 <span data-ttu-id="23ba9-196">次のコード例は、`LineString` インスタンスと `CompoundCurve` インスタンスを使用して同じ図を格納する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="23ba9-196">The following code examples show how to store the same figure using `LineString` and `CompoundCurve` instances:</span></span>

```sql
SET @g = geometry::Parse('LINESTRING(2 2, 4 2, 4 4, 2 4, 2 2)');
SET @g = geometry::Parse('COMPOUNDCURVE((2 2, 4 2), (4 2, 4 4), (4 4, 2 4), (2 4, 2 2))');
SET @g = geometry::Parse('COMPOUNDCURVE((2 2, 4 2, 4 4, 2 4, 2 2))');
```

 <span data-ttu-id="23ba9-197">or</span><span class="sxs-lookup"><span data-stu-id="23ba9-197">or</span></span>

 <span data-ttu-id="23ba9-198">上の例では、`LineString` インスタンスまたは `CompoundCurve` インスタンスで図を格納できます。</span><span class="sxs-lookup"><span data-stu-id="23ba9-198">In the examples above, either a `LineString` instance or a `CompoundCurve` instance could store the figure.</span></span>  <span data-ttu-id="23ba9-199">次の例では、`CompoundCurve` を使用して円のスライスを格納します。</span><span class="sxs-lookup"><span data-stu-id="23ba9-199">This next example uses a `CompoundCurve` to store a pie slice:</span></span>

```sql
SET @g = geometry::Parse('COMPOUNDCURVE(CIRCULARSTRING(2 2, 1 3, 0 2),(0 2, 1 0, 2 2))');
```

 <span data-ttu-id="23ba9-200">`CompoundCurve` インスタンスは円弧セグメント (2 2, 1 3, 0 2) を直接格納できますが、`LineString` インスタンスでは曲線をいくつかの小さな直線セグメントに変換する必要があります。</span><span class="sxs-lookup"><span data-stu-id="23ba9-200">A `CompoundCurve` instance can store the circular arc segment (2 2, 1 3, 0 2) directly whereas a `LineString` instance would have to convert the curve into several smaller line segments.</span></span>

### <a name="circularstring-and-compoundcurve-comparison"></a><span data-ttu-id="23ba9-201">CircularString と CompoundCurve の比較</span><span class="sxs-lookup"><span data-stu-id="23ba9-201">CircularString and CompoundCurve comparison</span></span>
 <span data-ttu-id="23ba9-202">次のコード例は、`CircularString` インスタンスに円のスライスを格納する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="23ba9-202">The following code example shows how the pie slice can be stored in a `CircularString` instance:</span></span>

```sql
DECLARE @g geometry;
SET @g = geometry::Parse('CIRCULARSTRING( 0 0, 1 2.1082, 3 6.3246, 0 7, -3 6.3246, -1 2.1082, 0 0)');
SELECT @g.ToString(), @g.STLength();
```

 <span data-ttu-id="23ba9-203">`CircularString` インスタンスを使用して円のスライスを格納するには、各直線セグメントで 3 つの点を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="23ba9-203">To store the pie slice using a `CircularString` instance requires that three points be used for each line segment.</span></span>  <span data-ttu-id="23ba9-204">中間点が不明な場合は、中間点を計算するか、次のスニペットで示すように直線セグメントの端点を二重にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="23ba9-204">If an intermediate point is not known, it either has to be calculated or the endpoint of the line segment has to be doubled as the following snippet shows:</span></span>

```sql
SET @g = geometry::Parse('CIRCULARSTRING( 0 0, 3 6.3246, 3 6.3246, 0 7, -3 6.3246, 0 0, 0 0)');
```

 <span data-ttu-id="23ba9-205">`CompoundCurve` インスタンスは `LineString` コンポーネントおよび `CircularString` コンポーネントを許可して、認識される必要がある点が、円のスライスの直線セグメントの 2 点だけになるようにします。</span><span class="sxs-lookup"><span data-stu-id="23ba9-205">`CompoundCurve` instances allow both `LineString` and `CircularString` components so that only two points to the line segments of the pie slice need to be known.</span></span>  <span data-ttu-id="23ba9-206">このコード例は、`CompoundCurve` を使用して同じ図を格納する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="23ba9-206">This code example shows how to use a `CompoundCurve` to store the same figure:</span></span>

```sql
DECLARE @g geometry;
SET @g = geometry::Parse('COMPOUNDCURVE(CIRCULARSTRING( 3 6.3246, 0 7, -3 6.3246), (-3 6.3246, 0 0, 3 6.3246))');
SELECT @g.ToString(), @g.STLength();
```

### <a name="polygon-and-curvepolygon-comparison"></a><span data-ttu-id="23ba9-207">Polygon と CurvePolygon の比較</span><span class="sxs-lookup"><span data-stu-id="23ba9-207">Polygon and CurvePolygon comparison</span></span>
 <span data-ttu-id="23ba9-208">`CurvePolygon` インスタンスは、外部リングと内部リングを定義するときに `CircularString` インスタンスと `CompoundCurve` インスタンスを使用できます。</span><span class="sxs-lookup"><span data-stu-id="23ba9-208">`CurvePolygon` instances can use `CircularString` and `CompoundCurve` instances when defining their exterior and interior rings.</span></span>  <span data-ttu-id="23ba9-209">`Polygon` インスタンスは、`CircularString` および `CompoundCurve` の円弧型を使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="23ba9-209">`Polygon` instances cannot use the circular arc segment types: `CircularString` and `CompoundCurve`.</span></span>


## <a name="see-also"></a><span data-ttu-id="23ba9-210">参照</span><span class="sxs-lookup"><span data-stu-id="23ba9-210">See Also</span></span>
 <span data-ttu-id="23ba9-211">[空間データ &#40;SQL Server&#41;](../spatial/spatial-data-sql-server.md) [Geometry データ型メソッド参照](/sql/t-sql/spatial-geometry/spatial-types-geometry-transact-sql) [geography データ型メソッド参照](/sql/t-sql/spatial-geography/spatial-types-geography) [stnumcurves &#40;geometry データ型&#41;](/sql/t-sql/spatial-geometry/stnumcurves-geometry-data-type) [stnumcurves &#40;geography データ型](/sql/t-sql/spatial-geography/stnumcurves-geography-data-type)&#41;[STGeomFromText &#40;geometry データ型&#41;](/sql/t-sql/spatial-geometry/stgeomfromtext-geometry-data-type) [STGeomFromText &#40;geography データ型&#41;](/sql/t-sql/spatial-geography/stgeomfromtext-geography-data-type)</span><span class="sxs-lookup"><span data-stu-id="23ba9-211">[Spatial Data &#40;SQL Server&#41;](../spatial/spatial-data-sql-server.md) [geometry Data Type Method Reference](/sql/t-sql/spatial-geometry/spatial-types-geometry-transact-sql) [geography Data Type Method Reference](/sql/t-sql/spatial-geography/spatial-types-geography) [STNumCurves &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stnumcurves-geometry-data-type) [STNumCurves &#40;geography Data Type&#41;](/sql/t-sql/spatial-geography/stnumcurves-geography-data-type) [STGeomFromText &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stgeomfromtext-geometry-data-type) [STGeomFromText &#40;geography Data Type&#41;](/sql/t-sql/spatial-geography/stgeomfromtext-geography-data-type)</span></span>


