---
title: サブセレクトとサブキューブで計算されるメンバー |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 6e35e8f7-ae1c-4549-8432-accf036d2373
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6e6f4277c864b637c7fc5d93232ac6ebd8c4bb4d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642375"
---
# <a name="calculated-members-in-subselects-and-subcubes"></a><span data-ttu-id="48d51-102">サブセレクトとサブキューブで計算されるメンバー</span><span class="sxs-lookup"><span data-stu-id="48d51-102">Calculated Members in Subselects and Subcubes</span></span>
  <span data-ttu-id="48d51-103">以前のリリースでは、計算されるメンバーは、サブセレクトまたはサブキューブで許可されませんでした。</span><span class="sxs-lookup"><span data-stu-id="48d51-103">In previous releases, calculated members were not allowed in subselects or subcubes.</span></span> <span data-ttu-id="48d51-104">しかし、SQL Server 2008 以降では、接続プロパティによって許可され有効になりました。</span><span class="sxs-lookup"><span data-stu-id="48d51-104">However, starting with SQL Server 2008 they are allowed and enabled by a connection property.</span></span> <span data-ttu-id="48d51-105">さらに、サブセレクトおよびサブキューブにおける計算されるメンバーの新しい動作が、SQL Server 2008 R2 で導入されました。</span><span class="sxs-lookup"><span data-stu-id="48d51-105">In addition, a new behavior for calculated members, in subselects and subcubes, was introduced in SQL Server 2008 R2.</span></span>  
  
## <a name="calculated-members-in-subselects-and-subcubes"></a><span data-ttu-id="48d51-106">サブセレクトとサブキューブで計算されるメンバー</span><span class="sxs-lookup"><span data-stu-id="48d51-106">Calculated Members in Subselects and Subcubes</span></span>  
 <span data-ttu-id="48d51-107">`SubQueries`Xmla&#41;では、の接続文字列プロパティ <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.ConnectionString%2A> または `DBPROPMSMDSUBQUERIES` [サポートされる xmla プロパティ &#40;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties)のプロパティで、計算されるメンバーまたはサブキューブの計算されるメンバーまたは計算されるセットの動作または許容値を定義します。</span><span class="sxs-lookup"><span data-stu-id="48d51-107">The `SubQueries` connection string property in <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.ConnectionString%2A> or the `DBPROPMSMDSUBQUERIES` property in [Supported XMLA Properties &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties) defines the behavior or allowance of calculated members or calculated sets on subselects or subcubes.</span></span> <span data-ttu-id="48d51-108">このドキュメントのコンテキストでは、特に明記しない限り、サブセレクトはサブセレクトとサブキューブを示します。</span><span class="sxs-lookup"><span data-stu-id="48d51-108">In the context of this document, subselect refers to subselects and subcubes unless otherwise stated.</span></span>  
  
 <span data-ttu-id="48d51-109">SubQueries プロパティでは次の値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="48d51-109">The SubQueries property allows the following values.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="48d51-110">値</span><span class="sxs-lookup"><span data-stu-id="48d51-110">Value</span></span>|<span data-ttu-id="48d51-111">説明</span><span class="sxs-lookup"><span data-stu-id="48d51-111">Description</span></span>|  
