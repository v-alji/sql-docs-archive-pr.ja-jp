---
title: 集計変換 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.aggregatetrans.f1
helpviewer_keywords:
- IsBig property
- aggregate functions [Integration Services]
- Aggregate transformation [Integration Services]
- large data, SSIS transformations
ms.assetid: 2871cf2a-fbd3-41ba-807d-26ffff960e81
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9e69d741ddd2bd14a31d7aa79a8c825641713523
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712209"
---
# <a name="aggregate-transformation"></a><span data-ttu-id="985f4-102">集計変換</span><span class="sxs-lookup"><span data-stu-id="985f4-102">Aggregate Transformation</span></span>
  <span data-ttu-id="985f4-103">集計変換は Average などの集計関数を列の値に適用し、その結果を変換出力にコピーします。</span><span class="sxs-lookup"><span data-stu-id="985f4-103">The Aggregate transformation applies aggregate functions, such as Average, to column values and copies the results to the transformation output.</span></span> <span data-ttu-id="985f4-104">集計変換では、集計関数の他に GROUP BY 句を使用して集計範囲のグループを指定できます。</span><span class="sxs-lookup"><span data-stu-id="985f4-104">Besides aggregate functions, the transformation provides the GROUP BY clause, which you can use to specify groups to aggregate across.</span></span>  
  
## <a name="operations"></a><span data-ttu-id="985f4-105">操作</span><span class="sxs-lookup"><span data-stu-id="985f4-105">Operations</span></span>  
 <span data-ttu-id="985f4-106">集計変換では、次の操作がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="985f4-106">The Aggregate transformation supports the following operations.</span></span>  
  
