---
title: モデルフィルターの構文と例 (Analysis Services データマイニング) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- model filter [data mining]
- filter syntax [data mining]
- filters [data mining]
- filters [Analysis Services]
ms.assetid: c729d9b3-8fda-405e-9497-52b2d7493eae
author: minewiskan
ms.author: owend
ms.openlocfilehash: f7ca200d179c0fe81b948793a4b4478f71502657
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712650"
---
# <a name="model-filter-syntax-and-examples-analysis-services---data-mining"></a><span data-ttu-id="763da-102">モデル フィルターの構文と例 (Analysis Services - データ マイニング)</span><span class="sxs-lookup"><span data-stu-id="763da-102">Model Filter Syntax and Examples (Analysis Services - Data Mining)</span></span>
  <span data-ttu-id="763da-103">ここでは、モデル フィルターの構文について詳しく説明し、サンプル式を示します。</span><span class="sxs-lookup"><span data-stu-id="763da-103">This section provides detailed information about the syntax for model filters, together with sample expressions.</span></span>  
  
 
  
##  <a name="filter-syntax"></a><a name="bkmk_Syntax"></a><span data-ttu-id="763da-104">フィルター構文</span><span class="sxs-lookup"><span data-stu-id="763da-104">Filter Syntax</span></span>  
 <span data-ttu-id="763da-105">一般に、フィルター式は WHERE 句の内容に相当します。</span><span class="sxs-lookup"><span data-stu-id="763da-105">Filter expressions generally are equivalent to the content of a WHERE clause.</span></span> <span data-ttu-id="763da-106">`AND`、`OR`、および `NOT` の論理演算子を使用すると、複数の条件を結合できます。</span><span class="sxs-lookup"><span data-stu-id="763da-106">You can connect multiple conditions by using the logical operators `AND`, `OR`, and `NOT`.</span></span>  
  
 <span data-ttu-id="763da-107">入れ子になったテーブルでは、`EXISTS` 演算子と `NOT EXISTS` 演算子も使用できます。</span><span class="sxs-lookup"><span data-stu-id="763da-107">In nested tables, you can also use the `EXISTS` and `NOT EXISTS` operators.</span></span> <span data-ttu-id="763da-108">サブクエリから少なくとも 1 行が返される場合、`EXISTS` 条件が `true` と評価されます。</span><span class="sxs-lookup"><span data-stu-id="763da-108">An `EXISTS` condition evaluates to `true` if the subquery returns at least one row.</span></span> <span data-ttu-id="763da-109">これは、入れ子になったテーブルに特定の値があるケース (ある品目を少なくとも 1 回購入した顧客など) のみをモデルで使用する場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="763da-109">This is useful in cases where you want to restrict the model to cases that contain a particular value in the nested table: for example, customers who have purchased an item at least once.</span></span>  
  
 <span data-ttu-id="763da-110">サブクエリに指定した条件が存在しない場合、`NOT EXISTS` 条件が `true` と評価されます。</span><span class="sxs-lookup"><span data-stu-id="763da-110">A `NOT EXISTS` condition evaluates to `true` if the condition specified in the subquery does not exist.</span></span> <span data-ttu-id="763da-111">特定の品目を購入したことがない顧客のみをモデルで使用する場合などに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="763da-111">An example is when you want to restrict the model to customers who have never purchased a particular item.</span></span>  
  
 <span data-ttu-id="763da-112">一般的な構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="763da-112">The general syntax is as follows:</span></span>  
  
