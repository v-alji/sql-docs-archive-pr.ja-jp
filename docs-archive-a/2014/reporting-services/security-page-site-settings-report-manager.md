---
title: '[セキュリティ] ページ、サイトの設定 ( レポートマネージャー) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: acc9a905-90f8-4544-aec6-b2ab3a1b0015
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 997806b8bba92d210a8d108a7101e086f21abb74
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634832"
---
# <a name="security-page-site-settings-report-manager"></a><span data-ttu-id="c8f84-103">[セキュリティ] ページ、サイトの設定 (</span><span class="sxs-lookup"><span data-stu-id="c8f84-103">Security Page (Site Settings.</span></span> <span data-ttu-id="c8f84-104">レポート マネージャー)</span><span class="sxs-lookup"><span data-stu-id="c8f84-104">Report Manager)</span></span>
  <span data-ttu-id="c8f84-105">[セキュリティ] ページは、レポート サーバー サイトへのアクセスを制御するシステム ロールの割り当てを表示するために使用します。</span><span class="sxs-lookup"><span data-stu-id="c8f84-105">Use the Security page to view the system role assignments that control access to the report server site.</span></span> <span data-ttu-id="c8f84-106">システム ロールの割り当ては、レポート サーバー名前空間やフォルダー階層の外の領域でも有効です。</span><span class="sxs-lookup"><span data-stu-id="c8f84-106">System role assignments exist outside of the scope of the report server namespace or folder hierarchy.</span></span> <span data-ttu-id="c8f84-107">システム ロールの割り当てはグローバルであり、特定のアイテムによって変わることがありません。</span><span class="sxs-lookup"><span data-stu-id="c8f84-107">System role assignments are global and cannot vary for specific items.</span></span> <span data-ttu-id="c8f84-108">システム ロールの割り当てによってサポートされる操作には、共有スケジュールの作成と使用、レポート ビルダーの使用、および一部のサーバー機能の既定値の設定が含まれます。</span><span class="sxs-lookup"><span data-stu-id="c8f84-108">Operations that are supported through system role assignments include creating and using shared schedules, using Report Builder, and setting default values for some server features.</span></span>  
  
 <span data-ttu-id="c8f84-109">レポート サーバーのインストール時に、既定のシステム ロールの割り当てが作成されます。</span><span class="sxs-lookup"><span data-stu-id="c8f84-109">A default system role assignment is created when the report server is installed.</span></span> <span data-ttu-id="c8f84-110">このシステム ロールの割り当てによって、ローカルのシステム管理者にレポート サーバー環境を管理する権限が与えられます。</span><span class="sxs-lookup"><span data-stu-id="c8f84-110">This system role assignment grants permissions to local system administrators to manage the report server environment.</span></span> <span data-ttu-id="c8f84-111">ローカルのシステム管理者は、システム ロールの割り当てが削除された場合でも、常にローカル レポート サーバーのセキュリティを設定できます。</span><span class="sxs-lookup"><span data-stu-id="c8f84-111">A local system administrator can always set security for a local report server, even if system role assignments are deleted.</span></span>  
  
 <span data-ttu-id="c8f84-112">レポート ビルダーまたは共有スケジュールにアクセスする必要がある他のすべてのユーザーは、システム ロールの割り当てに割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="c8f84-112">All other users who require access to Report Builder or shared schedules must be assigned to a system role assignment.</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="c8f84-113">ナビゲーション</span><span class="sxs-lookup"><span data-stu-id="c8f84-113">Navigation</span></span>  
 <span data-ttu-id="c8f84-114">ユーザー インターフェイス (UI) のこの場所に移動するには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="c8f84-114">Use the following procedure to navigate to this location in the user interface (UI).</span></span>  
  
###### <a name="to-open-the-security-page-for-site-settings"></a><span data-ttu-id="c8f84-115">[サイトの設定] の [セキュリティ] ページを開くには</span><span class="sxs-lookup"><span data-stu-id="c8f84-115">To open the Security page for Site Settings</span></span>  
  
1.  <span data-ttu-id="c8f84-116">レポート マネージャーを開きます。</span><span class="sxs-lookup"><span data-stu-id="c8f84-116">Open Report Manager.</span></span>  
  
