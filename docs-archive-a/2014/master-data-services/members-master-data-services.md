---
title: メンバー (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- leaf members [Master Data Services]
- consolidated members [Master Data Services]
- consolidated members [Master Data Services], about consolidated members
- members [Master Data Services], about members
- leaf members [Master Data Services], about leaf members
- members [Master Data Services]
ms.assetid: 0fda32b9-677d-4ba2-bb28-f76f2383a30f
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 89d2edb21b58575dffc21d9a6470171251889cc0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714497"
---
# <a name="members-master-data-services"></a><span data-ttu-id="3bb72-102">メンバー (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="3bb72-102">Members (Master Data Services)</span></span>
  <span data-ttu-id="3bb72-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]では、メンバーは物理マスター データです。</span><span class="sxs-lookup"><span data-stu-id="3bb72-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], members are the physical master data.</span></span> <span data-ttu-id="3bb72-104">たとえば、Product エンティティの Road-150 バイクや、Customer エンティティの特定の顧客をメンバーにすることができます。</span><span class="sxs-lookup"><span data-stu-id="3bb72-104">For example, a member can be a Road-150 bike in a Product entity or a specific customer in a Customer entity.</span></span>

## <a name="how-members-relate-to-other-model-objects"></a><span data-ttu-id="3bb72-105">メンバーと他のモデル オブジェクトの関連付け</span><span class="sxs-lookup"><span data-stu-id="3bb72-105">How Members Relate to Other Model Objects</span></span>
 <span data-ttu-id="3bb72-106">メンバーは、テーブルの行と考えることができます。</span><span class="sxs-lookup"><span data-stu-id="3bb72-106">You can think of members as rows in a table.</span></span> <span data-ttu-id="3bb72-107">関連するメンバーはエンティティに含まれ、各メンバーは属性値によって定義されます。</span><span class="sxs-lookup"><span data-stu-id="3bb72-107">Related members are contained in an entity, and each member is defined by attribute values.</span></span>

 <span data-ttu-id="3bb72-108">この例では、テーブルはエンティティを、テーブルの行はメンバーを、テーブルの列は属性を、それぞれ表しています。</span><span class="sxs-lookup"><span data-stu-id="3bb72-108">In this example, the table represents an entity, the rows in the table represent members, and the columns in the table represent attributes.</span></span> <span data-ttu-id="3bb72-109">各セルは特定のメンバーの属性値を表します。</span><span class="sxs-lookup"><span data-stu-id="3bb72-109">Each cell represents an attribute value for a specific member.</span></span>

 <span data-ttu-id="3bb72-110">![テーブルとして表されたマスター データ サービス エンティティ](../../2014/master-data-services/media/mds-conc-entity-table.gif "テーブルとして表されたマスター データ サービス エンティティ")</span><span class="sxs-lookup"><span data-stu-id="3bb72-110">![Master Data Services Entity Represented as Table](../../2014/master-data-services/media/mds-conc-entity-table.gif "Master Data Services Entity Represented as Table")</span></span>

## <a name="member-types"></a><span data-ttu-id="3bb72-111">メンバーの種類</span><span class="sxs-lookup"><span data-stu-id="3bb72-111">Member Types</span></span>
 <span data-ttu-id="3bb72-112">メンバーには、リーフ メンバー、統合メンバー、およびコレクション メンバーという 2 種類があります。</span><span class="sxs-lookup"><span data-stu-id="3bb72-112">There are three types of members: leaf members, consolidated members, and collection members.</span></span>

 <span data-ttu-id="3bb72-113">リーフ メンバーは、エンティティの既定のメンバーです。</span><span class="sxs-lookup"><span data-stu-id="3bb72-113">Leaf members are the default members in an entity.</span></span>

-   <span data-ttu-id="3bb72-114">派生階層では、リーフ メンバーは唯一の種類のメンバーです。</span><span class="sxs-lookup"><span data-stu-id="3bb72-114">In derived hierarchies, leaf members are the only type of member.</span></span> <span data-ttu-id="3bb72-115">1 つのエンティティのリーフ メンバーは、別のエンティティのリーフ メンバーの親として使用されます。</span><span class="sxs-lookup"><span data-stu-id="3bb72-115">Leaf members from one entity are used as parents of leaf members from another entity.</span></span>

