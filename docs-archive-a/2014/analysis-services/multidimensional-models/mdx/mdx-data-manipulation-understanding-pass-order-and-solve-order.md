---
title: パス順序と解決順序について (MDX) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- evaluation order [MDX]
- calculation order [MDX]
- SOLVE_ORDER property
- queries [MDX], solve orders
- solve orders [MDX]
- pass orders [MDX]
- expressions [MDX], solve orders
ms.assetid: 7ed7d4ee-4644-4c5d-99a4-c4b429d0203c
author: minewiskan
ms.author: owend
ms.openlocfilehash: d92ccd9d1eeb05272a95c6f429f8c756bcb0022e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639700"
---
# <a name="understanding-pass-order-and-solve-order-mdx"></a><span data-ttu-id="4e77a-102">パス順序と解決順序の概要 (MDX)</span><span class="sxs-lookup"><span data-stu-id="4e77a-102">Understanding Pass Order and Solve Order (MDX)</span></span>
  <span data-ttu-id="4e77a-103">MDX スクリプトの結果としてキューブが計算される場合、計算に関連するさまざまな機能の使われ方によっては、キューブは多数の計算段階をたどることがあります。</span><span class="sxs-lookup"><span data-stu-id="4e77a-103">When a cube is calculated as the result of an MDX script, it can go through many stages of computation depending on the use of various calculation-related features.</span></span> <span data-ttu-id="4e77a-104">それらの各段階は、計算パスと呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="4e77a-104">Each of these stages is referred to as a calculation pass.</span></span>  
  
 <span data-ttu-id="4e77a-105">計算パスは、計算パス番号と呼ばれる序数で表すこともできます。</span><span class="sxs-lookup"><span data-stu-id="4e77a-105">A calculation pass can be referred to by an ordinal position, called the calculation pass number.</span></span> <span data-ttu-id="4e77a-106">キューブのセルすべてを完全に計算するために必要な計算パスの数を、キューブの計算パスの深さと呼びます。</span><span class="sxs-lookup"><span data-stu-id="4e77a-106">The count of calculation passes that are required to fully compute all the cells of a cube is referred to as the calculation pass depth of the cube.</span></span>  
  
 <span data-ttu-id="4e77a-107">パス 0 に影響するのはファクト テーブルと書き戻しデータだけです。</span><span class="sxs-lookup"><span data-stu-id="4e77a-107">Fact table and writeback data only impact pass 0.</span></span> <span data-ttu-id="4e77a-108">スクリプトがデータを設定するのはパス 0 の後です。ステートメント内に代入や計算ステートメントがある場合、新しいパスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="4e77a-108">Scripts populate data after pass 0; each assignment and calculate statement in a script creates a new pass.</span></span> <span data-ttu-id="4e77a-109">MDX スクリプト以外では、絶対パス 0 への参照がある場合、それはキューブに対するスクリプトによって最後に作成されたパスを意味します。</span><span class="sxs-lookup"><span data-stu-id="4e77a-109">Outside the MDX script, references to absolute pass 0 refer to the last pass created by the script for the cube.</span></span>  
  
 <span data-ttu-id="4e77a-110">計算されるメンバーはすべてのパスで作成されますが、式が適用されるのは現在のパスです。</span><span class="sxs-lookup"><span data-stu-id="4e77a-110">Calculated members are created at all passes, but the expression is applied at the current pass.</span></span> <span data-ttu-id="4e77a-111">以前のパスには計算されるメジャーが含まれますが、値は NULL です。</span><span class="sxs-lookup"><span data-stu-id="4e77a-111">Prior passes contain the calculated measure, but with a null value.</span></span>  
  
## <a name="solve-order"></a><span data-ttu-id="4e77a-112">解決順序</span><span class="sxs-lookup"><span data-stu-id="4e77a-112">Solve Order</span></span>  
 <span data-ttu-id="4e77a-113">解決順序は、競合する式がある場合に計算の優先順位を決定します。</span><span class="sxs-lookup"><span data-stu-id="4e77a-113">Solve order determines the priority of calculation in the event of competing expressions.</span></span> <span data-ttu-id="4e77a-114">1 つのパスの中では、解決順序によって以下の 2 つの順序が決まります。</span><span class="sxs-lookup"><span data-stu-id="4e77a-114">Within a single pass, solve order determines two things:</span></span>  
  
-   <span data-ttu-id="4e77a-115">が [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] ディメンション、メンバー、計算されるメンバー、カスタムロールアップ、および計算されるセルを評価する順序。</span><span class="sxs-lookup"><span data-stu-id="4e77a-115">The order in which [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] evaluates dimensions, members, calculated members, custom rollups, and calculated cells.</span></span>  
  
