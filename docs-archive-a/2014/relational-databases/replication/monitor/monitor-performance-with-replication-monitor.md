---
title: レプリケーション モニターを使用したパフォーマンスの監視 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- monitoring performance [SQL Server replication], Replication Monitor
- Log Reader Agent, monitoring
- Replication Monitor, performance
- Merge Agent, monitoring
- Queue Reader Agent, monitoring
- Snapshot Agent, monitoring
- Distribution Agent, monitoring
- monitoring performance [SQL Server replication]
ms.assetid: f212397d-1bfd-496b-a246-668952891d09
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d02cb17aae5dfe72a9660de62e516e61313ef03c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634394"
---
# <a name="monitor-performance-with-replication-monitor"></a><span data-ttu-id="8056d-102">レプリケーション モニターを使用したパフォーマンスの監視</span><span class="sxs-lookup"><span data-stu-id="8056d-102">Monitor Performance with Replication Monitor</span></span>
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] <span data-ttu-id="8056d-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] レプリケーション モニターを使用すると、トランザクション レプリケーションとマージ レプリケーションのパフォーマンスを次の方法で監視できます。</span><span class="sxs-lookup"><span data-stu-id="8056d-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Replication Monitor allows you to monitor the performance of transactional replication and merge replication in the following ways:</span></span>  
  
-   <span data-ttu-id="8056d-104">警告およびしきい値の設定</span><span class="sxs-lookup"><span data-stu-id="8056d-104">Setting warnings and thresholds</span></span>  
  
-   <span data-ttu-id="8056d-105">パフォーマンス測定値の表示</span><span class="sxs-lookup"><span data-stu-id="8056d-105">Viewing performance measurements</span></span>  
  
-   <span data-ttu-id="8056d-106">トレーサー トークンによる待機時間の判断 (トランザクション レプリケーション)</span><span class="sxs-lookup"><span data-stu-id="8056d-106">Determining latency with tracer tokens (transactional replication)</span></span>  
  
-   <span data-ttu-id="8056d-107">詳細な同期統計情報の表示 (マージ レプリケーション)</span><span class="sxs-lookup"><span data-stu-id="8056d-107">Viewing detailed synchronization statistics (merge replication)</span></span>  
  
-   <span data-ttu-id="8056d-108">トランザクションおよび配信時間の表示 (トランザクション レプリケーション)</span><span class="sxs-lookup"><span data-stu-id="8056d-108">Viewing transactions and delivery time (transactional replication)</span></span>  
  
## <a name="set-warnings-and-thresholds"></a><span data-ttu-id="8056d-109">警告としきい値の設定</span><span class="sxs-lookup"><span data-stu-id="8056d-109">Set Warnings and Thresholds</span></span>  
 <span data-ttu-id="8056d-110">レプリケーション モニターでは、多くのパフォーマンス条件に対して警告を有効にできます。</span><span class="sxs-lookup"><span data-stu-id="8056d-110">Replication Monitor allows you to enable warnings for a number of performance conditions.</span></span> <span data-ttu-id="8056d-111">警告を有効にする際には、しきい値を指定します。</span><span class="sxs-lookup"><span data-stu-id="8056d-111">When you enable a warning, you specify a threshold.</span></span> <span data-ttu-id="8056d-112">しきい値に達したり、しきい値を超えると、サブスクリプションおよびそのサブスクリプションが同期しているパブリケーションの **[状態]** 列に警告が表示されます。</span><span class="sxs-lookup"><span data-stu-id="8056d-112">When that threshold is met or exceeded, a warning is displayed in the **Status** column for the subscription and the publication with which it synchronizes (unless an issue with a higher priority needs to be displayed).</span></span> <span data-ttu-id="8056d-113">しきい値に到達した場合は、レプリケーション モニターに警告を表示でき、さらに通知を発行することができます。</span><span class="sxs-lookup"><span data-stu-id="8056d-113">In addition to displaying a warning in Replication Monitor, reaching a threshold can also trigger an alert.</span></span> <span data-ttu-id="8056d-114">以下のようなパフォーマンス条件について、警告を有効にできます。</span><span class="sxs-lookup"><span data-stu-id="8056d-114">You can enable warnings for the following performance conditions:</span></span>  
  
