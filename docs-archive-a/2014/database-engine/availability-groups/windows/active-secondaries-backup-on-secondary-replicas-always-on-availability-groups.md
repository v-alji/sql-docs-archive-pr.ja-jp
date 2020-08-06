---
title: 'アクティブなセカンダリ: セカンダリレプリカでのバックアップ (Always On 可用性グループ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- backup priority
- backup on secondary replicas
- Availability Groups [SQL Server], availability replicas
- Availability Groups [SQL Server], backup on secondary replicas
- active secondary replicas [SQL Server], backup on
- automated backup preference
- Availability Groups [SQL Server], active secondary replicas
ms.assetid: 82afe51b-71d1-4d5b-b20a-b57afc002405
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0cf899cdbeb1ae4ede6c9196b8eb93a9d9e54f05
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716849"
---
# <a name="active-secondaries-backup-on-secondary-replicas-always-on-availability-groups"></a><span data-ttu-id="12585-102">アクティブなセカンダリ: セカンダリ レプリカでのバックアップ (AlwaysOn 可用性グループ)</span><span class="sxs-lookup"><span data-stu-id="12585-102">Active Secondaries: Backup on Secondary Replicas (Always On Availability Groups)</span></span>
  <span data-ttu-id="12585-103">[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] のアクティブなセカンダリ機能では、セカンダリ レプリカでのバックアップ操作の実行をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="12585-103">The [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] active secondary capabilities include support for performing backup operations on secondary replicas.</span></span> <span data-ttu-id="12585-104">バックアップ操作では、(バックアップ圧縮により) I/O と CPU に大きな負荷がかかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="12585-104">Backup operations can put significant strain on I/O and CPU (with backup compression).</span></span> <span data-ttu-id="12585-105">同期済みまたは同期中のセカンダリ レプリカへバックアップをオフロードすることで、ワークロードが最も多いプライマリ レプリカをホストするサーバー インスタンスでリソースを使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="12585-105">Offloading backups to a synchronized or synchronizing secondary replica allows you to use the resources on server instance that hosts the primary replica for your tier-1 workloads.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="12585-106">可用性グループのプライマリ データベースとセカンダリ データベースでは、RESTORE ステートメントを使用できません。</span><span class="sxs-lookup"><span data-stu-id="12585-106">RESTORE statements are not allowed on either the primary or secondary databases of an availability group.</span></span>  
  
  
  
##  <a name="backup-types-supported-on-secondary-replicas"></a><a name="SupportedBuTypes"></a> <span data-ttu-id="12585-107">セカンダリ レプリカでサポートされるバックアップの種類</span><span class="sxs-lookup"><span data-stu-id="12585-107">Backup Types Supported on Secondary Replicas</span></span>  
  
-   <span data-ttu-id="12585-108">セカンダリ レプリカで実行されたときに `BACKUP DATABASE` でサポートされるのは、データベース、ファイル、またはファイル グループのコピーのみの完全バックアップだけです。</span><span class="sxs-lookup"><span data-stu-id="12585-108">`BACKUP DATABASE` supports only copy-only full backups of databases, files, or filegroups when it is executed on secondary replicas.</span></span> <span data-ttu-id="12585-109">コピーのみのバックアップはログ チェーンには影響しません。また、コピーのみのバックアップを実行しても、差分ビットマップは消去されません。</span><span class="sxs-lookup"><span data-stu-id="12585-109">Note that copy-only backups do not impact the log chain or clear the differential bitmap.</span></span>  
  
-   <span data-ttu-id="12585-110">差分バックアップは、セカンダリ レプリカではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="12585-110">Differential backups are not supported on secondary replicas.</span></span>  
  
-   <span data-ttu-id="12585-111">**BACKUP LOG** でサポートされるのは通常のログ バックアップだけです (セカンダリ レプリカでのログ バックアップでは、COPY_ONLY オプションはサポートされていません)。</span><span class="sxs-lookup"><span data-stu-id="12585-111">**BACKUP LOG** supports only regular log backups (the COPY_ONLY option is not supported for log backups on secondary replicas).</span></span>  
  
     <span data-ttu-id="12585-112">可用性モード (同期コミットまたは非同期コミット) に関係なく、任意のレプリカ (プライマリまたはセカンダリ) で取得されたログ バックアップ全体にわたって一貫性のあるログ チェーンが保証されます。</span><span class="sxs-lookup"><span data-stu-id="12585-112">A consistent log chain is ensured across log backups taken on any of the replicas (primary or secondary), irrespective of their availability mode (synchronous-commit or asynchronous-commit).</span></span>  
  
-   <span data-ttu-id="12585-113">セカンダリ データベースをバックアップするには、セカンダリ レプリカがプライマリ レプリカと通信可能で、`SYNCHRONIZED` または `SYNCHRONIZING` であることが必要です。</span><span class="sxs-lookup"><span data-stu-id="12585-113">To back up a secondary database, a secondary replica must be able to communicate with the primary replica and must be `SYNCHRONIZED` or `SYNCHRONIZING`.</span></span>  
  
