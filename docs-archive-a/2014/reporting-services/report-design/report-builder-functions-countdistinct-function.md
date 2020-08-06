---
title: CountDistinct 関数 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 902c251e-e1e8-41d2-ac20-5bb6138ac410
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 62fab53d4f26a874ac40e0a915c4242a41c72ce0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640689"
---
# <a name="countdistinct-function-report-builder-and-ssrs"></a><span data-ttu-id="de3cb-102">CountDistinct 関数 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="de3cb-102">CountDistinct Function (Report Builder and SSRS)</span></span>
  <span data-ttu-id="de3cb-103">式で指定された NULL 以外の値が全部で何種類あるかを、指定されたスコープのコンテキストで評価して返します。</span><span class="sxs-lookup"><span data-stu-id="de3cb-103">Returns a count of all distinct non-null values specified by the expression, evaluated in the context of the given scope.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a><span data-ttu-id="de3cb-104">構文</span><span class="sxs-lookup"><span data-stu-id="de3cb-104">Syntax</span></span>  
  
```  
  
CountDistinct(expression, scope, recursive)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="de3cb-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="de3cb-105">Parameters</span></span>  
 <span data-ttu-id="de3cb-106">*式 (expression)*</span><span class="sxs-lookup"><span data-stu-id="de3cb-106">*expression*</span></span>  
 <span data-ttu-id="de3cb-107">(`Variant`) この集計関数の実行対象の式です。</span><span class="sxs-lookup"><span data-stu-id="de3cb-107">(`Variant`) The expression on which to perform the aggregation.</span></span>  
  
 <span data-ttu-id="de3cb-108">*スコープ (scope)*</span><span class="sxs-lookup"><span data-stu-id="de3cb-108">*scope*</span></span>  
 <span data-ttu-id="de3cb-109">(`String`) 省略可。</span><span class="sxs-lookup"><span data-stu-id="de3cb-109">(`String`) Optional.</span></span> <span data-ttu-id="de3cb-110">集計関数の適用先となるレポート アイテムを含むデータセット、グループ、またはデータ領域の名前です。</span><span class="sxs-lookup"><span data-stu-id="de3cb-110">The name of a dataset, group, or data region that contains the report items to which to apply the aggregate function.</span></span> <span data-ttu-id="de3cb-111">*scope* を指定しない場合、現在のスコープが使用されます。</span><span class="sxs-lookup"><span data-stu-id="de3cb-111">If *scope* is not specified, the current scope is used.</span></span>  
  
 <span data-ttu-id="de3cb-112">*再帰*</span><span class="sxs-lookup"><span data-stu-id="de3cb-112">*recursive*</span></span>  
 <span data-ttu-id="de3cb-113">(**列挙型**) 省略可。</span><span class="sxs-lookup"><span data-stu-id="de3cb-113">(**Enumerated Type**) Optional.</span></span> <span data-ttu-id="de3cb-114">`Simple` (既定値) または `RdlRecursive` です。</span><span class="sxs-lookup"><span data-stu-id="de3cb-114">`Simple` (default) or `RdlRecursive`.</span></span> <span data-ttu-id="de3cb-115">集計を再帰的に実行するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="de3cb-115">Specifies whether to perform the aggregation recursively.</span></span>  
  
## <a name="return-type"></a><span data-ttu-id="de3cb-116">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="de3cb-116">Return Type</span></span>  
 <span data-ttu-id="de3cb-117">`Integer` を返します。</span><span class="sxs-lookup"><span data-stu-id="de3cb-117">Returns an `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="de3cb-118">解説</span><span class="sxs-lookup"><span data-stu-id="de3cb-118">Remarks</span></span>  
 <span data-ttu-id="de3cb-119">*scope* の値は文字列定数である必要があり、式にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="de3cb-119">The value of *scope* must be a string constant and cannot be an expression.</span></span> <span data-ttu-id="de3cb-120">外部の集計または他の集計を指定しない集計では、 *scope* は現在のスコープまたはコンテナー スコープを参照する必要があります。</span><span class="sxs-lookup"><span data-stu-id="de3cb-120">For outer aggregates or aggregates that do not specify other aggregates, *scope* must refer to the current scope or a containing scope.</span></span> <span data-ttu-id="de3cb-121">集計の集計では、入れ子になった集計に、子のスコープを指定できます。</span><span class="sxs-lookup"><span data-stu-id="de3cb-121">For aggregates of aggregates, nested aggregates can specify a child scope.</span></span>  
  
 <span data-ttu-id="de3cb-122">*Expression* には、入れ子になった集計関数への呼び出しを含めることができます。ただし、次に示すように、これには例外および条件があります。</span><span class="sxs-lookup"><span data-stu-id="de3cb-122">*Expression* can contain calls to nested aggregate functions with the following exceptions and conditions:</span></span>  
  
