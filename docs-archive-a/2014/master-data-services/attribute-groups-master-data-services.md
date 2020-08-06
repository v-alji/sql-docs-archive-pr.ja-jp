---
title: 属性グループ (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- attribute groups [Master Data Services]
- attribute groups [Master Data Services], about attribute groups
ms.assetid: 648b3d0b-e15a-45f9-8292-3a54a072e62c
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 390b402489799639e66a44992da1e20b0d0c1bbf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641725"
---
# <a name="attribute-groups-master-data-services"></a><span data-ttu-id="c85ec-102">属性グループ (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="c85ec-102">Attribute Groups (Master Data Services)</span></span>
  <span data-ttu-id="c85ec-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]では、属性グループがエンティティ内の属性の整理に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="c85ec-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], attribute groups help organize attributes in an entity.</span></span> <span data-ttu-id="c85ec-104">エンティティ内に多数の属性がある場合、属性グループを使用すると、 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Web アプリケーションでのエンティティの表示が見やすくなります。</span><span class="sxs-lookup"><span data-stu-id="c85ec-104">When an entity has lots of attributes, attribute groups improve the way an entity is displayed in the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] web application.</span></span>  
  
## <a name="how-attribute-groups-change-the-display"></a><span data-ttu-id="c85ec-105">属性グループによる表示の変更</span><span class="sxs-lookup"><span data-stu-id="c85ec-105">How Attribute Groups Change the Display</span></span>  
 <span data-ttu-id="c85ec-106">属性グループは、 **の** [エクスプローラー] [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]機能領域のグリッドの上部にタブとして表示されます。</span><span class="sxs-lookup"><span data-stu-id="c85ec-106">Attribute groups are displayed as tabs above the grid in the **Explorer** functional area of [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].</span></span>  
  
 <span data-ttu-id="c85ec-107">1 つのエンティティに多くの属性がある場合、 **[エクスプローラー]** のグリッド内でエンティティのすべての属性を表示するには、右にスクロールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="c85ec-107">When an entity has a large number of attributes and you view that entity in a grid in **Explorer**, you must scroll to the right to view all of the attributes.</span></span> <span data-ttu-id="c85ec-108">このスクロールを回避するために、属性グループを作成できます。</span><span class="sxs-lookup"><span data-stu-id="c85ec-108">To prevent this scrolling, you can create attribute groups.</span></span>  
  
-   <span data-ttu-id="c85ec-109">属性グループには必ず、Name 属性と Code 属性が含まれます。</span><span class="sxs-lookup"><span data-stu-id="c85ec-109">Attribute groups always include the Name and Code attributes.</span></span>  
  
-   <span data-ttu-id="c85ec-110">エンティティの各属性は、1 つまたは複数の属性グループに属する場合があります。</span><span class="sxs-lookup"><span data-stu-id="c85ec-110">Each attribute for an entity can belong to one or more attribute groups.</span></span>  
  
-   <span data-ttu-id="c85ec-111">すべての属性が、 **エクスプローラー** の **[すべての属性]** タブに自動的に表示されます。</span><span class="sxs-lookup"><span data-stu-id="c85ec-111">All attributes are automatically included on the **All Attributes** tab in **Explorer**.</span></span>  
  
-   <span data-ttu-id="c85ec-112">**[すべての属性]** タブを非表示にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="c85ec-112">There is no way to hide the **All Attributes** tab.</span></span>  
  
 <span data-ttu-id="c85ec-113">属性グループは、 **の** [システム管理] [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]機能領域で管理します。</span><span class="sxs-lookup"><span data-stu-id="c85ec-113">Attribute groups are administered in the **System Administration** functional area of [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].</span></span>  
  
