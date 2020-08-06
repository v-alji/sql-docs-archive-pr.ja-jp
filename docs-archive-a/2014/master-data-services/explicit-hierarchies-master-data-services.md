---
title: 明示的階層 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- explicit hierarchies, about explicit hierarchies
- hierarchies [Master Data Services], explicit hierarchies
- explicit hierarchies
ms.assetid: e6f44e37-e1f0-4c38-a816-1935a856d5a4
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: f37f341dc2c003683e696f2767a6b644047d5a0a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715514"
---
# <a name="explicit-hierarchies-master-data-services"></a><span data-ttu-id="511b8-102">明示的階層 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="511b8-102">Explicit Hierarchies (Master Data Services)</span></span>
  <span data-ttu-id="511b8-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]の明示的階層は、1 つのエンティティからのメンバーを指定した任意の方法で整理します。</span><span class="sxs-lookup"><span data-stu-id="511b8-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], an explicit hierarchy organizes members from a single entity in any way you specify.</span></span> <span data-ttu-id="511b8-104">構造は不規則にすることができます。派生階層とは異なり、明示的階層はドメイン ベースの属性のリレーションシップに基づいていません。</span><span class="sxs-lookup"><span data-stu-id="511b8-104">The structure can be ragged and unlike derived hierarchies, explicit hierarchies are not based on domain-based attribute relationships.</span></span>

## <a name="consolidated-members-group-other-members"></a><span data-ttu-id="511b8-105">他のメンバーをグループ化する統合メンバー</span><span class="sxs-lookup"><span data-stu-id="511b8-105">Consolidated Members Group Other Members</span></span>
 <span data-ttu-id="511b8-106">明示的階層では、他のメンバーをグループ化する目的で作成する統合メンバーを使用します。</span><span class="sxs-lookup"><span data-stu-id="511b8-106">An explicit hierarchy uses consolidated members that you create for the purpose of grouping other members.</span></span> <span data-ttu-id="511b8-107">これらの統合メンバーは、一度に 1 つの明示的階層にのみ属することができます。</span><span class="sxs-lookup"><span data-stu-id="511b8-107">These consolidated members can belong to only one explicit hierarchy at a time.</span></span> <span data-ttu-id="511b8-108">また、明示的階層は、関連付けられたエンティティのすべてのリーフ メンバーを含みます。</span><span class="sxs-lookup"><span data-stu-id="511b8-108">An explicit hierarchy also includes all of the leaf members from the associated entity.</span></span>

 <span data-ttu-id="511b8-109">明示的階層は不規則で、階層は異なるレベルで同時に終了できます。</span><span class="sxs-lookup"><span data-stu-id="511b8-109">An explicit hierarchy can be ragged, which means that the hierarchy can end at different levels simultaneously.</span></span> <span data-ttu-id="511b8-110">各統合メンバーの下位に統合メンバーとリーフ メンバーを無制限に含めることも、まったく含めないこともできます。</span><span class="sxs-lookup"><span data-stu-id="511b8-110">Each consolidated member can have an unlimited number of consolidated and leaf members underneath, or can have none.</span></span> <span data-ttu-id="511b8-111">リーフ メンバーは、単一の統合メンバーの下位に含めることも、複数レベルの統合メンバーの下位に含めることもできます。</span><span class="sxs-lookup"><span data-stu-id="511b8-111">The leaf members can be under a single consolidated member or under multiple levels of consolidated members.</span></span>

