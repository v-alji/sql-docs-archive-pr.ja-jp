---
title: '[ディストリビューターの設定] ダイアログボックス |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.DistributorSettings.f1
helpviewer_keywords:
- Distributor Settings dialog box
ms.assetid: 8276a521-bdd1-4783-bdb6-7ab43499c0ca
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b864620f155e899868c95f58350f98e2b659c4e4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632374"
---
# <a name="sql-server-replication-distributor-settings-dialog-box"></a><span data-ttu-id="4498c-102">[ディストリビューターの設定] ダイアログボックス SQL Server レプリケーション</span><span class="sxs-lookup"><span data-stu-id="4498c-102">SQL Server Replication 'Distributor Settings' dialog box</span></span>
  <span data-ttu-id="4498c-103">**[ディストリビューターの設定]** ダイアログ ボックスを使用すると、レプリケーション モニターの左ペインに追加されているディストリビューターの設定を変更できます。</span><span class="sxs-lookup"><span data-stu-id="4498c-103">The **Distributor Settings** dialog box enables you to change settings for Distributors that were added to the left pane in Replication Monitor.</span></span>  
  
## <a name="options"></a><span data-ttu-id="4498c-104">オプション</span><span class="sxs-lookup"><span data-stu-id="4498c-104">Options</span></span>  
 <span data-ttu-id="4498c-105">**[レプリケーション モニターが起動したときに自動的に接続する]**</span><span class="sxs-lookup"><span data-stu-id="4498c-105">**Connect automatically when Replication Monitor starts**</span></span>  
 <span data-ttu-id="4498c-106">レプリケーション モニターでディストリビューターに接続して状態情報を取得する場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="4498c-106">Select to let Replication Monitor connect to the Distributor and retrieve status information.</span></span>  
  
 <span data-ttu-id="4498c-107">**Connection**</span><span class="sxs-lookup"><span data-stu-id="4498c-107">**Connection**</span></span>  
 <span data-ttu-id="4498c-108">クリックすると、 **[サーバーへの接続]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4498c-108">Click to display the **Connect to Server** dialog box.</span></span> <span data-ttu-id="4498c-109">このダイアログ ボックスでは、レプリケーション モニターがディストリビューターに接続するときに使用する接続プロパティおよび資格情報を表示および変更できます。</span><span class="sxs-lookup"><span data-stu-id="4498c-109">This enables you to view and change the connection properties and credentials that Replication Monitor uses to connect to the Distributor.</span></span>  
  
 <span data-ttu-id="4498c-110">**[このディストリビューターとパブリケーションのステータスを自動的に更新する]**</span><span class="sxs-lookup"><span data-stu-id="4498c-110">**Automatically refresh the status of this Distributor and its publications**</span></span>  
 <span data-ttu-id="4498c-111">レプリケーション モニターでディストリビューターのステータスを自動的に更新する場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="4498c-111">Select to let Replication Monitor automatically refresh the status for the Distributor.</span></span> <span data-ttu-id="4498c-112">このオプションがオンの場合、レプリケーション モニターは、 **[更新頻度]** オプションにより設定されたポーリング間隔に基づき、状態情報についてディストリビューターをポーリングします。</span><span class="sxs-lookup"><span data-stu-id="4498c-112">If this option is selected, Replication Monitor polls the Distributor for status information based on the polling interval set by the **Refresh rate** option.</span></span> <span data-ttu-id="4498c-113">レプリケーション モニターでの更新については、「 [Caching, Refresh, and Replication Monitor Performance](monitor/caching-refresh-and-replication-monitor-performance.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4498c-113">For more information about refresh in Replication Monitor, see [Caching, Refresh, and Replication Monitor Performance](monitor/caching-refresh-and-replication-monitor-performance.md).</span></span>  
  
 <span data-ttu-id="4498c-114">**[更新頻度]**</span><span class="sxs-lookup"><span data-stu-id="4498c-114">**Refresh rate**</span></span>  
 <span data-ttu-id="4498c-115">レプリケーション モニターが状態についてディストリビューターをポーリングする間隔 (秒数) を入力します。</span><span class="sxs-lookup"><span data-stu-id="4498c-115">Enter a value (in seconds) to specify how frequently Replication Monitor should poll the Distributor for status.</span></span> <span data-ttu-id="4498c-116">入力する値が小さいほど、ポーリングの発生頻度が高くなります。</span><span class="sxs-lookup"><span data-stu-id="4498c-116">Lower values result in more frequent polling.</span></span> <span data-ttu-id="4498c-117">多数のパブリッシャーを監視している場合は、ディストリビューターのパフォーマンスに影響する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="4498c-117">This can affect performance at the Distributor if you are monitoring many Publishers.</span></span> <span data-ttu-id="4498c-118">システムをテストしながら適切な値を見つけてください。</span><span class="sxs-lookup"><span data-stu-id="4498c-118">We recommend that you test your system to determine an appropriate value.</span></span> <span data-ttu-id="4498c-119">**[更新頻度]** 設定は、レプリケーション モニターのいずれかの詳細ウィンドウで **[自動更新]** を選択している場合にも使用されます。</span><span class="sxs-lookup"><span data-stu-id="4498c-119">The **Refresh rate** setting is also used if you select **Auto Refresh** in any of the detail windows in Replication Monitor.</span></span>  
  
 <span data-ttu-id="4498c-120">**[このディストリビューターのすべてのパブリッシャーを次のグループに表示する]**</span><span class="sxs-lookup"><span data-stu-id="4498c-120">**Show all Publishers of this Distributor in the following group**</span></span>  
 <span data-ttu-id="4498c-121">一覧からパブリッシャー グループを選択します。</span><span class="sxs-lookup"><span data-stu-id="4498c-121">Select a Publisher group from the list.</span></span> <span data-ttu-id="4498c-122">パブリッシャーは、左ペインでこのグループの下に表示されます。</span><span class="sxs-lookup"><span data-stu-id="4498c-122">The Publisher is displayed under this group in the left pane.</span></span> <span data-ttu-id="4498c-123">グループはパブリッシャーを整理するもので、レプリケーションの動作には影響を与えません。</span><span class="sxs-lookup"><span data-stu-id="4498c-123">Groups provide a way for you to organize Publishers and do not affect how replication functions.</span></span>  
  
 <span data-ttu-id="4498c-124">**[新しいグループ]**</span><span class="sxs-lookup"><span data-stu-id="4498c-124">**New Group**</span></span>  
 <span data-ttu-id="4498c-125">クリックすると、新しいパブリッシャー グループを作成できます。</span><span class="sxs-lookup"><span data-stu-id="4498c-125">Click to create a new Publisher group.</span></span> <span data-ttu-id="4498c-126">パブリッシャー グループを利用すると、レプリケーション モニター内でパブリッシャーを容易に整理できます。</span><span class="sxs-lookup"><span data-stu-id="4498c-126">A Publisher group provides a way for you to conveniently organize Publishers within Replication Monitor.</span></span> <span data-ttu-id="4498c-127">グループは、データのレプリケーションや、レプリケーション トポロジ内のサーバー間のリレーションシップには影響を与えません。</span><span class="sxs-lookup"><span data-stu-id="4498c-127">Groups do not affect the replication of data or the relationship among servers in a replication topology.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4498c-128">参照</span><span class="sxs-lookup"><span data-stu-id="4498c-128">See Also</span></span>  
 <span data-ttu-id="4498c-129">[レプリケーション モニターの開始](monitor/start-the-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="4498c-129">[Start the Replication Monitor](monitor/start-the-replication-monitor.md) </span></span>  
 [<span data-ttu-id="4498c-130">レプリケーションの監視</span><span class="sxs-lookup"><span data-stu-id="4498c-130">Monitoring Replication</span></span>](monitoring-replication.md)  
  
  
