---
title: キューブ空間 |Microsoft Docs
ms.custom: ''
ms.date: 07/17/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: c3a012b4-9ca0-4fb8-9c26-5ecc0e2e2b2b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0a6a6da73815f06aa5ab80f6ad5a9d06227ed842
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639705"
---
# <a name="cube-space"></a><span data-ttu-id="ba66f-102">キューブ空間</span><span class="sxs-lookup"><span data-stu-id="ba66f-102">Cube Space</span></span>
  <span data-ttu-id="ba66f-103">キューブ空間は、そのキューブのメジャーを伴った、キューブの属性階層のメンバーから構成されます。</span><span class="sxs-lookup"><span data-stu-id="ba66f-103">Cube space is the product of the members of a cube's attribute hierarchies with the cube's measures.</span></span> <span data-ttu-id="ba66f-104">したがって、キューブ空間はキューブ内のすべての属性階層のメンバーとキューブのメジャーの組み合わせによって決まり、キューブの最大サイズを定義します。</span><span class="sxs-lookup"><span data-stu-id="ba66f-104">Therefore, the cube space is determined by the combinatorial product of all attribute hierarchy members in the cube and the cube's measures and defines the maximum size of the cube.</span></span> <span data-ttu-id="ba66f-105">重要なのは、この空間には属性階層メンバーで考えられるすべての組み合わせが含まれるということです。現実世界において不可能と考えられるような組み合わせ (たとえば、都市を Paris、国を England、Spain、Japan、India などに指定する) も含まれます。</span><span class="sxs-lookup"><span data-stu-id="ba66f-105">It is important to note that this space includes all possible combinations of attribute hierarchy members; even combinations that might be deem as impossible in the real world i.e. combinations where the city is Paris and the countries are England or Spain or Japan or India or elsewhere.</span></span>  
  
## <a name="autoexists-and-cube-space"></a><span data-ttu-id="ba66f-106">Autoexists とキューブ空間</span><span class="sxs-lookup"><span data-stu-id="ba66f-106">Autoexists and cube space</span></span>  
 <span data-ttu-id="ba66f-107">*autoexists* の概念を導入すると、このキューブ空間を、実際に存在するセルのみに限定できます。</span><span class="sxs-lookup"><span data-stu-id="ba66f-107">The concept of *autoexists* limits this cube space to those cells that actually exist.</span></span> <span data-ttu-id="ba66f-108">あるディメンション内の属性階層のメンバーは、同じディメンション内の別の属性階層のメンバーと共存できない場合があります。</span><span class="sxs-lookup"><span data-stu-id="ba66f-108">Members of an attribute hierarchy in a dimension may not exist with members of another attribute hierarchy in the same dimension.</span></span>  
  
 <span data-ttu-id="ba66f-109">たとえば、City 属性階層、Country 属性階層、および Internet Sales Amount メジャーが含まれたキューブがあるとします。このキューブの空間には、共存できるメンバーのみが含まれます。</span><span class="sxs-lookup"><span data-stu-id="ba66f-109">For example, if you have a cube that has a City attribute hierarchy, a Country attribute hierarchy, and an Internet Sales Amount measure, the space of this cube only includes those members that exist with each other.</span></span> <span data-ttu-id="ba66f-110">City 属性階層に都市 New York、London、Paris、Tokyo、Melbourne があり、Country 属性階層に国 United States、United Kingdom、France、Japan、Australia があるとすると、このキューブ空間に Paris と United States が交差する領域 (セル) は含まれません。</span><span class="sxs-lookup"><span data-stu-id="ba66f-110">For example, if the City attribute hierarchy includes the cities New York, London, Paris, Tokyo, and Melbourne; and the Country attribute hierarchy includes the countries United States, United Kingdom, France, Japan, and Australia; then the space of the cube does not include the space (cell) at the intersection of Paris and United States.</span></span>  
  
 <span data-ttu-id="ba66f-111">存在しないセルに対するクエリを実行すると、NULL が返されます。つまり、存在しないセルには計算を含めることができないので、この領域に書き込みを行う計算は定義できません。</span><span class="sxs-lookup"><span data-stu-id="ba66f-111">When querying cells that do not exist, non-existing cells return nulls; that is, they cannot contain calculations and you cannot define a calculation that writes to this space.</span></span> <span data-ttu-id="ba66f-112">たとえば、次のステートメントには、存在しないセルが含まれています。</span><span class="sxs-lookup"><span data-stu-id="ba66f-112">For example, the following statement includes cells that do not exist.</span></span>  
  
