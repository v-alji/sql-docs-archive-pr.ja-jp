---
title: パブリッシャー情報、[サブスクリプションウォッチリスト] (スナップショットパブリケーション、SQL Server 2005 以降) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.publisherinfo.subscriptionssummary.snapshot.f1
ms.assetid: 2ebeee62-7f54-4c77-9d37-15708bc5cc23
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ea44958c81465570c036ab7dd83247fb55652f1f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716254"
---
# <a name="publisher-information-subscription-watch-list-snapshot-publication-sql-server-2005-and-later"></a><span data-ttu-id="2b288-102">パブリッシャー情報、[サブスクリプション ウォッチ リスト] (スナップショット パブリケーション、SQL Server 2005 以降)</span><span class="sxs-lookup"><span data-stu-id="2b288-102">Publisher Information, Subscription Watch List (Snapshot Publication, SQL Server 2005 and Later)</span></span>
  <span data-ttu-id="2b288-103">**以降を実行しているディストリビューターでは、** [サブスクリプション ウォッチ リスト] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] タブを使用できます。このタブは、選択されているパブリッシャーで使用できるすべてのパブリケーションのサブスクリプションについて情報を表示するために用意されています。</span><span class="sxs-lookup"><span data-stu-id="2b288-103">The **Subscription Watch List** tab is available for Distributors running [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions; it is intended to display information on subscriptions from all publications available at the selected Publisher.</span></span> <span data-ttu-id="2b288-104">サブスクリプションの一覧にフィルターをかけて、エラー、警告、および動作に問題があるサブスクリプションを確認できます。</span><span class="sxs-lookup"><span data-stu-id="2b288-104">You can filter the list of subscriptions to see errors, warnings, and any poorly performing subscriptions.</span></span> <span data-ttu-id="2b288-105">このタブは、パブリッシャーにおけるすべてのレプリケーション動作を管理者が一元的に監視できる場所です。レプリケーション モニターは、選択されているレプリケーションの種類と **[表示]** ボックスで選択されたオプションに基づいて、注意が必要なすべてのサブスクリプションを表示します。</span><span class="sxs-lookup"><span data-stu-id="2b288-105">This tab provides a single location for an administrator to monitor all replication activity at a Publisher: Replication Monitor displays all subscriptions that require attention, based on the selected replication type and on the option chosen in the **Show** drop-down list box.</span></span> <span data-ttu-id="2b288-106">このタブに表示されるアイテムは現在の状態およびパフォーマンスに基づいているので、現時点での **[表示]** ボックスのオプションに一致する場合にのみ、このページにサブスクリプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2b288-106">Because the items displayed on this tab are based on current status and performance, subscriptions are displayed on this page only if they match the option in the **Show** list box at the current time.</span></span>  
  
## <a name="options"></a><span data-ttu-id="2b288-107">Options</span><span class="sxs-lookup"><span data-stu-id="2b288-107">Options</span></span>  
 <span data-ttu-id="2b288-108">サブスクリプションに関する詳細情報やタスクを調べるには、そのサブスクリプションの行を右クリックし、ショートカット メニューのオプションをクリックします。</span><span class="sxs-lookup"><span data-stu-id="2b288-108">For more detailed information and tasks related to a subscription, right-click the row for that subscription, and then click an option on the shortcut menu.</span></span> <span data-ttu-id="2b288-109">グリッドにデータを表示する方法を変更するには、グリッドを右クリックし、次のいずれかのオプションをクリックします。</span><span class="sxs-lookup"><span data-stu-id="2b288-109">To change the way that the grid displays data, right-click the grid, and then click one of the following options:</span></span>  
  
-   <span data-ttu-id="2b288-110">**[並べ替え]**: **[列の並べ替え]** ダイアログ ボックスで、1 つ以上の列を基準にして並べ替えを行います。</span><span class="sxs-lookup"><span data-stu-id="2b288-110">**Sort**: Sort on one or more columns in the **Sort Columns** dialog box.</span></span>  
  
-   <span data-ttu-id="2b288-111">**[表示する列の選択]**: **[列の選択]** ダイアログ ボックスで、表示する列とその表示順序を選択します。</span><span class="sxs-lookup"><span data-stu-id="2b288-111">**Choose Columns to Show**: Select which columns to display and the order in which to display them in the **Choose Columns** dialog box.</span></span>  
  
-   <span data-ttu-id="2b288-112">**[フィルター]**: **[フィルターの設定]** ダイアログ ボックスで、列の値に基づいてグリッドの行をフィルター選択します。</span><span class="sxs-lookup"><span data-stu-id="2b288-112">**Filter**: Filter rows in the grid based on column values in the **Filter Settings** dialog box.</span></span>  
  
-   <span data-ttu-id="2b288-113">**[フィルターのクリア]**: グリッドのフィルター設定をすべてクリアします。</span><span class="sxs-lookup"><span data-stu-id="2b288-113">**Clear Filter**: Clear any filter settings for the grid.</span></span>  
  
 <span data-ttu-id="2b288-114">フィルター設定は各グリッドに固有です。</span><span class="sxs-lookup"><span data-stu-id="2b288-114">Filter settings are specific to each grid.</span></span> <span data-ttu-id="2b288-115">列の選択と並べ替えは、各パブリッシャーのパブリケーション グリッドなど、同じ種類のすべてのグリッドに適用されます。</span><span class="sxs-lookup"><span data-stu-id="2b288-115">Column selection and sorting are applied to all grids of the same type, such as the publications grid for each Publisher.</span></span>  
  
 <span data-ttu-id="2b288-116">**[スナップショット サブスクリプションの表示]**</span><span class="sxs-lookup"><span data-stu-id="2b288-116">**Show Snapshot Subscriptions**</span></span>  
 <span data-ttu-id="2b288-117">選択したパブリッシャーに対して表示するサブスクリプションの種類 (トランザクション、スナップショット、またはマージ) を選択します。</span><span class="sxs-lookup"><span data-stu-id="2b288-117">Select the type of subscriptions (transactional, snapshot, or merge) to display for the selected Publisher.</span></span>  
  
 <span data-ttu-id="2b288-118">**表示**</span><span class="sxs-lookup"><span data-stu-id="2b288-118">**Show**</span></span>  
 <span data-ttu-id="2b288-119">サブスクリプション状態を選択すると、選択した種類の状態のサブスクリプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2b288-119">Select the subscription states to display for the selected subscription type.</span></span> <span data-ttu-id="2b288-120">たとえば、エラーを含むサブスクリプションのみを表示するように設定できます。</span><span class="sxs-lookup"><span data-stu-id="2b288-120">For example, you can select to display only those subscriptions that have an error.</span></span>  
  
 <span data-ttu-id="2b288-121">**状態**</span><span class="sxs-lookup"><span data-stu-id="2b288-121">**Status**</span></span>  
 <span data-ttu-id="2b288-122">各サブスクリプションの状態です。スナップショット エージェントまたはディストリビューション エージェントの状態 (より高い優先度の状態が表示されます) によって決定されます。</span><span class="sxs-lookup"><span data-stu-id="2b288-122">The status of each subscription, which is determined by the status of the Snapshot Agent or the Distribution Agent (the higher priority status is displayed).</span></span>  
  
 <span data-ttu-id="2b288-123">既定では、サブスクリプション情報を表示するグリッドは **[状態]** 列の順序で並べられています。</span><span class="sxs-lookup"><span data-stu-id="2b288-123">By default, the grid containing subscription information is sorted by the **Status** column.</span></span> <span data-ttu-id="2b288-124">表示される状態の値と、その値の並べ替え順 (たとえば、エラーは常にグリッドの上部に表示されます) を次に示します。</span><span class="sxs-lookup"><span data-stu-id="2b288-124">The following list shows the possible status values and the sort order for the values (for example, errors are always shown at the top of the grid).</span></span>  
  
-   <span data-ttu-id="2b288-125">エラー</span><span class="sxs-lookup"><span data-stu-id="2b288-125">Error</span></span>  
  
-   <span data-ttu-id="2b288-126">まもなく期限切れ/期限切れ</span><span class="sxs-lookup"><span data-stu-id="2b288-126">Expiring soon/Expired</span></span>  
  
-   <span data-ttu-id="2b288-127">[初期化されていないサブスクリプション]</span><span class="sxs-lookup"><span data-stu-id="2b288-127">Uninitialized subscription</span></span>  
  
-   <span data-ttu-id="2b288-128">[失敗したコマンドの再試行]</span><span class="sxs-lookup"><span data-stu-id="2b288-128">Retrying failed command</span></span>  
  
-   <span data-ttu-id="2b288-129">[同期中]</span><span class="sxs-lookup"><span data-stu-id="2b288-129">Synchronizing</span></span>  
  
-   <span data-ttu-id="2b288-130">[同期されていません]</span><span class="sxs-lookup"><span data-stu-id="2b288-130">Not synchronizing</span></span>  
  
 <span data-ttu-id="2b288-131">特定のサブスクリプションが複数の状態である場合に表示される値も、並べ替え順によって決まります。</span><span class="sxs-lookup"><span data-stu-id="2b288-131">The sort order also determines which value is displayed if a given subscription is in more than one state.</span></span> <span data-ttu-id="2b288-132">たとえば、サブスクリプションにエラーがあり、まもなく期限切れになる場合、 **[状態]** 列には **[エラー]** と表示されます。</span><span class="sxs-lookup"><span data-stu-id="2b288-132">For example, if a subscription has an error and is expiring soon, the **Status** column displays **Error**.</span></span>  
  
 <span data-ttu-id="2b288-133">状態値 **[まもなく期限切れ/期限切れ]** および **[初期化されていないサブスクリプション]** は警告です。</span><span class="sxs-lookup"><span data-stu-id="2b288-133">The status values **Expiring soon/Expired** and **Uninitialized subscription** are warnings.</span></span> <span data-ttu-id="2b288-134">警告が表示される場合、 **[状態]** 列にはエージェントが実行中かどうかも表示されます。</span><span class="sxs-lookup"><span data-stu-id="2b288-134">When a warning is displayed, the **Status** column also displays if an agent is running.</span></span> <span data-ttu-id="2b288-135">たとえば、 **[実行中]、[まもなく期限切れ/期限切れ]** という形式で状態が表示されます。</span><span class="sxs-lookup"><span data-stu-id="2b288-135">For example, the status could be **Running, Expiring soon/Expired**.</span></span>  
  
 <span data-ttu-id="2b288-136">状態値 **[まもなく期限切れ/期限切れ]** は、しきい値が設定されている場合のみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="2b288-136">The status value **Expiring soon/Expired** is displayed only if a threshold is set.</span></span> <span data-ttu-id="2b288-137">しきい値の設定方法の詳細については、「[レプリケーション モニターのしきい値と警告の設定](monitor/set-thresholds-and-warnings-in-replication-monitor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2b288-137">For information on setting thresholds, see [Set Thresholds and Warnings in Replication Monitor](monitor/set-thresholds-and-warnings-in-replication-monitor.md).</span></span>  
  
 <span data-ttu-id="2b288-138">**サブスクリプション**</span><span class="sxs-lookup"><span data-stu-id="2b288-138">**Subscription**</span></span>  
 <span data-ttu-id="2b288-139">各サブスクリプションの名前です。 *SubscriberName: SubscriptionDatabaseName*という形式になります。</span><span class="sxs-lookup"><span data-stu-id="2b288-139">The name of each subscription, in the form: *SubscriberName: SubscriptionDatabaseName*.</span></span>  
  
 <span data-ttu-id="2b288-140">**Publication**</span><span class="sxs-lookup"><span data-stu-id="2b288-140">**Publication**</span></span>  
 <span data-ttu-id="2b288-141">サブスクリプションと同期するパブリケーションの名前です。 *PublicationDatabaseName: PublicationName*という形式になります。</span><span class="sxs-lookup"><span data-stu-id="2b288-141">The name of the publication with which a subscription synchronizes, in the form: *PublicationDatabaseName: PublicationName*.</span></span>  
  
 <span data-ttu-id="2b288-142">**[最後の同期]**</span><span class="sxs-lookup"><span data-stu-id="2b288-142">**Last Synchronization**</span></span>  
 <span data-ttu-id="2b288-143">ディストリビューション エージェントが最後に実行された時刻です。</span><span class="sxs-lookup"><span data-stu-id="2b288-143">The time at which the Distribution Agent last ran.</span></span> <span data-ttu-id="2b288-144">同期が進行中の場合は、 **[実行中]** と表示されます。</span><span class="sxs-lookup"><span data-stu-id="2b288-144">If synchronization is in progress, **In progress** is displayed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b288-145">参照</span><span class="sxs-lookup"><span data-stu-id="2b288-145">See Also</span></span>  
 <span data-ttu-id="2b288-146">[レプリケーションモニターを開始する](monitor/start-the-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="2b288-146">[Start the Replication Monitor](monitor/start-the-replication-monitor.md) </span></span>  
 <span data-ttu-id="2b288-147">[レプリケーション モニターを使用して情報を表示し、タスクを実行する](monitor/view-information-and-perform-tasks-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="2b288-147">[View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md) </span></span>  
 [<span data-ttu-id="2b288-148">レプリケーションの監視</span><span class="sxs-lookup"><span data-stu-id="2b288-148">Monitoring Replication</span></span>](monitoring-replication.md)  
  
  
