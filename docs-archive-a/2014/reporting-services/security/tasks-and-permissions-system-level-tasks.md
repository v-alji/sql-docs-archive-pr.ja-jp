---
title: システムレベルのタスク | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- system-level tasks [Reporting Services]
ms.assetid: 7023b388-40b2-4590-b227-115cf380a1e7
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 98f9390664064cd293b80d094d65c903869bc709
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739157"
---
# <a name="system-level-tasks"></a><span data-ttu-id="85d82-102">システムレベルのタスク</span><span class="sxs-lookup"><span data-stu-id="85d82-102">System-Level Tasks</span></span>
  <span data-ttu-id="85d82-103">システムレベルのタスクとは、レポート サーバー サイト全体に適用される操作に関連した権限を集めたタスクです。</span><span class="sxs-lookup"><span data-stu-id="85d82-103">A system-level task is a collection of permissions that relate to operations that apply to the report server site as a whole.</span></span> [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="85d82-104">にはこの他に、特定のアイテムに適用されるアイテムレベルのタスクがあります。</span><span class="sxs-lookup"><span data-stu-id="85d82-104">also includes item-level tasks that apply to specific items.</span></span> <span data-ttu-id="85d82-105">詳細については、「 [アイテムレベルのタスク](tasks-and-permissions-item-level-tasks.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="85d82-105">For more information, see [Item-Level Tasks](tasks-and-permissions-item-level-tasks.md).</span></span> <span data-ttu-id="85d82-106">一般的なタスクおよび権限の詳細については、「 [タスクと権限](tasks-and-permissions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="85d82-106">For more information about tasks and permissions in general, see [Tasks and Permissions](tasks-and-permissions.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="85d82-107">プログラムでこれらのタスクを使用して処理を実行している場合、システムレベルのタスクをサポートしているメソッドを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="85d82-107">If you are working with these tasks programmatically, you must use methods that support system-level tasks.</span></span> <span data-ttu-id="85d82-108">詳細については、「 <xref:ReportService2010.ReportingService2010.ListTasks%2A> および <xref:ReportService2010.ReportingService2010.ListRoles%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="85d82-108">For more information, see <xref:ReportService2010.ReportingService2010.ListTasks%2A> and <xref:ReportService2010.ReportingService2010.ListRoles%2A>.</span></span>  
  
## <a name="permissions-in-system-level-tasks"></a><span data-ttu-id="85d82-109">システムレベルのタスクの権限</span><span class="sxs-lookup"><span data-stu-id="85d82-109">Permissions in System-Level Tasks</span></span>  
 <span data-ttu-id="85d82-110">次の表に、一連の権限をシステム タスクごとに示します。</span><span class="sxs-lookup"><span data-stu-id="85d82-110">The following table identifies the collection of permissions for each system task.</span></span> <span data-ttu-id="85d82-111">権限の一覧は、タスクごとに利用できる機能をより詳細に示すためにのみ記載されています。</span><span class="sxs-lookup"><span data-stu-id="85d82-111">Permissions are listed for informational purposes only, to provide a more exact description of the functionality available through each task.</span></span>  
  
|<span data-ttu-id="85d82-112">タスク</span><span class="sxs-lookup"><span data-stu-id="85d82-112">Task</span></span>|<span data-ttu-id="85d82-113">アクセス許可</span><span class="sxs-lookup"><span data-stu-id="85d82-113">Permissions</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="85d82-114">レポート定義の実行</span><span class="sxs-lookup"><span data-stu-id="85d82-114">Execute report definitions</span></span>|<span data-ttu-id="85d82-115">レポート定義の実行 (権限とタスクの名前が同じです)</span><span class="sxs-lookup"><span data-stu-id="85d82-115">Execute Report Definitions (the permission and task name are the same)</span></span>|  
|<span data-ttu-id="85d82-116">イベントの生成</span><span class="sxs-lookup"><span data-stu-id="85d82-116">Generate events</span></span>|<span data-ttu-id="85d82-117">イベントの生成</span><span class="sxs-lookup"><span data-stu-id="85d82-117">Generate Events</span></span>|  
|<span data-ttu-id="85d82-118">ジョブの管理</span><span class="sxs-lookup"><span data-stu-id="85d82-118">Manage jobs</span></span>|<span data-ttu-id="85d82-119">システム プロパティの読み取り</span><span class="sxs-lookup"><span data-stu-id="85d82-119">Read System Properties</span></span><br /><br /> <span data-ttu-id="85d82-120">システム プロパティの更新</span><span class="sxs-lookup"><span data-stu-id="85d82-120">Update System Properties</span></span>|  
|<span data-ttu-id="85d82-121">レポート サーバーのプロパティを管理</span><span class="sxs-lookup"><span data-stu-id="85d82-121">Manage report server properties</span></span>|<span data-ttu-id="85d82-122">システム プロパティの読み取り</span><span class="sxs-lookup"><span data-stu-id="85d82-122">Read System Properties</span></span><br /><br /> <span data-ttu-id="85d82-123">システム プロパティの更新</span><span class="sxs-lookup"><span data-stu-id="85d82-123">Update System Properties</span></span>|  
|<span data-ttu-id="85d82-124">ロールの管理</span><span class="sxs-lookup"><span data-stu-id="85d82-124">Manage roles</span></span>|<span data-ttu-id="85d82-125">ロールの作成</span><span class="sxs-lookup"><span data-stu-id="85d82-125">Create Roles</span></span><br /><br /> <span data-ttu-id="85d82-126">ロールの削除</span><span class="sxs-lookup"><span data-stu-id="85d82-126">Delete Roles</span></span><br /><br /> <span data-ttu-id="85d82-127">ロールのプロパティの読み取り</span><span class="sxs-lookup"><span data-stu-id="85d82-127">Read Role Properties</span></span><br /><br /> <span data-ttu-id="85d82-128">ロールのプロパティの更新</span><span class="sxs-lookup"><span data-stu-id="85d82-128">Update Role Properties</span></span>|  
|<span data-ttu-id="85d82-129">共有スケジュールの管理</span><span class="sxs-lookup"><span data-stu-id="85d82-129">Manage shared schedules</span></span>|<span data-ttu-id="85d82-130">スケジュールの作成</span><span class="sxs-lookup"><span data-stu-id="85d82-130">Create Schedules</span></span>|  
|<span data-ttu-id="85d82-131">レポート サーバーのセキュリティを管理</span><span class="sxs-lookup"><span data-stu-id="85d82-131">Manage report server security</span></span>|<span data-ttu-id="85d82-132">システムのセキュリティ ポリシーの読み取り</span><span class="sxs-lookup"><span data-stu-id="85d82-132">Read System Security Policies</span></span><br /><br /> <span data-ttu-id="85d82-133">システムのセキュリティ ポリシーの更新</span><span class="sxs-lookup"><span data-stu-id="85d82-133">Update System Security Policies</span></span>|  
|<span data-ttu-id="85d82-134">レポート サーバーのプロパティを表示</span><span class="sxs-lookup"><span data-stu-id="85d82-134">View report server properties</span></span>|<span data-ttu-id="85d82-135">システム プロパティの読み取り</span><span class="sxs-lookup"><span data-stu-id="85d82-135">Read System Properties</span></span>|  
|<span data-ttu-id="85d82-136">共有スケジュールの表示</span><span class="sxs-lookup"><span data-stu-id="85d82-136">View shared schedules</span></span>|<span data-ttu-id="85d82-137">スケジュールの読み取り</span><span class="sxs-lookup"><span data-stu-id="85d82-137">Read Schedules</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="85d82-138">参照</span><span class="sxs-lookup"><span data-stu-id="85d82-138">See Also</span></span>  
 [<span data-ttu-id="85d82-139">ネイティブ モードのレポート サーバーに対する権限の許可</span><span class="sxs-lookup"><span data-stu-id="85d82-139">Granting Permissions on a Native Mode Report Server</span></span>](granting-permissions-on-a-native-mode-report-server.md)  
  
  
