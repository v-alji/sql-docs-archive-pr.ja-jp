---
title: リーフ アクセス許可 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- attribute groups [Master Data Services], permissions
- members [Master Data Services], leaf member permissions
- permissions [Master Data Services], leaf members
- leaf members [Master Data Services], attribute permissions
- attributes [Master Data Services], leaf member attribute permissions
ms.assetid: bde16e8c-bcd4-4041-8130-55c5450e5f72
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 794e1d138b91e896b8df16765ae8984c6e60aca7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738461"
---
# <a name="leaf-permissions-master-data-services"></a><span data-ttu-id="d5e0b-102">リーフ権限 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="d5e0b-102">Leaf Permissions (Master Data Services)</span></span>
  <span data-ttu-id="d5e0b-103">リーフ権限は、エンティティのすべてのリーフ メンバーの属性値に適用されます。</span><span class="sxs-lookup"><span data-stu-id="d5e0b-103">Leaf permissions apply to the attribute values for all leaf members of an entity.</span></span>  
  
 <span data-ttu-id="d5e0b-104">明示的階層が有効になっていないエンティティの場合、 **リーフ** への権限の割り当ては、エンティティへの権限の割り当てと同じです。</span><span class="sxs-lookup"><span data-stu-id="d5e0b-104">For entities without explicit hierarchies enabled, assigning permission to **Leaf** is the same as assigning permission to the entity.</span></span>  
  
 <span data-ttu-id="d5e0b-105">**注:**</span><span class="sxs-lookup"><span data-stu-id="d5e0b-105">**Notes:**</span></span>  
  
-   <span data-ttu-id="d5e0b-106">リーフ権限は、ユーザー インターフェイスの **[エクスプローラー]** 機能領域にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="d5e0b-106">Leaf permissions apply to the **Explorer** functional area of the user interface only.</span></span>  
  
-   <span data-ttu-id="d5e0b-107">**Name** 属性および **Code** 属性に割り当てられる権限は適用されません。</span><span class="sxs-lookup"><span data-stu-id="d5e0b-107">Permissions assigned to **Name** and **Code** attributes are not enforced.</span></span>  
  
|<span data-ttu-id="d5e0b-108">権限</span><span class="sxs-lookup"><span data-stu-id="d5e0b-108">Permission</span></span>|<span data-ttu-id="d5e0b-109">説明</span><span class="sxs-lookup"><span data-stu-id="d5e0b-109">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="d5e0b-110">**読み取り専用です。**</span><span class="sxs-lookup"><span data-stu-id="d5e0b-110">**Read-only**</span></span>|<span data-ttu-id="d5e0b-111">リーフ メンバーが表示されますが、ユーザーはそれらのメンバーを追加、削除、または変更できません。</span><span class="sxs-lookup"><span data-stu-id="d5e0b-111">Leaf members are displayed but the user cannot add, remove, or change them.</span></span><br /><br /> <span data-ttu-id="d5e0b-112">統合メンバーが存在する場合は、名前とコードが表示されますが、ユーザーはそれらを追加、削除、または変更できません。</span><span class="sxs-lookup"><span data-stu-id="d5e0b-112">If consolidated members exist, the names and codes are displayed but the user cannot add, remove, or change them.</span></span>|  
|<span data-ttu-id="d5e0b-113">**アップデート**</span><span class="sxs-lookup"><span data-stu-id="d5e0b-113">**Update**</span></span>|<span data-ttu-id="d5e0b-114">リーフ メンバーが表示され、ユーザーはそれらのメンバーを追加、削除、および変更できます。</span><span class="sxs-lookup"><span data-stu-id="d5e0b-114">Leaf members are displayed and the user can add, remove, and change them.</span></span><br /><br /> <span data-ttu-id="d5e0b-115">統合メンバーが存在する場合は、名前とコードが表示されますが、ユーザーはそれらを追加、削除、または変更できません。</span><span class="sxs-lookup"><span data-stu-id="d5e0b-115">If consolidated members exist, the names and codes are displayed but the user cannot add, remove, or change them.</span></span>|  
|<span data-ttu-id="d5e0b-116">**Deny**</span><span class="sxs-lookup"><span data-stu-id="d5e0b-116">**Deny**</span></span>|<span data-ttu-id="d5e0b-117">エンティティのリーフ メンバーが表示されません。</span><span class="sxs-lookup"><span data-stu-id="d5e0b-117">Leaf members for the entity are not displayed.</span></span>|  
  
