---
title: タスクとアクセス許可 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- permissions [Reporting Services], tasks
- role-based security [Reporting Services], permissions
- security [Reporting Services], tasks
- security [Reporting Services], permissions
- role-based security [Reporting Services], tasks
- predefined tasks [Reporting Services]
- tasks [Reporting Services]
ms.assetid: d7ff90b5-b976-4270-b9ad-9d7b801d8263
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 01cbf00850c5dd57e7ca1575a1a0cb826c009714
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739145"
---
# <a name="tasks-and-permissions"></a><span data-ttu-id="d4c3a-102">タスクと権限</span><span class="sxs-lookup"><span data-stu-id="d4c3a-102">Tasks and Permissions</span></span>
  <span data-ttu-id="d4c3a-103">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]における *タスク* とは、ユーザーまたは管理者が実行できるアクションのことです。</span><span class="sxs-lookup"><span data-stu-id="d4c3a-103">In [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], *tasks* are actions that a user or administrator can perform.</span></span> <span data-ttu-id="d4c3a-104">タスクは事前に定義されています。</span><span class="sxs-lookup"><span data-stu-id="d4c3a-104">Tasks are predefined.</span></span> <span data-ttu-id="d4c3a-105">カスタム タスクを作成したり、プログラムまたはツールから提供されるタスクを変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="d4c3a-105">You cannot create custom tasks or modify the ones provided either programmatically or through a tool.</span></span> <span data-ttu-id="d4c3a-106">タスクは全部で 25 種類あります。</span><span class="sxs-lookup"><span data-stu-id="d4c3a-106">There are twenty-five tasks in all.</span></span> <span data-ttu-id="d4c3a-107">これらのタスクにより、ロールベースのセキュリティで実行できる操作の全体が構成されています。</span><span class="sxs-lookup"><span data-stu-id="d4c3a-107">These tasks comprise the entire set of operations that are available in role-based security.</span></span> <span data-ttu-id="d4c3a-108">タスクの例としては、"レポートの表示"、"レポートの管理"、"レポート サーバーのプロパティを管理" などがあります。</span><span class="sxs-lookup"><span data-stu-id="d4c3a-108">Some examples of tasks include "View reports," "Manage reports," and "Manage report server properties."</span></span>  
  
 <span data-ttu-id="d4c3a-109">各タスクは、同様に事前定義されている一連の権限で構成されます。</span><span class="sxs-lookup"><span data-stu-id="d4c3a-109">Each task consists of a set of permissions, which are also predefined.</span></span> <span data-ttu-id="d4c3a-110">たとえば、"フォルダーの管理" タスクには、フォルダーを作成および削除する権限や、フォルダーのプロパティを表示および更新する権限が含まれています。</span><span class="sxs-lookup"><span data-stu-id="d4c3a-110">For example, the "Manage folders" task contains permissions to create and delete folders and view and update folder properties.</span></span> <span data-ttu-id="d4c3a-111">各タスクに対する権限は、各タスクをより詳細に説明するために記述されています。</span><span class="sxs-lookup"><span data-stu-id="d4c3a-111">Permissions for each task are documented to provide a more exact description of each task.</span></span> <span data-ttu-id="d4c3a-112">権限を直接操作したり、ロールの割り当てで指定したりすることはできません。</span><span class="sxs-lookup"><span data-stu-id="d4c3a-112">It is not possible to interact with permissions directly or to specify them in role assignments.</span></span> <span data-ttu-id="d4c3a-113">ユーザーは、ロールの定義に含まれているタスクから間接的に権限を与えられます。</span><span class="sxs-lookup"><span data-stu-id="d4c3a-113">Users are granted permissions indirectly through the tasks that are included in role definitions.</span></span>  
  
 <span data-ttu-id="d4c3a-114">タスクは、そのタスクがロールの一部であり、そのロールがロールの割り当てに含まれている場合にのみ実行できます。</span><span class="sxs-lookup"><span data-stu-id="d4c3a-114">Tasks can be performed only if they are part of a role and that role is included in a role assignment.</span></span> <span data-ttu-id="d4c3a-115">そのため、たとえば "モデルの表示" タスクがロールに含まれていない場合や、そのロールがロールの割り当てに含まれていない場合、ユーザーはレポート モデルを表示できません。</span><span class="sxs-lookup"><span data-stu-id="d4c3a-115">Thus, if the View Models task is not included in a role, or that role is not included in a role assignment, users cannot view report models.</span></span> <span data-ttu-id="d4c3a-116">次の図では、権限がタスクにどのように組み込まれるか、および特定のロールの割り当てに使用できるロールにタスクがどのように組み込まれるかを示します。</span><span class="sxs-lookup"><span data-stu-id="d4c3a-116">The following diagram shows how permissions are combined into tasks, and how tasks are combined into roles that can be used for specific role assignments.</span></span>  
  
 <span data-ttu-id="d4c3a-117">![権限とタスク図](../media/report-securityobjects.gif "権限とタスク図")</span><span class="sxs-lookup"><span data-stu-id="d4c3a-117">![Permissions and task diagram](../media/report-securityobjects.gif "Permissions and task diagram")</span></span>  