##  <a name="configuring-where-backup-jobs-run"></a><a name="WhereBuJobsRun"></a> <span data-ttu-id="12585-114">バックアップ ジョブを実行する場所の構成</span><span class="sxs-lookup"><span data-stu-id="12585-114">Configuring Where Backup Jobs Run</span></span>  
 <span data-ttu-id="12585-115">セカンダリ レプリカでバックアップを実行してプライマリ運用サーバーからバックアップ ワークロードをオフロードすると、非常に大きな利点があります。</span><span class="sxs-lookup"><span data-stu-id="12585-115">Performing backups on a secondary replica to offload the backup workload from the primary production server is a great benefit.</span></span> <span data-ttu-id="12585-116">ただし、セカンダリ レプリカでバックアップを実行する場合は、バックアップ ジョブを実行する場所を決定するプロセスは非常に複雑です。</span><span class="sxs-lookup"><span data-stu-id="12585-116">However, performing backups on secondary replicas introduce significant complexity to the process of determining where backup jobs should run.</span></span> <span data-ttu-id="12585-117">これに対処するには、バックアップ ジョブを実行する場所を次のように構成します。</span><span class="sxs-lookup"><span data-stu-id="12585-117">To address this, configure where backup jobs run as follows:</span></span>  
  
1.  <span data-ttu-id="12585-118">可用性グループを構成して、バックアップを優先的に実行する可用性レプリカを指定します。</span><span class="sxs-lookup"><span data-stu-id="12585-118">Configure the availability group to specify which availability replicas where you would prefer backups to be performed.</span></span> <span data-ttu-id="12585-119">詳細については、「 *CREATE AVAILABILITY GROUP &#40;Transact-SQL&#41;* 」または「 *ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;* 」の [CREATE AVAILABILITY GROUP &amp;#40;Transact-SQL&amp;#41;](/sql/t-sql/statements/create-availability-group-transact-sql) または [ALTER AVAILABILITY GROUP &amp;#40;Transact-SQL&amp;#41;](/sql/t-sql/statements/alter-availability-group-transact-sql)であることが必要です。</span><span class="sxs-lookup"><span data-stu-id="12585-119">For more information, see *AUTOMATED_BACKUP_PREFERENCE* and *BACKUP_PRIORITY* parameters in [CREATE AVAILABILITY GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-availability-group-transact-sql) or [ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-availability-group-transact-sql).</span></span>  
  
2.  <span data-ttu-id="12585-120">バックアップの実行の候補である可用性レプリカをホストするすべてのサーバー インスタンス上のすべての可用性データベースに対して、スクリプト化されたバックアップ ジョブを作成します。</span><span class="sxs-lookup"><span data-stu-id="12585-120">Create scripted backup jobs for every availability database on every server instance that hosts an availability replica that is a candidate for performing backups.</span></span> <span data-ttu-id="12585-121">詳細については、「 [可用性レプリカでのバックアップの構成 &#40;SQL Server&#41;](configure-backup-on-availability-replicas-sql-server.md) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="12585-121">For more information, see the "Follow Up: After Configuring Backup on Secondary Replicas" section of [Configure Backup on Availability Replicas &#40;SQL Server&#41;](configure-backup-on-availability-replicas-sql-server.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="12585-122">関連タスク</span><span class="sxs-lookup"><span data-stu-id="12585-122">Related Tasks</span></span>  
 <span data-ttu-id="12585-123">**セカンダリ レプリカでバックアップを構成するには**</span><span class="sxs-lookup"><span data-stu-id="12585-123">**To configure backup on secondary replicas**</span></span>  
  
-   [<span data-ttu-id="12585-124">可用性レプリカでのバックアップの構成 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="12585-124">Configure Backup on Availability Replicas &#40;SQL Server&#41;</span></span>](configure-backup-on-availability-replicas-sql-server.md)  
  
 <span data-ttu-id="12585-125">**現在のレプリカが推奨されるバックアップ レプリカであるかどうかを判別するには**</span><span class="sxs-lookup"><span data-stu-id="12585-125">**To determine whether the current replica is the preferred backup replica**</span></span>  
  
-   [<span data-ttu-id="12585-126">sys.fn_hadr_backup_is_preferred_replica</span><span class="sxs-lookup"><span data-stu-id="12585-126">sys.fn_hadr_backup_is_preferred_replica</span></span>](/sql/relational-databases/system-functions/sys-fn-hadr-backup-is-preferred-replica-transact-sql)  
  
 <span data-ttu-id="12585-127">**バックアップ ジョブを作成するには**</span><span class="sxs-lookup"><span data-stu-id="12585-127">**To create a backup job**</span></span>  
  
-   [<span data-ttu-id="12585-128">メンテナンス プラン ウィザードの使用</span><span class="sxs-lookup"><span data-stu-id="12585-128">Use the Maintenance Plan Wizard</span></span>](../../../relational-databases/maintenance-plans/use-the-maintenance-plan-wizard.md)  
  
-   [<span data-ttu-id="12585-129">ジョブの実装</span><span class="sxs-lookup"><span data-stu-id="12585-129">Implement Jobs</span></span>](../../../ssms/agent/implement-jobs.md)  
  
  
## <a name="see-also"></a><span data-ttu-id="12585-130">参照</span><span class="sxs-lookup"><span data-stu-id="12585-130">See Also</span></span>  
 <span data-ttu-id="12585-131">[AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="12585-131">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="12585-132">[コピーのみのバックアップ &#40;SQL Server&#41;](../../../relational-databases/backup-restore/copy-only-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="12585-132">[Copy-Only Backups &#40;SQL Server&#41;](../../../relational-databases/backup-restore/copy-only-backups-sql-server.md) </span></span>  
 <span data-ttu-id="12585-133">[CREATE AVAILABILITY GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-availability-group-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="12585-133">[CREATE AVAILABILITY GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-availability-group-transact-sql) </span></span>  
 [<span data-ttu-id="12585-134">ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="12585-134">ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-availability-group-transact-sql)  
  
  
