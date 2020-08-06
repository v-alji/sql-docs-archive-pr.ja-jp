---
title: レプリケーションの監視 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- monitoring performance [SQL Server replication], about monitoring replication
- transactional replication, monitoring
- monitoring [SQL Server replication]
- merge replication monitoring [SQL Server replication]
- snapshot replication [SQL Server], monitoring
- replication [SQL Server], monitoring
- administering replication, monitoring
ms.assetid: f182f43a-6af8-45bc-a708-08d5f7a6984a
author: rothja
ms.author: jroth
ms.openlocfilehash: df2760e4ce04c95f38ceb9dfe9fa9f79c4c467f3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718003"
---
# <a name="monitoring-replication"></a><span data-ttu-id="ab403-102">監視 (レプリケーション)</span><span class="sxs-lookup"><span data-stu-id="ab403-102">Monitoring (Replication)</span></span>
  <span data-ttu-id="ab403-103">レプリケーション トポロジの監視は、レプリケーションの配置における重要な側面です。</span><span class="sxs-lookup"><span data-stu-id="ab403-103">Monitoring a replication topology is an important aspect of deploying replication.</span></span> <span data-ttu-id="ab403-104">レプリケーション処理は分散環境で行われるため、レプリケーションに関連するすべてのコンピューターについてその利用状況と状態を追跡することが不可欠です。</span><span class="sxs-lookup"><span data-stu-id="ab403-104">Because replication activity is distributed, it is essential to track activity and status across all computers involved in replication.</span></span> <span data-ttu-id="ab403-105">レプリケーションの監視には以下のツールを使用できます。</span><span class="sxs-lookup"><span data-stu-id="ab403-105">The following tools can be used to monitor replication:</span></span>  
  
-   [!INCLUDE[msCoName](../../includes/msCoName-md.md)]<span data-ttu-id="ab403-106">[!INCLUDE[ssNoVersion](../../includes/ssNoVersion-md.md)]レプリケーションモニター</span><span class="sxs-lookup"><span data-stu-id="ab403-106">[!INCLUDE[ssNoVersion](../../includes/ssNoVersion-md.md)] Replication Monitor</span></span>  
  
     <span data-ttu-id="ab403-107">レプリケーションの監視を行うにあたり、最も重要なツールがレプリケーション モニターです。すべてのレプリケーションの利用状況がパブリッシャー関連のビューで表示されます。</span><span class="sxs-lookup"><span data-stu-id="ab403-107">Replication Monitor is the most important tool for monitoring replication, presenting a Publisher-focused view of all replication activity.</span></span> <span data-ttu-id="ab403-108">詳細については、「[レプリケーションモニターを使用したパフォーマンスの監視](monitor/monitor-performance-with-replication-monitor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ab403-108">For more information, see [Monitor performance with Replication Monitor](monitor/monitor-performance-with-replication-monitor.md).</span></span>  
  
-   [!INCLUDE[msCoName](../../includes/msCoName-md.md)] <span data-ttu-id="ab403-109">[!INCLUDE[ssManStudioFull](../../includes/ssManStudioFull-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab403-109">[!INCLUDE[ssManStudioFull](../../includes/ssManStudioFull-md.md)]</span></span>  
  
     [!INCLUDE[ssManStudio](../../includes/ssManStudio-md.md)] <span data-ttu-id="ab403-110">を使用して、レプリケーション モニターにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="ab403-110">provides access to Replication Monitor.</span></span> <span data-ttu-id="ab403-111">また、次に示すエージェントによってログに記録された現在の状態や最後のメッセージを表示したり、各エージェントを開始および停止したりすることができます。ログ リーダー エージェント、スナップショット エージェント、マージ エージェント、ディストリビューション エージェント。</span><span class="sxs-lookup"><span data-stu-id="ab403-111">It also allows you to view the current status and last message logged by the following agents and allows you start and stop each agent: Log Reader Agent, Snapshot Agent, Merge Agent, and Distribution Agent.</span></span> <span data-ttu-id="ab403-112">詳細については、「 [Monitor Replication Agents](monitor/monitor-replication-agents.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ab403-112">For more information, see [Monitor Replication Agents](monitor/monitor-replication-agents.md).</span></span>  
  
-   [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="ab403-113">およびレプリケーション管理オブジェクト (RMO)</span><span class="sxs-lookup"><span data-stu-id="ab403-113">and Replication Management Objects (RMO)</span></span>  
  
     <span data-ttu-id="ab403-114">どちらのインターフェイスでも、ディストリビューターからすべての種類のレプリケーションを監視できます。</span><span class="sxs-lookup"><span data-stu-id="ab403-114">Both interfaces allow you to monitor all types of replication from the Distributor.</span></span> <span data-ttu-id="ab403-115">マージ レプリケーションでは、サブスクライバーからレプリケーションを監視することもできます。</span><span class="sxs-lookup"><span data-stu-id="ab403-115">Merge replication also provides the ability to monitor replication from the Subscriber.</span></span>  
  
-   <span data-ttu-id="ab403-116">レプリケーション エージェント イベントに対する警告</span><span class="sxs-lookup"><span data-stu-id="ab403-116">Alerts for replication agent events</span></span>  
  
     <span data-ttu-id="ab403-117">レプリケーションには、レプリケーション エージェント イベントに対する定義済みの警告が多数用意されています。また、必要に応じて追加の警告を作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="ab403-117">Replication provides a number of predefined alerts for replication agent events, and you can create additional alerts if necessary.</span></span> <span data-ttu-id="ab403-118">警告を使用して、イベントに対する自動応答のトリガーを起動したり、管理者に通知することができます。</span><span class="sxs-lookup"><span data-stu-id="ab403-118">Alerts can be used to trigger an automated response to an event and/or notify an administrator.</span></span> <span data-ttu-id="ab403-119">詳細については、「[レプリケーション エージェント イベントに対する警告の使用](agents/use-alerts-for-replication-agent-events.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ab403-119">For more information, see [Use Alerts for Replication Agent Events](agents/use-alerts-for-replication-agent-events.md).</span></span>  
  
-   <span data-ttu-id="ab403-120">システム モニター</span><span class="sxs-lookup"><span data-stu-id="ab403-120">System Monitor</span></span>  
  
     <span data-ttu-id="ab403-121">システム モニターには、レプリケーションに関するさまざまなカウンターが表示されるので、パフォーマンスを監視する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="ab403-121">System Monitor can be useful for monitoring performance, providing a number of counters for replication.</span></span> <span data-ttu-id="ab403-122">詳細については、「 [Monitoring Replication with System Monitor](monitor/monitoring-replication-with-system-monitor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ab403-122">For more information, see [Monitoring Replication with System Monitor](monitor/monitoring-replication-with-system-monitor.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab403-123">参照</span><span class="sxs-lookup"><span data-stu-id="ab403-123">See Also</span></span>  
 <span data-ttu-id="ab403-124">[レプリケーション管理に関する FAQ](administration/frequently-asked-questions-for-replication-administrators.md) </span><span class="sxs-lookup"><span data-stu-id="ab403-124">[Replication Administration FAQ](administration/frequently-asked-questions-for-replication-administrators.md) </span></span>  
 [<span data-ttu-id="ab403-125">Best Practices for Replication Administration</span><span class="sxs-lookup"><span data-stu-id="ab403-125">Best Practices for Replication Administration</span></span>](administration/best-practices-for-replication-administration.md)   

  
  
