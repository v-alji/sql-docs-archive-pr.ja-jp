---
title: LookupSet 関数 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 7685acfd-1c8d-420c-993c-903236fbe1ff
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4edc7a17f2aa3813e8aa73e538594b5df3aeabc1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640675"
---
# <a name="lookupset-function-report-builder-and-ssrs"></a><span data-ttu-id="b9efa-102">LookupSet 関数 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="b9efa-102">LookupSet Function (Report Builder and SSRS)</span></span>
  <span data-ttu-id="b9efa-103">名前と値のペアを含むデータセットから、指定された名前に対応する一連の値を返します</span><span class="sxs-lookup"><span data-stu-id="b9efa-103">Returns the set of matching values for the specified name from a dataset that contains name/value pairs.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a><span data-ttu-id="b9efa-104">構文</span><span class="sxs-lookup"><span data-stu-id="b9efa-104">Syntax</span></span>  
  
```  
  
LookupSet(source_expression, destination_expression, result_expression, dataset)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b9efa-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b9efa-105">Parameters</span></span>  
 <span data-ttu-id="b9efa-106">*source_expression*</span><span class="sxs-lookup"><span data-stu-id="b9efa-106">*source_expression*</span></span>  
 <span data-ttu-id="b9efa-107">(`Variant`) 現在のスコープ内で評価される式。参照する名前またはキーを指定します。</span><span class="sxs-lookup"><span data-stu-id="b9efa-107">(`Variant`) An expression that is evaluated in the current scope and that specifies the name or key to look up.</span></span> <span data-ttu-id="b9efa-108">たとえば、「 `=Fields!ID.Value` 」のように入力します。</span><span class="sxs-lookup"><span data-stu-id="b9efa-108">For example, `=Fields!ID.Value`.</span></span>  
  
 <span data-ttu-id="b9efa-109">*destination_expression*</span><span class="sxs-lookup"><span data-stu-id="b9efa-109">*destination_expression*</span></span>  
 <span data-ttu-id="b9efa-110">(`Variant`) データセット内の各行に対して評価される式。照合する名前またはキーを指定します。</span><span class="sxs-lookup"><span data-stu-id="b9efa-110">(`Variant`) An expression that is evaluated for each row in a dataset and that specifies the name or key to match on.</span></span> <span data-ttu-id="b9efa-111">たとえば、「 `=Fields!CustomerID.Value` 」のように入力します。</span><span class="sxs-lookup"><span data-stu-id="b9efa-111">For example, `=Fields!CustomerID.Value`.</span></span>  
  
 <span data-ttu-id="b9efa-112">*result_expression*</span><span class="sxs-lookup"><span data-stu-id="b9efa-112">*result_expression*</span></span>  
 <span data-ttu-id="b9efa-113">( `Variant` ) データセット内の行に対して評価される式*source_expression*  = *destination_expression*、は取得する値を指定します。</span><span class="sxs-lookup"><span data-stu-id="b9efa-113">(`Variant`) An expression that is evaluated for the row in the dataset where *source_expression* = *destination_expression*, and that specifies the value to retrieve.</span></span> <span data-ttu-id="b9efa-114">たとえば、「 `=Fields!PhoneNumber.Value` 」のように入力します。</span><span class="sxs-lookup"><span data-stu-id="b9efa-114">For example, `=Fields!PhoneNumber.Value`.</span></span>  
  
 <span data-ttu-id="b9efa-115">*データセット (dataset)*</span><span class="sxs-lookup"><span data-stu-id="b9efa-115">*dataset*</span></span>  
 <span data-ttu-id="b9efa-116">レポート内のデータセットの名前を指定する定数。</span><span class="sxs-lookup"><span data-stu-id="b9efa-116">A constant that specifies the name of a dataset in the report.</span></span> <span data-ttu-id="b9efa-117">たとえば、"ContactInformation" のように指定します。</span><span class="sxs-lookup"><span data-stu-id="b9efa-117">For example, "ContactInformation".</span></span>  
  
## <a name="return"></a><span data-ttu-id="b9efa-118">戻り値</span><span class="sxs-lookup"><span data-stu-id="b9efa-118">Return</span></span>  
 <span data-ttu-id="b9efa-119">`VariantArray` を返します。一致する結果がなかった場合は、`Nothing` を返します。</span><span class="sxs-lookup"><span data-stu-id="b9efa-119">Returns a `VariantArray`, or `Nothing` if there is no match.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b9efa-120">解説</span><span class="sxs-lookup"><span data-stu-id="b9efa-120">Remarks</span></span>  
 <span data-ttu-id="b9efa-121">指定したデータセットで、名前と値のペアについて 1 対多のリレーションシップが存在する場合、`LookupSet` を使用して一連の値を取得します。</span><span class="sxs-lookup"><span data-stu-id="b9efa-121">Use `LookupSet` to retrieve a set of values from the specified dataset for a name/value pair where there is a 1-to-many relationship.</span></span> <span data-ttu-id="b9efa-122">たとえば、テーブル内の顧客識別子に対して `LookupSet` を使用して、データ領域にバインドされていないデータセットから、顧客に関連付けられている電話番号をすべて取得することができます。</span><span class="sxs-lookup"><span data-stu-id="b9efa-122">For example, for a customer identifier in a table, you can use `LookupSet` to retrieve all the associated phone numbers for that customer from a dataset that is not bound to the data region.</span></span>  
  
 <span data-ttu-id="b9efa-123">`LookupSet` を実行すると、次の処理が行われます。</span><span class="sxs-lookup"><span data-stu-id="b9efa-123">`LookupSet` does the following:</span></span>  
  
-   <span data-ttu-id="b9efa-124">ソースの式を現在のスコープ内で評価します。</span><span class="sxs-lookup"><span data-stu-id="b9efa-124">Evaluates the source expression in the current scope.</span></span>  
  
-   <span data-ttu-id="b9efa-125">フィルターを適用した後で、指定されたデータセットの照合順序に基づき、指定されたデータセットの各行に対して変換先の式を評価します。</span><span class="sxs-lookup"><span data-stu-id="b9efa-125">Evaluates the destination expression for each row of the specified dataset after filters have been applied, based on the collation of the specified dataset.</span></span>  
  
-   <span data-ttu-id="b9efa-126">変換元の式と変換先の式が一致するたびに、データセット内のその行に対して結果式を評価します。</span><span class="sxs-lookup"><span data-stu-id="b9efa-126">For each match of source expression and destination expression, evaluates the result expression for that row in the dataset.</span></span>  
  
-   <span data-ttu-id="b9efa-127">結果式の一連の値を返します。</span><span class="sxs-lookup"><span data-stu-id="b9efa-127">Returns the set of result expression values.</span></span>  
  
 <span data-ttu-id="b9efa-128">指定した名前に対応する、名前と値のペアを含むデータセットに 1 対 1 のリレーションシップが存在する場合、このデータセットから 1 つの値を取得するには、[Lookup 関数 &#40;レポート ビルダーおよび SSRS&#41;](report-builder-functions-lookup-function.md) を使用します。</span><span class="sxs-lookup"><span data-stu-id="b9efa-128">To retrieve a single value from a dataset with name/value pairs for a specified name where there is a 1-to-1 relationship, use [Lookup Function &#40;Report Builder and SSRS&#41;](report-builder-functions-lookup-function.md).</span></span> <span data-ttu-id="b9efa-129">一連の `Lookup` 値に対してを呼び出すには、 [Multilookup 関数 &#40;レポートビルダーと SSRS&#41;](report-builder-functions-multilookup-function.md)を使用します。</span><span class="sxs-lookup"><span data-stu-id="b9efa-129">To call `Lookup` for a set of values, use [Multilookup Function &#40;Report Builder and SSRS&#41;](report-builder-functions-multilookup-function.md).</span></span>  
  
 <span data-ttu-id="b9efa-130">次の制限事項が適用されます。</span><span class="sxs-lookup"><span data-stu-id="b9efa-130">The following restrictions apply:</span></span>  
  
-   <span data-ttu-id="b9efa-131">`LookupSet`は、すべてのフィルター式が適用された後に評価されます。</span><span class="sxs-lookup"><span data-stu-id="b9efa-131">`LookupSet` is evaluated after all filter expressions are applied.</span></span>  
  
-   <span data-ttu-id="b9efa-132">1 レベルの参照のみがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="b9efa-132">Only one level of lookup is supported.</span></span> <span data-ttu-id="b9efa-133">変換元、変換先、または結果の式に、Lookup 関数への参照を含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="b9efa-133">A source, destination, or result expression cannot include a reference to a lookup function.</span></span>  
  
-   <span data-ttu-id="b9efa-134">変換元および変換先の式は、同じデータ型として評価される必要があります。</span><span class="sxs-lookup"><span data-stu-id="b9efa-134">Source and destination expressions must evaluate to the same data type.</span></span>  
  
-   <span data-ttu-id="b9efa-135">変換元、変換先、結果の式には、レポート変数またはグループ変数への参照を含めることができません。</span><span class="sxs-lookup"><span data-stu-id="b9efa-135">Source, destination, and result expressions cannot include references to report or group variables.</span></span>  
  
-   <span data-ttu-id="b9efa-136">`LookupSet` は、次のレポート アイテムを求める式として使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="b9efa-136">`LookupSet` cannot be used as an expression for the following report items:</span></span>  
  
    -   <span data-ttu-id="b9efa-137">データ ソースの動的な接続文字列。</span><span class="sxs-lookup"><span data-stu-id="b9efa-137">Dynamic connection strings for a data source.</span></span>  
  
    -   <span data-ttu-id="b9efa-138">データセット内の計算フィールド。</span><span class="sxs-lookup"><span data-stu-id="b9efa-138">Calculated fields in a dataset.</span></span>  
  
    -   <span data-ttu-id="b9efa-139">データセット内のクエリ パラメーター。</span><span class="sxs-lookup"><span data-stu-id="b9efa-139">Query parameters in a dataset.</span></span>  
  
    -   <span data-ttu-id="b9efa-140">データセット内のフィルター。</span><span class="sxs-lookup"><span data-stu-id="b9efa-140">Filters in a dataset.</span></span>  
  
    -   <span data-ttu-id="b9efa-141">レポート パラメーター。</span><span class="sxs-lookup"><span data-stu-id="b9efa-141">Report parameters.</span></span>  
  
    -   <span data-ttu-id="b9efa-142">Report.Language プロパティ。</span><span class="sxs-lookup"><span data-stu-id="b9efa-142">The Report.Language property.</span></span>  
  
 <span data-ttu-id="b9efa-143">詳細については、「[集計関数リファレンス &#40;レポート ビルダーおよび SSRS&#41;](report-builder-functions-aggregate-functions-reference.md)」および「[合計、集計、および組み込みコレクションの式のスコープ &#40;レポート ビルダーおよび SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b9efa-143">For more information, see [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) and [Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b9efa-144">例</span><span class="sxs-lookup"><span data-stu-id="b9efa-144">Example</span></span>  
 <span data-ttu-id="b9efa-145">次の例では、販売区域の識別子である TerritoryGroupID を含むデータセットにテーブルがバインドされているとします。</span><span class="sxs-lookup"><span data-stu-id="b9efa-145">In the following example, assume the table is bound to a dataset that includes a sales territory identifier TerritoryGroupID.</span></span> <span data-ttu-id="b9efa-146">別のデータセットである "Stores" には、販売区域の全店舗の一覧が含まれ、販売区域識別子 ID と、店舗名を表す StoreName が含まれています。</span><span class="sxs-lookup"><span data-stu-id="b9efa-146">A separate dataset called "Stores" contains the list of all stores in a territory and includes the territory identifier ID and the name of the store StoreName.</span></span>  
  
 <span data-ttu-id="b9efa-147">次の式では、"Stores" という名前のデータセットの各行に対して `LookupSet` を実行し、TerritoryGroupID の値を ID と比較します。</span><span class="sxs-lookup"><span data-stu-id="b9efa-147">In the following expression, `LookupSet` compares the value TerritoryGroupID to ID for each row in the dataset called "Stores".</span></span> <span data-ttu-id="b9efa-148">一致するたびに、その行の StoreName フィールドの値が結果セットに追加されます。</span><span class="sxs-lookup"><span data-stu-id="b9efa-148">For each match, the value of the StoreName field for that row is added to the result set.</span></span>  
  
```  
=LookupSet(Fields!TerritoryGroupID.Value, Fields!ID.Value, Fields!StoreName.Value, "Stores")  
```  
  
## <a name="example"></a><span data-ttu-id="b9efa-149">例</span><span class="sxs-lookup"><span data-stu-id="b9efa-149">Example</span></span>  
 <span data-ttu-id="b9efa-150">`LookupSet` はオブジェクトのコレクションを返すため、結果式をテキスト ボックスに直接表示することはできません。</span><span class="sxs-lookup"><span data-stu-id="b9efa-150">Because `LookupSet` returns a collection of objects, you cannot display the result expression directly in a text box.</span></span> <span data-ttu-id="b9efa-151">コレクション内の各オブジェクトの値を文字列として連結することはできます。</span><span class="sxs-lookup"><span data-stu-id="b9efa-151">You can concatenate the value of each object in the collection as a string.</span></span>  
  
 <span data-ttu-id="b9efa-152">一連のオブジェクトから区切り記号付きの文字列を作成するには、[!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 関数である `Join` を使用します。</span><span class="sxs-lookup"><span data-stu-id="b9efa-152">Use the [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] function `Join` create a delimited string from a set of objects.</span></span> <span data-ttu-id="b9efa-153">コンマを区切り記号として使用し、オブジェクトを 1 行に結合します。</span><span class="sxs-lookup"><span data-stu-id="b9efa-153">Use a comma as a separator to combine the objects in a single line.</span></span> <span data-ttu-id="b9efa-154">レンダラーによっては、 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] の改行 (`vbCrLF`) を区切り記号として使用し、各値を新しい 1 つの行に表示することもできます。</span><span class="sxs-lookup"><span data-stu-id="b9efa-154">In some renderers, you might use a [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] line feed (`vbCrLF`) as a separator to list each value on a new line.</span></span>  
  
 <span data-ttu-id="b9efa-155">次の式は、テキストボックスの値プロパティとして使用されている場合、を使用して `Join` リストを作成します。</span><span class="sxs-lookup"><span data-stu-id="b9efa-155">The following expression, when it is used as the Value property for a text box, uses `Join` to create a list.</span></span>  
  
```  
=Join(LookupSet(Fields!TerritoryGroupID.Value, Fields!ID.Value, Fields!StoreName.Value, "Stores"),",")  
```  
  
## <a name="example"></a><span data-ttu-id="b9efa-156">例</span><span class="sxs-lookup"><span data-stu-id="b9efa-156">Example</span></span>  
 <span data-ttu-id="b9efa-157">数回しか表示されないテキスト ボックスでは、テキスト ボックスの値を表示する HTML を生成するカスタム コードを追加してもよいでしょう。</span><span class="sxs-lookup"><span data-stu-id="b9efa-157">For text boxes that only render a few times, you might choose to add custom code to generate HTML to display values in a text box.</span></span> <span data-ttu-id="b9efa-158">テキスト ボックス内に HTML を生成すると追加の処理が必要になるため、数千回も表示されるようなテキスト ボックスの場合、この方法はお勧めできません。</span><span class="sxs-lookup"><span data-stu-id="b9efa-158">HTML in a text box requires extra processing, so this would not be a good choice for a text box that is rendered thousands of times.</span></span>  
  
 <span data-ttu-id="b9efa-159">次の [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 関数をレポート定義の Code ブロックにコピーします。</span><span class="sxs-lookup"><span data-stu-id="b9efa-159">Copy the following [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] functions to a Code block in a report definition.</span></span> <span data-ttu-id="b9efa-160">**MakeList** では、 *result_expression* で返されたオブジェクト配列を受け取り、HTML タグを使用して、順序指定されないリストを生成します。</span><span class="sxs-lookup"><span data-stu-id="b9efa-160">**MakeList** takes the object array that is returned in *result_expression* and builds an unordered list by using HTML tags.</span></span> <span data-ttu-id="b9efa-161">**Length** は、オブジェクト配列内の項目数を返します。</span><span class="sxs-lookup"><span data-stu-id="b9efa-161">**Length** returns the number of items in the object array.</span></span>  
  
```  
Function MakeList(ByVal items As Object()) As String  
   If items Is Nothing Then  
      Return Nothing  
   End If  
  
   Dim builder As System.Text.StringBuilder =   
      New System.Text.StringBuilder()  
   builder.Append("<ul>")  
  
   For Each item As Object In items  
      builder.Append("<li>")  
      builder.Append(item)  
   Next  
   builder.Append("</ul>")  
  
   Return builder.ToString()  
