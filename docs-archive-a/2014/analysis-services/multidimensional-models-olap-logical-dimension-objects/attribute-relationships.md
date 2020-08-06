---
title: 属性リレーションシップ |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- member properties [Analysis Services], attribute relationships
- security [Analysis Services], properties
- PROPERTIES keyword
- storage [Analysis Services], attribute relationships
- natural hierarchies [Analysis Services]
- dimensions [Analysis Services], member properties
- queries [MDX], attribute relationships
- user-defined hierarchies [Analysis Services]
- attributes [Analysis Services], relationships
- member properties [Analysis Services]
- members [Analysis Services], attribute relationships
- storing data [Analysis Services], attribute relationships
- relationships [Analysis Services], attributes
ms.assetid: 2491422a-4cf5-4b23-b6ab-289222b22ce8
author: minewiskan
ms.author: owend
ms.openlocfilehash: 122638a2728a8a85ee58661196797383da20eef8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716906"
---
# <a name="attribute-relationships"></a><span data-ttu-id="f1871-102">のディメンション デザイナーでは、[ディメンション構造] ビューの</span><span class="sxs-lookup"><span data-stu-id="f1871-102">Attribute Relationships</span></span>
  <span data-ttu-id="f1871-103">では [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 、ディメンション内の属性は常に、直接または間接的にキー属性に関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="f1871-103">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], attributes within a dimension are always related either directly or indirectly to the key attribute.</span></span> <span data-ttu-id="f1871-104">同一のリレーショナル テーブルからすべてのディメンション属性が派生するスター スキーマに基づいてディメンションを定義すると、ディメンションのキー属性と各非キー属性の間に自動的に属性リレーションシップが定義されます。</span><span class="sxs-lookup"><span data-stu-id="f1871-104">When you define a dimension based on a star schema, which is where all dimension attributes are derived from the same relational table, an attribute relationship is automatically defined between the key attribute and each non-key attribute of the dimension.</span></span> <span data-ttu-id="f1871-105">関連を持った複数のテーブルからディメンション属性が派生するスノーフレーク スキーマを基にディメンションを定義すると、属性リレーションシップが自動的に次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="f1871-105">When you define a dimension based on a snowflake schema, which is where dimension attributes are derived from multiple related tables, an attribute relationship is automatically defined as follows:</span></span>  
  
-   <span data-ttu-id="f1871-106">キー属性と、メイン ディメンション テーブルの列にバインドされた各非キー属性の間</span><span class="sxs-lookup"><span data-stu-id="f1871-106">Between the key attribute and each non-key attribute bound to columns in the main dimension table.</span></span>  
  
-   <span data-ttu-id="f1871-107">キー属性と、基になるディメンション テーブルにリンクしているセカンダリ テーブルの外部キーにバインドされた属性の間</span><span class="sxs-lookup"><span data-stu-id="f1871-107">Between the key attribute and the attribute bound to the foreign key in the secondary table that links the underlying dimension tables.</span></span>  
  
