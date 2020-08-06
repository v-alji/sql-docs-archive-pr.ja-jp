---
title: ロールの割り当て | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- users [Reporting Services]
- roles [Reporting Services]
- role-based security [Reporting Services], role assignments
- groups [Reporting Services]
- security [Reporting Services], role assignments
ms.assetid: 600e112c-1897-48a6-93c0-6e9f3f12dc01
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f156a009dfce8d91c3d3c8460160a4fdad62b573
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641445"
---
# <a name="role-assignments"></a><span data-ttu-id="06994-102">ロールの割り当て</span><span class="sxs-lookup"><span data-stu-id="06994-102">Role Assignments</span></span>
  <span data-ttu-id="06994-103">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]では、 *”ロール”* の割り当てにより、格納されているアイテムおよびレポート サーバー自体にアクセスできるかどうかが決まります。</span><span class="sxs-lookup"><span data-stu-id="06994-103">In [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], *role assignments* determine access to stored items and to the report server itself.</span></span> <span data-ttu-id="06994-104">ロールの割り当ては以下の要素で構成されています。</span><span class="sxs-lookup"><span data-stu-id="06994-104">A role assignment has the following parts:</span></span>  
  
-   <span data-ttu-id="06994-105">アクセスを制御するセキュリティ保護可能なアイテム。</span><span class="sxs-lookup"><span data-stu-id="06994-105">A securable item for which you want to control access.</span></span> <span data-ttu-id="06994-106">セキュリティ保護可能なアイテムの例として、フォルダー、レポート、リソースがあります。</span><span class="sxs-lookup"><span data-stu-id="06994-106">Examples of securable items include folders, reports, and resources.</span></span>  
  
-   <span data-ttu-id="06994-107">Windows セキュリティまたはその他の認証メカニズムにより認証できるユーザー アカウントまたはグループ アカウント。</span><span class="sxs-lookup"><span data-stu-id="06994-107">A user or group account that can be authenticated by Windows security or another authentication mechanism.</span></span>  
  
-   <span data-ttu-id="06994-108">タスクのセットを定義するロールの定義。</span><span class="sxs-lookup"><span data-stu-id="06994-108">Role definitions that define a set of tasks.</span></span> <span data-ttu-id="06994-109">ロールの定義の例としては、 **システム管理者**、 **コンテンツ マネージャー**、 **パブリッシャー**があります。</span><span class="sxs-lookup"><span data-stu-id="06994-109">Examples of role definitions include **System Administrator**, **Content Manager**, and **Publisher**.</span></span>  
  
 <span data-ttu-id="06994-110">ロールの割り当ては、フォルダー階層内で継承されます。</span><span class="sxs-lookup"><span data-stu-id="06994-110">Role assignments are inherited within the folder hierarchy.</span></span> <span data-ttu-id="06994-111">あるフォルダーに対して定義されたロールの割り当ては、そのフォルダーに含まれるすべてのレポート、共有データ ソース、リソース、およびサブフォルダーに自動的に継承されます。</span><span class="sxs-lookup"><span data-stu-id="06994-111">The role assignment that is defined for a folder is automatically inherited by all reports, shared data sources, resources, and subfolders contained within that folder.</span></span> <span data-ttu-id="06994-112">個別のアイテムにロールの割り当てを定義することで、継承されるセキュリティをオーバーライドすることができます。</span><span class="sxs-lookup"><span data-stu-id="06994-112">You can override inherited security by defining role assignments for individual items.</span></span> <span data-ttu-id="06994-113">フォルダー階層のすべての部分が、少なくとも 1 つのロールの割り当てによってセキュリティ保護されるようにしてください。</span><span class="sxs-lookup"><span data-stu-id="06994-113">All parts of the folder hierarchy must be secured by at least one role assignment.</span></span> <span data-ttu-id="06994-114">セキュリティで保護されていないアイテムを作成したり、セキュリティで保護されていないアイテムを作成するように設定を操作することはできません。</span><span class="sxs-lookup"><span data-stu-id="06994-114">You cannot create an unsecured item or manipulate settings in a way that produces an unsecured item.</span></span>  
  
 <span data-ttu-id="06994-115">フォルダー B に対する **パブリッシャー** ロールにグループおよび特定のユーザーをマップするロールの割り当ての図を次に示します。</span><span class="sxs-lookup"><span data-stu-id="06994-115">The following diagram illustrates a role assignment that maps a group and a specific user to the **Publisher** role for Folder B.</span></span>  
  
 <span data-ttu-id="06994-116">![ロールの割り当ての図](../media/report-securityarch.gif "ロールの割り当ての図")</span><span class="sxs-lookup"><span data-stu-id="06994-116">![Role assignments diagram](../media/report-securityarch.gif "Role assignments diagram")</span></span>  
