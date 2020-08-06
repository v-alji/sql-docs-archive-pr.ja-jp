---
title: MultiLineString | Microsoft Docs
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- MultiLineString geometry subtype [SQL Server]
- geometry subtypes [SQL Server]
ms.assetid: 95deeefe-d6c5-4a11-b347-379e4486e7b7
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: fdd093d99d055df8e15fc22e3e570e6805e35d6e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644928"
---
# <a name="multilinestring"></a><span data-ttu-id="3bf3c-102">MultiLineString</span><span class="sxs-lookup"><span data-stu-id="3bf3c-102">MultiLineString</span></span>
  <span data-ttu-id="3bf3c-103">は、 `MultiLineString` 0 個以上の `geometry` インスタンスまたは**geographyLineString**インスタンスのコレクションです。</span><span class="sxs-lookup"><span data-stu-id="3bf3c-103">A `MultiLineString` is a collection of zero or more `geometry` or **geographyLineString** instances.</span></span>  
  
## <a name="multilinestring-instances"></a><span data-ttu-id="3bf3c-104">MultiLineString インスタンス</span><span class="sxs-lookup"><span data-stu-id="3bf3c-104">MultiLineString instances</span></span>  
 <span data-ttu-id="3bf3c-105">次の図は、`MultiLineString` インスタンスの例です。</span><span class="sxs-lookup"><span data-stu-id="3bf3c-105">The illustration below shows examples of `MultiLineString` instances.</span></span>  
  
 <span data-ttu-id="3bf3c-106">![geometry MultiLineString インスタンスの例](../../database-engine/media/multilinestring.gif "geometry MultiLineString インスタンスの例")</span><span class="sxs-lookup"><span data-stu-id="3bf3c-106">![Examples of geometry MultiLineString instances](../../database-engine/media/multilinestring.gif "Examples of geometry MultiLineString instances")</span></span>  
  
 <span data-ttu-id="3bf3c-107">この図は次のことを示しています。</span><span class="sxs-lookup"><span data-stu-id="3bf3c-107">As shown in the illustration:</span></span>  
  
-   <span data-ttu-id="3bf3c-108">図1は、 `MultiLineString` 境界が2つの要素の4つのエンドポイントである単純なインスタンスです `LineString` 。</span><span class="sxs-lookup"><span data-stu-id="3bf3c-108">Figure 1 is a simple `MultiLineString` instance whose boundary is the four endpoints of its two `LineString` elements.</span></span>  
  
-   <span data-ttu-id="3bf3c-109">図 2 の `MultiLineString` インスタンスは、`LineString` 要素の終点のみで交差しているため単純です。</span><span class="sxs-lookup"><span data-stu-id="3bf3c-109">Figure 2 is a simple `MultiLineString` instance because only the endpoints of the `LineString` elements intersect.</span></span> <span data-ttu-id="3bf3c-110">このインスタンスの境界は、重なっていない 2 つの終点です。</span><span class="sxs-lookup"><span data-stu-id="3bf3c-110">The boundary is the two non-overlapping endpoints.</span></span>  
  
-   <span data-ttu-id="3bf3c-111">図 3 の `MultiLineString` インスタンスは、一方の `LineString` 要素の内部で交差しているため単純ではありません。</span><span class="sxs-lookup"><span data-stu-id="3bf3c-111">Figure 3 is a nonsimple `MultiLineString` instance because the interior of one of its `LineString` elements is intersected.</span></span> <span data-ttu-id="3bf3c-112">この `MultiLineString` インスタンスの境界は 4 つの終点です。</span><span class="sxs-lookup"><span data-stu-id="3bf3c-112">The boundary of this `MultiLineString` instance is the four endpoints.</span></span>  
  
-   <span data-ttu-id="3bf3c-113">図 4 は、単純でなく、閉じていない `MultiLineString` インスタンスです。</span><span class="sxs-lookup"><span data-stu-id="3bf3c-113">Figure 4 is a nonsimple, nonclosed `MultiLineString` instance.</span></span>  
  
-   <span data-ttu-id="3bf3c-114">図 5 は、単純な閉じていない `MultiLineString` です。</span><span class="sxs-lookup"><span data-stu-id="3bf3c-114">Figure 5 is a simple, nonclosed `MultiLineString`.</span></span> <span data-ttu-id="3bf3c-115">要素が閉じられていないため、閉じられていません `LineStrings` 。</span><span class="sxs-lookup"><span data-stu-id="3bf3c-115">It is not closed because its `LineStrings` elements are not closed.</span></span> <span data-ttu-id="3bf3c-116">このインスタンスが単純なのは、内部で交差している `LineStrings` インスタンスがないからです。</span><span class="sxs-lookup"><span data-stu-id="3bf3c-116">It is simple because none of the interiors of any of the `LineStrings` instances intersect.</span></span>  
  
