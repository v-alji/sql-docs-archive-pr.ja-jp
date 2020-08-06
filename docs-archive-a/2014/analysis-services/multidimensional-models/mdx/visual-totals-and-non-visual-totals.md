---
title: ビジュアルの合計と非表示の合計 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: ea9d02f2-a668-4547-ade5-e3d077a2e1bd
author: minewiskan
ms.author: owend
ms.openlocfilehash: ddff047be6a819d05276848cbeb430fb8e4c9c2f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736984"
---
# <a name="visual-totals-and-non-visual-totals"></a><span data-ttu-id="66ceb-102">表示部分の合計と非表示部分の合計</span><span class="sxs-lookup"><span data-stu-id="66ceb-102">Visual Totals and Non Visual Totals</span></span>
  <span data-ttu-id="66ceb-103">表示部分の合計とは、列または行の最後に表示される合計で、列または行内に表示されるすべてのアイテムを加算したものです。</span><span class="sxs-lookup"><span data-stu-id="66ceb-103">Visual Totals are totals at the end of a column or row that add up all of the items visible in the column or row.</span></span> <span data-ttu-id="66ceb-104">これは、ほとんどのテーブルが表示されるときの既定の動作です。</span><span class="sxs-lookup"><span data-stu-id="66ceb-104">This is the default behavior for most tables when displayed.</span></span> <span data-ttu-id="66ceb-105">ただし、非表示の行を含む行全体の合計を維持しながら、テーブル内の特定の列のみを表示する場合もあります。</span><span class="sxs-lookup"><span data-stu-id="66ceb-105">However, there are times when the user wants to display only certain columns in a table but keep the totals for the entire row, including those that are not displayed.</span></span> <span data-ttu-id="66ceb-106">これらは、合計が表示部分と非表示部分の両方の値から取得されることから `Non Visual Totals` と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="66ceb-106">These are called `Non Visual Totals`, because the total comes from both the visible and non-visible values.</span></span>  
  
 <span data-ttu-id="66ceb-107">次のシナリオは、非表示部分の合計の動作を示します。</span><span class="sxs-lookup"><span data-stu-id="66ceb-107">The following scenario demonstrates the behavior of Non Visual totals.</span></span> <span data-ttu-id="66ceb-108">最初のステップで表示部分の合計の既定の動作を示します。</span><span class="sxs-lookup"><span data-stu-id="66ceb-108">The first step shows the default behavior of Visual Totals.</span></span>  
  
 <span data-ttu-id="66ceb-109">次の例では、製品カテゴリが列、再販業者の業種が行であるテーブルから [Reseller Sales Amount] の数値を取得するための [Adventure Works] のクエリを示します。</span><span class="sxs-lookup"><span data-stu-id="66ceb-109">The following example is a query of [Adventure Works] to obtain [Reseller Sales Amount] figures in a table where the product categories are the columns and the reseller business types are the rows.</span></span> <span data-ttu-id="66ceb-110">次の SELECT ステートメントが発行されると、製品と再販業者の両方について合計が示されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="66ceb-110">Note that totals are given for both products and resellers when the following SELECT statement is issued:</span></span>  
  
 `select [Category].members on 0,`  
  
 `[Business Type].members on 1`  
  
 `from [Adventure Works]`  
  
 `where [Measures].[Reseller Sales Amount]`  
  
 <span data-ttu-id="66ceb-111">結果は、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="66ceb-111">Produces the following results:</span></span>  
  