```  
SELECT [Customer].[Gender].[Gender].Members ON COLUMNS,  
{[Customer].[Customer].[Aaron A. Allen]  
   ,[Customer].[Customer].[Abigail Clark]} ON ROWS   
FROM [Adventure Works]  
WHERE Measures.[Internet Sales Amount]  
```  
  
> [!NOTE]  
>  <span data-ttu-id="ba66f-113">このクエリでは、 [Members (セット) (MDX)](/sql/mdx/members-set-mdx) 関数を使用して列軸の Gender 属性階層のメンバーのセットを取得し、それを行軸の Customer 属性階層のメンバーの限定的なセットと交差させています。</span><span class="sxs-lookup"><span data-stu-id="ba66f-113">This query uses the [Members (Set) (MDX)](/sql/mdx/members-set-mdx) function to return the set of members of the Gender attribute hierarchy on the column axis, and crosses this set with the specified set of members from the Customer attribute hierarchy on the row axis.</span></span>  
  
 <span data-ttu-id="ba66f-114">上記のクエリを実行すると、Aaron A. Allen と Female が交差するセルに NULL が表示されます。</span><span class="sxs-lookup"><span data-stu-id="ba66f-114">When you execute the previous query, the cell at the intersection of Aaron A. Allen and Female displays a null.</span></span> <span data-ttu-id="ba66f-115">同様に、Abigail Clark と Male が交差するセルに NULL が表示されます。</span><span class="sxs-lookup"><span data-stu-id="ba66f-115">Similarly, the cell at the intersection of Abigail Clark and Male displays a null.</span></span> <span data-ttu-id="ba66f-116">これらのセルは存在しないため値を含めることができませんが、クエリから返される結果には、存在しないセルが表示される場合があります。</span><span class="sxs-lookup"><span data-stu-id="ba66f-116">These cells do not exist and cannot contain a value, but cells that do not exist can appear in the result returned by a query.</span></span>  
  
 <span data-ttu-id="ba66f-117">[Crossjoin (MDX)](/sql/mdx/crossjoin-mdx) 関数を使用して同一ディメンションの異なる属性階層に属するメンバーのクロス積を取得した場合、取得される組は完全なデカルト積ではなく、autoexist によって実際に存在する組のセットのみに限定されます。</span><span class="sxs-lookup"><span data-stu-id="ba66f-117">When you use the [Crossjoin (MDX)](/sql/mdx/crossjoin-mdx) function to return the cross-product of attribute hierarchy members from attribute hierarchies in the same dimension, auto-exists limits those tuples being returned to the set of tuples that actually exist, rather than returning a full Cartesian product.</span></span> <span data-ttu-id="ba66f-118">たとえば、次のクエリを実行し、実行結果を確認します。</span><span class="sxs-lookup"><span data-stu-id="ba66f-118">For example, run and then examine the results from the execution of the following query.</span></span>  
  
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
>  <span data-ttu-id="ba66f-119">このクエリでは、列軸を表す axis(0) の略記である 0 を使用して、列軸を指定しています。</span><span class="sxs-lookup"><span data-stu-id="ba66f-119">Notice that 0 is used to designate the column axis, which is shorthand for axis(0) - which is the column axis.</span></span>  
  
 <span data-ttu-id="ba66f-120">上のクエリを実行すると、クエリ内の各属性階層から、共存できるメンバーのセルのみが返されます。</span><span class="sxs-lookup"><span data-stu-id="ba66f-120">The previous query only returns cells for members from each attribute hierarchy in the query that exist with each other.</span></span> <span data-ttu-id="ba66f-121">前のクエリは、 [ \* (Crossjoin) (MDX)](/sql/mdx/crossjoin-mdx)関数の新しい \* バリアントを使用して記述することもできます。</span><span class="sxs-lookup"><span data-stu-id="ba66f-121">The previous query can also be written using the new \* variant of the [\* (Crossjoin) (MDX)](/sql/mdx/crossjoin-mdx) function.</span></span>  
  
