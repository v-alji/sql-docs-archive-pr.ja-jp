---
title: '[新しいシステムロールの割り当て]: [システムロールの割り当てを編集] ページ (レポートマネージャー) |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 62a22ab9-1eb4-4ce5-8dd7-06b5ed2d9a2a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6e04ec18b8ee27c5897156753c1e4f7991991eae
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632958"
---
# <a name="new-system-role-assignments-edit-system-role-assignments-page-report-manager"></a><span data-ttu-id="dcb9f-102">[新しいシステム ロールの割り当て]: [システム ロールの割り当てを編集] ページ (レポート マネージャー)</span><span class="sxs-lookup"><span data-stu-id="dcb9f-102">New System Role Assignments: Edit System Role Assignments Page (Report Manager)</span></span>
  <span data-ttu-id="dcb9f-103">レポート サーバーのセキュリティを定義する場合には、[システム ロールの新規割り当て] ページまたは [システム ロールの割り当てを編集] ページを使用します。</span><span class="sxs-lookup"><span data-stu-id="dcb9f-103">Use the New System Role Assignments or Edit System Role Assignments page to define security for the report server.</span></span> <span data-ttu-id="dcb9f-104">すべてのセキュリティはロールの割り当てによって定義され、この割り当てを通じて、実行できるタスクに特定のユーザーまたはグループがマップされます。</span><span class="sxs-lookup"><span data-stu-id="dcb9f-104">All security is defined through role assignments that map specific users or groups to the tasks that they can perform.</span></span> <span data-ttu-id="dcb9f-105">タスク リストは、ロールの割り当ての作成時に選択するロールの定義を示します。</span><span class="sxs-lookup"><span data-stu-id="dcb9f-105">The task list is represented as a role definition that you select when making the role assignment.</span></span>  
  
 <span data-ttu-id="dcb9f-106">システム レベルでは、作成または変更するロールの割り当てがレポート サーバー全体に適用されます。</span><span class="sxs-lookup"><span data-stu-id="dcb9f-106">At the system level, the role assignments that you create or modify apply to the report server as a whole.</span></span> <span data-ttu-id="dcb9f-107">たとえば、共有スケジュールはシステム全体で使用されるため、共有スケジュールを作成する機能はシステム レベルで指定されます。</span><span class="sxs-lookup"><span data-stu-id="dcb9f-107">For example, the ability to create shared schedules is specified at the system level because shared schedules are used throughout the system.</span></span>  
  
 <span data-ttu-id="dcb9f-108">Reporting Services には既定で 2 つの定義済みのシステム レベルのロールが用意されています。</span><span class="sxs-lookup"><span data-stu-id="dcb9f-108">By default, Reporting Services provides two predefined system level roles:</span></span>  
  
-   <span data-ttu-id="dcb9f-109">システム ユーザーには、ユーザーがレポート サーバーのプロパティと共有スケジュールを表示したり、レポート定義を実行したりできるようにするタスクが含まれています。レポート定義の実行は、レポート サーバーにパブリッシュされたクリックスルー レポートをユーザーが表示できるようにするタスクです。</span><span class="sxs-lookup"><span data-stu-id="dcb9f-109">System User includes tasks that allow users to view report server properties and shared schedules, and to execute report definitions, which allows users to view clickthrough reports that have been published to the report server.</span></span> <span data-ttu-id="dcb9f-110">ほとんどのユーザーがこのロールに割り当てられる必要があります。</span><span class="sxs-lookup"><span data-stu-id="dcb9f-110">Most users should be assigned to this role.</span></span>  
  
-   <span data-ttu-id="dcb9f-111">システム管理者には、共有スケジュールの作成および管理、サーバー プロパティの設定、他のユーザーに対するシステム レベルのロールの割り当ての作成などのタスクが含まれます。</span><span class="sxs-lookup"><span data-stu-id="dcb9f-111">System Administrator includes tasks for creating and managing shared schedules, setting server properties, and creating system-level role assignments for other users.</span></span> <span data-ttu-id="dcb9f-112">このレベルの権限が必要なユーザーは少数です。</span><span class="sxs-lookup"><span data-stu-id="dcb9f-112">Few users require permissions at this level.</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="dcb9f-113">ナビゲーション</span><span class="sxs-lookup"><span data-stu-id="dcb9f-113">Navigation</span></span>  
 <span data-ttu-id="dcb9f-114">ユーザー インターフェイス (UI) のこの場所に移動するには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="dcb9f-114">Use the following procedure to navigate to this location in the user interface (UI).</span></span>  
  
