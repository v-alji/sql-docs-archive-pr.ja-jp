---
title: Autoexists |Microsoft Docs
ms.custom: ''
ms.date: 07/17/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 56283497-624c-45b5-8a0d-036b0e331d22
author: minewiskan
ms.author: owend
ms.openlocfilehash: dd35958a364456c12d58392afe3754f6adcf97b8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642382"
---
# <a name="autoexists"></a><span data-ttu-id="79b09-102">autoexists</span><span class="sxs-lookup"><span data-stu-id="79b09-102">Autoexists</span></span>
  <span data-ttu-id="79b09-103">*autoexists* の概念を導入すると、このキューブ空間を、同じ階層から属性階層メンバーの可能なすべての組み合わせを作成した結果として存在するセルでなく、実際に存在するセルのみに限定できます。</span><span class="sxs-lookup"><span data-stu-id="79b09-103">The concept of *autoexists* limits the cube space to those cells that actually exist in the cube in contraposition to those that might exist as a result of creating all possible combinations of attribute hierarchy members from the same hierarchy.</span></span> <span data-ttu-id="79b09-104">これは、1 つの属性階層のメンバーは、同じディメンション内の別の属性階層のメンバーと共存できないためです。</span><span class="sxs-lookup"><span data-stu-id="79b09-104">This is because members of one attribute hierarchy cannot exist with members of another attribute hierarchy in the same dimension.</span></span> <span data-ttu-id="79b09-105">SELECT ステートメントに同じディメンションの属性階層を複数使用した場合、こうした属性のメンバーは、Analysis Services が属性の式を評価する際、それ以外のすべての属性の条件を満たすよう、適切に絞り込まれます。</span><span class="sxs-lookup"><span data-stu-id="79b09-105">When two or more attribute hierarchies of the same dimension are used in a SELECT statement, Analysis Services evaluates the attributes' expressions to make sure that the members of those attributes are properly confined to meet the criteria of all other attributes.</span></span>  
  
 <span data-ttu-id="79b09-106">たとえば、Geography ディメンションの属性を指定したとします。</span><span class="sxs-lookup"><span data-stu-id="79b09-106">For example, suppose you are working with attributes from the Geography dimension.</span></span> <span data-ttu-id="79b09-107">一方の式で City 属性のすべてのメンバーを返し、もう一方の式で Country 属性のメンバーを欧州内の国のみに限定した場合、結果として得られる City メンバーは、欧州の国に属する市区町村に限定されます。</span><span class="sxs-lookup"><span data-stu-id="79b09-107">If you have one expression that returns all members from the City attribute and another expression that confines members from the Country attribute to all countries in Europe, then this will result in the City members being confined to only those cities that belong to countries in Europe.</span></span> <span data-ttu-id="79b09-108">これは、Analysis Services が備えている Autoexists という特性のためです。</span><span class="sxs-lookup"><span data-stu-id="79b09-108">This is because of the autoexists characteristic of Analysis Services.</span></span> <span data-ttu-id="79b09-109">Autoexists が同じディメンションの属性にのみ適用されるのは、一方の属性式で排除されたディメンション レコードが、もう一方の属性式で含められるのを防ぐように機能するためです。</span><span class="sxs-lookup"><span data-stu-id="79b09-109">Autoexists only applies to attributes from the same dimension because it tries to prevent the dimension records excluded in one attribute expression from being included by the other attribute expressions.</span></span> <span data-ttu-id="79b09-110">ディメンション行に複数の属性式を適用した結果の共通集合と考えることもできます。</span><span class="sxs-lookup"><span data-stu-id="79b09-110">Autoexists can also be understood as the resulting intersection of the different attributes expressions over the dimension rows.</span></span>  
  
## <a name="cell-existence"></a><span data-ttu-id="79b09-111">セルの存在</span><span class="sxs-lookup"><span data-stu-id="79b09-111">Cell Existence</span></span>  
 <span data-ttu-id="79b09-112">次のセルは常に存在します。</span><span class="sxs-lookup"><span data-stu-id="79b09-112">The following cells always exist:</span></span>  
  
-   <span data-ttu-id="79b09-113">同じディメンション内の他の階層のメンバーの影響を受ける場合、各階層の (All) メンバー</span><span class="sxs-lookup"><span data-stu-id="79b09-113">The (All) member, of every hierarchy, when crossed with members of other hierarchies in the same dimension.</span></span>  
  
-   <span data-ttu-id="79b09-114">計算されない兄弟または計算されない兄弟の親または子孫の影響を受ける場合、計算されるメンバー</span><span class="sxs-lookup"><span data-stu-id="79b09-114">Calculated members when crossed with their non-calculated siblings, or with the parents or descendants of their non-calculated siblings.</span></span>  
  
## <a name="providing-non-existing-cells"></a><span data-ttu-id="79b09-115">存在しないセルの指定</span><span class="sxs-lookup"><span data-stu-id="79b09-115">Providing Non-existing cells</span></span>  
 <span data-ttu-id="79b09-116">存在しないセルは、キューブ内に存在しないセルを要求するクエリまたは計算に対する応答としてシステムによって提供されるセルです。</span><span class="sxs-lookup"><span data-stu-id="79b09-116">A non-existing cell is a cell provided by the system as a response to a query or calculation that requests a cell that does not exist in the cube.</span></span> <span data-ttu-id="79b09-117">たとえば、Geography ディメンションに属する City 属性階層と Country 属性階層、および Internet Sales Amount メジャーが含まれたキューブがあるとします。このキューブの空間には、共存できるメンバーのみが含まれます。</span><span class="sxs-lookup"><span data-stu-id="79b09-117">For example, if you have a cube that has a City attribute hierarchy and a Country attribute hierarchy that belong to the Geography dimension, and an Internet Sales Amount measure, the space of this cube only includes those members that exist with each other.</span></span> <span data-ttu-id="79b09-118">City 属性階層に都市 New York、London、Paris、Tokyo、Melbourne があり、Country 属性階層に国 United States、United Kingdom、France、Japan、Australia があるとすると、このキューブ空間に Paris と United States が交差する領域 (セル) は含まれません。</span><span class="sxs-lookup"><span data-stu-id="79b09-118">For example, if the City attribute hierarchy includes the cities New York, London, Paris, Tokyo, and Melbourne; and the Country attribute hierarchy includes the countries United States, United Kingdom, France, Japan, and Australia; then the space of the cube does not include the space (cell) at the intersection of Paris and United States.</span></span>  
  
 <span data-ttu-id="79b09-119">存在しないセルに対するクエリを実行すると、NULL が返されます。つまり、存在しないセルには計算を含めることができないので、この領域に書き込みを行う計算は定義できません。</span><span class="sxs-lookup"><span data-stu-id="79b09-119">When querying cells that do not exist, non-existing cells return nulls; that is, they cannot contain calculations and you cannot define a calculation that writes to this space.</span></span> <span data-ttu-id="79b09-120">たとえば、次のステートメントには、存在しないセルが含まれています。</span><span class="sxs-lookup"><span data-stu-id="79b09-120">For example, the following statement includes cells that do not exist.</span></span>  
  
