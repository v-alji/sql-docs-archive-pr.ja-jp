---
title: パブリッシャー情報、[サブスクリプションウォッチリスト] (トランザクションパブリケーション、SQL Server 2005 以降) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.publisherinfo.subscriptionssummary.tran.f1
ms.assetid: 6bc64ddb-5c86-4681-a391-77fc1d3c4e6e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: bf6d151b75bca1dbfd2e5ad8f7601fb1002e84be
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630898"
---
# <a name="publisher-information-subscription-watch-list-transactional-publication-sql-server-2005-and-later"></a><span data-ttu-id="2b938-102">パブリッシャー情報、[サブスクリプション ウォッチ リスト] (トランザクション パブリケーション、SQL Server 2005 以降)</span><span class="sxs-lookup"><span data-stu-id="2b938-102">Publisher Information, Subscription Watch List (Transactional Publication, SQL Server 2005 and Later)</span></span>
  <span data-ttu-id="2b938-103">SQL Server 2005 以降を実行しているディストリビューターでは、 **[サブスクリプション ウォッチ リスト]** タブを使用できます。このタブは、選択されているパブリッシャーで使用できるすべてのパブリケーションのサブスクリプションについて情報を表示するために用意されています。</span><span class="sxs-lookup"><span data-stu-id="2b938-103">The **Subscription Watch List** tab is available for Distributors running SQL Server 2005 and later versions; it is intended to display information on subscriptions from all publications available at the selected Publisher.</span></span> <span data-ttu-id="2b938-104">サブスクリプションの一覧にフィルターをかけて、エラー、警告、および動作に問題があるサブスクリプションを確認できます。</span><span class="sxs-lookup"><span data-stu-id="2b938-104">You can filter the list of subscriptions to see errors, warnings, and any poorly performing subscriptions.</span></span> <span data-ttu-id="2b938-105">このタブは、パブリッシャーにおけるすべてのレプリケーション動作を管理者が一元的に監視できる場所です。レプリケーション モニターは、選択されているレプリケーションの種類と **[表示]** ボックスで選択されたオプションに基づいて、注意が必要なすべてのサブスクリプションを表示します。</span><span class="sxs-lookup"><span data-stu-id="2b938-105">This tab provides a single location for an administrator to monitor all replication activity at a Publisher: Replication Monitor displays all subscriptions that require attention, based on the selected replication type and on the option chosen in the **Show** drop-down list box.</span></span> <span data-ttu-id="2b938-106">このタブに表示されるアイテムは現在の状態およびパフォーマンスに基づいているので、現時点での **[表示]** ボックスのオプションに一致する場合にのみ、このページにサブスクリプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2b938-106">Because the items displayed on this tab are based on current status and performance, subscriptions are displayed on this page only if they match the option in the **Show** list box at the current time.</span></span>  
  
## <a name="options"></a><span data-ttu-id="2b938-107">オプション</span><span class="sxs-lookup"><span data-stu-id="2b938-107">Options</span></span>  
 <span data-ttu-id="2b938-108">サブスクリプションに関する詳細情報やタスクを調べるには、そのサブスクリプションの行を右クリックし、ショートカット メニューのオプションをクリックします。</span><span class="sxs-lookup"><span data-stu-id="2b938-108">For more detailed information and tasks related to a subscription, right-click the row for that subscription, and then click an option on the shortcut menu.</span></span> <span data-ttu-id="2b938-109">グリッドにデータを表示する方法を変更するには、グリッドを右クリックし、次のいずれかのオプションをクリックします。</span><span class="sxs-lookup"><span data-stu-id="2b938-109">To change the way that the grid displays data, right-click the grid, and then click one of the following options:</span></span>  
  
-   <span data-ttu-id="2b938-110">**[並べ替え]** : **[列の並べ替え]** ダイアログ ボックスで、1 つ以上の列を基準にして並べ替えを行います。</span><span class="sxs-lookup"><span data-stu-id="2b938-110">**Sort**: Sort on one or more columns in the **Sort Columns** dialog box.</span></span>  
  
-   <span data-ttu-id="2b938-111">**[表示する列の選択]** : **[列の選択]** ダイアログ ボックスで、表示する列とその表示順序を選択します。</span><span class="sxs-lookup"><span data-stu-id="2b938-111">**Choose Columns to Show**: Select which columns to display and the order in which to display them in the **Choose Columns** dialog box.</span></span>  
  
-   <span data-ttu-id="2b938-112">**[フィルター]** : **[フィルターの設定]** ダイアログ ボックスで、列の値に基づいてグリッドの行をフィルター選択します。</span><span class="sxs-lookup"><span data-stu-id="2b938-112">**Filter**: Filter rows in the grid based on column values in the **Filter Settings** dialog box.</span></span>  
  
