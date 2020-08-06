---
title: AlwaysOn 可用性グループを使用した Service Broker (SQL Server) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Service Broker, AlwaysOn Availability Groups
- Availability Groups [SQL Server], interoperability
ms.assetid: 881c20e5-1c99-44eb-b393-09fc5ea0f122
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: da179219363422c4ec242d29be61f35dd1609823
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641247"
---
# <a name="service-broker-with-alwayson-availability-groups-sql-server"></a><span data-ttu-id="f6b79-102">Service Broker と AlwaysOn 可用性グループ (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="f6b79-102">Service Broker with AlwaysOn Availability Groups (SQL Server)</span></span>
  <span data-ttu-id="f6b79-103">このトピックでは、 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] で Service Broker を [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]と共に使用できるように構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f6b79-103">This topic contains information about configuring Service Broker to work with [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>  
  
 <span data-ttu-id="f6b79-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="f6b79-104">**In This Topic:**</span></span>  
  
-   [<span data-ttu-id="f6b79-105">可用性グループのサービスでリモートメッセージを受信するための要件</span><span class="sxs-lookup"><span data-stu-id="f6b79-105">Requirements for a Service in an Availability Group to Receive Remote Messages</span></span>](#ReceiveRemoteMessages)  
  
-   [<span data-ttu-id="f6b79-106">可用性グループのリモートサービスにメッセージを送信するための要件</span><span class="sxs-lookup"><span data-stu-id="f6b79-106">Requirements for Sending Messages to a Remote Service in an Availability Group</span></span>](#SendRemoteMessages)  
  
##  <a name="requirements-for-a-service-in-an-availability-group-to-receive-remote-messages"></a><a name="ReceiveRemoteMessages"></a> <span data-ttu-id="f6b79-107">可用性グループのサービスでリモート メッセージを受信するための要件</span><span class="sxs-lookup"><span data-stu-id="f6b79-107">Requirements for a Service in an Availability Group to Receive Remote Messages</span></span>  
  
1.  <span data-ttu-id="f6b79-108">**可用性グループにリスナーが存在している。**</span><span class="sxs-lookup"><span data-stu-id="f6b79-108">**Ensure that the availability group possesses a listener.**</span></span>  
  
     <span data-ttu-id="f6b79-109">詳細については、「 [可用性グループ リスナーの作成または構成 &#40;SQL Server&#41;](create-or-configure-an-availability-group-listener-sql-server.md)が存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f6b79-109">For more information, see [Create or Configure an Availability Group Listener &#40;SQL Server&#41;](create-or-configure-an-availability-group-listener-sql-server.md).</span></span>  
  
2.  <span data-ttu-id="f6b79-110">**Service Broker エンドポイントが存在し、正しく構成されている。**</span><span class="sxs-lookup"><span data-stu-id="f6b79-110">**Ensure that the Service Broker endpoint exists and is correctly configured.**</span></span>  
  
     <span data-ttu-id="f6b79-111">可用性グループの可用性レプリカをホストするすべての [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスで、次のように Service Broker エンドポイントを構成します。</span><span class="sxs-lookup"><span data-stu-id="f6b79-111">On every instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that hosts an availability replica for the availability group, configure the Service Broker endpoint, as follows:</span></span>  
  
    -   <span data-ttu-id="f6b79-112">LISTENER_IP を "ALL" に設定します。</span><span class="sxs-lookup"><span data-stu-id="f6b79-112">Set LISTENER_IP to 'ALL'.</span></span> <span data-ttu-id="f6b79-113">この設定により、可用性グループ リスナーにバインドされている有効な IP アドレスに接続できるようになります。</span><span class="sxs-lookup"><span data-stu-id="f6b79-113">This setting enables connections on any valid IP address that is bound to the availability group listener.</span></span>  
  
    -   <span data-ttu-id="f6b79-114">すべてのホスト サーバー インスタンスで Service Broker の PORT を同じポート番号に設定します。</span><span class="sxs-lookup"><span data-stu-id="f6b79-114">Set the Service Broker PORT to the same port number on all the host server instances.</span></span>  
  
        > [!TIP]  
        >  <span data-ttu-id="f6b79-115">特定のサーバー インスタンスの Service Broker エンドポイントのポート番号を確認するには、 **sys.tcp_endpoints** カタログ ビューの [port](/sql/relational-databases/system-catalog-views/sys-tcp-endpoints-transact-sql) 列に対してクエリを実行します ( **type_desc** = 'SERVICE_BROKER')。</span><span class="sxs-lookup"><span data-stu-id="f6b79-115">To view the port number of the Service Broker endpoint on a given server instance, query the **port** column of the [sys.tcp_endpoints](/sql/relational-databases/system-catalog-views/sys-tcp-endpoints-transact-sql) catalog view, where **type_desc** = 'SERVICE_BROKER'.</span></span>  
  
     <span data-ttu-id="f6b79-116">次の例では、既定の Service Broker ポート (4022) を使用し、有効なすべての IP アドレスをリッスンする Windows 認証済みの Service Broker エンドポイントを作成します。</span><span class="sxs-lookup"><span data-stu-id="f6b79-116">The following example creates a Windows authenticated Service Broker endpoint that uses the default Service Broker port (4022) and listens to all valid IP addresses.</span></span>  
  
    ```  
    CREATE ENDPOINT [SSBEndpoint]  
        STATE = STARTED  
        AS TCP  (LISTENER_PORT = 4022, LISTENER_IP = ALL )  
        FOR SERVICE_BROKER (AUTHENTICATION = WINDOWS)  
    ```  
  
     <span data-ttu-id="f6b79-117">詳細については、「[CREATE ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f6b79-117">For more information, see [CREATE ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql).</span></span>  
  
3.  <span data-ttu-id="f6b79-118">**エンドポイントに対する CONNECT 権限を許可する。**</span><span class="sxs-lookup"><span data-stu-id="f6b79-118">**Grant CONNECT permission on the endpoint.**</span></span>  
  
     <span data-ttu-id="f6b79-119">Service Broker エンドポイントに対する CONNECT 権限を PUBLIC またはログインに許可します。</span><span class="sxs-lookup"><span data-stu-id="f6b79-119">Grant CONNECT permission on the Service Broker endpoint either to PUBLIC or to a login.</span></span>  
  
     <span data-ttu-id="f6b79-120">次の例では、 `broker_endpoint` という名前の Service Broker エンドポイントに対する接続を PUBLIC に許可します。</span><span class="sxs-lookup"><span data-stu-id="f6b79-120">The following example grants the connection on a Service Broker endpoint named `broker_endpoint` to PUBLIC.</span></span>  
  
    ```  
    GRANT CONNECT ON ENDPOINT::[broker_endpoint] TO [PUBLIC]  
    ```  
  
     <span data-ttu-id="f6b79-121">詳細については、「 [GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql)と共に使用できるように構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f6b79-121">For more information, see [GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql).</span></span>  
  
4.  <span data-ttu-id="f6b79-122">**msdb に AutoCreatedLocal ルートまたは特定のサービスへのルートが含まれている。**</span><span class="sxs-lookup"><span data-stu-id="f6b79-122">**Ensure that msdb contains either an AutoCreatedLocal route or a route to the specific service.**</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f6b79-123">**msdb**を含む各ユーザー データベースには、既定で **AutoCreatedLocal**というルートが含まれています。</span><span class="sxs-lookup"><span data-stu-id="f6b79-123">By default, each user database, including **msdb**, contains the route **AutoCreatedLocal**.</span></span> <span data-ttu-id="f6b79-124">このルートは、どのサービス名および任意のブローカー インスタンスにも適用でき、現在のインスタンス内でメッセージを配信するように指定します。</span><span class="sxs-lookup"><span data-stu-id="f6b79-124">This route matches any service name and broker instance and specifies that the message should be delivered within the current instance.</span></span> <span data-ttu-id="f6b79-125">**AutoCreatedLocal** の優先度は、リモート インスタンスと通信する特定のサービスを明示的に指定したルートよりも低くなります。</span><span class="sxs-lookup"><span data-stu-id="f6b79-125">**AutoCreatedLocal** has lower priority than routes that explicitly specify a specific service that communicates with a remote instance.</span></span>  
  
     <span data-ttu-id="f6b79-126">ルートの作成の詳細については、「 [Service Broker のルーティングの例](https://msdn.microsoft.com/library/ms166090\(SQL.105\).aspx) 」( [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] バージョンのオンライン ブック) および「 [CREATE ROUTE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-route-transact-sql)と共に使用できるように構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f6b79-126">For information about creating routes, see [Service Broker Routing Examples](https://msdn.microsoft.com/library/ms166090\(SQL.105\).aspx) (in the [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] version of Books Online) and [CREATE ROUTE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-route-transact-sql).</span></span>  
  
##  <a name="requirements-for-sending-messages-to-a-remote-service-in-an-availability-group"></a><a name="SendRemoteMessages"></a> <span data-ttu-id="f6b79-127">可用性グループのリモート サービスにメッセージを送信するための要件</span><span class="sxs-lookup"><span data-stu-id="f6b79-127">Requirements for Sending Messages to a Remote Service in an Availability Group</span></span>  
  
1.  <span data-ttu-id="f6b79-128">**対象サービスへのルートを作成する。**</span><span class="sxs-lookup"><span data-stu-id="f6b79-128">**Create a route to the target service.**</span></span>  
  
     <span data-ttu-id="f6b79-129">次のようにルートを構成します。</span><span class="sxs-lookup"><span data-stu-id="f6b79-129">Configure the route as follows:</span></span>  
  
    -   <span data-ttu-id="f6b79-130">ADDRESS を、サービス データベースをホストする可用性グループのリスナーの IP アドレスに設定します。</span><span class="sxs-lookup"><span data-stu-id="f6b79-130">Set ADDRESS to the listener IP address of availability group that hosts the service database.</span></span>  
  
    -   <span data-ttu-id="f6b79-131">PORT を、各リモート SQL Server インスタンスの Service Broker エンドポイントに指定したポートに設定します。</span><span class="sxs-lookup"><span data-stu-id="f6b79-131">Set PORT to the port that you specified in the Service Broker endpoint of each of the remote SQL Server instances.</span></span>  
  
     <span data-ttu-id="f6b79-132">次の例では、 `RouteToTargetService` サービスに対する `ISBNLookupRequestService` という名前のルートを作成します。</span><span class="sxs-lookup"><span data-stu-id="f6b79-132">The following example creates a route named `RouteToTargetService` for the `ISBNLookupRequestService` service.</span></span> <span data-ttu-id="f6b79-133">ルートの対象は、ポート 4022 を使用している可用性グループ リスナー `MyAgListener`です。</span><span class="sxs-lookup"><span data-stu-id="f6b79-133">The route targets the availability group listener, `MyAgListener`, which uses port 4022.</span></span>  
  
    ```  
    CREATE ROUTE [RouteToTargetService] WITH   
    SERVICE_NAME = 'ISBNLookupRequestService',   
    ADDRESS = 'TCP://MyAgListener:4022';  
  
    ```  
  
     <span data-ttu-id="f6b79-134">詳細については、「 [CREATE ROUTE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-route-transact-sql)と共に使用できるように構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f6b79-134">For more information, see [CREATE ROUTE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-route-transact-sql).</span></span>  
  
2.  <span data-ttu-id="f6b79-135">**msdb に AutoCreatedLocal ルートまたは特定のサービスへのルートが含まれている。**</span><span class="sxs-lookup"><span data-stu-id="f6b79-135">**Ensure that msdb contains either an AutoCreatedLocal route or a route to the specific service.**</span></span> <span data-ttu-id="f6b79-136">(詳細については、このトピックの前の「 [可用性グループのサービスでリモート メッセージを受信するための要件](#ReceiveRemoteMessages)」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="f6b79-136">(For more information, see [Requirements for a Service in an Availability Group to Receive Remote Messages](#ReceiveRemoteMessages), earlier in this topic.)</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="f6b79-137">関連タスク</span><span class="sxs-lookup"><span data-stu-id="f6b79-137">Related Tasks</span></span>  
  
-   [<span data-ttu-id="f6b79-138">CREATE ENDPOINT &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f6b79-138">CREATE ENDPOINT &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-endpoint-transact-sql)  
  
-   [<span data-ttu-id="f6b79-139">CREATE ROUTE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f6b79-139">CREATE ROUTE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-route-transact-sql)  
  
-   [<span data-ttu-id="f6b79-140">GRANT &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f6b79-140">GRANT &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/grant-transact-sql)  
  
-   <span data-ttu-id="f6b79-141">[可用性グループ リスナーの作成または構成 &#40;SQL Server&#41;](create-or-configure-an-availability-group-listener-sql-server.md)</span><span class="sxs-lookup"><span data-stu-id="f6b79-141">[Create or Configure an Availability Group Listener &#40;SQL Server&#41;](create-or-configure-an-availability-group-listener-sql-server.md).</span></span>  
  
-   [<span data-ttu-id="f6b79-142">可用性グループの作成と構成 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="f6b79-142">Creation and Configuration of Availability Groups &#40;SQL Server&#41;</span></span>](creation-and-configuration-of-availability-groups-sql-server.md)  
  
-   [<span data-ttu-id="f6b79-143">データベースミラーリングまたは AlwaysOn 可用性グループ &#40;SQL Server のログインアカウントを設定&#41;</span><span class="sxs-lookup"><span data-stu-id="f6b79-143">Set Up Login Accounts for Database Mirroring or AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](../../database-mirroring/set-up-login-accounts-database-mirroring-always-on-availability.md)  
  
## <a name="see-also"></a><span data-ttu-id="f6b79-144">参照</span><span class="sxs-lookup"><span data-stu-id="f6b79-144">See Also</span></span>  
 <span data-ttu-id="f6b79-145">[AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="f6b79-145">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="f6b79-146">[可用性グループ リスナー、クライアント接続、およびアプリケーションのフェールオーバー &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md) </span><span class="sxs-lookup"><span data-stu-id="f6b79-146">[Availability Group Listeners, Client Connectivity, and Application Failover &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md) </span></span>  
 [<span data-ttu-id="f6b79-147">SQL Server Service Broker (SQL Server Service Broker)</span><span class="sxs-lookup"><span data-stu-id="f6b79-147">SQL Server Service Broker</span></span>](../../configure-windows/sql-server-service-broker.md)  
  
  
