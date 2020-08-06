---
title: GeometryCollection | Microsoft Docs
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- GeomCollection geometry subtype [SQL Server]
- geometry subtypes [SQL Server]
ms.assetid: 4445c0d9-a66b-4d7c-88e4-a66fa6f7d9fd
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 71d2234a9b73b7647554e364fe3864f089a47a0b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644938"
---
# <a name="geometrycollection"></a><span data-ttu-id="94f47-102">GeometryCollection</span><span class="sxs-lookup"><span data-stu-id="94f47-102">GeometryCollection</span></span>
  <span data-ttu-id="94f47-103">`GeometryCollection` は、0 個以上の `geometry` インスタンスまたは `geography` インスタンスのコレクションです。</span><span class="sxs-lookup"><span data-stu-id="94f47-103">A `GeometryCollection` is a collection of zero or more `geometry` or `geography` instances.</span></span> <span data-ttu-id="94f47-104">`GeometryCollection` は空にできます。</span><span class="sxs-lookup"><span data-stu-id="94f47-104">A `GeometryCollection` can be empty.</span></span>  
  
## <a name="geometrycollection-instances"></a><span data-ttu-id="94f47-105">GeometryCollection インスタンス</span><span class="sxs-lookup"><span data-stu-id="94f47-105">GeometryCollection Instances</span></span>  
  
### <a name="accepted-instances"></a><span data-ttu-id="94f47-106">許容されるインスタンス</span><span class="sxs-lookup"><span data-stu-id="94f47-106">Accepted Instances</span></span>  
 <span data-ttu-id="94f47-107">`GeometryCollection` インスタンスが許容されるためには、空の `GeometryCollection` インスタンスであるか、`GeometryCollection` インスタンスを構成するすべてのインスタンスが許容されるインスタンスである必要があります。</span><span class="sxs-lookup"><span data-stu-id="94f47-107">For a `GeometryCollection` instance to be accepted, it must either be an empty `GeometryCollection` instance or all the instances comprising the `GeometryCollection` instance must be accepted instances.</span></span> <span data-ttu-id="94f47-108">次の例に、許容されるインスタンスを示します。</span><span class="sxs-lookup"><span data-stu-id="94f47-108">The following example shows accepted instances.</span></span>  
  
```  
DECLARE @g1 geometry = 'GEOMETRYCOLLECTION EMPTY';  
DECLARE @g2 geometry = 'GEOMETRYCOLLECTION(LINESTRING EMPTY,POLYGON((-1 -1, -1 -5, -5 -5, -5 -1, -1 -1)))';  
DECLARE @g3 geometry = 'GEOMETRYCOLLECTION(LINESTRING(1 1, 3 5),POLYGON((-1 -1, -1 -5, -5 -5, -5 -1, -1 -1)))';  
```  
  
 <span data-ttu-id="94f47-109">次の例では、`LinesString` インスタンス内の `GeometryCollection` インスタンスが許容されないため、`System.FormatException` がスローされます。</span><span class="sxs-lookup"><span data-stu-id="94f47-109">The following example throws a `System.FormatException` because the `LinesString` instance in the `GeometryCollection` instance is not accepted.</span></span>  
  
```  
DECLARE @g geometry = 'GEOMETRYCOLLECTION(LINESTRING(1 1), POLYGON((-1 -1, -1 -5, -5 -5, -5 -1, -1 -1)))';  
```  
  
### <a name="valid-instances"></a><span data-ttu-id="94f47-110">有効なインスタンス</span><span class="sxs-lookup"><span data-stu-id="94f47-110">Valid Instances</span></span>  
 <span data-ttu-id="94f47-111">`GeometryCollection` インスタンスを構成するすべてのインスタンスが有効である場合、`GeometryCollection` インスタンスは有効です。</span><span class="sxs-lookup"><span data-stu-id="94f47-111">A `GeometryCollection` instance is valid when all instances that comprise the `GeometryCollection` instance are valid.</span></span> <span data-ttu-id="94f47-112">次の例に、3 つの有効な `GeometryCollection` インスタンスと 1 つの無効な インスタンスを示します。</span><span class="sxs-lookup"><span data-stu-id="94f47-112">The following shows three valid `GeometryCollection` instances and one instance that is not valid.</span></span>  
  
```  
DECLARE @g1 geometry = 'GEOMETRYCOLLECTION EMPTY';  
DECLARE @g2 geometry = 'GEOMETRYCOLLECTION(LINESTRING EMPTY,POLYGON((-1 -1, -1 -5, -5 -5, -5 -1, -1 -1)))';  
DECLARE @g3 geometry = 'GEOMETRYCOLLECTION(LINESTRING(1 1, 3 5),POLYGON((-1 -1, -1 -5, -5 -5, -5 -1, -1 -1)))';  
DECLARE @g4 geometry = 'GEOMETRYCOLLECTION(LINESTRING(1 1, 3 5),POLYGON((-1 -1, 1 -5, -5 5, -5 -1, -1 -1)))';  
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid(), @g4.STIsValid();  
```  
  
 <span data-ttu-id="94f47-113">`@g4` は、`Polygon` 内の `GeometryCollection` インスタンスが有効ではないため、有効ではありません。</span><span class="sxs-lookup"><span data-stu-id="94f47-113">`@g4` is not valid because the `Polygon` instance in the `GeometryCollection` instance is not valid.</span></span>  
  
 <span data-ttu-id="94f47-114">受け取られる有効なインスタンスについては、 [Point](point.md)、 [MultiPoint](multipoint.md)、 [LineString](linestring.md)、 [MultiLineString](multilinestring.md)、 [Polygon](polygon.md)、 [MultiPolygon](multipolygon.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="94f47-114">For more information on accepted and valid instances, see [Point](point.md), [MultiPoint](multipoint.md), [LineString](linestring.md), [MultiLineString](multilinestring.md), [Polygon](polygon.md), and [MultiPolygon](multipolygon.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="94f47-115">例</span><span class="sxs-lookup"><span data-stu-id="94f47-115">Examples</span></span>  
 <span data-ttu-id="94f47-116">`geometry``GeometryCollection` を、 `Point` インスタンスと `Polygon` インスタンスを含む SRID 1 の Z 値でインスタンス化する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="94f47-116">The following example instantiates a `geometry``GeometryCollection` with Z values in SRID 1 containing a `Point` instance and a `Polygon` instance.</span></span>  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomCollFromText('GEOMETRYCOLLECTION(POINT(3 3 1), POLYGON((0 0 2, 1 10 3, 1 0 4, 0 0 2)))', 1);  
```  
  
## <a name="see-also"></a><span data-ttu-id="94f47-117">参照</span><span class="sxs-lookup"><span data-stu-id="94f47-117">See Also</span></span>  
 [<span data-ttu-id="94f47-118">空間データ &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="94f47-118">Spatial Data &#40;SQL Server&#41;</span></span>](spatial-data-sql-server.md)  
  
  
