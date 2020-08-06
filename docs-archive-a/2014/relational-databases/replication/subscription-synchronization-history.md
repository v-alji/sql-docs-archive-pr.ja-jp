---
title: サブスクリプション、[同期の履歴] (マージサブスクリプション、SQL Server 2005 以降) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.subscription.synchhistory.f1
- sql12.rep.monitor.subscription.downlevelsynchhistory.f1
ms.assetid: 85f666f6-14ee-4f19-b385-e5cc508aabe4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 49fe19f22976116813ac2454b2d08fc1fe47d8de
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643776"
---
# <a name="subscription-synchronization-history-merge-subscription-sql-server-2005-and-later"></a><span data-ttu-id="0165f-102">サブスクリプション、[同期の履歴] (マージ サブスクリプション、SQL Server 2005 以降)</span><span class="sxs-lookup"><span data-stu-id="0165f-102">Subscription, Synchronization History (Merge Subscription, SQL Server 2005 and Later)</span></span>
  <span data-ttu-id="0165f-103">**[同期の履歴]** タブには、マージ エージェントの状態、アーティクル統計、履歴、情報メッセージ、エラー メッセージなど詳細情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0165f-103">The **Synchronization History** tab displays detailed information on the Merge Agent, including status, article statistics, history, informational messages, and any error messages.</span></span>  
  
## <a name="options"></a><span data-ttu-id="0165f-104">オプション</span><span class="sxs-lookup"><span data-stu-id="0165f-104">Options</span></span>  
 <span data-ttu-id="0165f-105">表示するマージ エージェント セッションを **[表示]** メニューで選択した後、 **[マージ エージェントのセッション]** という名前のグリッドで特定のセッションを選択します。</span><span class="sxs-lookup"><span data-stu-id="0165f-105">Select which Merge Agent sessions to view from the **View** menu, and then select a specific session in the grid labeled **Sessions of the Merge Agent**.</span></span> <span data-ttu-id="0165f-106">**[選択されたセッションで処理されるアーティクル]** というラベルの付いたグリッド内に、このセッションの詳細情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0165f-106">Detailed information on this session is displayed in the grid labeled **Articles processed in the selected session**.</span></span>  
  
 <span data-ttu-id="0165f-107">**表示**</span><span class="sxs-lookup"><span data-stu-id="0165f-107">**View**</span></span>  
 <span data-ttu-id="0165f-108">表示するマージ エージェント セッションを選択します。</span><span class="sxs-lookup"><span data-stu-id="0165f-108">Select which Merge Agent sessions to view.</span></span>  
  
 <span data-ttu-id="0165f-109">**状態**</span><span class="sxs-lookup"><span data-stu-id="0165f-109">**Status**</span></span>  
 <span data-ttu-id="0165f-110">セッションの最後のマージ エージェントの状態です。</span><span class="sxs-lookup"><span data-stu-id="0165f-110">The status of the Merge Agent at the end of the session.</span></span> <span data-ttu-id="0165f-111">表示される状態の種類を、次に示します。</span><span class="sxs-lookup"><span data-stu-id="0165f-111">The following list shows the possible status values:</span></span>  
  
-   <span data-ttu-id="0165f-112">エラー</span><span class="sxs-lookup"><span data-stu-id="0165f-112">Error</span></span>  
  
-   <span data-ttu-id="0165f-113">[完了]</span><span class="sxs-lookup"><span data-stu-id="0165f-113">Completed</span></span>  
  
-   <span data-ttu-id="0165f-114">[再試行中]</span><span class="sxs-lookup"><span data-stu-id="0165f-114">Retrying</span></span>  
  
