---
title: Multilookup 関数 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 1fec079e-33b3-4e4d-92b3-6b4d06a49a77
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2f2aff7a2a39e1a072cf4b05f0a04e12ced529af
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640670"
---
# <a name="multilookup-function-report-builder-and-ssrs"></a><span data-ttu-id="c80cb-102">Multilookup 関数 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="c80cb-102">Multilookup Function (Report Builder and SSRS)</span></span>
  <span data-ttu-id="c80cb-103">名前と値のペアを含むデータセットから、指定された名前のセットに最初に一致した値のセットを返します。</span><span class="sxs-lookup"><span data-stu-id="c80cb-103">Returns the set of first-match values for the specified set of names from a dataset that contains name/value pairs.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a><span data-ttu-id="c80cb-104">構文</span><span class="sxs-lookup"><span data-stu-id="c80cb-104">Syntax</span></span>  
  
```  
  
Multilookup(source_expression, destination_expression, result_expression, dataset)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c80cb-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c80cb-105">Parameters</span></span>  
 <span data-ttu-id="c80cb-106">*source_expression*</span><span class="sxs-lookup"><span data-stu-id="c80cb-106">*source_expression*</span></span>  
 <span data-ttu-id="c80cb-107">(`VariantArray`) 現在のスコープ内で評価される式。参照する名前またはキーのセットを指定します。</span><span class="sxs-lookup"><span data-stu-id="c80cb-107">(`VariantArray`) An expression that is evaluated in the current scope and that specifies the set of names or keys to look up.</span></span> <span data-ttu-id="c80cb-108">たとえば、複数値パラメーターの場合、 `=Parameters!IDs.value`のように指定します。</span><span class="sxs-lookup"><span data-stu-id="c80cb-108">For example, for a multivalue parameter, `=Parameters!IDs.value`.</span></span>  
  
 <span data-ttu-id="c80cb-109">*destination_expression*</span><span class="sxs-lookup"><span data-stu-id="c80cb-109">*destination_expression*</span></span>  
 <span data-ttu-id="c80cb-110">(`Variant`) データセット内の各行に対して評価される式。照合する名前またはキーを指定します。</span><span class="sxs-lookup"><span data-stu-id="c80cb-110">(`Variant`) An expression that is evaluated for each row in a dataset and that specifies the name or key to match on.</span></span> <span data-ttu-id="c80cb-111">たとえば、「 `=Fields!ID.Value` 」のように入力します。</span><span class="sxs-lookup"><span data-stu-id="c80cb-111">For example, `=Fields!ID.Value`.</span></span>  
  
 <span data-ttu-id="c80cb-112">*result_expression*</span><span class="sxs-lookup"><span data-stu-id="c80cb-112">*result_expression*</span></span>  
 <span data-ttu-id="c80cb-113">( `Variant` ) データセット内の行に対して評価される式*source_expression*  = *destination_expression*、は取得する値を指定します。</span><span class="sxs-lookup"><span data-stu-id="c80cb-113">(`Variant`) An expression that is evaluated for the row in the dataset where *source_expression* = *destination_expression*, and that specifies the value to retrieve.</span></span> <span data-ttu-id="c80cb-114">たとえば、「 `=Fields!Name.Value` 」のように入力します。</span><span class="sxs-lookup"><span data-stu-id="c80cb-114">For example, `=Fields!Name.Value`.</span></span>  
  
 <span data-ttu-id="c80cb-115">*データセット (dataset)*</span><span class="sxs-lookup"><span data-stu-id="c80cb-115">*dataset*</span></span>  
 <span data-ttu-id="c80cb-116">レポート内のデータセットの名前を指定する定数。</span><span class="sxs-lookup"><span data-stu-id="c80cb-116">A constant that specifies the name of a dataset in the report.</span></span> <span data-ttu-id="c80cb-117">たとえば、"Colors" と指定します。</span><span class="sxs-lookup"><span data-stu-id="c80cb-117">For example, "Colors".</span></span>  
  
## <a name="return"></a><span data-ttu-id="c80cb-118">戻り値</span><span class="sxs-lookup"><span data-stu-id="c80cb-118">Return</span></span>  
 <span data-ttu-id="c80cb-119">`VariantArray` を返します。一致する結果がなかった場合は、`Nothing` を返します。</span><span class="sxs-lookup"><span data-stu-id="c80cb-119">Returns a `VariantArray`, or `Nothing` if there is no match.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c80cb-120">解説</span><span class="sxs-lookup"><span data-stu-id="c80cb-120">Remarks</span></span>  
 <span data-ttu-id="c80cb-121">データセットで、名前と値の各ペアに 1 対 1 のリレーションシップが存在する場合、`Multilookup` を使用して一連の値を取得します。</span><span class="sxs-lookup"><span data-stu-id="c80cb-121">Use `Multilookup` to retrieve a set of values from a dataset for name-value pairs where each pair has a 1-to-1 relationship.</span></span> <span data-ttu-id="c80cb-122">`MultiLookup` は、一連の名前またはキーに対して `Lookup` を呼び出すことと同じです。</span><span class="sxs-lookup"><span data-stu-id="c80cb-122">`MultiLookup` is the equivalent of calling `Lookup` for a set of names or keys.</span></span> <span data-ttu-id="c80cb-123">たとえば、主キー識別子に基づく複数値パラメーターの場合、テーブルのテキスト ボックス内の式で `Multilookup` を使用して、パラメーターまたはテーブルにバインドされていないデータセットから、関連付けられている値を取得することができます。</span><span class="sxs-lookup"><span data-stu-id="c80cb-123">For example, for a multivalue parameter that is based on primary key identifiers, you can use `Multilookup` in an expression in a text box in a table to retrieve associated values from a dataset that is not bound to the parameter or to the table.</span></span>  
  
 <span data-ttu-id="c80cb-124">`Multilookup` を実行すると、次の処理が行われます。</span><span class="sxs-lookup"><span data-stu-id="c80cb-124">`Multilookup` does the following:</span></span>  
  
-   <span data-ttu-id="c80cb-125">現在のスコープ内でソース式が評価され、variant オブジェクトの配列が生成されます。</span><span class="sxs-lookup"><span data-stu-id="c80cb-125">Evaluates the source expression in the current scope and generates an array of variant objects.</span></span>  
  
-   <span data-ttu-id="c80cb-126">配列内の各オブジェクトに対して [Lookup 関数 &#40;レポート ビルダーおよび SSRS&#41;](report-builder-functions-lookup-function.md) が呼び出され、返される配列に結果が追加されます。</span><span class="sxs-lookup"><span data-stu-id="c80cb-126">For each object in the array, calls [Lookup Function &#40;Report Builder and SSRS&#41;](report-builder-functions-lookup-function.md) and adds the result to the return array.</span></span>  
  
-   <span data-ttu-id="c80cb-127">結果セットが返されます。</span><span class="sxs-lookup"><span data-stu-id="c80cb-127">Returns the set of results.</span></span>  
  
 <span data-ttu-id="c80cb-128">指定した名前に対応する、名前と値のペアを含むデータセットに 1 対 1 のリレーションシップが存在する場合、このデータセットから 1 つの値を取得するには、[Lookup 関数 &#40;レポート ビルダーおよび SSRS&#41;](report-builder-functions-lookup-function.md) を使用します。</span><span class="sxs-lookup"><span data-stu-id="c80cb-128">To retrieve a single value from a dataset with name-value pairs for a specified name where there is a 1-to-1 relationship, use [Lookup Function &#40;Report Builder and SSRS&#41;](report-builder-functions-lookup-function.md).</span></span> <span data-ttu-id="c80cb-129">指定した名前に対応する、名前と値のペアを含むデータセットに 1 対多のリレーションシップが存在する場合、このデータセットから複数の値を取得するには、[LookupSet 関数 &#40;レポート ビルダーおよび SSRS&#41;](report-builder-functions-lookupset-function.md) を使用します。</span><span class="sxs-lookup"><span data-stu-id="c80cb-129">To retrieve multiple values from a dataset with name-value pairs for a name where there is a 1-to-many relationship, use [LookupSet Function &#40;Report Builder and SSRS&#41;](report-builder-functions-lookupset-function.md).</span></span>  
  
 <span data-ttu-id="c80cb-130">次の制限事項が適用されます。</span><span class="sxs-lookup"><span data-stu-id="c80cb-130">The following restrictions apply:</span></span>  
  
-   <span data-ttu-id="c80cb-131">`Multilookup` は、すべてのフィルター式が適用された後で評価されます。</span><span class="sxs-lookup"><span data-stu-id="c80cb-131">`Multilookup` is evaluated after all filter expressions are applied</span></span>  
  
-   <span data-ttu-id="c80cb-132">1 レベルの参照のみがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="c80cb-132">Only one level of look-up is supported.</span></span> <span data-ttu-id="c80cb-133">変換元、変換先、または結果の式に、Lookup 関数への参照を含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="c80cb-133">A source, destination, or result expression cannot include a reference to a lookup function.</span></span>  
  
-   <span data-ttu-id="c80cb-134">変換元および変換先の式は、同じデータ型として評価される必要があります。</span><span class="sxs-lookup"><span data-stu-id="c80cb-134">Source and destination expressions must evaluate to the same data type.</span></span>  
  
-   <span data-ttu-id="c80cb-135">変換元、変換先、結果の式には、レポート変数またはグループ変数への参照を含めることができません。</span><span class="sxs-lookup"><span data-stu-id="c80cb-135">Source, destination, and result expressions cannot include references to report or group variables.</span></span>  
  
-   <span data-ttu-id="c80cb-136">`Multilookup` は、次のレポート アイテムを求める式として使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="c80cb-136">`Multilookup` cannot be used as an expression for the following report items:</span></span>  
  
    -   <span data-ttu-id="c80cb-137">データ ソースの動的な接続文字列。</span><span class="sxs-lookup"><span data-stu-id="c80cb-137">Dynamic connection strings for a data source.</span></span>  
  
    -   <span data-ttu-id="c80cb-138">データセット内の計算フィールド。</span><span class="sxs-lookup"><span data-stu-id="c80cb-138">Calculated fields in a dataset.</span></span>  
  
    -   <span data-ttu-id="c80cb-139">データセット内のクエリ パラメーター。</span><span class="sxs-lookup"><span data-stu-id="c80cb-139">Query parameters in a dataset.</span></span>  
  
    -   <span data-ttu-id="c80cb-140">データセット内のフィルター。</span><span class="sxs-lookup"><span data-stu-id="c80cb-140">Filters in a dataset.</span></span>  
  
    -   <span data-ttu-id="c80cb-141">レポート パラメーター。</span><span class="sxs-lookup"><span data-stu-id="c80cb-141">Report parameters.</span></span>  
  
    -   <span data-ttu-id="c80cb-142">Report.Language プロパティ。</span><span class="sxs-lookup"><span data-stu-id="c80cb-142">The Report.Language property.</span></span>  
  
 <span data-ttu-id="c80cb-143">詳細については、「[集計関数リファレンス &#40;レポート ビルダーおよび SSRS&#41;](report-builder-functions-aggregate-functions-reference.md)」および「[合計、集計、および組み込みコレクションの式のスコープ &#40;レポート ビルダーおよび SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c80cb-143">For more information, see [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) and [Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c80cb-144">例</span><span class="sxs-lookup"><span data-stu-id="c80cb-144">Example</span></span>  
 <span data-ttu-id="c80cb-145">"Category" というデータセットに、CategoryList フィールドが含まれているとします。このフィールドには、コンマ区切りのカテゴリの識別子のリスト ("2, 4, 2, 1" など) が含まれています。</span><span class="sxs-lookup"><span data-stu-id="c80cb-145">Assume a dataset called "Category" contains the field CategoryList, which is a field that contains a comma-separated list of category identifers, for example, "2, 4, 2, 1".</span></span>  
  
 <span data-ttu-id="c80cb-146">CategoryNames データセットには、次の表に示すように、カテゴリ識別子とカテゴリ名が格納されています。</span><span class="sxs-lookup"><span data-stu-id="c80cb-146">The dataset CategoryNames contains the category identifier and category name, as shown in the following table.</span></span>  
  
|<span data-ttu-id="c80cb-147">id</span><span class="sxs-lookup"><span data-stu-id="c80cb-147">ID</span></span>|<span data-ttu-id="c80cb-148">Name</span><span class="sxs-lookup"><span data-stu-id="c80cb-148">Name</span></span>|  
|--------|----------|  
|<span data-ttu-id="c80cb-149">1</span><span class="sxs-lookup"><span data-stu-id="c80cb-149">1</span></span>|<span data-ttu-id="c80cb-150">Accessories</span><span class="sxs-lookup"><span data-stu-id="c80cb-150">Accessories</span></span>|  
|<span data-ttu-id="c80cb-151">2</span><span class="sxs-lookup"><span data-stu-id="c80cb-151">2</span></span>|<span data-ttu-id="c80cb-152">Bikes</span><span class="sxs-lookup"><span data-stu-id="c80cb-152">Bikes</span></span>|  
|<span data-ttu-id="c80cb-153">3</span><span class="sxs-lookup"><span data-stu-id="c80cb-153">3</span></span>|<span data-ttu-id="c80cb-154">Clothing</span><span class="sxs-lookup"><span data-stu-id="c80cb-154">Clothing</span></span>|  
|<span data-ttu-id="c80cb-155">4</span><span class="sxs-lookup"><span data-stu-id="c80cb-155">4</span></span>|<span data-ttu-id="c80cb-156">Components</span><span class="sxs-lookup"><span data-stu-id="c80cb-156">Components</span></span>|  
  
 <span data-ttu-id="c80cb-157">識別子のリストに対応する名前を参照するには、`Multilookup` を使用します。</span><span class="sxs-lookup"><span data-stu-id="c80cb-157">To look up the names that correspond to the list of  identifiers, use `Multilookup`.</span></span> <span data-ttu-id="c80cb-158">まず、リストを文字列の配列に分割する必要があります。次に、`Multilookup` を呼び出してカテゴリ名を取得し、結果を連結して文字列にします。</span><span class="sxs-lookup"><span data-stu-id="c80cb-158">You must first split the list into a string array, call `Multilookup` to retrieve the category names, and concatenate the results into a string.</span></span>  
  
 <span data-ttu-id="c80cb-159">Category データセットにバインドされているデータ領域内のテキスト ボックスに次の式を置いた場合、"Bikes, Components, Bikes, Accessories" と表示されます。</span><span class="sxs-lookup"><span data-stu-id="c80cb-159">The following expression, when placed in a text box in a data region bound to the Category dataset, displays "Bikes, Components, Bikes, Accessories":</span></span>  
  
```  
=Join(MultiLookup(Split(Fields!CategoryList.Value,","),  
   Fields!CategoryID.Value,Fields!CategoryName.Value,"Category")),  
   ", ")  
