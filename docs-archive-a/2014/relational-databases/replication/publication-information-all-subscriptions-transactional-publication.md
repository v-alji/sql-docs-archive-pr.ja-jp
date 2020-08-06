---
title: パブリケーション情報、[すべてのサブスクリプション] (トランザクション パブリケーション) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.publicationinfo.allsubscriptions.tran.f1
ms.assetid: 7073350c-f667-4f70-88e9-152c9a1b08dd
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ccc34bbe0933f4558478bd1d8276898219016e24
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633084"
---
# <a name="publication-information-all-subscriptions-transactional-publication"></a><span data-ttu-id="c46d3-102">パブリケーション情報、[すべてのサブスクリプション]\(トランザクション パブリケーション)</span><span class="sxs-lookup"><span data-stu-id="c46d3-102">Publication Information, All Subscriptions (Transactional Publication)</span></span>
  <span data-ttu-id="c46d3-103">**[すべてのサブスクリプション]** タブには、選択したトランザクション パブリケーションに対するすべてのサブスクリプションの情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="c46d3-103">The **All Subscriptions** tab displays information on all subscriptions to the selected transactional publication.</span></span>  
  
## <a name="options"></a><span data-ttu-id="c46d3-104">Options</span><span class="sxs-lookup"><span data-stu-id="c46d3-104">Options</span></span>  
 <span data-ttu-id="c46d3-105">サブスクリプションに関する詳細情報やタスクを調べるには、そのサブスクリプションの行を右クリックし、ショートカット メニューのオプションをクリックします。</span><span class="sxs-lookup"><span data-stu-id="c46d3-105">For more detailed information and tasks related to a subscription, right-click the row for that subscription, and then click an option on the shortcut menu.</span></span> <span data-ttu-id="c46d3-106">グリッドにデータを表示する方法を変更するには、グリッドを右クリックし、次のいずれかのオプションをクリックします。</span><span class="sxs-lookup"><span data-stu-id="c46d3-106">To change the way that the grid displays data, right-click the grid, and then click one of the following options:</span></span>  
  
-   <span data-ttu-id="c46d3-107">**[並べ替え]**: **[列の並べ替え]** ダイアログ ボックスで、1 つ以上の列を基準にして並べ替えを行います。</span><span class="sxs-lookup"><span data-stu-id="c46d3-107">**Sort**: Sort on one or more columns in the **Sort Columns** dialog box.</span></span>  
  
-   <span data-ttu-id="c46d3-108">**[表示する列の選択]**: **[列の選択]** ダイアログ ボックスで、表示する列とその表示順序を選択します。</span><span class="sxs-lookup"><span data-stu-id="c46d3-108">**Choose Columns to Show**: Select which columns to display and the order in which to display them in the **Choose Columns** dialog box.</span></span>  
  
-   <span data-ttu-id="c46d3-109">**[フィルター]**: **[フィルターの設定]** ダイアログ ボックスで、列の値に基づいてグリッドの行をフィルター選択します。</span><span class="sxs-lookup"><span data-stu-id="c46d3-109">**Filter**: Filter rows in the grid based on column values in the **Filter Settings** dialog box.</span></span>  
  
