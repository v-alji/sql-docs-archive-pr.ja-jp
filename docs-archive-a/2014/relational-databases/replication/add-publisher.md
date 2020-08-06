---
title: '[パブリッシャーの追加] ダイアログボックス'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.addpublisher.f1
helpviewer_keywords:
- Add Publisher dialog box
ms.assetid: 4b57e298-655f-42c2-82bc-25cdad94a194
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5c7e607c04aa74db7e5facf13051bf0c47c9dae0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632418"
---
# <a name="sql-server-replication-add-publisher-dialog-box"></a><span data-ttu-id="8a766-102">[パブリッシャーの追加] ダイアログボックス SQL Server レプリケーション</span><span class="sxs-lookup"><span data-stu-id="8a766-102">SQL Server Replication 'Add Publisher' dialog box</span></span> 
  <span data-ttu-id="8a766-103">**[パブリッシャーの追加]** ダイアログ ボックスを使用すると、レプリケーション モニターの左ペインに 1 つまたは複数のパブリッシャーを追加できます。</span><span class="sxs-lookup"><span data-stu-id="8a766-103">The **Add Publisher** dialog box allows you to add to one or more Publishers to the left pane of Replication Monitor.</span></span> <span data-ttu-id="8a766-104">パブリッシャーを追加した後、左ペインでパブリッシャーを選択すると、そのパブリッシャーに関する情報が右ペインに表示されます。</span><span class="sxs-lookup"><span data-stu-id="8a766-104">After adding a Publisher, selecting the Publisher in the left pane shows information on the Publisher in the right pane.</span></span>  
  
## <a name="options"></a><span data-ttu-id="8a766-105">オプション</span><span class="sxs-lookup"><span data-stu-id="8a766-105">Options</span></span>  
 <span data-ttu-id="8a766-106">**追加**</span><span class="sxs-lookup"><span data-stu-id="8a766-106">**Add**</span></span>  
 <span data-ttu-id="8a766-107">クリックすると、追加するパブリッシャーの種類を選択するための **[サーバーへの接続]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="8a766-107">Click to select a type of Publisher to add, which launches the **Connect to Server** dialog box.</span></span> <span data-ttu-id="8a766-108">オプションは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="8a766-108">The options are:</span></span>  
  
-   <span data-ttu-id="8a766-109">**SQL Server パブリッシャーの追加...**</span><span class="sxs-lookup"><span data-stu-id="8a766-109">**Add SQL Server Publisher...**</span></span>  
  
     <span data-ttu-id="8a766-110">**[サーバーへの接続]** ダイアログ ボックスを使用して、パブリッシャーに接続します。</span><span class="sxs-lookup"><span data-stu-id="8a766-110">Connect to the Publisher using the **Connect to Server** dialog box.</span></span>  
  
-   <span data-ttu-id="8a766-111">**Oracle パブリッシャーの追加...**</span><span class="sxs-lookup"><span data-stu-id="8a766-111">**Add Oracle Publisher...**</span></span>  
  
     <span data-ttu-id="8a766-112">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ダイアログ ボックスを使用して、Oracle パブリッシャーに関連付けられている **[サーバーへの接続]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="8a766-112">Connect to the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributor associated with the Oracle Publisher using the **Connect to Server** dialog box.</span></span>  
  
