---
title: 可用性グループの読み取り専用ルーティングの構成 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 10/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- read-only routing
- Availability Groups [SQL Server], readable secondary replicas
- Availability Groups [SQL Server], read-only routing
- readable secondary replicas
- Availability Groups [SQL Server], client connectivity
- Availability Groups [SQL Server], active secondary replicas
ms.assetid: 7bd89ddd-0403-4930-a5eb-3c78718533d4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2d51d1db75caa29814a01fc1f49bfdd49b403c3d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642962"
---
# <a name="configure-read-only-routing-for-an-availability-group-sql-server"></a><span data-ttu-id="6df45-102">可用性グループの読み取り専用ルーティングの構成 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="6df45-102">Configure Read-Only Routing for an Availability Group (SQL Server)</span></span>
  <span data-ttu-id="6df45-103">[!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]で読み取り専用ルーティングをサポートするように AlwaysOn 可用性グループを構成するには、 [!INCLUDE[tsql](../../../includes/tsql-md.md)] または PowerShell を使用します。</span><span class="sxs-lookup"><span data-stu-id="6df45-103">To configure an AlwaysOn availability group to support read-only routing in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], you can use either [!INCLUDE[tsql](../../../includes/tsql-md.md)] or PowerShell.</span></span> <span data-ttu-id="6df45-104">*読み取り専用ルーティング* は、対象の読み取り専用接続要求を、AlwaysOn の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 読み取り可能なセカンダリ レプリカ [(セカンダリ ロールで実行されているときに、読み取り専用ワークロードを許可するように構成されているレプリカ) にルーティングする](active-secondaries-readable-secondary-replicas-always-on-availability-groups.md) の機能です。</span><span class="sxs-lookup"><span data-stu-id="6df45-104">*Read-only routing* refers to the ability of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to route qualifying read-only connection requests to an available AlwaysOn [readable secondary replica](active-secondaries-readable-secondary-replicas-always-on-availability-groups.md) (that is, a replica that is configured to allow read-only workloads when running under the secondary role).</span></span> <span data-ttu-id="6df45-105">読み取り専用ルーティングをサポートするには、可用性グループに [可用性グループ リスナー](../../listeners-client-connectivity-application-failover.md)が存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6df45-105">To support read-only routing, the availability group must possess an [availability group listener](../../listeners-client-connectivity-application-failover.md).</span></span> <span data-ttu-id="6df45-106">読み取り専用クライアントは、このリスナーに接続要求を送信する必要があります。クライアントの接続文字列では、アプリケーションの目的として "読み取り専用" を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6df45-106">Read-only clients must direct their connection requests to this listener, and the client's connection strings must specify the application intent as "read-only."</span></span> <span data-ttu-id="6df45-107">つまり、 *読み取りを目的とした接続要求*であることが必要です。</span><span class="sxs-lookup"><span data-stu-id="6df45-107">That is, they must be *read-intent connection requests*.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6df45-108">読み取り可能なセカンダリ レプリカを構成する方法については、「 [可用性レプリカでの読み取り専用アクセスの構成 &#40;SQL Server&#41;](configure-read-only-access-on-an-availability-replica-sql-server.md)が存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6df45-108">For information about how to configure a readable secondary replica, see [Configure Read-Only Access on an Availability Replica &#40;SQL Server&#41;](configure-read-only-access-on-an-availability-replica-sql-server.md).</span></span>