|<span data-ttu-id="48d51-112">0</span><span class="sxs-lookup"><span data-stu-id="48d51-112">0</span></span>|<span data-ttu-id="48d51-113">計算されるメンバーは、サブセレクトまたはサブキューブで許可されません。</span><span class="sxs-lookup"><span data-stu-id="48d51-113">Calculated members are not allowed in subselects or subcubes.</span></span><br /><br /> <span data-ttu-id="48d51-114">計算されるメンバーが参照されている場合にサブセレクトまたはサブキューブを評価すると、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="48d51-114">An error is raised when evaluating the subselect or subcube if a calculated member is referenced.</span></span>|  
|<span data-ttu-id="48d51-115">1</span><span class="sxs-lookup"><span data-stu-id="48d51-115">1</span></span>|<span data-ttu-id="48d51-116">計算されるメンバーはサブセレクトまたはサブキューブで許可されますが、返されるサブ空間に先祖メンバーは含まれません。</span><span class="sxs-lookup"><span data-stu-id="48d51-116">Calculated members are allowed in subselects or subcubes but no ascendant members are introduced in the returning subspace.</span></span>|  
|<span data-ttu-id="48d51-117">2</span><span class="sxs-lookup"><span data-stu-id="48d51-117">2</span></span>|<span data-ttu-id="48d51-118">計算されるメンバーはサブセレクトまたはサブキューブで許可され、返されるサブ空間に先祖メンバーが含まれます。</span><span class="sxs-lookup"><span data-stu-id="48d51-118">Calculated members are allowed in subselects or subcubes and ascendant members are introduced in the returning subspace.</span></span> <span data-ttu-id="48d51-119">また、混合粒度は、計算されるメンバーの選択で許可されます。</span><span class="sxs-lookup"><span data-stu-id="48d51-119">Also, mixed granularity is allowed in the selection of calculated members.</span></span>|  
  
 <span data-ttu-id="48d51-120">SubQueries プロパティに値 1 または 2 を使用すると、計算されるメンバーをサブセレクトから返されるサブ空間のフィルター処理に使用できます。</span><span class="sxs-lookup"><span data-stu-id="48d51-120">Using values of 1 or 2 in the SubQueries property allows calculated members to be used to filter the returning subspace of subselects.</span></span>  
  
 <span data-ttu-id="48d51-121">この概念をわかりやすくするため、例を示します。まず、計算されるメンバーを作成し、次に上記の動作を示すためにサブセレクト クエリを発行します。</span><span class="sxs-lookup"><span data-stu-id="48d51-121">An example will help clarify the concept; first a calculated member must be created and then a subselect query issued to show the above mentioned behavior.</span></span>  
  
 <span data-ttu-id="48d51-122">次の例では、[Seattle Metro] を都市として Washington 州の [Geography].[Geography] 階層に追加する、計算されるメンバーを作成します。</span><span class="sxs-lookup"><span data-stu-id="48d51-122">The following sample creates a calculated member that adds [Seattle Metro] as a city to the [Geography].[Geography] hierarchy under Washington state.</span></span>  
  
 <span data-ttu-id="48d51-123">この例を実行するには、値 1 を持つ SubQueries プロパティが接続文字列に含まれており、すべての MDX ステートメントを同じセッションで実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="48d51-123">To run the example, the connection string must contain the SubQueries property with a value of 1 and all MDX statements must be run in the same session.</span></span>  
  
 <span data-ttu-id="48d51-124">最初に、次の MDX 式を発行します。</span><span class="sxs-lookup"><span data-stu-id="48d51-124">First issue the following MDX expression:</span></span>  
  
```  
//Remember to set Subqueries=1 in the connection string prior  
//to issue these commands  
//--> AS2008 behavior  
CREATE MEMBER [Adventure Works].[Geography].[Geography].[State-Province].&[WA]&[US].[Seattle Metro Agg]   
   AS  AGGREGATE(   
                 {   
                   [Geography].[Geography].[City].&[Bellevue]&[WA]  
                 , [Geography].[Geography].[City].&[Issaquah]&[WA]  
                 , [Geography].[Geography].[City].&[Redmond]&[WA]  
                 , [Geography].[Geography].[City].&[Seattle]&[WA]  
                 }  
                )    
```  
  
 <span data-ttu-id="48d51-125">次の MDX クエリを発行し、サブセレクトで許可された計算されるメンバーを表示します。</span><span class="sxs-lookup"><span data-stu-id="48d51-125">Then issue the following MDX query to see calculated members allowed in subselects.</span></span>  
  
```  
Select [Date].[Calendar Year].members on 0,  
       [Geography].[Geography].allmembers on 1  
from (Select {[Geography].[Geography].[State-Province].&[WA]&[US].[Seattle Metro Agg]} on 0 from [Adventure Works])  
Where [Measures].[Reseller Sales Amount]  
```  
  
 <span data-ttu-id="48d51-126">次の結果が得られます。</span><span class="sxs-lookup"><span data-stu-id="48d51-126">The obtained results are:</span></span>  
  
