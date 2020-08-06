---
title: レプリケーションエージェントコマンドプロンプトパラメーターの表示および変更 (SQL Server Management Studio) |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- agents [SQL Server replication], command prompt parameters
ms.assetid: 45f2e781-c21d-4b44-8992-89f60fb3d022
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 752f674c21bb66c7b64e399e30e4917512431195
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632405"
---
# <a name="view-and-modify-replication-agent-command-prompt-parameters-sql-server-management-studio"></a><span data-ttu-id="a5293-102">レプリケーション エージェント コマンド プロンプト パラメーターを表示および変更する (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="a5293-102">View and Modify Replication Agent Command Prompt Parameters (SQL Server Management Studio)</span></span>
  <span data-ttu-id="a5293-103">レプリケーション エージェントは、コマンド ライン パラメーターを使用できる実行可能ファイルです。</span><span class="sxs-lookup"><span data-stu-id="a5293-103">Replication agents are executables that accept command line parameters.</span></span> <span data-ttu-id="a5293-104">既定では、エージェントは [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] エージェント ジョブ ステップで実行されるため、これらのパラメーターは、 **[ジョブのプロパティ - \<Job>]** ダイアログ ボックスを使用して表示および変更できます。</span><span class="sxs-lookup"><span data-stu-id="a5293-104">By default, agents run under [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent job steps, so these parameters can be viewed and modified using the **Job Properties - \<Job>** dialog box.</span></span> <span data-ttu-id="a5293-105">このダイアログ ボックスは、 **の** [ジョブ] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] フォルダーおよびレプリケーション モニター内の **[エージェント]** タブからアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="a5293-105">This dialog box is available from the **Jobs** folder in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] and from the **Agents** tab in Replication Monitor.</span></span> <span data-ttu-id="a5293-106">レプリケーション モニターの起動の詳細については、「[Start the Replication Monitor](../monitor/start-the-replication-monitor.md)」 (レプリケーション モニターの開始) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a5293-106">For information about starting Replication Monitor, see [Start the Replication Monitor](../monitor/start-the-replication-monitor.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a5293-107">エージェント パラメーターの変更は、エージェントの次回起動時に反映されます。</span><span class="sxs-lookup"><span data-stu-id="a5293-107">Agent parameter changes take effect the next time the agent is started.</span></span> <span data-ttu-id="a5293-108">エージェントを継続して実行している場合は、そのエージェントを停止して再起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a5293-108">If the agent runs continuously, you must stop and restart the agent.</span></span>  
  
 <span data-ttu-id="a5293-109">パラメーターは直接変更することもできますが、エージェント プロファイルを使用して変更する方が一般的です。</span><span class="sxs-lookup"><span data-stu-id="a5293-109">Although parameters can be modified directly, it is more common to modify them through an agent profile.</span></span> <span data-ttu-id="a5293-110">詳しくは、「 [レプリケーション エージェント プロファイル](replication-agent-profiles.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a5293-110">For more information, see [Replication Agent Profiles](replication-agent-profiles.md).</span></span>  
  
 <span data-ttu-id="a5293-111">**[ジョブ]** フォルダーからエージェント ジョブにアクセスする場合は、次の表を使用して、各エージェントで使用できるエージェント ジョブ名とパラメーターを決定してください。</span><span class="sxs-lookup"><span data-stu-id="a5293-111">If you access agent jobs from the **Jobs** folder, use the following table to determine the agent job name and the parameters available for each agent.</span></span>  
  
|<span data-ttu-id="a5293-112">エージェント</span><span class="sxs-lookup"><span data-stu-id="a5293-112">Agent</span></span>|<span data-ttu-id="a5293-113">ジョブ名</span><span class="sxs-lookup"><span data-stu-id="a5293-113">Job name</span></span>|<span data-ttu-id="a5293-114">パラメーターの一覧の参照先</span><span class="sxs-lookup"><span data-stu-id="a5293-114">For a list of parameters, see...</span></span>|  
|-----------|--------------|------------------------------------|  
|<span data-ttu-id="a5293-115">スナップショット エージェント</span><span class="sxs-lookup"><span data-stu-id="a5293-115">Snapshot Agent</span></span>|**\<Publisher>-\<PublicationDatabase>-\<Publication>-\<integer>**|[<span data-ttu-id="a5293-116">Replication Snapshot Agent</span><span class="sxs-lookup"><span data-stu-id="a5293-116">Replication Snapshot Agent</span></span>](replication-snapshot-agent.md)|  
|<span data-ttu-id="a5293-117">マージ パブリケーション パーティションに対するスナップショット エージェント</span><span class="sxs-lookup"><span data-stu-id="a5293-117">Snapshot Agent for a merge publication partition</span></span>|<span data-ttu-id="a5293-118">**Dyn_\<Publisher>-\<PublicationDatabase>-\<Publication>-\<GUID>**</span><span class="sxs-lookup"><span data-stu-id="a5293-118">**Dyn_\<Publisher>-\<PublicationDatabase>-\<Publication>-\<GUID>**</span></span>|[<span data-ttu-id="a5293-119">Replication Snapshot Agent</span><span class="sxs-lookup"><span data-stu-id="a5293-119">Replication Snapshot Agent</span></span>](replication-snapshot-agent.md)|  
|<span data-ttu-id="a5293-120">ログ リーダー エージェント (Log Reader Agent)</span><span class="sxs-lookup"><span data-stu-id="a5293-120">Log Reader Agent</span></span>|**\<Publisher>-\<PublicationDatabase>-\<integer>**|[<span data-ttu-id="a5293-121">レプリケーション ログ リーダー エージェント</span><span class="sxs-lookup"><span data-stu-id="a5293-121">Replication Log Reader Agent</span></span>](replication-log-reader-agent.md)|  
|<span data-ttu-id="a5293-122">プル サブスクリプションに対するマージ エージェント</span><span class="sxs-lookup"><span data-stu-id="a5293-122">Merge Agent for pull subscriptions</span></span>|**\<Publisher>-\<PublicationDatabase>-\<Publication>-\<Subscriber>-\<SubscriptionDatabase>-\<integer>**|[<span data-ttu-id="a5293-123">Replication Merge Agent</span><span class="sxs-lookup"><span data-stu-id="a5293-123">Replication Merge Agent</span></span>](replication-merge-agent.md)|  
|<span data-ttu-id="a5293-124">プッシュ サブスクリプションに対するマージ エージェント</span><span class="sxs-lookup"><span data-stu-id="a5293-124">Merge Agent for push subscriptions</span></span>|**\<Publisher>-\<PublicationDatabase>-\<Publication>-\<Subscriber>-\<integer>**|[<span data-ttu-id="a5293-125">Replication Merge Agent</span><span class="sxs-lookup"><span data-stu-id="a5293-125">Replication Merge Agent</span></span>](replication-merge-agent.md)|  
|<span data-ttu-id="a5293-126">プッシュ サブスクリプションに対するディストリビューション エージェント</span><span class="sxs-lookup"><span data-stu-id="a5293-126">Distribution Agent for push subscriptions</span></span>|<span data-ttu-id="a5293-127">**\<Publisher>-\<PublicationDatabase>-\<Publication>-\<Subscriber>-\<integer>** <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="a5293-127">**\<Publisher>-\<PublicationDatabase>-\<Publication>-\<Subscriber>-\<integer>** <sup>1</sup></span></span>|[<span data-ttu-id="a5293-128">Replication Distribution Agent</span><span class="sxs-lookup"><span data-stu-id="a5293-128">Replication Distribution Agent</span></span>](replication-distribution-agent.md)|  
|<span data-ttu-id="a5293-129">プル サブスクリプションに対するディストリビューション エージェント</span><span class="sxs-lookup"><span data-stu-id="a5293-129">Distribution Agent for pull subscriptions</span></span>|<span data-ttu-id="a5293-130">**\<Publisher>-\<PublicationDatabase>-\<Publication>-\<Subscriber>-\<SubscriptionDatabase>-\<GUID>** <sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="a5293-130">**\<Publisher>-\<PublicationDatabase>-\<Publication>-\<Subscriber>-\<SubscriptionDatabase>-\<GUID>** <sup>2</sup></span></span>|[<span data-ttu-id="a5293-131">Replication Distribution Agent</span><span class="sxs-lookup"><span data-stu-id="a5293-131">Replication Distribution Agent</span></span>](replication-distribution-agent.md)|  
|<span data-ttu-id="a5293-132">SQL Server 以外のサブスクライバーへのプッシュ サブスクリプションに対するディストリビューション エージェント</span><span class="sxs-lookup"><span data-stu-id="a5293-132">Distribution Agent for push subscriptions to non-SQL Server Subscribers</span></span>|**\<Publisher>-\<PublicationDatabase>-\<Publication>-\<Subscriber>-\<integer>**|[<span data-ttu-id="a5293-133">Replication Distribution Agent</span><span class="sxs-lookup"><span data-stu-id="a5293-133">Replication Distribution Agent</span></span>](replication-distribution-agent.md)|  
|<span data-ttu-id="a5293-134">キュー リーダー エージェント (Queue Reader Agent)</span><span class="sxs-lookup"><span data-stu-id="a5293-134">Queue Reader Agent</span></span>|<span data-ttu-id="a5293-135">**[\<Distributor>].\<integer>**</span><span class="sxs-lookup"><span data-stu-id="a5293-135">**[\<Distributor>].\<integer>**</span></span>|[<span data-ttu-id="a5293-136">レプリケーション キュー リーダー エージェント</span><span class="sxs-lookup"><span data-stu-id="a5293-136">Replication Queue Reader Agent</span></span>](replication-queue-reader-agent.md)|  
  
 <span data-ttu-id="a5293-137"><sup>1</sup> Oracle パブリケーションに対するプッシュ サブスクリプションの場合は、 **\<Publisher>-\<PublicationDatabase>** ではなく \*\*\<Publisher>-\<Publisher**> になります</span><span class="sxs-lookup"><span data-stu-id="a5293-137"><sup>1</sup> For push subscriptions to Oracle publications, it is \*\*\<Publisher>-\<Publisher**> rather than **\<Publisher>-\<PublicationDatabase>**</span></span>  
  
 <span data-ttu-id="a5293-138"><sup>2</sup> Oracle パブリケーションに対するプル サブスクリプションの場合は、 **\<Publisher>-\<PublicationDatabase>** ではなく \*\*\<Publisher>-\<DistributionDatabase**> になります</span><span class="sxs-lookup"><span data-stu-id="a5293-138"><sup>2</sup> For pull subscriptions to Oracle publications, it is \*\*\<Publisher>-\<DistributionDatabase**> rather than **\<Publisher>-\<PublicationDatabase>**</span></span>  
  
### <a name="to-view-and-modify-replication-agent-command-line-parameters-from-management-studio"></a><span data-ttu-id="a5293-139">Management Studio からレプリケーション エージェント コマンド ライン パラメーターを表示または変更するには</span><span class="sxs-lookup"><span data-stu-id="a5293-139">To view and modify replication agent command line parameters from Management Studio</span></span>  
  
1.  <span data-ttu-id="a5293-140">[!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]で適切なコンピューターに接続して、サーバー ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="a5293-140">Connect to the appropriate computer in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)], and then expand the server node:</span></span>  
  
    -   <span data-ttu-id="a5293-141">プル サブスクリプションに対するディストリビューション エージェントとマージ エージェントの場合は、サブスクライバーに接続します。</span><span class="sxs-lookup"><span data-stu-id="a5293-141">For the Distribution Agent and Merge Agent for pull subscriptions, connect to the Subscriber.</span></span>  
  
    -   <span data-ttu-id="a5293-142">その他のエージェントの場合は、ディストリビューターに接続します。</span><span class="sxs-lookup"><span data-stu-id="a5293-142">For all other agents, connect to the Distributor.</span></span>  
  
