---
title: ユーザーまたはグループを削除する (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- deleting groups [Master Data Services]
- groups [Master Data Services], deleting
- users [Master Data Services], deleting
- deleting users [Master Data Services]
ms.assetid: 0bbf9d2c-b826-48bb-8aa9-9905db6e717f
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: be302bc974994d0f4f17a8e61244065c76fa93ca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644508"
---
# <a name="delete-users-or-groups-master-data-services"></a><span data-ttu-id="911c7-102">ユーザーまたはグループを削除する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="911c7-102">Delete Users or Groups (Master Data Services)</span></span>
  <span data-ttu-id="911c7-103">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]にアクセスする必要のなくなったユーザーまたはグループを削除します。</span><span class="sxs-lookup"><span data-stu-id="911c7-103">Delete users or groups when you no longer want them to access [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].</span></span>  
  
 <span data-ttu-id="911c7-104">ユーザーおよびグループを削除する場合、次の点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="911c7-104">Note the following behavior when deleting users and groups:</span></span>  
  
-   <span data-ttu-id="911c7-105">ユーザーが [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]へのアクセスを持つグループのメンバーである場合、そのユーザーは、Active Directory またはローカル グループから削除されるまで [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="911c7-105">If you delete a user who is a member of a group that has access to [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], then the user can still access [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] until you remove the user from the Active Directory or local group.</span></span>  
  
-   <span data-ttu-id="911c7-106">グループを削除した場合、そのメンバーを削除するまで、 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] にアクセスしたことのあるグループのすべてのメンバーは **[ユーザー]** ボックスの一覧に表示されます。</span><span class="sxs-lookup"><span data-stu-id="911c7-106">If you delete a group, all users from the group who have accessed [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] are displayed in the **Users** list until you delete them.</span></span>  
  
-   <span data-ttu-id="911c7-107">セキュリティの変更は、20 分間は MDS [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)] に反映されません。</span><span class="sxs-lookup"><span data-stu-id="911c7-107">Changes to security are not propagated to the MDS [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)] for 20 minutes.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="911c7-108">前提条件</span><span class="sxs-lookup"><span data-stu-id="911c7-108">Prerequisites</span></span>  
 <span data-ttu-id="911c7-109">この手順を実行するには</span><span class="sxs-lookup"><span data-stu-id="911c7-109">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="911c7-110">**[ユーザー/グループの権限]** 機能領域にアクセスするための権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="911c7-110">You must have permission to access the **Users and Group Permissions** functional area.</span></span>  
  
-   <span data-ttu-id="911c7-111">モデル管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="911c7-111">You must be a model administrator.</span></span> <span data-ttu-id="911c7-112">詳細については、「[管理者 &#40;マスターデータサービス&#41;](administrators-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="911c7-112">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-delete-users-or-groups"></a><span data-ttu-id="911c7-113">ユーザーまたはグループを削除するには</span><span class="sxs-lookup"><span data-stu-id="911c7-113">To delete users or groups</span></span>  
  
1.  <span data-ttu-id="911c7-114">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[ユーザー/グループの権限]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="911c7-114">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **User and Group Permissions**.</span></span>  
  
2.  <span data-ttu-id="911c7-115">ユーザーを削除するには、 **[ユーザー]** ページを表示します。</span><span class="sxs-lookup"><span data-stu-id="911c7-115">To delete a user, remain on the **Users** page.</span></span> <span data-ttu-id="911c7-116">グループを削除するには、メニュー バーの **[グループの管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="911c7-116">To delete a group, from the menu bar, click **ManageGroups.**</span></span>  
  
3.  <span data-ttu-id="911c7-117">グリッドで、削除するユーザーまたはグループの行を選択します。</span><span class="sxs-lookup"><span data-stu-id="911c7-117">In the grid,select the row for the user or group that you want to delete.</span></span>  
  
4.  <span data-ttu-id="911c7-118">**[選択したユーザーの削除]** または **[選択したグループの削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="911c7-118">Click **Delete selected user** or **Delete selected group**.</span></span>  
  
5.  <span data-ttu-id="911c7-119">確認のダイアログ ボックスで **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="911c7-119">On the confirmation dialog box, click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="911c7-120">参照</span><span class="sxs-lookup"><span data-stu-id="911c7-120">See Also</span></span>  
 [<span data-ttu-id="911c7-121">セキュリティ (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="911c7-121">Security &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/security-master-data-services.md)  
  
  
