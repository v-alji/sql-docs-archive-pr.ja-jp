---
title: モデル アクセス許可 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- models [Master Data Services], permissions
- permissions [Master Data Services], models
ms.assetid: 210f440b-2cc1-4c49-94b1-3a97e2af7bc3
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 2846918b515bba16d12d48cd7058cf25863bf569
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641041"
---
# <a name="model-permissions-master-data-services"></a><span data-ttu-id="6a947-102">モデル権限 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="6a947-102">Model Permissions (Master Data Services)</span></span>
  <span data-ttu-id="6a947-103">モデル権限は、モデル内に存在するすべてのエンティティ、派生階層、明示的階層、およびコレクションに適用されます。</span><span class="sxs-lookup"><span data-stu-id="6a947-103">Model permissions apply to all entities, derived hierarchies, explicit hierarchies, and collections that exist within the model.</span></span> <span data-ttu-id="6a947-104">モデルに割り当てられる権限は、個々のオブジェクトでオーバーライドすることができます。</span><span class="sxs-lookup"><span data-stu-id="6a947-104">Permissions assigned to the model can be overridden for any individual object.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6a947-105">ユーザーがモデル管理者の場合、そのモデルはユーザー インターフェイスのすべての機能領域に表示されます。</span><span class="sxs-lookup"><span data-stu-id="6a947-105">If a user is a model administrator, the model is displayed in all functional areas of the user interface.</span></span> <span data-ttu-id="6a947-106">それ以外の場合、モデルは **[エクスプローラー]** 機能領域にのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="6a947-106">Otherwise, the model is displayed in the **Explorer** functional area only.</span></span> <span data-ttu-id="6a947-107">詳細については、「[管理者 &#40;マスターデータサービス&#41;](administrators-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6a947-107">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
|<span data-ttu-id="6a947-108">権限</span><span class="sxs-lookup"><span data-stu-id="6a947-108">Permission</span></span>|<span data-ttu-id="6a947-109">説明</span><span class="sxs-lookup"><span data-stu-id="6a947-109">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="6a947-110">**読み取り専用です。**</span><span class="sxs-lookup"><span data-stu-id="6a947-110">**Read-only**</span></span>|<span data-ttu-id="6a947-111">[**エクスプローラー**] にモデルが表示されますが、ユーザーはメンバーを追加または削除できません。また、属性値、階層メンバーシップ、コレクションメンバーシップを更新することもできません。</span><span class="sxs-lookup"><span data-stu-id="6a947-111">In **Explorer**, the model is displayed but the user cannot add or remove members, and cannot update attribute values, hierarchy memberships, or collection memberships.</span></span>|  
|<span data-ttu-id="6a947-112">**アップデート**</span><span class="sxs-lookup"><span data-stu-id="6a947-112">**Update**</span></span>|<span data-ttu-id="6a947-113">[**エクスプローラー**] にモデルが表示され、ユーザーはメンバーを追加および削除したり、属性値、階層メンバーシップ、コレクションメンバーシップを更新したりできます。</span><span class="sxs-lookup"><span data-stu-id="6a947-113">In **Explorer**, the model is displayed and the user can add and remove members, can update attribute values, hierarchy memberships, and collection memberships.</span></span>|  
|<span data-ttu-id="6a947-114">**Deny**</span><span class="sxs-lookup"><span data-stu-id="6a947-114">**Deny**</span></span>|<span data-ttu-id="6a947-115">モデルが表示されません。</span><span class="sxs-lookup"><span data-stu-id="6a947-115">The model is not displayed.</span></span>|  
  
 <span data-ttu-id="6a947-116">モデルに権限を割り当てると、ユーザーはすべてのバージョンのモデルにアクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="6a947-116">When you assign permission to a model, the user gets access to all versions of the model.</span></span> <span data-ttu-id="6a947-117">個々のバージョンに権限を割り当てることはできません。</span><span class="sxs-lookup"><span data-stu-id="6a947-117">You cannot assign permission to an individual version.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a947-118">参照</span><span class="sxs-lookup"><span data-stu-id="6a947-118">See Also</span></span>  
 <span data-ttu-id="6a947-119">[モデルオブジェクト権限の割り当て &#40;マスターデータサービス&#41;](../../2014/master-data-services/assign-model-object-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="6a947-119">[Assign Model Object Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/assign-model-object-permissions-master-data-services.md) </span></span>  
 <span data-ttu-id="6a947-120">[モデルオブジェクト権限 &#40;マスターデータサービス&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="6a947-120">[Model Object Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md) </span></span>  
 <span data-ttu-id="6a947-121">[エンティティのアクセス許可 &#40;マスターデータサービス&#41;](../../2014/master-data-services/entity-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="6a947-121">[Entity Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/entity-permissions-master-data-services.md) </span></span>  
 [<span data-ttu-id="6a947-122">コレクション アクセス許可 (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="6a947-122">Collection Permissions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/collection-permissions-master-data-services.md)  
  
  
