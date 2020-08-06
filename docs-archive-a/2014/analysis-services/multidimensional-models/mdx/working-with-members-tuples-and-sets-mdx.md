---
title: メンバー、組、およびセットの操作 (MDX) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- MDX [Analysis Services], tuples
- member keys [MDX]
- MDX [Analysis Services], sets
- calculated members [MDX]
- members [MDX]
- Multidimensional Expressions [Analysis Services], members
- named sets [MDX]
- Multidimensional Expressions [Analysis Services], tuples
- member functions [MDX]
- sets [MDX]
- MDX [Analysis Services], members
- member names [MDX]
- Multidimensional Expressions [Analysis Services], sets
- tuple functions
- tuples
- set functions [MDX]
ms.assetid: b6ec2439-caef-46d3-9fd7-5f4526cee334
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5ce3bf2d5ad7df2b1cd74897b3b49c7cef97e8ed
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632140"
---
# <a name="working-with-members-tuples-and-sets-mdx"></a><span data-ttu-id="aebf2-102">メンバー、組、およびセットの操作 (MDX)</span><span class="sxs-lookup"><span data-stu-id="aebf2-102">Working with Members, Tuples, and Sets (MDX)</span></span>
  <span data-ttu-id="aebf2-103">MDX には、1 つ以上のメンバー、組、またはセットを返す操作や、メンバー、組、またはセットに対する操作を行うための関数が各種用意されています。</span><span class="sxs-lookup"><span data-stu-id="aebf2-103">MDX provides numerous functions that return one or more members, tuples, or sets; or that act upon a member, tuple, or set.</span></span>  
  
## <a name="member-functions"></a><span data-ttu-id="aebf2-104">メンバー関数</span><span class="sxs-lookup"><span data-stu-id="aebf2-104">Member Functions</span></span>  
 <span data-ttu-id="aebf2-105">MDX には、ディメンション、レベル、セット、組などの他の MDX エンティティからメンバーを取得するための関数がいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="aebf2-105">MDX provides several functions for retrieving members from other MDX entities, such as from dimensions, levels, sets, or tuples.</span></span> <span data-ttu-id="aebf2-106">たとえば、 [FirstChild](/sql/mdx/firstchild-mdx) 関数はメンバーに対して操作を実行してメンバーを返す関数です。</span><span class="sxs-lookup"><span data-stu-id="aebf2-106">For example, the [FirstChild](/sql/mdx/firstchild-mdx) function is a function that acts upon a member and returns a member.</span></span>  
  
 <span data-ttu-id="aebf2-107">時間ディメンションの最初の子メンバーを取得するには、次の例のように、明示的にメンバーを指定できます。</span><span class="sxs-lookup"><span data-stu-id="aebf2-107">To obtain the first child member of the Time dimension, you can explicitly state the member, as in the following example.</span></span>  
  
```  
SELECT [Date].[Calendar Year].[CY 2001] on 0  
FROM [Adventure Works]  
  
```  
  
 <span data-ttu-id="aebf2-108">または、次の例のように、`FirstChild` 関数を使用して同じメンバーを返すこともできます。</span><span class="sxs-lookup"><span data-stu-id="aebf2-108">You can also use the `FirstChild` function to return the same member, as in the following example.</span></span>  
  