-   <span data-ttu-id="2b938-113">**[フィルターのクリア]** : グリッドのフィルター設定をすべてクリアします。</span><span class="sxs-lookup"><span data-stu-id="2b938-113">**Clear Filter**: Clear any filter settings for the grid.</span></span>  
  
 <span data-ttu-id="2b938-114">フィルター設定は各グリッドに固有です。</span><span class="sxs-lookup"><span data-stu-id="2b938-114">Filter settings are specific to each grid.</span></span> <span data-ttu-id="2b938-115">列の選択と並べ替えは、各パブリッシャーのパブリケーション グリッドなど、同じ種類のすべてのグリッドに適用されます。</span><span class="sxs-lookup"><span data-stu-id="2b938-115">Column selection and sorting are applied to all grids of the same type, such as the publications grid for each Publisher.</span></span>  
  
 <span data-ttu-id="2b938-116">**[トランザクション サブスクリプションの表示]**</span><span class="sxs-lookup"><span data-stu-id="2b938-116">**Show Transactional Subscriptions**</span></span>  
 <span data-ttu-id="2b938-117">選択したパブリッシャーに対して表示するサブスクリプションの種類 (トランザクション、スナップショット、またはマージ) を選択します。</span><span class="sxs-lookup"><span data-stu-id="2b938-117">Select the type of subscriptions (transactional, snapshot, or merge) to display for the selected Publisher.</span></span>  
  
 <span data-ttu-id="2b938-118">**[表示]**</span><span class="sxs-lookup"><span data-stu-id="2b938-118">**Show**</span></span>  
 <span data-ttu-id="2b938-119">サブスクリプション状態を選択すると、選択した種類の状態のサブスクリプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2b938-119">Select the subscription states to display for the selected subscription type.</span></span> <span data-ttu-id="2b938-120">たとえば、エラーを含むサブスクリプションのみを表示するように設定できます。</span><span class="sxs-lookup"><span data-stu-id="2b938-120">For example, you can select to display only those subscriptions that have an error.</span></span>  
  
 <span data-ttu-id="2b938-121">**状態**</span><span class="sxs-lookup"><span data-stu-id="2b938-121">**Status**</span></span>  
 <span data-ttu-id="2b938-122">各サブスクリプションの状態です。これは、ディストリビューション エージェントまたはログ リーダー エージェントの状態により決まります (より優先度の高い状態が表示されます。キュー更新サブスクリプションが使用されている場合、この状態はキュー リーダー エージェントによって決まる場合もあります)。</span><span class="sxs-lookup"><span data-stu-id="2b938-122">The status of each subscription, which is determined by the status of the Distribution Agent or the Log Reader Agent (the higher priority status is displayed; the status can also be determined by the Queue Reader Agent if queued updating subscriptions are used).</span></span>  
  
 <span data-ttu-id="2b938-123">既定では、サブスクリプションの情報を表示するグリッドは **[状態]** 列の順序で並べられています (同じ状態のサブスクリプションは、 **[パフォーマンス]** 列の順序で並べられています)。</span><span class="sxs-lookup"><span data-stu-id="2b938-123">By default, the grid containing subscription information is sorted by the **Status** column (and then sorted by the **Performance** column for those subscriptions with the same status).</span></span> <span data-ttu-id="2b938-124">表示される状態の値と、その値の並べ替え順 (たとえば、エラーは常にグリッドの上部に表示されます) を次に示します。</span><span class="sxs-lookup"><span data-stu-id="2b938-124">The following list shows the possible status values and the sort order for the values (for example, errors are always shown at the top of the grid).</span></span>  
  
-   <span data-ttu-id="2b938-125">エラー</span><span class="sxs-lookup"><span data-stu-id="2b938-125">Error</span></span>  
  
-   <span data-ttu-id="2b938-126">[パフォーマンス クリティカル]</span><span class="sxs-lookup"><span data-stu-id="2b938-126">Performance critical</span></span>  
  
-   <span data-ttu-id="2b938-127">まもなく期限切れ/期限切れ</span><span class="sxs-lookup"><span data-stu-id="2b938-127">Expiring soon/Expired</span></span>  
  
-   <span data-ttu-id="2b938-128">[初期化されていないサブスクリプション]</span><span class="sxs-lookup"><span data-stu-id="2b938-128">Uninitialized subscription</span></span>  
  
-   <span data-ttu-id="2b938-129">[失敗したコマンドの再試行]</span><span class="sxs-lookup"><span data-stu-id="2b938-129">Retrying failed command</span></span>  
  
