---
title: '[新しいロールの割り当て]: [ロールの割り当ての編集] ページ (レポートマネージャー) |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 3319ced0-4b86-42af-b18d-da41a625113c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 1640617dbf9836986597ee49d4ca1ddc37fd84ab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738023"
---
# <a name="new-role-assignment-edit-role-assignment-page-report-manager"></a><span data-ttu-id="8c5fb-102">[新しいロールの割り当て]: [ロールの割り当てを編集] ページ (レポート マネージャー)</span><span class="sxs-lookup"><span data-stu-id="8c5fb-102">New Role Assignment: Edit Role Assignment Page (Report Manager)</span></span>
  <span data-ttu-id="8c5fb-103">レポート サーバーのアイテムと操作に対する権限を与えるには、[新しいロールの割り当て] ページまたは [ロールの割り当てを編集] ページを使用します。</span><span class="sxs-lookup"><span data-stu-id="8c5fb-103">Use the New Role Assignment or Edit Role Assignment page to grant permissions to report server items and operations.</span></span> <span data-ttu-id="8c5fb-104">レポート サーバーへのアクセスを必要とするユーザーごとに、アクセスのレベルを定義するロールの割り当てが必要です。</span><span class="sxs-lookup"><span data-stu-id="8c5fb-104">Each user who requires access to a report server must have a role assignment that defines the level of access.</span></span> <span data-ttu-id="8c5fb-105">ロールの割り当ては、ルート ノードか、特定のレポート、モデル、フォルダー、リソース、または共有データ ソースに作成できます。</span><span class="sxs-lookup"><span data-stu-id="8c5fb-105">You can create role assignments at the root node, or on a specific report, model, folder, resource, or shared data source.</span></span> [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] <span data-ttu-id="8c5fb-106">のセキュリティは、アイテムに適用するロールの割り当てによって設定されます。</span><span class="sxs-lookup"><span data-stu-id="8c5fb-106">security is enforced through role assignments that you apply to items.</span></span> <span data-ttu-id="8c5fb-107">ロールの割り当てにより、グループまたはユーザーをロールの定義と適合させます。各ロールの定義により、特定のアイテムに対してグループまたはユーザーが実行できるタスクが識別されます。</span><span class="sxs-lookup"><span data-stu-id="8c5fb-107">A role assignment matches a group or user to a role definition, where each role definition identifies the tasks that groups or users can perform with regards to a specific item.</span></span>  
  
 <span data-ttu-id="8c5fb-108">アイテム レベルのロールの割り当ては、広い範囲に影響を与えることがあります。</span><span class="sxs-lookup"><span data-stu-id="8c5fb-108">Item-level role assignments can have a broad impact.</span></span> <span data-ttu-id="8c5fb-109">アイテム レベルのロールの割り当ては、単一のレポートまたはフォルダーと関連付けることができますが、フォルダー階層の高いレベルで定義し、ツリーの子フォルダーおよび子アイテムに継承することも可能です。</span><span class="sxs-lookup"><span data-stu-id="8c5fb-109">Although they can be associated with a single report or folder, they can also be defined at a high level in the folder hierarchy and be inherited by folders and items that are lower in the tree.</span></span> <span data-ttu-id="8c5fb-110">詳細については、「[レポートサーバーへのユーザーアクセスを許可する &#40;レポートマネージャー&#41;](security/grant-user-access-to-a-report-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8c5fb-110">For more information, see [Grant User Access to a Report Server &#40;Report Manager&#41;](security/grant-user-access-to-a-report-server.md).</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="8c5fb-111">ナビゲーション</span><span class="sxs-lookup"><span data-stu-id="8c5fb-111">Navigation</span></span>  
 <span data-ttu-id="8c5fb-112">ユーザー インターフェイス (UI) のこの場所に移動するには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="8c5fb-112">Use the following procedure to navigate to this location in the user interface (UI).</span></span>  
  
###### <a name="to-open-the-new-role-assignment-or-edit-role-assignment-page"></a><span data-ttu-id="8c5fb-113">[新しいロールの割り当て] ページまたは [ロールの割り当てを編集] ページを開くには</span><span class="sxs-lookup"><span data-stu-id="8c5fb-113">To open the New Role Assignment or Edit Role Assignment page</span></span>  
  
1.  <span data-ttu-id="8c5fb-114">レポート マネージャーを開き、新しいロールの割り当てを追加するアイテムか、ロールの割り当てを編集するアイテムを探します。</span><span class="sxs-lookup"><span data-stu-id="8c5fb-114">Open Report Manager, and locate an item for which you want to add a new role assignment or edit a role assignment.</span></span>  
  
2.  <span data-ttu-id="8c5fb-115">アイテムの上にマウス ポインターを移動し、下矢印をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8c5fb-115">Hover over the item, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="8c5fb-116">ドロップダウン メニューの **[セキュリティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8c5fb-116">In the drop-down menu, click **Security**.</span></span> <span data-ttu-id="8c5fb-117">この操作により、アイテムの [セキュリティ] プロパティ ページが開きます。</span><span class="sxs-lookup"><span data-stu-id="8c5fb-117">This opens the Security properties page for the item.</span></span>  
  
4.  <span data-ttu-id="8c5fb-118">新しいロールの割り当てを追加する場合は、ツール バーの **[新しいロールの割り当て]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8c5fb-118">If you want to add a new role assignment, in the toolbar, click **New Role Assignment**.</span></span> <span data-ttu-id="8c5fb-119">ロールの割り当てを編集する場合は、編集するグループまたはユーザーの名前の隣にある **[編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8c5fb-119">If you want to edit a role assignment, click **Edit** next to the group or user name you want to edit.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8c5fb-120">アイテムが現在、親アイテムからセキュリティを継承している場合は、ツール バーの **[アイテムのセキュリティを編集]** をクリックしてセキュリティの設定を変更します。</span><span class="sxs-lookup"><span data-stu-id="8c5fb-120">If an item currently inherits security from a parent item, click **Edit Item Security** in the toolbar to change the security settings.</span></span>  
  
## <a name="options"></a><span data-ttu-id="8c5fb-121">Options</span><span class="sxs-lookup"><span data-stu-id="8c5fb-121">Options</span></span>  
 <span data-ttu-id="8c5fb-122">**[グループ名またはユーザー名]**</span><span class="sxs-lookup"><span data-stu-id="8c5fb-122">**Group or User Name**</span></span>  
 <span data-ttu-id="8c5fb-123">ロールの割り当てが作成されるグループ アカウントまたはユーザー アカウントの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="8c5fb-123">Type the name of a group or user account for which the role assignment is being created.</span></span> <span data-ttu-id="8c5fb-124">グループ名またはユーザー名は、有効な Windows ドメイン アカウントである必要があります。</span><span class="sxs-lookup"><span data-stu-id="8c5fb-124">The group or user name must be a valid Windows domain account.</span></span> <span data-ttu-id="8c5fb-125">アカウントは、<アカウントの形式で入力し \<domain> \\ \> ます。</span><span class="sxs-lookup"><span data-stu-id="8c5fb-125">Enter the account in this format: \<domain>\\<account\>.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8c5fb-126">このボックスは、[新しいロールの割り当て] ページでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="8c5fb-126">This box is available only on the New Role Assignment page.</span></span>  
  
 <span data-ttu-id="8c5fb-127">**ロール**</span><span class="sxs-lookup"><span data-stu-id="8c5fb-127">**Role**</span></span>  
 <span data-ttu-id="8c5fb-128">アイテムのセキュリティの定義に使用できる、レポート サーバーで定義されているすべてのロールを表示します。</span><span class="sxs-lookup"><span data-stu-id="8c5fb-128">Shows all roles defined on the report server that can be used to define security for items.</span></span> <span data-ttu-id="8c5fb-129">レポートやフォルダーへのロールの割り当てを作成または変更する場合、1 つ以上のロールを選択して、ユーザーが実行する必要のある操作が一連のタスクとして記述されるようにします。</span><span class="sxs-lookup"><span data-stu-id="8c5fb-129">When you create or change a role assignment for a report or folder, select one or more roles until the combined set of tasks describe the actions that the user should be allowed to perform.</span></span> <span data-ttu-id="8c5fb-130">各ロールでサポートされている一連のタスクを表示するには、を使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] します。</span><span class="sxs-lookup"><span data-stu-id="8c5fb-130">To view the set of tasks that each role supports, use [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)].</span></span> <span data-ttu-id="8c5fb-131">レポート マネージャーでロールを表示、作成、変更、または削除することはできません。</span><span class="sxs-lookup"><span data-stu-id="8c5fb-131">You cannot view, create, modify, or delete roles in Report Manager.</span></span> <span data-ttu-id="8c5fb-132">手順については、「[ロールを作成、削除、または変更する &#40;Management Studio&#41;](security/role-definitions-create-delete-or-modify.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8c5fb-132">For instructions, see [Create, Delete, or Modify a Role &#40;Management Studio&#41;](security/role-definitions-create-delete-or-modify.md).</span></span>  
  
 <span data-ttu-id="8c5fb-133">**説明**</span><span class="sxs-lookup"><span data-stu-id="8c5fb-133">**Description**</span></span>  
 <span data-ttu-id="8c5fb-134">ロールに関する詳細を表示します。</span><span class="sxs-lookup"><span data-stu-id="8c5fb-134">Shows additional information about the role.</span></span> <span data-ttu-id="8c5fb-135">**閲覧者** や **コンテンツ マネージャー**などの定義済みロールに関しては、各ロールでサポートされているタスクの要約が説明として提供されます。</span><span class="sxs-lookup"><span data-stu-id="8c5fb-135">For predefined roles such as **Browser** or **Content Manager**, the description summarizes the tasks that each role supports.</span></span>  
  
 <span data-ttu-id="8c5fb-136">**ロールの割り当ての削除**</span><span class="sxs-lookup"><span data-stu-id="8c5fb-136">**Delete Role Assignment**</span></span>  
 <span data-ttu-id="8c5fb-137">ユーザーまたはグループの既存のロールの割り当てを削除する場合にクリックします。</span><span class="sxs-lookup"><span data-stu-id="8c5fb-137">Click to delete an existing role assignment for a user or a group.</span></span> <span data-ttu-id="8c5fb-138">残っているロールの割り当てが 1 つのみである場合、そのロールの割り当てを削除することはできません (各アイテムは、ロールの割り当てを少なくとも 1 つ保持している必要があります)。</span><span class="sxs-lookup"><span data-stu-id="8c5fb-138">You cannot delete a role assignment if it is the only one left (each item must have a minimum of one role assignment).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8c5fb-139">このボタンは、[ロールの割り当てを編集] ページでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="8c5fb-139">This button is available only on the Edit Role Assignment page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c5fb-140">参照</span><span class="sxs-lookup"><span data-stu-id="8c5fb-140">See Also</span></span>  
 <span data-ttu-id="8c5fb-141">[ロール &#40;Management Studio の作成、削除、または変更&#41;](security/role-definitions-create-delete-or-modify.md) </span><span class="sxs-lookup"><span data-stu-id="8c5fb-141">[Create, Delete, or Modify a Role &#40;Management Studio&#41;](security/role-definitions-create-delete-or-modify.md) </span></span>  
 <span data-ttu-id="8c5fb-142">[ネイティブ モードのレポート サーバーに対する権限の許可](security/granting-permissions-on-a-native-mode-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="8c5fb-142">[Granting Permissions on a Native Mode Report Server](security/granting-permissions-on-a-native-mode-report-server.md) </span></span>  
 <span data-ttu-id="8c5fb-143">[レポート マネージャー &#40;SSRS ネイティブ モード&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="8c5fb-143">[Report Manager  &#40;SSRS Native Mode&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="8c5fb-144">[レポートマネージャーの F1 ヘルプ](../../2014/reporting-services/report-manager-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="8c5fb-144">[Report Manager F1 Help](../../2014/reporting-services/report-manager-f1-help.md) </span></span>  
 <span data-ttu-id="8c5fb-145">[ロールの割り当て](security/role-assignments.md) </span><span class="sxs-lookup"><span data-stu-id="8c5fb-145">[Role Assignments](security/role-assignments.md) </span></span>  
 [<span data-ttu-id="8c5fb-146">レポート サーバーへのユーザー アクセスを許可する (レポート マネージャー)</span><span class="sxs-lookup"><span data-stu-id="8c5fb-146">Grant User Access to a Report Server &#40;Report Manager&#41;</span></span>](security/grant-user-access-to-a-report-server.md)  
  
  