|<span data-ttu-id="985f4-107">操作</span><span class="sxs-lookup"><span data-stu-id="985f4-107">Operation</span></span>|<span data-ttu-id="985f4-108">説明</span><span class="sxs-lookup"><span data-stu-id="985f4-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="985f4-109">グループ化</span><span class="sxs-lookup"><span data-stu-id="985f4-109">Group by</span></span>|<span data-ttu-id="985f4-110">データセットをグループに分割します。</span><span class="sxs-lookup"><span data-stu-id="985f4-110">Divides datasets into groups.</span></span> <span data-ttu-id="985f4-111">グループ化には、任意のデータ型の列を使用できます。</span><span class="sxs-lookup"><span data-stu-id="985f4-111">Columns of any data type can be used for grouping.</span></span> <span data-ttu-id="985f4-112">詳細については、「[GROUP BY (Transact-SQL)](/sql/t-sql/queries/select-group-by-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="985f4-112">For more information, see [GROUP BY &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-group-by-transact-sql).</span></span>|  
|<span data-ttu-id="985f4-113">SUM</span><span class="sxs-lookup"><span data-stu-id="985f4-113">Sum</span></span>|<span data-ttu-id="985f4-114">列内の値を合計します。</span><span class="sxs-lookup"><span data-stu-id="985f4-114">Sums the values in a column.</span></span> <span data-ttu-id="985f4-115">numeric データ型を持つ列のみ、合計することができます。</span><span class="sxs-lookup"><span data-stu-id="985f4-115">Only columns with numeric data types can be summed.</span></span> <span data-ttu-id="985f4-116">詳細については、「[SUM (Transact-SQL)](/sql/t-sql/functions/sum-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="985f4-116">For more information, see [SUM &#40;Transact-SQL&#41;](/sql/t-sql/functions/sum-transact-sql).</span></span>|  
|<span data-ttu-id="985f4-117">Average</span><span class="sxs-lookup"><span data-stu-id="985f4-117">Average</span></span>|<span data-ttu-id="985f4-118">列内の列値の平均を返します。</span><span class="sxs-lookup"><span data-stu-id="985f4-118">Returns the average of the column values in a column.</span></span> <span data-ttu-id="985f4-119">numeric データ型を持つ列のみ、平均値を計算することができます。</span><span class="sxs-lookup"><span data-stu-id="985f4-119">Only columns with numeric data types can be averaged.</span></span> <span data-ttu-id="985f4-120">詳細については、「[AVG (Transact-SQL)](/sql/t-sql/functions/avg-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="985f4-120">For more information, see [AVG &#40;Transact-SQL&#41;](/sql/t-sql/functions/avg-transact-sql).</span></span>|  
|<span data-ttu-id="985f4-121">Count</span><span class="sxs-lookup"><span data-stu-id="985f4-121">Count</span></span>|<span data-ttu-id="985f4-122">グループ内のアイテムの数を返します。</span><span class="sxs-lookup"><span data-stu-id="985f4-122">Returns the number of items in a group.</span></span> <span data-ttu-id="985f4-123">詳細については、「[COUNT (Transact-SQL)](/sql/t-sql/functions/count-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="985f4-123">For more information, see [COUNT &#40;Transact-SQL&#41;](/sql/t-sql/functions/count-transact-sql).</span></span>|  
|<span data-ttu-id="985f4-124">個別のカウント</span><span class="sxs-lookup"><span data-stu-id="985f4-124">Count distinct</span></span>|<span data-ttu-id="985f4-125">グループ内の NULL でない一意の値の数を返します。</span><span class="sxs-lookup"><span data-stu-id="985f4-125">Returns the number of unique nonnull values in a group.</span></span>|  
|<span data-ttu-id="985f4-126">最小値</span><span class="sxs-lookup"><span data-stu-id="985f4-126">Minimum</span></span>|<span data-ttu-id="985f4-127">グループ内の最小値を返します。</span><span class="sxs-lookup"><span data-stu-id="985f4-127">Returns the minimum value in a group.</span></span> <span data-ttu-id="985f4-128">詳細については、「[MIN (Transact-SQL)](/sql/t-sql/functions/min-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="985f4-128">For more information, see [MIN &#40;Transact-SQL&#41;](/sql/t-sql/functions/min-transact-sql).</span></span> <span data-ttu-id="985f4-129">Transact-SQL MIN 関数とは異なり、この操作は数値、日付、および時間データ型に対してのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="985f4-129">In contrast to the Transact-SQL MIN function, this operation can be used only with numeric, date, and time data types.</span></span>|  
|<span data-ttu-id="985f4-130">最大値</span><span class="sxs-lookup"><span data-stu-id="985f4-130">Maximum</span></span>|<span data-ttu-id="985f4-131">グループ内の最大値を返します。</span><span class="sxs-lookup"><span data-stu-id="985f4-131">Returns the maximum value in a group.</span></span> <span data-ttu-id="985f4-132">詳細については、「[MAX (Transact-SQL)](/sql/t-sql/functions/max-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="985f4-132">For more information, see [MAX &#40;Transact-SQL&#41;](/sql/t-sql/functions/max-transact-sql).</span></span> <span data-ttu-id="985f4-133">Transact-SQL MAX 関数とは異なり、この操作は数値、日付、および時間データ型に対してのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="985f4-133">In contrast to the Transact-SQL MAX function, this operation can be used only with numeric, date, and time data types.</span></span>|  
  
 <span data-ttu-id="985f4-134">集計変換では、NULL 値を、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] リレーショナル データベース エンジンと同じ方法で処理します。</span><span class="sxs-lookup"><span data-stu-id="985f4-134">The Aggregate transformation handles null values in the same way as the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] relational database engine.</span></span> <span data-ttu-id="985f4-135">この動作は SQL-92 標準で定義されています。</span><span class="sxs-lookup"><span data-stu-id="985f4-135">The behavior is defined in the SQL-92 standard.</span></span> <span data-ttu-id="985f4-136">次の規則が適用されます。</span><span class="sxs-lookup"><span data-stu-id="985f4-136">The following rules apply:</span></span>  
  
-   <span data-ttu-id="985f4-137">GROUP BY 句では、他の列の値と同様に NULL が処理されます。</span><span class="sxs-lookup"><span data-stu-id="985f4-137">In a GROUP BY clause, nulls are treated like other column values.</span></span> <span data-ttu-id="985f4-138">グループ化に使われる列に複数の NULL 値が含まれる場合は、それらの NULL 値が 1 つのグループになります。</span><span class="sxs-lookup"><span data-stu-id="985f4-138">If the grouping column contains more than one null value, the null values are put into a single group.</span></span>  
  
-   <span data-ttu-id="985f4-139">COUNT (列名) および COUNT (DISTINCT 列名) 関数では、NULL は無視され、名前付き列内の NULL 値を含む行が結果から除外されます。</span><span class="sxs-lookup"><span data-stu-id="985f4-139">In the COUNT (column name) and COUNT (DISTINCT column name) functions, nulls are ignored and the result excludes rows that contain null values in the named column.</span></span>  
  
-   <span data-ttu-id="985f4-140">COUNT (\*) 関数では、NULL 値の行を含め、すべての行がカウントされます。</span><span class="sxs-lookup"><span data-stu-id="985f4-140">In the COUNT (\*) function, all rows are counted, including rows with null values.</span></span>  
  
## <a name="big-numbers-in-aggregates"></a><span data-ttu-id="985f4-141">集計における大きな数値</span><span class="sxs-lookup"><span data-stu-id="985f4-141">Big Numbers in Aggregates</span></span>  
 <span data-ttu-id="985f4-142">大きな数値または大きな有効桁数が必要な列がある場合は、特別な注意が必要です。</span><span class="sxs-lookup"><span data-stu-id="985f4-142">A column may contain numeric values that require special consideration because of their large value or precision requirements.</span></span> <span data-ttu-id="985f4-143">集計変換には、IsBig プロパティが含まれています。このプロパティを使用すると、出力列で、大きな数値または大きな有効桁数の数値に対し、特別な処理を実行するように設定できます。</span><span class="sxs-lookup"><span data-stu-id="985f4-143">The Aggregation transformation includes the IsBig property, which you can set on output columns to invoke special handling of big or high-precision numbers.</span></span> <span data-ttu-id="985f4-144">列の値が 40 億を超える場合、または float データ型よりも大きな有効桁数が必要な場合は、IsBig を 1 に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="985f4-144">If a column value may exceed 4 billion or a precision beyond a float data type is required, IsBig should be set to 1.</span></span>  
  
 <span data-ttu-id="985f4-145">IsBig プロパティを 1 に設定すると、集計変換の出力は、次のような影響を受けます。</span><span class="sxs-lookup"><span data-stu-id="985f4-145">Setting the IsBig property to 1 affects the output of the aggregation transformation in the following ways:</span></span>  
  
-   <span data-ttu-id="985f4-146">DT_R4 データ型の代わりに DT_R8 データ型が使用されます。</span><span class="sxs-lookup"><span data-stu-id="985f4-146">The DT_R8 data type is used instead of the DT_R4 data type.</span></span>  
  
-   <span data-ttu-id="985f4-147">カウントの結果は、DT_UI8 データ型として格納されます。</span><span class="sxs-lookup"><span data-stu-id="985f4-147">Count results are stored as the DT_UI8 data type.</span></span>  
  
-   <span data-ttu-id="985f4-148">個別のカウントの結果は、DT_UI4 データ型として格納されます。</span><span class="sxs-lookup"><span data-stu-id="985f4-148">Distinct count results are stored as the DT_UI4 data type.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="985f4-149">グループ化、最大、または最小操作で使用される列では、IsBig を 1 に設定することはできません。</span><span class="sxs-lookup"><span data-stu-id="985f4-149">You cannot set IsBig to 1 on columns that are used in the GROUP BY, Maximum, or Minimum operations.</span></span>  
  
## <a name="performance-considerations"></a><span data-ttu-id="985f4-150">パフォーマンスに関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="985f4-150">Performance Considerations</span></span>  
 <span data-ttu-id="985f4-151">集計変換には、変換のパフォーマンスが向上するように設定できる、プロパティのセットが含まれています。</span><span class="sxs-lookup"><span data-stu-id="985f4-151">The Aggregate transformation includes a set of properties that you can set to enhance the performance of the transformation.</span></span>  
  
-   <span data-ttu-id="985f4-152">**グループ化** 操作を実行する場合は、コンポーネントとコンポーネント出力の Keys プロパティまたは KeysScale プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="985f4-152">When performing a **Group by** operation, set the Keys or KeysScale properties of the component and the component outputs.</span></span> <span data-ttu-id="985f4-153">Keys を使用すると、変換で処理されるキーの正確な数を指定できます</span><span class="sxs-lookup"><span data-stu-id="985f4-153">Using Keys, you can specify the exact number of keys the transformation is expected to handle.</span></span> <span data-ttu-id="985f4-154">(ここでは、Keys は、 **グループ化** 操作の結果として予想されるグループの数を示します)。KeysScale を使用すると、キーの概数を指定できます。</span><span class="sxs-lookup"><span data-stu-id="985f4-154">(In this context, Keys refers to the number of groups that are expected to result from a **Group by** operation.) Using KeysScale, you can specify an approximate number of keys.</span></span> <span data-ttu-id="985f4-155">Keys または KeysScale に適切な値を指定すると、変換時にキャッシュされるデータ用に十分なメモリが割り当てられるようになるため、パフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="985f4-155">When you specify an appropriate value for Keys or KeyScale, you improve performance because the tranformation is able to allocate adequate memory for the data that the transformation caches.</span></span>  
  
-   <span data-ttu-id="985f4-156">**個別のカウント** 操作を実行するときは、コンポーネントの CountDistinctKeys プロパティまたは CountDistinctScale プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="985f4-156">When performing a **Distinct count** operation, set the CountDistinctKeys or CountDistinctScale properties of the component.</span></span> <span data-ttu-id="985f4-157">CountDistinctKeys を使用すると、変換時に個別のカウント操作で処理されるキーの正確な数を指定できます</span><span class="sxs-lookup"><span data-stu-id="985f4-157">Using CountDistinctKeys, you can specify the exact number of keys the transformation is expected to handle for a count distinct operation.</span></span> <span data-ttu-id="985f4-158">(ここでは、CountDistinctKeys は、 **個別のカウント** 操作の結果として予想される個別の値の数を示します)。CountDistinctScale を使用すると、個別のカウントの操作で処理するキーの概数を指定できます。</span><span class="sxs-lookup"><span data-stu-id="985f4-158">(In this context, CountDistinctKeys refers to the number of distinct values that are expected to result from a **Distinct count** operation.) Using CountDistinctScale, you can specify an approximate number of keys for a count distinct operation.</span></span> <span data-ttu-id="985f4-159">CountDistinctKeys または CountDistinctScale に適切な値を指定すると、変換時にキャッシュされるデータ用に十分なメモリが割り当てられるようになるため、パフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="985f4-159">When you specify an appropriate value for CountDistinctKeys or CountDistinctScale, you improve performance because the transformation is able to allocate adequate memory for the data that the transformation caches.</span></span>  
  
## <a name="aggregate-transformation-configuration"></a><span data-ttu-id="985f4-160">集計変換の構成</span><span class="sxs-lookup"><span data-stu-id="985f4-160">Aggregate Transformation Configuration</span></span>  
 <span data-ttu-id="985f4-161">集計変換は、変換、出力、および列の各レベルで構成します。</span><span class="sxs-lookup"><span data-stu-id="985f4-161">You configure the Aggregate transformation at the transformation, output, and column levels.</span></span>  
  
-   <span data-ttu-id="985f4-162">変換レベルでは、次の値を指定することにより、集計変換を構成してパフォーマンスを高めることができます。</span><span class="sxs-lookup"><span data-stu-id="985f4-162">At the transformation level, you configure the Aggregate transformation for performance by specifying the following values:</span></span>  
  
    -   <span data-ttu-id="985f4-163">**グループ化** 操作の結果として予想されるグループの数。</span><span class="sxs-lookup"><span data-stu-id="985f4-163">The number of groups that are expected to result from a **Group by** operation.</span></span>  
  
    -   <span data-ttu-id="985f4-164">**個別のカウント** 操作の結果として予想される個別の値の数。</span><span class="sxs-lookup"><span data-stu-id="985f4-164">The number of distinct values that are expected to result from a **Count distinct** operation.</span></span>  
  
    -   <span data-ttu-id="985f4-165">集計の際にメモリを拡張できる割合。</span><span class="sxs-lookup"><span data-stu-id="985f4-165">The percentage by which memory can be extended during the aggregation.</span></span>  
  
     <span data-ttu-id="985f4-166">また、除数の値が 0 のときに失敗せずに警告を生成するように、集計変換を構成することもできます。</span><span class="sxs-lookup"><span data-stu-id="985f4-166">The Aggregate transformation can also be configured to generate a warning instead of failing when the value of a divisor is zero.</span></span>  
  
-   <span data-ttu-id="985f4-167">出力レベルでは、 **グループ化** 操作の結果として予想されるグループの数を指定することにより、集計変換を構成してパフォーマンスを高めることができます。</span><span class="sxs-lookup"><span data-stu-id="985f4-167">At the output level, you configure the Aggregate transformation for performance by specifying the number of groups that are expected to result from a **Group by** operation.</span></span> <span data-ttu-id="985f4-168">集計変換では複数の出力を設定して、各列を個別に構成できます。</span><span class="sxs-lookup"><span data-stu-id="985f4-168">The Aggregate transformation supports multiple outputs, and each can be configured differently.</span></span>  
  
-   <span data-ttu-id="985f4-169">列レベルでは、次の値を指定します。</span><span class="sxs-lookup"><span data-stu-id="985f4-169">At the column level, you specify the following values:</span></span>  
  
    -   <span data-ttu-id="985f4-170">列が実行する集計。</span><span class="sxs-lookup"><span data-stu-id="985f4-170">The aggregation that the column performs.</span></span>  
  
    -   <span data-ttu-id="985f4-171">集計の比較オプション。</span><span class="sxs-lookup"><span data-stu-id="985f4-171">The comparison options of the aggregation.</span></span>  
  
 <span data-ttu-id="985f4-172">また、次の値を指定することにより、集計変換を構成してパフォーマンスを高めることもできます。</span><span class="sxs-lookup"><span data-stu-id="985f4-172">You can also configure the Aggregate transformation for performance by specifying these values:</span></span>  
  
-   <span data-ttu-id="985f4-173">列に対する **グループ化** 操作の結果として予想されるグループの数。</span><span class="sxs-lookup"><span data-stu-id="985f4-173">The number of groups that are expected to result from a **Group by** operation on the column.</span></span>  
  
-   <span data-ttu-id="985f4-174">列に対する **個別のカウント** 操作の結果として予想される個別の値の数。</span><span class="sxs-lookup"><span data-stu-id="985f4-174">The number of distinct values that are expected to result from a **Count distinct** operation on the column.</span></span>  
  
 <span data-ttu-id="985f4-175">列に含まれる数値が大きい場合、または数値の有効桁数が大きい場合には、その列を IsBig として識別することもできます。</span><span class="sxs-lookup"><span data-stu-id="985f4-175">You can also identify columns as IsBig if a column contains large numeric values or numeric values with high precision.</span></span>  
  
 <span data-ttu-id="985f4-176">集計変換は非同期です。つまり、行ごとにデータを使用またはパブリッシュしません。</span><span class="sxs-lookup"><span data-stu-id="985f4-176">The Aggregate transformation is asynchronous, which means that it does not consume and publish data row by row.</span></span> <span data-ttu-id="985f4-177">集計変換は行セット全体を使用してグループ化と集計を実行し、その結果をパブリッシュします。</span><span class="sxs-lookup"><span data-stu-id="985f4-177">Instead it consumes the whole rowset, performs its groupings and aggregations, and then publishes the results.</span></span>  
  
 <span data-ttu-id="985f4-178">この変換では列をパススルーすることはなく、変換によりパブリッシュされるデータ用に、新しい列がデータ フロー内に作成されます。</span><span class="sxs-lookup"><span data-stu-id="985f4-178">This transformation does not pass through any columns, but creates new columns in the data flow for the data it publishes.</span></span> <span data-ttu-id="985f4-179">集計関数が適用される入力列、または変換がグループ化用に使用する入力列のみが、変換出力にコピーされます。</span><span class="sxs-lookup"><span data-stu-id="985f4-179">Only the input columns to which aggregate functions apply or the input columns the transformation uses for grouping are copied to the transformation output.</span></span> <span data-ttu-id="985f4-180">たとえば、集計変換入力に、 **CountryRegion**、 **City**、および **Population**という 3 つの列があるものとします。</span><span class="sxs-lookup"><span data-stu-id="985f4-180">For example, an Aggregate transformation input might have three columns: **CountryRegion**, **City**, and **Population**.</span></span> <span data-ttu-id="985f4-181">集計変換は、 **CountryRegion** 列によりグループ化を行い、 関数を **Population** 列に適用します。</span><span class="sxs-lookup"><span data-stu-id="985f4-181">The transformation groups by the **CountryRegion** column and applies the Sum function to the **Population** column.</span></span> <span data-ttu-id="985f4-182">したがって、出力には **City** 列は含まれません。</span><span class="sxs-lookup"><span data-stu-id="985f4-182">Therefore the output does not include the **City** column.</span></span>  
  
 <span data-ttu-id="985f4-183">また、複数の出力を集計変換に追加し、各集計を別々の出力に送ることもできます。</span><span class="sxs-lookup"><span data-stu-id="985f4-183">You can also add multiple outputs to the Aggregate transformation and direct each aggregation to a different output.</span></span> <span data-ttu-id="985f4-184">たとえば、集計変換が Sum および Average 関数を適用する場合に、各集計をそれぞれ別の出力に送ることができます。</span><span class="sxs-lookup"><span data-stu-id="985f4-184">For example, if the Aggregate transformation applies the Sum and the Average functions, each aggregation can be directed to a different output.</span></span>  
  
 <span data-ttu-id="985f4-185">1 つの入力列に複数の集計を適用できます。</span><span class="sxs-lookup"><span data-stu-id="985f4-185">You can apply multiple aggregations to a single input column.</span></span> <span data-ttu-id="985f4-186">たとえば、 **Sales**という名前の入力列の合計値と平均値を計算する場合に、Sum および Average 関数の両方を **Sales** 列に適用するように、集計変換を構成できます。</span><span class="sxs-lookup"><span data-stu-id="985f4-186">For example, if you want the sum and average values for an input column named **Sales**, you can configure the transformation to apply both the Sum and Average functions to the **Sales** column.</span></span>  
  
 <span data-ttu-id="985f4-187">集計変換は、1 つの入力と 1 つ以上の出力をとります。</span><span class="sxs-lookup"><span data-stu-id="985f4-187">The Aggregate transformation has one input and one or more outputs.</span></span> <span data-ttu-id="985f4-188">エラー出力はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="985f4-188">It does not support an error output.</span></span>  
  
 <span data-ttu-id="985f4-189">プロパティを設定するには [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。</span><span class="sxs-lookup"><span data-stu-id="985f4-189">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="985f4-190">**[集計変換エディター]** ダイアログ ボックスで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="985f4-190">For more information about the properties that you can set in the **Aggregate Transformation Editor** dialog box, click one of the following topics:</span></span>  
  
-   <span data-ttu-id="985f4-191">[[集計変換エディター] ([集計] タブ)](../../aggregate-transformation-editor-aggregations-tab.md)</span><span class="sxs-lookup"><span data-stu-id="985f4-191">[Aggregate Transformation Editor &#40;Aggregations Tab&#41;](../../aggregate-transformation-editor-aggregations-tab.md)</span></span>  
  
-   <span data-ttu-id="985f4-192">[[集計変換エディター] &#40;[詳細設定] タブ&#41;](../../aggregate-transformation-editor-advanced-tab.md)</span><span class="sxs-lookup"><span data-stu-id="985f4-192">[Aggregate Transformation Editor &#40;Advanced Tab&#41;](../../aggregate-transformation-editor-advanced-tab.md)</span></span>  
  
 <span data-ttu-id="985f4-193">**[詳細エディター]** ダイアログ ボックスには、プログラムによって設定できるプロパティが反映されます。</span><span class="sxs-lookup"><span data-stu-id="985f4-193">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="985f4-194">**[詳細エディター]** ダイアログ ボックスまたはプログラムで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="985f4-194">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="985f4-195">Common Properties</span><span class="sxs-lookup"><span data-stu-id="985f4-195">Common Properties</span></span>](../../common-properties.md)  
  
-   [<span data-ttu-id="985f4-196">変換のカスタム プロパティ</span><span class="sxs-lookup"><span data-stu-id="985f4-196">Transformation Custom Properties</span></span>](transformation-custom-properties.md)  
  
 <span data-ttu-id="985f4-197">プロパティの設定方法の詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="985f4-197">For more information about how to set properties, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="985f4-198">集計変換を使用してデータセットの値を集計する</span><span class="sxs-lookup"><span data-stu-id="985f4-198">Aggregate Values in a Dataset by Using the Aggregate Transformation</span></span>](aggregate-values-in-a-dataset-by-using-the-aggregate-transformation.md)  
  
-   [<span data-ttu-id="985f4-199">データ フロー コンポーネントのプロパティを設定する</span><span class="sxs-lookup"><span data-stu-id="985f4-199">Set the Properties of a Data Flow Component</span></span>](../set-the-properties-of-a-data-flow-component.md)  
  
-   [<span data-ttu-id="985f4-200">マージ変換およびマージ結合変換用にデータを並べ替える</span><span class="sxs-lookup"><span data-stu-id="985f4-200">Sort Data for the Merge and Merge Join Transformations</span></span>](sort-data-for-the-merge-and-merge-join-transformations.md)  
  
## <a name="related-tasks"></a><span data-ttu-id="985f4-201">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="985f4-201">Related Tasks</span></span>  
 [<span data-ttu-id="985f4-202">集計変換を使用してデータセットの値を集計する</span><span class="sxs-lookup"><span data-stu-id="985f4-202">Aggregate Values in a Dataset by Using the Aggregate Transformation</span></span>](aggregate-values-in-a-dataset-by-using-the-aggregate-transformation.md)  
  
## <a name="see-also"></a><span data-ttu-id="985f4-203">参照</span><span class="sxs-lookup"><span data-stu-id="985f4-203">See Also</span></span>  
 <span data-ttu-id="985f4-204">[データ フロー](../data-flow.md) </span><span class="sxs-lookup"><span data-stu-id="985f4-204">[Data Flow](../data-flow.md) </span></span>  
 [<span data-ttu-id="985f4-205">Integration Services の変換</span><span class="sxs-lookup"><span data-stu-id="985f4-205">Integration Services Transformations</span></span>](integration-services-transformations.md)  
  
  
