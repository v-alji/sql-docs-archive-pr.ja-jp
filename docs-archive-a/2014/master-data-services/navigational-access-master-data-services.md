---
title: ナビゲーション アクセス (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- navigational access [Master Data Services]
- security [Master Data Services], navigational access
ms.assetid: 3403b7b0-44e2-48c3-a1b7-9c4612b874b8
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 7af3c16d98320b6fea3d4611e9e4c6d37c6015bd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631115"
---
# <a name="navigational-access-master-data-services"></a><span data-ttu-id="3e606-102">ナビゲーション アクセス (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="3e606-102">Navigational Access (Master Data Services)</span></span>
  <span data-ttu-id="3e606-103">ナビゲーション アクセスは、 **[モデル]** タブで割り当てられるモデル オブジェクト セキュリティに適用されます。</span><span class="sxs-lookup"><span data-stu-id="3e606-103">Navigational access applies to model object security, which is assigned on the **Models** tab.</span></span>  
  
 <span data-ttu-id="3e606-104">ナビゲーション アクセスは、セキュリティを割り当てたレベルよりも高いレベルへのアクセスです。</span><span class="sxs-lookup"><span data-stu-id="3e606-104">Navigational access is the access you get to levels higher than where you've assigned security.</span></span>  
  
 <span data-ttu-id="3e606-105">この例では、権限がエンティティに割り当てられているため、ナビゲーション アクセスがモデル レベルで付与されます。</span><span class="sxs-lookup"><span data-stu-id="3e606-105">In this example, permissions are assigned to an entity, and so navigational access is granted at the model level.</span></span>  
  
 <span data-ttu-id="3e606-106">![mds_conc_inheritance_model](../../2014/master-data-services/media/mds-conc-inheritance-model.gif "mds_conc_inheritance_model")</span><span class="sxs-lookup"><span data-stu-id="3e606-106">![mds_conc_inheritance_model](../../2014/master-data-services/media/mds-conc-inheritance-model.gif "mds_conc_inheritance_model")</span></span>  
  
 <span data-ttu-id="3e606-107">**エンティティ**</span><span class="sxs-lookup"><span data-stu-id="3e606-107">**Entities**</span></span>  
  
 <span data-ttu-id="3e606-108">エンティティ、リーフ メンバー、またはその統合メンバーに権限を割り当てた場合、ナビゲーション アクセスにより、すべてのメンバーの名前およびコードの読み取りまたは更新を実行できます。</span><span class="sxs-lookup"><span data-stu-id="3e606-108">When you assign permission to an entity, its leaf members, or its consolidated members, navigational access means you can read or update the name and code for all members.</span></span> <span data-ttu-id="3e606-109">また、モデル名を読み取ることもできます。</span><span class="sxs-lookup"><span data-stu-id="3e606-109">You can also read the model name.</span></span>  
  
 <span data-ttu-id="3e606-110">**属性**</span><span class="sxs-lookup"><span data-stu-id="3e606-110">**Attributes**</span></span>  
  
 <span data-ttu-id="3e606-111">属性に権限を割り当てた場合、ナビゲーション アクセスにより、エンティティのすべてのメンバーの名前およびコードの読み取りまたは更新を実行できます。</span><span class="sxs-lookup"><span data-stu-id="3e606-111">When you assign permission to an attribute, navigational access means you can read or update the name and code for all members in the entity.</span></span> <span data-ttu-id="3e606-112">また、モデル名を読み取ることもできます。</span><span class="sxs-lookup"><span data-stu-id="3e606-112">You can also read the model name.</span></span>  
  
 <span data-ttu-id="3e606-113">**コレクション**</span><span class="sxs-lookup"><span data-stu-id="3e606-113">**Collections**</span></span>  
  
 <span data-ttu-id="3e606-114">コレクションに権限を割り当てた場合、名前、コード、説明、および所有者 ID の読み取りまたは更新を実行できます。</span><span class="sxs-lookup"><span data-stu-id="3e606-114">When you assign permissions to collections, you can read or update the name, code, description and owner ID.</span></span> <span data-ttu-id="3e606-115">また、モデル名を読み取ることもできます。</span><span class="sxs-lookup"><span data-stu-id="3e606-115">You can also read the model name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e606-116">参照</span><span class="sxs-lookup"><span data-stu-id="3e606-116">See Also</span></span>  
 [<span data-ttu-id="3e606-117">権限の決定方法 (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="3e606-117">How Permissions Are Determined &#40;Master Data Services&#41;</span></span>](how-permissions-are-determined-master-data-services.md)  
  
  