-   <span data-ttu-id="4e77a-116">カスタム メンバー、計算されるメンバー、カスタム ロールアップ、および計算されるセルが [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] によって計算される順序。</span><span class="sxs-lookup"><span data-stu-id="4e77a-116">The order in which [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] calculates custom members, calculated members, custom rollup, and calculated cells.</span></span>  
  
 <span data-ttu-id="4e77a-117">最も高い解決順序を持つメンバーが最も優先されます。</span><span class="sxs-lookup"><span data-stu-id="4e77a-117">The member with the highest solve order takes precedence.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4e77a-118">この優先順位に関する例外は、Aggregate 関数です。</span><span class="sxs-lookup"><span data-stu-id="4e77a-118">The exception to this precedence is the Aggregate function.</span></span> <span data-ttu-id="4e77a-119">Aggregate 関数を使用して計算されるメンバーの解決順序は、交差するどの計算されるメジャーの解決順序よりも低くなります。</span><span class="sxs-lookup"><span data-stu-id="4e77a-119">Calculated members with the Aggregate function have a lower solve order than any intersecting calculated measure.</span></span>  
  
## <a name="solve-order-values-and-precedence"></a><span data-ttu-id="4e77a-120">解決順序の値と優先順位</span><span class="sxs-lookup"><span data-stu-id="4e77a-120">Solve Order Values and Precedence</span></span>  
 <span data-ttu-id="4e77a-121">解決順序は、-8,181 ～ 65,535 の値をとります。</span><span class="sxs-lookup"><span data-stu-id="4e77a-121">Solve order values can range from -8181 to 65535.</span></span> <span data-ttu-id="4e77a-122">この範囲内で、いくつかの解決順序の値は、次の表のように特定の種類の計算に対応しています。</span><span class="sxs-lookup"><span data-stu-id="4e77a-122">In this range, some solve order values correspond to specific kinds of calculations, as shown in the following table.</span></span>  
  
|<span data-ttu-id="4e77a-123">計算</span><span class="sxs-lookup"><span data-stu-id="4e77a-123">Calculation</span></span>|<span data-ttu-id="4e77a-124">解決順序</span><span class="sxs-lookup"><span data-stu-id="4e77a-124">Solve Order</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="4e77a-125">カスタム メンバー式</span><span class="sxs-lookup"><span data-stu-id="4e77a-125">Custom member formulas</span></span>|<span data-ttu-id="4e77a-126">-5119</span><span class="sxs-lookup"><span data-stu-id="4e77a-126">-5119</span></span>|  
|<span data-ttu-id="4e77a-127">単項演算子</span><span class="sxs-lookup"><span data-stu-id="4e77a-127">Unary operators</span></span>|<span data-ttu-id="4e77a-128">-5119</span><span class="sxs-lookup"><span data-stu-id="4e77a-128">-5119</span></span>|  
|<span data-ttu-id="4e77a-129">表示部分の合計計算</span><span class="sxs-lookup"><span data-stu-id="4e77a-129">Visual totals calculation</span></span>|<span data-ttu-id="4e77a-130">-4096</span><span class="sxs-lookup"><span data-stu-id="4e77a-130">-4096</span></span>|  
|<span data-ttu-id="4e77a-131">その他のすべての計算 (特に指定されていない場合)</span><span class="sxs-lookup"><span data-stu-id="4e77a-131">All other calculations (if not otherwise specified)</span></span>|<span data-ttu-id="4e77a-132">0</span><span class="sxs-lookup"><span data-stu-id="4e77a-132">0</span></span>|  
  
 <span data-ttu-id="4e77a-133">解決順序の値を設定するときは、正の整数のみを使用することを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="4e77a-133">It is highly recommended that you use only positive integers when setting solve order values.</span></span> <span data-ttu-id="4e77a-134">前の表に示されている解決順序の値よりも低い値を割り当てると、計算パスが予測不能になることがあります。</span><span class="sxs-lookup"><span data-stu-id="4e77a-134">If you assign values that are lower than the solve order values shown in the previous table, the calculation pass can become unpredictable.</span></span> <span data-ttu-id="4e77a-135">たとえば、計算されるメンバーの計算に、解決順序の値として既定のカスタム ロールアップ式の値である -5119 より低い値を割り当てるとします。</span><span class="sxs-lookup"><span data-stu-id="4e77a-135">For example, the calculation for a calculated member receives a solve order value that is lower than the default custom rollup formula value of -5119.</span></span> <span data-ttu-id="4e77a-136">このように低い解決順序の値を持つ計算されるメンバーはカスタム ロールアップ式より先に計算され、正確な結果が得られないことがあります。</span><span class="sxs-lookup"><span data-stu-id="4e77a-136">Such a low solve order value causes the calculated members to be calculated before the custom rollup formulas, and can produce incorrect results.</span></span>  
  