|||||||  
|-|-|-|-|-|-|  
||<span data-ttu-id="66ceb-112">**すべての製品**</span><span class="sxs-lookup"><span data-stu-id="66ceb-112">**All Products**</span></span>|<span data-ttu-id="66ceb-113">**アクセサリ**</span><span class="sxs-lookup"><span data-stu-id="66ceb-113">**Accessories**</span></span>|<span data-ttu-id="66ceb-114">**バイク**</span><span class="sxs-lookup"><span data-stu-id="66ceb-114">**Bikes**</span></span>|<span data-ttu-id="66ceb-115">**衣服**</span><span class="sxs-lookup"><span data-stu-id="66ceb-115">**Clothing**</span></span>|<span data-ttu-id="66ceb-116">**コンポーネント**</span><span class="sxs-lookup"><span data-stu-id="66ceb-116">**Components**</span></span>|  
|<span data-ttu-id="66ceb-117">**All Resellers**</span><span class="sxs-lookup"><span data-stu-id="66ceb-117">**All Resellers**</span></span>|<span data-ttu-id="66ceb-118">**$80,450,596.98**</span><span class="sxs-lookup"><span data-stu-id="66ceb-118">**$80,450,596.98**</span></span>|<span data-ttu-id="66ceb-119">**$571,297.93**</span><span class="sxs-lookup"><span data-stu-id="66ceb-119">**$571,297.93**</span></span>|<span data-ttu-id="66ceb-120">**$66,302,381.56**</span><span class="sxs-lookup"><span data-stu-id="66ceb-120">**$66,302,381.56**</span></span>|<span data-ttu-id="66ceb-121">**$1,777,840.84**</span><span class="sxs-lookup"><span data-stu-id="66ceb-121">**$1,777,840.84**</span></span>|<span data-ttu-id="66ceb-122">**$11,799,076.66**</span><span class="sxs-lookup"><span data-stu-id="66ceb-122">**$11,799,076.66**</span></span>|  
|<span data-ttu-id="66ceb-123">**Specialty Bike Shop**</span><span class="sxs-lookup"><span data-stu-id="66ceb-123">**Specialty Bike Shop**</span></span>|<span data-ttu-id="66ceb-124">**$6,756,166.18**</span><span class="sxs-lookup"><span data-stu-id="66ceb-124">**$6,756,166.18**</span></span>|<span data-ttu-id="66ceb-125">**$65,125.48**</span><span class="sxs-lookup"><span data-stu-id="66ceb-125">**$65,125.48**</span></span>|<span data-ttu-id="66ceb-126">**$6,080,117.73**</span><span class="sxs-lookup"><span data-stu-id="66ceb-126">**$6,080,117.73**</span></span>|<span data-ttu-id="66ceb-127">**$252,933.91**</span><span class="sxs-lookup"><span data-stu-id="66ceb-127">**$252,933.91**</span></span>|<span data-ttu-id="66ceb-128">**$357,989.07**</span><span class="sxs-lookup"><span data-stu-id="66ceb-128">**$357,989.07**</span></span>|  
|<span data-ttu-id="66ceb-129">**Value Added Reseller**</span><span class="sxs-lookup"><span data-stu-id="66ceb-129">**Value Added Reseller**</span></span>|<span data-ttu-id="66ceb-130">**$34,967,517.33**</span><span class="sxs-lookup"><span data-stu-id="66ceb-130">**$34,967,517.33**</span></span>|<span data-ttu-id="66ceb-131">**$175,002.81**</span><span class="sxs-lookup"><span data-stu-id="66ceb-131">**$175,002.81**</span></span>|<span data-ttu-id="66ceb-132">**$30,892,354.33**</span><span class="sxs-lookup"><span data-stu-id="66ceb-132">**$30,892,354.33**</span></span>|<span data-ttu-id="66ceb-133">**$592,385.71**</span><span class="sxs-lookup"><span data-stu-id="66ceb-133">**$592,385.71**</span></span>|<span data-ttu-id="66ceb-134">**$3,307,774.48**</span><span class="sxs-lookup"><span data-stu-id="66ceb-134">**$3,307,774.48**</span></span>|  
|<span data-ttu-id="66ceb-135">**ウェアハウス**</span><span class="sxs-lookup"><span data-stu-id="66ceb-135">**Warehouse**</span></span>|<span data-ttu-id="66ceb-136">**$38,726,913.48**</span><span class="sxs-lookup"><span data-stu-id="66ceb-136">**$38,726,913.48**</span></span>|<span data-ttu-id="66ceb-137">**$331,169.64**</span><span class="sxs-lookup"><span data-stu-id="66ceb-137">**$331,169.64**</span></span>|<span data-ttu-id="66ceb-138">**$29,329,909.50**</span><span class="sxs-lookup"><span data-stu-id="66ceb-138">**$29,329,909.50**</span></span>|<span data-ttu-id="66ceb-139">**$932,521.23**</span><span class="sxs-lookup"><span data-stu-id="66ceb-139">**$932,521.23**</span></span>|<span data-ttu-id="66ceb-140">**$8,133,313.11**</span><span class="sxs-lookup"><span data-stu-id="66ceb-140">**$8,133,313.11**</span></span>|  
  