-   <span data-ttu-id="0165f-115">実行中</span><span class="sxs-lookup"><span data-stu-id="0165f-115">Running</span></span>  
  
 <span data-ttu-id="0165f-116">**Start Time**</span><span class="sxs-lookup"><span data-stu-id="0165f-116">**Start Time**</span></span>  
 <span data-ttu-id="0165f-117">セッションの開始時刻です。</span><span class="sxs-lookup"><span data-stu-id="0165f-117">The start time of the session.</span></span>  
  
 <span data-ttu-id="0165f-118">**[終了時刻]**</span><span class="sxs-lookup"><span data-stu-id="0165f-118">**End Time**</span></span>  
 <span data-ttu-id="0165f-119">セッションの終了時刻です。</span><span class="sxs-lookup"><span data-stu-id="0165f-119">The end time of the session.</span></span> <span data-ttu-id="0165f-120">エージェントが停止していない場合は、このフィールドは空になっています。</span><span class="sxs-lookup"><span data-stu-id="0165f-120">If the agent has not stopped, this field is empty.</span></span>  
  
 <span data-ttu-id="0165f-121">**Duration**</span><span class="sxs-lookup"><span data-stu-id="0165f-121">**Duration**</span></span>  
 <span data-ttu-id="0165f-122">セッションでマージ エージェントが動作した時間の長さです。</span><span class="sxs-lookup"><span data-stu-id="0165f-122">The amount of time the Merge Agent has run in a session.</span></span> <span data-ttu-id="0165f-123">この時間は、エージェントが現在実行中の場合は経過時間、エージェントが以前に実行されている場合は合計時間を表します。</span><span class="sxs-lookup"><span data-stu-id="0165f-123">The time represents elapsed time if the agent is currently running and total time if the agent has run previously.</span></span>  
  
 <span data-ttu-id="0165f-124">**[アップロードされたコマンド]**</span><span class="sxs-lookup"><span data-stu-id="0165f-124">**Uploaded Commands**</span></span>  
 <span data-ttu-id="0165f-125">マージ エージェント セッションの間にアップロードされた行数です。</span><span class="sxs-lookup"><span data-stu-id="0165f-125">The number of rows uploaded during the Merge Agent session.</span></span>  
  
 <span data-ttu-id="0165f-126">**[ダウンロードされたコマンド]**</span><span class="sxs-lookup"><span data-stu-id="0165f-126">**Downloaded Commands**</span></span>  
 <span data-ttu-id="0165f-127">マージ エージェント セッションの間にダウンロードされた行数です。</span><span class="sxs-lookup"><span data-stu-id="0165f-127">The number of rows downloaded during the Merge Agent session.</span></span>  
  
 <span data-ttu-id="0165f-128">**エラー メッセージ**</span><span class="sxs-lookup"><span data-stu-id="0165f-128">**Error Message**</span></span>  
 <span data-ttu-id="0165f-129">セッションがエラーで終了した場合、このフィールドにはマージ エージェントによってログに記録された最後のエラー メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0165f-129">If a session ended in an error, this field displays the last error message logged by the Merge Agent.</span></span> <span data-ttu-id="0165f-130">セッションがエラーで終了しなかった場合は、このフィールドは空白です。</span><span class="sxs-lookup"><span data-stu-id="0165f-130">If a session did not end in an error, this field is blank.</span></span>  
  
 <span data-ttu-id="0165f-131">**記事**</span><span class="sxs-lookup"><span data-stu-id="0165f-131">**Article**</span></span>  
 <span data-ttu-id="0165f-132">パブリケーション内の各アーティクルの名前です。パブリケーション全体に対して以下の処理フェーズがあります。</span><span class="sxs-lookup"><span data-stu-id="0165f-132">The name of each article in the publication, and the following processing phases for the entire publication:</span></span>  
  
-   <span data-ttu-id="0165f-133">**[初期化]** 。</span><span class="sxs-lookup"><span data-stu-id="0165f-133">**Initialization**.</span></span> <span data-ttu-id="0165f-134">マージ エージェントを開始することを示しています。スナップショットの適用が行われるサブスクリプションの初期化とは同期しません。</span><span class="sxs-lookup"><span data-stu-id="0165f-134">This refers to starting the Merge Agent; this is not synonymous with initializing a subscription, which involves applying a snapshot.</span></span>  
  
-   <span data-ttu-id="0165f-135">**[スキーマの変更と一括挿入]** 。</span><span class="sxs-lookup"><span data-stu-id="0165f-135">**Schema changes and bulk inserts**.</span></span>  
  
-   <span data-ttu-id="0165f-136">**[パブリッシャーへの変更のアップロード]** 。</span><span class="sxs-lookup"><span data-stu-id="0165f-136">**Upload changes to Publisher**.</span></span>  
  