-   <span data-ttu-id="c46d3-110">**[フィルターのクリア]**: グリッドのフィルター設定をすべてクリアします。</span><span class="sxs-lookup"><span data-stu-id="c46d3-110">**Clear Filter**: Clear any filter settings for the grid.</span></span>  
  
 <span data-ttu-id="c46d3-111">フィルター設定は各グリッドに固有です。</span><span class="sxs-lookup"><span data-stu-id="c46d3-111">Filter settings are specific to each grid.</span></span> <span data-ttu-id="c46d3-112">列の選択と並べ替えは、各パブリッシャーのパブリケーション グリッドなど、同じ種類のすべてのグリッドに適用されます。</span><span class="sxs-lookup"><span data-stu-id="c46d3-112">Column selection and sorting are applied to all grids of the same type, such as the publications grid for each Publisher.</span></span>  
  
 <span data-ttu-id="c46d3-113">**表示**</span><span class="sxs-lookup"><span data-stu-id="c46d3-113">**Show**</span></span>  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="c46d3-114">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のバージョンのみです。</span><span class="sxs-lookup"><span data-stu-id="c46d3-114">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions only.</span></span> <span data-ttu-id="c46d3-115">サブスクリプション状態を選択すると、選択した種類の状態のサブスクリプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c46d3-115">Select the subscription states to display for the selected subscription type.</span></span> <span data-ttu-id="c46d3-116">たとえば、エラーを含むサブスクリプションのみを表示するように設定できます。</span><span class="sxs-lookup"><span data-stu-id="c46d3-116">For example, you can select to display only those subscriptions that have an error.</span></span>  
  
 <span data-ttu-id="c46d3-117">**状態**</span><span class="sxs-lookup"><span data-stu-id="c46d3-117">**Status**</span></span>  
 <span data-ttu-id="c46d3-118">各サブスクリプションの状態です。これは、ディストリビューション エージェントまたはログ リーダー エージェントの状態により決まります (より優先度の高い状態が表示されます。キュー更新サブスクリプションが使用されている場合、この状態はキュー リーダー エージェントによって決まる場合もあります)。</span><span class="sxs-lookup"><span data-stu-id="c46d3-118">The status of each subscription, which is determined by the status of the Distribution Agent or the Log Reader Agent (the higher priority status is displayed; the status can also be determined by the Queue Reader Agent if queued updating subscriptions are used).</span></span>  
  
 <span data-ttu-id="c46d3-119">既定では、サブスクリプションの情報を表示するグリッドは **[状態]** 列の順序で並べられています (同じ状態のサブスクリプションは、 **[パフォーマンス]** 列の順序で並べられています)。</span><span class="sxs-lookup"><span data-stu-id="c46d3-119">By default, the grid containing subscription information is sorted by the **Status** column (and then sorted by the **Performance** column for those subscriptions with the same status).</span></span> <span data-ttu-id="c46d3-120">表示される状態の値と、その値の並べ替え順 (たとえば、エラーは常にグリッドの上部に表示されます) を次に示します。</span><span class="sxs-lookup"><span data-stu-id="c46d3-120">The following list shows the possible status values and the sort order for the values (for example, errors are always shown at the top of the grid).</span></span>  
  
-   <span data-ttu-id="c46d3-121">エラー</span><span class="sxs-lookup"><span data-stu-id="c46d3-121">Error</span></span>  
  
