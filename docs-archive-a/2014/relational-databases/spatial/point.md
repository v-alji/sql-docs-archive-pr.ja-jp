---
title: ポイント | Microsoft Docs
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Point geometry subtype [SQL Server]
- geometry data type [SQL Server], spatial data
ms.assetid: 2a596ec4-8b2f-4962-bcb4-e5c8f77edad5
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 4b12069d84e00738e3ddac8c414f33903f4f0999
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644921"
---
# <a name="point"></a><span data-ttu-id="bd114-102">ポイント</span><span class="sxs-lookup"><span data-stu-id="bd114-102">Point</span></span>
  <span data-ttu-id="bd114-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 空間データの `Point` は、1 つの場所を表す 0 次元のオブジェクトです。 には、Z (昇格) 値と M (メジャー) 値が含まれる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="bd114-103">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] spatial data, a `Point` is a 0-dimensional object representing a single location and may contain Z (elevation) and M (measure) values.</span></span>  
  
## <a name="geography-data-type"></a><span data-ttu-id="bd114-104">geography データ型</span><span class="sxs-lookup"><span data-stu-id="bd114-104">Geography Data Type</span></span>  
 <span data-ttu-id="bd114-105">geography データ型の Point 型は、 *Lat* が緯度、 *Long* が経度を表している 1 つの場所を表します。</span><span class="sxs-lookup"><span data-stu-id="bd114-105">The Point type for the geography data type represents a single location where *Lat* represents latitude and *Long* represents longitude.</span></span> <span data-ttu-id="bd114-106">緯度と経度の値は度数で測定されます。</span><span class="sxs-lookup"><span data-stu-id="bd114-106">The values for latitude and longitude are measured in degrees.</span></span> <span data-ttu-id="bd114-107">緯度の値は、常に [-90, 90] の範囲内になります。この範囲外の値が入力されると、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="bd114-107">Values for latitude always lie in the interval [-90, 90], and values that are inputted outside this range will throw an exception.</span></span> <span data-ttu-id="bd114-108">経度の値は、常に [-180, 180] の範囲内になります。この範囲外の入力値は、この範囲に収まるように調整されます。</span><span class="sxs-lookup"><span data-stu-id="bd114-108">Values for longitude always lie in the interval (-180, 180], and values inputted outside this range are wrapped around to fit in this range.</span></span> <span data-ttu-id="bd114-109">たとえば、経度の値として 190 を入力した場合は、値 -170 に調整されます。</span><span class="sxs-lookup"><span data-stu-id="bd114-109">For example, if 190 is inputted for longitude, then it will be wrapped to the value -170.</span></span> <span data-ttu-id="bd114-110">*SRID* は、返される **geography** インスタンスの空間参照 ID を表します。</span><span class="sxs-lookup"><span data-stu-id="bd114-110">*SRID* represents the spatial reference ID of the **geography** instance that you wish to return.</span></span>  
  
## <a name="geometry-data-type"></a><span data-ttu-id="bd114-111">geometry データ型</span><span class="sxs-lookup"><span data-stu-id="bd114-111">Geometry Data Type</span></span>  
 <span data-ttu-id="bd114-112">geometry データ型の Point 型は、 *X* が生成される Point の X 座標、 *Y* が生成される Point の Y 座標を表している 1 つの場所を表します。</span><span class="sxs-lookup"><span data-stu-id="bd114-112">The Point type for the geometry data type represents a single location where *X* represents the X-coordinate of the Point being generated and *Y* represents the Y-coordinate of the Point being generated.</span></span> <span data-ttu-id="bd114-113">*SRID* は、返される **geometry** インスタンスの空間参照 ID を表します。</span><span class="sxs-lookup"><span data-stu-id="bd114-113">*SRID* represents the spatial reference ID of the **geometry** instance that you wish to return.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="bd114-114">例</span><span class="sxs-lookup"><span data-stu-id="bd114-114">Examples</span></span>  
 <span data-ttu-id="bd114-115">次の例では、点 (3, 4) を表す `geometry Point`インスタンスを作成します。このインスタンスの SRID は 0 です。</span><span class="sxs-lookup"><span data-stu-id="bd114-115">The following example creates a `geometry Point`instance representing the point (3, 4) with an SRID of 0.</span></span>  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('POINT (3 4)', 0);  
```  
  
 <span data-ttu-id="bd114-116">次の例では、SRID が 0 (既定)、Z (昇格) 値が 7、M (メジャー) 値が 2.5 の、点 (3, 4) を表す `geometry``Point` インスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="bd114-116">The next example creates a `geometry``Point` instance representing the point (3, 4) with a Z (elevation) value of 7, an M (measure) value of 2.5, and the default SRID of 0.</span></span>  
  
```  
DECLARE @g geometry;  
SET @g = geometry::Parse('POINT(3 4 7 2.5)');  
```  
  
 <span data-ttu-id="bd114-117">最後の例では、 `geometry``Point` インスタンスの X、Y、Z、および M の値を返します。</span><span class="sxs-lookup"><span data-stu-id="bd114-117">The final example returns the X, Y, Z, and M values for the `geometry``Point` instance.</span></span>  
  
```  
SELECT @g.STX;  
SELECT @g.STY;  
SELECT @g.Z;  
SELECT @g.M;  
```  
  
 <span data-ttu-id="bd114-118">Z と M の値は、次の例のように明示的に NULL として指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="bd114-118">Z and M values may be explicitly specified as NULL, as shown in the following example.</span></span>  
  
```  
DECLARE @g geometry;  
SET @g = geometry::Parse('POINT(3 4 NULL NULL)');  
```  
  
## <a name="see-also"></a><span data-ttu-id="bd114-119">参照</span><span class="sxs-lookup"><span data-stu-id="bd114-119">See Also</span></span>  
 <span data-ttu-id="bd114-120">[MultiPoint](multipoint.md) </span><span class="sxs-lookup"><span data-stu-id="bd114-120">[MultiPoint](multipoint.md) </span></span>  
 <span data-ttu-id="bd114-121">[STX &#40;geometry データ型&#41;](/sql/t-sql/spatial-geometry/stx-geometry-data-type) </span><span class="sxs-lookup"><span data-stu-id="bd114-121">[STX &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stx-geometry-data-type) </span></span>  
 <span data-ttu-id="bd114-122">[STY &#40;geometry データ型&#41;](/sql/t-sql/spatial-geometry/sty-geometry-data-type) </span><span class="sxs-lookup"><span data-stu-id="bd114-122">[STY &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/sty-geometry-data-type) </span></span>  
 [<span data-ttu-id="bd114-123">空間データ &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="bd114-123">Spatial Data &#40;SQL Server&#41;</span></span>](spatial-data-sql-server.md)  
  
  
