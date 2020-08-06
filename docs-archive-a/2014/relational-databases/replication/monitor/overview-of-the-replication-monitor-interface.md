---
title: レプリケーション モニターのインターフェイスの概要 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Replication Monitor
- Replication Monitor, about Replication Monitor
ms.assetid: 078f0e34-7153-45c4-8725-778b5bef88da
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4d9b7edbd76153f23168ec9bcf4a286d5f7cbe9b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634390"
---
# <a name="overview-of-the-replication-monitor-interface"></a><span data-ttu-id="6d2cd-102">レプリケーション モニターのインターフェイスの概要</span><span class="sxs-lookup"><span data-stu-id="6d2cd-102">Overview of the Replication Monitor Interface</span></span>
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] <span data-ttu-id="6d2cd-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] レプリケーション モニターでは、レプリケーションのすべての利用状況について、パブリッシャー関連の情報またはディストリビューター関連の情報が 2 つのペインで表示されます。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Replication Monitor presents a Publisher-focused view or Distributor-focused view of all replication activity in a two pane format.</span></span> <span data-ttu-id="6d2cd-104">左ペインにパブリッシャーを追加すると、パブリッシャーとそのパブリケーション、パブリケーションのサブスクリプション、およびさまざまなレプリケーション エージェントに関する情報が右ペインに表示されます。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-104">You add a Publisher to the monitor in the left pane, and in the right pane the monitor displays information on the Publisher, its publications, the subscriptions to those publications, and the various replication agents.</span></span> <span data-ttu-id="6d2cd-105">レプリケーション モニターでは、レプリケーション トポロジに関する情報の表示に加えて、エージェントの開始や停止、データの検証などさまざまなタスクを実行できます。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-105">In addition to presenting information for the replication topology, Replication Monitor allows you to perform a number of tasks, such as starting and stopping agents, and validating data.</span></span>  
  
## <a name="viewing-information-for-the-entire-topology"></a><span data-ttu-id="6d2cd-106">トポロジ全体の情報を表示</span><span class="sxs-lookup"><span data-stu-id="6d2cd-106">Viewing Information for the Entire Topology</span></span>  
 <span data-ttu-id="6d2cd-107">レプリケーション モニターの左ペインに表示される情報</span><span class="sxs-lookup"><span data-stu-id="6d2cd-107">The left pane of Replication Monitor displays</span></span>  
  
-   <span data-ttu-id="6d2cd-108">パブリッシャー グループ、パブリッシャー、およびパブリケーション</span><span class="sxs-lookup"><span data-stu-id="6d2cd-108">Publisher groups, Publishers, and publications.</span></span>  
  
-   <span data-ttu-id="6d2cd-109">ディストリビューター、パブリッシャー、およびパブリケーション</span><span class="sxs-lookup"><span data-stu-id="6d2cd-109">Distributors, Publishers, and publications.</span></span>  
  
 <span data-ttu-id="6d2cd-110">レプリケーション モニターで情報を表示するには、最初にパブリッシャーを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-110">To view any information in Replication Monitor, you must first add a Publisher.</span></span> <span data-ttu-id="6d2cd-111">詳細については、「 [レプリケーション モニターのパブリッシャーの追加および削除](add-and-remove-publishers-from-replication-monitor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-111">For more information, see [Add and Remove Publishers from Replication Monitor](add-and-remove-publishers-from-replication-monitor.md).</span></span>  
  
 <span data-ttu-id="6d2cd-112">左ペインに表示される情報は、以下に示す疑問点の解決に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-112">The left pane helps answer the following questions:</span></span>  
  
-   <span data-ttu-id="6d2cd-113">レプリケーション システムは正常に動作していますか。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-113">Is my replication system healthy?</span></span>  
  
     <span data-ttu-id="6d2cd-114">左ペインのノードにエラー アイコンが表示されていない場合、レプリケーション システムは比較的正常に動作しています。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-114">The replication system is relatively healthy if there are no error icons on nodes in the left pane.</span></span> <span data-ttu-id="6d2cd-115">システムの状態に関するより詳細な情報を得るには、 **[サブスクリプション ウォッチ リスト]** タブについても確認する必要があります。このタブには、注意を要するサブスクリプションについての情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-115">To get a more complete view of system health, you should also check the **Subscription Watch List** tab, which displays information on subscriptions that might require attention.</span></span>  
  