2.  <span data-ttu-id="a5293-143">**[SQL Server エージェント]** フォルダーを展開して、 **[ジョブ]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="a5293-143">Expand the **SQL Server Agent** folder, and then expand the **Jobs** folder.</span></span>  
  
3.  <span data-ttu-id="a5293-144">ジョブを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a5293-144">Right-click a job, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="a5293-145">**[ジョブのプロパティ - \<Job>]** ダイアログ ボックスの **[ステップ]** ページで、ステップ **[エージェントを実行します]** を選択し、 **[編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a5293-145">On the **Steps** page of the **Job Properties - \<Job>** dialog box, select the step **Run agent**, and then click **Edit**.</span></span>  
  
5.  <span data-ttu-id="a5293-146">**[ジョブ ステップのプロパティ - エージェントを実行します]** ダイアログ ボックスで、 **[コマンド]** フィールドを編集します。</span><span class="sxs-lookup"><span data-stu-id="a5293-146">In the **Job Step Properties - Run agent** dialog box, edit the **Command** field.</span></span>  
  
6.  <span data-ttu-id="a5293-147">両方のダイアログ ボックスで **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a5293-147">Click **OK** on both dialog boxes.</span></span>  
  
### <a name="to-view-and-modify-distribution-agent-and-merge-agent-command-line-parameters-from-replication-monitor"></a><span data-ttu-id="a5293-148">レプリケーション モニターからディストリビューション エージェントとマージ エージェントのコマンド ライン パラメーターを表示および変更するには</span><span class="sxs-lookup"><span data-stu-id="a5293-148">To view and modify Distribution Agent and Merge Agent command line parameters from Replication Monitor</span></span>  
  