```  
<filter>::=<predicate list>  | ( <predicate list> )  
<predicate list>::= <predicate> | [<logical_operator> <predicate list>]   
<logical_operator::= AND| OR  
<predicate>::= NOT <predicate>|( <predicate> ) <avPredicate> | <nestedTablePredicate> | ( <predicate> )   
<avPredicate>::= <columnName> <operator> <scalar> | <columnName> IS [NOT] NULL  
<operator>::= = | != | <> | > | >= | < | <=  
<nestedTablePredicate>::= EXISTS (<subquery>)  
<subquery>::=SELECT * FROM <columnName>[ WHERE  <predicate list> ]  
```  
  
 <span data-ttu-id="763da-113">*filter*</span><span class="sxs-lookup"><span data-stu-id="763da-113">*filter*</span></span>  
 <span data-ttu-id="763da-114">論理演算子で結合された 1 つ以上の述語が含まれます。</span><span class="sxs-lookup"><span data-stu-id="763da-114">Contains one or more predicates, connected by logical operators.</span></span>  
  
 <span data-ttu-id="763da-115">*predicate list*</span><span class="sxs-lookup"><span data-stu-id="763da-115">*predicate list*</span></span>  
 <span data-ttu-id="763da-116">論理演算子で区切られた 1 つ以上の有効なフィルター式です。</span><span class="sxs-lookup"><span data-stu-id="763da-116">One or more valid filter expressions, separated by logical operators.</span></span>  
  
 <span data-ttu-id="763da-117">*columnName*</span><span class="sxs-lookup"><span data-stu-id="763da-117">*columnName*</span></span>  
 <span data-ttu-id="763da-118">マイニング構造列の名前です。</span><span class="sxs-lookup"><span data-stu-id="763da-118">The name of a mining structure column.</span></span>  
  
 <span data-ttu-id="763da-119">logical operator</span><span class="sxs-lookup"><span data-stu-id="763da-119">logical operator</span></span>  
 <span data-ttu-id="763da-120">`AND`, `OR`, `NOT`</span><span class="sxs-lookup"><span data-stu-id="763da-120">`AND`, `OR`, `NOT`</span></span>  
  
 <span data-ttu-id="763da-121">*avPredicate*</span><span class="sxs-lookup"><span data-stu-id="763da-121">*avPredicate*</span></span>  
 <span data-ttu-id="763da-122">スカラー マイニング構造列にのみ適用できるフィルター式です。</span><span class="sxs-lookup"><span data-stu-id="763da-122">Filter expression that can be applied to scalar mining structure column only.</span></span> <span data-ttu-id="763da-123">*avPredicate* 式は、モデル フィルターと入れ子になったテーブルのフィルターの両方で使用できます。</span><span class="sxs-lookup"><span data-stu-id="763da-123">An *avPredicate* expression can be used in both model filters or nested table filters.</span></span>  
  
 <span data-ttu-id="763da-124">次のいずれかの演算子を使用する式は、連続列にのみ適用できます。</span><span class="sxs-lookup"><span data-stu-id="763da-124">An expression that uses any of the following operators can only be applied to a continuous column.</span></span> <span data-ttu-id="763da-125">:</span><span class="sxs-lookup"><span data-stu-id="763da-125">:</span></span>  
  
-   <span data-ttu-id="763da-126">**\<**(より小さい)</span><span class="sxs-lookup"><span data-stu-id="763da-126">**\<** (less than)</span></span>  
  
-   <span data-ttu-id="763da-127">**>**(より大きい)</span><span class="sxs-lookup"><span data-stu-id="763da-127">**>** (greater than)</span></span>  
  
-   <span data-ttu-id="763da-128">**>=**(以上)</span><span class="sxs-lookup"><span data-stu-id="763da-128">**>=** (greater than or equal to)</span></span>  
  
-   <span data-ttu-id="763da-129">**\<=**(以下)</span><span class="sxs-lookup"><span data-stu-id="763da-129">**\<=** (less than or equal to)</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="763da-130">データ型にかかわらず、`Discrete`、`Discretized`、または `Key` の型の列にこれらの演算子を適用することはできません。</span><span class="sxs-lookup"><span data-stu-id="763da-130">Regardless of the data type, these operators cannot be applied to a column that has the type `Discrete`, `Discretized`, or `Key`.</span></span>  
  
 <span data-ttu-id="763da-131">次のいずれかの演算子を使用する式は、連続列、不連続列、離散化列、またはキー列に適用できます。</span><span class="sxs-lookup"><span data-stu-id="763da-131">An expression that uses any of the following operators can be applied to a continuous, discrete, discretized, or key column:</span></span>  
  
-   <span data-ttu-id="763da-132">**=** str</span><span class="sxs-lookup"><span data-stu-id="763da-132">**=** (equals)</span></span>  
  
-   <span data-ttu-id="763da-133">**! =** (等しくない)</span><span class="sxs-lookup"><span data-stu-id="763da-133">**!=** (not equal to)</span></span>  
  