> [!NOTE]
>  <span data-ttu-id="6df45-109">読み取り専用ルーティングの構成は [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]ではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="6df45-109">Configuring read-only routing is not supported by [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="6df45-110">はじめに</span><span class="sxs-lookup"><span data-stu-id="6df45-110">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="6df45-111">前提条件</span><span class="sxs-lookup"><span data-stu-id="6df45-111">Prerequisites</span></span>  
  
-   <span data-ttu-id="6df45-112">可用性グループに可用性グループ リスナーが存在している必要があります。</span><span class="sxs-lookup"><span data-stu-id="6df45-112">The availability group must possess an availability group listener.</span></span> <span data-ttu-id="6df45-113">詳細については、「 [可用性グループ リスナーの作成または構成 &#40;SQL Server&#41;](create-or-configure-an-availability-group-listener-sql-server.md)が存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6df45-113">For more information, see [Create or Configure an Availability Group Listener &#40;SQL Server&#41;](create-or-configure-an-availability-group-listener-sql-server.md).</span></span>  
  
-   <span data-ttu-id="6df45-114">1つまたは複数の可用性レプリカは、セカンダリロールで読み取り専用を受け入れるように構成する必要があります (つまり、読み取り[可能なセカンダリレプリカ](active-secondaries-readable-secondary-replicas-always-on-availability-groups.md)(AlwaysOn% 20availability% 20availability \) . md))。</span><span class="sxs-lookup"><span data-stu-id="6df45-114">One or more availability replicas must be configured to accept read-only in the secondary role (that is, to be [readable secondary replicas](active-secondaries-readable-secondary-replicas-always-on-availability-groups.md)(AlwaysOn%20Availability%20Groups\).md)).</span></span> <span data-ttu-id="6df45-115">詳細については、「 [可用性レプリカでの読み取り専用アクセスの構成 &#40;SQL Server&#41;](configure-read-only-access-on-an-availability-replica-sql-server.md)が存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6df45-115">For more information, see [Configure Read-Only Access on an Availability Replica &#40;SQL Server&#41;](configure-read-only-access-on-an-availability-replica-sql-server.md).</span></span>  
  
-   <span data-ttu-id="6df45-116">現在のプライマリ レプリカをホストするサーバー インスタンスに接続されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="6df45-116">You must be connected to the server instance that hosts the current primary replica.</span></span>  
  
###  <a name="what-replica-properties-do-you-need-to-configure-to-support-read-only-routing"></a><a name="RORReplicaProperties"></a><span data-ttu-id="6df45-117">読み取り専用ルーティングをサポートするように構成する必要があるレプリカのプロパティ</span><span class="sxs-lookup"><span data-stu-id="6df45-117">What Replica Properties Do you Need to Configure to Support Read-Only Routing?</span></span>  
  
-   <span data-ttu-id="6df45-118">読み取り専用ルーティングをサポートしようとしている読み取り可能なセカンダリ レプリカに対して、 *読み取り専用ルーティングの URL*を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6df45-118">For each readable secondary replica that is to support read-only routing, you need to specify a *read-only routing URL*.</span></span> <span data-ttu-id="6df45-119">この URL は、ローカル レプリカがセカンダリ ロールで実行されている場合にのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="6df45-119">This URL takes effect only when the local replica is running under the secondary role.</span></span> <span data-ttu-id="6df45-120">読み取り専用ルーティングの URL は、必要に応じてレプリカごとに指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6df45-120">The read-only routing URL must be specified on a replica-by-replica basis, as needed.</span></span> <span data-ttu-id="6df45-121">各読み取り専用ルーティングの URL は、読み取りを目的とした接続要求を特定の読み取り可能なセカンダリ レプリカにルーティングする際に使用されます。</span><span class="sxs-lookup"><span data-stu-id="6df45-121">Each read-only routing URL is used for routing read-intent connection requests to a specific readable secondary replica.</span></span> <span data-ttu-id="6df45-122">通常は、読み取り可能なすべてのセカンダリ レプリカに読み取り専用ルーティングの URL が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="6df45-122">Typically, every readable secondary replica is assigned a read-only routing URL.</span></span>  
  
     <span data-ttu-id="6df45-123">可用性レプリカの読み取り専用ルーティングの URL の計算の詳細については、「 [AlwaysOn の read_only_routing_url の計算](https://docs.microsoft.com/archive/blogs/mattn/calculating-read_only_routing_url-for-alwayson)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6df45-123">For information about calculating the read-only routing URL for an availability replica, see [Calculating read_only_routing_url for AlwaysOn](https://docs.microsoft.com/archive/blogs/mattn/calculating-read_only_routing_url-for-alwayson).</span></span>  
  
-   <span data-ttu-id="6df45-124">可用性レプリカがプライマリ レプリカである場合に読み取り専用ルーティングをサポートするには、その可用性レプリカに対して *読み取り専用ルーティング リスト*を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6df45-124">For each availability replica that you want to support read-only routing when it is the primary replica, you need to specify a *read-only routing list*.</span></span> <span data-ttu-id="6df45-125">読み取り専用ルーティング リストは、ローカル レプリカがプライマリ ロールで実行されている場合にのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="6df45-125">A given read-only routing list takes effect only when the local replica is running under the primary role.</span></span> <span data-ttu-id="6df45-126">このリストは、必要に応じてレプリカごとに指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6df45-126">This list must be specified on a replica-by-replica basis, as needed.</span></span> <span data-ttu-id="6df45-127">通常、各読み取り専用ルーティング リストには、すべての読み取り専用ルーティングの URL が含まれており、リストの末尾にローカル レプリカの URL が示されています。</span><span class="sxs-lookup"><span data-stu-id="6df45-127">Typically, each read-only routing list would contain every read-only routing URL, with the URL of the local replica at the end of the list.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6df45-128">読み取りを目的とした接続要求は、現在のプライマリ レプリカの読み取り専用ルーティング リスト内の最初に使用できる読み取り可能なセカンダリにルーティングされます。</span><span class="sxs-lookup"><span data-stu-id="6df45-128">Read-intent connection requests are routed to the first available readable secondary on the read-only routing list of the current primary replica.</span></span> <span data-ttu-id="6df45-129">負荷分散はありません。</span><span class="sxs-lookup"><span data-stu-id="6df45-129">There is no load balancing.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6df45-130">可用性グループ リスナーと読み取り専用ルーティングの詳細については、「 [可用性グループ リスナー、クライアント接続、およびアプリケーションのフェールオーバー &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md)が存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6df45-130">For information about availability group listeners and more information about read-only routing, see [Availability Group Listeners, Client Connectivity, and Application Failover &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="6df45-131">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="6df45-131">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="6df45-132">Permissions</span><span class="sxs-lookup"><span data-stu-id="6df45-132">Permissions</span></span>  
  
|<span data-ttu-id="6df45-133">タスク</span><span class="sxs-lookup"><span data-stu-id="6df45-133">Task</span></span>|<span data-ttu-id="6df45-134">アクセス許可</span><span class="sxs-lookup"><span data-stu-id="6df45-134">Permissions</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="6df45-135">可用性グループの作成時にレプリカを構成する</span><span class="sxs-lookup"><span data-stu-id="6df45-135">To configure replicas when creating an availability group</span></span>|<span data-ttu-id="6df45-136">**sysadmin** 固定サーバー ロールのメンバーシップと、CREATE AVAILABILITY GROUP サーバー権限、ALTER ANY AVAILABILITY GROUP 権限、CONTROL SERVER 権限のいずれかが必要です。</span><span class="sxs-lookup"><span data-stu-id="6df45-136">Requires membership in the **sysadmin** fixed server role and either CREATE AVAILABILITY GROUP server permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>|  
|<span data-ttu-id="6df45-137">可用性レプリカを変更する</span><span class="sxs-lookup"><span data-stu-id="6df45-137">To modify an availability replica</span></span>|<span data-ttu-id="6df45-138">可用性グループの ALTER AVAILABILITY GROUP 権限、CONTROL AVAILABILITY GROUP 権限、ALTER ANY AVAILABILITY GROUP 権限、または CONTROL SERVER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="6df45-138">Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>|  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="6df45-139">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="6df45-139">Using Transact-SQL</span></span>  
 <span data-ttu-id="6df45-140">**読み取り専用ルーティングを構成するには**</span><span class="sxs-lookup"><span data-stu-id="6df45-140">**To Configure read-only routing**</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6df45-141">コード例については、このセクションの後半の「 [例 (Transact-SQL)](#TsqlExample)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6df45-141">For a code example, see [Example (Transact-SQL)](#TsqlExample), later in this section.</span></span>  
  
1.  <span data-ttu-id="6df45-142">プライマリ レプリカをホストするサーバー インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="6df45-142">Connect to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="6df45-143">新しい可用性グループのレプリカを指定する場合は、 [CREATE AVAILABILITY GROUP](/sql/t-sql/statements/create-availability-group-transact-sql)[!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="6df45-143">If you are specifying a replica for a new availability group, use the [CREATE AVAILABILITY GROUP](/sql/t-sql/statements/create-availability-group-transact-sql)[!INCLUDE[tsql](../../../includes/tsql-md.md)] statement.</span></span> <span data-ttu-id="6df45-144">既存の可用性グループのレプリカを追加または変更する場合は、 [ALTER AVAILABILITY group](/sql/t-sql/statements/alter-availability-group-transact-sql)ステートメントを使用し [!INCLUDE[tsql](../../../includes/tsql-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="6df45-144">If you are adding or modifying a replica for an existing availability group, use the [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql)[!INCLUDE[tsql](../../../includes/tsql-md.md)] statement.</span></span>  
  
    -   <span data-ttu-id="6df45-145">セカンダリ ロールの読み取り専用ルーティングを構成するには、ADD REPLICA 句または MODIFY REPLICA WITH 句で、SECONDARY_ROLE オプションを次のように指定します。</span><span class="sxs-lookup"><span data-stu-id="6df45-145">To configure read-only routing for the secondary role, in the ADD REPLICA or MODIFY REPLICA WITH clause, specify the SECONDARY_ROLE option, as follows:</span></span>  
  
         <span data-ttu-id="6df45-146">SECONDARY_ROLE **(** READ_ONLY_ROUTING_URL **= '** TCP **:// *`system-address`* : *`port`* ')**</span><span class="sxs-lookup"><span data-stu-id="6df45-146">SECONDARY_ROLE **(** READ_ONLY_ROUTING_URL **='** TCP **://*`system-address`*:*`port`*')**</span></span>  
  
         <span data-ttu-id="6df45-147">読み取り専用ルーティング URL のパラメーターは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="6df45-147">The parameters of the read-only routing URL are as follows:</span></span>  
  
         <span data-ttu-id="6df45-148">*system-address*</span><span class="sxs-lookup"><span data-stu-id="6df45-148">*system-address*</span></span>  
         <span data-ttu-id="6df45-149">システム名、完全修飾ドメイン名では、対象のコンピューター システムを明確に識別する、IP アドレスなどの文字列です。</span><span class="sxs-lookup"><span data-stu-id="6df45-149">Is a string, such as a system name, a fully qualified domain name, or an IP address, that unambiguously identifies the destination computer system.</span></span>  
  
         <span data-ttu-id="6df45-150">*port*</span><span class="sxs-lookup"><span data-stu-id="6df45-150">*port*</span></span>  
         <span data-ttu-id="6df45-151">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスのデータベース エンジンによって使用されるポート番号です。</span><span class="sxs-lookup"><span data-stu-id="6df45-151">Is a port number that is used by the Database Engine of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance.</span></span>  
  
         <span data-ttu-id="6df45-152">例:   `SECONDARY_ROLE (READ_ONLY_ROUTING_URL = N'TCP://COMPUTER01.contoso.com:1433')`</span><span class="sxs-lookup"><span data-stu-id="6df45-152">For example:   `SECONDARY_ROLE (READ_ONLY_ROUTING_URL = N'TCP://COMPUTER01.contoso.com:1433')`</span></span>  
  
         <span data-ttu-id="6df45-153">レプリカが既に読み取り専用接続を許可するように構成されている場合、MODIFY REPLICA 句の ALLOW_CONNECTIONS は省略可能です。</span><span class="sxs-lookup"><span data-stu-id="6df45-153">In a MODIFY REPLICA clause the ALLOW_CONNECTIONS is optional if the replica is already configured to allow read-only connections.</span></span>  
  
         <span data-ttu-id="6df45-154">詳細については、「 [AlwaysOn の read_only_routing_url の計算](https://docs.microsoft.com/archive/blogs/mattn/calculating-read_only_routing_url-for-alwayson)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6df45-154">For more information, see [Calculating read_only_routing_url for AlwaysOn](https://docs.microsoft.com/archive/blogs/mattn/calculating-read_only_routing_url-for-alwayson).</span></span>  
  
    -   <span data-ttu-id="6df45-155">プライマリ ロールの読み取り専用ルーティングを構成するには、ADD REPLICA 句または MODIFY REPLICA WITH 句で、PRIMARY_ROLE オプションを次のように指定します。</span><span class="sxs-lookup"><span data-stu-id="6df45-155">To configure read-only routing for the primary role, in the ADD REPLICA or MODIFY REPLICA WITH clause, specify the PRIMARY_ROLE option, as follows:</span></span>  
  
         <span data-ttu-id="6df45-156">PRIMARY_ROLE **(** READ_ONLY_ROUTING_LIST **= (' *`server`* '** [ **,**...*n* ]) **)**</span><span class="sxs-lookup"><span data-stu-id="6df45-156">PRIMARY_ROLE **(** READ_ONLY_ROUTING_LIST **=('*`server`*'** [ **,**...*n* ] **))**</span></span>  
  
         <span data-ttu-id="6df45-157">*server* は、可用性グループの読み取り専用セカンダリ レプリカをホストするサーバー インスタンスを識別します。</span><span class="sxs-lookup"><span data-stu-id="6df45-157">where, *server* identifies a server instance that hosts a read-only secondary replica in the availability group.</span></span>  
  
         <span data-ttu-id="6df45-158">例:   `PRIMARY_ROLE (READ_ONLY_ROUTING_LIST=('Server1','Server2'))`</span><span class="sxs-lookup"><span data-stu-id="6df45-158">For example:   `PRIMARY_ROLE (READ_ONLY_ROUTING_LIST=('Server1','Server2'))`</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="6df45-159">読み取り専用ルーティング リストを構成する前に、読み取り専用ルーティング URL を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6df45-159">You must set the read-only routing URL before configuring the read-only routing list.</span></span>  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="6df45-160">例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="6df45-160">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="6df45-161">次の例では、既存の可用性グループ `AG1` の 2 つの可用性レプリカを、これらのレプリカのいずれかが現在プライマリ ロールを所有している場合に読み取り専用ルーティングをサポートするように変更します。</span><span class="sxs-lookup"><span data-stu-id="6df45-161">The following example modifies two availability replicas of an existing availability group, `AG1` to support read-only routing if one of these replicas currently owns the primary role.</span></span> <span data-ttu-id="6df45-162">可用性レプリカをホストするサーバー インスタンスを識別するために、この例ではインスタンス名 `COMPUTER01` および `COMPUTER02` を指定します。</span><span class="sxs-lookup"><span data-stu-id="6df45-162">To identify the server instances that host the availability replica, this example specifies the instance names-`COMPUTER01` and `COMPUTER02`.</span></span>  
  
```sql
ALTER AVAILABILITY GROUP [AG1]  
 MODIFY REPLICA ON  
N'COMPUTER01' WITH   
(SECONDARY_ROLE (ALLOW_CONNECTIONS = READ_ONLY));  
ALTER AVAILABILITY GROUP [AG1]  
 MODIFY REPLICA ON  
N'COMPUTER01' WITH   
(SECONDARY_ROLE (READ_ONLY_ROUTING_URL = N'TCP://COMPUTER01.contoso.com:1433'));  
  
ALTER AVAILABILITY GROUP [AG1]  
 MODIFY REPLICA ON  
N'COMPUTER02' WITH   
(SECONDARY_ROLE (ALLOW_CONNECTIONS = READ_ONLY));  
ALTER AVAILABILITY GROUP [AG1]  
 MODIFY REPLICA ON  
N'COMPUTER02' WITH   
(SECONDARY_ROLE (READ_ONLY_ROUTING_URL = N'TCP://COMPUTER02.contoso.com:1433'));  
  
ALTER AVAILABILITY GROUP [AG1]   
MODIFY REPLICA ON  
N'COMPUTER01' WITH   
(PRIMARY_ROLE (READ_ONLY_ROUTING_LIST=('COMPUTER02','COMPUTER01')));  
  
ALTER AVAILABILITY GROUP [AG1]   
MODIFY REPLICA ON  
N'COMPUTER02' WITH   
(PRIMARY_ROLE (READ_ONLY_ROUTING_LIST=('COMPUTER01','COMPUTER02')));  
GO
```  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a><span data-ttu-id="6df45-163">PowerShell の使用</span><span class="sxs-lookup"><span data-stu-id="6df45-163">Using PowerShell</span></span>  

### <a name="to-configure-read-only-routing"></a><span data-ttu-id="6df45-164">読み取り専用ルーティングを構成するには</span><span class="sxs-lookup"><span data-stu-id="6df45-164">To Configure read-only routing</span></span>
  
> [!NOTE]  
>  <span data-ttu-id="6df45-165">コード例については、このセクションの後半の「 [例 (PowerShell)](#PSExample)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6df45-165">For a code example, see [Example (PowerShell)](#PSExample), later in this section.</span></span>  
  
1.  <span data-ttu-id="6df45-166">既定 (`cd`) を、プライマリ レプリカをホストするサーバー インスタンスに設定します。</span><span class="sxs-lookup"><span data-stu-id="6df45-166">Set default (`cd`) to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="6df45-167">可用性グループに可用性レプリカを追加する場合は、`New-SqlAvailabilityReplica` コマンドレットを使用します。</span><span class="sxs-lookup"><span data-stu-id="6df45-167">When adding an availability replica to an availability group, use the `New-SqlAvailabilityReplica` cmdlet.</span></span> <span data-ttu-id="6df45-168">既存の可用性レプリカを変更する場合は、`Set-SqlAvailabilityReplica` コマンドレットを使用します。</span><span class="sxs-lookup"><span data-stu-id="6df45-168">When modifying an existing availability replica, use the `Set-SqlAvailabilityReplica` cmdlet.</span></span> <span data-ttu-id="6df45-169">関連するパラメーターは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="6df45-169">The relevant parameters are as follows:</span></span>  
  
    -   <span data-ttu-id="6df45-170">セカンダリロールの読み取り専用ルーティングを構成するには、 **ReadonlyRoutingConnectionUrl " *`url`* "** パラメーターを指定します。</span><span class="sxs-lookup"><span data-stu-id="6df45-170">To configure read-only routing for the secondary role, specify the **ReadonlyRoutingConnectionUrl"*`url`*"** parameter.</span></span>  
  
         <span data-ttu-id="6df45-171">*url* は、読み取り専用接続のためにレプリカにルーティングするときに使用する、接続の完全修飾ドメイン名 (FQDN) およびポートです。</span><span class="sxs-lookup"><span data-stu-id="6df45-171">where, *url* is the connectivity fully-qualified domain name (FQDN) and port to use when routing to the replica for read-only connections.</span></span> <span data-ttu-id="6df45-172">次に例を示します。`-ReadonlyRoutingConnectionUrl "TCP://DBSERVER8.manufacturing.Adventure-Works.com:7024"`</span><span class="sxs-lookup"><span data-stu-id="6df45-172">For example:  `-ReadonlyRoutingConnectionUrl "TCP://DBSERVER8.manufacturing.Adventure-Works.com:7024"`</span></span>  
  
         <span data-ttu-id="6df45-173">詳細については、「 [AlwaysOn の read_only_routing_url の計算](https://docs.microsoft.com/archive/blogs/mattn/calculating-read_only_routing_url-for-alwayson)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6df45-173">For more information, see [Calculating read_only_routing_url for AlwaysOn](https://docs.microsoft.com/archive/blogs/mattn/calculating-read_only_routing_url-for-alwayson).</span></span>  
  
    -   <span data-ttu-id="6df45-174">プライマリロールの接続アクセスを構成するには、 **ReadonlyRoutingList " *`server`* "** [ **,**...] を指定します。*n* ]。ここで、*サーバー*は、可用性グループ内の読み取り専用セカンダリレプリカをホストするサーバーインスタンスを識別します。</span><span class="sxs-lookup"><span data-stu-id="6df45-174">To configure connection access for the primary role, specify **ReadonlyRoutingList"*`server`*"** [ **,**...*n* ], where *server* identifies a server instance that hosts a read-only secondary replica in the availability group.</span></span> <span data-ttu-id="6df45-175">次に例を示します。`-ReadOnlyRoutingList "SecondaryServer","PrimaryServer"`</span><span class="sxs-lookup"><span data-stu-id="6df45-175">For example:  `-ReadOnlyRoutingList "SecondaryServer","PrimaryServer"`</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="6df45-176">レプリカの読み取り専用ルーティング リストを構成する前に、レプリカの読み取り専用ルーティング URL を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6df45-176">You must set the read-only routing URL of a replica before configuring its read-only routing list.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6df45-177">コマンドレットの構文を表示するには、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell 環境で `Get-Help` コマンドレットを使用します。</span><span class="sxs-lookup"><span data-stu-id="6df45-177">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell environment.</span></span> <span data-ttu-id="6df45-178">詳細については、「 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6df45-178">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
<span data-ttu-id="6df45-179">SQL Server PowerShell プロバイダーを設定して使用するには、「 [SQL Server PowerShell プロバイダー](../../../powershell/sql-server-powershell-provider.md) 」と「[ヘルプの表示 SQL Server PowerShell](../../../powershell/sql-server-powershell.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6df45-179">To set up and use the SQL Server PowerShell provider, see [SQL Server PowerShell Provider](../../../powershell/sql-server-powershell-provider.md) and [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>
  
###  <a name="example-powershell"></a><a name="PSExample"></a> <span data-ttu-id="6df45-180">例 (PowerShell)</span><span class="sxs-lookup"><span data-stu-id="6df45-180">Example (PowerShell)</span></span>  
 <span data-ttu-id="6df45-181">次の例では、可用性グループ内のプライマリ レプリカと 1 つのセカンダリ レプリカを読み取り専用ルーティング用に構成します。</span><span class="sxs-lookup"><span data-stu-id="6df45-181">The following example configures the primary replica and one secondary replica in an availability group for read-only routing.</span></span> <span data-ttu-id="6df45-182">まず、読み取り専用ルーティングの URL が各レプリカに割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="6df45-182">First, the example assigns a read-only routing URL to each replica.</span></span> <span data-ttu-id="6df45-183">次に、プライマリ レプリカで読み取り専用ルーティング リストを設定します。</span><span class="sxs-lookup"><span data-stu-id="6df45-183">Then it sets the read-only routing list on the primary replica.</span></span> <span data-ttu-id="6df45-184">接続文字列で "ReadOnly" プロパティが設定された接続は、セカンダリ レプリカにリダイレクトされます。</span><span class="sxs-lookup"><span data-stu-id="6df45-184">Connections with the "ReadOnly" property set in the connection string will be redirected to the secondary replica.</span></span> <span data-ttu-id="6df45-185">このセカンダリ レプリカが読み取り不可である場合 (`ConnectionModeInSecondaryRole` 設定によって決まります)、接続はプライマリ レプリカに戻されます。</span><span class="sxs-lookup"><span data-stu-id="6df45-185">If this secondary replica is not readable (as determined by the `ConnectionModeInSecondaryRole` setting), the connection will be directed back to the primary replica.</span></span>  
  
```powershell
Set-Location SQLSERVER:\SQL\PrimaryServer\default\AvailabilityGroups\MyAg  
$primaryReplica = Get-Item "AvailabilityReplicas\PrimaryServer"  
$secondaryReplica = Get-Item "AvailabilityReplicas\SecondaryServer"  
  
Set-SqlAvailabilityReplica -ReadOnlyRoutingConnectionUrl "TCP://PrimaryServer.domain.com:1433" -InputObject $primaryReplica  
Set-SqlAvailabilityReplica -ReadOnlyRoutingConnectionUrl "TCP://SecondaryServer.domain.com:1433" -InputObject $secondaryReplica  
Set-SqlAvailabilityReplica -ReadOnlyRoutingList "SecondaryServer","PrimaryServer" -InputObject $primaryReplica  
```  
  
##  <a name="follow-up-after-configuring-read-only-routing"></a><a name="FollowUp"></a><span data-ttu-id="6df45-186">補足情報: 読み取り専用ルーティングを構成した後</span><span class="sxs-lookup"><span data-stu-id="6df45-186">Follow Up: After Configuring Read-Only Routing</span></span>  
 <span data-ttu-id="6df45-187">現在のプライマリ レプリカと読み取り可能なセカンダリ レプリカをそれぞれのロールで読み取り専用ルーティングをサポートするように設定すると、読み取り可能なセカンダリ レプリカは、可用性グループ リスナーを介して接続するクライアントからの読み取りを目的とした接続要求を受信できるようになります。</span><span class="sxs-lookup"><span data-stu-id="6df45-187">Once the current primary replica and the readable secondary replicas are configured to support read-only routing in both roles, the readable secondary replicas can receive read read-intent connection requests from clients that connect via the availability group listener.</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="6df45-188">[Bcp ユーティリティ](../../../tools/bcp-utility.md)または[sqlcmd ユーティリティ](../../../tools/sqlcmd-utility.md)を使用する場合は、スイッチを指定することによって、読み取り専用アクセスが有効になっている任意のセカンダリレプリカへの読み取り専用アクセスを指定でき `-K ReadOnly` ます。</span><span class="sxs-lookup"><span data-stu-id="6df45-188">When using the [bcp Utility](../../../tools/bcp-utility.md) or [sqlcmd Utility](../../../tools/sqlcmd-utility.md), you can specify read-only access to any secondary replica that is enabled for read-only access by specifying the `-K ReadOnly` switch.</span></span>  
  
###  <a name="requirements-and-recommendations-for-client-connection-strings"></a><a name="ConnStringReqsRecs"></a><span data-ttu-id="6df45-189">クライアント接続文字列の要件と推奨事項</span><span class="sxs-lookup"><span data-stu-id="6df45-189">Requirements and Recommendations for Client Connection-Strings</span></span>  
 <span data-ttu-id="6df45-190">クライアント アプリケーションで読み取り専用ルーティングを使用するには、クライアントの接続文字列が次の要件を満たしている必要があります。</span><span class="sxs-lookup"><span data-stu-id="6df45-190">For a client application to use read-only routing, its connection string must satisfy the following requirements:</span></span>  
  
-   <span data-ttu-id="6df45-191">TCP プロトコルを使用する。</span><span class="sxs-lookup"><span data-stu-id="6df45-191">Use the TCP protocol.</span></span>  
  
-   <span data-ttu-id="6df45-192">アプリケーションの目的の属性またはプロパティを読み取り専用に設定する。</span><span class="sxs-lookup"><span data-stu-id="6df45-192">Set the application intent attribute/property to readonly.</span></span>  
  
-   <span data-ttu-id="6df45-193">読み取り専用ルーティングをサポートするように構成された可用性グループのリスナーを参照する。</span><span class="sxs-lookup"><span data-stu-id="6df45-193">Reference the listener of an availability group that is configured to support read-only routing.</span></span>  
  
-   <span data-ttu-id="6df45-194">その可用性グループ内のデータベースを参照する。</span><span class="sxs-lookup"><span data-stu-id="6df45-194">Reference a database in that availability group.</span></span>  
  
 <span data-ttu-id="6df45-195">さらに、接続文字列でマルチサブネット フェールオーバーを有効にすることをお勧めします。マルチサブネット フェールオーバーは、各サブネット上の各レプリカについて並行クライアント スレッドをサポートします。</span><span class="sxs-lookup"><span data-stu-id="6df45-195">In addition, we recommend that connection strings enable multi-subnet failover, which supports a parallel client thread for each replica on each subnet.</span></span> <span data-ttu-id="6df45-196">これにより、フェールオーバー後のクライアント再接続時間が最小化されます。</span><span class="sxs-lookup"><span data-stu-id="6df45-196">This minimizes client reconnection time after a failover.</span></span>  
  
 <span data-ttu-id="6df45-197">接続文字列の構文は、アプリケーションが使用している SQL Server プロバイダーに依存します。</span><span class="sxs-lookup"><span data-stu-id="6df45-197">The syntax for a connection string depends on the SQL Server provider an application is using.</span></span> <span data-ttu-id="6df45-198">.NET Framework Data Provider 4.0.2 for SQL Server 用の次の接続文字列例は、読み取り専用ルーティング用に機能することが必須および推奨される接続文字列の一部を示しています。</span><span class="sxs-lookup"><span data-stu-id="6df45-198">The following example connection string for the .NET Framework Data Provider 4.0.2 for SQL Server illustrates the parts of a connection string that are required and recommended to work for read-only routing.</span></span>  
  
```  
Server=tcp:MyAgListener,1433;Database=Db1;IntegratedSecurity=SSPI;ApplicationIntent=ReadOnly;MultiSubnetFailover=True  
```  
  
 <span data-ttu-id="6df45-199">読み取り専用のアプリケーションの目的と読み取り専用のルーティングの詳細については、「 [可用性グループ リスナー、クライアント接続、およびアプリケーションのフェールオーバー &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md)が存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6df45-199">For more information about read-only application intent and read-only routing, see [Availability Group Listeners, Client Connectivity, and Application Failover &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md).</span></span>  
  
### <a name="if-read-only-routing-is-not-working-correctly"></a><span data-ttu-id="6df45-200">読み取り専用ルーティングが正常に動作しない場合</span><span class="sxs-lookup"><span data-stu-id="6df45-200">If Read-Only Routing is Not Working Correctly</span></span>  
 <span data-ttu-id="6df45-201">読み取り専用ルーティング構成のトラブルシューティングの詳細については、「 [読み取り専用ルーティングが正常に動作しない](troubleshoot-always-on-availability-groups-configuration-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6df45-201">For information about troubleshooting a read-only routing configuration, see [Read-Only Routing is Not Working Correctly](troubleshoot-always-on-availability-groups-configuration-sql-server.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="6df45-202">関連タスク</span><span class="sxs-lookup"><span data-stu-id="6df45-202">Related Tasks</span></span>  

### <a name="to-view-read-only-routing-configurations"></a><span data-ttu-id="6df45-203">読み取り専用ルーティングの構成を表示するには</span><span class="sxs-lookup"><span data-stu-id="6df45-203">To view read-only routing configurations</span></span>
  
-   [<span data-ttu-id="6df45-204">sys.availability_read_only_routing_lists &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="6df45-204">sys.availability_read_only_routing_lists &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-read-only-routing-lists-transact-sql)  
  
-   <span data-ttu-id="6df45-205">[sys.availability_replicas &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-availability-replicas-transact-sql) (**read_only_routing_url** 列)</span><span class="sxs-lookup"><span data-stu-id="6df45-205">[sys.availability_replicas &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-availability-replicas-transact-sql) (**read_only_routing_url** column)</span></span>  
  
### <a name="to-configure-client-connection-access"></a><span data-ttu-id="6df45-206">クライアント接続アクセスを構成するには</span><span class="sxs-lookup"><span data-stu-id="6df45-206">To configure client connection access</span></span>
  
-   [<span data-ttu-id="6df45-207">可用性グループ リスナーの作成または構成 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="6df45-207">Create or Configure an Availability Group Listener &#40;SQL Server&#41;</span></span>](create-or-configure-an-availability-group-listener-sql-server.md)  
  
-   [<span data-ttu-id="6df45-208">可用性レプリカでの読み取り専用アクセスの構成 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="6df45-208">Configure Read-Only Access on an Availability Replica &#40;SQL Server&#41;</span></span>](configure-read-only-access-on-an-availability-replica-sql-server.md)  
  
### <a name="to-use-connection-strings-in-applications"></a><span data-ttu-id="6df45-209">アプリケーションで接続文字列を使用するには</span><span class="sxs-lookup"><span data-stu-id="6df45-209">To use connection strings in applications</span></span>
  
-   [<span data-ttu-id="6df45-210">SQL Server Native Client の HADR サポート</span><span class="sxs-lookup"><span data-stu-id="6df45-210">SQL Server Native Client Support for High Availability, Disaster Recovery</span></span>](../../../relational-databases/native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md)  
  
-   [<span data-ttu-id="6df45-211">SQL Server Native Client での接続文字列キーワードの使用</span><span class="sxs-lookup"><span data-stu-id="6df45-211">Using Connection String Keywords with SQL Server Native Client</span></span>](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="6df45-212">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="6df45-212">Related Content</span></span>  
  
-   <span data-ttu-id="6df45-213">**ブログ:**</span><span class="sxs-lookup"><span data-stu-id="6df45-213">**Blogs:**</span></span>  
  
     [<span data-ttu-id="6df45-214">AlwaysOn の read_only_routing_url の計算</span><span class="sxs-lookup"><span data-stu-id="6df45-214">Calculating read_only_routing_url for AlwaysOn</span></span>](https://docs.microsoft.com/archive/blogs/mattn/calculating-read_only_routing_url-for-alwayson)  
  
     [<span data-ttu-id="6df45-215">SQL Server AlwaysOn チームのブログ:SQL Server AlwaysOn チームのオフィシャル ブログ</span><span class="sxs-lookup"><span data-stu-id="6df45-215">SQL Server AlwaysOn Team Blogs: The official SQL Server AlwaysOn Team Blog</span></span>](https://blogs.msdn.com/b/sqlalwayson/)  
  
     [<span data-ttu-id="6df45-216">CSS SQL Server エンジニアのブログ</span><span class="sxs-lookup"><span data-stu-id="6df45-216">CSS SQL Server Engineers Blogs</span></span>](https://blogs.msdn.com/b/psssql/)  
  
-   <span data-ttu-id="6df45-217">**ホワイトペーパー:**</span><span class="sxs-lookup"><span data-stu-id="6df45-217">**White papers:**</span></span>  
  
     [<span data-ttu-id="6df45-218">SQL Server 2012 に関する Microsoft ホワイト ペーパー</span><span class="sxs-lookup"><span data-stu-id="6df45-218">Microsoft White Papers for SQL Server 2012</span></span>](https://msdn.microsoft.com/library/hh403491.aspx)  
  
     [<span data-ttu-id="6df45-219">SQL Server ユーザー諮問チームのホワイト ペーパー</span><span class="sxs-lookup"><span data-stu-id="6df45-219">SQL Server Customer Advisory Team Whitepapers</span></span>](http://sqlcat.com/)  
  
## <a name="see-also"></a><span data-ttu-id="6df45-220">参照</span><span class="sxs-lookup"><span data-stu-id="6df45-220">See Also</span></span>  
 <span data-ttu-id="6df45-221">[AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="6df45-221">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="6df45-222">[AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="6df45-222">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="6df45-223">[アクティブなセカンダリ: 読み取り可能なセカンダリレプリカ (AlwaysOn 可用性グループ)](active-secondaries-readable-secondary-replicas-always-on-availability-groups.md) </span><span class="sxs-lookup"><span data-stu-id="6df45-223">[Active Secondaries: Readable Secondary Replicas (AlwaysOn Availability Groups)](active-secondaries-readable-secondary-replicas-always-on-availability-groups.md) </span></span>  
 <span data-ttu-id="6df45-224">[可用性レプリカに対するクライアント接続アクセスについて &#40;SQL Server&#41;](about-client-connection-access-to-availability-replicas-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="6df45-224">[About Client Connection Access to Availability Replicas &#40;SQL Server&#41;](about-client-connection-access-to-availability-replicas-sql-server.md) </span></span>  
 [<span data-ttu-id="6df45-225">可用性グループ リスナー、クライアント接続、およびアプリケーションのフェールオーバー &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="6df45-225">Availability Group Listeners, Client Connectivity, and Application Failover &#40;SQL Server&#41;</span></span>](../../listeners-client-connectivity-application-failover.md)  