```  
SELECT [Customer].[Gender].[Gender].Members ON COLUMNS,  
{[Customer].[Customer].[Aaron A. Allen]  
   ,[Customer].[Customer].[Abigail Clark]} ON ROWS   
FROM [Adventure Works]  
WHERE Measures.[Internet Sales Amount]  
```  
  
> [!NOTE]  
>  <span data-ttu-id="79b09-121">このクエリでは、 [Members (セット) (MDX)](/sql/mdx/members-set-mdx) 関数を使用して列軸の Gender 属性階層のメンバーのセットを取得し、それを行軸の Customer 属性階層のメンバーの限定的なセットと交差させています。</span><span class="sxs-lookup"><span data-stu-id="79b09-121">This query uses the [Members (Set) (MDX)](/sql/mdx/members-set-mdx) function to return the set of members of the Gender attribute hierarchy on the column axis, and crosses this set with the specified set of members from the Customer attribute hierarchy on the row axis.</span></span>  
  
 <span data-ttu-id="79b09-122">上記のクエリを実行すると、Aaron A. Allen と Female が交差するセルに NULL が表示されます。</span><span class="sxs-lookup"><span data-stu-id="79b09-122">When you execute the previous query, the cell at the intersection of Aaron A. Allen and Female displays a null.</span></span> <span data-ttu-id="79b09-123">同様に、Abigail Clark と Male が交差するセルに NULL が表示されます。</span><span class="sxs-lookup"><span data-stu-id="79b09-123">Similarly, the cell at the intersection of Abigail Clark and Male displays a null.</span></span> <span data-ttu-id="79b09-124">これらのセルは存在しないため値を含めることができませんが、クエリから返される結果には、存在しないセルが表示される場合があります。</span><span class="sxs-lookup"><span data-stu-id="79b09-124">These cells do not exist and cannot contain a value, but cells that do not exist can appear in the result returned by a query.</span></span>  
  
 <span data-ttu-id="79b09-125">[Crossjoin (MDX)](/sql/mdx/crossjoin-mdx) 関数を使用して同一ディメンションの異なる属性階層に属するメンバーのクロス積を取得した場合、取得される組は完全なデカルト積ではなく、autoexist によって実際に存在する組のセットのみに限定されます。</span><span class="sxs-lookup"><span data-stu-id="79b09-125">When you use the [Crossjoin (MDX)](/sql/mdx/crossjoin-mdx) function to return the cross-product of attribute hierarchy members from attribute hierarchies in the same dimension, auto-exists limits those tuples being returned to the set of tuples that actually exist, rather than returning a full Cartesian product.</span></span> <span data-ttu-id="79b09-126">たとえば、次のクエリを実行し、実行結果を確認します。</span><span class="sxs-lookup"><span data-stu-id="79b09-126">For example, run and then examine the results from the execution of the following query.</span></span>  
  
```  
SELECT CROSSJOIN  
   (  
      {[Customer].[Country].[United States]},  
         [Customer].[State-Province].Members  
  ) ON 0   
FROM [Adventure Works]  
WHERE Measures.[Internet Sales Amount]  
```  
  
> [!NOTE]  
>  <span data-ttu-id="79b09-127">このクエリでは、列軸を表す axis(0) の略記である 0 を使用して、列軸を指定しています。</span><span class="sxs-lookup"><span data-stu-id="79b09-127">Notice that 0 is used to designate the column axis, which is shorthand for axis(0) - which is the column axis.</span></span>  
  
 <span data-ttu-id="79b09-128">上のクエリを実行すると、クエリ内の各属性階層から、共存できるメンバーのセルのみが返されます。</span><span class="sxs-lookup"><span data-stu-id="79b09-128">The previous query only returns cells for members from each attribute hierarchy in the query that exist with each other.</span></span> <span data-ttu-id="79b09-129">上記のクエリは、 [Crossjoin (MDX)](/sql/mdx/crossjoin-mdx)関数の新しい \* バリアントを使用して記述することもできます。</span><span class="sxs-lookup"><span data-stu-id="79b09-129">The previous query can also be written using the new \* variant of the [Crossjoin (MDX)](/sql/mdx/crossjoin-mdx) function.</span></span>  
  
```  
SELECT   
   [Customer].[Country].[United States] *   
      [Customer].[State-Province].Members  
ON 0   
FROM [Adventure Works]  
WHERE Measures.[Internet Sales Amount]  
```  
  
 <span data-ttu-id="79b09-130">上のクエリは、次のように記述することもできます。</span><span class="sxs-lookup"><span data-stu-id="79b09-130">The previous query could also be written in the following manner:</span></span>  
  
```  
SELECT [Customer].[State-Province].Members  
ON 0   
FROM [Adventure Works]  
WHERE (Measures.[Internet Sales Amount],  
   [Customer].[Country].[United States])  
```  
  
 <span data-ttu-id="79b09-131">結果セットのメタデータが異なりますが、返されるセルの値は同一です。</span><span class="sxs-lookup"><span data-stu-id="79b09-131">The cells values returned will be identical, although the metadata in the result set will be different.</span></span> <span data-ttu-id="79b09-132">たとえば上のクエリで、Country 階層は (WHERE 句の) スライサー軸に移動されたので、結果セットに明示的には出現しません。</span><span class="sxs-lookup"><span data-stu-id="79b09-132">For example, with the previous query, the Country hierarchy was moved to the slicer axis (in the WHERE clause) and therefore does not appear explicitly in the result set.</span></span>  
  
 <span data-ttu-id="79b09-133">上記の3つのクエリはそれぞれ、の自動存在の動作の効果を示して [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] います。</span><span class="sxs-lookup"><span data-stu-id="79b09-133">Each of these three previous queries demonstrates the effect of the auto-exists behavior in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span></span>  
  