-   <span data-ttu-id="763da-134">**IS NULL**</span><span class="sxs-lookup"><span data-stu-id="763da-134">**IS NULL**</span></span>  
  
 <span data-ttu-id="763da-135">*avPredicate*を離散化列に適用する場合、フィルターに使用される値は、特定のバケット内の任意の値です。</span><span class="sxs-lookup"><span data-stu-id="763da-135">If the argument, *avPredicate*, applies to a discretized column, the value used in the filter can be any value in a specific bucket.</span></span>  
  
 <span data-ttu-id="763da-136">つまり、 `AgeDisc = '25-35'`などの条件を定義する代わりに、その範囲の値を計算して使用します。</span><span class="sxs-lookup"><span data-stu-id="763da-136">In other words, you do not define the condition as `AgeDisc = '25-35'`, but instead compute and then use a value from that interval.</span></span>  
  
 <span data-ttu-id="763da-137">たとえば  `AgeDisc = 27`  は、27 と同じ範囲 (ここでは 25 ～ 35) 内の任意の値を意味します。</span><span class="sxs-lookup"><span data-stu-id="763da-137">Example:  `AgeDisc = 27`  means any value in the same interval as 27, which in this case is 25-35.</span></span>  
  
 <span data-ttu-id="763da-138">*nestedTablePredicate*</span><span class="sxs-lookup"><span data-stu-id="763da-138">*nestedTablePredicate*</span></span>  
 <span data-ttu-id="763da-139">入れ子になったテーブルに適用するフィルター式です。</span><span class="sxs-lookup"><span data-stu-id="763da-139">Filter expression that applies to a nested table.</span></span> <span data-ttu-id="763da-140">モデル フィルターでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="763da-140">Can be used in model filters only.</span></span>  
  
 <span data-ttu-id="763da-141">*nestedTablePredicate*のサブクエリの引数は、テーブルのマイニング構造列にのみ適用できます。</span><span class="sxs-lookup"><span data-stu-id="763da-141">The sub-query argument of the argument, *nestedTablePredicate*, can only apply to a table mining structure column</span></span>  
  
 <span data-ttu-id="763da-142">サブクエリ</span><span class="sxs-lookup"><span data-stu-id="763da-142">subquery</span></span>  
 <span data-ttu-id="763da-143">SELECT ステートメントの後に有効な述語または述語の一覧を指定します。</span><span class="sxs-lookup"><span data-stu-id="763da-143">A SELECT statement followed by a valid predicate or list of predicates.</span></span>  
  
 <span data-ttu-id="763da-144">すべての述語が *avPredicates*で示される型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="763da-144">All the predicates must be of the type described in *avPredicates*.</span></span> <span data-ttu-id="763da-145">また、述語で、 *columnName*引数を指定して参照できるのは、現在の入れ子になったテーブルに含まれている列だけです。</span><span class="sxs-lookup"><span data-stu-id="763da-145">Furthermore, the predicates can refer only to columns that are included in the current nested table, identified by the argument, *columnName*.</span></span>  
  
### <a name="limitations-on-filter-syntax"></a><span data-ttu-id="763da-146">フィルター構文に関する制限事項</span><span class="sxs-lookup"><span data-stu-id="763da-146">Limitations on Filter Syntax</span></span>  
 <span data-ttu-id="763da-147">フィルターには次の制限が適用されます。</span><span class="sxs-lookup"><span data-stu-id="763da-147">The following restrictions apply to filters:</span></span>  
  
-   <span data-ttu-id="763da-148">フィルターに指定できるのは、単純な述語だけです。</span><span class="sxs-lookup"><span data-stu-id="763da-148">A filter can contain only simple predicates.</span></span> <span data-ttu-id="763da-149">これらには、算術演算子、スカラー、および列名が含まれます。</span><span class="sxs-lookup"><span data-stu-id="763da-149">These include mathematical operators, scalars, and column names.</span></span>  
  
-   <span data-ttu-id="763da-150">フィルター構文では、ユーザー定義関数がサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="763da-150">User-defined functions are not supported in the filter syntax.</span></span>  
  
-   <span data-ttu-id="763da-151">フィルター構文では、ブール型以外の演算子 (プラス記号やマイナス記号など) がサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="763da-151">Non-Boolean operators, such as the plus or minus signs, are not supported in the filter syntax.</span></span>  
  