-   <span data-ttu-id="c46d3-122">[パフォーマンス クリティカル]\([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のバージョンのみ)</span><span class="sxs-lookup"><span data-stu-id="c46d3-122">Performance critical ([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions only)</span></span>  
  
-   <span data-ttu-id="c46d3-123">[まもなく期限切れ/期限切れ] ([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のバージョンのみ)</span><span class="sxs-lookup"><span data-stu-id="c46d3-123">Expiring soon/Expired ([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions only)</span></span>  
  
-   <span data-ttu-id="c46d3-124">[初期化されていないサブスクリプション]\([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のバージョンのみ)</span><span class="sxs-lookup"><span data-stu-id="c46d3-124">Uninitialized subscription ([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions only)</span></span>  
  
-   <span data-ttu-id="c46d3-125">[失敗したコマンドの再試行]</span><span class="sxs-lookup"><span data-stu-id="c46d3-125">Retrying failed command</span></span>  
  
-   <span data-ttu-id="c46d3-126">停止中</span><span class="sxs-lookup"><span data-stu-id="c46d3-126">Not Running</span></span>  
  
-   <span data-ttu-id="c46d3-127">実行中</span><span class="sxs-lookup"><span data-stu-id="c46d3-127">Running</span></span>  
  
 <span data-ttu-id="c46d3-128">特定のサブスクリプションが複数の状態である場合に表示される値も、並べ替え順によって決まります。</span><span class="sxs-lookup"><span data-stu-id="c46d3-128">The sort order also determines which value is displayed if a given subscription is in more than one state.</span></span> <span data-ttu-id="c46d3-129">たとえば、サブスクリプションにエラーがあり、まもなく期限切れになる場合、 **[状態]** 列には **[エラー]** と表示されます。</span><span class="sxs-lookup"><span data-stu-id="c46d3-129">For example, if a subscription has an error and is expiring soon, the **Status** column displays **Error**.</span></span>  
  
 <span data-ttu-id="c46d3-130">状態値 **[パフォーマンス クリティカル]**、 **[まもなく期限切れ/期限切れ]**、および **[初期化されていないサブスクリプション]** は警告です。</span><span class="sxs-lookup"><span data-stu-id="c46d3-130">The status values **Performance critical**, **Expiring soon/Expired**, and **Uninitialized subscription** are warnings.</span></span> <span data-ttu-id="c46d3-131">警告が表示される場合、 **[状態]** 列にはエージェントが実行中かどうかも表示されます。</span><span class="sxs-lookup"><span data-stu-id="c46d3-131">When a warning is displayed, the **Status** column also displays if an agent is running.</span></span> <span data-ttu-id="c46d3-132">たとえば、 **[実行中]、[パフォーマンス クリティカル]** という形で状態が表示されます。</span><span class="sxs-lookup"><span data-stu-id="c46d3-132">For example, the status could be **Running, Performance critical**.</span></span>  
  
 <span data-ttu-id="c46d3-133">状態値 **[パフォーマンス クリティカル]** および **[まもなく期限切れ/期限切れ]** は、しきい値が設定されている場合のみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="c46d3-133">The status values **Performance critical** and **Expiring soon/Expired** are displayed only if thresholds are set.</span></span> <span data-ttu-id="c46d3-134">パフォーマンスの測定としきい値の設定については、「[Monitor Performance with Replication Monitor](monitor/monitor-performance-with-replication-monitor.md)」 (レプリケーション モニターを使用したパフォーマンスの監視) と「[レプリケーション モニターのしきい値と警告の設定](monitor/set-thresholds-and-warnings-in-replication-monitor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c46d3-134">For information on performance measurements and setting thresholds, see [Monitor Performance with Replication Monitor](monitor/monitor-performance-with-replication-monitor.md) and [Set Thresholds and Warnings in Replication Monitor](monitor/set-thresholds-and-warnings-in-replication-monitor.md).</span></span>  
  
 <span data-ttu-id="c46d3-135">**サブスクリプション**</span><span class="sxs-lookup"><span data-stu-id="c46d3-135">**Subscription**</span></span>  
 <span data-ttu-id="c46d3-136">各サブスクリプションの名前です。 *SubscriberName: SubscriptionDatabaseName*という形式になります。</span><span class="sxs-lookup"><span data-stu-id="c46d3-136">The name of each subscription, in the form: *SubscriberName: SubscriptionDatabaseName*.</span></span>  
  
 <span data-ttu-id="c46d3-137">**パフォーマンス**</span><span class="sxs-lookup"><span data-stu-id="c46d3-137">**Performance**</span></span>  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] <span data-ttu-id="c46d3-138">以降のバージョンのみです。</span><span class="sxs-lookup"><span data-stu-id="c46d3-138">and later versions only.</span></span> <span data-ttu-id="c46d3-139">各サブスクリプションのパフォーマンス評価は、レプリケーション モニターにより取得され、履歴パフォーマンスに反映されていない、最も新しい計測値に基づいています。</span><span class="sxs-lookup"><span data-stu-id="c46d3-139">The performance rating for each subscription is based on the most recent measurements taken by Replication Monitor and does not reflect historical performance.</span></span> <span data-ttu-id="c46d3-140">パフォーマンスは、パフォーマンスしきい値が定義されているパブリケーションへのサブスクリプションについてのみ計測されます。パブリケーションにパフォーマンスしきい値が定義されていない場合、この列には **[有効になっていません]** と表示されます。</span><span class="sxs-lookup"><span data-stu-id="c46d3-140">Performance is measured for subscriptions to publications that have performance thresholds defined; if performance thresholds are not defined for a publication, this column displays **Not enabled**.</span></span> <span data-ttu-id="c46d3-141">パフォーマンス評価は、次のいずれかの値になります。</span><span class="sxs-lookup"><span data-stu-id="c46d3-141">The performance rating is one of the following values:</span></span>  
  
-   <span data-ttu-id="c46d3-142">非常に良い</span><span class="sxs-lookup"><span data-stu-id="c46d3-142">Excellent</span></span>  
  
-   <span data-ttu-id="c46d3-143">良い</span><span class="sxs-lookup"><span data-stu-id="c46d3-143">Good</span></span>  
  
-   <span data-ttu-id="c46d3-144">普通</span><span class="sxs-lookup"><span data-stu-id="c46d3-144">Fair</span></span>  
  
-   <span data-ttu-id="c46d3-145">悪い</span><span class="sxs-lookup"><span data-stu-id="c46d3-145">Poor</span></span>  
  
-   <span data-ttu-id="c46d3-146">重要</span><span class="sxs-lookup"><span data-stu-id="c46d3-146">Critical</span></span>  
  
 <span data-ttu-id="c46d3-147">パフォーマンスが [重大] の場合、 **[状態]** 列に **[パフォーマンス クリティカル]** と表示されます。</span><span class="sxs-lookup"><span data-stu-id="c46d3-147">If performance is critical, **Performance Critical** is displayed in the **Status** column.</span></span> <span data-ttu-id="c46d3-148">パフォーマンス評価の定義方法とパフォーマンスしきい値の設定方法については、「[Monitor Performance with Replication Monitor](monitor/monitor-performance-with-replication-monitor.md)」 (レプリケーション モニターを使用したパフォーマンスの監視) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c46d3-148">For more information on how performance ratings are defined and how performance thresholds are set, see [Monitor Performance with Replication Monitor](monitor/monitor-performance-with-replication-monitor.md).</span></span>  
  
 <span data-ttu-id="c46d3-149">**待機時間**</span><span class="sxs-lookup"><span data-stu-id="c46d3-149">**Latency**</span></span>  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] <span data-ttu-id="c46d3-150">以降のバージョンのみです。</span><span class="sxs-lookup"><span data-stu-id="c46d3-150">and later versions only.</span></span> <span data-ttu-id="c46d3-151">トランザクションがパブリッシャー側でコミットされたときから、サブスクライバー側で対応するトランザクションがコミットされるまでに経過した時間の平均値です。</span><span class="sxs-lookup"><span data-stu-id="c46d3-151">The average amount of time that elapses between a transaction being committed at the Publisher and the corresponding transaction being committed at the Subscriber.</span></span> <span data-ttu-id="c46d3-152">表示される待機時間は、レプリケーション モニターにより取得された最新の計測値に基づいています。</span><span class="sxs-lookup"><span data-stu-id="c46d3-152">The latency displayed is based on the most recent measurements taken by Replication Monitor.</span></span> <span data-ttu-id="c46d3-153">待機時間の計測の詳細については、「[トランザクション レプリケーションの待機時間の計測および接続の検証](monitor/measure-latency-and-validate-connections-for-transactional-replication.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c46d3-153">For more information about measuring latency, see [Measure Latency and Validate Connections for Transactional Replication](monitor/measure-latency-and-validate-connections-for-transactional-replication.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c46d3-154">参照</span><span class="sxs-lookup"><span data-stu-id="c46d3-154">See Also</span></span>  
 <span data-ttu-id="c46d3-155">[レプリケーションモニターを開始する](monitor/start-the-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="c46d3-155">[Start the Replication Monitor](monitor/start-the-replication-monitor.md) </span></span>  
 <span data-ttu-id="c46d3-156">[レプリケーション モニターを使用して情報を表示し、タスクを実行する](monitor/view-information-and-perform-tasks-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="c46d3-156">[View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md) </span></span>  
 [<span data-ttu-id="c46d3-157">レプリケーションの監視</span><span class="sxs-lookup"><span data-stu-id="c46d3-157">Monitoring Replication</span></span>](monitoring-replication.md)  
  
  