## <a name="attribute-permissions"></a><span data-ttu-id="d5e0b-118">属性の権限</span><span class="sxs-lookup"><span data-stu-id="d5e0b-118">Attribute Permissions</span></span>  
 <span data-ttu-id="d5e0b-119">属性の権限は、特定のエンティティの属性の値に適用されます。</span><span class="sxs-lookup"><span data-stu-id="d5e0b-119">Attribute permissions apply to the attribute's values for the specific entity.</span></span> <span data-ttu-id="d5e0b-120">属性の権限のみを持つユーザーは、メンバーを追加または削除できません。</span><span class="sxs-lookup"><span data-stu-id="d5e0b-120">Users with attribute permissions only cannot add or remove members.</span></span>  
  
|<span data-ttu-id="d5e0b-121">権限</span><span class="sxs-lookup"><span data-stu-id="d5e0b-121">Permission</span></span>|<span data-ttu-id="d5e0b-122">説明</span><span class="sxs-lookup"><span data-stu-id="d5e0b-122">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="d5e0b-123">**読み取り専用です。**</span><span class="sxs-lookup"><span data-stu-id="d5e0b-123">**Read-only**</span></span>|<span data-ttu-id="d5e0b-124">属性が表示されますが、ユーザーは属性の値を変更できません。</span><span class="sxs-lookup"><span data-stu-id="d5e0b-124">The attribute is displayed but the user cannot change attribute values.</span></span>|  
|<span data-ttu-id="d5e0b-125">**アップデート**</span><span class="sxs-lookup"><span data-stu-id="d5e0b-125">**Update**</span></span>|<span data-ttu-id="d5e0b-126">属性が表示され、ユーザーは属性の値を変更できます。</span><span class="sxs-lookup"><span data-stu-id="d5e0b-126">The attribute is displayed and the user can change attribute values.</span></span>|  
|<span data-ttu-id="d5e0b-127">**Deny**</span><span class="sxs-lookup"><span data-stu-id="d5e0b-127">**Deny**</span></span>|<span data-ttu-id="d5e0b-128">属性が表示されません。</span><span class="sxs-lookup"><span data-stu-id="d5e0b-128">The attribute is not displayed.</span></span><br /><br /> <span data-ttu-id="d5e0b-129">注: Name 属性と Code 属性へのアクセスを明示的に拒否することはできません。</span><span class="sxs-lookup"><span data-stu-id="d5e0b-129">Note: You cannot explicitly deny access to Name and Code attributes.</span></span>|  
  
### <a name="example"></a><span data-ttu-id="d5e0b-130">例</span><span class="sxs-lookup"><span data-stu-id="d5e0b-130">Example</span></span>  
 <span data-ttu-id="d5e0b-131">Product エンティティの場合、Subcategory 属性に **更新** 権限を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="d5e0b-131">For the Product entity, assign **Update** permission to Subcategory attribute.</span></span> <span data-ttu-id="d5e0b-132">他のすべての属性に対しては権限を拒否します。</span><span class="sxs-lookup"><span data-stu-id="d5e0b-132">Deny permission to all other attributes.</span></span>  
  
