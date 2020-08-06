---
title: アクセス許可の決定方法 (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- permissions [Master Data Services], determining permissions
ms.assetid: 1dc0b43a-d023-4e7d-b027-8b1459fd058c
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 3ea3306b772224bc8602659c7e17e8dc1634f0d5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642141"
---
# <a name="how-permissions-are-determined-master-data-services"></a><span data-ttu-id="e87be-102">権限の決定方法 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="e87be-102">How Permissions Are Determined (Master Data Services)</span></span>
  <span data-ttu-id="e87be-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]でセキュリティを構成する最も簡単な方法は、ユーザーが属しているグループにモデル オブジェクト権限を割り当てることです。</span><span class="sxs-lookup"><span data-stu-id="e87be-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], the simplest way to configure security is to assign model object permissions to a group that the user is a member of.</span></span>

 <span data-ttu-id="e87be-104">次の場合、セキュリティはより複雑になります。</span><span class="sxs-lookup"><span data-stu-id="e87be-104">Security becomes more complex when:</span></span>

-   <span data-ttu-id="e87be-105">モデル オブジェクトと階層メンバーの両方の権限が割り当てられている。</span><span class="sxs-lookup"><span data-stu-id="e87be-105">Both model object and hierarchy member permissions are assigned.</span></span>

-   <span data-ttu-id="e87be-106">ユーザーがグループに属しており、そのユーザーとグループの両方に権限が割り当てられている。</span><span class="sxs-lookup"><span data-stu-id="e87be-106">The user belongs to groups and permission is assigned to both the user and groups.</span></span>

-   <span data-ttu-id="e87be-107">ユーザーがグループに属しており、複数のグループに権限が割り当てられている。</span><span class="sxs-lookup"><span data-stu-id="e87be-107">The user belongs to groups and permission is assigned to multiple groups.</span></span>

## <a name="permissions-assigned-to-a-single-group-or-user"></a><span data-ttu-id="e87be-108">単一のグループまたはユーザーに割り当てられた権限</span><span class="sxs-lookup"><span data-stu-id="e87be-108">Permissions assigned to a single group or user</span></span>
 <span data-ttu-id="e87be-109">単一のグループまたはユーザーに権限を割り当てた場合、次のワークフローに基づいて権限が決定されます。</span><span class="sxs-lookup"><span data-stu-id="e87be-109">If you assign permissions to a single group or user, permissions are determined based on the following workflow.</span></span>

 <span data-ttu-id="e87be-110">![mds_conc_security_no_overlap](../../2014/master-data-services/media/mds-conc-security-no-overlap.gif "mds_conc_security_no_overlap")</span><span class="sxs-lookup"><span data-stu-id="e87be-110">![mds_conc_security_no_overlap](../../2014/master-data-services/media/mds-conc-security-no-overlap.gif "mds_conc_security_no_overlap")</span></span>

### <a name="step-1-effective-attribute-permissions-are-determined"></a><span data-ttu-id="e87be-111">ステップ 1: 有効な属性の権限が決定される。</span><span class="sxs-lookup"><span data-stu-id="e87be-111">Step 1: Effective attribute permissions are determined.</span></span>
 <span data-ttu-id="e87be-112">有効な属性の権限は、次のように決定されます。</span><span class="sxs-lookup"><span data-stu-id="e87be-112">The following list describes how effective attribute permissions are determined:</span></span>

-   <span data-ttu-id="e87be-113">モデル オブジェクトに割り当てられた権限によって、ユーザーがアクセスできる属性が決まる。</span><span class="sxs-lookup"><span data-stu-id="e87be-113">Permissions assigned to model objects determine which attributes a user can access.</span></span>

-   <span data-ttu-id="e87be-114">すべてのモデル オブジェクトは、モデル構造内の上位レベルにある最も近いオブジェクトの権限を自動的に継承する。</span><span class="sxs-lookup"><span data-stu-id="e87be-114">All model objects automatically inherit permission from the closest object at a higher level in the model structure.</span></span>

-   <span data-ttu-id="e87be-115">エンティティと同じレベルのオブジェクトは、暗黙的に拒否される。</span><span class="sxs-lookup"><span data-stu-id="e87be-115">Any objects at the same level as the entity are implicitly denied.</span></span>