-   <span data-ttu-id="f1871-108">セカンダリ テーブルの外部キーにバインドされた属性と、セカンダリ テーブルの列にバインドされた各非キー属性の間</span><span class="sxs-lookup"><span data-stu-id="f1871-108">Between the attribute bound to foreign key in the secondary table and each non-key attribute bound to columns from the secondary table.</span></span>  
  
 <span data-ttu-id="f1871-109">ただし、さまざまな理由で、上記の既定の属性リレーションシップの変更が必要になる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="f1871-109">However, there are a number of reasons why you might want to change these default attribute relationships.</span></span> <span data-ttu-id="f1871-110">たとえば、非キー属性に基づいて、自然階層、カスタムの並べ替え順、ディメンションの粒度などを定義できます。</span><span class="sxs-lookup"><span data-stu-id="f1871-110">For example, you might want to define a natural hierarchy, a custom sort order, or dimension granularity based on a non-key attribute.</span></span> <span data-ttu-id="f1871-111">詳細については、「[ディメンション属性プロパティのリファレンス](../multidimensional-models/dimension-attribute-properties-reference.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f1871-111">For more information, see [Dimension Attribute Properties Reference](../multidimensional-models/dimension-attribute-properties-reference.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f1871-112">属性リレーションシップは、多次元式 (MDX) ではメンバーのプロパティと呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="f1871-112">Attribute relationships are known in Multidimensional Expressions (MDX) as member properties.</span></span>  
  
## <a name="natural-hierarchy-relationships"></a><span data-ttu-id="f1871-113">自然階層リレーションシップ</span><span class="sxs-lookup"><span data-stu-id="f1871-113">Natural Hierarchy Relationships</span></span>  
 <span data-ttu-id="f1871-114">ユーザー定義階層内の各属性がそのすぐ下の属性と一対多のリレーションシップにある場合、階層は自然階層になります。</span><span class="sxs-lookup"><span data-stu-id="f1871-114">A hierarchy is a natural hierarchy when each attribute included in the user-defined hierarchy has a one to many relationship with the attribute immediately below it.</span></span> <span data-ttu-id="f1871-115">たとえば、次の 8 つの列から構成されるリレーショナル ソース テーブルを基にした Customer ディメンションを考えてみます。</span><span class="sxs-lookup"><span data-stu-id="f1871-115">For example, consider a Customer dimension based on a relational source table with eight columns:</span></span>  
  
-   <span data-ttu-id="f1871-116">CustomerKey</span><span class="sxs-lookup"><span data-stu-id="f1871-116">CustomerKey</span></span>  
  
-   <span data-ttu-id="f1871-117">CustomerName</span><span class="sxs-lookup"><span data-stu-id="f1871-117">CustomerName</span></span>  
  
-   <span data-ttu-id="f1871-118">年齢</span><span class="sxs-lookup"><span data-stu-id="f1871-118">Age</span></span>  
  
-   <span data-ttu-id="f1871-119">性別</span><span class="sxs-lookup"><span data-stu-id="f1871-119">Gender</span></span>  
  
-   <span data-ttu-id="f1871-120">Email</span><span class="sxs-lookup"><span data-stu-id="f1871-120">Email</span></span>  
  
-   <span data-ttu-id="f1871-121">City</span><span class="sxs-lookup"><span data-stu-id="f1871-121">City</span></span>  
  
-   <span data-ttu-id="f1871-122">Country</span><span class="sxs-lookup"><span data-stu-id="f1871-122">Country</span></span>  
  
-   <span data-ttu-id="f1871-123">リージョン</span><span class="sxs-lookup"><span data-stu-id="f1871-123">Region</span></span>  
  
 <span data-ttu-id="f1871-124">対応する Analysis Services ディメンションには、次の 7 つの属性があります。</span><span class="sxs-lookup"><span data-stu-id="f1871-124">The corresponding Analysis Services dimension has seven attributes:</span></span>  
  
-   <span data-ttu-id="f1871-125">Customer (CustomerKey キーを基に CustomerName でメンバー名を指定)</span><span class="sxs-lookup"><span data-stu-id="f1871-125">Customer (based on CustomerKey, with CustomerName supplying member names)</span></span>  
  
-   <span data-ttu-id="f1871-126">Age、Gender、Email、City、Region、Country</span><span class="sxs-lookup"><span data-stu-id="f1871-126">Age, Gender, Email, City, Region, Country</span></span>  
  
 <span data-ttu-id="f1871-127">自然階層を表すリレーションシップを適用するには、あるレベルの属性とその下のレベルの属性との間に属性リレーションシップを作成します。</span><span class="sxs-lookup"><span data-stu-id="f1871-127">Relationships representing natural hierarchies are enforced by creating an attribute relationship between the attribute for a level and the attribute for the level below it.</span></span> <span data-ttu-id="f1871-128">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] では、このしくみによって、自然なリレーションシップと潜在的な集計が指定されます。</span><span class="sxs-lookup"><span data-stu-id="f1871-128">For [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], this specifies a natural relationship and potential aggregation.</span></span> <span data-ttu-id="f1871-129">Customer ディメンションには、Country 属性、Region 属性、City 属性、および Customer 属性に対する自然階層が存在します。</span><span class="sxs-lookup"><span data-stu-id="f1871-129">In the Customer dimension, a natural hierarchy exists for the Country, Region, City, and Customer attributes.</span></span> <span data-ttu-id="f1871-130">`{Country, Region, City, Customer}` の自然階層は、次の属性リレーションシップを追加して記述します。</span><span class="sxs-lookup"><span data-stu-id="f1871-130">The natural hierarchy for `{Country, Region, City, Customer}` is described by adding the following attribute relationships:</span></span>  
  