## <a name="deep-and-shallow-autoexists"></a><span data-ttu-id="79b09-134">Deep および Shallow Autoexists</span><span class="sxs-lookup"><span data-stu-id="79b09-134">Deep and Shallow Autoexists</span></span>  
 <span data-ttu-id="79b09-135">Autoexists は、式に対して深く (deep) または浅く (shallow) 適用できます。</span><span class="sxs-lookup"><span data-stu-id="79b09-135">Autoexists can be applied to the expressions as Deep or Shallow.</span></span> <span data-ttu-id="79b09-136">`Deep Autoexists` では、スライサーの式、軸の下位選択式などを適用した後、可能な限り深い場所に到達するように、すべての式が評価されます。</span><span class="sxs-lookup"><span data-stu-id="79b09-136">`Deep Autoexists` means that all expressions will be evaluated to meet the deepest possible space after applying the slicer expressions, the sub select expressions in the axis, and so on.</span></span> <span data-ttu-id="79b09-137">`Shallow Autoexists` では、現在の式より前に外部の式が評価され、その結果が現在の式に渡されます。</span><span class="sxs-lookup"><span data-stu-id="79b09-137">`Shallow Autoexists` means that external expressions are evaluated before the current expression and those results are passed to the current expression.</span></span> <span data-ttu-id="79b09-138">既定の設定は deep autoexists です。</span><span class="sxs-lookup"><span data-stu-id="79b09-138">The default setting is deep autoexists.</span></span>  
  
 <span data-ttu-id="79b09-139">以下のシナリオとサンプルでは、さまざまな種類の Autoexists について説明します。</span><span class="sxs-lookup"><span data-stu-id="79b09-139">The following scenario and samples will help to illustrate the different types of Autoexistss.</span></span> <span data-ttu-id="79b09-140">この例では 2 つのセットを 1 つは計算式として、もう 1 つは定数式として作成します。</span><span class="sxs-lookup"><span data-stu-id="79b09-140">In the following examples two sets will be created: one as a calculated expression and the other as a constant expression.</span></span>  
  
 `//Obtain the Top 10 best reseller selling products by Name`  
  
 `with member [Measures].[PCT Discount] AS '[Measures].[Discount Amount]/[Measures].[Reseller Sales Amount]', FORMAT_STRING = 'Percent'`  
  
 `set Top10SellingProducts as 'topcount([Product].[Model Name].children, 10, [Measures].[Reseller Sales Amount])'`  
  
 `set Preferred10Products as '`  
  
 `{[Product].[Model Name].&[Mountain-200],`  
  
 `[Product].[Model Name].&[Road-250],`  
  
 `[Product].[Model Name].&[Mountain-100],`  
  
 `[Product].[Model Name].&[Road-650],`  
  
 `[Product].[Model Name].&[Touring-1000],`  
  
 `[Product].[Model Name].&[Road-550-W],`  
  
 `[Product].[Model Name].&[Road-350-W],`  
  
 `[Product].[Model Name].&[HL Mountain Frame],`  
  
 `[Product].[Model Name].&[Road-150],`  
  
 `[Product].[Model Name].&[Touring-3000]`  
  
 `}'`  
  
 `select {[Measures].[Reseller Sales Amount], [Measures].[Discount Amount], [Measures].[PCT Discount]} on 0,`  
  
 `Top10SellingProducts on 1`  
  
 `from [Adventure Works]`  
  
 <span data-ttu-id="79b09-141">取得される結果セットは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="79b09-141">The obtained result set is:</span></span>  
  
|||||  
|-|-|-|-|  
||<span data-ttu-id="79b09-142">**Reseller Sales Amount**</span><span class="sxs-lookup"><span data-stu-id="79b09-142">**Reseller Sales Amount**</span></span>|<span data-ttu-id="79b09-143">**Discount Amount**</span><span class="sxs-lookup"><span data-stu-id="79b09-143">**Discount Amount**</span></span>|<span data-ttu-id="79b09-144">**PCT Discount**</span><span class="sxs-lookup"><span data-stu-id="79b09-144">**PCT Discount**</span></span>|  
|<span data-ttu-id="79b09-145">**Mountain-200**</span><span class="sxs-lookup"><span data-stu-id="79b09-145">**Mountain-200**</span></span>|<span data-ttu-id="79b09-146">**$14,356,699.36**</span><span class="sxs-lookup"><span data-stu-id="79b09-146">**$14,356,699.36**</span></span>|<span data-ttu-id="79b09-147">**$19,012.71**</span><span class="sxs-lookup"><span data-stu-id="79b09-147">**$19,012.71**</span></span>|<span data-ttu-id="79b09-148">**0.13%**</span><span class="sxs-lookup"><span data-stu-id="79b09-148">**0.13%**</span></span>|  
|<span data-ttu-id="79b09-149">**Road-250**</span><span class="sxs-lookup"><span data-stu-id="79b09-149">**Road-250**</span></span>|<span data-ttu-id="79b09-150">**$9,377,457.68**</span><span class="sxs-lookup"><span data-stu-id="79b09-150">**$9,377,457.68**</span></span>|<span data-ttu-id="79b09-151">**$4,032.47**</span><span class="sxs-lookup"><span data-stu-id="79b09-151">**$4,032.47**</span></span>|<span data-ttu-id="79b09-152">**0.04%**</span><span class="sxs-lookup"><span data-stu-id="79b09-152">**0.04%**</span></span>|  
|<span data-ttu-id="79b09-153">**Mountain-100**</span><span class="sxs-lookup"><span data-stu-id="79b09-153">**Mountain-100**</span></span>|<span data-ttu-id="79b09-154">**$8,568,958.27**</span><span class="sxs-lookup"><span data-stu-id="79b09-154">**$8,568,958.27**</span></span>|<span data-ttu-id="79b09-155">**$139,393.27**</span><span class="sxs-lookup"><span data-stu-id="79b09-155">**$139,393.27**</span></span>|<span data-ttu-id="79b09-156">**1.63%**</span><span class="sxs-lookup"><span data-stu-id="79b09-156">**1.63%**</span></span>|  
|<span data-ttu-id="79b09-157">**道路 650**</span><span class="sxs-lookup"><span data-stu-id="79b09-157">**Road-650**</span></span>|<span data-ttu-id="79b09-158">**$7,442,141.81**</span><span class="sxs-lookup"><span data-stu-id="79b09-158">**$7,442,141.81**</span></span>|<span data-ttu-id="79b09-159">**$39,698.30**</span><span class="sxs-lookup"><span data-stu-id="79b09-159">**$39,698.30**</span></span>|<span data-ttu-id="79b09-160">**0.53%**</span><span class="sxs-lookup"><span data-stu-id="79b09-160">**0.53%**</span></span>|  
|<span data-ttu-id="79b09-161">**Touring 1000**</span><span class="sxs-lookup"><span data-stu-id="79b09-161">**Touring-1000**</span></span>|<span data-ttu-id="79b09-162">**$6,723,794.29**</span><span class="sxs-lookup"><span data-stu-id="79b09-162">**$6,723,794.29**</span></span>|<span data-ttu-id="79b09-163">**$166,144.17**</span><span class="sxs-lookup"><span data-stu-id="79b09-163">**$166,144.17**</span></span>|<span data-ttu-id="79b09-164">**2.47%**</span><span class="sxs-lookup"><span data-stu-id="79b09-164">**2.47%**</span></span>|  
|<span data-ttu-id="79b09-165">**道路-w 550**</span><span class="sxs-lookup"><span data-stu-id="79b09-165">**Road-550-W**</span></span>|<span data-ttu-id="79b09-166">**$3,668,383.88**</span><span class="sxs-lookup"><span data-stu-id="79b09-166">**$3,668,383.88**</span></span>|<span data-ttu-id="79b09-167">**$1,901.97**</span><span class="sxs-lookup"><span data-stu-id="79b09-167">**$1,901.97**</span></span>|<span data-ttu-id="79b09-168">**0.05%**</span><span class="sxs-lookup"><span data-stu-id="79b09-168">**0.05%**</span></span>|  
|<span data-ttu-id="79b09-169">**Road-350-W**</span><span class="sxs-lookup"><span data-stu-id="79b09-169">**Road-350-W**</span></span>|<span data-ttu-id="79b09-170">**$3,665,932.31**</span><span class="sxs-lookup"><span data-stu-id="79b09-170">**$3,665,932.31**</span></span>|<span data-ttu-id="79b09-171">**$20,946.50**</span><span class="sxs-lookup"><span data-stu-id="79b09-171">**$20,946.50**</span></span>|<span data-ttu-id="79b09-172">**0.57%**</span><span class="sxs-lookup"><span data-stu-id="79b09-172">**0.57%**</span></span>|  
|<span data-ttu-id="79b09-173">**HL Mountain Frame**</span><span class="sxs-lookup"><span data-stu-id="79b09-173">**HL Mountain Frame**</span></span>|<span data-ttu-id="79b09-174">**$3,365,069.27**</span><span class="sxs-lookup"><span data-stu-id="79b09-174">**$3,365,069.27**</span></span>|<span data-ttu-id="79b09-175">**$174.11**</span><span class="sxs-lookup"><span data-stu-id="79b09-175">**$174.11**</span></span>|<span data-ttu-id="79b09-176">**0.01%**</span><span class="sxs-lookup"><span data-stu-id="79b09-176">**0.01%**</span></span>|  
|<span data-ttu-id="79b09-177">**Road-150**</span><span class="sxs-lookup"><span data-stu-id="79b09-177">**Road-150**</span></span>|<span data-ttu-id="79b09-178">**$2,363,805.16**</span><span class="sxs-lookup"><span data-stu-id="79b09-178">**$2,363,805.16**</span></span>|<span data-ttu-id="79b09-179">**$0.00**</span><span class="sxs-lookup"><span data-stu-id="79b09-179">**$0.00**</span></span>|<span data-ttu-id="79b09-180">**0.00%**</span><span class="sxs-lookup"><span data-stu-id="79b09-180">**0.00%**</span></span>|  
|<span data-ttu-id="79b09-181">**Touring-3000**</span><span class="sxs-lookup"><span data-stu-id="79b09-181">**Touring-3000**</span></span>|<span data-ttu-id="79b09-182">**$2,046,508.26**</span><span class="sxs-lookup"><span data-stu-id="79b09-182">**$2,046,508.26**</span></span>|<span data-ttu-id="79b09-183">**$79,582.15**</span><span class="sxs-lookup"><span data-stu-id="79b09-183">**$79,582.15**</span></span>|<span data-ttu-id="79b09-184">**3.89%**</span><span class="sxs-lookup"><span data-stu-id="79b09-184">**3.89%**</span></span>|  
  
 <span data-ttu-id="79b09-185">取得された製品のセットは、Preferred10Products と同じであるように見えます。そこで、Preferred10Products のセットを検証してみることにします。</span><span class="sxs-lookup"><span data-stu-id="79b09-185">The obtained set of products seems to be the same as Preferred10Products; so, verifying the Preferred10Products set:</span></span>  
  
 `with member [Measures].[PCT Discount] AS '[Measures].[Discount Amount]/[Measures].[Reseller Sales Amount]', FORMAT_STRING = 'Percent'`  
  
 `set Top10SellingProducts as 'topcount([Product].[Model Name].children, 10, [Measures].[Reseller Sales Amount])'`  
  
 `set Preferred10Products as '`  
  
 `{[Product].[Model Name].&[Mountain-200],`  
  
 `[Product].[Model Name].&[Road-250],`  
  
 `[Product].[Model Name].&[Mountain-100],`  
  
 `[Product].[Model Name].&[Road-650],`  
  
 `[Product].[Model Name].&[Touring-1000],`  
  
 `[Product].[Model Name].&[Road-550-W],`  
  
 `[Product].[Model Name].&[Road-350-W],`  
  
 `[Product].[Model Name].&[HL Mountain Frame],`  
  
 `[Product].[Model Name].&[Road-150],`  
  
 `[Product].[Model Name].&[Touring-3000]`  
  
 `}'`  
  
 `select {[Measures].[Reseller Sales Amount], [Measures].[Discount Amount], [Measures].[PCT Discount]} on 0,`  
  
 `Preferred10Products on 1`  
  
 `from [Adventure Works]`  
  
 <span data-ttu-id="79b09-186">次の結果から、両方のセット (Top10SellingProducts と Preferred10Products) が同一であることがわかります。</span><span class="sxs-lookup"><span data-stu-id="79b09-186">As per the following results, both sets (Top10SellingProducts, Preferred10Products) are the same</span></span>  
  
