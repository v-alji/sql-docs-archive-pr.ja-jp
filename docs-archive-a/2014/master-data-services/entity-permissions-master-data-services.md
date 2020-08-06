---
title: エンティティ アクセス許可 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- entities [Master Data Services], permissions
- permissions [Master Data Services], entities
ms.assetid: 22785062-4faf-46ee-bffa-01cbd6d5a5b3
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: eaec809cb0f9dea3f760958bcf95015edd5a490e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712065"
---
# <a name="entity-permissions-master-data-services"></a><span data-ttu-id="a8122-102">エンティティ権限 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="a8122-102">Entity Permissions (Master Data Services)</span></span>
  <span data-ttu-id="a8122-103">エンティティ権限は、次のものに適用されます。</span><span class="sxs-lookup"><span data-stu-id="a8122-103">Entity permissions apply to:</span></span>  
  
-   <span data-ttu-id="a8122-104">リーフ メンバーと統合メンバーの両方に対する、 **Name** および **Code**を含む、エンティティのすべての属性。</span><span class="sxs-lookup"><span data-stu-id="a8122-104">All of the entity's attributes, including **Name** and **Code**, for both leaf and consolidated members.</span></span>  
  
-   <span data-ttu-id="a8122-105">エンティティのすべてのコレクション。</span><span class="sxs-lookup"><span data-stu-id="a8122-105">All of the entity's collections.</span></span>  
  
-   <span data-ttu-id="a8122-106">明示的階層のメンバーシップとリレーションシップ。</span><span class="sxs-lookup"><span data-stu-id="a8122-106">Explicit hierarchy memberships and relationships.</span></span>  
  
 <span data-ttu-id="a8122-107">エンティティに対する権限がある場合は、エンティティ、その明示的階層、およびそのコレクションに対してメンバーの追加および削除を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="a8122-107">When you have permission to an entity, you can add and remove members from the entity, its explicit hierarchies, and its collections.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a8122-108">これらの権限は、ユーザー インターフェイスの **[エクスプローラー]** 機能領域にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="a8122-108">These permissions apply to the **Explorer** functional area of the user interface only.</span></span>  
  
|<span data-ttu-id="a8122-109">権限</span><span class="sxs-lookup"><span data-stu-id="a8122-109">Permission</span></span>|<span data-ttu-id="a8122-110">説明</span><span class="sxs-lookup"><span data-stu-id="a8122-110">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="a8122-111">**読み取り専用です。**</span><span class="sxs-lookup"><span data-stu-id="a8122-111">**Read-only**</span></span>|<span data-ttu-id="a8122-112">エンティティが表示されますが、ユーザーはメンバーを追加、削除、または変更できません。</span><span class="sxs-lookup"><span data-stu-id="a8122-112">The entity is displayed but the user cannot add, remove, or change members.</span></span>|  
|<span data-ttu-id="a8122-113">**アップデート**</span><span class="sxs-lookup"><span data-stu-id="a8122-113">**Update**</span></span>|<span data-ttu-id="a8122-114">エンティティが表示され、ユーザーはメンバーを追加、削除、および変更できます。</span><span class="sxs-lookup"><span data-stu-id="a8122-114">The entity is displayed and the user can add, remove, and change members.</span></span>|  
|<span data-ttu-id="a8122-115">**Deny**</span><span class="sxs-lookup"><span data-stu-id="a8122-115">**Deny**</span></span>|<span data-ttu-id="a8122-116">エンティティが表示されません。</span><span class="sxs-lookup"><span data-stu-id="a8122-116">The entity is not displayed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a8122-117">参照</span><span class="sxs-lookup"><span data-stu-id="a8122-117">See Also</span></span>  
 <span data-ttu-id="a8122-118">[モデルオブジェクト権限の割り当て &#40;マスターデータサービス&#41;](assign-model-object-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="a8122-118">[Assign Model Object Permissions &#40;Master Data Services&#41;](assign-model-object-permissions-master-data-services.md) </span></span>  
 <span data-ttu-id="a8122-119">[モデルオブジェクト権限 &#40;マスターデータサービス&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="a8122-119">[Model Object Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md) </span></span>  
 [<span data-ttu-id="a8122-120">エンティティ (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="a8122-120">Entities &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/entities-master-data-services.md)  
  
  
