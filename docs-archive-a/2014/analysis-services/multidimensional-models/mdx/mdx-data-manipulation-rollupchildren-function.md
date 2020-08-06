---
title: RollupChildren 関数の操作 (MDX) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- queries [MDX], RollupChildren function
- RollupChildren function
- custom member properties [MDX]
- IIf function
ms.assetid: 03c624d4-f277-451d-9995-623a07ea2f86
author: minewiskan
ms.author: owend
ms.openlocfilehash: 341468d521cebe1fda33d73ea999f3b6571cb01e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737038"
---
# <a name="working-with-the-rollupchildren-function-mdx"></a><span data-ttu-id="d72b6-102">RollupChildren 関数の操作 (MDX)</span><span class="sxs-lookup"><span data-stu-id="d72b6-102">Working with the RollupChildren Function (MDX)</span></span>
  <span data-ttu-id="d72b6-103">多次元式 (MDX) [Rollupchildren](/sql/mdx/rollupchildren-mdx) [Script for Search and Replace] 関数は、メンバーの子をロールアップし、それぞれの子に異なる単項演算子を適用して、このロールアップの値を数値として返します。</span><span class="sxs-lookup"><span data-stu-id="d72b6-103">The Multidimensional Expressions (MDX) [RollupChildren](/sql/mdx/rollupchildren-mdx) [Script for Search and Replace] function rolls up the children of a member, applying a different unary operator to each child, and returns the value of this rollup as a number.</span></span> <span data-ttu-id="d72b6-104">単項演算子は、子メンバーに関連付けられたメンバー プロパティによって提供されるか、関数に直接指定される文字列式の場合もあります。</span><span class="sxs-lookup"><span data-stu-id="d72b6-104">The unary operator can be supplied by a member property associated with the child member, or the operator can be a string expression provided directly to the function.</span></span>  
  
## <a name="rollupchildren-function-examples"></a><span data-ttu-id="d72b6-105">RollupChildren 関数の例</span><span class="sxs-lookup"><span data-stu-id="d72b6-105">RollupChildren Function Examples</span></span>  
 <span data-ttu-id="d72b6-106">`RollupChildren` 関数を多次元式 (MDX) ステートメントで使用する方法は簡単に説明できますが、この関数が MDX クエリに与える影響は広範囲にわたります。</span><span class="sxs-lookup"><span data-stu-id="d72b6-106">The use of the `RollupChildren` function in Multidimensional Expressions (MDX) statements is simple to explain, but the effect of this function on MDX queries can be wide-ranging.</span></span>  
  
 <span data-ttu-id="d72b6-107">`RollupChildren` 関数は、既存のキューブ データに対して選択的な分析を実行するように設計されている MDX クエリに影響を与えます。</span><span class="sxs-lookup"><span data-stu-id="d72b6-107">The effect of the `RollupChildren` function occurs in MDX queries designed to perform selective analysis on existing cube data.</span></span> <span data-ttu-id="d72b6-108">たとえば、次の表は、Net Sales 親メンバーの子メンバーの一覧です。かっこ内は各子メンバーの単項演算子です (`UNARY_OPERATOR` メンバー プロパティによって表されます)。</span><span class="sxs-lookup"><span data-stu-id="d72b6-108">For example, the following table contains a list of child members for the Net Sales parent member, with their unary operators (represented by the `UNARY_OPERATOR` member property) shown in parentheses.</span></span>  
  
|<span data-ttu-id="d72b6-109">[親メンバー]</span><span class="sxs-lookup"><span data-stu-id="d72b6-109">Parent member</span></span>|<span data-ttu-id="d72b6-110">子メンバー</span><span class="sxs-lookup"><span data-stu-id="d72b6-110">Child member</span></span>|  
|-------------------|------------------|  
|<span data-ttu-id="d72b6-111">純売上高</span><span class="sxs-lookup"><span data-stu-id="d72b6-111">Net Sales</span></span>|<span data-ttu-id="d72b6-112">国内売上 (+)</span><span class="sxs-lookup"><span data-stu-id="d72b6-112">Domestic Sales (+)</span></span><br /><br /> <span data-ttu-id="d72b6-113">国内返品 (-)</span><span class="sxs-lookup"><span data-stu-id="d72b6-113">Domestic Returns (-)</span></span><br /><br /> <span data-ttu-id="d72b6-114">国外売上 (+)</span><span class="sxs-lookup"><span data-stu-id="d72b6-114">Foreign Sales (+)</span></span><br /><br /> <span data-ttu-id="d72b6-115">国外返品 (-)</span><span class="sxs-lookup"><span data-stu-id="d72b6-115">Foreign Returns (-)</span></span>|  
  
 <span data-ttu-id="d72b6-116">現在、Net Sales 親メンバーは、売上の総合計から、国内と国外の返品の合計値を差し引いた値に相当します。国内と国外の返品は、ロールアップの一部として減算されています。</span><span class="sxs-lookup"><span data-stu-id="d72b6-116">The Net Sales parent member currently provides a total of net sales minus the gross domestic and foreign sales values, with the domestic and foreign returns subtracted as part of the rollup.</span></span>  
  
 <span data-ttu-id="d72b6-117">ここで、国内と国外の返品は無視し、国内と国外の総売上が 10% 増加した場合の予測をすばやく簡単に行いたいとします。</span><span class="sxs-lookup"><span data-stu-id="d72b6-117">However, you want to provide a quick and easy forecast of domestic and foreign gross sales plus 10%, ignoring the domestic and foreign returns.</span></span> <span data-ttu-id="d72b6-118">この値を計算するには、`RollupChildren` 関数を 2 つの方法で使用できます。1 つはカスタム メンバー プロパティを使用する方法で、もう 1 つは `IIf` 関数を使用する方法です。</span><span class="sxs-lookup"><span data-stu-id="d72b6-118">To calculate this value, you can use the `RollupChildren` function in one of two ways: with a custom member property or with the `IIf` function.</span></span>  
  