### <a name="creating-and-changing-solve-order"></a><span data-ttu-id="4e77a-137">解決順序の作成と変更</span><span class="sxs-lookup"><span data-stu-id="4e77a-137">Creating and Changing Solve Order</span></span>  
 <span data-ttu-id="4e77a-138">キューブ デザイナーでは、 **[計算]** ペインで計算の順序を変更することによって、計算されるメンバーと計算されるセルの解決順序を変更できます。</span><span class="sxs-lookup"><span data-stu-id="4e77a-138">In Cube Designer, on the **Calculations Pane**, you can change the solve order for calculated members and calculated cells by changing the order of the calculations.</span></span>  
  
 <span data-ttu-id="4e77a-139">MDX では、計算されるメンバーや計算されるセルを作成または変更するときに `SOLVE_ORDER` キーワードを使用できます。</span><span class="sxs-lookup"><span data-stu-id="4e77a-139">In MDX, you can use the `SOLVE_ORDER` keyword to create or change calculated members and calculated cells.</span></span>  
  
## <a name="solve-order-examples"></a><span data-ttu-id="4e77a-140">解決順序の例</span><span class="sxs-lookup"><span data-stu-id="4e77a-140">Solve Order Examples</span></span>  
 <span data-ttu-id="4e77a-141">解決順序がどれほど複雑なものになることがあるかを示すために、個別のクエリとしては解決順序を考慮する必要のない 2 つのクエリで始まる一連の MDX クエリを次に示します。</span><span class="sxs-lookup"><span data-stu-id="4e77a-141">To illustrate the potential complexities of solve order, the following series of MDX queries starts with two queries that each individually have no solve order issues.</span></span> <span data-ttu-id="4e77a-142">それらの 2 つのクエリを組み合わせると、解決順序を考慮しなければならないクエリになります。</span><span class="sxs-lookup"><span data-stu-id="4e77a-142">These two queries are then combined into a query that requires solve order.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4e77a-143">Adventure Works サンプル多次元データベースに対してこれらの MDX クエリを実行できます。</span><span class="sxs-lookup"><span data-stu-id="4e77a-143">You can run these MDX queries against the Adventure Works sample multidimensional database.</span></span> <span data-ttu-id="4e77a-144">[AdventureWorks Multidimensional Models SQL Server 2012](https://msftdbprodsamples.codeplex.com/releases/view/55330) サンプルは、CodePlex サイトからダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="4e77a-144">You can download the [AdventureWorks Multidimensional Models SQL Server 2012](https://msftdbprodsamples.codeplex.com/releases/view/55330) sample from the codeplex site.</span></span>  
  
### <a name="query-1-differences-in-income-and-expenses"></a><span data-ttu-id="4e77a-145">クエリ 1-収益と経費の違い</span><span class="sxs-lookup"><span data-stu-id="4e77a-145">Query 1-Differences in Income and Expenses</span></span>  
 <span data-ttu-id="4e77a-146">1 番目の MDX クエリとして、年ごとの売上とコストの差を計算するために、次の例のような単純な MDX クエリを作成します。</span><span class="sxs-lookup"><span data-stu-id="4e77a-146">For the first MDX query, calculate the difference in sales and costs for each year by constructing a simple MDX query similar to the following example:</span></span>  
  
```  
WITH   
MEMBER  
[Date].[Calendar].[Year Difference] AS ([Date].[Calendar].[Calendar Year].&[2008] - [Date].[Calendar].[Calendar Year].&[2007] )  
SELECT   
{[Measures].[Internet Sales Amount], [Measures].[Internet Total Product Cost] }  
ON COLUMNS ,  
{ [Date].[Calendar].[Calendar Year].&[2007], [Date].[Calendar].[Calendar Year].&[2008], [Date].[Year Difference] }  
ON ROWS  
FROM [Adventure Works]  
```  
  
 <span data-ttu-id="4e77a-147">このクエリでは、計算されるメンバーは `Year Difference`の 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="4e77a-147">In this query, there is only one calculated member, `Year Difference`.</span></span> <span data-ttu-id="4e77a-148">計算されるメンバーが 1 つだけなので、キューブで計算されるメンバーが使用されない限り、解決順序を考慮する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="4e77a-148">Because there is only one calculated member, solve order is not an issue, as long as the cube does not use any calculated members.</span></span>  
  
 <span data-ttu-id="4e77a-149">この MDX クエリは、次の表のような結果セットを作成します。</span><span class="sxs-lookup"><span data-stu-id="4e77a-149">This MDX query produces a result set similar to the following table.</span></span>  
  
