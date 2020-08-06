---
title: パブリケーション情報、[すべてのサブスクリプション] (マージ パブリケーション) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.publicationinfo.allsubscriptions.merge.f1
ms.assetid: 0f4fa946-a0d9-4d3b-b90b-53503c40fba2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 251e4c6e2e2adc60c838c7875d5d7d99aee64b54
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740822"
---
# <a name="publication-information-all-subscriptions-merge-publication"></a><span data-ttu-id="6f285-102">パブリケーション情報、[すべてのサブスクリプション] (マージ パブリケーション)</span><span class="sxs-lookup"><span data-stu-id="6f285-102">Publication Information, All Subscriptions (Merge Publication)</span></span>
  <span data-ttu-id="6f285-103">**[すべてのサブスクリプション]** タブには、選択したマージ パブリケーションに対するすべてのサブスクリプションの情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="6f285-103">The **All Subscriptions** tab displays information on all subscriptions to the selected merge publication.</span></span>  
  
## <a name="options"></a><span data-ttu-id="6f285-104">Options</span><span class="sxs-lookup"><span data-stu-id="6f285-104">Options</span></span>  
 <span data-ttu-id="6f285-105">サブスクリプションに関する詳細情報やタスクを調べるには、そのサブスクリプションの行を右クリックし、ショートカット メニューのオプションをクリックします。</span><span class="sxs-lookup"><span data-stu-id="6f285-105">For more detailed information and tasks related to a subscription, right-click the row for that subscription, and then click an option on the shortcut menu.</span></span> <span data-ttu-id="6f285-106">グリッドにデータを表示する方法を変更するには、グリッドを右クリックし、次のいずれかのオプションをクリックします。</span><span class="sxs-lookup"><span data-stu-id="6f285-106">To change the way that the grid displays data, right-click the grid, and then click one of the following options:</span></span>  
  
-   <span data-ttu-id="6f285-107">**[並べ替え]**: **[列の並べ替え]** ダイアログ ボックスで、1 つ以上の列を基準にして並べ替えを行います。</span><span class="sxs-lookup"><span data-stu-id="6f285-107">**Sort**: Sort on one or more columns in the **Sort Columns** dialog box.</span></span>  
  
-   <span data-ttu-id="6f285-108">**[表示する列の選択]**: **[列の選択]** ダイアログ ボックスで、表示する列とその表示順序を選択します。</span><span class="sxs-lookup"><span data-stu-id="6f285-108">**Choose Columns to Show**: Select which columns to display and the order in which to display them in the **Choose Columns** dialog box.</span></span>  
  
-   <span data-ttu-id="6f285-109">**[フィルター]**: **[フィルターの設定]** ダイアログ ボックスで、列の値に基づいてグリッドの行をフィルター選択します。</span><span class="sxs-lookup"><span data-stu-id="6f285-109">**Filter**: Filter rows in the grid based on column values in the **Filter Settings** dialog box.</span></span>  
  
