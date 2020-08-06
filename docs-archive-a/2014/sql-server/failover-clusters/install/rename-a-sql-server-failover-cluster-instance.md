---
title: SQL Server のフェールオーバー クラスター インスタンスの名前変更 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- clusters [SQL Server], virtual servers
- renaming virtual servers
- virtual servers [SQL Server], failover clustering
- failover clustering [SQL Server], virtual servers
ms.assetid: 2a49d417-25fb-4760-8ae5-5871bfb1e6f3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 397e36931e446861db0fcb899cad30e8c7b1ffc2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640552"
---
# <a name="rename-a-sql-server-failover-cluster-instance"></a><span data-ttu-id="a5efe-102">SQL Server のフェールオーバー クラスター インスタンスの名前変更</span><span class="sxs-lookup"><span data-stu-id="a5efe-102">Rename a SQL Server Failover Cluster Instance</span></span>
  <span data-ttu-id="a5efe-103">フェールオーバー クラスターに含まれる [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスの場合、仮想サーバーの名前を変更する手順は、スタンドアロン インスタンスでの手順とは異なります。</span><span class="sxs-lookup"><span data-stu-id="a5efe-103">When a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance is part of a failover cluster, the process of renaming the virtual server differs from that of renaming a stand-alone instance.</span></span> <span data-ttu-id="a5efe-104">詳細については、 [SQL Server のスタンドアロン インスタンスをホストするコンピューターの名前変更](../../../database-engine/install-windows/rename-a-computer-that-hosts-a-stand-alone-instance-of-sql-server.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a5efe-104">For more information, see [Rename a Computer that Hosts a Stand-Alone Instance of SQL Server](../../../database-engine/install-windows/rename-a-computer-that-hosts-a-stand-alone-instance-of-sql-server.md).</span></span>  
  
 <span data-ttu-id="a5efe-105">仮想サーバーの名前は、常に SQL ネットワーク名 (SQL 仮想サーバー ネットワーク名) と同じになります。</span><span class="sxs-lookup"><span data-stu-id="a5efe-105">The name of the virtual server is always the same as the name of the SQL Network Name (the SQL Virtual Server Network Name).</span></span> <span data-ttu-id="a5efe-106">仮想サーバー名は変更できますが、インスタンス名は変更できません。</span><span class="sxs-lookup"><span data-stu-id="a5efe-106">Although you can change the name of the virtual server, you cannot change the instance name.</span></span> <span data-ttu-id="a5efe-107">たとえば、VS1\instance1 という仮想サーバー名を SQL35\instance1 などの別の名前に変更することはできますが、名前のインスタンスの部分 instance1 は変更されません。</span><span class="sxs-lookup"><span data-stu-id="a5efe-107">For example, you can change a virtual server named VS1\instance1 to some other name, such as SQL35\instance1, but the instance portion of the name, instance1, will remain unchanged.</span></span>  
  
 <span data-ttu-id="a5efe-108">名前の変更処理を開始する前に、次の項目を確認します。</span><span class="sxs-lookup"><span data-stu-id="a5efe-108">Before you begin the renaming process, review the items below.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="a5efe-109">では、レプリケーションにログ配布が使用されている場合を除いて、レプリケーション対象サーバーの名前は変更できません。</span><span class="sxs-lookup"><span data-stu-id="a5efe-109">does not support renaming servers involved in replication, except in the case of using log shipping with replication.</span></span> <span data-ttu-id="a5efe-110">プライマリ サーバーが完全に存在しなくなった場合は、ログ配布対象のセカンダリ サーバーの名前を変更することができます。</span><span class="sxs-lookup"><span data-stu-id="a5efe-110">The secondary server in log shipping can be renamed if the primary server is permanently lost.</span></span> <span data-ttu-id="a5efe-111">詳細については、[ログ配布とレプリケーション &#40;SQL Server&#41;](../../../database-engine/log-shipping/log-shipping-and-replication-sql-server.md) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a5efe-111">For more information, see [Log Shipping and Replication &#40;SQL Server&#41;](../../../database-engine/log-shipping/log-shipping-and-replication-sql-server.md).</span></span>  
  
-   <span data-ttu-id="a5efe-112">データベース ミラーリングを使用するよう構成されている仮想サーバーの名前を変更する場合は、名前の変更を行う前にデータベース ミラーリングを無効にし、名前の変更後に新しい仮想サーバー名でデータベース ミラーリングを再確立する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a5efe-112">When renaming a virtual server that is configured to use database mirroring, you must turn off database mirroring before the renaming operation, and then re-establish database mirroring with the new virtual server name.</span></span> <span data-ttu-id="a5efe-113">データベース ミラーリングのメタデータは、新しい仮想サーバー名に、自動的には更新されません。</span><span class="sxs-lookup"><span data-stu-id="a5efe-113">Metadata for database mirroring will not be updated automatically to reflect the new virtual server name.</span></span>  
  
### <a name="to-rename-a-virtual-server"></a><span data-ttu-id="a5efe-114">仮想サーバーの名前を変更するには</span><span class="sxs-lookup"><span data-stu-id="a5efe-114">To rename a virtual server</span></span>  
  
1.  <span data-ttu-id="a5efe-115">クラスター アドミニストレーターを使用して、SQL ネットワーク名を新しい名前に変更します。</span><span class="sxs-lookup"><span data-stu-id="a5efe-115">Using Cluster Administrator, change the SQL Network Name to the new name.</span></span>  
  
2.  <span data-ttu-id="a5efe-116">ネットワーク名リソースをオフラインにします。</span><span class="sxs-lookup"><span data-stu-id="a5efe-116">Take the network name resource offline.</span></span> <span data-ttu-id="a5efe-117">これにより、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] リソースや、他の依存リソースもオフラインになります。</span><span class="sxs-lookup"><span data-stu-id="a5efe-117">This takes the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] resource and other dependent resources offline as well.</span></span>  
  
3.  <span data-ttu-id="a5efe-118">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] リソースをオンラインに戻します。</span><span class="sxs-lookup"><span data-stu-id="a5efe-118">Bring the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] resource back online.</span></span>  
  
