---
title: '[集計変換エディター] ([詳細設定] タブ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.aggregationtransformation.advanced.f1
helpviewer_keywords:
- Aggregate Transformation Editor
ms.assetid: 186a9736-2554-40a0-9cb2-877a8db5fde8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: cb3742a83f363f74004a5aac0eefc589ee2a5be2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633988"
---
# <a name="aggregate-transformation-editor-advanced-tab"></a><span data-ttu-id="cf4fb-102">[集計変換エディター] ([詳細設定] タブ)</span><span class="sxs-lookup"><span data-stu-id="cf4fb-102">Aggregate Transformation Editor (Advanced Tab)</span></span>
  <span data-ttu-id="cf4fb-103">**[集計変換エディター]** ダイアログ ボックスの **[詳細設定]** タブを使用すると、コンポーネントのプロパティの設定、集計の指定、入力列と出力列のプロパティの設定を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="cf4fb-103">Use the **Advanced** tab of the **Aggregate Transformation Editor** dialog box to set component properties, specify aggregations, and set properties of input and output columns.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cf4fb-104">キーの数、キー スケール、個別のキーの数、個別のキー スケールのオプションは、 **[詳細設定]** タブで指定した場合はコンポーネント レベル、 **[集計]** タブの [詳細設定] 画面で指定した場合は出力レベル、 **[集計]** タブの下部にある列の一覧で指定した場合は列レベルで適用されます。</span><span class="sxs-lookup"><span data-stu-id="cf4fb-104">The options for key count, key scale, distinct key count, and distinct key scale apply at the component level when specified on the **Advanced** tab, at the output level when specified in the advanced display of the **Aggregations** tab, and at the column level when specified in the column list at the bottom of the **Aggregations** tab.</span></span>  