-   <span data-ttu-id="6f285-110">**[フィルターのクリア]**: グリッドのフィルター設定をすべてクリアします。</span><span class="sxs-lookup"><span data-stu-id="6f285-110">**Clear Filter**: Clear any filter settings for the grid.</span></span>  
  
 <span data-ttu-id="6f285-111">フィルター設定は各グリッドに固有です。</span><span class="sxs-lookup"><span data-stu-id="6f285-111">Filter settings are specific to each grid.</span></span> <span data-ttu-id="6f285-112">列の選択と並べ替えは、各パブリッシャーのパブリケーション グリッドなど、同じ種類のすべてのグリッドに適用されます。</span><span class="sxs-lookup"><span data-stu-id="6f285-112">Column selection and sorting are applied to all grids of the same type, such as the publications grid for each Publisher.</span></span>  
  
 <span data-ttu-id="6f285-113">**表示**</span><span class="sxs-lookup"><span data-stu-id="6f285-113">**Show**</span></span>  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="6f285-114">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のバージョンのみです。</span><span class="sxs-lookup"><span data-stu-id="6f285-114">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions only.</span></span> <span data-ttu-id="6f285-115">サブスクリプション状態を選択すると、選択した種類の状態のサブスクリプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="6f285-115">Select the subscription states to display for the selected subscription type.</span></span> <span data-ttu-id="6f285-116">たとえば、エラーを含むサブスクリプションのみを表示するように設定できます。</span><span class="sxs-lookup"><span data-stu-id="6f285-116">For example, you can select to display only those subscriptions that have an error.</span></span>  
  
 <span data-ttu-id="6f285-117">**状態**</span><span class="sxs-lookup"><span data-stu-id="6f285-117">**Status**</span></span>  
 <span data-ttu-id="6f285-118">各サブスクリプションの状態です。これは、マージ エージェントの状態により決定されます。</span><span class="sxs-lookup"><span data-stu-id="6f285-118">The status of each subscription, which is determined by the status of the Merge Agent.</span></span>  
  
 <span data-ttu-id="6f285-119">既定では、サブスクリプションの情報を表示するグリッドは **[状態]** 列の順序で並べられています (同じ状態のサブスクリプションは、 **[パフォーマンス]** 列の順序で並べられています)。</span><span class="sxs-lookup"><span data-stu-id="6f285-119">By default, the grid containing subscription information is sorted by the **Status** column (and then sorted by the **Performance** column for those subscriptions with the same status).</span></span> <span data-ttu-id="6f285-120">表示される状態の値と、その値の並べ替え順 (たとえば、エラーは常にグリッドの上部に表示されます) を次に示します。</span><span class="sxs-lookup"><span data-stu-id="6f285-120">The following list shows the possible status values and the sort order for the values (for example, errors are always shown at the top of the grid).</span></span>  
  
-   <span data-ttu-id="6f285-121">エラー</span><span class="sxs-lookup"><span data-stu-id="6f285-121">Error</span></span>  
  