-   <span data-ttu-id="2b938-130">停止中</span><span class="sxs-lookup"><span data-stu-id="2b938-130">Not Running</span></span>  
  
-   <span data-ttu-id="2b938-131">実行中</span><span class="sxs-lookup"><span data-stu-id="2b938-131">Running</span></span>  
  
 <span data-ttu-id="2b938-132">特定のサブスクリプションが複数の状態である場合に表示される値も、並べ替え順によって決まります。</span><span class="sxs-lookup"><span data-stu-id="2b938-132">The sort order also determines which value is displayed if a given subscription is in more than one state.</span></span> <span data-ttu-id="2b938-133">たとえば、サブスクリプションにエラーがあり、まもなく期限切れになる場合、 **[状態]** 列には **[エラー]** と表示されます。</span><span class="sxs-lookup"><span data-stu-id="2b938-133">For example, if a subscription has an error and is expiring soon, the **Status** column displays **Error**.</span></span>  
  
 <span data-ttu-id="2b938-134">状態値 **[パフォーマンス クリティカル]** 、 **[まもなく期限切れ/期限切れ]** 、および **[初期化されていないサブスクリプション]** は警告です。</span><span class="sxs-lookup"><span data-stu-id="2b938-134">The status values **Performance critical**, **Expiring soon/Expired**, and **Uninitialized subscription** are warnings.</span></span> <span data-ttu-id="2b938-135">警告が表示される場合、 **[状態]** 列にはエージェントが実行中かどうかも表示されます。</span><span class="sxs-lookup"><span data-stu-id="2b938-135">When a warning is displayed, the **Status** column also displays if an agent is running.</span></span> <span data-ttu-id="2b938-136">たとえば、 **[実行中]、[パフォーマンス クリティカル]** という形で状態が表示されます。</span><span class="sxs-lookup"><span data-stu-id="2b938-136">For example, the status could be **Running, Performance critical**.</span></span>  
  
 <span data-ttu-id="2b938-137">状態値 **[パフォーマンス クリティカル]** および **[まもなく期限切れ/期限切れ]** は、しきい値が設定されている場合のみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="2b938-137">The status values **Performance critical** and **Expiring soon/Expired** are displayed only if thresholds are set.</span></span> <span data-ttu-id="2b938-138">パフォーマンスの測定としきい値の設定については、「[Monitor Performance with Replication Monitor](monitor/monitor-performance-with-replication-monitor.md)」 (レプリケーション モニターを使用したパフォーマンスの監視) と「[レプリケーション モニターのしきい値と警告の設定](monitor/set-thresholds-and-warnings-in-replication-monitor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2b938-138">For information about performance measurements and setting thresholds, see [Monitor Performance with Replication Monitor](monitor/monitor-performance-with-replication-monitor.md) and [Set Thresholds and Warnings in Replication Monitor](monitor/set-thresholds-and-warnings-in-replication-monitor.md).</span></span>  
  
 <span data-ttu-id="2b938-139">**サブスクリプション**</span><span class="sxs-lookup"><span data-stu-id="2b938-139">**Subscription**</span></span>  
 <span data-ttu-id="2b938-140">各サブスクリプションの名前です。 *SubscriberName: SubscriptionDatabaseName*という形式になります。</span><span class="sxs-lookup"><span data-stu-id="2b938-140">The name of each subscription, in the form: *SubscriberName: SubscriptionDatabaseName*.</span></span>  
  
 <span data-ttu-id="2b938-141">**パブリケーション**</span><span class="sxs-lookup"><span data-stu-id="2b938-141">**Publication**</span></span>  
 <span data-ttu-id="2b938-142">サブスクリプションと同期するパブリケーションの名前です。 *PublicationDatabaseName: PublicationName*という形式になります。</span><span class="sxs-lookup"><span data-stu-id="2b938-142">The name of the publication with which a subscription synchronizes, in the form: *PublicationDatabaseName: PublicationName*.</span></span>  
  
 <span data-ttu-id="2b938-143">**パフォーマンス**</span><span class="sxs-lookup"><span data-stu-id="2b938-143">**Performance**</span></span>  
 <span data-ttu-id="2b938-144">各サブスクリプションのパフォーマンス評価は、レプリケーション モニターにより取得され、履歴パフォーマンスに反映されていない、最も新しい計測値に基づいています。</span><span class="sxs-lookup"><span data-stu-id="2b938-144">The performance rating for each subscription is based on the most recent measurements taken by Replication Monitor and does not reflect historical performance.</span></span> <span data-ttu-id="2b938-145">パフォーマンスは、パフォーマンスしきい値が定義されているパブリケーションへのサブスクリプションについてのみ計測されます。パブリケーションにパフォーマンスしきい値が定義されていない場合、この列には **[有効になっていません]** と表示されます。</span><span class="sxs-lookup"><span data-stu-id="2b938-145">Performance is measured for subscriptions to publications that have performance thresholds defined; if performance thresholds are not defined for a publication, this column displays **Not enabled**.</span></span> <span data-ttu-id="2b938-146">パフォーマンス評価は、次のいずれかの値になります。</span><span class="sxs-lookup"><span data-stu-id="2b938-146">The performance rating is one of the following values:</span></span>  
  
-   <span data-ttu-id="2b938-147">[非常に良い]</span><span class="sxs-lookup"><span data-stu-id="2b938-147">Excellent</span></span>  
  
-   <span data-ttu-id="2b938-148">[良い]</span><span class="sxs-lookup"><span data-stu-id="2b938-148">Good</span></span>  
  
-   <span data-ttu-id="2b938-149">[普通]</span><span class="sxs-lookup"><span data-stu-id="2b938-149">Fair</span></span>  
  
-   <span data-ttu-id="2b938-150">悪い</span><span class="sxs-lookup"><span data-stu-id="2b938-150">Poor</span></span>  
  
-   <span data-ttu-id="2b938-151">Critical</span><span class="sxs-lookup"><span data-stu-id="2b938-151">Critical</span></span>  
  
 <span data-ttu-id="2b938-152">パフォーマンスが [重大] の場合、 **[状態]** 列に **[パフォーマンス クリティカル]** と表示されます。</span><span class="sxs-lookup"><span data-stu-id="2b938-152">If performance is critical, **Performance Critical** is displayed in the **Status** column.</span></span> <span data-ttu-id="2b938-153">パフォーマンス評価の定義方法とパフォーマンスしきい値の設定方法については、「[Monitor Performance with Replication Monitor](monitor/monitor-performance-with-replication-monitor.md)」 (レプリケーション モニターを使用したパフォーマンスの監視) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2b938-153">For more information about how performance ratings are defined and how performance thresholds are set, see [Monitor Performance with Replication Monitor](monitor/monitor-performance-with-replication-monitor.md).</span></span>  
  
 <span data-ttu-id="2b938-154">**待機時間**</span><span class="sxs-lookup"><span data-stu-id="2b938-154">**Latency**</span></span>  
 <span data-ttu-id="2b938-155">トランザクションがパブリッシャー側でコミットされたときから、サブスクライバー側で対応するトランザクションがコミットされるまでに経過した時間の平均値です。</span><span class="sxs-lookup"><span data-stu-id="2b938-155">The average amount of time that elapses between a transaction being committed at the Publisher and the corresponding transaction being committed at the Subscriber.</span></span> <span data-ttu-id="2b938-156">表示される待機時間は、レプリケーション モニターにより取得された最新の計測値に基づいています。</span><span class="sxs-lookup"><span data-stu-id="2b938-156">The latency displayed is based on the most recent measurements taken by Replication Monitor.</span></span> <span data-ttu-id="2b938-157">待機時間の計測の詳細については、「[トランザクション レプリケーションの待機時間の計測および接続の検証](monitor/measure-latency-and-validate-connections-for-transactional-replication.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2b938-157">For more information about measuring latency, see [Measure Latency and Validate Connections for Transactional Replication](monitor/measure-latency-and-validate-connections-for-transactional-replication.md).</span></span>  
  
 <span data-ttu-id="2b938-158">**[最後の同期]**</span><span class="sxs-lookup"><span data-stu-id="2b938-158">**Last Synchronization**</span></span>  
 <span data-ttu-id="2b938-159">ディストリビューション エージェントが最後に実行された時刻です。</span><span class="sxs-lookup"><span data-stu-id="2b938-159">The time when the Distribution Agent last ran.</span></span> <span data-ttu-id="2b938-160">同期が進行中の場合は、 **[実行中]** と表示されます。</span><span class="sxs-lookup"><span data-stu-id="2b938-160">If synchronization is in progress, **In progress** is displayed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b938-161">参照</span><span class="sxs-lookup"><span data-stu-id="2b938-161">See Also</span></span>  
 <span data-ttu-id="2b938-162">[レプリケーション モニターの開始](monitor/start-the-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="2b938-162">[Start the Replication Monitor](monitor/start-the-replication-monitor.md) </span></span>  
 <span data-ttu-id="2b938-163">[レプリケーション モニターを使用して情報を表示し、タスクを実行する](monitor/view-information-and-perform-tasks-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="2b938-163">[View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md) </span></span>  
 [<span data-ttu-id="2b938-164">レプリケーションの監視</span><span class="sxs-lookup"><span data-stu-id="2b938-164">Monitoring Replication</span></span>](monitoring-replication.md)  
  
  
