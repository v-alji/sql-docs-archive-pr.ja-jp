---
title: レプリケーション エージェントを起動および停止する (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- agents [SQL Server replication], stopping
- agents [SQL Server replication], starting
ms.assetid: 97977c4a-8c7c-4a22-9480-69aa812bd1e5
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b40e329e0f04e8a54a2d5a40c30aff418da2cd65
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632406"
---
# <a name="start-and-stop-a-replication-agent-sql-server-management-studio"></a><span data-ttu-id="302cf-102">レプリケーション エージェントを起動および停止する (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="302cf-102">Start and Stop a Replication Agent (SQL Server Management Studio)</span></span>
  <span data-ttu-id="302cf-103">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] の **[ジョブ]** フォルダーと **[レプリケーション]** フォルダーから、およびレプリケーション モニターからエージェントを開始および停止します。</span><span class="sxs-lookup"><span data-stu-id="302cf-103">Start and stop agents from the **Jobs** folder and the **Replication** folder in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] and from Replication Monitor.</span></span> <span data-ttu-id="302cf-104">以下のエージェントおよびジョブの開始と停止を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="302cf-104">Start and stop the following agents and jobs:</span></span>  
  
-   <span data-ttu-id="302cf-105">すべてのパブリケーションで使用されるスナップショット エージェント</span><span class="sxs-lookup"><span data-stu-id="302cf-105">The Snapshot Agent, which is used by all publications.</span></span>  
  
-   <span data-ttu-id="302cf-106">すべてのトランザクション パブリケーションで使用されるログ リーダー エージェント</span><span class="sxs-lookup"><span data-stu-id="302cf-106">The Log Reader Agent, which is used by all transactional publications.</span></span>  
  
-   <span data-ttu-id="302cf-107">キュー更新サブスクリプションに有効なトランザクション パブリケーションで使用されるキュー リーダー エージェント</span><span class="sxs-lookup"><span data-stu-id="302cf-107">The Queue Reader Agent, which is used by transactional publications enabled for queued updating subscriptions.</span></span>  
  
-   <span data-ttu-id="302cf-108">トランザクション パブリケーションやスナップショット パブリケーションに対するサブスクリプションを同期するディストリビューション エージェント</span><span class="sxs-lookup"><span data-stu-id="302cf-108">The Distribution Agent, which synchronizes subscriptions to transactional and snapshot publications.</span></span>  
  
-   <span data-ttu-id="302cf-109">マージ パブリケーションに対するサブスクリプションを同期するマージ エージェント</span><span class="sxs-lookup"><span data-stu-id="302cf-109">The Merge Agent, which synchronizes subscriptions to merge publications.</span></span>  
  
-   <span data-ttu-id="302cf-110">レプリケーション メンテナンス ジョブ。</span><span class="sxs-lookup"><span data-stu-id="302cf-110">Replication maintenance jobs.</span></span>  
  
 <span data-ttu-id="302cf-111">マージ エージェントとディストリビューション エージェントの開始について詳しくは、「[プッシュ サブスクリプションの同期](../synchronize-a-push-subscription.md)」および「[プル サブスクリプションの同期](../synchronize-a-pull-subscription.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="302cf-111">For more information about starting the Merge Agent and the Distribution Agent, see [Synchronize a Push Subscription](../synchronize-a-push-subscription.md) and [Synchronize a Pull Subscription](../synchronize-a-pull-subscription.md).</span></span> <span data-ttu-id="302cf-112">メンテナンス ジョブについて詳しくは、「[レプリケーション メンテナンス ジョブの実行 &#40;SQL Server Management Studio&#41;](../../../ssms/sql-server-management-studio-ssms.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="302cf-112">For more information about maintenance jobs, see [Run Replication Maintenance Jobs &#40;SQL Server Management Studio&#41;](../../../ssms/sql-server-management-studio-ssms.md).</span></span>  
  
 <span data-ttu-id="302cf-113">レプリケーション モニターの起動の詳細については、「[Start the Replication Monitor](../monitor/start-the-replication-monitor.md)」 (レプリケーション モニターの開始) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="302cf-113">For information about starting Replication Monitor, see [Start the Replication Monitor](../monitor/start-the-replication-monitor.md).</span></span>  
  
### <a name="to-start-and-stop-a-snapshot-agent-or-log-reader-agent-from-management-studio"></a><span data-ttu-id="302cf-114">Management Studio からスナップショット エージェントまたはログ リーダー エージェントを開始および停止するには</span><span class="sxs-lookup"><span data-stu-id="302cf-114">To start and stop a Snapshot Agent or Log Reader Agent from Management Studio</span></span>  
  
1.  <span data-ttu-id="302cf-115">[!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]でパブリッシャーに接続して、サーバー ノードと **[レプリケーション]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="302cf-115">Connect to the Publisher in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)], and then expand the server node and the **Replication** folder.</span></span>  
  
