---
title: Last 関数 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 123b78a0-d6c9-4f78-b0e7-73b21854a250
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c343e72e476d4a717ca551eedeb0f02650479ca4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640677"
---
# <a name="last-function-report-builder-and-ssrs"></a><span data-ttu-id="ace7d-102">Last 関数 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="ace7d-102">Last Function (Report Builder and SSRS)</span></span>
  <span data-ttu-id="ace7d-103">指定された式の指定されたスコープの最後の値を返します。</span><span class="sxs-lookup"><span data-stu-id="ace7d-103">Returns the last value in the given scope of the specified expression.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a><span data-ttu-id="ace7d-104">構文</span><span class="sxs-lookup"><span data-stu-id="ace7d-104">Syntax</span></span>  
  
```  
  
Last(expression, scope)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ace7d-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ace7d-105">Parameters</span></span>  
 <span data-ttu-id="ace7d-106">*式 (expression)*</span><span class="sxs-lookup"><span data-stu-id="ace7d-106">*expression*</span></span>  
 <span data-ttu-id="ace7d-107">(`Variant` または `Binary`) この集計関数の実行対象の式です (`=Fields!Fieldname.Value` など)。</span><span class="sxs-lookup"><span data-stu-id="ace7d-107">(`Variant` or `Binary`) The expression on which to perform the aggregation, for example, `=Fields!Fieldname.Value`.</span></span>  
  
 <span data-ttu-id="ace7d-108">*スコープ (scope)*</span><span class="sxs-lookup"><span data-stu-id="ace7d-108">*scope*</span></span>  
 <span data-ttu-id="ace7d-109">(`String`) (省略可) この関数の適用先となるレポート アイテムを含むデータセット、データ領域、またはグループの名前です。</span><span class="sxs-lookup"><span data-stu-id="ace7d-109">(`String`) (Optional) The name of a dataset, data region, or group that contains the report items to which to apply the function.</span></span> <span data-ttu-id="ace7d-110">*scope* を指定しない場合、現在のスコープが使用されます。</span><span class="sxs-lookup"><span data-stu-id="ace7d-110">If *scope* is not specified, the current scope is used.</span></span>  
  
## <a name="return-type"></a><span data-ttu-id="ace7d-111">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="ace7d-111">Return Type</span></span>  
 <span data-ttu-id="ace7d-112">式の種類によって決まります。</span><span class="sxs-lookup"><span data-stu-id="ace7d-112">Determined by the type of expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ace7d-113">解説</span><span class="sxs-lookup"><span data-stu-id="ace7d-113">Remarks</span></span>  
 <span data-ttu-id="ace7d-114">`Last` 関数は、指定されたスコープですべての並べ替えおよびフィルター処理が適用された後、データセットの最後の値を返します。</span><span class="sxs-lookup"><span data-stu-id="ace7d-114">The `Last` function returns the final value in a set of data after all sorting and filtering have been applied at the specified scope.</span></span>  
  
 <span data-ttu-id="ace7d-115">`Last` 関数は、現在 (既定) のスコープ以外のスコープを使用してグループ化フィルター式で使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="ace7d-115">The `Last` function cannot be used in group filter expressions with anything except the current (default) scope.</span></span>  
  
 <span data-ttu-id="ace7d-116">また、ページ ヘッダーで `Last` を使用して、ページの `ReportItems` コレクションから最後の値を返し、各ページの最初と最後のエントリを表示する辞書形式のヘッダーを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="ace7d-116">You can also use `Last` in a page header to return the last value from the `ReportItems` collection for a page in order to produce dictionary-style headings that display the first and last entries on a page.</span></span>  
  
 <span data-ttu-id="ace7d-117">*scope* の値は文字列定数である必要があり、式にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="ace7d-117">The value of *scope* must be a string constant andcannot be an expression.</span></span> <span data-ttu-id="ace7d-118">外部の集計または他の集計を指定しない集計では、 *scope* は現在のスコープまたはコンテナー スコープを参照する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ace7d-118">For outer aggregates or aggregates that do not specify other aggregates, *scope* must refer to the current scope or a containing scope.</span></span> <span data-ttu-id="ace7d-119">集計の集計では、入れ子になった集計に、子のスコープを指定できます。</span><span class="sxs-lookup"><span data-stu-id="ace7d-119">For aggregates of aggregates, nested aggregates can specify a child scope.</span></span>  
  
 <span data-ttu-id="ace7d-120">*Expression* には、入れ子になった集計関数への呼び出しを含めることができます。ただし、次に示すように、これには例外および条件があります。</span><span class="sxs-lookup"><span data-stu-id="ace7d-120">*Expression* can contain calls to nested aggregate functions with the following exceptions and conditions:</span></span>  
  
-   <span data-ttu-id="ace7d-121">入れ子集計の*Scope* は、外部集計のスコープと同じであるか、そのスコープに含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="ace7d-121">*Scope* for nested aggregates must be the same as, or contained by, the scope of the outer aggregate.</span></span> <span data-ttu-id="ace7d-122">式内のすべてのスコープについては、1 つのスコープがそれ以外のすべてのスコープに対する子であるようなリレーションシップが必要です。</span><span class="sxs-lookup"><span data-stu-id="ace7d-122">For all distinct scopes in the expression, one scope must be in a child relationship to all other scopes.</span></span>  
  
-   <span data-ttu-id="ace7d-123">入れ子集計の*Scope* には、データセット名は使用できません。</span><span class="sxs-lookup"><span data-stu-id="ace7d-123">*Scope* for nested aggregates cannot be the name of a dataset.</span></span>  
  
-   <span data-ttu-id="ace7d-124">*式*には、、、 `First` `Last` `Previous` 、または関数を含めることはできません `RunningValue` 。</span><span class="sxs-lookup"><span data-stu-id="ace7d-124">*Expression* must not contain `First`, `Last`, `Previous`, or `RunningValue` functions.</span></span>  
  
-   <span data-ttu-id="ace7d-125">*Expression* には、 *recursive*を指定する入れ子集計を含めることができません。</span><span class="sxs-lookup"><span data-stu-id="ace7d-125">*Expression* must not contain nested aggregates that specify *recursive*.</span></span>  
  
 <span data-ttu-id="ace7d-126">詳細については、「[集計関数リファレンス &#40;レポート ビルダーおよび SSRS&#41;](report-builder-functions-aggregate-functions-reference.md)」および「[合計、集計、および組み込みコレクションの式のスコープ &#40;レポート ビルダーおよび SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ace7d-126">For more information, see [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) and [Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md).</span></span>  
  
 <span data-ttu-id="ace7d-127">再帰的集計については、「[複数の再帰型階層グループの作成 &#40;レポート ビルダーおよび SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ace7d-127">For more information about recursive aggregates, see [Creating Recursive Hierarchy Groups &#40;Report Builder and SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ace7d-128">例</span><span class="sxs-lookup"><span data-stu-id="ace7d-128">Example</span></span>  
 <span data-ttu-id="ace7d-129">次のコード例では、データ領域の `Category` グループの最後の製品番号が返されます。</span><span class="sxs-lookup"><span data-stu-id="ace7d-129">The following code example returns the last product number in the `Category` group of a data region.</span></span>  
  
```  
=Last(Fields!ProductNumber.Value, "Category")  
```  
  
## <a name="see-also"></a><span data-ttu-id="ace7d-130">参照</span><span class="sxs-lookup"><span data-stu-id="ace7d-130">See Also</span></span>  
 <span data-ttu-id="ace7d-131">[レポートでの式の使用 (レポート ビルダーおよび SSRS)](expression-uses-in-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ace7d-131">[Expression Uses in Reports &#40;Report Builder and SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="ace7d-132">[式の例 (レポート ビルダーおよび SSRS)](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ace7d-132">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="ace7d-133">[式で使用されるデータ型 &#40;レポート ビルダーおよび SSRS&#41;](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ace7d-133">[Data Types in Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="ace7d-134">合計、集計、および組み込みコレクションの式のスコープ (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="ace7d-134">Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;</span></span>](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