|||||||  
|-|-|-|-|-|-|  
||<span data-ttu-id="48d51-127">All Periods</span><span class="sxs-lookup"><span data-stu-id="48d51-127">All Periods</span></span>|<span data-ttu-id="48d51-128">CY 2001</span><span class="sxs-lookup"><span data-stu-id="48d51-128">CY 2001</span></span>|<span data-ttu-id="48d51-129">CY 2002</span><span class="sxs-lookup"><span data-stu-id="48d51-129">CY 2002</span></span>|<span data-ttu-id="48d51-130">CY 2003</span><span class="sxs-lookup"><span data-stu-id="48d51-130">CY 2003</span></span>|<span data-ttu-id="48d51-131">CY 2004</span><span class="sxs-lookup"><span data-stu-id="48d51-131">CY 2004</span></span>|  
|<span data-ttu-id="48d51-132">Seattle Metro Agg</span><span class="sxs-lookup"><span data-stu-id="48d51-132">Seattle Metro Agg</span></span>|<span data-ttu-id="48d51-133">$2,383,545.69</span><span class="sxs-lookup"><span data-stu-id="48d51-133">$2,383,545.69</span></span>|<span data-ttu-id="48d51-134">$291,248.93</span><span class="sxs-lookup"><span data-stu-id="48d51-134">$291,248.93</span></span>|<span data-ttu-id="48d51-135">$763,557.02</span><span class="sxs-lookup"><span data-stu-id="48d51-135">$763,557.02</span></span>|<span data-ttu-id="48d51-136">$915,832.36</span><span class="sxs-lookup"><span data-stu-id="48d51-136">$915,832.36</span></span>|<span data-ttu-id="48d51-137">$412,907.37</span><span class="sxs-lookup"><span data-stu-id="48d51-137">$412,907.37</span></span>|  
  
 <span data-ttu-id="48d51-138">前述のように、SubQueries=1 の場合は、返されるサブ空間に [Seattle Metro] の先祖が存在しないため、[Geography].[Geography].allmembers には計算されるメンバーのみが含まれます。</span><span class="sxs-lookup"><span data-stu-id="48d51-138">As said before, the ascendants of [Seattle Metro] do not exist in the returned subspace, when SubQueries=1, hence [Geography].[Geography].allmembers only contains the calculated member.</span></span>  
  
 <span data-ttu-id="48d51-139">接続文字列で SubQueries=2 を使用して実行すると、次の結果が得られます。</span><span class="sxs-lookup"><span data-stu-id="48d51-139">If the example is run using SubQueries=2, in the connection string, the obtained results are:</span></span>  
  
