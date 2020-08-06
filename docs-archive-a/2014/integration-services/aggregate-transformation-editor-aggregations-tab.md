---
title: '[集計変換エディター] ([集計] タブ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.aggregationtransformation.aggregations.f1
helpviewer_keywords:
- Aggregate Transformation Editor
ms.assetid: a01cb124-ec79-4673-b1a1-bf4d60ee1b45
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 30cafb68a69a061fe4b79e832f356b82926c9761
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633985"
---
# <a name="aggregate-transformation-editor-aggregations-tab"></a><span data-ttu-id="ef25d-102">[集計変換エディター] ([集計] タブ)</span><span class="sxs-lookup"><span data-stu-id="ef25d-102">Aggregate Transformation Editor (Aggregations Tab)</span></span>
  <span data-ttu-id="ef25d-103">**[集計変換エディター]** ダイアログ ボックスの **[集計]** タブを使用すると、集計列および集計プロパティを指定できます。</span><span class="sxs-lookup"><span data-stu-id="ef25d-103">Use the **Aggregations** tab of the **Aggregate Transformation Editor** dialog box to specify columns for aggregation and aggregation properties.</span></span> <span data-ttu-id="ef25d-104">複数の集計を適用することができます。</span><span class="sxs-lookup"><span data-stu-id="ef25d-104">You can apply multiple aggregations.</span></span> <span data-ttu-id="ef25d-105">この変換ではエラー出力を生成しません。</span><span class="sxs-lookup"><span data-stu-id="ef25d-105">This transformation does not generate an error output.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ef25d-106">キーの数、キー スケール、個別のキーの数、個別のキー スケールのオプションは、 **[詳細設定]** タブで指定した場合はコンポーネント レベル、 **[集計]** タブの [詳細設定] 画面で指定した場合は出力レベル、 **[集計]** タブの下部にある列の一覧で指定した場合は列レベルで適用されます。</span><span class="sxs-lookup"><span data-stu-id="ef25d-106">The options for key count, key scale, distinct key count, and distinct key scale apply at the component level when specified on the **Advanced** tab, at the output level when specified in the advanced display of the **Aggregations** tab, and at the column level when specified in the column list at the bottom of the **Aggregations** tab.</span></span>  