|||||  
|-|-|-|-|  
||<span data-ttu-id="79b09-187">**Reseller Sales Amount**</span><span class="sxs-lookup"><span data-stu-id="79b09-187">**Reseller Sales Amount**</span></span>|<span data-ttu-id="79b09-188">**Discount Amount**</span><span class="sxs-lookup"><span data-stu-id="79b09-188">**Discount Amount**</span></span>|<span data-ttu-id="79b09-189">**PCT Discount**</span><span class="sxs-lookup"><span data-stu-id="79b09-189">**PCT Discount**</span></span>|  
|<span data-ttu-id="79b09-190">**Mountain-200**</span><span class="sxs-lookup"><span data-stu-id="79b09-190">**Mountain-200**</span></span>|<span data-ttu-id="79b09-191">**$14,356,699.36**</span><span class="sxs-lookup"><span data-stu-id="79b09-191">**$14,356,699.36**</span></span>|<span data-ttu-id="79b09-192">**$19,012.71**</span><span class="sxs-lookup"><span data-stu-id="79b09-192">**$19,012.71**</span></span>|<span data-ttu-id="79b09-193">**0.13%**</span><span class="sxs-lookup"><span data-stu-id="79b09-193">**0.13%**</span></span>|  
|<span data-ttu-id="79b09-194">**Road-250**</span><span class="sxs-lookup"><span data-stu-id="79b09-194">**Road-250**</span></span>|<span data-ttu-id="79b09-195">**$9,377,457.68**</span><span class="sxs-lookup"><span data-stu-id="79b09-195">**$9,377,457.68**</span></span>|<span data-ttu-id="79b09-196">**$4,032.47**</span><span class="sxs-lookup"><span data-stu-id="79b09-196">**$4,032.47**</span></span>|<span data-ttu-id="79b09-197">**0.04%**</span><span class="sxs-lookup"><span data-stu-id="79b09-197">**0.04%**</span></span>|  
|<span data-ttu-id="79b09-198">**Mountain-100**</span><span class="sxs-lookup"><span data-stu-id="79b09-198">**Mountain-100**</span></span>|<span data-ttu-id="79b09-199">**$8,568,958.27**</span><span class="sxs-lookup"><span data-stu-id="79b09-199">**$8,568,958.27**</span></span>|<span data-ttu-id="79b09-200">**$139,393.27**</span><span class="sxs-lookup"><span data-stu-id="79b09-200">**$139,393.27**</span></span>|<span data-ttu-id="79b09-201">**1.63%**</span><span class="sxs-lookup"><span data-stu-id="79b09-201">**1.63%**</span></span>|  
|<span data-ttu-id="79b09-202">**道路 650**</span><span class="sxs-lookup"><span data-stu-id="79b09-202">**Road-650**</span></span>|<span data-ttu-id="79b09-203">**$7,442,141.81**</span><span class="sxs-lookup"><span data-stu-id="79b09-203">**$7,442,141.81**</span></span>|<span data-ttu-id="79b09-204">**$39,698.30**</span><span class="sxs-lookup"><span data-stu-id="79b09-204">**$39,698.30**</span></span>|<span data-ttu-id="79b09-205">**0.53%**</span><span class="sxs-lookup"><span data-stu-id="79b09-205">**0.53%**</span></span>|  
|<span data-ttu-id="79b09-206">**Touring 1000**</span><span class="sxs-lookup"><span data-stu-id="79b09-206">**Touring-1000**</span></span>|<span data-ttu-id="79b09-207">**$6,723,794.29**</span><span class="sxs-lookup"><span data-stu-id="79b09-207">**$6,723,794.29**</span></span>|<span data-ttu-id="79b09-208">**$166,144.17**</span><span class="sxs-lookup"><span data-stu-id="79b09-208">**$166,144.17**</span></span>|<span data-ttu-id="79b09-209">**2.47%**</span><span class="sxs-lookup"><span data-stu-id="79b09-209">**2.47%**</span></span>|  
|<span data-ttu-id="79b09-210">**道路-w 550**</span><span class="sxs-lookup"><span data-stu-id="79b09-210">**Road-550-W**</span></span>|<span data-ttu-id="79b09-211">**$3,668,383.88**</span><span class="sxs-lookup"><span data-stu-id="79b09-211">**$3,668,383.88**</span></span>|<span data-ttu-id="79b09-212">**$1,901.97**</span><span class="sxs-lookup"><span data-stu-id="79b09-212">**$1,901.97**</span></span>|<span data-ttu-id="79b09-213">**0.05%**</span><span class="sxs-lookup"><span data-stu-id="79b09-213">**0.05%**</span></span>|  
|<span data-ttu-id="79b09-214">**Road-350-W**</span><span class="sxs-lookup"><span data-stu-id="79b09-214">**Road-350-W**</span></span>|<span data-ttu-id="79b09-215">**$3,665,932.31**</span><span class="sxs-lookup"><span data-stu-id="79b09-215">**$3,665,932.31**</span></span>|<span data-ttu-id="79b09-216">**$20,946.50**</span><span class="sxs-lookup"><span data-stu-id="79b09-216">**$20,946.50**</span></span>|<span data-ttu-id="79b09-217">**0.57%**</span><span class="sxs-lookup"><span data-stu-id="79b09-217">**0.57%**</span></span>|  
|<span data-ttu-id="79b09-218">**HL Mountain Frame**</span><span class="sxs-lookup"><span data-stu-id="79b09-218">**HL Mountain Frame**</span></span>|<span data-ttu-id="79b09-219">**$3,365,069.27**</span><span class="sxs-lookup"><span data-stu-id="79b09-219">**$3,365,069.27**</span></span>|<span data-ttu-id="79b09-220">**$174.11**</span><span class="sxs-lookup"><span data-stu-id="79b09-220">**$174.11**</span></span>|<span data-ttu-id="79b09-221">**0.01%**</span><span class="sxs-lookup"><span data-stu-id="79b09-221">**0.01%**</span></span>|  
|<span data-ttu-id="79b09-222">**Road-150**</span><span class="sxs-lookup"><span data-stu-id="79b09-222">**Road-150**</span></span>|<span data-ttu-id="79b09-223">**$2,363,805.16**</span><span class="sxs-lookup"><span data-stu-id="79b09-223">**$2,363,805.16**</span></span>|<span data-ttu-id="79b09-224">**$0.00**</span><span class="sxs-lookup"><span data-stu-id="79b09-224">**$0.00**</span></span>|<span data-ttu-id="79b09-225">**0.00%**</span><span class="sxs-lookup"><span data-stu-id="79b09-225">**0.00%**</span></span>|  
|<span data-ttu-id="79b09-226">**Touring-3000**</span><span class="sxs-lookup"><span data-stu-id="79b09-226">**Touring-3000**</span></span>|<span data-ttu-id="79b09-227">**$2,046,508.26**</span><span class="sxs-lookup"><span data-stu-id="79b09-227">**$2,046,508.26**</span></span>|<span data-ttu-id="79b09-228">**$79,582.15**</span><span class="sxs-lookup"><span data-stu-id="79b09-228">**$79,582.15**</span></span>|<span data-ttu-id="79b09-229">**3.89%**</span><span class="sxs-lookup"><span data-stu-id="79b09-229">**3.89%**</span></span>|  
  
 <span data-ttu-id="79b09-230">次の例が示しているのは、deep Autoexists の概念です。</span><span class="sxs-lookup"><span data-stu-id="79b09-230">The following example will illustrate the concept of deep Autoexists.</span></span> <span data-ttu-id="79b09-231">この例では、[Mountain] グループの製品について、[Product].[Product Line] 属性で Top10SellingProducts をフィルター処理します。</span><span class="sxs-lookup"><span data-stu-id="79b09-231">In the example we are filtering Top10SellingProducts by [Product].[Product Line] attribute for those in [Mountain] group.</span></span> <span data-ttu-id="79b09-232">どちらの属性 (スライサーおよび軸) も同じディメンション ([Product]) に属している点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="79b09-232">Note that both attributes (slicer and axis) belong to the same dimension, [Product].</span></span>  
  
 `with member [Measures].[PCT Discount] AS '[Measures].[Discount Amount]/[Measures].[Reseller Sales Amount]', FORMAT_STRING = 'Percent'`  
  
 `set Top10SellingProducts as 'topcount([Product].[Model Name].children, 10, [Measures].[Reseller Sales Amount])'`  
  
 `// Preferred10Products set removed for clarity`  
  
 `select {[Measures].[Reseller Sales Amount], [Measures].[Discount Amount], [Measures].[PCT Discount]} on 0,`  
  
 `Top10SellingProducts on 1`  
  
 `from [Adventure Works]`  
  
 `where [Product].[Product Line].[Mountain]`  
  
 <span data-ttu-id="79b09-233">結果セットは、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="79b09-233">Produces the following result set:</span></span>  
  
