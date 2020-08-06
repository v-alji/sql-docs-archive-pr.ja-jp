---
title: 空間データ (SQL Server) | Microsoft Docs
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- geography data type [SQL Server], spatial storage design
- planar spatial data [SQL Server], designing
- spatial data types [SQL Server]
- geodetic spatial data [SQL Server]
- geometry data type [SQL Server], spatial storage design
- spatial storage [SQL Server]
- geodetic spatial data [SQL Server], designing
ms.assetid: 41a132a1-09e2-4426-b9df-225270cb8e15
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 4d491420a9eca7c35b89b254a03381c6467c834c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644916"
---
# <a name="spatial-data-sql-server"></a><span data-ttu-id="ad871-102">空間データ (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="ad871-102">Spatial Data (SQL Server)</span></span>
  <span data-ttu-id="ad871-103">空間データは、幾何学的オブジェクトの物理的な場所と形状に関する情報を表します。</span><span class="sxs-lookup"><span data-stu-id="ad871-103">Spatial data represents information about the physical location and shape of geometric objects.</span></span> <span data-ttu-id="ad871-104">これらのオブジェクトは、ポイントの場所や、国、道路、湖などのより複雑なオブジェクトである可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ad871-104">These objects can be point locations or more complex objects such as countries, roads, or lakes.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="ad871-105">では、`geometry` と `geography` の 2 つの空間データ型がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="ad871-105">supports two spatial data types: the `geometry` data type and the `geography` data type.</span></span>  
  
-   <span data-ttu-id="ad871-106">`geometry` 型は、ユークリッド (平面) 座標系のデータを表します。</span><span class="sxs-lookup"><span data-stu-id="ad871-106">The `geometry` type represents data in a Euclidean (flat) coordinate system.</span></span>  
  
-   <span data-ttu-id="ad871-107">`geography` 型は、球体地球座標系のデータを表します。</span><span class="sxs-lookup"><span data-stu-id="ad871-107">The `geography` type represents data in a round-earth coordinate system.</span></span>  
  
 <span data-ttu-id="ad871-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]では、どちらのデータ型も .NET 共通言語ランタイム (CLR) のデータ型として実装されています。</span><span class="sxs-lookup"><span data-stu-id="ad871-108">Both data types are implemented as .NET common language runtime (CLR) data types in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="ad871-109">[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]で導入された空間機能の詳細な説明とサンプルについては、ホワイト ペーパー「 [New Spatial Features in SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=226407)」 (SQL Server 2012 の新しい空間機能) をダウンロードして参照してください。</span><span class="sxs-lookup"><span data-stu-id="ad871-109">For a detailed description and examples of spatial features introduced in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], download the white paper, [New Spatial Features in SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=226407).</span></span>  
  
