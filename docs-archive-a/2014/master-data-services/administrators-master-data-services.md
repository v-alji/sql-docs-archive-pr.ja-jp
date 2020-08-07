---
title: 管理者 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- administrators [Master Data Services], about administrators
- administrators [Master Data Services]
- models [Master Data Services], administrators
ms.assetid: d330aa4e-6ade-4b09-b376-1b15d6c78f7d
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 52e16d4e77acc0a6b50b87e00184918cb9ce64b1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718398"
---
# <a name="administrators-master-data-services"></a><span data-ttu-id="d3bc3-102">管理者 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="d3bc3-102">Administrators (Master Data Services)</span></span>
  <span data-ttu-id="d3bc3-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] には、モデル管理者と [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] システム管理者の 2 種類の管理者があります。</span><span class="sxs-lookup"><span data-stu-id="d3bc3-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], there are two types of administrators: model administrators, and the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] system administrator.</span></span>  
  
## <a name="model-administrators"></a><span data-ttu-id="d3bc3-104">モデル管理者</span><span class="sxs-lookup"><span data-stu-id="d3bc3-104">Model Administrators</span></span>  
 <span data-ttu-id="d3bc3-105">で [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] は、モデル管理者は、[**モデルオブジェクト**] タブの最上位のモデルオブジェクトに割り当てられた**更新**権限を持ち、その他の割り当てられた権限がないユーザーです。</span><span class="sxs-lookup"><span data-stu-id="d3bc3-105">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], a model administrator is a user who has **Update** permission assigned to the top-level model object on the **Model Objects** tab and no other assigned permissions.</span></span>  
  
-   <span data-ttu-id="d3bc3-106">ユーザーに **[エクスプローラー]** 機能領域へのアクセス権がある場合、ユーザーはこのデータ領域のすべてのマスター データを追加、削除、および更新できます。</span><span class="sxs-lookup"><span data-stu-id="d3bc3-106">If the user has access to the **Explorer** functional area, the user can add, delete, and update all master data in this area.</span></span>  
  
-   <span data-ttu-id="d3bc3-107">ユーザーに他の機能領域へのアクセス権がある場合、その機能領域で利用できるすべての管理タスクを実行できます。</span><span class="sxs-lookup"><span data-stu-id="d3bc3-107">If the user has access to other functional areas, the user can perform all administrative tasks available in the functional area.</span></span>  
  
 <span data-ttu-id="d3bc3-108">各モデルには複数の管理者を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="d3bc3-108">Each model can have multiple administrators.</span></span> <span data-ttu-id="d3bc3-109">各ユーザーは、1 つまたは複数のモデルのモデル管理者になることができ、 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] の配置内のすべてのモデルのモデル管理者になることもできます。</span><span class="sxs-lookup"><span data-stu-id="d3bc3-109">Each user can be a model administrator for one, several, or all models in the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] deployment.</span></span>  
  
 <span data-ttu-id="d3bc3-110">ユーザーをモデル管理者として構成するには、 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] を使用するかプログラムで構成します。</span><span class="sxs-lookup"><span data-stu-id="d3bc3-110">A user can be configured as a model administrator either in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] or programmatically.</span></span> <span data-ttu-id="d3bc3-111">詳細については、「 [モデル管理者を作成する (マスター データ サービス)](create-a-model-administrator-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d3bc3-111">For more information, see [Create a Model Administrator &#40;Master Data Services&#41;](create-a-model-administrator-master-data-services.md).</span></span>  
  
## <a name="master-data-services-system-administrator"></a><span data-ttu-id="d3bc3-112">Master Data Services システム管理者</span><span class="sxs-lookup"><span data-stu-id="d3bc3-112">Master Data Services System Administrator</span></span>  
 <span data-ttu-id="d3bc3-113">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] システム管理者は 1 人だけです。</span><span class="sxs-lookup"><span data-stu-id="d3bc3-113">There is only one [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] system administrator.</span></span> <span data-ttu-id="d3bc3-114">システム管理者は、データベースの作成時に**管理者アカウント**に対して指定されたユーザーです [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="d3bc3-114">The system administrator is the user specified for the **Administrator Account** when you create the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database.</span></span>  
  
 <span data-ttu-id="d3bc3-115">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] システム管理者:</span><span class="sxs-lookup"><span data-stu-id="d3bc3-115">The [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] system administrator:</span></span>  
  
-   <span data-ttu-id="d3bc3-116">すべての機能領域に対するアクセス権が自動的に付与されます。</span><span class="sxs-lookup"><span data-stu-id="d3bc3-116">Automatically has access to all functional areas.</span></span>  
  
