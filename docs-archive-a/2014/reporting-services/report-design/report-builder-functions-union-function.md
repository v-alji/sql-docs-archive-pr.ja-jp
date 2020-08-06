---
title: Union 関数 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: c87e16fe-c12a-4c9d-a9df-7a94e229fd04
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c80926be53254ec512b2189c4b67e8cd5885733f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640653"
---
# <a name="union-function-report-builder-and-ssrs"></a><span data-ttu-id="d5edd-102">Union 関数 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="d5edd-102">Union Function (Report Builder and SSRS)</span></span>
  <span data-ttu-id="d5edd-103">式で指定された NULL 以外のすべての数値の結合を、指定されたスコープで評価して返します。</span><span class="sxs-lookup"><span data-stu-id="d5edd-103">Returns the union of all the non-null numeric values specified by the expression, evaluated in the given scope.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a><span data-ttu-id="d5edd-104">構文</span><span class="sxs-lookup"><span data-stu-id="d5edd-104">Syntax</span></span>  
  
```  
  
Union(expression, scope, recursive)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d5edd-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d5edd-105">Parameters</span></span>  
 <span data-ttu-id="d5edd-106">*式 (expression)*</span><span class="sxs-lookup"><span data-stu-id="d5edd-106">*expression*</span></span>  
 <span data-ttu-id="d5edd-107">(`SqlGeometry` または `SqlGeography`) この集計関数の実行対象の式です。</span><span class="sxs-lookup"><span data-stu-id="d5edd-107">(`SqlGeometry` or `SqlGeography`) The expression on which to perform the aggregation.</span></span>  
  
 <span data-ttu-id="d5edd-108">*スコープ (scope)*</span><span class="sxs-lookup"><span data-stu-id="d5edd-108">*scope*</span></span>  
 <span data-ttu-id="d5edd-109">(`String`) 省略可。</span><span class="sxs-lookup"><span data-stu-id="d5edd-109">(`String`) Optional.</span></span> <span data-ttu-id="d5edd-110">集計関数の適用先となるレポート アイテムを含むデータセット、グループ、またはデータ領域の名前です。</span><span class="sxs-lookup"><span data-stu-id="d5edd-110">The name of a dataset, group, or data region that contains the report items to which to apply the aggregate function.</span></span> <span data-ttu-id="d5edd-111">*scope* を指定しない場合、現在のスコープが使用されます。</span><span class="sxs-lookup"><span data-stu-id="d5edd-111">If *scope* is not specified, the current scope is used.</span></span>  
  
 <span data-ttu-id="d5edd-112">*再帰*</span><span class="sxs-lookup"><span data-stu-id="d5edd-112">*recursive*</span></span>  
 <span data-ttu-id="d5edd-113">(**列挙型**) 省略可。</span><span class="sxs-lookup"><span data-stu-id="d5edd-113">(**Enumerated Type**) Optional.</span></span> <span data-ttu-id="d5edd-114">`Simple` (既定値) または `RdlRecursive` です。</span><span class="sxs-lookup"><span data-stu-id="d5edd-114">`Simple` (default) or `RdlRecursive`.</span></span> <span data-ttu-id="d5edd-115">集計を再帰的に実行するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="d5edd-115">Specifies whether to perform the aggregation recursively.</span></span>  
  
## <a name="return"></a><span data-ttu-id="d5edd-116">戻り値</span><span class="sxs-lookup"><span data-stu-id="d5edd-116">Return</span></span>  
 <span data-ttu-id="d5edd-117">`SqlGeometry`式の型に基づいて、またはのいずれかの空間オブジェクトを返し `SqlGeography` ます。</span><span class="sxs-lookup"><span data-stu-id="d5edd-117">Returns a spatial object, either `SqlGeometry` or `SqlGeography`, based on the expression type.</span></span> <span data-ttu-id="d5edd-118">および空間データ型の詳細について `SqlGeometry` `SqlGeography` は、「[空間データ型の概要](../../relational-databases/spatial/spatial-data-types-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d5edd-118">For more information about `SqlGeometry` and `SqlGeography` spatial data types, see [Spatial Data Types Overview](../../relational-databases/spatial/spatial-data-types-overview.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d5edd-119">解説</span><span class="sxs-lookup"><span data-stu-id="d5edd-119">Remarks</span></span>  
 <span data-ttu-id="d5edd-120">式で指定されたデータセットは、同じデータ型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="d5edd-120">The set of data specified in the expression must have the same data type.</span></span>  
  
 <span data-ttu-id="d5edd-121">*scope* の値は文字列定数である必要があり、式にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="d5edd-121">The value of *scope* must be a string constant and cannot be an expression.</span></span> <span data-ttu-id="d5edd-122">外部の集計または他の集計を指定しない集計では、 *scope* は現在のスコープまたはコンテナー スコープを参照する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d5edd-122">For outer aggregates or aggregates that do not specify other aggregates, *scope* must refer to the current scope or a containing scope.</span></span> <span data-ttu-id="d5edd-123">データセットのスコープはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="d5edd-123">Dataset scopes are not supported.</span></span> <span data-ttu-id="d5edd-124">集計の集計では、入れ子になった集計に、子のスコープを指定できます。</span><span class="sxs-lookup"><span data-stu-id="d5edd-124">For aggregates of aggregates, nested aggregates can specify a child scope.</span></span>  
  
 <span data-ttu-id="d5edd-125">*Expression* には、入れ子になった集計関数への呼び出しを含めることができます。ただし、次に示すように、これには例外および条件があります。</span><span class="sxs-lookup"><span data-stu-id="d5edd-125">*Expression* can contain calls to nested aggregate functions with the following exceptions and conditions:</span></span>  
  
-   <span data-ttu-id="d5edd-126">入れ子集計の*Scope* は、外部集計のスコープと同じであるか、そのスコープに含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="d5edd-126">*Scope* for nested aggregates must be the same as, or contained by, the scope of the outer aggregate.</span></span> <span data-ttu-id="d5edd-127">式内のすべてのスコープについては、1 つのスコープがそれ以外のすべてのスコープに対する子であるようなリレーションシップが必要です。</span><span class="sxs-lookup"><span data-stu-id="d5edd-127">For all distinct scopes in the expression, one scope must be in a child relationship to all other scopes.</span></span>  
  
-   <span data-ttu-id="d5edd-128">入れ子集計の*Scope* には、データセット名は使用できません。</span><span class="sxs-lookup"><span data-stu-id="d5edd-128">*Scope* for nested aggregates cannot be the name of a dataset.</span></span>  
  
-   <span data-ttu-id="d5edd-129">*式*には、、、 `First` `Last` `Previous` 、または関数を含めることはできません `RunningValue` 。</span><span class="sxs-lookup"><span data-stu-id="d5edd-129">*Expression* must not contain `First`, `Last`, `Previous`, or `RunningValue` functions.</span></span>  
  
-   <span data-ttu-id="d5edd-130">*Expression* には、 *recursive*を指定する入れ子集計を含めることができません。</span><span class="sxs-lookup"><span data-stu-id="d5edd-130">*Expression* must not contain nested aggregates that specify *recursive*.</span></span>  
  
 <span data-ttu-id="d5edd-131">詳細については、「[集計関数リファレンス &#40;レポート ビルダーおよび SSRS&#41;](report-builder-functions-aggregate-functions-reference.md)」および「[合計、集計、および組み込みコレクションの式のスコープ &#40;レポート ビルダーおよび SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d5edd-131">For more information, see [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) and [Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md).</span></span>  
  
 <span data-ttu-id="d5edd-132">再帰的集計については、「[複数の再帰型階層グループの作成 &#40;レポート ビルダーおよび SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d5edd-132">For more information about recursive aggregates, see [Creating Recursive Hierarchy Groups &#40;Report Builder and SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d5edd-133">例</span><span class="sxs-lookup"><span data-stu-id="d5edd-133">Example</span></span>  
 <span data-ttu-id="d5edd-134">次の表に、`SqlGeometry` 式の例と、それに `Union` 式を適用した結果を、空間データ用の WKT (Well Known Text) 形式で示します。</span><span class="sxs-lookup"><span data-stu-id="d5edd-134">The following table shows examples of `SqlGeometry` expressions and `Union` result expression, shown in WKT (Well Known Text) format for spatial data.</span></span>  
  
|<span data-ttu-id="d5edd-135">空間データを含むフィールド</span><span class="sxs-lookup"><span data-stu-id="d5edd-135">Field with spatial data</span></span>|<span data-ttu-id="d5edd-136">例</span><span class="sxs-lookup"><span data-stu-id="d5edd-136">Example</span></span>|<span data-ttu-id="d5edd-137">Union の結果</span><span class="sxs-lookup"><span data-stu-id="d5edd-137">Union result</span></span>|  
|-----------------------------|-------------|------------------|  
|<span data-ttu-id="d5edd-138">[PointLocation]</span><span class="sxs-lookup"><span data-stu-id="d5edd-138">[PointLocation]</span></span>|<span data-ttu-id="d5edd-139">POINT(1 2)</span><span class="sxs-lookup"><span data-stu-id="d5edd-139">POINT(1 2)</span></span><br /><br /> <span data-ttu-id="d5edd-140">POINT(3 4)</span><span class="sxs-lookup"><span data-stu-id="d5edd-140">POINT(3 4)</span></span>|<span data-ttu-id="d5edd-141">MULTIPOINT((1 2), (3 4))</span><span class="sxs-lookup"><span data-stu-id="d5edd-141">MULTIPOINT((1 2), (3 4))</span></span>|  
|<span data-ttu-id="d5edd-142">[PathDefinition]</span><span class="sxs-lookup"><span data-stu-id="d5edd-142">[PathDefinition]</span></span>|<span data-ttu-id="d5edd-143">LINESTRING(1 2, 3 4)</span><span class="sxs-lookup"><span data-stu-id="d5edd-143">LINESTRING(1 2, 3 4)</span></span><br /><br /> <span data-ttu-id="d5edd-144">LINESTRING(5 6, 7 8)</span><span class="sxs-lookup"><span data-stu-id="d5edd-144">LINESTRING(5 6, 7 8)</span></span>|<span data-ttu-id="d5edd-145">MULTILINESTRING((7 8, 5 6), (3 4, 1 2))</span><span class="sxs-lookup"><span data-stu-id="d5edd-145">MULTILINESTRING((7 8, 5 6), (3 4, 1 2))</span></span>|  
|<span data-ttu-id="d5edd-146">[PolygonDefinition]</span><span class="sxs-lookup"><span data-stu-id="d5edd-146">[PolygonDefinition]</span></span>|<span data-ttu-id="d5edd-147">POLYGON((1 2, 3 4, 5 2, 1 2))</span><span class="sxs-lookup"><span data-stu-id="d5edd-147">POLYGON((1 2, 3 4, 5 2, 1 2))</span></span><br /><br /> <span data-ttu-id="d5edd-148">POLYGON((-1 2, -3 4, -5 2, -1 2))</span><span class="sxs-lookup"><span data-stu-id="d5edd-148">POLYGON((-1 2, -3 4, -5 2, -1 2))</span></span>|<span data-ttu-id="d5edd-149">MULTIPOLYGON(((1 2, 5 2, 3 4, 1 2)), ((-5 2, -1 2, -3 4, -5 2)))</span><span class="sxs-lookup"><span data-stu-id="d5edd-149">MULTIPOLYGON(((1 2, 5 2, 3 4, 1 2)), ((-5 2, -1 2, -3 4, -5 2)))</span></span>|  
  
```  
=Union(Fields!PointLocation.Value)  
=Union(Fields!PathDefinition.Value)  
=Union(Fields!PolygonDefinition.Value, "Group1")  
```  
  
## <a name="see-also"></a><span data-ttu-id="d5edd-150">参照</span><span class="sxs-lookup"><span data-stu-id="d5edd-150">See Also</span></span>  
 <span data-ttu-id="d5edd-151">[レポートでの式の使用 (レポート ビルダーおよび SSRS)](expression-uses-in-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="d5edd-151">[Expression Uses in Reports &#40;Report Builder and SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="d5edd-152">[式の例 (レポート ビルダーおよび SSRS)](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="d5edd-152">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="d5edd-153">[式で使用されるデータ型 &#40;レポート ビルダーおよび SSRS&#41;](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="d5edd-153">[Data Types in Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="d5edd-154">合計、集計、および組み込みコレクションの式のスコープ (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="d5edd-154">Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;</span></span>](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