-   <span data-ttu-id="de3cb-123">入れ子集計の*Scope* は、外部集計のスコープと同じであるか、そのスコープに含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="de3cb-123">*Scope* for nested aggregates must be the same as, or contained by, the scope of the outer aggregate.</span></span> <span data-ttu-id="de3cb-124">式内のすべてのスコープについては、1 つのスコープがそれ以外のすべてのスコープに対する子であるようなリレーションシップが必要です。</span><span class="sxs-lookup"><span data-stu-id="de3cb-124">For all distinct scopes in the expression, one scope must be in a child relationship to all other scopes.</span></span>  
  
-   <span data-ttu-id="de3cb-125">入れ子集計の*Scope* には、データセット名は使用できません。</span><span class="sxs-lookup"><span data-stu-id="de3cb-125">*Scope* for nested aggregates cannot be the name of a dataset.</span></span>  
  
-   <span data-ttu-id="de3cb-126">*式*には、、、 `First` `Last` `Previous` 、または関数を含めることはできません `RunningValue` 。</span><span class="sxs-lookup"><span data-stu-id="de3cb-126">*Expression* must not contain `First`, `Last`, `Previous`, or `RunningValue` functions.</span></span>  
  
-   <span data-ttu-id="de3cb-127">*Expression* には、 *recursive*を指定する入れ子集計を含めることができません。</span><span class="sxs-lookup"><span data-stu-id="de3cb-127">*Expression* must not contain nested aggregates that specify *recursive*.</span></span>  
  
 <span data-ttu-id="de3cb-128">詳細については、「[集計関数リファレンス &#40;レポート ビルダーおよび SSRS&#41;](report-builder-functions-aggregate-functions-reference.md)」および「[合計、集計、および組み込みコレクションの式のスコープ &#40;レポート ビルダーおよび SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="de3cb-128">For more information, see [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) and [Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md).</span></span>  
  
 <span data-ttu-id="de3cb-129">再帰的集計については、「[複数の再帰型階層グループの作成 &#40;レポート ビルダーおよび SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="de3cb-129">For more information about recursive aggregates, see [Creating Recursive Hierarchy Groups &#40;Report Builder and SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="de3cb-130">例</span><span class="sxs-lookup"><span data-stu-id="de3cb-130">Example</span></span>  
 <span data-ttu-id="de3cb-131">次のコード例では、既定のスコープおよび親グループのスコープで、 `Size` の NULL でない一意の値の数を計算する式を示します。</span><span class="sxs-lookup"><span data-stu-id="de3cb-131">The following code example shows an expression that calculates the number of unique non-null values of `Size` for the default scope and for a parent group scope.</span></span> <span data-ttu-id="de3cb-132">この式は、子グループ `GroupbySubcategory`に属する行内のセルに追加されます。</span><span class="sxs-lookup"><span data-stu-id="de3cb-132">The expression is added to a cell in a row that belongs to the child group `GroupbySubcategory`.</span></span> <span data-ttu-id="de3cb-133">親グループは `GroupbyCategory`です。</span><span class="sxs-lookup"><span data-stu-id="de3cb-133">The parent group is `GroupbyCategory`.</span></span> <span data-ttu-id="de3cb-134">この式では、 `GroupbySubcategory` (既定のスコープ) の結果、次に `GroupbyCategory` (親グループのスコープ) の結果が表示されます。</span><span class="sxs-lookup"><span data-stu-id="de3cb-134">The expression displays the results for `GroupbySubcategory` (the default scope) and then for `GroupbyCategory` (the parent group scope).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="de3cb-135">実際には、式に復帰と改行を含めないでください。サンプル コードでは、ドキュメントを読みやすくするためにこれらが含まれています。</span><span class="sxs-lookup"><span data-stu-id="de3cb-135">Expressions should not contain actual carriage returns and line breaks; these are included in the example code to support documentation renderers.</span></span> <span data-ttu-id="de3cb-136">次の例をコピーする場合は、各行の復帰を削除してください。</span><span class="sxs-lookup"><span data-stu-id="de3cb-136">If you copy the following example, remove carriage returns from each line.</span></span>  
  
```  
="Distinct count (Subcategory): " & CountDistinct(Fields!Size.Value) &   
"Distinct count (Category): " & CountDistinct(Fields!Size.Value,"GroupbyCategory")  
```  
  
## <a name="see-also"></a><span data-ttu-id="de3cb-137">参照</span><span class="sxs-lookup"><span data-stu-id="de3cb-137">See Also</span></span>  
 <span data-ttu-id="de3cb-138">[レポートでの式の使用 (レポート ビルダーおよび SSRS)](expression-uses-in-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="de3cb-138">[Expression Uses in Reports &#40;Report Builder and SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="de3cb-139">[式の例 (レポート ビルダーおよび SSRS)](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="de3cb-139">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="de3cb-140">[式で使用されるデータ型 &#40;レポート ビルダーおよび SSRS&#41;](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="de3cb-140">[Data Types in Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="de3cb-141">合計、集計、および組み込みコレクションの式のスコープ (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="de3cb-141">Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;</span></span>](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