## <a name="non-visual-on-rows-and-columns"></a><span data-ttu-id="66ceb-141">行および列の非表示部分</span><span class="sxs-lookup"><span data-stu-id="66ceb-141">Non-Visual on rows and columns</span></span>  
 <span data-ttu-id="66ceb-142">Accessories 製品と Clothing 製品、および Value Added Reseller 再販業者と Warehouse 再販業者のみのデータを含むテーブルを生成する場合、全体的な合計も維持するには、NON VISUAL を使用して次のように記述できます。</span><span class="sxs-lookup"><span data-stu-id="66ceb-142">To produce a table with data only for the Accessories and Clothing products, the Value Added Reseller and Warehouse resellers, yet keeping the overall totals could be written as follows using NON VISUAL:</span></span>  
  
 `select [Category].members on 0,`  
  
 `[Business Type].members on 1`  
  
 `from NON VISUAL (Select {[Category].Accessories, [Category].Clothing} on 0,`  
  
 `{[Business Type].[Value Added Reseller], [Business Type].[Warehouse]} on 1`  
  
 `from [Adventure Works])`  
  
 `where [Measures].[Reseller Sales Amount]`  
  
 <span data-ttu-id="66ceb-143">結果は、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="66ceb-143">Produces the following results:</span></span>  
  
|||||  
|-|-|-|-|  
||<span data-ttu-id="66ceb-144">**すべての製品**</span><span class="sxs-lookup"><span data-stu-id="66ceb-144">**All Products**</span></span>|<span data-ttu-id="66ceb-145">**アクセサリ**</span><span class="sxs-lookup"><span data-stu-id="66ceb-145">**Accessories**</span></span>|<span data-ttu-id="66ceb-146">**衣服**</span><span class="sxs-lookup"><span data-stu-id="66ceb-146">**Clothing**</span></span>|  
|<span data-ttu-id="66ceb-147">**All Resellers**</span><span class="sxs-lookup"><span data-stu-id="66ceb-147">**All Resellers**</span></span>|<span data-ttu-id="66ceb-148">**$80,450,596.98**</span><span class="sxs-lookup"><span data-stu-id="66ceb-148">**$80,450,596.98**</span></span>|<span data-ttu-id="66ceb-149">**$571,297.93**</span><span class="sxs-lookup"><span data-stu-id="66ceb-149">**$571,297.93**</span></span>|<span data-ttu-id="66ceb-150">**$1,777,840.84**</span><span class="sxs-lookup"><span data-stu-id="66ceb-150">**$1,777,840.84**</span></span>|  
|<span data-ttu-id="66ceb-151">**Value Added Reseller**</span><span class="sxs-lookup"><span data-stu-id="66ceb-151">**Value Added Reseller**</span></span>|<span data-ttu-id="66ceb-152">**$34,967,517.33**</span><span class="sxs-lookup"><span data-stu-id="66ceb-152">**$34,967,517.33**</span></span>|<span data-ttu-id="66ceb-153">**$175,002.81**</span><span class="sxs-lookup"><span data-stu-id="66ceb-153">**$175,002.81**</span></span>|<span data-ttu-id="66ceb-154">**$592,385.71**</span><span class="sxs-lookup"><span data-stu-id="66ceb-154">**$592,385.71**</span></span>|  
|<span data-ttu-id="66ceb-155">**ウェアハウス**</span><span class="sxs-lookup"><span data-stu-id="66ceb-155">**Warehouse**</span></span>|<span data-ttu-id="66ceb-156">**$38,726,913.48**</span><span class="sxs-lookup"><span data-stu-id="66ceb-156">**$38,726,913.48**</span></span>|<span data-ttu-id="66ceb-157">**$331,169.64**</span><span class="sxs-lookup"><span data-stu-id="66ceb-157">**$331,169.64**</span></span>|<span data-ttu-id="66ceb-158">**$932,521.23**</span><span class="sxs-lookup"><span data-stu-id="66ceb-158">**$932,521.23**</span></span>|  
  
