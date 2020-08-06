---
title: Lookup 関数 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: e60e5bab-b286-4897-9685-9ff12703517d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 053fefff51e4b4e338e262664bd7570280c92540
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640672"
---
# <a name="lookup-function-report-builder-and-ssrs"></a><span data-ttu-id="72382-102">Lookup 関数 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="72382-102">Lookup Function (Report Builder and SSRS)</span></span>
  <span data-ttu-id="72382-103">名前と値のペアを含むデータセットから、指定された名前に最初に一致した値を返します。</span><span class="sxs-lookup"><span data-stu-id="72382-103">Returns the first matching value for the specified name from a dataset that contains name/value pairs.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a><span data-ttu-id="72382-104">構文</span><span class="sxs-lookup"><span data-stu-id="72382-104">Syntax</span></span>  
  
```  
  
Lookup(source_expression, destination_expression, result_expression, dataset)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="72382-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="72382-105">Parameters</span></span>  
 <span data-ttu-id="72382-106">*source_expression*</span><span class="sxs-lookup"><span data-stu-id="72382-106">*source_expression*</span></span>  
 <span data-ttu-id="72382-107">(`Variant`) 現在のスコープ内で評価される式。参照する名前またはキーを指定します。</span><span class="sxs-lookup"><span data-stu-id="72382-107">(`Variant`) An expression that is evaluated in the current scope and that specifies the name or key to look up.</span></span> <span data-ttu-id="72382-108">たとえば、「 `=Fields!ProdID.Value` 」のように入力します。</span><span class="sxs-lookup"><span data-stu-id="72382-108">For example, `=Fields!ProdID.Value`.</span></span>  
  
 <span data-ttu-id="72382-109">*destination_expression*</span><span class="sxs-lookup"><span data-stu-id="72382-109">*destination_expression*</span></span>  
 <span data-ttu-id="72382-110">(`Variant`) データセット内の各行に対して評価される式。照合する名前またはキーを指定します。</span><span class="sxs-lookup"><span data-stu-id="72382-110">(`Variant`) An expression that is evaluated for each row in a dataset and that specifies the name or key to match on.</span></span> <span data-ttu-id="72382-111">たとえば、「 `=Fields!ProductID.Value` 」のように入力します。</span><span class="sxs-lookup"><span data-stu-id="72382-111">For example, `=Fields!ProductID.Value`.</span></span>  
  
 <span data-ttu-id="72382-112">*result_expression*</span><span class="sxs-lookup"><span data-stu-id="72382-112">*result_expression*</span></span>  
 <span data-ttu-id="72382-113">( `Variant` ) データセット内の行に対して評価される式*source_expression*  = *destination_expression*、は取得する値を指定します。</span><span class="sxs-lookup"><span data-stu-id="72382-113">(`Variant`) An expression that is evaluated for the row in the dataset where *source_expression* = *destination_expression*, and that specifies the value to retrieve.</span></span> <span data-ttu-id="72382-114">たとえば、「 `=Fields!ProductName.Value` 」のように入力します。</span><span class="sxs-lookup"><span data-stu-id="72382-114">For example, `=Fields!ProductName.Value`.</span></span>  
  
 <span data-ttu-id="72382-115">*データセット (dataset)*</span><span class="sxs-lookup"><span data-stu-id="72382-115">*dataset*</span></span>  
 <span data-ttu-id="72382-116">レポート内のデータセットの名前を指定する定数。</span><span class="sxs-lookup"><span data-stu-id="72382-116">A constant that specifies the name of a dataset in the report.</span></span> <span data-ttu-id="72382-117">たとえば、"Products" などです。</span><span class="sxs-lookup"><span data-stu-id="72382-117">For example, "Products".</span></span>  
  
## <a name="return"></a><span data-ttu-id="72382-118">戻り値</span><span class="sxs-lookup"><span data-stu-id="72382-118">Return</span></span>  
 <span data-ttu-id="72382-119">`Variant` を返します。一致する結果がなかった場合は、`Nothing` を返します。</span><span class="sxs-lookup"><span data-stu-id="72382-119">Returns a `Variant`, or `Nothing` if there is no match.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="72382-120">解説</span><span class="sxs-lookup"><span data-stu-id="72382-120">Remarks</span></span>  
 <span data-ttu-id="72382-121">指定したデータセットで、名前と値のペアについて 1 対 1 のリレーションシップが存在する場合、`Lookup` を使用して値を取得します。</span><span class="sxs-lookup"><span data-stu-id="72382-121">Use `Lookup` to retrieve the value from the specified dataset for a name/value pair where there is a 1-to-1 relationship.</span></span> <span data-ttu-id="72382-122">たとえば、テーブル内の ID フィールドに対して `Lookup` を使用して、データ領域にバインドされていないデータセットから対応する Name フィールドを取得することができます。</span><span class="sxs-lookup"><span data-stu-id="72382-122">For example, for an ID field in a table, you can use `Lookup` to retrieve the corresponding Name field from a dataset that is not bound to the data region.</span></span>  
  
 <span data-ttu-id="72382-123">`Lookup` を実行すると、次の処理が行われます。</span><span class="sxs-lookup"><span data-stu-id="72382-123">`Lookup` does the following:</span></span>  
  
-   <span data-ttu-id="72382-124">ソースの式を現在のスコープ内で評価します。</span><span class="sxs-lookup"><span data-stu-id="72382-124">Evaluates the source expression in the current scope.</span></span>  
  
-   <span data-ttu-id="72382-125">フィルターを適用した後で、指定されたデータセットの照合順序に基づき、指定されたデータセットの各行に対して変換先の式を評価します。</span><span class="sxs-lookup"><span data-stu-id="72382-125">Evaluates the destination expression for each row of the specified dataset after filters have been applied, based on the collation of the specified dataset.</span></span>  
  
-   <span data-ttu-id="72382-126">変換元の式と変換先の式が最初に一致したときに、データセット内のその行に対して結果式を評価します。</span><span class="sxs-lookup"><span data-stu-id="72382-126">On the first match of source expression and destination expression, evaluates the result expression for that row in the dataset.</span></span>  
  
-   <span data-ttu-id="72382-127">結果式の値を返します。</span><span class="sxs-lookup"><span data-stu-id="72382-127">Returns the result expression value.</span></span>  
  
 <span data-ttu-id="72382-128">1 対多のリレーションシップがある場合、1 つの名前フィールドまたはキー フィールドに対応する複数の値を取得するには、[LookupSet 関数 &#40;レポート ビルダーおよび SSRS&#41;](report-builder-functions-lookupset-function.md) を使用します。</span><span class="sxs-lookup"><span data-stu-id="72382-128">To retrieve multiple values for a single name or key field where there is a 1-to-many relationship, use [LookupSet Function &#40;Report Builder and SSRS&#41;](report-builder-functions-lookupset-function.md).</span></span> <span data-ttu-id="72382-129">一連の `Lookup` 値に対してを呼び出すには、 [Multilookup 関数 &#40;レポートビルダーと SSRS&#41;](report-builder-functions-lookup-function.md)を使用します。</span><span class="sxs-lookup"><span data-stu-id="72382-129">To call `Lookup` for a set of values, use [Multilookup Function &#40;Report Builder and SSRS&#41;](report-builder-functions-lookup-function.md).</span></span>  
  
 <span data-ttu-id="72382-130">次の制限事項が適用されます。</span><span class="sxs-lookup"><span data-stu-id="72382-130">The following restrictions apply:</span></span>  
  
-   <span data-ttu-id="72382-131">`Lookup`は、すべてのフィルター式が適用された後に評価されます。</span><span class="sxs-lookup"><span data-stu-id="72382-131">`Lookup` is evaluated after all filter expressions are applied.</span></span>  
  
-   <span data-ttu-id="72382-132">1 レベルの参照のみがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="72382-132">Only one level of lookup is supported.</span></span> <span data-ttu-id="72382-133">変換元、変換先、または結果の式に、Lookup 関数への参照を含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="72382-133">A source, destination, or result expression cannot include a reference to a lookup function.</span></span>  
  
-   <span data-ttu-id="72382-134">変換元および変換先の式は、同じデータ型として評価される必要があります。</span><span class="sxs-lookup"><span data-stu-id="72382-134">Source and destination expressions must evaluate to the same data type.</span></span> <span data-ttu-id="72382-135">戻り値の型は、評価された結果式のデータ型と同じです。</span><span class="sxs-lookup"><span data-stu-id="72382-135">The return type is the same as the data type of the evaluated result expression.</span></span>  
  
-   <span data-ttu-id="72382-136">変換元、変換先、結果の式には、レポート変数またはグループ変数への参照を含めることができません。</span><span class="sxs-lookup"><span data-stu-id="72382-136">Source, destination, and result expressions cannot include references to report or group variables.</span></span>  
  
-   <span data-ttu-id="72382-137">`Lookup` は、次のレポート アイテムを求める式として使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="72382-137">`Lookup` cannot be used as an expression for the following report items:</span></span>  
  
    -   <span data-ttu-id="72382-138">データ ソースの動的な接続文字列。</span><span class="sxs-lookup"><span data-stu-id="72382-138">Dynamic connection strings for a data source.</span></span>  
  
    -   <span data-ttu-id="72382-139">データセット内の計算フィールド。</span><span class="sxs-lookup"><span data-stu-id="72382-139">Calculated fields in a dataset.</span></span>  
  
    -   <span data-ttu-id="72382-140">データセット内のクエリ パラメーター。</span><span class="sxs-lookup"><span data-stu-id="72382-140">Query parameters in a dataset.</span></span>  
  
    -   <span data-ttu-id="72382-141">データセット内のフィルター。</span><span class="sxs-lookup"><span data-stu-id="72382-141">Filters in a dataset.</span></span>  
  
    -   <span data-ttu-id="72382-142">レポート パラメーター。</span><span class="sxs-lookup"><span data-stu-id="72382-142">Report parameters.</span></span>  
  
    -   <span data-ttu-id="72382-143">Report.Language プロパティ。</span><span class="sxs-lookup"><span data-stu-id="72382-143">The Report.Language property.</span></span>  
  
 <span data-ttu-id="72382-144">詳細については、「[集計関数リファレンス &#40;レポート ビルダーおよび SSRS&#41;](report-builder-functions-aggregate-functions-reference.md)」および「[合計、集計、および組み込みコレクションの式のスコープ &#40;レポート ビルダーおよび SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="72382-144">For more information, see [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) and [Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="72382-145">例</span><span class="sxs-lookup"><span data-stu-id="72382-145">Example</span></span>  
 <span data-ttu-id="72382-146">次の例では、製品の識別子である ProductID のフィールドを含むデータセットにテーブルがバインドされているとします。</span><span class="sxs-lookup"><span data-stu-id="72382-146">In the following example, assume that a table is bound to a dataset that includes a field for the product identifier ProductID.</span></span> <span data-ttu-id="72382-147">別のデータセットである "Product" には、対応する製品識別子 ID と、製品名を表す Name が含まれています。</span><span class="sxs-lookup"><span data-stu-id="72382-147">A separate dataset called "Product" contains the corresponding product identifier ID and the product name Name.</span></span>  
  
 <span data-ttu-id="72382-148">次の式では、`Lookup` を使用して "Product" データセットの各行に含まれる ID と ProductID の値を比較し、一致が見つかった場合には、その行の Name フィールドの値を返します。</span><span class="sxs-lookup"><span data-stu-id="72382-148">In the following expression, `Lookup` compares the value of ProductID to ID in each row of the dataset called "Product" and, when a match is found, returns the value of the Name field for that row.</span></span>  
  
```  
=Lookup(Fields!ProductID.Value, Fields!ID.Value, Fields!Name.Value, "Product")  
```  
  
## <a name="see-also"></a><span data-ttu-id="72382-149">参照</span><span class="sxs-lookup"><span data-stu-id="72382-149">See Also</span></span>  
 <span data-ttu-id="72382-150">[レポートでの式の使用 (レポート ビルダーおよび SSRS)](expression-uses-in-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="72382-150">[Expression Uses in Reports &#40;Report Builder and SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="72382-151">[式の例 (レポート ビルダーおよび SSRS)](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="72382-151">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="72382-152">[式で使用されるデータ型 &#40;レポート ビルダーおよび SSRS&#41;](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="72382-152">[Data Types in Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="72382-153">合計、集計、および組み込みコレクションの式のスコープ (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="72382-153">Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;</span></span>](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
