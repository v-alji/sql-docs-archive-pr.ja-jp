---
title: '[セキュリティ] プロパティページ、アイテム (レポートマネージャー) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 351b8503-354f-4b1b-a7ac-f1245d978da0
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 297ae2ceefad89d64c59b5da25d51d541917c894
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634827"
---
# <a name="security-properties-page-items-report-manager"></a><span data-ttu-id="13e5e-102">[セキュリティのプロパティ] ページ、アイテム (レポート マネージャー)</span><span class="sxs-lookup"><span data-stu-id="13e5e-102">Security Properties Page, Items (Report Manager)</span></span>
  <span data-ttu-id="13e5e-103">[セキュリティのプロパティ] ページを使用すると、フォルダー、レポート、モデル、リソース、および共有データ ソースへのアクセスを決定するセキュリティ設定の表示や変更を行えます。</span><span class="sxs-lookup"><span data-stu-id="13e5e-103">Use the Security properties page to view or modify the security settings that determine access to folders, reports, models, resources, and shared data sources.</span></span> <span data-ttu-id="13e5e-104">このページは、セキュリティ保護の権限の対象となるアイテムに対して利用できます。</span><span class="sxs-lookup"><span data-stu-id="13e5e-104">This page is available for items that you have permission to secure.</span></span>  
  
 <span data-ttu-id="13e5e-105">アイテムへのアクセスは、グループまたはユーザーが実行できるタスクを指定するロールの割り当てによって定義されます。</span><span class="sxs-lookup"><span data-stu-id="13e5e-105">Access to items is defined through role assignments that specify the tasks that a group or user can perform.</span></span> <span data-ttu-id="13e5e-106">ロールの割り当ては、1 つのユーザー名またはグループ名、および一連のタスクを指定する 1 つ以上のロールの定義で構成されています。</span><span class="sxs-lookup"><span data-stu-id="13e5e-106">A role assignment consists of one user or group name and one or more role definitions that specify a collection of tasks.</span></span>  
  
 <span data-ttu-id="13e5e-107">セキュリティ設定は、ルート フォルダーからサブフォルダーおよびサブフォルダー内のアイテムにまで継承されます。</span><span class="sxs-lookup"><span data-stu-id="13e5e-107">Security settings are inherited from the root folder down to subfolders and items within those folders.</span></span> <span data-ttu-id="13e5e-108">継承されたセキュリティを明示的に破棄しない限り、親アイテムのセキュリティ コンテキストがサブフォルダーおよびアイテムに継承されます。</span><span class="sxs-lookup"><span data-stu-id="13e5e-108">Unless you explicitly break inherited security, subfolders and items inherit the security context of a parent item.</span></span> <span data-ttu-id="13e5e-109">中間層のフォルダーのセキュリティ ポリシーを再定義した場合、サブフォルダーを含む子アイテムに新しいセキュリティ設定が有効になります。</span><span class="sxs-lookup"><span data-stu-id="13e5e-109">If you redefine a security policy for a folder in the middle of the hierarchy, all its child items, including subfolders, assume the new security settings.</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="13e5e-110">ナビゲーション</span><span class="sxs-lookup"><span data-stu-id="13e5e-110">Navigation</span></span>  
 <span data-ttu-id="13e5e-111">ユーザー インターフェイス (UI) のこの場所に移動するには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="13e5e-111">Use the following procedure to navigate to this location in the user interface (UI).</span></span>  
  
###### <a name="to-open-the-security-page-for-an-item"></a><span data-ttu-id="13e5e-112">アイテムの [セキュリティ] ページを開くには</span><span class="sxs-lookup"><span data-stu-id="13e5e-112">To open the Security page for an item</span></span>  
  
1.  <span data-ttu-id="13e5e-113">レポート マネージャーを開き、セキュリティの設定を構成するアイテムを探します。</span><span class="sxs-lookup"><span data-stu-id="13e5e-113">Open Report Manager, and locate the item for which you want to configure security settings.</span></span>  
  