-   <span data-ttu-id="8056d-115">指定した待機時間 (パブリッシャーでトランザクションがコミットされてから、対応するトランザクションがサブスクライバーでコミットされるまでの経過時間) の超過</span><span class="sxs-lookup"><span data-stu-id="8056d-115">Exceeding the specified latency (the amount of time that elapses between a transaction being committed at the Publisher and the corresponding transaction being committed at the Subscriber).</span></span>  
  
     <span data-ttu-id="8056d-116">トランザクション レプリケーションに適用できます。</span><span class="sxs-lookup"><span data-stu-id="8056d-116">This applies to transactional replication.</span></span> <span data-ttu-id="8056d-117">指定したしきい値に達したり、それを超えたりすると、状態が " **パフォーマンス クリティカル**" と表示されます。</span><span class="sxs-lookup"><span data-stu-id="8056d-117">If the specified threshold is met or exceeded, the status is displayed as **Performance critical**.</span></span>  
  
-   <span data-ttu-id="8056d-118">指定した同期時刻を超えた場合。</span><span class="sxs-lookup"><span data-stu-id="8056d-118">Exceeding the specified synchronization time.</span></span>  
  
     <span data-ttu-id="8056d-119">マージ レプリケーションに適用できます。</span><span class="sxs-lookup"><span data-stu-id="8056d-119">This applies to merge replication.</span></span> <span data-ttu-id="8056d-120">指定したしきい値に達したり、それを超えたりすると、状態が " **長期マージ**" と表示されます。</span><span class="sxs-lookup"><span data-stu-id="8056d-120">If the specified threshold is met or exceeded, the status is displayed as **Long-running merge**.</span></span> <span data-ttu-id="8056d-121">ダイヤルアップ接続とローカル エリア ネットワーク (LAN) 接続にそれぞれ別のしきい値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="8056d-121">You can specify different thresholds for dial-up and Local Area Network (LAN) connections.</span></span>  
  