### <a name="using-a-custom-member-property"></a><span data-ttu-id="d72b6-119">カスタム メンバー プロパティの使用</span><span class="sxs-lookup"><span data-stu-id="d72b6-119">Using a Custom Member Property</span></span>  
 <span data-ttu-id="d72b6-120">ロールアップ計算を頻繁に実行する場合、特定の関数に対してそれぞれの子が使用する演算子を格納するメンバー プロパティを作成しておくという方法があります。</span><span class="sxs-lookup"><span data-stu-id="d72b6-120">If the rollup calculation is to be a frequently performed operation, one method is to create a member property that stores the operator that will be used for each child for a specific function.</span></span> <span data-ttu-id="d72b6-121">次の表では、有効な単項演算子を示し、予期される結果を説明します。</span><span class="sxs-lookup"><span data-stu-id="d72b6-121">The following table displays valid unary operators and describes the expected result.</span></span>  
  
|<span data-ttu-id="d72b6-122">演算子</span><span class="sxs-lookup"><span data-stu-id="d72b6-122">Operator</span></span>|<span data-ttu-id="d72b6-123">結果</span><span class="sxs-lookup"><span data-stu-id="d72b6-123">Result</span></span>|  
|--------------|------------|  
|+|<span data-ttu-id="d72b6-124">合計 = 合計 + 現在の子</span><span class="sxs-lookup"><span data-stu-id="d72b6-124">total = total + current child</span></span>|  
|-|<span data-ttu-id="d72b6-125">合計 = 合計 - 現在の子</span><span class="sxs-lookup"><span data-stu-id="d72b6-125">total = total - current child</span></span>|  
|*|<span data-ttu-id="d72b6-126">合計 = 合計 \* 現在の子</span><span class="sxs-lookup"><span data-stu-id="d72b6-126">total = total \* current child</span></span>|  
|/|<span data-ttu-id="d72b6-127">合計 = 合計 / 現在の子</span><span class="sxs-lookup"><span data-stu-id="d72b6-127">total = total / current child</span></span>|  
|~|<span data-ttu-id="d72b6-128">子はロールアップでは使用されません。</span><span class="sxs-lookup"><span data-stu-id="d72b6-128">Child is not used in the rollup.</span></span> <span data-ttu-id="d72b6-129">子の値は無視されます。</span><span class="sxs-lookup"><span data-stu-id="d72b6-129">The child's value is ignored.</span></span>|  
  
 <span data-ttu-id="d72b6-130">たとえば、`SALES_OPERATOR` というメンバー プロパティを作成し、次の表に示すように、単項演算子をそのメンバー プロパティに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="d72b6-130">For example, a member property called `SALES_OPERATOR` could be created, and the following unary operators would be assigned to that member property, as shown in the following table.</span></span>  
  
