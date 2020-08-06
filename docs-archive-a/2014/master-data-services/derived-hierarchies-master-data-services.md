---
title: 派生階層 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- derived hierarchies
- hierarchies [Master Data Services], derived hierarchies
- derived hierarchies, about derived hierarchies
ms.assetid: a0fbd519-a10e-4cbd-92e6-5de9b8d3e3f0
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 92867f225a8f14e59cb9a519f174902d0739773a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646193"
---
# <a name="derived-hierarchies-master-data-services"></a><span data-ttu-id="adc72-102">派生階層 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="adc72-102">Derived Hierarchies (Master Data Services)</span></span>
  <span data-ttu-id="adc72-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] の派生階層は、モデル内のエンティティ間に既に存在するドメインベースの属性のリレーションシップから派生します。</span><span class="sxs-lookup"><span data-stu-id="adc72-103">A [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] derived hierarchy is derived from the domain-based attribute relationships that already exist between entities in a model.</span></span>

 <span data-ttu-id="adc72-104">派生階層を作成することで、モデル内の既存のドメイン ベースの属性リレーションシップを強調表示できます。</span><span class="sxs-lookup"><span data-stu-id="adc72-104">You can create a derived hierarchy to highlight any of the existing domain-based attribute relationships in the model.</span></span>

## <a name="leaf-members-group-other-leaf-members"></a><span data-ttu-id="adc72-105">他のリーフ メンバーをグループ化するリーフメンバー</span><span class="sxs-lookup"><span data-stu-id="adc72-105">Leaf Members Group Other Leaf Members</span></span>
 <span data-ttu-id="adc72-106">派生階層では、1 つのエンティティのリーフ メンバーを使用して別のエンティティのリーフ メンバーをグループ化します。</span><span class="sxs-lookup"><span data-stu-id="adc72-106">In a derived hierarchy, the leaf members from one entity are used to group the leaf members of another entity.</span></span> <span data-ttu-id="adc72-107">派生階層は、これらのエンティティの間のリレーションシップに基づいています。</span><span class="sxs-lookup"><span data-stu-id="adc72-107">A derived hierarchy is based on the relationship between these entities.</span></span> <span data-ttu-id="adc72-108">これに対し、明示的階層は単一エンティティのメンバーに基づき、指定した任意の方法で構造化されます。</span><span class="sxs-lookup"><span data-stu-id="adc72-108">An explicit hierarchy, in contrast, is based on members from a single entity only and is structured in any way you specify.</span></span>

 <span data-ttu-id="adc72-109">派生階層の構造は、基になるデータに影響を与えることなく変更できます。</span><span class="sxs-lookup"><span data-stu-id="adc72-109">You can change the structure of a derived hierarchy without affecting the underlying data.</span></span> <span data-ttu-id="adc72-110">モデル内にリレーションシップが存在している限り、派生階層を削除してもマスター データには影響しません。</span><span class="sxs-lookup"><span data-stu-id="adc72-110">As long as the relationships still exist in the model, deleting a derived hierarchy has no effect on your master data.</span></span>

## <a name="explicit-hierarchies-versus-derived-hierarchies"></a><span data-ttu-id="adc72-111">明示的階層と派生階層</span><span class="sxs-lookup"><span data-stu-id="adc72-111">Explicit Hierarchies versus Derived Hierarchies</span></span>
 <span data-ttu-id="adc72-112">次の表は、明示的階層と派生階層の相違点の一部を示しています。</span><span class="sxs-lookup"><span data-stu-id="adc72-112">The following table shows some of the differences between explicit and derived hierarchies.</span></span>