```  
SELECT   
   [Customer].[Country].[United States] *   
      [Customer].[State-Province].Members  
ON 0   
FROM [Adventure Works]  
WHERE Measures.[Internet Sales Amount]  
```  
  
 <span data-ttu-id="ba66f-122">上のクエリは、次のように記述することもできます。</span><span class="sxs-lookup"><span data-stu-id="ba66f-122">The previous query could also be written in the following manner:</span></span>  
  
```  
SELECT [Customer].[State-Province].Members  
ON 0   
FROM [Adventure Works]  
WHERE (Measures.[Internet Sales Amount],  
   [Customer].[Country].[United States])  
```  
  
 <span data-ttu-id="ba66f-123">結果セットのメタデータが異なりますが、返されるセルの値は同一です。</span><span class="sxs-lookup"><span data-stu-id="ba66f-123">The cells values returned will be identical, although the metadata in the result set will be different.</span></span> <span data-ttu-id="ba66f-124">たとえば上のクエリで、Country 階層は (WHERE 句の) スライサー軸に移動されたので、結果セットに明示的には出現しません。</span><span class="sxs-lookup"><span data-stu-id="ba66f-124">For example, with the previous query, the Country hierarchy was moved to the slicer axis (in the WHERE clause) and therefore does not appear explicitly in the result set.</span></span>  
  
 <span data-ttu-id="ba66f-125">上記の3つのクエリはそれぞれ、の自動存在の動作の効果を示して [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] います。</span><span class="sxs-lookup"><span data-stu-id="ba66f-125">Each of these three previous queries demonstrates the effect of the auto-exists behavior in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span></span>  
  
## <a name="user-defined-hierarchies-and-cube-space"></a><span data-ttu-id="ba66f-126">ユーザー定義階層とキューブ空間</span><span class="sxs-lookup"><span data-stu-id="ba66f-126">User-Defined Hierarchies and Cube Space</span></span>  
 <span data-ttu-id="ba66f-127">このトピックのここまでの例では、属性階層を使用してキューブ空間内の位置を定義していました。</span><span class="sxs-lookup"><span data-stu-id="ba66f-127">The previous examples in this topic define positions in cube space by using attribute hierarchies.</span></span> <span data-ttu-id="ba66f-128">キューブ空間内の位置は、ディメンション内の属性階層を基に定義したユーザー定義階層を使用して定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="ba66f-128">However, you can also define a position in cube space by using user-defined hierarchies that have been defined based on attribute hierarchies in a dimension.</span></span> <span data-ttu-id="ba66f-129">ユーザー定義階層は、ユーザーによるキューブ データの参照を容易にするための、属性階層の階層です。</span><span class="sxs-lookup"><span data-stu-id="ba66f-129">A user-defined hierarchy is a hierarchy of attribute hierarchies designed to facilitate browsing of cube data by users.</span></span>  
  
 <span data-ttu-id="ba66f-130">たとえば、上のセクションの `CROSSJOIN` クエリは、次のようにも記述できます。</span><span class="sxs-lookup"><span data-stu-id="ba66f-130">For example, the `CROSSJOIN` query in the previous section could also have been written as follows:</span></span>  
  
```  
SELECT CROSSJOIN  
   (  
      {[Customer].[Country].[United States]},  
         [Customer].[Customer Geography].[State-Province].Members  
   )   
ON 0   
FROM [Adventure Works]  
WHERE Measures.[Internet Sales Amount]  
```  
  
 <span data-ttu-id="ba66f-131">先ほど属性階層を使用して定義していたキューブ空間内の位置を、このクエリでは、Customer ディメンション内の Customer Geography ユーザー定義階層で定義しています。</span><span class="sxs-lookup"><span data-stu-id="ba66f-131">In the previous query, the Customer Geography user-defined hierarchy within the Customer dimension is used to define the position in cube space that was previously defined by using an attribute hierarchy.</span></span> <span data-ttu-id="ba66f-132">属性階層とユーザー定義階層のどちらを使用しても、キューブ空間内の同じ場所を定義できます。</span><span class="sxs-lookup"><span data-stu-id="ba66f-132">The identical position in cube space can be defined by using either attribute hierarchies or user-defined hierarchies.</span></span>  
  