||<span data-ttu-id="4e77a-150">Internet Sales Amount</span><span class="sxs-lookup"><span data-stu-id="4e77a-150">Internet Sales Amount</span></span>|<span data-ttu-id="4e77a-151">Internet Total Product Cost</span><span class="sxs-lookup"><span data-stu-id="4e77a-151">Internet Total Product Cost</span></span>|  
|-|---------------------------|---------------------------------|  
|<span data-ttu-id="4e77a-152">**CY 2007**</span><span class="sxs-lookup"><span data-stu-id="4e77a-152">**CY 2007**</span></span>|<span data-ttu-id="4e77a-153">$9,791,060.30</span><span class="sxs-lookup"><span data-stu-id="4e77a-153">$9,791,060.30</span></span>|<span data-ttu-id="4e77a-154">$5,718,327.17</span><span class="sxs-lookup"><span data-stu-id="4e77a-154">$5,718,327.17</span></span>|  
|<span data-ttu-id="4e77a-155">**CY 2008**</span><span class="sxs-lookup"><span data-stu-id="4e77a-155">**CY 2008**</span></span>|<span data-ttu-id="4e77a-156">$9,770,899.74</span><span class="sxs-lookup"><span data-stu-id="4e77a-156">$9,770,899.74</span></span>|<span data-ttu-id="4e77a-157">$5,721,205.24</span><span class="sxs-lookup"><span data-stu-id="4e77a-157">$5,721,205.24</span></span>|  
|<span data-ttu-id="4e77a-158">**Year Difference**</span><span class="sxs-lookup"><span data-stu-id="4e77a-158">**Year Difference**</span></span>|<span data-ttu-id="4e77a-159">($20,160.56)</span><span class="sxs-lookup"><span data-stu-id="4e77a-159">($20,160.56)</span></span>|<span data-ttu-id="4e77a-160">$2,878.06</span><span class="sxs-lookup"><span data-stu-id="4e77a-160">$2,878.06</span></span>|  
  
### <a name="query-2-percentage-of-income-after-expenses"></a><span data-ttu-id="4e77a-161">クエリ 2-経費後の収益の割合</span><span class="sxs-lookup"><span data-stu-id="4e77a-161">Query 2-Percentage of Income after Expenses</span></span>  
 <span data-ttu-id="4e77a-162">2 番目のクエリとして、年ごとの経費差し引き後の収益のパーセンテージを計算するために、次の MDX クエリを使用します。</span><span class="sxs-lookup"><span data-stu-id="4e77a-162">For the second query, calculate the percentage of income after expenses for each year using the following MDX query:</span></span>  
  
```  
WITH   
MEMBER  
[Measures].[Profit Margin] AS   
([Measures].[Internet Sales Amount] - [Measures].[Internet Total Product Cost] ) / [Measures].[Internet Sales Amount] ,  
FORMAT_STRING="Percent"  
SELECT   
{[Measures].[Internet Sales Amount], [Measures].[Internet Total Product Cost], [Measures].[Profit Margin] }  
ON COLUMNS ,  
{ [Date].[Calendar].[Calendar Year].&[2007], [Date].[Calendar].[Calendar Year].&[2008] }  
ON ROWS  
FROM [Adventure Works]  
```  
  
 <span data-ttu-id="4e77a-163">前のクエリと同様、この MDX クエリでも計算されるメンバーは `Profit Margin`の 1 つだけであるため、解決順序の複雑さはありません。</span><span class="sxs-lookup"><span data-stu-id="4e77a-163">This MDX query, like the previous one, has only a single calculated member, `Profit Margin`, and therefore does not have any solve order complications.</span></span>  
  
 <span data-ttu-id="4e77a-164">この MDX クエリは、次の表のようなわずかに異なる結果セットを作成します。</span><span class="sxs-lookup"><span data-stu-id="4e77a-164">This MDX query produces a slightly different result set, similar to the following table.</span></span>  
  