-   <span data-ttu-id="6d2cd-116">なぜエージェントが実行されないのですか。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-116">Why is an agent not running?</span></span>  
  
     <span data-ttu-id="6d2cd-117">特定の時間にエージェントが実行されないのは、実行がスケジュールされていないためか、またはエラーが発生したためです。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-117">An agent is not running at a particular time either because it is not scheduled to run or because an error has occurred.</span></span> <span data-ttu-id="6d2cd-118">エラーが発生した場合、左ペインの該当ノードにエラー アイコンが表示されます。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-118">If an error has occurred, an error icon is displayed on the appropriate nodes in the left pane.</span></span> <span data-ttu-id="6d2cd-119">たとえば、パブリケーションのスナップショット エージェントがエラーのために停止したとすると、パブリッシャー グループ、パブリッシャー、およびパブリケーション ノードにエラー アイコンが表示されます。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-119">For example, if the Snapshot Agent for a publication stopped because of an error, an error icon is displayed on the Publisher group, Publisher, and publication nodes.</span></span> <span data-ttu-id="6d2cd-120">パブリケーションの **[エージェント]** タブには、スナップショット エージェントの概要情報が表示されます。このタブのスナップショット エージェントをダブルクリックすると、エラー情報の詳細が表示されます。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-120">Summary information for the Snapshot Agent is displayed on the **Agents** tab for the publication; double click the Snapshot Agent on this tab for detailed error information.</span></span>  
  
## <a name="viewing-information-and-performing-tasks-related-to-distributors"></a><span data-ttu-id="6d2cd-121">ディストリビューター関連の情報の表示とタスクの実行</span><span class="sxs-lookup"><span data-stu-id="6d2cd-121">Viewing Information and Performing Tasks Related to Distributors</span></span>  
 <span data-ttu-id="6d2cd-122">レプリケーション モニターでは、以下の 3 つのタブにディストリビューターに関する情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-122">Replication Monitor displays information about Distributors on three tabs:</span></span>  
  
-   <span data-ttu-id="6d2cd-123">**[パブリケーション]** タブ</span><span class="sxs-lookup"><span data-stu-id="6d2cd-123">**Publications** tab</span></span>  
  
     <span data-ttu-id="6d2cd-124">このタブには、ディストリビューターのすべてのパブリケーションに関する概要情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-124">This tab provides summary information for all publications of a Distributor.</span></span>  
  
-   <span data-ttu-id="6d2cd-125">**[サブスクリプション ウォッチ リスト]** タブ</span><span class="sxs-lookup"><span data-stu-id="6d2cd-125">**Subscription Watch List** tab</span></span>  
  
     <span data-ttu-id="6d2cd-126">このタブには、選択されたディストリビューターのサブスクリプションに関する情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-126">This tab provides information about subscriptions for the selected Distributor.</span></span> <span data-ttu-id="6d2cd-127">サブスクリプションの一覧にフィルターをかけて、エラー、警告、および動作に問題があるサブスクリプションを確認できます。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-127">You can filter the list of subscriptions to see errors, warnings, and any poorly performing subscriptions.</span></span> <span data-ttu-id="6d2cd-128">このタブでは、サブスクリプションのプロパティへのアクセス、エージェントやサブスクリプションに関連付けられたエージェントに関する詳細情報へのアクセス、サブスクリプションの再初期化、およびサブスクリプションの検証を行うこともできます。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-128">The tab also lets you to perform the following tasks: access subscription properties, access detailed information about the agent or agents associated with a subscription, reinitialize subscriptions, and validate subscriptions.</span></span>  
  
     <span data-ttu-id="6d2cd-129">**[サブスクリプション ウォッチ リスト]** タブに表示される情報は、以下に示す疑問点の解決に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-129">The **Subscription Watch List** tab helps answer the following questions:</span></span>  
  
    -   <span data-ttu-id="6d2cd-130">処理の遅いサブスクリプションはどれですか。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-130">Which subscriptions are slow?</span></span>  
  
         <span data-ttu-id="6d2cd-131">このタブのオプションを設定すると、パフォーマンス順に並べられたサブスクリプションがグリッドに表示されます。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-131">Set options on this tab so that the grid displays subscriptions in order by their relative performance.</span></span>  
  
    -   <span data-ttu-id="6d2cd-132">レプリケーション システムは正常に動作していますか。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-132">Is my replication system healthy?</span></span>  
  
         <span data-ttu-id="6d2cd-133">このタブのグリッドには、注意を要するすべてのサブスクリプションのエラー アイコンと警告アイコンが表示されます。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-133">The grid on this tab displays error and warning icons for any subscriptions that require your attention.</span></span>  
  
     <span data-ttu-id="6d2cd-134">このタブは、 [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] 以前のバージョンが動作しているディストリビューターでは利用できません。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-134">This tab is not available for Distributors that are running versions of [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] or earlier.</span></span>  
  