##  <a name="attribute-relationships-and-cube-space"></a><a name="AttribRelationships"></a><span data-ttu-id="ba66f-133">属性リレーションシップとキューブ空間</span><span class="sxs-lookup"><span data-stu-id="ba66f-133">Attribute Relationships and Cube Space</span></span>  
 <span data-ttu-id="ba66f-134">関連する属性間に属性リレーションシップを定義すると、(適切な集計が円滑に作成されるようになり) クエリのパフォーマンスが向上するだけでなく、属性階層のメンバーと共に出現する、関連する属性階層のメンバーに影響を及ぼします。</span><span class="sxs-lookup"><span data-stu-id="ba66f-134">Defining attribute relationships between related attributes improves query performance (by facilitating the creation of appropriate aggregations) and affects the member of a related attribute hierarchy that appears with an attribute hierarchy member.</span></span> <span data-ttu-id="ba66f-135">たとえば、City 属性階層のメンバーが含まれた組を定義した場合、その組に Country 属性階層のメンバーが明示的に定義されていなくても、関連する Country 属性階層のメンバーが Country 属性階層の既定メンバーであると予測できます。</span><span class="sxs-lookup"><span data-stu-id="ba66f-135">For example, when you define a tuple that includes a member from the City attribute hierarchy and the tuple does not explicitly define the Country attribute hierarchy member, you might expect that the default Country attribute hierarchy member would be the related member of the Country attribute hierarchy.</span></span> <span data-ttu-id="ba66f-136">ただしこれは、City 属性階層と Country 属性階層の間に属性リレーションシップが定義されている場合に限ります。</span><span class="sxs-lookup"><span data-stu-id="ba66f-136">However, this is only true if an attribute relationship is defined between the City attribute hierarchy and the Country attribute hierarchy.</span></span>  
  
 <span data-ttu-id="ba66f-137">次の例は、関連する属性階層に所属する、クエリに明示的に含まれていないメンバーを返します。</span><span class="sxs-lookup"><span data-stu-id="ba66f-137">The following example returns the member of a related attribute hierarchy that is not included explicitly in the query.</span></span>  
  
```  
WITH MEMBER Measures.x AS   
   Customer.Country.CurrentMember.Name  
SELECT Measures.x ON 0,  
Customer.City.Members ON 1  
FROM [Adventure Works]  
```  
  
