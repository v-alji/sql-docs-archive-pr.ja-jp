---
title: 階層メンバーのアクセス許可を割り当てる (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- permissions [Master Data Services], assigning member permissions
- members [Master Data Services], assigning permissions
ms.assetid: e1b8b46a-7cd1-4a7d-9345-dd7df081e145
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 4a1602f9fe351f826b63d4447f90dcf02a10f49e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641742"
---
# <a name="assign-hierarchy-member-permissions-master-data-services"></a><span data-ttu-id="76c60-102">階層メンバーの権限を割り当てる (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="76c60-102">Assign Hierarchy Member Permissions (Master Data Services)</span></span>
  <span data-ttu-id="76c60-103">階層メンバーに権限を割り当てて、 **の** [エクスプローラー] [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]機能領域にあるデータを表示するためのアクセス権をユーザーまたはグループに付与します。</span><span class="sxs-lookup"><span data-stu-id="76c60-103">Assign permissions to hierarchy members to give users or groups access to view data in the **Explorer** functional area of [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].</span></span>  
  
 <span data-ttu-id="76c60-104">階層メンバーの権限はオプションです。</span><span class="sxs-lookup"><span data-stu-id="76c60-104">Hierarchy member permissions are optional.</span></span> <span data-ttu-id="76c60-105">階層メンバーの権限は、必須であるモデル オブジェクトの権限に粒度を追加します。</span><span class="sxs-lookup"><span data-stu-id="76c60-105">They provide added granularity to model object permissions, which are required.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="76c60-106">前提条件</span><span class="sxs-lookup"><span data-stu-id="76c60-106">Prerequisites</span></span>  
 <span data-ttu-id="76c60-107">この手順を実行するには</span><span class="sxs-lookup"><span data-stu-id="76c60-107">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="76c60-108">**[ユーザー/グループの権限]** 機能領域にアクセスするための権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="76c60-108">You must have permission to access the **Users and Group Permissions** functional area.</span></span>  
  
-   <span data-ttu-id="76c60-109">モデル管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="76c60-109">You must be a model administrator.</span></span> <span data-ttu-id="76c60-110">詳細については、「[管理者 &#40;マスターデータサービス&#41;](administrators-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="76c60-110">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-assign-hierarchy-member-permissions"></a><span data-ttu-id="76c60-111">階層メンバーの権限を割り当てるには</span><span class="sxs-lookup"><span data-stu-id="76c60-111">To assign hierarchy member permissions</span></span>  
  
1.  <span data-ttu-id="76c60-112">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[ユーザー/グループの権限]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="76c60-112">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **User and Group Permissions**.</span></span>  
  
2.  <span data-ttu-id="76c60-113">**[ユーザー]** または **[グループ]** ページで、編集するユーザーまたはグループの行を選択します。</span><span class="sxs-lookup"><span data-stu-id="76c60-113">On the **Users** or **Groups** page, select the row for the user or group that you want to edit.</span></span>  
  
3.  <span data-ttu-id="76c60-114">**[選択したユーザーの編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="76c60-114">Click **Edit selected user**.</span></span>  
  
4.  <span data-ttu-id="76c60-115">**[階層メンバー]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="76c60-115">Click the **Hierarchy Members** tab.</span></span>  
  
5.  <span data-ttu-id="76c60-116">**[モデル]** ボックスの一覧からモデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="76c60-116">From the **Model** list, select a model.</span></span>  
  
6.  <span data-ttu-id="76c60-117">**[バージョン]** ボックスの一覧からバージョンを選択します。</span><span class="sxs-lookup"><span data-stu-id="76c60-117">From the **Version** list, select a version.</span></span>  
  
7.  <span data-ttu-id="76c60-118">**[階層]** ボックスの一覧から階層を選択します。</span><span class="sxs-lookup"><span data-stu-id="76c60-118">From the **Hierarchy** list, select a hierarchy.</span></span>  
  
8.  <span data-ttu-id="76c60-119">**[編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="76c60-119">Click **Edit**.</span></span>  
  
9. <span data-ttu-id="76c60-120">ツリーを展開して、権限を割り当てる階層ノードをクリックします。</span><span class="sxs-lookup"><span data-stu-id="76c60-120">Expand the tree, and click the hierarchy node you want to assign permissions to.</span></span>  
  
10. <span data-ttu-id="76c60-121">メニューから、[**読み取り**専用]、[**更新**]、または [**拒否**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="76c60-121">From the menu, select **Read-only**, **Update**, or **Deny**.</span></span>  
  
11. <span data-ttu-id="76c60-122">**[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="76c60-122">Click **Save**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="76c60-123">階層メンバーの権限は、すぐには有効になりません。</span><span class="sxs-lookup"><span data-stu-id="76c60-123">Hierarchy member permissions do not take effect immediately.</span></span> <span data-ttu-id="76c60-124">詳細については、「[メンバー権限を直ちに適用する (マスター データ サービス)](../../2014/master-data-services/immediately-apply-member-permissions-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="76c60-124">See [Immediately Apply Member Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/immediately-apply-member-permissions-master-data-services.md) for more information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76c60-125">参照</span><span class="sxs-lookup"><span data-stu-id="76c60-125">See Also</span></span>  
 <span data-ttu-id="76c60-126">[マスターデータサービス &#40;階層メンバーの権限を削除&#41;](../../2014/master-data-services/delete-hierarchy-member-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="76c60-126">[Delete Hierarchy Member Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/delete-hierarchy-member-permissions-master-data-services.md) </span></span>  
 <span data-ttu-id="76c60-127">[モデルオブジェクト権限の割り当て &#40;マスターデータサービス&#41;](../../2014/master-data-services/assign-model-object-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="76c60-127">[Assign Model Object Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/assign-model-object-permissions-master-data-services.md) </span></span>  
 [<span data-ttu-id="76c60-128">階層メンバーの権限 (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="76c60-128">Hierarchy Member Permissions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/hierarchy-member-permissions-master-data-services.md)  
  
  
