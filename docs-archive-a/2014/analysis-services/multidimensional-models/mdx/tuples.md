---
title: タプル |Microsoft Docs
ms.custom: ''
ms.date: 07/17/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 35b629ae-b1ef-44b1-b556-96956aeb56e7
author: minewiskan
ms.author: owend
ms.openlocfilehash: c39d03d60cb66f3b2e26b2e660bd85f4e5e9d4ec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736996"
---
# <a name="tuples"></a><span data-ttu-id="cc4e4-102">タプル</span><span class="sxs-lookup"><span data-stu-id="cc4e4-102">Tuples</span></span>
  <span data-ttu-id="cc4e4-103">組はキューブからデータのスライスを一意に識別します。</span><span class="sxs-lookup"><span data-stu-id="cc4e4-103">A tuple uniquely identifies a slice of data from a cube.</span></span> <span data-ttu-id="cc4e4-104">組は、同じ階層に属するメンバーが複数存在しない限り、ディメンション メンバーを組み合わせて作成されます。</span><span class="sxs-lookup"><span data-stu-id="cc4e4-104">The tuple is formed by a combination of dimension members, as long as there are no two or more members that belong to the same hierarchy.</span></span>  
  
## <a name="implicit-or-default-attribute-members-in-a-tuple"></a><span data-ttu-id="cc4e4-105">組の暗黙的または既定の属性メンバー</span><span class="sxs-lookup"><span data-stu-id="cc4e4-105">Implicit or default attribute members in a tuple</span></span>  
 <span data-ttu-id="cc4e4-106">MDX クエリまたは式で組を定義する際に、すべての属性階層の属性メンバーを明示的に含める必要はありません。</span><span class="sxs-lookup"><span data-stu-id="cc4e4-106">When defining a tuple in an MDX query or expression, you do not need to explicitly include the attribute member from every attribute hierarchy.</span></span> <span data-ttu-id="cc4e4-107">属性階層のメンバーをクエリまたは式に明示的に含めなかった場合、その属性階層の既定のメンバーが暗黙的に組に含められます。</span><span class="sxs-lookup"><span data-stu-id="cc4e4-107">If a member from an attribute hierarchy is not explicitly included in a query or an expression, the default member for that attribute hierarchy is the attribute member implicitly included in the tuple.</span></span> <span data-ttu-id="cc4e4-108">(All) メンバーが存在する場合、キューブで他に明示的に定義されていない限り、(All) メンバーがすべての属性階層の既定のメンバーになります。</span><span class="sxs-lookup"><span data-stu-id="cc4e4-108">Unless otherwise explicitly defined in a cube, the default member for every attribute hierarchy is the (All) member, if an (All) member exists.</span></span> <span data-ttu-id="cc4e4-109">属性階層に (All) メンバーが存在しない場合、属性階層の最上位のメンバーが既定のメンバーになります。</span><span class="sxs-lookup"><span data-stu-id="cc4e4-109">If an (All) member does not exist within an attribute hierarchy, the default member is a member of the attribute hierarchy's top level.</span></span> <span data-ttu-id="cc4e4-110">既定のメジャーを明示的に定義している場合を除き、キューブ内で指定された最初のメジャーが既定のメジャーになります。</span><span class="sxs-lookup"><span data-stu-id="cc4e4-110">The default measure is the first measure specified in the cube, unless a default measure is explicitly defined.</span></span> <span data-ttu-id="cc4e4-111">詳細については、「[既定メンバーの定義](../attribute-properties-define-a-default-member.md)」および「[DefaultMember (MDX)](/sql/mdx/defaultmember-mdx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cc4e4-111">For more information, see [Define a Default Member](../attribute-properties-define-a-default-member.md) and [DefaultMember &#40;MDX&#41;](/sql/mdx/defaultmember-mdx).</span></span>  
  
 <span data-ttu-id="cc4e4-112">たとえば、次の組はメジャー ディメンションの単一のメンバーのみを明示的に定義することで、Adventure Works データベースの 1 つのセルを識別しています。</span><span class="sxs-lookup"><span data-stu-id="cc4e4-112">For example, the following tuple identifies a single cell in the Adventure Works database by explicitly defining only a single member of the Measures dimension.</span></span>  
  
