---
title: MSSQL_ENG020554 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG020554 error
ms.assetid: ef1a1b88-b2ab-43e8-99cd-163a973262d6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b48714f19fdec520c7bd20e4d8598d491f6e1908
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87717960"
---
# <a name="mssql_eng020554"></a><span data-ttu-id="a8e16-102">MSSQL_ENG020554</span><span class="sxs-lookup"><span data-stu-id="a8e16-102">MSSQL_ENG020554</span></span>
    
## <a name="message-details"></a><span data-ttu-id="a8e16-103">メッセージの詳細</span><span class="sxs-lookup"><span data-stu-id="a8e16-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a8e16-104">製品名</span><span class="sxs-lookup"><span data-stu-id="a8e16-104">Product Name</span></span>|<span data-ttu-id="a8e16-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="a8e16-105">SQL Server</span></span>|  
|<span data-ttu-id="a8e16-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="a8e16-106">Event ID</span></span>|<span data-ttu-id="a8e16-107">20554</span><span class="sxs-lookup"><span data-stu-id="a8e16-107">20554</span></span>|  
|<span data-ttu-id="a8e16-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="a8e16-108">Event Source</span></span>|<span data-ttu-id="a8e16-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="a8e16-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="a8e16-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="a8e16-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="a8e16-111">シンボル名</span><span class="sxs-lookup"><span data-stu-id="a8e16-111">Symbolic Name</span></span>||  
|<span data-ttu-id="a8e16-112">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="a8e16-112">Message Text</span></span>|<span data-ttu-id="a8e16-113">レプリケーション エージェントでは、進捗状況メッセージが %ld 分間ログに記録されていません。</span><span class="sxs-lookup"><span data-stu-id="a8e16-113">The replication agent has not logged a progress message in %ld minutes.</span></span> <span data-ttu-id="a8e16-114">この現象は、エージェントの応答が止まったか、システムの使用率が高いことを示している場合があります。</span><span class="sxs-lookup"><span data-stu-id="a8e16-114">This might indicate an unresponsive agent or high system activity.</span></span> <span data-ttu-id="a8e16-115">レコードがレプリケーション先にレプリケートされていること、およびサブスクライバー、パブリッシャー、ディストリビューターへの接続がアクティブなままであることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="a8e16-115">Verify that records are being replicated to the destination and that connections to the Subscriber, Publisher, and Distributor are still active.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="a8e16-116">説明</span><span class="sxs-lookup"><span data-stu-id="a8e16-116">Explanation</span></span>  
 <span data-ttu-id="a8e16-117">**レプリケーション エージェントの検査** ジョブは、指定された間隔 (既定では 10 分) で実行され、各レプリケーション エージェントの状態を確認します。</span><span class="sxs-lookup"><span data-stu-id="a8e16-117">The **Replication agents checkup** job runs at a specified interval (10 minutes by default) to check on the status of each replication agent.</span></span> <span data-ttu-id="a8e16-118">エージェントが、最後の検査ジョブを実行してからまったく進捗状況メッセージを記録していない場合は、MSSQL_ENG020554 エラーが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a8e16-118">If an agent has not logged any progress messages since the last time the agent checkup job ran, error MSSQL_ENG020554 can be raised.</span></span> <span data-ttu-id="a8e16-119">他のレプリケーション処理が実行されていない場合でも、エージェントは少なくとも履歴メッセージだけは記録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a8e16-119">The agent is expected at least to log history messages even if no other replication activity is occurring.</span></span> <span data-ttu-id="a8e16-120">レプリケーション エージェントは、予想どおり応答していない場合でも、停止したり障害が発生するとは限りません (エージェントで障害が発生すると、エラー MSSQL_ENG020536 が発生します)。</span><span class="sxs-lookup"><span data-stu-id="a8e16-120">Although the replication agent is not responding as expected, it has not necessarily stopped or failed (if an agent has failed, error MSSQL_ENG020536 should be raised).</span></span>  
  
 <span data-ttu-id="a8e16-121">MSSQL_ENG020554 は、次のような問題が原因で発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a8e16-121">The following issues can cause error MSSQL_ENG020554 to be raised:</span></span>  
  
-   <span data-ttu-id="a8e16-122">エージェントがビジーである場合</span><span class="sxs-lookup"><span data-stu-id="a8e16-122">The agent is busy.</span></span>  
  
     <span data-ttu-id="a8e16-123">エージェントの検査ジョブでポーリングが実行されているときにエージェントがビジーで応答できない場合、エージェントの検査ジョブは、レプリケーション エージェントが正しく機能しているかどうかについて報告できません。</span><span class="sxs-lookup"><span data-stu-id="a8e16-123">If the agent is too busy to respond when polled by the agent checkup job, the agent checkup job cannot report whether the replication agent is functioning properly.</span></span> <span data-ttu-id="a8e16-124">レプリケーション エージェントがビジーになるのは、レプリケートされているデータの量が多すぎたり、アプリケーションの設計または構成の問題が原因でプロセスが長時間実行されるなど、さまざまな原因があります。</span><span class="sxs-lookup"><span data-stu-id="a8e16-124">There are a number of reasons why the replication agent could be busy: there might be a lot of data being replicated, or there might be application design or configuration issues that result in processes that run for a long time.</span></span>  
  
