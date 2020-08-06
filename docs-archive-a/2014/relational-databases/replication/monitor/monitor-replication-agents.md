---
title: レプリケーション エージェントの監視 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- monitoring performance [SQL Server replication], agents
- Log Reader Agent, monitoring
- Replication Monitor, agents
- Merge Agent, monitoring
- Queue Reader Agent, monitoring
- Snapshot Agent, monitoring
- agents [SQL Server replication], monitoring
- Distribution Agent, monitoring
ms.assetid: d06ed24f-82d7-4b9e-9e40-cc9780476a71
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: baa22ef9e9f7c4621f76838e82c309d17f1e12a6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634395"
---
# <a name="monitor-replication-agents"></a><span data-ttu-id="2835b-102">レプリケーション エージェントの監視</span><span class="sxs-lookup"><span data-stu-id="2835b-102">Monitor Replication Agents</span></span>
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] <span data-ttu-id="2835b-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] レプリケーション モニターを使用すると、レプリケーションの利用状況を体系的に表示でき、特定のエージェントに関する情報を簡単に見つけることもできます。</span><span class="sxs-lookup"><span data-stu-id="2835b-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Replication Monitor provides a systemic view of replication activity, but also makes it straightforward to find information on a specific agent.</span></span> <span data-ttu-id="2835b-104">次の一覧に、各エージェント、各エージェントを利用できるレプリケーション モニターのタブ、およびそれらのタブへのアクセス方法について説明しているトピックへのリンクを示します。</span><span class="sxs-lookup"><span data-stu-id="2835b-104">The following list includes each agent, the tabs in the Replication Monitor on which it can be found, and a link to a topic that explains how to access these tabs:</span></span>  
  
