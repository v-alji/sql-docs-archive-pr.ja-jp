---
title: '[ユーザー ロールのプロパティ] (Management Studio) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.userroleproperties.f1
ms.assetid: c8b22236-a8b1-4e15-b1ff-4e1909b602d3
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6f79953abdf5e3d1cdb03de8c5feeb6b2de34ab7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715997"
---
# <a name="user-role-properties-management-studio"></a><span data-ttu-id="7717f-102">[ユーザー ロールのプロパティ]\(Management Studio)</span><span class="sxs-lookup"><span data-stu-id="7717f-102">User Role Properties (Management Studio)</span></span>
  <span data-ttu-id="7717f-103">このページを使用すると、アイテムレベルのロールの定義に含まれるタスクを表示できます。</span><span class="sxs-lookup"><span data-stu-id="7717f-103">Use this page to view which tasks are included in an item-level role definition.</span></span> <span data-ttu-id="7717f-104">また、このページを使用して、タスク一覧を変更したりロールの説明を変更したりすることもできます。</span><span class="sxs-lookup"><span data-stu-id="7717f-104">You can also use this page to change the task list or modify a role description.</span></span>  
  
 <span data-ttu-id="7717f-105">アイテムレベルのロールの定義は、ユーザーが特定のアイテム (フォルダー、レポート、リソース、または共有データ ソース) に対して実行する名前付きの一連のタスクです。</span><span class="sxs-lookup"><span data-stu-id="7717f-105">An item-level role definition is a named collection of tasks that users perform relative to a specific item (that is, a folder, report, resource, or shared data source).</span></span> <span data-ttu-id="7717f-106">ロールの定義は、レポート マネージャーでロールの割り当てを作成するためにユーザーまたはグループに割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="7717f-106">Role definitions are assigned to a user or group to create a role assignment in Report Manager.</span></span> <span data-ttu-id="7717f-107">ユーザーまたはグループが実行できる内容は、ロールの定義に含まれているタスクによって記述されます。</span><span class="sxs-lookup"><span data-stu-id="7717f-107">The tasks in the role definition describe what the user or group can do.</span></span>  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="7717f-108">には、作業に使用できる事前定義されたアイテムレベルのロールの定義が多く含まれています。</span><span class="sxs-lookup"><span data-stu-id="7717f-108">includes a number of predefined item-level role definitions that you can work with.</span></span> <span data-ttu-id="7717f-109">定義ごとのタスク一覧を変更することで、ロールの定義を変更できます。</span><span class="sxs-lookup"><span data-stu-id="7717f-109">You can modify the role definitions by changing the task list of each one.</span></span> <span data-ttu-id="7717f-110">ロールの定義を編集すると、そのロールの定義を含むすべてのロールの割り当てに反映されます。</span><span class="sxs-lookup"><span data-stu-id="7717f-110">Editing a role definition affects all role assignments that include the role definition.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7717f-111">ユーザー ロールの割り当ては、ネイティブ モードで実行されているレポート サーバーでのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="7717f-111">User role assignments are used only on a report server that runs in native mode.</span></span> <span data-ttu-id="7717f-112">レポート サーバーが SharePoint 統合モード用に構成されている場合、このページには、SharePoint サイトで定義されているロールと権限レベルに関する読み取り専用の情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="7717f-112">If the report server is configured for SharePoint integration, this page displays read-only information about the roles and permission levels that are defined on the SharePoint site.</span></span>  
  
## <a name="options"></a><span data-ttu-id="7717f-113">オプション</span><span class="sxs-lookup"><span data-stu-id="7717f-113">Options</span></span>  
 <span data-ttu-id="7717f-114">**Name**</span><span class="sxs-lookup"><span data-stu-id="7717f-114">**Name**</span></span>  
 <span data-ttu-id="7717f-115">ロールの定義名を指定します。</span><span class="sxs-lookup"><span data-stu-id="7717f-115">Specifies the name of the role definition.</span></span>  
  
 <span data-ttu-id="7717f-116">**説明**</span><span class="sxs-lookup"><span data-stu-id="7717f-116">**Description**</span></span>  
 <span data-ttu-id="7717f-117">ロール定義の説明が表示されます。</span><span class="sxs-lookup"><span data-stu-id="7717f-117">Shows a description of the role definition.</span></span> <span data-ttu-id="7717f-118">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]では、この説明はこのページにのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="7717f-118">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], this description is only visible in this page.</span></span> <span data-ttu-id="7717f-119">この説明は、レポート マネージャーでロールの割り当てを行う際にそのロールを使用するかどうかを判断するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="7717f-119">In Report Manager, this description helps users decide whether to use the role in a role assignment.</span></span>  
  
 <span data-ttu-id="7717f-120">**タスク**</span><span class="sxs-lookup"><span data-stu-id="7717f-120">**Task**</span></span>  
 <span data-ttu-id="7717f-121">このロール定義で選択できるアイテムレベルのタスクがすべて一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="7717f-121">Lists all item-level tasks that can be selected for this role definition.</span></span> <span data-ttu-id="7717f-122">定義済みタスクの一覧にアイテムを追加または一覧から削除することで、ユーザーがこのロールを使用して特定のアイテムにアクセスする方法を定義できます。</span><span class="sxs-lookup"><span data-stu-id="7717f-122">You can add or remove items from the predefined task list to define how users access a given item through this role.</span></span> <span data-ttu-id="7717f-123">新しいタスクを作成したり、既存のタスクを変更したりすることはできません。</span><span class="sxs-lookup"><span data-stu-id="7717f-123">You cannot create new tasks, and you cannot modify existing tasks.</span></span> <span data-ttu-id="7717f-124">ロールの定義のタスク一覧は、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="7717f-124">The task list of a role definition appears only in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="7717f-125">**タスクの説明**</span><span class="sxs-lookup"><span data-stu-id="7717f-125">**Task Description**</span></span>  
 <span data-ttu-id="7717f-126">各タスクに関する情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="7717f-126">Provides information about each task.</span></span> <span data-ttu-id="7717f-127">タスクの説明を変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="7717f-127">You cannot modify task descriptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7717f-128">参照</span><span class="sxs-lookup"><span data-stu-id="7717f-128">See Also</span></span>  
 <span data-ttu-id="7717f-129">[アイテムレベルのタスク](../security/tasks-and-permissions-item-level-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="7717f-129">[Item-Level Tasks](../security/tasks-and-permissions-item-level-tasks.md) </span></span>  
 <span data-ttu-id="7717f-130">[ロールの定義](../security/role-definitions.md) </span><span class="sxs-lookup"><span data-stu-id="7717f-130">[Role Definitions](../security/role-definitions.md) </span></span>  
 <span data-ttu-id="7717f-131">[Management Studio のレポート サーバーの F1 ヘルプ](report-server-in-management-studio-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="7717f-131">[Report Server in Management Studio F1 Help](report-server-in-management-studio-f1-help.md) </span></span>  
 <span data-ttu-id="7717f-132">[タスクと権限](../security/tasks-and-permissions.md) </span><span class="sxs-lookup"><span data-stu-id="7717f-132">[Tasks and Permissions](../security/tasks-and-permissions.md) </span></span>  
 [<span data-ttu-id="7717f-133">定義済みロール</span><span class="sxs-lookup"><span data-stu-id="7717f-133">Predefined Roles</span></span>](../security/role-definitions-predefined-roles.md)  
  
  