## <a name="examples-of-filters"></a><span data-ttu-id="763da-152">フィルターの例</span><span class="sxs-lookup"><span data-stu-id="763da-152">Examples of Filters</span></span>  
 <span data-ttu-id="763da-153">次の例は、マイニング モデルに適用するフィルターの使用方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="763da-153">The following examples demonstrate the use of filters applied to a mining model.</span></span> <span data-ttu-id="763da-154">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]を使用してフィルター式を作成する場合、 **[プロパティ]** ウィンドウや、フィルターのダイアログ ボックスの **[式]** ペインには、WITH FILTER キーワードより後の文字列だけが表示されます。</span><span class="sxs-lookup"><span data-stu-id="763da-154">If you create the filter expression by using [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], in the **Property** window and the **Expression** pane of the filter dialog box, you would see only the string that appears after the WITH FILTER keywords.</span></span> <span data-ttu-id="763da-155">ここでは、列の型と使用法をわかりやすくするため、マイニング構造の定義も示します。</span><span class="sxs-lookup"><span data-stu-id="763da-155">Here, the definition of the mining structure is included to make it easier to understand the column type and usage.</span></span>  
  
###  <a name="example-1-typical-case-level-filtering"></a><a name="bkmk_Ex1"></a> <span data-ttu-id="763da-156">例 1 : 一般的なケースレベルのフィルター処理</span><span class="sxs-lookup"><span data-stu-id="763da-156">Example 1: Typical Case-Level Filtering</span></span>  
 <span data-ttu-id="763da-157">次の例は、モデルに使用するケースを、職業が Architect で 31 歳以上の顧客だけに制限するための、単純なフィルターです。</span><span class="sxs-lookup"><span data-stu-id="763da-157">This example shows a simple filter that restricts the cases used in the model to customers whose occupation is architect and whose age is over 30.</span></span>  
  
```  
ALTER MINING STRUCTURE MyStructure  ADD MINING MODEL MyModel_1  
(  
CustomerId,  
Age,  
Occupation,  
MaritalStatus PREDICT  
)  
WITH FILTER (Age > 30 AND Occupation='Architect')  
```  
  

  
###  <a name="example-2-case-level-filtering-using-nested-table-attributes"></a><a name="bkmk_Ex2"></a> <span data-ttu-id="763da-158">例 2: 入れ子になったテーブルの属性を使用したケースレベルのフィルター処理</span><span class="sxs-lookup"><span data-stu-id="763da-158">Example 2: Case-Level Filtering using Nested Table Attributes</span></span>  
 <span data-ttu-id="763da-159">入れ子になったテーブルがマイニング構造に含まれている場合は、入れ子になったテーブルに値が存在するかどうかに基づいてフィルター処理することも、特定の値を含む入れ子になったテーブル行に基づいてフィルター処理することもできます。</span><span class="sxs-lookup"><span data-stu-id="763da-159">If your mining structure contains nested tables, you can either filter on the existence of a value in a nested table, or filter on nested table rows that contain a specific value.</span></span> <span data-ttu-id="763da-160">次の例では、モデルに使用するケースを、Milk を購入したことがある 31 歳以上の顧客だけに制限します。</span><span class="sxs-lookup"><span data-stu-id="763da-160">This example restricts the cases used for the model to customers over the age of 30 who made at least one purchase that included milk.</span></span>  
  
 <span data-ttu-id="763da-161">この例からわかるとおり、フィルターには、モデルに含まれている列のみを使用する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="763da-161">As this example shows, it is not necessary that the filter use only columns that are included in the model.</span></span> <span data-ttu-id="763da-162">入れ子になったテーブル **Products** はマイニング構造の一部ですが、マイニング モデルには含まれていません。</span><span class="sxs-lookup"><span data-stu-id="763da-162">The nested table **Products** is part of the mining structure, but is not included in the mining model.</span></span> <span data-ttu-id="763da-163">それでも、この入れ子になったテーブル内の値や属性に基づいてフィルター処理を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="763da-163">However, you can still filter on values and attributes in the nested table.</span></span> <span data-ttu-id="763da-164">これらのケースの詳細を表示するには、ドリルスルーを有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="763da-164">To view the details of these cases, drillthrough must be enabled.</span></span>  
  
```  
ALTER MINING STRUCTURE MyStructure  ADD MINING MODEL MyModel_2  
(  
CustomerId,  
Age,  
Occupation,  
MaritalStatus PREDICT  
)  
WITH DRILLTHROUGH,   
FILTER (Age > 30 AND EXISTS (SELECT * FROM Products WHERE ProductName='Milk')  
)  
```  
  
 
  
