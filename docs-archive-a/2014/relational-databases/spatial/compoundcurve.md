---
title: CompoundCurve | Microsoft Docs
ms.custom: ''
ms.date: 10/18/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: ae357f9b-e3e2-4cdf-af02-012acda2e466
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 6a899bbe9a17a64083592e1078e8cac93365f02b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632319"
---
# <a name="compoundcurve"></a><span data-ttu-id="d505d-102">CompoundCurve</span><span class="sxs-lookup"><span data-stu-id="d505d-102">CompoundCurve</span></span>
  <span data-ttu-id="d505d-103">`CompoundCurve` は、geometry 型または geography 型の 0 個以上の連続する `CircularString` インスタンスあるいは  `LineString` インスタンスのコレクションです。</span><span class="sxs-lookup"><span data-stu-id="d505d-103">A `CompoundCurve` is a collection of zero or more continuous `CircularString` or `LineString` instances of either geometry or geography types.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="d505d-104">サブタイプを含め、このリリースの新しい空間機能の詳細な説明と例については、 `CompoundCurve` ホワイトペーパー「 [SQL Server 2012 の新しい空間機能」](https://go.microsoft.com/fwlink/?LinkId=226407)をダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="d505d-104">For a detailed description and examples of the new spatial features in this release, including the `CompoundCurve` subtype, download the white paper, [New Spatial Features in SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=226407).</span></span>

 <span data-ttu-id="d505d-105">空の `CompoundCurve` インスタンスをインスタンス化することはできますが、`CompoundCurve` を有効にするには、次の条件を満たす必要があります。</span><span class="sxs-lookup"><span data-stu-id="d505d-105">An empty `CompoundCurve` instance can be instantiated, but for a `CompoundCurve` to be valid it must meet the following criteria:</span></span>

1.  <span data-ttu-id="d505d-106">1 つ以上の `CircularString` インスタンスまたは `LineString` インスタンスが含まれている。</span><span class="sxs-lookup"><span data-stu-id="d505d-106">It must contain at least one `CircularString` or `LineString` instance.</span></span>

2.  <span data-ttu-id="d505d-107">`CircularString` インスタンスまたは `LineString` インスタンスのシーケンスが連続している。</span><span class="sxs-lookup"><span data-stu-id="d505d-107">The sequence of `CircularString` or `LineString` instances must be continuous.</span></span>

 <span data-ttu-id="d505d-108">に `CompoundCurve` 複数のおよびインスタンスのシーケンスが含まれている場合 `CircularString` `LineString` 、最後のインスタンスを除くすべてのインスタンスの終了エンドポイントは、シーケンス内の次のインスタンスの開始エンドポイントである必要があります。</span><span class="sxs-lookup"><span data-stu-id="d505d-108">If a `CompoundCurve` contains a sequence of multiple `CircularString` and `LineString` instances, the ending endpoint for every instance except for the last instance must be the starting endpoint for the next instance in the sequence.</span></span> <span data-ttu-id="d505d-109">これは、シーケンス内の前のインスタンスの終点が (4 3 7 2) である場合は、シーケンス内の次のインスタンスの始点が (4 3 7 2) になる必要があることを意味します。</span><span class="sxs-lookup"><span data-stu-id="d505d-109">This means that if the ending point of a prior instance in the sequence is (4 3 7 2), the starting point for the next instance in the sequence must be (4 3 7 2).</span></span> <span data-ttu-id="d505d-110">点の Z (標高) 値および M (メジャー) 値も同じである必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="d505d-110">Note that Z(elevation) and M(measure) values for the point must also be the same.</span></span> <span data-ttu-id="d505d-111">これら 2 つの点が異なる場合は、 `System.FormatException` がスローされます。</span><span class="sxs-lookup"><span data-stu-id="d505d-111">If there is a difference in the two points, a `System.FormatException` is thrown.</span></span> <span data-ttu-id="d505d-112">`CircularString` の点は、Z 値または M 値を持つ必要はありません。</span><span class="sxs-lookup"><span data-stu-id="d505d-112">Points in a `CircularString` do not have to have a Z or M value.</span></span> <span data-ttu-id="d505d-113">前のインスタンスの終点に対して Z 値または M 値が指定されていない場合、次のインスタンスの始点には Z 値または M 値を含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="d505d-113">If no Z or M values are given for the ending point of the prior instance, the starting point of the next instance cannot include Z or M values.</span></span> <span data-ttu-id="d505d-114">前のシーケンスの終点が (4 3) である場合、次のシーケンスの始点は (4 3) となり、(4 3 7 2) を設定することはできません。</span><span class="sxs-lookup"><span data-stu-id="d505d-114">If the ending point for the prior sequence is (4 3), the starting point for the next sequence must be (4 3); it cannot be (4 3 7 2).</span></span> <span data-ttu-id="d505d-115">`CompoundCurve` インスタンスのすべての点は、Z 値をまったく持たないか、または同じ Z 値を持つ必要があります。</span><span class="sxs-lookup"><span data-stu-id="d505d-115">All points in a `CompoundCurve` instance must have either no Z value or the same Z value.</span></span>

## <a name="compoundcurve-instances"></a><span data-ttu-id="d505d-116">CompoundCurve インスタンス</span><span class="sxs-lookup"><span data-stu-id="d505d-116">CompoundCurve instances</span></span>
 <span data-ttu-id="d505d-117">次の図は、有効な `CompoundCurve` 型を示しています。</span><span class="sxs-lookup"><span data-stu-id="d505d-117">The following illustration shows valid `CompoundCurve` types.</span></span>

 ![](../../database-engine/media/f278742e-b861-4555-8b51-3d972b7602bf.png "f278742e-b861-4555-8b51-3d972b7602bf")

### <a name="accepted-instances"></a><span data-ttu-id="d505d-118">許容されるインスタンス</span><span class="sxs-lookup"><span data-stu-id="d505d-118">Accepted instances</span></span>
 <span data-ttu-id="d505d-119">`CompoundCurve` インスタンスは、空のインスタンスであるかまたは次の条件を満たす場合に許容されます。</span><span class="sxs-lookup"><span data-stu-id="d505d-119">`CompoundCurve` instance is accepted if it is an empty instance or meets the following criteria.</span></span>

1.  <span data-ttu-id="d505d-120">`CompoundCurve` インスタンスに含まれるすべてのインスタンスが、許容される円弧インスタンスである。</span><span class="sxs-lookup"><span data-stu-id="d505d-120">All the instances contained by `CompoundCurve` instance are accepted circular arc segment instances.</span></span> <span data-ttu-id="d505d-121">許容される円弧セグメントのインスタンスの詳細については、「 [LineString](linestring.md) 」および「 [CircularString](circularstring.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d505d-121">For more information on accepted circular arc segment instances, see [LineString](linestring.md) and [CircularString](circularstring.md).</span></span>

2.  <span data-ttu-id="d505d-122">`CompoundCurve` インスタンス内のすべての円弧が接続されている。</span><span class="sxs-lookup"><span data-stu-id="d505d-122">All of the circular arc segments in the `CompoundCurve` instance are connected.</span></span> <span data-ttu-id="d505d-123">後続のそれぞれの円弧の始点が、前の円弧の終点と同じである必要があります。</span><span class="sxs-lookup"><span data-stu-id="d505d-123">The first point for each succeeding circular arc segment is the same as the last point on the preceding circular arc segment.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="d505d-124">これには、Z 座標および M 座標が含まれます。</span><span class="sxs-lookup"><span data-stu-id="d505d-124">This includes the Z and M coordinates.</span></span> <span data-ttu-id="d505d-125">したがって、4 つの座標 (X、Y、Z、M) すべてが同じである必要があります。</span><span class="sxs-lookup"><span data-stu-id="d505d-125">So, all four coordinates X, Y, Z, and M must be the same.</span></span>

3.  <span data-ttu-id="d505d-126">含まれているすべてのインスタンスが、空のインスタンスではない。</span><span class="sxs-lookup"><span data-stu-id="d505d-126">None of the contained instances are empty instances.</span></span>

 <span data-ttu-id="d505d-127">次の例は、許容される `CompoundCurve` インスタンスを示しています。</span><span class="sxs-lookup"><span data-stu-id="d505d-127">The following example shows accepted `CompoundCurve` instances.</span></span>

```
DECLARE @g1 geometry = 'COMPOUNDCURVE EMPTY';
DECLARE @g2 geometry = 'COMPOUNDCURVE(CIRCULARSTRING(1 0, 0 1, -1 0), (-1 0, 2 0))';
```

 <span data-ttu-id="d505d-128">許容されない `CompoundCurve` インスタンスを次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="d505d-128">The following example shows `CompoundCurve` instances that are not accepted.</span></span> <span data-ttu-id="d505d-129">これらのインスタンスは、 `System.FormatException`をスローします。</span><span class="sxs-lookup"><span data-stu-id="d505d-129">These instances throw `System.FormatException`.</span></span>

```
DECLARE @g1 geometry = 'COMPOUNDCURVE(CIRCULARSTRING EMPTY)';
DECLARE @g2 geometry = 'COMPOUNDCURVE(CIRCULARSTRING(1 0, 0 1, -1 0), (1 0, 2 0))';
```

### <a name="valid-instances"></a><span data-ttu-id="d505d-130">有効なインスタンス</span><span class="sxs-lookup"><span data-stu-id="d505d-130">Valid instances</span></span>
 <span data-ttu-id="d505d-131">`CompoundCurve` インスタンスは、次の条件を満たす場合に有効です。</span><span class="sxs-lookup"><span data-stu-id="d505d-131">A `CompoundCurve` instance is valid if it meets the following criteria.</span></span>

1.  <span data-ttu-id="d505d-132">`CompoundCurve` インスタンスが許容されている。</span><span class="sxs-lookup"><span data-stu-id="d505d-132">The `CompoundCurve` instance is accepted.</span></span>

2.  <span data-ttu-id="d505d-133">`CompoundCurve` インスタンスに含まれるすべての円弧インスタンスが、有効なインスタンスである。</span><span class="sxs-lookup"><span data-stu-id="d505d-133">All circular arc segment instances contained by the `CompoundCurve` instance are valid instances.</span></span>

 <span data-ttu-id="d505d-134">次の例は、有効な `CompoundCurve` インスタンスを示しています。</span><span class="sxs-lookup"><span data-stu-id="d505d-134">The following example shows valid `CompoundCurve` instances.</span></span>

```
DECLARE @g1 geometry = 'COMPOUNDCURVE EMPTY';
DECLARE @g2 geometry = 'COMPOUNDCURVE(CIRCULARSTRING(1 0, 0 1, -1 0), (-1 0, 2 0))';
DECLARE @g3 geometry = 'COMPOUNDCURVE(CIRCULARSTRING(1 1, 1 1, 1 1), (1 1, 3 5, 5 4))';
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid();

```

 <span data-ttu-id="d505d-135">`@g3` は、`CircularString` インスタンスが有効であるため、有効です。</span><span class="sxs-lookup"><span data-stu-id="d505d-135">`@g3` is valid because the `CircularString` instance is valid.</span></span> <span data-ttu-id="d505d-136">インスタンスの有効性の詳細につい `CircularString` ては、「 [CircularString](circularstring.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d505d-136">For more information on the validity of the `CircularString` instance, see [CircularString](circularstring.md).</span></span>

 <span data-ttu-id="d505d-137">次の例は、無効な `CompoundCurve` インスタンスを示しています。</span><span class="sxs-lookup"><span data-stu-id="d505d-137">The following example shows `CompoundCurve` instances that are not valid.</span></span>

```
DECLARE @g1 geometry = 'COMPOUNDCURVE(CIRCULARSTRING(1 1, 1 1, 1 1), (1 1, 3 5, 5 4, 3 5))';
DECLARE @g2 geometry = 'COMPOUNDCURVE((1 1, 1 1))';
DECLARE @g3 geometry = 'COMPOUNDCURVE(CIRCULARSTRING(1 1, 2 3, 1 1))';
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid();
```

 <span data-ttu-id="d505d-138">`@g1` 2 番目のインスタンスが有効な LineString インスタンスではないため、無効です。</span><span class="sxs-lookup"><span data-stu-id="d505d-138">`@g1` is not valid because the second instance is not a valid LineString instance.</span></span> <span data-ttu-id="d505d-139">`@g2` は、`LineString` インスタンスが有効ではないため、無効です。</span><span class="sxs-lookup"><span data-stu-id="d505d-139">`@g2` is not valid because the `LineString` instance is not valid.</span></span> <span data-ttu-id="d505d-140">`@g3` は、`CircularString` インスタンスが有効ではないため、無効です。</span><span class="sxs-lookup"><span data-stu-id="d505d-140">`@g3` is not valid because the `CircularString` instance is not valid.</span></span> <span data-ttu-id="d505d-141">有効なおよびインスタンスの詳細につい `CircularString` `LineString` ては、「 [CircularString](circularstring.md) and [LineString](linestring.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d505d-141">For more information on valid `CircularString` and `LineString` instances, see [CircularString](circularstring.md) and [LineString](linestring.md).</span></span>

## <a name="examples"></a><span data-ttu-id="d505d-142">例</span><span class="sxs-lookup"><span data-stu-id="d505d-142">Examples</span></span>

### <a name="a-instantiating-a-geometry-instance-with-an-empty-compooundcurve"></a><span data-ttu-id="d505d-143">A.</span><span class="sxs-lookup"><span data-stu-id="d505d-143">A.</span></span> <span data-ttu-id="d505d-144">空の CompooundCurve を使用して geometry インスタンスをインスタンス化する</span><span class="sxs-lookup"><span data-stu-id="d505d-144">Instantiating a geometry instance with an empty CompooundCurve</span></span>
 <span data-ttu-id="d505d-145">次の例は、空の `CompoundCurve` インスタンスを作成する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="d505d-145">The following example shows how to create an empty `CompoundCurve` instance:</span></span>

```sql
DECLARE @g geometry;
SET @g = geometry::Parse('COMPOUNDCURVE EMPTY');
```

### <a name="b-declaring-and-instantiating-a-geometry-instance-using-a-compoundcurve-in-the-same-statement"></a><span data-ttu-id="d505d-146">B.</span><span class="sxs-lookup"><span data-stu-id="d505d-146">B.</span></span> <span data-ttu-id="d505d-147">CompoundCurve を同じステートメント内で使用して geometry インスタンスを宣言およびインスタンス化する</span><span class="sxs-lookup"><span data-stu-id="d505d-147">Declaring and instantiating a geometry instance using a CompoundCurve in the same statement</span></span>
 <span data-ttu-id="d505d-148">次の例は、 `geometry` を同じステートメント内で使用して `CompoundCurve`インスタンスを宣言および初期化する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="d505d-148">The following example shows how to declare and initialize a `geometry` instance with a `CompoundCurve`in the same statement:</span></span>

```sql
DECLARE @g geometry = 'COMPOUNDCURVE ((2 2, 0 0),CIRCULARSTRING (0 0, 1 2.1082, 3 6.3246, 0 7, -3 6.3246, -1 2.1082, 0 0))';
```

### <a name="c-instantiating-a-geography-instance-with-a-compoundcurve"></a><span data-ttu-id="d505d-149">C.</span><span class="sxs-lookup"><span data-stu-id="d505d-149">C.</span></span> <span data-ttu-id="d505d-150">CompoundCurve を使用して geography インスタンスをインスタンス化する</span><span class="sxs-lookup"><span data-stu-id="d505d-150">Instantiating a geography instance with a CompoundCurve</span></span>
 <span data-ttu-id="d505d-151">次の例は、`CompoundCurve` を使用して `geography` インスタンスを宣言およびインスタンス化する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="d505d-151">The following example shows how to declare and initialize a `geography` instance with a `CompoundCurve`:</span></span>

```sql
DECLARE @g geography = 'COMPOUNDCURVE(CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))';
```

### <a name="d-storing-a-square-in-a-compoundcurve-instance"></a><span data-ttu-id="d505d-152">D.</span><span class="sxs-lookup"><span data-stu-id="d505d-152">D.</span></span> <span data-ttu-id="d505d-153">CompoundCurve インスタンスに正方形を格納する</span><span class="sxs-lookup"><span data-stu-id="d505d-153">Storing a square in a CompoundCurve instance</span></span>
 <span data-ttu-id="d505d-154">次の例では、2 つの異なる方法で `CompoundCurve` インスタンスを使用して、正方形を格納しています。</span><span class="sxs-lookup"><span data-stu-id="d505d-154">The following example uses two different ways to use a `CompoundCurve` instance to store a square.</span></span>

```sql
DECLARE @g1 geometry, @g2 geometry;
SET @g1 = geometry::Parse('COMPOUNDCURVE((1 1, 1 3), (1 3, 3 3),(3 3, 3 1), (3 1, 1 1))');
SET @g2 = geometry::Parse('COMPOUNDCURVE((1 1, 1 3, 3 3, 3 1, 1 1))');
SELECT @g1.STLength(), @g2.STLength();
```

 <span data-ttu-id="d505d-155">`@g1` と `@g2` の長さは同じです。</span><span class="sxs-lookup"><span data-stu-id="d505d-155">The lengths for both `@g1` and `@g2` are the same.</span></span> <span data-ttu-id="d505d-156">この例に示すように、`CompoundCurve` インスタンスは、1 つまたは複数の `LineString` インスタンスを格納できます。</span><span class="sxs-lookup"><span data-stu-id="d505d-156">Notice from the example that a `CompoundCurve` instance can store one or more instances of `LineString`.</span></span>

### <a name="e-instantiating-a-geometry-instance-using-a-compoundcurve-with-multiple-circularstrings"></a><span data-ttu-id="d505d-157">E.</span><span class="sxs-lookup"><span data-stu-id="d505d-157">E.</span></span> <span data-ttu-id="d505d-158">複数の CircularString を含む CompoundCurve を使用して geometry インスタンスをインスタンス化する</span><span class="sxs-lookup"><span data-stu-id="d505d-158">Instantiating a geometry instance using a CompoundCurve with multiple CircularStrings</span></span>
 <span data-ttu-id="d505d-159">次の例は、2 つの異なる `CircularString` インスタンスを使用して `CompoundCurve`を初期化する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="d505d-159">The following example shows how to use two different `CircularString` instances to initialize a `CompoundCurve`.</span></span>

```sql
DECLARE @g geometry;
SET @g = geometry::Parse('COMPOUNDCURVE(CIRCULARSTRING(0 2, 2 0, 4 2), CIRCULARSTRING(4 2, 2 4, 0 2))');
SELECT @g.STLength();
```

 <span data-ttu-id="d505d-160">これにより、次の出力が生成されます。 12.566370...これは 4&#x03c0; (4 \* pi) に相当します。</span><span class="sxs-lookup"><span data-stu-id="d505d-160">This produces the following output: 12.566370... which is the equivalent of 4&#x03c0; (4 \* pi).</span></span> <span data-ttu-id="d505d-161">この例の `CompoundCurve` インスタンスは、半径が 2 の円を格納します。</span><span class="sxs-lookup"><span data-stu-id="d505d-161">The `CompoundCurve` instance in the example stores a circle with a radius of 2.</span></span> <span data-ttu-id="d505d-162">前のコード例のどちらの場合も、 `CompoundCurve`を使用する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="d505d-162">Both of the previous code examples did not have to use a `CompoundCurve`.</span></span> <span data-ttu-id="d505d-163">最初の例では `LineString` インスタンスを、2 番目の例では `CircularString` インスタンスをより単純化することができました。</span><span class="sxs-lookup"><span data-stu-id="d505d-163">For the first example a `LineString` instance would have been simpler, and a `CircularString` instance would have been simpler for the second example.</span></span> <span data-ttu-id="d505d-164">ただし、次の例は、 `CompoundCurve` がより優れた代替手段となるケースを示しています。</span><span class="sxs-lookup"><span data-stu-id="d505d-164">However, the next example shows where a `CompoundCurve` provides a better alternative.</span></span>

### <a name="f-using-a-compoundcurve-to-store-a-semicircle"></a><span data-ttu-id="d505d-165">F.</span><span class="sxs-lookup"><span data-stu-id="d505d-165">F.</span></span> <span data-ttu-id="d505d-166">CompoundCurve を使用して半円を格納する</span><span class="sxs-lookup"><span data-stu-id="d505d-166">Using a CompoundCurve to store a semicircle</span></span>
 <span data-ttu-id="d505d-167">次の例では、 `CompoundCurve` インスタンスを使用して半円を格納します。</span><span class="sxs-lookup"><span data-stu-id="d505d-167">The following example uses a `CompoundCurve` instance to store a semicircle.</span></span>

```sql
DECLARE @g geometry;
SET @g = geometry::Parse('COMPOUNDCURVE(CIRCULARSTRING(0 2, 2 0, 4 2), (4 2, 0 2))');
SELECT @g.STLength();
```

### <a name="g-storing-multiple-circularstring-and-linestring-instances-in-a-compoundcurve"></a><span data-ttu-id="d505d-168">G.</span><span class="sxs-lookup"><span data-stu-id="d505d-168">G.</span></span> <span data-ttu-id="d505d-169">CompoundCurve に複数の CircularString インスタンスおよび LineString インスタンスを格納する</span><span class="sxs-lookup"><span data-stu-id="d505d-169">Storing multiple CircularString and LineString instances in a CompoundCurve</span></span>
 <span data-ttu-id="d505d-170">次の例は、 `CircularString` インスタンスを使用して、複数の `LineString` インスタンスおよび `CompoundCurve`インスタンスを格納する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="d505d-170">The following example shows how multiple `CircularString` and `LineString` instances can be stored by using a `CompoundCurve`.</span></span>

```sql
DECLARE @g geometry
SET @g = geometry::Parse('COMPOUNDCURVE((3 5, 3 3), CIRCULARSTRING(3 3, 5 1, 7 3), (7 3, 7 5), CIRCULARSTRING(7 5, 5 7, 3 5))');
SELECT @g.STLength();
```

### <a name="h-storing-instances-with-z-and-m-values"></a><span data-ttu-id="d505d-171">H.</span><span class="sxs-lookup"><span data-stu-id="d505d-171">H.</span></span> <span data-ttu-id="d505d-172">Z 値および M 値を持つインスタンスを格納する</span><span class="sxs-lookup"><span data-stu-id="d505d-172">Storing instances with Z and M values</span></span>
 <span data-ttu-id="d505d-173">次の例は、 `CompoundCurve` インスタンスを使用して、Z 値と M 値の両方を持つ `CircularString` インスタンスおよび `LineString` インスタンスのシーケンスを格納する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="d505d-173">The following example shows how to use a `CompoundCurve` instance to store a sequence of `CircularString` and `LineString` instances with both Z and M values.</span></span>

```sql
SET @g = geometry::Parse('COMPOUNDCURVE(CIRCULARSTRING(7 5 4 2, 5 7 4 2, 3 5 4 2), (3 5 4 2, 8 7 4 2))');
```

### <a name="i-illustrating-why-circularstring-instances-must-be-explicitly-declared"></a><span data-ttu-id="d505d-174">I.</span><span class="sxs-lookup"><span data-stu-id="d505d-174">I.</span></span> <span data-ttu-id="d505d-175">CircularString インスタンスを明示的に宣言する必要がある理由を示す</span><span class="sxs-lookup"><span data-stu-id="d505d-175">Illustrating why CircularString instances must be explicitly declared</span></span>
 <span data-ttu-id="d505d-176">次の例は、 `CircularString` を明示的に宣言する必要がある理由を示しています。</span><span class="sxs-lookup"><span data-stu-id="d505d-176">The following example shows why `CircularString` instances must be explicitly declared.</span></span> <span data-ttu-id="d505d-177">この例では、円を `CompoundCurve` インスタンスに格納しようとしています。</span><span class="sxs-lookup"><span data-stu-id="d505d-177">The programmer is trying to store a circle in a `CompoundCurve` instance.</span></span>

```sql
DECLARE @g1 geometry;  
DECLARE @g2 geometry;
SET @g1 = geometry::Parse('COMPOUNDCURVE(CIRCULARSTRING(0 2, 2 0, 4 2), (4 2, 2 4, 0 2))');
SELECT 'Circle One', @g1.STLength() AS Perimeter;  -- gives an inaccurate amount
SET @g2 = geometry::Parse('COMPOUNDCURVE(CIRCULARSTRING(0 2, 2 0, 4 2), CIRCULARSTRING(4 2, 2 4, 0 2))');
SELECT 'Circle Two', @g2.STLength() AS Perimeter;  -- now we get an accurate amount
```

 <span data-ttu-id="d505d-178">出力は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="d505d-178">The output is as follows:</span></span>

```
Circle One11.940039...
Circle Two12.566370...
```

 <span data-ttu-id="d505d-179">円2の境界は約 4&#x03c0; (4 \* pi) で、これは境界の実際の値です。</span><span class="sxs-lookup"><span data-stu-id="d505d-179">The perimeter for Circle Two is approximately 4&#x03c0; (4 \* pi), which is the actual value for the perimeter.</span></span> <span data-ttu-id="d505d-180">ただし、Circle One の境界はきわめて不正確です。</span><span class="sxs-lookup"><span data-stu-id="d505d-180">However, the perimeter for Circle One is significantly inaccurate.</span></span> <span data-ttu-id="d505d-181">Circle One の `CompoundCurve` インスタンスは、1 つの円弧 (ABC) と 2 つの線分 (CD、DA) を格納します。</span><span class="sxs-lookup"><span data-stu-id="d505d-181">Circle One's `CompoundCurve` instance stores one circular arc segment (ABC) and two line segments (CD, DA).</span></span> <span data-ttu-id="d505d-182">`CompoundCurve` インスタンスは、円を定義するために 2 つの円弧 (ABC、CDA) を格納する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d505d-182">The `CompoundCurve` instance has to store two circular arc segments (ABC, CDA) to define a circle.</span></span> <span data-ttu-id="d505d-183">`LineString` インスタンスは、2 番目の点のセット (4 2, 2 4, 0 2) を Circle One の `CompoundCurve` インスタンスに定義します。</span><span class="sxs-lookup"><span data-stu-id="d505d-183">A `LineString` instance defines the second set of points (4 2, 2 4, 0 2) in Circle One's `CompoundCurve` instance.</span></span> <span data-ttu-id="d505d-184">ここで、 `CircularString` 内の `CompoundCurve`インスタンスを明示的に宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d505d-184">You have to explicitly declare a `CircularString` instance inside a `CompoundCurve`.</span></span>

## <a name="see-also"></a><span data-ttu-id="d505d-185">参照</span><span class="sxs-lookup"><span data-stu-id="d505d-185">See Also</span></span>
 <span data-ttu-id="d505d-186">[Stisvalid &#40;Geometry データ型&#41;](/sql/t-sql/spatial-geometry/stisvalid-geometry-data-type) [stisvalid &#40;geometry データ型&#41;](/sql/t-sql/spatial-geometry/stlength-geometry-data-type) [STStartPoint &#40;geometry データ型&#41;](/sql/t-sql/spatial-geometry/ststartpoint-geometry-data-type) [stisvalid &#40;Geometry データ](/sql/t-sql/spatial-geometry/stendpoint-geometry-data-type)型&#41;[LineString](linestring.md) [CircularString](circularstring.md) [空間データ型の概要](spatial-data-types-overview.md)[ポイント](point.md)</span><span class="sxs-lookup"><span data-stu-id="d505d-186">[STIsValid &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stisvalid-geometry-data-type) [STLength &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stlength-geometry-data-type) [STStartPoint &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/ststartpoint-geometry-data-type) [STEndpoint &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stendpoint-geometry-data-type) [LineString](linestring.md) [CircularString](circularstring.md) [Spatial Data Types Overview](spatial-data-types-overview.md) [Point](point.md)</span></span>


