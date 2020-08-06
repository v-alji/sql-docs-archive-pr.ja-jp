---
title: セッションスコープの計算されるセルを作成する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- session-scoped calculated members [MDX]
ms.assetid: f2d14a89-6286-4e74-9afb-091076f93f21
author: minewiskan
ms.author: owend
ms.openlocfilehash: 199de07778a153cd1bc40b5033d364e5e0055bd3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639702"
---
# <a name="creating-session-scoped-calculated-cells"></a><span data-ttu-id="d439d-102">セッション スコープの計算されるセルの作成</span><span class="sxs-lookup"><span data-stu-id="d439d-102">Creating Session-Scoped Calculated Cells</span></span>
    
> [!IMPORTANT]  
>  <span data-ttu-id="d439d-103">この構文は非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="d439d-103">This syntax has been deprecated.</span></span> <span data-ttu-id="d439d-104">代わりに、MDX 割り当てを使用してください。</span><span class="sxs-lookup"><span data-stu-id="d439d-104">You should use MDX assignments should instead.</span></span> <span data-ttu-id="d439d-105">割り当ての詳細については、「[基本的な MDX スクリプト &#40;MDX&#41;](the-basic-mdx-script-mdx.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d439d-105">For more information on assignments, see [The Basic MDX Script &#40;MDX&#41;](the-basic-mdx-script-mdx.md).</span></span>  
  
 <span data-ttu-id="d439d-106">同じセッション内のすべてのクエリで使用可能な計算されるセルを作成するには、 [CREATE CELL CALCULATION](/sql/mdx/mdx-data-definition-create-cell-calculation) ステートメントまたは [ALTER CUBE](/sql/mdx/mdx-data-definition-alter-cube) ステートメントを使用できます。</span><span class="sxs-lookup"><span data-stu-id="d439d-106">To create calculated cells that are available to all queries in the same session, you can use either the [CREATE CELL CALCULATION](/sql/mdx/mdx-data-definition-create-cell-calculation) statement or the [ALTER CUBE](/sql/mdx/mdx-data-definition-alter-cube) statement.</span></span> <span data-ttu-id="d439d-107">どちらのステートメントを使用しても結果は同じになります。</span><span class="sxs-lookup"><span data-stu-id="d439d-107">Both statements have the same result.</span></span>  
  
## <a name="create-cell-calculation-syntax"></a><span data-ttu-id="d439d-108">CREATE CELL CALCULATION の構文</span><span class="sxs-lookup"><span data-stu-id="d439d-108">CREATE CELL CALCULATION Syntax</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="d439d-109">この構文は非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="d439d-109">This syntax has been deprecated.</span></span> <span data-ttu-id="d439d-110">代わりに、MDX 割り当てを使用してください。</span><span class="sxs-lookup"><span data-stu-id="d439d-110">You should use MDX assignments should instead.</span></span> <span data-ttu-id="d439d-111">割り当ての詳細については、「[基本的な MDX スクリプト &#40;MDX&#41;](the-basic-mdx-script-mdx.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d439d-111">For more information on assignments, see [The Basic MDX Script &#40;MDX&#41;](the-basic-mdx-script-mdx.md).</span></span>  
  
 <span data-ttu-id="d439d-112">セッション スコープの計算されるセルを定義するために CREATE CELL CALCULATION ステートメントを使用するには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="d439d-112">Use the following syntax to use the CREATE CELL CALCULATION statement to define a session-scoped calculated cell:</span></span>  
  
```  
CREATE CELL CALCULATION Cube_Expression.<CREATE CELL CALCULATION body clause>  
  
<CREATE CELL CALCULATION body clause> ::=CellCalc_Identifier FOR String_Expression AS 'MDX_Expression'   
   [ <CREATE CELL CALCULATION property clause> [ , <CREATE CELL CALCULATION property clause> ... ] ]  
  
<CREATE CELL CALCULATION property clause> ::=  
   ( CONDITION = 'Logical_Expression' ) |   
   ( DISABLED = { TRUE | FALSE } ) |   
   ( DESCRIPTION =String_Expression ) |   
   ( CALCULATION_PASS_NUMBER = Integer_Expression ) |   
   ( CALCULATION_PASS_DEPTH = Integer_Expression ) |   
   ( SOLVE_ORDER = Integer_Expression ) |   
   ( FORMAT_STRING = String_Expression ) |   
   ( CellProperty_Identifier = Scalar_Expression )  
```  
  
## <a name="alter-cube-syntax"></a><span data-ttu-id="d439d-113">ALTER CUBE の構文</span><span class="sxs-lookup"><span data-stu-id="d439d-113">ALTER CUBE Syntax</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="d439d-114">この構文は非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="d439d-114">This syntax has been deprecated.</span></span> <span data-ttu-id="d439d-115">代わりに、MDX 割り当てを使用してください。</span><span class="sxs-lookup"><span data-stu-id="d439d-115">You should use MDX assignments should instead.</span></span> <span data-ttu-id="d439d-116">割り当ての詳細については、「[基本的な MDX スクリプト &#40;MDX&#41;](the-basic-mdx-script-mdx.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d439d-116">For more information on assignments, see [The Basic MDX Script &#40;MDX&#41;](the-basic-mdx-script-mdx.md).</span></span>  
  
 <span data-ttu-id="d439d-117">セッション スコープの計算されるセルを定義するために ALTER CUBE ステートメントを使用するには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="d439d-117">Use the following syntax to use the ALTER CUBE statement to define a session-scoped calculated cell:</span></span>  
  
```  
ALTER CUBE Cube_Identifier CREATE CELL CALCULATION  
FOR String_Expression AS 'MDX_Expression'   
   [ <CREATE CELL CALCULATION property clause> [ , <CREATE CELL CALCULATION property clause> ... ] ]  
  
<CREATE CELL CALCULATION property clause> ::=  
   ( CONDITION = 'Logical_Expression' ) |   
   ( DISABLED = { TRUE | FALSE } ) |   
   ( DESCRIPTION =String_Expression ) |   
   ( CALCULATION_PASS_NUMBER = Integer_Expression ) |   
   ( CALCULATION_PASS_DEPTH = Integer_Expression ) |   
   ( SOLVE_ORDER = Integer_Expression ) |   
   ( FORMAT_STRING = String_Expression ) |   
   ( CellProperty_Identifier = Scalar_Expression )  
```  
  
 <span data-ttu-id="d439d-118">`String_Expression` 値には、直交する 1 次元の MDX セット式のリストを指定します。それぞれの式は、次の表のいずれかのセット カテゴリに解決される必要があります。</span><span class="sxs-lookup"><span data-stu-id="d439d-118">The `String_Expression` value contains a list of orthogonal, single-dimensional MDX set expressions, each of which must resolve to one of the categories of sets that are listed in the following table.</span></span>  
  
|<span data-ttu-id="d439d-119">カテゴリ</span><span class="sxs-lookup"><span data-stu-id="d439d-119">Category</span></span>|<span data-ttu-id="d439d-120">説明</span><span class="sxs-lookup"><span data-stu-id="d439d-120">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="d439d-121">空セット</span><span class="sxs-lookup"><span data-stu-id="d439d-121">Empty set</span></span>|<span data-ttu-id="d439d-122">空セットに解決される MDX セット式。</span><span class="sxs-lookup"><span data-stu-id="d439d-122">An MDX set expression that resolves into an empty set.</span></span> <span data-ttu-id="d439d-123">この場合、計算されるセルのスコープはキューブ全体です。</span><span class="sxs-lookup"><span data-stu-id="d439d-123">In this case, the scope of the calculated cell is the whole cube.</span></span>|  
|<span data-ttu-id="d439d-124">単一メンバー セット</span><span class="sxs-lookup"><span data-stu-id="d439d-124">Single member set</span></span>|<span data-ttu-id="d439d-125">1 つのメンバーに解決される MDX セット式。</span><span class="sxs-lookup"><span data-stu-id="d439d-125">An MDX set expression that resolves into a single member.</span></span>|  
|<span data-ttu-id="d439d-126">レベル メンバーのセット</span><span class="sxs-lookup"><span data-stu-id="d439d-126">Set of level members</span></span>|<span data-ttu-id="d439d-127">単一レベルのメンバーに解決される MDX セット式。</span><span class="sxs-lookup"><span data-stu-id="d439d-127">An MDX set expression that resolves into the members of a single level.</span></span> <span data-ttu-id="d439d-128">この例としては、 *Level_Expression*があります。`Members`</span><span class="sxs-lookup"><span data-stu-id="d439d-128">An example of this is the *Level_Expression*.`Members`</span></span> <span data-ttu-id="d439d-129">MDX 関数です。</span><span class="sxs-lookup"><span data-stu-id="d439d-129">MDX function.</span></span> <span data-ttu-id="d439d-130">計算されるメンバーを含めるには、 *Level_Expression*を使用します。`AllMembers`</span><span class="sxs-lookup"><span data-stu-id="d439d-130">To include calculated members, use the *Level_Expression*.`AllMembers`</span></span> <span data-ttu-id="d439d-131">MDX 関数です。</span><span class="sxs-lookup"><span data-stu-id="d439d-131">MDX function.</span></span><br /><br /> <span data-ttu-id="d439d-132">詳細については、「[AllMembers (MDX)](/sql/mdx/allmembers-mdx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d439d-132">For more information, see [AllMembers &#40;MDX&#41;](/sql/mdx/allmembers-mdx).</span></span>|  
|<span data-ttu-id="d439d-133">子孫のセット</span><span class="sxs-lookup"><span data-stu-id="d439d-133">Set of descendants</span></span>|<span data-ttu-id="d439d-134">指定したメンバーの子孫に解決される MDX セット式。</span><span class="sxs-lookup"><span data-stu-id="d439d-134">An MDX set expression that resolves into the descendants of a specified member.</span></span> <span data-ttu-id="d439d-135">この例として、 `Descendants` (*Member_Expression*、 *Level_Expression*、 *Desc_Flag*) MDX 関数があります。</span><span class="sxs-lookup"><span data-stu-id="d439d-135">An example of this is the `Descendants`(*Member_Expression*, *Level_Expression*, *Desc_Flag*) MDX function.</span></span><br /><br /> <span data-ttu-id="d439d-136">詳細については、「[Descendants (MDX)](/sql/mdx/descendants-mdx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d439d-136">For more information, see [Descendants &#40;MDX&#41;](/sql/mdx/descendants-mdx).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d439d-137">参照</span><span class="sxs-lookup"><span data-stu-id="d439d-137">See Also</span></span>  
 [<span data-ttu-id="d439d-138">MDX でのセル計算の作成 &#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="d439d-138">Building Cell Calculations in MDX &#40;MDX&#41;</span></span>](../../multidimensional-models-olap-logical-cube-objects/calculations.md)  
  
  