|||||  
|-|-|-|-|  
||<span data-ttu-id="79b09-234">**Reseller Sales Amount**</span><span class="sxs-lookup"><span data-stu-id="79b09-234">**Reseller Sales Amount**</span></span>|<span data-ttu-id="79b09-235">**Discount Amount**</span><span class="sxs-lookup"><span data-stu-id="79b09-235">**Discount Amount**</span></span>|<span data-ttu-id="79b09-236">**PCT Discount**</span><span class="sxs-lookup"><span data-stu-id="79b09-236">**PCT Discount**</span></span>|  
|<span data-ttu-id="79b09-237">**Mountain-200**</span><span class="sxs-lookup"><span data-stu-id="79b09-237">**Mountain-200**</span></span>|<span data-ttu-id="79b09-238">**$14,356,699.36**</span><span class="sxs-lookup"><span data-stu-id="79b09-238">**$14,356,699.36**</span></span>|<span data-ttu-id="79b09-239">**$19,012.71**</span><span class="sxs-lookup"><span data-stu-id="79b09-239">**$19,012.71**</span></span>|<span data-ttu-id="79b09-240">**0.13%**</span><span class="sxs-lookup"><span data-stu-id="79b09-240">**0.13%**</span></span>|  
|<span data-ttu-id="79b09-241">**Mountain-100**</span><span class="sxs-lookup"><span data-stu-id="79b09-241">**Mountain-100**</span></span>|<span data-ttu-id="79b09-242">**$8,568,958.27**</span><span class="sxs-lookup"><span data-stu-id="79b09-242">**$8,568,958.27**</span></span>|<span data-ttu-id="79b09-243">**$139,393.27**</span><span class="sxs-lookup"><span data-stu-id="79b09-243">**$139,393.27**</span></span>|<span data-ttu-id="79b09-244">**1.63%**</span><span class="sxs-lookup"><span data-stu-id="79b09-244">**1.63%**</span></span>|  
|<span data-ttu-id="79b09-245">**HL Mountain Frame**</span><span class="sxs-lookup"><span data-stu-id="79b09-245">**HL Mountain Frame**</span></span>|<span data-ttu-id="79b09-246">**$3,365,069.27**</span><span class="sxs-lookup"><span data-stu-id="79b09-246">**$3,365,069.27**</span></span>|<span data-ttu-id="79b09-247">**$174.11**</span><span class="sxs-lookup"><span data-stu-id="79b09-247">**$174.11**</span></span>|<span data-ttu-id="79b09-248">**0.01%**</span><span class="sxs-lookup"><span data-stu-id="79b09-248">**0.01%**</span></span>|  
|<span data-ttu-id="79b09-249">**Mountain ～ 300**</span><span class="sxs-lookup"><span data-stu-id="79b09-249">**Mountain-300**</span></span>|<span data-ttu-id="79b09-250">**$1,907,249.38**</span><span class="sxs-lookup"><span data-stu-id="79b09-250">**$1,907,249.38**</span></span>|<span data-ttu-id="79b09-251">**$876.95**</span><span class="sxs-lookup"><span data-stu-id="79b09-251">**$876.95**</span></span>|<span data-ttu-id="79b09-252">**0.05%**</span><span class="sxs-lookup"><span data-stu-id="79b09-252">**0.05%**</span></span>|  
|<span data-ttu-id="79b09-253">**Mountain-500**</span><span class="sxs-lookup"><span data-stu-id="79b09-253">**Mountain-500**</span></span>|<span data-ttu-id="79b09-254">**$1,067,327.31**</span><span class="sxs-lookup"><span data-stu-id="79b09-254">**$1,067,327.31**</span></span>|<span data-ttu-id="79b09-255">**$17,266.09**</span><span class="sxs-lookup"><span data-stu-id="79b09-255">**$17,266.09**</span></span>|<span data-ttu-id="79b09-256">**1.62%**</span><span class="sxs-lookup"><span data-stu-id="79b09-256">**1.62%**</span></span>|  
|<span data-ttu-id="79b09-257">**Mountain-400-W**</span><span class="sxs-lookup"><span data-stu-id="79b09-257">**Mountain-400-W**</span></span>|<span data-ttu-id="79b09-258">**$592,450.05**</span><span class="sxs-lookup"><span data-stu-id="79b09-258">**$592,450.05**</span></span>|<span data-ttu-id="79b09-259">**$303.49**</span><span class="sxs-lookup"><span data-stu-id="79b09-259">**$303.49**</span></span>|<span data-ttu-id="79b09-260">**0.05%**</span><span class="sxs-lookup"><span data-stu-id="79b09-260">**0.05%**</span></span>|  
|<span data-ttu-id="79b09-261">**LL Mountain Frame**</span><span class="sxs-lookup"><span data-stu-id="79b09-261">**LL Mountain Frame**</span></span>|<span data-ttu-id="79b09-262">**$521,864.42**</span><span class="sxs-lookup"><span data-stu-id="79b09-262">**$521,864.42**</span></span>|<span data-ttu-id="79b09-263">**$252.41**</span><span class="sxs-lookup"><span data-stu-id="79b09-263">**$252.41**</span></span>|<span data-ttu-id="79b09-264">**0.05%**</span><span class="sxs-lookup"><span data-stu-id="79b09-264">**0.05%**</span></span>|  
|<span data-ttu-id="79b09-265">**ML Mountain Frame-W**</span><span class="sxs-lookup"><span data-stu-id="79b09-265">**ML Mountain Frame-W**</span></span>|<span data-ttu-id="79b09-266">**$482,953.16**</span><span class="sxs-lookup"><span data-stu-id="79b09-266">**$482,953.16**</span></span>|<span data-ttu-id="79b09-267">**$206.95**</span><span class="sxs-lookup"><span data-stu-id="79b09-267">**$206.95**</span></span>|<span data-ttu-id="79b09-268">**0.04%**</span><span class="sxs-lookup"><span data-stu-id="79b09-268">**0.04%**</span></span>|  
|<span data-ttu-id="79b09-269">**ML Mountain Frame**</span><span class="sxs-lookup"><span data-stu-id="79b09-269">**ML Mountain Frame**</span></span>|<span data-ttu-id="79b09-270">**$343,785.29**</span><span class="sxs-lookup"><span data-stu-id="79b09-270">**$343,785.29**</span></span>|<span data-ttu-id="79b09-271">**$161.82**</span><span class="sxs-lookup"><span data-stu-id="79b09-271">**$161.82**</span></span>|<span data-ttu-id="79b09-272">**0.05%**</span><span class="sxs-lookup"><span data-stu-id="79b09-272">**0.05%**</span></span>|  
|<span data-ttu-id="79b09-273">**Women's Mountain Shorts**</span><span class="sxs-lookup"><span data-stu-id="79b09-273">**Women's Mountain Shorts**</span></span>|<span data-ttu-id="79b09-274">**$260,304.09**</span><span class="sxs-lookup"><span data-stu-id="79b09-274">**$260,304.09**</span></span>|<span data-ttu-id="79b09-275">**$6,675.56**</span><span class="sxs-lookup"><span data-stu-id="79b09-275">**$6,675.56**</span></span>|<span data-ttu-id="79b09-276">**2.56%**</span><span class="sxs-lookup"><span data-stu-id="79b09-276">**2.56%**</span></span>|  
  
 <span data-ttu-id="79b09-277">この結果セットを見ると、Top10SellingProducts のリストに、新しい製品が 7 つ出現していることがわかります。また、Mountain-200、Mountain-100、および HL Mountain Frame がリストの上位に移動しています。</span><span class="sxs-lookup"><span data-stu-id="79b09-277">In the above result set we have seven newcomers to the list of Top10SellingProducts and Mountain-200, Mountain-100, and HL Mountain Frame have moved to the top of the list.</span></span> <span data-ttu-id="79b09-278">その前の結果セットでは、この 3 つの値がばらばらに存在していました。</span><span class="sxs-lookup"><span data-stu-id="79b09-278">In the previous result set those three values were interspersed.</span></span>  
  
 <span data-ttu-id="79b09-279">クエリのスライス条件を満たすように Top10SellingProducts のセットが評価されていることから、これを deep Autoexists といいます。</span><span class="sxs-lookup"><span data-stu-id="79b09-279">This is called Deep Autoexists, because the Top10SellingProducts set is evaluated to meet the slicing conditions of the query.</span></span> <span data-ttu-id="79b09-280">deep Autoexists では、スライサーの式、軸の下位選択式などを適用した後、可能な限り深い場所に到達するように、すべての式が評価されます。</span><span class="sxs-lookup"><span data-stu-id="79b09-280">Deep Autoexists means that all expressions will be evaluated to meet the deepest possible space after applying the slicer expressions, the sub select expressions in the axis, and so on.</span></span>  
  
 <span data-ttu-id="79b09-281">ただし、場合によっては、次の例のように、Top10SellingProducts に対して、Preferred10Products と同等の分析を行うことができれば便利です。</span><span class="sxs-lookup"><span data-stu-id="79b09-281">However, one might want to be able to do the analysis over the Top10SellingProducts as equivalent to Preferred10Products, as in the following example:</span></span>  
  
 `with member [Measures].[PCT Discount] AS '[Measures].[Discount Amount]/[Measures].[Reseller Sales Amount]', FORMAT_STRING = 'Percent'`  
  
 `set Top10SellingProducts as 'topcount([Product].[Model Name].children, 10, [Measures].[Reseller Sales Amount])'`  
  
 `set Preferred10Products as '`  
  
 `{[Product].[Model Name].&[Mountain-200],`  
  
 `[Product].[Model Name].&[Road-250],`  
  
 `[Product].[Model Name].&[Mountain-100],`  
  
 `[Product].[Model Name].&[Road-650],`  
  
 `[Product].[Model Name].&[Touring-1000],`  
  
 `[Product].[Model Name].&[Road-550-W],`  
  
 `[Product].[Model Name].&[Road-350-W],`  
  
 `[Product].[Model Name].&[HL Mountain Frame],`  
  
 `[Product].[Model Name].&[Road-150],`  
  
 `[Product].[Model Name].&[Touring-3000]`  
  
 `}'`  
  
 `select {[Measures].[Reseller Sales Amount], [Measures].[Discount Amount], [Measures].[PCT Discount]} on 0,`  
  
 `Preferred10Products on 1`  
  
 `from [Adventure Works]`  
  
 `where [Product].[Product Line].[Mountain]`  
  
 <span data-ttu-id="79b09-282">結果セットは、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="79b09-282">Produces the following result set:</span></span>  
  