> [!NOTE]  
>  <span data-ttu-id="ba66f-138">キーワードを使用して、 `WITH` [currentmember (mdx)](/sql/mdx/current-mdx)関数と[Name (mdx)](/sql/mdx/members-string-mdx)関数では、クエリで使用するための計算されるメンバーを作成することに注意してください。</span><span class="sxs-lookup"><span data-stu-id="ba66f-138">Notice that the `WITH` keyword is used with the [CurrentMember (MDX)](/sql/mdx/current-mdx) and [Name (MDX)](/sql/mdx/members-string-mdx) functions to create a calculated member for use in the query.</span></span> <span data-ttu-id="ba66f-139">詳細については、「[MDX の基本的なクエリ &#40;MDX&#41;](mdx-query-the-basic-query.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ba66f-139">For more information, see [The Basic MDX Query &#40;MDX&#41;](mdx-query-the-basic-query.md).</span></span>  
  
 <span data-ttu-id="ba66f-140">上のクエリでは、State 属性階層の各メンバーに関連付けられた Country 属性階層のメンバーの名前が返されます。</span><span class="sxs-lookup"><span data-stu-id="ba66f-140">In the previous query, the name of the member of the Country attribute hierarchy that is associated with each member of the State attribute hierarchy is returned.</span></span> <span data-ttu-id="ba66f-141">City 属性と Country 属性の間には属性リレーションシップが定義されているので、予測どおりに Country メンバーが返されます。</span><span class="sxs-lookup"><span data-stu-id="ba66f-141">The expected Country member appears (because an attribute relationship is defined between the City and Country attributes).</span></span> <span data-ttu-id="ba66f-142">ところが、次のクエリで示すように、同一ディメンションの属性階層間に属性リレーションシップが定義されていない場合は、(All) メンバーが返されます。</span><span class="sxs-lookup"><span data-stu-id="ba66f-142">However, if no attribute relationship were defined between attribute hierarchies in the same dimension, the (All) member would be returned, as illustrated in the following query.</span></span>  
  
```  
WITH MEMBER Measures.x AS   
   Customer.Education.Currentmember.Name  
SELECT Measures.x  ON 0,   
Customer.City.Members ON 1  
FROM [Adventure Works]  
```  
  
 <span data-ttu-id="ba66f-143">上のクエリでは、Education と City の間に属性リレーションシップが定義されていないので、(All) メンバー ("All Customers") が返されます。</span><span class="sxs-lookup"><span data-stu-id="ba66f-143">In the previous query, the (All) member ("All Customers") is returned, because there is no relationship between Education and City.</span></span> <span data-ttu-id="ba66f-144">したがって、Education メンバーが明示的に指定されていない場合、City 属性階層が含まれている組の Education 属性階層の既定のメンバーは Education 属性階層の (All) メンバーになります。</span><span class="sxs-lookup"><span data-stu-id="ba66f-144">Therefore, the (All) member of the Education attribute hierarchy would be the default member of the Education attribute hierarchy used in any tuple involving the City attribute hierarchy where an Education member is not explicitly provided.</span></span>  
  
## <a name="calculation-context"></a><span data-ttu-id="ba66f-145">計算コンテキスト</span><span class="sxs-lookup"><span data-stu-id="ba66f-145">Calculation Context</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba66f-146">参照</span><span class="sxs-lookup"><span data-stu-id="ba66f-146">See Also</span></span>  
 <span data-ttu-id="ba66f-147">[MDX &#40;Analysis Services の主な概念&#41;](../key-concepts-in-mdx-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="ba66f-147">[Key Concepts in MDX &#40;Analysis Services&#41;](../key-concepts-in-mdx-analysis-services.md) </span></span>  
 <span data-ttu-id="ba66f-148">[組](tuples.md) </span><span class="sxs-lookup"><span data-stu-id="ba66f-148">[Tuples](tuples.md) </span></span>  
 <span data-ttu-id="ba66f-149">[Autoexists](autoexists.md) </span><span class="sxs-lookup"><span data-stu-id="ba66f-149">[Autoexists](autoexists.md) </span></span>  
 <span data-ttu-id="ba66f-150">[MDX&#41;&#40;メンバー、組、およびセットの操作](working-with-members-tuples-and-sets-mdx.md) </span><span class="sxs-lookup"><span data-stu-id="ba66f-150">[Working with Members, Tuples, and Sets &#40;MDX&#41;](working-with-members-tuples-and-sets-mdx.md) </span></span>  
 <span data-ttu-id="ba66f-151">[ビジュアルの合計と非表示の合計](visual-totals-and-non-visual-totals.md) </span><span class="sxs-lookup"><span data-stu-id="ba66f-151">[Visual Totals and Non Visual Totals](visual-totals-and-non-visual-totals.md) </span></span>  
 <span data-ttu-id="ba66f-152">[Mdx 言語リファレンス &#40;MDX&#41;](/sql/mdx/mdx-language-reference-mdx) </span><span class="sxs-lookup"><span data-stu-id="ba66f-152">[MDX Language Reference &#40;MDX&#41;](/sql/mdx/mdx-language-reference-mdx) </span></span>  
 [<span data-ttu-id="ba66f-153">多次元式 &#40;MDX&#41; リファレンス</span><span class="sxs-lookup"><span data-stu-id="ba66f-153">Multidimensional Expressions &#40;MDX&#41; Reference</span></span>](/sql/mdx/multidimensional-expressions-mdx-reference)  
  
  