|<span data-ttu-id="d5e0b-133">名前</span><span class="sxs-lookup"><span data-stu-id="d5e0b-133">Name</span></span>|<span data-ttu-id="d5e0b-134">コード</span><span class="sxs-lookup"><span data-stu-id="d5e0b-134">Code</span></span>|<span data-ttu-id="d5e0b-135">Subcategory (更新)</span><span class="sxs-lookup"><span data-stu-id="d5e0b-135">Subcategory (Update)</span></span>|  
|----------|----------|----------------------------|  
|<span data-ttu-id="d5e0b-136">Mountain-100</span><span class="sxs-lookup"><span data-stu-id="d5e0b-136">Mountain-100</span></span>|<span data-ttu-id="d5e0b-137">BK-M101</span><span class="sxs-lookup"><span data-stu-id="d5e0b-137">BK-M101</span></span>|<span data-ttu-id="d5e0b-138">{5}マウンテンバイク</span><span class="sxs-lookup"><span data-stu-id="d5e0b-138">{5} Mountain Bikes</span></span>|  
|<span data-ttu-id="d5e0b-139">Mountain-100</span><span class="sxs-lookup"><span data-stu-id="d5e0b-139">Mountain-100</span></span>|<span data-ttu-id="d5e0b-140">BK-M201</span><span class="sxs-lookup"><span data-stu-id="d5e0b-140">BK-M201</span></span>|<span data-ttu-id="d5e0b-141">{5}マウンテンバイク</span><span class="sxs-lookup"><span data-stu-id="d5e0b-141">{5} Mountain Bikes</span></span>|  
  
 <span data-ttu-id="d5e0b-142">**[エクスプローラー]** では、Subcategory 列の属性値を更新できます。</span><span class="sxs-lookup"><span data-stu-id="d5e0b-142">In **Explorer**, you can update any attribute value in the Subcategory column.</span></span> <span data-ttu-id="d5e0b-143">属性に対する権限がない場合、その属性は表示されません。</span><span class="sxs-lookup"><span data-stu-id="d5e0b-143">If you do not have permission to an attribute, the attribute is not displayed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d5e0b-144">この例では、Subcategory は、SubcategoryList エンティティに基づくドメイン ベースの属性です。</span><span class="sxs-lookup"><span data-stu-id="d5e0b-144">In this example, Subcategory is a domain-based attribute, based on the SubcategoryList entity.</span></span> <span data-ttu-id="d5e0b-145">Mountain-100 に対して別のサブカテゴリを選択することはできますが、SubcategoryList エンティティへのメンバーの追加または SubcategoryList エンティティからのメンバーの削除を行うことはできません。</span><span class="sxs-lookup"><span data-stu-id="d5e0b-145">You can select a different subcategory for Mountain-100 but you cannot add members to or delete members from the SubcategoryList entity.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5e0b-146">参照</span><span class="sxs-lookup"><span data-stu-id="d5e0b-146">See Also</span></span>  
 <span data-ttu-id="d5e0b-147">[モデルオブジェクト権限の割り当て &#40;マスターデータサービス&#41;](assign-model-object-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="d5e0b-147">[Assign Model Object Permissions &#40;Master Data Services&#41;](assign-model-object-permissions-master-data-services.md) </span></span>  
 <span data-ttu-id="d5e0b-148">[統合アクセス許可 &#40;マスターデータサービス&#41;](../../2014/master-data-services/consolidated-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="d5e0b-148">[Consolidated Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/consolidated-permissions-master-data-services.md) </span></span>  
 <span data-ttu-id="d5e0b-149">[モデルオブジェクト権限 &#40;マスターデータサービス&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="d5e0b-149">[Model Object Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md) </span></span>  
 <span data-ttu-id="d5e0b-150">[メンバー &#40;マスターデータサービス&#41;](../../2014/master-data-services/members-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="d5e0b-150">[Members &#40;Master Data Services&#41;](../../2014/master-data-services/members-master-data-services.md) </span></span>  
 [<span data-ttu-id="d5e0b-151">属性 (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="d5e0b-151">Attributes &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/attributes-master-data-services.md)  
  
  
