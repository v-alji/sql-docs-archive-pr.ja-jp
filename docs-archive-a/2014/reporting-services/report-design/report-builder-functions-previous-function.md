---
title: Previous 関数 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 403a9384-6ca4-42e8-97ca-ac3f6fe4316b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3891deec3f152cdf46da77a7f2d11d38387c5c8a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640666"
---
# <a name="previous-function-report-builder-and-ssrs"></a><span data-ttu-id="2ebe5-102">Previous 関数 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="2ebe5-102">Previous Function (Report Builder and SSRS)</span></span>
  <span data-ttu-id="2ebe5-103">アイテムの、指定されたスコープ内の直前のインスタンスに対応する値または指定された集計値を返します。</span><span class="sxs-lookup"><span data-stu-id="2ebe5-103">Returns the value or the specified aggregate value for the previous instance of an item within the specified scope.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a><span data-ttu-id="2ebe5-104">構文</span><span class="sxs-lookup"><span data-stu-id="2ebe5-104">Syntax</span></span>  
  
```  
  
Previous(expression, scope)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2ebe5-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2ebe5-105">Parameters</span></span>  
 <span data-ttu-id="2ebe5-106">*式 (expression)*</span><span class="sxs-lookup"><span data-stu-id="2ebe5-106">*expression*</span></span>  
 <span data-ttu-id="2ebe5-107">(`Variant` または `Binary`) データを識別し、直前の値を取得するための式 (`Fields!Fieldname.Value` や `Sum(Fields!Fieldname.Value)` など) です。</span><span class="sxs-lookup"><span data-stu-id="2ebe5-107">(`Variant` or `Binary`) The expression to use to identify the data and for which to retrieve the previous value, for example, `Fields!Fieldname.Value` or `Sum(Fields!Fieldname.Value)`.</span></span>  
  
 <span data-ttu-id="2ebe5-108">*スコープ (scope)*</span><span class="sxs-lookup"><span data-stu-id="2ebe5-108">*scope*</span></span>  
 <span data-ttu-id="2ebe5-109">(`String`) 省略可。</span><span class="sxs-lookup"><span data-stu-id="2ebe5-109">(`String`) Optional.</span></span> <span data-ttu-id="2ebe5-110">`Nothing` [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] *式*によって指定された前の値の取得元となるスコープを指定する、グループまたはデータ領域の名前、または null (では) です。</span><span class="sxs-lookup"><span data-stu-id="2ebe5-110">The name of a group or data region, or null (`Nothing` in [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]), that specifies the scope from which to retrieve the previous value specified by *expression*.</span></span>  
  
## <a name="return-type"></a><span data-ttu-id="2ebe5-111">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="2ebe5-111">Return Type</span></span>  
 <span data-ttu-id="2ebe5-112">`Variant` または `Binary` 値を返します。</span><span class="sxs-lookup"><span data-stu-id="2ebe5-112">Returns a `Variant` or `Binary`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2ebe5-113">解説</span><span class="sxs-lookup"><span data-stu-id="2ebe5-113">Remarks</span></span>  
 <span data-ttu-id="2ebe5-114">`Previous` 関数は、すべての並べ替えおよびフィルター処理が適用された後、指定されたスコープで評価された式の直前の値を返します。</span><span class="sxs-lookup"><span data-stu-id="2ebe5-114">The `Previous` function returns the previous value for the expression evaluated in the specified scope after all sorting and filtering have been applied.</span></span>  
  
 <span data-ttu-id="2ebe5-115">*式*に集計が含まれていない場合、 `Previous` 関数は既定でレポートアイテムの現在のスコープに設定されます。</span><span class="sxs-lookup"><span data-stu-id="2ebe5-115">If *expression* does not contain an aggregate, the `Previous` function defaults to the current scope for the report item.</span></span>  
  
 <span data-ttu-id="2ebe5-116">詳細グループで、直前の詳細行のフィールド参照の値を指定するには `Previous` を使用します。</span><span class="sxs-lookup"><span data-stu-id="2ebe5-116">In a details group, use `Previous` to specify the value of a field reference in the previous instance of the detail row.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2ebe5-117">関数は、 `Previous` 詳細グループ内のフィールド参照のみをサポートします。</span><span class="sxs-lookup"><span data-stu-id="2ebe5-117">The `Previous` function only supports field references in the details group.</span></span> <span data-ttu-id="2ebe5-118">たとえば、詳細グループのテキスト ボックスの場合、 `=Previous(Fields!Quantity.Value)` では、直前の行から `Quantity` フィールドのデータが返されます。</span><span class="sxs-lookup"><span data-stu-id="2ebe5-118">For example, in a text box in the details group, `=Previous(Fields!Quantity.Value)` returns the data for the field `Quantity` from the previous row.</span></span> <span data-ttu-id="2ebe5-119">この式が先頭行にある場合は、NULL ([!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] では `Nothing`) が返されます。</span><span class="sxs-lookup"><span data-stu-id="2ebe5-119">In the first row, this expression returns a null (`Nothing` in [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]).</span></span>  
  
 <span data-ttu-id="2ebe5-120">*Expression*に既定のスコープを使用する集計関数が含まれている場合、は、 `Previous` 集計関数の呼び出しで指定されたスコープの前のインスタンス内のデータを集計します。</span><span class="sxs-lookup"><span data-stu-id="2ebe5-120">If *expression* contains an aggregate function that uses a default scope, `Previous` aggregates the data within the previous instance of the scope specified in the aggregate function call.</span></span>  
  
 <span data-ttu-id="2ebe5-121">*Expression*に既定以外のスコープを指定する集計関数が含まれている場合、関数の*scope*パラメーターは、 `Previous` 集計関数の呼び出しで指定されたスコープのスコープを含んでいる必要があります。</span><span class="sxs-lookup"><span data-stu-id="2ebe5-121">If *expression* contains an aggregate function that specifies a scope other than the default, the *scope* parameter for the `Previous` function must be a containing scope for the scope specified in the aggregate function call.</span></span>  
  
 <span data-ttu-id="2ebe5-122">`Level` `InScope` 式パラメーターでは、、、および関数は `Aggregate` `Previous` 使用できません。 *expression*</span><span class="sxs-lookup"><span data-stu-id="2ebe5-122">The functions `Level`, `InScope`, `Aggregate` and `Previous` cannot be used in the *expression*parameter.</span></span> <span data-ttu-id="2ebe5-123">集計関数に *recursive* パラメーターを指定することはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="2ebe5-123">Specifying the *recursive* parameter for any aggregate function is not supported.</span></span>  
  
 <span data-ttu-id="2ebe5-124">詳細については、「[集計関数リファレンス &#40;レポート ビルダーおよび SSRS&#41;](report-builder-functions-aggregate-functions-reference.md)」および「[合計、集計、および組み込みコレクションの式のスコープ &#40;レポート ビルダーおよび SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2ebe5-124">For more information, see [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) and [Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="2ebe5-125">例</span><span class="sxs-lookup"><span data-stu-id="2ebe5-125">Examples</span></span>  
  
### <a name="description"></a><span data-ttu-id="2ebe5-126">説明</span><span class="sxs-lookup"><span data-stu-id="2ebe5-126">Description</span></span>  
 <span data-ttu-id="2ebe5-127">次のコード例は、データ領域の既定のデータ行に配置されると、直前の行の `LineTotal` フィールドの値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="2ebe5-127">The following code example, when placed in the default data row of a data region, provides the value for the field `LineTotal` in the previous row.</span></span>  
  
### <a name="code"></a><span data-ttu-id="2ebe5-128">コード</span><span class="sxs-lookup"><span data-stu-id="2ebe5-128">Code</span></span>  
  
```  
=Previous(Fields!LineTotal.Value)  
```  
  
### <a name="description"></a><span data-ttu-id="2ebe5-129">説明</span><span class="sxs-lookup"><span data-stu-id="2ebe5-129">Description</span></span>  
 <span data-ttu-id="2ebe5-130">次の例では、特定の月日の売上合計と、前年のその月日の値を計算する式を示します。</span><span class="sxs-lookup"><span data-stu-id="2ebe5-130">The following example shows an expression that calculates the sum of sales on a specific day of the month and the previous value for that day of the month in a previous year.</span></span> <span data-ttu-id="2ebe5-131">この式は、子グループ `GroupbyDay`に属する行内のセルに追加されます。</span><span class="sxs-lookup"><span data-stu-id="2ebe5-131">The expression is added to a cell in a row that belongs to the child group `GroupbyDay`.</span></span> <span data-ttu-id="2ebe5-132">その親グループは `GroupbyMonth`で、このグループの親グループは `GroupbyYear`です。</span><span class="sxs-lookup"><span data-stu-id="2ebe5-132">Its parent group is `GroupbyMonth`, which has a parent group `GroupbyYear`.</span></span> <span data-ttu-id="2ebe5-133">この式では、GroupbyDay (既定のスコープ) の結果、次に `GroupbyYear` (親グループ `GroupbyMonth`の親) の結果が表示されます。</span><span class="sxs-lookup"><span data-stu-id="2ebe5-133">The expression displays the results for GroupbyDay (the default scope) and then for `GroupbyYear` (the parent of the parent group `GroupbyMonth`).</span></span>  
  
 <span data-ttu-id="2ebe5-134">たとえば、親グループが `Year`、その子グループが `Month`、そのまた子グループが `Day` という名前のデータ領域 (入れ子レベル 3) の場合、</span><span class="sxs-lookup"><span data-stu-id="2ebe5-134">For example, for a data region with a parent group named `Year`, its child group named `Month`, and its child group named `Day` (3 nested levels).</span></span> <span data-ttu-id="2ebe5-135">グループ `=Previous(Sum(Fields!Sales.Value,"Day"),"Year")` に関連付けられた行内の式 `Day` は、前年の同じ月日の売上高の値を返します。</span><span class="sxs-lookup"><span data-stu-id="2ebe5-135">The expression `=Previous(Sum(Fields!Sales.Value,"Day"),"Year")` in a row associated with the group `Day` returns the sales value for the same day and month for the previous year.</span></span>  
  
### <a name="code"></a><span data-ttu-id="2ebe5-136">コード</span><span class="sxs-lookup"><span data-stu-id="2ebe5-136">Code</span></span>  
  
```  
=Sum(Fields!Sales.Value) & " " & Previous(Sum(Fields!Sales.Value,"GroupbyDay"),"GroupbyYear")  
```  
  
## <a name="see-also"></a><span data-ttu-id="2ebe5-137">参照</span><span class="sxs-lookup"><span data-stu-id="2ebe5-137">See Also</span></span>  
 <span data-ttu-id="2ebe5-138">[レポートでの式の使用 (レポート ビルダーおよび SSRS)](expression-uses-in-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="2ebe5-138">[Expression Uses in Reports &#40;Report Builder and SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="2ebe5-139">[式の例 (レポート ビルダーおよび SSRS)](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="2ebe5-139">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="2ebe5-140">[式で使用されるデータ型 &#40;レポート ビルダーおよび SSRS&#41;](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="2ebe5-140">[Data Types in Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="2ebe5-141">合計、集計、および組み込みコレクションの式のスコープ (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="2ebe5-141">Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;</span></span>](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