1.  <span data-ttu-id="a5293-149">レプリケーション モニターの左ペインのパブリッシャー グループを展開し、パブリッシャーを展開して、パブリケーションをクリックします。</span><span class="sxs-lookup"><span data-stu-id="a5293-149">Expand a Publisher group in the left pane of Replication Monitor, expand a Publisher, and then click a publication.</span></span>  
  
2.  <span data-ttu-id="a5293-150">**[すべてのサブスクリプション]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="a5293-150">Click the **All Subscriptions** tab.</span></span>  
  
3.  <span data-ttu-id="a5293-151">サブスクリプションを右クリックし、 **[詳細表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a5293-151">Right-click a subscription, and then click **View Details**.</span></span>  
  
4.  <span data-ttu-id="a5293-152">[**サブスクリプション \< SubscriptionName> \*\* ] ウィンドウで、[**アクション**] をクリックし、[ \*\* \<AgentName> ジョブのプロパティ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a5293-152">In the **Subscription \< SubscriptionName>** window, click **Action**, and then click **\<AgentName> Job Properties**.</span></span>  
  
5.  <span data-ttu-id="a5293-153">**[ジョブのプロパティ - \<Job>]** ダイアログ ボックスの **[ステップ]** ページで、ステップ **[エージェントを実行します]** を選択し、 **[編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a5293-153">On the **Steps** page of the **Job Properties - \<Job>** dialog box, select the step **Run agent**, and then click **Edit**.</span></span>  
  
6.  <span data-ttu-id="a5293-154">**[ジョブ ステップのプロパティ - エージェントを実行します]** ダイアログ ボックスで、 **[コマンド]** フィールドを編集します。</span><span class="sxs-lookup"><span data-stu-id="a5293-154">In the **Job Step Properties - Run agent** dialog box, edit the **Command** field.</span></span>  
  
7.  <span data-ttu-id="a5293-155">両方のダイアログ ボックスで **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a5293-155">Click **OK** on both dialog boxes.</span></span>  
  
### <a name="to-view-and-modify-snapshot-agent-log-reader-agent-and-queue-reader-agent-command-line-parameters-from-replication-monitor"></a><span data-ttu-id="a5293-156">レプリケーション モニターからスナップショット エージェント、ログ リーダー エージェント、およびキュー リーダー エージェントのコマンド ライン パラメーターを表示および変更するには</span><span class="sxs-lookup"><span data-stu-id="a5293-156">To view and modify Snapshot Agent, Log Reader Agent, and Queue Reader Agent command line parameters from Replication Monitor</span></span>  
  
1.  <span data-ttu-id="a5293-157">レプリケーション モニターの左ペインのパブリッシャー グループを展開し、パブリッシャーを展開して、パブリケーションをクリックします。</span><span class="sxs-lookup"><span data-stu-id="a5293-157">Expand a Publisher group in the left pane of Replication Monitor, expand a Publisher, and then click a publication.</span></span>  
  
2.  <span data-ttu-id="a5293-158">**[エージェント]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="a5293-158">Click the **Agents** tab.</span></span>  
  
3.  <span data-ttu-id="a5293-159">グリッド内のエージェントを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a5293-159">Right-click an agent in the grid, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="a5293-160">**[ジョブのプロパティ - \<Job>]** ダイアログ ボックスの **[ステップ]** ページで、ステップ **[エージェントを実行します]** を選択し、 **[編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a5293-160">On the **Steps** page of the **Job Properties - \<Job>** dialog box, select the step **Run agent**, and then click **Edit**.</span></span>  
  
5.  <span data-ttu-id="a5293-161">**[ジョブ ステップのプロパティ - エージェントを実行します]** ダイアログ ボックスで、 **[コマンド]** フィールドを編集します。</span><span class="sxs-lookup"><span data-stu-id="a5293-161">In the **Job Step Properties - Run agent** dialog box, edit the **Command** field.</span></span>  
  
6.  <span data-ttu-id="a5293-162">両方のダイアログ ボックスで **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a5293-162">Click **OK** on both dialog boxes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5293-163">参照</span><span class="sxs-lookup"><span data-stu-id="a5293-163">See Also</span></span>  
 <span data-ttu-id="a5293-164">[レプリケーション エージェントの管理](replication-agent-administration.md) </span><span class="sxs-lookup"><span data-stu-id="a5293-164">[Replication Agent Administration](replication-agent-administration.md) </span></span>  
 <span data-ttu-id="a5293-165">[レプリケーション エージェント実行可能ファイルの概念](../concepts/replication-agent-executables-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="a5293-165">[Replication Agent Executables Concepts](../concepts/replication-agent-executables-concepts.md) </span></span>  
 [<span data-ttu-id="a5293-166">レプリケーション エージェントの概要</span><span class="sxs-lookup"><span data-stu-id="a5293-166">Replication Agents Overview</span></span>](replication-agents-overview.md)  
  
  