|<span data-ttu-id="adc72-113">明示的階層</span><span class="sxs-lookup"><span data-stu-id="adc72-113">Explicit Hierarchies</span></span>|<span data-ttu-id="adc72-114">派生階層</span><span class="sxs-lookup"><span data-stu-id="adc72-114">Derived Hierarchies</span></span>|
|--------------------------|-------------------------|
|<span data-ttu-id="adc72-115">構造はユーザーによって定義される</span><span class="sxs-lookup"><span data-stu-id="adc72-115">Structure is defined by the user</span></span>|<span data-ttu-id="adc72-116">構造はドメイン ベースの属性間のリレーションシップから派生する</span><span class="sxs-lookup"><span data-stu-id="adc72-116">Structure is derived from the relationships between domain-based attributes</span></span>|
|<span data-ttu-id="adc72-117">単一のエンティティからのメンバーを含む</span><span class="sxs-lookup"><span data-stu-id="adc72-117">Contains members from a single entity</span></span>|<span data-ttu-id="adc72-118">複数のエンティティからのメンバーを含む</span><span class="sxs-lookup"><span data-stu-id="adc72-118">Contains members from multiple entities</span></span>|
|<span data-ttu-id="adc72-119">他のメンバーをグループ化する統合メンバーを使用する</span><span class="sxs-lookup"><span data-stu-id="adc72-119">Uses consolidated members to group other members</span></span>|<span data-ttu-id="adc72-120">1 つのエンティティのリーフ メンバーを使用して、別のエンティティのリーフ メンバーをグループ化する</span><span class="sxs-lookup"><span data-stu-id="adc72-120">Uses leaf members from one entity to group leaf members from another entity</span></span>|
|<span data-ttu-id="adc72-121">不規則になる場合がある</span><span class="sxs-lookup"><span data-stu-id="adc72-121">Can be ragged</span></span>|<span data-ttu-id="adc72-122">常に一定のレベル数を含む</span><span class="sxs-lookup"><span data-stu-id="adc72-122">Always contains a consistent number of levels</span></span>|

## <a name="creating-a-variable-depth-hierarchy"></a><span data-ttu-id="adc72-123">変数の深さ階層の作成</span><span class="sxs-lookup"><span data-stu-id="adc72-123">Creating a Variable-Depth Hierarchy</span></span>
 <span data-ttu-id="adc72-124">変数の深さ階層の作成方法として、次の 2 種類の方法をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="adc72-124">There are two recommended ways to create a variable-depth hierarchy:</span></span>

-   <span data-ttu-id="adc72-125">すべてのレベルの属性を同じにする場合は、単一のエンティティを作成してから、エンティティに基づくドメイン ベースの属性を使用してそのエンティティの再帰型階層を作成します。</span><span class="sxs-lookup"><span data-stu-id="adc72-125">If you need all levels to have the same attributes, create a single entity, and then create a recursive hierarchy on this entity, using a domain-based attribute that is based on the entity.</span></span>

-   <span data-ttu-id="adc72-126">リーフ メンバーに 1 セットの属性が必要で、上位レベルにはもう 1 セット属性が必要な場合は、派生階層に 2 つのエンティティを作成します。</span><span class="sxs-lookup"><span data-stu-id="adc72-126">If you need one set of attributes for the leaf members and another set of attributes in the upper levels, create two entities for a derived hierarchy.</span></span> <span data-ttu-id="adc72-127">リーフ エンティティに対しては、親エンティティに基づくドメイン ベースの属性を使用します。</span><span class="sxs-lookup"><span data-stu-id="adc72-127">For the leaf entity, use a domain-based attribute that is based upon the parent entity.</span></span> <span data-ttu-id="adc72-128">親エンティティに対しては、親エンティティ自体に基づくドメイン ベースの属性を使用します。</span><span class="sxs-lookup"><span data-stu-id="adc72-128">For the parent entity, use a domain-based attribute that is based upon itself.</span></span>

