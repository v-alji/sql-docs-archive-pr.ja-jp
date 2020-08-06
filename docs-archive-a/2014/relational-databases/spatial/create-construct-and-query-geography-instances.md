---
title: geography インスタンスの作成、構築、およびクエリ | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- geography data type [SQL Server]
- geodetic data type [SQL Server]
- geography data type [SQL Server], about geography data type
ms.assetid: b585851e-d15b-411f-adeb-aeabeb777c0b
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: d744457cc517a6172cca96b27eae1f456deca24e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632317"
---
# <a name="create-construct-and-query-geography-instances"></a><span data-ttu-id="2b572-102">geography インスタンスの作成、構築、およびクエリ</span><span class="sxs-lookup"><span data-stu-id="2b572-102">Create, Construct, and Query geography Instances</span></span>
  <span data-ttu-id="2b572-103">地理空間データ型の `geography` は、球体地球座標系のデータを表します。</span><span class="sxs-lookup"><span data-stu-id="2b572-103">The geography spatial data type, `geography`, represents data in a round-earth coordinate system.</span></span> <span data-ttu-id="2b572-104">この型は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]では .NET 共通言語ランタイム (CLR) のデータ型として実装されています。</span><span class="sxs-lookup"><span data-stu-id="2b572-104">This type is implemented as a .NET common language runtime (CLR) data type in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="2b572-105">データ型には、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `geography` GPS の緯度や経度の座標などの楕円体 (地球) データが格納されます。</span><span class="sxs-lookup"><span data-stu-id="2b572-105">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `geography` data type stores ellipsoidal (round-earth) data, such as GPS latitude and longitude coordinates.</span></span>  
  
 <span data-ttu-id="2b572-106">`geography` 型は、各データベースで使用できるように事前に定義されています。</span><span class="sxs-lookup"><span data-stu-id="2b572-106">The `geography` type is predefined and available in each database.</span></span> <span data-ttu-id="2b572-107">`geography` 型のテーブル列を作成し、システムが提供する他のデータ型を使用するときと同じように `geography` データを操作できます。</span><span class="sxs-lookup"><span data-stu-id="2b572-107">You can create table columns of type `geography` and operate on `geography` data in the same manner as you would use other system-supplied types.</span></span>  
  
##  <a name="creating-or-constructing-a-new-geography-instance"></a><a name="creating"></a> <span data-ttu-id="2b572-108">新しい geography インスタンスの作成または構築</span><span class="sxs-lookup"><span data-stu-id="2b572-108">Creating or constructing a new geography instance</span></span>  
  
