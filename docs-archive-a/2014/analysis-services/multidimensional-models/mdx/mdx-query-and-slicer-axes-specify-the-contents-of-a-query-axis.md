---
title: クエリ軸の内容の指定 (MDX) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- cellsets [MDX]
- query axis [MDX]
ms.assetid: c745ade0-738e-4a98-a3f0-3eabfd3eeba2
author: minewiskan
ms.author: owend
ms.openlocfilehash: 28fd867b8f8caaf74e4dd704753c354368da2e89
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718771"
---
# <a name="specifying-the-contents-of-a-query-axis-mdx"></a><span data-ttu-id="a8e8c-102">クエリ軸の内容の指定 (MDX)</span><span class="sxs-lookup"><span data-stu-id="a8e8c-102">Specifying the Contents of a Query Axis (MDX)</span></span>
  <span data-ttu-id="a8e8c-103">クエリ軸は、多次元式 (MDX) の SELECT ステートメントから返されるセル セットの範囲を指定します。</span><span class="sxs-lookup"><span data-stu-id="a8e8c-103">Query axes specify the edges of a cellset returned by a Multidimensional Expressions (MDX) SELECT statement.</span></span> <span data-ttu-id="a8e8c-104">セル セットの範囲を指定することで、返されるデータのうち、クライアントで表示するデータを限定できます。</span><span class="sxs-lookup"><span data-stu-id="a8e8c-104">Specifying the edges of a cellset lets you restrict the returned data that is visible to the client.</span></span>  
  
 <span data-ttu-id="a8e8c-105">クエリ軸を指定するには、 `<SELECT query axis clause>` を使用して特定のクエリ軸にセットを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="a8e8c-105">To specify query axes, you use the `<SELECT query axis clause>` to assign a set to a particular query axis.</span></span> <span data-ttu-id="a8e8c-106">それぞれの `<SELECT query axis clause>` の値によって、1 つのクエリ軸を定義します。</span><span class="sxs-lookup"><span data-stu-id="a8e8c-106">Each `<SELECT query axis clause>` value defines one query axis.</span></span> <span data-ttu-id="a8e8c-107">データセットの軸の数は、SELECT ステートメントの `<SELECT query axis clause>` 値の数と同じです。</span><span class="sxs-lookup"><span data-stu-id="a8e8c-107">The number of axes in the dataset is equal to the number of `<SELECT query axis clause>` values in the SELECT statement.</span></span>  
  
## <a name="query-axis-syntax"></a><span data-ttu-id="a8e8c-108">クエリ軸の構文</span><span class="sxs-lookup"><span data-stu-id="a8e8c-108">Query Axis Syntax</span></span>  
 <span data-ttu-id="a8e8c-109">`<SELECT query axis clause>`の構文は以下のとおりです。</span><span class="sxs-lookup"><span data-stu-id="a8e8c-109">The following syntax shows the syntax for the `<SELECT query axis clause>`:</span></span>  
  
