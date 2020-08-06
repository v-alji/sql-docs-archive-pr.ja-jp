---
title: RunningValue 関数 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 6bee2f15-0e69-49c8-9689-b04544063b1d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 168073a0409455041f4ebe3aa4c5dcfc8fa129a0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640658"
---
# <a name="runningvalue-function-report-builder-and-ssrs"></a><span data-ttu-id="a337d-102">RunningValue 関数 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="a337d-102">RunningValue Function (Report Builder and SSRS)</span></span>
  <span data-ttu-id="a337d-103">式で指定された NULL 以外のすべての数値の実行中の集計を、指定されたスコープに対して評価して返します。</span><span class="sxs-lookup"><span data-stu-id="a337d-103">Returns a running aggregate of all non-null numeric values specified by the expression, evaluated for the given scope.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a><span data-ttu-id="a337d-104">構文</span><span class="sxs-lookup"><span data-stu-id="a337d-104">Syntax</span></span>  
  
```  
  
RunningValue(expression, function, scope)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a337d-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a337d-105">Parameters</span></span>  
 <span data-ttu-id="a337d-106">*式 (expression)*</span><span class="sxs-lookup"><span data-stu-id="a337d-106">*expression*</span></span>  
 <span data-ttu-id="a337d-107">この集計関数の実行対象の式です ( `[Quantity]`など)。</span><span class="sxs-lookup"><span data-stu-id="a337d-107">The expression on which to perform the aggregation, for example, `[Quantity]`.</span></span>  
  
 <span data-ttu-id="a337d-108">*function*</span><span class="sxs-lookup"><span data-stu-id="a337d-108">*function*</span></span>  
 <span data-ttu-id="a337d-109">(`Enum`) 式に適用する集計関数の名前です (`Sum` など)。</span><span class="sxs-lookup"><span data-stu-id="a337d-109">(`Enum`) The name of the aggregate function to apply to the expression, for example, `Sum`.</span></span> <span data-ttu-id="a337d-110">この関数は、`RunningValue`、`RowNumber`、または `Aggregate` にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="a337d-110">This function cannot be `RunningValue`, `RowNumber`, or `Aggregate`.</span></span>  
  
 <span data-ttu-id="a337d-111">*スコープ (scope)*</span><span class="sxs-lookup"><span data-stu-id="a337d-111">*scope*</span></span>  
 <span data-ttu-id="a337d-112">(`String`) 集計を評価するコンテキストを示すデータセット、データ領域、またはグループの名前である文字列定数か、NULL ([!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] では `Nothing`) です。</span><span class="sxs-lookup"><span data-stu-id="a337d-112">(`String`) A string constant that is the name of a dataset, data region, or group, or null (`Nothing` in [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]), that specifies the context in which to evaluate the aggregation.</span></span> <span data-ttu-id="a337d-113">`Nothing` は、最も外側のコンテキスト (通常はレポート データセット) を示します。</span><span class="sxs-lookup"><span data-stu-id="a337d-113">`Nothing` specifies the outermost context, usually the report dataset.</span></span>  
  
## <a name="return-type"></a><span data-ttu-id="a337d-114">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="a337d-114">Return Type</span></span>  
 <span data-ttu-id="a337d-115">*function* パラメーターに指定された集計関数によって決まります。</span><span class="sxs-lookup"><span data-stu-id="a337d-115">Determined by the aggregate function that is specified in the *function* parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a337d-116">解説</span><span class="sxs-lookup"><span data-stu-id="a337d-116">Remarks</span></span>  
 <span data-ttu-id="a337d-117">`RunningValue` の値は、スコープの新しいインスタンスごとに 0 にリセットされます。</span><span class="sxs-lookup"><span data-stu-id="a337d-117">The value for `RunningValue` resets to 0 for each new instance of the scope.</span></span> <span data-ttu-id="a337d-118">グループが指定された場合は、累計値はグループ式の変更時にリセットされます。</span><span class="sxs-lookup"><span data-stu-id="a337d-118">If a group is specified, the running value is reset when the group expression changes.</span></span> <span data-ttu-id="a337d-119">データ領域が指定された場合は、累計値はデータ領域の新しいインスタンスごとにリセットされます。</span><span class="sxs-lookup"><span data-stu-id="a337d-119">If a data region is specified, the running value is reset for each new instance of the data region.</span></span> <span data-ttu-id="a337d-120">データセットが指定された場合は、累計値はデータセット全体にわたってリセットされません。</span><span class="sxs-lookup"><span data-stu-id="a337d-120">If a dataset is specified, the running value is not reset throughout the entire dataset.</span></span>  
  
 <span data-ttu-id="a337d-121">`RunningValue` は、フィルター式または並べ替え式では使用できません。</span><span class="sxs-lookup"><span data-stu-id="a337d-121">`RunningValue` cannot be used in a filter or sort expression.</span></span>  
  
 <span data-ttu-id="a337d-122">実行中の値が計算される一連のデータは、同じデータ型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="a337d-122">The set of data for which the running value is calculated must have the same data type.</span></span> <span data-ttu-id="a337d-123">複数の数値データ型のデータを同じデータ型に変換するには、`CInt`、`CDbl`、`CDec` などの変換関数を使用します。</span><span class="sxs-lookup"><span data-stu-id="a337d-123">To convert data that has multiple numeric data types to the same data type, use conversion functions like `CInt`, `CDbl` or `CDec`.</span></span> <span data-ttu-id="a337d-124">詳細については、「 [データ型変換関数](https://go.microsoft.com/fwlink/?LinkId=96142)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a337d-124">For more information, see [Type Conversion Functions](https://go.microsoft.com/fwlink/?LinkId=96142).</span></span>  
  
 <span data-ttu-id="a337d-125">*Scope* には、式を指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="a337d-125">*Scope* cannot be an expression.</span></span>  
  
 <span data-ttu-id="a337d-126">*Expression* には、入れ子になった集計関数への呼び出しを含めることができます。ただし、次に示すように、これには例外および条件があります。</span><span class="sxs-lookup"><span data-stu-id="a337d-126">*Expression* can contain calls to nested aggregate functions with the following exceptions and conditions:</span></span>  
  
-   <span data-ttu-id="a337d-127">入れ子集計のスコープは、外部集計のスコープと同じであるか、そのスコープに含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="a337d-127">Scope for nested aggregates must be the same as, or contained by, the scope of the outer aggregate.</span></span> <span data-ttu-id="a337d-128">式内のすべてのスコープについては、1 つのスコープがそれ以外のすべてのスコープに対する子であるようなリレーションシップが必要です。</span><span class="sxs-lookup"><span data-stu-id="a337d-128">For all distinct scopes in the expression, one scope must be in a child relationship to all other scopes.</span></span>  
  
-   <span data-ttu-id="a337d-129">入れ子集計のスコープには、データセット名は使用できません。</span><span class="sxs-lookup"><span data-stu-id="a337d-129">Scope for nested aggregates cannot be the name of a dataset.</span></span>  
  
-   <span data-ttu-id="a337d-130">*式*には、、、 `First` `Last` `Previous` 、または関数を含めることはできません `RunningValue` 。</span><span class="sxs-lookup"><span data-stu-id="a337d-130">*Expression* must not contain `First`, `Last`, `Previous`, or `RunningValue` functions.</span></span>  
  
-   <span data-ttu-id="a337d-131">*Expression* には、 *recursive*を指定する入れ子集計を含めることができません。</span><span class="sxs-lookup"><span data-stu-id="a337d-131">*Expression* must not contain nested aggregates that specify *recursive*.</span></span>  
  
 <span data-ttu-id="a337d-132">行数の累計値を計算するには、`RowNumber` を使用します。</span><span class="sxs-lookup"><span data-stu-id="a337d-132">To calculate the running value of the number of rows, use `RowNumber`.</span></span> <span data-ttu-id="a337d-133">詳細については、「[RowNumber 関数 &#40;レポート ビルダーおよび SSRS&#41;](report-builder-functions-rownumber-function.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a337d-133">For more information, see [RowNumber Function &#40;Report Builder and SSRS&#41;](report-builder-functions-rownumber-function.md).</span></span>  
  
 <span data-ttu-id="a337d-134">詳細については、「[集計関数リファレンス &#40;レポート ビルダーおよび SSRS&#41;](report-builder-functions-aggregate-functions-reference.md)」および「[合計、集計、および組み込みコレクションの式のスコープ &#40;レポート ビルダーおよび SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a337d-134">For more information, see [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) and [Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md).</span></span>  
  
 <span data-ttu-id="a337d-135">再帰的集計については、「[複数の再帰型階層グループの作成 &#40;レポート ビルダーおよび SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a337d-135">For more information about recursive aggregates, see [Creating Recursive Hierarchy Groups &#40;Report Builder and SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="a337d-136">例</span><span class="sxs-lookup"><span data-stu-id="a337d-136">Examples</span></span>  
 <span data-ttu-id="a337d-137">次のコード例では、最も外側のスコープ (データセット) の `Cost` フィールドの累計が返されます。</span><span class="sxs-lookup"><span data-stu-id="a337d-137">The following code example provides a running sum of the field named `Cost` in the outermost scope, which is the dataset.</span></span>  
  
```  
=RunningValue(Fields!Cost.Value, Sum, Nothing)  
```  
  
 <span data-ttu-id="a337d-138">次のコード例では、 `Score` データセットの `DataSet1`フィールドの累計が返されます。</span><span class="sxs-lookup"><span data-stu-id="a337d-138">The following code example provides a running sum of the field named `Score` in the dataset named `DataSet1`.</span></span>  
  
```  
=RunningValue(Fields!Score.Value,sum,"DataSet1")  
```  
  
 <span data-ttu-id="a337d-139">次のコード例では、最も外側のスコープの `Traffic Charges` フィールドの累計が返されます。</span><span class="sxs-lookup"><span data-stu-id="a337d-139">The following code example provides a running sum of the field named `Traffic Charges` in the outermost scope.</span></span>  
  
```  
=RunningValue(Fields!Traffic Charges.Value, Sum, Nothing)  
```  
  
## <a name="see-also"></a><span data-ttu-id="a337d-140">参照</span><span class="sxs-lookup"><span data-stu-id="a337d-140">See Also</span></span>  
 <span data-ttu-id="a337d-141">[レポートでの式の使用 (レポート ビルダーおよび SSRS)](expression-uses-in-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="a337d-141">[Expression Uses in Reports &#40;Report Builder and SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="a337d-142">[式の例 (レポート ビルダーおよび SSRS)](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="a337d-142">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="a337d-143">[式で使用されるデータ型 &#40;レポート ビルダーおよび SSRS&#41;](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="a337d-143">[Data Types in Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="a337d-144">合計、集計、および組み込みコレクションの式のスコープ (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="a337d-144">Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;</span></span>](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
