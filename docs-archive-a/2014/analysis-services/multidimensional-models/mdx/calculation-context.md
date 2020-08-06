---
title: 計算コンテキスト |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: aec8aa98-b77d-4f8f-9684-2618b1d8e970
author: minewiskan
ms.author: owend
ms.openlocfilehash: e6d14df51c6ec37fb96520af7acf207227ae4ea5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716893"
---
# <a name="calculation-context"></a><span data-ttu-id="77c1e-102">計算コンテキスト</span><span class="sxs-lookup"><span data-stu-id="77c1e-102">Calculation Context</span></span>
  <span data-ttu-id="77c1e-103">計算コンテキストとは、式が評価され、すべての座標が明示的に知られているか、または式から派生することができる、キューブの既知のサブ空間です。</span><span class="sxs-lookup"><span data-stu-id="77c1e-103">The calculation context is the known subspace of the cube where an expression is evaluated and all coordinates are either explicitly known or can be derived from the expression.</span></span>  
  
## <a name="determining-the-calculation-context"></a><span data-ttu-id="77c1e-104">計算コンテキストの決定</span><span class="sxs-lookup"><span data-stu-id="77c1e-104">Determining the calculation context</span></span>  
 <span data-ttu-id="77c1e-105">すべてのセット、メンバー、組、数値関数は、MDX 式またはステートメント全体のコンテキストで実行されます。</span><span class="sxs-lookup"><span data-stu-id="77c1e-105">Every set, member, tuple, or numeric function executes in the context of the entire MDX expression or statement.</span></span> <span data-ttu-id="77c1e-106">組などの引数を関数に渡す際には、キューブ空間内の一部の座標のみが明示的に指定されます。</span><span class="sxs-lookup"><span data-stu-id="77c1e-106">When an argument, such as a tuple, is passed to a function, only some of the coordinates in the cube space are explicitly provided.</span></span> <span data-ttu-id="77c1e-107">その他の座標は現在の計算コンテキストを基に取得されます。</span><span class="sxs-lookup"><span data-stu-id="77c1e-107">The other coordinates are obtained based on the current calculation context.</span></span>  
  
 <span data-ttu-id="77c1e-108">指定のないセル座標と属性メンバーの計算コンテキストは、次の順序で決定されます。</span><span class="sxs-lookup"><span data-stu-id="77c1e-108">The calculation context for unspecified cell coordinates and attribute members is determined in the following order:</span></span>  
  
1.  <span data-ttu-id="77c1e-109">FROM 句 (該当する場合) : キューブ全体、または SELECT ステートメントの形式でサブキューブを指定できます。</span><span class="sxs-lookup"><span data-stu-id="77c1e-109">The FROM clause (if applicable) - this clause can either specify an entire cube or can specify a subcube in the form of a SELECT statement.</span></span>  
  
2.  <span data-ttu-id="77c1e-110">WHERE 句 (該当する場合) : *スライサー軸*ともいいます。この軸に、クエリの列と行の軸で返されるメンバーを制限するセット、組、メンバーを指定します。</span><span class="sxs-lookup"><span data-stu-id="77c1e-110">The WHERE clause (if applicable) - this clause, which is also known as the *slicer axis*, on which you specify a set, tuple, or member that restricts the members returned on the column and row axis by a query.</span></span> <span data-ttu-id="77c1e-111">概念上、列または行の軸で明示的に指定されていないすべての属性階層の既定のメンバーは、スライサー軸の一部として使用されます。</span><span class="sxs-lookup"><span data-stu-id="77c1e-111">Conceptually, the default member of every attribute hierarchy that is not explicitly specified on column or row axis is part of the slicer axis.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="77c1e-112">特定の属性のセル座標がスライサー軸とそれ以外の軸で指定されている場合、軸のセットのメンバーを決定する際に、関数で指定されている座標が優先的に使用されることがあります。</span><span class="sxs-lookup"><span data-stu-id="77c1e-112">When cell coordinates for a particular attribute are specified on both the slicer axis and on another axis, the coordinates specified in the function may take precedence in determining the members of the set on the axis.</span></span> <span data-ttu-id="77c1e-113">[Filter (MDX)](/sql/mdx/filter-mdx) 関数および [Order (MDX)](/sql/mdx/order-mdx) 関数はその例です。WHERE 句、または FROM 句の SELECT ステートメントによって計算コンテキストから除外された属性メンバーを使用して、結果の絞り込みや順序指定ができます。</span><span class="sxs-lookup"><span data-stu-id="77c1e-113">The [Filter (MDX)](/sql/mdx/filter-mdx) and [Order (MDX)](/sql/mdx/order-mdx) functions are examples of such functions - you can filter or order a result by attribute members that are excluded from the calculation context by the WHERE clause, or by a SELECT statement in the FROM clause.</span></span>  
  
3.  <span data-ttu-id="77c1e-114">クエリまたは式で定義されている、名前付きセットと計算されるメンバー。</span><span class="sxs-lookup"><span data-stu-id="77c1e-114">The named sets and calculated members defined in the query or expression.</span></span>  
  
4.  <span data-ttu-id="77c1e-115">行軸および列軸で指定された組とセット : 行軸、列軸、またはスライサー軸に出現しない属性については、既定のメンバーが使用されます。</span><span class="sxs-lookup"><span data-stu-id="77c1e-115">The tuples and sets specified on the row and column axes, utilizing the default member for attributes that do not appear on the row, column, or slicer axis.</span></span>  
  
