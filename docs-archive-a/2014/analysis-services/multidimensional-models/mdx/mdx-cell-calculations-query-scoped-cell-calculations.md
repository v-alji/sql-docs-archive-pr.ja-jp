---
title: クエリスコープのセル計算の作成 (MDX) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- WITH keyword
- query-scoped cell calculations [MDX]
ms.assetid: 45987daa-4400-41e9-add7-2428fd75709b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5a9c9d529bfeb26b959b2521e4ce3c3d7f10d082
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741393"
---
# <a name="creating-query-scoped-cell-calculations-mdx"></a><span data-ttu-id="5cdf8-102">クエリ スコープのセル計算の作成 (MDX)</span><span class="sxs-lookup"><span data-stu-id="5cdf8-102">Creating Query-Scoped Cell Calculations (MDX)</span></span>
  <span data-ttu-id="5cdf8-103">計算されるセルをクエリのコンテキストの中で記述するには、多次元式 (MDX) の `WITH` キーワードを使用します。</span><span class="sxs-lookup"><span data-stu-id="5cdf8-103">You use the `WITH` keyword in Multidimensional Expressions (MDX) to describe calculated cells within the context of a query.</span></span> <span data-ttu-id="5cdf8-104">`WITH` キーワードの構文は、以下のとおりです。</span><span class="sxs-lookup"><span data-stu-id="5cdf8-104">The `WITH` keyword has the following syntax:</span></span>  
  
```  
WITH CELL CALCULATION Cube_Name.CellCalc_Identifier  String_Expression  
```  
  
 <span data-ttu-id="5cdf8-105">`CellCalc_Identifier` の値は、計算されるセルの名前です。</span><span class="sxs-lookup"><span data-stu-id="5cdf8-105">The `CellCalc_Identifier` value is the name of the calculated cells.</span></span> <span data-ttu-id="5cdf8-106">`String_Expression` の値には、直交する 1 次元の MDX セット式の一覧を指定します。</span><span class="sxs-lookup"><span data-stu-id="5cdf8-106">The `String_Expression` value contains a list of orthogonal, single-dimensional MDX set expressions.</span></span> <span data-ttu-id="5cdf8-107">それぞれの式は次の表に示されているカテゴリのいずれかに解決する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5cdf8-107">Each of these set expressions must resolve to one of the categories listed in the following table.</span></span>  
  
