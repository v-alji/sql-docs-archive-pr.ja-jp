---
title: コレクション (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- collections [Master Data Services]
- collections [Master Data Services], about collections
ms.assetid: 5aa1d1e0-b4e5-4897-8e74-01dcf418df73
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: ce49c57aad5da52dabba32a0f3fb9b6f4f45b209
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715553"
---
# <a name="collections-master-data-services"></a><span data-ttu-id="db69f-102">コレクション (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="db69f-102">Collections (Master Data Services)</span></span>
  <span data-ttu-id="db69f-103">コレクションは、1 つのエンティティのリーフ メンバーと統合メンバーのグループです。</span><span class="sxs-lookup"><span data-stu-id="db69f-103">A collection is a group of leaf and consolidated members from a single entity.</span></span> <span data-ttu-id="db69f-104">コレクションは、完全な階層を必要としない場合で、レポートまたは分析のためにメンバーのさまざまなグループを表示するとき、または分類を作成する必要があるときに使用します。</span><span class="sxs-lookup"><span data-stu-id="db69f-104">Use collections when you do not need a complete hierarchy and you want to view different groupings of members for reporting or analysis, or when you need to create a taxonomy.</span></span>  
  
## <a name="what-collections-contain"></a><span data-ttu-id="db69f-105">コレクションに含められるもの</span><span class="sxs-lookup"><span data-stu-id="db69f-105">What Collections Contain</span></span>  
 <span data-ttu-id="db69f-106">コレクションは、メンバーが同じエンティティ内に存在する限り、含めることができるメンバーの数または種類が制限されません。</span><span class="sxs-lookup"><span data-stu-id="db69f-106">Collections do not limit the number or type of members you can include, as long as the members are within the same entity.</span></span> <span data-ttu-id="db69f-107">コレクションには、複数の必須および任意の明示的階層に属するリーフ メンバーと統合メンバーを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="db69f-107">A collection can contain leaf and consolidated members from multiple mandatory and non-mandatory explicit hierarchies.</span></span>  
  
 <span data-ttu-id="db69f-108">コレクションを作成しても、階層構造は作成されません。作成されるのはメンバーのフラット リストです。</span><span class="sxs-lookup"><span data-stu-id="db69f-108">When you create a collection, you are not creating a hierarchical structure; you are creating a flat list of members.</span></span> <span data-ttu-id="db69f-109">階層からノードを選択し、コレクションに追加すると、選択した統合メンバーだけがコレクションに追加されます。</span><span class="sxs-lookup"><span data-stu-id="db69f-109">When you select a node from a hierarchy and add it to the collection, the consolidated member you selected is the only member added to the collection.</span></span>  
  
 <span data-ttu-id="db69f-110">コレクションに他のコレクションを含めることもできます。</span><span class="sxs-lookup"><span data-stu-id="db69f-110">A collection can also contain other collections.</span></span> <span data-ttu-id="db69f-111">コレクションのコレクションを使用して、分類を作成できます。</span><span class="sxs-lookup"><span data-stu-id="db69f-111">You can use collections of collections to create taxonomies.</span></span>  
  
 <span data-ttu-id="db69f-112">コレクションを作成すると、作成者は所有者として自動的に一覧に表示されます。</span><span class="sxs-lookup"><span data-stu-id="db69f-112">When you create a collection you are automatically listed as the owner.</span></span> <span data-ttu-id="db69f-113">管理者の場合は、必要に応じて、コレクションの他の属性を作成できます。</span><span class="sxs-lookup"><span data-stu-id="db69f-113">If you are an administrator, you can create other attributes for your collection as needed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="db69f-114">コレクションを作成するには、明示的階層でエンティティを有効にしておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="db69f-114">Before you can create a collection, the entity must be enabled for explicit hierarchies.</span></span> <span data-ttu-id="db69f-115">詳細については、「[明示的階層とコレクションのエンティティの有効化 &#40;マスターデータサービス&#41;](enable-an-entity-for-explicit-hierarchies-and-collections-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="db69f-115">For more information, see [Enable an Entity for Explicit Hierarchies and Collections &#40;Master Data Services&#41;](enable-an-entity-for-explicit-hierarchies-and-collections-master-data-services.md).</span></span>  
  
## <a name="subscription-views-for-collections"></a><span data-ttu-id="db69f-116">コレクションのサブスクリプション ビュー</span><span class="sxs-lookup"><span data-stu-id="db69f-116">Subscription Views for Collections</span></span>  
 <span data-ttu-id="db69f-117">コレクションを表示するサブスクリプション ビューには 2 つの種類があります。</span><span class="sxs-lookup"><span data-stu-id="db69f-117">There are two types of subscription views that show collections.</span></span> <span data-ttu-id="db69f-118">**コレクション属性** 形式では、コレクションのリストと、コレクションに関係のある属性 (説明や所有者など) の一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="db69f-118">The **Collection attributes** format shows a list of collections and any attributes related to the collections (like description or owner).</span></span> <span data-ttu-id="db69f-119">**コレクション** 形式では、すべてのコレクション内のすべてのメンバーと、各メンバーの重みおよび並べ替え順序が表示されます。</span><span class="sxs-lookup"><span data-stu-id="db69f-119">The **Collections** format shows all members in all collections, as well as each members weight and sort order.</span></span> <span data-ttu-id="db69f-120">詳細については、「[データ &#40;マスターデータサービス&#41;のエクスポート](overview-exporting-data-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="db69f-120">For more information, see [Exporting Data &#40;Master Data Services&#41;](overview-exporting-data-master-data-services.md).</span></span>  
  
 <span data-ttu-id="db69f-121">コレクションで特定のメンバーに重みの値を設定した場合、関連するサブスクリプション ビューでその値を使用できます。</span><span class="sxs-lookup"><span data-stu-id="db69f-121">If you set weight values for specific members in a collection, these values are available in related subscription views.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="db69f-122">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="db69f-122">Related Tasks</span></span>  
  
|<span data-ttu-id="db69f-123">タスクの説明</span><span class="sxs-lookup"><span data-stu-id="db69f-123">Task Description</span></span>|<span data-ttu-id="db69f-124">トピック</span><span class="sxs-lookup"><span data-stu-id="db69f-124">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="db69f-125">明示的階層とコレクションに対してエンティティを有効にする。</span><span class="sxs-lookup"><span data-stu-id="db69f-125">Enable an entity for explicit hierarchies and collections.</span></span>|[<span data-ttu-id="db69f-126">明示的階層およびコレクションに対してエンティティを有効にする &#40;マスターデータサービス&#41;</span><span class="sxs-lookup"><span data-stu-id="db69f-126">Enable an Entity for Explicit Hierarchies and Collections &#40;Master Data Services&#41;</span></span>](enable-an-entity-for-explicit-hierarchies-and-collections-master-data-services.md)|  
|<span data-ttu-id="db69f-127">新しいコレクションを作成する。</span><span class="sxs-lookup"><span data-stu-id="db69f-127">Create a new collection.</span></span>|[<span data-ttu-id="db69f-128">コレクションを作成する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="db69f-128">Create a Collection &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-collection-master-data-services.md)|  
|<span data-ttu-id="db69f-129">既存のコレクションにメンバーを追加する。</span><span class="sxs-lookup"><span data-stu-id="db69f-129">Add members to an existing collection.</span></span>|[<span data-ttu-id="db69f-130">コレクションにメンバーを追加する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="db69f-130">Add Members to a Collection &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/add-members-to-a-collection-master-data-services.md)|  
  
## <a name="related-content"></a><span data-ttu-id="db69f-131">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="db69f-131">Related Content</span></span>  
  
-   [<span data-ttu-id="db69f-132">明示的階層 (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="db69f-132">Explicit Hierarchies &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/explicit-hierarchies-master-data-services.md)  
  
-   [<span data-ttu-id="db69f-133">データのエクスポート &#40;マスターデータサービス&#41;</span><span class="sxs-lookup"><span data-stu-id="db69f-133">Exporting Data &#40;Master Data Services&#41;</span></span>](overview-exporting-data-master-data-services.md)  
  
  
