---
title: 機能領域アクセス許可 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- functional area permissions [Master Data Services], about functional area permissions
- functional area permissions [Master Data Services]
- permissions [Master Data Services], functional areas
ms.assetid: a80b87b3-b904-4cda-8582-0761c2617c57
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 3f1f2639f83f63c135daab2214614e93c3926d3a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715502"
---
# <a name="functional-area-permissions-master-data-services"></a><span data-ttu-id="52cf7-102">機能領域権限 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="52cf7-102">Functional Area Permissions (Master Data Services)</span></span>
  <span data-ttu-id="52cf7-103">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] ユーザー インターフェイス (UI) の各機能領域に、権限を割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="52cf7-103">You can assign permission to each of the functional areas of the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] user interface (UI).</span></span> <span data-ttu-id="52cf7-104">次の 5 つの機能領域があります。</span><span class="sxs-lookup"><span data-stu-id="52cf7-104">There are five functional areas:</span></span>  
  
-   <span data-ttu-id="52cf7-105">**エクスプローラー**</span><span class="sxs-lookup"><span data-stu-id="52cf7-105">**Explorer**</span></span>  
  
-   <span data-ttu-id="52cf7-106">**バージョン管理**</span><span class="sxs-lookup"><span data-stu-id="52cf7-106">**Version Management**</span></span>  
  
-   <span data-ttu-id="52cf7-107">**統合管理**</span><span class="sxs-lookup"><span data-stu-id="52cf7-107">**Integration Management**</span></span>  
  
-   <span data-ttu-id="52cf7-108">**システム管理**</span><span class="sxs-lookup"><span data-stu-id="52cf7-108">**System Administration**</span></span>  
  
-   <span data-ttu-id="52cf7-109">**ユーザー/グループの権限**</span><span class="sxs-lookup"><span data-stu-id="52cf7-109">**User and Group Permissions**</span></span>  
  
 <span data-ttu-id="52cf7-110">機能領域に権限を割り当てると、UI のその領域がユーザーまたはグループに表示されます。</span><span class="sxs-lookup"><span data-stu-id="52cf7-110">When you assign permission to a functional area, you are making an area of the UI visible to the user or group.</span></span>  
  
 <span data-ttu-id="52cf7-111">**[エクスプローラー]** 機能領域内でユーザーがアクセスできるデータは、モデル オブジェクトおよび階層メンバーに割り当てられた追加権限によって決定されます。</span><span class="sxs-lookup"><span data-stu-id="52cf7-111">Within the **Explorer** functional area, additional permissions assigned to model objects and hierarchy members determine which data a user can access.</span></span> <span data-ttu-id="52cf7-112">その他のすべての機能領域内でモデルを表示および操作するには、ユーザーはモデル管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="52cf7-112">Within all other functional areas, a user must be a model administrator to view a model and act on it.</span></span> <span data-ttu-id="52cf7-113">詳細については、「[管理者 &#40;マスターデータサービス&#41;](administrators-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="52cf7-113">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
 <span data-ttu-id="52cf7-114">**にアクセスするには、ユーザーまたはグループが、少なくとも 1 つの機能領域および** [モデル] [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]タブに表示される少なくとも 1 つのモデルに対する権限を持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="52cf7-114">A user or group must have permission to at least one functional area and one model on the **Models** tab in order to access [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52cf7-115">参照</span><span class="sxs-lookup"><span data-stu-id="52cf7-115">See Also</span></span>  
 <span data-ttu-id="52cf7-116">[機能領域のアクセス許可を割り当て &#40;マスターデータサービス&#41;](../../2014/master-data-services/assign-functional-area-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="52cf7-116">[Assign Functional Area Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/assign-functional-area-permissions-master-data-services.md) </span></span>  
 <span data-ttu-id="52cf7-117">[モデルオブジェクト権限 &#40;マスターデータサービス&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="52cf7-117">[Model Object Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md) </span></span>  
 <span data-ttu-id="52cf7-118">[階層メンバーの権限 &#40;マスターデータサービス&#41;](../../2014/master-data-services/hierarchy-member-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="52cf7-118">[Hierarchy Member Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/hierarchy-member-permissions-master-data-services.md) </span></span>  
 [<span data-ttu-id="52cf7-119">権限の決定方法 (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="52cf7-119">How Permissions Are Determined &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/how-permissions-are-determined-master-data-services.md)  
  
  