###  <a name="example-3-case-level-filtering-on-multiple-nested-table-attributes"></a><a name="bkmk_Ex3"></a> <span data-ttu-id="763da-165">例 3: 入れ子になったテーブルの複数の属性に基づくケースレベルのフィルター処理</span><span class="sxs-lookup"><span data-stu-id="763da-165">Example 3: Case-Level Filtering on Multiple Nested Table Attributes</span></span>  
 <span data-ttu-id="763da-166">次の例では、3 つの部分から成るフィルターを示します。ケース テーブルに適用する条件、入れ子になったテーブルの属性に対する条件、入れ子になったテーブル列の特定の値に対する条件の 3 つです。</span><span class="sxs-lookup"><span data-stu-id="763da-166">This example shows a three-part filter: a condition applies to the case table, another condition to an attribute in the nested table, and another condition on a specific value in one of the nested table columns.</span></span>  
  
 <span data-ttu-id="763da-167">フィルターの最初の条件 `Age > 30`は、ケース テーブル内の列に適用されます。</span><span class="sxs-lookup"><span data-stu-id="763da-167">The first condition in the filter, `Age > 30`, applies to a column in the case table.</span></span> <span data-ttu-id="763da-168">残りの条件は、入れ子になったテーブルに適用されます。</span><span class="sxs-lookup"><span data-stu-id="763da-168">The remaining conditions apply to the nested table.</span></span>  
  
 <span data-ttu-id="763da-169">2 番目の条件 `EXISTS (SELECT * FROM Products WHERE ProductName='Milk'`では、入れ子になったテーブル内に、Milk を含む購入が 1 回以上存在するかどうかを調べます。</span><span class="sxs-lookup"><span data-stu-id="763da-169">The second condition, `EXISTS (SELECT * FROM Products WHERE ProductName='Milk'`, checks for the presence of at least one purchase in the nested table that included milk.</span></span> <span data-ttu-id="763da-170">3 番目の条件 `Quantity>=2`は、顧客が 2 単位以上の Milk を一度に購入している必要があることを意味します。</span><span class="sxs-lookup"><span data-stu-id="763da-170">The third condition, `Quantity>=2`, means that the customer must have purchased at least two units of milk in a single transaction.</span></span>  
  
```  
ALTER MINING STRUCTURE MyStructure  ADD MINING MODEL MyModel_3  
(  
CustomerId,  
Age,  
Occupation,  
MaritalStatus PREDICT,  
Products PREDICT  
(  
ProductName KEY,  
Quantity        
)  
)  
FILTER (Age > 30 AND EXISTS (SELECT * FROM Products WHERE ProductName='Milk'  AND Quantity >= 2)   
)  
```  
  

  
###  <a name="example-4-case-level-filtering-on-absence-of-nested-table-attributes"></a><a name="bkmk_Ex4"></a> <span data-ttu-id="763da-171">例 4: 入れ子になったテーブルの属性が存在しないことに基づくケースレベルのフィルター処理</span><span class="sxs-lookup"><span data-stu-id="763da-171">Example 4: Case-Level Filtering On Absence of Nested Table Attributes</span></span>  
 <span data-ttu-id="763da-172">次の例では、入れ子になったテーブル内に属性が存在しないケースをフィルター選択することで、特定の品目を購入しなかった顧客のケースに制限する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="763da-172">This example shows how to limit cases to customer who did not purchase a specific item, by filtering on the absence of an attribute in the nested table.</span></span> <span data-ttu-id="763da-173">この場合、Milk を購入したことがない 31 歳以上の顧客を使用して、モデルのトレーニングが行われます。</span><span class="sxs-lookup"><span data-stu-id="763da-173">In this example, the model is trained using customers over the age of 30 who have never bought milk.</span></span>  
  
