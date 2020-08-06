---
title: geometry インスタンスの作成、構築、およびクエリ | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- planar spatial data [SQL Server], getting started
- geometry data type [SQL Server], getting started
ms.assetid: c6b5c852-37d2-48d0-a8ad-e43bb80d6514
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 539f3f8bb1d9a1c277d6317cc571cf8bcb281833
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632315"
---
# <a name="create-construct-and-query-geometry-instances"></a><span data-ttu-id="01673-102">geometry インスタンスの作成、構築、およびクエリ</span><span class="sxs-lookup"><span data-stu-id="01673-102">Create, Construct, and Query geometry Instances</span></span>
  <span data-ttu-id="01673-103">平面空間データ型の `geometry` は、ユークリッド (平面) 座標系のデータを表します。</span><span class="sxs-lookup"><span data-stu-id="01673-103">The planar spatial data type, `geometry`, represents data in a Euclidean (flat) coordinate system.</span></span> <span data-ttu-id="01673-104">この型は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]では共通言語ランタイム (CLR) のデータ型として実装されています。</span><span class="sxs-lookup"><span data-stu-id="01673-104">This type is implemented as a common language runtime (CLR) data type in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="01673-105">`geometry` 型は、各データベースで使用できるように事前に定義されています。</span><span class="sxs-lookup"><span data-stu-id="01673-105">The `geometry` type is predefined and available in each database.</span></span> <span data-ttu-id="01673-106">型のテーブル列 `geometry` を作成し、 `geometry` 他の CLR 型を使用する場合と同じ方法でデータを操作できます。</span><span class="sxs-lookup"><span data-stu-id="01673-106">You can create table columns of type `geometry` and operate on `geometry` data in the same manner as you would use other CLR types.</span></span>  
  
 <span data-ttu-id="01673-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によってサポートされている `geometry` データ型 (平面) は、Open Geospatial Consortium (OGC) Simple Features for SQL Specification version 1.1.0 に準拠しています。</span><span class="sxs-lookup"><span data-stu-id="01673-107">The `geometry` data type (planar) supported by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] conforms to the Open Geospatial Consortium (OGC) Simple Features for SQL Specification version 1.1.0.</span></span>  
  
 <span data-ttu-id="01673-108">OGC の仕様の詳細については、以下を参照してください。</span><span class="sxs-lookup"><span data-stu-id="01673-108">For more information on OGC specifications, see the following:</span></span>  
  
