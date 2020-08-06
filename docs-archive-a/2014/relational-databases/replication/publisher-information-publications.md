---
title: SQL Server レプリケーション [パブリッシャー情報] ダイアログボックス |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.publisherinfo.publications.f1
ms.assetid: 0b2e3d4e-03b7-4c31-8f96-48648d750010
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d3797ae4f9fe8f42b4abec715c63bc627c2a62cf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714146"
---
# <a name="sql-server-replication-publisher-information-dialog-box"></a><span data-ttu-id="64b47-102">[パブリッシャー情報] ダイアログボックスの SQL Server レプリケーション</span><span class="sxs-lookup"><span data-stu-id="64b47-102">SQL Server Replication 'Publisher Information' dialog box</span></span>
  <span data-ttu-id="64b47-103">**[パブリケーション]** タブを使用すると、左ペインで選択したパブリッシャーにおけるすべてのパブリケーションに関する要約情報を取得できます。</span><span class="sxs-lookup"><span data-stu-id="64b47-103">The **Publications** tab provides summary information for all publications at the Publisher selected in the left pane.</span></span>  
  
## <a name="options"></a><span data-ttu-id="64b47-104">オプション</span><span class="sxs-lookup"><span data-stu-id="64b47-104">Options</span></span>  
 <span data-ttu-id="64b47-105">グリッドにデータを表示する方法を変更するには、グリッドを右クリックし、次のいずれかのオプションをクリックします。</span><span class="sxs-lookup"><span data-stu-id="64b47-105">To change the way that the grid displays data, right-click the grid, and then click one of the following options:</span></span>  
  
-   <span data-ttu-id="64b47-106">**[並べ替え]** : **[列の並べ替え]** ダイアログ ボックスで、1 つ以上の列を基準にして並べ替えを行います。</span><span class="sxs-lookup"><span data-stu-id="64b47-106">**Sort**: Sort on one or more columns in the **Sort Columns** dialog box.</span></span>  
  
-   <span data-ttu-id="64b47-107">**[表示する列の選択]** : **[列の選択]** ダイアログ ボックスで、表示する列とその表示順序を選択します。</span><span class="sxs-lookup"><span data-stu-id="64b47-107">**Choose Columns to Show**: Select which columns to display and the order in which to display them in the **Choose Columns** dialog box.</span></span>  
  
-   <span data-ttu-id="64b47-108">**[フィルター]** : **[フィルターの設定]** ダイアログ ボックスで、列の値に基づいてグリッドの行をフィルター選択します。</span><span class="sxs-lookup"><span data-stu-id="64b47-108">**Filter**: Filter rows in the grid based on column values in the **Filter Settings** dialog box.</span></span>  
  
-   <span data-ttu-id="64b47-109">**[フィルターのクリア]** : グリッドのフィルター設定をすべてクリアします。</span><span class="sxs-lookup"><span data-stu-id="64b47-109">**Clear Filter**: Clear any filter settings for the grid.</span></span>  
  
 <span data-ttu-id="64b47-110">フィルター設定は各グリッドに固有です。</span><span class="sxs-lookup"><span data-stu-id="64b47-110">Filter settings are specific to each grid.</span></span> <span data-ttu-id="64b47-111">列の選択と並べ替えは、各パブリッシャーのパブリケーション グリッドなど、同じ種類のすべてのグリッドに適用されます。</span><span class="sxs-lookup"><span data-stu-id="64b47-111">Column selection and sorting are applied to all grids of the same type, such as the publications grid for each Publisher.</span></span>  
  
 <span data-ttu-id="64b47-112">**状態**</span><span class="sxs-lookup"><span data-stu-id="64b47-112">**Status**</span></span>  
 <span data-ttu-id="64b47-113">各パブリケーションの状態です。これは、サブスクリプションの最も優先度の高い状態により決定されます。</span><span class="sxs-lookup"><span data-stu-id="64b47-113">The status of each publication, which is determined by the highest priority status of its subscriptions.</span></span> <span data-ttu-id="64b47-114">既定では、パブリケーション情報を表示するグリッドは **[状態]** 列の順序で並べられています。</span><span class="sxs-lookup"><span data-stu-id="64b47-114">By default, the grid containing publication information is sorted by the **Status** column.</span></span> <span data-ttu-id="64b47-115">表示される状態の値と、その値の並べ替え順 (たとえば、エラーは常にグリッドの上部に表示されます) を次に示します。</span><span class="sxs-lookup"><span data-stu-id="64b47-115">The following list shows the possible status values and the sort order for the values (for example, errors are always shown at the top of the grid):</span></span>  
  
