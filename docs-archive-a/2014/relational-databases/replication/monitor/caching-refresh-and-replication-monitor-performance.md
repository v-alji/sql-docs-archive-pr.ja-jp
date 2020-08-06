---
title: キャッシュ、更新、およびレプリケーション モニターのパフォーマンス | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- monitoring performance [SQL Server replication], Replication Monitor
- cache [SQL Server], replication
- Replication Monitor, caching
- refreshing data
- Replication Monitor, refreshing
ms.assetid: a2d8b666-ed41-4f86-b2b8-c8e118416ab7
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b04a91e971e65d19c66cc36f142d8c4764b1b05a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634396"
---
# <a name="caching-refresh-and-replication-monitor-performance"></a><span data-ttu-id="98110-102">キャッシュ、更新、およびレプリケーション モニターのパフォーマンス</span><span class="sxs-lookup"><span data-stu-id="98110-102">Caching, Refresh, and Replication Monitor Performance</span></span>
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)]<span data-ttu-id="98110-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]レプリケーションモニターは、運用システム内の多数のコンピューターを効率的に監視するように設計されています。</span><span class="sxs-lookup"><span data-stu-id="98110-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Replication Monitor is designed to efficiently monitor a large number of computers in a production system.</span></span> <span data-ttu-id="98110-104">計算の実行、およびデータの収集のためにレプリケーション モニターによって使用されるクエリは、定期的にキャッシュおよび更新されます。</span><span class="sxs-lookup"><span data-stu-id="98110-104">The queries that Replication Monitor uses to perform calculations and gather data are cached and refreshed on a periodic basis.</span></span> <span data-ttu-id="98110-105">キャッシュによってレプリケーション モニターでさまざまなページを表示する際に必要なクエリと計算の数が削減され、監視のスケーラビリティが向上し、複数のユーザーに対応できるようになります。</span><span class="sxs-lookup"><span data-stu-id="98110-105">Caching reduces the number of queries and calculations required as you view different pages in Replication Monitor and allows monitoring to scale well for multiple users.</span></span>  
  
 <span data-ttu-id="98110-106">キャッシュの更新は、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] エージェント ジョブである **ディストリビューションのレプリケーション モニターの状態更新機能**によって処理されます。</span><span class="sxs-lookup"><span data-stu-id="98110-106">Cache refresh is handled by a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent job, the **Replication monitoring refresher for distribution**.</span></span> <span data-ttu-id="98110-107">このジョブは継続的に実行されますが、キャッシュの更新スケジュールは、前回の更新後の待機時間に基づいて設定されます。</span><span class="sxs-lookup"><span data-stu-id="98110-107">The job runs continuously, but the cache refresh schedule is based on waiting a certain amount time after the previous refresh:</span></span>  
  
-   <span data-ttu-id="98110-108">前回のキャッシュの作成時以降にエージェント履歴が変更された場合、待機時間は、最短の 4 秒、または前回のキャッシュが作成されたときにかかった時間になります。</span><span class="sxs-lookup"><span data-stu-id="98110-108">If there were agent history changes since the cache was last created, the wait time is the minimum of: 4 seconds; or the amount of time taken to create the previous cache.</span></span>  
  
-   <span data-ttu-id="98110-109">前回のキャッシュ作成時以降に (他の種類の変更があったとしても) エージェント履歴が変更されなかった場合、待機時間は、最長の 30 秒、または前回のキャッシュが作成されたときにかかった時間になります。</span><span class="sxs-lookup"><span data-stu-id="98110-109">If there were no agent history changes since the cache was last created (there could have been other changes), the wait time is the maximum of: 30 seconds; or the amount of time taken to create the previous cache.</span></span>  
  
## <a name="refreshing-the-replication-monitor-user-interface"></a><span data-ttu-id="98110-110">レプリケーション モニターのユーザー インターフェイスの更新</span><span class="sxs-lookup"><span data-stu-id="98110-110">Refreshing the Replication Monitor User Interface</span></span>  
 <span data-ttu-id="98110-111">レプリケーション モニターのユーザー インターフェイスは、以下の方法で更新できます。</span><span class="sxs-lookup"><span data-stu-id="98110-111">The Replication Monitor user interface can be refreshed in the following ways:</span></span>  
  