## <a name="verify-the-renaming-operation"></a><span data-ttu-id="a5efe-119">名前の変更操作の確認</span><span class="sxs-lookup"><span data-stu-id="a5efe-119">Verify the Renaming Operation</span></span>  
 <span data-ttu-id="a5efe-120">仮想サーバーの名前を変更したら、このサーバーの古い名前を使用している接続は、新しい名前を使用して接続するように変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a5efe-120">After a virtual server has been renamed, any connections that used the old name must now connect using the new name.</span></span>  
  
 <span data-ttu-id="a5efe-121">名前の変更が完了していることを確認するには、`@@servername` または `sys.servers` のいずれかを使用して情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="a5efe-121">To verify that the renaming operation has completed, select information from either `@@servername` or `sys.servers`.</span></span> <span data-ttu-id="a5efe-122">`@@servername` 関数は新しい仮想サーバー名を返し、`sys.servers` テーブルには新しい仮想サーバー名が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a5efe-122">The `@@servername` function will return the new virtual server name, and the `sys.servers` table will show the new virtual server name.</span></span> <span data-ttu-id="a5efe-123">また、フェールオーバー処理が新しい名前を使って正常に機能していることを確認するには、他のノードに対する [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] リソースのフェールオーバーが発生するように試行します。</span><span class="sxs-lookup"><span data-stu-id="a5efe-123">To verify that the failover process is working correctly with the new name, the user should also try to fail the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] resource over to the other nodes.</span></span>  
  
 <span data-ttu-id="a5efe-124">クラスター内のノードからの接続については、新しい名前を直ちに使用できます。</span><span class="sxs-lookup"><span data-stu-id="a5efe-124">For connections from any node in the cluster, the new name can be used almost immediately.</span></span> <span data-ttu-id="a5efe-125">ただし、クライアント コンピューターから新しい名前を使用して接続する場合は、クライアント コンピューターが新しい名前を認識できるようにならないと、新しい名前を使用してサーバーに接続することはできません。</span><span class="sxs-lookup"><span data-stu-id="a5efe-125">However, for connections using the new name from a client computer, the new name cannot be used to connect to the server until the new name is visible to that client computer.</span></span> <span data-ttu-id="a5efe-126">新しい名前がネットワーク全体に伝達されるのに必要な時間は、ネットワークの構成により異なり、数秒で済むことも、3 ～ 5 分かかることもあります。ネットワークから古い仮想サーバー名が消去されるには、さらに時間がかかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="a5efe-126">The length of time required for the new name to be propagated across a network can be a few seconds, or as long as 3 to 5 minutes, depending on the network configuration; additional time may be required before the old virtual server name is no longer visible on the network.</span></span>  
  
 <span data-ttu-id="a5efe-127">仮想サーバー名の変更をネットワークに伝達する時間を最小限に抑えるには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="a5efe-127">To minimize network propagation delay of a virtual server renaming operation, use the following steps:</span></span>  
  