## <a name="derived-hierarchy-example"></a><span data-ttu-id="adc72-129">派生階層の例</span><span class="sxs-lookup"><span data-stu-id="adc72-129">Derived Hierarchy Example</span></span>
 <span data-ttu-id="adc72-130">次の例では、Product エンティティのリーフ メンバーは Subcategory エンティティのリーフ メンバーによってグループ化されています。Subcategory エンティティは、Category エンティティのリーフ メンバーによってグループ化されています。</span><span class="sxs-lookup"><span data-stu-id="adc72-130">In the following example, leaf members of the Product entity are grouped by leaf members of the Subcategory entity, which are then grouped by leaf members of the Category entity.</span></span> <span data-ttu-id="adc72-131">Product エンティティには Subcategory というドメイン ベースの属性があり、Subcategory エンティティには Category というドメイン ベースの属性があるので、この階層は有効です。</span><span class="sxs-lookup"><span data-stu-id="adc72-131">This hierarchy is possible because the Product entity has a domain-based attribute named Subcategory, and the Subcategory entity has a domain-based attribute named Category.</span></span>

 <span data-ttu-id="adc72-132">階層構造は、メンバーがグループ化されている方法を示します。</span><span class="sxs-lookup"><span data-stu-id="adc72-132">The hierarchy structure shows how the members are grouped.</span></span> <span data-ttu-id="adc72-133">ほとんどのメンバーを持つエンティティは一番下に位置します。</span><span class="sxs-lookup"><span data-stu-id="adc72-133">The entity with the most members is at the bottom.</span></span>

 <span data-ttu-id="adc72-134">![モデル構造から派生した階層](../../2014/master-data-services/media/mds-conc-derived-hierarchy-structure.gif "モデル構造から派生した階層")</span><span class="sxs-lookup"><span data-stu-id="adc72-134">![Hierarchy Derived from Model Structure](../../2014/master-data-services/media/mds-conc-derived-hierarchy-structure.gif "Hierarchy Derived from Model Structure")</span></span>

 <span data-ttu-id="adc72-135">派生階層では、Product と Subcategory 間のリレーションシップを強調表示してから、Subcategory と Category 間のリレーションシップを強調表示できます。</span><span class="sxs-lookup"><span data-stu-id="adc72-135">In a derived hierarchy, you can highlight the relationship between Product and Subcategory, and then between Subcategory and Category.</span></span> <span data-ttu-id="adc72-136">この階層内にメンバーを表示すると、ツリー内の各レベルに同じエンティティのメンバーが含まれています。</span><span class="sxs-lookup"><span data-stu-id="adc72-136">When you view the members in this hierarchy, each level in the tree contains members from the same entity.</span></span>

 <span data-ttu-id="adc72-137">![マウンテン バイク派生階層の例](../../2014/master-data-services/media/mds-conc-derived-hierarchy-example.gif "マウンテン バイク派生階層の例")</span><span class="sxs-lookup"><span data-stu-id="adc72-137">![Mountain Bike Derived Hierarchy Example](../../2014/master-data-services/media/mds-conc-derived-hierarchy-example.gif "Mountain Bike Derived Hierarchy Example")</span></span>

 <span data-ttu-id="adc72-138">この種類の階層では、無効なレベルにメンバーを移動できません。</span><span class="sxs-lookup"><span data-stu-id="adc72-138">This type of hierarchy prevents you from moving a member to a level that is not valid.</span></span> <span data-ttu-id="adc72-139">たとえば、自転車 Road-650 は、Road Bikes というサブカテゴリから Mountain Bikes という別のサブカテゴリに移動することはできますが、</span><span class="sxs-lookup"><span data-stu-id="adc72-139">For example, you can move the Road-650 bike from one subcategory, Road Bikes, to another, Mountain Bikes.</span></span> <span data-ttu-id="adc72-140">1 {Bikes} などのカテゴリの直下に移動することはできません。</span><span class="sxs-lookup"><span data-stu-id="adc72-140">You cannot move Road-650 directly under a category, like 1 {Bikes}.</span></span> <span data-ttu-id="adc72-141">階層ツリー内でメンバーを移動するたびに、メンバーのドメイン ベースの属性値は、移動を反映して変更されます。</span><span class="sxs-lookup"><span data-stu-id="adc72-141">Each time you move a member in the hierarchy tree, the member's domain-based attribute value changes to reflect the move.</span></span>