-   <span data-ttu-id="6d2cd-135">**[エージェント]** タブ</span><span class="sxs-lookup"><span data-stu-id="6d2cd-135">**Agents** tab</span></span>  
  
     <span data-ttu-id="6d2cd-136">このタブには、すべての種類のレプリケーションで使用されるエージェントおよびジョブに関する詳細情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-136">This tab displays detailed information about the agents and jobs that are used by all types of replication.</span></span> <span data-ttu-id="6d2cd-137">また、各エージェントとジョブを開始および停止することもできます。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-137">The tab also let you start and stop each agent and job.</span></span>  
  
 <span data-ttu-id="6d2cd-138">レプリケーション モニターでは、ディストリビューター ノードのコンテキスト メニューも使用できます。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-138">Replication Monitor also provides a context menu for the Distributor node.</span></span> <span data-ttu-id="6d2cd-139">左ペインのディストリビューターを右クリックすると、以下の操作を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-139">Right-click a Distributor in the left pane to perform the following tasks:</span></span>  
  
-   <span data-ttu-id="6d2cd-140">レプリケーション モニターにパブリッシャーを追加する。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-140">Add a Publisher to Replication Monitor.</span></span>  
  
-   <span data-ttu-id="6d2cd-141">ディストリビューターに対するレプリケーション モニター設定を編集する。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-141">Edit Replication Monitor settings for the Distributor.</span></span>  
  
-   <span data-ttu-id="6d2cd-142">パブリッシャー グループ ビューに切り替える。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-142">Switch to the Publisher Group view.</span></span>  
  
## <a name="viewing-information-and-performing-tasks-related-to-publishers"></a><span data-ttu-id="6d2cd-143">情報の表示とパブリッシャー関連のタスクの実行</span><span class="sxs-lookup"><span data-stu-id="6d2cd-143">Viewing Information and Performing Tasks Related to Publishers</span></span>  
 <span data-ttu-id="6d2cd-144">レプリケーション モニターでは、以下の 3 つのタブにパブリッシャーに関する情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-144">Replication Monitor displays information about Publishers on three tabs:</span></span>  
  
-   <span data-ttu-id="6d2cd-145">**[パブリケーション]** タブ</span><span class="sxs-lookup"><span data-stu-id="6d2cd-145">**Publications** tab</span></span>  
  
     <span data-ttu-id="6d2cd-146">このタブには、パブリッシャーのすべてのパブリケーションに関する概要情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-146">This tab provides summary information for all publications at a Publisher.</span></span>  
  
-   <span data-ttu-id="6d2cd-147">**[サブスクリプション ウォッチ リスト]** タブ</span><span class="sxs-lookup"><span data-stu-id="6d2cd-147">**Subscription Watch List** tab</span></span>  
  
     <span data-ttu-id="6d2cd-148">このタブには、選択したパブリッシャーで利用可能なすべてのパブリケーションからのサブスクリプションに関する情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-148">This tab is intended to display information on subscriptions from all publications available at the selected Publisher.</span></span> <span data-ttu-id="6d2cd-149">サブスクリプションの一覧にフィルターをかけて、エラー、警告、および動作に問題があるサブスクリプションを確認できます。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-149">You can filter the list of subscriptions to see errors, warnings, and any poorly performing subscriptions.</span></span> <span data-ttu-id="6d2cd-150">このタブでは、サブスクリプションのプロパティへのアクセス、エージェントやサブスクリプションに関連付けられたエージェントに関する詳細情報へのアクセス、サブスクリプションの再初期化、およびサブスクリプションの検証を行うこともできます。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-150">The tab also allows you to: access subscription properties; access detailed information about the agent or agents associated with a subscription; reinitialize subscriptions; and validate subscriptions.</span></span>  
  
     <span data-ttu-id="6d2cd-151">**[サブスクリプション ウォッチ リスト]** タブに表示される情報は、以下に示す疑問点の解決に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-151">The **Subscription Watch List** tab helps answer the following questions:</span></span>  
  
    -   <span data-ttu-id="6d2cd-152">処理の遅いサブスクリプションはどれですか。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-152">Which subscriptions are slow?</span></span>  
  
         <span data-ttu-id="6d2cd-153">このタブのオプションを設定すると、パフォーマンス順に並べられたサブスクリプションがグリッドに表示されます。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-153">Set options on this tab so that the grid displays subscriptions in order by their relative performance.</span></span>  
  
    -   <span data-ttu-id="6d2cd-154">レプリケーション システムは正常に動作していますか。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-154">Is my replication system healthy?</span></span>  
  
         <span data-ttu-id="6d2cd-155">このタブのグリッドには、注意を要するすべてのサブスクリプションのエラー アイコンと警告アイコンが表示されます。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-155">The grid on this tab displays error and warning icons for any subscriptions that require your attention.</span></span>  
  
     <span data-ttu-id="6d2cd-156">[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]より前のバージョンを実行しているディストリビューターでは、このタブが表示されません。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-156">This tab is not displayed for Distributors running versions prior to [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].</span></span>  
  
