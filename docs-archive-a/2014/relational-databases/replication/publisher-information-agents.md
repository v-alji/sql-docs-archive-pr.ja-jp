---
title: パブリッシャー情報、[エージェント] | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.publisherinfo.commonjobs.f1
ms.assetid: 2346c00d-c269-45a1-af14-68e7fd7ebd7e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: bdd2055ed022257524bc4d2784bdc333537be855
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631790"
---
# <a name="publisher-information-agents"></a><span data-ttu-id="45106-102">パブリッシャー情報、[エージェント]</span><span class="sxs-lookup"><span data-stu-id="45106-102">Publisher Information, Agents</span></span>
  <span data-ttu-id="45106-103">**[エージェント]** タブには、パブリッシャーに関連するエージェントおよびメンテナンス ジョブに関する詳細情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="45106-103">The **Agents** tab displays information about the agents and maintenance jobs that are associated with the Publisher:</span></span>  
  
-   <span data-ttu-id="45106-104">すべてのパブリケーションで表示されるスナップショット エージェント</span><span class="sxs-lookup"><span data-stu-id="45106-104">Snapshot Agent, which is displayed for all publications.</span></span>  
  
-   <span data-ttu-id="45106-105">すべてのトランザクション パブリケーションで表示されるログ リーダー エージェント</span><span class="sxs-lookup"><span data-stu-id="45106-105">Log Reader Agent, which is displayed for all transactional publications.</span></span>  
  
-   <span data-ttu-id="45106-106">キュー更新サブスクリプション用に有効になっているトランザクション パブリケーションで表示されるキュー リーダー エージェント</span><span class="sxs-lookup"><span data-stu-id="45106-106">Queue Reader Agent, which is displayed for those transactional publications that are enabled for queued updating subscriptions.</span></span>  
  
