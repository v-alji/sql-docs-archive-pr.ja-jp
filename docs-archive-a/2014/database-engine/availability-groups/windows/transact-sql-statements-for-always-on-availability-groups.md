---
title: AlwaysOn 可用性グループの Transact-sql ステートメントの概要 (SQL Server) |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], about
- Availability Groups [SQL Server], Transact-SQL statements
ms.assetid: 184d0a81-2259-4db9-9d0d-01aac0b502c8
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ff25fecf54cfdd1d9c03d1586f0272896542bfa7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741286"
---
# <a name="overview-of-transact-sql-statements-for-alwayson-availability-groups-sql-server"></a><span data-ttu-id="8d83b-102">AlwaysOn 可用性グループの Transact-SQL ステートメントの概要 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="8d83b-102">Overview of Transact-SQL Statements for AlwaysOn Availability Groups (SQL Server)</span></span>
  <span data-ttu-id="8d83b-103">このトピックでは、 [!INCLUDE[tsql](../../../includes/tsql-md.md)] の配置のほか、可用性グループ、可用性レプリカ、および可用性データベースの作成と管理をサポートする [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] ステートメントについて説明します。</span><span class="sxs-lookup"><span data-stu-id="8d83b-103">This topic introduces the [!INCLUDE[tsql](../../../includes/tsql-md.md)] statements that support deploying [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] and creating and managing an given availability group, availability replica and availability database.</span></span>  
  
  