<span data-ttu-id="06994-117">ロールの割り当ての図</span><span class="sxs-lookup"><span data-stu-id="06994-117">Role assignments diagram</span></span>  
  
## <a name="system-level-and-item-level-role-assignments"></a><span data-ttu-id="06994-118">システムレベルおよびアイテムレベルのロールの割り当て</span><span class="sxs-lookup"><span data-stu-id="06994-118">System-Level and Item-Level Role Assignments</span></span>  
 <span data-ttu-id="06994-119">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] におけるロールベースのセキュリティは、次のレベルに分類されます。</span><span class="sxs-lookup"><span data-stu-id="06994-119">Role-based security in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] is organized into the following levels:</span></span>  
  
-   <span data-ttu-id="06994-120">アイテムレベルのロールの割り当ては、レポート サーバーのフォルダー階層内にあるレポート、フォルダー、レポート モデル、共有データ ソース、およびリソースに対するアクセスを制御します。</span><span class="sxs-lookup"><span data-stu-id="06994-120">Item-level role assignments control access to reports, folders, report models, shared data sources, and resources in the report server folder hierarchy.</span></span> <span data-ttu-id="06994-121">アイテムレベルのロールの割り当ては、特定のアイテムまたは [ホーム] フォルダーに対するロールの割り当てを作成するときに定義されます。</span><span class="sxs-lookup"><span data-stu-id="06994-121">Item-level role assignments are defined when create a role assignment on a specific item or on the Home folder.</span></span>  
  
-   <span data-ttu-id="06994-122">システム ロールの割り当ては、サーバー全体を対象とする操作を承認します (たとえば、ジョブの管理はシステムレベルの操作です)。</span><span class="sxs-lookup"><span data-stu-id="06994-122">System role assignments authorize operations that are scoped to the server as a whole (for example, the ability to manage jobs is a system level operation).</span></span> <span data-ttu-id="06994-123">システム ロールの割り当ては、システム管理者と同じではありません。</span><span class="sxs-lookup"><span data-stu-id="06994-123">A system role assignment is not the equivalent of a system administrator.</span></span> <span data-ttu-id="06994-124">システム ロールの割り当てでは、レポート サーバーのフル コントロールを許可する権限は付与されません。</span><span class="sxs-lookup"><span data-stu-id="06994-124">It does not confer advanced permissions that grant full control of a report server.</span></span>  
  
 <span data-ttu-id="06994-125">システム ロールの割り当てでは、フォルダー階層内のアイテムに対するアクセスは承認されません。</span><span class="sxs-lookup"><span data-stu-id="06994-125">A system role assignment does not authorize access to items in the folder hierarchy.</span></span> <span data-ttu-id="06994-126">システムレベルとアイテムレベルのセキュリティは、相互排他的です。</span><span class="sxs-lookup"><span data-stu-id="06994-126">System and item security are mutually exclusive.</span></span> <span data-ttu-id="06994-127">特定のユーザーはまたはグループについて、レポート サーバーに対する十分なアクセスを提供するには、システムレベルとアイテムレベルのロールの割り当てを両方とも作成することが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="06994-127">For any given user or group, you might need to create both a system-level and item-level role assignment to provide sufficient access to a report server.</span></span>  
  