-   <span data-ttu-id="45106-107">すべてのパブリケーションで表示されるメンテナンス ジョブ</span><span class="sxs-lookup"><span data-stu-id="45106-107">Maintenance jobs, displayed for all publications:</span></span>  
  
    -   <span data-ttu-id="45106-108">データ検証で問題が見つかったサブスクリプションの再初期化</span><span class="sxs-lookup"><span data-stu-id="45106-108">Reinitialize subscriptions that have data validation failures</span></span>  
  
    -   <span data-ttu-id="45106-109">エージェント履歴のクリーンアップ: ディストリビューション</span><span class="sxs-lookup"><span data-stu-id="45106-109">Agent history cleanup: distribution</span></span>  
  
    -   <span data-ttu-id="45106-110">ディストリビューションのレプリケーション モニターの状態更新機能</span><span class="sxs-lookup"><span data-stu-id="45106-110">Replication monitoring refresher for distribution</span></span>  
  
    -   <span data-ttu-id="45106-111">レプリケーション エージェントの検査</span><span class="sxs-lookup"><span data-stu-id="45106-111">Replication agents checkup</span></span>  
  
    -   <span data-ttu-id="45106-112">ディストリビューションのクリーンアップ: ディストリビューション</span><span class="sxs-lookup"><span data-stu-id="45106-112">Distribution cleanup: distribution</span></span>  
  
    -   <span data-ttu-id="45106-113">有効期限が切れたサブスクリプションのクリーンアップ</span><span class="sxs-lookup"><span data-stu-id="45106-113">Expired subscription cleanup</span></span>  
  
 <span data-ttu-id="45106-114">これらのジョブの詳細については、「[Replication Agent Administration](agents/replication-agent-administration.md)」 (レプリケーション エージェントの管理) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="45106-114">For more information about these jobs, see [Replication Agent Administration](agents/replication-agent-administration.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="45106-115">オプション</span><span class="sxs-lookup"><span data-stu-id="45106-115">Options</span></span>  
 <span data-ttu-id="45106-116">エージェントまたはジョブに関する情報を表示するには、 **[エージェントとジョブの種類]** メニューから選択します。</span><span class="sxs-lookup"><span data-stu-id="45106-116">To display information about an agent or job, select from the **Agent and Job Types** drop-down menu.</span></span> <span data-ttu-id="45106-117">エージェントまたはジョブに関する詳細情報やタスクを調べるには、対象のエージェントまたはジョブの行を右クリックし、ショートカット メニューのオプションをクリックします。</span><span class="sxs-lookup"><span data-stu-id="45106-117">For more detailed information and tasks that are related to an agent or job, right-click the row for that agent or job, and then click an option on the shortcut menu.</span></span> <span data-ttu-id="45106-118">グリッドにデータを表示する方法を変更するには、グリッドを右クリックし、次のいずれかのオプションをクリックします。</span><span class="sxs-lookup"><span data-stu-id="45106-118">To change the way that the grid displays data, right-click the grid, and then click one of the following options:</span></span>  
  
-   <span data-ttu-id="45106-119">**[並べ替え]** : **[列の並べ替え]** ダイアログ ボックスで、1 つ以上の列を基準にして並べ替えを行います。</span><span class="sxs-lookup"><span data-stu-id="45106-119">**Sort**: Sort on one or more columns in the **Sort Columns** dialog box.</span></span>  
  
-   <span data-ttu-id="45106-120">**[表示する列の選択]** : **[列の選択]** ダイアログ ボックスで、表示する列とその表示順序を選択します。</span><span class="sxs-lookup"><span data-stu-id="45106-120">**Choose Columns to Show**: Select which columns to display and the order in which to display them in the **Choose Columns** dialog box.</span></span>  
  
-   <span data-ttu-id="45106-121">**[フィルター]** : **[フィルターの設定]** ダイアログ ボックスで、列の値に基づいてグリッドの行をフィルター選択します。</span><span class="sxs-lookup"><span data-stu-id="45106-121">**Filter**: Filter rows in the grid based on column values in the **Filter Settings** dialog box.</span></span>  
  
-   <span data-ttu-id="45106-122">**[フィルターのクリア]** : グリッドのフィルター設定をすべてクリアします。</span><span class="sxs-lookup"><span data-stu-id="45106-122">**Clear Filter**: Clear any filter settings for the grid.</span></span>  
  
 <span data-ttu-id="45106-123">フィルター設定は各グリッドに固有です。</span><span class="sxs-lookup"><span data-stu-id="45106-123">Filter settings are specific to each grid.</span></span> <span data-ttu-id="45106-124">列の選択と並べ替えは、各パブリッシャーのパブリケーション グリッドなど、同じ種類のすべてのグリッドに適用されます。</span><span class="sxs-lookup"><span data-stu-id="45106-124">Column selection and sorting are applied to all grids of the same type, such as the publications grid for each Publisher.</span></span>  
  
 <span data-ttu-id="45106-125">この後のセクションでは、このタブでエージェントまたはジョブごとに表示されるデータについて説明します。</span><span class="sxs-lookup"><span data-stu-id="45106-125">The following sections describe the data that is displayed on this tab for each agent or job.</span></span>  
  
### <a name="snapshot-agent"></a><span data-ttu-id="45106-126">スナップショット エージェント</span><span class="sxs-lookup"><span data-stu-id="45106-126">Snapshot Agent</span></span>  
 <span data-ttu-id="45106-127">**状態**</span><span class="sxs-lookup"><span data-stu-id="45106-127">**Status**</span></span>  
 <span data-ttu-id="45106-128">エージェントの状態です。</span><span class="sxs-lookup"><span data-stu-id="45106-128">The status of the agent.</span></span> <span data-ttu-id="45106-129">表示される状態の種類を、次に示します。</span><span class="sxs-lookup"><span data-stu-id="45106-129">The following list shows the possible status values:</span></span>  
  
-   <span data-ttu-id="45106-130">エラー</span><span class="sxs-lookup"><span data-stu-id="45106-130">Error</span></span>  
  
-   <span data-ttu-id="45106-131">[再試行]</span><span class="sxs-lookup"><span data-stu-id="45106-131">Retry</span></span>  
  
-   <span data-ttu-id="45106-132">実行中</span><span class="sxs-lookup"><span data-stu-id="45106-132">Running</span></span>  
  
-   <span data-ttu-id="45106-133">[完了]</span><span class="sxs-lookup"><span data-stu-id="45106-133">Completed</span></span>  
  
 <span data-ttu-id="45106-134">**パブリケーション**</span><span class="sxs-lookup"><span data-stu-id="45106-134">**Publication**</span></span>  
 <span data-ttu-id="45106-135">エージェントが関連付けられているパブリケーションの名前です。</span><span class="sxs-lookup"><span data-stu-id="45106-135">The name of the publication with which the agent is associated.</span></span>  
  
 <span data-ttu-id="45106-136">**[前回の開始時刻]**</span><span class="sxs-lookup"><span data-stu-id="45106-136">**Last Start Time**</span></span>  
 <span data-ttu-id="45106-137">前回のエージェントの開始時刻です。</span><span class="sxs-lookup"><span data-stu-id="45106-137">The last time at which the agent started.</span></span>  
  
 <span data-ttu-id="45106-138">**Duration**</span><span class="sxs-lookup"><span data-stu-id="45106-138">**Duration**</span></span>  
 <span data-ttu-id="45106-139">エージェントが実行された時間の長さです。</span><span class="sxs-lookup"><span data-stu-id="45106-139">The length of time the agent has run.</span></span> <span data-ttu-id="45106-140">この時間は、エージェントが現在実行中の場合は経過時間、エージェントが以前に実行されている場合は合計時間を表します。</span><span class="sxs-lookup"><span data-stu-id="45106-140">The time represents elapsed time if the agent is currently running, and total time if the agent has run previously.</span></span>  
  
 <span data-ttu-id="45106-141">**[最後のアクション]**</span><span class="sxs-lookup"><span data-stu-id="45106-141">**Last Action**</span></span>  
 <span data-ttu-id="45106-142">エージェントが最後に実行されたときに最後に実行されたアクションです。</span><span class="sxs-lookup"><span data-stu-id="45106-142">The last action performed during the most recent run of the agent.</span></span>  
  
 <span data-ttu-id="45106-143">**[配信率]**</span><span class="sxs-lookup"><span data-stu-id="45106-143">**Delivery Rate**</span></span>  
 <span data-ttu-id="45106-144">エージェントが最後に実行されたときにディストリビューション データベースで初期化コマンドがコミットされた頻度 (1 秒あたりのコマンド数) です。</span><span class="sxs-lookup"><span data-stu-id="45106-144">The rate, in commands per second, at which initialization commands are committed in the distribution database during the most recent run of the agent.</span></span>  
  
 <span data-ttu-id="45106-145">**[#Trans]**</span><span class="sxs-lookup"><span data-stu-id="45106-145">**#Trans**</span></span>  
 <span data-ttu-id="45106-146">エージェントが最後に実行されたときにディストリビューション データベースでコミットされたトランザクションの数です。</span><span class="sxs-lookup"><span data-stu-id="45106-146">The number of transactions committed in the distribution database during the most recent run of the agent.</span></span>  
  
 <span data-ttu-id="45106-147">**[#Cmds]**</span><span class="sxs-lookup"><span data-stu-id="45106-147">**#Cmds**</span></span>  
 <span data-ttu-id="45106-148">エージェントが最後に実行されたときにディストリビューション データベースでコミットされたコマンドの数です。</span><span class="sxs-lookup"><span data-stu-id="45106-148">The number of commands committed in the distribution database during the most recent run of the agent.</span></span> <span data-ttu-id="45106-149">更新などのデータ変更がコマンドに相当します。</span><span class="sxs-lookup"><span data-stu-id="45106-149">A command is equivalent to a data change, such as an update.</span></span>  
  
### <a name="log-reader-agent"></a><span data-ttu-id="45106-150">ログ リーダー エージェント (Log Reader Agent)</span><span class="sxs-lookup"><span data-stu-id="45106-150">Log Reader Agent</span></span>  
 <span data-ttu-id="45106-151">**状態**</span><span class="sxs-lookup"><span data-stu-id="45106-151">**Status**</span></span>  
 <span data-ttu-id="45106-152">エージェントの状態です。</span><span class="sxs-lookup"><span data-stu-id="45106-152">The status of the agent.</span></span> <span data-ttu-id="45106-153">表示される状態の種類を、次に示します。</span><span class="sxs-lookup"><span data-stu-id="45106-153">The following list shows the possible status values:</span></span>  
  
-   <span data-ttu-id="45106-154">エラー</span><span class="sxs-lookup"><span data-stu-id="45106-154">Error</span></span>  
  
-   <span data-ttu-id="45106-155">[再試行]</span><span class="sxs-lookup"><span data-stu-id="45106-155">Retry</span></span>  
  
-   <span data-ttu-id="45106-156">実行中</span><span class="sxs-lookup"><span data-stu-id="45106-156">Running</span></span>  
  
-   <span data-ttu-id="45106-157">[実行されていません]</span><span class="sxs-lookup"><span data-stu-id="45106-157">Not running</span></span>  
  
 <span data-ttu-id="45106-158">**パブリケーション データベース**</span><span class="sxs-lookup"><span data-stu-id="45106-158">**Publication Database**</span></span>  
 <span data-ttu-id="45106-159">エージェントが関連付けられているパブリケーションの名前です。</span><span class="sxs-lookup"><span data-stu-id="45106-159">The name of the publication with which the agent is associated.</span></span>  
  
 <span data-ttu-id="45106-160">**[前回の開始時刻]**</span><span class="sxs-lookup"><span data-stu-id="45106-160">**Last Start Time**</span></span>  
 <span data-ttu-id="45106-161">前回のエージェントの開始時刻です。</span><span class="sxs-lookup"><span data-stu-id="45106-161">The last time at which the agent started.</span></span>  
  
 <span data-ttu-id="45106-162">**Duration**</span><span class="sxs-lookup"><span data-stu-id="45106-162">**Duration**</span></span>  
 <span data-ttu-id="45106-163">エージェントが実行された時間の長さです。</span><span class="sxs-lookup"><span data-stu-id="45106-163">The length of time the agent has run.</span></span> <span data-ttu-id="45106-164">この時間は、エージェントが現在実行中の場合は経過時間、エージェントが以前に実行されている場合は合計時間を表します。</span><span class="sxs-lookup"><span data-stu-id="45106-164">The time represents elapsed time if the agent is currently running, and total time if the agent has run previously.</span></span>  
  
 <span data-ttu-id="45106-165">**[最後のアクション]**</span><span class="sxs-lookup"><span data-stu-id="45106-165">**Last Action**</span></span>  
 <span data-ttu-id="45106-166">エージェントが最後に実行されたときに最後に実行されたアクションです。</span><span class="sxs-lookup"><span data-stu-id="45106-166">The last action performed during the most recent run of the agent.</span></span>  
  
 <span data-ttu-id="45106-167">**[配信率]**</span><span class="sxs-lookup"><span data-stu-id="45106-167">**Delivery Rate**</span></span>  
 <span data-ttu-id="45106-168">ディストリビューション データベースで変更がコミットされた頻度 (1 秒あたりのコマンド数) です。</span><span class="sxs-lookup"><span data-stu-id="45106-168">The rate, in commands per second, at which changes are committed in the distribution database.</span></span>  
  
 <span data-ttu-id="45106-169">**待機時間**</span><span class="sxs-lookup"><span data-stu-id="45106-169">**Latency**</span></span>  
 <span data-ttu-id="45106-170">パブリケーション データベースで最新の変更がコミットされてから、ディストリビューション データベースで対応するコマンドがコミットされるまでに経過した時間 (秒単位) です。</span><span class="sxs-lookup"><span data-stu-id="45106-170">The amount of time, in seconds, that has elapsed between the most recent change being committed in the publication database, and the corresponding command being committed in the distribution database.</span></span>  
  
 <span data-ttu-id="45106-171">**[#Trans]**</span><span class="sxs-lookup"><span data-stu-id="45106-171">**#Trans**</span></span>  
 <span data-ttu-id="45106-172">エージェントが最後に実行されたときにディストリビューション データベースでコミットされたトランザクションの数です。</span><span class="sxs-lookup"><span data-stu-id="45106-172">The number of transactions committed in the distribution database during the most recent run of the agent.</span></span>  
  
 <span data-ttu-id="45106-173">**[#Cmds]**</span><span class="sxs-lookup"><span data-stu-id="45106-173">**#Cmds**</span></span>  
 <span data-ttu-id="45106-174">エージェントが最後に実行されたときにディストリビューション データベースでコミットされたコマンドの数です。</span><span class="sxs-lookup"><span data-stu-id="45106-174">The number of commands committed in the distribution database during the most recent run of the agent.</span></span> <span data-ttu-id="45106-175">更新などのデータ変更がコマンドに相当します。</span><span class="sxs-lookup"><span data-stu-id="45106-175">A command is equivalent to a data change, such as an update.</span></span>  
  
 <span data-ttu-id="45106-176">**[Avg. #Cmds]**</span><span class="sxs-lookup"><span data-stu-id="45106-176">**Avg. #Cmds**</span></span>  
 <span data-ttu-id="45106-177">エージェントが最後に実行されたときの 1 トランザクションあたりの平均コマンド数です。</span><span class="sxs-lookup"><span data-stu-id="45106-177">The average number of commands per transaction during the most recent run of the agent.</span></span>  
  
### <a name="queue-reader-agent"></a><span data-ttu-id="45106-178">キュー リーダー エージェント (Queue Reader Agent)</span><span class="sxs-lookup"><span data-stu-id="45106-178">Queue Reader Agent</span></span>  
 <span data-ttu-id="45106-179">**状態**</span><span class="sxs-lookup"><span data-stu-id="45106-179">**Status**</span></span>  
 <span data-ttu-id="45106-180">エージェントの状態です。</span><span class="sxs-lookup"><span data-stu-id="45106-180">The status of the agent.</span></span> <span data-ttu-id="45106-181">表示される状態の種類を、次に示します。</span><span class="sxs-lookup"><span data-stu-id="45106-181">The following list shows the possible status values:</span></span>  
  
-   <span data-ttu-id="45106-182">エラー</span><span class="sxs-lookup"><span data-stu-id="45106-182">Error</span></span>  
  
-   <span data-ttu-id="45106-183">[再試行]</span><span class="sxs-lookup"><span data-stu-id="45106-183">Retry</span></span>  
  
-   <span data-ttu-id="45106-184">実行中</span><span class="sxs-lookup"><span data-stu-id="45106-184">Running</span></span>  
  
-   <span data-ttu-id="45106-185">[実行されていません]</span><span class="sxs-lookup"><span data-stu-id="45106-185">Not running</span></span>  
  
 <span data-ttu-id="45106-186">**ディストリビューション データベース**</span><span class="sxs-lookup"><span data-stu-id="45106-186">**Distribution Database**</span></span>  
 <span data-ttu-id="45106-187">エージェントが関連付けられているディストリビューション データベースの名前です。</span><span class="sxs-lookup"><span data-stu-id="45106-187">The name of the distribution database with which the agent is associated.</span></span>  
  
 <span data-ttu-id="45106-188">**[前回の開始時刻]**</span><span class="sxs-lookup"><span data-stu-id="45106-188">**Last Start Time**</span></span>  
 <span data-ttu-id="45106-189">前回のエージェントの開始時刻です。</span><span class="sxs-lookup"><span data-stu-id="45106-189">The last time at which the agent started.</span></span>  
  
 <span data-ttu-id="45106-190">**Duration**</span><span class="sxs-lookup"><span data-stu-id="45106-190">**Duration**</span></span>  
 <span data-ttu-id="45106-191">エージェントが実行された時間の長さです。</span><span class="sxs-lookup"><span data-stu-id="45106-191">The length of time the agent has run.</span></span> <span data-ttu-id="45106-192">この時間は、エージェントが現在実行中の場合は経過時間、エージェントが以前に実行されている場合は合計時間を表します。</span><span class="sxs-lookup"><span data-stu-id="45106-192">The time represents elapsed time if the agent is currently running and total time if the agent has run previously.</span></span>  
  
 <span data-ttu-id="45106-193">**[最後のアクション]**</span><span class="sxs-lookup"><span data-stu-id="45106-193">**Last Action**</span></span>  
 <span data-ttu-id="45106-194">エージェントが最後に実行されたときに最後に実行されたアクションです。</span><span class="sxs-lookup"><span data-stu-id="45106-194">The last action performed during the most recent run of the agent.</span></span>  
  
 <span data-ttu-id="45106-195">**[配信率]**</span><span class="sxs-lookup"><span data-stu-id="45106-195">**Delivery Rate**</span></span>  
 <span data-ttu-id="45106-196">ディストリビューション データベースで変更がコミットされた頻度 (1 秒あたりのコマンド数) です。</span><span class="sxs-lookup"><span data-stu-id="45106-196">The rate, in commands per second, at which changes are committed in the distribution database.</span></span>  
  
 <span data-ttu-id="45106-197">**待機時間**</span><span class="sxs-lookup"><span data-stu-id="45106-197">**Latency**</span></span>  
 <span data-ttu-id="45106-198">サブスクリプション データベースで最新の変更がコミットされてから、パブリケーション データベースで対応するコマンドがコミットされるまでに経過した時間 (秒単位) です。</span><span class="sxs-lookup"><span data-stu-id="45106-198">The amount of time, in seconds, that has elapsed between the most recent change being committed in a subscription database, and the corresponding command being committed in the publication database.</span></span>  
  
 <span data-ttu-id="45106-199">**[#Trans]**</span><span class="sxs-lookup"><span data-stu-id="45106-199">**#Trans**</span></span>  
 <span data-ttu-id="45106-200">エージェントが最後に実行されたときにパブリケーション データベースでコミットされたトランザクションの数です。</span><span class="sxs-lookup"><span data-stu-id="45106-200">The number of transactions committed in the publication database during the most recent run of the agent.</span></span>  
  
 <span data-ttu-id="45106-201">**[#Cmds]**</span><span class="sxs-lookup"><span data-stu-id="45106-201">**#Cmds**</span></span>  
 <span data-ttu-id="45106-202">エージェントが最後に実行されたときにパブリケーション データベースでコミットされたコマンドの数です。</span><span class="sxs-lookup"><span data-stu-id="45106-202">The number of commands committed in the publication database during the most recent run of the agent.</span></span> <span data-ttu-id="45106-203">更新などのデータ変更がコマンドに相当します。</span><span class="sxs-lookup"><span data-stu-id="45106-203">A command is equivalent to a data change, such as an update.</span></span>  
  
 <span data-ttu-id="45106-204">**[Avg. #Cmds]**</span><span class="sxs-lookup"><span data-stu-id="45106-204">**Avg. #Cmds**</span></span>  
 <span data-ttu-id="45106-205">エージェントが最後に実行されたときの 1 トランザクションあたりの平均コマンド数です。</span><span class="sxs-lookup"><span data-stu-id="45106-205">The average number of commands per transaction during the most recent run of the agent.</span></span>  
  
### <a name="maintenance-jobs"></a><span data-ttu-id="45106-206">メンテナンス ジョブ</span><span class="sxs-lookup"><span data-stu-id="45106-206">Maintenance Jobs</span></span>  
 <span data-ttu-id="45106-207">**状態**</span><span class="sxs-lookup"><span data-stu-id="45106-207">**Status**</span></span>  
 <span data-ttu-id="45106-208">それぞれのジョブの状態。</span><span class="sxs-lookup"><span data-stu-id="45106-208">The status of each job.</span></span> <span data-ttu-id="45106-209">表示される状態の種類を、次に示します。</span><span class="sxs-lookup"><span data-stu-id="45106-209">The following list shows the possible status values:</span></span>  
  
-   <span data-ttu-id="45106-210">エラー</span><span class="sxs-lookup"><span data-stu-id="45106-210">Error</span></span>  
  
-   <span data-ttu-id="45106-211">[再試行]</span><span class="sxs-lookup"><span data-stu-id="45106-211">Retry</span></span>  
  
-   <span data-ttu-id="45106-212">実行中</span><span class="sxs-lookup"><span data-stu-id="45106-212">Running</span></span>  
  
-   <span data-ttu-id="45106-213">[実行されていません]</span><span class="sxs-lookup"><span data-stu-id="45106-213">Not running</span></span>  
  
 <span data-ttu-id="45106-214">**ジョブ**</span><span class="sxs-lookup"><span data-stu-id="45106-214">**Job**</span></span>  
 <span data-ttu-id="45106-215">ジョブの名前。</span><span class="sxs-lookup"><span data-stu-id="45106-215">The name of the job.</span></span>  
  
 <span data-ttu-id="45106-216">**[前回の開始時刻]**</span><span class="sxs-lookup"><span data-stu-id="45106-216">**Last Start Time**</span></span>  
 <span data-ttu-id="45106-217">前回のジョブの開始時刻。</span><span class="sxs-lookup"><span data-stu-id="45106-217">The last time at which the job started.</span></span>  
  
 <span data-ttu-id="45106-218">**Duration**</span><span class="sxs-lookup"><span data-stu-id="45106-218">**Duration**</span></span>  
 <span data-ttu-id="45106-219">ジョブが実行された時間の長さ。</span><span class="sxs-lookup"><span data-stu-id="45106-219">The length of time the job has run.</span></span> <span data-ttu-id="45106-220">この時間は、ジョブが現在実行されている場合は経過時間を表し、ジョブの実行が完了している場合は合計時間を表します。</span><span class="sxs-lookup"><span data-stu-id="45106-220">The time represents elapsed time if the job is currently running, and total time if the job has run previously.</span></span>  
  
 <span data-ttu-id="45106-221">**[最後のアクション]**</span><span class="sxs-lookup"><span data-stu-id="45106-221">**Last Action**</span></span>  
 <span data-ttu-id="45106-222">ジョブが最後に実行されたときに最後に実行されたアクションです。</span><span class="sxs-lookup"><span data-stu-id="45106-222">The last action performed during the most recent run of the job.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45106-223">参照</span><span class="sxs-lookup"><span data-stu-id="45106-223">See Also</span></span>  
 <span data-ttu-id="45106-224">[レプリケーション モニターの開始](monitor/start-the-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="45106-224">[Start the Replication Monitor](monitor/start-the-replication-monitor.md) </span></span>  
 <span data-ttu-id="45106-225">[レプリケーション モニターを使用して情報を表示し、タスクを実行する](monitor/view-information-and-perform-tasks-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="45106-225">[View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md) </span></span>  
 [<span data-ttu-id="45106-226">レプリケーションの監視</span><span class="sxs-lookup"><span data-stu-id="45106-226">Monitoring Replication</span></span>](monitoring-replication.md)  
  
  