-   <span data-ttu-id="a8e16-125">エージェントがトポロジ内のコンピューターのいずれにもログインできない場合</span><span class="sxs-lookup"><span data-stu-id="a8e16-125">The agent cannot log in to one of the computers in the topology.</span></span>  
  
     <span data-ttu-id="a8e16-126">すべてのエージェントには **-LoginTimeOut** パラメーター (既定では 15 秒に設定) が指定されています。このパラメーターによって、エージェントがレプリケーション ノードにログインする (マージ エージェントがパブリッシャーにログインするなど) 時間が決まります。</span><span class="sxs-lookup"><span data-stu-id="a8e16-126">All agents have a parameter **-LoginTimeOut** (set to 15 seconds by default), which governs how long an agent attempts to log in to a replication node, such as a Merge Agent logging in to the Publisher.</span></span> <span data-ttu-id="a8e16-127">**-LoginTimeOut** の値を、レプリケーション エージェントの検査ジョブを実行する間隔よりも高く設定すると、ログインの問題がエラーの根本原因になる場合があります。エージェントで他の具体的なエラーが発生する前にエラー MSSQL_ENG020554 が発生します。</span><span class="sxs-lookup"><span data-stu-id="a8e16-127">If the **-LoginTimeOut** value is set higher than the interval at which the replication agent checkup job runs, a login problem could be the root cause of the error: error MSSQL_ENG020554 is raised before the agent is able to raise a more specific error.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a8e16-128">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="a8e16-128">User Action</span></span>  
 <span data-ttu-id="a8e16-129">必要な操作は、エラーが発生した原因によって異なります。</span><span class="sxs-lookup"><span data-stu-id="a8e16-129">The action required depends on the cause of the error:</span></span>  
  