|||||  
|-|-|-|-|  
||<span data-ttu-id="79b09-283">**Reseller Sales Amount**</span><span class="sxs-lookup"><span data-stu-id="79b09-283">**Reseller Sales Amount**</span></span>|<span data-ttu-id="79b09-284">**Discount Amount**</span><span class="sxs-lookup"><span data-stu-id="79b09-284">**Discount Amount**</span></span>|<span data-ttu-id="79b09-285">**PCT Discount**</span><span class="sxs-lookup"><span data-stu-id="79b09-285">**PCT Discount**</span></span>|  
|<span data-ttu-id="79b09-286">**Mountain-200**</span><span class="sxs-lookup"><span data-stu-id="79b09-286">**Mountain-200**</span></span>|<span data-ttu-id="79b09-287">**$14,356,699.36**</span><span class="sxs-lookup"><span data-stu-id="79b09-287">**$14,356,699.36**</span></span>|<span data-ttu-id="79b09-288">**$19,012.71**</span><span class="sxs-lookup"><span data-stu-id="79b09-288">**$19,012.71**</span></span>|<span data-ttu-id="79b09-289">**0.13%**</span><span class="sxs-lookup"><span data-stu-id="79b09-289">**0.13%**</span></span>|  
|<span data-ttu-id="79b09-290">**Mountain-100**</span><span class="sxs-lookup"><span data-stu-id="79b09-290">**Mountain-100**</span></span>|<span data-ttu-id="79b09-291">**$8,568,958.27**</span><span class="sxs-lookup"><span data-stu-id="79b09-291">**$8,568,958.27**</span></span>|<span data-ttu-id="79b09-292">**$139,393.27**</span><span class="sxs-lookup"><span data-stu-id="79b09-292">**$139,393.27**</span></span>|<span data-ttu-id="79b09-293">**1.63%**</span><span class="sxs-lookup"><span data-stu-id="79b09-293">**1.63%**</span></span>|  
|<span data-ttu-id="79b09-294">**HL Mountain Frame**</span><span class="sxs-lookup"><span data-stu-id="79b09-294">**HL Mountain Frame**</span></span>|<span data-ttu-id="79b09-295">**$3,365,069.27**</span><span class="sxs-lookup"><span data-stu-id="79b09-295">**$3,365,069.27**</span></span>|<span data-ttu-id="79b09-296">**$174.11**</span><span class="sxs-lookup"><span data-stu-id="79b09-296">**$174.11**</span></span>|<span data-ttu-id="79b09-297">**0.01%**</span><span class="sxs-lookup"><span data-stu-id="79b09-297">**0.01%**</span></span>|  
  
 <span data-ttu-id="79b09-298">上の結果では、スライスによって、Preferred10Products から、[Product].[Product Line] の [Mountain] グループに属する製品だけを含む結果が得られます。Preferred10Products は定数式であるため、これは当然の結果と言えます。</span><span class="sxs-lookup"><span data-stu-id="79b09-298">In the above results, the slicing gives a result that contains only those products from Preferred10Products that are part of the [Mountain] group in [Product].[Product Line]; as expected, because Preferred10Products is a constant expression.</span></span>  
  
 <span data-ttu-id="79b09-299">この結果セットは、Shallow Autoexists と考えることもできます。</span><span class="sxs-lookup"><span data-stu-id="79b09-299">This result set is also understood as Shallow Autoexists.</span></span> <span data-ttu-id="79b09-300">式がスライス句よりも前に評価されるためです。</span><span class="sxs-lookup"><span data-stu-id="79b09-300">This is because the expression is evaluated before the slicing clause.</span></span> <span data-ttu-id="79b09-301">前の例では、概念をわかりやすく説明するために、定数式を使用しました。</span><span class="sxs-lookup"><span data-stu-id="79b09-301">In the previous example, the expression was a constant expression for illustration purposes in order to introduce the concept.</span></span>  
  
 <span data-ttu-id="79b09-302">Autoexists の動作は、`Autoexists` 接続文字列プロパティを使用することにより、セッション レベルで変更できます。</span><span class="sxs-lookup"><span data-stu-id="79b09-302">Autoexists behavior can be modified at the session level using the `Autoexists` connection string property.</span></span> <span data-ttu-id="79b09-303">次の例は、まず、新しいセッションを開いてを追加する、 *Autoexists=3* プロパティを接続文字列にします。</span><span class="sxs-lookup"><span data-stu-id="79b09-303">The following example begins by opening a new session and adding the *Autoexists=3* property to the connection string.</span></span> <span data-ttu-id="79b09-304">この例を実行するには、新しい接続を開く必要があります。</span><span class="sxs-lookup"><span data-stu-id="79b09-304">You must open a new connection in order to do the example.</span></span> <span data-ttu-id="79b09-305">いったん Autoexist 設定で確立された接続は、その接続が解除されるまで有効です。</span><span class="sxs-lookup"><span data-stu-id="79b09-305">Once the connection is established with the Autoexist setting it will remain in effect until that connection is finished.</span></span>  
  
 `with member [Measures].[PCT Discount] AS '[Measures].[Discount Amount]/[Measures].[Reseller Sales Amount]', FORMAT_STRING = 'Percent'`  
  
 `set Top10SellingProducts as 'topcount([Product].[Model Name].children, 10, [Measures].[Reseller Sales Amount])'`  
  
 `//Preferred10Products set removed for clarity`  
  
 `select {[Measures].[Reseller Sales Amount], [Measures].[Discount Amount], [Measures].[PCT Discount]} on 0,`  
  
 `Top10SellingProducts on 1`  
  
 `from [Adventure Works]`  
  
 `where [Product].[Product Line].[Mountain]`  
  
 <span data-ttu-id="79b09-306">次の結果セットは、shallow Autoexists の動作を示しています。</span><span class="sxs-lookup"><span data-stu-id="79b09-306">The following result set now shows the shallow behavior of Autoexists.</span></span>  
  