## <a name="show-or-hide-attribute-groups"></a><span data-ttu-id="c85ec-114">属性グループの表示と非表示</span><span class="sxs-lookup"><span data-stu-id="c85ec-114">Show or Hide Attribute Groups</span></span>  
 <span data-ttu-id="c85ec-115">属性グループを作成すると、作成者以外のすべてのユーザーに対して自動的に非表示に設定されます。</span><span class="sxs-lookup"><span data-stu-id="c85ec-115">When you create an attribute group, it is automatically hidden from all users except the one who created it.</span></span> <span data-ttu-id="c85ec-116">グループを表示する方法の詳細については、「 [属性グループのユーザーへの表示 (マスター データ サービス)](make-an-attribute-group-visible-to-users-master-data-services.md)機能領域のグリッドの上部にタブとして表示されます。</span><span class="sxs-lookup"><span data-stu-id="c85ec-116">For more information about making the group visible, see [Make an Attribute Group Visible to Users &#40;Master Data Services&#41;](make-an-attribute-group-visible-to-users-master-data-services.md).</span></span>  
  
 <span data-ttu-id="c85ec-117">グループ内の特定の属性を非表示にするために、その属性に **[拒否]** の権限を割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="c85ec-117">If you want to hide a specific attribute within a group, you can assign **Deny** permission to the attribute.</span></span> <span data-ttu-id="c85ec-118">詳細については、「[リーフ権限 (マスター データ サービス)](../../2014/master-data-services/leaf-permissions-master-data-services.md)」または「[統合権限 (マスター データ サービス)](../../2014/master-data-services/consolidated-permissions-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c85ec-118">For more information, see [Leaf Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/leaf-permissions-master-data-services.md) or [Consolidated Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/consolidated-permissions-master-data-services.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="c85ec-119">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="c85ec-119">Related Tasks</span></span>  
  
|<span data-ttu-id="c85ec-120">タスクの説明</span><span class="sxs-lookup"><span data-stu-id="c85ec-120">Task Description</span></span>|<span data-ttu-id="c85ec-121">トピック</span><span class="sxs-lookup"><span data-stu-id="c85ec-121">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="c85ec-122">新しい属性グループを作成して属性を追加する。</span><span class="sxs-lookup"><span data-stu-id="c85ec-122">Create a new attribute group and add attributes to it.</span></span>|[<span data-ttu-id="c85ec-123">属性グループを作成する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="c85ec-123">Create an Attribute Group &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-an-attribute-group-master-data-services.md)|  
|<span data-ttu-id="c85ec-124">属性グループがユーザーに表示されるようにする。</span><span class="sxs-lookup"><span data-stu-id="c85ec-124">Make an attribute group visible to users.</span></span>|[<span data-ttu-id="c85ec-125">属性グループのユーザーへの表示 (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="c85ec-125">Make an Attribute Group Visible to Users &#40;Master Data Services&#41;</span></span>](make-an-attribute-group-visible-to-users-master-data-services.md)|  
|<span data-ttu-id="c85ec-126">既存の属性グループの名前を変更する。</span><span class="sxs-lookup"><span data-stu-id="c85ec-126">Change the name of an existing attribute group.</span></span>|[<span data-ttu-id="c85ec-127">属性グループ名を変更する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="c85ec-127">Change an Attribute Group Name &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/change-an-attribute-group-name-master-data-services.md)|  
|<span data-ttu-id="c85ec-128">既存の属性グループを削除する。</span><span class="sxs-lookup"><span data-stu-id="c85ec-128">Delete an existing attribute group.</span></span>|[<span data-ttu-id="c85ec-129">属性グループを削除する &#40;マスター データ サービス&#41;</span><span class="sxs-lookup"><span data-stu-id="c85ec-129">Delete an Attribute Group &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/delete-an-attribute-group-master-data-services.md)|  
  
## <a name="related-content"></a><span data-ttu-id="c85ec-130">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="c85ec-130">Related Content</span></span>  
  
-   [<span data-ttu-id="c85ec-131">属性 (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="c85ec-131">Attributes &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/attributes-master-data-services.md)  
  
  