###  <a name="creating-a-new-geography-instance-from-an-existing-instance"></a><a name="existing"></a> <span data-ttu-id="2b572-109">既存のインスタンスからの新しい geography インスタンスの作成</span><span class="sxs-lookup"><span data-stu-id="2b572-109">Creating a New geography Instance from an Existing Instance</span></span>  
 <span data-ttu-id="2b572-110">`geography` データ型には、既存のインスタンスに基づいて新しい `geography` インスタンスを作成するために使用できる組み込みメソッドが数多く用意されています。</span><span class="sxs-lookup"><span data-stu-id="2b572-110">The `geography` data type provides numerous built-in methods you can use to create new `geography` instances based on existing instances.</span></span>  
  
 <span data-ttu-id="2b572-111">**geography の周りにバッファーを作成するには**</span><span class="sxs-lookup"><span data-stu-id="2b572-111">**To create a buffer around a geography**</span></span>  
 [<span data-ttu-id="2b572-112">STBuffer &#40;geography データ型&#41;</span><span class="sxs-lookup"><span data-stu-id="2b572-112">STBuffer &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stbuffer-geography-data-type)  
  
 <span data-ttu-id="2b572-113">**geography の周りにバッファーを作成して許容誤差を指定するには**</span><span class="sxs-lookup"><span data-stu-id="2b572-113">**To create a buffer around a geography, allowing for a tolerance**</span></span>  
 [<span data-ttu-id="2b572-114">BufferWithTolerance &#40;geography データ型&#41;</span><span class="sxs-lookup"><span data-stu-id="2b572-114">BufferWithTolerance &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/bufferwithtolerance-geography-data-type)  
  
 <span data-ttu-id="2b572-115">**2 つの geography インスタンスの積集合から geography を作成するには**</span><span class="sxs-lookup"><span data-stu-id="2b572-115">**To create a geography from the intersection of two geography instances**</span></span>  
 [<span data-ttu-id="2b572-116">STIntersection &#40;geography データ型&#41;</span><span class="sxs-lookup"><span data-stu-id="2b572-116">STIntersection &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stintersection-geography-data-type)  
  
 <span data-ttu-id="2b572-117">**2 つの geography インスタンスの和集合から geography を作成するには**</span><span class="sxs-lookup"><span data-stu-id="2b572-117">**To create a geography from the union of two geography instances**</span></span>  
 [<span data-ttu-id="2b572-118">STUnion &#40;geography データ型&#41;</span><span class="sxs-lookup"><span data-stu-id="2b572-118">STUnion &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stunion-geography-data-type)  
  
 <span data-ttu-id="2b572-119">**一方の geography の、もう一方の geography と重なる部分を除いた点から geography を作成するには**</span><span class="sxs-lookup"><span data-stu-id="2b572-119">**To create a geography from the points where one geography does not overlap another**</span></span>  
 [<span data-ttu-id="2b572-120">STDifference &#40;geography データ型&#41;</span><span class="sxs-lookup"><span data-stu-id="2b572-120">STDifference &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stdifference-geography-data-type)  
  
###  <a name="constructing-a-geography-instance-from-well-known-text-input"></a><a name="wkt"></a> <span data-ttu-id="2b572-121">Well-Known Text 入力からの geography インスタンスの構築</span><span class="sxs-lookup"><span data-stu-id="2b572-121">Constructing a geography Instance from Well-Known Text Input</span></span>  
 <span data-ttu-id="2b572-122">`geography` データ型には、Open Geospatial Consortium (OGC) WKT 表現から geography を生成する組み込みのメソッドが数多く用意されています。</span><span class="sxs-lookup"><span data-stu-id="2b572-122">The `geography` data type provides several built-in methods that generate a geography from the Open Geospatial Consortium (OGC) WKT representation.</span></span> <span data-ttu-id="2b572-123">WKT 標準は geography データをテキスト形式で交換できるテキスト文字列です。</span><span class="sxs-lookup"><span data-stu-id="2b572-123">The WKT standard is a text string that allows geography data to be exchanged in textual form.</span></span>  
  
 <span data-ttu-id="2b572-124">**WKT 入力から任意の型の geography インスタンスを構築するには**</span><span class="sxs-lookup"><span data-stu-id="2b572-124">**To construct any type of geography instance from WKT input**</span></span>  
 [<span data-ttu-id="2b572-125">STGeomFromText #40;geography データ型&#41;</span><span class="sxs-lookup"><span data-stu-id="2b572-125">STGeomFromText &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stgeomfromtext-geography-data-type)  
  
 [<span data-ttu-id="2b572-126">Parse &#40;geography データ型&#41;</span><span class="sxs-lookup"><span data-stu-id="2b572-126">Parse &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/parse-geography-data-type)  
  
 <span data-ttu-id="2b572-127">**WKT 入力から geography Point インスタンスを構築するには**</span><span class="sxs-lookup"><span data-stu-id="2b572-127">**To construct a geography Point instance from WKT input**</span></span>  
 [<span data-ttu-id="2b572-128">STPointFromText &#40;geography データ型&#41;</span><span class="sxs-lookup"><span data-stu-id="2b572-128">STPointFromText &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stpointfromtext-geography-data-type)  
  
 <span data-ttu-id="2b572-129">**WKT 入力から geography MultiPoint インスタンスを構築するには**</span><span class="sxs-lookup"><span data-stu-id="2b572-129">**To construct a geography MultiPoint instance from WKT input**</span></span>  
 [<span data-ttu-id="2b572-130">STMPointFromText &#40;geography データ型&#41;</span><span class="sxs-lookup"><span data-stu-id="2b572-130">STMPointFromText &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stmpointfromtext-geography-data-type)  
  
 <span data-ttu-id="2b572-131">**WKT 入力から geography LineString インスタンスを構築するには**</span><span class="sxs-lookup"><span data-stu-id="2b572-131">**To construct a geography LineString instance from WKT input**</span></span>  
 <span data-ttu-id="2b572-132">STLineFromText (geography データ型)</span><span class="sxs-lookup"><span data-stu-id="2b572-132">STLineFromText (geography Data Type)</span></span>  
  
 <span data-ttu-id="2b572-133">**WKT 入力から geography MultiLineString インスタンスを構築するには**</span><span class="sxs-lookup"><span data-stu-id="2b572-133">**To construct a geography MultiLineString instance from WKT input**</span></span>  
 [<span data-ttu-id="2b572-134">STMLineFromText &#40;geography データ型&#41;</span><span class="sxs-lookup"><span data-stu-id="2b572-134">STMLineFromText &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stmlinefromtext-geography-data-type)  
  
 <span data-ttu-id="2b572-135">**WKT 入力から geography Polygon インスタンスを構築するには**</span><span class="sxs-lookup"><span data-stu-id="2b572-135">**To construct a geography Polygon instance from WKT input**</span></span>  
 [<span data-ttu-id="2b572-136">STPolyFromText &#40;geography データ型&#41;</span><span class="sxs-lookup"><span data-stu-id="2b572-136">STPolyFromText &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stpolyfromtext-geography-data-type)  
  
 <span data-ttu-id="2b572-137">**WKT 入力から geography MultiPolygon インスタンスを構築するには**</span><span class="sxs-lookup"><span data-stu-id="2b572-137">**To construct a geography MultiPolygon instance from WKT input**</span></span>  
 [<span data-ttu-id="2b572-138">STMPolyFromText &#40;geography データ型&#41;</span><span class="sxs-lookup"><span data-stu-id="2b572-138">STMPolyFromText &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stmpolyfromtext-geography-data-type)  
  
 <span data-ttu-id="2b572-139">**WKT 入力から geography GeometryCollection インスタンスを構築するには**</span><span class="sxs-lookup"><span data-stu-id="2b572-139">**To construct a geography GeometryCollection instance from WKT input**</span></span>  
 [<span data-ttu-id="2b572-140">STGeomCollFromText &#40;geography データ型&#41;</span><span class="sxs-lookup"><span data-stu-id="2b572-140">STGeomCollFromText &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stgeomcollfromtext-geography-data-type)  
  
###  <a name="constructing-a-geography-instance-from-well-known-binary-input"></a><a name="wkb"></a> <span data-ttu-id="2b572-141">Well-Known Binary 入力からの geography インスタンスの構築</span><span class="sxs-lookup"><span data-stu-id="2b572-141">Constructing a geography Instance from Well-Known Binary Input</span></span>  
 <span data-ttu-id="2b572-142">WKB は、`Geography` データをアプリケーションと SQL データベース間で交換することができる、OGC で指定されたバイナリ形式です。</span><span class="sxs-lookup"><span data-stu-id="2b572-142">WKB is a binary format specified by the OGC that permits `Geography` data to be exchanged between a client application and an SQL database.</span></span> <span data-ttu-id="2b572-143">次の関数は、WKB 入力を受け入れて geography インスタンスを構築します。</span><span class="sxs-lookup"><span data-stu-id="2b572-143">The following functions accept WKB input to construct geography instances:</span></span>  
  
 <span data-ttu-id="2b572-144">**WKB 入力から任意の型の geography インスタンスを構築するには**</span><span class="sxs-lookup"><span data-stu-id="2b572-144">**To construct any type of geography instance from WKB input**</span></span>  
 [<span data-ttu-id="2b572-145">STGeomFromWKB &#40;geography データ型&#41;</span><span class="sxs-lookup"><span data-stu-id="2b572-145">STGeomFromWKB &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stgeomfromwkb-geography-data-type)  
  
 <span data-ttu-id="2b572-146">**WKB 入力から geography Point インスタンスを構築するには**</span><span class="sxs-lookup"><span data-stu-id="2b572-146">**To construct a geography Point instance from WKB input**</span></span>  
 [<span data-ttu-id="2b572-147">STPointFromWKB &#40;geography データ型&#41;</span><span class="sxs-lookup"><span data-stu-id="2b572-147">STPointFromWKB &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stpointfromwkb-geography-data-type)  
  
 <span data-ttu-id="2b572-148">**WKB 入力から geography MultiPoint インスタンスを構築するには**</span><span class="sxs-lookup"><span data-stu-id="2b572-148">**To construct a geography MultiPoint instance from WKB input**</span></span>  
 [<span data-ttu-id="2b572-149">STMPointFromWKB &#40;geography データ型&#41;</span><span class="sxs-lookup"><span data-stu-id="2b572-149">STMPointFromWKB &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stmpointfromwkb-geography-data-type)  
  
 <span data-ttu-id="2b572-150">**WKB 入力から geography LineString インスタンスを構築するには**</span><span class="sxs-lookup"><span data-stu-id="2b572-150">**To construct a geography LineString instance from WKB input**</span></span>  
 [<span data-ttu-id="2b572-151">STLineFromWKB &#40;geography データ型&#41;</span><span class="sxs-lookup"><span data-stu-id="2b572-151">STLineFromWKB &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stlinefromwkb-geography-data-type)  
  
 <span data-ttu-id="2b572-152">**WKB 入力から geography MultiLineString インスタンスを構築するには**</span><span class="sxs-lookup"><span data-stu-id="2b572-152">**To construct a geography MultiLineString instance from WKB input**</span></span>  
 [<span data-ttu-id="2b572-153">STMLineFromWKB &#40;geography データ型&#41;</span><span class="sxs-lookup"><span data-stu-id="2b572-153">STMLineFromWKB &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stmlinefromwkb-geography-data-type)  
  
 <span data-ttu-id="2b572-154">**WKB 入力から geography Polygon インスタンスを構築するには**</span><span class="sxs-lookup"><span data-stu-id="2b572-154">**To construct a geography Polygon instance from WKB input**</span></span>  
 [<span data-ttu-id="2b572-155">STPolyFromWKB &#40;geography データ型&#41;</span><span class="sxs-lookup"><span data-stu-id="2b572-155">STPolyFromWKB &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stpolyfromwkb-geography-data-type)  
  
 <span data-ttu-id="2b572-156">**WKB 入力から geography MultiPolygon インスタンスを構築するには**</span><span class="sxs-lookup"><span data-stu-id="2b572-156">**To construct a geography MultiPolygon instance from WKB input**</span></span>  
 [<span data-ttu-id="2b572-157">STMPolyFromWKB &#40;geography データ型&#41;</span><span class="sxs-lookup"><span data-stu-id="2b572-157">STMPolyFromWKB &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stmpolyfromwkb-geography-data-type)  
  
 <span data-ttu-id="2b572-158">**WKB 入力から geography GeometryCollection インスタンスを構築するには**</span><span class="sxs-lookup"><span data-stu-id="2b572-158">**To construct a geography GeometryCollection instance from WKB input**</span></span>  
 <span data-ttu-id="2b572-159">[STGeomCollFromWKB &#40;geography データ型&#41;](/sql/t-sql/spatial-geography/stgeomcollfromwkb-geography-data-type)STGeomCollFromWKB (geography データ型)</span><span class="sxs-lookup"><span data-stu-id="2b572-159">[STGeomCollFromWKB &#40;geography Data Type&#41;](/sql/t-sql/spatial-geography/stgeomcollfromwkb-geography-data-type)STGeomCollFromWKB (geography Data Type)</span></span>  
  
###  <a name="constructing-a-geography-instance-from-gml-text-input"></a><a name="gml"></a> <span data-ttu-id="2b572-160">GML Text 入力からの geography インスタンスの構築</span><span class="sxs-lookup"><span data-stu-id="2b572-160">Constructing a geography Instance from GML Text Input</span></span>  
 <span data-ttu-id="2b572-161">データ型には、 `geography` `geography` GML (インスタンスの XML 表現) からインスタンスを生成するメソッドが用意されて `geography` います。</span><span class="sxs-lookup"><span data-stu-id="2b572-161">The `geography` data type provides a method that generates a `geography` instance from GML, an XML representation of a `geography` instance.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="2b572-162">では、GML のサブセットをサポートします。</span><span class="sxs-lookup"><span data-stu-id="2b572-162">supports a subset of GML.</span></span>  
  
 <span data-ttu-id="2b572-163">Geography Markup Language の詳細については、OGC の仕様の「 [OGC の仕様、Geography Markup Language](https://go.microsoft.com/fwlink/?LinkId=93629)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2b572-163">For more information on Geography Markup Language, see the OGC Specification: [OGC Specifications, Geography Markup Language.](https://go.microsoft.com/fwlink/?LinkId=93629)</span></span>  
  
 <span data-ttu-id="2b572-164">**GML 入力から任意の型の geography インスタンスを構築するには**</span><span class="sxs-lookup"><span data-stu-id="2b572-164">**To construct any type of geography instance from GML input**</span></span>  
 [<span data-ttu-id="2b572-165">GeomFromGML &#40;geography データ型&#41;</span><span class="sxs-lookup"><span data-stu-id="2b572-165">GeomFromGML &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/geomfromgml-geography-data-type)  
  
##  <a name="returning-well-known-text-and-well-known-binary-from-a-geography-instance"></a><a name="returning"></a> <span data-ttu-id="2b572-166">geography インスタンスからの Well-Known Text および Well-Known Binary の取得</span><span class="sxs-lookup"><span data-stu-id="2b572-166">Returning Well-Known Text and Well-Known Binary from a geography Instance</span></span>  
 <span data-ttu-id="2b572-167">次のメソッドを使用して、`geography` インスタンスの WKT 形式または WKB 形式のいずれかを取得できます。</span><span class="sxs-lookup"><span data-stu-id="2b572-167">You can use the following methods to return either the WKT or WKB format of a `geography` instance:</span></span>  
  
 <span data-ttu-id="2b572-168">**geography インスタンスの WKT 表現を取得するには**</span><span class="sxs-lookup"><span data-stu-id="2b572-168">**To return the WKT representation of a geography instance**</span></span>  
 [<span data-ttu-id="2b572-169">STAsText &#40;geography データ型&#41;</span><span class="sxs-lookup"><span data-stu-id="2b572-169">STAsText &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stastext-geography-data-type)  
  
 [<span data-ttu-id="2b572-170">ToString &#40;geography データ型&#41;</span><span class="sxs-lookup"><span data-stu-id="2b572-170">ToString &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/tostring-geography-data-type)  
  
 <span data-ttu-id="2b572-171">**geography インスタンスの WKT 表現を Z と M の値も含めて取得するには**</span><span class="sxs-lookup"><span data-stu-id="2b572-171">**To return the WKT representation of a geography instance including any Z and M values**</span></span>  
 [<span data-ttu-id="2b572-172">AsTextZM &#40;geography データ型&#41;</span><span class="sxs-lookup"><span data-stu-id="2b572-172">AsTextZM &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/astextzm-geography-data-type)  
  
 <span data-ttu-id="2b572-173">**geography インスタンスの WKB 表現を取得するには**</span><span class="sxs-lookup"><span data-stu-id="2b572-173">**To return the WKB representation of a geography instance**</span></span>  
 [<span data-ttu-id="2b572-174">STAsBinary &#40;geography データ型&#41;</span><span class="sxs-lookup"><span data-stu-id="2b572-174">STAsBinary &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stasbinary-geography-data-type)  
  
 <span data-ttu-id="2b572-175">**geography インスタンスの GML 表現を取得するには**</span><span class="sxs-lookup"><span data-stu-id="2b572-175">**To return a GML representation of a geography instance**</span></span>  
 [<span data-ttu-id="2b572-176">AsGml &#40;geography データ型&#41;</span><span class="sxs-lookup"><span data-stu-id="2b572-176">AsGml &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/asgml-geography-data-type)  
  
##  <a name="querying-the-properties-and-behaviors-of-geography-instances"></a><a name="query"></a> <span data-ttu-id="2b572-177">geography インスタンスのプロパティと動作のクエリ</span><span class="sxs-lookup"><span data-stu-id="2b572-177">Querying the Properties and Behaviors of geography Instances</span></span>  
 <span data-ttu-id="2b572-178">すべて `geography` のインスタンスには、が提供するメソッドを使用して取得できるいくつかのプロパティがあり [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="2b572-178">All `geography` instances have a number of properties that can be retrieved through methods that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provides.</span></span> <span data-ttu-id="2b572-179">以下のトピックでは、geography 型のプロパティおよび動作と、geography 型に対するクエリを実行するためのメソッドについて説明します。</span><span class="sxs-lookup"><span data-stu-id="2b572-179">The following topics define the properties and behaviors of geography types, and the methods for querying each one.</span></span>  
  
###  <a name="validity-instance-type-and-geometrycollection-information"></a><a name="valid"></a> <span data-ttu-id="2b572-180">有効性、インスタンスの型、および GeometryCollection 情報</span><span class="sxs-lookup"><span data-stu-id="2b572-180">Validity, Instance Type, and GeometryCollection Information</span></span>  
 <span data-ttu-id="2b572-181">インスタンス `geography` が構築された後、次のメソッドを使用してインスタンスの型を返すことができます。インスタンスの場合は、 `GeometryCollection` 特定のインスタンスを返し `geography` ます。</span><span class="sxs-lookup"><span data-stu-id="2b572-181">After a `geography` instance is constructed, you can use the following methods to return the instance type, or if it is a `GeometryCollection` instance, return a specific `geography` instance.</span></span>  
  
 <span data-ttu-id="2b572-182">**geography インスタンスの型を取得するには**</span><span class="sxs-lookup"><span data-stu-id="2b572-182">**To return the instance type of a geography**</span></span>  
 [<span data-ttu-id="2b572-183">STGeometryType &#40;geography データ型&#41;</span><span class="sxs-lookup"><span data-stu-id="2b572-183">STGeometryType &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stgeometrytype-geography-data-type)  
  
 <span data-ttu-id="2b572-184">**geography が特定のインスタンスの型であるかどうかを調べるには**</span><span class="sxs-lookup"><span data-stu-id="2b572-184">**To determine if a geography is a given instance type**</span></span>  
 [<span data-ttu-id="2b572-185">InstanceOf &#40;geography データ型&#41;</span><span class="sxs-lookup"><span data-stu-id="2b572-185">InstanceOf &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/instanceof-geography-data-type)  
  
 <span data-ttu-id="2b572-186">**geography インスタンスがそのインスタンスの型に対応する適切な形式であるかどうかを調べるには**</span><span class="sxs-lookup"><span data-stu-id="2b572-186">**To determine if a geography instance is well-formed for its instance type**</span></span>  
 [<span data-ttu-id="2b572-187">STNumGeometries &#40;geography データ型&#41;</span><span class="sxs-lookup"><span data-stu-id="2b572-187">STNumGeometries &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stnumgeometries-geography-data-type)  
  
 <span data-ttu-id="2b572-188">**GeometryCollection インスタンス内の特定の geography を取得するには**</span><span class="sxs-lookup"><span data-stu-id="2b572-188">**To return a specific geography in a GeometryCollection instance**</span></span>  
 <span data-ttu-id="2b572-189">[STGeometryN &#40;geography データ型&#41;](/sql/t-sql/spatial-geography/stgeometryn-geography-data-type)STGeometryN (geography データ型)</span><span class="sxs-lookup"><span data-stu-id="2b572-189">[STGeometryN &#40;geography Data Type&#41;](/sql/t-sql/spatial-geography/stgeometryn-geography-data-type)STGeometryN (geography Data Type)</span></span>  
  
###  <a name="number-of-points"></a><a name="number"></a> <span data-ttu-id="2b572-190">点の数</span><span class="sxs-lookup"><span data-stu-id="2b572-190">Number of Points</span></span>  
 <span data-ttu-id="2b572-191">空でないすべて `geography` のインスタンスは、*ポイント*で構成されます。</span><span class="sxs-lookup"><span data-stu-id="2b572-191">All nonempty `geography` instances are comprised of *points*.</span></span> <span data-ttu-id="2b572-192">これらの点は、`geography` インスタンスが描画される地球の緯度経度座標を表します。</span><span class="sxs-lookup"><span data-stu-id="2b572-192">These points represent the latitude and longitude coordinates of the earth on which the `geography` instances are drawn.</span></span> <span data-ttu-id="2b572-193">`geography` データ型には、インスタンスの点に対するクエリを実行するための組み込みメソッドが数多く用意されています。</span><span class="sxs-lookup"><span data-stu-id="2b572-193">The data type `geography` provides numerous built-in methods for querying the points of an instance.</span></span>  
  
 <span data-ttu-id="2b572-194">**インスタンスを構成する点の数を取得するには**</span><span class="sxs-lookup"><span data-stu-id="2b572-194">**To return the number of points that comprise an instance**</span></span>  
 [<span data-ttu-id="2b572-195">STNumPoints &#40;geography データ型&#41;</span><span class="sxs-lookup"><span data-stu-id="2b572-195">STNumPoints &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stnumpoints-geography-data-type)  
  
 <span data-ttu-id="2b572-196">**インスタンスの特定の点を取得するには**</span><span class="sxs-lookup"><span data-stu-id="2b572-196">**To return a specific point in an instance**</span></span>  
 [<span data-ttu-id="2b572-197">STPointN &#40;geometry データ型&#41;</span><span class="sxs-lookup"><span data-stu-id="2b572-197">STPointN &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stpointn-geometry-data-type)  
  
 <span data-ttu-id="2b572-198">**インスタンスの始点を取得するには**</span><span class="sxs-lookup"><span data-stu-id="2b572-198">**To return the start point of an instance**</span></span>  
 [<span data-ttu-id="2b572-199">STStartPoint &#40;geography データ型&#41;</span><span class="sxs-lookup"><span data-stu-id="2b572-199">STStartPoint &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/ststartpoint-geography-data-type)  
  
 <span data-ttu-id="2b572-200">**インスタンスの終点を取得するには**</span><span class="sxs-lookup"><span data-stu-id="2b572-200">**To return the end point of an instance**</span></span>  
 [<span data-ttu-id="2b572-201">STEndpoint &#40;geography データ型&#41;</span><span class="sxs-lookup"><span data-stu-id="2b572-201">STEndpoint &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stendpoint-geography-data-type)  
  
###  <a name="dimension"></a><a name="dimension"></a> <span data-ttu-id="2b572-202">[ディメンション]</span><span class="sxs-lookup"><span data-stu-id="2b572-202">Dimension</span></span>  
 <span data-ttu-id="2b572-203">空でない `geography` インスタンスの次元は、0 次元、1 次元、2 次元のいずれかになります。</span><span class="sxs-lookup"><span data-stu-id="2b572-203">A nonempty `geography` instance can be 0-, 1-, or 2-dimensional.</span></span> <span data-ttu-id="2b572-204">0次元の `geography` インスタンス (やなど `Point` ) `MultiPoint` には、長さや面積はありません。</span><span class="sxs-lookup"><span data-stu-id="2b572-204">Zero-dimensional `geography` instances, such as `Point` and `MultiPoint`, have no length or area.</span></span> <span data-ttu-id="2b572-205">1 次元のオブジェクト (`LineString, CircularString`、`CompoundCurve`、`MultiLineString` など) には長さがあります。</span><span class="sxs-lookup"><span data-stu-id="2b572-205">One-dimensional objects, such as `LineString, CircularString`, `CompoundCurve`, and `MultiLineString`, have length.</span></span> <span data-ttu-id="2b572-206">2 次元のインスタンス (`Polygon, CurvePolygon`、`MultiPolygon` など) には面積と長さがあります。</span><span class="sxs-lookup"><span data-stu-id="2b572-206">Two-dimensional instances, such as `Polygon, CurvePolygon`, and `MultiPolygon`, have area and length.</span></span> <span data-ttu-id="2b572-207">空のインスタンスの次元は -1 としてレポートされます。`GeometryCollection` ではその内容の最も大きな次元がレポートされます。</span><span class="sxs-lookup"><span data-stu-id="2b572-207">Empty instances report a dimension of -1, and a `GeometryCollection` reports the maximum dimension of its contents.</span></span>  
  
 <span data-ttu-id="2b572-208">**インスタンスの次元を取得するには**</span><span class="sxs-lookup"><span data-stu-id="2b572-208">**To return the dimension of an instance**</span></span>  
 [<span data-ttu-id="2b572-209">STDimension &#40;geography データ型&#41;</span><span class="sxs-lookup"><span data-stu-id="2b572-209">STDimension &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stdimension-geography-data-type)  
  
 <span data-ttu-id="2b572-210">**インスタンスの長さを取得するには**</span><span class="sxs-lookup"><span data-stu-id="2b572-210">**To return the length of an instance**</span></span>  
 [<span data-ttu-id="2b572-211">STLength &#40;geography データ型&#41;</span><span class="sxs-lookup"><span data-stu-id="2b572-211">STLength &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stlength-geography-data-type)  
  
 <span data-ttu-id="2b572-212">**インスタンスの面積を取得するには**</span><span class="sxs-lookup"><span data-stu-id="2b572-212">**To return the area of an instance**</span></span>  
 [<span data-ttu-id="2b572-213">STArea &#40;geography データ型&#41;</span><span class="sxs-lookup"><span data-stu-id="2b572-213">STArea &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/starea-geography-data-type)  
  
###  <a name="empty"></a><a name="empty"></a> <span data-ttu-id="2b572-214">空</span><span class="sxs-lookup"><span data-stu-id="2b572-214">Empty</span></span>  
 <span data-ttu-id="2b572-215">*空* `geography` のインスタンスには点はありません。</span><span class="sxs-lookup"><span data-stu-id="2b572-215">An *empty*`geography` instance does not have any points.</span></span> <span data-ttu-id="2b572-216">空の `LineString, CircularString`、`CompoundCurve`、および `MultiLineString` インスタンスの長さは 0 です。</span><span class="sxs-lookup"><span data-stu-id="2b572-216">The length of empty `LineString, CircularString`, `CompoundCurve`, and `MultiLineString` instances is 0.</span></span> <span data-ttu-id="2b572-217">空の `Polygon, CurvePolygon`、および `MultiPolygon` インスタンスの面積は 0 です。</span><span class="sxs-lookup"><span data-stu-id="2b572-217">The area of empty `Polygon, CurvePolygon` and `MultiPolygon` instances is 0.</span></span>  
  
 <span data-ttu-id="2b572-218">**インスタンスが空かどうかを調べるには**</span><span class="sxs-lookup"><span data-stu-id="2b572-218">**To determine if an instance is empty**</span></span>  
 [<span data-ttu-id="2b572-219">STIsEmpty &#40;geography データ型&#41;</span><span class="sxs-lookup"><span data-stu-id="2b572-219">STIsEmpty &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stisempty-geography-data-type)  
  
###  <a name="closure"></a><a name="closure"></a> <span data-ttu-id="2b572-220">閉鎖性</span><span class="sxs-lookup"><span data-stu-id="2b572-220">Closure</span></span>  
 <span data-ttu-id="2b572-221">*閉じ*た `geography` インスタンスは、始点と終点が同じである図形です。</span><span class="sxs-lookup"><span data-stu-id="2b572-221">A *closed*`geography` instance is a figure whose start points and end points are the same.</span></span> <span data-ttu-id="2b572-222">`Polygon` インスタンスは閉じていると見なされます。</span><span class="sxs-lookup"><span data-stu-id="2b572-222">`Polygon` instances are considered closed.</span></span> <span data-ttu-id="2b572-223">`Point` インスタンスは閉じていないと見なされます。</span><span class="sxs-lookup"><span data-stu-id="2b572-223">`Point` instances are not closed.</span></span>  
  
 <span data-ttu-id="2b572-224">リングは、単純な閉じている `LineString` インスタンスです。</span><span class="sxs-lookup"><span data-stu-id="2b572-224">A ring is a simple, closed `LineString` instance.</span></span>  
  
 <span data-ttu-id="2b572-225">**インスタンスが閉じているかどうかを調べるには**</span><span class="sxs-lookup"><span data-stu-id="2b572-225">**To determine if an instance is closed**</span></span>  
 [<span data-ttu-id="2b572-226">STIsClosed &#40;geography データ型&#41;</span><span class="sxs-lookup"><span data-stu-id="2b572-226">STIsClosed &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stisclosed-geography-data-type)  
  
 <span data-ttu-id="2b572-227">**Polygon インスタンスのリングの数を取得するには**</span><span class="sxs-lookup"><span data-stu-id="2b572-227">**To return the number of rings in a Polygon instance**</span></span>  
 [<span data-ttu-id="2b572-228">NumRings &#40;geography データ型&#41;</span><span class="sxs-lookup"><span data-stu-id="2b572-228">NumRings &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/numrings-geography-data-type)  
  
 <span data-ttu-id="2b572-229">**geography インスタンスの指定したリングを取得するには**</span><span class="sxs-lookup"><span data-stu-id="2b572-229">**To return a specified ring of a geography instance**</span></span>  
 [<span data-ttu-id="2b572-230">RingN &#40;geography データ型&#41;</span><span class="sxs-lookup"><span data-stu-id="2b572-230">RingN &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/ringn-geography-data-type)  
  
###  <a name="spatial-reference-id-srid"></a><a name="srid"></a> <span data-ttu-id="2b572-231">SRID (spatial reference ID)</span><span class="sxs-lookup"><span data-stu-id="2b572-231">Spatial Reference ID (SRID)</span></span>  
 <span data-ttu-id="2b572-232">SRID (spatial reference ID) は、`geography` インスタンスがどの楕円体座標系で表されているかを示す識別子です。</span><span class="sxs-lookup"><span data-stu-id="2b572-232">The spatial reference ID (SRID) is an identifier specifying which ellipsoidal coordinate system the `geography` instance is represented in.</span></span> <span data-ttu-id="2b572-233">SRID が異なる 2 つの `geography` インスタンスを比較することはできません。</span><span class="sxs-lookup"><span data-stu-id="2b572-233">Two `geography` instances with different SRIDs cannot be compared.</span></span>  
  
 <span data-ttu-id="2b572-234">**インスタンスの SRID を設定または取得するには**</span><span class="sxs-lookup"><span data-stu-id="2b572-234">**To set or return the SRID of an instance**</span></span>  
 [<span data-ttu-id="2b572-235">STSrid &#40;geography データ型&#41;</span><span class="sxs-lookup"><span data-stu-id="2b572-235">STSrid &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stsrid-geography-data-type)  
  
 <span data-ttu-id="2b572-236">このプロパティは変更できます。</span><span class="sxs-lookup"><span data-stu-id="2b572-236">This property can be modified.</span></span>  
  
##  <a name="determining-relationships-between-geography-instances"></a><a name="rel"></a> <span data-ttu-id="2b572-237">geography インスタンスの関係の特定</span><span class="sxs-lookup"><span data-stu-id="2b572-237">Determining Relationships between geography Instances</span></span>  
 <span data-ttu-id="2b572-238">`geography` データ型には、2 つの `geography` インスタンスの関係を調べるために使用できる組み込みメソッドが数多く用意されています。</span><span class="sxs-lookup"><span data-stu-id="2b572-238">The `geography` data type provides many built-in methods you can use to determine relationships between two `geography` instances.</span></span>  
  
 <span data-ttu-id="2b572-239">**2 つのインスタンスが同じ点の集合で構成されているかどうかを調べるには**</span><span class="sxs-lookup"><span data-stu-id="2b572-239">**To determine if two instances comprise the same point set**</span></span>  
 [<span data-ttu-id="2b572-240">STEquals &#40;geometry データ型&#41;</span><span class="sxs-lookup"><span data-stu-id="2b572-240">STEquals &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stequals-geometry-data-type)  
  
 <span data-ttu-id="2b572-241">**2 つのインスタンスが互いに離れているかどうかを調べるには**</span><span class="sxs-lookup"><span data-stu-id="2b572-241">**To determine if two instances are disjoint**</span></span>  
 [<span data-ttu-id="2b572-242">STDisjoint &#40;geometry データ型&#41;</span><span class="sxs-lookup"><span data-stu-id="2b572-242">STDisjoint &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stdisjoint-geometry-data-type)  
  
 <span data-ttu-id="2b572-243">**2 つのインスタンスが交差するかどうかを調べるには**</span><span class="sxs-lookup"><span data-stu-id="2b572-243">**To determine if two instances intersect**</span></span>  
 [<span data-ttu-id="2b572-244">STIntersects &#40;geometry データ型&#41;</span><span class="sxs-lookup"><span data-stu-id="2b572-244">STIntersects &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stintersects-geometry-data-type)  
  
 <span data-ttu-id="2b572-245">**2 つのインスタンスが交差する点を調べるには**</span><span class="sxs-lookup"><span data-stu-id="2b572-245">**To determine the point or points where two instances intersect**</span></span>  
 [<span data-ttu-id="2b572-246">STIntersection &#40;geography データ型&#41;</span><span class="sxs-lookup"><span data-stu-id="2b572-246">STIntersection &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stintersection-geography-data-type)  
  
 <span data-ttu-id="2b572-247">**2 つの geography インスタンスの点の間の最短距離を調べるには**</span><span class="sxs-lookup"><span data-stu-id="2b572-247">**To determine the shortest distance between points in two geography instances**</span></span>  
 [<span data-ttu-id="2b572-248">STDistance &#40;geometry データ型&#41;</span><span class="sxs-lookup"><span data-stu-id="2b572-248">STDistance &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stdistance-geometry-data-type)  
  
 <span data-ttu-id="2b572-249">**2 つの geography インスタンスの点の相違を調べるには**</span><span class="sxs-lookup"><span data-stu-id="2b572-249">**To determine the difference in points between two geography instances**</span></span>  
 [<span data-ttu-id="2b572-250">STDifference &#40;geography データ型&#41;</span><span class="sxs-lookup"><span data-stu-id="2b572-250">STDifference &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stdifference-geography-data-type)  
  
 <span data-ttu-id="2b572-251">**2 つの geography インスタンスを比較して一方のインスタンスの対称差 (重複しない点) を取得するには**</span><span class="sxs-lookup"><span data-stu-id="2b572-251">**To derive the symmetric difference, or unique points, of one geography instance compared with another instance**</span></span>  
 [<span data-ttu-id="2b572-252">STSymDifference &#40;geography データ型&#41;</span><span class="sxs-lookup"><span data-stu-id="2b572-252">STSymDifference &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stsymdifference-geography-data-type)  
  
##  <a name="geography-instances-must-use-supported-srid"></a><a name="supportedsrid"></a> <span data-ttu-id="2b572-253">geography インスタンスでは必ずサポート対象の SRID を使用</span><span class="sxs-lookup"><span data-stu-id="2b572-253">geography Instances Must Use Supported SRID</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="2b572-254">EPSG 標準に基づく SRID をサポートします。</span><span class="sxs-lookup"><span data-stu-id="2b572-254">supports SRIDs based on the EPSG standards.</span></span> <span data-ttu-id="2b572-255">地理空間データを使用して計算を実行したりメソッドを使用したりする際には、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] でサポートされている SRID を `geography` インスタンスで使用する必要があります </span><span class="sxs-lookup"><span data-stu-id="2b572-255">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-supported SRID for `geography` instances must be used when performing calculations or using methods with geography spatial data.</span></span> <span data-ttu-id="2b572-256">その SRID が、 **sys.spatial_reference_systems** カタログ ビューに表示される SRID のいずれかに一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2b572-256">The SRID must match one of the SRIDs displayed in the **sys.spatial_reference_systems** catalog view.</span></span> <span data-ttu-id="2b572-257">既に説明したように、`geography` データ型を使用して空間データの計算を実行する場合、計算結果は、データの作成に使用された楕円体によって異なります。これは、各楕円体に特定の SRID (spatial reference identifier) が割り当てられているからです。</span><span class="sxs-lookup"><span data-stu-id="2b572-257">As mentioned previously, when you perform calculations on your spatial data using the `geography` data type, your results will depend on which ellipsoid was used in the creation of your data, as each ellipsoid is assigned a specific spatial reference identifier (SRID).</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="2b572-258">で使用される既定の SRID は 4326 です。SRID 4326 は、`geography` インスタンスのメソッドを使用する際に WGS 84 空間参照系にマップされます。</span><span class="sxs-lookup"><span data-stu-id="2b572-258">uses the default SRID of 4326, which maps to the WGS 84 spatial reference system, when using methods on `geography` instances.</span></span> <span data-ttu-id="2b572-259">WGS 84 (SRID 4326) 以外の空間参照系のデータを使用する場合は、その地理空間データの SRID を確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2b572-259">If you use data from a spatial reference system other than WGS 84 (or SRID 4326), you will need to determine the specific SRID for your geography spatial data.</span></span>  
  
##  <a name="examples"></a><a name="examples"></a> <span data-ttu-id="2b572-260">使用例</span><span class="sxs-lookup"><span data-stu-id="2b572-260">Examples</span></span>  
 <span data-ttu-id="2b572-261">次の例は、geography 型のデータの追加方法とクエリ方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="2b572-261">The following examples show how to add and query geography data.</span></span>  
  
-   <span data-ttu-id="2b572-262">最初の例では、ID 列と `geography` 型の `GeogCol1`列を含むテーブルを作成します。</span><span class="sxs-lookup"><span data-stu-id="2b572-262">The first example creates a table with an identity column and a `geography` column `GeogCol1`.</span></span> <span data-ttu-id="2b572-263">3 番目の列で、 `geography` 型の列をその Open Geospatial Consortium (OGC) の Well-Known Text (WKT) 表現で示し、 `STAsText()` メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="2b572-263">A third column renders the `geography` column into its Open Geospatial Consortium (OGC) Well-Known Text (WKT) representation, and uses the `STAsText()` method.</span></span> <span data-ttu-id="2b572-264">次に 2 つの行が挿入されます。1 つは、 `LineString` の `geography`インスタンスを含む行で、もう 1 つは `Polygon` インスタンスを含む行です。</span><span class="sxs-lookup"><span data-stu-id="2b572-264">Two rows are then inserted: one row contains a `LineString` instance of `geography`, and one row contains a `Polygon` instance.</span></span>  
  
    ```  
    IF OBJECT_ID ( 'dbo.SpatialTable', 'U' ) IS NOT NULL   
        DROP TABLE dbo.SpatialTable;  
    GO  
  
    CREATE TABLE SpatialTable   
        ( id int IDENTITY (1,1),  
        GeogCol1 geography,   
        GeogCol2 AS GeogCol1.STAsText() );  
    GO  
  
    INSERT INTO SpatialTable (GeogCol1)  
    VALUES (geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326));  
  
    INSERT INTO SpatialTable (GeogCol1)  
    VALUES (geography::STGeomFromText('POLYGON((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))', 4326));  
    GO  
    ```  
  
-   <span data-ttu-id="2b572-265">2 番目の例では、 `STIntersection()` メソッドを使用して、前の例で挿入した 2 つの `geography` インスタンスが交差する点を返します。</span><span class="sxs-lookup"><span data-stu-id="2b572-265">The second example uses the `STIntersection()` method to return the points where the two previously inserted `geography` instances intersect.</span></span>  
  
    ```  
    DECLARE @geog1 geography;  
    DECLARE @geog2 geography;  
    DECLARE @result geography;  
  
    SELECT @geog1 = GeogCol1 FROM SpatialTable WHERE id = 1;  
    SELECT @geog2 = GeogCol1 FROM SpatialTable WHERE id = 2;  
    SELECT @result = @geog1.STIntersection(@geog2);  
    SELECT @result.STAsText();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="2b572-266">参照</span><span class="sxs-lookup"><span data-stu-id="2b572-266">See Also</span></span>  
 [<span data-ttu-id="2b572-267">空間データ &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="2b572-267">Spatial Data &#40;SQL Server&#41;</span></span>](spatial-data-sql-server.md)  
  
  