## <a name="users-and-groups-in-role-assignments"></a><span data-ttu-id="06994-128">ロールの割り当てにおけるユーザーとグループ</span><span class="sxs-lookup"><span data-stu-id="06994-128">Users and Groups in Role Assignments</span></span>  
 <span data-ttu-id="06994-129">ロールの割り当てには、ドメイン アカウントであるユーザー アカウントまたはグループ アカウントを指定します。</span><span class="sxs-lookup"><span data-stu-id="06994-129">The users or group accounts that you specify in role assignments are domain accounts.</span></span> <span data-ttu-id="06994-130">レポート サーバーからは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows ドメイン (カスタム セキュリティ拡張機能を使用している場合は別のセキュリティ モデル) のユーザーおよびグループの参照は行われますが、作成や管理は行われません。</span><span class="sxs-lookup"><span data-stu-id="06994-130">The report server references, but does not create or manage, users and groups from a [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows domain (or another security model if you are using a custom security extension).</span></span>  
  
 <span data-ttu-id="06994-131">ある特定のアイテムに適用されるすべてのロールの割り当ての中で、同じユーザーまたはグループを重複して指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="06994-131">Of all the role assignments that apply to any given item, no two can specify the same user or group.</span></span> <span data-ttu-id="06994-132">あるユーザー アカウントがグループ アカウントのメンバーでもあり、両方のアカウントに対してロールの割り当てを行っている場合、そのユーザーは両方のロールの割り当てに対するタスクを合わせたものを利用できます。</span><span class="sxs-lookup"><span data-stu-id="06994-132">If a user account is also a member of a group account, and you have role assignments for both, the combined set of tasks for both role assignments are available to the user.</span></span>  
  
 <span data-ttu-id="06994-133">既にロールの割り当ての一部であるグループにユーザーを追加するとき、そのユーザーに対するロールの割り当てを有効にするには、インターネット インフォメーション サービス (IIS) を再設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="06994-133">When you add a user to a group that is already part of a role assignment, you must reset Internet Information Services (IIS) for the new role assignment to take effect for that user.</span></span>  
  
## <a name="predefined-role-assignments"></a><span data-ttu-id="06994-134">定義済みロールの割り当て</span><span class="sxs-lookup"><span data-stu-id="06994-134">Predefined Role Assignments</span></span>  
 <span data-ttu-id="06994-135">既定では、ローカル管理者によるレポート サーバーの管理を許可する定義済みのロールの割り当てが実装されます。</span><span class="sxs-lookup"><span data-stu-id="06994-135">By default, predefined role assignments are implemented that allow local administrators to manage the report server.</span></span> <span data-ttu-id="06994-136">ロールの割り当てを追加して、他のユーザーにアクセス権を与える必要があります。</span><span class="sxs-lookup"><span data-stu-id="06994-136">You must add additional role assignments to grant access to other users.</span></span>  
  
 <span data-ttu-id="06994-137">既定のセキュリティを提供する定義済みのロールの割り当ての詳細については、「 [定義済みロール](role-definitions-predefined-roles.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="06994-137">For more information about the predefined role assignments that provide default security, see [Predefined Roles](role-definitions-predefined-roles.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06994-138">参照</span><span class="sxs-lookup"><span data-stu-id="06994-138">See Also</span></span>  
 <span data-ttu-id="06994-139">[ロール &#40;Management Studio の作成、削除、または変更&#41;](role-definitions-create-delete-or-modify.md) </span><span class="sxs-lookup"><span data-stu-id="06994-139">[Create, Delete, or Modify a Role &#40;Management Studio&#41;](role-definitions-create-delete-or-modify.md) </span></span>  
 <span data-ttu-id="06994-140">[レポートサーバーへのユーザーアクセスを許可する &#40;レポートマネージャー&#41;](grant-user-access-to-a-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="06994-140">[Grant User Access to a Report Server &#40;Report Manager&#41;](grant-user-access-to-a-report-server.md) </span></span>  
 <span data-ttu-id="06994-141">[ロールの割り当てを変更または削除する &#40;レポートマネージャー&#41;](role-assignments-modify-or-delete.md) </span><span class="sxs-lookup"><span data-stu-id="06994-141">[Modify or Delete a Role Assignment &#40;Report Manager&#41;](role-assignments-modify-or-delete.md) </span></span>  
 <span data-ttu-id="06994-142">[Sharepoint サイト上のレポートサーバーアイテムに対する権限を設定するには、SharePoint 統合モードで Reporting Services &#40;&#41;](set-permissions-for-report-server-items-on-a-sharepoint-site.md) </span><span class="sxs-lookup"><span data-stu-id="06994-142">[Set Permissions for Report Server Items on a SharePoint Site &#40;Reporting Services in SharePoint Integrated Mode&#41;](set-permissions-for-report-server-items-on-a-sharepoint-site.md) </span></span>  
 [<span data-ttu-id="06994-143">ネイティブ モードのレポート サーバーに対する権限の許可</span><span class="sxs-lookup"><span data-stu-id="06994-143">Granting Permissions on a Native Mode Report Server</span></span>](granting-permissions-on-a-native-mode-report-server.md)  
  
  
