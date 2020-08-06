---
title: パブリッシャー情報、[サブスクリプションウォッチリスト] (マージパブリケーション、SQL Server 2005 以降) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.publisherinfo.subscriptionssummary.merge.f1
ms.assetid: 4ec956bf-5cef-4377-a1d1-8c7f0107a6cb
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: cd38540533e3e663fa23eee2c651f0beb9463546
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87721284"
---
# <a name="publisher-information-subscription-watch-list-merge-publication-sql-server-2005-and-later"></a><span data-ttu-id="56bcb-102">パブリッシャー情報、[サブスクリプション ウォッチ リスト] (マージ パブリケーション、SQL Server 2005 以降)</span><span class="sxs-lookup"><span data-stu-id="56bcb-102">Publisher Information, Subscription Watch List (Merge Publication, SQL Server 2005 and Later)</span></span>
  <span data-ttu-id="56bcb-103">**以降を実行しているディストリビューターでは、** [サブスクリプション ウォッチ リスト] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] タブを使用できます。このタブは、選択されているパブリッシャーで使用できるすべてのパブリケーションのサブスクリプションについて情報を表示するために用意されています。</span><span class="sxs-lookup"><span data-stu-id="56bcb-103">The **Subscription Watch List** tab is available for Distributors running [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions; it is intended to display information on subscriptions from all publications available at the selected Publisher.</span></span> <span data-ttu-id="56bcb-104">サブスクリプションの一覧にフィルターをかけて、エラー、警告、および動作に問題があるサブスクリプションを確認できます。</span><span class="sxs-lookup"><span data-stu-id="56bcb-104">You can filter the list of subscriptions to see errors, warnings, and any poorly performing subscriptions.</span></span> <span data-ttu-id="56bcb-105">このタブは、パブリッシャーにおけるすべてのレプリケーション動作を管理者が一元的に監視できる場所です。レプリケーション モニターは、選択されているレプリケーションの種類と **[表示]** ボックスで選択されたオプションに基づいて、注意が必要なすべてのサブスクリプションを表示します。</span><span class="sxs-lookup"><span data-stu-id="56bcb-105">This tab provides a single location for an administrator to monitor all replication activity at a Publisher: Replication Monitor displays all subscriptions that require attention, based on the selected replication type and on the option chosen in the **Show** drop-down list box.</span></span> <span data-ttu-id="56bcb-106">このタブに表示されるアイテムは現在の状態およびパフォーマンスに基づいているので、現時点での **[表示]** ボックスのオプションに一致する場合にのみ、このページにサブスクリプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="56bcb-106">Because the items displayed on this tab are based on current status and performance, subscriptions are displayed on this page only if they match the option in the **Show** list box at the current time.</span></span>  
  
## <a name="options"></a><span data-ttu-id="56bcb-107">Options</span><span class="sxs-lookup"><span data-stu-id="56bcb-107">Options</span></span>  
 <span data-ttu-id="56bcb-108">サブスクリプションに関する詳細情報やタスクを調べるには、そのサブスクリプションの行を右クリックし、ショートカット メニューのオプションをクリックします。</span><span class="sxs-lookup"><span data-stu-id="56bcb-108">For more detailed information and tasks related to a subscription, right-click the row for that subscription, and then click an option on the shortcut menu.</span></span> <span data-ttu-id="56bcb-109">グリッドにデータを表示する方法を変更するには、グリッドを右クリックし、次のいずれかのオプションをクリックします。</span><span class="sxs-lookup"><span data-stu-id="56bcb-109">To change the way that the grid displays data, right-click the grid, and then click one of the following options:</span></span>  
  
-   <span data-ttu-id="56bcb-110">**[並べ替え]**: **[列の並べ替え]** ダイアログ ボックスで、1 つ以上の列を基準にして並べ替えを行います。</span><span class="sxs-lookup"><span data-stu-id="56bcb-110">**Sort**: Sort on one or more columns in the **Sort Columns** dialog box.</span></span>  
  
-   <span data-ttu-id="56bcb-111">**[表示する列の選択]**: **[列の選択]** ダイアログ ボックスで、表示する列とその表示順序を選択します。</span><span class="sxs-lookup"><span data-stu-id="56bcb-111">**Choose Columns to Show**: Select which columns to display and the order in which to display them in the **Choose Columns** dialog box.</span></span>  
  
-   <span data-ttu-id="56bcb-112">**[フィルター]**: **[フィルターの設定]** ダイアログ ボックスで、列の値に基づいてグリッドの行をフィルター選択します。</span><span class="sxs-lookup"><span data-stu-id="56bcb-112">**Filter**: Filter rows in the grid based on column values in the **Filter Settings** dialog box.</span></span>  
  
-   <span data-ttu-id="56bcb-113">**[フィルターのクリア]**: グリッドのフィルター設定をすべてクリアします。</span><span class="sxs-lookup"><span data-stu-id="56bcb-113">**Clear Filter**: Clear any filter settings for the grid.</span></span>  
  
 <span data-ttu-id="56bcb-114">フィルター設定は各グリッドに固有です。</span><span class="sxs-lookup"><span data-stu-id="56bcb-114">Filter settings are specific to each grid.</span></span> <span data-ttu-id="56bcb-115">列の選択と並べ替えは、各パブリッシャーのパブリケーション グリッドなど、同じ種類のすべてのグリッドに適用されます。</span><span class="sxs-lookup"><span data-stu-id="56bcb-115">Column selection and sorting are applied to all grids of the same type, such as the publications grid for each Publisher.</span></span>  
  
 <span data-ttu-id="56bcb-116">**[マージ サブスクリプションの表示]**</span><span class="sxs-lookup"><span data-stu-id="56bcb-116">**Show Merge Subscriptions**</span></span>  
 <span data-ttu-id="56bcb-117">選択したパブリッシャーに対して表示するサブスクリプションの種類 (トランザクション、スナップショット、またはマージ) を選択します。</span><span class="sxs-lookup"><span data-stu-id="56bcb-117">Select the type of subscriptions (transactional, snapshot, or merge) to display for the selected Publisher.</span></span>  
  
 <span data-ttu-id="56bcb-118">**表示**</span><span class="sxs-lookup"><span data-stu-id="56bcb-118">**Show**</span></span>  
 <span data-ttu-id="56bcb-119">サブスクリプション状態を選択すると、選択した種類の状態のサブスクリプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="56bcb-119">Select the subscription states to display for the selected subscription type.</span></span> <span data-ttu-id="56bcb-120">たとえば、エラーを含むサブスクリプションのみを表示するように設定できます。</span><span class="sxs-lookup"><span data-stu-id="56bcb-120">For example, you can select to display only those subscriptions that have an error.</span></span>  
  
 <span data-ttu-id="56bcb-121">**状態**</span><span class="sxs-lookup"><span data-stu-id="56bcb-121">**Status**</span></span>  
 <span data-ttu-id="56bcb-122">各サブスクリプションの状態です。これは、マージ エージェントの状態により決定されます。</span><span class="sxs-lookup"><span data-stu-id="56bcb-122">The status of each subscription, which is determined by the status of the Merge Agent.</span></span>  
  
 <span data-ttu-id="56bcb-123">既定では、サブスクリプションの情報を表示するグリッドは **[状態]** 列の順序で並べられています (同じ状態のサブスクリプションは、 **[パフォーマンス]** 列の順序で並べられています)。</span><span class="sxs-lookup"><span data-stu-id="56bcb-123">By default, the grid containing subscription information is sorted by the **Status** column (and then sorted by the **Performance** column for those subscriptions with the same status).</span></span> <span data-ttu-id="56bcb-124">表示される状態の値と、その値の並べ替え順 (たとえば、エラーは常にグリッドの上部に表示されます) を次に示します。</span><span class="sxs-lookup"><span data-stu-id="56bcb-124">The following list shows the possible status values and the sort order for the values (for example, errors are always shown at the top of the grid).</span></span>  
  
-   <span data-ttu-id="56bcb-125">エラー</span><span class="sxs-lookup"><span data-stu-id="56bcb-125">Error</span></span>  
  
-   <span data-ttu-id="56bcb-126">[パフォーマンス クリティカル]</span><span class="sxs-lookup"><span data-stu-id="56bcb-126">Performance critical</span></span>  
  
-   <span data-ttu-id="56bcb-127">[長期マージ]</span><span class="sxs-lookup"><span data-stu-id="56bcb-127">Long-running merge</span></span>  
  
-   <span data-ttu-id="56bcb-128">まもなく期限切れ/期限切れ</span><span class="sxs-lookup"><span data-stu-id="56bcb-128">Expiring soon/Expired</span></span>  
  
-   <span data-ttu-id="56bcb-129">[初期化されていないサブスクリプション]</span><span class="sxs-lookup"><span data-stu-id="56bcb-129">Uninitialized subscription</span></span>  
  
-   <span data-ttu-id="56bcb-130">[失敗したコマンドの再試行]</span><span class="sxs-lookup"><span data-stu-id="56bcb-130">Retrying failed command</span></span>  
  
-   <span data-ttu-id="56bcb-131">[同期中]</span><span class="sxs-lookup"><span data-stu-id="56bcb-131">Synchronizing</span></span>  
  
-   <span data-ttu-id="56bcb-132">[同期されていません]</span><span class="sxs-lookup"><span data-stu-id="56bcb-132">Not synchronizing</span></span>  
  
 <span data-ttu-id="56bcb-133">特定のサブスクリプションが複数の状態である場合に表示される値も、並べ替え順によって決まります。</span><span class="sxs-lookup"><span data-stu-id="56bcb-133">The sort order also determines which value is displayed if a given subscription is in more than one state.</span></span> <span data-ttu-id="56bcb-134">たとえば、サブスクリプションにエラーがあり、まもなく期限切れになる場合、 **[状態]** 列には **[エラー]** と表示されます。</span><span class="sxs-lookup"><span data-stu-id="56bcb-134">For example, if a subscription has an error and is expiring soon, the **Status** column displays **Error**.</span></span>  
  
 <span data-ttu-id="56bcb-135">状態値 **[パフォーマンス クリティカル]**、 **[長期マージ]**、 **[まもなく期限切れ/期限切れ]**、および **[初期化されていないサブスクリプション]** は警告です。</span><span class="sxs-lookup"><span data-stu-id="56bcb-135">The status values **Performance critical**, **Long-running merge**, **Expiring soon/Expired**, and **Uninitialized subscription** are warnings.</span></span> <span data-ttu-id="56bcb-136">警告が表示される場合、 **[状態]** 列にはエージェントが同期中かどうかも表示されます。</span><span class="sxs-lookup"><span data-stu-id="56bcb-136">When a warning is displayed, the **Status** column also displays if an agent is synchronizing.</span></span> <span data-ttu-id="56bcb-137">たとえば、 **[同期中]、[パフォーマンス クリティカル]** という形で状態が表示されます。</span><span class="sxs-lookup"><span data-stu-id="56bcb-137">For example, the status could be **Synchronizing, Performance critical**.</span></span>  
  
 <span data-ttu-id="56bcb-138">状態値 **[まもなく期限切れ/期限切れ]** および **[長期マージ]** は、しきい値が設定されている場合のみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="56bcb-138">The status values **Expiring soon/Expired** and **Long-running merge** can be displayed only if thresholds are set.</span></span> <span data-ttu-id="56bcb-139">**[パフォーマンス クリティカル]** の状態の値は、同じ種類の接続 (ダイヤルアップまたは LAN) によるサブスクリプションの同期が 5 回行われた後にのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="56bcb-139">The status value **Performance critical** can be displayed only after five synchronizations of subscriptions with the same connection type (dial-up or LAN).</span></span> <span data-ttu-id="56bcb-140">パフォーマンスの測定としきい値の設定については、「[Monitor Performance with Replication Monitor](monitor/monitor-performance-with-replication-monitor.md)」 (レプリケーション モニターを使用したパフォーマンスの監視) と「[レプリケーション モニターのしきい値と警告の設定](monitor/set-thresholds-and-warnings-in-replication-monitor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="56bcb-140">For information on performance measurements and setting thresholds, see [Monitor Performance with Replication Monitor](monitor/monitor-performance-with-replication-monitor.md) and [Set Thresholds and Warnings in Replication Monitor](monitor/set-thresholds-and-warnings-in-replication-monitor.md).</span></span>  
  
 <span data-ttu-id="56bcb-141">**[サブスクリプション]**</span><span class="sxs-lookup"><span data-stu-id="56bcb-141">**Subscription**</span></span>  
 <span data-ttu-id="56bcb-142">各サブスクリプションの名前です。*SubscriberName: SubscriptionDatabaseName*という形式になります。</span><span class="sxs-lookup"><span data-stu-id="56bcb-142">The name of each subscription, in the form:*SubscriberName: SubscriptionDatabaseName*.</span></span>  
  
 <span data-ttu-id="56bcb-143">**フレンドリ名**</span><span class="sxs-lookup"><span data-stu-id="56bcb-143">**Friendly Name**</span></span>  
 <span data-ttu-id="56bcb-144">各サブスクリプションの説明です。</span><span class="sxs-lookup"><span data-stu-id="56bcb-144">The description of each subscription.</span></span> <span data-ttu-id="56bcb-145">説明は、[サブスクリプションの**プロパティ**] ダイアログボックスで入力するか、 **@description** [sp_addmergesubscription](/sql/relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql)または[sp_addmergepullsubscription](/sql/relational-databases/system-stored-procedures/sp-addmergepullsubscription-transact-sql)のパラメーターと共に指定します。</span><span class="sxs-lookup"><span data-stu-id="56bcb-145">The description is entered in the **Subscription Properties** dialog box or specified with the **@description** parameter of [sp_addmergesubscription](/sql/relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql) or [sp_addmergepullsubscription](/sql/relational-databases/system-stored-procedures/sp-addmergepullsubscription-transact-sql).</span></span> <span data-ttu-id="56bcb-146">多くの場合、この説明は "表示名"、つまりサブスクリプションの通称として使用されます。</span><span class="sxs-lookup"><span data-stu-id="56bcb-146">Users often use the description as a "friendly name" or nickname for the subscription.</span></span>  
  
 <span data-ttu-id="56bcb-147">**Publication**</span><span class="sxs-lookup"><span data-stu-id="56bcb-147">**Publication**</span></span>  
 <span data-ttu-id="56bcb-148">サブスクリプションと同期するパブリケーションの名前です。 *PublicationDatabaseName: PublicationName*という形式になります。</span><span class="sxs-lookup"><span data-stu-id="56bcb-148">The name of the publication with which a subscription synchronizes, in the form: *PublicationDatabaseName: PublicationName*.</span></span>  
  
 <span data-ttu-id="56bcb-149">**パフォーマンス**</span><span class="sxs-lookup"><span data-stu-id="56bcb-149">**Performance**</span></span>  
 <span data-ttu-id="56bcb-150">各サブスクリプションのパフォーマンス評価です。これはレプリケーション モニターにより取得された、最新の配信率の計測結果に基づいています。</span><span class="sxs-lookup"><span data-stu-id="56bcb-150">The performance rating for each subscription, based on the most recent measurements of delivery rate taken by Replication Monitor.</span></span> <span data-ttu-id="56bcb-151">パフォーマンス評価は、接続の種類が同じ (ダイヤルアップまたは LAN) パブリケーションに対するサブスクリプションの履歴の平均パフォーマンスと、個々のサブスクリプションのパフォーマンスを比較することで決定されます。</span><span class="sxs-lookup"><span data-stu-id="56bcb-151">The rating is determined by comparing individual subscription performance to the average historical performance of subscriptions to the publication that have the same connection type (dial-up or LAN).</span></span> <span data-ttu-id="56bcb-152">レプリケーション モニターには、50 以上の変更を伴う同期がそれぞれ同じ種類の接続により 5 回行われた後で、値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="56bcb-152">Replication Monitor displays a value after five synchronizations have occurred with 50 or more changes each over the same type of connection.</span></span> <span data-ttu-id="56bcb-153">50 以上の変更を伴う同期が 5 回未満の場合、または最新の同期における変更が 50 未満の場合には、この列は空白になります。</span><span class="sxs-lookup"><span data-stu-id="56bcb-153">If there have been less than five synchronizations with 50 or more changes or the most recent synchronization has less than 50 changes, this column is blank.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="56bcb-154">パフォーマンスは、 **[接続]** 列に表示される接続の種類に基づいて決まります。したがって、配信率が低いサブスクリプションが低速の接続で同期されている場合、配信率が高いサブスクリプションよりも高いパフォーマンスが表示される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="56bcb-154">Performance is based on the connection type displayed in the **Connection** column; therefore it is possible for a subscription with a lower delivery rate to display a better performance rating than another subscription if the first subscription is synchronized over a slower connection.</span></span>  
  
 <span data-ttu-id="56bcb-155">パフォーマンス評価は、次のいずれかの値になります。</span><span class="sxs-lookup"><span data-stu-id="56bcb-155">The performance rating is one of the following values:</span></span>  
  
-   <span data-ttu-id="56bcb-156">非常に良い</span><span class="sxs-lookup"><span data-stu-id="56bcb-156">Excellent</span></span>  
  
-   <span data-ttu-id="56bcb-157">良い</span><span class="sxs-lookup"><span data-stu-id="56bcb-157">Good</span></span>  
  
-   <span data-ttu-id="56bcb-158">普通</span><span class="sxs-lookup"><span data-stu-id="56bcb-158">Fair</span></span>  
  
-   <span data-ttu-id="56bcb-159">悪い</span><span class="sxs-lookup"><span data-stu-id="56bcb-159">Poor</span></span>  
  
 <span data-ttu-id="56bcb-160">パフォーマンス評価の定義方法とパフォーマンスしきい値の設定方法については、「[Monitor Performance with Replication Monitor](monitor/monitor-performance-with-replication-monitor.md)」 (レプリケーション モニターを使用したパフォーマンスの監視) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="56bcb-160">For more information about how performance ratings are defined and how performance thresholds are set, see [Monitor Performance with Replication Monitor](monitor/monitor-performance-with-replication-monitor.md).</span></span>  
  
 <span data-ttu-id="56bcb-161">**[配信率]**</span><span class="sxs-lookup"><span data-stu-id="56bcb-161">**Delivery Rate**</span></span>  
 <span data-ttu-id="56bcb-162">マージ エージェントにより 1 秒間に処理される行数です。</span><span class="sxs-lookup"><span data-stu-id="56bcb-162">The number of rows per second processed by the Merge Agent.</span></span>  
  
 <span data-ttu-id="56bcb-163">**[最後の同期]**</span><span class="sxs-lookup"><span data-stu-id="56bcb-163">**Last Synchronization**</span></span>  
 <span data-ttu-id="56bcb-164">マージ エージェントが最後に実行された時刻です。</span><span class="sxs-lookup"><span data-stu-id="56bcb-164">The time at which the Merge Agent last ran.</span></span> <span data-ttu-id="56bcb-165">この同期では変更が処理されていることも、処理されていないこともあります。</span><span class="sxs-lookup"><span data-stu-id="56bcb-165">Changes may or may not have been processed during this synchronization.</span></span> <span data-ttu-id="56bcb-166">同期が進行中の場合、進行状況を示すパーセント値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="56bcb-166">If synchronization is in progress, a percentage complete value is displayed.</span></span>  
  
 <span data-ttu-id="56bcb-167">**Duration**</span><span class="sxs-lookup"><span data-stu-id="56bcb-167">**Duration**</span></span>  
 <span data-ttu-id="56bcb-168">最後の同期中におけるマージ エージェントの実行時間です。</span><span class="sxs-lookup"><span data-stu-id="56bcb-168">The amount of time the Merge Agent has run during the last synchronization.</span></span> <span data-ttu-id="56bcb-169">マージ エージェントが現在同期中の場合、これは経過時間を表します。マージ エージェントが以前に同期された場合、これは合計時間を表します。</span><span class="sxs-lookup"><span data-stu-id="56bcb-169">The time represents elapsed time if the Merge Agent is currently synchronizing and total time if the Merge Agent has synchronized previously.</span></span>  
  
 <span data-ttu-id="56bcb-170">**接続**</span><span class="sxs-lookup"><span data-stu-id="56bcb-170">**Connection**</span></span>  
 <span data-ttu-id="56bcb-171">サブスクライバーとパブリッシャーの接続の種類です。</span><span class="sxs-lookup"><span data-stu-id="56bcb-171">The type of connection between the Subscriber and the Publisher.</span></span> <span data-ttu-id="56bcb-172">**[LAN]**、 **[ダイヤルアップ]**、 **[インターネット]** のいずれかの値になります。</span><span class="sxs-lookup"><span data-stu-id="56bcb-172">The possible values are **LAN**, **Dialup**, and **Internet**.</span></span> <span data-ttu-id="56bcb-173">サブスクリプションで Web 同期が使用されている場合、 **[インターネット]** が表示されます。</span><span class="sxs-lookup"><span data-stu-id="56bcb-173">The **Internet** value is displayed if the subscription uses Web synchronization.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56bcb-174">参照</span><span class="sxs-lookup"><span data-stu-id="56bcb-174">See Also</span></span>  
 <span data-ttu-id="56bcb-175">[レプリケーションモニターを開始する](monitor/start-the-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="56bcb-175">[Start the Replication Monitor](monitor/start-the-replication-monitor.md) </span></span>  
 <span data-ttu-id="56bcb-176">[レプリケーション モニターを使用して情報を表示し、タスクを実行する](monitor/view-information-and-perform-tasks-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="56bcb-176">[View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md) </span></span>  
 <span data-ttu-id="56bcb-177">[レプリケーションの監視](monitoring-replication.md) </span><span class="sxs-lookup"><span data-stu-id="56bcb-177">[Monitoring Replication](monitoring-replication.md) </span></span>  
 [<span data-ttu-id="56bcb-178">マージ レプリケーションの Web 同期</span><span class="sxs-lookup"><span data-stu-id="56bcb-178">Web Synchronization for Merge Replication</span></span>](web-synchronization-for-merge-replication.md)  
  
  