-   <span data-ttu-id="8056d-122">指定した数の行を特定の時間内で処理できない場合。</span><span class="sxs-lookup"><span data-stu-id="8056d-122">Falling short of processing the specified number of rows in a given amount of time.</span></span>  
  
     <span data-ttu-id="8056d-123">マージ レプリケーションに適用できます。</span><span class="sxs-lookup"><span data-stu-id="8056d-123">This applies to merge replication.</span></span> <span data-ttu-id="8056d-124">指定したしきい値に達したり、それを超えたりすると、状態が " **パフォーマンス クリティカル**" と表示されます。</span><span class="sxs-lookup"><span data-stu-id="8056d-124">If the specified threshold is met or exceeded, the status is displayed as **Performance critical**.</span></span> <span data-ttu-id="8056d-125">ダイヤルアップ接続と LAN 接続にそれぞれ別のしきい値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="8056d-125">You can specify different thresholds for dial-up and LAN connections.</span></span>  
  
 <span data-ttu-id="8056d-126">詳細については、「 [Set Thresholds and Warnings in Replication Monitor](set-thresholds-and-warnings-in-replication-monitor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8056d-126">For more information, see [Set Thresholds and Warnings in Replication Monitor](set-thresholds-and-warnings-in-replication-monitor.md).</span></span>  
  
## <a name="view-performance-measurements"></a><span data-ttu-id="8056d-127">パフォーマンス測定値の表示</span><span class="sxs-lookup"><span data-stu-id="8056d-127">View Performance Measurements</span></span>  
 <span data-ttu-id="8056d-128">レプリケーション モニターでは、パブリケーションの **[現在の平均パフォーマンス]** 列と **[現在の最低パフォーマンス]** 列、およびサブスクリプションの **[パフォーマンス]** 列に、トランザクション レプリケーションおよびマージ レプリケーションのパフォーマンスの品質を示す値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="8056d-128">Replication Monitor displays performance quality values for transactional replication and merge replication in the **Current Average Performance** and **Current Worst Performance** columns for publications and the **Performance** column for subscriptions.</span></span> <span data-ttu-id="8056d-129">値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="8056d-129">The values are:</span></span>  
  
-   <span data-ttu-id="8056d-130">[非常に良い]</span><span class="sxs-lookup"><span data-stu-id="8056d-130">Excellent</span></span>  
  
-   <span data-ttu-id="8056d-131">[良い]</span><span class="sxs-lookup"><span data-stu-id="8056d-131">Good</span></span>  
  
-   <span data-ttu-id="8056d-132">[普通]</span><span class="sxs-lookup"><span data-stu-id="8056d-132">Fair</span></span>  
  
-   <span data-ttu-id="8056d-133">悪い</span><span class="sxs-lookup"><span data-stu-id="8056d-133">Poor</span></span>  
  
-   <span data-ttu-id="8056d-134">重大 (トランザクション レプリケーションの場合のみ)</span><span class="sxs-lookup"><span data-stu-id="8056d-134">Critical (transactional replication only)</span></span>  
  
 <span data-ttu-id="8056d-135">値は、以下のように決定されます。</span><span class="sxs-lookup"><span data-stu-id="8056d-135">The values are determined in the following ways:</span></span>  
  
-   <span data-ttu-id="8056d-136">トランザクション レプリケーションの場合、パフォーマンス品質は待機時間のしきい値によって決定されます。</span><span class="sxs-lookup"><span data-stu-id="8056d-136">For transactional replication, performance quality is determined by the latency threshold.</span></span> <span data-ttu-id="8056d-137">しきい値が設定されていない場合、値は表示されません。</span><span class="sxs-lookup"><span data-stu-id="8056d-137">If the threshold is not set, a value is not displayed.</span></span> <span data-ttu-id="8056d-138">次の表は、しきい値とパフォーマンス品質値の相関関係を示しています。</span><span class="sxs-lookup"><span data-stu-id="8056d-138">The following table shows the correlation between the threshold and the performance quality value.</span></span> <span data-ttu-id="8056d-139">たとえば、しきい値が 60 秒に設定されている場合に、実際の待機時間が 30 秒であるとすると、待機時間はしきい値の 50% となり、値は [良い] になります。</span><span class="sxs-lookup"><span data-stu-id="8056d-139">For example, if the threshold is set to 60 seconds and the actual latency is 30 seconds, latency is 50% of the threshold, resulting in a value of Good.</span></span>  
  
    |<span data-ttu-id="8056d-140">[非常に良い]</span><span class="sxs-lookup"><span data-stu-id="8056d-140">Excellent</span></span>|<span data-ttu-id="8056d-141">[良い]</span><span class="sxs-lookup"><span data-stu-id="8056d-141">Good</span></span>|<span data-ttu-id="8056d-142">[普通]</span><span class="sxs-lookup"><span data-stu-id="8056d-142">Fair</span></span>|<span data-ttu-id="8056d-143">悪い</span><span class="sxs-lookup"><span data-stu-id="8056d-143">Poor</span></span>|<span data-ttu-id="8056d-144">Critical</span><span class="sxs-lookup"><span data-stu-id="8056d-144">Critical</span></span>|  
    |---------------|----------|----------|----------|--------------|  
    |<span data-ttu-id="8056d-145">0 - 34%</span><span class="sxs-lookup"><span data-stu-id="8056d-145">0 - 34%</span></span>|<span data-ttu-id="8056d-146">35 - 59%</span><span class="sxs-lookup"><span data-stu-id="8056d-146">35 - 59%</span></span>|<span data-ttu-id="8056d-147">60 - 84%</span><span class="sxs-lookup"><span data-stu-id="8056d-147">60 - 84%</span></span>|<span data-ttu-id="8056d-148">85 - 99%</span><span class="sxs-lookup"><span data-stu-id="8056d-148">85 - 99%</span></span>|<span data-ttu-id="8056d-149">100% +</span><span class="sxs-lookup"><span data-stu-id="8056d-149">100% +</span></span>|  
  
-   <span data-ttu-id="8056d-150">マージ レプリケーションの場合、パフォーマンス品質は、しきい値とは関係ありません (行処理しきい値は、 **[パフォーマンス クリティカル]** の値を **[状態]** 列に表示するかどうかを決定します)。</span><span class="sxs-lookup"><span data-stu-id="8056d-150">For merge replication, performance quality is independent of either threshold (the row processing threshold does determine if a value of **Performance critical** is displayed in the **Status** column).</span></span> <span data-ttu-id="8056d-151">パフォーマンス品質は、個々のサブスクリプション パフォーマンスを、接続の種類 (ダイヤルアップまたは LAN) が同じパブリケーションのサブスクリプションの平均的な過去のパフォーマンスと比較することで決定されます。</span><span class="sxs-lookup"><span data-stu-id="8056d-151">Performance quality is determined by comparing individual subscription performance to the average historical performance of subscriptions to the publication that have the same connection type (dial-up or LAN).</span></span> <span data-ttu-id="8056d-152">レプリケーション モニターには、50 以上の変更を伴う同期がそれぞれ同じ種類の接続により 5 回行われた後で、値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="8056d-152">Replication Monitor displays a value after five synchronizations have occurred with 50 or more changes each over the same type of connection.</span></span> <span data-ttu-id="8056d-153">50 以上の変更に伴う同期が 5 回未満の場合、または最も最近の同期での変更が 50 未満の場合、レプリケーション モニターには値は表示されません。</span><span class="sxs-lookup"><span data-stu-id="8056d-153">If there have been less than five synchronizations with 50 or more changes or the most recent synchronization has less than 50 changes, Replication Monitor does not display a value.</span></span>  
  
     <span data-ttu-id="8056d-154">次の表は、平均パフォーマンスとパフォーマンス品質値の相関関係を示しています。</span><span class="sxs-lookup"><span data-stu-id="8056d-154">The following table shows the correlation between the average performance and the performance quality value.</span></span> <span data-ttu-id="8056d-155">たとえば、10 個のサブスクライバーが 1 秒あたり平均 100 行の速度で LAN 接続経由で同期し、サブスクリプションの 1 つが 1 秒あたり 125 行の速度で同期している場合、そのサブスクライバーの同期のパフォーマンスは平均の 125% となり、結果は [良い] となります。</span><span class="sxs-lookup"><span data-stu-id="8056d-155">For example, if ten Subscribers have synchronized over a LAN connection with an average rate of 100 rows per second, and one of the subscriptions then synchronizes at a rate of 125 rows per second, the performance for that Subscriber's synchronization is 125% of the average, resulting in a value of Good.</span></span>  
  
    |<span data-ttu-id="8056d-156">[非常に良い]</span><span class="sxs-lookup"><span data-stu-id="8056d-156">Excellent</span></span>|<span data-ttu-id="8056d-157">[良い]</span><span class="sxs-lookup"><span data-stu-id="8056d-157">Good</span></span>|<span data-ttu-id="8056d-158">[普通]</span><span class="sxs-lookup"><span data-stu-id="8056d-158">Fair</span></span>|<span data-ttu-id="8056d-159">悪い</span><span class="sxs-lookup"><span data-stu-id="8056d-159">Poor</span></span>|  
    |---------------|----------|----------|----------|  
    |<span data-ttu-id="8056d-160">151+%</span><span class="sxs-lookup"><span data-stu-id="8056d-160">151+%</span></span>|<span data-ttu-id="8056d-161">76 - 150%</span><span class="sxs-lookup"><span data-stu-id="8056d-161">76 - 150%</span></span>|<span data-ttu-id="8056d-162">26 - 75%</span><span class="sxs-lookup"><span data-stu-id="8056d-162">26 - 75%</span></span>|<span data-ttu-id="8056d-163">0 - 25%</span><span class="sxs-lookup"><span data-stu-id="8056d-163">0 - 25%</span></span>|  
  
 <span data-ttu-id="8056d-164">サブスクリプション情報の表示に関する詳細については、「[レプリケーション モニターを使用して情報を表示し、タスクを実行する](view-information-and-perform-tasks-replication-monitor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8056d-164">For more information about viewing subscription information, see [View Information and Perform Tasks using Replication Monitor](view-information-and-perform-tasks-replication-monitor.md).</span></span>  
  
## <a name="determine-latency-with-tracer-tokens"></a><span data-ttu-id="8056d-165">トレーサー トークンによる待機時間の判断</span><span class="sxs-lookup"><span data-stu-id="8056d-165">Determine Latency with Tracer Tokens</span></span>  
 <span data-ttu-id="8056d-166">トランザクション レプリケーションでは、パブリケーション データベースのトランザクション ログにトークン (少量のデータ) を挿入し、それがディストリビューターおよびサブスクライバーに到達するまでにかかった時間を記録することにより、システムの待機時間を計測できます。</span><span class="sxs-lookup"><span data-stu-id="8056d-166">Transactional replication allows you to measure the latency in a system by inserting a token (a small amount of data) in the transaction log of the publication database and recording how long it takes to arrive at the Distributor and Subscribers.</span></span> <span data-ttu-id="8056d-167">このトークンを使用すると、データがディストリビューターまたはサブスクライバーに到達しているかどうかを識別することもできます。</span><span class="sxs-lookup"><span data-stu-id="8056d-167">The token also allows you to identify if data is not reaching the Distributor or Subscriber.</span></span> <span data-ttu-id="8056d-168">詳細については、「 [トランザクション レプリケーションの待機時間の計測および接続の検証](measure-latency-and-validate-connections-for-transactional-replication.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8056d-168">For more information, see [Measure Latency and Validate Connections for Transactional Replication](measure-latency-and-validate-connections-for-transactional-replication.md).</span></span>  
  
## <a name="view-detailed-synchronization-performance-for-merge-replication"></a><span data-ttu-id="8056d-169">マージ レプリケーションの詳細な同期パフォーマンスの表示</span><span class="sxs-lookup"><span data-stu-id="8056d-169">View Detailed Synchronization Performance for Merge Replication</span></span>  
 <span data-ttu-id="8056d-170">マージ レプリケーションの場合、レプリケーション モニターには、同期中に処理される各アーティクルの詳細な統計情報が表示されます。この統計には、各処理フェーズ (変更のアップロードやダウンロードなど) にかかる時間などが含まれます。</span><span class="sxs-lookup"><span data-stu-id="8056d-170">For merge replication, Replication Monitor displays detailed statistics for each article processed during synchronization, including the amount of time spent in each processing phase (uploading changes, downloading changes, and so on).</span></span> <span data-ttu-id="8056d-171">この情報によって、速度低下の原因となっているテーブルを特定することができます。マージ サブスクリプションのパフォーマンスに関するトラブルシューティングを、この情報から開始することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="8056d-171">It can help pinpoint specific tables that are causing slow downs and is the best place to troubleshoot performance issues with merge subscriptions.</span></span> <span data-ttu-id="8056d-172">詳細な統計情報を表示する方法について詳しくは、「[レプリケーション モニターを使用して情報を表示し、タスクを実行する](view-information-and-perform-tasks-replication-monitor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8056d-172">For more information on viewing detailed statistics, see [View Information and Perform Tasks using Replication Monitor](view-information-and-perform-tasks-replication-monitor.md).</span></span>  
  
## <a name="view-transactions-and-delivery-time-for-transactional-replication"></a><span data-ttu-id="8056d-173">トランザクション レプリケーションのトランザクションおよび配信時間の表示</span><span class="sxs-lookup"><span data-stu-id="8056d-173">View Transactions and Delivery Time for Transactional Replication</span></span>  
 <span data-ttu-id="8056d-174">トランザクション レプリケーションの場合、レプリケーション モニターには、サブスクライバーにまだ配布されていないディストリビューション データベース内のトランザクションの数と、これらのトランザクションの予測配布時間が表示されます。</span><span class="sxs-lookup"><span data-stu-id="8056d-174">For transactional replication, Replication Monitor displays information about the number of transactions in the distribution database that have not yet been distributed to a Subscriber and the estimated time for distributing these transactions.</span></span> <span data-ttu-id="8056d-175">詳細については、「[レプリケーション モニターを使用して情報を表示し、タスクを実行する](view-information-and-perform-tasks-replication-monitor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8056d-175">For more information, see [View Information and Perform Tasks using Replication Monitor](view-information-and-perform-tasks-replication-monitor.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8056d-176">参照</span><span class="sxs-lookup"><span data-stu-id="8056d-176">See Also</span></span>  
 <span data-ttu-id="8056d-177">[レプリケーションの監視](../monitoring-replication.md) </span><span class="sxs-lookup"><span data-stu-id="8056d-177">[Monitoring Replication](../monitoring-replication.md) </span></span>  
 [<span data-ttu-id="8056d-178">レプリケーション モニターのしきい値と警告の設定</span><span class="sxs-lookup"><span data-stu-id="8056d-178">Set Thresholds and Warnings in Replication Monitor</span></span>](set-thresholds-and-warnings-in-replication-monitor.md)  
  
  