-   <span data-ttu-id="a8e16-130">このエラーが発生するすべてのケースで、次のアクションを実行します。</span><span class="sxs-lookup"><span data-stu-id="a8e16-130">For all cases in which this error is raised:</span></span>  
  
     <span data-ttu-id="a8e16-131">レプリケーション モニターでエラーの詳細を確認してから、エージェントが停止している場合は再起動します。</span><span class="sxs-lookup"><span data-stu-id="a8e16-131">Check the error details in Replication Monitor, and then restart the agent if it has stopped.</span></span> <span data-ttu-id="a8e16-132">エラーの詳細には、エージェントが正しく実行されなかった原因について追加の情報が示されている場合があります。</span><span class="sxs-lookup"><span data-stu-id="a8e16-132">The error details might provide additional information on why the agent was not running properly.</span></span> <span data-ttu-id="a8e16-133">エージェントが実行中の場合は、エージェントを停止および再起動しないでください。停止および再起動すると、問題がさらに悪化する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a8e16-133">If the agent is running, do not stop and restart the agent, because that can exacerbate the problem.</span></span> <span data-ttu-id="a8e16-134">レプリケーション モニターにおけるエージェントの状態およびエラーの詳細の表示については、以下のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="a8e16-134">For information about viewing agent status and error details in Replication Monitor, see the following topics:</span></span>  
  
    -   <span data-ttu-id="a8e16-135">スナップショットエージェント、ログリーダーエージェント、キューリーダーエージェントについては、「[レプリケーションモニターを使用して情報を表示し、タスクを実行](monitor/view-information-and-perform-tasks-replication-monitor.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a8e16-135">For the Snapshot Agent, Log Reader Agent, and Queue Reader Agent, see [View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md).</span></span>  
  
    -   <span data-ttu-id="a8e16-136">ディストリビューションエージェントとマージエージェントについては、「[レプリケーションモニターを使用して情報を表示し、タスクを実行](monitor/view-information-and-perform-tasks-replication-monitor.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a8e16-136">For the Distribution Agent and Merge Agent, see [View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md).</span></span>  
  
-   <span data-ttu-id="a8e16-137">エージェントがビジーであるためにこのエラーが頻繁に発生する場合は、次の操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="a8e16-137">If this error is raised frequently because the agent is busy:</span></span>  
  
     <span data-ttu-id="a8e16-138">場合によっては、エージェントの処理時間が短くなるように、アプリケーションを再設計する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a8e16-138">You might need to redesign your application so that the agent spends less time processing.</span></span>  
  
     <span data-ttu-id="a8e16-139">**[ジョブのプロパティ]** ダイアログ ボックスを使用してエージェントの状態を確認する間隔を長くすることができます。</span><span class="sxs-lookup"><span data-stu-id="a8e16-139">You can increase the interval at which agent status is checked using the **Job Properties** dialog box.</span></span> <span data-ttu-id="a8e16-140">レプリケーションジョブのこのダイアログボックスへのアクセスの詳細については、「[レプリケーションモニターを使用して情報を表示し、タスクを実行する](monitor/view-information-and-perform-tasks-replication-monitor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a8e16-140">For information about accessing this dialog box for replication jobs, see [View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md).</span></span>  
  
-   <span data-ttu-id="a8e16-141">エージェントがトポロジ内のコンピューターのいずれにもログインできない場合には、次の操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="a8e16-141">If an agent cannot log in to one of the computers in the topology:</span></span>  
  
     <span data-ttu-id="a8e16-142">**-LoginTimeOut** の値を、レプリケーション エージェントの検査ジョブを実行する間隔よりも低い値に設定することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="a8e16-142">We recommend that the **-LoginTimeOut** value be set lower than the interval at which the replication agent checkup job runs.</span></span> <span data-ttu-id="a8e16-143">ネットワークの問題により、 **-LoginTimeOut** が高く設定され、その結果ログインがタイムアウトになる場合があります。 **-LoginTimeOut** の値を低く設定すると、レプリケーションから他の具体的なエラーが報告されるので、ログインの問題の原因 (権限、ネットワーク障害、その他の問題など) を特定してトラブルシューティングできます。</span><span class="sxs-lookup"><span data-stu-id="a8e16-143">In some cases, the value for **-LoginTimeOut** is set higher because of network issues that cause logins to time out. If the **-LoginTimeOut** is set lower, replication can report more specific errors, allowing you to troubleshoot login problems that could be caused by permissions, network problems, or other issues.</span></span> <span data-ttu-id="a8e16-144">エージェント パラメーターは、エージェント プロファイルおよびコマンド ラインで指定できます。</span><span class="sxs-lookup"><span data-stu-id="a8e16-144">Agent parameters can be specified in agent profiles and on the command line.</span></span> <span data-ttu-id="a8e16-145">詳細については、次を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a8e16-145">For more information, see:</span></span>  
  
    -   [<span data-ttu-id="a8e16-146">レプリケーション エージェント プロファイルの操作</span><span class="sxs-lookup"><span data-stu-id="a8e16-146">Work with Replication Agent Profiles</span></span>](agents/replication-agent-profiles.md)  
  
    -   [<span data-ttu-id="a8e16-147">レプリケーション エージェント コマンド プロンプト パラメーターを表示および変更する &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="a8e16-147">View and Modify Replication Agent Command Prompt Parameters &#40;SQL Server Management Studio&#41;</span></span>](agents/view-and-modify-replication-agent-command-prompt-parameters.md)  
  
    -   <span data-ttu-id="a8e16-148">[Replication Agent Executables Concepts](concepts/replication-agent-executables-concepts.md)に割り当てるメモリの最大容量と最小容量を設定する。</span><span class="sxs-lookup"><span data-stu-id="a8e16-148">[Replication Agent Executables Concepts](concepts/replication-agent-executables-concepts.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8e16-149">参照</span><span class="sxs-lookup"><span data-stu-id="a8e16-149">See Also</span></span>  
 <span data-ttu-id="a8e16-150">[レプリケーション エージェントの管理](agents/replication-agent-administration.md) </span><span class="sxs-lookup"><span data-stu-id="a8e16-150">[Replication Agent Administration](agents/replication-agent-administration.md) </span></span>  
 <span data-ttu-id="a8e16-151">[エラーとイベントのリファレンス &#40;レプリケーション&#41;](errors-and-events-reference-replication.md) </span><span class="sxs-lookup"><span data-stu-id="a8e16-151">[Errors and Events Reference &#40;Replication&#41;](errors-and-events-reference-replication.md) </span></span>  
 <span data-ttu-id="a8e16-152">[Replication Distribution Agent](agents/replication-distribution-agent.md) </span><span class="sxs-lookup"><span data-stu-id="a8e16-152">[Replication Distribution Agent](agents/replication-distribution-agent.md) </span></span>  
 <span data-ttu-id="a8e16-153">[Replication Log Reader Agent](agents/replication-log-reader-agent.md) </span><span class="sxs-lookup"><span data-stu-id="a8e16-153">[Replication Log Reader Agent](agents/replication-log-reader-agent.md) </span></span>  
 <span data-ttu-id="a8e16-154">[Replication Merge Agent](agents/replication-merge-agent.md) </span><span class="sxs-lookup"><span data-stu-id="a8e16-154">[Replication Merge Agent](agents/replication-merge-agent.md) </span></span>  
 <span data-ttu-id="a8e16-155">[レプリケーション キュー リーダー エージェント](agents/replication-queue-reader-agent.md) </span><span class="sxs-lookup"><span data-stu-id="a8e16-155">[Replication Queue Reader Agent](agents/replication-queue-reader-agent.md) </span></span>  
 [<span data-ttu-id="a8e16-156">Replication Snapshot Agent</span><span class="sxs-lookup"><span data-stu-id="a8e16-156">Replication Snapshot Agent</span></span>](agents/replication-snapshot-agent.md)  
  
  