<span data-ttu-id="d4c3a-118">権限とタスク図</span><span class="sxs-lookup"><span data-stu-id="d4c3a-118">Permissions and task diagram</span></span>  
  
## <a name="system-and-item-level-tasks"></a><span data-ttu-id="d4c3a-119">システムレベルおよびアイテムレベルのタスク</span><span class="sxs-lookup"><span data-stu-id="d4c3a-119">System and Item Level Tasks</span></span>  
 <span data-ttu-id="d4c3a-120">タスクは、システムレベルとアイテムレベルの 2 つのカテゴリに分類されます。</span><span class="sxs-lookup"><span data-stu-id="d4c3a-120">Tasks fall into two categories: system level and item level.</span></span> <span data-ttu-id="d4c3a-121">ロールは、単一のカテゴリからのみタスクを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="d4c3a-121">A role can include tasks only from a single category.</span></span> <span data-ttu-id="d4c3a-122">次の表で、タスクの各カテゴリについて説明します。</span><span class="sxs-lookup"><span data-stu-id="d4c3a-122">The following table describes each category of tasks.</span></span>  
  
|<span data-ttu-id="d4c3a-123">カテゴリ</span><span class="sxs-lookup"><span data-stu-id="d4c3a-123">Category</span></span>|<span data-ttu-id="d4c3a-124">説明</span><span class="sxs-lookup"><span data-stu-id="d4c3a-124">Description</span></span>|  
|--------------|-----------------|  
|[<span data-ttu-id="d4c3a-125">アイテムレベルのタスク</span><span class="sxs-lookup"><span data-stu-id="d4c3a-125">Item-Level Tasks</span></span>](tasks-and-permissions-item-level-tasks.md)|<span data-ttu-id="d4c3a-126">フォルダー、レポート、レポート モデル、リソースなど、レポート サーバーで管理されるアイテムに対して実行されるアクションです。</span><span class="sxs-lookup"><span data-stu-id="d4c3a-126">Actions that are performed on items managed by a report server, such as folders, reports, report models, and resources.</span></span><br /><br /> <span data-ttu-id="d4c3a-127">アイテムレベルのタスクは、レポート サーバー フォルダーの名前空間に対して有効です。</span><span class="sxs-lookup"><span data-stu-id="d4c3a-127">Item-level tasks are scoped to the report server folder namespace.</span></span> <span data-ttu-id="d4c3a-128">レポート サーバーのフォルダーまたは URL によってアクセスするすべてのアイテムは、アイテムレベルのタスクを含んだロールの割り当てによってセキュリティ保護されています。</span><span class="sxs-lookup"><span data-stu-id="d4c3a-128">All items that you access through the folders on a report server or through URL access are secured by role assignments that include item-level tasks.</span></span>|  
|[<span data-ttu-id="d4c3a-129">システムレベルのタスク</span><span class="sxs-lookup"><span data-stu-id="d4c3a-129">System-Level Tasks</span></span>](tasks-and-permissions-system-level-tasks.md)|<span data-ttu-id="d4c3a-130">ジョブまたは共有スケジュールの管理などの、システムレベルで実行されるアクションです。これらのアクションは、多くのアイテムで使用できます。</span><span class="sxs-lookup"><span data-stu-id="d4c3a-130">Actions that are performed at the system level, such as managing jobs or shared schedules that can be used with many items.</span></span> <span data-ttu-id="d4c3a-131">システムレベルのタスクは、レポート サーバー フォルダーの名前空間の外部に対して有効です。</span><span class="sxs-lookup"><span data-stu-id="d4c3a-131">System-level tasks are scoped outside of the report server folder namespace.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d4c3a-132">参照</span><span class="sxs-lookup"><span data-stu-id="d4c3a-132">See Also</span></span>  
 <span data-ttu-id="d4c3a-133">[ロールの定義](role-definitions.md) </span><span class="sxs-lookup"><span data-stu-id="d4c3a-133">[Role Definitions](role-definitions.md) </span></span>  
 <span data-ttu-id="d4c3a-134">[定義済みロール](role-definitions-predefined-roles.md) </span><span class="sxs-lookup"><span data-stu-id="d4c3a-134">[Predefined Roles](role-definitions-predefined-roles.md) </span></span>  
 [<span data-ttu-id="d4c3a-135">ネイティブ モードのレポート サーバーに対する権限の許可</span><span class="sxs-lookup"><span data-stu-id="d4c3a-135">Granting Permissions on a Native Mode Report Server</span></span>](granting-permissions-on-a-native-mode-report-server.md)  
  
  