```  
SELECT [Date].[Calendar Year].FirstChild on 0  
FROM [Adventure Works]  
  
```  
  
 <span data-ttu-id="aebf2-109">MDX メンバー関数の詳細については、「 [MDX 関数リファレンス &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="aebf2-109">For more information about MDX member functions, see [MDX Function Reference &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx).</span></span>  
  
## <a name="tuple-functions"></a><span data-ttu-id="aebf2-110">組関数</span><span class="sxs-lookup"><span data-stu-id="aebf2-110">Tuple Functions</span></span>  
 <span data-ttu-id="aebf2-111">MDX には、組を返す関数がいくつかあります。これらの関数は、組を使用できる任意の箇所で使用できます。</span><span class="sxs-lookup"><span data-stu-id="aebf2-111">MDX provides several functions that return tuples, and they can be used anywhere that a tuple is accepted.</span></span> <span data-ttu-id="aebf2-112">たとえば、[Item &#40;組&#41; &#40;MDX&#41;](/sql/mdx/item-tuple-mdx) 関数はセットから最初の組を抽出するために使用できます。これは、セットに含まれているのが単一の組であるとわかっており、組を 1 つ必要とする関数にその組を渡す場合に非常に便利です。</span><span class="sxs-lookup"><span data-stu-id="aebf2-112">For example, the [Item &#40;Tuple&#41; &#40;MDX&#41;](/sql/mdx/item-tuple-mdx) function can be used to extract the first tuple from set, which is very useful when you know that a set is composed of a single tuple and you want to supply that tuple to a function that requires a tuple.</span></span>  
  
 <span data-ttu-id="aebf2-113">次の例では、列軸上の組のセット内から最初の組を返します。</span><span class="sxs-lookup"><span data-stu-id="aebf2-113">The following example returns the first tuple from within the set of tuples on the column axis.</span></span>  
  
```  
SELECT {  
   ([Measures].[Reseller Sales Amount]  
      ,[Date].[Calendar Year].[CY 2003]  
   )  
, ([Measures].[Reseller Sales Amount]  
      ,[Date].[Calendar Year].[CY 2004]  
   )  
}.Item(0)  
ON COLUMNS   
FROM [Adventure Works]  
```  
  
 <span data-ttu-id="aebf2-114">組関数の詳細については、「 [MDX 関数リファレンス &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="aebf2-114">For more information about tuple functions, see [MDX Function Reference &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx).</span></span>  
  
## <a name="set-functions"></a><span data-ttu-id="aebf2-115">集合関数</span><span class="sxs-lookup"><span data-stu-id="aebf2-115">Set Functions</span></span>  
 <span data-ttu-id="aebf2-116">MDX には、セットを返す関数がいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="aebf2-116">MDX provides several functions that return sets.</span></span> <span data-ttu-id="aebf2-117">セットを取得する方法は、明示的に組を入力して中かっこで囲むだけではありません。</span><span class="sxs-lookup"><span data-stu-id="aebf2-117">Explicitly typing tuples and enclosing them in braces is not the only way to retrieve a set.</span></span> <span data-ttu-id="aebf2-118">セットを返すメンバー関数の詳細については、「 [MDX の主な概念 &#40;Analysis Services&#41;](../key-concepts-in-mdx-analysis-services.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="aebf2-118">For more information about the members function to return a set, see [Key Concepts in MDX &#40;Analysis Services&#41;](../key-concepts-in-mdx-analysis-services.md).</span></span> <span data-ttu-id="aebf2-119">他にも多くのセット関数があります。</span><span class="sxs-lookup"><span data-stu-id="aebf2-119">There are many additional set functions.</span></span>  
  
 <span data-ttu-id="aebf2-120">コロン演算子を使用すれば、メンバーの順序を指定してセットを作成できます。</span><span class="sxs-lookup"><span data-stu-id="aebf2-120">The colon operator lets you use the natural order of members to create a set.</span></span> <span data-ttu-id="aebf2-121">たとえば、次の例のセットには、2002 年度の第 1 四半期から第 4 四半期までの組が含まれます。</span><span class="sxs-lookup"><span data-stu-id="aebf2-121">For example, the set shown in the following example contains tuples for the 1st through the 4th quarter of calendar year 2002.</span></span>  
  
```  
SELECT   
   {[Calendar Quarter].[Q1 CY 2002]:[Calendar Quarter].[Q4 CY 2002]}   
ON 0  
FROM [Adventure Works]  
```  
  
 <span data-ttu-id="aebf2-122">コロン演算子を使用してセットを作成しない場合は、次の例のような組を指定することで、同じメンバー セットを作成できます。</span><span class="sxs-lookup"><span data-stu-id="aebf2-122">If you do not use the colon operator to create the set, you can create the same set of members by specifying the tuples in the following example.</span></span>  
  
```  
SELECT {  
   [Calendar Quarter].[Q1 CY 2002],   
   [Calendar Quarter].[Q2 CY 2002],   
   [Calendar Quarter].[Q3 CY 2002],   
   [Calendar Quarter].[Q4 CY 2002]  
   } ON 0  
FROM [Adventure Works]  
  
```  
  
 <span data-ttu-id="aebf2-123">コロン演算子は内包的な関数です。</span><span class="sxs-lookup"><span data-stu-id="aebf2-123">The colon operator is an inclusive function.</span></span> <span data-ttu-id="aebf2-124">コロン演算子の両側のメンバーはどちらも結果セットに含まれます。</span><span class="sxs-lookup"><span data-stu-id="aebf2-124">The members on both sides of the colon operator are included in the resulting set.</span></span>  
  
 <span data-ttu-id="aebf2-125">セット関数の詳細については、「 [MDX 関数リファレンス &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="aebf2-125">For more information about set functions, see [MDX Function Reference &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx).</span></span>  
  
## <a name="array-functions"></a><span data-ttu-id="aebf2-126">配列関数</span><span class="sxs-lookup"><span data-stu-id="aebf2-126">Array Functions</span></span>  
 <span data-ttu-id="aebf2-127">配列関数は、セットに対して操作を実行して配列を返します。</span><span class="sxs-lookup"><span data-stu-id="aebf2-127">An array function acts upon a set and returns an array.</span></span> <span data-ttu-id="aebf2-128">配列関数の詳細については、「 [MDX 関数リファレンス &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="aebf2-128">For more information about array functions, see [MDX Function Reference &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx).</span></span>  
  
## <a name="hierarchy-functions"></a><span data-ttu-id="aebf2-129">階層関数</span><span class="sxs-lookup"><span data-stu-id="aebf2-129">Hierarchy Functions</span></span>  
 <span data-ttu-id="aebf2-130">階層関数は、メンバー、レベル、階層、または文字列に対して操作を実行して、階層を返します。</span><span class="sxs-lookup"><span data-stu-id="aebf2-130">A hierarchy function returns a hierarchy by acting upon a member, level, hierarchy, or string.</span></span> <span data-ttu-id="aebf2-131">階層関数の詳細については、「 [MDX 関数リファレンス &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="aebf2-131">For more information about hierarchy functions, see [MDX Function Reference &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx).</span></span>  
  
## <a name="level-functions"></a><span data-ttu-id="aebf2-132">レベル関数</span><span class="sxs-lookup"><span data-stu-id="aebf2-132">Level Functions</span></span>  
 <span data-ttu-id="aebf2-133">レベル関数は、メンバー、レベル、または文字列に対して操作を実行して、レベルを返します。</span><span class="sxs-lookup"><span data-stu-id="aebf2-133">A level function returns a level by acting upon a member, level, or string.</span></span> <span data-ttu-id="aebf2-134">レベル関数の詳細については、「 [MDX 関数リファレンス &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="aebf2-134">For more information about level functions, see [MDX Function Reference &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx).</span></span>  
  
## <a name="logical-functions"></a><span data-ttu-id="aebf2-135">論理関数</span><span class="sxs-lookup"><span data-stu-id="aebf2-135">Logical Functions</span></span>  
 <span data-ttu-id="aebf2-136">論理関数は、MDX 式に対して操作を実行し、その式の組、メンバー、またはセットに関する情報を返します。</span><span class="sxs-lookup"><span data-stu-id="aebf2-136">A logical function acts upon a MDX expression to return information about the tuples, members, or sets in the expression.</span></span> <span data-ttu-id="aebf2-137">たとえば、[IsEmpty &#40;MDX&#41;](/sql/mdx/isempty-mdx) 関数は、式から空のセル値が返されるかどうかを評価します。</span><span class="sxs-lookup"><span data-stu-id="aebf2-137">For example, the [IsEmpty &#40;MDX&#41;](/sql/mdx/isempty-mdx) function evaluates whether an expression has returned an empty cell value.</span></span> <span data-ttu-id="aebf2-138">論理関数の詳細については、「 [MDX 関数リファレンス &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="aebf2-138">For more information about logical functions, see [MDX Function Reference &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx).</span></span>  
  
## <a name="numeric-functions"></a><span data-ttu-id="aebf2-139">数値関数</span><span class="sxs-lookup"><span data-stu-id="aebf2-139">Numeric Functions</span></span>  
 <span data-ttu-id="aebf2-140">数値関数は、MDX 式に対して操作を実行してスカラー値を返します。</span><span class="sxs-lookup"><span data-stu-id="aebf2-140">A numeric function acts upon a MDX expression to return a scalar value.</span></span> <span data-ttu-id="aebf2-141">たとえば、[Aggregate &#40;MDX&#41;](/sql/mdx/aggregate-mdx) 関数は、指定されたセットの組に対し、メジャーを集計することで計算されるスカラー値を返します。</span><span class="sxs-lookup"><span data-stu-id="aebf2-141">For example, the [Aggregate &#40;MDX&#41;](/sql/mdx/aggregate-mdx) function returns a scalar value calculated by aggregating measures over the tuples in a specified set.</span></span> <span data-ttu-id="aebf2-142">数値関数の詳細については、「 [MDX 関数リファレンス &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="aebf2-142">For more information about numeric functions, see [MDX Function Reference &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx).</span></span>  
  
## <a name="string-functions"></a><span data-ttu-id="aebf2-143">文字列関数</span><span class="sxs-lookup"><span data-stu-id="aebf2-143">String Functions</span></span>  
 <span data-ttu-id="aebf2-144">文字列関数は、MDX 式に対して操作を実行して文字列を返します。</span><span class="sxs-lookup"><span data-stu-id="aebf2-144">A string function acts upon a MDX expression to return a string.</span></span> <span data-ttu-id="aebf2-145">たとえば、[UniqueName &#40;MDX&#41;](/sql/mdx/uniquename-mdx) 関数は、ディメンション、階層、レベル、メンバーの一意の名前を格納した文字列値を返します。</span><span class="sxs-lookup"><span data-stu-id="aebf2-145">For example, the [UniqueName &#40;MDX&#41;](/sql/mdx/uniquename-mdx) function returns a string value containing the unique name of a dimension, hierarchy, level, or member.</span></span> <span data-ttu-id="aebf2-146">文字列関数の詳細については、「 [MDX 関数リファレンス &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="aebf2-146">For more information about string functions, see [MDX Function Reference &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aebf2-147">参照</span><span class="sxs-lookup"><span data-stu-id="aebf2-147">See Also</span></span>  
 <span data-ttu-id="aebf2-148">[MDX &#40;Analysis Services の主な概念&#41;](../key-concepts-in-mdx-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="aebf2-148">[Key Concepts in MDX &#40;Analysis Services&#41;](../key-concepts-in-mdx-analysis-services.md) </span></span>  
 <span data-ttu-id="aebf2-149">[MDX クエリの基礎 &#40;Analysis Services&#41;](mdx-query-fundamentals-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="aebf2-149">[MDX Query Fundamentals &#40;Analysis Services&#41;](mdx-query-fundamentals-analysis-services.md) </span></span>  
 [<span data-ttu-id="aebf2-150">MDX 関数リファレンス &#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="aebf2-150">MDX Function Reference &#40;MDX&#41;</span></span>](/sql/mdx/mdx-function-reference-mdx)  
  
  
