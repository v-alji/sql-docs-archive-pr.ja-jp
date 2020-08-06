---
title: システム ロールのプロパティ (Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.systemroleproperties.f1
ms.assetid: 0210fc2a-74fb-41dd-8e39-4830047ec417
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b37ebb1cb95d6628884d81156c9c1bc29bff86fd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633716"
---
# <a name="system-role-properties-management-studio"></a><span data-ttu-id="a3639-102">システム ロールのプロパティ (Management Studio)</span><span class="sxs-lookup"><span data-stu-id="a3639-102">System Role Properties (Management Studio)</span></span>
  <span data-ttu-id="a3639-103">[システム ロール] ページは、レポート サーバーで現在定義されているシステム ロールの定義を表示するために使用します。</span><span class="sxs-lookup"><span data-stu-id="a3639-103">Use the System Roles page to view the system role definitions that are currently defined for the report server.</span></span> <span data-ttu-id="a3639-104">システム ロールの定義には、個別のアイテムではなく、サイト全体に関連して実行される名前付きのタスクのコレクションが含まれています。</span><span class="sxs-lookup"><span data-stu-id="a3639-104">A system role definition contains a named collection of tasks that are performed relative to the entire site, instead of an individual item.</span></span> <span data-ttu-id="a3639-105">ロールの定義は、ロールの割り当てを作成するために、ユーザーまたはグループに割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="a3639-105">Role definitions are assigned to a user or groups to create a resulting role assignment.</span></span> <span data-ttu-id="a3639-106">ロールの定義のタスクには、ユーザーまたはグループが実行できる操作を指定します。</span><span class="sxs-lookup"><span data-stu-id="a3639-106">The tasks in the role definition specify what the user or group can do.</span></span>  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="a3639-107">では、 **システム管理者** と **システム ユーザー**という 2 つのシステム ロールがあらかじめ定義されています。</span><span class="sxs-lookup"><span data-stu-id="a3639-107">has two predefined system role definitions: **System Administrator** and **System User**.</span></span> <span data-ttu-id="a3639-108">タスクの一覧を変更することにより、ロールの定義を変更できます。また、異なるタスクの組み合わせをサポートする新しいシステム ロールを作成できます。</span><span class="sxs-lookup"><span data-stu-id="a3639-108">You can modify these role definitions by changing the task list, or you can create a new system role that supports a different combination of tasks.</span></span> <span data-ttu-id="a3639-109">ロールの定義を編集すると、そのロールの定義を含むすべてのロールの割り当てに反映されます。</span><span class="sxs-lookup"><span data-stu-id="a3639-109">Editing a role definition affects all role assignments that include the role definition.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a3639-110">システム ロールの割り当ては、ネイティブ モードで実行されているレポート サーバーでのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="a3639-110">System role assignments are used only on a report server that runs in native mode.</span></span> <span data-ttu-id="a3639-111">レポート サーバーが SharePoint 統合モード用に構成されている場合、このページは使用できません。</span><span class="sxs-lookup"><span data-stu-id="a3639-111">If the report server is configured for SharePoint integration, this page is not available.</span></span>  
  
## <a name="options"></a><span data-ttu-id="a3639-112">オプション</span><span class="sxs-lookup"><span data-stu-id="a3639-112">Options</span></span>  
 <span data-ttu-id="a3639-113">**Name**</span><span class="sxs-lookup"><span data-stu-id="a3639-113">**Name**</span></span>  
 <span data-ttu-id="a3639-114">システム ロールの定義名を指定します。</span><span class="sxs-lookup"><span data-stu-id="a3639-114">Specifies the name of the system role definition.</span></span>  
  
 <span data-ttu-id="a3639-115">**説明**</span><span class="sxs-lookup"><span data-stu-id="a3639-115">**Description**</span></span>  
 <span data-ttu-id="a3639-116">システム ロール定義の説明が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a3639-116">Shows a description of the system role definition.</span></span> <span data-ttu-id="a3639-117">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] では、この説明はこのページにのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="a3639-117">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], this description is only visible in this page.</span></span> <span data-ttu-id="a3639-118">レポート マネージャーを使用してこのアイテムを表示すると、フォルダー階層を参照しているときにこの説明が表示される場合があります。</span><span class="sxs-lookup"><span data-stu-id="a3639-118">Users who view this item through Report Manager may see this description when browsing the folder hierarchy.</span></span>  
  
 <span data-ttu-id="a3639-119">**タスク**</span><span class="sxs-lookup"><span data-stu-id="a3639-119">**Task**</span></span>  
 <span data-ttu-id="a3639-120">このロール定義で選択できるシステムレベルのタスクがすべて一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="a3639-120">Lists all system-level tasks that can be selected for this role definition.</span></span> <span data-ttu-id="a3639-121">定義済みタスクの一覧にアイテムを追加または一覧から削除することで、ユーザーがこのロールを使用して特定のアイテムにアクセスする方法を定義できます。</span><span class="sxs-lookup"><span data-stu-id="a3639-121">You can add or remove items from the predefined task list to define how users access a given item through this role.</span></span> <span data-ttu-id="a3639-122">新しいタスクを作成したり、既存のタスクを変更したりすることはできません。</span><span class="sxs-lookup"><span data-stu-id="a3639-122">You cannot create new tasks, and you cannot modify existing tasks.</span></span>  
  
 <span data-ttu-id="a3639-123">**説明**</span><span class="sxs-lookup"><span data-stu-id="a3639-123">**Description**</span></span>  
 <span data-ttu-id="a3639-124">各タスクに関する情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a3639-124">Provides information about each task.</span></span> <span data-ttu-id="a3639-125">タスクの説明を変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="a3639-125">You cannot modify task descriptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3639-126">参照</span><span class="sxs-lookup"><span data-stu-id="a3639-126">See Also</span></span>  
 <span data-ttu-id="a3639-127">[Management Studio のレポート サーバーの F1 ヘルプ](report-server-in-management-studio-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="a3639-127">[Report Server in Management Studio F1 Help](report-server-in-management-studio-f1-help.md) </span></span>  
 <span data-ttu-id="a3639-128">[システムレベルのタスク](../security/tasks-and-permissions-system-level-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="a3639-128">[System-Level Tasks](../security/tasks-and-permissions-system-level-tasks.md) </span></span>  
 <span data-ttu-id="a3639-129">[タスクと権限](../security/tasks-and-permissions.md) </span><span class="sxs-lookup"><span data-stu-id="a3639-129">[Tasks and Permissions](../security/tasks-and-permissions.md) </span></span>  
 [<span data-ttu-id="a3639-130">定義済みロール</span><span class="sxs-lookup"><span data-stu-id="a3639-130">Predefined Roles</span></span>](../security/role-definitions-predefined-roles.md)  
  
  
