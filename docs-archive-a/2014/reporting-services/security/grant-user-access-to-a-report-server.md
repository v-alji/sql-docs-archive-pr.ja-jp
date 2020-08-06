---
title: レポートサーバーへのユーザーアクセスを許可する (レポートマネージャー) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- removing role assignments
- permissions [Reporting Services], granting report server access
- roles [Reporting Services], assignments
- modifying role assignments
- deleting role assignments
ms.assetid: 2144c020-3253-4b47-8cda-e14c928bb471
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: bceaa648827d756e2b301662ce281b37a76d6839
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713765"
---
# <a name="grant-user-access-to-a-report-server-report-manager"></a><span data-ttu-id="157cd-102">レポート サーバーへのユーザー アクセスを許可する (レポート マネージャー)</span><span class="sxs-lookup"><span data-stu-id="157cd-102">Grant User Access to a Report Server (Report Manager)</span></span>
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="157cd-103">では、ロール ベースのセキュリティを使用して、レポート サーバーへのアクセス権がユーザーに付与されます。</span><span class="sxs-lookup"><span data-stu-id="157cd-103">uses role-based security to grant user access to a report server.</span></span> <span data-ttu-id="157cd-104">新しいレポート サーバーをインストールした直後は、ローカル Administrators グループに属するユーザーにのみ、レポート サーバーのコンテンツと操作に対する権限が与えられます。</span><span class="sxs-lookup"><span data-stu-id="157cd-104">On a new report server installation, only users who are members of the local Administrators group have permissions to report server content and operations.</span></span> <span data-ttu-id="157cd-105">他のユーザーがレポート サーバーにアクセスできるようにするには、ロール割り当てを作成して、ユーザーまたはグループ アカウントを、一連のタスクが指定された定義済みのロールにマップする必要があります。</span><span class="sxs-lookup"><span data-stu-id="157cd-105">To make the report server available to other users, you must create role assignments that map  user or group accounts to a predefined role that specifies a collection of tasks.</span></span>  
  
 <span data-ttu-id="157cd-106">**SharePoint モードのレポート サーバー:** SharePoint 統合モード用に構成されたレポート サーバーの場合は、SharePoint サイトから、SharePoint の権限を使ってアクセスを構成します。</span><span class="sxs-lookup"><span data-stu-id="157cd-106">**SharePoint mode report servers:** For a report server that is configured for SharePoint integrated mode, you configure access from a SharePoint site using SharePoint permissions.</span></span> <span data-ttu-id="157cd-107">レポート サーバーのコンテンツや操作にアクセスできるかどうかは、SharePoint サイト上の権限レベルによって決まります。</span><span class="sxs-lookup"><span data-stu-id="157cd-107">Permission levels on the SharePoint site determine access to report server content and operations.</span></span> <span data-ttu-id="157cd-108">SharePoint サイトでの権限を付与できるのはサイト管理者だけです。</span><span class="sxs-lookup"><span data-stu-id="157cd-108">You must be a site administrator to grant permissions on a SharePoint site.</span></span> <span data-ttu-id="157cd-109">詳細については、「 [SharePoint サイトのレポート サーバー アイテムに対する権限の付与](granting-permissions-on-report-server-items-on-a-sharepoint-site.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="157cd-109">For more information, see [Granting Permissions on Report Server Items on a SharePoint Site](granting-permissions-on-report-server-items-on-a-sharepoint-site.md).</span></span>  
  
 <span data-ttu-id="157cd-110">**ネイティブ モードのレポート サーバー:** このトピックでは、ネイティブ モードで構成されているレポート サーバーと、ロールにユーザーを割り当てるレポート マネージャーの使用方法に注目します。</span><span class="sxs-lookup"><span data-stu-id="157cd-110">**Native mode report servers:** This topic is focused on a report server that is configured for native mode and the use of Report Manager to assign users to a role.</span></span> <span data-ttu-id="157cd-111">ロールには次の 2 種類があります。</span><span class="sxs-lookup"><span data-stu-id="157cd-111">There are two types of roles:</span></span>  
  
-   <span data-ttu-id="157cd-112">アイテムレベルのロール : レポート サーバーのコンテンツ、サブスクリプション、レポート処理、レポート履歴などを表示、追加、および管理するためのロール。</span><span class="sxs-lookup"><span data-stu-id="157cd-112">Item-level roles are used to view, add, and manage report server content, subscriptions, report processing, and report history.</span></span> <span data-ttu-id="157cd-113">アイテム レベルのロール割り当ては、ルート ノード ([ホーム] フォルダー)、または階層内でそれより下位にある特定のフォルダーやアイテムに対して定義できます。</span><span class="sxs-lookup"><span data-stu-id="157cd-113">Item-level role assignments are defined on the root node (the Home folder) or on specific folders or items farther down the hierarchy.</span></span>  
  
-   <span data-ttu-id="157cd-114">システムレベルのロール : 特定のアイテムではなく、サイト全体にわたる操作へのアクセスを許可します。</span><span class="sxs-lookup"><span data-stu-id="157cd-114">System-level roles grant access to site-wide operations that are not bound to any specific item.</span></span> <span data-ttu-id="157cd-115">たとえば、レポート ビルダーや共有スケジュールを使用することが含まれます。</span><span class="sxs-lookup"><span data-stu-id="157cd-115">Examples include using Report Builder and using shared schedules.</span></span>  
  
     <span data-ttu-id="157cd-116">この 2 種類のロールは相互補完的な関係にあり、組み合わせて使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="157cd-116">The two types of roles complement each other and should be used together.</span></span> <span data-ttu-id="157cd-117">そのため、レポート サーバーにユーザーを追加するには、2 段階の処理が必要となります。</span><span class="sxs-lookup"><span data-stu-id="157cd-117">For this reason, adding a user to a report server is a two-part operation.</span></span> <span data-ttu-id="157cd-118">ユーザーをアイテムレベルのロールに割り当てる場合は、同時にシステムレベルのロールにも割り当てる必要があります。</span><span class="sxs-lookup"><span data-stu-id="157cd-118">If you assign a user to an item-level role, you should also assign them to a system-level role.</span></span> <span data-ttu-id="157cd-119">ユーザーをロールに割り当てる際は、既に定義されているロールを選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="157cd-119">When assigning a user to a role, you must select a role that is already defined.</span></span> <span data-ttu-id="157cd-120">ロールを作成、変更、または削除するには、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] を使用します。</span><span class="sxs-lookup"><span data-stu-id="157cd-120">To create, modify, or delete roles, use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span> <span data-ttu-id="157cd-121">詳細については、「 [ロールを作成、削除、または変更する &#40;Management Studio&#41;](role-definitions-create-delete-or-modify.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="157cd-121">For more information, see [Create, Delete, or Modify a Role &#40;Management Studio&#41;](role-definitions-create-delete-or-modify.md).</span></span>  
  
## <a name="before-you-start"></a><span data-ttu-id="157cd-122">開始する前に</span><span class="sxs-lookup"><span data-stu-id="157cd-122">Before you start</span></span>  
 <span data-ttu-id="157cd-123">ネイティブ モードのレポート サーバーにユーザーを追加する場合は、あらかじめ次の点を確認してください。</span><span class="sxs-lookup"><span data-stu-id="157cd-123">Review the following list before adding users to a native mode report server.</span></span>  
  
-   <span data-ttu-id="157cd-124">レポート サーバー コンピューターのローカル Administrators グループのメンバーとしてログインする必要があります。</span><span class="sxs-lookup"><span data-stu-id="157cd-124">You must be a member of the local Administrators group on the report server computer.</span></span> <span data-ttu-id="157cd-125">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] を [!INCLUDE[wiprlhlong](../../includes/wiprlhlong-md.md)] または Windows Server 2008 に配置する場合、レポート サーバーをローカルで管理するには追加の構成が必要となります。</span><span class="sxs-lookup"><span data-stu-id="157cd-125">If you are deploying [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] on [!INCLUDE[wiprlhlong](../../includes/wiprlhlong-md.md)] or Windows Server 2008, additional configuration is required before you can administer a report server locally.</span></span> <span data-ttu-id="157cd-126">詳細については、「 [ローカル管理用のネイティブ モードのレポート サーバー &#40;SSRS&#41; の構成](../report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="157cd-126">For more information, see [Configure a Native Mode Report Server for Local Administration &#40;SSRS&#41;](../report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md).</span></span>  
  
-   <span data-ttu-id="157cd-127">このタスクを他のユーザーに委任する場合は、ユーザー アカウントをコンテンツ マネージャー ロールとシステム管理者ロールにマップするためのロール割り当てを作成します。</span><span class="sxs-lookup"><span data-stu-id="157cd-127">To delegate this task to other users, create role assignments that map user accounts to Content Manager and System Administrator roles.</span></span> <span data-ttu-id="157cd-128">コンテンツ マネージャーとシステム管理者の権限を与えられたユーザーは、レポート サーバーにユーザーを追加できます。</span><span class="sxs-lookup"><span data-stu-id="157cd-128">Users who have Content Manager and System Administrator permissions can add users to a report server.</span></span>  
  
-   <span data-ttu-id="157cd-129">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] で、システム ロールおよびユーザー ロールに対して定義されているロールを確認し、それぞれのロールにどのようなタスクが含まれているかを確認します。</span><span class="sxs-lookup"><span data-stu-id="157cd-129">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], view the predefined roles for System Roles and User Roles so that you are familiar with the kinds of tasks in each role.</span></span> <span data-ttu-id="157cd-130">レポート マネージャーではタスクの説明が表示されません。そのため、ユーザーを追加する前に、各ロールについて理解しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="157cd-130">Task descriptions are not visible in Report Manager, so you will want to be familiar with the roles before you begin adding users.</span></span>  
  
