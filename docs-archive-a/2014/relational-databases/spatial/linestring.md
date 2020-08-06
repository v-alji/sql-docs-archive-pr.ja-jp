---
title: LineString | Microsoft Docs
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- LineString geometry subtype [SQL Server]
- geometry subtypes [SQL Server]
ms.assetid: e50d0b86-8b31-4285-be71-ad05c7712cbd
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 5a0f77959cfe4492eca6c38951ba2868452d41ad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644936"
---
# <a name="linestring"></a><span data-ttu-id="ba1cc-102">LineString</span><span class="sxs-lookup"><span data-stu-id="ba1cc-102">LineString</span></span>
  <span data-ttu-id="ba1cc-103">`LineString` は、一連の点と、それらを結ぶ線分を表す 1 次元のオブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="ba1cc-103">A `LineString` is a one-dimensional object representing a sequence of points and the line segments connecting them.</span></span>

## <a name="linestring-instances"></a><span data-ttu-id="ba1cc-104">LineString インスタンス</span><span class="sxs-lookup"><span data-stu-id="ba1cc-104">LineString Instances</span></span>
 <span data-ttu-id="ba1cc-105">次の図は、`LineString` インスタンスの例です。</span><span class="sxs-lookup"><span data-stu-id="ba1cc-105">The illustration below shows examples of `LineString` instances.</span></span>

 <span data-ttu-id="ba1cc-106">![geometry LineString インスタンスの例](../../database-engine/media/linestring.gif "geometry LineString インスタンスの例")</span><span class="sxs-lookup"><span data-stu-id="ba1cc-106">![Examples of geometry LineString instances](../../database-engine/media/linestring.gif "Examples of geometry LineString instances")</span></span>

 <span data-ttu-id="ba1cc-107">この図は次のことを示しています。</span><span class="sxs-lookup"><span data-stu-id="ba1cc-107">As shown in the illustration:</span></span>

-   <span data-ttu-id="ba1cc-108">図 1 は、単純な閉じていない `LineString` インスタンスです。</span><span class="sxs-lookup"><span data-stu-id="ba1cc-108">Figure 1 is a simple, nonclosed `LineString` instance.</span></span>

-   <span data-ttu-id="ba1cc-109">図 2 は、単純でない、閉じていない `LineString` インスタンスです。</span><span class="sxs-lookup"><span data-stu-id="ba1cc-109">Figure 2 is a nonsimple, nonclosed `LineString` instance.</span></span>

-   <span data-ttu-id="ba1cc-110">図 3 は、閉じている単純な `LineString` インスタンスです。したがって、このインスタンスはリングです。</span><span class="sxs-lookup"><span data-stu-id="ba1cc-110">Figure 3 is a closed, simple `LineString` instance, and therefore is a ring.</span></span>

-   <span data-ttu-id="ba1cc-111">図 4 は、閉じている単純でない `LineString` インスタンスです。したがって、このインスタンスはリングではありません。</span><span class="sxs-lookup"><span data-stu-id="ba1cc-111">Figure 4 is a closed, nonsimple `LineString` instance, and therefore is not a ring.</span></span>

### <a name="accepted-instances"></a><span data-ttu-id="ba1cc-112">許容されるインスタンス</span><span class="sxs-lookup"><span data-stu-id="ba1cc-112">Accepted Instances</span></span>
 <span data-ttu-id="ba1cc-113">許容される `LineString` インスタンスはジオメトリ変数に入力できますが、これらが有効な `LineString` インスタンスであるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="ba1cc-113">Accepted `LineString` instances can be input into a geometry variable, but they may not be valid `LineString` instances.</span></span> <span data-ttu-id="ba1cc-114">`LineString` インスタンスが許容されるには、次の条件を満たす必要があります。</span><span class="sxs-lookup"><span data-stu-id="ba1cc-114">The following criteria must be met for a `LineString` instance to be accepted.</span></span> <span data-ttu-id="ba1cc-115">インスタンスは、2 つ以上の異なる点から構成されているか、または空である必要があります。</span><span class="sxs-lookup"><span data-stu-id="ba1cc-115">The instance must be formed of at least two points or it must be empty.</span></span> <span data-ttu-id="ba1cc-116">次に示す LineString instances インスタンスは許容されます。</span><span class="sxs-lookup"><span data-stu-id="ba1cc-116">The following LineString instances are accepted.</span></span>

