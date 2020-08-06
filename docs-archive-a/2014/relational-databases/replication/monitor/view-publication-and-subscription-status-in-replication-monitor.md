---
title: レプリケーション モニターでのパブリケーションおよびサブスクリプションの状態の表示 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Log Reader Agent, monitoring
- Merge Agent, monitoring
- Queue Reader Agent, monitoring
- publications [SQL Server replication], viewing information
- Snapshot Agent, monitoring
- Distribution Agent, monitoring
- monitoring performance [SQL Server replication], publication status
- monitoring performance [SQL Server replication], subscription status
- subscriptions [SQL Server replication], viewing status
- Replication Monitor, publication and subscription status
ms.assetid: 16590771-9867-463e-a973-36a5c145ac16
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4f1f714e18a961546a4e5a7f6709beca8d525800
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741813"
---
# <a name="view-publication-and-subscription-status-in-replication-monitor"></a><span data-ttu-id="a3937-102">レプリケーション モニターでのパブリケーションおよびサブスクリプションの状態の表示</span><span class="sxs-lookup"><span data-stu-id="a3937-102">View Publication and Subscription Status in Replication Monitor</span></span>
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)]<span data-ttu-id="a3937-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]レプリケーションモニターには、パブリケーションとサブスクリプションの状態情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a3937-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Replication Monitor displays status information for publications and subscriptions:</span></span>  
  
-   <span data-ttu-id="a3937-104">パブリケーションの状態は、そのサブスクリプションの最も優先度の高い状態によって決定されます。</span><span class="sxs-lookup"><span data-stu-id="a3937-104">The status of a publication is determined by the highest priority status of its subscriptions.</span></span> <span data-ttu-id="a3937-105">たとえば、あるパブリケーションに対する 1 つのサブスクリプションにエラーが発生し、別のサブスクリプションにはパフォーマンス上の問題がある場合、そのパブリケーションに対してはエラーの状態が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a3937-105">For example, if one subscription to a publication has an error and another has a performance issue, a status of error is displayed for the publication.</span></span>  
  
-   <span data-ttu-id="a3937-106">サブスクリプションの状態は、そのサブスクリプションにサービスを提供するエージェントの状態によって決定されます。</span><span class="sxs-lookup"><span data-stu-id="a3937-106">The status of a subscription is determined by the status of the agents that service the subscription.</span></span> <span data-ttu-id="a3937-107">マージ レプリケーションの場合はマージ エージェントです。</span><span class="sxs-lookup"><span data-stu-id="a3937-107">For merge replication, this is the Merge Agent.</span></span> <span data-ttu-id="a3937-108">トランザクション レプリケーションの場合は、ログ リーダー エージェントまたはディストリビューション エージェントです (優先度の高い方の状態が表示されます。キュー更新サブスクリプションが使用されている場合は、状態はキュー リーダー エージェントによっても決定されます)。</span><span class="sxs-lookup"><span data-stu-id="a3937-108">For transactional replication, this is either the Log Reader Agent or the Distribution Agent (the higher priority status is displayed; the status can also be determined by the Queue Reader Agent if queued updating subscriptions are used).</span></span> <span data-ttu-id="a3937-109">スナップショット レプリケーションの場合は、スナップショット エージェントまたはディストリビューション エージェントです (優先度の高い方の状態が表示されます)。</span><span class="sxs-lookup"><span data-stu-id="a3937-109">For snapshot replication, this is the Snapshot Agent or the Distribution Agent (the higher priority status is displayed).</span></span>  
  
 <span data-ttu-id="a3937-110">以下に、パブリケーションおよびサブスクリプションの状態の値の一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="a3937-110">Tables in the following sections list the possible status values for publications and subscriptions.</span></span> <span data-ttu-id="a3937-111">しきい値に達したか、超えた場合にのみ、3 つの状態値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a3937-111">Three of the status values are displayed only if a threshold is met or exceeded:</span></span>  
  