```  
ALTER MINING STRUCTURE MyStructure  ADD MINING MODEL MyModel_4  
(  
CustomerId,  
Age,  
Occupation,  
MaritalStatus PREDICT,  
Products PREDICT  
(  
ProductName  
)  
)  
FILTER (Age > 30 AND NOT EXISTS (SELECT * FROM Products WHERE ProductName='Milk') )  
```  
  

  
###  <a name="example-5-filtering-on-multiple-nested-table-values"></a><a name="bkmk_Ex5"></a> <span data-ttu-id="763da-174">例 5: 入れ子になったテーブルの複数の値に基づくフィルター処理</span><span class="sxs-lookup"><span data-stu-id="763da-174">Example 5: Filtering on Multiple Nested Table Values</span></span>  
 <span data-ttu-id="763da-175">次の例では、入れ子になったテーブルのフィルター処理について説明します。</span><span class="sxs-lookup"><span data-stu-id="763da-175">The purpose of the example is to show nested table filtering.</span></span> <span data-ttu-id="763da-176">入れ子になったテーブルのフィルターは、ケース フィルターの後に適用され、入れ子になったテーブル行だけを制限します。</span><span class="sxs-lookup"><span data-stu-id="763da-176">The nested table filter is applied after the case filter, and only restricts nested table rows.</span></span>  
  
 <span data-ttu-id="763da-177">EXISTS を指定していないため、このモデルには、空の入れ子になったテーブルを持つケースが複数含まれる場合があります。</span><span class="sxs-lookup"><span data-stu-id="763da-177">This model could contain multiple cases with empty nested tables because EXISTS is not specified.</span></span>  
  
```  
ALTER MINING STRUCTURE MyStructure  ADD MINING MODEL MyModel_5  
(  
CustomerId,  
Age,  
Occupation,  
MaritalStatus PREDICT,  
Products PREDICT  
(  
ProductName KEY,  
Quantity        
) WITH FILTER(ProductName='Milk' OR ProductName='bottled water')  
)  
WITH DRILLTHROUGH  
```  
  

  
###  <a name="example-6-filtering-on-nested-table-attributes-and-exists"></a><a name="bkmk_Ex6"></a> <span data-ttu-id="763da-178">例 6: 入れ子になったテーブルの属性および EXISTS に基づくフィルター処理</span><span class="sxs-lookup"><span data-stu-id="763da-178">Example 6: Filtering on Nested Table Attributes and EXISTS</span></span>  
 <span data-ttu-id="763da-179">次の例では、入れ子になったテーブルに対するフィルターで、Milk か bottled water のいずれかを含む行に制限します。</span><span class="sxs-lookup"><span data-stu-id="763da-179">In this example, the filter on the nested table restricts the rows to those that contain either milk or bottled water.</span></span> <span data-ttu-id="763da-180">さらに、`EXISTS` ステートメントを使用してモデル内のケースを制限します。</span><span class="sxs-lookup"><span data-stu-id="763da-180">Then, the cases in the model are restricted by using an `EXISTS` statement.</span></span> <span data-ttu-id="763da-181">これにより、入れ子になったテーブルが空にならないようにします。</span><span class="sxs-lookup"><span data-stu-id="763da-181">This makes sure that the nested table is not empty.</span></span>  
  