-   <span data-ttu-id="e87be-116">上位レベルのオブジェクトには、ナビゲーション アクセスが与えられる。</span><span class="sxs-lookup"><span data-stu-id="e87be-116">Any objects at a higher level are given navigational access.</span></span> <span data-ttu-id="e87be-117">ナビゲーションアクセスの詳細については、「[ナビゲーションアクセス &#40;マスターデータサービス&#41;](navigational-access-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e87be-117">For more information about navigational access, see [Navigational Access &#40;Master Data Services&#41;](navigational-access-master-data-services.md).</span></span>

 <span data-ttu-id="e87be-118">この例では、**読み取り**専用権限がエンティティに割り当てられており、その権限がその属性に継承されます。この権限は、モデル構造の下位レベルにあります。</span><span class="sxs-lookup"><span data-stu-id="e87be-118">In this example, **Read-only** permission is assigned to an entity and that permission is inherited by its attribute, which is at a lower level in the model structure.</span></span> <span data-ttu-id="e87be-119">モデルでは、このエンティティとその属性に対するナビゲーション アクセスが提供されています。</span><span class="sxs-lookup"><span data-stu-id="e87be-119">The model provides navigational access to this entity and its attribute.</span></span> <span data-ttu-id="e87be-120">モデル内のその他のエンティティは、明示的な権限が割り当てられておらず、権限の継承もしていないため、暗黙的に拒否されます。</span><span class="sxs-lookup"><span data-stu-id="e87be-120">The other entity in the model has no explicit permission assigned and does not inherit any permissions, so it is implicitly denied.</span></span>

 <span data-ttu-id="e87be-121">![mds_conc_inheritance_model](../../2014/master-data-services/media/mds-conc-inheritance-model.gif "mds_conc_inheritance_model")</span><span class="sxs-lookup"><span data-stu-id="e87be-121">![mds_conc_inheritance_model](../../2014/master-data-services/media/mds-conc-inheritance-model.gif "mds_conc_inheritance_model")</span></span>

### <a name="step-2-if-hierarchy-member-permissions-are-assigned-effective-member-permissions-are-determined"></a><span data-ttu-id="e87be-122">ステップ 2: 階層メンバーの権限が割り当てられた場合、有効なメンバーの権限が決定される。</span><span class="sxs-lookup"><span data-stu-id="e87be-122">Step 2: If hierarchy member permissions are assigned, effective member permissions are determined.</span></span>
 <span data-ttu-id="e87be-123">有効な階層メンバーの権限は、次のように決定されます。</span><span class="sxs-lookup"><span data-stu-id="e87be-123">The following list describes how effective hierarchy member permissions are determined:</span></span>

-   <span data-ttu-id="e87be-124">階層ノードに割り当てられた権限によって、ユーザーがアクセスできるメンバーが決まる。</span><span class="sxs-lookup"><span data-stu-id="e87be-124">Permissions assigned to hierarchy nodes determine which members a user can access.</span></span>

-   <span data-ttu-id="e87be-125">階層内のすべてのノードは、階層構造内の上位レベルにある最も近いオブジェクトの権限を自動的に継承する。</span><span class="sxs-lookup"><span data-stu-id="e87be-125">All nodes in a hierarchy automatically inherit permission from the closest object at a higher level in the hierarchy structure.</span></span>

-   <span data-ttu-id="e87be-126">同じレベルのノードは、暗黙的に拒否される。</span><span class="sxs-lookup"><span data-stu-id="e87be-126">Any nodes at the same level are implicitly denied.</span></span>

-   <span data-ttu-id="e87be-127">権限が割り当てられていない上位レベルのノードは、暗黙的に拒否される。</span><span class="sxs-lookup"><span data-stu-id="e87be-127">Any nodes at higher levels that do not have permissions assigned are implicitly denied.</span></span>

 <span data-ttu-id="e87be-128">この例では、**読み取り**専用権限が階層の1つのノードに割り当てられ、その権限は階層構造の下位レベルにあるノードによって継承されます。</span><span class="sxs-lookup"><span data-stu-id="e87be-128">In this example, **Read-only** permission is assigned to one node of the hierarchy and that permission is inherited by a node at a lower level in the hierarchy structure.</span></span> <span data-ttu-id="e87be-129">ルートは、権限が割り当てられていないため、暗黙的に拒否されます。</span><span class="sxs-lookup"><span data-stu-id="e87be-129">The root has no permission assigned, so it is implicitly denied.</span></span> <span data-ttu-id="e87be-130">階層構造内のその他のノードは、明示的な権限が割り当てられておらず、権限の継承もしていないため、暗黙的に拒否されます。</span><span class="sxs-lookup"><span data-stu-id="e87be-130">The other node in the hierarchy structure has no explicit permission assigned and does not inherit any permissions, so it is implicitly denied.</span></span>

 <span data-ttu-id="e87be-131">![mds_conc_inheritance_hierarchy](../../2014/master-data-services/media/mds-conc-inheritance-hierarchy.gif "mds_conc_inheritance_hierarchy")</span><span class="sxs-lookup"><span data-stu-id="e87be-131">![mds_conc_inheritance_hierarchy](../../2014/master-data-services/media/mds-conc-inheritance-hierarchy.gif "mds_conc_inheritance_hierarchy")</span></span>

### <a name="step-3-the-intersection-of-attribute-and-member-permissions-is-determined"></a><span data-ttu-id="e87be-132">ステップ 3: 属性とメンバーの権限の共通部分が決定される。</span><span class="sxs-lookup"><span data-stu-id="e87be-132">Step 3: The intersection of attribute and member permissions is determined.</span></span>
 <span data-ttu-id="e87be-133">有効な属性の権限が有効なメンバーの権限とは異なる場合、個々の属性値ごとに権限を決定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e87be-133">If the effective attribute permissions are different than the effective member permissions, permissions must be determined for each individual attribute value.</span></span> <span data-ttu-id="e87be-134">詳細については、「 [モデル権限とメンバー権限の重複 (マスター データ サービス)](../../2014/master-data-services/overlapping-model-and-member-permissions-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e87be-134">For more information, see [Overlapping Model and Member Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/overlapping-model-and-member-permissions-master-data-services.md).</span></span>

## <a name="permissions-assigned-to-multiple-groups"></a><span data-ttu-id="e87be-135">複数のグループに割り当てられた権限</span><span class="sxs-lookup"><span data-stu-id="e87be-135">Permissions assigned to multiple groups</span></span>
 <span data-ttu-id="e87be-136">ユーザーが 1 つ以上のグループに属しており、ユーザーとグループの両方に権限が割り当てられている場合、ワークフローはより複雑になります。</span><span class="sxs-lookup"><span data-stu-id="e87be-136">If a user belongs to one or more groups and permissions are assigned to both the user and the groups, the workflow becomes more complex.</span></span>

 <span data-ttu-id="e87be-137">![mds_conc_security_group_overlap](../../2014/master-data-services/media/mds-conc-security-group-overlap.gif "mds_conc_security_group_overlap")</span><span class="sxs-lookup"><span data-stu-id="e87be-137">![mds_conc_security_group_overlap](../../2014/master-data-services/media/mds-conc-security-group-overlap.gif "mds_conc_security_group_overlap")</span></span>

 <span data-ttu-id="e87be-138">この場合に、モデル オブジェクトと階層メンバーの権限を比較するには、ユーザーとグループでの権限の重複を解決する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e87be-138">In this case, overlapping user and group permissions must be resolved before model object and hierarchy member permissions can be compared.</span></span> <span data-ttu-id="e87be-139">詳細については、「 [ユーザー権限とグループ権限の重複 (マスター データ サービス)](../../2014/master-data-services/overlapping-user-and-group-permissions-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e87be-139">For more information, see [Overlapping User and Group Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/overlapping-user-and-group-permissions-master-data-services.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e87be-140">参照</span><span class="sxs-lookup"><span data-stu-id="e87be-140">See Also</span></span>
 <span data-ttu-id="e87be-141">[ユーザーおよびグループの権限の重複&#41;マスターデータサービス &#40;](../../2014/master-data-services/overlapping-user-and-group-permissions-master-data-services.md)重複する[モデルとメンバーの権限 &#40;マスターデータサービス&#41;](../../2014/master-data-services/overlapping-model-and-member-permissions-master-data-services.md)</span><span class="sxs-lookup"><span data-stu-id="e87be-141">[Overlapping User and Group Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/overlapping-user-and-group-permissions-master-data-services.md) [Overlapping Model and Member Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/overlapping-model-and-member-permissions-master-data-services.md)</span></span>