|||||||  
|-|-|-|-|-|-|  
||<span data-ttu-id="48d51-140">All Periods</span><span class="sxs-lookup"><span data-stu-id="48d51-140">All Periods</span></span>|<span data-ttu-id="48d51-141">CY 2001</span><span class="sxs-lookup"><span data-stu-id="48d51-141">CY 2001</span></span>|<span data-ttu-id="48d51-142">CY 2002</span><span class="sxs-lookup"><span data-stu-id="48d51-142">CY 2002</span></span>|<span data-ttu-id="48d51-143">CY 2003</span><span class="sxs-lookup"><span data-stu-id="48d51-143">CY 2003</span></span>|<span data-ttu-id="48d51-144">CY 2004</span><span class="sxs-lookup"><span data-stu-id="48d51-144">CY 2004</span></span>|  
|<span data-ttu-id="48d51-145">All Geographies</span><span class="sxs-lookup"><span data-stu-id="48d51-145">All Geographies</span></span>|<span data-ttu-id="48d51-146">(null)</span><span class="sxs-lookup"><span data-stu-id="48d51-146">(null)</span></span>|<span data-ttu-id="48d51-147">(null)</span><span class="sxs-lookup"><span data-stu-id="48d51-147">(null)</span></span>|<span data-ttu-id="48d51-148">(null)</span><span class="sxs-lookup"><span data-stu-id="48d51-148">(null)</span></span>|<span data-ttu-id="48d51-149">(null)</span><span class="sxs-lookup"><span data-stu-id="48d51-149">(null)</span></span>|<span data-ttu-id="48d51-150">(null)</span><span class="sxs-lookup"><span data-stu-id="48d51-150">(null)</span></span>|  
|<span data-ttu-id="48d51-151">United States</span><span class="sxs-lookup"><span data-stu-id="48d51-151">United States</span></span>|<span data-ttu-id="48d51-152">(null)</span><span class="sxs-lookup"><span data-stu-id="48d51-152">(null)</span></span>|<span data-ttu-id="48d51-153">(null)</span><span class="sxs-lookup"><span data-stu-id="48d51-153">(null)</span></span>|<span data-ttu-id="48d51-154">(null)</span><span class="sxs-lookup"><span data-stu-id="48d51-154">(null)</span></span>|<span data-ttu-id="48d51-155">(null)</span><span class="sxs-lookup"><span data-stu-id="48d51-155">(null)</span></span>|<span data-ttu-id="48d51-156">(null)</span><span class="sxs-lookup"><span data-stu-id="48d51-156">(null)</span></span>|  
|<span data-ttu-id="48d51-157">ワシントン</span><span class="sxs-lookup"><span data-stu-id="48d51-157">Washington</span></span>|<span data-ttu-id="48d51-158">(null)</span><span class="sxs-lookup"><span data-stu-id="48d51-158">(null)</span></span>|<span data-ttu-id="48d51-159">(null)</span><span class="sxs-lookup"><span data-stu-id="48d51-159">(null)</span></span>|<span data-ttu-id="48d51-160">(null)</span><span class="sxs-lookup"><span data-stu-id="48d51-160">(null)</span></span>|<span data-ttu-id="48d51-161">(null)</span><span class="sxs-lookup"><span data-stu-id="48d51-161">(null)</span></span>|<span data-ttu-id="48d51-162">(null)</span><span class="sxs-lookup"><span data-stu-id="48d51-162">(null)</span></span>|  
|<span data-ttu-id="48d51-163">Seattle Metro Agg</span><span class="sxs-lookup"><span data-stu-id="48d51-163">Seattle Metro Agg</span></span>|<span data-ttu-id="48d51-164">$2,383,545.69</span><span class="sxs-lookup"><span data-stu-id="48d51-164">$2,383,545.69</span></span>|<span data-ttu-id="48d51-165">$291,248.93</span><span class="sxs-lookup"><span data-stu-id="48d51-165">$291,248.93</span></span>|<span data-ttu-id="48d51-166">$763,557.02</span><span class="sxs-lookup"><span data-stu-id="48d51-166">$763,557.02</span></span>|<span data-ttu-id="48d51-167">$915,832.36</span><span class="sxs-lookup"><span data-stu-id="48d51-167">$915,832.36</span></span>|<span data-ttu-id="48d51-168">$412,907.37</span><span class="sxs-lookup"><span data-stu-id="48d51-168">$412,907.37</span></span>|  
  
 <span data-ttu-id="48d51-169">前述のように、SubQueries=2 の場合は、返されるサブ空間に [Seattle Metro] の先祖が存在しますが、集計に使用する標準メンバーが存在しないため、これらのメンバーに対する値はありません。</span><span class="sxs-lookup"><span data-stu-id="48d51-169">As said before, when using SubQueries=2, the ascendants of [Seattle Metro] exist in the returned subspace but no values exist for those members because there is no regular members to provide for the aggregations.</span></span> <span data-ttu-id="48d51-170">したがって、この例では、計算されるメンバーのすべての先祖メンバーに対して NULL 値が返されます。</span><span class="sxs-lookup"><span data-stu-id="48d51-170">Therefore, NULL values are provided for all ascendant members of the calculated member in this example.</span></span>  
  
 <span data-ttu-id="48d51-171">上記の動作を理解するには、計算されるメンバーは標準メンバーのように親の集計に影響を与えないということを知っておくと役に立ちます。前者は、計算されるメンバーのみでフィルター処理を行うと、作成されたサブ空間の集計値に影響を与える標準メンバーが存在しないため、先祖が空になることを意味します。</span><span class="sxs-lookup"><span data-stu-id="48d51-171">To understand the above behavior, it helps to understand that calculated members do not contribute to the aggregations of their parents as regular members do; the former implies that filtering by calculated members alone will lead to empty ascendants because there are no regular members to contribute to the aggregated values of the resulting subspace.</span></span> <span data-ttu-id="48d51-172">標準メンバーをフィルター式に追加すると、これらの標準メンバーから集計値が得られます。</span><span class="sxs-lookup"><span data-stu-id="48d51-172">If you add regular members to the filtering expression then the aggregated values will come from those regular members.</span></span> <span data-ttu-id="48d51-173">上記の例を引き続き使用すると、Oregon の都市 Portland と Washington の都市 Spokane は、次の MDX 式に示すように、計算されるメンバーが表示される同じ軸に追加されます。</span><span class="sxs-lookup"><span data-stu-id="48d51-173">Continuing with the above example, if the cities of Portland, in Oregon, and the city of Spokane, in Washington, are added to the same axis where the calculated member appears; as shown in the next MDX expression:</span></span>  
  