##  <a name="related-tasks"></a><a name="reltasks"></a> <span data-ttu-id="ad871-110">関連タスク</span><span class="sxs-lookup"><span data-stu-id="ad871-110">Related Tasks</span></span>  
 [<span data-ttu-id="ad871-111">geometry インスタンスの作成、構築、およびクエリ</span><span class="sxs-lookup"><span data-stu-id="ad871-111">Create, Construct, and Query geometry Instances</span></span>](create-construct-and-query-geometry-instances.md)  
 <span data-ttu-id="ad871-112">geometry データ型のインスタンスで使用できるメソッドについて説明します。</span><span class="sxs-lookup"><span data-stu-id="ad871-112">Describes the methods that you can use with instances of the geometry data type.</span></span>  
  
 [<span data-ttu-id="ad871-113">geography インスタンスの作成、構築、およびクエリ</span><span class="sxs-lookup"><span data-stu-id="ad871-113">Create, Construct, and Query geography Instances</span></span>](create-construct-and-query-geography-instances.md)  
 <span data-ttu-id="ad871-114">geography データ型のインスタンスで使用できるメソッドについて説明します。</span><span class="sxs-lookup"><span data-stu-id="ad871-114">Describes the methods that you can use with instances of the geography data type.</span></span>  
  
 [<span data-ttu-id="ad871-115">空間データに対するニアレスト ネイバーのクエリ</span><span class="sxs-lookup"><span data-stu-id="ad871-115">Query Spatial Data for Nearest Neighbor</span></span>](query-spatial-data-for-nearest-neighbor.md)  
 <span data-ttu-id="ad871-116">特定の空間オブジェクトに最も近い空間オブジェクトを検索するための一般的なクエリ パターンについて説明します。</span><span class="sxs-lookup"><span data-stu-id="ad871-116">Describes the common query pattern that is used to find the closest spatial objects to a specific spatial object.</span></span>  
  
 [<span data-ttu-id="ad871-117">空間インデックスの作成、変更、および削除</span><span class="sxs-lookup"><span data-stu-id="ad871-117">Create, Modify, and Drop Spatial Indexes</span></span>](create-modify-and-drop-spatial-indexes.md)  
 <span data-ttu-id="ad871-118">空間インデックスの作成、変更、および削除に関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="ad871-118">Provides information about creating, altering, and dropping a spatial index.</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="ad871-119">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="ad871-119">Related Content</span></span>  
 [<span data-ttu-id="ad871-120">空間データ型の概要</span><span class="sxs-lookup"><span data-stu-id="ad871-120">Spatial Data Types Overview</span></span>](spatial-data-types-overview.md)  
 <span data-ttu-id="ad871-121">空間データ型について説明します。</span><span class="sxs-lookup"><span data-stu-id="ad871-121">Introduces the spatial data types.</span></span>  
  
-   [<span data-ttu-id="ad871-122">Point</span><span class="sxs-lookup"><span data-stu-id="ad871-122">Point</span></span>](point.md)  
  
-   [<span data-ttu-id="ad871-123">LineString</span><span class="sxs-lookup"><span data-stu-id="ad871-123">LineString</span></span>](linestring.md)  
  
-   [<span data-ttu-id="ad871-124">CircularString</span><span class="sxs-lookup"><span data-stu-id="ad871-124">CircularString</span></span>](circularstring.md)  
  
-   [<span data-ttu-id="ad871-125">CompoundCurve</span><span class="sxs-lookup"><span data-stu-id="ad871-125">CompoundCurve</span></span>](compoundcurve.md)  
  
-   [<span data-ttu-id="ad871-126">Polygon</span><span class="sxs-lookup"><span data-stu-id="ad871-126">Polygon</span></span>](polygon.md)  
  
-   [<span data-ttu-id="ad871-127">CurvePolygon</span><span class="sxs-lookup"><span data-stu-id="ad871-127">CurvePolygon</span></span>](curvepolygon.md)  
  
-   [<span data-ttu-id="ad871-128">MultiPoint</span><span class="sxs-lookup"><span data-stu-id="ad871-128">MultiPoint</span></span>](multipoint.md)  
  
-   [<span data-ttu-id="ad871-129">MultiLineString</span><span class="sxs-lookup"><span data-stu-id="ad871-129">MultiLineString</span></span>](multilinestring.md)  
  
-   [<span data-ttu-id="ad871-130">MultiPolygon</span><span class="sxs-lookup"><span data-stu-id="ad871-130">MultiPolygon</span></span>](multipolygon.md)  
  
-   [<span data-ttu-id="ad871-131">GeometryCollection</span><span class="sxs-lookup"><span data-stu-id="ad871-131">GeometryCollection</span></span>](geometrycollection.md)  
  
 [<span data-ttu-id="ad871-132">空間インデックスの概要</span><span class="sxs-lookup"><span data-stu-id="ad871-132">Spatial Indexes Overview</span></span>](spatial-indexes-overview.md)  
 <span data-ttu-id="ad871-133">空間インデックス、テセレーション、テセレーション スキームについて説明します。</span><span class="sxs-lookup"><span data-stu-id="ad871-133">Introduces spatial indexes and describes tessellation and tessellation schemes.</span></span>  
  
  