>   
>  <span data-ttu-id="ef25d-107">集計変換では、 **[キー]** および **[キー スケール]** は、 **グループ化** 操作の結果として予想されるグループの数を示します。</span><span class="sxs-lookup"><span data-stu-id="ef25d-107">In the Aggregate transformation, **Keys** and **Keys scale** refer to the number of groups that are expected to result from a **Group by** operation.</span></span> <span data-ttu-id="ef25d-108">**[個別カウント キー数]** および **[個別カウント スケール]** は、 **個別のカウント** 操作の結果として予想される個別の値の数を示します。</span><span class="sxs-lookup"><span data-stu-id="ef25d-108">**Count distinct keys** and **Count distinct scale** refer to the number of distinct values that are expected to result from a **Distinct count** operation.</span></span>  
  
 <span data-ttu-id="ef25d-109">集計変換の詳細については、「 [集計変換](data-flow/transformations/aggregate-transformation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ef25d-109">To learn more about the Aggregate transformation, see [Aggregate Transformation](data-flow/transformations/aggregate-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="ef25d-110">Options</span><span class="sxs-lookup"><span data-stu-id="ef25d-110">Options</span></span>  
 <span data-ttu-id="ef25d-111">**[詳細設定]/[基本]**</span><span class="sxs-lookup"><span data-stu-id="ef25d-111">**Advanced / Basic**</span></span>  
 <span data-ttu-id="ef25d-112">複数の出力用に複数の集計を構成するオプションを表示したり非表示にしたりします。</span><span class="sxs-lookup"><span data-stu-id="ef25d-112">Display or hide options to configure multiple aggregations for multiple outputs.</span></span> <span data-ttu-id="ef25d-113">既定では、[詳細設定] オプションは非表示です。</span><span class="sxs-lookup"><span data-stu-id="ef25d-113">By default, the Advanced options are hidden.</span></span>  
  
 <span data-ttu-id="ef25d-114">**[集計名]**</span><span class="sxs-lookup"><span data-stu-id="ef25d-114">**Aggregation Name**</span></span>  
 <span data-ttu-id="ef25d-115">[詳細設定] 画面で、集計の表示名を入力します。</span><span class="sxs-lookup"><span data-stu-id="ef25d-115">In the Advanced display, type a friendly name for the aggregation.</span></span>  
  
 <span data-ttu-id="ef25d-116">**[グループ化列]**</span><span class="sxs-lookup"><span data-stu-id="ef25d-116">**Group By Columns**</span></span>  
 <span data-ttu-id="ef25d-117">[詳細設定] 画面で、後で説明するように、 **[使用できる入力列]** リストを使用してグループ化する列を選択します。</span><span class="sxs-lookup"><span data-stu-id="ef25d-117">In the Advanced display, select columns for grouping by using the **Available Input Columns** list as described below.</span></span>  
  
 <span data-ttu-id="ef25d-118">**[キー スケール]**</span><span class="sxs-lookup"><span data-stu-id="ef25d-118">**Key Scale**</span></span>  
 <span data-ttu-id="ef25d-119">[詳細設定] 画面で、集計によって書き込むことのできるキーの概数をオプションで指定します。</span><span class="sxs-lookup"><span data-stu-id="ef25d-119">In the Advanced display, optionally specify the approximate number of keys that the aggregation can write.</span></span> <span data-ttu-id="ef25d-120">既定では、このオプションの値は **[未指定]** です。</span><span class="sxs-lookup"><span data-stu-id="ef25d-120">By default, the value of this option is **Unspecified**.</span></span> <span data-ttu-id="ef25d-121">**[キー スケール]** プロパティと **[キー]** プロパティの両方が設定されている場合、 **[キー]** の値が優先されます。</span><span class="sxs-lookup"><span data-stu-id="ef25d-121">If both the **Key Scale** and **Keys** properties are set, the value of **Keys** takes precedence.</span></span>  
  
|<span data-ttu-id="ef25d-122">値</span><span class="sxs-lookup"><span data-stu-id="ef25d-122">Value</span></span>|<span data-ttu-id="ef25d-123">説明</span><span class="sxs-lookup"><span data-stu-id="ef25d-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ef25d-124">指定されていません。</span><span class="sxs-lookup"><span data-stu-id="ef25d-124">Unspecified</span></span>|<span data-ttu-id="ef25d-125">[キー スケール] プロパティは使用されません。</span><span class="sxs-lookup"><span data-stu-id="ef25d-125">The Key Scale property is not used.</span></span>|  
|<span data-ttu-id="ef25d-126">低</span><span class="sxs-lookup"><span data-stu-id="ef25d-126">Low</span></span>|<span data-ttu-id="ef25d-127">集計では約 500,000 キーを書き込むことができます。</span><span class="sxs-lookup"><span data-stu-id="ef25d-127">Aggregation can write approximately 500,000 keys.</span></span>|  
|<span data-ttu-id="ef25d-128">Medium</span><span class="sxs-lookup"><span data-stu-id="ef25d-128">Medium</span></span>|<span data-ttu-id="ef25d-129">集計では約 5,000,000 キーを書き込むことができます。</span><span class="sxs-lookup"><span data-stu-id="ef25d-129">Aggregation can write approximately 5,000,000 keys.</span></span>|  
|<span data-ttu-id="ef25d-130">高</span><span class="sxs-lookup"><span data-stu-id="ef25d-130">High</span></span>|<span data-ttu-id="ef25d-131">集計では 25,000,000 を超えるキーを書き込むことができます。</span><span class="sxs-lookup"><span data-stu-id="ef25d-131">Aggregation can write more than 25,000,000 keys.</span></span>|  
  
 <span data-ttu-id="ef25d-132">**[キー]**</span><span class="sxs-lookup"><span data-stu-id="ef25d-132">**Keys**</span></span>  
 <span data-ttu-id="ef25d-133">[詳細設定] 画面で、集計によって書き込むことのできる正確なキーの数をオプションで指定します。</span><span class="sxs-lookup"><span data-stu-id="ef25d-133">In the Advanced display, optionally specify the exact number of keys that the aggregation can write.</span></span> <span data-ttu-id="ef25d-134">**[キー スケール]** と **[キー]** の両方が指定されている場合、 **[キー]** が優先されます。</span><span class="sxs-lookup"><span data-stu-id="ef25d-134">If both **Key Scale** and **Keys** are specified, **Keys** takes precedence.</span></span>  
  
 <span data-ttu-id="ef25d-135">**使用できる入力列**</span><span class="sxs-lookup"><span data-stu-id="ef25d-135">**Available Input Columns**</span></span>  
 <span data-ttu-id="ef25d-136">このテーブルのチェック ボックスを使用して、使用できる入力列の一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="ef25d-136">Select from the list of available input columns by using the check boxes in this table.</span></span>  
  
 <span data-ttu-id="ef25d-137">**入力列**</span><span class="sxs-lookup"><span data-stu-id="ef25d-137">**Input Column**</span></span>  
 <span data-ttu-id="ef25d-138">使用できる入力列の一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="ef25d-138">Select from the list of available input columns.</span></span>  
  
 <span data-ttu-id="ef25d-139">**[出力の別名]**</span><span class="sxs-lookup"><span data-stu-id="ef25d-139">**Output Alias**</span></span>  
 <span data-ttu-id="ef25d-140">各列に対して別名を入力します。</span><span class="sxs-lookup"><span data-stu-id="ef25d-140">Type an alias for each column.</span></span> <span data-ttu-id="ef25d-141">既定は入力列の名前です。一意のわかりやすい名前を付けることもできます。</span><span class="sxs-lookup"><span data-stu-id="ef25d-141">The default is the name of the input column; however, you can choose any unique, descriptive name.</span></span>  
  
 <span data-ttu-id="ef25d-142">**操作**</span><span class="sxs-lookup"><span data-stu-id="ef25d-142">**Operation**</span></span>  
 <span data-ttu-id="ef25d-143">使用可能な操作の一覧から選択します。次の表を指針として使用できます。</span><span class="sxs-lookup"><span data-stu-id="ef25d-143">Choose from the list of available operations, using the following table as a guide.</span></span>  
  
|<span data-ttu-id="ef25d-144">操作</span><span class="sxs-lookup"><span data-stu-id="ef25d-144">Operation</span></span>|<span data-ttu-id="ef25d-145">説明</span><span class="sxs-lookup"><span data-stu-id="ef25d-145">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ef25d-146">**GroupBy**</span><span class="sxs-lookup"><span data-stu-id="ef25d-146">**GroupBy**</span></span>|<span data-ttu-id="ef25d-147">データセットをグループに分割します。</span><span class="sxs-lookup"><span data-stu-id="ef25d-147">Divides datasets into groups.</span></span> <span data-ttu-id="ef25d-148">どのようなデータ型を持つ列でもグループ化に使用できます。</span><span class="sxs-lookup"><span data-stu-id="ef25d-148">Columns with any data type can be used for grouping.</span></span> <span data-ttu-id="ef25d-149">詳細については、「GROUP BY」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ef25d-149">For more information, see GROUP BY.</span></span>|  
|<span data-ttu-id="ef25d-150">**SUM**</span><span class="sxs-lookup"><span data-stu-id="ef25d-150">**Sum**</span></span>|<span data-ttu-id="ef25d-151">列内の値を合計します。</span><span class="sxs-lookup"><span data-stu-id="ef25d-151">Sums the values in a column.</span></span> <span data-ttu-id="ef25d-152">numeric データ型を持つ列のみ、合計することができます。</span><span class="sxs-lookup"><span data-stu-id="ef25d-152">Only columns with numeric data types can be summed.</span></span> <span data-ttu-id="ef25d-153">詳細については、「SUM」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ef25d-153">For more information, see SUM.</span></span>|  
|<span data-ttu-id="ef25d-154">**Average**</span><span class="sxs-lookup"><span data-stu-id="ef25d-154">**Average**</span></span>|<span data-ttu-id="ef25d-155">列内の列値の平均を返します。</span><span class="sxs-lookup"><span data-stu-id="ef25d-155">Returns the average of the column values in a column.</span></span> <span data-ttu-id="ef25d-156">numeric データ型を持つ列のみ、平均値を計算することができます。</span><span class="sxs-lookup"><span data-stu-id="ef25d-156">Only columns with numeric data types can be averaged.</span></span> <span data-ttu-id="ef25d-157">詳細については、「AVG」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ef25d-157">For more information, see AVG.</span></span>|  
|<span data-ttu-id="ef25d-158">**Count**</span><span class="sxs-lookup"><span data-stu-id="ef25d-158">**Count**</span></span>|<span data-ttu-id="ef25d-159">グループ内のアイテムの数を返します。</span><span class="sxs-lookup"><span data-stu-id="ef25d-159">Returns the number of items in a group.</span></span> <span data-ttu-id="ef25d-160">詳細については、「COUNT」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ef25d-160">For more information, see COUNT.</span></span>|  
|<span data-ttu-id="ef25d-161">**CountDistinct**</span><span class="sxs-lookup"><span data-stu-id="ef25d-161">**CountDistinct**</span></span>|<span data-ttu-id="ef25d-162">グループ内の NULL でない一意の値の数を返します。</span><span class="sxs-lookup"><span data-stu-id="ef25d-162">Returns the number of unique nonnull values in a group.</span></span> <span data-ttu-id="ef25d-163">詳細については、「COUNT」および「DISTINCT」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ef25d-163">For more information, see COUNT and Distinct.</span></span>|  
|<span data-ttu-id="ef25d-164">**最小**</span><span class="sxs-lookup"><span data-stu-id="ef25d-164">**Minimum**</span></span>|<span data-ttu-id="ef25d-165">グループ内の最小値を返します。</span><span class="sxs-lookup"><span data-stu-id="ef25d-165">Returns the minimum value in a group.</span></span> <span data-ttu-id="ef25d-166">numeric データ型に制限されます。</span><span class="sxs-lookup"><span data-stu-id="ef25d-166">Restricted to numeric data types.</span></span>|  
|<span data-ttu-id="ef25d-167">**[最大]**</span><span class="sxs-lookup"><span data-stu-id="ef25d-167">**Maximum**</span></span>|<span data-ttu-id="ef25d-168">グループ内の最大値を返します。</span><span class="sxs-lookup"><span data-stu-id="ef25d-168">Returns the maximum value in a group.</span></span> <span data-ttu-id="ef25d-169">numeric データ型に制限されます。</span><span class="sxs-lookup"><span data-stu-id="ef25d-169">Restricted to numeric data types.</span></span>|  
  
 <span data-ttu-id="ef25d-170">**[比較フラグ]**</span><span class="sxs-lookup"><span data-stu-id="ef25d-170">**Comparison Flags**</span></span>  
 <span data-ttu-id="ef25d-171">**[グループ化]** を選択する場合、チェック ボックスを使用して、変換により比較がどのように実行されるかを制御します。</span><span class="sxs-lookup"><span data-stu-id="ef25d-171">If you choose **Group By**, use the check boxes to control how the transformation performs the comparison.</span></span> <span data-ttu-id="ef25d-172">文字列比較オプションについては、「 [文字列データの比較](data-flow/comparing-string-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ef25d-172">For information on the string comparison options, see [Comparing String Data](data-flow/comparing-string-data.md).</span></span>  
  
 <span data-ttu-id="ef25d-173">**個別カウントスケール**</span><span class="sxs-lookup"><span data-stu-id="ef25d-173">**Count Distinct Scale**</span></span>  
 <span data-ttu-id="ef25d-174">集計で書き込むことのできる個別の値の概数をオプションで指定します。</span><span class="sxs-lookup"><span data-stu-id="ef25d-174">Optionally specify the approximate number of distinct values that the aggregation can write.</span></span> <span data-ttu-id="ef25d-175">既定では、このオプションの値は **[未指定]** です。</span><span class="sxs-lookup"><span data-stu-id="ef25d-175">By default, the value of this option is **Unspecified**.</span></span> <span data-ttu-id="ef25d-176">`CountDistinctScale`と**CountDistinctKeys**の両方が指定されている場合、 **CountDistinctKeys**が優先されます。</span><span class="sxs-lookup"><span data-stu-id="ef25d-176">If both `CountDistinctScale` and **CountDistinctKeys** are specified, **CountDistinctKeys** takes precedence.</span></span>  
  
|<span data-ttu-id="ef25d-177">値</span><span class="sxs-lookup"><span data-stu-id="ef25d-177">Value</span></span>|<span data-ttu-id="ef25d-178">説明</span><span class="sxs-lookup"><span data-stu-id="ef25d-178">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ef25d-179">指定されていません。</span><span class="sxs-lookup"><span data-stu-id="ef25d-179">Unspecified</span></span>|<span data-ttu-id="ef25d-180">`CountDistinctScale` プロパティは使用されません。</span><span class="sxs-lookup"><span data-stu-id="ef25d-180">The `CountDistinctScale` property is not used.</span></span>|  
|<span data-ttu-id="ef25d-181">低</span><span class="sxs-lookup"><span data-stu-id="ef25d-181">Low</span></span>|<span data-ttu-id="ef25d-182">集計では約 500,000 の個別の値を書き込むことができます。</span><span class="sxs-lookup"><span data-stu-id="ef25d-182">Aggregation can write approximately 500,000 distinct values.</span></span>|  
|<span data-ttu-id="ef25d-183">Medium</span><span class="sxs-lookup"><span data-stu-id="ef25d-183">Medium</span></span>|<span data-ttu-id="ef25d-184">集計では約 5,000,000 の個別の値を書き込むことができます。</span><span class="sxs-lookup"><span data-stu-id="ef25d-184">Aggregation can write approximately 5,000,000 distinct values.</span></span>|  
|<span data-ttu-id="ef25d-185">高</span><span class="sxs-lookup"><span data-stu-id="ef25d-185">High</span></span>|<span data-ttu-id="ef25d-186">集計では 25,000,000 を超える個別の値を書き込むことができます。</span><span class="sxs-lookup"><span data-stu-id="ef25d-186">Aggregation can write more than 25,000,000 distinct values.</span></span>|  
  
 <span data-ttu-id="ef25d-187">**個別カウントキー数**</span><span class="sxs-lookup"><span data-stu-id="ef25d-187">**Count Distinct Keys**</span></span>  
 <span data-ttu-id="ef25d-188">集計によって書き込むことのできる個別の値の正確な数をオプションで指定します。</span><span class="sxs-lookup"><span data-stu-id="ef25d-188">Optionally specify the exact number of distinct values that the aggregation can write.</span></span> <span data-ttu-id="ef25d-189">`CountDistinctScale`と**CountDistinctKeys**の両方が指定されている場合、 **CountDistinctKeys**が優先されます。</span><span class="sxs-lookup"><span data-stu-id="ef25d-189">If both `CountDistinctScale` and **CountDistinctKeys** are specified, **CountDistinctKeys** takes precedence.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef25d-190">参照</span><span class="sxs-lookup"><span data-stu-id="ef25d-190">See Also</span></span>  
 <span data-ttu-id="ef25d-191">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="ef25d-191">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="ef25d-192">[[集計変換エディター] &#40;[詳細設定] タブ&#41;](../../2014/integration-services/aggregate-transformation-editor-advanced-tab.md) </span><span class="sxs-lookup"><span data-stu-id="ef25d-192">[Aggregate Transformation Editor &#40;Advanced Tab&#41;](../../2014/integration-services/aggregate-transformation-editor-advanced-tab.md) </span></span>  
 [<span data-ttu-id="ef25d-193">集計変換を使用してデータセットの値を集計する</span><span class="sxs-lookup"><span data-stu-id="ef25d-193">Aggregate Values in a Dataset by Using the Aggregate Transformation</span></span>](data-flow/transformations/aggregate-values-in-a-dataset-by-using-the-aggregate-transformation.md)  
  
  