```  
Select [Date].[Calendar Year].members on 0,  
       [Geography].[Geography].allmembers on 1  
from (Select {  
               [Seattle Metro Agg]  
             , [Geography].[Geography].[City].&[Portland]&[OR]  
             , [Geography].[Geography].[City].&[Spokane]&[WA]  
             } on 0 from [Adventure Works]  
     )  
Where [Measures].[Reseller Sales Amount]  
```  
  
 <span data-ttu-id="48d51-174">結果は、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="48d51-174">The following results are obtained.</span></span>  
  
|||||||  
|-|-|-|-|-|-|  
||<span data-ttu-id="48d51-175">All Periods</span><span class="sxs-lookup"><span data-stu-id="48d51-175">All Periods</span></span>|<span data-ttu-id="48d51-176">CY 2001</span><span class="sxs-lookup"><span data-stu-id="48d51-176">CY 2001</span></span>|<span data-ttu-id="48d51-177">CY 2002</span><span class="sxs-lookup"><span data-stu-id="48d51-177">CY 2002</span></span>|<span data-ttu-id="48d51-178">CY 2003</span><span class="sxs-lookup"><span data-stu-id="48d51-178">CY 2003</span></span>|<span data-ttu-id="48d51-179">CY 2004</span><span class="sxs-lookup"><span data-stu-id="48d51-179">CY 2004</span></span>|  
|<span data-ttu-id="48d51-180">All Geographies</span><span class="sxs-lookup"><span data-stu-id="48d51-180">All Geographies</span></span>|<span data-ttu-id="48d51-181">$235,171.62</span><span class="sxs-lookup"><span data-stu-id="48d51-181">$235,171.62</span></span>|<span data-ttu-id="48d51-182">$419.46</span><span class="sxs-lookup"><span data-stu-id="48d51-182">$419.46</span></span>|<span data-ttu-id="48d51-183">$4,996.25</span><span class="sxs-lookup"><span data-stu-id="48d51-183">$4,996.25</span></span>|<span data-ttu-id="48d51-184">$131,788.82</span><span class="sxs-lookup"><span data-stu-id="48d51-184">$131,788.82</span></span>|<span data-ttu-id="48d51-185">$97,967.09</span><span class="sxs-lookup"><span data-stu-id="48d51-185">$97,967.09</span></span>|  
|<span data-ttu-id="48d51-186">United States</span><span class="sxs-lookup"><span data-stu-id="48d51-186">United States</span></span>|<span data-ttu-id="48d51-187">$235,171.62</span><span class="sxs-lookup"><span data-stu-id="48d51-187">$235,171.62</span></span>|<span data-ttu-id="48d51-188">$419.46</span><span class="sxs-lookup"><span data-stu-id="48d51-188">$419.46</span></span>|<span data-ttu-id="48d51-189">$4,996.25</span><span class="sxs-lookup"><span data-stu-id="48d51-189">$4,996.25</span></span>|<span data-ttu-id="48d51-190">$131,788.82</span><span class="sxs-lookup"><span data-stu-id="48d51-190">$131,788.82</span></span>|<span data-ttu-id="48d51-191">$97,967.09</span><span class="sxs-lookup"><span data-stu-id="48d51-191">$97,967.09</span></span>|  
|<span data-ttu-id="48d51-192">オレゴン</span><span class="sxs-lookup"><span data-stu-id="48d51-192">Oregon</span></span>|<span data-ttu-id="48d51-193">$30,968.25</span><span class="sxs-lookup"><span data-stu-id="48d51-193">$30,968.25</span></span>|<span data-ttu-id="48d51-194">$419.46</span><span class="sxs-lookup"><span data-stu-id="48d51-194">$419.46</span></span>|<span data-ttu-id="48d51-195">$4,996.25</span><span class="sxs-lookup"><span data-stu-id="48d51-195">$4,996.25</span></span>|<span data-ttu-id="48d51-196">$17,442.97</span><span class="sxs-lookup"><span data-stu-id="48d51-196">$17,442.97</span></span>|<span data-ttu-id="48d51-197">$8,109.56</span><span class="sxs-lookup"><span data-stu-id="48d51-197">$8,109.56</span></span>|  
|<span data-ttu-id="48d51-198">Portland</span><span class="sxs-lookup"><span data-stu-id="48d51-198">Portland</span></span>|<span data-ttu-id="48d51-199">$30,968.25</span><span class="sxs-lookup"><span data-stu-id="48d51-199">$30,968.25</span></span>|<span data-ttu-id="48d51-200">$419.46</span><span class="sxs-lookup"><span data-stu-id="48d51-200">$419.46</span></span>|<span data-ttu-id="48d51-201">$4,996.25</span><span class="sxs-lookup"><span data-stu-id="48d51-201">$4,996.25</span></span>|<span data-ttu-id="48d51-202">$17,442.97</span><span class="sxs-lookup"><span data-stu-id="48d51-202">$17,442.97</span></span>|<span data-ttu-id="48d51-203">$8,109.56</span><span class="sxs-lookup"><span data-stu-id="48d51-203">$8,109.56</span></span>|  
|<span data-ttu-id="48d51-204">97205</span><span class="sxs-lookup"><span data-stu-id="48d51-204">97205</span></span>|<span data-ttu-id="48d51-205">$30,968.25</span><span class="sxs-lookup"><span data-stu-id="48d51-205">$30,968.25</span></span>|<span data-ttu-id="48d51-206">$419.46</span><span class="sxs-lookup"><span data-stu-id="48d51-206">$419.46</span></span>|<span data-ttu-id="48d51-207">$4,996.25</span><span class="sxs-lookup"><span data-stu-id="48d51-207">$4,996.25</span></span>|<span data-ttu-id="48d51-208">$17,442.97</span><span class="sxs-lookup"><span data-stu-id="48d51-208">$17,442.97</span></span>|<span data-ttu-id="48d51-209">$8,109.56</span><span class="sxs-lookup"><span data-stu-id="48d51-209">$8,109.56</span></span>|  
|<span data-ttu-id="48d51-210">ワシントン</span><span class="sxs-lookup"><span data-stu-id="48d51-210">Washington</span></span>|<span data-ttu-id="48d51-211">$204,203.37</span><span class="sxs-lookup"><span data-stu-id="48d51-211">$204,203.37</span></span>|<span data-ttu-id="48d51-212">(null)</span><span class="sxs-lookup"><span data-stu-id="48d51-212">(null)</span></span>|<span data-ttu-id="48d51-213">(null)</span><span class="sxs-lookup"><span data-stu-id="48d51-213">(null)</span></span>|<span data-ttu-id="48d51-214">$114,345.85</span><span class="sxs-lookup"><span data-stu-id="48d51-214">$114,345.85</span></span>|<span data-ttu-id="48d51-215">$89,857.52</span><span class="sxs-lookup"><span data-stu-id="48d51-215">$89,857.52</span></span>|  
|<span data-ttu-id="48d51-216">Spokane</span><span class="sxs-lookup"><span data-stu-id="48d51-216">Spokane</span></span>|<span data-ttu-id="48d51-217">$204,203.37</span><span class="sxs-lookup"><span data-stu-id="48d51-217">$204,203.37</span></span>|<span data-ttu-id="48d51-218">(null)</span><span class="sxs-lookup"><span data-stu-id="48d51-218">(null)</span></span>|<span data-ttu-id="48d51-219">(null)</span><span class="sxs-lookup"><span data-stu-id="48d51-219">(null)</span></span>|<span data-ttu-id="48d51-220">$114,345.85</span><span class="sxs-lookup"><span data-stu-id="48d51-220">$114,345.85</span></span>|<span data-ttu-id="48d51-221">$89,857.52</span><span class="sxs-lookup"><span data-stu-id="48d51-221">$89,857.52</span></span>|  
|<span data-ttu-id="48d51-222">99202</span><span class="sxs-lookup"><span data-stu-id="48d51-222">99202</span></span>|<span data-ttu-id="48d51-223">$204,203.37</span><span class="sxs-lookup"><span data-stu-id="48d51-223">$204,203.37</span></span>|<span data-ttu-id="48d51-224">(null)</span><span class="sxs-lookup"><span data-stu-id="48d51-224">(null)</span></span>|<span data-ttu-id="48d51-225">(null)</span><span class="sxs-lookup"><span data-stu-id="48d51-225">(null)</span></span>|<span data-ttu-id="48d51-226">$114,345.85</span><span class="sxs-lookup"><span data-stu-id="48d51-226">$114,345.85</span></span>|<span data-ttu-id="48d51-227">$89,857.52</span><span class="sxs-lookup"><span data-stu-id="48d51-227">$89,857.52</span></span>|  
|<span data-ttu-id="48d51-228">Seattle Metro Agg</span><span class="sxs-lookup"><span data-stu-id="48d51-228">Seattle Metro Agg</span></span>|<span data-ttu-id="48d51-229">$2,383,545.69</span><span class="sxs-lookup"><span data-stu-id="48d51-229">$2,383,545.69</span></span>|<span data-ttu-id="48d51-230">$291,248.93</span><span class="sxs-lookup"><span data-stu-id="48d51-230">$291,248.93</span></span>|<span data-ttu-id="48d51-231">$763,557.02</span><span class="sxs-lookup"><span data-stu-id="48d51-231">$763,557.02</span></span>|<span data-ttu-id="48d51-232">$915,832.36</span><span class="sxs-lookup"><span data-stu-id="48d51-232">$915,832.36</span></span>|<span data-ttu-id="48d51-233">$412,907.37</span><span class="sxs-lookup"><span data-stu-id="48d51-233">$412,907.37</span></span>|  
  
 <span data-ttu-id="48d51-234">上記の結果では、[All Geographies]、[United States]、[Oregon]、および [Washington] の集計値は、&[Portland]&[OR] および &[Spokane]&[WA] の子孫の集計から取得されます。</span><span class="sxs-lookup"><span data-stu-id="48d51-234">In the above results the aggregated values for [All Geographies], [United States], [Oregon] and [Washington] come from aggregating over the descendants of &[Portland]&[OR] and &[Spokane]&[WA].</span></span> <span data-ttu-id="48d51-235">計算されるメンバーから取得されるものはありません。</span><span class="sxs-lookup"><span data-stu-id="48d51-235">Nothing comes from the calculated member.</span></span>  
  
