---
title: スライサー軸の内容の指定 (MDX) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- slicer axis
- filtering data [MDX]
ms.assetid: c56b0a70-cdec-427f-990e-425290344e7d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8620c54970ea14a2ac01c85262a372d2b3db0d68
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712558"
---
# <a name="specifying-the-contents-of-a-slicer-axis-mdx"></a><span data-ttu-id="653de-102">スライサー軸の内容の指定 (MDX)</span><span class="sxs-lookup"><span data-stu-id="653de-102">Specifying the Contents of a Slicer Axis (MDX)</span></span>
  <span data-ttu-id="653de-103">スライサー軸は、多次元式 (MDX) の SELECT ステートメントから返されるデータを絞り込み、指定されているメンバーと重なり合うデータだけが返されるように、返されるデータを制限します。</span><span class="sxs-lookup"><span data-stu-id="653de-103">The slicer axis filters the data returned by the Multidimensional Expressions (MDX) SELECT statement, restricting the returned data so that only data intersecting with the specified members will be returned.</span></span> <span data-ttu-id="653de-104">クエリ内の見えない追加の軸であると考えることができます。</span><span class="sxs-lookup"><span data-stu-id="653de-104">It can be thought of as an invisible extra axis in a query.</span></span> <span data-ttu-id="653de-105">スライサー軸は、MDX の SELECT ステートメントの WHERE 句で定義します。</span><span class="sxs-lookup"><span data-stu-id="653de-105">The slicer axis is defined in the WHERE clause of the SELECT statement in MDX.</span></span>  
  
## <a name="slicer-axis-syntax"></a><span data-ttu-id="653de-106">スライサー軸の構文</span><span class="sxs-lookup"><span data-stu-id="653de-106">Slicer Axis Syntax</span></span>  
 <span data-ttu-id="653de-107">スライサー軸を明示的に指定するには、MDX の `<SELECT slicer axis clause>` を使用します。その際の構文は以下のとおりです。</span><span class="sxs-lookup"><span data-stu-id="653de-107">To explicitly specify a slicer axis, you  using the `<SELECT slicer axis clause>` in MDX, as described in the following syntax:</span></span>  
  
```  
<SELECT slicer axis clause> ::=  WHERE Set_Expression  
```  
  
 <span data-ttu-id="653de-108">このスライサー軸の構文で使用する `Set_Expression` には、その句を評価するためのセットとして処理される組式、またはセット式を指定できます。</span><span class="sxs-lookup"><span data-stu-id="653de-108">In the slicer axis syntax shown, `Set_Expression` can take either a tuple expression, which is treated as a set for the purposes of evaluating the clause, or a set expression.</span></span> <span data-ttu-id="653de-109">セット式を指定した場合は、指定したセットが評価され、そのセット内のすべての組の結果セルが集計されます。</span><span class="sxs-lookup"><span data-stu-id="653de-109">If a set expression is specified, MDX will try to evaluate the set, aggregating the result cells in every tuple along the set.</span></span> <span data-ttu-id="653de-110">つまり、指定したセットに対して [Aggregate](/sql/mdx/aggregate-mdx) 関数が適用され、メジャーごとに定義されている集計関数によって各メジャーが集計されます。</span><span class="sxs-lookup"><span data-stu-id="653de-110">In other words, MDX will try to use the [Aggregate](/sql/mdx/aggregate-mdx) function on the set, aggregating each measure by its associated aggregation function.</span></span> <span data-ttu-id="653de-111">また、セット式を属性階層メンバーのクロス積として表せない場合は、スライサーのセット式の外部にあるセルを NULL と見なして評価されます。</span><span class="sxs-lookup"><span data-stu-id="653de-111">Also, if the set expression cannot be expressed as a crossjoin of attribute hierarchy members, MDX treats cells that fall outside of the set expression for the slicer as null for evaluation purposes.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="653de-112">SQL の WHERE 句とは異なり、MDX SELECT ステートメントの WHERE 句は、クエリの ROWS 軸で返される対象を直接フィルター選択することはありません。</span><span class="sxs-lookup"><span data-stu-id="653de-112">Unlike the WHERE clause in SQL, the WHERE clause of an MDX SELECT statement never directly filters what is returned on the Rows axis of a query.</span></span> <span data-ttu-id="653de-113">クエリの ROWS 軸または COLUMNS 軸に表示される対象をフィルター選択するには、たとえば FILTER、NONEMPTY、TOPCOUNT などの、さまざまな MDX 関数を使用します。</span><span class="sxs-lookup"><span data-stu-id="653de-113">To filter what appears on the Rows or Columns axis of a query, you can use a variety of MDX functions, for example FILTER, NONEMPTY and TOPCOUNT.</span></span>  
  
