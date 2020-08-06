---
title: 可用性レプリカでの読み取り専用アクセスの構成 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 10/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- connection access to availability replicas
- Availability Groups [SQL Server], readable secondary replicas
- active secondary replicas [SQL Server], read-only access to
- Availability Groups [SQL Server], read-only routing
- Availability Groups [SQL Server], client connectivity
ms.assetid: 22387419-22c4-43fa-851c-5fecec4b049b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ab13081396aff46d193c1b0449d6b93042ee60d6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713513"
---
# <a name="configure-read-only-access-on-an-availability-replica-sql-server"></a><span data-ttu-id="bdc77-102">可用性レプリカでの読み取り専用アクセスの構成 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="bdc77-102">Configure Read-Only Access on an Availability Replica (SQL Server)</span></span>
  <span data-ttu-id="bdc77-103">既定では、プライマリ レプリカへの読み取り/書き込みアクセスと読み取りを目的としたアクセスの両方が許可され、AlwaysOn 可用性グループのセカンダリ レプリカへの接続は許可されません。</span><span class="sxs-lookup"><span data-stu-id="bdc77-103">By default both read-write and read-intent access are allowed to the primary replica and no connections are allowed to secondary replicas of an AlwaysOn availability group.</span></span> <span data-ttu-id="bdc77-104">このトピックでは、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 、 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]、または PowerShell を使用して、 [!INCLUDE[tsql](../../../includes/tsql-md.md)]の AlwaysOn 可用性グループの可用性レプリカに対して接続アクセスを構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="bdc77-104">This topic describes how to configure connection access on an availability replica of an AlwaysOn availability group in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or PowerShell.</span></span>  
  
 <span data-ttu-id="bdc77-105">セカンダリ レプリカに対して読み取り専用アクセスを有効にすることによる影響と、接続アクセスの概要については、「[可用性レプリカに対するクライアント接続アクセスについて &#40;SQL Server&#41;](about-client-connection-access-to-availability-replicas-sql-server.md)」および「[アクティブなセカンダリ: 読み取り可能なセカンダリ レプリカ &#40;AlwaysOn 可用性グループ&#41;](active-secondaries-readable-secondary-replicas-always-on-availability-groups.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bdc77-105">For information about the implications of enabling read-only access for a secondary replica and for an introduction to connection access, see [About Client Connection Access to Availability Replicas &#40;SQL Server&#41;](about-client-connection-access-to-availability-replicas-sql-server.md) and [Active Secondaries: Readable Secondary Replicas &#40;AlwaysOn Availability Groups&#41;](active-secondaries-readable-secondary-replicas-always-on-availability-groups.md).</span></span>  
  
  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="bdc77-106">はじめに</span><span class="sxs-lookup"><span data-stu-id="bdc77-106">Before You Begin</span></span>  
  
###  <a name="prerequisites-and-restrictions"></a><a name="Prerequisites"></a> <span data-ttu-id="bdc77-107">前提条件と制限</span><span class="sxs-lookup"><span data-stu-id="bdc77-107">Prerequisites and Restrictions</span></span>  
  
-   <span data-ttu-id="bdc77-108">別の接続アクセスを構成するには、プライマリ レプリカをホストするサーバー インスタンスに接続している必要があります。</span><span class="sxs-lookup"><span data-stu-id="bdc77-108">To configure different connection access, you must be connected to the server instance that hosts the primary replica.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="bdc77-109">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="bdc77-109">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="bdc77-110">Permissions</span><span class="sxs-lookup"><span data-stu-id="bdc77-110">Permissions</span></span>  
  
|<span data-ttu-id="bdc77-111">タスク</span><span class="sxs-lookup"><span data-stu-id="bdc77-111">Task</span></span>|<span data-ttu-id="bdc77-112">アクセス許可</span><span class="sxs-lookup"><span data-stu-id="bdc77-112">Permissions</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="bdc77-113">可用性グループの作成時にレプリカを構成する</span><span class="sxs-lookup"><span data-stu-id="bdc77-113">To configure replicas when creating an availability group</span></span>|<span data-ttu-id="bdc77-114">**sysadmin** 固定サーバー ロールのメンバーシップと、CREATE AVAILABILITY GROUP サーバー権限、ALTER ANY AVAILABILITY GROUP 権限、CONTROL SERVER 権限のいずれかが必要です。</span><span class="sxs-lookup"><span data-stu-id="bdc77-114">Requires membership in the **sysadmin** fixed server role and either CREATE AVAILABILITY GROUP server permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>|  
|<span data-ttu-id="bdc77-115">可用性レプリカを変更する</span><span class="sxs-lookup"><span data-stu-id="bdc77-115">To modify an availability replica</span></span>|<span data-ttu-id="bdc77-116">可用性グループの ALTER AVAILABILITY GROUP 権限、CONTROL AVAILABILITY GROUP 権限、ALTER ANY AVAILABILITY GROUP 権限、または CONTROL SERVER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="bdc77-116">Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>|  
  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="bdc77-117">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="bdc77-117">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="bdc77-118">**可用性レプリカに対してアクセスを構成するには**</span><span class="sxs-lookup"><span data-stu-id="bdc77-118">**To configure access on an availability replica**</span></span>  
  
1.  <span data-ttu-id="bdc77-119">オブジェクト エクスプローラーで、プライマリ レプリカをホストするサーバー インスタンスに接続し、サーバー ツリーを展開します。</span><span class="sxs-lookup"><span data-stu-id="bdc77-119">In Object Explorer, connect to the server instance that hosts the primary replica, and expand the server tree.</span></span>  
  
2.  <span data-ttu-id="bdc77-120">**[AlwaysOn 高可用性]** ノードと **[可用性グループ]** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="bdc77-120">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="bdc77-121">変更するレプリカが含まれる可用性グループをクリックします。</span><span class="sxs-lookup"><span data-stu-id="bdc77-121">Click the availability group whose replica you want to change.</span></span>  
  
4.  <span data-ttu-id="bdc77-122">可用性レプリカを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bdc77-122">Right-click the availability replica, and click **Properties**.</span></span>  
  
5.  <span data-ttu-id="bdc77-123">**[可用性レプリカ プロパティ]** ダイアログ ボックスで、プライマリ ロールおよびセカンダリ ロールの接続アクセスを、次のように変更できます。</span><span class="sxs-lookup"><span data-stu-id="bdc77-123">In the **Availability Replica Properties** dialog box, you can change the connection access for the primary role and for the secondary role, as follows:</span></span>  
  
    -   <span data-ttu-id="bdc77-124">セカンダリ ロールの場合は、 **[読み取り可能セカンダリ]** ボックスの一覧から新しい値を選択します。値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="bdc77-124">For the secondary role, select a new value from the **Readable secondary** drop list, as follows:</span></span>  
  
         <span data-ttu-id="bdc77-125">**いいえ**</span><span class="sxs-lookup"><span data-stu-id="bdc77-125">**No**</span></span>  
         <span data-ttu-id="bdc77-126">このレプリカのセカンダリ データベースに対するユーザー接続は禁止されます。</span><span class="sxs-lookup"><span data-stu-id="bdc77-126">No user connections are allowed to secondary databases of this replica.</span></span> <span data-ttu-id="bdc77-127">読み取りアクセスで利用することはできません。</span><span class="sxs-lookup"><span data-stu-id="bdc77-127">They are not available for read access.</span></span> <span data-ttu-id="bdc77-128">これが既定の設定です。</span><span class="sxs-lookup"><span data-stu-id="bdc77-128">This is the default setting.</span></span>  
  
         <span data-ttu-id="bdc77-129">**[読み取り目的のみ]**</span><span class="sxs-lookup"><span data-stu-id="bdc77-129">**Read-intent only**</span></span>  
         <span data-ttu-id="bdc77-130">このレプリカのセカンダリ データベースに対する接続は、読み取り専用でのみ許可されます。</span><span class="sxs-lookup"><span data-stu-id="bdc77-130">Only read-only connections are allowed to secondary databases of this replica.</span></span> <span data-ttu-id="bdc77-131">セカンダリ データベースはすべて読み取りアクセスで利用できます。</span><span class="sxs-lookup"><span data-stu-id="bdc77-131">The secondary database(s) are all available for read access.</span></span>  
  
         <span data-ttu-id="bdc77-132">**はい**</span><span class="sxs-lookup"><span data-stu-id="bdc77-132">**Yes**</span></span>  
         <span data-ttu-id="bdc77-133">読み取りアクセスに限り、このレプリカのセカンダリ データベースに対するすべての接続が許可されます。</span><span class="sxs-lookup"><span data-stu-id="bdc77-133">All connections are allowed to secondary databases of this replica, but only for read access.</span></span> <span data-ttu-id="bdc77-134">セカンダリ データベースはすべて読み取りアクセスで利用できます。</span><span class="sxs-lookup"><span data-stu-id="bdc77-134">The secondary database(s) are all available for read access.</span></span>  
  
    -   <span data-ttu-id="bdc77-135">プライマリ ロールの場合は、 **[プライマリ ロールの接続]** ボックスの一覧から新しい値を選択します。値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="bdc77-135">For the primary role, select a new value from the **Connections in primary role** drop list, as follows:</span></span>  
  
         <span data-ttu-id="bdc77-136">**[すべての接続を許可]**</span><span class="sxs-lookup"><span data-stu-id="bdc77-136">**Allow all connections**</span></span>  
         <span data-ttu-id="bdc77-137">プライマリ レプリカのデータベースに対するすべての接続が許可されます。</span><span class="sxs-lookup"><span data-stu-id="bdc77-137">All connections are allowed to the databases in the primary replica.</span></span> <span data-ttu-id="bdc77-138">これが既定の設定です。</span><span class="sxs-lookup"><span data-stu-id="bdc77-138">This is the default setting.</span></span>  
  
         <span data-ttu-id="bdc77-139">**[読み取り/書き込みの接続を許可]**</span><span class="sxs-lookup"><span data-stu-id="bdc77-139">**Allow read/write connections**</span></span>  
         <span data-ttu-id="bdc77-140">Application Intent プロパティが **ReadWrite** に設定されている場合、または Application Intent 接続プロパティが設定されていない場合は、接続が許可されます。</span><span class="sxs-lookup"><span data-stu-id="bdc77-140">When the Application Intent property is set to **ReadWrite** or the Application Intent connection property is not set, the connection is allowed.</span></span> <span data-ttu-id="bdc77-141">Application Intent 接続プロパティが **ReadOnly** に設定されている接続は許可されません。</span><span class="sxs-lookup"><span data-stu-id="bdc77-141">Connections where the Application Intent connection property is set to **ReadOnly** are not allowed.</span></span> <span data-ttu-id="bdc77-142">これにより、読み取りを目的としたワークロードが誤ってプライマリ レプリカに接続されるのを防ぐことができます。</span><span class="sxs-lookup"><span data-stu-id="bdc77-142">This can help prevent customers from connecting a read-intent work load to the primary replica by mistake.</span></span> <span data-ttu-id="bdc77-143">"アプリケーションの目的" 接続プロパティの詳細については、「 [Using Connection String Keywords with SQL Server Native Client](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bdc77-143">For more information about Application Intent connection property, see [Using Connection String Keywords with SQL Server Native Client](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).</span></span>  
  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="bdc77-144">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="bdc77-144">Using Transact-SQL</span></span>  
 <span data-ttu-id="bdc77-145">**可用性レプリカに対してアクセスを構成するには**</span><span class="sxs-lookup"><span data-stu-id="bdc77-145">**To configure access on an availability replica**</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bdc77-146">この手順の例については、このセクションの後半の「 [例 (Transact-SQL)](#TsqlExample)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bdc77-146">For an example of this procedure, see [Example (Transact-SQL)](#TsqlExample), later in this section.</span></span>  
  
1.  <span data-ttu-id="bdc77-147">プライマリ レプリカをホストするサーバー インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="bdc77-147">Connect to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="bdc77-148">新しい可用性グループのレプリカを指定する場合は、 [CREATE AVAILABILITY GROUP](/sql/t-sql/statements/create-availability-group-transact-sql)[!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="bdc77-148">If you are specifying a replica for a new availability group, use the [CREATE AVAILABILITY GROUP](/sql/t-sql/statements/create-availability-group-transact-sql)[!INCLUDE[tsql](../../../includes/tsql-md.md)] statement.</span></span> <span data-ttu-id="bdc77-149">既存の可用性グループのレプリカを追加または変更する場合は、 [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql)[!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="bdc77-149">If you are adding or modifying a replica of an existing availability group, use the [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql)[!INCLUDE[tsql](../../../includes/tsql-md.md)] statement.</span></span>  
  
    -   <span data-ttu-id="bdc77-150">セカンダリ ロールの接続アクセスを構成するには、ADD REPLICA 句または MODIFY REPLICA WITH 句で、SECONDARY_ROLE オプションを次のように指定します。</span><span class="sxs-lookup"><span data-stu-id="bdc77-150">To configure connection access for the secondary role, in the ADD REPLICA or MODIFY REPLICA WITH clause, specify the SECONDARY_ROLE option, as follows:</span></span>  
  
         <span data-ttu-id="bdc77-151">SECONDARY_ROLE **(** ALLOW_CONNECTIONS **=** { NO | READ_ONLY | ALL } **)**</span><span class="sxs-lookup"><span data-stu-id="bdc77-151">SECONDARY_ROLE **(** ALLOW_CONNECTIONS **=** { NO | READ_ONLY | ALL } **)**</span></span>  
  
         <span data-ttu-id="bdc77-152">パラメーターの説明</span><span class="sxs-lookup"><span data-stu-id="bdc77-152">where,</span></span>  
  
         <span data-ttu-id="bdc77-153">NO</span><span class="sxs-lookup"><span data-stu-id="bdc77-153">NO</span></span>  
         <span data-ttu-id="bdc77-154">このレプリカのセカンダリ データベースに対する直接接続は禁止されます。</span><span class="sxs-lookup"><span data-stu-id="bdc77-154">No direct connections are allowed to secondary databases of this replica.</span></span> <span data-ttu-id="bdc77-155">読み取りアクセスで利用することはできません。</span><span class="sxs-lookup"><span data-stu-id="bdc77-155">They are not available for read access.</span></span> <span data-ttu-id="bdc77-156">これが既定の設定です。</span><span class="sxs-lookup"><span data-stu-id="bdc77-156">This is the default setting.</span></span>  
  
         <span data-ttu-id="bdc77-157">READ_ONLY</span><span class="sxs-lookup"><span data-stu-id="bdc77-157">READ_ONLY</span></span>  
         <span data-ttu-id="bdc77-158">このレプリカのセカンダリ データベースに対する接続は、読み取り専用でのみ許可されます。</span><span class="sxs-lookup"><span data-stu-id="bdc77-158">Only read-only connections are allowed to secondary databases of this replica.</span></span> <span data-ttu-id="bdc77-159">セカンダリ データベースはすべて読み取りアクセスで利用できます。</span><span class="sxs-lookup"><span data-stu-id="bdc77-159">The secondary database(s) are all available for read access.</span></span>  
  
         <span data-ttu-id="bdc77-160">ALL</span><span class="sxs-lookup"><span data-stu-id="bdc77-160">ALL</span></span>  
         <span data-ttu-id="bdc77-161">読み取りアクセスに限り、このレプリカのセカンダリ データベースに対するすべての接続が許可されます。</span><span class="sxs-lookup"><span data-stu-id="bdc77-161">All connections are allowed to secondary databases of this replica, but only for read access.</span></span> <span data-ttu-id="bdc77-162">セカンダリ データベースはすべて読み取りアクセスで利用できます。</span><span class="sxs-lookup"><span data-stu-id="bdc77-162">The secondary database(s) are all available for read access.</span></span>  
  
3.  <span data-ttu-id="bdc77-163">プライマリ ロールの接続アクセスを構成するには、ADD REPLICA 句または MODIFY REPLICA WITH 句で、PRIMARY_ROLE オプションを次のように指定します。</span><span class="sxs-lookup"><span data-stu-id="bdc77-163">To configure connection access for the primary role, in the ADD REPLICA or MODIFY REPLICA WITH clause, specify the PRIMARY_ROLE option, as follows:</span></span>  
  
     <span data-ttu-id="bdc77-164">PRIMARY_ROLE **(** ALLOW_CONNECTIONS **=** { READ_WRITE | ALL } **)**</span><span class="sxs-lookup"><span data-stu-id="bdc77-164">PRIMARY_ROLE **(** ALLOW_CONNECTIONS **=** { READ_WRITE | ALL } **)**</span></span>  
  
     <span data-ttu-id="bdc77-165">パラメーターの説明</span><span class="sxs-lookup"><span data-stu-id="bdc77-165">where,</span></span>  
  
     <span data-ttu-id="bdc77-166">READ_WRITE</span><span class="sxs-lookup"><span data-stu-id="bdc77-166">READ_WRITE</span></span>  
     <span data-ttu-id="bdc77-167">Application Intent 接続プロパティが **ReadOnly** に設定されている接続は許可されません。</span><span class="sxs-lookup"><span data-stu-id="bdc77-167">Connections where the Application Intent connection property is set to **ReadOnly** are disallowed.</span></span>  <span data-ttu-id="bdc77-168">Application Intent プロパティが **ReadWrite** に設定されている場合、または Application Intent 接続プロパティが設定されていない場合は、接続が許可されます。</span><span class="sxs-lookup"><span data-stu-id="bdc77-168">When the Application Intent property is set to **ReadWrite** or the Application Intent connection property is not set, the connection is allowed.</span></span> <span data-ttu-id="bdc77-169">"アプリケーションの目的" 接続プロパティの詳細については、「 [Using Connection String Keywords with SQL Server Native Client](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bdc77-169">For more information about Application Intent connection property, see [Using Connection String Keywords with SQL Server Native Client](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).</span></span>  
  
     <span data-ttu-id="bdc77-170">ALL</span><span class="sxs-lookup"><span data-stu-id="bdc77-170">ALL</span></span>  
     <span data-ttu-id="bdc77-171">プライマリ レプリカのデータベースに対するすべての接続が許可されます。</span><span class="sxs-lookup"><span data-stu-id="bdc77-171">All connections are allowed to the databases in the primary replica.</span></span> <span data-ttu-id="bdc77-172">これが既定の設定です。</span><span class="sxs-lookup"><span data-stu-id="bdc77-172">This is the default setting.</span></span>  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="bdc77-173">例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="bdc77-173">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="bdc77-174">次の例では、セカンダリ レプリカを *AG2*という名前の可用性グループに追加します。</span><span class="sxs-lookup"><span data-stu-id="bdc77-174">The following example adds a secondary replica to an availability group named *AG2*.</span></span> <span data-ttu-id="bdc77-175">新しい可用性レプリカをホストするため、スタンドアロン サーバー インスタンスの *COMPUTER03\HADR_INSTANCE*が指定されています。</span><span class="sxs-lookup"><span data-stu-id="bdc77-175">A stand-alone server instance, *COMPUTER03\HADR_INSTANCE*, is specified to host the new availability replica.</span></span> <span data-ttu-id="bdc77-176">このレプリカは、プライマリ ロールに対してのみ読み取り/書き込み接続を許可し、セカンダリ ロールに対しては読み取りを目的とした接続のみを許可するように構成されています。</span><span class="sxs-lookup"><span data-stu-id="bdc77-176">This replica configured to allow only read-write connections for the primary role and to allow only read-intent connections for secondary role.</span></span>  
  
```sql
ALTER AVAILABILITY GROUP AG2   
   ADD REPLICA ON   
      'COMPUTER03\HADR_INSTANCE' WITH   
         (  
         ENDPOINT_URL = 'TCP://COMPUTER03:7022',  
         PRIMARY_ROLE ( ALLOW_CONNECTIONS = READ_WRITE ),  
         SECONDARY_ROLE (ALLOW_CONNECTIONS = READ_ONLY )  
         );   
GO  
```  
  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="bdc77-177">PowerShell の使用</span><span class="sxs-lookup"><span data-stu-id="bdc77-177">Using PowerShell</span></span>  

### <a name="to-configure-access-on-an-availability-replica"></a><span data-ttu-id="bdc77-178">可用性レプリカに対してアクセスを構成するには</span><span class="sxs-lookup"><span data-stu-id="bdc77-178">To configure access on an availability replica</span></span>
  
> [!NOTE]  
>  <span data-ttu-id="bdc77-179">コード例については、このセクションで後述する PowerShell の例を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bdc77-179">For a code example, see the PowerShell examples later in this section.</span></span>  
  
1.  <span data-ttu-id="bdc77-180">プライマリ レプリカをホストするサーバー インスタンスにディレクトリを変更 (`cd`) します。</span><span class="sxs-lookup"><span data-stu-id="bdc77-180">Change directory (`cd`) to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="bdc77-181">可用性グループに可用性レプリカを追加する場合は、`New-SqlAvailabilityReplica` コマンドレットを使用します。</span><span class="sxs-lookup"><span data-stu-id="bdc77-181">When adding an availability replica to an availability group, use the `New-SqlAvailabilityReplica` cmdlet.</span></span> <span data-ttu-id="bdc77-182">既存の可用性レプリカを変更する場合は、`Set-SqlAvailabilityReplica` コマンドレットを使用します。</span><span class="sxs-lookup"><span data-stu-id="bdc77-182">When modifying an existing availability replica, use the `Set-SqlAvailabilityReplica` cmdlet.</span></span> <span data-ttu-id="bdc77-183">関連するパラメーターは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="bdc77-183">The relevant parameters are as follows:</span></span>  
  
    -   <span data-ttu-id="bdc77-184">セカンダリロールの接続アクセスを構成するには、 `ConnectionModeInSecondaryRole` *secondary_role_keyword*パラメーターを指定します。 *secondary_role_keyword*は次のいずれかの値になります。</span><span class="sxs-lookup"><span data-stu-id="bdc77-184">To configure connection access for the secondary role, specify the `ConnectionModeInSecondaryRole`*secondary_role_keyword* parameter, where *secondary_role_keyword* equals one of the following values:</span></span>  
  
         `AllowNoConnections`  
         <span data-ttu-id="bdc77-185">セカンダリ レプリカのデータベースに対する直接接続は許可されず、データベースに対して読み取りアクセスを実行できません。</span><span class="sxs-lookup"><span data-stu-id="bdc77-185">No direct connections are allowed to the databases in the secondary replica and the databases are not available for read access.</span></span> <span data-ttu-id="bdc77-186">これが既定の設定です。</span><span class="sxs-lookup"><span data-stu-id="bdc77-186">This is the default setting.</span></span>  
  
         `AllowReadIntentConnectionsOnly`  
         <span data-ttu-id="bdc77-187">Application Intent プロパティが **ReadOnly**に設定されている場合に限り、セカンダリ レプリカのデータベースに対する接続が許可されます。</span><span class="sxs-lookup"><span data-stu-id="bdc77-187">Connections are allowed only to the databases in the secondary replica where the Application Intent property is set to **ReadOnly**.</span></span> <span data-ttu-id="bdc77-188">このプロパティの詳細については、「 [Using Connection String Keywords with SQL Server Native Client](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bdc77-188">For more information about this property, see [Using Connection String Keywords with SQL Server Native Client](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).</span></span>  
  
         `AllowAllConnections`  
         <span data-ttu-id="bdc77-189">読み取り専用アクセスに限り、セカンダリ レプリカのデータベースに対するすべての接続が許可されます。</span><span class="sxs-lookup"><span data-stu-id="bdc77-189">All connections are allowed to the databases in the secondary replica for read-only access.</span></span>  
  
    -   <span data-ttu-id="bdc77-190">プライマリロールの接続アクセスを構成するには、primary_role_keyword を指定し `ConnectionModeInPrimaryRole` *primary_role_keyword*ます。 *primary_role_keyword*は次のいずれかの値になります。</span><span class="sxs-lookup"><span data-stu-id="bdc77-190">To configure connection access for the primary role, specify `ConnectionModeInPrimaryRole`*primary_role_keyword*, where *primary_role_keyword* equals one of the following values:</span></span>  
  
         `AllowReadWriteConnections`  
         <span data-ttu-id="bdc77-191">Application Intent 接続プロパティが ReadOnly に設定されている接続は許可されません。</span><span class="sxs-lookup"><span data-stu-id="bdc77-191">Connections where the Application Intent connection property is set to ReadOnly are disallowed.</span></span> <span data-ttu-id="bdc77-192">Application Intent プロパティが ReadWrite に設定されている場合、または Application Intent 接続プロパティが設定されていない場合は、接続が許可されます。</span><span class="sxs-lookup"><span data-stu-id="bdc77-192">When the Application Intent property is set to ReadWrite or the Application Intent connection property is not set, the connection is allowed.</span></span> <span data-ttu-id="bdc77-193">"アプリケーションの目的" 接続プロパティの詳細については、「 [Using Connection String Keywords with SQL Server Native Client](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bdc77-193">For more information about Application Intent connection property, see [Using Connection String Keywords with SQL Server Native Client](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).</span></span>  
  
         `AllowAllConnections`  
         <span data-ttu-id="bdc77-194">プライマリ レプリカのデータベースに対するすべての接続が許可されます。</span><span class="sxs-lookup"><span data-stu-id="bdc77-194">All connections are allowed to the databases in the primary replica.</span></span> <span data-ttu-id="bdc77-195">これが既定の設定です。</span><span class="sxs-lookup"><span data-stu-id="bdc77-195">This is the default setting.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="bdc77-196">コマンドレットの構文を表示するには、[!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] PowerShell 環境で `Get-Help` コマンドレットを使用します。</span><span class="sxs-lookup"><span data-stu-id="bdc77-196">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] PowerShell environment.</span></span> <span data-ttu-id="bdc77-197">詳細については、「 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bdc77-197">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
<span data-ttu-id="bdc77-198">SQL Server PowerShell プロバイダーを設定して使用する方法については、「 [SQL Server PowerShell プロバイダー](../../../powershell/sql-server-powershell-provider.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bdc77-198">To set up and use the SQL Server PowerShell provider, see [SQL Server PowerShell Provider](../../../powershell/sql-server-powershell-provider.md).</span></span>
  
<span data-ttu-id="bdc77-199">以下の例は、`ConnectionModeInSecondaryRole` パラメーターと `ConnectionModeInPrimaryRole` パラメーターの両方を `AllowAllConnections` に設定しています。</span><span class="sxs-lookup"><span data-stu-id="bdc77-199">The following example, sets the both the `ConnectionModeInSecondaryRole` and `ConnectionModeInPrimaryRole` parameters to `AllowAllConnections`.</span></span>  
  
```powershell
Set-Location SQLSERVER:\SQL\PrimaryServer\default\AvailabilityGroups\MyAg  
$primaryReplica = Get-Item "AvailabilityReplicas\PrimaryServer"  

Set-SqlAvailabilityReplica -ConnectionModeInSecondaryRole "AllowAllConnections" `
 -InputObject $primaryReplica  
Set-SqlAvailabilityReplica -ConnectionModeInPrimaryRole "AllowAllConnections" `
-InputObject $primaryReplica
```  

##  <a name="follow-up-after-configuring-read-only-access-for-an-availability-replica"></a><a name="FollowUp"></a><span data-ttu-id="bdc77-200">補足情報: 可用性レプリカに対する読み取り専用アクセスの構成後</span><span class="sxs-lookup"><span data-stu-id="bdc77-200">Follow Up: After Configuring Read-Only Access for an Availability Replica</span></span>  
 <span data-ttu-id="bdc77-201">**読み取り可能なセカンダリ レプリカに対する読み取り専用アクセス**</span><span class="sxs-lookup"><span data-stu-id="bdc77-201">**Read-only access to a readable secondary replica**</span></span>  
  
-   <span data-ttu-id="bdc77-202">[Bcp ユーティリティ](../../../tools/bcp-utility.md)または[sqlcmd ユーティリティ](../../../tools/sqlcmd-utility.md)を使用する場合は、スイッチを指定することによって、読み取り専用アクセスが有効になっている任意のセカンダリレプリカへの読み取り専用アクセスを指定でき `-K ReadOnly` ます。</span><span class="sxs-lookup"><span data-stu-id="bdc77-202">When using the [bcp Utility](../../../tools/bcp-utility.md) or [sqlcmd Utility](../../../tools/sqlcmd-utility.md), you can specify read-only access to any secondary replica that is enabled for read-only access by specifying the `-K ReadOnly` switch.</span></span>  
  
-   <span data-ttu-id="bdc77-203">読み取り可能なセカンダリ レプリカに接続するクライアント アプリケーションを有効にするには:</span><span class="sxs-lookup"><span data-stu-id="bdc77-203">To enable client applications to connect to readable secondary replicas:</span></span>  
  
    ||<span data-ttu-id="bdc77-204">前提条件</span><span class="sxs-lookup"><span data-stu-id="bdc77-204">Prerequisite</span></span>|<span data-ttu-id="bdc77-205">Link</span><span class="sxs-lookup"><span data-stu-id="bdc77-205">Link</span></span>|  
    |-|------------------|----------|  
    |<span data-ttu-id="bdc77-206">![Checkbox](../../media/checkboxemptycenterxtraspacetopandright.gif "Checkbox")</span><span class="sxs-lookup"><span data-stu-id="bdc77-206">![Checkbox](../../media/checkboxemptycenterxtraspacetopandright.gif "Checkbox")</span></span>|<span data-ttu-id="bdc77-207">可用性グループにリスナーがあることを確認する。</span><span class="sxs-lookup"><span data-stu-id="bdc77-207">Ensure that the availability group has a listener.</span></span>|[<span data-ttu-id="bdc77-208">可用性グループ リスナーの作成または構成 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="bdc77-208">Create or Configure an Availability Group Listener &#40;SQL Server&#41;</span></span>](create-or-configure-an-availability-group-listener-sql-server.md)|  
    |<span data-ttu-id="bdc77-209">![Checkbox](../../media/checkboxemptycenterxtraspacetopandright.gif "Checkbox")</span><span class="sxs-lookup"><span data-stu-id="bdc77-209">![Checkbox](../../media/checkboxemptycenterxtraspacetopandright.gif "Checkbox")</span></span>|<span data-ttu-id="bdc77-210">可用性グループの読み取り専用ルーティングを構成する。</span><span class="sxs-lookup"><span data-stu-id="bdc77-210">Configure read-only routing for the availability group.</span></span>|[<span data-ttu-id="bdc77-211">可用性グループの読み取り専用ルーティングの構成 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="bdc77-211">Configure Read-Only Routing for an Availability Group &#40;SQL Server&#41;</span></span>](configure-read-only-routing-for-an-availability-group-sql-server.md)|  
  
 <span data-ttu-id="bdc77-212">**フェールオーバー後にトリガーとジョブに影響する可能性がある要因**</span><span class="sxs-lookup"><span data-stu-id="bdc77-212">**Factors that might affect triggers and jobs after a failover**</span></span>  
  
 <span data-ttu-id="bdc77-213">読み取り可能でないセカンダリ データベースまたは読み取り可能なセカンダリ データベースで実行されたときに失敗するトリガーとジョブがある場合は、トリガーとジョブをスクリプト化して、特定のレプリカに対して、データベースがプライマリ データベースか読み取り可能なセカンダリ データベースかを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bdc77-213">If you have triggers and jobs that will fail when running on a non-readable secondary database or on a readable secondary database, you need to script the triggers and jobs to check on a given replica to determine whether the database is a primary database or is a readable secondary database.</span></span> <span data-ttu-id="bdc77-214">この情報を入手するには、データベースの [Updatability](/sql/t-sql/functions/databasepropertyex-transact-sql) プロパティを返す **DATABASEPROPERTYEX** 関数を使用します。</span><span class="sxs-lookup"><span data-stu-id="bdc77-214">To obtain this information, use the [DATABASEPROPERTYEX](/sql/t-sql/functions/databasepropertyex-transact-sql) function to return the **Updatability** property of the database.</span></span> <span data-ttu-id="bdc77-215">読み取り専用データベースを識別するには、次のように、値として READ_ONLY を指定します。</span><span class="sxs-lookup"><span data-stu-id="bdc77-215">To identify a read-only database, specify READ_ONLY as the value, as follows:</span></span>  
  
```  
DATABASEPROPERTYEX([db name],'Updatability') = N'READ_ONLY'  
```  
  
 <span data-ttu-id="bdc77-216">読み取り/書き込みデータベースを識別するには、値として READ_WRITE を指定します。</span><span class="sxs-lookup"><span data-stu-id="bdc77-216">To identify a read-write database, specify READ_WRITE as the value.</span></span>  
  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="bdc77-217">関連タスク</span><span class="sxs-lookup"><span data-stu-id="bdc77-217">Related Tasks</span></span>  
  
-   [<span data-ttu-id="bdc77-218">可用性グループの読み取り専用ルーティングの構成 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="bdc77-218">Configure Read-Only Routing for an Availability Group &#40;SQL Server&#41;</span></span>](configure-read-only-routing-for-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="bdc77-219">可用性グループ リスナーの作成または構成 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="bdc77-219">Create or Configure an Availability Group Listener &#40;SQL Server&#41;</span></span>](create-or-configure-an-availability-group-listener-sql-server.md)  
  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="bdc77-220">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="bdc77-220">Related Content</span></span>  
  
-   [<span data-ttu-id="bdc77-221">Always On:読み取り可能なセカンダリの価格提案</span><span class="sxs-lookup"><span data-stu-id="bdc77-221">Always On: Value Proposition of Readable Secondary</span></span>](https://docs.microsoft.com/archive/blogs/sqlserverstorageengine/alwayson-value-proposition-of-readable-secondary)  
  
-   [<span data-ttu-id="bdc77-222">Always On:読み取りワークロードのセカンダリ レプリカを有効にするオプションが 2 つ存在する理由</span><span class="sxs-lookup"><span data-stu-id="bdc77-222">Always On: Why there are two options to enable a secondary replica for read workload?</span></span>](https://docs.microsoft.com/archive/blogs/sqlserverstorageengine/alwayson-why-there-are-two-options-to-enable-a-secondary-replica-for-read-workload)  
  
-   [<span data-ttu-id="bdc77-223">Always On:読み取り可能なセカンダリ レプリカのセットアップ</span><span class="sxs-lookup"><span data-stu-id="bdc77-223">Always On: Setting up Readable Secondary Replica</span></span>](https://docs.microsoft.com/archive/blogs/sqlserverstorageengine/alwayson-setting-up-readable-seconary-replica)  
  
-   [<span data-ttu-id="bdc77-224">Always On:読み取り可能なセカンダリを有効にしたばかりだが、クエリがブロックされる</span><span class="sxs-lookup"><span data-stu-id="bdc77-224">Always On: I just enabled Readable Secondary but my query is blocked?</span></span>](https://docs.microsoft.com/archive/blogs/sqlserverstorageengine/alwayson-i-just-enabled-readable-secondary-but-my-query-is-blocked)  
  
-   [<span data-ttu-id="bdc77-225">Always On:読み取り可能なセカンダリ、読み取り専用のデータベース、データベースのスナップショットで最新の統計情報を取得できるようにする</span><span class="sxs-lookup"><span data-stu-id="bdc77-225">Always On: Making latest statistics available on Readable Secondary, Read-Only database and Database Snapshot</span></span>](https://docs.microsoft.com/archive/blogs/sqlserverstorageengine/alwayson-making-latest-statistics-available-on-readable-secondary-read-only-database-and-database-snapshot)  
  
-   [<span data-ttu-id="bdc77-226">Always On:読み取り専用のデータベース、データベースのスナップショット、セカンダリ レプリカでの統計に関する課題</span><span class="sxs-lookup"><span data-stu-id="bdc77-226">Always On: Challenges with statistics on ReadOnly database, Database Snapshot and Secondary Replica</span></span>](https://docs.microsoft.com/archive/blogs/sqlserverstorageengine/alwayson-challenges-with-statistics-on-readonly-database-database-snapshot-and-secondary-replica)  
  
-   [<span data-ttu-id="bdc77-227">Always On:セカンダリ レプリカでレポート ワークロードを実行した場合にプライマリ ワークロードに及ぶ影響</span><span class="sxs-lookup"><span data-stu-id="bdc77-227">Always On: Impact on the primary workload when you run reporting workload on the secondary replica</span></span>](https://docs.microsoft.com/archive/blogs/sqlserverstorageengine/alwayson-impact-on-the-primary-workload-when-you-run-reporting-workload-on-the-secondary-replica)  
  
-   [<span data-ttu-id="bdc77-228">Always On:読み取り可能なセカンダリのレポート ワークロードをスナップショット分離にマップした場合の影響</span><span class="sxs-lookup"><span data-stu-id="bdc77-228">Always On: Impact of mapping reporting workload on Readable Secondary to Snapshot Isolation</span></span>](https://docs.microsoft.com/archive/blogs/sqlserverstorageengine/alwayson-impact-of-mapping-reporting-workload-on-readable-secondary-to-snapshot-isolation)  
  
-   [<span data-ttu-id="bdc77-229">Always On:セカンダリ レプリカでレポート ワークロードを実行する場合に再実行スレッドのブロッキングを最小限に抑える</span><span class="sxs-lookup"><span data-stu-id="bdc77-229">Always On: Minimizing blocking of REDO thread when running reporting workload on Secondary Replica</span></span>](https://docs.microsoft.com/archive/blogs/sqlserverstorageengine/alwayson-minimizing-blocking-of-redo-thread-when-running-reporting-workload-on-secondary-replica)  
  
-   [<span data-ttu-id="bdc77-230">Always On:読み取り可能なセカンダリとデータ待機時間</span><span class="sxs-lookup"><span data-stu-id="bdc77-230">Always On: Readable Secondary and data latency</span></span>](https://docs.microsoft.com/archive/blogs/sqlserverstorageengine/alwayson-readable-secondary-and-data-latency)  
  
## <a name="see-also"></a><span data-ttu-id="bdc77-231">参照</span><span class="sxs-lookup"><span data-stu-id="bdc77-231">See Also</span></span>  
 <span data-ttu-id="bdc77-232">[AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="bdc77-232">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="bdc77-233">アクティブなセカンダリ: 読み取り可能なセカンダリレプリカ &#40;AlwaysOn 可用性グループ&#41;</span><span class="sxs-lookup"><span data-stu-id="bdc77-233">Active Secondaries: Readable Secondary Replicas &#40;AlwaysOn Availability Groups&#41;</span></span>](active-secondaries-readable-secondary-replicas-always-on-availability-groups.md)  
 [<span data-ttu-id="bdc77-234">可用性レプリカに対するクライアント接続アクセスについて &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="bdc77-234">About Client Connection Access to Availability Replicas &#40;SQL Server&#41;</span></span>](about-client-connection-access-to-availability-replicas-sql-server.md)  