|<span data-ttu-id="d72b6-131">[親メンバー]</span><span class="sxs-lookup"><span data-stu-id="d72b6-131">Parent member</span></span>|<span data-ttu-id="d72b6-132">子メンバー</span><span class="sxs-lookup"><span data-stu-id="d72b6-132">Child member</span></span>|  
|-------------------|------------------|  
|<span data-ttu-id="d72b6-133">純売上高</span><span class="sxs-lookup"><span data-stu-id="d72b6-133">Net Sales</span></span>|<span data-ttu-id="d72b6-134">国内売上 (+)</span><span class="sxs-lookup"><span data-stu-id="d72b6-134">Domestic Sales (+)</span></span><br /><br /> <span data-ttu-id="d72b6-135">国内返品 (~)</span><span class="sxs-lookup"><span data-stu-id="d72b6-135">Domestic Returns (~)</span></span><br /><br /> <span data-ttu-id="d72b6-136">国外売上 (+)</span><span class="sxs-lookup"><span data-stu-id="d72b6-136">Foreign Sales (+)</span></span><br /><br /> <span data-ttu-id="d72b6-137">国外返品 (~)</span><span class="sxs-lookup"><span data-stu-id="d72b6-137">Foreign Returns (~)</span></span>|  
  
 <span data-ttu-id="d72b6-138">この新しいメンバー プロパティを使用すれば、次の MDX ステートメントで、総売上の予測をすばやく効率的に実行できます (国外と国内の返品は無視されます)。</span><span class="sxs-lookup"><span data-stu-id="d72b6-138">With this new member property, the following MDX statement would perform the gross sales estimate operation quickly and efficiently (ignoring Foreign and Domestic returns):</span></span>  
  
```  
RollupChildren([Net Sales], [Net Sales].CurrentMember.Properties("SALES_OPERATOR")) * 1.1  
```  
  
 <span data-ttu-id="d72b6-139">関数が呼び出されると、それぞれの子の値は、メンバー プロパティに格納されている演算子を使用して合計に算入されます。</span><span class="sxs-lookup"><span data-stu-id="d72b6-139">When the function is called, the value of each child is applied to a total using the operator stored in the member property.</span></span> <span data-ttu-id="d72b6-140">国内と国外の返品のメンバーは無視され、`RollupChildren` 関数によって返されるロールアップ合計に 1.1 が乗算されます。</span><span class="sxs-lookup"><span data-stu-id="d72b6-140">The members for domestic and foreign returns are ignored, and the rollup total returned by the `RollupChildren` function is multiplied by 1.1.</span></span>  
  
### <a name="using-the-iif-function"></a><span data-ttu-id="d72b6-141">IIf 関数の使用</span><span class="sxs-lookup"><span data-stu-id="d72b6-141">Using the IIf Function</span></span>  
 <span data-ttu-id="d72b6-142">この例の操作が一般的でない場合、または操作が1つの MDX クエリのみに適用される場合は、関数と共に[IIf](/sql/mdx/iif-mdx)関数を使用して同じ結果を得ることができ `RollupChildren` ます。</span><span class="sxs-lookup"><span data-stu-id="d72b6-142">If the example operation is not commonplace or if the operation applies only to one MDX query, the [IIf](/sql/mdx/iif-mdx) function can be used with the `RollupChildren` function to provide the same result.</span></span> <span data-ttu-id="d72b6-143">次の MDX クエリでは、前の例の MDX クエリと同じ結果を返します。ただし、カスタム メンバー プロパティは使用していません。</span><span class="sxs-lookup"><span data-stu-id="d72b6-143">The following MDX query provides the same result as the earlier MDX example, but does so without resorting to the use of a custom member property:</span></span>  
  
```  
RollupChildren([Net Sales], IIf([Net Sales].CurrentMember.Properties("UNARY_OPERATOR") = "-", "~", [Net Sales].CurrentMember.Properties("UNARY_OPERATOR))) * 1.1  
```  
  
 <span data-ttu-id="d72b6-144">MDX ステートメントは、子メンバーの単項演算子を調べます。</span><span class="sxs-lookup"><span data-stu-id="d72b6-144">The MDX statement examines the unary operator of the child member.</span></span> <span data-ttu-id="d72b6-145">単項演算子が減算 (この例では、国内と国外の返品のメンバーの場合) のために使用されている場合、`IIf` 関数はその代わりにティルダ (~) 単項演算子を使用します。</span><span class="sxs-lookup"><span data-stu-id="d72b6-145">If the unary operator is used for subtraction (as in the case with the domestic and foreign returns members), the `IIf` function substitutes the tilde (~) unary operator.</span></span> <span data-ttu-id="d72b6-146">それ以外の場合、`IIf` 関数は子メンバーの単項演算子を使用します。</span><span class="sxs-lookup"><span data-stu-id="d72b6-146">Otherwise, the `IIf` function uses the unary operator of the child member.</span></span> <span data-ttu-id="d72b6-147">最後に、返されたロールアップ合計に 1.1 が乗算され、国内と国外の総売上の予測値が得られます。</span><span class="sxs-lookup"><span data-stu-id="d72b6-147">Finally, the returned rollup total is then multiplied by 1.1 to provide the domestic and foreign gross sales forecast value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d72b6-148">参照</span><span class="sxs-lookup"><span data-stu-id="d72b6-148">See Also</span></span>  
 [<span data-ttu-id="d72b6-149">データの操作 (MDX)</span><span class="sxs-lookup"><span data-stu-id="d72b6-149">Manipulating Data &#40;MDX&#41;</span></span>](mdx-data-manipulation-manipulating-data.md)  
  
  
