---
title: ロールの割り当てを作成および管理する | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- removing role assignments
- roles [Reporting Services], assignments
- security [Reporting Services], role assignments
- modifying role assignments
- deleting role assignments
ms.assetid: 086d0987-b43c-4834-8372-e08fb4b432f8
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2064e2a6d4dda99ed6b8b61de363b84d073d8ef9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715085"
---
# <a name="create-and-manage-role-assignments"></a><span data-ttu-id="b200c-102">ロールの割り当てを作成および管理する</span><span class="sxs-lookup"><span data-stu-id="b200c-102">Create and Manage Role Assignments</span></span>
  <span data-ttu-id="b200c-103">*ロールの割り当て* は、ユーザーまたはグループが特定のレポート サーバー アイテムにアクセスできるか、または操作を実行できるかを決定するセキュリティ ポリシーです。</span><span class="sxs-lookup"><span data-stu-id="b200c-103">A *role assignment* is a security policy that determines whether a user or group can access a specific report server item or perform an operation.</span></span> <span data-ttu-id="b200c-104">ロールの割り当ては、ユーザーまたはグループのアカウント名 1 つと、1 つ以上のロールの定義で構成されます。</span><span class="sxs-lookup"><span data-stu-id="b200c-104">A role assignment consists of a single user or group account name and one or more role definitions.</span></span>  
  
 <span data-ttu-id="b200c-105">ロールの割り当ては、 *アイテムレベル* または *システムレベル*で有効です。</span><span class="sxs-lookup"><span data-stu-id="b200c-105">Role assignments are scoped to the *item level* or *system level*.</span></span>  
  
-   <span data-ttu-id="b200c-106">アイテムレベルのロールの割り当ては、必ずレポート サーバーのフォルダー階層にある特定のアイテムまたは分岐のコンテキストで作成されます。</span><span class="sxs-lookup"><span data-stu-id="b200c-106">An item-level role assignment is always created in the context of a specific item or branch in the report server folder hierarchy.</span></span> <span data-ttu-id="b200c-107">特定のフォルダーまたはアイテムに移動して、そのフォルダーまたはアイテム用のロールの割り当てを作成します。</span><span class="sxs-lookup"><span data-stu-id="b200c-107">You navigate to a specific folder or item to create a role assignment for it.</span></span>  
  
-   <span data-ttu-id="b200c-108">システムレベルのロールの割り当てでは、レポート サーバー サイト全体に影響するタスクを実行する権限が、選択したユーザーに与えられます。</span><span class="sxs-lookup"><span data-stu-id="b200c-108">System-level role assignments give selected users the capability to perform tasks that affect the report server site as a whole.</span></span> <span data-ttu-id="b200c-109">これらのタスクには、共有スケジュールの作成、ジョブの管理、レポート ビルダーでのレポートの処理、およびプロパティの設定が含まれています。</span><span class="sxs-lookup"><span data-stu-id="b200c-109">These tasks include creating shared schedules, managing jobs, processing reports in Report Builder, and setting properties.</span></span> <span data-ttu-id="b200c-110">システムレベルのセキュリティでは、レポート サーバー フォルダー階層内のアイテムに対するアクセスは設定されません。</span><span class="sxs-lookup"><span data-stu-id="b200c-110">System-level security does not convey access to items in the report server folder hierarchy.</span></span>  
  