|||||  
|-|-|-|-|  
||<span data-ttu-id="79b09-307">**Reseller Sales Amount**</span><span class="sxs-lookup"><span data-stu-id="79b09-307">**Reseller Sales Amount**</span></span>|<span data-ttu-id="79b09-308">**Discount Amount**</span><span class="sxs-lookup"><span data-stu-id="79b09-308">**Discount Amount**</span></span>|<span data-ttu-id="79b09-309">**PCT Discount**</span><span class="sxs-lookup"><span data-stu-id="79b09-309">**PCT Discount**</span></span>|  
|<span data-ttu-id="79b09-310">**Mountain-200**</span><span class="sxs-lookup"><span data-stu-id="79b09-310">**Mountain-200**</span></span>|<span data-ttu-id="79b09-311">**$14,356,699.36**</span><span class="sxs-lookup"><span data-stu-id="79b09-311">**$14,356,699.36**</span></span>|<span data-ttu-id="79b09-312">**$19,012.71**</span><span class="sxs-lookup"><span data-stu-id="79b09-312">**$19,012.71**</span></span>|<span data-ttu-id="79b09-313">**0.13%**</span><span class="sxs-lookup"><span data-stu-id="79b09-313">**0.13%**</span></span>|  
|<span data-ttu-id="79b09-314">**Mountain-100**</span><span class="sxs-lookup"><span data-stu-id="79b09-314">**Mountain-100**</span></span>|<span data-ttu-id="79b09-315">**$8,568,958.27**</span><span class="sxs-lookup"><span data-stu-id="79b09-315">**$8,568,958.27**</span></span>|<span data-ttu-id="79b09-316">**$139,393.27**</span><span class="sxs-lookup"><span data-stu-id="79b09-316">**$139,393.27**</span></span>|<span data-ttu-id="79b09-317">**1.63%**</span><span class="sxs-lookup"><span data-stu-id="79b09-317">**1.63%**</span></span>|  
|<span data-ttu-id="79b09-318">**HL Mountain Frame**</span><span class="sxs-lookup"><span data-stu-id="79b09-318">**HL Mountain Frame**</span></span>|<span data-ttu-id="79b09-319">**$3,365,069.27**</span><span class="sxs-lookup"><span data-stu-id="79b09-319">**$3,365,069.27**</span></span>|<span data-ttu-id="79b09-320">**$174.11**</span><span class="sxs-lookup"><span data-stu-id="79b09-320">**$174.11**</span></span>|<span data-ttu-id="79b09-321">**0.01%**</span><span class="sxs-lookup"><span data-stu-id="79b09-321">**0.01%**</span></span>|  
  
 <span data-ttu-id="79b09-322">Autoexists の動作は、接続文字列の AUTOEXISTS = [1 | 2 | 3] パラメーターを使用して変更できます。パラメーターの使用法については、「 [xmla&#41;&#40;サポートされる Xmla プロパティ](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties)」を参照してください <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.ConnectionString%2A> 。</span><span class="sxs-lookup"><span data-stu-id="79b09-322">Autoexists behavior can be modified by using the AUTOEXISTS=[1|2|3] parameter in the connection string; see [Supported XMLA Properties &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties) and <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.ConnectionString%2A> for parameter usage.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79b09-323">参照</span><span class="sxs-lookup"><span data-stu-id="79b09-323">See Also</span></span>  
 <span data-ttu-id="79b09-324">[MDX &#40;Analysis Services の主な概念&#41;](../key-concepts-in-mdx-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="79b09-324">[Key Concepts in MDX &#40;Analysis Services&#41;](../key-concepts-in-mdx-analysis-services.md) </span></span>  
 <span data-ttu-id="79b09-325">[キューブ空間](cube-space.md) </span><span class="sxs-lookup"><span data-stu-id="79b09-325">[Cube Space](cube-space.md) </span></span>  
 <span data-ttu-id="79b09-326">[組](tuples.md) </span><span class="sxs-lookup"><span data-stu-id="79b09-326">[Tuples](tuples.md) </span></span>  
 <span data-ttu-id="79b09-327">[MDX&#41;&#40;メンバー、組、およびセットの操作](working-with-members-tuples-and-sets-mdx.md) </span><span class="sxs-lookup"><span data-stu-id="79b09-327">[Working with Members, Tuples, and Sets &#40;MDX&#41;](working-with-members-tuples-and-sets-mdx.md) </span></span>  
 <span data-ttu-id="79b09-328">[ビジュアルの合計と非表示の合計](visual-totals-and-non-visual-totals.md) </span><span class="sxs-lookup"><span data-stu-id="79b09-328">[Visual Totals and Non Visual Totals](visual-totals-and-non-visual-totals.md) </span></span>  
 <span data-ttu-id="79b09-329">[Mdx 言語リファレンス &#40;MDX&#41;](/sql/mdx/mdx-language-reference-mdx) </span><span class="sxs-lookup"><span data-stu-id="79b09-329">[MDX Language Reference &#40;MDX&#41;](/sql/mdx/mdx-language-reference-mdx) </span></span>  
 [<span data-ttu-id="79b09-330">多次元式 &#40;MDX&#41; リファレンス</span><span class="sxs-lookup"><span data-stu-id="79b09-330">Multidimensional Expressions &#40;MDX&#41; Reference</span></span>](/sql/mdx/multidimensional-expressions-mdx-reference)  
  
  