```  
ALTER MINING STRUCTURE MyStructure  ADD MINING MODEL MyModel_6  
(  
CustomerId,  
Age,  
Occupation,  
MaritalStatus PREDICT,  
Products PREDICT  
(  
ProductName KEY,  
Quantity        
) WITH FILTER(ProductName='Milk' OR ProductName='bottled water')  
)  
FILTER (EXISTS (Products))  
```  
  

  
###  <a name="example-7-complex-filter-combinations"></a><a name="bkmk_Ex7"></a> <span data-ttu-id="763da-182">例 7: フィルターの複雑な組み合わせ</span><span class="sxs-lookup"><span data-stu-id="763da-182">Example 7: Complex Filter Combinations</span></span>  
 <span data-ttu-id="763da-183">次のモデルのシナリオは例 4 と似ていますが、はるかに複雑です。</span><span class="sxs-lookup"><span data-stu-id="763da-183">The scenario for this model resembles that of Example 4, but is far more complex.</span></span> <span data-ttu-id="763da-184">入れ子になったテーブルの "製品**Onsale**" には、[ `(OnSale)` ProductName] に表示されている製品に対して [ **onsale** ] の値を指定する必要があることを示すフィルター条件があり `true` ます。 **ProductName**</span><span class="sxs-lookup"><span data-stu-id="763da-184">The nested table, **ProductsOnSale**, has the filter condition `(OnSale)` meaning that the value of **OnSale** must be `true` for the product listed in **ProductName**.</span></span> <span data-ttu-id="763da-185">この **[OnSale]** は構造列です。</span><span class="sxs-lookup"><span data-stu-id="763da-185">Here, **OnSale** is a structure column.</span></span>  
  
 <span data-ttu-id="763da-186">フィルターの2番目の部分 (製品**Notonsale**) は、この構文を繰り返しますが、 **onsale**の値がである製品に対してフィルター処理を `not true``(!OnSale)` 行います。</span><span class="sxs-lookup"><span data-stu-id="763da-186">The second part of the filter, for **ProductsNotOnSale**, repeats this syntax, but filters on products for which the value of **OnSale** is `not true``(!OnSale)`.</span></span>  
  
 <span data-ttu-id="763da-187">最後にこれらの条件を組み合わせ、ケース テーブルに対する制限をさらに 1 つ追加します。</span><span class="sxs-lookup"><span data-stu-id="763da-187">Finally, the conditions are combined and one additional restriction is added to the case table.</span></span> <span data-ttu-id="763da-188">その結果、25 歳以上のすべての顧客を対象として、 **[ProductsOnSale]** の一覧内のケースに基づき、 **[ProductsNotOnSale]** の一覧内の製品の購入が予測されます。</span><span class="sxs-lookup"><span data-stu-id="763da-188">The result is to predict purchases of products in the **ProductsNotOnSale** list, based on the cases that are included in the **ProductsOnSale** list, for all customers over the age of 25.</span></span>  
  
 `ALTER MINING STRUCTURE MyStructure  ADD MINING MODEL MyModel_7`  
  
 `(`  
  
 `CustomerId,`  
  
 `Age,`  
  
 `Occupation,`  
  
 `MaritalStatus,`  
  
 `ProductsOnSale`  
  
 `(`  
  
 `ProductName KEY`  
  
 `) WITH FILTER(OnSale),`  
  
 `ProductsNotOnSale PREDICT ONLY`  
  
 `(`  
  
 `ProductName KEY`  
  
 `) WITH FILTER(!OnSale)`  
  
 `)`  
  
 `WITH DRILLTHROUGH,`  
  
 `FILTER (EXISTS (ProductsOnSale) AND EXISTS(ProductsNotOnSale) AND Age > 25)`  
  
  
  
###  <a name="example-8-filtering-on-dates"></a><a name="bkmk_Ex8"></a> <span data-ttu-id="763da-189">例 8: 日付に基づくフィルター処理</span><span class="sxs-lookup"><span data-stu-id="763da-189">Example 8: Filtering on Dates</span></span>  
 <span data-ttu-id="763da-190">他のデータと同様に、日付に基づいて入力列をフィルター処理することができます。</span><span class="sxs-lookup"><span data-stu-id="763da-190">You can filter input columns on dates, as you would any other data.</span></span> <span data-ttu-id="763da-191">日付/時刻の型の列に含まれる日付は連続値です。そのため、大なり (>) や小なり (<) などの演算子を使用して、日付範囲を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="763da-191">Dates contained in a column of type date/time are continuous values; therefore, you can specify a date range by using operators such as greater than (>) or less than (<).</span></span> <span data-ttu-id="763da-192">データ ソースの日付が連続するデータ型で表されず、不連続値またはテキスト値として表されている場合は、日付範囲に基づいてフィルター処理を行うことはできず、個々の不連続値を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="763da-192">If your data source does not represent dates by a Continuous data type, but as discrete or text values, you cannot filter on a date range, but must specify individual discrete values.</span></span>  
  
 <span data-ttu-id="763da-193">ただし、フィルターに使用されている日付列がモデルのキー列でもある場合は、時系列モデルの日付列に基づくフィルターを作成できません。</span><span class="sxs-lookup"><span data-stu-id="763da-193">However, you cannot create a filter on the date column in a time series model if the date column used for the filter is also the key column for the model.</span></span> <span data-ttu-id="763da-194">これは、時系列モデルおよびシーケンス クラスター モデルでは、日付列が `KeyTime` 型または `KeySequence` 型として処理される場合があるためです。</span><span class="sxs-lookup"><span data-stu-id="763da-194">That is because, in time series models and sequence clustering models, the date column might be handled as type `KeyTime` or `KeySequence`.</span></span>  
  
 <span data-ttu-id="763da-195">時系列モデルで連続する日付に対してフィルター処理を行う必要がある場合は、マイニング構造で列のコピーを作成し、新しい列に基づいてモデルをフィルター処理することができます。</span><span class="sxs-lookup"><span data-stu-id="763da-195">If you need to filter on continuous dates in a time series model, you can create a copy of the column in the mining structure, and filter the model on the new column.</span></span>  
  
 <span data-ttu-id="763da-196">たとえば、次の式は、Forecasting モデルに追加された、`Continuous` 型の日付列に対するフィルターを表しています。</span><span class="sxs-lookup"><span data-stu-id="763da-196">For example, the following expression represents a filter on a date column of type `Continuous` that has been added to the Forecasting model.</span></span>  
  
 `=[DateCopy] > '12:31:2003:00:00:00'`  
  