### <a name="implicit-slicer-axis"></a><span data-ttu-id="653de-114">暗黙的なスライサー軸</span><span class="sxs-lookup"><span data-stu-id="653de-114">Implicit Slicer Axis</span></span>  
 <span data-ttu-id="653de-115">キューブ内の階層のメンバーがクエリ軸に明示的に含まれていない場合は、その階層の既定のメンバーが暗黙的にスライサー軸に含まれます。</span><span class="sxs-lookup"><span data-stu-id="653de-115">If a member from a hierarchy within the cube is not explicitly included in a query axis, the default member from that hierarchy is implicitly included in the slicer axis.</span></span> <span data-ttu-id="653de-116">詳細については、「 [既定メンバーの定義](../attribute-properties-define-a-default-member.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="653de-116">For more information about default members, see [Define a Default Member](../attribute-properties-define-a-default-member.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="653de-117">例</span><span class="sxs-lookup"><span data-stu-id="653de-117">Examples</span></span>  
 <span data-ttu-id="653de-118">次のクエリは、WHERE 句を含んでおらず、すべての年の Internet Sales Amount メジャーの値を返します。</span><span class="sxs-lookup"><span data-stu-id="653de-118">The following query does not include a WHERE clause, and returns the value of the Internet Sales Amount measure for all Calendar Years:</span></span>  
  
```  
SELECT {[Measures].[Internet Sales Amount]} ON COLUMNS,  
[Date].[Calendar Year].MEMBERS ON ROWS  
FROM [Adventure Works]  
```  
  
 <span data-ttu-id="653de-119">これに、WHERE 句を次のように追加します。</span><span class="sxs-lookup"><span data-stu-id="653de-119">Adding a WHERE clause, as follows:</span></span>  
  
```  
SELECT {[Measures].[Internet Sales Amount]} ON COLUMNS,  
[Date].[Calendar Year].MEMBERS ON ROWS  
FROM [Adventure Works]  
WHERE([Customer].[Customer Geography].[Country].&[United States])  
  
```  
  
 <span data-ttu-id="653de-120">クエリの行と列に返される対象は変わりませんが、各セルに返される値は変わります。</span><span class="sxs-lookup"><span data-stu-id="653de-120">does not change what is returned on Rows or Columns in the query; it changes the values returned for each cell.</span></span> <span data-ttu-id="653de-121">この例では、クエリがスライスされて、すべての年の、米国に住む顧客だけに関する Internet Sales Amount の値を返すようになります。WHERE 句には、異なる階層の複数のメンバーを追加できます。</span><span class="sxs-lookup"><span data-stu-id="653de-121">In this example, the query is sliced so that it returns the value of Internet Sales Amount for all Calendar Years but only for Customers who live in the United States.Multiple members from different hierarchies can be added to the WHERE clause.</span></span> <span data-ttu-id="653de-122">次のクエリは、すべての年の、カテゴリ Bikes の製品を購入した、米国に住む顧客に関する Internet Sales Amount の値を表示します。</span><span class="sxs-lookup"><span data-stu-id="653de-122">The following query shows the value of Internet Sales Amount for all Calendar Years for Customers who live in the United States and who bought Products in the Category Bikes:</span></span>  
  
```  
SELECT {[Measures].[Internet Sales Amount]} ON COLUMNS,  
[Date].[Calendar Year].MEMBERS ON ROWS  
FROM [Adventure Works]  
WHERE([Customer].[Customer Geography].[Country].&[United States], [Product].[Category].&[1])  
```  
  
 <span data-ttu-id="653de-123">同じ階層の複数のメンバーを使用する場合は、WHERE 句にセットを含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="653de-123">If you want to use multiple members from the same hierarchy, you need to include a set in the WHERE clause.</span></span> <span data-ttu-id="653de-124">たとえば、次のクエリは、すべての年の、カテゴリ Bikes の製品を購入した、米国およびイギリスに住む顧客に関する Internet Sales Amount の値を表示します。</span><span class="sxs-lookup"><span data-stu-id="653de-124">For example, the following query shows the value of Internet Sales Amount for all Calendar Years for Customers who bought Products in the Category Bikes and live in either the United States or the United Kingdom:</span></span>  
  
```  
SELECT {[Measures].[Internet Sales Amount]} ON COLUMNS,  
[Date].[Calendar Year].MEMBERS ON ROWS  
FROM [Adventure Works]  
WHERE(  
{[Customer].[Customer Geography].[Country].&[United States]  
, [Customer].[Customer Geography].[Country].&[United Kingdom]}  
, [Product].[Category].&[1])  
  
```  
  
 <span data-ttu-id="653de-125">上で説明したように、WHERE 句でセットを使用すると、セット内のすべてのメンバーに関する値が暗黙的に集計されます。</span><span class="sxs-lookup"><span data-stu-id="653de-125">As mentioned above, using a set in the WHERE clause will implicitly aggregate values for all members in the set.</span></span> <span data-ttu-id="653de-126">この例の場合、クエリは各セルに米国とイギリスの集計値を表示します。</span><span class="sxs-lookup"><span data-stu-id="653de-126">In this case, the query shows aggregated values for the United States and the United Kingdom in each cell.</span></span>  
  
  