2.  <span data-ttu-id="c8f84-117">ページの上部にある **[サイトの設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c8f84-117">At the top of the page, click **Site Settings**.</span></span> <span data-ttu-id="c8f84-118">この操作により、サイトの [全般] プロパティ ページが開きます。</span><span class="sxs-lookup"><span data-stu-id="c8f84-118">This opens the General Properties page of the site.</span></span>  
  
3.  <span data-ttu-id="c8f84-119">**[セキュリティ]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="c8f84-119">Select the **Security** tab.</span></span>  
  
## <a name="options"></a><span data-ttu-id="c8f84-120">Options</span><span class="sxs-lookup"><span data-stu-id="c8f84-120">Options</span></span>  
 <span data-ttu-id="c8f84-121">**削除**</span><span class="sxs-lookup"><span data-stu-id="c8f84-121">**Delete**</span></span>  
 <span data-ttu-id="c8f84-122">既存のロールの割り当てを削除する場合にクリックします。</span><span class="sxs-lookup"><span data-stu-id="c8f84-122">Click to delete an existing role assignment.</span></span> <span data-ttu-id="c8f84-123">削除するグループ名またはユーザー名の横のチェック ボックスをオンにしてから、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c8f84-123">Before clicking **Delete**, select the check box next to the group or user name that you want to remove.</span></span> <span data-ttu-id="c8f84-124">1 つしか残っていないロールの割り当ては削除できません。</span><span class="sxs-lookup"><span data-stu-id="c8f84-124">You cannot delete a role assignment if it is the only one remaining.</span></span> <span data-ttu-id="c8f84-125">ロールの割り当てを削除しても、グループ アカウントやユーザー アカウント、またはロールの定義は削除されません。</span><span class="sxs-lookup"><span data-stu-id="c8f84-125">Deleting a role assignment does not delete a group or user account or role definitions.</span></span>  
  
 <span data-ttu-id="c8f84-126">**新しいロールの割り当て**</span><span class="sxs-lookup"><span data-stu-id="c8f84-126">**New Role Assignment**</span></span>  
 <span data-ttu-id="c8f84-127">クリックすると、[新しいシステム ロールの割り当て] ページが開きます。このページは、レポート サーバー サイトの新たなシステム ロールの割り当てを作成するために使用します。</span><span class="sxs-lookup"><span data-stu-id="c8f84-127">Click to open the New System Role Assignments page, which is used to create additional system role assignments for the report server site.</span></span> <span data-ttu-id="c8f84-128">詳細については、「[新しいシステムロールの割り当て: [システムロールの割り当てを編集] ページ &#40;レポートマネージャー&#41;](../../2014/reporting-services/new-system-role-assignments-edit-system-role-assignments-page-report-manager.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c8f84-128">For more information, see [New System Role Assignments: Edit System Role Assignments Page &#40;Report Manager&#41;](../../2014/reporting-services/new-system-role-assignments-edit-system-role-assignments-page-report-manager.md).</span></span>  
  
 <span data-ttu-id="c8f84-129">**[編集]**</span><span class="sxs-lookup"><span data-stu-id="c8f84-129">**Edit**</span></span>  
 <span data-ttu-id="c8f84-130">クリックすると、[システム ロールの割り当てを編集] ページが開きます。このページは、レポート サーバー サイトの個別のシステム ロールの割り当てを編集するために使用します。</span><span class="sxs-lookup"><span data-stu-id="c8f84-130">Click to open the Edit System Role Assignments page, which is used to edit individual system role assignments for the report server site.</span></span> <span data-ttu-id="c8f84-131">詳細については、「[新しいシステムロールの割り当て: [システムロールの割り当てを編集] ページ &#40;レポートマネージャー&#41;](../../2014/reporting-services/new-system-role-assignments-edit-system-role-assignments-page-report-manager.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c8f84-131">For more information, see [New System Role Assignments: Edit System Role Assignments Page &#40;Report Manager&#41;](../../2014/reporting-services/new-system-role-assignments-edit-system-role-assignments-page-report-manager.md).</span></span>  
  
 <span data-ttu-id="c8f84-132">**[グループまたはユーザー]**</span><span class="sxs-lookup"><span data-stu-id="c8f84-132">**Group or User**</span></span>  
 <span data-ttu-id="c8f84-133">既存のロールの割り当ての一部であるグループおよびユーザーが一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="c8f84-133">Lists the groups and users that are part of an existing role assignment.</span></span> <span data-ttu-id="c8f84-134">この列には、現在のフォルダーに対する既存のロールの割り当てが定義されているグループおよびユーザーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c8f84-134">Existing role assignments for the current folder are defined for the groups and users that appear in this column.</span></span> <span data-ttu-id="c8f84-135">ロールの割り当ての詳細を表示または編集するには、グループ名またはユーザー名の横にある **[編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c8f84-135">Click **Edit** next to a group or user name to view or edit role assignment details.</span></span>  
  
 <span data-ttu-id="c8f84-136">**ロール**</span><span class="sxs-lookup"><span data-stu-id="c8f84-136">**Roles**</span></span>  
 <span data-ttu-id="c8f84-137">既存のロールの割り当ての一部であるロールの定義が 1 つ以上表示されます。</span><span class="sxs-lookup"><span data-stu-id="c8f84-137">Lists one or more role definitions that are part of an existing role assignment.</span></span> <span data-ttu-id="c8f84-138">1 つのグループ アカウントまたは 1 つのユーザー アカウントに複数のロールが割り当てられている場合、そのグループまたはユーザーは、すべてのロールに属するすべてのタスクを実行できます。</span><span class="sxs-lookup"><span data-stu-id="c8f84-138">If multiple roles are assigned to a group or user account, that group or user can perform all tasks that belong to all roles.</span></span> <span data-ttu-id="c8f84-139">各ロールでサポートされている一連のタスクを表示するには、を使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] します。</span><span class="sxs-lookup"><span data-stu-id="c8f84-139">To view the set of tasks that each role supports, use [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)].</span></span> <span data-ttu-id="c8f84-140">レポート マネージャーでロールを表示、作成、変更、または削除することはできません。</span><span class="sxs-lookup"><span data-stu-id="c8f84-140">You cannot view, create, modify, or delete roles in Report Manager.</span></span> <span data-ttu-id="c8f84-141">手順については、「[ロールを作成、削除、または変更する &#40;Management Studio&#41;](security/role-definitions-create-delete-or-modify.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c8f84-141">For instructions, see [Create, Delete, or Modify a Role &#40;Management Studio&#41;](security/role-definitions-create-delete-or-modify.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8f84-142">参照</span><span class="sxs-lookup"><span data-stu-id="c8f84-142">See Also</span></span>  
 <span data-ttu-id="c8f84-143">[レポートマネージャーの F1 ヘルプ](../../2014/reporting-services/report-manager-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="c8f84-143">[Report Manager F1 Help](../../2014/reporting-services/report-manager-f1-help.md) </span></span>  
 [<span data-ttu-id="c8f84-144">ネイティブ モードのレポート サーバーに対する権限の許可</span><span class="sxs-lookup"><span data-stu-id="c8f84-144">Granting Permissions on a Native Mode Report Server</span></span>](security/granting-permissions-on-a-native-mode-report-server.md)  
  
  