-   <span data-ttu-id="a3937-112">有効期限切れサブスクリプション</span><span class="sxs-lookup"><span data-stu-id="a3937-112">Expiring subscription</span></span>  
  
     <span data-ttu-id="a3937-113">この状態値は、すべての種類のレプリケーションに適用されます。</span><span class="sxs-lookup"><span data-stu-id="a3937-113">This status value applies to all types of replication.</span></span> <span data-ttu-id="a3937-114">詳細については、「 [Set Thresholds and Warnings in Replication Monitor](set-thresholds-and-warnings-in-replication-monitor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a3937-114">For more information, see [Set Thresholds and Warnings in Replication Monitor](set-thresholds-and-warnings-in-replication-monitor.md).</span></span>  
  
-   <span data-ttu-id="a3937-115">[パフォーマンス クリティカル]</span><span class="sxs-lookup"><span data-stu-id="a3937-115">Performance critical</span></span>  
  
     <span data-ttu-id="a3937-116">この状態値は、トランザクション レプリケーションとマージ レプリケーションに適用されます。</span><span class="sxs-lookup"><span data-stu-id="a3937-116">This status value applies to transactional replication and merge replication.</span></span> <span data-ttu-id="a3937-117">詳細については、「[レプリケーション モニターを使用したパフォーマンスの監視](monitor-performance-with-replication-monitor.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a3937-117">For more information, see [Monitor Performance with Replication Monitor](monitor-performance-with-replication-monitor.md).</span></span>  
  
-   <span data-ttu-id="a3937-118">[長期マージ]</span><span class="sxs-lookup"><span data-stu-id="a3937-118">Long-running merge</span></span>  
  
     <span data-ttu-id="a3937-119">この状態値はマージ レプリケーションに適用されます。</span><span class="sxs-lookup"><span data-stu-id="a3937-119">This status value applies to merge replication.</span></span> <span data-ttu-id="a3937-120">詳細については、「[レプリケーション モニターを使用したパフォーマンスの監視](monitor-performance-with-replication-monitor.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a3937-120">For more information, see [Monitor Performance with Replication Monitor](monitor-performance-with-replication-monitor.md).</span></span>  
  
 <span data-ttu-id="a3937-121">パブリケーションおよびサブスクリプションの状態の他に、マージ レプリケーションではアーティクル レベルの統計が使用できます。この情報は、マージ フェーズの完了までに要する時間、指定されたアーティクルの処理に費やされた時間、サブスクライバーが使用している接続の種類、およびその他の重要な情報についての詳細を提供します。</span><span class="sxs-lookup"><span data-stu-id="a3937-121">In addition to publication and subscription status, merge replication provides article-level statistics, which give detailed information about: how much longer a merge phase will take to complete; how much time was spent processing a given article; the type of connection a Subscriber is using; and other important information.</span></span> <span data-ttu-id="a3937-122">統計情報は、レプリケーション モニターの [マージ エージェント] ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="a3937-122">The statistics are displayed in the Merge Agent window in Replication Monitor.</span></span> <span data-ttu-id="a3937-123">スナップショット レプリケーションおよびトランザクション レプリケーションでは、ディストリビューション エージェントの処理に関する詳細が提供されます。</span><span class="sxs-lookup"><span data-stu-id="a3937-123">Snapshot and transactional replication provide detailed information on Distribution Agent processing.</span></span>  
  
 <span data-ttu-id="a3937-124">**パブリケーションおよびサブスクリプションの状態を表示するには**</span><span class="sxs-lookup"><span data-stu-id="a3937-124">**To view publication and subscription status**</span></span>  
  
-   <span data-ttu-id="a3937-125">レプリケーションモニター:[レプリケーションモニターを使用して情報を表示し、タスクを実行](view-information-and-perform-tasks-replication-monitor.md)します。</span><span class="sxs-lookup"><span data-stu-id="a3937-125">Replication Monitor: [View Information and Perform Tasks using Replication Monitor](view-information-and-perform-tasks-replication-monitor.md).</span></span>
  
  
## <a name="publication-status-values"></a><span data-ttu-id="a3937-126">パブリケーションの状態の値</span><span class="sxs-lookup"><span data-stu-id="a3937-126">Publication Status Values</span></span>  
 <span data-ttu-id="a3937-127">次の表は、パブリケーションの状態の値と対応するアイコンを優先度順に示しています。</span><span class="sxs-lookup"><span data-stu-id="a3937-127">The following table shows publication status values and their corresponding icons in priority order.</span></span>  
  
|<span data-ttu-id="a3937-128">Status</span><span class="sxs-lookup"><span data-stu-id="a3937-128">Status</span></span>|<span data-ttu-id="a3937-129">アイコン</span><span class="sxs-lookup"><span data-stu-id="a3937-129">Icon</span></span>|  
|------------|----------|  
|<span data-ttu-id="a3937-130">エラー</span><span class="sxs-lookup"><span data-stu-id="a3937-130">Error</span></span>|<span data-ttu-id="a3937-131">![UI アイコン: エラー](../media/repl-icon-error.gif "UI アイコン: エラー")</span><span class="sxs-lookup"><span data-stu-id="a3937-131">![UI icon: error](../media/repl-icon-error.gif "UI icon: error")</span></span>|  
|<span data-ttu-id="a3937-132">[パフォーマンス クリティカル]</span><span class="sxs-lookup"><span data-stu-id="a3937-132">Performance critical</span></span>|<span data-ttu-id="a3937-133">![UI アイコン: 警告](../media/repl-icon-warn.gif "UI アイコン: 警告")</span><span class="sxs-lookup"><span data-stu-id="a3937-133">![UI icon: warning](../media/repl-icon-warn.gif "UI icon: warning")</span></span>|  
|<span data-ttu-id="a3937-134">[失敗したコマンドの再試行]</span><span class="sxs-lookup"><span data-stu-id="a3937-134">Retrying failed command</span></span>|<span data-ttu-id="a3937-135">![UI アイコン: レプリケーション エージェントの再試行](../media/repl-icon-retry.gif "UI アイコン: レプリケーション エージェントの再試行")</span><span class="sxs-lookup"><span data-stu-id="a3937-135">![UI icon: replication agent retry](../media/repl-icon-retry.gif "UI icon: replication agent retry")</span></span>|  
|<span data-ttu-id="a3937-136">[OK]</span><span class="sxs-lookup"><span data-stu-id="a3937-136">OK</span></span>|<span data-ttu-id="a3937-137">なし</span><span class="sxs-lookup"><span data-stu-id="a3937-137">none</span></span>|  
  
## <a name="subscription-status-values"></a><span data-ttu-id="a3937-138">サブスクリプションの状態値</span><span class="sxs-lookup"><span data-stu-id="a3937-138">Subscription Status Values</span></span>  
 <span data-ttu-id="a3937-139">次の表は、サブスクリプションの状態値と対応するアイコンを優先度順に示しています。</span><span class="sxs-lookup"><span data-stu-id="a3937-139">The following tables show subscription status values and their corresponding icons in priority order.</span></span> <span data-ttu-id="a3937-140">サブスクリプションは、" **まもなく期限切れ/期限切れ** " と " **失敗したコマンドの再試行**" など同時に 2 つの状態になることがあります。その場合、最も優先度の高い状態が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a3937-140">It is possible for a subscription to be in two states at the same time, such as **Expiring soon/Expired** and **Retrying failed command**; the highest priority status is displayed.</span></span>  
  
 <span data-ttu-id="a3937-141">状態値 " **パフォーマンス クリティカル**"、" **まもなく期限切れ/期限切れ**"、および " **初期化されていないサブスクリプション** " は警告です。</span><span class="sxs-lookup"><span data-stu-id="a3937-141">The status values **Performance critical**, **Expiring soon/Expired**, and **Uninitialized** are warnings.</span></span> <span data-ttu-id="a3937-142">警告が表示されるとき、レプリケーション モニターにはエージェントが実行中であるかどうかも表示されます。</span><span class="sxs-lookup"><span data-stu-id="a3937-142">When a warning is displayed, Replication Monitor also displays whether an agent is running.</span></span> <span data-ttu-id="a3937-143">たとえば、 **[実行中]、[パフォーマンス クリティカル]** という形で状態が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a3937-143">For example, the status could be **Running, Performance critical**.</span></span>  
  
### <a name="transactional-subscriptions"></a><span data-ttu-id="a3937-144">トランザクション サブスクリプション</span><span class="sxs-lookup"><span data-stu-id="a3937-144">Transactional subscriptions</span></span>  
  
|<span data-ttu-id="a3937-145">Status</span><span class="sxs-lookup"><span data-stu-id="a3937-145">Status</span></span>|<span data-ttu-id="a3937-146">アイコン</span><span class="sxs-lookup"><span data-stu-id="a3937-146">Icon</span></span>|  
|------------|----------|  
|<span data-ttu-id="a3937-147">エラー</span><span class="sxs-lookup"><span data-stu-id="a3937-147">Error</span></span>|<span data-ttu-id="a3937-148">![UI アイコン: エラー](../media/repl-icon-error.gif "UI アイコン: エラー")</span><span class="sxs-lookup"><span data-stu-id="a3937-148">![UI icon: error](../media/repl-icon-error.gif "UI icon: error")</span></span>|  
|<span data-ttu-id="a3937-149">[パフォーマンス クリティカル]</span><span class="sxs-lookup"><span data-stu-id="a3937-149">Performance critical</span></span>|<span data-ttu-id="a3937-150">![UI アイコン: 警告](../media/repl-icon-warn.gif "UI アイコン: 警告")</span><span class="sxs-lookup"><span data-stu-id="a3937-150">![UI icon: warning](../media/repl-icon-warn.gif "UI icon: warning")</span></span>|  
|<span data-ttu-id="a3937-151">まもなく期限切れ/期限切れ</span><span class="sxs-lookup"><span data-stu-id="a3937-151">Expiring soon/Expired</span></span>|<span data-ttu-id="a3937-152">![UI アイコン: 警告](../media/repl-icon-warn.gif "UI アイコン: 警告")</span><span class="sxs-lookup"><span data-stu-id="a3937-152">![UI icon: warning](../media/repl-icon-warn.gif "UI icon: warning")</span></span>|  
|<span data-ttu-id="a3937-153">[初期化されていないサブスクリプション]</span><span class="sxs-lookup"><span data-stu-id="a3937-153">Uninitialized subscription</span></span>|<span data-ttu-id="a3937-154">![UI アイコン: 警告](../media/repl-icon-warn.gif "UI アイコン: 警告")</span><span class="sxs-lookup"><span data-stu-id="a3937-154">![UI icon: warning](../media/repl-icon-warn.gif "UI icon: warning")</span></span>|  
|<span data-ttu-id="a3937-155">[失敗したコマンドの再試行]</span><span class="sxs-lookup"><span data-stu-id="a3937-155">Retrying failed command</span></span>|<span data-ttu-id="a3937-156">![UI アイコン: レプリケーション エージェントの再試行](../media/repl-icon-retry.gif "UI アイコン: レプリケーション エージェントの再試行")</span><span class="sxs-lookup"><span data-stu-id="a3937-156">![UI icon: replication agent retry](../media/repl-icon-retry.gif "UI icon: replication agent retry")</span></span>|  
|<span data-ttu-id="a3937-157">[実行されていません]</span><span class="sxs-lookup"><span data-stu-id="a3937-157">Not running</span></span>|<span data-ttu-id="a3937-158">![UI アイコン: レプリケーション エージェントの停止](../media/repl-icon-stopped.gif "UI アイコン: レプリケーション エージェントの停止")</span><span class="sxs-lookup"><span data-stu-id="a3937-158">![UI icon: replication agent stopped](../media/repl-icon-stopped.gif "UI icon: replication agent stopped")</span></span>|  
|<span data-ttu-id="a3937-159">実行中</span><span class="sxs-lookup"><span data-stu-id="a3937-159">Running</span></span>|<span data-ttu-id="a3937-160">![UI アイコン: レプリケーション エージェントの実行](../media/repl-icon-running.gif "UI アイコン: レプリケーション エージェントの実行")</span><span class="sxs-lookup"><span data-stu-id="a3937-160">![UI icon: replication agent running](../media/repl-icon-running.gif "UI icon: replication agent running")</span></span>|  
  
### <a name="merge-subscriptions"></a><span data-ttu-id="a3937-161">マージ サブスクリプション</span><span class="sxs-lookup"><span data-stu-id="a3937-161">Merge subscriptions</span></span>  
  
|<span data-ttu-id="a3937-162">Status</span><span class="sxs-lookup"><span data-stu-id="a3937-162">Status</span></span>|<span data-ttu-id="a3937-163">アイコン</span><span class="sxs-lookup"><span data-stu-id="a3937-163">Icon</span></span>|  
|------------|----------|  
|<span data-ttu-id="a3937-164">エラー</span><span class="sxs-lookup"><span data-stu-id="a3937-164">Error</span></span>|<span data-ttu-id="a3937-165">![UI アイコン: エラー](../media/repl-icon-error.gif "UI アイコン: エラー")</span><span class="sxs-lookup"><span data-stu-id="a3937-165">![UI icon: error](../media/repl-icon-error.gif "UI icon: error")</span></span>|  
|<span data-ttu-id="a3937-166">[パフォーマンス クリティカル]</span><span class="sxs-lookup"><span data-stu-id="a3937-166">Performance critical</span></span>|<span data-ttu-id="a3937-167">![UI アイコン: 警告](../media/repl-icon-warn.gif "UI アイコン: 警告")</span><span class="sxs-lookup"><span data-stu-id="a3937-167">![UI icon: warning](../media/repl-icon-warn.gif "UI icon: warning")</span></span>|  
|<span data-ttu-id="a3937-168">[長期マージ]</span><span class="sxs-lookup"><span data-stu-id="a3937-168">Long-running merge</span></span>|<span data-ttu-id="a3937-169">![UI アイコン: 警告](../media/repl-icon-warn.gif "UI アイコン: 警告")</span><span class="sxs-lookup"><span data-stu-id="a3937-169">![UI icon: warning](../media/repl-icon-warn.gif "UI icon: warning")</span></span>|  
|<span data-ttu-id="a3937-170">まもなく期限切れ/期限切れ</span><span class="sxs-lookup"><span data-stu-id="a3937-170">Expiring soon/Expired</span></span>|<span data-ttu-id="a3937-171">![UI アイコン: 警告](../media/repl-icon-warn.gif "UI アイコン: 警告")</span><span class="sxs-lookup"><span data-stu-id="a3937-171">![UI icon: warning](../media/repl-icon-warn.gif "UI icon: warning")</span></span>|  
|<span data-ttu-id="a3937-172">[初期化されていないサブスクリプション]</span><span class="sxs-lookup"><span data-stu-id="a3937-172">Uninitialized subscription</span></span>|<span data-ttu-id="a3937-173">![UI アイコン: 警告](../media/repl-icon-warn.gif "UI アイコン: 警告")</span><span class="sxs-lookup"><span data-stu-id="a3937-173">![UI icon: warning](../media/repl-icon-warn.gif "UI icon: warning")</span></span>|  
|<span data-ttu-id="a3937-174">[失敗したコマンドの再試行]</span><span class="sxs-lookup"><span data-stu-id="a3937-174">Retrying failed command</span></span>|<span data-ttu-id="a3937-175">![UI アイコン: レプリケーション エージェントの再試行](../media/repl-icon-retry.gif "UI アイコン: レプリケーション エージェントの再試行")</span><span class="sxs-lookup"><span data-stu-id="a3937-175">![UI icon: replication agent retry](../media/repl-icon-retry.gif "UI icon: replication agent retry")</span></span>|  
|<span data-ttu-id="a3937-176">[同期中]</span><span class="sxs-lookup"><span data-stu-id="a3937-176">Synchronizing</span></span>|<span data-ttu-id="a3937-177">![UI アイコン: レプリケーション エージェントの実行](../media/repl-icon-running.gif "UI アイコン: レプリケーション エージェントの実行")</span><span class="sxs-lookup"><span data-stu-id="a3937-177">![UI icon: replication agent running](../media/repl-icon-running.gif "UI icon: replication agent running")</span></span>|  
|<span data-ttu-id="a3937-178">同期されていません</span><span class="sxs-lookup"><span data-stu-id="a3937-178">Not Synchronizing</span></span>|<span data-ttu-id="a3937-179">![UI アイコン: レプリケーション エージェントの停止](../media/repl-icon-stopped.gif "UI アイコン: レプリケーション エージェントの停止")</span><span class="sxs-lookup"><span data-stu-id="a3937-179">![UI icon: replication agent stopped](../media/repl-icon-stopped.gif "UI icon: replication agent stopped")</span></span>|  
  
### <a name="snapshot-subscriptions"></a><span data-ttu-id="a3937-180">スナップショット サブスクリプション</span><span class="sxs-lookup"><span data-stu-id="a3937-180">Snapshot subscriptions</span></span>  
  
|<span data-ttu-id="a3937-181">Status</span><span class="sxs-lookup"><span data-stu-id="a3937-181">Status</span></span>|<span data-ttu-id="a3937-182">アイコン</span><span class="sxs-lookup"><span data-stu-id="a3937-182">Icon</span></span>|  
|------------|----------|  
|<span data-ttu-id="a3937-183">エラー</span><span class="sxs-lookup"><span data-stu-id="a3937-183">Error</span></span>|<span data-ttu-id="a3937-184">![UI アイコン: エラー](../media/repl-icon-error.gif "UI アイコン: エラー")</span><span class="sxs-lookup"><span data-stu-id="a3937-184">![UI icon: error](../media/repl-icon-error.gif "UI icon: error")</span></span>|  
|<span data-ttu-id="a3937-185">まもなく期限切れ/期限切れ</span><span class="sxs-lookup"><span data-stu-id="a3937-185">Expiring soon/Expired</span></span>|<span data-ttu-id="a3937-186">![UI アイコン: 警告](../media/repl-icon-warn.gif "UI アイコン: 警告")</span><span class="sxs-lookup"><span data-stu-id="a3937-186">![UI icon: warning](../media/repl-icon-warn.gif "UI icon: warning")</span></span>|  
|<span data-ttu-id="a3937-187">[初期化されていないサブスクリプション]</span><span class="sxs-lookup"><span data-stu-id="a3937-187">Uninitialized subscription</span></span>|<span data-ttu-id="a3937-188">![UI アイコン: 警告](../media/repl-icon-warn.gif "UI アイコン: 警告")</span><span class="sxs-lookup"><span data-stu-id="a3937-188">![UI icon: warning](../media/repl-icon-warn.gif "UI icon: warning")</span></span>|  
|<span data-ttu-id="a3937-189">[失敗したコマンドの再試行]</span><span class="sxs-lookup"><span data-stu-id="a3937-189">Retrying failed command</span></span>|<span data-ttu-id="a3937-190">![UI アイコン: レプリケーション エージェントの再試行](../media/repl-icon-retry.gif "UI アイコン: レプリケーション エージェントの再試行")</span><span class="sxs-lookup"><span data-stu-id="a3937-190">![UI icon: replication agent retry](../media/repl-icon-retry.gif "UI icon: replication agent retry")</span></span>|  
|<span data-ttu-id="a3937-191">[同期中]</span><span class="sxs-lookup"><span data-stu-id="a3937-191">Synchronizing</span></span>|<span data-ttu-id="a3937-192">![UI アイコン: レプリケーション エージェントの実行](../media/repl-icon-running.gif "UI アイコン: レプリケーション エージェントの実行")</span><span class="sxs-lookup"><span data-stu-id="a3937-192">![UI icon: replication agent running](../media/repl-icon-running.gif "UI icon: replication agent running")</span></span>|  
|<span data-ttu-id="a3937-193">同期されていません</span><span class="sxs-lookup"><span data-stu-id="a3937-193">Not Synchronizing</span></span>|<span data-ttu-id="a3937-194">![UI アイコン: レプリケーション エージェントの停止](../media/repl-icon-stopped.gif "UI アイコン: レプリケーション エージェントの停止")</span><span class="sxs-lookup"><span data-stu-id="a3937-194">![UI icon: replication agent stopped](../media/repl-icon-stopped.gif "UI icon: replication agent stopped")</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a3937-195">参照</span><span class="sxs-lookup"><span data-stu-id="a3937-195">See Also</span></span>  
 [<span data-ttu-id="a3937-196">レプリケーションの監視</span><span class="sxs-lookup"><span data-stu-id="a3937-196">Monitoring Replication</span></span>](../monitoring-replication.md)  
  
  