-   <span data-ttu-id="d3bc3-117">[**エクスプローラー** ] 機能領域のすべてのモデルのすべてのマスターデータを追加、削除、および更新できます。</span><span class="sxs-lookup"><span data-stu-id="d3bc3-117">Can add, delete, and update all master data for all models in the **Explorer** functional area.</span></span>  
  
 <span data-ttu-id="d3bc3-118"> システム管理者として割り当てられているユーザーを変更できます。</span><span class="sxs-lookup"><span data-stu-id="d3bc3-118">You can change the user who is assigned as the system administrator.</span></span> <span data-ttu-id="d3bc3-119">詳細については、「[マスターデータサービス&#41;&#40;システム管理者アカウントを変更](../../2014/master-data-services/change-the-system-administrator-account-master-data-services.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d3bc3-119">For more information, see [Change the System Administrator Account &#40;Master Data Services&#41;](../../2014/master-data-services/change-the-system-administrator-account-master-data-services.md).</span></span>  
  
## <a name="comparing-administrator-types"></a><span data-ttu-id="d3bc3-120">管理者の種類の比較</span><span class="sxs-lookup"><span data-stu-id="d3bc3-120">Comparing Administrator Types</span></span>  
  
|<span data-ttu-id="d3bc3-121">管理者の種類</span><span class="sxs-lookup"><span data-stu-id="d3bc3-121">Administrator Type</span></span>|<span data-ttu-id="d3bc3-122">Description</span><span class="sxs-lookup"><span data-stu-id="d3bc3-122">Description</span></span>|  
|------------------------|-----------------|  
|[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] <span data-ttu-id="d3bc3-123">システム管理者</span><span class="sxs-lookup"><span data-stu-id="d3bc3-123">system administrator</span></span>|<span data-ttu-id="d3bc3-124">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] で割り当てられている権限は、管理者のアクセス権に影響を与えません。</span><span class="sxs-lookup"><span data-stu-id="d3bc3-124">Permissions assigned in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] have no effect on the administrator's access.</span></span><br /><br /> <span data-ttu-id="d3bc3-125">すべてのモデルに対する**更新**権限が自動的に付与されます。</span><span class="sxs-lookup"><span data-stu-id="d3bc3-125">Automatically has **Update** permission to all models.</span></span><br /><br /> <span data-ttu-id="d3bc3-126">すべての機能領域に対するアクセス権が自動的に付与されます。</span><span class="sxs-lookup"><span data-stu-id="d3bc3-126">Automatically has access to all functional areas.</span></span><br /><br /> <span data-ttu-id="d3bc3-127">Mdm.tbluser では、 **ID**列の値は**1**です。</span><span class="sxs-lookup"><span data-stu-id="d3bc3-127">In mdm.tblUser, the value in the **ID** column is **1**.</span></span>|  
|<span data-ttu-id="d3bc3-128">モデル管理者</span><span class="sxs-lookup"><span data-stu-id="d3bc3-128">Model administrator</span></span>|<span data-ttu-id="d3bc3-129">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で割り当てられた権限によって、ユーザーがモデル管理者であるかどうかが決まります。</span><span class="sxs-lookup"><span data-stu-id="d3bc3-129">Permissions assigned in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] determine whether or not the user is a model administrator.</span></span><br /><br /> <span data-ttu-id="d3bc3-130">明示的に割り当てられている権限、またはグループから継承した権限に基づいてモデル管理者になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="d3bc3-130">Can be a model administrator based on permissions assigned explicitly or permissions inherited from a group.</span></span><br /><br /> <span data-ttu-id="d3bc3-131">は、最上位のモデルオブジェクトに割り当てられた**更新**権限を持ち、他の権限がないモデルに対してのみ管理者になります。</span><span class="sxs-lookup"><span data-stu-id="d3bc3-131">Is an administrator only for models that have **Update** permission assigned to top-level model object, and no other permissions.</span></span><br /><br /> <span data-ttu-id="d3bc3-132">アクセス権が付与された機能領域だけにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="d3bc3-132">Has access only to functional areas that access is granted to.</span></span><br /><br /> <span data-ttu-id="d3bc3-133">Mdm.tbluser で、 **ID**列の値が**1**ではありません。</span><span class="sxs-lookup"><span data-stu-id="d3bc3-133">In mdm.tblUser, the value in the **ID** column is not **1**.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d3bc3-134">参照</span><span class="sxs-lookup"><span data-stu-id="d3bc3-134">See Also</span></span>  
 <span data-ttu-id="d3bc3-135">[モデル管理者 &#40;マスターデータサービスを作成し&#41;](create-a-model-administrator-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="d3bc3-135">[Create a Model Administrator &#40;Master Data Services&#41;](create-a-model-administrator-master-data-services.md) </span></span>  
 <span data-ttu-id="d3bc3-136">[システム管理者アカウント &#40;マスターデータサービスに変更&#41;](../../2014/master-data-services/change-the-system-administrator-account-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="d3bc3-136">[Change the System Administrator Account &#40;Master Data Services&#41;](../../2014/master-data-services/change-the-system-administrator-account-master-data-services.md) </span></span>  
 <span data-ttu-id="d3bc3-137">[マスターデータサービスデータベースを作成する](install-windows/create-a-master-data-services-database.md) </span><span class="sxs-lookup"><span data-stu-id="d3bc3-137">[Create a Master Data Services Database](install-windows/create-a-master-data-services-database.md) </span></span>  
 [<span data-ttu-id="d3bc3-138">通知 (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="d3bc3-138">Notifications &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/notifications-master-data-services.md)  
  
  
