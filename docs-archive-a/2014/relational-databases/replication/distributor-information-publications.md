---
title: SQL Server レプリケーション [ディストリビューター情報] ダイアログボックス |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.Distributor.Publications.f1
- sql12.rep.monitor.Distributor.commonjobs..f1
- sql12.rep.monitor.Distributor.SubscriptionSummary.merge.f1
- sql12.rep.monitor.Distributor.SubscriptionSummary.snapshot.f1
- sql12.rep.monitor.Distributor.SubscriptionSummary.tran.f1
ms.assetid: 1f499277-7f12-42ba-8cf4-52b683434944
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8ca0717a63c9660c225ec238e1e4d2423f7d01ba
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632379"
---
# <a name="distributor-information-dialog-box"></a><span data-ttu-id="4e9b1-102">[ディストリビューター情報] ダイアログボックス</span><span class="sxs-lookup"><span data-stu-id="4e9b1-102">Distributor Information Dialog Box</span></span> 
<span data-ttu-id="4e9b1-103">このトピックでは、[**ディストリビューター** ] ダイアログボックスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="4e9b1-103">This topic provides information on the **Distributor** dialog box</span></span> 

## <a name="publications"></a><span data-ttu-id="4e9b1-104">パブリケーション</span><span class="sxs-lookup"><span data-stu-id="4e9b1-104">Publications</span></span>

  <span data-ttu-id="4e9b1-105">**[パブリケーション]** タブを使用すると、左ペインで選択したディストリビューターにおけるすべてのパブリケーションに関する要約情報を取得できます。</span><span class="sxs-lookup"><span data-stu-id="4e9b1-105">The **Publications** tab provides summary information for all publications at the Distributor that is selected in the left pane.</span></span>  
  
