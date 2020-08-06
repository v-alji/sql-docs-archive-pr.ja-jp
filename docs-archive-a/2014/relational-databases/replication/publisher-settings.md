---
title: SQL Server レプリケーションの [パブリッシャーの設定] ダイアログ ボックス | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.publishersettings.f1
helpviewer_keywords:
- Publisher Settings dialog box
ms.assetid: 4fb70427-082d-4179-82a1-34b235accc43
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3a9a5ca5b0d7bfae895287708af159f3316e4474
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740810"
---
# <a name="sql-server-replication-publisher-settings-dialog-box"></a><span data-ttu-id="f2553-102">SQL Server レプリケーションの [パブリッシャーの設定] ダイアログ ボックス</span><span class="sxs-lookup"><span data-stu-id="f2553-102">SQL Server Replication 'Publisher Settings' dialog box</span></span>
  <span data-ttu-id="f2553-103">**[パブリッシャーの設定]** ダイアログ ボックスを使用すると、レプリケーション モニターの左ペインに追加されているパブリッシャーの設定を変更できます。</span><span class="sxs-lookup"><span data-stu-id="f2553-103">The **Publisher Settings** dialog box allows you to change settings for Publishers that have been added to the left pane in Replication Monitor.</span></span>  
  
## <a name="options"></a><span data-ttu-id="f2553-104">オプション</span><span class="sxs-lookup"><span data-stu-id="f2553-104">Options</span></span>  
 <span data-ttu-id="f2553-105">**[パブリッシャー接続]**</span><span class="sxs-lookup"><span data-stu-id="f2553-105">**Publisher Connection**</span></span>  
 <span data-ttu-id="f2553-106">クリックすると、 **[サーバーへの接続]** ダイアログ ボックスが表示されます。このダイアログ ボックスでは、レプリケーション モニターがパブリッシャーに接続するときに使用する接続プロパティおよび資格情報を表示および変更できます。</span><span class="sxs-lookup"><span data-stu-id="f2553-106">Click to launch the **Connect to Server** dialog box, which allows you to view and change the connection properties and credentials Replication Monitor uses to connect to a Publisher.</span></span>  
  
 <span data-ttu-id="f2553-107">**[ディストリビューター接続]**</span><span class="sxs-lookup"><span data-stu-id="f2553-107">**Distributor Connection**</span></span>  
 <span data-ttu-id="f2553-108">パブリッシャーがリモート ディストリビューターを使用する場合にのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="f2553-108">Displayed only if the Publisher uses a remote Distributor.</span></span> <span data-ttu-id="f2553-109">クリックすると、 **[サーバーへの接続]** ダイアログ ボックスが表示されます。このダイアログ ボックスでは、レプリケーション モニターがリモート ディストリビューターに接続するときに使用する接続プロパティおよび資格情報を表示および変更できます。</span><span class="sxs-lookup"><span data-stu-id="f2553-109">Click to launch the **Connect to Server** dialog box, which allows you to view and change the connection properties and credentials Replication Monitor uses to connect to the remote Distributor.</span></span>  
  
 <span data-ttu-id="f2553-110">**[レプリケーション モニターが起動したときに自動的に接続する]**</span><span class="sxs-lookup"><span data-stu-id="f2553-110">**Connect automatically when Replication Monitor starts**</span></span>  
 <span data-ttu-id="f2553-111">オンにした場合、レプリケーション モニターは自動的にディストリビューターに接続し、ダイアログ ボックスの上部のグリッドで選択されているパブリッシャーの状態情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="f2553-111">Select to allow Replication Monitor to automatically connect to the Distributor and retrieve status information for the Publisher selected in the grid at the top of the dialog box.</span></span> <span data-ttu-id="f2553-112">このチェック ボックスがオフの場合は、レプリケーション モニターを起動した後に手動でパブリッシャーに接続する必要があります。つまり、レプリケーション モニターの左ペインでパブリッシャーを右クリックし、 **[接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f2553-112">If this checkbox is cleared, you must manually connect after launching Replication Monitor: right-click the Publisher in the left pane of Replication Monitor, and click **Connect**.</span></span>  
  
 <span data-ttu-id="f2553-113">**[このパブリッシャーとパブリケーションのステータスを自動的に更新する]**</span><span class="sxs-lookup"><span data-stu-id="f2553-113">**Automatically refresh the status of this Publisher and its publications**</span></span>  
 <span data-ttu-id="f2553-114">オンにした場合、レプリケーション モニターは、ダイアログ ボックスの上部のグリッドで選択されているパブリッシャーの状態情報を自動的に更新します。</span><span class="sxs-lookup"><span data-stu-id="f2553-114">Select to allow Replication Monitor to automatically refresh status for the Publisher selected in the grid at the top of the dialog box.</span></span> <span data-ttu-id="f2553-115">このオプションがオンの場合、レプリケーション モニターは、パブリッシャーとそのパブリケーションの状態情報についてディストリビューターをポーリングします。</span><span class="sxs-lookup"><span data-stu-id="f2553-115">If this option is selected, Replication Monitor polls the Distributor for status information on the Publisher and its publications.</span></span> <span data-ttu-id="f2553-116">ポーリング間隔は、 **[更新頻度]** オプションで設定します。</span><span class="sxs-lookup"><span data-stu-id="f2553-116">The polling interval is set by the **Refresh rate** option.</span></span> <span data-ttu-id="f2553-117">レプリケーション モニターでの更新の詳細については、「[キャッシュ、更新、およびレプリケーション モニターのパフォーマンス](monitor/caching-refresh-and-replication-monitor-performance.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f2553-117">For more information on refresh in Replication Monitor, see [Caching, Refresh, and Replication Monitor Performance](monitor/caching-refresh-and-replication-monitor-performance.md).</span></span>  
  
 <span data-ttu-id="f2553-118">**[更新頻度]**</span><span class="sxs-lookup"><span data-stu-id="f2553-118">**Refresh rate**</span></span>  
 <span data-ttu-id="f2553-119">レプリケーション モニターが状態についてディストリビューターをポーリングする間隔 (秒数) を入力します。</span><span class="sxs-lookup"><span data-stu-id="f2553-119">Enter a value (in seconds) to specify how frequently Replication Monitor should poll the Distributor for status.</span></span> <span data-ttu-id="f2553-120">小さい値を指定すると、ポーリングがより短い間隔で行われ、その結果、監視対象のパブリッシャーが数多くある場合にディストリビューター側のパフォーマンスが影響を受ける可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f2553-120">Lower values result in more frequent polling, which can affect performance at the Distributor if you are monitoring a large number of Publishers.</span></span> <span data-ttu-id="f2553-121">システムをテストしながら適切な値を見つけてください。</span><span class="sxs-lookup"><span data-stu-id="f2553-121">It is recommended that you test your system to determine an appropriate value.</span></span> <span data-ttu-id="f2553-122">**[更新頻度]** 設定は、レプリケーション モニターのいずれかの詳細ウィンドウで **[自動更新]** を選択している場合にも使用されます。</span><span class="sxs-lookup"><span data-stu-id="f2553-122">The **Refresh rate** setting is also used if you select **Auto Refresh** in any of the detail windows in Replication Monitor.</span></span>  
  
 <span data-ttu-id="f2553-123">**[このパブリッシャーを次のグループに表示する]**</span><span class="sxs-lookup"><span data-stu-id="f2553-123">**Show this Publisher in the following group**</span></span>  
 <span data-ttu-id="f2553-124">一覧からパブリッシャー グループを選択します。</span><span class="sxs-lookup"><span data-stu-id="f2553-124">Select a Publisher group from the list.</span></span> <span data-ttu-id="f2553-125">パブリッシャーは、左ペインでこのグループの下に表示されます。</span><span class="sxs-lookup"><span data-stu-id="f2553-125">The Publisher is displayed under this group in the left pane.</span></span> <span data-ttu-id="f2553-126">グループはパブリッシャーを整理するもので、レプリケーションの動作には影響を与えません。</span><span class="sxs-lookup"><span data-stu-id="f2553-126">Groups provide a way to organize Publishers and have no effect on how replication functions.</span></span>  
  
 <span data-ttu-id="f2553-127">**[新しいグループ]**</span><span class="sxs-lookup"><span data-stu-id="f2553-127">**New Group**</span></span>  
 <span data-ttu-id="f2553-128">クリックすると、新しいパブリッシャー グループを作成できます。</span><span class="sxs-lookup"><span data-stu-id="f2553-128">Click to create a new Publisher group.</span></span> <span data-ttu-id="f2553-129">パブリッシャー グループを利用すると、レプリケーション モニター内でパブリッシャーを容易に整理できます。</span><span class="sxs-lookup"><span data-stu-id="f2553-129">A Publisher group provides a convenient way to organize Publishers within Replication Monitor.</span></span> <span data-ttu-id="f2553-130">グループは、データのレプリケーションや、レプリケーション トポロジ内のサーバー間のリレーションシップには影響を与えません。</span><span class="sxs-lookup"><span data-stu-id="f2553-130">Groups do not affect the replication of data or the relationship among servers in a replication topology.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2553-131">参照</span><span class="sxs-lookup"><span data-stu-id="f2553-131">See Also</span></span>  
 <span data-ttu-id="f2553-132">[レプリケーション モニターの開始](monitor/start-the-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="f2553-132">[Start the Replication Monitor](monitor/start-the-replication-monitor.md) </span></span>  
 [<span data-ttu-id="f2553-133">レプリケーションの監視</span><span class="sxs-lookup"><span data-stu-id="f2553-133">Monitoring Replication</span></span>](monitoring-replication.md)  
  
  