-   <span data-ttu-id="8a766-113">**ディストリビューターを指定し、そのパブリッシャーを追加します...**</span><span class="sxs-lookup"><span data-stu-id="8a766-113">**Specify a Distributor and Add Its Publishers...**</span></span>  
  
     <span data-ttu-id="8a766-114">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [サーバーへの接続] **ダイアログ ボックスを使用して、1 つまたは複数のパブリッシャーに関連付けられている** ディストリビューターに接続します。</span><span class="sxs-lookup"><span data-stu-id="8a766-114">Connect to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributor associated with one or more Publishers using the **Connect to Server** dialog box.</span></span>  
  
 <span data-ttu-id="8a766-115">パブリッシャーまたはディストリビューターに正常に接続されると、各パブリッシャーおよびそのディストリビューターの名前がダイアログ ボックスの上部のグリッドに表示されます。</span><span class="sxs-lookup"><span data-stu-id="8a766-115">After successfully connecting to the Publisher or Distributor, the name of each Publisher and its Distributor are displayed in the grid at the top of the dialog box.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8a766-116">通常はディストリビューターとパブリッシャーを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の同一インスタンス上で実行しますが、ディストリビューターを別のインスタンス上で実行することもできます (この構成をリモート ディストリビューターと呼びます)。</span><span class="sxs-lookup"><span data-stu-id="8a766-116">The Distributor and Publisher often run on the same instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], but the Distributor can run on another instance (this configuration is referred to as a remote Distributor).</span></span>  
  
 <span data-ttu-id="8a766-117">**Remove**</span><span class="sxs-lookup"><span data-stu-id="8a766-117">**Remove**</span></span>  
 <span data-ttu-id="8a766-118">ダイアログ ボックスの上部のグリッドでパブリッシャーを選択し、 **[削除]** をクリックすると、追加対象のパブリッシャーの一覧からパブリッシャーを削除できます。</span><span class="sxs-lookup"><span data-stu-id="8a766-118">Select a Publisher in the grid at the top of the dialog box, and click **Remove** to remove the Publisher from the list of Publishers to be added.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8a766-119">このボタンを使用してレプリケーション モニターに既に表示されているパブリッシャーを削除することはできません。</span><span class="sxs-lookup"><span data-stu-id="8a766-119">This button cannot be used to remove a Publisher that is already displayed in Replication Monitor.</span></span> <span data-ttu-id="8a766-120">既に表示されているパブリッシャーを削除するには、レプリケーション モニターの左ペインでパブリッシャーを右クリックし、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a766-120">To remove a Publisher that is already displayed right-click the Publisher in the left pane of Replication Monitor and click **Remove**.</span></span>  
  
 <span data-ttu-id="8a766-121">**[レプリケーション モニターが起動したときに自動的に接続する]**</span><span class="sxs-lookup"><span data-stu-id="8a766-121">**Connect automatically when Replication Monitor starts**</span></span>  
 <span data-ttu-id="8a766-122">オンにした場合、レプリケーション モニターは自動的にディストリビューターに接続し、ダイアログ ボックスの上部のグリッドで選択されているパブリッシャーの状態情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="8a766-122">Select to allow Replication Monitor to automatically connect to the Distributor and retrieve status information for the Publisher selected in the grid at the top of the dialog box.</span></span> <span data-ttu-id="8a766-123">このチェック ボックスがオフの場合は、レプリケーション モニターを起動した後に手動でパブリッシャーに接続する必要があります。つまり、レプリケーション モニターの左ペインでパブリッシャーを右クリックし、 **[接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a766-123">If this checkbox is cleared, you must manually connect after launching Replication Monitor: right-click the Publisher in the left pane of Replication Monitor, and click **Connect**.</span></span>  
  
 <span data-ttu-id="8a766-124">**[このパブリッシャーとパブリケーションのステータスを自動的に更新する]**</span><span class="sxs-lookup"><span data-stu-id="8a766-124">**Automatically refresh the status of this Publisher and its publications**</span></span>  
 <span data-ttu-id="8a766-125">オンにした場合、レプリケーション モニターは、ダイアログ ボックスの上部のグリッドで選択されているパブリッシャーの状態情報を自動的に更新します。</span><span class="sxs-lookup"><span data-stu-id="8a766-125">Select to allow Replication Monitor to automatically refresh status for the Publisher selected in the grid at the top of the dialog box.</span></span> <span data-ttu-id="8a766-126">このオプションがオンの場合、レプリケーション モニターは、パブリッシャーとそのパブリケーションの状態情報についてディストリビューターをポーリングします。</span><span class="sxs-lookup"><span data-stu-id="8a766-126">If this option is selected, Replication Monitor polls the Distributor for status information on the Publisher and its publications.</span></span> <span data-ttu-id="8a766-127">ポーリング間隔は、 **[更新頻度]** オプションで設定します。</span><span class="sxs-lookup"><span data-stu-id="8a766-127">The polling interval is set by the **Refresh rate** option.</span></span> <span data-ttu-id="8a766-128">レプリケーション モニターでの更新の詳細については、「[キャッシュ、更新、およびレプリケーション モニターのパフォーマンス](monitor/caching-refresh-and-replication-monitor-performance.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8a766-128">For more information on refresh in Replication Monitor, see [Caching, Refresh, and Replication Monitor Performance](monitor/caching-refresh-and-replication-monitor-performance.md).</span></span>  
  
 <span data-ttu-id="8a766-129">**[更新頻度]**</span><span class="sxs-lookup"><span data-stu-id="8a766-129">**Refresh rate**</span></span>  
 <span data-ttu-id="8a766-130">レプリケーション モニターが状態についてディストリビューターをポーリングする間隔 (秒数) を入力します。</span><span class="sxs-lookup"><span data-stu-id="8a766-130">Enter a value (in seconds) to specify how frequently Replication Monitor should poll the Distributor for status.</span></span> <span data-ttu-id="8a766-131">小さい値を指定すると、ポーリングがより短い間隔で行われ、その結果、監視対象のパブリッシャーが数多くある場合にディストリビューター側のパフォーマンスが影響を受ける可能性があります。</span><span class="sxs-lookup"><span data-stu-id="8a766-131">Lower values result in more frequent polling, which can affect performance at the Distributor if you are monitoring a large number of Publishers.</span></span> <span data-ttu-id="8a766-132">システムをテストしながら適切な値を見つけてください。</span><span class="sxs-lookup"><span data-stu-id="8a766-132">It is recommended that you test your system to determine an appropriate value.</span></span> <span data-ttu-id="8a766-133">**[更新頻度]** 設定は、レプリケーション モニターのいずれかの詳細ウィンドウで **[自動更新]** を選択している場合にも使用されます。</span><span class="sxs-lookup"><span data-stu-id="8a766-133">The **Refresh rate** setting is also used if you select **Auto Refresh** in any of the detail windows in Replication Monitor.</span></span>  
  
 <span data-ttu-id="8a766-134">**[このパブリッシャーを次のグループに表示する]**</span><span class="sxs-lookup"><span data-stu-id="8a766-134">**Show this Publisher in the following group**</span></span>  
 <span data-ttu-id="8a766-135">一覧からパブリッシャー グループを選択します。</span><span class="sxs-lookup"><span data-stu-id="8a766-135">Select a Publisher group from the list.</span></span> <span data-ttu-id="8a766-136">パブリッシャーは、左ペインでこのグループの下に表示されます。</span><span class="sxs-lookup"><span data-stu-id="8a766-136">The Publisher is displayed under this group in the left pane.</span></span> <span data-ttu-id="8a766-137">グループはパブリッシャーを整理するもので、レプリケーションの動作には影響を与えません。</span><span class="sxs-lookup"><span data-stu-id="8a766-137">Groups provide a way to organize Publishers and have no effect on how replication functions.</span></span> <span data-ttu-id="8a766-138">グループが定義されていない場合または新しいグループを作成する場合は、 **[新しいグループ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a766-138">If no groups are defined or you want to create a new one, click **New Group**.</span></span>  
  
 <span data-ttu-id="8a766-139">**[新しいグループ]**</span><span class="sxs-lookup"><span data-stu-id="8a766-139">**New Group**</span></span>  
 <span data-ttu-id="8a766-140">クリックすると、新しいパブリッシャー グループを作成できます。</span><span class="sxs-lookup"><span data-stu-id="8a766-140">Click to create a new Publisher group.</span></span> <span data-ttu-id="8a766-141">パブリッシャー グループを利用すると、レプリケーション モニター内でパブリッシャーを容易に整理できます。</span><span class="sxs-lookup"><span data-stu-id="8a766-141">A Publisher group provides a convenient way to organize Publishers within Replication Monitor.</span></span> <span data-ttu-id="8a766-142">グループは、データのレプリケーションや、レプリケーション トポロジ内のサーバー間のリレーションシップには影響を与えません。</span><span class="sxs-lookup"><span data-stu-id="8a766-142">Groups do not affect the replication of data or the relationship among servers in a replication topology.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a766-143">参照</span><span class="sxs-lookup"><span data-stu-id="8a766-143">See Also</span></span>  
 <span data-ttu-id="8a766-144">[レプリケーション モニターの開始](monitor/start-the-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="8a766-144">[Start the Replication Monitor](monitor/start-the-replication-monitor.md) </span></span>  
 [<span data-ttu-id="8a766-145">レプリケーションの監視</span><span class="sxs-lookup"><span data-stu-id="8a766-145">Monitoring Replication</span></span>](monitoring-replication.md)  
  
  
