---
title: モデル アクセス許可とメンバー アクセス許可の重複 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- models [Master Data Services], effective permissions
- permissions [Master Data Services], model and member overlaps
- members [Master Data Services], effective permissions
ms.assetid: 9fd7a555-43bf-4796-a8b6-1ca63a291216
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: ec5f4019f25a777e4c70433bd9a7e72fca2277e2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632540"
---
# <a name="overlapping-model-and-member-permissions-master-data-services"></a><span data-ttu-id="afd5a-102">モデル権限とメンバー権限の重複 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="afd5a-102">Overlapping Model and Member Permissions (Master Data Services)</span></span>
  <span data-ttu-id="afd5a-103">メンバーに割り当てられている権限は、モデル オブジェクトに割り当てられている権限と重複している可能性があります。</span><span class="sxs-lookup"><span data-stu-id="afd5a-103">Permission assigned to a member can overlap with permission assigned to a model object.</span></span> <span data-ttu-id="afd5a-104">重複が発生すると、より制限の厳しい権限が有効になります。</span><span class="sxs-lookup"><span data-stu-id="afd5a-104">When overlaps occur, the more restrictive permission takes effect.</span></span>  
  
 <span data-ttu-id="afd5a-105">メンバーに割り当てられている権限が、対応するモデル オブジェクトの権限とは異なる場合、次のルールが適用されます。</span><span class="sxs-lookup"><span data-stu-id="afd5a-105">If a member has permission that is different than its corresponding model object, the following rules apply:</span></span>  
  
-   <span data-ttu-id="afd5a-106">**拒否** が他のどの権限をオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="afd5a-106">**Deny** overrides all other permissions.</span></span>  
  
-   <span data-ttu-id="afd5a-107">**読み取り専用は** **Update**をオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="afd5a-107">**Read-only** overrides **Update**.</span></span>  
  
 <span data-ttu-id="afd5a-108">次の図は、属性の権限がメンバーの権限とは異なる場合に、個々の属性値に対して有効な権限を示しています。</span><span class="sxs-lookup"><span data-stu-id="afd5a-108">The following image shows which permissions take effect on an individual attribute value when attribute permissions are different than member permissions.</span></span>  
  
 <span data-ttu-id="afd5a-109">![mds_conc_security_member_overlap_table](../../2014/master-data-services/media/mds-conc-security-member-overlap-table.gif "mds_conc_security_member_overlap_table")</span><span class="sxs-lookup"><span data-stu-id="afd5a-109">![mds_conc_security_member_overlap_table](../../2014/master-data-services/media/mds-conc-security-member-overlap-table.gif "mds_conc_security_member_overlap_table")</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="afd5a-110">例 1</span><span class="sxs-lookup"><span data-stu-id="afd5a-110">Example 1</span></span>  
 <span data-ttu-id="afd5a-111">![mds_conc_overlap_model_1](../../2014/master-data-services/media/mds-conc-overlap-model-1.gif "mds_conc_overlap_model_1")</span><span class="sxs-lookup"><span data-stu-id="afd5a-111">![mds_conc_overlap_model_1](../../2014/master-data-services/media/mds-conc-overlap-model-1.gif "mds_conc_overlap_model_1")</span></span>  
  
 <span data-ttu-id="afd5a-112">**[モデル]** タブで、Product エンティティに **更新** 権限が割り当てられています。</span><span class="sxs-lookup"><span data-stu-id="afd5a-112">On the **Models** tab, the Product entity has **Update** permission assigned.</span></span> <span data-ttu-id="afd5a-113">エンティティのすべての属性がこの権限を継承しています。</span><span class="sxs-lookup"><span data-stu-id="afd5a-113">All attributes in the entity inherit that permission.</span></span>  
  
 <span data-ttu-id="afd5a-114">**[階層メンバー]** タブで、派生階層の Mountain Bikes サブカテゴリ ノードに **更新** 権限が割り当てられています。</span><span class="sxs-lookup"><span data-stu-id="afd5a-114">On the **Hierarchy Members** tab, the Mountain Bikes subcategory node in a derived hierarchy has **Update** permission assigned.</span></span>  
  
 <span data-ttu-id="afd5a-115">結果: **[エクスプローラー]** で、Mountain Bikes ノード内のすべてのメンバーについて、すべての属性値に対する **更新** 権限がユーザーに与えられます。</span><span class="sxs-lookup"><span data-stu-id="afd5a-115">Result: In **Explorer**, the user has **Update** permission to all attribute values for all members in the Mountain Bikes node.</span></span> <span data-ttu-id="afd5a-116">その他のメンバーと属性は、すべて非表示になります。</span><span class="sxs-lookup"><span data-stu-id="afd5a-116">All other members and attributes are hidden.</span></span>  
  
 <span data-ttu-id="afd5a-117">![mds_conc_overlap_model_example_1](../../2014/master-data-services/media/mds-conc-overlap-model-example-1.gif "mds_conc_overlap_model_example_1")</span><span class="sxs-lookup"><span data-stu-id="afd5a-117">![mds_conc_overlap_model_example_1](../../2014/master-data-services/media/mds-conc-overlap-model-example-1.gif "mds_conc_overlap_model_example_1")</span></span>  
  