||<span data-ttu-id="4e77a-165">Internet Sales Amount</span><span class="sxs-lookup"><span data-stu-id="4e77a-165">Internet Sales Amount</span></span>|<span data-ttu-id="4e77a-166">Internet Total Product Cost</span><span class="sxs-lookup"><span data-stu-id="4e77a-166">Internet Total Product Cost</span></span>|<span data-ttu-id="4e77a-167">利益率</span><span class="sxs-lookup"><span data-stu-id="4e77a-167">Profit Margin</span></span>|  
|-|---------------------------|---------------------------------|-------------------|  
|<span data-ttu-id="4e77a-168">**CY 2007**</span><span class="sxs-lookup"><span data-stu-id="4e77a-168">**CY 2007**</span></span>|<span data-ttu-id="4e77a-169">$9,791,060.30</span><span class="sxs-lookup"><span data-stu-id="4e77a-169">$9,791,060.30</span></span>|<span data-ttu-id="4e77a-170">$5,718,327.17</span><span class="sxs-lookup"><span data-stu-id="4e77a-170">$5,718,327.17</span></span>|<span data-ttu-id="4e77a-171">41.60%</span><span class="sxs-lookup"><span data-stu-id="4e77a-171">41.60%</span></span>|  
|<span data-ttu-id="4e77a-172">**CY 2008**</span><span class="sxs-lookup"><span data-stu-id="4e77a-172">**CY 2008**</span></span>|<span data-ttu-id="4e77a-173">$9,770,899.74</span><span class="sxs-lookup"><span data-stu-id="4e77a-173">$9,770,899.74</span></span>|<span data-ttu-id="4e77a-174">$5,721,205.24</span><span class="sxs-lookup"><span data-stu-id="4e77a-174">$5,721,205.24</span></span>|<span data-ttu-id="4e77a-175">41.45%</span><span class="sxs-lookup"><span data-stu-id="4e77a-175">41.45%</span></span>|  
  
 <span data-ttu-id="4e77a-176">1 番目のクエリと 2 番目のクエリの結果セットの違いは、計算されるメンバーの配置位置の違いによるものです。</span><span class="sxs-lookup"><span data-stu-id="4e77a-176">The difference in result sets between the first query and the second query comes from the difference in placement of the calculated member.</span></span> <span data-ttu-id="4e77a-177">1 番目のクエリでは、計算されるメンバーは ROWS 軸の一部ですが、2 番目のクエリの場合は COLUMNS 軸の一部になっています。</span><span class="sxs-lookup"><span data-stu-id="4e77a-177">In the first query, the calculated member is part of the ROWS axis, not the COLUMNS axis shown in the second query.</span></span> <span data-ttu-id="4e77a-178">次の例で、2 つの計算されるメンバーを 1 つの MDX クエリで組み合わせて使用するときに、この配置位置の違いが重要になります。</span><span class="sxs-lookup"><span data-stu-id="4e77a-178">This difference in placement becomes important in the next query, which combines the two calculated members in a single MDX query.</span></span>  
  
### <a name="query-3-combined-year-difference-and-net-income-calculations"></a><span data-ttu-id="4e77a-179">クエリ 3-年の差と純利益の計算の組み合わせ</span><span class="sxs-lookup"><span data-stu-id="4e77a-179">Query 3-Combined Year Difference and Net Income Calculations</span></span>  
 <span data-ttu-id="4e77a-180">最後のクエリでは、前の 2 つの例を 1 つの MDX クエリに結合します。このとき、列と行の両方で計算を行うため、解決順序が重要になります。</span><span class="sxs-lookup"><span data-stu-id="4e77a-180">In this final query combining both of the previous examples into a single MDX query, solve order becomes important because of the calculations on both columns and rows.</span></span> <span data-ttu-id="4e77a-181">計算が正しい順序で確実に行われるように、`SOLVE_ORDER` キーワードを使用して計算の行われる順序を定義します。</span><span class="sxs-lookup"><span data-stu-id="4e77a-181">To make sure that the calculations occur in the correct sequence, define the sequence in which the calculations occur by using the `SOLVE_ORDER` keyword.</span></span>  
  
 <span data-ttu-id="4e77a-182">`SOLVE_ORDER` キーワードは、MDX クエリまたは `CREATE MEMBER` コマンド内の計算されるメンバーの解決順序を指定します。</span><span class="sxs-lookup"><span data-stu-id="4e77a-182">The `SOLVE_ORDER` keyword specifies the solve order of calculated members in an MDX query or a `CREATE MEMBER` command.</span></span> <span data-ttu-id="4e77a-183">`SOLVE_ORDER` キーワードで使用される整数値は相対値であり、0 で始まる必要はありません。また、連続値である必要もありません。</span><span class="sxs-lookup"><span data-stu-id="4e77a-183">The integer values used with the `SOLVE_ORDER` keyword are relative, do not need to start at zero, and do not need to be consecutive.</span></span> <span data-ttu-id="4e77a-184">この値は、より高い値を持つメンバーを計算して得られる値に基づいてそのメンバーを計算するように MDX に指示するだけです。</span><span class="sxs-lookup"><span data-stu-id="4e77a-184">The value simply tells MDX to calculate a member based on values derived from calculating members with a higher value.</span></span> <span data-ttu-id="4e77a-185">計算されるメンバーの定義に `SOLVE_ORDER` キーワードが含まれていない場合、その計算されるメンバーの既定値は 0 です。</span><span class="sxs-lookup"><span data-stu-id="4e77a-185">If a calculated member is defined without the `SOLVE_ORDER` keyword, the default value of that calculated member is zero.</span></span>  
  
 <span data-ttu-id="4e77a-186">たとえば、最初の 2 つの例のクエリで使用されている計算を結合すると、計算対象となる 2 つのメンバーである `Year Difference` と `Profit Margin`は、MDX クエリの例の結果データセット内にある 1 つのセルで交差します。</span><span class="sxs-lookup"><span data-stu-id="4e77a-186">For example, if you combine the calculations used in the first two example queries, the two calculated members, `Year Difference` and `Profit Margin`, intersect at a single cell in the result dataset of the MDX query example.</span></span> <span data-ttu-id="4e77a-187">[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] がこのセルをどのように評価するかを決定する唯一の方法は、解決順序を指定することです。</span><span class="sxs-lookup"><span data-stu-id="4e77a-187">The only way to determine how [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] will evaluate this cell is by the solve order.</span></span> <span data-ttu-id="4e77a-188">このセルを作成するために使用する数式は、2 つの計算されるメンバーの解決順序に応じて、異なる結果を作成します。</span><span class="sxs-lookup"><span data-stu-id="4e77a-188">The formulas that are used to construct this cell will produce different results depending upon the solve order of the two calculated members.</span></span>  
  
 <span data-ttu-id="4e77a-189">まず、最初の 2 つのクエリで使用されている計算を次の MDX クエリのように結合してみます。</span><span class="sxs-lookup"><span data-stu-id="4e77a-189">First, try combining the calculations used in the first two queries in the following MDX query:</span></span>  
  