-   <span data-ttu-id="98110-112">レプリケーション モニターのメイン ウィンドウ (すべてのタブが含まれます) は、既定では、5 秒間隔で自動的に更新されます。</span><span class="sxs-lookup"><span data-stu-id="98110-112">The main Replication Monitor window (including all tabs), automatically refreshes by default every five seconds.</span></span> <span data-ttu-id="98110-113">自動更新によって、キャッシュの更新が強制的に行われることはありません。ユーザー インターフェイスには、キャッシュからの最新のバージョンのデータが表示されます。</span><span class="sxs-lookup"><span data-stu-id="98110-113">Automatic refreshes do not force a refresh of the cache; the user interface displays the most recent version of the data from the cache.</span></span> <span data-ttu-id="98110-114">パブリッシャーの設定を編集することによって、パブリッシャーに関連付けられているすべてのウィンドウに使用される更新頻度をカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="98110-114">You can customize the refresh rate used for all windows associated with a Publisher by editing the Publisher settings.</span></span> <span data-ttu-id="98110-115">また、パブリッシャーの自動更新を無効にすることもできます。</span><span class="sxs-lookup"><span data-stu-id="98110-115">You can also disable automatic refreshes for a Publisher.</span></span>  
  
-   <span data-ttu-id="98110-116">レプリケーション モニターから起動される詳細ウィンドウは、既定では自動的に更新されません (ただし、同期されているマージ サブスクリプションに関連付けられているウィンドウは、例外です)。</span><span class="sxs-lookup"><span data-stu-id="98110-116">The detail windows that are launched from Replication Monitor are not automatically refreshed by default, with the exception of windows related to merge subscriptions that are synchronizing.</span></span> <span data-ttu-id="98110-117">詳細ウィンドウが自動的に更新されるように指定すると、レプリケーション モニターのメイン ウィンドウと同じスケジュールで更新されます。</span><span class="sxs-lookup"><span data-stu-id="98110-117">If you specify that detail windows should automatically refresh, they refresh on the same schedule as the main Replication Monitor window.</span></span>  
  
-   <span data-ttu-id="98110-118">すべてのウィンドウは、F5 キーを押すか、またはレプリケーション モニターのツリー内でノードを右クリックし、 **[更新]** をクリックすることによって、手動で更新できます。</span><span class="sxs-lookup"><span data-stu-id="98110-118">All windows can be manually refreshed by pressing F5 or by right-clicking a node in the Replication Monitor tree and clicking **Refresh**.</span></span> <span data-ttu-id="98110-119">手動の更新を行うと、キャッシュは強制的に更新されます。</span><span class="sxs-lookup"><span data-stu-id="98110-119">Manual refreshes force a refresh of the cache.</span></span>  
  
 <span data-ttu-id="98110-120">詳細については、「[レプリケーション モニターのデータの更新](refresh-data-in-replication-monitor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="98110-120">For more information, see [Refresh Data in Replication Monitor](refresh-data-in-replication-monitor.md).</span></span>  
  
## <a name="performance-considerations"></a><span data-ttu-id="98110-121">パフォーマンスに関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="98110-121">Performance Considerations</span></span>  
 <span data-ttu-id="98110-122">レプリケーション モニターは効率的に実行することを目的に設計されていますが、以下の点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="98110-122">Although Replication Monitor is designed to run efficiently, be aware of the following:</span></span>  
  
-   <span data-ttu-id="98110-123">多数のパブリケーションとサブスクリプションがある場合は、ユーザー インターフェイスの自動更新スケジュールの頻度を少なくすることを検討してください。</span><span class="sxs-lookup"><span data-stu-id="98110-123">If you have a large number of publications or subscriptions, consider setting a less frequent automatic refresh schedule for the user interface.</span></span>  
  
-   <span data-ttu-id="98110-124">レプリケーション モニターの複数のインスタンスを同時に実行しないでください。</span><span class="sxs-lookup"><span data-stu-id="98110-124">Avoid concurrently running multiple instances of Replication Monitor.</span></span>  
  
-   <span data-ttu-id="98110-125">多数のディストリビューターを登録しないようにしてください。また、レプリケーション モニターがそれらのすべてに自動的に接続するような設定にしないでください。</span><span class="sxs-lookup"><span data-stu-id="98110-125">Avoid registering a large number of Distributors and setting Replication Monitor to automatically connect to all of them.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98110-126">参照</span><span class="sxs-lookup"><span data-stu-id="98110-126">See Also</span></span>  
 <span data-ttu-id="98110-127">[レプリケーション メンテナンス ジョブの実行 &#40;SQL Server Management Studio&#41;](../../../ssms/sql-server-management-studio-ssms.md) </span><span class="sxs-lookup"><span data-stu-id="98110-127">[Run Replication Maintenance Jobs &#40;SQL Server Management Studio&#41;](../../../ssms/sql-server-management-studio-ssms.md) </span></span>  
 [<span data-ttu-id="98110-128">レプリケーションの監視</span><span class="sxs-lookup"><span data-stu-id="98110-128">Monitoring Replication</span></span>](../monitoring-replication.md)  
  
  
