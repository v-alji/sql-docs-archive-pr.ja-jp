---
title: 集計関数 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 16ce643f-bbb3-40a5-ba78-7aed73156f3e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: fcc65f1e60c29ba9ea6a4206b419eb0b13edb0ff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641457"
---
# <a name="aggregate-function-report-builder-and-ssrs"></a><span data-ttu-id="d82bd-102">集計関数 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="d82bd-102">Aggregate Function (Report Builder and SSRS)</span></span>
  <span data-ttu-id="d82bd-103">データ プロバイダーの定義に従い、指定された式のカスタムの集計を返します。</span><span class="sxs-lookup"><span data-stu-id="d82bd-103">Returns a custom aggregate of the specified expression, as defined by the data provider.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a><span data-ttu-id="d82bd-104">構文</span><span class="sxs-lookup"><span data-stu-id="d82bd-104">Syntax</span></span>  
  
```  
  
Aggregate(expression, scope)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d82bd-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d82bd-105">Parameters</span></span>  
 <span data-ttu-id="d82bd-106">*式 (expression)*</span><span class="sxs-lookup"><span data-stu-id="d82bd-106">*expression*</span></span>  
 <span data-ttu-id="d82bd-107">この集計関数の実行対象の式です。</span><span class="sxs-lookup"><span data-stu-id="d82bd-107">The expression on which to perform the aggregation.</span></span> <span data-ttu-id="d82bd-108">指定する式は、単純なフィールド参照の式である必要があります。</span><span class="sxs-lookup"><span data-stu-id="d82bd-108">The expression must be a simple field reference.</span></span>  
  
 <span data-ttu-id="d82bd-109">*スコープ (scope)*</span><span class="sxs-lookup"><span data-stu-id="d82bd-109">*scope*</span></span>  
 <span data-ttu-id="d82bd-110">(`String`) 集計関数の適用先となるレポート アイテムを含むデータセット、グループ、またはデータ領域の名前です。</span><span class="sxs-lookup"><span data-stu-id="d82bd-110">(`String`) The name of a dataset, group, or data region that contains the report items to which to apply the aggregate function.</span></span> <span data-ttu-id="d82bd-111">*Scope* は文字列定数である必要があり、また、式を指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="d82bd-111">*Scope* must be a string constant andcannot be an expression.</span></span> <span data-ttu-id="d82bd-112">*scope* を指定しない場合、現在のスコープが使用されます。</span><span class="sxs-lookup"><span data-stu-id="d82bd-112">If *scope* is not specified, the current scope is used.</span></span>  
  
## <a name="return-type"></a><span data-ttu-id="d82bd-113">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="d82bd-113">Return Type</span></span>  
 <span data-ttu-id="d82bd-114">戻り値の型はデータ プロバイダーによって決められます。</span><span class="sxs-lookup"><span data-stu-id="d82bd-114">Return type is determined by the data provider.</span></span> <span data-ttu-id="d82bd-115">プロバイダーがこの関数をサポートしていない場合や、データが取得できなかった場合は、`Nothing` が返されます。</span><span class="sxs-lookup"><span data-stu-id="d82bd-115">Returns `Nothing` if the data provider does not support this function or data is not available.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d82bd-116">解説</span><span class="sxs-lookup"><span data-stu-id="d82bd-116">Remarks</span></span>  
 <span data-ttu-id="d82bd-117">`Aggregate` 関数を使用すると、外部データ ソース上で計算される集計を使用できます。</span><span class="sxs-lookup"><span data-stu-id="d82bd-117">The `Aggregate` function provides a way to use aggregates that are calculated on the external data source.</span></span> <span data-ttu-id="d82bd-118">この機能のサポートは、データ拡張機能によって異なります。</span><span class="sxs-lookup"><span data-stu-id="d82bd-118">Support for this feature is determined by the data extension.</span></span> <span data-ttu-id="d82bd-119">たとえば、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データ処理拡張機能では、MDX クエリからフラットな行セットを取得します。</span><span class="sxs-lookup"><span data-stu-id="d82bd-119">For example, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] data processing extension retrieves flattened rowsets from an MDX query.</span></span> <span data-ttu-id="d82bd-120">結果セット内の一部の行には、データ ソース サーバーで計算される集計値を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="d82bd-120">Some rows in the result set can contain aggregate values calculated on the data source server.</span></span> <span data-ttu-id="d82bd-121">これらは、 *サーバー集計*と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="d82bd-121">These are known as *server aggregates*.</span></span> <span data-ttu-id="d82bd-122">サーバー集計を [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]のグラフィカル クエリ デザイナーで表示するには、ツール バーの **[集計の表示]** ボタンを使用します。</span><span class="sxs-lookup"><span data-stu-id="d82bd-122">To view server aggregates in the graphical query designer for [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], you can use the **Show Aggregate** button on the toolbar.</span></span> <span data-ttu-id="d82bd-123">詳細については、「[Analysis Services の MDX クエリ デザイナーのユーザー インターフェイス &#40;レポート ビルダー&#41;](../analysis-services-mdx-query-designer-user-interface-report-builder.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d82bd-123">For more information, see [Analysis Services MDX Query Designer User Interface &#40;Report Builder&#41;](../analysis-services-mdx-query-designer-user-interface-report-builder.md).</span></span>  
  
 <span data-ttu-id="d82bd-124">Tablix データ領域の詳細行にデータセットの集計値および詳細値の組み合わせを表示する場合、通常、サーバー集計値は詳細データではないため含まれません。</span><span class="sxs-lookup"><span data-stu-id="d82bd-124">When you display the combination of aggregate and detail dataset values on detail rows of a Tablix data region, server aggregates would not typically be included because they are not detail data.</span></span> <span data-ttu-id="d82bd-125">ただし、データセットから取得したすべての値を表示し、集計データを計算および表示する方法をカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="d82bd-125">However, you may want to display all values retrieved for the dataset and customize the way aggregate data is calculated and displayed.</span></span>  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="d82bd-126">では、サーバー集計値を詳細行に表示するかどうかを判断するため、レポート内の式で `Aggregate` 関数の使用が検出されます。</span><span class="sxs-lookup"><span data-stu-id="d82bd-126">detects the use of the `Aggregate` function in expressions in your report in order to determine whether to display server aggregates on detail rows.</span></span> <span data-ttu-id="d82bd-127">データ領域の式に `Aggregate` を含めると、サーバー集計値は、詳細行ではなくグループの合計行または総計行のみに表示されます。</span><span class="sxs-lookup"><span data-stu-id="d82bd-127">If you include `Aggregate` in an expression in a data region, server aggregates can only appear on group total or grand total rows, not on detail rows.</span></span> <span data-ttu-id="d82bd-128">サーバー集計値を詳細行に表示する場合は、`Aggregate` 関数を使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="d82bd-128">If you want to display server aggregates on detail rows, do not use the `Aggregate` function.</span></span>  
  
 <span data-ttu-id="d82bd-129">この既定の動作を変更するには、 **[データセットのプロパティ]** ダイアログ ボックスの **[小計を詳細行として解釈]** オプションの値を変更します。</span><span class="sxs-lookup"><span data-stu-id="d82bd-129">You can change this default behavior by changing the value of the **Interpret subtotals as details** option on the **Dataset Properties** dialog box.</span></span> <span data-ttu-id="d82bd-130">このオプションを `True` に設定すると、サーバー集計値を含むすべてのデータが詳細データとして表示されます。</span><span class="sxs-lookup"><span data-stu-id="d82bd-130">When this option is set to `True`, all data, including server aggregates, appears as detail data.</span></span> <span data-ttu-id="d82bd-131">`False` に設定すると、サーバー集計値は合計として表示されます。</span><span class="sxs-lookup"><span data-stu-id="d82bd-131">When set to `False`, server aggregates appear as totals.</span></span> <span data-ttu-id="d82bd-132">このプロパティの設定は、このデータセットにリンクされているすべてのデータ領域に影響します。</span><span class="sxs-lookup"><span data-stu-id="d82bd-132">The setting for this property affects all data regions that are linked to this dataset.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d82bd-133">`Aggregate` を参照するレポート アイテムを含むすべてのグループでは、そのグループ式に単純なフィールド参照 (`[FieldName]` など) が指定されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="d82bd-133">All containing groups for the report item that references `Aggregate` must have simple field references for their group expressions, for example, `[FieldName]`.</span></span> <span data-ttu-id="d82bd-134">複雑なグループ式を使用するデータ領域で `Aggregate` を使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="d82bd-134">You cannot use `Aggregate` in a data region that uses complex group expressions.</span></span> <span data-ttu-id="d82bd-135">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データ処理拡張機能では、`Aggregate` 関数を使用した集計がサポートされるように、(`MemberProperty` 型ではなく) `LevelProperty` 型の MDX フィールドをクエリに含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="d82bd-135">For the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] data processing extension, your query must include MDX fields of type `LevelProperty` (not `MemberProperty`) to support aggregation using the `Aggregate`function.</span></span>  
  
 <span data-ttu-id="d82bd-136">*Expression* には、入れ子になった集計関数への呼び出しを含めることができます。ただし、次に示すように、これには例外および条件があります。</span><span class="sxs-lookup"><span data-stu-id="d82bd-136">*Expression* can contain calls to nested aggregate functions with the following exceptions and conditions:</span></span>  
  
-   <span data-ttu-id="d82bd-137">入れ子集計の*Scope* は、外部集計のスコープと同じであるか、そのスコープに含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="d82bd-137">*Scope* for nested aggregates must be the same as, or contained by, the scope of the outer aggregate.</span></span> <span data-ttu-id="d82bd-138">式内のすべてのスコープについては、1 つのスコープがそれ以外のすべてのスコープに対する子であるようなリレーションシップが必要です。</span><span class="sxs-lookup"><span data-stu-id="d82bd-138">For all distinct scopes in the expression, one scope must be in a child relationship to all other scopes.</span></span>  
  
-   <span data-ttu-id="d82bd-139">入れ子集計の*Scope* には、データセット名は使用できません。</span><span class="sxs-lookup"><span data-stu-id="d82bd-139">*Scope* for nested aggregates cannot be the name of a dataset.</span></span>  
  
-   <span data-ttu-id="d82bd-140">*式*には、、、 `First` `Last` `Previous` 、または関数を含めることはできません `RunningValue` 。</span><span class="sxs-lookup"><span data-stu-id="d82bd-140">*Expression* must not contain `First`, `Last`, `Previous`, or `RunningValue` functions.</span></span>  
  
-   <span data-ttu-id="d82bd-141">*Expression* には、 *recursive*を指定する入れ子集計を含めることができません。</span><span class="sxs-lookup"><span data-stu-id="d82bd-141">*Expression* must not contain nested aggregates that specify *recursive*.</span></span>  
  
 <span data-ttu-id="d82bd-142">詳細については、「[集計関数リファレンス &#40;レポート ビルダーおよび SSRS&#41;](report-builder-functions-aggregate-functions-reference.md)」および「[合計、集計、および組み込みコレクションの式のスコープ &#40;レポート ビルダーおよび SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d82bd-142">For more information, see [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) and [Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md).</span></span>  
  
 <span data-ttu-id="d82bd-143">再帰的集計については、「[複数の再帰型階層グループの作成 &#40;レポート ビルダーおよび SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d82bd-143">For more information about recursive aggregates, see [Creating Recursive Hierarchy Groups &#40;Report Builder and SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md).</span></span>  
  
## <a name="comparing-the-aggregate-and-sum-functions"></a><span data-ttu-id="d82bd-144">Aggregate 関数と Sum 関数の比較</span><span class="sxs-lookup"><span data-stu-id="d82bd-144">Comparing the Aggregate and Sum Functions</span></span>  
 <span data-ttu-id="d82bd-145">`Aggregate` 関数はデータ プロバイダーまたはデータ処理拡張機能によって計算される値を返すという点で、`Sum` 関数は `Aggregate` などの数値の集計関数と異なります。</span><span class="sxs-lookup"><span data-stu-id="d82bd-145">The `Aggregate` function differs from numeric aggregate functions like `Sum` in that the `Aggregate` function returns a value that is calculated by the data provider or data processing extension.</span></span> <span data-ttu-id="d82bd-146">のような数値集計関数は、 `Sum` *スコープ*パラメーターによって決定されるデータセットのデータセットに基づいて、レポートプロセッサによって計算される値を返します。</span><span class="sxs-lookup"><span data-stu-id="d82bd-146">Numeric aggregate functions like `Sum` return a value that is calculated by the report processor on a set of data from the dataset that is determined by the *scope* parameter.</span></span> <span data-ttu-id="d82bd-147">詳細については、「[集計関数リファレンス &#40;レポート ビルダーおよび SSRS&#41;](report-builder-functions-aggregate-functions-reference.md)」に示されている集計関数を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d82bd-147">For more information, see the aggregate functions listed in [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d82bd-148">例</span><span class="sxs-lookup"><span data-stu-id="d82bd-148">Example</span></span>  
 <span data-ttu-id="d82bd-149">次のコード例では、 `LineTotal`フィールドのサーバー集計値を取得する式を示します。</span><span class="sxs-lookup"><span data-stu-id="d82bd-149">The following code example shows an expression that retrieves a server aggregate for the field `LineTotal`.</span></span> <span data-ttu-id="d82bd-150">式は、 `GroupbyOrder`グループに属する行内のセルに追加されます。</span><span class="sxs-lookup"><span data-stu-id="d82bd-150">The expression is added to a cell in a row that belongs to the group `GroupbyOrder`.</span></span>  
  
```  
=Aggregate(Fields!LineTotal.Value, "GroupbyOrder")  
```  
  
## <a name="see-also"></a><span data-ttu-id="d82bd-151">参照</span><span class="sxs-lookup"><span data-stu-id="d82bd-151">See Also</span></span>  
 <span data-ttu-id="d82bd-152">[レポートでの式の使用 (レポート ビルダーおよび SSRS)](expression-uses-in-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="d82bd-152">[Expression Uses in Reports &#40;Report Builder and SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="d82bd-153">[式の例 (レポート ビルダーおよび SSRS)](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="d82bd-153">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="d82bd-154">[式で使用されるデータ型 &#40;レポート ビルダーおよび SSRS&#41;](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="d82bd-154">[Data Types in Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="d82bd-155">合計、集計、および組み込みコレクションの式のスコープ (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="d82bd-155">Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;</span></span>](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