```  
WITH   
MEMBER  
[Date].[Calendar].[Year Difference] AS ([Date].[Calendar].[Calendar Year].&[2008] - [Date].[Calendar].[Calendar Year].&[2007] ) ,  
SOLVE_ORDER = 1  
MEMBER  
[Measures].[Profit Margin] AS   
( [Measures].[Internet Sales Amount] - [Measures].[Internet Total Product Cost] ) / [Measures].[Internet Sales Amount] ,  
FORMAT_STRING="Percent" ,  
SOLVE_ORDER = 2  
SELECT   
{[Measures].[Internet Sales Amount], [Measures].[Internet Total Product Cost], [Measures].[Profit Margin] }  
ON COLUMNS ,  
{ [Date].[Calendar].[Calendar Year].&[2007], [Date].[Calendar].[Calendar Year].&[2008], [Date].[Year Difference] }  
ON ROWS  
FROM [Adventure Works]  
```  
  
 <span data-ttu-id="4e77a-190">この結合された MDX クエリの例では、 `Profit Margin` が最も高い解決順序を持つため、2 つの式が相互作用するときに優先されます。</span><span class="sxs-lookup"><span data-stu-id="4e77a-190">In this combined MDX query example, `Profit Margin` has the highest solve order, so it takes precedence when the two expressions interact.</span></span> [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] <span data-ttu-id="4e77a-191">は、問題のセルを `Profit Margin` の数式を使用して評価します。</span><span class="sxs-lookup"><span data-stu-id="4e77a-191">evaluates the cell in question by using the `Profit Margin` formula.</span></span> <span data-ttu-id="4e77a-192">この入れ子にされた計算は、次の表に示すような結果を作成します。</span><span class="sxs-lookup"><span data-stu-id="4e77a-192">The results of this nested calculation, as shown in the following table.</span></span>  
  
||<span data-ttu-id="4e77a-193">Internet Sales Amount</span><span class="sxs-lookup"><span data-stu-id="4e77a-193">Internet Sales Amount</span></span>|<span data-ttu-id="4e77a-194">Internet Total Product Cost</span><span class="sxs-lookup"><span data-stu-id="4e77a-194">Internet Total Product Cost</span></span>|<span data-ttu-id="4e77a-195">利益率</span><span class="sxs-lookup"><span data-stu-id="4e77a-195">Profit Margin</span></span>|  
|-|---------------------------|---------------------------------|-------------------|  
|<span data-ttu-id="4e77a-196">**CY 2007**</span><span class="sxs-lookup"><span data-stu-id="4e77a-196">**CY 2007**</span></span>|<span data-ttu-id="4e77a-197">$9,791,060.30</span><span class="sxs-lookup"><span data-stu-id="4e77a-197">$9,791,060.30</span></span>|<span data-ttu-id="4e77a-198">$5,718,327.17</span><span class="sxs-lookup"><span data-stu-id="4e77a-198">$5,718,327.17</span></span>|<span data-ttu-id="4e77a-199">41.60%</span><span class="sxs-lookup"><span data-stu-id="4e77a-199">41.60%</span></span>|  
|<span data-ttu-id="4e77a-200">**CY 2008**</span><span class="sxs-lookup"><span data-stu-id="4e77a-200">**CY 2008**</span></span>|<span data-ttu-id="4e77a-201">$9,770,899.74</span><span class="sxs-lookup"><span data-stu-id="4e77a-201">$9,770,899.74</span></span>|<span data-ttu-id="4e77a-202">$5,721,205.24</span><span class="sxs-lookup"><span data-stu-id="4e77a-202">$5,721,205.24</span></span>|<span data-ttu-id="4e77a-203">41.45%</span><span class="sxs-lookup"><span data-stu-id="4e77a-203">41.45%</span></span>|  
|<span data-ttu-id="4e77a-204">**Year Difference**</span><span class="sxs-lookup"><span data-stu-id="4e77a-204">**Year Difference**</span></span>|<span data-ttu-id="4e77a-205">($20,160.56)</span><span class="sxs-lookup"><span data-stu-id="4e77a-205">($20,160.56)</span></span>|<span data-ttu-id="4e77a-206">$2,878.06</span><span class="sxs-lookup"><span data-stu-id="4e77a-206">$2,878.06</span></span>|<span data-ttu-id="4e77a-207">114.28%</span><span class="sxs-lookup"><span data-stu-id="4e77a-207">114.28%</span></span>|  
  
 <span data-ttu-id="4e77a-208">共有されるセルの結果は、 `Profit Margin`の数式に基づいています。</span><span class="sxs-lookup"><span data-stu-id="4e77a-208">The result in the shared cell is based on the formula for `Profit Margin`.</span></span> <span data-ttu-id="4e77a-209">つまり、 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] は共有されるセルの結果を `Year Difference` のデータを使用して計算し、次の数式を作成します。結果はわかりやすくするために丸めてあります。</span><span class="sxs-lookup"><span data-stu-id="4e77a-209">That is, [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] calculates the result in the shared cell with the `Year Difference` data, producing the following formula (the result is rounded for clarity):</span></span>  
  