>   
>  <span data-ttu-id="cf4fb-105">集計変換では、 **[キー]** および **[キー スケール]** は、 **グループ化** 操作の結果として予想されるグループの数を示します。</span><span class="sxs-lookup"><span data-stu-id="cf4fb-105">In the Aggregate transformation, **Keys** and **Keys scale** refer to the number of groups that are expected to result from a **Group by** operation.</span></span> <span data-ttu-id="cf4fb-106">**[個別カウント キー数]** および **[個別カウント スケール]** は、 **個別のカウント** 操作の結果として予想される個別の値の数を示します。</span><span class="sxs-lookup"><span data-stu-id="cf4fb-106">**Count distinct keys** and **Count distinct scale** refer to the number of distinct values that are expected to result from a **Distinct count** operation.</span></span>  
  
 <span data-ttu-id="cf4fb-107">集計変換の詳細については、「 [集計変換](data-flow/transformations/aggregate-transformation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cf4fb-107">To learn more about the Aggregate transformation, see [Aggregate Transformation](data-flow/transformations/aggregate-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="cf4fb-108">Options</span><span class="sxs-lookup"><span data-stu-id="cf4fb-108">Options</span></span>  
 <span data-ttu-id="cf4fb-109">**[キー スケール]**</span><span class="sxs-lookup"><span data-stu-id="cf4fb-109">**Keys scale**</span></span>  
 <span data-ttu-id="cf4fb-110">集計で予想される、概算のキー数をオプションで指定します。</span><span class="sxs-lookup"><span data-stu-id="cf4fb-110">Optionally specify the approximate number of keys that the aggregation expects.</span></span> <span data-ttu-id="cf4fb-111">変換ではこの情報を使用して最初のキャッシュ サイズを最適化します。</span><span class="sxs-lookup"><span data-stu-id="cf4fb-111">The transformation uses this information to optimize its initial cache size.</span></span> <span data-ttu-id="cf4fb-112">既定では、このオプションの値は **[未指定]** です。</span><span class="sxs-lookup"><span data-stu-id="cf4fb-112">By default, the value of this option is **Unspecified**.</span></span> <span data-ttu-id="cf4fb-113">**[キー スケール]** と **[キーの数]** の両方が指定されている場合、 **[キーの数]** の方が優先されます。</span><span class="sxs-lookup"><span data-stu-id="cf4fb-113">If both **Keys scale** and **Number of keys** are specified, **Number of keys** takes precedence.</span></span>  
  
|<span data-ttu-id="cf4fb-114">値</span><span class="sxs-lookup"><span data-stu-id="cf4fb-114">Value</span></span>|<span data-ttu-id="cf4fb-115">説明</span><span class="sxs-lookup"><span data-stu-id="cf4fb-115">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="cf4fb-116">指定されていません。</span><span class="sxs-lookup"><span data-stu-id="cf4fb-116">Unspecified</span></span>|<span data-ttu-id="cf4fb-117">**[キー スケール]** プロパティは使用されません。</span><span class="sxs-lookup"><span data-stu-id="cf4fb-117">The **Keys scale** property is not used.</span></span>|  
|<span data-ttu-id="cf4fb-118">低</span><span class="sxs-lookup"><span data-stu-id="cf4fb-118">Low</span></span>|<span data-ttu-id="cf4fb-119">集計では約 500,000 キーを書き込むことができます。</span><span class="sxs-lookup"><span data-stu-id="cf4fb-119">Aggregation can write approximately 500,000 keys.</span></span>|  
|<span data-ttu-id="cf4fb-120">Medium</span><span class="sxs-lookup"><span data-stu-id="cf4fb-120">Medium</span></span>|<span data-ttu-id="cf4fb-121">集計では約 5,000,000 キーを書き込むことができます。</span><span class="sxs-lookup"><span data-stu-id="cf4fb-121">Aggregation can write approximately 5,000,000 keys.</span></span>|  
|<span data-ttu-id="cf4fb-122">高</span><span class="sxs-lookup"><span data-stu-id="cf4fb-122">High</span></span>|<span data-ttu-id="cf4fb-123">集計では 25,000,000 を超えるキーを書き込むことができます。</span><span class="sxs-lookup"><span data-stu-id="cf4fb-123">Aggregation can write more than 25,000,000 keys.</span></span>|  
  
 <span data-ttu-id="cf4fb-124">**[キーの数]**</span><span class="sxs-lookup"><span data-stu-id="cf4fb-124">**Number of keys**</span></span>  
 <span data-ttu-id="cf4fb-125">集計で予想される、正確なキー数をオプションで指定します。</span><span class="sxs-lookup"><span data-stu-id="cf4fb-125">Optionally specify the exact number of keys that the aggregation expects.</span></span> <span data-ttu-id="cf4fb-126">変換ではこの情報を使用して最初のキャッシュ サイズを最適化します。</span><span class="sxs-lookup"><span data-stu-id="cf4fb-126">The transformation uses this information to optimize its initial cache size.</span></span> <span data-ttu-id="cf4fb-127">**[キー スケール]** と **[キーの数]** の両方が指定されている場合、 **[キーの数]** の方が優先されます。</span><span class="sxs-lookup"><span data-stu-id="cf4fb-127">If both **Keys scale** and **Number of keys** are specified, **Number of keys** takes precedence.</span></span>  
  
 <span data-ttu-id="cf4fb-128">**[個別カウント スケール]**</span><span class="sxs-lookup"><span data-stu-id="cf4fb-128">**Count distinct scale**</span></span>  
 <span data-ttu-id="cf4fb-129">集計で書き込むことのできる個別の値の概数をオプションで指定します。</span><span class="sxs-lookup"><span data-stu-id="cf4fb-129">Optionally specify the approximate number of distinct values that the aggregation can write.</span></span> <span data-ttu-id="cf4fb-130">既定では、このオプションの値は **[未指定]** です。</span><span class="sxs-lookup"><span data-stu-id="cf4fb-130">By default, the value of this option is **Unspecified**.</span></span> <span data-ttu-id="cf4fb-131">**[個別カウント スケール]** と **[個別カウント キー数]** の両方が指定されている場合、 **[個別カウント キー数]** の方が優先されます。</span><span class="sxs-lookup"><span data-stu-id="cf4fb-131">If both **Count distinct scale** and **Count distinct keys** are specified, **Count distinct keys** takes precedence.</span></span>  
  
|<span data-ttu-id="cf4fb-132">値</span><span class="sxs-lookup"><span data-stu-id="cf4fb-132">Value</span></span>|<span data-ttu-id="cf4fb-133">説明</span><span class="sxs-lookup"><span data-stu-id="cf4fb-133">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="cf4fb-134">指定されていません。</span><span class="sxs-lookup"><span data-stu-id="cf4fb-134">Unspecified</span></span>|<span data-ttu-id="cf4fb-135">CountDistinctScale プロパティは使用されません。</span><span class="sxs-lookup"><span data-stu-id="cf4fb-135">The CountDistinctScale property is not used.</span></span>|  
|<span data-ttu-id="cf4fb-136">低</span><span class="sxs-lookup"><span data-stu-id="cf4fb-136">Low</span></span>|<span data-ttu-id="cf4fb-137">集計では約 500,000 の個別の値を書き込むことができます。</span><span class="sxs-lookup"><span data-stu-id="cf4fb-137">Aggregation can write approximately 500,000 distinct values.</span></span>|  
|<span data-ttu-id="cf4fb-138">Medium</span><span class="sxs-lookup"><span data-stu-id="cf4fb-138">Medium</span></span>|<span data-ttu-id="cf4fb-139">集計では約 5,000,000 の個別の値を書き込むことができます。</span><span class="sxs-lookup"><span data-stu-id="cf4fb-139">Aggregation can write approximately 5,000,000 distinct values.</span></span>|  
|<span data-ttu-id="cf4fb-140">高</span><span class="sxs-lookup"><span data-stu-id="cf4fb-140">High</span></span>|<span data-ttu-id="cf4fb-141">集計では 25,000,000 を超える個別の値を書き込むことができます。</span><span class="sxs-lookup"><span data-stu-id="cf4fb-141">Aggregation can write more than 25,000,000 distinct values.</span></span>|  
  
 <span data-ttu-id="cf4fb-142">**[個別カウント キー数]**</span><span class="sxs-lookup"><span data-stu-id="cf4fb-142">**Count distinct keys**</span></span>  
 <span data-ttu-id="cf4fb-143">集計によって書き込むことのできる個別の値の正確な数をオプションで指定します。</span><span class="sxs-lookup"><span data-stu-id="cf4fb-143">Optionally specify the exact number of distinct values that the aggregation can write.</span></span> <span data-ttu-id="cf4fb-144">**[個別カウント スケール]** と **[個別カウント キー数]** の両方が指定されている場合、 **[個別カウント キー数]** の方が優先されます。</span><span class="sxs-lookup"><span data-stu-id="cf4fb-144">If both **Count distinct scale** and **Count distinct keys** are specified, **Count distinct keys** takes precedence.</span></span>  
  
 <span data-ttu-id="cf4fb-145">**[自動拡張率]**</span><span class="sxs-lookup"><span data-stu-id="cf4fb-145">**Auto extend factor**</span></span>  
 <span data-ttu-id="cf4fb-146">集計の際にメモリを拡張できる割合を 1 ～ 100% の範囲で指定します。</span><span class="sxs-lookup"><span data-stu-id="cf4fb-146">Use a value between 1 and 100 to specify the percentage by which memory can be extended during the aggregation.</span></span> <span data-ttu-id="cf4fb-147">既定では、このオプションの値は **25%** です。</span><span class="sxs-lookup"><span data-stu-id="cf4fb-147">By default, the value of this option is **25%**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf4fb-148">参照</span><span class="sxs-lookup"><span data-stu-id="cf4fb-148">See Also</span></span>  
 <span data-ttu-id="cf4fb-149">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="cf4fb-149">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="cf4fb-150">[集計変換エディター &#40;集計] タブ&#41;](../../2014/integration-services/aggregate-transformation-editor-aggregations-tab.md) </span><span class="sxs-lookup"><span data-stu-id="cf4fb-150">[Aggregate Transformation Editor &#40;Aggregations Tab&#41;](../../2014/integration-services/aggregate-transformation-editor-aggregations-tab.md) </span></span>  
 [<span data-ttu-id="cf4fb-151">集計変換を使用してデータセットの値を集計する</span><span class="sxs-lookup"><span data-stu-id="cf4fb-151">Aggregate Values in a Dataset by Using the Aggregate Transformation</span></span>](data-flow/transformations/aggregate-values-in-a-dataset-by-using-the-aggregate-transformation.md)  
  
  