-   <span data-ttu-id="64b47-116">エラー</span><span class="sxs-lookup"><span data-stu-id="64b47-116">Error</span></span>  
  
-   <span data-ttu-id="64b47-117">[パフォーマンス クリティカル]</span><span class="sxs-lookup"><span data-stu-id="64b47-117">Performance critical</span></span>  
  
-   <span data-ttu-id="64b47-118">[失敗したコマンドの再試行]</span><span class="sxs-lookup"><span data-stu-id="64b47-118">Retrying failed command</span></span>  
  
-   <span data-ttu-id="64b47-119">[OK]</span><span class="sxs-lookup"><span data-stu-id="64b47-119">OK</span></span>  
  
 <span data-ttu-id="64b47-120">**[パフォーマンス クリティカル]** 状態は、トランザクション サブスクリプションとマージ サブスクリプションに関連しています。トランザクション サブスクリプションの場合は、しきい値が設定されている場合にのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="64b47-120">The status value **Performance critical** is relevant for transactional subscriptions and merge subscriptions; for transactional subscriptions, it can be displayed only if a threshold is set.</span></span> <span data-ttu-id="64b47-121">パフォーマンスの測定としきい値の設定については、「[Monitor Performance with Replication Monitor](monitor/monitor-performance-with-replication-monitor.md)」 (レプリケーション モニターを使用したパフォーマンスの監視) と「[レプリケーション モニターのしきい値と警告の設定](monitor/set-thresholds-and-warnings-in-replication-monitor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="64b47-121">For information on performance measurements and setting thresholds, see [Monitor Performance with Replication Monitor](monitor/monitor-performance-with-replication-monitor.md) and [Set Thresholds and Warnings in Replication Monitor](monitor/set-thresholds-and-warnings-in-replication-monitor.md).</span></span>  
  
 <span data-ttu-id="64b47-122">**パブリケーション**</span><span class="sxs-lookup"><span data-stu-id="64b47-122">**Publication**</span></span>  
 <span data-ttu-id="64b47-123">各パブケーションの名前です。 *PublicationDatabaseName: PublicationName*という形式になります。</span><span class="sxs-lookup"><span data-stu-id="64b47-123">The name of each publication, in the form *PublicationDatabaseName: PublicationName*.</span></span>  
  
 <span data-ttu-id="64b47-124">**サブスクリプション**</span><span class="sxs-lookup"><span data-stu-id="64b47-124">**Subscriptions**</span></span>  
 <span data-ttu-id="64b47-125">各パブリケーションのサブスクリプションの数です。</span><span class="sxs-lookup"><span data-stu-id="64b47-125">The number of subscriptions for each publication.</span></span>  
  
 <span data-ttu-id="64b47-126">**[同期中]**</span><span class="sxs-lookup"><span data-stu-id="64b47-126">**Synchronizing**</span></span>  
 <span data-ttu-id="64b47-127">各パブリケーションにおいて現在同期しているサブスクリプションの数です。</span><span class="sxs-lookup"><span data-stu-id="64b47-127">The number of subscriptions for each publication that are currently synchronizing:</span></span>  
  
-   <span data-ttu-id="64b47-128">トランザクション サブスクリプションが "同期" している場合、ディストリビューション エージェントが実行されていても、データは必ずしもレプリケートされるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="64b47-128">For transactional replication, "synchronizing" means that the Distribution Agent is running, but data is not necessarily being replicated.</span></span>  
  
-   <span data-ttu-id="64b47-129">マージ レプリケーションが "同期" している場合、マージ エージェントは実行されており、データは現在レプリケートされています。</span><span class="sxs-lookup"><span data-stu-id="64b47-129">For merge replication, "synchronizing" means that the Merge Agent is running and that data is currently being replicated.</span></span>  
  
-   <span data-ttu-id="64b47-130">スナップショット レプリケーションが "同期" している場合、ディストリビューション エージェントは実行されており、データは現在レプリケートされています。</span><span class="sxs-lookup"><span data-stu-id="64b47-130">For snapshot replication, "synchronizing" means that the Distribution Agent is running and that data is currently being replicated.</span></span>  
  
 <span data-ttu-id="64b47-131">**[現在の平均パフォーマンス]** と **[現在の最低パフォーマンス]**</span><span class="sxs-lookup"><span data-stu-id="64b47-131">**Current Average Performance** and **Current Worst Performance**</span></span>  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="64b47-132">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のバージョンのみです。</span><span class="sxs-lookup"><span data-stu-id="64b47-132">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions only.</span></span> <span data-ttu-id="64b47-133">それぞれ、パブリケーションに対するすべてのサブスクリプションの、平均パフォーマンスと最低パフォーマンスの評価を表します。</span><span class="sxs-lookup"><span data-stu-id="64b47-133">The average performance rating and the worst performance rating, respectively, for all subscriptions to a publication.</span></span> <span data-ttu-id="64b47-134">評価は、レプリケーション モニターにより取得された最新の計測結果に基づいています。サブスクリプションの経過的なパフォーマンスは反映されません。</span><span class="sxs-lookup"><span data-stu-id="64b47-134">Ratings are based on the most recent measurements taken by Replication Monitor and do not reflect the performance of a subscription over time.</span></span>  
  
 <span data-ttu-id="64b47-135">トランザクション レプリケーションの場合、レプリケーション モニターには、パフォーマンスしきい値が定義されているパブリケーションに対してのみ値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="64b47-135">For transactional replication, Replication Monitor displays a value only for publications that have performance thresholds defined.</span></span> <span data-ttu-id="64b47-136">パブリケーションにパフォーマンスしきい値が定義されていない場合、この列には **[有効になっていません]** と表示されます。</span><span class="sxs-lookup"><span data-stu-id="64b47-136">If performance thresholds are not defined for a publication, this column displays **Not enabled**.</span></span> <span data-ttu-id="64b47-137">マージ レプリケーションの場合、レプリケーション モニターには、50 以上の変更を伴う同期がそれぞれ同じ種類の接続 (ダイヤルアップまたは LAN) により 5 回行われた後で、値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="64b47-137">For merge replication, Replication Monitor displays a value after five synchronizations have occurred with 50 or more changes each over the same type of connection (dial-up or LAN).</span></span> <span data-ttu-id="64b47-138">50 以上の変更を伴う同期が 5 回未満の場合、または最新の同期における変更が 50 未満の場合には、この列は空白になります。</span><span class="sxs-lookup"><span data-stu-id="64b47-138">If there have been less than five synchronizations with 50 or more changes or the most recent synchronization has less than 50 changes, this column is blank.</span></span>  
  
 <span data-ttu-id="64b47-139">パフォーマンス評価は、次のいずれかの値になります。</span><span class="sxs-lookup"><span data-stu-id="64b47-139">The performance rating is one of the following values:</span></span>  
  
-   <span data-ttu-id="64b47-140">[非常に良い]</span><span class="sxs-lookup"><span data-stu-id="64b47-140">Excellent</span></span>  
  
-   <span data-ttu-id="64b47-141">[良い]</span><span class="sxs-lookup"><span data-stu-id="64b47-141">Good</span></span>  
  
-   <span data-ttu-id="64b47-142">[普通]</span><span class="sxs-lookup"><span data-stu-id="64b47-142">Fair</span></span>  
  
-   <span data-ttu-id="64b47-143">悪い</span><span class="sxs-lookup"><span data-stu-id="64b47-143">Poor</span></span>  
  
-   <span data-ttu-id="64b47-144">Critical</span><span class="sxs-lookup"><span data-stu-id="64b47-144">Critical</span></span>  
  
 <span data-ttu-id="64b47-145">パフォーマンス評価の定義方法とパフォーマンスしきい値の設定方法については、「[Monitor Performance with Replication Monitor](monitor/monitor-performance-with-replication-monitor.md)」 (レプリケーション モニターを使用したパフォーマンスの監視) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="64b47-145">For more information about how performance ratings are defined and how performance thresholds are set, see [Monitor Performance with Replication Monitor](monitor/monitor-performance-with-replication-monitor.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64b47-146">参照</span><span class="sxs-lookup"><span data-stu-id="64b47-146">See Also</span></span>  
 <span data-ttu-id="64b47-147">[レプリケーション モニターの開始](monitor/start-the-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="64b47-147">[Start the Replication Monitor](monitor/start-the-replication-monitor.md) </span></span>  
 <span data-ttu-id="64b47-148">[レプリケーション モニターを使用して情報を表示し、タスクを実行する](monitor/view-information-and-perform-tasks-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="64b47-148">[View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md) </span></span>  
 [<span data-ttu-id="64b47-149">レプリケーションの監視</span><span class="sxs-lookup"><span data-stu-id="64b47-149">Monitoring Replication</span></span>](monitoring-replication.md)  
  
  