```  
((9,770,899.74 - 9,791,060.30) - (5,721,205.24 - 5,718,327.17)) / (9,770,899.74 - 9,791,060.30) = 1.14275744   
```  
  
 <span data-ttu-id="4e77a-210">or</span><span class="sxs-lookup"><span data-stu-id="4e77a-210">or</span></span>  
  
```  
(23,038.63) / (20,160.56) = 114.28%  
```  
  
 <span data-ttu-id="4e77a-211">これは明らかに正しくありません。</span><span class="sxs-lookup"><span data-stu-id="4e77a-211">This is clearly incorrect.</span></span> <span data-ttu-id="4e77a-212">しかし、MDX クエリ内の計算されるメンバーの解決順序を入れ替えると、 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] は共有されるセルの結果を異なる方法で計算します。</span><span class="sxs-lookup"><span data-stu-id="4e77a-212">However, [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] calculates the result in the shared cell differently if you switch the solve orders for the calculated members in the MDX query.</span></span> <span data-ttu-id="4e77a-213">次の結合された MDX クエリでは、計算されるメンバーの解決順序を逆にしています。</span><span class="sxs-lookup"><span data-stu-id="4e77a-213">The following combined MDX query reverses the solve order for the calculated members:</span></span>  
  
```  
WITH   
MEMBER  
[Date].[Calendar].[Year Difference] AS ([Date].[Calendar].[Calendar Year].&[2008] - [Date].[Calendar].[Calendar Year].&[2007] ) ,  
SOLVE_ORDER = 2  
MEMBER  
[Measures].[Profit Margin] AS   
( [Measures].[Internet Sales Amount] - [Measures].[Internet Total Product Cost] ) / [Measures].[Internet Sales Amount] ,  
FORMAT_STRING="Percent" ,  
SOLVE_ORDER = 1  
SELECT   
{[Measures].[Internet Sales Amount], [Measures].[Internet Total Product Cost], [Measures].[Profit Margin] }  
ON COLUMNS ,  
{ [Date].[Calendar].[Calendar Year].&[2007], [Date].[Calendar].[Calendar Year].&[2008], [Date].[Year Difference] }  
ON ROWS  
FROM [Adventure Works]  
```  
  
 <span data-ttu-id="4e77a-214">計算されるメンバーの順序が入れ替わったため、 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] は `Year Difference` の数式を使用してセルを評価します。結果は次の表のようになります。</span><span class="sxs-lookup"><span data-stu-id="4e77a-214">As the order of the calculated members has been switched, [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] uses the `Year Difference` formula to evaluate the cell, as shown in the following table.</span></span>  
  
