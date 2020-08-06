---
title: モデル オブジェクト アクセス許可を削除する (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- deleting model object permissions [Master Data Services]
- permissions [Master Data Services], deleting model object permissions
- models [Master Data Services], deleting object permissions
ms.assetid: 859c5952-f600-4940-8064-1afd13f7f6dc
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 98da869476e597d76a83b0b86cc9e6e4274a25e9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715522"
---
# <a name="delete-model-object-permissions-master-data-services"></a><span data-ttu-id="8dc4e-102">モデル オブジェクト権限を削除する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="8dc4e-102">Delete Model Object Permissions (Master Data Services)</span></span>
  <span data-ttu-id="8dc4e-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]でモデル オブジェクトの権限を削除して、作成されている割り当てを削除します。</span><span class="sxs-lookup"><span data-stu-id="8dc4e-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], delete model object permissions to remove any assignments that have been made.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="8dc4e-104">前提条件</span><span class="sxs-lookup"><span data-stu-id="8dc4e-104">Prerequisites</span></span>  
 <span data-ttu-id="8dc4e-105">この手順を実行するには</span><span class="sxs-lookup"><span data-stu-id="8dc4e-105">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="8dc4e-106">**[ユーザー/グループの権限]** 機能領域にアクセスするための権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="8dc4e-106">You must have permission to access the **Users and Group Permissions** functional area.</span></span>  
  
-   <span data-ttu-id="8dc4e-107">モデル管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="8dc4e-107">You must be a model administrator.</span></span> <span data-ttu-id="8dc4e-108">詳細については、「[管理者 &#40;マスターデータサービス&#41;](administrators-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8dc4e-108">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-delete-model-object-permissions"></a><span data-ttu-id="8dc4e-109">モデル オブジェクト権限を削除するには</span><span class="sxs-lookup"><span data-stu-id="8dc4e-109">To delete model object permissions</span></span>  
  
1.  <span data-ttu-id="8dc4e-110">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[ユーザー/グループの権限]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8dc4e-110">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **User and Group Permissions**.</span></span>  
  
2.  <span data-ttu-id="8dc4e-111">**[ユーザー]** または **[グループ]** ページで、編集するユーザーまたはグループの行を選択します。</span><span class="sxs-lookup"><span data-stu-id="8dc4e-111">On the **Users** or **Groups** page, select the row for the user or group that you want to edit.</span></span>  
  
3.  <span data-ttu-id="8dc4e-112">**[選択したユーザーの編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8dc4e-112">Click **Edit selected user**.</span></span>  
  
4.  <span data-ttu-id="8dc4e-113">**[モデル]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="8dc4e-113">Click the **Models** tab.</span></span>  
  
5.  <span data-ttu-id="8dc4e-114">**[モデル]** ボックスの一覧からモデルを選択します (オプション)。</span><span class="sxs-lookup"><span data-stu-id="8dc4e-114">Optionally, select a model from the **Model** list.</span></span>  
  
6.  <span data-ttu-id="8dc4e-115">[**モデル権限の概要**] ペインで、削除する権限の行を選択します。</span><span class="sxs-lookup"><span data-stu-id="8dc4e-115">In the **Model Permission Summary** pane, select the row for the permission that you want to delete.</span></span>  
  
7.  <span data-ttu-id="8dc4e-116">[**選択したアクセス許可の削除**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8dc4e-116">Click **Delete selected permission**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8dc4e-117">権限がグループから継承されている場合、ユーザーから権限を削除できません。</span><span class="sxs-lookup"><span data-stu-id="8dc4e-117">You cannot remove a permission from a user if the permission is inherited from a group.</span></span> <span data-ttu-id="8dc4e-118">グループから権限を削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8dc4e-118">You must remove the permission from the group instead.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8dc4e-119">参照</span><span class="sxs-lookup"><span data-stu-id="8dc4e-119">See Also</span></span>  
 <span data-ttu-id="8dc4e-120">[モデルオブジェクト権限 &#40;マスターデータサービス&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="8dc4e-120">[Model Object Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md) </span></span>  
 [<span data-ttu-id="8dc4e-121">モデル オブジェクト権限を割り当てる (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="8dc4e-121">Assign Model Object Permissions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/assign-model-object-permissions-master-data-services.md)  
  
  