2.  <span data-ttu-id="302cf-116">**[ローカル パブリケーション]** フォルダーを展開し、パブリケーションを右クリックします。</span><span class="sxs-lookup"><span data-stu-id="302cf-116">Expand the **Local Publications** folder, and then right-click a publication.</span></span>  
  
3.  <span data-ttu-id="302cf-117">**[スナップショット エージェントの状態の表示]** または **[ログ リーダー エージェントの状態の表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="302cf-117">Click **View Snapshot Agent Status** or **View Log Reader Agent Status**.</span></span>  
  
4.  <span data-ttu-id="302cf-118">**[開始]** または **[停止]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="302cf-118">Click **Start** or **Stop**.</span></span>  
  
### <a name="to-start-and-stop-a-queue-reader-agent-from-management-studio"></a><span data-ttu-id="302cf-119">Management Studio からキュー リーダー エージェントを開始および停止するには</span><span class="sxs-lookup"><span data-stu-id="302cf-119">To start and stop a Queue Reader Agent from Management Studio</span></span>  
  
1.  <span data-ttu-id="302cf-120">[!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]でディストリビューターに接続して、サーバー ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="302cf-120">Connect to the Distributor in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="302cf-121">**[SQL Server エージェント]** フォルダーを展開して、 **[ジョブ]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="302cf-121">Expand the **SQL Server Agent** folder, and then expand the **Jobs** folder.</span></span>  
  
3.  <span data-ttu-id="302cf-122">エージェントのジョブを右クリックして **[ジョブの開始]** または **[ジョブの停止]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="302cf-122">Right-click the job for the agent, and then click **Start Job** or **Stop Job**.</span></span> <span data-ttu-id="302cf-123">キュー リーダー エージェントのジョブの名前は、 **[\<Distributor>].\<integer>** という形式になっています。</span><span class="sxs-lookup"><span data-stu-id="302cf-123">The name of the job for the Queue Reader Agent is in the form **[\<Distributor>].\<integer>**.</span></span>  
  
### <a name="to-start-and-stop-a-snapshot-agent-log-reader-agent-or-queue-reader-agent-from-replication-monitor"></a><span data-ttu-id="302cf-124">レプリケーション モニターからスナップショット エージェント、ログ リーダー エージェント、またはキュー リーダー エージェントを開始および停止するには</span><span class="sxs-lookup"><span data-stu-id="302cf-124">To start and stop a Snapshot Agent, Log Reader Agent, or Queue Reader Agent from Replication Monitor</span></span>  
  
1.  <span data-ttu-id="302cf-125">左ペインでパブリッシャー グループを展開し、パブリッシャーを展開して、パブリケーションをクリックします。</span><span class="sxs-lookup"><span data-stu-id="302cf-125">Expand a Publisher group in the left pane, expand a Publisher, and then click a publication.</span></span>  
  
2.  <span data-ttu-id="302cf-126">**[エージェント]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="302cf-126">Click the **Agents** tab.</span></span>  
  
3.  <span data-ttu-id="302cf-127">エージェントを右クリックして **[エージェントの開始]** または **[エージェントの停止]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="302cf-127">Right-click an agent, and then click **Start Agent** or **Stop Agent**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="302cf-128">参照</span><span class="sxs-lookup"><span data-stu-id="302cf-128">See Also</span></span>  
 <span data-ttu-id="302cf-129">[レプリケーションの監視](../monitoring-replication.md) </span><span class="sxs-lookup"><span data-stu-id="302cf-129">[Monitoring Replication](../monitoring-replication.md) </span></span>  
 <span data-ttu-id="302cf-130">[レプリケーション エージェント実行可能ファイルの概念](../concepts/replication-agent-executables-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="302cf-130">[Replication Agent Executables Concepts](../concepts/replication-agent-executables-concepts.md) </span></span>  
 [<span data-ttu-id="302cf-131">レプリケーション エージェントの概要</span><span class="sxs-lookup"><span data-stu-id="302cf-131">Replication Agents Overview</span></span>](replication-agents-overview.md)  
  
  
