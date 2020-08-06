---
title: ロールの割り当てを変更または削除する (レポート マネージャー) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- removing role assignments
- roles [Reporting Services], assignments
- system roles [Reporting Services]
- modifying role assignments
- deleting role assignments
ms.assetid: 523bdd32-92cb-4b48-a3a9-d58b2385bde7
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d67c5cdb7647d50008f72890e4ac3e3c7eed456e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716073"
---
# <a name="modify-or-delete-a-role-assignment-report-manager"></a><span data-ttu-id="fe0ef-102">ロールの割り当てを変更または削除する (レポート マネージャー)</span><span class="sxs-lookup"><span data-stu-id="fe0ef-102">Modify or Delete a Role Assignment (Report Manager)</span></span>
  <span data-ttu-id="fe0ef-103">ロールの割り当てとは、実行できるタスクがあらかじめ規定されたロール定義に、グループまたはユーザー アカウントをマップすることです。</span><span class="sxs-lookup"><span data-stu-id="fe0ef-103">A role assignment maps a group or user account to a predefined role definition that includes tasks that can be performed.</span></span> <span data-ttu-id="fe0ef-104">ユーザーが実行できる操作の種類は、フォルダー、レポート、モデルなど、コンテンツの種類に基づいて決定されます。</span><span class="sxs-lookup"><span data-stu-id="fe0ef-104">It determines the types of operations that a user can perform relative to a folder, report, model, or other content type.</span></span> <span data-ttu-id="fe0ef-105">ロールの割り当てを作成、変更、または削除するには、レポート マネージャーを使用します。</span><span class="sxs-lookup"><span data-stu-id="fe0ef-105">To create, modify, or delete role assignments, you use Report Manager.</span></span> <span data-ttu-id="fe0ef-106">特定のユーザーまたはグループに対して作成したロールの割り当ては、後で異なるロールを選択することによって変更できます。</span><span class="sxs-lookup"><span data-stu-id="fe0ef-106">After you create a role assignment for a particular user or group, you can modify it later by selecting a different role.</span></span> <span data-ttu-id="fe0ef-107">レポート サーバーに対する権限を取り消したい場合は、ロールの割り当てをレポート サーバーから削除します。</span><span class="sxs-lookup"><span data-stu-id="fe0ef-107">If you want to revoke permissions to a report server, you can delete a role assignment from the report server.</span></span>  
  
 <span data-ttu-id="fe0ef-108">目的によっては、別の方法を用いた方がよい場合もあります。</span><span class="sxs-lookup"><span data-stu-id="fe0ef-108">Depending on your objective, alternative approaches might be more appropriate.</span></span> <span data-ttu-id="fe0ef-109">つまり、新しいロール定義の作成やカスタマイズ、Active Directory 内グループ アカウントのメンバーシップ変更などです。</span><span class="sxs-lookup"><span data-stu-id="fe0ef-109">Examples include customizing or creating a new role definition, or modifying the membership of a group account in Active Directory.</span></span>  
  
 <span data-ttu-id="fe0ef-110">たとえば、ある一連のユーザーが、自分たちのコンテンツを詳細に管理する必要があるとします。これらのユーザーに対して、コンテンツ マネージャーに関連付けられている権限をすべて付与するわけにはいきません。</span><span class="sxs-lookup"><span data-stu-id="fe0ef-110">For example, suppose you have a group of users who need to fully manage their content, but should not have the full set of permissions associated with Content Manager.</span></span> <span data-ttu-id="fe0ef-111">このような場合は、"部門コンテンツ マネージャー" という新しいロール定義を作成し、コンテンツ マネージャーの **[アイテムごとにセキュリティを設定]** を除く、すべてのタスクを含めます。</span><span class="sxs-lookup"><span data-stu-id="fe0ef-111">In this case, you could create a new role definition called Department Content Manager that includes all of the tasks in Content Manager except **Set security policies for items**.</span></span>  
  
 <span data-ttu-id="fe0ef-112">同様に、システム管理者やネットワーク管理者にとっては、レポート マネージャーでロールの割り当てを管理するよりも、Active Directory のグループ アカウントを管理した方が容易であるという場合も考えられます。そのようなときは、グループ アカウントに対するロールの割り当てを 1 つだけ作成し、ユーザーがレポートにアクセスする必要がなくなった時点でグループのメンバーシップを調整することによって、ロールの割り当て管理に伴うオーバーヘッドを低減できます。</span><span class="sxs-lookup"><span data-stu-id="fe0ef-112">Similarly, if you are a system or network administrator and it is easier for you to manage Active Directory group accounts than role assignments in Report Manager, you could reduce the overhead of managing role assignments by creating a single role assignment for a group account, and then adjust group membership when users no longer require access to reports.</span></span>  
  
 <span data-ttu-id="fe0ef-113">ロールの割り当てを変更または削除することが最善の方法であると判断した場合は、必ずシステム ロールの割り当てとアイテム ロールの割り当ての両方を確認してください。</span><span class="sxs-lookup"><span data-stu-id="fe0ef-113">If you determine that modifying or deleting a role assignment is the best approach, remember to check for both system role assignments and item role assignments.</span></span> <span data-ttu-id="fe0ef-114">レポート マネージャーでロールの割り当てを構成する際に使用するページは、ロールの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="fe0ef-114">Each type of role assignment is configured through different pages in Report Manager.</span></span>  
  
