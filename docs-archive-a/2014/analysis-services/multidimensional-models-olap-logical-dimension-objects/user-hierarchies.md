---
title: ユーザー階層 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- members [Analysis Services], hierarchies
- dimensions [Analysis Services], hierarchies
- user hierarchies [Analysis Services]
- hierarchies [Analysis Services], multilevel
- hierarchies [Analysis Services], attribute
- attributes [Analysis Services], hierarchies
- parent-child hierarchies [Analysis Services]
- hierarchies [Analysis Services], user
- ragged hierarchies [Analysis Services]
- balanced hierarchies [Analysis Services]
- hierarchies [Analysis Services]
- OLAP objects [Analysis Services], hierarchies
- multilevel hierarchies [Analysis Services]
- unbalanced hierarchies [Analysis Services]
ms.assetid: 9394e9a3-2242-4f0e-85e0-25d499d2d3b6
author: minewiskan
ms.author: owend
ms.openlocfilehash: 533b244a8a5b6ec5e2866b068cfbf5eb6f31a7a3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639742"
---
# <a name="user-hierarchies"></a><span data-ttu-id="91630-102">ユーザー階層</span><span class="sxs-lookup"><span data-stu-id="91630-102">User Hierarchies</span></span>
  <span data-ttu-id="91630-103">ユーザー定義階層は、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ディメンションのメンバーを階層構造に整理し、キューブ内にナビゲーションパスを提供するためにで使用される属性のユーザー定義階層です。</span><span class="sxs-lookup"><span data-stu-id="91630-103">User-defined hierarchies are user-defined hierarchies of attributes that are used in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] to organize the members of a dimension into hierarchical structures and provide navigation paths in a cube.</span></span> <span data-ttu-id="91630-104">たとえば、次のテーブルでは、時間ディメンションにディメンション テーブルを定義します。</span><span class="sxs-lookup"><span data-stu-id="91630-104">For example, the following table defines a dimension table for a time dimension.</span></span> <span data-ttu-id="91630-105">ディメンション テーブルは、年、四半期、月という 3 つの属性をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="91630-105">The dimension table supports three attributes, named Year, Quarter, and Month.</span></span>  
  