##  <a name="create-endpoint"></a><a name="CreateEndpoint"></a><span data-ttu-id="8d83b-104">エンドポイントの作成</span><span class="sxs-lookup"><span data-stu-id="8d83b-104">CREATE ENDPOINT</span></span>  
 <span data-ttu-id="8d83b-105">[エンドポイントの作成...](/sql/t-sql/statements/create-endpoint-transact-sql)では、サーバーインスタンスにデータベースミラーリングエンドポイントが存在しない場合、DATABASE_MIRRORING によって作成されます。</span><span class="sxs-lookup"><span data-stu-id="8d83b-105">[CREATE ENDPOINT ... FOR DATABASE_MIRRORING](/sql/t-sql/statements/create-endpoint-transact-sql) creates a database mirroring endpoint, if none exists on the server instance.</span></span> <span data-ttu-id="8d83b-106">[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] またはデータベース ミラーリングの配置を検討しているすべてのサーバー インスタンスには、データベース ミラーリング エンドポイントが必要です。</span><span class="sxs-lookup"><span data-stu-id="8d83b-106">Every server instance on which you intend to deploy [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] or database mirroring requires a database mirroring endpoint.</span></span>  
  
 <span data-ttu-id="8d83b-107">このステートメントは、エンドポイントの作成先となるサーバー インスタンス上で実行します。</span><span class="sxs-lookup"><span data-stu-id="8d83b-107">Execute this statement on the server instance on which you are creating the endpoint.</span></span> <span data-ttu-id="8d83b-108">特定のサーバー インスタンスに対して作成できるデータベース ミラーリング エンドポイントは 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="8d83b-108">You can create only one database mirroring endpoint on a given server instance.</span></span> <span data-ttu-id="8d83b-109">詳細については、「 [データベース ミラーリング エンドポイント &#40;SQL Server&#41;](../../database-mirroring/the-database-mirroring-endpoint-sql-server.md)のインスタンスに AlwaysOn 可用性グループを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="8d83b-109">For more information, see [The Database Mirroring Endpoint &#40;SQL Server&#41;](../../database-mirroring/the-database-mirroring-endpoint-sql-server.md).</span></span>  
  
##  <a name="create-availability-group"></a><a name="CreateAG"></a><span data-ttu-id="8d83b-110">可用性グループの作成</span><span class="sxs-lookup"><span data-stu-id="8d83b-110">CREATE AVAILABILITY GROUP</span></span>  
 <span data-ttu-id="8d83b-111">[CREATE AVAILABILITY GROUP](/sql/t-sql/statements/create-availability-group-transact-sql) は、新しい可用性グループと、必要に応じて可用性グループのリスナーを作成します。</span><span class="sxs-lookup"><span data-stu-id="8d83b-111">[CREATE AVAILABILITY GROUP](/sql/t-sql/statements/create-availability-group-transact-sql) creates a new availability group and optionally an availability group listener.</span></span> <span data-ttu-id="8d83b-112">少なくとも、初期プライマリ レプリカとなるローカル サーバー インスタンスを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8d83b-112">Minimally, you must specify your local server instance, which will become the initial primary replica.</span></span> <span data-ttu-id="8d83b-113">必要に応じて、セカンダリ レプリカを 4 つまで指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="8d83b-113">Optionally, you can also specify up to four secondary replicas.</span></span>  
  
 <span data-ttu-id="8d83b-114">新しい可用性グループの初期プライマリ レプリカをホストする [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスで CREATE AVAILABILITY GROUP を実行します。</span><span class="sxs-lookup"><span data-stu-id="8d83b-114">Execute CREATE AVAILABILITY GROUP on the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that you want to host the initial primary replica of your new availability group.</span></span> <span data-ttu-id="8d83b-115">このサーバーインスタンスは、Windows Server フェールオーバークラスター (WSFC) のノードに存在する必要があります (詳細については、「 [AlwaysOn 可用性グループ &#40;SQL Server&#41;の前提条件、制限事項、および推奨事項](prereqs-restrictions-recommendations-always-on-availability.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8d83b-115">This server instance must reside on a node of a Windows Server Failover Cluster (WSFC) (for more information, see [Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md).</span></span>  
  
##  <a name="alter-availability-group"></a><a name="AlterAG"></a><span data-ttu-id="8d83b-116">可用性グループの変更</span><span class="sxs-lookup"><span data-stu-id="8d83b-116">ALTER AVAILABILITY GROUP</span></span>  
 <span data-ttu-id="8d83b-117">[ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) は、既存の可用性グループまたは可用性グループ リスナーの変更と、可用性グループのフェールオーバーをサポートします。</span><span class="sxs-lookup"><span data-stu-id="8d83b-117">[ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) supports changing an existing availability group or availability group listener and for failing over an availability group.</span></span>  
  
 <span data-ttu-id="8d83b-118">現在のプライマリ レプリカをホストする [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスで ALTER AVAILABILITY GROUP を実行します。</span><span class="sxs-lookup"><span data-stu-id="8d83b-118">Execute ALTER AVAILABILITY GROUP on the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that hosts the current primary replica.</span></span>  
  
##  <a name="alter-database--set-hadr-"></a><a name="AlterDb"></a><span data-ttu-id="8d83b-119">データベースの変更...HADR の設定...</span><span class="sxs-lookup"><span data-stu-id="8d83b-119">ALTER DATABASE ... SET HADR ...</span></span>  
 <span data-ttu-id="8d83b-120">ALTER DATABASE ステートメントの [SET HADR](/sql/t-sql/statements/alter-database-transact-sql-set-hadr) 句のオプションを使用すると、セカンダリ データベースを対応するプライマリ データベースの可用性グループに参加させたり、参加データベースを削除したりできます。さらに、参加データベースでのデータ同期化の削除やデータ同期化の再開も行うことができます。</span><span class="sxs-lookup"><span data-stu-id="8d83b-120">The options of the [SET HADR](/sql/t-sql/statements/alter-database-transact-sql-set-hadr) clause of the ALTER DATABASE statement enables you to join a secondary database to the availability group of the corresponding primary database, remove a joined database, and suspend data synchronization on a joined database, and resume data synchronization.</span></span>  
  
##  <a name="drop-availability-group"></a><a name="DropAG"></a><span data-ttu-id="8d83b-121">可用性グループの削除</span><span class="sxs-lookup"><span data-stu-id="8d83b-121">DROP AVAILABILITY GROUP</span></span>  
 <span data-ttu-id="8d83b-122">[DROP AVAILABILITY GROUP](/sql/t-sql/statements/drop-availability-group-transact-sql) は、指定された可用性グループとそのすべてのレプリカを削除します。</span><span class="sxs-lookup"><span data-stu-id="8d83b-122">[DROP AVAILABILITY GROUP](/sql/t-sql/statements/drop-availability-group-transact-sql) removes a specified availability group and all of its replicas.</span></span> <span data-ttu-id="8d83b-123">DROP AVAILABILITY GROUP は、WSFC フェールオーバー クラスター内の任意の [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] ノードから実行できます。</span><span class="sxs-lookup"><span data-stu-id="8d83b-123">DROP AVAILABILITY GROUP can be run from any [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] node in the WSFC failover cluster.</span></span>  
  
##  <a name="restrictions-on-the-availability-group-transact-sql-statements"></a><a name="Restrictions"></a><span data-ttu-id="8d83b-124">可用性グループの Transact-sql ステートメントに関する制限事項</span><span class="sxs-lookup"><span data-stu-id="8d83b-124">Restrictions on the AVAILABILITY GROUP Transact-SQL Statements</span></span>  
 <span data-ttu-id="8d83b-125">CREATE AVAILABILITY GROUP、ALTER AVAILABILITY GROUP、および DROP AVAILABILITY GROUP の各 [!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメントには、次の制限があります。</span><span class="sxs-lookup"><span data-stu-id="8d83b-125">The CREATE AVAILABILITY GROUP, ALTER AVAILABILITY GROUP, and DROP AVAILABILITY GROUP [!INCLUDE[tsql](../../../includes/tsql-md.md)] statements have the following limitations:</span></span>  
  
-   <span data-ttu-id="8d83b-126">DROP AVAILABILITY GROUP を除き、これらのステートメントを実行するには、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンス上で HADR サービスが有効になっている必要があります。</span><span class="sxs-lookup"><span data-stu-id="8d83b-126">With the exception of DROP AVAILABILITY GROUP, executing these statements requires that the HADR service is enabled on the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="8d83b-127">詳細については、「[AlwaysOn 可用性グループの有効化と無効化 &#40;SQL Server&#41;](enable-and-disable-always-on-availability-groups-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8d83b-127">For more information, see [Enable and Disable AlwaysOn Availability Groups &#40;SQL Server&#41;](enable-and-disable-always-on-availability-groups-sql-server.md).</span></span>  
  
-   <span data-ttu-id="8d83b-128">これらのステートメントは、トランザクションまたはバッチ内で実行することはできません。</span><span class="sxs-lookup"><span data-stu-id="8d83b-128">These statements cannot be executed within transactions or batches.</span></span>  
  
-   <span data-ttu-id="8d83b-129">障害発生後のクリーンアップについてはベスト エフォートとなります。これらのステートメントでは、障害発生時にすべての変更が確実にロールバックされるという保証はありません。</span><span class="sxs-lookup"><span data-stu-id="8d83b-129">Though they make a best effort to clean up after a failure, these statements do not guarantee that they will roll back all changes on failure.</span></span> <span data-ttu-id="8d83b-130">ただし、システム的には、クリーンに処理し、部分的な障害については無視するようになっています。</span><span class="sxs-lookup"><span data-stu-id="8d83b-130">However, systems should be able cleanly handle and then ignore partial failures.</span></span>  
  
-   <span data-ttu-id="8d83b-131">これらのステートメントは、式または変数をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="8d83b-131">These statements do not support expressions or variables.</span></span>  
  
-   <span data-ttu-id="8d83b-132">[!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメントを実行したときに、別の可用性グループ アクションまたは復旧が進行中であった場合は、エラーが返されます。</span><span class="sxs-lookup"><span data-stu-id="8d83b-132">If a [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement is executed while another availability group action or recovery is in process, the statement returns an error.</span></span> <span data-ttu-id="8d83b-133">必要に応じて、アクションまたは復旧の完了を待ってステートメントを再試行してください。</span><span class="sxs-lookup"><span data-stu-id="8d83b-133">Wait for the action or recovery to complete, and retry the statement, if necessary.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d83b-134">参照</span><span class="sxs-lookup"><span data-stu-id="8d83b-134">See Also</span></span>  
 [<span data-ttu-id="8d83b-135">AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;</span><span class="sxs-lookup"><span data-stu-id="8d83b-135">Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](overview-of-always-on-availability-groups-sql-server.md)  
  
  