> [!NOTE]
>  <span data-ttu-id="511b8-112">明示的階層を作成するには、明示的階層でエンティティを有効にしておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="511b8-112">Before you can create an explicit hierarchy, the entity must be enabled for explicit hierarchies.</span></span> <span data-ttu-id="511b8-113">詳細については、「[明示的階層とコレクションのエンティティの有効化 &#40;マスターデータサービス&#41;](enable-an-entity-for-explicit-hierarchies-and-collections-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="511b8-113">For more information, see [Enable an Entity for Explicit Hierarchies and Collections &#40;Master Data Services&#41;](enable-an-entity-for-explicit-hierarchies-and-collections-master-data-services.md).</span></span>

## <a name="types-of-explicit-hierarchies"></a><span data-ttu-id="511b8-114">明示的階層の種類</span><span class="sxs-lookup"><span data-stu-id="511b8-114">Types of Explicit Hierarchies</span></span>
 <span data-ttu-id="511b8-115">明示的階層には、必須階層と任意階層の 2 種類があります。</span><span class="sxs-lookup"><span data-stu-id="511b8-115">There are two types of explicit hierarchies: mandatory and non-mandatory.</span></span>

### <a name="mandatory-explicit-hierarchy"></a><span data-ttu-id="511b8-116">必須の明示的階層</span><span class="sxs-lookup"><span data-stu-id="511b8-116">Mandatory Explicit Hierarchy</span></span>
 <span data-ttu-id="511b8-117">必須の明示的階層は、階層ツリーにすべてのリーフ メンバーを含める必要がある階層です。</span><span class="sxs-lookup"><span data-stu-id="511b8-117">A mandatory explicit hierarchy is a hierarchy in which all leaf members must be included in the hierarchy tree.</span></span> <span data-ttu-id="511b8-118">既定では、すべてのメンバーがツリーのルートに含まれます。</span><span class="sxs-lookup"><span data-stu-id="511b8-118">By default, all members are included at the root of the tree.</span></span> <span data-ttu-id="511b8-119">必要に応じて、メンバーを再配置できます。</span><span class="sxs-lookup"><span data-stu-id="511b8-119">You can rearrange the members as needed.</span></span>

### <a name="non-mandatory-explicit-hierarchy"></a><span data-ttu-id="511b8-120">任意の明示的階層</span><span class="sxs-lookup"><span data-stu-id="511b8-120">Non-Mandatory Explicit Hierarchy</span></span>
 <span data-ttu-id="511b8-121">必須でない明示的階層は、すべてのリーフ メンバーがシステムで作成された **[未使用]** ノードである階層です。</span><span class="sxs-lookup"><span data-stu-id="511b8-121">A non-mandatory explicit hierarchy is a hierarchy in which all leaf members are in a system-created **Unused** node.</span></span> <span data-ttu-id="511b8-122">必要に応じて、このノードからメンバーを移動できます。</span><span class="sxs-lookup"><span data-stu-id="511b8-122">You can move members out of this node as you need them.</span></span> <span data-ttu-id="511b8-123">残りのメンバーは、 **[未使用]** ノードに残ることになります。</span><span class="sxs-lookup"><span data-stu-id="511b8-123">The rest of the members can remain in the **Unused** node.</span></span>

 <span data-ttu-id="511b8-124">任意の明示的階層を使用する場合、階層で実行されるすべてのレポートや分析が、必須の明示的階層で実行されるレポートや分析と一致するわけではありません。</span><span class="sxs-lookup"><span data-stu-id="511b8-124">When you use non-mandatory explicit hierarchies, any reporting or analysis done on the hierarchy may not match reporting or analysis done on mandatory hierarchies.</span></span>

## <a name="rules"></a><span data-ttu-id="511b8-125">ルール</span><span class="sxs-lookup"><span data-stu-id="511b8-125">Rules</span></span>
 <span data-ttu-id="511b8-126">明示的階層 (必須階層と任意階層の両方) には、次のルールが適用されます。</span><span class="sxs-lookup"><span data-stu-id="511b8-126">The following rules apply to explicit hierarchies (both mandatory and non-mandatory).</span></span>

-   <span data-ttu-id="511b8-127">各リーフ メンバーは、1 回のみ階層に含めることができます。</span><span class="sxs-lookup"><span data-stu-id="511b8-127">Each leaf member can be included in the hierarchy only once.</span></span>

-   <span data-ttu-id="511b8-128">すべての統合メンバーを 1 つの階層内に含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="511b8-128">All consolidated members must be included in a hierarchy.</span></span>

-   <span data-ttu-id="511b8-129">統合メンバーを複数の明示的階層に含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="511b8-129">Consolidated members cannot be in more than one explicit hierarchy.</span></span>

-   <span data-ttu-id="511b8-130">階層ツリー内の統合メンバーの下位に、リーフ メンバーを含める必要はありません。</span><span class="sxs-lookup"><span data-stu-id="511b8-130">Consolidated members in the hierarchy tree do not have to contain leaf members underneath them.</span></span>

-   <span data-ttu-id="511b8-131">明示的階層を削除する場合、階層内で使用されたすべての統合メンバーが削除されます。</span><span class="sxs-lookup"><span data-stu-id="511b8-131">If you delete an explicit hierarchy, all consolidated members that were used in the hierarchy are deleted.</span></span>

-   <span data-ttu-id="511b8-132">明示的階層に含まれていた統合メンバーを削除すると、その統合メンバーにグループ化されていたリーフ メンバーはルートに移動されます。</span><span class="sxs-lookup"><span data-stu-id="511b8-132">If you delete a consolidated member that was in an explicit hierarchy, all leaf members that were grouped by that consolidated member are moved to the root.</span></span>

## <a name="explicit-hierarchies-versus-derived-hierarchies"></a><span data-ttu-id="511b8-133">明示的階層と派生階層</span><span class="sxs-lookup"><span data-stu-id="511b8-133">Explicit Hierarchies versus Derived Hierarchies</span></span>
 <span data-ttu-id="511b8-134">次の表は、明示的階層と派生階層の相違点の一部を示しています。</span><span class="sxs-lookup"><span data-stu-id="511b8-134">The following table shows some of the differences between explicit and derived hierarchies.</span></span>

|<span data-ttu-id="511b8-135">明示的階層</span><span class="sxs-lookup"><span data-stu-id="511b8-135">Explicit Hierarchies</span></span>|<span data-ttu-id="511b8-136">派生階層</span><span class="sxs-lookup"><span data-stu-id="511b8-136">Derived Hierarchies</span></span>|
|--------------------------|-------------------------|
|<span data-ttu-id="511b8-137">構造はユーザーによって定義される</span><span class="sxs-lookup"><span data-stu-id="511b8-137">Structure is defined by the user</span></span>|<span data-ttu-id="511b8-138">構造はドメイン ベースの属性間のリレーションシップから派生する</span><span class="sxs-lookup"><span data-stu-id="511b8-138">Structure is derived from the relationships between domain-based attributes</span></span>|
|<span data-ttu-id="511b8-139">単一のエンティティからのメンバーを含む</span><span class="sxs-lookup"><span data-stu-id="511b8-139">Contains members from a single entity</span></span>|<span data-ttu-id="511b8-140">複数のエンティティからのメンバーを含む</span><span class="sxs-lookup"><span data-stu-id="511b8-140">Contains members from multiple entities</span></span>|
|<span data-ttu-id="511b8-141">他のメンバーをグループ化する統合メンバーを使用する</span><span class="sxs-lookup"><span data-stu-id="511b8-141">Uses consolidated members to group other members</span></span>|<span data-ttu-id="511b8-142">1 つのエンティティのリーフ メンバーを使用して、別のエンティティのリーフ メンバーをグループ化する</span><span class="sxs-lookup"><span data-stu-id="511b8-142">Uses leaf members from one entity to group leaf members from another entity</span></span>|
|<span data-ttu-id="511b8-143">不規則になる場合がある</span><span class="sxs-lookup"><span data-stu-id="511b8-143">Can be ragged</span></span>|<span data-ttu-id="511b8-144">常に一定のレベル数を含む</span><span class="sxs-lookup"><span data-stu-id="511b8-144">Always contains a consistent number of levels</span></span>|

## <a name="explicit-hierarchy-example"></a><span data-ttu-id="511b8-145">明示的階層の例</span><span class="sxs-lookup"><span data-stu-id="511b8-145">Explicit Hierarchy Example</span></span>
 <span data-ttu-id="511b8-146">次の例では、Product エンティティは、BK-M101 {Mountain-100}、BK-M201 {Mountain-200}、BK-M301 {Mountain-300}、BK-R150 {Road-150}、BK-R450 {Road-450}、および BK-R650 {Road-650} のリーフ メンバーを含みます。</span><span class="sxs-lookup"><span data-stu-id="511b8-146">In the following example, the Product entity contains these leaf members: BK-M101 {Mountain-100}, BK-M201 {Mountain-200}, BK-M301 {Mountain-300}, BK-R150 {Road-150}, BK-R450 {Road-450}, and BK-R650 {Road-650}.</span></span>

 <span data-ttu-id="511b8-147">これらのリーフ メンバーを特定の統合ポイントで集計するには、Product エンティティに統合メンバーを作成します。</span><span class="sxs-lookup"><span data-stu-id="511b8-147">To summarize these leaf members at specific consolidation points, you can create consolidated members in the Product entity.</span></span> <span data-ttu-id="511b8-148">リーフ メンバーを集計する階層ツリー内のレベルに、統合メンバーを挿入します。</span><span class="sxs-lookup"><span data-stu-id="511b8-148">Insert the consolidated members at levels in the hierarchy tree where you want to summarize the leaf members.</span></span> <span data-ttu-id="511b8-149">統合メンバーを挿入するレベルについての制限はありませんが、各メンバー (リーフまたは統合) を使用できるのは 1 回のみです。</span><span class="sxs-lookup"><span data-stu-id="511b8-149">There is no limitation on where you insert your consolidated members; however, each member (leaf or consolidated) can be used only once.</span></span>

 <span data-ttu-id="511b8-150">![マウンテン バイク明示的階層の例](../../2014/master-data-services/media/mds-conc-explicit-hierarchy.gif "マウンテン バイク明示的階層の例")</span><span class="sxs-lookup"><span data-stu-id="511b8-150">![Mountain Bike Explicit Hierarchy Example](../../2014/master-data-services/media/mds-conc-explicit-hierarchy.gif "Mountain Bike Explicit Hierarchy Example")</span></span>

 <span data-ttu-id="511b8-151">統合メンバーを使用して任意のレベルでメンバーをグループ化したり、リーフ メンバーと統合メンバーを特定の順序で並べ替えたりすることができます。</span><span class="sxs-lookup"><span data-stu-id="511b8-151">Consolidated members can be used to group members at any level, and leaf and consolidated members are sorted in the order you determine.</span></span>

## <a name="related-tasks"></a><span data-ttu-id="511b8-152">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="511b8-152">Related Tasks</span></span>

|<span data-ttu-id="511b8-153">タスクの説明</span><span class="sxs-lookup"><span data-stu-id="511b8-153">Task Description</span></span>|<span data-ttu-id="511b8-154">トピック</span><span class="sxs-lookup"><span data-stu-id="511b8-154">Topic</span></span>|
|----------------------|-----------|
|<span data-ttu-id="511b8-155">明示的階層とコレクションに対してエンティティを有効にする。</span><span class="sxs-lookup"><span data-stu-id="511b8-155">Enable an entity for explicit hierarchies and collections.</span></span>|[<span data-ttu-id="511b8-156">明示的階層およびコレクションに対してエンティティを有効にする &#40;マスターデータサービス&#41;</span><span class="sxs-lookup"><span data-stu-id="511b8-156">Enable an Entity for Explicit Hierarchies and Collections &#40;Master Data Services&#41;</span></span>](enable-an-entity-for-explicit-hierarchies-and-collections-master-data-services.md)|
|<span data-ttu-id="511b8-157">新しく明示的階層を作成する。</span><span class="sxs-lookup"><span data-stu-id="511b8-157">Create a new explicit hierarchy.</span></span>|[<span data-ttu-id="511b8-158">明示的階層を作成する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="511b8-158">Create an Explicit Hierarchy &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-an-explicit-hierarchy-master-data-services.md)|
|<span data-ttu-id="511b8-159">既存の明示的階層の名前を変更する。</span><span class="sxs-lookup"><span data-stu-id="511b8-159">Change the name of an existing explicity hierarchy.</span></span>|[<span data-ttu-id="511b8-160">明示的階層名を変更する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="511b8-160">Change an Explicit Hierarchy Name &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/change-an-explicit-hierarchy-name-master-data-services.md)|
|<span data-ttu-id="511b8-161">既存の明示的階層を削除する。</span><span class="sxs-lookup"><span data-stu-id="511b8-161">Delete an existing explicit hierarchy.</span></span>|[<span data-ttu-id="511b8-162">明示的階層を削除する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="511b8-162">Delete an Explicit Hierarchy &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/delete-an-explicit-hierarchy-master-data-services.md)|
|||

## <a name="related-content"></a><span data-ttu-id="511b8-163">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="511b8-163">Related Content</span></span>

-   [<span data-ttu-id="511b8-164">派生階層 (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="511b8-164">Derived Hierarchies &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/derived-hierarchies-master-data-services.md)

-   [<span data-ttu-id="511b8-165">コレクション (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="511b8-165">Collections &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/collections-master-data-services.md)