-   <span data-ttu-id="0165f-137">**[サブスクライバーへの変更のダウンロード]** 。</span><span class="sxs-lookup"><span data-stu-id="0165f-137">**Download changes to Subscriber**.</span></span>  
  
 <span data-ttu-id="0165f-138">これらのフェーズを含めることにより、選択されたセッションで各フェーズにかかった時間と合計時間に対する割合をグリッドに表示できます。</span><span class="sxs-lookup"><span data-stu-id="0165f-138">The phases are included so that the grid can display the amount of time and percentage of total time that each phase accounts for in the selected session.</span></span>  
  
 <span data-ttu-id="0165f-139">**[% (合計に対する割合)]**</span><span class="sxs-lookup"><span data-stu-id="0165f-139">**% of total**</span></span>  
 <span data-ttu-id="0165f-140">選択されたセッションで各フェーズにかかった時間の合計処理時間に対する割合です。</span><span class="sxs-lookup"><span data-stu-id="0165f-140">The percentage of total processing time that each phase accounts for in the selected session.</span></span>  
  
 <span data-ttu-id="0165f-141">**Duration**</span><span class="sxs-lookup"><span data-stu-id="0165f-141">**Duration**</span></span>  
 <span data-ttu-id="0165f-142">各処理フェーズにかかった時間の長さです。</span><span class="sxs-lookup"><span data-stu-id="0165f-142">The amount of time spent in each processing phase.</span></span> <span data-ttu-id="0165f-143">この時間は、セッションに対してマージ エージェントが現在実行中の場合は経過時間、マージ エージェントが以前に実行されている場合は合計時間を表します。</span><span class="sxs-lookup"><span data-stu-id="0165f-143">The time represents elapsed time if the Merge Agent is currently running for the session and total time if the Merge Agent has run previously.</span></span>  
  
 <span data-ttu-id="0165f-144">**Inserts**</span><span class="sxs-lookup"><span data-stu-id="0165f-144">**Inserts**</span></span>  
 <span data-ttu-id="0165f-145">選択されたセッションの該当フェーズで挿入された行数です。</span><span class="sxs-lookup"><span data-stu-id="0165f-145">The number of rows inserted in this phase of the selected session.</span></span>  
  
 <span data-ttu-id="0165f-146">**更新プログラム**</span><span class="sxs-lookup"><span data-stu-id="0165f-146">**Updates**</span></span>  
 <span data-ttu-id="0165f-147">選択されたセッションの該当フェーズで更新された行数です。</span><span class="sxs-lookup"><span data-stu-id="0165f-147">The number of rows updated in this phase of the selected session.</span></span>  
  
 <span data-ttu-id="0165f-148">**Deletes**</span><span class="sxs-lookup"><span data-stu-id="0165f-148">**Deletes**</span></span>  
 <span data-ttu-id="0165f-149">選択されたセッションの該当フェーズで削除された行数です。</span><span class="sxs-lookup"><span data-stu-id="0165f-149">The number of rows deleted in this phase of the selected session.</span></span>  
  
 <span data-ttu-id="0165f-150">**競合**</span><span class="sxs-lookup"><span data-stu-id="0165f-150">**Conflicts**</span></span>  
 <span data-ttu-id="0165f-151">選択されたセッション内の競合の数です。</span><span class="sxs-lookup"><span data-stu-id="0165f-151">The number of conflicts in the selected session.</span></span>  
  
 <span data-ttu-id="0165f-152">**[スキーマの変更]**</span><span class="sxs-lookup"><span data-stu-id="0165f-152">**Schema Changes**</span></span>  
 <span data-ttu-id="0165f-153">選択されたセッション内のスキーマの変更の数です。</span><span class="sxs-lookup"><span data-stu-id="0165f-153">The number of schema changes in the selected session.</span></span> <span data-ttu-id="0165f-154">パブリケーション データベースからレプリケートされるスキーマの変更、アーティクルの追加または削除、およびアーティクル プロパティまたはパブリケーション プロパティへの変更の結果として、スキーマの変更が発生します。</span><span class="sxs-lookup"><span data-stu-id="0165f-154">Schema changes can result from: schema changes being replicated from the publication database; adding or dropping articles; and changes to article or publication properties.</span></span>  
  
 <span data-ttu-id="0165f-155">**[選択されたセッションの最終メッセージ]**</span><span class="sxs-lookup"><span data-stu-id="0165f-155">**Last message of the selected session**</span></span>  
 <span data-ttu-id="0165f-156">このテキスト領域は、選択されたセッションの最終メッセージを表示します。</span><span class="sxs-lookup"><span data-stu-id="0165f-156">This text area displays the last message in the selected session.</span></span> <span data-ttu-id="0165f-157">エラーが発生している場合は、詳細なエラー情報と、エラー発生時に実行しようとしていたコマンドが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0165f-157">If an error has occurred, it displays detailed error information and the command that was attempted at the time of the error.</span></span> <span data-ttu-id="0165f-158">エラーに関連する追加コンテンツへのリンクも含まれます。</span><span class="sxs-lookup"><span data-stu-id="0165f-158">It also includes links to additional content related to the error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0165f-159">参照</span><span class="sxs-lookup"><span data-stu-id="0165f-159">See Also</span></span>  
 <span data-ttu-id="0165f-160">[レプリケーション モニターの開始](monitor/start-the-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="0165f-160">[Start the Replication Monitor](monitor/start-the-replication-monitor.md) </span></span>  
 <span data-ttu-id="0165f-161">[レプリケーション モニターを使用して情報を表示し、タスクを実行する](monitor/view-information-and-perform-tasks-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="0165f-161">[View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md) </span></span>  
 <span data-ttu-id="0165f-162">[レプリケーションの監視](monitoring-replication.md) </span><span class="sxs-lookup"><span data-stu-id="0165f-162">[Monitoring Replication](monitoring-replication.md) </span></span>  
 [<span data-ttu-id="0165f-163">レプリケーション エージェントの概要</span><span class="sxs-lookup"><span data-stu-id="0165f-163">Replication Agents Overview</span></span>](agents/replication-agents-overview.md)  
  
  
