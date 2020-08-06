---
title: モデル オブジェクト アクセス許可を割り当てる (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- models [Master Data Services], assigning object permissions
- permissions [Master Data Services], assigning model object permissions
ms.assetid: 4b80148d-2318-415c-9479-28c240e48bcd
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 92ac8ef3ac63b7128c4cbb7e9305ee6bd56ca010
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641726"
---
# <a name="assign-model-object-permissions-master-data-services"></a><span data-ttu-id="6989e-102">モデル オブジェクト権限を割り当てる (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="6989e-102">Assign Model Object Permissions (Master Data Services)</span></span>
  <span data-ttu-id="6989e-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]では、 **の** [エクスプローラー] [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]機能領域内のデータにユーザーまたはグループがアクセスできるようにする必要があるとき、またはユーザーまたはグループを管理者にする必要があるときは、モデル オブジェクトに権限を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="6989e-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], assign permissions to model objects when you need to give a user or group access to data in the **Explorer** functional area of [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], or when you need to make a user or group an administrator.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6989e-104">モデルに権限を割り当てると、その他のすべてのモデルへの権限は暗黙的に拒否されます。</span><span class="sxs-lookup"><span data-stu-id="6989e-104">When you assign permission to a model, permission to all other models is implicitly denied.</span></span> <span data-ttu-id="6989e-105">モデル オブジェクト権限を割り当てない場合、ユーザーまたはグループは **[エクスプローラー]** のデータにアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="6989e-105">If you do not assign model object permissions, the user or group cannot access any data in **Explorer**.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="6989e-106">前提条件</span><span class="sxs-lookup"><span data-stu-id="6989e-106">Prerequisites</span></span>  
 <span data-ttu-id="6989e-107">この手順を実行するには</span><span class="sxs-lookup"><span data-stu-id="6989e-107">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="6989e-108">**[ユーザー/グループの権限]** 機能領域にアクセスするための権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="6989e-108">You must have permission to access the **Users and Group Permissions** functional area.</span></span>  
  
-   <span data-ttu-id="6989e-109">モデル管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="6989e-109">You must be a model administrator.</span></span> <span data-ttu-id="6989e-110">詳細については、「[管理者 &#40;マスターデータサービス&#41;](administrators-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6989e-110">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-assign-model-object-permissions"></a><span data-ttu-id="6989e-111">モデル オブジェクト権限を割り当てるには</span><span class="sxs-lookup"><span data-stu-id="6989e-111">To assign model object permissions</span></span>  
  
1.  <span data-ttu-id="6989e-112">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[ユーザー/グループの権限]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6989e-112">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **User and Group Permissions**.</span></span>  
  
2.  <span data-ttu-id="6989e-113">**[ユーザー]** または **[グループ]** ページで、編集するユーザーまたはグループの行を選択します。</span><span class="sxs-lookup"><span data-stu-id="6989e-113">On the **Users** or **Groups** page, select the row for the user or group that you want to edit.</span></span>  
  
3.  <span data-ttu-id="6989e-114">**[選択したユーザーの編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6989e-114">Click **Edit selected user**.</span></span>  
  
4.  <span data-ttu-id="6989e-115">**[モデル]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="6989e-115">Click the **Models** tab.</span></span>  
  
5.  <span data-ttu-id="6989e-116">**[モデル]** ボックスの一覧からモデルを選択します (オプション)。</span><span class="sxs-lookup"><span data-stu-id="6989e-116">Optionally, select a model from the **Model** list.</span></span>  
  
6.  <span data-ttu-id="6989e-117">**[編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6989e-117">Click **Edit**.</span></span>  
  
7.  <span data-ttu-id="6989e-118">ツリーを展開して、権限を割り当てるモデル オブジェクトをクリックします。</span><span class="sxs-lookup"><span data-stu-id="6989e-118">Expand the tree, and click the model object you want to assign permissions to.</span></span>  
  
8.  <span data-ttu-id="6989e-119">メニューから、[**読み取り**専用]、[**更新**]、または [**拒否**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="6989e-119">From the menu, select **Read-only**, **Update**, or **Deny**.</span></span>  
  
9. <span data-ttu-id="6989e-120">**[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6989e-120">Click **Save**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="6989e-121">次の手順</span><span class="sxs-lookup"><span data-stu-id="6989e-121">Next Steps</span></span>  
  
-   <span data-ttu-id="6989e-122">(省略可能) [階層メンバーの権限を割り当てる (マスター データ サービス)](../../2014/master-data-services/assign-hierarchy-member-permissions-master-data-services.md)</span><span class="sxs-lookup"><span data-stu-id="6989e-122">(Optional) [Assign Hierarchy Member Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/assign-hierarchy-member-permissions-master-data-services.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6989e-123">参照</span><span class="sxs-lookup"><span data-stu-id="6989e-123">See Also</span></span>  
 <span data-ttu-id="6989e-124">[マスターデータサービス&#41;&#40;モデルオブジェクト権限の削除](../../2014/master-data-services/delete-model-object-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="6989e-124">[Delete Model Object Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/delete-model-object-permissions-master-data-services.md) </span></span>  
 <span data-ttu-id="6989e-125">[モデルオブジェクト権限 &#40;マスターデータサービス&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="6989e-125">[Model Object Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md) </span></span>  
 [<span data-ttu-id="6989e-126">モデル管理者を作成する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="6989e-126">Create a Model Administrator &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-model-administrator-master-data-services.md)  
  
  