## <a name="creating-an-item-level-role-assignment"></a><span data-ttu-id="b200c-111">アイテムレベルのロールの割り当ての作成</span><span class="sxs-lookup"><span data-stu-id="b200c-111">Creating an Item-level Role Assignment</span></span>  
 <span data-ttu-id="b200c-112">ロールの割り当てを作成または管理するには、レポート マネージャーで、セキュリティで保護するアイテムの [セキュリティ] プロパティ ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="b200c-112">To create or manage role assignments, use Report Manager and open the Security property pages of the item that you want to secure.</span></span>  
  
 <span data-ttu-id="b200c-113">ロールの割り当ては、レポート サーバーへのアクセスを必要とするユーザーまたはグループのアカウントごとに作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b200c-113">You must create a separate role assignment for each user or group account that requires access to the report server.</span></span> <span data-ttu-id="b200c-114">レポート サーバーが存在するドメインとは別のドメインにアカウントがある場合、そのドメイン名を含めます。</span><span class="sxs-lookup"><span data-stu-id="b200c-114">If the account is on a domain other than the one that contains the report server, include the domain name.</span></span> <span data-ttu-id="b200c-115">アカウントの指定後、1 つ以上のロールの定義を選択できます。</span><span class="sxs-lookup"><span data-stu-id="b200c-115">After you specify an account, you can choose one or more role definitions.</span></span> <span data-ttu-id="b200c-116">ロールの定義は追加式になっています。</span><span class="sxs-lookup"><span data-stu-id="b200c-116">The role definitions are additive.</span></span> <span data-ttu-id="b200c-117">特定のユーザーまたはグループのロールの割り当てで、すべての定義のすべてのタスクを組み合わせて使用できます。</span><span class="sxs-lookup"><span data-stu-id="b200c-117">The combined set of all tasks from all definitions are supported in the assignment for a particular user or group.</span></span>  
  
 <span data-ttu-id="b200c-118">広範囲にアクセスできるようにするには、フォルダー階層の上位のアイテム (たとえば、ルート ノードの [ホーム]) を選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b200c-118">To enable widespread access, you should choose an item that is high in the folder hierarchy (for example, the root node Home).</span></span> <span data-ttu-id="b200c-119">その後、下位のロールの割り当てを作成し、フォルダー階層の特定の領域を制限できます。</span><span class="sxs-lookup"><span data-stu-id="b200c-119">You can then create subsequent role assignments to lock down specific areas of the folder hierarchy.</span></span>  
  
 <span data-ttu-id="b200c-120">ロールの割り当てを作成するには、レポート サーバー コンピューターのローカル管理者グループのメンバーであることが必要です。</span><span class="sxs-lookup"><span data-stu-id="b200c-120">You must be a member of the local Administrator's group on the report server computer to create a role assignment.</span></span> <span data-ttu-id="b200c-121">この役割は、別のユーザーを **コンテンツ マネージャー** ロールに割り当てることで委任できます。</span><span class="sxs-lookup"><span data-stu-id="b200c-121">You can delegate that responsibility by assigning other users to the **Content Manager** role.</span></span>  
  
 <span data-ttu-id="b200c-122">詳細については、「[レポートサーバーへのユーザーアクセスを許可する &#40;レポートマネージャー&#41;](grant-user-access-to-a-report-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b200c-122">For more information, see [Grant User Access to a Report Server &#40;Report Manager&#41;](grant-user-access-to-a-report-server.md).</span></span>  
  
## <a name="creating-a-system-level-role-assignment"></a><span data-ttu-id="b200c-123">システムレベルのロールの割り当ての作成</span><span class="sxs-lookup"><span data-stu-id="b200c-123">Creating a System-level Role Assignment</span></span>  
 <span data-ttu-id="b200c-124">システムレベルのロールの割り当てを作成または管理するには、レポート マネージャーで [サイトの設定] ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="b200c-124">To create or manage a system-level role assignment, use Report Manager and open the Site Settings page.</span></span>  
  
 <span data-ttu-id="b200c-125">システムレベルのロールの割り当てとアイテムレベルのロールの割り当ては関連しています。</span><span class="sxs-lookup"><span data-stu-id="b200c-125">System-level and item-level role assignments go together.</span></span> <span data-ttu-id="b200c-126">アイテムレベルでロールが割り当てられているユーザーまたはグループごとに、システムレベルのロールの割り当てを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b200c-126">You should create a system-level role assignment for each user or group that has an item-level role assignment.</span></span>  
  
 <span data-ttu-id="b200c-127">システムレベルのロールの割り当てには広範囲の権限が含まれますが、アイテムレベルのロールの割り当てに組み込まれている権限は含まれません。</span><span class="sxs-lookup"><span data-stu-id="b200c-127">System-level role assignments include a wide range of permissions, but they do not include permissions that are part of an item-level role assignment.</span></span> <span data-ttu-id="b200c-128">コンピューター上のシステム権限とは異なり、レポート サーバーのシステム ロールは、考えられるすべての操作を含んだ包括的な権限を与えるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="b200c-128">In contrast with system permissions on a computer, system roles in Reporting Servers do not convey overarching permissions that include the full set of all possible operations.</span></span> <span data-ttu-id="b200c-129">システムレベルのロールの割り当ては、レポート サーバー サイトで有効な一連のタスクのみが対象です。</span><span class="sxs-lookup"><span data-stu-id="b200c-129">Instead, system-level role assignments are simply a set of tasks that are scoped to the report server site.</span></span> <span data-ttu-id="b200c-130">システム ロールの割り当てによって与えられる権限では、ユーザーがアプリケーション プロパティ (ホーム ページのイメージやタイトルなど) を表示できるか、共有スケジュールを表示または管理できるか、あるいはレポート ビルダーを使用できるかどうかを決定します。</span><span class="sxs-lookup"><span data-stu-id="b200c-130">Permissions that are conveyed through system role assignments determine whether users can view application properties (such as the image or title of the Home page), view or manage shared schedules, or use Report Builder.</span></span>  
  
 <span data-ttu-id="b200c-131">詳細については、「 [レポート サーバーへのユーザー アクセスを許可する (レポート マネージャー)](grant-user-access-to-a-report-server.md) 」と「 [定義済みロール](role-definitions-predefined-roles.md)で有効です。</span><span class="sxs-lookup"><span data-stu-id="b200c-131">For more information, see [Grant User Access to a Report Server &#40;Report Manager&#41;](grant-user-access-to-a-report-server.md) and [Predefined Roles](role-definitions-predefined-roles.md).</span></span>  
  
## <a name="modifying-a-role-assignment"></a><span data-ttu-id="b200c-132">ロールの割り当ての変更</span><span class="sxs-lookup"><span data-stu-id="b200c-132">Modifying a Role Assignment</span></span>  
 <span data-ttu-id="b200c-133">ロールの割り当ては、いつでも変更できます。</span><span class="sxs-lookup"><span data-stu-id="b200c-133">You can modify a role assignment at any time.</span></span> <span data-ttu-id="b200c-134">変更は、ロールの割り当てを保存すると有効になります。</span><span class="sxs-lookup"><span data-stu-id="b200c-134">Your changes take effect when you save the role assignment.</span></span> <span data-ttu-id="b200c-135">ユーザー セッションは、ロールの割り当ての変更による影響を受けません。</span><span class="sxs-lookup"><span data-stu-id="b200c-135">User sessions are not affected by role assignment changes.</span></span> <span data-ttu-id="b200c-136">ユーザーがレポートを開いているときに、ロールの割り当てを変更してアクセスを拒否しても、セッションがアクティブである間はユーザーはレポートを使用し続けることができます。</span><span class="sxs-lookup"><span data-stu-id="b200c-136">If a user has a report open, and you modify a role assignment to deny access, the user can continue using the report as long as the session is active.</span></span>  
  
 <span data-ttu-id="b200c-137">既にロールの割り当ての一部であるグループにユーザー アカウントを追加する場合、そのユーザー アカウントがグループ アカウント ポリシーを通じてアイテムにアクセスできるようになるまでに遅れが生じます。</span><span class="sxs-lookup"><span data-stu-id="b200c-137">If you add a user account to a group that is already part of a role assignment, there will be a delay before the user account is able to access items through the group account policies.</span></span> <span data-ttu-id="b200c-138">この遅れの原因は、インターネット インフォメーション サービス (IIS) による認証トークンのキャッシュにあります。</span><span class="sxs-lookup"><span data-stu-id="b200c-138">This delay is caused by Internet Information Services (IIS) caching of authentication tokens.</span></span> <span data-ttu-id="b200c-139">トークンが更新されるまで待つことも (通常は 15 分間)、IIS をリセットしてキャッシュを直ちに更新することもできます。</span><span class="sxs-lookup"><span data-stu-id="b200c-139">You can either wait for the tokens to refresh (typically, the wait period is fifteen minutes) or you can reset IIS to update the cache immediately.</span></span>  
  
 <span data-ttu-id="b200c-140">ロールの割り当ては、一度に 1 つのみ変更できます。</span><span class="sxs-lookup"><span data-stu-id="b200c-140">You can only modify one role assignment at a time.</span></span> <span data-ttu-id="b200c-141">グローバルな検索および置換操作を実行して、ロールの定義名またはロールの割り当ての設定を変更したり、特定のユーザーまたはグループを含むすべてのロールの割り当てを検索することはできません。</span><span class="sxs-lookup"><span data-stu-id="b200c-141">You cannot perform a global search-and-replace operation to change role definition names or role assignment settings, or to find all the role assignments that include a specific user or group.</span></span>  
  
## <a name="deleting-a-role-assignment"></a><span data-ttu-id="b200c-142">ロールの割り当ての削除</span><span class="sxs-lookup"><span data-stu-id="b200c-142">Deleting a Role Assignment</span></span>  
 <span data-ttu-id="b200c-143">削除する各ロールの割り当てのチェック ボックスをオンにして、 **[削除]** をクリックすることにより、ロールの割り当てを削除できます。</span><span class="sxs-lookup"><span data-stu-id="b200c-143">You can delete role assignments by selecting the checkbox by each assignment you want to delete, and then clicking **Delete**.</span></span> <span data-ttu-id="b200c-144">また、 **[親のセキュリティに戻す]** をクリックして、ロールの割り当てを削除することもできます。</span><span class="sxs-lookup"><span data-stu-id="b200c-144">You can also delete role assignments by clicking **Revert to Parent Security**.</span></span> <span data-ttu-id="b200c-145">このボタンをクリックすると、アイテムの既存のロールの割り当てが削除され、代わりに親アイテムから提供されるロールの割り当てが使用されます。</span><span class="sxs-lookup"><span data-stu-id="b200c-145">When you click this button, the existing role assignments for the item are deleted, and those that are provided through a parent item are used instead.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b200c-146">参照</span><span class="sxs-lookup"><span data-stu-id="b200c-146">See Also</span></span>  
 <span data-ttu-id="b200c-147">[レポートサーバーへのユーザーアクセスを許可する &#40;レポートマネージャー&#41;](grant-user-access-to-a-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="b200c-147">[Grant User Access to a Report Server &#40;Report Manager&#41;](grant-user-access-to-a-report-server.md) </span></span>  
 <span data-ttu-id="b200c-148">[ロールの割り当てを変更または削除する &#40;レポートマネージャー&#41;](role-assignments-modify-or-delete.md) </span><span class="sxs-lookup"><span data-stu-id="b200c-148">[Modify or Delete a Role Assignment &#40;Report Manager&#41;](role-assignments-modify-or-delete.md) </span></span>  
 <span data-ttu-id="b200c-149">[ロールの割り当て](role-assignments.md) </span><span class="sxs-lookup"><span data-stu-id="b200c-149">[Role Assignments](role-assignments.md) </span></span>  
 <span data-ttu-id="b200c-150">[ロールの定義](role-definitions.md) </span><span class="sxs-lookup"><span data-stu-id="b200c-150">[Role Definitions](role-definitions.md) </span></span>  
 <span data-ttu-id="b200c-151">[定義済みロール](role-definitions-predefined-roles.md) </span><span class="sxs-lookup"><span data-stu-id="b200c-151">[Predefined Roles](role-definitions-predefined-roles.md) </span></span>  
 [<span data-ttu-id="b200c-152">ネイティブ モードのレポート サーバーに対する権限の許可</span><span class="sxs-lookup"><span data-stu-id="b200c-152">Granting Permissions on a Native Mode Report Server</span></span>](granting-permissions-on-a-native-mode-report-server.md)  
  
  