-   <span data-ttu-id="3bb72-116">明示的階層では、リーフ メンバーは最下位レベルで、子を持つことができません。</span><span class="sxs-lookup"><span data-stu-id="3bb72-116">In explicit hierarchies, leaf members are the lowest level and cannot have children.</span></span>

 <span data-ttu-id="3bb72-117">統合メンバーは、エンティティの明示的階層およびコレクションが有効になっているときにのみ存在します。</span><span class="sxs-lookup"><span data-stu-id="3bb72-117">Consolidated members exist only when explicit hierarchies and collections are enabled for the entity.</span></span>

-   <span data-ttu-id="3bb72-118">派生階層には、統合メンバーは含まれません。</span><span class="sxs-lookup"><span data-stu-id="3bb72-118">Derived hierarchies do not contain consolidated members.</span></span>

-   <span data-ttu-id="3bb72-119">明示的階層では、統合メンバーは階層内の他のメンバーの親になることも、子になることもできます。</span><span class="sxs-lookup"><span data-stu-id="3bb72-119">In explicit hierarchies, consolidated members can be parents of other members within the hierarchy, or they can be children.</span></span>

## <a name="use-hierarchies-and-collections-to-organize-members"></a><span data-ttu-id="3bb72-120">階層とコレクションを使用したメンバーの整理</span><span class="sxs-lookup"><span data-stu-id="3bb72-120">Use Hierarchies and Collections to Organize Members</span></span>
 <span data-ttu-id="3bb72-121">階層およびコレクションを使用して、レポートまたは分析のためにメンバーをグループ化できます。</span><span class="sxs-lookup"><span data-stu-id="3bb72-121">Hierarchies and collections can be used to group members for reporting or analysis.</span></span> <span data-ttu-id="3bb72-122">詳細については、「 [階層 (マスター データ サービス)](hierarchies-master-data-services.md) 」および「 [コレクション (マスター データ サービス)](../../2014/master-data-services/collections-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3bb72-122">For more information, see [Hierarchies &#40;Master Data Services&#41;](hierarchies-master-data-services.md) and [Collections &#40;Master Data Services&#41;](../../2014/master-data-services/collections-master-data-services.md).</span></span>

## <a name="member-example"></a><span data-ttu-id="3bb72-123">メンバーの例</span><span class="sxs-lookup"><span data-stu-id="3bb72-123">Member Example</span></span>
 <span data-ttu-id="3bb72-124">次の例では、各メンバーは、Name、Code、Subcategory、StandardCost、ListPrice、および FilePhoto という属性値で構成されています。</span><span class="sxs-lookup"><span data-stu-id="3bb72-124">In the following example, each member is made up of a Name, Code, Subcategory, StandardCost, ListPrice, and FilePhoto attribute value.</span></span>

 <span data-ttu-id="3bb72-125">![自転車製品エンティティ テーブル](../../2014/master-data-services/media/mds-conc-entity-table-w-data.gif "自転車製品エンティティ テーブル")</span><span class="sxs-lookup"><span data-stu-id="3bb72-125">![Bike Product Entity Table](../../2014/master-data-services/media/mds-conc-entity-table-w-data.gif "Bike Product Entity Table")</span></span>

## <a name="related-tasks"></a><span data-ttu-id="3bb72-126">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="3bb72-126">Related Tasks</span></span>

|<span data-ttu-id="3bb72-127">タスクの説明</span><span class="sxs-lookup"><span data-stu-id="3bb72-127">Task Description</span></span>|<span data-ttu-id="3bb72-128">トピック</span><span class="sxs-lookup"><span data-stu-id="3bb72-128">Topic</span></span>|
|----------------------|-----------|
|<span data-ttu-id="3bb72-129">新しいリーフ メンバーを作成する。</span><span class="sxs-lookup"><span data-stu-id="3bb72-129">Create a new leaf member.</span></span>|[<span data-ttu-id="3bb72-130">リーフ メンバーを作成する &#40;マスター データ サービス&#41;</span><span class="sxs-lookup"><span data-stu-id="3bb72-130">Create a Leaf Member &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-leaf-member-master-data-services.md)|
|<span data-ttu-id="3bb72-131">新しい統合メンバーを作成する。</span><span class="sxs-lookup"><span data-stu-id="3bb72-131">Create a new consolidated member.</span></span>|[<span data-ttu-id="3bb72-132">統合メンバーを作成する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="3bb72-132">Create a Consolidated Member &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-consolidated-member-master-data-services.md)|
|<span data-ttu-id="3bb72-133">既存のメンバーまたはコレクションを削除する。</span><span class="sxs-lookup"><span data-stu-id="3bb72-133">Delete an existing member or collection.</span></span>|[<span data-ttu-id="3bb72-134">メンバーまたはコレクションを削除する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="3bb72-134">Delete a Member or Collection &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/delete-a-member-or-collection-master-data-services.md)|
|<span data-ttu-id="3bb72-135">削除したメンバーまたはコレクションを再アクティブ化する。</span><span class="sxs-lookup"><span data-stu-id="3bb72-135">Reactivate a deleted member or collection.</span></span>|[<span data-ttu-id="3bb72-136">メンバーまたはコレクションを再アクティブ化する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="3bb72-136">Reactivate a Member or Collection &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/reactivate-a-member-or-collection-master-data-services.md)|
|<span data-ttu-id="3bb72-137">メンバーの属性値を更新する。</span><span class="sxs-lookup"><span data-stu-id="3bb72-137">Update the attribute values of a member.</span></span>|[<span data-ttu-id="3bb72-138">属性の型の変更 (Excel 用 MDS アドイン)</span><span class="sxs-lookup"><span data-stu-id="3bb72-138">Change the Attribute Type &#40;MDS Add-in for Excel&#41;</span></span>](microsoft-excel-add-in/change-the-attribute-type-mds-add-in-for-excel.md)|
|<span data-ttu-id="3bb72-139">階層内のメンバーを移動する。</span><span class="sxs-lookup"><span data-stu-id="3bb72-139">Move members within a hierarchy.</span></span>|[<span data-ttu-id="3bb72-140">階層内のメンバーを移動する &#40;マスターデータサービス&#41;</span><span class="sxs-lookup"><span data-stu-id="3bb72-140">Move Members within a Hierarchy &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/move-members-within-a-hierarchy-master-data-services.md)|

## <a name="related-content"></a><span data-ttu-id="3bb72-141">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="3bb72-141">Related Content</span></span>

-   [<span data-ttu-id="3bb72-142">マスター データ サービス概要</span><span class="sxs-lookup"><span data-stu-id="3bb72-142">Master Data Services Overview</span></span>](master-data-services-overview-mds.md)

-   [<span data-ttu-id="3bb72-143">エンティティ (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="3bb72-143">Entities &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/entities-master-data-services.md)

-   [<span data-ttu-id="3bb72-144">属性 (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="3bb72-144">Attributes &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/attributes-master-data-services.md)

-   [<span data-ttu-id="3bb72-145">階層 (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="3bb72-145">Hierarchies &#40;Master Data Services&#41;</span></span>](hierarchies-master-data-services.md)

-   [<span data-ttu-id="3bb72-146">コレクション (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="3bb72-146">Collections &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/collections-master-data-services.md)

-   [<span data-ttu-id="3bb72-147">リーフ権限 (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="3bb72-147">Leaf Permissions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/leaf-permissions-master-data-services.md)

-   [<span data-ttu-id="3bb72-148">統合アクセス許可 &#40;マスターデータサービス&#41;</span><span class="sxs-lookup"><span data-stu-id="3bb72-148">Consolidated Permissions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/consolidated-permissions-master-data-services.md)

-   [<span data-ttu-id="3bb72-149">フィルター演算子 (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="3bb72-149">Filter Operators &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/filter-operators-master-data-services.md)


