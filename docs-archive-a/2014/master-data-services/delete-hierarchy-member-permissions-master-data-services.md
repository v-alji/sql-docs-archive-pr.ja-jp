---
title: 階層メンバーのアクセス許可を削除する (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- deleting member permissions [Master Data Services]
- members [Master Data Services], deleting permissions
- permissions [Master Data Services], deleting member permissions
ms.assetid: 7f22d5e2-70c1-422c-99c2-e995a47d812a
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 8b6e7fbfc4379733d5cb809ce4d46d2c12d05a48
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715525"
---
# <a name="delete-hierarchy-member-permissions-master-data-services"></a><span data-ttu-id="78ef3-102">階層メンバーの権限を削除する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="78ef3-102">Delete Hierarchy Member Permissions (Master Data Services)</span></span>
  <span data-ttu-id="78ef3-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]でモデル オブジェクトの権限を削除して、作成されている割り当てを削除します。</span><span class="sxs-lookup"><span data-stu-id="78ef3-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], delete model object permissions to remove any assignments that have been made.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="78ef3-104">前提条件</span><span class="sxs-lookup"><span data-stu-id="78ef3-104">Prerequisites</span></span>  
 <span data-ttu-id="78ef3-105">この手順を実行するには</span><span class="sxs-lookup"><span data-stu-id="78ef3-105">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="78ef3-106">**[ユーザー/グループの権限]** 機能領域にアクセスするための権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="78ef3-106">You must have permission to access the **Users and Group Permissions** functional area.</span></span>  
  
-   <span data-ttu-id="78ef3-107">モデル管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="78ef3-107">You must be a model administrator.</span></span> <span data-ttu-id="78ef3-108">詳細については、「[管理者 &#40;マスターデータサービス&#41;](administrators-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="78ef3-108">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-delete-hierarchy-member-permissions"></a><span data-ttu-id="78ef3-109">階層メンバーの権限を削除するには</span><span class="sxs-lookup"><span data-stu-id="78ef3-109">To delete hierarchy member permissions</span></span>  
  
1.  <span data-ttu-id="78ef3-110">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[ユーザー/グループの権限]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="78ef3-110">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **User and Group Permissions**.</span></span>  
  
2.  <span data-ttu-id="78ef3-111">**[ユーザー]** または **[グループ]** ページで、編集するユーザーまたはグループの行を選択します。</span><span class="sxs-lookup"><span data-stu-id="78ef3-111">On the **Users** or **Groups** page, select the row for the user or group that you want to edit.</span></span>  
  
3.  <span data-ttu-id="78ef3-112">**[選択したユーザーの編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="78ef3-112">Click **Edit selected user**.</span></span>  
  
4.  <span data-ttu-id="78ef3-113">**[階層メンバー]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="78ef3-113">Click the **Hierarchy Members** tab.</span></span>  
  
5.  <span data-ttu-id="78ef3-114">**[モデル]** ボックスの一覧からモデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="78ef3-114">From the **Model** list, select a model.</span></span>  
  
6.  <span data-ttu-id="78ef3-115">**[バージョン]** ボックスの一覧からバージョンを選択します。</span><span class="sxs-lookup"><span data-stu-id="78ef3-115">From the **Version** list, select a version.</span></span>  
  
7.  <span data-ttu-id="78ef3-116">[**階層メンバーの権限の概要**] ペインで、削除する権限の行を選択します。</span><span class="sxs-lookup"><span data-stu-id="78ef3-116">In the **Hierarchy Member Permission Summary** pane, select the row for the permission that you want to delete.</span></span>  
  
8.  <span data-ttu-id="78ef3-117">[**選択したアクセス許可の削除**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="78ef3-117">Click **Delete selected permission**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="78ef3-118">権限がグループから継承されている場合、ユーザーから権限を削除できません。</span><span class="sxs-lookup"><span data-stu-id="78ef3-118">You cannot remove a permission from a user if the permission is inherited from a group.</span></span> <span data-ttu-id="78ef3-119">グループから権限を削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="78ef3-119">You must remove the permission from the group instead.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78ef3-120">参照</span><span class="sxs-lookup"><span data-stu-id="78ef3-120">See Also</span></span>  
 <span data-ttu-id="78ef3-121">[階層メンバーの権限 &#40;マスターデータサービス&#41;](../../2014/master-data-services/hierarchy-member-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="78ef3-121">[Hierarchy Member Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/hierarchy-member-permissions-master-data-services.md) </span></span>  
 [<span data-ttu-id="78ef3-122">階層メンバーの権限を割り当てる (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="78ef3-122">Assign Hierarchy Member Permissions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/assign-hierarchy-member-permissions-master-data-services.md)  
  
  