End Function  
  
Function Length(ByVal items as Object()) as Integer  
   If items is Nothing Then  
      Return 0  
   End If  
   Return items.Length  
End Function  
```  
  
## <a name="example"></a><span data-ttu-id="b9efa-162">例</span><span class="sxs-lookup"><span data-stu-id="b9efa-162">Example</span></span>  
 <span data-ttu-id="b9efa-163">HTML を生成するには、関数を呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="b9efa-163">To generate the HTML, you must call the function.</span></span> <span data-ttu-id="b9efa-164">次の式をテキスト ボックスの Value プロパティに貼り付け、テキストのマークアップの種類を HTML に設定します。</span><span class="sxs-lookup"><span data-stu-id="b9efa-164">Paste the following expression in the Value property for the text box and set the markup type for text to HTML.</span></span> <span data-ttu-id="b9efa-165">詳細については、「[レポートへの HTML の追加 &#40;レポート ビルダーおよび SSRS&#41;](add-html-into-a-report-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b9efa-165">For more information, see [Add HTML into a Report &#40;Report Builder and SSRS&#41;](add-html-into-a-report-report-builder-and-ssrs.md).</span></span>  
  
```  
=Code.MakeList(LookupSet(Fields!TerritoryGroupID.Value, Fields!ID.Value, Fields!StoreName.Value, "Stores"))  
```  
  
## <a name="see-also"></a><span data-ttu-id="b9efa-166">参照</span><span class="sxs-lookup"><span data-stu-id="b9efa-166">See Also</span></span>  
 <span data-ttu-id="b9efa-167">[レポートでの式の使用 (レポート ビルダーおよび SSRS)](expression-uses-in-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="b9efa-167">[Expression Uses in Reports &#40;Report Builder and SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="b9efa-168">[式の例 (レポート ビルダーおよび SSRS)](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="b9efa-168">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="b9efa-169">[式で使用されるデータ型 &#40;レポート ビルダーおよび SSRS&#41;](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="b9efa-169">[Data Types in Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="b9efa-170">合計、集計、および組み込みコレクションの式のスコープ (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="b9efa-170">Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;</span></span>](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