-   [<span data-ttu-id="01673-109">OGC の仕様、簡易機能アクセス Part 1 - 共通アーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="01673-109">OGC Specifications, Simple Feature Access Part 1 - Common Architecture</span></span>](https://go.microsoft.com/fwlink/?LinkId=93628)  
  
-   [<span data-ttu-id="01673-110">OGC の仕様、簡易機能アクセス Part 2 - SQL オプション</span><span class="sxs-lookup"><span data-stu-id="01673-110">OGC Specifications, Simple Feature Access Part 2 - SQL Options</span></span>](https://go.microsoft.com/fwlink/?LinkId=93629)  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="01673-111">は、次のスキーマで定義されている既存の GML 3.1 標準のサブセットをサポートしています: [https://schemas.microsoft.com/sqlserver/profiles/gml/SpatialGML.xsd](https://go.microsoft.com/fwlink/?LinkId=230959)。</span><span class="sxs-lookup"><span data-stu-id="01673-111">supports a subset of the existing GML 3.1 standard which is defined in the following schema: [https://schemas.microsoft.com/sqlserver/profiles/gml/SpatialGML.xsd](https://go.microsoft.com/fwlink/?LinkId=230959).</span></span>  
  
##  <a name="creating-or-constructing-a-new-geometry-instance"></a><a name="creating"></a> <span data-ttu-id="01673-112">新しい geometry インスタンスの作成または構築</span><span class="sxs-lookup"><span data-stu-id="01673-112">Creating or constructing a new geometry instance</span></span>  
  
###  <a name="creating-a-new-geometry-instance-from-an-existing-instance"></a><a name="existing"></a> <span data-ttu-id="01673-113">既存のインスタンスからの新しい geometry インスタンスの作成</span><span class="sxs-lookup"><span data-stu-id="01673-113">Creating a New geometry Instance from an Existing Instance</span></span>  
 <span data-ttu-id="01673-114">`geometry` データ型には、既存のインスタンスに基づいて新しい `geometry` インスタンスを作成するために使用できる組み込みメソッドが数多く用意されています。</span><span class="sxs-lookup"><span data-stu-id="01673-114">The `geometry` data type provides numerous built-in methods you can use to create new `geometry` instances based on existing instances.</span></span>  
  
 <span data-ttu-id="01673-115">**geometry の周りにバッファーを作成するには**</span><span class="sxs-lookup"><span data-stu-id="01673-115">**To create a buffer around a geometry**</span></span>  
 [<span data-ttu-id="01673-116">STBuffer &#40;geometry データ型&#41;</span><span class="sxs-lookup"><span data-stu-id="01673-116">STBuffer &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stbuffer-geometry-data-type)  
  
 [<span data-ttu-id="01673-117">BufferWithTolerance &#40;geometry データ型&#41;</span><span class="sxs-lookup"><span data-stu-id="01673-117">BufferWithTolerance &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/bufferwithtolerance-geometry-data-type)  
  
 <span data-ttu-id="01673-118">**簡素化されたバージョンの geometry を作成するには**</span><span class="sxs-lookup"><span data-stu-id="01673-118">**To create a simplified version of a geometry**</span></span>  
 [<span data-ttu-id="01673-119">Reduce &#40;geometry データ型&#41;</span><span class="sxs-lookup"><span data-stu-id="01673-119">Reduce &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/reduce-geometry-data-type)  
  
 <span data-ttu-id="01673-120">**geometry の凸包を作成するには**</span><span class="sxs-lookup"><span data-stu-id="01673-120">**To create the convex hull of a geometry**</span></span>  
 [<span data-ttu-id="01673-121">STConvexHull &#40;geometry データ型&#41;</span><span class="sxs-lookup"><span data-stu-id="01673-121">STConvexHull &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stconvexhull-geometry-data-type)  
  
 <span data-ttu-id="01673-122">**2 つの geometry の積集合から geometry を作成するには**</span><span class="sxs-lookup"><span data-stu-id="01673-122">**To create a geometry from the intersection of two geometries**</span></span>  
 [<span data-ttu-id="01673-123">STIntersection &#40;geometry データ型&#41;</span><span class="sxs-lookup"><span data-stu-id="01673-123">STIntersection &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stintersection-geometry-data-type)  
  
 <span data-ttu-id="01673-124">**2 つの geometry の和集合から geometry を作成するには**</span><span class="sxs-lookup"><span data-stu-id="01673-124">**To create a geometry from the union of two geometries**</span></span>  
 [<span data-ttu-id="01673-125">STUnion &#40;geometry データ型&#41;</span><span class="sxs-lookup"><span data-stu-id="01673-125">STUnion &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stunion-geometry-data-type)  
  
 <span data-ttu-id="01673-126">**一方の geometry の、もう一方の geometry と重なる部分を除いた点から geometry を作成するには**</span><span class="sxs-lookup"><span data-stu-id="01673-126">**To create a geometry from the points where one geometry does not overlap another**</span></span>  
 [<span data-ttu-id="01673-127">STDifference &#40;geometry データ型&#41;</span><span class="sxs-lookup"><span data-stu-id="01673-127">STDifference &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stdifference-geometry-data-type)  
  
 <span data-ttu-id="01673-128">**2 つの geometry の重なる部分を除いた点から geometry を作成するには**</span><span class="sxs-lookup"><span data-stu-id="01673-128">**To create a geometry from the points where two geometries do not overlap**</span></span>  
 [<span data-ttu-id="01673-129">STSymDifference &#40;geometry データ型&#41;</span><span class="sxs-lookup"><span data-stu-id="01673-129">STSymDifference &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stsymdifference-geometry-data-type)  
  
 <span data-ttu-id="01673-130">**既存の geometry 上にある任意の Point インスタンスを作成するには**</span><span class="sxs-lookup"><span data-stu-id="01673-130">**To create an arbitrary Point instance that lies on an existing geometry**</span></span>  
 [<span data-ttu-id="01673-131">STPointOnSurface &#40;geometry データ型&#41;</span><span class="sxs-lookup"><span data-stu-id="01673-131">STPointOnSurface &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stpointonsurface-geometry-data-type)  
  
  
  
###  <a name="constructing-a-geometry-instance-from-well-known-text-input"></a><a name="wkt"></a> <span data-ttu-id="01673-132">Well-Known Text 入力からの geometry インスタンスの構築</span><span class="sxs-lookup"><span data-stu-id="01673-132">Constructing a geometry Instance from Well-Known Text Input</span></span>  
 <span data-ttu-id="01673-133">`geometry` データ型には、Open Geospatial Consortium (OGC) WKT 表現からジオメトリを生成する組み込みのメソッドが数多く用意されています。</span><span class="sxs-lookup"><span data-stu-id="01673-133">The `geometry` data type provides several built-in methods that generate a geometry from the Open Geospatial Consortium (OGC) WKT representation.</span></span> <span data-ttu-id="01673-134">WKT 標準は geometry データをテキスト形式で交換できるテキスト文字列です。</span><span class="sxs-lookup"><span data-stu-id="01673-134">The WKT standard is a text string that allows geometry data to be exchanged in textual form.</span></span>  
  
 <span data-ttu-id="01673-135">**WKT 入力から任意の型の geometry インスタンスを構築するには**</span><span class="sxs-lookup"><span data-stu-id="01673-135">**To construct any type of geometry instance from WKT input**</span></span>  
 [<span data-ttu-id="01673-136">STGeomFromText#40;geometry データ型&#41;</span><span class="sxs-lookup"><span data-stu-id="01673-136">STGeomFromText &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stgeomfromtext-geometry-data-type)  
  
 [<span data-ttu-id="01673-137">Parse &#40;geometry データ型&#41;</span><span class="sxs-lookup"><span data-stu-id="01673-137">Parse &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/parse-geometry-data-type)  
  
 <span data-ttu-id="01673-138">**WKT 入力から geometry Point インスタンスを構築するには**</span><span class="sxs-lookup"><span data-stu-id="01673-138">**To construct a geometry Point instance from WKT input**</span></span>  
 [<span data-ttu-id="01673-139">STPointFromText &#40;geometry データ型&#41;</span><span class="sxs-lookup"><span data-stu-id="01673-139">STPointFromText &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stpointfromtext-geometry-data-type)  
  
 <span data-ttu-id="01673-140">**WKT 入力から geometry MultiPoint インスタンスを構築するには**</span><span class="sxs-lookup"><span data-stu-id="01673-140">**To construct a geometry MultiPoint instance from WKT input**</span></span>  
 [<span data-ttu-id="01673-141">STMPointFromText &#40;geometry データ型&#41;</span><span class="sxs-lookup"><span data-stu-id="01673-141">STMPointFromText &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stmpointfromtext-geometry-data-type)  
  
 <span data-ttu-id="01673-142">**WKT 入力から geometry LineString インスタンスを構築するには**</span><span class="sxs-lookup"><span data-stu-id="01673-142">**To construct a geometry LineString instance from WKT input**</span></span>  
 [<span data-ttu-id="01673-143">STLineFromText &#40;geometry データ型&#41;</span><span class="sxs-lookup"><span data-stu-id="01673-143">STLineFromText &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stlinefromtext-geometry-data-type)  
  
 <span data-ttu-id="01673-144">**WKT 入力から geometry MultiLineString インスタンスを構築するには**</span><span class="sxs-lookup"><span data-stu-id="01673-144">**To construct a geometry MultiLineString instance from WKT input**</span></span>  
 [<span data-ttu-id="01673-145">STMLineFromText &#40;geometry データ型&#41;</span><span class="sxs-lookup"><span data-stu-id="01673-145">STMLineFromText &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stmlinefromtext-geometry-data-type)  
  
 <span data-ttu-id="01673-146">**WKT 入力から geometry Polygon インスタンスを構築するには**</span><span class="sxs-lookup"><span data-stu-id="01673-146">**To construct a geometry Polygon instance from WKT input**</span></span>  
 [<span data-ttu-id="01673-147">STPolyFromText &#40;geometry データ型&#41;</span><span class="sxs-lookup"><span data-stu-id="01673-147">STPolyFromText &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stpolyfromtext-geometry-data-type)  
  
 <span data-ttu-id="01673-148">**WKT 入力から geometry MultiPolygon インスタンスを構築するには**</span><span class="sxs-lookup"><span data-stu-id="01673-148">**To construct a geometry MultiPolygon instance from WKT input**</span></span>  
 [<span data-ttu-id="01673-149">STMPolyFromText &#40;geometry データ型&#41;</span><span class="sxs-lookup"><span data-stu-id="01673-149">STMPolyFromText &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stmpolyfromtext-geometry-data-type)  
  
 <span data-ttu-id="01673-150">**WKT 入力から geometry GeometryCollection インスタンスを構築するには**</span><span class="sxs-lookup"><span data-stu-id="01673-150">**To construct a geometry GeometryCollection instance from WKT input**</span></span>  
 [<span data-ttu-id="01673-151">TGeomCollFromText &#40;geometry データ型&#41;</span><span class="sxs-lookup"><span data-stu-id="01673-151">STGeomCollFromText &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stgeomcollfromtext-geometry-data-type)  
  
  
  
###  <a name="constructing-a-geometry-instance-from-well-known-binary-input"></a><a name="wkb"></a> <span data-ttu-id="01673-152">Well-Known Binary 入力からの geometry インスタンスの構築</span><span class="sxs-lookup"><span data-stu-id="01673-152">Constructing a geometry Instance from Well-Known Binary Input</span></span>  
 <span data-ttu-id="01673-153">WKB は、`geometry` データをアプリケーションと SQL データベース間で交換することができる、Open Geospatial Consortium (OGC) で指定されたバイナリ形式です。</span><span class="sxs-lookup"><span data-stu-id="01673-153">WKB is a binary format specified by the Open Geospatial Consortium (OGC) that permits `geometry` data to be exchanged between a client application and an SQL database.</span></span> <span data-ttu-id="01673-154">次の関数は、WKB 入力を受け入れてジオメトリを構築します。</span><span class="sxs-lookup"><span data-stu-id="01673-154">The following functions accept WKB input to construct geometries:</span></span>  
  
 <span data-ttu-id="01673-155">**WKB 入力から任意の型の geometry インスタンスを構築するには**</span><span class="sxs-lookup"><span data-stu-id="01673-155">**To construct any type of geometry instance from WKB input**</span></span>  
 [<span data-ttu-id="01673-156">STGeomFromWKB &#40;geometry データ型&#41;</span><span class="sxs-lookup"><span data-stu-id="01673-156">STGeomFromWKB &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stgeomfromwkb-geometry-data-type)  
  
 <span data-ttu-id="01673-157">**WKB 入力から geometry Point インスタンスを構築するには**</span><span class="sxs-lookup"><span data-stu-id="01673-157">**To construct a geometry Point instance from WKB input**</span></span>  
 [<span data-ttu-id="01673-158">STPointFromWKB &#40;geometry データ型e&#41;</span><span class="sxs-lookup"><span data-stu-id="01673-158">STPointFromWKB &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stpointfromwkb-geometry-data-type)  
  
 <span data-ttu-id="01673-159">**WKB 入力から geometry MultiPoint インスタンスを構築するには**</span><span class="sxs-lookup"><span data-stu-id="01673-159">**To construct a geometry MultiPoint instance from WKB input**</span></span>  
 [<span data-ttu-id="01673-160">STMPointFromWKB &#40;geometry データ型&#41;</span><span class="sxs-lookup"><span data-stu-id="01673-160">STMPointFromWKB &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stmpointfromwkb-geometry-data-type)  
  
 <span data-ttu-id="01673-161">**WKB 入力から geometry LineString インスタンスを構築するには**</span><span class="sxs-lookup"><span data-stu-id="01673-161">**To construct a geometry LineString instance from WKB input**</span></span>  
 [<span data-ttu-id="01673-162">STLineFromWKB &#40;geometry データ型&#41;</span><span class="sxs-lookup"><span data-stu-id="01673-162">STLineFromWKB &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stlinefromwkb-geometry-data-type)  
  
 <span data-ttu-id="01673-163">**WKB 入力から geometry MultiLineString インスタンスを構築するには**</span><span class="sxs-lookup"><span data-stu-id="01673-163">**To construct a geometry MultiLineString instance from WKB input**</span></span>  
 [<span data-ttu-id="01673-164">STMLineFromWKB &#40;geometry データ型&#41;</span><span class="sxs-lookup"><span data-stu-id="01673-164">STMLineFromWKB &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stmlinefromwkb-geometry-data-type)  
  
 <span data-ttu-id="01673-165">**WKB 入力から geometry Polygon インスタンスを構築するには**</span><span class="sxs-lookup"><span data-stu-id="01673-165">**To construct a geometry Polygon instance from WKB input**</span></span>  
 [<span data-ttu-id="01673-166">STPolyFromWKB &#40;geometry データ型&#41;</span><span class="sxs-lookup"><span data-stu-id="01673-166">STPolyFromWKB &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stpolyfromwkb-geometry-data-type)  
  
 <span data-ttu-id="01673-167">**WKB 入力から geometry MultiPolygon インスタンスを構築するには**</span><span class="sxs-lookup"><span data-stu-id="01673-167">**To construct a geometry MultiPolygon instance from WKB input**</span></span>  
 [<span data-ttu-id="01673-168">STMPolyFromWKB &#40;geometry データ型&#41;</span><span class="sxs-lookup"><span data-stu-id="01673-168">STMPolyFromWKB &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stmpolyfromwkb-geometry-data-type)  
  
 <span data-ttu-id="01673-169">**WKB 入力から geometry GeometryCollection インスタンスを構築するには**</span><span class="sxs-lookup"><span data-stu-id="01673-169">**To construct a geometry GeometryCollection instance from WKB input**</span></span>  
 [<span data-ttu-id="01673-170">STGeomCollFromWKB &#40;geometry データ型&#41;</span><span class="sxs-lookup"><span data-stu-id="01673-170">STGeomCollFromWKB &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stgeomcollfromwkb-geometry-data-type)  
  
  
  
###  <a name="constructing-a-geometry-instance-from-gml-text-input"></a><a name="gml"></a> <span data-ttu-id="01673-171">GML Text 入力からの geometry インスタンスの構築</span><span class="sxs-lookup"><span data-stu-id="01673-171">Constructing a geometry Instance from GML Text Input</span></span>  
 <span data-ttu-id="01673-172">データ型には、 `geometry` `geometry` GML (ジオメトリックオブジェクトの XML 表現) からインスタンスを生成するメソッドが用意されています。</span><span class="sxs-lookup"><span data-stu-id="01673-172">The `geometry` data type provides a method that generates a `geometry` instance from GML, an XML representation of geometric objects.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="01673-173">では、GML のサブセットをサポートします。</span><span class="sxs-lookup"><span data-stu-id="01673-173">supports a subset of GML.</span></span>  
  
 <span data-ttu-id="01673-174">**GML 入力から任意の型の geometry インスタンスを構築するには**</span><span class="sxs-lookup"><span data-stu-id="01673-174">**To construct any type of geometry instance from GML input**</span></span>  
 [<span data-ttu-id="01673-175">GeomFromGml &#40;geometry データ型&#41;</span><span class="sxs-lookup"><span data-stu-id="01673-175">GeomFromGml &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/geomfromgml-geometry-data-type)  
  
  
  
##  <a name="returning-well-known-text-and-well-known-binary-from-a-geometry-instance"></a><a name="returning"></a> <span data-ttu-id="01673-176">geometry インスタンスからの Well-Known Text および Well-Known Binary の取得</span><span class="sxs-lookup"><span data-stu-id="01673-176">Returning Well-Known Text and Well-Known Binary from a geometry Instance</span></span>  
 <span data-ttu-id="01673-177">次のメソッドを使用して、`geometry` インスタンスの WKT 形式または WKB 形式のいずれかを取得できます。</span><span class="sxs-lookup"><span data-stu-id="01673-177">You can use the following methods to return either the WKT or WKB format of a `geometry` instance:</span></span>  
  
 <span data-ttu-id="01673-178">**geometry インスタンスの WKT 表現を取得するには**</span><span class="sxs-lookup"><span data-stu-id="01673-178">**To return the WKT representation of a geometry instance**</span></span>  
 [<span data-ttu-id="01673-179">STAsText &#40;geometry データ型&#41;</span><span class="sxs-lookup"><span data-stu-id="01673-179">STAsText &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stastext-geometry-data-type)  
  
 [<span data-ttu-id="01673-180">ToString &#40;geometry データ型&#41;</span><span class="sxs-lookup"><span data-stu-id="01673-180">ToString &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/tostring-geometry-data-type)  
  
 <span data-ttu-id="01673-181">**geometry インスタンスの WKT 表現を Z と M の値も含めて取得するには**</span><span class="sxs-lookup"><span data-stu-id="01673-181">**To return the WKT representation of a geometry instance including any Z and M values**</span></span>  
 [<span data-ttu-id="01673-182">AsTextZM &#40;geometry データ型&#41;</span><span class="sxs-lookup"><span data-stu-id="01673-182">AsTextZM &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/astextzm-geometry-data-type)  
  
 <span data-ttu-id="01673-183">**geometry インスタンスの WKB 表現を取得するには**</span><span class="sxs-lookup"><span data-stu-id="01673-183">**To return the WKB representation of a geometry instance**</span></span>  
 [<span data-ttu-id="01673-184">STAsBinary &#40;geometry データ型&#41;</span><span class="sxs-lookup"><span data-stu-id="01673-184">STAsBinary &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stasbinary-geometry-data-type)  
  
 <span data-ttu-id="01673-185">**geometry インスタンスの GML 表現を取得するには**</span><span class="sxs-lookup"><span data-stu-id="01673-185">**To return a GML representation of a geometry instance**</span></span>  
 [<span data-ttu-id="01673-186">AsGml &#40;geometry データ型&#41;</span><span class="sxs-lookup"><span data-stu-id="01673-186">AsGml &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/asgml-geometry-data-type)  
  
  
  
##  <a name="querying-the-properties-and-behaviors-of-geometry-instances"></a><a name="querying"></a> <span data-ttu-id="01673-187">geometry インスタンスのプロパティと動作のクエリ</span><span class="sxs-lookup"><span data-stu-id="01673-187">Querying the Properties and Behaviors of geometry Instances</span></span>  
 <span data-ttu-id="01673-188">すべて `geometry` のインスタンスには、が提供するメソッドを使用して取得できるいくつかのプロパティがあり [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="01673-188">All `geometry` instances have a number of properties that can be retrieved through methods that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provides.</span></span> <span data-ttu-id="01673-189">以下のトピックでは、geometry 型のプロパティおよび動作と、geometry 型のクエリを実行するためのメソッドについて説明します。</span><span class="sxs-lookup"><span data-stu-id="01673-189">The following topics define the properties and behaviors of geometry types, and the methods for querying each one.</span></span>  
  
###  <a name="validity-instance-type-and-geometrycollection-information"></a><a name="valid"></a> <span data-ttu-id="01673-190">有効性、インスタンスの型、および GeometryCollection 情報</span><span class="sxs-lookup"><span data-stu-id="01673-190">Validity, Instance Type, and GeometryCollection Information</span></span>  
 <span data-ttu-id="01673-191">`geometry` インスタンスを構築したら、次のメソッドを使用して、そのインスタンスが適切な形式であるかどうかを確認したり、インスタンスの型を取得することができます。また、コレクション インスタンスの場合は、特定の `geometry` インスタンスを取得できます。</span><span class="sxs-lookup"><span data-stu-id="01673-191">Once a `geometry` instance is constructed, you can use the following methods to determine if it is well-formed, return the instance type, or, if it is a collection instance, return a specific `geometry` instance.</span></span>  
  
 <span data-ttu-id="01673-192">**geometry のインスタンスの型を取得するには**</span><span class="sxs-lookup"><span data-stu-id="01673-192">**To return the instance type of a geometry**</span></span>  
 [<span data-ttu-id="01673-193">STGeometryType &#40;geometry データ型&#41;</span><span class="sxs-lookup"><span data-stu-id="01673-193">STGeometryType &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stgeometrytype-geometry-data-type)  
  
 <span data-ttu-id="01673-194">**geometry が特定のインスタンスの型であるかどうかを調べるには**</span><span class="sxs-lookup"><span data-stu-id="01673-194">**To determine if a geometry is a given instance type**</span></span>  
 [<span data-ttu-id="01673-195">InstanceOf &#40;geometry データ型&#41;</span><span class="sxs-lookup"><span data-stu-id="01673-195">InstanceOf &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/instanceof-geometry-data-type)  
  
 <span data-ttu-id="01673-196">**geometry インスタンスがそのインスタンスの型に対応する適切な形式であるかどうかを調べるには**</span><span class="sxs-lookup"><span data-stu-id="01673-196">**To determine if a geometry instance is well-formed for its instance type**</span></span>  
 [<span data-ttu-id="01673-197">STIsValid &#40;geometry データ型&#41;</span><span class="sxs-lookup"><span data-stu-id="01673-197">STIsValid &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stisvalid-geometry-data-type)  
  
 <span data-ttu-id="01673-198">**geometry インスタンスをインスタンスの型に対応する適切な形式の geometry インスタンスに変換するには**</span><span class="sxs-lookup"><span data-stu-id="01673-198">**To convert a geometry instance to a well-formed geometry instance with an instance type**</span></span>  
 [<span data-ttu-id="01673-199">MakeValid &#40;geometry データ型&#41;</span><span class="sxs-lookup"><span data-stu-id="01673-199">MakeValid &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/makevalid-geometry-data-type)  
  
 <span data-ttu-id="01673-200">**geometry コレクション インスタンス内のジオメトリの数を取得するには**</span><span class="sxs-lookup"><span data-stu-id="01673-200">**To return the number of geometries in a geometry collection instance**</span></span>  
 [<span data-ttu-id="01673-201">STNumGeometries &#40;geometry データ型&#41;</span><span class="sxs-lookup"><span data-stu-id="01673-201">STNumGeometries &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stnumgeometries-geometry-data-type)  
  
 <span data-ttu-id="01673-202">geometry コレクション インスタンス内の特定の geometry を取得するには</span><span class="sxs-lookup"><span data-stu-id="01673-202">To return a specific geometry in a geometry collection instance</span></span>  
 <span data-ttu-id="01673-203">[STGeometryN &#40;geometry データ型&#41;](/sql/t-sql/spatial-geometry/stgeometryn-geometry-data-type)STGeometryN (geometry データ型)</span><span class="sxs-lookup"><span data-stu-id="01673-203">[STGeometryN &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stgeometryn-geometry-data-type)STGeometryN (geometry Data type)</span></span>  
  
  
  
###  <a name="number-of-points"></a><a name="number"></a> <span data-ttu-id="01673-204">点の数</span><span class="sxs-lookup"><span data-stu-id="01673-204">Number of Points</span></span>  
 <span data-ttu-id="01673-205">空でないすべて `geometry` のインスタンスは、*ポイント*で構成されます。</span><span class="sxs-lookup"><span data-stu-id="01673-205">All nonempty `geometry` instances are comprised of *points*.</span></span> <span data-ttu-id="01673-206">これらの点は、ジオメトリが描画される平面の X 座標と Y 座標を表します</span><span class="sxs-lookup"><span data-stu-id="01673-206">These points represent the X- and Y-coordinates of the plane on which the geometries are drawn.</span></span> <span data-ttu-id="01673-207">`geometry` には、インスタンスの点に対するクエリを実行するための組み込みメソッドが数多く用意されています。</span><span class="sxs-lookup"><span data-stu-id="01673-207">`geometry` provides numerous built-in methods for querying the points of an instance.</span></span>  
  
 <span data-ttu-id="01673-208">**インスタンスを構成する点の数を取得するには**</span><span class="sxs-lookup"><span data-stu-id="01673-208">**To return the number of points that comprise an instance**</span></span>  
 [<span data-ttu-id="01673-209">STNumPoints &#40;geometry データ型&#41;</span><span class="sxs-lookup"><span data-stu-id="01673-209">STNumPoints &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stnumpoints-geometry-data-type)  
  
 <span data-ttu-id="01673-210">**インスタンスの特定の点を取得するには**</span><span class="sxs-lookup"><span data-stu-id="01673-210">**To return a specific point in an instance**</span></span>  
 [<span data-ttu-id="01673-211">STPointN</span><span class="sxs-lookup"><span data-stu-id="01673-211">STPointN</span></span>](/sql/t-sql/spatial-geometry/stpointn-geometry-data-type)  
  
 <span data-ttu-id="01673-212">**インスタンス上にある任意の点を取得するには**</span><span class="sxs-lookup"><span data-stu-id="01673-212">**To return an arbitrary point that lies on an instance**</span></span>  
 [<span data-ttu-id="01673-213">STPointOnSurface</span><span class="sxs-lookup"><span data-stu-id="01673-213">STPointOnSurface</span></span>](/sql/t-sql/spatial-geometry/stpointonsurface-geometry-data-type)  
  
 <span data-ttu-id="01673-214">**インスタンスの始点を取得するには**</span><span class="sxs-lookup"><span data-stu-id="01673-214">**To return the start point of an instance**</span></span>  
 [<span data-ttu-id="01673-215">STStartPoint</span><span class="sxs-lookup"><span data-stu-id="01673-215">STStartPoint</span></span>](/sql/t-sql/spatial-geometry/ststartpoint-geometry-data-type)  
  
 <span data-ttu-id="01673-216">**インスタンスの終点を取得するには**</span><span class="sxs-lookup"><span data-stu-id="01673-216">**To return the end point of an instance**</span></span>  
 [<span data-ttu-id="01673-217">STEndpoint</span><span class="sxs-lookup"><span data-stu-id="01673-217">STEndpoint</span></span>](/sql/t-sql/spatial-geometry/stendpoint-geometry-data-type)  
  
 <span data-ttu-id="01673-218">**Point インスタンスの X 座標を取得するには**</span><span class="sxs-lookup"><span data-stu-id="01673-218">**To return the X-coordinate of a Point instance**</span></span>  
 [<span data-ttu-id="01673-219">STX &#40;geometry データ型&#41;</span><span class="sxs-lookup"><span data-stu-id="01673-219">STX &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stx-geometry-data-type)  
  
 <span data-ttu-id="01673-220">**Point インスタンスの Y 座標を取得するには**</span><span class="sxs-lookup"><span data-stu-id="01673-220">**To return the Y-coordinate of a Point instance**</span></span>  
 [<span data-ttu-id="01673-221">STY</span><span class="sxs-lookup"><span data-stu-id="01673-221">STY</span></span>](/sql/t-sql/spatial-geometry/sty-geometry-data-type)  
  
 <span data-ttu-id="01673-222">**Polygon、CurvePolygon、または MultiPolygon インスタンスの幾何学中心点を取得するには**</span><span class="sxs-lookup"><span data-stu-id="01673-222">**To return the geometric center point of a Polygon, CurvePolygon, or MultiPolygon instance**</span></span>  
 [<span data-ttu-id="01673-223">STCentroid</span><span class="sxs-lookup"><span data-stu-id="01673-223">STCentroid</span></span>](/sql/t-sql/spatial-geometry/stcentroid-geometry-data-type)  
  
  
  
###  <a name="dimension"></a><a name="dimension"></a> <span data-ttu-id="01673-224">[ディメンション]</span><span class="sxs-lookup"><span data-stu-id="01673-224">Dimension</span></span>  
 <span data-ttu-id="01673-225">空でない `geometry` インスタンスの次元は、0 次元、1 次元、2 次元のいずれかになります。</span><span class="sxs-lookup"><span data-stu-id="01673-225">A nonempty `geometry` instance can be 0-, 1-, or 2-dimensional.</span></span> <span data-ttu-id="01673-226">0 次元の `geometries` (`Point` や `MultiPoint` など) には長さや面積はありません。</span><span class="sxs-lookup"><span data-stu-id="01673-226">Zero-dimensional `geometries`, such as `Point` and `MultiPoint`, have no length or area.</span></span> <span data-ttu-id="01673-227">1 次元のオブジェクト (`LineString, CircularString, CompoundCurve`、`MultiLineString` など) には長さがあります。</span><span class="sxs-lookup"><span data-stu-id="01673-227">One-dimensional objects, such as `LineString, CircularString, CompoundCurve`, and `MultiLineString`, have length.</span></span> <span data-ttu-id="01673-228">2 次元のインスタンス (`Polygon`、`CurvePolygon`、`MultiPolygon` など) には面積と長さがあります。</span><span class="sxs-lookup"><span data-stu-id="01673-228">Two-dimensional instances, such as `Polygon`, `CurvePolygon`, and `MultiPolygon`, have area and length.</span></span> <span data-ttu-id="01673-229">空のインスタンスの次元は -1 としてレポートされます。`GeometryCollection` でレポートされる面積は、その内容の型によって異なります。</span><span class="sxs-lookup"><span data-stu-id="01673-229">Empty instances will report a dimension of -1, and a `GeometryCollection` will report an area dependent on the types of its contents.</span></span>  
  
 <span data-ttu-id="01673-230">**インスタンスの次元を取得するには**</span><span class="sxs-lookup"><span data-stu-id="01673-230">**To return the dimension of an instance**</span></span>  
 [<span data-ttu-id="01673-231">STDimension</span><span class="sxs-lookup"><span data-stu-id="01673-231">STDimension</span></span>](/sql/t-sql/spatial-geometry/stdimension-geometry-data-type)  
  
 <span data-ttu-id="01673-232">**インスタンスの長さを取得するには**</span><span class="sxs-lookup"><span data-stu-id="01673-232">**To return the length of an instance**</span></span>  
 [<span data-ttu-id="01673-233">STLength</span><span class="sxs-lookup"><span data-stu-id="01673-233">STLength</span></span>](/sql/t-sql/spatial-geometry/stlength-geometry-data-type)  
  
 <span data-ttu-id="01673-234">**インスタンスの面積を取得するには**</span><span class="sxs-lookup"><span data-stu-id="01673-234">**To return the area of an instance**</span></span>  
 [<span data-ttu-id="01673-235">STArea</span><span class="sxs-lookup"><span data-stu-id="01673-235">STArea</span></span>](/sql/t-sql/spatial-geometry/starea-geometry-data-type)  
  
  
  
###  <a name="empty"></a><a name="empty"></a> <span data-ttu-id="01673-236">空</span><span class="sxs-lookup"><span data-stu-id="01673-236">Empty</span></span>  
 <span data-ttu-id="01673-237">*空* `geometry` のインスタンスには点はありません。</span><span class="sxs-lookup"><span data-stu-id="01673-237">An *empty*`geometry` instance does not have any points.</span></span> <span data-ttu-id="01673-238">空の `LineString, CircularString` 、 `CompoundCurve` 、およびインスタンスの長さ `MultiLineString` は0です。</span><span class="sxs-lookup"><span data-stu-id="01673-238">The length of empty `LineString, CircularString`, `CompoundCurve`, and `MultiLineString` instances is zero.</span></span> <span data-ttu-id="01673-239">空の `Polygon`、`CurvePolygon`、および `MultiPolygon` インスタンスの面積は 0 です。</span><span class="sxs-lookup"><span data-stu-id="01673-239">The area of empty `Polygon`, `CurvePolygon`, and `MultiPolygon` instances is 0.</span></span>  
  
 <span data-ttu-id="01673-240">**インスタンスが空かどうかを調べるには**</span><span class="sxs-lookup"><span data-stu-id="01673-240">**To determine if an instance is empty**</span></span>  
 <span data-ttu-id="01673-241">[STIsEmpty](/sql/t-sql/spatial-geometry/stisempty-geometry-data-type)。</span><span class="sxs-lookup"><span data-stu-id="01673-241">[STIsEmpty](/sql/t-sql/spatial-geometry/stisempty-geometry-data-type).</span></span>  
  
  
  
###  <a name="simple"></a><a name="simple"></a> <span data-ttu-id="01673-242">Simple</span><span class="sxs-lookup"><span data-stu-id="01673-242">Simple</span></span>  
 <span data-ttu-id="01673-243">`geometry`インスタンスを*単純*にするには、次の両方の要件を満たしている必要があります。</span><span class="sxs-lookup"><span data-stu-id="01673-243">For a `geometry` of the instance to be *simple*, it must meet both of these requirements:</span></span>  
  
-   <span data-ttu-id="01673-244">インスタンスの各図形が終点以外で自己交差していてはいけない。</span><span class="sxs-lookup"><span data-stu-id="01673-244">Each figure of the instance must not intersect itself, except at its endpoints.</span></span>  
  
-   <span data-ttu-id="01673-245">インスタンスの 2 つの図形が、両方の図形の境界外部の点で互いに交差していてはいけない。</span><span class="sxs-lookup"><span data-stu-id="01673-245">No two figures of the instance can intersect each other at a point that is not in both of their boundaries.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="01673-246">空のジオメトリは常に単純です。</span><span class="sxs-lookup"><span data-stu-id="01673-246">Empty geometries are always simple.</span></span>  
  
 <span data-ttu-id="01673-247">**インスタンスが単純かどうかを調べるには**</span><span class="sxs-lookup"><span data-stu-id="01673-247">**To determine if an instance is simple**</span></span>  
 <span data-ttu-id="01673-248">[STIsSimple](/sql/t-sql/spatial-geometry/stissimple-geometry-data-type)。</span><span class="sxs-lookup"><span data-stu-id="01673-248">[STIsSimple](/sql/t-sql/spatial-geometry/stissimple-geometry-data-type).</span></span>  
  
  
  
###  <a name="boundary-interior-and-exterior"></a><a name="boundary"></a> <span data-ttu-id="01673-249">境界、内部、および外部</span><span class="sxs-lookup"><span data-stu-id="01673-249">Boundary, Interior, and Exterior</span></span>  
 <span data-ttu-id="01673-250">インスタンスの*内部*は、 `geometry` インスタンスによって占有されている領域であり、*外部*は占有されていない領域です。</span><span class="sxs-lookup"><span data-stu-id="01673-250">The *interior* of a `geometry` instance is the space occupied by the instance, and the *exterior* is the space not occupied it.</span></span>  
  
 <span data-ttu-id="01673-251">*境界* は、OGC によって次のように定義されています。</span><span class="sxs-lookup"><span data-stu-id="01673-251">*Boundary* is defined by the OGC as follows:</span></span>  
  
-   <span data-ttu-id="01673-252">`Point` インスタンスと `MultiPoint` インスタンスには境界はありません。</span><span class="sxs-lookup"><span data-stu-id="01673-252">`Point` and `MultiPoint` instances do not have a boundary.</span></span>  
  
-   <span data-ttu-id="01673-253">`LineString` と `MultiLineString` の境界は、始点と終点 (偶数回出現するものを除く) によって形成されます。</span><span class="sxs-lookup"><span data-stu-id="01673-253">`LineString` and `MultiLineString` boundaries are formed by the start points and end points, removing those that occur an even number of times.</span></span>  
  
```  
DECLARE @g geometry;  
SET @g = geometry::Parse('MULTILINESTRING((0 1, 0 0, 1 0, 0 1), (1 1, 1 0))');  
SELECT @g.STBoundary().ToString();  
```  
  
 <span data-ttu-id="01673-254">`Polygon` インスタンスや `MultiPolygon` インスタンスの境界は、そのリングの集合です。</span><span class="sxs-lookup"><span data-stu-id="01673-254">The boundary of a `Polygon` or `MultiPolygon` instance is the set of its rings.</span></span>  
  
```  
DECLARE @g geometry;  
SET @g = geometry::Parse('POLYGON((0 0, 3 0, 3 3, 0 3, 0 0), (1 1, 1 2, 2 2, 2 1, 1 1))');  
SELECT @g.STBoundary().ToString();  
```  
  
 <span data-ttu-id="01673-255">**インスタンスの境界を取得するには**</span><span class="sxs-lookup"><span data-stu-id="01673-255">**To return the boundary of an instance**</span></span>  
 [<span data-ttu-id="01673-256">STBoundary</span><span class="sxs-lookup"><span data-stu-id="01673-256">STBoundary</span></span>](/sql/t-sql/spatial-geometry/stboundary-geometry-data-type)  
  
  
  
###  <a name="envelope"></a><a name="envelope"></a> <span data-ttu-id="01673-257">エンベロープ</span><span class="sxs-lookup"><span data-stu-id="01673-257">Envelope</span></span>  
 <span data-ttu-id="01673-258">インスタンスの*エンベロープ* `geometry` (*境界ボックス*とも呼ばれます) は、インスタンスの最小値と最大値 (X, Y) 座標によって形成される、軸に沿った四角形です。</span><span class="sxs-lookup"><span data-stu-id="01673-258">The *envelope* of a `geometry` instance, also known as the *bounding box*, is the axis-aligned rectangle formed by the minimum and maximum (X,Y) coordinates of the instance.</span></span>  
  
 <span data-ttu-id="01673-259">**インスタンスのエンベロープを取得するには**</span><span class="sxs-lookup"><span data-stu-id="01673-259">**To return the envelope of an instance**</span></span>  
 [<span data-ttu-id="01673-260">STEnvelope</span><span class="sxs-lookup"><span data-stu-id="01673-260">STEnvelope</span></span>](/sql/t-sql/spatial-geometry/stenvelope-geometry-data-type)  
  
  
  
###  <a name="closure"></a><a name="closure"></a> <span data-ttu-id="01673-261">閉鎖性</span><span class="sxs-lookup"><span data-stu-id="01673-261">Closure</span></span>  
 <span data-ttu-id="01673-262">*閉じ*た `geometry` インスタンスは、始点と終点が同じである図形です。</span><span class="sxs-lookup"><span data-stu-id="01673-262">A *closed*`geometry` instance is a figure whose start points and end points are the same.</span></span> <span data-ttu-id="01673-263">`Polygon` インスタンスは閉じていると見なされます。</span><span class="sxs-lookup"><span data-stu-id="01673-263">`Polygon` instances are considered closed.</span></span> <span data-ttu-id="01673-264">`Point` インスタンスは閉じていないと見なされます。</span><span class="sxs-lookup"><span data-stu-id="01673-264">`Point` instances are not closed.</span></span>  
  
 <span data-ttu-id="01673-265">リングは、単純な閉じている `LineString` インスタンスです。</span><span class="sxs-lookup"><span data-stu-id="01673-265">A ring is a simple, closed `LineString` instance.</span></span>  
  
 <span data-ttu-id="01673-266">**インスタンスが閉じているかどうかを調べるには**</span><span class="sxs-lookup"><span data-stu-id="01673-266">**To determine if an instance is closed**</span></span>  
 [<span data-ttu-id="01673-267">STIsClosed</span><span class="sxs-lookup"><span data-stu-id="01673-267">STIsClosed</span></span>](/sql/t-sql/spatial-geometry/stisclosed-geometry-data-type)  
  
 <span data-ttu-id="01673-268">**インスタンスがリングかどうかを調べるには**</span><span class="sxs-lookup"><span data-stu-id="01673-268">**To determine if an instance is a ring**</span></span>  
 [<span data-ttu-id="01673-269">STIsRing</span><span class="sxs-lookup"><span data-stu-id="01673-269">STIsRing</span></span>](/sql/t-sql/spatial-geometry/stisring-geometry-data-type)  
  
 <span data-ttu-id="01673-270">**Polygon インスタンスの外部リングを取得するには**</span><span class="sxs-lookup"><span data-stu-id="01673-270">**To return the exterior ring of a Polygon instance**</span></span>  
 [<span data-ttu-id="01673-271">STExteriorRing</span><span class="sxs-lookup"><span data-stu-id="01673-271">STExteriorRing</span></span>](/sql/t-sql/spatial-geometry/stexteriorring-geometry-data-type)  
  
 <span data-ttu-id="01673-272">**Polygon の内部リングの数を取得するには**</span><span class="sxs-lookup"><span data-stu-id="01673-272">**To return the number of interior rings in a Polygon**</span></span>  
 [<span data-ttu-id="01673-273">STNumInteriorRing</span><span class="sxs-lookup"><span data-stu-id="01673-273">STNumInteriorRing</span></span>](/sql/t-sql/spatial-geometry/stnuminteriorring-geometry-data-type)  
  
 <span data-ttu-id="01673-274">**Polygon の指定した内部リングを取得するには**</span><span class="sxs-lookup"><span data-stu-id="01673-274">**To return a specified interior ring of a Polygon**</span></span>  
 [<span data-ttu-id="01673-275">STInteriorRingN</span><span class="sxs-lookup"><span data-stu-id="01673-275">STInteriorRingN</span></span>](/sql/t-sql/spatial-geometry/stinteriorringn-geometry-data-type)  
  
  
  
###  <a name="spatial-reference-id-srid"></a><a name="srid"></a> <span data-ttu-id="01673-276">SRID (spatial reference ID)</span><span class="sxs-lookup"><span data-stu-id="01673-276">Spatial Reference ID (SRID)</span></span>  
 <span data-ttu-id="01673-277">SRID (spatial reference ID) は、`geometry` インスタンスがどの座標系で表されているかを示す識別子です。</span><span class="sxs-lookup"><span data-stu-id="01673-277">The spatial reference ID (SRID) is an identifier specifying which coordinate system the `geometry` instance is represented in.</span></span> <span data-ttu-id="01673-278">SRID が異なる 2 つのインスタンスを比較することはできません。</span><span class="sxs-lookup"><span data-stu-id="01673-278">Two instances with different SRIDs are incomparable.</span></span>  
  
 <span data-ttu-id="01673-279">**インスタンスの SRID を設定または取得するには**</span><span class="sxs-lookup"><span data-stu-id="01673-279">**To set or return the SRID of an instance**</span></span>  
 [<span data-ttu-id="01673-280">STSrid</span><span class="sxs-lookup"><span data-stu-id="01673-280">STSrid</span></span>](/sql/t-sql/spatial-geometry/stsrid-geometry-data-type)  
  
 <span data-ttu-id="01673-281">このプロパティは変更できます。</span><span class="sxs-lookup"><span data-stu-id="01673-281">This property can be modified.</span></span>  
  
  
  
##  <a name="determining-relationships-between-geometry-instances"></a><a name="rel"></a> <span data-ttu-id="01673-282">geometry インスタンス間の関係の特定</span><span class="sxs-lookup"><span data-stu-id="01673-282">Determining Relationships between geometry Instances</span></span>  
 <span data-ttu-id="01673-283">`geometry` データ型には、2 つの `geometry` インスタンスの関係を調べるために使用できる組み込みメソッドが数多く用意されています。</span><span class="sxs-lookup"><span data-stu-id="01673-283">The `geometry` data type provides many built-in methods you can use to determine relationships between two `geometry` instances.</span></span>  
  
 <span data-ttu-id="01673-284">**2 つのインスタンスが同じ点の集合で構成されているかどうかを調べるには**</span><span class="sxs-lookup"><span data-stu-id="01673-284">**To determine if two instances comprise the same point set**</span></span>  
 [<span data-ttu-id="01673-285">STEquals</span><span class="sxs-lookup"><span data-stu-id="01673-285">STEquals</span></span>](/sql/t-sql/spatial-geometry/stequals-geometry-data-type)  
  
 <span data-ttu-id="01673-286">**2 つのインスタンスが互いに離れているかどうかを調べるには**</span><span class="sxs-lookup"><span data-stu-id="01673-286">**To determine if two instances are disjoint**</span></span>  
 [<span data-ttu-id="01673-287">STDisjoint</span><span class="sxs-lookup"><span data-stu-id="01673-287">STDisjoint</span></span>](/sql/t-sql/spatial-geometry/stdisjoint-geometry-data-type)  
  
 <span data-ttu-id="01673-288">**2 つのインスタンスが交差するかどうかを調べるには**</span><span class="sxs-lookup"><span data-stu-id="01673-288">**To determine if two instances intersect**</span></span>  
 [<span data-ttu-id="01673-289">STIntersects</span><span class="sxs-lookup"><span data-stu-id="01673-289">STIntersects</span></span>](/sql/t-sql/spatial-geometry/stintersects-geometry-data-type)  
  
 <span data-ttu-id="01673-290">**2 つのインスタンスが相互に接しているかどうかを調べるには**</span><span class="sxs-lookup"><span data-stu-id="01673-290">**To determine if two instances touch**</span></span>  
 [<span data-ttu-id="01673-291">STTouches</span><span class="sxs-lookup"><span data-stu-id="01673-291">STTouches</span></span>](/sql/t-sql/spatial-geometry/sttouches-geometry-data-type)  
  
 <span data-ttu-id="01673-292">**2 つのインスタンスが重なっているかどうかを調べるには**</span><span class="sxs-lookup"><span data-stu-id="01673-292">**To determine if two instances overlap**</span></span>  
 [<span data-ttu-id="01673-293">STOverlaps</span><span class="sxs-lookup"><span data-stu-id="01673-293">STOverlaps</span></span>](/sql/t-sql/spatial-geometry/stoverlaps-geometry-data-type)  
  
 <span data-ttu-id="01673-294">**2 つのインスタンスが交わるかどうかを調べるには**</span><span class="sxs-lookup"><span data-stu-id="01673-294">**To determine if two instances cross**</span></span>  
 [<span data-ttu-id="01673-295">STCrosses</span><span class="sxs-lookup"><span data-stu-id="01673-295">STCrosses</span></span>](/sql/t-sql/spatial-geometry/stcrosses-geometry-data-type)  
  
 <span data-ttu-id="01673-296">**あるインスタンスが別のインスタンスに含まれているかどうかを調べるには**</span><span class="sxs-lookup"><span data-stu-id="01673-296">**To determine if one instance is within another**</span></span>  
 [<span data-ttu-id="01673-297">STWithin</span><span class="sxs-lookup"><span data-stu-id="01673-297">STWithin</span></span>](/sql/t-sql/spatial-geometry/stwithin-geometry-data-type)  
  
 <span data-ttu-id="01673-298">**あるインスタンスが別のインスタンスを含んでいるかどうかを調べるには**</span><span class="sxs-lookup"><span data-stu-id="01673-298">**To determine if one instance contains another**</span></span>  
 [<span data-ttu-id="01673-299">STContains</span><span class="sxs-lookup"><span data-stu-id="01673-299">STContains</span></span>](/sql/t-sql/spatial-geometry/stcontains-geometry-data-type)  
  
 <span data-ttu-id="01673-300">**あるインスタンスが別のインスタンスと重なっているかどうかを調べるには**</span><span class="sxs-lookup"><span data-stu-id="01673-300">**To determine if one instance overlaps another**</span></span>  
 [<span data-ttu-id="01673-301">STOverlaps</span><span class="sxs-lookup"><span data-stu-id="01673-301">STOverlaps</span></span>](/sql/t-sql/spatial-geometry/stoverlaps-geometry-data-type)  
  
 <span data-ttu-id="01673-302">**2 つのインスタンスが空間的に関連するかどうかを調べるには**</span><span class="sxs-lookup"><span data-stu-id="01673-302">**To determine if two instances are spatially related**</span></span>  
 [<span data-ttu-id="01673-303">STRelate</span><span class="sxs-lookup"><span data-stu-id="01673-303">STRelate</span></span>](/sql/t-sql/spatial-geometry/strelate-geometry-data-type)  
  
 <span data-ttu-id="01673-304">**2 つのジオメトリの点の間の最短距離を調べるには**</span><span class="sxs-lookup"><span data-stu-id="01673-304">**To determine the shortest distance between points in two geometries**</span></span>  
 [<span data-ttu-id="01673-305">STDistance</span><span class="sxs-lookup"><span data-stu-id="01673-305">STDistance</span></span>](/sql/t-sql/spatial-geometry/stdistance-geometry-data-type)  
  
  
  
##  <a name="geometry-instances-default-to-zero-srid"></a><a name="defaultsrid"></a> <span data-ttu-id="01673-306">geometry インスタンスの既定の SRID は 0</span><span class="sxs-lookup"><span data-stu-id="01673-306">geometry Instances Default to Zero SRID</span></span>  
 <span data-ttu-id="01673-307">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の `geometry` インスタンスの既定の SRID は 0 です。</span><span class="sxs-lookup"><span data-stu-id="01673-307">The default SRID for `geometry` instances in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is 0.</span></span> <span data-ttu-id="01673-308">`geometry` 空間データでは、空間インスタンスに特定の SRID がなくても計算を実行できます。したがって、インスタンスは未定義の平面空間に存在することができます。</span><span class="sxs-lookup"><span data-stu-id="01673-308">With `geometry` spatial data, the specific SRID of the spatial instance is not required to perform calculations; thus, instances can reside in undefined planar space.</span></span> <span data-ttu-id="01673-309">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]では、`geometry` データ型のメソッドの計算で未定義の平面空間を表すために SRID 0 が使用されます。</span><span class="sxs-lookup"><span data-stu-id="01673-309">To indicate undefined planar space in the calculations of `geometry` data type methods, the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] uses SRID 0.</span></span>  
  
##  <a name="examples"></a><a name="examples"></a> <span data-ttu-id="01673-310">使用例</span><span class="sxs-lookup"><span data-stu-id="01673-310">Examples</span></span>  
 <span data-ttu-id="01673-311">次の 2 つの例は、geometry 型のデータの追加方法とクエリ方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="01673-311">The following two examples show how to add and query geometry data.</span></span>  
  
-   <span data-ttu-id="01673-312">最初の例では、ID 列と `geometry` 型の `GeomCol1`列を含むテーブルを作成します。</span><span class="sxs-lookup"><span data-stu-id="01673-312">The first example creates a table with an identity column and a `geometry` column `GeomCol1`.</span></span> <span data-ttu-id="01673-313">3 番目の列で、 `geometry` 型の列をその Open Geospatial Consortium (OGC) の Well-Known Text (WKT) 表現で示し、 `STAsText()` メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="01673-313">A third column renders the `geometry` column into its Open Geospatial Consortium (OGC) Well-Known Text (WKT) representation, and uses the `STAsText()` method.</span></span> <span data-ttu-id="01673-314">次に 2 つの行が挿入されます。1 つは、 `LineString` の `geometry`インスタンスを含む行で、もう 1 つは `Polygon` インスタンスを含む行です。</span><span class="sxs-lookup"><span data-stu-id="01673-314">Two rows are then inserted: one row contains a `LineString` instance of `geometry`, and one row contains a `Polygon` instance.</span></span>  
  
    ```  
    IF OBJECT_ID ( 'dbo.SpatialTable', 'U' ) IS NOT NULL   
        DROP TABLE dbo.SpatialTable;  
    GO  
  
    CREATE TABLE SpatialTable   
        ( id int IDENTITY (1,1),  
        GeomCol1 geometry,   
        GeomCol2 AS GeomCol1.STAsText() );  
    GO  
  
    INSERT INTO SpatialTable (GeomCol1)  
    VALUES (geometry::STGeomFromText('LINESTRING (100 100, 20 180, 180 180)', 0));  
  
    INSERT INTO SpatialTable (GeomCol1)  
    VALUES (geometry::STGeomFromText('POLYGON ((0 0, 150 0, 150 150, 0 150, 0 0))', 0));  
    GO  
    ```  
  
-   <span data-ttu-id="01673-315">2 番目の例では、 `STIntersection()` メソッドを使用して、前の例で挿入した 2 つの `geometry` インスタンスが交差する点を返します。</span><span class="sxs-lookup"><span data-stu-id="01673-315">The second example uses the `STIntersection()` method to return the points where the two previously inserted `geometry` instances intersect.</span></span>  
  
    ```  
    DECLARE @geom1 geometry;  
    DECLARE @geom2 geometry;  
    DECLARE @result geometry;  
  
    SELECT @geom1 = GeomCol1 FROM SpatialTable WHERE id = 1;  
    SELECT @geom2 = GeomCol1 FROM SpatialTable WHERE id = 2;  
    SELECT @result = @geom1.STIntersection(@geom2);  
    SELECT @result.STAsText();  
    ```  
  
  
  
## <a name="see-also"></a><span data-ttu-id="01673-316">参照</span><span class="sxs-lookup"><span data-stu-id="01673-316">See Also</span></span>  
 [<span data-ttu-id="01673-317">空間データ &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="01673-317">Spatial Data &#40;SQL Server&#41;</span></span>](spatial-data-sql-server.md)  
  
  