## <a name="non-visual-on-rows"></a><span data-ttu-id="66ceb-159">行の非表示部分</span><span class="sxs-lookup"><span data-stu-id="66ceb-159">Non-Visual on rows</span></span>  
 <span data-ttu-id="66ceb-160">列の表示部分の合計を算出するが、行の合計についてはすべての [Category] の実際の合計を示すテーブルを生成するには、次のクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="66ceb-160">To produce a table that visually totals the columns but for row totals brings the true total of all [Category], the following query should be issued:</span></span>  
  
 `select [Category].members on 0,`  
  
 `[Business Type].members on 1`  
  
 `from NON VISUAL (Select {[Category].Accessories, [Category].Clothing} on 0`  
  
 `from ( Select {[Business Type].[Value Added Reseller], [Business Type].[Warehouse]} on 0`  
  
 `from [Adventure Works])`  
  
 `)`  
  
 `where [Measures].[Reseller Sales Amount]`  
  
 <span data-ttu-id="66ceb-161">NON VISUAL が [Category] のみに適用されていることに注目してください。</span><span class="sxs-lookup"><span data-stu-id="66ceb-161">Note how NON VISUAL is only applied to [Category].</span></span>  
  
 <span data-ttu-id="66ceb-162">上記のクエリの結果は、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="66ceb-162">The above query produces the following results:</span></span>  
  
