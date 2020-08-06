---
title: SQL Server モニターの概要 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql12.swb.sqlservermonitor.main.f1
helpviewer_keywords:
- SQL Server Monitor [SQL Server]
ms.assetid: 048ae16d-31c3-489a-9f1e-1400a3bacd39
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ab90186ed493e616e672cfacf881fd61be166f88
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632091"
---
# <a name="sql-server-monitor-overview"></a><span data-ttu-id="a22da-102">SQL Server モニターの概要</span><span class="sxs-lookup"><span data-stu-id="a22da-102">SQL Server Monitor Overview</span></span>
  <span data-ttu-id="a22da-103">SQL Server モニターでは、監視機能を実行するのではなく、監視を行うモジュールをホストします。</span><span class="sxs-lookup"><span data-stu-id="a22da-103">SQL Server Monitor does not perform monitoring functions, but it hosts modules that do.</span></span> <span data-ttu-id="a22da-104">SQL Server モニターのモジュールには、レプリケーション モニターやデータベース ミラーリング モニターが含まれます。</span><span class="sxs-lookup"><span data-stu-id="a22da-104">The SQL Server Monitor modules include Replication Monitor and Database Mirroring Monitor.</span></span>  
  
 <span data-ttu-id="a22da-105">これらのモジュールのいずれかを使用するには、 **[実行]** メニューから該当するモジュールを選択します。</span><span class="sxs-lookup"><span data-stu-id="a22da-105">To use one of these modules, select that module on the **Go** menu.</span></span> <span data-ttu-id="a22da-106">現在選択されているモジュールには、ナビゲーション ペインと詳細ペインの内容、詳細ペインでのユーザーとのやり取り、および内容と状態に関するクエリがあります。</span><span class="sxs-lookup"><span data-stu-id="a22da-106">The currently selected module owns the content of the navigation and detail panes, user interaction in the detail panes, and the queries for content and status.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a22da-107">これらのモニターの詳細については、「 [レプリケーションの監視](../../relational-databases/replication/monitoring-replication.md) 」および「 [データベース ミラーリングの監視 &#40;SQL Server&#41;](../database-mirroring/database-mirroring-sql-server.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a22da-107">For more information about these monitors, see [Monitoring Replication](../../relational-databases/replication/monitoring-replication.md) and [Monitoring Database Mirroring &#40;SQL Server&#41;](../database-mirroring/database-mirroring-sql-server.md).</span></span>  
  
## <a name="permissions"></a><span data-ttu-id="a22da-108">アクセス許可</span><span class="sxs-lookup"><span data-stu-id="a22da-108">Permissions</span></span>  
  
-   <span data-ttu-id="a22da-109">レプリケーション モニター</span><span class="sxs-lookup"><span data-stu-id="a22da-109">Replication Monitor</span></span>  
  
     <span data-ttu-id="a22da-110">レプリケーションを監視するためには、ディストリビューターで **sysadmin** 固定サーバー ロールのメンバーか、ディストリビューション データベースの **replmonitor** 固定データベース ロールのメンバーであることが必要です。</span><span class="sxs-lookup"><span data-stu-id="a22da-110">To monitor replication, you must be a member of the **sysadmin** fixed server role at the Distributor or a member of the **replmonitor** fixed database role in the distribution database.</span></span> <span data-ttu-id="a22da-111">システム管理者は、 **replmonitor** ロールに任意のユーザーを追加することが可能で、これによりユーザーがレプリケーション モニターでレプリケーションの動作状況を表示できるようになります。ただし、レプリケーションを管理することはできません。</span><span class="sxs-lookup"><span data-stu-id="a22da-111">A system administrator can add any user to the **replmonitor** role, which allows that user to view replication activity in Replication Monitor; however, the user cannot administer replication.</span></span>  
  
-   <span data-ttu-id="a22da-112">データベース ミラーリング モニター (Database Mirroring Monitor)</span><span class="sxs-lookup"><span data-stu-id="a22da-112">Database Mirroring Monitor</span></span>  
  
     <span data-ttu-id="a22da-113">データベース ミラーリングを監視するには、 **sysadmin** 固定サーバー ロールのメンバーか、サーバー インスタンスの **dbm_monitor** 固定データベース ロールのメンバーであることが必要です。</span><span class="sxs-lookup"><span data-stu-id="a22da-113">To monitor database mirroring, you must be a member of either the **sysadmin** fixed server role or the **dbm_monitor** fixed database role on the server instance.</span></span> <span data-ttu-id="a22da-114">1 つのパートナー サーバー インスタンスだけが **sysadmin** または **dbm_monitor** のメンバーの場合、モニターは、該当するパートナーにのみ接続でき、他のパートナーからは情報を取得できません。</span><span class="sxs-lookup"><span data-stu-id="a22da-114">If you are a member of **sysadmin** or **dbm_monitor** on only one of the partner server instances, the monitor can connect only to that partner; the monitor cannot retrieve information from the other partner.</span></span> <span data-ttu-id="a22da-115">詳細については、「 [データベース ミラーリング モニターの概要](../database-mirroring/database-mirroring-monitor-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a22da-115">For more information, see [Database Mirroring Monitor Overview](../database-mirroring/database-mirroring-monitor-overview.md).</span></span>  
  
## <a name="menu-options"></a><span data-ttu-id="a22da-116">メニュー オプション</span><span class="sxs-lookup"><span data-stu-id="a22da-116">Menu Options</span></span>  
 <span data-ttu-id="a22da-117">SQL Server モニターには、SQL Server モニターに関連するコマンドを含むメニューがあります。</span><span class="sxs-lookup"><span data-stu-id="a22da-117">SQL Server Monitor has a menu that contains commands that pertain to SQL Server Monitor.</span></span> <span data-ttu-id="a22da-118">このメニューには、選択されたモジュールのコマンドが設定されている場合もあります。</span><span class="sxs-lookup"><span data-stu-id="a22da-118">This menu may also contain commands from the selected module.</span></span>  
  
 <span data-ttu-id="a22da-119">次のメニュー オプションは、SQL Server モニターに関するものです。</span><span class="sxs-lookup"><span data-stu-id="a22da-119">The following menu options pertain to SQL Server Monitor.</span></span>  
  
 <span data-ttu-id="a22da-120">**[最近使ったファイル]**</span><span class="sxs-lookup"><span data-stu-id="a22da-120">**File**</span></span>  
 <span data-ttu-id="a22da-121">このメニューには、 **[終了]** が含まれます。</span><span class="sxs-lookup"><span data-stu-id="a22da-121">This menu contains the **Exit** command.</span></span>  
  
 <span data-ttu-id="a22da-122">**操作**</span><span class="sxs-lookup"><span data-stu-id="a22da-122">**Action**</span></span>  
 <span data-ttu-id="a22da-123">ナビゲーション ツリーで選択されたノードのコンテキスト メニューが含まれます。</span><span class="sxs-lookup"><span data-stu-id="a22da-123">Contains the context menu of the node selected in the navigation tree.</span></span>  
  
 <span data-ttu-id="a22da-124">**Go**</span><span class="sxs-lookup"><span data-stu-id="a22da-124">**Go**</span></span>  
 <span data-ttu-id="a22da-125">監視するコンポーネントの一覧が含まれます。</span><span class="sxs-lookup"><span data-stu-id="a22da-125">Contains a list of monitoring components:</span></span>  
  
-   <span data-ttu-id="a22da-126">データベース ミラーリング</span><span class="sxs-lookup"><span data-stu-id="a22da-126">Database Mirroring</span></span>  
  
-   <span data-ttu-id="a22da-127">レプリケーション</span><span class="sxs-lookup"><span data-stu-id="a22da-127">Replication</span></span>  
  
 <span data-ttu-id="a22da-128">**SQL Server Management Studio を使用してデータベース ミラーリングを監視するには**</span><span class="sxs-lookup"><span data-stu-id="a22da-128">**To use SQL Server Management Studio to monitor database mirroring**</span></span>  
  
-   [<span data-ttu-id="a22da-129">データベース ミラーリング モニターの起動 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="a22da-129">Start Database Mirroring Monitor &#40;SQL Server Management Studio&#41;</span></span>](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md)  
  
## <a name="see-also"></a><span data-ttu-id="a22da-130">参照</span><span class="sxs-lookup"><span data-stu-id="a22da-130">See Also</span></span>  
 [<span data-ttu-id="a22da-131">データベース ミラーリングの監視 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a22da-131">Monitoring Database Mirroring &#40;SQL Server&#41;</span></span>](../database-mirroring/database-mirroring-sql-server.md)  
  
  
