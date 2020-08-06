---
title: 統合アクセス許可 (マスターデータサービス) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- attributes [Master Data Services], consolidated member attribute permissions
- consolidated members [Master Data Services], attribute permissions
- permissions [Master Data Services], consolidated members
- members [Master Data Services], consolidated member permissions
ms.assetid: 084055a3-5fd3-43f3-b620-ac6afab42a3d
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: c4c93e74acc84d6e742139263bedc011c4028efb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646201"
---
# <a name="consolidated-permissions-master-data-services"></a><span data-ttu-id="99cc2-102">統合権限 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="99cc2-102">Consolidated Permissions (Master Data Services)</span></span>
  <span data-ttu-id="99cc2-103">統合権限は、エンティティのすべての統合メンバーの属性値に適用されます。</span><span class="sxs-lookup"><span data-stu-id="99cc2-103">Consolidated permissions apply to the attribute values for all consolidated members of an entity.</span></span>  
  
 <span data-ttu-id="99cc2-104">統合権限は、明示的階層およびコレクションに対して有効なエンティティにのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="99cc2-104">Consolidated permissions apply only to entities that are enabled for explicit hierarchies and collections.</span></span>  
  
 <span data-ttu-id="99cc2-105">**注:**</span><span class="sxs-lookup"><span data-stu-id="99cc2-105">**Notes:**</span></span>  
  
-   <span data-ttu-id="99cc2-106">リーフ権限は、ユーザー インターフェイスの **[エクスプローラー]** 機能領域にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="99cc2-106">Leaf permissions apply to the **Explorer** functional area of the user interface only.</span></span>  
  
-   <span data-ttu-id="99cc2-107">**Name** 属性および **Code** 属性に割り当てられる権限は適用されません。</span><span class="sxs-lookup"><span data-stu-id="99cc2-107">Permissions assigned to **Name** and **Code** attributes are not enforced.</span></span>  
  
|<span data-ttu-id="99cc2-108">権限</span><span class="sxs-lookup"><span data-stu-id="99cc2-108">Permission</span></span>|<span data-ttu-id="99cc2-109">説明</span><span class="sxs-lookup"><span data-stu-id="99cc2-109">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="99cc2-110">**読み取り専用です。**</span><span class="sxs-lookup"><span data-stu-id="99cc2-110">**Read-only**</span></span>|<span data-ttu-id="99cc2-111">統合メンバーが表示されますが、ユーザーはそれらのメンバーを追加、削除、または変更できません。</span><span class="sxs-lookup"><span data-stu-id="99cc2-111">Consolidated members are displayed but the user cannot add, remove, or change them.</span></span>|  
|<span data-ttu-id="99cc2-112">**アップデート**</span><span class="sxs-lookup"><span data-stu-id="99cc2-112">**Update**</span></span>|<span data-ttu-id="99cc2-113">統合メンバーが表示され、ユーザーはそれらのメンバーを追加、削除、および変更できます。</span><span class="sxs-lookup"><span data-stu-id="99cc2-113">Consolidated members are displayed and the user can add, remove, and change them.</span></span>|  
|<span data-ttu-id="99cc2-114">**Deny**</span><span class="sxs-lookup"><span data-stu-id="99cc2-114">**Deny**</span></span>|<span data-ttu-id="99cc2-115">エンティティの統合メンバーが表示されません。</span><span class="sxs-lookup"><span data-stu-id="99cc2-115">Consolidated members for the entity are not displayed.</span></span>|  
  
## <a name="attribute-permissions"></a><span data-ttu-id="99cc2-116">属性の権限</span><span class="sxs-lookup"><span data-stu-id="99cc2-116">Attribute Permissions</span></span>  
 <span data-ttu-id="99cc2-117">属性の権限は、特定のエンティティの属性の値に適用されます。</span><span class="sxs-lookup"><span data-stu-id="99cc2-117">Attribute permissions apply to the attribute's values for the specific entity.</span></span> <span data-ttu-id="99cc2-118">属性権限のみを持つユーザーは、メンバーを追加または削除できません。</span><span class="sxs-lookup"><span data-stu-id="99cc2-118">Users with only attribute permissions cannot add or remove members.</span></span>  
  
|<span data-ttu-id="99cc2-119">権限</span><span class="sxs-lookup"><span data-stu-id="99cc2-119">Permission</span></span>|<span data-ttu-id="99cc2-120">説明</span><span class="sxs-lookup"><span data-stu-id="99cc2-120">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="99cc2-121">**読み取り専用です。**</span><span class="sxs-lookup"><span data-stu-id="99cc2-121">**Read-only**</span></span>|<span data-ttu-id="99cc2-122">属性が表示されますが、ユーザーは属性の値を変更できません。</span><span class="sxs-lookup"><span data-stu-id="99cc2-122">The attribute is displayed but the user cannot change attribute values.</span></span>|  
|<span data-ttu-id="99cc2-123">**アップデート**</span><span class="sxs-lookup"><span data-stu-id="99cc2-123">**Update**</span></span>|<span data-ttu-id="99cc2-124">属性が表示され、ユーザーは属性の値を変更できます。</span><span class="sxs-lookup"><span data-stu-id="99cc2-124">The attribute is displayed and the user can change attribute values.</span></span>|  
|<span data-ttu-id="99cc2-125">**Deny**</span><span class="sxs-lookup"><span data-stu-id="99cc2-125">**Deny**</span></span>|<span data-ttu-id="99cc2-126">属性が表示されません。</span><span class="sxs-lookup"><span data-stu-id="99cc2-126">The attribute is not displayed.</span></span><br /><br /> <span data-ttu-id="99cc2-127">注: Name 属性と Code 属性へのアクセスを明示的に拒否することはできません。</span><span class="sxs-lookup"><span data-stu-id="99cc2-127">Note: You cannot explicitly deny access to Name and Code attributes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="99cc2-128">参照</span><span class="sxs-lookup"><span data-stu-id="99cc2-128">See Also</span></span>  
 <span data-ttu-id="99cc2-129">[モデルオブジェクト権限の割り当て &#40;マスターデータサービス&#41;](assign-model-object-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="99cc2-129">[Assign Model Object Permissions &#40;Master Data Services&#41;](assign-model-object-permissions-master-data-services.md) </span></span>  
 <span data-ttu-id="99cc2-130">[リーフアクセス許可 &#40;マスターデータサービス&#41;](../../2014/master-data-services/leaf-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="99cc2-130">[Leaf Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/leaf-permissions-master-data-services.md) </span></span>  
 <span data-ttu-id="99cc2-131">[モデルオブジェクト権限 &#40;マスターデータサービス&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="99cc2-131">[Model Object Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md) </span></span>  
 <span data-ttu-id="99cc2-132">[メンバー &#40;マスターデータサービス&#41;](../../2014/master-data-services/members-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="99cc2-132">[Members &#40;Master Data Services&#41;](../../2014/master-data-services/members-master-data-services.md) </span></span>  
 [<span data-ttu-id="99cc2-133">属性 (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="99cc2-133">Attributes &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/attributes-master-data-services.md)  
  
  
