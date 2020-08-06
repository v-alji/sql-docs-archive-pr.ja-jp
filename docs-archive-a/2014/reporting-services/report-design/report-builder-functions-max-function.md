---
title: Max 関数 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 61c4d6ff-6435-456a-9cbd-5113d2113e8a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 03cea448500a6219fef5c04f1cea528ddc11f693
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640671"
---
# <a name="max-function-report-builder-and-ssrs"></a><span data-ttu-id="b868e-102">Max 関数 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="b868e-102">Max Function (Report Builder and SSRS)</span></span>
  <span data-ttu-id="b868e-103">指定されたスコープのコンテキストで、式で指定された NULL 以外のすべての数値の中から最大値を返します。</span><span class="sxs-lookup"><span data-stu-id="b868e-103">Returns the maximum value of all non-null numeric values specified by the expression, in the context of the given scope.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a><span data-ttu-id="b868e-104">構文</span><span class="sxs-lookup"><span data-stu-id="b868e-104">Syntax</span></span>  
  
```  
  
Max(expression, scope, recursive)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b868e-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b868e-105">Parameters</span></span>  
 <span data-ttu-id="b868e-106">*式 (expression)*</span><span class="sxs-lookup"><span data-stu-id="b868e-106">*expression*</span></span>  
 <span data-ttu-id="b868e-107">(`Variant`) この集計関数の実行対象の式です。</span><span class="sxs-lookup"><span data-stu-id="b868e-107">(`Variant`) The expression on which to perform the aggregation.</span></span>  
  
 <span data-ttu-id="b868e-108">*スコープ (scope)*</span><span class="sxs-lookup"><span data-stu-id="b868e-108">*scope*</span></span>  
 <span data-ttu-id="b868e-109">(`String`) 省略可。</span><span class="sxs-lookup"><span data-stu-id="b868e-109">(`String`) Optional.</span></span> <span data-ttu-id="b868e-110">集計関数の適用先となるレポート アイテムを含むデータセット、グループ、またはデータ領域の名前です。</span><span class="sxs-lookup"><span data-stu-id="b868e-110">The name of a dataset, group, or data region that contains the report items to which to apply the aggregate function.</span></span> <span data-ttu-id="b868e-111">*scope* を指定しない場合、現在のスコープが使用されます。</span><span class="sxs-lookup"><span data-stu-id="b868e-111">If *scope* is not specified, the current scope is used.</span></span>  
  
 <span data-ttu-id="b868e-112">*再帰*</span><span class="sxs-lookup"><span data-stu-id="b868e-112">*recursive*</span></span>  
 <span data-ttu-id="b868e-113">(**列挙型**) 省略可。</span><span class="sxs-lookup"><span data-stu-id="b868e-113">(**Enumerated Type**) Optional.</span></span> <span data-ttu-id="b868e-114">`Simple` (既定値) または `RdlRecursive` です。</span><span class="sxs-lookup"><span data-stu-id="b868e-114">`Simple` (default) or `RdlRecursive`.</span></span> <span data-ttu-id="b868e-115">集計を再帰的に実行するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="b868e-115">Specifies whether to perform the aggregation recursively.</span></span>  
  
## <a name="return-type"></a><span data-ttu-id="b868e-116">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="b868e-116">Return Type</span></span>  
 <span data-ttu-id="b868e-117">式の型によって決まります。</span><span class="sxs-lookup"><span data-stu-id="b868e-117">Determined by the type of the expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b868e-118">解説</span><span class="sxs-lookup"><span data-stu-id="b868e-118">Remarks</span></span>  
 <span data-ttu-id="b868e-119">式で指定されたデータセットは、同じデータ型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="b868e-119">The set of data specified in the expression must have the same data type.</span></span> <span data-ttu-id="b868e-120">複数の数値データ型のデータを同じデータ型に変換するには、`CInt`、`CDbl`、`CDec` などの変換関数を使用します。</span><span class="sxs-lookup"><span data-stu-id="b868e-120">To convert data that has multiple numeric data types to the same data type, use conversion functions like `CInt`, `CDbl` or `CDec`.</span></span> <span data-ttu-id="b868e-121">詳細については、「 [データ型変換関数](https://go.microsoft.com/fwlink/?LinkId=96142)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b868e-121">For more information, see [Type Conversion Functions](https://go.microsoft.com/fwlink/?LinkId=96142).</span></span>  
  
 <span data-ttu-id="b868e-122">*scope* の値は文字列定数である必要があり、式にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="b868e-122">The value of *scope* must be a string constant and cannot be an expression.</span></span> <span data-ttu-id="b868e-123">外部の集計または他の集計を指定しない集計では、 *scope* は現在のスコープまたはコンテナー スコープを参照する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b868e-123">For outer aggregates or aggregates that do not specify other aggregates, *scope* must refer to the current scope or a containing scope.</span></span> <span data-ttu-id="b868e-124">集計の集計では、入れ子になった集計に、子のスコープを指定できます。</span><span class="sxs-lookup"><span data-stu-id="b868e-124">For aggregates of aggregates, nested aggregates can specify a child scope.</span></span>  
  
 <span data-ttu-id="b868e-125">*Expression* には、入れ子になった集計関数への呼び出しを含めることができます。ただし、次に示すように、これには例外および条件があります。</span><span class="sxs-lookup"><span data-stu-id="b868e-125">*Expression* can contain calls to nested aggregate functions with the following exceptions and conditions:</span></span>  
  
-   <span data-ttu-id="b868e-126">入れ子集計の*Scope* は、外部集計のスコープと同じであるか、そのスコープに含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="b868e-126">*Scope* for nested aggregates must be the same as, or contained by, the scope of the outer aggregate.</span></span> <span data-ttu-id="b868e-127">式内のすべてのスコープについては、1 つのスコープがそれ以外のすべてのスコープに対する子であるようなリレーションシップが必要です。</span><span class="sxs-lookup"><span data-stu-id="b868e-127">For all distinct scopes in the expression, one scope must be in a child relationship to all other scopes.</span></span>  
  
-   <span data-ttu-id="b868e-128">入れ子集計の*Scope* には、データセット名は使用できません。</span><span class="sxs-lookup"><span data-stu-id="b868e-128">*Scope* for nested aggregates cannot be the name of a dataset.</span></span>  
  
-   <span data-ttu-id="b868e-129">*式*には、、、 `First` `Last` `Previous` 、または関数を含めることはできません `RunningValue` 。</span><span class="sxs-lookup"><span data-stu-id="b868e-129">*Expression* must not contain `First`, `Last`, `Previous`, or `RunningValue` functions.</span></span>  
  
-   <span data-ttu-id="b868e-130">*Expression* には、 *recursive*を指定する入れ子集計を含めることができません。</span><span class="sxs-lookup"><span data-stu-id="b868e-130">*Expression* must not contain nested aggregates that specify *recursive*.</span></span>  
  
 <span data-ttu-id="b868e-131">詳細については、「[集計関数リファレンス &#40;レポート ビルダーおよび SSRS&#41;](report-builder-functions-aggregate-functions-reference.md)」および「[合計、集計、および組み込みコレクションの式のスコープ &#40;レポート ビルダーおよび SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b868e-131">For more information, see [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) and [Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md).</span></span>  
  
 <span data-ttu-id="b868e-132">再帰的集計については、「[複数の再帰型階層グループの作成 &#40;レポート ビルダーおよび SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b868e-132">For more information about recursive aggregates, see [Creating Recursive Hierarchy Groups &#40;Report Builder and SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b868e-133">例</span><span class="sxs-lookup"><span data-stu-id="b868e-133">Example</span></span>  
 <span data-ttu-id="b868e-134">次のコード例では、 `Year` グループまたはデータ領域内の合計のうちの最大値が返されます。</span><span class="sxs-lookup"><span data-stu-id="b868e-134">The following code example provides the highest total in the `Year` group or data region.</span></span>  
  
```  
=Max(Fields!OrderTotal.Value, "Year")  
```  
  
## <a name="see-also"></a><span data-ttu-id="b868e-135">参照</span><span class="sxs-lookup"><span data-stu-id="b868e-135">See Also</span></span>  
 <span data-ttu-id="b868e-136">[レポートでの式の使用 (レポート ビルダーおよび SSRS)](expression-uses-in-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="b868e-136">[Expression Uses in Reports &#40;Report Builder and SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="b868e-137">[式の例 (レポート ビルダーおよび SSRS)](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="b868e-137">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="b868e-138">[式で使用されるデータ型 &#40;レポート ビルダーおよび SSRS&#41;](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="b868e-138">[Data Types in Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="b868e-139">合計、集計、および組み込みコレクションの式のスコープ (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="b868e-139">Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;</span></span>](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