-   <span data-ttu-id="3bf3c-117">図 6 は、単純な閉じている `MultiLineString` インスタンスです。</span><span class="sxs-lookup"><span data-stu-id="3bf3c-117">Figure 6 is a simple, closed `MultiLineString` instance.</span></span> <span data-ttu-id="3bf3c-118">このインスタンスが閉じているのは、そのすべての要素が閉じているからです。</span><span class="sxs-lookup"><span data-stu-id="3bf3c-118">It is closed because all its elements are closed.</span></span> <span data-ttu-id="3bf3c-119">このインスタンスが単純なのは、内部で交差している要素がないからです。</span><span class="sxs-lookup"><span data-stu-id="3bf3c-119">It is simple because none of its elements intersect at the interiors.</span></span>  
  
### <a name="accepted-instances"></a><span data-ttu-id="3bf3c-120">許容されるインスタンス</span><span class="sxs-lookup"><span data-stu-id="3bf3c-120">Accepted instances</span></span>  
 <span data-ttu-id="3bf3c-121">MultiLineString`MultiLineString` インスタンスが許容されるためには、空であるか、許容される `LineString` インスタンスのみで構成されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="3bf3c-121">For a `MultiLineString` instance to be accepted it must either be empty or comprised of only `LineString` intances that are accepted.</span></span> <span data-ttu-id="3bf3c-122">許容されるインスタンスの詳細につい `LineString` ては、「 [LineString](../spatial/linestring.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3bf3c-122">For more information on accepted `LineString` instances, see [LineString](../spatial/linestring.md).</span></span> <span data-ttu-id="3bf3c-123">次の例に、許容される `MultiLineString` インスタンスを示します。</span><span class="sxs-lookup"><span data-stu-id="3bf3c-123">The following are examples of accepted `MultiLineString` instances.</span></span>  
  
```  
DECLARE @g1 geometry = 'MULTILINESTRING EMPTY';  
DECLARE @g2 geometry = 'MULTILINESTRING((1 1, 3 5), (-5 3, -8 -2))';  
DECLARE @g3 geometry = 'MULTILINESTRING((1 1, 5 5), (1 3, 3 1))';  
DECLARE @g4 geometry = 'MULTILINESTRING((1 1, 3 3, 5 5),(3 3, 5 5, 7 7))';  
```  
  
 <span data-ttu-id="3bf3c-124">次の例では、2 番目の `LineString` インスタンスが有効ではないため、`System.FormatException` がスローされます。</span><span class="sxs-lookup"><span data-stu-id="3bf3c-124">The following example throws a `System.FormatException` because the second `LineString` instance is not valid.</span></span>  
  
```  
DECLARE @g geometry = 'MULTILINESTRING((1 1, 3 5),(-5 3))';  
```  
  
### <a name="valid-instances"></a><span data-ttu-id="3bf3c-125">有効なインスタンス</span><span class="sxs-lookup"><span data-stu-id="3bf3c-125">Valid instances</span></span>  
 <span data-ttu-id="3bf3c-126">インスタンスを有効にするには、 `MultiLineString` 次の条件を満たしている必要があります。</span><span class="sxs-lookup"><span data-stu-id="3bf3c-126">For a `MultiLineString` instance to be valid it must meet the following criteria:</span></span>  
  
1.  <span data-ttu-id="3bf3c-127">`MultiLineString` インスタンスを構成するすべてのインスタンスが、有効な `LineString` インスタンスである。</span><span class="sxs-lookup"><span data-stu-id="3bf3c-127">All instances comprising the `MultiLineString` instance must be valid `LineString` instances.</span></span>  
  
2.  <span data-ttu-id="3bf3c-128">`LineString` インスタンスを構成する 2 つの `MultiLineString` インスタンスが内部で互いに重ならない。</span><span class="sxs-lookup"><span data-stu-id="3bf3c-128">No two `LineString` instances comprising the `MultiLineString` instance may overlap over an interval.</span></span> <span data-ttu-id="3bf3c-129">`LineString` インスタンスは、有限数の接点のみで、互いにまたは他の `LineString` インスタンスと交差するか接することができます。</span><span class="sxs-lookup"><span data-stu-id="3bf3c-129">The `LineString` instances can only intersect or touch themselves or other `LineString` instances at a finite number of points.</span></span>  
  
 <span data-ttu-id="3bf3c-130">次の例に、3 つの有効な `MultiLineString` インスタンスと 1 つの無効な `MultiLineString` インスタンスを示します。</span><span class="sxs-lookup"><span data-stu-id="3bf3c-130">The following example shows three valid `MultiLineString` instances and one `MultiLineString` instance that is not valid.</span></span>  
  
```  
DECLARE @g1 geometry = 'MULTILINESTRING EMPTY';  
DECLARE @g2 geometry = 'MULTILINESTRING((1 1, 3 5), (-5 3, -8 -2))';  
DECLARE @g3 geometry = 'MULTILINESTRING((1 1, 5 5), (1 3, 3 1))';  
DECLARE @g4 geometry = 'MULTILINESTRING((1 1, 3 3, 5 5),(3 3, 5 5, 7 7))';  
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid(), @g4.STIsValid();  
```  
  
 <span data-ttu-id="3bf3c-131">`@g4` は、2 番目の `LineString` インスタンスが最初の `LineString` インスタンスと内部で重なっているため、有効ではありません。</span><span class="sxs-lookup"><span data-stu-id="3bf3c-131">`@g4` is not valid because the second `LineString` instance overlaps the first `LineString` instance at an interval.</span></span> <span data-ttu-id="3bf3c-132">有限数の接点で接しています。</span><span class="sxs-lookup"><span data-stu-id="3bf3c-132">They touch at an infinite number of points.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="3bf3c-133">例</span><span class="sxs-lookup"><span data-stu-id="3bf3c-133">Examples</span></span>  
 <span data-ttu-id="3bf3c-134">次の例では、2 つの `geometry``MultiLineString` 要素を含む SRID 0 の単純な `LineString` インスタンスを作成しています。</span><span class="sxs-lookup"><span data-stu-id="3bf3c-134">The following example creates a simple `geometry``MultiLineString` instance containing two `LineString` elements with the SRID 0.</span></span>  
  
```  
DECLARE @g geometry;  
SET @g = geometry::Parse('MULTILINESTRING((0 2, 1 1), (1 0, 1 1))');  
```  
  
 <span data-ttu-id="3bf3c-135">このインスタンスを別の SRID で作成するには、 `STGeomFromText()` または `STMLineStringFromText()`を使用します。</span><span class="sxs-lookup"><span data-stu-id="3bf3c-135">To instantiate this instance with a different SRID, use `STGeomFromText()` or `STMLineStringFromText()`.</span></span> <span data-ttu-id="3bf3c-136">次の例のように、 `Parse()` を使用して、その後に SRID を変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="3bf3c-136">You can also use `Parse()` and then modify the SRID, as shown in the following example.</span></span>  
  
```  
DECLARE @g geometry;  
SET @g = geometry::Parse('MULTILINESTRING((0 2, 1 1), (1 0, 1 1))');  
SET @g.STSrid = 13;  
```  
  
## <a name="see-also"></a><span data-ttu-id="3bf3c-137">参照</span><span class="sxs-lookup"><span data-stu-id="3bf3c-137">See Also</span></span>  
 <span data-ttu-id="3bf3c-138">[STLength &#40;geometry データ型&#41;](/sql/t-sql/spatial-geometry/stlength-geometry-data-type) </span><span class="sxs-lookup"><span data-stu-id="3bf3c-138">[STLength &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stlength-geometry-data-type) </span></span>  
 <span data-ttu-id="3bf3c-139">[STIsClosed &#40;geometry データ型&#41;](/sql/t-sql/spatial-geometry/stisclosed-geometry-data-type) </span><span class="sxs-lookup"><span data-stu-id="3bf3c-139">[STIsClosed &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stisclosed-geometry-data-type) </span></span>  
 <span data-ttu-id="3bf3c-140">[LineString](../spatial/linestring.md) </span><span class="sxs-lookup"><span data-stu-id="3bf3c-140">[LineString](../spatial/linestring.md) </span></span>  
 [<span data-ttu-id="3bf3c-141">空間データ &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3bf3c-141">Spatial Data &#40;SQL Server&#41;</span></span>](../spatial/spatial-data-sql-server.md)  
  
  
