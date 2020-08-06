---
title: モデル オブジェクト アクセス許可 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- permissions [Master Data Services], model objects
- models [Master Data Services], object permissions
ms.assetid: fab6335b-4cae-47de-ae7c-6c4743e0680f
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 4cc64d753b680cfabc3707a29c6d9de631708c20
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644506"
---
# <a name="model-object-permissions-master-data-services"></a><span data-ttu-id="cd47d-102">モデル オブジェクト権限 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="cd47d-102">Model Object Permissions (Master Data Services)</span></span>
  <span data-ttu-id="cd47d-103">モデル オブジェクト権限は必須です。</span><span class="sxs-lookup"><span data-stu-id="cd47d-103">Model object permissions are mandatory.</span></span> <span data-ttu-id="cd47d-104">これにより、UI の **[エクスプローラー]** 機能領域でユーザーがアクセスできる属性が決まります。</span><span class="sxs-lookup"><span data-stu-id="cd47d-104">They determine the attributes a user can access in the **Explorer** functional area of the UI.</span></span>  
  
 <span data-ttu-id="cd47d-105">たとえば、ユーザーに Product エンティティに対する **更新** 権限を割り当てると、ユーザーは Product エンティティのすべての属性を更新できます。</span><span class="sxs-lookup"><span data-stu-id="cd47d-105">For example, if you assign a user **Update** permission to the Product entity, the user can update all of the attributes of the Product entity.</span></span> <span data-ttu-id="cd47d-106">単一の属性に対する **更新** 権限を割り当てた場合は、ユーザーはその属性のみを更新できます。</span><span class="sxs-lookup"><span data-stu-id="cd47d-106">If you assign **Update** permission to a single attribute, the user can update that attribute only.</span></span>  
  
 <span data-ttu-id="cd47d-107">個別の各属性値に割り当てられるセキュリティを決定するため、モデル オブジェクト権限は階層メンバー権限と組み合わされて、ユーザーがアクセスできるメンバーが決定されます。</span><span class="sxs-lookup"><span data-stu-id="cd47d-107">To determine security assigned on each individual attribute value, model object permissions are combined with hierarchy member permissions, which determine the members a user can access.</span></span>  
  
 <span data-ttu-id="cd47d-108">[**エクスプローラー**] 以外の機能領域へのアクセスをユーザーに付与するには、ユーザーがモデル管理者である必要があります。これには、モデルオブジェクト権限の割り当ても含まれます。</span><span class="sxs-lookup"><span data-stu-id="cd47d-108">To give a user access to a functional area other than **Explorer**, the user must be a model administrator, which also involves assigning model object permissions.</span></span> <span data-ttu-id="cd47d-109">詳細については、「[管理者 &#40;マスターデータサービス&#41;](administrators-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cd47d-109">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
 <span data-ttu-id="cd47d-110">モデルオブジェクト権限は、 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] ユーザーインターフェイス (UI) の [**ユーザー/グループの権限**] 機能領域の [**モデル**] タブで割り当てられます。このタブでは、モデルがツリー構造として表されます。</span><span class="sxs-lookup"><span data-stu-id="cd47d-110">Model object permissions are assigned in the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] user interface (UI), in the **User and Group Permissions** functional area on the **Models** tab. On this tab, the model is represented as a tree structure.</span></span> <span data-ttu-id="cd47d-111">ツリー内のオブジェクトに権限を割り当てると、下位にあるすべてのオブジェクトがその権限を継承します。</span><span class="sxs-lookup"><span data-stu-id="cd47d-111">When you assign permission to an object in the tree, all objects below inherit that permission.</span></span> <span data-ttu-id="cd47d-112">継承をオーバーライドするには、個々のオブジェクトに権限を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="cd47d-112">You can override that inheritance by assigning permission to individual objects.</span></span>  
  
 <span data-ttu-id="cd47d-113">モデルオブジェクトには、**読み取り専用**、**更新**、または**拒否**の権限を割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="cd47d-113">You can assign **Read-only**, **Update**, or **Deny** permission to model objects.</span></span> <span data-ttu-id="cd47d-114">**[モデル]** タブで権限を割り当てない場合、ユーザーは [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]でモデルおよびデータを表示できません。</span><span class="sxs-lookup"><span data-stu-id="cd47d-114">If you do not assign any permissions on the **Models** tab, the user cannot view any models or data in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].</span></span>  
  
## <a name="best-practice"></a><span data-ttu-id="cd47d-115">推奨事項</span><span class="sxs-lookup"><span data-stu-id="cd47d-115">Best Practice</span></span>  
 <span data-ttu-id="cd47d-116">通常は、モデルオブジェクトに**更新**権限を割り当て、その下のオブジェクトに権限を明示的に割り当てる必要があります。</span><span class="sxs-lookup"><span data-stu-id="cd47d-116">In general, you should assign **Update** permission to the model object, and then explicitly assign permission to objects underneath.</span></span> <span data-ttu-id="cd47d-117">下にあるオブジェクトに権限を割り当てないと、権限が継承されて、ユーザーは管理者になります。</span><span class="sxs-lookup"><span data-stu-id="cd47d-117">If you do not assign permission to objects underneath, the permissions are inherited and the user is an administrator.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd47d-118">参照</span><span class="sxs-lookup"><span data-stu-id="cd47d-118">See Also</span></span>  
 <span data-ttu-id="cd47d-119">[モデルオブジェクト権限の割り当て &#40;マスターデータサービス&#41;](../../2014/master-data-services/assign-model-object-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="cd47d-119">[Assign Model Object Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/assign-model-object-permissions-master-data-services.md) </span></span>  
 <span data-ttu-id="cd47d-120">[モデル権限 &#40;マスターデータサービス&#41;](../../2014/master-data-services/model-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="cd47d-120">[Model Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/model-permissions-master-data-services.md) </span></span>  
 <span data-ttu-id="cd47d-121">[機能領域のアクセス許可 &#40;マスターデータサービス&#41;](../../2014/master-data-services/functional-area-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="cd47d-121">[Functional Area Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/functional-area-permissions-master-data-services.md) </span></span>  
 <span data-ttu-id="cd47d-122">[階層メンバーの権限 &#40;マスターデータサービス&#41;](../../2014/master-data-services/hierarchy-member-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="cd47d-122">[Hierarchy Member Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/hierarchy-member-permissions-master-data-services.md) </span></span>  
 [<span data-ttu-id="cd47d-123">権限の決定方法 (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="cd47d-123">How Permissions Are Determined &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/how-permissions-are-determined-master-data-services.md)  
  
  