> [!NOTE]  
>  <span data-ttu-id="763da-197">モデルに列を追加すると、結果に影響を及ぼす場合があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="763da-197">Note that any extra columns that you add to the model might affect the results.</span></span> <span data-ttu-id="763da-198">そのため、系列の計算に列を使用しない場合は、マイニング構造のみに列を追加し、モデルには追加しないでください。</span><span class="sxs-lookup"><span data-stu-id="763da-198">Therefore, if you do not want the column to be used in computation of the series, you should add the column only to the mining structure, and not to the model.</span></span> <span data-ttu-id="763da-199">列のモデル フラグを `PredictOnly` または `Ignore` に設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="763da-199">You can also set the model flag on the column to `PredictOnly` or to `Ignore`.</span></span> <span data-ttu-id="763da-200">詳細については、「[モデリング フラグ &#40;データ マイニング&#41;](modeling-flags-data-mining.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="763da-200">For more information, see [Modeling Flags &#40;Data Mining&#41;](modeling-flags-data-mining.md).</span></span>  
  
 <span data-ttu-id="763da-201">その他のモデルの種類では、他の列の場合と同様に、入力条件やフィルター条件として日付を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="763da-201">For other model types, you can use dates as input criteria or filter criteria just like you would in any other column.</span></span> <span data-ttu-id="763da-202">ただし、`Continuous` データ型でサポートされていない、特定のレベルの粒度を使用する必要がある場合は、複数の式を使用してフィルター処理と分析で使用する単位を抽出することで、データ ソースの派生値を作成できます。</span><span class="sxs-lookup"><span data-stu-id="763da-202">However, if you need to use a specific level of granularity that is not supported by a `Continuous` data type, you can create a derived value in the data source by using expressions to extract the unit to use in filtering and analysis.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="763da-203">フィルター条件として日付を指定する場合は、現在の OS の日付の形式に関係なく、 `mm/dd/yyyy`という形式を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="763da-203">When you specify a dates as filter criteria, you must use the following format, regardless of the date format for the current OS: `mm/dd/yyyy`.</span></span> <span data-ttu-id="763da-204">他の形式では、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="763da-204">Any other format results in an error.</span></span>  
  
 <span data-ttu-id="763da-205">たとえば、コール センターの結果にフィルターを適用して週末のみを表示する場合、データ ソース ビューに各日付の曜日名を抽出する式を作成して、その曜日名の値を入力に使用したり、フィルター処理で不連続値として使用したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="763da-205">For example, if you want to filter your call center results to show only weekends, you can create an expression in the data source view that extracts the weekday name for each date, and then use that weekday name value for input or as a discrete value in filtering.</span></span> <span data-ttu-id="763da-206">繰り返し値はモデルに影響を及ぼす可能性があるため、日付列と不連続値ではなく、1 列のみを使用する必要があることを忘れないでください。</span><span class="sxs-lookup"><span data-stu-id="763da-206">Just remember that repeating values can affect the model, so you should use only one of the columns, not the date column plus the derived value.</span></span>  
  
 
  
## <a name="see-also"></a><span data-ttu-id="763da-207">参照</span><span class="sxs-lookup"><span data-stu-id="763da-207">See Also</span></span>  
 <span data-ttu-id="763da-208">[マイニングモデルのフィルター &#40;Analysis Services データマイニング&#41;](mining-models-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="763da-208">[Filters for Mining Models &#40;Analysis Services - Data Mining&#41;](mining-models-analysis-services-data-mining.md) </span></span>  
 [<span data-ttu-id="763da-209">テストおよび検証 &#40;データ マイニング&#41;</span><span class="sxs-lookup"><span data-stu-id="763da-209">Testing and Validation &#40;Data Mining&#41;</span></span>](testing-and-validation-data-mining.md)  
  
  