### <a name="to-modify-or-delete-a-system-role-assignment"></a><span data-ttu-id="fe0ef-115">システム ロールの割り当てを変更または削除するには</span><span class="sxs-lookup"><span data-stu-id="fe0ef-115">To modify or delete a system role assignment</span></span>  
  
1.  <span data-ttu-id="fe0ef-116">[レポート マネージャー &#40;SSRS ネイティブ モード&#41;](../report-manager-ssrs-native-mode.md) を開始します。</span><span class="sxs-lookup"><span data-stu-id="fe0ef-116">Start [Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md).</span></span>  
  
2.  <span data-ttu-id="fe0ef-117">**[サイトの設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fe0ef-117">Click **Site Settings**.</span></span>  
  
3.  <span data-ttu-id="fe0ef-118">**[セキュリティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fe0ef-118">Click **Security**.</span></span> <span data-ttu-id="fe0ef-119">現在、サーバーまたはスケールアウト配置に対して定義されているシステムレベルのロールの割り当てが、アカウント名ごとに一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="fe0ef-119">All system-level role assignments currently defined for the server or scale-out deployment are listed by account name.</span></span>  
  
4.  <span data-ttu-id="fe0ef-120">変更または削除するロールの割り当てを探します。</span><span class="sxs-lookup"><span data-stu-id="fe0ef-120">Find the role assignment that you want to modify or delete.</span></span>  
  
5.  <span data-ttu-id="fe0ef-121">特定のユーザーまたはグループに対するロールを追加または削除するには、 **[編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fe0ef-121">To add or remove the role for a particular user or group, click **Edit**.</span></span>  
  
6.  <span data-ttu-id="fe0ef-122">ロールの割り当てを削除するには、ユーザーまたはグループ名の隣にあるチェック ボックスをオンにして、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fe0ef-122">To delete a role assignment, click the check box next to the user or group name, and then click **Delete**.</span></span>  
  
### <a name="to-modify-or-delete-an-item-role-assignment"></a><span data-ttu-id="fe0ef-123">アイテム ロールの割り当てを変更または削除するには</span><span class="sxs-lookup"><span data-stu-id="fe0ef-123">To modify or delete an item role assignment</span></span>  
  
1.  <span data-ttu-id="fe0ef-124">**レポート マネージャー** を起動し、ロールの割り当てを編集または削除するアイテムを探します。</span><span class="sxs-lookup"><span data-stu-id="fe0ef-124">Start **Report Manager** and locate the item for which you want to edit or delete a role assignment.</span></span>  
  
2.  <span data-ttu-id="fe0ef-125">アイテムの上にマウス ポインターを移動し、下矢印をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fe0ef-125">Hover over the item, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="fe0ef-126">ドロップダウン メニューの **[セキュリティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fe0ef-126">In the drop-down menu, click **Security**.</span></span>  
  
4.  <span data-ttu-id="fe0ef-127">変更または削除するロールの割り当てを探します。</span><span class="sxs-lookup"><span data-stu-id="fe0ef-127">Find the role assignment that you want to modify or delete.</span></span>  
  
5.  <span data-ttu-id="fe0ef-128">特定のユーザーまたはグループに対するロールを追加または削除するには、 **[編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fe0ef-128">To add or remove the role for a particular user or group, click **Edit**.</span></span>  
  
6.  <span data-ttu-id="fe0ef-129">ロールの割り当てを削除するには、ユーザーまたはグループ名の隣にあるチェック ボックスをオンにして、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fe0ef-129">To delete a role assignment, click the check box next to the user or group name, and then click **Delete**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe0ef-130">参照</span><span class="sxs-lookup"><span data-stu-id="fe0ef-130">See Also</span></span>  
 <span data-ttu-id="fe0ef-131">(create-and-manage-role-assignments.md)</span><span class="sxs-lookup"><span data-stu-id="fe0ef-131">(create-and-manage-role-assignments.md)</span></span>   
 <span data-ttu-id="fe0ef-132">[ロールの割り当て](role-assignments.md) </span><span class="sxs-lookup"><span data-stu-id="fe0ef-132">[Role Assignments](role-assignments.md) </span></span>  
 <span data-ttu-id="fe0ef-133">[[サイトの設定] ページ &#40;レポートマネージャー&#41;](../site-settings-page-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="fe0ef-133">[Site Settings Page &#40;Report Manager&#41;](../site-settings-page-report-manager.md) </span></span>  
 <span data-ttu-id="fe0ef-134">[[新しいシステム ロールの割り当て]: [システム ロールの割り当てを編集] ページ &#40;レポート マネージャー&#41;](../new-system-role-assignments-edit-system-role-assignments-page-report-manager.md)</span><span class="sxs-lookup"><span data-stu-id="fe0ef-134">[New System Role Assignments: Edit System Role Assignments Page &#40;Report Manager&#41;](../new-system-role-assignments-edit-system-role-assignments-page-report-manager.md)</span></span>  
  
  