5.  <span data-ttu-id="77c1e-116">各軸上のキューブ セルまたはサブキューブ セル : 軸上の空の組が削除され、HAVING 句が適用されます。</span><span class="sxs-lookup"><span data-stu-id="77c1e-116">The cube or subcube cells on each axis, eliminating empty tuples on the axis and applying the HAVING clause.</span></span>  
  
6.  <span data-ttu-id="77c1e-117">詳細については、「 [クエリ内のキューブ コンテキストの確立 &#40;MDX&#41;](establishing-cube-context-in-a-query-mdx.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="77c1e-117">For more information, see [Establishing Cube Context in a Query &#40;MDX&#41;](establishing-cube-context-in-a-query-mdx.md).</span></span>  
  
 <span data-ttu-id="77c1e-118">次のクエリでは、WHERE 句で指定されている Country 属性のメンバーと Calendar Year 属性のメンバーによって、行軸の計算コンテキストを制限しています。</span><span class="sxs-lookup"><span data-stu-id="77c1e-118">In the following query, the calculation context for the row axis is restricted by the Country attribute member and the Calendar Year attribute member that are specified in the WHERE clause.</span></span>  
  
```  
SELECT Customer.City.City.Members ON 0  
FROM [Adventure Works]  
WHERE (Customer.Country.France, [Date].[Calendar].[Calendar Year].[CY 2004],  
   Measures.[Internet Sales Amount])  
```  
  
 <span data-ttu-id="77c1e-119">このクエリを修正して、行軸に `FILTER` 関数を指定し、この `FILTER` 関数に Calendar Year 属性階層のメンバーを指定した場合、列軸上のセットのメンバーに対して計算コンテキストを指定している Calendar Year 属性階層の属性メンバーを変更できます。</span><span class="sxs-lookup"><span data-stu-id="77c1e-119">However, if you modify this query by specifying the `FILTER` function on the row axis, and utilize a Calendar Year attribute hierarchy member in the `FILTER` function, then the attribute member from the Calendar Year attribute hierarchy that is used to provide the calculation context for the members of the set on the column axis can be modified.</span></span>  
  
```  
SELECT FILTER  
   (  
      Customer.City.City.Members,   
         ([Date].[Calendar].[Calendar Year].[CY 2003],  
            Measures.[Internet Order Quantity]) > 75   
   ) ON 0  
FROM [Adventure Works]  
WHERE (Customer.Country.France,  
   [Date].[Calendar].[Calendar Year].[CY 2004],  
   Measures.[Internet Sales Amount])  
```  
  
 <span data-ttu-id="77c1e-120">上のクエリで、Calendar Year 属性階層の通常の計算コンテキストは CY 2004 ですが、列軸に表示する組のセルの計算コンテキストは、Calendar Year 属性階層の CY 2003 メンバーによってフィルター処理されています。</span><span class="sxs-lookup"><span data-stu-id="77c1e-120">In the previous query, the calculation context for the cells in the tuples that appear on the column axis is filtered by the CY 2003 member of the Calendar Year attribute hierarchy, even though the nominal calculation context for the Calendar Year attribute hierarchy is CY 2004.</span></span> <span data-ttu-id="77c1e-121">さらに、Internet Order Quantity メジャーによるフィルター処理も行われています。</span><span class="sxs-lookup"><span data-stu-id="77c1e-121">Furthermore, it is filtered by the Internet Order Quantity measure.</span></span> <span data-ttu-id="77c1e-122">ただし、列軸のセット メンバーがいったん設定されると、列軸に表示されるメンバーの値に対する計算コンテキストは、WHERE 句によって決定されます。</span><span class="sxs-lookup"><span data-stu-id="77c1e-122">However, once the members of the set on the column axis is set, the calculation context for the values for the members that appear on the axis is again determined by the WHERE clause.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="77c1e-123">クエリのパフォーマンスを向上するには、解決プロセスのできるだけ早い段階でメンバーおよび組を削除してください。</span><span class="sxs-lookup"><span data-stu-id="77c1e-123">To increase query performance, you should eliminate members and tuples as early in the resolution process as possible.</span></span> <span data-ttu-id="77c1e-124">こうすることで、最終的なメンバーのセットに対するクエリ時の複雑な計算を、最小限のセルに対して行うことができます。</span><span class="sxs-lookup"><span data-stu-id="77c1e-124">In this manner, complex query time calculations on the final set of members operate on the fewest cells possible.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77c1e-125">参照</span><span class="sxs-lookup"><span data-stu-id="77c1e-125">See Also</span></span>  
 <span data-ttu-id="77c1e-126">[MDX&#41;&#40;クエリでのキューブコンテキストの確立](establishing-cube-context-in-a-query-mdx.md) </span><span class="sxs-lookup"><span data-stu-id="77c1e-126">[Establishing Cube Context in a Query &#40;MDX&#41;](establishing-cube-context-in-a-query-mdx.md) </span></span>  
 <span data-ttu-id="77c1e-127">[MDX クエリの基礎 &#40;Analysis Services&#41;](mdx-query-fundamentals-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="77c1e-127">[MDX Query Fundamentals &#40;Analysis Services&#41;](mdx-query-fundamentals-analysis-services.md) </span></span>  
 [<span data-ttu-id="77c1e-128">MDX の主な概念 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="77c1e-128">Key Concepts in MDX &#40;Analysis Services&#41;</span></span>](../key-concepts-in-mdx-analysis-services.md)  
  
  
