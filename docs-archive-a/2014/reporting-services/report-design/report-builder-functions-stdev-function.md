---
title: StDev 関数 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: cb51e96e-a828-42f0-b67c-cee3f4d221e7
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 58f913501c708b10ca01c24dd591d3378584afa5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640657"
---
# <a name="stdev-function-report-builder-and-ssrs"></a><span data-ttu-id="ff150-102">StDev 関数 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="ff150-102">StDev Function (Report Builder and SSRS)</span></span>
  <span data-ttu-id="ff150-103">式で指定された NULL 以外のすべての数値の標準偏差を、指定されたスコープで評価して返します。</span><span class="sxs-lookup"><span data-stu-id="ff150-103">Returns the standard deviation of all non-null numeric values specified by the expression, evaluated in the given scope.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a><span data-ttu-id="ff150-104">構文</span><span class="sxs-lookup"><span data-stu-id="ff150-104">Syntax</span></span>  
  
```  
  
StDev(expression, scope, recursive)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ff150-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff150-105">Parameters</span></span>  
 <span data-ttu-id="ff150-106">*式 (expression)*</span><span class="sxs-lookup"><span data-stu-id="ff150-106">*expression*</span></span>  
 <span data-ttu-id="ff150-107">(`Integer` または `Float`) この集計関数の実行対象の式です。</span><span class="sxs-lookup"><span data-stu-id="ff150-107">(`Integer` or `Float`) The expression on which to perform the aggregation.</span></span>  
  
 <span data-ttu-id="ff150-108">*スコープ (scope)*</span><span class="sxs-lookup"><span data-stu-id="ff150-108">*scope*</span></span>  
 <span data-ttu-id="ff150-109">(`String`) 省略可。</span><span class="sxs-lookup"><span data-stu-id="ff150-109">(`String`) Optional.</span></span> <span data-ttu-id="ff150-110">集計関数の適用先となるレポート アイテムを含むデータセット、グループ、またはデータ領域の名前です。</span><span class="sxs-lookup"><span data-stu-id="ff150-110">The name of a dataset, group, or data region that contains the report items to which to apply the aggregate function.</span></span> <span data-ttu-id="ff150-111">*scope* を指定しない場合、現在のスコープが使用されます。</span><span class="sxs-lookup"><span data-stu-id="ff150-111">If *scope* is not specified, the current scope is used.</span></span>  
  
 <span data-ttu-id="ff150-112">*再帰*</span><span class="sxs-lookup"><span data-stu-id="ff150-112">*recursive*</span></span>  
 <span data-ttu-id="ff150-113">(**列挙型**) 省略可。</span><span class="sxs-lookup"><span data-stu-id="ff150-113">(**Enumerated Type**) Optional.</span></span> <span data-ttu-id="ff150-114">`Simple` (既定値) または `RdlRecursive` です。</span><span class="sxs-lookup"><span data-stu-id="ff150-114">`Simple` (default) or `RdlRecursive`.</span></span> <span data-ttu-id="ff150-115">集計を再帰的に実行するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="ff150-115">Specifies whether to perform the aggregation recursively.</span></span>  
  
## <a name="return-type"></a><span data-ttu-id="ff150-116">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="ff150-116">Return Type</span></span>  
 <span data-ttu-id="ff150-117">10 進数型の式には `Decimal` 値が、その他すべての式には `Double` 値が返されます。</span><span class="sxs-lookup"><span data-stu-id="ff150-117">Returns a `Decimal` for decimal expressions and a `Double` for all other expressions.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ff150-118">解説</span><span class="sxs-lookup"><span data-stu-id="ff150-118">Remarks</span></span>  
 <span data-ttu-id="ff150-119">式で指定されたデータセットは、同じデータ型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="ff150-119">The set of data specified in the expression must have the same data type.</span></span> <span data-ttu-id="ff150-120">複数の数値データ型のデータを同じデータ型に変換するには、`CInt`、`CDbl`、`CDec` などの変換関数を使用します。</span><span class="sxs-lookup"><span data-stu-id="ff150-120">To convert data that has multiple numeric data types to the same data type, use conversion functions like `CInt`, `CDbl` or `CDec`.</span></span> <span data-ttu-id="ff150-121">詳細については、「 [データ型変換関数](https://go.microsoft.com/fwlink/?LinkId=96142)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ff150-121">For more information, see [Type Conversion Functions](https://go.microsoft.com/fwlink/?LinkId=96142).</span></span>  
  
 <span data-ttu-id="ff150-122">*scope* の値は文字列定数である必要があり、式にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="ff150-122">The value of *scope* must be a string constant and cannot be an expression.</span></span> <span data-ttu-id="ff150-123">外部の集計または他の集計を指定しない集計では、 *scope* は現在のスコープまたはコンテナー スコープを参照する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ff150-123">For outer aggregates or aggregates that do not specify other aggregates, *scope* must refer to the current scope or a containing scope.</span></span> <span data-ttu-id="ff150-124">集計の集計では、入れ子になった集計に、子のスコープを指定できます。</span><span class="sxs-lookup"><span data-stu-id="ff150-124">For aggregates of aggregates, nested aggregates can specify a child scope.</span></span>  
  
 <span data-ttu-id="ff150-125">*Expression* には、入れ子になった集計関数への呼び出しを含めることができます。ただし、次に示すように、これには例外および条件があります。</span><span class="sxs-lookup"><span data-stu-id="ff150-125">*Expression* can contain calls to nested aggregate functions with the following exceptions and conditions:</span></span>  
  
-   <span data-ttu-id="ff150-126">入れ子集計の*Scope* は、外部集計のスコープと同じであるか、そのスコープに含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="ff150-126">*Scope* for nested aggregates must be the same as, or contained by, the scope of the outer aggregate.</span></span> <span data-ttu-id="ff150-127">式内のすべてのスコープについては、1 つのスコープがそれ以外のすべてのスコープに対する子であるようなリレーションシップが必要です。</span><span class="sxs-lookup"><span data-stu-id="ff150-127">For all distinct scopes in the expression, one scope must be in a child relationship to all other scopes.</span></span>  
  
-   <span data-ttu-id="ff150-128">入れ子集計の*Scope* には、データセット名は使用できません。</span><span class="sxs-lookup"><span data-stu-id="ff150-128">*Scope* for nested aggregates cannot be the name of a dataset.</span></span>  
  
-   <span data-ttu-id="ff150-129">*式*には、、、 `First` `Last` `Previous` 、または関数を含めることはできません `RunningValue` 。</span><span class="sxs-lookup"><span data-stu-id="ff150-129">*Expression* must not contain `First`, `Last`, `Previous`, or `RunningValue` functions.</span></span>  
  
-   <span data-ttu-id="ff150-130">*Expression* には、 *recursive*を指定する入れ子集計を含めることができません。</span><span class="sxs-lookup"><span data-stu-id="ff150-130">*Expression* must not contain nested aggregates that specify *recursive*.</span></span>  
  
 <span data-ttu-id="ff150-131">詳細については、「[集計関数リファレンス &#40;レポート ビルダーおよび SSRS&#41;](report-builder-functions-aggregate-functions-reference.md)」および「[合計、集計、および組み込みコレクションの式のスコープ &#40;レポート ビルダーおよび SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ff150-131">For more information, see [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) and [Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md).</span></span>  
  
 <span data-ttu-id="ff150-132">再帰的集計については、「[複数の再帰型階層グループの作成 &#40;レポート ビルダーおよび SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ff150-132">For more information about recursive aggregates, see [Creating Recursive Hierarchy Groups &#40;Report Builder and SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ff150-133">例</span><span class="sxs-lookup"><span data-stu-id="ff150-133">Example</span></span>  
 <span data-ttu-id="ff150-134">次のコード例では、 `Order` グループまたはデータ領域の行アイテムの合計の標準偏差が返されます。</span><span class="sxs-lookup"><span data-stu-id="ff150-134">The following code example provides the standard deviation of line item totals in the `Order` group or data region.</span></span>  
  
```  
=StDev(Fields!LineTotal.Value, "Order")  
```  
  
## <a name="see-also"></a><span data-ttu-id="ff150-135">参照</span><span class="sxs-lookup"><span data-stu-id="ff150-135">See Also</span></span>  
 <span data-ttu-id="ff150-136">[レポートでの式の使用 (レポート ビルダーおよび SSRS)](expression-uses-in-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ff150-136">[Expression Uses in Reports &#40;Report Builder and SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="ff150-137">[式の例 (レポート ビルダーおよび SSRS)](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ff150-137">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="ff150-138">[式で使用されるデータ型 &#40;レポート ビルダーおよび SSRS&#41;](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ff150-138">[Data Types in Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="ff150-139">合計、集計、および組み込みコレクションの式のスコープ (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="ff150-139">Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;</span></span>](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  