```  
(Measures.[Reseller Sales Amount])  
```  
  
 <span data-ttu-id="cc4e4-113">上記の例は、メジャー ディメンションの Reseller Sales Amount メンバーとキューブに所属するすべての属性階層の既定のメンバーから構成されるセルを一意に識別します。</span><span class="sxs-lookup"><span data-stu-id="cc4e4-113">The previous example uniquely identifies the cell consisting of the Reseller Sales Amount member from the Measures dimension and the default member from every attribute hierarchy in the cube.</span></span> <span data-ttu-id="cc4e4-114">Destination Currency 属性階層を除くすべての属性階層の既定のメンバーは (All) メンバーです。</span><span class="sxs-lookup"><span data-stu-id="cc4e4-114">The default member is the (All) member for every attribute hierarchy other than the Destination Currency attribute hierarchy.</span></span> <span data-ttu-id="cc4e4-115">Destination Currency 階層の既定のメンバーは US Dollar メンバーです (この既定のメンバーは Adventure Works キューブの MDX スクリプトで定義されています)。</span><span class="sxs-lookup"><span data-stu-id="cc4e4-115">The default member for the Destination Currency hierarchy is the US Dollar member (this default member is defined in the MDX script for the Adventure Works cube).</span></span>  
  
 <span data-ttu-id="cc4e4-116">次のクエリは、上記の例で指定した組が参照するセルの値 ($80,450.596.98) を返します。</span><span class="sxs-lookup"><span data-stu-id="cc4e4-116">The following query returns the value for the cell referenced by the tuple specified in the previous example, ($80,450.596.98).</span></span>  
  
```  
SELECT   
Measures.[Reseller Sales Amount] ON COLUMNS   
FROM [Adventure Works]  
```  
  
