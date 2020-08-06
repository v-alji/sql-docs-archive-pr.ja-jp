---
title: ユーザーおよびグループ (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- users [Master Data Services]
- groups [Master Data Services]
- users [Master Data Services], about users
- groups [Master Data Services], about groups
ms.assetid: ed08dd2d-248e-4b68-91d4-e9961cb50eed
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: efad65bf273d58b4f60b98d050a8b99705cb00ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743325"
---
# <a name="users-and-groups-master-data-services"></a><span data-ttu-id="ea012-102">ユーザーおよびグループ (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="ea012-102">Users and Groups (Master Data Services)</span></span>
  <span data-ttu-id="ea012-103">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Web アプリケーションにアクセスするには、Windows ドメイン アカウント、または [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] がインストールされているサーバー コンピューター上のアカウントがユーザーに必要です。</span><span class="sxs-lookup"><span data-stu-id="ea012-103">To access the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] web application a user must have a Windows domain account or an account on the server computer where [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] is installed.</span></span> <span data-ttu-id="ea012-104">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] へのアクセスを許可するには、次のいずれかを実行します。</span><span class="sxs-lookup"><span data-stu-id="ea012-104">To grant access to [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] you can either:</span></span>  
  
-   <span data-ttu-id="ea012-105">ユーザー アカウントをドメインまたはローカル グループに追加するか、 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]でグループの一覧にグループを追加します。</span><span class="sxs-lookup"><span data-stu-id="ea012-105">Add the user account to a domain or local group and then add the group to the list of groups in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].</span></span>  
  
-   <span data-ttu-id="ea012-106">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]でユーザーの一覧にユーザー アカウントを追加します。</span><span class="sxs-lookup"><span data-stu-id="ea012-106">Add the user account to the list of users in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ea012-107">ユーザーが [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]へのアクセス権があるグループに所属している場合、そのユーザーが初めて [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] または MDS [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)]にアクセスすると、そのユーザーの一覧にユーザー名が自動的に追加されます。</span><span class="sxs-lookup"><span data-stu-id="ea012-107">When a user belongs to a group that has access to [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], the user's name is automatically added to the list of users the first time the user accesses [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] or the MDS [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)].</span></span>  
  
 <span data-ttu-id="ea012-108">UI の **[エクスプローラー]** 機能領域で操作を実行するには、グループまたはユーザーに **[エクスプローラー]** 機能領域へのアクセス権、およびモデル オブジェクトへの権限が割り当てられている必要があります。</span><span class="sxs-lookup"><span data-stu-id="ea012-108">To take action within the **Explorer** functional area of the UI, the group or user must be assigned access to the **Explorer** functional area and assigned permission to model objects.</span></span>  
  
 <span data-ttu-id="ea012-109">ユーザーまたはグループにその他の機能領域へのアクセス権が必要な場合、そのユーザーまたはグループは管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="ea012-109">If a user or group needs access to other functional areas, the user or group must be an administrator.</span></span> <span data-ttu-id="ea012-110">詳細については、「[管理者 &#40;マスターデータサービス&#41;](administrators-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ea012-110">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
## <a name="best-practice"></a><span data-ttu-id="ea012-111">推奨事項</span><span class="sxs-lookup"><span data-stu-id="ea012-111">Best Practice</span></span>  
 <span data-ttu-id="ea012-112">管理を簡素化するには、グループを作成し、各グループに機能領域およびモデル オブジェクトへの権限を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="ea012-112">To simplify administration, create groups and assign each group permission to functional areas and model objects.</span></span> <span data-ttu-id="ea012-113">また、 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] の UI にアクセスすることなくグループに対してユーザーの追加または削除を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="ea012-113">You can then add and remove users from the groups without accessing the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] UI.</span></span>  
  
 <span data-ttu-id="ea012-114">個々のユーザーに追加の権限を割り当てたり、ユーザーを [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]にアクセスできる複数のグループに含めたりしないでください。</span><span class="sxs-lookup"><span data-stu-id="ea012-114">Do not assign additional permissions to an individual user, and do not include a user in multiple groups that have access to [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].</span></span> <span data-ttu-id="ea012-115">また、特定のメンバーに対するグループのアクセスを制限する必要がない限り、階層メンバーの権限は使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="ea012-115">In addition, do not use hierarchy member permissions unless you want a group to have limited access to specific members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea012-116">参照</span><span class="sxs-lookup"><span data-stu-id="ea012-116">See Also</span></span>  
 <span data-ttu-id="ea012-117">[ユーザー &#40;マスターデータサービスを追加&#41;](../../2014/master-data-services/add-a-user-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="ea012-117">[Add a User &#40;Master Data Services&#41;](../../2014/master-data-services/add-a-user-master-data-services.md) </span></span>  
 <span data-ttu-id="ea012-118">[グループ &#40;マスターデータサービスを追加&#41;](../../2014/master-data-services/add-a-group-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="ea012-118">[Add a Group &#40;Master Data Services&#41;](../../2014/master-data-services/add-a-group-master-data-services.md) </span></span>  
 <span data-ttu-id="ea012-119">[マスターデータサービス &#40;のユーザーまたはグループを削除&#41;](../../2014/master-data-services/delete-users-or-groups-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="ea012-119">[Delete Users or Groups &#40;Master Data Services&#41;](../../2014/master-data-services/delete-users-or-groups-master-data-services.md) </span></span>  
 [<span data-ttu-id="ea012-120">ユーザーのアクセス許可のテスト (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="ea012-120">Test a User's Permissions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/test-a-user-s-permissions-master-data-services.md)  
  
  