```  
  
<SELECT query axis clause> ::=  
   [ NON EMPTY ] Set_Expression [ <SELECT dimension property list clause> ] [<HAVING clause>]  
   ON {  
      Integer_Expression |   
      AXIS( Integer_Expression ) |   
      {COLUMNS | ROWS | PAGES | SECTIONS | CHAPTERS}     
      }  
  
```  
  
 <span data-ttu-id="a8e8c-110">各クエリ軸には番号が付いており、0 は X 軸、1 は Y 軸、2 は Z 軸のようになっています。</span><span class="sxs-lookup"><span data-stu-id="a8e8c-110">Each query axis has a number: zero (0) for the x-axis, 1 for the y-axis, 2 for the z-axis, and so on.</span></span> <span data-ttu-id="a8e8c-111">`<SELECT query axis clause>`の構文では、 `Integer_Expression` の値によって軸の番号を指定します。</span><span class="sxs-lookup"><span data-stu-id="a8e8c-111">In the syntax for the `<SELECT query axis clause>`, the `Integer_Expression` value specifies the axis number.</span></span> <span data-ttu-id="a8e8c-112">MDX クエリでは、最大 128 個まで軸を指定できます。ただし、5 つを超える軸を使用する MDX クエリはほとんどありません。</span><span class="sxs-lookup"><span data-stu-id="a8e8c-112">An MDX query can support up to 128 specified axes, but very few MDX queries will use more than 5 axes.</span></span> <span data-ttu-id="a8e8c-113">最初の 5 つの軸については、COLUMNS、ROWS、PAGES、SECTIONS、CHAPTERS という別名を使用することも可能です。</span><span class="sxs-lookup"><span data-stu-id="a8e8c-113">For the first 5 axes, the aliases COLUMNS, ROWS, PAGES, SECTIONS, and CHAPTERS can instead be used.</span></span>  
  
 <span data-ttu-id="a8e8c-114">MDX クエリは、クエリ軸をスキップできません。</span><span class="sxs-lookup"><span data-stu-id="a8e8c-114">An MDX query cannot skip query axes.</span></span> <span data-ttu-id="a8e8c-115">つまり、1 つ以上のクエリ軸を含むクエリでは、番号の小さい方の軸または中間の軸を除外できません。</span><span class="sxs-lookup"><span data-stu-id="a8e8c-115">That is, a query that includes one or more query axes must not exclude lower-numbered or intermediate axes.</span></span> <span data-ttu-id="a8e8c-116">たとえば、クエリで COLUMNS 軸を除外して ROWS 軸を指定することや、ROWS 軸を除外して COLUMNS 軸と PAGES 軸を指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="a8e8c-116">For example, a query cannot have a ROWS axis without a COLUMNS axis, or have COLUMNS and PAGES axes without a ROWS axis.</span></span>  
  
 <span data-ttu-id="a8e8c-117">ただし、軸を指定しない SELECT 句、つまり空の SELECT 句は指定できます。</span><span class="sxs-lookup"><span data-stu-id="a8e8c-117">However, you can specify a SELECT clause without any axes (that is, an empty SELECT clause).</span></span> <span data-ttu-id="a8e8c-118">この場合、すべてのディメンションがスライサー ディメンションになり、MDX クエリは 1 つのセルを選択します。</span><span class="sxs-lookup"><span data-stu-id="a8e8c-118">In this case, all dimensions are slicer dimensions, and the MDX query selects one cell.</span></span>  
  
 <span data-ttu-id="a8e8c-119">上記のクエリ軸の構文では、 `Set_Expression` の値によって、クエリ軸の内容を定義するセットを指定します。</span><span class="sxs-lookup"><span data-stu-id="a8e8c-119">In the query axis syntax previously shown, each `Set_Expression` value specifies the set that defines the contents of the query axis.</span></span> <span data-ttu-id="a8e8c-120">セットの詳細については、「[メンバー、組、およびセットの操作 &#40;MDX&#41;](working-with-members-tuples-and-sets-mdx.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a8e8c-120">For more information about sets, see [Working with Members, Tuples, and Sets &#40;MDX&#41;](working-with-members-tuples-and-sets-mdx.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="a8e8c-121">例</span><span class="sxs-lookup"><span data-stu-id="a8e8c-121">Examples</span></span>  
 <span data-ttu-id="a8e8c-122">次の単純な SELECT ステートメントは、COLUMNS 軸で Internet Sales Amount メジャーを返し、MDX の MEMBERS 関数を使って、ROWS 軸で Date ディメンションの Calendar 階層のすべてのメンバーを返します。</span><span class="sxs-lookup"><span data-stu-id="a8e8c-122">The following simple SELECT statement returns the measure Internet Sales Amount on the Columns axis, and uses the MDX MEMBERS function to return all the members from the Calendar hierarchy on the Date dimension on the Rows axis:</span></span>  
  
```  
SELECT {[Measures].[Internet Sales Amount]} ON COLUMNS,  
{[Date].[Calendar].MEMBERS} ON ROWS  
FROM [Adventure Works]  
  
```  
  
 <span data-ttu-id="a8e8c-123">以下の 2 つのクエリは、まったく同じ結果を返しますが、軸の別名ではなく番号を使用する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="a8e8c-123">The two following queries return exactly the same results but demonstrate the use of axis numbers rather than aliases:</span></span>  
  
```  
SELECT {[Measures].[Internet Sales Amount]} ON 0,  
{[Date].[Calendar].MEMBERS} ON 1  
FROM [Adventure Works]  
  
SELECT {[Measures].[Internet Sales Amount]} ON AXIS(0),  
{[Date].[Calendar].MEMBERS} ON AXIS(1)  
FROM [Adventure Works]  
  
```  
  
 <span data-ttu-id="a8e8c-124">セットの定義の前に NON EMPTY キーワードを使用すると、軸からすべての空の組を簡単に削除できます。</span><span class="sxs-lookup"><span data-stu-id="a8e8c-124">The NON EMPTY keyword, used before the set definition, is an easy way to remove all empty tuples from an axis.</span></span> <span data-ttu-id="a8e8c-125">たとえば、ここまでの例では、2004年8月以降のデータはキューブに含まれていません。</span><span class="sxs-lookup"><span data-stu-id="a8e8c-125">For example, in the examples we've seen so far there is no data in the cube from August 2004 onwards.</span></span> <span data-ttu-id="a8e8c-126">どの列にもデータがないすべての行をセルセットから削除するには、ROWS 軸のセットの定義の前に、以下のように NON EMPTY を追加します。</span><span class="sxs-lookup"><span data-stu-id="a8e8c-126">To remove all rows from the cellset that have no data in any column, simply add NON EMPTY before the set on the Rows axis definition as follows:</span></span>  
  
```  
SELECT {[Measures].[Internet Sales Amount]} ON COLUMNS,  
NON EMPTY  
{[Date].[Calendar].MEMBERS} ON ROWS  
FROM [Adventure Works]  
  
```  
  
 <span data-ttu-id="a8e8c-127">NON EMPTY は、クエリのすべての軸で使用できます。</span><span class="sxs-lookup"><span data-stu-id="a8e8c-127">NON EMPTY can be used on all axes in a query.</span></span> <span data-ttu-id="a8e8c-128">以下の 2 つのクエリの結果を比較してみましょう。最初のクエリは NON EMPTY を使っておらず、2 番目のクエリでは両方の軸で使用しています。</span><span class="sxs-lookup"><span data-stu-id="a8e8c-128">Compare the results of the following two queries, the first of which does not use NON EMPTY and the second of which does on both axes:</span></span>  
  
```  
SELECT {[Measures].[Internet Sales Amount]}   
* [Promotion].[Promotion].[Promotion].MEMBERS  
ON COLUMNS,  
{[Date].[Calendar].[Calendar Year].MEMBERS} ON ROWS  
FROM [Adventure Works]  
WHERE([Product].[Subcategory].&[19])  
  
SELECT NON EMPTY {[Measures].[Internet Sales Amount]}   
* [Promotion].[Promotion].[Promotion].MEMBERS  
ON COLUMNS,  
NON EMPTY  
{[Date].[Calendar].[Calendar Year].MEMBERS} ON ROWS  
FROM [Adventure Works]  
WHERE([Product].[Subcategory].&[19])  
  
```  
  
 <span data-ttu-id="a8e8c-129">軸の内容を特定の条件に基づいてフィルター選択するために、HAVING 句を使用できます。FILTER 関数のような、同じ結果が得られる他の方法ほど柔軟性がありませんが、使用方法が簡単です。</span><span class="sxs-lookup"><span data-stu-id="a8e8c-129">The HAVING clause can be used to filter the contents of an axis based on a specific criteria; it is less flexible than other methods that can achieve the same results, such as the FILTER function, but it is simpler to use.</span></span> <span data-ttu-id="a8e8c-130">次の例は、Internet Sales Amount が 15,000 ドルより大きい日付だけを返します。</span><span class="sxs-lookup"><span data-stu-id="a8e8c-130">Here is an example that returns only those dates where Internet Sales Amount is greater than $15,000:</span></span>  
  
```  
SELECT {[Measures].[Internet Sales Amount]}   
ON COLUMNS,  
NON EMPTY  
{[Date].[Calendar].[Date].MEMBERS}   
HAVING [Measures].[Internet Sales Amount]>15000  
ON ROWS  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="a8e8c-131">参照</span><span class="sxs-lookup"><span data-stu-id="a8e8c-131">See Also</span></span>  
 [<span data-ttu-id="a8e8c-132">スライサー軸の内容の指定 &#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="a8e8c-132">Specifying the Contents of a Slicer Axis &#40;MDX&#41;</span></span>](mdx-query-and-slicer-axes-specify-the-contents-of-a-slicer-axis.md)  
  
  
