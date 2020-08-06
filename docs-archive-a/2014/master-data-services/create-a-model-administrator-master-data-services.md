---
title: モデル管理者を作成する (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- administrators [Master Data Services], creating
ms.assetid: dae17afc-3b39-490e-b51f-2d8da26d429e
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 24efc3961e6ed5b9f41b2321dfcc4fbf16632270
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645717"
---
# <a name="create-a-model-administrator-master-data-services"></a><span data-ttu-id="cb571-102">モデル管理者を作成する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="cb571-102">Create a Model Administrator (Master Data Services)</span></span>
  <span data-ttu-id="cb571-103">で [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 、1つまたは複数のモデルのすべてのオブジェクトに対する**更新**権限をグループまたはユーザーに付与する場合は、モデル管理者を作成します。</span><span class="sxs-lookup"><span data-stu-id="cb571-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], create a model administrator when you want a group or user to have **Update** permission to all objects in one or more models.</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="cb571-104">管理を簡略化するには、Windows グループまたはローカルグループを作成し、モデル管理者として構成します。</span><span class="sxs-lookup"><span data-stu-id="cb571-104">To simplify administration, create a Windows or local group and configure it as a model administrator.</span></span> <span data-ttu-id="cb571-105">また、 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]にアクセスすることなくグループに対してユーザーの追加または削除を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="cb571-105">You can then add and remove users from the group without accessing [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="cb571-106">前提条件</span><span class="sxs-lookup"><span data-stu-id="cb571-106">Prerequisites</span></span>  
 <span data-ttu-id="cb571-107">この手順を実行するには</span><span class="sxs-lookup"><span data-stu-id="cb571-107">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="cb571-108">**[ユーザー/グループの権限]** 機能領域にアクセスするための権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="cb571-108">You must have permission to access the **User and Group Permissions** functional area.</span></span>  
  
-   <span data-ttu-id="cb571-109">モデル管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="cb571-109">You must be a model administrator.</span></span> <span data-ttu-id="cb571-110">詳細については、「[管理者 &#40;マスターデータサービス&#41;](administrators-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cb571-110">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-create-a-model-administrator"></a><span data-ttu-id="cb571-111">モデル管理者を作成するには</span><span class="sxs-lookup"><span data-stu-id="cb571-111">To create a model administrator</span></span>  
  
1.  <span data-ttu-id="cb571-112">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[ユーザー/グループの権限]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cb571-112">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **User and Group Permissions**.</span></span>  
  
2.  <span data-ttu-id="cb571-113">**[ユーザー]** または **[グループ]** ページで、編集するユーザーまたはグループの行を選択します。</span><span class="sxs-lookup"><span data-stu-id="cb571-113">On the **Users** or **Groups** page, select the row for the user or group that you want to edit.</span></span>  
  
3.  <span data-ttu-id="cb571-114">**[選択したユーザーの編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cb571-114">Click **Edit selected user**.</span></span>  
  
4.  <span data-ttu-id="cb571-115">**[モデル]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="cb571-115">Click the **Models** tab.</span></span>  
  
5.  <span data-ttu-id="cb571-116">**[モデル]** ボックスの一覧からモデルを選択します (オプション)。</span><span class="sxs-lookup"><span data-stu-id="cb571-116">Optionally, select a model from the **Model** list.</span></span>  
  
6.  <span data-ttu-id="cb571-117">**[編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cb571-117">Click **Edit**.</span></span>  
  
7.  <span data-ttu-id="cb571-118">権限を与えるモデルをクリックします。</span><span class="sxs-lookup"><span data-stu-id="cb571-118">Click the model you want to grant permission to.</span></span>  
  
8.  <span data-ttu-id="cb571-119">メニューから [**更新**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="cb571-119">From the menu, select **Update**.</span></span>  
  
9. <span data-ttu-id="cb571-120">グループまたはユーザーを管理者にする各モデルについて、手順 7 と 8 を実行します。</span><span class="sxs-lookup"><span data-stu-id="cb571-120">Complete steps 7 and 8 for each model you want the group or user to be an administrator for.</span></span>  
  
10. <span data-ttu-id="cb571-121">**[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cb571-121">Click **Save**.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cb571-122">解説</span><span class="sxs-lookup"><span data-stu-id="cb571-122">Remarks</span></span>  
 <span data-ttu-id="cb571-123">モデル オブジェクトまたは階層メンバーに他の権限を割り当てないでください。</span><span class="sxs-lookup"><span data-stu-id="cb571-123">Do not assign any other permissions to model objects or hierarchy members.</span></span> <span data-ttu-id="cb571-124">この場合、ユーザーは管理者ではなくなり、[**エクスプローラー**] 以外の機能領域でモデルを表示することはできません。</span><span class="sxs-lookup"><span data-stu-id="cb571-124">If you do, the user is no longer an administrator and cannot view the model in any functional area other than **Explorer**.</span></span>  
  
 <span data-ttu-id="cb571-125">例外が1つあります。ユーザーが [**階層メンバー** ] タブで階層の**ルート**に割り当てられた**更新**権限を持っている場合、そのユーザーは引き続きモデル管理者と見なされます。</span><span class="sxs-lookup"><span data-stu-id="cb571-125">There is one exception: if the user has **Update** permission assigned to a hierarchy **Root** on the **Hierarchy Members** tab, the user is still considered a model administrator.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb571-126">参照</span><span class="sxs-lookup"><span data-stu-id="cb571-126">See Also</span></span>  
 <span data-ttu-id="cb571-127">[管理者 &#40;マスターデータサービス&#41;](administrators-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="cb571-127">[Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md) </span></span>  
 <span data-ttu-id="cb571-128">[モデルオブジェクト権限の割り当て &#40;マスターデータサービス&#41;](../../2014/master-data-services/assign-model-object-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="cb571-128">[Assign Model Object Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/assign-model-object-permissions-master-data-services.md) </span></span>  
 <span data-ttu-id="cb571-129">[階層メンバーの権限を割り当てる &#40;マスターデータサービス&#41;](../../2014/master-data-services/assign-hierarchy-member-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="cb571-129">[Assign Hierarchy Member Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/assign-hierarchy-member-permissions-master-data-services.md) </span></span>  
 <span data-ttu-id="cb571-130">[モデルオブジェクト権限 &#40;マスターデータサービス&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="cb571-130">[Model Object Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md) </span></span>  
 [<span data-ttu-id="cb571-131">階層メンバーの権限 (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="cb571-131">Hierarchy Member Permissions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/hierarchy-member-permissions-master-data-services.md)  
  
  