-   <span data-ttu-id="f1871-131">Region 属性に対する属性リレーションシップとしての Country 属性</span><span class="sxs-lookup"><span data-stu-id="f1871-131">The Country attribute as an attribute relationship to the Region attribute.</span></span>  
  
-   <span data-ttu-id="f1871-132">City 属性に対する属性リレーションシップとしての Region 属性</span><span class="sxs-lookup"><span data-stu-id="f1871-132">The Region attribute as an attribute relationship to the City attribute.</span></span>  
  
-   <span data-ttu-id="f1871-133">Customer 属性に対する属性リレーションシップとしての City 属性</span><span class="sxs-lookup"><span data-stu-id="f1871-133">The City attribute as an attribute relationship to the Customer attribute.</span></span>  
  
 <span data-ttu-id="f1871-134">キューブ内のデータを移動する場合は、データの自然階層を表さないユーザー定義階層 (*アドホック*または*レポート*階層と呼ばれます) を作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="f1871-134">For navigating data in the cube, you can also create a user-defined hierarchy that does not represent a natural hierarchy in the data (which is called an *ad hoc* or *reporting* hierarchy).</span></span> <span data-ttu-id="f1871-135">たとえば、`{Age, Gender}` を基にしたユーザー定義階層を作成できます。</span><span class="sxs-lookup"><span data-stu-id="f1871-135">For example, you could create a user-defined hierarchy based on `{Age, Gender}`.</span></span> <span data-ttu-id="f1871-136">ユーザーは、2つの階層がどのように動作するかに違いはありません。ただし、自然階層は、ソースデータ内の自然なリレーションシップのために、ユーザーから非表示になります。</span><span class="sxs-lookup"><span data-stu-id="f1871-136">Users do not see any difference in how the two hierarchies behave, although the natural hierarchy benefits from aggregating and indexing structures - hidden from the user - that account for the natural relationships in the source data.</span></span>  
  
 <span data-ttu-id="f1871-137">あるレベルの `SourceAttribute` プロパティには、そのレベルの記述に使用する属性を指定します。</span><span class="sxs-lookup"><span data-stu-id="f1871-137">The `SourceAttribute` property of a level determines which attribute is used to describe the level.</span></span> <span data-ttu-id="f1871-138">属性の `KeyColumns` プロパティには、メンバーの取り込み元のデータ ソース ビューの列を指定します。</span><span class="sxs-lookup"><span data-stu-id="f1871-138">The `KeyColumns` property on the attribute specifies the column in the data source view that supplies the members.</span></span> <span data-ttu-id="f1871-139">属性の `NameColumn` プロパティには、別の名前列をメンバーに対して指定できます。</span><span class="sxs-lookup"><span data-stu-id="f1871-139">The `NameColumn` property on the attribute can specify a different name column for the members.</span></span>  
  
 <span data-ttu-id="f1871-140">を使用してユーザー定義階層内のレベルを定義するには [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 、ディメンション**デザイナー**でディメンション属性、ディメンションテーブルの列、またはキューブのデータソースビューに含まれる関連テーブルの列を選択します。</span><span class="sxs-lookup"><span data-stu-id="f1871-140">To define a level in a user-defined hierarchy using [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], the **Dimension Designer** allows you to select a dimension attribute, a column in a dimension table, or a column from a related table included in the data source view for the cube.</span></span> <span data-ttu-id="f1871-141">ユーザー定義階層の作成の詳細については、「[ユーザー定義階層の作成](../multidimensional-models/user-defined-hierarchies-create.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f1871-141">For more information about creating user-defined hierarchies, see [Create User-Defined Hierarchies](../multidimensional-models/user-defined-hierarchies-create.md).</span></span>  
  
 <span data-ttu-id="f1871-142">Analysis Services では通常、メンバーの内容が想定されています。</span><span class="sxs-lookup"><span data-stu-id="f1871-142">In Analysis Services, an assumption is usually made about the content of members.</span></span> <span data-ttu-id="f1871-143">リーフ メンバーには子孫がなく、元のデータ ソースから派生したデータが含まれています。</span><span class="sxs-lookup"><span data-stu-id="f1871-143">Leaf members have no descendents and contain data derived from underlying data sources.</span></span> <span data-ttu-id="f1871-144">非リーフ メンバーには子孫があり、子メンバーで実行した集計から派生したデータが含まれています。</span><span class="sxs-lookup"><span data-stu-id="f1871-144">Nonleaf members have descendents and contain data derived from aggregations performed on child members.</span></span> <span data-ttu-id="f1871-145">集計レベルのメンバーは、下位レベルの集計が基になっています。</span><span class="sxs-lookup"><span data-stu-id="f1871-145">In aggregated levels, members are based on aggregations of subordinate levels.</span></span> <span data-ttu-id="f1871-146">したがって、あるレベルのソース属性の `IsAggregatable` プロパティを `False` に設定するときは、集計可能な属性をこれより上位のレベルとして追加しないでください。</span><span class="sxs-lookup"><span data-stu-id="f1871-146">Therefore, when the `IsAggregatable` property is set to `False` on a source attribute for a level, no aggregatable attributes should be added as levels above it.</span></span>  
  
## <a name="defining-an-attribute-relationship"></a><span data-ttu-id="f1871-147">属性リレーションシップの定義</span><span class="sxs-lookup"><span data-stu-id="f1871-147">Defining an Attribute Relationship</span></span>  
 <span data-ttu-id="f1871-148">属性リレーションシップを作成するときの主な制約は、属性リレーションシップによって参照される属性に、属性リレーションシップが所属する属性のメンバーの値が 2 つ以上含まれていないことを確認する必要があることです。</span><span class="sxs-lookup"><span data-stu-id="f1871-148">The main constraint when you create an attribute relationship is to make sure that the attribute referred to by the attribute relationship has no more than one value for any member in the attribute to which the attribute relationship belongs.</span></span> <span data-ttu-id="f1871-149">たとえば、City 属性と State 属性の間のリレーションシップを定義する場合、それぞれの市区町村は 1 つの都道府県にのみ関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="f1871-149">For example, if you define a relationship between a City attribute and a State attribute, each city can only relate to a single state.</span></span>  
  
## <a name="attribute-relationship-queries"></a><span data-ttu-id="f1871-150">属性リレーションシップのクエリ</span><span class="sxs-lookup"><span data-stu-id="f1871-150">Attribute Relationship Queries</span></span>  
 <span data-ttu-id="f1871-151">MDX クエリを使用すると、MDX `PROPERTIES` ステートメントの `SELECT` キーワードを指定することにより、メンバーのプロパティの形式で属性リレーションシップからデータを取得することができます。</span><span class="sxs-lookup"><span data-stu-id="f1871-151">You can use MDX queries to retrieve data from attribute relationships, in the form of member properties, with the `PROPERTIES` keyword of the MDX `SELECT` statement.</span></span> <span data-ttu-id="f1871-152">MDX を使用してメンバープロパティを取得する方法の詳細については、「 [mdx&#41;&#40;メンバープロパティを使用](../multidimensional-models/mdx/mdx-member-properties.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f1871-152">For more information about how to use MDX to retrieve member properties, see [Using Member Properties &#40;MDX&#41;](../multidimensional-models/mdx/mdx-member-properties.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1871-153">参照</span><span class="sxs-lookup"><span data-stu-id="f1871-153">See Also</span></span>  
 <span data-ttu-id="f1871-154">[属性と属性階層](attributes-and-attribute-hierarchies.md) </span><span class="sxs-lookup"><span data-stu-id="f1871-154">[Attributes and Attribute Hierarchies](attributes-and-attribute-hierarchies.md) </span></span>  
 <span data-ttu-id="f1871-155">[ディメンションの属性のプロパティのリファレンス](../multidimensional-models/dimension-attribute-properties-reference.md) </span><span class="sxs-lookup"><span data-stu-id="f1871-155">[Dimension Attribute Properties Reference](../multidimensional-models/dimension-attribute-properties-reference.md) </span></span>  
 <span data-ttu-id="f1871-156">[ユーザー階層](user-hierarchies.md) </span><span class="sxs-lookup"><span data-stu-id="f1871-156">[User Hierarchies](user-hierarchies.md) </span></span>  
 [<span data-ttu-id="f1871-157">ユーザー階層プロパティ</span><span class="sxs-lookup"><span data-stu-id="f1871-157">User Hierarchy Properties</span></span>](user-hierarchies-properties.md)  
  
  