-   <span data-ttu-id="6d2cd-157">**[エージェント]** タブ</span><span class="sxs-lookup"><span data-stu-id="6d2cd-157">**Agents** tab</span></span>  
  
     <span data-ttu-id="6d2cd-158">このタブには、すべての種類のレプリケーションで使用されるエージェントおよびジョブに関する詳細情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-158">This tab displays detailed information about the agents and jobs used by all types of replication.</span></span> <span data-ttu-id="6d2cd-159">また、各エージェントとジョブを開始および停止することもできます。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-159">The tab also allows you to start and stop each agent and job.</span></span>  
  
 <span data-ttu-id="6d2cd-160">詳細については、「[レプリケーション モニターを使用して情報を表示し、タスクを実行する](view-information-and-perform-tasks-replication-monitor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-160">For more information, see [View Information and Perform Tasks using Replication Monitor](view-information-and-perform-tasks-replication-monitor.md).</span></span>  
  
 <span data-ttu-id="6d2cd-161">レプリケーション モニターでは、パブリッシャー ノードのコンテキスト メニューも使用できます。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-161">Replication Monitor also provides a context menu for the Publisher node.</span></span> <span data-ttu-id="6d2cd-162">左ペインのパブリッシャーを右クリックすると、以下の操作を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-162">Right-click a Publisher in the left pane to:</span></span>  
  
-   <span data-ttu-id="6d2cd-163">パブリッシャーに対するレプリケーション モニター設定の編集</span><span class="sxs-lookup"><span data-stu-id="6d2cd-163">Edit Replication Monitor settings for the Publisher</span></span>  
  
-   <span data-ttu-id="6d2cd-164">レプリケーション モニターからのパブリッシャーの削除</span><span class="sxs-lookup"><span data-stu-id="6d2cd-164">Remove the Publisher from Replication Monitor</span></span>  
  
-   <span data-ttu-id="6d2cd-165">エージェント プロファイルの表示と編集</span><span class="sxs-lookup"><span data-stu-id="6d2cd-165">View and edit agent profiles</span></span>  
  
-   <span data-ttu-id="6d2cd-166">パブリッシャーについての情報を格納するディストリビューターへの接続と切断</span><span class="sxs-lookup"><span data-stu-id="6d2cd-166">Connect to or disconnect from the Distributor that stores information about the Publisher</span></span>  
  
## <a name="viewing-information-and-performing-tasks-related-to-publications"></a><span data-ttu-id="6d2cd-167">情報の表示とパブリケーション関連のタスクの実行</span><span class="sxs-lookup"><span data-stu-id="6d2cd-167">Viewing Information and Performing Tasks Related to Publications</span></span>  
 <span data-ttu-id="6d2cd-168">レプリケーション モニターでは、以下の 3 つのタブとさまざまな詳細ウィンドウにパブリケーション関連の情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-168">Replication Monitor displays information about publications on three tabs and a number of detail windows:</span></span>  
  
-   <span data-ttu-id="6d2cd-169">**[すべてのサブスクリプション]** タブ</span><span class="sxs-lookup"><span data-stu-id="6d2cd-169">**All Subscriptions** tab</span></span>  
  
     <span data-ttu-id="6d2cd-170">このタブには、選択されたパブリケーションのすべてのサブスクリプションに関する情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-170">This tab displays information about all subscriptions to the selected publication.</span></span> <span data-ttu-id="6d2cd-171">このタブの既定の並べ替えには、まずエラーの優先度、次に警告の優先度、そしてパフォーマンス (昇順) が使用され、パフォーマンスに問題のあるサブスクリプションが上位に表示されます。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-171">By default, this tab is sorted in priority order: errors, then warnings, then in increasing order of performance, with any poorly performing subscriptions at the top.</span></span>  
  
     <span data-ttu-id="6d2cd-172">**[すべてのサブスクリプション]** タブに表示される情報は、以下に示す疑問点の解決に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-172">The **All Subscriptions** tab helps answer the following questions:</span></span>  
  
    -   <span data-ttu-id="6d2cd-173">処理の遅いサブスクリプションはどれですか。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-173">Which subscriptions are slow?</span></span>  
  
         <span data-ttu-id="6d2cd-174">このタブのオプションを設定すると、パフォーマンス順に並べられたサブスクリプションがグリッドに表示されます。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-174">Set options on this tab so that the grid displays subscriptions in order by their relative performance.</span></span>  
  
    -   <span data-ttu-id="6d2cd-175">レプリケーション システムは正常に動作していますか。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-175">Is my replication system healthy?</span></span>  
  
         <span data-ttu-id="6d2cd-176">このタブのグリッドには、注意を要するすべてのサブスクリプションのエラー アイコンと警告アイコンが表示されます。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-176">The grid on this tab displays error and warning icons for any subscriptions that require your attention.</span></span>  
  
-   <span data-ttu-id="6d2cd-177">**[エージェント]** タブ</span><span class="sxs-lookup"><span data-stu-id="6d2cd-177">**Agents** tab</span></span>  
  
     <span data-ttu-id="6d2cd-178">このタブには、レプリケーションで使用されるエージェントに関する情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-178">This tab displays information about the agents that are used by replication.</span></span> <span data-ttu-id="6d2cd-179">このタブには、以下のエージェントの情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-179">This tab displays information about the following agents:</span></span>  
  
    -   <span data-ttu-id="6d2cd-180">すべてのパブリケーションで使用されるスナップショット エージェント</span><span class="sxs-lookup"><span data-stu-id="6d2cd-180">The Snapshot Agent, which is used by all publications.</span></span>  
  
    -   <span data-ttu-id="6d2cd-181">すべてのトランザクション パブリケーションで使用されるログ リーダー エージェント</span><span class="sxs-lookup"><span data-stu-id="6d2cd-181">The Log Reader Agent, which is used by all transactional publications.</span></span>  
  
    -   <span data-ttu-id="6d2cd-182">キュー更新サブスクリプションに有効なトランザクション パブリケーションで使用されるキュー リーダー エージェント</span><span class="sxs-lookup"><span data-stu-id="6d2cd-182">The Queue Reader Agent, which is used by transactional publications enabled for queued updating subscriptions.</span></span>  
  
     <span data-ttu-id="6d2cd-183">このタブでは、各エージェントに関する詳細情報へのアクセス、および各エージェントの開始と停止を行うこともできます。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-183">The tab also allows for you to perform the following tasks: access detailed information about each agent, and start and stop each agent.</span></span> <span data-ttu-id="6d2cd-184">サブスクリプションに関連するエージェント (ディストリビューション エージェントおよびマージ エージェント) の詳細については、このトピックの「情報の表示とサブスクリプション関連のタスクの実行」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-184">For information about agents that are associated with subscriptions (the Distribution Agent and Merge Agent), see the section "Viewing Information and Performing Tasks Related to Subscriptions" in this topic.</span></span>  
  
-   <span data-ttu-id="6d2cd-185">**[警告]** タブ</span><span class="sxs-lookup"><span data-stu-id="6d2cd-185">**Warnings** tab</span></span>  
  
     <span data-ttu-id="6d2cd-186">このタブを使用して、エージェントに対する警告とアラートを指定できます。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-186">This tab enables you to specify warnings and alerts for agents.</span></span> <span data-ttu-id="6d2cd-187">詳細については、「 [Set Thresholds and Warnings in Replication Monitor](set-thresholds-and-warnings-in-replication-monitor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-187">For more information, see [Set Thresholds and Warnings in Replication Monitor](set-thresholds-and-warnings-in-replication-monitor.md).</span></span>  
  
-   <span data-ttu-id="6d2cd-188">**[トレーサー トークン]** タブ (トランザクション レプリケーションのみ)</span><span class="sxs-lookup"><span data-stu-id="6d2cd-188">**Tracer Tokens** tab (transactional replication only)</span></span>  
  
     <span data-ttu-id="6d2cd-189">このタブでは、待機時間、つまりパブリッシャーでトランザクションがコミットされてから、対応するトランザクションがサブスクライバーでコミットされるまでの経過時間を測定できます。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-189">This tab allows you to measure latency, the amount of time that elapses between a transaction being committed at the Publisher and the corresponding transaction being committed at the Subscriber.</span></span>  
  
     <span data-ttu-id="6d2cd-190">このタブに表示される情報は、以下に示す疑問点の解決に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-190">This tab helps answers the following question:</span></span>  
  
    -   <span data-ttu-id="6d2cd-191">トランザクション レプリケーションにおいて、コミットされたトランザクションがサブスクライバーに伝達されるまでどれくらいの時間が必要ですか。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-191">How long will it take a transaction committed now to reach a Subscriber in transactional replication?</span></span>  
  
         <span data-ttu-id="6d2cd-192">システムにおけるトランザクションの伝達時間を表示して、以前の伝達時間と比較します。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-192">View the total time for a transaction to travel through the system and also compare it to previous times.</span></span>  
  
     <span data-ttu-id="6d2cd-193">[!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] 以前のバージョンを実行しているディストリビューターでは、このタブが表示されません。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-193">This tab is not displayed for Distributors running [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] or earlier.</span></span> <span data-ttu-id="6d2cd-194">トレーサー トークンの詳細については、「[トランザクション レプリケーションの待機時間の計測および接続の検証](measure-latency-and-validate-connections-for-transactional-replication.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-194">For more information on tracer tokens, see [Measure Latency and Validate Connections for Transactional Replication](measure-latency-and-validate-connections-for-transactional-replication.md).</span></span>  
  
-   <span data-ttu-id="6d2cd-195">パブリケーションに関連するエージェントの詳細ウィンドウ。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-195">Detail windows for the agents associated with a publication.</span></span> <span data-ttu-id="6d2cd-196">パブリケーションに関連するエージェントは以下のとおりです。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-196">The following agents are associated with publications:</span></span>  
  
    -   <span data-ttu-id="6d2cd-197">すべてのパブリケーションで使用されるスナップショット エージェント</span><span class="sxs-lookup"><span data-stu-id="6d2cd-197">The Snapshot Agent, which is used by all publications.</span></span>  
  
    -   <span data-ttu-id="6d2cd-198">すべてのトランザクション パブリケーションで使用されるログ リーダー エージェント</span><span class="sxs-lookup"><span data-stu-id="6d2cd-198">The Log Reader Agent, which is used by all transactional publications.</span></span>  
  
    -   <span data-ttu-id="6d2cd-199">キュー更新サブスクリプションに有効なトランザクション パブリケーションで使用されるキュー リーダー エージェント</span><span class="sxs-lookup"><span data-stu-id="6d2cd-199">The Queue Reader Agent, which is used by transactional publications enabled for queued updating subscriptions.</span></span>  
  
     <span data-ttu-id="6d2cd-200">詳細ウィンドウの情報にアクセスするには、レプリケーション モニターのエージェントをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-200">Double-click an agent in Replication Monitor to access information in a detail window.</span></span> <span data-ttu-id="6d2cd-201">上記のエージェントに加えて、サブスクリプションに関連するエージェントがあります。これらのエージェントには、スナップショットおよびトランザクション パブリケーションに対するサブスクリプションのディストリビューション エージェントと、マージ パブリケーションに対するサブスクリプションのマージエージェントがあります。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-201">In addition to the agents listed above, there are agents associated with subscriptions: the Distribution Agent for subscriptions to snapshot and transactional publications; and the Merge Agent for subscriptions to merge publications.</span></span> <span data-ttu-id="6d2cd-202">詳細については、このトピックの「情報の表示とサブスクリプション関連のタスクの実行」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-202">For more information, see the section "Viewing Information and Performing Tasks Related to Subscriptions" in this topic.</span></span>  
  
     <span data-ttu-id="6d2cd-203">エージェントの詳細ウィンドウには、セッションの開始時刻、終了時刻、期間、セッション中に実行されるアクションなど、エージェントのセッションに関する情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-203">The agent detail windows provide information about agent sessions, including start time, end time, duration, and the actions performed in a session.</span></span> <span data-ttu-id="6d2cd-204">これらの情報は、以下に示す疑問点の解決に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-204">They help to answer the following question:</span></span>  
  
    -   <span data-ttu-id="6d2cd-205">なぜエージェントが実行されないのですか。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-205">Why is an agent not running?</span></span>  
  
         <span data-ttu-id="6d2cd-206">エラー メッセージに、エージェントが実行されない理由についての詳細情報が表示され、パブリケーションに関連するエージェントに対するトラブルシューティングを開始できます。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-206">The error messages available provide detailed information on why an agent is not running and provide a starting point for troubleshooting issues with the agents associated with a publication.</span></span>  
  
 <span data-ttu-id="6d2cd-207">詳細については、「[レプリケーション モニターを使用して情報を表示し、タスクを実行する](view-information-and-perform-tasks-replication-monitor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-207">For more information, see [View Information and Perform Tasks using Replication Monitor](view-information-and-perform-tasks-replication-monitor.md).</span></span>  
  
 <span data-ttu-id="6d2cd-208">レプリケーション モニターでは、パブリケーション ノードのコンテキスト メニューも使用できます。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-208">Replication Monitor also provides a context menu for the publications node.</span></span> <span data-ttu-id="6d2cd-209">左ペインのパブリケーションを右クリックすると、以下の操作を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-209">Right-click a publication in the left pane to:</span></span>  
  
-   <span data-ttu-id="6d2cd-210">パブリケーションに対するすべてのサブスクリプションの再初期化</span><span class="sxs-lookup"><span data-stu-id="6d2cd-210">Reinitialize all subscriptions to a publication</span></span>  
  
-   <span data-ttu-id="6d2cd-211">パブリケーションに対するすべてのサブスクリプションの検証</span><span class="sxs-lookup"><span data-stu-id="6d2cd-211">Validate all subscriptions to a publication</span></span>  
  
-   <span data-ttu-id="6d2cd-212">パブリケーションのスナップショットの生成</span><span class="sxs-lookup"><span data-stu-id="6d2cd-212">Generate a snapshot for a publication</span></span>  
  
-   <span data-ttu-id="6d2cd-213">パブリケーションのプロパティの表示と編集</span><span class="sxs-lookup"><span data-stu-id="6d2cd-213">View and edit publication properties</span></span>  
  
## <a name="viewing-information-and-performing-tasks-related-to-subscriptions"></a><span data-ttu-id="6d2cd-214">情報の表示とサブスクリプション関連のタスクの実行</span><span class="sxs-lookup"><span data-stu-id="6d2cd-214">Viewing Information and Performing Tasks Related to Subscriptions</span></span>  
 <span data-ttu-id="6d2cd-215">レプリケーション モニターでは、さまざまなタブにサブスクリプションに関する情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-215">Replication Monitor displays information about subscriptions on a number of different tabs.</span></span> <span data-ttu-id="6d2cd-216">詳細ウィンドウのこれらのタブにアクセスするには、レプリケーション モニターのサブスクリプションをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-216">Double-click a subscription in Replication Monitor to access these tabs in a detail window.</span></span> <span data-ttu-id="6d2cd-217">これらのタブはすべて、エージェントが実行されない理由の解決に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-217">All of the tabs are useful in answering the question "Why is an agent not running?"</span></span> <span data-ttu-id="6d2cd-218">エラー メッセージに、エージェントが実行されない理由についての詳細情報が表示され、サブスクリプションに関連するエージェントに対するトラブルシューティングを開始できます。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-218">The error messages available provide detailed information on why an agent is not running and provide a starting point for troubleshooting issues with the agents associated with a subscription.</span></span>  
  
-   <span data-ttu-id="6d2cd-219">**[すべてのサブスクリプション]** 」および「 **[サブスクリプション ウォッチ リスト]**</span><span class="sxs-lookup"><span data-stu-id="6d2cd-219">**All Subscriptions tab** and **Subscription Watch List tab.**</span></span>  
  
     <span data-ttu-id="6d2cd-220">これらのタブについては、このトピックの前半で説明しています。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-220">These tabs are described earlier in this topic.</span></span>  
  
-   <span data-ttu-id="6d2cd-221">**[パブリッシャーからディストリビューターまでの履歴]** タブ (トランザクション レプリケーションのみ)</span><span class="sxs-lookup"><span data-stu-id="6d2cd-221">**Publisher to Distributor History** tab (transactional replication only)</span></span>  
  
     <span data-ttu-id="6d2cd-222">このタブには、パブリケーションのログ リーダー エージェントに関する情報が表示されます (このタブはログ リーダー エージェントの詳細ウィンドウと同じです)。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-222">This tab displays information on the Log Reader Agent for a publication (the tab is identical to the Log Reader Agent details window).</span></span>  
  
-   <span data-ttu-id="6d2cd-223">**[ディストリビューターからサブスクライバーまでの履歴]** タブ (スナップショット レプリケーションおよびトランザクション レプリケーション)</span><span class="sxs-lookup"><span data-stu-id="6d2cd-223">**Distributor to Subscriber History** tab (snapshot replication and transactional replication)</span></span>  
  
     <span data-ttu-id="6d2cd-224">このタブには、サブスクリプションのディストリビューション エージェントに関する情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-224">This tab displays information on the Distribution Agent for a subscription.</span></span>  
  
-   <span data-ttu-id="6d2cd-225">**[未配布のコマンド]** タブ (トランザクション レプリケーションのみ)</span><span class="sxs-lookup"><span data-stu-id="6d2cd-225">**Undistributed Commands** tab (transactional replication only)</span></span>  
  
     <span data-ttu-id="6d2cd-226">このタブには、選択したサブスクライバーにまだ配布されていないディストリビューション データベース内のコマンドの数と、これらのコマンドの配布予測時間が表示されます。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-226">This tab displays information about the number of commands in the distribution database that have not been delivered to the selected Subscriber, and the estimated time to deliver those commands.</span></span> <span data-ttu-id="6d2cd-227">このタブに表示される情報は、サブスクリプションがどの程度遅れているのかという疑問の解決に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-227">The tab helps answer the question, "How far behind is my subscription?"</span></span> <span data-ttu-id="6d2cd-228">SQL Server 2005 より前のバージョンを実行しているディストリビューターでは、このタブが表示されません。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-228">This tab is not displayed for Distributors running versions prior to SQL Server 2005.</span></span>  
  
-   <span data-ttu-id="6d2cd-229">**[同期の履歴]** タブ (マージ レプリケーションのみ)</span><span class="sxs-lookup"><span data-stu-id="6d2cd-229">**Synchronization History** tab (merge replication only)</span></span>  
  
     <span data-ttu-id="6d2cd-230">このタブには、サブスクリプションのマージ エージェントに関する情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-230">This tab displays information on the Merge Agent for a subscription.</span></span> <span data-ttu-id="6d2cd-231">このタブに表示される情報は、以下に示す疑問点の解決に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-231">This tab helps answer the following question:</span></span>  
  
    -   <span data-ttu-id="6d2cd-232">なぜマージ サブスクリプションの処理が遅いのですか。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-232">Why is my merge subscription slow?</span></span>  
  
         <span data-ttu-id="6d2cd-233">このタブには、同期中に処理される各アーティクルの詳細な統計が表示されます。この統計には、各処理フェーズ (変更のアップロードやダウンロードなど) にかかる時間などが含まれます。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-233">This tab provides detailed statistics for each article processed during synchronization, including the amount of time spent in each processing phase (uploading changes, downloading changes, and so on).</span></span> <span data-ttu-id="6d2cd-234">このタブによって、速度低下の原因となっているテーブルを特定することができます。また、マージ サブスクリプションのパフォーマンスに関するトラブルシューティングを開始するのにも最適です。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-234">It can help pinpoint specific tables that are causing slowdowns and is the best place to troubleshoot performance issues with merge subscriptions.</span></span>  
  
 <span data-ttu-id="6d2cd-235">詳細については、「[レプリケーション モニターを使用して情報を表示し、タスクを実行する](view-information-and-perform-tasks-replication-monitor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-235">For more information, see [View Information and Perform Tasks using Replication Monitor](view-information-and-perform-tasks-replication-monitor.md).</span></span>
  
## <a name="viewing-information-and-performing-tasks-related-to-agent-profiles"></a><span data-ttu-id="6d2cd-236">情報の表示とエージェント プロファイル関連のタスクの実行</span><span class="sxs-lookup"><span data-stu-id="6d2cd-236">Viewing Information and Performing Tasks Related to Agent Profiles</span></span>  
 <span data-ttu-id="6d2cd-237">レプリケーション モニターには、エージェント プロファイルを管理するためのさまざまなダイアログ ボックスが用意されています。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-237">Replication Monitor includes a number of dialog boxes for managing agent profiles.</span></span> <span data-ttu-id="6d2cd-238">エージェント プロファイルとは、エージェントのパラメーターのセットであり、これらのパラメーターによってエージェントの動作が決定されます。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-238">Agent profiles are sets of parameters for an agent that determine agent behavior.</span></span> <span data-ttu-id="6d2cd-239">詳しくは、「 [レプリケーション エージェント プロファイル](../agents/replication-agent-profiles.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-239">For more information, see [Replication Agent Profiles](../agents/replication-agent-profiles.md).</span></span> <span data-ttu-id="6d2cd-240">これらのダイアログ ボックスには以下のものがあります。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-240">The dialog boxes are:</span></span>  
  
-   <span data-ttu-id="6d2cd-241">**エージェント プロファイル**</span><span class="sxs-lookup"><span data-stu-id="6d2cd-241">**Agent Profiles**</span></span>  
  
     <span data-ttu-id="6d2cd-242">このダイアログ ボックスでは、プロファイルのプロパティの変更、プロファイルの作成と削除、既定のプロファイルの指定、および特定の種類のエージェント (スナップショット エージェントなど) のすべてが使用するプロファイルの指定を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-242">This dialog box allows you to: change the properties of profiles; create and delete profiles; specify a default profile; and specify that all agents of a specific type (such as Snapshot Agents) should use a given profile.</span></span>  
  
-   <span data-ttu-id="6d2cd-243">**\<AgentProfileName>プロパティ**</span><span class="sxs-lookup"><span data-stu-id="6d2cd-243">**\<AgentProfileName> Properties**</span></span>  
  
     <span data-ttu-id="6d2cd-244">このダイアログ ボックスでは、プロファイルのパラメーター設定の表示と編集を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-244">This dialog box allows you to view and edit the parameter settings in a profile.</span></span>  
  
-   <span data-ttu-id="6d2cd-245">**[新しいエージェント プロファイル]**</span><span class="sxs-lookup"><span data-stu-id="6d2cd-245">**New Agent Profile**</span></span>  
  
     <span data-ttu-id="6d2cd-246">このダイアログ ボックスでは新しいプロファイルを作成できます。新しいプロファイルには、既存のプロファイルの値をオプションで指定できます。</span><span class="sxs-lookup"><span data-stu-id="6d2cd-246">This dialog box allows you to create a new profile, optionally including the values from an existing profile.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d2cd-247">参照</span><span class="sxs-lookup"><span data-stu-id="6d2cd-247">See Also</span></span>  
 [<span data-ttu-id="6d2cd-248">レプリケーションの監視</span><span class="sxs-lookup"><span data-stu-id="6d2cd-248">Monitoring Replication</span></span>](../monitoring-replication.md)  
  
  