||<span data-ttu-id="4e77a-215">Internet Sales Amount</span><span class="sxs-lookup"><span data-stu-id="4e77a-215">Internet Sales Amount</span></span>|<span data-ttu-id="4e77a-216">Internet Total Product Cost</span><span class="sxs-lookup"><span data-stu-id="4e77a-216">Internet Total Product Cost</span></span>|<span data-ttu-id="4e77a-217">利益率</span><span class="sxs-lookup"><span data-stu-id="4e77a-217">Profit Margin</span></span>|  
|-|---------------------------|---------------------------------|-------------------|  
|<span data-ttu-id="4e77a-218">**CY 2007**</span><span class="sxs-lookup"><span data-stu-id="4e77a-218">**CY 2007**</span></span>|<span data-ttu-id="4e77a-219">$9,791,060.30</span><span class="sxs-lookup"><span data-stu-id="4e77a-219">$9,791,060.30</span></span>|<span data-ttu-id="4e77a-220">$5,718,327.17</span><span class="sxs-lookup"><span data-stu-id="4e77a-220">$5,718,327.17</span></span>|<span data-ttu-id="4e77a-221">41.60%</span><span class="sxs-lookup"><span data-stu-id="4e77a-221">41.60%</span></span>|  
|<span data-ttu-id="4e77a-222">**CY 2008**</span><span class="sxs-lookup"><span data-stu-id="4e77a-222">**CY 2008**</span></span>|<span data-ttu-id="4e77a-223">$9,770,899.74</span><span class="sxs-lookup"><span data-stu-id="4e77a-223">$9,770,899.74</span></span>|<span data-ttu-id="4e77a-224">$5,721,205.24</span><span class="sxs-lookup"><span data-stu-id="4e77a-224">$5,721,205.24</span></span>|<span data-ttu-id="4e77a-225">41.45%</span><span class="sxs-lookup"><span data-stu-id="4e77a-225">41.45%</span></span>|  
|<span data-ttu-id="4e77a-226">**Year Difference**</span><span class="sxs-lookup"><span data-stu-id="4e77a-226">**Year Difference**</span></span>|<span data-ttu-id="4e77a-227">($20,160.56)</span><span class="sxs-lookup"><span data-stu-id="4e77a-227">($20,160.56)</span></span>|<span data-ttu-id="4e77a-228">$2,878.06</span><span class="sxs-lookup"><span data-stu-id="4e77a-228">$2,878.06</span></span>|<span data-ttu-id="4e77a-229">(0.15%)</span><span class="sxs-lookup"><span data-stu-id="4e77a-229">(0.15%)</span></span>|  
  
 <span data-ttu-id="4e77a-230">このクエリは `Year Difference` の数式を使用し、 `Profit Margin` のデータをその数式に使用するため、共有されるセルの数式は次の計算のようになります。</span><span class="sxs-lookup"><span data-stu-id="4e77a-230">Because this query uses the `Year Difference` formula with the `Profit Margin` data, the formula for the shared cell resembles the following calculation:</span></span>  
  
```  
(($9,770,899.74 - 5,721,205.24) / $9,770,899.74) - ((9,791,060.30 - 5,718,327.17) / 9,791,060.30) = -0.15   
```  
  
 <span data-ttu-id="4e77a-231">または</span><span class="sxs-lookup"><span data-stu-id="4e77a-231">Or</span></span>  
  
```  
0.4145 - 0.4160= -0.15  
```  
  
## <a name="additional-considerations"></a><span data-ttu-id="4e77a-232">その他の考慮事項</span><span class="sxs-lookup"><span data-stu-id="4e77a-232">Additional Considerations</span></span>  
 <span data-ttu-id="4e77a-233">解決順序の問題は、計算されるメンバー、カスタム ロールアップ式、または計算されるセルの関係するディメンションが多数あるキューブの場合は特に、非常に複雑になります。</span><span class="sxs-lookup"><span data-stu-id="4e77a-233">Solve order can be a very complex issue to deal with, especially in cubes with a high number of dimensions involving calculated member, custom rollup formulas, or calculated cells.</span></span> <span data-ttu-id="4e77a-234">[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] が MDX クエリを評価するとき、 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] は、MDX クエリで指定されているキューブのディメンションも含め、特定のパスに関係するものすべての解決順序の値を考慮します。</span><span class="sxs-lookup"><span data-stu-id="4e77a-234">When [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] evaluates an MDX query, [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] takes into account the solve order values for everything involved within a given pass, including the dimensions of the cube specified in the MDX query.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e77a-235">参照</span><span class="sxs-lookup"><span data-stu-id="4e77a-235">See Also</span></span>  
 <span data-ttu-id="4e77a-236">[計算 Ationcurrentpass &#40;MDX&#41;](/sql/mdx/calculationcurrentpass-mdx) </span><span class="sxs-lookup"><span data-stu-id="4e77a-236">[CalculationCurrentPass &#40;MDX&#41;](/sql/mdx/calculationcurrentpass-mdx) </span></span>  
 <span data-ttu-id="4e77a-237">[MDX&#41;&#40;計算 Ationpass 値](/sql/mdx/calculationpassvalue-mdx) </span><span class="sxs-lookup"><span data-stu-id="4e77a-237">[CalculationPassValue &#40;MDX&#41;](/sql/mdx/calculationpassvalue-mdx) </span></span>  
 <span data-ttu-id="4e77a-238">[CREATE MEMBER ステートメント &#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-member) </span><span class="sxs-lookup"><span data-stu-id="4e77a-238">[CREATE MEMBER Statement &#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-member) </span></span>  
 [<span data-ttu-id="4e77a-239">データの操作 (MDX)</span><span class="sxs-lookup"><span data-stu-id="4e77a-239">Manipulating Data &#40;MDX&#41;</span></span>](mdx-data-manipulation-manipulating-data.md)  
  