```  
  
## <a name="example"></a><span data-ttu-id="c80cb-160">例</span><span class="sxs-lookup"><span data-stu-id="c80cb-160">Example</span></span>  
 <span data-ttu-id="c80cb-161">ProductColors データセットに、次の表に示すように色の識別子のフィールドである ColorID と、色の値のフィールドである Color が含まれているとします。</span><span class="sxs-lookup"><span data-stu-id="c80cb-161">Assume a dataset ProductColors contains a color identifier field ColorID and a color value field Color, as shown in the following table.</span></span>  
  
|<span data-ttu-id="c80cb-162">ColorID</span><span class="sxs-lookup"><span data-stu-id="c80cb-162">ColorID</span></span>|<span data-ttu-id="c80cb-163">Color</span><span class="sxs-lookup"><span data-stu-id="c80cb-163">Color</span></span>|  
|-------------|-----------|  
|<span data-ttu-id="c80cb-164">1</span><span class="sxs-lookup"><span data-stu-id="c80cb-164">1</span></span>|<span data-ttu-id="c80cb-165">[赤]</span><span class="sxs-lookup"><span data-stu-id="c80cb-165">Red</span></span>|  
|<span data-ttu-id="c80cb-166">2</span><span class="sxs-lookup"><span data-stu-id="c80cb-166">2</span></span>|<span data-ttu-id="c80cb-167">青</span><span class="sxs-lookup"><span data-stu-id="c80cb-167">Blue</span></span>|  
|<span data-ttu-id="c80cb-168">3</span><span class="sxs-lookup"><span data-stu-id="c80cb-168">3</span></span>|<span data-ttu-id="c80cb-169">[緑]</span><span class="sxs-lookup"><span data-stu-id="c80cb-169">Green</span></span>|  
  
 <span data-ttu-id="c80cb-170">複数値パラメーターである *MyColors* が、使用可能な値について、データセットにバインドされていないとします。</span><span class="sxs-lookup"><span data-stu-id="c80cb-170">Assume the multivalue parameter *MyColors* is not bound to a dataset for its available values.</span></span> <span data-ttu-id="c80cb-171">このパラメーターの既定値は、2 および 3 に設定されています。</span><span class="sxs-lookup"><span data-stu-id="c80cb-171">The default values for the parameter are set to 2 and 3.</span></span> <span data-ttu-id="c80cb-172">次の式をテーブル内のテキスト ボックスに置いた場合、パラメーターの複数選択された値がコンマ区切りの一覧として連結され、"Blue, Green" と表示されます。</span><span class="sxs-lookup"><span data-stu-id="c80cb-172">The following expression, when placed in a text box in a table, concatenates the multiple selected values for the parameter into a comma-separated list and displays "Blue, Green".</span></span>  
  
```  
=Join(MultiLookup(Parameters!MyColors.Value,Fields!ColorID.Value,Fields!Color.Value,"ProductColors"),", ")  
```  
  
## <a name="see-also"></a><span data-ttu-id="c80cb-173">参照</span><span class="sxs-lookup"><span data-stu-id="c80cb-173">See Also</span></span>  
 <span data-ttu-id="c80cb-174">[レポートでの式の使用 (レポート ビルダーおよび SSRS)](expression-uses-in-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c80cb-174">[Expression Uses in Reports &#40;Report Builder and SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="c80cb-175">[式の例 (レポート ビルダーおよび SSRS)](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c80cb-175">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="c80cb-176">[式で使用されるデータ型 &#40;レポート ビルダーおよび SSRS&#41;](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c80cb-176">[Data Types in Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="c80cb-177">合計、集計、および組み込みコレクションの式のスコープ (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="c80cb-177">Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;</span></span>](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