|<span data-ttu-id="91630-106">Year</span><span class="sxs-lookup"><span data-stu-id="91630-106">Year</span></span>|<span data-ttu-id="91630-107">Quarter</span><span class="sxs-lookup"><span data-stu-id="91630-107">Quarter</span></span>|<span data-ttu-id="91630-108">Month</span><span class="sxs-lookup"><span data-stu-id="91630-108">Month</span></span>|  
|----------|-------------|-----------|  
|<span data-ttu-id="91630-109">1999</span><span class="sxs-lookup"><span data-stu-id="91630-109">1999</span></span>|<span data-ttu-id="91630-110">第1四半期</span><span class="sxs-lookup"><span data-stu-id="91630-110">Quarter 1</span></span>|<span data-ttu-id="91630-111">1 月</span><span class="sxs-lookup"><span data-stu-id="91630-111">Jan</span></span>|  
|<span data-ttu-id="91630-112">1999</span><span class="sxs-lookup"><span data-stu-id="91630-112">1999</span></span>|<span data-ttu-id="91630-113">第1四半期</span><span class="sxs-lookup"><span data-stu-id="91630-113">Quarter 1</span></span>|<span data-ttu-id="91630-114">2 月</span><span class="sxs-lookup"><span data-stu-id="91630-114">Feb</span></span>|  
|<span data-ttu-id="91630-115">1999</span><span class="sxs-lookup"><span data-stu-id="91630-115">1999</span></span>|<span data-ttu-id="91630-116">第1四半期</span><span class="sxs-lookup"><span data-stu-id="91630-116">Quarter 1</span></span>|<span data-ttu-id="91630-117">3 月</span><span class="sxs-lookup"><span data-stu-id="91630-117">Mar</span></span>|  
|<span data-ttu-id="91630-118">1999</span><span class="sxs-lookup"><span data-stu-id="91630-118">1999</span></span>|<span data-ttu-id="91630-119">第2四半期</span><span class="sxs-lookup"><span data-stu-id="91630-119">Quarter 2</span></span>|<span data-ttu-id="91630-120">4 月</span><span class="sxs-lookup"><span data-stu-id="91630-120">Apr</span></span>|  
|<span data-ttu-id="91630-121">1999</span><span class="sxs-lookup"><span data-stu-id="91630-121">1999</span></span>|<span data-ttu-id="91630-122">第2四半期</span><span class="sxs-lookup"><span data-stu-id="91630-122">Quarter 2</span></span>|<span data-ttu-id="91630-123">May</span><span class="sxs-lookup"><span data-stu-id="91630-123">May</span></span>|  
|<span data-ttu-id="91630-124">1999</span><span class="sxs-lookup"><span data-stu-id="91630-124">1999</span></span>|<span data-ttu-id="91630-125">第2四半期</span><span class="sxs-lookup"><span data-stu-id="91630-125">Quarter 2</span></span>|<span data-ttu-id="91630-126">6 月</span><span class="sxs-lookup"><span data-stu-id="91630-126">Jun</span></span>|  
|<span data-ttu-id="91630-127">1999</span><span class="sxs-lookup"><span data-stu-id="91630-127">1999</span></span>|<span data-ttu-id="91630-128">第3四半期</span><span class="sxs-lookup"><span data-stu-id="91630-128">Quarter 3</span></span>|<span data-ttu-id="91630-129">7 月</span><span class="sxs-lookup"><span data-stu-id="91630-129">Jul</span></span>|  
|<span data-ttu-id="91630-130">1999</span><span class="sxs-lookup"><span data-stu-id="91630-130">1999</span></span>|<span data-ttu-id="91630-131">第3四半期</span><span class="sxs-lookup"><span data-stu-id="91630-131">Quarter 3</span></span>|<span data-ttu-id="91630-132">8 月</span><span class="sxs-lookup"><span data-stu-id="91630-132">Aug</span></span>|  
|<span data-ttu-id="91630-133">1999</span><span class="sxs-lookup"><span data-stu-id="91630-133">1999</span></span>|<span data-ttu-id="91630-134">第3四半期</span><span class="sxs-lookup"><span data-stu-id="91630-134">Quarter 3</span></span>|<span data-ttu-id="91630-135">9 月</span><span class="sxs-lookup"><span data-stu-id="91630-135">Sep</span></span>|  
|<span data-ttu-id="91630-136">1999</span><span class="sxs-lookup"><span data-stu-id="91630-136">1999</span></span>|<span data-ttu-id="91630-137">第 4 四半期</span><span class="sxs-lookup"><span data-stu-id="91630-137">Quarter 4</span></span>|<span data-ttu-id="91630-138">Oct</span><span class="sxs-lookup"><span data-stu-id="91630-138">Oct</span></span>|  
|<span data-ttu-id="91630-139">1999</span><span class="sxs-lookup"><span data-stu-id="91630-139">1999</span></span>|<span data-ttu-id="91630-140">第 4 四半期</span><span class="sxs-lookup"><span data-stu-id="91630-140">Quarter 4</span></span>|<span data-ttu-id="91630-141">11 月</span><span class="sxs-lookup"><span data-stu-id="91630-141">Nov</span></span>|  
|<span data-ttu-id="91630-142">1999</span><span class="sxs-lookup"><span data-stu-id="91630-142">1999</span></span>|<span data-ttu-id="91630-143">第 4 四半期</span><span class="sxs-lookup"><span data-stu-id="91630-143">Quarter 4</span></span>|<span data-ttu-id="91630-144">Dec</span><span class="sxs-lookup"><span data-stu-id="91630-144">Dec</span></span>|  
  
 <span data-ttu-id="91630-145">年、四半期、月の各属性は、時間ディメンションに Calendar というユーザー定義階層を作成するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="91630-145">The Year, Quarter, and Month attributes are used to construct a user-defined hierarchy, named Calendar, in the time dimension.</span></span> <span data-ttu-id="91630-146">次の図は、Calendar ディメンション (標準のディメンション) のレベルとメンバーの関係を示しています。</span><span class="sxs-lookup"><span data-stu-id="91630-146">The relationship between the levels and members of the Calendar dimension (a regular dimension) is shown in the following diagram.</span></span>  
  
 <span data-ttu-id="91630-147">![時間ディメンションのレベルとメンバーの階層構造](../dev-guide/media/as-levelconcepts.gif "時間ディメンションのレベルとメンバーの階層構造")</span><span class="sxs-lookup"><span data-stu-id="91630-147">![Level and member hierarchy for a time dimension](../dev-guide/media/as-levelconcepts.gif "Level and member hierarchy for a time dimension")</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="91630-148">2 つのレベルで構成される既定の属性階層以外の階層はすべて、ユーザー定義階層と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="91630-148">Any hierarchy other than the default two-level attribute hierarchy is called a user-defined hierarchy.</span></span> <span data-ttu-id="91630-149">属性階層の詳細については、「[属性と属性階層](../multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="91630-149">For more information about attribute hierarchies, see [Attributes and Attribute Hierarchies](../multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md).</span></span>  
  
## <a name="member-structures"></a><span data-ttu-id="91630-150">メンバー構造</span><span class="sxs-lookup"><span data-stu-id="91630-150">Member Structures</span></span>  
 <span data-ttu-id="91630-151">親子階層の例外を除いて、階層内のメンバーの位置は、階層定義の属性の順序に制御されます。</span><span class="sxs-lookup"><span data-stu-id="91630-151">With the exception of parent-child hierarchies, the positions of members within the hierarchy are controlled by the order of the attributes in the hierarchy's definition.</span></span> <span data-ttu-id="91630-152">階層定義内の各属性によって階層のレベルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="91630-152">Each attribute in the hierarchy definition constitutes a level in the hierarchy.</span></span> <span data-ttu-id="91630-153">レベル内のメンバーの位置は、レベルの作成に使用された属性の順序によって決まります。</span><span class="sxs-lookup"><span data-stu-id="91630-153">The position of a member within a level is determined by the ordering of the attribute used to create the level.</span></span> <span data-ttu-id="91630-154">ユーザー定義階層のメンバー構造は、メンバー間の関係によって、4 つの基本形式のいずれかになります。</span><span class="sxs-lookup"><span data-stu-id="91630-154">The member structures of user-defined hierarchies can take one of four basic forms, depending on how the members are related to each other.</span></span>  
  
### <a name="balanced-hierarchies"></a><span data-ttu-id="91630-155">均衡階層</span><span class="sxs-lookup"><span data-stu-id="91630-155">Balanced Hierarchies</span></span>  
 <span data-ttu-id="91630-156">均衡階層では、階層のすべての分岐は同じレベルに至り、各メンバーの論理上の親はそのメンバーのすぐ上のレベルです。</span><span class="sxs-lookup"><span data-stu-id="91630-156">In a balanced hierarchy, all branches of the hierarchy descend to the same level, and each member's logical parent is the level immediately above the member.</span></span> <span data-ttu-id="91630-157">[!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] サンプルの [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースが示す Product ディメンションの Product Categories 階層は、均衡階層の好例です。</span><span class="sxs-lookup"><span data-stu-id="91630-157">The Product Categories hierarchy of the Product dimension in the [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] sample [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database is a good example of a balanced hierarchy.</span></span> <span data-ttu-id="91630-158">Product Name レベルの各メンバーは Subcategory レベルに親メンバーがあり、Subcategory レベルは Category レベルに親メンバーがあります。</span><span class="sxs-lookup"><span data-stu-id="91630-158">Each member in the Product Name level has a parent member in the Subcategory level, which in turn has a parent member in the Category level.</span></span> <span data-ttu-id="91630-159">また、階層内の各分岐には Product Name レベルのリーフ メンバーがあります。</span><span class="sxs-lookup"><span data-stu-id="91630-159">Also, every branch in the hierarchy has a leaf member in the Product Name level.</span></span>  
  
### <a name="unbalanced-hierarchies"></a><span data-ttu-id="91630-160">不均衡階層</span><span class="sxs-lookup"><span data-stu-id="91630-160">Unbalanced Hierarchies</span></span>  
 <span data-ttu-id="91630-161">不均衡階層では、階層の分岐はさまざまなレベルに至ります。</span><span class="sxs-lookup"><span data-stu-id="91630-161">In an unbalanced hierarchy, branches of the hierarchy descend to different levels.</span></span> <span data-ttu-id="91630-162">親子階層は不均衡階層です。</span><span class="sxs-lookup"><span data-stu-id="91630-162">Parent-child hierarchies are unbalanced hierarchies.</span></span> <span data-ttu-id="91630-163">たとえば、[!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] サンプルの [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースの Organization ディメンションには、各従業員のメンバーが含まれています。</span><span class="sxs-lookup"><span data-stu-id="91630-163">For example, the Organization dimension in the [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] sample [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database contains a member for each employee.</span></span> <span data-ttu-id="91630-164">CEO は階層の最上位メンバーで、部長と役員秘書は CEO の直下にあります。</span><span class="sxs-lookup"><span data-stu-id="91630-164">The CEO is the top member in the hierarchy, and the division managers and executive secretary are immediately beneath the CEO.</span></span> <span data-ttu-id="91630-165">部長は従属メンバーですが、役員秘書は直属です。</span><span class="sxs-lookup"><span data-stu-id="91630-165">The division managers have subordinate members but the executive secretary does not.</span></span>  
  
 <span data-ttu-id="91630-166">エンド ユーザーは、不均衡階層と不規則階層を区別できません。</span><span class="sxs-lookup"><span data-stu-id="91630-166">It may be impossible for end users to distinguish between unbalanced and ragged hierarchies.</span></span> <span data-ttu-id="91630-167">ただし、管理者は、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] でさまざまなテクニックとプロパティを使用してこれらの 2 種類の階層をサポートできます。</span><span class="sxs-lookup"><span data-stu-id="91630-167">However, you employ different techniques and properties in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] to support these two types of hierarchies.</span></span> <span data-ttu-id="91630-168">詳細については、「[不規則階層](../multidimensional-models/user-defined-hierarchies-ragged-hierarchies.md)」と「[親子階層の属性](../multidimensional-models/parent-child-dimension-attributes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="91630-168">For more information, see [Ragged Hierarchies](../multidimensional-models/user-defined-hierarchies-ragged-hierarchies.md), and [Attributes in Parent-Child Hierarchies](../multidimensional-models/parent-child-dimension-attributes.md).</span></span>  
  
### <a name="ragged-hierarchies"></a><span data-ttu-id="91630-169">不規則階層</span><span class="sxs-lookup"><span data-stu-id="91630-169">Ragged Hierarchies</span></span>  
 <span data-ttu-id="91630-170">不規則階層では、少なくとも 1 つのメンバーの論理上の親メンバーが、そのメンバーのすぐ上のレベルにありません。</span><span class="sxs-lookup"><span data-stu-id="91630-170">In a ragged hierarchy, the logical parent member of at least one member is not in the level immediately above the member.</span></span> <span data-ttu-id="91630-171">このため、不規則階層の分岐はさまざまなレベルに至ります。</span><span class="sxs-lookup"><span data-stu-id="91630-171">This can cause branches of the hierarchy to descend to different levels.</span></span> <span data-ttu-id="91630-172">たとえば、Continent、CountryRegion、City の各レベルで順に定義されている地域ディメンションでは、メンバー Europe は階層の最上位レベルに表示され、メンバー France は中間レベル、メンバー Paris は最下位レベルに表示されます。</span><span class="sxs-lookup"><span data-stu-id="91630-172">For example, in a Geography dimension defined with the levels Continent, CountryRegion, and City, in that order, the member Europe appears in the top level of the hierarchy, the member France appears in the middle level, and the member Paris appears in the bottom level.</span></span> <span data-ttu-id="91630-173">France は Europe より限定的で、Paris は France より限定的です。</span><span class="sxs-lookup"><span data-stu-id="91630-173">France is more specific than Europe, and Paris is more specific than France.</span></span> <span data-ttu-id="91630-174">この標準階層は、次のように変更されます。</span><span class="sxs-lookup"><span data-stu-id="91630-174">To this regular hierarchy, the following changes are made:</span></span>  
  
-   <span data-ttu-id="91630-175">Vatican City メンバーが CountryRegion レベルに追加されます。</span><span class="sxs-lookup"><span data-stu-id="91630-175">The Vatican City member is added to the CountryRegion level.</span></span>  
  
-   <span data-ttu-id="91630-176">City レベルにメンバーが追加され、CountryRegion レベルの Vatican City メンバーに関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="91630-176">Members are added to the City level and are associated with the Vatican City member in the CountryRegion level.</span></span>  
  
-   <span data-ttu-id="91630-177">Province というレベルが CountryRegion レベルと City レベルの間に追加されます。</span><span class="sxs-lookup"><span data-stu-id="91630-177">A level, named Province, is added between the CountryRegion and City levels.</span></span>  
  
 <span data-ttu-id="91630-178">Province レベルに、CountryRegion レベルの他のメンバーに関連付けられているメンバーが生成され、City レベルのメンバーが Province レベルの対応するメンバーに関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="91630-178">The Province level is populated with members associated with other members in the CountryRegion level, and members in the City level are associated with their corresponding members in the Province level.</span></span> <span data-ttu-id="91630-179">ただし、CountryRegion レベルの Vatican City メンバーは Province レベルのメンバーに関連付けられていないため、メンバーは City レベルから CountryRegion レベルの Vatican City メンバーに直接関連付ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="91630-179">However, because the Vatican City member in the CountryRegion level has no associated members in the Province level, members must be associated from the City level directly to the Vatican City member in the CountryRegion level.</span></span> <span data-ttu-id="91630-180">この変更により、このディメンションの階層は不規則になります。</span><span class="sxs-lookup"><span data-stu-id="91630-180">Because of the changes, the hierarchy of the dimension is now ragged.</span></span> <span data-ttu-id="91630-181">市 Vatican City の親は国/地域である Vatican City で、これは City レベルの Vatican City メンバーの真上にはありません。</span><span class="sxs-lookup"><span data-stu-id="91630-181">The parent of the city Vatican City is the country/region Vatican City, which is not in the level immediately above the Vatican City member in the City level.</span></span> <span data-ttu-id="91630-182">詳細については、「 [不規則階層](../multidimensional-models/user-defined-hierarchies-ragged-hierarchies.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="91630-182">For more information, see [Ragged Hierarchies](../multidimensional-models/user-defined-hierarchies-ragged-hierarchies.md).</span></span>  
  
### <a name="parent-child-hierarchies"></a><span data-ttu-id="91630-183">親子階層</span><span class="sxs-lookup"><span data-stu-id="91630-183">Parent-Child Hierarchies</span></span>  
 <span data-ttu-id="91630-184">ディメンションの親子階層は、親子属性という特殊な属性を使用して定義され、これによってメンバー間の相互関係が決まります。</span><span class="sxs-lookup"><span data-stu-id="91630-184">Parent-child hierarchies for dimensions are defined by using a special attribute, called a parent attribute, to determine how members relate to each other.</span></span> <span data-ttu-id="91630-185">親属性は、ディメンション メイン テーブル内の *自己参照型リレーションシップ*または *自己結合*を記述します。</span><span class="sxs-lookup"><span data-stu-id="91630-185">A parent attribute describes a *self-referencing relationship*, or *self-join*, within a dimension main table.</span></span> <span data-ttu-id="91630-186">親子階層は 1 つの親属性から構築されます。</span><span class="sxs-lookup"><span data-stu-id="91630-186">Parent-child hierarchies are constructed from a single parent attribute.</span></span> <span data-ttu-id="91630-187">親子階層に存在するレベルは、親属性に関連付けられているメンバー間の親子リレーションシップに基づいているので、1 つの親子階層に割り当てられるレベルは 1 つのみです。</span><span class="sxs-lookup"><span data-stu-id="91630-187">Only one level is assigned to a parent-child hierarchy, because the levels present in the hierarchy are drawn from the parent-child relationships between members associated with the parent attribute.</span></span> <span data-ttu-id="91630-188">親子階層のディメンション スキーマは、ディメンション メイン テーブルに存在する自己参照型リレーションシップに依存します。</span><span class="sxs-lookup"><span data-stu-id="91630-188">The dimension schema of a parent-child hierarchy depends on a self-referencing relationship present on the dimension main table.</span></span> <span data-ttu-id="91630-189">たとえば、次の図は、サンプルデータベースの**DimOrganization**ディメンションメインテーブルを示してい [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="91630-189">For example, the following diagram illustrates the **DimOrganization** dimension main table in the [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] sample database.</span></span>  
  
 <span data-ttu-id="91630-190">![DimOrganization テーブルの自己参照による結合](../dev-guide/media/dimorganization.gif "DimOrganization テーブルの自己参照による結合")</span><span class="sxs-lookup"><span data-stu-id="91630-190">![Self-referencing join in DimOrganization table](../dev-guide/media/dimorganization.gif "Self-referencing join in DimOrganization table")</span></span>  
  
 <span data-ttu-id="91630-191">このディメンション テーブルでは、 **ParentOrganizationKey** 列に **OrganizationKey** 主キー列との外部キー リレーションシップがあります。</span><span class="sxs-lookup"><span data-stu-id="91630-191">In this dimension table, the **ParentOrganizationKey** column has a foreign key relationship with the **OrganizationKey** primary key column.</span></span> <span data-ttu-id="91630-192">つまり、このテーブル内の各レコードは、親子リレーションシップによりテーブル内の別のレコードと関連している可能性があります。</span><span class="sxs-lookup"><span data-stu-id="91630-192">In other words, each record in this table can be related through a parent-child relationship with another record in the table.</span></span> <span data-ttu-id="91630-193">この種の自己結合は、通常、部署内の従業員の管理構造などの組織エンティティ データを表すために使用します。</span><span class="sxs-lookup"><span data-stu-id="91630-193">This kind of self-join is generally used to represent organization entity data, such as the management structure of employees in a department.</span></span>  
  
 <span data-ttu-id="91630-194">親子階層を作成する場合、両方の属性で表す列は同じデータ型でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="91630-194">When you create a parent-child hierarchy, the columns represented by both attributes must have the same data type.</span></span> <span data-ttu-id="91630-195">また、どちらの属性も同じテーブルに属する必要があります。</span><span class="sxs-lookup"><span data-stu-id="91630-195">Both attributes must also be in the same table.</span></span> <span data-ttu-id="91630-196">既定では、親キーがそのメンバー キーと同じ値、NULL、0 を持つメンバー、またはメンバー キーの列にない値を持つメンバーは、(All) を除くトップレベルのメンバーと見なされます。</span><span class="sxs-lookup"><span data-stu-id="91630-196">By default, any member whose parent key equals its own member key, null, 0 (zero), or a value absent from the column for member keys is assumed to be a member of the top level (excluding the (All) level).</span></span>  
  
 <span data-ttu-id="91630-197">親子階層の深さは、その階層の分岐によって異なります。</span><span class="sxs-lookup"><span data-stu-id="91630-197">The depth of a parent-child hierarchy can vary among its hierarchical branches.</span></span> <span data-ttu-id="91630-198">つまり、親子階層は不均衡階層と見なされます。</span><span class="sxs-lookup"><span data-stu-id="91630-198">In other words, a parent-child hierarchy is considered an unbalanced hierarchy.</span></span>  
  
 <span data-ttu-id="91630-199">エンド ユーザーに表示されるレベル数が階層内のレベル数によって決まるユーザー定義階層とは異なり、親子階層は、単一レベルの属性階層で定義され、この単一レベルの値によりユーザーに表示される複数レベルが生成されます。</span><span class="sxs-lookup"><span data-stu-id="91630-199">Unlike user-defined hierarchies, in which the number of levels in the hierarchy determines the number of levels that can be seen by end users, a parent-child hierarchy is defined with the single level of an attribute hierarchy, and the values in this single level produce the multiple levels seen by users.</span></span> <span data-ttu-id="91630-200">表示レベルの数は、メンバー キーと親キーが格納されるディメンション テーブルの列の内容によって異なります。</span><span class="sxs-lookup"><span data-stu-id="91630-200">The number of displayed levels depends on the contents of the dimension table columns that store the member keys and the parent keys.</span></span> <span data-ttu-id="91630-201">レベルの数は、ディメンション テーブルのデータが変わると変化します。</span><span class="sxs-lookup"><span data-stu-id="91630-201">The number of levels can change when the data in the dimension tables change.</span></span> <span data-ttu-id="91630-202">詳細については、「親子[階層](../multidimensional-models/parent-child-dimension.md)」と「親子階層[の属性](../multidimensional-models/parent-child-dimension-attributes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="91630-202">For more information, see [Parent-Child Hierarchy](../multidimensional-models/parent-child-dimension.md), and [Attributes in Parent-Child Hierarchies](../multidimensional-models/parent-child-dimension-attributes.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91630-203">参照</span><span class="sxs-lookup"><span data-stu-id="91630-203">See Also</span></span>  
 <span data-ttu-id="91630-204">[ユーザー定義階層の作成](../multidimensional-models/user-defined-hierarchies-create.md) </span><span class="sxs-lookup"><span data-stu-id="91630-204">[Create User-Defined Hierarchies](../multidimensional-models/user-defined-hierarchies-create.md) </span></span>  
 <span data-ttu-id="91630-205">[ユーザー階層のプロパティ](../multidimensional-models-olap-logical-dimension-objects/user-hierarchies-properties.md) </span><span class="sxs-lookup"><span data-stu-id="91630-205">[User Hierarchy Properties](../multidimensional-models-olap-logical-dimension-objects/user-hierarchies-properties.md) </span></span>  
 [<span data-ttu-id="91630-206">ディメンションの属性のプロパティの参照</span><span class="sxs-lookup"><span data-stu-id="91630-206">Dimension Attribute Properties Reference</span></span>](../multidimensional-models/dimension-attribute-properties-reference.md)  
  
  