|<span data-ttu-id="5cdf8-108">カテゴリ</span><span class="sxs-lookup"><span data-stu-id="5cdf8-108">Category</span></span>|<span data-ttu-id="5cdf8-109">説明</span><span class="sxs-lookup"><span data-stu-id="5cdf8-109">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="5cdf8-110">空セット</span><span class="sxs-lookup"><span data-stu-id="5cdf8-110">Empty set</span></span>|<span data-ttu-id="5cdf8-111">空セットに解決される MDX セット式。</span><span class="sxs-lookup"><span data-stu-id="5cdf8-111">An MDX set expression that resolves into an empty set.</span></span> <span data-ttu-id="5cdf8-112">この場合、計算されるセルのスコープはキューブ全体です。</span><span class="sxs-lookup"><span data-stu-id="5cdf8-112">In this case, the scope of the calculated cell is the whole cube.</span></span>|  
|<span data-ttu-id="5cdf8-113">単一メンバー セット</span><span class="sxs-lookup"><span data-stu-id="5cdf8-113">Single member set</span></span>|<span data-ttu-id="5cdf8-114">1 つのメンバーに解決される MDX セット式。</span><span class="sxs-lookup"><span data-stu-id="5cdf8-114">An MDX set expression that resolves into a single member.</span></span>|  
|<span data-ttu-id="5cdf8-115">レベル メンバーのセット</span><span class="sxs-lookup"><span data-stu-id="5cdf8-115">Set of level members</span></span>|<span data-ttu-id="5cdf8-116">単一レベルのメンバーに解決される MDX セット式。</span><span class="sxs-lookup"><span data-stu-id="5cdf8-116">An MDX set expression that resolves into the members of a single level.</span></span> <span data-ttu-id="5cdf8-117">このようなセット式の例としては、 *Level_Expression*があります。`Members`</span><span class="sxs-lookup"><span data-stu-id="5cdf8-117">An example of such a set expression is the *Level_Expression*.`Members`</span></span> <span data-ttu-id="5cdf8-118">MDX 関数です。</span><span class="sxs-lookup"><span data-stu-id="5cdf8-118">MDX function.</span></span> <span data-ttu-id="5cdf8-119">計算されるメンバーを含めるには、 *Level_Expression*を使用します。`AllMembers`</span><span class="sxs-lookup"><span data-stu-id="5cdf8-119">To include calculated members, use the *Level_Expression*.`AllMembers`</span></span> <span data-ttu-id="5cdf8-120">MDX 関数です。</span><span class="sxs-lookup"><span data-stu-id="5cdf8-120">MDX function.</span></span> <span data-ttu-id="5cdf8-121">詳細については、「[AllMembers (MDX)](/sql/mdx/allmembers-mdx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5cdf8-121">For more information, see [AllMembers &#40;MDX&#41;](/sql/mdx/allmembers-mdx).</span></span>|  
|<span data-ttu-id="5cdf8-122">子孫のセット</span><span class="sxs-lookup"><span data-stu-id="5cdf8-122">Set of descendants</span></span>|<span data-ttu-id="5cdf8-123">指定したメンバーの子孫に解決される MDX セット式。</span><span class="sxs-lookup"><span data-stu-id="5cdf8-123">An MDX set expression that resolves into the descendants of a specified member.</span></span> <span data-ttu-id="5cdf8-124">このようなセット式の例としては、 `Descendants` (*Member_Expression*、 *Level_Expresion*、 *Desc_Flag*) MDX 関数があります。</span><span class="sxs-lookup"><span data-stu-id="5cdf8-124">An example of such a set expression is the `Descendants`(*Member_Expression*, *Level_Expresion*, *Desc_Flag*) MDX function.</span></span> <span data-ttu-id="5cdf8-125">詳細については、「[Descendants (MDX)](/sql/mdx/descendants-mdx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5cdf8-125">For more information, see [Descendants &#40;MDX&#41;](/sql/mdx/descendants-mdx).</span></span>|  
  
 <span data-ttu-id="5cdf8-126">`String_Expression` 引数でディメンションが記述されていない場合、MDX は計算サブキューブの構築のためにすべてのメンバーが含まれていると想定します。</span><span class="sxs-lookup"><span data-stu-id="5cdf8-126">If the `String_Expression` argument does not describe a dimension, MDX assumes that all members are included for the purposes of constructing the calculation subcube.</span></span> <span data-ttu-id="5cdf8-127">したがって、 `String_Expression` 引数が NULL の場合、計算されるセルの定義はキューブ全体に適用されます。</span><span class="sxs-lookup"><span data-stu-id="5cdf8-127">Therefore, if the `String_Expression` argument is NULL, the calculated cells definition applies to the whole cube.</span></span>  
  
 <span data-ttu-id="5cdf8-128">`MDX_Expression` 引数には、 `String_Expression` 引数で定義したすべてのセルのセル値に評価される MDX 式を指定します。</span><span class="sxs-lookup"><span data-stu-id="5cdf8-128">The `MDX_Expression` argument contains an MDX expression that evaluates to a cell value for all the cells defined in the `String_Expression` argument.</span></span>  
  
## <a name="additional-considerations"></a><span data-ttu-id="5cdf8-129">その他の考慮事項</span><span class="sxs-lookup"><span data-stu-id="5cdf8-129">Additional Considerations</span></span>  
 <span data-ttu-id="5cdf8-130">`CONDITION` プロパティによって指定された計算条件は、MDX によって一度だけ処理されます。</span><span class="sxs-lookup"><span data-stu-id="5cdf8-130">MDX processes the calculation condition, specified by the `CONDITION` property, only once.</span></span> <span data-ttu-id="5cdf8-131">このように一度だけの処理を行うことにより、複数の計算されるセルの定義を評価する場合、特に計算されるセルがキューブ パス間で重複している場合のパフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="5cdf8-131">This single processing provides increased performance for the evaluation of multiple calculated cells definitions, especially with overlapping calculated cells across cube passes.</span></span>  
  
 <span data-ttu-id="5cdf8-132">この一度だけの処理がいつ行われるかは、計算されるセルの定義の作成スコープによって異なります。</span><span class="sxs-lookup"><span data-stu-id="5cdf8-132">When this single processing occurs depends on the creation scope of the calculated cells definition:</span></span>  
  
-   <span data-ttu-id="5cdf8-133">キューブの一部としてグローバル スコープで作成した計算条件は、MDX によってそのキューブの処理時に処理されます。</span><span class="sxs-lookup"><span data-stu-id="5cdf8-133">If created at global scope, as part of a cube, MDX process the calculation condition when the cube is processed.</span></span> <span data-ttu-id="5cdf8-134">キューブ内でセルがなんらかの方法で修正され、そのセルが計算されるセルの定義の計算サブキューブに含まれている場合は、キューブが再処理されるまで正確な計算条件が得られないことがあります。</span><span class="sxs-lookup"><span data-stu-id="5cdf8-134">If cells are modified in the cube in any way, and the cells are included in the calculation subcube of a calculated cells definition, the calculation condition may not be accurate until the cube is reprocessed.</span></span> <span data-ttu-id="5cdf8-135">たとえば、書き戻しによってセルの修正が発生する場合があります。</span><span class="sxs-lookup"><span data-stu-id="5cdf8-135">Cell modification can occur from writebacks, for example.</span></span> <span data-ttu-id="5cdf8-136">計算条件は、キューブと共に再処理されます。</span><span class="sxs-lookup"><span data-stu-id="5cdf8-136">The calculation condition is reprocessed when the cube is reprocessed.</span></span>  
  
-   <span data-ttu-id="5cdf8-137">セッション スコープで作成された計算条件は、MDX によってセッション中のステートメントの実行時に処理されます。</span><span class="sxs-lookup"><span data-stu-id="5cdf8-137">If created at session scope, MDX process the calculation condition when the statement is issued during the session.</span></span> <span data-ttu-id="5cdf8-138">グローバルに作成された計算されるセルの定義と同様に、この種の計算されるセルの定義の場合も、セルが修正されると正確な計算条件が得られないことがあります。</span><span class="sxs-lookup"><span data-stu-id="5cdf8-138">As with calculated cells definitions created globally, if the cells are modified, the calculation condition may not be accurate for the calculated cells definition.</span></span>  
  
-   <span data-ttu-id="5cdf8-139">クエリ スコープで作成された計算条件は、MDX によってクエリの実行時に処理されます。</span><span class="sxs-lookup"><span data-stu-id="5cdf8-139">If created at query scope, MDX processes the calculation condition when the query runs.</span></span> <span data-ttu-id="5cdf8-140">この場合もセルの修正に関する問題が当てはまりますが、MDX クエリの実行は処理時間が少ないため、データ待機時間に伴う問題は最小限に抑えられます。</span><span class="sxs-lookup"><span data-stu-id="5cdf8-140">The cell modification issue applies here, also, although data latency issues are minimal because of the low processing time of MDX query execution.</span></span>  
  
 <span data-ttu-id="5cdf8-141">一方、計算式は、計算されるセルの定義に含まれるセルを伴うキューブに対して MDX クエリが実行されるたびに MDX によって処理されます。</span><span class="sxs-lookup"><span data-stu-id="5cdf8-141">On the other hand, MDX processes the calculation formula whenever an MDX query is issued against the cube involving cells included in the calculated cells definition.</span></span> <span data-ttu-id="5cdf8-142">この処理は、作成スコープに関係なく行われます。</span><span class="sxs-lookup"><span data-stu-id="5cdf8-142">This processing occurs regardless of the creation scope.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cdf8-143">参照</span><span class="sxs-lookup"><span data-stu-id="5cdf8-143">See Also</span></span>  
 [<span data-ttu-id="5cdf8-144">CREATE CELL CALCULATION ステートメント (MDX)</span><span class="sxs-lookup"><span data-stu-id="5cdf8-144">CREATE CELL CALCULATION Statement &#40;MDX&#41;</span></span>](/sql/mdx/mdx-data-definition-create-cell-calculation)  
  
  
