---
title: First 関数 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: d0914520-30c5-4d63-9b59-8d9342ed63b9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2cd8578a1d9a17030d603457d4eaadf107316bdd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640680"
---
# <a name="first-function-report-builder-and-ssrs"></a><span data-ttu-id="52a8b-102">First 関数 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="52a8b-102">First Function (Report Builder and SSRS)</span></span>
  <span data-ttu-id="52a8b-103">指定された式の指定されたスコープの最初の値を返します。</span><span class="sxs-lookup"><span data-stu-id="52a8b-103">Returns the first value in the given scope of the specified expression.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a><span data-ttu-id="52a8b-104">構文</span><span class="sxs-lookup"><span data-stu-id="52a8b-104">Syntax</span></span>  
  
```  
  
First(expression, scope)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="52a8b-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="52a8b-105">Parameters</span></span>  
 <span data-ttu-id="52a8b-106">*式 (expression)*</span><span class="sxs-lookup"><span data-stu-id="52a8b-106">*expression*</span></span>  
 <span data-ttu-id="52a8b-107">(`Variant` または `Binary`) この集計関数の実行対象の式です (`=Fields!FieldName.Value` など)。</span><span class="sxs-lookup"><span data-stu-id="52a8b-107">(`Variant` or `Binary`) The expression on which to perform the aggregation, for example, `=Fields!FieldName.Value`.</span></span>  
  
 <span data-ttu-id="52a8b-108">*スコープ (scope)*</span><span class="sxs-lookup"><span data-stu-id="52a8b-108">*scope*</span></span>  
 <span data-ttu-id="52a8b-109">(`String`) 省略可。</span><span class="sxs-lookup"><span data-stu-id="52a8b-109">(`String`) Optional.</span></span> <span data-ttu-id="52a8b-110">集計関数の適用先となるレポート アイテムを含むデータセット、グループ、またはデータ領域の名前です。</span><span class="sxs-lookup"><span data-stu-id="52a8b-110">The name of a dataset, group, or data region that contains the report items to which to apply the aggregate function.</span></span> <span data-ttu-id="52a8b-111">*scope* を指定しない場合、現在のスコープが使用されます。</span><span class="sxs-lookup"><span data-stu-id="52a8b-111">If *scope* is not specified, the current scope is used.</span></span>  
  
## <a name="return-type"></a><span data-ttu-id="52a8b-112">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="52a8b-112">Return Type</span></span>  
 <span data-ttu-id="52a8b-113">式の種類によって決まります。</span><span class="sxs-lookup"><span data-stu-id="52a8b-113">Determined by the type of expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="52a8b-114">解説</span><span class="sxs-lookup"><span data-stu-id="52a8b-114">Remarks</span></span>  
 <span data-ttu-id="52a8b-115">`First` 関数は、指定されたスコープですべての並べ替えおよびフィルター処理が適用された後、データセットの最初の値を返します。</span><span class="sxs-lookup"><span data-stu-id="52a8b-115">The `First` function returns the first value in a set of data after all sorting and filtering have been applied at the specified scope.</span></span>  
  
 <span data-ttu-id="52a8b-116">`First` 関数は、現在 (既定) のスコープ以外のスコープを使用してグループ化フィルター式で使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="52a8b-116">The `First` function cannot be used in group filter expressions with anything except the current (default) scope.</span></span>  
  
 <span data-ttu-id="52a8b-117">また、ページ ヘッダーで `First` を使用して、ページの `ReportItems` コレクションから最初の値を返し、各ページの最初と最後のエントリを表示する辞書形式のヘッダーを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="52a8b-117">You can also use `First` in a page header to return the first value from the `ReportItems` collection for a page in order to produce dictionary-style headings that display the first and last entries on a page.</span></span>  
  
 <span data-ttu-id="52a8b-118">*scope* の値は文字列定数である必要があり、式にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="52a8b-118">The value of *scope* must be a string constant andcannot be an expression.</span></span> <span data-ttu-id="52a8b-119">外部の集計または他の集計を指定しない集計では、 *scope* は現在のスコープまたはコンテナー スコープを参照する必要があります。</span><span class="sxs-lookup"><span data-stu-id="52a8b-119">For outer aggregates or aggregates that do not specify other aggregates, *scope* must refer to the current scope or a containing scope.</span></span> <span data-ttu-id="52a8b-120">集計の集計では、入れ子になった集計に、子のスコープを指定できます。</span><span class="sxs-lookup"><span data-stu-id="52a8b-120">For aggregates of aggregates, nested aggregates can specify a child scope.</span></span>  
  
 <span data-ttu-id="52a8b-121">*Expression* には、入れ子になった集計関数への呼び出しを含めることができます。ただし、次に示すように、これには例外および条件があります。</span><span class="sxs-lookup"><span data-stu-id="52a8b-121">*Expression* can contain calls to nested aggregate functions with the following exceptions and conditions:</span></span>  
  
-   <span data-ttu-id="52a8b-122">入れ子集計の*Scope* は、外部集計のスコープと同じであるか、そのスコープに含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="52a8b-122">*Scope* for nested aggregates must be the same as, or contained by, the scope of the outer aggregate.</span></span> <span data-ttu-id="52a8b-123">式内のすべてのスコープについては、1 つのスコープがそれ以外のすべてのスコープに対する子であるようなリレーションシップが必要です。</span><span class="sxs-lookup"><span data-stu-id="52a8b-123">For all distinct scopes in the expression, one scope must be in a child relationship to all other scopes.</span></span>  
  
-   <span data-ttu-id="52a8b-124">入れ子集計の*Scope* には、データセット名は使用できません。</span><span class="sxs-lookup"><span data-stu-id="52a8b-124">*Scope* for nested aggregates cannot be the name of a dataset.</span></span>  
  
-   <span data-ttu-id="52a8b-125">*式*には、、、 `First` `Last` `Previous` 、または関数を含めることはできません `RunningValue` 。</span><span class="sxs-lookup"><span data-stu-id="52a8b-125">*Expression* must not contain `First`, `Last`, `Previous`, or `RunningValue` functions.</span></span>  
  
-   <span data-ttu-id="52a8b-126">*Expression* には、 *recursive*を指定する入れ子集計を含めることができません。</span><span class="sxs-lookup"><span data-stu-id="52a8b-126">*Expression* must not contain nested aggregates that specify *recursive*.</span></span>  
  
 <span data-ttu-id="52a8b-127">詳細については、「[集計関数リファレンス &#40;レポート ビルダーおよび SSRS&#41;](report-builder-functions-aggregate-functions-reference.md)」および「[合計、集計、および組み込みコレクションの式のスコープ &#40;レポート ビルダーおよび SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="52a8b-127">For more information, see [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) and [Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md).</span></span>  
  
 <span data-ttu-id="52a8b-128">再帰的集計については、「[複数の再帰型階層グループの作成 &#40;レポート ビルダーおよび SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="52a8b-128">For more information about recursive aggregates, see [Creating Recursive Hierarchy Groups &#40;Report Builder and SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="52a8b-129">例</span><span class="sxs-lookup"><span data-stu-id="52a8b-129">Example</span></span>  
 <span data-ttu-id="52a8b-130">次のコード例では、データ領域の `Category` グループの最初の製品番号が返されます。</span><span class="sxs-lookup"><span data-stu-id="52a8b-130">The following code example returns the first product number in the `Category` group of a data region:</span></span>  
  
```  
=First(Fields!ProductNumber.Value, "Category")  
```  
  
## <a name="see-also"></a><span data-ttu-id="52a8b-131">参照</span><span class="sxs-lookup"><span data-stu-id="52a8b-131">See Also</span></span>  
 <span data-ttu-id="52a8b-132">[レポートでの式の使用 (レポート ビルダーおよび SSRS)](expression-uses-in-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="52a8b-132">[Expression Uses in Reports &#40;Report Builder and SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="52a8b-133">[式の例 (レポート ビルダーおよび SSRS)](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="52a8b-133">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="52a8b-134">[式で使用されるデータ型 &#40;レポート ビルダーおよび SSRS&#41;](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="52a8b-134">[Data Types in Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="52a8b-135">合計、集計、および組み込みコレクションの式のスコープ (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="52a8b-135">Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;</span></span>](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