-   <span data-ttu-id="6f285-122">[パフォーマンス クリティカル]\([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のバージョンのみ)</span><span class="sxs-lookup"><span data-stu-id="6f285-122">Performance critical ([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions only)</span></span>  
  
-   <span data-ttu-id="6f285-123">[長期マージ]\([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のバージョンのみ)</span><span class="sxs-lookup"><span data-stu-id="6f285-123">Long-running merge ([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions only)</span></span>  
  
-   <span data-ttu-id="6f285-124">[まもなく期限切れ/期限切れ] ([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のバージョンのみ)</span><span class="sxs-lookup"><span data-stu-id="6f285-124">Expiring soon/Expired ([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions only)</span></span>  
  
-   <span data-ttu-id="6f285-125">[初期化されていないサブスクリプション]\([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のバージョンのみ)</span><span class="sxs-lookup"><span data-stu-id="6f285-125">Uninitialized subscription ([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions only)</span></span>  
  
-   <span data-ttu-id="6f285-126">[失敗したコマンドの再試行]</span><span class="sxs-lookup"><span data-stu-id="6f285-126">Retrying failed command</span></span>  
  
-   <span data-ttu-id="6f285-127">[同期中]</span><span class="sxs-lookup"><span data-stu-id="6f285-127">Synchronizing</span></span>  
  
-   <span data-ttu-id="6f285-128">[同期されていません]</span><span class="sxs-lookup"><span data-stu-id="6f285-128">Not synchronizing</span></span>  
  
 <span data-ttu-id="6f285-129">特定のサブスクリプションが複数の状態である場合に表示される値も、並べ替え順によって決まります。</span><span class="sxs-lookup"><span data-stu-id="6f285-129">The sort order also determines which value is displayed if a given subscription is in more than one state.</span></span> <span data-ttu-id="6f285-130">たとえば、サブスクリプションにエラーがあり、まもなく期限切れになる場合、 **[状態]** 列には **[エラー]** と表示されます。</span><span class="sxs-lookup"><span data-stu-id="6f285-130">For example, if a subscription has an error and is expiring soon, the **Status** column displays **Error**.</span></span>  
  
 <span data-ttu-id="6f285-131">状態値 **[パフォーマンス クリティカル]**、 **[長期マージ]**、 **[まもなく期限切れ/期限切れ]**、および **[初期化されていないサブスクリプション]** は警告です。</span><span class="sxs-lookup"><span data-stu-id="6f285-131">The status values **Performance critical**, **Long-running merge**, **Expiring soon/Expired**, and **Uninitialized subscription** are warnings.</span></span> <span data-ttu-id="6f285-132">警告が表示される場合、 **[状態]** 列にはエージェントが同期中かどうかも表示されます。</span><span class="sxs-lookup"><span data-stu-id="6f285-132">When a warning is displayed, the **Status** column also displays if an agent is synchronizing.</span></span> <span data-ttu-id="6f285-133">たとえば、 **[同期中]、[パフォーマンス クリティカル]** という形で状態が表示されます。</span><span class="sxs-lookup"><span data-stu-id="6f285-133">For example, the status could be **Synchronizing, Performance critical**.</span></span>  
  
 <span data-ttu-id="6f285-134">状態値 **[まもなく期限切れ/期限切れ]** および **[長期マージ]** は、しきい値が設定されている場合のみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="6f285-134">The status values **Expiring soon/Expired** and **Long-running merge** can be displayed only if thresholds are set.</span></span> <span data-ttu-id="6f285-135">**[パフォーマンス クリティカル]** の状態の値は、同じ種類の接続 (ダイヤルアップまたは LAN) によるサブスクリプションの同期が 5 回行われた後にのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="6f285-135">The status value **Performance critical** can be displayed only after five synchronizations of subscriptions with the same connection type (dial-up or LAN).</span></span> <span data-ttu-id="6f285-136">パフォーマンスの測定としきい値の設定については、「[Monitor Performance with Replication Monitor](monitor/monitor-performance-with-replication-monitor.md)」 (レプリケーション モニターを使用したパフォーマンスの監視) と「[レプリケーション モニターのしきい値と警告の設定](monitor/set-thresholds-and-warnings-in-replication-monitor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6f285-136">For information about performance measurements and setting thresholds, see [Monitor Performance with Replication Monitor](monitor/monitor-performance-with-replication-monitor.md) and [Set Thresholds and Warnings in Replication Monitor](monitor/set-thresholds-and-warnings-in-replication-monitor.md).</span></span>  
  
 <span data-ttu-id="6f285-137">**サブスクリプション**</span><span class="sxs-lookup"><span data-stu-id="6f285-137">**Subscription**</span></span>  
 <span data-ttu-id="6f285-138">各サブスクリプションの名前です。*SubscriberName: SubscriptionDatabaseName*という形式になります。</span><span class="sxs-lookup"><span data-stu-id="6f285-138">The name of each subscription, in the form:*SubscriberName: SubscriptionDatabaseName*.</span></span>  
  
 <span data-ttu-id="6f285-139">**フレンドリ名**</span><span class="sxs-lookup"><span data-stu-id="6f285-139">**Friendly Name**</span></span>  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] <span data-ttu-id="6f285-140">以降のバージョンのみです。</span><span class="sxs-lookup"><span data-stu-id="6f285-140">and later versions only.</span></span> <span data-ttu-id="6f285-141">各サブスクリプションの説明です。</span><span class="sxs-lookup"><span data-stu-id="6f285-141">The description of each subscription.</span></span> <span data-ttu-id="6f285-142">説明は、[サブスクリプションの**プロパティ**] ダイアログボックスで入力するか、 **@description** [sp_addmergesubscription](/sql/relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql)または[sp_addmergepullsubscription](/sql/relational-databases/system-stored-procedures/sp-addmergepullsubscription-transact-sql)のパラメーターと共に指定します。</span><span class="sxs-lookup"><span data-stu-id="6f285-142">The description is entered in the **Subscription Properties** dialog box or specified with the **@description** parameter of [sp_addmergesubscription](/sql/relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql) or [sp_addmergepullsubscription](/sql/relational-databases/system-stored-procedures/sp-addmergepullsubscription-transact-sql).</span></span> <span data-ttu-id="6f285-143">多くの場合、この説明は "表示名"、つまりサブスクリプションの通称として使用されます。</span><span class="sxs-lookup"><span data-stu-id="6f285-143">Users often use the description as a "friendly name" or nickname for the subscription.</span></span>  
  
 <span data-ttu-id="6f285-144">**パフォーマンス**</span><span class="sxs-lookup"><span data-stu-id="6f285-144">**Performance**</span></span>  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] <span data-ttu-id="6f285-145">以降のバージョンのみです。</span><span class="sxs-lookup"><span data-stu-id="6f285-145">and later versions only.</span></span> <span data-ttu-id="6f285-146">各サブスクリプションのパフォーマンス評価です。これはレプリケーション モニターにより取得された、最新の配信率の計測結果に基づいています。</span><span class="sxs-lookup"><span data-stu-id="6f285-146">The performance rating for each subscription, based on the most recent measurements of delivery rate taken by Replication Monitor.</span></span> <span data-ttu-id="6f285-147">パフォーマンス評価は、接続の種類が同じ (ダイヤルアップまたは LAN) パブリケーションに対するサブスクリプションの履歴の平均パフォーマンスと、個々のサブスクリプションのパフォーマンスを比較することで決定されます。</span><span class="sxs-lookup"><span data-stu-id="6f285-147">The rating is determined by comparing individual subscription performance to the average historical performance of subscriptions to the publication that have the same connection type (dial-up or LAN).</span></span> <span data-ttu-id="6f285-148">レプリケーション モニターには、50 以上の変更を伴う同期がそれぞれ同じ種類の接続により 5 回行われた後で、値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="6f285-148">Replication Monitor displays a value after five synchronizations have occurred with 50 or more changes each over the same type of connection.</span></span> <span data-ttu-id="6f285-149">50 以上の変更を伴う同期が 5 回未満の場合、または最新の同期における変更が 50 未満の場合には、この列は空白になります。</span><span class="sxs-lookup"><span data-stu-id="6f285-149">If there have been less than five synchronizations with 50 or more changes or the most recent synchronization has less than 50 changes, this column is blank.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6f285-150">パフォーマンスは、 **[接続]** 列に表示される接続の種類に基づいて決まります。したがって、配信率が低いサブスクリプションが低速の接続で同期されている場合、配信率が高いサブスクリプションよりも高いパフォーマンスが表示される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="6f285-150">Performance is based on the connection type displayed in the **Connection** column; therefore it is possible for a subscription with a lower delivery rate to display a better performance rating than another subscription if the first subscription is synchronized over a slower connection.</span></span>  
  
 <span data-ttu-id="6f285-151">パフォーマンス評価は、次のいずれかの値になります。</span><span class="sxs-lookup"><span data-stu-id="6f285-151">The performance rating is one of the following values:</span></span>  
  
-   <span data-ttu-id="6f285-152">非常に良い</span><span class="sxs-lookup"><span data-stu-id="6f285-152">Excellent</span></span>  
  
-   <span data-ttu-id="6f285-153">良い</span><span class="sxs-lookup"><span data-stu-id="6f285-153">Good</span></span>  
  
-   <span data-ttu-id="6f285-154">普通</span><span class="sxs-lookup"><span data-stu-id="6f285-154">Fair</span></span>  
  
-   <span data-ttu-id="6f285-155">悪い</span><span class="sxs-lookup"><span data-stu-id="6f285-155">Poor</span></span>  
  
 <span data-ttu-id="6f285-156">パフォーマンス評価の定義方法とパフォーマンスしきい値の設定方法については、「[Monitor Performance with Replication Monitor](monitor/monitor-performance-with-replication-monitor.md)」 (レプリケーション モニターを使用したパフォーマンスの監視) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6f285-156">For more information on how performance ratings are defined and how performance thresholds are set, see [Monitor Performance with Replication Monitor](monitor/monitor-performance-with-replication-monitor.md).</span></span>  
  
 <span data-ttu-id="6f285-157">**[配信率]**</span><span class="sxs-lookup"><span data-stu-id="6f285-157">**Delivery Rate**</span></span>  
 <span data-ttu-id="6f285-158">マージ エージェントにより 1 秒間に処理される行数です。</span><span class="sxs-lookup"><span data-stu-id="6f285-158">The number of rows per second processed by the Merge Agent.</span></span>  
  
 <span data-ttu-id="6f285-159">**[最後の同期]**</span><span class="sxs-lookup"><span data-stu-id="6f285-159">**Last Synchronization**</span></span>  
 <span data-ttu-id="6f285-160">マージ エージェントが最後に実行された時刻です。</span><span class="sxs-lookup"><span data-stu-id="6f285-160">The time at which the Merge Agent last ran.</span></span> <span data-ttu-id="6f285-161">この同期では変更が処理されていることも、処理されていないこともあります。</span><span class="sxs-lookup"><span data-stu-id="6f285-161">Changes may or may not have been processed during this synchronization.</span></span> <span data-ttu-id="6f285-162">同期が進行中の場合、進行状況を示すパーセント値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="6f285-162">If synchronization is in progress, a percentage complete value is displayed.</span></span>  
  
 <span data-ttu-id="6f285-163">**Duration**</span><span class="sxs-lookup"><span data-stu-id="6f285-163">**Duration**</span></span>  
 <span data-ttu-id="6f285-164">最後の同期中におけるマージ エージェントの実行時間です。</span><span class="sxs-lookup"><span data-stu-id="6f285-164">The amount of time the Merge Agent has run during the last synchronization.</span></span> <span data-ttu-id="6f285-165">マージ エージェントが現在同期中の場合、これは経過時間を表します。マージ エージェントが以前に同期された場合、これは合計時間を表します。</span><span class="sxs-lookup"><span data-stu-id="6f285-165">The time represents elapsed time if the Merge Agent is currently synchronizing and total time if the Merge Agent has synchronized previously.</span></span>  
  
 <span data-ttu-id="6f285-166">**接続**</span><span class="sxs-lookup"><span data-stu-id="6f285-166">**Connection**</span></span>  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] <span data-ttu-id="6f285-167">以降のバージョンのみです。</span><span class="sxs-lookup"><span data-stu-id="6f285-167">and later versions only.</span></span> <span data-ttu-id="6f285-168">サブスクライバーとパブリッシャーの接続の種類です。</span><span class="sxs-lookup"><span data-stu-id="6f285-168">The type of connection between the Subscriber and the Publisher.</span></span> <span data-ttu-id="6f285-169">**[LAN]**、 **[ダイヤルアップ]**、 **[インターネット]** のいずれかの値になります。</span><span class="sxs-lookup"><span data-stu-id="6f285-169">The possible values are **LAN**, **Dialup**, and **Internet**.</span></span> <span data-ttu-id="6f285-170">サブスクリプションで Web 同期が使用されている場合、 **[インターネット]** が表示されます。</span><span class="sxs-lookup"><span data-stu-id="6f285-170">The **Internet** value is displayed if the subscription uses Web synchronization.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f285-171">参照</span><span class="sxs-lookup"><span data-stu-id="6f285-171">See Also</span></span>  
 <span data-ttu-id="6f285-172">[レプリケーションモニターを開始する](monitor/start-the-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="6f285-172">[Start the Replication Monitor](monitor/start-the-replication-monitor.md) </span></span>  
 <span data-ttu-id="6f285-173">[レプリケーション モニターを使用して情報を表示し、タスクを実行する](monitor/view-information-and-perform-tasks-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="6f285-173">[View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md) </span></span>  
 <span data-ttu-id="6f285-174">[レプリケーションの監視](monitoring-replication.md) </span><span class="sxs-lookup"><span data-stu-id="6f285-174">[Monitoring Replication](monitoring-replication.md) </span></span>  
 [<span data-ttu-id="6f285-175">マージ レプリケーションの Web 同期</span><span class="sxs-lookup"><span data-stu-id="6f285-175">Web Synchronization for Merge Replication</span></span>](web-synchronization-for-merge-replication.md)  
  
  