-   <span data-ttu-id="2835b-105">以下のエージェントは、レプリケーション モニターでパブリケーションと関連付けられています。</span><span class="sxs-lookup"><span data-stu-id="2835b-105">The following agents are associated with publications in Replication Monitor:</span></span>  
  
    -   <span data-ttu-id="2835b-106">スナップショット エージェント</span><span class="sxs-lookup"><span data-stu-id="2835b-106">Snapshot Agent</span></span>  
  
    -   <span data-ttu-id="2835b-107">ログ リーダー エージェント (Log Reader Agent)</span><span class="sxs-lookup"><span data-stu-id="2835b-107">Log Reader Agent</span></span>  
  
    -   <span data-ttu-id="2835b-108">キュー リーダー エージェント (Queue Reader Agent)</span><span class="sxs-lookup"><span data-stu-id="2835b-108">Queue Reader Agent</span></span>  
  
     <span data-ttu-id="2835b-109">これらのエージェントに関連付けられている情報およびタスクにアクセスするには、次のタブを使用します。 **[エージェント]** (各パブリッシャーとパブリケーションで使用可能) と **[警告]** (各パブリケーションで使用可能)。</span><span class="sxs-lookup"><span data-stu-id="2835b-109">Access information and tasks associated with these agents through the following tabs: **Agents** (available for each Publisher and publication) and **Warnings** (available for each publication).</span></span> <span data-ttu-id="2835b-110">詳細については、「[レプリケーション モニターを使用して情報を表示し、タスクを実行する](view-information-and-perform-tasks-replication-monitor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2835b-110">For more information, see [View Information and Perform Tasks using Replication Monitor](view-information-and-perform-tasks-replication-monitor.md).</span></span>  
  
-   <span data-ttu-id="2835b-111">以下のエージェントは、レプリケーション モニターでサブスクリプションと関連付けられています。</span><span class="sxs-lookup"><span data-stu-id="2835b-111">The following agents are associated with subscriptions in Replication Monitor:</span></span>  
  
    -   <span data-ttu-id="2835b-112">ディストリビューション エージェント</span><span class="sxs-lookup"><span data-stu-id="2835b-112">Distribution Agent</span></span>  
  
    -   <span data-ttu-id="2835b-113">[マージ エージェント]</span><span class="sxs-lookup"><span data-stu-id="2835b-113">Merge Agent</span></span>  
  
     <span data-ttu-id="2835b-114">これらのエージェントに関連付けられている情報およびタスクにアクセスするには、次のタブを使用します。 **[サブスクリプション ウォッチ リスト]** (各パブリッシャーで使用可能)、または **[すべてのサブスクリプション]** タブ (各パブリケーションで使用可能)。</span><span class="sxs-lookup"><span data-stu-id="2835b-114">Access information and tasks associated with these agents through the following tabs: **Subscription Watch List** (available for each Publisher) or the **All Subscriptions** tab (available for each publication).</span></span> <span data-ttu-id="2835b-115">詳細については、「[レプリケーション モニターを使用して情報を表示し、タスクを実行する](view-information-and-perform-tasks-replication-monitor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2835b-115">For more information, see [View Information and Perform Tasks using Replication Monitor](view-information-and-perform-tasks-replication-monitor.md).</span></span>  
  
## <a name="using-sql-server-management-studio-to-monitor-replication-agents"></a><span data-ttu-id="2835b-116">SQL Server Management Studio を使用してレプリケーション エージェントを監視する</span><span class="sxs-lookup"><span data-stu-id="2835b-116">Using SQL Server Management Studio to Monitor Replication Agents</span></span>  
 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] <span data-ttu-id="2835b-117">[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] には、レプリケーション エージェントの監視用に以下のダイアログ ボックスが用意されています。</span><span class="sxs-lookup"><span data-stu-id="2835b-117">[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] provides the following dialog boxes for monitoring replication agents:</span></span>  
  
-   <span data-ttu-id="2835b-118">**[スナップショット エージェントの状態の表示]** ダイアログ ボックス (すべてのパブリケーション用)</span><span class="sxs-lookup"><span data-stu-id="2835b-118">**View Snapshot Agent Status** (for all publications)</span></span>  
  
-   <span data-ttu-id="2835b-119">**[ログ リーダー エージェントの状態の表示]** ダイアログ ボックス (すべてのトランザクション パブリケーション用)</span><span class="sxs-lookup"><span data-stu-id="2835b-119">**View Log Reader Agent Status** (for all transactional publications)</span></span>  
  
-   <span data-ttu-id="2835b-120">**[同期の状態の表示]** ダイアログ ボックス (すべてのサブスクリプション用。このダイアログ ボックスからディストリビューション エージェントおよびマージ エージェントにアクセスできます)</span><span class="sxs-lookup"><span data-stu-id="2835b-120">**View Synchronization Status** (for all subscriptions; this dialog box allows access to the Distribution Agent and the Merge Agent)</span></span>  
  
 <span data-ttu-id="2835b-121">レプリケーション モニターでは、各エージェントに関する追加情報が表示され、キュー リーダー エージェントが使用されている場合はその監視機能も提供されます。</span><span class="sxs-lookup"><span data-stu-id="2835b-121">Replication Monitor provides additional information about each agent and provides monitoring for the Queue Reader Agent, if it is used.</span></span> <span data-ttu-id="2835b-122">詳細については、「[レプリケーション モニターを使用して情報を表示し、タスクを実行する](view-information-and-perform-tasks-replication-monitor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2835b-122">For more information, see [View Information and Perform Tasks using Replication Monitor](view-information-and-perform-tasks-replication-monitor.md).</span></span>  
  
#### <a name="to-monitor-the-snapshot-agent-and-log-reader-agent"></a><span data-ttu-id="2835b-123">スナップショット エージェントおよびログ リーダー エージェントを監視するには</span><span class="sxs-lookup"><span data-stu-id="2835b-123">To monitor the Snapshot Agent and Log Reader Agent</span></span>  
  
1.  <span data-ttu-id="2835b-124">[!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]でパブリッシャーに接続し、サーバー ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="2835b-124">Connect to the Publisher in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="2835b-125">**[レプリケーション]** フォルダーを展開し、 **[ローカル パブリケーション]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="2835b-125">Expand the **Replication** folder, and then expand the **Local Publications** folder.</span></span>  
  
3.  <span data-ttu-id="2835b-126">パブリケーションを右クリックし、 **[ログ リーダー エージェントの状態の表示]** または **[スナップショット エージェントの状態の表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2835b-126">Right-click a publication, and then click **View Log Reader Agent Status** or **View Snapshot Agent Status**.</span></span>  
  
4.  <span data-ttu-id="2835b-127">**[ログ リーダー エージェントの状態の表示]** または **[スナップショット エージェントの状態の表示]** ダイアログ ボックスで、以下の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="2835b-127">In the **View Log Reader Agent Status** or **View Snapshot Agent Status** dialog box:</span></span>  
  
    -   <span data-ttu-id="2835b-128">エージェントの状態を表示します。</span><span class="sxs-lookup"><span data-stu-id="2835b-128">View agent status.</span></span>  
  
    -   <span data-ttu-id="2835b-129">必要に応じてエージェントを開始または停止します。</span><span class="sxs-lookup"><span data-stu-id="2835b-129">Start or stop the agent if necessary.</span></span>  
  
    -   <span data-ttu-id="2835b-130">**[監視]** をクリックして **レプリケーション モニター**を起動します。</span><span class="sxs-lookup"><span data-stu-id="2835b-130">Click **Monitor** to launch **Replication Monitor**.</span></span>  
  
5.  <span data-ttu-id="2835b-131">**[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2835b-131">Click **Close**.</span></span>  
  
#### <a name="to-monitor-the-distribution-agent-and-merge-agent-from-the-publisher"></a><span data-ttu-id="2835b-132">ディストリビューション エージェントおよびマージ エージェントを監視するには (パブリッシャー側から)</span><span class="sxs-lookup"><span data-stu-id="2835b-132">To monitor the Distribution Agent and Merge Agent (from the Publisher)</span></span>  
  
1.  <span data-ttu-id="2835b-133">[!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]でパブリッシャーに接続し、サーバー ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="2835b-133">Connect to the Publisher in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="2835b-134">**[レプリケーション]** フォルダーを展開し、 **[ローカル パブリケーション]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="2835b-134">Expand the **Replication** folder, and then expand the **Local Publications** folder.</span></span>  
  
3.  <span data-ttu-id="2835b-135">監視するサブスクリプションのパブリケーションを展開します。</span><span class="sxs-lookup"><span data-stu-id="2835b-135">Expand the publication for the subscription you want to monitor.</span></span>  
  
4.  <span data-ttu-id="2835b-136">サブスクリプションを右クリックし、 **[同期の状態の表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2835b-136">Right-click the subscription, and then click **View Synchronization Status**.</span></span>  
  
5.  <span data-ttu-id="2835b-137">**[同期の状態の表示]** ダイアログ ボックスで、以下の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="2835b-137">In the **View Synchronization Status** dialog box:</span></span>  
  
    -   <span data-ttu-id="2835b-138">エージェントの状態を表示します。</span><span class="sxs-lookup"><span data-stu-id="2835b-138">View agent status.</span></span>  
  
    -   <span data-ttu-id="2835b-139">必要に応じてエージェントを開始または停止します。</span><span class="sxs-lookup"><span data-stu-id="2835b-139">Start or stop the agent if necessary.</span></span>  
  
    -   <span data-ttu-id="2835b-140">プッシュ サブスクリプションの場合、 **[監視]** をクリックして **レプリケーション モニター**を起動します。</span><span class="sxs-lookup"><span data-stu-id="2835b-140">For push subscriptions, click **Monitor** to launch **Replication Monitor**.</span></span>  
  
    -   <span data-ttu-id="2835b-141">プル サブスクリプションの場合、 **[ジョブ履歴の表示]** をクリックして **ログ ファイル ビューアー**を起動します。エージェント ログからの出力が表示されます。</span><span class="sxs-lookup"><span data-stu-id="2835b-141">For pull subscriptions, click **View Job History** to launch the **Log File Viewer**, which displays output from the agent log.</span></span>  
  
6.  <span data-ttu-id="2835b-142">**[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2835b-142">Click **Close**.</span></span>  
  
#### <a name="to-monitor-the-distribution-agent-and-merge-agent-from-the-subscriber"></a><span data-ttu-id="2835b-143">ディストリビューション エージェントおよびマージ エージェントを監視するには (サブスクライバー側から)</span><span class="sxs-lookup"><span data-stu-id="2835b-143">To monitor the Distribution Agent and Merge Agent (from the Subscriber)</span></span>  
  
1.  <span data-ttu-id="2835b-144">[!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]でサブスクライバーに接続して、サーバー ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="2835b-144">Connect to the Subscriber in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="2835b-145">**[レプリケーション]** フォルダーを展開し、 **[ローカル サブスクリプション]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="2835b-145">Expand the **Replication** folder, and then expand the **Local Subscriptions** folder.</span></span>  
  
3.  <span data-ttu-id="2835b-146">監視するサブスクリプションを右クリックして **[同期の状態の表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2835b-146">Right-click the subscription you want to monitor, and then click **View Synchronization Status**.</span></span>  
  
4.  <span data-ttu-id="2835b-147">**[同期の状態の表示]** ダイアログ ボックスで、以下の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="2835b-147">In the **View Synchronization Status** dialog box:</span></span>  
  
    -   <span data-ttu-id="2835b-148">エージェントの状態を表示します。</span><span class="sxs-lookup"><span data-stu-id="2835b-148">View agent status.</span></span>  
  
    -   <span data-ttu-id="2835b-149">必要に応じてエージェントを開始または停止します。</span><span class="sxs-lookup"><span data-stu-id="2835b-149">Start or stop the agent if necessary.</span></span>  
  
    -   <span data-ttu-id="2835b-150">**[ジョブ履歴の表示]** をクリックして **ログ ファイル ビューアー**を起動します。エージェント ログからの出力が表示されます。</span><span class="sxs-lookup"><span data-stu-id="2835b-150">Click **View Job History** to launch the **Log File Viewer**, which displays output from the agent log.</span></span>  
  
5.  <span data-ttu-id="2835b-151">**[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2835b-151">Click **Close**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2835b-152">参照</span><span class="sxs-lookup"><span data-stu-id="2835b-152">See Also</span></span>  
 <span data-ttu-id="2835b-153">[レプリケーションの監視](../monitoring-replication.md) </span><span class="sxs-lookup"><span data-stu-id="2835b-153">[Monitoring Replication](../monitoring-replication.md) </span></span>  
 [<span data-ttu-id="2835b-154">レプリケーション エージェントの概要</span><span class="sxs-lookup"><span data-stu-id="2835b-154">Replication Agents Overview</span></span>](../agents/replication-agents-overview.md)  
  
  