#### <a name="to-minimize-network-propagation-delay"></a><span data-ttu-id="a5efe-128">ネットワークの伝達の遅延を最小限に抑えるには</span><span class="sxs-lookup"><span data-stu-id="a5efe-128">To minimize network propagation delay</span></span>  
  
1.  <span data-ttu-id="a5efe-129">サーバー ノードでコマンド プロンプトから次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="a5efe-129">Issue the following commands from a command prompt on the server node:</span></span>  
  
    ```  
    ipconfig /flushdns  
    ipconfig /registerdns  
    nbtstat -RR  
    ```  
  
## <a name="additional-considerations-after-the-renaming-operation"></a><span data-ttu-id="a5efe-130">名前変更操作後のその他の考慮事項</span><span class="sxs-lookup"><span data-stu-id="a5efe-130">Additional considerations after the Renaming Operation</span></span>  
 <span data-ttu-id="a5efe-131">フェールオーバー クラスターのネットワーク名を変更した後は、以下の点を検証および実行して、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] エージェントと [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]のすべてのシナリオを有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a5efe-131">After we rename the network name of failover cluster we need to verify and perform the following instructions to enable all scenarios in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent and [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="a5efe-132">\*\* [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] :\*\* [!INCLUDE[ssASCurrent](../../../includes/ssascurrent-md.md)] Windows クラスターアドミニストレーターツールを使用してフェールオーバークラスターインスタンスのネットワーク名を変更した後、今後のアップグレードまたはアンインストール操作が失敗する場合があります。</span><span class="sxs-lookup"><span data-stu-id="a5efe-132">**[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]:** After you change the network name of a [!INCLUDE[ssASCurrent](../../../includes/ssascurrent-md.md)] failover cluster instance using Windows Cluster Administrator tool, the future upgrade or uninstall operation might fail.</span></span> <span data-ttu-id="a5efe-133">この問題を解決するには、[この](https://go.microsoft.com/fwlink/?LinkId=244002)記事の「解決方法」の手順に従って、 **ClusterName**レジストリエントリを更新します (「」を参照して https://go.microsoft.com/fwlink/?LinkId=244002) ください。</span><span class="sxs-lookup"><span data-stu-id="a5efe-133">To resolve this issue update the **ClusterName** registry entry following the instructions in the resolution section of [this](https://go.microsoft.com/fwlink/?LinkId=244002) (https://go.microsoft.com/fwlink/?LinkId=244002).</span></span>  
  
 <span data-ttu-id="a5efe-134">\*\* [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] エージェントサービス:\*\* 次の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 追加アクションを確認して実行します。エージェントサービス:</span><span class="sxs-lookup"><span data-stu-id="a5efe-134">**[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent Service:** Verify and perform the below additional actions for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent Service:</span></span>  
  
-   <span data-ttu-id="a5efe-135">SQL エージェントがイベントの転送用に構成されている場合は、レジストリ設定を修正します。</span><span class="sxs-lookup"><span data-stu-id="a5efe-135">Fix the registry settings if SQL Agent is configured for event forwarding.</span></span> <span data-ttu-id="a5efe-136">詳細については、[イベントの転送先サーバーの指定 &#40;SQL Server Management Studio&#41;](../../../ssms/agent/designate-an-events-forwarding-server-sql-server-management-studio.md) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a5efe-136">For more information, see [Designate an Events Forwarding Server &#40;SQL Server Management Studio&#41;](../../../ssms/agent/designate-an-events-forwarding-server-sql-server-management-studio.md).</span></span>  
  
-   <span data-ttu-id="a5efe-137">コンピューター/クラスターのネットワーク名が変更されている場合は、マスター サーバー (MSX) とターゲット サーバー (TSX) のインスタンス名を修正します。</span><span class="sxs-lookup"><span data-stu-id="a5efe-137">Fix the master server (MSX) and target servers (TSX) instance names when machines / cluster network name is renamed.</span></span> <span data-ttu-id="a5efe-138">詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="a5efe-138">For more information, see the following topics:</span></span>  
  
    -   [<span data-ttu-id="a5efe-139">マスター サーバーからの複数のターゲット サーバーの参加の解除</span><span class="sxs-lookup"><span data-stu-id="a5efe-139">Defect Multiple Target Servers from a Master Server</span></span>](../../../ssms/agent/defect-multiple-target-servers-from-a-master-server.md)  
  
    -   [<span data-ttu-id="a5efe-140">マルチサーバー環境の作成</span><span class="sxs-lookup"><span data-stu-id="a5efe-140">Create a Multiserver Environment</span></span>](../../../ssms/agent/create-a-multiserver-environment.md)  
  
-   <span data-ttu-id="a5efe-141">ログ配布を再構成して、更新されたサーバー名を使ってログがバックアップおよび復元されるようにします。</span><span class="sxs-lookup"><span data-stu-id="a5efe-141">Reconfigure the Log Shipping so that updated server name is used to backup and restore logs.</span></span> <span data-ttu-id="a5efe-142">詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="a5efe-142">For more information, see the following topics:</span></span>  
  
    -   [<span data-ttu-id="a5efe-143">ログ配布の構成 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a5efe-143">Configure Log Shipping &#40;SQL Server&#41;</span></span>](../../../database-engine/log-shipping/configure-log-shipping-sql-server.md)  
  
    -   [<span data-ttu-id="a5efe-144">ログ配布の削除 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a5efe-144">Remove Log Shipping &#40;SQL Server&#41;</span></span>](../../../database-engine/log-shipping/remove-log-shipping-sql-server.md)  
  
-   <span data-ttu-id="a5efe-145">サーバー名を使用するジョブ ステップを更新します。</span><span class="sxs-lookup"><span data-stu-id="a5efe-145">Update the Jobsteps that depend on server name.</span></span> <span data-ttu-id="a5efe-146">詳細については、 [ジョブ ステップの管理](../../../ssms/agent/manage-job-steps.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a5efe-146">For more information, see [Manage Job Steps](../../../ssms/agent/manage-job-steps.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5efe-147">参照</span><span class="sxs-lookup"><span data-stu-id="a5efe-147">See Also</span></span>  
 [<span data-ttu-id="a5efe-148">SQL Server のスタンドアロン インスタンスをホストするコンピューターの名前変更</span><span class="sxs-lookup"><span data-stu-id="a5efe-148">Rename a Computer that Hosts a Stand-Alone Instance of SQL Server</span></span>](../../../database-engine/install-windows/rename-a-computer-that-hosts-a-stand-alone-instance-of-sql-server.md)  
  
  