|||||  
|-|-|-|-|  
||<span data-ttu-id="66ceb-163">All Products</span><span class="sxs-lookup"><span data-stu-id="66ceb-163">All Products</span></span>|<span data-ttu-id="66ceb-164">アクセサリ</span><span class="sxs-lookup"><span data-stu-id="66ceb-164">Accessories</span></span>|<span data-ttu-id="66ceb-165">衣服</span><span class="sxs-lookup"><span data-stu-id="66ceb-165">Clothing</span></span>|  
|<span data-ttu-id="66ceb-166">All Resellers</span><span class="sxs-lookup"><span data-stu-id="66ceb-166">All Resellers</span></span>|<span data-ttu-id="66ceb-167">$73,694,430.80</span><span class="sxs-lookup"><span data-stu-id="66ceb-167">$73,694,430.80</span></span>|<span data-ttu-id="66ceb-168">$506,172.45</span><span class="sxs-lookup"><span data-stu-id="66ceb-168">$506,172.45</span></span>|<span data-ttu-id="66ceb-169">$1,524,906.93</span><span class="sxs-lookup"><span data-stu-id="66ceb-169">$1,524,906.93</span></span>|  
|<span data-ttu-id="66ceb-170">Value Added Reseller</span><span class="sxs-lookup"><span data-stu-id="66ceb-170">Value Added Reseller</span></span>|<span data-ttu-id="66ceb-171">$34,967,517.33</span><span class="sxs-lookup"><span data-stu-id="66ceb-171">$34,967,517.33</span></span>|<span data-ttu-id="66ceb-172">$175,002.81</span><span class="sxs-lookup"><span data-stu-id="66ceb-172">$175,002.81</span></span>|<span data-ttu-id="66ceb-173">$592,385.71</span><span class="sxs-lookup"><span data-stu-id="66ceb-173">$592,385.71</span></span>|  
|<span data-ttu-id="66ceb-174">Warehouse</span><span class="sxs-lookup"><span data-stu-id="66ceb-174">Warehouse</span></span>|<span data-ttu-id="66ceb-175">$38,726,913.48</span><span class="sxs-lookup"><span data-stu-id="66ceb-175">$38,726,913.48</span></span>|<span data-ttu-id="66ceb-176">$331,169.64</span><span class="sxs-lookup"><span data-stu-id="66ceb-176">$331,169.64</span></span>|<span data-ttu-id="66ceb-177">$932,521.23</span><span class="sxs-lookup"><span data-stu-id="66ceb-177">$932,521.23</span></span>|  
  
 <span data-ttu-id="66ceb-178">前の結果と比較すると、[All Resellers] 行は [Value Added Reseller] と [Warehouse] の表示値の合計を示していますが、[All Products] 列は表示されていない製品も含むすべての製品の合計額を示していることがわかります。</span><span class="sxs-lookup"><span data-stu-id="66ceb-178">When compared with the previous results, you can observe that the [All Resellers] row now adds up to the displayed values for [Value Added Reseller] and [Warehouse] but that the [All Products] column shows the total value for all products, including those not displayed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66ceb-179">参照</span><span class="sxs-lookup"><span data-stu-id="66ceb-179">See Also</span></span>  
 <span data-ttu-id="66ceb-180">[MDX &#40;Analysis Services の主な概念&#41;](../key-concepts-in-mdx-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="66ceb-180">[Key Concepts in MDX &#40;Analysis Services&#41;](../key-concepts-in-mdx-analysis-services.md) </span></span>  
 <span data-ttu-id="66ceb-181">[Autoexists](autoexists.md) </span><span class="sxs-lookup"><span data-stu-id="66ceb-181">[Autoexists](autoexists.md) </span></span>  
 <span data-ttu-id="66ceb-182">[MDX&#41;&#40;メンバー、組、およびセットの操作](working-with-members-tuples-and-sets-mdx.md) </span><span class="sxs-lookup"><span data-stu-id="66ceb-182">[Working with Members, Tuples, and Sets &#40;MDX&#41;](working-with-members-tuples-and-sets-mdx.md) </span></span>  
 <span data-ttu-id="66ceb-183">[MDX クエリの基礎 &#40;Analysis Services&#41;](mdx-query-fundamentals-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="66ceb-183">[MDX Query Fundamentals &#40;Analysis Services&#41;](mdx-query-fundamentals-analysis-services.md) </span></span>  
 <span data-ttu-id="66ceb-184">[MDX の基本的なクエリ &#40;MDX&#41;](mdx-query-the-basic-query.md) </span><span class="sxs-lookup"><span data-stu-id="66ceb-184">[The Basic MDX Query &#40;MDX&#41;](mdx-query-the-basic-query.md) </span></span>  
 <span data-ttu-id="66ceb-185">[MDX&#41;&#40;クエリ軸とスライサー軸を使用したクエリの制限](mdx-query-and-slicer-axes-restricting-the-query.md) </span><span class="sxs-lookup"><span data-stu-id="66ceb-185">[Restricting the Query with Query and Slicer Axes &#40;MDX&#41;](mdx-query-and-slicer-axes-restricting-the-query.md) </span></span>  
 [<span data-ttu-id="66ceb-186">クエリ内のキューブ コンテキストの確立 &#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="66ceb-186">Establishing Cube Context in a Query &#40;MDX&#41;</span></span>](establishing-cube-context-in-a-query-mdx.md)  
  
  
