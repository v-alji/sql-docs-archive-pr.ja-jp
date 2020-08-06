---
title: 階層 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- hierarchies [Master Data Services]
- hierarchies [Master Data Services], about hierarchies
ms.assetid: 70dbb1fc-ead7-45be-9552-a45e3ccd8d21
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 126a01c03134c6859426c09fda398408694795f5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642145"
---
# <a name="hierarchies-master-data-services"></a><span data-ttu-id="c1810-102">階層 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="c1810-102">Hierarchies (Master Data Services)</span></span>
  <span data-ttu-id="c1810-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]の階層とは、次の処理に使用できるツリー構造です。</span><span class="sxs-lookup"><span data-stu-id="c1810-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], a hierarchy is a tree structure that you can use to:</span></span>

-   <span data-ttu-id="c1810-104">編成を目的として、類似するメンバーをグループ化する。</span><span class="sxs-lookup"><span data-stu-id="c1810-104">Group similar members for organizational purposes.</span></span>

-   <span data-ttu-id="c1810-105">レポートと分析のために、メンバーを統合し集計する。</span><span class="sxs-lookup"><span data-stu-id="c1810-105">Consolidate and summarize members for reporting and analysis.</span></span>

## <a name="what-hierarchies-contain"></a><span data-ttu-id="c1810-106">階層の内容</span><span class="sxs-lookup"><span data-stu-id="c1810-106">What Hierarchies Contain</span></span>
 <span data-ttu-id="c1810-107">各階層には、1 つ以上のエンティティのメンバーが含まれます。</span><span class="sxs-lookup"><span data-stu-id="c1810-107">Each hierarchy contains members from one or more entities.</span></span> <span data-ttu-id="c1810-108">メンバーを追加、変更、または削除すると、すべての階層が更新されます。</span><span class="sxs-lookup"><span data-stu-id="c1810-108">When a member is added, changed, or deleted, all hierarchies are updated.</span></span> <span data-ttu-id="c1810-109">これにより、すべての階層でデータの正確さが確保されます。</span><span class="sxs-lookup"><span data-stu-id="c1810-109">This ensures that the data is accurate in all hierarchies.</span></span> <span data-ttu-id="c1810-110">また、階層を使用すると、各メンバーが 1 回だけカウントされるようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="c1810-110">Hierarchies also help ensure that each member is counted once and only once.</span></span>

 <span data-ttu-id="c1810-111">メンバーのサブセットのグループを作成する場合は、コレクションの使用を検討してください。</span><span class="sxs-lookup"><span data-stu-id="c1810-111">If you want to create a grouping of a subset of members, consider using a collection.</span></span> <span data-ttu-id="c1810-112">詳細については、「 [コレクション (マスター データ サービス)](collections-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c1810-112">For more information, see [Collections &#40;Master Data Services&#41;](collections-master-data-services.md).</span></span>

## <a name="kinds-of-hierarchies"></a><span data-ttu-id="c1810-113">階層の種類</span><span class="sxs-lookup"><span data-stu-id="c1810-113">Kinds of Hierarchies</span></span>
 <span data-ttu-id="c1810-114">さまざまな方法でメンバーを表示したり編成したりするために、複数の階層を作成できます。</span><span class="sxs-lookup"><span data-stu-id="c1810-114">You can create multiple hierarchies to view and organize your members in different ways.</span></span> <span data-ttu-id="c1810-115">次の階層を作成できます。</span><span class="sxs-lookup"><span data-stu-id="c1810-115">You can create:</span></span>

-   <span data-ttu-id="c1810-116">明示的階層と呼ばれる、単一エンティティから作成される不規則階層。</span><span class="sxs-lookup"><span data-stu-id="c1810-116">Ragged hierarchies from a single entity, which are called explicit hierarchies.</span></span> <span data-ttu-id="c1810-117">詳細については、「 [明示的階層 (マスター データ サービス)](../../2014/master-data-services/explicit-hierarchies-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c1810-117">For more information, see [Explicit Hierarchies &#40;Master Data Services&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md).</span></span>

-   <span data-ttu-id="c1810-118">派生階層と呼ばれる、複数のエンティティと属性間の既存のリレーションシップに基づいて作成されるレベル ベースの階層。</span><span class="sxs-lookup"><span data-stu-id="c1810-118">Level-based hierarchies from multiple entities, based on the existing relationships between entities and their attributes, which are called derived hierarchies.</span></span> <span data-ttu-id="c1810-119">詳細については、「 [派生階層 (マスター データ サービス)](../../2014/master-data-services/derived-hierarchies-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c1810-119">For more information, see [Derived Hierarchies &#40;Master Data Services&#41;](../../2014/master-data-services/derived-hierarchies-master-data-services.md).</span></span>

> [!NOTE]
>  <span data-ttu-id="c1810-120">階層内のすべてのメンバーは、同じモデル内に含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="c1810-120">All members in a hierarchy must be within the same model.</span></span>

## <a name="hierarchies-are-not-taxonomies"></a><span data-ttu-id="c1810-121">階層と分類の相違</span><span class="sxs-lookup"><span data-stu-id="c1810-121">Hierarchies Are Not Taxonomies</span></span>
 <span data-ttu-id="c1810-122">階層は分類とは異なります。</span><span class="sxs-lookup"><span data-stu-id="c1810-122">A hierarchy is different from a taxonomy.</span></span> <span data-ttu-id="c1810-123">分類ではメンバーを一度に複数の属性で編成しますが、階層ではメンバーを一度に 1 つの属性で編成します。</span><span class="sxs-lookup"><span data-stu-id="c1810-123">A taxonomy organizes members by multiple attributes at the same time, while a hierarchy organizes members by one attribute at a time.</span></span> <span data-ttu-id="c1810-124">分類には同じメンバーを複数回含めることができますが、階層には一度しか含めることができません。</span><span class="sxs-lookup"><span data-stu-id="c1810-124">A taxonomy can include the same member multiple times, while a hierarchy includes a member only once.</span></span>

 <span data-ttu-id="c1810-125">たとえば、分類には同じ自転車を 2 回含めることができます。つまり、一度は赤色という理由で、もう一度はサイズが 38 という理由で含めることができます。</span><span class="sxs-lookup"><span data-stu-id="c1810-125">For example, the same bike can be included in a taxonomy twice: once because it's red, and once because it's a size 38.</span></span> <span data-ttu-id="c1810-126">階層には、自転車は一度しか含められないので、色かサイズのどちらの関連で示すかを決定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c1810-126">In a hierarchy, the bike is included only once, so you must decide whether to show it in relation to its color or its size.</span></span>

## <a name="hierarchy-example"></a><span data-ttu-id="c1810-127">階層の例</span><span class="sxs-lookup"><span data-stu-id="c1810-127">Hierarchy Example</span></span>
 <span data-ttu-id="c1810-128">次の例では、製品メンバーはサブカテゴリ メンバーごとにグループ化されます。</span><span class="sxs-lookup"><span data-stu-id="c1810-128">In the following example, product members are grouped by subcategory members.</span></span>

 <span data-ttu-id="c1810-129">![サブカテゴリごとにグループ化された階層の例](../../2014/master-data-services/media/mds-conc-hierarchy.gif "サブカテゴリごとにグループ化された階層の例")</span><span class="sxs-lookup"><span data-stu-id="c1810-129">![Hierarchy Grouped by Subcategory Example](../../2014/master-data-services/media/mds-conc-hierarchy.gif "Hierarchy Grouped by Subcategory Example")</span></span>

## <a name="related-tasks"></a><span data-ttu-id="c1810-130">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="c1810-130">Related Tasks</span></span>

|<span data-ttu-id="c1810-131">タスクの説明</span><span class="sxs-lookup"><span data-stu-id="c1810-131">Task Description</span></span>|<span data-ttu-id="c1810-132">トピック</span><span class="sxs-lookup"><span data-stu-id="c1810-132">Topic</span></span>|
|----------------------|-----------|
|<span data-ttu-id="c1810-133">明示的階層とコレクションに対してエンティティを有効にする。</span><span class="sxs-lookup"><span data-stu-id="c1810-133">Enable an entity for explicit hierarchies and collections.</span></span>|[<span data-ttu-id="c1810-134">明示的階層およびコレクションに対してエンティティを有効にする &#40;マスターデータサービス&#41;</span><span class="sxs-lookup"><span data-stu-id="c1810-134">Enable an Entity for Explicit Hierarchies and Collections &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/enable-an-entity-for-explicit-hierarchies-and-collections-master-data-services.md)|
|<span data-ttu-id="c1810-135">明示的階層を作成する。</span><span class="sxs-lookup"><span data-stu-id="c1810-135">Create a explicit hierarchy.</span></span>|[<span data-ttu-id="c1810-136">明示的階層を作成する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="c1810-136">Create an Explicit Hierarchy &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-an-explicit-hierarchy-master-data-services.md)|
|<span data-ttu-id="c1810-137">派生階層を作成する。</span><span class="sxs-lookup"><span data-stu-id="c1810-137">Create a derived hierarchy.</span></span>|[<span data-ttu-id="c1810-138">派生階層を作成する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="c1810-138">Create a Derived Hierarchy &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-derived-hierarchy-master-data-services.md)|
|<span data-ttu-id="c1810-139">既存の派生階層のレベルを非表示にするか、または削除する。</span><span class="sxs-lookup"><span data-stu-id="c1810-139">Hide or delete levels in an existing derived hierarchy.</span></span>|[<span data-ttu-id="c1810-140">派生階層のレベルを非表示にするか削除する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="c1810-140">Hide or Delete Levels in a Derived Hierarchy &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/hide-or-delete-levels-in-a-derived-hierarchy-master-data-services.md)|

## <a name="related-content"></a><span data-ttu-id="c1810-141">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="c1810-141">Related Content</span></span>

-   [<span data-ttu-id="c1810-142">明示的階層 (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="c1810-142">Explicit Hierarchies &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/explicit-hierarchies-master-data-services.md)

-   [<span data-ttu-id="c1810-143">派生階層 (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="c1810-143">Derived Hierarchies &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/derived-hierarchies-master-data-services.md)

-   [<span data-ttu-id="c1810-144">再帰型階層 (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="c1810-144">Recursive Hierarchies &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/recursive-hierarchies-master-data-services.md)

-   [<span data-ttu-id="c1810-145">明示的なキャップを持つ派生階層 (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="c1810-145">Derived Hierarchies with Explicit Caps &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/derived-hierarchies-with-explicit-caps-master-data-services.md)

-   [<span data-ttu-id="c1810-146">コレクション (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="c1810-146">Collections &#40;Master Data Services&#41;</span></span>](collections-master-data-services.md)