```
DECLARE @g1 geometry = 'LINESTRING EMPTY';
DECLARE @g2 geometry = 'LINESTRING(1 1,2 3,4 8, -6 3)';
DECLARE @g3 geometry = 'LINESTRING(1 1, 1 1)';
```

 <span data-ttu-id="ba1cc-117">`@g3` の場合、`LineString` インスタンスは許容されますが、有効ではありません。</span><span class="sxs-lookup"><span data-stu-id="ba1cc-117">`@g3` shows that a `LineString` instance can be accepted, but not valid.</span></span>

 <span data-ttu-id="ba1cc-118">次に示す `LineString` インスタンスは許容されません。</span><span class="sxs-lookup"><span data-stu-id="ba1cc-118">The following `LineString` instance is not accepted.</span></span> <span data-ttu-id="ba1cc-119">`System.FormatException`がスローされます。</span><span class="sxs-lookup"><span data-stu-id="ba1cc-119">It will throw a `System.FormatException`.</span></span>

```
DECLARE @g geometry = 'LINESTRING(1 1)';
```

### <a name="valid-instances"></a><span data-ttu-id="ba1cc-120">有効なインスタンス</span><span class="sxs-lookup"><span data-stu-id="ba1cc-120">Valid Instances</span></span>
 <span data-ttu-id="ba1cc-121">`LineString` インスタンスを有効にするためには、次の条件を満たす必要があります。</span><span class="sxs-lookup"><span data-stu-id="ba1cc-121">For a `LineString` instance to be valid it must meet the following criteria.</span></span>

1.  <span data-ttu-id="ba1cc-122">`LineString` インスタンスが許容されていること。</span><span class="sxs-lookup"><span data-stu-id="ba1cc-122">The `LineString` instance must be accepted.</span></span>

2.  <span data-ttu-id="ba1cc-123">`LineString` インスタンスが空でない場合は、2 つ以上の異なる点が含まれていること。</span><span class="sxs-lookup"><span data-stu-id="ba1cc-123">If a `LineString` instance is not empty then it must contain at least two distinct points.</span></span>

3.  <span data-ttu-id="ba1cc-124">`LineString` インスタンスは、それ自体を 2 つ以上の連続する点の区間に重ねることはできない。</span><span class="sxs-lookup"><span data-stu-id="ba1cc-124">The `LineString` instance cannot overlap itself over an interval of two or more consecutive points.</span></span>

 <span data-ttu-id="ba1cc-125">次に示す `LineString` インスタンスは有効です。</span><span class="sxs-lookup"><span data-stu-id="ba1cc-125">The following `LineString` instances are valid.</span></span>

```
DECLARE @g1 geometry= 'LINESTRING EMPTY';
DECLARE @g2 geometry= 'LINESTRING(1 1, 3 3)';
DECLARE @g3 geometry= 'LINESTRING(1 1, 3 3, 2 4, 2 0)';
DECLARE @g4 geometry= 'LINESTRING(1 1, 3 3, 2 4, 2 0, 1 1)';
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid(), @g4.STIsValid();

```

 <span data-ttu-id="ba1cc-126">次に示す `LineString` インスタンスは無効です。</span><span class="sxs-lookup"><span data-stu-id="ba1cc-126">The following `LineString` instances are not valid.</span></span>

```
DECLARE @g1 geometry = 'LINESTRING(1 4, 3 4, 2 4, 2 0)';
DECLARE @g2 geometry = 'LINESTRING(1 1, 1 1)';
SELECT @g1.STIsValid(), @g2.STIsValid();
```

> [!WARNING]
>  <span data-ttu-id="ba1cc-127">`LineString` の重複の検出は浮動小数点計算に基づいて行われますが、この計算は正確ではありません。</span><span class="sxs-lookup"><span data-stu-id="ba1cc-127">The detection of `LineString` overlaps is based on floating-point calculations, which are not exact.</span></span>

## <a name="examples"></a><span data-ttu-id="ba1cc-128">例</span><span class="sxs-lookup"><span data-stu-id="ba1cc-128">Examples</span></span>
 <span data-ttu-id="ba1cc-129">次の例は、3 つの点を持つ `geometry``LineString` インスタンスを作成する方法を示しています。このインスタンスの SRID は 0 です。</span><span class="sxs-lookup"><span data-stu-id="ba1cc-129">The following example shows how to create a `geometry``LineString` instance with three points and an SRID of 0:</span></span>