> [!NOTE]  
>  <span data-ttu-id="cc4e4-117">クエリでセット (ここでは、1 つの組から構成されます) の軸を指定するときは、行の軸のセットを指定する前に列の軸のセットを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cc4e4-117">When you specify an axis for a set (in this case composed of a single tuple) in a query, you must begin by specifying a set for the column axis before specifying a set for the row axis.</span></span> <span data-ttu-id="cc4e4-118">列の軸は、 *axis(0)* 、または単に *0*とも表現できます。</span><span class="sxs-lookup"><span data-stu-id="cc4e4-118">The column axis can also be referred to as *axis(0)* or simply *0*.</span></span> <span data-ttu-id="cc4e4-119">MDX クエリの詳細については、「[MDX の基本的なクエリ (MDX)](mdx-query-the-basic-query.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cc4e4-119">For more information about MDX queries, see [The Basic MDX Query &#40;MDX&#41;](mdx-query-the-basic-query.md).</span></span>  
  
### <a name="tuples-as-values-or-member-references"></a><span data-ttu-id="cc4e4-120">値またはメンバー参照としての組</span><span class="sxs-lookup"><span data-stu-id="cc4e4-120">Tuples as values or member references</span></span>  
 <span data-ttu-id="cc4e4-121">上記の例のように、クエリで組を使用して、その組が参照しているセルの値を取得できます。</span><span class="sxs-lookup"><span data-stu-id="cc4e4-121">You can use a tuple in a query to return the value in the cell that is referenced by the tuple, as in the previous example.</span></span> <span data-ttu-id="cc4e4-122">また、式で組を使用して、組で指定されているメンバーを明示的に参照できます。</span><span class="sxs-lookup"><span data-stu-id="cc4e4-122">Or you can use a tuple in an expression to explicitly refer to the members specified in the tuple.</span></span> <span data-ttu-id="cc4e4-123">組を取得または使用する関数をクエリまたは式で使用できます。</span><span class="sxs-lookup"><span data-stu-id="cc4e4-123">The query or the expression can utilize functions that either return or consume tuples.</span></span> <span data-ttu-id="cc4e4-124">組を使用して、組で指定されているセルの値を参照できます。また、関数内で使用する場合はメンバーの組み合わせを指定できます。</span><span class="sxs-lookup"><span data-stu-id="cc4e4-124">A tuple can be used to either refer to the value of the cell that the tuple specifies, or to specify a combination of members when utilized in a function.</span></span>  
  
### <a name="tuple-dimensionality"></a><span data-ttu-id="cc4e4-125">組の次元</span><span class="sxs-lookup"><span data-stu-id="cc4e4-125">Tuple dimensionality</span></span>  
 <span data-ttu-id="cc4e4-126">組の中のメンバーの並びまたは順序を組の *次元* といいます。</span><span class="sxs-lookup"><span data-stu-id="cc4e4-126">The *dimensionality* of a tuple refers to the sequence or order of the members in the tuple.</span></span> <span data-ttu-id="cc4e4-127">暗黙的なメンバーの出現順序は常に変わらないので、通常は組の中で明示的に定義されているメンバーについて次元を考えます。</span><span class="sxs-lookup"><span data-stu-id="cc4e4-127">Since the implicit members always occur in the same order, dimensionality is most often thought of in terms of the explicitly defined members of the tuple.</span></span> <span data-ttu-id="cc4e4-128">組のメンバーの順序は、組のセットを定義するときに重要です。</span><span class="sxs-lookup"><span data-stu-id="cc4e4-128">The ordering of the members of the tuple is important when you define a set of tuples.</span></span> <span data-ttu-id="cc4e4-129">次の例では、列の軸となる組で 2 つのメンバーが使用されています。</span><span class="sxs-lookup"><span data-stu-id="cc4e4-129">The following example includes two members in a tuple on the column axis.</span></span>  
  
```  
SELECT   
([Measures].[Reseller Sales Amount],[Date].[Calendar Year].[CY 2004]) ON COLUMNS   
FROM [Adventure Works]  
```  
  
> [!NOTE]  
>  <span data-ttu-id="cc4e4-130">複数のディメンションから構成される組のメンバーを明示的に指定するときは、組全体をかっこで囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="cc4e4-130">When you explicitly specify a member in a tuple from more than one dimension, you must include the entire tuple in parentheses.</span></span> <span data-ttu-id="cc4e4-131">組のメンバー 1 つのみを指定する場合、かっこの使用は任意です。</span><span class="sxs-lookup"><span data-stu-id="cc4e4-131">When only specifying a single member in a tuple, parentheses are optional.</span></span>  
  
 <span data-ttu-id="cc4e4-132">上記の例のクエリで使用している組は、メジャー ディメンションの Reseller Sales Amount メジャーと Date ディメンションの Calendar Year 属性階層の CY 2004 メンバーが交差するキューブ セルを返すよう指定しています。</span><span class="sxs-lookup"><span data-stu-id="cc4e4-132">The tuple in the query in the previous example specifies the return of the cube cell at the intersection of the Reseller Sales Amount Measure of the Measures dimension and the CY 2004 member of the Calendar Year attribute hierarchy in the Date dimension.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cc4e4-133">属性メンバーは、メンバー名またはメンバー キーで参照できます。</span><span class="sxs-lookup"><span data-stu-id="cc4e4-133">An attribute member can be referred by either its member name or its member key.</span></span> <span data-ttu-id="cc4e4-134">上記の例で、[CY 2004] への参照を &[2004] としてもかまいません。</span><span class="sxs-lookup"><span data-stu-id="cc4e4-134">In the previous example, you could replace the reference to [CY 2004] with &[2004].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc4e4-135">参照</span><span class="sxs-lookup"><span data-stu-id="cc4e4-135">See Also</span></span>  
 <span data-ttu-id="cc4e4-136">[MDX &#40;Analysis Services の主な概念&#41;](../key-concepts-in-mdx-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="cc4e4-136">[Key Concepts in MDX &#40;Analysis Services&#41;](../key-concepts-in-mdx-analysis-services.md) </span></span>  
 <span data-ttu-id="cc4e4-137">[キューブ空間](cube-space.md) </span><span class="sxs-lookup"><span data-stu-id="cc4e4-137">[Cube Space](cube-space.md) </span></span>  
 <span data-ttu-id="cc4e4-138">[Autoexists](autoexists.md) </span><span class="sxs-lookup"><span data-stu-id="cc4e4-138">[Autoexists](autoexists.md) </span></span>  
 [<span data-ttu-id="cc4e4-139">メンバー、組、およびセットの操作 (MDX)</span><span class="sxs-lookup"><span data-stu-id="cc4e4-139">Working with Members, Tuples, and Sets &#40;MDX&#41;</span></span>](working-with-members-tuples-and-sets-mdx.md)  
  
  