## <a name="notes"></a><span data-ttu-id="adc72-142">Notes</span><span class="sxs-lookup"><span data-stu-id="adc72-142">Notes</span></span>
 <span data-ttu-id="adc72-143">派生階層ツリー内のすべてのメンバーは、コードによって並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="adc72-143">All members in a derived hierarchy tree are sorted by code.</span></span> <span data-ttu-id="adc72-144">並べ替え順序は変更できません。</span><span class="sxs-lookup"><span data-stu-id="adc72-144">You cannot change the sort order.</span></span>

 <span data-ttu-id="adc72-145">メンバーのドメイン ベースの属性が空で、その属性が派生階層で使用される場合、そのメンバーは階層内に表示されません。</span><span class="sxs-lookup"><span data-stu-id="adc72-145">If a member's domain-based attribute is blank and the attribute is used for a derived hierarchy, the member is not displayed in the hierarchy.</span></span> <span data-ttu-id="adc72-146">属性への値の設定を要求するビジネス ルールを作成してください。</span><span class="sxs-lookup"><span data-stu-id="adc72-146">Create business rules to require attributes to be populated.</span></span> <span data-ttu-id="adc72-147">詳細については、「[属性値を要求する &#40;マスター データ サービス&#41;](require-attribute-values-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="adc72-147">For more information, see [Require Attribute Values &#40;Master Data Services&#41;](require-attribute-values-master-data-services.md).</span></span>

## <a name="related-tasks"></a><span data-ttu-id="adc72-148">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="adc72-148">Related Tasks</span></span>

|<span data-ttu-id="adc72-149">タスクの説明</span><span class="sxs-lookup"><span data-stu-id="adc72-149">Task Description</span></span>|<span data-ttu-id="adc72-150">トピック</span><span class="sxs-lookup"><span data-stu-id="adc72-150">Topic</span></span>|
|----------------------|-----------|
|<span data-ttu-id="adc72-151">新しい派生階層を作成する。</span><span class="sxs-lookup"><span data-stu-id="adc72-151">Create a new derived hierarchy.</span></span>|[<span data-ttu-id="adc72-152">派生階層を作成する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="adc72-152">Create a Derived Hierarchy &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-derived-hierarchy-master-data-services.md)|
|<span data-ttu-id="adc72-153">既存の派生階層のレベルを非表示にするか、または削除する。</span><span class="sxs-lookup"><span data-stu-id="adc72-153">Hide or delete levels in an existing derived hierarchy.</span></span>|[<span data-ttu-id="adc72-154">派生階層のレベルを非表示にするか削除する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="adc72-154">Hide or Delete Levels in a Derived Hierarchy &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/hide-or-delete-levels-in-a-derived-hierarchy-master-data-services.md)|
|<span data-ttu-id="adc72-155">既存の派生階層の名前を変更する。</span><span class="sxs-lookup"><span data-stu-id="adc72-155">Change the name of an existing derived hierarchy.</span></span>|[<span data-ttu-id="adc72-156">派生階層名を変更する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="adc72-156">Change a Derived Hierarchy Name &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/change-a-derived-hierarchy-name-master-data-services.md)|
|<span data-ttu-id="adc72-157">既存の派生階層を削除する。</span><span class="sxs-lookup"><span data-stu-id="adc72-157">Delete an existing derived hierarchy.</span></span>|[<span data-ttu-id="adc72-158">派生階層を削除する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="adc72-158">Delete a Derived Hierarchy &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/delete-a-derived-hierarchy-master-data-services.md)|
|||

## <a name="related-content"></a><span data-ttu-id="adc72-159">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="adc72-159">Related Content</span></span>

-   [<span data-ttu-id="adc72-160">ドメインベースの属性 (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="adc72-160">Domain-Based Attributes &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/domain-based-attributes-master-data-services.md)

-   [<span data-ttu-id="adc72-161">明示的階層 (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="adc72-161">Explicit Hierarchies &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/explicit-hierarchies-master-data-services.md)

-   [<span data-ttu-id="adc72-162">再帰型階層 (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="adc72-162">Recursive Hierarchies &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/recursive-hierarchies-master-data-services.md)

-   [<span data-ttu-id="adc72-163">明示的なキャップを持つ派生階層 (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="adc72-163">Derived Hierarchies with Explicit Caps &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/derived-hierarchies-with-explicit-caps-master-data-services.md)

-   [<span data-ttu-id="adc72-164">コレクション (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="adc72-164">Collections &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/collections-master-data-services.md)