###### <a name="to-open-the-new-system-role-assignments-or-edit-system-role-assignments-page"></a><span data-ttu-id="dcb9f-115">[新しいシステム ロールの割り当て] ページまたは [システム ロールの割り当てを編集] ページを開くには</span><span class="sxs-lookup"><span data-stu-id="dcb9f-115">To open the New System Role Assignments or Edit System Role Assignments page</span></span>  
  
1.  <span data-ttu-id="dcb9f-116">レポート マネージャーを開きます。</span><span class="sxs-lookup"><span data-stu-id="dcb9f-116">Open Report Manager.</span></span>  
  
2.  <span data-ttu-id="dcb9f-117">ページの右上隅の **[サイトの設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dcb9f-117">At the top of the page, in the right-hand corner, click **Site Settings**.</span></span> <span data-ttu-id="dcb9f-118">この操作により、サイトの [全般] プロパティ ページが開きます。</span><span class="sxs-lookup"><span data-stu-id="dcb9f-118">This opens the General properties page for the site.</span></span>  
  
3.  <span data-ttu-id="dcb9f-119">[**セキュリティ**] タブを選択します。このページにアクセスするには、コンテンツマネージャーとシステム管理者のアクセス許可が必要です。</span><span class="sxs-lookup"><span data-stu-id="dcb9f-119">Select the **Security** tab. You must have Content Manager and System Administrator permissions to access this page.</span></span>  
  
4.  <span data-ttu-id="dcb9f-120">新しいロールの割り当てを作成する場合は、ツール バーの **[新しいロールの割り当て]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dcb9f-120">To create a new role assignment, click **New Role Assignment** in the toolbar.</span></span> <span data-ttu-id="dcb9f-121">既存のロールの割り当てを編集する場合は、[セキュリティ] プロパティ ページで、グループまたはユーザーの隣にある **[編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dcb9f-121">To edit an existing role assignment, click **Edit** next to a group or user on the Security properties page.</span></span>  
  
## <a name="options"></a><span data-ttu-id="dcb9f-122">Options</span><span class="sxs-lookup"><span data-stu-id="dcb9f-122">Options</span></span>  
 <span data-ttu-id="dcb9f-123">**[グループまたはユーザー]**</span><span class="sxs-lookup"><span data-stu-id="dcb9f-123">**Group or User**</span></span>  
 <span data-ttu-id="dcb9f-124">ドメインのグループ アカウント名またはユーザー アカウント名を入力します。</span><span class="sxs-lookup"><span data-stu-id="dcb9f-124">Type the name of a group or user account in your domain.</span></span> <span data-ttu-id="dcb9f-125">レポート サーバーがローカル アカウントで実行されている場合は、ローカルのグループまたはユーザーを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dcb9f-125">If the report server is running under a local account, you must specify local groups or users.</span></span> <span data-ttu-id="dcb9f-126">レポート サーバーがドメイン アカウントで実行されている場合は、ドメイン グループまたはドメイン ユーザーを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dcb9f-126">If the report server is running under a domain account, you must specify domain groups or users.</span></span> <span data-ttu-id="dcb9f-127">アカウントは、<アカウントの形式で入力し \<domain> \\ \> ます。</span><span class="sxs-lookup"><span data-stu-id="dcb9f-127">Enter the account in this format: \<domain>\\<account\>.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dcb9f-128">このボックスは、[新しいロールの割り当て] ページでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="dcb9f-128">This box is available only on the New Role Assignment page.</span></span>  
  
 <span data-ttu-id="dcb9f-129">**ロール**</span><span class="sxs-lookup"><span data-stu-id="dcb9f-129">**Roles**</span></span>  
 <span data-ttu-id="dcb9f-130">他のユーザーに割り当てることができるシステム レベルのロールを指定します。</span><span class="sxs-lookup"><span data-stu-id="dcb9f-130">Provides a list of system-level roles that you can assign to other users.</span></span> <span data-ttu-id="dcb9f-131">1 つのロールの割り当てに複数のロールを指定できます。</span><span class="sxs-lookup"><span data-stu-id="dcb9f-131">You can specify multiple roles for a single role assignment.</span></span>  
  
 <span data-ttu-id="dcb9f-132">レポート マネージャーでは、各ロールのタスクは表示されず、タスクを追加または変更することもできません。</span><span class="sxs-lookup"><span data-stu-id="dcb9f-132">Report Manager does not display the tasks in each role or provide a way to add or modify the tasks.</span></span> <span data-ttu-id="dcb9f-133">ロールは定義されているとおりに使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dcb9f-133">You must use the roles as they are defined.</span></span> <span data-ttu-id="dcb9f-134">ロールを作成、変更、または削除するには、を使用し [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="dcb9f-134">To create, modify, or delete roles, use [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)].</span></span> <span data-ttu-id="dcb9f-135">詳細については、「 [ロールを作成、削除、または変更する &#40;Management Studio&#41;](security/role-definitions-create-delete-or-modify.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dcb9f-135">For more information, see [Create, Delete, or Modify a Role &#40;Management Studio&#41;](security/role-definitions-create-delete-or-modify.md).</span></span>  
  
 <span data-ttu-id="dcb9f-136">[!INCLUDE[ssExpressEd2005](../includes/ssexpressed2005-md.md)] with Advanced Services を使用している場合、提供されている既定のロールを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dcb9f-136">Note that if you are using [!INCLUDE[ssExpressEd2005](../includes/ssexpressed2005-md.md)] with Advanced Services, you must use the default roles that are provided.</span></span>  
  
 <span data-ttu-id="dcb9f-137">**説明**</span><span class="sxs-lookup"><span data-stu-id="dcb9f-137">**Descriptions**</span></span>  
 <span data-ttu-id="dcb9f-138">ロールに関する詳細を表示します。</span><span class="sxs-lookup"><span data-stu-id="dcb9f-138">Shows additional information about the role.</span></span> <span data-ttu-id="dcb9f-139">システム ユーザーやシステム管理者などの定義済みロールに関しては、各ロールでサポートされているタスクの要約が説明として提供されます。</span><span class="sxs-lookup"><span data-stu-id="dcb9f-139">For predefined roles such as System User or System Administrator, the description summarizes the tasks that each role supports.</span></span>  
  
 <span data-ttu-id="dcb9f-140">**ロールの割り当ての削除**</span><span class="sxs-lookup"><span data-stu-id="dcb9f-140">**Delete Role Assignment**</span></span>  
 <span data-ttu-id="dcb9f-141">ユーザーまたはグループの既存のロールの割り当てを削除する場合にクリックします。</span><span class="sxs-lookup"><span data-stu-id="dcb9f-141">Click to delete an existing role assignment for a user or a group.</span></span> <span data-ttu-id="dcb9f-142">残っているロールの割り当てが 1 つのみである場合、そのロールの割り当てを削除することはできません (各アイテムは、ロールの割り当てを少なくとも 1 つ保持している必要があります)。</span><span class="sxs-lookup"><span data-stu-id="dcb9f-142">You cannot delete a role assignment if it is the only one left (each item must have a minimum of one role assignment).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dcb9f-143">このボタンは、[ロールの割り当てを編集] ページでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="dcb9f-143">This button is available only on the Edit Role Assignment page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcb9f-144">参照</span><span class="sxs-lookup"><span data-stu-id="dcb9f-144">See Also</span></span>  
 <span data-ttu-id="dcb9f-145">[レポートマネージャーの F1 ヘルプ](../../2014/reporting-services/report-manager-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="dcb9f-145">[Report Manager F1 Help](../../2014/reporting-services/report-manager-f1-help.md) </span></span>  
 <span data-ttu-id="dcb9f-146">[ロールの割り当て](security/role-assignments.md) </span><span class="sxs-lookup"><span data-stu-id="dcb9f-146">[Role Assignments](security/role-assignments.md) </span></span>  
 [<span data-ttu-id="dcb9f-147">ロールの定義</span><span class="sxs-lookup"><span data-stu-id="dcb9f-147">Role Definitions</span></span>](security/role-definitions.md)  
  
  