2.  <span data-ttu-id="13e5e-114">アイテムの上にマウス ポインターを移動し、下矢印をクリックします。</span><span class="sxs-lookup"><span data-stu-id="13e5e-114">Hover over the item, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="13e5e-115">ドロップダウン メニューで次のいずれかの操作を行います。</span><span class="sxs-lookup"><span data-stu-id="13e5e-115">In the drop-down menu, perform one of the following steps:</span></span>  
  
    -   <span data-ttu-id="13e5e-116">**[セキュリティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="13e5e-116">Click **Security**.</span></span> <span data-ttu-id="13e5e-117">この操作により、アイテムの [セキュリティ] プロパティ ページが開きます。</span><span class="sxs-lookup"><span data-stu-id="13e5e-117">This opens the Security properties page for the item.</span></span>  
  
    -   <span data-ttu-id="13e5e-118">**[管理]** をクリックし、アイテムの [全般] プロパティ ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="13e5e-118">Click **Manage** to open the General properties page for the item.</span></span> <span data-ttu-id="13e5e-119">次に、 **[セキュリティ]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="13e5e-119">Then select the **Security** tab.</span></span>  
  
 <span data-ttu-id="13e5e-120">**[アイテムのセキュリティを編集]**</span><span class="sxs-lookup"><span data-stu-id="13e5e-120">**Edit Item Security**</span></span>  
 <span data-ttu-id="13e5e-121">現在のアイテムに定義されているセキュリティを変更する場合にクリックします。</span><span class="sxs-lookup"><span data-stu-id="13e5e-121">Click to change how security is defined for the current item.</span></span> <span data-ttu-id="13e5e-122">フォルダーのセキュリティを編集している場合、現在のフォルダーと任意のサブフォルダーの内容に変更が適用されます。</span><span class="sxs-lookup"><span data-stu-id="13e5e-122">If you are editing security for a folder, your changes apply to the contents of the current folder and any subfolders.</span></span>  
  
 <span data-ttu-id="13e5e-123">このボタンは、[ホーム] フォルダーでは使用できません。</span><span class="sxs-lookup"><span data-stu-id="13e5e-123">This button is not available for the Home folder.</span></span>  
  
 <span data-ttu-id="13e5e-124">アイテムのセキュリティを編集する際、以下のボタンが使用可能になります。</span><span class="sxs-lookup"><span data-stu-id="13e5e-124">The following buttons become available when you edit item security.</span></span>  
  
 <span data-ttu-id="13e5e-125">**削除**</span><span class="sxs-lookup"><span data-stu-id="13e5e-125">**Delete**</span></span>  
 <span data-ttu-id="13e5e-126">削除するグループ名またはユーザー名の横のチェック ボックスをオンにして、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="13e5e-126">Select the check box next to the group or user name that you want to delete and click **Delete**.</span></span> <span data-ttu-id="13e5e-127">ロールの割り当てが 1 つしか残っていない場合、またはロールの割り当てがレポート サーバーのセキュリティの基準を定義する組み込みのロールの割り当て ("Built-in\Administrators" など) である場合、ロールの割り当てを削除することはできません。</span><span class="sxs-lookup"><span data-stu-id="13e5e-127">You cannot delete a role assignment if it is the only one remaining, or if it is a built-in role assignment (for example, "Built-in\Administrators") that defines the security baseline for the report server.</span></span> <span data-ttu-id="13e5e-128">ロールの割り当てを削除しても、グループ アカウントやユーザー アカウント、またはロールの定義は削除されません。</span><span class="sxs-lookup"><span data-stu-id="13e5e-128">Deleting a role assignment does not delete a group or user account or role definitions.</span></span>  
  
 <span data-ttu-id="13e5e-129">**新しいロールの割り当て**</span><span class="sxs-lookup"><span data-stu-id="13e5e-129">**New Role Assignment**</span></span>  
 <span data-ttu-id="13e5e-130">クリックすると、[新しいロールの割り当て] ページが開きます。このページは、現在のアイテムに新たなロールの割り当てを作成するために使用します。</span><span class="sxs-lookup"><span data-stu-id="13e5e-130">Click to open the New Role Assignment page, which is used to create additional role assignments for the current item.</span></span> <span data-ttu-id="13e5e-131">詳細については、「[新しいロールの割り当て: [ロールの割り当ての編集] ページ &#40;レポートマネージャー&#41;](../../2014/reporting-services/new-role-assignment-edit-role-assignment-page-report-manager.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="13e5e-131">For more information, see [New Role Assignment: Edit Role Assignment Page &#40;Report Manager&#41;](../../2014/reporting-services/new-role-assignment-edit-role-assignment-page-report-manager.md).</span></span>  
  
 <span data-ttu-id="13e5e-132">**[親のセキュリティに戻す]**</span><span class="sxs-lookup"><span data-stu-id="13e5e-132">**Revert to Parent Security**</span></span>  
 <span data-ttu-id="13e5e-133">セキュリティ設定を直接の親フォルダーの設定に再設定する場合にクリックします。</span><span class="sxs-lookup"><span data-stu-id="13e5e-133">Click to reset the security settings to that of the immediate parent folder.</span></span> <span data-ttu-id="13e5e-134">レポート サーバーのフォルダー階層全体で継承が維持される場合、最上位のフォルダーである [ホーム] フォルダーのセキュリティ設定が使用されます。</span><span class="sxs-lookup"><span data-stu-id="13e5e-134">If inheritance is unbroken throughout the report server folder hierarchy, the security settings of the top-level folder, Home, are used.</span></span>  
  
 <span data-ttu-id="13e5e-135">**[グループまたはユーザー]**</span><span class="sxs-lookup"><span data-stu-id="13e5e-135">**Group or User**</span></span>  
 <span data-ttu-id="13e5e-136">現在のアイテムにおける、既存のロールの割り当ての一部であるグループおよびユーザーが一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="13e5e-136">Lists the groups and users that are part of an existing role assignment for the current item.</span></span> <span data-ttu-id="13e5e-137">この列には、現在のフォルダーに対する既存のロールの割り当てが定義されているグループおよびユーザーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="13e5e-137">Existing role assignments for the current folder are defined for the groups and users that appear in this column.</span></span> <span data-ttu-id="13e5e-138">グループ名またはユーザー名をクリックして、ロールの割り当ての詳細を表示または編集できます。</span><span class="sxs-lookup"><span data-stu-id="13e5e-138">You can click a group or user name to view or edit role assignment details.</span></span>  
  
 <span data-ttu-id="13e5e-139">**ロール**</span><span class="sxs-lookup"><span data-stu-id="13e5e-139">**Roles**</span></span>  
 <span data-ttu-id="13e5e-140">既存のロールの割り当ての一部であるロールの定義が 1 つ以上表示されます。</span><span class="sxs-lookup"><span data-stu-id="13e5e-140">Lists one or more role definitions that are part of an existing role assignment.</span></span> <span data-ttu-id="13e5e-141">1 つのグループ アカウントまたは 1 つのユーザー アカウントに複数のロールが割り当てられている場合、そのグループまたはユーザーは、そのロールに属するすべてのタスクを実行できます。</span><span class="sxs-lookup"><span data-stu-id="13e5e-141">If multiple roles are assigned to a group or user account, that group or user can perform all tasks that belong to those roles.</span></span> <span data-ttu-id="13e5e-142">ロールに関連付けられているタスクを表示するには、SQL Server Management Studio を使用して各ロール定義のタスクを表示します。</span><span class="sxs-lookup"><span data-stu-id="13e5e-142">To view the tasks that are associated with a role, use SQL Server Management Studio to view the tasks in each role definition.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13e5e-143">参照</span><span class="sxs-lookup"><span data-stu-id="13e5e-143">See Also</span></span>  
 <span data-ttu-id="13e5e-144">[レポートマネージャーの F1 ヘルプ](../../2014/reporting-services/report-manager-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="13e5e-144">[Report Manager F1 Help](../../2014/reporting-services/report-manager-f1-help.md) </span></span>  
 <span data-ttu-id="13e5e-145">[定義済みロール](security/role-definitions-predefined-roles.md) </span><span class="sxs-lookup"><span data-stu-id="13e5e-145">[Predefined Roles](security/role-definitions-predefined-roles.md) </span></span>  
 <span data-ttu-id="13e5e-146">[ネイティブ モードのレポート サーバーに対する権限の許可](security/granting-permissions-on-a-native-mode-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="13e5e-146">[Granting Permissions on a Native Mode Report Server](security/granting-permissions-on-a-native-mode-report-server.md) </span></span>  
 <span data-ttu-id="13e5e-147">[ロールの割り当て](security/role-assignments.md) </span><span class="sxs-lookup"><span data-stu-id="13e5e-147">[Role Assignments](security/role-assignments.md) </span></span>  
 [<span data-ttu-id="13e5e-148">ロールの定義</span><span class="sxs-lookup"><span data-stu-id="13e5e-148">Role Definitions</span></span>](security/role-definitions.md)  
  
  