-   <span data-ttu-id="157cd-131">必要であれば、ロールをカスタマイズするか、新しいロールを定義して必要なタスクを追加します。</span><span class="sxs-lookup"><span data-stu-id="157cd-131">Optionally, customize the roles or define additional roles to include the collection of tasks that you require.</span></span> <span data-ttu-id="157cd-132">たとえば、個々のアイテムにカスタム セキュリティ設定を使用する場合は、フォルダーの閲覧権限を付与した新しいロール定義を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="157cd-132">For example, if you plan to use custom security settings for individual items, you might want to create a new role definition that grants view-access to folders.</span></span>  
  
### <a name="to-add-a-user-or-group-to-a-system-role"></a><span data-ttu-id="157cd-133">ユーザーまたはグループをシステム ロールに追加するには</span><span class="sxs-lookup"><span data-stu-id="157cd-133">To add a user or group to a system role</span></span>  
  
1.  <span data-ttu-id="157cd-134">[レポート マネージャー &#40;SSRS ネイティブ モード&#41;](../report-manager-ssrs-native-mode.md) を開始します。</span><span class="sxs-lookup"><span data-stu-id="157cd-134">Start [Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md).</span></span>  
  
2.  <span data-ttu-id="157cd-135">**[サイトの設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="157cd-135">Click **Site Settings**.</span></span>  
  
3.  <span data-ttu-id="157cd-136">**[セキュリティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="157cd-136">Click **Security**.</span></span>  
  
4.  <span data-ttu-id="157cd-137">**[新しいロールの割り当て]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="157cd-137">Click **New Role Assignment**.</span></span>  
  
5.  <span data-ttu-id="157cd-138">[**グループ名またはユーザー名**] に、Windows ドメインユーザーまたはグループアカウントを<アカウントの形式で入力し \<domain> \\ \> ます。</span><span class="sxs-lookup"><span data-stu-id="157cd-138">In **Group or user name**, enter a Windows domain user or group account in this format: \<domain>\\<account\>.</span></span> <span data-ttu-id="157cd-139">フォーム認証やカスタム セキュリティを使用している場合は、その環境に合った適切な形式でユーザー アカウントまたはグループ アカウントを指定します。</span><span class="sxs-lookup"><span data-stu-id="157cd-139">If you are using forms authentication or custom security, specify the user or group account in the format that is correct for your deployment.</span></span>  
  
6.  <span data-ttu-id="157cd-140">システム ロールを選択し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="157cd-140">Select a system role, and then click **OK**.</span></span>  
  
     <span data-ttu-id="157cd-141">ロールは累積されます。したがって、システム管理者とシステム ユーザーを両方とも選択した場合、そのユーザーまたはグループは、これら両方のロールのタスクを実行できるようになります。</span><span class="sxs-lookup"><span data-stu-id="157cd-141">Roles are cumulative, so if you select both System Administrator and System User, a user or group will be able to perform the tasks in both roles.</span></span>  
  
7.  <span data-ttu-id="157cd-142">割り当てを作成するユーザーまたはグループが他にもある場合は、以上の手順を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="157cd-142">Repeat to create assignments for additional users or groups.</span></span>  
  
### <a name="to-add-a-user-or-group-to-an-item-role"></a><span data-ttu-id="157cd-143">ユーザーまたはグループをアイテム ロールに追加するには</span><span class="sxs-lookup"><span data-stu-id="157cd-143">To add a user or group to an item role</span></span>  
  
1.  <span data-ttu-id="157cd-144">**レポート マネージャー** を起動し、ユーザーまたはグループを追加するレポート アイテムを探します。</span><span class="sxs-lookup"><span data-stu-id="157cd-144">Start **Report Manager** and locate the report item for which you want to add a user or group.</span></span>  
  
2.  <span data-ttu-id="157cd-145">アイテムの上にマウス ポインターを移動し、下矢印をクリックします。</span><span class="sxs-lookup"><span data-stu-id="157cd-145">Hover over the item, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="157cd-146">ドロップダウン メニューの **[セキュリティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="157cd-146">In the drop-down menu, click **Security**.</span></span>  
  
4.  <span data-ttu-id="157cd-147">**[新しいロールの割り当て]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="157cd-147">Click **New Role Assignment**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="157cd-148">アイテムが現在、親アイテムからセキュリティを継承している場合は、ツール バーの **[アイテムのセキュリティを編集]** をクリックしてセキュリティの設定を変更します。</span><span class="sxs-lookup"><span data-stu-id="157cd-148">If an item currently inherits security from a parent item, click **Edit Item Security** in the toolbar to change the security settings.</span></span> <span data-ttu-id="157cd-149">**[新しいロールの割り当て]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="157cd-149">Then click **New Role Assignment**.</span></span>  
  
5.  <span data-ttu-id="157cd-150">[**グループ名またはユーザー名**] に、Windows ドメインユーザーまたはグループアカウントを<アカウントの形式で入力し \<domain> \\ \> ます。</span><span class="sxs-lookup"><span data-stu-id="157cd-150">In **Group or user name**, enter a Windows domain user or group account in this format: \<domain>\\<account\>.</span></span> <span data-ttu-id="157cd-151">フォーム認証やカスタム セキュリティを使用している場合は、その環境に合った適切な形式でユーザー アカウントまたはグループ アカウントを指定します。</span><span class="sxs-lookup"><span data-stu-id="157cd-151">If you are using forms authentication or custom security, specify the user or group account in the format that is correct for your deployment.</span></span>  
  
6.  <span data-ttu-id="157cd-152">ユーザーまたはグループがアイテムにアクセスする方法を表すロールの定義を 1 つ以上選択して、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="157cd-152">Select one or more role definitions that describe how the user or group should access the item, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="157cd-153">割り当てを作成するユーザーまたはグループが他にもある場合は、以上の手順を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="157cd-153">Repeat to create assignments for additional users or groups.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="157cd-154">参照</span><span class="sxs-lookup"><span data-stu-id="157cd-154">See Also</span></span>  
 <span data-ttu-id="157cd-155">(create-and-manage-role-assignments.md)</span><span class="sxs-lookup"><span data-stu-id="157cd-155">(create-and-manage-role-assignments.md)</span></span>   
 <span data-ttu-id="157cd-156">[[新しいロールの割り当て]: [ロールの割り当ての編集] ページ &#40;レポートマネージャー&#41;](../new-role-assignment-edit-role-assignment-page-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="157cd-156">[New Role Assignment: Edit Role Assignment Page &#40;Report Manager&#41;](../new-role-assignment-edit-role-assignment-page-report-manager.md) </span></span>  
 <span data-ttu-id="157cd-157">[[セキュリティ] プロパティページ、アイテム &#40;レポートマネージャー&#41;](../security-properties-page-items-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="157cd-157">[Security Properties Page, Items &#40;Report Manager&#41;](../security-properties-page-items-report-manager.md) </span></span>  
 <span data-ttu-id="157cd-158">[ロールの割り当て](role-assignments.md) </span><span class="sxs-lookup"><span data-stu-id="157cd-158">[Role Assignments](role-assignments.md) </span></span>  
 [<span data-ttu-id="157cd-159">ロールの定義</span><span class="sxs-lookup"><span data-stu-id="157cd-159">Role Definitions</span></span>](role-definitions.md)  
  
  