### <a name="remarks"></a><span data-ttu-id="48d51-236">解説</span><span class="sxs-lookup"><span data-stu-id="48d51-236">Remarks</span></span>  
 <span data-ttu-id="48d51-237">サブセレクトまたはサブキューブ式で許可されるのは、グローバルまたはセッションで計算されるメンバーのみです。</span><span class="sxs-lookup"><span data-stu-id="48d51-237">Only global or session calculated members are allowed in the subselect or subcube expressions.</span></span> <span data-ttu-id="48d51-238">MDX 式にクエリで計算されるメンバーが含まれている場合に、サブセレクトまたはサブキューブ式を評価すると、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="48d51-238">Having query calculated members in the MDX expression will raise an error when the subselect or subcube expression is evaluated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48d51-239">参照</span><span class="sxs-lookup"><span data-stu-id="48d51-239">See Also</span></span>  
 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.ConnectionString%2A>   
 <span data-ttu-id="48d51-240">[クエリのサブセレクト](subselects-in-queries.md) </span><span class="sxs-lookup"><span data-stu-id="48d51-240">[Subselects in Queries](subselects-in-queries.md) </span></span>  
 [<span data-ttu-id="48d51-241">サポートされる XMLA プロパティ (XMLA)</span><span class="sxs-lookup"><span data-stu-id="48d51-241">Supported XMLA Properties &#40;XMLA&#41;</span></span>](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties)  
  
  