### <a name="options"></a><span data-ttu-id="4e9b1-106">Options</span><span class="sxs-lookup"><span data-stu-id="4e9b1-106">Options</span></span>  
 <span data-ttu-id="4e9b1-107">ディストリビューターによりサポートされるパブリケーションについて表示される情報には、パブリッシャーの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスを含む列などがあります。</span><span class="sxs-lookup"><span data-stu-id="4e9b1-107">The information that is displayed about the publications supported by the Distributor includes a column that contains the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance of the Publisher.</span></span> <span data-ttu-id="4e9b1-108">それ以外は、レプリケーション モニターのパブリッシャー ビューに表示されるものと同じパブリケーション情報です。</span><span class="sxs-lookup"><span data-stu-id="4e9b1-108">Otherwise, the publication information is the same as the publication information that is provided when you view publications in the Publisher view of Replication Monitor.</span></span> <span data-ttu-id="4e9b1-109">**[パブリケーション]** タブ内の列の詳細については、「 [Publisher Information, Publications](publisher-information-publications.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4e9b1-109">For more information about the columns in the **Publications** tab, see [Publisher Information, Publications](publisher-information-publications.md).</span></span>  

## <a name="subscription-watch-list"></a><span data-ttu-id="4e9b1-110">サブスクリプション ウォッチ リスト</span><span class="sxs-lookup"><span data-stu-id="4e9b1-110">Subscription watch list</span></span>

### <a name="transactional-replication"></a><span data-ttu-id="4e9b1-111">トランザクション レプリケーション</span><span class="sxs-lookup"><span data-stu-id="4e9b1-111">Transactional replication</span></span> 
  <span data-ttu-id="4e9b1-112">トランザクション サブスクリプションの情報にはパブリッシャーの名前が含まれます。</span><span class="sxs-lookup"><span data-stu-id="4e9b1-112">Information for transactional subscriptions includes the name of the Publisher.</span></span> <span data-ttu-id="4e9b1-113">それ以外は、このダイアログ ボックスで提供される機能と情報はパブリッシャーのビューと同様です。</span><span class="sxs-lookup"><span data-stu-id="4e9b1-113">Otherwise, the functionality and the information that is provided in this dialog box is the same as in the Publisher view.</span></span> <span data-ttu-id="4e9b1-114">このダイアログ ボックスに関する情報については、「[Publisher Information, Subscription Watch List &#40;Transactional Publication, SQL Server 2005 and Later&#41;](publisher-information-subscription-watch-list-transactional.md)」 (パブリッシャー情報、サブスクリプション ウォッチ リスト スナップショット (トランザクション パブリケーション、SQL Server 2005 以降)) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4e9b1-114">For more information about how to use this dialog box, see [Publisher Information, Subscription Watch List &#40;Transactional Publication, SQL Server 2005 and Later&#41;](publisher-information-subscription-watch-list-transactional.md).</span></span>  

### <a name="merge-replication"></a><span data-ttu-id="4e9b1-115">マージ レプリケーション</span><span class="sxs-lookup"><span data-stu-id="4e9b1-115">Merge replication</span></span>
  <span data-ttu-id="4e9b1-116">マージ パブリケーションのサブスクリプションの情報にはパブリッシャーの名前が含まれます。</span><span class="sxs-lookup"><span data-stu-id="4e9b1-116">Information for merge publication subscriptions includes the name of the Publisher.</span></span> <span data-ttu-id="4e9b1-117">それ以外は、このダイアログ ボックスで提供される機能と情報はパブリッシャーのビューと同様です。</span><span class="sxs-lookup"><span data-stu-id="4e9b1-117">Otherwise, the functionality and the information that is provided in this dialog box is the same as in the Publisher view.</span></span> <span data-ttu-id="4e9b1-118">このダイアログ ボックスに関する情報については、「[Publisher Information, Subscription Watch List &#40;Merge Publication, SQL Server 2005 and Later&#41;](publisher-information-subscription-watch-list-merge-publication.md)」 (パブリッシャー情報、サブスクリプション ウォッチ リスト スナップショット (マージ パブリケーション、SQL Server 2005 以降)) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4e9b1-118">For more information about how to use this dialog box, see [Publisher Information, Subscription Watch List &#40;Merge Publication, SQL Server 2005 and Later&#41;](publisher-information-subscription-watch-list-merge-publication.md).</span></span> 

### <a name="snapshot-replication"></a><span data-ttu-id="4e9b1-119">スナップショット レプリケーション</span><span class="sxs-lookup"><span data-stu-id="4e9b1-119">Snapshot replication</span></span>
  <span data-ttu-id="4e9b1-120">スナップショット パブリケーションのサブスクリプションの情報にはパブリッシャーの名前が含まれます。</span><span class="sxs-lookup"><span data-stu-id="4e9b1-120">Information for snapshot publication subscriptions includes the name of the Publisher.</span></span> <span data-ttu-id="4e9b1-121">それ以外は、このダイアログ ボックスで提供される機能と情報はパブリッシャーのビューと同様です。</span><span class="sxs-lookup"><span data-stu-id="4e9b1-121">Otherwise, the functionality and the information that is provided in this dialog box is the same as in the Publisher view.</span></span> <span data-ttu-id="4e9b1-122">このダイアログ ボックスに関する情報については、「[Publisher Information, Subscription Watch List &#40;Snapshot Publication, SQL Server 2005 and Later&#41;](publisher-information-subscription-watch-list-snapshot.md)」 (パブリッシャー情報、サブスクリプション ウォッチ リスト スナップショット (スナップショット パブリケーション、SQL Server 2005 以降)) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4e9b1-122">For more information about how to use this dialog box, see [Publisher Information, Subscription Watch List &#40;Snapshot Publication, SQL Server 2005 and Later&#41;](publisher-information-subscription-watch-list-snapshot.md).</span></span>  

## <a name="agents"></a><span data-ttu-id="4e9b1-123">エージェント</span><span class="sxs-lookup"><span data-stu-id="4e9b1-123">Agents</span></span>
  <span data-ttu-id="4e9b1-124">**[エージェント]** タブには、パブリッシャーおよびサブスクライバーに関連するエージェントおよびメンテナンス ジョブに関する詳細情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="4e9b1-124">The **Agents** tab displays information about the agents and maintenance jobs that are associated with the Publisher and Subscriber.</span></span>  
  
 <span data-ttu-id="4e9b1-125">ディストリビューター ビューのディストリビューターの **[エージェント]** タブで利用可能なエージェントには、パブリッシャーの **[エージェント]** タブで利用可能なすべてのエージェントが含まれています。</span><span class="sxs-lookup"><span data-stu-id="4e9b1-125">The agents that are available in the **Agents** tab for a Distributor in Distributor view include all the agents that are available in the **Agents** tab for a Publisher.</span></span> <span data-ttu-id="4e9b1-126">ただし、ディストリビューター ビューのディストリビューターの **[エージェント]** タブには、ディストリビューター エージェントおよびマージ エージェントも含まれています。</span><span class="sxs-lookup"><span data-stu-id="4e9b1-126">However, the **Agents** tab for a Distributor in Distributor view also includes a Distributor Agent and a Merge Agent.</span></span>  
  
 <span data-ttu-id="4e9b1-127">スナップショット エージェント、ログ リーダー エージェント、キュー リーダー エージェント、およびメンテナンス ジョブの詳細については、「 [Publisher Information, Agents](publisher-information-agents.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4e9b1-127">For more information about the Snapshot, Log Reader, and Queue Reader agents, and maintenance jobs, see [Publisher Information, Agents](publisher-information-agents.md).</span></span> <span data-ttu-id="4e9b1-128">ディストリビューターの **[エージェント]** タブでエージェント情報を表示する場合は、スナップショット エージェントおよびログ リーダー エージェントのパブリッシャー情報があることに注意してください</span><span class="sxs-lookup"><span data-stu-id="4e9b1-128">Notice that when you are viewing agent information on the **Agents** tab for a Distributor, Publisher information is present for the Snapshot and Log Reader agents.</span></span> <span data-ttu-id="4e9b1-129">ただし、ディストリビューター ビューのディストリビューターの **[エージェント]** タブでは、 **[ディストリビューター エージェント]** および **[マージ エージェント]** も選択できます。</span><span class="sxs-lookup"><span data-stu-id="4e9b1-129">However, in the **Agents** tab for a Distributor in Distributor view, you can also select **Distributor Agent** and **Merge Agent**.</span></span>  
  
### <a name="options"></a><span data-ttu-id="4e9b1-130">Options</span><span class="sxs-lookup"><span data-stu-id="4e9b1-130">Options</span></span>  
 <span data-ttu-id="4e9b1-131">この後のセクションでは、このタブで表示されるディストリビューター エージェントおよびマージ エージェントのデータについて説明します。</span><span class="sxs-lookup"><span data-stu-id="4e9b1-131">The following sections describe the data that is displayed on this tab for the Distributor Agent and Merge Agent.</span></span>  
  
### <a name="distributor-agent"></a><span data-ttu-id="4e9b1-132">[ディストリビューター エージェント]</span><span class="sxs-lookup"><span data-stu-id="4e9b1-132">Distributor Agent</span></span>  
 <span data-ttu-id="4e9b1-133">**状態**</span><span class="sxs-lookup"><span data-stu-id="4e9b1-133">**Status**</span></span>  
 <span data-ttu-id="4e9b1-134">エージェントの状態です。</span><span class="sxs-lookup"><span data-stu-id="4e9b1-134">The status of the agent.</span></span> <span data-ttu-id="4e9b1-135">表示される状態の種類を、次に示します。</span><span class="sxs-lookup"><span data-stu-id="4e9b1-135">The following list shows the possible status values:</span></span>  
  
-   <span data-ttu-id="4e9b1-136">エラー</span><span class="sxs-lookup"><span data-stu-id="4e9b1-136">Error</span></span>    
-   <span data-ttu-id="4e9b1-137">再試行</span><span class="sxs-lookup"><span data-stu-id="4e9b1-137">Retry</span></span>    
-   <span data-ttu-id="4e9b1-138">実行中</span><span class="sxs-lookup"><span data-stu-id="4e9b1-138">Running</span></span>    
-   <span data-ttu-id="4e9b1-139">停止中</span><span class="sxs-lookup"><span data-stu-id="4e9b1-139">Not Running</span></span>    
-   <span data-ttu-id="4e9b1-140">[一度も開始していない]</span><span class="sxs-lookup"><span data-stu-id="4e9b1-140">Never started</span></span>  
  
 <span data-ttu-id="4e9b1-141">**発行元**</span><span class="sxs-lookup"><span data-stu-id="4e9b1-141">**Publisher**</span></span>  
 <span data-ttu-id="4e9b1-142">パブリッシャーの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスです。</span><span class="sxs-lookup"><span data-stu-id="4e9b1-142">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance of the Publisher.</span></span>  
  
 <span data-ttu-id="4e9b1-143">**Publication**</span><span class="sxs-lookup"><span data-stu-id="4e9b1-143">**Publication**</span></span>  
 <span data-ttu-id="4e9b1-144">エージェントが関連付けられているパブリケーションの名前です。</span><span class="sxs-lookup"><span data-stu-id="4e9b1-144">The name of the publication with which the agent is associated.</span></span>  
  
 <span data-ttu-id="4e9b1-145">**サブスクリプション**</span><span class="sxs-lookup"><span data-stu-id="4e9b1-145">**Subscription**</span></span>  
 <span data-ttu-id="4e9b1-146">[*SubscriberName*].[*Database*] という形式のサブスクリプションの名前です。</span><span class="sxs-lookup"><span data-stu-id="4e9b1-146">The name of the subscription, in the form: [*SubscriberName*].[*Database*].</span></span>  
  
 <span data-ttu-id="4e9b1-147">**Type**</span><span class="sxs-lookup"><span data-stu-id="4e9b1-147">**Type**</span></span>  
 <span data-ttu-id="4e9b1-148">レプリケーションの種類 (プッシュ、プル、または匿名) です。</span><span class="sxs-lookup"><span data-stu-id="4e9b1-148">Type of replication: push, pull, or Anonymous.</span></span>  
  
 <span data-ttu-id="4e9b1-149">**前回の開始時刻**</span><span class="sxs-lookup"><span data-stu-id="4e9b1-149">**Last Start Time**</span></span>  
 <span data-ttu-id="4e9b1-150">前回のエージェントの開始時刻です。</span><span class="sxs-lookup"><span data-stu-id="4e9b1-150">The last time at which the agent started.</span></span>  
  
 <span data-ttu-id="4e9b1-151">**Duration**</span><span class="sxs-lookup"><span data-stu-id="4e9b1-151">**Duration**</span></span>  
 <span data-ttu-id="4e9b1-152">エージェントが実行された時間の長さです。</span><span class="sxs-lookup"><span data-stu-id="4e9b1-152">The length of time that the agent has run.</span></span> <span data-ttu-id="4e9b1-153">この時間は、エージェントが現在実行中の場合は経過時間、エージェントが以前に実行されている場合は合計時間を表します。</span><span class="sxs-lookup"><span data-stu-id="4e9b1-153">The time represents elapsed time if the agent is currently running, and total time if the agent has run previously.</span></span>  
  
 <span data-ttu-id="4e9b1-154">**[最後のアクション]**</span><span class="sxs-lookup"><span data-stu-id="4e9b1-154">**Last Action**</span></span>  
 <span data-ttu-id="4e9b1-155">エージェントが最後に実行されたときに最後に実行されたアクションです。</span><span class="sxs-lookup"><span data-stu-id="4e9b1-155">The last action that was performed during the most recent run of the agent.</span></span>  
  
 <span data-ttu-id="4e9b1-156">**[配信率]**</span><span class="sxs-lookup"><span data-stu-id="4e9b1-156">**Delivery Rate**</span></span>  
 <span data-ttu-id="4e9b1-157">エージェントが最後に実行されたときにディストリビューション データベースで初期化コマンドがコミットされた頻度 (1 秒あたりのコマンド数) です。</span><span class="sxs-lookup"><span data-stu-id="4e9b1-157">The rate, in commands per second, at which initialization commands are committed in the distribution database during the most recent run of the agent.</span></span>  
  
 <span data-ttu-id="4e9b1-158">**待機時間**</span><span class="sxs-lookup"><span data-stu-id="4e9b1-158">**Latency**</span></span>  
 <span data-ttu-id="4e9b1-159">パブリケーション データベースで最新の変更がコミットされてから、ディストリビューション データベースで対応するコマンドがコミットされるまでに経過した時間 (秒単位) です。</span><span class="sxs-lookup"><span data-stu-id="4e9b1-159">The time, in seconds, that has elapsed between the most recent change being committed in the publication database, and the corresponding command being committed in the distribution database.</span></span>  
  
 <span data-ttu-id="4e9b1-160">**[#Trans]**</span><span class="sxs-lookup"><span data-stu-id="4e9b1-160">**#Trans**</span></span>  
 <span data-ttu-id="4e9b1-161">エージェントが最後に実行されたときにディストリビューション データベースでコミットされたトランザクションの数です。</span><span class="sxs-lookup"><span data-stu-id="4e9b1-161">The number of transactions committed in the distribution database during the most recent run of the agent.</span></span>  
  
 <span data-ttu-id="4e9b1-162">**[#Cmds]**</span><span class="sxs-lookup"><span data-stu-id="4e9b1-162">**#Cmds**</span></span>  
 <span data-ttu-id="4e9b1-163">エージェントが最後に実行されたときにディストリビューション データベースでコミットされたコマンドの数です。</span><span class="sxs-lookup"><span data-stu-id="4e9b1-163">The number of commands committed in the distribution database during the most recent run of the agent.</span></span> <span data-ttu-id="4e9b1-164">更新などのデータ変更がコマンドに相当します。</span><span class="sxs-lookup"><span data-stu-id="4e9b1-164">A command is the same as a data change, such as an update.</span></span>  
  
 <span data-ttu-id="4e9b1-165">**[Avg. #Cmds]**</span><span class="sxs-lookup"><span data-stu-id="4e9b1-165">**Avg. #Cmds**</span></span>  
 <span data-ttu-id="4e9b1-166">エージェントが最後に実行されたときの 1 トランザクションあたりの平均コマンド数です。</span><span class="sxs-lookup"><span data-stu-id="4e9b1-166">The average number of commands per transaction during the most recent run of the agent.</span></span>  
  
### <a name="merge-agent"></a><span data-ttu-id="4e9b1-167">[マージ エージェント]</span><span class="sxs-lookup"><span data-stu-id="4e9b1-167">Merge Agent</span></span>  
 <span data-ttu-id="4e9b1-168">**状態**</span><span class="sxs-lookup"><span data-stu-id="4e9b1-168">**Status**</span></span>  
 <span data-ttu-id="4e9b1-169">エージェントの状態です。</span><span class="sxs-lookup"><span data-stu-id="4e9b1-169">The status of the agent.</span></span> <span data-ttu-id="4e9b1-170">表示される状態の種類を、次に示します。</span><span class="sxs-lookup"><span data-stu-id="4e9b1-170">The following list shows the possible status values:</span></span>  
  
-   <span data-ttu-id="4e9b1-171">エラー</span><span class="sxs-lookup"><span data-stu-id="4e9b1-171">Error</span></span>    
-   <span data-ttu-id="4e9b1-172">再試行</span><span class="sxs-lookup"><span data-stu-id="4e9b1-172">Retry</span></span>    
-   <span data-ttu-id="4e9b1-173">実行中</span><span class="sxs-lookup"><span data-stu-id="4e9b1-173">Running</span></span>    
-   <span data-ttu-id="4e9b1-174">停止中</span><span class="sxs-lookup"><span data-stu-id="4e9b1-174">Not Running</span></span>    
-   <span data-ttu-id="4e9b1-175">[一度も開始していない]</span><span class="sxs-lookup"><span data-stu-id="4e9b1-175">Never started</span></span>  
  
 <span data-ttu-id="4e9b1-176">**発行元**</span><span class="sxs-lookup"><span data-stu-id="4e9b1-176">**Publisher**</span></span>  
 <span data-ttu-id="4e9b1-177">パブリッシャーの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスです。</span><span class="sxs-lookup"><span data-stu-id="4e9b1-177">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance of the Publisher.</span></span>  
  
 <span data-ttu-id="4e9b1-178">**Publication**</span><span class="sxs-lookup"><span data-stu-id="4e9b1-178">**Publication**</span></span>  
 <span data-ttu-id="4e9b1-179">エージェントが関連付けられているパブリケーションの名前です。</span><span class="sxs-lookup"><span data-stu-id="4e9b1-179">The name of the publication with which the agent is associated.</span></span>  
  
 <span data-ttu-id="4e9b1-180">**サブスクリプション**</span><span class="sxs-lookup"><span data-stu-id="4e9b1-180">**Subscription**</span></span>  
 <span data-ttu-id="4e9b1-181">[*SubscriberName*].[*Database*] という形式のサブスクリプションの名前です。</span><span class="sxs-lookup"><span data-stu-id="4e9b1-181">The name of the subscription, in the form: [*SubscriberName*].[*Database*].</span></span>  
  
 <span data-ttu-id="4e9b1-182">**Type**</span><span class="sxs-lookup"><span data-stu-id="4e9b1-182">**Type**</span></span>  
 <span data-ttu-id="4e9b1-183">レプリケーションの種類 (プッシュ、プル、または匿名) です。</span><span class="sxs-lookup"><span data-stu-id="4e9b1-183">Type of replication: push, pull, or Anonymous.</span></span>  
  
 <span data-ttu-id="4e9b1-184">**前回の開始時刻**</span><span class="sxs-lookup"><span data-stu-id="4e9b1-184">**Last Start Time**</span></span>  
 <span data-ttu-id="4e9b1-185">前回のエージェントの開始時刻です。</span><span class="sxs-lookup"><span data-stu-id="4e9b1-185">The last time at which the agent started.</span></span>  
  
 <span data-ttu-id="4e9b1-186">**Duration**</span><span class="sxs-lookup"><span data-stu-id="4e9b1-186">**Duration**</span></span>  
 <span data-ttu-id="4e9b1-187">エージェントが実行された時間の長さです。</span><span class="sxs-lookup"><span data-stu-id="4e9b1-187">The length of time that the agent has run.</span></span> <span data-ttu-id="4e9b1-188">この時間は、エージェントが現在実行中の場合は経過時間、エージェントが以前に実行されている場合は合計時間を表します。</span><span class="sxs-lookup"><span data-stu-id="4e9b1-188">The time represents elapsed time if the agent is currently running, and total time if the agent has run previously.</span></span>  
  
 <span data-ttu-id="4e9b1-189">**[最後のアクション]**</span><span class="sxs-lookup"><span data-stu-id="4e9b1-189">**Last Action**</span></span>  
 <span data-ttu-id="4e9b1-190">エージェントが最後に実行されたときに最後に実行されたアクションです。</span><span class="sxs-lookup"><span data-stu-id="4e9b1-190">The last action that was performed during the most recent run of the agent.</span></span>  
  
 <span data-ttu-id="4e9b1-191">**[配信率]**</span><span class="sxs-lookup"><span data-stu-id="4e9b1-191">**Delivery Rate**</span></span>  
 <span data-ttu-id="4e9b1-192">ディストリビューション データベースで変更がコミットされた頻度 (1 秒あたりのコマンド数) です。</span><span class="sxs-lookup"><span data-stu-id="4e9b1-192">The rate, in commands per second, at which changes are committed in the distribution database.</span></span>  
  
 <span data-ttu-id="4e9b1-193">**[パブリッシャーの挿入]**</span><span class="sxs-lookup"><span data-stu-id="4e9b1-193">**Publisher Inserts**</span></span>  
 <span data-ttu-id="4e9b1-194">パブリッシャー側で適用される INSERT コマンドの数です。</span><span class="sxs-lookup"><span data-stu-id="4e9b1-194">Number of INSERT commands applied at the Publisher.</span></span>  
  
 <span data-ttu-id="4e9b1-195">**[パブリッシャーの更新]**</span><span class="sxs-lookup"><span data-stu-id="4e9b1-195">**Publisher Updates**</span></span>  
 <span data-ttu-id="4e9b1-196">パブリッシャー側で適用される UPDATE コマンドの数です。</span><span class="sxs-lookup"><span data-stu-id="4e9b1-196">Number of UPDATE commands applied at the Publisher.</span></span>  
  
 <span data-ttu-id="4e9b1-197">**[パブリッシャーの削除]**</span><span class="sxs-lookup"><span data-stu-id="4e9b1-197">**Publisher Deletes**</span></span>  
 <span data-ttu-id="4e9b1-198">パブリッシャー側で適用される DELETE コマンドの数です。</span><span class="sxs-lookup"><span data-stu-id="4e9b1-198">Number of DELETE commands applied at the Publisher.</span></span>  
  
 <span data-ttu-id="4e9b1-199">**[パブリッシャーの競合]**</span><span class="sxs-lookup"><span data-stu-id="4e9b1-199">**Publisher Conflicts**</span></span>  
 <span data-ttu-id="4e9b1-200">マージ プロセス中にパブリッシャー側で発生した競合の数です。</span><span class="sxs-lookup"><span data-stu-id="4e9b1-200">The number of conflicts occurring at the Publisher during the merge process.</span></span>  
  
 <span data-ttu-id="4e9b1-201">**[サブスクライバーの挿入]**</span><span class="sxs-lookup"><span data-stu-id="4e9b1-201">**Subscriber Inserts**</span></span>  
 <span data-ttu-id="4e9b1-202">サブスクライバー側で適用される INSERT コマンドの数です。</span><span class="sxs-lookup"><span data-stu-id="4e9b1-202">Number of INSERT commands applied at the Subscriber.</span></span>  
  
 <span data-ttu-id="4e9b1-203">**[サブスクライバーの更新]**</span><span class="sxs-lookup"><span data-stu-id="4e9b1-203">**Subscriber Updates**</span></span>  
 <span data-ttu-id="4e9b1-204">サブスクライバー側で適用される UPDATE コマンドの数です。</span><span class="sxs-lookup"><span data-stu-id="4e9b1-204">Number of UPDATE commands applied at the Subscriber.</span></span>  
  
 <span data-ttu-id="4e9b1-205">**[サブスクライバーの削除]**</span><span class="sxs-lookup"><span data-stu-id="4e9b1-205">**Subscriber Deletes**</span></span>  
 <span data-ttu-id="4e9b1-206">サブスクライバー側で適用される DELETE コマンドの数です。</span><span class="sxs-lookup"><span data-stu-id="4e9b1-206">Number of DELETE commands applied at the Subscriber.</span></span>  
  
 <span data-ttu-id="4e9b1-207">**[サブスクライバーの競合]**</span><span class="sxs-lookup"><span data-stu-id="4e9b1-207">**Subscriber Conflicts**</span></span>  
 <span data-ttu-id="4e9b1-208">マージ プロセス中にサブスクライバー側で発生した競合の数です。</span><span class="sxs-lookup"><span data-stu-id="4e9b1-208">The number of conflicts occurring at the Subscriber during the merge process.</span></span>  
  
 
## <a name="see-also"></a><span data-ttu-id="4e9b1-209">参照</span><span class="sxs-lookup"><span data-stu-id="4e9b1-209">See Also</span></span>  
 <span data-ttu-id="4e9b1-210">[レプリケーションモニターを開始する](monitor/start-the-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="4e9b1-210">[Start the Replication Monitor](monitor/start-the-replication-monitor.md) </span></span>  
 [<span data-ttu-id="4e9b1-211">レプリケーションの監視</span><span class="sxs-lookup"><span data-stu-id="4e9b1-211">Monitoring Replication</span></span>](monitoring-replication.md)  
  
  