```
DECLARE @g geometry;
SET @g = geometry::STGeomFromText('LINESTRING(1 1, 2 4, 3 9)', 0);
```

 <span data-ttu-id="ba1cc-130">`LineString` インスタンスのそれぞれの点には、Z (昇格) 値と M (メジャー) 値を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="ba1cc-130">Each point in the `LineString` instance may contain Z (elevation) and M (measure) values.</span></span> <span data-ttu-id="ba1cc-131">次の例では、上の例で作成した `LineString` インスタンスに M 値を追加します。</span><span class="sxs-lookup"><span data-stu-id="ba1cc-131">This example adds M values to the `LineString` instance created in the example above.</span></span> <span data-ttu-id="ba1cc-132">M および Z は NULL 値にすることができます。</span><span class="sxs-lookup"><span data-stu-id="ba1cc-132">M and Z can be null values.</span></span>

```
DECLARE @g geometry;
SET @g = geometry::STGeomFromText('LINESTRING(1 1 NULL 0, 2 4 NULL 12.3, 3 9 NULL 24.5)', 0);
```

 <span data-ttu-id="ba1cc-133">次の例は、同じ 2 つの点を持つ `geometry LineString` インスタンスを作成する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="ba1cc-133">The following example shows how to create a `geometry LineString` instance with two points that are the same.</span></span> <span data-ttu-id="ba1cc-134">`IsValid` 呼び出しは、`LineString` インスタンスが無効であることを示します。`MakeValid` 呼び出しは、`LineString` インスタンスを `Point` に変換します。</span><span class="sxs-lookup"><span data-stu-id="ba1cc-134">A call to `IsValid` indicates that the `LineString` instance is not valid and a call to `MakeValid` will convert the `LineString` instance into a `Point`.</span></span>

```sql
DECLARE @g geometry
SET @g = geometry::STGeomFromText('LINESTRING(1 3, 1 3)',0);
IF @g.STIsValid() = 1
  BEGIN
     SELECT @g.ToString() + ' is a valid LineString.';  
  END
ELSE
  BEGIN
     SELECT @g.ToString() + ' is not a valid LineString.';
     SET @g = @g.MakeValid();
     SELECT @g.ToString() + ' is a valid Point.';  
  END

```

 <span data-ttu-id="ba1cc-135">上のコード スニペットは、次の結果を返します。</span><span class="sxs-lookup"><span data-stu-id="ba1cc-135">The above code snippet will return the following:</span></span>

```
LINESTRING(1 3, 1 3) is not a valid LineString
POINT(1 3) is a valid Point.
```

## <a name="see-also"></a><span data-ttu-id="ba1cc-136">参照</span><span class="sxs-lookup"><span data-stu-id="ba1cc-136">See Also</span></span>
 <span data-ttu-id="ba1cc-137">[Stlength &#40;Geometry データ型&#41;](/sql/t-sql/spatial-geometry/stlength-geometry-data-type) [STStartPoint &#40;geometry データ型&#41;](/sql/t-sql/spatial-geometry/ststartpoint-geometry-data-type) [stlength &#40;geometry データ型&#41;](/sql/t-sql/spatial-geometry/stendpoint-geometry-data-type) [stpointn &#40;geometry](/sql/t-sql/spatial-geometry/stpointn-geometry-data-type)データ型&#41;[stnumpoints](/sql/t-sql/spatial-geometry/stnumpoints-geometry-data-type) &#40;geometry データ型&#41;stisring [STIsRing &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stisring-geometry-data-type) [&#40;geometry データ](/sql/t-sql/spatial-geometry/stisclosed-geometry-data-type)型&#41;[stpointonsurface](/sql/t-sql/spatial-geometry/stpointonsurface-geometry-data-type) &#40;geometry データ型&#41;[空間データ &#40;](../spatial/spatial-data-sql-server.md)&#41;に &#40;</span><span class="sxs-lookup"><span data-stu-id="ba1cc-137">[STLength &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stlength-geometry-data-type) [STStartPoint &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/ststartpoint-geometry-data-type) [STEndpoint &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stendpoint-geometry-data-type) [STPointN &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stpointn-geometry-data-type) [STNumPoints &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stnumpoints-geometry-data-type) [STIsRing &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stisring-geometry-data-type) [STIsClosed &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stisclosed-geometry-data-type) [STPointOnSurface &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stpointonsurface-geometry-data-type) [Spatial Data &#40;SQL Server&#41;](../spatial/spatial-data-sql-server.md)</span></span>