## <a name="example-2"></a><span data-ttu-id="afd5a-118">例 2</span><span class="sxs-lookup"><span data-stu-id="afd5a-118">Example 2</span></span>  
 <span data-ttu-id="afd5a-119">![mds_conc_overlap_model_2](../../2014/master-data-services/media/mds-conc-overlap-model-2.gif "mds_conc_overlap_model_2")</span><span class="sxs-lookup"><span data-stu-id="afd5a-119">![mds_conc_overlap_model_2](../../2014/master-data-services/media/mds-conc-overlap-model-2.gif "mds_conc_overlap_model_2")</span></span>  
  
 <span data-ttu-id="afd5a-120">**[モデル]** タブで、Subcategory 属性に **更新** 権限が割り当てられています。</span><span class="sxs-lookup"><span data-stu-id="afd5a-120">On the **Models** tab, the Subcategory attribute has **Update** permission assigned.</span></span>  
  
 <span data-ttu-id="afd5a-121">[**階層メンバー** ] タブで、派生階層の [マウンテン Bikes サブカテゴリ] ノードには、明示的に**読み取り**専用権限が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="afd5a-121">On the **Hierarchy Members** tab, the Mountain Bikes subcategory node in a derived hierarchy is explicitly assigned **Read-only** permission.</span></span>  
  
 <span data-ttu-id="afd5a-122">結果: [**エクスプローラー**] で、[マウンテンバイク] ノードのメンバーのサブカテゴリ属性値に対する**読み取り**専用権限がユーザーに与えられます。</span><span class="sxs-lookup"><span data-stu-id="afd5a-122">Result: In **Explorer**, the user has **Read-only** permission to the Subcategory attribute values for the members in the Mountain Bikes node.</span></span> <span data-ttu-id="afd5a-123">その他のメンバーと属性は、すべて非表示になります。</span><span class="sxs-lookup"><span data-stu-id="afd5a-123">All other members and attributes are hidden.</span></span>  
  
 <span data-ttu-id="afd5a-124">![mds_conc_overlap_model_example_2](../../2014/master-data-services/media/mds-conc-overlap-model-example-2.gif "mds_conc_overlap_model_example_2")</span><span class="sxs-lookup"><span data-stu-id="afd5a-124">![mds_conc_overlap_model_example_2](../../2014/master-data-services/media/mds-conc-overlap-model-example-2.gif "mds_conc_overlap_model_example_2")</span></span>  
  
## <a name="example-3"></a><span data-ttu-id="afd5a-125">例 3</span><span class="sxs-lookup"><span data-stu-id="afd5a-125">Example 3</span></span>  
 <span data-ttu-id="afd5a-126">![mds_conc_overlap_model_3](../../2014/master-data-services/media/mds-conc-overlap-model-3.gif "mds_conc_overlap_model_3")</span><span class="sxs-lookup"><span data-stu-id="afd5a-126">![mds_conc_overlap_model_3](../../2014/master-data-services/media/mds-conc-overlap-model-3.gif "mds_conc_overlap_model_3")</span></span>  
  
 <span data-ttu-id="afd5a-127">[**モデル**] タブでは、サブカテゴリ属性に**読み取り**専用アクセス許可が割り当てられています。</span><span class="sxs-lookup"><span data-stu-id="afd5a-127">On the **Models** tab, the Subcategory attribute has **Read-only** permission assigned.</span></span>  
  
 <span data-ttu-id="afd5a-128">**[階層メンバー]** タブで、派生階層の Mountain Bikes サブカテゴリに **更新** 権限が明示的に割り当てられています。</span><span class="sxs-lookup"><span data-stu-id="afd5a-128">On the **Hierarchy Members** tab, the Mountain Bikes subcategory in a derived hierarchy is explicitly assigned **Update** permission.</span></span>  
  
 <span data-ttu-id="afd5a-129">結果: [**エクスプローラー**] で、属性値に対する**読み取り**専用権限がユーザーに与えられます。</span><span class="sxs-lookup"><span data-stu-id="afd5a-129">Result: In **Explorer**, the user has **Read-only** permission to the attribute values.</span></span> <span data-ttu-id="afd5a-130">その他のメンバーと属性は、すべて非表示になります。</span><span class="sxs-lookup"><span data-stu-id="afd5a-130">All other members and attributes are hidden.</span></span>  
  
 <span data-ttu-id="afd5a-131">![mds_conc_overlap_model_example_2](../../2014/master-data-services/media/mds-conc-overlap-model-example-2.gif "mds_conc_overlap_model_example_2")</span><span class="sxs-lookup"><span data-stu-id="afd5a-131">![mds_conc_overlap_model_example_2](../../2014/master-data-services/media/mds-conc-overlap-model-example-2.gif "mds_conc_overlap_model_example_2")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afd5a-132">参照</span><span class="sxs-lookup"><span data-stu-id="afd5a-132">See Also</span></span>  
 <span data-ttu-id="afd5a-133">[アクセス許可の決定方法 &#40;マスターデータサービス&#41;](how-permissions-are-determined-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="afd5a-133">[How Permissions Are Determined &#40;Master Data Services&#41;](how-permissions-are-determined-master-data-services.md) </span></span>  
 [<span data-ttu-id="afd5a-134">ユーザー権限とグループ権限の重複 (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="afd5a-134">Overlapping User and Group Permissions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/overlapping-user-and-group-permissions-master-data-services.md)  
  
  
